---
title: Metadatenschemata definieren das Layout der Seite mit den Metadaten-Eigenschaften
description: Das Metadatenschema definiert das Layout der Eigenschaftsseite und die für Assets angezeigten Metadateneigenschaften. Erfahren Sie, wie Sie ein benutzerdefiniertes Metadatenschema erstellen, ein Metadatenschema bearbeiten und ein Metadatenschema auf Assets anwenden können.
contentOwner: AG
feature: Metadata
role: User, Admin
exl-id: 9e94afeb-1c54-4653-bf52-b0910c0cb6c1
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '2634'
ht-degree: 100%

---

# Metadatenschemata {#metadata-schemas}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/metadata-schemas.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Unternehmen entwickeln ein Metadatenmodell, das die Asset-Erkennung, -Nutzung, -Interoperabilität usw. verbessert. Die richtige Anwendung der Metadaten ist sakrosankt, um metadatengesteuerte Workflows und Prozesse zu verwalten. Um die unternehmensweite Metadatenstrategie und -standards einzuhalten, können Sie Metadatenschemata verwenden, die DAM-Benutzern die Abstimmung erleichtern. [!DNL Adobe Experience Manager] ermöglicht einfache und flexible Methoden zum Erstellen, Verwalten und Anwenden von Metadatenschemata.

In [!DNL Adobe Experience Manager Assets] enthalten Schemata bestimmte Felder für bestimmte einzutragende Informationen. Es enthält auch Layout-Informationen, um Metadatenfelder benutzerfreundlich anzuzeigen. Zu den Metadaten-Eigenschaften zählen u. a. Titel, Beschreibung, MIME-Typen, Tags usw. Mit dem Editor für [!UICONTROL Metadatenschema-Formulare] können Sie vorhandene Schemata ändern oder benutzerdefinierte Metadatenschemata hinzufügen.

Gehen Sie wie folgt vor, um die Eigenschaftenseite für ein Asset anzuzeigen und zu bearbeiten:

1. Klicken Sie in den Schnellaktionen auf der Asset-Kachel in der Kartenansicht auf die Option **[!UICONTROL Eigenschaften anzeigen]**. Wählen Sie alternativ ein Asset aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Eigenschaften]**, ![Eigenschaften anzeigen](assets/do-not-localize/info-circle-icon.png).

1. Sie können die verschiedenen bearbeitbaren Metadaten-Eigenschaften auf den verfügbaren Registerkarten bearbeiten. Den Asset-[!UICONTROL Typ] können Sie jedoch nicht auf der Registerkarte [!UICONTROL Standard] der Eigenschaftsseite ändern.

   ![Registerkarte „Standard“ der Asset-Eigenschaften, auf der der Asset-Typ nicht geändert werden kann](assets/asset-properties-basic-tab.png)

   *Abbildung: Registerkarte „Standard“ in den Asset-[!UICONTROL Eigenschaften].*

   Verwenden Sie zum Ändern des MIME-Typs für ein Asset ein benutzerdefiniertes Metadatenschema-Formular oder ändern Sie ein vorhandenes Formular. Weitere Informationen finden Sie unter [Bearbeiten von Metadatenschema-Formularen](#edit-metadata-schema-forms). Wenn Sie das Metadatenschema eines MIME-Typs ändern, wird das Seiten-Layout der Eigenschaften für die Assets und alle Untertypen geändert. Durch die Bearbeitung des jpeg-Schemas unter `default/image` wird nur das Metadaten-Layout (Asset-Eigenschaften) für Assets mit dem MIME-Typ `image/jpeg` bearbeitet. Wenn Sie allerdings das „default“-Schema ändern, wird dadurch das Metadaten-Layout für alle Asset-Typen geändert.

## Metadatenschema-Formulare {#default-metadata-schema-forms}

Um eine Liste von Formularen oder Vorlagen anzuzeigen, gehen Sie in der [!DNL Experience Manager]-Benutzeroberfläche zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemata]**.

[!DNL Experience Manager] stellt die folgenden Metadatenschema-Formularvorlagen bereit.

| Vorlagen | | Beschreibung |
|---|---|---|
| [!UICONTROL default] | | Dies ist das Basis-Metadatenschema-Formular für Assets. |
| | Die folgenden untergeordneten Formulare übernehmen die Eigenschaften des [!UICONTROL Standard]-Formulars: | |
| | <ul><li>[!UICONTROL Dm_video]</li></ul> | Schemaformular für Dynamic Media-Videos. |
| | <ul><li>[!UICONTROL image]</li></ul> | Schemaformular für Bilder mit dem MIME-Typ wie z. B. `image/jpeg` und `image/png`. <br> Das Formular [!UICONTROL Bild] weist die folgenden untergeordneten Formularvorlagen auf: <ul><li> [!UICONTROL jpeg]: Schemaformular für Assets mit dem Untertyp [!UICONTROL jpeg].</li> <li>[!UICONTROL tiff]: Schemaformular für Assets mit dem Untertyp „tiff“.</li></ul> |
| | <ul><li>[!UICONTROL Anwendung]</li></ul> | Schemaformular für Assets mit dem MIME-Typ wie z. B. `application/pdf` und `application/zip`. <br>[!UICONTROL pdf]: Schemaformular für Assets mit dem Untertyp „pdf“. |
| | <ul><li>[!UICONTROL Video]</li></ul> | Schemaformular für Video-Assets mit dem MIME-Typ wie z. B. `video/avi` und `video/mp4`. |
| [!UICONTROL collection] | | Schemaformular für Sammlungen. |
| [!UICONTROL contentfragment] | | Schemaformular für Inhaltsfragmente. |
| [!UICONTROL forms] | | Dieses Schemaformular bezieht sich auf [!DNL Adobe Experience Manager Forms]. |
| [!UICONTROL ugc_contentfragment] | | Schemaformular für benutzergenerierte Inhaltselemente und Assets, die aus Social Media in Experience Manager integriert wurden. |

>[!NOTE]
>
>Um die untergeordneten Formulare eines Schemaformulars anzuzeigen, klicken Sie auf den Namen des Schemaformulars.

## Hinzufügen von Metadatenschema-Formularen {#add-a-metadata-schema-form}

Gehen Sie wie folgt vor, um ein Metadatenschema-Formular hinzuzufügen:

1. Um eine benutzerdefinierte Vorlage zur Liste hinzuzufügen, klicken Sie in der Symbolleiste auf **[!UICONTROL Erstellen]**.

   >[!NOTE]
   >
   >Bei den nicht bearbeiteten Vorlagen wird ein Sperrsymbol angezeigt. Wenn Sie eine Vorlage anpassen, ist sie nicht gesperrt ![lock closed](assets/do-not-localize/lock_closed_icon.svg).

1. Geben Sie im Dialog den Titel des Schemaformulars ein und klicken Sie auf **[!UICONTROL Erstellen]**, um den Prozess zur Formularerstellung abzuschließen.

## Bearbeiten von Metadatenschema-Formularen {#edit-metadata-schema-forms}

Sie können ein neu hinzugefügtes oder vorhandenes Metadatenschema-Formular bearbeiten. Das Metadatenschema-Formular enthält Registerkarten und Formularelemente auf Registerkarten. Sie können diese Formularelemente einem Feld innerhalb eines Metdatenknotens im CRX-Repository zuordnen bzw. dafür konfigurieren. Sie können dem Metadatenschema-Formular Registerkarten oder Formularelemente hinzufügen. Die vom übergeordneten Objekt abgeleiteten Registerkarten und Formularelemente sind gesperrt. Sie können auf untergeordneter Ebene nicht geändert werden.

1. Wählen Sie auf der Seite [!UICONTROL Metadatenschema-Formulare] ein Formular aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.

1. Passen Sie auf der Seite **[!UICONTROL Metadatenschema-Formular-Editor]** das Metadaten-Formular an. Ziehen Sie die erforderlichen Komponenten von der Registerkarte **[!UICONTROL Formular erstellen]** auf eine der Registerkarten.

   ![Metadatenschema-Editor zum Anpassen der Asset-Eigenschaftsseite](assets/metadata-schema-editor.png)

   *Abbildung: Eine [!UICONTROL Metadatenschema-Formular-Editor]-Seite mit verfügbaren Registerkarten.*

1. Um eine Komponente zu konfigurieren, wählen Sie diese aus und ändern Sie ihre Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**.

### Komponenten auf der Registerkarte [!UICONTROL Formular erstellen] {#components-within-the-build-form-tab}

Die Registerkarte **[!UICONTROL Formular erstellen]** enthält Formularelemente, die Sie im Schemaformular verwenden. Die Registerkarte **[!UICONTROL Einstellungen]** enthält die Attribute für jedes Element, das Sie auf der Registerkarte **[!UICONTROL Formular erstellen]** auswählen. Die folgende Tabelle enthält die auf der Registerkarte **[!UICONTROL Formular erstellen]** verfügbaren Formularelemente:

| Komponentenname | Beschreibung |
| -------------------------------- | ----------------------------------------------------------------------------------- |
| [!UICONTROL Bereichs-Kopfzeile] | Fügen Sie eine Abschnittsüberschrift für eine Liste allgemeiner Komponenten hinzu. |
| [!UICONTROL Einzeilentext] | Fügen Sie eine einzeilige Texteigenschaft hinzu. Diese wird als Zeichenfolge gespeichert. |
| [!UICONTROL Mehrfachwerttext] | Fügen Sie eine Texteigenschaft mit mehreren Werten hinzu. Diese wird als Zeichenfolgen-Array gespeichert. |
| [!UICONTROL Zahl] | Fügen Sie eine Zahlenkomponente hinzu. |
| [!UICONTROL Datum] | Fügen Sie eine Datumskomponente hinzu. |
| [!UICONTROL Dropdown] | Fügen Sie eine Dropdown-Liste hinzu. |
| [!UICONTROL Standard-Tags] | Fügen Sie ein Tag hinzu. |
| [!UICONTROL Smart-Tags] | Fügen Sie automatisch Metadaten-Tags hinzu, um Suchfunktionen zu ergänzen. |
| [!UICONTROL Ausgeblendetes Feld] | Fügen Sie ein ausgeblendetes Feld hinzu. Dieses wird beim Speichern des Assets als POST-Parameter gesendet. |
| [!UICONTROL Asset referenziert von] | Fügen Sie diese Komponente hinzu, um eine Liste der vom Asset referenzierten Assets anzuzeigen. |
| [!UICONTROL Asset-Verweise] | Fügen Sie dies hinzu, um eine Liste der Assets anzuzeigen, die das Asset referenzieren. |
| [!UICONTROL Produktverweise] | Fügen Sie dies hinzu, um die Liste der mit dem Asset verknüpften Produkte anzuzeigen. |
| [!UICONTROL Kontextuelle Metadaten] | Fügen Sie diese Komponente hinzu, um weitere Metadaten auf der Seite „Eigenschaften“ von Assets anzuzeigen. |

<!-- TBD: Ratings are not available in Experience Manager as a Cloud Service. Removed via cqdoc-18089 ticket. 
| [!UICONTROL Asset Rating]        | Add to display options for rating the asset.                                       |
-->

#### Bearbeiten von Metadatenkomponenten {#edit-the-metadata-component}

Um die Eigenschaften einer Metadaten-Komponente im Formular zu bearbeiten, klicken Sie auf die Komponente und bearbeiten Sie alle Eigenschaften oder einen Teil der folgenden Eigenschaften auf der Registerkarte **[!UICONTROL Einstellungen]**. Es wird empfohlen, nur ein Feld einer bestimmten Eigenschaft im Metadatenschema zuzuordnen. Andernfalls wird das der Eigenschaft zuletzt zugeordnete Feld vom System ausgewählt.

**Feldbezeichnung**: Der Name der Metadateneigenschaft, der auf der Eigenschaftenseite des Assets angezeigt wird.

**Zu Eigenschaft zuordnen**: Diese Eigenschaft gibt den relativen Pfad/Namen zum Asset-Knoten an, unter dem die Eigenschaft im CRX-Repository gespeichert ist. Sie beginnt mit `./`, um anzugeben, dass der Pfad sich unter dem Knoten des Assets befindet.

Im Folgenden finden Sie Beispiele für gültige Werte für eine Eigenschaft:

* `./jcr:content/metadata/dc:title`: Speichert den Wert im Metadatenknoten des Assets als die Eigenschaft `dc:title`.

* `./jcr:created`: Speichert das Erstellungsdatum und die Erstellungsuhrzeit eines Assets. Dies ist eine geschützte Eigenschaft. Wenn Sie diese Eigenschaften konfigurieren, empfiehlt Adobe, dass Sie sie mit Bearbeitung deaktivieren markieren. Andernfalls tritt der Fehler „Assets konnten nicht geändert werden“ auf, wenn Sie die Eigenschaften des Assets speichern.

Um sicherzustellen, dass die Komponente ordnungsgemäß im Metadatenschema-Formular angezeigt wird, sollte der Eigenschaftspfad keine Leerzeichen enthalten.

* **Platzhalter**: Verwenden Sie diese Eigenschaft, um relevanten Platzhaltertext für die Metadateneigenschaft anzugeben.
* **Erforderlich**: Mit dieser Eigenschaft können Sie eine Metadateneigenschaft auf der Eigenschaftsseite als obligatorisch markieren.
* **Bearbeitung deaktivieren**: Verwenden Sie diese Eigenschaft, um die Bearbeitung einer Eigenschaft auf der Eigenschaftsseite zu verbieten.
* **Leeres Feld schreibgeschützt anzeigen**: Markieren Sie diese Eigenschaft, um eine Metadateneigenschaft auch dann auf der Eigenschaftenseite anzuzeigen, wenn sie keinen Wert aufweist. Standardmäßig werden Metadateneigenschaften ohne Werte nicht auf der Eigenschaftenseite aufgeführt.
* **Liste geordnet anzeigen**: Mit dieser Eigenschaft zeigen Sie eine geordnete Liste von Optionen an.
* **Wahlen**: Mit dieser Eigenschaft legen Sie Optionen in einer Liste fest.
* **Beschreibung**: Mit dieser Eigenschaft können Sie eine kurze Beschreibung für die Metadatenkomponente hinzufügen.
* **Klasse**: Objektklasse, mit der die Eigenschaft verknüpft ist.
* **Löschen**: Klicken Sie auf [!UICONTROL Löschen], um eine Komponente aus dem Schemaformular zu löschen.

>[!NOTE]
>
>Die Komponente [!UICONTROL Ausgeblendetes Feld] enthält diese Attribute nicht. Sie enthält stattdessen Eigenschaften wie die Attribute „Name“, „Wert“, „Feldbezeichnung“ und „Beschreibung“. Die Werte für die Komponente „Ausgeblendetes Feld“ werden beim Speichern des Assets als POST-Parameter gesendet. Sie werden nicht als Metadaten für das Asset gespeichert.

Wenn Sie die Option **[!UICONTROL Erforderlich]** auswählen, können Sie nach Assets suchen, denen obligatorische Metadaten fehlen. Erweitern Sie im Bedienfeld **[!UICONTROL Filter]** die Eigenschaft **[!UICONTROL Metadatenvalidierung]** und wählen Sie die Option **[!UICONTROL Ungültig]**. Die Suchergebnisse zeigen Assets an, denen erforderliche Metadaten fehlen, die Sie über das Schemaformular konfiguriert haben.

Wenn Sie die Komponente „Kontextuelle Metadaten“ zu einer beliebigen Registerkarte eines beliebigen Schemaformulars hinzufügen, erscheint die Komponente als Liste auf der Eigenschaftsseite der Assets, auf die das jeweilige Schema angewendet wird. Die Liste enthält alle anderen Registerkarten außer der Registerkarte, auf die Sie die Komponente „Kontextuelle Metadaten“ angewendet haben. Derzeit bietet diese Funktion grundlegende Funktionalität zur Steuerung der Anzeige von Metadaten, die auf dem Kontext basieren.

Wenn Sie auf der Eigenschaftenseite zusätzlich zur Registerkarte, auf die die Komponente „Kontextuelle Metadaten“ angewendet wird, eine weitere Registerkarte aufnehmen möchten, wählen Sie die Registerkarte aus der Liste aus. Die Registerkarte wird der Eigenschaftenseite hinzugefügt.

### Festlegen von Eigenschaften in einer JSON-Datei {#specify-properties-in-json-file}

Anstatt die Eigenschaften für die Optionen auf der Registerkarte **[!UICONTROL Einstellungen]** anzugeben, können Sie die Optionen in einer JSON-Datei definieren, indem Sie die entsprechenden Schlüssel/Wert-Paare angeben. Geben Sie den Pfad der JSON-Datei im Feld **[!UICONTROL JSON-Pfad]** an.

#### Hinzufügen oder Löschen von Registerkarten im Schemaformular {#add-delete-a-tab-in-the-schema-form}

Mit dem Schema-Editor können Sie Registerkarten hinzufügen oder löschen. Das Standard-Schemaformular umfasst die Registerkarten **[!UICONTROL Standard]**, **[!UICONTROL Erweitert]**, **[!UICONTROL IPTC]** und **[!UICONTROL IPTC-Erweiterung]**.

![Standard-Registerkarten im Metadatenschema-Formular](assets/metadata-schema-form-tabs.png)

Klicken Sie auf `+`, um einem Schemaformular eine Registerkarte hinzuzufügen. Standardmäßig hat die neue Registerkarte den Namen `Unnamed-1`. Sie können den Namen auf der Registerkarte **[!UICONTROL Einstellungen]** ändern. Klicken Sie auf `X`, um eine Registerkarte zu löschen.

![Hinzufügen oder Löschen von Registerkarten mithilfe des Metadatenschema-Editors](assets/metadata-schema-form-new-tab.png)

## Löschen von Metadatenschema-Formularen {#deleting-metadata-schema-forms}

In Experience Manager können Sie nur benutzerdefinierte Schemaformulare löschen. Die Standardschemaformulare/-vorlagen können nicht gelöscht werden. Sie können jedoch alle benutzerdefinierten Änderungen in diesen Formularen löschen.

Um ein Formular zu löschen, wählen Sie das Formular aus und klicken Sie auf das Symbol zum Löschen.

>[!NOTE]
>
>Wenn Sie benutzerspezifische Änderungen an einem Standardformular löschen, wird das Sperrsymbol wieder vor dem Formular auf der Metadatenschema-Benutzeroberfläche angezeigt, um zu kennzeichnen, dass das Formular wieder in den Standardzustand versetzt wurde.

>[!NOTE]
>
>* Nachdem Sie benutzerdefinierte Änderungen an einem Standardformular gelöscht haben, wird die Sperre ![lock closed](assets/do-not-localize/lock_closed_icon.svg) vor dem Formular erneut angezeigt. Sie zeigt an, dass das Formular wieder in den Standardzustand versetzt wurde.
>* Sie können die Standard-Metadatenschema-Formulare in [!DNL Assets] nicht löschen.

## Schemaformulare für MIME-Typen {#schema-forms-for-mime-types}

[!DNL Experience Manager] stellt voreingestellte Standardformulare für verschiedene MIME-Typen bereit. Sie können jedoch benutzerdefinierte Formulare für verschiedene MIME-Typen hinzufügen.

### Hinzufügen neuer Formulare für MIME-Typen {#adding-new-forms-for-mime-types}

Erstellen Sie ein neues Formular unter dem entsprechenden Formulartyp. Beispiel: Um eine neue Vorlage für den Untertyp `image/png` hinzuzufügen, erstellen Sie das Formular unter den „Bild“-Formularen. Der Titel für das Schemaformular ist der Name des Untertyps. In diesem Fall ist der Titel `png`.

#### Verwenden einer vorhandenen Schemavorlage für verschiedene MIME-Typen {#use-an-existing-schema-template-for-various-mime-types}

Sie können eine vorhandene Vorlage für einen anderen MIME-Typ verwenden. Nutzen Sie beispielsweise das Formular `image/jpeg` für Assets mit dem MIME-Typ `image/png`.

Erstellen Sie in diesem Fall einen Knoten unter `/etc/dam/metadataeditor/mimetypemappings` im CRX-Repository. Geben Sie einen Namen für den Knoten an und definieren Sie die folgenden Eigenschaften:

| Name | Beschreibung | Typ | Wert |
|------|-------------|------|-------|
| `exposedmimetype` | Name des vorhandenen Formulars, das zugeordnet werden soll | `String` | `image/jpeg` |
| `mimetypes` | Liste der MIME-Typen, die das im Attribut `exposedmimetype` definierte Formular verwenden | `String` | `image/png` |

[!DNL Assets] ordnet die folgenden MIME-Typen und Schemaformulare zu:

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

## Zugriff auf Metadatenschemata gewähren {#grant-access-to-metadata-schemas}

Die Funktion „Metadatenschema“ ist nur für Administratoren verfügbar. Administratoren können anderen Benutzern allerdings Zugriff erteilen, indem sie einige Berechtigungen ändern. Geben Sie Benutzern ohne Administratorrechte Berechtigungen zum Erstellen, Ändern und Löschen für den Ordner `/conf`.

## Anwenden von ordnerspezifischen Metadaten {#applying-folder-specific-metadata}

Mit [!DNL Assets] können Sie Varianten eines Metadatenschemata definieren und auf einen bestimmten Ordner anwenden.

Sie können beispielsweise eine Variante des Standard-Metadatenschemas definieren und auf einen Ordner anwenden. Wenn Sie das geänderte Schema anwenden, überschreibt es das ursprüngliche standardmäßige Metadatenschema, das auf Assets im Ordner angewendet wird.

Nur Assets, die in den Ordner hochgeladen werden, auf den dieses Schema angewendet wird, entsprechen den geänderten Metadaten, die in der Variante des Metadatenschemas definiert sind. [!DNL Assets] in anderen Ordnern, für die das ursprüngliche Schema gilt, entsprechen weiterhin den im ursprünglichen Schema definierten Metadaten.

Die Metadatenübernahme durch Assets richtet sich nach dem Schema, das auf den Ordner der ersten Ebene in der Hierarchie angewendet wird. Dasselbe Schema wird auf die Unterordner angewendet oder von diesen übernommen. Wenn ein anderes Schema auf Unterordnerebene angewendet wird, stoppt die Übernahme.

1. Gehen Sie in der [!DNL Experience Manager]-Benutzeroberfläche zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemata]**. Die Seite **[!UICONTROL Metadatenschema-Formulare]** wird angezeigt.
1. Aktivieren Sie das Kontrollkästchen vor einem Formular, z. B. dem Standard-Metadatenformular, klicken Sie auf **[!UICONTROL Kopieren]** und speichern Sie es als benutzerdefiniertes Formular. Geben Sie einen benutzerdefinierten Namen für das Formular an, beispielsweise `my_default`. Alternativ können Sie ein benutzerdefiniertes Formular erstellen.

1. Wählen Sie auf der Seite **[!UICONTROL Metadatenschema-Formulare]** das Formular `my_default` und klicken Sie dann auf **[!UICONTROL Bearbeiten]**.
1. Fügen Sie auf der Seite **[!UICONTROL Metadatenschema-Editor]** ein Textfeld in das Schemaformular ein. Fügen Sie beispielsweise ein Feld mit der Bezeichnung **[!UICONTROL Kategorie]** hinzu.
1. Klicken Sie auf **[!UICONTROL Speichern]**. Das geänderte Formular wird auf der Seite **[!UICONTROL Metadatenschema-Formulare]** aufgeführt.
1. Wählen Sie in der Symbolleiste **[!UICONTROL Auf Ordner anwenden]** aus, um die benutzerdefinierten Metadaten auf einen Ordner anzuwenden.
1. Wählen Sie den Ordner aus, auf den Sie das geänderte Schema anwenden möchten, und wählen Sie anschließend **[!UICONTROL Anwenden]** aus.
1. Wurde das andere Metadatenschema auf den Ordner angewendet, erhalten Sie eine Meldung mit der Warnung, dass Sie im Begriff sind, das vorhandene Metadatenschema zu überschreiben. Klicken Sie auf **Überschreiben**.
1. Klicken Sie auf **OK**, um die Erfolgsmeldung zu schließen.
1. Navigieren Sie zu dem Ordner, auf den Sie das geänderte Metadatenschema angewendet haben.

## Definieren erforderlicher Metadaten {#defining-mandatory-metadata}

Sie können Pflichtfelder auf Ordnerebene definieren, die für in den Ordner hochgeladene Assets erzwungen werden. Wenn Sie Assets mit fehlenden Metadaten für die zuvor definierten Pflichtfelder hochladen, wird in der Kartenansicht ein entsprechender visueller Hinweis für die Assets angezeigt.

>[!NOTE]
>
>Ein Metadatenfeld kann je nach dem Wert eines weiteren Felds als Pflichtfeld definiert werden. In der Kartenansicht zeigt Experience Manager keine Warnung zu fehlenden Metadaten für solche obligatorischen Metadatenfelder an.

1. Klicken Sie auf das Experience Manager-Logo und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemas]**. Die Seite **[!UICONTROL Metadatenschema-Formulare]** wird angezeigt.
1. Speichern Sie die Standard-Metadatenformulare als benutzerdefiniertes Formular. Speichern Sie sie beispielsweise unter dem Namen `my_default`.
1. Bearbeiten Sie das benutzerdefinierte Formular. Fügen Sie ein erforderliches Feld hinzu. Fügen Sie beispielsweise ein Feld mit der Bezeichnung **[!UICONTROL Kategorie]** hinzu und definieren Sie es als Pflichtfeld.
1. Klicken Sie auf **[!UICONTROL Speichern]**. Das geänderte Formular wird auf der Seite **[!UICONTROL Metadatenschema-Formulare]** aufgeführt. Wählen Sie das Formular und anschließend in der Symbolleiste **[!UICONTROL Auf Ordner anwenden]** aus, um die benutzerdefinierten Metadaten auf einen Ordner anzuwenden.
1. Navigieren Sie zum Ordner und laden Sie einige Assets mit fehlenden Metadaten für das Pflichtfeld, das Sie dem benutzerdefinierten Formular hinzugefügt haben. Eine Meldung über die fehlenden Metadaten für das Pflichtfeld wird auf der Kartenansicht des Assets angezeigt.
1. (Optional) Rufen Sie `https://[server]:[port]/system/console/components/` auf. Konfigurieren und aktivieren Sie die Komponente `com.day.cq.dam.core.impl.MissingMetadataNotificationJob`, die standardmäßig deaktiviert ist. Legen Sie fest, mit welcher Häufigkeit Experience Manager die Gültigkeit der Metadaten in den Assets überprüfen soll.

   Diese Konfiguration fügt eine Eigenschaft `hasValidMetadata` zu `jcr:content` in Assets hinzu. Mit dieser Eigenschaft kann Experience Manager die Ergebnisse in einer Suche filtern.

   >[!NOTE]
   >
   >Wenn ein Asset nach der geplanten Prüfung hinzugefügt wird, wird das Asset erst bei der nächsten geplanten Prüfung mit `hasValidMetadata` gekennzeichnet. In der Zwischenzeit werden die Assets nicht in Suchergebnissen angezeigt.

   >[!CAUTION]
   >
   >Die Metadaten-Überprüfungen sind ressourcenintensiv und können die Leistung Ihres Systems beeinträchtigen. Planen Sie die Überprüfungen entsprechend. Wenn der Server die Last nicht bewältigen kann, versuchen Sie, diesen Auftrag zu deaktivieren

**Siehe auch**

* [Assets übersetzen](translate-assets.md)
* [Assets-HTTP-API](mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](file-format-support.md)
* [Suchen von Assets](search-assets.md)
* [Connected Assets](use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](asset-reports.md)
* [Herunterladen von Assets](download-assets-from-aem.md)
* [Verwalten von Metadaten](manage-metadata.md)
* [Suchfacetten](search-facets.md)
* [Verwalten von Sammlungen](manage-collections.md)
* [Massenimport von Metadaten](metadata-import-export.md)
* [Veröffentlichen von Assets in AEM und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)