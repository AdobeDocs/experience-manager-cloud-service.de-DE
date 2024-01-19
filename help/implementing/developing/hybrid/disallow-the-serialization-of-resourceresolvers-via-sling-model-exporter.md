---
title: Deaktivieren der Serialisierung von ResourceResolvers über den Sling Model Exporter
description: Deaktivieren der Serialisierung von ResourceResolvers über den Sling Model Exporter
source-git-commit: 4543a4646719f8433df7589b21344433c43ab432
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# Deaktivieren der Serialisierung von ResourceResolvers über den Sling Model Exporter {#disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter}

Mit der Funktion Sling Model Exporter können Sling Models-Objekte in ein JSON-Format serialisiert werden. Diese Funktion wird häufig verwendet, da sie es SPA (Single Page Applications) ermöglicht, einfach auf Daten aus AEM zuzugreifen. Auf der Implementierungsseite wird die Jacson Databind-Bibliothek verwendet, um diese Objekte zu serialisieren.

Die Serialisierung ist ein rekursiver Vorgang. Ausgehend von einem &quot;Stammobjekt&quot;durchläuft es rekursiv alle Objekte und serialisiert sie und ihre untergeordneten Elemente. Eine Beschreibung der serialisierten Felder finden Sie unter [diesem Artikel](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not).

Bei diesem Ansatz werden alle Objekttypen in JSON serialisiert, und natürlich kann auch ein Sling serialisiert werden `ResourceResolver` -Objekt, wenn es von den Serialisierungsregeln abgedeckt wird. Dies ist problematisch, da die `ResourceResolver` -Dienst (und damit auch das Dienstobjekt, das ihn darstellt) potenziell vertrauliche Informationen enthält, die nicht offen gelegt werden sollten. Zum Beispiel:

* Die Benutzer-ID
* Suchpfade zum Auflösen relativer Pfade
* Die `propertyMap`.

Besonders empfindlich ist die `propertyMap` (siehe API-Dokumentation von [`getPropertyMap`](https://sling.apache.org/apidocs/sling12/org/apache/sling/api/resource/ResourceResolver.html#getPropertyMap--)), da es sich um eine interne Datenstruktur handelt, die für viele Zwecke verwendet werden kann - z. B. zum Zwischenspeichern von Objekten, die denselben Lebenszyklus wie das `ResourceResolver`. Die Serialisierung dieser Daten kann Details zur Implementierung überlappen und möglicherweise Auswirkungen auf die Sicherheit haben, da Daten offen gelegt werden, die für Endbenutzer nicht lesbar und zugänglich sein sollten. Aus diesem Grund `ResourceResolvers` sollten nicht in JSON serialisiert werden.

Adobe plant, die Serialisierung von `ResourceResolvers` in einem zweistufigen Ansatz:

1. Ab AEM as a Cloud Service Version 14697 `ResourceResolver` ist serialisiert AEM protokolliert eine Warnmeldung. Es wird allen Kunden empfohlen, ihre Anwendungsprotokolle auf diese Protokollanweisungen zu überprüfen und ihre Codebasis entsprechend anzupassen.
1. Zu einem späteren Zeitpunkt deaktiviert Adobe die Serialisierung von ResourceResolvers als JSON.

## Implementierung {#implementation}

Die WARN-Meldung wird sowohl in AEM as a Cloud Service als auch in lokalen AEM SDK-Instanzen protokolliert und sieht wie folgt aus:

```
[127.0.0.1 [1705061734620] GET /content/../page.model.json HTTP/1.1] org.apache.sling.models.jacksonexporter.impl.JacksonExporter A ResourceResolver is serialized with all its private fields containing implementation details you should not disclose. Please review your Sling Model implementation(s) and remove all public accessors to a ResourceResolver.
```

Diese Protokollmeldung bedeutet, dass während des Serialisierungsprozesses der `/content/…/page` in JSON a `ResourceResolver` ist bereits serialisiert. Auf Anfrage `/content/../page.model.json` Sie können überprüfen, wo genau die Felder der `ResourceResolver` werden angezeigt und verwenden Sie dies, um die Sling-Modell-Klasse zu identifizieren, die dieses Verhalten auslöst.


>[!NOTE]
>
>AEM Kernkomponenten wurden dahingehend überprüft, dass sie von diesem Problem nicht betroffen sind.

## Angeforderte Aktion {#requested-action}

Adobe fordert alle Kunden auf, ihre Anwendungsprotokolle und Codebasis zu überprüfen, um festzustellen, ob sie von diesem Problem betroffen sind, und gegebenenfalls die benutzerdefinierte Anwendung zu ändern, sodass diese WARN-Meldung nicht mehr angezeigt wird.

Es wird davon ausgegangen, dass diese erforderlichen Änderungen in den meisten Fällen direkt vorwärts erfolgen, da die `ResourceResolver` -Objekte sind in der JSON-Ausgabe überhaupt nicht erforderlich, da die dort enthaltenen Informationen normalerweise nicht für Frontend-Anwendungen erforderlich sind. Das bedeutet, dass es in den meisten Fällen ausreichen sollte, die `ResourceResolver` -Objekt, das von Jackson berücksichtigt wird (siehe [Regeln](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not)).

Wenn ein Sling-Modell von diesem Problem betroffen ist, aber nicht geändert wird, wird die explizite Deaktivierung der Serizalisierung des `ResourceResolver` -Objekt (wie von Adobe als 2. Schritt ausgeführt) erzwingt eine Änderung in der JSON-Ausgabe.



