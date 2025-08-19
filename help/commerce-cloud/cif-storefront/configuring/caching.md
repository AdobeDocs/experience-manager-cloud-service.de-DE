---
title: Caching und Leistung
description: Erfahren Sie mehr über die verschiedenen verfügbaren Konfigurationen, um GraphQL und Inhalts-Caching zu aktivieren und die Leistung Ihrer Commerce-Implementierung zu optimieren.
exl-id: 21ccdab8-4a2d-49ce-8700-2cbe129debc6
feature: Commerce Integration Framework
role: Admin
index: false
source-git-commit: 80bd8da1531e009509e29e2433a7cbc8dfe58e60
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 99%

---


# Caching und Leistung {#caching}

## Komponenten- und GraphQL-Antwort-Caching {#graphql}

Die AEM-CIF-Kernkomponenten bieten bereits integrierte Unterstützung für das Caching von GraphQL-Antworten für einzelne Komponenten. Diese Funktion kann verwendet werden, um die Anzahl der GraphQL Backend-Aufrufe erheblich zu reduzieren. Effektives Caching kann insbesondere bei sich wiederholenden Abfragen erreicht werden, z. B. beim Abrufen der Kategoriestruktur für eine Navigationskomponente oder beim Abrufen aller verfügbaren Aggregations-/Facettenwerte, die auf den Produktsuchen- und Kategorieseiten angezeigt werden.

Für die AEM-CIF-Kernkomponenten wird das Caching auf Komponentenbasis konfiguriert, sodass gesteuert werden kann, ob (und wie lange) GraphQL-Anfragen/Antworten für jede Komponente zwischengespeichert werden. Es ist auch möglich, das Caching-Verhalten für OSGi-Services mithilfe des GraphQL-Clients festzulegen.

### Konfiguration {#configuration}

Nach der Konfiguration für eine bestimmte Komponente speichert der Cache die von den einzelnen Cache-Konfigurationseinträgen definierten GraphQL-Abfragen und -Antworten zwischen. Die Größe des Cache und die Caching-Dauer jedes Eintrags werden auf Projektbasis definiert, z. B. abhängig von Folgendem:

* Wie oft sich die Katalogdaten ändern können.
* Wie wichtig es ist, dass eine Komponente immer die neuesten möglichen Daten anzeigt usw.

Es gibt keine Invalidierung des Caches. Seien Sie daher beim Festlegen der Dauer des Cache vorsichtig.

Beim Konfigurieren des Cachings für Komponenten muss der Cache-Name dem Namen der **Proxy-Komponenten** entsprechen, die Sie in Ihrem Projekt definieren.

Bevor der Client eine GraphQL-Anfrage sendet, prüft er, ob **exakt** diese GraphQL-Anfrage bereits zwischengespeichert ist, und gibt ggf. die zwischengespeicherte Antwort zurück. Für eine Übereinstimmung _muss_ die GraphQL-Anfrage exakt übereinstimmen. Das heißt, sowohl die Abfrage als auch der Vorgangsname (falls vorhanden) und die Variablen (falls vorhanden) _müssen_ der zwischengespeicherten Anfrage entsprechen. Außerdem _müssen_ alle benutzerdefinierten HTTP-Header, die möglicherweise festgelegt werden, auch identisch sein. Beispielsweise _muss_ beim Adobe Commerce-`Store`-Header eine Übereinstimmung vorliegen.

### Beispiele {#examples}

Adobe empfiehlt, zum Konfigurieren des Cachings für den Such-Service alle verfügbaren Aggregations-/Facettenwerte abzurufen, die auf den Produktsuch- und Kategorieseiten angezeigt werden. Diese Werte ändern sich normalerweise nur, wenn beispielsweise ein neues Attribut zu Produkten hinzugefügt wird. Daher kann die Dauer für diesen Cache-Eintrag „groß“ sein, wenn sich der Satz von Produktattributen nicht häufig ändert. Auch wenn dieser Eintrag projektspezifisch ist, empfiehlt Adobe, diese Werte für Projektentwicklungsphasen auf wenige Minuten und für stabile Produktionssysteme auf einige Stunden festzulegen.

Diese Einstellung wird in der Regel mit dem folgenden Cache-Eintrag konfiguriert:

```text
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:10:3600
```

Ein weiteres Beispiel-Szenario für die Verwendung der GraphQl-Caching-Funktion ist die Navigationskomponente. Der Grund dafür ist, dass auf allen Seiten dieselbe GraphQL-Abfrage gesendet wird. In diesem Fall wird der Caching-Eintrag normalerweise auf Folgendes festgelegt:

```text
venia/components/structure/navigation:true:10:600
```

Dabei wird vorausgesetzt, dass die [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia) verwendet wird. Beachten Sie, dass der Komponenten-Proxy-Namen `venia/components/structure/navigation` und **nicht** der Name der CIF-Navigationskomponente (`core/cif/components/structure/navigation/v1/navigation`) verwendet wird.

Das Caching für andere Komponenten sollte auf Projektbasis definiert werden, üblicherweise in Abstimmung mit dem auf Dispatcher-Ebene konfigurierten Cachings. Beachten Sie, dass diese Caches nicht invalidiert werden, daher sollte die Caching-Dauer mit Umsicht festgelegt werden. Es gibt keine „Universalwerte“, die sich für alle Projekte und Anwendungsfälle eignen. Stellen Sie sicher, dass Sie eine Caching-Strategie auf Projektebene definieren, die den Anforderungen Ihres Projekts am besten entspricht.

## Dispatcher-Caching {#dispatcher}

Das Caching von AEM-Seiten oder -Fragmenten in [AEM Dispatcher](https://experienceleague.adobe.com/de/docs/experience-manager-dispatcher/using/dispatcher) gilt als Best Practice für AEM-Projekte. Normalerweise beruht es auf Invalidierungsverfahren, die sicherstellen, dass alle in AEM geänderten Inhalte in AEM Dispatcher ordnungsgemäß aktualisiert werden. Diese Funktion ist von zentraler Bedeutung für die AEM Dispatcher-Caching-Strategie.

Neben den rein von AEM verwalteten Inhalten kann eine CIF-Seite in der Regel Commerce-Daten anzeigen, die dynamisch über GraphQL von Adobe Commerce abgerufen werden. Zwar ändert sich die Seitenstruktur selbst möglicherweise nie, aber dafür kann sich der Commerce-Inhalt möglicherweise ändern. Wenn sich beispielsweise Produktdaten wie Name und Preis in Adobe Commerce ändern.

Um sicherzustellen, dass CIF-Seiten für eine begrenzte Zeit im AEM Dispatcher zwischengespeichert werden, empfiehlt Adobe die Verwendung von [zeitbasierter Cache-Invalidierung](https://experienceleague.adobe.com/en/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration#configuring-time-based-cache-invalidation-enablettl) (bezeichnet als TTL-basierte Zwischenspeicherung) beim Zwischenspeichern von CIF-Seiten im AEM Dispatcher. Diese Funktion kann AEM mit dem zusätzlichen [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/)-Paket konfiguriert werden.

Beim TTL-basierten Caching definiert ein Entwickler normalerweise eine oder mehrere Caching-Dauerangaben für bestimmte AEM-Seiten. Durch diese Dauer wird sichergestellt, dass CIF-Seiten nur bis zur konfigurierten Dauer in AEM Dispatcher zwischengespeichert werden und die Inhalte häufig aktualisiert werden.

>[!NOTE]
>
>Während Server-seitige Daten von AEM Dispatcher zwischengespeichert werden können, rufen einige CIF-Komponenten wie die `product`-, `productlist`- und `searchresults`-Komponenten die Produktpreise in der Regel immer in einer Client-seitigen Browser-Anfrage erneut ab, wenn die Seite geladen wird. Dadurch wird sichergestellt, dass beim Laden der Seite immer die wesentlichen dynamischen Inhalte abgerufen werden.

## Zusätzliche Ressourcen {#additional}

* [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia)
* [GraphQL-Caching-Konfiguration](https://github.com/adobe/commerce-cif-graphql-client#caching)
* [AEM Dispatcher](https://experienceleague.adobe.com/de/docs/experience-manager-dispatcher/using/dispatcher)
