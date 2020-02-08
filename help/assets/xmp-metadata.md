---
title: XMP-Metadaten
description: Erfahren Sie mehr über den XMP-Metadatenstandard (Extensible Metadata Platform) für die Metadatenverwaltung. Es wird von AEM als standardisiertes Format für die Erstellung, Verarbeitung und den Austausch von Metadaten verwendet.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# XMP metadata {#xmp-metadata}

XMP (Extensible Metadata Platform) ist der Metadatenstandard, der von AEM Assets für die gesamte Metadatenverwaltung eingesetzt wird. XMP liefert ein Standardformat für die Erstellung, die Verarbeitung und den Austausch von Metadaten für eine Vielzahl an Anwendungen.

Aside from offering universal metadata encoding that can be embedded into all file formats, XMP provides a rich [content model](#xmp-core-concepts) and is [supported by Adobe](#advantages-of-xmp) and other companies, so that users of XMP in combination with AEM Assets have a powerful platform to build upon.

## XMP-Übersicht und Ökosystem {#xmp-ecosystem}

AEM Assets unterstützt nativ den XMP-Metadatenstandard. XMP ist ein Standard für die Verarbeitung und Speicherung von standardisierten und proprietären Metadaten in digitalen Assets. XMP ist als der gemeinsame Standard konzipiert, dank dem mehrere Anwendungen effektiv mit Metadaten arbeiten können.

Produktionsexperten nutzen beispielsweise die integrierte XMP-Unterstützung innerhalb der Adobe-Anwendungen, um Informationen über mehrere Dateiformate hinweg zu übergeben. Das AEM Assets-Repository extrahiert die XMP-Metadaten und verwaltet damit den Inhaltslebenszyklus. Außerdem wird die Erstellung von Automatisierungs-Workflows ermöglicht.

XMP standardisiert die Art, wie Metadaten definiert, erstellt und verarbeitet werden, indem ein Datenmodell, ein Speichermodell und Schemata bereitgestellt werden. Diese Grundlagen werden alle in diesem Abschnitt behandelt.

Alle Legacy-Metadaten aus EXIF, ID3 oder Microsoft Office werden automatisch in XMP übersetzt. Dies kann erweitert werden, um kundenspezifische Metadatenschemata wie Produktkataloge zu unterstützen.

Metadaten in XMP bestehen aus einer Reihe von Eigenschaften. Diese Eigenschaften sind immer mit einer bestimmten Entität verknüpft, die als Ressource bezeichnet wird. Das heißt, die Eigenschaften beziehen sich auf die Ressource. Bei XMP ist die Ressource stets das Asset.

XMP definiert ein [Metadaten](https://en.wikipedia.org/wiki/Metadata)-Modell, das mit jedem definierten Set aus Metadatenelementen verwendet werden kann. XMP definiert außerdem bestimmte [Schemata](https://en.wikipedia.org/wiki/XML_schema) für grundlegende Eigenschaften, die zum Aufzeichnen des Verlaufs einer Ressource durch mehrere Verarbeitungsschritte nützlich sind – vom Fotografieren, [Scannen](https://en.wikipedia.org/wiki/Image_scanner) oder Verfassen als Text über Fotobearbeitungsschritte (wie [Beschneiden](https://en.wikipedia.org/wiki/Cropping_%28image%29) oder Farbanpassung) bis hin zur Zusammenstellung des endgültigen Bildes. Dank XMP kann jedes dabei verwendete Softwareprogramm oder Gerät eigene Informationen zu einer digitalen Ressource hinzufügen, die dann in der endgültigen digitalen Datei beibehalten werden kann.

XMP wird meist mit einer Teilmenge des [W3C](https://en.wikipedia.org/wiki/World_Wide_Web_Consortium) [Resource Description Framework](https://en.wikipedia.org/wiki/Resource_Description_Framework) (RDF) serialisiert und gespeichert. Dies wird wiederum im [XML](https://en.wikipedia.org/wiki/XML) ausgedrückt.

### Vorteile von XMP {#advantages-of-xmp}

XMP bietet die folgenden Vorteile gegenüber anderen Kodierungsstandards und Schemata:

* XMP-basierte Metadaten sind sehr leistungsstark und fein granuliert.
* Mit XMP können Sie mehrere Werte für eine Eigenschaft festlegen.
* XMP verfügt über standardisierte Kodierung, wodurch Sie Metadaten einfach austauschen können.
* XMP ist erweiterbar. Sie können Ihren Assets weitere Informationen hinzufügen.

Das XMP-Standardformat ist erweiterbar, sodass Sie den XMP-Daten benutzerdefinierte Arten von Metadaten hinzufügen können. Bei EXIF ist dies dagegen nicht möglich. Die feste Liste der Eigenschaften kann nicht erweitert werden.

>[!NOTE]
>
>XMP lässt im Allgemeinen nicht zu, dass binäre Datentypen eingebettet werden. To carry binary data in XMP, for example, thumbnail images, they must be encoded in an XML-friendly format such as `Base64`.

### XMP core concepts {#xmp-core-concepts}

**Namespaces und Schemata**

Ein XMP-Schema ist ein Set aus Eigenschaftsnamen in einem gemeinsamen XML-Namespace, der
den Datentyp und beschreibende Informationen umfasst. Ein XMP-Schema wird durch die zugehörige XML-Namespace-URI identifiziert. Durch Verwendung von Namespaces werden Konflikte zwischen Eigenschaften in verschiedenen Schemata verhindert, die denselben Namen, aber eine andere Bedeutung haben.

Beispiel: Die Eigenschaft **Creator** in zwei unabhängig voneinander entwickelten Schemata kann einerseits für die Person stehen, die das Asset erstellt hat, oder andererseits für die Anwendung, von der das Asset erstellt wurde (z. B. Adobe Photoshop).

**XMP-Eigenschaften und -Werte**

XMP kann Eigenschaften von einem oder mehreren der Schemata umfassen. Viele Adobe-Anwendungen verwenden beispielsweise Folgendes:

* Dublin-Kernschema: `dc:title`, `dc:creator`, `dc:subject`, `dc:format`, `dc:rights`
* XMP-Basisschema: `xmp:CreateDate`, `xmp:CreatorTool`, `xmp:ModifyDate``xmp:metadataDate`
* XMP Rights Management-Schema: `xmpRights:WebStatement`, `xmpRights:Marked`
* XMP media management schema: `xmpMM:DocumentID`

**Sprachliche Alternativen**

Mit XMP können Sie die Eigenschaft `xml:lang` zu Texteigenschaften hinzufügen, um die Sprache des Textes anzugeben.

## XMP-Writeback in Ausgabeformate {#xmp-writeback-to-renditions}

Diese XMP-Rückgabefunktion in Adobe Experience Manager (AEM) Assets repliziert Änderungen an Asset-Metadaten in den Darstellungen des Assets.

Wenn Sie die Metadaten für ein Asset aus AEM Assets ändern oder das Asset hochladen, werden Änderungen zunächst innerhalb des Asset-Knotens in CRXDE gespeichert.

Die XMP-Rückgabefunktion propagiert die Änderungen der Metadaten an alle oder bestimmte Darstellungen des Assets.

Consider a scenario where you modify the [!UICONTROL Title] property of the asset titled `Classic Leather` to `Nylon`.

![metadata](assets/metadata.png)

In diesem Fall speichert AEM Assets die Änderungen an der Eigenschaft **[!UICONTROL Titel]** im Parameter `dc:title` der in der Elementhierarchie gespeicherten Asset-Metadaten.

![metadata_saved](assets/metadata_stored.png)

AEM Assets propagiert die Metadatenänderungen jedoch nicht automatisch in die Ausgabeformate eines Assets.

Mit der XMP-Rückgabefunktion können Sie die Metadatenänderungen an alle oder bestimmte Darstellungen des Assets weiterleiten. Die Änderungen werden allerdings nicht unter dem Metadatenknoten in der Asset-Hierarchie gespeichert. Stattdessen werden die Änderungen mit dieser Funktion in die Binärdateien für die Ausgabeformate eingebettet.

### XMP-Schreibback aktivieren {#enable-xmp-writeback}

<!-- asgupta, Engg: Need attention here to update the configuration manager changes.
-->

Um Metadatenänderungen beim Hochladen des Assets in die Ausgabeformate zu propagieren, bearbeiten Sie die Konfiguration **[!UICONTROL Adobe CQ DAM Rendition Maker]** in Configuration Manager.

1. Um Configuration Manager zu öffnen, rufen Sie auf `https://[aem_server]:[port]/system/console/configMgr`.
1. Open the **[!UICONTROL Adobe CQ DAM Rendition Maker]** configuration.
1. Select the **[!UICONTROL Propagate XMP]** option, and then save the changes.

### XMP-Rückmeldung für bestimmte Darstellungen aktivieren {#enable-xmp-writeback-for-specific-renditions}

To let the XMP write-back feature propagate metadata changes to select renditions, specify these renditions to the [!UICONTROL XMP Writeback Process] workflow step of DAM Metadata WriteBack workflow. Standardmäßig ist dieser Schritt mit der ursprünglichen Darstellung konfiguriert.

Führen Sie die folgenden Schritte aus, damit die XMP-Funktion zum Zurückschreiben von Metadaten an die Darstellungsminiaturen 140.100.png und 319.319.png weitergegeben wird.

1. Tap/click the AEM logo, and then navigate to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. From the Models page, open the **[!UICONTROL DAM Metadata Writeback]** workflow model.
1. In the **[!UICONTROL DAM Metadata Writeback]** properties page, open the **[!UICONTROL XMP Writeback Process]** step.
1. In the **[!UICONTROL Step Properties]** dialog box, tap/click the **[!UICONTROL Process]** tab.
1. Fügen Sie im Feld **[!UICONTROL Argumente]** hinzu `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`und tippen/klicken Sie dann auf **[!UICONTROL OK]**.

   ![step_properties](assets/step_properties.png)

1. Speichern Sie die Änderungen.
1. To regenerate the Pyramid TIFF (PTIFF) renditions for Dynamic Media images with the new attributes, add the **[!UICONTROL Dynamic Media Process Image Assets]** step to the DAM Metadata write-back workflow. PTIFF-Wiedergaben werden nur lokal in einer Dynamic Media Hybrid-Implementierung erstellt und gespeichert.

1. Speichern Sie den Workflow.

Die Änderungen an den Metadaten werden an die Darstellungen thumbnail.140.100.png und thumbnail.319.319.png des Assets weitergeleitet, nicht an die anderen.

<!--
>[!NOTE]
>
>For XMP writeback issues in 64 bit Linux, see [How to enable XMP write-back on 64-bit RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>For more information about supported platforms, see [XMP metadata write-back prerequisites](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).
-->

### XMP-Metadaten filtern {#filtering-xmp-metadata}

AEM Assets unterstützt sowohl die Blacklist- als auch die Whitelist-Filterung von Eigenschaften/Knoten für XMP-Metadaten, die aus Asset-Binärdateien gelesen und bei der Erfassung von Assets in JCR gespeichert werden.

Bei der Filterung nach der Blacklist können Sie alle XMP-Metadateneigenschaften importieren – mit Ausnahme der Eigenschaften, für die ein Ausschluss angegeben ist. Jedoch ist der Name der zu filternden Knoten für Elementtypen wie INDD-Dateien mit enormen Mengen an XMP-Metadaten (z. B. 1.000 Knoten mit 10.000 Eigenschaften) nicht immer bereits im Voraus bekannt. Wenn durch das Filtern nach der Blacklist eine große Anzahl von Assets mit vielen XMP-Metadaten importiert werden kann, kann es zu Stabilitätsproblemen bei AEM-Instanz/-Cluster kommen, zum Beispiel zu blockierten Beobachtungswarteschlangen.

Dieses Problem lässt sich mit dem Whitelist-Filter für XMP-Metadaten lösen, mit dem Sie die zu importierenden XMP-Eigenschaften definieren können. Auf diese Weise werden andere/unbekannte XMP-Eigenschaften ignoriert. Aus Gründen der Abwärtskompatibilität können Sie einige dieser Eigenschaften dem Blacklist-Filter hinzufügen.

>[!NOTE]
>
>Die Filterung funktioniert nur für aus XMP-Quellen in Asset-Binärdateien abgeleitete Eigenschaften. Bei Eigenschaften, die aus XMP-fremden Quellen wie EXIF- und IPTC-Formaten abgeleitet wurden, funktioniert die Filterung nicht. Beispielsweise wird das Datum der Asset-Erstellung in der Eigenschaft `CreateDate` in EXIF TIFF gespeichert. AEM meldet diesen Wert im Metadatenfeld `exif:DateTimeOriginal`. Da es sich um eine andere Quelle als XMP handelt, funktioniert die Filterung nicht bei dieser Eigenschaft.

1. Um Configuration Manager zu öffnen, rufen Sie auf `https://[aem_server]:[port]/system/console/configMgr`.
1. Open the **[!UICONTROL Adobe CQ DAM XmpFilter]** configuration.
1. To apply whitelist filtering, select **[!UICONTROL Apply Whitelist to XMP Properties]**, and specify the properties to be imported in the **[!UICONTROL Whitelisted XML Names for XMP filtering]** box.

1. To filter out blacklisted XMP properties after applying whitelist filtering, specify them in the **[!UICONTROL Blacklisted XML Names for XMP filtering]** box.

   >[!NOTE]
   >
   >Die Option **[!UICONTROL Blacklist auf XMP-Eigenschaften anwenden]** ist standardmäßig ausgewählt. Das heißt, das Filtern nach der Blacklist ist standardmäßig aktiviert. To disable blacklist filtering, unselect the **[!UICONTROL Apply Blacklist to XMP Properties]** option.

1. Speichern Sie die Änderungen.

>[!MORELIKETHIS]
>
>* [XMP-Spezifikation von Adobe](https://www.adobe.com/devnet/xmp.html)