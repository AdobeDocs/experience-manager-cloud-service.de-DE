---
title: Inhaltsvererbung im universellen Editor
description: Erfahren Sie, wie der universelle Editor die Inhaltsvererbung für Multi-Site-Management und Launches unterstützt, um die Wiederverwendung und Lokalisierung von Inhalten zu unterstützen.
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 773ce75975f4dcc2c5310422bcc377b487ebec25
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 80%

---


# Inhaltsvererbung im universellen Editor {#inheritance}

Erfahren Sie, wie der universelle Editor die Inhaltsvererbung für Multi-Site-Management und Launches unterstützt, um die Wiederverwendung und Lokalisierung von Inhalten zu unterstützen.

>[!NOTE]
>
>Diese Funktion ist nur für Inhalte verfügbar, die im AEM Repository gespeichert sind.

## Anwendungsfall {#use-case}

Für viele AEM-Benutzende ist das Erstellen einer Seite nur der Anfang. Für die effektive Skalierung von Inhalten sind nach der Seitenerstellung in der Regel die folgenden Schritte erforderlich:

1. **Übersetzen Sie die Seite** mithilfe von Sprachkopien und Übersetzungs-Workflows.
1. **Lokalisieren Sie die Seite**, indem Sie die übersetzte Seite mithilfe von Multi-Site-Management in verschiedene Märkte einführen.
1. **Erstellen Sie neue Versionen**, indem Sie Launches verwenden, um zukünftige Iterationen der Seite vorzubereiten und diese Änderungen live zu stellen.

Diese Schritte können die Inhaltsgeschwindigkeit beschleunigen und die Konsistenz zwischen Inhalten sicherstellen. Der universelle Editor unterstützt die Vererbung von Inhalten. Hierbei handelt es sich um den Mechanismus, auf den Sprachkopien, Multi-Site-Management und Launches basieren.

## Vererbung {#what-is-inheritance}

Vererbung ist der Mechanismus, durch den Inhalte so verknüpft werden können, dass Inhaltsänderungen automatisch übernommen werden. 

MSM und Launches sind leistungsstarke Tools, mit denen Sie Ihren Inhalt mithilfe der Vererbung wiederverwenden können. Seiten können aus einer zentralen Quelle (dem Blueprint) kopiert werden, damit Autorinnen und Autoren spezifische Änderungen für den Kontext dieser Kopien vornehmen können, während der Rest des Inhalts von dem Blueprint übernommen wird. Dies ist äußerst nützlich bei der Lokalisierung von Sites.

Um einen Teil des Inhalts der Kopien zu ändern, unterbrechen Autorinnen und Autoren die Vererbung für die betroffenen Komponenten, um sicherzustellen, dass ihre lokalen Änderungen nicht überschrieben werden, wenn die Kopien aus dem Blueprint synchronisiert werden.

## Inhaltsvererbung und der universelle Editor {#universal-editor}

Wenn eine Seite Teil des MSM oder eines Launches ist und Inhalte mit dem universellen Editor bearbeitet werden, deaktiviert der Editor automatisch die Vererbung für alle Änderungen, die von Autorinnen und Autoren auf dieser Seite vorgenommen werden. Dadurch wird sichergestellt, dass geänderte Inhalte beibehalten werden, wenn Aktualisierungen aus dem Blueprint synchronisiert werden.

Die Autorin oder der Autor muss zum Deaktivieren der Vererbung nicht erst auf eine Schaltfläche klicken oder andere Schritte unternehmen, bevor sie oder er lokale Bearbeitungen vornimmt. Sobald eine Änderung vorgenommen wurde, wird die Vererbung implizit abgebrochen. Dieses Verhalten steht im Gegensatz zum [Seiteneditor](/help/sites-cloud/authoring/page-editor/edit-content.md#inherited-components).

Der universelle Editor hat keine Auswirkungen auf den zugrunde liegenden Mechanismus der Vererbung. Weitere Informationen zur Funktionsweise der Vererbung finden Sie in der folgenden Dokumentation.

* [Multi-Site-Management (MSM)](/help/sites-cloud/administering/msm/overview.md)
* [Launches](/help/sites-cloud/authoring/launches/overview.md)

## Einschränkungen {#limitations}

* Autorinnen und Autoren können die Vererbung für einzelne Komponenten nicht zurücksetzen.
   * Die Vererbung kann nur für die gesamte Seite über die
      * [Konsole „Live Copy-Übersicht“](/help/sites-cloud/administering/msm/live-copy-overview.md)
      * [Launch-Konsole](/help/sites-cloud/authoring/launches/overview.md#the-launches-console)
      * Verwenden Sie die Schaltfläche **Zurücksetzen** auf der Registerkarte **Live Copy** des Fensters mit den Seiteneigenschaften [.](/help/sites-cloud/authoring/sites-console/page-properties.md)
* Autorinnen und Autoren verfügen über kein visuelles Feedback, um zu sehen, für welche Komponenten ihre Vererbung deaktiviert ist und welche sie weiterhin beibehalten haben.
* Diese Funktionen sind derzeit auf Komponenten auf Seiten beschränkt und gelten noch nicht für [Inhaltsfragmente,](/help/sites-cloud/administering/content-fragments/overview.md), obwohl sie auch MSM- und Launch-Funktionen aufweisen.
