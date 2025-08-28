---
title: Was sind adaptive Formularfragmente?
description: Adaptive Formulare bieten einen Mechanismus zum Erstellen eines Formularsegments (z. B. eines Bedienfelds oder einer Gruppe von Feldern) und zum Verwenden dieses Segments in einem beliebigen adaptiven Formular. Sie können auch ein vorhandenes Bedienfeld als Fragment speichern.
topic-tags: author
keywords: Adaptive Formularfragmente hinzufügen, adaptive Formularfragmente, Formularfragment erstellen, Fragment zu einem adaptiven Formular hinzufügen, Fragmente verwalten
feature: Adaptive Forms, Core Components
exl-id: 3a9ad1b7-2f6f-4ca9-a1c9-549c4238c59e
role: User, Developer
source-git-commit: bc422429d4a57bbbf89b7af2283b537a1f516ab5
workflow-type: ht
source-wordcount: '1479'
ht-degree: 100%

---

# Erstellen und Verwenden adaptiver Formularfragmente in einem adaptiven Formular basierend auf Kernkomponenten {#adaptive-form-fragments}


| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service (Kernkomponenten) | Dieser Artikel |
| AEM as a Cloud Service (Foundation-Komponenten) | [Hier klicken](/help/forms/adaptive-form-fragments.md) |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/adaptive-form-fragments.html?lang=de) |

Zwar wurde jedes Formular für einen bestimmten Zweck entwickelt, aber in den meisten Formularen gibt es gängige Segmente für persönliche Angaben wie Name und Anschrift, Familienmitglieder und Einkommen. Eine Formularentwicklerin bzw. ein Formularentwickler muss diese gängigen Segmente jedes Mal erstellen, wenn ein neues Formular erstellt wird.

Adaptive Formulare bieten einen praktischen Mechanismus, mit dem Formularsegmente wie ein Bedienfeld oder eine Gruppe von Feldern nur einmal erstellt und dann in adaptiven Formularen wiederverwendet werden können. Diese wiederverwendbaren, unabhängigen Segmente werden als adaptive Formularfragmente bezeichnet.

Formularfragmente lassen sich nahtlos in mehrere Formulare integrieren, wodurch die Erstellung konsistenter und professionell aussehender Formulare optimiert wird. Formularfragmente sorgen für Wiederverwendbarkeit, Standardisierung und Markenkonsistenz durch die Funktion „Einmal ändern und überall widerspiegeln“. Erleben Sie mehr Wartbarkeit und Effizienz, da Aktualisierungen an einem Ort automatisch über alle Formulare hinweg übernommen werden, die diese Fragmente verwenden.

Sie können ein Fragment mehrmals zu einem Dokument hinzufügen und die Datenbindungseigenschaften seiner Komponenten verwenden, um es mit verschiedenen Datenquellen oder Schemata zu verknüpfen. Beispielsweise können Sie dasselbe Adressfragment für permanente, Kommunikations- und Abrechnungsadressen verwenden und es mit verschiedenen Feldern einer Datenquellen oder eines Schemas verbinden.

>[!NOTE]
>
> Mit dem [Konfigurationsdialogfeld und dem Design-Dialogfeld der Formularfragment-Komponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/adaptive-form-fragment) können Sie Ihre Fragmente ganz einfach an die Bedürfnisse der Benutzenden anpassen.

## Erstellen eines adaptiven Formularfragments {#create-a-fragment}

Sie können adaptive Formularfragmente von Grund auf neu erstellen oder ein Panel in einem vorhandenen adaptiven Formular als Fragment speichern. So erstellen Sie ein Formularfragment:

1. Melden Sie sich bei Ihrer AEM Forms-Instanz unter https://[*hostname*]:[*port*]/aem/forms.html an.
1. Klicken Sie auf **Erstellen > Adaptives Formularfragment**.

   ![Erstellen eines adaptiven Formularfragments](/help/forms/assets/adaptive-form-fragment.png)

1. Geben Sie Titel, Namen, Beschreibung und Tags für das Fragment an. Stellen Sie sicher, dass Sie einen eindeutigen Namen für das Fragment angeben. Wenn bereits ein anderes Fragment mit demselben Namen vorhanden ist, kann das Fragment nicht erstellt werden.
1. Wählen Sie eine Formularvorlage aus. Sie können ein Formularfragment für auf Kernkomponenten basierende adaptive Formulare oder auf Foundation-Komponenten basierende adaptive Formulare erstellen. Um Formularfragmente für auf Kernkomponenten basierende Formulare zu erstellen, wählen Sie eine auf Kernkomponenten basierende Vorlage aus.

   Wenn Sie Formularfragmente für auf Kernkomponenten basierende Formulare erstellen, verwenden Sie die Option „Formular-Design auswählen“, um ein Kernkomponenten-basiertes Design auszuwählen.

1. Klicken Sie, um die Registerkarte **Formularmodell** zu öffnen. Wählen Sie dann aus der Dropdown-Liste **Auswählen aus** eines der folgenden Fragmentmodelle:

   ![Zeigt den Modelltyp auf der Registerkarte „Formularmodell“ an](assets/create-af-1-1.png)

   * **Keine**: Gibt an, dass das Fragment von Grund auf ohne Formularmodell erstellt werden soll.

     >[!NOTE]
     >
     > In adaptiven Formularen können Sie ein einzelnes Formularfragment (basierend auf Kernkomponenten) mehrmals verwenden. Es unterstützt sowohl auf nichts basierende als auch schemabasierte Formularfragmente.

   * **Schema**: Das Fragment wird mithilfe eines XML- oder JSON-Schemas erstellt, das auf AEM Forms hochgeladen wurde. Sie können ein XML- oder JSON-Schema als Formularmodell hochladen oder aus den verfügbaren Schemata wählen. Wenn Sie ein XML-Schema auswählen, können Sie auch ein adaptives Formularfragment erstellen, indem Sie einen „complexType“ im ausgewählten Schema aus der Dropdown-Liste **[!UICONTROL XML-Schema – komplexer Typ]** auswählen. Wenn Sie ein JSON-Schema auswählen, können Sie auch ein adaptives Formularfragment erstellen, indem Sie eine Schemadefinition im ausgewählten Schema aus der Dropdown-Liste **[!UICONTROL JSON-Schemadefinitionen]** auswählen.
   * **Formulardatenmodell**: Gibt an, dass das Fragment mit einem Formulardatenmodell (FDM) erstellt werden soll. Sie können ein adaptives Formularfragment auf Grundlage eines einzelnen Datenmodellobjekts in einem Formulardatenmodell (FDM) erstellen. Erweitern Sie die Dropdown-Liste mit Definitionen für Formulardatenmodelle (FDM). Hier sind sämtliche Datenmodellobjekte im angegebenen Formulardatenmodell (FDM) aufgelistet. Wählen Sie ein Datenmodellobjekt aus der Liste aus.

   ![Formulardatenmodell (FDM)](assets/create-af-3.png)

1. Klicken Sie auf **Erstellen** und dann auf **Öffnen**, um das Fragment mit einer Standardvorlage im Bearbeitungsmodus zu öffnen. Im Bearbeitungsmodus können Sie dem Fragment eine beliebige Komponente des adaptiven Formulars hinzufügen.

<!-- For information about Adaptive Form components, see [Introduction to authoring Adaptive Forms](../../forms/using/introduction-forms-authoring.md). --> Wenn Sie außerdem ein XML-Schema als Formularmodell für Ihr Fragment ausgewählt haben, wird in der Inhaltssuche eine neue Registerkarte mit der Formularmodellhierarchie angezeigt. Sie können dann Formularmodellelemente per Drag-and-Drop auf das Fragment ziehen. <!--The added form-model elements get converted into form components while retaining the original properties from the associated XDP or XSD. -->

Wenn das auf einem Schema oder Formulardatenmodell (FDM) basierende adaptive Formularfragment erstellt ist, werden Formulardatenmodelle (FDM) oder Schemaelemente auf der Registerkarte „Datenquellen“ des Inhalts-Browsers im Editor für adaptive Formulare angezeigt. Sie können per Drag-and-Drop Formularmodellelemente auf das Fragment ziehen. Die hinzugefügten Formularmodellelemente werden in Formularkomponenten konvertiert, während die ursprünglichen Eigenschaften aus dem zugehörigen Schema beibehalten werden.


## Hinzufügen eines Fragments zu einem adaptiven Formular {#insert-a-fragment-in-an-adaptive-form}

So fügen Sie einem adaptiven Formular ein adaptives Formularfragment hinzu:

1. Öffnen Sie das adaptive Formular im Bearbeitungsmodus.
1. Fügen Sie die **Adaptives Formularfragment**-Komponente in das Formular ein.
1. Öffnen Sie das Dialogfeld „Konfiguration“ der Komponente **Adaptives Formularfragment**.
1. Wählen Sie den **Fragmentverweis** auf der Registerkarte **Allgemein** aus. Je nach Formularmodell werden alle für Ihr Formular verfügbaren adaptiven Formularfragmente angezeigt.

1. Wählen Sie ein adaptives Formularfragment auf der Komponente **Adaptives Formularfragment** in Ihrem adaptiven Formular aus.

   ![Wählen Sie die Option „Adaptive Formularfragmente“ aus](/help/forms/assets/adaptive-form-fragment-basic.png)

<!-- 
   >[!NOTE]
   >
   >The Adaptive Form fragment is not enabled for authoring from within the Adaptive Form. Moreover, you cannot use an XSD-based fragment in a JSON-based Adaptive Form and the opposite way. 
-->

Das adaptive Formularfragment wird als Verweis in das adaptive Formular eingefügt und bleibt mit dem eigenständigen adaptiven Formularfragment synchronisiert. Dies bedeutet, dass alle Änderungen am adaptiven Formularfragment über alle Instanzen hinweg gespiegelt werden, in denen das Fragment in adaptive Formulare integriert ist.

<!--### Embed a fragment in Adaptive Form {#embed-a-fragment-in-adaptive-form}

You can choose to embed an Adaptive Form fragment in an Adaptive Form by clicking the ![Embed](assets/Smock_Import_18_N.svg) icon the panel toolbar of the added fragment

The embedded fragment is no longer linked with the standalone fragment. You can edit the components in the embedded fragment from within the Adaptive Form.-->

<!-- 
## Configure fragment appearance {#configure-fragment-appearance}

Any fragment you insert in Adaptive Forms appears as a placeholder image. The placeholder displays titles of up to a maximum of ten child panels in the fragment. You can configure AEM Forms to show the complete fragment instead of the placeholder image.

Perform the following steps to show complete fragments in forms:

1. Go to AEM web console configuration page at https:[*host*]:[*port*]/system/console/configMgr.

1. Search and click **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]** to open it in edit mode.
1. Disable **[!UICONTROL Enable Placeholder in place of Fragment]** checkbox to show complete fragments rather than the placeholder image.

-->

### Verwenden von Fragmenten innerhalb von Fragmenten {#using-fragments-within-fragments}

Sie können verschachtelte adaptive Formularfragmente erstellen, d. h. ein Fragment in einem anderen Fragment hinzufügen, um eine verschachtelte Fragmentstruktur zu erstellen.

### Mehrfaches Verwenden eines Formularfragments in einem adaptiven Formular {#using-form-fragment-mutiple-times-in-af}

Sie können ein schemabasiertes Formularfragment mehrfach in einem adaptiven Formular verwenden, um Daten für jedes Formularfragmentfeld eindeutig zu speichern. Es ist beispielsweise möglich, ein Adressformularfragment zu verwenden, um Adressangaben zum ständigen Wohnsitz, zur Kommunikation und zum aktuellen Wohnsitz in einem Kreditantragsformular zu erfassen.

![Verwenden mehrerer Fragmente in einem adaptiven Formular](/help/forms/assets/using-multiple-fragment-af.gif)

## Unterstützung der automatischen Zuordnung von Fragmenten in einem adaptiven Formular

Wenn Sie ein Fragment für ein adaptives Formular erstellen, das auf einer JSON-Schemadefinition basiert, kann es automatisch in Formularen wiederverwendet werden, die aus demselben Schema erstellt wurden.
Wenn Sie ein Schemaobjekt oder verschachtelte Objekte, das bzw. die der JSON-Schemadefinitionszuordnung eines adaptiven Formularfragments entsprechen, per Drag-and-Drop verschieben, wird das Objekt durch das entsprechende adaptive Formularfragment ersetzt. Anstatt ein Panel mit einzelnen Feldern hinzuzufügen, fügt das Formular das zugeordnete adaptive Formularfragment ein.

![Verschieben eines Fragments per Drag-and-Drop](/help/forms/assets/fragment.png)

Sie können auch per Drag-and-Drop ein gebundenes adaptives Formularfragment aus der adaptiven Formularfragment-Bibliothek in der AEM-Inhaltssuche ziehen und den richtigen Bindungsverweis aus dem Dialogfeld „Komponente bearbeiten“ des Bereichs „Adaptives Formularfragment“ angeben.

## Verwalten von Fragmenten {#manage-fragments}

Sie können über die Benutzeroberfläche von AEM Forms mehrere Vorgänge mit adaptiven Formularfragmenten durchführen.

1. Rufen Sie `https://[hostname]/aem/forms.html` auf.

1. Klicken Sie in der Symbolleiste von AEM Forms auf **Auswählen** und wählen Sie ein adaptives Formularfragment aus. Die Symbolleiste zeigt die folgenden Vorgänge an, die Sie mit dem ausgewählten adaptiven Formularfragment durchführen können.

<table>
 <tbody>
  <tr>
   <td><p><strong>Vorgang</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p>Bearbeiten</p> </td>
   <td><p>Öffnet das ausgewählte adaptive Formularfragment im Bearbeitungsmodus.<br /> <br /> </p> </td>
  </tr>
   <tr>
   <td><p>Vorschau</p> </td>
   <td><p>Enthält Optionen zum Anzeigen einer HTML- oder benutzerdefinierten Vorschau des Fragments durch Zusammenführen von Daten aus einer XML-Datei und dem Fragment. Weitere Informationen finden Sie unter <a>Erstellen einer Vorschau für ein Formular</a>. <br /><br /> </p> </td>
  </tr>
  <tr>
   <td><p>Herunterladen</p> </td>
   <td><p>Lädt das ausgewählte Fragment herunter.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Überprüfung starten/Überprüfung verwalten</p> </td>
   <td><p>Initiieren und Verwalten einer Review des ausgewählten Fragments. Weitere Informationen finden Sie unter <a>Erstellen und Verwalten von Reviews</a>. <br /><br /> </p> </td>
  </tr>
  <tr>
   <td><p>Wörterbuch hinzufügen</p> </td>
   <td><p>Erzeugt ein Wörterbuch zum Lokalisieren des ausgewählten Fragments. Weitere Informationen finden Sie unter <a>Lokalisieren adaptiver Formulare</a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Veröffentlichen/Veröffentlichung rückgängig machen</p> </td>
   <td><p>Veröffentlicht das ausgewählte Fragment bzw. macht die Veröffentlichung rückgängig.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Löschen</p> </td>
   <td><p>Löscht das ausgewählte Fragment.<br /> <br /> </p> </td>
  </tr>
 </tbody>
</table>

## Wichtige Hinweise zum Arbeiten mit Fragmenten {#key-points-to-remember-when-working-with-fragments}

* Stellen Sie sicher, dass der Fragmentname eindeutig ist. Wenn bereits ein anderes Fragment mit demselben Namen vorhanden ist, kann das Fragment nicht erstellt werden.
* Alle Ausdrücke, Skripte oder Stile in einem eigenständigen adaptiven Formularfragment bleiben erhalten, wenn es als Verweis eingefügt oder in ein adaptives Formular eingebettet wird.
* Adaptive Formularfragmente, die als Verweis eingefügt wurden, können nicht in einem adaptiven Formular bearbeitet werden. Ändern Sie zum Bearbeiten das eigenständige adaptive Formularfragment.
* Wenn Sie ein adaptives Formular veröffentlichen, müssen Sie die eigenständigen adaptiven Formularfragmente veröffentlichen, die per Verweis in das adaptive Formular eingefügt wurden.
* Beim erneuten Veröffentlichen eines aktualisierten adaptiven Formularfragments werden die Änderungen in den veröffentlichten Instanzen des adaptiven Formulars, in denen das Fragment verwendet wird, wiedergegeben.
* Adaptive Formulare, die die Überprüfungskomponente enthalten, unterstützen keine anonymen Benutzenden. Außerdem wird nicht empfohlen, die Überprüfungskomponente in einem adaptiven Formularfragment zu verwenden.

## Referenzfragmente {#reference-fragments}

Es sind Referenzfragmente für adaptive Formulare vorhanden, die Sie zum Erstellen von Formularen verwenden können.
<!-- For more information, see [Reference Fragments](../../forms/using/reference-adaptive-form-fragments.md). -->



## Siehe auch {#see-also}

{{see-also}}