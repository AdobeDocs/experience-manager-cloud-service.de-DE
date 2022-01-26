---
title: Entfernung des generischen Lucene-Index
description: Entfernung des generischen Lucene-Index
exl-id: fe0e00ac-f9c8-43cf-83c2-5a353f5eaeab
source-git-commit: bc7ef6567ad5baa4becd28a7e7d96bd6b579e1ad
workflow-type: tm+mt
source-wordcount: '1305'
ht-degree: 0%

---

# Entfernung des &quot;generischen Lucene&quot;-Index

Adobe beabsichtigt, den &quot;generischen Lucene&quot;-Index (`/oak:index/lucene-*`) von Adobe Experience Manager as a Cloud Service. Dieser Index wird seit AEM 6.5 nicht mehr unterstützt. In dieser Dokumentation werden die Auswirkungen dieser Entscheidung beschrieben, zusammen mit detaillierten Beschreibungen, wie Sie untersuchen können, ob eine AEM Instanz betroffen ist. Schließlich enthält es Möglichkeiten, Abfragen so zu ändern, dass sie funktionieren, ohne dass dieser Index vorhanden ist.

## Hintergrund

In AEM sind &quot;fulltext&quot;-Abfragen diejenigen, die die folgenden Funktionen verwenden:

* `jcr:contains()` in JCR XPATH
* `CONTAINS` in JCR-SQL2

Solche Abfragen können keine Ergebnisse ohne Verwendung eines Index zurückgeben. Im Gegensatz zu Abfragen, die nur Pfad- oder Eigenschaftsbeschränkungen enthalten, gibt eine Abfrage mit einer Volltextbeschränkung, für die kein Index gefunden werden kann (und daher eine Umkehrung durchgeführt wird), immer 0 Ergebnisse zurück.

Der &quot;generische Lucene&quot;-Index (`/oak:index/lucene-*`) gibt es seit AEM 6.0 / Oak 1.0, um eine Volltextsuche über den Großteil der Repository-Hierarchie hinweg bereitzustellen (einige Pfade, wie z. B. `/jcr:system` und `/var` wurden immer von dieser Seite ausgeschlossen), dieser Index wurde jedoch größtenteils durch Indizes für spezifischere Knotentypen ersetzt (z. B. `damAssetLucene-*` für den Knotentyp &quot;dam:Asset&quot;), der sowohl Volltext- als auch Eigenschaftssuchen unterstützt.

In AEM 6.5 wurde der &quot;generische Lucene&quot;-Index als veraltet markiert (was bedeutet, dass er in zukünftigen Versionen entfernt wird), und seither wurde ein WARN protokolliert, wenn der Index verwendet wurde:

```
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'search term') and isdescendantnode(a, '/content/mysite') /* xpath: /jcr:root/content/mysite//*[jcr:contains(.,"search term")] */ fullText="search" "term", path=/content/mysite//*). Please change the query or the index definitions.
```

In den letzten AEM-Versionen wurde der &quot;generische Lucene&quot;-Index verwendet, um eine sehr geringe Anzahl von Funktionen zu unterstützen. Diese werden überarbeitet, um andere Indizes zu verwenden, oder anderweitig geändert, um die Abhängigkeit von diesem Index zu entfernen.
Beispielsweise sollten &quot;Referenz-Lookup&quot;-Abfragen des unten gezeigten Formulars jetzt den Index unter &quot;/oak:index/pathreference&quot;verwenden (der nur Zeichenfolgeneigenschaftswerte indiziert, die mit einem regulären Ausdruck übereinstimmen, der nach JCR-Pfaden sucht). 

```
//*[jcr:contains(., '"/content/dam/mysite"')]
```

Um größere Kundendatenvolumen zu unterstützen, wird Adobe den &quot;generischen Lucene&quot;-Index nicht mehr in neuen AEM as a Cloud Service Umgebungen erstellen und daraufhin mit dem Entfernen des Index aus bestehenden Repositorys beginnen. Wir haben die Indexkosten (über die Eigenschaften &quot;costPerEntry&quot;und &quot;costPerExecution&quot;) bereits angepasst, um sicherzustellen, dass andere Indizes (z. B. `/oak:index/pathreference`) verwendet werden, wird `/oak:index/lucene-*` soweit möglich. 

Kundenanwendungen, die Abfragen verwenden, die noch von diesem Index abhängig sind, sollten unverzüglich aktualisiert werden, um andere vorhandene Indizes zu nutzen (die bei Bedarf angepasst werden können), oder der Kundenanwendung sollten neue benutzerdefinierte Indizes hinzugefügt werden. Eine vollständige Anleitung zur Indexverwaltung in AEM as a Cloud Service finden Sie unter [Indizierungsdokumentation](/help/operations/indexing.md).

## Wie kann ich feststellen, ob Ihre Anwendung vom &quot;generischen Lucene&quot;-Index abhängt?

Der &quot;generische Lucene&quot;-Index wird derzeit als &quot;Fallback&quot;verwendet, wenn kein anderer Volltext-Index eine Abfrage bedienen kann. Wenn dieser veraltete Index verwendet wird, wird eine Meldung wie die folgende auf WARN-Ebene protokolliert:

```
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*). Please change the query or the index definitions.
```

Unter bestimmten Umständen versucht Oak möglicherweise, einen anderen Volltext-Index zu verwenden (z. B. `/oak:index/pathreference`), um die Volltext-Abfrage zu unterstützen. Wenn die Abfragezeichenfolge jedoch nicht mit dem regulären Ausdruck in der Indexdefinition übereinstimmt, wird eine Nachricht auf WARN-Ebene protokolliert und die Abfrage liefert wahrscheinlich keine Ergebnisse.

```
org.apache.jackrabbit.oak.query.QueryImpl Potentially improper use of index /oak:index/pathReference with queryFilterRegex (["']|^)/ to search for value "test"
```

Sobald der Index &quot;allgemeines Lucene&quot;entfernt wurde, wird eine Meldung wie unten gezeigt auf WARN-Ebene protokolliert, wenn eine Volltext-Abfrage keine geeignete Indexdefinition finden kann:

```
org.apache.jackrabbit.oak.query.QueryImpl Fulltext query without index for filter Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*); no results will be returned
```

Wenn einer dieser Werte protokolliert wird, müssen Sie die Abfrage möglicherweise neu erstellen, um einen anderen Volltext-Index zu verwenden, oder einen neuen Index zur Unterstützung der Abfrage angeben. Details zu den Typen von Abhängigkeiten, die möglicherweise angezeigt werden, und wie Sie sie beheben können, finden Sie unten.

## Potenzielle Abhängigkeiten vom Index &quot;generic lucene&quot;

### Veröffentlichen  

#### Benutzerdefinierte Anwendungsabfragen

Die häufigste Quelle von Abfragen, die den Index &quot;generic lucene&quot;auf der Veröffentlichungsinstanz verwenden, sind benutzerdefinierte Anwendungsabfragen.

In den einfachsten Fällen kann es sich um Abfragen ohne angegebenen Knotentyp (also &#39;nt:base&#39;) oder explizit angegebenes nt:base handeln, z. B.:

```
/jcr:root/content/mysite//*[jcr:contains(., 'search term')]
/jcr:root/content/mysite//element(*, nt:base)[jcr:contains(., 'search term')]
```

Erforderliche Aktion : Diese Abfragen können geändert werden, um einen geeigneten Knotentyp zu verwenden - um beispielsweise Ergebnisse mit übereinstimmenden Seiten (oder eines der &quot;Aggregate&quot;unter dem Knoten cq:Page ) zurückzugeben, könnte die Abfrage wie folgt aussehen:

```
/jcr:root/content/mysite//element(*, cq:Page)[jcr:contains(., 'search term')]
```

In anderen Fällen kann eine Abfrage einen Knotentyp angeben, aber eine Volltextbeschränkung enthalten, die nicht von einem anderen Volltext-Index verarbeitet werden kann, z. B.:

```
/jcr:root/content/dam//element(*, dam:Asset)[jcr:contains(jcr:content/metadata/@cq:tags, 'NewsTopics:cateogries/domestic'))]
```

In diesem Fall weist die Abfrage den Knotentyp &quot;dam:Asset&quot;auf, enthält jedoch eine Volltextbeschränkung für die relative `jcr:content/metadata/@cq:tags` -Eigenschaft.

Diese Eigenschaft wird im damAssetLucene-Index (dem am häufigsten für Abfragen mit dem Knotentyp &#39;dam:Asset&#39; verwendeten Volltext-Index) nicht als &quot;analysiert&quot;markiert, sodass dieser Index nicht für diese Abfrage verwendet werden kann.

Daher greift die Abfrage auf den &quot;generischen Volltext&quot;-Index zurück, bei dem alle eingeschlossenen Eigenschaften durch die Wildcard-Übereinstimmung gekennzeichnet sind unter `/oak:index/lucene-2/indexRules/nt:base/properties/prop`.

Kundenaktion erforderlich : die `jcr:content/metadata/@cq:tags` -Eigenschaft in einer benutzerdefinierten Version des damAssetLucene-Index &quot;analysiert&quot;wird dazu führen, dass diese Abfrage von diesem Index verarbeitet wird, und es wird kein WARN protokolliert.

### Autor 

Zusätzlich zu Abfragen in Kundenanwendungs-Servlets, OSGi-Komponenten und Rendering-Skripten kann es eine Reihe von author-spezifischen Verwendungen des &quot;generischen Lucene&quot;-Index geben. 

#### Referenzsuche

Historisch wurde der &quot;generische Lucene&quot;-Index verwendet, um die &quot;Referenzsuche&quot;zu unterstützen (Suchen nach Inhalten, die Verweise auf einen anderen Inhaltspfad enthalten). Solche Abfragen sollten bereits zur Verwendung des neuen &quot;/oak:index/pathreference&quot;-Index verschoben worden sein.
Kundenaktion erforderlich : keine Kundenaktion erforderlich.


#### Pathfield-Auswahl-Suche

AEM enthält eine benutzerdefinierte Dialogfeldkomponente (Sling-Ressourcentyp &#39;granite/ui/components/coral/foundation/form/pathfield&#39;), die einen Browser (Auswahl) zur Auswahl eines anderen AEM-Pfads bereitstellt.  Die Standardauswahl für Pfadfelder (die verwendet wird, wenn keine benutzerdefinierte Eigenschaft &quot;pickerSrc&quot;in der Inhaltsstruktur definiert ist) rendert eine Suchleiste im Popup-Dialogfeld.
Die Knotentypen, für die gesucht werden soll, können mit der Eigenschaft &quot;nodeTypes&quot;angegeben werden.

Wenn derzeit keine Eigenschaft &quot;nodeTypes&quot;vorhanden ist, verwendet die zugrunde liegende Suchabfrage den Knotentyp &quot;nt:base&quot;und verwendet daher wahrscheinlich den Index &quot;generic lucene&quot;(typischerweise protokolliert man die unten gezeigten WARN-Meldungen).

```
20.01.2022 18:56:06.412 *WARN* [127.0.0.1 [1642704966377] POST /mnt/overlay/granite/ui/content/coral/foundation/form/pathfield/picker.result.single.html HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') and isdescendantnode(a, '/content') /* xpath: /jcr:root/content//element(*, nt:base)[(jcr:contains(., 'test'))] order by @jcr:score descending */ fullText="test", path=/content//*). Please change the query or the index definitions.
```

Vor dem Entfernen von &quot;allgemeines Lucene&quot;wird die Komponente &quot;pathfield&quot;aktualisiert, sodass das Suchfeld für Komponenten mit der Standardauswahl ausgeblendet wird, die keine Eigenschaft &quot;nodeTypes&quot;bereitstellen.

| Pathfield-Auswahl mit Suche | Pathfield-Auswahl ohne Suche |
|---|---|
| ![Pathfield-Auswahl mit Suche](assets/index-pathfield-picker-with-search.png) | ![Pathfield-Auswahl ohne Suche](assets/index-pathfield-picker-without-search.png) |


Kundenaktion erforderlich : Wenn keine Suche erforderlich ist, ist vom Kunden keine Aktion erforderlich.

Wenn der Kunde die Suchfunktion in der Pfadfeldauswahl beibehalten möchte, sollte eine Eigenschaft &quot;nodeTypes&quot;bereitgestellt werden, in der die Knotentypen aufgelistet sind, anhand derer er Abfragen durchführen möchte. Diese können als kommagetrennte Liste von Knotentypen in einer String-Eigenschaft angegeben werden.


>[!NOTE]
>Der Inhaltsfragmentmodell-Editor verwendet spezialisierte Pfadfelder mit dem Sling-Ressourcentyp &quot;dam/cfm/models/editor/components/contentreference&quot;.
> * Derzeit führen diese Abfragen Abfragen ohne angegebene Knotentypen durch, was dazu führt, dass aufgrund der Verwendung des &quot;generischen Lucene&quot;-Index eine WARN protokolliert wird.
> * Instanzen dieser Komponenten verwenden in Kürze automatisch die Knotentypen &quot;cq:Page&quot;und &quot;dam:Asset&quot;ohne weitere Kundenaktion.
> * Die Eigenschaft &quot;nodeTypes&quot;kann hinzugefügt werden, um diese Standard-Knotentypen zu überschreiben. 





## Zeitleiste für das Entfernen von &quot;allgemeines Lucene&quot;

Die Adobe wird einen zweistufigen Ansatz verfolgen, um den &quot;generischen Lucene&quot;-Index zu streichen.

**Phase 1** (Voraussichtlicher Beginn am 31. Januar 2022): Erstellen Sie &quot;/oak:index/lucene-*&quot;nicht mehr in neuen AEM as a Cloud Service Umgebungen.

**Phase 2** (Geplanter Beginn am 31. März 2022) : Entfernen Sie den Index &quot;/oak:index/lucene-*&quot;aus den neuen AEM as a Cloud Service Umgebungen.

Adobe überwacht die oben genannten Protokollmeldungen und versucht, Kunden zu kontaktieren, die weiterhin vom allgemeinen Lucene-Index abhängig sind.

Als kurzfristige Abmilderung werden bei Bedarf benutzerdefinierte Indexdefinitionen direkt zu Kundensystemen hinzugefügt, um Funktions- oder Leistungsprobleme infolge der Entfernung des &quot;generischen Lucene&quot;-Index zu vermeiden.

In solchen Fällen wird dem Kunden die aktualisierte Indexdefinition bereitgestellt und empfohlen, diese in zukünftige Versionen seiner Anwendung über Cloud Manager aufzunehmen.
