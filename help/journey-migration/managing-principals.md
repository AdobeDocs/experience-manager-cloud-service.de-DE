---
title: Verwalten von Prinzipalen
description: Verwalten von Prinzipalen für die Migration mithilfe von Admin Console
exl-id: a75598d0-8f59-466b-984e-dfe527388c2a
source-git-commit: a5bec2c05b46f8db55762b7ee1f346f3bb099d24
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 7%

---

# Verwalten von Prinzipalen {#managing-principals}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_managingprincipals"
>title="Verwalten von Prinzipalen"
>abstract="Erfahren Sie, was Sie tun müssen, um Benutzende während oder nach einer Inhaltsmigration zu verwalten"

Bevor Inhalte in die AEM as a Cloud Service-Cloud-Umgebung übertragen werden, können einige Aufgaben für die Admin Console ausgeführt werden.  Sie sind: Benutzer erstellen, Gruppen erstellen und Benutzer Gruppen zuweisen. Diese Benutzer und Gruppen sind in IMS vorhanden, Adobe Identity Management Service, der zur Verwaltung von Benutzern und Gruppen für alle Adobe Cloud-basierten Dienste verwendet wird.

### Erstellen von Gruppen und ihren Benutzern in Admin Console

[Verwenden der Admin Console für AEM Prinzipale](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/ims-support#how-to-set-up) enthält detaillierte Anweisungen zum Erstellen von Benutzern und Gruppen in IMS und zum Hinzufügen der Benutzer zu den Gruppen gleichzeitig oder später.  Das Dokument bietet drei Möglichkeiten zur Erstellung: manuell über die Admin Console, per CSV-Upload über die Admin Console und über ein Tool zur Benutzersynchronisierung.

Mit der manuellen Option können Sie jeweils eine Gruppe oder einen Benutzer erstellen. Beim CSV-Upload können Sie mehrere Benutzer und Gruppen gleichzeitig erstellen und verknüpfen. Mit dem Tool zur Benutzersynchronisierung können Sie einen vorhandenen IDP verwenden, um die IMS-Benutzer und -Gruppen zu erstellen und zu verwalten.

Sobald sich ein Benutzer mit IMS bei AEM anmeldet, wird eine AEM Benutzerdarstellung erstellt.  Darüber hinaus werden für alle IMS-Gruppen, in denen sich der Benutzer befindet, AEM gleichen Gruppen in AEM erstellt.  Diese IMS-erstellten AEM Benutzer und Gruppen werden weiterhin hauptsächlich über die Admin Console verwaltet.

Nach Abschluss der Inhaltsmigration müssen IMS-Gruppen in der Regel über eine zusätzliche Konfiguration verfügen, damit Benutzer auf den migrierten Inhalt zugreifen können.  Siehe [Migrieren von Prinzipalen nach der Migration](/help/journey-migration/managing-principals-after-migration.md)

Weitere Informationen zur Integration und Verwaltung von AEM- und IMS-Benutzern und -Gruppen finden Sie unter [Tutorial, AEM Benutzer, Gruppen und Berechtigungen](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions) .
