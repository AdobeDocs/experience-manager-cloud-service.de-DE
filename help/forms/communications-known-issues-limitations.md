---
title: 'Bekannte Probleme '
description: Best Practices für die Kommunikation, bekannte Probleme und Einschränkungen
source-git-commit: bf7ce5850700141a8a6d1eeb90ea0fd21ff811e7
workflow-type: tm+mt
source-wordcount: '1703'
ht-degree: 91%

---


# Überlegungen zu bekannten Problemen und Best Practices {#best-practices-known-issues-and-limitations}

Bevor Sie mit der Verwendung von Kommunikations-APIs beginnen, lesen Sie die folgenden Überlegungen, bekannten Probleme und häufig gestellten Fragen:

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


### Druckbereiche {#printable-areas}

Der standardmäßige, nicht druckbare Rand von 0,25 Zoll ist für Etikettendrucker nicht exakt und variiert von Drucker zu Drucker und von Beschriftungsgröße zu Beschriftungsgröße. Es wird jedoch empfohlen, den 0,25-Zoll-Rand beizubehalten oder ihn zu reduzieren. Es wird in jedem Fall empfohlen, den nicht druckbaren Rand nicht zu vergrößern. Andernfalls werden Informationen im druckbaren Bereich nicht ordnungsgemäß gedruckt.

Stellen Sie immer sicher, dass Sie die richtige XDC-Datei für den Drucker verwenden. Vermeiden Sie beispielsweise die Auswahl einer XDC-Datei für einen 300-dpi-Drucker und das Senden des Dokuments an einen 200-dpi-Drucker.

### Skripte nur für XFA-Formulare (XDP/PDF) {#scripts}

Ein Formular-Design, das mit den Kommunikations-APIs verwendet wird, kann Skripte enthalten, die auf dem Server ausgeführt werden. Stellen Sie sicher, dass ein Formular-Design keine Skripte enthält, die auf dem Client ausgeführt werden. Informationen zum Erstellen von Formularentwurfsskripten finden Sie unter [Designer-Hilfe](use-forms-designer.md).

<!-- #### Working with Fonts
 Document Considerations for Working with Fonts>> -->

### Schriftzuordnung {#font-mapping}

Um ein Formular zu entwerfen, das druckerresidente Schriftarten verwendet, wählen Sie in Designer den Namen einer Schriftart, die mit den auf dem Drucker verfügbaren Schriftarten übereinstimmt. Eine Liste der für PCL oder PostScript unterstützten Schriftarten befindet sich in den entsprechenden Geräteprofilen (XDC-Dateien). Alternativ kann eine Schriftzuordnung erstellt werden, um nicht druckerresidente Schriftarten druckerresidenten Schriftarten mit einem anderen Schriftartennamen zuzuordnen. In einem PostScript-Szenario können beispielsweise Verweise auf die Schriftart Arial® der druckerresidenten Helvetica®-Schriftart zugeordnet werden.

Wenn eine Schriftart auf einem Client-Computer installiert ist, ist sie in der Dropdown-Liste in Designer verfügbar. Wenn die Schriftart nicht installiert ist, müssen Sie den Schriftnamen manuell angeben. Die Option „Nicht verfügbare Schriften dauerhaft ersetzen“ in Designer kann deaktiviert sein. Andernfalls wird beim Speichern der XDP-Datei in Designer der Name der Ersatzschriftart in die XDP-Datei geschrieben. Dies bedeutet, dass die druckerresidente Schriftart nicht verwendet wird.

Es gibt zwei Arten von OpenType®-Schriftarten. Ein Typ ist eine TrueType OpenType®-Schriftart, die von PCL unterstützt wird. Der andere ist CFF OpenType®. Die PDF- und PostScript-Ausgabe unterstützt eingebettete Type-1-, TrueType- und OpenType®-Schriftarten. Die PCL-Ausgabe unterstützt eingebettete TrueType-Schriftarten.

Type-1- und OpenType®-Schriftarten sind nicht in die PCL-Ausgabe eingebettet. Inhalte, die mit Type-1- und OpenType®-Schriftarten formatiert sind, werden gerastert und als ein Bitmap-Bild generiert, das groß und langsamer zu generieren sein kann.

Heruntergeladene oder eingebettete Schriftarten werden beim Generieren der PostScript-, PCL- oder PDF-Ausgabe automatisch ersetzt. Dies bedeutet, dass nur die Teilmenge der Schriftzeichen, die zum ordnungsgemäßen Rendern des generierten Dokuments erforderlich sind, in der generierten Ausgabe enthalten ist.

### Arbeiten mit Geräteprofildateien (XDC-Datei) {#working-with-xdc-files}

Ein Geräteprofil (XDC-Datei) ist eine Druckerbeschreibungsdatei im XML-Format. Diese Datei ermöglicht es den Kommunikations-APIs, Dokumente als Laser- oder Etikettendruckerformate auszugeben. Kommunikations-APIs verwenden die XDC-Dateien, einschließlich der folgenden:

* hppcl5c.xdc

* hppcl5e.xdc

* ps_plain_level3.xdc

* ps_plain.xdc

* zpl300.xdc

* zpl600.xdc

* zpl300.xdc

* ipl300.xdc

* ipl400.xdc

* tpcl600.xdc

* dpl300.xdc

* dpl406.xdc

* dpl600.xdc

Sie können die bereitgestellten XDC-Dateien verwenden, um Druckdokumente zu erstellen oder diese nach Ihren Anforderungen zu ändern.
<!-- It is not necessary to modify these files to create documents. However, you can modify them to meet your business requirements. -->

Diese Dateien sind Beispiel-XDC-Dateien, die die Funktionsmerkmale bestimmter Drucker, z. B. residente Schriftarten, Papierfächer und Hefter, unterstützen. Dieser Beispieldateien sollen Ihnen verständlich machen, wie Sie Ihre eigenen Drucker mithilfe von Geräteprofilen einrichten können. Die Beispiele sind auch ein Ausgangspunkt für ähnliche Drucker in derselben Produktlinie.

### Arbeiten mit der XCI-Konfigurationsdatei {#working-with-xci-files}

Kommunikations-APIs verwenden eine XCI-Konfigurationsdatei, um Aufgaben auszuführen, z. B. um zu steuern, ob es sich bei der Ausgabe um einen einzelnen Bereich handelt oder ob sie paginiert wird. Obwohl diese Datei Einstellungen enthält, die festgelegt werden können, ist es nicht üblich, diesen Wert zu ändern. <!-- The default.xci file is located in the svcdata\XMLFormService folder. -->

Sie können eine modifizierte XCI-Datei übergeben, während Sie eine Kommunikations-API verwenden. Erstellen Sie dabei eine Kopie der Standarddatei, ändern Sie nur die Werte, die geändert werden müssen, um Ihre Geschäftsanforderungen zu erfüllen, und verwenden Sie die geänderte XCI-Datei.

Kommunikations-APIs beginnen mit der standardmäßigen XCI-Datei (oder der geänderten Datei). Anschließend werden Werte angewendet, die mithilfe der Kommunikations-APIs angegeben werden. Diese Werte überschreiben die XCI-Einstellungen.

Die folgende Tabelle gibt die XCI-Optionen an.

| XCI-Option | Beschreibung |
| ------------------------------------| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| config/present/pdf/creator | Identifiziert den Ersteller des Dokuments mithilfe des Eintrags „Ersteller“ im Wörterbuch zu Dokumentinformationen. Weitere Informationen zu diesem Wörterbuch finden Sie im Handbuch „PDF-Referenzen“. |
| config/present/pdf/producer | Identifiziert den Produzenten des Dokuments mithilfe des Eintrags „Produzent“ im Wörterbuch zu Dokumentinformationen. Weitere Informationen zu diesem Wörterbuch finden Sie im Handbuch „PDF-Referenzen“. |
| config/present/layout | Steuert, ob es sich bei der Ausgabe um einen einzelnen Bereich handelt oder ob sie paginiert wird. |
| config/present/pdf/compression/level | Gibt den Komprimierungsgrad an, der beim Generieren eines PDF-Dokuments verwendet werden soll. |
| config/present/pdf/scriptModel | Steuert, ob XFA-spezifische Informationen im PDF-Ausgabedokument enthalten sind. |
| config/present/common/data/adjustData | Steuert, ob die XFA-Anwendung die Daten nach dem Zusammenführen anpasst. |
| config/present/pdf/renderPolicy | Steuert, ob die Erstellung des Seiteninhalts auf dem Server erfolgt oder zum Client ausgelagert wird. |
| config/present/common/locale | Gibt das im Ausgabedokument verwendete Standardgebietsschema an. |
| config/present/destination | Gibt das Ausgabeformat an, wenn es in einem vorhandenen Element enthalten ist. Gibt die Aktion an, die beim Öffnen des Dokuments in einem interaktiven Client ausgeführt werden soll, wenn sie in einem openAction-Element enthalten ist. |
| config/present/output/type | Gibt entweder die Art der Komprimierung an, die auf eine Datei angewendet werden soll, oder den Typ der zu erzeugenden Ausgabe. |
| config/present/common/temp/uri | Gibt den Formular-URI an. |
| config/present/common/template/base | Liefert einen Basisspeicherort für URIs im Formular-Design. Wenn dieses Element fehlt oder leer ist, wird der Speicherort des Formular-Designs als Basis verwendet. |
| config/present/common/log/to | Steuert den Speicherort, an den Protokolldaten oder Ausgabedaten geschrieben werden. |
| config/present/output/to | Steuert den Speicherort, an den Protokolldaten oder Ausgabedaten geschrieben werden. |
| config/present/script/currentPage | Gibt die Anfangsseite an, auf der das Dokument geöffnet wird. |
| config/present/script/exclude | Informiert AEM Forms-Server-/Kommunikations-APIs, welche Ereignisse ignoriert werden sollen. |
| config/present/pdf/linearized | Steuert, ob das ausgegebene PDF-Dokument linearisiert ist. |
| config/present/script/runScripts | Steuert, welcher Satz von Skripten von AEM Forms ausgeführt wird. |
| config/present/pdf/tagged | Steuert die Einbeziehung von Tags in das PDF-Ausgabedokument. Tags sind im Kontext von PDF zusätzliche Informationen, die in einem Dokument enthalten sind, um die logische Struktur des Dokuments anzuzeigen. Tags unterstützen Barrierefreiheitshilfen und die Neuformatierung. Beispielsweise kann eine Seitenzahl als Artefakt getaggt werden, sodass eine Bildschirmlesehilfe sie nicht in der Mitte des Textes anzeigt. Obwohl Tags ein Dokument nützlicher machen, erhöhen sie auch die Größe des Dokuments und die Verarbeitungszeit bei der Erstellung. |
| config/present/pdf/version | Gibt die Version des zu erzeugenden PDF-Dokuments an. |


## Bekannte Probleme

* Sie können einen bestimmten Rendertyp (PDF, PRINT) nur einmal in der Liste der Druckoptionen verwenden. Beispielsweise können Sie nicht über zwei PRINT-Optionen verfügen, die jeweils einen PCL-Rendertyp angeben.

* Für eine Batch-Konfiguration ist nur eine Instanz der Kombination von Werten von OutputType (PDF, PRINT) und RenderType (PostScript, PCL, IPL, ZPL usw.) zulässig.

* Bei asynchronen APIs (Batch-Verarbeitung) wird die standardmäßige Datensatzebene auf 2 gesetzt. Sie können eine benutzerdefinierte XCI-Datei verwenden, um die Datensatzebene in 1 zu ändern.

* Wenn die standardmäßige XCI-Datei konfiguriert ist, enthält sie den Pfad bis zur ursprünglichen Ausgabe. Beispiel `/content/dam/formsanddocuments/default.xci/jcr:content/renditions/original`



## Best Practices

* Adobe empfiehlt, Datendateien im Blob-Container-Store in der von AEM Cloud Service verwendeten Cloud-Region zu hosten.

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
