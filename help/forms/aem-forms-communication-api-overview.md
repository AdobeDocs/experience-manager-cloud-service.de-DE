---
title: AEM Forms Communications APIs - Übersicht
description: Übersicht über AEM Forms Communications-APIs einschließlich Authentifizierungsmethoden und vollständiger API-Referenz
role: Developer, User
feature: Adaptive Forms, APIs & Integrations
source-git-commit: d9eb9a93aba71a5ef5940c9d1d75cfd4e738c26b
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 9%

---


# AEM Forms Communications APIs - Übersicht

AEM Forms-APIs bieten eine umfassende Suite an Cloud-nativen APIs, die Unternehmen bei der Automatisierung von Dokumenten-Workflows unterstützen.

AEM Forms-APIs sind über zwei Hauptkonsolen strukturiert und zugänglich:

* [Adobe Developer Console (ADC)](https://developer.adobe.com/developer-console/) - Adobe Developer Console ist das Gateway zu Adobe-APIs, Ereignissen, Runtime und App Builder.

* [AEM Developer Console](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console) - AEM Developer Console bietet Zugriff auf Details auf Umgebungsebene, Konfigurationen, technische Konten und Service-Anmeldeinformationen, um Betriebs- und Integrationsaufgaben zu unterstützen.

Verschiedene APIs unterstützen verschiedene [Authentifizierungsmethoden](#authentication-methods).

## Authentifizierungsmethoden

Verschiedene Forms-APIs verwenden je nach Veröffentlichungszeitplan unterschiedliche Authentifizierungsmethoden:

* [OAuth-Server-zu-Server](/help/forms/oauth-api-authetication.md)
* [JWT (JSON Web Token) Server-zu-Server](/help/forms/jwt-api-authentication.md)

Frühere APIs unterstützen die JWT-basierte Server-zu-Server-Authentifizierung, die über die AEM Developer Console konfiguriert und verwaltet wird. Neuere APIs verwenden OAuth-Server-zu-Server-Authentifizierung und werden über die Adobe Developer Console konfiguriert.

<!--
>[!NOTE]
>
> Adobe is standardizing authentication method across all APIs and is gradually onboarding APIs to the Adobe Developer Console, which supports the OAuth Server-to-Server authentication method.-->

## Übersicht über die API-Klassifizierung

Alle AEM Forms-APIs sind in zwei Hauptteile unterteilt:

* [APIs für Bereitstellung und Laufzeit adaptiver Formulare](https://developer-stage.adobe.com/experience-cloud/experience-manager-apis/api/stable/forms/)

* [AEM Forms-Kommunikations-APIs](#aem-forms-communications-apis)

| Details | APIs für Bereitstellung und Laufzeit adaptiver Formulare | Kommunikations-APIs |
|--------------|----------------------------|--------------------------|
| Zweck | Verarbeiten von Bereitstellungs- und Laufzeitvorgängen für adaptive Formulare | Dokumenterstellung und -bearbeitung |
| Anwendungsszenarien | - Formular-Rendering<br>- <br>- Formularübermittlungen<br>- Entwurfsverwaltung | - PDF-<br>: Zusammenführen von Dokumenten<br> Stapelverarbeitung<br> Druckvorgänge |
| Autorisierungsmethode | Unterstützt OAuth-Server-zu-Server-/Benutzer-Authentifizierungsmethoden. | Unterstützt je nach API die Server-zu-Server-Authentifizierung, entweder JWT oder OAuth. Eine API kann nicht beide Authentifizierungsmethoden unterstützen. |

### AEM Forms Communications-APIs

Kommunikations-APIs sind der primäre Fokus für dokumentzentrierte Vorgänge.

In der folgenden Tabelle sind alle [AEM Forms Communications APIs ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/) ihre unterstützten Authentifizierungsmethoden und Ausführungsmodelle aufgeführt:

#### APIs zur Dokumenterstellung


| API-Endpunkt | Beschreibung | Ausführungsmodell | Authentifizierungsmethode |
| ----- | ------ |------- | ------ |
| [/adobe/forms/batch/output/config](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Configuration/operation/CreateBatchConfig) | Erstellt eine neue Batch-Konfiguration für Dokumenterstellungsaufträge. | Asynchron/Batch | [JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/batch/output/config/{configName}](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Configuration/operation/GetBatchConfigbyName) | Ruft Details zu einer bestimmten Batch-Konfiguration ab. | Asynchron/Batch | [JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/batch/output/config/configs](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Configuration/operation/GetAllBatchConfigs) | Gibt eine Liste aller verfügbaren Batch-Konfigurationen zurück. | Asynchron/Batch | [JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/batch/output/config/{configName}/execution](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Execution/operation/StartBatchRun) | Startet eine Batch-Ausgabegenerierung mithilfe einer Konfiguration. | Asynchron/Batch | [JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/batch/output/config/{configName}/execution/{executionId}](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Execution/operation/GetBatchRunInstanceState) | Ruft den Ausführungsstatus eines Batch-Vorgangs ab. | Asynchron/Batch | [JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/batch/output/config/{configName}/execution](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/#tag/Batch-Execution/operation/GetAllRunningInstancesForBatch) | Listet alle laufenden Instanzen für eine bestimmte Batch-Konfiguration auf. | Asynchron/Batch | [JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/doc/v1/generatePDFOutput](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/#tag/Communications-Services/paths/~1adobe~1forms~1doc~1v1~1generatePDFOutput/post) | Erzeugt synchron eine PDF-Ausgabe basierend auf Vorlagen und Daten. | Synchron | [JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/doc/v1/generatePrintedOutput](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/#tag/Batch-Execution/operation/GetAllRunningInstancesForBatch) | Generiert druckfertige Ausgabeformate (z. B. PCL, PostScript). | Synchron | [JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/doc/v1/generate/afp](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/#tag/Communications-Services/paths/~1adobe~1forms~1doc~1v1~1generate~1afp/post) | Generiert eine AFP-Ausgabe für den Druck großer Volumen. | Synchron | [JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/document/generate/pdfform](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFForm) | Rendert ein PDF-Formular (XFA/XDP) mit zusammengeführten Daten. | Synchron | [OAuth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/generate/pdfform/jobs/{id}/status](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFFormJobStatus) | Ruft den Status eines PDF-Formulargenerierungsauftrags ab. | Synchron | [OAuth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/generate/pdfform/jobs/{id}/result](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFFormJobResult) | Ruft die Ausgabe/das Ergebnis eines abgeschlossenen PDF-Formularauftrags ab. | Synchron | [OAuth](/help/forms/oauth-api-authetication.md) |


#### APIs zur Dokumentbearbeitung

| API-Endpunkt | Beschreibung | Ausführungsmodell | Authentifizierungsmethode |
| ------------------ | ---------------- | ----------| ---------- |
| [/adobe/forms/assembler/ddx/invoke](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/#tag/DDX-execution/operation/InvokeDDX) | Führt DDX-Anweisungen aus, um PDFs zu kombinieren, aufzuteilen oder zu bearbeiten. | Synchron | [JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/assembler/pdfa/convert](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/#tag/Document-conversion/operation/ConvertToPDFA) | Konvertiert ein PDF-Dokument in das PDF/A-Format. | Synchron | [JWT](/help/forms/jwt-api-authentication.md) |
| [/adobe/forms/assembler/pdfa/validate](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/#tag/Document-validation/operation/CheckIsPDFA) | Prüft, ob ein PDF den PDF/A-Standard erfüllt | Synchron | [JWT](/help/forms/jwt-api-authentication.md) |

#### APIs zur Dokumentkonvertierung

| API-Endpunkt | Beschreibung | Ausführungsmodell | Authentifizierungsmethode |
|--------- | -------|---------|----------------------|
| [/adobe/document/convert/pdftoxdp](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Conversion/paths/~1convert~1pdftoxdp/post) | Konvertiert ein PDF-Formular in das XDP-Format. | Synchron | [OAuth](/help/forms/oauth-api-authetication.md) |

#### APIs zur Dokumentextraktion

| API-Endpunkt | Beschreibung | Ausführungsmodell | Authentifizierungsmethode |
|---------| -------|---------|----------------------|
| [/adobe/forms/doc/v1/extract/pdfproperties](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Extraction/paths/~1extract~1pdfproperties/post) | Extrahiert Eigenschaften und Strukturinformationen aus einer PDF. | Synchron | [OAuth](/help/forms/oauth-api-authetication.md) |
| [/adobe/forms/doc/v1/extract/usagerrights](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/extractUsageRights) | Extrahiert in eine PDF eingebettete Verwendungsrechte. | Synchron | [OAuth](/help/forms/oauth-api-authetication.md) |
| [/adobe/forms/doc/v1/extract/metadata](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Extraction/paths/~1extract~1metadata/post) | Extrahiert Metadaten wie Titel, Autor und Schlüsselwörter. | Synchron | [OAuth](/help/forms/oauth-api-authetication.md) |
| [/adobe/forms/doc/v1/extract/data](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/exportData) | Extrahiert Formulardaten (XML/JSON) aus PDF forms. | Synchron | [OAuth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/extract/security](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Extraction/paths/~1extract~1security/post) | Extrahiert Sicherheitseinstellungen wie Berechtigungen und Verschlüsselung. | Synchron | [OAuth](/help/forms/oauth-api-authetication.md) |

#### Document Transformation-APIs


| API-Endpunkt | Beschreibung | Ausführungsmodell | Authentifizierungsmethode |
|--------|---------|---------|----------------------|
| [/adobe/document/transform/metadata](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1transform~1metadata/post) | Aktualisiert oder fügt Metadaten in einem PDF-Dokument hinzu. | Synchron | [OAuth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/field/signature/add](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1field~1signature~1add/post) | Fügt ein digitales Signaturfeld zu einer PDF hinzu. | Synchron | [OAuth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/field/signature/clear](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1field~1signature~1clear/post) | Löscht den Inhalt eines Signaturfelds. | Synchron | [OAuth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/field/signature/remove](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Transformation/paths/~1field~1signature~1remove/post) | Entfernt ein Signaturfeld aus einer PDF. | Synchron | [OAuth](/help/forms/oauth-api-authetication.md) |

#### Document Assurance-APIs

| API-Endpunkt | Beschreibung | Ausführungsmodell | Authentifizierungsmethode |
|---------|-------|---------|----------------------|
| [/adobe/document/assurance/usagerrights](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/applyUsageRights) | Wendet Verwendungsrechte auf eine PDF an (z. B. Kommentieren, Ausfüllen, Signieren). | Synchron | [OAuth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/assurance/encrypt](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1encrypt/post) | Verschlüsselt eine PDF mit Passwort- oder Zertifikatsicherheit. | Synchron | [OAuth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/assurance/decrypt](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1decrypt/post) | Entschlüsselt ein gesichertes PDF-Dokument. | Synchron | [OAuth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/assurance/sign](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1sign/post) | Digitales Signieren eines PDF-Dokuments. | Synchron | [OAuth](/help/forms/oauth-api-authetication.md) |
| [/adobe/document/assurance/certificate](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#tag/Document-Assurance/paths/~1assure~1certify/post) | Zertifiziert eine PDF mit einem digitalen Zertifikat. | Synchron | [OAuth](/help/forms/oauth-api-authetication.md) |


## Verwandte Schritte

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
