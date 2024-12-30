---
title: Verwalten von Prinzipalen
description: Verwalten von Prinzipalen für die Migration mithilfe der Admin Console
exl-id: a75598d0-8f59-466b-984e-dfe527388c2a
source-git-commit: a5bec2c05b46f8db55762b7ee1f346f3bb099d24
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 100%

---

# Verwalten von Prinzipalen {#managing-principals}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_managingprincipals"
>title="Verwalten von Prinzipalen"
>abstract="Erfahren Sie, was Sie tun müssen, um Benutzende während oder nach einer Inhaltsmigration zu verwalten"

Bevor Inhalte in die Cloud-Umgebung von AEM as a Cloud Service übertragen werden, können einige Aufgaben in der Admin Console ausgeführt werden.  Diese Aufgaben sind: Benutzende erstellen, Gruppen erstellen und Benutzende zu Gruppen zuweisen. Diese Benutzenden und Gruppen sind im IMS (Adobe Identity Management Service) vorhanden, der zur Verwaltung von Benutzenden und Gruppen für alle Adobe Cloud-basierten Dienste verwendet wird.

### Erstellen von Gruppen und ihren Benutzenden in der Admin Console

[Verwenden der Admin Console für AEM-Prinzipale](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/security/ims-support#how-to-set-up) enthält detaillierte Anweisungen zum Erstellen von Benutzenden und Gruppen im IMS und dazu, wie gleichzeitig oder später Benutzende zu den Gruppen hinzugefügt werden.  Das Dokument umfasst drei Möglichkeiten zur Erstellung: manuell über die Admin Console, per CSV-Upload über die Admin Console und über ein Tool zur Benutzersynchronisierung.

Mit der manuellen Option können Sie eine Gruppe, eine Benutzerin oder einen Benutzer jeweils einzeln erstellen. Beim CSV-Upload können Sie mehrere Benutzende und Gruppen gleichzeitig erstellen und verknüpfen. Mit dem Tool zur Benutzersynchronisierung können Sie einen vorhandenen IDP verwenden, um die Benutzenden und Gruppen im IMS zu erstellen und zu verwalten.

Sobald sich eine Person mit dem IMS bei AEM anmeldet, wird eine AEM-Benutzerdarstellung erstellt.  Darüber hinaus werden für alle IMS-Gruppen, denen die Person angehört, äquivalente AEM-Gruppen in AEM erstellt.  Diese vom IMS erstellten AEM-Benutzenden und -Gruppen werden weiterhin hauptsächlich über die Admin Console verwaltet.

Nach Abschluss der Inhaltsmigration müssen IMS-Gruppen in der Regel über eine zusätzliche Konfiguration verfügen, damit Benutzende auf die migrierten Inhalte zugreifen können.  Weitere Informationen finden Sie unter [Migrieren von Prinzipalen nach der Migration](/help/journey-migration/managing-principals-after-migration.md)

Außerdem finden Sie unter [Tutorial, AEM-Benutzende, Gruppen und Berechtigungen](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions) weitere Informationen zur Integration und Verwaltung von AEM- und IMS-Benutzenden und -Gruppen.
