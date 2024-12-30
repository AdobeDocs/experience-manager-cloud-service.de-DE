---
title: Konfiguration des Referrer-Filters mit AEM Headless
description: Der Referrer-Filter von Adobe Experience Manager ermöglicht den Zugriff über Drittanbieter-Hosts. Eine OSGi-Konfiguration für den Referrer-Filter ist erforderlich, um den Zugriff auf den GraphQL-Endpunkt für Headless-Anwendungen zu ermöglichen.
feature: Headless, GraphQL API
exl-id: e2e3d2dc-b839-4811-b5d1-38ed8ec2cc87
solution: Experience Manager
role: Admin, Developer
source-git-commit: 3096436f8057833419249d51cb6c15e6c28e9e13
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 100%

---

# Referrer-Filter {#referrer-filter}

Der Referrer-Filter von Adobe Experience Manager ermöglicht den Zugriff über Drittanbieter-Hosts.

Für den Referrer-Filter ist eine OSGi-Konfiguration erforderlich, um für Headless-Anwendungen den Zugriff auf den GraphQL-Endpunkt über HTTP POST zu ermöglichen. Bei der Verwendung von persistenten Abfragen von AEM Headless, die über HTTP GET auf AEM zugreifen, ist keine Konfiguration des Referrer-Filters erforderlich.

>[!WARNING]
> Der Referrer-Filter von AEM ist keine OSGi-Konfigurations-Factory, d. h., für einen AEM-Service ist immer nur eine Konfiguration aktiv. Nach Möglichkeit ist das Hinzufügen benutzerdefinierter Referrer-Filter-Konfigurationen zu vermeiden, da dies die nativen Konfigurationen von AEM überschreibt und die Produktfunktionalität beeinträchtigen kann.

Dies geschieht durch Hinzufügen einer entsprechenden OSGi-Konfiguration für den Referrer-Filter, die:

* einen vertrauenswürdigen Website-Hostnamen angibt (entweder `allow.hosts` oder `allow.hosts.regexp`),
* Zugriff auf diesen Hostnamen gewährt.

Der Name der Datei muss `org.apache.sling.security.impl.ReferrerFilter.cfg.json` lauten.

## Beispielkonfiguration {#example-configuration}

Um beispielsweise Zugriff auf Anfragen mit dem Referrer `my.domain` zu gewähren, können Sie:

>[!CAUTION]
>
>Dies ist ein grundlegendes Beispiel, das die Standardkonfiguration möglicherweise überschreibt. Sie müssen sicherstellen, dass Produktaktualisierungen immer auf alle Anpassungen angewendet werden.

```xml
{
    "allow.empty": false,
    "allow.hosts": [
      "my.domain"
    ],
    "allow.hosts.regexp": [
      ""
    ],
    "filter.methods": [
      "POST",
      "PUT",
      "DELETE",
      "COPY",
      "MOVE"
    ],
    "exclude.agents.regexp": [
      ""
    ]
}
```

## Datensicherheit {#data-security}

>[!CAUTION]
>
>Es liegt in Ihrer Verantwortung, die folgenden Punkte in vollem Umfang anzugehen.

Um sicherzustellen, dass Ihre Daten sicher bleiben, müssen Sie Folgendes sicherstellen:

* Zugriff wird **ausschließlich** vertrauenswürdigen Domains gewährt.

* Eine Platzhaltersyntax [`*`] wird **nicht** verwendet. Dadurch wird der authentifizierte Zugriff auf den GraphQL-Endpunkt deaktiviert und zusätzlich der Öffentlichkeit zugänglich gemacht.

* Vertrauliche Informationen werden **nie** offen gelegt; weder direkt noch indirekt:

   * Beispielsweise sind alle [GraphQL-Schemata](/help/headless/graphql-api/content-fragments.md#schema-generation):

      * von Inhaltsfragmentmodellen abgeleitet, die **aktiviert** wurden

     **und**

      * über den GraphQL-Endpunkt lesbar sind

     Dies bedeutet, dass Informationen verfügbar werden können, die in der Modelldefinition als Feldnamen vorhanden sind.

Sie müssen sicherstellen, dass keine sensiblen Daten auf irgendeine Weise verfügbar sind. Daher müssen solche Details sorgfältig bedacht werden.
