---
title: Asset-Beschaffungsportal für AEM Assets
description: Erfahren Sie, wie Sie das Assets-Beschaffungsportal erstellen, das ein sicheres Self-Service-Erlebnis für das Erfassen von Assets von externen Mitwirkenden bietet, ohne ihnen Zugriff auf Adobe Experience Manager Assets zu gewähren.
role: Admin
hide: true
badgeSaas: label="AEM Assets" type="Positive" tooltip="Gilt für AEM Assets)."
source-git-commit: c2a7e7ab0b3c8c336343036af105a827cd77f3c2
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 4%

---


# Asset-Beschaffungsportal für AEM Assets {#asset-sourcing-portal-aem-assets}

Unternehmen sind häufig auf Fotografen, Kreativagenturen und andere externe Mitwirkende angewiesen, um digitale Assets bereitzustellen. Das Erfassen dieser Assets über E-Mail, freigegebene Laufwerke oder File-Sharing-Dienste kann zu inkonsistenten Metadaten, manueller Verarbeitung und zusätzlichem Verwaltungsaufwand führen. Für die Bereitstellung von direktem Zugriff auf ein DAM-System (Digital Asset Management) für externe Mitwirkende können zusätzliche Lizenzen erforderlich sein und interne Inhalte verfügbar gemacht werden.

Das Assets-Beschaffungsportal bietet ein sicheres Self-Service-Erlebnis für die Erfassung von Assets von externen Mitwirkenden, ohne ihnen Zugriff auf Adobe Experience Manager Assets zu gewähren. Mitwirkende können Assets hochladen, die erforderlichen Metadaten bereitstellen und Inhalte direkt an einen bestimmten Aufnahmeort senden, während Admins die Kontrolle über die Organisation und Governance der Assets behalten.

>[!IMPORTANT]
>
>Diese Funktion ist als Funktion für eingeschränkte Verfügbarkeit verfügbar. Sie können [einen Adobe-Support-Fall erstellen und übermitteln](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) um die Funktion für Ihre Bereitstellung zu aktivieren.

## Vorteile {#benefits-asset-sourcing-aem-assets}

Die Verwendung des Assets-Beschaffungsportals bietet die folgenden Vorteile:

- Externen Mitwirkenden erlauben, Assets hochzuladen, ohne eine AEM Assets-Lizenz zu benötigen.
- Vereinfachen Sie die Asset-Aufnahme durch ein dediziertes Upload-Erlebnis.
- Reduzieren Sie die manuelle Verarbeitung durch die automatische Anwendung von Metadaten- und Aufnahmerichtlinien.
- Verbessern Sie die Governance, indem Sie kontrollieren, wo hochgeladene Assets gespeichert werden und welche Metadaten von Mitwirkenden bereitgestellt werden.
- Skalieren Sie das Onboarding für mehrere Mitwirkende, ohne benutzerdefinierte Upload-Lösungen zu erstellen.

## Wie funktioniert die Asset-Beschaffung? {#how-asset-sourcing-works-in-aem-assets}

Admins konfigurieren ein Quellportal für externe Mitwirkende, indem sie Folgendes definieren:

- Der Zielspeicherort für die Aufnahme hochgeladener Assets.
- Die Metadatenfelder, die Mitwirkende ausfüllen müssen.
- Optionale Aufnahmerichtlinien, wie Namenskonventionen und Benachrichtigungen.

Mitwirkende erhalten ein dediziertes Upload-Erlebnis, in dem sie:

- Laden Sie ein oder mehrere Assets hoch.
- Füllen Sie die erforderlichen Metadatenfelder aus.
- Übermitteln von Assets für die Aufnahme in Adobe Experience Manager Assets.

Während der Aufnahme werden hochgeladene Assets gemäß den konfigurierten Richtlinien verarbeitet, bevor sie am angegebenen Aufnahmespeicherort gespeichert werden.

## Upload-Methoden {#upload-methods-asset-sourcing-aem-assets}

Das Assets-Quellportal unterstützt mehrere Upload-Methoden, damit Mitwirkende in ihren bevorzugten Workflows arbeiten können.

- **Browser-Portal:** Bietet ein Web-basiertes Upload-Erlebnis, bei dem Mitwirkende Dateien per Drag-and-Drop verschieben und die erforderlichen Metadaten abschließen können, bevor sie Assets senden.

- **REST API:** Ermöglicht Unternehmen die Integration von Asset-Uploads in bestehende Produktionssysteme oder automatisierte Workflows.

- **Anbieter-MCP:** Ermöglicht es Mitwirkenden, die in KI-unterstützten Umgebungen arbeiten, Assets über unterstützte Konversations-Workflows hochzuladen.

Alle Upload-Methoden bieten dieselben grundlegenden Asset-Aufnahmefunktionen.

## Schlüsselfunktionen {#key-capabilities-asset-sourcing-aem-assets}

- **Sicherer Zugriff für Mitwirkende** Externe Mitwirkende können Assets hochladen, ohne auf das DAM zuzugreifen, Repositorys zu durchsuchen oder andere Assets anzuzeigen.

- **Konfigurierbare Metadatenerfassung:** Admins wählen Metadatenfelder aus dem AEM Assets-Metadatenschema aus. Das Portal generiert automatisch das Übermittlungsformular des oder der Mitwirkenden auf der Grundlage der ausgewählten Felder.

- **Automatisierte Asset-Aufnahme:** Hochgeladene Assets werden an einen bestimmten Aufnahmespeicherort weitergeleitet, wobei konfigurierte Metadaten während der Aufnahme angewendet werden.

- **Konfigurierbare Erfassungsrichtlinien:**-Administratoren können Erfassungsregeln für jeden Mitwirkenden definieren, einschließlich erforderlicher und optionaler Metadatenfelder, vorausgefüllter Werte, Batch-Kennungen, Asset-Benennungskonventionen, Zielpfaden, minimaler Asset-Dimensionen und Administrator-Benachrichtigungen.

- **Onboarding von skalierbaren Mitwirkenden:** Konfigurieren mehrerer Mitwirkender mit verschiedenen Upload-Zielen, Metadatenanforderungen und Aufnahmerichtlinien, ohne benutzerdefinierte Upload-Anwendungen zu entwickeln.

## Anwendungsbeispiele {#example-use-cases-asset-sourcing}

- **Sammeln von Assets aus Kreativagenturen:** Sie Agenturen zu, Kampagnen-Assets über ein dediziertes Upload-Portal zu senden, ohne Zugriff auf das DAM der Organisation zu gewähren.

- **Fotografieeinreichungen erhalten:** Ermöglichen Sie Fotografen ein einfaches Upload-Erlebnis, bei dem die erforderlichen Metadaten automatisch erfasst und Assets am entsprechenden Aufnahmespeicherort gespeichert werden.

- **Integrieren von externen Produktionssystemen:** Verwenden Sie die REST-API, um Assets automatisch aus Produktions- oder Inhaltserstellungssystemen von Drittanbietern zu übermitteln.

## Verwendung dieser Funktion {#when-to-use-this-capability}

Verwenden Sie das Assets-Quellportal, wenn Sie Folgendes tun müssen:

- Sammeln Sie Assets von Fotografen, Agenturen und externen Anbietern.
- Standardisieren der Metadatenerfassung während der Asset-Aufnahme.
- Sichern von Asset-Übermittlungen ohne DAM-Zugriff.
- Automatisieren Sie die Asset-Aufnahme an festgelegten Aufnahmespeicherorten.
- Unterstützung einer großen Anzahl externer Mitwirkender.

## Wann diese Funktion nicht verwendet werden sollte {#when-not-to-use-this-capability}

Das Assets-Beschaffungsportal ist nicht für Folgendes vorgesehen:

- Verwalten von Assets innerhalb des DAM nach der Aufnahme.
- Bereitstellen von Zugriff für Mitwirkende zum Durchsuchen, Suchen oder Herunterladen von DAM-Assets.
- Workflows für die interne Zusammenarbeit, die vollständige DAM-Funktionalität erfordern