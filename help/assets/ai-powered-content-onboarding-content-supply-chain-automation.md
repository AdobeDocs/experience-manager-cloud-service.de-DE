---
title: KI-gestütztes Content-Onboarding und Inhaltsautomatisierung mit supply chain
description: Erfahren Sie, wie Sie einmalige Inhaltsmigrationen und die Automatisierung von supply chain-Inhalten zwischen Adobe und unterstützten Repositorys von Drittanbietern automatisieren können.
role: Admin
hide: true
badgeSaas: label="AEM Assets" type="Positive" tooltip="Gilt für AEM Assets)."
source-git-commit: 3985d61b59b610c63f94407a9fdc4860390d7e42
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 2%

---


# KI-gestütztes Content-Onboarding und Inhaltsautomatisierung mit supply chain {#ai-powered-content-onboarding-content-supply-chain-automation}

Unternehmen speichern häufig digitale Assets und Metadaten über mehrere Repositorys hinweg, z. B. Digital Asset Management (DAM)-Systeme, Cloud-Speicher-Services und Inhaltsplattformen. Die Migration von Inhalten auf ein neues System oder die Synchronisierung mehrerer Repositorys erfordert in der Regel manuellen Aufwand oder benutzerdefinierte Integrationen, die schwer zu erstellen und zu pflegen sind.

Mit dieser Funktion können Sie einmalige Inhaltsmigrationen und wiederkehrende Synchronisierungen zwischen unterstützten Repositorys automatisieren. Ein KI-basierter Agent führt Sie durch die Konfiguration von Inhaltsübertragungen, indem er Repository-Verbindungen, Metadatenzuordnungen und Übertragungseinstellungen vorschlägt und so den Aufwand für das Verschieben und Synchronisieren von Inhalten zwischen Systemen reduziert.

## Vorteile {#benefits-ai-powered-content-onboarding-content-supply-chain-automation}

Die Automatisierung des Onboarding und der Synchronisierung von Inhalten bietet die folgenden Vorteile:

- Beschleunigen Sie das Onboarding, indem Sie den Zeitaufwand für die Migration vorhandener Assets und Metadaten in ein neues Repository reduzieren.
- Vereinfachen Sie die wiederkehrende Synchronisierung durch die Automatisierung geplanter Inhaltsübertragungen zwischen Datensatzsystemen.
- Reduzieren Sie den Wartungsaufwand, indem Sie benutzerdefinierte Integrationen durch konfigurierbare Verbindungen ersetzen.
- Unterstützung von Inhaltstransfers zwischen Adobe und Repositorys von Drittanbietern.
- Überprüfen Sie die Übertragungseinstellungen mithilfe von Probeläufen, bevor Sie Inhalte verschieben.

## Wie funktionieren Inhaltsübertragungen? {#how-content-transfer-work}

Der KI-gestützte Agent hilft beim Konfigurieren einer Inhaltsübertragung zwischen einem Quell-Repository und einem Ziel-Repository.

Während der Konfiguration wird der Agent:

- Erfasst die für die Verbindung mit jedem Repository erforderlichen Informationen.
- Bietet Zuordnungen zwischen Metadatenfeldern und Taxonomien.
- Ermöglicht die Überprüfung und Validierung der vorgeschlagenen Zuordnungen vor der Übertragung von Inhalten.
- Unterstützt Probeläufe, damit Sie die Konfiguration überprüfen können, bevor Sie Produktionsinhalte verschieben.
- Konfiguriert einmalige oder wiederkehrende Übertragungspläne.

Jede konfigurierte Übertragung wird als &quot;**&quot;**. Eine Verbindung verwendet **Gateways** um mit den Quell- und Ziel-Repositorys zu kommunizieren. Jede Ausführung einer Verbindung wird als &quot;**&quot;**.

Ausführungen sind statusbehaftet. Sie verfolgen zuvor übertragene Assets und Metadaten, sodass bei nachfolgenden Ausführungen nur neue oder geänderte Inhalte übertragen werden, anstatt das gesamte Repository erneut zu verarbeiten.

## Schlüsselfunktionen {#key-capabilities-ai-powered-content-onboarding-content-supply-chain-automation}

- **Identitätszuordnung**: Behält die Beziehung zwischen Assets im Quell- und Ziel-Repository über mehrere Ausführungen hinweg bei.

- **Änderungserkennung**: Überträgt nur Assets und Metadaten, die sich seit der vorherigen Ausführung geändert haben, wodurch die unnötige Verarbeitung reduziert und die Effizienz verbessert wird.

- **Metadatenzuordnung**: Ordnet Metadatenfelder und Taxonomien zwischen Repositorys im Rahmen des Inhaltstransfers zu.

- **Probeläufe**: Validiert Zuordnungen und Übertragungseinstellungen, bevor Inhalte in das Ziel-Repository verschoben werden.

- **Geplante Synchronisierung**: Führt Übertragungen nach einem wiederkehrenden Zeitplan aus, z. B. stündlich, täglich oder wöchentlich.

- **Benutzerdefinierte Umwandlungen**: Unterstützt bei Bedarf zusätzliche Umwandlungslogik, einschließlich JavaScript, regulären Ausdrücken, Webhooks und Inhalts-Hashing.

## Unterstützte Repositorys {#supported-repositories}

Inhalte können über unterstützte Quell- und Ziel-Gateways zwischen Adobe und Repositorys von Drittanbietern übertragen werden.

Beispiele für unterstützte Repositorys:

- Adobe Experience Manager Assets
- Adobe Content Platform
- Adobe Commerce
- Amazon S3
- Azure Blob Storage
- Box
- Dropbox
- Google Drive
- OneDrive
- WordPress
- Workfront
- FTP- und SFTP-Server
- SMB-Dateifreigaben

Weitere Repositorys sind für zukünftige Versionen geplant.

## Anwendungsbeispiele {#example-use-cases}

### Migrieren von Inhalten in ein neues Repository

Konfigurieren Sie eine einmalige Migration von einem alten DAM- oder Cloud-Speicher-Repository in ein neues Aufzeichnungssystem. Prüfen Sie die Metadatenzuordnungen mit einem Probelauf, bevor Sie Produktionsinhalte übertragen.

### Synchronisieren von Repositorys

Halten Sie Inhalte zwischen dem Cloud-Speicher und einem DAM synchronisiert, indem Sie eine wiederkehrende Übertragung konfigurieren, die nur neu hinzugefügte oder geänderte Assets verarbeitet.

### Optimieren von supply chain-Inhalten

Reduzieren Sie manuelle Inhaltsverschiebungen, indem Sie die Übertragung zwischen Repositorys automatisieren, die während des gesamten Inhaltslebenszyklus Ihres Unternehmens verwendet werden.

## Verwendung dieser Funktion {#when-to-use-ai-powered-content-onboarding-content-supply-chain-automation}

Diese Funktion ist gut geeignet für:

- Einmalige Inhaltsmigrationen.
- Onboarding neuer Datensatzsysteme.
- Wiederkehrende Synchronisierung zwischen Repositorys.
- Metadaten- und Taxonomiezuordnung während Inhaltsübertragungen.
- Automatisieren der Inhaltsverschiebung über mehrere Repositorys hinweg

## Wann diese Funktion nicht verwendet werden sollte {#when-not-to-use-ai-powered-content-onboarding-content-supply-chain-automation}

Diese Funktion ist nicht für Folgendes vorgesehen:

- Allgemeine Workflow- oder Geschäftsprozessautomatisierung.
- Analytics- oder Kundendaten-ETL-Pipelines.
- Ereignisgesteuerte Echtzeit-Verbreitung.
- Kontinuierliches Byte-Streaming zwischen Repositorys.




