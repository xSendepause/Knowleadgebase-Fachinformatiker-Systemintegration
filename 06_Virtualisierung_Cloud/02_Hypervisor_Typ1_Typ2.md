# Hypervisor Typ 1 und Typ 2

> 📝 **Prüfungsrelevanz:** AP1 + AP2
> 🔖 **Lernstatus:** ⬜ Nicht begonnen | 🔄 In Bearbeitung | ✅ Abgeschlossen

## Lernziele
- [ ] Lernziel 1
- [ ] Lernziel 2

## Grundlagen
 **Was ist ein Hypervisor**
Ein Hypervisor ist eine Software, die virtuelle Maschinen erstellt, verwaltet und mit den benötigten Hardware-Ressourcen direkt an die virtuellen Maschinen Verteilen.

**Typ-1 Hypervisor(Bare Metal)**
Ein Typ-1-Hypervisor wird direkt auf der physischen Hardware installiert. Er benötigt kein zusätzliches Host-Betriebssystem und kann die vorhandenen Ressourcen direkt an die virtuellen Maschinen verteilen. Beispiele dafür sind VMWare ESXi, Microsoft Hyper-V, Citrix Hypervisor & Proxmox.

*Vorteile:*
  -Hohe Leistung
  -hohe Stabilität
  -geringer Ressourcenverbrauch
  -Besonders für Rechenzentren und Unternehmensumgebungen geeignet

**Typ-2 Hypervisor(Hosted)
Anders als bei einem Typ-1 Hypervisor wird in Typ-2-Hypervisor auf einem bereits vorhandenen Betriebssystem installiert. Die virtuellen Maschinen laufen somit über das Host-Betriebssystem. Beispiel dafür sind: Oracle VirtualBox, VMware Workstation und VMware Player

*Vorteile*
  -Einfache Installation
  -Sehr gut für Lern- und Testumgebungen
  -keine spezielle Hardware erforderlich

<!-- TODO: Grundlegende Konzepte ergänzen -->

## Wichtige Begriffe

| Begriff | Definition |
|---------|------------|
| Begriff | Erklärung |
|----------|----------|
| Hypervisor | Software zur Erstellung und Verwaltung virtueller Maschinen. |
| Typ-1-Hypervisor | Hypervisor, der direkt auf der physischen Hardware läuft. |
| Typ-2-Hypervisor | Hypervisor, der auf einem bestehenden Betriebssystem installiert wird. |
| Bare-Metal | Bezeichnung für den direkten Betrieb auf physischer Hardware. |
| Host-System | Physisches System, auf dem virtuelle Maschinen ausgeführt werden. |
| Gastbetriebssystem | Betriebssystem innerhalb einer virtuellen Maschine. |
| Ressourcenverwaltung | Zuweisung von CPU, RAM, Speicherplatz und Netzwerkressourcen an VMs. |
| Virtualisierungsplattform | Umgebung zur Bereitstellung und Verwaltung virtueller Maschinen. |

 

## Vergleich von Hypervisor Typ 1 und Typ 2

 

| Merkmal | Typ 1 | Typ 2 |
|----------|----------|----------|
| Installation | Direkt auf der Hardware | Auf einem Betriebssystem |
| Leistung | Sehr hoch | Etwas geringer |
| Ressourcenverbrauch | Gering | Höher |
| Einsatzgebiet | Unternehmen, Rechenzentren | Test-, Entwicklungs- und Schulungsumgebungen |
| Beispiele | VMware ESXi, Hyper-V, Citrix Hypervisor | VirtualBox, VMware Workstation |

 
24
> **Merksatz:**
25
> Typ-1-Hypervisoren laufen direkt auf der Hardware, während Typ-2-Hypervisoren auf einem bestehenden Betriebssystem ausgeführt werden.

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
[↩ Zurück zur Übersicht](../README.md) | [Vorheriges Thema](01_Virtualisierung_Grundlagen.md) | [Nächstes Thema](03_VMware_Hyper-V.md)
