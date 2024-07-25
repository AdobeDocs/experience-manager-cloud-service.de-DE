---
title: Inhaltsvererbung im universellen Editor
description: Erfahren Sie, wie der universelle Editor die Vererbung von Inhalten für Multi-Site-Management und Launches unterstützt, um die Wiederverwendung und Lokalisierung von Inhalten zu unterstützen.
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 58c58243dc98a21161afe0976da4dcdc235da0d3
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 7%

---


# Inhaltsvererbung im universellen Editor {#inheritance}

Erfahren Sie, wie der universelle Editor die Vererbung von Inhalten für Multi-Site-Management und Launches unterstützt, um die Wiederverwendung und Lokalisierung von Inhalten zu unterstützen.

## Nutzungsszenario {#use-case}

Für viele AEM ist das Erstellen einer Seite nur der Anfang. Um Inhalte effektiv zu skalieren, sind in der Regel die folgenden Schritte nach der Seitenerstellung erforderlich:

1. **Übersetzen Sie die Seite** mithilfe von Sprachkopien und Übersetzungs-Workflows.
1. **Lokalisieren Sie die Seite**, indem Sie die übersetzte Seite mithilfe der Multi-Site-Verwaltung in verschiedene Märkte einführen.
1. **Erstellen Sie neue Versionen**, indem Sie Launches verwenden, um zukünftige Iterationen der Seite vorzubereiten und diese Änderungen live zu stellen.

Diese Schritte können die Content-Geschwindigkeit beschleunigen und die Content-Konsistenz sicherstellen. Der universelle Editor unterstützt die Vererbung von Inhalten. Dies ist der Mechanismus, auf den diese Schritte basieren.

## Vererbung {#what-is-inheritance}

Vererbung ist der Mechanismus, bei dem Inhalte so verknüpft werden können, dass Inhaltsänderungen automatisch übernommen werden. Vererbte Komponenten können sich aus diversen Szenarien ergeben, wie:

* [Multi-Site-Management (MSM)](/help/sites-cloud/administering/msm/overview.md)
* [Launches](/help/sites-cloud/authoring/launches/overview.md)

MSM und Launches sind leistungsstarke Tools, mit denen Sie Ihre Inhalte wiederverwenden können. Seiten können aus einer zentralen Quelle (dem Blueprint) kopiert werden, damit Autoren spezifische Änderungen für den Kontext dieser Kopien vornehmen können, während der Rest des Inhalts von der Blueprint übernommen wird. Dies ist bei der Lokalisierung von Sites äußerst nützlich.

Um einen Teil des Inhalts der Kopien zu ändern, brechen Autoren die Vererbung für die betroffenen Komponenten auf, um sicherzustellen, dass ihre lokalen Änderungen nicht überschrieben werden, wenn die Kopien aus dem Blueprint synchronisiert werden.

## Inhaltsvererbung und der universelle Editor {#universal-editor}

Wenn eine Seite Teil von MSM ist oder ein Launch und Inhalt mit dem universellen Editor bearbeitet wird, deaktiviert der Editor automatisch die Vererbung für alle Änderungen, die von Autoren auf dieser Seite vorgenommen werden. Dadurch wird sichergestellt, dass geänderte Inhalte beibehalten werden, wenn Aktualisierungen aus dem Blueprint synchronisiert werden.

Der Autor muss nicht auf eine Schaltfläche klicken oder andere Schritte unternehmen, um die Vererbung zu deaktivieren, bevor er lokale Bearbeitungen vornimmt. Sobald eine Änderung vorgenommen wurde, wird die Vererbung implizit abgebrochen. Dies steht im Gegensatz zum [Seiten-Editor](/help/sites-cloud/authoring/page-editor/edit-content.md#inherited-components).

## Einschränkungen {#limitations}

* Autoren können die Vererbung für einzelne Komponenten nicht wiederherstellen.
   * Die Vererbung kann nur für die gesamte Seite über die Konsole [Live Copy Overview Console](/help/sites-cloud/administering/msm/live-copy-overview.md) oder die Konsole [Launches](/help/sites-cloud/authoring/launches/overview.md#the-launches-console) zurückgesetzt werden.
* Autoren haben kein visuelles Feedback, um zu sehen, für welche Komponenten ihre Vererbung deaktiviert ist und welche sie weiterhin beibehalten haben.
* Diese Funktionen sind derzeit auf Komponenten auf Seiten beschränkt und gelten noch nicht für [Inhaltsfragmente, ](/help/sites-cloud/administering/content-fragments/overview.md), obwohl sie auch MSM- und Launch-Funktionen aufweisen.
