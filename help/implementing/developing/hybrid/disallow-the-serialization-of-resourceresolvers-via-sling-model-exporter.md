---
title: Deaktivieren der Serialisierung von ResourceResolvers über den Sling Model Exporter
description: Deaktivieren der Serialisierung von ResourceResolvers über den Sling Model Exporter
exl-id: 63972c1e-04bd-4eae-bb65-73361b676687
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 85cef99dc7a8d762d12fd6e1c9bc2aeb3f8c1312
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 100%

---

# Deaktivieren der Serialisierung von ResourceResolvers über den Sling Model Exporter {#disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter}

Mit der Funktion Sling Model Exporter können Sling Models-Objekte in ein JSON-Format serialisiert werden. Diese Funktion wird häufig verwendet, da sie es SPAs (Single Page Applications) ermöglicht, einfach auf Daten aus AEM zuzugreifen. Auf der Implementierungsseite wird die Jacson Databind-Bibliothek verwendet, um diese Objekte zu serialisieren.

Die Serialisierung ist ein rekursiver Vorgang. Ausgehend von einem „Stammobjekt“ durchläuft es rekursiv alle infrage kommenden Objekte und serialisiert sie und ihre untergeordneten Elemente. Eine Beschreibung der serialisierten Felder finden Sie im Artikel [Jackson – Entscheiden, welche Felder serialisiert/desialisiert werden](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not).

Bei diesem Ansatz werden alle Objekttypen in JSON serialisiert, und natürlich kann auch ein Sling-`ResourceResolver`-Objekt serialisiert werden, wenn es von den Serialisierungsregeln abgedeckt wird. Dies ist problematisch, da der `ResourceResolver`-Dienst (und damit auch das Dienstobjekt, das ihn darstellt) potenziell vertrauliche Informationen enthält, die nicht offen gelegt werden sollten. Zum Beispiel:

* Die Benutzer-ID
* Die Suchpfade zum Auflösen relativer Pfade
* Die `propertyMap`.

Besonders empfindlich ist die `propertyMap` (siehe API-Dokumentation von [`getPropertyMap`](https://sling.apache.org/apidocs/sling12/org/apache/sling/api/resource/ResourceResolver.html#getPropertyMap--)), da es sich um eine interne Datenstruktur handelt, die für viele Zwecke verwendet werden kann – z. B. zum Zwischenspeichern von Objekten, die denselben Lebenszyklus wie der `ResourceResolver` haben. Die Serialisierung dieser Daten kann Implementierungsdetails preisgeben und möglicherweise Auswirkungen auf die Sicherheit haben, da Daten offengelegt werden, die für Endbenutzende nicht lesbar und zugänglich sein sollten. Aus diesem Grund sollten `ResourceResolvers` nicht in JSON serialisiert werden.

Adobe plant, die Serialisierung von `ResourceResolvers` in einem zweistufigen Ansatz zu deaktivieren:

1. Ab AEM as a Cloud Service Version 14697 protokolliert AEM eine Warnmeldung, wenn ein `ResourceResolver` serialisiert wird. Es wird allen Kundinnen und Kunden empfohlen, ihre Anwendungsprotokolle auf diese Protokollanweisungen zu überprüfen und ihre Code-Basis entsprechend anzupassen.
1. Zu einem späteren Zeitpunkt wird Adobe die Serialisierung von ResourceResolvers als JSON deaktivieren.

## Implementierung {#implementation}

Die WARN-Meldung wird sowohl in AEM as a Cloud Service als auch in lokalen AEM SDK-Instanzen protokolliert und sieht wie folgt aus:

```
[127.0.0.1 [1705061734620] GET /content/../page.model.json HTTP/1.1] org.apache.sling.models.jacksonexporter.impl.JacksonExporter A ResourceResolver is serialized with all its private fields containing implementation details you should not disclose. Please review your Sling Model implementation(s) and remove all public accessors to a ResourceResolver.
```

Diese Protokollmeldung bedeutet, dass während des Serialisierungsprozesses von `/content/…/page` in JSON ein `ResourceResolver` bereits serialisiert ist. Durch die Abfrage von `/content/../page.model.json` können Sie überprüfen, wo genau die Felder von `ResourceResolver` angezeigt werden, und dies zur Identifizierung der Sling-Modellklasse verwenden, die dieses Verhalten tatsächlich auslöst.


>[!NOTE]
>
>AEM-Kernkomponenten wurden dahingehend überprüft, dass sie von diesem Problem nicht betroffen sind.

## Angeforderte Aktion {#requested-action}

Adobe fordert alle Kundinnen und Kunden auf, ihre Anwendungsprotokolle und Codebasis zu überprüfen, um festzustellen, ob sie von diesem Problem betroffen sind, und gegebenenfalls die benutzerdefinierte Anwendung zu ändern, sodass diese WARN-Meldung nicht mehr angezeigt wird.

Es wird davon ausgegangen, dass diese erforderlichen Änderungen in den meisten Fällen unkompliziert sind, da die `ResourceResolver`-Objekte in der JSON-Ausgabe überhaupt nicht erforderlich sind, weil die dort enthaltenen Informationen normalerweise nicht für Frontend-Anwendungen erforderlich sind. Das bedeutet, dass es in den meisten Fällen ausreichen sollte, das `ResourceResolver`-Objekt von der Berücksichtigung durch Jackson auszuschließen (siehe die [Regeln](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not)).

Wenn ein Sling-Modell von diesem Problem betroffen ist, aber nicht geändert wird, wird die explizite Deaktivierung der Serialisierung des `ResourceResolver`-Objekts (wie von Adobe als 2. Schritt ausgeführt) eine Änderung in der JSON-Ausgabe erzwingen.
