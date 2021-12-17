---
title: Creating a Site
description: Erfahren Sie, wie Sie AEM verwenden, um eine Site mithilfe von Site-Vorlagen zu erstellen, um den Stil und die Struktur Ihrer Site zu definieren.
feature: Administering
role: Admin
source-git-commit: 5e1a89743c5ac36635a139ada690849507813c30
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 1%

---


# Creating a Site {#creating-site}

Erfahren Sie, wie Sie mit AEM Site-Vorlagen erstellen, um den Stil und die Struktur Ihrer Site zu definieren.

## Übersicht {#overview}

Bevor Inhaltsautoren Seiten mit Inhalten erstellen können, muss die Site zuerst erstellt werden. This is generally performed by an AEM administrator who defines the initial structure of the site. Die Verwendung von Site-Vorlagen ermöglicht eine schnelle und flexible Erstellung von Websites.

Mit dem Tool AEM schnelle Site-Erstellung können Nicht-Entwickler mithilfe von Site-Vorlagen schnell eine neue Site von Grund auf neu erstellen.

Once created, the Quick Site Creation tool also enables fast customization of the theme and styling of the AEM site (JavaScript, CSS, and static resources). Dadurch kann der Frontend-Entwickler, der keine Kenntnisse über AEM benötigt, getrennt und parallel zu den Erstellern von Inhalten arbeiten. The AEM administrator simply downloads the site theme and provides it to the front-end developer who customizes it using their favorite tools and then commits the changes to the AEM code repository, which is then deployed.

Dieses Dokument konzentriert sich auf die Erstellung von Websites mithilfe des Tools für die schnelle Site-Erstellung. Wenn Sie einen Überblick über den Site-Erstellungs- und Anpassungs-Workflow erhalten möchten, lesen Sie bitte den Abschnitt [Journey zur AEM SchnellSite-Erstellung](/help/journey-sites/quick-site/overview.md)

## Planen der Site-Struktur {#structure}

Nehmen Sie sich Zeit, um den Zweck Ihrer Site und die geplanten Inhalte rechtzeitig im Voraus zu prüfen. Dadurch wird bestimmt, wie Sie die Struktur der Site entwerfen. Eine gute Site-Struktur unterstützt die einfache Navigation und Inhaltssuche für Ihre Site-Besucher sowie verschiedene AEM Funktionen wie [Verwaltung und Übersetzung mehrerer Websites.](/help/sites-cloud/administering/msm-and-translation.md)

>[!TIP]
>
>[Die WKND-Referenz-Website](https://wknd.site) bietet eine Best-Practice-Implementierung einer voll funktionsfähigen Website mit einer Marke für Outdoor-Erlebnisse. Erkunden Sie es, um zu sehen, wie eine gut AEM Site strukturiert ist.

## Site-Vorlagen {#site-templates}

Because site structure is so important to the success of a site, it is convenient to have predefined structures available to quickly deploy a new site based on a set of existing standards. Site templates are a way to combine basic site content into a convenient and reusable package.

Site-Vorlagen enthalten in der Regel grundlegende Site-Inhalte und -Struktur sowie Site-Styling-Informationen, um neue Sites schnell zu starten. Vorlagen sind leistungsstark, da sie wiederverwendbar und anpassbar sind. Da in Ihrer AEM mehrere Vorlagen zur Verfügung stehen, können Sie verschiedene Sites erstellen, um unterschiedlichen geschäftlichen Anforderungen gerecht zu werden.

>[!TIP]
>
>For further detail on site templates, please review the [Site Templates](site-templates.md) article.

>[!NOTE]
>
>Die Site-Vorlage darf nicht mit Seitenvorlagen verwechselt werden. Site templates define the overall structure of a site. Eine Seitenvorlage definiert die Struktur und den anfänglichen Inhalt einer einzelnen Seite.

## Erstellen einer Site {#create-site}

Die Verwendung einer Vorlage zum Erstellen einer Site ist einfach.

1. Sign into your AEM authoring environment and navigate to the Sites console

   * `https://<your-author-environment>.adobeaemcloud.com/sites.html/content`

1. Tap or click **Create** at the top-right of the screen and from the drop-down menu select **Site from template**.

   ![Erstellen einer Site aus einer Vorlage](../assets/create-site-from-template.png)

1. Tippen oder klicken Sie im Assistenten Site erstellen auf eine vorhandene Vorlage im linken Bereich oder auf **Import** oben in der linken Spalte, um eine neue Vorlage zu importieren.

   ![Site creation wizard](../assets/site-creation-wizard.png)

   1. Wenn Sie sich für den Import entschieden haben, suchen Sie im Dateibrowser die gewünschte Vorlage und tippen oder klicken Sie auf **Hochladen**.

   1. Nach dem Hochladen wird er in der Liste der verfügbaren Vorlagen angezeigt.

1. When selecting a template, it reveals information about the template in the right column. Tippen oder klicken Sie bei ausgewählter Vorlage auf **Nächste**.

   ![Wählen Sie eine Vorlage aus](../assets/select-site-template.png)

1. Geben Sie einen Titel für Ihre Site an. Ein Site-Name kann angegeben werden oder wird aus dem Titel generiert, wenn er weggelassen wird.

   * The site title appears in the browsers title bar.
   * The site name becomes part of the URL.
   * The site name must comply with [AEM&#39;s page naming conventions.](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#page-name-restrictions-and-best-practices)

1. Tippen oder klicken Sie auf **Erstellen** und die Site aus der Site-Vorlage erstellt wird.

   ![Details der neuen Site](../assets/create-site-details.png)

1. Tippen oder klicken Sie im angezeigten Bestätigungsdialogfeld auf **Fertig**.

   ![Dialogfeld &quot;Erfolg&quot;](../assets/success.png)

1. In the sites console, the new site is visible and can be navigated to explore its basic structure as defined by the template.

   ![Neue Site-Struktur](../assets/new-site.png)

Content authors can now begin authoring!

## Site-Anpassung {#site-customization}

Wenn Ihre Site über die verfügbaren Vorlagen hinaus angepasst werden muss, haben Sie eine Reihe von Optionen.

* Wenn die Site-Struktur oder der anfängliche Inhalt angepasst werden muss, [Die Site-Vorlage kann an Ihre Anforderungen angepasst werden.](site-templates.md)
* Wenn der Site-Stil angepasst werden muss, [Das Site-Design kann heruntergeladen und angepasst werden.](/help/journey-sites/quick-site/overview.md)
* Wenn die Site-Funktionalität angepasst werden muss, [Die Site kann vollständig angepasst werden.](/help/implementing/developing/introduction/develop-wknd-tutorial.md)

Any customization should be undertaken with the support of a development team.
