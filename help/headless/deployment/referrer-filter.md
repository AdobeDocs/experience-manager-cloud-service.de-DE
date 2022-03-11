---
title: Konfiguration des Referrer-Filters mit AEM Headless
description: Der Referrer-Filter von Adobe Experience Manager ermöglicht den Zugriff von Drittanbieter-Hosts. Eine OSGi-Konfiguration für den Referrer-Filter ist erforderlich, um den Zugriff auf den GraphQL-Endpunkt für Headless-Anwendungen zu ermöglichen.
feature: GraphQL API
exl-id: e2e3d2dc-b839-4811-b5d1-38ed8ec2cc87
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 58%

---

# Referrer-Filter {#referrer-filter}

Der Referrer-Filter von Adobe Experience Manager ermöglicht den Zugriff von Drittanbieter-Hosts. Eine OSGi-Konfiguration für den Referrer-Filter ist erforderlich, um den Zugriff auf den GraphQL-Endpunkt für Headless-Anwendungen zu ermöglichen.

Dies geschieht durch Hinzufügen einer entsprechenden OSGi-Konfiguration für den Referrer-Filter, die:

* einen vertrauenswürdigen Website-Hostnamen angibt (entweder `allow.hosts` oder `allow.hosts.regexp`),
* Zugriff auf diesen Hostnamen gewährt.

Der Name der Datei muss `org.apache.sling.security.impl.ReferrerFilter.cfg.json`.

Um beispielsweise Zugriff auf Anfragen mit dem Referrer `my.domain` zu gewähren, können Sie:

```xml
{
    "allow.empty":false,
    "allow.hosts":[
      "my.domain"
    ],
    "allow.hosts.regexp":[
      ""
    ],
    "filter.methods":[
      "POST",
      "PUT",
      "DELETE",
      "COPY",
      "MOVE"
    ],
    "exclude.agents.regexp":[
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
>Alle GraphQL-[Schemas](#schema-generation) (abgeleitet von Inhaltsfragmentmodellen, die **aktiviert** wurden) können über den GraphQL-Endpunkt gelesen werden.
>
>Das bedeutet, dass Sie sicherstellen müssen, dass keine vertraulichen Daten verfügbar sind, da sie auf diese Weise an die Öffentlichkeit gelangen könnten. Dazu gehören beispielsweise Informationen, die als Feldnamen in der Modelldefinition vorhanden sein könnten.
