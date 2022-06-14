---
title: Konfiguration der herkunftsübergreifenden Ressourcennutzung (Cross-Origin Resource Sharing, CORS) mit AEM Headless
description: Das CORS von Adobe Experience Manager ermöglicht Headless-Webanwendungen, Client-seitige Aufrufe an AEM durchzuführen. Eine CORS-Konfiguration ist erforderlich, um den Zugriff auf den GraphQL-Endpunkt zu ermöglichen.
feature: GraphQL API
exl-id: 426be9f9-f44a-4744-ac08-e64bb97308a0
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 100%

---

# Konfiguration der herkunftsübergreifenden Ressourcennutzung (Cross-Origin Resource Sharing, CORS)

>[!NOTE]
>
>Einen detaillierten Überblick über die CORS-Richtlinie zur gemeinsamen Nutzung von Ressourcen in AEM finden Sie unter [Grundlegendes zur gemeinsamen Nutzung gemeinsamer Ressourcen (Cross-Origin Resource Sharing – CORS)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=de#understand-cross-origin-resource-sharing-(cors)).

Um auf den GraphQL-Endpunkt zuzugreifen, muss eine CORS-Richtlinie konfiguriert und einem AEM-Projekt hinzugefügt werden, das [in AEM über Cloud Manager bereitgestellt](/help/implementing/cloud-manager/deploy-code.md) wird. Dazu wird eine entsprechende OSGi-CORS-Konfigurationsdatei für den/die gewünschten Endpunkt(e) hinzugefügt. Es können mehrere CORS-Konfigurationen erstellt und in verschiedenen Umgebungen bereitgestellt werden. Beispiele finden Sie im Abschnitt [WKND-Referenz-Site](https://github.com/adobe/aem-guides-wknd/tree/master/ui.config/src/main/content/jcr_root/apps/wknd/osgiconfig)

Diese Konfiguration muss als vertrauenswürdige Website-Herkunft `alloworigin` oder `alloworiginregexp` angeben, für die der Zugriff gewährt werden muss.

Die Konfigurationsdatei muss wie folgt benannt sein: `com.adobe.granite.cors.impl.CORSPolicyImpl~appname-graphql.cfg.json`, wobei `appname` den Namen Ihrer Anwendung widerspiegelt.

Um beispielsweise den Zugriff auf den GraphQL-Endpunkt `/content/cq:graphql/wknd/endpoint` und den Persistenzabfrage-Endpunkt für `https://my.domain` zu gewähren, können Sie Folgendes verwenden:

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
