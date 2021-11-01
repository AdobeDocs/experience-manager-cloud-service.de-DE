---
title: Caching und Leistung
description: Erfahren Sie mehr über die verschiedenen verfügbaren Konfigurationen, um GraphQL und Inhalts-Caching zu aktivieren und die Leistung Ihrer Commerce-Implementierung zu optimieren.
exl-id: 21ccdab8-4a2d-49ce-8700-2cbe129debc6,8b969821-5073-4540-a997-95c74a11e4f0
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 100%

---

# Caching und Leistung {#caching}

## Komponenten- und GraphQL-Antwort-Caching {#graphql}

Die AEM-CIF-Kernkomponenten bieten bereits integrierte Unterstützung für das Caching von GraphQL-Antworten für einzelne Komponenten. Diese Funktion kann verwendet werden, um die Anzahl der GraphQL Backend-Aufrufe erheblich zu reduzieren. Effektives Caching kann insbesondere bei sich wiederholenden Abfragen erreicht werden, z. B. beim Abrufen der Kategoriestruktur für eine Navigationskomponente oder beim Abrufen aller verfügbaren Aggregations-/Facettenwerte, die auf den Produktsuchen- und Kategorieseiten angezeigt werden.

Für die AEM-CIF-Kernkomponenten wird das Caching auf Komponentenbasis konfiguriert, sodass gesteuert werden kann, ob (und wie lange) GraphQL-Anfragen/Antworten für jede Komponente zwischengespeichert werden. Es ist auch möglich, das Caching-Verhalten für OSGi-Services mithilfe des GraphQL-Clients festzulegen.

### Konfiguration

Nach der Konfiguration für eine bestimmte Komponente speichert der Cache die von den einzelnen Cache-Konfigurationseinträgen definierten GraphQL-Abfragen und -Antworten zwischen. Die Größe des Caches und die Caching-Dauer jedes Eintrags sind auf Projektbasis festzulegen, z. B. je nachdem, wie oft sich die Katalogdaten ändern können, oder wie wichtig es ist, dass eine Komponente immer die neuestmöglichen Daten anzeigt. Beachten Sie, dass der Cache nicht invalidiert wird. Gehen Sie daher beim Festlegen der Caching-Dauer umsichtig vor.

Beim Konfigurieren des Cachings für Komponenten muss der Cache-Name dem Namen der **Proxy-Komponenten** entsprechen, die Sie in Ihrem Projekt definieren.

Bevor der Client eine GraphQL-Anfrage sendet, prüft er, ob **exakt** diese GraphQL-Anfrage bereits zwischengespeichert ist und gibt ggf. die zwischengespeicherte Antwort zurück. Für diese Zuordnung muss die GraphQL-Anfrage exakt übereinstimmen, d. h. die Abfrage, der Vorgangsname (falls vorhanden), die Variablen (falls vorhanden) müssen der zwischengespeicherten Anfrage entsprechen, und auch alle benutzerdefinierten HTTP-Header, die möglicherweise festgelegt wurden, müssen ebenfalls identisch sein. Beispielsweise muss beim Magento-`Store`-Header eine Übereinstimmung vorliegen.

### Beispiele

Es wird empfohlen, zum Konfigurieren des Cachings für den Such-Service alle verfügbaren Aggregations-/Facettenwerte abzurufen, die auf den Produktsuchen- und Kategorieseiten angezeigt werden. Diese Werte ändern sich normalerweise nur, wenn beispielsweise ein neues Attribut zu Produkten hinzugefügt wird. Daher kann die Dauer für diesen Cache-Eintrag auf „groß“ festgelegt sein, wenn die Produktattribute nur selten geändert werden. Auch wenn diese Einstellungen vom jeweiligen Projekt abhängen, empfiehlt es sich für Projektentwicklungsphasen die Werte auf wenige Minuten und für stabile Produktionssysteme auf einige Stunden festzulegen.

Dies wird in der Regel mit dem folgenden Cache-Eintrag konfiguriert:

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:10:3600
```

Ein weiteres Beispiel für die Verwendung der GraphQL-Caching-Funktion ist die Navigationskomponente, da sie auf allen Seiten dieselbe GraphQL-Abfrage sendet. In diesem Fall wird der Caching-Eintrag normalerweise auf Folgendes festgelegt:

```
venia/components/structure/navigation:true:10:600
```

wenn die Verwendung der [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia) erwogen wird. Beachten Sie, dass der Komponenten-Proxy-Namen `venia/components/structure/navigation` und **nicht** der Name der CIF-Navigationskomponente (`core/cif/components/structure/navigation/v1/navigation`) verwendet wird.

Das Caching für andere Komponenten sollte auf Projektbasis definiert werden, üblicherweise in Abstimmung mit dem auf Dispatcher-Ebene konfigurierten Cachings. Beachten Sie, dass diese Cashes nicht invalidiert werden, daher sollte die Caching-Dauer mit Umsicht festgelegt werden. Es gibt keine „Universalwerte“, die sich für alle Projekte und Anwendungsfälle eignen. Stellen Sie sicher, dass Sie eine Caching-Strategie auf Projektebene definieren, die den Anforderungen Ihres Projekts am besten entspricht.

## Dispatcher-Caching {#dispatcher}

Das Caching von AEM-Seiten oder -Fragmenten in [AEM Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de) gilt als Best Practice für AEM-Projekte. Normalerweise beruht es auf Invalidierungsverfahren, die sicherstellen, dass alle in AEM geänderten Inhalte in AEM Dispatcher ordnungsgemäß aktualisiert werden. Dies ist ein wesentlicher Aspekt der Caching-Strategie von AEM Dispatcher.

Neben den rein von AEM verwalteten Inhalten kann eine CIF-Seite in der Regel Commerce-Daten anzeigen, die dynamisch über GraphQL von Magento abgerufen werden. Während die Seitenstruktur selbst möglicherweise immer unverändert bleibt, können sich die Commerce-Inhalte ändern, etwa wenn Produktdaten (z. B. Name oder Preis) in Magento aktualisiert werden.

Um sicherzustellen, dass CIF-Seiten für eine begrenzte Zeit in AEM Dispatcher zwischengespeichert werden können, empfehlen wir daher die Verwendung der [zeitbasierten Cache-Invalidierung](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#configuring-time-based-cache-invalidation-enablettl) (auch TTL-basiertes Caching genannt) beim Zwischenspeichern von CIF-Seiten in AEM Dispatcher. Diese Funktion kann AEM mit dem zusätzlichen [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/)-Paket konfiguriert werden.

Beim TTL-basierten Caching definiert ein Entwickler normalerweise eine oder mehrere Caching-Dauerangaben für bestimmte AEM-Seiten. Dadurch wird sichergestellt, dass CIF-Seiten nur bis zur konfigurierten Dauer im AEM Dispatcher zwischengespeichert werden und die Inhalte häufig aktualisiert werden.

>[!NOTE]
>
>Während Server-seitige Daten von AEM Dispatcher zwischengespeichert werden können, rufen einige CIF-Komponenten wie die `product`-, `productlist`- und `searchresults`-Komponenten die Produktpreise in der Regel immer in einer Client-seitigen Browser-Anfrage erneut ab, wenn die Seite geladen wird. Dadurch wird sichergestellt, dass beim Laden der Seite immer die wesentlichen dynamischen Inhalte abgerufen werden.

## Zusätzliche Ressourcen

- [Venia-Referenz-Storefront](https://github.com/adobe/aem-cif-guides-venia)
- [GraphQL-Caching-Konfiguration](https://github.com/adobe/commerce-cif-graphql-client#caching)
- [AEM Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html)
