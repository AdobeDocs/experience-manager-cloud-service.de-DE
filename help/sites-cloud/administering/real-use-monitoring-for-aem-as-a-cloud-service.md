---
title: Real Use Monitoring (RUM) für AEM as a Cloud Service
description: Erfahren Sie, wie Sie mit Real Use Monitoring (RUM) die digitalen User Experience einer Website oder Applikation in Echtzeit erfassen und analysieren können.
exl-id: 91fe9454-3dde-476a-843e-0e64f6f73aaf
feature: Administering
role: Admin
source-git-commit: 9a8adf777008b7a601abc8760cee67ec3c1816c6
workflow-type: tm+mt
source-wordcount: '1301'
ht-degree: 14%

---

# Real Use Monitoring Dienst für AEM als Cloud Service {#real-use-monitoring-service-for-aem-as-a-cloud-service}

>[!NOTE]
>
>Der Real Use Monitoring-Dienst, die Client-seitig Sammlung von Daten, ist ein automatisierter Dienst. Es ist keine Einrichtung durch den Kunden erforderlich.

>[!INFO]
>
>Die Client-seitige Überwachung funktioniert nur für Kunden mit AEM Cloud Service Version **2024.5.16461** und höher.

## Überblick {#overview}

Der Real Use Monitoring (RUM)-Dienst ist eine Leistungsüberwachungstechnologie, die die digitalen User Erfahrungen einer Website oder eines Applikation in Echtzeit erfasst und analysiert. Es bietet Einblick in die Echtzeit-Performance eines Web-Anwendung und bietet tiefere Einblick in die End-User Experience. Der Dienst konzentriert sich auf die Optimierung der Leistung durch die Überwachung der Website-Interaktionen und nicht auf die Benutzer selbst.

Mit RUM werden wichtige Leistungskennzahlen von der Initiierung des URL bis zur Auslieferung des Anfrage an die Browser verfolgt. Es hilft Entwicklern, die Applikation zu verbessern, um sie für Endbenutzer benutzerfreundlich zu machen.

>[!INFO]
>
>&quot;Real User Monitoring&quot; wurde in &quot;Real Use Monitoring&quot; umbenannt, da es das wahre Wesen des Dienstes besser widerspiegelt.

## Wer kann von einem Real Use Monitoring Dienst profitieren? {#who-can-benefit-from-rum-service}

Der Real Use Monitoring-Service ist für alle Kunden von Vorteil. Es bietet ein repräsentatives Spiegelbild User Interaktionen und gewährleistet eine zuverlässige messen der Website-Interaktion, indem es die Anzahl der Client-seitig Seite Aufrufe erfasst.

Für alle Adobe Systems Kunden bietet dieser Service wertvolle Einblicke in User Interaktionen. Kunden, die ihre eigenen CDN einsetzen, können von einer vereinfachten Traffic Berichte profitieren, da Adobe Systems die Datenerfassung jetzt direkt integriert und keine separaten Berichte während der Verlängerungszyklen mehr erforderlich sind.

## Verstehen, wie die Dienst zur Überwachung der realen Nutzung funktioniert {#understand-how-the-rum-service-works}

Adobe Experience Manager (AEM) verwendet Real Use Monitoring (RUM), um Kunden und Adobe Systems dabei zu helfen, zu verstehen, wie Besucher mit AEM Websites interagieren. Es hilft ihnen, Leistungsprobleme zu diagnostizieren und die Effektivität von Experimenten zu messen. RUM bewahrt die Privatsphäre der Besucher durch Sampling - nur ein kleiner Teil aller Seite Ansichten wird überwacht - und es werden keine personenbezogenen Daten (PII) gesammelt.

## Real Use Monitoring Dienst und Datenschutz {#rum-service-and-privacy}

Der Real Use Monitoring-Dienst in AEM wurde entwickelt, um Besucher Privatsphäre zu wahren und Datenerfassung zu minimieren. Als Besucher bedeutet dies, dass die Website, die Sie besuchen oder Adobe Systems zur Verfügung stellen, keine personenbezogenen Daten sammelt.

Als Site-Betreiber sind keine zusätzlichen Opt-in erforderlich, um die Überwachung durch diese Funktion zu aktivieren. Es gibt keine zusätzliche Popup oder Einverständniserklärung, die die Endbenutzer für die Aktivierung von RUM akzeptieren müssen.

## Reale Gebrauchsüberwachung Dienst Daten Probenahme {#rum-service-data-sampling}

Herkömmliche Web-Analyse-Lösungen versuchen, Daten zu allen Besucherinnen und Besuchern zu erfassen. Der RUM-Dienst von AEM erfasst nur Informationen aus einem kleinen Bruchteil der Seite Ansichten. Der Dienst soll nicht als Ersatz für Analyse dienen, sondern als Stichprobenmuster und anonymisiert werden. Standardmäßig haben Seiten ein Sampling-Verhältnis von 1:100. Seitenbetreiber können die Sampling Rate derzeit nicht erhöhen oder verringern. Um die Gesamt Traffic genau zu schätzen, werden für jeweils 100 Seite Ansichten Daten von 1 erfasst, sodass Sie eine zuverlässige Näherung der Gesamt Traffic erhalten.

Die Entscheidung, ob die Daten gesammelt werden, wird Seitenansicht für Seitenansicht getroffen, und es wird praktisch unmöglich, Interaktionen über mehrere Seiten hinweg zu verfolgen. Standardmäßig hat RUM Design kein Konzept von Besuchern oder Sitzungen, sondern nur von Seite Ansichten.

## Welche Daten werden erfasst? {#what-data-is-being-collected}

Der Real Use Monitoring-Dienst wurde entwickelt, um die Sammlung von personenbezogenen Daten zu verhindern. Der vollständige Satz der von RUM gesammelten Informationen ist unten aufgeführt:

* Der Host-Name der besuchten Site, beispielsweise: `experienceleague.adobe.com`
* Der allgemeine User Agententyp und das Betriebssystem, das zum Anzeigen der Seite verwendet wird, z. B.: `desktop:windows` oder `mobile:ios`
* Der Zeitpunkt der Datenerfassung, z. B.: `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`
* Die URL der besuchten Seite, z. B.: `https://experienceleague.adobe.com/docs`
* Die Referrer-URL (die URL der Seite, die mit der aktuellen Seite verknüpft ist, wenn die Person einem Link gefolgt ist)
* Eine zufällig generierte ID der Seitenansicht in einem Format, das dem folgenden ähnelt: `2Ac6`
* Die Gewichtung oder der Kehrwert der Stichprobenrate, beispielsweise: `100`. Das bedeutet, dass nur einer von hundert Seite Aufrufen aufgezeichnet wird
* Der Checkpoint oder Name einer bestimmten Ereignis im Sequenz des Ladens der Seite. Oder als Besucher mit ihm zu interagieren
* Die Quelle oder der Bezeichner des DOM-Elements, mit dem die User für die oben genannten Checkpoint interagiert. Für Instanz könnte es ein Bild sein
* Die Zielgruppe oder der Link zu einer externen Seite oder Ressource, mit der die Person für den oben genannten Checkpoint interagiert. Beispiel: `https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* Die Leistungsmetriken Core Web Vitals (CWV), einschließlich Largest Contentful Paint (LCP), First Eingabefeld Verzögerung (FID), Cumulative Layout Shift (CLS) und Zeit To First Byte (TTFB), die die Qualität der Erlebnis des Besucher beschreiben.

## So funktioniert die reale Nutzung für einen Kunden {#how-rum-works-for-a-customer}

Real Use Monitoring überwacht automatisch Client-seitig Traffic, um Ihnen wertvolle Erkenntnisse zu liefern. Als Adobe Systems Kunde müssen Sie keine zusätzlichen Schritte unternehmen, da sich dieser Service nahtlos in Ihr bestehendes Setup integriert. Mit dem General Availability (GA) Rollout profitieren Sie automatisch von dieser neuen Funktion.

<!-- Alexandru: hiding temporarily, until we figure out where this needs to be linked to 

If you wish to leverage more insights with this new feature to optimize your digital experiences effortlessly, please see here (link to Row 99). -->

## Verwendung von Real Use Monitoring Dienst Daten {#how-rum-service-data-is-being-used}

RUM-Daten sind für folgende Zwecke von Vorteil:

* Identifizieren und Beheben von Leistungsengpässen bei Kunden-Sites
* Zur Optimierung der automatisierten Traffic Suche, die Seite Ansichten einschließt.
* Um zu verstehen, wie AEM mit anderen Skripten (z. B. Analyse, Targeting oder externen Bibliotheken) auf derselben Seite interagiert, um die Kompatibilität zu erhöhen.

## Einschränkungen und Verstehen von Abweichungen bei Seitenansichten und Leistungsmetriken {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

Beim Analysieren von RUM-Daten kann es zu Abweichungen bei Seite Ansichten und anderen Leistungsmetriken kommen. Diese Abweichungen können verschiedenen Faktoren zugeschrieben werden, die mit der Client-seitigen Überwachung in Echtzeit verbunden sind. Im Folgenden finden Sie wichtige Hinweise, die Kundinnen und Kunden bei der Interpretation ihrer RUM-Daten beachten sollten:

1. **Tracker-Blocker**

   * Ende-Benutzer, die Tracker-Blocker oder Datenschutzerweiterungen verwenden, können die RUM-Datenerfassung behindern, da diese Tools die Ausführung der Tracking Skripte einschränken. Diese Einschränkung kann dazu Lead, dass Seite Ansichten und Interaktionen User zu wenig gemeldet werden, wodurch eine Diskrepanz zwischen den tatsächlichen Aktivität der Website und den von RUM erfassten Daten entsteht.

1. **Einschränkungen beim Erfassen von Headless-API-/JSON-Aufrufen**

   * Der RUM-Datendienst konzentriert sich auf die Client-seitig Erlebnis und erfasst derzeit nicht die Back-End-API- oder JSON-Aufrufe, die von einer nicht AEM Headless-App getätigt werden. Der Ausschluss dieser Aufrufe aus RUM-Dienstdaten führt zu Abweichungen von den Inhalte Anforderungen, die von CDN Analytics gemessen werden.

## FAQs {#faq}


1. **Können Kunden die RUM-Service-Skripte in Drittsysteme liken Dynatrace integrieren?**

   Ja. 

1. **Werden Web-Vital-Metriken vom Typ &quot;Interaktion zum nächsten Mal&quot;, &quot;Zeit zum ersten Byte&quot; und &quot;Erster Inhalt zum Anstrich&quot; erfasst?**

   Wechselwirkung mit nächster Farbe (INP) und Zeit mit erstem Byte (TTFB) werden erfasst.  Die erste inhaltsreiche Farbe wird derzeit nicht erfasst.

1. **Das `/.rum` Pfad ist auf meiner Site blockiert, wie kann ich das beheben?**

   Die `/.rum` Pfad ist erforderlich, damit RUM Sammlung funktioniert. Wenn Sie eine CDN vor dem haben, was Adobe Systems als Teil von AEM als Cloud Service bereitstellt, stellen Sie sicher, dass die `/.rum` Pfad an dieselbe AEM Herkunft weiterleitet wie der Rest Ihrer AEM Inhalte. Und stellen Sie sicher, dass es in keiner Weise angepasst wird.

1. **Zählt RUM Sammlung zu Inhalte Anfragen für vertragliche Zwecke?**

   Die RUM-Bibliothek und die RUM-Sammlung zählen nicht als Inhalte-Anforderungen und erhöhen nicht die gemeldete Anzahl Seite-Ansichten oder API-Aufrufe. Darüber hinaus ist Server-seitig Sammlung](#serverside-collection) für Kunden, die vorkonfigurierte CDN mit AEM als Cloud Service verwenden, [die Grundlage für Inhalte Anforderungen.

1. **Wie kann ich Opt-out?**

   Adobe Systems empfiehlt die Verwendung des Real Use Monitoring (RUM), da es erhebliche Vorteile bietet und es Ihnen ermöglicht, Ihre digitalen Erlebnisse zu optimieren. Sie kann wertvolle Erkenntnisse Angebot, die zur Verbesserung der Leistung der Website beitragen können. Der Dienst ist so konzipiert, dass er nahtlos funktioniert und keine Auswirkungen auf die Leistung Ihrer Website hat.

   Wenn Sie sich abmelden, verpassen Sie diese Erkenntnisse. Sollten dennoch Probleme auftreten, wenden Sie sich an den Adobe Systems Support.
