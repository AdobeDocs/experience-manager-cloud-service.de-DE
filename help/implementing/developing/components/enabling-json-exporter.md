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

Der JSON-Export basiert auf [Sling-Modellen](https://sling.apache.org/documentation/bundles/models.html) und auf dem [Sling-Modell-Exporter](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130)-Framework (das wiederum auf [Jackson-Anmerkungen](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) basiert).

Das bedeutet, dass die Komponente über ein Sling-Modell verfügen muss, wenn JSON exportiert werden soll. Deshalb müssen Sie diese beiden Schritte befolgen, um einen JSON-Export für eine beliebige Komponente zu aktivieren.

* [Definieren eines Sling-Modells für die Komponente](#define-a-sling-model-for-the-component)
* [Kommentieren der Sling-Modell-Oberfläche](#annotate-the-sling-model-interface)

## Definieren eines Sling-Modells für die Komponente {#define-a-sling-model-for-the-component}

Zunächst muss ein Sling-Modell für die Komponente definiert werden.

>[!NOTE]
>
>Ein Beispiel für die Verwendung von Sling-Modellen finden Sie im Artikel [Developing Sling Model Exporters in AEM](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/develop-sling-model-exporter.html).

Die Implementierungsklasse des Sling-Modells muss wie folgt kommentiert werden:

```java
@Model(... adapters = {..., ComponentExporter.class})
@Exporter(name = ExporterConstants.SLING_MODEL_EXPORTER_NAME, extensions = ExporterConstants.SLING_MODEL_EXTENSION)
@JsonSerialize(as = MyComponent.class)
```

Dadurch wird sichergestellt, dass Ihre Komponente mit der Auswahl `.model` und der Erweiterung `.json` selbst exportiert werden kann.

Außerdem kann die Sling-Modell-Klasse dadurch in der `ComponentExporter`-Oberfläche übernommen werden.

>[!NOTE]
>
>Jackson-Anmerkungen werden in der Regel nicht auf der Ebene der Sling-Modell-Klasse festgelegt, sondern auf der Ebene der Modell-Oberfläche. Damit wird sichergestellt, dass der JSON-Export als Teil der Komponenten-API gewertet wird.

>[!NOTE]
>
>Die Klassen `ExporterConstants` und `ComponentExporter` stammen aus dem `com.adobe.cq.export.json`-Bundle.

### Verwenden mehrerer Selektoren {#multiple-selectors}

Obwohl es sich nicht um einen Standardverwendungsfall handelt, können mehrere Selektoren zusätzlich zum Selektor `model` konfiguriert werden.

```
https://<server>:<port>/content/page.model.selector1.selector2.json
```

In einem solchen Fall muss der Selektor `model` jedoch der erste Selektor sein und die Erweiterung muss `.json` sein.

## Anmerkungen für die Sling-Modell-Oberfläche {#annotate-the-sling-model-interface}

Damit sie im JSON-Exporter-Framework beachtet wird, sollte die `ComponentExporter`-Oberfläche (oder `ContainerExporter` bei Container-Komponenten) in der Modell-Oberfläche implementiert werden.

Die entsprechende Sling-Modell-Schnittstelle (`MyComponent`) wird dann mit [Jackson-Anmerkungen](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) kommentiert, um zu definieren, wie sie exportiert (serialisiert) werden soll.

Es müssen die richtigen Anmerkungen für die Modell-Oberfläche angewendet werden, um zu definieren, welche Methoden serialisiert werden sollen. Standardmäßig werden alle Methoden serialisiert, die die gängigen Benennungskonventionen für Abfragemethoden einhalten. Ihre JSON-Eigenschaftsnamen werden dabei naturgemäß von den Namen der Abfragemethode abgeleitet. Dies kann verhindert oder überschrieben werden, indem die JSON-Eigenschaft umbenannt wird.`@JsonProperty``@JsonIgnore`

## Beispiel {#example}

[Die Core-](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/introduction.html) Komponenten unterstützen den JSON-Export und können als Referenz verwendet werden.

Ein Beispiel ist die Sling-Modell-Implementierung der Bild-Kernkomponente und deren kommentierte Oberfläche.

## Verwandte Dokumentation {#related-documentation}

Weitere Informationen finden Sie unter:

* [Inhaltsfragmente im Benutzerhandbuch &quot;Assets&quot;](/help/assets/content-fragments/content-fragments.md)
* [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)
* [Bearbeitung mit Inhaltsfragmenten](/help/sites-cloud/authoring/fundamentals/content-fragments.md)
* [Kernkomponenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) und die [Inhaltsfragmentkomponente](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/components/content-fragment-component.html)
