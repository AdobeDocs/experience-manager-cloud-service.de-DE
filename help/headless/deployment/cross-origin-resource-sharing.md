---
title: Cross-Origin Resource Sharing (CORS)-Konfiguration mit AEM Headless
description: Die Cross-Origin Resource Sharing (CORS) von Adobe Experience Manager ermöglicht Headless-Webanwendungen, clientseitige Aufrufe an AEM durchzuführen. Eine CORS-Konfiguration ist erforderlich, um den Zugriff auf den GraphQL-Endpunkt zu ermöglichen.
feature: GraphQL API
source-git-commit: 0cc131209f497241949f8da6e8144dfcaffe7e6e
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 28%

---


# CORS-Konfiguration (Cross-Origin Resource Sharing)

>[!NOTE]
>
>Einen detaillierten Überblick über die CORS-Richtlinie zur gemeinsamen Nutzung von Ressourcen in AEM finden Sie unter [Grundlegendes zur gemeinsamen Nutzung gemeinsamer Ressourcen (Cross-Origin Resource Sharing – CORS)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=de#understand-cross-origin-resource-sharing-(cors)).

Um auf den GraphQL-Endpunkt zuzugreifen, muss eine CORS-Richtlinie konfiguriert und einem AEM Projekt hinzugefügt werden, das [bereitgestellt für AEM über Cloud Manager](/help/implementing/cloud-manager/deploy-code.md). Dazu wird eine entsprechende OSGi-CORS-Konfigurationsdatei für den/die gewünschten Endpunkt(e) hinzugefügt. Es können mehrere CORS-Konfigurationen erstellt und in verschiedenen Umgebungen bereitgestellt werden. Beispiele finden Sie im Abschnitt [WKND-Referenz-Site](https://github.com/adobe/aem-guides-wknd/tree/master/ui.config/src/main/content/jcr_root/apps/wknd/osgiconfig)

Die CORS-Konfiguration muss einen vertrauenswürdigen Website-Ursprung angeben `alloworigin` oder `alloworiginregexp` für die der Zugang gewährt werden muss.

Die Konfigurationsdatei muss wie folgt benannt sein: `com.adobe.granite.cors.impl.CORSPolicyImpl~appname-graphql.cfg.json` where `appname` spiegelt den Namen Ihrer Anwendung wider.

So gewähren Sie beispielsweise Zugriff auf den GraphQL-Endpunkt `/content/cq:graphql/wknd/endpoint` und der Endpunkt für persistente Abfragen für `https://my.domain` Sie können Folgendes verwenden:

```json
{
  "supportscredentials":false,
  "supportedmethods":[
    "GET",
    "HEAD",
    "POST"
  ],
  "exposedheaders":[
    ""
  ],
  "alloworigin":[
    "https://my.domain"
  ],
  "maxage:Integer":1800,
  "alloworiginregexp":[
    ""
  ],
  "supportedheaders":[
    "Origin",
    "Accept",
    "X-Requested-With",
    "Content-Type",
    "Access-Control-Request-Method",
    "Access-Control-Request-Headers"
  ],
  "allowedpaths":[
    "/content/cq:graphql/wknd/endpoint.json",
    "/graphql/execute.json/.*"
  ]
}
```

Wenn Sie einen Vanity-Pfad für den Endpunkt konfiguriert haben, können Sie ihn auch in `allowedpaths` verwenden.


