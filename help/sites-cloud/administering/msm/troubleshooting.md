---
title: Beheben von Problemen mit MSM und häufig gestellte Fragen
description: Erfahren Sie, wie Sie die häufigsten MSM-bezogenen Probleme beheben und Antworten auf die häufigsten MSM-bezogenen Fragen erhalten.
feature: Multi Site Manager
role: Admin
exl-id: 50f02f4f-a347-4619-ac90-b3136a7b1782
source-git-commit: c31f43986e44099a3a36cc6c9c2f1a7251499ffb
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 52%

---

# Beheben von Problemen mit MSM und häufig gestellte Fragen {#troubleshooting-msm}

## Fehlerbehebung: erste Schritte {#first-steps}

Wenn Sie ein Ihrer Ansicht nach falsches Verhalten oder einen Fehler in MSM feststellen, sollten Sie vor der detaillierten Fehlerbehebung Folgendes sicherstellen:

* Überprüfen Sie die [Häufig gestellte Fragen zu MSM](#faq) weil Ihre Probleme oder Fragen möglicherweise bereits dort angesprochen werden.
* Überprüfen Sie die [Artikel zu Best Practices für MSM](best-practices.md) da dort mehrere Tipps sowie Erläuterungen zu einigen falschen Vorstellungen angeboten werden.

## Erweiterte Informationen zum Status Ihres Blueprints und Ihrer Live Copy {#advanced-info}

MSM enthält mehrere Servlets, die mit Selektoren in den Ressourcen-URLs angefordert werden. Diese werden auf der Benutzeroberfläche verwendet, können aber auch direkt angefordert werden, um zusätzliche erweiterte und berechnete MSM-Statusinformationen für Ihre Seiten direkt anzuzeigen:

1. `http://<host>:<port>/content/path/to/bluprint/page.blueprint.json?&maxSize=500&advancedStatus=true&returnRelationships=true&msm%3Atrigger=ROLLOUT`
   * Verwenden Sie diesen Code auf einer Blueprint-Seite, um die Liste aller mit ihr verknüpften Live Copies mit zusätzlichen Live Copy-Statusinformationen abzurufen.
   * zum Beispiel:
     `http://localhost:4502/content/wknd/language-masters/en.blueprint.json?&maxSize=500&advancedStatus=true&returnRelationships=true&msm%3Atrigger=ROLLOUT`

1. `http://<host>:<port>/content/path/to/livecopy/page.msm.json`
   * Verwenden Sie diesen Code auf Live Copy-Seiten, um erweiterte Informationen über die Verbindung mit den Blueprint-Seiten abzurufen. Wenn es sich bei der Seite nicht um eine Live Copy handelt, erhalten Sie kein Ergebnis.
   * zum Beispiel:
     `http://localhost:4502/content/wknd/ca/en.msm.json`

Diese Servlets generieren DEBUG-Protokollmeldungen über den `com.day.cq.wcm.msm`-Logger, die ebenfalls hilfreich sein können.

## Abrufen MSM-spezifischer Informationen im Repository {#checking-repo}

Die Servlets haben berechnete Informationen auf Grundlage MSM-spezifischer Knoten und Mixins zurückgegeben. Diese Informationen werden folgendermaßen im Repository gespeichert.

* `cq:LiveSync`-Mixin-Typ
   * Dieser wird auf `jcr:content`-Knoten festgelegt und definiert Live Copy-Stammseiten.
   * Diese Seiten haben eine `cq:LiveSyncConfig` untergeordneter Knoten des Typs `cq:LiveCopy` , die grundlegende und obligatorische Informationen über die Live Copy über die folgenden Eigenschaften enthält:
      * `cq:master` verweist auf die Blueprint-Seite der Live Copy.
      * `cq:rolloutConfigs` zeigt aktive Rollout-Konfigurationen an, die auf die Live Copy angewendet werden.
      * `cq:isDeep` ist „true“, wenn die untergeordneten Seiten dieses Live Copy-Stamms in der Live Copy enthalten sind.
* `cq:LiveRelationship`-Mixin-Typ
   * Jede Live Copy-Seite verfügt über einen solchen Mixin-Typ auf ihrem `jcr:content`-Knoten.
   * Ist dies nicht der Fall, wurde die Seite irgendwann getrennt oder manuell über die Authoring-Oberfläche außerhalb einer Live Copy-Aktion erstellt (Erstellen oder Rollout).
* `cq:LiveSyncCancelled`-Mixin-Typ
   * Wurde zu `jcr:content`-Knoten der Live Copy-Seiten hinzugefügt, die ausgesetzt wurden.
   * Wenn die Aussetzung auch für untergeordnete Seiten gilt, wird eine `cq:isCancelledForChildren`-Eigenschaft auf demselben Knoten auf „true“ festgelegt.

Die in diesen Eigenschaften enthaltenen Informationen sollten auf der Benutzeroberfläche angezeigt werden. Bei der Fehlerbehebung ist es jedoch hilfreich, das MSM-Verhalten direkt im Repository zu beobachten, wenn MSM-Aktionen auftreten.

Das Wissen über diese Eigenschaften kann auch nützlich sein, damit Sie Ihr Repository abfragen und Seitensätze herausfinden können, die sich in bestimmten Status befinden. Beispiel:

* `select * from cq:LiveSync` gibt als Ergebnis alle Live Copy-Stammseiten zurück.

## Häufig gestellte Fragen (FAQ) {#faq}

Im Folgenden finden Sie einige häufig gestellte Fragen zu MSM und Live Copy.

### Warum werden einige Eigenschaften (z. B. Titel, Anmerkungen) während eines MSM-Rollouts nicht aktualisiert? {#missing-properties}

MSM-Synchronisierungsaktionen sind hochgradig konfigurierbar. Welche Eigenschaften oder Komponenten bei Rollouts direkt geändert werden, hängt von den Eigenschaften dieser Konfigurationen ab.

Weitere Informationen zu diesem Thema finden Sie in [diesem Artikel](best-practices.md).

### Wie kann ich Rollout-Berechtigungen für eine Gruppe von Autoren entfernen? {#remove-rollout-permissions}

Es gibt keine **Rollout** Berechtigung, die für Adobe Experience Manager-Prinzipale (Benutzer oder Gruppen) festgelegt oder entfernt werden kann.

Stattdessen können Sie Folgendes tun:

* Passen Sie die Benutzeroberfläche des Produkts an, um die Rollout-Aktionen für einen bestimmten Prinzipal auszublenden.
* Entfernen Sie Schreibberechtigungen aus der Live Copy-Struktur für Autoren, die keine Rollout durchführen dürfen.

### Warum sehe ich Live Copy-Seiten mit dem Suffix „_msm_move“? {#moved-pages}

Wenn eine Blueprint-Seite bereitgestellt wird, aktualisiert sie entweder ihre Live Copy-Seite oder erstellt eine Live Copy-Seite, falls sie noch nicht vorhanden ist. Beispiel: Das Rollout erfolgt zum ersten Mal oder die Live Copy-Seite wurde manuell gelöscht.

In diesem letzteren Fall jedoch, wenn eine Seite ohne `cq:LiveRelationship` -Eigenschaft mit demselben Namen vorhanden ist, wird diese Seite so umbenannt, bevor die Live Copy-Seite erstellt wird.

Standardmäßig erwartet der Rollout eine verknüpfte Live Copy-Seite, auf die die Aktualisierungen der Blueprints bereitgestellt werden. Oder es erwartet überhaupt keine Seite, wenn eine Live Copy-Seite erstellt wird.

Wenn eine &quot;eigenständige&quot;Seite gefunden wird, wählt MSM, diese Seite umzubenennen, und erstellt eine separate, verknüpfte Live Copy-Seite.

Eine solche eigenständige Seite in einer Live Copy-Unterstruktur ist normalerweise das Ergebnis einer **Trennen** oder die frühere Live Copy-Seite von einem Autor manuell gelöscht und dann mit demselben Namen neu erstellt wurde.

Verwenden Sie dazu die Live Copy **Aussetzen** anstelle von **Trennen**. Weitere Informationen über **Trennen** -Aktion finden Sie unter [diesen Artikel.](creating-live-copies.md)
