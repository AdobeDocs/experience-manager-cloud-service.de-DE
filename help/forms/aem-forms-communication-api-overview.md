---
title: AEM Forms Communications APIs - Übersicht
description: Übersicht über AEM Forms Communications-APIs einschließlich Authentifizierungsmethoden und vollständiger API-Referenz
role: Developer, User
feature: Adaptive Forms, APIs & Integrations
hide: true
hidefromtoc: true
index: false
source-git-commit: fcc25eb44b485db69ec1c267f4cf8774c4279b24
workflow-type: tm+mt
source-wordcount: '899'
ht-degree: 11%

---


# AEM Forms Communications APIs - Übersicht

AEM Forms Communications-APIs bieten eine umfassende Suite an Cloud-nativen APIs, die Unternehmen bei der Automatisierung von Dokumenten-Workflows unterstützen.

AEM Forms-APIs sind über zwei Hauptkonsolen strukturiert und zugänglich:

* [Adobe Developer Console (ADC)](https://developer.adobe.com/developer-console/) - Adobe Developer Console ist das Gateway zu Adobe-APIs, Ereignissen, Runtime und App Builder.

* [AEM Developer Console](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console) - AEM Developer Console bietet Tools zum Debuggen und Überprüfen von AEM as a Cloud Service-Umgebungen.

Jede Konsole bietet Zugriff auf verschiedene APIs und Dienste für die Dokumentverarbeitung, Generierung, Konvertierung, Verschlüsselung und Kommunikation. Die APIs unterstützen verschiedene [Authentifizierungsmethoden](#authentication-methods).

## Authentifizierungsmethoden

APIs unterstützen mehrere Authentifizierungsmethoden für eine sichere Integration zwischen Ihren Programmen und Adobe-Services:

| Aspekt | OAuth Server-zu-Server (empfohlen) | JWT (JSON Web Token) |
|-------------|------------------------------------------|---------------------------|
| Beschreibung | Moderne und sichere Methode für API-Zugriff ohne Benutzerinteraktion. | Ältere Methode mit signierten Token für den Zugriff. |
| Setup-Speicherort | Adobe Developer Console und AEM Developer Console | Nur AEM Developer Console |
| Sicherheit | Hoch - Verwendet Client-Anmeldeinformationen und -Bereiche | Mittelmäßig - hängt von der Schlüsselverwaltung ab |
| Skalierbarkeit | Hochgradig skalierbar für Backend-Integrationen | Eingeschränkt, geeignet für ältere Anwendungen |
| Token-Verwaltung | Automatische Generierung und Erneuerung | Manuelle Token-Signierung und -Rotation |
| Status | Empfohlen | Nicht weiter unterstützt |


>[!NOTE]
>
> Klicken Sie auf die unten stehenden Links, um mehr zu erfahren:-
> 
> * [OAuth Server-zu-Server (empfohlen)](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)
> * [JWT (JSON Web Token)](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/)

<!--### Execution Models

The following table highlights the key differences between Synchronous (On-Demand) and Asynchronous (Batch) execution models supported in AEM Forms Communications APIs:

| Feature | Synchronous (On-Demand) | Batch (Asynchronous) |
|---------|-------------------------|----------------------|
| **Execution Model** | Real-time, immediate | Queued, scheduled |
| **Response Time** | Seconds | Minutes to hours |
| **Volume** | Single or few documents | Hundreds to thousands |
| **Testing Environment** | Author & Publish | Author Only |
| **Use Case** | User-triggered actions | Scheduled bulk operations |
| **Console Access** | ADC & AEM Developer Console | AEM Developer Console Only |-->

## Übersicht über die API-Klassifizierung

Alle AEM Forms-APIs sind in zwei Hauptteile unterteilt:

* [APIs für Bereitstellung und Laufzeit adaptiver Formulare](https://developer-stage.adobe.com/experience-cloud/experience-manager-apis/api/stable/forms/)

* [AEM Forms-Kommunikations-APIs](#aem-forms-communications-apis)

| Details | APIs für Bereitstellung und Laufzeit adaptiver Formulare | Kommunikations-APIs |
|--------------|----------------------------|--------------------------|
| Zweck | Verarbeiten von Bereitstellungs- und Laufzeitvorgängen für adaptive Formulare | Dokumenterstellung und -bearbeitung |
| Anwendungsszenarien | - Formular-Rendering<br>- <br>- Formularübermittlungen<br>- Entwurfsverwaltung | - PDF-<br>: Zusammenführen von Dokumenten<br> Stapelverarbeitung<br> Druckvorgänge |
| Autorisierungsmethode | Unterstützt OAuth-Server-zu-Server-/Benutzer-Authentifizierungsmethoden. | Unterstützt nur OAuth Server-zu-Server-Authentifizierung. |

### AEM Forms Communications-APIs

Kommunikations-APIs sind der primäre Fokus für dokumentzentrierte Vorgänge.

In der folgenden Tabelle sind alle [AEM Forms Communications APIs ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/) ihre unterstützten Authentifizierungsmethoden und Ausführungsmodelle aufgeführt:

#### APIs zur Dokumenterstellung

| API-Endpunkt | Ausführungsmodell | Authentifizierungsmethode |
| ------------------ | ---------------- | --------------------------- |
| [/adobe/forms/batch/output/config](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Configuration/operation/CreateBatchConfig) | Asynchron/Batch | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[JWT](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [/adobe/forms/batch/output/config/{configName}](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Configuration/operation/GetBatchConfigbyName) | Asynchron/Batch | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[JWT](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [/adobe/forms/batch/output/config/configs](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Configuration/operation/GetAllBatchConfigs) | Asynchron/Batch | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[JWT](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [/adobe/forms/batch/output/config/{configName}/execution](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Execution/operation/StartBatchRun) | Asynchron/Batch | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[JWT](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [/adobe/forms/batch/output/config/{configName}/execution/{executionId}](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Execution/operation/GetBatchRunInstanceState) | Asynchron/Batch | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[JWT](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [/adobe/forms/batch/output/config/{configName}/execution](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Execution/operation/GetAllRunningInstancesForBatch) | Asynchron/Batch | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[JWT](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [/adobe/forms/doc/v1/generatePDFOutput](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/#tag/Communications-Services/paths/~1adobe~1forms~1doc~1v1~1generatePDFOutput/post) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[JWT](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [/adobe/forms/doc/v1/generatePrintedOutput](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/#tag/Batch-Execution/operation/GetAllRunningInstancesForBatch) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[JWT](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [/adobe/forms/doc/v1/generate/afp](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/#tag/Communications-Services/paths/~1adobe~1forms~1doc~1v1~1generate~1afp/post) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[JWT](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [/adobe/document/generate/pdfform](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFForm) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [/adobe/document/generate/pdfform/jobs/{id}/status](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFFormJobStatus) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [/adobe/document/generate/pdfform/jobs/{id}/result](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFFormJobResult) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |


#### APIs zur Dokumentbearbeitung

| API-Endpunkt | Ausführungsmodell | Authentifizierungsmethode |
| ------------------ | ---------------- | --------------------------- |
| [/adobe/forms/assembler/ddx/invoke](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/#tag/DDX-execution/operation/InvokeDDX) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[JWT](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [/adobe/forms/assembler/pdfa/convert](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/#tag/Document-conversion/operation/ConvertToPDFA) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[JWT](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |
| [/adobe/forms/assembler/pdfa/validate](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/#tag/Document-validation/operation/CheckIsPDFA) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)/[JWT](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) |

#### APIs zur Dokumentkonvertierung

| API-Endpunkt | Ausführungsmodell | Authentifizierungsmethode |
|----------------|---------|----------------------|
| [/adobe/document/convert/pdftoxdp](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Conversion/paths/~1convert~1pdftoxdp/post) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |

#### APIs zur Dokumentextraktion

| API-Endpunkt | Ausführungsmodell | Authentifizierungsmethode |
|----------------|---------|----------------------|
| [/adobe/forms/doc/v1/extract/pdfproperties](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Extraction/paths/~1extract~1pdfproperties/post) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [/adobe/forms/doc/v1/extract/usagerrights](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/extractUsageRights) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [/adobe/forms/doc/v1/extract/metadata](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Extraction/paths/~1extract~1metadata/post) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [/adobe/forms/doc/v1/extract/data](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/exportData) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [/adobe/document/extract/security](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Extraction/paths/~1extract~1security/post) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |

#### Document Transformation-APIs


| API-Endpunkt | Ausführungsmodell | Authentifizierungsmethode |
|----------------|---------|----------------------|
| [/adobe/document/transform/metadata](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1transform~1metadata/post) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [/adobe/document/field/signature/add](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1field~1signature~1add/post) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [/adobe/document/field/signature/clear](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1field~1signature~1clear/post) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [/adobe/document/field/signature/remove](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1field~1signature~1remove/post) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |

#### Document Assurance-APIs

| API-Endpunkt | Ausführungsmodell | Authentifizierungsmethode |
|----------------|---------|----------------------|
| [/adobe/document/assurance/usagerrights](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/applyUsageRights) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [/adobe/document/assurance/encrypt](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1encrypt/post) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [/adobe/document/assurance/decrypt](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1decrypt/post) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [/adobe/document/assurance/sign](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1sign/post) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |
| [/adobe/document/assurance/certificate](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1certify/post) | Synchron | [OAuth-Server zu Server](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation) |


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


>[!MORELIKETHIS]
>
>* [Einführung in die Kommunikationsfunktion von AEM Forms as a Cloud Service](/help/forms/aem-forms-cloud-service-communications-introduction.md)
>* [AEM Forms as a Cloud Service-Architektur für adaptive Formulare und Kommunikations-APIs](/help/forms/aem-forms-cloud-service-architecture.md)
>* [Kommunikationsverarbeitung – synchrone APIs](/help/forms/aem-forms-cloud-service-communications.md)
>* [Kommunikationsverarbeitung – Batch-APIs](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)
>* [Kommunikationsverarbeitung - On-Demand-APIs](/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md)