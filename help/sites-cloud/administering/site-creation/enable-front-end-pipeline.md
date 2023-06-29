---
title: Aktivieren der Frontend-Pipeline
description: Erfahren Sie, wie Sie die Frontend-Pipeline für vorhandene Sites aktivieren können, um Site-Designs zu verwenden und Ihre Site schneller anzupassen.
feature: Administering
role: Admin
exl-id: 55d54d72-f87b-47c9-955f-67ec5244dd6e
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 82%

---

# Aktivieren der Frontend-Pipeline {#enable-front-end-pipeline}

Erfahren Sie, wie Sie die Frontend-Pipeline für vorhandene Sites aktivieren können, um Site-Designs zu verwenden und Ihre Site schneller anzupassen.

## Übersicht {#overview}

Die Frontend-Pipeline ist ein Mechanismus, der schnell nur den Frontend-Code Ihrer Websites bereitstellt, basierend auf [Site-Designs](site-themes.md) und [Site-Vorlagen](site-templates.md).

Statt den Full-Stack bereitzustellen, wird nur Frontend-Code von dieser Pipeline verarbeitet, wodurch der Prozess schneller wird, und Frontend-Entwicklern ermöglicht wird, Ihre Site einfach und schnell anzupassen, ohne dass Kenntnisse über AEM erforderlich sind.

Sites, die auf Site-Vorlagen basieren, können standardmäßig die Front-End-Pipeline verwenden. In diesem Dokument wird beschrieben, wie Sie Ihre vorhandenen Sites anpassen können, um die Frontend-Pipeline nutzen zu können.

>[!TIP]
>
>Wenn Sie nicht mit der Front-End-Pipeline vertraut sind und erfahren, wie Sie Sites mit ihr und Site-Vorlagen schnell bereitstellen, finden Sie weitere Informationen unter [Journey zur schnellen Site-Erstellung](/help/journey-sites/quick-site/overview.md) für eine Einführung.

Wenn Sie Ihre vorhandene Site nicht auf der Grundlage von Site-Vorlagen und Designs erstellt haben, kann AEM Ihre Site so konfigurieren, dass die Designs, die mit der Frontend-Pipeline bereitgestellt werden, auf die vorhandenen Client-Bibliotheken geladen werden.

## Technische Details {#technical-details}

Wenn Sie die Frontend-Pipeline für eine Site aktivieren, nimmt AEM die folgenden Änderungen an Ihrer Site-Struktur vor.

* Alle Seiten der Site enthalten eine zusätzliche CSS- und JS-Datei, die durch die Bereitstellung von Aktualisierungen über eine dedizierte Cloud Manager-Frontend-Pipeline geändert werden kann.
* Die hinzugefügten CSS- und JS-Dateien sind anfangs leer, aber es kann ein „Design-Quellen“-Ordner heruntergeladen werden, um die Ordnerstruktur zu erstellen, die es ermöglicht, CSS- und JS-Code-Updates über diese Pipeline bereitzustellen.
* Diese Änderung kann nur von einem Entwickler rückgängig gemacht werden, indem er die Knoten `SiteConfig` und `HtmlPageItemsConfig` löscht, die durch diesen Vorgang unterhalb von `/conf/<site-name>/sling:configs` entstehen.

>[!NOTE]
>
>Durch diese Aktion werden die vorhandenen Client-Bibliotheken der Site nicht automatisch für die Verwendung der Frontend-Pipeline konvertiert. Das Verschieben dieser Quellen aus dem Client-Bibliotheksordner in den Frontend-Pipeline-Ordner ist eine Aufgabe, die von einem Frontend-Entwickler manuell durchgeführt werden muss.

## Voraussetzungen {#requirements}

AEM kann Ihre vorhandene Site automatisch an die Frontend-Pipeline anpassen. Um dies zu erreichen, muss Ihre Site [v2 oder neuer der Seitenkomponente der Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/page.html?lang=de) verwenden.

## Aktivieren der Frontend-Pipeline {#enabling}

Die Aktivierung Ihrer Site erfolgt über die Sites-Konsole unter Verwendung der [Site-Leiste](site-rail.md).

1. Melden Sie sich bei AEM an und gehen Sie über **Globale Navigation** > **Sites** zu Ihrer Site.
1. Wählen Sie Ihre Site in der Konsole aus. Sie müssen den Stamm der Site und keine untergeordneten Seiten auswählen.
1. Wenn Ihre Site ausgewählt ist, öffnen Sie die [Leistenauswahl](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector) auf der linken Seite und wählen Sie **Site**.
1. Klicken Sie in der Leiste **Site** auf die Schaltfläche **Frontend-Pipeline aktivieren**.

   ![Frontend-Pipeline aktivieren](/help/sites-cloud/administering/assets/enable-front-end-pipeline.png)

1. AEM fordert Sie auf, die vorgenommenen Änderungen mit einem Überblick zu bestätigen. Bestätigen Sie, und Ihre Site ist angepasst.

Jetzt kann Ihre Site die Frontend-Pipeline verwenden. Weitere Informationen zur Frontend-Pipeline und zur Verwaltung Ihres Site-Designs finden Sie unter:

* [Verwenden der Site-Leiste zum Verwalten Ihres Site-Designs](site-rail.md)
* [Tour zur schnellen Site-Erstellung](/help/journey-sites/quick-site/overview.md): Diese Dokumentations-Tour gibt Ihnen einen umfassenden Überblick über den Prozess der schnellen Bereitstellung einer Website mithilfe der Frontend-Pipeline und des Tools zur schnellen Site-Erstellung.
* [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end): In diesem Dokument wird die Frontend-Pipeline im Kontext der Full-Stack- und Web-Stufen-Pipelines beschrieben.
