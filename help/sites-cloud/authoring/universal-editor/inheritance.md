---
title: Inhaltsvererbung im universellen Editor
description: Erfahren Sie, wie der universelle Editor die Inhaltsvererbung für Multi-Site-Management und Launches unterstützt, um die Wiederverwendung und Lokalisierung von Inhalten zu unterstützen.
solution: Experience Manager Sites
feature: Authoring
role: User
exl-id: 2a1b87c2-29b9-4689-9a15-e17942439160
source-git-commit: 20f57e2b1b502f48f54e8a03d35a231d0c905739
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 82%

---

# Inhaltsvererbung im universellen Editor {#inheritance}

Erfahren Sie, wie der universelle Editor die Inhaltsvererbung für Multi-Site-Management und Launches unterstützt, um die Wiederverwendung und Lokalisierung von Inhalten zu unterstützen.

>[!NOTE]
>
>Diese Funktion ist nur für im AEM-Repository gespeicherte Dateitypen verfügbar.

## Anwendungsfall {#use-case}

Für viele AEM-Benutzende ist das Erstellen einer Seite nur der Anfang. Für die effektive Skalierung von Inhalten sind nach der Seitenerstellung in der Regel die folgenden Schritte erforderlich:

1. **Übersetzen Sie die Seite** mithilfe von Sprachkopien und Übersetzungs-Workflows.
1. **Lokalisieren Sie die Seite**, indem Sie die übersetzte Seite mithilfe von Multi-Site-Management in verschiedene Märkte einführen.
1. **Erstellen Sie neue Versionen**, indem Sie Launches verwenden, um zukünftige Iterationen der Seite vorzubereiten und diese Änderungen live zu stellen.

Diese Schritte können die Inhaltsgeschwindigkeit beschleunigen und die Konsistenz zwischen Inhalten sicherstellen. Der universelle Editor unterstützt die Vererbung von Inhalten. Dies ist der Mechanismus, auf dem Sprachkopien, das Multi Site Management und Launches basieren.

## Vererbung {#what-is-inheritance}

Vererbung ist der Mechanismus, durch den Inhalte so verknüpft werden können, dass Inhaltsänderungen automatisch übernommen werden. 

MSM und Launches sind leistungsstarke Tools, mit denen Sie Ihre Inhalte mithilfe der Vererbung wiederverwenden können. Seiten können aus einer zentralen Quelle (dem Blueprint) kopiert werden, damit Autorinnen und Autoren spezifische Änderungen für den Kontext dieser Kopien vornehmen können, während der Rest des Inhalts von dem Blueprint übernommen wird. Dies ist äußerst nützlich bei der Lokalisierung von Sites.

Um einen Teil des Inhalts der Kopien zu ändern, unterbrechen Autorinnen und Autoren die Vererbung für die betroffenen Komponenten, um sicherzustellen, dass ihre lokalen Änderungen nicht überschrieben werden, wenn die Kopien aus dem Blueprint synchronisiert werden.

## Inhaltsvererbung und der universelle Editor {#universal-editor}

Wenn eine Seite Teil des MSM oder eines Launches ist und Inhalte mit dem universellen Editor bearbeitet werden, deaktiviert der Editor automatisch die Vererbung für alle Änderungen, die von Autorinnen und Autoren auf dieser Seite vorgenommen werden. Dadurch wird sichergestellt, dass geänderte Inhalte beibehalten werden, wenn Aktualisierungen aus dem Blueprint synchronisiert werden.

Die Autorin oder der Autor muss zum Deaktivieren der Vererbung nicht erst auf eine Schaltfläche klicken oder andere Schritte unternehmen, bevor sie oder er lokale Bearbeitungen vornimmt. Sobald eine Änderung vorgenommen wurde, wird die Vererbung implizit abgebrochen. Dieser Workflow steht im Gegensatz zum [Seiteneditor](/help/sites-cloud/authoring/page-editor/edit-content.md#inherited-components).

Die Vererbung kann für die gesamte Seite über Folgendes rückgängig gemacht werden:

* [Konsole „Live Copy-Übersicht“](/help/sites-cloud/administering/msm/live-copy-overview.md)
* [Launch-Konsole](/help/sites-cloud/authoring/launches/overview.md#the-launches-console)
* Verwenden Sie die Schaltfläche **Zurücksetzen** auf der Registerkarte **Live Copy** des [Fensters „Seiteneigenschaften“](/help/sites-cloud/authoring/sites-console/page-properties.md).

Der universelle Editor wirkt sich nicht auf den zugrundeliegenden Mechanismus der Vererbung aus. Weitere Informationen zur Funktionsweise der Vererbung finden Sie in der folgenden Dokumentation.

* [Multi-Site-Management (MSM)](/help/sites-cloud/administering/msm/overview.md)
* [Launches](/help/sites-cloud/authoring/launches/overview.md)

### AEM-Erweiterung für Multi-Site-Management (MSM) {#msm-extension}

Sofern installiert, zeigt die Erweiterung **AEM Multi-Site-Management (MSM)** den aktuellen Vererbungsstatus der ausgewählten Komponente an und ermöglicht es Ihnen, die Vererbung auf Komponentenebene zu unterbrechen oder wiederherzustellen.

Weitere Informationen finden Sie in [ Dokumentation zur Bearbeitung ](/help/sites-cloud/authoring/universal-editor/authoring.md#inheritance)

## Einschränkungen {#limitations}

* Um die Vererbung für Einzelkomponenten rückgängig zu machen, muss die Erweiterung für die **AEM-Verwaltung mehrerer Websites (**) aktiviert sein.
* Um mit visuellem Feedback zu ermitteln, für welche Komponenten die Vererbung deaktiviert ist und für welche die Vererbung weiterhin beibehalten wird, muss die Erweiterung für die **AEM-** (MSM) aktiviert sein.
* Diese Funktionen sind derzeit auf Komponenten auf Seiten beschränkt und gelten noch nicht für [Inhaltsfragmente](/help/sites-cloud/administering/content-fragments/overview.md), obwohl diese ebenfalls MSM- und Launch-Funktionen aufweisen.
