---
title: Hinzufügen von IP-Zulassungslisten
description: Erfahren Sie, wie Sie Ihre eigenen IP-Zulassungslisten mit Cloud Manager hinzufügen.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 1415d07235641262814e81362c806572bcf582ba
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 12%

---


# Hinzufügen einer IP-Zulassungsliste {#add-ip-allow-list}

Erfahren Sie, wie Sie Ihre eigene IP-Zulassungsliste mit Cloud Manager hinzufügen.

Ein Benutzer mit der Rolle **Business Owner** oder **Deployment Manager** kann die folgenden Schritte ausführen, um eine IP-Zulassungsliste hinzuzufügen.

{{add-cm-allowlist-frontend-pipeline}}

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

## Hinzufügen der Cloud Manager IP-Zulassungsliste {#add-cm-allowlist}

Für die Front-End-Pipeline muss zuvor die folgende Cloud Manager IP-Zulassungsliste hinzugefügt werden.

**IP-Zulassungsliste von Cloud Manager**

`52.254.106.192/28,20.186.185.181,52.254.106.240/28,52.254.107.128/28,52.254.105.192/28,52.254.106.176/28,20.186.185.227,52.254.106.144/28,52.254.107.64/28,20.186.185.239,20.22.83.112,52.254.107.80/28,52.254.107.144/28,52.254.106.224/28,20.14.241.153,52.254.107.0/28,52.254.107.32/28,52.254.106.208/28,40.70.154.136/29,52.254.106.160/28,52.254.107.16/28,52.254.106.0/28,4.152.211.251`

Um eine Unterbrechung der Ausführung der Frontend-Pipeline zu vermeiden, stellen Sie sicher, dass diese Cloud Manager IP-Zulassungsliste hinzugefügt und dann auf den Autorendienst der Umgebung angewendet wird, *vor* aktivieren Sie die Pipeline.

**Hinzufügen der Cloud Manager IP-Zulassungsliste:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Klicken Sie auf der Seite **Programmübersicht** über das Seitenbedienfeld auf der linken Seite (Sie müssen möglicherweise auf das Hamburger-Symbol oben links klicken, um das Bedienfeld anzuzeigen) auf **IP-Zulassungslisten**.

1. Klicken Sie oben rechts auf der Seite &quot;IP-Zulassungslisten&quot;auf **IP-Zulassungsliste hinzufügen**.

1. Geben Sie im Dialogfeld **IP-Zulassungsliste hinzufügen** im Feld **Name der IP-Zulassungsliste** den Wert *`Cloud Manager`* ein.

1. Kopieren Sie den Block der oben genannten IP-Zulassungsliste-Adressen von Cloud Manager. Jede Adresse ist bereits durch ein Komma getrennt.

1. Fügen Sie im Dialogfeld **IP-Zulassungsliste hinzufügen** den Baustein in das Feld **IP-Adresse/CIDR** ein.

1. Platzieren Sie den Cursor direkt nach dem ersten Komma in der Adressliste und drücken Sie **Enter**.

1. Klicken Sie auf **Speichern**.

Wenden Sie nun [die IP-Zulassungsliste von Cloud Manager](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) auf Ihre Programmumgebungen an.



