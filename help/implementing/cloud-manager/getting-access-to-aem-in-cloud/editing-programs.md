---
title: Bearbeiten von Programmen
description: Erfahren Sie, wie Sie Ihre Produktions- und Sandbox-Programme bearbeiten, um ihre Optionen nach der Erstellung anzupassen.
exl-id: 819e4a6e-f77a-4594-a402-a300dcbdf510
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f0cf9fa7da7e89d42ab90dee0e8400b26f004574
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 84%

---


# Bearbeiten von Programmen {#editing-programs}

Um Programme zu verwalten und zu bearbeiten, beginnen Sie bei der Konsole [**Meine Programme**](/help/implementing/cloud-manager/navigation.md). Die Seite **Meine Programme** bietet einen Überblick über alle Programme, auf die Sie Zugriff haben. Wenn Sie ein einzelnes Programm auswählen, finden Sie auf der Seite **Programmübersicht** Details zu dem Programm auf einen Blick.

Von der **Programmübersicht** aus können Benutzende mit den erforderlichen Berechtigungen [Produktionsprogramme, die in Ihrer Organisation erstellt wurden](creating-production-programs.md) und [Sandbox-Programme, die in Ihrer Organisation erstellt wurden](creating-sandbox-programs.md), bearbeiten. Durch die Bearbeitung eines Programms haben Sie folgende Möglichkeiten:

* Hinzufügen der Sites-Lösung zu einem vorhandenen Programm mit Assets oder umgekehrt.
* Entfernen von Sites oder Assets aus einem vorhandenen Programm, das sowohl Sites als auch Assets umfasst.
* Hinzufügen einer nicht verwendeten Lösungsberechtigung zu einem vorhandenen Programm oder Erstellen eines neuen Programms.
* Löschen von Sandbox-Programmen.

## Berechtigungen {#permissions}

Sie müssen über die Rolle **Geschäftsinhaber** verfügen, um Programme zu bearbeiten, Sandbox-Programme zu löschen und auf das Lizenz-Dashboard zuzugreifen.

## Bearbeiten eines Programms {#editing}

Jedes Mal, wenn ein Programm bearbeitet wird, einschließlich des Hinzufügens oder Entfernens einer Lösung oder eines Add-ons, werden diese Änderungen erst nach der nächsten Bereitstellung wirksam.

**Bearbeiten eines Programms:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf der Seite **[Meine Programme](#my-programs)** auf das Programm, das Sie bearbeiten möchten, um seine Details anzuzeigen.

1. Klicken Sie oben links auf der Seite auf den Namen Ihres Programms und anschließend auf **Programm bearbeiten**.

   ![Option „Programm bearbeiten“](assets/edit-program-overview.png)

1. Die Seite **Programm bearbeiten** öffnet sich auf der Registerkarte **Allgemein**.

   ![Registerkarte „Allgemein“](assets/edit-program-prod1.png)

1. Bei den Optionen, die zum Bearbeiten des Programms verfügbar sind, handelt es sich um dieselben Optionen für die Programmerstellung.
   * Einzelheiten zu den einzelnen Optionen finden Sie unter [Erstellen von Produktionsprogrammen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) und [Erstellen von Sandbox-Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md).
   * Abhängig von den Ansprüchen Ihrer Organisation können [weitere Optionen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#options) für Ihr Produktionsprogramm verfügbar sein.

1. Klicken Sie auf **Aktualisieren**, um Ihre Änderungen am Programm zu speichern.

## Löschen eines Sandbox-Programms {#delete-sandbox-program}

Durch das Löschen eines Sandbox-Programms werden alle damit verbundenen Umgebungen und Pipelines entfernt.

>[!TIP]
>
>Benutzende mit den Rollen **Geschäftsinhaber** oder **Bereitstellungs-Manager** können alternativ ihre Produktions- und Staging-Umgebungen anstelle des gesamten Sandbox-Programms löschen.

**So löschen Sie ein Sandbox-Programm:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf der Seite **[Meine Programme](#my-programs)** auf das Programm, das Sie bearbeiten möchten, um seine Details anzuzeigen.

1. Klicken Sie oben links auf der Seite auf den Namen Ihres Programms und wählen Sie anschließend **Programm löschen** aus.

   ![Option „Programm löschen“](assets/delete-sandbox1.png)

Alternativ können Sie auf der Übersichtsseite von Cloud Manager auf ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) Karte Ihres Programms auf ![Mehr-Symbol“ klicken und anschließend auf **Programm löschen**.

![Sandbox aus Programmkarte löschen](assets/delete-sandbox2.png)

>[!NOTE]
>
>Es können nur Sandbox-Programme gelöscht werden. Produktionsprogramme können nicht gelöscht werden.
