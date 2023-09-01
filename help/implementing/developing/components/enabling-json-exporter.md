---
title: Aktivieren eines JSON-Exports für eine Komponente
description: Komponenten können angepasst werden, um einen JSON-Export ihrer Inhalte basierend auf einem Modeler-Framework zu generieren.
exl-id: e9be5c0c-618e-4b56-a365-fcdd185ae808
source-git-commit: 3d20f4bca566edcdb5f13eab581c33b7f3cf286d
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 80%

---

# Aktivieren eines JSON-Exports für eine Komponente {#enabling-json-export-for-a-component}

Komponenten können angepasst werden, um einen JSON-Export ihrer Inhalte basierend auf einem Modeler-Framework zu generieren.

## Übersicht {#overview}

Der JSON-Export basiert auf [Sling-Modellen](https://sling.apache.org/documentation/bundles/models.html) und auf dem Framework des [Sling Model Exporter](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130) (der sich wiederum auf [Jackson-Anmerkungen](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) stützt).

Das bedeutet, dass die Komponente über ein Sling-Modell verfügen muss, wenn sie JSON exportieren muss. Daher müssen Sie diese beiden Schritte ausführen, um den JSON-Export für jede Komponente zu aktivieren.

* [Definieren eines Sling-Modells für die Komponente](#define-a-sling-model-for-the-component)
* [Kommentieren der Sling-Modell-Oberfläche](#annotate-the-sling-model-interface)

## Definieren eines Sling-Modells für die Komponente {#define-a-sling-model-for-the-component}

Zunächst muss ein Sling-Modell für die Komponente definiert werden.

>[!NOTE]
>
>Ein Beispiel für die Verwendung von Sling-Modellen finden Sie im Artikel [Entwickeln von Sling Model Exportern in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/develop-sling-model-exporter.html?lang=de).

Die Implementierungsklasse des Sling-Modells muss wie folgt kommentiert werden:

```java
@Model(... adapters = {..., ComponentExporter.class})
@Exporter(name = ExporterConstants.SLING_MODEL_EXPORTER_NAME, extensions = ExporterConstants.SLING_MODEL_EXTENSION)
@JsonSerialize(as = MyComponent.class)
```

Dadurch wird sichergestellt, dass Ihre Komponente mit dem `.model`-Selektor und der `.json`-Erweiterung eigenständig exportiert werden kann.

Außerdem kann die Sling-Modell-Klasse dadurch in der `ComponentExporter`-Oberfläche übernommen werden.

>[!NOTE]
>
>Jackson-Anmerkungen werden normalerweise nicht auf der Ebene der Sling-Modell-Klasse, sondern auf der Ebene der Modell-Oberfläche angegeben. Dadurch soll sichergestellt werden, dass der JSON-Export als Teil der Komponenten-API betrachtet wird.

>[!NOTE]
>
>Die Klassen `ExporterConstants` und `ComponentExporter` stammen aus dem `com.adobe.cq.export.json`-Paket.

### Verwenden mehrerer Selektoren {#multiple-selectors}

Obwohl dies kein Standardnutzungsszenario ist, können zusätzlich zum `model`-Selektor mehrere Selektoren konfiguriert werden.

```
https://<server>:<port>/content/page.model.selector1.selector2.json
```

In einem solchen Fall muss der `model`-Selektor jedoch der erste Selektor und `.json` die Erweiterung sein.

## Kommentieren der Sling-Modell-Oberfläche {#annotate-the-sling-model-interface}

Damit sie im JSON Exporter-Framework beachtet wird, sollte die `ComponentExporter`-Oberfläche (oder `ContainerExporter` bei Container-Komponenten) in der Modelloberfläche implementiert werden.

Für die entsprechende Sling-Modell-Oberfläche (`MyComponent`) wird in diesem Fall über [Jackson-Anmerkungen](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) definiert, wie sie exportiert (serialisiert) werden soll.

Es müssen die richtigen Anmerkungen für die Modell-Oberfläche angewendet werden, um zu definieren, welche Methoden serialisiert werden sollen. Standardmäßig werden alle Methoden, die die übliche Benennungskonvention für Getter einhalten, serialisiert und leiten ihre JSON-Eigenschaftsnamen natürlich von den Getter-Namen ab. Um dies zu vermeiden bzw. zu überschreiben, benennen Sie die JSON-Eigenschaft mit `@JsonIgnore` oder `@JsonProperty` um.

## Beispiel {#example}

[Die Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) unterstützen den JSON-Export und können als Referenz verwendet werden.

Ein Beispiel ist die Sling-Modell-Implementierung der Bild-Kernkomponente und deren kommentierte Oberfläche.

## Verwandte Dokumentation {#related-documentation}

Weitere Informationen finden Sie unter:

* [Inhaltsfragmente](/help/sites-cloud/administering/content-fragments/overview.md)
* [Inhaltsfragmentmodelle](/help/sites-cloud/administering/content-fragments/content-fragment-models.md)
* [Bearbeitung mit Inhaltsfragmenten](/help/sites-cloud/authoring/fundamentals/content-fragments.md)
* [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) und die [Inhaltsfragmentkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=de)
