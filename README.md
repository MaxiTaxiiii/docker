
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
Ein **SAN** ist ein Netzwerk, das Server mit Speichersystemen verbindet, um eine effiziente und flexible Verwaltung großer Datenmengen zu ermöglichen. 
Er besteht meistens aus einem Fibre-Channel-Switch, einem oder mehreren Disk-Arrays und den Servern, die über sogenannte Host-Bus-Adapter, mit dem Fibre-Channel-Switch verbunden werden.
SANs nutzen blockbasierte Datenzugriffe und arbeiten typischerweise mit Protokollen wie Fibre Channel oder iSCSI. 
Sie bieten hohe Performance (bis zu 16 Gbit/s) und ermöglichen eine zentrale Verwaltung von Speicherkapazitäten.

* **NAS**:
Ein **NAS** ist ein Speichersystem, das über ein Netzwerk, meist ein LAN, zugänglich ist. Es besteht aus mehreren Festplatten, die entweder in einem Gehäuse oder auf mehreren Geräten untergebracht sind. NAS-Systeme werden häufig für das Filesharing und die zentrale Ablage von Daten verwendet. Im Gegensatz zum SAN, das Block-Level-Storage nutzt, speichert ein NAS Daten auf Dateisystemebene. Dies bedeutet, dass Daten in Form von Dateien gespeichert werden, die auf einem Dateisystem wie EXT4, NTFS oder ZFS abgelegt sind. Um besseren Schutz zu gewährleisten, sind die Festplatten in einem NAS meist in einem RAID-Array untergebracht, das abhängig von der Konfiguration vermeidet, dass, wenn eine Festplatte ausfällt, nicht gleichzeitig alle ausfallen.

Welche Speichermedien werden wahrscheinlich in Zukunft verwendet werden und wie funktionieren diese?
* **DNA Speicher**:
DNA-Speicher speichert Daten in form von DNA-Molekülen. DNA-Speicher funktioniert, indem digitale Daten in binäre Form umgewandelt und in DNA-Sequenzen übersetzt werden, die dann im Labor synthetisiert werden. Um die Haltbarkeit der DNA zu erhöhen, wird sie in Glaspartikel eingeschlossen, was sie vor Umwelteinflüssen schützt und sie für etwa 1000 Jahre stabil hält. Ein Gramm DNA könnte theoretisch bis zu ein Exabyte an Daten speichern, was es zu einem extrem kompakten Medium für riesige Datenmengen macht.
* **Quanten Speicher**: 
Ein Quanten-Speicher nutzt Qubits, die im Gegensatz zu klassischen Bits nicht nur einen Zustand (0 oder 1) annehmen, sondern gleichzeitig beide Zustände in einer Überlagerung einnehmen können. Diese Überlagerung bedeutet, dass das Qubit eine Mischung aus „0“ und „1“ ist, wobei der Informationsgehalt durch das Verhältnis der beiden Zustände bestimmt wird (z. B. 20% „0“ und 80% „1“), somit können Berechnung parallel zueinander durchgeführt werden. Weil ein Qubit mehrere Zustände gleichzeitig darstellen kann, kann ein Qubit viel mehr Informationen speicher als ein klassiches Bit. Dadurch könnte die Speicherdichte von Quanten-Speichern erheblich höher sein, was die Speicherung großer Datenmengen effizienter machen könnte.

Welche Backup Strategie verfolgst du im Moment?

* Ich speichere alle meine wichtigen Dateien in der Cloud.

Welche Daten verlierst du solltest du jetzt deinen Laptop verlieren?

* Programme, Spiele und Lokal gespeicherten Daten.
## 4. Arbeitsschritte

**Docker Desktop Installieren**
https://www.docker.com/products/docker-desktop/

**Docker Compose Datei erstellen**
Die Datei docker-compose.yml nennen und folgenden Inhalt hinzufügen:
```
services:
  ghost:
    image: ghost:5-alpine
    restart: always
    ports:
      - 8080:2368
    environment:
      database__client: mysql
      database__connection__host: db
      database__connection__user: root
      database__connection__password: example
      database__connection__database: ghost
      url: http://localhost:8080
    volumes:
      - ghost:/var/lib/ghost/content

  db:
    image: mysql:8.0
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: example
    volumes:
      - db:/var/lib/mysql
volumes:
  ghost:
  db: 
```

**Docker Compose Datei ausführen**

```docker compose up -d```

**Auf das Ghost Webinterface zugreifen**

```localhost:8080``` in den Webbrowser eingeben

Somit haben wir erfolgreich ein Docker Container mithilfe von Docker Compose erstellt!
Dieses kann man nun mit ```docker compose down``` beenden

## 5. Zusammenfassung

In diesem Projekt wurde die Erstellung und Verwaltung eines Ghost Docker Containers mithilfe von Docker Compose durchgeführt. Ziel war es, eine isolierte und einfach zu skalierende Umgebung für die Ghost-Blog-Plattform zu schaffen, die auf einem Docker-Container läuft und mit einer MySQL-Datenbank verbunden ist. Dies wurde durch eine gut strukturierte docker-compose.yml-Datei erreicht, die die Konfiguration der beiden Container festlegt.

## 6. Quellen

[1] wikipedia.org, "Storage Area Network". [online]. Available at https://de.wikipedia.org/wiki/Storage_Area_Network. [Accessed 15 January 2025]

[2] wikipedia.org, "Network Attached Storage". [online]. Available at "https://de.wikipedia.org/wiki/Network_Attached_Storage". [Accessed 15 January 2025]

[3] mpg.de, "Quanten-Speicher mit Langzeitgedächtnis". [online]. Available at "https://www.mpg.de/5838737/quanteninformation_quantenspeicher_raumtemperatur". [Accessed 15 January 2025]

[4] uni-wuerzburg.de, "DNA-Chips als Speichermedien der Zukunft". [online]. Available at "https://www.uni-wuerzburg.de/aktuelles/pressemitteilungen/single/news/dna-chips/". [Accessed 15 January 2025]

[5] hub.docker.com, "ghost". [online]. Available at "https://hub.docker.com/_/ghost/". [Accessed 15 January 2025]
