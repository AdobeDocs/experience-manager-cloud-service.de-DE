---
title: JSON-Exporter für Content Services
description: Mit den AEM Content Services können die Beschreibung und Bereitstellung von Inhalten in/über AEM über einen Fokus auf Webseiten hinweg generalisiert werden. Sie ermöglichen die Bereitstellung von Inhalten in Kanälen, die keine traditionellen AEM-Webseiten sind, und nutzen standardisierte Methoden, die von allen Clients genutzt werden können.
translation-type: tm+mt
source-git-commit: 0799a817095558edd49b53ddc915c9474181fef7
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 75%

---


# JSON-Exporter für Content Services {#json-exporter-for-content-services}

AEM Content Services wurden entwickelt, um die Beschreibung und den Versand von Inhalten in/von AEM jenseits des Fokus von Webseiten zu verallgemeinern.

Sie ermöglichen die Bereitstellung von Inhalten in Kanälen, die keine traditionellen AEM-Webseiten sind, und nutzen standardisierte Methoden, die von allen Clients genutzt werden können. Diese Kanäle können Folgendes sein:

* Einzelseiten-Webanwendungen
* native Mobile Apps
* Andere Kanal und Berührungspunkte außerhalb von AEM

Bei Inhaltsfragmenten, die strukturierte Inhalte verwenden, können Sie Inhaltsdienste bereitstellen, indem Sie den JSON-Exporter verwenden, um den Inhalt einer (y) AEM Seite im JSON-Datenmodellformat bereitzustellen. Diese können dann von Ihren eigenen Anwendungen genutzt werden.

## JSON Exporter mit Inhaltsfragment-Kernkomponenten {#json-exporter-with-content-fragment-core-components}

Mit dem AEM JSON Exporter können Sie die Inhalte auf einer (beliebigen) AEM-Seite im JSON-Datenmodellformat bereitstellen. Diese können dann von Ihren eigenen Anwendungen genutzt werden.

Innerhalb AEM Versands wird mithilfe der Selektoren `model` und `.json` erreicht.

`.model.json`

1. Zum Beispiel werden über eine URL wie:

   ```shell
   http://localhost:4502/content/wknd/language-masters/en/magazine/guide-la-skateparks.model.json
   ```

1. Inhalte der folgenden Art bereitgestellt:

   ![JSON-Modell für WKND-Inhalt](assets/json-model-wknd.png)

Alternativ können Sie die Inhalte eines strukturierten Inhaltsfragments bereitstellen, indem Sie dieses spezifisch nachverfolgen.

Verwenden Sie dazu den vollständigen Pfad zum Fragment (über `jcr:content`); beispielsweise mit dem folgenden Suffix:

`.../jcr:content/root/container/container/contentfragment.model.json`

Ihre Seite kann entweder ein einzelnes Inhaltsfragment oder mehrere Komponenten verschiedener Art enthalten. Sie können außerdem Mechanismen wie Listenkomponenten verwenden, um automatisch nach relevantem Inhalt zu suchen.

* Zum Beispiel werden über eine URL wie:

   ```shell
   http://localhost:4502/content/wknd/language-masters/en/magazine/guide-la-skateparks/jcr:content/root/container/container/contentfragment.model.json
   ```

* Inhalte der folgenden Art bereitgestellt:

   ![JSON-Modell des WKND-Inhaltsfragments](assets/json-model-wknd-content-fragment.png)

   >[!NOTE]
   >
   >Sie können [Ihre eigenen Komponenten anpassen](enabling-json-exporter.md), um auf diese Daten zuzugreifen und sie zu verwenden.

   >[!NOTE]
   >
   >Obwohl es sich nicht um eine Standardimplementierung handelt, werden [mehrere Selektoren unterstützt, ](enabling-json-exporter.md#multiple-selectors), `model` muss jedoch die erste sein.

### Weiterführende Informationen {#further-information}

Siehe auch:

* Assets-HTTP-API
   * [Assets-HTTP-API](/help/assets/developer-reference-material-apis.md)
* Sling-Modelle:
   * [Sling-Modelle – Zuweisung von Modellklassen und Ressourcentypen seit 1.3.0](https://sling.apache.org/documentation/bundles/models.html#associating-a-model-class-with-a-resource-type-since-130)
* AEM mit JSON:
   * [Aktivieren eines JSON-Exports für eine Komponente](enabling-json-exporter.md)

## Verwandte Dokumentation {#related-documentation}

Weitere Informationen finden Sie unter:

* [Inhaltsfragmente im Benutzerhandbuch &quot;Assets&quot;](/help/assets/content-fragments/content-fragments.md)
* [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)
* [Bearbeitung mit Inhaltsfragmenten](/help/sites-cloud/authoring/fundamentals/content-fragments.md)
* [Kernkomponenten](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/introduction.html) und die [Inhaltsfragmentkomponente](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/components/content-fragment-component.html)
