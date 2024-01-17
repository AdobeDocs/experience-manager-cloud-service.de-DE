---
title: Anwenden und Aufheben der Anwendung von IP-Zulassungslisten
description: Erfahren Sie, wie Sie IP-Zulassungslisten auf Umgebungen anwenden und wie Sie deren Anwendung wieder aufheben.
exl-id: 7158496c-b0c4-4228-a306-71dc51003c57
source-git-commit: 90250c13c5074422e24186baf78f84c56c9e3c4f
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 97%

---


# Anwenden und Aufheben der Anwendung von IP-Zulassungslisten {#apply-allow-list}

Beim Anwenden einer IP-Zulassungsliste sind alle in der Listendefinition enthaltenen IP-Bereiche mit einem Authoring- oder Publishing-Service in einer Umgebung verknüpft. Das Aufheben der Anwendung einer Liste ist das Gegenteil zu diesem Prozess.

## Anwenden von IP-Zulassungslisten {#applying}

Benutzerinnen oder Benutzer mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können diese Schritte ausführen, um eine IP-Zulassungsliste anzuwenden.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Im **[Eigene Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** angezeigt, wählen Sie das Programm aus.
1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.
1. Gehen Sie im Bildschirm **Umgebungen** zur Seite mit den Umgebungsdetails und dann zur Tabelle **IP-Zulassungsliste**.
1. Verwenden Sie die Eingabefelder oben in der Tabelle, um die IP-Zulassungsliste und den Author- oder Publish-Service auszuwählen, auf den Sie sie anwenden möchten.
   * Die IP-Zulassungsliste muss in Cloud Manager vorhanden sein, damit sie angewendet werden kann.
1. Klicken Sie auf **Anwenden** und bestätigen Sie Ihre Übermittlung.

## Aufheben der Anwendung von Zulassungslisten {#un-applying}

Benutzende mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können die folgenden Schritte ausführen, um die Anwendung einer IP-Zulassungsliste aufzuheben.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.
1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.
1. Gehen Sie im Bildschirm **Umgebungen** zur Seite mit den Umgebungsdetails und dann zur Tabelle **IP-Zulassungsliste**.
1. Ermitteln Sie die Zeile der IP-Zulassungsliste, deren Anwendung Sie aufheben möchten.
1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten ganz rechts in der Zeile.
1. Wählen Sie die Option **Anwendung aufheben** aus und bestätigen Sie Ihre Übermittlung.
