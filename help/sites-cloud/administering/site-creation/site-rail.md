---
title: Verwenden der Site-Leiste zum Verwalten Ihres Site-Designs
description: Erfahren Sie mehr über die leistungsstarken Funktionen der Seitenleiste, mit denen Sie Ihr Site-Design einfach anpassen und verwalten können.
feature: Administering
role: Admin
exl-id: 45785e5a-4fa2-4cf2-a300-f1865f6f5807
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# Verwenden der Site-Leiste zum Verwalten Ihres Site-Designs {#site-rail}

Erfahren Sie mehr über die leistungsstarken Funktionen der Seitenleiste, mit denen Sie Ihr Site-Design einfach anpassen und verwalten können.

## Übersicht {#overview}

Mit der Seitenleiste können Sie die Design- und Vorlagenressourcen Ihrer Site verwalten. [Wie andere Leisten](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector) z. B. die Leisten Inhaltsstruktur, Verweise oder Timeline wird die Seitenleiste in der Sites-Konsole als Bereich ganz links angezeigt, der Informationen zum ausgewählten Element anzeigt. Im Gegensatz zu anderen Leisten gilt die Seitenleiste nur für Site-Stämme.

Die Seitenleiste wird verwendet, um Informationen zu Designs und Vorlagen für Ihre Site zu verwalten, darunter:

* [Herunterladen von Themenquellen](#downloading-theme-sources)
* [Herunterladen von Vorlagenressourcen wie Wireframes](#downloading-template-resources)
* [Anzeigen und Ändern von Designversionen](#theme-vrsions)
* [Aktivieren der Front-End-Pipeline](#enabling-the-front-end-pipeline)

>[!TIP]
>
>Überprüfen Sie die [Journey zur schnellen Site-Erstellung](/help/journey-sites/quick-site/overview.md) , um sich mit dem Tool für die schnelle Site-Erstellung und der Front-End-Pipeline vertraut zu machen, um Ihr Site-Design einfach anzupassen.

##  Herunterladen von Themenquellen {#downloading-theme-sources}

Wenn Sie eine Site in AEM erstellen, die auf einer [Site-Vorlage,](site-templates.md) Sie können [Site-Design](site-themes.md) über die Seitenleiste.

Wenn die Seitenleiste in der Sites-Konsole angezeigt wird, wählen Sie den Stamm Ihrer Site aus, um Designinformationen über die Site anzuzeigen.

![Herunterladen von Themenquellen](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Tippen oder klicken Sie auf **Themenquellen herunterladen** , um eine lokale Kopie des Site-Designs als `.zip` -Datei zu Anpassungszwecken.

##  Herunterladen von Vorlagenressourcen {#downloading-template-resources}

[Site-Vorlagen](site-templates.md) kann zusätzlich zu Ihrer Site-Inhaltsstruktur Informationen enthalten und [Site-Design.](site-themes.md) Site-Vorlagen können beispielsweise Wireframe-Designs oder andere Site-bezogene Dateien enthalten.

Wenn Ihre Site auf einer Site-Vorlage basiert und die Site-Leiste in der Sites-Konsole angezeigt wird, wählen Sie den Stamm Ihrer Site aus, um Designinformationen über die Site anzuzeigen, einschließlich zusätzlicher Site-Ressourcen.

![Herunterladen von Themenquellen](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Tippen oder klicken Sie auf die Schaltfläche oder Schaltflächen unter der Überschrift **Zusätzliche Vorlagenressourcen herunterladen** um eine lokale Kopie der verfügbaren Dateien herunterzuladen.

## Anzeigen und Ändern von Designversionen {#them-versions}

Wenn Ihre Site auf einer Site-Vorlage basiert, kann es sein, dass das Design bereits von Ihrem Frontend-Entwickler angepasst wurde. Über die Seitenleiste können Sie anzeigen, welche Version des Site-Designs derzeit bereitgestellt ist, und zu früheren Versionen wechseln.

Wenn die Seitenleiste in der Sites-Konsole angezeigt wird, wählen Sie den Stamm Ihrer Site aus, um Designinformationen über die Site anzuzeigen.

![Site-Versionen in der Leiste](/help/sites-cloud/administering/assets/theme-versions.png)

Die aktuelle Version des Designs wird mit dem Commithash und dem Zeitstempel der letzten Aktualisierung angezeigt.

Tippen oder klicken Sie auf **Version auswählen** , um frühere Versionen des Designs anzuzeigen.

![Designversion auswählen](/help/sites-cloud/administering/assets/select-theme-versions.png)

Tippen oder klicken Sie auf die Version, zu der Sie ändern möchten, und tippen oder klicken Sie dann auf **Anwenden** , um die Änderung vorzunehmen.

Wenn AEM erkennt, dass eine neuere Version des Designs über die Frontend-Pipeline bereitgestellt, aber nicht auf Ihre Site angewendet wurde, wird ein Benachrichtigungssymbol angezeigt.

![Neuere Version der Designanzeige](/help/sites-cloud/administering/assets/new-theme-version.png)

Sie können die **Version auswählen** -Schaltfläche, um auf die neue Designversion zu aktualisieren.

## Aktivieren der Front-End-Pipeline {#enabling-front-end-pipeline}

Wenn Ihre Site nicht mit einer Site-Vorlage erstellt wurde, ist es nicht möglich, die Front-End-Pipeline zum Anpassen und Bereitstellen ihres Designs zu verwenden.

Sie können die Front-End-Pipeline für Ihre Site jedoch über die Site-Leiste aktivieren.

Wenn die Seitenleiste in der Sites-Konsole angezeigt wird, wählen Sie den Stamm Ihrer Site aus, um Designinformationen über die Site anzuzeigen, und tippen oder klicken Sie dann auf **Front-End-Pipeline aktivieren**.

![Aktivieren der Front-End-Pipeline](/help/sites-cloud/administering/assets/enable-fep.png)

Weitere Informationen finden Sie im Dokument . [Aktivieren der Front-End-Pipeline.](enable-front-end-pipeline.md)
