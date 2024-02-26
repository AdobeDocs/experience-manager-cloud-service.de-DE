---
title: Verwalten des Site-Designs mithilfe des Site-Bedienfelds
description: Erfahren Sie mehr über die leistungsstarken Funktionen des Bedienfelds "Site", mit denen Sie Ihr Site-Design einfach anpassen und verwalten können.
feature: Administering
role: Admin
exl-id: 45785e5a-4fa2-4cf2-a300-f1865f6f5807
source-git-commit: f6162dcbc5b7937d55922e8c963a402697110329
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 49%

---


# Verwenden des Bedienfelds &quot;Site&quot;zum Verwalten Ihres Site-Designs {#site-panel}

Erfahren Sie mehr über die leistungsstarken Funktionen des Bedienfelds &quot;Site&quot;, mit denen Sie Ihr Site-Design einfach anpassen und verwalten können.

## Übersicht {#overview}

Im Bereich &quot;Site&quot;können Sie das Design und die Vorlagenressourcen Ihrer Site verwalten. [Wie andere Panels](/help/sites-cloud/authoring/sites-console/console-side-panel.md) z. B. in den Bedienfeldern Inhaltsstruktur, Verweise oder Timeline wird das Bedienfeld Site in der Sites-Konsole als Bereich ganz links angezeigt, der Informationen zum ausgewählten Element anzeigt. Im Gegensatz zu anderen Bedienfeldern gilt das Bedienfeld &quot;Site&quot;nur für die Stammordner der Site.

Der Bereich &quot;Site&quot;wird verwendet, um Informationen zu Themen und Vorlagen für Ihre Site zu verwalten, darunter:

* [Herunterladen von Design-Quellen](#downloading-theme-sources)
* [Herunterladen von Vorlagenressourcen wie Wireframes](#downloading-template-resources)
* [Anzeigen und Ändern von Design-Versionen](#theme-vrsions)
* [Aktivieren der Frontend-Pipeline](#enabling-the-front-end-pipeline)

>[!TIP]
>
>Lesen Sie den Artikel [Journey zur schnellen Site-Erstellung](/help/journey-sites/quick-site/overview.md), um sich mit dem Tool für die schnelle Site-Erstellung und der Frontend-Pipeline vertraut zu machen. Das wird Ihnen helfen, Ihr Site-Design einfach anzupassen.

## Herunterladen von Design-Quellen {#downloading-theme-sources}

Wenn Sie eine Site in AEM erstellen, die auf einer [Site-Vorlage,](site-templates.md) Sie können [Site-Design](site-themes.md) über den Bereich &quot;Site&quot;.

Wenn der Bereich &quot;Site&quot;in der Sites-Konsole angezeigt wird, wählen Sie den Stamm Ihrer Site aus, um Designinformationen über die Site anzuzeigen.

![Herunterladen von Design-Quellen](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Wählen Sie **Design-Quellen herunterladen** aus, um eine lokale Kopie des Site-Designs als `.zip`-Datei zu Anpassungszwecken herunterzuladen.

## Herunterladen von Vorlagenressourcen {#downloading-template-resources}

[Site-Vorlagen](site-templates.md) können zusätzlich zu Ihrer Site-Inhaltsstruktur und dem [Site-Design Informationen enthalten.](site-themes.md) Site-Vorlagen können beispielsweise Wireframe-Designs oder andere Site-bezogene Dateien enthalten.

Wenn Ihre Site auf einer Site-Vorlage basiert und der Site-Bereich in der Sites-Konsole angezeigt wird, wählen Sie den Stamm Ihrer Site aus, um Designinformationen über die Site anzuzeigen, einschließlich zusätzlicher Site-Ressourcen.

![Herunterladen von Design-Quellen](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Wählen Sie die Schaltfläche oder die Schaltflächen unter der Überschrift **Zusätzliche Vorlagenressourcen herunterladen** aus, um eine lokale Kopie der verfügbaren Dateien herunterzuladen.

## Anzeigen und Ändern von Design-Versionen {#them-versions}

Wenn Ihre Site auf einer Site-Vorlage basiert, kann es sein, dass das Design bereits von Ihrem Frontend-Entwickler angepasst wurde. Im Bedienfeld &quot;Site&quot;können Sie anzeigen, welche Version des Site-Designs derzeit bereitgestellt ist, und zu früheren Versionen wechseln.

Wenn der Bereich &quot;Site&quot;in der Sites-Konsole angezeigt wird, wählen Sie den Stamm Ihrer Site aus, um Designinformationen über die Site anzuzeigen.

![Site-Versionen im Bereich](/help/sites-cloud/administering/assets/theme-versions.png)

Die aktuelle Version des Designs wird mit dem Commit-Hash und dem Zeitstempel der letzten Aktualisierung angezeigt.

Wählen Sie **Version auswählen** aus, um frühere Versionen des Designs anzuzeigen.

![Auswahl der Design-Version](/help/sites-cloud/administering/assets/select-theme-versions.png)

Wählen Sie die Version aus, zu der Sie die Änderung vornehmen möchten, und wählen Sie dann **Anwenden**, um die Änderung vorzunehmen.

Wenn AEM erkennt, dass eine neuere Version des Designs über die Frontend-Pipeline bereitgestellt, aber nicht auf Ihre Site angewendet wurde, wird ein Benachrichtigungssymbol angezeigt.

![Neuere Version der Design-Anzeige](/help/sites-cloud/administering/assets/new-theme-version.png)

Sie können die Schaltfläche **Version auswählen** verwenden, um auf die neue Design-Version zu aktualisieren.

## Aktivieren der Frontend-Pipeline {#enabling-front-end-pipeline}

Wenn Ihre Site nicht mit einer Site-Vorlage erstellt wurde, ist es nicht möglich, die Frontend-Pipeline zum Anpassen und Bereitstellen ihres Designs zu verwenden.

Sie können die Front-End-Pipeline für Ihre Site jedoch über den Bereich &quot;Site&quot;aktivieren.

Wenn der Bereich &quot;Site&quot;in der Sites-Konsole angezeigt wird, wählen Sie den Stamm Ihrer Site aus, um Designinformationen über die Site anzuzeigen, und klicken Sie dann auf **Front-End-Pipeline aktivieren**.

![Aktivieren der Frontend-Pipeline](/help/sites-cloud/administering/assets/enable-fep.png)

Weitere Informationen finden Sie im Dokument [Aktivieren der Frontend-Pipeline.](enable-front-end-pipeline.md)
