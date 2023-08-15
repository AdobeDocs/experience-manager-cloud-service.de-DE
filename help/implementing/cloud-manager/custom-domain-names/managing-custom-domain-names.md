---
title: Verwalten von benutzerdefinierten Domain-Namen
description: Erfahren Sie, wie Sie mit Cloud Manager benutzerdefinierte Domain-Namen anzeigen, aktualisieren, ersetzen und löschen können.
exl-id: 6cab8cf2-22c0-4f4b-9c54-a1425e74ddd0
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 96%

---

# Verwalten von benutzerdefinierten Domain-Namen {#managing-custom-domain-names}

Mit Cloud Manager können Sie benutzerdefinierte Domänennamen anzeigen, aktualisieren, ersetzen und löschen.

## Anzeigen und Aktualisieren {#view-and-update}

Über Sie das Menü **Anzeigen und aktualisieren** können Sie die Details eines oder aller Ihrer benutzerdefinierten Domain-Namen anzeigen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Ermitteln Sie die Zeile, in der der benutzerdefinierte Domain-Name aufgeführt ist, den Sie anzeigen oder aktualisieren möchten.

1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten ganz rechts in der Zeile.

1. Wählen Sie die Option **Anzeigen und aktualisieren** aus.

## Aktualisieren des SSL-Zertifikats des benutzerdefinierten Domain-Namens {#update-cert}

Sie können [die gleichen Schritte zum Anzeigen und Aktualisieren eines benutzerdefinierten Domain-Namens ausführen](#view-and-update), um das SSL-Zertifikat eines benutzerdefinierten Domain-Namens zu aktualisieren.

>[!NOTE]
>
>Das SSL-Zertifikat muss gültig und [bereits konfiguriert](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) sein und den benutzerdefinierten Domain-Namen enthalten, den Sie aktualisieren.

## Löschen eines anwenderdefinierten Domain-Namens {#deleting}

Benutzerinnen oder Benutzer mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können Cloud Manager verwenden, um einen benutzerdefinierten Domain-Namen zu löschen.

### Löschen eines benutzerdefinierten Domain-Namens aus allen zugehörigen Umgebungen {#delete-cdn-all}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Navigieren Sie im Bildschirm **Umgebungen** zur Seite mit den **Domain-Einstellungen**.

1. Ermitteln Sie die Zeile, in der der benutzerdefinierte Domain-Name aufgeführt ist, den Sie löschen möchten.

1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten ganz rechts in der Zeile.

1. Wählen Sie **Löschen** aus.

   ![Löschen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/assets/cdn/cdn-delete.png)

1. Bestätigen Sie Ihre Übermittlung.

### Löschen eines benutzerdefinierten Domain-Namens aus einer bestimmten Umgebung {#delete-cdn-specific}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.
1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.
1. Gehen Sie von der Seite **Umgebungen** zum Bildschirm „Umgebungsdetails“ der betreffenden Umgebung.
1. Ermitteln Sie in der Tabelle mit den Domain-Namen die Zeile, in der der benutzerdefinierte Domain-Name aufgeführt ist, den Sie löschen möchten.
1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten ganz rechts in der Zeile.
1. Wählen Sie **Löschen** aus.
1. Bestätigen Sie Ihre Übermittlung.
