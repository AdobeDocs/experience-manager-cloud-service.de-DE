---
title: Fehlerbehebung für MSM-Probleme und häufig gestellte Fragen
description: Erfahren Sie, wie Sie die häufigsten MSM-bezogenen Probleme beheben und Antworten auf die häufigsten MSM-bezogenen Fragen erhalten.
feature: Multi-Site-Manager
role: Administrator
exl-id: 50f02f4f-a347-4619-ac90-b3136a7b1782
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 0%

---

# Fehlerbehebung bei MSM-Problemen und häufig gestellten Fragen {#troubleshooting-msm}

## Fehlerbehebung bei den ersten Schritten {#first-steps}

Wenn Sie feststellen, dass das Verhalten in MSM falsch oder fehlerhaft ist, sollten Sie vor dem Beginn und der detaillierten Fehlerbehebung Folgendes sicherstellen:

* Überprüfen Sie die [MSM FAQ](#faq), da Ihre Probleme oder Fragen möglicherweise bereits dort angesprochen werden.
* Überprüfen Sie den Artikel [Best Practices für MSM](best-practices.md), da dort eine Reihe von Tipps sowie Erläuterungen zu einer Reihe falscher Konzepte angeboten werden.

## Erweiterte Informationen zu Ihrem Blueprint- und Live Copy-Status {#advanced-info} finden

MSM registriert mehrere Servlets, die mit Selektoren für die Ressourcen-URLs angefordert werden können. Diese werden von der Benutzeroberfläche verwendet, können aber auch direkt angefordert werden, um direkt zusätzliche erweiterte berechnete MSM-Status für Ihre Seiten anzuzeigen:

1. `http://<host>:<port>/content/path/to/bluprint/page.blueprint.json?&maxSize=500&advancedStatus=true&returnRelationships=true&msm%3Atrigger=ROLLOUT`
   * Verwenden Sie dies auf einer Blueprint-Seite, um die Liste aller damit verknüpften Live Copies mit zusätzlichen Live Copy-Statusinformationen abzurufen.
1. `http://<host>:<port>/content/path/to/livecopy/page.msm.json`
   * Verwenden Sie dies auf Live Copy-Seiten, um erweiterte Informationen über ihre Verbindung mit ihren Blueprint-Seiten abzurufen. Wenn es sich bei der Seite nicht um eine Live Copy handelt, wird nichts zurückgegeben.

Diese Servlets generieren DEBUG-Protokollmeldungen über den `com.day.cq.wcm.msm`-Logger, der auch hilfreich sein kann.

## Überprüfen von MSM-spezifischen Informationen im Repository {#checking-repo}

Die vorherigen Servlets gaben berechnete Informationen basierend auf den MSM-spezifischen Knoten und Mixins zurück. Die Informationen werden wie folgt im Repository gespeichert.

* `cq:LiveSync` Mixin-Typ
   * Dies wird auf `jcr:content` -Knoten festgelegt und definiert Root Live Copy-Seiten.
   * Diese Seiten haben einen untergeordneten Knoten des Typs `cq:LiveCopy` , der grundlegende und obligatorische Informationen über die Live Copy über die folgenden Eigenschaften enthält:`cq:LiveSyncConfig`
      * `cq:master` verweist auf die Blueprint-Seite der Live Copy.
      * `cq:rolloutConfigs` zeigt aktive Rollout-Konfigurationen an, die auf die Live Copy angewendet werden.
      * `cq:isDeep` ist &quot;true&quot;, wenn die untergeordneten Seiten dieser Live Copy-Stammseite in der Live Copy enthalten sind.
* `cq:LiveRelationship` Mixin-Typ
   * Jede Live Copy-Seite hat einen solchen Mixin-Typ auf ihrem `jcr:content` -Knoten.
   * Ist dies nicht der Fall, wurde die Seite irgendwann getrennt oder manuell über die Authoring-Oberfläche außerhalb einer Live Copy-Aktion (Erstellen oder Rollout) erstellt.
* `cq:LiveSyncCancelled` Mixin-Typ
   * wurde zu `jcr:content` -Knoten von Live Copy-Seiten hinzugefügt, die ausgesetzt wurden.
   * Wenn die Aussetzung auch für untergeordnete Seiten wirksam ist, wird eine `cq:isCancelledForChildren` -Eigenschaft auf demselben Knoten auf &quot;true&quot;gesetzt.

Die in diesen Eigenschaften vorhandenen Informationen sollten in der Benutzeroberfläche angezeigt werden. Bei der Fehlerbehebung kann es jedoch hilfreich sein, das MSM-Verhalten direkt im Repository zu beobachten, da MSM-Aktionen auftreten.

Das Wissen über diese Eigenschaften kann auch nützlich sein, um Ihr Repository abzufragen und Seitensätze zu finden, die sich in bestimmten Status befinden. Beispiel:

* `select * from cq:LiveSync` gibt alle Live Copy-Stammseiten zurück.

## Häufig gestellte Fragen (FAQ) {#faq}

Im Folgenden finden Sie einige häufig gestellte Fragen zu MSM und Live Copy.

### Warum werden einige Eigenschaften (z. B. Titel, Anmerkungen) während eines MSM-Rollouts nicht aktualisiert? {#missing-properties}

MSM-Synchronisierungsaktionen sind hochgradig konfigurierbar. Welche Eigenschaften oder Komponenten bei Rollouts direkt geändert werden, hängt von den Eigenschaften dieser Konfigurationen ab.

Weitere Informationen zu diesem Thema finden Sie in [diesem Artikel](best-practices.md) .

### Wie kann ich Rollout-Berechtigungen für eine Gruppe von Autoren entfernen? {#remove-rollout-permissions}

Es gibt keine **Rollout**-Berechtigung, die für AEM Prinzipale (Benutzer oder Gruppen) festgelegt oder entfernt werden kann.

Alternativ können Sie Folgendes tun:

* Passen Sie die Produktoberfläche an, um die Rollout-Aktionen für einen bestimmten Prinzipal auszublenden.
* Entfernen Sie Schreibberechtigungen aus der Live Copy-Struktur für Autoren, die keine Rollout durchführen dürfen.

### Warum werden Live Copy-Seiten mit dem Suffix &quot;_msm_moved&quot;angezeigt? {#moved-pages}

Wenn eine Blueprint-Seite bereitgestellt wird, aktualisiert sie entweder ihre Live Copy-Seite oder erstellt eine neue Live Copy-Seite, falls sie noch nicht vorhanden ist (z. B. wenn sie zum ersten Mal bereitgestellt wird oder die Live Copy-Seite manuell gelöscht wurde).

Wenn in diesem Fall jedoch eine Seite ohne `cq:LiveRelationship`-Eigenschaft mit demselben Namen vorhanden ist, wird diese Seite entsprechend umbenannt, bevor die Live Copy-Seite erstellt wird.

Standardmäßig erwartet der Rollout entweder eine verknüpfte Live Copy-Seite, auf die die Blueprints aktualisiert werden, oder bei der Erstellung einer Live Copy-Seite keine Seite.

Wenn eine &quot;eigenständige&quot;Seite gefunden wird, wählt MSM, diese Seite umzubenennen und eine separate, verknüpfte Live Copy-Seite zu erstellen.

Eine solche eigenständige Seite in einem Live Copy-Unterbaum ist in der Regel das Ergebnis eines Vorgangs **Trennen** oder die frühere Live Copy-Seite wurde von einem Autor manuell gelöscht und dann mit demselben Namen neu erstellt.

Um dies zu vermeiden, verwenden Sie die Funktion Live Copy **Aussetzen** anstelle von **Trennen**. Weitere Informationen zur Aktion **Trennen** in [diesem Artikel.](creating-live-copies.md)
