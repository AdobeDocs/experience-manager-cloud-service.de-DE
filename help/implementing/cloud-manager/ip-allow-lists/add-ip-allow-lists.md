---
title: Hinzufügen von IP-Zulassungslisten
description: Erfahren Sie, wie Sie Ihre eigene IP-Zulassungsliste mit Cloud Manager hinzufügen.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
source-git-commit: 378ff582435f1ab3db431a0c9c3e80a4661cccc4
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 15%

---


# Hinzufügen einer IP-Zulassungsliste {#add-ip-allow-list}

Erfahren Sie, wie Sie Ihre eigene IP-Zulassungsliste mit Cloud Manager hinzufügen.

Ein Benutzer im **Business Owner** oder **Bereitstellungsmanager** Rolle kann diese Schritte ausführen, um eine IP-Zulassungsliste hinzuzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zu **Umgebungen** -Bildschirm aus dem **Übersicht** Seite.

1. Navigieren Sie vom Bildschirm **Umgebungen** zur Seite **IP-Zulassungslisten**.

   ![Option &quot;IP-Zulassungslisten&quot;im Seitenbereich](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. Klicken Sie auf **IP-Zulassungsliste hinzufügen** , um **IP-Zulassungsliste hinzufügen** angezeigt.

   ![Dialogfeld &quot;IP-Zulassungsliste hinzufügen&quot;](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. Geben Sie einen Namen ein, mit dem Sie auf die Zulassungsliste im **Name der IP-Zulassungsliste** -Feld.

   * Dies ist nur informativ und sollte beschreibend sein, um Sie bei der Identifizierung der Liste zu unterstützen.

1. Geben Sie einen IP- oder IP-CIDR-Block im **IP-Adresse/CIDR.** -Feld.

   * Mehrere Blöcke können durch ein Komma oder eine Registerkarte getrennt werden.

1. Klicken **Speichern** , um Ihre Übermittlung zu bestätigen.

Nach dem Speichern wird die neu erstellte IP-Zulassungsliste als Zeile in der Tabelle in der **IP-Zulassungslisten** Seite.
