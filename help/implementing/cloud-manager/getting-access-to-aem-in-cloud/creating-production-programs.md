---
title: 'Erstellen von Produktionsprogrammen '
description: Erfahren Sie, wie Sie mit Cloud Manager Ihr eigenes Produktionsprogramm für das Hosten von Live-Traffic erstellen.
exl-id: 4ccefb80-de77-4998-8a9d-e68d29772bb4
source-git-commit: 3557ddbc76ff21bcfe4ac0338f116b02b5135f2c
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 74%

---


# Erstellen von Produktionsprogrammen {#create-production-program}

Ein Produktionsprogramm ist für einen Benutzer gedacht, der mit AEM und Cloud Manager vertraut ist und Code für die Bereitstellung zum Hosten von Live-Traffic schreiben, erstellen und testen möchte.

Weitere Informationen zu Programmtypen finden Sie im Dokument [Programm- und Programmtypen](program-types.md).

## Video-Tutorials {#video-tutorials}

Sie können sich diese beiden Video-Tutorials ansehen, um zu erfahren, wie Sie ein Programm im Cloud Manager erstellen, [oder unsere dokumentierten Anweisungen befolgen.](#create)

>[!VIDEO](https://video.tv.adobe.com/v/334953)

>[!VIDEO](https://video.tv.adobe.com/v/334954)

## Erstellen eines Produktionsprogramms {#create}

Gehen Sie wie folgt vor, um ein Produktionsprogramm zu erstellen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie oben rechts im Bildschirm auf **Programm hinzufügen**.

   ![Cloud Manager-Landingpage](assets/first_timelogin1.png)

1. Wählen Sie im Assistenten „Programm erstellen“ die Option **Für die Produktion einrichten** aus, um ein Produktionsprogramm zu erstellen. Sie können den standardmäßigen Programmnamen akzeptieren oder ihn bearbeiten, bevor Sie auf **Weiter**.

   ![Assistent zum Erstellen von Programmen](assets/create-prod1.png)

1. Im **Lösungen und Add-ons** wählen Sie die Lösungen aus, die in das Programm aufgenommen werden sollen.

   ![Lösungen auswählen](assets/setup-prod-select.png)

1. Klicken Sie auf den Pfeil vor dem Lösungsnamen, um optionale Add-ons anzuzeigen, z. B. die Add-on-Option **Commerce** unter **Sites**.

   ![Add-ons auswählen](assets/setup-prod-commerce.png)

1. Klicken Sie bei ausgewählten Lösungen und Add-ons auf **Weiter**.

1. Im **Aufschaltdatum** auf, geben Sie das Datum ein, an dem Ihr Produktionsprogramm live geschaltet werden soll.

   ![Geplantes Live-Datum definieren](assets/setup-go-live.png)

   * Dieses Datum kann jederzeit bearbeitet werden.
   * Dieses Datum dient nur zur informativen Verwendung und Trigger erhalten über das Widget Go Live auf der Programmübersichtsseite produktinterne Links zu AEM as a Cloud Service Best Practice-Dokumentation, die zeitnah mit Ihrem Journey übereinstimmen und zu einem erfolgreichen und reibungslosen Go Live-Erlebnis führen.

1. Klicken Sie auf **Erstellen**.

Ihr Programm wird von Cloud Manager erstellt, wird auf der Landingpage angezeigt und kann dort ausgewählt werden.

![Übersicht über Cloud Manager](assets/navigate-cm.png)

## Zugriff auf ein Programm {#acessing}

1. Sobald Sie die Programmkarte auf der Landingpage sehen, klicken Sie auf die Schaltfläche mit den Auslassungspunkten, um die für Sie verfügbaren Menüoptionen anzuzeigen.

   ![Programmübersicht](assets/program-overview.png)

1. Wählen Sie **Cloud Manager** aus, um zur Seite **Übersicht** von Cloud Manager zu gelangen.

1. Die wichtigste Karte mit Handlungsaufforderung auf der Übersichtsseite führt Sie durch die Erstellung einer Umgebung, einer produktionsfremden Pipeline und schließlich einer Produktions-Pipeline.

   ![Programmübersicht](assets/set-up-prod5.png)

Wenn Sie irgendwann zu einem anderen Programm wechseln oder zur Übersichtsseite zurückkehren möchten, um ein anderes Programm zu erstellen, klicken Sie auf den Namen Ihres Programms oben links im Bildschirm, um die Option **Navigieren zu** aufzurufen.

![Navigieren zu](assets/create-program-a1.png)

>[!NOTE]
>
>Im Gegensatz zu einem [Sandbox-Programm](introduction-sandbox-programs.md#auto-creation) erfordert ein Produktionsprogramm, dass der Benutzer das Projekt in der entsprechenden Cloud Manager-Rolle erstellt und über die Self-Service-Benutzeroberfläche eine Umgebung hinzufügt.
