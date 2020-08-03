---
title: Zwischenspeicherung und Leistung
description: Zwischenspeicherung und Leistung
translation-type: tm+mt
source-git-commit: 2997a28e79b51e88ececbd46c81dbc6a6c443e68
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 2%

---


# Zwischenspeicherung und Leistung {#caching}

## Komponenten- und GraphQL-Antwortzwischenspeicherung {#graphql}

Die AEM CIF-Kernkomponenten bieten bereits integrierte Unterstützung für die Zwischenspeicherung von GraphQL-Antworten für einzelne Komponenten. Diese Funktion kann verwendet werden, um die Anzahl der GraphQL Backend-Aufrufe um einen großen Faktor zu reduzieren. Eine effektive Zwischenspeicherung kann insbesondere bei sich wiederholenden Abfragen erreicht werden, z. B. beim Abrufen der Kategorien-Struktur für eine Navigationskomponente oder beim Abrufen aller verfügbaren Aggregations-/Facettenwerte, die auf den Produktseiten für die Suche und Kategorie angezeigt werden.

Für die AEM CIF-Kernkomponenten wird die Zwischenspeicherung auf Komponentenbasis konfiguriert, sodass gesteuert werden kann, ob (und wie lange) GraphQL-Anforderungen/Antworten für jede Komponente zwischengespeichert werden. Es ist auch möglich, das Cache-Verhalten für OSGi-Dienste mithilfe des GraphQL-Clients zu definieren.

### Konfiguration

Nach der Konfiguration für eine bestimmte Komponente werden die Cache-Beginn, die GraphQL-Abfragen und -Antworten speichern, wie von jedem Cache-Konfigurationseintrag definiert. Die Größe des Zwischenspeichers und die Cachedauer jedes Eintrags sind auf Projektbasis festzulegen, z. B. je nachdem, wie oft sich die Katalogdaten ändern können, wie wichtig es ist, dass eine Komponente immer die neuesten möglichen Daten anzeigt usw. Beachten Sie, dass der Cache nicht ungültig gemacht wird. Gehen Sie daher beim Festlegen der Cachedauer vorsichtig vor.

Beim Konfigurieren der Zwischenspeicherung für Komponenten muss der Cache-Name der Name der **Proxykomponenten** sein, die Sie in Ihrem Projekt definieren.

Bevor der Client eine GraphQL-Anforderung sendet, prüft er, ob diese **exakt** gleiche GraphQL-Anforderung bereits zwischengespeichert ist und gibt möglicherweise die zwischengespeicherte Antwort zurück. Damit eine Übereinstimmung vorliegt, MÜSSEN die GraphQL-Anforderung exakt übereinstimmen, d. h. die Abfrage, der Vorgangsname (sofern vorhanden), die Variablen (falls vorhanden) MÜSSEN der zwischengespeicherten Anforderung entsprechen, und auch alle benutzerdefinierten HTTP-Header, die festgelegt werden können, MÜSSEN ebenfalls identisch sein. Beispielsweise MUSS die `Store` Kopfzeile des Magentos übereinstimmen.

### Beispiele

Es wird empfohlen, zum Konfigurieren einer Zwischenspeicherung für den Suchdienst alle verfügbaren Aggregations-/Facettenwerte abzurufen, die auf den Produktseiten für die Suche und Kategorie angezeigt werden. Diese Werte ändern sich normalerweise nur, wenn ein neues Attribut zum Beispiel zu Produkten hinzugefügt wird. Daher kann die Dauer für diesen Cache-Eintrag &quot;groß&quot;sein, wenn sich der Satz der Produktattribute nicht oft ändert. Obwohl dies projektspezifisch ist, empfehlen wir Werte von ein paar Minuten in Projektentwicklungsphasen und ein paar Stunden auf stabilen Produktionssystemen.

Dies wird in der Regel mit dem folgenden Cache-Eintrag konfiguriert:

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:10:3600
```

Ein weiteres Beispiel für die Verwendung der GraphQl-Cache-Funktion ist die Navigationskomponente, da sie auf allen Seiten dieselbe GraphQL-Abfrage sendet. In diesem Fall wird der Cache-Eintrag normalerweise auf Folgendes festgelegt:

```
venia/components/structure/navigation:true:10:600
```

wenn der [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) verwendet wird. Beachten Sie die Verwendung des Komponenten-Proxynamens `venia/components/structure/navigation`, **nicht** den Namen der CIF-Navigationskomponente (`core/cif/components/structure/navigation/v1/navigation`).

Die Zwischenspeicherung für andere Komponenten sollte auf Projektbasis festgelegt werden, in der Regel in Abstimmung mit der auf der Ebene des Dispatchers konfigurierten Zwischenspeicherung. Denken Sie daran, dass diese Zwischenspeicher nicht aktiv ungültig gemacht werden, daher sollte die Cachedauer sorgfältig eingestellt werden. Es gibt keine &quot;Einheitsgröße für alle&quot;-Werte, die mit allen möglichen Projekten und Anwendungsfällen übereinstimmen. Stellen Sie sicher, dass Sie eine Cachestrategie auf Projektebene definieren, die den Anforderungen Ihres Projekts am besten entspricht.

## Dispatcher caching {#dispatcher}

Das Zwischenspeichern AEM Seiten oder Fragmente im [AEM Dispatcher](https://docs.adobe.com/content/help/de-DE/experience-manager-dispatcher/using/dispatcher.html) ist eine Best Practice für AEM Projekte. Normalerweise beruht sie auf Ungültigmachungstechniken, die sicherstellen, dass alle Inhaltsänderungen in AEM im Dispatcher ordnungsgemäß aktualisiert werden. Dies ist ein Kernmerkmal der Cachestrategie für AEM Dispatcher.

Neben reinem AEM verwaltetem Inhalt kann CIF eine Seite in der Regel Commerce-Daten anzeigen, die dynamisch über GraphQL von Magento abgerufen werden. Während sich die Seitenstruktur selbst möglicherweise nie ändert, kann sich der Commerce-Inhalt ändern, z. B. wenn sich einige Produktdaten (Name, Preis usw.) im Magento ändern.

Um sicherzustellen, dass CIF-Seiten für eine begrenzte Zeit im AEM Dispatcher zwischengespeichert werden können, empfehlen wir daher die Verwendung der [zeitbasierten Cache-Ungültigmachung](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring-time-based-cache-invalidation-enablettl) (auch TTL-basierte Zwischenspeicherung genannt) beim Zwischenspeichern von CIF-Seiten im AEM Dispatcher. Diese Funktion kann AEM mit dem zusätzlichen [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/) Paket konfiguriert werden.

Bei der TTL-basierten Zwischenspeicherung definiert ein Entwickler normalerweise eine oder mehrere Zwischenspeicherungszeiträume für ausgewählte AEM. Dadurch wird sichergestellt, dass CIF-Seiten nur bis zur konfigurierten Dauer im AEM Dispatcher zwischengespeichert werden und der Inhalt häufig aktualisiert wird.

>[!NOTE]
>
>Während serverseitige Daten vom AEM Dispatcher zwischengespeichert werden können, holen einige CIF-Komponenten wie die `product`, `productlist`und `searchresults` Komponenten die Produktpreise in der Regel immer in einer clientseitigen Browseranforderung zurück, wenn die Seite geladen wird. Dadurch wird sichergestellt, dass beim Laden der Seite immer wichtige dynamische Inhalte abgerufen werden.

## Zusätzliche Ressourcen

- [Venedig-Referenzspeicher](https://github.com/adobe/aem-cif-guides-venia)
- [GraphQL-Cache-Konfiguration](https://github.com/adobe/commerce-cif-graphql-client#caching)
- [AEM Dispatcher](https://docs.adobe.com/content/help/de-DE/experience-manager-dispatcher/using/dispatcher.html)