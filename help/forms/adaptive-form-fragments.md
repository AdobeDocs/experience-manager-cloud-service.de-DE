---
title: Wie werden adaptive Formularfragmente erstellt und verwendet?
description: Ein Formularfragment ist eine modulare und wiederverwendbare Komponente eines Formulars. Erfahren Sie, wie Sie Formularfragmente erstellen und sie formularübergreifend wiederverwenden können, um eine effiziente Formularanordnung zu gewährleisten.
uuid: bb4830b5-82a0-4026-9dae-542daed10e6f
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
feature: Adaptive Forms, Foundation Components
discoiquuid: 1a32eb24-db3b-4fad-b1c7-6326b5af4e5e
exl-id: e4d8bcb9-ce1f-425e-b35c-d0a79fa771f3
role: User, Developer
source-git-commit: bcd3a2a813833d7c1705e45829bcf769645cd154
workflow-type: tm+mt
source-wordcount: '2150'
ht-degree: 100%

---

# Erstellen und Verwenden adaptiver Formularfragmente in einem adaptiven Formular  {#adaptive-form-fragments}


| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service (Foundation-Komponenten) | Dieser Artikel |
| AEM as a Cloud Service (Kernkomponenten) | [Hier klicken](/help/forms/adaptive-form-fragments-core-components.md) |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/adaptive-form-fragments.html?lang=de) |

Zwar wird jedes Formular für einen bestimmten Zweck entwickelt, doch enthalten die meisten Formulare einige gängige Elemente (z. B. für persönliche Angaben wie Name und Anschrift, Angaben zu Familienstand, Einkommen usw.). Formularentwicklerinnen und -entwickler müssen diese gängigen Segmente jedes Mal erstellen, wenn ein neues Formular erstellt wird. Adaptive Formulare bieten einen praktischen Mechanismus, mit dem Formularsegmente wie ein Bedienfeld oder eine Gruppe von Feldern nur einmal erstellt und dann in adaptiven Formularen wiederverwendet werden können. Diese wiederverwendbaren, unabhängigen Segmente werden als adaptive Formularfragmente bezeichnet.


## Erstellen eines Fragments {#create-a-fragment}

Sie können adaptive Formularfragmente von Grund auf neu erstellen oder einen Bereich in einem vorhandenen adaptiven Formular als Fragment speichern.

### Neuerstellen von Fragmenten {#create-fragment-from-scratch}

1. Melden Sie sich bei der Autoreninstanz von [!DNL AEM Forms] unter https://[*Hostname*]:[*Port*]/aem/forms.html an.
1. Klicken Sie auf **Erstellen > Adaptives Formularfragment**.
1. Geben Sie Titel, Name, Beschreibung und Tags für das Fragment an.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Sie einen eindeutigen Namen für das Fragment angeben. Wenn bereits ein anderes Fragment mit demselben Namen vorhanden ist, kann das Fragment nicht erstellt werden.

1. Klicken Sie, um die Registerkarte **Formularmodell** zu öffnen. Wählen Sie dann aus der Dropdown-Liste **Auswählen** eines der folgenden Fragmentmodelle:

   * **Keine**: Gibt an, dass das Fragment von Grund auf ohne Formularmodell erstellt werden soll.

     >[!NOTE]
     >
     > In Adaptive Forms können Sie ein einzelnes Formularfragment (basierend auf Kernkomponenten) mehrmals in einem Formular verwenden. Es unterstützt sowohl auf nichts basierende als auch schemabasierte Formularfragmente.

   * **Formularvorlage**: Das Fragment wird mithilfe einer XDP-Vorlage erstellt, die in [!DNL AEM Forms] hochgeladen wurde. Wählen Sie die entsprechende XDP-Vorlage als Formularmodell für das Fragment aus.

   ![Erstellen eines adaptiven Formulars mit einer Formularvorlage als Modell](assets/form-template-model.png)

   Die Teilformulare, die als Fragmente in der ausgewählten Vorlage markiert sind, werden ebenfalls angezeigt. Sie können ein Teilformular für ein adaptives Formularfragment aus der Dropdown-Liste wählen.

   ![Auswählen von Teilformularen aus der angegebenen Formularvorlage](assets/fragment-subform.png)

   Außerdem können Sie ein adaptives Formularfragment aus Teilformularen erstellen, die nicht als Fragmente in der Formularvorlage markiert sind, indem Sie den SOM-Ausdruck für das Teilformular in der Dropdown-Liste angeben.

   * **XML-Schema**: Das Fragment wird mithilfe eines XML-Schemas erstellt, das in [!DNL AEM Forms] hochgeladen wurde. Sie können ein XML-Schema als Formularmodell hochladen oder aus den verfügbaren Schemas wählen.

   ![Erstellen eines adaptiven Formularfragments anhand eines XML-Schemas als Modell](assets/xml-schema-model.png)

   Sie können ein adaptives Formularfragment auch erstellen, indem Sie einen „complexType“ im ausgewählten Schema aus der Dropdown-Liste wählen.

   ![Wählen Sie einen komplexen Typ aus dem angegebenen XML-Schema-Modell.](assets/complex-type.png)

1. Klicken Sie auf **Erstellen** und dann auf **Öffnen**, um das Fragment mit einer Standardvorlage im Bearbeitungsmodus zu öffnen.

Im Bearbeitungsmodus können Sie eine beliebige adaptive Formularkomponente aus dem AEM Sidekick auf das Fragment ziehen. <!-- For information about Adaptive Form components, see Introduction to authoring Adaptive Forms. -->

Wenn Sie außerdem ein XML-Schema oder eine XDP-Formularvorlage als Formularmodell für Ihr Fragment ausgewählt haben, wird in der Inhaltssuche eine neue Registerkarte mit der Formularmodellhierarchie angezeigt. Sie können dann Formularmodellelemente auf das Fragment ziehen. Die hinzugefügten Formularmodellelemente werden in Formularkomponenten konvertiert, wobei die ursprünglichen Eigenschaften des verbundenen XDP oder XSD beibehalten werden.

### Bereich als Fragment speichern {#save-panel-as-a-fragment}

1. Öffnen Sie ein adaptives Formular, das das Bedienfeld enthält, das Sie als adaptives Formularfragment speichern möchten.
1. Klicken Sie in der Symbolleiste des Bedienfelds auf **[!UICONTROL Als Fragment speichern]**. Das Dialogfeld „Als Fragment speichern“ wird geöffnet.

   >[!NOTE]
   >
   >Wenn das Panel, das Sie gerade als Fragment speichern, untergeordnete Panels umfasst, sind diese auch Teil des resultierenden Fragments.

1. Geben Sie im Dialogfeld für die Fragmenterstellung die folgenden Informationen an:

   * **Name**: Name des Fragments. Der Standardwert ist der Elementname des Panels. Dies ist ein Pflichtfeld.

     >[!NOTE]
     >
     >Stellen Sie sicher, dass Sie einen eindeutigen Namen für das Fragment angeben. Wenn bereits ein anderes Fragment mit demselben Namen vorhanden ist, kann das Fragment nicht erstellt werden.

   * **Titel**: Titel des Formulars. Der Standardwert ist der Titel des Bedienfelds.

   * **Beschreibung**: Beschreibung des Fragments.

   * **Tags**: Kennzeichnet Metadaten für das Fragment.

   * **Zielpfad**: Pfad zum Repository, in dem das Fragment gespeichert wird. Wenn Sie keinen Pfad angeben, wird ein Knoten mit dem Namen des Fragments neben dem Knoten erstellt, der das adaptive Formular enthält. Das Fragment wird in diesem Knoten gespeichert.

   * **Formularmodell**: Je nach Formularmodell für das adaptive Formular wird das **XML-Schema**, die **Formularvorlage** oder **Ohne** angezeigt. Dies ist ein Feld, das nicht bearbeitet werden kann.

   * **Fragmentmodellstamm**: Diese Option wird nur in XSD-basierten adaptiven Formularen angezeigt. Sie gibt den Stamm für das Fragmentmodell an. Sie können auch **/** oder den komplexen XSD-Typ aus der Dropdown-Liste auswählen. Sie können das Fragment nur in einem anderen adaptiven Formular wiederverwenden, wenn Sie den komplexen Typ als Fragmentmodellstamm auswählen.
Wenn Sie **/** als Fragmentmodellstamm auswählen, wird die vollständige XSD-Struktur vom Stamm in der Registerkarte für das Datenmodell des adaptiven Formulars angezeigt. Für den Fragmentmodellstamm eines komplexen Typs werden lediglich die untergeordneten Elemente des ausgewählten komplexen Typs in der Registerkarte des Datenmodells des adaptiven Formulars angezeigt.

   * **XSD-Ref**: Diese Option ist nur in XSD-basierten adaptiven Formularen verfügbar. Sie zeigt den Ort des XML-Schemas an.

   * **XDP-Ref**: Diese Option ist nur in XDP-basierten adaptiven Formularen verfügbar. Es wird der Speicherort der XDP-Vorlage angezeigt.

   ![save-fragment](assets/save-fragment.png)

   Dialogfeld „Als Fragment speichern“.

1. Klicken Sie auf **OK**.

   Das Bedienfeld wird am angegebenen oder am Standardspeicherort im Repository gespeichert. In einem adaptiven Formular wird das Fenster durch einen Schnappschuss des Fragments ersetzt. Wie unten gezeigt, werden das Bedienfeld „Allgemeine Informationen“ und seine untergeordneten Bedienfelder, „Persönliche Informationen“ und „Adresse“, als Fragment gespeichert.

   Um das Fragment zu bearbeiten, klicken Sie in der Symbolleiste des Bedienfelds auf das Symbol **[!UICONTROL Element bearbeiten]**. Das Fragment wird auf einer neuen Registerkarte oder in einem neuen Fenster im Bearbeitungsmodus geöffnet.

   ![Bearbeiten von Fragmenten](assets/edit-fragment.png)

## Arbeiten mit Fragmenten {#working-with-fragments}

### Konfigurieren des Erscheinungsbildes von Fragmenten {#configure-fragment-appearance}

Alle Fragmente, die Sie in adaptive Formulare einfügen, werden als Platzhalterbild angezeigt. Der Platzhalter zeigt die Titel von bis zu maximal zehn untergeordneten Bedienfeldern im Fragment an. Sie können [!DNL AEM Forms] so konfigurieren, dass das vollständige Fragment anstelle des Platzhalterbildes angezeigt wird.

Führen Sie die folgenden Schritte aus, um vollständige Fragmente in Formularen anzuzeigen:

1. Wechseln Sie zur Seite zur Konfiguration der AEM-Web-Konsole unter https://[*Host*]:[*Port*]/system/console/configMgr.

1. Suchen Sie nach **[!UICONTROL Konfigurations-Service für adaptive Formulare]** und klicken Sie darauf, um die Funktion im Bearbeitungsmodus zu öffnen.
1. Deaktivieren Sie das Kontrollkästchen **[!UICONTROL Platzhalter anstelle des Fragments aktivieren]**, um vollständige Fragmente anstelle des Platzhalterbildes anzuzeigen.

### Einfügen eines Fragments in ein adaptives Formular {#insert-a-fragment-in-an-adaptive-form}

Die adaptiven Formularfragmente, die Sie erstellen, werden auf der Registerkarte „Adaptive Formularfragmente“ der AEM-Inhaltssuche angezeigt. So fügen Sie ein adaptives Formularfragment in ein adaptives Formular ein:

1. Öffnen Sie das adaptive Formular, in das Sie ein adaptives Formularfragment einfügen möchten, im Bearbeitungsmodus.
1. Klicken Sie in der Seitenleiste auf **Assets** ![assets-browser](assets/assets-browser.png). Wählen Sie im Assets-Browser **Adaptive Formularfragmente** aus der Dropdown-Liste.

   Sie können auch alle adaptiven Formularfragmente anzeigen oder die Fragmente nach ihrem Formularmodell (Formularvorlage, XML-Schema oder Allgemein) filtern.

1. Ziehen Sie ein adaptives Formularfragment auf das adaptive Formular.

   >[!NOTE]
   >
   >Das adaptive Formularfragment kann nicht aus dem adaptiven Formular heraus erstellt werden. Darüber hinaus ist es nicht möglich, ein XSD-basiertes Fragment in einem JSON-basierten adaptiven Formular oder ein JSON-basiertes Fragment in einem XSD-basierten Formular zu verwenden.

Das adaptive Formularfragment wird als Verweis in das adaptive Formular eingefügt und mit dem eigenständigen adaptiven Formularfragment synchronisiert. Das bedeutet, dass Änderungen, die Sie am adaptiven Formularfragment vornehmen, in allen adaptiven Formularen, in denen das Fragment verwendet wird, widergespiegelt werden.

### Einbetten eines Fragments in ein adaptives Formular {#embed-a-fragment-in-adaptive-form}

Sie können ein adaptives Formularfragment in ein adaptives Formular einbetten, indem Sie in der Symbolleiste des hinzugefügten Fragments auf die Schaltfläche **Element einbetten: &lt;*fragmentName*>** klicken (siehe Beispielbild unten).

![Einbetten eines Formularfragments in ein adaptives Formular](assets/embed-fragment.png)

>[!NOTE]
>
>Das eingebettete Fragment ist nicht mehr mit dem eigenständigen Fragment verknüpft. Die Komponenten im eingebetteten Fragment können aus dem adaptiven Formular heraus bearbeitet werden.

### Verwenden von Fragmenten innerhalb von Fragmenten {#using-fragments-within-fragments}

Sie können verschachtelte adaptive Formularfragmente erstellen, d. h. ein Fragment in ein anderes Fragment ziehen, um eine verschachtelte Fragmentstruktur zu erstellen.

### Ändern von Fragmenten {#change-fragments}

Sie können ein adaptives Formularfragment ändern oder durch ein anderes ersetzen, indem Sie die Eigenschaft **Fragment-Asset auswählen** im Dialogfeld „Komponente bearbeiten“ eines adaptiven Formularfragments verwenden.

### Mehrfaches Verwenden eines Formularfragments in einem adaptiven Formular {#using-form-fragment-mutiple-times-in-af}

Sie können ein schemabasiertes Formularfragment mehrfach in einem adaptiven Formular verwenden, um Daten für jedes Formularfragmentfeld eindeutig zu speichern. Es ist beispielsweise möglich, ein Adressformularfragment zu verwenden, um Adressangaben zum ständigen Wohnsitz, zur Kommunikation und zum aktuellen Wohnsitz in einem Kreditantragsformular zu erfassen.

![Verwenden mehrerer Fragmente in einem adaptiven Formular](/help/forms/assets/using-multiple-fragment-af.gif)

>[!NOTE]
>
> Wenn Sie nicht-basierte Formularfragmente mehrfach in einem adaptiven Formular verwenden, tritt ein Problem bei der Datensynchronisierung zwischen den Feldern der Fragmente auf. Sie können eine [Kernkomponente (basierend auf Formularfragmenten)](/help/forms/adaptive-form-fragments-core-components.md), die nicht an ein Formulardatenmodell (FDM) gebunden ist, mehrfach in einem Formular verwenden, ohne dass Probleme mit der Datensynchronisierung auftreten.

## Automatisches Zuordnen von Fragmenten für die Datenbindung {#auto-mapping-of-fragments-for-data-binding}

Wenn Sie ein adaptives Formularfragment mithilfe einer XFA-Formularvorlage oder eines komplexen XSD-Typs erstellen und es auf ein adaptives Formular ziehen, wird das XFA-Fragment bzw. der komplexe XSD-Typ automatisch durch das entsprechende adaptive Formularfragment ersetzt, dessen Fragmentmodellstamm dem XFA-Fragment bzw. komplexen XSD-Typ zugeordnet ist.

Das Fragment-Asset und dessen Bindungen können im Dialogfeld „Komponente bearbeiten“ geändert werden.

>[!NOTE]
>
>Sie können auch ein gebundenes adaptives Formularfragment aus der adaptiven Formularfragment-Bibliothek in der AEM-Inhaltssuche ziehen und den richtigen Bindungsverweis aus dem Dialogfeld „Komponente bearbeiten“ des Bereichs „Adaptives Formularfragment“ angeben.

## Verwalten von Fragmenten {#manage-fragments}

Sie können über die Benutzeroberfläche von [!DNL AEM Forms] mehrere Vorgänge mit adaptiven Formularfragmenten durchführen.

1. Rufen Sie `https://[hostname]:'port'/aem/forms.html` auf.

1. Klicken Sie in der Symbolleiste von [!DNL AEM Forms] auf **Auswählen** und wählen Sie ein adaptives Formularfragment aus. Die Symbolleiste enthält die folgenden Vorgänge, die Sie mit dem ausgewählten adaptiven Formularfragment durchführen können.

<table>
 <tbody>
  <tr>
   <td><p><strong>Vorgang</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p>Öffnen</p> </td>
   <td><p>Öffnet das adaptive Formularfragment im Bearbeitungsmodus.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Eigenschaften anzeigen</p> </td>
   <td><p>Öffnet das Bedienfeld „Eigenschaften“. Im Bedienfeld „Eigenschaften“ können Sie Eigenschaften anzeigen und bearbeiten, eine Vorschau erstellen und ein Miniaturbild für das ausgewählte Fragment hochladen. Weitere Informationen finden Sie unter <a href="manage-form-metadata.md" target="_blank">Verwalten von Metadaten</a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Kopieren</p> </td>
   <td><p>Kopiert das ausgewählte Fragment. Die Schaltfläche „Einfügen“ wird in der Symbolleiste angezeigt.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Download</p> </td>
   <td><p>Lädt das ausgewählte Fragment herunter.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Vorschau</p> </td>
   <td><p>Enthält Optionen zum Anzeigen einer HTML- oder benutzerdefinierten Vorschau des Fragments durch Zusammenführen von Daten aus einer XML-Datei und dem Fragment. <!-- For more information, see <a href="previewing-forms.md" target="_blank">Previewing a form</a>.<br /> <br /> --></p> </td>
  </tr>
  <tr>
   <td><p>Review starten/verwalten</p> </td>
   <td><p>Initiieren und Verwalten einer Review des ausgewählten Fragments. <!-- For more information, see <a href="create-reviews-forms.md" target="_blank">Creating and managing reviews</a>.<br /> <br /> </p> --> </td>
  </tr>
  <tr>
   <td><p>Wörterbuch erstellen</p> </td>
   <td><p>Erzeugt ein Wörterbuch zum Lokalisieren des ausgewählten Fragments. <!-- For more information, see <a href="lazy-loading-adaptive-forms.md" target="_blank">Localizing Adaptive Forms</a>.<br /> <br /> --> </p> </td>
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

## Lokalisieren von adaptiven Formularen, die Fragmente enthalten {#localizing-adaptive-form-containing-fragments}

Zum Lokalisieren eines adaptiven Formulars, das adaptive Formularfragmente enthält, müssen die Fragmente und das Formular separat lokalisiert werden. Auf diese Weise muss ein Fragment nur einmal lokalisiert werden und kann dann später in mehreren adaptiven Formularen wiederverwendet werden.

>[!NOTE]
>
>Die Lokalisierungsschlüssel im Fragment werden nicht in der XLIFF-Datei für ein adaptives Formular angezeigt.

## Wichtige Hinweise zum Arbeiten mit Fragmenten {#key-points-to-remember-when-working-with-fragments}

* Stellen Sie sicher, dass der Fragmentname eindeutig ist. Das Fragment kann nicht erstellt werden, wenn ein vorhandenes Fragment mit demselben Namen vorhanden ist.
* Wenn Sie in einem XDP-basierten adaptiven Formular ein Bedienfeld, das ein anderes XDP-Fragment enthält, als Fragment speichern, wird das daraus resultierende Fragment automatisch an das untergeordnete XDP-Fragment gebunden. Bei XSD-basierten adaptiven Formularen wird das resultierende Fragment an den Schemastamm gebunden.
* Wenn Sie ein adaptives Formularfragment erstellen, wird ein Fragmentknoten erstellt, der dem Knoten „guideContainer“ für ein adaptives Formular in CRXDe Lite ähnelt.
* Ein Fragment, das ein anderes Formulardatenmodell (FDM) verwendet, wird in einem adaptiven Formular nicht unterstützt. Zum Beispiel wird in einem XSD-basierten adaptiven Formular ein XDP-basiertes Fragment nicht unterstützt und umgekehrt.
* Adaptive Formularfragmente sind in der AEM-Inhaltssuche auf der Registerkarte „Adaptive Formularfragmente“ verfügbar.
* Alle Ausdrücke, Skripts oder Stile in einem eigenständigen adaptiven Formularfragment bleiben erhalten, wenn es als Verweis eingefügt oder in ein adaptives Formular eingebettet wird.
* Adaptive Formularfragmente, die als Verweis eingefügt wurden, können nicht in einem adaptiven Formular bearbeitet werden. Sie bearbeiten stattdessen entweder das eigenständige adaptive Formularfragment oder betten das Fragment in das adaptive Formular ein.
* Wenn Sie ein adaptives Formular veröffentlichen, müssen Sie die eigenständigen adaptiven Formularfragmente veröffentlichen, die per Verweis in das adaptive Formular eingefügt wurden.
* Beim erneuten Veröffentlichen eines aktualisierten adaptiven Formularfragments werden die Änderungen in den veröffentlichten Instanzen des adaptiven Formulars, in denen das Fragment verwendet wird, wiedergegeben.
* Adaptive Formulare, die die Verify-Komponente enthalten, unterstützen keine anonymen Benutzer. Außerdem wird nicht empfohlen, die Verify-Komponente in einem adaptiven Formularfragment zu verwenden.
* (**Nur Mac**) Um sicherzustellen, dass die Formularfragmentfunktionalität in allen Szenarien einwandfrei funktioniert, fügen Sie der Datei „/private/etc/hosts“ den folgenden Eintrag hinzu:
  `127.0.0.1 <Host machine>` **Host-Computer**: Der Apple Mac-Computer, auf dem [!DNL AEM Forms] bereitgestellt wird.

<!--
## Reference Fragments {#reference-fragments}

Reference Adaptive Form Fragments that you can use to create your form are available. For more information, see [Reference Fragments](reference-adaptive-form-fragments.md).
-->

>[!MORELIKETHIS]
>
>* [Adaptive Formularfragmente in Kernkomponenten](/help/forms/adaptive-form-fragments-core-components.md)
