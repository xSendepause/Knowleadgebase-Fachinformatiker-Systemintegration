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

Nach Bearbeitung dieses Themas kannst du:

* die Aufgaben und Funktionsweise eines Switches erklären.
* den Unterschied zwischen **Hub, Switch und Router** erklären.
* erklären, wie ein Switch anhand von **MAC-Adressen** Frames weiterleitet.
* die **MAC-Adress-Tabelle (CAM-Tabelle)** eines Switches erklären.
* **Unicast, Broadcast und Multicast** unterscheiden.
* erklären, was ein **VLAN** ist und warum VLANs eingesetzt werden.
* **Access-Port und Trunk-Port** unterscheiden.
* die Funktion von **IEEE 802.1Q (VLAN-Tagging)** erklären.
* VLANs sinnvoll in einem Netzwerk planen und konfigurieren.
* erklären, warum Geräte in unterschiedlichen VLANs nicht direkt miteinander kommunizieren können.
* die Funktion von **Inter-VLAN-Routing** erklären.
* typische Fehler bei VLAN-Konfigurationen erkennen und systematisch analysieren.
* typische Prüfungsaufgaben zu Switching und VLAN lösen.

---

## Grundlagen

### Was ist Switching?

Ein **Switch** verbindet Netzwerkgeräte innerhalb eines lokalen Netzwerks (LAN).

Ein Switch arbeitet hauptsächlich auf **Schicht 2 (Sicherungsschicht)** des OSI-Modells und verwendet **MAC-Adressen**, um Ethernet-Frames gezielt weiterzuleiten.

Beispiel:

```text
PC 1 ───┐
        │
PC 2 ───┤
        │
      Switch
        │
PC 3 ───┘
```

Im Gegensatz zu einem Hub sendet ein Switch einen bekannten Unicast-Frame normalerweise **nur an den Port, an dem sich das Zielgerät befindet**.

### Wie lernt ein Switch MAC-Adressen?

Ein Switch baut automatisch eine **MAC-Adress-Tabelle** auf.

Dazu untersucht er die **Quell-MAC-Adresse** eingehender Ethernet-Frames.

Beispiel:

| Port  | MAC-Adresse       |
| ----- | ----------------- |
| Gi0/1 | AA:AA:AA:AA:AA:01 |
| Gi0/2 | BB:BB:BB:BB:BB:02 |
| Gi0/3 | CC:CC:CC:CC:CC:03 |

Kommt ein Frame von MAC `AA:AA:AA:AA:AA:01` an Port `Gi0/1`, merkt sich der Switch:

> MAC AA:AA:AA:AA:AA:01 befindet sich an Port Gi0/1.

### Weiterleitung eines Frames

Der Switch betrachtet die **Ziel-MAC-Adresse**.

**Ziel-MAC bekannt:**

```text
PC 1 → Switch → PC 3
             X
           PC 2
```

Der Switch leitet den Frame nur an den passenden Port weiter.

**Ziel-MAC unbekannt:**

Der Switch führt ein **Flooding** durch und sendet den Frame an alle passenden Ports außer dem Eingangsport.

---

## Hub vs. Switch vs. Router

| Gerät  | Hauptaufgabe                       | Typische OSI-Schicht | Adressierung |
| ------ | ---------------------------------- | -------------------: | ------------ |
| Hub    | Weiterleitung an alle Ports        |              Layer 1 | keine        |
| Switch | Weiterleitung innerhalb eines LANs |              Layer 2 | MAC-Adresse  |
| Router | Weiterleitung zwischen Netzwerken  |              Layer 3 | IP-Adresse   |

> **Prüfungstipp:**
> „MAC-Adresse“ → typischerweise **Switch / Layer 2**
> „IP-Adresse / Routing“ → typischerweise **Router / Layer 3**

---

# VLAN

## Was ist ein VLAN?

**VLAN** steht für **Virtual Local Area Network**.

Mit VLANs kann ein physisches Netzwerk logisch in mehrere getrennte Netzwerke aufgeteilt werden.

Beispiel ohne VLAN:

```text
             Switch
          /    |    \
        PC1   PC2   PC3
```

Alle Geräte befinden sich im gleichen Layer-2-Netz.

Mit VLANs:

```text
             Switch
          /    |    \
       PC1    PC2    PC3
       VLAN10 VLAN20 VLAN10
```

PC1 und PC3 gehören zu VLAN 10.

PC2 gehört zu VLAN 20.

### Vorteile von VLANs

* logische Trennung von Netzwerken
* kleinere Broadcast-Domänen
* bessere Übersicht und Netzwerkstruktur
* Trennung verschiedener Abteilungen
* Verbesserung der Sicherheit
* flexible Netzwerkplanung unabhängig von der physischen Verkabelung

Beispiel:

| VLAN | Zweck       | Beispiel                   |
| ---: | ----------- | -------------------------- |
|   10 | Verwaltung  | Mitarbeiter-PCs            |
|   20 | Entwicklung | Entwickler-PCs             |
|   30 | Gäste       | Gastgeräte                 |
|   40 | Server      | Server                     |
|   99 | Management  | Switch-/Netzwerkmanagement |

---

# Broadcast-Domänen

Ein wichtiger Prüfungsaspekt ist die **Broadcast-Domäne**.

Ein Broadcast wird innerhalb eines VLANs verteilt.

Beispiel:

```text
VLAN 10
PC1 ── PC2 ── PC3
 ↑      ↑      ↑
 └──── Broadcast ────┘
```

Ein Broadcast aus VLAN 10 erreicht **nicht automatisch VLAN 20**.

Damit wird jedes VLAN zu einer eigenen **Broadcast-Domäne**.

> **Merksatz:**
> **Ein VLAN = eine eigene Layer-2-Broadcast-Domäne.**

---

# VLAN-Ports

## Access-Port

Ein **Access-Port** gehört normalerweise zu **einem VLAN**.

Typischer Einsatz:

* PC
* Drucker
* Server
* IP-Telefon (je nach Konfiguration)

Beispiel:

```text
PC ───── Access-Port ───── Switch
                         VLAN 10
```

Der Endgeräte-Port transportiert dabei normalerweise **untagged Ethernet Frames**.

---

## Trunk-Port

Ein **Trunk-Port** kann **mehrere VLANs gleichzeitig** übertragen.

Typischer Einsatz:

```text
Switch A ───────── Trunk ───────── Switch B
          VLAN 10, 20, 30, 40
```

Trunks werden beispielsweise verwendet für:

* Switch ↔ Switch
* Switch ↔ Router
* Switch ↔ Layer-3-Switch
* Switch ↔ Virtualisierungsserver

---

# IEEE 802.1Q

**IEEE 802.1Q** ist ein Standard für VLAN-Tagging in Ethernet-Frames.

Bei einem Trunk können Frames mit einem VLAN-Tag versehen werden.

Vereinfacht:

```text
Ethernet-Frame
┌────────┬──────────┬────────┬───────┐
│ Ziel   │ Quelle   │ VLAN   │ Daten │
│ MAC    │ MAC      │ Tag    │       │
└────────┴──────────┴────────┴───────┘
```

Der VLAN-Tag enthält unter anderem die **VLAN-ID**.

### VLAN-ID

Bei IEEE 802.1Q stehen grundsätzlich **12 Bit für die VLAN-ID** zur Verfügung.

Damit sind theoretisch VLAN-IDs von **0 bis 4095** darstellbar.

Nicht alle Werte können jedoch als normale VLAN-Nummer verwendet werden.

> **Prüfungsrelevant:**
> **802.1Q = VLAN-Tagging**

---

# Native VLAN

Bei 802.1Q kann ein Trunk ein sogenanntes **Native VLAN** verwenden.

Frames dieses VLANs werden auf dem Trunk typischerweise **ohne VLAN-Tag** übertragen.

> **Prüfung:** Native VLAN nicht mit „VLAN 1“ gleichsetzen.
> VLAN 1 ist häufig standardmäßig vorhanden, muss aber nicht zwangsläufig das Native VLAN sein.

---

# Kommunikation zwischen VLANs

Geräte in unterschiedlichen VLANs können nicht einfach auf Layer 2 miteinander kommunizieren.

Beispiel:

```text
VLAN 10                VLAN 20

PC1 ── Switch ── X ── PC2
```

PC1 kann PC2 nicht direkt über Layer 2 erreichen.

Für die Kommunikation wird **Routing zwischen den VLANs** benötigt.

---

# Inter-VLAN-Routing

**Inter-VLAN-Routing** ermöglicht die Kommunikation zwischen unterschiedlichen VLANs.

Möglichkeiten:

### 1. Router-on-a-Stick

Ein Router verwendet eine physische Schnittstelle mit mehreren logischen Subinterfaces.

```text
             Router
          /          \
      VLAN 10       VLAN 20
          \          /
             Trunk
               |
             Switch
```

Der Switch-Port zum Router ist ein **Trunk-Port**.

### 2. Layer-3-Switch

Ein Layer-3-Switch kann Routing direkt durchführen.

```text
VLAN 10 ──┐
          │
       L3-Switch
          │
VLAN 20 ──┘
```

Hier werden typischerweise **SVIs (Switched Virtual Interfaces)** als Gateway für die VLANs verwendet.

---

# VLAN und IP-Adressierung

In der Praxis wird häufig jedem VLAN ein eigenes IP-Subnetz zugeordnet.

Beispiel:

| VLAN | Netzwerk        | Gateway      |
| ---: | --------------- | ------------ |
|   10 | 192.168.10.0/24 | 192.168.10.1 |
|   20 | 192.168.20.0/24 | 192.168.20.1 |
|   30 | 192.168.30.0/24 | 192.168.30.1 |

Beispiel:

```text
PC1
VLAN 10
192.168.10.10/24
Gateway: 192.168.10.1

        ↓

    L3-Switch

        ↓

PC2
VLAN 20
192.168.20.10/24
Gateway: 192.168.20.1
```

Die Kommunikation zwischen den Subnetzen erfolgt über Routing.

---

# Wichtige Begriffe

| Begriff                       | Definition                                                            |
| ----------------------------- | --------------------------------------------------------------------- |
| **Switch**                    | Netzwerkgerät zur Weiterleitung von Ethernet-Frames                   |
| **MAC-Adresse**               | Hardware-/Layer-2-Adresse einer Netzwerkschnittstelle                 |
| **MAC-Tabelle / CAM-Tabelle** | Tabelle, die MAC-Adressen den Switch-Ports zuordnet                   |
| **Frame**                     | Datenübertragungseinheit auf Layer 2                                  |
| **Broadcast**                 | Nachricht an alle Teilnehmer einer Broadcast-Domäne                   |
| **Unicast**                   | Kommunikation von einem Sender zu genau einem Empfänger               |
| **Multicast**                 | Kommunikation von einem Sender an eine bestimmte Empfängergruppe      |
| **VLAN**                      | Logische Unterteilung eines Layer-2-Netzwerks                         |
| **VLAN-ID**                   | Nummer zur Identifikation eines VLANs                                 |
| **Access-Port**               | Switch-Port für ein einzelnes VLAN                                    |
| **Trunk-Port**                | Port zur Übertragung mehrerer VLANs                                   |
| **802.1Q**                    | Standard für VLAN-Tagging                                             |
| **Native VLAN**               | VLAN, dessen Frames auf einem 802.1Q-Trunk untagged übertragen werden |
| **Broadcast-Domäne**          | Bereich, in dem sich Layer-2-Broadcasts ausbreiten                    |
| **Inter-VLAN-Routing**        | Routing zwischen verschiedenen VLANs                                  |
| **SVI**                       | Virtuelle Layer-3-Schnittstelle eines Switches                        |
| **Default Gateway**           | Router/L3-Gerät, über das ein Host andere IP-Netze erreicht           |

---

# Prüfungsrelevante Inhalte

## Besonders wichtig für AP1

Diese Themen solltest du sicher beherrschen:

* Funktion eines Switches
* MAC-Adressen
* MAC-Adress-Tabelle
* Unterschied Hub / Switch / Router
* OSI-Schichten
* Ethernet-Frames
* Unicast / Broadcast / Multicast
* VLAN-Grundlagen
* Broadcast-Domänen
* Access-Port
* Trunk-Port
* VLAN-ID
* 802.1Q

### Typische AP1-Aufgabe

> Ein Switch erhält einen Ethernet-Frame. Die Ziel-MAC-Adresse ist bereits in seiner MAC-Tabelle bekannt. Was macht der Switch?

**Antwort:**
Er leitet den Frame gezielt über den Port weiter, der der Ziel-MAC-Adresse zugeordnet ist.

---

## Besonders wichtig für AP2

Für AP2 solltest du zusätzlich sicher beherrschen:

* VLAN-Konzeption
* VLAN-Zuordnung
* Access-/Trunk-Konfiguration
* 802.1Q
* Inter-VLAN-Routing
* Router-on-a-Stick
* Layer-3-Switching
* SVI
* IP-Subnetze pro VLAN
* Default Gateway
* VLAN-Fehleranalyse
* Netzwerksegmentierung
* Sicherheitsaspekte von VLANs
* Planung eines strukturierten Unternehmensnetzwerks

---

# Praxisbeispiel

Ein Unternehmen hat drei Abteilungen:

* Verwaltung
* Entwicklung
* Gäste

Das Netzwerk soll logisch getrennt werden.

### VLAN-Plan

| VLAN | Abteilung   | Netzwerk        |
| ---: | ----------- | --------------- |
|   10 | Verwaltung  | 192.168.10.0/24 |
|   20 | Entwicklung | 192.168.20.0/24 |
|   30 | Gäste       | 192.168.30.0/24 |

Auf einem Switch:

```text
PC Verwaltung
     │
     │ Access
     ▼
┌─────────────┐
│   Switch    │
│             │
│ VLAN 10     │
│ VLAN 20     │
│ VLAN 30     │
└──────┬──────┘
       │
       │ Trunk
       │ 802.1Q
       ▼
 ┌────────────┐
 │ L3-Switch  │
 └────────────┘
```

Die VLANs sind logisch voneinander getrennt.

Der Layer-3-Switch kann kontrolliert zwischen ihnen routen.

Zusätzlich können **ACLs (Access Control Lists)** eingesetzt werden.

Beispiel:

```text
Verwaltung ──→ Server       erlaubt
Entwicklung ─→ Server       erlaubt
Gäste ───────→ Internet     erlaubt
Gäste ───────→ Verwaltung   verboten
```

---

# Typische Fehleranalyse

## Fehler 1: PC erreicht andere PCs im gleichen VLAN nicht

Mögliche Ursachen:

* falsches VLAN am Access-Port
* falsche Verkabelung
* Netzwerkkarte deaktiviert
* falsche IP-Adresse
* falsche Subnetzmaske
* Port administrativ deaktiviert

---

## Fehler 2: VLAN funktioniert über mehrere Switches nicht

Mögliche Ursachen:

* Verbindung zwischen Switches ist kein Trunk
* VLAN wurde auf einem Switch nicht angelegt
* VLAN ist auf dem Trunk nicht erlaubt
* falsche VLAN-Konfiguration
* Native-VLAN-Konfiguration stimmt nicht überein

---

## Fehler 3: Unterschiedliche VLANs können nicht miteinander kommunizieren

Mögliche Ursachen:

* kein Inter-VLAN-Routing
* falsches Default Gateway
* falsche IP-Konfiguration
* Routing fehlt
* ACL/Firewall blockiert den Datenverkehr

> **Prüfungsstrategie:**
> Bei Netzwerkfehlern systematisch von **Layer 1 → Layer 2 → Layer 3** prüfen.

```text
Layer 1
Kabel / Link / Port
       ↓
Layer 2
VLAN / MAC / Trunk
       ↓
Layer 3
IP / Subnetz / Gateway / Routing
       ↓
Firewall / ACL
```

---

# Prüfungsfallen

### ❌ „Ein VLAN ist ein eigenes physisches Netzwerk.“

Nicht zwingend.

Ein VLAN ist eine **logische Segmentierung** eines physischen Netzwerks.

### ❌ „Ein Trunk gehört nur zu einem VLAN.“

Falsch.

Ein Trunk kann **mehrere VLANs transportieren**.

### ❌ „VLANs können immer miteinander kommunizieren.“

Falsch.

Für die Kommunikation zwischen VLANs wird **Routing** benötigt.

### ❌ „Ein Switch arbeitet nur mit IP-Adressen.“

Falsch.

Ein klassischer Layer-2-Switch verwendet hauptsächlich **MAC-Adressen**.

### ❌ „Ein Router ersetzt immer einen Switch.“

Falsch.

Router und Switches erfüllen unterschiedliche Aufgaben.

---

# Zusammenfassung

* Ein **Switch** verbindet Geräte innerhalb eines LANs.
* Ein Switch arbeitet auf Layer 2 hauptsächlich mit **MAC-Adressen**.
* Die **MAC-Tabelle** ordnet MAC-Adressen Switch-Ports zu.
* Ein **VLAN** trennt ein Netzwerk logisch in verschiedene Layer-2-Netze.
* Jedes VLAN bildet grundsätzlich eine eigene **Broadcast-Domäne**.
* Ein **Access-Port** transportiert normalerweise ein VLAN.
* Ein **Trunk-Port** transportiert mehrere VLANs.
* **IEEE 802.1Q** ermöglicht VLAN-Tagging.
* VLANs werden häufig mit eigenen **IP-Subnetzen** kombiniert.
* Kommunikation zwischen VLANs benötigt **Inter-VLAN-Routing**.
* Dafür können Router, Router-on-a-Stick oder Layer-3-Switches verwendet werden.
* **SVIs** ermöglichen auf Layer-3-Switches Routing für VLANs.
* **ACLs** können den Datenverkehr zwischen VLANs zusätzlich kontrollieren.
* Für die Prüfung sind besonders **Access vs. Trunk, 802.1Q, Broadcast-Domänen, MAC-Tabellen und Inter-VLAN-Routing** wichtig.

---

# Prüfungsfragen zum Üben

### Grundlagen

1. Auf welcher OSI-Schicht arbeitet ein klassischer Layer-2-Switch?
2. Welche Adresse verwendet ein Switch zur Weiterleitung eines Ethernet-Frames?
3. Wie lernt ein Switch die MAC-Adresse eines Geräts?
4. Was passiert, wenn die Ziel-MAC-Adresse noch nicht in der MAC-Tabelle vorhanden ist?
5. Was ist der Unterschied zwischen Unicast, Broadcast und Multicast?
6. Was ist der Unterschied zwischen Hub, Switch und Router?

### VLAN

7. Was ist ein VLAN?
8. Welche Vorteile bietet die Verwendung von VLANs?
9. Was ist eine Broadcast-Domäne?
10. Warum reduziert die Verwendung mehrerer VLANs Broadcasts?
11. Was ist der Unterschied zwischen Access-Port und Trunk-Port?
12. Wofür wird IEEE 802.1Q verwendet?
13. Was ist ein VLAN-Tag?
14. Was ist das Native VLAN?
15. Können zwei Geräte aus unterschiedlichen VLANs direkt auf Layer 2 miteinander kommunizieren?

### Routing

16. Was versteht man unter Inter-VLAN-Routing?
17. Welche Aufgabe hat das Default Gateway eines Hosts?
18. Was ist Router-on-a-Stick?
19. Was ist ein SVI?
20. Welche Vorteile bietet ein Layer-3-Switch gegenüber Router-on-a-Stick?

### Praxis / Fehleranalyse

21. Ein PC hat eine IP-Adresse aus dem richtigen Netzwerk, kann aber keinen anderen PC im gleichen VLAN erreichen. Welche Ursachen kommen infrage?
22. Zwei PCs im gleichen VLAN, aber an unterschiedlichen Switches, können nicht miteinander kommunizieren. Welche Trunk-Einstellungen würdest du überprüfen?
23. Ein PC aus VLAN 10 kann einen PC aus VLAN 20 nicht erreichen. Welche Komponenten und Einstellungen prüfst du?
24. Warum sollte ein Gäste-VLAN keinen uneingeschränkten Zugriff auf das Verwaltungs-VLAN erhalten?
25. Plane eine VLAN-Struktur für ein Unternehmen mit Verwaltung, Entwicklung, Servern und Gästen.

---

# Mini-Prüfung

**Aufgabe 1 – VLAN**

Ein Unternehmen verwendet:

* VLAN 10 = Verwaltung
* VLAN 20 = Entwicklung
* VLAN 30 = Gäste

Ein PC aus VLAN 10 soll auf einen Server in VLAN 30 zugreifen.

**Frage:** Welche technische Funktion wird benötigt?

<details>
<summary>▶ Lösung</summary>

**Inter-VLAN-Routing.**

Die VLANs stellen getrennte Layer-2-Netze dar. Ein Layer-3-Gerät muss den Datenverkehr zwischen den Netzen routen.

</details>

---

**Aufgabe 2 – Trunk**

Zwei Switches sind miteinander verbunden. Geräte aus VLAN 10 funktionieren, Geräte aus VLAN 20 jedoch nicht.

**Frage:** Welche Ursache solltest du unter anderem prüfen?

**Lösung:**
Prüfen, ob VLAN 20 auf beiden Switches vorhanden ist und auf dem Trunk **erlaubt/transportiert** wird.

---

**Aufgabe 3 – MAC-Tabelle**

Ein Switch kennt die Ziel-MAC-Adresse bereits.

**Frage:** Was macht er mit dem Frame?

**Lösung:**
Er leitet den Frame gezielt an den Port weiter, der zur Ziel-MAC-Adresse gehört.

---

**Aufgabe 4 – Subnetze**

Gegeben:

```text
VLAN 10 → 192.168.10.0/24
VLAN 20 → 192.168.20.0/24
```

**Frage:** Können zwei Hosts aus diesen VLANs ohne Routing direkt miteinander kommunizieren?

**Lösung:**
Nein. Es handelt sich um unterschiedliche IP-Netze und VLANs. Für die Kommunikation wird Routing benötigt.

---

# Quellen

* IEEE 802.1 – Standards für Bridging und VLANs
* Cisco Networking Academy – Switching und VLAN-Grundlagen
* RFC 791 – Internet Protocol
* RFC 826 – Address Resolution Protocol (ARP)
* OSI-Referenzmodell / ISO 7498-1


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
