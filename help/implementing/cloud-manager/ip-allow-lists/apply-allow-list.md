---
title: Anwenden und Anwenden von IP-Zulassungslisten
description: Erfahren Sie, wie Sie IP-Zulassungslisten auf Cloud Manager-Umgebungen anwenden und deren Anwendung aufheben.
exl-id: 7158496c-b0c4-4228-a306-71dc51003c57
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: d6ecdae8dd78c3c93a410ca2c8b80322340f439e
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 22%

---


# Anwenden und Aufheben der Anwendung von IP-Zulassungslisten {#apply-allow-list}

Beim Anwenden von IP-Zulassungslisten werden alle in der Listendefinition enthaltenen IP-Bereiche mit einem Autoren- oder Veröffentlichungsdienst in einer Umgebung verknüpft. Das Aufheben der Anwendung einer Liste ist das Gegenteil zu diesem Prozess.

{{add-cm-allowlist-frontend-pipeline}}

## Anwenden von IP-Zulassungslisten {#applying}

Ein Benutzer mit der Rolle **Business Owner** oder **Deployment Manager** kann die folgenden Schritte ausführen, um eine IP-Zulassungsliste anzuwenden.

**So wenden Sie IP-Zulassungslisten an:**

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an.
1. Wählen Sie die entsprechende Organisation aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.
1. Navigieren Sie auf der Seite **Übersicht** zum Bildschirm **Umgebungen**.
1. Navigieren Sie auf dem Bildschirm **Umgebungen** zur Seite mit den spezifischen Umgebungsdetails.
1. Navigieren Sie zur Tabelle **IP-Zulassungsliste** .
1. Verwenden Sie die Eingabefelder oben in der Tabelle, damit Sie die IP-Zulassungsliste und den Autoren- oder Veröffentlichungsdienst auswählen können, auf die Sie sie anwenden möchten.
Die IP-Zulassungsliste muss bereits in Cloud Manager vorhanden sein, um sie anzuwenden. Siehe [IP-Zulassungslisten hinzufügen](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md).
1. Klicken Sie auf **Anwenden** und bestätigen Sie Ihre Übermittlung.

## IP-Zulassungslisten aufheben {#un-applying}

Ein Benutzer mit der Rolle **Business Owner** oder **Deployment Manager** kann die folgenden Schritte ausführen, um die Anwendung einer IP-Zulassungsliste aufzuheben.

**So heben Sie die Anwendung von IP-Zulassungslisten auf:**

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an.
1. Wählen Sie die entsprechende Organisation aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.
1. Navigieren Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.
1. Navigieren Sie zur Seite mit den spezifischen Umgebungsdetails auf dem Bildschirm **Umgebungen** .1. Navigieren Sie zur Tabelle **IP-Zulassungsliste** .
1. Identifizieren Sie die Zeile der IP-Zulassungsliste, deren Anwendung Sie aufheben möchten.
1. Klicken Sie rechts neben der identifizierten Zeile auf die Suchschaltfläche und wählen Sie dann **Unapply** aus.
1. Bestätigen Sie Ihre Übermittlung.
