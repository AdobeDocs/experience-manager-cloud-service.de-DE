---
title: Benutzerzugriff auf neue Relation
description: Auf dieser Seite erfahren Sie mehr über die neue Überwachung der Leistung von Anwendungen für AEM as a Cloud Service
source-git-commit: 696b86e9e88ca1fd7c0a5b688fa78f46227df3a4
workflow-type: tm+mt
source-wordcount: '1049'
ht-degree: 1%

---


# Benutzerzugriff auf neue Relation {#user-access}

## Einführung {#introduction}

Adobe legt großen Wert auf die Überwachung, Verfügbarkeit und Leistung Ihrer Anwendung. Um dieses Ziel zu erreichen, bietet AEM as a Cloud Service Zugriff auf eine benutzerdefinierte Neue Relic-Monitoring-Suite als Teil des Standardproduktangebots, um sicherzustellen, dass Ihre Teams die größtmögliche Sichtbarkeit Ihrer Adobe Experience Manager-Cloud Service-System- und Umgebungsleistungsmetriken erhalten. In diesem Abschnitt werden die neuen Funktionen für die Überwachung von Relic beschrieben, die in Ihren AEM as a Cloud Service Umgebungen aktiviert sind, um die Leistung zu steigern und Ihnen zu ermöglichen, AEM as a Cloud Service optimal zu nutzen.

## AEM as a Cloud Service Transaktionsüberwachung über neue Relic - Value Provision {#transaction-monitoring}

Hier finden Sie die Zusammenfassung des Wertvorschlags aus der neuen Überwachung der Leistung von Relischen Anwendungen für AEM as a Cloud Service:

* Direkter Zugriff auf ein dediziertes New Relic One-Konto (Zugriff über Adobe Support möglich).

* Instrumentiert Neuer relischer APM-Agent, der exakte Methodenaufrufe mit Zeilennummern anzeigt, einschließlich externer Abhängigkeiten und Datenbanken.

* Ganzheitliche Leistungsoptimierung durch Kombination von Schlüsselmetriken aus der Überwachung auf Infrastrukturebene und der Überwachung der Anwendung (Adobe Experience Manager).

* Exposition von AEM as a Cloud Service JMX-MBans und Konsistenzprüfungen direkt in neue Metriken für &quot;Relic Insights&quot;, wodurch die Leistung und Konsistenzmetriken von Anwendungen eingehend überprüft werden können.

## Zugriff auf Ihr AEM as a Cloud Service neues relatives Konto {#accessing-new-relic}

Ihr dediziertes neues relatives Konto wird von Adobe über die Kundenunterstützung bereitgestellt und verwaltet. Adobe bleibt Eigentümer und Administrator und stellt das Konto in Ihrem Namen bereit, um Zugriff auf Ihr dediziertes Unterkonto zu gewähren.

Um Zugriff auf Ihr neues relatives Unterkonto zu erhalten, das mit Ihrem AEM as a Cloud Service Programm verknüpft ist:

* Öffnen Sie eine Anfrage, indem Sie in der Admin Console auf die Registerkarte Support zugreifen.
* Stellen Sie sicher, dass Ihr Ticket die Details Ihrer Programm-ID sowie die Liste der Adobe-Teams enthält, für die Sie den Zugriff auf die neue Relie anfordern.
* Alle Benutzer müssen einen vollständigen Namen und eine gültige E-Mail-Adresse erhalten.

   >[!NOTE]
   >Siehe [AEM Support-Portal für Experience Cloud](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) für weitere Details.

Sobald der Zugriff bereitgestellt wurde, sendet New Relic eine Bestätigungs-E-Mail an jeden Benutzer, damit der Benutzer den Einrichtungsprozess abschließen und sich anmelden kann.

Wenn der Benutzer die ursprüngliche Bestätigungs-E-Mail für das Konto nicht finden kann:

1. Navigieren Sie zur Anmeldeseite von New Relic unter [login.newrelic.com/login](https://login.newrelic.com/login).

1. Auswählen **Kennwort vergessen**.

   ![](/help/implementing/cloud-manager/assets/new-relic/newrelic-1.png)

1. Geben Sie die E-Mail-Adresse des Kontos ein und wählen Sie **Link zum Zurücksetzen senden**.

   ![](/help/implementing/cloud-manager/assets/new-relic/newrelic-2.png)

1. Wenn das System von New Relic eine E-Mail-Nachricht zurückgibt, wählen Sie den darin enthaltenen Link aus, um Ihr Konto erneut zu bestätigen.

   >[!NOTE]
   >Wenn Sie keine E-Mail von New Relic erhalten:
   >Überprüfen Sie Ihre [Spamfilter](https://docs.newrelic.com/docs/accounts/accounts-billing/account-setup/create-your-new-relic-account/). Falls zutreffend [Neue Relation zu Ihrer E-Mail-Zulassungsliste hinzufügen](https://docs.newrelic.com/docs/accounts/accounts/account-maintenance/account-email-settings/#email-whitelist).
   >Bitte geben Sie Feedback zum Support-Ticket und das Supportteam hilft Ihnen weiter.

1. Wenn Sie den Anmeldevorgang abgeschlossen haben und sich aufgrund von E-Mail- oder Kennwortfehlermeldungen nicht bei Ihrem Konto anmelden können, melden Sie sich bitte über [Admin Console](https://adminconsole.adobe.com/).

### E-Mail verifizieren {#verify-email}

Wenn Sie aufgefordert werden, Ihre E-Mail während der Anmeldung zu verifizieren, wird Ihre E-Mail mit mehreren Konten verknüpft und erhalten die Möglichkeit, Ihre E-Mail bei der Anmeldung zu überprüfen. Auf diese Weise können Sie festlegen, auf welches Konto zugegriffen werden soll. Wenn Sie Ihre E-Mail-Adresse nicht verifizieren, versucht New Relic, Sie mit dem zuletzt erstellten Benutzerdatensatz anzumelden, der mit Ihrer E-Mail-Adresse verknüpft ist. Um zu vermeiden, dass Ihre E-Mail bei jeder Anmeldung überprüft wird, klicken Sie im Anmeldebildschirm auf das Kontrollkästchen Angaben speichern .

Weitere Hilfe erhalten Sie, wenn Sie ein Support-Ticket über [AEM Support Portal](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).

## Exceptions {#exceptions}

AEM as a Cloud Service konzentriert das Angebot ausschließlich auf die neue Relic APM-Lösung und bietet keine Unterstützung für Warn-, Protokollierungs- oder API-Integrationsfunktionen.

Für weitere Hilfe oder zusätzliche Anleitungen zu neuen Relic-Angeboten für Ihr AEM as a Cloud Service Programm öffnen Sie bitte ein Support-Ticket über [AEM Support Portal](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html) Hilfe.

## Häufig gestellte Fragen zum neuen Relic-Konto {#faqs}

### Was überwacht Adobe mit New Relic? {#adobe-monitor}

Adobe überwacht die AEM as a Cloud Service Autoren-, Veröffentlichungs- und Vorschaudienste (sofern verfügbar) über das neue Relic APM Java Plug-in. Adobe ermöglicht benutzerspezifische, neue Relic APM-Telemetrie und -Überwachung in Nicht-Produktions- und Produktionsumgebungen AEM as a Cloud Service Umgebungen. Ihr neues Relic-Konto ist an ein primäres Konto angehängt, das von der Adobe verwaltet wird und über mehrere Anwendungen verfügt, die darüber berichten.

Drei pro AEM as a Cloud Service Umgebung:

* Eine Anwendung für den Autorendienst pro Umgebung
* Eine Anwendung für den Veröffentlichungsdienst pro Umgebung (einschließlich Golden Publish)
* Eine Anwendung für den Vorschaudienst pro Umgebung
   >[!IMPORTANT]
   >Jede Anwendung verwendet einen Lizenzschlüssel, AEM as a Cloud Service Umgebungen nur ein neues Relic-Konto melden. Vollständige Überwachungsmetriken und -ereignisse für die neue reine APM werden 7 Tage lang beibehalten.

### Wer kann auf die Daten des neuen Relischen Cloud Service zugreifen? {#access-new-relic-cloud}

Der volle Lesezugriff wird bis zu 10 Mitgliedern Ihres Teams gewährt. Der Lesezugriff umfasst alle APM-Metriken, die vom New Relic Agent erfasst wurden.

### Wird eine benutzerdefinierte SSO-Konfiguration unterstützt? {#custom-sso}

Die benutzerdefinierte SSO-Konfiguration wird derzeit für das von Adobe bereitgestellte neue relative Konto nicht unterstützt.

### Was ist, wenn Sie bereits ein neues Abonnement vor Ort haben? {#new-relic-subscription}

Die neue Beobachtungsplattform von New Relic namens New Relic One ermöglicht es Adobe Support-Gruppen und Ihren Teams, Metriken und Ereignisse an einem Ort zu beobachten, zu überwachen und anzuzeigen. Neue Relische Einheit bietet Benutzern die Möglichkeit, alle Konten zu durchsuchen, in denen sie Zugriff auf die Daten von allen Diensten und Hosts haben, und sie in einer Ansicht zu visualisieren. Während Adobe Support-Teams die AEM as a Cloud Service Anwendung mit New Relic und anderen internen Tools im Rahmen Ihres Dienstes überwachen, können Ihre Teams weiterhin New Relic für lokal gehostete Dienste und Infrastruktur nutzen. Sie können die Daten sowohl aus von Adobe als auch von kundenverwalteten New Relic-Konten visualisieren.

>[!NOTE]
>Der Benutzer muss über die richtigen Berechtigungen verfügen und dieselbe Anmeldemethode für beide Konten verwenden (Adobe und kundenverwaltetes neues relatives Konto).


