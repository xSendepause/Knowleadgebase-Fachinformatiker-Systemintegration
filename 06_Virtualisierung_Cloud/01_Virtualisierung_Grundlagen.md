# Virtualisierung Grundlagen

> 📝 **Prüfungsrelevanz:** AP1 + AP2
> 🔖 **Lernstatus:** ⬜ Nicht begonnen | 🔄 In Bearbeitung | ✅ Abgeschlossen

## Lernziele
- [ ] Lernziel 1
- [ ] Lernziel 2

## Grundlagen

<!-- TODO: Grundlegende Konzepte ergänzen -->
**Was ist Virtualisierung**
Virtuelle Maschinen (VMs) simulieren physische Computer in Softwareform. Jede VM verfügt über eigene virtuelle Hardwarekomponenten wie CPU, Arbeitsspeicher, Festplatte und Netzwerkkarte sowie über ein eigenes Betriebssystem. Dadurch können mehrere Betriebssysteme parallel auf derselben physischen Hardware betrieben werden.

Hypervisoren sind Softwarekomponenten, die die Ressourcen der physischen Hardware verwalten und den virtuellen Maschinen zuweisen. Sie stellen den VMs die benötigten Ressourcen wie Prozessorleistung, Arbeitsspeicher, Speicherplatz und Netzwerkverbindungen bereit. Dabei sorgt der Hypervisor dafür, dass die VMs voneinander getrennt bleiben. Man unterscheidet grundsätzlich zwischen Typ1-Hypervisor(Baremetal) und Typ2-Hypervisor(gehosteter Hypervisor).

Ein wichtiges Merkmal der Virtualisierung ist die Isolation. Jede VM arbeitet unabhängig von den anderen VMs. Probleme oder Abstürze in einer VM wirken sich in der Regel nicht auf andere virtuelle Maschinen aus.

Zudem bietet Virtualisierung eine Abstraktion der Hardware. Das Gastbetriebssystem in der VM sieht nur die virtuelle Hardware und hat keinen direkten Zugriff auf die physische Hardware des Hostsystems. Dadurch können VMs flexibel zwischen verschiedenen physischen Systemen verschoben werden.

**Vorteile von Virtualisierung**
Effizientere Ressourcennutzung Mehrere VMs können auf einer physischen Hardware betrieben werden
Geringere Kosten - Weniger physische Hardware
schnelle Bereitstellung neuer Server und Dienste 
Sicherheit - VM's sind isoliert, was sie ideal für Tests und den Schutz vor Malware macht

**Nachteile Virtualisierung ** 
Abhängigkeit vom Hostsystem
Hohe Anforderungen an Hardware
Komplexere Verwaltung
Host-Ausfall betrifft mehrere VMs

** Snapshot ** 
Ein Snapshot speichert den Zustand einer VM zu einem bestimmten Zeitpunkt. Dadurch kann die virtuelle Maschine bei Problemen oder nach fehlgeschlagenen Änderungen auf diesen gespeicherten Zustand zurückgesetzt werden.

## Wichtige Begriffe

| Begriff | Erklärung |
|----------|----------|
| Virtualisierung | Technologie, die es ermöglicht, mehrere virtuelle Systeme auf einer physischen Hardware zu betreiben. |
| Virtuelle Maschine (VM) | Softwarebasierter Computer mit eigenem Betriebssystem und virtueller Hardware. |
| Hypervisor | Software, die die Hardware-Ressourcen verwaltet und den virtuellen Maschinen zuweist. |
| Typ-1-Hypervisor | Hypervisor, der direkt auf der physischen Hardware läuft (Bare-Metal). |
| Typ-2-Hypervisor | Hypervisor, der auf einem bestehenden Betriebssystem läuft. |
| Host | Physischer Rechner, auf dem die virtuellen Maschinen betrieben werden. |
| Gastbetriebssystem | Betriebssystem, das innerhalb einer virtuellen Maschine installiert ist. |
| Ressourcen | CPU, Arbeitsspeicher, Speicherplatz und Netzwerkressourcen, die den VMs zugewiesen werden. |
| Isolation | Trennung der virtuellen Maschinen, sodass sie unabhängig voneinander arbeiten. |
| Abstraktion | Die physische Hardware wird durch virtuelle Hardware dargestellt. |
| Snapshot | Speicherung des Zustands einer VM zu einem bestimmten Zeitpunkt, um diesen später wiederherstellen zu können. |
| Klonen (Clone) | Erstellung einer identischen Kopie einer virtuellen Maschine. |
| VDI (Virtual Desktop Infrastructure) | Bereitstellung virtueller Desktop-Arbeitsplätze über zentrale Server. |
| Migration | Verschieben einer VM von einem Host auf einen anderen. |

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
