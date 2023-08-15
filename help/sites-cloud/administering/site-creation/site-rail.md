---
title: Verwenden der Site-Leiste zum Verwalten Ihres Site-Designs
description: Erfahren Sie mehr über die leistungsstarken Funktionen der Site-Leiste, mit denen Sie Ihr Site-Design einfach anpassen und verwalten können.
feature: Administering
role: Admin
exl-id: 45785e5a-4fa2-4cf2-a300-f1865f6f5807
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 97%

---

# Verwenden der Site-Leiste zum Verwalten Ihres Site-Designs {#site-rail}

Erfahren Sie mehr über die leistungsstarken Funktionen der Site-Leiste, mit denen Sie Ihr Site-Design einfach anpassen und verwalten können.

## Übersicht {#overview}

Über die Seitenleiste können Sie das Design und die Vorlagenressourcen Ihrer Site verwalten. [Wie andere Leisten](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector), z. B. die Inhaltsstruktur-, Verweis- oder Timeline-Leisten wird die Site-Leiste in der Sites-Konsole als Bereich ganz links angezeigt, der Informationen zum ausgewählten Element anzeigt. Im Gegensatz zu anderen Leisten gilt die Site-Leiste nur für Site-Stammverzeichnisse.

Die Site-Leiste wird verwendet, um Informationen zu Designs und Vorlagen für Ihre Site zu verwalten, darunter:

* [Herunterladen von Design-Quellen](#downloading-theme-sources)
* [Herunterladen von Vorlagenressourcen wie Wireframes](#downloading-template-resources)
* [Anzeigen und Ändern von Design-Versionen](#theme-vrsions)
* [Aktivieren der Frontend-Pipeline](#enabling-the-front-end-pipeline)

>[!TIP]
>
>Lesen Sie den Artikel [Journey zur schnellen Site-Erstellung](/help/journey-sites/quick-site/overview.md), um sich mit dem Tool für die schnelle Site-Erstellung und der Frontend-Pipeline vertraut zu machen. Das wird Ihnen helfen, Ihr Site-Design einfach anzupassen.

## Herunterladen von Design-Quellen {#downloading-theme-sources}

Wenn Sie in AEM eine Site erstellen, die auf einer [Site-Vorlage](site-templates.md) basiert, können Sie Ihr [Site-Design](site-themes.md) über die Site-Leiste herunterladen.

Wenn die Site-Leiste in der Sites-Konsole angezeigt wird, wählen Sie das Stammverzeichnis Ihrer Site aus, um Design-Informationen über die Site anzuzeigen.

![Herunterladen von Design-Quellen](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Tippen oder klicken Sie auf **Design-Quellen herunterladen**, um eine lokale Kopie des Site-Designs als `.zip`-Datei zu Anpassungszwecken herunterzuladen.

## Herunterladen von Vorlagenressourcen {#downloading-template-resources}

[Site-Vorlagen](site-templates.md) können zusätzlich zu Ihrer Site-Inhaltsstruktur und dem [Site-Design Informationen enthalten.](site-themes.md) Site-Vorlagen können beispielsweise Wireframe-Designs oder andere Site-bezogene Dateien enthalten.

Wenn Ihre Site auf einer Site-Vorlage basiert und die Site-Leiste in der Sites-Konsole angezeigt wird, wählen Sie das Stammverzeichnis Ihrer Site aus, um Design-Informationen über die Site anzuzeigen, einschließlich zusätzlicher Site-Ressourcen.

![Herunterladen von Design-Quellen](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Tippen oder klicken Sie auf die Schaltfläche oder die Schaltflächen unter der Überschrift **Zusätzliche Vorlagenressourcen herunterladen**, um eine lokale Kopie der verfügbaren Dateien herunterzuladen.

## Anzeigen und Ändern von Design-Versionen {#them-versions}

Wenn Ihre Site auf einer Site-Vorlage basiert, kann es sein, dass das Design bereits von Ihrem Frontend-Entwickler angepasst wurde. Über die Site-Leiste können Sie anzeigen, welche Version des Site-Designs derzeit bereitgestellt ist, und zu früheren Versionen wechseln.

Wenn die Site-Leiste in der Sites-Konsole angezeigt wird, wählen Sie das Stammverzeichnis Ihrer Site aus, um Design-Informationen über die Site anzuzeigen.

![Site-Versionen in der Leiste](/help/sites-cloud/administering/assets/theme-versions.png)

Die aktuelle Version des Designs wird mit dem Commit-Hash und dem Zeitstempel der letzten Aktualisierung angezeigt.

Tippen oder klicken Sie auf **Version auswählen**, um frühere Versionen des Designs anzuzeigen.

![Auswahl der Design-Version](/help/sites-cloud/administering/assets/select-theme-versions.png)

Tippen oder klicken Sie auf die Version, zu der Sie wechseln möchten, und tippen oder klicken Sie dann auf **Anwenden**, um den Wechsel zu vollziehen.

Wenn AEM erkennt, dass eine neuere Version des Designs über die Frontend-Pipeline bereitgestellt, aber nicht auf Ihre Site angewendet wurde, wird ein Benachrichtigungssymbol angezeigt.

![Neuere Version der Design-Anzeige](/help/sites-cloud/administering/assets/new-theme-version.png)

Sie können die Schaltfläche **Version auswählen** verwenden, um auf die neue Design-Version zu aktualisieren.

## Aktivieren der Frontend-Pipeline {#enabling-front-end-pipeline}

Wenn Ihre Site nicht mit einer Site-Vorlage erstellt wurde, ist es nicht möglich, die Frontend-Pipeline zum Anpassen und Bereitstellen ihres Designs zu verwenden.

Sie können die Frontend-Pipeline für Ihre Site jedoch über die Site-Leiste aktivieren.

Wenn die Site-Leiste in der Sites-Konsole angezeigt wird, wählen Sie das Stammverzeichnis Ihrer Site aus, um Design-Informationen über die Site anzuzeigen, und tippen oder klicken Sie dann auf **Frontend-Pipeline aktivieren**.

![Aktivieren der Frontend-Pipeline](/help/sites-cloud/administering/assets/enable-fep.png)

Weitere Informationen finden Sie im Dokument [Aktivieren der Frontend-Pipeline.](enable-front-end-pipeline.md)
