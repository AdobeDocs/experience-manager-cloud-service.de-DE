---
title: Beheben von Problemen mit MSM und häufig gestellte Fragen
description: Hier erfahren Sie, wie Sie die häufigsten Probleme mit MSM beheben, und erhalten Antworten auf häufig gestellte Fragen zu MSM.
feature: Multi Site Manager
role: Admin
exl-id: 50f02f4f-a347-4619-ac90-b3136a7b1782
solution: Experience Manager Sites
source-git-commit: 85cef99dc7a8d762d12fd6e1c9bc2aeb3f8c1312
workflow-type: ht
source-wordcount: '762'
ht-degree: 100%

---

# Beheben von Problemen mit MSM und häufig gestellte Fragen {#troubleshooting-msm}

## Fehlerbehebung: erste Schritte {#first-steps}

Wenn Sie ein Ihrer Ansicht nach falsches Verhalten oder einen Fehler in MSM feststellen, sollten Sie vor der detaillierten Fehlerbehebung Folgendes sicherstellen:

* Lesen Sie die [häufig gestellten Fragen zu MSM](#faq) durch, da Ihre Probleme oder Fragen dort möglicherweise bereits angesprochen werden.
* Unter [Best Practices für MSM](best-practices.md) finden Sie mehrere Tipps und es werden einige Missverständnisse ausgeräumt.

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
   * Diese Seiten haben einen `cq:LiveSyncConfig` untergeordneten Knoten des Typs `cq:LiveCopy`, der grundlegende und obligatorische Informationen über die Live Copy in den folgenden Eigenschaften enthält:
      * `cq:master` verweist auf die Blueprint-Seite der Live Copy.
      * `cq:rolloutConfigs` zeigt aktive Rollout-Konfigurationen an, die auf die Live Copy angewendet werden.
      * `cq:isDeep` ist „true“, wenn die untergeordneten Seiten dieses Live Copy-Stamms in der Live Copy enthalten sind.
* `cq:LiveRelationship`-Mixin-Typ
   * Jede Live Copy-Seite verfügt über einen solchen Mixin-Typ auf ihrem `jcr:content`-Knoten.
   * Ist dies nicht der Fall, wurde die Seite zu einem bestimmten Zeitpunkt getrennt oder manuell über die Autorenoberfläche außerhalb einer Live Copy-Aktion (Erstellen oder Rollout) erstellt.
* `cq:LiveSyncCancelled`-Mixin-Typ
   * Wurde zu `jcr:content`-Knoten der Live Copy-Seiten hinzugefügt, die ausgesetzt wurden.
   * Wenn die Aussetzung auch für untergeordnete Seiten gilt, wird eine `cq:isCancelledForChildren`-Eigenschaft auf demselben Knoten auf „true“ festgelegt.

Die in diesen Eigenschaften enthaltenen Informationen sollten auf der Benutzeroberfläche angezeigt werden. Bei der Fehlerbehebung ist es jedoch hilfreich, das MSM-Verhalten direkt im Repository zu beobachten, wenn MSM-Aktionen auftreten.

Die Kenntnis dieser Eigenschaften ist auch nützlich, um Abfragen an Ihr Repository zu senden und Seitensätze zu finden, die einen bestimmten Status aufweisen. Zum Beispiel:

* `select * from cq:LiveSync` gibt als Ergebnis alle Live Copy-Stammseiten zurück.

## Häufig gestellte Fragen {#faq}

Im Folgenden finden Sie einige häufig gestellte Fragen zu MSM und Live Copy.

### Warum werden einige Eigenschaften (z. B. Titel, Anmerkungen) während eines MSM-Rollouts nicht aktualisiert? {#missing-properties}

MSM-Synchronisierungsaktionen sind detailliert konfigurierbar. Welche Eigenschaften oder Komponenten während der Rollouts geändert werden, hängt unmittelbar von den Eigenschaften dieser Konfigurationen ab.

Weitere Informationen zu diesem Thema finden Sie in den [Best Practices für MSM](best-practices.md).

### Wie kann ich Rollout-Berechtigungen für eine Gruppe von Autorinnen und Autoren entfernen? {#remove-rollout-permissions}

Es gibt keine **Rollout**-Berechtigung, die für AEM-Prinzipale (Benutzende oder Gruppen) festgelegt oder entfernt werden kann.

Stattdessen können Sie Folgendes tun:

* Passen Sie die Benutzeroberfläche des Produkts an, um die Rollout-Aktionen für einen bestimmten Prinzipal auszublenden.
* Entfernen Sie Schreibberechtigungen aus der Live Copy-Struktur für Autorinnen und Autoren, die keinen Rollout durchführen dürfen.

### Warum sehe ich Live Copy-Seiten mit dem Suffix „_msm_moved“? {#moved-pages}

Wenn eine Blueprint-Seite bereitgestellt wird, aktualisiert sie entweder ihre Live Copy-Seite oder erstellt eine Live Copy-Seite, falls diese noch nicht vorhanden ist. Beispielsweise geschieht dies, wenn sie zum ersten Mal bereitgestellt wird oder die Live Copy-Seite manuell gelöscht wurde.

Wenn in letzterem Fall jedoch eine Seite ohne `cq:LiveRelationship`-Eigenschaft mit demselben Namen vorhanden ist, wird diese Seite entsprechend umbenannt, bevor die Live Copy-Seite erstellt wird.

Standardmäßig erwartet der Rollout eine verknüpfte Live Copy-Seite, auf die die Aktualisierungen der Blueprints bereitgestellt werden. Oder es wird überhaupt keine Seite erwartet, wenn eine Live Copy-Seite erstellt wird.

Wenn eine eigenständige Seite gefunden wird, benennt MSM diese Seite um und erstellt eine separate, verknüpfte Live Copy-Seite.

Eine solche eigenständige Seite in einer Live Copy-Unterstruktur ist normalerweise das Ergebnis der Aktion **Trennen** oder die vorherige Live Copy-Seite wurde von einer Autorin oder einem Autor manuell gelöscht und dann mit demselben Namen neu erstellt.

Um dies zu vermeiden, verwenden Sie die Funktion **Aussetzen** für die Live Copy anstelle von **Trennen**. Weitere Informationen zur Aktion **Trennen** finden Sie in [diesem Artikel.](creating-live-copies.md)
