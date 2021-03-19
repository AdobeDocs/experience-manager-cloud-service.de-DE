---
title: Fehlerbehebung bei MSM-Problemen und häufig gestellte Fragen
description: Erfahren Sie, wie Sie die häufigsten MSM-bezogenen Probleme beheben können, und erhalten Sie Antworten auf die häufigsten MSM-bezogenen Fragen.
feature: Multi-Site-Manager
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---


# Fehlerbehebung bei MSM-Problemen und häufig gestellten Fragen {#troubleshooting-msm}

## Fehlerbehebung bei ersten Schritten {#first-steps}

Wenn Sie ein falsches Verhalten oder einen Fehler in MSM feststellen, sollten Sie vor dem Beginn und der detaillierten Fehlerbehebung Folgendes sicherstellen:

* Überprüfen Sie die [MSM FAQ](#faq), da Ihre Probleme oder Fragen dort möglicherweise bereits angesprochen werden.
* Überprüfen Sie den Artikel [MSM Best Practices](best-practices.md), da hier eine Reihe von Tipps sowie Klarstellungen zu einer Reihe von falschen Vorstellungen angeboten werden.

## Erweiterte Informationen zu Ihrem blueprint- und Live Copy-Status {#advanced-info}

MSM registriert mehrere Servlets, die mit Selektoren in den Ressourcen-URLs angefordert werden können. Diese werden von der Benutzeroberfläche verwendet, können aber auch direkt angefordert werden, um direkt zusätzliche berechnete MSM-Status für Ihre Seiten anzuzeigen:

1. `http://<host>:<port>/content/path/to/bluprint/page.blueprint.json?&maxSize=500&advancedStatus=true&returnRelationships=true&msm%3Atrigger=ROLLOUT`
   * Verwenden Sie dies auf einer Blueprint-Seite, um die Liste aller mit ihr verknüpften Live-Kopien mit zusätzlichen Live Copy-Statusinformationen abzurufen.
1. `http://<host>:<port>/content/path/to/livecopy/page.msm.json`
   * Verwenden Sie dies auf Live Copy-Seiten, um erweiterte Informationen über ihre Verbindung mit ihren Musterseiten abzurufen. Wenn es sich bei der Seite nicht um eine Live Copy handelt, wird nichts zurückgegeben.

Diese Servlets erzeugen DEBUG-Logmeldungen über die `com.day.cq.wcm.msm`-Protokollfunktion, die ebenfalls hilfreich sein kann.

## Überprüfen von MSM-spezifischen Informationen im Repository {#checking-repo}

Die vorherigen Servlets gaben berechnete Informationen basierend auf den MSM-spezifischen Knoten und Mixins zurück. Die Informationen werden wie folgt im Repository gespeichert.

* `cq:LiveSync` mixin-Typ
   * Dies wird auf `jcr:content`-Knoten festgelegt und definiert Live Copy-Stammseiten.
   * Diese Seiten haben einen untergeordneten Knoten des Typs `cq:LiveCopy`, der grundlegende und obligatorische Informationen über die Live Copy über die folgenden Eigenschaften enthält:`cq:LiveSyncConfig`
      * `cq:master` verweist auf die Blueprint-Seite der Live Copy.
      * `cq:rolloutConfigs` zeigt aktive Rollout-Konfigurationen an, die auf die Live Copy angewendet werden.
      * `cq:isDeep` ist &quot;true&quot;, wenn die untergeordneten Seiten dieser Live Copy-Stammseite in der Live Copy-Datei enthalten sind.
* `cq:LiveRelationship` mixin-Typ
   * Jede Live Copy-Seite hat einen solchen Mixin-Typ auf ihrem `jcr:content`-Knoten.
   * Ist dies nicht der Fall, wurde die Seite zu einem bestimmten Zeitpunkt über die Authoring-Oberfläche außerhalb einer Live Copy-Aktion (Erstellen oder Rollout) getrennt oder manuell erstellt.
* `cq:LiveSyncCancelled` mixin-Typ
   * Es wurden `jcr:content`-Knoten der Live Copy-Seiten hinzugefügt, die ausgesetzt wurden.
   * Wenn die Aussetzung auch für untergeordnete Seiten wirksam ist, wird für eine `cq:isCancelledForChildren`-Eigenschaft auf demselben Knoten true festgelegt.

Die in diesen Eigenschaften enthaltenen Informationen sollten in der Benutzeroberfläche angezeigt werden. Bei der Fehlerbehebung kann es jedoch hilfreich sein, das MSM-Verhalten direkt im Repository zu beobachten, wenn MSM-Aktionen auftreten.

Das Wissen über diese Eigenschaften kann auch nützlich sein, um Ihr Repository zu Abfrage und herauszufinden, Gruppen von Seiten, die in bestimmten Status sind. Beispiel:

* `select * from cq:LiveSync` gibt alle Live Copy-Stammseiten zurück.

## Häufig gestellte Fragen (FAQ){#faq}

Hier sind einige häufig gestellte Fragen zu MSM und Live Copy.

### Warum werden einige Eigenschaften (z. B. Titel, Anmerkungen) während einer MSM-Einführung nicht aktualisiert? {#missing-properties}

MSM-Synchronisierungsaktionen sind hochgradig konfigurierbar. Welche Eigenschaften oder Komponenten während der Rollouts direkt geändert werden, hängt von den Eigenschaften dieser Konfigurationen ab.

Weitere Informationen zu diesem Thema finden Sie in [diesem Artikel](best-practices.md).

### Wie kann ich Rollout-Berechtigungen für eine Gruppe von Autoren entfernen? {#remove-rollout-permissions}

Es gibt keine **Rollout**-Berechtigung, die für AEM Prinzipale (Benutzer oder Gruppen) festgelegt oder entfernt werden kann.

Alternativ können Sie:

* Passen Sie die Benutzeroberfläche des Produkts an, um die Rollout-Aktionen für einen bestimmten Prinzipal auszublenden.
* Entfernen Sie Schreibberechtigungen aus der Live Copy-Struktur für Autoren, die keine Datenaggregation durchführen dürfen.

### Warum sehe ich Live Copy-Seiten mit dem Suffix &quot;_msm_move&quot;? {#moved-pages}

Wenn ein Rollout einer Musterseite erfolgt, wird entweder die entsprechende Live Copy-Seite aktualisiert oder eine neue Live Copy-Seite erstellt, falls diese noch nicht vorhanden ist (z. B. wenn sie zum ersten Mal herausgegeben wird oder die Live Copy-Seite manuell gelöscht wurde).

Wenn in diesem Fall jedoch eine Seite ohne `cq:LiveRelationship`-Eigenschaft mit demselben Namen vorhanden ist, wird diese Seite entsprechend umbenannt, bevor die Live Copy-Seite erstellt wird.

Standardmäßig erwartet die Einführung entweder eine verknüpfte Live Copy-Seite, auf die die Aktualisierungen der Entwürfe veröffentlicht werden, oder keine Seite bei der Erstellung einer Live Copy-Seite.

Wenn eine eigenständige Seite gefunden wird, wählt MSM, diese Seite umzubenennen und eine separate, verknüpfte Live Copy-Seite zu erstellen.

Eine solche eigenständige Seite in einer Live Copy-Unterstruktur ist normalerweise das Ergebnis eines Vorgangs **Detach** oder die vorherige Live Copy-Seite wurde von einem Autor manuell gelöscht und dann mit demselben Namen neu erstellt.

Um dies zu vermeiden, verwenden Sie die Funktion &quot;Live Copy **Suspend**&quot;anstelle von **Detach**. Weitere Informationen zur Aktion **Detach** in [diesem Artikel.](creating-live-copies.md)
