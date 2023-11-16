---
title: Benachrichtigungen
description: Erfahren Sie, wie Sie mithilfe des Adobe Experience Cloud-Benachrichtigungssystems Informationen zu Pipeline-Bereitstellungen erhalten.
exl-id: c1c740b0-c873-45a8-9518-a856db2be75b
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 79%

---


# Benachrichtigungen {#notifications}

Erfahren Sie, wie Sie von Cloud Manager über wichtige Ereignisse benachrichtigt werden.

## Benachrichtigungen in Cloud Manager {#cloud-manager-notifications}

[!UICONTROL Cloud Manager] sendet Ihnen zu Beginn einer Produktionsbereitstellung beim Start und beim Abschluss der Produktions-Pipeline (erfolgreich oder nicht erfolgreich) Benachrichtigungen.

Diese Benachrichtigungen werden über das [!UICONTROL Experience Cloud]-Benachrichtigungssystem an Benutzer mit den Rollen **Geschäftsinhaber**, **Programm-Manager** und **Bereitstellungs-Manager** gesendet.

Die Benachrichtigungen werden in einer Seitenleiste der [!UICONTROL Cloud Manager]-Benutzeroberfläche und überall in Adobe [!UICONTROL Experience Cloud] angezeigt. Das Glockensymbol in der Kopfzeile zeigt ein Badge, wenn es neue Benachrichtigungen für Sie gibt.

![Benachrichtigungssymbol](assets/notifications-bell-badged.png)

Klicken Sie auf das Glockensymbol, um die Seitenleiste zu öffnen und die Benachrichtigungen anzuzeigen. Die Registerkarte **Benachrichtigungen** in der Seitenleiste listet die neuesten Benachrichtigungen wie beispielsweise Bereitstellungsbestätigungen auf. Benachrichtigungen beziehen sich auf Ihre Umgebungen.

![Benachrichtigungsseitenleiste](assets/notifications-activities.png)

Die Registerkarte **Ankündigungen** enthält Ankündigungen zu Adobe-Produkten. Ankündigungen beziehen sich auf das Produkt.

![Benachrichtigungsseitenleiste](assets/notificaitons-announcements.png)

Klicken Sie auf eine Benachrichtigung oder Mitteilung, um deren Details anzuzeigen. Benachrichtigungen, die mit Aktivitäten wie Pipeline-Bereitstellungen verknüpft sind, führen Sie zu den Details dieser Aktivität, beispielsweise dem Pipeline-Ausführungsfenster.

Klicken Sie auf **Alle anzeigen** unten im Bedienfeld, um alle Ankündigungen in Ihrem Posteingang anzuzeigen.

Klicken Sie auf **Alle als gelesen markieren** -Option am unteren Rand des Bedienfelds, um alle ungelesenen Benachrichtigungen als gelesen zu markieren und das Glockensymbol-Badging zu löschen.

## Konfiguration von Benachrichtigungen {#configuration}

Sie können einstellen, wie Sie welche Benachrichtigungen erhalten möchten.

Klicken Sie auf das Zahnradsymbol oben in der Benachrichtigungsseitenleiste.

![Symbol für Benachrichtigungseinstellungen](assets/notifications-configuration.png)

Dadurch öffnet sich das Fenster **Experience Cloud-Einstellungen**, in dem Sie Benachrichtigungsabonnements auswählen und festlegen können, wie Sie Benachrichtigungen erhalten.

### Abonnements {#subscriptions}

Mit den Abonnements legen Sie fest, welche Benachrichtigungen Sie für welche Produkte erhalten.

![Abonnements für Benachrichtigungen](assets/notifications-subscriptions.png)

Standardmäßig erhalten Sie alle Benachrichtigungen für alle Produkte sowohl in der Anwendung als auch per E-Mail. Klicken Sie auf den Pfeil neben einem Produktnamen, um die detaillierten Optionen anzuzeigen und die Benachrichtigungstypen zu definieren, die Sie für dieses Produkt erhalten. Oder aktivieren oder deaktivieren Sie die Optionen auf Produktebene, um alle Optionen für das Produkt auszuwählen/abzuwählen.

![Anpassung des Benachrichtigungsabonnements](assets/notifications-subscriptions-customize.png)

### Priorität {#priority}

Prioritätswarnhinweise werden mit einem **HOCH**-Tag gekennzeichnet und können so konfiguriert werden, dass sie ausschließlich als Warnhinweise empfangen werden. Im Abschnitt **Priorität** können Sie festlegen, welche Kategorien als Prioritätsbenachrichtigungen eingestuft werden.

![Benachrichtigungspriorität](assets/notifications-priority.png)

Verwenden Sie die Dropdown-Liste, um die Liste der Kategorien zu erweitern, die als prioritär eingestuft werden. Klicken Sie auf das X neben den Kategorienamen, um sie zu entfernen.

### Warnhinweise {#alerts}

Warnhinweise werden für einige Sekunden in der oberen rechten Ecke des Fensters angezeigt. Im Abschnitt **Warnhinweise** können Sie festlegen, für welche Benachrichtigungen Sie Warnhinweise erhalten möchten.

![Benachrichtigungs-Warnhinweise](assets/notifications-alerts.png)

Sie können das Verhalten der Warnhinweise definieren.

* **Warnhinweise anzeigen für**: Definiert die Arten von Benachrichtigungen, die Warnhinweise auslösen.
* **Warnhinweise sollen am Bildschirm angezeigt werden, bis ich sie schließe**: Legt fest, ob die Warnhinweise bestehen bleiben sollen, bis Sie sie aktiv deaktivieren.
* **Dauer**: Legt fest, wie lange ein Warnhinweis auf dem Bildschirm eingeblendet werden soll, außer Sie haben ausgewählt, dass ein Warnhinweis auf dem Bildschirm verbleiben soll.

### E-Mails {#emails}

Benachrichtigungen sind in der Web-Benutzeroberfläche aller Adobe [!UICONTROL Experience Cloud]-Lösungen verfügbar. Sie können auch im Abschnitt **E-Mails** festlegen, dass diese Benachrichtigungen per E-Mai gesendet werden sollen.

![Benachrichtigungs-E-Mails](assets/notifications-emails.png)

Standardmäßig werden keine E-Mails versendet. Sie haben für den E-Mail-Empfang folgende Wahlmöglichkeiten:

* Sofort
* Täglich
* Wöchentlich

Wenn die **sofortige Benachrichtigung** ausgewählt ist, werden für jede Benachrichtigung sofort E-Mails versendet. Bei einer **täglichen Zusammenfassung** können Sie die Uhrzeit und bei einer **wöchentlichen Zusammenfassung** können Sie den Tag und die Uhrzeit des Versands auswählen.