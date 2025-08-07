---
title: Konfigurieren einer Edge Delivery-Site zur Verwendung eines externen Git-Repositorys
description: Erfahren Sie, wie Sie eine Edge Delivery-Site mit einem privaten oder Unternehmens-Git-Repository verknüpfen.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 239ee3021057dd108d18ab2d7729680692223403
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 9%

---


# Konfigurieren einer Edge Delivery-Site zur Verwendung eines externen Git-Repositorys

Sie können Ihre Edge Delivery-Site so konfigurieren, dass Code aus jedem privaten Git-Repository abgerufen wird, das bereits in Cloud Manager integriert ist.

**Unterstützte Git-Anbieter**

| Unterstützungsebene | Anbieter | Anmerkungen |
| --- | --- | --- |
| Allgemeine Verfügbarkeit | ・ GitHub Enterprise (selbst gehostete Version)<br>・ Bitbucket (Cloud-Version)<br>・ GitLab (Cloud- und selbst gehostete Version) | Verbindung ohne Aktivierungsanfragen herstellen |
| Alpha-Programm | Azure DevOps (Cloud-Version) | [Zugriff anfordern](mailto:grp-cloudmanager_byog@adobe.com) |
| Beta-Programm | Von Adobe gehostetes Repository (in Cloud Manager erstellt) | [Zugriff anfordern](mailto:grp-cloudmanager_byog@adobe.com) |

**So konfigurieren Sie eine Edge Delivery-Site für die Verwendung eines externen Git-Repositorys:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.

1. Wählen Sie in der **[Meine](/help/implementing/cloud-manager/navigation.md#my-programs)**&quot; das Programm mit konfiguriertem Edge Delivery Services aus, für das Sie eine Edge Delivery-Site für die Verwendung eines externen Git-Repo konfigurieren möchten.

1. Klicken Sie in der linken Leiste unter **Programm** auf **![Übersichtssymbol](/help/implementing/cloud-manager/edge-delivery/assets/overview.svg) Übersicht**.

1. Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Edge Delivery**. 

1. Klicken Sie in der Tabelle **Edge Delivery Sites** auf ![Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) am Ende einer Zeile, deren Site Sie für die Verwendung eines externen Repositorys konfigurieren möchten, und klicken Sie dann auf **Eigenes Git**.

1. Wählen Sie im Dialogfeld Eigenes Git einbringen in der Dropdown-Liste **Repository-Name** ein Git-Repository mit `READY` Status aus und klicken Sie dann auf **Bestätigen**.

   Cloud Manager gibt ein einmaliges Geheimnis-Token zurück. Wenn Sie die Site neu konfigurieren, generiert Cloud Manager ein neues Geheim-Token.

1. Kopieren Sie das Token und fügen Sie es der Site-Konfiguration in **helix-admin** hinzu, wie im [BYO Git-Handbuch](https://www.aem.live/developer/byo-git) beschrieben.

1. Zurück in Cloud Manager klicken Sie auf ![Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)Symbol) am Ende einer Zeile, deren Site Sie gerade für die Verwendung eines externen Repositorys konfiguriert haben, und klicken Sie dann auf **Code synchronisieren**.

1. Wählen Sie die zu synchronisierende Verzweigung aus und klicken Sie auf **Synchronisieren**.

Jeder Commit auf einer Verzweigung Trigger jetzt eine automatische Synchronisierung. Verwenden Sie **Sync** Code erneut, wenn eine vollständige manuelle Synchronisierung erforderlich ist.

