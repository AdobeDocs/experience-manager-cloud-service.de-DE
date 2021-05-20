---
title: Personalisierung und Content-Targeting
description: Erfahren Sie, wie AEM personalisierte Inhalte erstellen kann
exl-id: b9b5dbf6-d491-48a6-99b1-19bc1b651b8c
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 100%

---

# Personalisierung und Content-Targeting {#personalization}

## Personalisierung und Content-Targeting {#personalization-and-content-targeting}

AEM stellt eine Reihe von Werkzeugen zur Bearbeitung von Inhalten für eine bestimmte Zielgruppe und die Darstellung personalisierter Erlebnisse bereit.

## Targeting-Modus  {#targeting-mode}

[Verfassen Sie zielgerichtete Inhalte](/help/sites-cloud/authoring/personalization/targeted-content.md) im Targeting-Modus von AEM. Der Targeting-Modus und die Targeting-Komponente sind wichtige Werkzeuge für die Erstellung von Erlebnisinhalten für Ihre Marketingaktivitäten.

## Aktivitäten  {#activities}

Mit Aktivitäten lassen sich Ihre Marketingprojekte definieren und organisieren. Teil der Aktivitäten sind die gewünschten Zielgruppen sowie der Zeitraum, in dem das Targeting durchgeführt wird.

Ihr Produktkatalog kann z. B. Teaser enthalten, die die Aufmerksamkeit auf Produkte der aktuellen Saison lenken sollen. In der Aktivität „Sommersport“ sind die Marketing-Segmente definiert, die während der Sommermonate gezielt angesprochen werden sollen.

Mit Aktivitäten wird zudem auch die [Targeting-Engine](#targeting-engine) bestimmt, die Ihre Seiten verwenden.

Mit der [Aktivitätskonsole](/help/sites-cloud/authoring/personalization/activities.md) können Sie die Aktivitäten Ihrer Marken erstellen und verwalten. Sie können auch Aktivitäten erstellen, während Sie [zielgerichtete Inhalte erstellen](/help/sites-cloud/authoring/personalization/targeted-content.md).

## Erlebnisse {#experiences}

Legen Sie für jede Aktivität ein oder mehr Erlebnisse fest, in denen die gewünschten Zielgruppen identifiziert sind. Mit AEM verfügen Sie über die Möglichkeit, die Inhalte jedes Erlebnisses gezielt zu steuern.

Zielgruppen basieren auf Marketingsegmenten, die entweder in AEM oder Adobe Target erstellt werden. Öffnet ein Besucher eine Webseite, bestimmt die Seitenlogik die Zielgruppe, in die er fällt, und zeigt die für diese Zielgruppe erstellten Inhalte an.

Mit einer Aktivität können beispielsweise Erlebnisse für zwei verschiedene Zielgruppen festgelegt werden: Frauen über 30 und Frauen unter 30. Die Damenabteilung einer Website könnte für jedes Erlebnis verschiedene Produkte anzeigen.

Die Erlebnisse der Aktivitäten werden von Ihnen festgelegt. Sie können hierzu die [Aktivitätskonsole](/help/sites-cloud/authoring/personalization/activities.md#adding-editing-an-activity-using-the-activities-console) oder den [Targeting-Modus](/help/sites-cloud/authoring/personalization/targeted-content.md#adding-and-removing-experiences-using-targeting-mode) verwenden und Aktivitäten Erlebnisse hinzufügen.

## Angebote   {#offers}

Angebote sind Inhalte, die an einem Ort auf einer Seite angezeigt werden, die für ein Erlebnis festgelegt wurde. Verwenden Sie für verschiedene Erlebnisse verschiedene Angebote, um Inhalte optimal auf Ihre Zielgruppen zuzuschneiden.

Beispielsweise könnte die Damenabteilung einer Beispiel-Website Angebote als das Teaser-Bild verwenden, das oben auf der Seite eingeblendet wird. Für Erlebnisse für Frauen über 30 werden andere Angebote eingesetzt als für Frauen unter 30.

Mit der [Angebotskonsole](/help/sites-cloud/authoring/personalization/offers.md) lassen sich Angebote erstellen, die für mehrere Erlebnisse eingesetzt werden sollen. Erstellen Sie Einmal-Angebote oder fügen Sie Angebote aus einer Angebotsbibliothek hinzu, wenn Sie [zielgerichtete Inhalte erstellen](/help/sites-cloud/authoring/personalization/targeted-content.md).

## Targeting-Engine    {#targeting-engine}

Die Targeting-Engine ist der Mechanismus, der die Logik hinter zielgerichteten Inhalten darstellt. [Aktivitäten](/help/sites-cloud/authoring/personalization/activities.md) sind so konfiguriert, dass eine von zwei verfügbaren Targeting-Engines verwendet wird: AEM oder Adobe Target.

### AEM {#aem}

AEM verfügt über eine integrierte Targeting-Engine, mit der Seitenanfragen verarbeitet und anzuzeigende Inhalte bestimmt werden. Bei der Verwendung der AEM Targeting-Engine sind Sie auf den Einsatz von Segmenten beschränkt, die in AEM erstellt wurden und die Zielgruppen Ihrer Erlebnisse festlegen.

### Adobe Target {#adobe-target}

Mit der Adobe Target-Targeting-Engine werden von Seitenbesuchen gesammelte Informationen in Adobe Target verfolgt.

* Bei der Verwendung dieser Targeting-Engine setzen Sie Segmente ein, die Sie aus Adobe Target importieren und die die Zielgruppen Ihrer Erlebnisse bestimmen.
* Aktivitäten, die mit der Adobe Target-Engine bereitgestellt werden, werden [mit Target synchronisiert](/help/sites-cloud/authoring/personalization/activities.md#synchronizing-activities-with-adobe-target).

Sie können diese Engine verwenden, wenn Sie über eine Integration mit Adobe Target verfügen. <!--You can use this engine when you have [integrated with Adobe Target](/help/sites-administering/opt-in.md).-->
