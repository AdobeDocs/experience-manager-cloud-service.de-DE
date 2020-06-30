---
title: Überlagerungen für Adobe Experience Manager als Cloud Service
description: AEM als Cloud Service verwendet das Prinzip von Überlagerungen, um Ihnen das Erweitern und Anpassen der Konsolen und anderer Funktionen zu ermöglichen
translation-type: tm+mt
source-git-commit: 58440cb565039becd5b08333994b70f2ea77cc99
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 39%

---


# Überlagerungen in AEM als Cloud Service {#overlays-in-aem}

Adobe Experience Manager als Cloud Service verwendet das Prinzip von Überlagerungen, um Ihnen zu ermöglichen, die Konsolen und andere Funktionen (z. B. das Erstellen von Seiten) zu erweitern und anzupassen.

<!--
Adobe Experience Manager as a Cloud Service uses the principle of overlays to allow you to extend and customize the [consoles](/help/sites-developing/customizing-consoles-touch.md) and other functionality (for example, [page authoring](/help/sites-developing/customizing-page-authoring-touch.md)).
-->

Überlagerung ist ein Begriff, der in unterschiedlichen Zusammenhängen verwendet werden kann. In diesem Kontext (Erweiterung von AEM als Cloud Service) bedeutet eine Überlagerung, die vordefinierte Funktionen zu übernehmen und eigene Definitionen darüber aufzuzwingen (um die Standardfunktion anzupassen).

In a standard instance the predefined functionality is held under `/libs` and it is recommended practice to define your overlay (customizations) under the `/apps` branch. AEM uses a search path to find a resource, searching first the `/apps` branch and then the `/libs` branch (the [search path can be configured](#configuring-the-search-paths)). Durch diesen Mechanismus hat Ihre Überlagerung (und die dort definierten Anpassungen) Priorität.

* Die touchfähige Benutzeroberfläche verwendet [Granitüberlagerungen](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html):

   * Methode

      * Reconstruct the appropriate `/libs` structure under `/apps`.

         This does not require a 1:1 copy, as the [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) is used to cross-reference the original definitions that are required. Der Sling Resource Merger stellt Dienste für den Zugriff auf und die Zusammenführung von Ressourcen mittels Vergleichsmechanismen bereit.

      * Make any changes under `/apps`.
   * Vorteile

      * Robuster gegenüber Änderungen unter `/libs`.
      * Nur die erforderlichen Aspekte müssen neu definiert werden.


<!-- Still links to reference material in 6.5 -->

>[!CAUTION]
>
>Der [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) und die zugehörigen Methoden können nur mit [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html) verwendet werden. Das bedeutet, dass die Erstellung einer Überlagerung mit einem Strukturgerüst nur für die standardmäßige Touch-optimierte Benutzeroberfläche geeignet ist.

Überlagerungen empfehlen sich für viele Änderungen, beispielsweise das Konfigurieren von Konsolen oder Erstellen der Auswahlkategorie für den Asset-Browser im seitlichen Bedienfeld (wird bei der Seitenbearbeitung verwendet). Sie sind aus folgenden Gründen erforderlich:

<!--
Overlays are the recommended method for many changes, such as [configuring your consoles](/help/sites-developing/customizing-consoles-touch.md#create-a-custom-console) or [creating your selection category to the asset browser in the side panel](/help/sites-developing/customizing-page-authoring-touch.md#add-new-selection-category-to-asset-browser) (used when authoring pages). They are required as:
-->

* You ***must not *make changes in the`/libs`branch **Any changes you do make may be lost, because this branch is liable to changes whenever you:

   * Bei Upgrades auf Ihrer Instanz
   * Beim Anwenden eines Hotfix
   * Beim Installieren eines Feature Packs

* Überlagerungen bündeln Ihre Änderungen an zentraler Stelle und erleichtern es Ihnen, Ihre Änderungen zu verfolgen, zu migrieren, zu sichern und/oder zu debuggen.

## Konfigurieren von Suchpfaden {#configuring-the-search-paths}

Bei Überlagerungen ist die bereitgestellte Ressource ein Aggregat der abgerufenen Ressourcen und Eigenschaften, abhängig von den definierbaren Suchpfaden:

* Der **Suchpfad des Ressourcen-Resolvers** wie in der [OSGi-Konfiguration](/help/implementing/deploying/configuring-osgi.md) für die **Apache Sling-ResourceResolverFactory** definiert

   * Die Reihenfolge der Suchpfade von oben nach unten gibt die jeweiligen Prioritäten an.
   * In a standard installation the primary defaults are `/apps`, `/libs` - so the content of `/apps` has a higher priority than that of `/libs` (i.e. it *overlays* it).

* Zwei Dienstbenutzer benötigen JCR:READ-Zugriff auf den Speicherort der Skripten. Diese Benutzer sind: components-search-service (wird von den com.day.cq.wcm.coreTo-Access/cache-Komponenten verwendet) und sling-scripting (wird von org.apache.sling.servlets.resolver verwendet, um Servlets zu finden).
* Die folgende Konfiguration muss auch entsprechend der Stelle konfiguriert werden, an der Sie Ihre Skripte ablegen (in diesem Beispiel unter /etc, /libs oder /apps).

   ```
   PID = org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl
   resource.resolver.searchpath=["/etc","/apps","/libs"]
   resource.resolver.vanitypath.whitelist=["/etc/","/apps/","/libs/","/content/"]
   ```

* Schließlich muss auch der Servlet-Resolver konfiguriert werden (in diesem Beispiel auch um /etc hinzuzufügen)

   ```
   PID = org.apache.sling.servlets.resolver.SlingServletResolver
   servletresolver.paths=["/bin/","/libs/","/apps/","/etc/","/system/","/index.servlet","/login.servlet","/services/"]
   ```

<!--
## Example of Usage {#example-of-usage}

Some examples are covered when:

* [Customizing the Consoles](/help/sites-developing/customizing-consoles-touch.md)
* [Customizing Page Authoring](/help/sites-developing/customizing-page-authoring-touch.md)
-->