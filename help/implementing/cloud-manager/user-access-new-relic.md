---
title: New Relic One
description: Erfahren Sie mehr über den APM-Service (Application Performance Monitoring) von New Relic One für AEM as a Cloud Service und wie Sie darauf zugreifen können.
exl-id: 9fa0c5eb-415d-4e56-8136-203d59be927e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 087285bf1023f844fe8d63817e0202276e01c411
workflow-type: tm+mt
source-wordcount: '2274'
ht-degree: 71%

---


# New Relic One {#user-access}

Erfahren Sie mehr über den APM-Service (Application Performance Monitoring) von New Relic One für AEM as a Cloud Service und wie Sie darauf zugreifen können.

## Über New Relic One {#introduction}

Adobe erachtet die Überwachbarkeit, Verfügbarkeit und Leistungsfähigkeit Ihrer Anwendung als außerordentlich wichtig. AEM as a Cloud Service bietet Zugriff auf die New Relic One-Überwachung, sodass Teams im Rahmen des Standardproduktangebots umfassende Einblicke in Metriken zur System- und Umgebungsleistung erhalten.

In diesem Dokument wird beschrieben, wie Sie den Zugriff auf Funktionen zur Leistungsüberwachung von New Relic One-Anwendungen (APM) in AEM as a Cloud Service-Umgebungen verwalten. Die effektive Verwaltung dieser Funktionen unterstützt eine optimale Leistung und maximiert die Vorteile von AEM as a Cloud Service.

Wenn ein neues Produktionsprogramm erstellt wird, wird automatisch ein mit Ihrem AEM as a Cloud Service-Programm verknüpftes New Relic One-Unterkonto erstellt. [Dieses Unterkonto muss aktiviert werden](#activate-sub-account), damit die Aufnahme von Daten beginnen kann.

## Funktionen {#transaction-monitoring}

New Relic One APM für AEM as a Cloud Service hat viele Funktionen.

* Direkter Zugriff auf ein dediziertes New Relic One-Konto.

* Instrumentierter New Relic One APM-Agent, der exakte Methodenaufrufe mit Zeilennummern anzeigt, einschließlich externer Abhängigkeiten und Datenbanken.

* Ganzheitliche Leistungsoptimierung durch Kombination von Schlüsselmetriken aus der Überwachung auf Infrastrukturebene und der Überwachung der Anwendung (Adobe Experience Manager).

* Automatische Änderungsverfolgung für Cloud Manager-Pipeline-Ausführungen, AEM-Upgrades und Code-Wiederherstellungsvorgänge. Mit diesen Trackern können Teams Bereitstellungen direkt in New Relic One mit Änderungen der Anwendungsleistung korrelieren.

## Aktivieren Ihres New Relic One-Unterkontos {#activate-sub-account}

Für ein neu erstelltes Programm wird ein New Relic One-Unterkonto für Sie erstellt. Sie müssen es jedoch aktivieren, damit es Daten aufnehmen kann. Diese Aktivierung erfolgt nicht automatisch. Führen Sie die folgenden Schritte aus, um Ihr Unterkonto zu aktivieren.

>[!NOTE]
>
>Ein Benutzer mit der Rolle **Geschäftsinhaber** muss angemeldet sein, um das New Relic One-Unterkonto zu verwalten.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** auf das Programm, für das die New Relic One-Benutzenden verwaltet werden sollen.

1. Klicken Sie auf der Seite „Programmübersicht“ unten auf der Karte **Umgebungen** auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) und wählen Sie **New Relic aktivieren** aus.

   ![Benutzer verwalten](assets/newrelic-activate-sub-account.png)

   * Sie können auch auf die Option **Benutzer verwalten** zugreifen. Klicken Sie oben auf dem Bildschirm **Umgebungen** Ihres Programms auf das Symbol ![Smock more](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).

1. [Führen Sie eine Pipeline](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines) für dieselbe Umgebung bis zum erfolgreichen Abschluss aus, um die Aktivierung des Unterkontos abzuschließen.

Wenn das Unterkonto deaktiviert ist, werden keine Daten aufgenommen.

## Verwalten von New Relic One-Benutzenden {#manage-users}

Führen Sie diese Schritte aus, um die Benutzenden Ihres New Relic One-Unterkontos, das mit Ihrem AEM as a Cloud Service-Programm verbunden ist, zu definieren.

>[!NOTE]
>
>Eine Person muss mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** angemeldet sein, um New Relic One-Benutzende verwalten zu können.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, für das Sie Ihre New Relic One-Benutzenden verwalten möchten.

1. Klicken Sie auf der Seite „Programmübersicht“ unten auf der Karte **Umgebungen** auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) und wählen Sie **Benutzer verwalten** aus.

   ![Benutzer verwalten](assets/newrelic-manage-users.png)

   * Sie können auch auf die Option **Benutzer verwalten** zugreifen. Klicken Sie oben auf dem Bildschirm **Umgebungen** Ihres Programms auf das Symbol ![Smock more](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).

1. Geben Sie im Dialogfeld **New Relic-Benutzer verwalten** den Vor- und Nachnamen der Person ein, die Sie hinzufügen möchten, und klicken Sie auf die Schaltfläche **Hinzufügen**. Wiederholen Sie diesen Schritt für alle Benutzenden, die Sie hinzufügen möchten.

   ![Hinzufügen von Benutzenden](assets/newrelic-add-users.png)

1. Um einen New Relic One-Benutzer zu entfernen, klicken Sie auf die Schaltfläche Löschen am rechten Ende der Zeile für den Benutzer.

1. Klicken Sie auf **Speichern**, um die-Benutzenden zu erstellen.

Sobald die Benutzenden definiert sind, sendet New Relic eine Bestätigungs-E-Mail an jede Person, der Sie Zugriff gewährt haben, damit sie den Einrichtungsprozess abschließen und sich anmelden kann.

>[!NOTE]
>
>Wenn Sie die New Relic One-Benutzer verwalten, müssen Sie sich auch selbst als Benutzer hinzufügen. Die Rolle als **Geschäftsinhaber** oder **Bereitstellungs-Manager** reicht nicht aus, um Zugriff auf New Relic One zu erhalten.

## Aktivieren Ihres New Relic One-Benutzerkontos {#activate-user-account}

Nachdem ein New Relic One-Benutzerkonto, wie in [Verwalten von New Relic One-Benutzern](#manage-users) beschrieben, erstellt wurde, sendet New Relic diesen Benutzern eine Bestätigungs-E-Mail an die angegebene Adresse. Um diese Konten verwenden zu können, müssen Benutzende zunächst ihre Konten bei New Relic aktivieren, indem sie ihre Kennwörter zurücksetzen.

**Aktivieren Ihres New Relic One-Benutzerkontos**

1. Klicken Sie auf den Link in der E-Mail von New Relic.

1. Wählen Sie auf der Anmeldeseite von New Relic die Option **Kennwort vergessen?**.

   ![New Relic-Anmeldung](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Geben Sie die E-Mail-Adresse ein, an die Sie die Bestätigungs-E-Mail erhalten haben, und klicken Sie auf **Link zum Zurücksetzen senden**.

   ![E-Mail-Adresse eingeben](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. New Relic sendet Ihnen eine E-Mail mit einem Link zur Kontobestätigung.

Wenn Sie keine Bestätigungs-E-Mail von New Relic erhalten, finden Sie weitere Informationen im Abschnitt [Fehlerbehebung](#troubshooting).

## Zugriff auf New Relic One {#accessing-new-relic}

Nachdem Sie [Ihr New Relic-Konto aktiviert haben](#activate-account), können Sie über Cloud Manager oder direkt auf New Relic One zugreifen.

**Zugriff auf New Relic One über Cloud Manager**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, für das Sie auf New Relic One zugreifen möchten.

1. Klicken Sie auf der Seite „Programmübersicht“ unten auf der Karte **Umgebungen** auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) und wählen Sie **New Relic öffnen** aus.

   ![Benutzer verwalten](assets/newrelic-access.png)

   * Sie können auch auf New Relic zugreifen. Klicken Sie oben auf dem Bildschirm **Umgebungen** Ihres Programms auf das Symbol ![Smock more](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).

1. Melden Sie sich in der sich öffnenden neuen Browser-Registerkarte bei New Relic One an.

**So greifen Sie direkt auf New Relic One zu:**

1. Zur Anmeldeseite von [New Relic](https://login.newrelic.com/login).

1. Melden Sie sich bei New Relic One an.

### Verifizieren Ihrer E-Mail-Adresse {#verify-email}

Wenn Sie während der Anmeldung bei New Relic One aufgefordert werden, Ihre E-Mail-Adresse zu verifizieren, bedeutet dies, dass sie mit mehreren Konten verknüpft ist. Sie können auswählen, auf welches Konto zugegriffen werden soll.

Wenn Sie Ihre E-Mail-Adresse nicht verifizieren, versucht New Relic, Sie mit dem zuletzt erstellten Benutzereintrag anzumelden, der mit Ihrer E-Mail-Adresse verknüpft ist. Um zu vermeiden, dass Ihre E-Mail-Adresse bei jeder Anmeldung überprüft wird, klicken Sie im Anmeldebildschirm auf das Kontrollkästchen **Angaben speichern**.

Um weitere Hilfe zu erhalten, öffnen Sie ein Support-Ticket über das [AEM Support-Portal](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).

## Änderungs-Tracker verwenden {#change-tracker}

Cloud Manager sendet automatisch Änderungs-Tracker an New Relic One, wenn unterstützte Pipeline-Ausführungen, AEM-Upgrades und die Code-Wiederherstellung abgeschlossen sind. Diese Tracker werden als Änderungsereignisse in der Ansicht **Änderungsverfolgung** von New Relic angezeigt, sodass Ihr Team Bereitstellungen mit Änderungen bei der Anwendungsleistung, den Fehlerquoten und dem Durchsatz korrelieren kann.

<!-- See also [Introduction to change tracking](https://docs.newrelic.com/docs/change-tracking/overview/) and [Record and view deployments](https://docs.newrelic.com/docs/apm/apm-ui-pages/events/record-deployments/). -->

### Unterstützte Pipelines und Flüsse {#supported-pipelines}

Die folgenden Cloud Manager-Pipelines und die beiden letzten Flusstypen generieren in New Relic One Änderungs-Tracker:

| Pipeline-/Flusstyp | Beschreibung |
|---|---|
| **Full-Stack (CI_CD-Bereitstellung)** | Full-Stack-Pipeline-Ausführungen Die Ablaufverfolgung enthält den Pipeline-Namen und die Ausführungs-ID. |
| **Web-Stufen-Konfiguration** | Web-Stufen-Konfigurations-Pipeline-Ausführungen. Die Ablaufverfolgung enthält den Pipeline-Namen und die Ausführungs-ID. |
| **Frontend** | Frontend-Pipeline-Ausführungen. Die Ablaufverfolgung enthält den Pipeline-Namen und die Ausführungs-ID. |
| **config** | Pipeline-Ausführungen konfigurieren. Die Ablaufverfolgung enthält den Pipeline-Namen und die Ausführungs-ID. |
| **AEM-Update** | AEM-Versionsaktualisierungen. Beispielsweise von Version {} zu Version {}. Tracker werden erstellt, wenn das Änderungsereignis der Umgebung abgeschlossen ist. |
| **Code wiederherstellen** | Der Code stellt Vorgänge aus einem bestimmten Repository und einer bestimmten Verzweigung wieder her. |

>[!NOTE]
>
>Änderungs-Tracker werden derzeit nur für Skyline-Umgebungen unterstützt. Pipelines, die außerhalb des Bereichs liegen, wie z. B. Hochskalierungs-Pipelines und Service Pack-Pipelines, generieren keine Tracker.

### Anzeigen von Änderungs-Trackern in New Relic One {#view-change-trackers}

Nach Abschluss der Ausführung einer unterstützten Pipeline können Sie den entsprechenden Änderungs-Tracker in New Relic One anzeigen.

**So zeigen Sie Änderungs-Tracker in New Relic One an:**

1. [Greifen Sie über ](#accessing-new-relic) Cloud Manager oder direkt auf New Relic One zu.
1. Navigieren Sie zu **APM und Services** und wählen Sie die Anwendung für die entsprechende Umgebung aus.
1. Suchen Sie auf der Seite Anwendungszusammenfassung nach den Indikatoren für die Änderungsnachverfolgung im Diagramm. Bewegen Sie den Mauszeiger über einen Tracker, um Bereitstellungsdetails anzuzeigen.

   ![Ändern von Tracker-Indikatoren im Zeitdiagramm für Web-Transaktionen](/help/implementing/cloud-manager/assets/new-relic/new-relic-web-transactions-time.png)

1. Klicken Sie auf ein beliebiges Änderungsereignis in der Tabelle, um eine Detailansicht zu öffnen.

   ![Bedienfeld „Bereitstellungsattribute“ mit hervorgehobener DeepLink](/help/implementing/cloud-manager/assets/new-relic/new-relic-deeplink.png)URL <i>Detailansicht eines Änderungsereignisses.</i>

   Das **Details ändern** auf der rechten Seite zeigt unter anderem die Entität, den Zeitstempel, die Epoche, die Kategorie, die Bereitstellungs-ID und den API-Typ an.

   Für jeden Änderungs-Tracker, den Cloud Manager an New Relic One sendet **werden im Bedienfeld „Bereitstellungsattribute** unten rechts die folgenden Attribute angezeigt:

   | Attribut | Beschreibung |
   |---|---|
   | **version** | Eine Beschreibungszeichenfolge, die den Pipeline-Namen und die Ausführungs-ID enthält. |
   | **changelog** | Reserviert für zukünftige Verwendung. |
   | **commit** | Reserviert für zukünftige Verwendung. |
   | **deepLink** | Klicken Sie auf die URL, um zur Seite „Pipeline-Ausführung“ in Cloud Manager zurückzukehren. |

1. Um eine vollständige Liste der Änderungs-Tracker anzuzeigen, klicken Sie in der linken Seitenleiste unter **Ereignisse** auf **Änderungs-Tracking**.

   Die **Änderungsereignisse** Tabelle zeigt jede Bereitstellung mit ihrem Zeitstempel und ihrer Versionsbeschreibung.

   ![Tracking-Option für Änderungen mit Anzeige der Tabelle mit Änderungsereignissen](/help/implementing/cloud-manager/assets/new-relic/new-relic-change-tracking.png)

>[!TIP]
>
>Verwenden Sie Änderungs-Tracker zusammen mit den Leistungsindikatoren von New Relic One **Antwortzeit** und **Durchsatz**. Anhand dieser Indikatoren können Sie erkennen, ob eine bestimmte Bereitstellung Leistungsregressionen oder Verbesserungen mit sich gebracht hat. Sie können Metriken von vor und nach einer Bereitstellung direkt auf der Seite mit den Details zum Änderungsereignis vergleichen.

## Fehlerbehebung beim Benutzerzugriff auf New Relic One {#troubleshooting}

Wenn Sie als New Relic One-Benutzerin bzw. -Benutzer hinzugefügt wurden, wie unter [Verwalten von New Relic One-Benutzenden](#manage-users) beschrieben, und die ursprüngliche E-Mail zur Kontobestätigung nicht mehr finden können, führen Sie zur Fehlerbehebung die folgenden Schritte aus.

**Fehlerbehebung beim Benutzerzugriff auf New Relic One**

1. Navigieren Sie zur Anmeldeseite von New Relic unter [`login.newrelic.com/login`](https://login.newrelic.com/login).

1. Klicken Sie auf **[!UICONTROL Kennwort vergessen?]**.

   ![New Relic-Anmeldung](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Geben Sie die E-Mail-Adresse ein, mit der Ihr Konto erstellt wurde, und wählen Sie **Link zum Zurücksetzen senden**.

   ![E-Mail-Adresse eingeben](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. New Relic sendet Ihnen eine E-Mail mit einem Link zur Kontobestätigung.

Wenn Sie den Anmeldevorgang abgeschlossen haben und sich aufgrund von E-Mail- oder Kennwortfehlermeldungen nicht bei Ihrem Konto anmelden können, reichen Sie über die [Admin Console](https://adminconsole.adobe.com/) ein Support-Ticket ein.

Falls Sie keine E-Mail von New Relic erhalten, gehen Sie wie folgt vor:

* Überprüfen Sie Ihre [Spam-Filter](https://docs.newrelic.com/docs/accounts/accounts-billing/account-setup/create-your-new-relic-account/).
* [Fügen Sie New Relic gegebenenfalls zu Ihrer E-Mail-Zulassungsliste hinzu](https://docs.newrelic.com/docs/accounts/accounts/account-maintenance/account-email-settings/#email-whitelist).
* Wenn keiner dieser Vorschläge hilft, geben Sie Feedback zum Support-Ticket.

## Nutzungshinweise {#usage-notes}

* Es können maximal 30 Benutzende hinzugefügt werden. Wenn die maximale Anzahl von Benutzenden erreicht wurde, entfernen Sie Benutzende, um neue Benutzende hinzufügen zu können.
* Benutzende, die zu New Relic hinzugefügt werden, weisen den Typ **Allgemein** auf. Weitere Informationen finden Sie in der [ New Relic-Dokumentation](https://docs.newrelic.com/docs/accounts/accounts-billing/new-relic-one-user-management/user-type/).
* AEM as a Cloud Service bietet nur die New Relic One APM-Lösung, aber keine Unterstützung für Warnhinweise, Protokollierung oder API-Integrationen.

>[!NOTE]
>
>Wenn in Ihrem New Relic One-Unterkonto mindestens 30 Tage lang keine Aktivität einer **Benutzeranmeldung** erkannt wurde, wird der APM-Agent angehalten. Daten werden nicht von AEM Cloud Service an New Relic gesendet. *Daten werden erst dann erneut gesendet, wenn Ihr Unterkonto wieder aktiviert wurde.*
>
>Führen Sie die Schritte aus dem Abschnitt [Aktivieren Ihres New Relic One-Unterkontos](#activate-sub-account) in diesem Dokument aus, um Ihr New Relic One-Unterkonto erneut zu aktivieren.

Um weitere Hilfe oder zusätzliche Anleitungen zu New Relic One-Angeboten für Ihr Programm in AEM as a Cloud Service zu erhalten, öffnen Sie ein Support-Ticket über das [AEM-Support-Portal](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).

## Häufig gestellte Fragen {#faqs}

+++**Was überwacht Adobe mit New Relic One?**

Über das Java-Plug-in von New Relic One überwacht Adobe die Autoren-, Veröffentlichungs- und Vorschau-Services (sofern verfügbar) von AEM as a Cloud Service. Adobe ermöglicht benutzerspezifische Telemetrie und Überwachung mit New Relic One APM in Nicht-Produktions- und Produktionsumgebungen in AEM as a Cloud Service.

Ihr New Relic One-Konto ist mit einem primären, von Adobe bereitgestellten Konto verknüpft und erhält von mehreren Anwendungen Daten; je drei Anwendungen pro AEM as a Cloud Service-Umgebung.

* Ein Programm für den Autoren-Service pro Umgebung
* Eine Anwendung für den `Publish`-Service pro Umgebung (einschließlich „Golden Publish“)
* Ein Programm für den Vorschau-Service pro Umgebung

Hinweis:

* Pro Anwendung wird ein Lizenzschlüssel verwendet.
* AEM as a Cloud Service-Umgebungen senden Berichte nur an ein einziges New Relic One-Konto.
* Vollständige Überwachungsmetriken und Ereignisse für New Relic One werden drei Monate lang gespeichert. 

+++

+++**Sendet Adobe Warnhinweise über New Relic One?**

Adobe bietet Zugriff auf New Relic One nur zu Beobachtungszwecken und nutzt ihn nicht für Kundenwarnungen oder interne betriebliche Warnungen. Benachrichtigungen über Vorfälle werden über [Benutzerbenachrichtigungsprofile](/help/journey-onboarding/notification-profiles.md) gesendet.
+++

+++**Wer kann auf die Daten des Cloud-Service von New Relic One zugreifen?**

Bis zu 30 Mitgliedern Ihres Teams wird vollständiger Lesezugriff gewährt. Sie erhalten für alle APM-Metriken, die vom New Relic One-Agenten erfasst werden, Lesezugriff.
+++

+++**Wird eine benutzerdefinierte SSO-Konfiguration unterstützt?**

Das von Adobe bereitgestellte New Relic One-Konto unterstützt keine benutzerdefinierte SSO-Konfiguration.
+++

+++**Was ist, wenn ich bereits über ein lokales New Relic-Abonnement verfüge?**

New Relic One ist die neue Beobachtungsplattform von New Relic und ermöglicht es dem Support von Adobe und Ihren Teams, Metriken und Ereignisse an einem zentralen Ort zu beobachten, zu überwachen und anzuzeigen.

New Relic One bietet Benutzenden die Möglichkeit, alle Konten zu durchsuchen, zu denen sie Zugriff haben, und die Daten von allen Services und Hosts in einer Ansicht zu visualisieren.

Der Adobe-Support überwacht AEM as a Cloud Service mit New Relic One und anderen Tools, während Ihre Teams New Relic weiterhin für On-Premise-Dienste und -Infrastruktur verwenden können. Die Visualisierung der Daten ist sowohl über das Adobe New Relic One-Konto als auch über kundenseitig verwaltete New Relic-Konten möglich.

>[!NOTE]
>
>Um beide Datensätze in New Relic One anzuzeigen, müssen Benutzende über die entsprechenden Berechtigungen verfügen und für beide Konten (das Adobe New Relic One- und das kundenseitig verwaltete New Relic-Konto) dieselbe Anmeldemethode verwenden.

+++

+++**Der APM-Agent für mein New Relic One-Konto wurde angehalten. Was ist passiert?**

[APM-Agents werden angehalten](#limitations), wenn mindestens 30 Tage lang keine Aktivität erkannt wurde. Führen Sie die Schritte aus dem Abschnitt [Aktivieren Ihres New Relic One-Unterkontos](#activate-sub-account) in diesem Dokument aus, um Ihr New Relic One-Unterkonto erneut zu aktivieren.
+++
