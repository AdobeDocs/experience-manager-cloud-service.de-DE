---
title: Zugriff auf Repositorys
description: Erfahren Sie, wie Sie mithilfe der Self-Service-Git-Kontoverwaltung über Cloud Manager auf Ihr Git-Repository zugreifen und es verwalten können.
exl-id: 0c0671a3-e400-46f3-ad86-166a6cfdd44b
source-git-commit: 1b24fa084577f2ba0dc718ee35d12e42ac9d609c
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 85%

---


# Zugriff auf Repositorys {#accessing-repos}

Erfahren Sie, wie Sie mithilfe der Self-Service-Git-Kontoverwaltung über Cloud Manager auf Ihr Git-Repository zugreifen und es verwalten können.

## Verwenden der Self-Service-Repository-Kontoverwaltung {#self-service-repos}

Cloud Manager macht es Ihnen leicht, Ihre Repository-Informationen abzurufen, indem Sie die Schaltfläche **Zugriff auf Repo-Info** verwenden, die sich auf der Pipeline-Karte befindet.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie in der **Programmübersicht** zur Karte **Pipelines** und verwenden Sie die Schaltfläche **Zugriff auf Repo Info**, um auf Ihr Git-Repository zuzugreifen und es zu verwalten.

   ![Schaltfläche „Zugriff auf Repo Info“ auf der Karte „Umgebungen“](/help/implementing/cloud-manager/assets/repos/access-repo1.png)

1. Klicken Sie auf die Schaltfläche **Repo-Info anzeigen**, um ein Dialogfeld mit folgenden Inhalten zu öffnen:

   * Die URL zum Git-Repository von Cloud Manager.
   * Der Git-Benutzername.
   * Das Git-Kennwort, dessen Wert durch Klicken auf die Schaltfläche **Kennwort generieren** angezeigt wird.

   ![Repo-Info-Ansicht](/help/implementing/cloud-manager/assets/repos/access-repo-create.png)

Mithilfe dieser Anmeldeinformationen können Benutzende eine lokale Kopie des Repositorys klonen und Änderungen an diesem lokalen Repository vornehmen und etwaige Code-Änderungen wieder in das remote Code-Repository in Cloud Manager übertragen.

Die Option **Zugriff auf Repo-Info** ist auch auf der Pipeline-Registerkarte **Produktionsfremd** der **Pipeline**-Karte verfügbar. 

![Die Schaltfläche „Zugriff auf Repo-Info“ auf produktionsfremden Registerkarten](/help/implementing/cloud-manager/assets/repos/access-repo-nonprod.png)

>[!NOTE]
>
>Die Option **Zugriff auf Repo-Info** ist für Benutzende mit der Rolle **Entwickler** oder **Bereitstellungs-Manager** sichtbar.

## Sperren eines Zugangskennworts {#revoke-password}

Sie können jederzeit ein Zugangskennwort sperren. Um dies zu tun, bitte [ein Support-Ticket für diese Anfrage erstellen.](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;support-tab=home#support)

Das Ticket wird mit hoher Priorität behandelt und sollte innerhalb eines Tages widerrufen werden.
