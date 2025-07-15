---
title: OpenAPI-basierte APIs
description: Erfahren Sie mehr über die AEM as a Cloud Service-Unterstützung für OpenAPI-basierte APIs
feature: Developing
role: Admin, Architect, Developer
exl-id: 4aeafba9-8f9e-4ecb-9e37-8d048b0474cc
source-git-commit: 320fe55d652b94cd63dfe82d4165c1f957653a63
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 1%

---

# OpenAPI-basierte APIs {#openapi-based-apis}

Neuere AEM as a Cloud Service-APIs folgen der OpenAPI-Spezifikation und bieten daher einen konsistenten und gut dokumentierten Satz von APIs.

>[!NOTE]
>
> Ein [-Tutorial ist eine ](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/invoke-api-using-oauth-s2s) Ressource, in der Sie erfahren, wie Sie die OpenAPI-basierten AEM-APIs konfigurieren und aufrufen können.

Bei Endpunkten, für die eine Authentifizierung erforderlich ist, unterscheidet sich der Authentifizierungsansatz je nach Endpunkt, verwendet jedoch möglicherweise OAuth Server-zu-Server, OAuth Web App oder OAuth Single Page App (SPA). Anmeldeinformationen werden über Projekte in [Adobe Developer Console konfiguriert](https://developer.adobe.com/developer-console/).

Häufige API-Anwendungsfälle umfassen Integrationen mit Systemen wie CRM oder PIM, bei denen AEM-APIs aufgerufen werden, um Daten abzurufen oder beizubehalten. Im Rahmen der Integrationsimplementierung können Anwendungen [von AEM ausgelöste Ereignisse](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-eventing/overview) abonnieren, wodurch Geschäftslogik in Adobe App Builder oder einer anderen Infrastruktur Trigger werden kann.

Dieses Dokument dient als Übersicht, eine ausführlichere Dokumentation ist jedoch auf den folgenden Seiten verfügbar:

* Die Links aus dem Abschnitt zur OpenAPI-basierten API in [Referenzdokumentation](https://developer.adobe.com/experience-cloud/experience-manager-apis/). Die Referenzdokumentation jeder API enthält auch einen API-Playground, mit dem Sie einen Endpunkt einfach mithilfe eines mit der Adobe Developer Console generierten Bearer-Tokens ausprobieren können.

* Informative [Handbücher](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/) einschließlich [API-Konzepte und -Syntax](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/how-to/).

* Ein Tutorial auf oberster Ebene, in dem [Authentifizierungsansätze](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/overview#authentication-support) und andere Konzepte beschrieben werden.

* Ein Tutorial mit Video, das sich auf [ Konfiguration der OpenAPI-basierten APIs ](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup).

* [Ein Tutorial mit allen Schritten](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/invoke-api-using-oauth-s2s) zum Konfigurieren und Aufrufen von OpenAPIs mit der Server-zu-Server-Authentifizierungsstrategie. Ähnliche Tutorials finden Sie auch für Authentifizierungsansätze für Web-Anwendungen und Einzelseiten-Apps.

## API-Zugriff konfigurieren {#configuring-api-access}

Einige OpenAPI-basierte AEM-APIs müssen authentifiziert werden. Dazu müssen Anmeldeinformationen mithilfe von [Adobe Developer Console generiert ](https://developer.adobe.com/developer-console/). Die Konfiguration umfasst die folgenden Schritte:

1. Modernisierung der AEM as a Cloud Service-Umgebung. Weitere Informationen finden Sie unter [Modernisierung der AEM as a Cloud Service-Umgebung](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup?#modernization-of-aem-as-a-cloud-service-environment) Tutorial-Schritt.
1. Aktivieren des Zugriffs auf die AEM-APIs mithilfe von Produktprofilen. Produktprofile sind mit den Services verknüpft, die AEM-Benutzergruppen mit vordefinierten Zugriffssteuerungslisten (ACLs) darstellen. Während einige Services standardmäßig bestimmten Produktprofilen zugeordnet sind, müssen andere explizit zugeordnet werden. Beispielsweise ist der AEM Assets-API-Benutzerdienst mit keinem [Produktprofil](/help/onboarding/aem-cs-team-product-profiles.md#aem-product-profiles) verknüpft. Daher müssen Sie ihn für die Verwendung der AEM Assets-API aktivieren. Weitere Informationen finden Sie im Tutorial[Schritt „Zugriff auf AEM](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup#enable-aem-apis-access)APIs aktivieren“.
1. Um die Server-zu-Server-Authentifizierung hinzuzufügen, muss die Benutzereinstellungsintegration der Systemadministrator des Unternehmens in der Adobe Admin Console sein oder dem Produktprofil, mit dem der Service verknüpft ist, als Entwickler hinzugefügt werden. Weitere Informationen finden Sie im Tutorial[Schritt „Zugriff auf AEM](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup#enable-aem-apis-access)APIs aktivieren“.
1. Erstellen Sie ein Adobe Developer Console-Projekt (ADC).
1. Konfigurieren Sie das ADC-Projekt. Dadurch werden Anmeldeinformationen generiert, die beim Aufrufen der API später zum Austausch gegen ein Bearer-Token verwendet werden.
1. Konfigurieren Sie die AEM-Instanz, um die ADC-Projektkommunikation zu aktivieren. Dazu müssen Sie die Client-ID bei der Umgebung registrieren, indem Sie eine YAML-Datei konfigurieren und bereitstellen, wie im Abschnitt [Registrieren einer Client-ID](#registering-a-client-id) unten beschrieben.

Detaillierte schrittweise Anweisungen finden Sie im Tutorial [Einrichten von OpenAPI-basierten APIs](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup).

### Registrieren einer Client-ID {#registering-a-client-id}

Mit Client-IDs werden die APIs in einem Adobe Developer Console-Projekt auf bestimmte AEM-Umgebungen beschränkt. Dies wird wie folgt erreicht:

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
