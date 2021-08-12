---
title: Zugreifen auf Repositorys
seo-title: Zugreifen auf Repositorys
description: Auf dieser Seite wird beschrieben, wie Sie auf das Git-Repository zugreifen und es verwalten können.
seo-description: Auf dieser Seite erfahren Sie, wie Sie auf Ihr Git-Repository zugreifen und es verwalten.
exl-id: 0c0671a3-e400-46f3-ad86-166a6cfdd44b
source-git-commit: 9898baebfbb43059f2497fa6b4db801eef12a9d0
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 60%

---

# Zugreifen auf Repositorys {#accessing-repos}

Sie können über die Benutzeroberfläche von Cloud Manager mit der Self-Service-Git-Kontoverwaltung auf Ihr Git-Repository zugreifen und es verwalten.

## Verwenden der Kontoverwaltung für Self-Service-Repositorys {#self-service-repos}

Verwenden Sie die Schaltfläche **Zugriff auf Repo Info** in der Cloud Manager-Benutzeroberfläche, insbesondere auf der Pipeline-Karte.

1. Navigieren Sie von Ihrer Seite **Programmübersicht** zur Karte **Pipelines** .

1. Sie sehen die Option **Zugriff auf Repo Info** , um auf Ihr Git-Repository zuzugreifen und es zu verwalten.

   ![](assets/repos/access-repo1.png)

   Wenn Sie außerdem die Pipeline-Registerkarte **Nicht-Produktion** auswählen, wird auch dort die Option **Zugriff auf Repo Info** angezeigt.

   ![](assets/repos/access-repo-nonprod.png)

   >[!NOTE]
   >Die Option **Zugriff auf Repo Info** ist für Benutzer in der Rolle &quot;Entwickler&quot;oder &quot;Bereitstellungs-Manager&quot;sichtbar. Wenn Sie auf diese Schaltfläche klicken, wird ein Dialogfeld geöffnet, in dem der Benutzer die URL zum Cloud Manager-Git-Repository sowie den Benutzernamen und das Kennwort findet.

   ![](assets/repos/access-repo-create.png)

   Wichtige Aspekte bei der Verwaltung Ihres Git-Repositorys in Cloud Manager:

   * **URL**: Die Repository-URL
   * **Benutzername**: Der Benutzername
   * **Kennwort**: Der Wert, der angezeigt wird, wenn auf die Schaltfläche **Kennwort generieren** geklickt wird.


      >[!NOTE]
      >Ein Benutzer kann eine Kopie seines Codes auschecken und Änderungen am lokalen Code-Repository vornehmen. Sobald die Änderungen vorgenommen wurden, kann der Benutzer die Code-Änderungen wieder in das Remote-Code-Repository in Cloud Manager übertragen.
