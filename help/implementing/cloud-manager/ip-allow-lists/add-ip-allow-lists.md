---
title: Hinzufügen von IP-Zulassungslisten
description: Erfahren Sie, wie Sie mit Cloud Manager Ihre eigene IP-Zulassungsliste hinzufügen.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
source-git-commit: fa6d0670a011276facc561f62f52c6e69147a49e
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 87%

---


# Hinzufügen einer IP-Zulassungsliste {#add-ip-allow-list}

Erfahren Sie, wie Sie mit Cloud Manager Ihre eigene IP-Zulassungsliste hinzufügen.

Benutzerinnen oder Benutzer mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können diese Schritte ausführen, um eine IP-Zulassungsliste hinzuzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Im **[Eigene Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** -Konsole, wählen Sie das Programm aus.

1. Aus dem **Übersicht** Seite, navigieren Sie zur **IP-Zulassungslisten** Seite mithilfe der Registerkarte Seitennavigation.

   ![Option „IP-Zulassungslisten“ im seitlichen Bedienfeld](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. Klicken Sie auf **IP-Zulassungsliste hinzufügen**.

   ![Dialogfeld „IP-Zulassungsliste hinzufügen“](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. Geben Sie im Dialogfeld **IP-Zulassungsliste hinzufügen** in das Feld **IP-Zulassungslistenname** einen Namen ein, den Sie als Referenz für die Zulassungsliste verwenden möchten.

   * Dieser Name ist nur informativ und sollte beschreibend sein, um Ihnen bei der Identifizierung der Liste zu helfen.

1. Geben Sie einen IP- oder IP-CIDR-Block in das Feld **IP-Adresse/CIDR** ein.

   * Mehrere Blöcke können durch ein Komma oder einen Tabstopp getrennt werden.

1. Klicken Sie auf **Speichern**.

Nach dem Speichern erscheint die neu erstellte IP-Zulassungsliste als Zeile in der Tabelle auf der Seite **IP-Zulassungslisten**.
