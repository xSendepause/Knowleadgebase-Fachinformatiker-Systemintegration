# Einsatzbereiche IT-Systeme

> 📝 **Prüfungsrelevanz:** AP1 + AP2
> 🔖 **Lernstatus:** ⬜ Nicht begonnen | 🔄 In Bearbeitung | ✅ Abgeschlossen

## Lernziele
- [ ] Kommunikationssysteme kennen
- [ ] Client-Server-Systeme verstehen
- [ ] Active Directory Einbindung verstehen
- [ ] Netzwerkprotokolle kennen

## Grundlagen


## Wichtige Begriffe

| Begriff | Definition |
|---------|------------|
| Client | |Ein Client ist ein Computerprogramm oder Gerät das auf einem Computer oder anderer Hardware ausgeführt wird und Dienste oder Ressourcen von einem Server über ein Netzwerk anfordert 
| Server | Ein Server ist ein Leistungsstarker Rechner oder Programm das Ressourcen , Daten, Dienste oder Programme für andere Geräte oder Programme, sogenannte Clients, über ein Netzwerk bereitstellt.|
| Domäne | Eine Domäne ist ein administrativ abgegrenzter Bereich Netzwerkbereich in dem Benutzer, Geräte und Ressourcen zentral verwaltet werden und durch einheitliche Sicherheitsrichtlinien einheitlich gesteuert werden. Typische zentrale Verwaltung umfasst Benutzerkonten, Computer, Gruppen, Zugriffrechte und Gruppenrichtlinien.|
| Active Directory |Active Directory (AD) ist ein von Microsoft entwickelter Verzeichnisdienst für Windows-Netzwerke. Er ermöglicht die zentrale Verwaltung von Benutzern, Computern, Gruppen, Berechtigungen und weiteren Netzwerkressourcen. In klassischen Windows-Unternehmensnetzwerken bildet insbesondere Active Directory Domain Services (AD DS) häufig eine zentrale Komponente für Identitäts-, Authentifizierungs- und Autorisierungsdienste.
*Kernkomponenenten der AD*
Gesamtstruktur(Forest): | Die höchst logische Struktur innerhalb einer Active Directory. Ein Forest umfasst eine oder mehrere Domänen, die sich ein gemeinsames Schema und eine gemeinsame Konfiguration teilen. Zudem stellt ein Forest einen globalen Katalog bereit . über den Informationen zu Objekten forestweit/ in der gesamten Struktur gesucht werden können. Zwischen den Domänen eines Forests bestehen automatisch transitive Vertrauenstellungen. (sind automatische, bidirektionale Vertrauensbeziehungen zwischen übergeordneten und untergeordneten Domänen)|
Domain Controller:| Ein Server der auf dem Active Directory Domain Services (AD DS) er speichert eine vollständige Kopie der AD-Datenbank und übernimmt unter anderem Authentifizierung, Autorisierung und Replikation. in der Regel werden in einer professionellen Infrastruktur 2 installiert um eine Redundanz zu bilden |
Organistationseinheit: |Organisationseinheiten sind Container innerhalb einer Domäne, mit denen du Objekte logisch gruppieren kannst. Sie spiegeln oft die Unternehemensstruktur wieder, etwa OUs für verschiedene Abteilungen, Standorte, Benutzer, Computer, Drucker und Gruppen. |
Schema: |Das Schema definiert die Struktur und die Regeln des Active Directory. Es legt fest, welche Objekttypen (Klassen) und welche Eigenschaften (Attribute) für diese Objekte im Active Directory existieren und gespeichert werden können. Beispielsweise definiert das Schema die Objektklasse Benutzer (User) mit möglichen Attributen wie Vorname, Nachname, E-Mail-Adresse und Telefonnummer|
Authentifizierung und Protokolle:
 | -LDAP: |LDAP ist das Protokoll, über das Anwendungen mit Active Directory kommunizieren. Wenn du beispielsweise im Adressbuch von Outlook nach einem Kollegen suchst, stellt Outlook eine LDAP-Abfrage an den Domain Controller|
  -Kerberos: |Das standardmäßige Authentifizierungsprotokoll in Active-Directory-Domänen. Es arbeitet ticketbasiert und ermöglicht unter anderem Single Sign-on (SSO).|
  -Protokolle: |
Gruppenrichtlinien: |Gruppenrichtlinien(GPO's) ermöglichen die zentrale Konfiguration und Durchsetzung von Einstellungen für Benutzer und Computer in einer Active Directory Umgebung. Einstellungen lassen sich auf die jeweils betroffenen Benutzer und Computer anwenden, ohne jeden rechnr einzeln konfigurieren zu müssen.
      Typische Einsatzbereiche sind: Sicherheitseinstellungen wie bspw. Kennwort- und        Kontorichtlinien, Konfigurationen von Windowseinstellungen und Systemeinstellungen, Einschränkung des Zugriffs auf verschiedenen Funktionen, Ausführen von An- und Abmeldeskripten, Startskripte, Konfiguration von Defender Firewall, Bereitstellung bestimmter Software über GPO Plicy Softwareinstallation.|


## Kommunikationssysteme

*Kommunikationsysteme sind technische Einrichtungen oder Netzwerke, die den Austausch von Informationen zwischen Sendern und Empfängern ermöglichen. Sie bilden die Grundlage für die moderne Informationsgesellschaft und sind essenziell für Wirtschaft, Bildung und soziale Interaktionen*

### Arten von Kommunikationssystemen:

**Videokonferenzsysteme:**
- ermöglichen Echtzeitkommunkation pber Video & Audio
- ALL-In-One Systeme mit integrierter Hardware (Kamera, Mikrofon & Lautsprecher)
- Funktionen wie intelligente Sprechererkennung und Bildanpassung
- z.B. Teams, Skype(auch wenn es das nicht mehr gibt ^^) oder Webex

**Social Media System:**
- Digitale Plattform, die den sozialen Austasuch, networking und Content sharing ermöglichen.
- synchrone und asynchrone Kommunikation
- Multimedia Inhalte (Bilder, Texte, Videos usw.)

**

## Client-Server-Systeme

Ein Client-Server-System besteht aus mehreren Clients, die mit einem oder mehreren Servern verbunden sind. Clients sind hier Endgeräte wie Smartphones, Laptops, Desktop-PC's & Thinclients.

### Client begriff

- **ThinClient:** Minimaler Client, der hauptsächlich serverabhängig ist. Bspw. Zeigen diese 
nur eine minimale Benutzeroberfläche, oder haben mittels Virtueller Maschine eine 
“Übertragung” eines vollwertigen Betriebssystems. Die eigentliche Verarbeitung passiert 
auf dem Server

- **Thick Client:**  Laptops oder Desktop-PCs von Mitarbeitern kann man als Thick-Client 
beschreiben, die Geräte speichern und verarbeiten Daten Direkt, können aber auf 
Dateiserver oder Datenbankserver zugreifen für zusätzliche Information.

### Server Beispiele

**Druckserver:** Verwalten und steuern Drucker und Druckaufträge, zentralle Schnittstelle 
für alle Drucker
**Dateiserver:** Bspw. Ordnerstrukturen für NAS, die auch Zugriffsrechte etc. Regeln
**Datenbankserver:**  wo die Anfragen von Clients bearbeitet werden, um Daten abzurufen 
oder generell Manipulieren zu können. Bspw. SQL (Structured Query Language)


## Einbindung Domäne (Active Directory)

Die Einbindung eines Endgeräts in eine Domäne – zum Beispiel in einem Unternehmensnetzwerk – ermöglicht es, zentrale Netzwerkressourcen und Richtlinien gemeinsam zu nutzen. Ein großer Vorteil ist die zentrale Benutzerverwaltung: Mitarbeitende können sich mit denselben Zugangsdaten an verschiedenen Geräten anmelden und erhalten dabei automatisch die für sie vorgesehenen Rechte und Zugriffe.

Durch die Domäne lassen sich Zugriffe auf Dateien, Drucker und Anwendungen effizient steuern. Bekannte Lösungen wie Microsoft Active Directory bieten hierfür eine übersichtliche, hierarchische Struktur, in der Benutzer, Gruppen und Ressourcen verwaltet werden. So können beispielsweise Gruppenrichtlinien (Group Policies) genutzt werden, um Sicherheitsvorgaben, Verschlüsselung oder Multi-Faktor-Authentifizierung zentral und einheitlich umzusetzen. Das sorgt für mehr Sicherheit und erleichtert die Administration im Unternehmen.


## Netzwerkprotokolle

![OSI-Modell](OSI-Modell.png)

| Protokoll / Technologie | Zweck / Funktion | Typische Einsatzgebiete | Port(s) |
|---|---|---|---|
| **TCP** (Transmission Control Protocol) | Zuverlässige, verbindungsorientierte Datenübertragung | Internet, Web-Kommunikation | Keine feste Portnummer – TCP verwendet Ports 0–65535 |
| **UDP** (User Datagram Protocol) | Schnelle, verbindungslose Datenübertragung | Streaming, VoIP, Online-Gaming | Keine feste Portnummer – UDP verwendet Ports 0–65535 |
| **IP** (Internet Protocol) | Adressierung & Routing von Datenpaketen | Internet, Netzwerke | Keine Ports |
| **ICMP** (Internet Control Message Protocol) | Fehler- & Statusmeldungen | Netzwerkdiagnose (z. B. Ping) | Keine Ports |
| **HTTP** (Hypertext Transfer Protocol) | Datenübertragung für Webseiten | Webbrowser, Webseiten | TCP 80 |
| **HTTPS** (HTTP Secure) | Verschlüsselte Web-Kommunikation über TLS | Sichere Webseiten, Webanwendungen | TCP 443 / HTTP/3: UDP 443 |
| **FTP** (File Transfer Protocol) | Dateiübertragung zwischen Client & Server | Webhosting, Dateiübertragung | TCP 21 (Steuerung), TCP 20 (Active Mode) |
| **SMTP** (Simple Mail Transfer Protocol) | Versand und Übertragung von E-Mails | E-Mail-Server | TCP 25 / 465 / 587 |
| **IMAP** (Internet Message Access Protocol) | E-Mail-Abruf mit Server-Synchronisation | E-Mail-Clients | TCP 143 / TLS: TCP 993 |
| **POP3** (Post Office Protocol 3) | Abruf von E-Mails vom Mailserver | E-Mail-Clients | TCP 110 / TLS: TCP 995 |
| **DNS** (Domain Name System) | Namensauflösung und Bereitstellung von DNS-Informationen | Internet, Netzwerke, Active Directory | UDP/TCP 53 |
| **DHCP** (Dynamic Host Configuration Protocol) | Automatische Vergabe von Netzwerkkonfigurationen | Heimnetzwerke, Unternehmen | UDP 67/68 (IPv4), UDP 546/547 (IPv6) |
| **SNMP** (Simple Network Management Protocol) | Überwachung & Verwaltung von Netzwerkgeräten | IT-Administration, Monitoring | UDP 161 / Traps: UDP 162 |
| **TLS** (Transport Layer Security) | Verschlüsselung und Authentifizierung von Netzwerkverbindungen | HTTPS, E-Mail, LDAP | Kein eigener Port |
| **SSH** (Secure Shell) | Sichere Fernsteuerung von Systemen | Server-Administration, IT-Sicherheit | TCP 22 |
| **Wi-Fi** (IEEE 802.11) | Drahtlose Netzwerkkommunikation | WLAN-Netzwerke | Keine TCP/UDP-Ports |
| **Bluetooth** | Drahtlose Kurzstreckenkommunikation | Kopfhörer, Eingabegeräte, IoT | Keine TCP/UDP-Ports |
| **NFC** (Near Field Communication) | Drahtlose Nahfeldkommunikation | Kontaktloses Bezahlen, Smartcards | Keine TCP/UDP-Ports |
| **VoIP** (Voice over IP) | Sprachkommunikation über IP-Netzwerke | IP-Telefonie, Videokonferenzen | Abhängig von SIP/RTP |
| **Ethernet** (IEEE 802.3) | Kabelgebundene Datenübertragung im LAN | LAN, Switches, Unternehmensnetzwerke | Keine TCP/UDP-Ports |
| **ARP** (Address Resolution Protocol) | Ermittelt die MAC-Adresse zu einer IPv4-Adresse | IPv4-LAN | Keine Ports |
| **IPv4 / IPv6** | Adressierung und Routing von Datenpaketen | LAN, WAN, Internet | Keine Ports |
| **VLAN** (IEEE 802.1Q) | Logische Segmentierung eines Netzwerks | Netztrennung, Unternehmensnetzwerke | Keine Ports |
| **NAT** (Network Address Translation) | Übersetzung von IP-Adressen zwischen Netzwerken | Router, Firewalls, Internetzugang | Kein eigener Port |
| **NTP** (Network Time Protocol) | Synchronisation der Systemzeit | Server, Clients, Active Directory | UDP 123 |
| **LDAP** (Lightweight Directory Access Protocol) | Zugriff auf Verzeichnisdienste | Active Directory | TCP/UDP 389 |
| **LDAPS** (LDAP over TLS) | Verschlüsselter LDAP-Zugriff | Active Directory | TCP 636 |
| **Kerberos** | Ticketbasierte Authentifizierung | Active Directory, Single Sign-on | TCP/UDP 88 |
| **SMB** (Server Message Block) | Zugriff auf Dateien, Drucker und Netzwerkfreigaben | Windows-Netzwerke, Fileserver, Active Directory | TCP 445 |
| **RDP** (Remote Desktop Protocol) | Grafischer Fernzugriff auf Windows-Systeme | Windows-Administration | TCP/UDP 3389 |
| **SFTP** (SSH File Transfer Protocol) | Sichere Dateiübertragung über SSH | Server-Administration | TCP 22 |
| **SCP** (Secure Copy Protocol) | Sichere Dateiübertragung über SSH | Linux-/Unix-Systeme | TCP 22 |
| **SIP** (Session Initiation Protocol) | Aufbau und Steuerung von VoIP-Sitzungen | IP-Telefonie, VoIP | UDP/TCP 5060 / TLS: TCP 5061 |
| **RTP** (Real-time Transport Protocol) | Übertragung von Audio- und Videodaten in Echtzeit | VoIP, Videokonferenzen | Dynamische UDP-Ports |
| **SRTP** (Secure Real-time Transport Protocol) | Verschlüsselte Echtzeitübertragung von Audio/Video | Sichere VoIP-Kommunikation | Dynamische Ports |
| **OSPF** (Open Shortest Path First) | Dynamisches Routing innerhalb eines autonomen Systems | Router, Unternehmensnetzwerke | Keine TCP/UDP-Ports, IP-Protokollnummer 89 |
| **BGP** (Border Gateway Protocol) | Routing zwischen autonomen Systemen | Internet, Provider | TCP 179 |
| **IPsec** (Internet Protocol Security) | Absicherung von IP-Kommunikation | VPN, Site-to-Site-Verbindungen | IKE: UDP 500 / NAT-T: UDP 4500 |
| **L2TP** (Layer 2 Tunneling Protocol) | Tunneling von Netzwerkverbindungen | VPN | UDP 1701 |
| **WireGuard** | Modernes VPN-Protokoll | Remote-Access- und Site-to-Site-VPN | UDP, häufig 51820 |
| **MQTT** (Message Queuing Telemetry Transport) | Leichtgewichtiges Publish/Subscribe-Messaging | IoT, Sensoren, Automatisierung | TCP 1883 / TLS: TCP 8883 |
| **mDNS** (Multicast DNS) | Namensauflösung ohne zentralen DNS-Server | Lokale Netzwerke, Bonjour, IoT | UDP 5353 |


## Prüfungsrelevante Inhalte

<!-- TODO: Wichtige Prüfungspunkte ergänzen -->

## Beispiele / Praxisbezug

<!-- TODO: Praktische Beispiele ergänzen -->

## Zusammenfassung

<!-- TODO: Kurze Zusammenfassung -->

## Prüfungsfragen zum Üben

- [ ] Was ist der Unterschied zwischen TCP und UDP?
- [ ] Wie funktioniert die Einbindung in eine Active Directory Domäne?
- [ ] Welche Protokolle werden für E-Mail verwendet?

## Quellen

- [ ] Noch keine Quellen

---
[↩ Zurück zur Übersicht](../README.md) | [Vorheriges Thema](01_Marktgaengige_IT_Systeme.md) | [Nächstes Thema](03_Leistungsfaehigkeit_Energieeffizienz.md)
