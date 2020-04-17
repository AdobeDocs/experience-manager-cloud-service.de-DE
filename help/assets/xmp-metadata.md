---
title: XMP-Metadaten
description: Erfahren Sie mehr über den XMP-Metadatenstandard (Extensible Metadata Platform) für die Metadatenverwaltung. Er wird von AEM als standardisiertes Format für die Erstellung, Verarbeitung und den Austausch von Metadaten verwendet.
contentOwner: AG
translation-type: ht
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# XMP-Metadaten {#xmp-metadata}

XMP (Extensible Metadata Platform) ist der Metadatenstandard, der von AEM Assets für die gesamte Metadatenverwaltung eingesetzt wird. XMP liefert ein Standardformat für die Erstellung, die Verarbeitung und den Austausch von Metadaten für eine Vielzahl an Anwendungen.

XMP bietet nicht nur universelle Metadatenkodierung, die in alle Dateiformate eingebettet werden kann, sondern auch ein [Rich-Content-Modell](#xmp-core-concepts). Außerdem wird XMP [von Adobe](#advantages-of-xmp) und anderen Unternehmen unterstützt, sodass Benutzer, die XMP in Kombination mit AEM Assets einsetzen, über eine leistungsstarke Plattform verfügen.

## XMP-Übersicht und Ökosystem {#xmp-ecosystem}

AEM Assets unterstützt nativ den XMP-Metadatenstandard. XMP ist ein Standard für die Verarbeitung und Speicherung von standardisierten und proprietären Metadaten in digitalen Assets. XMP ist als der gemeinsame Standard konzipiert, dank dem mehrere Anwendungen effektiv mit Metadaten arbeiten können.

Produktionsexperten nutzen beispielsweise die integrierte XMP-Unterstützung innerhalb der Adobe-Anwendungen, um Informationen über mehrere Dateiformate hinweg zu übergeben. Das AEM Assets-Repository extrahiert die XMP-Metadaten und verwaltet damit den Inhaltslebenszyklus. Außerdem wird die Erstellung von Automatisierungs-Workflows ermöglicht.

XMP standardisiert die Art, wie Metadaten definiert, erstellt und verarbeitet werden, indem ein Datenmodell, ein Speichermodell und Schemata bereitgestellt werden. Diese Grundlagen werden alle in diesem Abschnitt behandelt.

Alle Legacy-Metadaten aus EXIF, ID3 oder Microsoft Office werden automatisch in XMP übersetzt. Dies kann erweitert werden, um kundenspezifische Metadatenschemata wie Produktkataloge zu unterstützen.

Metadaten in XMP bestehen aus einer Reihe von Eigenschaften. Diese Eigenschaften sind stets mit einer bestimmten Entität verknüpft, die als Ressource bezeichnet wird. Die Eigenschaften beziehen sich also auf die Ressource. Bei XMP ist die Ressource stets das Asset.

XMP definiert ein [Metadaten](https://de.wikipedia.org/wiki/Metadaten)-Modell, das mit jedem definierten Set aus Metadatenelementen verwendet werden kann. XMP definiert außerdem bestimmte [Schemata](https://de.wikipedia.org/wiki/Schemasprache_(XML)) für grundlegende Eigenschaften, die zum Aufzeichnen des Verlaufs einer Ressource durch mehrere Verarbeitungsschritte nützlich sind – vom Fotografieren, [Scannen](https://de.wikipedia.org/wiki/Scanner_(Datenerfassung)) oder Verfassen als Text über Fotobearbeitungsschritte (wie [Beschneiden](https://de.wikipedia.org/wiki/Cropping) oder Farbanpassung) bis hin zur Zusammenstellung des endgültigen Bildes. Dank XMP kann jedes dabei verwendete Softwareprogramm oder Gerät eigene Informationen zu einer digitalen Ressource hinzufügen, die dann in der endgültigen digitalen Datei beibehalten werden kann.

XMP wird meist mit einer Teilmenge des [W3C](https://de.wikipedia.org/wiki/World_Wide_Web_Consortium) [Resource Description Framework](https://de.wikipedia.org/wiki/Resource_Description_Framework) (RDF) serialisiert und gespeichert. Dies wird wiederum im [XML](https://de.wikipedia.org/wiki/Extensible_Markup_Language) ausgedrückt.

### Vorteile von XMP   {#advantages-of-xmp}

XMP bietet die folgenden Vorteile gegenüber anderen Kodierungsstandards und Schemata:

* XMP-basierte Metadaten sind sehr leistungsstark und fein granuliert.
* Mit XMP können Sie mehrere Werte für eine Eigenschaft festlegen.
* XMP verfügt über standardisierte Kodierung, wodurch Sie Metadaten einfach austauschen können.
* XMP ist erweiterbar. Sie können Assets zusätzliche Informationen hinzufügen.

Das XMP-Standardformat ist erweiterbar, sodass Sie den XMP-Daten benutzerdefinierte Arten von Metadaten hinzufügen können. Bei EXIF ist dies dagegen nicht möglich. Die feste Liste der Eigenschaften kann nicht erweitert werden.

>[!NOTE]
>
>XMP lässt im Allgemeinen nicht zu, dass binäre Datentypen eingebettet werden. Um binäre Daten wie etwa Miniaturansichten in XMP zu übertragen, müssen diese in einem XML-kompatiblen Format wie beispielsweise `Base64` kodiert werden.

### Grundlegende XMP-Konzepte {#xmp-core-concepts}

**Namespaces und Schemata**

Ein XMP-Schema ist ein Set aus Eigenschaftsnamen in einem gemeinsamen XML-Namespace, der
den Datentyp und beschreibende Informationen umfasst. Ein XMP-Schema wird durch die zugehörige XML-Namespace-URI identifiziert. Durch Verwendung von Namespaces werden Konflikte zwischen Eigenschaften in verschiedenen Schemata verhindert, die denselben Namen, aber eine andere Bedeutung haben.

Beispiel: Die Eigenschaft **Creator** in zwei unabhängig voneinander entwickelten Schemata kann einerseits für die Person stehen, die das Asset erstellt hat, oder andererseits für die Anwendung, von der das Asset erstellt wurde (z. B. Adobe Photoshop).

**XMP-Eigenschaften und -Werte**

XMP kann Eigenschaften von einem oder mehreren der Schemata umfassen. Viele Adobe-Anwendungen verwenden beispielsweise Folgendes:

* Dublin Core-Schema: `dc:title`, `dc:creator`, `dc:subject`, `dc:format`, `dc:rights`
* XMP-Basisschema: `xmp:CreateDate`, `xmp:CreatorTool`, `xmp:ModifyDate`, `xmp:metadataDate`
* XMP-Rechteverwaltungsschema: `xmpRights:WebStatement`, `xmpRights:Marked`
* XMP-Medienverwaltungsschema: `xmpMM:DocumentID`

**Sprachalternativen**

Mit XMP können Sie die Eigenschaft `xml:lang` zu Texteigenschaften hinzufügen, um die Sprache des Textes anzugeben.

## XMP-Writeback in Ausgabeformaten {#xmp-writeback-to-renditions}

Die XMP-Writeback-Funktion in Adobe Experience Manager (AEM) Assets repliziert Änderungen von Asset-Metadaten in den Ausgabeformaten des Assets.

Wenn Sie die Metadaten eines Assets in AEM Assets ändern oder das Asset hochladen, werden die Änderungen zunächst im Asset-Knoten in CRXDE gespeichert.

Die XMP-Writeback-Funktion kopiert die Metadatenänderungen in alle oder nur in bestimmte Ausgabeformate des Assets.

Stellen Sie sich vor, Sie ändern die Eigenschaft [!UICONTROL Titel] des Assets `Classic Leather` in `Nylon`.

![Metadaten](assets/metadata.png)

In diesem Fall speichert AEM Assets die Änderungen an der Eigenschaft **[!UICONTROL Titel]** im Parameter `dc:title` der in der Elementhierarchie gespeicherten Asset-Metadaten.

![metadata_stored](assets/metadata_stored.png)

AEM Assets propagiert die Metadatenänderungen jedoch nicht automatisch in die Ausgabeformate eines Assets.

Mit der XMP-Writeback-Funktion können Sie die Metadatenänderungen in alle oder nur in bestimmte Ausgabeformate des Assets kopieren. Die Änderungen werden allerdings nicht unter dem Metadatenknoten in der Asset-Hierarchie gespeichert. Stattdessen werden die Änderungen mit dieser Funktion in die Binärdateien für die Ausgabeformate eingebettet.

### Aktivieren von XMP-Writeback {#enable-xmp-writeback}

<!-- asgupta, Engg: Need attention here to update the configuration manager changes.
-->

Um Metadatenänderungen beim Hochladen des Assets in die Ausgabeformate zu propagieren, bearbeiten Sie die Konfiguration **[!UICONTROL Adobe CQ DAM Rendition Maker]** in Configuration Manager.

1. Um Configuration Manager zu öffnen, rufen Sie `https://[aem_server]:[port]/system/console/configMgr` auf.
1. Öffnen Sie die Konfiguration **[!UICONTROL Adobe CQ DAM Rendition Maker]**.
1. Wählen Sie die Option **[!UICONTROL XMP propagieren]** aus und speichern Sie die Änderungen.

### Aktivieren von XMP-Writeback für bestimmte Ausgabeformate {#enable-xmp-writeback-for-specific-renditions}

Damit die XMP-Writeback-Funktion die Metadatenänderungen in die Ausgabeformate kopieren kann, müssen Sie diese Ausgabeformate im Workflow-Schritt [!UICONTROL XMP-Writeback-Vorgang] des Workflows „DAM-Metadaten-Writeback“ angeben. Standardmäßig ist dieser Schritt mit dem ursprünglichen Format konfiguriert.

Führen Sie folgende Schritte durch, damit die XMP-Writeback-Funktion Metadaten in die Miniaturansichten des Ausgabeformats „140.100.png“ und „319.319.png“ übertragen.

1. Tippen oder klicken Sie auf das AEM-Logo und öffnen Sie **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.
1. Öffnen Sie über die Seite „Modelle“ das Workflow-Modell **[!UICONTROL DAM-Metadaten-Writeback]**.
1. Öffnen Sie auf der Eigenschaftsseite **[!UICONTROL DAM-Metadaten-Writeback]** den Schritt **[!UICONTROL XMP-Writeback-Vorgang]**.
1.  Tippen/Klicken Sie im Dialogfeld **[!UICONTROL Schritt-Eigenschaften]** auf die Registerkarte **[!UICONTROL Prozess]**.
1. Fügen Sie im Feld **[!UICONTROL Argumente]** `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png` hinzu und tippen/klicken Sie auf **[!UICONTROL OK]**.

   ![Schritteigenschaften](assets/step_properties.png)

1. Speichern Sie die Änderungen.
1. Um das Pyramid-PTIFF-Ausgabeformat für Dynamic Media-Bilder mit neuen Attributen zu erstellen, fügen Sie den Schritt **[!UICONTROL Dynamic Media Process Image-Assets]** zum Workflow „DAM-Metadaten-Writeback“ hinzu. PTIFF-Wiedergaben werden nur lokal in einer Dynamic Media Hybrid-Implementierung erstellt und gespeichert.

1. Speichern Sie den Workflow.

Die Metadatenänderungen werden in die Ausgabeformate „thumbnail.140.100.png“ und „thumbnail.319.319.png“ des Elements und nicht auf die anderen Ausgabeformate übertragen.

<!--
>[!NOTE]
>
>For XMP writeback issues in 64 bit Linux, see [How to enable XMP write-back on 64-bit RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>For more information about supported platforms, see [XMP metadata write-back prerequisites](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).
-->

### Filtern von XMP-Metadaten {#filtering-xmp-metadata}

AEM Assets unterstützt das Filtern von Eigenschaften/Knoten nach der Whitelist und der Blacklist für XMP-Metadaten, die von den Binärdateien des Elements gelesen und in JCR gespeichert werden, wenn Assets erfasst werden.

Bei der Filterung nach der Blacklist können Sie alle XMP-Metadateneigenschaften importieren – mit Ausnahme der Eigenschaften, für die ein Ausschluss angegeben ist. Jedoch ist der Name der zu filternden Knoten für Elementtypen wie INDD-Dateien mit enormen Mengen an XMP-Metadaten (z. B. 1.000 Knoten mit 10.000 Eigenschaften) nicht immer bereits im Voraus bekannt. Wenn durch das Filtern nach der Blacklist eine große Anzahl von Assets mit vielen XMP-Metadaten importiert werden kann, kann es zu Stabilitätsproblemen bei AEM-Instanz/-Cluster kommen, zum Beispiel zu blockierten Beobachtungswarteschlangen.

Dieses Problem lässt sich mit dem Whitelist-Filter für XMP-Metadaten lösen, mit dem Sie die zu importierenden XMP-Eigenschaften definieren können. Auf diese Weise werden andere/unbekannte XMP-Eigenschaften ignoriert. Aus Gründen der Abwärtskompatibilität können Sie einige dieser Eigenschaften dem Blacklist-Filter hinzufügen.

>[!NOTE]
>
>Die Filterung funktioniert nur für aus XMP-Quellen in Asset-Binärdateien abgeleitete Eigenschaften. Bei Eigenschaften, die aus XMP-fremden Quellen wie EXIF- und IPTC-Formaten abgeleitet wurden, funktioniert die Filterung nicht. Beispielsweise wird das Datum der Asset-Erstellung in der Eigenschaft `CreateDate` in EXIF TIFF gespeichert. AEM meldet diesen Wert im Metadatenfeld `exif:DateTimeOriginal`. Da es sich um eine andere Quelle als XMP handelt, funktioniert die Filterung nicht bei dieser Eigenschaft.

1. Um Configuration Manager zu öffnen, rufen Sie `https://[aem_server]:[port]/system/console/configMgr` auf.
1. Öffnen Sie die Konfiguration **[!UICONTROL Adobe CQ DAM XmpFilter]**.
1. Um die Filterfunktion nach Whitelist anzuwenden, klicken Sie auf **[!UICONTROL Whitelist auf XMP-Eigenschaften anwenden]** und geben Sie die Eigenschaften an, die in das Feld **[!UICONTROL XML-Namen aus Whitelist für XMP-Filterfunktion]** importiert werden sollen.

1. Um nach Anwendung des Whitelist-Filters die XMP-Eigenschaften aus der Blacklist herauszufiltern, geben Sie sie im Feld **[!UICONTROL XML-Namen aus Blacklist für XMP-Filterfunktion]** an.

   >[!NOTE]
   >
   >Die Option **[!UICONTROL Blacklist auf XMP-Eigenschaften anwenden]** ist standardmäßig ausgewählt. Das heißt, das Filtern nach der Blacklist ist standardmäßig aktiviert. Um die Filterfunktion nach der Blacklist zu deaktivieren, deaktivieren Sie die Option **[!UICONTROL Blacklist auf XMP-Eigenschaften anwenden]**.

1. Speichern Sie die Änderungen.

>[!MORELIKETHIS]
>
>* [XMP-Spezifikation von Adobe](https://www.adobe.com/devnet/xmp.html)