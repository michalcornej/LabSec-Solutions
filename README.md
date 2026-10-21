# Technical Lab – LabSec Solutions

Tento repozitář slouží jako technická dokumentace k simulaci interní sítě LAN1. Projekt demonstruje schopnost konfigurace síťových služeb, zabezpečení koncových bodů a analýzy síťového provozu – klíčové kompetence pro role v IT Security a GRC.

## Topologie sítě
Prostředí je postaveno na platformě VirtualBox. Každý virtuální stroj má dva adaptéry:

* **enp0s3 – NAT (10.0.2.0/24):** přístup k internetu (aktualizace, instalace balíčků).
* **enp0s8 – LAN1 (192.168.100.0/24):** interní virtuální síť VirtualBoxu, nedostupná zvenčí.

Uzly v síti LAN1:

* **Ubuntu Server 24.04 (192.168.100.10):** hostitel služeb SSH a webového serveru (Apache2, později nahrazen Nginx).
* **Ubuntu Desktop (192.168.100.20):** klientská a administrační stanice, monitorovací uzel (Wireshark).

---

## Dokumentace testů a konfigurací

Kliknutím na odkaz se dostanete k detailnímu popisu, použitým příkazům a screenshotům.

| Fáze projektu | Popis aktivity | Dokumentace |
| :--- | :--- | :--- |
| **Příprava sítě** | Ověření konfigurace rozhraní, IP adres a směrování | [network_setup.md](./Technical-Lab/network_setup.md) |
| **Konektivita** | Ověření dostupnosti uzlů v rámci LAN1 (ICMP) | [network_tests.md](./Technical-Lab/network_tests.md) |
| **Vzdálený přístup** | První SSH připojení (autentizace heslem) | [ssh_tests.md](./Technical-Lab/ssh_tests.md) |
| **Přenos dat** | Bezpečné kopírování souborů přes SCP | [file_transfer.md](./Technical-Lab/file_transfer.md) |
| **Služby** | Nasazení Apache2 a test HTTP protokolu | [web_server.md](./Technical-Lab/web_server.md) |
| **Bezpečnost** | Výchozí stav firewallu UFW (před hardeningem) | [firewall.md](./Technical-Lab/firewall.md) |
| **Analýza** | Monitoring provozu a zachycení paketů | [wireshark.md](./Technical-Lab/wireshark.md) |
| **Zabezpečení** | Hardening: SSH klíče a omezení SSH ve firewallu UFW | [ssh_access.md](./Technical-Lab/ssh_access.md) |
| **Správa služeb** | Diagnostika a oprava webového serveru Nginx | [nginx_configuration.md](./Technical-Lab/nginx_configuration.md) |

---

## Bezpečnostní dokumentace (ISMS)

| Dokument | Obsah |
| :--- | :--- |
| [scope.md](./ISMS/scope.md) | Rozsah ISMS |
| [assets.md](./ISMS/assets.md) | Seznam aktiv a jejich kritičnost |
| [risk_assessment.md](./ISMS/risk_assessment.md) | Analýza rizik a návrh mitigací |
| [password_policy.md](./ISMS/password_policy.md) | Politika hesel |

---

## Důkazní materiály
Snímky obrazovky prokazující provedení testů naleznete v adresáři [`Screenshots/`](./Screenshots). Odkazy na konkrétní screenshoty jsou také přímo v jednotlivých `.md` souborech.

---
*Tento lab slouží jako evidence technických dovedností pro účely profesního portfolia.*
