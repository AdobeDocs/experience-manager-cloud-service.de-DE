---
title: Aktivieren der Frontend-Pipeline
description: Erfahren Sie, wie Sie die Frontend-Pipeline für vorhandene traditionelle AEM-Authoring-Sites mit Veröffentlichungsbereitstellung aktivieren können, um Site-Designs zur schnelleren Anpassung Ihre Site zu nutzen.
feature: Administering
role: Admin
exl-id: 55d54d72-f87b-47c9-955f-67ec5244dd6e
solution: Experience Manager Sites
recommendations: display, noCatalog
source-git-commit: 0a458616afad836efae27e67dbe145fc44bee968
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 90%

---


# Aktivieren der Frontend-Pipeline {#enable-front-end-pipeline}

{{traditional-aem}}

Erfahren Sie, wie Sie die Frontend-Pipeline für vorhandene traditionelle AEM-Authoring-Sites mit Veröffentlichungsbereitstellung aktivieren können, um Site-Designs zur schnelleren Anpassung Ihre Site zu nutzen.

## Überblick {#overview}

Die Frontend-Pipeline ist ein Mechanismus für traditionelle AEM-Authoring-Projekte mit [Veröffentlichungsbereitstellung](/help/sites-cloud/authoring/author-publish.md), mit dem Sie schnell den Frontend-Code Ihrer Websites basierend auf [Site-Designs](site-themes.md) und [Site-Vorlagen](site-templates.md) bereitstellen können.

Diese Pipeline verarbeitet nur Frontend-Code, wodurch der Bereitstellungsprozess schneller ist als Full-Stack-Bereitstellungen. Dadurch können Frontend-Entwickelnde Ihre Site einfach anpassen, ohne Kenntnisse über AEM zu benötigen.

Sites, die auf Site-Vorlagen basieren, können standardmäßig die Frontend-Pipeline nutzen. In diesem Dokument wird beschrieben, wie Sie Ihre vorhandenen Sites anpassen können, um die Frontend-Pipeline nutzen zu können.

>[!TIP]
>
>Wenn Sie mit der Frontend-Pipeline und der schnellen Bereitstellung von Sites mithilfe dieser Pipeline und von Site-Vorlagen nicht vertraut sind, gehen Sie die [Tour zur schnellen Site-Erstellung](/help/journey-sites/quick-site/overview.md) durch, die Ihnen eine Einführung bietet.

AEM kann Ihre Site so konfigurieren, dass mit der Frontend-Pipeline bereitgestellte Designs geladen werden, selbst wenn Ihre Site nicht mit Site-Vorlagen und Designs erstellt wurde, indem sie diese auf vorhandenen Client-Bibliotheken ablegen.

## Technische Details {#technical-details}

Wenn Sie die Frontend-Pipeline für eine Site aktivieren, nimmt AEM die folgenden Änderungen an Ihrer Site-Struktur vor.

* Alle Seiten der Site enthalten eine zusätzliche CSS- und JS-Datei, die durch die Bereitstellung von Aktualisierungen über eine dedizierte Cloud Manager-Frontend-Pipeline geändert werden kann.
* Die hinzugefügten CSS- und JS-Dateien sind anfangs leer. Sie können jedoch einen Ordner „theme sources“ (Design-Quellen) herunterladen, um die notwendige Ordnerstruktur einzurichten, damit CSS- und JS-Code-Aktualisierungen über diese Pipeline bereitgestellt werden können.
* Nur Entwickelnde können die Änderung rückgängig machen, indem sie die Knoten `SiteConfig` und `HtmlPageItemsConfig` löschen, die dieser Vorgang unter `/conf/<site-name>/sling:configs` erstellt.

>[!NOTE]
>
>Durch diese Aktion werden die vorhandenen Client-Bibliotheken der Site nicht automatisch für die Verwendung der Frontend-Pipeline konvertiert. Das Verschieben dieser Quellen aus dem Client-Bibliotheksordner in den Frontend-Pipeline-Ordner ist eine Aufgabe, die von einem Frontend-Entwickler manuell durchgeführt werden muss.

## Voraussetzungen {#requirements}

AEM kann Ihre vorhandene Site automatisch an die Frontend-Pipeline anpassen. Um diesen Workflow auszuführen, muss Ihre Site [v2 oder neuer der Seitenkomponente der Kernkomponenten](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/wcm-components/page) verwenden.

## Aktivieren der Frontend-Pipeline {#enabling}

{{add-cm-allowlist-frontend-pipeline}}

Die Aktivierung Ihrer Site erfolgt über die Sites-Konsole unter Verwendung der [Site-Leiste](site-rail.md).

1. Melden Sie sich bei AEM an und gehen Sie über **Globale Navigation** > **Sites** zu Ihrer Site.
1. Wählen Sie Ihre Site in der Konsole aus. Wählen Sie den Stamm der Site aus, keine untergeordneten Seiten.
1. Wenn Ihre Site ausgewählt ist, öffnen Sie die [Leistenauswahl](/help/sites-cloud/authoring/basic-handling.md#rail-selector) auf der linken Seite und wählen Sie **Site**.
1. Klicken Sie in der Leiste **Site** auf die Schaltfläche **Frontend-Pipeline aktivieren**.

   ![Frontend-Pipeline aktivieren](/help/sites-cloud/administering/assets/enable-front-end-pipeline.png)

1. AEM fordert Sie zur Bestätigung auf, wobei Sie einen Überblick über die vorzunehmenden Änderungen erhalten. Bestätigen Sie dies, und Ihre Site wird angepasst.

Jetzt kann Ihre Site die Frontend-Pipeline verwenden. Weitere Informationen zur Frontend-Pipeline und zur Verwaltung Ihres Site-Designs finden Sie unter:

* [Verwenden der Site-Leiste zum Verwalten Ihres Site-Designs](site-rail.md)
* [Tour zur schnellen Site-Erstellung](/help/journey-sites/quick-site/overview.md): Diese Dokumentations-Tour gibt Ihnen einen umfassenden Überblick über den Prozess der schnellen Bereitstellung einer Website mithilfe der Frontend-Pipeline und des Tools zur schnellen Site-Erstellung.
* [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end): In diesem Dokument wird die Frontend-Pipeline im Kontext der Full-Stack- und Web-Stufen-Pipelines beschrieben.

## Frontend-Pipeline und benutzerdefinierte Domains {#custom-domains}

Die Frontend-Pipeline kann mit der [benutzerdefinierten Domain-Funktion von Cloud Manager](/help/implementing/cloud-manager/custom-domain-names/introduction.md) verwendet werden. Beachten Sie jedoch die folgenden Anforderungen, wenn Sie beide Funktionen zusammen verwenden.

### Statische Frontend-Dateien {#static-files}

Statische Frontend-Assets, die über die Frontend-Pipeline bereitgestellt werden, werden standardmäßig aus der vordefinierten statischen Adobe-Domain bereitgestellt.

Wenn Sie eine benutzerdefinierte Domain für Frontend-Assets benötigen, können Sie eine benutzerdefinierte Domain auf der Veröffentlichungsebene installieren und die Dispatcher so konfigurieren, dass bestimmte Pfade (wie `/static/`) zum statischen Hosting-Speicherort von Adobe weitergeleitet werden. Für diese Methode müssen Ihre [Dispatcher-Regeln](https://experienceleague.adobe.com/de/docs/experience-manager-dispatcher/using/dispatcher) aktualisiert werden, damit Anfragen für statische Assets ordnungsgemäß weitergeleitet und zwischengespeichert werden können.

Nachdem Sie Ihre benutzerdefinierte Domain und den Dispatcher konfiguriert haben, können Sie AEM so konfigurieren, dass Ihre Frontend-Assets von der statischen Domain bereitgestellt werden.

### Konfiguration {#configuration}

Wie im Abschnitt [Technische Details](#technical-details) beschrieben, werden beim Aktivieren der Funktion „Frontend-Pipeline“ für eine Site die Knoten `SiteConfig` und `HtmlPageItemsConfig` unter `/conf/<site-name>/sling:configs` erstellt.

Wenn Sie die Funktion „Benutzerdefinierte Domains“ von Cloud Manager zusammen mit der Frontend-Pipeline für Status-Assets für Ihre Site verwenden möchten, müssen zu diesen Knoten zusätzliche Eigenschaften hinzugefügt werden.

1. Legen Sie die Eigenschaft `customFrontendPrefix` in `SiteConfig` für die Site fest. 
   1. Navigieren Sie zu `/conf/<site-name>/sling:configs/com.adobe.aem.wcm.site.manager.config.SiteConfig`.
   1. Fügen Sie die Eigenschaft `customFrontendPrefix = "https://your-custom-domain.com/static/"` hinzu oder aktualisieren Sie sie.
1. Dadurch wird der `prefixPath`-Wert der `HtmlPageItemsConfig` mit der benutzerdefinierten Domain aktualisiert.
   1. Navigieren Sie zu `/conf/<site-name>/sling:configs/com.adobe.cq.wcm.core.components.config.HtmlPageItemsConfig`.
   1. Stellen Sie sicher, dass `prefixPath` Ihre benutzerdefinierte Domain wie etwa `prefixPath = "https://your-custom-domain.com/static/<hash>/..."` widerspiegelt.
   * Dieser Wert kann bei Bedarf auch manuell überschrieben werden.
1. Überprüfen Sie Ihr Setup.
   1. Vergewissern Sie sich nach der Bereitstellung, dass die Seiten korrekt auf Design-Artefakte aus der benutzerdefinierten Domain verweisen.
   1. Öffnen Sie die Entwickler-Tools Ihres Browsers und überprüfen Sie die `theme.css` und `theme.js` Dateipfade, um sicherzustellen, dass sie von der richtigen Domain geladen werden.

Seiten für die Site verweisen dann auf Design-Artefakte aus dieser aktualisierten URL. Der Dispatcher leitet dann Anfragen für diese Ressourcen an die statische Domain weiter.

## Best Practices für Frontend-Entwickelnde {#best-practices}

Wenn Sie Frontend-Assets lokal entwickeln und testen müssen, bevor Sie sie über die Frontend-Pipeline bereitstellen, berücksichtigen Sie die folgenden Ansätze:

* Verwenden Sie den [Proxymodus des Site-Design-Builders](https://github.com/adobe/aem-site-theme-builder?tab=readme-ov-file#proxy) um Design-Artefakte lokal zum Testen zu überschreiben.
* Stellen Sie Ihre Design-Dateien manuell über einen lokalen Entwicklungs-Server bereit und aktualisieren Sie `prefixPath` in `HtmlPageItemsConfig` in Übereinstimmung mit der lokalen Server-Adresse.
* Stellen Sie sicher, dass das Browser-Caching während des Tests deaktiviert ist, um Live-Aktualisierungen anzuzeigen.

Weitere Informationen zur lokalen Frontend-Entwicklung finden Sie in der [Dokumentation zum Site-Design-Builder](https://github.com/adobe/aem-site-theme-builder).
