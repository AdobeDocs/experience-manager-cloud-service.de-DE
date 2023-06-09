---
title: Zugriff auf Repositorys
description: Erfahren Sie, wie Sie mithilfe der Self-Service-Git-Kontoverwaltung über Cloud Manager auf Ihr Git-Repository zugreifen und es verwalten können.
exl-id: 0c0671a3-e400-46f3-ad86-166a6cfdd44b
source-git-commit: 9ec45753f56d0576e75f148ca0165c0ccd621f23
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 54%

---

# Zugriff auf Repositorys {#accessing-repos}

Erfahren Sie, wie Sie mithilfe der Self-Service-Git-Kontoverwaltung über Cloud Manager auf Ihr Git-Repository zugreifen und es verwalten können.

## Verwenden der Self-Service-Repository-Kontoverwaltung {#self-service-repos}

Cloud Manager erleichtert das Abrufen Ihrer Repository-Informationen mithilfe der **Zugriff auf Repo Info** auf der Pipeline-Karte verfügbar.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie in der **Programmübersicht** zur Karte **Pipelines** und verwenden Sie die Schaltfläche **Zugriff auf Repo Info**, um auf Ihr Git-Repository zuzugreifen und es zu verwalten.

   ![Schaltfläche „Zugriff auf Repo Info“ auf der Karte „Umgebungen“](/help/implementing/cloud-manager/assets/repos/access-repo1.png)

1. Klicken Sie auf die Schaltfläche **Repo Info anzeigen**, um ein Dialogfeld mit folgenden Inhalten zu öffnen:

   * Die URL zum Git-Repository von Cloud Manager.
   * Der Git-Benutzername.
   * Das Git-Kennwort, dessen Wert durch Klicken auf die Schaltfläche **Kennwort generieren** angezeigt wird.

   ![Repo Info View](/help/implementing/cloud-manager/assets/repos/access-repo-create.png)

Mithilfe dieser Anmeldeinformationen können Benutzende eine lokale Kopie des Repositorys klonen und Änderungen an diesem lokalen Repository vornehmen und etwaige Code-Änderungen wieder in das remote Code-Repository in Cloud Manager übertragen.

Die **Zugriff auf Repo Info** ist auch auf der **Nicht Produktion** Pipeline-Registerkarte der **Pipelines** Karte.

![Schaltfläche &quot;Repo Info&quot;auf Nicht-Produktions-Registerkarte aufrufen](/help/implementing/cloud-manager/assets/repos/access-repo-nonprod.png)

>[!NOTE]
>
>Die **Zugriff auf Repo Info** -Option für Benutzer mit **Entwickler** oder **Bereitstellungsmanager** Rollen.
