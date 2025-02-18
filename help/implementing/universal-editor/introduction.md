---
title: Einführung in den universellen Editor
description: Der universelle Editor ist ein modernes visuelles Authoring-Tool, mit dem Ihr Marketing-Unternehmen wirkungsvolle Web-Erlebnisse erstellen kann.
exl-id: d4fc2384-a0f5-4a6f-9572-62749786be4c
feature: Developing
role: Admin, Architect, Developer
source-git-commit: ae962d89b842b0708c1ac8633bb49c86cb2edfda
workflow-type: tm+mt
source-wordcount: '949'
ht-degree: 27%

---


# Einführung in den universellen Editor {#introduction}

Der universelle Editor ist ein modernes visuelles Authoring-Tool, mit dem Ihr Marketing-Unternehmen wirkungsvolle Web-Erlebnisse erstellen kann.

## Überblick {#overview}

Der universelle Editor ist ein vielseitiger visueller Editor, der Teil von Adobe Experience Manager Sites ist. Damit können Autorinnen und Autoren eine WYSIWYG-Bearbeitung (What you see is what you get) von Headless- oder Headful-Erlebnissen durchführen. Es bietet:

* **Sofortbearbeitung**: Autoren können Inhalte direkt im Vorschauerlebnis bearbeiten, sodass sie nicht mehr nach einzelnen Inhaltsquellen suchen und zu diesen navigieren müssen.
* **Visuelle Bearbeitung**: Beim Vornehmen von Änderungen sehen Autoren sofort, wie sich diese auf das tatsächliche Besuchererlebnis auswirken, wodurch Reibung minimiert wird.
* **Entdeckbare Optionen**: Klar beschriftete Optionen und eine intuitive Benutzeroberfläche ermöglichen es Autoren, Metadaten zu konfigurieren und Layouts einfach zu erstellen.
* **Nicht technisch**: Für Änderungen ist kein spezielles Fachwissen erforderlich, während die Markenrichtlinien des Unternehmens automatisch durchgesetzt werden, was die Skalierung von Inhaltsaufgaben in Ihrem Unternehmen erleichtert.
* **Integration und Erweiterbarkeit**: Voll integriert mit AEM, den flexiblen [Erweiterungspunkten“ des universellen Editors](#extensibility) ermöglichen die Vereinheitlichung aller wichtigen Tools in einer einzigen, zusammenhängenden Oberfläche. Von KI-gestützten Funktionen bis hin zu benutzerdefinierten Erweiterungen, die auf Ihre individuellen Geschäftsanforderungen zugeschnitten sind, ermöglicht es Teams, Workflows zu optimieren und die Produktivität mühelos zu verbessern.

Zusammenfassend:

* **Autoren profitieren** der Flexibilität des universellen Editors, da er dieselbe konsistente visuelle Bearbeitung für alle Formen von AEM-Inhalten unterstützt.
* **Entwickler profitieren von** Vielseitigkeit des universellen Editors, da er eine echte Entkopplung der Implementierung unterstützt.

Da es sich um einen echten Editor als Service handelt und dieser insgesamt flexibler ist, beabsichtigt der universelle Editor, den [Seiteneditor“ letztendlich zu ersetzen](/help/sites-cloud/authoring/page-editor/introduction.md)

## Unterstützte Architekturen {#supported-architectures}

Der universelle Editor unterstützt die beiden folgenden primären AEM-Setups:

1. **[Edge Delivery Services](/help/edge/overview.md)**: Dies ist der bevorzugte Ansatz für seine Einfachheit, schnellere Time-to-Value und verbesserte Leistung.
1. **[Headless-Implementierungen](/help/headless/introduction.md)**: Wenn Sie ein vorhandenes Headless-Projekt oder spezielle Anforderungen für das entkoppelte Rendering haben, ermöglicht der universelle Editor die visuelle Bearbeitung auf Unternehmensniveau, ohne dass das gesamte Projekt umgestaltet werden muss. Es ist mit praktisch jeder Architektur (SSR, CSR), jedem Web-Framework (Next.js, React, Astro usw.) und Hosting-Modellen („bring your own app„) kompatibel.

>[!TIP]
>
>Bitte lesen Sie das Dokument [Anwendungsfälle und Lernpfade des universellen Editors](/help/implementing/universal-editor/use-cases.md) für weitere Details zu den unterstützten Architekturen.

## Unterstützte AEM-Versionen {#aem-versions}

Der universelle Editor wird unterstützt von:

* AEM as a Cloud Service (Version `2023.8.13099` oder höher)
* AEM 6.5 (Service Pack 21 oder 22 plus ein Feature Pack)

Diese Dokumentation ist für die Verwendung des universellen Editors mit AEM as a Cloud Service vorgesehen. Informationen zur Verwendung des universellen Editors mit AEM 6.5 [finden Sie in der Dokumentation zu AEM 6.5.](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction?lang=en)

## Funktionen {#features}

Der universelle Editor bietet viele Funktionen zur Unterstützung einer Vielzahl von Anwendungsfällen für ein effizientes Content-Management.

* **[WYSIWYG](/help/sites-cloud/authoring/universal-editor/authoring.md)**: Führen Sie eine Bearbeitung aller Arten von Web-Inhalten durch, einschließlich Nur-Text, Rich-Text, Medien und Metadaten.
* **[Komposition](/help/sites-cloud/authoring/universal-editor/authoring.md#editing-content)**: Erstellen, Bearbeiten, neu anordnen, verschachteln oder löschen Sie Inhaltsblöcke verschiedener Typen (Titel, Schaltflächen, Teaser, Abschnitte, Einbettungen usw.).
* **[Layout](/help/sites-cloud/authoring/universal-editor/templates.md)**: Verwenden Sie Seitenvorlagen, wenden Sie visuelle Stile an und erstellen Sie Layouts mit Blöcken wie Spalten, Karussells und Akkordeons.
* **[Gerätesimulation](/help/sites-cloud/authoring/universal-editor/navigation.md#emulator)**: Vorschau und Optimierung von Inhalten für verschiedene Besuchergeräte beim Bearbeiten.
* **Omnichannel**: Wiederverwenden von strukturierten und unstrukturierten Inhalten über mehrere Kanäle hinweg.
* **[Lokalisierung](/help/sites-cloud/authoring/universal-editor/inheritance.md)**: Optimierung der Workflows für die Inhaltsübersetzung und effiziente Verwaltung der lokalisierten Inhalte mit Multi-Site-Manager.
* **Konsistenz**: Stellen Sie die Einhaltung von Markenrichtlinien sicher und sorgen Sie für Einheitlichkeit bei allen Inhalten.
* **Sicherheit**: [Zugriffskontrolle erzwingen](/help/implementing/universal-editor/authentication.md) Inhaltsintegrität schützen und Änderungen mit nachverfolgen [robuste Versionierung.](/help/sites-cloud/authoring/sites-console/page-versions.md)
* **[Publishing](/help/sites-cloud/authoring/universal-editor/publishing.md)**: Integrieren Sie Prüfungs-, Genehmigungs- und Veröffentlichungs-Workflows direkt im Editor.
* **Unified**: Vollständige Integration in AEM-Tools wie [Sites-Konsole](/help/sites-cloud/authoring/sites-console/introduction.md) [Inhaltsfragment-Editor ](/help/sites-cloud/administering/content-fragments/overview.md) vieles mehr und bietet ein kohärentes Authoring-Erlebnis.

## Erweiterbarkeit {#extensibility}

Der universelle Editor ist nicht nur sehr leistungsfähig, sondern bietet eine Reihe von Erweiterungsmöglichkeiten.

* **Erweiterungen** sind zahlreich und für die Unterstützung von Anforderungen wie die Unterstützung von Workflows, das Generieren von Varianten und das Ermöglichen von Experimenten, um nur einige zu nennen, vorbereitet.
* **Eine erweiterbare Benutzeroberfläche** ermöglicht es Ihnen, eigene Erweiterungen mit denselben zugrunde liegenden Frameworks zu erstellen, die die vorgefertigten Erweiterungen nutzen, was eine ultimative Flexibilität ermöglicht, um sich an Ihre Projektanforderungen anzupassen.
* **Erweiterungspunkte** wie Blöcke, benutzerdefinierte Datentypen und Ereignisse, ermöglichen die nahtlose Integration benutzerdefinierter Geschäftsanforderungen über die Benutzeroberfläche hinaus.

>[!TIP]
>
>Weitere Informationen zur Erweiterbarkeit des universellen Editors finden Sie im Dokument [Erweitern des universellen Editors.](/help/implementing/universal-editor/extending.md)

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
* Für AEM as a Cloud Service ist Version `2023.8.13099` oder höher erforderlich.
* Inhaltsautorinnen und Inhaltsautoren müssen über eigene Experience Cloud-Konten verfügen.
* Im Rahmen von AEM unterstützt der universelle Editor [dieselben Desktop-Browser wie AEM.](/help/overview/supported-platforms.md)
   * Mobilversionen dieser Browser werden nicht unterstützt.

{{ue-ip-allow-lists}}

## Nächste Schritte {#next-steps}

Lesen Sie das Dokument [Anwendungsfälle und Lernpfade für den universellen Editor](/help/implementing/universal-editor/use-cases.md), um mehr über gängige Anwendungsfälle für den universellen Editor zu erfahren und die richtigen Dokumentationsressourcen zu finden, die Sie bei Ihrem Projekt unterstützen können.
