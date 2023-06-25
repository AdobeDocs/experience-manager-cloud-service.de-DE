---
title: Caching und Leistung
description: Erfahren Sie mehr über die verschiedenen verfügbaren Konfigurationen, um GraphQL und Inhalts-Caching zu aktivieren und die Leistung Ihrer Commerce-Implementierung zu optimieren.
exl-id: 21ccdab8-4a2d-49ce-8700-2cbe129debc6
source-git-commit: afbcd1e50a12a9b0642c586d7d81bb90ea91a58d
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 48%

---

# Caching und Leistung {#caching}

## Komponenten- und GraphQL-Antwort-Caching {#graphql}

Die AEM-CIF-Kernkomponenten bieten bereits integrierte Unterstützung für das Caching von GraphQL-Antworten für einzelne Komponenten. Diese Funktion kann verwendet werden, um die Anzahl der GraphQL Backend-Aufrufe erheblich zu reduzieren. Effektives Caching kann insbesondere bei sich wiederholenden Abfragen erreicht werden, z. B. beim Abrufen der Kategoriestruktur für eine Navigationskomponente oder beim Abrufen aller verfügbaren Aggregations-/Facettenwerte, die auf den Produktsuchen- und Kategorieseiten angezeigt werden.

Für die AEM-CIF-Kernkomponenten wird das Caching auf Komponentenbasis konfiguriert, sodass gesteuert werden kann, ob (und wie lange) GraphQL-Anfragen/Antworten für jede Komponente zwischengespeichert werden. Es ist auch möglich, das Caching-Verhalten für OSGi-Services mithilfe des GraphQL-Clients festzulegen.

### Konfiguration {#configuration}

Nach der Konfiguration für eine bestimmte Komponente speichert der Cache die von den einzelnen Cache-Konfigurationseinträgen definierten GraphQL-Abfragen und -Antworten zwischen. Die Größe des Caches und die Caching-Dauer jedes Eintrags werden auf Projektbasis definiert, z. B. abhängig von Folgendem:

* Wie oft sich die Katalogdaten ändern können.
* Wie wichtig es ist, dass eine Komponente immer die neuesten möglichen Daten anzeigt usw.

Es gibt keine Cache-Invalidierung. Seien Sie daher beim Festlegen der Cache-Dauer vorsichtig.

Beim Konfigurieren des Cachings für Komponenten muss der Cache-Name dem Namen der **Proxy-Komponenten** entsprechen, die Sie in Ihrem Projekt definieren.

Bevor der Client eine GraphQL-Anforderung sendet, wird überprüft, ob dies **exact** Dieselbe GraphQL-Anfrage wurde bereits zwischengespeichert und gibt möglicherweise die zwischengespeicherte Antwort zurück. Übereinstimmung mit der GraphQL-Anforderung _must_ exakt übereinstimmen. Das heißt die Abfrage, den Vorgangsnamen (falls vorhanden), Variablen (falls vorhanden). _must_ alle der zwischengespeicherten Anforderung entsprechen. Und alle benutzerdefinierten HTTP-Header, die festgelegt werden können _must_ auch identisch sein. Beispielsweise die Adobe Commerce `Store` header _must_ übereinstimmen.

### Beispiele {#examples}

Adobe empfiehlt, dass Sie das Zwischenspeichern für den Suchdienst konfigurieren, der alle verfügbaren Aggregations-/Facettenwerte abruft, die auf den Produktsuche- und Kategorieseiten angezeigt werden. Diese Werte ändern sich normalerweise nur, wenn beispielsweise ein neues Attribut zu Produkten hinzugefügt wird. Daher kann die Dauer für diesen Cache-Eintrag &quot;groß&quot;sein, wenn sich der Satz von Produktattributen nicht häufig ändert. Obwohl dieser Eintrag projektspezifisch ist, empfiehlt Adobe Werte von einigen Minuten in Projektentwicklungsphasen und einige Stunden in stabilen Produktionssystemen.

Diese Einstellung wird normalerweise mit dem folgenden Cache-Eintrag konfiguriert:

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:10:3600
```

Ein weiteres Beispiel für die Verwendung der GraphQl-Caching-Funktion ist die Navigationskomponente. Der Grund dafür ist, dass auf allen Seiten dieselbe GraphQL-Abfrage gesendet wird. In diesem Fall wird der Caching-Eintrag normalerweise auf Folgendes festgelegt:

```
venia/components/structure/navigation:true:10:600
```

In der Erwägung, dass das [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia) verwendet. Beachten Sie, dass der Komponenten-Proxy-Namen `venia/components/structure/navigation` und **nicht** der Name der CIF-Navigationskomponente (`core/cif/components/structure/navigation/v1/navigation`) verwendet wird.

Das Caching für andere Komponenten sollte auf Projektbasis definiert werden, üblicherweise in Abstimmung mit dem auf Dispatcher-Ebene konfigurierten Cachings. Beachten Sie, dass diese Cashes nicht invalidiert werden, daher sollte die Caching-Dauer mit Umsicht festgelegt werden. Es gibt keine „Universalwerte“, die sich für alle Projekte und Anwendungsfälle eignen. Stellen Sie sicher, dass Sie eine Caching-Strategie auf Projektebene definieren, die den Anforderungen Ihres Projekts am besten entspricht.

## Dispatcher-Caching {#dispatcher}

Das Caching von AEM-Seiten oder -Fragmenten in [AEM Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de) gilt als Best Practice für AEM-Projekte. Normalerweise beruht es auf Invalidierungsverfahren, die sicherstellen, dass alle in AEM geänderten Inhalte in AEM Dispatcher ordnungsgemäß aktualisiert werden. Diese Funktion ist von zentraler Bedeutung für die AEM Dispatcher-Caching-Strategie.

Neben dem reinen CIF für AEM-verwaltete Inhalte kann eine Seite in der Regel Commerce-Daten anzeigen, die dynamisch über GraphQL aus Adobe Commerce abgerufen werden. Während sich die Seitenstruktur selbst möglicherweise nie ändert, ändert sich der Commerce-Inhalt möglicherweise. Wenn sich beispielsweise Produktdaten wie Name und Preis in Adobe Commerce ändern.

Um sicherzustellen, dass CIF-Seiten für eine begrenzte Zeit im AEM Dispatcher zwischengespeichert werden, empfiehlt Adobe die Verwendung von [Zeitbasierte Cache-Invalidierung](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#configuring-time-based-cache-invalidation-enablettl) (TTL-basierte Zwischenspeicherung) beim Zwischenspeichern von CIF-Seiten im AEM Dispatcher. Diese Funktion kann AEM mit dem zusätzlichen [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/)-Paket konfiguriert werden.

Beim TTL-basierten Caching definiert ein Entwickler normalerweise eine oder mehrere Caching-Dauerangaben für bestimmte AEM-Seiten. Diese Dauer stellt sicher, dass CIF-Seiten nur bis zur konfigurierten Dauer im AEM Dispatcher zwischengespeichert werden und der Inhalt häufig aktualisiert wird.

>[!NOTE]
>
>Während Server-seitige Daten vom AEM Dispatcher zwischengespeichert werden können, enthalten einige CIF-Komponenten wie die `product`, `productlist`und `searchresults` -Komponenten entsprechen in der Regel immer den Produktpreisen in einer clientseitigen Browser-Anforderung, wenn die Seite geladen wird. Dadurch wird sichergestellt, dass beim Laden der Seite immer wichtige dynamische Inhalte abgerufen werden.

## Zusätzliche Ressourcen {#additional}

* [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia)
* [GraphQL-Caching-Konfiguration](https://github.com/adobe/commerce-cif-graphql-client#caching)
* [AEM Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de)
