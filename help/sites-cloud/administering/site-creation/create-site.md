---
title: Erstellen einer Site
description: Erfahren Sie, wie Sie AEM verwenden, um eine Site mithilfe von Site-Vorlagen zu erstellen, um den Stil und die Struktur Ihrer Site zu definieren.
feature: Administering
role: Admin
exl-id: 9c71c167-2934-4210-abd9-ab085b36593b
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 100%

---

# Erstellen einer Site {#creating-site}

Erfahren Sie, wie Sie mit AEM eine Site mithilfe von Site-Vorlagen erstellen, um den Stil und die Struktur Ihrer Site zu definieren.

## Übersicht {#overview}

Bevor Inhaltsautoren Seiten mit Inhalten erstellen können, muss die Site zuerst erstellt werden. Dies wird im Allgemeinen von einem AEM-Administrator durchgeführt, der die anfängliche Struktur der Site definiert. Die Verwendung von Site-Vorlagen ermöglicht eine schnelle und flexible Erstellung von Sites.

Mit dem Tool AEM Quick Site Creation können Nicht-Entwickler mithilfe von Site-Vorlagen schnell eine neue Site von Grund auf erstellen.

Nach der Erstellung ermöglicht das Tool Quick Site Creation auch eine schnelle Anpassung des Designs und des Stils der AEM-Site (JavaScript, CSS und statische Ressourcen). Dadurch kann der Frontend-Entwickler, der keine Kenntnisse über AEM benötigt, getrennt und parallel zu den Erstellern von Inhalten arbeiten. Der AEM-Administrator lädt ganz einfach das Site-Design herunter und stellt es dem Frontend-Entwickler bereit, der es mithilfe seiner bevorzugten Tools anpasst und dann die Änderungen an das AEM Code-Repository übergibt, das dann bereitgestellt wird.

Dieses Dokument konzentriert sich auf die Erstellung von Sites mithilfe des Tools Quick Site Creation. Wenn Sie einen Überblick über den Site-Erstellungs- und Anpassungs-Workflow erhalten möchten, lesen Sie den Abschnitt [Tour zu AEM Quick Site Creation](/help/journey-sites/quick-site/overview.md)

## Planen der Site-Struktur {#structure}

Nehmen Sie sich Zeit, um den Zweck Ihrer Site und die geplanten Inhalte rechtzeitig im Voraus zu prüfen. Dadurch wird bestimmt, wie Sie die Struktur der Site entwerfen. Eine gute Site-Struktur unterstützt die einfache Navigation und Inhaltssuche für Ihre Site-Besucher sowie verschiedene AEM-Funktionen wie [Multisite-Management und Übersetzung](/help/sites-cloud/administering/msm-and-translation.md).

>[!TIP]
>
>[Die WKND-Referenz-Website](https://wknd.site) bietet eine Best-Practice-Implementierung einer voll funktionsfähigen Website für eine Outdoor-Marke. Erkunden Sie sie, um zu sehen, wie eine gut aufgebaute AEM-Site strukturiert ist.

## Site-Vorlagen {#site-templates}

Da die Site-Struktur für den Erfolg einer Site so wichtig ist, ist es praktisch, vordefinierte Strukturen zur Verfügung zu haben, um schnell eine neue Site auf der Grundlage einer Reihe vorhandener Standards bereitzustellen. Site-Vorlagen bieten die Möglichkeit, grundlegende Site-Inhalte in einem handlichen und wiederverwendbaren Paket zu kombinieren.

Site-Vorlagen enthalten in der Regel grundlegende Site-Inhalte und -Struktur sowie Site-Styling-Informationen, um neue Sites schnell live zu schalten. Vorlagen sind leistungsstark, da sie wiederverwendbar und anpassbar sind. Da in Ihrer AEM-Installation mehrere Vorlagen zur Verfügung stehen, können Sie verschiedene Sites erstellen, um unterschiedlichen geschäftlichen Anforderungen gerecht zu werden.

>[!TIP]
>
>Weitere Informationen zu Site-Vorlagen finden Sie im Abschnitt [Site-Vorlagen](site-templates.md).

>[!NOTE]
>
>Die Site-Vorlage darf nicht mit Seitenvorlagen verwechselt werden. Site-Vorlagen definieren die Gesamtstruktur einer Site. Eine Seitenvorlage definiert die Struktur und den anfänglichen Inhalt einer einzelnen Seite.

## Erstellen einer Site {#create-site}

Die Verwendung einer Vorlage zum Erstellen einer Site ist einfach.

1. Melden Sie sich bei Ihrer AEM-Authoring-Umgebung an und navigieren Sie zur Sites-Konsole

   * `https://<your-author-environment>.adobeaemcloud.com/sites.html/content`

1. Tippen oder klicken Sie oben rechts im Bildschirm auf **Erstellen** und wählen Sie aus dem Dropdown-Menü **Site aus Vorlage**.

   ![Erstellen einer Site aus einer Vorlage](../assets/create-site-from-template.png)

1. Tippen oder klicken Sie im Seitenerstellungsassistenten auf eine vorhandene Vorlage im linken Bereich oder auf **Importieren** oben in der linken Spalte, um eine neue Vorlage zu importieren.

   ![Assistent zur Site-Erstellung](../assets/site-creation-wizard.png)

   1. Wenn Sie sich für den Import entschieden haben, suchen Sie im Datei-Browser die gewünschte Vorlage und tippen oder klicken Sie auf **Hochladen**.

   1. Nach dem Hochladen wird sie in der Liste der verfügbaren Vorlagen angezeigt.

1. Bei der Auswahl einer Vorlage werden Informationen zur Vorlage in der rechten Spalte angezeigt. Tippen oder klicken Sie bei ausgewählter Vorlage auf **Weiter**.

   ![Vorlage auswählen](../assets/select-site-template.png)

1. Geben Sie einen Titel für die Site ein. Ein Site-Name kann angegeben werden oder wird aus dem Titel generiert, wenn er weggelassen wird.

   * Der Titel der Site wird in der Titelleiste des Browsers angezeigt.
   * Der Site-Name wird Teil der URL.
   * Der Site-Name muss den [Konventionen zur Seitenbenennung von AEM](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#page-name-restrictions-and-best-practices) entsprechen.

1. Tippen oder klicken Sie auf **Erstellen**, um die Site aus der Site-Vorlage zu erstellen.

   ![Details der neuen Site](../assets/create-site-details.png)

1. Tippen oder klicken Sie im angezeigten Bestätigungsdialogfeld auf **Fertig**.

   ![Dialogfeld „Erfolg“](../assets/success.png)

1. In der Sites-Konsole ist die neue Site sichtbar. Sie kann zur Untersuchung ihrer grundlegenden Struktur, wie von der Vorlage definiert, navigiert werden.

   ![Neue Site-Struktur](../assets/new-site.png)

Inhaltsautoren können jetzt mit der Bearbeitung beginnen!

## Site-Anpassung {#site-customization}

Wenn Ihre Site über die verfügbaren Vorlagen hinaus angepasst werden muss, haben Sie eine Reihe von Optionen.

* Wenn die Site-Struktur oder der anfängliche Inhalt angepasst werden muss, [kann die Site-Vorlage an Ihre Anforderungen angepasst werden](site-templates.md).
* Wenn der Site-Stil angepasst werden muss, [kann das Site-Design heruntergeladen und angepasst werden](/help/journey-sites/quick-site/overview.md).
* Wenn die Site-Funktionalität angepasst werden muss, [kann die Site vollständig angepasst werden](/help/implementing/developing/introduction/develop-wknd-tutorial.md).

Jede Anpassung sollte mit Unterstützung eines Entwicklungs-Teams vorgenommen werden.
