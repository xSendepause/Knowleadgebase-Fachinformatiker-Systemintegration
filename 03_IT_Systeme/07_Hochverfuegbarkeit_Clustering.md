# Hochverfügbarkeit und Clustering

> 📝 **Prüfungsrelevanz:** AP2
> 🔖 **Lernstatus:** ⬜ Nicht begonnen | 🔄 In Bearbeitung | ✅ Abgeschlossen

## Lernziele
- [ ] Hochverfügbarkeit verstehen
- [ ] Clustering-Konzepte kennen

## Grundlagen

<!-- TODO: Grundlegende Konzepte ergänzen -->

## Wichtige Begriffe

| Begriff | Definition |
|---------|------------|
| Hochverfügbarkeit |Bedeutet, dass ein IT-System möglichst ohne Unterbrechung verfügbar bleibt. Fällt zum Beispiel ein Server aus, kann ein anderer Server dessen Aufgaben übernehmen. Dadurch werden Ausfallzeiten möglichst gering gehalten.KURZ: in System bleibt auch bei einem Ausfall möglichst weiter erreichbar.|
| Cluster | Ein Cluster besteht aus mehreren miteinander verbundenen Servern, die zusammenarbeiten. Sie können sich gegenseitig absichern oder gemeinsam Aufgaben bearbeiten. Fällt ein Server aus, können andere Server im Cluster seine Aufgaben übernehmen. KURZ: mehrere Server arbeiten zusammen wie ein System.|
| Failover | Bezeichnet das automatische Umschalten auf ein Ersatzsystem, wenn das aktive System ausfällt. Beispielsweise fällt Server A aus und Server B übernimmt automatisch dessen Aufgabe. KURZ:Fällt ein Server aus, übernimmt automatisch ein anderer Server.|
| Load Balancing |Dabei werden Anfragen oder Arbeitslasten auf mehrere Server verteilt, damit kein einzelner Server überlastet wird. Dadurch können Leistung und Verfügbarkeit verbessert werden. Kurz: Die Arbeit bzw. Anfragen werden auf mehrere Server verteilt, damit keiner überlastet wird. Wichtige Verfahren: Round Robin: Anfragen werden der Reihe nach auf alle Server verteilt. Beispiel: A → B → C → A → B → C. Least Connections: Eine neue Anfrage geht an den Server mit den wenigsten aktiven Verbindungen. Beispiel: Server A = 10 Verbindungen, Server B = 3 Verbindungen → die neue Anfrage geht an Server B. IP Hash: Die IP-Adresse des Clients wird verwendet, um einen Server auszuwählen. Dadurch wird derselbe Client in der Regel demselben Server zugeordnet. Beispiel: Client X mit der IP-Adresse 192.168.1.50 → Server B.|

## Clustering

<!-- TODO: Clustering ergänzen -->
Clustering bedeutet, dass mehrere Server miteinander verbunden werden und gemeinsam als ein System arbeiten. Dadurch können die Verfügbarkeit, Ausfallsicherheit und Leistung verbessert werden.

Fällt ein Server im Cluster aus, kann ein anderer Server dessen Aufgaben übernehmen.

Wichtige Arten von Clustern
High-Availability-Cluster (HA-Cluster): Dient der Ausfallsicherheit. Fällt ein Server aus, übernimmt ein anderer Server seine Aufgaben.
Load-Balancing-Cluster: Verteilt Anfragen und Arbeitslasten auf mehrere Server, damit kein einzelner Server überlastet wird.
Hochleistungscluster (HPC): Mehrere Server arbeiten gemeinsam an rechenintensiven Aufgaben, um eine höhere Rechenleistung zu erreichen.

## Prüfungsrelevante Inhalte

<!-- TODO: Wichtige Prüfungspunkte ergänzen -->

## Beispiele / Praxisbezug

<!-- TODO: Praktische Beispiele ergänzen -->

## Zusammenfassung

<!-- TODO: Kurze Zusammenfassung -->

## Prüfungsfragen zum Üben

- [ ] Was ist ein Cluster?
- [ ] Was bedeutet Hochverfügbarkeit?

## Quellen

- [ ] Noch keine Quellen

---
[↩ Zurück zur Übersicht](../README.md) | [Vorheriges Thema](06_Speichertechnologien_SAN_NAS.md)
