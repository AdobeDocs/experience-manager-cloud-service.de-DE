---
title: Verwalten von Metadaten
seo-title: Manage [!DNL AEM Forms] metadata
description: Metadaten ermöglichen eine einfachere Kategorisierung und Organisation der Assets und erleichtern Benutzern die Suche nach einem bestimmten Asset.
seo-description: Metadata allows for easier categorization and organization of assets and helps users who are looking for a specific asset.
exl-id: 8527246a-37f0-4d43-a49e-1c76c265514e
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1660'
ht-degree: 100%

---

# Hinzufügen, Entfernen oder Bearbeiten von Metadaten eines adaptiven Formulars {#manage-form-metadata}

Metadaten ermöglichen eine einfachere Kategorisierung und Organisation der Assets und erleichtern Benutzern die Suche nach einem bestimmten Asset.

[!DNL AEM Forms] stellt standardmäßig einen definierten Metadatensatz für jeden Asset-Typ bereit. Neben den Standardmetadaten können Sie auch benutzerdefinierte Metadaten zu den einzelnen Asset-Typen hinzufügen. [!DNL AEM Forms] bietet Ihnen außerdem die richtigen Möglichkeiten zum effizienten Erstellen, Verwalten und Austauschen aller Metadaten für Ihre Formulare.

<!-- If you're a developer or a site owner, you can customize Forms Portal, the end-user interface for [!DNL AEM Forms] to reflect the metadata you're using in your organization. For more information abouts Forms Portal, see [Introduction to publishing forms on a portal](introduction-publishing-forms.md). -->

## Metadaten in [!DNL AEM Forms] {#metadata-in-aem-forms}

In [!DNL AEM Forms] ist die Liste der mit einem Asset verknüpften Metadateneigenschaften von dessen Typ abhängig. Wenn Sie außerdem eine benutzerdefinierte Metadateneigenschaft hinzufügen, wird diese für alle Assets des Typs hinzugefügt, für den die benutzerdefinierten Metadaten hinzugefügt wurden.

### Asset-Typen {#asset-types}

Die folgenden Asset-Typen werden in [!DNL AEM Forms] unterstützt:

* Formularvorlagen (XFA-Formulare)
* PDF-Formulare
* Dokument (Flat-PDFs)
* Adaptive Formulare
* Formulardatenmodell
* XFS

#### Umfassende Liste der Metadaten {#extensive-list-of-metadata}

Im Folgenden sehen Sie eine umfassende Liste der Metadateneigenschaften, die in [!DNL AEM Forms] unterstützt werden:

<table>
 <tbody> 
  <tr> 
   <td><strong>Eigenschaftsname</strong></td> 
   <td><strong>Asset-Typ</strong></td> 
   <td><strong>Beschreibung</strong><br /> </td> 
  </tr> 
  <tr> 
   <td>Titel</td> 
   <td>Alle außer Ressource</td> 
   <td>Anzeigename des Assets<br /> </td> 
  </tr> 
  <tr> 
   <td>Beschreibung</td> 
   <td>Alle außer Ressource</td> 
   <td>Beschreibung des Assets. Der Benutzer kann diesen Wert angeben.<br /> </td> 
  </tr> 
  <tr> 
   <td>Typ</td> 
   <td>Alle</td> 
   <td><p>Ein schreibgeschützter Wert, der den Typ des Assets angibt. Er kann einen der folgenden Werte annehmen:</p> 
    <ul> 
     <li>Formularvorlage</li> 
     <li>PDF-Formular, PDF-Formular (Acroform) oder PDF-Formular (Signiert)</li> 
     <li>Dokument, Dokument (Signiert)</li> 
     <li>Adaptives Formular</li> 
     <li>Formulardatenmodell</li>
     <li>Ressource</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Erstellt</td> 
   <td>Alle</td> 
   <td>Ein schreibgeschützter Wert, der den Zeitpunkt der Asset-Erstellung angibt.</td> 
  </tr> 
  <tr> 
   <td>Datum der letzten Änderung</td> 
   <td>Alle</td> 
   <td>Ein schreibgeschützter Wert, der angibt, wann das Asset zuletzt geändert wurde.</td> 
  </tr> 
  <tr> 
   <td>Autor</td> 
   <td>Alle außer Ressource</td> 
   <td><p>Ein schreibgeschützter Wert, der automatisch basierend auf dem Formulartyp berechnet wird.</p> 
    <ul> 
     <li>PDF/Formularvorlage/Dokument – von der hochgeladenen Binärdatei abgerufen.</li> 
     <li>Adaptives Formular – angemeldeter Benutzer zum Zeitpunkt der Formularerstellung.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Status</td> 
   <td>Alle außer Ressource</td> 
   <td><p> Ein schreibgeschützter Wert, der einen der folgenden Status eines Formulars definiert:</p> 
    <ul> 
     <li>Kein Wert: Wenn ein Formular noch nicht veröffentlicht wurde.</li> 
     <li>Veröffentlicht: Wenn ein Formular veröffentlicht wurde.</li> 
     <li>Geändert: Wenn ein Formular nach seiner Veröffentlichung geändert wurde.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Letztes Veröffentlichungsdatum</td> 
   <td>Alle außer Ressource</td> 
   <td>Ein schreibgeschützter Wert, der angibt, wann das Formular zuletzt veröffentlicht wurde.</td> 
  </tr> 
  <tr> 
   <td>Publish on/off time (Zeit für Veröffentlichung ein/aus)</td> 
   <td>Alle außer Ressource</td> 
   <td><p>Zeitpunkt, an dem das Formular planmäßig automatisch veröffentlicht bzw. die Veröffentlichung rückgängig gemacht werden soll. Der Benutzer legt diesen Wert beim Bearbeiten der Metadaten fest.</p> 
    <ul> 
     <li>Die Werte für diese Einstellung müssen nach dem aktuellen Datum liegen. </li> 
     <li>Die Zeit für die Deaktivierung der Veröffentlichung muss nach der Aktivierungszeit liegen. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Übermittlungs-URL</td> 
   <td><p>Formularvorlage</p> <p>PDF-Formular</p> </td> 
   <td><p>Zum Konfigurieren einer benutzerspezifizierten URL zum Übermitteln von Formulardaten an ein Servlet.</p> <p>Die Übermittlungs-URL kann mit einer der folgenden Methoden konfiguriert werden, die nach Priorität sortiert aufgeführt werden:</p> 
    <ul> 
     <li>Geben Sie über die Schaltfläche zum Übermitteln von HTTP beim Erstellen eines XFA-Formulars in AEM Forms Designer eine Übermittlungs-URL direkt in einer Formularvorlage an.</li> 
     <li>Wählen Sie in der AEM Forms-Benutzeroberfläche ein Formular aus und geben Sie eine Übermittlungs-URL bei der Bearbeitung der Metadateneigenschaften an.</li> 
     <!-- <li>In Forms Portal, edit the Search &amp; Lister component and specify a submit URL under the Form Link tab.</li> -->
    </ul> </td> 
  </tr> 
  <tr> 
   <td>HTML render profile (HTML-Renderprofil)</td> 
   <td>Formularvorlage</td> 
   <td>Das HTML-Renderprofil, das bei der Wiedergabe einer Formularvorlage im HTML-Format verwendet wird.</td> 
  </tr> 
  <tr> 
   <td>Render format (Renderformat)</td> 
   <td><p>Formularvorlage</p> <p>Adaptives Formular</p> </td> 
   <td><p>Diese Option ermöglicht es dem Benutzer, das Renderformat des Formulars anzugeben, wenn die Formulare veröffentlicht werden:</p> 
    <ul> 
     <li>HTML</li> 
     <li>PDF</li> 
     <li>Beide</li> 
    </ul> <p>Diese Option wird zum Eingrenzen des Renderformats der Formulare nur im Forms Portal verwendet, wo sie für Endbenutzer sichtbar sind.</p> </td> 
  </tr> 
  <tr> 
   <td>Tags</td> 
   <td>Alle außer Ressource</td> 
   <td>Mit dem Formular verknüpfte Beschriftungen, um schnelle und einfache Suche zu erleichtern.</td> 
  </tr> 
  <tr> 
   <td>Verweise</td> 
   <td><p>Adaptives Formular</p> <p>Formularvorlage</p> <p>Ressource</p> </td> 
   <td><p>Liste der Assets (andere Formulare oder Ressourcen), mit denen dieses Formular verwandt ist. Diese Assets können zu den folgenden zwei Kategorien gehören:</p> 
    <ul> 
     <li>Refers (Verweist): Assets, auf die das aktuelle Formular verweist.</li> 
     <li>Referred by (Referenziert von): Assets, die auf das aktuelle Asset verweisen.</li> 
    </ul> <p>Diese Assets werden als Links angezeigt, auf die Sie klicken können, um direkt auf ihre Metadaten zuzugreifen.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>Form model (XDP/XSD) selection (Formularmodellauswahl (XDP/XSD))</td> 
   <td>Adaptives Formular</td> 
   <td><p>Gibt an, welches Formularmodell beim Verfassen des adaptiven Formulars verwendet wird. Diese Eigenschaft kann folgende Werte haben:</p> 
    <ul> 
      <li>Formulardatenmodell </li>
      <li>Schema: Ein XML- oder JSON-Schema</li>
     <!-- <li>Form template: A form template is selected from the ones existing in the repository. This value can be updated.</li> 
     <li>XML schema: An XSD file is uploaded. This value can be updated.</li> -->
     <li>Ohne</li> 
    </ul> 
    <div>
      Ein ausgewähltes Formularmodell kann aktualisiert, aber nicht entfernt werden. 
    </div> </td> 
  </tr> 
 </tbody> 
</table>

## Anzeigen von Formularmetadaten {#view-form-metadata}

Assets weisen vorhandene Eigenschaftswerte auf, die im schreibgeschützten Modus angezeigt werden können. Diese Metadaten entstehen zum Zeitpunkt des Formular-Uploads oder der Formularerstellung.

1. Navigieren Sie zum Speicherort des Assets, für das Sie Metadaten anzeigen möchten.

1. Öffnen Sie die Eigenschaftsseite mit einer der folgenden Methoden:

   * Klicken Sie in den Schnellaktionen auf das Symbol **[!UICONTROL Eigenschaften]** (![Properties](assets/Smock_Info_18_N.svg)).

      >[!NOTE]
      >
      >Schnellaktionen sind die Aktionselemente, die beim Zeigen mit der Maus auf eine Miniaturansicht angezeigt werden.

   * Wählen Sie das Formular aus und klicken Sie auf das Symbol **[!UICONTROL Eigenschaften]** (![Properties](assets/Smock_Info_18_N.svg)) in der Symbolleiste.
   * Navigieren Sie zur Seite mit den Formulardetails, indem Sie auf die Formularminiaturansicht klicken, während Sie sich nicht im Auswahlmodus befinden. Klicken Sie nun oben rechts auf das Symbol ![Properties](assets/Smock_Info_18_N.svg) und anschließend in der Liste darunter auf „Eigenschaften“.

1. Auf der daraufhin geöffneten Eigenschaftsseite wird ein Schema angezeigt, das nur die Metadateneigenschaften mit einem Wert enthält.

   <!-- The properties page has a toolbar containing two action icons:

    * Edit: ![Edit](assets/Smock_Edit_18_N.svg) Edit the metadata property values
    * View: ![aem6forms_eye_viewon](assets/aem6forms_eye_viewon.png) Navigate to the form details page, which opens the form in the preview mode. -->

   Der Inhaltsbereich ist in zwei Abschnitte unterteilt:

   * Das linke Bedienfeld enthält die Miniaturansicht des Formulars.
   * Das rechte Bedienfeld enthält Metadateneigenschaften im schreibgeschützten Modus, die über verschiedene Registerkarten verteilt sind.

## Hinzufügen/Aktualisieren von Formularmetadatenwerten {#add-update-form-metadata-values}

Sie können den Wert vorhandener Metadateneigenschaften bearbeiten oder einem vorhandenen Metadateneigenschaftsfeld neue Werte hinzufügen (zum Beispiel wenn ein Metadatenfeld leer ist).

<!-- ### Update metadata property values {#update-metadata-property-values}

1. Follow the steps mentioned in the previous section to open the properties page where existing metadata of the selected form can be viewed.  

1. From the toolbar, click the Edit icon ![Edit](assets/Smock_Edit_18_N.svg) to change the mode of the page from read-only to read/write.  

1. The properties page that opens holds a schema that contains a mix of editable input fields and static text.  

1. The properties displayed in static text are the ones that you cannot edit.  

1. You can navigate to other tabs to find input fields for metadata properties placed under them.

   This page has a toolbar containing two action icons different from those in view mode:

    * Cancel: ![aem6forms_close](assets/aem6forms_close.svg_w24.png) Cancel any changes made to metadata property values so far
    * Done: ![aem6forms_check](assets/aem6forms_check.png) Save all the changes made to metadata property values so far

   Both these actions direct the user back to read-only mode of the properties page containing the updated values.-->

### Aktualisieren der Formularminiaturansicht {#update-the-form-thumbnail}

Im linken Bedienfeld der Eigenschaftsseite wird die Miniaturansicht des Formulars angezeigt. Standardmäßig wird die angezeigte Miniaturansicht zum Zeitpunkt der Formularerstellung (adaptives Formular) oder des Formular-Uploads generiert.

Bei allen Formulartypen können Sie ein Bild hochladen, indem Sie auf **[!UICONTROL Bild hochladen]** klicken und nach einer Bilddatei im lokalen Verzeichnis suchen. Das ausgewählte Bild wird anstelle des Standardbilds als Miniaturansicht verwendet.

Bei adaptiven Formularen werden zusätzliche Funktionen bereitgestellt, mit denen der Benutzer eine Miniaturansicht als Momentaufnahme der aktuellen Vorschau des adaptiven Formulars generieren kann. Da [!DNL AEM Forms] auch das Erstellen adaptiver Formulare unterstützt, kann sich die Vorschau des adaptiven Formulars ändern, wenn Sie das adaptive Formular ändern. Mit dieser Funktion zum Generieren einer Miniaturansicht können Sie eine neue Miniaturansicht für das adaptive Formular erzeugen, die auf dem aktuellen Vorschaustatus basiert. Klicken Sie auf **[!UICONTROL Vorschau generieren]**, um diese Aktion durchzuführen.

>[!NOTE]
>
>* Verwenden Sie ein quadratisches Bild für die Miniatur. Wenn Sie ein nicht quadratisches Bild verwenden und die Miniaturansicht in der Listenansicht anzeigen, ist die Miniaturansicht abgeschnitten.
>* Sobald ein neues Bild hochgeladen oder generiert wurde, wird die Miniaturansicht durch dieses Bild ersetzt und kann nicht auf das vorherige Bild zurückgesetzt werden.
>


## Hinzufügen benutzerdefinierter Metadaten {#add-custom-metadata}

Zusätzlich zu den standardmäßig bereitgestellten Metadaten unterstützt [!DNL AEM Forms] auch neue benutzerdefinierte Metadaten.

Ein Tool (Metadatenschema-Editor) wird bereitgestellt, um das Schema für das Metadaten-Layout zu definieren (also das Layout des Inhalts der Seite **[!UICONTROL Eigenschaften]** eines Formulars). Mit dem Metadatenschema-Editor können Sie ein benutzerdefiniertes Schema für Ihre Assets hinzufügen oder ändern.

[!DNL AEM Forms] stellt die Metadatenschemas der unterstützten Formulartypen in diesem Tool dar. Auf diese Weise können Sie auf diese Schemas zugreifen und die Funktion des Metadatenschema-Editors verwenden, um benutzerdefinierte Eigenschaften hinzuzufügen.

### Navigieren im Metadatenschema-Editor {#navigate-the-metadata-schema-editor}

1. Navigieren Sie zu **[!UICONTROL Tools > Assets > Metadatenschemas]**.

1. Klicken Sie in den aufgeführten Schemaformularen auf **[!UICONTROL Formulare]**.

1. Klicken Sie in der Liste, die geöffnet wird, auf den Asset-Typ, für den Sie benutzerdefinierte Metadaten hinzufügen möchten.

   >[!NOTE]
   >
   >Diese Schemas enthalten Metadateneigenschaften, die standardmäßig bereitgestellt werden und nicht geändert/bearbeitet werden dürfen (Kontrollkästchen aktivieren und in der Symbolleiste auf „Bearbeiten“ klicken), um Funktionsprobleme zu vermeiden.

1. Wenn Sie auf einen Asset-Typ klicken, wird eine Liste mit der Option `extendedmetadata` geöffnet. Bearbeiten Sie dieses Schema.

1. Aktivieren Sie das Kontrollkästchen neben `extendedmetadata` und klicken Sie dann auf das Bearbeitungssymbol ![Edit](assets/Smock_Edit_18_N.svg), das in der Symbolleiste angezeigt wird.

1. [!DNL AEM Forms] öffnet den Metadatenschema-Editor/Formularersteller des ausgewählten Asset-Typs (in diesem Fall „adaptives Formular“).

   Metadateneditor

   1. Das linke Bedienfeld enthält Abschnitte in Registerkarten mit den Feldern und im rechten Bedienfeld werden alle verfügbaren Benutzeroberflächen-Komponenten sowie die Eigenschaften des im linken Bedienfeld ausgewählten Feldes angezeigt.

   1. Der gesperrte Abschnitt kann nicht bearbeitet werden und enthält Felder für alle Metadateneigenschaften, die standardmäßig bereitgestellt werden.

   1. Sie können weitere Registerkarten hinzufügen, indem Sie auf + klicken.

   1. Sie können ein benutzerdefiniertes Feld des gewünschten Typs hinzufügen, indem Sie die Feldkomponente aus dem Abschnitt **[!UICONTROL Formular erstellen]** auf die Schemaseite ziehen.
   1. Die Spezifikationen für dieses Feld können im Abschnitt **[!UICONTROL Einstellungen]** angegeben werden, nachdem Sie auf das Feld geklickt haben.

### Hinzufügen benutzerdefinierter Metadateneigenschaften im Schemaeditor {#add-custom-metadata-property-in-schema-editor}

1. Navigieren Sie zur Registerkarte (vorhanden oder neu), der Sie die benutzerdefinierte Eigenschaft hinzufügen möchten.

1. Ziehen Sie eine Komponente des gewünschten Typs aus dem Abschnitt **[!UICONTROL Formular erstellen]** in das linke Bedienfeld und platzieren Sie sie an der gewünschten Stelle.

   >[!NOTE]
   >
   >Sie können gesperrte Abschnitte nicht verschieben, aber Sie können die Komponente in einem der leeren Bereiche platzieren.

1. Klicken Sie auf eine Komponente, die Sie gerade verschoben haben. Geben Sie in der Registerkarte „Einstellungen“, die im rechten Bedienfeld geöffnet wird, die Informationen für folgende Felder ein:

   1. Geben Sie eine Feldbeschriftung an, die als Anzeigename über dem im Schema platzierten Feld verwendet wird (zum Beispiel: Abteilung).
   1. Unter dem Feld „Zu Eigenschaft zuordnen“ wird ein bereits befüllter Wert angezeigt **&#39;./jcr:content/metadata/default“**. Ändern Sie „**default**“ in einen gewünschten Eigenschaftsnamen, mit dem die Eigenschaft im CRX-Repository gespeichert wird (zum Beispiel „./jcr:content/metadata/department“)

      >[!NOTE]
      >
      >Ändern Sie nicht das Präfix „./jcr:content/metadata/“, da es den Pfad definiert, unter dem die Eigenschaft gespeichert ist.
      >
      >Außerdem muss der Eigenschaftsname eindeutig sein, damit nicht Werte für zwei oder mehr Eigenschaften in dieselbe Position im Repository geschrieben werden. Daher wird empfohlen, den Wert „default“ zu ändern.

   1. Geben Sie je nach Bedarf weitere Einstellungen an. Beispiel: Wählen Sie die Option „Erforderlich“, um das Feld zu einem Pflichtfeld zu machen.
   1. Um ein hinzugefügtes Feld zu löschen, wählen Sie das Feld aus und klicken Sie dann auf das Symbol zum Löschen (![Delete](assets/Smock_Delete_18_N.svg)).

1. Bei Bedarf können Sie die Schritte 1 bis 3 wiederholen, um eine weitere Eigenschaft hinzuzufügen.
1. Klicken Sie auf **[!UICONTROL Speichern]**, nachdem Sie alle Änderungen vorgenommen haben.

   Sie haben erfolgreich eine benutzerdefinierte Metadateneigenschaft hinzugefügt.

Alle adaptiven Formulare in [!DNL AEM Forms] enthalten jetzt diese zusätzliche Metadateneigenschaft. Sie können sie über die Eigenschaftsseite bearbeiten.
