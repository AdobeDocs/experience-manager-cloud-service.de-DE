---
title: Aktivieren eines JSON-Exports für eine Komponente
description: Komponenten können angepasst werden, um einen JSON-Export ihrer Inhalte basierend auf einem Modeler-Framework zu generieren.
exl-id: e9be5c0c-618e-4b56-a365-fcdd185ae808
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 07327f80b23e1e6fdbb3fb49d861221877724d39
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 100%

---

# Aktivieren eines JSON-Exports für eine Komponente {#enabling-json-export-for-a-component}

Komponenten können angepasst werden, um einen JSON-Export ihrer Inhalte basierend auf einem Modeler-Framework zu generieren.

## Überblick {#overview}

Der JSON-Export basiert auf [Sling-Modellen](https://sling.apache.org/documentation/bundles/models.html) und auf dem Framework des [Sling Model Exporter](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130) (der sich wiederum auf [Jackson-Anmerkungen](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) stützt).

Das bedeutet, dass die Komponente über ein Sling-Modell verfügen muss, wenn JSON exportiert werden soll. Führen Sie daher diese beiden Schritte aus, um den JSON-Export für jede Komponente zu aktivieren.

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
>Jackson-Anmerkungen werden in der Regel nicht auf der Ebene der Sling-Modell-Klasse festgelegt, sondern auf der Ebene der Modell-Oberfläche. Damit wird sichergestellt, dass der JSON-Export als Teil der Komponenten-API gewertet wird.

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

Es müssen die richtigen Anmerkungen für die Modell-Oberfläche angewendet werden, um zu definieren, welche Methoden serialisiert werden sollen. Standardmäßig werden alle Methoden serialisiert, die die gängigen Namenskonventionen für Abfragemethoden einhalten. Ihre JSON-Eigenschaftsnamen werden dabei naturgemäß von den Namen der Abfragemethode abgeleitet. Um dies zu vermeiden bzw. zu überschreiben, benennen Sie die JSON-Eigenschaft mit `@JsonIgnore` oder `@JsonProperty` um.

## Beispiel {#example}

[Die Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) unterstützen den JSON-Export und können als Referenz verwendet werden.

Ein Beispiel ist die Sling-Modell-Implementierung der Bild-Kernkomponente und deren kommentierte Oberfläche.

## Verwandte Dokumentation {#related-documentation}

* [Inhaltsfragmente](/help/sites-cloud/administering/content-fragments/overview.md)
* [Inhaltsfragmentmodelle](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md)
* [Bearbeitung mit Inhaltsfragmenten](/help/sites-cloud/authoring/fragments/content-fragments.md)
* [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) und die [Inhaltsfragmentkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=de)
