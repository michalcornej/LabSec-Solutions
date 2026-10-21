# Nginx Configuration & Service Recovery – LabSec Solutions

Tento dokument popisuje nasazení webového serveru Nginx místo Apache2,
diagnostiku chybné konfigurace, která způsobila výpadek služby,
a obnovení provozu bez restartu celého operačního systému.

## Použité systémy
- Ubuntu Server: cílový uzel s Nginx (192.168.100.10)
- Interní síť: LAN1 (VirtualBox Internal Network)

---

## Popis incidentu a verifikace
Cílem bylo identifikovat příčinu selhání služby Nginx a provést nápravu tak, aby:

- byla před nasazením ověřena syntaktická správnost konfigurace (`nginx -t`)
- byla restartována pouze služba, nikoliv celý OS

## Diagnostika a oprava (postup)

### 1. Detekce chyby
Nejprve bylo nutné zjistit, proč služba neběží:

```bash
sudo systemctl status nginx
sudo journalctl -u nginx --no-pager | tail -n 20
```

Log odhalil dva problémy v různých časech:

- **Konflikt portu:** `bind() to 0.0.0.0:80 failed (98: Address already in use)` – port 80 obsazoval dosud běžící Apache2. Po jeho zastavení se Nginx spustil úspěšně.
- **Chyba konfigurace:** `host not found in "80abc" of the "listen" directive` – neplatná hodnota direktivy `listen`, služba se nespustila.

### 2. Validace konfigurace
Kontrola syntaxe určila přesné místo chyby:

```bash
sudo nginx -t
```

```
[emerg] host not found in "80abc" of the "listen" directive in /etc/nginx/sites-enabled/default:22
nginx: configuration file /etc/nginx/nginx.conf test failed
```

### 3. Oprava a restart služby
V souboru `/etc/nginx/sites-enabled/default` byla direktiva opravena
z `listen 80abc default_server;` na `listen 80 default_server;`.
Po úspěšném testu syntaxe byla restartována pouze služba:

```bash
sudo nginx -t
sudo systemctl restart nginx
```

## Výsledek
- **Služba:** Nginx je plně funkční a v aktivním stavu (`active (running)`).
- **Konfigurace:** výstup `nginx -t` potvrzuje `syntax is ok` a `test is successful`.
- **Dostupnost:** webová služba byla obnovena okamžitě po opravě konfigurace, bez zbytečného downtime způsobeného rebootem.

## Důkaz
![Chybná direktiva listen 80abc a neúspěšný restart](../Screenshots/nginx_broken.png)

![Log služby Nginx (journalctl)](../Screenshots/nginx_failed.png)

![Výstup nginx -t s chybou](../Screenshots/nginx_error.png)

![Opravená konfigurace a úspěšný nginx -t](../Screenshots/nginx_repaired.png)

## Závěr
Díky logům (`journalctl`), kontrole syntaxe (`nginx -t`) a správě služeb
přes `systemctl` byla chyba rychle lokalizována a odstraněna. Postup
demonstruje správu webového serveru s minimálním dopadem na dostupnost
ostatních služeb běžících na stejném uzlu.

[← Zpět na hlavní přehled](../README.md)
