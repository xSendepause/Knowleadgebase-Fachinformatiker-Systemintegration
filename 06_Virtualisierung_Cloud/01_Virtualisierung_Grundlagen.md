# Virtualisierung Grundlagen

> 📝 **Prüfungsrelevanz:** AP1 + AP2
> 🔖 **Lernstatus:** ⬜ Nicht begonnen | 🔄 In Bearbeitung | ✅ Abgeschlossen

## Lernziele
- [ ] Lernziel 1
- [ ] Lernziel 2

## Grundlagen

<!-- TODO: Grundlegende Konzepte ergänzen -->
** Was ist Virtualisierung **
Virtuelle Maschinen (VMs) simulieren physische Computer in Softwareform. Jede VM verfügt über eigene virtuelle Hardwarekomponenten wie CPU, Arbeitsspeicher, Festplatte und Netzwerkkarte sowie über ein eigenes Betriebssystem. Dadurch können mehrere Betriebssysteme parallel auf derselben physischen Hardware betrieben werden.

Hypervisoren sind Softwarekomponenten, die die Ressourcen der physischen Hardware verwalten und den virtuellen Maschinen zuweisen. Sie stellen den VMs die benötigten Ressourcen wie Prozessorleistung, Arbeitsspeicher, Speicherplatz und Netzwerkverbindungen bereit. Dabei sorgt der Hypervisor dafür, dass die VMs voneinander getrennt bleiben.

Ein wichtiges Merkmal der Virtualisierung ist die Isolation. Jede VM arbeitet unabhängig von den anderen VMs. Probleme oder Abstürze in einer VM wirken sich in der Regel nicht auf andere virtuelle Maschinen aus.

Zudem bietet Virtualisierung eine Abstraktion der Hardware. Das Gastbetriebssystem in der VM sieht nur die virtuelle Hardware und hat keinen direkten Zugriff auf die physische Hardware des Hostsystems. Dadurch können VMs flexibel zwischen verschiedenen physischen Systemen verschoben werden.

** Vorteile von Virtualisierung **
Effizientere Ressourcennutzung Mehrere VMs können auf einer physischen Hardware betrieben werden
Geringere Kosten - Weniger physische Hardware
schnelle Bereitstellung neuer Server und Dienste 
Sicherheit - VM's sind isoliert, was sie ideal für Tests und den Schutz vor Malware macht

** Nachteile Virtualisierung ** 
Abhängigkeit vom Hostsystem
Hohe Anforderungen an Hardware
Komplexere Verwaltung
Host-Ausfall betrifft mehrere VMs

** Snapshot ** 
Ein Snapshot speichert den Zustand einer VM zu einem bestimmten Zeitpunkt. Dadurch kann die virtuelle Maschine bei Problemen oder nach fehlgeschlagenen Änderungen auf diesen gespeicherten Zustand zurückgesetzt werden.

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

## Quellen

- [ ] Noch keine Quellen

---
[↩ Zurück zur Übersicht](../README.md) | [Nächstes Thema](02_Hypervisor_Typ1_Typ2.md)
