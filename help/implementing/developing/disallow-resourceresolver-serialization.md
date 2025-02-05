---
title: Deaktivieren der Serialisierung von ResourceResolvers über den Sling Model Exporter
description: Deaktivieren der Serialisierung von ResourceResolvers über den Sling Model Exporter
exl-id: 63972c1e-04bd-4eae-bb65-73361b676687
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 35%

---

# Deaktivieren der Serialisierung von ResourceResolvers über den Sling Model Exporter {#disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter}

Die Sling Model Exporter-Funktion ermöglicht das Serialisieren von Sling-Modell-Objekten in das JSON-Format. Diese Funktion wird häufig verwendet, da sie es SPAs (Single Page Applications) ermöglicht, einfach auf Daten aus AEM zuzugreifen. Auf der Implementierungsseite wird die Jackson-Datenbindungsbibliothek verwendet, um diese Objekte zu serialisieren.

Die Serialisierung ist ein rekursiver Vorgang. Ausgehend von einem „Stammobjekt“ durchläuft es rekursiv alle geeigneten Objekte und serialisiert sie und ihre untergeordneten Elemente. Eine Beschreibung der serialisierten Felder finden Sie im Artikel [Jackson - Decide What Fields Get Serialized/Deserialized](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not).

Bei diesem Ansatz werden alle Objekttypen in JSON serialisiert. Natürlich kann es auch ein Sling-`ResourceResolver` serialisieren, wenn es von den Serialisierungsregeln abgedeckt wird. Dies ist problematisch, da der `ResourceResolver`-Dienst (und damit auch das Dienstobjekt, das ihn darstellt) potenziell vertrauliche Informationen enthält, die nicht offen gelegt werden sollten. Zum Beispiel:

* Die Benutzer-ID
* Die Suchpfade zum Auflösen relativer Pfade
* Die `propertyMap`

Besonders sensibel ist die `propertyMap` (siehe API-Dokumentation von [`getPropertyMap`](https://sling.apache.org/apidocs/sling12/org/apache/sling/api/resource/ResourceResolver.html#getPropertyMap--)), da es sich um eine interne Datenstruktur handelt, die für viele Zwecke verwendet werden kann, z. B. zum Caching von Objekten, die denselben Lebenszyklus wie die `ResourceResolver` haben. Das Serialisieren dieser Daten kann zu undichten Implementierungsdetails führen und sich möglicherweise auf die Sicherheit auswirken, da Daten offen gelegt werden, die für Endbenutzende nicht lesbar und zugänglich sein sollten. Aus diesem Grund sollten `ResourceResolvers` nicht in JSON serialisiert werden.

Adobe plant, die Serialisierung von `ResourceResolvers` in einem zweistufigen Ansatz zu deaktivieren:

1. Ab AEM as a Cloud Service-Version 14697 protokolliert AEM bei jeder Serialisierung eines `ResourceResolver` eine Warnmeldung. Es wird allen Kundinnen und Kunden empfohlen, ihre Anwendungsprotokolle auf diese Protokollanweisungen zu überprüfen und ihre Code-Basis entsprechend anzupassen.
1. Zu einem späteren Zeitpunkt wird Adobe die Serialisierung von `ResourceResolver`s als JSON deaktivieren.

## Implementierung {#implementation}

Die WARN-Meldung wird sowohl in AEM as a Cloud Service als auch in lokalen AEM SDK-Instanzen protokolliert und sieht wie folgt aus:

```text
[127.0.0.1 [1705061734620] GET /content/../page.model.json HTTP/1.1] org.apache.sling.models.jacksonexporter.impl.JacksonExporter A ResourceResolver is serialized with all its private fields containing implementation details you should not disclose. Please review your Sling Model implementation(s) and remove all public accessors to a ResourceResolver.
```

Diese Protokollmeldung bedeutet, dass während des Serialisierungsprozesses von `/content/…/page` in JSON ein `ResourceResolver` bereits serialisiert ist. Durch die Abfrage von `/content/../page.model.json` können Sie überprüfen, wo genau die Felder von `ResourceResolver` angezeigt werden, und dies zur Identifizierung der Sling-Modellklasse verwenden, die dieses Verhalten tatsächlich auslöst.


>[!NOTE]
>
>[AEM-Kernkomponenten](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/introduction) wurden so validiert, dass sie von diesem Problem nicht betroffen sind.

## Angeforderte Aktion {#requested-action}

Adobe fordert alle Kunden auf, ihre Anwendungsprotokolle und Code-Basen zu überprüfen, um festzustellen, ob sie von diesem Problem betroffen sind, und die benutzerdefinierte Anwendung bei Bedarf zu ändern, sodass diese Warnmeldung nicht mehr in den Protokollen angezeigt wird.

Es wird davon ausgegangen, dass diese erforderlichen Änderungen in den meisten Fällen unkompliziert sind. Die `ResourceResolver` Objekte sind in der JSON-Ausgabe überhaupt nicht erforderlich, da die dort enthaltenen Informationen normalerweise von Frontend-Anwendungen nicht benötigt werden, was in den meisten Fällen ausreichen sollte, um das `ResourceResolver` Objekt von der Berücksichtigung durch Jackson auszuschließen (siehe [Regeln](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not).)

Wenn ein Sling-Modell von diesem Problem betroffen, aber nicht geändert wird, erzwingt die explizite Deaktivierung der Serialisierung des `ResourceResolver`-Objekts (wie durch Adobe als zweiter Schritt ausgeführt) eine Änderung in der JSON-Ausgabe.
