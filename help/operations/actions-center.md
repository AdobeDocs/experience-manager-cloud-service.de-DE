---
title: Aktionszentrum
description: Nutzen Sie das Aktionszentrum, um bequem auf Vorfälle und andere wichtige Informationen reagieren zu können
exl-id: d5a95ac4-aa88-44d5-ba02-7c9702050208
source-git-commit: df10d8d210877e166312f66d5c4e74dbe771446a
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 92%

---

# Aktionszentrum {#actions-center}

AEM as a Cloud Service sendet Aktionszentrums-Benachrichtigungs-E-Mails bei kritischen Vorfällen, die sofortiges Handeln erfordern, sowie proaktive Empfehlungen für Optimierungen. Beispiele sind eine blockierte Warteschlange oder ein ablaufender Satz von Anmeldeinformationen. Die vollständige Liste der Aktionszentrums-Benachrichtigungstypen ist in der [Tabelle unten](#supported-notification-types) zu sehen, die im Laufe der Zeit erweitert wird.

Wer eine Benachrichtigungs-E-Mail vom Aktionszentrum empfängt, kann darauf klicken, um das Aktionszentrum von AEM as a Cloud Service mit einem Popup zu öffnen, in dem ein zusätzlicher Kontext angezeigt wird, der einer Kundin bzw. einem Kunden die Aktion erklärt.

Zusätzlich zur Anzeige von Informationen über die gerade angeklickte Benachrichtigungs-E-Mail dient das Aktionszentrum als Drehscheibe, über den Sie den Satz aktueller und älterer Benachrichtigungen anzeigen und verwalten können. <!-- It can be accessed directly at the url TBD (Alexandru: I'm intentionally keeping it TBD for now so customers do not find it) -->

Im Aktionszentrum werden zwei übergeordnete Benachrichtigungskategorien angezeigt:

1. Operative Vorfälle: Ein Ereignis ist aufgetreten, für das normalerweise eine sofortige Lösung erforderlich ist. Beispiel: Beheben einer blockierten Warteschlange.
1. Proaktiv Empfehlungen: Adobe hat eine Empfehlung für eine Aktion, die eine Kundin oder ein Kunde in naher Zukunft durchführen sollte. Es kann sich beispielsweise darum handeln, nicht mehr auf eine veraltete Benutzeroberfläche zu verweisen.

In der [Tabelle unten](#supported-notification-types) finden Sie die derzeit im Aktionszentrum unterstützten Benachrichtigungen.

Im Aktionszentrum können Sie ein bestimmtes Programm und eine bestimmte Umgebung auswählen, wodurch in diesem Umfang gefiltert wird.

## Konfiguration {#configuration}

Um den Empfang von Aktionszentrums-Benachrichtigungs-E-Mail zu konfigurieren, erstellen Sie die in diesem Artikel beschriebenen [Produktprofile](/help/journey-onboarding/notification-profiles.md), nämlich Benachrichtigung bei Vorfällen – Cloud Service und proaktive Benachrichtigung – Cloud Service. Weisen Sie diesen Profilen auch die entsprechenden Adobe-IDs aus Ihrer Organisation zu. Auf diese Weise kann ein Admin bestimmen, welche Personen für den Erhalt dieser Benachrichtigungs-E-Mails qualifiziert sind.

>[!NOTE]
>Aktionszentrums-Benachrichtigungs-E-Mails werden auf Organisationsebene erstellt, sodass die Abonnierenden Benachrichtigungen für alle Programme und Umgebungen innerhalb dieser Programme erhalten.

## Detaillierter Benutzerfluss {#detailed-user-flow}

Durch Klicken auf die E-Mail gelangen Sie zum Aktionszentrum mit einem Popup-Fenster, in dem der Kontext der angeklickten Benachrichtigung sowie in einigen Fällen Links zu zusätzlichen Informationen angezeigt werden, die beschreiben, wie Korrekturmaßnahmen ergriffen werden können. Sie können auch direkt auf das Aktionszentrum zugreifen unter [https://experience.adobe.com/aem/actions-center](https://experience.adobe.com/aem/actions-center/), wo Sie das entsprechende Programm und die entsprechende Umgebung auswählen können.

![Details zu Vorfällen](/help/operations/assets/incident-details.png)

Wenn Sie auf den Link **Mehr erfahren** klicken, gelangen Sie zu diesem Artikel, in dem der Benachrichtigungstyp in der Tabelle [Unterstützte Benachrichtigungstypen](#supported-notification-types) unten aufgeführt ist, die Hinweise zu den zu ergreifenden Maßnahmen enthält.

Im Aktionszentrum wird eine Liste weiterer aktueller Benachrichtigungen angezeigt. Es wird empfohlen, dass Sie mithilfe der Aktionsliste eine Benachrichtigung bestätigen, um Adobe mitzuteilen, dass Ihr Unternehmen über die Aufgabe informiert ist, und damit die Benachrichtigung später aufgelöst wird, wenn Korrekturmaßnahmen ergriffen worden sind.

![Benachrichtigungsliste](/help/operations/assets/notification-list.png)

In den meisten Fällen sollte das Popup den erforderlichen Kontext bieten, um das Problem zu beheben. Wenn Sie jedoch Fragen an den Adobe-Support haben, können Sie auf den Link **Support kontaktieren** im Popup klicken. Dadurch wird ein Formular eingeblendet, in dem Sie die Frage beschreiben und zur Erstellung eines Support-Tickets einreichen können. Das Formular enthält auch einen Verweis auf die spezifische Benachrichtigung, sodass die Kontaktperson des Adobe-Supports über den entsprechenden Kontext verfügt.

![Support 1 kontaktieren](/help/operations/assets/contact-support1.png)

![Support 2 kontaktieren](/help/operations/assets/contact-support2.png)

Wie alle Support-Tickets wird es [auf der Registerkarte „Support-Fälle“ in der Adobe Admin Console](https://helpx.adobe.com/de/enterprise/using/support-for-enterprise.html) angezeigt, wo Sie es verfolgen und zusätzliche Kommentare hinzufügen können.

![Support für die Admin Console](/help/operations/assets/admin-console-support.png)

## Welche Benachrichtigungen werden angezeigt? {#which-notification}

AEM as a Cloud Service verfügt über mehrere Arten von Benachrichtigungen, aber nur eine Teilmenge wird im Aktionszentrum angezeigt, wie in der unten stehenden Tabelle dargestellt.

| Benachrichtigungstyp | Beschreibung | Vorgehensweise bei der Konfiguration | Wird im Aktionszentrum angezeigt |
|---|---|---|---|
| Operative Vorfälle | Kritische Vorfälle, die sofortiges Handeln erfordern | Benutzerin bzw. Benutzer, die/der dem Produktprofil „Benachrichtigung bei Vorfällen – Cloud Service“ zugewiesen ist | X |
| Proaktive Empfehlungen | Zu planende Optimierungen | Benutzerin bzw. Benutzer, die/der dem Produktprofil „proaktive Benachrichtigung – Cloud Service“ zugewiesen ist | X |
| Cloud Manager-Pipeline-Status | Informationen zum Zustand Ihrer Pipelines | Benutzende mit den Rollen „Geschäftsinhaber“, „Programm-Manager“ oder „Bereitstellungs-Manager“ und aktiviertem Kontrollkästchen „Sonstige“ in den [Experience Cloud-Voreinstellungen](https://experience.adobe.com/preferences), wie [hier beschrieben](/help/implementing/cloud-manager/notifications.md). |   |

## Unterstützte Benachrichtigungstypen {#supported-notification-types}

In der folgenden Tabelle sind die Benachrichtigungsarten aufgeführt, die derzeit im Aktionszentrum unterstützt werden. Benachrichtigungen sind derzeit auf Produktionsumgebungen beschränkt.

| Benachrichtigungstyp | Verwandtes Produktprofil | Korrekturmaßnahmen |
|---------------------------------|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Blockierte Replikations-Warteschlange | Vorfall | Heben Sie die Blockierung der Warteschlange auf, indem Sie den Anweisungen in der [Replikations-Dokumentation](/help/operations/replication.md#troubleshooting) folgen |
| Ungültige persistierte GraphQL-Abfrage | Vorfall | Korrigieren Sie die ungültige GraphQL-Abfrage, indem Sie auf die [Dokumentation zur Fehlerbehebung bei persistierten GraphQL-Abfragen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/headless/graphql-api/persisted-queries-troubleshoot.html?lang=de) verweisen |
| Ablaufendes S2S-Zertifikat | Proaktiv | Erfahren Sie in der Dokumentation [Erstellen von Zugriffstoken für Server-seitige APIs](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials), wie Sie eine Berechtigung aktualisieren können. | High Connection Count | Proaktiv | Erfahren Sie mehr über Verbindungspools in [Dokumentation zu Verbindungspools zusammen mit erweiterter Vernetzung](/help/security/configuring-advanced-networking.md#connection-pooling-advanced-networking) |
| Traffic-Spitze beim Ursprung | Vorfall | Protect Sie Ihre Herkunft, indem Sie Regeln für Traffic-Filter mit Ratenbegrenzung konfigurieren, die bei der Warnung zur Herkunft einen Trigger erreichen, der unter den standardmäßigen Traffic-Spitzen liegt.  Siehe [Blockieren von DoS- und DoS-Angriffen mithilfe von Traffic-Regeln](/help/security/traffic-filter-rules-including-waf.md#blocking-dos-and-ddos-attacks-using-traffic-filter-rules) in der Dokumentation zu Traffic-Filterregeln , in der auf ein Tutorial verwiesen wird. |
