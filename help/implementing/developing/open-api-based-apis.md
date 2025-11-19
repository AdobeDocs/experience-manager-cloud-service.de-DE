---
title: Auf OpenAPI basierende APIs
description: Erfahren Sie mehr über die AEM as a Cloud Service-Unterstützung für auf OpenAPI basierende APIs
feature: Developing
role: Admin, Developer
exl-id: 4aeafba9-8f9e-4ecb-9e37-8d048b0474cc
source-git-commit: 3a46db9c98fe634bf2d4cffd74b54771de748515
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 100%

---

# Auf OpenAPI basierende APIs {#openapi-based-apis}

Neuere AEM as a Cloud Service-APIs basieren auf der OpenAPI-Spezifikation und bieten daher einen konsistenten und gut dokumentierten Satz von APIs.

>[!NOTE]
>
> Ein [End-to-End-Tutorial](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/invoke-api-using-oauth-s2s) ist eine empfohlene Ressource, in der Sie erfahren, wie Sie die auf OpenAPI basierenden AEM-APIs konfigurieren und aufrufen können.

Bei Endpunkten, für die eine Authentifizierung erforderlich ist, unterscheidet sich der Authentifizierungsansatz je nach Endpunkt, verwendet jedoch möglicherweise OAuth-Server-zu-Server, OAuth-Web-Anwendung oder OAuth-Single-Page-Application (SPA). Anmeldedaten werden über Projekte in der [Adobe Developer Console](https://developer.adobe.com/developer-console/) konfiguriert.

Häufige API-Anwendungsfälle umfassen Integrationen mit Systemen wie CRM oder PIM, bei denen AEM-APIs aufgerufen werden, um Daten abzurufen oder beizubehalten. Im Rahmen der Integrationsimplementierung können Anwendungen [von AEM ausgegebene Ereignisse](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-eventing/overview) abonnieren, wodurch Geschäftslogik in Adobe App Builder oder einer anderen Infrastruktur ausgelöst werden kann.

Dieses Dokument dient als Überblick, eine ausführlichere Dokumentation ist jedoch auf den folgenden Seiten verfügbar:

* Die Links aus dem Abschnitt zur auf OpenAPI basierenden API in der [Referenzdokumentation](https://developer.adobe.com/experience-cloud/experience-manager-apis/). Die Referenzdokumentation jeder API enthält auch einen API-Playground, mit dem Sie einen Endpunkt einfach mithilfe eines mit der Adobe Developer Console generierten Bearer-Tokens ausprobieren können.

* Informative [Handbücher](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/) einschließlich [API-Konzepte und -Syntax](https://developer.adobe.com/experience-cloud/experience-manager-apis/guides/how-to/).

* Ein allgemeines Tutorial, in dem [Authentifizierungsansätze](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/overview#authentication-support) und andere Konzepte beschrieben werden.

* Ein Tutorial mit Video, das [die Konfiguration der auf OpenAPI basierenden APIs](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup) behandelt.

* [Ein End-to-End-Tutorial](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/invoke-api-using-oauth-s2s) zum Konfigurieren und Aufrufen von OpenAPIs mit der Server-zu-Server-Authentifizierungsstrategie. Ähnliche Tutorials finden Sie auch für Web-Anwendungs- und Single-Page-Application-Authentifizierungsansätze.

## Konfigurieren von API-Zugriff {#configuring-api-access}

Einige auf OpenAPI basierende AEM-APIs erfordern eine Authentifizierung. Dazu müssen Anmeldedaten mithilfe der [Adobe Developer Console](https://developer.adobe.com/developer-console/) generiert werden. Die Konfiguration umfasst die folgenden Schritte:

1. Modernisieren Sie die AEM as a Cloud Service-Umgebung. Weitere Informationen finden Sie im Tutorial-Schritt [Modernisieren der AEM as a Cloud Service-Umgebung](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup?#modernization-of-aem-as-a-cloud-service-environment).
1. Aktivieren Sie den Zugriffs auf die AEM-APIs mithilfe von Produktprofilen. Die neu hinzugefügten Produktprofile sind mit den Services verknüpft, die AEM-Benutzergruppen mit vordefinierten Zugriffssteuerungslisten (Access Control Lists, ACLs) darstellen. Während einige Services standardmäßig mit bestimmten Produktprofilen verknüpft sind, müssen andere explizit verknüpft werden. Beispielsweise ist der AEM Assets-API-Benutzerdienst mit keinem [Produktprofil](/help/onboarding/aem-cs-team-product-profiles.md#aem-product-profiles) verknüpft. Daher müssen Sie die Verwendung der AEM Assets-API für ihn aktivieren. Weitere Informationen finden Sie im Tutorial-Schritt [Aktivieren des AEM-API-Zugriffs](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup#enable-aem-apis-access).
1. Um die Server-zu-Server-Authentifizierung hinzuzufügen, muss die Person, die die Integration einrichtet, die bzw. der Systemadmin des Unternehmens in der Adobe Admin Console sein oder dem mit dem Service verknüpften Produktprofil als Entwicklerin bzw. Entwickler hinzugefügt sein. Weitere Informationen finden Sie im Tutorial-Schritt [Aktivieren des AEM-API-Zugriffs](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup#enable-aem-apis-access).
1. Erstellen Sie ein Projekt in der Adobe Developer Console (ADC)
1. Konfigurieren Sie das ADC-Projekt. Dadurch werden Anmeldedaten generiert, die beim Aufrufen der API später gegen ein Bearer-Token ausgetauscht werden werden.
1. Konfigurieren Sie die AEM-Instanz zur Aktivierung der ADC-Projektkommunikation. Dazu müssen Sie die Client-ID bei der Umgebung registrieren, indem Sie eine YAML-Datei konfigurieren und bereitstellen, wie im Abschnitt [Registrieren einer Client-ID](#registering-a-client-id) unten beschrieben.

Detaillierte Schritt-für-Schritt-Anweisungen finden Sie im Tutorial [Einrichten von OpenAPI-basierten AEM-APIs](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup).

### Registrieren einer Client-ID {#registering-a-client-id}

Mit Client-IDs werden die APIs in einem Projekt in der Adobe Developer Console auf bestimmte AEM-Umgebungen beschränkt. Dies geschieht wie folgt:

1. Erstellen Sie eine Datei mit dem Namen `api.yaml` oder ähnlich mit einer Konfiguration wie dem folgenden Ausschnitt, einschließlich der gewünschten Ebenen (Autoren-, Veröffentlichungs-, Vorschauebene). `Client_id`-Werte sollten aus Ihren Adobe Developer Console-API-Projekten stammen.

   Die Eigenschaften `kind`, `version` und `metadata` werden im Artikel zu [Konfigurations-Pipelines](/help/operations/config-pipeline.md#common-syntax) beschrieben. Der Eigenschaftswert `kind` sollte *API* sein, und die Eigenschaft `version` sollte auf *1* festgelegt werden.

   ```
   kind: "API"
   version: "1"
   data:
     allowedClientIDs:
       author:
         - "<client_id>"
       publish:
         - "<client_id>"
       preview:
         - "<client_id>"
   ```

1. Platzieren Sie die Datei mit dem Namen `config` oder ähnlich unter einem Ordner der obersten Ebene, wie unter [Konfigurations-Pipelines](/help/operations/config-pipeline.md#folder-structure) beschrieben.
1. Erstellen Sie für andere Umgebungstypen als RDE (die Befehlszeilen-Tools verwendet) eine zielgerichtete Bereitstellungskonfigurations-Pipeline in Cloud Manager, wie in [diesem Abschnitt](/help/operations/config-pipeline.md#creating-and-managing) im Artikel zu Konfigurations-Pipelines beschrieben. Beachten Sie, dass Full-Stack-Pipelines und Web-Stufen-Pipelines die Konfigurationsdatei nicht bereitstellen.
1. Implementieren Sie die Konfiguration.
