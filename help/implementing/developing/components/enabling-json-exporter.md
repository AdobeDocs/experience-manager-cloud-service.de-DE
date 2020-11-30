---
title: Aktivieren eines JSON-Exports für eine Komponente
description: Komponenten können angepasst werden, um einen JSON-Export ihrer Inhalte basierend auf einem Modeler-Framework zu generieren.
translation-type: tm+mt
source-git-commit: 83c27daae4e8ae2ae6a8f115c9da9527971c6ecb
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 68%

---


# Aktivieren eines JSON-Exports für eine Komponente {#enabling-json-export-for-a-component}

Komponenten können angepasst werden, um einen JSON-Export ihrer Inhalte basierend auf einem Modeler-Framework zu generieren.

## Überblick{#overview}

The JSON Export is based on [Sling Models](https://sling.apache.org/documentation/bundles/models.html), and on the [Sling Model Exporter](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130) framework (which itself relies on [Jackson annotations](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations)).

Das bedeutet, dass die Komponente über ein Sling-Modell verfügen muss, wenn JSON exportiert werden soll. Deshalb müssen Sie diese beiden Schritte befolgen, um einen JSON-Export für eine beliebige Komponente zu aktivieren.

* [Definieren eines Sling-Modells für die Komponente](#define-a-sling-model-for-the-component)
* [Kommentieren der Sling-Modell-Oberfläche](#annotate-the-sling-model-interface)

## Definieren eines Sling-Modells für die Komponente {#define-a-sling-model-for-the-component}

Zunächst muss ein Sling-Modell für die Komponente definiert werden.

>[!NOTE]
>
>For an example of using Sling Models see the article [Developing Sling Model Exporters in AEM](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/develop-sling-model-exporter.html).

Die Implementierungsklasse des Sling-Modells muss wie folgt kommentiert werden:

```java
@Model(... adapters = {..., ComponentExporter.class})
@Exporter(name = ExporterConstants.SLING_MODEL_EXPORTER_NAME, extensions = ExporterConstants.SLING_MODEL_EXTENSION)
@JsonSerialize(as = MyComponent.class)
```

This ensures that your component could be exported on its own, using the `.model` selector and the `.json` extension.

Außerdem kann die Sling-Modell-Klasse dadurch in der `ComponentExporter`-Oberfläche übernommen werden.

>[!NOTE]
>
>Jackson-Anmerkungen werden in der Regel nicht auf der Ebene der Sling-Modell-Klasse festgelegt, sondern auf der Ebene der Modell-Oberfläche. Damit wird sichergestellt, dass der JSON-Export als Teil der Komponenten-API gewertet wird.

>[!NOTE]
>
>The `ExporterConstants` and `ComponentExporter` classes come from the `com.adobe.cq.export.json` bundle.

### Mehrere Selektoren verwenden {#multiple-selectors}

Obwohl es sich nicht um einen Standard-Anwendungsfall handelt, ist es möglich, zusätzlich zum `model` Selektor mehrere Selektoren zu konfigurieren.

```
https://<server>:<port>/content/page.model.selector1.selector2.json
```

In einem solchen Fall muss der `model` Selektor jedoch der erste Selektor sein und die Erweiterung muss `.json`sein.

## Anmerkungen für die Sling-Modell-Oberfläche {#annotate-the-sling-model-interface}

Damit sie im JSON-Exporter-Framework beachtet wird, sollte die `ComponentExporter`-Oberfläche (oder `ContainerExporter` bei Container-Komponenten) in der Modell-Oberfläche implementiert werden.

The corresponding Sling Model interface (`MyComponent`) would be then annotated using [Jackson annotations](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) to define how it should be exported (serialized).

Es müssen die richtigen Anmerkungen für die Modell-Oberfläche angewendet werden, um zu definieren, welche Methoden serialisiert werden sollen. Standardmäßig werden alle Methoden serialisiert, die die gängigen Benennungskonventionen für Abfragemethoden einhalten. Ihre JSON-Eigenschaftsnamen werden dabei naturgemäß von den Namen der Abfragemethode abgeleitet. This can be prevented or overridden using `@JsonIgnore` or `@JsonProperty` to rename the JSON property.

## Beispiel {#example}

[Die Hauptkomponenten](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/introduction.html) unterstützen den JSON-Export und können als Referenz verwendet werden.

Ein Beispiel ist die Sling-Modell-Implementierung der Bild-Kernkomponente und deren kommentierte Oberfläche.

## Verwandte Dokumentation {#related-documentation}

Weitere Informationen finden Sie unter:

* [Inhaltsfragmente im Benutzerhandbuch &quot;Assets&quot;](/help/assets/content-fragments/content-fragments.md)
* [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)
* [Bearbeitung mit Inhaltsfragmenten](/help/sites-cloud/authoring/fundamentals/content-fragments.md)
* [Kernkomponenten](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/introduction.html) und die [Inhaltsfragmentkomponente](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/components/content-fragment-component.html)
