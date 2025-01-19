
## Docker

Verfasser: **Maksymilian Saferyjski 2CHIT**

Datum: **15.01.2025**

## 1. Einführung
Docker ist eine Plattform, die es ermöglicht, Software in sogenannten Containern zu verpacken und auszuführen. Ein Container ist eine isolierte Umgebung, die alles enthält, was eine Anwendung benötigt, um zu laufen: den Code, die Bibliotheken, die Abhängigkeiten und die Systemtools. Container können auf jedem System ausgeführt werden, das Docker unterstützt, unabhängig davon, ob es sich um einen Server, einen Desktop-PC oder eine virtuelle Maschine handelt.
## 2. Projektbeschreibung
Es wurde ein Ghost Docker Container mithilfe von Docker Compose erstellt. 
## 3. Theorie
Was ist Docker? Was sind Container? Was sind dessen Vorteile?

Docker ist eine Virtualisierungssoftware, die Anwendungen in Container isoliert. Container sind Umgebungen für Anwendungen, die alles beinhalten, um das jeweilige Program in einem isolierten Bereich laufen zu lassen. Dies bringt mit sich einige Vorteile. Zuerst können Docker-Container ganz leicht installiert, gestartet und beendet werden. Zweitens kann man sie von Umgebung zu Umgebung ganz einfach verschieben. Zusätzlich hat Docker eine große Community, die stets neue Funktionen und Verbesserungen hinzufügt

Vergleiche die Performance von verschiedenen Virtualisierungsumgebungen (z.B. VMWare, Virtualbox, Parallels und Docker.)

* **VMware**: Sehr gut, besonders bei großen und komplexen Workloads mit geringem Overhead.
* **VirtualBox**: Akzeptabel, aber langsamer als VMware und Parallels, besonders bei grafikintensiven Anwendungen.
* **Parallels**: Exzellent auf macOS, besonders bei der Virtualisierung von Windows und Linux, mit minimalem Overhead.
* **Docker**: Sehr gut, nahezu native Performance, besonders bei serverseitigen, leichtgewichtigen Anwendungen.

Welche dieser Software kann in einem Modernen Rechenzentrum gefunden werden?
* VMware und Docker

Welche Speichermedien werden in modernen Rechenzentren verwendet? Und für welche Aufgaben?

* **SAN** (Storage Area Network) für Hochleistungs-Datenbanken, Virtualisierung, Hochleistungsrechnen ...
* **NAS** (Network Attached Storage) für Backup, Archivierung, Filesharing ...

Wie funktioniert physikalisch die Arbeitsweise dieser Speichermedien? (Erkläre Detailiert wie die Daten auf dem Medium gespeichert werden.)
* **SAN**:
Ein **SAN** fässt die einzelnen Laufwerke, unabhängig von Ort oder Betriebssystem, von Disk-Arrays zusammen und teilt sie in wenige große Speichergeräte, sodass ein großes Dateispeicher-Netzwerk entsteht und sie von jedem Server
über das Speichernetz gemeinsam genutzt werden können. Der eigentliche Zugriff erfolgt auf Block-Level und wird durch SAN-Switche und Storage-Controller verwaltet,
dabei sind diese Komponenten miteinander meist durch Fibre Channel verknüpft und somit ist eine sehr schnelle Übertragung möglich.
Aufgrund einer Meshed-artigen Struktur, bietet ein SAN eine sehr hohe Ausfallsicherheit.

* **NAS**:
Ein NAS ist ein Speichersystem, das über ein Netzwerk, meist ein LAN, zugänglich ist. Es besteht aus mehreren Festplatten, die entweder in einem Gehäuse oder auf mehreren Geräten untergebracht sind. NAS-Systeme werden häufig für das Filesharing und die zentrale Ablage von Daten verwendet.

Welche Speichermedien werden wahrscheinlich in Zukunft verwendet werden und wie funktionieren diese?
* **Racetrack Speicher**:
Dieses Speichermedium speichert die Bits auf nebeneinander geordneten ferromagnetischen Nanodrähten, dabei wäre der Raumbedarf bei diesen Nanodrähten so niedrig, dass eine bis zu 100 mal höhere Speicherdichte als heutige Flasch-Speicher möglich wäre.
* **Protein-coated Disc**: 
Dieses Speichermedium ist eine DVD, die mit einem Protein überzogen wurde. Diese gibt bei Lichteinstrahlung eine Substanz ab, die als Energiespeicher genutzt werden kann. Somit wäre eine Kapazität von bis zu 50 TB möglich.
* **Holographische/Mehrdimensionale optische Datenträger**:
Dieses Speichermedium hat eine Ebene mehr als übliche DVD/CDs und können somit eine enorme Kapazität erreichen.

Welche Backup Strategie verfolgst du im Moment?

* Ich speichere alle meine wichtigen Dateien in der Cloud.

Welche Daten verlierst du solltest du jetzt deinen Laptop verlieren?

* Programme, Spiele und Lokal gespeicherten Daten.
## 4. Arbeitsschritte