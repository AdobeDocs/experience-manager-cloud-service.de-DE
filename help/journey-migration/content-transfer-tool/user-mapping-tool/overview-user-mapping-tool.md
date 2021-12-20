---
title: Überblick über das Tool für die Benutzerzuordnung
description: Überblick über das Tool für die Benutzerzuordnung
source-git-commit: bcbf4e4ba1330bef9f2c8c473419903e40ac0e58
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 85%

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

Nachdem Sie das Tool für die Benutzerzuordnung kennengelernt haben, können Sie jetzt wichtige Überlegungen und Ausnahmefälle vor der Verwendung des Tools für die Benutzerzuordnung überprüfen. Siehe [Wichtige Überlegungen zum Benutzerzuordnungs-Tool](/help/journey-migration/content-transfer-tool/user-mapping-tool/considerations-user-mapping-tool.md) für weitere Details.