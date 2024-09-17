---
title: Real Use Monitoring (RUM) für AEM as a Cloud Service
description: Erfahren Sie mehr über Real Use Monitoring (RUM) , einen automatisierten Dienst, der die Überwachung der clientseitigen Datenerfassung ermöglicht.
exl-id: 91fe9454-3dde-476a-843e-0e64f6f73aaf
feature: Administering
role: Admin
source-git-commit: fbc3358f1be3ae7ce3142cdc84815d304a2d6c38
workflow-type: tm+mt
source-wordcount: '1009'
ht-degree: 13%

---

# Real Use Monitoring Service für AEM as a Cloud Service {#real-use-monitoring-service-for-aem-as-a-cloud-service}

>[!NOTE]
>
>Der Real Use Monitoring-Dienst, die clientseitige Datenerfassung, ist ein automatisierter Dienst. Es ist keine Kundeneinrichtung erforderlich.

>[!INFO]
>
>Die clientseitige Überwachung funktioniert nur für Kunden mit AEM (Adobe Experience Manager) Cloud Service-Version **2024.5.16461** und höher.

## Übersicht {#overview}

Der RUM-Dienst (Real Use Monitoring) ist eine Technologie zur Leistungsüberwachung, die den clientseitigen Traffic auf einer Website oder einer Anwendung in Echtzeit überwacht. Dieser Dienst konzentriert sich auf die Erfassung von Metriken und Daten, die für die Leistungsoptimierung durch die Überwachung von Website-Interaktionen und nicht von den Benutzern selbst benötigt werden. Mit RUM werden wichtige Leistungsmetriken direkt von der Initiierung der URL bis zur Rückgabe der Anfrage an den Browser verfolgt.

## Wer kann von einem echten Anwendungsüberwachungsdienst profitieren? {#who-can-benefit-from-rum-service}

Die Überwachung der tatsächlichen Verwendung hilft Kunden und Adobe, zu verstehen, wie Endbenutzer mit AEM Sites interagieren. Bei der Überwachung der tatsächlichen Verwendung werden Leistungsprobleme diagnostiziert und die Effektivität von Experimenten gemessen. Die Überwachung der tatsächlichen Verwendung wahrt den Datenschutz von Besuchern durch Stichproben - nur ein kleiner Teil aller Seitenansichten wird überwacht - und es werden keine personenbezogenen Daten (PII) erfasst.

## Überwachungsdienst für die tatsächliche Verwendung und Datenschutz {#rum-service-and-privacy}

Der Real Use Monitoring-Dienst in AEM bewahrt den Datenschutz der Besucher und minimiert die Datenerfassung. Als Besucher bedeutet dies, dass die Website, die Sie besuchen oder der Adobe zur Verfügung gestellt werden, keine personenbezogenen Daten erfasst.

Als Site-Benutzer ist keine zusätzliche Anmeldung erforderlich, um die Überwachung über diese Funktion zu aktivieren. Es gibt kein zusätzliches Popup- oder Zustimmungsformular, das die Endbenutzer für die Aktivierung von RUM akzeptieren können.

## Datenstichproben für den Real Use Monitoring-Dienst {#rum-service-data-sampling}

Herkömmliche Web-Analyse-Lösungen versuchen, Daten zu allen Besucherinnen und Besuchern zu erfassen. AEM Real Use Monitoring (RUM)-Dienst erfasst nur Informationen aus einem kleinen Bruchteil der Seitenansichten. Der Dienst ist dazu gedacht, gesampelt und anonymisiert zu werden und nicht als Ersatz für Analytics. Standardmäßig haben Seiten ein Stichprobenverhältnis von 1:100. Site-Operatoren können die Sampling-Rate derzeit nicht erhöhen oder verringern. Um den Traffic insgesamt genau zu schätzen, werden für jede 100 Seitenansichten Daten aus 1 erfasst, sodass Sie eine zuverlässige Annäherung des gesamten Traffics erhalten.

Bei der Entscheidung, ob die Daten erfasst werden, erfolgt dies auf Seitenansichtsbasis und es ist praktisch unmöglich, Interaktionen auf mehreren Seiten zu verfolgen. Standardmäßig hat RUM kein Konzept von Besuchern oder Sitzungen, sondern nur von Seitenansichten.

## Welche Daten werden erfasst? {#what-data-is-being-collected}

Der Real Use Monitoring Service soll verhindern, dass personenbezogene Daten erfasst werden. Die vollständigen Informationen, die von RUM gesammelt wurden, sind unten aufgeführt:

* Der Host-Name der besuchten Site, beispielsweise: `experienceleague.adobe.com`
* Der allgemeine Benutzeragenten-Typ und das Betriebssystem, mit dem die Seite angezeigt wird, z. B.: `desktop:windows` oder `mobile:ios`
* Der Zeitpunkt der Datenerfassung, z. B.: `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`
* Die URL der besuchten Seite, z. B.: `https://experienceleague.adobe.com/docs`
* Die Referrer-URL (die URL der Seite, die mit der aktuellen Seite verknüpft ist, wenn die Person einem Link gefolgt ist)
* Eine zufällig generierte ID der Seitenansicht in einem Format, das dem folgenden ähnelt: `2Ac6`
* Die Gewichtung oder der Kehrwert der Stichprobenrate, beispielsweise: `100`. Das bedeutet, dass nur ein von hundert Seitenansichten aufgezeichnet wird.
* Checkpoint oder Name eines bestimmten Ereignisses in der Abfolge des Ladens der Seite. Oder interagieren mit ihr als Besucher
* Die Quelle oder Kennung des DOM-Elements, mit dem der Benutzer für den oben genannten Checkpoint interagiert. Es kann sich beispielsweise um ein Bild handeln
* Die Zielgruppe oder der Link zu einer externen Seite oder Ressource, mit der die Person für den oben genannten Checkpoint interagiert. Beispiel: `https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* Die Leistungsmetriken für Web Vitals (CWV), einschließlich der größten inhaltsbezogenen Farbe (LCP), der ersten Eingabeverzögerung (FID), der kumulativen Layoutverschiebung (CLS) und der Zeit bis zum ersten Byte (TTFB), die die Erlebnisqualität des Besuchers beschreiben.

## Funktionsweise der Echtzeit-Nutzungsüberwachung für Kunden {#how-rum-works-for-a-customer}

Die Überwachung der tatsächlichen Verwendung überwacht automatisch den clientseitigen Traffic. Als Adobe-Kunde müssen Sie keine zusätzlichen Schritte ausführen, da dieser Dienst nahtlos in Ihre bestehende Einrichtung integriert ist. Da der Real Use Monitoring (RUM)-Dienst allgemein verfügbar ist, profitieren Sie automatisch von dieser neuen Funktion. Der Real Use Monitoring-Dienst stellt heute keine kundenrelevanten Metriken zur Überwachung bereit. Wir arbeiten daran, Ihnen diese Funktion so schnell wie möglich zur Verfügung zu stellen.

<!-- Alexandru: hiding temporarily, until we figure out where this needs to be linked to 

If you wish to leverage more insights with this new feature to optimize your digital experiences effortlessly, please see here (link to Row 99). -->

## Wie Adobe die Echtuse-Überwachung verwendet {#how-rum-data-is-being-used}

Die Daten zur Überwachung der tatsächlichen Verwendung werden für folgende Zwecke verwendet:

* Identifizieren und Beheben von Leistungsengpässen bei Kunden-Sites
* Um zu verstehen, wie AEM mit anderen Skripten (z. B. Analyse-, Targeting- oder externen Bibliotheken) auf derselben Seite interagiert, können Sie die Kompatibilität erhöhen.
<!--
## Limitations and understanding variance in page views and performance metrics {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

Here are key considerations for customers to keep in mind when interpreting their RUM data:

1. **Tracker blockers**

   * End-users employing tracker blockers or privacy extensions can impede RUM data collection, as these tools restrict the tracking scripts' execution. This restriction may lead to underreported page views and user interactions, creating a discrepancy between actual site activity and the data captured by RUM.

1. **Limitations in capturing headless API/JSON calls**

   * RUM data service focuses on the client-side experience and doesn't capture the backend API or JSON calls made from a non-AEM headless app at this time. The exclusion of these calls from RUM service data creates variances from the content requests measured by CDN Analytics.
-->

## Häufig gestellte Fragen {#faq}

<!-- REMOVED THIS FAQ AS PER EMAIL REQUEST FROM SHWETA DUA, SEPTEMBER 4, 2024 TO THE DL-AEM-DOCS GROUP 
1. **Can customers integrate the RUM service scripts with third-party systems like Dynatrace?**

   Yes.
-->

1. **Werden die Metriken &quot;Interaktion mit der nächsten Farbe&quot;, &quot;Zeit bis zum ersten Byte&quot;und &quot;Erste inhaltsreiche Farbe&quot;erfasst?**

   Die Interaktion mit der nächsten Farbe (INP) und der Zeit bis zum ersten Byte (TTFB) werden erfasst.  Die erste inhaltsreiche Farbe wird derzeit nicht erfasst.

1. **Der Pfad `/.rum` ist auf meiner Site blockiert. Wie soll ich beheben?**

   Der Pfad `/.rum` ist erforderlich, damit die RUM-Sammlung funktioniert. Wenn Sie das CDN vor einem Adobe AEM as a Cloud Service verwenden, stellen Sie sicher, dass der Pfad `/.rum` zum selben AEM wie Ihr anderer AEM weitergeleitet wird. Und stellen Sie sicher, dass sie in keiner Weise angepasst wird.

1. **Zählt die RUM-Erfassung für Inhaltsanforderungen aus vertraglichen Gründen?**

   Die RUM-Bibliothek und die RUM-Sammlung zählen nicht als Inhaltsanfragen und erhöhen nicht die gemeldete Anzahl von Seitenansichten oder API-Aufrufen. Darüber hinaus bildet die [serverseitige Erfassung](#serverside-collection) für Kunden, die das vordefinierte CDN mit AEM as a Cloud Service verwenden, die Grundlage für Inhaltsanforderungen.

1. **Wie kann ich mich abmelden?**

   Adobe empfiehlt die Verwendung des Real Use Monitoring (RUM) aufgrund seiner wesentlichen Vorteile und dass es Adobe ermöglicht, Ihre digitalen Erlebnisse zu optimieren, indem die Website-Performance verbessert wird. Der Dienst ist nahtlos konzipiert und hat keine Auswirkungen auf die Leistung Ihrer Website.

   Die Abmeldung kann bedeuten, dass Sie eine Chance verpassen, die Traffic-Interaktion auf Ihrer Website zu verbessern. Sollten Sie dennoch auf Probleme stoßen, wenden Sie sich an den Adobe Support.