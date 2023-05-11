---
title: Benachrichtigungszentrum
description: Nutzen Sie das Benachrichtigungszentrum, um bequem auf Vorfälle und andere wichtige Informationen reagieren zu können.
hidefromtoc: true
hide: true
exl-id: d5a95ac4-aa88-44d5-ba02-7c9702050208
source-git-commit: 3aa753fb5cc5130ced7e9baafde63e8825394dce
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 0%

---

# Benachrichtigungszentrum {#notification-center}

>[!NOTE]
>Diese Funktion wurde noch nicht veröffentlicht.

AEM als Cloud Service sendet Benachrichtigungen bei kritischen Vorfällen, die sofortiges Handeln erfordern, sowie proaktive Empfehlungen für Optimierungen. Beispiele sind eine blockierte Warteschlange oder ein ablaufender Berechtigungssatz; Der vollständige Satz von Benachrichtigungstypen kann im [Tabelle unten](#supported-notification-types), die sich mit der Zeit ausweiten wird.

Diese Benachrichtigungen können für den Empfang sowohl per E-Mail als auch unter dem Benachrichtigungs-Widget konfiguriert werden. Der Zugriff erfolgt über das Glockensymbol oben rechts in der gesamten Adobe Experience Cloud.

Wenn eine Benachrichtigung empfangen wird, kann darauf geklickt werden, um AEM Benachrichtigungszentrum von as a Cloud Service mit einem Popup zu öffnen, in dem ein zusätzlicher Kontext angezeigt wird, der die Aktion für einen Kunden erklärt.

Zusätzlich zur Anzeige von Informationen über die gerade angeklickte Benachrichtigung dient das Benachrichtigungszentrum als Drehscheibe, über den Sie den Satz aktueller und älterer Benachrichtigungen anzeigen und verwalten können. <!-- It can be accessed directly at the url TBD (Alexandru: I'm intentionally keeping it TBD for now so customers don't find it) -->

Im Notification Center werden zwei allgemeine Benachrichtigungskategorien angezeigt:

1. Operative Vorfälle - Ein Ereignis ist aufgetreten, das in der Regel eine schnelle Lösung erfordert. Beispielsweise das Auflösen einer blockierten Warteschlange.
1. Proaktive Empfehlungen - Adobe empfiehlt, in naher Zukunft Maßnahmen zu ergreifen. So können Sie beispielsweise aufhören, auf eine veraltete Benutzeroberfläche zu verweisen.

Siehe [Tabelle unten](#supported-notification-types) für die derzeit unterstützten Benachrichtigungen.

Im Benachrichtigungszentrum können Sie ein bestimmtes Programm und eine bestimmte Umgebung auswählen, die eine Filterung dieses Bereichs bewirken.

## Konfiguration {#configuration}

Gehen Sie wie folgt vor, um Benachrichtigungen zu konfigurieren:

1. Erstellen Sie die folgenden Produktprofile wie beschrieben. [in diesem Artikel](/help/journey-onboarding/notification-profiles.md), wobei diesen Profilen auch die entsprechenden Adoben-IDs aus Ihrer Organisation zugewiesen werden. Auf diese Weise kann ein Administrator bestimmen, welche Benutzer für den Erhalt dieser Benachrichtigungen qualifiziert sind.
1. Jeder im vorherigen Schritt zugewiesene Benutzer kann konfigurieren, wie er seine Benachrichtigungen erhalten möchte. Im [Seite &quot;Experience Cloud-Voreinstellungen&quot;](https://experience.adobe.com/preferences/notification-section), stellen Sie sicher, dass das Experience Manager-Abonnement aktiviert ist, und **Operative Vorfälle** und **Proaktive Empfehlungen** -Kontrollkästchen sind sowohl für die In-App- als auch für die E-Mail-Spalte ausgewählt (siehe Abbildung unten). Darüber hinaus wird empfohlen, den Abschnitt E-Mails auf **Sofortige Benachrichtigungen** so werden Benachrichtigungen sofort bei einem Vorfall empfangen.

![Konfigurieren von Abonnements](/help/operations/assets/configure-subscriptions.png)

>[!NOTE]
>Benachrichtigungen funktionieren auf Organisationsebene, sodass Abonnenten Benachrichtigungen für alle Programme und Umgebungen innerhalb dieser Programme erhalten.

## Detaillierter Benutzerfluss {#detailed-user-flow}

Durch Klicken auf die E-Mail gelangen Sie zum Benachrichtigungszentrum mit einem Popup-Fenster, in dem der Kontext der angeklickten Benachrichtigung sowie in einigen Fällen Links zu zusätzlichen Informationen angezeigt werden, die beschreiben, wie Korrekturmaßnahmen ergriffen werden können.

![Details zu Vorfällen](/help/operations/assets/incident-details.png)

Klicken Sie auf **Weitere Infos** -Link navigiert den Benutzer zu diesem Artikel, in dem auf die Benachrichtigung in der unten stehenden Tabelle verwiesen werden kann, der Hinweise zu den zu ergreifenden Maßnahmen enthält.

Im Benachrichtigungszentrum wird eine Liste weiterer aktueller Benachrichtigungen angezeigt. Es wird empfohlen, dass Sie mithilfe der Aktionsliste eine Benachrichtigung bestätigen, um der Adobe mitzuteilen, dass Ihr Unternehmen über die Aufgabe informiert ist, und die Benachrichtigung später auflösen, wenn Abhilfemaßnahmen ergriffen wurden.

![Benachrichtigungsliste](/help/operations/assets/notification-list.png)

In den meisten Fällen sollte die Benachrichtigung den erforderlichen Kontext bieten, um das Problem zu beheben. Wenn jedoch Fragen zur Adobe-Unterstützung vorliegen, können Sie auf die **Support kontaktieren** im Benachrichtigungs-Popup-Fenster. Dadurch wird ein Formular eingeblendet, in dem Sie die Frage beschreiben und zur Erstellung des Support-Tickets einreichen können. Das Formular enthält auch einen Verweis auf die spezifische Benachrichtigung, sodass ein Support-Mitarbeiter der Adobe den entsprechenden Kontext hat.

![Support kontaktieren 1](/help/operations/assets/contact-support1.png)

![Support kontaktieren 2](/help/operations/assets/contact-support2.png)

Wie alle Support-Tickets wird sie im [Registerkarte &quot;Adobe Admin Console-Support-Fälle&quot;](https://helpx.adobe.com/enterprise/using/support-for-enterprise.html), wo Sie sie verfolgen und zusätzliche Kommentare hinzufügen können.

![Admin Console-Support](/help/operations/assets/admin-console-support.png)

## Welche Benachrichtigungen werden angezeigt? {#which-notification}

AEM as a Cloud Service verfügt über mehrere Arten von Benachrichtigungen, aber nur eine Teilmenge wird im Benachrichtigungszentrum angezeigt, wie in der unten stehenden Tabelle dargestellt.

| Benachrichtigungstyp | Beschreibung | Konfiguration | Wird im Benachrichtigungszentrum angezeigt |
|---|---|---|---|
| Operative Vorfälle | Kritische Vorfälle, die sofortiges Handeln erfordern | Benutzer, der dem Produktprofil &quot;Incident Notification - Cloud Service&quot;zugewiesen ist, Kontrollkästchen &quot;Operative Vorfälle&quot;aktiviert in [Experience Cloud-Voreinstellungen](https://experience.adobe.com/preferences) | X |
| Proaktive Empfehlungen | Zu planende Optimierungen | Benutzer, der dem Produktprofil &quot;Proaktive Benachrichtigung - Cloud Service&quot;zugewiesen ist, Kontrollkästchen &quot;Proaktive Empfehlungen&quot;in [Experience Cloud-Voreinstellungen](https://experience.adobe.com/preferences) | X |
| Cloud Manager-Pipeline-Status | Informationen zum Zustand Ihrer Pipelines | Benutzer mit den Rollen Business Owner, Programm-Manager oder Deployment Manager, Kontrollkästchen &quot;Sonstige&quot;in [Experience Cloud-Voreinstellungen](https://experience.adobe.com/preferences) |  |

## Unterstützte Benachrichtigungstypen {#supported-notification-types}

In der folgenden Tabelle sind die derzeit unterstützten Benachrichtigungstypen aufgeführt.

| Benachrichtigungstyp | Verwandtes Produktprofil | Korrektive Aktion |
|---|---|---|
| Blockierte Replikationswarteschlange | Vorfall | Heben Sie die Blockierung der Warteschlange auf, indem Sie den Anweisungen im Abschnitt [Replikationsdokumentation](/help/operations/replication.md#troubleshooting) |
| S2S-Zertifikat ablaufen | Proaktiv | Erfahren Sie im Abschnitt [Dokumentation zum Generieren von Zugriffstoken für serverseitige APIs](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials) |

