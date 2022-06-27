---
title: Lizenz-Dashboard
description: Cloud Manager bietet ein Dashboard, über das Sie die AEMaaCS-Produktberechtigungen leicht anzeigen können, die für Ihre Organisation oder Ihren Mandanten verfügbar sind.
exl-id: bf0f54a9-fe86-4bfb-9fa6-03cf0fd5f404
source-git-commit: 5bf65238ce4d1f619507d9a5f8b7574e58352d51
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 6%

---

# Lizenz-Dashboard {#license-dashboard}

Cloud Manager bietet ein Dashboard, über das Sie die AEMaaCS-Produktberechtigungen leicht anzeigen können, die für Ihre Organisation oder Ihren Mandanten verfügbar sind.

## Übersicht {#overview}

Das Cloud Manager License Dashboard bietet einfachen Zugriff auf folgende Informationen:

1. Lösungsberechtigungen, die Ihnen für alle Ihre Programme zur Verfügung stehen, einschließlich verwendeter und verfügbarer Lösungen
1. Inhaltsanforderungskonsummetriken mit Trend-Darstellung nach Monaten für die Sites-Lösung

## Verwenden des Lizenz-Dashboards {#using-dashboard}

Gehen Sie wie folgt vor, um auf Ihr Lizenz-Dashboard zuzugreifen.

>[!NOTE]
>
>Ein Benutzer in **Business Owner** -Rolle muss angemeldet sein, um das Lizenz-Dashboard anzeigen zu können.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wechseln Sie auf der Seite &quot;Produktübersicht&quot;zum **Lizenz** Registerkarte.

![Lizenz-Dashboard](assets/license-dashboard.png)

Das Dashboard ist in drei Abschnitte unterteilt, die Ihnen Folgendes zeigen:

* **Lösungen** - In diesem Abschnitt werden die von Ihnen lizenzierten Lösungen wie Sites oder Assets zusammengefasst.
* **Add-ons** - In diesem Abschnitt werden die Add-ons zu Ihren lizenzierten Lösungen zusammengefasst, die Sie verfügbar haben.
* **Sandbox- und Entwicklungsumgebungen** - In diesem Abschnitt werden die verfügbaren Umgebungen zusammengefasst.

Jeder Abschnitt fasst zusammen, was verfügbar ist und wie es aktuell verwendet wird, wenn überhaupt. Derzeit werden nur Sites-Lösungen angezeigt, selbst wenn im Mandanten andere Lösungen vorhanden sind.

* Die **Status** zeigt die Anzahl der nicht verwendeten Berechtigungen im Vergleich zur Gesamtanzahl an, die für den Mandanten verfügbar sind.
* Die **Konfiguriert in** gibt die Programme an, auf die die Lösungsberechtigungen angewendet wurden.
   * Eine Berechtigung gilt nur dann als verwendet, wenn eine Produktionsumgebung erstellt wurde oder bereits eine existiert, wenn eine Update-Pipeline dafür ausgeführt wurde.
* Die **Nutzung** -Spalte zeigt die Inhaltsanforderungen an, die in den letzten 12 Monaten als Grafik beim Klicken verbraucht wurden.

>[!TIP]
>
>Unter [Übersicht über die Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) erfahren Sie, wie Sie Ihre Adobe-Berechtigungen in Ihrer gesamten Organisation von der Admin Console aus verwalten.

## Häufig gestellte Fragen {#faq}

### Was ist eine Inhaltsanforderung? {#what-is-a-content-request}

Bei einer Inhaltsanfrage handelt es sich um eine Anfrage, die an AEM Sites oder ein vom Kunden bereitgestelltes Caching-System wie ein Inhaltsbereitstellungsnetzwerk gesendet wird, um Inhalte oder Daten entweder im HTML-Format als Seitenansicht oder im JSON-Format als API-Aufruf bereitzustellen.

Eine Inhaltsanfrage wird für jeden Seitenaufruf oder für alle fünf API-Aufrufe gezählt, gemessen am Eingang des ersten Caching-Systems, das eine Inhaltsanfrage erhält. Inhaltsanforderungen werden nur für Produktionsumgebungen gezählt.

Inhaltsanforderungen schließen Anforderungen oder Aktivitäten aus, die von oder für die Adobe allein zum Zweck der Bereitstellung von Produkten und Dienstleistungen initiiert wurden. Auch der von Adoben identifizierte Benutzeragenten-Traffic von Bots, Crawlern und Spidern im Zusammenhang mit gängigen Suchmaschinen und Social-Media-Diensten ist ausgeschlossen.

### Wie misst Adobe Experience Manager Inhaltsanforderungen? {#how-are-content-requests-measured}

Inhaltsanforderungen werden auf den Edge-Servern AEM as a Cloud Service verfolgt. Der Ursprungs-Traffic zählt nicht für Inhaltsanforderungen. Das in AEM as a Cloud Service Tracking integrierte CDN verfolgt gültige HTML- und JSON-Anfragen.

AEM verfügt auch über Regeln, um bekannte Bots auszuschließen, einschließlich bekannter Dienste, die die Site regelmäßig besuchen, um ihren Suchindex oder -dienst zu aktualisieren.

Im Folgenden finden Sie eine nicht erschöpfende Liste von Beispielen ausgeschlossener bekannter Dienste.

* AddSearchBot
* AhrefsBot
* Applebot
* Ask Jeeves Corporate Spider
* Bingbot
* BingPreview
* BLEXBot
* BuiltWith
* Bytespider
* CrawlerKengo
* Facebookexternalhit
* Google AdsBot
* Google AdsBot Mobile

### Warum zeigt mein Analytics-Bericht andere Ergebnisse als die AEM Inhaltsanforderungen an? {#why-are-reports-different}

Inhaltsanforderungen weisen Abweichungen mit den Analytics-Reporting-Tools eines Unternehmens auf, wie in dieser Tabelle zusammengefasst.

| Grund für Abweichung | Erklärung |
|---|---|
| Tagging | Alle Seiten, die als AEM Inhaltsanfragen verfolgt werden, können mit dem Analytics-Tracking versehen werden.<br>Alle API-Aufrufe, die als AEM Inhaltsanfragen verfolgt werden, werden vom Analytics-Tool eines Unternehmens nicht mit Tags versehen.<br>Seiten oder API-Aufrufe können zur Verfolgung von Aktionen anstelle von Ansichten mit Tags versehen werden. |
| Tag Management-Regeln | Die Einstellungen von Tag-Management-Regeln können zu einer Vielzahl von Datenerfassungskonfigurationen auf einer Seite führen, was zu einigen Diskrepanzen beim Tracking von Inhaltsanforderungen führt. |
| Bots | Unbekannte Bots, die nicht voridentifiziert und von AEM entfernt wurden, können zu Tracking-Diskrepanzen führen. |
| Report Suites | Seiten, die Teil derselben AEM und Domäne sind, können Daten an verschiedene Analytics Report Suites senden. |
| Überwachungs- und Sicherheitstools von Drittanbietern | Überwachungs- und Sicherheitsüberprüfungswerkzeuge können Inhaltsanforderungen für AEM generieren, die in Analytics-Berichten nicht verfolgt werden. |
| Vorababruf-Anfragen | Die Verwendung eines Vorabrufdienstes zum Vorausfüllen von Seiten, um die Geschwindigkeit zu erhöhen, kann zu erheblichen Traffic-Zunahmen bei Inhaltsanforderungen führen. |
| DDOS | Adobe unternimmt zwar alle Anstrengungen, um Traffic automatisch aus DDOS-Angriffen zu erkennen und herauszufiltern, es gibt jedoch keine Garantie dafür, dass alle möglichen DDOS-Angriffe erkannt werden. |

### Was passiert, wenn ich mein eigenes CDN verwende? {#using-own-cdn}

Das Dashboard für Inhaltsanforderungen in Cloud Manager zeigt kein Tracking für Ihr eigenes CDN an.
