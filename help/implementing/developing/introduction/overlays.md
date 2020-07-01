---
title: Überlagerungen für Adobe Experience Manager als Cloud Service
description: AEM als Cloud Service verwendet das Prinzip von Überlagerungen, um Ihnen das Erweitern und Anpassen der Konsolen und anderer Funktionen zu ermöglichen
translation-type: tm+mt
source-git-commit: 8028682f19ba6ba7db6b60a2e5e5f5843f7ac11f
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 32%

---


# Überlagerungen in AEM als Cloud Service {#overlays-in-aem}

Adobe Experience Manager als Cloud Service verwendet das Prinzip von Überlagerungen, um Ihnen zu ermöglichen, die Konsolen und andere Funktionen (z. B. das Erstellen von Seiten) zu erweitern und anzupassen.

<!--
Adobe Experience Manager as a Cloud Service uses the principle of overlays to allow you to extend and customize the [consoles](/help/sites-developing/customizing-consoles-touch.md) and other functionality (for example, [page authoring](/help/sites-developing/customizing-page-authoring-touch.md)).
-->

Überlagerung ist ein Begriff, der in unterschiedlichen Zusammenhängen verwendet werden kann. In diesem Kontext (Erweiterung von AEM als Cloud Service) bedeutet eine Überlagerung, die vordefinierte Funktionen zu übernehmen und eigene Definitionen darüber aufzuzwingen (um die Standardfunktion anzupassen).

In einer Standardinstanz wird die vordefinierte Funktion unter gehalten `/libs` und es wird empfohlen, Ihre Überlagerung (Anpassungen) unter der `/apps` Verzweigung zu definieren (mithilfe eines [Suchpfads](#search-paths) , um die Ressourcen aufzulösen).

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

* You ***must not *make changes in the`/libs`branch **Any changes you do make may be lost, because this branch is liable to changes whenever upgrades are applied to your instance.

* Überlagerungen bündeln Ihre Änderungen an zentraler Stelle und erleichtern es Ihnen, Ihre Änderungen zu verfolgen, zu migrieren, zu sichern und/oder zu debuggen.

## Suchpfade {#search-paths}

AEM verwendet einen Suchpfad, um eine Ressource zu finden, wobei (standardmäßig) zuerst die `/apps` Verzweigung und dann die `/libs` Verzweigung gesucht wird. This mechanism means that your overlay in `/apps` (and the customizations defined there) will have priority.

Bei Überlagerungen ist die bereitgestellte Ressource ein Aggregat der abgerufenen Ressourcen und Eigenschaften, je nach den in der OSGi-Konfiguration definierten Suchpfaden.

<!--
## Example of Usage {#example-of-usage}

Some examples are covered when:

* [Customizing the Consoles](/help/sites-developing/customizing-consoles-touch.md)
* [Customizing Page Authoring](/help/sites-developing/customizing-page-authoring-touch.md)
-->