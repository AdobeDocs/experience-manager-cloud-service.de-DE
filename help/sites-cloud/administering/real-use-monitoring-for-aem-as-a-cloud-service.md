---
title: Echtzeit-Nutzungsüberwachung für AEM as a Cloud Service
description: Erfahren Sie, wie Sie mit Real Use Monitoring (RUM) das digitale Benutzererlebnis einer Website oder Anwendung in Echtzeit erfassen und analysieren können.
source-git-commit: a15f973c21044e16751401bd0ffb256a4d0fb17d
workflow-type: tm+mt
source-wordcount: '1409'
ht-degree: 22%

---


>[!NOTE]
>Wir freuen uns, die [GA-Rollout](/help/release-notes/release-notes-cloud/release-notes-current.md#real-use-monitoring) für den Real Use Monitoring-Dienst, die clientseitige Datenerfassung. Es handelt sich um einen automatisierten Dienst, für den kein Kunde eingerichtet werden muss.

# Real Use Monitoring Service für AEM as a Cloud Service {#real-use-monitoring-service-for-aem-as-a-cloud-service}

>[!INFO]
>
>Die clientseitige Überwachung funktioniert nur für Kunden mit AEM Cloud Service-Version **2024.5.16461** und höher.

## Überblick {#overview}

Der Real Use Monitoring (RUM)-Dienst ist eine Technologie zur Leistungsüberwachung, die die digitalen Benutzererlebnisse einer Website oder Anwendung in Echtzeit erfasst und analysiert. Es bietet Einblicke in die Echtzeit-Leistung einer Webanwendung und bietet tiefere Einblicke in das Erlebnis der Endbenutzer. &quot;Real User Monitoring&quot;wurde in &quot;Real Use Monitoring&quot;umbenannt, da es besser das wahre Wesen des Dienstes widerspiegelt, der sich auf die Optimierung der Leistung durch die Überwachung von Website-Interaktionen konzentriert, anstatt auf die Benutzer selbst.

Mit RUM werden wichtige Leistungsmetriken vom Beginn der URL bis zur Rückgabe der Anfrage an den Browser verfolgt. Dies alles hilft den Entwicklern, die Anwendung zu erweitern, um die Verwendung für die Endbenutzer zu vereinfachen.

## Wer kann von einem echten Kontrolldienst für die Verwendung profitieren? {#who-can-benefit-from-rum-service}

Der Real Use Monitoring Service ist für alle Kunden von Vorteil. Es bietet eine repräsentative Darstellung der Benutzerinteraktionen, um eine zuverlässige Messung der Website-Interaktion sicherzustellen, indem die Anzahl der clientseitigen Seitenansichten erfasst wird.

Für alle Adobe-Kunden bietet dieser Dienst wertvolle Einblicke in Benutzerinteraktionen. Kunden, die ihr eigenes CDN verwenden, können von der vereinfachten Traffic-Berichterstellung profitieren, da Adobe jetzt die Datenerfassung direkt integriert, sodass separate Berichte während der Verlängerungszyklen nicht mehr erforderlich sind.

Möchten Sie das gesamte Potenzial Ihrer Website mit dem Visualisierungstool Adobe Early Adopter RUM Explorer nutzen, um nützliche Einblicke in die Interaktion mit Ihrer Website zu erhalten? Dieses Tool kann Einblicke in die Seitenleistung bieten, einschließlich Metriken zur Anzahl der Klicks, Core Web Vitals (CWV), Konversionen und Journey-Maps von Kunden. Mithilfe dieser leistungsstarken Einblicke können Sie Ihre digitalen Erlebnisse optimal anpassen, um die Anforderungen Ihrer Benutzer effizienter zu erfüllen. Wenn Sie mehr erfahren und Zugriff erhalten möchten, wenden Sie sich bitte per E-Mail an uns unter `rum-explorer@adobe.com`.

## Erfahren Sie, wie der Real Use Monitoring Service funktioniert. {#understand-how-the-rum-service-works}

Adobe Experience Manager verwendet die Echtzeit-Nutzungsüberwachung (RUM), um Kunden und Adobe zu helfen, zu verstehen, wie Besucher mit Adobe Experience Manager-Sites interagieren, Leistungsprobleme zu diagnostizieren und die Effektivität von Experimenten zu messen. RUM bewahrt die Privatsphäre der Besucher durch Stichproben auf - nur ein kleiner Teil aller Seitenansichten wird überwacht - und es werden keine personenbezogenen Daten (PII) erfasst.

## Real Use Monitoring Service und Datenschutz {#rum-service-and-privacy}

Der Real Use Monitoring-Dienst in Adobe Experience Manager wurde entwickelt, um den Besucherdatenschutz zu wahren und die Datenerfassung zu minimieren. Als Besucher bedeutet dies, dass keine persönlichen Daten von der Website erfasst werden, die Sie besuchen, oder der Adobe zur Verfügung gestellt werden.

Als Site-Benutzer ist keine zusätzliche Anmeldung erforderlich, um die Überwachung über diese Funktion zu aktivieren. Es gibt kein zusätzliches Popup- oder Zustimmungsformular, das die Endbenutzer für die Aktivierung von RUM akzeptieren können.

## Daten-Sampling für den Real Use Monitoring Service {#rum-service-data-sampling}

Herkömmliche Web-Analyse-Lösungen versuchen, Daten zu allen Besucherinnen und Besuchern zu erfassen. Der RUM-Dienst von Adobe Experience Manager erfasst nur Informationen von einem kleinen Bruchteil der Seitenansichten. Der Dienst ist dazu gedacht, gesampelt und anonymisiert zu werden und nicht als Ersatz für Analytics. Standardmäßig haben Seiten ein Stichprobenverhältnis von 1:100. Site-Operatoren können die Sampling-Rate derzeit nicht erhöhen oder verringern. Um den Traffic insgesamt genau zu schätzen, werden für jede 100 Seitenansichten Daten aus 1 erfasst, sodass Sie eine zuverlässige Annäherung des gesamten Traffics erhalten.

Da die Entscheidung darüber, ob die Daten erfasst werden, für jede einzelne Seitenansicht erfolgt, ist es praktisch unmöglich, Interaktionen über mehrere Seiten hinweg zu verfolgen. Standardmäßig hat RUM kein Konzept von Besuchern oder Sitzungen, sondern nur von Seitenansichten.

## Welche Daten werden erfasst? {#what-data-is-being-collected}

Der Real Use Monitoring Service soll verhindern, dass personenbezogene Daten erfasst werden. Die vollständigen Informationen, die von RUM erfasst werden können, sind unten aufgeführt:

* Der Host-Name der besuchten Site, beispielsweise: `experienceleague.adobe.com`
* Der allgemeine Benutzeragenten-Typ und das Betriebssystem, mit dem die Seite angezeigt wird, z. B.: `desktop:windows` oder `mobile:ios`
* Der Zeitpunkt der Datenerfassung, z. B.: `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`
* Die URL der besuchten Seite, z. B.: `https://experienceleague.adobe.com/docs`
* Die Referrer-URL (die URL der Seite, die mit der aktuellen Seite verknüpft ist, wenn die Person einem Link gefolgt ist)
* Eine zufällig generierte ID der Seitenansicht in einem Format, das dem folgenden ähnelt: `2Ac6`
* Die Gewichtung oder der Kehrwert der Stichprobenrate, beispielsweise: `100`. Dies bedeutet, dass nur ein von hundert Seitenansichten aufgezeichnet wird.
* Der Checkpoint oder Name eines bestimmten Ereignisses in der Abfolge des Ladens der Seite oder der Interaktion mit ihr als Besucherin oder Besucher
* Die Quelle oder die Kennung des DOM-Elements, mit dem die Person für den oben genannten Checkpoint interagiert. Dies kann beispielsweise ein Bild sein.
* Die Zielgruppe oder der Link zu einer externen Seite oder Ressource, mit der die Person für den oben genannten Checkpoint interagiert. Beispiel: `https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* Die Leistungsmetriken für Web Vitals (CWV), einschließlich der größten inhaltsbezogenen Farbe (LCP), der ersten Eingabeverzögerung (FID), der kumulativen Layoutverschiebung (CLS) und der Zeit bis zum ersten Byte (TTFB), die die Erlebnisqualität des Besuchers beschreiben.

## Funktionsweise der Überwachung der tatsächlichen Verwendung für Kunden {#how-rum-works-for-a-customer}

Real Use Monitoring überwacht automatisch den clientseitigen Traffic, um Ihnen wertvolle Einblicke zu bieten. Als Adobe-Kunde müssen Sie keine zusätzlichen Schritte ausführen, da dieser Dienst nahtlos in Ihre bestehende Einrichtung integriert ist. Mit der Einführung der allgemeinen Verfügbarkeit (GA) profitieren Sie automatisch von dieser neuen Funktion.

<!-- Alexandru: hiding temporarily, until we figure out where this needs to be linked to 

If you wish to leverage more insights with this new feature to optimize your digital experiences effortlessly, please see here (link to Row 99). -->

## Verwendung der Daten des Real Use Monitoring Service {#how-rum-service-data-is-being-used}

RUM-Daten sind für folgende Zwecke von Vorteil:

* Identifizieren und Beheben von Leistungsengpässen bei Kunden-Sites
* Zur Optimierung der automatisierten Traffic-Suche, die Seitenansichten enthält.
* Um zu verstehen, wie Adobe Experience Manager mit anderen Skripten (z. B. Analyse, Targeting oder externen Bibliotheken) auf derselben Seite interagiert, und die Kompatibilität zu erhöhen.

## Einschränkungen und Verstehen von Abweichungen bei Seitenansichten und Leistungsmetriken {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

Während Sie RUM-Daten analysieren, kann es Abweichungen bei Seitenansichten und anderen Leistungsmetriken geben. Diese Abweichungen können verschiedenen Faktoren zugeschrieben werden, die mit der Client-seitigen Überwachung in Echtzeit verbunden sind. Im Folgenden finden Sie wichtige Hinweise, die Kundinnen und Kunden bei der Interpretation ihrer RUM-Daten beachten sollten:

1. **Tracker-Blocker**

   * Endbenutzer, die Tracker-Blocker oder Datenschutzerweiterungen verwenden, können die RUM-Datenerfassung behindern, da diese Tools die Ausführung der Tracking-Skripte einschränken. Diese Einschränkung kann zu untergemeldeten Seitenansichten und Benutzerinteraktionen führen, was zu einer Diskrepanz zwischen der tatsächlichen Site-Aktivität und den von RUM erfassten Daten führt.

1. **Einschränkungen bei der Erfassung von Headless-API-/JSON-Aufrufen**

   * Der RUM-Datendienst konzentriert sich auf das clientseitige Erlebnis und erfasst nicht die Backend-API- oder JSON-Aufrufe, die derzeit aus einer nicht AEM Headless-App stammen. Der Ausschluss dieser Aufrufe aus RUM-Dienstdaten führt zu Abweichungen von den von CDN Analytics gemessenen Inhaltsanforderungen.

## FAQs {#faq}


1. **Können Kunden die RUM-Dienstskripte in Drittanbietersysteme wie Dynatrace integrieren?**

   Ja. 

1. **Werden die Web Vitals-Metriken „Interaktion mit der nächsten Farbe“, „Zeit bis zum ersten Byte“ und „Erste inhaltsreiche Farbe“ erfasst?**

   Interaktion mit der nächsten Farbe (INP) und Zeit bis zum ersten Byte (TTFB) werden erfasst.  Die erste inhaltsreiche Farbe wird derzeit nicht erfasst.

1. **Die `/.rum` -Pfad auf meiner Site blockiert ist, wie soll ich ihn beheben?**

   Die `/.rum` Der Pfad ist erforderlich, damit die RUM-Sammlung funktioniert.  Wenn Sie ein CDN vor dem haben, was Adobe als Teil AEM as a Cloud Service bietet, müssen Sie sicherstellen, dass die `/.rum` Der Pfad wird zum gleichen AEM wie der Rest des AEM weitergeleitet.

1. **Zählt die RUM-Erfassung für Inhaltsanforderungen zu vertraglichen Zwecken?**

   Weder die RUM-Bibliothek noch die RUM-Sammlung zählen als Inhaltsanforderungen und erhöhen nicht die gemeldete Anzahl von Seitenansichten oder API-Aufrufen. Zusätzlich können Kunden, die vorkonfiguriertes CDN mit AEM as a Cloud Service verwenden, [Server-seitige Erfassung](#serverside-collection) ist die Grundlage für Inhaltsanforderungen.

1. **Wie kann ich mich abmelden?**

Wir empfehlen dringend die Verwendung der Real Use Monitoring (RUM), da sie erhebliche Vorteile bietet und Ihnen die Möglichkeit bietet, Ihre digitalen Erlebnisse zu optimieren. Es kann wertvolle Einblicke bieten, die die Leistung von Websites verbessern können. Der Dienst ist so konzipiert, dass er nahtlos ist und keine Auswirkungen auf die Leistung Ihrer Website hat.

&quot;Opt-out&quot;bedeutet, diese Einblicke zu verpassen. Sollten Probleme auftreten, wenden Sie sich bitte an den Adobe Support.
