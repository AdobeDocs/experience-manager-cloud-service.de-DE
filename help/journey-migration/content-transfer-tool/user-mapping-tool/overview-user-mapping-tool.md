---
title: Überblick über das Tool für die Benutzerzuordnung
description: Überblick über das Tool für die Benutzerzuordnung
exl-id: 17ed5721-093e-4491-b8c4-3dadcaa6598b
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 100%

---

# Überblick über das Tool für die Benutzerzuordnung {#overview-user-mapping-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_usermapping"
>title="User Mapping Tool"
>abstract="Mit dem Content Transfer Tool können Sie Anwender und Gruppen aus Ihrem vorhandenen AEM-System in AEM as a Cloud Service verschieben. Vorhandene Anwender und Gruppen müssen ihren IMS-IDs zugeordnet werden, um doppelte Anwender und Gruppen in der Cloud Service-Autoreninstanz zu vermeiden."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=de#important-considerations" text="Wichtige Überlegungen zur Verwendung des User Mapping Tools"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=de#using-user-mapping-tool" text="Verwenden des User Mapping Tools"

## Einführung {#introduction}

Im Rahmen der Umstellung auf Adobe Experience Manager (AEM) as a Cloud Service müssen Sie Benutzer und Gruppen aus Ihrem bestehenden AEM-System in AEM as a Cloud Service überführen. Verwenden Sie hierzu das Content Transfer Tool.

Eine wichtige Änderung an AEM as a Cloud Service ist die vollständig integrierte Verwendung von Adobe IDs für den Zugriff auf die Autorenebene.  Dies erfordert die Verwendung der [Adobe Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) zum Verwalten von Benutzern und Benutzergruppen. Die Benutzerprofilinformationen werden im Adobe Identity Management System (IMS) zentralisiert, das eine einmalige Anmeldung für alle Adobe Cloud-Programme ermöglicht. Weitere Informationen finden Sie unter [Identity Management](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=de#identity-management). Aufgrund dieser Änderung müssen bestehende Benutzer und Gruppen ihren IMS-IDs zugeordnet werden, um doppelte Benutzer und Gruppen in der Cloud Service-Autoreninstanz zu vermeiden.

## Benutzerzuordnungs-Tool {#mapping-tool}

Das Content Transfer Tool (ohne Benutzerzuordnung) migriert alle Benutzer und Gruppen, die mit den migrierten Inhalten verknüpft sind. Das User Mapping Tool ist Teil des Content Transfer Tools und soll nur dazu dienen, die Benutzer und Gruppen so zu ändern, dass sie von IMS, der Single Sign-On-Funktion, die von AEM as a Cloud Service verwendet wird, korrekt erkannt werden können. Sobald diese Änderungen vorgenommen wurden, migriert das Content Transfer Tool die Benutzer und Gruppen des angegebenen Inhalts wie gewohnt.

### Wie geht es weiter? {#whats-next}

Nun, da Sie das Tool für die Benutzerzuordnung kennengelernt haben, können Sie vor der Verwendung des Tools für die Benutzerzuordnung jetzt wichtige Überlegungen und Ausnahmefälle durchgehen. Weitere Einzelheiten finden Sie unter [Wichtige Überlegungen zum Tool für die Benutzerzuordnung](/help/journey-migration/content-transfer-tool/user-mapping-tool/considerations-user-mapping-tool.md).
