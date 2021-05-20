---
title: Überlagerungen für Adobe Experience Manager as a Cloud Service
description: AEM as a Cloud Service nutzt das Prinzip von Überlagerungen, um Ihnen zu ermöglichen, die Konsolen und andere Funktionen zu erweitern und anzupassen.
exl-id: 24bdb1a9-6d77-43c7-a75e-28e6e0fd7608
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 100%

---

# Überlagerungen in AEM as a Cloud Service{#overlays-in-aem}

Adobe Experience Manager as a Cloud Service verwendet das Prinzip von Überlagerungen, um Ihnen zu ermöglichen, die Konsolen und andere Funktionen (z. B. das Erstellen von Seiten) zu erweitern und anzupassen.

<!--
Adobe Experience Manager as a Cloud Service uses the principle of overlays to allow you to extend and customize the [consoles](/help/sites-developing/customizing-consoles-touch.md) and other functionality (for example, [page authoring](/help/sites-developing/customizing-page-authoring-touch.md)).
-->

Der Begriff „Überlagerung“ kann in unterschiedlichen Zusammenhängen verwendet werden. In diesem Zusammenhang (der Erweiterung von AEM as a Cloud Service) ist damit die Übernahme der vordefinierten Funktionen und das Anwenden eigener Definitionen (zum Anpassen der Standardfunktionalität) gemeint.

In einer Standardinstanz wird die vordefinierte Funktionalität unter `/libs` gespeichert und es wird empfohlen, Ihre Überlagerung (Anpassungen) unter der Verzweigung `/apps` zu definieren (mithilfe eines [Suchpfads](#search-paths), um die Ressourcen aufzulösen).

* Die Touch-optimierte Benutzeroberfläche verwendet Überlagerungen, die mit [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html) verbunden sind:

   * Methode

      * Rekonstruieren Sie die entsprechende `/libs`-Struktur unter `/apps`.

         Dies erfordert keine 1:1-Kopie, da der [Sling Resource Merger](/help/implementing/developing/introduction/sling-resource-merger.md) verwendet wird, um die erforderlichen Originaldefinitionen zu vergleichen. Der Sling Resource Merger stellt Dienste für den Zugriff auf und die Zusammenführung von Ressourcen mittels Vergleichsmechanismen bereit.

      * Nehmen Sie beliebige Änderungen unter `/apps` vor.
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

* Sie dürfen ***keine* Änderungen in der Verzweigung `/libs` vornehmen.**Jegliche Änderungen, die Sie vornehmen, können verloren gehen, sobald Aktualisierungen an Ihrer Instanz vorgenommen werden.

* Überlagerungen bündeln Ihre Änderungen an zentraler Stelle und erleichtern es Ihnen, Ihre Änderungen zu verfolgen, zu migrieren, zu sichern und/oder zu debuggen.

## Suchpfade {#search-paths}

AEM verwendet einen Suchpfad, um eine Ressource zu finden, wobei (standardmäßig) zuerst die Verzweigung `/apps` und dann die Verzweigung `/libs` gesucht wird. Durch diesen Mechanismus hat Ihre Überlagerung in `/apps` (und die dort definierten Anpassungen) Priorität.

Bei Überlagerungen ist die bereitgestellte Ressource ein Aggregat der abgerufenen Ressourcen und Eigenschaften, abhängig von den in der OSGi-Konfiguration definierten Suchpfaden.

<!--
## Example of Usage {#example-of-usage}

Some examples are covered when:

* [Customizing the Consoles](/help/sites-developing/customizing-consoles-touch.md)
* [Customizing Page Authoring](/help/sites-developing/customizing-page-authoring-touch.md)
-->
