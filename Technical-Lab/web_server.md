# Web Server Test – LabSec Solutions

Tento dokument popisuje test běžícího webového serveru
v interní síti LAN1 v testovacím lab prostředí.

## Použité systémy
- Ubuntu Server (Apache2, 192.168.100.10)
- Ubuntu Desktop (192.168.100.20)
- Interní síť: LAN1 (VirtualBox Internal Network)

---

## Test přístupu k webovému serveru

Cílem je ověřit, že webový server je dostupný z Ubuntu Desktopu
a správně poskytuje obsah přes HTTP.

### Použitý příkaz / prohlížeč
Na Desktopu otevřeno:
`http://192.168.100.10`

## Výsledek
- Stránka byla načtena úspěšně
- HTTP požadavky byly doručeny serveru
- Apache běží a odpovídá na požadavky z interní sítě

## Důkaz

![Výchozí stránka Apache2 v prohlížeči](../Screenshots/apache_test.png)

---

## Závěr
Webový server je funkční a dostupný z interní sítě LAN1.
Lab prostředí je připraveno pro další testy síťových služeb.

Poznámka: Apache2 byl později nahrazen webovým serverem Nginx –
viz [Nginx Configuration & Service Recovery](./nginx_configuration.md).

[← Zpět na hlavní přehled](../README.md)
