---
title: Aktivieren der Front-End-Pipeline
description: Erfahren Sie, wie Sie die Frontend-Pipeline für vorhandene Sites aktivieren können, um Site-Designs zu nutzen und Ihre Site schneller anzupassen.
feature: Administering
role: Admin
source-git-commit: dc7e89c601bb02c78f65ca58eff34c15092b5561
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---


# Aktivieren der Front-End-Pipeline {#enable-front-end-pipeline}

Erfahren Sie, wie Sie die Frontend-Pipeline für vorhandene Sites aktivieren können, um Site-Designs zu nutzen und Ihre Site schneller anzupassen.

## Übersicht {#overview}

Die Front-End-Pipeline ist ein Mechanismus, der schnell nur den Frontend-Code Ihrer Websites bereitstellt, basierend auf [Site-Designs](site-themes.md) und [Site-Vorlagen.](site-templates.md)

Statt den vollständigen Stapel bereitzustellen, wird nur Frontend-Code von dieser Pipeline verarbeitet, wodurch der Prozess schneller wird, und es Frontend-Entwicklern ermöglicht, Ihre Site einfach und schnell anzupassen, ohne dass Kenntnisse über AEM vorliegen.

Sites, die auf Site-Vorlagen basieren, können standardmäßig die Front-End-Pipeline nutzen. In diesem Dokument wird beschrieben, wie Sie Ihre vorhandenen Sites anpassen können, um die Front-End-Pipeline zu nutzen.

>[!TIP]
>
>Wenn Sie nicht mit der Frontend-Pipeline vertraut sind und erfahren, wie Sie Sites mit ihr und Site-Vorlagen schnell bereitstellen, lesen Sie bitte die Informationen unter [Journey zur schnellen Site-Erstellung](/help/journey-sites/quick-site/overview.md) für eine Einführung.

Wenn Sie Ihre vorhandene Site nicht auf der Grundlage von Site-Vorlagen und Designs erstellt haben, können AEM Ihre Site so konfigurieren, dass die Designs geladen werden, die mit der Frontend-Pipeline auf die vorhandenen Client-Bibliotheken bereitgestellt werden.

## Voraussetzungen {#requirements}

AEM können Ihre vorhandene Site automatisch an die Frontend-Pipeline anpassen. Um dies zu erreichen, muss Ihre Site [v2 oder neuer der Seitenkomponente der Kernkomponenten.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/page.html)

## Aktivieren der Front-End-Pipeline {#enabling}

Die Aktivierung Ihrer Site erfolgt über die Konsole Sites .

1. Melden Sie sich bei AEM an und navigieren Sie über **Globale Navigation** > **Sites**.
1. Wählen Sie Ihre Site in der Konsole aus. Sie müssen den Stamm der Site und keine untergeordneten Seiten auswählen.
1. Wenn Ihre Site ausgewählt ist, öffnen Sie die [Schienenauswahl](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector) auf der linken Seite und wählen Sie **Site**.
1. Im **Site** Leiste, klicken Sie auf die Schaltfläche **Front-End-Pipeline aktivieren**.

   ![Front-End-Pipeline aktivieren](/help/sites-cloud/administering/assets/enable-front-end-pipeline.png)

1. AEM fordert Sie zur Bestätigung auf, wobei Sie einen Überblick über die vorgenommenen Änderungen erhalten. Bestätigen Sie, dass Ihre Site angepasst wurde.

Jetzt kann Ihre Site die Front-End-Pipeline verwenden. Weitere Informationen zur Front-End-Pipeline finden Sie unter:

* [Journey zur schnellen Site-Erstellung](/help/journey-sites/quick-site/overview.md) - Diese Journey der Dokumentation bietet Ihnen einen Überblick über den Prozess der schnellen Bereitstellung einer Site mithilfe der Frontend-Pipeline und des Tools zur schnellen Site-Erstellung.
* [CI/CD Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) - In diesem Dokument wird die Front-End-Pipeline im Kontext der Full-Stack- und Web-Tier-Pipelines beschrieben.
