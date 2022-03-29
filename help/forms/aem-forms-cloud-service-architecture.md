---
title: Architektur von Experience Manager [!DNL AEM Forms] as a Cloud Service
description: Machen Sie sich mit der Architektur von [!DNL AEM Forms] as a Cloud Service vertraut, um mehr über die Skalierbarkeit, Widerstandsfähigkeit und Leistung der Plattform zu erfahren.
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1091'
ht-degree: 100%

---


# Architektur von [!DNL AEM] as a Cloud Service {#architecture}

[!DNL AEM Forms] as a Cloud Service standardisiert die Bereitstellungsarchitektur für alle Kunden mit dem Ziel, Kunden vollständig von Überlegungen bezüglich der Architektur zu entlasten. Auch wenn die neue Architektur von AEM as a Cloud Service beispielsweise aus Gründen der Persistenz weiterhin auf dem Konzept der Mikro-Kernel beruht, müssen sich Kunden keine Gedanken über die Wahl des Mikro-Kernels machen. Die für Authoring und Publishing verwendeten Mikro-Kernel sind nur für [!DNL AEM Cloud Service] verfügbar und ansonsten nicht von Kunden mit On-Premise-Implementierung nutzbar.

AEM as a Cloud Service verfügt über eine dynamische Architektur mit einer variablen Anzahl von AEM-Instanzen. Die Lösung bietet spezielle Umgebungen für Entwicklung, Staging, Produktion und Demonstration. Sie bietet Tools zum Verwalten von AEM (Cloud Manager), Verwalten von Benutzern und Authentifizierungen (Admin Console- und IMS (Adobe Identity Management)-System), Konfigurieren der Caching-Funktion (Fastly CDN) und für die Cloud-native Entwicklungsumgebung. Weitere Informationen zur Architektur finden Sie unter [Einführung in die Architektur von [!DNL Adobe Experience Manager as a Cloud Service]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html?lang=de).

## Cloud Manager {#cloud-manager}

Cloud Manager ist eine wesentliche Komponente von [AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=de). Jeder neue Mandant von [!DNL AEM Forms] as a Cloud Service erhält zunächst Zugriff auf Cloud Manager. Cloud Manager ist die zentrale Anlaufstelle für die Operations- und Developer-Persona unserer Kunden. Es ist der Ort, an dem AEM-Programme und -Umgebungen verwaltet werden. Cloud Manager hat sich zu einem Selbstbedienungsportal entwickelt, in dem die Hauptkomponenten von AEM as a Cloud Service erstellt und konfiguriert werden können:

* Erstellen und Verwalten von Programmen
* Erstellen und Verwalten von AEM-Umgebungen in diesen Programmen
* Erstellen und Verwalten der Pipelines für die Bereitstellung des Kunden-Codes und der zugehörigen Konfiguration in einer bestimmten Umgebung
* Benachrichtigung über wichtige Lebenszyklus-Ereignisse dieser Komponenten (z. B. Produkt-Updates)
Weitere Informationen zu Cloud Manager finden Sie unter [Grundlagen zu Adobe Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/understand-cloud-manager-for-aem.html?lang=de) und [Einführung in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=de).

## Benutzer und Authentifizierung {#users-and-authentication}

AEM as a Cloud Service umfasst die Unterstützung der Admin Console für AEM-Instanzen und die auf dem Adobe Identity Management System (IMS) basierende Authentifizierung. Die Admin Console ermöglicht Administratoren die zentrale Verwaltung aller Experience Cloud-Benutzer. Benutzer und Gruppen können Produktprofilen zugeordnet werden, die mit AEM as a Cloud Service-Instanzen verknüpft sind, sodass sie sich bei dieser Instanz anmelden können. Weitere Informationen zu Benutzern, Authentifizierung und Zugriff auf eine Instanz von AEM as a Cloud Service finden Sie unter [IMS-Unterstützung für [!DNL Adobe Experience Manager] as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=de#introduction).

An einem typischen [!DNL AEM Forms]-Projekt sind verschiedene Rollen beteiligt. Nach der Anmeldung bei Ihrer [!DNL AEM Forms] as a Cloud Service-Instanz können Sie [in der Admin Console Benutzer für die Rollen Ihres Unternehmens oder Projekts hinzufügen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=de) und dann [Benutzer den integrierten Gruppen zuweisen](forms-groups-privileges-tasks.md), um die erforderlichen Berechtigungen zu erteilen.

Weitere Informationen zu den verschiedenen integrierten [!DNL AEM Forms]-spezifischen Benutzergruppen und -Berechtigungen, die für die [!DNL AEM Forms] as a Cloud Service-Instanz verfügbar sind, finden Sie unter [Konfigurieren von Benutzern, Rollen und Gruppen](forms-groups-privileges-tasks.md).

## Entwicklererlebnis {#developer-experience}

Die neue Architektur von AEM as a Cloud Service beinhaltet einige wichtige Änderungen am Entwicklererlebnis. Eines der wichtigsten Ziele ist eine möglichst schnelle Migration zu AEM as a Cloud Service mit nur wenigen Änderungen am vorhandenen benutzerspezifischen Code.

## Cloud-Entwicklung {#cloud-development}

Folgende Empfehlungen für eine reibungslose Ausführung des vorhandenen Codes in AEM as a Cloud Service-Umgebungen sind zu beachten:

* Speichern Sie den Code und die Konfigurationen im Git-Repository des zugehörigen Cloud Manager-Programms. Das Verwalten und Integrieren von Code mit CI/CD wird dadurch stark vereinfacht.
* Gewährleisten Sie die Kompatibilität des Anwendungs-Codes und der Konfiguration mit den grundlegenden [!DNL AEM Forms]-Bildern. Die Verwendung der neuesten APIs hilft beim Erstellen von schnellen und sicheren Anwendungen.
* Verwenden Sie die Cloud Manager-Pipeline, die der Cloud Manager-Umgebung zugeordnet ist, zum Erstellen und Bereitstellen von Anwendungen. Sie hilft Ihnen, in Ihrer Umgebung von den neuesten Funktionen und Fehlerbehebungen für [!DNL AEM Forms] as a Cloud Service zu profitieren.
* Sorgen Sie dafür, dass Ihre benutzerdefinierten Anwendungen alle in der Pipeline erzwungenen Code-Qualitäts-, Sicherheits- und Leistungskriterien erfüllen. Dadurch können Sie sichere und effiziente Anwendungen entwickeln, die bessere Kundenerlebnisse ermöglichen. Über die Benutzeroberfläche von Cloud Manager können Sie jederzeit einige Prüfungen überspringen.
Dieser Prozess wird häufig als Cloud-First-Entwicklung bezeichnet. [!DNL AEM Forms] as a Cloud Service bietet zudem ein SDK für eine schnelle Entwicklung, bevor die ausstehenden Code- und Konfigurationsänderungen in der Cloud angewendet werden.
Einige Schnittstellen, die bisher Teil von AEM QuickStart waren, stehen den Benutzern der AEM as a Cloud Service-Umgebung nicht mehr zur Verfügung. Dazu gehört die Web Console, über die OSGI-Pakete und die zugehörige Konfiguration verwaltet werden. Der Content Repository Browser CRXDE Lite ist nur in Nicht-Produktions-Umgebungen verfügbar. Eine Untergruppe der Web Console-Funktionen, die Entwickler benötigen, insbesondere im Hinblick auf Diagnose und Status, wird über eine neue Entwicklerkonsole bereitgestellt.
Zu den häufigsten Entwickleranforderungen gehört der schnelle Zugriff auf die Protokolldateien der verschiedenen Umgebungen. Bei [!DNL AEM Cloud Service] werden die Protokolldateien der verschiedenen Knoten in den Autoren- und Veröffentlichungsknoten über Cloud Manager zur Verfügung gestellt, entweder in Form von Dateien, die heruntergeladen werden können, oder über APIs. Aufgrund der klaren Trennung von Code und Inhalt können Entwickler ein bestimmtes Verfahren zur Aktualisierung von Inhalten im Rahmen einer Implementierung verwenden. Typische Anwendungsfälle für veränderliche Inhalte sind:
* Standardinhalt, der Teil des Kundenprojekts ist (z. B. Ordner, Vorlagen, Workflows usw.)
* Suchindexdefinitionen
* ACLs und Berechtigungen
* Service-Benutzer und -Benutzergruppen
Richten Sie Ihre Entwicklungsumgebung ein, [konfigurieren Sie Ihre CI/CD Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=de) und erfahren Sie, wie Sie [Ihren Code in der Umgebung bereitstellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=de) können.

## Lokale Entwicklung {#local-development}

Wenn Sie eine [!DNL AEM Forms] as a Cloud Service-Umgebung einrichten und konfigurieren, richten Sie eigene Umgebungen für Entwicklung, Staging und Produktion ein. Richten Sie außerdem eine lokale Entwicklungsumgebung für schnelle Iterationen und Entwicklungsprozesse ein und konfigurieren Sie sie. Sie können das AEM SDK und das [!DNL AEM Forms]-Add-on-Funktionsarchiv herunterladen und einrichten, um eine lokale Entwicklungsumgebung für [!DNL Forms] as a Cloud Service bereitzustellen.  Detaillierte Anweisungen finden Sie unter [Einrichten einer lokalen Entwicklungsumgebung](setup-local-development-environment.md).

## Debugging {#debugging}

AEM as a Cloud Service wird auf einer skalierbaren Self-Service-Cloud-Infrastruktur ausgeführt. AEM-Entwickler müssen dazu in der Lage sein, verschiedene Facetten von AEM as a Cloud Service zu verstehen und zu debuggen, vom Entwickeln und Bereitstellen bis zum Abrufen von Informationen zu AEM-Programmen. Weitere Informationen finden Sie unter [Debugging von AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html?lang=de).
