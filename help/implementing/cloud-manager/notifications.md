---
title: Benachrichtigungen
description: Erfahren Sie, wie Sie mithilfe des Adobe Experience Cloud-Benachrichtigungssystems Informationen zu Pipelinebereitstellungen erhalten.
exl-id: c1c740b0-c873-45a8-9518-a856db2be75b
source-git-commit: 0de041211c8257d920bcf354593b3caa2db43572
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 12%

---


# Benachrichtigungen {#notifications}

Erfahren Sie, wie Sie von Cloud Manager über wichtige Ereignisse benachrichtigt werden.

## Benachrichtigungen in Cloud Manager {#cloud-manager-notifications}

[!UICONTROL Cloud Manager] sendet Ihnen zu Beginn einer Produktionsimplementierung Benachrichtigungen, wenn eine Produktions-Pipeline (erfolgreich oder nicht erfolgreich) gestartet und abgeschlossen wird.

Diese Benachrichtigungen werden über die [!UICONTROL Experience Cloud] Benachrichtigungssystem für Benutzer im **Business Owner**, **Programm-Manager** und **Bereitstellungsmanager** Rollen.

Die Benachrichtigungen werden in einer Seitenleiste der [!UICONTROL Cloud Manager]-Benutzeroberfläche und überall in Adobe [!UICONTROL Experience Cloud] angezeigt. Das Glockensymbol in der Kopfzeile zeigt ein Badge, wenn es neue Benachrichtigungen für Sie gibt.

![Benachrichtigungssymbol](assets/notifications-bell-badged.png)

Klicken Sie auf das Glockensymbol, um die Seitenleiste zu öffnen und die Benachrichtigungen anzuzeigen. Die **Benachrichtigungen** in der Seitenleiste werden die neuesten Benachrichtigungen, z. B. Bereitstellungsbestätigungen, aufgelistet. Benachrichtigungen beziehen sich auf Ihre Umgebungen.

![Benachrichtigungsseitenleiste](assets/notifications-activities.png)

Die **Mitteilungen** enthält Produktankündigungen für Adoben. Mitteilungen beziehen sich auf das Produkt.

![Benachrichtigungsseitenleiste](assets/notificaitons-announcements.png)

Klicken Sie auf eine Benachrichtigung oder Mitteilung, um deren Details anzuzeigen. Benachrichtigungen, die mit Aktivitäten wie Pipelinebereitstellungen verknüpft sind, führen Sie zu den Details dieser Aktivität, z. B. zum Pipeline-Ausführungsfenster.

Klicken Sie auf **Alle anzeigen** unten im Bedienfeld, um alle Ankündigungen in Ihrem Posteingang anzuzeigen.

Klicken Sie auf **Alle als gelesen markieren** -Option am unteren Rand des Bedienfelds, um alle ungelesenen Benachrichtigungen als gelesen zu markieren und das Glockensymbol-Badging zu löschen.

## Benachrichtigungskonfiguration {#configuration}

Sie können anpassen, wie Sie Benachrichtigungen erhalten und welche Benachrichtigungen Sie erhalten.

Klicken Sie auf das Zahnradsymbol oben in der Benachrichtigungsseitenleiste.

![Symbol für Benachrichtigungseinstellungen](assets/notifications-configuration.png)

Dadurch wird die **Experience Cloud-Voreinstellungen** -Fenster, in dem Sie Ihre Benachrichtigungs-Abonnements und den Empfang Ihrer Benachrichtigungen definieren können.

### Abonnements {#subscriptions}

Abonnements definieren, für welche Produkte Sie Benachrichtigungen erhalten und welche Benachrichtigungen.

![Abonnements für Benachrichtigungen](assets/notifications-subscriptions.png)

Standardmäßig erhalten Sie alle Benachrichtigungen für alle Produkte. Klicken Sie auf **Anpassen** neben einem Produkt , um die Benachrichtigungstypen zu definieren, die Sie für dieses Produkt erhalten.

![Anpassung von Benachrichtigungsanmeldungen](assets/notifications-subscriptions-customize.png)

### Priorität {#priority}

Vorrangige Warnhinweise werden mit einem **HOCH** -Tag und können so konfiguriert werden, dass sie ausschließlich als Warnhinweise empfangen werden. Im **Priorität** können Sie festlegen, welche Kategorien als Prioritätsbenachrichtigungen gelten.

![Benachrichtigungspriorität](assets/notifications-priority.png)

Verwenden Sie die Dropdown-Liste, um die Liste der Kategorien, die als prioritär gelten, hinzuzufügen. Klicken Sie auf das X neben den Kategorienamen, um sie zu entfernen.

### Warnhinweise {#alerts}

Warnhinweise werden einige Sekunden lang in der oberen rechten Ecke des Fensters angezeigt. Verwenden Sie die **Warnhinweise** um festzulegen, für welche Benachrichtigungen Sie Warnungen erhalten.

![Benachrichtigungen](assets/notifications-alerts.png)

Sie können das Verhalten der Warnhinweise definieren.

* **Warnhinweise anzeigen für** - Definiert die Benachrichtigungstypen, die von Trigger angezeigt werden
* **Warnhinweise sollten auf dem Bildschirm bleiben, bis ich sie schließe** - Steuert, ob die Warnhinweise bestehen bleiben sollen, wenn Sie sie nicht aktiv verwerfen
* **Dauer** - Definiert, wie lange der Warnhinweis auf dem Bildschirm bleiben soll, wenn Sie nicht ausgewählt haben, dass er auf dem Bildschirm angezeigt werden soll.

## E-Mails {#emails}

Benachrichtigungen sind in der gesamten Adobe in der Web-Benutzeroberfläche verfügbar [!UICONTROL Experience Cloud] Lösungen. Sie können sich auch dafür entscheiden, dass diese Benachrichtigungen per E-Mail im **E-Mails** Abschnitt.

![Benachrichtigungs-E-Mails](assets/notifications-emails.png)

Standardmäßig werden keine E-Mails gesendet. Sie können E-Mails wie folgt empfangen:

* Sofort
* Täglich
* Wöchentlich

Wann **Sofortige Benachrichtigungen** ausgewählt ist, werden für jede Benachrichtigung sofort E-Mails gesendet. Für **Tägliche Zusammenfassung** und **Wöchentliche Digest** Sie können wählen, wann Ihre tägliche Zusammenfassung gesendet wird und an welchem Tag und wann Ihre wöchentliche Zusammenfassung gesendet wird.