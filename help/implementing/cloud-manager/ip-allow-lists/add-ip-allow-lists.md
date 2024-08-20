---
title: Hinzufügen von IP-Zulassungslisten
description: Erfahren Sie, wie Sie Ihre eigenen IP-Zulassungslisten mit Cloud Manager hinzufügen.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f4c6331491bb08e81964476ad58065c1ee022967
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 14%

---


# Hinzufügen einer IP-Zulassungsliste {#add-ip-allow-list}

Erfahren Sie, wie Sie Ihre eigene IP-Zulassungsliste mit Cloud Manager hinzufügen.

Ein Benutzer mit der Rolle **Business Owner** oder **Deployment Manager** kann die folgenden Schritte ausführen, um eine IP-Zulassungsliste hinzuzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Klicken Sie auf der Seite **Programmübersicht** über das Seitenbedienfeld auf der linken Seite (Sie müssen möglicherweise auf das Hamburger-Symbol oben links klicken, um das Bedienfeld anzuzeigen) auf **IP-Zulassungslisten**.

   ![Option &quot;IP-Zulassungslisten&quot;im Seitenbereich](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. Klicken Sie oben rechts auf der Seite &quot;IP-Zulassungslisten&quot;auf **IP-Zulassungsliste hinzufügen**.

   ![Dialogfeld „IP-Zulassungsliste hinzufügen“](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. Geben Sie im Dialogfeld **IP-Zulassungsliste hinzufügen** im Feld **Name der IP-Zulassungsliste** einen Namen ein, den Sie verwenden möchten, um auf die IP-Zulassungsliste zu verweisen. Dieser Name ist nur informativ. Vergewissern Sie sich, dass sie beschreibend genug ist, um Sie bei der Identifizierung der Liste zu unterstützen.

1. Geben Sie im Feld **IP-Adresse/CIDR** einen IP- oder IP-CIDR-Block ein. Trennen Sie mehrere Blöcke durch ein Komma oder eine Registerkarte.

1. Klicken Sie auf **Speichern**.

Nach dem Speichern wird die neu erstellte IP-Zulassungsliste als Zeile in der Tabelle auf der Seite **IP-Zulassungslisten** angezeigt.
