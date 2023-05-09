---
title: Fehlerbehebung in AEM beim Authoring
description: Einige Probleme bei der Verwendung von AEM
exl-id: b9c0584d-255e-486d-b829-09e07499ecd2
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 72%

---

# Fehlerbehebung in AEM beim Authoring {#troubleshooting-aem-when-authoring}

Der folgende Abschnitt beschäftigt sich mit einigen Problemen, auf die Sie bei der Arbeit mit AEM stoßen können, und liefert entsprechende Lösungsvorschläge.

## Alte Seitenversion wird weiterhin auf der veröffentlichten Website angezeigt {#old-page-version-still-on-published-site}

* **Problem**:
   * Sie haben Änderungen an einer Seite vorgenommen und die Seite in die Veröffentlichungs-Website veröffentlicht, die *alte* Version der Seite wird aber weiterhin auf der Veröffentlichungs-Website angezeigt.
* **Grund**:
   * Dies kann verschiedene Ursachen haben, meist den Cache (entweder Ihren lokalen Browser oder den Dispatcher), obwohl es manchmal ein Problem mit der Replikationswarteschlange sein kann.
* **Lösungen**:
   * Hier gibt es verschiedene Möglichkeiten:
   * Überprüfen Sie, ob die Seite korrekt repliziert wurde. Überprüfen Sie den Seitenstatus und ggf. den Status der Replikationswarteschlange.
   * Löschen Sie den Cache des lokalen Browsers und rufen Sie die Seite erneut auf.
   * Fügen Sie dem Ende der Seiten-URL `?` hinzu:
      * `http://<host>:<port>/sites.html/content?`
      * Dadurch wird die Seite direkt von AEM abgerufen und der Dispatcher wird umgangen. Wenn die aktualisierte Seite angezeigt wird, ist dies ein Hinweis darauf, dass Sie den Dispatcher-Cache löschen müssen.
   * Wenden Sie sich an den Systemadministrator, wenn Probleme mit den Replikationswarteschlangen vorliegen.

## Komponentenaktionen nicht in der Symbolleiste sichtbar {#component-actions-not-visible-on-toolbar}

* **Problem**:
   * Sämtliche entsprechenden Komponentenaktionen sind nicht sichtbar, wenn eine Seite in der Autorenumgebung bearbeitet wird.
* **Grund**:
   * In seltenen Fällen kann sich eine frühere Aktion auf die Symbolleiste auswirken.
* **Lösung**:
   * Aktualisieren Sie die Seite.
