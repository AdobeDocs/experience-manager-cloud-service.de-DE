---
title: So gestalten Sie Ihren Inhalt
description: In diesem Teil der AEM Developer-Journey lernen Sie, wie Sie Ihre Inhalte für AEM Headless-Versand mit Datenmodellierung mit Inhaltsfragmentmodellen und Inhaltsfragmenten modellieren.
hide: true
hidefromtoc: true
index: false
translation-type: tm+mt
source-git-commit: 9fb18dbe60121f46dba1e11d4133e5264a6d538d
workflow-type: tm+mt
source-wordcount: '1671'
ht-degree: 4%

---


# So modellieren Sie Ihren Inhalt {#model-your-content}

>[!CAUTION]
>
>ARBEITEN IN FORTSCHRITTEN - Die Schaffung dieses Dokuments ist im Gange und sollte nicht als vollständig oder endgültig betrachtet werden und auch nicht für Produktionszwecke verwendet werden.

In diesem Teil der Journey [AEM Headless Developer lernen Sie, wie Sie Ihre Inhaltsstruktur modellieren. ](overview.md) Anschließend können Sie diese Struktur für Adobe Experience Manager (AEM) mithilfe von Inhaltsfragmentmodellen und Inhaltsfragmenten zur Wiederverwendung über mehrere Kanal hinweg nutzen.

## Die Meldung bisher {#story-so-far}

Am Anfang [Erfahren Sie mehr über CMS Headless Development](learn-about.md) deckte den Versand von kostenlosen Inhalten und warum er verwendet werden sollte. Dann [Erste Schritte mit AEM Headless als Cloud Service](getting-started.md) beschrieben AEM Kopflos im Kontext Ihres eigenen Projekts

Im vorherigen Dokument der AEM kopflosen Journey, [Pfad zu Ihrem ersten Erlebnis mit AEM Headless](/help/implementing/developing/headless-journey/path-to-first-experience.md), haben Sie dann die erforderlichen Schritte zur Implementierung Ihres ersten Projekts gelernt. Nach dem Lesen sollten Sie:

* Wichtige Planungsüberlegungen zum Entwerfen von Inhalten
* Machen Sie sich mit den Schritten vertraut, die Sie je nach den Anforderungen auf der Integrationsstufe durchführen möchten.
* Richten Sie die erforderlichen Werkzeuge und AEM Konfigurationen ein.
* Machen Sie sich mit Best Practices vertraut, um die Journey ohne Kopf zu glätten, die Inhaltserstellung effizient zu gestalten und sicherzustellen, dass Inhalte schnell bereitgestellt werden.

Dieser Artikel baut auf diesen Grundlagen auf, damit Sie verstehen, wie Sie Ihr eigenes AEM kopfloses Projekt vorbereiten.

## Vorgabe {#objective}

* **Audience**: Anfänger
* **Zielsetzung**: Erfahren Sie, wie Sie Ihre Inhaltsstruktur modellieren und diese Struktur dann mithilfe von AEM Inhaltsfragmentmodellen und Inhaltsfragmenten realisieren:
   * Einführung von Konzepten und Terminologie für [Datenmodellierung](#data-modeling).
   * Lernen Sie [warum Datenmodellierung für den Versand mit Headless-Inhalt](#data-modeling-for-aem-headless) erforderlich ist.
   * Lernen Sie [wie Sie diese Struktur mit AEM Inhaltsfragmentmodellen](#create-structure-content-fragment-models) (und mit [Inhaltsfragmenten](#use-content-to-author-content) erstellen) realisieren.
   * Lernen Sie [wie Sie Ihren Inhalt modellieren](#getting-started-examples); Grundprinzipien mit Basisproben.

>[!NOTE]
>
>Die Datenmodellierung ist ein sehr großes Feld, wie es bei der Entwicklung von relationalen Datenbanken verwendet wird. Es gibt viele Bücher und Online-Informationsquellen.
>
>Wir werden nur die Aspekte berücksichtigen, die bei der Modellierung von Daten für die Verwendung mit AEM Headless von Interesse sind.

## Datenmodellierung {#data-modeling}

*Es ist eine große schlechte Welt da draußen*.

Vielleicht nicht, aber es ist sicherlich eine große ***komplizierte*** Welt da draußen und Datenmodellierung wird verwendet, um eine vereinfachte Darstellung eines sehr (sehr) kleinen Unterabschnitts zu definieren, unter Verwendung der spezifischen Informationen, die für einen bestimmten Zweck benötigt werden.

Beispiel:

Es gibt viele Schulen, aber sie alle haben verschiedene Gemeinsamkeiten:

* Ein Ort
* Schulleiter
* Viele Lehrer
* Viele Lehrkräfte
* Viele Schüler
* Viele Exfredakteure
* Viele Schüler/innen
* Viele Klassenzimmer
* Viele (viele) Bücher
* Viele (viele) Ausrüstungsgegenstände
* Viele Aktivitäten außerhalb des Lehrplans
* und so weiter....

Selbst in einem so kleinen Beispiel kann die Liste endlos erscheinen. Wenn Sie jedoch möchten, dass Ihre Anwendung eine einfache Aufgabe durchführt, müssen Sie die Informationen auf das Wesentliche beschränken.

Beispielsweise die Werbung für besondere Ereignisse für alle Schulen in der Region:

* Schulname
* Schulort
* Schulleiter
* Typ des Ereignisses
* Ereignis
* Lehrer beim Organisieren des Ereignisses

### Konzepte {#concepts}

Was Sie beschreiben möchten, werden als **Entitäten** bezeichnet - im Grunde die &quot;Dinge&quot;, über die wir Informationen speichern möchten.

Die Informationen, die wir über sie speichern möchten, sind die **Attribute** (Eigenschaften) wie Name und Qualifikationen für die Lehrer.

Dann gibt es zwischen den Entitäten verschiedene **Beziehungen**. Zum Beispiel hat eine Schule normalerweise nur einen Schulleiter und viele Lehrer (und normalerweise ist der Schulleiter auch Lehrer).

Der Prozess der Analyse und Definition dieser Informationen zusammen mit den Beziehungen zwischen ihnen wird als **Datenmodellierung** bezeichnet.

### Grundlagen {#basics}

Oft müssen Sie einen Beginn erstellen, indem Sie ein **Konzeptbedingtes Schema** erstellen, das die Entitäten und ihre Beziehungen beschreibt. In der Regel ist dies eine hohe Ebene (konzeptuell).

Sobald dies stabil ist, können Sie die Modelle in ein **Logisches Schema** übersetzen, das die Entitäten zusammen mit den Attributen und den Beziehungen beschreibt. Auf dieser Ebene sollten Sie die Definitionen genau untersuchen, um Duplizierungen zu vermeiden und Ihr Design zu optimieren.

>[!NOTE]
>
>Manchmal werden diese beiden Schritte zusammengeführt, oft abhängig von der Komplexität Ihres Szenarios.

Benötigen Sie beispielsweise separate Entitäten für `Head Teacher` und `Teacher` oder einfach ein zusätzliches Attribut für das `Teacher`-Modell?

### Datenintegrität {#data-integrity} gewährleisten

Datenintegrität ist erforderlich, um die Genauigkeit und Konsistenz Ihrer Inhalte während des gesamten Lebenszyklus zu gewährleisten. Dazu gehört auch, sicherzustellen, dass Autoren leicht verstehen können, was sie dort speichern sollen - daher sind folgende Punkte von entscheidender Bedeutung:

* eine klare Struktur
* eine möglichst knappe Struktur (ohne Beeinträchtigung der Genauigkeit)
* Validierung einzelner Felder
* gegebenenfalls den Inhalt bestimmter Felder auf das aussagekräftige beschränken

### Beseitigung der Datenredundanz {#data-redundancy}

Eine Datenredundanz tritt auf, wenn dieselben Informationen zweimal in der Inhaltsstruktur gespeichert werden. Dies sollte vermieden werden, da dies beim Erstellen des Inhalts zu Verwirrung und zu Fehlern bei der Abfrage führen kann. ganz zu schweigen von der missbräuchlichen Nutzung von Datenspeicherung.

### Optimierung und Leistung {#optimization-and-performance}

Durch die Optimierung Ihrer Struktur können Sie die Leistung sowohl bei der Inhaltserstellung als auch bei der Abfrage verbessern.

Alles ist ein Balanceakt, aber die Schaffung einer Struktur, die zu komplex ist oder zu viele Ebenen hat, kann:

* Verwirrend für Autoren, die den Inhalt erstellen.

* Schwere Auswirkungen auf die Leistung, wenn die Abfrage auf mehrere verschachtelte (referenzierte) Inhaltsfragmente zugreifen muss, um den erforderlichen Inhalt abzurufen.

## Datenmodellierung für AEM Headless {#data-modeling-for-aem-headless}

Datenmodellierung ist eine Reihe etablierter Techniken, oft verwendet, wenn entwickelte Beziehungsdatenbanken, also was bedeutet es für AEM Headless?

### Warum? {#why}

Um sicherzustellen, dass Ihre Anwendung die erforderlichen Inhalte konsistent und effizient von AEM anfordern und empfangen kann, muss dieser Inhalt strukturiert sein.

Das bedeutet, dass Ihre Anwendung die Form der Antwort im Voraus kennt und daher weiß, wie sie verarbeitet wird. Dies ist viel einfacher als der Empfang von Freiforminhalten, die analysiert werden müssen, um zu bestimmen, was sie enthält und daher, wie sie verwendet werden können.

### Einführung in Wie? {#how}

AEM verwendet Inhaltsfragmente, um die Strukturen bereitzustellen, die für den kopflosen Versand Ihrer Inhalte in Ihren Anwendungen erforderlich sind.

Die Struktur Ihres Datenmodells lautet:

* durch die Definition Ihres Inhaltsfragmentmodells,
* als Grundlage der Inhaltsfragmente verwendet, die für Ihre Inhaltsgenerierung verwendet werden.

>[!NOTE]
>
>Die Inhaltsfragmentmodelle werden auch als Grundlage der AEM GraphQL-Schema verwendet, die zum Abrufen Ihrer Inhalte verwendet werden - mehr darüber in einer späteren Sitzung.

Anfragen nach Inhalten werden mit der AEM GraphQL API, einer benutzerdefinierten Implementierung der Standard GraphQL API, gestellt. Mit der AEM GraphQL API können Sie (komplexe) Abfragen an Inhaltsfragmenten durchführen, wobei jede Abfrage einem bestimmten Modelltyp entspricht.

Die zurückgegebenen Inhalte können dann von Ihren Programmen verwendet werden.

## Erstellen der Struktur mit Inhaltsfragmentmodellen {#create-structure-content-fragment-models}

Inhaltsfragmentmodelle bieten verschiedene Mechanismen, mit denen Sie die Struktur Ihres Inhalts definieren können.

Ein Inhaltsfragmentmodell beschreibt eine Entität.

>[!NOTE]
>Sie müssen die Funktion &quot;Inhaltsfragment&quot;im Konfigurationsbrowser aktivieren, damit Sie neue Modelle erstellen können.

>[!TIP]
>
>Das Modell sollte so benannt werden, dass der Autor des Inhalts weiß, welches Modell beim Erstellen eines Inhaltsfragments ausgewählt werden soll.

In einem Modell:

1. **Mit** Datentypen können Sie die einzelnen Attribute definieren.
Definieren Sie beispielsweise das Feld mit dem Namen eines Lehrers als **Text** und dessen Dienstjahre als **Zahl**.
1. Mit den Datentypen **Content Reference** und **Fragmentverweis** können Sie Beziehungen zu anderen Inhalten in AEM erstellen.
1. Mit dem Datentyp **Fragmentverweis** können Sie mehrere Strukturebenen realisieren, indem Sie Ihre Inhaltsfragmente verschachteln (je nach Modelltyp). Dies ist für Ihre Datenmodellierung von entscheidender Bedeutung.

Beispiel:
![Inhaltsmodellierung mit Inhaltsfragmenten](assets/headless-modeling-01.png "Inhaltsmodellierung mit Inhaltsfragmenten")

### Datentypen {#data-types}

AEM stellt die folgenden Datentypen bereit, mit denen Sie Ihre Inhalte modellieren können:

* Einzeilentext
* Mehrzeilentext
* Zahl
* Boolesch
* Datum und Uhrzeit
* Aufzählung
* Tags
* Inhaltsreferenz
* Fragmentreferenz
* JSON-Objekt

### Verweise und verschachtelte Inhalte {#references-nested-content}

Zwei Datentypen bieten Verweise auf Inhalte außerhalb eines bestimmten Fragments:

* **Content**
ReferenceDies bietet einen einfachen Verweis auf andere Inhalte beliebiger Art.
Sie können beispielsweise auf ein Bild an einer bestimmten Position verweisen.

* **Fragmentverweis**
Dies stellt Verweise auf andere Inhaltsfragmente bereit.
Dieser Referenztyp wird verwendet, um verschachtelte Inhalte zu erstellen und die Beziehungen einzuführen, die zum Erstellen des Modells Ihres Inhalts erforderlich sind.
Der Datentyp kann so konfiguriert werden, dass Fragmentautoren folgende Möglichkeiten haben:
   * Direktes Bearbeiten des referenzierten Fragments
   * Erstellen eines neuen Inhaltsfragments basierend auf dem entsprechenden Modell

## Verwenden des Modells zum Erstellen von Inhalten mit Inhaltsfragmenten {#use-content-to-author-content}

Inhaltsfragmente basieren immer auf einem Inhaltsfragmentmodell. Das Modell stellt die Struktur bereit, das Fragment enthält den Inhalt.

### Auswählen des entsprechenden Modells {#select-model}

Der erste Schritt zum Erstellen Ihres Inhalts besteht darin, ein Inhaltsfragment zu erstellen. Dies basiert auf einem bestimmten Inhaltsfragmentmodell, das Sie als ersten Schritt des Erstellungsprozesses auswählen.

### Erstellen und Bearbeiten von strukturierten Inhalten {#create-edit-structured-content}

Nachdem das Fragment erstellt wurde, können Sie es im Inhaltsfragment-Editor öffnen. Folgende Informationen/Optionen sind verfügbar:

* Bearbeiten Sie Ihre Inhalte entweder im normalen oder im Vollbildmodus.
* Formatieren Sie Ihre Inhalte entweder als Volltext, als Text oder als Markierungen.
* Erstellen und verwalten Sie Variationen Ihrer Inhalte.
* Inhalt verknüpfen.
* Bearbeiten Sie die Metadaten.
* Baumstruktur anzeigen.
* Vorschau der JSON-Vertretung.

## Erste Schritte mit einigen Beispielen {#getting-started-examples}

<!--
tbc...
...and/or see the structures covered for the GraphQL samples...
...will those (ever) be delivered as an official sample package?
-->

Eine Grundstruktur als Beispiel finden Sie unter Die Struktur des Beispielinhaltsfragments.

## Wie geht es weiter {#whats-next}

Nachdem Sie nun gelernt haben, wie Sie Ihre Struktur modellieren und abhängig davon Inhalte erstellen können, gehen Sie als Nächstes zu [Erfahren Sie, wie Sie mithilfe der GraphQL-Abfragen auf Ihre Inhaltsfragmente zugreifen und diese abrufen können. ](access-your-content.md) Dadurch werden GraphQL vorgestellt und diskutiert, und dann werden einige Abfragen untersucht, um zu sehen, wie die Dinge in der Praxis funktionieren.

## Zusätzliche Ressourcen {#additional-resources}

* [Erste Schritte mit AEMHeadless](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=de) - Eine kurze Videoschulung mit einem Überblick über die Verwendung AEM kopflosen Funktionen, einschließlich Datenmodellierung und GraphQL
* [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md)  - die Interessentenseite für Inhaltsfragmente
   * [Inhaltsfragmente im Konfigurationsbrowser](/help/assets/content-fragments/content-fragments-configuration-browser.md) : Aktivieren Sie die Funktion &quot;Inhaltsfragment&quot;im Konfigurationsbrowser
   * [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)  - Erstellen und Bearbeiten von Inhaltsfragmentmodellen
   * [Verwalten von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-managing.md)  - Erstellen und Erstellen von Inhaltsfragmenten; Diese Seite führt Sie zu anderen detaillierten Abschnitten
* [AEM GraphQL-Schema](/help/implementing/developing/headless-journey/access-your-content.md)  - wie GraphQL Modelle realisiert
* [Die Struktur des Musterinhaltsfragments](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql)
