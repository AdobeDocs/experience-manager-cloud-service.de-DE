---
title: Generisches Entfernen des Lucene-Index
description: Erfahren Sie mehr über die geplante Entfernung von generischen Lucene-Indizes und darüber, wie Sie betroffen sein können.
exl-id: 3b966d4f-6897-406d-ad6e-cd5cda020076
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '1349'
ht-degree: 0%

---

# Generisches Entfernen des Lucene-Index {#generic-lucene-index-removal}

Adobe beabsichtigt, den &quot;generischen Lucene&quot;-Index (`/oak:index/lucene-*`) von Adobe Experience Manager as a Cloud Service. Dieser Index wird seit AEM 6.5 nicht mehr unterstützt. In diesem Dokument werden die Auswirkungen dieser Entscheidung beschrieben, zusammen mit detaillierten Beschreibungen, wie Sie untersuchen können, ob eine AEM Instanz betroffen ist. Es enthält auch Möglichkeiten, Abfragen so zu ändern, dass sie weiterhin ohne den generischen Lucene-Index funktionieren.

## Hintergrund {#background}

In AEM sind Volltextabfragen diejenigen, die die folgenden Funktionen verwenden:

* `jcr:contains()` in JCR XPATH
* `CONTAINS` in JCR-SQL2

Solche Abfragen können keine Ergebnisse ohne Verwendung eines Index zurückgeben. Im Gegensatz zu Abfragen, die nur Pfad- oder Eigenschaftsbeschränkungen enthalten, liefert eine Abfrage mit einer Volltextbeschränkung, für die kein Index gefunden werden kann (und daher eine Umkehrung durchgeführt wird), immer null Ergebnisse.

Der generische Lucene-Index (`/oak:index/lucene-*`) gibt es seit AEM 6.0 / Oak 1.0, um eine Volltextsuche über den Großteil der Repository-Hierarchie hinweg bereitzustellen, obwohl einige Pfade, wie z. B. `/jcr:system` und `/var` wurden immer ausgeschlossen. Dieser Index wurde jedoch weitgehend durch Indizes für spezifischere Knotentypen ersetzt (z. B. `damAssetLucene-*` für `dam:Asset` Knotentyp), die sowohl Volltext- als auch Eigenschaftensuchen unterstützen.

In AEM 6.5 wurde der generische Lucene-Index als veraltet markiert, was darauf hinweist, dass er in zukünftigen Versionen entfernt wird. Seither wurde eine WARN protokolliert, wenn der Index verwendet wurde, wie durch das folgende Protokollfragment veranschaulicht:

```text
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'search term') and isdescendantnode(a, '/content/mysite') /* xpath: /jcr:root/content/mysite//*[jcr:contains(.,"search term")] */ fullText="search" "term", path=/content/mysite//*). Please change the query or the index definitions.
```

In den letzten AEM wurde der generische Lucene-Index verwendet, um eine sehr geringe Anzahl von Funktionen zu unterstützen. Diese werden überarbeitet, um andere Indizes zu verwenden, oder anderweitig geändert, um die Abhängigkeit von diesem Index zu entfernen.

Beispielsweise sollten Referenzabfrageabfragen, wie im folgenden Beispiel, jetzt den Index unter `/oak:index/pathreference`, die nur Indizes enthält `String` Eigenschaftswerte, die mit einem regulären Ausdruck übereinstimmen, der nach JCR-Pfaden sucht.

```text
//*[jcr:contains(., '"/content/dam/mysite"')]
```

Um größere Kundendatenvolumen zu unterstützen, erstellt Adobe nicht mehr den generischen Lucene-Index für neue AEM as a Cloud Service Umgebungen. Darüber hinaus beginnt Adobe mit dem Entfernen des Index aus vorhandenen Repositorys. [Anzeigen der Timeline](#timeline) am Ende dieses Dokuments für weitere Informationen.

Adobe hat die Indexkosten bereits über die `costPerEntry` und `costPerExecution` Eigenschaften, um sicherzustellen, dass andere Indizes wie `/oak:index/pathreference` werden nach Möglichkeit bevorzugt.

Kundenanwendungen, die Abfragen verwenden, die noch von diesem Index abhängig sind, sollten unverzüglich aktualisiert werden, um andere vorhandene Indizes zu nutzen, die bei Bedarf angepasst werden können. Alternativ können der Kundenanwendung neue benutzerdefinierte Indizes hinzugefügt werden. Eine vollständige Anleitung zur Indexverwaltung in AEM as a Cloud Service finden Sie im Abschnitt [Indizierungsdokumentation.](/help/operations/indexing.md)

## Bist du betroffen? {#are-you-affected}

Der generische Lucene-Index wird derzeit als Fallback verwendet, wenn kein anderer Volltext-Index eine Abfrage bedienen kann. Wenn dieser veraltete Index verwendet wird, wird eine Meldung wie die folgende auf WARN-Ebene protokolliert:

```text
org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*). Please change the query or the index definitions.
```

Unter bestimmten Umständen versucht Oak möglicherweise, einen anderen Volltext-Index zu verwenden (z. B. `/oak:index/pathreference`), um die Volltextabfrage zu unterstützen. Wenn die Abfragezeichenfolge jedoch nicht mit dem regulären Ausdruck in der Indexdefinition übereinstimmt, wird eine Nachricht auf WARN-Ebene protokolliert und die Abfrage liefert wahrscheinlich keine Ergebnisse.

```text
org.apache.jackrabbit.oak.query.QueryImpl Potentially improper use of index /oak:index/pathReference with queryFilterRegex (["']|^)/ to search for value "test"
```

Nachdem der generische Lucene-Index entfernt wurde, wird eine Meldung wie unten gezeigt auf WARN-Ebene protokolliert, wenn eine Volltextabfrage keine geeignete Indexdefinition finden kann:

```text
org.apache.jackrabbit.oak.query.QueryImpl Fulltext query without index for filter Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') /* xpath: //*[jcr:contains(.,"test")] */ fullText="test", path=*); no results will be returned
```

>[!IMPORTANT]
>
>**Erforderliche Kundenaktion**
>
> Wenn eine der oben genannten Warnmeldungen protokolliert wird, müssen Sie die Abfrage möglicherweise neu überarbeiten, um einen anderen Volltext-Index zu verwenden, oder Sie müssen einen neuen Index zur Unterstützung der Abfrage angeben.
>
>Details zu den Abhängigkeitstypen, die Sie sehen können, und wie Sie sie beheben können, finden Sie in den folgenden Abschnitten.

## Potenzielle Abhängigkeiten von generischen Lucene-Indizes {#potential-dependencies}

Es gibt eine Reihe von Bereichen, in denen Ihre Anwendungen und AEM Installationen von generischen Lucene-Indizes sowohl für Autoren- als auch Veröffentlichungsinstanzen abhängig sein können.

### Veröffentlichungsinstanz {#publish-instance}

#### Benutzerdefinierte Anwendungsabfragen {#custom-application-queries}

Die häufigste Quelle von Abfragen, die den generischen Lucene-Index auf einer Veröffentlichungsinstanz verwenden, sind benutzerdefinierte Anwendungsabfragen.

In den einfachsten Fällen kann es sich um Abfragen ohne angegebenen Knotentyp handeln, was bedeutet `nt:base` oder `nt:base` explizit angegeben werden, z. B.:

```text
/jcr:root/content/mysite//*[jcr:contains(., 'search term')]
/jcr:root/content/mysite//element(*, nt:base)[jcr:contains(., 'search term')]
```

>[!IMPORTANT]
>
>**Erforderliche Kundenaktion**
>
>Die oben genannten Abfragen sollten geändert werden, um einen geeigneten Knotentyp zu verwenden, wie im folgenden Abschnitt beschrieben.

Beispielsweise können die Abfragen so geändert werden, dass Ergebnisse zurückgegeben werden, die mit Seiten übereinstimmen, oder eines der Aggregate unter der `cq:Page node`. Die Abfrage könnte somit wie folgt lauten:

```text
/jcr:root/content/mysite//element(*, cq:Page)[jcr:contains(., 'search term')]
```

In anderen Fällen kann eine Abfrage einen Knotentyp angeben, aber eine Volltextbeschränkung enthalten, die nicht von einem anderen Volltext-Index verarbeitet werden kann, z. B.:

```text
/jcr:root/content/dam//element(*, dam:Asset)[jcr:contains(jcr:content/metadata/@cq:tags, 'NewsTopics:cateogries/domestic'))]
```

In diesem Fall weist die Abfrage die `dam:Asset` Knotentyp, enthält jedoch eine Volltextbeschränkung für die relative `jcr:content/metadata/@cq:tags` -Eigenschaft.

Diese Eigenschaft wird nicht als im `damAssetLucene` index, der am häufigsten für Abfragen mit der `dam:Asset` Knotentyp. Daher kann dieser Index nicht für diese Abfrage verwendet werden.

Daher greift die Abfrage auf den generischen Volltext-Index zurück, in dem alle eingeschlossenen Eigenschaften als durch die Platzhalterübereinstimmung unter `/oak:index/lucene-2/indexRules/nt:base/properties/prop`.

>[!IMPORTANT]
>
>**Erforderliche Kundenaktion**
>
>Markieren Sie die `jcr:content/metadata/@cq:tags` -Eigenschaft in einer benutzerdefinierten Version der `damAssetLucene` -Index führt dazu, dass diese Abfrage von diesem Index verarbeitet wird und keine WARN protokolliert wird.

### Autoreninstanz {#author-instance}

Zusätzlich zu Abfragen in Kundenanwendungs-Servlets, OSGi-Komponenten und Rendering-Skripten kann es eine Reihe von author-spezifischen Verwendungen des generischen Lucene-Index geben.

#### Referenzsuche {#reference-search}

Bisher wurde der generische Lucene-Index verwendet, um die Referenzsuche oder die Suche nach Inhalten zu unterstützen, die Verweise auf einen anderen Inhaltspfad enthalten. Solche Abfragen sollten bereits aktualisiert worden sein, um die neue `/oak:index/pathreference` Index.

#### Suche für Pfadfeldwähler {#picker-search}

AEM enthält eine benutzerdefinierte Dialogfeldkomponente mit dem Sling-Ressourcentyp `granite/ui/components/coral/foundation/form/pathfield`, die einen Browser/eine Auswahl zur Auswahl eines anderen AEM-Pfads bietet. Die Standardauswahl für Pfadfelder, die verwendet wird, wenn kein benutzerdefinierter `pickerSrc` -Eigenschaft in der Inhaltsstruktur definiert ist, rendert eine Suchleiste im Popup-Dialogfeld.

Die Knotentypen, anhand derer gesucht werden soll, können mithilfe der `nodeTypes` -Eigenschaft.

Derzeit, wenn nicht `nodeTypes` -Eigenschaft vorhanden ist, verwendet die zugrunde liegende Suchabfrage die `nt:base` Knotentyp und daher wahrscheinlich den generischen Lucene-Index verwenden, typischerweise protokollieren Sie WARN-Meldungen ähnlich den folgenden.

```text
20.01.2022 18:56:06.412 *WARN* [127.0.0.1 [1642704966377] POST /mnt/overlay/granite/ui/content/coral/foundation/form/pathfield/picker.result.single.html HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.lucene.LucenePropertyIndex This index is deprecated: /oak:index/lucene-2; it is used for query Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a where contains(*, 'test') and isdescendantnode(a, '/content') /* xpath: /jcr:root/content//element(*, nt:base)[(jcr:contains(., 'test'))] order by @jcr:score descending */ fullText="test", path=/content//*). Please change the query or the index definitions.
```

Vor dem Entfernen des generischen Lucene-Index muss die `pathfield` -Komponente aktualisiert, sodass das Suchfeld für Komponenten mit der Standardauswahl ausgeblendet wird, die keine `nodeTypes` -Eigenschaft.

| Pfadfeldauswahl mit Suche | Pfadfeldauswahl ohne Suche |
|---|---|
| ![Pfadfeldauswahl mit Suche](assets/index-pathfield-picker-with-search.png) | ![Pfadfeldauswahl ohne Suche](assets/index-pathfield-picker-without-search.png) |

>[!IMPORTANT]
>
>**Erforderliche Kundenaktion**
>
>Wenn der Kunde die Suchfunktion in der Pfadfeldauswahl beibehalten möchte, wird eine `nodeTypes` -Eigenschaft angegeben werden, die die Knotentypen auflistet, für die sie Abfragen durchführen möchten. Diese können als kommagetrennte Liste von Knotentypen in einer `String` -Eigenschaft. Wenn keine Suche erforderlich ist, ist vom Kunden keine Aktion erforderlich.

>[!NOTE]
>
>Der Inhaltsfragmentmodell-Editor verwendet spezielle Pfadfelder mit dem Sling-Ressourcentyp `dam/cfm/models/editor/components/contentreference`.
> * Derzeit führen diese Abfragen Abfragen ohne angegebene Knotentypen durch, was dazu führt, dass aufgrund der Verwendung des generischen Lucene-Index eine WARN protokolliert wird.
> * Instanzen dieser Komponenten werden in Kürze automatisch auf `cq:Page` und `dam:Asset` Knotentypen ohne weitere Kundenaktion.
> * Die `nodeTypes` -Eigenschaft hinzugefügt werden, um diese standardmäßigen Knotentypen zu überschreiben.


## Zeitleiste für die generische Lucene-Entfernung {#timeline}

Adobe wird einen zweiphasigen Ansatz verfolgen, um den generischen Lucene-Index zu entfernen.

* **Phase 1** (Voraussichtlicher Beginn am 31. Januar 2022): Nicht mehr erstellen `/oak:index/lucene-*` in neuen AEM as a Cloud Service Umgebungen.
* **Phase 2** (Geplanter Beginn am 31. März 2022): Entfernen `/oak:index/lucene-*` aus bestehenden AEM as a Cloud Service Umgebungen.

Adobe überwacht die oben genannten Protokollmeldungen und versucht, Kunden zu kontaktieren, die weiterhin vom generischen Lucene-Index abhängig sind.

Als kurzfristige Abmilderung fügt Adobe benutzerdefinierte Indexdefinitionen direkt zu Kundensystemen hinzu, um Funktions- oder Leistungsprobleme zu vermeiden, die durch die Entfernung des generischen Lucene-Index bei Bedarf auftreten.

In solchen Fällen wird dem Kunden die aktualisierte Indexdefinition bereitgestellt und empfohlen, diese in zukünftige Versionen seiner Anwendung über Cloud Manager aufzunehmen.
