---
title: Einführung in den universellen Editor
description: Erfahren Sie, wie der universelle Editor die WYSIWYG-Bearbeitung (What-you-see-is-what-you-get) von Headless- und Headful-Erlebnissen ermöglicht. Erfahren Sie, wie er Autorinnen und Autoren dabei helfen kann, außergewöhnliche Inhalte zu erstellen sowie die Geschwindigkeit ihrer Inhalte zu erhöhen, und wie er Entwicklerinnen und Entwicklern ein modernes Erlebnis bietet.
exl-id: d4fc2384-a0f5-4a6f-9572-62749786be4c
source-git-commit: 79fe3133a6b0553209b14c4cf47faa9db28caacc
workflow-type: tm+mt
source-wordcount: '919'
ht-degree: 88%

---


# Einführung in den universellen Editor {#introduction}

Erfahren Sie, wie der universelle Editor die WYSIWYG-Bearbeitung (What-you-see-is-what-you-get) von Headless- und Headful-Erlebnissen ermöglicht. Erfahren Sie, wie er Autorinnen und Autoren dabei helfen kann, außergewöhnliche Inhalte zu erstellen sowie die Geschwindigkeit ihrer Inhalte zu erhöhen, und wie er Entwicklerinnen und Entwicklern ein modernes Erlebnis bietet.

## Hintergrund {#background}

Das leistungsfähigste Tool für AEM-Inhaltsautorinnen und -autoren ist der Seiteneditor. Der Seiteneditor bietet eine intuitive, visuelle, kontextbezogene WYSIWYG-Authoring-Erfahrung, die nur minimale Schulung erfordert und den Autorinnen und Autoren genau zeigt, wie der Inhalt aussehen wird.

Der Seiteneditor kann jedoch nur AEM Seiteninhalte, die Struktur und die darin enthaltenen Komponenten bearbeiten. Heutzutage werden Inhalte jedoch nur selten von einem einzigen Ort bezogen. Der universelle Editor bietet dieselbe integrierte Bearbeitungserfahrung wie der Seiteneditor, jedoch für alle Aspekte von Inhalten in jeder Implementierung.

## Wahrhaftig universell {#universal}

Der universelle Editor kann für jede Implementierung, für jeden Inhalt und für jeden Aspekt des Inhalts instrumentiert werden.

![Was ihn universell macht](assets/universal.png)

### Jegliche Implementierung {#any-implementation}

Da Erlebnisse auf viele verschiedene Arten erstellt werden können, kann jede Implementierung den universellen Editor nutzen, damit Autorinnen und Autoren Bearbeitungen direkt im Kontext durchführen können.

Benutzer glauben oft, dass eine Headless-Implementierung die Autoren daran hindert, alle Inhalte in einer formularbasierten Benutzeroberfläche zu bearbeiten. Dies ist jedoch beim universellen Editor nicht der Fall.

Die Anforderungen für eine Implementierung zur Nutzung des universellen Editors sind sehr einfach und unterstützen die folgenden Punkte:

* **Beliebige Architektur** – Server-seitiges Rendering, Edge-seitiges Rendering, Client-seitiges Rendering usw.
* **Jegliches Framework** – Vanilla-AEM oder Drittanbieter-Frameworks wie React, Next.js, Angular usw.
* **Beliebiges Hosting** – Kann lokal auf AEM oder auf einer Remote-Domain gehostet werden.

### Beliebiger Inhalt {#any-content}

Inhaltsautorinnen und -autoren sollten dasselbe leistungsstarke Bearbeitungserlebnis erhalten, das ihnen zuvor vom AEM-Seiteneditor geboten wurde. Der universelle Editor erlaubt es Autorinnen und Autoren, **beliebige** Inhalte visuell und im Kontext zu bearbeiten und unterstützt:

* **AEM Seitenstrukturen** – Verschachtelte `cq:Components` von `cq:Pages`, einschließlich Experience Fragments.
* **AEM-Inhaltsfragmente** – Bearbeiten Sie Inhalte aus Inhaltsfragmenten so, wie sie im Kontext des Erlebnisses erscheinen.
* **Dokumente** – Der Machbarkeitsnachweis hat gezeigt, dass auch Word-, Excel-, Google-Dokumente oder Markdown-Dokumente auf die gleiche Weise bearbeitet werden können (dies ist noch in Arbeit).

### Beliebiger Aspekt {#any-aspect}

Für Inhaltsautorinnen und -autoren geht es bei Inhalten nicht nur um die enthaltenen Informationen, sondern auch darum, wie sie gerendert und empfangen werden. Zu den Inhalten gehören zusätzliche Metadaten- und Instrumentierungsregeln, die der universelle Editor verstehen und bearbeiten kann, darunter:

* **Anwendung von Layout und Stil** – Mithilfe eines Stilsystems können Marketing-Teams und Inhaltsautorinnen bzw. -autoren unterschiedliche Stile auf ihre Inhalte anwenden und unterschiedliche Layouts für die Inhalte erstellen, z. B. Spalten, Karussells, Registerkarten, Akkordeons usw.

## Wert  {#value}

Durch die Entkopplung des Inhaltserstellungserlebnisses von einem bestimmten Inhaltsbereitstellungssystem wird der Editor wirklich universell und flexibel, sodass Inhaltsautorinnen und -autoren außergewöhnliche Erlebnisse bereitstellen und die Inhaltsgeschwindigkeit erhöhen können und ein modernes Entwicklererlebnis geboten wird.

![Der Wert des universellen Editors](assets/value.png)

* **Bereitstellen außergewöhnlicher Erlebnisse**: Damit technische Fachkräfte ein überzeugendes Erlebnis für Besucherinnen und Besucher schaffen können, können sie im universellen Editor die Inhalte im Kontext der Vorschau erstellen und bearbeiten. Auf diese Weise können sie Inhalte erstellen, die dem Design des Erlebnisses entsprechen und zu einer aussagekräftigen Journey für Besuchende beitragen.
* **Inhaltsgeschwindigkeit erhöhen** – Um den Verwaltungs-Workflow für technische Fachkräfte zu optimieren, ermöglicht der universelle Editor die Bearbeitung von Inhalten in der Vorschau, um sie zu leiten, indem nur die Optionen angezeigt werden, die für diesen Kontext relevant sind, und der Workflow von den Inhaltsquellen unabhängig wird.
* **Modernstes Entwicklererlebnis** – Zur Unterstützung der heterogenen Anwendungslandschaft in der realen Welt ist der universelle Editor vollständig entkoppelt und technologieunabhängig, sodass Entwicklerinnen und Entwickler ihren bevorzugten Technologiestapel zur Implementierung des Erlebnisses nutzen können.

## Universal Editor und der Inhaltsfragment-Editor {#universal-editor-content-fragment-editor}

Auf den ersten Blick sieht es so aus, als ob der Universal Editor und der Inhaltsfragment-Editor ähnliche Bearbeitungsfunktionen bieten. Die beiden Editoren bieten jedoch sehr unterschiedliche Funktionen und erledigen unterschiedliche Aufgaben für Marketing-Fachleute.

### Inhaltsfragment-Editor {#content-fragment-editor}

Eine Marketing-Fachkraft möchte Inhalte erstellen, ohne sich um das Layout kümmern zu müssen, damit sie in zahlreichen Kontexten des Erlebnisses wiederverwendet werden können.

* Die zugrunde liegende Aufgabe besteht darin, die Inhaltsstrategie zu skalieren.

### Universeller Editor {#universal-editor}

Eine Marketing-Fachkraft möchte Inhalte erstellen, die auf das Layout eines bestimmten Kontexts zugeschnitten sind, um ein außergewöhnliches Erlebnis zu bieten.

* Die zugrunde liegende Aufgabe besteht darin, eine überzeugende Verbindung mit den Leserinnen und Lesern herzustellen.

## Entwicklungsplan {#road-map}

Es ist wichtig zu beachten, dass der universelle Editor noch in Bearbeitung ist und dass einige der in diesem Dokument beschriebenen Funktionen eine Vision des endgültigen Editors darstellen, aber nicht notwendigerweise für seine aktuellen Funktionen repräsentativ sind.

Wenden Sie sich an Ihre Ansprechperson bei Adobe, um mehr über die für den universellen Editor geplanten Funktionen zu erfahren.

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zum universellen Editor finden Sie in diesen Dokumenten.

* [Inhaltserstellung mit dem universellen Editor](authoring.md) – Erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und -autoren ist, Inhalte mit dem universellen Editor zu erstellen.
* [Veröffentlichen von Inhalten mit dem universellen Editor](publishing.md) - Erfahren Sie, wie der Universal Editor Inhalte veröffentlicht und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.
* [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) – Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.
* [Architektur des universellen Editors](architecture.md) – Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
* [Attribute und Typen](attributes-types.md) – Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
* [Authentifizierung beim universellen Editor](authentication.md) – Erfahren Sie, wie beim universellen Editor authentifiziert wird.
