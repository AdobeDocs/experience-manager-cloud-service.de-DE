---
title: Erstellen von Sandbox-Programmen
description: Erfahren Sie, wie Sie mit Cloud Manager Ihr eigenes Sandbox-Programm für Schulungs-, Demo-, POC- oder andere produktionsfremde Zwecke erstellen.
exl-id: 10011392-3059-4bb0-88db-0af1d390742e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 17306cf0877513d1412ffba311bd5d601edec062
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 15%

---

# Sandbox-Programme erstellen {#create-sandbox-program}

Sandbox-Programme werden normalerweise für Schulungen, laufende Demos, Aktivierungen, POCs oder Dokumentationen erstellt und sind nicht für Live-Traffic vorgesehen. Siehe [Einführung in Sandbox-Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md).

Weitere Informationen zu Programmtypen finden Sie im Dokument [Grundlegendes zu Programm- und Programmtypen](program-types.md) .

## Sandbox-Programm erstellen {#create}

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** in der rechten oberen Ecke auf **Programm hinzufügen**.

   ![Cloud Manager-Landingpage](assets/log-in.png)

1. Geben Sie im Assistenten *Erstellen Ihres Programms* im Textfeld **Programmname** den gewünschten Namen für das Programm ein.

1. Wählen Sie unter **Programmziel** die Option **`Set up a sandbox`** aus.

   ![Erstellen von Programmtypen](assets/create-sandbox.png)

1. (Optional) Führen Sie in der rechten unteren Ecke des Assistenten-Dialogfelds einen der folgenden Schritte aus:

   * Ziehen Sie eine Bilddatei per Drag-and-Drop auf das Ziel **Programmbild hinzufügen** .
   * Klicken Sie auf **Programmbild hinzufügen** und wählen Sie dann ein Bild aus einem Dateibrowser aus.
   * Klicken Sie auf das Papierkorbsymbol, um ein hinzugefügtes Bild zu löschen.

1. Klicken Sie auf **Weiter**.

1. Wählen Sie im Listenfeld **Lösungen und Add-ons** eine oder mehrere Lösungen aus, die in das Programm aufgenommen werden sollen.

   * Klicken Sie auf den Pfeil links neben dem Lösungsnamen, um alle verfügbaren optionalen Add-ons anzuzeigen, die Sie in eine ausgewählte Lösung aufnehmen möchten.
   * Die Lösungen **Sites**, **Assets** und **Edge Deliver Services** sind beim Erstellen eines Sandbox-Programms standardmäßig immer ausgewählt. Sie können die Auswahl nicht aufheben.

   ![Lösungen und Add-ons für eine Sandbox auswählen](assets/sandbox-solutions-add-ons.png)

1. Klicken Sie auf **Erstellen**. Cloud Manager erstellt Ihr Sandbox-Programm und zeigt es zur Auswahl auf der Landingpage an.

![Erstellen von Sandboxes von der Übersichtsseite](assets/sandbox-setup.png)

## Sandbox-Zugriff {#access}

Nachdem ein neues Sandbox-Programm erstellt wurde, können Sie die Details Ihrer Sandbox-Einrichtung anzeigen und auf die Umgebung zugreifen, indem Sie die Seite mit der Programmübersicht aufrufen.

1. Klicken Sie auf der Cloud Manager-Landingpage im erstellten Sandbox-Programm auf die Suchschaltfläche .

   ![Zugriff auf die Programmübersicht](assets/program-overview-sandbox.png)

1. Wenn der Schritt zur Projekterstellung abgeschlossen ist, können Sie auf den Link **Repo Info (Repo Info) aufrufen** klicken, um Ihr Git-Repository verwenden zu können.

   ![Konfiguration von Programmen](assets/create-program4.png)

   >[!TIP]
   >
   >Weitere Informationen zum Zugriff auf und zur Verwaltung Ihres Git-Repositorys finden Sie unter [Zugriff auf Git](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

1. Nachdem die Entwicklungsumgebung erstellt wurde, können Sie auf **Zugriff AEM** klicken und sich bei AEM anmelden.

   ![Link „Zugriff auf AEM“](assets/create-program5.png)

1. Wenn die Nicht-Produktions-Pipeline, die für die Entwicklung bereitgestellt wird, abgeschlossen ist, führt der Assistent im Aktionsaufruf Sie dazu, entweder auf die AEM Entwicklungsumgebung zuzugreifen oder Code in der Entwicklungsumgebung bereitzustellen.

   ![Bereitstellen einer Sandbox](assets/create-program-setup-deploy.png)

>[!TIP]
>
>Weitere Informationen zum Navigieren in Cloud Manager und zum Verständnis der Konsole **Meine Programme** finden Sie unter [Navigieren in der Cloud Manager-Benutzeroberfläche](/help/implementing/cloud-manager/navigation.md) .
