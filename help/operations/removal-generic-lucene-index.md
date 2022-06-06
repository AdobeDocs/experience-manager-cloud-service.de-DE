---
title: Entfernen des generischen Lucene-Index
description: Erfahren Sie mehr über die geplante Entfernung des generischen Lucene-Index und darüber, wie Sie betroffen sein könnten.
exl-id: 3b966d4f-6897-406d-ad6e-cd5cda020076
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: ht
source-wordcount: '1349'
ht-degree: 100%

---

# Entfernen des generischen Lucene-Index {#generic-lucene-index-removal}

Adobe beabsichtigt, den generischen Lucene-Index (`/oak:index/lucene-*`) aus Adobe Experience Manager as a Cloud Service zu entfernen. Dieser Index wird seit AEM 6.5 nicht mehr unterstützt. In diesem Dokument werden die Auswirkungen dieser Entscheidung beschrieben. Außerdem finden Sie detaillierte Beschreibungen, wie Sie untersuchen können, ob eine AEM-Instanz betroffen ist. Es enthält auch Möglichkeiten, Abfragen so zu ändern, dass sie weiterhin ohne den generischen Lucene-Index funktionieren.

## Hintergrund {#background}

In AEM sind Volltextabfragen diejenigen, die die folgenden Funktionen verwenden:

* `jcr:contains()` in JCR XPATH
* `CONTAINS` in JCR-SQL2

Solche Abfragen können keine Ergebnisse ohne Verwendung eines Index zurückgeben. Im Gegensatz zu Abfragen, die nur Pfad- oder Eigenschaftsbeschränkungen enthalten, liefert eine Abfrage mit einer Volltextbeschränkung, für die kein Index gefunden werden kann (und daher eine Umkehrung durchgeführt wird), immer null Ergebnisse.

Den generischen Lucene-Index (`/oak:index/lucene-*`) gibt es seit AEM 6.0/Oak 1.0, um eine Volltextsuche über den Großteil der Repository-Hierarchie hinweg zu ermöglichen, obwohl einige Pfade, wie z. B. `/jcr:system` und `/var` immer ausgeschlossen wurden. Dieser Index wurde jedoch weitgehend durch Indizes für spezifischere Knotentypen ersetzt (z. B. `damAssetLucene-*` für den Knotentyp `dam:Asset`), die sowohl Volltext- als auch Eigenschaftensuchen unterstützen.

In AEM 6.5 wurde der generische Lucene-Index als veraltet markiert, was darauf hinweist, dass er in zukünftigen Versionen entfernt wird. Seither wurde eine WARNUNG protokolliert, wenn der Index verwendet wurde, wie durch das folgende Protokoll-Snippet veranschaulicht:

```text
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'search term') and isdescendantnode(a, '/content/mysite') /* xpath: /jcr:root/content/mysite//*[jcr:contains(.,"search term")] */ fullText="search" "term", path=/content/mysite//*). Please change the query or the index definitions.
```

In den letzten AEM-Versionen wurde der generische Lucene-Index verwendet, um eine sehr geringe Anzahl von Funktionen zu unterstützen. Diese werden überarbeitet, sodass sie nun andere Indizes verwenden, oder anderweitig geändert, um die Abhängigkeit von diesem Index zu entfernen.

Beispielsweise sollten Referenz-Lookup-Abfragen, wie im folgenden Beispiel, nun den Index bei `/oak:index/pathreference` verwenden, der nur `String`-Eigenschaftswerte indiziert, die einem regulären Ausdruck entsprechen, der nach JCR-Pfaden sucht.

```text
//*[jcr:contains(., '"/content/dam/mysite"')]
```

Um größere Kundendatenvolumen zu unterstützen, erstellt Adobe für neue AEM as a Cloud Service Umgebungen den generischen Lucene-Index nicht mehr. Darüber hinaus beginnt Adobe mit dem Entfernen des Index aus vorhandenen Repositorys. Weitere Einzelheiten finden Sie [in der Timeline](#timeline) am Ende dieses Dokuments.

Adobe hat die Indexkosten bereits über die `costPerEntry`- und `costPerExecution`-Eigenschaften angepasst, um sicherzustellen, dass andere Indizes wie `/oak:index/pathreference` nach Möglichkeit bevorzugt werden.

Kundenprogramme, die Abfragen verwenden, die noch von diesem Index abhängig sind, sollten unverzüglich aktualisiert werden, um andere vorhandene Indizes zu nutzen, die bei Bedarf angepasst werden können. Alternativ können dem Kundenprogramm neue benutzerdefinierte Indizes hinzugefügt werden. Eine vollständige Anleitung zur Indexverwaltung in AEM as a Cloud Service finden Sie im Abschnitt [Dokumentation zur Indizierung](/help/operations/indexing.md).

## Sind Sie betroffen? {#are-you-affected}

Der generische Lucene-Index wird derzeit als Fallback verwendet, wenn kein anderer Volltext-Index eine Abfrage bedienen kann. Wenn dieser veraltete Index verwendet wird, wird eine Meldung wie die folgende auf WARNUNGS-Ebene protokolliert:

```text
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*). Please change the query or the index definitions.
```

Unter bestimmten Umständen versucht Oak möglicherweise, einen anderen Volltext-Index zu verwenden (z. B. `/oak:index/pathreference`), um die Volltextabfrage zu unterstützen. Wenn die Abfragezeichenfolge jedoch nicht mit dem regulären Ausdruck in der Indexdefinition übereinstimmt, wird eine Nachricht auf WARNUNGS-Ebene protokolliert und die Abfrage liefert wahrscheinlich keine Ergebnisse.

```text
org.apache.jackrabbit.oak.query.QueryImpl Potentially improper use of index /oak:index/pathReference with queryFilterRegex (["']|^)/ to search for value "test"
```

Nachdem der generische Lucene-Index entfernt wurde, wird, wenn eine Volltextabfrage keine geeignete Indexdefinition finden kann, eine Meldung wie unten gezeigt auf WARNUNGS-Ebene protokolliert:

```text
org.apache.jackrabbit.oak.query.QueryImpl Fulltext query without index for filter Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*); no results will be returned
```

>[!IMPORTANT]
>
>**Erforderliche Kundenaktion**
>
> Wenn eine der oben genannten Warnmeldungen protokolliert wird, müssen Sie die Abfrage möglicherweise neu überarbeiten, um einen anderen Volltextindex zu verwenden, oder Sie müssen einen neuen Index zur Unterstützung der Abfrage angeben.
>
>Details zu den Abhängigkeitstypen, die Sie sehen können, und wie Sie sie behandeln können, finden Sie in den folgenden Abschnitten.

## Potenzielle Abhängigkeiten von generischen Lucene-Indizes {#potential-dependencies}

Es gibt eine Reihe von Bereichen, in denen Ihre Programme und AEM-Installationen von generischen Lucene-Indizes sowohl für Autoren- als auch Veröffentlichungsinstanzen abhängig sein können.

### Veröffentlichungsinstanz {#publish-instance}

#### Benutzerdefinierte Programmabfragen {#custom-application-queries}

Die häufigste Quelle von Abfragen, die den generischen Lucene-Index auf einer Veröffentlichungsinstanz verwenden, sind benutzerdefinierte Programmabfragen.

In den einfachsten Fällen kann es sich um Abfragen ohne angegebenen Knotentyp handeln, was bedeutet, dass `nt:base` oder `nt:base` explizit angegeben werden, z.B.:

```text
/jcr:root/content/mysite//*[jcr:contains(., 'search term')]
/jcr:root/content/mysite//element(*, nt:base)[jcr:contains(., 'search term')]
```

>[!IMPORTANT]
>
>**Erforderliche Kundenaktion**
>
>Die oben genannten Abfragen sollten so geändert werden, dass sie einen geeigneten Knotentyp verwenden, wie im folgenden Abschnitt beschrieben.

Beispielsweise können die Abfragen so geändert werden, dass Ergebnisse zurückgegeben werden, die mit Seiten oder einem der Aggregate unter dem `cq:Page node` übereinstimmen. Die Abfrage könnte somit wie folgt lauten:

```text
/jcr:root/content/mysite//element(*, cq:Page)[jcr:contains(., 'search term')]
```

In anderen Fällen kann eine Abfrage einen Knotentyp angeben, aber eine Volltextbeschränkung enthalten, die nicht von einem anderen Volltextindex verarbeitet werden kann, z. B.:

```text
/jcr:root/content/dam//element(*, dam:Asset)[jcr:contains(jcr:content/metadata/@cq:tags, 'NewsTopics:cateogries/domestic'))]
```

In diesem Fall weist die Abfrage den Knotentyp `dam:Asset` auf, enthält jedoch eine Volltextbeschränkung für die relative `jcr:content/metadata/@cq:tags`-Eigenschaft.

Diese Eigenschaft wird im `damAssetLucene`-Index, dem Volltextindex, der am häufigsten für Abfragen zum Knotentyp `dam:Asset` verwendet wird, nicht als „Analysiert“ gekennzeichnet. Daher kann dieser Index nicht für diese Abfrage verwendet werden.

Deshalb greift die Abfrage auf den allgemeinen Volltextindex zurück, in dem alle eingeschlossenen Eigenschaften als durch den Wildcard-Treffer bei `/oak:index/lucene-2/indexRules/nt:base/properties/prop` analysiert markiert sind.

>[!IMPORTANT]
>
>**Erforderliche Kundenaktion**
>
>Wenn Sie die `jcr:content/metadata/@cq:tags`-Eigenschaft in einer benutzerdefinierten Version des `damAssetLucene`-Index als analysiert markieren, wird diese Abfrage von diesem Index verarbeitet und es wird keine WARNUNG protokolliert.

### Autoreninstanz {#author-instance}

Zusätzlich zu Abfragen in Kundenprogramm-Servlets, OSGi-Komponenten und Rendering-Skripten kann es eine Reihe von autorenspezifischen Verwendungen des generischen Lucene-Index geben.

#### Referenzsuche {#reference-search}

Bisher wurde der generische Lucene-Index verwendet, um die Referenzsuche oder die Suche nach Inhalten zu unterstützen, die Verweise auf einen anderen Inhaltspfad enthalten. Solche Abfragen sollten bereits so geändert worden sein, dass sie den neuen `/oak:index/pathreference`-Index verwenden.

#### Suche für Pfadfeldwähler {#picker-search}

AEM enthält eine benutzerdefinierte Dialogfeldkomponente mit dem Sling-Ressourcentyp `granite/ui/components/coral/foundation/form/pathfield`, die einen Browser/einen Auswahlassistenten zum Auswählen eines anderen AEM-Pfads bietet. Der Pfadfeldwähler, der verwendet wird, wenn keine benutzerdefinierte `pickerSrc`-Eigenschaft in der Inhaltsstruktur definiert ist, rendert eine Suchleiste im Popup-Dialogfeld.

Die Knotentypen, nach denen gesucht werden soll, können mit der Eigenschaft `nodeTypes` angegeben werden.

Wenn derzeit keine `nodeTypes`-Eigenschaft vorhanden ist, verwendet die zugrunde liegende Suchabfrage den Knotentyp `nt:base` und verwendet daher wahrscheinlich den generischen Lucene-Index, wobei in der Regel WARNUNGS-Meldungen ähnlich der folgenden protokolliert werden.

```text
20.01.2022 18:56:06.412 *WARN* [127.0.0.1 [1642704966377] POST /mnt/overlay/granite/ui/content/coral/foundation/form/pathfield/picker.result.single.html HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') and isdescendantnode(a, '/content') /* xpath: /jcr:root/content//element(*, nt:base)[(jcr:contains(., 'test'))] order by @jcr:score descending */ fullText="test", path=/content//*). Please change the query or the index definitions.
```

Vor dem Entfernen des generischen Lucene-Index wird die Komponente `pathfield` aktualisiert, sodass das Suchfeld für Komponenten mithilfe der Standardauswahl ausgeblendet wird, die keine `nodeTypes`-Eigenschaft bereitstellt.

| Pfadfeldwähler mit Suche | Pfadfeldwähler ohne Suche |
|---|---|
| ![Pfadfeldwähler mit Suche](assets/index-pathfield-picker-with-search.png) | ![Pfadfeldwähler ohne Suche](assets/index-pathfield-picker-without-search.png) |

>[!IMPORTANT]
>
>**Erforderliche Kundenaktion**
>
>Wenn der Kunde die Suchfunktion im Pfadfeldwähler beibehalten möchte, sollte eine `nodeTypes`-Eigenschaft angegeben werden, die die Knotentypen auflistet, für die er Abfragen durchführen möchte. Diese können als kommagetrennte Liste von Knotentypen in einer `String`-Eigenschaft angegeben werden. Wenn keine Suche erforderlich ist, ist keine Aktion seitens des Kunden notwendig.

>[!NOTE]
>
>Der Inhaltsfragmentmodell-Editor verwendet spezielle Pfadfelder mit dem Sling-Ressourcentyp `dam/cfm/models/editor/components/contentreference`.
> * Derzeit führen diese Abfragen ohne angegebene Knotentypen durch, was dazu führt, dass aufgrund der Verwendung des generischen Lucene-Index eine WARNUNG protokolliert wird.
> * Instanzen dieser Komponenten werden in Kürze automatisch ohne weitere Kundenaktion standardmäßig die Knotentypen `cq:Page` und `dam:Asset` verwenden.
> * Die `nodeTypes`-Eigenschaft kann hinzugefügt werden, um diese standardmäßigen Knotentypen zu überschreiben.


## Timeline für die Entfernung des generischen Lucene-Index {#timeline}

Adobe wird den generischen Lucene-Index in zwei Phasen entfernen.

* **Phase 1** (Geplanter Beginn am 31. Januar 2022): In neuen AEM as a Cloud Service-Umgebungen wird kein `/oak:index/lucene-*` mehr erstellt.
* **Phase 2** (Geplanter Beginn am 31. März 2022): Der `/oak:index/lucene-*`-Index wird aus bestehenden AEM as a Cloud Service-Umgebungen entfernt.

Adobe überwacht die oben genannten Protokollmeldungen und versucht, Kunden zu kontaktieren, die weiterhin vom generischen Lucene-Index abhängig sind.

Als kurzfristige Lösung fügt Adobe bei Bedarf benutzerdefinierte Indexdefinitionen direkt zu Kundensystemen hinzu, um Funktions- oder Leistungsprobleme zu vermeiden, die durch die Entfernung des generischen Lucene-Index auftreten.

In solchen Fällen wird dem Kunden die aktualisierte Indexdefinition bereitgestellt und empfohlen, diese über Cloud Manager in zukünftige Versionen seines Programms aufzunehmen.
