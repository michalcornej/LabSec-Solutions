# Firewall Status – LabSec Solutions

Tento dokument popisuje kontrolu výchozího stavu firewallu UFW
na Ubuntu Serveru v testovacím lab prostředí (před hardeningem).

## Použité systémy
- Ubuntu Server (192.168.100.10)
- Ubuntu Desktop (192.168.100.20)
- Interní síť: LAN1 (VirtualBox Internal Network)

---

## Test stavu firewallu (UFW)

Cílem je ověřit, že firewall je aktivní, a zkontrolovat, které
porty povoluje.

### Použitý příkaz (Server)
```bash
sudo ufw status
```

## Výsledek
- Firewall je aktivní (`Status: active`).
- Povoleny jsou porty **22/tcp (SSH)** a **80/tcp (HTTP)**, oba z libovolné adresy (`Anywhere`), pro IPv4 i IPv6.
- Ostatní příchozí provoz je blokován výchozí politikou UFW.

## Důkaz
![Výchozí stav UFW](../Screenshots/firewall_status.png)

## Zjištění
SSH je dostupné z jakékoli adresy, což zbytečně zvětšuje útočnou
plochu. Náprava (omezení SSH pouze na administrační stanici
192.168.100.20) je popsána v [SSH Access & Firewall](./ssh_access.md).

## Závěr
Firewall na serveru je funkční a poskytuje základní ochranu,
pravidla pro SSH však bylo nutné zpřísnit.

[← Zpět na hlavní přehled](../README.md)
