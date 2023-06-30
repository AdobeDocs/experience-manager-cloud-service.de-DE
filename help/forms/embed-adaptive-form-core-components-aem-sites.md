---
title: Hinzufügen oder Erstellen eines adaptiven Formulars (Kernkomponenten) auf der AEM Sites-Seite
seo-title: How to add or create an Adaptive Form (Core Components) to an AEM Sites page?
description: Sie können adaptive Formulare (Kernkomponenten) auf einer AEM Sites-Seite verwenden, um ein Formular auszufüllen und zu senden, ohne die AEM Sites-Seiten zu verlassen.
feature: Adaptive Forms
hide: true
hidefromtoc: true
exl-id: 1046231f-787c-4e49-9ba0-e7dd59e41bce
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '2135'
ht-degree: 100%

---

# Erstellen oder Hinzufügen eines adaptiven Formulars mit dem AEM Sites-Editor {#add-an-adaptive-form-to-aem-sites-page}

Sie können adaptive Formulare nahtlos in eine AEM Sites-Seite verfassen oder einbetten, damit Ihre Benutzenden ein Formular ausfüllen und senden können, ohne die Sites-Seite zu verlassen. Es hilft Benutzenden, im Kontext anderer Elemente der Web-Seite zu bleiben und gleichzeitig mit dem Formular zu interagieren.

Sie können eine der folgenden Methoden wählen, um ein adaptives Formular auf einer AEM Sites-Seite zu erstellen oder hinzuzufügen:

* **Erstellen eines adaptiven Formulars mit der Komponente des Containers für adaptive Formulare**: Mit der Komponente [Container für adaptive Formulare](#af-container-component) können Sie digitale Registrierungserlebnisse erstellen, indem Sie adaptive Formularkomponenten direkt im AEM Sites-Editor verwenden. Diese Integration bietet ein nahtloses Erlebnis für AEM Sites-Autoren, die Formulare auf ihren AEM Sites-Seiten erstellen und verwalten möchten.

* **Hinzufügen eines vorhandenen adaptiven Formulars**: Mit der [Adaptive Formulare – Einbettungskomponente (v2)](#embed-existing-af) können Sie ganz einfach ein bereits vorhandenes adaptives Formular zu einer AEM Sites-Seite hinzufügen. Diese Funktion verbessert die Anpassungsfähigkeit und Wiederverwendbarkeit von adaptiven Formularen. Diese Integration bietet eine praktische Möglichkeit für Kunden oder Kundinnen, die bereits erstellte adaptiven Formulare wiederzuverwenden.

* **Verwenden des Assistenten für adaptive Formulare zum Erstellen eines Formulars**: Verwenden Sie die [Adaptive Formulare – Einbettungskomponente (v2)](#embed-new-af), um mithilfe des Assistenten zur Formularerstellung im AEM Sites-Editor ein adaptives Formular zu erstellen. Das Formular wird als externe Entität gespeichert. Sie können dieses Formular auch in anderen Sites-Seiten und eigenständigen Formularen wiederverwenden.

* **Hinzufügen mehrerer adaptiver Formulare auf einer AEM Sites-Seite**: Um mehrere adaptive Formulare zu einer AEM Sites-Seite hinzuzufügen, verwenden Sie die AEM Forms-Container-Komponenten: [Adaptive Formulare – Einbettungskomponente (v2)](#embed-new-af) und [Container für adaptive Formulare](#af-container-component). Wenn Sie innerhalb einer AEM Sites-Seite mehr als ein adaptives Formular als Div hinzufügen müssen, können Sie die Container-Komponente für adaptive Formulare verwenden.

Sie können den Regeleditor verwenden, um das dynamische Verhalten von Komponenten des adaptiven Formulars hinzuzufügen oder zu steuern. Beispielsweise können Sie eine Komponente ein- oder ausblenden. Der Regeleditor ist für nicht-adaptive Formularkomponenten nicht verfügbar. Seien Sie also vorsichtig, wenn Sie nicht-adaptive Formularkomponenten in der AEM Forms-Container-Komponente verwenden.

## Erstellen eines adaptiven Formulars mit der Komponente „Container für adaptive Formulare“ {#af-container-component}

Die Komponente [!UICONTROL Container für adaptive Formulare] ermöglicht das Erstellen von digitalen Registrierungserlebnissen mithilfe von adaptiven Formularkomponenten im AEM Sites-Editor. Sie können ein adaptives Formular per Drag-and-Drop der Formularkomponenten erstellen.

### Voraussetzungen {#prerequisites-af-container}

+++ Aktivieren der Komponente **[!UICONTROL Container für adaptive Formulare]**.

Um die Komponente [!UICONTROL Container für adaptive Formulare] in der Richtlinie der Vorlage zu aktivieren, führen Sie die folgenden Schritte aus:

1. Navigieren Sie zu [!UICONTROL Seiteninformationen] => [!UICONTROL Vorlage bearbeiten]
1. Klicken Sie auf [!UICONTROL Richtlinie] und aktivieren Sie das Kontrollkästchen **[!UICONTROL Container für adaptive Formulare]** unter **[AEM Archetyp-Projektname] – Adaptives Formular**.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

+++

+++ Einbinden von adaptiven Formular-Client-Bibliotheken in die AEM Sites-Seite

Um adaptive Formularkomponenten in einer AEM Sites-Seite zu verwenden, fügen Sie die Clientbibliotheken „Customheaderlibs“ und „Customfooterlibs“ mithilfe des AEM Archetyp/Git-Repository und der Bereitstellungs-Pipeline in die AEM Sites-Seite ein.

1. Öffnen Sie Ihren [AEM Forms-Archetyp oder Ihr geklontes Git-Repository](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de)-Projekt in einem Texteditor. Beispielsweise in Visual Studio Code.
1. Navigieren Sie zu `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml`.
1. Kopieren Sie den Wert von `sling:resourceSuperType`. Der Wert lautet beispielsweise `core/wcm/components/page/v3/page`.

   ![Sling-Ressource](/help/forms/assets/slingresource.png)

1. Erstellen Sie eine ähnliche Struktur am Speicherort `ui.apps/src/main/content/jcr_root/apps` genauso wie `core/wcm/components/page/v3/page`.

   ![Überlagerungsstruktur](/help/forms/assets/overlaystructure.png)

1. Fügen Sie die Dateien `customheaderlibs.html` und `customfooterlibs.html` hinzu.

   ```
   //Customheaderlibs.html
   <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
   </sly> 
   
   //customfooterlibs.html
   <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
   </sly> 
   ```

   Die Datei „customfooterlibs.html“ wird für JavaScript und die Datei „customheaderlibs.html“ für CSS verwendet.

1. [Führen Sie die Pipeline aus](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html?lang=de), um die Änderungen bereitzustellen.

+++

### Erstellen eines adaptiven Formulars mit der Komponente „Container für adaptive Formulare“ {#create-af-using-af-container}


So erstellen Sie ein adaptives Formular mit der Komponente [!UICONTROL Container für adaptive Formulare]:

1. Öffnen Sie die AEM Sites-Seite im Bearbeitungsmodus.
1. Ziehen Sie die Komponente **[!UICONTROL Container für adaptive Formulare]** per Drag-and-Drop aus dem Komponenten-Browser auf die Seite.
1. Erstellen Sie ein adaptives Formular mit den adaptiven Formularkomponenten.
1. Speichern Sie die Einstellungen.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

Ihr Formular ist fertig. Wenn Sie die AEM Sites-Seite veröffentlichen, werden das adaptive Formular und die zugehörigen referenzierten Assets automatisch veröffentlicht.

#### Konfigurieren der Container-Eigenschaften für adaptive Formulare {#configure-additional-settings-container}

Sie können die erweiterten Einstellungen der Komponente [!UICONTROL Container für adaptive Formulare] anpassen. Beispiel:

* Sie können den Vorbefüllungsdienst so konfigurieren, dass ein adaptives Formular mit vorausgefüllten Werten auf der Seite einer Site geladen wird.
* Sie können die Datenmodelleinstellungen konfigurieren, um das adaptive Formular mit einer Datenquelle zu verknüpfen.
* Sie können die Übermittlungsaktionen konfigurieren, um die Daten auf Microsoft® OneDrive oder anderen Datenquellen bei Übermittlung eines Formulars zu senden. Sie können auch eine benutzerdefinierte Übermittlungsaktion für Ihre adaptiven Formulare erstellen und auswählen.

Um die Eigenschaften für die Komponente **[!UICONTROL Container für adaptive Formulare]** einzustellen, klicken Sie auf das ![Settings_icon](/help/forms/assets/Smock_Wrench_18_N.svg) in der Aktionsleiste. Das Dialogfeld **[!UICONTROL Container für adaptive Formulare bearbeiten]** wird geöffnet.

![Dialogfeld „Bearbeiten“](/help/forms/assets/adaptiveformcontainer-editdialog.png)

Im Dialogfeld [!UICONTROL Container für adaptive Formulare bearbeiten] können Sie Folgendes angeben.
* **Registerkarte „Allgemein“**
   * **Vorbefüllungsdienst**: Sie können den Vorbefüllungsdienst verwenden, um Felder eines adaptiven Formulars mit vorhandenen Daten automatisch auszufüllen. Wenn ein Benutzer ein Formular öffnet, werden die Werte für diese Felder vorbefüllt. Informationen zum Vorbefüllungsdienst finden Sie unter [Vorausfüllen von Feldern in adaptiven Formularen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/prepopulate-adaptive-form-fields.html?lang=de#configuring-prefill-service-using-configuration-manager)
   * **Kategorie der Client-Bibliothek**: Geben Sie die [JavaScript-Funktionen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-rules-and-use-expressions-in-an-adaptive-form/rule-editor.html?lang=de#custom-functions) an, die in Ausdrücken verwendet und von adaptiven Formularen unterstützt werden.
* **Datenmodell**: Ein Datenmodell ermöglicht Ihnen die Integration von Entitäten und Diensten aus unterschiedlichen Datenquellen in ein adaptives Formular. Wählen Sie das **[!UICONTROL Formulardatenmodell]**, wenn das adaptive Formular, das Sie erstellen, das Abrufen und Schreiben von Daten aus und in mehrere Datenquellen beinhaltet.
   * **Formulardatenmodell**: Mit einem Formulardatenmodell kann ein adaptives Formular mit unterschiedlichen Datenquellen kommunizieren. Informationen zum Konfigurieren einer Datenquelle finden Sie unter [Konfigurieren von Datenquellen](/help/forms/configure-data-sources.md).
   * **Schema**: Das Schema stellt die Struktur dar, in der Daten vom Back-End-System in Ihrer Organisation produziert oder genutzt werden. Sie können das [Schema mit einem adaptiven Formular verknüpfen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/adaptive-form-json-schema-form-model.html?lang=de) und dem Formular mithilfe der Elemente dieses Schemas dynamische Inhalte hinzufügen. 

     >[!NOTE]
     >
     > Nach dem Konfigurieren des Formulardatenmodells können Sie das verknüpfte Formularmodell nicht ändern. Es ist jedoch möglich, das mit dem Formulardatenmodell verknüpfte Schema zu ändern.

* **Registerkarte „Übermittlung“**

   * **Zu URL umleiten**
      * **Umleitungs-URL/Pfad**: Gibt die URL oder den Pfad an, zu dem ein adaptives Formular nach der Übermittlung umgeleitet wird.

      * **Übermittlungsaktion**: Eine Übermittlungsaktion wird ausgelöst, wenn in einem adaptiven Formular auf die Schaltfläche „Senden“ geklickt wird. Sie können die [Übermittlungsaktion in einem adaptiven Formular konfigurieren](/help/forms/configuring-submit-actions.md). Adaptive Forms stellt die folgenden Übermittlungsaktionen standardmäßig bereit:
         * An REST-Endpunkt übermitteln
         * E-Mail senden
         * Senden mit Formulardatenmodell
         * AEM-Workflow aufrufen
         * An SharePoint senden
         * An OneDrive senden
         * Senden an Azure Blob-Speicher

  Sie können auch die [standardmäßige Übermittlungsaktion erweitern](custom-submit-action-form.md), um Ihre eigene benutzerdefinierte Übermittlungsaktion zu erstellen.

* **Nachricht anzeigen**
   * **Nachrichteninhalt**: Verfassen Sie im Rich-Text-Editor eine Nachricht, die beim Absenden des Formulars angezeigt werden soll. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesnachricht angezeigt werden soll.

## Einbetten eines adaptiven Formulars  {#aem-container-component}

Mit **[!UICONTROL Adaptive Formulare – Einbettungskomponente (V2)]** können Sie entweder ein neues adaptives Formular einbetten oder ein bestehendes adaptives Formular in die Seite der Website einbetten. Die [!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)] ermöglicht es Ihnen:

* [Ein bestehendes adaptives Formular hinzuzufügen](#embed-new-af)

* [Erstellen und Hinzufügen eines neuen adaptiven Formulars](#embed-existing-af)

### Voraussetzungen {#prerequisites}

+++ Aktivieren der **Adaptive Formulare – Einbettungskomponente**.

Um die [!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)] in der Richtlinie der Vorlage zu aktivieren, führen Sie die folgenden Schritte aus:

1. Navigieren Sie zu [!UICONTROL Seiteninformationen] => [!UICONTROL Vorlage bearbeiten]

1. Klicken Sie auf [!UICONTROL Richtlinie] und aktivieren Sie das Kontrollkästchen **[!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)]** unter der Gruppe **[!UICONTROL [AEM-Archetyp-Projektname] – Forms]**.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419369?quality=12&learn=on)

+++

+++ Einbinden von adaptiven Formular-Client-Bibliotheken in die AEM Sites-Seite

Wenn die Option **[!UICONTROL Wenn das Formular die gesamte Breite einer Seite einnimmt]** im Konfigurationsdialogfeld **[!UICONTROL Formular-Container]** ausgewählt ist und **Adaptive Formulare unter Verwendung von Kernkomponenten** verwendet werden, ist es notwendig, die Clientlibs auf der Seite der entsprechenden Site einzubinden.

![Gif überlagern](/help/forms/assets/overlaycorecomponent.gif)

Um adaptive Formularkomponenten auf einer AEM Sites-Seite zu verwenden, fügen Sie die Clientbibliotheken `Customheaderlibs` und `Customfooterlibs` mithilfe des AEM-Archetyp/Git-Repository und der Bereitstellungs-Pipeline in die AEM Sites-Seite ein.

1. Öffnen Sie Ihren [AEM Forms-Archetyp oder Ihr geklontes Git-Repository](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de)-Projekt in einem Texteditor. Beispielsweise in Visual Studio Code.
1. Navigieren Sie zu `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml`.
1. Kopieren Sie den Wert von `sling:resourceSuperType`. Der Wert lautet beispielsweise `core/wcm/components/page/v3/page`.

   ![Sling-Ressource](/help/forms/assets/slingresource.png)

1. Erstellen Sie eine ähnliche Struktur am Speicherort `ui.apps/src/main/content/jcr_root/apps` genauso wie `core/wcm/components/page/v3/page`.

   ![Überlagerungsstruktur](/help/forms/assets/overlaystructure.png)

1. Fügen Sie die Dateien `customheaderlibs.html` und `customfooterlibs.html` hinzu.

   ```
   //Customheaderlibs.html
   <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html"
       data-sly-use.form="com.adobe.cq.forms.core.components.models.aemform.AEMForm">
       <sly data-sly-test="${form.formVersion=='2.1' && !wcmmode.edit}" data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
   </sly>
   
   //customfooterlibs.html
   <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html"
     data-sly-use.form="com.adobe.cq.forms.core.components.models.aemform.AEMForm">
     <sly data-sly-test="${form.formVersion=='2.1' && !wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
   </sly>
   ```

   `customfooterlibs.html` wird für JavaScript verwendet und `customheaderlibs.html` für CSS.

1. [Führen Sie die Pipeline aus](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html?lang=de), um die Änderungen bereitzustellen.

+++

### Hinzufügen eines vorhandenen adaptiven Formulars zur AEM Sites-Seite {#embed-existing-af}

1. Öffnen Sie die AEM Sites-Seite im Bearbeitungsmodus.
1. Ziehen Sie die [!UICONTROL Adaptive Formulare – Einbettungskomponente] per Drag-and-Drop aus dem Komponenten-Browser auf die Seite.
1. Tippen Sie auf die [!UICONTROL Adaptive Formulare – Einbettungskomponente] auf der Sites-Seite und tippen Sie auf ![Settings_icon](/help/forms/assets/Smock_Wrench_18_N.svg) in der Aktionsleiste. Das Dialogfeld **[!UICONTROL Bearbeiten der „Adaptive Formulare – Einbettungskomponente“]** wird geöffnet.
1. Wählen Sie das adaptive Formular aus, das Sie in den [!UICONTROL Asset-Pfad] einbetten möchten.
1. Speichern Sie die Einstellungen. Das adaptive Formular ist jetzt in der Seite eingebettet.

>[!VIDEO](https://video.tv.adobe.com/v/3419368?quality=12&learn=on)



### Erstellen und Hinzufügen eines neuen adaptiven Formulars zur AEM Sites-Seite {#embed-new-af}

1. Öffnen Sie die AEM Sites-Seite im Bearbeitungsmodus.
1. Ziehen Sie die [!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)] per Drag-and-Drop aus dem Komponenten-Browser auf die Seite.
1. Klicken Sie auf das **Plus**-Symbol, und Sie werden zum Assistenten für die Formularerstellung weitergeleitet.

   ![Adaptive Formulare – Einbettungskomponente](/help/forms/assets/aemformcontainer.png)

1. Erstellen Sie ein neues adaptives Formular aus dem Assistenten für die [!UICONTROL Formularerstellung].
1. Der [!UICONTROL Asset-Pfad] enthält bereits den Pfad eines erstellten adaptiven Formulars
1. Speichern Sie die Einstellungen. Das adaptive Formular ist jetzt in der Seite eingebettet.

>[!VIDEO](https://video.tv.adobe.com/v/3419366/adaptive-form-aem-forms?quality=12&learn=on)

#### Konfigurieren Sie die Eigenschaften der „Adaptive Formulare – Einbettungskomponente (v2)“ {#configure-adaptive-form-embed}

Sie können die erweiterten Einstellungen der [!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)] anpassen. Im Dialogfeld [!UICONTROL Bearbeiten der „Adaptive Formulare – Einbettungskomponente (v2)“] können Sie Folgendes angeben.

* **Asset-Pfad**: Klicken Sie auf „Durchsuchen“ und wählen Sie das einzubettende adaptive Formular aus. Es wird automatisch ausgefüllt, wenn Sie es über den Assets-Browser eingefügt haben.
* **Nach dem Senden**: Wählen Sie die Aktion aus, die bei der Formularübermittlung ausgelöst werden soll. Sie können auswählen, dass eine Dankesnachricht oder eine Dankeseite angezeigt werden soll.
   * **Dankesnachricht anzeigen**: Verfassen Sie im Rich-Text-Editor eine Nachricht, die beim Absenden des Formulars angezeigt werden soll. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesnachricht angezeigt werden soll.
   * **Dankesseite anzeigen**: Suchen und wählen Sie die Seite aus, die bei Übermittlung eines Formulars angezeigt wird. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesseite angezeigt werden soll.
   * **Umleiten zur Dankeseite**: Aktivieren Sie die Option, um die Seite mit dem eingebetteten adaptiven Formular durch die Dankeseite zu ersetzen. Andernfalls ersetzt die Dankesseite das adaptive Formular in der [!UICONTROL Adaptive Formulare – Einbettungskomponente], ohne die darunter liegenden Seiten zu aktualisieren. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankeseite angezeigt werden soll.
* **Seitensprache verwenden**: Verwenden Sie das Gebietsschema der AEM Sites-Seite anstelle des Gebietsschemas des adaptiven Formulars.
* **Fokus auf Formular festlegen**: Wählen Sie diese Option aus, um den Fokus auf das erste Feld des adaptiven Formulars zu legen.
* **Formular deckt die gesamte Breite des Rahmens ab**: Wenn diese Option aktiviert ist, wird iframe nicht zum Rendern des Formulars verwendet.
* **Höhe**: Geben Sie die Höhe des Containers an. Lassen Sie es leer, um die Größe des Containers automatisch zu anzupassen.
* **CSS-Client-Bibliothek**: Geben Sie den Pfad zu einer CSS-Client-Bibliothek an.

### Veröffentlichen hinzugefügter adaptiver Formulare mithilfe der „Adaptive Formulare – Einbettungskomponente (v2)“  {#publish-embedded-adaptive-form}

Beachten Sie die folgenden Szenarien für die Veröffentlichung des hinzugefügten adaptiven Formulars unter Verwendung der **[!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)]**:

* Wenn Sie eine AEM Sites-Seite zum ersten Mal veröffentlichen, werden die der Sites-Seite hinzugefügten Formulare automatisch veröffentlicht.
* Wenn Sie ein adaptives Formular ändern, das zu einer bereits veröffentlichten Sites-Seite hinzugefügt wurde, veröffentlichen Sie die entsprechenden adaptiven Formulare manuell.
* Wenn Sie eine Sites-Seite und die entsprechenden adaptiven Formulare ändern, veröffentlichen Sie die Sites-Seite und alle adaptiven Formulare, die zur Sites-Seite hinzugefügt wurden, erneut.

### Ändern hinzugefügter adaptiver Formulare mithilfe der „Adaptive Formulare – Einbettungskomponente (v2)“  {#modifying-embedded-adaptive-form}

Um eine Konfiguration oder Eigenschaft eines adaptiven Formulars zu ändern, führen Sie einen der folgenden Schritte aus:

* Öffnen Sie das Originalformular in einem adaptiven Formular im entsprechenden Editor und ändern Sie es.
* Tippen Sie von der Sites-Seite aus im Bearbeitungsmodus auf das adaptive Formular und tippen Sie dann auf **[!UICONTROL In neuem Fenster bearbeiten]**. Das ursprüngliche Formular wird im Bearbeitungsmodus geöffnet, sodass Sie es bearbeiten können.

## Änderung des Layouts eines adaptiven Formulars, das zu einer AEM Sites-Seite hinzugefügt wurde {#change-layout-af-aem-sites-page}

Auf der AEM Sites-Seite können Sie mit dem [Layout-Modus](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/features/responsive-layout.html?lang=de#defining-layouts-layout-mode) die Größe eines adaptiven Formulars ändern, das erstellt oder zu einer AEM Sites-Seite hinzugefügt wurde.

![AF-Layout-Support](/help/forms/assets/afsite-layoutsupport.gif)

Die AEM Sites-Seite enthält einen Verweis auf das adaptive Formular. Wenn Sie eine AEM Sites-Seite übersetzen, werden ein adaptives Formular und die damit verknüpften referenzierten Elemente mithilfe der [Übersetzungsprojekte](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/reusing-content/translation/managing-projects.html?lang=de#adding-pages-assets-to-a-translation-job) automatisch in andere Sprachen übersetzt.

## Best Practices {#best-practices}

* Die Kopf- und Fußzeile im Originalformular sind nicht im eingebetteten Formular enthalten.
* Benutzerentwürfe und -übermittlungen von eingebetteten Formularen werden unterstützt und sind auf den Registerkarten „Entwürfe“und „Gesendete Formulare“ im Formularportal sichtbar.