# SSH Access Test – LabSec Solutions

Tento dokument popisuje první test vzdáleného přístupu přes SSH
v testovacím lab prostředí, ještě před hardeningem.

## Použité systémy
- Ubuntu Server (192.168.100.10)
- Ubuntu Desktop (192.168.100.20)
- Interní síť: LAN1 (VirtualBox Internal Network)

---

## Test SSH přihlášení

Cílem je ověřit funkční vzdálené přihlášení z Ubuntu Desktopu
na Ubuntu Server pomocí SSH.

### Použitý příkaz (Desktop)
```bash
ssh admin@192.168.100.10
```

## Výsledek
- Přihlášení bylo úspěšné.
- Autentizace proběhla **heslem** uživatele `admin` (výchozí stav OpenSSH).
- SSH spojení je stabilní a připravené pro přenosy souborů (SCP).

## Důkaz
![SSH přihlášení heslem](../Screenshots/ssh_handshake.png)

## Závěr
SSH přístup mezi virtuálními stroji funguje. Autentizace heslem je
zranitelná vůči útokům hrubou silou, proto byla v dalším kroku
nahrazena SSH klíči – viz [SSH Access & Firewall](./ssh_access.md).

[← Zpět na hlavní přehled](../README.md)
