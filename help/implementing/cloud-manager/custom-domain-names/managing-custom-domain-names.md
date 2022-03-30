---
title: Verwalten von benutzerdefinierten Domain-Namen
description: Erfahren Sie, wie Sie mit Cloud Manager benutzerdefinierte Domänennamen anzeigen, aktualisieren, ersetzen und löschen können.
source-git-commit: 4604b5fad59524a05dc7addf16c70246a14cfea1
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 32%

---


# Verwalten von benutzerdefinierten Domain-Namen {#managing-custom-domain-names}

Mit Cloud Manager können Sie benutzerdefinierte Domänennamen anzeigen, aktualisieren, ersetzen und löschen.

## Anzeigen und Aktualisieren {#view-and-update}

Verwenden Sie die **Anzeigen und Aktualisieren** -Menü, um die Details Ihrer benutzerdefinierten Domänennamen anzuzeigen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zum **Umgebungen** -Bildschirm aus dem **Übersicht** Seite.

1. Identifizieren Sie die Zeile des benutzerspezifischen Domänennamens, den Sie anzeigen oder aktualisieren möchten.

1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten ganz rechts in der Zeile.

1. Wählen Sie die Option **Anzeigen und Aktualisieren** aus.

## Aktualisieren des SSL-Zertifikats des benutzerdefinierten Domain-Namens {#update-cert}

Sie können [dieselben Schritte zum Anzeigen und Aktualisieren eines benutzerdefinierten Domänennamen](#view-and-update) , um das SSL-Zertifikat eines benutzerdefinierten Domänennamens zu aktualisieren.

>[!NOTE]
>
>Das SSL-Zertifikat muss gültig sein; [bereits konfiguriert,](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) und enthalten den benutzerdefinierten Domänennamen, den Sie aktualisieren.

##  Löschen eines anwenderdefinierten Domain-Namens {#deleting}

Ein Benutzer mit der **Business Owner** oder **Bereitstellungsmanager** -Rolle kann Cloud Manager verwenden, um einen benutzerdefinierten Domänennamen zu löschen.

### Löschen eines benutzerdefinierten Domain-Namens aus allen zugehörigen Umgebungen {#delete-cdn-all}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zum **Umgebungen** -Bildschirm aus dem **Übersicht** Seite.

1. Navigieren Sie im Bildschirm **Umgebungen** zur Seite mit den **Domain-Einstellungen**.

1. Identifizieren Sie die Zeile des benutzerspezifischen Domänennamens, den Sie löschen möchten.

1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten ganz rechts in der Zeile.

1. Wählen Sie **Löschen** aus.
   ![](/help/implementing/cloud-manager/assets/cdn/cdn-delete.png)

1. Bestätigen Sie Ihre Übermittlung.

### Löschen eines benutzerdefinierten Domain-Namens aus einer bestimmten Umgebung {#delete-cdn-specific}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.
1. Navigieren Sie zum **Umgebungen** -Bildschirm aus dem **Übersicht** Seite.
1. Aus dem **Umgebungen** Seite, navigieren Sie zum Detailbildschirm der gewünschten Umgebung.
1. Geben Sie in der Tabelle mit den Domänennamen die Zeile des benutzerspezifischen Domänennamens an, den Sie löschen möchten.
1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten ganz rechts in der Zeile.
1. Wählen Sie **Löschen** aus.
1. Bestätigen Sie Ihre Übermittlung.
