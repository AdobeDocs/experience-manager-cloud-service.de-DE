---
title: Wie wird ein adaptives Formular zur AEM Sites-Seite hinzugefügt?
description: Hier erfahren Sie, wie Sie ein adaptives Formular erstellen oder zu Ihrer AEM Sites-Seite hinzufügen können. Lernen Sie auch die Vorteile und verschiedene Möglichkeiten zum Integrieren von Formularen in Ihre Website kennen.
feature: Adaptive Forms, Foundation Components
Keywords: AF in Sites editor, af in aem sites, aem sites af, add af to a sites page, af aem sites, af sites, create af in a sites page, adaptive form in aem sites, forms aem sites, add form to a sites page, adaptive forms aem sites, add adaptive forms to aem page, create forms in an aem sites page
exl-id: a1846c5d-7b0f-4f48-9d15-96b2a8836a9d
role: User, Developer
source-git-commit: 5b55a280c5b445d366c7bf189b54b51e961f6ec2
workflow-type: tm+mt
source-wordcount: '3306'
ht-degree: 95%

---

# Hinzufügen eines adaptiven Formulars zu einer AEM Sites-Seite oder einem Experience Fragment {#create-or-add-an-adaptive-form-to-aem-sites-page}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/create-or-add-an-adaptive-form-to-aem-sites-page.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

## Überblick {#overview}

Mit AEM Forms können Sie Ihrer AEM Sites-Seite nahtlos ein adaptives Formular hinzufügen. Dadurch können Ihre Besucherinnen und Besucher bequem Formulare ausfüllen und senden, ohne jemals die Seite verlassen zu müssen, auf der sie sich befinden. Sie können mühelos mit anderen Elementen der Website interagieren und gleichzeitig aktiv mit dem Formular interagieren.

Mit dem AEM-Seiteneditor können Sie schnell mehrere Formulare erstellen und zu Ihren AEM Sites-Seiten hinzufügen. Die Verwendung des AEM-Seiteneditors ermöglicht es Inhaltsautorinnen und Inhaltsautoren, nahtlose Erlebnisse zur Datenerfassung auf einer Sites-Seite zu erstellen, indem sie die Leistung adaptiver Formularkomponenten nutzen, einschließlich dynamischem Verhalten, Überprüfungen, Datenintegration, Generierung von Datensatzdokumenten und Automatisierung von Geschäftsprozessen. Außerdem können Sie damit verschiedene Funktionen von AEM Sites-Seiten verwenden, z. B. Versionierung, Targeting, Übersetzung und Multi-Site Manager.

Der AEM Forms Cloud Service bietet Container- und Einbettungskomponenten für adaptive Formulare. Sie können den Container für adaptive Formulare verwenden, um ein Formular auf einer AEM Sites-Seite oder in einem Experience Fragment zu erstellen. Oder Sie können mit der Einbettungskomponente für adaptive Formulare ein vorhandenes adaptives Formular hinzufügen oder mit dem Editor für adaptive Formulare ein Formular erstellen.

![Beispiel für ein adaptives Formular auf einer AEM Sites-Seite](/help/forms/assets/adaptive-form-in-sites-page.png)

## Warum werden Kernkomponenten für adaptive Formulare verwendet, um ein adaptives Formular auf der AEM Sites-Seite oder im Experience Fragment zu erstellen?

Wenn Sie in der Vergangenheit Foundation-Komponenten für adaptive Formulare oder einfache HTML-basierte Formulare für Ihre Sites erstellt haben, empfiehlt Adobe, Kernkomponenten für adaptive Formulare zu verwenden, um ein adaptives Formular auf der AEM Sites-Seite oder im Experience Fragment zu erstellen. Mit diesen können Sie verschiedene Funktionen von AEM Sites-Seiten verwenden, wie z. B. Versionierung, Targeting, Übersetzung und Multi-Site Manager, wodurch die Erstellung und Verwaltung von adaptiven Formularen insgesamt verbessert wird. Sehen wir uns einige dieser Funktionen an:

* **Versionierung:** AEM Sites-Seiten bieten eine [robuste Versionierungfähigkeiten](/help/sites-cloud/authoring/sites-console/page-versions.md), mit der Sie verschiedene Versionen Ihrer Formulare verfolgen und verwalten können. Dadurch können Sie Änderungen und Verbesserungen an Formularen vornehmen und gleichzeitig bei Bedarf auf frühere Versionen zurücksetzen. Versionierung stellt einen kontrollierten und organisierten Ansatz für die Formularentwicklung und -weiterentwicklung sicher.
* **Targeting (Integration mit Adobe Target):** Mit den Targeting-Funktionen von AEM Sites-Seiten können Sie auch [das Formularerlebnis für verschiedene Zielgruppen personalisieren](/help/sites-cloud/integrating/integrating-adobe-target.md). Mithilfe von Benutzersegmenten und Targeting-Kriterien können Sie den Inhalt, das Design oder das Verhalten des Formulars an bestimmte Benutzergruppen anpassen. Auf diese Weise können Sie ein personalisiertes und relevantes Formularerlebnis bereitstellen und die Interaktions- und Konversionsraten steigern.
* **Übersetzung:** AEM Sites kann [nahtlos mit Übersetzungsdiensten integriert werden](/help/sites-cloud/administering/translation/overview.md), sodass Sie Formulare einfach in mehrere Sprachen übersetzen können. Diese Funktion vereinfacht den Lokalisierungsprozess und stellt sicher, dass Ihre Formulare für eine globale Zielgruppe zugänglich ist. Sie können Übersetzungen effizient in AEM-Übersetzungsprojekten verwalten und so Zeit und Aufwand für die Unterstützung mehrsprachiger Formulare reduzieren. Weitere Informationen zu Übersetzung finden Sie im Abschnitt „Überlegungen“.
* **Multi-Site-Management und Live Copy:** AEM Sites bietet robuste [Fähigkeiten für die Verwaltung mehrerer Sites und Live Copys](/help/sites-cloud/administering/msm/overview.md), mit denen Sie mehrere Websites in einer Umgebung erstellen und verwalten können. Mit dieser Funktion können Sie nun Formulare über verschiedene Sites hinweg wiederverwenden, was Konsistenz gewährleistet und doppelte Arbeit vermeidet. Mit zentralisierter Kontrolle und Verwaltung können Sie Formulare effizient über mehrere Websites hinweg verwalten und aktualisieren.
* **Themen:** AEM Sites-Seiten bieten ein Framework für das Entwerfen und Verwalten konsistenter visueller Stile auf mehreren Web-Seiten. Diese definieren Farben, Schriftarten, Stylesheets und andere visuelle Elemente, die zum allgemeinen Look-and-Feel der Website beitragen. [Sie können die Designs verwenden, die für ein adaptives Formular einer AEM Sites-Seite entwickelt wurden, was Zeit und Mühe spart.](/help/sites-cloud/administering/site-creation/site-themes.md#using-site-themes-using-themes).
* **Tagging:** Mit AEM Sites-Seiten können Sie [Tags oder Beschriftungen zu einer Seite, einem Asset oder anderen Inhalten zuweisen](/help/implementing/developing/introduction/tagging-framework.md). Tags sind Keywords oder Metadatenbeschriftungen, die eine Möglichkeit bieten, Inhalte basierend auf bestimmten Kriterien zu kategorisieren und zu organisieren. Sie können Seiten, Assets oder anderen Inhaltselementen in AEM ein oder mehrere Tags zuweisen, um die Suche zu verbessern und die Assets zu kategorisieren.
* **Sperren und Entsperren von Inhalten:** Mit AEM Sites können Benutzerinnen und Benutzer in der AEM Sites-Umgebung [Zugriff und Änderungen auf Seiten steuern](/help/sites-cloud/authoring/page-editor/edit-content.md). Wenn eine Seite gesperrt ist, bedeutet dies, dass sie von anderen Benutzenden vor unbefugten Änderungen oder Bearbeitungen geschützt ist. Nur Benutzende, die den Inhalt gesperrt haben, oder Admins können ihn entsperren, um Änderungen zuzulassen.

Darüber hinaus verwenden adaptive Formulare im AEM-Seiteneditor die [Kernkomponenten für adaptive Formulare](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de#features). Diese Kernkomponenten bieten eine standardmäßige und einfachere Methode zum Formatieren und Anpassen der Komponenten, genau wie für [WCM-Komponenten für AEM Sites](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de).


## Wie erstelle oder füge ich ein adaptives Formular auf der AEM Sites-Seite oder in einem AEM Experience Fragment hinzu? {#various-options-to-creat-or-add-an-adaptive-form-in-aem-sites-page-or-aem-experience-fragment}

Sie können diese Funktion bestmöglich nutzen, indem Sie die folgenden Optionen verwenden:

* **[Erstellen und Hinzufügen eines benutzerdefinierten adaptiven Formulars zu einer AEM Sites-Seite](#create-an-adaptive-form-in-sites-editor-or-experience-fragment):** Sie können die Container-Komponente für adaptive Formulare verwenden, um ein brandneues Formular von Grund auf neu zu erstellen und es speziell auf Ihre Anforderungen und Design-Voreinstellungen anzupassen.

* **[Erstellen und Hinzufügen eines benutzerdefinierten adaptiven Formulars zu Experience Fragments](#create-an-adaptive-form-in-sites-editor):** Sie können die Reichweite Ihrer Formulare erweitern, indem Sie sie zu AEM Experience Fragments hinzufügen, wodurch eine nahtlose Wiederverwendung über mehrere Seiten oder Sites hinweg ermöglicht wird.

* **[Konvertieren eines adaptiven Formulars in ein Experience Fragment](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment):** Konvertieren Sie ein adaptives Formular, das zu einer AEM Sites-Seite hinzugefügt wurde, in ein Experience Fragment, um das Formular auf mehreren AEM Sites-Seiten wiederverwenden zu können.

* **[Erstellen und Hinzufügen von Formularen basierend auf genehmigten Vorlagen zu einer AEM Sites-Seite:](/help/forms/embed-adaptive-form-aem-sites.md#embed-form-using-adaptive-form-wizzard-aem-sites)** Sie können vorab genehmigte Vorlagen nutzen, um schnell adaptive Formulare zu erstellen, die den Branding-Richtlinien und Design-Standards Ihres Unternehmens entsprechen. Die Option ist nur für adaptive Formulare verfügbar, die mit dem Editor oder der Einbettungskomponente für adaptive Formulare erstellt wurde.

* **[Hinzufügen von vorhandenen Formularen zu einer AEM Sites-Seite:](/help/forms/embed-adaptive-form-aem-sites.md#embed-an-adaptive-form-in-sites-editor)** Sie können bereits erstellte Formulare einfach in Ihre Websites integrieren, sodass Besucherinnen und Besucher direkt mit ihnen interagieren können. Die Option ist nur für adaptive Formulare verfügbar, die mit dem Editor oder der Einbettungskomponente für adaptive Formulare erstellt wurde.


* **Hinzufügen von mehreren Formularen zu einer AEM Sites-Seite oder einem Experience Fragment:** Sie können mehrere adaptive Formulare erstellen oder zu einer AEM Sites-Seite hinzufügen, um Benutzenden basierend auf ihren Vorlieben und Anforderungen mehrere Optionen zur Verfügung zu stellen. Dies kann eine Kombination aus neuen und vorhandenen Formularen sein. Sie können die Komponente **[!UICONTROL Container für adaptive Formulare]** mehrfach verwenden, um einer AEM Sites-Seite adaptive Formulare hinzuzufügen. Sie können **[!UICONTROL Adaptive Formulare – Einbettungskomponente]** nur dann mehrfach auf einer AEM Sites-Seite verwenden, wenn die Option **[!UICONTROL Formular deckt die gesamte Breite des Rahmens ab]** ausgewählt ist. Falls die Option **[!UICONTROL Formular deckt die gesamte Breite des Rahmens ab]** nicht aktiviert ist, unterstützt die AEM Sites-Seite nur ein adaptives Formular ohne iFrame. Wählen Sie zum Hinzufügen mit der **[!UICONTROL Adaptive Formulare – Einbettungskomponente]** die Option **[!UICONTROL Formular deckt die gesamte Breite des Rahmens ab]** aus.

## Überlegungen zum Erstellen eines adaptiven Formulars auf einer AEM Sites-Seite oder in einem AEM Experience Fragment {#consideration}

* Wenn Sie den Container für adaptive Formulare verwenden, um ein Formular zu erstellen oder hinzuzufügen, werden die Formulare über den AEM Sites-Übersetzungsfluss übersetzt und lokalisiert. Für jede Sprache wird eine separate Kopie (Sprachkopie) der Sites-Seite und der entsprechenden Formulare generiert. Wenn Inhaltsautorinnen oder -autoren eine Regel in einem Formular auf der übergeordneten Seite ändern, müssen dieselben Änderungen in allen Sprachkopien des Formulars vorgenommen werden. Mit dem Container für adaptive Formulare können Sie auch verschiedene Funktionen von AEM Sites-Seiten verwenden, z. B. Versionierung, Targeting, Übersetzung und Multi-Site Manager.

* Wenn Sie ein Formular mithilfe der Einbettungskomponente für adaptive Formulare erstellen oder hinzufügen, werden die Formulare mithilfe des Übersetzungsflusses von AEM Forms übersetzt und lokalisiert. In diesem Fall wird ein einzelnes Formular beibehalten und in allen Sprachkopien der Sites-Seiten referenziert. Die Einbettungskomponente für adaptive Formulare bietet keinen Zugriff auf verschiedene Funktionen von AEM Sites-Seiten wie Versionierung, Targeting, Übersetzung und Multi-Site Manager.


## Anforderungen zum Erstellen oder Hinzufügen eines adaptiven Formulars auf einer AEM Sites-Seite oder in einem AEM Experience Fragment {#before-you-start-creating-an-adaptive-form}

Bevor Sie mit der Erstellung eines adaptiven Formulars beginnen, fügen Sie Ihrer AEM Sites-Seite adaptive Forms-Client-Bibliotheken hinzu:


### Hinzufügen von adaptiven Forms-Client-Bibliotheken zu Ihrer AEM Sites-Seite oder Ihrem Erlebnis

**1. Fall: Verwenden separater Sites-Seitenkomponenten**

Um die vollständige Funktionalität der Container-Komponente für adaptive Formulare zu aktivieren, fügen Sie die Client-Bibliotheken „customHeaderlibs“ und „customfooterlibs“ mithilfe der Bereitstellungs-Pipeline zu Ihrer AEM Sites-Seite hinzu. So werden die Bibliotheken hinzugefügt:

1. Greifen Sie auf Ihr [AEM Cloud Service-Git-Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/repositories.html?lang=de) zu und klonen Sie es.
1. Öffnen Sie den Ordner „AEM Cloud Service-Git-Repository“ in einem einfachen Texteditor. Beispielsweise Microsoft Visual Code.
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

>[!NOTE]
>
> Die benutzerdefinierte Funktion der Client-Bibliothek wird nur dann hartcodiert, wenn sie für alle Formulare erforderlich ist. Fügen Sie Bibliotheken, die sich je nach Formulartyp unterscheiden, über Vorlagenseitenrichtlinien hinzu, wie im nächsten Abschnitt erläutert.

**Fall 2: Verwenden derselben Sites-Seitenkomponente**

Schließen Sie die Laufzeitclientbibliotheken oder die benutzerdefinierten Funktionsbibliotheken in die Seitenrichtlinie der Vorlage ein, die zum Erstellen von Seiten mit Formularen verwendet wird.

1. Öffnen Sie die AEM Sites-Seite oder das Experience Fragment zur Bearbeitung. Um die Seite zur Bearbeitung zu öffnen, wählen Sie die Seite aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.
2. Öffnen Sie die Vorlage Ihrer Sites- oder Experience Fragment-Seite. Um die Vorlage zu öffnen, navigieren Sie zu **[!UICONTROL Seiteninformationen]** ![Seiteninformationen](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Vorlage bearbeiten]**. Dadurch wird die entsprechende Vorlage im Vorlageneditor geöffnet.
3. Gehen Sie zum **[!UICONTROL Seiteninformationen]** ![Seiteninformationen](/help/forms/assets/Smock_Properties_18_N.svg) der Vorlage und wählen Sie die Option **[!UICONTROL Seitenrichtlinie]** aus. Dadurch werden die Eigenschaften der AEM Sites-Vorlage geöffnet, in der Sie benutzerdefinierte Funktionen oder Laufzeit-Client-Bibliotheken definieren können.
4. Klicken Sie auf der Registerkarte **[!UICONTROL Eigenschaften]** auf die Schaltfläche **[!UICONTROL Hinzufügen]**, um neue benutzerdefinierte Funktionsbibliotheken für die Laufzeitbibliotheken hinzuzufügen.
5. Klicken Sie auf **[Fertig]**.

>[!VIDEO](https://video.tv.adobe.com/v/3476178?quality=12&learn=on)

### Aktivieren des Containers für adaptive Formulare für eine AEM Sites-Seite oder ein Experience Fragment

Um die Komponente [!UICONTROL Container für adaptive Formulare] in der Richtlinie der Vorlage zu aktivieren, führen Sie die folgenden Schritte aus:

1. Öffnen Sie die AEM Sites-Seite oder das Experience Fragment zur Bearbeitung. Um die Seite zur Bearbeitung zu öffnen, wählen Sie die Seite aus und klicken Sie auf „Bearbeiten“.
1. Öffnen Sie die Vorlage Ihrer Sites- oder Experience Fragment-Seite. Um die Vorlage zu öffnen, navigieren Sie zu [!UICONTROL Seiteninformationen] ![Seiteninformationen](/help/forms/assets/Smock_Properties_18_N.svg) > [!UICONTROL Vorlage bearbeiten]. Dadurch wird die entsprechende Vorlage im Vorlageneditor geöffnet.
1. Klicken Sie in der Strukturansicht auf das Symbol **[!UICONTROL Richtlinie]** ![Richtlinie](/help/forms/assets/Smock_FeedManagement_18_N.svg) in der Menüleiste. Klicken Sie auf die Liste **[!UICONTROL Zulässige Komponenten]** und aktivieren Sie das Kontrollkästchen **[!UICONTROL Container für adaptive Formulare]** unter **[AEM-Projektarchetyp-Name] – Adaptives Formular**.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

## Erstellen eines adaptiven Formulars {#create-an-adaptive-form-in-sites-editor-or-experience-fragment}

Sie können ein brandneues Formular direkt auf einer AEM Sites-Seite oder im Experience Fragment von Grund auf neu erstellen und es speziell an Ihre Anforderungen und Design-Voreinstellungen anpassen. Bei Formularen mit nur einem Verwendungszweck wird empfohlen, eine AEM Sites-Seite direkt zu erstellen, während Experience Fragments sich ideal für Formulare eignen, die auf mehreren Seiten auf Ihrer Website wiederverwendet werden müssen.

* [Erstellen eines Formulars auf einer AEM Sites-Seite](#create-an-adaptive-form-in-sites-editor)
* [Erstellen eines Formulars in einem Experience Fragment](#create-an-adaptive-form-in-experience-fragment)
* [Konvertieren eines adaptiven Formulars auf einer AEM-Sites-Seite zu einem Experience Fragment](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment)

### Erstellen eines Formulars auf einer AEM Sites-Seite {#create-an-adaptive-form-in-sites-editor}

Sie können die Container-Komponente für adaptive Formulare im AEM-Seiteneditor verwenden, um ein benutzerdefiniertes Formular zu erstellen. Mit der Komponente können Sie ein Formular erstellen, indem Sie die Formularkomponenten per Drag-and-Drop verschieben. Die Formularkomponenten basieren auf Kernkomponenten. Sie können diese einfach entsprechend den Anforderungen Ihrer Organisation anpassen.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

So erstellen Sie ein adaptives Formular auf einer Sites-Seite:

1. Öffnen Sie die AEM Sites-Seite im Bearbeitungsmodus.
1. Ziehen Sie die Container-Komponente für **[!UICONTROL adaptive Formulare]** vom Komponenten-Browser per Drag-and-Drop zur Sites-Seite. Dadurch wird Platz auf der Seite für das Formular erstellt. Sie können den Layout-Modus verwenden, um die Größe des Container-Bereichs zu ändern.
1. Ziehen Sie Kernkomponenten des adaptiven Formulars per Drag-and-Drop in den Container-Bereich, um das Formular zu erstellen.
1. Fügen Sie die Schaltfläche „Senden“ hinzu.

Legen Sie als Nächstes die [Aktion „Senden“](#configure-submit-action-for-form) und erweiterte Eigenschaften fest.

### Erstellen eines Formulars in einem Experience Fragment {#create-an-adaptive-form-in-experience-fragment}

Sie können die Reichweite Ihrer Formulare erweitern, indem Sie sie zu AEM Experience Fragments hinzufügen, wodurch eine nahtlose Wiederverwendung über mehrere Seiten oder Sites hinweg ermöglicht wird. Sie können beispielsweise ein Newsletter-Anmeldeformular in ein Experience Fragment einfügen. Dadurch können Sie das Fragment bequem über mehrere Seiten Ihrer Website hinweg wiederverwenden, sodass das Formular nicht wiederholt neu erstellt werden muss. Alle Aktualisierungen oder Änderungen, die im Experience Fragment am Newsletter-Anmeldeformular vorgenommen werden, werden automatisch auf alle Seiten übertragen, auf denen es verwendet wird. Dadurch wird der Prozess optimiert und ein nahtloses Benutzererlebnis bei gleichzeitiger Vereinfachung der Verwaltung von Formularen auf Ihrer Website sichergestellt.

So erstellen Sie ein adaptives Formular in einem Experience Fragment:

1. Öffnen Sie ein Experience Fragment.
1. Ziehen Sie die Container-Komponente für **[!UICONTROL adaptive Formulare]** vom Komponenten-Browser per Drag-and-Drop zum Experience Fragment.
1. Ziehen Sie Kernkomponenten des adaptiven Formulars per Drag-and-Drop in den Container-Bereich im Experience Fragment, um das Formular zu erstellen.
1. Fügen Sie die Schaltfläche „Senden“ hinzu.

Legen Sie als Nächstes die [Aktion „Senden“](#configure-submit-action-for-form) und erweiterte Eigenschaften fest.

### Konvertieren eines Formulars auf einer AEM Sites-Seite in ein Experience Fragment {#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment}

Sie können ein vorhandenes adaptives Formular in einem Sites-Seiteneditor in ein Experience Fragment konvertieren, um es auf mehreren Seiten oder Sites wiederzuverwenden.

So konvertieren Sie ein adaptives Formular auf einer AEM Sites-Seite in ein Experience Fragment:

1. Öffnen Sie die AEM Sites-Seite mit dem adaptiven Formular (in der Komponente „Container für adaptive Formulare“) im Bearbeitungsmodus.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]**, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formulare hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.
1. Wählen Sie in der Menüleiste das ![In Experience Fragment konvertieren-Symbol](/help/forms/assets/Smock_FilingCabinet_18_N.svg) Symbol „In Experience Fragment-Variante konvertieren“ aus.
   ![Klicken des Archivlogos, um ein adaptives Formular in einer AEM Sites-Seite in ein Experience Fragment zu konvertieren](/help/forms/assets/convert-form-in-sites-page-to-an-experience-fragment.png)

   Es wird ein Dialogfeld zum Konvertieren des Containers für adaptive Formulare in ein neues Experience Fragment oder zu dessen Hinzufügen zu einem vorhandenen Experience Fragment angezeigt.
1. Legen Sie im Dialogfeld „In Experience Fragment-Variante konvertieren“ Werte für die folgenden Optionen fest:

   * **Aktion:** Wählen Sie diese Option aus, um ein Experience Fragment zu erstellen oder zu einem vorhandenen Experience Fragment hinzuzufügen.
   * **Übergeordneter Pfad:** Geben Sie den Pfad des Ordners an, in dem das Experience Fragment gehostet werden soll. Die Option ist nur zum Erstellen eines Experience Fragments verfügbar.
   * **Vorlage:** Geben Sie den Pfad der Experience Fragment-Vorlage an. Wenn Sie keine Experience Fragment-Vorlage haben, [erstellen Sie eine](/help/implementing/developing/extending/experience-fragments.md). Die Option ist nur zum Hinzufügen des adaptiven Formulars zu einem vorhandenen Experience Fragment verfügbar.
   * **Fragmenttitel:** Geben Sie den Titel des Experience Fragments an. Der Titel identifiziert ein Experience Fragment eindeutig.


## Konfigurieren der Sendeaktion für ein Formular auf einer AEM Sites-Seite oder in einem Experience Fragment {#configure-submit-action-for-form}

Mit einer Übermittlungsaktion können Sie das Ziel der Daten auswählen, die über ein adaptives Formular erfasst werden. Eine Übermittlungsaktion wird ausgelöst, wenn eine Benutzerin bzw. ein Benutzer in einem adaptiven Formular auf die Schaltfläche „Senden“ klickt. Adaptive Formulare enthalten einige vordefinierte Sendeaktionen. Sie können außerdem die standardmäßigen Sendeaktionen erweitern, um Ihre eigene benutzerdefinierte Sendeaktion zu erstellen. So konfigurieren Sie eine Sendeaktion für Ihr Formular:

1. Öffnen Sie den AEM Seiten-Editor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]**, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formulare hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg). Das Dialogfeld des Containers für adaptive Formulare zum Konfigurieren von Sendeaktionen wird geöffnet.
   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld „Container für ein adaptives Formular“ zu öffnen und eine Übermittlungsaktion für ein adaptives Formular zu konfigurieren.](/help/forms/assets/adaptive-forms-container.png)
1. Wählen Sie je nach Ihren Anforderungen eine Sendeaktion aus und konfigurieren Sie sie. Detaillierte Informationen zu Sendeaktionen finden Sie unter [Sendeaktion für adaptive Formulare](/help/forms/configuring-submit-actions.md)


## Konfigurieren eines Schemas oder Formulardatenmodells (FDM) für ein Formular auf einer AEM Sites-Seite oder in einem Experience Fragment {#configure-schema-or-data-model-for-form}

Sie können das Formulardatenmodell (FDM) verwenden, um ein Formular mit einer Datenquelle zu verbinden und Daten basierend auf Benutzeraktionen zu senden und zu empfangen. Sie können auch ein Formular mit einem JSON-Schema verbinden, um die gesendeten Daten in einem vordefinierten Format zu empfangen. Verbinden Sie Ihr Formular je nach Anforderung mit einem JSON-Schema oder Formulardatenmodell (FDM):

* [Erstellen Sie ein JSON-Schema und laden Sie es in Ihre Umgebung hoch](/help/forms/adaptive-form-json-schema-form-model.md) oder
* [Erstellen eines Formulardatenmodells (FDM)](/help/forms/create-form-data-models.md)

So konfigurieren Sie ein JSON-Schema oder ein Formulardatenmodell (FDM) für Ihr Formular:

1. Öffnen Sie den AEM Seiten-Editor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]**, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formulare hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg). Das Dialogfeld der Container für adaptive Formulare zum Konfigurieren von Datenmodellen wird geöffnet.
   ![Klicken Sie auf das Schraubenschlüsselsymbol, um Datenmodelle für das adaptive Formular zu konfigurieren.](/help/forms/assets/form-data-model-adaptive-forms-container.png)
1. Wählen Sie ein JSON-Schema oder ein Formulardatenmodell (FDM) aus und konfigurieren Sie es entsprechend Ihren Anforderungen. Detaillierte Informationen zu Sendeaktionen finden Sie unter [Sendeaktion für adaptive Formulare](/help/forms/configuring-submit-actions.md).

   * Wenn Sie die Option **[!UICONTROL Formularmodell]** wählen, können Sie mit der Option **[!UICONTROL Formulardatenmodell auswählen]** ein vorkonfiguriertes Formulardatenmodell (FDM) auswählen.
   * Wenn Sie die Option **[!UICONTROL Schema]** wählen, verwenden Sie die Option **[!UICONTROL Schema]**, um ein JSON-Schema für Ihr Formular auszuwählen.

1. Klicken Sie auf **[!UICONTROL Fertig]**.

## Konfigurieren eines Vorbefüllungsdienstes für ein Formular auf einer AEM Sites-Seite oder in einem Experience Fragment {#configure-prefill-service-for-form}

Sie können den Vorbefüllungsdienst verwenden, um Felder eines adaptiven Formulars automatisch mit vorhandenen Daten auszufüllen. Wenn eine Benutzerin oder ein Benutzer ein Formular öffnet, sind die Werte für diese Felder schon vorbefüllt. Sie haben folgende Möglichkeiten:

* [Erstellen eines benutzerdefinierten Vorbefüllungsdienstes](/help/forms/prepopulate-adaptive-form-fields.md)
* [Verwenden des Vorbefüllungsdienstes für Formulardatenmodelle](#fdm-prefill-service)

### Verwenden Sie den Vorbefüllungsdienst für Formulardatenmodelle, um Felder eines Formulars auf der AEM Sites-Seite oder im Experience Fragment vorab auszufüllen. {#fdm-prefill-service}

Sie können den Vorbefüllungsdienst für Formulardatenmodelle verwenden, um Felder eines adaptiven Formulars auf der AEM Sites-Seite oder im Experience Fragment mit einem Formulardatenmodell oder einem benutzerdefinierten Vorbefüllungsdienst im Voraus auszufüllen. Der Vorbefüllungsdienst für das Formulardatenmodell verwendet den [Get-Dienst des konfigurierten Formulardatenmodells](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) zum Abrufen von Daten. So verwenden Sie für ein adaptives Formular den Vorbefüllungsdienst für Formulardatenmodelle:

1. Öffnen Sie den AEM Seiten-Editor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]**, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formulare hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg). Das Dialogfeld der Container für adaptive Formulare zum Konfigurieren von Datenmodellen wird geöffnet.
   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld „Container für ein adaptives Formular“ zu öffnen und den Vorbefüllungsdienst für das adaptive Formular zu konfigurieren](/help/forms/assets/adaptive-forms-container.png)
1. Wählen Sie ein Formulardatenmodell aus. Öffnen Sie die Registerkarte **[!UICONTROL Allgemein]**. Wählen Sie im Vorbefüllungsdienst die Option **[!UICONTROL Vorbefüllungsdienst für Formulardatenmodell]**.
1. Klicken Sie auf **[!UICONTROL Fertig]**. Ihr adaptives Formular ist jetzt so konfiguriert, dass es die Vorbefüllung für Formulardatenmodelle verwendet. Sie können nun den [Regeleditor](rule-editor.md) verwenden, um Regeln zu erstellen, nach denen Felder des Formulars vorausgefüllt werden.


## Leiten Sie bei der Formularübermittlung die Benutzenden auf eine Seite um oder zeigen Sie eine Dankesnachricht an

Beim Senden eines Formulars können Sie die Benutzenden zu einer anderen Web-Seite oder Nachricht umleiten. So leiten Sie die Benutzenden um oder konfigurieren die Dankesnachricht:

1. Öffnen Sie den AEM Seiten-Editor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]**, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formulare hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.

1. Öffnen Sie die Registerkarte **[!UICONTROL Übermittlung]**.

   * Wählen Sie zum Konfigurieren einer Umleitungs-URL für die Senden-Option die Option **[!UICONTROL Zu URL umleiten]** aus, durchsuchen Sie eine AEM Sites-Seite und wählen Sie sie aus oder geben Sie die URL einer externen Seite an.
   * Wählen Sie zum Konfigurieren einer benutzerdefinierten Nachricht oder einer Dankesnachricht für die Senden-Option die Option **[!UICONTROL Nachricht anzeigen]** und geben Sie im Feld **[!UICONTROL Nachrichteninhalt]** eine Nachricht ein. Es handelt sich um ein Rich-Text-Feld. Sie können die Vollbildoption verwenden, um alle verfügbaren Rich-Text-Elemente anzuzeigen.


