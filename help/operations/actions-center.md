---
title: Aktionszentrum
description: Nutzen Sie das Aktionszentrum, um bequem auf Vorfälle und andere wichtige Informationen reagieren zu können
exl-id: d5a95ac4-aa88-44d5-ba02-7c9702050208
feature: Operations
role: Admin
source-git-commit: 1bfa9ff24d3515a450216f3569b1e8b0b1e31ecc
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 98%

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

Um den Empfang von Benachrichtigungs-E-Mails des Aktionszentrums zu konfigurieren, erstellen Sie die unter [Benachrichtungsprofile](/help/journey-onboarding/notification-profiles.md) beschriebenen Produktprofile, nämlich „Benachrichtigung bei Vorfällen – Cloud Service“ und „Proaktive Benachrichtigung – Cloud Service“. Weisen Sie diesen Profilen auch die entsprechenden Adobe-IDs aus Ihrer Organisation zu. Auf diese Weise kann ein Admin bestimmen, welche Personen für den Erhalt dieser Benachrichtigungs-E-Mails qualifiziert sind.

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
|---------------------------------|-----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------|
| Operative Vorfälle | Kritische Vorfälle, die sofortiges Handeln erfordern | Benutzerin bzw. Benutzer, die/der dem Produktprofil „Benachrichtigung bei Vorfällen – Cloud Service“ zugewiesen ist | X |
| Proaktive Empfehlungen | Zu planende Optimierungen | Benutzerin bzw. Benutzer, die/der dem Produktprofil „proaktive Benachrichtigung – Cloud Service“ zugewiesen ist | X |
| Cloud Manager-Pipeline-Status | Informationen zum Zustand Ihrer Pipelines | Benutzende mit den Rollen „Geschäftsinhaber“, „Programm-Manager“ oder „Bereitstellungs-Manager“ und aktiviertem Kontrollkästchen „Sonstige“ in den [Experience Cloud-Voreinstellungen](https://experience.adobe.com/preferences), wie in [Benachrichtigungen](/help/implementing/cloud-manager/notifications.md). |                           |

## Unterstützte Benachrichtigungstypen {#supported-notification-types}

In der folgenden Tabelle sind die Benachrichtigungsarten aufgeführt, die derzeit im Aktionszentrum unterstützt werden. Benachrichtigungen sind derzeit auf Produktionsumgebungen beschränkt.

| Benachrichtigungstyp | Verwandtes Produktprofil | Korrekturmaßnahmen |
|---------------------------------|-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Blockierte Replikations-Warteschlange | Vorfall | Heben Sie die Blockierung der Warteschlange auf, indem Sie den Anweisungen in der [Replikations-Dokumentation](/help/operations/replication.md#troubleshooting) folgen |
| Ungültige persistierte GraphQL-Abfrage | Vorfall | Korrigieren Sie die ungültige GraphQL-Abfrage, indem Sie auf die [Dokumentation zur Fehlerbehebung bei persistierten GraphQL-Abfragen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/headless/graphql-api/persisted-queries-troubleshoot.html?lang=de) verweisen |
| Traffic-Spitze am Ursprung | Vorfall | Schützen Sie Ihren Ursprung, indem Sie Traffic-Filterregeln zur Ratenbegrenzung konfigurieren, die bei niedrigeren Schwellenwerten ausgelöst werden als die Warnung bei standardmäßiger Traffic-Spitze am Ursprung.  Weitere Informationen finden Sie im Abschnitt [Blockieren von DoS- und DDoS-Angriffen mithilfe von Traffic-Regeln](/help/security/traffic-filter-rules-including-waf.md#blocking-dos-and-ddos-attacks-using-traffic-filter-rules) in der Dokumentation zu den Traffic-Filterregeln, die auf ein Tutorial verweist. |
| Ausgelöste Regeln für CDN-Traffic-Filter | Vorfall | Wenn die passende Traffic-Filterregel einen Angriff widerspiegelt und Ihre Site diesen Traffic nicht blockiert, schützen Sie Ihre Site, indem Sie eine Traffic-Filterregel im Blockierungsmodus konfigurieren. Weitere Informationen finden Sie im Abschnitt [Schützen von Websites mit Traffic-Filterregeln (einschließlich WAF-Regeln)](/help/security/traffic-filter-rules-including-waf.md#tutorial-protecting-websites) in der Dokumentation zu den Traffic-Filterregeln, wo auf ein Tutorial verwiesen wird. |
| Fehler bei der Splunk-Protokollweiterleitung | Vorfall | Überprüfen Sie, ob Ihr Splunk-Endpunkt funktioniert und über Ihre AEM Cloud Service-Umgebung erreichbar ist. Weitere Informationen zur Protokollweiterleitung finden Sie in der [Dokumentation zur Splunk-Protokollweiterleitung](/help/implementing/developing/introduction/logging.md#splunk-logs). Wenn Sie Hilfe bei der Fehlerbehebung benötigen oder Änderungen an Ihrer Protokollierungskonfiguration vornehmen müssen, erstellen Sie ein Support-Ticket bei Adobe. |
| Seiten enthalten eine große Anzahl von Knoten | Proaktiv | Reduzieren Sie die Gesamtanzahl der Knoten auf einer Seite. Siehe die [Dokumentation zur Seitenkomplexität](https://experienceleague.adobe.com/de/docs/experience-manager-pattern-detection/table-of-contents/pcx) | |
| Große Anzahl an laufenden Workflow-Instanzen | Proaktiv | Beenden Sie laufende Workflows, die nicht mehr benötigt werden. Erfahren Sie, wie Sie einen [Bereinigungsauftrag konfigurieren](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/operations/maintenance). |               |
| Ablaufendes S2S-Zertifikat | Proaktiv | Erfahren Sie in der Dokumentation [Erstellen von Zugriffstoken für Server-seitige APIs](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials), wie Sie eine Berechtigung aktualisieren können. | Hohe Verbindungsanzahl | Proaktiv | Erfahren Sie mehr über das Pooling von Verbindungen in der [Dokumentation über das Pooling von Verbindungen im Zusammenhang mit erweiterten Netzwerkfunktionen](/help/security/configuring-advanced-networking.md#connection-pooling-advanced-networking) |
| Veraltete Dienstbenutzerzuordnung | Proaktiv | Erfahren Sie, wie Sie das neuere Format der Sling-Dienstbenutzerzuordnung verwenden, wie in [Best Practices für die Sling-Dienstbenutzerzuordnung und Dienstbenutzerdefinition](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/security/best-practices-for-sling-service-user-mapping-and-service-user-definition) beschrieben. |
| Hohe Verbindungsanzahl | Proaktiv | Erfahren Sie mehr über das Pooling von Verbindungen in der [Dokumentation zu den erweiterten Netzwerkfunktionen](/help/security/configuring-advanced-networking.md#connection-pooling-advanced-networking) |  |
| Benutzende, die direkt zu benutzerdefinierten Gruppen hinzugefügt wurden | Proaktiv | Benutzende müssen relevanten IMS-Gruppen hinzugefügt werden, und diese IMS-Gruppen müssen als Mitglieder von AEM-Gruppen hinzugefügt werden. Verwenden Sie die [Best Practices für IMS](/help/security/ims-support.md). | |
| Fehlende JCR-Inhalte | Proaktiv | Fügen Sie den fehlenden JCR-Inhaltsknoten hinzu. Siehe die [Dokumentation zu Assets Content Validator](https://experienceleague.adobe.com/de/docs/experience-manager-pattern-detection/table-of-contents/acv) | |
| Abgeschlossene Workflows werden nicht bereinigt | Proaktiv | Minimieren Sie die Anzahl der Workflow-Instanzen und optimieren Sie die Leistung, indem Sie mehr als 90 Tage alte Workflow-Instanzen bereinigen. Erfahren Sie, wie Sie [Wartungsaufgaben konfigurieren](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/operations/maintenance). | |
| Fehlender Sling-Ressourcentyp in Seite | Proaktiv | Fügen Sie den Knoten des fehlenden Sling-Ressourcentyps hinzu. Siehe die [Dokumentation zu Assets Content Validator](https://experienceleague.adobe.com/de/docs/experience-manager-pattern-detection/table-of-contents/acv) | |
| Langsame Abfrage | Proaktiv | Beheben Sie langsame Abfragen, indem Sie die richtigen Indexdefinitionen definieren, wie im [JCQ-Abfrage-Datenblatt](https://experienceleague.adobe.com/docs/experience-manager-65/assets/JCR_query_cheatsheet-v1.1.pdf) vorgeschlagen. |