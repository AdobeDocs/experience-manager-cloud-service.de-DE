---
title: Deaktivieren der Serialisierung von ResourceResolvers über den Sling Model Exporter
description: Deaktivieren der Serialisierung von ResourceResolvers über den Sling Model Exporter
exl-id: 63972c1e-04bd-4eae-bb65-73361b676687
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 100%

---

# Deaktivieren der Serialisierung von ResourceResolvers über den Sling Model Exporter {#disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter}

Mit der Funktion „Sling Model Exporter“ können Sling-Modellobjekte in ein JSON-Format serialisiert werden. Diese Funktion wird häufig verwendet, da sie es SPAs (Single Page Applications) ermöglicht, einfach auf Daten aus AEM zuzugreifen. Auf der Implementierungsseite wird die Jacson Databind-Bibliothek verwendet, um diese Objekte zu serialisieren.

Die Serialisierung ist ein rekursiver Vorgang. Ausgehend von einem „Stammobjekt“ durchläuft sie rekursiv alle infrage kommenden Objekte und serialisiert sie und ihre untergeordneten Elemente. Eine Beschreibung der serialisierten Felder finden Sie im Artikel [Jackson – Decide What Fields Get Serialized/Deserialized](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not).

Bei diesem Ansatz werden alle Objekttypen in JSON serialisiert. Natürlich kann auch ein Sling-`ResourceResolver`-Objekt serialisiert werden, wenn dieses den Serialisierungsregeln entspricht. Dies ist problematisch, da der `ResourceResolver`-Dienst (und damit auch das Dienstobjekt, das ihn darstellt) potenziell vertrauliche Informationen enthält, die nicht offen gelegt werden sollten. Beispiel:

* Die Benutzer-ID
* Die Suchpfade zum Auflösen relativer Pfade
* Die `propertyMap`

`propertyMap` ist besonders empfindlich (siehe API-Dokumentation von [`getPropertyMap`](https://sling.apache.org/apidocs/sling12/org/apache/sling/api/resource/ResourceResolver.html#getPropertyMap--)), da es sich um eine interne Datenstruktur handelt, die für viele Zwecke verwendet werden kann, z. B. zum Caching von Objekten mit demselben Lebenszyklus wie `ResourceResolver`. Die Serialisierung dieser Daten kann Implementierungsdetails preisgeben und möglicherweise Auswirkungen auf die Sicherheit haben, da Daten offengelegt werden, die für Endbenutzende nicht lesbar und zugänglich sein sollten. Aus diesem Grund sollten `ResourceResolvers` nicht in JSON serialisiert werden.

Adobe plant, die Serialisierung von `ResourceResolvers` in einem zweistufigen Ansatz zu deaktivieren:

1. Ab Version 14697 von AEM as a Cloud Service protokolliert AEM eine Warnmeldung, wenn ein `ResourceResolver` serialisiert wird. Es wird allen Kundinnen und Kunden empfohlen, ihre Anwendungsprotokolle auf diese Protokollanweisungen zu überprüfen und ihre Code-Basis entsprechend anzupassen.
1. Zu einem späteren Zeitpunkt wird Adobe die Serialisierung von `ResourceResolver` als JSON deaktivieren.

## Implementierung {#implementation}

Die WARN-Meldung wird sowohl in AEM as a Cloud Service als auch in lokalen AEM SDK-Instanzen protokolliert und sieht wie folgt aus:

```text
[127.0.0.1 [1705061734620] GET /content/../page.model.json HTTP/1.1] org.apache.sling.models.jacksonexporter.impl.JacksonExporter A ResourceResolver is serialized with all its private fields containing implementation details you should not disclose. Please review your Sling Model implementation(s) and remove all public accessors to a ResourceResolver.
```

Diese Protokollmeldung bedeutet, dass während des Serialisierungsprozesses von `/content/…/page` in JSON ein `ResourceResolver` bereits serialisiert ist. Durch die Abfrage von `/content/../page.model.json` können Sie überprüfen, wo genau die Felder von `ResourceResolver` angezeigt werden, und dies zur Identifizierung der Sling-Modellklasse verwenden, die dieses Verhalten tatsächlich auslöst.


>[!NOTE]
>
>Es wurde bestätigt, dass [AEM-Kernkomponenten](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/introduction) nicht von diesem Problem betroffen sind.

## Angeforderte Aktion {#requested-action}

Adobe fordert alle Kundinnen und Kunden auf, ihre Anwendungsprotokolle und Code-Basis zu überprüfen, um festzustellen, ob sie von diesem Problem betroffen sind. Gegebenenfalls soll die benutzerdefinierte Anwendung geändert werden, sodass diese Warnmeldung nicht mehr in den Protokollen angezeigt wird.

Es wird davon ausgegangen, dass diese erforderlichen Änderungen in den meisten Fällen unkompliziert sind. Die `ResourceResolver`-Objekte sind in der JSON-Ausgabe überhaupt nicht erforderlich, da die dort enthaltenen Informationen normalerweise von Frontend-Anwendungen nicht benötigt werden. Das reicht in den meisten Fällen aus, um das `ResourceResolver`-Objekt von der Berücksichtigung durch Jackson auszuschließen (siehe [Regeln](https://www.baeldung.com/jackson-field-serializable-deserializable-or-not).)

Wenn ein Sling-Modell von diesem Problem betroffen ist, aber nicht geändert wird, erzwingt die explizite Deaktivierung der Serialisierung des `ResourceResolver`-Objekts (wie von Adobe als zweiten Schritt ausgeführt) eine Änderung in der JSON-Ausgabe.
