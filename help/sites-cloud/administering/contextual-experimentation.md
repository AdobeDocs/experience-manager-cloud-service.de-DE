---
title: Kontextuelles Experimentieren in AEM as a Cloud Service
description: Erfahren Sie, wie Sie Ihrer Site mithilfe der Experimentierleiste Experimentierfunktionen hinzufügen können.
feature: Administering
role: Admin
exl-id: 420f8d5e-27f9-4081-b174-b2d7752779f7
source-git-commit: ca9d8326f1c628bd3129aeda1f2d0d0c3386d60e
workflow-type: tm+mt
source-wordcount: '1949'
ht-degree: 2%

---

# Kontextuelles Experimentieren in AEM as a Cloud Service {#contextual-experimentation}

Experimentieren ist die Praxis, das Design, die Funktionalität und den Code Ihrer Site zu testen, um die Leistung zu verbessern und Ihre Site effektiver und rationeller zu gestalten. Dies wird erreicht, indem entweder Inhalt oder Funktionalität geändert, die Ergebnisse mit einer früheren Version verglichen und die Verbesserungen ausgewählt werden, die messbare Auswirkungen haben.

Wenn es richtig gemacht wird, ist es ein leistungsstarkes Muster, um Konversionen, Interaktion und Besuchererlebnis zu verbessern. Im Allgemeinen gibt es einige Probleme, die zu vermeiden sind, wenn Sie nach einer Übernahme der Praxis suchen:

* **Zu wenig**: Die meisten Unternehmen experimentieren nicht genug, und wenn sie dies tun, experimentieren sie mit zu wenig Traffic, um aussagekräftige Ergebnisse zu erhalten.
* **Zu langsam**: Viele Experimentier-Frameworks verlangsamen die Site so sehr, dass die potenziellen neuen Konversionen den verlorenen Traffic und die Bounces aufgrund des langsamen Renderings nicht ausgleichen können.
* **Zu komplex**: Wenn die Einrichtung eines neuen Experiments zu viel Zeit in Anspruch nimmt, werden weniger Experimente ausgeführt.

Bei Sites, die auf Adobe Experience Manager ausgeführt werden, haben Entwickler die Möglichkeit, ihrer Site eine neue Experimentierfunktion hinzuzufügen. Drei Dinge unterscheiden diesen Ansatz von anderen Experimentier-Frameworks:

* Es ist einfach, Tests mit den Tools einzurichten, die Ihre Autoren bereits kennen, und es ist keine separate Anmeldung erforderlich.
* Es ist tief in das AEM-Bereitstellungssystem integriert, verlangsamt Ihre Site nicht und ist widerstandsfähig gegenüber Code- und Inhaltsänderungen.
* Es ermöglicht das Testen einfacher Inhaltsänderungen sowie von Experimenten, die Design, Funktionalität und Code abdecken.

## Experimentationsleiste {#experimentation-rail}

Die Experimentleiste ist die primäre Möglichkeit, Experimente einzurichten. Sie kann mit Ihrem Projekt entweder im Kontext von [Edge Delivery Services](/help/edge/overview.md) oder im [universellen Editor“ verwendet ](/help/implementing/universal-editor/introduction.md). Daher benötigen Sie ein GitHub-Konto, ein Inhalts-Repository wie SharePoint oder Google Drive sowie das Plug-in [AEM Sidekick](https://www.aem.live/docs/sidekick). Wenn Sie den universellen Editor verwenden möchten, benötigen Sie auch Zugriff auf eine [AEM as a Cloud Service-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md). Siehe auch die Seite [Erste Schritte - Entwickler-Tutorial für den universellen Editor](https://www.aem.live/developer/tutorial).

>[!WARNING]
>Die Experimentier-Engine ist erforderlich, um die Experimentierfunktion verwenden zu können. Stellen Sie sicher, dass die Engine ordnungsgemäß installiert und aktualisiert wurde, bevor Sie die folgenden Schritte implementieren. Weitere Informationen finden [ auf der folgenden ](https://github.com/adobe/aem-experimentation/tree/v2?tab=readme-ov-file#installation).

### Einrichten von Experimenten mit AEM Sidekick in Edge Delivery Services

Für den Zugriff auf die Funktionen der Experimentationsleiste in Ihrem Edge Delivery Services-Projekt benötigen Sie das Plug-in [AEM Sidekick](https://www.aem.live/docs/sidekick). Gehen Sie wie folgt vor, um den Sidekick einzurichten:

1. Fügen Sie die [AEM Sidekick-](https://chromewebstore.google.com/search/AEM%20Sidekick?hl=en-US&utm_source=ext_sidebar) hinzu und heften Sie sie an Ihren Browser an.
1. Öffnen Sie Ihre Projektseite im Vorschaumodus.
1. Klicken Sie in der AEM Sidekick-Leiste auf das Einstellungssymbol ![Einstellungen](/help/sites-cloud/administering/assets/settings-1.png) und wählen Sie **Dieses Projekt hinzufügen** aus.
1. Klicken Sie auf die Registerkarte Experimentieren , um die Experimentierleiste zu öffnen.

### Einrichten von Experimenten im universellen Editor

Beachten Sie vor der Einrichtung von Experimenten, dass Sie AEM Sites als Inhaltsquelle verwenden müssen, um im universellen Editor Inhalte erstellen zu können. Bei Bedarf können Sie Ihr vorhandenes Projekt in AEM Sites als Inhaltsquelle konvertieren, indem Sie der Anleitung auf der Seite [Einrichten von AEM Sites as a Content Source](https://www.aem.live/developer/ue-tutorial) folgen. Gehen Sie wie folgt vor, um Experimente im universellen Editor einzurichten:

1. Öffnen Sie Ihr Projekt im universellen Editor und überprüfen Sie die **A/B** Icon-Erweiterung. Falls das Symbol nicht sichtbar ist, überprüfen Sie, ob Sie die Funktion im Erweiterungs-Manager aktiviert haben. Wenn sie nicht aktiviert ist, aktivieren Sie sie oder fordern Sie Zugriff an.
1. Verweisen Sie Ihre `fstab.yaml` auf Ihre Projektkonfiguration und verknüpfen Sie sie mit Ihrer AEM-Autoreninstanz. Siehe auch [Verbinden des Codes mit dem Inhalt](https://www.aem.live/developer/ue-tutorial#connect-your-code-to-your-content)
1. Öffnen Sie Ihre AEM-Instanz und wenn Sie Ihr Projekt fertig haben, öffnen Sie es direkt im universellen Editor.
1. Öffnen Sie das Projekt und die Indexseite, auf der die Experimente ausgeführt werden sollen, und klicken Sie **der oberen Leiste auf** Bearbeiten“.
1. Klicken Sie auf das A/B-Symbol, um die Experimenterweiterung zu öffnen.

>[!NOTE]
>Wenn Sie Probleme beim Einrichten von Experimenten für Ihr Projekt haben, wenden Sie sich bitte an `aem-contextual-experimentation@adobe.com`.

>[!NOTE]
>Weitere Informationen zum Einrichten und Konfigurieren der Experimentier-Engine finden Sie im Dokumentationsabschnitt des folgenden [Repositorys](https://github.com/adobe/aem-experimentation/tree/v2-ui) .

## Experimentvarianten und allgemeiner Workflow {#experiment-variants-workflow}

Bevor Sie den Rest des Handbuchs zum Konfigurieren Ihres ersten Experiments befolgen, gibt es einige häufig verwendete Begriffe, mit denen Sie vertraut sein sollten:

* **Kontrolle**: Das Erlebnis vor der Ausführung des Experiments. Bei allen Experimenten wird versucht, eine Verbesserung gegenüber dem Kontrollerlebnis zu testen und nachzuweisen.
* **Challenger**: ein Erlebnis, das sich von dem Kontrollerlebnis unterscheidet und entweder gegen dieses oder daneben „getestet“ wird.
* **Varianten**: Kontrolle und Challenger sind alle Varianten eines Experiments.
* **Statistische Signifikanz**: Bewerten, ob der Herausforderer wirklich besser ist als die Kontrolle. Die Berechnung der statistischen Signifikanz erlaubt es, Glück auszuschließen und sich auf die Ergebnisse zu konzentrieren, die eine echte Wirkung haben.

Im Allgemeinen verwenden Sie beim Einrichten eines Experiments eine bereits vorhandene Seite als Steuerelementseite. Mithilfe der Experimentleiste erstellen Sie dann eine Challenger-Seite, die zunächst eine Kopie der Steuerelementseite ist. Auf der Challenger-Seite können Sie verschiedene Dinge wie Inhaltsvarianten, verschiedene Seiten-Layouts, call-to-action (CTA) usw. testen. Sie können auch KI-generierte Varianten verwenden, indem Sie die Funktion **Variante generieren** in der Experimentleiste verwenden.

Für jedes Experiment wird der Traffic zunächst zwischen Kontrolle und Herausforderer aufgeteilt (50/50), aber Sie können konfigurieren, wie der Traffic nach Bedarf aufgeteilt wird. Nach der Aktivierung des Experiments erhalten Sie Daten über den Operativen Telemetrie-Dienst.

Der [Operative Telemetrie](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md)Service erfasst Daten, z. B. die Anzahl der Besucher auf der Kontrollseite im Vergleich zur Challenger-Seite. Anschließend verwenden Sie diese Daten, um die erforderlichen Verbesserungen für Ihre Site auszuwählen. Solange Sie sich in der etablierten Design-Sprache Ihrer Website bewegen und die vorhandene Funktionalität nutzen, sollten Sie in der Lage sein, eine Experimentvariante einzurichten und innerhalb von Minuten an die Produktion zu senden.

>[!NOTE]
>Beachten Sie, dass das Plug-in keine Endbenutzerdaten verwendet bzw. beibehält, die zu ihrer Identifizierung führen könnten. Bei Verwendung der Standardkonfiguration, die den &quot;[ Telemetrieservice in AEM as a Cloud Service&quot; verwendet, ist weder ein Opt-in noch ein Cookie-Einverständnis ](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md).

<!--
### Frequently used terms {#frequently-used-terms}

Before following the rest of the guide to set up your first experiment, there are a few frequently used terms that you should be familiar with:

* **Control**: the experience prior to running the experiment. All experiments try to test and demonstrate an improvement over the control experience.
* **Challenger**: an experience that is different from the control experience and is "tested" against it or alongside it.
* **Variants**: control and challenger are all variants of an experiment.
* **Statistical Significance**: Evaluating if your challenger is really better than the control. Calculating statistical significance allows you to rule out luck and concentrate on the results that have a real effect. 
-->

### Erstellen von Experimenten im universellen Editor

Um die Experimentierfunktionen im universellen Editor zu verwenden, müssen Sie zunächst die Experimentierleiste wie in den oben beschriebenen Kapiteln beschrieben einrichten und sicherstellen, dass Sie AEM Sites als Inhaltsquelle verwenden. Nachdem alles eingerichtet wurde, führen Sie die folgenden Schritte aus.

### Projektbearbeitung im universellen Editor starten

Öffnen Sie Ihre AEM-Instanz und wenn Sie Ihr Projekt fertig haben, öffnen Sie es direkt im universellen Editor. Wenn Sie kein Projekt fertig haben und AEM Sites als Inhaltsquelle eingerichtet ist, erstellen Sie ein neues Textbausteinprojekt aus der bereitgestellten Vorlage. Sie können entweder Ihr Repository oder unser Beispiel-Repository verknüpfen, um es zu steuern [https://github.com/sudo-buddy/ue-experimentation](https://github.com/sudo-buddy/ue-experimentation). Siehe auch die Seite [Einrichten von AEM Sites as a Content Source](https://www.aem.live/developer/ue-tutorial). Nachdem das Projekt eingerichtet wurde, öffnen Sie es und die Indexseite, auf der Sie Experimente ausführen möchten, und klicken Sie in der oberen Leiste **Bearbeiten**.

### Starten der A/B-Erweiterung

Klicken Sie auf das **A/B**-Symbol, um die Experimenterweiterung zu öffnen. Bei Ihrer ersten Verwendung ist die Benutzeroberfläche leer. Klicken Sie **Neu erstellen**, um ein neues Experiment zu starten.

![a-b](/help/sites-cloud/administering/assets/a-b.png)

### Konfigurieren der Experimentdetails

Einige der Experimentwerte sind wie folgt vordefiniert:

**Experimenttyp**: A/B-Test (derzeit nur für Typ unterstützt)
**Optimieren für**: Konvertierung (derzeit nur Typ unterstützt)

Sie können Ihr Experiment auch in etwas Beschreibenderes umbenennen, z. B. `homepage-head-experiment`.

![experiment-details](/help/sites-cloud/administering/assets/exp-values.png)

### Hinzufügen und Bearbeiten von Varianten

Vergewissern Sie sich, dass Sie die Konzepte von Challenger und Variante wie oben beschrieben verstehen, bevor Sie fortfahren. Klicken Sie **Neu hinzufügen** um eine Challenger-Variante zu erstellen:

* Sie werden auf derselben Registerkarte zur Challenger-Seite weitergeleitet - es ist zunächst nur eine Kopie Ihres Steuerelements.
* Bearbeiten Sie die Seite entweder direkt im Kontext oder klicken Sie auf **Variante erstellen**, um die KI-Unterstützung zu verwenden.
* Nachdem Sie Änderungen vorgenommen haben, kehren Sie zur Erweiterung zurück, um fortzufahren.

![Kontrollvariante](/help/sites-cloud/administering/assets/control-variant.png)

### Andere Eigenschaften definieren und als Entwurf speichern

In der Experimentleiste können Sie ein Start- und Enddatum festlegen (beide optional). Wenn kein Startdatum angegeben wird, beginnt der Test mit der Veröffentlichung. Wenn kein Enddatum angegeben wird, wird der Test unbegrenzt ausgeführt. Sie können auch die Traffic-Aufteilung anpassen. Wir empfehlen, mit einer geraden 50/50-Aufteilung zu beginnen.

Wenn Sie fertig sind, klicken Sie auf **Speichern**. Dadurch wird Ihr Experiment als Entwurf gespeichert. Beachten Sie, dass das Experiment noch nicht aktiv ist. Sie können zur Übersicht zurückkehren, indem Sie auf **Zurück zum Experiment** klicken, oder Sie bleiben in der Bearbeitungsschnittstelle, um das Experiment zu aktivieren.

![Entwurf](/help/sites-cloud/administering/assets/draft-save.png)

### Experiment aktivieren

Wenn Sie fertig sind, klicken Sie auf **Aktivieren**, um das Experiment zu starten und die Experimentseite zu veröffentlichen. Der Test beginnt mit der Erfassung der RUM-Daten (Operational Telemetry) (weitere Einzelheiten finden Sie in den folgenden Kapiteln).

![Aktivieren](/help/sites-cloud/administering/assets/activate.png)

### Überwachen und Bewerben

Nachdem das Experiment statistische Signifikanz erreicht hat, klicken Sie auf **Bewerben**, um die gewünschte Variante zu Ihrem neuen Steuerelement zu machen. Beachten Sie, dass Sie die Experimentvariante nach der Aktivierung jederzeit bewerben können, auch wenn sie keine statistische Signifikanz erreicht.

### Experimentieren mit AEM Sidekick in Edge Delivery Services

Wenn Sie AEM Sidekick installiert haben, können Sie die Experimentierleiste direkt mit Ihrem Projekt in Edge Delivery Service verwenden, ohne den universellen Editor zu verwenden. Die Funktionalität ist im Wesentlichen dieselbe wie bei dem oben beschriebenen A/B-Test. Beachten Sie jedoch, dass Sie den **Vorschau**-Modus verwenden müssen, um den Test zu bearbeiten und zu konfigurieren. Nachdem Sie die Konfiguration des Tests abgeschlossen haben, klicken Sie auf **Aktivieren**, um sowohl das Steuerelement als auch die Challenger-Variante live zu schalten und mit der Erfassung von Telemetriedaten zu beginnen.

<!--
### Experiment Identifier {#experiment-identifier}

Before you start, every experiment should have its own identifier for tracking and analytics purposes. A good starting point is to come up with a good, unique identifier for your experiment which will be the "Experiment ID". Experiments are often numbered linearly or correlated to their Issue ID in an issue tracker or management system. Experiment IDs often use a prefix for the project, for example: `OPT-0134`, `EXP0004` or `CCX0076`.

### Create your Challenger Page {#create-challenger-page}

By convention, it is recommended to create a folder with a lowercase experiment ID in your `/experiments/ folder` (for example /experiments/ccx0076/). All the pages for the challenger variants are located in this folder. You create this folder in your local repository, for example, Sharepoint or Goggle Drive.

Your experiments folder should look something like this:

![experiments-folder](/help/sites-cloud/administering/assets/experiments-folder.png)

Once the folder is created, put a copy of your control page into that folder, and apply the changes on the page that you would like to test as part of your experiment variant (see video above). As an example let's assume we have the following page on the website that we want to run an experiment on:

![control-page](/help/sites-cloud/administering/assets/control-page.png)

Your copy of the challenger placed in the experiments/experiment-id folder might look like this:

![challenger-page](/help/sites-cloud/administering/assets/challenger-page.png)

Preview and publish the challenger page using the sidekick and when you are done authoring the challenger page. The URL of the published challenger will be used in the next section - configuring the experiment.

### Configuring the experiment {#configure-experiment}

As soon as the challenger pages are ready to go, you need to go back to the control page and add metadata indicating that the page(s) are now part of the test.

There are two metadata rows that need to be added for an experiment variant.

* **Experiment**: containing your experiment ID.

* **Experiment Variants**: containing URLs for all the challengers of this page, separated by line breaks if you have more than one challenger.

See the example below:

![metadata-page](/help/sites-cloud/administering/assets/metadata-page.png)

For each experiment, the traffic is split between all the variants (control and challengers) and is automatically set to an even distribution. As such, if you have one challenger, there will automatically be an even 50/50 split between control and the challenger. If you have two challengers, you will automatically see a third of the traffic allocated to control and each challenger and so on.

You can override the traffic split by configuring the metadata. For more information on how you can customize the metadata used in your experiments, see the following [page](https://github.com/adobe/aem-experience-decisioning/wiki/Experiments#authoring).

### Preview and Stage your Experiment Variants {#preview-stage-experiment}

As soon as you are ready to preview and stage your experiment, click Preview from the side-kick in the upper left side. Whenever you are previewing a page that has a running experiment, you will see the experimentation overlay in your `.aem.page` preview environment. The experimentation overlay lets you switch between the experiment variants and also provides traffic data.

![experimentation-overlay](/help/sites-cloud/administering/assets/experimentation-overlay.png)

By using the experimentation overlay, authors can get quick insights on the performance of experiments being run on the production site. These insights are helpful in making a decision about the duration of the experiment, but also about which variant is best suited for production.

The data collection to measure the effectiveness of each variant is based on the [Operational Telemetry service in AEM as a Cloud Service](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md).

### Send your Experiment Variant to Production {#production-experiment}

Select the experiment pages and click Publish from the side-kick to push both the control and the challenger variant(s) live.

### Use Case Examples {#use-case-examples}

Presented below are several use case examples for experiment variants. Generally speaking, the basic worklflow will be similar to the one described above, with particular changes for each use case (like the number of challenger pages or metadata changes).

#### Full Page Experiment {#full-page}

You use a full page experiment to test between two variants of the same page. This is a full page variant of an a/b test where you have a control and a challenger page. You will replace the whole content of the "original" control page in the challenger variant with a different type of content. Keep in mind that by default the customer traffic is split evenly (50/50), but you can create custom splits if you like.

The metadata on the control page should look like this:

METADATA SETUP

#### Sections of the page Experiment {#sections-of-the-page}

This is experiment is similar to the full page one presented above but now the a/b test will contain changes to a section of the page instead of the whole content. For example, you can modify and test a carousel element, the call to action element and so on. As such, you will have a control and a challenger page, with the challenger page containing the modified elements. The metadata on the control page should look like this:

METADATA SETUP

#### Multi-path Experiment {#multi-path}

By leveraging the experimentation plug-in, you can set up a/b tests on several pages of your website at once. For example, on all product pages, photo galleries, all blog posts and so on.

The configuration logic is the same as above - you will create a control page and one or more challenger variants of that page. What changes in the multi-page use-case, is the following:

* You will create multiple control pages each with one or more variants.
* The control pages must have the same experiment ID in metadata field.

For example: We have 5 different production pages for which we need to set up an a/b test. We create 5 control pages (as detailed in the chapters above) and 5 (or more) challenger variants.

We then create an experiment ID, let's say `prod-exp` and add this ID in the experiment metadata field for each control page. This basically means that all pages with the same ID are now "grouped". We then assign the challenger variants for each control page, taking care to sequence them properly in case we have more than one variant for each control.

The metadata on the control page should look like this:

METADATA SETUP

#### Code-level experiments {#code-level}

Note that the examples above assume you have different content variants to serve, but if you want to run a pure code-based a/b test, this is achievable via:

Metadata

Experiment    Hero Test
Experiment Variants    2

This will create just two variants, without touching the content, and you'll be able to target those based on the `experiment-hero-test` and `variant-control/variant-challenger-1/variant-challenger-`2 CSS classes that will be set on the `<body>` element.

#### Browser based audience experiment {#browser-based}

You can create browser based experiments, where you deliver separate challenger pages depending on the browser used. You can, for example, serve a different challenger page to a Firefox user as opposed to a Chrome user. This is achieved by leveraging the audience parameter.

Once you configure the experiment, the target audience will be evaluated based on the context of the browser (client side) and limited to the browser APIs available. As such, you do not need to use server side third-party systems or customer profile data for your experiment.

Before you start authoring this experiment variant, the audience parameter needs to be defined in the project codebase. For more details, see ee the following [page](https://github.com/adobe/aem-experience-decisioning/wiki/Experiments#authoring).

Once the audiences have been defined you are ready to author the experiment. As stated previously, let's say you want to create a Firefox versus Chrome experiment where you will serve different pages depending on the browser.

You need two different challenger pages, so set up the experiment as follows:

1.Duplicate the Control page by right-clicking and copying it to the experiment folder. You need to copies, one for Firefox and one for Chrome.
2.Rename the copies. Give them specific names like "page-for-firefox".
3.Change the content of the pages depending on what you need to serve on Firefox versus Chrome.
4.Change the metadata as explained in the section below.
5.Click Preview from the side-kick in the upper left side, to preview the changes.

The most important part when authoring this experiment is to change the metadata in the control page. Let's say you defined the browser audiences in the codebase as: Audience: Firefox and Audience: Chrome. You need to edit the control page and add these audiences and point to the appropriate challenge page you set up previously. It should look similar to this:

Metadata
Title Control Page
Description This is the control page.
Experiment ExpBrowser
Experiment Variants `https://{ref}--{repo}--{org}.hlx.page/my-page-for-firefox https://{ref}--{repo}--{org}.hlx.page/my-page-for-chrome`
Audience: Firefox `https://{ref}--{repo}--{org}.hlx.page/page-for-firefox`
Audience: Chrome `https://{ref}--{repo}--{org}.hlx.page/page-for-chrome`

After this configuration, the users will be triaged based on the browser they connect with and the appropriate challenger page will be served.

Please keep in mind that the names above are only for illustration purposes. You can define the Audiences parameter and the challenger pages according to your needs, for example: Audience (Firefox) or Audience Firefox.
-->

## Weitere Überlegungen {#other-considerations}

Im Folgenden werden einige Aspekte vorgestellt, die Sie bei der Verwendung von Kontextexperimenten berücksichtigen sollten.

### Konversion {#conversion}

Experimente sind so eingerichtet, dass sie auf die Konvertierung abzielen (sie verfolgt klickbare Elemente auf Ihrer Seite). Derzeit unterstützen wir Experimente auf Seitenebene mit einem Experiment pro Seite.

<!--
### Make sure experiment Variants are not indexed {#experiment-not-indexed}

When running experiments, it is usually best practice to exclude the variants from the sitemap and ensure they are not indexed by search engines. This is because the variant page could be seen as duplicate content and negatively impact SEO.

You can do this by using either of the following two methods:

* If you centralize all experiments in a dedicated folder, like `/experiments`: make sure your bulk `metadata.xlsx` sheet contains a row with `/experiments/**` as path, and a robots column with the values `noindex`, `nofollow`.
* If you keep the experiment control and variants with the regular content: add a robots entry in the page metadata for each variant, with the value `noindex`, `nofollow`.
-->

## Entwickler- und technische Ressourcen {#dev-resources}

Adobe Experience Manager verwendet [Operational Telemetry](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md), um Betriebsdaten zu erfassen, die unbedingt erforderlich sind, um Funktions- und Leistungsprobleme an Adobe Experience Manager-gestützten Sites zu ermitteln und zu beheben. Operative Telemetriedaten können zur Diagnose von Leistungsproblemen verwendet werden. Operative Telemetrie bewahrt die Privatsphäre der Besucher durch Sampling (nur ein kleiner Teil aller Seitenansichten wird überwacht).

### Datenschutz {#privacy-experimentation}

[Operativer Telemetrie-Service in AEM as a Cloud Service](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md) wurde entwickelt, um die Privatsphäre der Besucher zu wahren und die Datenerfassung zu minimieren. Als Besucher bedeutet dies, dass Adobe nicht versucht, personenbezogene Daten über Sie oder Informationen zu erfassen, die auf Sie zurückverfolgt werden können. Überprüfen Sie als Site-Operator die unten erfassten Datenelemente, um zu verstehen, ob sie eine Zustimmung erfordern.

Die operative Telemetrie von AEM verwendet keinen Client-seitigen Status oder keine Client-seitige ID, z. B. Cookies oder `localStorage` oder `sessionStorage` oder Ähnliches, um Nutzungsmetriken zu erfassen. Die Daten werden transparent über einen `Navigator.sendBeacon` Aufruf übermittelt, nicht über Pixel oder ähnliche Verfahren. Es erfolgt kein „Fingerabdruck“ von Geräten oder Einzelpersonen über ihre IP-Adresse, Benutzeragenten-Zeichenfolge oder andere Daten zum Zweck der Erfassung von erfassten Daten.

Es ist nicht gestattet, personenbezogene Daten in die Erfassung der betrieblichen Telemetriedaten aufzunehmen, noch dürfen betriebliche Telemetriedaten für Anwendungsfälle verwendet werden, die über das unbedingt erforderliche Maß hinausgehen.
