---
title: Verwalten von benutzerdefinierten Domain-Namen
description: Erfahren Sie, wie Sie mit Cloud Manager benutzerdefinierte Domain-Namen anzeigen, aktualisieren, ersetzen und löschen können.
exl-id: 6cab8cf2-22c0-4f4b-9c54-a1425e74ddd0
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 2d1382c84d872719332986baa5829d1623d9d9a6
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 88%

---


# Verwalten von benutzerdefinierten Domain-Namen {#managing-custom-domain-names}

Mit Cloud Manager können Sie benutzerdefinierte Domain-Namen bearbeiten, aktualisieren, ersetzen und löschen.

## Bearbeiten der Konfiguration eines benutzerdefinierten Domain-Namens {#view-and-update}

Es könnte aus folgenden Gründen erforderlich sein, dass Sie die Konfiguration eines benutzerdefinierten Domain-Namens in Adobe Cloud Manager bearbeiten:

* **Wechseln von Umgebungen**: Um die richtige Konfiguration anzuwenden, je nachdem, ob Sie Inhalte für Endbenutzende (Veröffentlichen) oder interne Benutzende (Autor) bereitstellen.
* **Sicherheits-Updates**: Zum Aktualisieren auf ein neueres SSL-Zertifikat, um die Sicherheit oder Compliance zu verbessern.
* **Ändern der Bereitstellungsstrategie**: Um sicherzustellen, dass das richtige SSL-Zertifikat auf eine bestimmte Umgebung angewendet wird, um eine ordnungsgemäße Verschlüsselung und den Site-Zugriff zu gewährleisten.

**So bearbeiten Sie die Konfiguration eines benutzerdefinierten Domain-Namens:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Klicken Sie oben links auf der Seite auf das Hamburgersymbol, damit das linke Navigationsmenü angezeigt wird.
1. Klicken Sie unter der Überschrift **Services** auf **CDN-Konfigurationen**.
1. Klicken Sie auf der Seite **CDN-Konfigurationen** am Ende einer Zeile, deren CDN Sie bearbeiten möchten, auf das Symbol ![Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) .
1. Klicken Sie auf **Bearbeiten**.
1. Gehen Sie im Dialogfeld **CDN-Konfiguration bearbeiten** wie folgt vor:
   * Wählen Sie in der Dropdownliste **Ebene** die Ebene (Publish oder Vorschau) aus, die Sie verwenden möchten.
   * Wählen Sie in der Dropdownliste **SSL-Zertifikat** das SSL-Zertifikat aus, das Sie verwenden möchten.
1. Klicken Sie auf **Aktualisieren**.


## Aktualisieren des SSL-Zertifikats eines benutzerdefinierten Domain-Namens {#update-cert}

Sie können [die gleichen Schritte zum Anzeigen und Aktualisieren eines benutzerdefinierten Domain-Namens ausführen](#view-and-update), um das SSL-Zertifikat eines benutzerdefinierten Domain-Namens zu aktualisieren.

>[!NOTE]
>
>Das SSL-Zertifikat muss gültig und [bereits konfiguriert](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md) sein und den benutzerdefinierten Domain-Namen enthalten, den Sie aktualisieren.


## Löschen eines benutzerdefinierten Domain-Namens {#deleting}

Benutzende mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** können Cloud Manager verwenden, um einen benutzerdefinierten Domain-Namen zu löschen.

### Löschen eines benutzerdefinierten Domain-Namens aus allen zugehörigen Umgebungen {#delete-cdn-all}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie über den Bildschirm **Umgebungen** zur Seite **Domain-Einstellungen**.

1. Ermitteln Sie die Zeile, in der der benutzerdefinierte Domain-Name aufgeführt ist, den Sie löschen möchten.

1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten ganz rechts in der Zeile.

1. Wählen Sie **Löschen** aus.

1. Bestätigen Sie Ihre Übermittlung.


### Löschen eines benutzerdefinierten Domain-Namens aus einer bestimmten Umgebung {#delete-cdn-specific}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.
1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.
1. Navigieren Sie von der Seite **Umgebungen** zum Bildschirm „Umgebungsdetails“ der betreffenden Umgebung.
1. Ermitteln Sie in der Tabelle mit den Domain-Namen die Zeile, in der der benutzerdefinierte Domain-Name aufgeführt ist, den Sie löschen möchten.
1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten ganz rechts in der Zeile.
1. Wählen Sie **Löschen** aus.
1. Bestätigen Sie Ihre Übermittlung.
