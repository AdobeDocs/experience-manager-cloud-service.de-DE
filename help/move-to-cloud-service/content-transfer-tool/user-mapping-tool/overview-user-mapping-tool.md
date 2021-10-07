---
title: Überblick über das Tool für die Benutzerzuordnung
description: Überblick über das Tool für die Benutzerzuordnung
source-git-commit: 60e67e92f4f1ecaaf12c58f16f4324868d223934
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 63%

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

Das Content Transfer Tool (ohne Benutzerzuordnung) migriert alle Benutzer und Gruppen, die mit dem migrierten Inhalt verknüpft sind. Das Tool für die Benutzerzuordnung ist Teil des Content Transfer-Tools und soll nur dazu dienen, die Benutzer und Gruppen so zu ändern, dass sie von IMS, der von AEM as a Cloud Service Single-Sign-On-Funktion, richtig erkannt werden. Sobald diese Änderungen vorgenommen wurden, migriert das Content Transfer Tool die Benutzer und Gruppen des angegebenen Inhalts wie gewohnt.

### Nächste Schritte {#whats-next}

Nachdem Sie das Tool für die Benutzerzuordnung kennengelernt haben, können Sie jetzt wichtige Überlegungen und Ausnahmefälle vor der Verwendung des Tools für die Benutzerzuordnung überprüfen. Weitere Informationen finden Sie unter [Wichtige Überlegungen zum Benutzerzuordnungs-Tool](/help/move-to-cloud-service/content-transfer-tool/user-mapping-tool/considerations-user-mapping-tool.md) .