---
title: Erstellen einer Site
description: Erfahren Sie, wie Sie AEM verwenden, um eine Site mithilfe von Site-Vorlagen zu erstellen, um den Stil und die Struktur Ihrer Site zu definieren.
feature: Administering
role: Admin
exl-id: 9c71c167-2934-4210-abd9-ab085b36593b
solution: Experience Manager Sites
source-git-commit: 4d45e7ef626ad0b46f5323263cca791b14f9732f
workflow-type: ht
source-wordcount: '726'
ht-degree: 100%

---


# Erstellen einer Site {#creating-site}

Erfahren Sie, wie Sie mit AEM eine Site mithilfe von Site-Vorlagen erstellen, um den Stil und die Struktur Ihrer Site zu definieren.

## Überblick {#overview}

Bevor Inhaltsautoren Seiten mit Inhalten erstellen können, muss die Site zuerst erstellt werden. Dies wird im Allgemeinen von einem AEM-Administrator durchgeführt, der die anfängliche Struktur der Site definiert. Die Verwendung von Site-Vorlagen ermöglicht Benutzenden ohne Entwicklungs-Know-how eine schnelle und flexible Erstellung von Sites.

## Planen der Site-Struktur {#structure}

Nehmen Sie sich Zeit, um den Zweck Ihrer Site und die geplanten Inhalte rechtzeitig im Voraus zu prüfen. Dadurch wird bestimmt, wie Sie die Struktur der Site entwerfen. Eine gute Site-Struktur unterstützt die einfache Navigation und Inhaltssuche für die Besucherinnen und Besucher Ihrer Site sowie verschiedene AEM-Funktionen wie [Multisite-Management und Übersetzung](/help/sites-cloud/administering/msm-and-translation.md).

## Site-Vorlagen {#site-templates}

Da die Site-Struktur für den Erfolg einer Site so wichtig ist, ist es praktisch, vordefinierte Strukturen zur Verfügung zu haben, um schnell eine neue Site auf der Grundlage einer Reihe vorhandener Standards bereitzustellen. Site-Vorlagen bieten die Möglichkeit, grundlegende Site-Inhalte in einem handlichen und wiederverwendbaren Paket zu kombinieren.

Site-Vorlagen enthalten in der Regel grundlegende Site-Inhalte und -Struktur sowie Site-Styling-Informationen, um neue Sites schnell live schalten zu können. Vorlagen sind leistungsstark, da sie wiederverwendbar und anpassbar sind. Da in Ihrer AEM-Installation mehrere Vorlagen zur Verfügung stehen, können Sie verschiedene Sites erstellen, um unterschiedlichen geschäftlichen Anforderungen gerecht zu werden.

>[!TIP]
>
>Weitere Informationen zu Site-Vorlagen finden Sie unter [Site-Vorlagen](site-templates.md).

>[!NOTE]
>
>Verwechseln Sie Site-Vorlagen nicht mit [Seitenvorlagen. ](/help/sites-cloud/authoring/page-editor/templates.md) Site-Vorlagen definieren die Gesamtstruktur einer Site. Eine Seitenvorlage definiert die Struktur und den anfänglichen Inhalt einer einzelnen Seite.

### Von Adobe bereitgestellte Site-Vorlagen {#adobe-templates}

{{adobe-templates}}

## Erstellen einer Site {#create-site}

Die Verwendung einer Vorlage zum Erstellen einer Site ist einfach.

1. Melden Sie sich bei Ihrer AEM-Authoring-Umgebung an und navigieren Sie zur Sites-Konsole

   * `https://<your-author-environment>.adobeaemcloud.com/sites.html/content`

1. Wählen Sie oben rechts im Bildschirm die Option **Erstellen** und dann aus dem Dropdown-Menü die Option **Site aus Vorlage** aus.

   ![Erstellen einer Site aus einer Vorlage](../assets/create-site-from-template.png)

1. Wählen Sie im Assistenten zur Site-Erstellung über das linke Bedienfeld eine vorhandene Vorlage oder oben in der linken Spalte die Option **Importieren** aus, um eine neue Vorlage zu importieren.

   ![Assistent zur Site-Erstellung](../assets/site-creation-wizard.png)

   1. Wenn Sie sich für den Import entschieden haben, suchen Sie im Datei-Browser die gewünschte Vorlage und wählen Sie **Hochladen** aus.

   1. Nach dem Hochladen wird sie in der Liste der verfügbaren Vorlagen angezeigt.

1. Bei der Auswahl einer Vorlage werden Informationen zur Vorlage in der rechten Spalte angezeigt. Wählen Sie bei ausgewählter Vorlage die Option **Weiter** aus.

   ![Auswählen einer Vorlage](../assets/select-site-template.png)

1. Geben Sie einen Titel für die Site ein. Der Name der Site kann angegeben oder aus dem Titel generiert werden, falls er weggelassen wird.

   * Der Titel der Site wird in der Titelleiste des Browsers angezeigt.
   * Der Site-Name wird Teil der URL.
   * Der Site-Name muss den [AEM-Konventionen zur Seitenbenennung](/help/sites-cloud/authoring/sites-console/organizing-pages.md#page-name-restrictions-and-best-practices) entsprechen.

1. Geben Sie die von der Site-Vorlage geforderten zusätzlichen Site-Details an.

   * Verschiedene Vorlagen erfordern möglicherweise zusätzliche Details.
   * Bei Vorlagen für [Edge Delivery Services-Projekte](https://www.aem.live/developer/ue-tutorial) ist beispielsweise das GitHub-Repository Ihres Projekts erforderlich.

1. Wählen Sie **Erstellen** aus. Die Site wird daraufhin anhand der Site-Vorlage erstellt.

   ![Details der neuen Site](../assets/create-site-details.png)

1. Wählen Sie im angezeigten Bestätigungsdialogfeld **Fertig** aus.

   ![Dialogfeld „Erfolg“](../assets/success.png)

1. In der Sites-Konsole ist die neue Site sichtbar. Sie kann zur Untersuchung ihrer grundlegenden Struktur, wie von der Vorlage definiert, navigiert werden.

   ![Neue Site-Struktur](../assets/new-site.png)

Inhaltsautoren können jetzt mit der Bearbeitung beginnen!

## Site-Anpassung {#site-customization}

Vorlagen sind hilfreich, um die grundlegende Struktur und den Stil einer Site schnell einzurichten. Die meisten Projekte erfordern jedoch einige zusätzliche Stile und Anpassungen. Site-Vorlagen helfen dabei, die Formatierung der Site zu entkoppeln. Frontend-Entwicklerinnen und -Entwickler benötigen keine Kenntnisse von AEM zur Gestaltung der Site und können unabhängig und parallel mit den Inhaltserstellenden arbeiten. Je nach Art des Projekts kann dies auf zweierlei Weise erfolgen.

* Bei Projekten mit AEM-Seitenerstellung mit dem universellen Editor und Bereitstellung über [Edge Delivery](/help/edge/overview.md) erfolgt die gesamte Formatierung im GitHub-Projekt.
   * Weitere Informationen finden Sie im Dokument [Erste Schritte – Entwickler-Tutorial für den universellen Editor](https://www.aem.live/developer/ue-tutorial).
* Bei Projekten mit traditioneller AEM-Seitenerstellung und Bereitstellung über [Veröffentlichungsbereitstellung](/help/sites-cloud/authoring/author-publish.md) lädt der AEM-Admin ganz einfach das Site-Design herunter und stellt es den Frontend-Entwickelnden bereit, die es mit ihren bevorzugten Tools anpassen und dann die Änderungen an das AEM Code-Repository übergeben, das dann bereitgestellt wird.
   * Weitere Informationen finden Sie im Dokument [Schnelle Erstellung von AEM-Sites](/help/journey-sites/quick-site/overview.md).
