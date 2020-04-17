---
title: Handbuch zur Optimierung der Asset-Leistung
description: Wichtige Bereiche der AEM-Konfiguration, Änderungen an Hardware, Software und Netzwerkkomponenten, um Engpässe zu beseitigen und die Performance von AEM Assets zu optimieren.
contentOwner: AG
translation-type: ht
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Handbuch zur Optimierung der Asset-Leistung{#assets-performance-tuning-guide}

Das Setup von Adobe Experience Manager (AEM) Assets umfasst eine Reihe von Hardware-, Software- und Netzwerkkomponenten. Je nach Ihrem Bereitstellungsszenario benötigen Sie möglicherweise bestimmte Konfigurationsänderungen an den Hardware-, Software- und Netzwerkkomponenten, um Leistungsengpässe zu vermeiden.

Wenn Sie sich darüber hinaus an bestimmte Richtlinien zur Optimierung der Hardware und Software halten, schaffen Sie eine solide Grundlage für Ihre AEM Assets-Bereitstellung, mit der Sie alle Anforderungen an Leistung, Skalierbarkeit und Zuverlässigkeit erfüllen.

Eine schwache Leistung von AEM Assets kann sich auf die Benutzerfreundlichkeit auswirken und die interaktive Leistung, Asset-Verarbeitung und Download-Geschwindigkeit und andere Bereiche beeinträchtigen.

Daher gehört die Leistungsoptimierung zu den grundlegenden Aufgaben, bevor Sie Zielmetriken für Ihre Projekte erstellen.

In den folgenden Schlüsselbereichen sollten Sie besonders darauf achten, dass Leistungsprobleme erkannt und behoben werden, bevor sie sich auf das Benutzererlebnis auswirken.

## Plattform {#platform}

AEM wird auf einer Reihe von Plattformen unterstützt. Adobe zufolge werden die nativen Tools jedoch unter Linux und Windows besonders gut unterstützt und können dort zur optimalen Leistung und Vereinfachung der Implementierung beitragen. Ein 64-Bit-Betriebssystem ist ideal für die hohen Speicheranforderungen einer AEM Asset-Bereitstellung. Wie bei jeder AEM-Bereitstellung sollten Sie nach Möglichkeit TarMK implementieren. TarMK kann zwar nicht über eine einzelne Autoreninstanz skaliert werden, erzielt jedoch erfahrungsgemäß eine bessere Leistung als MongoMK. Sie können TarMK-Offload-Instanzen hinzufügen, um die Leistung der Workflow-Verarbeitung Ihrer AEM Assets-Bereitstellung zu erhöhen.

### Temporärer Ordner   {#temp-folder}

Nutzen Sie einen Hochleistungsspeicher für das temporäre Java-Verzeichnis, um das Hochladen der Assets zu beschleunigen. Unter Linux und Windows können Sie beispielsweise ein RAM- oder SSD-Laufwerk verwenden. In Cloud-basierten Umgebungen kann ein äquivalenter Hochgeschwindigkeitsspeicher verwendet werden. In Amazon EC2 beispielsweise kann ein Laufwerk vom Typ [ephemeral drive](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) als temporärer Ordner eingesetzt werden.

Bei einer großen Speicherkapazität des Servers kann ein RAM-Laufwerk konfiguriert werden. Führen Sie unter Linux die folgenden Befehle aus, um ein RAM-Laufwerk von 8 GB zu erstellen:

```
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

Unter Windows müssen Sie den Treiber eines Drittanbieters nutzen, um ein RAM-Laufwerk zu erstellen, oder einen Hochleistungsspeicher wie SSD verwenden.

Sobald das temporäre Hochleistungs-Volume bereit ist, stellen Sie den JVM-Parameter Djava.io.tmpdir ein. Sie können beispielsweise den JVM-Parameter unter der Variablen „CQ_JVM_OPTS“ im Skript „bin/start“ von AEM einfügen:

`-Djava.io.tmpdir=/mnt/aem-tmp`

## Java-Konfiguration {#java-configuration}

### Java-Version {#java-version}

Da Oracle seit April 2015 keine Updates für Java 7 mehr herausgibt, empfiehlt Adobe die Bereitstellung von AEM Assets auf Java 8. Damit wurde in einigen Fällen eine bessere Leistung erzielt.

### JVM-Parameter   {#jvm-parameters}

Legen Sie die folgenden JVM-Parameter fest:

* `-XX:+UseConcMarkSweepGC`
* `-Doak.queryLimitInMemory`=500000
* `-Doak.queryLimitReads`=100000
* `-Dupdate.limit`=250000
* `-Doak.fastQuerySize`=true

## Datenspeicher- und Arbeitsspeicherkonfiguration {#data-store-and-memory-configuration}

### Dateidatenspeicherkonfiguration {#file-data-store-configuration}

Allen Benutzern von AEM Assets wird angeraten, Datenspeicher und Segmentspeicher zu trennen. Außerdem kann die Leistung durch die Konfiguration der Parameter `maxCachedBinarySize` und `cacheSizeInMB` maximiert werden. Stellen Sie `maxCachedBinarySize` auf die kleinste im Cache unterstützte Dateigröße ein. Geben Sie die Größe des Arbeitsspeicher-Cache für den Datenspeicher in `cacheSizeInMB` ein. Adobe empfiehlt, diesen Wert auf 2–10 Prozent der gesamten Heap-Größe einzustellen. Mithilfe von Last-/Leistungstests lässt sich die ideale Einstellung herausfinden.

### Konfigurieren der Maximalgröße des gepufferten Bilder-Caches   {#configure-the-maximum-size-of-the-buffered-image-cache}

Verringern Sie beim Hochladen großer Mengen an Assets in Adobe Experience Manager zur Berücksichtigung unerwarteter Spitzen bei der Speichernutzung und zur Verhinderung von JVM-Fehlern mit OutOfMemoryErrors die konfigurierte Maximalgröße des gepufferten Bilder-Caches. Betrachten wir ein Beispiel mit einem System, das über eine maximale Heap-Größe (-`Xmx`param) von 5 GB verfügt und bei dem der Oak-Blob-Cache auf 1 GB und der Dokumenten-Cache auf 2 GB eingestellt ist. In diesem Fall würde der gepufferte Cache das Maximum von 1,25 GB Speicher in Anspruch nehmen, wodurch nur 0,75 GB Speicher für unerwartete Spitzen verblieben.

Konfigurieren Sie die Größe des gepufferten Cache in der OSGi-Webkonsole. Legen Sie bei `https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache` die Eigenschaft `cq.dam.image.cache.max.memory` in Byte fest. 1073741824 entspricht beispielsweise 1 GB (1024 x 1024 x 1024 = 1 GB).

Wenn Sie über AEM 6.1 SP1 einen `sling:osgiConfig`-Knoten zur Konfiguration dieser Eigenschaft verwenden, stellen Sie sicher, dass Sie diesen Datentyp auf „Long“ einstellen. Weitere Details finden Sie unter [CQBufferedImageCache belegt beim Asset-Upload den Heap](https://helpx.adobe.com/de/experience-manager/kb/cqbufferedimagecache-consumes-heap-during-asset-uploads.html).

### Gemeinsame Datenspeicher   {#shared-data-stores}

Mit der Implementierung eines S3-Datenspeichers oder Shared File Datastore sparen Sie Speicherplatz auf der Festplatte und erhöhen den Netzwerkdurchsatz in großen Implementierungen.

### S3-Datenspeicher {#s-data-store}

Mit der folgenden Konfiguration des S3-Datenspeichers (`org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.cfg`) konnte Adobe binäre große Objekte (BLOBs) mit einer Größe von 12,8 TB von einem vorhandenen Dateidatenspeicher in einen S3-Datenspeicher am Standort eines Kunden extrahieren:

```
accessKey=<snip>
 secretKey=<snip>
 s3Bucket=<snip>
 s3Region=us-standard
 s3EndPoint=<a href="https://s3.amazonaws.com/">s3.amazonaws.com</a>
 connectionTimeout=120000
 socketTimeout=120000
 maxConnections=80
 writeThreads=60
 concurrentUploadsThreads=30
 asyncUploadLimit=30
 maxErrorRetry=1000
 path=/opt/author/crx-quickstart/repository/datastore
 s3RenameKeys=false
 s3Encryption=SSE_S3
 proactiveCaching=true
 uploadRetries=1000
 migrateFailuresCount=400
```

## Netzwerkoptimierung {#network-optimization}

Adobe empfiehlt die Aktivierung von HTTPS, da viele Unternehmen über Firewalls verfügen, die den HTTP-Verkehr überprüfen und sich dadurch negativ auf Uploads auswirken und Dateien beschädigen. Stellen Sie bei großen Datei-Uploads sicher, dass Benutzer über Kabelverbindungen zum Netzwerk verfügen, da ein WLAN-Netzwerk schnell überfordert ist. Informationen zur Beurteilung der Netzwerkleistung mit einer Analyse der Netzwerktopologie finden Sie unter [Überlegungen zum Assets-Netzwerk](/help/assets/assets-network-considerations.md).

Welche Strategie der Netzwerkoptimierung Sie verwenden, hängt in erster Linie von der verfügbaren Bandbreite und der Last auf Ihrer AEM-Instanz ab. Allgemeine Konfigurationsoptionen, einschließlich Firewalls oder Proxys, können zur Verbesserung der Netzwerkleistung beitragen. Die folgenden Aspekte sollten berücksichtigt werden:

* Stellen Sie je nach Instanztyp (klein, mittel, groß) sicher, dass die Netzwerkbandbreite für Ihre AEM-Instanz ausreichend ist. Dies ist besonders wichtig, wenn AEM auf AWS gehostet wird.
* Wird Ihre AEM-Instanz auf AWS gehostet, können Sie von einer flexiblen Skalierung profitieren. Vergrößern Sie die Instanz, wenn Benutzer eine hohe Belastung erwarten. Verkleinern Sie die Instanz, wenn nur eine mäßige/geringe Belastung erwartet wird.
* HTTPS: Die meisten Benutzer verwenden Firewalls zur Überwachung des HTTP-Verkehrs. Sie können den Prozess des Hochladens beeinträchtigen oder Dateien beim Hochladen beschädigen.
* Upload großer Dateien: Die Benutzer benötigen Kabelverbindungen zum Netzwerk (WLAN-Verbindungen sind schnell gesättigt).

## Workflows   {#workflows}

### Verlaufs-Workflows {#transient-workflows}

Stellen Sie den Workflow „DAM-Update-Asset“ nach Möglichkeit auf „Übergang“ ein. Die Einstellung trägt zu einer erheblichen Reduzierung des Overheads bei, der für die Verarbeitung der Workflows benötigt wird, da die Workflows in diesem Fall nicht die normalen Tracking- und Archivierungsprozesse durchlaufen.

>[!NOTE]
>
>Standardmäßig wird der Workflow DAM-Update-Asset in AEM 6.3 auf „Übergang“ eingestellt. In diesem Fall können Sie das folgende Verfahren überspringen.

1. Navigieren Sie in der zu konfigurierenden AEM-Instanz zu */miscadmin* (d. h. [https://localhost:4502/miscadmin](https://localhost:4502/miscadmin)).
1. Erweitern Sie im Navigationsbaum **Tools** > **Workflow** > **Modelle** > **dam**.
1. Doppelklicken Sie auf **DAM-Update-Asset**.
1. Wechseln Sie im unverankerten Tool-Fenster auf die Registerkarte **Seite** und klicken Sie auf **Seiteneigenschaften…**
1. Wählen Sie **Verlaufs-Workflow** und klicken Sie auf **OK**.

   >[!NOTE]
   >
   >Einige Funktionen unterstützen keine Verlaufs-Workflows. Wenn diese Funktionen in Ihrer AEM Asset-Bereitstellung benötigt werden, konfigurieren Sie keine Verlaufs-Workflows.

   Wenn keine Verlaufs-Workflows verwendet werden können, führen Sie regelmäßig Workflow-Bereinigungen durch, um archivierte DAM-Update-Asset-Workflows zu löschen. So verhindern Sie eine Beeinträchtigung der Systemleistung.

   In der Regel sollten Sie Workflow-Bereinigungen auf wöchentlicher Basis durchführen. In ressourcenintensiven Szenarien wie z. B. einer umfangreichen Asset-Erfassung kann die Bereinigung auch häufiger ausgeführt werden.

   Um die Workflow-Bereinigung zu konfigurieren, fügen Sie in der OSGi-Konsole eine neue Adobe Granite-Workflow-Bereinigungskonfiguration hinzu. Konfigurieren und planen Sie im nächsten Schritt den Workflow als Teil des wöchentlichen Wartungsfensters.

   Dauert die Bereinigung zu lange, kommt es zu einem Timeout. Daher sollten Sie sicherstellen, dass die Bereinigungsaufträge abgeschlossen sind. So vermeiden Sie, dass Bereinigungs-Workflows aufgrund der hohen Zahl an Workflows nicht abgeschlossen werden können.

   Wenn Sie zahlreiche Nicht-Verlaufs-Workflows ausgeführt haben, die Workflow-Instanzknoten erstellen, können Sie das Tool [ACS AEM Commons Workflow Remover](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html) auf Ad-hoc-Basis ausführen. Es entfernt redundante, abgeschlossene Workflow-Instanzen sofort, ohne dass Sie auf die Ausführung des Adobe Granite-Workflow-Bereinigungsplaners warten müssen.

### Maximal parallel ausführbare Aufträge   {#maximum-parallel-jobs}

Standardmäßig kann AEM maximal so viele Aufträge parallel ausführen wie Prozessoren auf dem Server vorhanden sind. In Zeiten hoher Auslastung ist diese Einstellung jedoch problematisch, da alle Prozessoren von den DAM-Update-Asset-Workflows beansprucht werden und dadurch die Reaktionsfähigkeit der Benutzeroberfläche verlangsamt wird und AEM andere Prozesse zum Schutz von Serverleistung und -stabilität nicht ausführen kann. Es hat sich bewährt, diese Einstellung so zu wählen, dass nur die Hälfte der auf dem Server verfügbaren Prozessoren verwendet wird:

1. Navigieren Sie in AEM Author zu [https://localhost:4502/system/console/slingevent](https://localhost:4702/system/console/slingevent).
1. Klicken Sie für jede für Ihre Implementierung relevante Workflow-Warteschlange, z. B. für die Granite-Warteschlange für Verlaufs-Workflows, auf „Bearbeiten“.
1. Ändern Sie den Wert der maximal parallel ausführbaren Aufträge und klicken Sie auf „Speichern“.

Diese Einstellung des Werts auf die Hälfte der verfügbaren Prozesse ist für den Anfang eine praktikable Lösung. Unter Umständen müssen Sie diese Zahl jedoch nach oben oder unten anpassen, um den maximalen Durchsatz zu erreichen, und auch an die spezifische Umgebung anpassen. Es gibt separate Warteschlangen für Verlaufs- und Nicht-Verlaufs-Workflows sowie für andere Prozesse wie beispielsweise externe Workflows. Sind mehrere Warteschlangen, die auf 50 % der Prozessoren gesetzt sind, gleichzeitig aktiv, kann es schnell zu einer Überlastung des Systems kommen. Welche Warteschlangen stark ausgelastet sind, hängt in hohem Maße von den Benutzerimplementierungen ab. Sie müssen daher sorgfältig und mit Bedacht konfiguriert werden, um maximale Effizienz zu erreichen, die nicht zu Lasten der Serverstabilität geht.

### Konfiguration von DAM-Update-Asset {#dam-update-asset-configuration}

Der DAM-Update-Asset-Workflow enthält eine vollständige Suite an für Aufgaben konfigurierten Schritten, beispielsweise Scene7 PTIFF-Generierung und InDesign Server-Integration. Die meisten Benutzer benötigen jedoch nicht alle diese Schritte. Adobe empfiehlt die Erstellung einer benutzerdefinierten Kopie des DAM-Update-Asset-Workflow-Modells, in der alle unnötigen Schritte entfernt wurden. Aktualisieren Sie dann die Launcher für DAM-Update-Asset so, dass sie auf das neue Modell zeigen.

>[!NOTE]
>
>Wenn Sie den Workflow „DAM-Update-Asset“ häufig ausführen, kann hierdurch die Größe Ihres Dateidatenspeichers deutlich ansteigen. Entsprechende Tests von Adobe haben gezeigt, dass die Datenspeichergröße um ca. 400 GB ansteigt, wenn innerhalb von 8 Stunden 5.500 Workflows ausgeführt werden.
>
>Hierbei handelt es sich um einen vorübergehenden Anstieg. Nach Ausführung der Aufgabe zur Speicherbereinigung weist der Datenspeicher wieder seine ursprüngliche Größe auf.
>
>In der Regel wird die Speicherbereinigung wöchentlich gemeinsam mit anderen geplanten Wartungsaufgaben ausgeführt.
>
>Wenn Sie nur über eingeschränkten Speicherplatz verfügen und den Workflow „DAM-Update-Asset“ häufig ausführen, sollten Sie die Speicherbereinigung öfter planen.

#### Ausgabegenerierung zur Laufzeit {#runtime-rendition-generation}

Kunden verwenden Bilder unterschiedlicher Größen und Formate auf ihrer Website oder zur Weiterleitung an die Geschäftspartner. Da jede Darstellung den Footprint der Assets im Repository vergrößert, empfiehlt Adobe die umsichtige Verwendung dieser Funktion. Um die Menge der Ressourcen zu reduzieren, die für die Verarbeitung und Speicherung von Bildern benötigt wird, können Sie die Bilder statt als Ausgabeformate bei der Erfassung auch zur Laufzeit generieren.

Viele Kunden der Website implementieren ein Bild-Servlet, das Bilder zum Zeitpunkt ihrer Anforderung skaliert und beschneidet und der Veröffentlichungsinstanz damit eine zusätzliche Belastung auferlegt. Wenn diese Bilder zwischengespeichert werden können, lässt sich dieses Problem abmildern.

Ein alternativer Ansatz ist die Scene7-Technologie, mit der sich die Bildbearbeitung vollständig abgeben lässt. Darüber hinaus können Sie Brand Portal bereitstellen, das nicht nur die Verantwortung für die Generierung von Wiedergaben von der AEM-Infrastruktur übernimmt, sondern auch die gesamte Veröffentlichungsebene.

### XMP-Writeback {#xmp-writeback}

XMP-Writeback aktualisiert das Original-Asset, sobald Metadaten in AEM geändert werden. Folgende Änderungen werden vorgenommen:

* Das Asset selbst wird geändert.
* Eine Version des Assets wird erstellt.
* DAM-Update-Asset wird für das Asset ausgeführt.

Die aufgeführten Ergebnisse beanspruchen umfangreiche Ressourcen. Daher empfiehlt Adobe, [XMP-Writeback zu deaktivieren](https://helpx.adobe.com/de/experience-manager/kb/disable-xmp-writeback.html), wenn es nicht benötigt wird.

Wenn Sie eine große Menge an Metadaten importieren, kann es zu ressourcenintensiven XMP-Writeback-Aktivitäten kommen, falls das Flag für laufende Workflows gesetzt ist. Planen Sie einen solchen Import während Zeiten geringer Servernutzung, damit die Leistung anderer Benutzer nicht beeinträchtigt wird.

## Replikation {#replication}

Wenn Sie Assets in einer große Menge an veröffentlichten Instanzen replizieren (beispielsweise in einer Sites-Implementierung), empfiehlt Adobe die Kettenreplikation. In diesem Fall wird die Autorinstanz in eine einzelne Veröffentlichungsinstanz repliziert, die wiederum in die anderen Veröffentlichungsinstanzen repliziert wird und so die Autorinstanz freihält.

### Konfiguration der Kettenreplikation   {#configure-chain-replication}

1. Wählen Sie die Veröffentlichungsinstanz, mit der Sie die Replikationen verketten möchten.
1. Fügen Sie dieser Veröffentlichungsinstanz Agenten hinzu, die auf die anderen Veröffentlichungsinstanzen verweisen.
1. Aktivieren Sie für alle anderen Replikationsagenten die Option „Bei Empfang“ auf der Registerkarte „Auslöser“.

>[!NOTE]
>
>Adobe rät von der automatischen Aktivierung von Assets ab. Falls jedoch notwendig, sollte dies der letzte Schritt in einem Workflow, normalerweise „DAM-Update-Asset“, sein.

## Durchsuchen von Indizes   {#search-indexes}

Vergewissern Sie sich, dass Sie die neuesten Service Packs und leistungsrelevanten Hotfixes implementiert haben, da sie häufig Aktualisierungen der Systemindizes enthalten. Informationen zu je nach der AEM-Version anwendbaren Indexoptimierungen finden Sie unter [Tipps zur Leistungsoptimierung | 6.x](https://helpx.adobe.com/de/experience-manager/kb/performance-tuning-tips.html).

<!--
Create custom indexes for queries that you run often. For details, see [methodology for analyzing slow queries](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html) and [crafting custom indexes](/help/sites-deploying/queries-and-indexing.md). For additional insights around query and index best practices, see [Best Practices for Queries and Indexing](/help/sites-deploying/best-practices-for-queries-and-indexing.md).
-->

### Lucene-Indexkonfigurationen {#lucene-index-configurations}

Für die Oak-Indexkonfigurationen können Optimierungen vorgenommen werden, mit denen sich die Leistung von AEM Assets verbessern lässt:

Indexkonfigurationen aktualisieren, um die Zeit für Neuindizierungen zu verbessern:

1. Öffnen Sie CRXDe /crx/de/index.jsp und melden Sie sich als Benutzer mit Administratorrechten an.
1. Navigieren Sie zu /oak:index/lucene
1. Fügen Sie eine String[]-Eigenschaft mit dem Namen „excludedPaths“ und den Werten „/var“, „/etc/workflow/instances“ und „/etc/replication“ hinzu.
1. Navigieren Sie zu „/oak:index/damAssetLucene“.
1. Fügen Sie eine String[]-Eigenschaft mit dem Namen „includedPaths“ mit einem „/content/dam“-Wert hinzu.
1. Speichern

(Nur AEM 6.1 und 6.2) Aktualisieren Sie den Index „ntBaseLucene“, um die Leistung des Assets beim Löschen und Verschieben zu verbessern:

1. Navigieren Sie zu */oak:index/ntBaseLucene/indexRules/nt:base/properties*.
1. Fügen Sie unter */oak:index/ntBaseLucene/indexRules/nt:base/properties* zwei nt:unstructured-Knoten „slingResource“ und „damResolvedPath“ hinzu.
1. Legen Sie für die Knoten folgende Eigenschaften fest. (Dabei sind die Eigenschaften „ordered“ und „propertyIndex“ vom Typ *Boolesch*:
slingResource
name=&quot;sling:resource&quot;
ordered=false
propertyIndex= true
type=&quot;String&quot;
damResolvedPath
name=&quot;dam:resolvedPath&quot;
ordered=false
propertyIndex=true
type=&quot;String&quot;

1. Legen Sie für den Knoten „/oak:index/ntBaseLucene“ die Eigenschaft *reindex=true* fest.
1. Klicken Sie auf „Alle speichern“.
1. Überwachen Sie im Protokoll „error.log“ den Abschluss der Indizierung: Neuindizierung abgeschlossen für Indizes: [/oak:index/ntBaseLucene].
1. Den Abschluss der Indizierung können Sie auch nachverfolgen, indem Sie „/oak:index/ntBaseLucene“ in CRXDe aktualisieren. Die Eigenschaft für die Neuindizierung würde auf „false“ zurückgesetzt werden.
1. Gehen Sie nach Abschluss der Indizierung zurück zu CRXDe und stellen Sie die Eigenschaft „Typ“ auf den beiden Indizes auf „deaktiviert“ ein.

   * */oak:index/slingResource*
   * */oak:index/damResolvedPath*

1. Klicken Sie auf „Alle speichern“.

<!--
Disable Lucene Text Extraction:

If your users don't need to be able to search the contents of assets, for example, searching the text contained in PDF documents, then you can improve index performance by disabling this feature.

1. Go to the AEM package manager /crx/packmgr/index.jsp
1. Upload and install the package below

[Get File](assets/disable_indexingbinarytextextraction-10.zip)
-->

### guessTotal {#guess-total}

Verwenden Sie beim Erstellen von Abfragen mit großen Ergebnismengen den Parameter `guessTotal`, um eine übermäßige Belastung des Arbeitsspeichers bei der Ausführung zu vermeiden.

## Bekannte Probleme {#known-issues}

### Große Dateien {#large-files}

Zwei bekannte Probleme beziehen sich auf große Dateien in AEM. Bei Dateien, die größer als 2 GB sind, kann eine kalte Standby-Synchronisierung zu einem Speicherengpass führen. In einigen Fällen wird die Ausführung der Standby-Synchronisierung verhindert. In anderen Fällen stürzt die primäre Instanz ab. Dieses Szenario gilt für alle Dateien in AEM, die größer als 2 GB sind, darunter auch Inhaltspakete.

Entsprechend kann es bei Dateien, die in einem gemeinsamen S3-Datenspeicher eine Größe von 2 GB erreichen, einige Zeit dauern, bis die Datei vollständig aus dem Cache in das Dateisystem gespeichert werden kann. Wenn Sie die Binaryless-Replikation verwenden, kann es passieren, dass die binären Daten vor dem Abschluss der Replikation nicht dauerhaft gespeichert werden. Diese Situation kann zu Problemen führen, insbesondere wenn es auf hohe Datenverfügbarkeit ankommt.

## Leistungstests {#performance-testing}

Erstellen Sie für jede AEM-Bereitstellung ein Regime für Leistungstests, die Engpässe schnell identifizieren und beseitigen können. Konzentrieren Sie sich dabei auf die folgenden Schlüsselaspekte.

### Netzwerktests   {#network-testing}

Führen Sie für alle Aspekte, die die für Kunden relevante Netzwerkleistung betreffen, die folgenden Aufgaben aus:

* Testen Sie die Netzwerkleistung im Netzwerk des Kunden.
* Testen Sie die Netzwerkleistung im Adobe-Netzwerk. Arbeiten Sie bei AMS-Kunden mit CSE, um Tests innerhalb des Adobe-Netzwerks durchzuführen.
* Testen Sie die Netzwerkleistung an anderen Zugriffspunkten.
* Testen Sie unter Verwendung eines Benchmark-Tools für Netzwerke.
* Testen Sie mit dem Dispatcher.

### AEM-Instanztests   {#aem-instance-testing}

Überwachen Sie die Leistung Ihrer AEM-Instanz regelmäßig, um die Latenz zu reduzieren und mithilfe von effizienter CPU-Auslastung und Loadsharing einen hohen Durchsatz zu erzielen. Führen Sie insbesondere die folgenden Aufgaben aus:

* Führen Sie Lasttests für die AEM-Instanz aus.
* Überwachen Sie die Upload-Leistung und die Reaktionsfähigkeit der Benutzeroberfläche.

## AEM Assets-Leistungs-Checkliste     und Auswirkungen von Asset-Management-Aufgaben   {#checklist}

* Aktivieren Sie „HTTPS“, um alle vom Unternehmen installierten Sniffer für HTTP-Verkehr zu umgehen.
* Verwenden Sie eine Kabelverbindung, um umfangreiche Assets hochzuladen
* Implementieren Sie die Bereitstellung unter Java 8.
* Stellen Sie optimale JVM-Parameter ein.
* Konfigurieren Sie einen Dateisystem-DataStore oder einen S3-DataStore.
* Aktivieren Sie Verlaufs-Workflows.
* Stimmen Sie die Granit-Workflow-Warteschlangen ab, um gleichzeitige Aufträge einzuschränken.
* Konfigurieren Sie ImageMagick, um den Ressourcenverbrauch einzuschränken.
* Entfernen Sie unnötige Schritte aus dem DAM-Update-Asset-Workflow.
* Konfigurieren Sie Workflow- und Versionsbereinigung.
* Optimieren Sie die Indizes mit den neuesten Service Packs und Hotfixes. Fragen Sie den Adobe-Support nach verfügbaren zusätzlichen Indexoptimierungen.
* Optimieren Sie die Abfrageleistung mit guessTotal.
* Wenn Sie AEM so konfigurieren, dass Dateitypen aus dem Inhalt der Dateien erkannt werden (durch Aktivierung des **[!UICONTROL Day CQ DAM Mime Type Service]** in der **[!UICONTROL AEM-Web-Konsole]**), sollten Sie außerhalb der Spitzenzeiten größere Mengen an Dateien in Batches hochladen, da dieser Vorgang ressourcenintensiv ist.

