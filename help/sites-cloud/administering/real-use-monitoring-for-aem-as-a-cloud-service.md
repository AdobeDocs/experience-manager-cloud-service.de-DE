---
title: Real Use Monitoring (RUM) für AEM as a Cloud Service
description: Erfahren Sie mehr über Real Use Monitoring (RUM), einen automatisierten Dienst, der die Überwachung der Client-seitigen Datenerfassung ermöglicht.
exl-id: 91fe9454-3dde-476a-843e-0e64f6f73aaf
feature: Administering
role: Admin
source-git-commit: f3091a3868ac57150afd6f1640709ce3e9566bac
workflow-type: ht
source-wordcount: '913'
ht-degree: 100%

---

# Real Use Monitoring-Dienst für AEM as a Cloud Service {#real-use-monitoring-service-for-aem-as-a-cloud-service}

>[!NOTE]
>
>Der Real Use Monitoring-Dienst, die Client-seitige Datenerfassung, ist ein automatisierter Dienst. Es ist keine Kundeneinrichtung erforderlich.

>[!INFO]
>
>Die Client-seitige Überwachung funktioniert nur für Kundinnen und Kunden mit Version **2024.5.16461** und höher von AEM (Adobe Experience Manager) Cloud Service.

## Überblick {#overview}

Der RUM(Real Use Monitoring)-Dienst ist eine Technologie zur Leistungsüberwachung, die den Client-seitigen Traffic auf einer Website oder in einer Anwendung in Echtzeit überwacht. Dieser Dienst konzentriert sich auf die Erfassung von Metriken und Daten, die wichtig für die Leistungsoptimierung sind, indem er Website-Interaktionen und nicht die Benutzenden selbst überwacht. Mit RUM werden wichtige Leistungsmetriken direkt von der Initiierung der URL bis zur Rückgabe der Anfrage an den Browser verfolgt.

## Wer kann vom Real Use Monitoring-Dienst profitieren? {#who-can-benefit-from-rum-service}

Real Use Monitoring hilft Kundinnen und Kunden sowie Adobe, zu verstehen, wie Endbenutzende mit AEM Sites interagieren. Real Use Monitoring bewahrt die Privatsphäre der Besucherinnen und Besucher durch eine begrenzte Datenerfassung und Stichproben. Nur ein kleiner Teil aller Seitenansichten wird überwacht.

## Daten-Sampling für den Real Use Monitoring-Dienst {#rum-service-data-sampling}

Herkömmliche Web-Analyse-Lösungen versuchen, Daten zu allen Besucherinnen und Besuchern zu erfassen. Der Real Use Monitoring(RUM)-Dienst von AEM erfasst nur Informationen aus einem kleinen Bruchteil der Seitenansichten. Der Dienst ist für Stichproben und zur Anonymisierung gedacht und soll die Analyse nicht ersetzen. Standardmäßig haben Seiten ein Stichprobenverhältnis von 1:100. Site-Operatoren können die Stichprobenrate derzeit nicht erhöhen oder verringern. Um den gesamten Traffic genau zu schätzen, werden für jeweils 100 Seitenansichten Daten von einer Ansicht erfasst, um Ihnen einen zuverlässigen Näherungswert des gesamten Traffics zu liefern.

Da die Entscheidung darüber, ob die Daten erfasst werden, jeweils für jede einzelne Seitenansicht erfolgt, ist es praktisch unmöglich, Interaktionen über mehrere Seiten hinweg zu verfolgen. RUM hat absichtlich kein Konzept von Besuchenden oder Sitzungen, sondern nur von Seitenansichten.

## Welche Daten werden erfasst? {#what-data-is-being-collected}

Der Real Use Monitoring-Dienst wurde entwickelt, um die Datenerfassung zu minimieren. Die vollständigen Informationen, die vom RUM erfasst werden, finden Sie im Folgenden:

* Der Host-Name der besuchten Site, beispielsweise: `experienceleague.adobe.com`
* Der allgemeine Benutzeragenten-Typ und das zur Anzeige der Seite verwendete Betriebssystem, z. B. `desktop:windows` oder `mobile:ios`
* Der Zeitpunkt der Datenerfassung, z. B.: `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`
* Die URL der besuchten Seite, z. B.: `https://experienceleague.adobe.com/docs?lang=de`
* Die Referrer-URL (die URL der Seite, die mit der aktuellen Seite verknüpft ist, wenn die Person einem Link gefolgt ist)
* Eine zufällig generierte ID der Seitenansicht in einem Format, das dem folgenden ähnelt: `2Ac6`
* Die Gewichtung oder der Kehrwert der Stichprobenrate, beispielsweise: `100`. Das bedeutet, dass nur eine von hundert Seitenansichten aufgezeichnet wird.
* Der Checkpoint oder Name eines bestimmten Ereignisses in der Abfolge des Ladens der Seite. Oder die Interaktion mit ihr als Besucherin bzw. Besucher.
* Die Quelle oder die Kennung des DOM-Elements, mit dem die Person für den oben genannten Checkpoint interagiert. Dies kann beispielsweise ein Bild sein
* Die Zielgruppe oder der Link zu einer externen Seite oder Ressource, mit der die Person für den oben genannten Checkpoint interagiert. Beispiel: `https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* Die Leistungsmetriken [Core Web Vitals (CWV)](https://web.dev/articles/lcp), [Largest Contentful Paint (LCP)](https://web.dev/articles/lcp), [First Input Delay (FID)](https://web.dev/articles/inp) und [Cumulative Layout Shift (CLS)](https://web.dev/articles/cls), die die Erlebnisqualität der Besucherin bzw. des Besuchers beschreiben.

## Funktionsweise von Real Use Monitoring für Kundinnen und Kunden {#how-rum-works-for-a-customer}

Real Use Monitoring überwacht automatisch den Client-seitigen Traffic. Als Adobe-Kundin bzw. -Kunde müssen Sie keine zusätzlichen Schritte ausführen, da dieser Dienst nahtlos in Ihre bestehende Einrichtung integriert ist. Da der Real Use Monitoring(RUM)-Dienst allgemein verfügbar ist, profitieren Sie automatisch von dieser neuen Funktion. Der Real Use Monitoring-Dienst stellt derzeit keine kundenrelevanten Metriken zur Überwachung bereit. Wir arbeiten daran, Ihnen diese Funktion so schnell wie möglich zur Verfügung zu stellen.

<!-- Alexandru: hiding temporarily, until we figure out where this needs to be linked to 

If you wish to leverage more insights with this new feature to optimize your digital experiences effortlessly, please see here (link to Row 99). -->

## Verwendung von Real Use Monitoring durch Adobe {#how-rum-data-is-being-used}

Die Real Use Monitoring-Daten werden für folgende Zwecke verwendet:

* Identifizieren und Beheben von Leistungsengpässen bei Kunden-Sites
* Um zu verstehen, wie AEM mit anderen Skripten (z. B. Analyse, Targeting oder externen Bibliotheken) auf derselben Seite interagiert, und die Kompatibilität zu erhöhen.
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

1. **Werden die Metriken „Interaction To Next Paint“, „Time To First Byte“ und „First Contentful Paint“ erfasst?**

   „Interaction To Next Paint“ (INP) und „Time To First Byte“ (TTFB) werden erfasst.  „First Contentful Paint“ wird derzeit nicht erfasst.

1. **Der Pfad `/.rum` ist auf meiner Website blockiert. Wie gehe ich zur Fehlerbehebung vor?**

   Der Pfad `/.rum` ist erforderlich, damit die RUM-Erfassung funktioniert. Wenn Sie vor AEM as a Cloud Service von Adobe ein CDN verwenden, stellen Sie sicher, dass der Pfad `/.rum` Weiterleitungen zum selben AEM-Ursprung wie Ihre übrigen AEM-Inhalte vornimmt. Stellen Sie außerdem sicher, dass er in keiner Weise angepasst wird.

1. **Zählt die RUM-Erfassung zu den Inhaltsanfragen im Rahmen des Vertrags?**

   Die RUM-Bibliothek und die RUM-Erfassung zählen nicht als Inhaltsanfragen und erhöhen nicht die gemeldete Anzahl von Seitenansichten oder API-Aufrufen. Darüber hinaus bildet für Kundinnen und Kunden, die das vordefinierte CDN mit AEM as a Cloud Service verwenden, die [Server-seitige Erfassung](#serverside-collection) die Grundlage für Inhaltsanfragen.

1. **Wie kann ich RUM deaktivieren?**

   Adobe empfiehlt die Verwendung des Real Use Monitoring (RUM) aufgrund seiner wesentlichen Vorteile und weil es Adobe ermöglicht, Ihre digitalen Erlebnisse zu optimieren, indem die Website-Leistung verbessert wird. Der Dienst ist nahtlos konzipiert und hat keine Auswirkungen auf die Leistung Ihrer Website.

   Wenn Sie sich davon abmelden, könnten Sie die Chance verpassen, die Traffic-Interaktion auf Ihrer Website zu verbessern. Sollten Sie jedoch auf Probleme stoßen, wenden Sie sich an den Adobe-Support.