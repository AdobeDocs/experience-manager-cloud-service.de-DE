---
title: Überblick über das Tool für die Benutzerzuordnung (veraltete Version)
description: Überblick über das Tool für die Benutzerzuordnung (Veraltete Version)
exl-id: 17ed5721-093e-4491-b8c4-3dadcaa6598b
hide: true
hidefromtoc: true
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 28%

---

# Überblick über das Tool für die Benutzerzuordnung (veraltete Version) {#overview-user-mapping-tool}

>[!INFO]
>
>Diese Dokumentation bezieht sich auf eine veraltete Version des Tools. Weitere Informationen zur neuesten Version finden Sie unter [Benutzerzuordnung und Hauptmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md).

<!-- Alexandru: drafting this for now

NOTE: "LEGACY" for user mapping includes everything before (i.e. not including) 2.0.16 of CTT.

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="User Mapping Tool"
>abstract="The Content Transfer Tool helps you move users and groups from your existing AEM system to AEM as a Cloud Service. Existing users and groups need to be mapped to their IMS IDs to avoid duplicate users and groups on the Cloud Service author instance."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#important-considerations" text="Important Considerations for using User Mapping Tool"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#using-user-mapping-tool" text="Using User Mapping Tool"

-->

## Einführung {#introduction}

Im Rahmen der Umstellung auf Adobe Experience Manager (AEM) as a Cloud Service müssen Sie Benutzer und Gruppen von Ihrem bestehenden AEM auf AEM as a Cloud Service verschieben. Diese Migration wird vom Content Transfer Tool durchgeführt.

Eine wichtige Änderung an AEM as a Cloud Service ist die vollständig integrierte Verwendung von Adobe IDs für den Zugriff auf die Autorenebene. Diese Integration erfordert die Verwendung der [Adobe Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) für die Verwaltung von Benutzern und Benutzergruppen. Die Benutzerprofilinformationen werden im Adobe Identity Management System (IMS) zentralisiert, das Single Sign-On für alle Adobe Cloud-Anwendungen bietet. Weitere Informationen finden Sie unter [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html?lang=en#identity-management). Aufgrund dieser Änderung müssen bestehende Benutzer und Gruppen ihren IMS-IDs zugeordnet werden, um doppelte Benutzer und Gruppen in der Autoreninstanz des Cloud Service zu vermeiden.

## User Mapping Tool {#mapping-tool}

Das Content Transfer Tool (ohne Benutzerzuordnung) migriert alle Benutzer und Gruppen, die mit dem migrierten Inhalt verknüpft sind. Das Tool zur Benutzerzuordnung ist Teil des Content Transfer Tool. Der einzige Zweck besteht darin, die Benutzer so zu bearbeiten, dass sie von IMS, der von AEM as a Cloud Service verwendeten Single Sign-On-Funktion, korrekt erkannt werden. Nachdem diese Änderungen vorgenommen wurden, migriert das Content Transfer Tool die Benutzer und Gruppen des angegebenen Inhalts wie gewohnt.

### Wie geht es weiter {#whats-next}

Nun, da Sie das Tool für die Benutzerzuordnung kennengelernt haben, können Sie vor der Verwendung des Tools für die Benutzerzuordnung jetzt wichtige Überlegungen und Ausnahmefälle durchgehen. Weitere Einzelheiten finden Sie unter [Wichtige Überlegungen zum Tool für die Benutzerzuordnung](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).
