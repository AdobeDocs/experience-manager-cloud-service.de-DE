---
title: Verwenden des Panels „Site“ zum Verwalten Ihres Site-Designs
description: Lernen Sie die leistungsstarken Funktionen des Panels „Site“ kennen, mit denen Sie Ihr Site-Design für traditionelle AEM-Authoring-Projekte einfach mit Veröffentlichungsbereitstellung anpassen und verwalten können.
feature: Administering
role: Admin
exl-id: 45785e5a-4fa2-4cf2-a300-f1865f6f5807
solution: Experience Manager Sites
source-git-commit: 076005e1ed1ca3303ed5843a3f27e0d707df5022
workflow-type: ht
source-wordcount: '607'
ht-degree: 100%

---


# Verwenden des Panels „Site“ zum Verwalten Ihres Site-Designs {#site-panel}

{{traditional-aem}}

Lernen Sie die leistungsstarken Funktionen des Panels „Site“ kennen, mit denen Sie Ihr Site-Design für traditionelle AEM-Authoring-Projekte einfach mit Veröffentlichungsbereitstellung anpassen und verwalten können.

## Überblick {#overview}

Das Panel „Site“ ermöglicht Ihnen die Verwaltung der Design- und Vorlagenressourcen Ihrer Site für herkömmliche AEM-Authoring-Projekte mit [Veröffentlichungsbereitstellung.](/help/sites-cloud/authoring/author-publish.md) [Genau wie andere Panels](/help/sites-cloud/authoring/sites-console/console-side-panel.md), z. B. die Panels „Inhaltsstruktur“, „Verweis“ oder „Timeline“, wird auch das Panel „Site“ in der Sites-Konsole ganz links als Bereich angezeigt, der Informationen zum ausgewählten Element enthält. Im Gegensatz zu anderen Bedienfeldern gilt das Site-Bedienfeld aber nur für Site-Stammverzeichnisse.

Das Site-Bedienfeld wird verwendet, um Informationen zu Designs und Vorlagen für Ihre Site zu verwalten, darunter:

* [Herunterladen von Design-Quellen](#downloading-theme-sources)
* [Herunterladen von Vorlagenressourcen wie Wireframes](#downloading-template-resources)
* [Anzeigen und Ändern von Design-Versionen](#theme-vrsions)
* [Aktivieren der Frontend-Pipeline](#enabling-the-front-end-pipeline)

>[!TIP]
>
>Lesen Sie den Artikel [Journey zur schnellen Site-Erstellung](/help/journey-sites/quick-site/overview.md), um sich mit dem Tool für die schnelle Site-Erstellung und der Frontend-Pipeline vertraut zu machen. Das wird Ihnen helfen, Ihr Site-Design einfach anzupassen.

## Herunterladen von Design-Quellen {#downloading-theme-sources}

Wenn Sie in AEM eine Site erstellen, die auf einer [Site-Vorlage](site-templates.md) basiert, können Sie Ihr [Site-Design](site-themes.md) über das Site-Bedienfeld herunterladen.

Wenn das Site-Bedienfeld in der Sites-Konsole angezeigt wird, wählen Sie das Stammverzeichnis Ihrer Site aus, um Design-Informationen über die Site anzuzeigen.

![Herunterladen von Design-Quellen](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Wählen Sie **Design-Quellen herunterladen** aus, um eine lokale Kopie des Site-Designs als `.zip`-Datei zu Anpassungszwecken herunterzuladen.

## Herunterladen von Vorlagenressourcen {#downloading-template-resources}

[Site-Vorlagen](site-templates.md) können zusätzlich zu Ihrer Site-Inhaltsstruktur und dem [Site-Design Informationen enthalten.](site-themes.md) Site-Vorlagen können beispielsweise Wireframe-Designs oder andere Site-bezogene Dateien enthalten.

Wenn Ihre Site auf einer Site-Vorlage basiert und das Site-Bedienfeld in der Sites-Konsole angezeigt wird, wählen Sie das Stammverzeichnis Ihrer Site aus, um Design-Informationen über die Site anzuzeigen, einschließlich zusätzlicher Site-Ressourcen.

![Herunterladen von Design-Quellen](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Wählen Sie die Schaltfläche oder die Schaltflächen unter der Überschrift **Zusätzliche Vorlagenressourcen herunterladen** aus, um eine lokale Kopie der verfügbaren Dateien herunterzuladen.

## Anzeigen und Ändern von Design-Versionen {#them-versions}

Wenn Ihre Site auf einer Site-Vorlage basiert, kann es sein, dass das Design bereits von Ihrem Frontend-Entwickler angepasst wurde. Über das Site-Bedienfeld können Sie anzeigen, welche Version des Site-Designs derzeit bereitgestellt ist, und zu früheren Versionen wechseln.

Wenn das Site-Bedienfeld in der Sites-Konsole angezeigt wird, wählen Sie das Stammverzeichnis Ihrer Site aus, um Design-Informationen über die Site anzuzeigen.

![Site-Versionen im Bedienfeld](/help/sites-cloud/administering/assets/theme-versions.png)

Die aktuelle Version des Designs wird mit dem Commit-Hash und dem Zeitstempel der letzten Aktualisierung angezeigt.

Wählen Sie **Version auswählen** aus, um frühere Versionen des Designs anzuzeigen.

![Auswahl der Design-Version](/help/sites-cloud/administering/assets/select-theme-versions.png)

Wählen Sie die Version aus, zu der Sie die Änderung vornehmen möchten, und wählen Sie dann **Anwenden**, um die Änderung vorzunehmen.

Wenn AEM erkennt, dass eine neuere Version des Designs über die Frontend-Pipeline bereitgestellt, aber nicht auf Ihre Site angewendet wurde, wird ein Benachrichtigungssymbol angezeigt.

![Neuere Version der Design-Anzeige](/help/sites-cloud/administering/assets/new-theme-version.png)

Sie können die Schaltfläche **Version auswählen** verwenden, um auf die neue Design-Version zu aktualisieren.

## Aktivieren der Frontend-Pipeline {#enabling-front-end-pipeline}

Wenn Ihre Site nicht mit einer Site-Vorlage erstellt wurde, ist es nicht möglich, die Frontend-Pipeline zum Anpassen und Bereitstellen ihres Designs zu verwenden.

Sie können die Frontend-Pipeline für Ihre Site jedoch über das Site-Bedienfeld aktivieren.

Wenn das Site-Bedienfeld in der Sites-Konsole angezeigt wird, wählen Sie das Stammverzeichnis Ihrer Site aus, um Design-Informationen über die Site anzuzeigen, und wählen Sie dann **Frontend-Pipeline aktivieren** aus.

![Aktivieren der Frontend-Pipeline](/help/sites-cloud/administering/assets/enable-fep.png)

Weitere Informationen finden Sie im Dokument [Aktivieren der Frontend-Pipeline.](enable-front-end-pipeline.md)
