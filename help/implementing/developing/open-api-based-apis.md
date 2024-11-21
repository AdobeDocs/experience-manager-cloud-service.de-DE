---
title: OpenAPI-basierte APIs
description: Informationen zur AEM as a Cloud Service-Unterstützung für OpenAPI-basierte APIs
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 9259b064a0a03db67333c522ebd918883859018f
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 1%

---


# OpenAPI-basierte APIs {#openapi-based-apis}

>[!NOTE]
>
>OpenAPIs sind im Rahmen eines Programms für frühzeitigen Zugriff verfügbar. Wenn Sie daran interessiert sind, darauf zuzugreifen, empfehlen wir Ihnen, [aem-apis@adobe.com](mailto:aem-apis@adobe.com) mit einer Beschreibung Ihres Anwendungsfalls per E-Mail zu versenden.

Neuere AEM as a Cloud Service-APIs folgen der OpenAPI-Spezifikation und erzeugen daher konsistente, gut dokumentierte und benutzerfreundliche APIs. Detaillierte Informationen finden Sie auf den folgenden Seiten:

* Ein [End-to-End-Tutorial](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) zum Konfigurieren und Aufrufen von OpenAPI-basierten AEM-APIs.
* Informative [Handbücher](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/), einschließlich [API-Konzepten und -Syntax](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/how-to/).
* API-Endpunkt [verweist auf Dokumentation](https://developer.adobe.com/experience-cloud/experience-manager-apis/), in der einige APIs auf OpenAPI basieren, z. B. [diese Sites-API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/?lang=de). Die Referenzdokumentation enthält auch einen API-Player, der es einfacher macht, einen Endpunkt mithilfe eines mit Adobe Developer Console generierten Trägertokens auszuprobieren.

Ein gängiges API-Nutzungsszenario umfasst Integrationen mit Systemen wie einem CRM oder PIM, bei denen AEM APIs aufgerufen werden, um Daten abzurufen oder beizubehalten. Im Rahmen der Integrationsimplementierung abonnieren Anwendungen möglicherweise [AEM Ereignisse](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-eventing/overview), was die Geschäftslogik in Adobe App Builder oder anderen Infrastrukturen Trigger.

Die unterstützten API-Authentifizierungstypen unterscheiden sich je nach Endpunkt, können jedoch OAuth Server-to-Server, OAuth Web App und OAuth Single Page App (SPA) sein.

>[!NOTE]
>
> Das Tutorial [End-to-End](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) ist eine empfohlene Ressource, um zu erfahren, wie Sie die OpenAPI-basierten AEM-APIs konfigurieren und aufrufen.


## API-Zugriff konfigurieren {#configuring-api-access}

Viele OpenAPI-basierte AEM-APIs erfordern eine Authentifizierung, für die Anmeldeinformationen mit [Adobe Developer Console](https://developer.adobe.com/developer-console/docs/guides/) generiert werden müssen. Die Konfiguration umfasst die folgenden Schritte, die im Tutorial veranschaulicht werden:

1. Stellen Sie sicher, dass die [Produktprofile Ihres AEM-Programms aktualisiert wurden](/help/onboarding/aem-cs-team-product-profiles.md#aem-product-profiles) und ein entsprechender Dienst für den Zugriff auf die gewünschte API aktiviert ist.
1. Erstellen Sie ein neues Projekt in Adobe Developer Console und fügen Sie die gewünschten APIs zum Projekt hinzu. Wählen Sie außerdem den entsprechenden Authentifizierungstyp aus.
1. Erstellen Sie die Berechtigung, die später zum Austausch eines Trägertokens beim Aufrufen der API verwendet wird.
1. Registrieren Sie die Client-ID in der Umgebung, indem Sie eine YAML-Datei konfigurieren, die mithilfe der Config Pipeline (oder der Befehlszeile für RDEs) bereitgestellt wird.

## Registrieren einer Client-ID {#registering-a-client-id}

Client-IDs ermöglichen den Umfang der APs in einem Adobe Developer Console-Projekt auf bestimmte AEM Umgebungen. Dies wird wie folgt erreicht:

1. Erstellen Sie eine Datei mit dem Namen `api.yaml` oder eine ähnliche Datei mit einer Konfiguration wie dem unten stehenden Codefragment, einschließlich der gewünschten Ebenen (Autor, Veröffentlichung, Vorschau). `Client_id` -Werte sollten aus Ihren Adobe Developer Console API-Projekten stammen.

   Die Eigenschaften `kind`, `version` und `metadata` werden im Artikel [Config Pipeline konfigurieren](/help/operations/config-pipeline.md#common-syntax) beschrieben. Der Eigenschaftswert `kind` sollte auf *API* und die Eigenschaft `version` auf *1* gesetzt werden.

   ```
   kind: "API"
   version: "1"
   metadata:
     envTypes: ["dev"]
   data:
     allowedClientIDs:
       author:
         - "<client_id>"
       publish:
         - "<client_id>"
       preview:
         - "<client_id>"
   ```

1. Platzieren Sie die Datei in einen Ordner der obersten Ebene mit dem Namen `config` oder einen ähnlichen Ordner, wie unter [Config Pipeline](/help/operations/config-pipeline.md#folder-structure) beschrieben.
1. Erstellen Sie für andere Umgebungstypen als RDE (die Befehlszeilen-Tools verwenden) eine zielgerichtete Bereitstellungskonfigurations-Pipeline in Cloud Manager, auf die in [diesem Abschnitt](/help/operations/config-pipeline.md#creating-and-managing) im Artikel Config Pipeline verwiesen wird. Beachten Sie, dass die Konfigurationsdatei nicht von den Pipelines für das vollständige Stapeln und von Pipelines für die Web-Ebene bereitgestellt wird.
1. Stellen Sie die Konfiguration bereit.





