---
title: Verwalten von benutzerdefinierten Domain-Namen
description: Erfahren Sie, wie Sie mit Cloud Manager benutzerdefinierte Domain-Namen anzeigen, aktualisieren, ersetzen und löschen können.
exl-id: 6cab8cf2-22c0-4f4b-9c54-a1425e74ddd0
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 4e887b753eaf09e104c68484792f00dcb08ee304
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 68%

---


# Benutzerdefinierte Domänennamen verwalten {#managing-custom-domain-names}

Mit Cloud Manager können Sie benutzerdefinierte Domain-Namen anzeigen, aktualisieren, ersetzen und löschen.

## Benutzerdefinierten Domänennamen anzeigen und aktualisieren {#view-and-update}

Über Sie das Menü **Anzeigen und aktualisieren** können Sie die Details eines oder aller Ihrer benutzerdefinierten Domain-Namen anzeigen.

**So zeigen Sie einen benutzerdefinierten Domänennamen an und aktualisieren ihn:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Navigieren Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Identifizieren Sie die Zeile des benutzerdefinierten Domänennamens, den Sie anzeigen oder aktualisieren möchten.

1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten ganz rechts in der Zeile.

1. Wählen Sie die Option **Anzeigen und aktualisieren** aus.

## Aktualisieren des SSL-Zertifikats eines benutzerdefinierten Domänennamens {#update-cert}

Sie können [die gleichen Schritte zum Anzeigen und Aktualisieren eines benutzerdefinierten Domain-Namens ausführen](#view-and-update), um das SSL-Zertifikat eines benutzerdefinierten Domain-Namens zu aktualisieren.

>[!NOTE]
>
>Das SSL-Zertifikat muss gültig sein, [bereits konfiguriert](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) und den benutzerdefinierten Domänennamen enthalten, den Sie aktualisieren.

## Benutzerdefinierten Domänennamen löschen {#deleting}

Benutzerinnen oder Benutzer mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können Cloud Manager verwenden, um einen benutzerdefinierten Domain-Namen zu löschen.

### Löschen Sie den benutzerdefinierten Domänennamen aus allen verknüpften Umgebungen {#delete-cdn-all}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie über den Bildschirm **Umgebungen** zur Seite **Domain-Einstellungen**.

1. Identifizieren Sie die Zeile des benutzerdefinierten Domänennamens, den Sie löschen möchten.

1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten ganz rechts in der Zeile.

1. Wählen Sie **Löschen** aus.

1. Bestätigen Sie Ihre Übermittlung.

### Löschen eines benutzerdefinierten Domänennamens aus einer bestimmten Umgebung {#delete-cdn-specific}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.
1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.
1. Navigieren Sie auf der Seite **Umgebungen** zu einem Detailbildschirm der gewünschten Umgebung.
1. Ermitteln Sie in der Tabelle mit den Domain-Namen die Zeile, in der der benutzerdefinierte Domain-Name aufgeführt ist, den Sie löschen möchten.
1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten ganz rechts in der Zeile.
1. Wählen Sie **Löschen** aus.
1. Bestätigen Sie Ihre Übermittlung.
