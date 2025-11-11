---
title: Wie richte ich die OAuth Server-zu-Server-Authentifizierung ein?
description: Erfahren Sie, wie Sie die OAuth-Server-zu-Server-Authentifizierung für Adobe Experience Manager Forms as a Cloud Service konfigurieren
role: Admin, Developer, User
feature: Adaptive Forms, APIs & Integrations
hide: true
hidefromtoc: true
index: false
source-git-commit: fcc25eb44b485db69ec1c267f4cf8774c4279b24
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 3%

---


# OAuth Server-zu-Server-Authentifizierung - Empfohlen

Die OAuth Server-zu-Server-Authentifizierung ermöglicht den sicheren, Token-basierten Zugriff auf AEM Forms Communications-APIs, ohne dass eine Benutzerinteraktion erforderlich ist. Diese Methode eignet sich ideal für automatisierte Systeme, Backend-Services und Integrationen, die sich programmgesteuert authentifizieren müssen.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

* Stellen Sie sicher, dass Sie Zugriff auf die für [&#x200B; verwendete Umgebung spezifische &#x200B;](https://developer.adobe.com/console)Adobe Developer Console haben.
* Weisen Sie in der Adobe Admin Console die Rolle Systemadministrator oder Entwickler zu, um den Zugriff auf die Adobe Developer Console zu ermöglichen.

## Wie wird ein Zugriffs-Token mithilfe der OAuth-Server-zu-Server-Authentifizierung generiert?

Führen Sie die folgenden Schritte aus, um zu zeigen, wie Sie ein Zugriffstoken von der Adobe Developer-Konsole aus generieren und Ihren ersten API-Aufruf über OAuth-Server-zu-Server-Authentifizierung durchführen.


1. Navigieren Sie zu [Adobe Developer Console](https://developer.adobe.com/console)
2. Mit Adobe ID anmelden

3. Neues Projekt erstellen oder zu Ihrem vorhandenen Projekt navigieren

   **So erstellen Sie ein neues Projekt:**

   1. Klicken Sie **Abschnitt „Schnellstart** auf **Neues Projekt erstellen**
   2. Ein neues Projekt wird mit einem Standardnamen erstellt

      ![ADC-Projekt erstellen](/help/forms/assets/adc-home.png)

   3. Klicken **oben** auf „Projekt bearbeiten“

      ![Projekt bearbeiten](/help/forms/assets/adc-edit-project.png)

   4. Geben Sie einen aussagekräftigen Namen an (z. B. „FormsProject„)
   5. Klicken Sie auf **Speichern**.

      ![Projektname bearbeiten](/help/forms/assets/adc-edit-projectname.png)


   **So navigieren Sie zu Ihrem vorhandenen Projekt:**

   1. Klicken Sie **Adobe Developer Console auf** Alle Projekte“

      ![Projekte suchen](/help/forms/assets/search-adc-project.png)

   2. Suchen Sie Ihr Projekt und klicken Sie darauf, um es zu öffnen.

      ![Projekte suchen](/help/forms/assets/locate-adc-project.png)


      >[!NOTE]
      >
      > Sie können die API und die Authentifizierungsmethode zu Ihrem vorhandenen Projekt hinzufügen, indem Sie auf **Zum Projekt hinzufügen** > **API**\
      > ![API zu vorhandenem Projekt hinzufügen](/help/forms/assets/add-api-existing-project.png)
      > Um die API und die Authentifizierungsmethode hinzuzufügen, führen Sie dieselben Schritte wie unten für Ihr vorhandenes Projekt beschrieben aus.

4. Fügen Sie je nach Ihren Anforderungen verschiedene AEM Forms Communications-APIs hinzu.

   **a. Für Document Services-APIs**

   1. Klicken Sie auf **API hinzufügen**

      ![API hinzufügen](/help/forms/assets/adc-add-api.png)

   2. **Forms-Kommunikations-APIs**
      1. Filtern _im Dialogfeld „API_&quot; nach **Experience Cloud**
      2. Wählen Sie **Forms-Kommunikations-APIs“**

         ![Forms-Kommunikations-API hinzufügen](/help/forms/assets/adc-add-forms-api.png)


   3. Wählen Sie **OAuth Server-zu-Server** Authentifizierungsmethode aus

      ![Authentifizierungsmethode auswählen](/help/forms/assets/adc-add-authentication-method.png)


   **b. Für adaptive Forms Runtime-APIs**

   1. **Klicken Sie auf API hinzufügen**
Klicken Sie in Ihrem Projekt auf die Schaltfläche **API hinzufügen**

      ![API hinzufügen](/help/forms/assets/adc-add-api.png)

   2. **AEM Forms-Bereitstellungs- und Laufzeit-API auswählen**
      1. Filtern _im Dialogfeld „API_&quot; nach **Experience Cloud**
      2. Wählen Sie **AEM Forms-Bereitstellungs- und Laufzeit-API“**
      3. Klicken Sie auf **Weiter**.

   3. **Authentifizierungsmethode**
Wählen **Authentifizierungsmethode OAuth Server-zu-Server** aus.


      ![Authentifizierungsmethode auswählen](/help/forms/assets/adc-add-authentication-method.png)

5. **Produktprofil**:

   1. Wählen Sie das entsprechende **Produktprofil** basierend auf der erforderlichen Zugriffsebene aus:

      | Zugriffstyp | Produktprofil |
      |------------------|----------------------|
      | Nur-Lese-Zugriff | `AEM Users - author - Program XXX - Environment XXX` |
      | Lese-/Schreibzugriff | `AEM Assets Collaborator Users - author - Program XXX - Environment XXX` |
      | Vollständiger administrativer Zugriff | `AEM Administrators - author - Program XXX - Environment XXX` |

   2. Wählen Sie das **Produktprofil** aus, das Ihrer Autoren-Service-URL (`https://author-pXXXXX-eYYYYY.adobeaemcloud.com`) entspricht. Beispiel: `https://author-pXXXXX-eYYYYY.adobeaemcloud.com` auswählen.

   3. Klicken Sie auf **Konfigurierte API speichern**. Die API und das Produktprofil werden zu Ihrem Projekt hinzugefügt

      ![Projektkonfiguration auswählen](/help/forms/assets/adc-add-product-profile.png)

6. Erstellen und Speichern von Anmeldeinformationen

   1. Navigieren Sie zu Ihrem Projekt in Adobe Developer Console
   2. Klicken Sie auf **OAuth Server-zu-Server** Anmeldedaten
   3. Sehen Sie sich den Abschnitt **Anmeldedaten** an

      ![Anzeigen der Anmeldeinformationen](/help/forms/assets/adc-view-credential.png)

   4. API-Anmeldeinformationen für Einträge

      ```text
      API Credentials:
      ================
      Client ID: <your_client_id>
      Client Secret: <your_client_secret>
      Technical Account ID: <tech_account_id>
      Organization ID: <org_id>
      Scopes: AdobeID,openid,read_organizations
      ```

7. Erzeugung von Zugriffstoken

   **a. Zum Testen**

   Manuelles Generieren von Zugriffs-Token in Adobe Developer Console:

   1. **Navigieren Sie zu Ihrem Projekt**
      1. Öffnen Sie in Adobe Developer Console Ihr Projekt
      2. Klicken Sie auf **OAuth Server-zu-Server**

   2. **Zugriffs-Token generieren**
      1. Klicken Sie im API-Abschnitt Ihres Projekts auf **Schaltfläche** Zugriffs-Token generieren“.
      2. Kopieren des generierten Zugriffstokens

      ![Zugriffs-Token generieren](/help/forms/assets/adc-access-token.png)

      >[!NOTE]
      >
      > Das Zugriffs-Token ist nur für **24 Stunden gültig**

   **b. Für die Produktion**

   Programmgesteuerte Generierung von Token mithilfe der Adobe IMS-API:

   **Erforderliche Anmeldedaten:**

   * Client-ID
   * Client-Geheimnis
   * Bereiche (typischerweise: `openid, AdobeID, read_organizations, additional_info.projectedProductContext, read_pc.dma_aem_cloud, aem.document`)

   **Token-Endpunkt:**

   ```
   https://ims-na1.adobelogin.com/ims/token/v3
   ```

   **Beispielanfrage (curl):**

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

Sie können jetzt das generierte Zugriffstoken verwenden, um API-Aufrufe für Entwicklungs-, Staging- oder Produktionsumgebungen durchzuführen.

>[!NOTE]
>
> Weitere Informationen zur OAuth-Server-zu-Server-Implementierung zum Generieren des Zugriffstokens und zum Ausführen von API-Aufrufen [&#x200B; Sie hier](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation).

## Nächste Schritte

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


