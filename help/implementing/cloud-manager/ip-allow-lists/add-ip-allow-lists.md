---
title: Hinzufügen von IP-Zulassungslisten
description: Erfahren Sie, wie Sie mithilfe von Cloud Manager Ihre eigene IP-Zulassungsliste hinzufügen.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
source-git-commit: 97a6a7865f696f4d61a1fb4e25619caac7b68b51
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 30%

---


# Hinzufügen einer IP-Zulassungsliste {#add-ip-allow-list}

Erfahren Sie, wie Sie mithilfe von Cloud Manager Ihre eigene IP-Zulassungsliste hinzufügen.

Ein Benutzer im **Business Owner** oder **Bereitstellungsmanager** -Rolle kann die folgenden Schritte ausführen, um eine IP-Zulassungsliste hinzuzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Aus dem **Übersicht** Seite, navigieren Sie zur **Umgebungen** angezeigt.

1. Aus dem **Umgebungen** -Bildschirm, navigieren Sie zur **IP-Zulassungslisten** Seite.

   ![Option „IP-Zulassungslisten“ im seitlichen Bedienfeld](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. Klicks **IP-Zulassungsliste hinzufügen**.

   ![Dialogfeld &quot;IP-Zulassungsliste hinzufügen&quot;](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. Im **IP-Zulassungsliste hinzufügen** Geben Sie im Dialogfeld einen Namen ein, den Sie zum Verweisen auf die Zulassungsliste in der **IP-Zulassungsliste** -Feld.

   * Dieser Name ist nur informativ und sollte beschreibend sein, um Sie bei der Identifizierung der Liste zu unterstützen.

1. Geben Sie einen IP- oder IP-CIDR-Block in das Feld **IP-Adresse/CIDR** ein.

   * Mehrere Blöcke können durch ein Komma oder einen Tabstopp getrennt werden.

1. Klicken Sie auf **Speichern**.

Nach dem Speichern wird die neu erstellte IP-Zulassungsliste als Zeile in der Tabelle im **IP-Zulassungslisten** Seite.
