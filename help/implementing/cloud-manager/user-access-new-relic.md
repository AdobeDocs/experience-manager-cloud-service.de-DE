---
title: New Relic One
description: Erfahren Sie mehr über den APM-Service (Application Performance Monitoring) von New Relic One für AEM as a Cloud Service und wie Sie darauf zugreifen können.
exl-id: 9fa0c5eb-415d-4e56-8136-203d59be927e
source-git-commit: 3891a55ff48f48de4e55e0229e9f76e5bf500cb3
workflow-type: tm+mt
source-wordcount: '1843'
ht-degree: 76%

---


# New Relic One {#user-access}

Erfahren Sie mehr über den APM-Service (Application Performance Monitoring) von New Relic One für AEM as a Cloud Service und wie Sie darauf zugreifen können.

## Einführung    {#introduction}

Adobe erachtet die Überwachbarkeit, Verfügbarkeit und Leistungsfähigkeit Ihres Programms als außerordentlich wichtig. Als Teil des Standardproduktangebots bietet AEM as a Cloud Service Zugriff auf eine benutzerdefinierte Überwachungs-Suite für New Relic One. So wird sichergestellt, dass Ihre Teams ihre System- und Umgebungsleistungsmetriken in AEM as a Cloud Service optimal im Auge behalten können.

In diesem Dokument wird beschrieben, wie Sie den Zugriff auf die in Ihren AEM as a Cloud Service-Umgebungen aktivierten Funktionen zur Leistungsüberwachung (APM) von New Relic One-Programmen verwalten, sodass Sie die Leistung verbessern und AEM as a Cloud Service optimal nutzen können.

Wenn ein neues Produktionsprogramm erstellt wird, wird automatisch das New Relic One-Unterkonto erstellt, das Ihrem AEM as a Cloud Service Programm zugeordnet ist. [Dieses Unterkonto muss aktiviert werden](#activate-sub-account) , um mit der Aufnahme von Daten zu beginnen.

## Funktionen {#transaction-monitoring}

New Relic One APM für AEM as a Cloud Service hat viele Funktionen.

* Direkter Zugriff auf das dedizierte Konto „New Relic One“

* Instrumentierter New Relic One APM-Agent, der exakte Methodenaufrufe mit Zeilennummern anzeigt, einschließlich externer Abhängigkeiten und Datenbanken

* Ganzheitliche Leistungsoptimierung durch die Kombination von Schlüsselmetriken aus der Überwachung auf Infrastruktur- und Anwendungsebene (Adobe Experience Manager).

* Anzeige von JMX-Mbeans- und Konsistenzprüfungen von AEM as a Cloud Service direkt in New Relic Insights-Metriken, was eine umfassende Leistungsprüfung des Programm-Stacks und der Konsistenzmetriken ermöglicht.

## New Relic One-Unterkonto aktivieren {#activate-sub-account}

Für ein neu erstelltes Programm wird ein New Relic One-Unterkonto für Sie erstellt. Sie müssen sie jedoch aktivieren, damit sie Daten erfassen kann. Dies wird nicht automatisch durchgeführt. Führen Sie die folgenden Schritte aus, um Ihr Unterkonto zu aktivieren.

>[!NOTE]
>
>Ein Benutzer in **Business Owner** oder **Bereitstellungsmanager** -Rolle muss angemeldet sein, um das New Relic One-Unterkonto zu verwalten.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, für das Sie Ihre New Relic One-Benutzer verwalten möchten.

1. Am unteren Rand des **Umgebungen** -Karte auf der Seite mit der Programmübersicht klicken, auf die Suchschaltfläche mit Auslassungspunkten klicken und die Option **Aktivieren von New Relic**.

   ![Benutzer verwalten](assets/newrelic-activate-sub-account.png)

   * Sie können die Option **Benutzer verwalten** auch über die Schaltfläche mit den drei Punkten oben auf dem Bildschirm **Umgebungen** Ihres Programms aufrufen.

1. [Pipeline ausführen](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines) für dieselbe Umgebung erfolgreich abgeschlossen werden, um die Aktivierung des Unterkontos abzuschließen.

Wenn das Unterkonto deaktiviert wird, wird keine Datenerfassung durchgeführt.

## Verwalten von New Relic One-Benutzenden {#manage-users}

Führen Sie diese Schritte aus, um die Benutzenden Ihres New Relic One-Unterkontos zu definieren, das mit Ihrem AEM as a Cloud Service-Programm verbunden ist.

>[!NOTE]
>
>Eine Person muss mit der Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** angemeldet sein, um New Relic One-Benutzende verwalten zu können.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, für das Sie Ihre New Relic One-Benutzer verwalten möchten.

1. Klicken Sie auf der Programmübersichtsseite auf der Karte **Umgebungen** unten auf die Schaltfläche mit den drei Punkten und wählen Sie **Benutzer verwalten**.

   ![Benutzer verwalten](assets/newrelic-manage-users.png)

   * Sie können die Option **Benutzer verwalten** auch über die Schaltfläche mit den drei Punkten oben auf dem Bildschirm **Umgebungen** Ihres Programms aufrufen.

1. Im **Verwalten von New Relic-Benutzern** eingeben, den Vor- und Nachnamen des Benutzers eingeben, den Sie hinzufügen möchten, und klicken Sie auf **Hinzufügen** Schaltfläche. Wiederholen Sie diesen Schritt für alle Benutzer, die Sie hinzufügen möchten.

   ![Hinzufügen von Benutzenden](assets/newrelic-add-users.png)

1. Um New Relic One-Benutzende zu entfernen, klicken Sie am rechten Ende der Zeile für die jeweilige Person auf die Schaltfläche „Löschen“.

1. Klicken Sie auf **Speichern**, um die-Benutzenden zu erstellen.

Sobald die Benutzenden definiert sind, sendet New Relic eine Bestätigungs-E-Mail an jede Person, der Sie Zugriff gewährt haben, damit sie den Einrichtungsprozess abschließen und sich anmelden kann.

>[!NOTE]
>
>Wenn Sie die Benutzenden von New Relic One verwalten, müssen Sie sich auch selbst als Benutzerin bzw. Benutzer hinzufügen, um ebenfalls Zugriff zu erhalten. Die Rolle als **Geschäftsinhaber** oder **Bereitstellungs-Manager** reicht nicht aus, um Zugriff auf New Relic One zu erhalten. Sie müssen auch sich selbst die Benutzenden-Rolle zuweisen.

## Aktivieren Ihres New Relic One-Benutzerkontos {#activate-user-account}

Nachdem ein New Relic One-Benutzerkonto, wie im vorigen Abschnitt [Verwalten von New Relic One-Benutzenden](#manage-users) beschrieben, erstellt wurde, sendet New Relic diesen Benutzenden eine Bestätigungs-E-Mail an die angegebene Adresse. Um diese Konten verwenden zu können, müssen Benutzende zunächst ihre Konten bei New Relic aktivieren, indem sie ihre Kennwörter zurücksetzen.

Führen Sie diese Schritte aus, um Ihr Konto als New Relic-Benutzer bzw. -Benutzerin zu aktivieren.

1. Klicken Sie auf den Link in der E-Mail von New Relic. Dadurch öffnet sich im Browser die Anmeldeseite von New Relic.

1. Wählen Sie auf der Anmeldeseite von New Relic die Option **Kennwort vergessen?**.

   ![New Relic-Anmeldung](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Geben Sie die E-Mail-Adresse ein, an die Sie die Bestätigungs-E-Mail erhalten haben, und klicken Sie auf **Link zum Zurücksetzen senden**.

   ![E-Mail-Adresse eingeben](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. New Relic sendet Ihnen eine E-Mail mit einem Link zur Kontobestätigung.

Wenn Sie keine Bestätigungs-E-Mail von New Relic erhalten, lesen Sie bitte den Abschnitt [Fehlerbehebung](#troubshooting).

## Zugriff auf New Relic One {#accessing-new-relic}

Nachdem Sie [Ihr New Relic-Konto aktiviert haben](#activate-account), können Sie über Cloud Manager oder direkt auf New Relic One zugreifen.

Zugreifen auf New Relic One über Cloud Manager

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, für das Sie auf New Relic One zugreifen möchten.

1. Klicken Sie auf der Programmübersichtsseite auf der Karte **Umgebungen** unten auf die Schaltfläche mit den drei Punkten und wählen Sie **New Relic öffnen**.

   ![Verwalten der Benutzenden](assets/newrelic-access.png)

   * Sie können New Relic auch über die Schaltfläche mit den drei Punkten oben auf dem Bildschirm **Umgebungen** Ihres Programms aufrufen.

1. Melden Sie sich in der sich öffnenden neuen Browser-Registerkarte bei New Relic One an.

Direkter Zugriff auf New Relic One

1. Navigieren Sie zur Anmeldeseite von New Relic unter [`https://login.newrelic.com/login`](https://login.newrelic.com/login)

1. Melden Sie sich bei New Relic One an.

### Verifizieren Ihrer E-Mail-Adresse {#verify-email}

Wenn Sie während der Anmeldung bei New Relic One aufgefordert werden, Ihre E-Mail-Adresse zu überprüfen, bedeutet dies, dass Ihre E-Mail-Adresse mit mehreren Konten verknüpft ist. Auf diese Weise können Sie festlegen, auf welches Konto zugegriffen werden soll.

Wenn Sie Ihre E-Mail-Adresse nicht verifizieren, versucht New Relic, Sie mit dem zuletzt erstellten Benutzerdatensatz anzumelden, der mit Ihrer E-Mail-Adresse verknüpft ist. Um zu vermeiden, dass Ihre E-Mail-Adresse bei jeder Anmeldung überprüft wird, klicken Sie im Anmeldebildschirm auf das Kontrollkästchen **Angaben speichern**.

Um weitere Hilfe zu erhalten, öffnen Sie ein Support-Ticket über das [AEM Support-Portal](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).

## Fehlerbehebung beim Zugriff auf New Relic One-Benutzer {#troubleshooting}

Wenn Sie als New Relic One-Benutzer hinzugefügt wurden, wie im Abschnitt beschrieben [Verwalten von New Relic One-Benutzern](#manage-users) und die ursprüngliche E-Mail zur Kontobestätigung nicht finden können, führen Sie die folgenden Schritte aus.

1. Navigieren Sie zur Anmeldeseite von New Relic unter [`login.newrelic.com/login`](https://login.newrelic.com/login).

1. Klicken Sie auf **Kennwort vergessen?**.

   ![New Relic-Anmeldung](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Geben Sie die E-Mail-Adresse ein, mit der Ihr Konto erstellt wurde, und wählen Sie **Link zum Zurücksetzen senden**.

   ![E-Mail-Adresse eingeben](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. New Relic sendet Ihnen eine E-Mail mit einem Link zur Kontobestätigung.

Wenn Sie den Anmeldevorgang abgeschlossen haben und sich aufgrund von E-Mail- oder Kennwortfehlermeldungen nicht bei Ihrem Konto anmelden können, erstellen Sie ein Support-Ticket über die [Admin Console](https://adminconsole.adobe.com/).

Falls Sie keine E-Mail von New Relic erhalten:

* Überprüfen Sie Ihre [Spam-Filter](https://docs.newrelic.com/docs/accounts/accounts-billing/account-setup/create-your-new-relic-account/).
* [Fügen Sie New Relic gegebenenfalls zu Ihrer E-Mail-Zulassungsliste hinzu](https://docs.newrelic.com/docs/accounts/accounts/account-maintenance/account-email-settings/#email-whitelist).
* Wenn keiner dieser Vorschläge hilft, geben Sie Feedback zum Support-Ticket, und das Adobe-Supportteam wird Ihnen weiterhelfen.

## Einschränkungen {#limitations}

Die folgenden Einschränkungen gelten für das Hinzufügen von Benutzenden zu New Relic One:

* Es können maximal 30 Benutzende hinzugefügt werden. Wenn die maximale Anzahl von Benutzenden erreicht wurde, entfernen Sie Benutzende, um neue Benutzende hinzufügen zu können.
* Benutzende, die zu New Relic hinzugefügt wurden, sind vom Typ **Eingeschränkt**. Weitere Informationen finden Sie in der [Dokumentation zu New Relic](https://docs.newrelic.com/docs/accounts/original-accounts-billing/original-users-roles/users-roles-original-user-model/#:~:text=In%20general%2C%20Admins%20take%20responsibility,Restricted%20Users%20can%20use%20them.&amp;text=One%20or%20more%20individuals%20who,change).
* AEM as a Cloud Service bietet nur die New Relic One APM-Lösung, aber keine Unterstützung für Warnhinweise, Protokollierung oder API-Integrationen.

>[!NOTE]
>
>Wenn in Ihrem New Relic One-Unterkonto mindestens 90 Tage lang keine Aktivität erkannt wurde, wird der APM-Agent angehalten.
>
>Führen Sie dieselben Schritte im Abschnitt [New Relic One-Unterkonto aktivieren](#activate-sub-account) in diesem Dokument, um Ihr New Relic One-Unterkonto erneut zu aktivieren.

Wenn Sie weitere Hilfe oder zusätzliche Anleitungen zu New Relic One-Angeboten für Ihr AEM as a Cloud Service Programm benötigen, öffnen Sie ein Supportticket über [AEM Support-Portal.](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html)

## Häufig gestellte Fragen zu New Relic One {#faqs}

### Was überwacht Adobe mit New Relic One? {#adobe-monitor}

Über das Java-Plug-in von New Relic One überwacht Adobe die Autoren-, Veröffentlichungs- und Vorschau-Services (sofern verfügbar) von AEM as a Cloud Service. Adobe ermöglicht benutzerspezifische Telemetrie und Überwachung mit New Relic One APM in Nicht-Produktions- und Produktionsumgebungen in AEM as a Cloud Service.

Ihr New Relic One-Konto ist mit einem primären, von Adobe bereitgestellten Konto verknüpft und erhält Daten von mehreren Programmen: je drei Programmen pro Umgebung in AEM as a Cloud Service.

* Eine Anwendung pro Umgebung für den Autoren-Service
* Eine Anwendung pro Umgebung für den Veröffentlichungs-Service (einschließlich „Golden Publish“)
* Eine Anwendung pro Umgebung für den Vorschau-Service

Hinweis:

* Pro Anwendung wird ein Lizenzschlüssel verwendet.
* Umgebungen in AEM as a Cloud Service senden Berichte nur an ein einziges New Relic One-Konto.
* Vollständige Überwachungsmetriken und Ereignisse für New Relic One werden sieben Tage lang gespeichert.

### Sendet Adobe Warnhinweise von New Relic One? {#alerting-new-relic}

Adobe bietet New Relic One nur zu Beobachtungszwecken Zugriff und nutzt ihn nicht für Kundenwarnungen oder interne betriebliche Warnungen. Benachrichtigungen für Vorfälle werden über [Benutzerbenachrichtigungsprofile.](/help/journey-onboarding/notification-profiles.md)

### Wer kann auf die Daten des Cloud-Service von New Relic One zugreifen? {#access-new-relic-cloud}

Vollständiger Lesezugriff wird bis zu 30 Mitgliedern Ihres Teams gewährt. Sie erhalten Lesezugriff für alle APM-Metriken, die vom New Relic One-Agenten erfasst werden.

### Wird eine benutzerdefinierte SSO-Konfiguration unterstützt? {#custom-sso}

Das von Adobe bereitgestellte New Relic One-Konto unterstützt keine benutzerdefinierte SSO-Konfiguration.

### Was ist, wenn ich bereits über ein lokales New Relic-Abonnement verfüge? {#new-relic-subscription}

New Relic One ist die neue Beobachtungsplattform von New Relic und ermöglicht es dem Support von Adobe und Ihren Teams, Metriken und Ereignisse an einem zentralen Ort zu beobachten, zu überwachen und anzuzeigen.

New Relic One bietet Benutzenden die Möglichkeit, alle Konten zu durchsuchen, zu denen sie Zugriff haben, und die Daten von allen Services und Hosts in einer Ansicht zu visualisieren.

Während die Adobe-Supportteams im Rahmen Ihres Services die AEM as a Cloud Service-Anwendung mit New Relic One und anderen internen Tools überwachen, können Ihre Teams New Relic für lokal gehostete Services und Infrastrukturen nutzen. Die Visualisierung der Daten ist sowohl über das Adobe New Relic One-Konto als auch über kundenseitig verwaltete New Relic-Konten möglich.

>[!NOTE]
>
>Um beide Datensätze in New Relic One anzuzeigen, müssen Benutzende über die entsprechenden Berechtigungen verfügen und für beide Konten (das Adobe New Relic One- und das kundenseitig verwaltete New Relic-Konto) dieselbe Anmeldemethode verwenden.

### Der APM-Agent für mein New Relic One-Konto wird angehalten. Was ist passiert? {#deactivated}

[APM-Agenten werden angehalten](#limitations) , wenn mindestens 90 Tage lang keine Aktivität erkannt wurde. Führen Sie dieselben Schritte im Abschnitt [New Relic One-Unterkonto aktivieren](#activate-sub-account) in diesem Dokument, um Ihr New Relic One-Unterkonto erneut zu aktivieren.
