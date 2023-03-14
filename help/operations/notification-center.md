---
title: Benachrichtigungszentrum
description: Nutzen Sie das Benachrichtigungszentrum, um bequem auf Vorfälle und andere wichtige Informationen reagieren zu können.
hidefromtoc: true
source-git-commit: a5977c667d831c47d41cd86b68e9196fbe726899
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---


# Benachrichtigungszentrum {#notification-center}

>[!NOTE]
>Diese Funktion wurde noch nicht veröffentlicht.

Nach der Konfiguration sendet AEM als Cloud Service Benachrichtigungen zu wichtigen Informationen, für die Kunden Maßnahmen ergreifen sollen. Beispiele für Benachrichtigungen sind eine blockierte Warteschlange oder ein ablaufender Satz von Anmeldedaten. Die vollständigen Benachrichtigungstypen können im Abschnitt [Tabelle unten](#current-notification-types)und im Laufe der Zeit erweitert werden. Benachrichtigungen werden sowohl per E-Mail als auch als neuer Eintrag unter dem Benachrichtigungs-Widget empfangen, auf den Sie durch Klicken auf das Glockensymbol oben rechts in der gesamten Adobe Experience Cloud zugreifen können. Benachrichtigungseinstellungen können konfiguriert werden.

Wenn eine Benachrichtigung empfangen wird, kann darauf geklickt werden, um AEM Benachrichtigungszentrum von as a Cloud Service mit einem Popup zu öffnen, in dem ein zusätzlicher Kontext angezeigt wird, der die empfohlene Aktion für einen Kunden erklärt.

Zusätzlich zur Anzeige von Informationen über die gerade angeklickte Benachrichtigung dient das Benachrichtigungszentrum als Drehscheibe, über den Sie den Satz aktueller und älterer Benachrichtigungen anzeigen und verwalten können. <!-- It can be accessed directly at the url TBD (Alexandru: I'm intentionally keeping it TBD for now so customers don't find it) -->

Es gibt zwei allgemeine Benachrichtigungskategorien:

1. Vorfälle - Ein Ereignis ist aufgetreten, für das normalerweise eine sofortige Lösung erforderlich ist. Beispiel: Beheben einer blockierten Warteschlange
1. Proaktiv - Adobe empfiehlt, in naher Zukunft Maßnahmen zu ergreifen. So können Sie beispielsweise aufhören, auf eine veraltete Benutzeroberfläche zu verweisen.

Siehe [Tabelle unten](#current-notification-types) für die derzeit unterstützten Benachrichtigungen.

Im Bildschirm &quot;Benachrichtigungszentrum&quot;können Sie ein bestimmtes Programm und eine bestimmte Umgebung auswählen, die so gefiltert werden, dass sie diesen Bereich abdecken.

## Konfiguration {#configuration}

Gehen Sie wie folgt vor, um den Empfang von Benachrichtigungen zu konfigurieren:

1. Erstellen Sie die folgenden Produktprofile wie beschrieben. [in diesem Artikel](/help/journey-onboarding/user-groups.md), indem Sie diesen Profilen die entsprechenden Adoben-IDs aus Ihrer Organisation zuweisen.
1. Legen Sie die Konfigurationseinstellungen für die Benachrichtigung fest. [Auf dieser Seite](https://experience.adobe.com/preferences/notification-section), stellen Sie sicher, dass die Experience Manager-Anmeldung aktiviert ist und die **sonstige** aktiviert ist. Darüber hinaus wird empfohlen, den Abschnitt E-Mails auf **Sofortige Benachrichtigungen** sodass Sie Benachrichtigungen sofort nach einem Vorfall erhalten.

>[!NOTE]
>Abonnements werden auf Organisationsebene erstellt, sodass Abonnenten Benachrichtigungen für alle Programme und Umgebungen innerhalb dieser Programme erhalten.

## Detaillierter Benutzerfluss {#detailed-user-flow}

Durch Klicken auf die E-Mail gelangen Sie zum Benachrichtigungszentrum mit einem Popup-Fenster, in dem der Kontext der angeklickten Benachrichtigung sowie in einigen Fällen Links zu zusätzlichen Informationen angezeigt werden, die beschreiben, wie Korrekturmaßnahmen ergriffen werden können.

![Details zu Vorfällen](/help/operations/assets/incident-details.png)

Klicken Sie auf **Weitere Infos** -Link navigiert den Benutzer zu diesem Artikel, in dem auf die Benachrichtigung in der unten stehenden Tabelle verwiesen werden kann, der Hinweise zu den zu ergreifenden Maßnahmen enthält.

Im Benachrichtigungszentrum wird eine Liste weiterer aktueller Benachrichtigungen angezeigt. Es wird empfohlen, dass Sie mithilfe der Aktionsliste eine Benachrichtigung bestätigen, um der Adobe mitzuteilen, dass Ihr Unternehmen über die Aufgabe informiert ist, und die Benachrichtigung später auflösen, wenn Abhilfemaßnahmen ergriffen wurden.

![Benachrichtigungsliste](/help/operations/assets/notification-list.png)

In den meisten Fällen sollte die Benachrichtigung den erforderlichen Kontext bieten, um das Problem zu beheben. Wenn jedoch Fragen zur Adobe-Unterstützung vorliegen, können Sie auf die **Support kontaktieren** im Benachrichtigungs-Popup-Fenster. Dadurch wird ein Formular eingeblendet, in dem Sie die Frage beschreiben und zur Erstellung des Support-Tickets einreichen können. Das Formular enthält auch einen Verweis auf die spezifische Benachrichtigung, sodass ein Support-Mitarbeiter der Adobe über den entsprechenden Kontext verfügt.

![Support kontaktieren 1](/help/operations/assets/contact-support1.png)

![Support kontaktieren 2](/help/operations/assets/contact-support2.png)

Wie alle Support-Tickets wird sie im [Registerkarte &quot;Adobe Admin Console-Support-Fälle&quot;](https://helpx.adobe.com/enterprise/using/support-for-enterprise.html), wo Sie sie verfolgen und zusätzliche Kommentare hinzufügen können.

![Admin Console-Support](/help/operations/assets/admin-console-support.png)

## Aktuelle Benachrichtigungstypen {#current-notification-types}

In der folgenden Tabelle sind die derzeit unterstützten Benachrichtigungstypen aufgeführt

| Benachrichtigungstyp | Verwandtes Produktprofil | Korrektive Aktion |
|---|---|---|
| Blockierte Replikationswarteschlange | Vorfall | Heben Sie die Blockierung der Warteschlange auf, indem Sie den Anweisungen im Abschnitt [Replikationsdokumentation](/help/operations/replication.md#troubleshooting) |
| S2S-Zertifikat ablaufen | Proaktiv | Erfahren Sie im Abschnitt [Dokumentation zum Generieren von Zugriffstoken für serverseitige APIs](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials) |
