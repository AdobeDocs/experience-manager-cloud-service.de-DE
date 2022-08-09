---
title: Hinzufügen von IP-Zulassungslisten
description: Erfahren Sie, wie Sie Ihre eigene IP-Zulassungsliste mit Cloud Manager hinzufügen.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
source-git-commit: 378ff582435f1ab3db431a0c9c3e80a4661cccc4
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 100%

---


# Hinzufügen einer IP-Zulassungsliste {#add-ip-allow-list}

Erfahren Sie, wie Sie Ihre eigene IP-Zulassungsliste mit Cloud Manager hinzufügen.

Benutzerinnen oder Benutzer mit der Rolle **Geschäftsinhaber** oder **Implementierungs-Manager** können diese Schritte ausführen, um eine IP-Zulassungsliste hinzuzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie auf der **Übersichtsseite** zum Bildschirm **Umgebungen**.

1. Navigieren Sie vom Bildschirm **Umgebungen** zur Seite **IP-Zulassungslisten**.

   ![Option „IP-Zulassungslisten“ im seitlichen Bedienfeld](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. Klicken Sie auf **IP-Zulassungsliste hinzufügen**, um das Dialogfeld **IP-Zulassungsliste hinzufügen** zu öffnen.

   ![Dialogfeld „IP-Zulassungsliste hinzufügen“](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. Geben Sie im Feld **Name der IP-Zulassungsliste** einen Namen ein, mit dem Sie auf die Zulassungsliste verweisen möchten.

   * Dieser ist nur informativ und sollte beschreibend sein, um Ihnen bei der Identifizierung der Liste zu helfen.

1. Geben Sie einen IP- oder IP-CIDR-Block in das Feld **IP-Adresse/CIDR** ein.

   * Mehrere Blöcke können durch ein Komma oder einen Tabstopp getrennt werden.

1. Klicken Sie auf **Speichern**, um die Übermittlung zu bestätigen.

Nach dem Speichern erscheint die neu erstellte IP-Zulassungsliste als Zeile in der Tabelle auf der Seite **IP-Zulassungslisten**.
