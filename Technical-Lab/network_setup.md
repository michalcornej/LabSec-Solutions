# Network Setup – LabSec Solutions

Tento dokument popisuje síťovou konfiguraci Ubuntu Serveru v testovacím
lab prostředí: síťové adaptéry, IP adresy a směrovací tabulku.

## Použité systémy
- Ubuntu Server (192.168.100.10)
- Ubuntu Desktop (192.168.100.20)
- Interní síť: LAN1 (VirtualBox Internal Network)

---

## Adresní plán

| Uzel | Rozhraní | Typ sítě | IP adresa | Přidělení |
| :--- | :--- | :--- | :--- | :--- |
| Ubuntu Server | enp0s3 | NAT | 10.0.2.15/24 | DHCP (VirtualBox) |
| Ubuntu Server | enp0s8 | LAN1 | 192.168.100.10/24 | statická (netplan) |
| Ubuntu Desktop | enp0s8 | LAN1 | 192.168.100.20/24 | statická |

## Výpis IP adres a směrovací tabulky

Cílem je ověřit konfiguraci síťových adaptérů a směrovací tabulky
na Ubuntu Serveru.

### Použité příkazy (Server)
```bash
ip a
ip route
```

## Výsledek
- Rozhraní `lo` (loopback, 127.0.0.1/8) je aktivní.
- Rozhraní `enp0s3` (NAT) má adresu 10.0.2.15/24 přidělenou přes DHCP.
- Rozhraní `enp0s8` (LAN1) má statickou adresu 192.168.100.10/24.
- Výchozí brána vede přes NAT (`default via 10.0.2.2 dev enp0s3`).
- Síť LAN1 je dostupná přímo přes `enp0s8` (`192.168.100.0/24 dev enp0s8`), bez brány.

## Důkaz
![Výpis ip a a ip route na serveru](../Screenshots/ip_route.png)

## Závěr
Konfigurace síťových adaptérů a směrovací tabulky na serveru je
správná: internetový provoz jde přes NAT, provoz v LAN1 zůstává
v interní síti.

[← Zpět na hlavní přehled](../README.md)
