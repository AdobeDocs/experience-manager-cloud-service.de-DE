---
title: New Relic One
description: Erfahren Sie mehr über den neuen APM-Dienst (New Relic One Application Performance Monitoring) für AEM as a Cloud Service und wie Sie darauf zugreifen können.
exl-id: 9fa0c5eb-415d-4e56-8136-203d59be927e
source-git-commit: 8ae52afc366c6607cfc806f68bec2069a2e93f94
workflow-type: tm+mt
source-wordcount: '1612'
ht-degree: 10%

---


# Neuer Relikt {#user-access}

Erfahren Sie mehr über den neuen APM-Dienst (New Relic One Application Performance Monitoring) für AEM as a Cloud Service und wie Sie darauf zugreifen können.

## Einführung  {#introduction}

Adobe legt großen Wert auf die Überwachung, Verfügbarkeit und Leistung Ihrer Anwendung. AEM as a Cloud Service bietet Zugriff auf eine benutzerdefinierte New Relic One-Monitoring-Suite als Teil des Standardproduktangebots, um sicherzustellen, dass Ihre Teams die maximale Sichtbarkeit Ihrer AEM as a Cloud Service System- und Umgebungsleistungsmetriken erhalten.

In diesem Dokument wird beschrieben, wie Sie den Zugriff auf die in Ihren AEM as a Cloud Service Umgebungen aktivierten Funktionen zur Leistungsüberwachung neuer Relic One-Anwendungen (APM) verwalten, um die Leistung zu unterstützen und Ihnen zu ermöglichen, AEM as a Cloud Service optimal zu nutzen.

Wenn ein neues Produktionsprogramm erstellt wird, wird automatisch das mit Ihrem AEM as a Cloud Service Programm verknüpfte Unterkonto Neue Relische Eins erstellt.

## Funktionen {#transaction-monitoring}

Neue Relic One APM für AEM as a Cloud Service hat viele Funktionen.

* Direkter Zugriff auf ein dediziertes New Relic One-Konto (Zugriff über Adobe Support möglich)

* Instrumentierter neuer Relic One APM-Agent, der exakte Methodenaufrufe mit Zeilennummern anzeigt, einschließlich externer Abhängigkeiten und Datenbanken

* Ganzheitliche Leistungsoptimierung durch Kombination von Schlüsselmetriken aus der Überwachung auf Infrastrukturebene und der Überwachung der Anwendung (Adobe Experience Manager)

* Exposition von AEM as a Cloud Service JMX-MBans und Konsistenzprüfungen direkt in den neuen Metriken für &quot;Relic Insights&quot;, wodurch die Leistung und Konsistenzmetriken von Anwendungen eingehend überprüft werden können.

## Neue reale One-Benutzer verwalten {#manage-users}

Führen Sie diese Schritte aus, um die Benutzer Ihres neuen as a Cloud Service Programms &quot;Relic One&quot;zu definieren.

>[!NOTE]
>
>Ein Benutzer in **Business Owner** oder **Bereitstellungsmanager** -Rolle muss angemeldet sein, um neue Relic One-Benutzer zu verwalten.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, für das Sie Ihre New Relic One Benutzer verwalten möchten.

1. Am unteren Rand des **Umgebungen** auf der Programmübersichtsseite klicken, auf die Suchschaltfläche klicken und die Option **Benutzer verwalten**.

   ![Benutzer verwalten](assets/newrelic-manage-users.png)

   * Sie können auch auf die **Benutzer verwalten** über die Suchschaltfläche oben im **Umgebungen** Bildschirm Ihres Programms.

1. Im **Neue reine Benutzer verwalten** eingeben, den Vor- und Nachnamen des Benutzers eingeben, den Sie hinzufügen möchten, und klicken Sie auf **Hinzufügen** Schaltfläche. Wiederholen Sie diesen Schritt für alle Benutzer, die Sie hinzufügen möchten.

   ![Benutzer hinzufügen](assets/newrelic-add-users.png)

1. Um neue Relic One-Benutzer zu entfernen, klicken Sie auf die Schaltfläche &quot;Löschen&quot;am rechten Ende der Zeile, die den Benutzer darstellt.

1. Klicken **Speichern** , um die Benutzer zu erstellen.

Sobald die Benutzer definiert sind, sendet New Relic eine Bestätigungs-E-Mail an jeden Benutzer, dem Sie Zugriff gewährt haben, damit der Benutzer den Einrichtungsprozess abschließen und sich anmelden kann.

>[!NOTE]
>
>Wenn Sie die New Relic One-Benutzer verwalten, müssen Sie sich auch selbst als Benutzer hinzufügen, um ebenfalls Zugriff zu erhalten. Die **Business Owner** oder **Bereitstellungsmanager** reicht nicht aus, um Zugriff auf New Relic One zu haben. Sie müssen sich auch als Benutzer erstellen.

## Aktivieren Sie Ihr neues relic One-Benutzerkonto {#activate-account}

Sobald ein neues relisches Benutzerkonto erstellt wurde, wie im Abschnitt Vorschau beschrieben [Neue reale One-Benutzer verwalten](#manage-users), New Relic sendet diesen Benutzern eine Bestätigungs-E-Mail an die angegebene Adresse. Um diese Konten verwenden zu können, müssen Benutzer zunächst ihre Konten mit New Relic aktivieren, indem sie ihre Kennwörter zurücksetzen.

Führen Sie diese Schritte aus, um Ihr Konto als neuen relativen Benutzer zu aktivieren.

1. Klicken Sie in New Relic auf den in der E-Mail angegebenen Link. Dadurch wird Ihr Browser zur Seite Neues Symbol für Relic geöffnet.

1. Wählen Sie auf der Seite Neues Symbol für Relikt die Option **Kennwort vergessen?**.

   ![Neue reine Anmeldung](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Geben Sie die E-Mail-Adresse ein, an die Sie die Bestätigungs-E-Mail erhalten haben, und wählen Sie **Link zum Zurücksetzen senden**.

   ![E-Mail-Adresse eingeben](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. New Relic sendet Ihnen eine E-Mail mit einem Link zur Kontobestätigung.

Wenn Sie keine Bestätigungs-E-Mail von New Relic erhalten, lesen Sie bitte den Abschnitt [Fehlerbehebung .](#troubshooting)

## Zugriff auf die neue Relie {#accessing-new-relic}

Einmal [Ihr neues Relic-Konto aktiviert haben,](#activate-account) Sie können über Cloud Manager oder direkt auf New Relic One zugreifen.

So greifen Sie über Cloud Manager auf die neue Relie zu:

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, für das Sie auf New Relic One zugreifen möchten.

1. Am unteren Rand des **Umgebungen** auf der Programmübersichtsseite klicken, auf die Suchschaltfläche klicken und die Option **Neue Relie öffnen**.

   ![Benutzer verwalten](assets/newrelic-access.png)

   * Sie können auch über die Suchschaltfläche oben im **Umgebungen** Bildschirm Ihres Programms.

1. Melden Sie sich in der sich öffnenden neuen Browser-Registerkarte bei New Relic One an.

So greifen Sie direkt auf die neue Relic One zu:

1. Navigieren Sie zur Anmeldeseite von New Relic unter [`https://login.newrelic.com/login`](https://login.newrelic.com/login)

1. Melden Sie sich bei New Relic One an.

### E-Mail überprüfen {#verify-email}

Wenn Sie aufgefordert werden, Ihre E-Mail während der Anmeldung bei New Relic One zu überprüfen, bedeutet dies, dass Ihre E-Mail mit mehreren Konten verknüpft ist. Auf diese Weise können Sie festlegen, auf welches Konto zugegriffen werden soll.

Wenn Sie Ihre E-Mail-Adresse nicht verifizieren, versucht New Relic, Sie mit dem zuletzt erstellten Benutzerdatensatz anzumelden, der mit Ihrer E-Mail-Adresse verknüpft ist. Um zu vermeiden, dass Ihre E-Mail bei jeder Anmeldung überprüft wird, klicken Sie auf das **Angaben speichern** im Anmeldebildschirm.

Weitere Hilfe erhalten Sie, wenn Sie ein Support-Ticket über die [AEM Support Portal](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).

## Fehlerbehebung für neuen Zugriff auf Relic One {#troubleshooting}

Wenn Sie als neuer relativer One-Benutzer hinzugefügt wurden, wie im Abschnitt beschrieben [Neue reale One-Benutzer verwalten](#manage-users) und kann die ursprüngliche E-Mail zur Kontobestätigung nicht finden, führen Sie die folgenden Schritte aus.

1. Navigieren Sie zur Anmeldeseite von New Relic unter [`login.newrelic.com/login`](https://login.newrelic.com/login).

1. Auswählen **Kennwort vergessen?**.

   ![Neue reine Anmeldung](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Geben Sie die E-Mail-Adresse ein, unter der Ihr Konto erstellt wurde, und wählen Sie **Link zum Zurücksetzen senden**.

   ![E-Mail-Adresse eingeben](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. New Relic sendet Ihnen eine E-Mail mit einem Link zur Kontobestätigung.

Wenn Sie den Anmeldevorgang abgeschlossen haben und sich aufgrund von E-Mail- oder Kennwortfehlermeldungen nicht bei Ihrem Konto anmelden können, melden Sie ein Supportticket über das [Admin Console.](https://adminconsole.adobe.com/)

Wenn Sie keine E-Mail von New Relic erhalten:

* Überprüfen Sie Ihre [Spam-Filter](https://docs.newrelic.com/docs/accounts/accounts-billing/account-setup/create-your-new-relic-account/).
* Gegebenenfalls [fügen Sie New Relic zu Ihrer E-Mail-Zulassungsliste hinzu](https://docs.newrelic.com/docs/accounts/accounts/account-maintenance/account-email-settings/#email-whitelist).
* Wenn keiner der Vorschläge Ihnen hilft, geben Sie bitte Feedback zum Support-Ticket und das Supportteam hilft Ihnen weiter.

## Beschränkungen {#limitations}

Die folgenden Einschränkungen gelten für das Hinzufügen von Benutzern zu &quot;Neu: Relisch:&quot;

* Es können maximal 25 Benutzer hinzugefügt werden. Wenn die maximale Anzahl von Benutzern erreicht wurde, entfernen Sie Benutzer, um neue Benutzer hinzufügen zu können.
* Benutzer, die zu New Relic hinzugefügt wurden, sind vom Typ **Eingeschränkt** verweisen auf [Weitere Informationen finden Sie in der neuen Dokumentation zu Relic .](https://docs.newrelic.com/docs/accounts/original-accounts-billing/original-users-roles/users-roles-original-user-model/#:~:text=In%20general%2C%20Admins%20take%20responsibility,Restricted%20Users%20can%20use%20them.&amp;text=One%20or%20more%20Individuen%20who,change)%20any%20New%20Relic%20features.)
* AEM as a Cloud Service bietet nur die Neue Relic One APM-Lösung und bietet keine Unterstützung für Warnhinweise, Protokollierung oder API-Integrationen.

Für weitere Hilfe oder zusätzliche Anleitungen zu neuen Angeboten von Relic One für Ihr AEM as a Cloud Service Programm öffnen Sie bitte ein Support-Ticket über [AEM Support Portal](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## Häufig gestellte Fragen zu Neuem Relikt {#faqs}

### Was überwacht Adobe mit New Relic One? {#adobe-monitor}

Adobe überwacht die AEM as a Cloud Service Autoren-, Veröffentlichungs- und Vorschaudienste (sofern verfügbar) über das Java-Plug-in von New Relic One. Adobe ermöglicht die benutzerdefinierte Telemetrie und Überwachung von Relic One APM in Nicht-Produktions- und Produktionsumgebungen AEM as a Cloud Service Umgebungen.

Ihr neues Relic One-Konto ist an ein primäres, von der Adobe gepflegtes Konto angehängt und enthält mehrere Anwendungen, die ihm Berichte zuweisen: drei pro AEM as a Cloud Service Umgebung.

* Eine Anwendung für den Autorendienst pro Umgebung
* Eine Anwendung für den Veröffentlichungsdienst pro Umgebung (einschließlich Golden Publish)
* Eine Anwendung für den Vorschaudienst pro Umgebung

Hinweis:

* Jede Anwendung verwendet einen Lizenzschlüssel.
* AEM as a Cloud Service Umgebungen nur ein einziges Konto für Relic One anzeigen.
* Die vollständigen Überwachungsmetriken und -ereignisse für die neue Relie werden sieben Tage lang beibehalten.

### Wer kann auf die Daten des neuen Relic One-Cloud-Service zugreifen? {#access-new-relic-cloud}

Vollständiger Lesezugriff wird bis zu 10 Mitgliedern Ihres Teams gewährt. Der Lesezugriff umfasst alle APM-Metriken, die vom neuen Agenten &quot;Relic One&quot;erfasst wurden.

### Wird die benutzerdefinierte SSO-Konfiguration unterstützt? {#custom-sso}

Die benutzerdefinierte SSO-Konfiguration wird für das von Adobe bereitgestellte Neue Relic One-Konto nicht unterstützt.

### Was ist, wenn ich bereits ein neues Relic-Abonnement vor Ort habe? {#new-relic-subscription}

New Relic One ist die neue Beobachtungsplattform von New Relic und ermöglicht es dem Support von Adoben und Ihren Teams, Metriken und Ereignisse an einem Ort zu beobachten, zu überwachen und anzuzeigen.

New Relic One bietet Benutzern die Möglichkeit, alle Konten zu durchsuchen, zu denen sie Zugriff haben, und die Daten von allen Services und Hosts in einer Ansicht zu visualisieren.

Während die Adobe-Unterstützung die AEM as a Cloud Service Anwendung mit New Relic One und anderen internen Tools als Teil Ihres Dienstes überwacht, können Ihre Teams weiterhin New Relic für lokal gehostete Dienste und Infrastruktur nutzen. Sie können die Daten sowohl aus dem Adobe New Relic One-Konto als auch aus kundenverwalteten New Relic-Konten visualisieren.

>[!NOTE]
>
>Um beide Datensätze in New Relic One anzuzeigen, muss ein Benutzer über die richtigen Berechtigungen verfügen und dieselbe Anmeldemethode für beide Konten verwenden (Adobe New Relic One und kundenverwaltete neue Relic-Konten).
