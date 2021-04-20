---
title: Metadatenschemata
description: Das Metadatenschema definiert das Layout der Eigenschaftsseite und die für Assets angezeigten Metadaten-Eigenschaften. Erfahren Sie, wie Sie benutzerdefinierte Metadatenschemen erstellen und Metadatenschemen bearbeiten und auf Assets anwenden können.
contentOwner: AG
feature: Metadata
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 8093f6cec446223af58515fd8c91afa5940f9402
workflow-type: tm+mt
source-wordcount: '2513'
ht-degree: 100%

---


# Metadatenschemata   {#metadata-schemas}

Ein Metadatenschema in Adobe Experience Manager (AEM) Assets definiert das Layout der Eigenschaftenseite und die für Assets angezeigten Metadateneigenschaften, die das betreffende Schema verwenden. Zu den Metadateneigenschaften zählen u. a. Titel, Beschreibung, MIME-Typen, Tags usw.

Mit dem Editor für Metadaten-Schemaformulare können Sie vorhandene Schemata ändern oder benutzerdefinierte Metadatenschemata hinzufügen.

1. Um die Eigenschaftenseite für ein Asset anzuzeigen, klicken oder tippen Sie in den Schnellaktionen der Kachel „Assets“ in der Kartenansicht auf das Symbol **[!UICONTROL Eigenschaften anzeigen]**. Wählen Sie alternativ das Asset in der Benutzeroberfläche aus und klicken oder tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Eigenschaften]**.
1. Bearbeiten Sie dann unterschiedliche Eigenschaften in den verschiedenen Registerkarten. Den Asset-Typ können Sie auf der Seite mit den Eigenschaften jedoch nicht ändern.
Verwenden Sie zum Ändern des MIME-Typs für ein Asset ein benutzerdefiniertes Metadatenschema-Formular oder ändern Sie ein vorhandenes Formular. Weitere Informationen finden Sie unter [Bearbeiten von Metadatenschema-Formularen](#edit-metadata-schema-forms). Wenn Sie das Metadatenschema für einen bestimmten MIME-Typ ändern, werden das Layout der Eigenschaftenseite für Assets mit dem aktuellen MIME-Typ und alle untergeordneten Asset-Typen geändert. Durch die Bearbeitung des jpeg-Schemas unter `default/image` wird nur das Metadaten-Layout (Asset-Eigenschaften) für Assets mit dem MIME-Typ `image/jpeg` bearbeitet. Wenn Sie allerdings das „default“-Schema ändern, wird dadurch das Metadaten-Layout für alle Asset-Typen geändert.

1. Um eine Liste von Formularen/Vorlagen anzuzeigen, klicken Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemata]**.
Die folgenden Vorlagen sind standardmäßig in AEM verfügbar:

   * **default**: Dies ist das Basisformular für Assets.

   Folgende untergeordnete Formulare übernehmen die Eigenschaften des Standardformulars:
i. **image**: Schemaformular für Assets mit dem MIME-Typ „image“, z. B. `image/jpeg`, `image/png` usw.
Das Formular „image“ enthält die folgenden Vorlagen für untergeordnete Formulare:
a. **jpeg**: Schemaformular für Assets mit Untertyp `jpeg`.
b. ****: Schemaformular für Assets mit dem Untertyp `tiff`.

   ii. **application**: Schemaformular für Assets mit dem MIME-Typ `application` (wie `application/pdf`, `application/zip` usw.).
a. **pdf**: Schemaformular für Assets mit dem Untertyp `pdf`.

   iii. **video**: Schemaformular für Assets mit dem MIME-Typ `video` (wie `video/avi`, `video/mp4` usw.).

   * **collection**: Schemaformular für Sammlungen.
   * **contentfragment**: Schemaformular für Inhaltsfragmente.


>[!NOTE]
>
>Um die untergeordneten Formulare eines Schemaformulars anzuzeigen, klicken/tippen Sie auf den Namen des Schemaformulars.

## Hinzufügen von Metadatenschema-Formularen {#add-a-metadata-schema-form}

1. Um eine benutzerdefinierte Vorlage zur Liste hinzuzufügen, klicken Sie in der Symbolleiste auf **[!UICONTROL Erstellen]**.

   >[!NOTE]
   >
   >Nicht bearbeitete Vorlagen sind mit einem Sperrsymbol gekennzeichnet. Wenn Sie eine Vorlage anpassen, wird das Sperrsymbol vor der Vorlage ausgeblendet.

1. Geben Sie den Titel des Schemaformulars ein und klicken Sie auf **[!UICONTROL Erstellen]**, um den Prozess zur Formularerstellung abzuschließen.

## Bearbeiten von Metadatenschema-Formularen {#edit-metadata-schema-forms}

Sie können ein neu hinzugefügtes oder vorhandenes Metadatenschema-Formular bearbeiten. Das Metadatenschemaformular enthält die folgenden Elemente:

* Registerkarten
* Formularelemente innerhalb von Registerkarten

Sie können diese Formularelemente einem Feld innerhalb eines Metdatenknotens im CRX-Repository zuordnen bzw. dafür konfigurieren.

Sie können dem Metadatenschema-Formular neue Registerkarten oder Formularelemente hinzufügen. Die vom übergeordneten Objekt abgeleiteten Registerkarten und Formularelemente sind gesperrt. Sie können auf untergeordneter Ebene nicht geändert werden.

1. Aktivieren Sie auf der Seite „Schemaformular“ das Kontrollkästchen vor einem Formular und klicken Sie in der Symbolleiste auf das Symbol **Bearbeiten**.
1. Passen Sie auf der Seite **[!UICONTROL Metadatenschema-Formular]** die Eigenschaftenseite des Assets an, indem Sie Komponenten aus der Komponentenliste auf der Registerkarte **[!UICONTROL Formular erstellen]** in die Registerkarte **[!UICONTROL Basis]** ziehen.
1. Um eine Komponente zu konfigurieren, wählen Sie diese aus und ändern Sie ihre Eigenschaften auf der Registerkarte **Einstellungen**.

### Komponenten auf der Registerkarte „Formular erstellen“{#components-within-the-build-form-tab}

Die Registerkarte **[!UICONTROL Formular erstellen]** enthält Formularelemente, die Sie im Schemaformular verwenden. Die Registerkarte **[!UICONTROL Einstellungen]** enthält die Attribute für jedes Element, das Sie auf der Registerkarte **[!UICONTROL Formular erstellen]** auswählen. Die folgende Tabelle enthält die auf der Registerkarte **[!UICONTROL Formular erstellen]** verfügbaren Formularelemente:

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
   <td>Zahl</td>
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

**Feldbezeichnung**: Der Name der Metadateneigenschaft, der auf der Eigenschaftenseite des Assets angezeigt wird.

**Zu Eigenschaft zuordnen**: Diese Eigenschaft gibt den relativen Pfad/Namen zum Asset-Knoten an, unter dem die Eigenschaft im CRX-Repository gespeichert ist. Sie beginnt mit `./`, um anzugeben, dass der Pfad sich unter dem Knoten des Assets befindet.

Im Folgenden finden Sie die gültigen Werte für diese Eigenschaft:

* . `/jcr:content/metadata/dc:title`: Speichert den Wert im Metadatenknoten des Assets als die Eigenschaft `dc:title`.

* . `/jcr:created`: Zeigt die Eigenschaft „jcr“ im Knoten des Assets an. Wenn Sie diese Eigenschaften für Ansichtseigenschaften konfigurieren, wird empfohlen, dass Sie sie mit „Bearbeitung deaktivieren“ markieren, da sie geschützt sind. Andernfalls tritt der Fehler „Assets konnten nicht geändert werden“ auf, wenn Sie die Eigenschaften des Assets speichern.

Um sicherzustellen, dass die Komponente im Metadaten-Schemaformular korrekt angezeigt wird, sollte der Eigenschaftenpfad keine Leerzeichen enthalten.

**Platzhalter**: Geben Sie mit dieser Eigenschaft relevanten Platzhaltertext zur Metadateneigenschaft an.

**Erforderlich**: Mit dieser Eigenschaft können Sie eine Metadateneigenschaft auf der Eigenschaftenseite als obligatorisch markieren.

**Bearbeitung deaktivieren**: Mit dieser Eigenschaft können Sie verhindern, dass eine Metadateneigenschaft auf der Eigenschaftsseite bearbeitet werden kann.

**Leeres Feld schreibgeschützt anzeigen**: Markieren Sie diese Eigenschaft, um eine Metadateneigenschaft auch dann auf der Eigenschaftenseite anzuzeigen, wenn sie keinen Wert aufweist. Standardmäßig werden Metadateneigenschaften ohne Werte nicht auf der Eigenschaftenseite aufgeführt.

**Liste geordnet anzeigen**: Mit dieser Eigenschaft zeigen Sie eine geordnete Liste von Optionen an.

**Wahlen**: Mit dieser Eigenschaft legen Sie Optionen in einer Liste fest.

**Beschreibung**: Mit dieser Eigenschaft können Sie eine kurze Beschreibung für die Metadatenkomponente hinzufügen.

**Klasse**: Objektklasse, der die Eigenschaft zugeordnet ist.

**Löschen**: Klicken Sie darauf, um eine Komponente aus dem Schemaformular zu löschen.

>[!NOTE]
>
>Die Komponente „Verborgenes Feld“ enthält diese Attribute nicht. Sie enthält stattdessen Eigenschaften wie die Attribute „Name“, „Wert“, „Feldbezeichnung“ und „Beschreibung“. Die Werte für die Komponente „Ausgeblendetes Feld“ werden beim Speichern des Assets als POST-Parameter gesendet. Sie werden nicht als Metadaten für das Asset gespeichert.

Wenn Sie die Option **[!UICONTROL Erforderlich]** auswählen, können Sie nach Assets suchen, denen obligatorische Metadaten fehlen. Erweitern Sie im Bedienfeld **[!UICONTROL Filter]** die Eigenschaft **[!UICONTROL Metadatenvalidierung]** und wählen Sie die Option **[!UICONTROL Ungültig]**. Die Suchergebnisse zeigen Assets an, denen erforderliche Metadaten fehlen, die Sie über das Schemaformular konfiguriert haben.

Wenn Sie die Komponente „Kontextuelle Metadaten“ in eine beliebige Registerkarte eines Schemaformulars einfügen, wird sie in der Eigenschaftenseite der Assets als Liste angezeigt, auf die das bestimmte      Schema angewendet wird. Die Liste enthält alle anderen Registerkarten außer der Registerkarte, auf die Sie die Komponente „Kontextuelle Metadaten“ angewendet haben. Derzeit bietet diese Funktion grundlegende Funktionalität zur Steuerung der Anzeige von Metadaten, die auf dem Kontext basieren.

Wenn Sie auf der Eigenschaftenseite zusätzlich zur Registerkarte, auf die die Komponente „Kontextuelle Metadaten“ angewendet wird, eine weitere Registerkarte aufnehmen möchten, wählen Sie die Registerkarte aus der Liste aus. Die Registerkarte wird der Eigenschaftenseite hinzugefügt.

### Festlegen von Eigenschaften in einer JSON-Datei {#specify-properties-in-json-file}

Anstatt die Eigenschaften für die Optionen auf der Registerkarte **[!UICONTROL Einstellungen]** anzugeben, können Sie die Optionen in einer JSON-Datei definieren, indem Sie die entsprechenden Schlüssel/Wert-Paare angeben. Geben Sie den Pfad der JSON-Datei im Feld **[!UICONTROL JSON-Pfad]** an.

#### Hinzufügen und Löschen von Registerkarten im Schemaformular {#add-delete-a-tab-in-the-schema-form}

Mit dem Schema-Editor können Sie Registerkarten hinzufügen oder löschen. Das Standard-Schemaformular umfasst standardmäßig die Registerkarten **[!UICONTROL Standard]**, **[!UICONTROL Erweitert]**, **[!UICONTROL IPTC]** und **[!UICONTROL IPTC-Erweiterung]**.

Klicken Sie auf `+`, um einem Schemaformular eine neue Registerkarte hinzuzufügen. Standardmäßig hat die neue Registerkarte den Namen `Unnamed-1`. Sie können den Namen auf der Registerkarte **[!UICONTROL Einstellungen]** ändern. Klicken Sie auf `X`, um eine Registerkarte zu löschen.

## Löschen von Metadatenschema-Formularen {#deleting-metadata-schema-forms}

In AEM können Sie nur benutzerdefinierte Schemaformulare löschen. Die Standardschemaformulare/-vorlagen können nicht gelöscht werden. Sie können aber alle benutzerdefinierten Änderungen in diesen Formularen löschen.

Um ein Formular zu löschen, wählen Sie das Formular aus und klicken Sie auf das Symbol zum Löschen.

>[!NOTE]
>
>Wenn Sie benutzerspezifische Änderungen an einem Standardformular löschen, wird das Sperrsymbol wieder vor dem Formular auf der Metadatenschema-Benutzeroberfläche angezeigt, um zu kennzeichnen, dass das Formular wieder in den Standardzustand versetzt wurde.

>[!NOTE]
>
>Die Standard-Metadatenschemaformulare in AEM Assets können nicht gelöscht werden.

## Schemaformulare für MIME-Typen    {#schema-forms-for-mime-types}

AEM Assets stellt voreingestellte Standardformulare für verschiedene MIME-Typen bereit. Sie können jedoch benutzerdefinierte Formulare für verschiedene MIME-Typen hinzufügen.

### Hinzufügen neuer Formulare für MIME-Typen {#adding-new-forms-for-mime-types}

Erstellen Sie ein neues Formular unter dem entsprechenden Formulartyp. Beispiel: Um eine neue Vorlage für den Untertyp **image/png** hinzuzufügen, erstellen Sie das Formular unter den „image“-Formularen. Der Titel für das Schemaformular ist der Name des Untertyps. In diesem Fall lautet der Titel „png.**“**.

#### Verwenden einer vorhandenen Schemavorlage für verschiedene MIME-Typen {#using-an-existing-schema-template-for-various-mime-types}

Sie können eine vorhandene Vorlage für einen anderen MIME-Typ verwenden. Nutzen Sie beispielsweise das Formular `image/jpeg` für Assets mit dem MIME-Typ `image/png`.

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

Die Funktion „Metadatenschema“ ist nur für Administratoren verfügbar. Administratoren können anderen Benutzern allerdings Zugriff erteilen, indem sie einige Berechtigungen ändern. Nicht-Administratoren benötigen für den Ordner `/conf` Berechtigungen zum Erstellen, Ändern und Löschen.

## Anwenden von ordnerspezifischen Metadaten {#applying-folder-specific-metadata}

Mit AEM Assets können Sie Varianten eines Metadatenschemas definieren und auf einen bestimmten Ordner anwenden.

Zum Beispiel können Sie eine Variante des Standard-Metadatenschemas definieren und diese auf einen Ordner anwenden. Das ursprüngliche Standard-Metadatenschema wird dabei überschrieben.

Die Änderungen aus der Variante betreffen nur die Assets in dem Ordner, auf den das Schema angewendet wird.

Assets in anderen Ordnern, für die das ursprüngliche Schema gilt, entsprechen weiterhin den im ursprünglichen Schema definierten Metadaten.

Die Metadatenübernahme durch Assets richtet sich nach dem Schema, das auf den Ordner der ersten Ebene in der Hierarchie angewendet wird. Assets in Ordnern, die keine Unterordner enthalten, übernehmen die Metadaten aus dem Schema, das auf ihren Ordner angewendet wird.

Assets in Unterordnern übernehmen die Metadaten aus dem Schema, das auf den Unterordner angewendet wurde, wenn es sich um ein anderes Schema handelt als das des übergeordneten Ordners. Assets in Unterordnern, auf die kein Schema oder dasselbe Schema wie auf den übergeordneten Ordner angewendet wurde, übernehmen die Metadaten des Schemas für den übergeordneten Ordner.

1. Klicken Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemata]**. Die Seite **[!UICONTROL Metadatenschema-Formulare]** wird angezeigt.
1. Aktivieren Sie das Kontrollkästchen vor einem Formular, z. B. dem Standard-Metadatenformular, klicken oder tippen Sie auf das Symbol zum Kopieren und speichern Sie es als benutzerdefiniertes Formular. Geben Sie einen benutzerdefinierten Namen für das Formular an, beispielsweise `my_default`. Alternativ können Sie ein benutzerdefiniertes Formular erstellen.

1. Wählen Sie auf der Seite **[!UICONTROL Metadatenschema-Formulare]** das Formular `my_default` und klicken Sie dann auf das Symbol **[!UICONTROL Bearbeiten]**.
1. Fügen Sie auf der Seite **[!UICONTROL Metadatenschema-Editor]** ein Textfeld in das Schemaformular ein. Fügen Sie beispielsweise ein Feld mit der Bezeichnung **[!UICONTROL Kategorie]** hinzu.
1. Klicken Sie auf **[!UICONTROL Speichern]**. Das geänderte Formular wird auf der Seite **[!UICONTROL Metadatenschema-Formulare]** aufgeführt.
1. Klicken/tippen Sie in der Symbolleiste auf **[!UICONTROL Auf Ordner anwenden]**, um die benutzerdefinierten Metadaten auf einen Ordner anzuwenden.
1. Wählen Sie den Ordner aus, auf den Sie das bearbeitete Schema anwenden möchten, und klicken/tippen Sie auf **[!UICONTROL Anwenden]**.
1. Wurde das andere Metadatenschema auf den Ordner angewendet, erhalten Sie eine Meldung mit der Warnung, dass Sie im Begriff sind, das vorhandene Metadatenschema zu überschreiben. Klicken Sie auf **Überschreiben**.
1. Klicken Sie auf **OK**, um die Erfolgsmeldung zu schließen.
1. Navigieren Sie zu dem Ordner, auf den Sie das geänderte Metadatenschema angewendet haben.

## Definieren erforderlicher Metadaten    {#defining-mandatory-metadata}

Sie können Pflichtfelder auf Ordnerebene definieren, die für in den Ordner hochgeladene Assets erzwungen werden. Wenn Sie Assets mit fehlenden Metadaten für die zuvor definierten Pflichtfelder hochladen, wird in der Kartenansicht ein entsprechender visueller Hinweis für die Assets angezeigt.

>[!NOTE]
>
>Ein Metadatenfeld kann je nach dem Wert eines weiteren Felds als Pflichtfeld definiert werden. In der Kartenansicht zeigt AEM keine Warnung zu fehlenden Metadaten für solche obligatorischen Metadatenfelder an.

1. Klicken Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemata]**. Die Seite **[!UICONTROL Metadatenschema-Formulare]** wird angezeigt.
1. Speichern Sie die Standard-Metadatenformulare als benutzerdefiniertes Formular. Speichern Sie sie beispielsweise unter dem Namen `my_default`.
1. Bearbeiten Sie das benutzerdefinierte Formular. Fügen Sie ein erforderliches Feld hinzu. Fügen Sie beispielsweise ein Feld mit der Bezeichnung **[!UICONTROL Kategorie]** hinzu und definieren Sie es als Pflichtfeld.
1. Klicken Sie auf **[!UICONTROL Speichern]**. Das geänderte Formular wird auf der Seite **[!UICONTROL Metadatenschema-Formulare]** aufgeführt. Wählen Sie das Formular aus und klicken oder tippen Sie dann in der Symbolleiste auf **[!UICONTROL Auf Ordner anwenden]**, um die benutzerdefinierten Metadaten auf einen Ordner anzuwenden.
1. Navigieren Sie zum Ordner und laden Sie einige Assets mit fehlenden Metadaten für das Pflichtfeld, das Sie dem benutzerdefinierten Formular hinzugefügt haben. Eine Meldung über die fehlenden Metadaten für das Pflichtfeld wird auf der Kartenansicht des Assets angezeigt.
1. (Optional) Rufen Sie `https://[server]:[port]/system/console/components/` auf. Konfigurieren und aktivieren Sie die Komponente `com.day.cq.dam.core.impl.MissingMetadataNotificationJob`, die standardmäßig deaktiviert ist. Legen Sie fest, mit welcher Häufigkeit AEM die Gültigkeit der Metadaten in den Assets überprüfen soll.

   Diese Konfiguration fügt eine Eigenschaft `hasValidMetadata` zu `jcr:content` in Assets hinzu. Mit dieser Eigenschaft kann AEM die Ergebnisse in einer Suche filtern.

   >[!NOTE]
   >
   >Wenn ein Asset nach der geplanten Prüfung hinzugefügt wird, wird das Asset erst bei der nächsten geplanten Prüfung mit `hasValidMetadata` gekennzeichnet. In der Zwischenzeit werden die Assets nicht in Suchergebnissen angezeigt.

   >[!CAUTION]
   >
   >Die Metadaten-Überprüfungen sind ressourcenintensiv und können die Leistung Ihres Systems beeinträchtigen. Planen Sie die Überprüfungen entsprechend. Wenn der Server die Last nicht bewältigen kann, versuchen Sie, diesen Auftrag zu deaktivieren
