---
title: Hinzufügen oder Erstellen eines adaptiven Formulars (Kernkomponenten) auf der AEM Sites-Seite
seo-title: How to add or create an Adaptive Form (Core Components) to an AEM Sites page?
description: Sie können das adaptive Formular (Kernkomponenten) auf einer AEM Sites-Seite verwenden, um ein Formular auszufüllen und zu senden, ohne die AEM Sites-Seiten zu verlassen.
feature: Adaptive Forms
hide: true
hidefromtoc: true
exl-id: 1046231f-787c-4e49-9ba0-e7dd59e41bce
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '2135'
ht-degree: 14%

---

# Erstellen oder Hinzufügen eines adaptiven Formulars mit dem AEM Sites Editor {#add-an-adaptive-form-to-aem-sites-page}

Sie können Adaptive Forms nahtlos in eine AEM Sites-Seite verfassen oder einbetten, damit Ihre Benutzer ein Formular ausfüllen und senden können, ohne die Sites-Seite verlassen zu müssen. Dies hilft Benutzern, im Kontext anderer Elemente der Webseite zu bleiben und gleichzeitig mit dem Formular zu interagieren.

Sie können eine der folgenden Methoden auswählen, um ein adaptives Formular zu einer AEM Sites-Seite hinzuzufügen:

* **Erstellen eines adaptiven Formulars mit der Komponente Adaptiver Forms-Container**: Die [Container für adaptive Formulare](#af-container-component) -Komponente können Sie digitale Registrierungserlebnisse erstellen, indem Sie Adaptive Forms-Komponenten direkt im AEM Sites-Editor verwenden. Diese Integration bietet ein nahtloses Erlebnis für AEM Sites-Autoren, die Formulare auf ihren AEM Sites-Seiten erstellen und verwalten möchten.

* **Hinzufügen eines vorhandenen adaptiven Formulars**: Die [Adaptive Forms - Embed(v2)](#embed-existing-af) -Komponente können Sie in AEM Sites einfach ein bereits vorhandenes adaptives Formular zu einer Seite hinzufügen. Diese Funktion verbessert die Anpassungsfähigkeit und Wiederverwendbarkeit von Adaptive Forms. Diese Integration bietet eine praktische Möglichkeit für Kunden, die bereits erstellte adaptive Forms wiederzuverwenden.

* **Verwenden des Adaptiven Forms-Assistenten zum Erstellen eines Formulars**: Verwenden Sie die [Adaptive Forms - Embed(v2)](#embed-new-af) -Komponente, um mithilfe des Assistenten zur Formularerstellung im AEM Sites-Editor ein adaptives Formular zu erstellen. Das Formular wird als externe Entität gespeichert. Sie können dieses Formular auch in anderen Sites-Seiten und eigenständigen Formularen wiederverwenden.

* **Hinzufügen mehrerer adaptiver Forms auf einer AEM Sites-Seite**: Um mehrere adaptive Forms zu einer AEM Sites-Seite hinzuzufügen, verwenden Sie die AEM Forms-Container-Komponenten - [Adaptive Forms - Embed(v2)](#embed-new-af) und [Container für adaptive Formulare](#af-container-component). Wenn Sie innerhalb einer AEM Sites-Seite mehr als ein adaptives Formular als Div hinzufügen müssen, können Sie die Container-Komponente für adaptive Formulare verwenden.

Sie können den Regeleditor verwenden, um das dynamische Verhalten von Komponenten des adaptiven Formulars hinzuzufügen oder zu steuern. Beispielsweise können Sie eine Komponente ein- oder ausblenden. Der Regeleditor ist nicht für Komponenten ohne adaptives Formular verfügbar. Verwenden Sie daher Ihre Sorgfalt bei der Verwendung von nicht adaptiven Formularkomponenten in der AEM Forms-Container-Komponente.

## Erstellen eines adaptiven Formulars mit der Komponente Adaptiver Forms-Container {#af-container-component}

Die [!UICONTROL Container für adaptive Formulare] ermöglicht das Erstellen von digitalen Registrierungserlebnissen mithilfe von Adaptive Forms-Komponenten im AEM Sites-Editor. Sie können ein adaptives Formular durch Ziehen und Ablegen der Formularkomponenten erstellen.

### Voraussetzungen {#prerequisites-af-container}

+++ Aktivieren **[!UICONTROL Adaptiver Forms-Container]** -Komponente.

Aktivieren [!UICONTROL Adaptiver Forms-Container] -Komponente in der Richtlinie der Vorlage ausführen, führen Sie die folgenden Schritte aus:

1. Navigieren Sie zu [!UICONTROL Seiteninformationen] > [!UICONTROL Vorlage bearbeiten]
1. Klicken Sie auf [!UICONTROL Politik] und wählen Sie die **[!UICONTROL Adaptiver Forms-Container]**  Kontrollkästchen unter dem **[AEM Archetyp Projektname] - Adaptives Formular**.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

+++

+++ Adaptive Forms-Client-Bibliotheken in AEM Sites einschließen

Um adaptive Forms-Komponenten auf einer AEM Sites-Seite zu verwenden, schließen Sie die Client-Bibliotheken &quot;customHeaderLibs&quot;und &quot;customfooterlibs&quot;mit dem AEM Archetyp/Git-Repository und der Bereitstellungs-Pipeline in die AEM Sites-Seite ein.

1. Öffnen Sie Ihre [AEM Forms-Archetyp oder geklontes Git-Repository](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) Projekt in einem Texteditor. Beispielsweise Visual Studio-Code.
1. Navigieren Sie zu `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml`.
1. Kopieren Sie den Wert von `sling:resourceSuperType`. Der Wert lautet beispielsweise `core/wcm/components/page/v3/page`.

   ![Sling-Ressource](/help/forms/assets/slingresource.png)

1. Erstellen Sie eine ähnliche Struktur am Speicherort `ui.apps/src/main/content/jcr_root/apps` gleich wie `core/wcm/components/page/v3/page`.

   ![Überlagerungsstruktur](/help/forms/assets/overlaystructure.png)

1. Hinzufügen `customheaderlibs.html` und `customfooterlibs.html` Dateien.

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

   Die Datei customfooterlibs.html wird für JavaScript und die Datei customheaderlibs.html für css verwendet.

1. [Pipeline ausführen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) um die Änderungen bereitzustellen.

+++

### Erstellen eines adaptiven Formulars mit der Komponente Adaptiver Forms-Container {#create-af-using-af-container}


So erstellen Sie ein adaptives Formular mit [!UICONTROL Adaptiver Forms-Container] component:

1. Öffnen Sie die AEM Sites-Seite im Bearbeitungsmodus.
1. Ziehen Sie im Komponenten-Browser-Bedienfeld die **[!UICONTROL Adaptiver Forms-Container]** -Komponente auf der Seite.
1. Erstellen Sie ein adaptives Formular mit den Adaptive Forms-Komponenten.
1. Speichern Sie die Einstellungen.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

Ihr Formular ist bereit. Wenn Sie die AEM Sites-Seite veröffentlichen, werden das adaptive Formular und die zugehörigen referenzierten Assets automatisch veröffentlicht.

#### Konfigurieren der Container-Eigenschaften für adaptive Formulare {#configure-additional-settings-container}

Sie können die erweiterten Einstellungen der [!UICONTROL Container für adaptive Formulare] -Komponente. Beispiel:

* Sie können den Vorbefüllungs-Dienst so konfigurieren, dass ein adaptives Formular mit vorausgefüllten Werten auf der Seite einer Site geladen wird.
* Sie können die Datenmodelleinstellungen konfigurieren, um das adaptive Formular mit einer Datenquelle zu verknüpfen.
* Sie können die Sendeaktionen konfigurieren, um die Daten auf Microsoft® OneDrive, Microsoft® OneDrive oder anderen Datenquellen bei Übermittlung eines Formulars zu senden. Sie können auch eine benutzerdefinierte Übermittlungsaktion für Ihre adaptive Forms erstellen und auswählen.

So legen Sie die Eigenschaften für die **[!UICONTROL Adaptiver Forms-Container]** -Komponente klicken Sie auf die ![settings_icon](/help/forms/assets/Smock_Wrench_18_N.svg) in der Aktionsleiste. Die **[!UICONTROL Adaptiven Forms-Container bearbeiten]** wird geöffnet.

![Dialogfeld „Bearbeiten“](/help/forms/assets/adaptiveformcontainer-editdialog.png)

Im [!UICONTROL Adaptiven Forms-Container bearbeiten] können Sie Folgendes angeben.
* **Registerkarte „Allgemein“**
   * **Vorbefüllungs-Dienst**: Sie können den Vorbefüllungs-Dienst verwenden, um Felder eines adaptiven Formulars mit vorhandenen Daten automatisch auszufüllen. Wenn ein Benutzer ein Formular öffnet, werden die Werte für diese Felder vorbefüllt. Informationen zum Vorbefüllungs-Dienst finden Sie unter [Vorausfüllen von Feldern in adaptiven Formularen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/prepopulate-adaptive-form-fields.html#configuring-prefill-service-using-configuration-manager)
   * **Kategorie der Client-Bibliothek**: Geben Sie die [JavaScript-Funktionen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-rules-and-use-expressions-in-an-adaptive-form/rule-editor.html?lang=en#custom-functions) die in Ausdrücken verwendet und von Adaptive Forms unterstützt werden.
* **Datenmodell**: Mit einem Datenmodell können Sie Entitäten und Dienste aus unterschiedlichen Datenquellen in ein adaptives Formular integrieren. Auswählen **[!UICONTROL Formulardatenmodell]** wenn das adaptive Formular, das Sie erstellen, das Abrufen und Schreiben von Daten aus und in mehrere Datenquellen umfasst.
   * **Formulardatenmodell**: Mit einem Formulardatenmodell kann ein adaptives Formular mit unterschiedlichen Datenquellen kommunizieren. Informationen zum Konfigurieren einer Datenquelle finden Sie unter [Datenquellen konfigurieren](/help/forms/configure-data-sources.md).
   * **Schema**: Das Schema stellt die Struktur dar, in der Daten vom Back-End-System in Ihrem Unternehmen produziert oder genutzt werden. Sie können [Schema mit einem adaptiven Formular verknüpfen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/adaptive-form-json-schema-form-model.html) und verwenden die Elemente, um einem adaptiven Formular dynamischen Inhalt hinzuzufügen.

     >[!NOTE]
     >
     > Nach dem Konfigurieren des Formulardatenmodells können Sie das zugehörige Formularmodell nicht ändern. Es ist jedoch möglich, das mit dem Formulardatenmodell verknüpfte Schema zu ändern.

* **Registerkarte „Übermittlung“**

   * **Zu URL umleiten**
      * **Umleitungs-URL/Pfad**: Gibt die URL oder den Pfad an, zu dem ein adaptives Formular nach der Übermittlung umgeleitet wird.

      * **Übermittlungsaktion**: Eine Sendeaktion wird ausgelöst, wenn ein Benutzer in einem adaptiven Formular auf die Schaltfläche Senden klickt. Sie können [Konfigurieren der Sendeaktion im adaptiven Formular](/help/forms/configuring-submit-actions.md). Adaptive Formulare bieten die folgenden Übermittlungsaktionen standardmäßig:
         * An REST-Endpunkt übermitteln
         * E-Mail senden
         * Senden mit Formulardatenmodell
         * AEM-Workflow aufrufen
         * An SharePoint senden
         * An OneDrive senden
         * Senden an Azure Blob-Speicher

  Sie können auch [Standardmäßige Übermittlungsaktionen erweitern](custom-submit-action-form.md) , um eine eigene benutzerdefinierte Übermittlungsaktion zu erstellen.

* **Nachricht anzeigen**
   * **Nachrichteninhalt**: Schreiben Sie eine Nachricht mit dem Rich-Text-Editor, um sie beim Senden des Formulars anzuzeigen. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesnachricht angezeigt werden soll.

## Einbetten eines adaptiven Formulars  {#aem-container-component}

Verwenden **[!UICONTROL Adaptives Forms - Einbetten (V2)]** -Komponente können Sie entweder ein neues adaptives Formular einbetten oder ein vorhandenes adaptives Formular in die Seite der Site einbetten. Die [!UICONTROL Adaptive Forms - Embed(v2)] -Komponente können Sie:

* [Hinzufügen eines vorhandenen adaptiven Formulars](#embed-new-af)

* [Neues adaptives Formular erstellen und hinzufügen](#embed-existing-af)

### Voraussetzungen {#prerequisites}

+++ Aktivieren Sie die **Adaptives Forms - Einbetten** -Komponente.

Aktivieren [!UICONTROL Adaptive Forms - Embed(v2)] -Komponente in der Richtlinie der Vorlage ausführen, führen Sie die folgenden Schritte aus:

1. Navigieren Sie zu [!UICONTROL Seiteninformationen] > [!UICONTROL Vorlage bearbeiten]

1. Klicken Sie auf [!UICONTROL Politik] und wählen Sie die **[!UICONTROL Adaptives Formular - Einbetten (v2)]** Kontrollkästchen unter dem **[!UICONTROL [AEM Archetyp Projektname] - Forms]** Gruppe .
1. Klicken Sie auf **[!UICONTROL Fertig]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419369?quality=12&learn=on)

+++

+++ Adaptive Forms-Client-Bibliotheken in AEM Sites einschließen

Wenn die **[!UICONTROL Wenn das Formular die gesamte Breite einer Seite abdeckt]** ist in der **[!UICONTROL Formularcontainer]** Dialogfeld &quot;Konfigurieren&quot;und **Adaptives Forms mit Kernkomponenten** verwendet werden, ist es erforderlich, die clientlibs auf der entsprechenden Site-Seite aufzunehmen.

![Gif überlagern](/help/forms/assets/overlaycorecomponent.gif)

Um adaptive Forms-Komponenten auf einer AEM Sites-Seite zu verwenden, schließen Sie die `Customheaderlibs` und `Customfooterlibs` Client-Bibliotheken zur AEM Sites-Seite mithilfe des AEM-Archetyp-/Git-Repository und der Bereitstellungs-Pipeline.

1. Öffnen Sie Ihre [AEM Forms-Archetyp oder geklontes Git-Repository](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) Projekt in einem Texteditor. Beispielsweise Visual Studio-Code.
1. Navigieren Sie zu `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml`.
1. Kopieren Sie den Wert von `sling:resourceSuperType`. Der Wert lautet beispielsweise `core/wcm/components/page/v3/page`.

   ![Sling-Ressource](/help/forms/assets/slingresource.png)

1. Erstellen Sie eine ähnliche Struktur am Speicherort `ui.apps/src/main/content/jcr_root/apps` gleich wie `core/wcm/components/page/v3/page`.

   ![Überlagerungsstruktur](/help/forms/assets/overlaystructure.png)

1. Hinzufügen `customheaderlibs.html` und `customfooterlibs.html` Dateien.

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

   Die `customfooterlibs.html` wird für JavaScript verwendet und die Variable `customheaderlibs.html` für die CSS.

1. [Pipeline ausführen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) um die Änderungen bereitzustellen.

+++

### Hinzufügen eines vorhandenen adaptiven Formulars zur AEM Sites-Seite {#embed-existing-af}

1. Öffnen Sie die AEM Sites-Seite im Bearbeitungsmodus.
1. Ziehen Sie im Komponenten-Browser-Bedienfeld die [!UICONTROL Adaptives Forms - Einbetten] -Komponente auf der Seite.
1. Tippen Sie auf [!UICONTROL Adaptives Forms - Einbetten] Komponente auf der Siteseite und tippen Sie auf ![settings_icon](/help/forms/assets/Smock_Wrench_18_N.svg) in der Aktionsleiste. Die **[!UICONTROL Adaptive Forms bearbeiten - Einbetten]** wird geöffnet.
1. Suchen Sie nach dem einzubettenden adaptiven Formular und wählen Sie es aus. [!UICONTROL Asset-Pfad].
1. Speichern Sie die Einstellungen. Das adaptive Formular ist jetzt in der Seite eingebettet.

>[!VIDEO](https://video.tv.adobe.com/v/3419368?quality=12&learn=on)



### Erstellen und Hinzufügen eines neuen adaptiven Formulars zur AEM Sites-Seite {#embed-new-af}

1. Öffnen Sie die AEM Sites-Seite im Bearbeitungsmodus.
1. Ziehen Sie im Komponenten-Browser-Bedienfeld die [!UICONTROL Adaptive Forms - Embed(v2)] -Komponente auf der Seite.
1. Klicken Sie auf **Plus** und Sie werden zum Assistenten zur Formularerstellung weitergeleitet.

   ![Adaptives Forms - Einbettungskomponente](/help/forms/assets/aemformcontainer.png)

1. Erstellen Sie ein neues adaptives Formular aus dem [!UICONTROL Formularerstellung] Assistent.
1. Die [!UICONTROL Asset-Pfad] enthält bereits den Pfad eines erstellten adaptiven Formulars
1. Speichern Sie die Einstellungen. Das adaptive Formular ist jetzt in der Seite eingebettet.

>[!VIDEO](https://video.tv.adobe.com/v/3419366/adaptive-form-aem-forms?quality=12&learn=on)

#### Konfigurieren des adaptiven Formulars - Einbettungseigenschaften (v2) {#configure-adaptive-form-embed}

Sie können die erweiterten Einstellungen der [!UICONTROL Adaptives Formular - Embed(v2)] -Komponente. Im [!UICONTROL Adaptive Forms bearbeiten - Embed(v2)] können Sie Folgendes angeben.

* **Asset-Pfad**: Klicken Sie auf „Durchsuchen“ und wählen Sie das einzubettende adaptive Formular aus. Es wird automatisch ausgefüllt, wenn Sie es über den Assets-Browser eingefügt haben.
* **Nach dem Senden**: Wählen Sie die Aktion aus, die bei der Formularübermittlung ausgelöst werden soll. Sie können auswählen, dass eine Dankesnachricht oder eine Dankeseite angezeigt werden soll.
   * **Dankesmeldung anzeigen**: Schreiben Sie eine Nachricht mit dem Rich-Text-Editor, um sie beim Senden des Formulars anzuzeigen. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesnachricht angezeigt werden soll.
   * **Danksagungsseite anzeigen**: Suchen Sie die Seite, die bei der Formularübermittlung angezeigt werden soll, und wählen Sie sie aus. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankeseite angezeigt werden soll.
   * **Umleiten zur Dankeseite**: Aktivieren Sie die Option, um die Seite mit dem eingebetteten adaptiven Formular durch die Dankeseite zu ersetzen. Andernfalls ersetzt die Dankeseite das adaptive Formular im [!UICONTROL Adaptives Forms - Einbetten] -Komponente, ohne die zugrunde liegenden Sites auf der Seite zu aktualisieren. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankeseite angezeigt werden soll.
* **Seitensprache verwenden**: Verwenden Sie das Gebietsschema der AEM Sites-Seite anstelle des Gebietsschemas des adaptiven Formulars.
* **Fokus auf Formular festlegen**: Wählen Sie diese Option aus, um den Fokus auf das erste Feld des adaptiven Formulars zu legen.
* **Das Formular deckt die gesamte Breite des Rahmens ab**: Wenn diese Option aktiviert ist, wird iframe nicht zum Rendern des Formulars verwendet.
* **Höhe**: Geben Sie die Höhe des Containers an. Lassen Sie es leer, um die Größe des Containers automatisch zu ändern.
* **CSS-Client-Bibliothek**: Geben Sie den Pfad zu einer CSS-Client-Bibliothek an.

### Veröffentlichen hinzugefügter adaptiver Forms mithilfe der Komponente Adaptives Formular - Einbetten (v2)  {#publish-embedded-adaptive-form}

Beachten Sie die folgenden Szenarien für die Veröffentlichung des hinzugefügten adaptiven Forms mithilfe des **[!UICONTROL Adaptives Formular - Embed(v2)]** component:

* Wenn Sie eine AEM Sites-Seite zum ersten Mal veröffentlichen, werden die der Sites-Seite hinzugefügten Formulare automatisch veröffentlicht.
* Wenn Sie ein adaptives Formular ändern, das zu einer bereits veröffentlichten Sites-Seite hinzugefügt wurde, veröffentlichen Sie das entsprechende adaptive Forms manuell.
* Wenn Sie eine Sites-Seite und die entsprechende adaptive Forms ändern, veröffentlichen Sie die Sites-Seite und alle adaptiven Forms, die zur Sites-Seite hinzugefügt wurden, erneut.

### Ändern der hinzugefügten adaptiven Forms mithilfe der Komponente Adaptives Formular - Embed(v2)  {#modifying-embedded-adaptive-form}

Um eine Konfiguration oder Eigenschaft eines adaptiven Formulars zu ändern, führen Sie einen der folgenden Schritte aus:

* Öffnen Sie das Originalformular in einem adaptiven Formular im entsprechenden Editor und ändern Sie es.
* Tippen Sie von der Sites-Seite aus im Bearbeitungsmodus auf das adaptive Formular und tippen Sie dann auf **[!UICONTROL In neuem Fenster bearbeiten]**. Das ursprüngliche Formular wird im Bearbeitungsmodus geöffnet, sodass Sie es bearbeiten können.

## Layout eines adaptiven Formulars ändern, das zu einer AEM Sites-Seite hinzugefügt wurde {#change-layout-af-aem-sites-page}

Auf der AEM Sites-Seite wird die [Layout-Modus](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/features/responsive-layout.html?#defining-layouts-layout-mode) ermöglicht die Größenanpassung eines adaptiven Formulars, das erstellt oder der AEM Sites-Seite hinzugefügt wird.

![AF-layout-support](/help/forms/assets/afsite-layoutsupport.gif)

AEM Siteseite behält einen Verweis auf das adaptive Formular bei. Wenn Sie eine AEM Sites-Seite übersetzen, werden automatisch ein adaptives Formular und die zugehörigen referenzierten Assets mit der Variablen [Übersetzungsprojekte](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/reusing-content/translation/managing-projects.html?lang=en#adding-pages-assets-to-a-translation-job) in andere Sprachen übersetzen.

## Best Practices {#best-practices}

* Die Kopf- und Fußzeile im Originalformular sind nicht im eingebetteten Formular enthalten.
* Benutzerentwürfe und -übermittlungen von eingebetteten Formularen werden unterstützt und sind auf den Registerkarten &quot;Entwürfe&quot;und &quot;Gesendete Forms&quot;im Forms-Portal sichtbar.