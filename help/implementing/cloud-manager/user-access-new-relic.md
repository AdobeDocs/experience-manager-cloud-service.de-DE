---
title: Neuer Relikt
description: Erfahren Sie mehr über den neuen APM-Dienst (New Relic One Application Performance Monitoring) für AEM as a Cloud Service und wie Sie darauf zugreifen können.
exl-id: 9fa0c5eb-415d-4e56-8136-203d59be927e
source-git-commit: 6cf164093cc543fe4847859b248e70efd86efbb1
workflow-type: tm+mt
source-wordcount: '1038'
ht-degree: 18%

---


# Neuer Relikt {#user-access}

Erfahren Sie mehr über den neuen APM-Dienst (New Relic One Application Performance Monitoring) für AEM as a Cloud Service und wie Sie darauf zugreifen können.

## Einführung {#introduction}

Adobe legt großen Wert auf die Überwachung, Verfügbarkeit und Leistung Ihrer Anwendung. Um dieses Ziel zu erreichen, bietet AEM as a Cloud Service Zugriff auf eine benutzerdefinierte New Relic One-Monitoring-Suite als Teil des Standardproduktangebots, um sicherzustellen, dass Ihre Teams eine maximale Sichtbarkeit für Ihre AEM as a Cloud Service System- und Umgebungsleistungsmetriken haben.

In diesem Dokument werden die neuen Funktionen zur Leistungsüberwachung für Relic One-Anwendungen (APM) beschrieben, die in Ihren AEM as a Cloud Service Umgebungen aktiviert sind, um die Leistung zu unterstützen und Ihnen zu ermöglichen, AEM as a Cloud Service optimal zu nutzen.

## Funktionen {#transaction-monitoring}

Neue Relic One APM für AEM as a Cloud Service hat viele Funktionen.

* Direkter Zugriff auf ein dediziertes New Relic One-Konto (Zugriff über Adobe Support möglich)

* Instrumentierter neuer Relic One APM-Agent, der exakte Methodenaufrufe mit Zeilennummern anzeigt, einschließlich externer Abhängigkeiten und Datenbanken

* Ganzheitliche Leistungsoptimierung durch Kombination von Schlüsselmetriken aus der Überwachung auf Infrastrukturebene und der Überwachung der Anwendung (Adobe Experience Manager)

* Exposition von AEM as a Cloud Service JMX-MBans und Konsistenzprüfungen direkt in den neuen Metriken für &quot;Relic Insights&quot;, wodurch die Leistung und Konsistenzmetriken von Anwendungen eingehend überprüft werden können.

## Zugriff auf die neue Relie {#accessing-new-relic}

Führen Sie diese Schritte aus, um Zugriff auf Ihr neues relatives One-Unterkonto zu erhalten, das mit Ihrem AEM as a Cloud Service Programm verknüpft ist.

1. Öffnen Sie eine Anfrage, indem Sie in der Admin Console auf die Registerkarte „Support“ zugreifen.
1. Geben Sie in Ihrer Anfrage die Details Ihrer Programm-ID sowie die Liste der Benutzer an, die Zugriff auf New Relic benötigen.
   * Die vollständigen Namen und gültigen E-Mail-Adressen aller Benutzer müssen angegeben werden.

Siehe Dokument . [AEM Support-Portal für Experience Cloud](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) für weitere Informationen zum Öffnen von Tickets.

Sobald der Zugriff bereitgestellt wurde, sendet New Relic eine Bestätigungs-E-Mail an jeden Benutzer, damit der Benutzer den Einrichtungsprozess abschließen und sich anmelden kann.

Wenn der Benutzer die ursprüngliche Bestätigungs-E-Mail für das Konto nicht finden kann, führen Sie die folgenden Schritte aus.

1. Navigieren Sie zur Anmeldeseite von New Relic unter [`login.newrelic.com/login`](https://login.newrelic.com/login).

1. Auswählen **Kennwort vergessen?**.

   ![Neue reine Anmeldung](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Geben Sie die E-Mail-Adresse des Kontos ein und wählen Sie **Link zum Zurücksetzen senden**.

   ![E-Mail-Adresse eingeben](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. New Relic sendet dem Benutzer eine E-Mail mit einem Link zur Kontobestätigung.

Wenn Sie den Anmeldevorgang abgeschlossen haben und sich aufgrund von E-Mail- oder Kennwortfehlermeldungen nicht bei Ihrem Konto anmelden können, melden Sie ein Supportticket über das [Admin Console](https://adminconsole.adobe.com/).

>[!TIP]
>
>Wenn Sie keine E-Mail von New Relic erhalten:
>
>* Überprüfen Sie Ihre [Spam-Filter](https://docs.newrelic.com/docs/accounts/accounts-billing/account-setup/create-your-new-relic-account/).
>* Gegebenenfalls [fügen Sie New Relic zu Ihrer E-Mail-Zulassungsliste hinzu](https://docs.newrelic.com/docs/accounts/accounts/account-maintenance/account-email-settings/#email-whitelist).
>* Wenn keiner der Vorschläge Ihnen hilft, geben Sie bitte Feedback zum Support-Ticket und das Supportteam hilft Ihnen weiter.


### E-Mail überprüfen {#verify-email}

Wenn Sie aufgefordert werden, Ihre E-Mail während der Anmeldung zu überprüfen, bedeutet dies, dass Ihre E-Mail mit mehreren Konten verknüpft ist. Auf diese Weise können Sie festlegen, auf welches Konto zugegriffen werden soll.

Wenn Sie Ihre E-Mail-Adresse nicht verifizieren, versucht New Relic, Sie mit dem zuletzt erstellten Benutzerdatensatz anzumelden, der mit Ihrer E-Mail-Adresse verknüpft ist. Um zu vermeiden, dass Ihre E-Mail bei jeder Anmeldung überprüft wird, klicken Sie auf das **Angaben speichern** im Anmeldebildschirm.

Weitere Hilfe erhalten Sie, wenn Sie ein Support-Ticket über die [AEM Support Portal](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## Ausnahmen {#exceptions}

AEM as a Cloud Service bietet nur die Neue Relic One APM-Lösung und bietet keine Unterstützung für Warnhinweise, Protokollierung oder API-Integrationen.

Für weitere Hilfe oder zusätzliche Anleitungen zu neuen Angeboten von Relic One für Ihr AEM as a Cloud Service Programm öffnen Sie bitte ein Support-Ticket über [AEM Support Portal](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## Häufig gestellte Fragen zum New Relic-Konto {#faqs}

### Was überwacht Adobe mit New Relic One? {#adobe-monitor}

Adobe überwacht die AEM as a Cloud Service Autoren-, Veröffentlichungs- und Vorschaudienste (sofern verfügbar) über das Java-Plug-in von New Relic One. Adobe ermöglicht die benutzerdefinierte Telemetrie und Überwachung von Relic One APM in Nicht-Produktions- und Produktionsumgebungen AEM as a Cloud Service Umgebungen.

Ihr neues Relic One-Konto ist an ein primäres, von der Adobe gepflegtes Konto angehängt und enthält mehrere Anwendungen, die ihm Berichte zuweisen: drei pro AEM as a Cloud Service Umgebung.

* Eine Anwendung für den Autorendienst pro Umgebung
* Eine Anwendung für den Veröffentlichungsdienst pro Umgebung (einschließlich Golden Publish)
* Eine Anwendung für den Vorschaudienst pro Umgebung

Hinweis:

* Jede Anwendung verwendet einen Lizenzschlüssel.
* AEM as a Cloud Service Umgebungen nur ein einziges Konto für Relic One anzeigen.
* Vollständige Überwachungsmetriken und -ereignisse für &quot;Neu: Relisch eins&quot;werden 7 Tage lang beibehalten.

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
