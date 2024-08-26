---
title: Aktivieren der Frontend-Pipeline
description: Erfahren Sie, wie Sie die Frontend-Pipeline für vorhandene Sites aktivieren können, um Site-Designs zu verwenden und Ihre Site schneller anzupassen.
feature: Administering
role: Admin
exl-id: 55d54d72-f87b-47c9-955f-67ec5244dd6e
solution: Experience Manager Sites
source-git-commit: 1415d07235641262814e81362c806572bcf582ba
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 49%

---

# Aktivieren der Frontend-Pipeline {#enable-front-end-pipeline}

Erfahren Sie, wie Sie die Frontend-Pipeline für vorhandene Sites aktivieren können, um Site-Designs zu verwenden und Ihre Site schneller anzupassen.

## Übersicht {#overview}

Die Frontend-Pipeline ist ein Mechanismus, der schnell nur den Frontend-Code Ihrer Websites bereitstellt, basierend auf [Site-Designs](site-themes.md) und [Site-Vorlagen](site-templates.md).

Diese Pipeline verarbeitet nur Front-End-Code, wodurch der Bereitstellungsprozess schneller ist als die Bereitstellung im ganzen Stapel. Dadurch können Frontend-Entwickler Ihre Site einfach anpassen, ohne Kenntnisse über AEM zu benötigen.

Sites, die auf Site-Vorlagen basieren, können standardmäßig die Frontend-Pipeline nutzen. In diesem Dokument wird beschrieben, wie Sie Ihre vorhandenen Sites anpassen können, um die Frontend-Pipeline nutzen zu können.

>[!TIP]
>
>Wenn Sie nicht mit der Front-End-Pipeline vertraut sind und erfahren, wie Sie Sites schnell mit ihr und Sitevorlagen bereitstellen können, finden Sie eine Einführung unter [Quick Site Creation Journey](/help/journey-sites/quick-site/overview.md) .

AEM können Ihre Site so konfigurieren, dass mit der Frontend-Pipeline bereitgestellte Designs geladen werden, selbst wenn Ihre Site nicht mit Sitevorlagen und Designs erstellt wurde, indem sie diese auf vorhandenen Client-Bibliotheken ablegen.

## Technische Details {#technical-details}

Wenn Sie die Frontend-Pipeline für eine Site aktivieren, nimmt AEM die folgenden Änderungen an Ihrer Site-Struktur vor.

* Alle Seiten der Site enthalten eine zusätzliche CSS- und JS-Datei, die durch die Bereitstellung von Aktualisierungen über eine dedizierte Cloud Manager-Frontend-Pipeline geändert werden kann.
* Die hinzugefügten CSS- und JS-Dateien sind anfangs leer. Sie können jedoch einen Ordner &quot;Themenquellen&quot;herunterladen, um die Ordnerstruktur einzurichten, die zum Bereitstellen von CSS- und JS-Code-Updates über die Pipeline erforderlich ist.
* Nur ein Entwickler kann die Änderung rückgängig machen, indem er die `SiteConfig` - und `HtmlPageItemsConfig` -Knoten löscht, die dieser Vorgang unter `/conf/<site-name>/sling:configs` erstellt.

>[!NOTE]
>
>Durch diese Aktion werden die vorhandenen Client-Bibliotheken der Site nicht automatisch für die Verwendung der Schrift-End-Pipeline konvertiert. Das Verschieben dieser Quellen aus dem Client-Bibliotheksordner in den Frontend-Pipeline-Ordner ist eine Aufgabe, die von einem Frontend-Entwickler manuell durchgeführt werden muss.

## Voraussetzungen {#requirements}

AEM kann Ihre vorhandene Site automatisch an die Frontend-Pipeline anpassen. Um diesen Workflow durchführen zu können, muss Ihre Site [v2 oder höher der Seitenkomponente der Kernkomponenten verwenden.](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/wcm-components/page)

## Aktivieren der Frontend-Pipeline {#enabling}

{{add-cm-allowlist-frontend-pipeline}}

Die Aktivierung Ihrer Site erfolgt über die Sites-Konsole unter Verwendung der [Site-Leiste](site-rail.md).

1. Melden Sie sich bei AEM an und gehen Sie über **Globale Navigation** > **Sites** zu Ihrer Site.
1. Wählen Sie Ihre Site in der Konsole aus. Wählen Sie den Stamm der Site aus, keine untergeordneten Seiten.
1. Wenn Ihre Site ausgewählt ist, öffnen Sie die [Leistenauswahl](/help/sites-cloud/authoring/basic-handling.md#rail-selector) auf der linken Seite und wählen Sie **Site**.
1. Klicken Sie in der Leiste **Site** auf die Schaltfläche **Frontend-Pipeline aktivieren**.

   ![Frontend-Pipeline aktivieren](/help/sites-cloud/administering/assets/enable-front-end-pipeline.png)

1. AEM fordert Sie auf, die vorgenommenen Änderungen zu bestätigen. Bestätigen Sie, und Ihre Site ist angepasst.

Jetzt kann Ihre Site die Front-End-Pipeline verwenden. Weitere Informationen zur Frontend-Pipeline und zur Verwaltung Ihres Site-Designs finden Sie unter:

* [Verwenden der Site-Leiste zum Verwalten Ihres Site-Designs](site-rail.md)
* [Tour zur schnellen Site-Erstellung](/help/journey-sites/quick-site/overview.md): Diese Dokumentations-Tour gibt Ihnen einen umfassenden Überblick über den Prozess der schnellen Bereitstellung einer Website mithilfe der Frontend-Pipeline und des Tools zur schnellen Site-Erstellung.
* [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end): In diesem Dokument wird die Frontend-Pipeline im Kontext der Full-Stack- und Web-Stufen-Pipelines beschrieben.
