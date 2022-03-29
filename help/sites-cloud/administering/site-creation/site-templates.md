---
title: Site-Vorlagen
description: Erfahren Sie, wie AEM-Site-Vorlagen verwendet werden können, um die Site-Struktur und den anfänglichen Inhalt vorab zu definieren, damit Sie Sites schnell erstellen können.
feature: Administering
role: Admin
exl-id: 42eec922-b02e-4f2c-8107-7336192919c7
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 100%

---

# Site-Vorlagen {#site-templates}

Erfahren Sie, wie AEM-Site-Vorlagen verwendet werden können, um die Site-Struktur und den anfänglichen Inhalt vorab zu definieren, damit Sie Sites schnell erstellen können.

## Übersicht {#overview}

Es ist praktisch, vordefinierte Strukturen zur Verfügung zu haben, um schnell eine auf einem Satz vorhandener Standards basierte Site bereitzustellen. Site-Vorlagen bieten die Möglichkeit, grundlegende Site-Inhalte in einem handlichen und wiederverwendbaren Paket zu kombinieren.

Site-Vorlagen enthalten in der Regel grundlegende Site-Inhalte und -Strukturen sowie Informationen zum Site-Styling, dem sogenannten [Site-Design](site-themes.md), um schnell eine neue Site zu starten. Administratoren wählen [während des Site-Erstellungsprozesses](create-site.md) eine Site-Vorlage aus, auf der die Site basieren soll.

Vorlagen sind leistungsstark, da sie wiederverwendbar und anpassbar sind. Da in Ihrer AEM-Installation mehrere Vorlagen zur Verfügung stehen, können Sie verschiedene Sites erstellen, um unterschiedlichen geschäftlichen Anforderungen gerecht zu werden.

>[!NOTE]
>
>AEM-Site-Vorlagen sollten nicht mit [Seitenvorlagen verwechselt werden.](/help/sites-cloud/authoring/features/templates.md) Site-Vorlagen definieren die Gesamtstruktur einer Site. Eine Seitenvorlage definiert die Struktur und den anfänglichen Inhalt einer einzelnen Seite.
>
>AEM-Site-Vorlagen sollten nicht mit [AEM Site-Designs verwechselt werden.](site-themes.md) AEM-Site-Designs enthalten nur die Styling-Informationen für eine AEM-Site. AEM-Site-Vorlagen definieren die Site-Struktur und den anfänglichen Inhalt sowie ein AEM-Site-Design, um [eine schnelle Site-Erstellung](create-site.md) zu ermöglichen.

## Hinzufügen einer Site-Vorlage zu AEM {#adding}

Sie können mehrere Vorlagen zu AEM hinzufügen, die dann verwendet werden, um [Sites zu erstellen](create-site.md).

1. Melden Sie sich bei Ihrer AEM-Authoring-Umgebung an und navigieren Sie zur Sites-Konsole

   * `https://<your-author-environment>.adobeaemcloud.com/sites.html/content`

1. Tippen oder klicken Sie oben rechts im Bildschirm auf **Erstellen** und wählen Sie aus dem Dropdown-Menü **Site aus Vorlage**.

   ![Erstellen einer Site aus einer Vorlage](../assets/create-site-from-template.png)

1. Tippen oder klicken Sie im Assistenten oben in der linken Spalte auf **Importieren**.

   ![Assistent zur Site-Erstellung](../assets/site-creation-wizard.png)

1. Finden Sie im Datei-Browser die gewünschte Vorlage und tippen oder klicken Sie auf **Hochladen**.

1. Nach dem Hochladen wird sie in der Liste der verfügbaren Vorlagen angezeigt.

Ihre Vorlage wurde hochgeladen und kann verwendet werden, um [neue Sites zu erstellen](create-site.md).

Bei der Auswahl einer vorhandenen Vorlage werden Informationen über die Vorlage in der rechten Spalte angezeigt.

![Auswählen einer Vorlage](../assets/select-site-template.png)

## Site-Vorlagenstruktur {#structure}

Site-Vorlagen sind schlicht Pakete mit einer logischen Struktur, die den Zweck des Paketinhalts klar widerspiegelt. Eine Site-Vorlage weist die folgende Struktur auf.

* `files`: Ordner mit dem Benutzeroberflächen-Kit, einer XD-Datei und möglicherweise anderen Dateien
* `previews`: Ordner mit Screenshots der Site-Vorlage
* `site`: Inhaltspaket der Inhalte, die für jede aus dieser Vorlage erstellte Site kopiert werden, z. B. Seitenvorlagen, Seiten usw.
* `theme`: Quellen des [Site-Designs](site-themes.md), um das Aussehen der Site zu ändern, einschließlich CSS, JavaScript usw.

## Standard-Site-Vorlage {#standard-site-template}

Adobe bietet eine Best-Practices-Referenzvorlage, die Sie als Grundlage für die Erstellung Ihrer eigenen Vorlagen verwenden können. [Die Standard-Site-Vorlage ist auf GitHub verfügbar.](https://github.com/adobe/aem-site-template-standard)

[Die neueste Version der Standard-Site-Vorlage](https://github.com/adobe/aem-site-template-standard/releases) kann heruntergeladen werden und direkt für die [Erstellung neuer Sites](create-site.md) verwendet werden.

## Entwickeln von Site-Vorlagen {#developing-templates}

Adobe stellt AEM Site Template Builder als Satz von Skripten zur Erstellung neuer Site-Vorlagen bereit.

[AEM Site Template Builder ist zusammen mit der Nutzungsdokumentation auf GitHub verfügbar.](https://github.com/adobe/aem-site-template-builder) Für die Anpassung des [Site-Designs](site-themes.md) wird Frontend-Entwicklererfahrung und für die Anpassung der Site-Struktur und deren Inhalten wird AEM-Entwicklerwissen benötigt.
