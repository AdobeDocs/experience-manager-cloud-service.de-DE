---
title: Site-Vorlagen
description: Erfahren Sie, wie AEM Site-Vorlagen verwendet werden können, um die Site-Struktur und den anfänglichen Inhalt vorab zu definieren, damit Sie schnell Sites erstellen können.
feature: Administering
role: Admin
exl-id: 42eec922-b02e-4f2c-8107-7336192919c7
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 1%

---

# Site-Vorlagen {#site-templates}

Erfahren Sie, wie AEM Site-Vorlagen verwendet werden können, um die Site-Struktur und den anfänglichen Inhalt vorab zu definieren, damit Sie schnell Sites erstellen können.

## Übersicht {#overview}

Es ist praktisch, vordefinierte Strukturen zur Verfügung zu haben, um schnell eine neue Site basierend auf einem Satz vorhandener Standards bereitzustellen. Site-Vorlagen bieten die Möglichkeit, grundlegende Site-Inhalte in einem bequemen und wiederverwendbaren Paket zu kombinieren.

Site-Vorlagen enthalten in der Regel grundlegende Site-Inhalte und -Strukturen sowie Informationen zum Site-Stil, die als [Site-Design,](site-themes.md) um eine neue Site schnell zu starten. Administratoren wählen eine Site-Vorlage aus, auf der die Site basieren soll [während des Site-Erstellungsprozesses.](create-site.md)

Vorlagen sind leistungsstark, da sie wiederverwendbar und anpassbar sind. Da in Ihrer AEM mehrere Vorlagen zur Verfügung stehen, können Sie verschiedene Sites erstellen, um unterschiedlichen geschäftlichen Anforderungen gerecht zu werden.

>[!NOTE]
>
>AEM Site-Vorlagen sollten nicht mit [Seitenvorlagen.](/help/sites-cloud/authoring/features/templates.md) Site-Vorlagen definieren die Gesamtstruktur einer Site. Eine Seitenvorlage definiert die Struktur und den anfänglichen Inhalt einer einzelnen Seite.
>
>AEM Site-Vorlagen sollten nicht mit [AEM Site-Designs.](site-themes.md) AEM Site-Designs enthalten nur die Styling-Informationen für eine AEM Site. AEM Site-Vorlagen definieren die Site-Struktur und den anfänglichen Inhalt sowie ein AEM Site-Design, um [schnelle Site-Erstellung.](create-site.md)

## Hinzufügen einer Site-Vorlage zu AEM {#adding}

Sie können AEM mehrere Vorlagen hinzufügen, die dann zur [Sites erstellen.](create-site.md)

1. Melden Sie sich bei Ihrer AEM Authoring-Umgebung an und navigieren Sie zur Sites-Konsole

   * `https://<your-author-environment>.adobeaemcloud.com/sites.html/content`

1. Tippen oder klicken Sie auf **Erstellen** oben rechts im Bildschirm und aus dem Dropdown-Menü wählen Sie **Site aus Vorlage**.

   ![Erstellen einer Site aus einer Vorlage](../assets/create-site-from-template.png)

1. Tippen oder klicken Sie im Assistenten &quot;Site erstellen&quot;auf **Import** oben in der linken Spalte.

   ![Assistent zur Site-Erstellung](../assets/site-creation-wizard.png)

1. Suchen Sie im Dateibrowser die gewünschte Vorlage und tippen oder klicken Sie auf **Hochladen**.

1. Nach dem Hochladen wird er in der Liste der verfügbaren Vorlagen angezeigt.

Ihre Vorlage wurde hochgeladen und kann mit [neue Sites erstellen.](create-site.md)

Bei der Auswahl einer vorhandenen Vorlage werden Informationen über die Vorlage in der rechten Spalte angezeigt.

![Wählen Sie eine Vorlage aus](../assets/select-site-template.png)

## Site-Vorlagenstruktur {#structure}

Site-Vorlagen sind einfach Pakete mit einer logischen Struktur, die den Zweck des Paketinhalts klar widerspiegelt. Eine Site-Vorlage weist die folgende Struktur auf.

* `files`: Ordner mit dem Benutzeroberflächen-Kit, XD und möglicherweise anderen Dateien
* `previews`: Ordner mit Screenshots der Site-Vorlage
* `site`: Inhaltspaket des Inhalts, der für jede aus dieser Vorlage erstellte Site kopiert wird, z. B. Seitenvorlagen, Seiten usw.
* `theme`: Quellen der [Site-Design](site-themes.md) , um zu ändern, wie die Site aussieht, einschließlich CSS, JavaScript usw.

## Standardsite-Vorlage {#standard-site-template}

Adobe bietet eine Best-Practice-Referenzvorlage, die Sie als Grundlage für die Erstellung Ihrer eigenen Vorlagen verwenden können. [Die Standard-Site-Vorlage ist auf GitHub verfügbar.](https://github.com/adobe/aem-site-template-standard)

[Die neueste Version der Standard-Site-Vorlage](https://github.com/adobe/aem-site-template-standard/releases) herunterladen und direkt für [Erstellen neuer Sites.](create-site.md)

## Entwickeln von Site-Vorlagen {#developing-templates}

Adobe stellt und AEM Site-Vorlagen-Builder als Satz von Skripten zum Erstellen neuer Site-Vorlagen bereit.

[Der AEM Site Template Builder ist zusammen mit der Nutzungsdokumentation auf GitHub verfügbar.](https://github.com/adobe/aem-site-template-builder) Für die Anpassung der [Site-Design](site-themes.md) und AEM Entwicklerwissen ist für die Anpassung der Site-Struktur und des Inhalts erforderlich.
