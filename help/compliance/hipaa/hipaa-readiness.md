---
title: HIPAA-Bereitschaft für Adobe Experience Manager as a Cloud Service
description: Erfahren Sie mehr über die Unterstützung von Experience Manager as a Cloud Service für die HIPAA-Vorschriften und darüber, wie Sie sie bei der Implementierung eines neuen AEM as a Cloud Service-Projekts einhalten können.
feature: Compliance
role: Admin, Architect, Developer, Leader
source-git-commit: 49721ac71bc2bde10eb5f25db58ee1b07c8a82e5
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 6%

---

# HIPAA-Bereitschaft für Adobe Experience Manager as a Cloud Service {#hipaa-readiness-for-adobe-experience-manager-as-a-cloud-service}

>[!WARNING]
>
>Der Inhalt dieses Dokuments stellt keine Rechtsberatung dar und ist nicht als Ersatz für Rechtsberatung gedacht.
>
>Wenden Sie sich an die Rechtsabteilung Ihres Unternehmens, um sich über HIPAA-Vorschriften zu beraten.

>[!NOTE]
>
>Weitere Informationen über die Reaktion von Adobe auf Datenschutzprobleme und was dies für Sie als Adobe-Kunde bedeutet, finden Sie unter:
>
>* [HIPAA und Adobe Produkte und Services](https://www.adobe.com/trust/compliance/hipaa-hds/hipaa-ready.html) im Adobe Trust Center
>* [Datenschutzzentrum von Adobe](https://www.adobe.com/de/privacy.html)

Für Adobe Experience Manager (AEM) as a Cloud Service stellt Adobe Dokumentationen bereit, die Ihnen dabei helfen, die HIPAA-Bereitschaft zu verstehen. Dies kann Ihnen helfen, diese Vorschriften einzuhalten.

## Health Insurance Portability and Accountability Act (HIPAA) {#health-insurance-portability-and-accountability-act-hipaa}

### Gesetz über die Übertragbarkeit und Rechenschaftspflicht von Krankenversicherungen (HIPAA) {#the-health-insurance-portability-and-accountability-act-hipaa}

Die HIPAA-Regeln für Datenschutz, Sicherheit und Verletzungsbenachrichtigung legen wichtige Schutzbestimmungen für individuell identifizierbare Gesundheitsinformationen fest, die als geschützte Gesundheitsinformationen (Protected Health Information, PHI) bezeichnet werden.

Unter HIPAA ist eine abgedeckte Stelle ein Gesundheitsdienstleister, ein Gesundheitsplan oder eine Clearingstelle für Gesundheitsdienstleistungen. Ein Geschäftspartner ist eine Einheit, die Dienstleistungen für eine abgedeckte Einheit erbringt, die Zugang zu PHI beinhaltet. Die HIPAA-Datenschutz- und Sicherheitsvorschriften verlangen, dass ein abgedecktes Unternehmen schriftliche Zusicherungen von einem Geschäftspartner in Form einer Geschäftspartnervereinbarung (Business Associate Agreement, BAA) erhält, in der der Geschäftspartner verpflichtet ist, die Privatsphäre und Sicherheit des PHI des abgedeckten Unternehmens zu schützen.

### Bereitstellen von PHI für Adobe {#providing-phi-to-adobe}

Adobe fungiert als Business Associate für seine HIPAA-fähigen Services, die unter [HIPAA-Bereitschaft von Services in AEM as a Cloud Service&quot; aufgeführt ](#hipaa-readiness-of-services-in-aem-as-a-cloud-service).

Kunden, die einen Adobe HIPAA-fähigen Service zur Verarbeitung von PHI lizenzieren **müssen** über die richtige Lizenz verfügen und einen unterzeichneten BAA mit Adobe besitzen.

>[!IMPORTANT]
>
>Kunden sind nicht berechtigt, PHI über Adobe-Produkte und -Services zu erstellen, zu empfangen, zu pflegen oder zu übertragen, die nicht als HIPAA-fähige Services ausgewiesen sind, oder ohne die entsprechende Lizenz zur Verwendung eines HIPAA-fähigen Services.

### HIPAA - Gemeinsame Zuständigkeiten {#hipaa-shared-responsibilities}

Adobe HIPAA-fähige Services basieren auf einem Sicherheitsmodell mit gemeinsamer Verantwortung, bei dem der Kunde und Adobe jeweils unterschiedliche Verantwortlichkeiten für die Aufrechterhaltung der Sicherheit von PHI tragen. Bei diesem freigegebenen Sicherheitsmodell verlässt sich Adobe darauf, dass der Kunde die HIPAA-fähigen Services im Einklang mit HIPAA verwendet und konfiguriert.

Weitere Informationen zum Ausführen einer Adobe-BAA für HIPAA-fähige Services erhalten Sie von Ihrem Adobe-Vertriebsmitarbeiter oder Customer Success Manager.

>[!IMPORTANT]
>
>**Haftungsausschluss**:
>
>Der Kunde ist dafür verantwortlich, dass er Adobe HIPAA-fähige Services nutzt und sicherstellt, dass die Adobe HIPAA-fähigen Services die Compliance-Anforderungen erfüllen.

Weitere Informationen finden Sie unter [HIPAA und Adobe-Produkte und -Services](https://www.adobe.com/trust/compliance/hipaa-hds/hipaa-ready.html) im Adobe Trust Center.

## HIPAA-Terminologie {#hipaa-terminology}

Die folgende Tabelle beschreibt, wie AEM-Services für die HIPAA-Nutzung kategorisiert sind.

| HIPAA-Bereitschaft | Beschreibung |
| --- | --- |
| HIPAA-fähig | Entwickelt für die Verarbeitung von PHI bei entsprechender Konfiguration und Verwendung mit einer BAA. |
| Nicht HIPAA-fähig | Nicht für die Verarbeitung von PHI konzipiert und darf nicht in HIPAA-bezogenen Anwendungsfällen verwendet werden. |

>[!NOTE]
>
>Klassifizierungen der HIPAA-Bereitschaft basieren auf der beabsichtigten Funktionalität jedes Service und können sich im Laufe der Zeit ändern.
>
>Kunden sollten bei der Planung von HIPAA-bezogenen Bereitstellungen die aktuellste Dokumentation und die geltenden Vertragsbedingungen beachten.

## HIPAA-Bereitschaft der Services in AEM as a Cloud Service {#hipaa-readiness-of-services-in-aem-as-a-cloud-service}

In der folgenden Tabelle wird beschrieben, welche AEM-Services HIPAA-fähig sind und welche Services zusammen mit ihnen verwendet werden können. HIPAA-fähige Services erfordern den Kauf von Extended Security for Healthcare, wie unter [Zusätzliche Anforderungen](#additional-requirements) beschrieben.

| Produkt/Funktion | Service(s) | HIPAA-Bereitschaft |
| --- | --- | --- |
| AEM Sites | AEM Sites, AEM Publish, Edge Delivery Services | HIPAA-fähig |
| AEM Sites | Universeller Editor | Nicht HIPAA-bereit<br>[1] Kann einem erweiterten Sicherheitsprogramm hinzugefügt werden, wenn kein PHI eingeführt wird. |
| AEM Sites Optimizer | Sites Optimizer | Nicht HIPAA-bereit<br>[1] Kann einem erweiterten Sicherheitsprogramm hinzugefügt werden, wenn kein PHI eingeführt wird. |
| AEM Assets | AEM Assets | HIPAA-fähig |
| AEM Assets | Content Hub | Nicht HIPAA-bereit<br>[1] Kann einem erweiterten Sicherheitsprogramm hinzugefügt werden, wenn kein PHI eingeführt wird. |
| AEM Assets | Brand Portal | Nicht HIPAA-fähig |
| AEM Assets | Dynamic Media OpenAPI | Nicht HIPAA-bereit<br>[1] Kann einem erweiterten Sicherheitsprogramm hinzugefügt werden, wenn kein PHI eingeführt wird. |
| AEM Assets | Dynamic Media Scene7 | Nicht HIPAA-fähig |
| AEM Forms | AEM Forms, Authentication Facade Service, PDF Utility-Service | HIPAA-fähig |
| AEM CIF | Commerce Integration Framework | Nicht HIPAA-fähig |
| AEM Cloud Manager | AEM Cloud Manager, Release Orchestrator, Release-Umschalter, Release-Validator | HIPAA-fähig |
| AEM Cloud Manager | Software-Verteilung | Nicht HIPAA-bereit<br>[1] Kann einem erweiterten Sicherheitsprogramm hinzugefügt werden, wenn kein PHI eingeführt wird. |
|   |   |   |
| AEM Guides  | AEM Guides  | Nicht HIPAA-fähig |
|   |   |   |
| LLM Optimizer | LLM Optimizer | Nicht HIPAA-bereit<br>[1] Kann einem erweiterten Sicherheitsprogramm hinzugefügt werden, wenn kein PHI eingeführt wird. |

>[!NOTE]
>
>[1]
>
>Bei nicht HIPAA-fähigen Services, die als zu einem erweiterten Sicherheitsprogramm hinzugefügt werden können, müssen Kunden sicherstellen, dass PHI nicht zu diesen Services weitergeleitet oder in diesen gespeichert wird.
>
>Die Einführung von PHI in einen Service, der nicht HIPAA-fähig ist, kann zu Verstößen führen.

### Zusätzliche Anforderungen {#additional-requirements}

[Services aufgeführt](#hipaa-readiness-of-services-in-aem-as-a-cloud-service) als HIPAA-fähig erfordern den Kauf von Extended Security for Healthcare.

Beim Kauf von Extended Security for Healthcare besteht die Anforderung, dass:

* die für dieses Programm ausgewählten Produkte HIPAA-fähig sind (wie in der Tabelle aufgeführt),
* Für jedes Produkt wurde ein erweiterter Schutz für *erworben* wodurch eine ausreichende Anzahl von Cloud Manager-Credits sichergestellt wird.
* Erweiterte Sicherheit für das Gesundheitswesen wird zum Zeitpunkt der Programmerstellung angewendet.

Wenn die Anforderungen erfüllt sind, kann die erweiterte Sicherheit für das Gesundheitswesen bei der Erstellung des AEM-Programms angewendet werden. Weitere Informationen finden [ unter &quot;](#setup)&quot;.

>[!NOTE]
>
>Weitere Informationen zu Bereitstellung und Preisen erhalten Sie von Ihrem Vertriebsmitarbeiter.

## Umgebungen {#environments}

*HIPAA-fähig* gilt nicht für RDE- (Rapid Development Environment), Entwicklungs- oder Staging-Umgebungen, da PHI in diesen Umgebungen nicht zulässig ist.

Das bedeutet, dass Sie:

* Verwenden von Platzhalterdaten für Entwicklungs- und Testzwecke
* Nur PHI aus Produktionsumgebungen verarbeiten

Die folgende Tabelle zeigt, wo die Umgebungstypen als HIPAA-fähig unterstützt werden können.

| | RDE | Entw. | Etappe  | prod |
| --- | --- | --- | --- | --- |
| Umgebungstyp  | Nein  | Nein  | Nein  | Ja  |

## Einrichtung {#setup}

Beim [Erstellen von Produktionsprogrammen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) bietet die Registerkarte [Sicherheit“ die Optionen zum Aktivieren des HIPAA-Schutzes](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#security).