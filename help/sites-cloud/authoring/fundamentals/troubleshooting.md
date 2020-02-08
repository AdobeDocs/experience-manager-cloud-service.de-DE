---
title: Fehlerbehebung in AEM bei der Bearbeitung
description: Probleme, die bei der Verwendung mit AEM auftreten können
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Fehlerbehebung in AEM bei der Bearbeitung {#troubleshooting-aem-when-authoring}

Der folgende Abschnitt beschäftigt sich mit einigen Problemen, auf die Sie bei der Arbeit mit AEM stoßen können, und liefert entsprechende Lösungsvorschläge.

## Alte Seitenversion wird weiterhin auf der Veröffentlichungs-Website angezeigt {#old-page-version-still-on-published-site}

* **Problem**:
   * You have made changes to a page and published the page to the publish site, but the *old* version of the page is still being shown on the publish site.
* **Grund**:
   * Dies kann verschiedene Gründe haben. Meist liegt es am Cache (entweder dem Ihres lokalen Browsers oder dem des Dispatchers), gelegentlich kann es sich jedoch auch um ein Problem mit der Replikations-Warteschlange handeln.
* **Lösungen**:
   * Hier gibt es mehrere Möglichkeiten:
   * Überprüfen Sie, ob die Seite korrekt repliziert wurde. Prüfen Sie den Seitenstatus und ggf. den Status der Replikations-Warteschlange.
   * Löschen Sie den Cache des lokalen Browsers und rufen Sie die Seite erneut auf.
   * Add `?` to the end of the page URL. For example:
      * `http://<host>:<port>/sites.html/content?`
      * Dadurch wird die Seite direkt von AEM abgerufen und der Dispatcher wird umgangen. Wenn die aktualisierte Seite angezeigt wird, ist dies ein Hinweis darauf, dass Sie den Dispatcher-Cache löschen müssen.
   * Wenden Sie sich an den Systemadministrator, wenn Probleme mit den Replikations-Warteschlangen vorliegen.

## Komponentenaktionen nicht in der Symbolleiste sichtbar {#component-actions-not-visible-on-toolbar}

* **Problem**:
   * Sämtliche entsprechenden Komponentenaktionen sind nicht sichtbar, wenn eine Seite in der Autorenumgebung bearbeitet wird. 
* **Grund**:
   * In seltenen Fällen kann eine frühere Aktion die Symbolleiste beeinflussen.
* **Lösung**:
   * Aktualisieren Sie die Seite.
