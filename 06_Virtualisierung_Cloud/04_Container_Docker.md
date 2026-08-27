# Container und Docker

> 📝 **Prüfungsrelevanz:** AP1 + AP2
> 🔖 **Lernstatus:** ⬜ Nicht begonnen | 🔄 In Bearbeitung | ✅ Abgeschlossen

## Lernziele
- [ ] Lernziel 1
- [ ] Lernziel 2

## Grundlagen

**Docker und Container**
Docker ist eine Plattform zur Erstellung, Bereitstellung und Verwaltung von Containern.
Ein Container ist eine isolierte Laufzeitumgebung, in der eine Anwendung mit allen benötigten Komponenten (Bibliotheken, Dateien, Konfigurationen) ausgeführt wird.
Anders als bei virtuellen Maschinen wird kein eigenes Betriebssystem virtualisiert. Container teilen sich den Kernel des Host-Betriebssystems und benötigen dadurch deutlich weniger Ressourcen.

Einfach erklärt:


Virtuelle Maschine = kompletter virtueller Computer
Container = isolierte Anwendung auf einem bestehenden Betriebssystem


**Wie funktioniert Docker?**

Docker basiert auf mehreren Komponenten:

-*Docker Engine*


Die Docker Engine ist die Software, die Container erstellt und verwaltet.

-*Docker Image*


Ein Image ist eine Vorlage für einen Container.
Beispiele:
Ubuntu-Image
Nginx-Image
MySQL-Image
Docker Container

-*Ein Container ist eine laufende Instanz eines Images.*


Beispiel:
Shell
docker run nginx

Docker erstellt aus dem Nginx-Image einen laufenden Container.

-*Docker Hub*


Docker Hub ist ein öffentliches Repository für Docker Images.

Beispiel:
docker pull nginx

Hier wird das Nginx-Image aus Docker Hub heruntergeladen.

-*Unterschied zwischen VM und Container*


Virtuelle Maschine
Eigenes Betriebssystem
Eigener Kernel
Hoher Ressourcenverbrauch
Langsamer Start

Beispiel:

Hardware

|Hypervisor



├── VM1 (Windows) 


├── VM2 (Linux) 


└── VM3 (Linux) 

Container
Teilen sich den Host-Kernel
Geringer Ressourcenverbrauch
Starten innerhalb weniger Sekunden
Höhere Dichte an Anwendungen möglich

Beispiel:

Hardware


│
Betriebssystem


│
Docker Engine


├── Container 1


├── Container 2


└── Container 3
<!-- TODO: Grundlegende Konzepte ergänzen -->

**Vorteile von Docker**

Ressourcenschonend- Kein vollständiges Gastbetriebssystem erforderlich.
Schneller Start- Container starten meist in wenigen Sekunden.
Portabilität- Container laufen auf nahezu jeder Plattform mit Docker.
Einfache Bereitstellung- Anwendungen können überall identisch betrieben werden.
Skalierbarkeit- Container können schnell vervielfältigt werden.
Isolation- Anwendungen laufen voneinander getrennt.

**Nachteile**

Geringere Isolation als VM- Da Container den Host-Kernel nutzen, ist die Trennung nicht so stark wie bei einer VM.

Linux-Kernel-Abhängigkeit- Container teilen sich den Kernel des Hostsystems.

Persistenz- Daten in Containern gehen ohne Volumes beim Löschen verloren.

Komplexität bei großen Umgebungen- Viele Container benötigen zusätzliche Orchestrierung (z.B. Kubernetes).

**Merksatz**
Docker ist eine Container-Plattform, die Anwendungen inklusive aller Abhängigkeiten in isolierten Containern bereitstellt. Container teilen sich den Kernel des Host-Betriebssystems und benötigen dadurch deutlich weniger Ressourcen als virtuelle Maschinen.
## Wichtige Begriffe

| Begriff | Definition |
|---------|------------|
| Docker | Plattform zur Erstellung, Bereitstellung und Verwaltung von Containern |
| Container | Isolierte Laufzeitumgebung für Anwendungen |
| Image | Vorlage bzw. Abbild, aus dem Container erstellt werden |
| Dockerfile | Datei mit Anweisungen zum Erstellen eines Docker-Images |
| Docker Hub | Öffentliches Online-Repository für Docker-Images |
| Registry | Speicherort für Docker-Images (z. B. Docker Hub oder private Registry) |
| Volume | Dauerhafter Speicher für Containerdaten |
| Network | Virtuelles Netzwerk zur Kommunikation zwischen Containern |
| Docker Engine | Dienst bzw. Laufzeitumgebung zur Verwaltung von Containern |
| Tag | Versionskennzeichnung eines Images (z. B. `nginx:latest`) |
| Repository | Sammlung verschiedener Versionen eines Docker-Images |
| Port Mapping | Zuordnung eines Container-Ports zu einem Host-Port 
| Bind Mount | Einbindung eines Host-Verzeichnisses in einen Container |
| Orchestrierung | Zentrale Verwaltung und Automatisierung vieler Container |
| Kubernetes | Plattform zur Orchestrierung und Verwaltung von Containern |
| Microservice | Kleine, eigenständige Anwendungskomponente mit einer klar definierten Aufgabe |

**Typische Dockerbefehle**

Container starten:
docker run nginx


Laufende Container anzeigen:
docker ps


Alle Container anzeigen:
docker ps -a


Images anzeigen:
docker images

Container stoppen:
docker stop <Container-ID>


Container löschen:
docker rm <Container-ID>


Image herunterladen:
docker pull nginx

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
[↩ Zurück zur Übersicht](../README.md) | [Vorheriges Thema](03_VMware_Hyper-V.md) | [Nächstes Thema](05_Kubernetes_Grundlagen.md)
