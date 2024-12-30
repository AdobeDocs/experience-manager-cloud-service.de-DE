---
title: Einführung in den universellen Editor
description: Erfahren Sie, wie der universelle Editor die WYSIWYG-Bearbeitung (What you see is what you get) von beliebigen Headless- und Headful-Erlebnissen ermöglicht. Erfahren Sie, wie er Autorinnen und Autoren dabei helfen kann, außergewöhnliche Inhalte zu erstellen sowie die Geschwindigkeit ihrer Inhalte zu erhöhen, und inwiefern er Entwickelnden ein modernes Erlebnis bietet.
exl-id: d4fc2384-a0f5-4a6f-9572-62749786be4c
feature: Developing
role: Admin, Architect, Developer
source-git-commit: b8d56873b7bc23295fefc35a826b8047c626649e
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 98%

---


# Einführung in den universellen Editor {#introduction}

Der universelle Editor ist ein vielseitiger visueller Editor, der Teil von Adobe Experience Manager Sites ist. Er ermöglicht Autorinnen und Autoren die WYSIWYG-Bearbeitung (What you see is what you get) von beliebigen Headless- und Headful-Erlebnissen. Erfahren Sie, wie er Autorinnen und Autoren von Inhalten dabei helfen kann, außergewöhnliche Erlebnisse zu liefern, und wie er Entwicklerinnen und Entwicklern unvergleichliche Freiheit bietet.

## Hintergrund {#background}

Der universelle Editor bietet ein effizientes und intuitives kontextbezogenes Authoring-Erlebnis, das nur eine minimale Schulung erfordert. Mit ihm können Autorinnen und Autoren ihre Inhalte direkt im Kontext des Web-Erlebnisses verwalten, genau so, wie sie den Besuchenden angezeigt werden. Da es sich um einen echten Editor als Dienst handelt, der insgesamt flexibler ist, soll der Seiteneditor letztendlich durch ihn ersetzt werden.

Autorinnen und Autoren profitieren von der Flexibilität des universellen Editors, da er dieselbe konsistente visuelle Bearbeitung für alle Formen von AEM-Inhalten unterstützt: Die Bearbeitung im Kontext und die Layout-Komposition sind sowohl für Inhaltsfragmente als auch für Seitenkomponenten möglich. Die beiden Formen von Inhalten können sogar bearbeitet werden, wenn sie nebeneinander in einem Web-Erlebnis angezeigt werden, ohne dass die Autorinnen und Autoren den Kontext wechseln müssen. Dies ist eine enorme Verbesserung im Vergleich zu früheren AEM-Editoren, die nur eine Art von Inhalt unterstützten.

Entwicklerinnen und Entwickler profitieren von der Vielseitigkeit des universellen Editors, da er auch eine echte Entkopplung der Implementierung unterstützt. Damit können Entwicklerinnen und Entwickler praktisch jedes Framework oder jede Architektur ihrer Wahl nutzen, ohne dass sie SDK- oder Technologieeinschränkungen unterliegen. Diese Flexibilität erleichtert sogar die Instrumentierung vorhandener Web-Apps für den universellen Editor, ohne dass diese neu aufgebaut werden müssen.

## Wahrhaftig universell {#universal}

Der universelle Editor kann für jede Implementierung, für jeden Inhalt und für jeden Aspekt des Inhalts instrumentiert werden.

![Was ihn universell macht](assets/universal.png)

### Jegliche Implementierung {#any-implementation}

Da Erlebnisse auf viele verschiedene Arten erstellt werden können, kann jede Implementierung den universellen Editor nutzen, damit Autorinnen und Autoren Bearbeitungen direkt im Kontext durchführen können.

Benutzende glauben oft, dass eine Headless-Implementierung die Autorinnen und Autoren darauf beschränkt, alle Inhalte in einer formularbasierten Benutzeroberfläche zu bearbeiten, aber das ist beim universellen Editor nicht der Fall

Die Anforderungen für eine Implementierung zur Nutzung des universellen Editors sind sehr einfach und unterstützen die folgenden Punkte:

* **Jegliche Architektur** – Server-seitiges Rendering, Edge-seitiges Rendering, Client-seitiges Rendering usw.
* **Jegliches Framework** – Vanilla AEM oder Drittanbieter-Frameworks wie React, Next.js, Angular usw.
* **Beliebiges Hosting** – Kann lokal auf AEM oder auf einer Remote-Domain gehostet werden.

### Beliebiger Inhalt {#any-content}

Inhaltsautorinnen und -autoren sollten dasselbe leistungsstarke Bearbeitungserlebnis erhalten, das ihnen zuvor vom AEM-Seiteneditor geboten wurde. Der universelle Editor erlaubt es Autorinnen und Autoren, **beliebige** Inhalte visuell und im Kontext zu bearbeiten und unterstützt:

* **AEM Seitenstrukturen** – Verschachtelte `cq:Components` von `cq:Pages`, einschließlich Experience Fragments.
* **AEM-Inhaltsfragmente** – Bearbeiten Sie Inhalte aus Inhaltsfragmenten so, wie sie im Kontext des Erlebnisses erscheinen.
* **Dokumente** – Der Machbarkeitsnachweis hat gezeigt, dass auch Word-, Excel-, Google-Dokumente oder Markdown-Dokumente auf die gleiche Weise bearbeitet werden können (dies ist noch in Arbeit).

### Beliebiger Aspekt {#any-aspect}

Für Inhaltsautorinnen und -autoren geht es bei Inhalten nicht nur um die enthaltenen Informationen, sondern auch darum, wie sie gerendert und empfangen werden. Zu den Inhalten gehören zusätzliche Metadaten- und Instrumentierungsregeln, die der universelle Editor verstehen und bearbeiten kann, darunter:

* **Anwendung von Layout und Stil** – Mithilfe eines Stilsystems können Marketing-Teams und Inhaltsautorinnen bzw. Inhaltsautoren unterschiedliche Stile auf ihre Inhalte anwenden und unterschiedliche Layouts für die Inhalte erstellen, z. B. Spalten, Karussells, Registerkarten, Akkordeons usw.

## Wert  {#value}

Durch die Entkopplung des Inhaltserstellungserlebnisses von einem bestimmten Inhaltsbereitstellungssystem wird der Editor wirklich universell und flexibel, sodass Inhaltsautorinnen und -autoren außergewöhnliche Erlebnisse bereitstellen und die Inhaltsgeschwindigkeit erhöhen können und ein modernes Entwicklererlebnis geboten wird.

![Der Wert des universellen Editors](assets/value.png)

* **Bereitstellen außergewöhnlicher Erlebnisse**: Damit technische Fachkräfte ein überzeugendes Erlebnis für Besucherinnen und Besucher schaffen können, können sie im universellen Editor die Inhalte im Kontext der Vorschau erstellen und bearbeiten. Auf diese Weise können sie Inhalte erstellen, die dem Design des Erlebnisses entsprechen und zu einer aussagekräftigen Journey für Besuchende beitragen.
* **Inhaltsgeschwindigkeit erhöhen** – Um den Verwaltungs-Workflow für technische Fachkräfte zu optimieren, ermöglicht der universelle Editor die Bearbeitung von Inhalten in der Vorschau, um sie zu leiten, indem nur die Optionen angezeigt werden, die für diesen Kontext relevant sind, und der Workflow von den Inhaltsquellen unabhängig wird.
* **Modernstes Entwicklererlebnis** – Zur Unterstützung der heterogenen Anwendungslandschaft in der realen Welt ist der universelle Editor vollständig entkoppelt und technologieunabhängig, sodass Entwicklerinnen und Entwickler ihren bevorzugten Technologiestapel zur Implementierung des Erlebnisses nutzen können.

## Universeller Editor und der Inhaltsfragmenteditor {#universal-editor-content-fragment-editor}

Auf den ersten Blick sieht es so aus, als ob der universelle Editor und der Inhaltsfragmenteditor ähnliche Bearbeitungsfunktionen bieten. Die beiden Editoren bieten jedoch sehr unterschiedliche Funktionen und erledigen unterschiedliche Aufgaben für Marketing-Fachleute.

### Inhaltsfragment-Editor {#content-fragment-editor}

Eine Marketing-Fachkraft möchte Inhalte erstellen, ohne sich um das Layout kümmern zu müssen, damit sie in zahlreichen Kontexten des Erlebnisses wiederverwendet werden können.

* Die zugrunde liegende Aufgabe besteht darin, die Inhaltsstrategie zu skalieren.

### universellen Editor {#universal-editor}

Eine Marketing-Fachkraft möchte Inhalte erstellen, die auf das Layout eines bestimmten Kontexts zugeschnitten sind, um ein außergewöhnliches Erlebnis zu bieten.

* Die zugrunde liegende Aufgabe besteht darin, eine überzeugende Verbindung mit den Leserinnen und Lesern herzustellen.

## Einschränkungen {#limitations}

Beachten Sie bei der Erkundung des universellen Editors und später bei seiner Implementierung in Ihre eigenen Projekte folgende Einschränkungen:

* Auf einer einzelnen Seite sollten nicht mehr als 25 AEM-Ressourcen (Inhaltsfragmente, Seiten, Experience Fragments, Assets usw.) als Instrumentierung referenziert werden.
* AEM as a Cloud Service und [AEM 6.5](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction) sind die einzigen unterstützten AEM-Backends.
* Es ist AEM as a Cloud Service Version `2023.8.13099` oder höher erforderlich.
* Inhaltsautorinnen und Inhaltsautoren müssen über eigene Experience Cloud-Konten verfügen.
* Als Teil von AEM unterstützt der universelle Editor dieselben Desktop-Browser wie AEM.
   * Mobilversionen dieser Browser werden nicht unterstützt.

{{ue-ip-allow-lists}}

## Nächste Schritte {#next-steps}

Lesen Sie das Dokument [Anwendungsfälle und Lernpfade für den universellen Editor](/help/implementing/universal-editor/use-cases.md), um mehr über gängige Anwendungsfälle für den universellen Editor zu erfahren und die richtigen Dokumentationsressourcen zu finden, die Sie bei Ihrem Projekt unterstützen können.
