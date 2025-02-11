---
title: Wie wird ein adaptives Formular zu einer AEM Sites-Seite hinzugefügt?
description: Sie können adaptive Formulare nahtlos in eine AEM Sites-Seite oder eine außerhalb von AEM gehostete Webseite einbetten.
feature: Adaptive Forms
role: Admin, User, Developer
Keywords: Forms AEM Sites, Embed Form to a Sites page, Adaptive Forms AEM Sites, Embed Adaptive Forms to AEM Page, Embed Forms in an AEM Sites page
exl-id: 359b05e8-d8c1-4a77-9e70-6f6b6e668560
source-git-commit: 64a8b363cff079aa0a6f56effd77830ac797deca
workflow-type: ht
source-wordcount: '3145'
ht-degree: 100%

---

# Einbetten eines adaptiven Formulars in eine AEM Sites-Seite {#embed-an-adaptive-form-to-aem-sites-page}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/embed-adaptive-form-aem-sites.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |


## Übersicht {#overview}

Mit AEM Forms können Formularentwickelnde adaptive Formulare problemlos in eine AEM Sites-Seite oder in eine Web-Seite einbetten, die außerhalb von AEM gehostet wird. Das eingebettete adaptive Formular ist voll funktionsfähig, und Benutzende können es ausfüllen und senden, ohne die Seite zu verlassen. Dies hilft Benutzenden, im Kontext anderer Elemente auf der Web-Seite zu bleiben und gleichzeitig mit dem Formular zu interagieren. Dadurch können Benutzende bequem Formulare ausfüllen und senden, ohne jemals die Seite verlassen zu müssen, auf der sie sich befinden. Diese Integration bietet eine praktische Möglichkeit, die bereits erstellte adaptiven Formulare wiederzuverwenden.

Mit dem AEM-Seiteneditor können Sie schnell mehrere Formulare auf Ihren AEM Sites-Seiten einbetten. Durch die Verwendung des AEM-Seiteneditors können Inhaltsautorinnen und Inhaltsautoren nahtlose Erlebnisse zur Datenerfassung auf einer Sites-Seite erstellen, indem sie die Leistung adaptiver Formularkomponenten nutzen, einschließlich dynamischem Verhalten, Überprüfungen, Datenintegration, Generierung von Datensatzdokumenten und Automatisierung von Geschäftsprozessen. Außerdem können Sie damit verschiedene Funktionen von AEM Sites-Seiten verwenden, z. B. Versionierung, Targeting, Übersetzung und Multi-Site-Manager.

AEM Forms bietet **[!UICONTROL Container]**- und **[!UICONTROL Einbettungskomponenten für adaptive Formulare]**. Sie können **[!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)]** verwenden, um ein vorhandenes adaptives Formular hinzuzufügen oder ein Formular mit dem Editor für adaptive Formulare zu erstellen, oder **[!UICONTROL Container für adaptive Formulare]**, um ein neues Formular in einem Experience Fragment oder einer AEM Sites-Seite zu erstellen.

![Beispiel für ein adaptives Formular auf einer AEM Sites-Seite](/help/forms/assets/adaptive-form-in-sites-page.png)

<!-- For information about embedding an Adaptive Form in an external web page, see [Embed Adaptive Form in external web page](/help/forms/using/embed-adaptive-form-external-web-page.md). 

## Why embed an Adaptive Form in AEM Sites page or AEM Experience Fragment? 

Using **[!UICONTROL Adaptive Forms – Embed(v2)]** in AEM Page Editor lets you create seamless data capture experiences within a Sites page using the power of Adaptive Forms components including dynamic behavior, validations, data integration, generate document of record and business process automation. It also lets you use various features of AEM Sites pages like, versioning, targeting, translation, and multi-site manager, enhancing the overall form creation and management experience. Let's explore some of these features:

* **Versioning:** AEM Sites pages offer [robust versioning capabilities](/help/sites-cloud/authoring/sites-console/page-versions.md), allowing you to track and manage different versions of your forms. This enables you to make changes and enhancements to forms while maintaining the ability to roll back to previous versions if needed. Versioning ensures a controlled and organized approach to form development and evolution.
* **Targeting (Integration with Adobe Target):** With AEM Sites pages targeting capabilities, you can also [personalize the form experience for different audiences](/help/sites-cloud/integrating/integrating-adobe-target.md). By using user segments and targeting criteria, you can tailor the form's content, design, or behavior to specific groups of users. This enables you to provide a personalized and relevant form experience, increasing engagement and conversion rates.
* **Translation:** AEM Sites [seamless integration with translation services](/help/sites-cloud/administering/translation/overview.md), allowing you to translate forms into multiple languages easily. This feature simplifies the localization process, ensuring that your forms are accessible to a global audience. You can manage translations efficiently within AEM translation projects, reducing time and effort required for multilingual form support. See considerations section for more information on translation.  
* **Multi-site Management and Live Copy:** AEM Sites provide robust [Multi-site Management and Live Copy capabilities](/help/sites-cloud/administering/msm/overview.md), enabling you to create and manage multiple websites within a single environment. This feature now lets you reuse forms across different sites, ensuring consistency and reducing duplication efforts. With centralized control and management, you can efficiently maintain and update forms across multiple websites.
* **Themes:** AEM Sites pages provide a framework for designing and maintaining consistent visual styles across multiple web pages. These define colors, fonts, style sheets, and other visual elements that contribute to the overall look and feel of the website. [You can use the themes designed for an AEM Sites page for an Adaptive Form, saving time and effort](/help/sites-cloud/administering/site-creation/site-themes.md#using-site-themes-using-themes). 
* **Tagging:** AEM Sites pages allow you to [assign tags or labels to a page, an asset, or other content](/help/implementing/developing/introduction/tagging-framework.md). Tags are keywords or metadata labels that provide a way to categorize and organize content based on specific criteria. You can assign one or more tags to pages, assets, or any other content items within AEM to improve search and categorize the assets. 
* **Locking and Unlocking content:** AEM Sites allow users to [control access and modifications to pages](/help/sites-cloud/authoring/page-editor/edit-content.md) within the AEM Sites environment. When a page is locked, it means that it is protected from unauthorized changes or edits by other users. Only the user who has locked the content or a designated administrator can unlock it to allow modifications. 

In addition, Adaptive Forms in AEM Page Editor use [Adaptive Forms Core Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en#features). These Core Components provide a standard and easier methods to style and customize the components, identical to [AEM Sites WCM Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=en).

-->

## Wie kann ich ein adaptives Formular auf einer AEM Sites-Seite oder in einem AEM Experience Fragment erstellen oder einbetten? {#various-options-to-create-or-embed-an-adaptive-form-in-aem-sites-page-or-aem-experience-fragment}

Sie können diese Funktion bestmöglich nutzen, indem Sie die folgenden Optionen verwenden:

* **[Erstellen eines adaptiven Formulars mit genehmigten Vorlagen und Einbetten in eine AEM Sites-Seite](#embed-form-using-adaptive-form-wizzard-aem-sites):** Sie können vorab genehmigte Vorlagen nutzen, um schnell adaptive Formulare zu erstellen und einzubetten, die den Branding-Richtlinien und Design-Standards Ihres Unternehmens entsprechen.

* **[Einbetten von vorhandenen Formularen in eine AEM Sites-Seite:](#embed-an-adaptive-form-in-sites-editor)** Sie können bereits erstellte Formulare einfach in Ihre Websites integrieren, sodass Besucherinnen und Besucher direkt mit ihnen interagieren können.

* **[Konvertieren eines eingebetteten adaptiven Formulars in ein Experience Fragment](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment):** Konvertieren Sie ein eingebettetes adaptives Formular, das zu einer AEM Sites-Seite hinzugefügt wurde, in ein Experience Fragment, um das Formular auf mehreren AEM Sites-Seiten wiederverwenden zu können.

* **[Erstellen und Hinzufügen eines benutzerdefinierten adaptiven Formulars zu einer AEM Sites-Seite](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md#create-an-adaptive-form-in-sites-editor-or-experience-fragment):****[!UICONTROL Sie können die Container-Komponente für adaptive Formulare verwenden, um ein brandneues Formular von Grund auf neu zu erstellen und es speziell auf Ihre Anforderungen und Design-Vorlieben anzupassen.]**

* **[Erstellen und Hinzufügen eines benutzerdefinierten adaptiven Formulars zu Experience Fragments](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md#create-an-adaptive-form-in-sites-editor):** Sie können die Reichweite Ihrer Formulare erweitern, indem Sie sie zu AEM Experience Fragments hinzufügen, wodurch eine nahtlose Wiederverwendung über mehrere Seiten oder Sites hinweg ermöglicht wird.

* **Hinzufügen von mehreren Formularen zu einer AEM Sites-Seite oder einem Experience Fragment:** Sie können mehrere adaptive Formulare erstellen oder zu einer AEM Sites-Seite hinzufügen, um Benutzenden basierend auf ihren Vorlieben und Anforderungen mehrere Optionen zur Verfügung zu stellen. Mit dem AEM-Seiteneditor können Sie schnell mehrere Formulare auf Ihren AEM Sites-Seiten einbetten. Sie können die Komponente **[!UICONTROL Container für adaptive Formulare]** mehrfach verwenden, um einer AEM Sites-Seite adaptive Formulare hinzuzufügen. Sie können **[!UICONTROL Adaptive Formulare – Einbettungskomponente]** nur dann mehrfach auf einer AEM Sites-Seite verwenden, wenn die Option **[!UICONTROL Formular deckt die gesamte Breite des Rahmens ab]** ausgewählt ist. Falls die Option **[!UICONTROL Formular deckt die gesamte Breite des Rahmens ab]** nicht aktiviert ist, unterstützt die AEM Sites-Seite nur ein adaptives Formular ohne iFrame. Um weitere adaptive Formulare mit **[!UICONTROL Adaptive Formulare – Einbettungskomponente]** hinzuzufügen, wählen Sie die Option **[!UICONTROL Formular deckt die gesamte Breite des Rahmens ab]** aus.

## Überlegungen zum Einbetten eines adaptiven Formulars auf einer AEM Sites-Seite oder in einem AEM Experience Fragment {#consideration}

* Wenn Sie ein Formular mit **[!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)]** erstellen oder hinzufügen, werden die Formulare mithilfe des Übersetzungsflusses von AEM Forms übersetzt und lokalisiert. In diesem Fall wird ein einzelnes Formular beibehalten und in allen Sprachkopien der Sites-Seiten referenziert. **[!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)]** bietet keinen Zugriff auf verschiedene Funktionen von AEM Sites-Seiten wie Versionierung, Targeting, Übersetzung und Multi-Site-Manager.

* Wenn Sie den **[!UICONTROL Container für adaptive Formulare]** verwenden, um ein Formular zu erstellen, werden die Formulare über den AEM Sites-Übersetzungsfluss übersetzt und lokalisiert. Für jede Sprache wird eine separate Kopie (Sprachkopie) der Sites-Seite und der entsprechenden Formulare generiert. Wenn Inhaltsautorinnen oder Inhaltsautoren eine Regel in einem Formular auf der übergeordneten Seite ändern, müssen dieselben Änderungen in allen Sprachkopien des Formulars vorgenommen werden. Mit dem **[!UICONTROL Container für adaptive Formulare]** können Sie auch verschiedene Funktionen von AEM Sites-Seiten verwenden, z. B. Versionierung, Targeting, Übersetzung und Multi-Site-Manager.


## Anforderungen zum Einbetten eines adaptiven Formulars auf einer AEM Sites-Seite oder in einem AEM Experience Fragment {#before-you-start-embedding-an-adaptive-form}

Bevor Sie mit der Einbettung eines neuen adaptiven Formulars oder eines bereits vorhandenen adaptiven Formulars mit **[!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)]** beginnen, aktivieren Sie die **Kernkomponenten adaptiver Formulare** und fügen Sie **Client-Bibliotheken für adaptive Formulare** zu Ihrer AEM Sites-Seite hinzu:

### Aktivieren der Kernkomponenten für adaptive Formulare für Ihre AEM Cloud Service-Umgebung

Stellen Sie sicher, dass die [Kernkomponenten für adaptive Formulare für Ihre AEM Forms as a Cloud Service-Umgebung aktiviert sind](enable-adaptive-forms-core-components.md).

### Hinzufügen von Client-Bibliotheken für adaptive Formulare zu einer AEM Sites-Seite oder einem Experience Fragment

Wenn die Option **[!UICONTROL Wenn das Formular die gesamte Breite einer Seite einnimmt]** im Konfigurationsdialogfeld **[!UICONTROL Formular-Container]** ausgewählt ist und adaptive Formulare unter Verwendung von Kernkomponenten verwendet werden, ist es notwendig, die Client-Bibliotheken auf der entsprechenden Seite der Site einzubinden.

![Die Option „Formular deckt die gesamte Breite einer Seite ab“ ist ausgewählt und das adaptive Formular mit Kernkomponenten wird verwendet](/help/forms/assets/overlaycorecomponent.gif)


Fügen Sie die Client-Bibliotheken **Customheaderlibs** und **Customfooterlibs** auf Ihrer AEM Sites-Seite mithilfe der Bereitstellungs-Pipeline ein. Hinzufügen von Client-Bibliotheken:

1. Greifen Sie auf Ihr [AEM Cloud Service-Git-Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/repositories.html?lang=de) zu und klonen Sie es.
1. Öffnen Sie den Ordner „AEM Cloud Service-Git-Repository“ in einem einfachen Texteditor. Beispielsweise Microsoft® Visual Code.
1. Öffnen Sie die Datei `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\customheaderlibs.html` und fügen Sie ihr den folgenden Code hinzu:

   ```
       //Customheaderlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

1. Öffnen Sie die Datei `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\customfooterlibs.html` und fügen Sie ihr den folgenden Code hinzu:

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

1. Öffnen Sie die Datei `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\xfpage\customheaderlibs.html` und fügen Sie ihr den folgenden Code hinzu:

   ```
       //Customheaderlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

1. Öffnen Sie die Datei `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\xfpage\customfooterlibs.html` und fügen Sie ihr den folgenden Code hinzu:

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

1. [Führen Sie die Bereitstellungs-Pipeline aus](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html?lang=de), um die Client-Bibliotheken in Ihrer AEM as a Cloud Service-Umgebung bereitzustellen.

### Aktivieren der „Adaptive Formulare – Einbettungskomponente (v2)“ für Ihre AEM Sites-Seite oder ein Experience Fragment

Führen Sie die folgenden Schritte aus, um die **[!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)]** in der Richtlinie der Vorlage zu aktivieren:

1. Öffnen Sie die AEM Sites-Seite oder das Experience Fragment zur Bearbeitung. Um die Seite zur Bearbeitung zu öffnen, wählen Sie die Seite aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Öffnen Sie die Vorlage Ihrer Sites- oder Experience Fragment-Seite. Um die Vorlage zu öffnen, navigieren Sie zu **[!UICONTROL Seiteninformationen]** ![Seiteninformationen](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Vorlage bearbeiten]**. Dadurch wird die entsprechende Vorlage im Vorlageneditor geöffnet.
1. Klicken Sie in der Strukturansicht auf das Symbol **[!UICONTROL Richtlinie]** ![Richtlinie](/help/forms/assets/Smock_FeedManagement_18_N.svg) in der Menüleiste. Aktivieren Sie in der Liste **[!UICONTROL Zulässige Komponenten]** das Kontrollkästchen **[!UICONTROL Adaptive Formulare – Einbetten (v2)]** unter **[AEM-Projektarchetyp-Name] – Adaptives Formular**.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419369?quality=12&learn=on)

## Einbetten eines adaptiven Formulars mit der Adaptive Formulare – Einbettungskomponente (v2) {#embed-an-adaptive-form-in-sites-editor-or-experience-fragment}

Verwenden Sie die **[!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)]**, um mithilfe des Assistenten zur Formularerstellung im AEM Sites-Editor ein adaptives Formular zu erstellen. Das resultierende Formular wird als externe Entität gespeichert, sodass es in anderen Sites-Seiten und eigenständigen Formularen wiederverwendet werden kann. Sie können ein brandneues Formular von Grund auf neu direkt in eine AEM Sites-Seite oder ein Experience Fragment einbetten und es speziell an Ihre Anforderungen und Design-Vorlieben anpassen. Bei Formularen mit nur einem Verwendungszweck wird empfohlen, eine AEM Sites-Seite direkt zu erstellen, während Experience Fragments sich ideal für Formulare eignen, die auf mehreren Seiten auf Ihrer Website wiederverwendet werden müssen.

Sie können ein neues Formular einfach mit der **[!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)]** einbetten.  Stellen Sie sich beispielsweise vor, ein neues Kontaktformular in eine AEM Sites-Seite oder AEM Experience Fragment zu integrieren. Alle Aktualisierungen oder Änderungen, die auf der AEM Sites-Seite oder im Experience Fragment am Kontaktformular vorgenommen werden, werden automatisch auf alle Seiten übertragen, auf denen es bereitgestellt wird. Dies vereinfacht die Verwaltung der Formulare Ihrer Website, gewährleistet ein nahtloses Anwendererlebnis und optimiert gleichzeitig den gesamten Prozess.

Durch die Verwendung der **[!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)]** haben Sie folgende Möglichkeiten:

* [Einbetten eines neuen Formulars in eine AEM Sites-Seite mitihilfe des Assistenten für adaptive Formulare](#embed-form-using-adaptive-form-wizzard-aem-sites)
* [Einbetten eines neuen Formulars in ein Experience Fragment mithilfe des Assistenten für adaptive Formulare](#embed-form-using-adaptive-form-wizzard-experience-fragment)
* [Einbetten eines vorhandenen adaptiven Formulars in eine AEM Sites-Seite](#embed-an-adaptive-form-in-sites-editor)
* [Einbetten eines vorhandenen Formulars in ein Experience Fragment](#embed-an-adaptive-form-in-experience-fragment)
* [Konvertieren eines adaptiven Formulars in einer AEM-Sites-Seite zu einem Experience Fragment](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment)

### Einbetten eines neuen Formulars in eine AEM Sites-Seite mitihilfe des Assistenten für adaptive Formulare {#embed-form-using-adaptive-form-wizzard-aem-sites}

Schritte zum Einbetten eines neuen Formulars in eine AEM Sites-Seite:

1. Öffnen Sie die AEM Sites-Seite im Bearbeitungsmodus.
1. Ziehen Sie die **[!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)]** per Drag-and-Drop aus dem Komponenten-Browser auf die Seite.
1. Klicken Sie auf das **Plus**-Symbol, und Sie werden zum Assistenten für die Formularerstellung weitergeleitet.

   ![Adaptive Formulare – Einbettungskomponente](/help/forms/assets/aemformcontainer.png)

1. Erstellen Sie ein neues adaptives Formular mit dem Assistenten für die **[!UICONTROL Formularerstellung]**.
Der **[!UICONTROL Asset-Pfad]** enthält bereits den Pfad eines erstellten adaptiven Formulars
1. Speichern Sie die Einstellungen. Das adaptive Formular ist jetzt in der Seite eingebettet.

>[!VIDEO](https://video.tv.adobe.com/v/3419366/adaptive-form-aem-forms?quality=12&learn=on)

Als Nächstes können Sie mithilfe des Assistenten zur Formularerstellung die Übermittlungsaktion und die erweiterten Eigenschaften eines eingebetteten adaptiven Formulars [festlegen](/help/forms/configuring-submit-actions.md).


### Einbetten eines neuen Formulars in ein Experience Fragment mithilfe des Assistenten für adaptive Formulare {#embed-form-using-adaptive-form-wizzard-experience-fragment}

Schritte zum Einbetten eines neuen Formulars in ein Experience Fragment:

1. Öffnen Sie das Experience Fragment im Bearbeitungsmodus.
1. Ziehen Sie die **[!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)]** per Drag-and-Drop aus dem Komponenten-Browser auf die Seite.
1. Klicken Sie auf das **Plus**-Symbol, und Sie werden zum Assistenten für die Formularerstellung weitergeleitet.

   ![Adaptive Formulare – Einbettungskomponente](/help/forms/assets/aemformcontainer.png)

1. Erstellen Sie ein neues adaptives Formular mit dem Assistenten für die **[!UICONTROL Formularerstellung]**.
Der **[!UICONTROL Asset-Pfad]** enthält bereits den Pfad eines erstellten adaptiven Formulars
1. Speichern Sie die Einstellungen. Das adaptive Formular ist jetzt im Experience Fragment eingebettet.

Als Nächstes können Sie mithilfe des Assistenten zur Formularerstellung die Übermittlungsaktion und die erweiterten Eigenschaften eines eingebetteten adaptiven Formulars [festlegen](/help/forms/configuring-submit-actions.md).

### Einbetten eines vorhandenen adaptiven Formulars in eine AEM Sites-Seite {#embed-an-adaptive-form-in-sites-editor}

Mit der **[!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)]** können Sie mühelos ein bereits vorhandenes adaptives Formular in eine AEM Sites-Seite integrieren. Diese Funktion verbessert die Anpassungsfähigkeit und Wiederverwendbarkeit von adaptiven Formularen erheblich und bietet Kundinnen und Kunden eine bequeme Möglichkeit, bereits erstellte Formulare wiederzuverwenden. Stellen Sie sich beispielsweise vor, ein Kontaktformular in eine AEM Sites-Seite zu integrieren, sodass das Formular nicht mehrmals neu erstellt werden muss.

Einbetten eines adaptiven Formulars in eine Sites-Seite:

1. Öffnen Sie die AEM Sites-Seite im Bearbeitungsmodus.
1. Ziehen Sie die **[!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)]** per Drag-and-Drop vom Komponenten-Browser auf die Sites-Seite.
1. Wählen Sie auf der Sites-Seite die **[!UICONTROL Adaptive Formulare – Einbettungskomponente]** aus und wählen Sie dann in der Aktionsleiste die Option ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg) aus. Das Dialogfeld **[!UICONTROL Bearbeiten von „Adaptive Formulare – Einbetten (v2)“]** wird geöffnet.
1. Wählen Sie das adaptive Formular aus, das Sie in den **[!UICONTROL Asset-Pfad]** einbetten möchten.
1. Speichern Sie die Einstellungen. Das adaptive Formular ist jetzt in der Seite eingebettet.

>[!VIDEO](https://video.tv.adobe.com/v/3419368?quality=12&learn=on)

Als Nächstes können Sie mithilfe des Assistenten zur Formularerstellung die Übermittlungsaktion und die erweiterten Eigenschaften eines eingebetteten adaptiven Formulars [festlegen](/help/forms/configuring-submit-actions.md).

### Einbetten eines vorhandenen adaptiven Formulars in ein Experience Fragment: {#embed-an-adaptive-form-in-experience-fragment}

Sie können die Barrierefreiheit Ihrer Formulare auch erweitern, indem Sie sie in ein AEM Experience Fragment einbetten. Einbetten eines adaptiven Formulars in ein Experience Fragment:

1. Öffnen Sie ein Experience Fragment im Bearbeitungsmodus.
1. Ziehen Sie die **[!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)]** vom Komponenten-Browser per Drag-and-Drop zum Experience Fragment.
1. Wählen Sie im Experience Fragment die **[!UICONTROL Einbettungskomponente für adaptive Formulare]** aus und wählen Sie in der Aktionsleiste die Option ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg) aus. Das Dialogfeld **[!UICONTROL Bearbeiten von „Adaptive Formulare – Einbetten (v2)“]** wird geöffnet.
1. Wählen Sie das adaptive Formular aus, das Sie in den **[!UICONTROL Asset-Pfad]** einbetten möchten.
1. Speichern Sie die Einstellungen. Das adaptive Formular ist jetzt in das Experience Fragment eingebettet.

Als Nächstes können Sie mithilfe des Assistenten zur Formularerstellung die Übermittlungsaktion und die erweiterten Eigenschaften eines eingebetteten adaptiven Formulars [festlegen](/help/forms/configuring-submit-actions.md).

### Konvertieren eines Formulars auf einer AEM Sites-Seite in ein Experience Fragment {#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment}

Sie können ein vorhandenes adaptives Formular in einem Sites-Seiteneditor in ein Experience Fragment konvertieren, um es auf mehreren Seiten oder Sites wiederzuverwenden.

So konvertieren Sie ein adaptives Formular auf einer AEM Sites-Seite in ein Experience Fragment:

1. Öffnen Sie die AEM Sites-Seite mit dem adaptiven Formular (in der Komponente „Container für adaptive Formulare“) im Bearbeitungsmodus.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]**, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formulare hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.
1. Wählen Sie in der Menüleiste das Symbol ![In Experience Fragment-Variante konvertieren](/help/forms/assets/Smock_FilingCabinet_18_N.svg).

   ![Klicken des Archivlogos, um ein adaptives Formular in einer AEM Sites-Seite in ein Experience Fragment zu konvertieren](/help/forms/assets/convert-form-in-sites-page-to-an-experience-fragment.png)

   Es wird ein Dialogfeld zum Konvertieren des Containers für adaptive Formulare in ein neues Experience Fragment oder zum Hinzufügen zu einem vorhandenen Experience Fragment angezeigt.

1. Legen Sie im Dialogfeld **[!UICONTROL In Experience Fragment-Variante konvertieren]** Werte für die folgenden Optionen fest:

   * **Aktion:** Wählen Sie diese Option aus, um ein Experience Fragment zu erstellen oder zu einem vorhandenen Experience Fragment hinzuzufügen.
   * **Übergeordneter Pfad:** Geben Sie den Pfad des Ordners an, in dem das Experience Fragment gehostet werden soll. Die Option ist nur zum Erstellen eines neuen Experience Fragments verfügbar.
   * **Vorlage:** Geben Sie den Pfad der Experience Fragment-Vorlage an. Wenn Sie keine Experience Fragment-Vorlage haben, [erstellen Sie eine](/help/implementing/developing/extending/experience-fragments.md). Die Option ist nur zum Hinzufügen des adaptiven Formulars zu einem vorhandenen Experience Fragment verfügbar.
   * **Fragmenttitel:** Geben Sie den Titel des Experience Fragments an. Der Titel identifiziert ein Experience Fragment eindeutig.
   * **Fragment-Tags:** Geben Sie das Tag des Experience Fragments an. Das Tag identifiziert die Kategorie eines Experience Fragments eindeutig.

## Konfigurieren der Eigenschaften der „Adaptive Formulare – Einbettungskomponente (v2)“

Sie können die erweiterten Einstellungen der **[!UICONTROL Adaptive Formulare – Einbettungskomponente (v2)]** anpassen. Im Dialogfeld **[!UICONTROL Bearbeiten von „Adaptive Formulare – Einbettungen“]** können Sie Folgendes angeben:

* **Asset-Pfad**: Suchen und wählen Sie das einzubettende adaptive Formular aus. Es wird automatisch ausgefüllt, wenn Sie es über den Assets-Browser eingefügt haben.
* **Nach dem Senden**: Wählen Sie die Aktion aus, die bei der Formularübermittlung ausgelöst werden soll. Sie können auswählen, dass eine Dankesnachricht oder eine Dankeseite angezeigt werden soll.
   * **Dankesnachricht anzeigen**: Verfassen Sie im Rich-Text-Editor eine Nachricht, die beim Absenden des Formulars angezeigt werden soll. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesnachricht angezeigt werden soll.
   * **Dankesseite anzeigen**: Suchen und wählen Sie die Seite aus, die bei Übermittlung eines Formulars angezeigt wird. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesseite angezeigt werden soll.
   * **Umleiten zur Dankeseite**: Aktivieren Sie die Option, um die Seite mit dem eingebetteten adaptiven Formular durch die Dankeseite zu ersetzen. Andernfalls ersetzt die Dankesseite das adaptive Formular in der **[!UICONTROL Adaptive Formulare – Einbettungskomponente]**, ohne die darunter liegenden Seiten zu aktualisieren. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesseite angezeigt werden soll.
   * **Dankesnachricht**: Kurze Bestätigung, die nach dem erfolgreichen Senden eines Formulars auf dem Bildschirm angezeigt wird.
   * **Dankesseite**: Suchen und wählen Sie die Seite aus, die nach dem erfolgreichen Senden eines Formulars angezeigt wird. 

* **Seitensprache verwenden**: Verwenden des Gebietsschemas der AEM Sites-Seite anstelle des Gebietsschemas des adaptiven Formulars. Diese Option ist nur auf adaptive Formulare (Foundation) anwendbar.
* **Fokus auf Formular festlegen**: Wählen Sie diese Option aus, um den Fokus auf das erste Feld des adaptiven Formulars zu legen. Diese Option ist nur auf adaptive Formulare (Foundation) anwendbar.
* **Design**: Wählen Sie ein Design aus, das die Formatierung für die Komponenten in Ihrem adaptiven Formular definiert. Zur Formatierung gehören Eigenschaften des Erscheinungsbildes, wie Schriftstil, Hintergrundfarbe, Abmessungen und Ausrichtung. Diese Option ist nur auf adaptive Formulare (Foundation) anwendbar.

  >[!NOTE]
  >
  > Sie können die Optionen **Seitensprache verwenden**, **Fokus auf Formular festlegen** und **Design** nur für adaptive Formulare (Foundation) verwenden.

* **Formular deckt die gesamte Breite des Rahmens ab**: 
Ein Inline-Frame (iframe) ist ein HTML-Element, das ein adaptives Formular auf eine AEM Sites-Seite lädt.

   * Wenn das Kontrollkästchen **[!UICONTROL Formular deckt die gesamte Breite des Rahmens ab]** aktiviert ist, belegt ein adaptives Formular die gesamte Breite des Containers, in dem es platziert wird. In diesem Fall wird kein iFrame zum Rendern des Formulars verwendet.  Das Layout und Design eines adaptiven Formulars passen sich an die gesamte Breite des Containers an, sodass es responsiv ist und an verschiedene Bildschirmgrößen angepasst werden kann. Mit dieser Option können Sie mehrere adaptive Formulare in eine AEM Sites-Seite einbetten.

     >[!NOTE]
     >
     > Um mehrere Formulare in eine AEM Sites-Seite einzubetten, aktivieren Sie das Kontrollkästchen **[!UICONTROL Formular deckt die gesamte Breite des Rahmens ab]**.

   * Wenn das Kontrollkästchen **[!UICONTROL Formular deckt die gesamte Breite des Rahmens ab]** nicht aktiviert ist, deckt ein adaptives Formular nicht die gesamte Breite des Containers ab. Stattdessen wird ein iframe zum Rendern des Formulars verwendet, der nicht über eine bestimmte Breite hinaus erweitert werden kann. Dieser Ansatz ist nützlich, wenn ein adaptives Formular bestimmte Grenzen hat und im Container mit anderen AEM-Komponenten daneben koexistieren muss. Wenn diese Option nicht aktiviert ist, kann nur ein einziges adaptives Formular ohne iFrame in eine AEM Sites-Seite eingebettet werden.

     >[!NOTE]
     >
     > Die AEM Sites-Seite unterstützt nur ein einziges adaptives Formular, das ohne iFrame vorhanden ist. Um weitere adaptive Formulare mit **[!UICONTROL Adaptive Formulare – Einbettungskomponente]** hinzuzufügen, wählen Sie die Option **[!UICONTROL Formular deckt die gesamte Breite des Rahmens ab]** aus.

* **Höhe**: Geben Sie die Höhe des Containers an. Lassen Sie es leer, um die Größe des Containers automatisch zu anzupassen.
* **CSS-Client-Bibliothek**: Geben Sie den Pfad zu einer CSS-Client-Bibliothek an.

<!--
In AEM Sites page, you can add an Adaptive Form using:

* **Adaptive Forms - Embed component**
   Adaptive Forms - Embed component enables AEM Sites authors to include an existing Adaptive Form within an AEM Sites page, thereby enhancing the reusability of adaptive forms. Existing Adaptive Forms can be used standalone or embedded in the site page. This integration provides a convenient way for customers to reuse Adaptive Forms they have already created.

* **Asset browser**
  All the forms are available under Assets. You can drag-drop the form as an asset on your page.

## Prerequisites {#prerequisites}

 To embed an Adaptive Form in an AEM Sites page that uses an editable template, ensure that the AEM Form component is configured as an allowed component in the associated template. 

In case **Adaptive Forms - Embed component** is not visible in the **Component browser panel** of AEM sites page, perform the following steps as illustrated in the video.

>[!VIDEO](https://video.tv.adobe.com/v/3410544)

In case Sites page is using a static template, you need to configure it in the paragraph system of the site page. 

## Embedding an Adaptive Form {#af-component}

To embed an Adaptive Form using the **[!UICONTROL Adaptive Forms - Embed]** component:

1. Open the AEM sites page, in edit mode, in which you want to embed an Adaptive Form.
1. From the Component browser panel, drag-drop the [!UICONTROL Adaptive Forms - Embed] component on the page. Alternatively, you can search for an Adaptive Form in the Assets browser and drag-drop it onto the Sites page. You can add a new Adaptive Form or embed an existing Adaptive Form. 

   >[!NOTE]
   >
   >Multiple Adaptive Forms - Embed components on a page are not supported.

1. To create and embed a new form, on the component toolbar, select the **Create Form** icon. A window to create the form opens. 

1. Select the embedded Adaptive Forms - Embed component in the sites page, and then select ![settings_icon](assets/settings_icon.png) on the action bar. The **[!UICONTROL Edit Adaptive Forms - Embed]** dialog opens.
1. In the Edit Adaptive Forms - Embed dialog, specify the following.

    **Asset Type:** Select the type of asset to embed. 
    * **Asset Path**: Browse and select the Adaptive Form to embed. It is auto-populated if you dropped it from the Assets browser.
    * **Post Submission** : Select the action to trigger on form submission. You can choose to show a thank you message or a thank you page.
        * Show

        * **Thank You Message**: Write a message using the rich text editor to show on form submission. This option is available only when you choose to show a thank you message.
        * **Thank You Page**: Browse and select the page to display on form submission. This option is available only when you choose to show a thank you page.
           * **Redirect to thank you page**: Enable the option to replace the page containing the embedded Adaptive Form with thank you page. Otherwise, the thank you page replaces the Adaptive Form in the [!UICONTROL Adaptive Forms - Embed] component, without refreshing underlying sites the page. This option is available only when you choose to show a thank you page.
    * **Use Page Language**: Use local of the AEM Sites page instead locale of Adaptive Form.
    * **Set Focus on Form**: Select to set the focus on the first field of the Adaptive Form.
    * **Theme**: Select a theme that defines styling for components of your Adaptive Form. Styling includes appearance properties such as font style, background color, dimensions, and alignment.
    * **Form covers entire width of the frame**: If checked, iframe is not used to render the form. 
    * **Height**: Specify the height of the container. Leave it blank to automatically resize the container.
    * **CSS Client library**: Specify path to a CSS client library.

1. Save the settings. The Adaptive Form  is now embedded in the page.


AEM site also lets you create an Adaptive Form on the fly using the Adaptive Forms - Embed component. Follow the steps to create an Adaptive Form using the **Adaptive Forms - Embed component** on AEM sites page:
1. Open the AEM sites page, in edit mode, in which you want to embed an Adaptive Form.
1. From the Component browser panel, drag-drop the Adaptive Forms - Embed component on the page.
1. Click the **Plus** icon and you are redirected to the form creation wizard.

    ![Adaptive Forms - Embed Component](/help/forms/assets/aemformcontainer.png)

1. You can now embed an Adaptive Form on AEM site pages using the [!UICONTROL AEM Forms Container Component].
-->

## Veröffentlichen von eingebetteten adaptiven Formularen {#publishing-embedded-adaptive-form}

Betrachten wir die folgenden Szenarien für das Veröffentlichen eines eingebetteten Formulars in einer AEM Sites-Seite:

* Wenn Sie die AEM Sites-Seite zum ersten Mal veröffentlichen und sie ein eingebettetes adaptives Formular enthält, veröffentlichen Sie die Sites-Seite und das eingebettete Asset.
* Wenn Sie nur das eingebettete Formular in einer veröffentlichten Sites-Seite geändert haben, veröffentlichen Sie das ursprüngliche Asset, und die Änderungen werden in der veröffentlichten Sites-Seite übernommen. Die veröffentlichte Sites-Seite enthält einen Verweis auf das Asset und erfordert kein erneutes Veröffentlichen der Seite.
* Wenn Sie die Sites-Seite und das eingebettete adaptive Formular geändert haben, veröffentlichen Sie die Sites-Seite und das eingebettete Asset erneut.

## Ändern eines eingebetteten adaptiven Formulars  {#modifying-embedded-adaptive-form}

Um eine Konfiguration oder Eigenschaft des eingebetteten adaptiven Formulars zu ändern, führen Sie einen der folgenden Schritte aus.

* Öffnen Sie das Originalformular in einem adaptiven Formular im entsprechenden Editor und ändern Sie es.
* Wählen Sie von der Sites-Seite aus im Bearbeitungsmodus das adaptive Formular und dann **[!UICONTROL In neuem Fenster bearbeiten]**. Das ursprüngliche Formular wird im Bearbeitungsmodus geöffnet, sodass sie es bearbeiten können.

>[!NOTE]
>
>Die im ursprünglichen adaptiven Formular vorgenommenen Änderungen werden automatisch im eingebetteten Formular übernommen. Allerdings müssen Sie das adaptive Formular oder die Sites-Seite erneut veröffentlichen, damit die Änderungen auf der veröffentlichten Seite angezeigt werden.

## Best Practices {#best-practices}

Beachten Sie die folgenden Punkte, wenn Sie adaptive Formulare in AEM Sites-Seiten einbetten:

* Die Kopf- und Fußzeile im Originalformular sind nicht im eingebetteten Formular enthalten.
* Benutzerentwürfe und -übermittlungen von eingebetteten Formularen werden unterstützt und sind auf den Registerkarten „Entwürfe“und „Gesendete Formulare“ im Formularportal sichtbar.
* Die im Originalformular konfigurierte Übermittlungsaktion wird im eingebetteten Formular beibehalten.
* Wenn Sie für das Originalformular Adobe Analytics konfiguriert haben, werden die Analysedaten des eingebetteten Formulars in Adobe Analytics erfasst. Sie sind jedoch nicht im Formularanalysebericht verfügbar.

## Siehe auch {#see-also}

* [Auf Kernkomponenten basierende, eigenständige adaptive Formulare erstellen](/help/forms/creating-adaptive-form-core-components.md)
* [Auf Kernkomponenten basierende, adaptive Formulare direkt auf einer AEM Sites-Seite erstellen](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
