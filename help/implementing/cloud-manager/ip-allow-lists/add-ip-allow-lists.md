---
title: Hinzufügen von IP-Zulassungslisten
description: Erfahren Sie, wie Sie mit Cloud Manager Ihre eigene IP-Zulassungsliste hinzufügen.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: d36dc453097b1f2507ff1ca6d775acf8b9ac5add
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 63%

---


# Hinzufügen einer IP-Zulassungsliste {#add-ip-allow-list}

Erfahren Sie, wie Sie mit Cloud Manager Ihre eigene IP-Zulassungsliste hinzufügen.

Um eine IP-Zulassungsliste hinzuzufügen, kann ein Benutzer mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** die folgenden Schritte ausführen.

{{add-cm-allowlist-frontend-pipeline}}
{{ip-allow-lists-ue}}

**So fügen Sie eine IP-Zulassungsliste hinzu:**

{{sign-in-to-cloud-manager}}

1. Wählen Sie in **[Konsole](/help/implementing/cloud-manager/navigation.md#my-programs)** Meine Programme“ ein Programm aus.

1. Klicken Sie auf der **Programmübersicht** im linken Menü (klicken Sie ggf. auf ![Menüsymbol anzeigen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) oben links, um das Menü anzuzeigen) auf ![](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) Aufgabenlistensymbol **IP-Zulassungslisten**.

   ![Option „IP-Zulassungslisten“ im Menü auf der linken Seite](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. Klicken Sie oben rechts auf der Seite „IP-Zulassungslisten“ auf **IP-Zulassungsliste hinzufügen**.

   ![Dialogfeld „IP-Zulassungsliste hinzufügen“](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. Geben Sie im Dialogfeld **IP-Zulassungsliste hinzufügen** im Feld **IP-Zulassungslistenname** einen Namen ein, den Sie als Referenz für die IP-Zulassungsliste verwenden möchten. Dieser Name dient nur zu Informationszwecken. Stellen Sie sicher, dass sie beschreibend genug ist, um Ihnen bei der Identifizierung der Liste zu helfen.

1. Geben Sie im Feld **IP-Adresse/CIDR** bis zu 50 IP-Adressen oder CIDR-Blöcke. Sie können sie auf eine der folgenden Arten hinzufügen:

   * Einzeln: Geben Sie eine Adresse ein und drücken Sie dann `Enter`. Wiederholen Sie dies für jede weitere Adresse.
   * Mehrere gleichzeitig: Geben Sie Adressen ein, die durch Kommas (,) oder Tabulatoren getrennt sind, und drücken Sie dann `Enter`, damit jede Adresse einzeln verarbeitet wird.

1. Nachdem Sie die letzte IP-Adresse oder den letzten CIDR-Block eingegeben haben, drücken Sie `Enter`, um die Eingabe zu bestätigen. Der Eintrag wird erst nach Drücken von `Enter` bestätigt und die Schaltfläche **Speichern** wird aktiviert.

1. Klicken Sie auf **Speichern**.

Nach dem Speichern wird die neu erstellte IP-Zulassungsliste als Zeile in der Seitentabelle **IP-Zulassungslisten** angezeigt.

