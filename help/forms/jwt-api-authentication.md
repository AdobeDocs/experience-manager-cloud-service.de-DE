---
title: Wie wird die JWT-Authentifizierung (JSON Web Token) eingerichtet?
description: Erfahren Sie, wie Sie die JWT-Authentifizierung (JSON Web Token) für Adobe Experience Manager Forms as a Cloud Service konfigurieren
role: Admin, Developer, User
feature: Adaptive Forms, APIs & Integrations
source-git-commit: 43b648eb3984867fda35ee04de10b78dd836b481
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 11%

---


# JWT-Server-zu-Server-Authentifizierung (JSON Web Token)

Die JWT-Server-zu-Server-Authentifizierung in AEM Forms, insbesondere für Server-seitige Integrationen mit AEM as a Cloud Service, umfasst einen bestimmten Prozess für die sichere Interaktion mit AEM-Services. Die JWT-Server-zu-Server-Authentifizierung wird von AEM Developer Console unterstützt.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

* Stellen Sie sicher, dass Sie Zugriff auf die für [ verwendete Umgebung spezifische ](https://experience.adobe.com/#/@formsinternal01/cloud-manager/landing.html)Adobe Cloud Manager haben.
* Weisen Sie die Rolle [Systemadministrator oder Entwickler“ zu, um auf Adobe Cloud Manager zuzugreifen](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/requirements/access-rights).

## Wie wird ein Zugriffs-Token mit JWT-Anmeldeinformationen generiert?

Führen Sie die folgenden Schritte aus, um zu zeigen, wie Sie ein Zugriffs-Token aus den JWT-Anmeldeinformationen generieren.

1. **Adobe Cloud Manager**

   1. Melden Sie sich bei Ihrem [Cloud Manager-Konto an](https://experience.adobe.com/#/@formsinternal01/cloud-manager/landing.html).
   2. Klicken Sie im ausgewählten Programm auf **[!UICONTROL Programmübersicht]**.

      ![Cloud Manager-Konto](/help/forms/assets/jwt-cloud-manager-landing.png)

   3. Klicken Sie in Ihrem Programm auf das Dreipunkt-Menü und wählen Sie **[!UICONTROL Developer Console]**.

      ![Entwicklerkonsole](/help/forms/assets/jwt-developer-console.png)

2. **AEM Developer Console**
   1. Anmelden bei AEM Developer Console
   2. Klicken Sie **[!UICONTROL der oberen Menüleiste auf]** Integrationen“.

      ![Integrationen](/help/forms/assets/jwt-integrations.png)

   3. Klicken Sie auf die Option **[!UICONTROL Neues technisches Konto erstellen]**.

      ![Neues technisches Konto erstellen](/help/forms/assets/jwt-creae-new-tech-account.png)

   Wenn Sie auf Neues technisches Konto erstellen klicken, werden die erforderlichen Informationen zum Generieren des Zugriffs-Tokens wie Client-ID und Client-Geheimnis zusammen mit anderen technischen Kontoinformationen wie privatem Schlüssel, öffentlichem Schlüssel und Ablaufdatum generiert.

   ![JWT-Anmeldeinformationen](/help/forms/assets/jwt-credentials.png)


3. **Berechtigungen generieren und speichern**

   1. API-Anmeldeinformationen für Einträge

      ```text
      API Credentials:
      ================
      Client ID: <your_client_id>
      Client Secret: <your_client_secret>
      Technical Account ID: <tech_account_id>
      Organization ID: <org_id>
      Scopes: AdobeID,openid,read_organizations
      ```

4. **Generieren von Zugriffstoken**

   Programmgesteuerte Generierung von Token mithilfe des cURL-Befehls:

   **Erforderliche Anmeldedaten:**

   * Client-ID
   * Client-Geheimnis
   * Bereiche (typischerweise: `openid, AdobeID, read_organizations, additional_info.projectedProductContext, read_pc.dma_aem_cloud, aem.document`)

   **Token-Endpunkt:**

   ```
   https://ims-na1.adobelogin.com/ims/token/v3
   ```

   **Beispielanfrage (cURL):**

   ```bash
   curl -X POST 'https://ims-na1.adobelogin.com/ims/token/v3' \
   -H 'Content-Type: application/x-www-form-urlencoded' \
   -d 'grant_type=client_credentials' \
   -d 'client_id=<YOUR_CLIENT_ID>' \
   -d 'client_secret=<YOUR_CLIENT_SECRET>' \
   -d 'scope=AdobeID,openid,read_organizations'
   ```

   **Antwort:**

   ```json
   {
   "access_token": "eyJhbGciOiJSUz...",
   "token_type": "bearer",
   "expires_in": 86399
   }
   ```


>[!NOTE]
>
> Weitere Informationen zu Service-Anmeldeinformationen und zum Generieren eines Zugriffstokens mithilfe der Adobe IMS-API finden Sie [hier](https://experienceleague.adobe.com/de/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials).

Sie können jetzt das generierte Zugriffstoken verwenden, um API-Aufrufe für Entwicklungs-, Staging- oder Produktionsumgebungen durchzuführen.

## Verwandte Artikel

Erfahren Sie, wie Sie eine Umgebung für synchrone (On-Demand) und asynchrone (Batch) Forms Communications-APIs einrichten:

<!-- START CARDS HTML - DO NOT MODIFY BY HAND -->
<div class="columns">
    <!-- Synchronous APIs Card -->
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="AEM Forms Communications APIs - Synchronous">
        <div class="card" style="height: 100%; display: flex; flex-direction: column;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md" title="Synchrone APIs" target="_self" rel="referrer">
                        <img class="is-bordered-r-small" src="/help/forms/assets/sync-api.png" alt="Synchrone APIs"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md" target="_self" rel="referrer" title="AEM Forms Communications APIs - Synchron">AEM Forms-Kommunikations-APIs - synchron</a>
                    </p>
                    <p class="is-size-6">Erfahren Sie, wie Sie eine Umgebung für synchrone (On-Demand) Forms Communications-APIs einrichten, die Dokumente sofort generieren oder verarbeiten. </p>
                </div>
                <a href="/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md" target="_self" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">Weitere Informationen</span>
                </a>
            </div>
        </div>
    </div>
    <!-- Asynchronous APIs Card -->
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="AEM Forms Communications APIs - Asynchronous">
        <div class="card" style="height: 100%; display: flex; flex-direction: column;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="/help/forms/aem-forms-cloud-service-communications-batch-processing.md" title="AEM Forms Communications APIs - Asynchron" target="_self" rel="referrer">
                        <img class="is-bordered-r-small" src="/help/forms/assets/async-api.png" alt="Asynchrone APIs"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="/help/forms/aem-forms-cloud-service-communications-batch-processing.md" target="_self" rel="referrer" title="Asynchrone APIs">AEM Forms Communications APIs - asynchron (Batch)</a>
                    </p>
                    <p class="is-size-6">Erfahren Sie, wie Sie eine Umgebung für asynchrone (Batch-)Forms Communications-APIs einrichten, die mehrere Dokumente nach einem Zeitplan generieren oder verarbeiten.</p>
                </div>
                <a href="/help/forms/aem-forms-cloud-service-communications-batch-processing.md" target="_self" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold">Weitere Informationen</span>
                </a>
            </div>
        </div>
    </div>
</div>
<!-- END CARDS HTML - DO NOT MODIFY BY HAND -->


>[!MORELIKETHIS]
>
>* [Einführung in die Kommunikationsfunktion von AEM Forms as a Cloud Service](/help/forms/aem-forms-cloud-service-communications-introduction.md)
>* [AEM Forms as a Cloud Service-Architektur für adaptive Formulare und Kommunikations-APIs](/help/forms/aem-forms-cloud-service-architecture.md)
>* [Kommunikationsverarbeitung – synchrone APIs](/help/forms/aem-forms-cloud-service-communications.md)
>* [Kommunikationsverarbeitung – Batch-APIs](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)
>* [Forms-Kommunikations-API - Tutorial](/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md)