---
title: Hinzufügen von IP-Zulassungslisten
description: Erfahren Sie, wie Sie mit Cloud Manager Ihre eigene IP-Zulassungsliste hinzufügen.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 100%

---


# Hinzufügen einer IP-Zulassungsliste {#add-ip-allow-list}

Erfahren Sie, wie Sie mit Cloud Manager Ihre eigene IP-Zulassungsliste hinzufügen.

Benutzerinnen oder Benutzer mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können die folgenden Schritte ausführen, um eine IP-Zulassungsliste hinzuzufügen.

{{add-cm-allowlist-frontend-pipeline}}
{{ip-allow-lists-ue}}

**So fügen Sie eine IP-Zulassungsliste hinzu:**

1. Melden Sie sich unter [experiece.adobe.com](https://experience.adobe.com/de/experiencemanager/) bei Cloud Manager an.

1. Klicken Sie im linken Menü auf Cloud Manager und wählen Sie dann die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Klicken Sie auf der Seite **Programmübersicht** mithilfe des seitlichen Bedienfelds (Sie müssen möglicherweise erst auf ![Symbol „Menü anzeigen“](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) oben links klicken, um das Menü anzuzeigen) auf ![Symbol „Aufgabenliste“](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **IP-Zulassungsliste**.

   ![Option „IP-Zulassungslisten“ im Menü auf der linken Seite](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. Klicken Sie oben rechts auf der Seite „IP-Zulassungslisten“ auf **IP-Zulassungsliste hinzufügen**.

   ![Dialogfeld „IP-Zulassungsliste hinzufügen“](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. Geben Sie im Dialogfeld **IP-Zulassungsliste hinzufügen** im Feld **IP-Zulassungslistenname** einen Namen ein, den Sie als Referenz für die IP-Zulassungsliste verwenden möchten. Dieser Name dient nur zu Informationszwecken. Achten Sie darauf, dass er beschreibend genug ist, um Ihnen bei der Identifizierung der Liste zu helfen.

1. Geben Sie im Feld **IP-Adresse/CIDR** bis zu 50 IP-Adressen oder CIDR-Blöcke. Sie können sie auf eine der folgenden Arten hinzufügen:

   * Einzeln: Geben Sie eine Adresse ein und drücken Sie dann `Enter`. Wiederholen Sie dies für jede weitere Adresse.
   * Mehrere gleichzeitig: Geben Sie Adressen durch Kommata (,) oder Tabulatoren getrennt ein und drücken Sie dann `Enter`, damit jede Adresse einzeln erkannt wird.

1. Nachdem Sie die letzte IP-Adresse oder den letzten CIDR-Block eingegeben haben, drücken Sie `Enter`, um die Eingabe zu bestätigen. Der Eintrag wird erst nach Drücken von `Enter` bestätigt und die Schaltfläche **Speichern** wird aktiviert.

1. Klicken Sie auf **Speichern**.

Nach dem Speichern erscheint die neu erstellte IP-Zulassungsliste als Zeile in der Tabelle auf der Seite **IP-Zulassungslisten**.

