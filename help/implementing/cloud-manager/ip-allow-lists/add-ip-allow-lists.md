---
title: Hinzufügen von IP-Zulassungslisten
description: Erfahren Sie, wie Sie mit Cloud Manager Ihre eigene IP-Zulassungsliste hinzufügen.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
source-git-commit: 90250c13c5074422e24186baf78f84c56c9e3c4f
workflow-type: ht
source-wordcount: '198'
ht-degree: 100%

---


# Hinzufügen einer IP-Zulassungsliste {#add-ip-allow-list}

Erfahren Sie, wie Sie mit Cloud Manager Ihre eigene IP-Zulassungsliste hinzufügen.

Benutzerinnen oder Benutzer mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können diese Schritte ausführen, um eine IP-Zulassungsliste hinzuzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie im Bildschirm **[Eigene Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** das Programm aus.

1. Navigieren Sie auf der Seite **Übersicht** zum Bildschirm **Umgebungen**.

1. Navigieren Sie auf dem Bildschirm **Umgebungen** zur Seite **IP-Zulassungslisten**.

   ![Option „IP-Zulassungslisten“ im seitlichen Bedienfeld](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. Klicken Sie auf **IP-Zulassungsliste hinzufügen**.

   ![Dialogfeld „IP-Zulassungsliste hinzufügen“](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. Geben Sie im Dialogfeld **IP-Zulassungsliste hinzufügen** in das Feld **IP-Zulassungslistenname** einen Namen ein, den Sie als Referenz für die Zulassungsliste verwenden möchten.

   * Dieser Name ist nur informativ und sollte beschreibend sein, um Ihnen bei der Identifizierung der Liste zu helfen.

1. Geben Sie einen IP- oder IP-CIDR-Block in das Feld **IP-Adresse/CIDR** ein.

   * Mehrere Blöcke können durch ein Komma oder einen Tabstopp getrennt werden.

1. Klicken Sie auf **Speichern**.

Nach dem Speichern erscheint die neu erstellte IP-Zulassungsliste als Zeile in der Tabelle auf der Seite **IP-Zulassungslisten**.
