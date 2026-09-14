# Switching und VLAN

> 📝 **Prüfungsrelevanz:** AP1 + AP2
> 🔖 **Lernstatus:** ⬜ Nicht begonnen | 🔄 In Bearbeitung | ✅ Abgeschlossen

## Lernziele
- [ ] Lernziel 1
- [ ] Lernziel 2
# Switching und VLAN

> 📝 **Prüfungsrelevanz:** AP1 + AP2
> 🔖 **Lernstatus:** ⬜ Nicht begonnen | 🔄 In Bearbeitung | ✅ Abgeschlossen

## Lernziele

# Switching und VLAN

> 📝 **Prüfungsrelevanz:** AP1 + AP2
> 🔖 **Lernstatus:** ⬜ Nicht begonnen | 🔄 In Bearbeitung | ✅ Abgeschlossen

---

## Inhaltsverzeichnis

* [Lernziele](#lernziele)
* [Grundlagen](#grundlagen)

  * [Was ist Switching?](#was-ist-switching)
  * [Switching auf Layer 2](#switching-auf-layer-2)
  * [Ethernet-Frames](#ethernet-frames)
  * [MAC-Adressen](#mac-adressen)
  * [MAC-Adress-Tabelle](#mac-adress-tabelle)
  * [Wie entscheidet ein Switch?](#wie-entscheidet-ein-switch)
  * [Flooding](#flooding)
* [Switch-Arten und Weiterleitungsverfahren](#switch-arten-und-weiterleitungsverfahren)

  * [Hub](#hub)
  * [Layer-2-Switch](#layer-2-switch)
  * [Layer-3-Switch](#layer-3-switch)
  * [Store-and-Forward](#store-and-forward)
  * [Cut-Through](#cut-through)
* [Wichtige Begriffe](#wichtige-begriffe)
* [VLAN](#vlan)

  * [Was ist ein VLAN?](#was-ist-ein-vlan)
  * [Warum werden VLANs eingesetzt?](#warum-werden-vlans-eingesetzt)
  * [Broadcast-Domänen](#broadcast-domänen)
  * [VLAN-ID](#vlan-id)
* [VLAN-Porttypen](#vlan-porttypen)

  * [Access-Port](#access-port)
  * [Trunk-Port](#trunk-port)
  * [IEEE 802.1Q](#ieee-8021q)
  * [Native VLAN](#native-vlan)
* [VLAN-Planung](#vlan-planung)
* [VLAN und IP-Adressierung](#vlan-und-ip-adressierung)
* [Inter-VLAN-Routing](#inter-vlan-routing)

  * [Router-on-a-Stick](#router-on-a-stick)
  * [Layer-3-Switch](#layer-3-switch)
  * [SVI](#svi)
* [VLAN und Sicherheit](#vlan-und-sicherheit)
* [Typische Fehler und Fehleranalyse](#typische-fehler-und-fehleranalyse)
* [Prüfungsrelevante Inhalte AP1](#prüfungsrelevante-inhalte-ap1)
* [Prüfungsrelevante Inhalte AP2](#prüfungsrelevante-inhalte-ap2)
* [Praxisbeispiele](#praxisbeispiele)
* [Prüfungsfallen](#prüfungsfallen)
* [Prüfungsfragen zum Üben](#prüfungsfragen-zum-üben)
* [Mini-Prüfung](#mini-prüfung)
* [Zusammenfassung](#zusammenfassung)
* [Quellen](#quellen)

---

# Lernziele

Nach Bearbeitung dieses Themas kannst du:

* die Aufgabe eines Switches erklären.
* den Unterschied zwischen **Hub, Switch und Router** erklären.
* erklären, auf welcher OSI-Schicht ein Layer-2-Switch arbeitet.
* erklären, was eine **MAC-Adresse** ist.
* die Funktionsweise einer **MAC-Adress-Tabelle** erklären.
* erklären, wie ein Switch Ethernet-Frames weiterleitet.
* **Unicast, Broadcast und Multicast** unterscheiden.
* erklären, was bei einer unbekannten Ziel-MAC-Adresse passiert.
* den Begriff **VLAN** erklären.
* die Vorteile von VLANs nennen.
* **Broadcast-Domänen** erklären.
* Access-Ports und Trunk-Ports unterscheiden.
* **IEEE 802.1Q** erklären.
* die Funktion eines VLAN-Tags erklären.
* das Konzept des **Native VLANs** erklären.
* VLANs sinnvoll planen.
* VLANs mit IP-Subnetzen kombinieren.
* erklären, warum unterschiedliche VLANs unterschiedliche Broadcast-Domänen darstellen.
* **Inter-VLAN-Routing** erklären.
* **Router-on-a-Stick** erklären.
* die Funktionsweise eines **Layer-3-Switches** erklären.
* die Bedeutung eines **SVI** erklären.
* typische VLAN- und Switching-Fehler analysieren.
* VLANs als Bestandteil einer sicheren Netzwerksegmentierung einsetzen.
* typische Prüfungsaufgaben aus AP1 und AP2 lösen.

---

# Grundlagen

## Was ist Switching?

**Switching** bezeichnet die gezielte Weiterleitung von Daten innerhalb eines Netzwerks.

Ein Switch verbindet verschiedene Netzwerkgeräte, beispielsweise:

* PCs
* Server
* Drucker
* Access Points
* IP-Telefone
* weitere Switches

Ein klassischer Layer-2-Switch arbeitet hauptsächlich auf **Schicht 2 des OSI-Modells**, der Sicherungsschicht.

Zur Weiterleitung verwendet er hauptsächlich **MAC-Adressen**.

### Beispiel

```text
PC 1
  |
  |
  +---------+
            |
         Switch
            |
  +---------+
  |
PC 2
```

Der Switch kann erkennen, an welchem Port sich PC 1 und PC 2 befinden.

Dadurch kann er Daten gezielt weiterleiten.

---

## Switching auf Layer 2

Auf Layer 2 werden Ethernet-Frames übertragen.

Ein Switch untersucht insbesondere:

* Quell-MAC-Adresse
* Ziel-MAC-Adresse

Anhand dieser Informationen entscheidet er, über welchen Port ein Frame weitergeleitet wird.

### Vereinfacht

```text
         Ethernet-Frame
               |
               v
          +---------+
          | Switch  |
          +---------+
               |
        Ziel-MAC bekannt?
          /          \
        Ja            Nein
        |               |
        v               v
 gezielt weiter-     Flooding
   leiten
```

---

# Ethernet-Frames

Auf Ethernet-Ebene werden Daten in sogenannten **Frames** übertragen.

Ein Ethernet-Frame enthält unter anderem:

```text
+----------------+----------------+----------------+
| Ziel-MAC       | Quell-MAC      | Nutzdaten      |
+----------------+----------------+----------------+
```

Vereinfacht betrachtet benötigt der Switch vor allem:

* die **Quell-MAC-Adresse**, um seine MAC-Tabelle zu lernen.
* die **Ziel-MAC-Adresse**, um zu entscheiden, wohin der Frame weitergeleitet wird.

---

# MAC-Adressen

Eine **MAC-Adresse** ist eine Hardwareadresse einer Netzwerkschnittstelle.

Eine MAC-Adresse wird normalerweise hexadezimal dargestellt.

Beispiel:

```text
00:1A:2B:3C:4D:5E
```

Eine MAC-Adresse besteht aus **48 Bit**.

Das entspricht:

```text
6 Byte = 48 Bit
```

### Aufbau

Vereinfacht:

```text
00:1A:2B:3C:4D:5E
└──────┘ └──────┘
Hersteller-    Geräte-
anteil         anteil
```

Die tatsächliche Bedeutung einzelner Bits ist komplexer; für die Prüfung ist vor allem wichtig:

> **MAC-Adresse = Layer-2-Adresse**

---

# MAC-Adress-Tabelle

Ein Switch führt eine Tabelle, in der MAC-Adressen den Switch-Ports zugeordnet werden.

Diese Tabelle wird häufig als:

* MAC-Adress-Tabelle
* CAM-Tabelle
* Forwarding Database

bezeichnet.

### Beispiel

| Port  | MAC-Adresse       | VLAN |
| ----- | ----------------- | ---: |
| Gi0/1 | 00:11:22:33:44:01 |   10 |
| Gi0/2 | 00:11:22:33:44:02 |   10 |
| Gi0/3 | 00:11:22:33:44:03 |   20 |

Der Switch weiß dadurch:

```text
MAC 00:11:22:33:44:01 → Port Gi0/1
MAC 00:11:22:33:44:02 → Port Gi0/2
MAC 00:11:22:33:44:03 → Port Gi0/3
```

---

# Wie lernt ein Switch?

Ein Switch lernt MAC-Adressen anhand der **Quell-MAC-Adresse** eines eingehenden Frames.

### Beispiel

PC A sendet einen Frame:

```text
PC A
MAC: AA:AA:AA:AA:AA:AA
        |
        v
     Gi0/1
        |
      Switch
```

Der Switch sieht:

```text
Quell-MAC:
AA:AA:AA:AA:AA:AA
```

und merkt sich:

```text
AA:AA:AA:AA:AA:AA → Gi0/1
```

### Wichtig

Der Switch lernt die Adresse aus der:

> **Quell-MAC-Adresse**

Nicht aus der Ziel-MAC-Adresse.

---

# Wie entscheidet ein Switch?

Nachdem der Switch die Quell-MAC gelernt hat, untersucht er die **Ziel-MAC-Adresse**.

Es gibt drei wichtige Fälle.

## Fall 1: Ziel-MAC bekannt

Die Ziel-MAC befindet sich in der MAC-Tabelle.

Der Switch leitet den Frame gezielt an den entsprechenden Port weiter.

```text
PC A
  |
  v
Switch
  |
  +------> PC B
```

Andere Ports werden nicht mit diesem Unicast-Frame belastet.

---

## Fall 2: Ziel-MAC unbekannt

Die Ziel-MAC befindet sich nicht in der MAC-Tabelle.

Der Switch führt **Flooding** durch.

Dabei wird der Frame über alle passenden Ports weitergeleitet, außer über den Port, über den der Frame eingegangen ist.

```text
             PC B
              ^
              |
PC A ----> Switch ----> PC C
              |
              v
             PC D
```

---

## Fall 3: Broadcast

Bei einem Broadcast wird der Frame innerhalb der Broadcast-Domäne an alle passenden Ports weitergeleitet.

Beispiel:

```text
        PC A
          |
          v
       Switch
      /   |   \
     v    v    v
   PC B  PC C  PC D
```

Broadcasts werden nicht automatisch über einen Router in andere IP-Netze weitergeleitet.

---

# Flooding

**Flooding** bedeutet, dass ein Switch einen Frame über mehrere Ports weiterleitet.

Dies passiert beispielsweise bei:

* unbekannter Ziel-MAC-Adresse
* Broadcast

Ein Switch sendet den Frame dabei nicht zurück über den Port, über den er empfangen wurde.

---

# Switch-Arten und Weiterleitungsverfahren

## Hub

Ein Hub arbeitet auf **Layer 1**.

Er kennt keine MAC-Adressen und trifft keine intelligente Weiterleitungsentscheidung.

Empfängt ein Hub Daten, werden diese grundsätzlich an alle anderen Ports weitergegeben.

```text
          Hub
       /   |   \
      PC1 PC2  PC3
```

### Nachteile

* unnötiger Datenverkehr
* eine gemeinsame Collision Domain
* ineffiziente Kommunikation
* heute weitgehend durch Switches ersetzt

---

## Layer-2-Switch

Ein Layer-2-Switch arbeitet hauptsächlich auf Layer 2.

Er verwendet:

* MAC-Adressen
* MAC-Tabelle
* VLAN-Informationen

Er kann Frames gezielt weiterleiten.

---

## Layer-3-Switch

Ein Layer-3-Switch kann zusätzlich Routing durchführen.

Damit kann er beispielsweise zwischen VLANs routen.

```text
VLAN 10
   |
   |
Layer-3-Switch
   |
   |
VLAN 20
```

Ein Layer-3-Switch kombiniert somit Switching- und Routing-Funktionen.

---

# Store-and-Forward

Beim **Store-and-Forward-Verfahren** empfängt der Switch zunächst den vollständigen Frame.

Danach kann er den Frame prüfen und anschließend weiterleiten.

Vorteil:

* Fehlerhafte Frames können erkannt und verworfen werden.

Nachteil:

* höhere Latenz als bei Verfahren, die früher weiterleiten.

---

# Cut-Through

Beim **Cut-Through-Switching** beginnt der Switch bereits mit der Weiterleitung, sobald genügend Informationen über das Ziel vorhanden sind.

Dadurch kann die Latenz reduziert werden.

Nachteil:

* fehlerhafte Frames können unter Umständen weitergeleitet werden.

Für Prüfungen ist vor allem der grundlegende Unterschied wichtig:

> **Store-and-Forward:** erst vollständig empfangen, dann weiterleiten.
> **Cut-Through:** Weiterleitung beginnt früher.

---

# Wichtige Begriffe

| Begriff                | Bedeutung                                                             |
| ---------------------- | --------------------------------------------------------------------- |
| **Switch**             | Verbindet Netzwerkgeräte und leitet Frames gezielt weiter             |
| **Layer 2**            | Sicherungsschicht des OSI-Modells                                     |
| **Layer 3**            | Vermittlungsschicht des OSI-Modells                                   |
| **MAC-Adresse**        | Adresse einer Netzwerkschnittstelle auf Layer 2                       |
| **MAC-Tabelle**        | Zuordnung von MAC-Adressen zu Switch-Ports                            |
| **CAM-Tabelle**        | Häufig verwendete Bezeichnung für die MAC-/Forwarding-Tabelle         |
| **Frame**              | Datenübertragungseinheit auf Layer 2                                  |
| **Unicast**            | Kommunikation von einem Sender zu einem Empfänger                     |
| **Broadcast**          | Kommunikation an alle Teilnehmer einer Broadcast-Domäne               |
| **Multicast**          | Kommunikation an eine definierte Empfängergruppe                      |
| **Flooding**           | Weiterleitung eines Frames über mehrere passende Ports                |
| **VLAN**               | Logische Segmentierung eines Layer-2-Netzwerks                        |
| **VLAN-ID**            | Nummer zur Identifikation eines VLANs                                 |
| **Access-Port**        | Port, der einem VLAN für Endgeräte zugeordnet ist                     |
| **Trunk-Port**         | Port zur Übertragung mehrerer VLANs                                   |
| **802.1Q**             | Standard für VLAN-Tagging                                             |
| **VLAN-Tag**           | Information im Ethernet-Frame zur Kennzeichnung des VLANs             |
| **Native VLAN**        | VLAN, dessen Frames auf einem 802.1Q-Trunk untagged übertragen werden |
| **Broadcast-Domäne**   | Bereich, in dem sich Layer-2-Broadcasts ausbreiten                    |
| **Inter-VLAN-Routing** | Routing zwischen verschiedenen VLANs                                  |
| **SVI**                | Virtuelle Layer-3-Schnittstelle für ein VLAN                          |
| **Default Gateway**    | Gateway, über das ein Host andere IP-Netze erreicht                   |
| **Layer-3-Switch**     | Switch mit zusätzlichen Routing-Funktionen                            |
| **Router-on-a-Stick**  | Inter-VLAN-Routing über einen Router mit mehreren Subinterfaces       |

---

# VLAN

## Was ist ein VLAN?

**VLAN** steht für:

> **Virtual Local Area Network**

Mit VLANs kann ein physisches Netzwerk logisch in mehrere getrennte Layer-2-Netzwerke aufgeteilt werden.

### Ohne VLAN

```text
             Switch
          /    |    \
        PC1   PC2   PC3
```

Alle Geräte befinden sich grundsätzlich in derselben Layer-2-Broadcast-Domäne.

### Mit VLANs

```text
             Switch
          /    |    \
        PC1   PC2   PC3
        VLAN10 VLAN20 VLAN10
```

PC1 und PC3 gehören zu VLAN 10.

PC2 gehört zu VLAN 20.

Damit befinden sich PC1/PC3 und PC2 in unterschiedlichen Layer-2-Broadcast-Domänen.

---

# Warum werden VLANs eingesetzt?

VLANs bieten verschiedene Vorteile.

## 1. Netzwerksegmentierung

Ein physisches Netzwerk kann logisch aufgeteilt werden.

Beispiel:

```text
VLAN 10 → Verwaltung
VLAN 20 → Entwicklung
VLAN 30 → Gäste
VLAN 40 → Server
```

---

## 2. Kleinere Broadcast-Domänen

Broadcasts bleiben grundsätzlich innerhalb des jeweiligen VLANs.

Dadurch wird unnötiger Broadcast-Verkehr reduziert.

---

## 3. Sicherheit

VLANs können dabei helfen, Benutzergruppen und Systeme logisch voneinander zu trennen.

Beispiel:

```text
Verwaltung → VLAN 10
Gäste       → VLAN 30
```

Gäste sollen normalerweise nicht direkt auf Systeme der Verwaltung zugreifen können.

### Wichtig

Ein VLAN allein ist **keine vollständige Sicherheitslösung**.

Für eine tatsächliche Zugriffskontrolle können zusätzlich benötigt werden:

* ACLs
* Firewalls
* Routing-Regeln
* Authentifizierung
* Netzwerkzugriffskontrolle

---

## 4. Flexibilität

Die logische Zugehörigkeit zu einem VLAN muss nicht zwangsläufig davon abhängen, an welchem physischen Standort sich ein Gerät befindet.

---

# Broadcast-Domänen

Eine **Broadcast-Domäne** ist der Bereich eines Netzwerks, in dem ein Layer-2-Broadcast verteilt wird.

VLANs teilen ein physisches Netzwerk in mehrere Broadcast-Domänen.

Beispiel:

```text
VLAN 10
+-------------------------+
| PC1 -- PC2 -- PC3       |
|        Broadcast        |
+-------------------------+

VLAN 20
+-------------------------+
| PC4 -- PC5              |
|        Broadcast        |
+-------------------------+
```

Ein Broadcast aus VLAN 10 wird nicht automatisch in VLAN 20 übertragen.

> **Merksatz:**
> **Jedes VLAN bildet grundsätzlich eine eigene Layer-2-Broadcast-Domäne.**

---

# VLAN-ID

Jedes VLAN wird durch eine **VLAN-ID** identifiziert.

Beispiele:

```text
VLAN 10
VLAN 20
VLAN 30
```

Bei IEEE 802.1Q stehen **12 Bit** für die VLAN-ID zur Verfügung.

Theoretisch sind damit Werte von:

```text
0 bis 4095
```

darstellbar.

Allerdings sind nicht alle Werte als normale VLAN-IDs für Endgeräte-VLANs nutzbar.

Für die Prüfung reicht normalerweise:

> **802.1Q verwendet eine 12-Bit-VLAN-ID.**

---

# VLAN-Porttypen

## Access-Port

Ein Access-Port wird typischerweise einem einzelnen VLAN zugeordnet.

Er wird normalerweise für Endgeräte verwendet.

Beispiel:

```text
PC
 |
 | untagged
 |
Access-Port
 |
Switch
 |
VLAN 10
```

Typische Geräte:

* PC
* Drucker
* Server
* andere Endgeräte

Der Datenverkehr eines normalen Endgeräts wird am Access-Port typischerweise **untagged** übertragen.

---

# Trunk-Port

Ein Trunk-Port kann mehrere VLANs gleichzeitig übertragen.

Typische Einsatzfälle:

```text
Switch A
   |
   | Trunk
   |
Switch B
```

oder:

```text
Switch
   |
   | Trunk
   |
Router
```

oder:

```text
Switch
   |
   | Trunk
   |
Virtualisierungsserver
```

Ein Trunk ermöglicht beispielsweise:

```text
VLAN 10
VLAN 20
VLAN 30
VLAN 40
   |
   |
Trunk
   |
   |
anderer Switch
```

---

# IEEE 802.1Q

**IEEE 802.1Q** definiert VLAN-Tagging für Ethernet.

Über das VLAN-Tag kann ein Netzwerkgerät erkennen, zu welchem VLAN ein Frame gehört.

Vereinfacht:

```text
+----------+----------+----------+----------+
| Ziel-MAC | Quell-MAC| 802.1Q   | Daten    |
|          |          | VLAN-Tag  |          |
+----------+----------+----------+----------+
```

Der VLAN-Tag enthält unter anderem die VLAN-ID.

### Merksatz

> **802.1Q = VLAN-Tagging**

---

# Native VLAN

Auf einem 802.1Q-Trunk kann ein **Native VLAN** definiert werden.

Frames des Native VLANs werden auf dem Trunk normalerweise **ohne VLAN-Tag** übertragen.

Das Native VLAN sollte auf miteinander verbundenen Trunk-Ports konsistent konfiguriert sein.

> **Prüfungsfalle:**
> Native VLAN bedeutet nicht automatisch VLAN 1.

VLAN 1 ist auf vielen Switches standardmäßig vorhanden, aber das Native VLAN kann je nach Konfiguration anders festgelegt werden.

---

# VLAN-Planung

Bei der Planung eines Unternehmensnetzwerks sollte man VLANs nach logischen Anforderungen aufteilen.

### Beispiel

| VLAN | Zweck       | Netzwerk        |
| ---: | ----------- | --------------- |
|   10 | Verwaltung  | 192.168.10.0/24 |
|   20 | Entwicklung | 192.168.20.0/24 |
|   30 | Gäste       | 192.168.30.0/24 |
|   40 | Server      | 192.168.40.0/24 |
|   50 | VoIP        | 192.168.50.0/24 |
|   99 | Management  | 192.168.99.0/24 |

Dadurch erhält jede Gruppe ein eigenes logisches Netzwerk.

---

# VLAN und IP-Adressierung

In einer professionellen Netzwerkplanung wird häufig jedem VLAN ein eigenes IP-Subnetz zugeordnet.

Beispiel:

```text
VLAN 10
Netzwerk: 192.168.10.0/24
Gateway:  192.168.10.1

VLAN 20
Netzwerk: 192.168.20.0/24
Gateway:  192.168.20.1
```

### Warum unterschiedliche Subnetze?

VLANs trennen Layer-2-Netze.

Durch unterschiedliche IP-Subnetze werden diese logischen Netze auch auf Layer 3 voneinander getrennt.

---

# Beispiel einer vollständigen VLAN-Struktur

```text
                         Internet
                            |
                         Firewall
                            |
                       Layer-3-Switch
                            |
          +-----------------+-----------------+
          |                 |                 |
       VLAN 10           VLAN 20           VLAN 30
      Verwaltung       Entwicklung          Gäste
          |                 |                 |
        PCs               PCs              WLAN
```

Beispielhafte IP-Netze:

```text
VLAN 10 → 192.168.10.0/24
VLAN 20 → 192.168.20.0/24
VLAN 30 → 192.168.30.0/24
```

---

# Inter-VLAN-Routing

## Problem

VLANs sind voneinander getrennt.

Beispiel:

```text
VLAN 10                  VLAN 20

PC1 ─── Switch ─── X ─── Switch ─── PC2
```

PC1 kann PC2 nicht einfach auf Layer 2 erreichen.

Damit Kommunikation zwischen VLANs möglich wird, wird **Routing** benötigt.

---

# Router-on-a-Stick

Beim **Router-on-a-Stick** wird ein einzelner physischer Router-Port verwendet.

Auf diesem Router-Port werden mehrere logische Subinterfaces konfiguriert.

Beispiel:

```text
             Router
          +----------+
          |          |
          | Gi0/0    |
          +----+-----+
               |
             Trunk
               |
               |
            Switch
        +------+------+
        |             |
      VLAN 10       VLAN 20
```

Beispiel:

```text
Router Gi0/0.10
→ VLAN 10
→ 192.168.10.1

Router Gi0/0.20
→ VLAN 20
→ 192.168.20.1
```

Der Switch-Port zum Router muss entsprechend als Trunk konfiguriert werden.

### Ablauf

```text
PC VLAN 10
    |
    v
Switch
    |
  Trunk
    |
    v
Router
    |
Routing
    |
    v
Switch
    |
    v
PC VLAN 20
```

---

# Layer-3-Switch

Ein Layer-3-Switch kann Routing zwischen VLANs direkt durchführen.

Dadurch ist häufig kein separater Router für das interne Inter-VLAN-Routing erforderlich.

```text
             Layer-3-Switch
          +------------------+
          |                  |
       VLAN 10            VLAN 20
          |                  |
         PCs                PCs
```

Der Layer-3-Switch besitzt für die VLANs entsprechende Layer-3-Schnittstellen.

---

# SVI

**SVI** steht für:

> **Switched Virtual Interface**

Ein SVI ist eine virtuelle Layer-3-Schnittstelle eines Switches.

Beispiel:

```text
interface VLAN 10
IP: 192.168.10.1

interface VLAN 20
IP: 192.168.20.1
```

Diese IP-Adressen können als Default Gateway für die jeweiligen VLANs dienen.

Beispiel:

```text
PC aus VLAN 10
IP:       192.168.10.50
Maske:    255.255.255.0
Gateway:  192.168.10.1
```

---

# Default Gateway

Das **Default Gateway** wird verwendet, wenn ein Host ein Ziel in einem anderen IP-Netz erreichen möchte.

Beispiel:

```text
PC:
192.168.10.50/24

Ziel:
192.168.20.50/24
```

Da sich das Ziel in einem anderen Netzwerk befindet, sendet der PC den Datenverkehr an sein Default Gateway:

```text
192.168.10.1
```

Das Layer-3-Gerät übernimmt anschließend das Routing.

---

# VLAN und Sicherheit

VLANs sind ein wichtiges Mittel zur Netzwerksegmentierung.

Beispiel:

```text
VLAN 10 → Mitarbeiter
VLAN 20 → Server
VLAN 30 → Gäste
```

Man kann anschließend Regeln definieren:

```text
Mitarbeiter → Server       erlaubt
Mitarbeiter → Internet    erlaubt
Gäste       → Internet    erlaubt
Gäste       → Mitarbeiter verboten
Gäste       → Server      verboten
```

Solche Regeln können beispielsweise über:

* Firewalls
* ACLs
* Routing-Regeln

umgesetzt werden.

### Wichtig

> Ein VLAN allein stellt keine vollständige Sicherheitsmaßnahme dar.

Ein Angreifer kann beispielsweise versuchen, VLAN-Fehlkonfigurationen oder andere Netzwerkmechanismen auszunutzen.

---

# Typische Fehler und Fehleranalyse

Bei Problemen mit Switching und VLANs sollte systematisch vorgegangen werden.

## Layer 1 prüfen

Zuerst prüfen:

* Ist das Kabel angeschlossen?
* Leuchtet der Link?
* Ist der Switch-Port aktiv?
* Funktioniert die Netzwerkkarte?

```text
Layer 1
↓
Kabel
Port
Link
```

---

## Layer 2 prüfen

Danach prüfen:

* richtiges VLAN?
* Access-Port korrekt?
* Trunk korrekt?
* VLAN vorhanden?
* VLAN auf Trunk erlaubt?
* MAC-Adresse gelernt?

```text
Layer 2
↓
MAC
VLAN
Access
Trunk
802.1Q
```

---

## Layer 3 prüfen

Danach prüfen:

* richtige IP-Adresse?
* richtige Subnetzmaske?
* richtiges Gateway?
* Routing vorhanden?

```text
Layer 3
↓
IP
Subnetz
Gateway
Routing
```

---

## Layer 4 und höher

Anschließend können geprüft werden:

* Firewall
* ACL
* TCP/UDP-Port
* Anwendung
* DNS
* Dienste

---

# Typischer Fehler: Falsches VLAN

Ein PC sollte zu VLAN 10 gehören.

Der Switch-Port ist jedoch VLAN 20 zugeordnet.

```text
PC
 |
 |
Access-Port
 |
VLAN 20 ❌
```

Der PC befindet sich dadurch im falschen Layer-2-Netz.

---

# Typischer Fehler: VLAN fehlt

VLAN 20 wurde auf Switch A konfiguriert.

Auf Switch B existiert VLAN 20 jedoch nicht.

Geräte in VLAN 20 können dadurch möglicherweise nicht wie erwartet kommunizieren.

---

# Typischer Fehler: Trunk falsch konfiguriert

Zwei Switches sind über einen Link verbunden.

VLAN 10 funktioniert.

VLAN 20 funktioniert nicht.

Mögliche Ursache:

```text
VLAN 20
   |
   X
   |
Trunk
```

VLAN 20 wird möglicherweise auf dem Trunk nicht übertragen bzw. ist dort nicht erlaubt.

---

# Typischer Fehler: Kein Inter-VLAN-Routing

PC aus VLAN 10:

```text
192.168.10.10
```

PC aus VLAN 20:

```text
192.168.20.10
```

Beide PCs funktionieren innerhalb ihres eigenen VLANs.

Eine Kommunikation zwischen den VLANs funktioniert jedoch nicht.

Mögliche Ursache:

> Es existiert kein funktionierendes Inter-VLAN-Routing.

---

# Typischer Fehler: Falsches Default Gateway

PC:

```text
IP:       192.168.10.50
Maske:    255.255.255.0
Gateway:  192.168.20.1
```

Das Gateway liegt in einem anderen Subnetz.

Das ist eine fehlerhafte Konfiguration.

Ein mögliches Gateway wäre:

```text
192.168.10.1
```

---

# Typischer Fehler: Native VLAN stimmt nicht überein

Bei einem Trunk sind auf den beiden Seiten unterschiedliche Native VLANs konfiguriert.

```text
Switch A                  Switch B

Native VLAN 10  --------  Native VLAN 20
```

Dies kann zu VLAN-Mismatch-Problemen führen.

Die Konfiguration sollte auf beiden Seiten konsistent sein.

---

# Prüfungsrelevante Inhalte AP1

Für AP1 solltest du besonders sicher beherrschen:

### Switching

* Funktion eines Switches
* MAC-Adresse
* MAC-Tabelle
* Ethernet-Frame
* Layer 2
* Unicast
* Broadcast
* Multicast
* Flooding
* Unterschied Hub / Switch / Router

### VLAN

* Definition VLAN
* VLAN-ID
* Broadcast-Domäne
* Gründe für VLANs
* Access-Port
* Trunk-Port
* 802.1Q
* VLAN-Tag

### Typische AP1-Fragen

> Welche Adresse verwendet ein Layer-2-Switch zur Weiterleitung?

**MAC-Adresse**

> Wie lernt ein Switch eine MAC-Adresse?

**Über die Quell-MAC-Adresse eines eingehenden Frames.**

> Was passiert bei einer unbekannten Ziel-MAC-Adresse?

**Flooding innerhalb des entsprechenden Layer-2-Bereichs.**

> Was ist ein VLAN?

**Eine logische Unterteilung eines Layer-2-Netzwerks.**

> Was ist ein Trunk?

**Eine Verbindung, über die mehrere VLANs übertragen werden können.**

---

# Prüfungsrelevante Inhalte AP2

Für AP2 solltest du zusätzlich beherrschen:

* VLAN-Konzeption
* VLAN-Zuordnung
* Access-/Trunk-Konfiguration
* 802.1Q
* Native VLAN
* Inter-VLAN-Routing
* Router-on-a-Stick
* Layer-3-Switching
* SVI
* Default Gateway
* IP-Subnetze pro VLAN
* Netzwerksegmentierung
* ACLs
* Firewall-Zusammenhänge
* Fehleranalyse
* Planung eines Unternehmensnetzwerks

---

# Praxisbeispiele

## Beispiel 1: Unternehmensnetzwerk

Ein Unternehmen besitzt:

* Verwaltung
* Entwicklung
* Server
* Gäste

### VLAN-Plan

| VLAN | Abteilung   | Netzwerk        | Gateway      |
| ---: | ----------- | --------------- | ------------ |
|   10 | Verwaltung  | 192.168.10.0/24 | 192.168.10.1 |
|   20 | Entwicklung | 192.168.20.0/24 | 192.168.20.1 |
|   30 | Server      | 192.168.30.0/24 | 192.168.30.1 |
|   40 | Gäste       | 192.168.40.0/24 | 192.168.40.1 |
|   99 | Management  | 192.168.99.0/24 | 192.168.99.1 |

---

## Beispiel 2: Switch-Verbindungen

```text
                    Layer-3-Switch
                         |
                 +-------+-------+
                 |       |       |
              VLAN 10 VLAN 20 VLAN 30
                 |       |       |
                PCs     PCs    Server
```

Die Verbindungen zu den Endgeräten sind normalerweise Access-Ports.

---

## Beispiel 3: Zwei Switches

```text
PCs VLAN 10
    |
Switch A
    |
    | 802.1Q Trunk
    |
Switch B
    |
PCs VLAN 10
```

Der Trunk ermöglicht es, VLAN 10 über die Verbindung zwischen den Switches zu transportieren.

Wenn zusätzlich VLAN 20 benötigt wird:

```text
Switch A
    |
    | VLAN 10 + VLAN 20
    |
Switch B
```

muss VLAN 20 entsprechend auf dem Trunk zugelassen und auf den Switches korrekt eingerichtet sein.

---

# Prüfungsfallen

## Prüfungsfalle 1

> „Ein Switch arbeitet mit IP-Adressen.“

**Nicht grundsätzlich.**

Ein klassischer Layer-2-Switch verwendet hauptsächlich MAC-Adressen.

---

## Prüfungsfalle 2

> „Jedes VLAN ist ein eigenes physisches Netzwerk.“

**Falsch.**

Ein VLAN ist eine **logische** Netzwerksegmentierung.

---

## Prüfungsfalle 3

> „Ein Access-Port kann beliebig viele VLANs übertragen.“

**Falsch.**

Ein klassischer Access-Port ist einem einzelnen VLAN zugeordnet.

---

## Prüfungsfalle 4

> „Ein Trunk ist nur für Internetzugang notwendig.“

**Falsch.**

Trunks werden beispielsweise verwendet, um mehrere VLANs zwischen Netzwerkkomponenten zu übertragen.

---

## Prüfungsfalle 5

> „VLAN 10 und VLAN 20 können direkt miteinander kommunizieren.“

**Nicht auf Layer 2.**

Dafür wird Inter-VLAN-Routing benötigt.

---

## Prüfungsfalle 6

> „VLANs ersetzen Firewalls.“

**Falsch.**

VLANs segmentieren das Netzwerk. Eine Firewall oder ACL kann zusätzlich den Datenverkehr kontrollieren.

---

## Prüfungsfalle 7

> „802.1Q ist ein Routing-Protokoll.“

**Falsch.**

802.1Q ist ein Standard für VLAN-Tagging auf Ethernet-Verbindungen.

---

# Prüfungsfragen zum Üben

## Grundlagen

### Frage 1

Auf welcher OSI-Schicht arbeitet ein klassischer Layer-2-Switch?

<details>
<summary>Antwort anzeigen</summary>

Layer 2 – Sicherungsschicht.

</details>

---

### Frage 2

Welche Adresse verwendet ein Switch hauptsächlich zur Weiterleitung von Ethernet-Frames?

<details>
<summary>Antwort anzeigen</summary>

Die MAC-Adresse.

</details>

---

### Frage 3

Wie lernt ein Switch eine MAC-Adresse?

<details>
<summary>Antwort anzeigen</summary>

Er untersucht die Quell-MAC-Adresse eingehender Frames und ordnet sie dem Eingangsport zu.

</details>

---

### Frage 4

Was passiert, wenn die Ziel-MAC-Adresse unbekannt ist?

<details>
<summary>Antwort anzeigen</summary>

Der Switch führt Flooding durch und sendet den Frame über die entsprechenden Ports, außer über den Eingangsport.

</details>

---

### Frage 5

Was ist der Unterschied zwischen einem Hub und einem Switch?

<details>
<summary>Antwort anzeigen</summary>

Ein Hub arbeitet auf Layer 1 und leitet Signale grundsätzlich an mehrere bzw. alle anderen Ports weiter. Ein Switch arbeitet auf Layer 2 und kann Frames anhand von MAC-Adressen gezielt weiterleiten.

</details>

---

## VLAN

### Frage 6

Was bedeutet VLAN?

<details>
<summary>Antwort anzeigen</summary>

Virtual Local Area Network.

</details>

---

### Frage 7

Welche Vorteile haben VLANs?

<details>
<summary>Antwort anzeigen</summary>

Zum Beispiel:

* logische Netzwerksegmentierung
* kleinere Broadcast-Domänen
* bessere Strukturierung
* Trennung von Benutzergruppen
* zusätzliche Sicherheitsmöglichkeiten
* flexiblere Netzwerkplanung

</details>

---

### Frage 8

Was ist eine Broadcast-Domäne?

<details>
<summary>Antwort anzeigen</summary>

Der Bereich eines Layer-2-Netzwerks, in dem sich Broadcasts ausbreiten.

</details>

---

### Frage 9

Wie viele Broadcast-Domänen entstehen bei drei getrennten VLANs?

<details>
<summary>Antwort anzeigen</summary>

Grundsätzlich drei Broadcast-Domänen.

</details>

---

### Frage 10

Was ist ein Access-Port?

<details>
<summary>Antwort anzeigen</summary>

Ein Switch-Port, der typischerweise einem einzelnen VLAN zugeordnet ist und beispielsweise ein Endgerät verbindet.

</details>

---

### Frage 11

Was ist ein Trunk-Port?

<details>
<summary>Antwort anzeigen</summary>

Ein Port, über den mehrere VLANs übertragen werden können.

</details>

---

### Frage 12

Wofür wird IEEE 802.1Q verwendet?

<details>
<summary>Antwort anzeigen</summary>

Für VLAN-Tagging in Ethernet-Frames.

</details>

---

### Frage 13

Was ist ein Native VLAN?

<details>
<summary>Antwort anzeigen</summary>

Das VLAN eines 802.1Q-Trunks, dessen Frames typischerweise ohne VLAN-Tag übertragen werden.

</details>

---

# Inter-VLAN-Routing

### Frage 14

Können zwei Geräte in unterschiedlichen VLANs direkt auf Layer 2 miteinander kommunizieren?

<details>
<summary>Antwort anzeigen</summary>

Nein. Für die Kommunikation zwischen unterschiedlichen VLANs wird Routing benötigt.

</details>

---

### Frage 15

Was ist Inter-VLAN-Routing?

<details>
<summary>Antwort anzeigen</summary>

Routing zwischen unterschiedlichen VLANs bzw. deren IP-Netzen.

</details>

---

### Frage 16

Was ist Router-on-a-Stick?

<details>
<summary>Antwort anzeigen</summary>

Eine Methode für Inter-VLAN-Routing, bei der ein Router über eine physische Schnittstelle mit mehreren logischen Subinterfaces mehrere VLANs routet.

</details>

---

### Frage 17

Was ist ein SVI?

<details>
<summary>Antwort anzeigen</summary>

Ein Switched Virtual Interface ist eine virtuelle Layer-3-Schnittstelle eines Switches, die beispielsweise als Gateway für ein VLAN verwendet werden kann.

</details>

---

### Frage 18

Welche Aufgabe hat das Default Gateway?

<details>
<summary>Antwort anzeigen</summary>

Es ermöglicht einem Host, Daten an Ziele außerhalb seines eigenen IP-Netzes zu senden.

</details>

---

# Fehleranalyse

### Frage 19

Zwei PCs befinden sich laut Planung im gleichen VLAN, können sich aber nicht erreichen. Welche Punkte prüfst du?

<details>
<summary>Antwort anzeigen</summary>

Zum Beispiel:

1. Kabel und Link
2. Switch-Port
3. VLAN-Zuordnung
4. IP-Adresse
5. Subnetzmaske
6. Netzwerkkarte
7. Firewall
8. MAC-Tabelle

</details>

---

### Frage 20

VLAN 10 funktioniert zwischen zwei Switches, VLAN 20 jedoch nicht. Welche Ursache ist wahrscheinlich?

<details>
<summary>Antwort anzeigen</summary>

Möglicherweise wird VLAN 20 nicht über den Trunk übertragen oder ist auf einem der Switches nicht korrekt eingerichtet.

</details>

---

### Frage 21

Ein PC aus VLAN 10 kann einen PC aus VLAN 20 nicht erreichen. Was musst du prüfen?

<details>
<summary>Antwort anzeigen</summary>

Unter anderem:

* Inter-VLAN-Routing
* Default Gateway
* IP-Konfiguration
* Routing
* ACLs
* Firewall-Regeln

</details>

---

### Frage 22

Warum sollte ein Gäste-VLAN vom Verwaltungsnetz getrennt werden?

<details>
<summary>Antwort anzeigen</summary>

Um den Zugriff von Gastgeräten auf interne Systeme zu begrenzen und die Netzwerksegmentierung bzw. Sicherheit zu verbessern.

</details>

---

# Mini-Prüfung

## Aufgabe 1 – Switching

Ein Switch erhält einen Frame.

Die Quell-MAC-Adresse lautet:

```text
AA:AA:AA:AA:AA:01
```

Der Frame kommt über Port:

```text
Gi0/1
```

### Frage

Welche Information kann der Switch daraus lernen?

<details>
<summary>▶ Lösung</summary>

Der Switch kann speichern:

```text
AA:AA:AA:AA:AA:01 → Gi0/1
```

Er lernt die MAC-Adresse anhand der **Quell-MAC-Adresse**.

</details>

---

# Aufgabe 2 – Unbekannte MAC-Adresse

Ein Switch kennt die Ziel-MAC-Adresse eines Frames noch nicht.

### Frage

Was passiert?

<details>
<summary>▶ Lösung</summary>

Der Switch führt Flooding durch und sendet den Frame über die entsprechenden Ports, außer über den Eingangsport.

</details>

---

# Aufgabe 3 – VLAN

Ein Unternehmen besitzt:

```text
VLAN 10 → Verwaltung
VLAN 20 → Entwicklung
```

### Frage

Was ist ein wesentlicher Vorteil dieser Aufteilung?

<details>
<summary>▶ Lösung</summary>

Die Abteilungen werden logisch voneinander getrennt und befinden sich in unterschiedlichen Layer-2-Broadcast-Domänen.

</details>

---

# Aufgabe 4 – Trunk

Zwei Switches müssen folgende VLANs miteinander transportieren:

```text
VLAN 10
VLAN 20
VLAN 30
```

### Frage

Welcher Porttyp wird für die Verbindung verwendet?

<details>
<summary>▶ Lösung</summary>

Ein **Trunk-Port**.

Über den Trunk können mehrere VLANs übertragen werden.

</details>

---

# Aufgabe 5 – 802.1Q

### Frage

Welche Funktion hat IEEE 802.1Q?

<details>
<summary>▶ Lösung</summary>

IEEE 802.1Q definiert unter anderem das VLAN-Tagging von Ethernet-Frames.

</details>

---

# Aufgabe 6 – Inter-VLAN-Routing

Gegeben:

```text
VLAN 10:
192.168.10.0/24

VLAN 20:
192.168.20.0/24
```

PC1:

```text
192.168.10.10
```

PC2:

```text
192.168.20.10
```

PC1 und PC2 sollen miteinander kommunizieren.

### Frage

Was wird benötigt?

<details>
<summary>▶ Lösung</summary>

Es wird **Inter-VLAN-Routing** benötigt.

Dies kann beispielsweise über:

* einen Router
* Router-on-a-Stick
* einen Layer-3-Switch

realisiert werden.

</details>

---

# Aufgabe 7 – Gateway

PC1 besitzt:

```text
IP-Adresse:
192.168.10.50

Subnetzmaske:
255.255.255.0

Gateway:
192.168.20.1
```

### Frage

Ist die Gateway-Konfiguration sinnvoll?

<details>
<summary>▶ Lösung</summary>

Nein.

Bei einem `/24`-Netz gehört der PC zum Netzwerk:

```text
192.168.10.0/24
```

Das Gateway sollte sich normalerweise ebenfalls in diesem Netzwerk befinden, beispielsweise:

```text
192.168.10.1
```

</details>

---

# Aufgabe 8 – Fehleranalyse

Zwei Switches sind verbunden.

```text
Switch A ===== Switch B
```

VLAN 10 funktioniert.

VLAN 20 funktioniert nicht.

### Frage

Nenne mindestens drei mögliche Ursachen.

<details>
<summary>▶ Lösung</summary>

Mögliche Ursachen:

1. VLAN 20 existiert auf einem Switch nicht.
2. VLAN 20 ist auf dem Trunk nicht erlaubt.
3. Der Port ist nicht korrekt als Trunk konfiguriert.
4. Die Access-Ports der Endgeräte sind dem falschen VLAN zugeordnet.
5. Es liegt eine fehlerhafte VLAN-Konfiguration vor.

</details>

---

# Aufgabe 9 – Unternehmensnetzwerk

Ein Unternehmen benötigt folgende Netzwerke:

* Verwaltung
* Entwicklung
* Server
* Gäste

### Aufgabe

Erstelle eine sinnvolle VLAN-Struktur.

<details>
<summary>▶ Lösung</summary>

Eine mögliche Lösung:

| VLAN | Zweck       | Netzwerk        |
| ---: | ----------- | --------------- |
|   10 | Verwaltung  | 192.168.10.0/24 |
|   20 | Entwicklung | 192.168.20.0/24 |
|   30 | Server      | 192.168.30.0/24 |
|   40 | Gäste       | 192.168.40.0/24 |

Zusätzlich kann ein separates Management-VLAN, beispielsweise VLAN 99, verwendet werden.

</details>

---

# Aufgabe 10 – Sicherheit

Das Gäste-VLAN soll Internetzugriff haben, aber nicht auf die Verwaltung zugreifen können.

### Frage

Welche technischen Möglichkeiten gibt es?

<details>
<summary>▶ Lösung</summary>

Beispielsweise:

* Firewall-Regeln
* ACLs
* Routing-Regeln
* Netzwerksegmentierung

Das VLAN sorgt für die logische Trennung; die Zugriffskontrolle wird durch entsprechende Sicherheitsregeln umgesetzt.

</details>

---

# Zusammenfassung

## Switching

* Ein Switch verbindet Geräte innerhalb eines Netzwerks.
* Ein klassischer Layer-2-Switch arbeitet auf Layer 2.
* Ein Switch verwendet MAC-Adressen zur Frame-Weiterleitung.
* Der Switch lernt MAC-Adressen anhand der **Quell-MAC-Adresse**.
* Die MAC-Tabelle ordnet MAC-Adressen Switch-Ports zu.
* Bekannte Ziel-MAC → gezielte Weiterleitung.
* Unbekannte Ziel-MAC → Flooding.
* Broadcast → Weiterleitung innerhalb der Broadcast-Domäne.

## VLAN

* VLAN steht für **Virtual Local Area Network**.
* VLANs ermöglichen logische Netzwerksegmentierung.
* Jedes VLAN bildet grundsätzlich eine eigene Broadcast-Domäne.
* VLANs können beispielsweise Abteilungen oder Sicherheitszonen voneinander trennen.
* Ein Access-Port gehört typischerweise zu einem VLAN.
* Ein Trunk kann mehrere VLANs transportieren.
* IEEE 802.1Q wird für VLAN-Tagging verwendet.
* Das Native VLAN wird auf einem 802.1Q-Trunk normalerweise untagged übertragen.

## Routing

* Unterschiedliche VLANs können nicht direkt auf Layer 2 miteinander kommunizieren.
* Für die Kommunikation zwischen VLANs wird Routing benötigt.
* Inter-VLAN-Routing kann über einen Router oder Layer-3-Switch erfolgen.
* Router-on-a-Stick verwendet mehrere Subinterfaces.
* Ein Layer-3-Switch kann Routing direkt übernehmen.
* Ein SVI kann als Gateway für ein VLAN verwendet werden.
* Das Default Gateway ermöglicht die Kommunikation in andere IP-Netze.

## Prüfung

Für die AP1/AP2 solltest du insbesondere diese Zusammenhänge sicher beherrschen:

```text
MAC-Adresse
     ↓
Switch
     ↓
MAC-Tabelle
     ↓
Frame-Weiterleitung

VLAN
     ↓
Broadcast-Domäne
     ↓
Access / Trunk
     ↓
802.1Q

VLAN 10 ─────┐
             │
          Routing
             │
VLAN 20 ─────┘
     ↓
Inter-VLAN-Routing
```

---

# Prüfungs-Merksätze

> **Switch → MAC-Adresse**

> **Router → IP-Adresse**

> **Layer 2 → MAC**

> **Layer 3 → IP**

> **Access-Port → normalerweise ein VLAN**

> **Trunk → mehrere VLANs**

> **802.1Q → VLAN-Tagging**

> **VLAN → eigene Broadcast-Domäne**

> **Verschiedene VLANs → Routing erforderlich**

> **SVI → virtuelle Layer-3-Schnittstelle**

> **Default Gateway → Weg in andere IP-Netze**

> **MAC-Tabelle → MAC-Adresse ↔ Switch-Port**

> **Unbekannte Ziel-MAC → Flooding**

---

# Quellen

* IEEE – IEEE 802.1 Standards für Bridging und VLANs
* Cisco – Switching, VLAN und Inter-VLAN-Routing Dokumentation
* RFC 826 – Address Resolution Protocol (ARP)
* ISO/IEC 7498-1 – OSI Basic Reference Model
* IEEE 802.3 – Ethernet


## Wichtige Begriffe

| Begriff | Definition |
|---------|------------|
| | |

## Prüfungsrelevante Inhalte

<!-- TODO: Wichtige Prüfungspunkte ergänzen -->

## Beispiele / Praxisbezug

<!-- TODO: Praktische Beispiele ergänzen -->

## Zusammenfassung

<!-- TODO: Kurze Zusammenfassung -->

## Prüfungsfragen zum Üben

- [ ] Frage 1?
- [ ] Frage 2?

## Quellen

- [ ] Noch keine Quellen

---
[↩ Zurück zur Übersicht](../README.md) | [Vorheriges Thema](05_Routing_Protokolle.md) | [Nächstes Thema](07_WLAN_Standards_Konfiguration.md)
