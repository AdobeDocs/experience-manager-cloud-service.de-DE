---
title: Einführung in den universellen Editor
description: Der universelle Editor ist ein modernes visuelles Authoring-Tool, mit dem Ihre Marketing-Organisation wirkungsvolle Web-Erlebnisse erstellen kann.
exl-id: d4fc2384-a0f5-4a6f-9572-62749786be4c
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 08997c760bf1d609dce1dd17de0c549a26083917
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 96%

---


# Einführung in den universellen Editor {#introduction}

Der universelle Editor ist ein modernes visuelles Authoring-Tool, mit dem Ihre Marketing-Organisation wirkungsvolle Web-Erlebnisse erstellen kann.

## Überblick {#overview}

Der universelle Editor ist ein vielseitiger visueller Editor, der Teil von Adobe Experience Manager Sites ist. Er ermöglicht Autorinnen und Autoren die WYSIWYG-Bearbeitung („What you see is what you get“) von beliebigen Headless- und Headful-Erlebnissen. Er bietet Folgendes:

* **Sofortige Bearbeitung**: Autorinnen und Autoren können Inhalte direkt im Vorschauerlebnis bearbeiten und müssen nicht mehr nach einzelnen Inhaltsquellen suchen und zu diesen navigieren.
* **Visuelle Bearbeitung**: Beim Vornehmen von Änderungen sehen Autorinnen und Autoren sofort, wie sich diese auf das tatsächliche Besuchererlebnis auswirken, wodurch Reibung minimiert wird.
* **Auffindbare Optionen**: Klar beschriftete Optionen und eine intuitive Benutzeroberfläche ermöglichen es Autorinnen und Autoren, ganz einfach Metadaten zu konfigurieren und Layouts zu erstellen.
* **Nicht technisch**: Für Änderungen ist kein spezielles Fachwissen erforderlich, gleichzeitig werden die Markenrichtlinien des Unternehmens automatisch durchgesetzt, was die Skalierung von Inhaltsaufgaben in Ihrer Organisation erleichtert.
* **Integration und Erweiterbarkeit**: Da die flexiblen [Erweiterungspunkte](#extensibility) des universellen Editors voll in AEM integriert sind, ermöglichen sie die Vereinheitlichung aller wichtigen Tools in einer einzigen, zusammenhängenden Oberfläche. Von KI-gestützten Funktionen bis hin zu benutzerdefinierten Erweiterungen, die auf Ihre individuellen Geschäftsanforderungen zugeschnitten sind, ermöglicht er Teams, mühelos Workflows zu optimieren und die Produktivität zu verbessern.

Zusammengefasst:

* **Autorinnen und Autoren profitieren** von der Flexibilität des universellen Editors, da er die gleiche konsistente visuelle Bearbeitung für alle Formen von AEM-Inhalten unterstützt.
* **Entwicklerinnen und Entwickler** profitieren von der Vielseitigkeit des universellen Editors, da er eine echte Entkopplung der Implementierung unterstützt.

Da es sich um einen echten Editor als Service handelt und er insgesamt flexibler ist, wird der universelle Editor den [Seiteneditor](/help/sites-cloud/authoring/page-editor/introduction.md) letztendlich ersetzen.

## Unterstützte Architekturen {#supported-architectures}

Der universelle Editor unterstützt die beiden folgenden primären AEM-Setups:

1. **[Edge Delivery Services](/help/edge/overview.md)**: Dies ist aufgrund seiner Einfachheit, schnelleren Time-To-Value und verbesserten Leistung der bevorzugte Ansatz.
1. **[Headless-Implementierungen](/help/headless/introduction.md)**: Wenn Sie ein vorhandenes Headless-Projekt oder spezielle Anforderungen für das entkoppelte Rendering haben, ermöglicht der universelle Editor die visuelle Bearbeitung auf Unternehmensniveau, ohne dass das gesamte Projekt umgestaltet werden muss. Er ist mit praktisch jeder Architektur (SSR, CSR), jedem Web-Framework (Next.js, React, Astro usw.) und jedem Hosting-Modell („eigene App mitbringen“) kompatibel.

>[!TIP]
>
>Lesen Sie das Dokument [Anwendungsfälle und Lernpfade für den universellen Editor](/help/implementing/universal-editor/use-cases.md), um weitere Details zu den unterstützten Architekturen zu erhalten.

## Unterstützte AEM-Versionen {#aem-versions}

Der universelle Editor wird unterstützt von:

* AEM as a Cloud Service (Version `2023.8.13099` oder höher)
* [AEM 6.5 LTS](https://experienceleague.adobe.com/de/docs/experience-manager-65-lts/content/implementing/developing/headless/universal-editor/introduction)
   * Es wird sowohl lokales als auch AMS-Hosting unterstützt.
* [AEM 6.5](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction)
   * Es wird sowohl lokales als auch AMS-Hosting unterstützt.

Diese Dokumentation ist für die Verwendung des universellen Editors mit AEM as a Cloud Service vorgesehen.

## Funktionen {#features}

Der universelle Editor bietet viele Funktionen zur Unterstützung einer Vielzahl von Anwendungsfällen für ein effizientes Content-Management.

* **[WYSIWYG](/help/sites-cloud/authoring/universal-editor/authoring.md)**: Führen Sie eine „What-you-see-is-what-you-get“-Bearbeitung aller Arten von Web-Inhalten durch, einschließlich Nur-Text, Rich-Text, Medien und Metadaten.
* **[Komposition](/help/sites-cloud/authoring/universal-editor/authoring.md#editing-content)**: Erstellen, bearbeiten, verschieben, verschachteln oder löschen Sie Inhaltsblöcke verschiedener Typen (Titel, Schaltflächen, Teaser, Abschnitte, Einbettungen usw.).
* **[Layout](/help/sites-cloud/authoring/universal-editor/templates.md)**: Verwenden Sie Seitenvorlagen, wenden Sie visuelle Stile an und erstellen Sie Layouts mit Blöcken wie Spalten, Karussells und Akkordeons.
* **[Gerätesimulation](/help/sites-cloud/authoring/universal-editor/navigation.md#emulator)**: Zeigen Sie eine Vorschau von Inhalten an und optimieren Sie sie beim Bearbeiten für verschiedene Besuchergeräte.
* **Omni-Channel**: Verwenden Sie strukturierte und unstrukturierte Inhalte in mehreren Kanälen wieder.
* **[Lokalisierung](/help/sites-cloud/authoring/universal-editor/inheritance.md)**: Optimieren Sie die Workflows für die Inhaltsübersetzung und verarbeiten Sie die Vererbung von lokalisierten Inhalten mit Multi-Site-Manager effizient.
* **Konsistenz**: Stellen Sie die Einhaltung von Markenrichtlinien sicher und sorgen Sie für Einheitlichkeit bei allen Inhalten.
* **Sicherheit**: [Erzwingen Sie eine Zugriffskontrolle](/help/implementing/universal-editor/authentication.md), schützen Sie die Inhaltsintegrität und verfolgen sie Änderungen mit [robuster Versionierung](/help/sites-cloud/authoring/sites-console/page-versions.md) nach.
* **[Veröffentlichung](/help/sites-cloud/authoring/universal-editor/publishing.md)**: Integrieren Sie Prüfungs-, Genehmigungs- und Veröffentlichungs-Workflows direkt im Editor.
* **Vereinheitlicht**: Ist vollständig in AEM-Tools wie [Sites-Konsole](/help/sites-cloud/authoring/sites-console/introduction.md), [Inhaltsfragmenteditor ](/help/sites-cloud/administering/content-fragments/overview.md) und viele mehr integriert und bietet ein kohärentes Authoring-Erlebnis.

## Erweiterbarkeit {#extensibility}

Der universelle Editor ist nicht nur standardmäßig sehr leistungsfähig, sondern bietet eine Reihe von Erweiterungsmöglichkeiten.

* **Erweiterungen** sind zahlreich und vorbereitet für die Unterstützung von Anforderungen wie die Unterstützung von Workflows, das Generieren von Varianten und das Ermöglichen von Experimenten, um nur einige zu nennen.
* **Eine erweiterbare Benutzeroberfläche** ermöglicht es Ihnen, eigene Erweiterungen mit denselben zugrunde liegenden Frameworks zu erstellen, die die vorgefertigten Erweiterungen nutzen. Dadurch erreichen Sie eine ultimative Flexibilität für die Anpassung an Ihre Projektanforderungen.
* **Erweiterungspunkte** wie Blöcke, benutzerdefinierte Datentypen und Ereignisse ermöglichen die nahtlose Integration benutzerdefinierter Geschäftsanforderungen über die Benutzeroberfläche hinaus.

>[!TIP]
>
>Weitere Informationen zur Erweiterbarkeit des universellen Editors finden Sie im Dokument [Erweitern des universellen Editors](/help/implementing/universal-editor/extending.md).

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
* AEM as a Cloud Service, [AEM 6.5 LTS](https://experienceleague.adobe.com/de/docs/experience-manager-65-lts/content/implementing/developing/headless/universal-editor/introduction) und [AEM 6.5](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction) sind die einzigen unterstützten AEM-Backends.
* Für AEM as a Cloud Service ist Version `2023.8.13099` oder höher erforderlich.
* Inhaltsautorinnen und Inhaltsautoren müssen über eigene Experience Cloud-Konten verfügen.
* Als Teil von AEM [unterstützt der universelle Editor dieselben Desktop-Browser wie AEM](/help/overview/supported-platforms.md).
   * Mobilversionen dieser Browser werden nicht unterstützt.

{{ip-allow-lists-ue}}

## Nächste Schritte {#next-steps}

Lesen Sie das Dokument [Anwendungsfälle und Lernpfade für den universellen Editor](/help/implementing/universal-editor/use-cases.md), um mehr über gängige Anwendungsfälle für den universellen Editor zu erfahren und die richtigen Dokumentationsressourcen zu finden, die Sie bei Ihrem Projekt unterstützen können.
