---
title: Batch-Verarbeitung in der Kommunikationsfunktion von Experience Manager  [!DNL Forms]  as a Cloud Service
description: Wie erstelle ich markenorientierte und personalisierte Kommunikation?
exl-id: 542c8480-c1a7-492e-9265-11cb0288ce98
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '2299'
ht-degree: 80%

---

# Batch-Verarbeitung in der Kommunikationsfunktion von Forms as a Cloud Service

Mithilfe der Kommunikationsfunktion können Sie markenorientierte und personalisierte Kommunikation kreieren, zusammenstellen und bereitstellen, wie z. B. Geschäftskorrespondenz, Dokumente, Mitteilungen, Schadensbearbeitungsschreiben, Leistungsbenachrichtigungen, Monatsabrechnungen und Begrüßungs-Kits. Sie können Kommunikations-APIs verwenden, um eine Vorlage (XFA oder PDF) mit Kundendaten zu kombinieren und Dokumente im PDF-, PS-, PCL-, DPL-, IPL- und ZPL-Format zu generieren.

Die Kommunikationsfunktion bietet APIs für die On-Demand- und geplante Dokumenterstellung. Sie können synchrone APIs für die On-Demand-Dokumenterstellung und Batch-APIs (asynchrone APIs) für die geplante Dokumenterstellung verwenden:

* Synchrone APIs eignen sich für die Dokumenterstellung auf Anfrage, mit geringer Latenz und mit einzelnen Datensätzen. Diese APIs eignen sich besser für Anwendungen auf Basis einer Benutzeraktion. Zum Beispiel zum Generieren eines Dokuments, nachdem ein Anwender ein Formular ausgefüllt hat.

* Batch-APIs (asynchrone APIs) eignen sich für Anwendungsfälle für die geplante Erstellung mehrerer Dokumente mit hohem Durchsatz. Diese APIs generieren Dokumente in Stapeln. Beispielsweise werden damit monatliche Telefonrechnungen, Kreditkartenauszüge und Leistungsmitteilungen generiert.

<!-- The following skills are required to create templates and use HTTP APIs: 

* Understanding of Adobe Forms Designer or Acrobat Forms to create templates

* Understanding of HTTP APIs and experience of using HTTP APIs

* Basic understanding of Adobe Experience Manager -->


## Batch-Vorgänge {#batch-operations}

Bei einem Batch-Vorgang werden in terminierten Abständen mehrere Dokumente eines ähnlichen Typs für eine Gruppe von Datensätzen generiert. Ein Batch-Vorgang besteht aus zwei Teilen: Konfiguration (Definition) und Ausführung.

* **Konfiguration (Definition)**: In einer Batch-Konfiguration werden Informationen zu verschiedenen Assets und Eigenschaften gespeichert, die für generierte Dokumente festgelegt werden sollen. Beispielsweise enthält sie Details zur XDP- oder PDF-Vorlage und zum Speicherort der zu verwendenden Kundendaten und gibt verschiedene Eigenschaften für PDF-Ausgabedokumente an.

* **Ausführung**: Zum Starten eines Batch-Vorgangs geben Sie den Ausführungsbefehl an und übergeben Sie den Batch-Konfigurationsnamen an die Batch-Ausführungs-API.

### Komponenten eines Batch-Vorgangs {#components-of-a-batch-operations}

**Cloud-Konfiguration**: Mit der Experience Manager Cloud-Konfiguration können Sie eine Experience Manager-Instanz mit dem kundeneigenen Microsoft Azure-Speicher verbinden. Damit können Sie die Anmeldeinformationen für das kundeneigene Microsoft Azure-Konto angeben, mit dem eine Verbindung hergestellt werden soll.

**Batch-Datenspeicherkonfiguration (USC)**: Mit der Batch-Datenkonfiguration können Sie eine bestimmte Instanz des Blob-Speichers für Batch-APIs konfigurieren. Damit können Sie die Ein- und Ausgabespeicherorte im kundeneigenen Microsoft Azure Blob-Speicher angeben.

**Batch-APIs**: Ermöglicht Ihnen die Erstellung von Batch-Konfigurationen und die Ausführung der Batch-Vorgänge anhand dieser Konfigurationen, um einen Batch-Vorgang zu erstellen und auszuführen, um eine PDF- oder XDP-Vorlage mit Daten zusammenzuführen und eine Ausgabe in den Formaten PDF, PS, PCL, DPL, IPL und ZPL zu generieren. Die Kommunikationsfunktion stellt Batch-APIs für das Erstellen, Lesen, Aktualisieren und Löschen von Vorgängen bereit.

![data-merge-table](assets/communications-batch-structure.png)

**Datenspeicherung**: Kommunikations-APIs verwenden den kundeneigenen Microsoft Azure Cloud-Speicher, um Kundendatensätze abzurufen und generierte Dokumente zu speichern. Der Microsoft Azure-Speicher wird in der Experience Manager Cloud Service-Konfiguration konfiguriert.

**Programm**: Ihr benutzerdefiniertes Programm zum Generieren und Verwenden von Dokumenten unter Verwendung der Batch-APIs.

## Generieren mehrerer Dokumente mithilfe von Batch-Vorgängen {#generate-multiple-documents-using-batch-operations}

Mithilfe von Batch-Vorgängen können Sie mehrere Dokumente in terminierten Intervallen generieren.

>[!VIDEO](https://video.tv.adobe.com/v/337425)

Sehen Sie sich das Video an oder befolgen Sie die unten stehenden Anweisungen, um zu erfahren, wie Sie Dokumente mithilfe von Batch-Vorgängen erstellen. Die im Video verwendete API-Referenzdokumentation ist im .yaml-Format verfügbar. Sie können die [Batch-APIs](assets/batch-api.yaml) als Datei herunterladen und in Postman hochladen, um ihre Funktionalität zu überprüfen und dem Video zu folgen.

### Voraussetzungen {#pre-requisites}

Um eine Batch-API zu verwenden, ist Folgendes erforderlich:

* [Ein Konto für den Microsoft Azure-Speicher](https://docs.microsoft.com/de-de/azure/storage/common/storage-account-create?tabs=azure-portal)
* PDF- oder XDP-Vorlagen
* [Daten, die mit Vorlagen zusammengeführt werden sollen](#form-data)
* Benutzer mit Experience Manager-Administratorberechtigungen

### Einrichten Ihrer Arbeitsumgebung {#setup-your-environment}

Vor der Verwendung eines Batch-Vorgangs:

* Hochladen von Kundendaten (XML-Dateien) in den Microsoft Azure-Blob-Speicher
* Erstellen einer Cloud-Konfiguration
* Erstellen der Batch-Datenspeicherkonfiguration
* Hochladen von Vorlagen und anderen Assets in Ihre Experience Manager Forms Cloud Service-Instanz

### Hochladen von Kundendaten (XML-Dateien) in den Azure-Speicher {#upload-customer-data-to-Azure-Storage}

Erstellen Sie im Microsoft Azure-Speicher [Container](https://docs.microsoft.com/de-de/azure/vs-azure-tools-storage-explorer-blobs) und [laden Sie Kundendaten (XML)](https://docs.microsoft.com/de-de/azure/vs-azure-tools-storage-explorer-blobs#managing-blobs-in-a-blob-container) in die [Ordner](https://docs.microsoft.com/de-de/azure/storage/blobs/storage-quickstart-blobs-portal) innerhalb der Container hoch.
>[!NOTE]
>
>Sie können den Microsoft Azure-Speicher so konfigurieren, dass der Eingabeordner automatisch bereinigt oder der Inhalt des Ausgabeordners in terminierten Intervallen an einen anderen Speicherort verschoben wird. Stellen Sie jedoch sicher, dass Ordner nicht bereinigt werden, wenn ein Batch-Vorgang, der auf die Ordner verweist, weiterhin ausgeführt wird.

### Erstellen einer Cloud-Konfiguration {#create-a-cloud-configuration}

Die Cloud-Konfiguration verbindet Ihre Experience Manager-Instanz mit dem Microsoft Azure Datenspeicher. Erstellen einer Cloud-Konfiguration:

1. Gehen Sie zu „Tools“ > „Cloud Services“ > „Azure-Speicher“.
1. Öffnen Sie einen Ordner zum Hosten der Konfiguration und klicken Sie auf „Erstellen“. Verwenden Sie den Ordner „Global“ oder erstellen Sie einen Ordner.
1. Geben Sie den Namen der Konfiguration und die Anmeldeinformationen für die Verbindung mit dem Service an. Sie können [diese Anmeldeinformationen von Ihrem Microsoft Azure-Speicherportal abrufen](https://docs.microsoft.com/de-de/azure/storage/common/storage-account-keys-manage?tabs=azure-portal#view-account-access-keys).
1. Klicken Sie auf „Erstellen“.

Ihre Experience Manager-Instanz kann jetzt eine Verbindung zum Microsoft Azure Storage herstellen und Inhalte gegebenenfalls speichern und lesen.

### Erstellen der Batch-Datenspeicherkonfiguration {#create-batch-data-store-configuration}

Die Batch-Datenkonfiguration hilft Ihnen beim Konfigurieren von Containern und Ordnern für Ein- und Ausgabe. Sie bewahren Ihre Kundendatensätze im Quellordner auf, generierte Dokumente werden im Zielordner abgelegt.

Erstellen der Konfiguration:

1. Navigieren Sie zu „Tools“ > „Forms“ > „Ausgabe-Batch – Unified Storage Connector“.
1. Öffnen Sie einen Ordner zum Hosten der Konfiguration und klicken Sie auf „Erstellen“. Verwenden Sie den Ordner „Global“ oder erstellen Sie einen Ordner.
1. Geben Sie Titel und Namen der Konfiguration an. Wählen Sie unter „Speicher“ die Option „Microsoft Azure-Speicher“ aus.
1. Suchen Sie unter Speicherkonfigurationspfad die Cloud-Konfiguration, die die Anmeldeinformationen des kundeneigenen Azure Storage-Kontos enthält, und wählen Sie sie aus.
1. Geben Sie im Quellordner den Namen des Azure Storage-Containers und des Ordners mit Datensätzen an.
1. Geben Sie im Zielordner den Pfad des Azure-Speicher-Containers und des Ordners an, in dem die generierten Dokumente gespeichert werden sollen.
1. Klicken Sie auf „Erstellen“.

Ihre Experience Manager-Instanz ist jetzt mit dem Microsoft Azure-Speicher verbunden und so konfiguriert, dass Daten abgerufen und an bestimmte Speicherorte im Microsoft Azure-Speicher gesendet werden.

### Hochladen von Vorlagen und anderen Assets in Ihre Experience Manager-Instanz {#upload-templates-and-other-assets-to-your-AEM-instance}

Eine Organisation verfügt in der Regel über mehrere Vorlagen. Zum Beispiel eine Vorlage für Kreditkartenauszüge, Leistungsmitteilungen und Anträge. Laden Sie alle diese XDP- und PDF-Vorlagen in Ihre Experience Manager-Instanz hoch. Hochladen von Vorlagen:

1. Öffnen Sie die Experience Manager-Instanz.
1. Navigieren Sie zu „Forms“ > „Forms und Dokumente“.
1. Klicken Sie auf „Erstellen“ > „Ordner“ und erstellen Sie einen Ordner. Öffnen Sie den Ordner.
1. Klicken Sie auf „Erstellen“ > „Datei-Upload“ und laden Sie die Vorlagen hoch.

## Verwenden der Batch-API zum Generieren von Dokumenten {#use-batch-API-to-generate-documents}

Um eine Batch-API zu verwenden, erstellen Sie eine Batch-Konfiguration und führen Sie eine auf dieser Konfiguration basierende Ausführung aus. Die API-Dokumentation enthält Informationen zu APIs zum Erstellen und Ausführen eines Batches sowie zu entsprechenden Parametern und möglichen Fehlern. Sie können die [API-Definitionsdatei](assets/batch-api.yaml) speichern und in [Postman](https://go.postman.co/home) oder eine ähnliche Software hochladen, um die APIs zum Erstellen und Ausführen eines Batch-Vorgangs zu testen.

### Erstellen eines Batches {#create-a-batch}

Verwenden Sie zum Erstellen eines Batches die `GET /config`-API. Schließen Sie die folgenden obligatorischen Eigenschaften in den Text der HTTP-Anforderung ein:


* **configName**: Geben Sie den eindeutigen Namen des Batches an. Zum Beispiel: `wknd-job`
* **dataSourceConfigUri**: Geben Sie den Speicherort der Batch-Datenspeicherkonfiguration an. Es kann sich um den relativen oder absoluten Pfad der Konfiguration handeln. Beispiel: `/conf/global/settings/forms/usc/batch/wknd-batch`
* **outputTypes**: Geben Sie Ausgabeformate an: PDF oder PRINT. Wenn Sie den DRINT-Ausgabetyp verwenden, lesen Sie `printedOutputOptionsList` -Eigenschaft, geben Sie mindestens eine Druckoption an. Die Druckoptionen werden anhand ihres Rendertyps identifiziert, sodass derzeit mehrere Druckoptionen mit demselben Rendertyp nicht zulässig sind. Unterstützt werden PS, PCL, DPL, IPL und ZPL.

* **template**: Geben Sie den absoluten oder relativen Pfad der Vorlage an. Zum Beispiel: `crx:///content/dam/formsanddocuments/wknd/statements.xdp`

Wenn Sie einen relativen Pfad angeben, geben Sie auch einen Inhaltsstamm an. Weitere Informationen zum Inhaltsstamm finden Sie in der API-Dokumentation .

<!-- For example, you include the following JSON in the body of HTTP APIs to create a batch named wknd-job: -->

Nachdem Sie einen Batch erstellt haben, können Sie `GET /config /[configName]/execution/[execution-identifier]` verwenden, um Details zum Batch anzuzeigen.

### Ausführen eines Batches {#run-a-batch}

Um einen Batch auszuführen, verwenden Sie `POST /config /[configName]/execution`. Um beispielsweise einen Batch mit dem Namen „wknd-demo“ auszuführen, verwenden Sie „/config/wknd-demo/execution“. Der Server gibt beim Akzeptieren der Anfrage den HTTP-Antwort-Code 202 zurück. Die API gibt keine Payload zurück, sondern lediglich einen eindeutigen Code (execution-identifier) in der Kopfzeile der HTTP-Antwort für den auf dem Server ausgeführten Batch-Auftrag. Sie können die Ausführungskennung verwenden, um den Status des Batches abzurufen.

>[!NOTE]
>
>Nehmen Sie während der Ausführung des Batches keine Änderungen an den entsprechenden Quell- und Zielordnern, der Datenquellenkonfiguration und der Microsoft Azure-Cloud-Konfiguration vor.

### Überprüfen des Status eines Batches {#status-of-a-batch}

Um den Status eines Batches abzurufen, verwenden Sie `GET /config /[configName]/execution/[execution-identifier]`. Die Ausführungskennung ist im Header der HTTP-Antwort für die Batch-Ausführungsanforderung enthalten.  Die folgende Abbildung zeigt beispielsweise die Ausführungskennung für einen Batch-Auftrag.

Die Antwort der Statusanfrage enthält den Statusabschnitt. Er enthält Details zum Status des Batch-Auftrags, zur Anzahl der bereits in der Pipeline befindlichen Datensätze (bereits gelesen und verarbeitet) und zum Status jedes outputType/renderType(Anzahl der ausgeführten, erfolgreichen und fehlgeschlagenen Elemente). Der Status umfasst auch Start- und Endzeit des Batch-Auftrags sowie ggf. Informationen zu Fehlern. Die Endzeit beträgt -1, bis die Batch-Ausführung tatsächlich abgeschlossen ist.

>[!NOTE]
>
>* Wenn Sie mehrere PRINT-Formate anfordern, enthält der Status mehrere Einträge. Beispiel: PRINT/ZPL, PRINT/IPL.
>* Ein Batch-Auftrag liest nicht alle Datensätze gleichzeitig, sondern liest und erhöht die Anzahl der Datensätze nach und nach. Der Status gibt also bei jeder Ausführung eine andere Anzahl von Datensätzen zurück.


### Anzeigen generierter Dokumente {#view-generated-documents}

Nach Abschluss des Auftrags werden die generierten Dokumente im Ordner `success` an dem in der Batch-Datenspeicherkonfiguration angegebenen Zielspeicherort gespeichert. Wenn Fehler auftreten, erstellt der Service einen Ordner `failure`. Er enthält Informationen über die Art und den Grund von Fehlern.

Sehen wir uns dazu ein Beispiel an: Angenommen, es gibt eine Eingabedatendatei `record1.xml` und zwei Ausgabetypen: `PDF` und `PCL`. Dann enthält der Zielspeicherort zwei Unterordner `pdf` und `pcl`, einen für jeden Ausgabetyp. Nehmen wir an, die PDF-Generierung ist erfolgreich, dann wird die `pdf` Unterordner enthält die `success` Unterordner, der wiederum das eigentliche generierte PDF-Dokument enthält `record1.pdf`. Nehmen wir an, dass die PCL-Generierung fehlgeschlagen ist. Anschließend wird die `pcl` Unterordner enthält einen `failure` Unterordner, der wiederum eine Fehlerdatei enthält `record1.error.txt` enthält Details zum Fehler. Darüber hinaus enthält der Zielspeicherort einen temporären Ordner mit dem Namen `__tmp__` , der bestimmte Dateien enthält, die während der Batch-Ausführung erforderlich sind. Dieser Ordner kann gelöscht werden, wenn keine aktiven Batch-Vorgänge ausgeführt werden, die auf den Zielordner verweisen.

>[!NOTE]
>
>Die Verarbeitung eines Batches kann je nach Anzahl der Eingabedateien und Komplexität der Vorlage etwas dauern. Warten Sie einige Minuten, bevor Sie die Zielordner auf Ausgabedateien überprüfen.

## Zu beachten  {#considerations-for-communications-apis}

### Formulardaten {#form-data}

Kommunikations-APIs akzeptieren sowohl ein Formular-Design, das normalerweise in Designer erstellt wird, als auch XML-Formulardaten als Eingabe. Zum Ausfüllen eines Dokuments mit Daten muss in den XML-Formulardaten für jedes Formularfeld, das ausgefüllt werden soll, ein XML-Element vorhanden sein. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Es ist nicht erforderlich, die Reihenfolge zu berücksichtigen, in der die XML-Elemente angezeigt werden. Wichtig ist, dass die XML-Elemente mit entsprechenden Werten angegeben werden.

Beachten Sie das folgende Beispielformular für einen Kreditantrag:

![Kreditantragsformular](assets/loanFormData.png)

Um Daten mit diesem Formular-Design zusammenzuführen, erstellen Sie eine XML-Datenquelle, die dem Formular entspricht. Die folgende XML-Datei stellt eine XML-Datenquelle dar, die dem Beispielformular für einen Hypothekenantrag entspricht.

```XML
<?xml version="1.0" encoding="UTF-8" ?>
- <xfa:datasets xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/">
- <xfa:data>
- <data>
    - <Layer>
        <closeDate>1/26/2007</closeDate>
        <lastName>Johnson</lastName>
        <firstName>Jerry</firstName>
        <mailingAddress>JJohnson@NoMailServer.com</mailingAddress>
        <city>New York</city>
        <zipCode>00501</zipCode>
        <state>NY</state>
        <dateBirth>26/08/1973</dateBirth>
        <middleInitials>D</middleInitials>
        <socialSecurityNumber>(555) 555-5555</socialSecurityNumber>
        <phoneNumber>5555550000</phoneNumber>
    </Layer>
    - <Mortgage>
        <mortgageAmount>295000.00</mortgageAmount>
        <monthlyMortgagePayment>1724.54</monthlyMortgagePayment>
        <purchasePrice>300000</purchasePrice>
        <downPayment>5000</downPayment>
        <term>25</term>
        <interestRate>5.00</interestRate>
    </Mortgage>
</data>
</xfa:data>
</xfa:datasets>
```

### Unterstützte Dokumenttypen {#supported-document-types}

Für den vollständigen Zugriff auf die Rendering-Funktionen der Kommunikations-APIs wird empfohlen, eine XDP-Datei als Eingabe zu verwenden. Manchmal kann eine PDF-Datei verwendet werden. Bei Verwendung einer PDF-Datei als Eingabe gelten jedoch die folgenden Einschränkungen:

Ein PDF-Dokument, das keinen XFA-Stream enthält, kann nicht als PostScript, PCL oder ZPL gerendert werden. Kommunikations-APIs können PDF-Dokumente mit XFA-Streams (d. h. in Designer erstellte Formulare) in Laser- und Label-Formate wiedergeben. Wenn das PDF-Dokument signiert oder zertifiziert ist oder Verwendungsrechte enthält (die mithilfe des AEM Forms Reader Extensions-Service angewendet werden), kann es nicht in diesen Druckformaten gerendert werden.

## API-Referenzdokumentation

Die Dokumentation zur API-Referenz enthält detaillierte Informationen zu allen Parametern, Authentifizierungsmethoden und verschiedenen Services, die von APIs bereitgestellt werden. Die API-Referenzdokumentation ist auch im .yaml-Format verfügbar. Sie können die [Batch-APIs](assets/batch-api.yaml) als Datei herunterladen und in Postman hochladen, um die Funktionalität der APIs zu überprüfen.

## Bekannte Probleme {#known-issues}

* Stellen Sie sicher, dass die XML-Datendatei nicht den XML-Deklarations-Header enthält. Zum Beispiel: `<?xml version="1.0" encoding="UTF-8"?>`

* Wenn PRINT angegeben ist, kann ein bestimmter Rendertyp nur einmal in der Liste der Druckoptionen angegeben werden. Beispielsweise können Sie nicht über zwei Druckoptionen verfügen, mit denen jeweils ein PCL-Rendertyp angegeben wird.

* Ändern Sie die in einer Batch-Konfiguration verwendete Datenquellenkonfiguration (USC) und die Azure-Cloud-Konfiguration nicht, während der Batch ausgeführt wird. Wenn eine Aktualisierung erforderlich ist, erstellen Sie auch nach der Ausführung eine Kopie der Konfiguration, anstatt die in einer vorhandenen Batch-Konfiguration verwendete zu aktualisieren.

## Best Practices {#best-practices}

* Adobe empfiehlt, Datendateien im Blob-Container-Store in der vom Experience Manager Cloud Service verwendeten Cloud-Region zu hosten.

## Häufig gestellte Fragen  {#faq}

**Kann ich einen überwachten Ordner oder andere Speichermechanismen verwenden, um Eingabe und Ausgabe zu speichern?**

Derzeit können Sie den Microsoft Azure-Speicher verwenden, um Eingabedaten und generierte Dokumente zu speichern. Der Microsoft Azure-Speicher bietet verschiedene Optionen zur [Automatisierung von Datenverschiebungsvorgängen](https://docs.microsoft.com/de-de/azure/storage/common/storage-use-azcopy-v10).

**Ist ein Microsoft Azure-Speicherkonto in der Experience Manager Forms Cloud Service-Lizenz enthalten?**

Das Microsoft Azure-Speicherkonto ist unabhängig von der Experience Manager Forms Cloud Service-Lizenz.

**Speichern Kommunikation-APIs Daten auf Experience Manager Forms Cloud Service-Servern?**

Eingabe- und Ausgabedaten werden nur im Microsoft Azure-Speicher gespeichert.

**Sind Kommunikations-APIs nur für Experience Manager Forms Cloud Service verfügbar? Kann ich ähnliche Funktionen in der On-Premise-Umgebung erhalten?**

Sie können den AEM Forms Output-Service verwenden, um eine Vorlage (XFA oder PDF) mit Kundendaten zu kombinieren und Dokumente in den Formaten PDF, PS, PCL und ZPL zu generieren.

Im Vergleich zur On-Premise-Umgebung bietet Cloud Service zusätzliche Vorteile durch automatische Skalierung und Kosteneffizienz.

<!--**Where is data processed?**

**Who has access to data?**

**Is data encrypted?**

**Where is data hosted?** -->

**Kann ich mehrere Batch-Vorgänge gleichzeitig ausführen?**
Ja, Sie können mehrere Batch-Vorgänge gleichzeitig ausführen. Verwenden Sie immer unterschiedliche Quell- und Zielordner für jeden Vorgang, um Konflikte zu vermeiden.
