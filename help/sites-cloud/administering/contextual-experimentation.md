---
title: Kontextuelles Experimentieren in AEM as a Cloud Service
description: Erfahren Sie, wie Sie mit dem Experimentier-Plug-in Ihrer Site Experimentierfunktionen hinzufügen können.
feature: Administering
role: Admin
source-git-commit: 66ee08babae1f6640158260af051f8ad5f9bde85
workflow-type: tm+mt
source-wordcount: '1799'
ht-degree: 0%

---

# Kontextuelles Experimentieren in AEM as a Cloud Service {#contextual-experimentation}

>[!NOTE]
>Derzeit ist die Funktion für kontextuelle Experimente nur über das Beta-Programm verfügbar. Wenden Sie sich an den Adobe-Support oder Ihren Account Manager, um Zugriff auf das Beta-Programm zu erhalten.

Experimentieren ist die Praxis, das Design, die Funktionalität und den Code Ihrer Site zu testen, um die Leistung zu verbessern und Ihre Site effektiver und rationeller zu gestalten. Dies wird erreicht, indem entweder Inhalt oder Funktionalität geändert, die Ergebnisse mit einer früheren Version verglichen und die Verbesserungen ausgewählt werden, die messbare Auswirkungen haben.

Wenn es richtig gemacht wird, ist es ein leistungsstarkes Muster, um Konversionen, Interaktion und Besuchererlebnis zu verbessern. Im Allgemeinen gibt es einige Probleme, die zu vermeiden sind, wenn Sie nach einer Übernahme der Praxis suchen:

* **Zu wenig**: Die meisten Unternehmen experimentieren nicht genug, und wenn sie dies tun, experimentieren sie mit zu wenig Traffic, um aussagekräftige Ergebnisse zu erhalten.
* **Zu langsam**: Viele Experimentier-Frameworks verlangsamen die Site so sehr, dass die potenziellen neuen Konversionen den verlorenen Traffic und die Bounces aufgrund des langsamen Renderings nicht ausgleichen können.
* **Zu komplex**: Wenn die Einrichtung eines neuen Experiments zu viel Zeit in Anspruch nimmt, werden weniger Experimente ausgeführt.

Für Sites, die auf Adobe Experience Manager ausgeführt werden, gibt es das „vorkonfigurierte“ **Experimentier-Plug-in** mit dem Entwicklerinnen und Entwickler ihren Sites eine Experimentierfunktion hinzufügen können. Drei Dinge unterscheiden diesen Ansatz von anderen Experimentier-Frameworks:

* Es ist einfach, Tests mit den Tools einzurichten, die Ihre Autoren bereits kennen, und es ist keine separate Anmeldung erforderlich.
* Es ist tief in das AEM-Bereitstellungssystem integriert, verlangsamt Ihre Site nicht und ist widerstandsfähig gegenüber Code- und Inhaltsänderungen.
* Es ermöglicht das Testen einfacher Inhaltsänderungen sowie von Experimenten, die Design, Funktionalität und Code abdecken.

## Bevor Sie beginnen {#before-start}

Das Experimentier-Plug-in wird im Kontext von [Edge Delivery Services](/help/edge/overview.md) verwendet. Sie benötigen daher ein GitHub-Konto, ein Inhalts-Repository wie SharePoint oder Google Drive sowie [AEM Sidekick](https://www.aem.live/docs/sidekick). Weitere Informationen finden Sie [&#x200B; der Seite „Erste Schritte - Entwickler-Tutorial für den universellen Editor](https://www.aem.live/developer/tutorial) und [Erste Schritte - Entwickler-Tutorial](https://www.aem.live/developer/tutorial).

Nachdem Sie alles eingerichtet haben, sehen **sich dieses Video mit** Titel [Sofortiges Experimentieren](https://business.adobe.com/products/experience-manager/sites/testing-optimization.html) an, um eine kurze Demonstration zur Funktionsweise des Experimentier-Plug-ins zu erhalten.

## Häufig verwendete Begriffe {#frequently-used-terms}

Bevor Sie den Rest des Handbuchs zum Einrichten Ihres ersten Experiments befolgen, sollten Sie mit einigen häufig verwendeten Begriffen vertraut sein:

* **Kontrolle**: Das Erlebnis vor der Ausführung des Experiments. Bei allen Experimenten wird versucht, eine Verbesserung gegenüber dem Kontrollerlebnis zu testen und nachzuweisen.
* **Challenger**: ein Erlebnis, das sich von dem Kontrollerlebnis unterscheidet und gegen das oder neben dem Kontrollerlebnis „getestet“ wird.
* **Varianten**: Kontrolle und Challenger sind alle Varianten eines Experiments.
* **Statistische Signifikanz**: Bewerten, ob der Herausforderer wirklich besser ist als die Kontrolle. Die Berechnung der statistischen Signifikanz erlaubt es, Glück auszuschließen und sich auf die Ergebnisse zu konzentrieren, die eine echte Wirkung haben.

## Experimentvarianten und allgemeiner Workflow {#experiment-variants-workflow}

Im Allgemeinen verwenden Sie beim Einrichten eines Experiments eine bereits vorhandene Seite als Steuerelementseite. Anschließend erstellen Sie eine Challenger-Seite, die die Kontrollseite für einige Ihrer Besucher ersetzt. Auf der Challenger-Seite können Sie verschiedene Dinge wie Inhaltsvarianten, verschiedene Seiten-Layouts, call-to-action (CTA) usw. testen. Sie können diese Experimentvarianten konfigurieren, indem Sie Metadatenparameter auf der Steuerseite hinzufügen (siehe unten).

Der [Operative Telemetrie](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md)Service erfasst dann Daten, z. B. die Anzahl der Besucher auf der Kontrollseite im Vergleich zur Challenger-Seite. Anschließend verwenden Sie diese Daten, um die erforderlichen Verbesserungen für Ihre Site auszuwählen. Solange Sie sich in der etablierten Designsprache Ihrer Website bewegen und die vorhandene Blockfunktionalität nutzen, sollten Sie in der Lage sein, eine Experimentvariante einzurichten und innerhalb von Minuten an die Produktion zu senden.

>[!NOTE]
>Beachten Sie, dass das Plug-in keine Endbenutzerdaten verwendet bzw. beibehält, die zu ihrer Identifizierung führen könnten. Bei Verwendung der Standardkonfiguration, die den [Operative Telemetrie-Service in AEM as a Cloud Service) verwendet, ist weder ein Opt-in noch ein Cookie](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md)Einverständnis erforderlich.

### Experimentkennung {#experiment-identifier}

Bevor Sie beginnen, sollte jedes Experiment eine eigene Kennung für Tracking- und Analysezwecke haben. Ein guter Ausgangspunkt ist die Erstellung einer guten, eindeutigen Kennung für Ihr Experiment, die als „Experiment-ID“ bezeichnet wird. Experimente werden oft linear nummeriert oder mit ihrer Problem-ID in einem Problem-Tracker oder Management-System korreliert. Experiment-IDs verwenden oft ein Präfix für das Projekt, z. B.: `OPT-0134`, `EXP0004` oder `CCX0076`.

### Erstellen einer Challenger-Seite {#create-challenger-page}

Standardmäßig wird empfohlen, einen Ordner mit einer Experiment-ID in Kleinbuchstaben in Ihrem `/experiments/ folder` zu erstellen (z. B. /experiments/ccx0076/). Alle Seiten für die Challenger-Varianten befinden sich in diesem Ordner. Sie erstellen diesen Ordner in Ihrem lokalen Repository, z. B. SharePoint oder Google Drive.

Ihr Experimentordner sollte etwa so aussehen:

![experiments-folder](/help/sites-cloud/administering/assets/experiments-folder.png)

Platzieren Sie nach dem Erstellen des Ordners eine Kopie Ihrer Steuerelementseite in diesen Ordner und wenden Sie die Änderungen auf die Seite an, die Sie als Teil Ihrer Experimentvariante testen möchten (siehe Video oben). Nehmen wir als Beispiel die folgende Seite auf der Website an, auf der wir ein Experiment durchführen möchten:

![control-page](/help/sites-cloud/administering/assets/control-page.png)

Ihre Kopie des Challengers, der im `experiments/<experiment-id>` Ordner abgelegt ist, könnte wie folgt aussehen:

![Challenger-Page](/help/sites-cloud/administering/assets/challenger-page.png)

Zeigen Sie eine Vorschau der Challenger-Seite an und veröffentlichen Sie sie mithilfe des Sidekicks und nach Abschluss der Bearbeitung der Challenger-Seite. Die URL des veröffentlichten Challengers wird im nächsten Abschnitt - Konfigurieren des Experiments - verwendet.

### Konfigurieren des Experiments {#configure-experiment}

Sobald die Challenger-Seiten bereit sind, müssen Sie zurück zur Kontrollseite gehen und Metadaten hinzufügen, die angeben, dass die Seite(n) jetzt Teil des Tests sind.

Es gibt zwei Metadatenzeilen, die für eine Experimentvariante hinzugefügt werden müssen.

* **Experiment**: enthält Ihre Experiment-ID.

* **Experimentvarianten**: enthalten URLs für alle Challenger dieser Seite, getrennt durch Zeilenumbrüche, wenn Sie mehr als einen Challenger haben.

Siehe folgendes Beispiel:

![metadata-page](/help/sites-cloud/administering/assets/metadata-page.png)

Für jedes Experiment wird der Traffic auf alle Varianten (Kontrolle und Herausforderer) aufgeteilt und automatisch auf eine gleichmäßige Verteilung eingestellt. Wenn Sie also einen Herausforderer haben, wird es automatisch eine gerade 50/50-Aufteilung zwischen Kontrolle und dem Herausforderer geben. Wenn Sie zwei Herausforderer haben, sehen Sie automatisch ein Drittel des Traffics, der der Kontrolle zugeordnet ist, und jeden Herausforderer und so weiter.

Sie können die Traffic-Aufteilung außer Kraft setzen, indem Sie die Metadaten konfigurieren. Weitere Informationen zum Anpassen der in Ihren Experimenten verwendeten Metadaten finden Sie auf der folgenden [Seite](https://github.com/adobe/aem-experience-decisioning/wiki/Experiments#authoring).

### Vorschau und Staging von Experimentvarianten {#preview-stage-experiment}

Sobald Sie bereit sind, Ihr Experiment in der Vorschau anzuzeigen und zu inszenieren, klicken Sie im Sidekick oben links auf Vorschau . Bei jeder Vorschau einer Seite mit einem laufenden Experiment wird die Experimentier-Überlagerung in der `.aem.page` Vorschau-Umgebung angezeigt. Mit der Experimentier-Überlagerung können Sie zwischen den Experimentvarianten wechseln und erhalten außerdem Traffic-Daten.

<!--- ![experimentation-overlay](/help/sites-cloud/administering/assets/experimentation-overlay.png)

By using the experimentation overlay, authors can get quick insights on the performance of experiments being run on the production site. These insights are helpful in making a decision about the duration of the experiment, but also about which variant is best suited for production.-->

Die Datenerfassung zur Messung der Effektivität jeder Variante basiert auf dem [Operational Telemetry Service in AEM as a Cloud Service](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md).

### Senden der Experimentvariante an die Produktion {#production-experiment}

Wählen Sie die Experimentseiten aus und klicken Sie im Sidekick auf Veröffentlichen , um sowohl das Steuerelement als auch die Challenger-Variante(n) live zu schalten.

### Anwendungsbeispiele {#use-case-examples}

Nachfolgend finden Sie mehrere Anwendungsbeispiele für Experimentvarianten. Im Allgemeinen ähnelt der grundlegende Workflow dem oben beschriebenen, mit bestimmten Änderungen für jeden Anwendungsfall (wie die Anzahl der Challenger-Seiten oder Änderungen der Metadaten).

#### Ganzseitenexperiment {#full-page}

Sie verwenden ein ganzseitiges Experiment, um zwischen zwei Varianten derselben Seite zu testen. Dies ist eine vollständige Seitenvariante eines A/B-Tests, bei dem Sie über eine Kontroll- und eine Challenger-Seite verfügen. Sie ersetzen den gesamten Inhalt der „ursprünglichen“ Kontrollseite in der Challenger-Variante durch einen anderen Inhaltstyp. Beachten Sie, dass der Kunden-Traffic standardmäßig gleichmäßig aufgeteilt wird (50/50). Sie können jedoch bei Bedarf benutzerdefinierte Aufspaltungen erstellen.

<!--The metadata on the control page should look like this:

METADATA SETUP

#### Sections of the page Experiment {#sections-of-the-page}

This is experiment is similar to the full page one presented above but now the a/b test will contain changes to a section of the page instead of the whole content. For example, you can modify and test a carousel element, the call to action element and so on. As such, you will have a control and a challenger page, with the challenger page containing the modified elements. The metadata on the control page should look like this:

METADATA SETUP

#### Multi-path Experiment {#multi-path}

By leveraging the experimentation plug-in, you can set up a/b tests on several pages of your website at once. For example, on all product pages, photo galleries, all blog posts and so on.

The configuration logic is the same as above - you will create a control page and one or more challenger variants of that page. What changes in the multi-page use-case, is the following:

• You will create multiple control pages each with one or more variants.
• The control pages must have the same experiment ID in metadata field.

For example: We have 5 different production pages for which we need to set up an a/b test. We create 5 control pages (as detailed in the chapters above) and 5 (or more) challenger variants.

We then create an experiment ID, let’s say `prod-exp` and add this ID in the experiment metadata field for each control page. This basically means that all pages with the same ID are now “grouped”. We then assign the challenger variants for each control page, taking care to sequence them properly in case we have more than one variant for each control.

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

Once the audiences have been defined you are ready to author the experiment. As stated previously, let’s say you want to create a Firefox versus Chrome experiment where you will serve different pages depending on the browser.

You need two different challenger pages, so set up the experiment as follows:

1.Duplicate the Control page by right-clicking and copying it to the experiment folder. You need to copies, one for Firefox and one for Chrome.
2.Rename the copies. Give them specific names like “page-for-firefox”.
3.Change the content of the pages depending on what you need to serve on Firefox versus Chrome.
4.Change the metadata as explained in the section below.
5.Click Preview from the side-kick in the upper left side, to preview the changes.

The most important part when authoring this experiment is to change the metadata in the control page. Let’s say you defined the browser audiences in the codebase as: Audience: Firefox and Audience: Chrome. You need to edit the control page and add these audiences and point to the appropriate challenge page you set up previously. It should look similar to this:

Metadata
Title Control Page
Description This is the control page.
Experiment ExpBrowser
Experiment Variants `https://{ref}--{repo}--{org}.hlx.page/my-page-for-firefox https://{ref}--{repo}--{org}.hlx.page/my-page-for-chrome`
Audience: Firefox `https://{ref}--{repo}--{org}.hlx.page/page-for-firefox`
Audience: Chrome `https://{ref}--{repo}--{org}.hlx.page/page-for-chrome`

After this configuration, the users will be triaged based on the browser they connect with and the appropriate challenger page will be served.

Please keep in mind that the names above are only for illustration purposes. You can define the Audiences parameter and the challenger pages according to your needs, for example: Audience (Firefox) or Audience Firefox.-->

## Weitere Überlegungen {#other-considerations}

Im Folgenden werden einige weitere Aspekte vorgestellt, die Sie bei der Verwendung von Kontextexperimenten berücksichtigen sollten.

### Konversion {#conversion}

Experimente sind so eingerichtet, dass sie auf die Konvertierung abzielen (sie verfolgt klickbare Elemente auf Ihrer Seite). Alle Experimente müssen für Folgendes definiert werden:

* Experimenttyp
* Auf welchen Erlebnisblock das Experiment angewendet wird
* Wie viele Varianten enthält das Experiment?
* Wie setzt sich jede Variante zusammen?

### Sicherstellen, dass Experimentvarianten nicht indiziert sind {#experiment-not-indexed}

Beim Durchführen von Experimenten ist es in der Regel Best Practice, die Varianten aus der Sitemap auszuschließen und sicherzustellen, dass sie nicht von Suchmaschinen indiziert werden. Dies liegt daran, dass die Variantenseite als doppelter Inhalt angesehen werden kann und sich negativ auf SEO auswirkt.

Dazu können Sie eine der beiden folgenden Methoden verwenden:

* Wenn Sie alle Experimente in einem dedizierten Ordner zusammenfassen, z. B. `/experiments`: Stellen Sie sicher, dass Ihr `metadata.xlsx` eine Zeile mit `/experiments/**` als Pfad und eine Robots-Spalte mit den Werten `noindex`, `nofollow` enthält.
* Wenn Sie das Experiment und die Varianten mit dem regulären Inhalt halten: Fügen Sie für jede Variante einen Roboter-Eintrag in die Seitenmetadaten mit dem Wert `noindex`, `nofollow` hinzu.

## Entwickler- und technische Ressourcen {#dev-resources}

Adobe Experience Manager verwendet [operative Telemetrie]&#x200B;(/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md

), um Betriebsdaten zu sammeln, die unbedingt erforderlich sind, um Funktions- und Leistungsprobleme auf Adobe Experience Manager-gestützten Sites zu erkennen und zu beheben. Operative Telemetriedaten können zur Diagnose von Leistungsproblemen verwendet werden. Operative Telemetrie bewahrt die Privatsphäre der Besucher durch Sampling (nur ein kleiner Teil aller Seitenansichten wird überwacht).

### Datenschutz {#privacy-experimentation}

[Operativer Telemetrie-Service in AEM as a Cloud Service](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md) wurde entwickelt, um die Privatsphäre der Besucher zu wahren und die Datenerfassung zu minimieren. Als Besucher bedeutet dies, dass Adobe nicht versucht, personenbezogene Daten über Sie oder Informationen zu erfassen, die auf Sie zurückverfolgt werden können. Überprüfen Sie als Site-Operator die unten erfassten Datenelemente, um zu verstehen, ob sie eine Zustimmung erfordern.
Die operative Telemetrie von AEM verwendet keinen Client-seitigen Status oder keine Client-seitige ID, z. B. Cookies oder `localStorage` oder `sessionStorage` oder Ähnliches, um Nutzungsmetriken zu erfassen. Die Daten werden transparent über einen `Navigator.sendBeacon` Aufruf übermittelt, nicht über Pixel oder ähnliche Verfahren. Es erfolgt kein „Fingerabdruck“ von Geräten oder Einzelpersonen über ihre IP-Adresse, Benutzeragenten-Zeichenfolge oder andere Daten zum Zweck der Erfassung von erfassten Daten.

Es ist nicht gestattet, personenbezogene Daten in die Erfassung der betrieblichen Telemetriedaten aufzunehmen, noch dürfen betriebliche Telemetriedaten für Anwendungsfälle verwendet werden, die über das unbedingt erforderliche Maß hinausgehen.

### Häufig gestellte Fragen {#faq}

Nachfolgend finden Sie eine Liste häufig gestellter Fragen:

F: Kann ich das Aufspaltungsverhältnis zwischen den Varianten meines Experiments anpassen, zum Beispiel 10% auf Kontrolle und 90% auf den Herausforderer?

Ja, das Aufspaltungsverhältnis kann über ([) &#x200B;](#configure-experiment) werden.

F: Kann ich sowohl mit Text als auch mit Bildern experimentieren?

Ja, die Variante kann eine völlig andere Seite sein, sodass Sie sogar Layout-Änderungen testen können.
