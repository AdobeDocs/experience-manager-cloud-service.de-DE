---
title: Wie können Metadaten für AEM Forms verwaltet werden?
description: Metadaten ermöglichen eine einfachere Kategorisierung und Organisation der Assets und erleichtern Benutzern die Suche nach einem bestimmten Asset.
feature: Adaptive Forms, Foundation Components
exl-id: 8527246a-37f0-4d43-a49e-1c76c265514e
role: User, Developer
source-git-commit: b5340c23f0a2496f0528530bdd072871f0d70d62
workflow-type: tm+mt
source-wordcount: '1735'
ht-degree: 100%

---

# Hinzufügen, Entfernen oder Bearbeiten von Metadaten eines adaptiven Formulars {#manage-form-metadata}

>[!NOTE]
>
> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) für die Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/creating-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von adaptiven Formularen mithilfe von Foundation-Komponenten beschrieben.


| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/manage-form-metadata.html) |
| AEM as a Cloud Service | Dieser Artikel |

Metadaten ermöglichen eine einfachere Kategorisierung und Organisation der Assets und erleichtern Benutzern die Suche nach einem bestimmten Asset.

[!DNL AEM Forms] stellt standardmäßig einen definierten Metadatensatz für jeden Asset-Typ bereit. Neben den Standardmetadaten können Sie auch benutzerdefinierte Metadaten zu den einzelnen Asset-Typen hinzufügen. [!DNL AEM Forms] bietet Ihnen außerdem die richtigen Möglichkeiten zum effizienten Erstellen, Verwalten und Austauschen aller Metadaten für Ihre Formulare.

<!-- If you are a developer or a site owner, you can customize Forms Portal, the end-user interface for [!DNL AEM Forms] to reflect the metadata you are using in your organization. For more information abouts Forms Portal, see [Introduction to publishing forms on a portal](introduction-publishing-forms.md). -->

## Metadaten in [!DNL AEM Forms] {#metadata-in-aem-forms}

In [!DNL AEM Forms] ist die Liste der mit einem Asset verknüpften Metadateneigenschaften von dessen Typ abhängig. Wenn Sie außerdem eine benutzerdefinierte Metadateneigenschaft hinzufügen, wird diese für alle Assets des Typs hinzugefügt, für den die benutzerdefinierten Metadaten hinzugefügt wurden.

### Asset-Typen {#asset-types}

Die folgenden Asset-Typen werden in [!DNL AEM Forms] unterstützt:

* Formularvorlagen (XFA-Formulare)
* PDF-Formulare
* Dokument (einfache PDFs)
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
   <td>Beschreibung des Assets. Die Benutzerin bzw. der Benutzer kann diesen Wert angeben.<br /> </td> 
  </tr> 
  <tr> 
   <td>Typ</td> 
   <td>Alle</td> 
   <td><p>Ein schreibgeschützter Wert, der den Asset-Typ angibt. Er kann einen der folgenden Werte aufweisen:</p> 
    <ul> 
     <li>Formularvorlage</li> 
     <li>PDF-Formular, PDF-Formular (Acroform) oder PDF-Formular (Signiert)</li> 
     <li>Dokument, Dokument (Signiert)</li> 
     <li>Adaptives Formular</li> 
     <li>Formulardatenmodell (FDM)</li>
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
   <td><p>Ein schreibgeschützter Wert, der basierend auf dem Formulartyp automatisch berechnet wird.</p> 
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
     <li>Kein Wert: wenn ein Formular noch nie veröffentlicht wurde.</li> 
     <li>Veröffentlicht: wenn ein Formular veröffentlicht wurde.</li> 
     <li>Geändert: wenn ein Formular nach seiner Veröffentlichung geändert wurde.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Letztes Veröffentlichungsdatum</td> 
   <td>Alle außer Ressource</td> 
   <td>Ein schreibgeschützter Wert, der angibt, wann das Formular zuletzt veröffentlicht wurde.</td> 
  </tr> 
  <tr> 
   <td>Zeit von „Veröffentlichen ein/aus“</td> 
   <td>Alle außer Ressource</td> 
   <td><p>Zeitpunkt, zu dem die automatische Veröffentlichung bzw. Aufhebung der Veröffentlichung des Formulars geplant ist. Die Benutzerin bzw. der Benutzer legt diesen Wert beim Bearbeiten von Metadaten fest.</p> 
    <ul> 
     <li>Die beiden Zeiten „Veröffentlichen ein“ und „Veröffentlichen aus“ sollten über das aktuelle Datum hinausgehen. </li> 
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
   <td>HTML-Renderprofil</td> 
   <td>Formularvorlage</td> 
   <td>Das HTML-Renderprofil, das beim Rendern einer Formularvorlage im HTML-Format verwendet wird.</td> 
  </tr> 
  <tr> 
   <td>Renderformat</td> 
   <td><p>Formularvorlage</p> <p>Adaptives Formular</p> </td> 
   <td><p>Mit dieser Option kann die Benutzerin bzw. der Benutzer das Renderformat des Formulars bei der Veröffentlichung der Formulare angeben:</p> 
    <ul> 
     <li>HTML</li> 
     <li>PDF</li> 
     <li>Beide</li> 
    </ul> <p>Diese Option wird zum Eingrenzen des Renderformats der Formulare nur im Formularportal verwendet, wo sie für die Benutzenden sichtbar sind.</p> </td> 
  </tr> 
  <tr> 
   <td>Tags</td> 
   <td>Alle außer Ressource</td> 
   <td>Mit dem Formular verknüpfte Beschriftungen, um eine schnelle und einfache Suche zu ermöglichen.</td> 
  </tr> 
  <tr> 
   <td>Verweise</td> 
   <td><p>Adaptives Formular</p> <p>Formularvorlage</p> <p>Ressource</p> </td> 
   <td><p>Liste der Assets (andere Formulare oder Ressourcen), mit denen dieses Formular verknüpft ist. Diese Assets können in die folgenden beiden Kategorien unterteilt werden:</p> 
    <ul> 
     <li>Verweist auf: Assets, auf die das aktuelle Formular verweist.</li> 
     <li>Verwiesen von: Assets, die auf das aktuelle Asset verweisen.</li> 
    </ul> <p>Diese Assets werden als Links angezeigt, und der Zugriff auf ihre Metadaten erfolgt direkt durch Klicken auf sie.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>Auswahl des Formularmodells (XDP/XSD)</td> 
   <td>Adaptives Formular</td> 
   <td><p>Gibt an, welches Formularmodell beim Verfassen des adaptiven Formulars verwendet wird. Diese Eigenschaft kann folgende Werte haben:</p> 
    <ul> 
      <li>Formulardatenmodell (FDM)</li>
      <li>Schema: Ein XML- oder JSON-Schema</li>
     <!-- <li>Form template: A form template is selected from the ones existing in the repository. This value can be updated.</li> 
     <li>XML schema: An XSD file is uploaded. This value can be updated.</li> -->
     <li>Ohne</li> 
    </ul> 
    <div>
      Ein einmal ausgewähltes Formularmodell kann aktualisiert, aber nicht entfernt werden. 
    </div> </td> 
  </tr> 
 </tbody> 
</table>

## Anzeigen von Formularmetadaten {#view-form-metadata}

Assets verfügen über vorhandene Eigenschaftswerte, die im schreibgeschützten Modus angezeigt werden können. Diese Metadaten stammen vom Zeitpunkt des Formular-Uploads oder der Formularerstellung.

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

Für alle Formulartypen haben Sie die Möglichkeit, ein Bild hochzuladen, indem Sie auf **[!UICONTROL Bild hochladen]** klicken und im lokalen Verzeichnis nach einer Grafikdatei suchen. Das ausgewählte Bild wird anstelle des Standardbilds als Miniaturansicht verwendet.

Bei adaptiven Formularen werden zusätzliche Funktionen bereitgestellt, mit denen der Benutzer eine Miniaturansicht als Momentaufnahme der aktuellen Vorschau des adaptiven Formulars generieren kann. Da [!DNL AEM Forms] auch das Erstellen adaptiver Formulare unterstützt, kann sich die Vorschau des adaptiven Formulars ändern, wenn Sie das adaptive Formular ändern. Mit dieser Funktion zum Generieren einer Miniaturansicht können Sie eine neue Miniaturansicht für das adaptive Formular erzeugen, die auf dem aktuellen Vorschaustatus basiert. Klicken Sie auf **[!UICONTROL Vorschau generieren]**, um diese Aktion durchzuführen.

>[!NOTE]
>
>* Verwenden Sie ein quadratisches Bild für die Miniaturansicht. Wenn Sie ein nicht quadratisches Bild verwenden und die Miniaturansicht in der Listenansicht anzeigen, ist die Miniaturansicht abgeschnitten.
>* Sobald ein neues Bild hochgeladen oder generiert wurde, wird die Miniaturansicht durch dieses Bild ersetzt und kann nicht auf das vorherige Bild zurückgesetzt werden.
>

## Hinzufügen benutzerdefinierter Metadaten {#add-custom-metadata}

Zusätzlich zu den standardmäßig bereitgestellten Metadaten unterstützt [!DNL AEM Forms] auch neue benutzerdefinierte Metadaten.

Ein Tool (Metadatenschema-Editor) wird bereitgestellt, um das Schema für das Metadaten-Layout zu definieren (also das Layout des Inhalts der Seite **[!UICONTROL Eigenschaften]** eines Formulars). Mit dem Metadatenschema-Editor können Sie ein benutzerdefiniertes Schema für Ihre Assets hinzufügen oder ändern.

[!DNL AEM Forms] stellt die Metadatenschemas der unterstützten Formulartypen in diesem Tool dar. Auf diese Weise können Sie auf diese Schemata zugreifen und die Funktion des Metadatenschema-Editors verwenden, um benutzerdefinierte Eigenschaften hinzuzufügen.

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

   1. Geben Sie eine Feldbeschriftung an, die als Anzeigename über dem im Schema platzierten Feld verwendet werden soll (z. B.: Department)
   1. Unter dem Feld „Zu Eigenschaft zuordnen“ wird ein bereits befüllter Wert angezeigt **„./jcr:content/metadata/default&#39;**. Ändern Sie den Namen „**default**“ in einen gewünschten Eigenschaftsnamen, mit dem die Eigenschaft im CRX-Repository gespeichert wird (zum Beispiel: „./jcr:content/metadata/department“)

      >[!NOTE]
      >
      >Ändern Sie nicht das Präfix „./jcr:content/metadata/“, da es den Pfad definiert, in dem die Eigenschaft gespeichert ist.
      >
      >Außerdem muss der Eigenschaftsname eindeutig sein, um zu vermeiden, dass Werte für zwei oder mehr Eigenschaften am selben Speicherort im Repository geschrieben werden. Daher wird empfohlen, den Wert „default“ zu ändern.

   1. Füllen Sie andere Einstellungen nach Bedarf aus. Beispiel: Wählen Sie die Option „Erforderlich“, um das Feld zu einem Pflichtfeld zu machen.
   1. Um ein hinzugefügtes Feld zu löschen, wählen Sie das Feld aus und klicken Sie dann auf das Symbol zum Löschen (![Delete](assets/Smock_Delete_18_N.svg)).

1. Bei Bedarf können Sie die Schritte 1 bis 3 wiederholen, um eine weitere Eigenschaft hinzuzufügen.
1. Klicken Sie auf **[!UICONTROL Speichern]**, nachdem Sie alle Änderungen vorgenommen haben.

   Sie haben erfolgreich eine benutzerdefinierte Metadateneigenschaft hinzugefügt.

Alle adaptiven Formulare in [!DNL AEM Forms] enthalten jetzt diese zusätzliche Metadateneigenschaft. Sie können sie über die Eigenschaftsseite bearbeiten.


## Siehe auch {#see-also}

{{see-also}}