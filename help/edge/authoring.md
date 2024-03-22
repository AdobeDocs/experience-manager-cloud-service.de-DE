---
title: Erstellen von Inhalten für Edge Delivery Services
description: Erfahren Sie, wie Content-Authoring mit Edge Delivery Services funktioniert und wie Sie AEM-Inhalte mit Edge Delivery Services erstellen.
feature: Edge Delivery Services
exl-id: 963ff71a-8176-4d9d-8240-dc429405d139
source-git-commit: d91254b52c257a3758da200a2c74b736ca457884
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 90%

---

# Erstellen von Inhalten für Edge Delivery Services {#authoring-edge}

Mit Edge Delivery Services ist das Authoring einfach, schnell und flexibel. Sie haben zwei Optionen zum Erstellen von Inhalten für Edge Delivery Services:

* [Dokumentenbasiertes Authoring](#document-based) - wie Microsoft Word- oder Google-Dokumente
* [Universal Editor](#universal-editor) – Eine moderne UI für die Bearbeitung von Inhalten in AEM

## Dokumentenbasiertes Authoring  {#document-based}

Bei der dokumentbasierten Bearbeitung können Sie mit verschiedenen Quellen wie Microsoft Word- und Google-Dokumenten arbeiten. Dokumente aus diesen Quellen werden zu Seiten auf Ihrer Website. Überschriften, Listen, Bilder, Schriftelemente und Videos können von der ursprünglichen Quelle auf Ihre Website übertragen werden. Sie können Metadaten für SEO-Zwecke hinzufügen oder Blöcke verwenden, um mit strukturierten Inhalten zu arbeiten und Funktionen hinzuzufügen.

Weitere Informationen zur dokumentbasierten Bearbeitung finden Sie unter [Dieses Dokument finden Sie in der Edge Delivery Services-Dokumentation.](/help/edge/docs/authoring.md)

## Authoring mit dem universellen Editor {#universal-editor}

Bei der Verwendung von Edge Delivery Services mit AEM as a Cloud Service ist es die grundlegendste Tatsache zu verstehen, dass der von Ihnen erstellte Inhalt in AEM as a Cloud Service beibehalten wird.

![Funktionsweise des AEM-Authoring mit Edge Delivery Services](assets/how-aem-edge-works.png)

1. [Die AEM Authoring-Umgebung](/help/sites-cloud/authoring/quick-start.md) wird für das Content Management verwendet, z. B. zum Erstellen neuer Seiten, Experience Fragments, Inhaltsfragmente usw.
   * Alle Funktionen von AEM sind verfügbar, wie Workflows, MSM, Übersetzung, Launches usw.
1. [Der universelle Editor](/help/sites-cloud/authoring/universal-editor/authoring.md) wird verwendet, um die in AEM verwalteten Inhalte zu erstellen.
   * Der universelle Editor bietet eine neue und moderne Benutzeroberfläche für das Content-Authoring.
   * Zum Authoring rendert AEM die HTML, schließt jedoch die Skripte, Stile, Symbole und andere Ressourcen von Edge Delivery Services mit ein.
   * Obwohl der universelle Editor verwendet wird, werden alle Änderungen in AEM persistiert.
   * Der universelle Editor ist noch nicht auf Funktionsparität mit dem AEM-Seiteneditor ausgelegt und einige AEM-Funktionen sind im universellen Editor möglicherweise nicht verfügbar.
1. Inhalte, die Sie mit dem universellen Editor erstellen und in AEM persistieren, werden in Edge Delivery Services veröffentlicht.
   * Die Inhalte bleiben in AEM gespeichert.
   * AEM rendert semantische HTML, die für die Aufnahme benötigt wird.
   * Inhalte werden mit Edge Delivery Services veröffentlicht.
1. [Edge Delivery Services](/help/edge/developer/keeping-it-100.md) gewährleisten eine 100%ige Lighthouse-Bewertung.

Bausteine sind grundlegende Komponenten einer Seite, die von Edge Delivery Services bereitgestellt wird. Autorinnen und Autoren können aus Standardbausteinen wählen, die standardmäßig von Adobe bereitgestellt werden, oder aus Bausteinen, die von Ihren Entwicklerinnen und Entwicklern für Ihr Projekt angepasst wurden.

Der universelle Editor bietet eine moderne und intuitive grafische Benutzeroberfläche für das Verfassen von Inhalten durch Drag-and-Drop von Bausteinen.

![Drag-and-Drop von Bausteinen im universellen Editor](assets/blocks.png)

Details zu den Bausteinen können dann in der Leiste Eigenschaften konfiguriert werden.

![Bausteineigenschaften konfigurieren](assets/block-properties.png)

Weitere Informationen zum Verfassen mit dem universellen Editor finden Sie im Dokument [Inhaltserstellung mit dem universellen Editor.](/help/sites-cloud/authoring/universal-editor/authoring.md)

Lesen Sie hierzu das [Erste-Schritte-Handbuch für Entwickelnde zum AEM-Authoring mit Edge Delivery Services](/help/edge/edge-dev-getting-started.md), um zu erfahren, wie Sie Ihr eigenes Projekt mit AEM und Edge Delivery Services erstellen können.

## So beginnen Sie: {#how-to-get-started}

Wenden Sie sich an den Adobe-Support, um Zugriff auf diese Funktion zu erhalten.
