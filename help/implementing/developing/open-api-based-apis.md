---
title: OpenAPI-basierte APIs
description: Erfahren Sie mehr über die AEM as a Cloud Service-Unterstützung für OpenAPI-basierte APIs
feature: Developing
role: Admin, Architect, Developer
exl-id: 4aeafba9-8f9e-4ecb-9e37-8d048b0474cc
source-git-commit: e735f7d2a39e3165907969d2e27565639499a636
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 2%

---

# OpenAPI-basierte APIs {#openapi-based-apis}

>[!NOTE]
>
>OpenAPIs sind als Teil eines Early-Access-Programms verfügbar. Wenn Sie daran interessiert sind, darauf zuzugreifen, empfehlen wir Ihnen, eine E-Mail an [aem-apis@adobe.com](mailto:aem-apis@adobe.com) mit einer Beschreibung Ihres Anwendungsfalls zu senden.

Neuere AEM as a Cloud Service-APIs folgen der OpenAPI-Spezifikation und erzeugen somit konsistente, gut dokumentierte und benutzerfreundliche APIs. Detaillierte Informationen finden Sie auf den folgenden Seiten:

* Ein [-Tutorial ](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/invoke-api-using-oauth-s2s) Konfigurieren und Aufrufen von OpenAPI-basierten AEM-APIs mithilfe der Server-zu-Server-Authentifizierung.
* Informative [Handbücher](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/) einschließlich [API-Konzepte und -Syntax](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/how-to/).
* API-Endpunkt [Referenzdokumentation](https://developer.adobe.com/experience-cloud/experience-manager-apis/) wobei einige der APIs OpenAPI-basiert sind, z. B. [diese Sites-API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/?lang=de). Die Referenzdokumentation enthält auch einen API-Playground, der es einfach macht, einen Endpunkt mithilfe eines mit der Adobe Developer Console generierten Bearer-Tokens auszuprobieren.

Ein gängiger API-Anwendungsfall umfasst Integrationen mit Systemen wie CRM oder PIM, bei denen AEM-APIs aufgerufen werden, um Daten abzurufen oder beizubehalten. Im Rahmen der Integrationsimplementierung können Anwendungen [von AEM ausgelöste Ereignisse](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-eventing/overview) abonnieren, wodurch Geschäftslogik in Adobe App Builder oder einer anderen Infrastruktur Trigger werden kann.

Die unterstützten API-Authentifizierungstypen unterscheiden sich je nach Endpunkt, können aber OAuth Server-zu-Server, OAuth Web App und OAuth Single Page App (SPA) sein.

>[!NOTE]
>
> Das [End-to-End-Tutorial](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/invoke-api-using-oauth-s2s) ist eine empfohlene Ressource, in der Sie erfahren, wie Sie die OpenAPI-basierten AEM-APIs konfigurieren und aufrufen.


## API-Zugriff konfigurieren {#configuring-api-access}

Viele OpenAPI-basierte AEM-APIs erfordern eine Authentifizierung, für die Anmeldeinformationen mithilfe von [Adobe Developer Console generiert werden ](https://developer.adobe.com/developer-console/docs/guides/). Die Konfiguration umfasst die folgenden Schritte:

1. Stellen Sie sicher, dass die [Produktprofile“ Ihres AEM-Programms aktualisiert ](/help/onboarding/aem-cs-team-product-profiles.md#aem-product-profiles) und ein entsprechender Service für den Zugriff auf die gewünschte API aktiviert ist.
1. Erstellen Sie ein neues Projekt in Adobe Developer Console und fügen Sie die gewünschten API(s) zum Projekt hinzu, wobei Sie auch den entsprechenden Authentifizierungstyp auswählen.
1. Generieren Sie die Berechtigung, die später beim Aufrufen der API zum Austausch gegen ein Bearer-Token verwendet wird.
1. Registrieren Sie die Client-ID bei der Umgebung, indem Sie eine YAML-Datei konfigurieren, die mithilfe der Konfigurations-Pipeline (oder der Befehlszeile für RDEs) bereitgestellt wird.

Eine schrittweise Anleitung [ Sie im Tutorial ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/setup) Einrichten von OpenAPI-basierten APIs .

## Registrieren einer Client-ID {#registering-a-client-id}

Die Client-IDs umfassen die APIs in einem Adobe Developer Console-Projekt für bestimmte AEM-Umgebungen. Dies wird wie folgt erreicht:

1. Erstellen Sie eine Datei mit dem Namen `api.yaml` oder ähnlich mit einer Konfiguration wie dem folgenden Ausschnitt, einschließlich der gewünschten Ebenen (Autor, Veröffentlichung, Vorschau). `Client_id` sollten aus Ihren Adobe Developer Console-API-Projekten stammen.

   Die Eigenschaften `kind`, `version` und `metadata` werden im Artikel [Pipeline konfigurieren](/help/operations/config-pipeline.md#common-syntax) beschrieben. Der Wert der `kind`-Eigenschaft sollte auf &quot;*&quot;* und die `version`-Eigenschaft auf &quot;*&quot;*.

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

1. Platzieren Sie die Datei an einer beliebigen Stelle in einem Ordner der obersten Ebene mit dem Namen `config` oder Ähnliches, wie unter [Pipeline konfigurieren](/help/operations/config-pipeline.md#folder-structure) beschrieben.
1. Erstellen Sie für andere Umgebungstypen als RDE (die Befehlszeilen-Tools verwendet) eine zielgerichtete Bereitstellungskonfigurations-Pipeline in Cloud Manager, wie in [diesem Abschnitt) ](/help/operations/config-pipeline.md#creating-and-managing) Artikel „Pipeline konfigurieren“ beschrieben. Beachten Sie, dass Full-Stack-Pipelines und Web-Stufen-Pipelines die Konfigurationsdatei nicht bereitstellen.
1. Stellen Sie die Konfiguration bereit.
