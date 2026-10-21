# Network Connectivity Test – LabSec Solutions

Tento dokument popisuje ověření konektivity mezi Ubuntu Desktopem
a Ubuntu Serverem v interní síti LAN1.

## Použité systémy
- Ubuntu Server (192.168.100.10)
- Ubuntu Desktop (192.168.100.20)
- Interní síť: LAN1 (VirtualBox Internal Network)

---

## Ověření síťové konektivity (Ping)

Cílem testu je ověřit, že Ubuntu Desktop a Ubuntu Server spolu
komunikují v interní síti LAN1.

### Použitý příkaz (Desktop)
```bash
ping 192.168.100.10
```

## Výsledek
Ping byl úspěšný (6 paketů odesláno, 6 přijato, 0 % ztrát). Bylo potvrzeno:

- funkční interní síť LAN1
- správné nastavení IP adres (Desktop 192.168.100.20/24 na `enp0s8`)
- neblokovaný ICMP provoz

## Důkaz
![Ping z Desktopu na Server](../Screenshots/ping_server.png)

## Závěr
Základní síťová konektivita mezi virtuálními stroji v lab prostředí
je funkční. Průchod ICMP paketů je dále analyzován ve
[Wireshark capture](./wireshark.md).

[← Zpět na hlavní přehled](../README.md)
