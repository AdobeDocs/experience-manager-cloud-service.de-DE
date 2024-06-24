---
title: Konfiguration des Referrer-Filters mit AEM Headless
description: Der Referrer-Filter von Adobe Experience Manager ermöglicht den Zugriff über Drittanbieter-Hosts. Eine OSGi-Konfiguration für den Referrer-Filter ist erforderlich, um den Zugriff auf den GraphQL-Endpunkt für Headless-Anwendungen zu ermöglichen.
feature: Headless, GraphQL API
exl-id: e2e3d2dc-b839-4811-b5d1-38ed8ec2cc87
solution: Experience Manager
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '275'
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

Um beispielsweise Zugriff auf Anfragen mit dem Referrer `my.domain` zu gewähren, können Sie:

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

>[!CAUTION]
>
>Der Kunde ist für Folgendes verantwortlich:
>
>* Nur Zugriff auf vertrauenswürdige Domains gewähren
>* Sicherstellen, dass keine vertraulichen Informationen offengelegt werden
>* Keine Platzhaltersyntax [*] verwenden. Dadurch wird der authentifizierte Zugriff auf den GraphQL-Endpunkt deaktiviert und zusätzlich der Öffentlichkeit zugänglich gemacht.

>[!CAUTION]
>
>Alle GraphQL-[Schemata](#schema-generation) (abgeleitet von Inhaltsfragmentmodellen, die **aktiviert** wurden) können über den GraphQL-Endpunkt gelesen werden.
>
>Das bedeutet, dass Sie sicherstellen müssen, dass keine vertraulichen Daten verfügbar sind, da sie auf diese Weise an die Öffentlichkeit gelangen könnten. Dazu gehören beispielsweise Informationen, die als Feldnamen in der Modelldefinition vorhanden sein könnten.
