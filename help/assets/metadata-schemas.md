---
title: Metadatenschemata
description: Das Metadatenschema definiert das Layout der Eigenschaftsseite und die für Assets angezeigten Metadaten-Eigenschaften. Erfahren Sie, wie Sie benutzerdefinierte Metadatenschemen erstellen und Metadatenschemen bearbeiten und auf Assets anwenden können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Metadatenschemata {#metadata-schemas}

In Adobe Experience Manager (AEM)-Assets definiert ein Metadatenschema das Layout der Eigenschaftsseite und die für Assets angezeigten Metadateneigenschaften, die das jeweilige Schema verwenden. Zu den Metadateneigenschaften zählen u. a. Titel, Beschreibung, MIME-Typen, Tags usw.

Sie können den Metadaten-Schema-Forms-Editor verwenden, um vorhandene Schemata zu ändern oder benutzerdefinierte Metadaten-Schemata hinzuzufügen.

1. Um die Eigenschaftenseite für ein Asset anzuzeigen, klicken oder tippen Sie in den Schnellaktionen der Kachel „Assets“ in der Kartenansicht auf das Symbol **[!UICONTROL Eigenschaften anzeigen.]** Alternatively, select the asset in the UI and then click or tap the **[!UICONTROL Properties]** icon from the toolbar.
1. Bearbeiten Sie verschiedene Metadateneigenschaften unter den verschiedenen Registerkarten. Den Asset-Typ können Sie auf der Seite mit den Eigenschaften jedoch nicht ändern.
Verwenden Sie zum Ändern des MIME-Typs für ein Asset ein benutzerdefiniertes Metadatenschema-Formular oder ändern Sie ein vorhandenes Formular. Weitere Informationen finden Sie unter [Bearbeiten von Metadatenschema-Formularen](#edit-metadata-schema-forms). Wenn Sie das Metadatenschema für einen bestimmten MIME-Typ ändern, werden das Layout der Eigenschaftenseite für Assets mit dem aktuellen MIME-Typ und alle untergeordneten Asset-Typen geändert. For example, modifying a jpeg schema under `default/image` only modifies the metadata layout (asset properties) for assets with MIME type `image/jpeg`. Wenn Sie allerdings das Schema default ändern, wird dadurch das Metadatenlayout für alle Asset-Typen geändert.

1. To view a list of forms/templates, click the AEM logo and then navigate to **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**.
Die folgenden Vorlagen sind standardmäßig in AEM verfügbar:

   * **default**: Dies ist das Basisformular für Assets.
   Die folgenden untergeordneten Formulare übernehmen die Eigenschaften des Standardformulars:
i. **Bild**: Schemaformular für Assets mit dem MIME-Typ &quot;image&quot;, z. B. `image/jpeg`, `image/png`usw.
Das Formular &quot;image&quot;enthält die folgenden Vorlagen für untergeordnete Formulare:a. **jpeg**: Schemaformular für Assets mit Untertyp `jpeg`.
b. **tiff**: Schema form for the assets with sub type `tiff`.

   ii. **Anwendung**: Schemaformular für Assets mit MIME-Typ `application`, z. B. `application/pdf`, `application/zip`usw.
a. **pdf**: Schema form for assets with sub type `pdf`.

   iii. **video**: Schemaformular für Assets mit MIME-Typ `video`, z. B. `video/avi`, `video/mp4`usw.

   * **Sammlung**: Schemaformular für Sammlungen.
   * **** contentfragment: Schemaformular für Inhaltsfragmente.


>[!NOTE]
>
>Um die untergeordneten Formulare eines Schemaformulars anzuzeigen, klicken/tippen Sie auf den Namen des Schemaformulars.

## Hinzufügen von Metadatenschema-Formularen {#add-a-metadata-schema-form}

1. To add a custom template to the list, click **[!UICONTROL Create]** from the toolbar.

   >[!NOTE]
   >
   >Nicht bearbeitete Vorlagen haben ein Sperrsymbol vor ihnen. Wenn Sie eine der Vorlagen anpassen, wird das Sperrsymbol angezeigt, bevor die Vorlage ausgeblendet wird.

1. In the dialog, enter the title of the Schema form, and then click **[!UICONTROL Create]** to complete the form creation process.

## Bearbeiten von Metadatenschema-Formularen {#edit-metadata-schema-forms}

Sie können ein neu hinzugefügtes oder vorhandenes Metadatenschema-Formular bearbeiten. Das Metadatenschemaformular enthält die folgenden Elemente:

* Registerkarten
* Formularelemente innerhalb von Registerkarten

Sie können diese Formularelemente einem Feld innerhalb eines Metdatenknotens im CRX-Repository zuordnen bzw. dafür konfigurieren.

Sie können dem Metadatenschema-Formular neue Registerkarten oder Formularelemente hinzufügen. Die Registerkarten und Formularelemente, die von der übergeordneten Komponente abgeleitet wurden, befinden sich im gesperrten Status. Sie können auf untergeordneter Ebene nicht geändert werden.

1. In the Schema Forms page, select the check box before a form and then click the **Edit icon** on the toolbar.
1. In the **[!UICONTROL Metadata Schema Editor]** page, customize the properties page of the asset by dragging one or more components from the list of component types in the **[!UICONTROL Build Form]** tab to the **[!UICONTROL Basic]** tab.
1. Um eine Komponente zu konfigurieren, wählen Sie diese aus und ändern Sie ihre Eigenschaften auf der Registerkarte **Einstellungen**.

### Komponenten auf der Registerkarte „Formular erstellen“{#components-within-the-build-form-tab}

The **[!UICONTROL Build Form]** tab lists form items that you use in your schema form. Die Registerkarte **[!UICONTROL Einstellungen]** enthält die Attribute für jedes Element, das Sie auf der Registerkarte **[!UICONTROL Formular erstellen]** auswählen. Die folgende Tabelle enthält die auf der Registerkarte **[!UICONTROL Formular erstellen]** verfügbaren Formularelemente:

<table>
 <tbody>
  <tr>
   <td><strong>Komponentenname</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Bereichs-Kopfzeile</td>
   <td>Fügen Sie eine Abschnittsüberschrift für eine Liste allgemeiner Komponenten hinzu.</td>
  </tr>
  <tr>
   <td>Einzelzeilentext</td>
   <td>Fügen Sie eine einzeilige Texteigenschaft hinzu. Diese wird als Zeichenfolge gespeichert.</td>
  </tr>
  <tr>
   <td>Mehrwerttext</td>
   <td>Fügen Sie eine Texteigenschaft mit mehreren Werten hinzu. Diese wird als Zeichenfolgen-Array gespeichert.</td>
  </tr>
  <tr>
   <td>Nummer</td>
   <td>Fügen Sie eine Zahlenkomponente hinzu.</td>
  </tr>
  <tr>
   <td>Datum</td>
   <td>Fügen Sie eine Datumskomponente hinzu.</td>
  </tr>
  <tr>
   <td>Dropdown</td>
   <td>Fügen Sie eine Dropdown-Liste hinzu.</td>
  </tr>
  <tr>
   <td>Standard-Tags</td>
   <td>Fügen Sie ein Tag hinzu. </td>
  </tr>
  <tr>
   <td>Smart-Tags</td>
   <td>Fügen Sie automatisch Metadaten-Tags hinzu, um Suchfunktionen zu ergänzen.<br /> </td>
  </tr>
  <tr>
   <td>Ausgeblendetes Feld</td>
   <td>Fügen Sie ein ausgeblendetes Feld hinzu. Dieses wird beim Speichern des Assets als POST-Parameter gesendet.</td>
  </tr>
  <tr>
   <td>Asset referenziert von</td>
   <td>Fügen Sie diese Komponente hinzu, um eine Liste der vom Asset referenzierten Assets anzuzeigen.</td>
  </tr>
  <tr>
   <td>Asset-Verweise</td>
   <td>Fügen Sie dies hinzu, um eine Liste der Assets anzuzeigen, die das Asset referenzieren.</td>
  </tr>
  <tr>
   <td>Produktverweise</td>
   <td>Fügen Sie dies hinzu, um die Liste der mit dem Asset verknüpften Produkte anzuzeigen.</td>
  </tr>
  <tr>
   <td>Asset-Bewertung</td>
   <td>Fügen Sie dies hinzu, um Optionen zur Bewertung des Assets anzuzeigen.</td>
  </tr>
  <tr>
   <td>Kontextuelle Metadaten</td>
   <td>Fügen Sie diese Komponente hinzu, um weitere Metadaten auf der Seite „Eigenschaften“ von Assets anzuzeigen.</td>
  </tr>
 </tbody>
</table>

#### Bearbeiten von Metadatenkomponenten {#edit-the-metadata-component}

Um die Eigenschaften einer Metadatenkomponente im Formular zu bearbeiten, klicken Sie auf die Komponente und bearbeiten Sie alle Eigenschaften oder einen Teil der folgenden Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**.

**Feldbeschriftung**: Der Name der Metadateneigenschaft, die auf der Eigenschaftenseite für das Asset angezeigt wird.

**Zu Eigenschaft zuordnen**: Diese Eigenschaft gibt den relativen Pfad/Namen zum Asset-Knoten an, unter dem die Eigenschaft im CRX-Repository gespeichert ist. It starts with `./` because indicating that the path is under the asset&#39;s node.

Im Folgenden finden Sie die gültigen Werte für diese Eigenschaft:

* . `/jcr:content/metadata/dc:title`: Speichert den Wert im Metadatenknoten des Assets als die Eigenschaft `dc:title`.

* . `/jcr:created`: Zeigt die Eigenschaft „jcr“ im Knoten des Assets an. Wenn Sie diese Eigenschaften für Ansichtseigenschaften konfigurieren, wird empfohlen, dass Sie sie mit „Bearbeitung deaktivieren“ markieren, da sie geschützt sind. Andernfalls tritt der Fehler „Assets konnten nicht geändert werden“ auf, wenn Sie die Eigenschaften des Assets speichern.

Um sicherzustellen, dass die Komponente im Metadaten-Schemaformular korrekt angezeigt wird, sollte der Eigenschaftenpfad keine Leerzeichen enthalten.

**Platzhalter**: Geben Sie mit dieser Eigenschaft relevanten Platzhaltertext zur Metadateneigenschaft an.

**Erforderlich**: Mit dieser Eigenschaft können Sie eine Metadateneigenschaft auf der Eigenschaftenseite als obligatorisch markieren.

**Bearbeiten** deaktivieren: Verwenden Sie diese Eigenschaft, um eine Metadateneigenschaft auf der Seite &quot;Eigenschaften&quot;nicht zu bearbeiten.

**Leeres Feld schreibgeschützt anzeigen**: Markieren Sie diese Eigenschaft, um eine Metadateneigenschaft auch dann auf der Eigenschaftenseite anzuzeigen, wenn sie keinen Wert aufweist. Standardmäßig werden Metadateneigenschaften ohne Werte nicht auf der Eigenschaftenseite aufgeführt.

**Reihenfolge** der Liste anzeigen: Verwenden Sie diese Eigenschaft, um eine geordnete Liste der Auswahlmöglichkeiten anzuzeigen

**Wahlen**: Mit dieser Eigenschaft legen Sie Optionen in einer Liste fest.

**Beschreibung**: Mit dieser Eigenschaft können Sie eine kurze Beschreibung für die Metadatenkomponente hinzufügen.

**Klasse**: Objektklasse, der die Eigenschaft zugeordnet ist.

**Löschen**: Klicken Sie auf , um eine Komponente aus dem Schemaformular zu löschen.

>[!NOTE]
>
>Die Komponente „Verborgenes Feld“ enthält diese Attribute nicht. Sie enthält stattdessen Eigenschaften wie die Attribute „Name“, „Wert“, „Feldbezeichnung“ und „Beschreibung“. Die Werte für die Komponente „Ausgeblendetes Feld“ werden beim Speichern des Assets als POST-Parameter gesendet. Sie werden nicht als Metadaten für das Asset gespeichert.

Wenn Sie die Option **[!UICONTROL Erforderlich]** auswählen, können Sie nach Assets suchen, denen obligatorische Metadaten fehlen. Erweitern Sie im Bereich **[!UICONTROL Filter]** die Eigenschaft **[!UICONTROL Metadaten-Überprüfung]** und wählen Sie die Option **[!UICONTROL Ungültig]**. In den Suchergebnissen werden die Assets angezeigt, denen obligatorische Metadaten fehlen, die Sie im Schemaformular konfiguriert haben.

Wenn Sie die Komponente „Kontextuelle Metadaten“ in eine beliebige Registerkarte eines Schemaformulars einfügen, wird sie in der Eigenschaftenseite der Assets als Liste angezeigt, auf die das bestimmte  Schema angewendet wird. Die Liste enthält alle weiteren Registerkarten mit Ausnahme der Registerkarte, auf die Sie die Komponente &quot;Kontextuelle Metadaten&quot;angewendet haben. Derzeit bietet diese Funktion grundlegende Funktionalität zur Steuerung der Anzeige von Metadaten, die auf dem Kontext basieren.

Wenn Sie auf der Eigenschaftenseite zusätzlich zur Registerkarte, auf die die Komponente „Kontextuelle Metadaten“ angewendet wird, eine weitere Registerkarte aufnehmen möchten, wählen Sie die Registerkarte aus der Liste aus. Die Registerkarte wird der Eigenschaftenseite hinzugefügt.

### Specify properties in JSON file {#specify-properties-in-json-file}

Anstatt die Eigenschaften für die Optionen auf der Registerkarte **[!UICONTROL Einstellungen]** anzugeben, können Sie die Optionen in einer JSON-Datei definieren, indem Sie die entsprechenden Schlüssel/Wert-Paare angeben. Specify the path of the JSON file in the **[!UICONTROL JSON Path]** field.

#### Add and delete a tab in the schema form {#add-delete-a-tab-in-the-schema-form}

Mit dem Schema-Editor können Sie Registerkarten hinzufügen oder löschen. The default schema form includes the **[!UICONTROL Basic]**, **[!UICONTROL Advanced]** , **[!UICONTROL IPTC]**, and **[!UICONTROL IPTC Extension]** tabs, by default.

Click `+` to add a new tab on a schema form. By default, the new tab has the name `Unnamed-1`. You can modify the name from the **[!UICONTROL Settings]** tab. Click `X` to delete a tab.

## Löschen von Metadatenschema-Formularen {#deleting-metadata-schema-forms}

In AEM können Sie nur benutzerdefinierte Schemaformulare löschen. Die Standardschemaformulare/-vorlagen können nicht gelöscht werden. Sie können aber alle benutzerdefinierten Änderungen in diesen Formularen löschen.

Um ein Formular zu löschen, wählen Sie ein Formular aus und klicken Sie auf das Symbol zum Löschen.

>[!NOTE]
>
>Nachdem Sie benutzerdefinierte Änderungen an einem Standardformular gelöscht haben, wird auf der Benutzeroberfläche des Metadaten-Schemas das Sperrsymbol erneut angezeigt, um anzuzeigen, dass das Formular wieder den Standardstatus erreicht hat.

>[!NOTE]
>
>Die Standard-Metadatenschemaformulare in AEM Assets können nicht gelöscht werden.

## Schemaformulare für MIME-Typen {#schema-forms-for-mime-types}

AEM Assets stellt voreingestellte Standardformulare für verschiedene MIME-Typen bereit. Sie können jedoch benutzerdefinierte Formulare für verschiedene MIME-Typen hinzufügen.

### Hinzufügen neuer Formulare für MIME-Typen {#adding-new-forms-for-mime-types}

Erstellen Sie ein neues Formular unter dem entsprechenden Formulartyp. Beispiel: Um eine neue Vorlage für den Untertyp **image/png** hinzuzufügen, erstellen Sie das Formular unter den „image“-Formularen. Der Titel für das Schemaformular ist der Name des Untertyps. In diesem Fall ist der Titel „png“**.**

#### Verwenden einer vorhandenen Schemavorlage für verschiedene MIME-Typen {#using-an-existing-schema-template-for-various-mime-types}

Sie können eine vorhandene Vorlage für einen anderen MIME-Typ verwenden. For example, use the `image/jpeg` form for assets of MIME type `image/png`.

Erstellen Sie in diesem Fall einen neuen Knoten unter `/etc/dam/metadataeditor/mimetypemappings` im CRX-Repository. Geben Sie einen Namen für den Knoten an und definieren Sie die folgenden Eigenschaften:

| **Name** | **Beschreibung** | **Typ** | **Wert** |
|---|---|---|---|
| `exposedmimetype` | Name des vorhandenen Formulars, das zugeordnet werden soll | Zeichenfolge | `image/jpeg` |
| `mimetypes` | Liste der MIME-Typen, die das im Attribut `exposedmimetype` definierte Formular verwenden | Zeichenfolge | `image/png` |

AEM Assets ordnet die folgenden MIME-Typen und Schemaformulare zu:

| Schemaformular | MIME-Typen |
|---|---|
| image/jpeg | image/pjpeg |
| image/tiff | image/x-tiff |
| application/pdf | application/postscript |
| application/x-ImageSet | Multipart/Related; type=application/x-ImageSet |
| application/x-SpinSet | Multipart/Related; type=application/x-SpinSet |
| application/x-MixedMediaSet | Multipart/Related; type=application/x-MixedMediaSet |
| video/quicktime | video/x-quicktime |
| video/mpeg4 | video/mp4 |
| video/avi | video/avi, video/msvideo, video/x-msvideo |
| video/wmv | video/x-ms-wmv |
| video/flv | video/x-flv |

## Erteilen des Zugriffs auf Metadatenschemata {#granting-access-to-metadata-schemas}

Die Funktion „Metadatenschema“ ist nur für Administratoren verfügbar. Administratoren können anderen Benutzern allerdings Zugriff erteilen, indem sie einige Berechtigungen ändern. The non administrator should have create, modify, and delete permissions on the `/conf` folder.

## Anwenden von ordnerspezifischen Metadaten {#applying-folder-specific-metadata}

Mit AEM Assets können Sie Varianten eines Metadatenschemas definieren und auf einen bestimmten Ordner anwenden.

Zum Beispiel können Sie eine Variante des Standard-Metadatenschemas definieren und diese auf einen Ordner anwenden. Das ursprüngliche Standard-Metadatenschema wird dabei überschrieben.

Die Änderungen aus der Variante betreffen nur die Assets in dem Ordner, auf den das Schema angewendet wird.

Assets in anderen Ordnern, für die das ursprüngliche Schema gilt, entsprechen weiterhin den im ursprünglichen Schema definierten Metadaten.

Die Metadatenübernahme durch Assets richtet sich nach dem Schema, das auf den Ordner der ersten Ebene in der Hierarchie angewendet wird. Assets in Ordnern, die keine Unterordner enthalten, übernehmen die Metadaten aus dem Schema, das auf ihren Ordner angewendet wird.

Assets in Unterordnern übernehmen die Metadaten aus dem Schema, das auf den Unterordner angewendet wurde, wenn es sich um ein anderes Schema handelt als das des übergeordneten Ordners. Assets in Unterordnern, auf die kein Schema oder dasselbe Schema wie auf den übergeordneten Ordner angewendet wurde, übernehmen die Metadaten des Schemas für den übergeordneten Ordner.

1. Click the AEM logo and then navigate to **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**. The **[!UICONTROL Metadata Schema Forms]** page is displayed.
1. Aktivieren Sie das Kontrollkästchen vor einem Formular, z. B. dem Standard-Metadatenformular, und klicken Sie auf das Symbol &quot;Kopieren&quot;oder tippen Sie darauf und speichern Sie es als benutzerdefiniertes Formular. Specify a custom name for the form, for example `my_default`. Alternativ können Sie ein benutzerdefiniertes Formular erstellen.

1. In the **[!UICONTROL Metadata Schema Forms]** page, select the `my_default` form, and then click the **[!UICONTROL Edit]** icon.
1. In the **[!UICONTROL Metadata Schema Editor]** page, add a text field to the schema form. For example add a field with the label **[!UICONTROL Category]**.
1. Klicken Sie auf **[!UICONTROL Speichern]**. Das geänderte Formular wird auf der Seite **[!UICONTROL Metadatenschema-Formulare]** aufgeführt.
1. Klicken/tippen Sie in der Symbolleiste auf **[!UICONTROL Auf Ordner anwenden]**, um die benutzerdefinierten Metadaten auf einen Ordner anzuwenden.
1. Select the folder on which to apply the modified schema and then click/tap **[!UICONTROL Apply]**.
1. Wurde das andere Metadatenschema auf den Ordner angewendet, erhalten Sie eine Meldung mit der Warnung, dass Sie im Begriff sind, das vorhandene Metadatenschema zu überschreiben. Click **Overwrite**.
1. Click **OK** to close the success message.
1. Navigieren Sie zu dem Ordner, auf den Sie das geänderte Metadatenschema angewendet haben.

## Definieren erforderlicher Metadaten {#defining-mandatory-metadata}

Sie können Pflichtfelder auf Ordnerebene definieren, die für in den Ordner hochgeladene Assets erzwungen werden. Wenn Sie Assets mit fehlenden Metadaten für die zuvor definierten Pflichtfelder hochladen, wird in der Kartenansicht ein entsprechender visueller Hinweis für die Assets angezeigt.

>[!NOTE]
>
>Ein Metadatenfeld kann je nach dem Wert eines weiteren Felds als Pflichtfeld definiert werden. In der Kartenansicht zeigt AEM keine Warnung zu fehlenden Metadaten für solche obligatorischen Metadatenfelder an.

1. Click the AEM logo and then navigate to **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**. The **[!UICONTROL Metadata Schema Forms]** page is displayed.
1. Speichern Sie die Standard-Metadatenformulare als benutzerdefiniertes Formular. Speichern Sie es beispielsweise unter `my_default`.
1. Bearbeiten Sie das benutzerdefinierte Formular. Fügen Sie ein erforderliches Feld hinzu. For example, add a **[!UICONTROL Category]** field and make the field mandatory.
1. Klicken Sie auf **[!UICONTROL Speichern]**. Das geänderte Formular wird auf der Seite **[!UICONTROL Metadatenschema-Formulare]** aufgeführt. Wählen Sie das Formular aus und klicken oder tippen Sie dann in der Symbolleiste auf **[!UICONTROL Auf Ordner anwenden]**, um die benutzerdefinierten Metadaten auf einen Ordner anzuwenden.
1. Navigieren Sie zum Ordner und laden Sie einige Assets mit fehlenden Metadaten für das Pflichtfeld, das Sie dem benutzerdefinierten Formular hinzugefügt haben. Eine Meldung für die fehlenden Metadaten für das Pflichtfeld wird auf der Kartenansicht des Assets angezeigt.
1. (Optional) Zugriff `https://[server]:[port]/system/console/components/`. Configure and enable `com.day.cq.dam.core.impl.MissingMetadataNotificationJob` component that is disabled by default. Legen Sie fest, mit welcher Häufigkeit AEM die Gültigkeit der Metadaten in den Assets überprüft.

   This configuration adds a property `hasValidMetadata` to `jcr:content` of assets. Mit dieser Eigenschaft kann AEM die Ergebnisse in einer Suche filtern.

   >[!NOTE]
   >
   >If an asset is added after the scheduled check, the asset is not flagged with `hasValidMetadata` until the next scheduled check. Die Assets werden nicht in den Zwischensuchergebnissen angezeigt.

   >[!CAUTION]
   >
   >Die Metadaten-Überprüfungen sind ressourcenintensiv und können die Leistung Ihres Systems beeinträchtigen. Planen Sie die Überprüfungen entsprechend. Wenn der Server die Last nicht bewältigen kann, versuchen Sie, diesen Auftrag zu deaktivieren
