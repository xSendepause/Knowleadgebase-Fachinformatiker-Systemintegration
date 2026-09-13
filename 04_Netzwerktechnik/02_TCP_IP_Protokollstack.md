# TCP/IP Protokollstack

> 📝 **Prüfungsrelevanz:** AP1 + AP2
> 🔖 **Lernstatus:** ⬜ Nicht begonnen | 🔄 In Bearbeitung | ✅ Abgeschlossen

## Lernziele
- [ ] Lernziel 1
- [ ] Lernziel 2

## Grundlagen

<!-- TODO: Grundlegende Konzepte ergänzen -->
Definition

Der TCP/IP-Protokollstack ist ein Schichtenmodell für die Kommunikation von Geräten in IP-basierten Netzwerken und bildet die technische Grundlage des Internets.

Jede Schicht übernimmt bestimmte Aufgaben und stellt der darüberliegenden Schicht Dienste zur Verfügung. Beim Senden durchlaufen Daten den Stack von oben nach unten, beim Empfangen von unten nach oben.

## Wichtige Begriffe

| Begriff | Definition |
|---------|------------|
|4 Anwendungsschicht |Stellt Netzwerkdienste für Anwendungen bereit z.B HTTP(S), DNS, SMTP, SSH |
|3 Transportschicht |Kommunikation zwischen Prozessen auf Engeräten; verwendet Ports z.B. TCP, UDP |
|2 Internet | Logische Adressierung und weiterleitung zwischen Netzwerken z.B. IPv4, IPv6, ICMP |
|1 Netzzugang | Übertragung´über das konkrete lokale Netzwerk bzw. Meduim | Ethernet, WLAN|
## Prüfungsrelevante Inhalte

<!-- TODO: Wichtige Prüfungspunkte ergänzen -->

## Beispiele / Praxisbezug

<!-- TODO: Praktische Beispiele ergänzen -->

## Zusammenfassung

<!-- TODO: Kurze Zusammenfassung -->
Merksatz:
Anwendung → Transport → Internet → Netzzugang

Dabei beantwortet jede Schicht vereinfacht eine andere Frage:

Anwendung: Was möchte ich übertragen?
Transport: Welcher Prozess soll die Daten bekommen und wie sollen sie transportiert werden?
Internet: Zu welchem Zielsystem bzw. Netzwerkinterface müssen die Pakete gelangen?
Netzzugang: Wie gelangen die Daten zum nächsten Teilnehmer im aktuell verwendeten Netz?

## Prüfungsfragen zum Üben

- [ ] Frage 1?
- [ ] Frage 2?

## Quellen

- [ ] Noch keine Quellen

---
[↩ Zurück zur Übersicht](../README.md) | [Vorheriges Thema](01_OSI_Modell.md) | [Nächstes Thema](03_IPv4_Subnetting.md)
