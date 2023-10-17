---
title: Bearbeiten von Programmen
description: Erfahren Sie, wie Sie Ihre Produktions- und Sandbox-Programme bearbeiten, um ihre Optionen nach der Erstellung anzupassen.
exl-id: 819e4a6e-f77a-4594-a402-a300dcbdf510
source-git-commit: 97a6a7865f696f4d61a1fb4e25619caac7b68b51
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 50%

---

# Bearbeiten von Programmen {#editing-programs}

Benutzer mit den erforderlichen Berechtigungen können [in Ihrer Organisation erstellte Produktionsprogramme](creating-production-programs.md) und [Sandbox-Programme, die in Ihrer Organisation erstellt wurden.](creating-sandbox-programs.md) Durch die Bearbeitung eines Programms haben Sie folgende Möglichkeiten:

* Fügen Sie Sites-Lösungen zu einem vorhandenen Programm mit Assets hinzu und umgekehrt.
* Entfernen von Sites oder Assets aus einem vorhandenen Programm, das sowohl Sites als auch Assets umfasst.
* Fügen Sie einem vorhandenen Programm oder einem neuen Programm eine zweite nicht verwendete Lösungsberechtigung hinzu.
* Löschen von Sandbox-Programmen.

## Berechtigungen {#permissions}

Sie müssen Mitglied der Rolle **Geschäftsinhaber** sein, um Programme bearbeiten oder Sandbox-Programme löschen zu können.

## Bearbeiten von Programmen {#editing}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, das Sie bearbeiten möchten, um dessen Details anzuzeigen.

1. Klicken Sie oben links auf der Seite auf den Namen Ihres Programms und wählen Sie **Programm bearbeiten**.

   ![Option „Programm bearbeiten“](assets/edit-program-overview.png)

1. Die Seite **Programm bearbeiten** wird geöffnet. Wählen Sie die Registerkarte **Allgemein** aus, um den Programmnamen und die Beschreibung zu bearbeiten.

   * Für ein Programm muss mindestens eine Lösung ausgewählt sein.

   ![Registerkarte „Allgemein“](assets/edit-program-prod1.png)

1. Wählen Sie die Registerkarte **Lösungen und Add-ons** aus, um die Lösungen für das Programm zu ändern.

   ![Lösungen auswählen](assets/edit-prg.png)

1. Klicken Sie auf den Pfeil vor dem Lösungsnamen, um optionale Add-ons anzuzeigen, z. B. die **Handel** Add-On-Option unter **Sites**.

   ![Add-ons bearbeiten](assets/edit-program-add-on.png)

1. Auf der Registerkarte **Einstellungen für die Live-Schaltung** können Sie den geplanten Tag der Veröffentlichung für das Programm ändern.

   ![Live-Schaltungs-Einstellungen bearbeiten](assets/edit-program-go-live.png)

   * Dieses Datum ist nur zur informativen Verwendung bestimmt. Dadurch wird das Widget Go Live auf der Programmübersichtsseite Trigger. Im Gegenzug bietet es produktinterne Links zur as a Cloud Service Best-Practice-Dokumentation von Adobe Experience Manager (AEM), um sie an Ihre Journey anzupassen, was zu einem erfolgreichen Go Live-Erlebnis führt.
   * Diese Registerkarte ist nicht für Sandbox-Programme verfügbar.

1. Klicks **Aktualisieren** , um Ihre Änderungen am Programm zu speichern.

Jedes Mal, wenn ein Programm bearbeitet wird, einschließlich Hinzufügen oder Entfernen einer Lösung oder eines Add-ons, werden diese Änderungen nach der nächsten Bereitstellung wirksam.

Wenn für Ihr Produktionsprogramm die erweiterte Sicherheitsoption aktiviert war, ist die zusätzliche Registerkarte **Erweiterte Sicherheit** im Fenster **Programm bearbeiten** verfügbar, um zu bestätigen, dass diese Funktion für das Programm aktiv ist.

![Erweiterte Sicherheit für ein Programm aktiv](assets/edit-program-enhanced.png)

Sie können diese Einstellung nicht mehr bearbeiten, nachdem das Programm erstellt wurde. Weitere Informationen zur erweiterten Sicherheitsoption finden Sie unter [Erstellen von Produktionsprogrammen](creating-production-programs.md).

## Löschen von Sandbox-Programmen {#delete-sandbox-program}

Durch das Löschen eines Sandbox-Programms werden alle damit verbundenen Umgebungen und Pipelines entfernt.

>[!TIP]
>
>Benutzer mit den Rollen **Geschäftsinhaber** oder **Bereitstellungs-Manager** können alternativ ihre Produktions- und Staging-Umgebungen anstelle des gesamten Sandbox-Programms löschen.

Gehen Sie wie folgt vor, um ein Sandbox-Programm zu löschen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, das Sie bearbeiten möchten, um dessen Details anzuzeigen.

1. Klicken Sie links oben auf der Seite auf den Namen Ihres Programms und wählen Sie **Programm löschen**.

   ![Option „Programm löschen“](assets/delete-sandbox1.png)

Alternativ können Sie auf der Übersichtsseite von Cloud Manager auf der Karte Ihres Programms auf den Butten mit Auslassungspunkten klicken und anschließend auf **Programm löschen**.

![Sandbox aus Programmkarte löschen](assets/delete-sandbox2.png)

>[!NOTE]
>
>Es können nur Sandbox-Programme gelöscht werden. Produktionsprogramme können nicht gelöscht werden.
