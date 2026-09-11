# Speichertechnologien SAN/NAS

> 📝 **Prüfungsrelevanz:** AP2
> 🔖 **Lernstatus:** ⬜ Nicht begonnen | 🔄 In Bearbeitung | ✅ Abgeschlossen

## Lernziele
- [ ] SAN und NAS unterscheiden
- [ ] Speichertechnologien kennen

## Grundlagen

<!-- TODO: Grundlegende Konzepte ergänzen -->

## Wichtige Begriffe

| Begriff | Definition |
|---------|------------|
| SAN | **Storage Area Network** ist ein dediziertes Hochgeschwindigkeitsnetzwerk, das Server mit zentralen Speichernetzwerken verbindet und blockbasiertem Datenzugriff ermöglicht. Dabei handelt es sich und ein seperates Netzwerk, dass den Speicherverkehr vom LAN entkoppelt. Dadurch hat man hohe Performance und Skalierbarkeit für geschäftskritische Anwendungen wie Datenbanken und Virtualisierung zu gewährleisten. Zu beachten ist das es Hohe Kosten mit sich zieht und komplexer Aufbau und Konfiguration|
| NAS |**Network Attachet Storage** (netzwerkgebundener Speicher) ein dediziertes Speichergerät, das über ein lokales Netzwerk (LAN) oder das Internet mit Computern verbunden ist. Es fungiert als zentraler Dateiserver der autorisierten Nutzern und Geräten ermöglicht, Daten gemeinsam zu speichern, zu organisieren und darauf zuzugreifen, ohne dass die Dateien lokal auf den einzelnen Endgeräten gespeichert werden müssen. Vorteile sind unter anderem Zentralisierter Zugriff der es ermöglich allen eingebundenen Clients auf Daten zugreifen zu können, Redundanz und Sicherheit durch die Nutzung von Raidsystemen. NAchteile sind Netzwerkabhängugkeit, Skalierbarkeit - bei großen Umgebungungen teilweise limitierend. | 
| DAS |**Direct attached Storage** bezeichnet einen direkt an einen Computer oder Server angeschlossenen Speicher, der nicht über ein Netzwerk bereitgestellt wird. Beispielsweise Festplatten oder USB-Sticks |
| iSCSI | **Internet Small Computer Systems Interface** Es ist ein Netzwerkprotokoll für blockbasierten Speicherzugriff, bei dem SCSI-Kommandos über TCP/IP-Netzwerke übertragen werden. In einfachen Worten: ist eine Technik, mit der ein Computer Speicherplatz von einem anderen Gerät über das Netzwerk benutzen kann. |

## SAN vs NAS

| Merkmal | SAN | NAS |
|---------|-----|-----|
| Zugriff |blockbasiert wie eine lokale Festplatte |Dateibasiert Zugriff auf Dateien und Ordner |
| Protokoll |ISCI oder Fiberchannel| SMB und NFS |
| Einsatzbereich |Server, Datenbanken und Virtualisierung |Gemeinsame Daten, Backups und Medien |
| Kosten |eher hoch | im vergleich niedriger|

## Prüfungsrelevante Inhalte

<!-- TODO: Wichtige Prüfungspunkte ergänzen -->

## Beispiele / Praxisbezug

<!-- TODO: Praktische Beispiele ergänzen -->

## Zusammenfassung

<!-- TODO: Kurze Zusammenfassung -->

## Prüfungsfragen zum Üben

- [ ] Was ist der Unterschied zwischen SAN und NAS?
*SAN* (Storage Area Network): Stellt Speicherblöcke bereit. Für den Server sieht der Speicher wie eine direkt angeschlossene Festplatte aus. Typisch sind iSCSI oder Fibre Channel.
*NAS* (Network Attached Storage): Stellt Dateien und Ordner über das Netzwerk bereit. Typische Protokolle sind SMB und NFS.

## Quellen

- [ ] Noch keine Quellen

---
[↩ Zurück zur Übersicht](../README.md) | [Vorheriges Thema](05_Serverarchitekturen.md) | [Nächstes Thema](07_Hochverfuegbarkeit_Clustering.md)
