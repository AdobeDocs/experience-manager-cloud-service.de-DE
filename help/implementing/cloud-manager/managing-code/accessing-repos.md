---
title: Repository-Zugriffsinformationen
description: Erfahren Sie, wie Sie mithilfe der Self-Service-Git-Kontoverwaltung über Cloud Manager auf Ihre von Adobe verwalteten Git-Repositorys zugreifen und diese verwalten können.
exl-id: 0c0671a3-e400-46f3-ad86-166a6cfdd44b
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 533fa72b7610f671a24461073112b7fb798ce166
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 44%

---


# Repository-Zugriffsinformationen {#accessing-repos}

Erfahren Sie, wie Sie mithilfe der Self-Service-Git-Kontoverwaltung über Cloud Manager auf Ihre von Adobe verwalteten Git-Repositorys zugreifen und diese verwalten können.

## Zugriff auf Repository-Informationen über die Übersichtsseite {#overview-page}

Cloud Manager erleichtert das Abrufen Ihrer Repository-Zugriffsinformationen für von Adobe verwaltete Repositorys mithilfe von **Access Repo Info** über die Karte **Pipelines** .

Im Dialogfeld **Repository Info** können Sie die folgenden Zugriffsinformationen für von Adobe verwaltete Repositorys anzeigen:

* Den Git-Benutzernamen.
* Das Git-Kennwort.
* Die URL zum Git-Repository von Cloud Manager.
* Vordefinierte Git-Befehle zum schnellen Hinzufügen einer Remote-Verbindung zu Ihrem Git-Repository und Push-Code.

![Fenster „Repository-Informationen“](assets/repository-info.png)

Zugriffsinformationen über [private Repositorys](private-repositories.md) sind in Cloud Manager nicht verfügbar.

Die Funktion **Zugriff auf Repo Info** ist für Benutzer mit den Rollen **Entwickler** oder **Bereitstellungs-Manager** sichtbar.

**So greifen Sie auf Repository-Informationen von der Seite &quot;Übersicht&quot;zu:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie auf der Seite **Programmübersicht** unter der Karte **Pipelines** auf **Auf Repo Info zugreifen**.

   ![Zugriff auf Repo Info auf Pipelines-Karte](assets/pipelines-card.png)

1. Um auf das Kennwort zugreifen zu können, muss ein neues Kennwort generiert werden. Klicken Sie im Dialogfeld &quot;Repository Info&quot;auf **`Generate password`**.

1. Klicken Sie im Bestätigungsdialogfeld auf **`Generate password`**.

   ![Kennwortgenerierung bestätigen](assets/confirm-generated-password.png)

1. Klicken Sie rechts neben dem Feld **Kennwort** auf das Symbol ![Kopieren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) , um das Kennwort in die Zwischenablage zu kopieren.

   * Durch das Generieren eines Kennworts wird das vorherige Kennwort ungültig.
   * Cloud Manager speichert das Kennwort nicht. Es liegt in Ihrer Verantwortung, das Kennwort sicher zu speichern.
   * Da Cloud Manager das Kennwort nicht speichert, müssen Sie ein neues Kennwort neu generieren, wenn Sie das Kennwort verlieren.

   ![Kennwort im Dialogfeld &quot;Repository Info&quot;kopieren](/help/implementing/cloud-manager/managing-code/assets/repository-copy-password.png)

Mithilfe dieser Anmeldeinformationen können Sie eine lokale Kopie des Repositorys klonen, Änderungen an diesem lokalen Repository vornehmen und etwaige Code-Änderungen wieder in das Remote-Code-Repository in Cloud Manager übertragen.

## Zugriff auf Repository-Informationen über die Seite &quot;Repositorys&quot; {#repositories-window}

Die Funktion **Zugriff auf Repo Info** ist auch auf der Seite [**Repositorys**](managing-repositories.md) verfügbar. Es werden dieselben Informationen zum Zugriff auf von Adobe verwaltete Repositorys angezeigt.

## Widerrufen eines Zugangskennworts {#revoke-password}

Sie können jederzeit ein Zugangskennwort sperren.

Erstellen Sie dazu ein Support-Ticket für diese Anfrage](https://experienceleague.adobe.com/?lang=de?support-solution=Experience+Manager&amp;support-tab=home#support). [ Das Ticket wird mit hoher Priorität behandelt und normalerweise innerhalb eines Tages widerrufen.
