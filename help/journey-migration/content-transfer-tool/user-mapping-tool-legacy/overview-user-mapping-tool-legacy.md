---
title: Überblick über das Tool für die Benutzerzuordnung (veraltete Version)
description: Überblick über das Tool für die Benutzerzuordnung (veraltete Version)
exl-id: 17ed5721-093e-4491-b8c4-3dadcaa6598b
hide: true
hidefromtoc: true
feature: Migration
role: Admin
source-git-commit: e5fd1b351047213adbb83ef1d1722352958ce823
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 100%

---


# Überblick über das Tool für die Benutzerzuordnung (veraltete Version) {#overview-user-mapping-tool}

>[!INFO]
>
>Diese Dokumentation bezieht sich auf eine veraltete Version des Tools. Weitere Informationen zur neuesten Version finden Sie unter [Gruppenmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/group-migration.md).

<!-- Alexandru: drafting this for now

NOTE: "LEGACY" for user mapping includes everything before (that is, not including) 2.0.16 of CTT.

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="User Mapping Tool"
>abstract="The Content Transfer Tool helps you move users and groups from your existing AEM system to AEM as a Cloud Service. Existing users and groups need to be mapped to their IMS IDs to avoid duplicate users and groups on the Cloud Service author instance."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=de#important-considerations" text="Important Considerations for using User Mapping Tool"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=de#using-user-mapping-tool" text="Using User Mapping Tool"

-->

## Einführung {#introduction}

Im Rahmen der Übergangs zu Adobe Experience Manager (AEM) as a Cloud Service müssen Sie Benutzende und Gruppen aus Ihrem vorhandenen AEM-System nach AEM as a Cloud Service übertragen. Diese Migration erfolgt über das Content Transfer Tool.

Eine wichtige Änderung an AEM as a Cloud Service ist die vollständig integrierte Verwendung von Adobe IDs für den Zugriff auf die Authoring-Ebene. Diese Integration setzt voraus, dass die [Adobe Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) zum Verwalten von Benutzenden und Benutzergruppen verwendet wird. Die Benutzerprofilinformationen sind im Adobe Identity Management System (IMS) zentralisiert, das Single Sign-on über alle Adobe-Cloud-Anwendungen hinweg bereitstellt. Weitere Informationen finden Sie unter [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/what-is-new-and-different.html?lang=de#identity-management). Aufgrund dieser Änderung müssen vorhandene Benutzende und Gruppen ihren IMS-IDs zugeordnet werden, um doppelte Benutzende und Gruppen in der Authoring-Instanz in Cloud Service zu vermeiden.

## Tool für die Benutzerzuordnung {#mapping-tool}

Das Content Transfer Tool (ohne Benutzerzuordnung) migriert alle Benutzenden und Gruppen, die mit den migrierten Inhalten verknüpft sind. Das Tool für die Benutzerzuordnung ist Teil des Content Transfer Tools. Es dient einzig dazu, die Benutzenden und Gruppen so zu bearbeiten, dass sie von IMS, der von AEM as a Cloud Service verwendeten Single-Sign-on-Funktion, korrekt erkannt werden können. Sobald diese Änderungen vorgenommen wurden, migriert das Content Transfer Tool die mit dem angegebenen Inhalt verknüpften Benutzenden und Gruppen wie gewohnt.

### Wie geht es weiter {#whats-next}

Nun, da Sie das Tool für die Benutzerzuordnung kennengelernt haben, können Sie vor der Verwendung des Tools für die Benutzerzuordnung jetzt wichtige Überlegungen und Ausnahmefälle durchgehen. Weitere Einzelheiten finden Sie unter [Wichtige Überlegungen zum Tool für die Benutzerzuordnung](/help/journey-migration/content-transfer-tool/user-mapping-tool-legacy/considerations-user-mapping-tool-legacy.md).
