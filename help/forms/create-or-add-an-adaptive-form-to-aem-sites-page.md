---
title: Wie wird ein adaptives Formular zur AEM Sites-Seite hinzugefügt?
description: Erfahren Sie, wie Sie ein adaptives Formular erstellen oder zu Ihrer AEM Sites-Seite hinzufügen. Lernen Sie auch die Vorteile und verschiedene Möglichkeiten kennen, Formulare in Ihre Website zu integrieren.
feature: Adaptive Forms, Page Editor, Authoring
Keywords: AF in Sites editor, af in aem sites, aem sites af, add af to a sites page, af aem sites, af sites, create af in a sites page, adaptive form in aem sites, forms aem sites, add form to a sites page, adaptive forms aem sites, add adaptive forms to aem page, create forms in an aem sites page
source-git-commit: ecc881ac1a9f8dd98cd57bbeb44cc35deddcbb8e
workflow-type: tm+mt
source-wordcount: '3214'
ht-degree: 2%

---


# Hinzufügen eines adaptiven Formulars zu einer AEM Sites-Seite oder einem Experience Fragment {#create-or-add-an-adaptive-form-to-aem-sites-page}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/create-or-add-an-adaptive-form-to-aem-sites-page.html) |
| AEM as a Cloud Service | Dieser Artikel |

Mit AEM Forms können Sie Ihrer AEM Sites-Seite nahtlos ein Formular hinzufügen. Dadurch können Ihre Besucher bequem Formulare ausfüllen und senden, ohne jemals die Seite verlassen zu müssen, auf der sie sich befinden. Dadurch können sie mühelos mit anderen Elementen der Website interagieren und gleichzeitig aktiv mit dem Formular interagieren.

Mit AEM Seiteneditor können Sie schnell mehrere Formulare erstellen und zu Ihren AEM Sites-Seiten hinzufügen. Mit AEM Seiteneditor können Inhaltsautoren nahtlose Erlebnisse zur Datenerfassung auf einer Sites-Seite erstellen, indem sie die Leistung adaptiver Formularkomponenten nutzen, einschließlich dynamischem Verhalten, Überprüfungen, Datenintegration, Generierung von Datensatzdokumenten und Automatisierung von Geschäftsprozessen. Außerdem können Sie damit verschiedene Funktionen von AEM Sites-Seiten verwenden, z. B. Versionierung, Targeting, Übersetzung und Multi-Site-Manager.

AEM Forms Cloud Service bietet Container für adaptive Formulare und Komponenten für adaptive Forms - Einbetten. Sie können den Container für adaptive Formulare verwenden, um ein neues Formular auf einer AEM Sites-Seite oder in einem Experience Fragment zu erstellen, während Sie mit der Komponente Adaptive Forms - Embed ein vorhandenes adaptives Formular hinzufügen oder ein neues Formular mit dem Adaptive Forms Editor erstellen können.

![Beispiel eines adaptiven Formulars auf einer AEM Sites-Seite](/help/forms/assets/adaptive-form-in-sites-page.png)

## Warum verwenden Sie Adaptive Forms-Kernkomponenten, um ein adaptives Formular auf der AEM Sites-Seite oder im Experience Fragment zu erstellen?

Wenn Sie in der Vergangenheit adaptive Forms Foundation-Komponenten oder einfache HTML-basierte Formulare für Ihre Sites erstellt haben, empfiehlt Adobe, adaptive Forms-Kernkomponenten zu verwenden, um ein adaptives Formular auf der AEM Sites-Seite oder im Experience Fragment zu erstellen. Es ermöglicht Ihnen die Verwendung verschiedener Funktionen von AEM Sites-Seiten wie Versionierung, Targeting, Übersetzung und Multi-Site-Manager, wodurch die Erstellung und Verwaltung von Formularen für die adaptive Forms verbessert wird. Sehen wir uns einige dieser Funktionen an:

* **Versionierung:** AEM Sites-Seitenangebot [robuste Versionierungsfunktionen](/help/sites-cloud/authoring/features/page-versions.md), mit dem Sie verschiedene Versionen Ihrer Formulare verfolgen und verwalten können. Dadurch können Sie Änderungen und Verbesserungen an Formularen vornehmen und gleichzeitig bei Bedarf frühere Versionen wiederherstellen. Die Versionierung stellt einen kontrollierten und organisierten Ansatz für die Formularentwicklung und -entwicklung sicher.
* **Targeting (Integration mit Adobe Target):** Mit den Targeting-Funktionen von AEM Sites-Seiten können Sie auch [das Formularerlebnis für verschiedene Zielgruppen personalisieren](/help/sites-cloud/integrating/integration-adobe-target-ims.md). Mithilfe von Benutzersegmenten und Targeting-Kriterien können Sie den Inhalt, das Design oder das Verhalten des Formulars an bestimmte Benutzergruppen anpassen. Auf diese Weise können Sie ein personalisiertes und relevantes Formularerlebnis bereitstellen und die Interaktions- und Konversionsraten steigern.
* **Übersetzung:** AEM Sites [nahtlose Integration mit Übersetzungsdiensten](/help/sites-cloud/administering/translation/overview.md), sodass Sie Formulare einfach in mehrere Sprachen übersetzen können. Diese Funktion vereinfacht den Lokalisierungsprozess und stellt sicher, dass Ihre Formulare für eine globale Zielgruppe zugänglich sind. Sie können Übersetzungen effizient in AEM Übersetzungsprojekten verwalten und so Zeit und Aufwand für die Unterstützung mehrsprachiger Formulare reduzieren. Weitere Informationen zur Übersetzung finden Sie im Abschnitt Überlegungen .
* **Multi-Site-Management und Live Copy:** AEM Sites bietet eine robuste [Funktionen für die Verwaltung mehrerer Sites und die Live Copy](/help/sites-cloud/administering/msm/overview.md), mit dem Sie mehrere Websites in einer Umgebung erstellen und verwalten können. Mit dieser Funktion können Sie jetzt Formulare über verschiedene Sites hinweg wiederverwenden, um Konsistenz zu gewährleisten und doppelte Arbeit zu vermeiden. Mit zentralisierter Kontrolle und Verwaltung können Sie Formulare effizient über mehrere Websites hinweg verwalten und aktualisieren.
* **Themen:** AEM Sites-Seiten bieten ein Framework für das Entwerfen und Verwalten konsistenter visueller Stile auf mehreren Webseiten. Diese definieren Farben, Schriftarten, Stylesheets und andere visuelle Elemente, die zum allgemeinen Erscheinungsbild der Website beitragen. [Sie können die Designs verwenden, die für eine AEM Sites-Seite für ein adaptives Formular entwickelt wurden, wodurch Zeit und Mühe gespart werden.](/help/sites-cloud/administering/site-creation/site-themes.md#using-site-themes-using-themes).
* **Tagging:** Mit AEM Sites-Seiten können Sie [Zuweisen von Tags oder Beschriftungen zu einer Seite, einem Asset oder anderen Inhalten](/help/implementing/developing/introduction/tagging-framework.md). Tags sind Suchbegriffe oder Metadatenbeschriftungen, mit denen Inhalte basierend auf bestimmten Kriterien kategorisiert und organisiert werden können. Sie können Seiten, Assets oder anderen Inhaltselementen in AEM ein oder mehrere Tags zuweisen, um die Suche zu verbessern und die Assets zu kategorisieren.
* **Sperren und Entsperren von Inhalten:** Mit AEM Sites können Benutzer [Zugriff und Änderungen auf Seiten steuern](/help/sites-cloud/authoring/fundamentals/editing-content.md) in der AEM Sites-Umgebung. Wenn eine Seite gesperrt ist, bedeutet dies, dass sie von anderen Benutzern vor unbefugten Änderungen oder Bearbeitungen geschützt ist. Nur der Benutzer, der den Inhalt gesperrt hat, oder ein Administrator kann ihn entsperren, um Änderungen zuzulassen.

Darüber hinaus wird Adaptive Forms in AEM Seiteneditor verwendet [Adaptive Forms-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de#features). Diese Kernkomponenten bieten eine standardmäßige und einfachere Methode zum Formatieren und Anpassen der Komponenten, die mit dem Szenario [AEM Sites WCM-Komponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de).


## Erstellen oder Hinzufügen eines adaptiven Formulars auf der AEM Sites-Seite oder AEM Experience Fragment? {#various-options-to-creat-or-add-an-adaptive-form-in-aem-sites-page-or-aem-experience-fragment}

Sie können diese Funktion voll nutzen, indem Sie die folgenden Optionen verwenden:

* **[Erstellen und Hinzufügen eines benutzerdefinierten adaptiven Formulars zu einer AEM Sites-Seite](#create-an-adaptive-form-in-sites-editor-or-experience-fragment):** Sie können die Container-Komponente für adaptive Formulare verwenden, um ein brandneues Formular von Grund auf neu zu erstellen und es speziell auf Ihre Anforderungen und Design-Voreinstellungen anzupassen.

* **[Erstellen und Hinzufügen eines benutzerdefinierten adaptiven Formulars zu einem Experience Fragments](#create-an-adaptive-form-in-sites-editor):** Sie können die Reichweite Ihrer Formulare erweitern, indem Sie sie zu AEM Experience Fragments hinzufügen, wodurch eine nahtlose Wiederverwendung über mehrere Seiten oder Sites hinweg ermöglicht wird.

* **[Konvertieren eines adaptiven Formulars in Experience Fragment](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment):** Konvertieren Sie ein adaptives Formular, das zu einer AEM Sites-Seite hinzugefügt wurde, in ein Experience Fragment, um das Formular auf mehreren AEM Sites-Seiten wiederzuverwenden.

* **Fügen Sie einer AEM Sites-Seite oder einem Experience Fragment mehrere Formulare hinzu:**  Sie können mehrere adaptive Forms erstellen oder zu einer AEM Sites-Seite hinzufügen, um Benutzern basierend auf ihren Voreinstellungen und Anforderungen mehrere Optionen zur Verfügung zu stellen. Diese können eine Kombination aus neuen und vorhandenen Formularen darstellen.

* **Erstellen Sie Formulare basierend auf genehmigten Vorlagen und fügen Sie sie einer AEM Sites-Seite hinzu:** Sie können vorab genehmigte Vorlagen nutzen, um schnell Adaptive Forms zu erstellen, die den Branding-Richtlinien und Designstandards Ihres Unternehmens entsprechen. Die Option ist nur für adaptive Forms verfügbar, die mit dem Adaptiven Forms-Editor oder der Adaptiven Forms - Einbettungskomponente erstellt wurde.

* **Fügen Sie vorhandene Formulare zu einer AEM Sites-Seite hinzu:** Sie können bereits erstellte Formulare einfach in Ihre Websites integrieren, sodass Besucher direkt mit ihnen interagieren können. Die Option ist nur für adaptive Forms verfügbar, die mit dem Adaptiven Forms-Editor oder der Adaptiven Forms - Einbettungskomponente erstellt wurde.

## Überlegungen zum Erstellen eines adaptiven Formulars auf der AEM Sites-Seite oder AEM Experience Fragment {#consideration}

* Wenn Sie den Container für adaptive Formulare verwenden, um ein Formular zu erstellen oder hinzuzufügen, werden die Formulare über den AEM Sites-Übersetzungsfluss übersetzt und lokalisiert. Für jede Sprache wird eine separate Kopie (Sprachkopie) der Siteseite und der entsprechenden Formulare generiert. Wenn ein Inhaltsautor eine Regel in einem Formular auf der übergeordneten Seite ändert, müssen dieselben Änderungen in allen Sprachkopien des Formulars vorgenommen werden. Mit dem Container für adaptive Formulare können Sie auch verschiedene Funktionen von AEM Sites-Seiten verwenden, z. B. Versionierung, Targeting, Übersetzung und Multi-Site-Manager.

* Wenn Sie ein Formular mithilfe der Einbettungskomponente für adaptive Formulare erstellen oder hinzufügen, werden die Formulare mithilfe des AEM Forms-Übersetzungsflusses übersetzt und lokalisiert. In diesem Fall wird ein einzelnes Formular beibehalten und in allen Sprachkopien der Sites-Seiten referenziert. Die Einbettungskomponente für adaptive Formulare bietet keinen Zugriff auf verschiedene Funktionen von AEM Sites-Seiten wie Versionierung, Targeting, Übersetzung und Multi-Site-Manager.


## Anforderungen zum Erstellen oder Hinzufügen eines adaptiven Formulars auf der AEM Sites-Seite oder AEM Experience Fragment {#before-you-start-creating-an-adaptive-form}

Bevor Sie mit der Erstellung eines adaptiven Formulars beginnen, aktivieren Sie die Kernkomponenten des adaptiven Forms und fügen Sie Ihrer AEM Sites-Seite Adaptive Forms-Client-Bibliotheken hinzu:

+++  Aktivieren der adaptiven Forms-Kernkomponenten für Ihre AEM Cloud Service-Umgebung

Stellen Sie sicher, dass [Adaptive Forms-Kernkomponenten sind für Ihre as a Cloud Service AEM Forms-Umgebung aktiviert](enable-adaptive-forms-core-components.md).

+++

+++  Adaptive Forms-Client-Bibliotheken zu Ihrer AEM Sites-Seite oder Ihrem Experience Fragment hinzufügen

Um die vollständige Funktionalität der Komponente Adaptiver Forms-Container zu aktivieren, fügen Sie die Client-Bibliotheken &quot;customHeaderlibs&quot;und &quot;customfooterlibs&quot;mithilfe der Bereitstellungs-Pipeline zu Ihrer AEM Sites-Seite hinzu. Hinzufügen der Bibliotheken:

1. Zugriff und Klonen Sie Ihre [AEM Cloud Service Git Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/repositories.html).
1. Öffnen Sie den Ordner &quot;AEM Cloud Service Git Repository&quot;in einem Texteditor für Pläne. Zum Beispiel Microsoft Visual Code.
1. Öffnen Sie die `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\customheaderlibs.html` und fügen Sie der Datei den folgenden Code hinzu:

       &quot;
       /Customheaderlibs.html
       &lt;sly data-sly-use.clientlib=&quot;core/wcm/components/commons/v1/templates/clientlib.html&quot;>
       &lt;sly data-sly-call=&quot;${clientlib.css @ categories=&amp;#39;core.forms.components.runtime.all&amp;#39;}&quot; />
       &lt;/sly>
       
       &quot;
   
1. Öffnen Sie die `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\customfooterlibs.html` und fügen Sie der Datei den folgenden Code hinzu:

       &quot;
       
       /customfooterlibs.html
       &lt;sly data-sly-use.clientlib=&quot;core/wcm/components/commons/v1/templates/clientlib.html&quot;>
       &lt;sly data-sly-test=&quot;${!wcmmode.edit}&quot; data-sly-call=&quot;${clientlib.js @ categories=&amp;#39;core.forms.components.runtime.all&amp;#39;, async=true}&quot; />
       &lt;/sly>
       &quot;
   
1. Öffnen Sie die `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\xfpage\customheaderlibs.html` und fügen Sie der Datei den folgenden Code hinzu:

       &quot;
       /Customheaderlibs.html
       &lt;sly data-sly-use.clientlib=&quot;core/wcm/components/commons/v1/templates/clientlib.html&quot;>
       &lt;sly data-sly-call=&quot;${clientlib.css @ categories=&amp;#39;core.forms.components.runtime.all&amp;#39;}&quot; />
       &lt;/sly>
       
       &quot;
   
1. Öffnen Sie die `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\xfpage\customfooterlibs.html` und fügen Sie der Datei den folgenden Code hinzu:

       &quot;
       
       /customfooterlibs.html
       &lt;sly data-sly-use.clientlib=&quot;core/wcm/components/commons/v1/templates/clientlib.html&quot;>
       &lt;sly data-sly-test=&quot;${!wcmmode.edit}&quot; data-sly-call=&quot;${clientlib.js @ categories=&amp;#39;core.forms.components.runtime.all&amp;#39;, async=true}&quot; />
       &lt;/sly>
       &quot;
   
1. [Ausführen der Bereitstellungspipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html?lang=de) , um die Client-Bibliotheken in Ihrer AEM as a Cloud Service Umgebung bereitzustellen.

+++

+++ Aktivieren des adaptiven Forms-Containers für Ihre AEM Sites-Seite oder Ihr Experience Fragment

Um die Komponente [!UICONTROL Container für adaptive Formulare] in der Richtlinie der Vorlage zu aktivieren, führen Sie die folgenden Schritte aus:

1. Öffnen Sie die AEM Sites-Seite oder das Experience Fragment zur Bearbeitung. Um die Seite zur Bearbeitung zu öffnen, wählen Sie die Seite aus und klicken Sie auf &quot;Bearbeiten&quot;.
1. Öffnen Sie die Vorlage Ihrer Sites- oder Experience Fragment-Seite. Um die Vorlage zu öffnen, navigieren Sie zum [!UICONTROL Seiteninformationen] ![Seiteninformationen](/help/forms/assets/Smock_Properties_18_N.svg) > [!UICONTROL Vorlage bearbeiten]. Dadurch wird die entsprechende Vorlage im Vorlageneditor geöffnet.
1. Klicken Sie in der Strukturansicht auf die **[!UICONTROL Politik]** ![Politik](/help/forms/assets/Smock_FeedManagement_18_N.svg) in der Menüleiste. Im **[!UICONTROL Zugelassene Komponenten]** und wählen Sie die **[!UICONTROL Adaptiver Forms-Container]**  Kontrollkästchen unter dem **[AEM Archetyp Projektname] - Adaptives Formular**.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

+++

## Erstellen eines adaptiven Formulars {#create-an-adaptive-form-in-sites-editor-or-experience-fragment}

Sie können ein brandneues Formular von Grund auf neu erstellen und es speziell an Ihre Anforderungen und Designvoreinstellungen anpassen, direkt auf einer AEM Sites-Seite oder im Experience Fragment. Bei Formularen mit nur einem Verwendungszweck wird empfohlen, eine AEM Sites-Seite direkt zu erstellen, während Experience Fragments sich ideal für Formulare eignen, die auf mehreren Seiten auf Ihrer Website wiederverwendet werden müssen.

* [Erstellen eines Formulars auf einer AEM Sites-Seite](#create-an-adaptive-form-in-sites-editor)
* [Erstellen eines Formulars in einem Experience Fragment](#create-an-adaptive-form-in-experience-fragment)
* [Konvertieren eines adaptiven Formulars auf der Seite &quot;AEM Sites&quot;in ein Experience Fragment](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment)

### Erstellen eines Formulars auf einer AEM Sites-Seite {#create-an-adaptive-form-in-sites-editor}

Sie können die Komponente Container für adaptive Formulare im Seiteneditor AEM verwenden, um ein benutzerdefiniertes Formular zu erstellen. Mit der Komponente können Sie ein Formular erstellen, indem Sie die Formularkomponenten per Drag &amp; Drop verschieben. Die Formularkomponenten basieren auf Kernkomponenten. Sie können diese einfach entsprechend den Anforderungen Ihrer Organisation anpassen.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

So erstellen Sie ein adaptives Formular auf einer Siteseite:

1. Öffnen Sie die AEM Sites-Seite im Bearbeitungsmodus.
1. Ziehen Sie die **[!UICONTROL Adaptiver Forms-Container]** -Komponente vom Komponenten-Browser zur Seite &quot;Sites&quot;hinzugefügt. Dadurch wird ein Leerzeichen auf der Seite für das Formular erstellt. Sie können den Layout-Modus verwenden, um die Größe des Containerraums zu ändern.
1. Ziehen Sie Kernkomponenten des adaptiven Formulars per Drag-and-Drop in den Container-Bereich, um das Formular zu erstellen.
1. Fügen Sie die Senden -Schaltfläche hinzu.

Als Nächstes [Festlegen der Sendeaktion](#configure-submit-action-for-form) und erweiterten Eigenschaften.

### Erstellen eines Formulars in einem Experience Fragment {#create-an-adaptive-form-in-experience-fragment}

Sie können die Reichweite Ihrer Formulare erweitern, indem Sie sie zu AEM Experience Fragments hinzufügen, wodurch eine nahtlose Wiederverwendung über mehrere Seiten oder Sites hinweg ermöglicht wird. Sie können beispielsweise ein Newsletter-Anmeldeformular in ein Experience Fragment einfügen. Auf diese Weise können Sie das Fragment bequem über mehrere Seiten Ihrer Website hinweg wiederverwenden, sodass das Formular nicht wiederholt neu erstellt werden muss. Alle Aktualisierungen oder Änderungen, die im Experience Fragment am Newsletter-Anmeldeformular vorgenommen werden, werden automatisch auf alle Seiten übertragen, auf denen es verwendet wird. Dadurch wird der Prozess optimiert und ein nahtloses Benutzererlebnis bei gleichzeitiger Vereinfachung der Verwaltung von Formularen auf Ihrer Website sichergestellt.

So erstellen Sie ein adaptives Formular in einem Experience Fragment:

1. Öffnen Sie ein Experience Fragment.
1. Ziehen Sie die **[!UICONTROL Adaptiver Forms-Container]** vom Komponenten-Browser zum Experience Fragment hinzugefügt.
1. Ziehen Sie Kernkomponenten des adaptiven Formulars per Drag-and-Drop in den Container-Bereich im Experience Fragment, um das Formular zu erstellen.
1. Fügen Sie die Senden -Schaltfläche hinzu.

Als Nächstes [Festlegen der Sendeaktion](#configure-submit-action-for-form) und erweiterten Eigenschaften.

### Konvertieren eines Formulars auf der Seite &quot;AEM Sites&quot;in ein Experience Fragment {#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment}

Sie können ein vorhandenes adaptives Formular in einem Sites-Seiten-Editor in ein Experience Fragment konvertieren, um das Formular auf mehreren Seiten oder Sites wiederzuverwenden.

So konvertieren Sie ein adaptives Formular auf der Seite &quot;AEM Sites&quot;in ein Experience Fragment:

1. Öffnen Sie die AEM Sites-Seite mit dem adaptiven Formular (in der Komponente Adaptiver Forms-Container ) im Bearbeitungsmodus.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie die **[!UICONTROL Adaptiver Forms-Container]** , das Ihr adaptives Formular hostet. Auf einer AEM Sites-Seite können mehrere adaptive Forms-Seiten gehostet werden. Wählen Sie daher sorgfältig den richtigen Adaptiven Forms-Container aus.
1. Wählen Sie in der Menüleiste die ![Symbol &quot;In Experience Fragment konvertieren&quot;](/help/forms/assets/Smock_FilingCabinet_18_N.svg) In Experience Fragment-Variantensymbol konvertieren.
   ![Klicken Sie auf das Dateiverwaltungs-Logo, um ein adaptives Formular in AEM Sites in ein Experience Fragment zu konvertieren.](/help/forms/assets/convert-form-in-sites-page-to-an-experience-fragment.png)

   Ein Dialogfeld zum Konvertieren des Containers für adaptive Formulare in ein neues Experience Fragment oder zum Hinzufügen zu einem vorhandenen Experience Fragment wird angezeigt
1. Legen Sie im Dialogfeld In Experience Fragment-Variante konvertieren Werte für die folgenden Optionen fest:

   * **Aktion:** Wählen Sie diese Option aus, um ein neues Experience Fragment zu erstellen oder zu einem vorhandenen Experience Fragment hinzuzufügen.
   * **Übergeordneter Pfad:** Geben Sie den Pfad des Ordners an, in dem das Experience Fragment gehostet werden soll. Die Option ist nur zum Erstellen eines neuen Experience Fragment verfügbar.
   * **Vorlage:** Geben Sie den Pfad der Experience Fragment-Vorlage an. Wenn Sie keine Experience Fragment-Vorlage haben, [erstellen](/help/implementing/developing/extending/experience-fragments.md). Die Option ist nur zum Hinzufügen des adaptiven Formulars zu einem vorhandenen Experience Fragment verfügbar.
   * **Fragmenttitel:** Geben Sie den Titel des Experience Fragment an. Der Titel identifiziert ein Experience Fragment eindeutig


## Konfigurieren der Sendeaktion für ein Formular auf einer AEM Sites-Seite oder in einem Experience Fragment {#configure-submit-action-for-form}

Mit einer Übermittlungsaktion können Sie das Ziel der Daten auswählen, die über ein adaptives Formular erfasst werden. Sie wird ausgelöst, wenn ein Benutzer in einem adaptiven Formular auf die Schaltfläche Senden klickt. Adaptive Formulare enthalten einige vordefinierte Übermittlungsaktionen. Sie können auch eine standardmäßige Übermittlungsaktion erweitern, um eine eigene benutzerdefinierte Übermittlungsaktion zu erstellen. So konfigurieren Sie eine Sendeaktion für Ihr Formular:

1. Öffnen Sie den AEM Seiten-Editor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie die **[!UICONTROL Adaptiver Forms-Container]** , das Ihr adaptives Formular hostet. Auf einer AEM Sites-Seite können mehrere adaptive Forms-Seiten gehostet werden. Wählen Sie daher sorgfältig den richtigen Adaptiven Forms-Container aus.
1. Klicken Sie auf die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg) Symbol. Das Dialogfeld Container für adaptive Formulare zum Konfigurieren von Sendeaktionen wird geöffnet.
   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld Container für adaptive Formulare zu öffnen, um die Übermittlungsaktion für ein adaptives Formular zu konfigurieren.](/help/forms/assets/adaptive-forms-container.png)
1. Wählen Sie je nach Ihren Anforderungen eine Übermittlungsaktion aus und konfigurieren Sie sie. Detaillierte Informationen zu Übermittlungsaktionen finden Sie unter [Übermittlungsaktion für adaptive Formulare](/help/forms/configuring-submit-actions.md)


## Schema oder Formulardatenmodell für ein Formular auf einer AEM Sites-Seite oder in einem Experience Fragment konfigurieren {#configure-schema-or-data-model-for-form}

Sie können das Formulardatenmodell verwenden, um ein Formular mit einer Datenquelle zu verbinden und Daten basierend auf Benutzeraktionen zu senden und zu empfangen. Sie können auch ein Formular mit einem JSON-Schema verbinden, um die gesendeten Daten in einem vordefinierten Format zu empfangen. Verbinden Sie basierend auf der Anforderung Ihr Formular mit einem JSON-Schema oder Formulardatenmodell:

* [Erstellen eines JSON-Schemas und Hochladen in Ihre Umgebung](/help/forms/adaptive-form-json-schema-form-model.md)  oder
* [Formulardatenmodell erstellen](/help/forms/create-form-data-models.md)

So konfigurieren Sie ein JSON-Schema oder ein Formulardatenmodell für Ihr Formular:

1. Öffnen Sie den AEM Seiten-Editor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie die **[!UICONTROL Adaptiver Forms-Container]** , das Ihr adaptives Formular hostet. Auf einer AEM Sites-Seite können mehrere adaptive Forms-Seiten gehostet werden. Wählen Sie daher sorgfältig den richtigen Adaptiven Forms-Container aus.
1. Klicken Sie auf die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg) Symbol. Das Dialogfeld Container für adaptive Formulare zum Konfigurieren von Datenmodellen wird geöffnet.
   ![Klicken Sie auf das Schraubenschlüsselsymbol, um Datenmodelle für das adaptive Formular zu konfigurieren.](/help/forms/assets/form-data-model-adaptive-forms-container.png)
1. Wählen Sie ein JSON-Schema oder ein Formulardatenmodell aus und konfigurieren Sie es entsprechend Ihren Anforderungen. Detaillierte Informationen zu Übermittlungsaktionen finden Sie unter [Übermittlungsaktion für adaptive Formulare](/help/forms/configuring-submit-actions.md).

   * Wenn Sie die **[!UICONTROL Formularmodell]** verwenden, verwenden Sie die **[!UICONTROL Formulardatenmodell auswählen]** -Option, um ein vorkonfiguriertes Formulardatenmodell auszuwählen.
   * Wenn Sie die **[!UICONTROL Schema]** verwenden, verwenden Sie die **[!UICONTROL Schema]** -Option, um ein JSON-Schema für Ihr Formular auszuwählen.

1. Klicken Sie auf **[!UICONTROL Fertig]**.

## Konfigurieren eines Vorbefüllungs-Dienstes für ein Formular auf einer AEM Sites-Seite oder in einem Experience Fragment {#configure-prefill-service-for-form}

Sie können den Vorbefüllungs-Dienst verwenden, um Felder eines adaptiven Formulars mit vorhandenen Daten automatisch auszufüllen. Wenn ein Benutzer ein Formular öffnet, werden die Werte für diese Felder vorbefüllt. Sie haben folgende Möglichkeiten:

* [Erstellen eines benutzerdefinierten Vorbefüllungs-Dienstes](/help/forms/prepopulate-adaptive-form-fields.md)
* [Vorfülldienst für Formulardatenmodell verwenden](#fdm-prefill-service)

### Verwenden Sie den Vorbefüllungs-Dienst für Formulardatenmodelle, um Felder eines Formulars auf der AEM Sites-Seite oder im Experience Fragment vorab auszufüllen. {#fdm-prefill-service}

Sie können den Vorbefüllungs-Dienst für Formulardatenmodelle verwenden, um Felder eines adaptiven Formulars auf der AEM Sites-Seite oder im Experience Fragment mit einem Formulardatenmodell oder einem benutzerdefinierten Vorbefüllungs-Dienst im Voraus auszufüllen. Der Vorbefüllungs-Dienst für Formulardatenmodelle verwendet die [Dienst für konfiguriertes Formulardatenmodell abrufen](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) , um Daten abzurufen. So verwenden Sie den Vorbefüllungs-Dienst für Formulardatenmodelle für ein adaptives Formular:

1. Öffnen Sie den AEM Seiten-Editor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie die **[!UICONTROL Adaptiver Forms-Container]** , das Ihr adaptives Formular hostet. Auf einer AEM Sites-Seite können mehrere adaptive Forms-Seiten gehostet werden. Wählen Sie daher sorgfältig den richtigen Adaptiven Forms-Container aus.
1. Klicken Sie auf die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg) Symbol. Das Dialogfeld Container für adaptive Formulare zum Konfigurieren von Datenmodellen wird geöffnet.
   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld Container für adaptive Formulare zu öffnen, um den Vorbefüllungs-Dienst für das adaptive Formular zu konfigurieren.](/help/forms/assets/adaptive-forms-container.png)
1. Formulardatenmodell auswählen. Öffnen Sie die **[!UICONTROL Allgemein]** Registerkarte. Wählen Sie im Vorbefüllungs-Dienst die Option **[!UICONTROL Vorfüllservice für Formulardatenmodell]**.
1. Klicken Sie auf **[!UICONTROL Fertig]**. Ihr adaptives Formular ist jetzt so konfiguriert, dass es das Vorfüllen des Formulardatenmodells verwendet. Sie können jetzt die [Regeleditor](rule-editor.md) , um Regeln zum Vorausfüllen von Formularfeldern zu erstellen.


## Leiten Sie den Benutzer auf eine Seite um oder zeigen Sie bei der Formularübermittlung eine Dankesnachricht an

Beim Senden eines Formulars können Sie den Benutzer zu einer anderen Webseite oder Nachricht umleiten. So leiten Sie den Benutzer um oder konfigurieren die Dankesnachricht:

1. Öffnen Sie den AEM Seiten-Editor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie die **[!UICONTROL Adaptiver Forms-Container]** , das Ihr adaptives Formular hostet. Auf einer AEM Sites-Seite können mehrere adaptive Forms-Seiten gehostet werden. Wählen Sie daher sorgfältig den richtigen Adaptiven Forms-Container aus.

1. Öffnen Sie die **[!UICONTROL Einsendung]** Registerkarte.

   * Um eine Umleitungs-URL zu konfigurieren, wählen Sie für die Option &quot;Beim Senden&quot;die Option **[!UICONTROL Zu URL umleiten]** und eine AEM Sites-Seite durchsuchen und auswählen oder die URL einer externen Seite angeben.

   * Um eine benutzerdefinierte Nachricht oder Dankesnachricht zu konfigurieren, wählen Sie für die Option &quot;Senden&quot;die Option **[!UICONTROL Nachricht anzeigen]** und geben Sie eine Nachricht im **[!UICONTROL Nachrichteninhalt]** ankreuzen. Dies ist ein Rich-Text-Feld. Sie können die Vollbildoption verwenden, um alle verfügbaren Rich-Text-Elemente anzuzeigen.

## Siehe Nächste

* [Erstellen von Stilen oder Designs für Ihre Formulare](using-themes-in-core-components.md)
* [Dynamisches Verhalten zu Formularen mithilfe des Regeleditors hinzufügen](rule-editor.md)
* [Festlegen des Layouts von Formularen für verschiedene Bildschirmgrößen und Gerätetypen](/help/sites-cloud/authoring/features/responsive-layout.md)


## Verwandter Artikel {#related-article}

* [Erstellen eines eigenständigen, auf Kernkomponenten basierenden adaptiven Formulars](/help/forms/creating-adaptive-form-core-components.md)
