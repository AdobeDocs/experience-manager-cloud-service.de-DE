---
title: Anwenden und Aufheben der Anwendung von IP-Zulassungslisten
description: Erfahren Sie, wie Sie IP-Zulassungslisten auf Cloud Manager-Umgebungen anwenden und wie Sie deren Anwendung wieder aufheben.
exl-id: 7158496c-b0c4-4228-a306-71dc51003c57
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 593b8c704c5b016bb55ae6a25420b577044b4126
workflow-type: ht
source-wordcount: '303'
ht-degree: 100%

---


# Anwenden und Aufheben der Anwendung von IP-Zulassungslisten {#apply-allow-list}

Beim Anwenden von IP-Zulassungslisten sind alle in der Listendefinition enthaltenen IP-Bereiche mit einem Autoren- oder Veröffentlichungs-Service in einer Umgebung verknüpft. Das Aufheben der Anwendung einer Liste ist das Gegenteil zu diesem Prozess.

{{add-cm-allowlist-frontend-pipeline}}
{{ip-allow-lists-ue}}

## Anwenden von IP-Zulassungslisten {#applying}

Benutzerinnen oder Benutzer mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können diese Schritte ausführen, um eine IP-Zulassungsliste anzuwenden.

**Anwenden von IP-Zulassungslisten:**

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an.
1. Wählen Sie das entsprechende Unternehmen aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.
1. Navigieren Sie auf der Seite **Übersicht** zum Bildschirm **Umgebungen**.
1. Navigieren Sie auf dem Bildschirm **Umgebungen** zu der Seite mit den spezifischen Umgebungsdetails.
1. Navigieren Sie zur Tabelle **IP-Zulassungsliste** .
1. Verwenden Sie die Eingabefelder oben in der Tabelle, um die IP-Zulassungsliste und den Autoren-, Veröffentlichungs- oder Vorschau-Service auszuwählen, auf den sie angewendet werden soll.
Die IP-Zulassungsliste muss bereits in Cloud Manager vorhanden sein, damit sie angewendet werden kann. Siehe [Hinzufügen von IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md).
1. Klicken Sie auf ![Hinzufügen-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) **Anwenden** und bestätigen Sie die Übermittlung.

## Aufheben der Anwendung von IP-Zulassungslisten {#un-applying}

Benutzerinnen oder Benutzer mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können die folgenden Schritte ausführen, um die Anwendung einer IP-Zulassungsliste aufzuheben.

**Aufheben der Anwendung einer IP-Zulassungsliste:**

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an.
1. Wählen Sie das entsprechende Unternehmen aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.
1. Navigieren Sie auf der Seite **Übersicht** zur Seite **Umgebungen**.
1. Navigieren Sie zur Seite mit den spezifischen Umgebungsdetails.
1. Scrollen Sie auf der Registerkarte „Allgemein“ zur Tabelle **IP-Zulassungsliste**.
1. Ermitteln Sie die Zeile der IP-Zulassungsliste, deren Anwendung Sie aufheben möchten.
1. Klicken Sie rechts neben der identifizierten Zeile auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).
1. Klicken Sie auf **Aufheben**.
1. Klicken Sie im Dialogfeld **Anwendung der IP-Zulassungsliste aufheben** auf **Aufheben**.
