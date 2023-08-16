---
title: Wie wird ein adaptives Formular zur AEM Sites-Seite hinzugefügt?
description: Erfahren Sie, wie Sie ein adaptives Formular erstellen oder zu Ihrer AEM Sites-Seite hinzufügen. Lernen Sie auch die Vorteile und verschiedene Möglichkeiten kennen, Formulare in Ihre Website zu integrieren.
feature: Adaptive Forms, Page Editor, Authoring
Keywords: AF in Sites editor, af in aem sites, aem sites af, add af to a sites page, af aem sites, af sites, create af in a sites page, adaptive form in aem sites, forms aem sites, add form to a sites page, adaptive forms aem sites, add adaptive forms to aem page, create forms in an aem sites page
source-git-commit: bb2ee07f8750c15959ecdaa65f0932b05edfcd39
workflow-type: tm+mt
source-wordcount: '3229'
ht-degree: 61%

---


# Hinzufügen eines adaptiven Formulars zu einer AEM Sites-Seite oder einem Experience Fragment {#create-or-add-an-adaptive-form-to-aem-sites-page}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/create-or-add-an-adaptive-form-to-aem-sites-page.html) |
| AEM as a Cloud Service | Dieser Artikel |

## Übersicht {#overview}

Mit AEM Forms können Sie Ihrer AEM Sites-Seite nahtlos ein Formular hinzufügen. Dadurch können Ihre Besuchenden bequem Formulare ausfüllen und senden, ohne jemals die Seite verlassen zu müssen, auf der sie sich befinden. Dadurch können sie mühelos mit anderen Elementen der Website interagieren und gleichzeitig aktiv mit dem Formular interagieren.

Mit dem AEM-Seiteneditor können Sie schnell mehrere Formulare erstellen und zu Ihren AEM Sites-Seiten hinzufügen. Mit AEM Seiteneditor können Inhaltsautoren nahtlose Erlebnisse zur Datenerfassung auf einer Sites-Seite erstellen, indem sie die Leistung adaptiver Formularkomponenten nutzen, einschließlich dynamischem Verhalten, Überprüfungen, Datenintegration, Generierung von Datensatzdokumenten und Automatisierung von Geschäftsprozessen. Außerdem können Sie damit verschiedene Funktionen von AEM Sites-Seiten verwenden, z. B. Versionierung, Targeting, Übersetzung und Multi-Site-Manager.

AEM Forms Cloud Service bietet Container für adaptive Formulare und Komponenten für adaptive Forms - Einbetten. Sie können den Container für adaptive Formulare verwenden, um ein neues Formular auf einer AEM Sites-Seite oder in einem Experience Fragment zu erstellen, während Sie mit der Komponente Adaptive Forms - Embed ein vorhandenes adaptives Formular hinzufügen oder ein neues Formular mit dem Adaptive Forms Editor erstellen können.

![Beispiel eines adaptiven Formulars auf einer AEM Sites-Seite](/help/forms/assets/adaptive-form-in-sites-page.png)

## Warum verwenden Sie Adaptive Forms-Kernkomponenten, um ein adaptives Formular auf der AEM Sites-Seite oder im Experience Fragment zu erstellen?

Wenn Sie in der Vergangenheit adaptive Forms Foundation-Komponenten oder einfache HTML-basierte Formulare für Ihre Sites erstellt haben, empfiehlt Adobe, adaptive Forms-Kernkomponenten zu verwenden, um ein adaptives Formular auf der AEM Sites-Seite oder im Experience Fragment zu erstellen. Sie können verschiedene Funktionen von AEM Sites-Seiten verwenden, wie z. B. Versionierung, Targeting, Übersetzung und Multi-Site-Manager, um die Erstellung und Verwaltung von Formularen für die adaptive Forms zu verbessern. Sehen wir uns einige dieser Funktionen an:

* **Versionierung:** AEM Sites-Seiten bieten [robuste Versionierungsfunktionen](/help/sites-cloud/authoring/features/page-versions.md), mit denen Sie verschiedene Versionen Ihrer Formulare verfolgen und verwalten können. Dadurch können Sie Änderungen und Verbesserungen an Formularen vornehmen und gleichzeitig bei Bedarf frühere Versionen wiederherstellen. Die Versionierung gewährleistet eine kontrollierte und organisierte Vorgehensweise bei der Entwicklung und Weiterentwicklung von Formularen.
* **Targeting (Integration mit Adobe Target):** Mit den Targeting-Funktionen von AEM Sites-Seiten können Sie auch [das Formularerlebnis für verschiedene Zielgruppen personalisieren](/help/sites-cloud/integrating/integration-adobe-target-ims.md). Mithilfe von Benutzersegmenten und Targeting-Kriterien können Sie den Inhalt, das Design oder das Verhalten des Formulars an bestimmte Benutzergruppen anpassen. Auf diese Weise können Sie ein personalisiertes und relevantes Formularerlebnis bereitstellen und die Interaktions- und Konversionsraten steigern.
* **Übersetzung:** AEM Sites gewährleistet [nahtlose Integration mit Übersetzungsdiensten](/help/sites-cloud/administering/translation/overview.md), sodass Sie Formulare problemlos in mehrere Sprachen übersetzen können. Diese Funktion vereinfacht den Lokalisierungsprozess und stellt sicher, dass Ihre Formulare für eine globale Zielgruppe zugänglich sind. Sie können Übersetzungen effizient in AEM-Übersetzungsprojekten verwalten und so Zeit und Aufwand für die Unterstützung mehrsprachiger Formulare reduzieren. Weitere Informationen zur Übersetzung finden Sie im Abschnitt Überlegungen .
* **Multi-Site-Management und Live Copy:** AEM Sites bietet robuste [Multi-Site-Management- und Live Copy-Funktionen](/help/sites-cloud/administering/msm/overview.md), mit denen Sie mehrere Websites in einer einzigen Umgebung erstellen und verwalten können. Mit dieser Funktion können Sie jetzt Formulare über verschiedene Sites hinweg wiederverwenden, um Konsistenz zu gewährleisten und doppelte Arbeit zu vermeiden. Mit zentralisierter Kontrolle und Verwaltung können Sie Formulare effizient über mehrere Websites hinweg verwalten und aktualisieren.
* **Themen:** AEM Sites-Seiten bieten ein Framework für das Entwerfen und Verwalten konsistenter visueller Stile auf mehreren Web-Seiten. Diese definieren Farben, Schriftarten, Stylesheets und andere visuelle Elemente, die zum allgemeinen Erscheinungsbild der Website beitragen. [Sie können die Designs verwenden, die für eine AEM Sites-Seite für ein adaptives Formular entwickelt wurden, wodurch Zeit und Mühe gespart werden.](/help/sites-cloud/administering/site-creation/site-themes.md#using-site-themes-using-themes).
* **Tagging:** Auf AEM Sites-Seiten können Sie [einer Seite, einem Asset oder einem anderen Inhalt Tags oder Beschriftungen zuweisen](/help/implementing/developing/introduction/tagging-framework.md). Tags sind Schlüsselwörter oder Metadatenbeschriftungen, die eine Möglichkeit bieten, Inhalte basierend auf bestimmten Kriterien zu kategorisieren und zu organisieren. Sie können Seiten, Assets oder anderen Inhaltselementen in AEM ein oder mehrere Tags zuweisen, um die Suche zu verbessern und die Assets zu kategorisieren.
* **Sperren und Freigeben von Inhalten:** AEM Sites ermöglicht Benutzenden die [Kontrolle des Zugriffs und der Änderungen an Seiten](/help/sites-cloud/authoring/fundamentals/editing-content.md) innerhalb der AEM Sites-Umgebung. Wenn eine Seite gesperrt ist, bedeutet dies, dass sie von anderen Benutzenden vor unbefugten Änderungen oder Bearbeitungen geschützt ist. Nur Benutzende, die den Inhalt gesperrt haben, oder Admins können ihn entsperren, um Änderungen zuzulassen.

Darüber hinaus wird Adaptive Forms in AEM Seiteneditor verwendet [Adaptive Forms-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de#features). Diese Kernkomponenten bieten eine standardmäßige und einfachere Methode zum Formatieren und Anpassen der Komponenten, die mit dem Szenario [AEM Sites WCM-Komponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de).


## Erstellen oder Hinzufügen eines adaptiven Formulars auf der AEM Sites-Seite oder AEM Experience Fragment? {#various-options-to-creat-or-add-an-adaptive-form-in-aem-sites-page-or-aem-experience-fragment}

Sie können diese Funktion voll nutzen, indem Sie die folgenden Optionen verwenden:

* **[Erstellen und Hinzufügen eines benutzerdefinierten adaptiven Formulars zu einer AEM Sites-Seite](#create-an-adaptive-form-in-sites-editor-or-experience-fragment):** Sie können die Container-Komponente für adaptive Formulare verwenden, um ein brandneues Formular von Grund auf neu zu erstellen und es speziell auf Ihre Anforderungen und Design-Voreinstellungen anzupassen.

* **[Erstellen und Hinzufügen eines benutzerdefinierten adaptiven Formulars zu einem Experience Fragments](#create-an-adaptive-form-in-sites-editor):** Sie können die Reichweite Ihrer Formulare erweitern, indem Sie sie zu AEM Experience Fragments hinzufügen, wodurch eine nahtlose Wiederverwendung über mehrere Seiten oder Sites hinweg ermöglicht wird.

* **[Konvertieren eines adaptiven Formulars in Experience Fragment](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment):** Konvertieren Sie ein adaptives Formular, das zu einer AEM Sites-Seite hinzugefügt wurde, in ein Experience Fragment, um das Formular auf mehreren AEM Sites-Seiten wiederzuverwenden.

* **[Erstellen Sie Formulare basierend auf genehmigten Vorlagen und fügen Sie sie einer AEM Sites-Seite hinzu:](/help/forms/embed-adaptive-form-aem-sites.md#embed-form-using-adaptive-form-wizzard-aem-sites)** Sie können vorab genehmigte Vorlagen nutzen, um schnell Adaptive Forms zu erstellen, die den Branding-Richtlinien und Designstandards Ihres Unternehmens entsprechen. Die Option ist nur für adaptive Formulare verfügbar, die mit dem adaptiven Formular-Editor oder der „Adaptiven Formular – Einbettungskomponente“ erstellt wurde.

* **[Fügen Sie vorhandene Formulare zu einer AEM Sites-Seite hinzu:](/help/forms/embed-adaptive-form-aem-sites.md#embed-an-adaptive-form-in-sites-editor)** Sie können bereits erstellte Formulare einfach in Ihre Websites integrieren, sodass Besucher direkt mit ihnen interagieren können. Die Option ist nur für adaptive Formulare verfügbar, die mit dem adaptiven Formular-Editor oder der „Adaptiven Formular – Einbettungskomponente“ erstellt wurde.


* **Fügen Sie einer AEM Sites-Seite oder einem Experience Fragment mehrere Formulare hinzu:**  Sie können mehrere adaptive Forms erstellen oder zu einer AEM Sites-Seite hinzufügen, um Benutzern basierend auf ihren Voreinstellungen und Anforderungen mehrere Optionen zur Verfügung zu stellen. Diese können eine Kombination aus neuen und vorhandenen Formularen darstellen. Sie können die **[!UICONTROL Container für adaptive Formulare]** mehrere Male, um Adaptive Forms auf einer AEM Sites-Seite hinzuzufügen. Sie können die **[!UICONTROL Adaptives Forms - Einbetten]** Komponente mehrmals in einer AEM Sites-Seite verwenden, nur wenn **[!UICONTROL Das Formular deckt die gesamte Breite des Rahmens ab]** ausgewählt ist. In diesem Fall **[!UICONTROL Das Formular deckt die gesamte Breite des Rahmens ab]** nicht aktiviert ist, unterstützt die AEM Sites-Seite nur, dass nur ein adaptives Formular ohne iFrame vorhanden ist. So fügen Sie mit dem **[!UICONTROL Adaptives Forms - Einbetten]** Komponente, auswählen **[!UICONTROL Das Formular deckt die gesamte Breite des Rahmens ab]** -Option.

## Überlegungen zum Erstellen eines adaptiven Formulars auf der AEM Sites-Seite oder AEM Experience Fragment {#consideration}

* Wenn Sie den Container für adaptive Formulare verwenden, um ein Formular zu erstellen oder hinzuzufügen, werden die Formulare über den AEM Sites-Übersetzungsfluss übersetzt und lokalisiert. Für jede Sprache wird eine separate Kopie (Sprachkopie) der Sites-Seite und der entsprechenden Formulare generiert. Wenn eine Inhaltsautorin bzw. ein Inhaltsautor eine Regel in einem Formular auf der übergeordneten Seite ändert, müssen dieselben Änderungen in allen Sprachkopien des Formulars vorgenommen werden. Mit dem Container für adaptive Formulare können Sie außerdem verschiedene Funktionen von AEM Sites-Seiten verwenden, z. B. Versionierung, Targeting, Übersetzung und Multi-Site-Manager.

* Wenn Sie ein Formular mithilfe der Einbettungskomponente für adaptive Formulare erstellen oder hinzufügen, werden die Formulare mithilfe des AEM Forms-Übersetzungsflusses übersetzt und lokalisiert. In diesem Fall wird ein einzelnes Formular beibehalten und in allen Sprachkopien der Sites-Seiten referenziert. Die Einbettungskomponente für adaptive Formulare bietet keinen Zugriff auf verschiedene Funktionen von AEM Sites-Seiten wie Versionierung, Targeting, Übersetzung und Multi-Site-Manager.


## Anforderungen zum Erstellen oder Hinzufügen eines adaptiven Formulars auf der AEM Sites-Seite oder AEM Experience Fragment {#before-you-start-creating-an-adaptive-form}

Bevor Sie mit der Erstellung eines adaptiven Formulars beginnen, aktivieren Sie die Kernkomponenten des adaptiven Forms und fügen Sie Ihrer AEM Sites-Seite Adaptive Forms-Client-Bibliotheken hinzu:

+++  Aktivieren der adaptiven Forms-Kernkomponenten für Ihre AEM Cloud Service-Umgebung

Stellen Sie sicher, dass [Adaptive Forms-Kernkomponenten sind für Ihre as a Cloud Service AEM Forms-Umgebung aktiviert](enable-adaptive-forms-core-components.md).

+++

+++  Adaptive Forms-Client-Bibliotheken zu Ihrer AEM Sites-Seite oder Ihrem Experience Fragment hinzufügen

Um die vollständige Funktionalität der adaptiven Formular-Container-Komponente zu aktivieren, fügen Sie die Client-Bibliotheken „customHeaderlibs“ und „customfooterlibs“ mithilfe der Bereitstellungs-Pipeline zu Ihrer AEM Sites-Seite hinzu. So fügen Sie die Bibliotheken hinzu:

1. Zugriff und Klonen Sie Ihre [AEM Cloud Service Git Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/repositories.html).
1. Öffnen Sie den Ordner &quot;AEM Cloud Service Git Repository&quot;in einem Texteditor für Pläne. Zum Beispiel Microsoft Visual Code.
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

1. [Ausführen der Bereitstellungspipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html?lang=de) , um die Client-Bibliotheken in Ihrer AEM as a Cloud Service Umgebung bereitzustellen.

+++

+++ Aktivieren des adaptiven Forms-Containers für Ihre AEM Sites-Seite oder Ihr Experience Fragment

Um die Komponente [!UICONTROL Container für adaptive Formulare] in der Richtlinie der Vorlage zu aktivieren, führen Sie die folgenden Schritte aus:

1. Öffnen Sie die AEM Sites-Seite oder das Experience Fragment zur Bearbeitung. Um die Seite zur Bearbeitung zu öffnen, wählen Sie sie aus und klicken Sie auf „Bearbeiten“.
1. Öffnen Sie die Vorlage Ihrer Sites- oder Experience Fragment-Seite. Um die Vorlage zu öffnen, gehen Sie zu [!UICONTROL Seiteninformationen] ![Seiteninformationen](/help/forms/assets/Smock_Properties_18_N.svg) > [!UICONTROL Vorlage bearbeiten]. Dadurch wird die entsprechende Vorlage im Vorlageneditor geöffnet.
1. Klicken Sie in der Strukturansicht auf das Symbol **[!UICONTROL Richtlinie]** ![Richtlinie](/help/forms/assets/Smock_FeedManagement_18_N.svg) in der Menüleiste. Wählen Sie in der Liste **[!UICONTROL Zugelassene Komponenten]** das Kontrollkästchen **[!UICONTROL Container für adaptive Formulare]** unter dem **[AEM Archetyp-Projektname] – Adaptives Formular**.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

+++

## Erstellen eines adaptiven Formulars {#create-an-adaptive-form-in-sites-editor-or-experience-fragment}

Sie können ein brandneues Formular von Grund auf neu erstellen und es speziell an Ihre Anforderungen und Design-Voreinstellungen anpassen – direkt auf einer AEM Sites-Seite oder im Experience Fragment. Für Formulare, die nur einmal verwendet werden, wird die direkte Erstellung auf einer AEM Sites-Seite empfohlen, während Experience Fragments ideal für Formulare sind, die auf mehreren Seiten Ihrer Website wiederverwendet werden müssen.

* [Erstellen eines Formulars auf einer AEM Sites-Seite](#create-an-adaptive-form-in-sites-editor)
* [Erstellen eines Formulars in einem Experience Fragment](#create-an-adaptive-form-in-experience-fragment)
* [Konvertieren eines adaptiven Formulars in einer AEM Sites-Seite in ein Experience-Fragment](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment)

### Erstellen eines Formulars auf einer AEM Sites-Seite {#create-an-adaptive-form-in-sites-editor}

Sie können die Container-Komponente adaptiver Formulare im AEM-Seiteneditor verwenden, um ein benutzerdefiniertes Formular zu erstellen. Mit der Komponente können Sie ein Formular durch Ziehen und Ablegen der Formularkomponenten erstellen. Die Formularkomponenten basieren auf Kernkomponenten. Sie können diese einfach entsprechend den Anforderungen Ihrer Organisation anpassen.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

So erstellen Sie ein adaptives Formular auf einer Sites-Seite:

1. Öffnen Sie die AEM Sites-Seite im Bearbeitungsmodus.
1. Ziehen Sie die Komponente **[!UICONTROL Container für Adaptive Formulare]** vom Komponenten-Browser zur Sites-Seite hinzugefügt. Dadurch wird ein Bereich für das Formular auf der Seite geschaffen. Sie können den Layout-Modus verwenden, um die Größe des Container-Bereichs zu ändern.
1. Ziehen Sie Kernkomponenten des adaptiven Formulars per Drag &amp; Drop in den Container-Bereich, um das Formular zu erstellen.
1. Fügen Sie die Schaltfläche „Senden“ hinzu.

Legen Sie als Nächstes die [Sendeaktion](#configure-submit-action-for-form) und erweiterte Eigenschaften fest.

### Erstellen eines Formulars in einem Experience Fragment {#create-an-adaptive-form-in-experience-fragment}

Sie können die Reichweite Ihrer Formulare erweitern, indem Sie sie zu AEM Experience Fragments hinzufügen, was eine nahtlose Wiederverwendung über mehrere Seiten oder Sites hinweg ermöglicht. Sie können beispielsweise ein Newsletter-Registrierungsformular in ein Experience Fragment einfügen. Auf diese Weise können Sie das Fragment bequem über mehrere Seiten Ihrer Website hinweg wiederverwenden, sodass das Formular nicht wiederholt neu erstellt werden muss. Alle Aktualisierungen oder Änderungen, die im Experience Fragment am Newsletter-Registrierungsformular vorgenommen werden, werden automatisch auf alle Seiten übertragen, auf denen es verwendet wird. Dadurch wird der Prozess optimiert und ein nahtloses Benutzererlebnis sichergestellt, während die Verwaltung der Formulare Ihrer Website vereinfacht wird.

So erstellen Sie ein adaptives Formular in einem Experience Fragment:

1. Öffnen Sie ein Experience Fragment.
1. Ziehen Sie den **[!UICONTROL Container für adaptive Formulare]** vom Komponenten-Browser in das Experience Fragment.
1. Ziehen Sie Kernkomponenten des adaptiven Formulars per Drag &amp; Drop in den Container-Bereich im Experience Fragment, um das Formular zu erstellen.
1. Fügen Sie die Schaltfläche „Senden“ hinzu.

Legen Sie als Nächstes die [Sendeaktion](#configure-submit-action-for-form) und erweiterte Eigenschaften fest.

### Konvertieren eines Formulars auf der Seite &quot;AEM Sites&quot;in ein Experience Fragment {#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment}

Sie können ein vorhandenes adaptives Formular in einem Sites-Seiten-Editor in ein Experience Fragment konvertieren, um es auf mehreren Seiten oder Sites wiederzuverwenden.

So konvertieren Sie ein adaptives Formular auf einer AEM Sites-Seite in ein Experience Fragment:

1. Öffnen Sie die AEM Sites-Seite mit dem adaptiven Formular (in der Komponente „Container für adaptive Formulare“) im Bearbeitungsmodus.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]** aus, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formularseiten hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.
1. Wählen Sie in der Menüleiste die ![Symbol &quot;In Experience Fragment konvertieren&quot;](/help/forms/assets/Smock_FilingCabinet_18_N.svg) In Experience Fragment-Variantensymbol konvertieren.
   ![Klicken Sie auf das Dateiverwaltungs-Logo, um ein adaptives Formular in AEM Sites in ein Experience Fragment zu konvertieren.](/help/forms/assets/convert-form-in-sites-page-to-an-experience-fragment.png)

   Es wird ein Dialogfeld zum Konvertieren des Containers für adaptive Formulare in ein neues Experience Fragment oder zum Hinzufügen zu einem vorhandenen Experience Fragment angezeigt.
1. Legen Sie im Dialogfeld „In Experience Fragment-Variante konvertieren“ Werte für die folgenden Optionen fest:

   * **Aktion:** Wählen Sie diese Option aus, um ein neues Experience Fragment zu erstellen oder zu einem vorhandenen Experience Fragment hinzuzufügen.
   * **Übergeordneter Pfad:** Geben Sie den Pfad des Ordners an, in dem das Experience Fragment gehostet werden soll. Die Option ist nur zum Erstellen eines neuen Experience Fragment verfügbar.
   * **Vorlage:** Geben Sie den Pfad der Experience Fragment-Vorlage an. Wenn Sie keine Experience Fragment-Vorlage haben, [erstellen](/help/implementing/developing/extending/experience-fragments.md). Die Option ist nur zum Hinzufügen des adaptiven Formulars zu einem vorhandenen Experience Fragment verfügbar.
   * **Fragmenttitel:** Geben Sie den Titel des Experience Fragment an. Der Titel identifiziert ein Experience Fragment eindeutig.


## Konfigurieren der Sendeaktion für ein Formular auf einer AEM Sites-Seite oder in einem Experience Fragment {#configure-submit-action-for-form}

Mit einer Übermittlungsaktion können Sie das Ziel der Daten auswählen, die über ein adaptives Formular erfasst werden. Eine Sendeaktion wird ausgelöst, wenn eine Benutzerin bzw. ein Benutzer in einem adaptiven Formular auf die Schaltfläche „Senden“ klickt. Adaptive Formulare enthalten einige vordefinierte Sendeaktionen. Sie können außerdem die standardmäßigen Sendeaktionen erweitern, um Ihre eigene benutzerdefinierte Sendeaktion zu erstellen. So konfigurieren Sie eine Sendeaktion für Ihr Formular:

1. Öffnen Sie den AEM-Seiteneditor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]** aus, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formularseiten hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg). Das Dialogfeld zum Konfigurieren von Sendeaktionen der Container adaptiver Formulare wird geöffnet.
   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld Container für adaptive Formulare zu öffnen, um die Übermittlungsaktion für ein adaptives Formular zu konfigurieren.](/help/forms/assets/adaptive-forms-container.png)
1. Wählen Sie je nach Ihren Anforderungen eine Übermittlungsaktion aus und konfigurieren Sie sie. Detaillierte Informationen zu Übermittlungsaktionen finden Sie unter [Übermittlungsaktion für adaptive Formulare](/help/forms/configuring-submit-actions.md)


## Konfigurieren eines Schema- oder Formulardatenmodells für ein Formular auf der AEM Sites-Seite oder im Experience Fragment {#configure-schema-or-data-model-for-form}

Sie können das Formulardatenmodell verwenden, um ein Formular mit einer Datenquelle zu verbinden und Daten basierend auf Benutzeraktionen zu senden und zu empfangen. Sie können auch ein Formular mit einem JSON-Schema verbinden, um die gesendeten Daten in einem vordefinierten Format zu empfangen. Verbinden Sie basierend auf der Anforderung Ihr Formular mit einem JSON-Schema oder Formulardatenmodell:

* [Erstellen eines JSON-Schemas und Hochladen in Ihre Umgebung](/help/forms/adaptive-form-json-schema-form-model.md)  oder
* [Erstellen eines Formulardatenmodells](/help/forms/create-form-data-models.md)

So konfigurieren Sie ein JSON-Schema oder ein Formulardatenmodell für Ihr Formular:

1. Öffnen Sie den AEM-Seiteneditor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]** aus, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formularseiten hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg). Das Dialogfeld zum Konfigurieren von Datenmodellen der Container adaptiver Formulare wird geöffnet.
   ![Klicken Sie auf das Schraubenschlüsselsymbol, um Datenmodelle für das adaptive Formular zu konfigurieren.](/help/forms/assets/form-data-model-adaptive-forms-container.png)
1. Wählen Sie ein JSON-Schema oder ein Formulardatenmodell aus und konfigurieren Sie es entsprechend Ihren Anforderungen. Detaillierte Informationen zu Übermittlungsaktionen finden Sie unter [Übermittlungsaktion für adaptive Formulare](/help/forms/configuring-submit-actions.md).

   * Wenn Sie die Option **[!UICONTROL Formularmodell]** wählen, können Sie mit der Option **[!UICONTROL Formulardatenmodell auswählen]** ein vorkonfiguriertes Formulardatenmodell auswählen.
   * Wenn Sie die Option **[!UICONTROL Schema]** wählen, verwenden Sie die Option **[!UICONTROL Schema]**, um ein JSON-Schema für Ihr Formular auszuwählen.

1. Klicken Sie auf **[!UICONTROL Fertig]**.

## Konfigurieren eines Vorbefüllungsdienstes für ein Formular auf der AEM Sites-Seite oder im Experience Fragment {#configure-prefill-service-for-form}

Sie können den Vorbefüllungsdienst verwenden, um Felder eines adaptiven Formulars mit vorhandenen Daten automatisch auszufüllen. Wenn ein Benutzer ein Formular öffnet, werden die Werte für diese Felder vorbefüllt. Sie haben folgende Möglichkeiten:

* [Erstellen eines benutzerdefinierten Vorbefüllungsdienstes](/help/forms/prepopulate-adaptive-form-fields.md)
* [Verwenden des Vorbefüllungsdienstes für Formulardatenmodelle](#fdm-prefill-service)

### Verwenden Sie den Vorbefüllungs-Dienst für Formulardatenmodelle, um Felder eines Formulars auf der AEM Sites-Seite oder im Experience Fragment vorab auszufüllen. {#fdm-prefill-service}

Sie können den Vorbefüllungs-Dienst für Formulardatenmodelle verwenden, um Felder eines adaptiven Formulars auf der AEM Sites-Seite oder im Experience Fragment mit einem Formulardatenmodell oder einem benutzerdefinierten Vorbefüllungs-Dienst im Voraus auszufüllen. Der Vorbefüllungsdienst für das Formulardatenmodell verwendet den [Get-Dienst des konfigurierten Formulardatenmodells](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) zum Abrufen von Daten. So verwenden Sie den Vorbefüllungsdienst für Formulardatenmodelle eines adaptiven Formulars:

1. Öffnen Sie den AEM-Seiteneditor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]** aus, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formularseiten hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg). Das Dialogfeld zum Konfigurieren von Datenmodellen der Container adaptiver Formulare wird geöffnet.
   ![Klicken Sie auf das Schraubenschlüsselsymbol, um das Dialogfeld Container für adaptive Formulare zu öffnen, um den Vorbefüllungs-Dienst für das adaptive Formular zu konfigurieren.](/help/forms/assets/adaptive-forms-container.png)
1. Formulardatenmodell auswählen. Öffnen Sie die Registerkarte **[!UICONTROL Allgemein]**. Wählen Sie im Vorbefüllungs-Dienst die Option **[!UICONTROL Vorfüllservice für Formulardatenmodell]**.
1. Klicken Sie auf **[!UICONTROL Fertig]**. Ihr adaptives Formular ist jetzt so konfiguriert, dass es das Vorfüllen des Formulardatenmodells verwendet. Sie können jetzt die [Regeleditor](rule-editor.md) , um Regeln zum Vorausfüllen von Formularfeldern zu erstellen.


## Leiten Sie den Benutzer auf eine Seite um oder zeigen Sie bei der Formularübermittlung eine Dankesnachricht an

Beim Senden eines Formulars können Sie die Benutzenden zu einer anderen Web-Seite oder Nachricht umleiten. So leiten Sie die Benutzenden um oder konfigurieren die Dankesnachricht:

1. Öffnen Sie den AEM-Seiteneditor oder das Experience Fragment, das das adaptive Formular enthält.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Container für adaptive Formulare]** aus, der Ihr adaptives Formular enthält. Eine AEM Sites-Seite kann mehrere adaptive Formularseiten hosten. Wählen Sie daher sorgfältig den richtigen Container für adaptive Formulare aus.

1. Öffnen Sie die Registerkarte **[!UICONTROL Übermittlung]**.

   * Um eine Umleitungs-URL zu konfigurieren, wählen Sie für die Option &quot;Beim Senden&quot;die Option **[!UICONTROL Zu URL umleiten]** und eine AEM Sites-Seite durchsuchen und auswählen oder die URL einer externen Seite angeben.
   * Um eine benutzerdefinierte Nachricht oder Dankesnachricht zu konfigurieren, wählen Sie für die Option &quot;Senden&quot;die Option **[!UICONTROL Nachricht anzeigen]** und geben Sie eine Nachricht im **[!UICONTROL Nachrichteninhalt]** ankreuzen. Es handelt sich um ein Rich-Text-Feld. Sie können die Vollbildoption verwenden, um alle verfügbaren Rich-Text-Elemente anzuzeigen.

## Siehe Nächste

* [Erstellen von Stilen oder Designs für Ihre Formulare](using-themes-in-core-components.md)
* [Dynamisches Verhalten zu Formularen mithilfe des Regeleditors hinzufügen](rule-editor.md)
* [Festlegen des Layouts von Formularen für verschiedene Bildschirmgrößen und Gerätetypen](/help/sites-cloud/authoring/features/responsive-layout.md)


## Verwandter Artikel {#related-article}

* [Erstellen eines eigenständigen, auf Kernkomponenten basierenden adaptiven Formulars](/help/forms/creating-adaptive-form-core-components.md)
