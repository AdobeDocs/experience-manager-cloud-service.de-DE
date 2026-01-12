---
title: Wie richte ich die OAuth Server-zu-Server-Authentifizierung ein?
description: Erfahren Sie, wie Sie die OAuth-Server-zu-Server-Authentifizierung für Adobe Experience Manager Forms as a Cloud Service konfigurieren
role: Admin, Developer, User
feature: Adaptive Forms, APIs & Integrations
source-git-commit: d9eb9a93aba71a5ef5940c9d1d75cfd4e738c26b
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 4%

---


# OAuth Server-zu-Server-Authentifizierung

Die OAuth Server-zu-Server-Authentifizierung ermöglicht den sicheren, Token-basierten Zugriff auf AEM Forms Communications-APIs, ohne dass eine Benutzerinteraktion erforderlich ist. Die OAuth-Server-zu-Server-Authentifizierung wird von Adobe Developer Console unterstützt.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

* Stellen Sie sicher, dass Sie [Zugriff auf die Adobe Developer Console](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/requirements/access-rights) speziell für die von Ihnen verwendete Umgebung haben.
* [Weisen Sie in der Adobe Admin Console die Rolle „Systemadministrator“ oder „Entwickler“ zu](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-manager/content/requirements/role-based-permissions) um den Zugriff auf die Adobe Developer Console zu ermöglichen.

## Wie wird ein Zugriffs-Token mithilfe der OAuth-Server-zu-Server-Authentifizierung generiert?

Gehen Sie wie folgt vor, um ein Zugriffstoken von der Adobe Developer-Konsole aus zu generieren und Ihren ersten API-Aufruf über OAuth-Server-zu-Server-Authentifizierung durchzuführen.

### &#x200B;1. Adobe Developer Console-Projekteinrichtung

1. Navigieren Sie zu [Adobe Developer Console](https://developer.adobe.com/console)
2. Mit Adobe ID anmelden

3. Neues Projekt erstellen oder zu Ihrem vorhandenen Projekt navigieren

>[!BEGINTABS]

>[!TAB So erstellen Sie ein neues Projekt]

1. Klicken Sie **Abschnitt „Schnellstart** auf **Neues Projekt erstellen**
2. Ein neues Projekt wird mit einem Standardnamen erstellt

   ![ADC-Projekt erstellen](/help/forms/assets/adc-home.png)

3. Klicken **oben** auf „Projekt bearbeiten“

   ![Projekt bearbeiten](/help/forms/assets/adc-edit-project.png)

4. Geben Sie einen aussagekräftigen Namen an (z. B. „FormsProject„)
5. Klicken Sie auf **Speichern**.

   ![Projektname bearbeiten](/help/forms/assets/adc-edit-projectname.png)

>[!TAB So navigieren Sie zu Ihrem vorhandenen Projekt]

1. Klicken Sie **Adobe Developer Console auf** Alle Projekte“

   ![Projekte suchen](/help/forms/assets/search-adc-project.png)

2. Suchen Sie Ihr Projekt und klicken Sie darauf, um es zu öffnen.

   ![Projekte suchen](/help/forms/assets/locate-adc-project.png)

>[!ENDTABS]

### &#x200B;2. Hinzufügen von Forms-APIs

Fügen Sie Forms-APIs hinzu, je nachdem, was Sie tun möchten:

* **AEM Forms Communications APIs**: Wird verwendet, wenn Sie Dokumente (PDF und zugehörige Formate) generieren, konvertieren, zusammenstellen oder sichern müssen.
* **Adaptive Forms Runtime-APIs** - Wird verwendet, wenn Sie adaptive Forms zur Laufzeit rendern, übermitteln oder verarbeiten müssen.

>[!BEGINTABS]

>[!TAB Für AEM Forms Communications-APIs]

1. Klicken Sie auf **API hinzufügen**

   ![API hinzufügen](/help/forms/assets/adc-add-api.png)

2. **Forms-Kommunikations-APIs**
   1. Filtern _im Dialogfeld „API_&quot; nach **Experience Cloud**
   2. Wählen Sie **Forms-Kommunikations-APIs“**

      ![Forms-Kommunikations-API hinzufügen](/help/forms/assets/adc-add-forms-api.png)

   3. Klicken Sie auf **Weiter**.
   4. Wählen Sie **OAuth Server-zu-Server** Authentifizierungsmethode aus

      ![Authentifizierungsmethode auswählen](/help/forms/assets/adc-add-authentication-method.png)

>[!TAB Für adaptive Forms Runtime-APIs]

1. **Klicken Sie auf API hinzufügen**

   ![API hinzufügen](/help/forms/assets/adc-add-api.png)

2. **AEM Forms-Bereitstellungs- und Laufzeit-API auswählen**
   1. Filtern _im Dialogfeld „API_&quot; nach **Experience Cloud**
   2. Wählen Sie **AEM Forms-Bereitstellungs- und Laufzeit-API“**
      ![Forms-Kommunikations-API hinzufügen](/help/forms/assets/adc-add-runtime-api.png)

   3. Klicken Sie auf **Weiter**.
   4. Wählen Sie die Authentifizierungsmethode **OAuth-Server-zu-Server** aus.
      ![Authentifizierungsmethode auswählen](/help/forms/assets/adc-add-authentication-method.png)

>[!ENDTABS]

Sie können die API und die Authentifizierungsmethode auch zu Ihrem vorhandenen Projekt hinzufügen, indem Sie auf **Zum Projekt hinzufügen** > **API**\
![API zu vorhandenem Projekt hinzufügen](/help/forms/assets/add-api-existing-project.png)

### &#x200B;3. Produktprofil hinzufügen

Das Produktprofil stellt Berechtigungen (oder Autorisierung) für Anmeldeinformationen für den Zugriff auf die AEM-Ressourcen bereit.

1. Wählen Sie das **Produktprofil** aus, das Ihrer AEM-Instanz-URL (`https://Service Type -Environment Type-Program XXX-Environment XXX.adobeaemcloud.com`) entspricht.

   * **Service-Typ** - gibt die Services oder Berechtigungen an, die mit der AEM-Instanz verknüpft sind

   * **Umgebungstyp** - gibt an, ob die Umgebung für den Autoren- oder Veröffentlichungs-Service ist

   * **Programm XXX** - identifiziert die Cloud Manager-Programm-ID.

   * **Umgebung XXX** - identifiziert die spezifische Umgebungs-ID innerhalb dieses Programms

   >[!NOTE]
   >
   > Produktprofile sind an eine bestimmte AEM-Instanz (Programm + Umgebung) gebunden. Wählen Sie immer das Profil aus, das Ihrer Instanz-URL entspricht.

2. Klicken Sie auf **Konfigurierte API speichern**. Die API und das Produktprofil werden zu Ihrem Projekt hinzugefügt

   ![Projektkonfiguration auswählen](/help/forms/assets/adc-add-product-profile.png)

### &#x200B;4. Erstellen und Speichern von Anmeldeinformationen

1. Navigieren Sie zu Ihrem Projekt in Adobe Developer Console
2. Klicken Sie auf **OAuth Server-zu-Server** Anmeldedaten
3. Sehen Sie sich den Abschnitt **Anmeldedaten** an

   ![Anzeigen der Anmeldeinformationen](/help/forms/assets/adc-view-credential.png)

**API-Anmeldeinformationen aufzeichnen**

```text
    API Credentials:
    ================
    Client ID: <your_client_id>
    Client Secret: <your_client_secret>
    Technical Account ID: <tech_account_id>
    Organization ID: <org_id>
    Scopes: AdobeID,openid,read_organizations
```

### &#x200B;5. Erzeugung von Zugriffstoken

Erstellen Sie das Zugriffstoken entweder manuell oder programmgesteuert:

>[!BEGINTABS]

>[!TAB Zum Testen]

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

>[!TAB Für die Produktion]

Programmgesteuerte Generierung von Token mithilfe [Adobe IMS](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/security/setting-up-ims-integrations-for-aem-as-a-cloud-service)-API:

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

>[!ENDTABS]

Sie können jetzt das generierte Zugriffstoken verwenden, um API-Aufrufe für Entwicklungs-, Staging- oder Produktionsumgebungen durchzuführen.

## Best Practices: Verwalten von Anmeldeinformationen für Entwicklung, Staging und Produktion

* Verwenden Sie immer separate Anmeldeinformationen für Entwicklung, Staging und Produktion.

* Ordnen Sie jede Berechtigung der richtigen AEM-Umgebungs-URL zu.

* Geheime Daten sicher speichern und niemals in die Quell-Code-Verwaltung übertragen.

* Verfolgen Sie die Gültigkeit des Zugriffs-Tokens, da Token nur für 24 Stunden gültig sind.

## Nächste Schritte

Informationen zum Einrichten einer Umgebung für synchrone Forms-Kommunikations-APIs finden Sie unter [Synchrone Verarbeitung von AEM Forms as a Cloud Service Communications](/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md).


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


