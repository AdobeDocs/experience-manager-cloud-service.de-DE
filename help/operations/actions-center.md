---
title: Aktionszentrum
description: Nutzung des Aktionszentrums, um bequem Maßnahmen bei Vorfällen und anderen wichtigen Informationen zu ergreifen
exl-id: d5a95ac4-aa88-44d5-ba02-7c9702050208
source-git-commit: 4adae6ffe45dcd2b80d7d199fc29a806ce5e78c4
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 25%

---

# Aktionszentrum {#actions-center}

AEM als Cloud Service sendet E-Mail-Benachrichtigungen an das Aktionszentrum, wenn kritische Zwischenfälle auftreten, die sofortiges Handeln erfordern, und proaktive Empfehlungen für Optimierungen. Beispiele dafür sind eine blockierte Warteschlange oder ein ablaufender Satz von Anmeldeinformationen. Der vollständige Satz der Benachrichtigungstypen von Actions Center kann im Abschnitt [unten stehende Tabelle](#supported-notification-types), die sich im Laufe der Zeit ausweiten wird.

Wenn eine E-Mail-Benachrichtigung des Aktionszentrums empfangen wird, kann darauf geklickt werden, um AEM Aktionszentrum von as a Cloud Service mit einem Popup zu öffnen, in dem ein zusätzlicher Kontext angezeigt wird, der die Aktion für einen Kunden erklärt.

Zusätzlich zur Anzeige von Informationen über die gerade angeklickte E-Mail-Benachrichtigung dient das Aktionszentrum als Drehscheibe, über den Sie den Satz aktueller und älterer Benachrichtigungen anzeigen und verwalten können. <!-- It can be accessed directly at the url TBD (Alexandru: I'm intentionally keeping it TBD for now so customers do not find it) -->

Im Aktionszentrum werden zwei allgemeine Benachrichtigungskategorien angezeigt:

1. Operative Vorfälle: Ein Ereignis ist aufgetreten, für das normalerweise eine sofortige Lösung erforderlich ist. Beispiel: Beheben einer blockierten Warteschlange.
1. Proaktiv Empfehlungen: Adobe hat eine Empfehlung für eine Aktion, die eine Kundin oder ein Kunde in naher Zukunft durchführen sollte. Es kann sich beispielsweise darum handeln, nicht mehr auf eine veraltete Benutzeroberfläche zu verweisen.

Siehe [unten stehende Tabelle](#supported-notification-types) für die Benachrichtigungen, die derzeit im Aktionszentrum unterstützt werden.

Im Aktionszentrum können Sie ein bestimmtes Programm und eine bestimmte Umgebung auswählen, die sich durch Filtern nach diesem Bereich auswirkt.

## Konfiguration {#configuration}

Erstellen Sie zum Konfigurieren des Empfangs von E-Mail-Benachrichtigungen des Aktionszentrums die beschriebenen Produktprofile [in diesem Artikel](/help/journey-onboarding/notification-profiles.md), d. h. Benachrichtigung bei Vorfällen - Cloud Service und proaktive Benachrichtigung - Cloud Service. Weisen Sie diesen Profilen auch die entsprechenden Adoben-IDs aus Ihrer Organisation zu. Auf diese Weise kann ein Administrator bestimmen, welche Benutzer für den Erhalt dieser E-Mail-Benachrichtigungen qualifiziert sind.

>[!NOTE]
>Aktionen Center E-Mail-Benachrichtigungen funktionieren auf Organisationsebene, sodass Abonnenten Benachrichtigungen für alle Programme und Umgebungen innerhalb dieser Programme erhalten.

## Detaillierter Benutzerfluss {#detailed-user-flow}

Durch Klicken auf die E-Mail gelangen Sie zum Aktionszentrum mit einem Popup-Fenster, in dem der Kontext der angeklickten Benachrichtigung sowie in einigen Fällen Links zu weiteren Informationen angezeigt werden, die beschreiben, wie Korrekturmaßnahmen ergriffen werden können. Sie können auch direkt auf das Aktionszentrum zugreifen unter [https://experience.adobe.com/aem/actions-center](https://experience.adobe.com/aem/actions-center/), wo Sie das entsprechende Programm und die entsprechende Umgebung auswählen können.

![Details zu Vorfällen](/help/operations/assets/incident-details.png)

Klicken Sie auf **Weitere Infos** Der Link navigiert zum Benutzer zu diesem Artikel, in dem der Benachrichtigungstyp im [Tabelle mit unterstützten Benachrichtigungstypen](#supported-notification-types) im Folgenden finden Sie Leitlinien zu den zu ergreifenden Maßnahmen.

Im Aktionszentrum wird eine Liste weiterer aktueller Benachrichtigungen angezeigt. Es wird empfohlen, mithilfe der Aktionsliste eine Benachrichtigung zu bestätigen, um der Adobe mitzuteilen, dass Ihr Unternehmen über die Aufgabe informiert ist, und die Benachrichtigung später aufzulösen, wenn Abhilfemaßnahmen ergriffen wurden.

![Benachrichtigungsliste](/help/operations/assets/notification-list.png)

In den meisten Fällen sollte das Popup-Fenster den erforderlichen Kontext zur Lösung des Problems bieten. Wenn jedoch Fragen zur Adobe-Unterstützung vorliegen, können Sie auf die **Support kontaktieren** im Popup-Fenster. Dadurch wird ein Formular eingeblendet, in dem Sie die Frage beschreiben und zur Erstellung eines Support-Tickets einreichen können. Das Formular enthält auch einen Verweis auf die spezifische Benachrichtigung, sodass ein Support-Mitarbeiter der Adobe den entsprechenden Kontext hat.

![Support 1 kontaktieren](/help/operations/assets/contact-support1.png)

![Support 2 kontaktieren](/help/operations/assets/contact-support2.png)

Wie alle Support-Tickets wird es [auf der Registerkarte „Support-Fälle“ in der Adobe Admin Console](https://helpx.adobe.com/de/enterprise/using/support-for-enterprise.html) angezeigt, wo Sie es verfolgen und zusätzliche Kommentare hinzufügen können.

![Support für die Admin Console](/help/operations/assets/admin-console-support.png)

## Welche Benachrichtigungen werden angezeigt? {#which-notification}

AEM as a Cloud Service verfügt über mehrere Arten von Benachrichtigungen, aber im Aktionszentrum wird nur eine Teilmenge angezeigt, wie in der unten stehenden Tabelle dargestellt.

| Benachrichtigungstyp | Beschreibung | Vorgehensweise bei der Konfiguration | Wird im Aktionszentrum angezeigt |
|---|---|---|---|
| Operative Vorfälle | Kritische Vorfälle, die sofortiges Handeln erfordern | Benutzer, der dem Produktprofil &quot;Incident Notification - Cloud Service&quot;zugewiesen ist | X |
| Proaktive Empfehlungen | Zu planende Optimierungen | Dem Produktprofil &quot;Proaktive Benachrichtigung - Cloud Service&quot;zugewiesener Benutzer | X |
| Cloud Manager-Pipeline-Status | Informationen zum Zustand Ihrer Pipelines | Benutzende mit den Rollen „Geschäftsinhaber“, „Programm-Manager“ oder „Bereitstellungs-Manager“ und aktiviertem Kontrollkästchen „Sonstige“ in den [Experience Cloud-Voreinstellungen](https://experience.adobe.com/preferences), als [hier beschrieben](/help/implementing/cloud-manager/notifications.md). |   |

## Unterstützte Benachrichtigungstypen {#supported-notification-types}

In der folgenden Tabelle sind die Benachrichtigungstypen aufgeführt, die derzeit im Aktionszentrum unterstützt werden. Benachrichtigungen sind derzeit auf Produktionsumgebungen beschränkt.

| Benachrichtigungstyp | Verwandtes Produktprofil | Korrekturmaßnahmen |
|---|---|---|
| Blockierte Replikations-Warteschlange | Vorfall | Heben Sie die Blockierung der Warteschlange auf, indem Sie den Anweisungen in der [Replikations-Dokumentation](/help/operations/replication.md#troubleshooting) folgen |
| Ablaufendes S2S-Zertifikat | Proaktiv | Erfahren Sie in der Dokumentation [Erstellen von Zugriffstoken für Server-seitige APIs](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials), wie Sie eine Berechtigung aktualisieren können. |

