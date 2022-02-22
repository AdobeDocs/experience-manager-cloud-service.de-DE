---
title: Bearbeiten von Programmen
description: Erfahren Sie, wie Sie Ihre Produktions- und Sandbox-Programme bearbeiten, um ihre Optionen nach der Erstellung anzupassen.
source-git-commit: cf6941759dfc1e50928009490c7c518a89ed093e
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 4%

---


# Bearbeiten von Programmen {#editing-programs}

Benutzer mit den erforderlichen Berechtigungen können [in Ihrer Organisation erstellte Produktionsprogramme](creating-production-programs.md) sowie [Sandbox-Programme, die in Ihrer Organisation erstellt wurden.](creating-sandbox-programs.md) Durch die Bearbeitung eines Programms haben Sie folgende Möglichkeiten:

* Fügen Sie Sites-Lösungen zu einem vorhandenen Programm mit Assets hinzu und umgekehrt.
* Entfernen von Sites oder Assets aus einem vorhandenen Programm, das sowohl Sites als auch Assets umfasst.
* Fügen Sie eine zweite, nicht verwendete Lösungsberechtigung zu einem vorhandenen Programm oder einem neuen Programm hinzu.
* Löschen von Sandbox-Programmen.

>[!NOTE]
>
>Sie müssen Mitglied der **Business Owner** Rolle zum Bearbeiten von Programmen oder Löschen von Sandbox-Programmen.

Führen Sie diese Schritte aus, um ein Programm zu bearbeiten.

1. Melden Sie sich bei Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, das Sie bearbeiten möchten, um dessen Details anzuzeigen.

1. Klicken Sie oben links auf der Seite auf den Namen Ihres Programms und wählen Sie **Programm bearbeiten**.

   ![Option &quot;Programm bearbeiten&quot;](assets/edit-program-overview.png)

1. Die **Programm bearbeiten** Seite zeigt zwei Registerkarten an: **Allgemein** und **Lösungen und Add-ons**. Wählen Sie die **Allgemein** um den Programmnamen und die Beschreibung zu bearbeiten.

   * Für ein Programm muss mindestens eine Lösung ausgewählt sein.

   ![Registerkarte &quot;Allgemein&quot;](assets/edit-program-prod1.png)

1. Wählen Sie die **Lösungen und Add-ons** -Tab, um die Lösungen für das Programm zu ändern.

   ![Lösungen auswählen](assets/edit-prg.png)

1. Klicken Sie auf den Pfeil vor den Lösungsnamen, um optionale Add-ons anzuzeigen, z. B. die **Handel** Add-On-Option unter **Sites**.

   ![Add-ons bearbeiten](assets/edit-program-add-on.png)

1. Klicken Sie auf **Aktualisieren** , um Ihre Änderungen am Programm zu speichern.

Sobald Ihre Aktualisierungen vorgenommen wurden und die ausgewählten Lösungen geändert wurden, werden diese Änderungen nach der nächsten Bereitstellung wirksam.

## Löschen von Sandbox-Programmen {#delete-sandbox-program}

Durch das Löschen eines Sandbox-Programms werden alle damit verbundenen Umgebungen und Pipelines entfernt.

>[!TIP]
>
>Benutzer mit **Business Owner** oder **Bereitstellungsmanager** -Rollen können alternativ ihre Produktions- und Staging-Umgebungen anstelle des gesamten Sandbox-Programms löschen.

Führen Sie die folgenden Schritte aus, um ein Sandbox-Programm zu löschen.

1. Melden Sie sich bei Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, das Sie bearbeiten möchten, um dessen Details anzuzeigen.

1. Klicken Sie oben links auf der Seite auf den Namen Ihres Programms und wählen Sie **Programm löschen**.

   ![Option &quot;Programm löschen&quot;](assets/delete-sandbox1.png)

Alternativ können Sie auf der Übersichtsseite von Cloud Manager auf der Karte Ihres Programms auf die Suchschaltfläche mit Auslassungspunkten klicken und **Programm löschen**.

![Sandbox aus Programmkarte löschen](assets/delete-sandbox2.png)

>[!NOTE]
>
>Es können nur Sandbox-Programme gelöscht werden. Produktionsprogramme können nicht gelöscht werden.