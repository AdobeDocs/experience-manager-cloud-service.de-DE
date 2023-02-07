---
title: Bearbeiten von Programmen
description: Erfahren Sie, wie Sie Ihre Produktions- und Sandbox-Programme bearbeiten, um ihre Optionen nach der Erstellung anzupassen.
exl-id: 819e4a6e-f77a-4594-a402-a300dcbdf510
source-git-commit: d8815a17601f475267b50a6a527246f1433ed7eb
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 87%

---

# Bearbeiten von Programmen {#editing-programs}

Benutzer mit den erforderlichen Berechtigungen können [in Ihrer Organisation erstellte Produktionsprogramme](creating-production-programs.md) sowie [Sandbox-Programme, die in Ihrer Organisation erstellt wurden, bearbeiten.](creating-sandbox-programs.md) Durch die Bearbeitung eines Programms haben Sie folgende Möglichkeiten:

* Hinzufügen der Sites-Lösung zu einem vorhandenen Programm mit Assets oder umgekehrt.
* Entfernen von Sites oder Assets aus einem vorhandenen Programm, das sowohl Sites als auch Assets umfasst.
* Hinzufügen einer zweiten, nicht verwendeten Lösungsberechtigung entweder für ein vorhandenes Programm oder als neues Programm.
* Löschen von Sandbox-Programmen.

## Berechtigungen {#permissions}

Sie müssen Mitglied der Rolle **Geschäftsinhaber** sein, um Programme bearbeiten oder Sandbox-Programme löschen zu können.

## Bearbeiten von Programmen {#editing}

Führen Sie diese Schritte aus, um ein Programm zu bearbeiten.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, das Sie bearbeiten möchten, um dessen Details anzuzeigen.

1. Klicken Sie oben links auf der Seite auf den Namen Ihres Programms und anschließend auf **Programm bearbeiten**.

   ![Option „Programm bearbeiten“](assets/edit-program-overview.png)

1. Die Seite **Programm bearbeiten** wird geöffnet. Wählen Sie die Registerkarte **Allgemein** aus, um den Programmnamen und die Beschreibung zu bearbeiten.

   * Für ein Programm muss mindestens eine Lösung ausgewählt sein.

   ![Registerkarte „Allgemein“](assets/edit-program-prod1.png)

1. Wählen Sie die Registerkarte **Lösungen und Add-ons** aus, um die Lösungen für das Programm zu ändern.

   ![Lösungen auswählen](assets/edit-prg.png)

1. Klicken Sie auf den Pfeil vor dem Lösungsnamen, um optionale Add-ons anzuzeigen, z. B. die Add-on-Option **Commerce** unter **Sites**.

   ![Add-ons bearbeiten](assets/edit-program-add-on.png)

1. Auf der Registerkarte **Einstellungen für die Live-Schaltung** können Sie den geplanten Tag der Veröffentlichung für das Programm ändern.

   ![Live-Schaltungs-Einstellungen bearbeiten](assets/edit-program-go-live.png)

   * Dieses Datum dient nur zu Informationszwecken und löst das Live-Schaltungs-Widget auf der Programmübersichtsseite aus, um rechtzeitig produktinterne Links zur Best-Practice-Dokumentation von AEM as a Cloud Service bereitzustellen und Ihnen so eine erfolgreiche und reibungslose Live-Schaltung ermöglicht.

1. Klicken Sie auf **Aktualisieren**, um Ihre Änderungen am Programm zu speichern.

Jedes Mal, wenn ein Programm bearbeitet wird, einschließlich Hinzufügen oder Entfernen einer Lösung oder eines Add-ons, werden diese Änderungen erst nach der nächsten Implementierung wirksam.

Wenn für Ihr Produktionsprogramm die erhöhte Sicherheit aktiviert war, wird eine zusätzliche **Verbesserte Sicherheit** im **Programm bearbeiten** -Fenster, um zu bestätigen, dass die Funktion für das Programm aktiv ist.

![Erweiterte Sicherheit für ein Programm aktiv](assets/edit-program-enhanced.png)

Diese Einstellung kann nach der Erstellung des Programms nicht mehr geändert werden. Weitere Informationen zur Option &quot;Erweiterte Sicherheit&quot;finden Sie im Abschnitt [Erstellen von Produktionsprogrammen](creating-production-programs.md) Dokument.

## Löschen von Sandbox-Programmen {#delete-sandbox-program}

Durch das Löschen eines Sandbox-Programms werden alle damit verbundenen Umgebungen und Pipelines entfernt.

>[!TIP]
>
>Benutzer mit den Rollen **Geschäftsinhaber** oder **Implementierungs-Manager** können alternativ ihre Produktions- und Staging-Umgebungen anstelle des gesamten Sandbox-Programms löschen.

Führen Sie die folgenden Schritte aus, um ein Sandbox-Programm zu löschen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, das Sie bearbeiten möchten, um dessen Details anzuzeigen.

1. Klicken Sie oben links auf der Seite auf den Namen Ihres Programms und anschließend auf **Programm löschen**.

   ![Option „Programm löschen“](assets/delete-sandbox1.png)

Alternativ können Sie auf der Übersichtsseite von Cloud Manager auf der Karte Ihres Programms auf den Butten mit Auslassungspunkten klicken und anschließend auf **Programm löschen**.

![Sandbox aus Programmkarte löschen](assets/delete-sandbox2.png)

>[!NOTE]
>
>Es können nur Sandbox-Programme gelöscht werden. Produktionsprogramme können nicht gelöscht werden.
