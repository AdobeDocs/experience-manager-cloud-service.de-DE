---
title: Inhaltsoptimierungs-Agent
description: Erfahren Sie, wie Sie mit dem Inhaltsoptimierungs-Agenten transformieren können, wie Benutzer Assets verfeinern und anpassen, indem sie Anweisungen in natürlicher Sprache anwenden, um kanalfertige Varianten zu erstellen.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: 8b7bdb86c3d1b537b536173b6307c486fe436636
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---


# Inhaltsoptimierungs-Agent {#content-optimization-agent}

Der Content Optimization Agent transformiert, wie Benutzer Assets verfeinern und anpassen, indem er Anweisungen in natürlicher Sprache anwendet, um kanalfertige Varianten zu erstellen. Unabhängig davon, ob neue Ausgabedarstellungen erstellt, visuelle Eigenschaften angepasst, Hintergründe geändert oder Assets für bestimmte digitale Kanäle vorbereitet werden, interpretiert der Agent die Benutzerabsicht und führt komplexe Bearbeitungsaufgaben automatisch aus. Es arbeitet nahtlos mit dem Discovery Agent zusammen, nimmt die gefundenen Assets auf und erstellt optimierte Varianten unter Verwendung von [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) die ohne manuellen Design-Aufwand die Marken-, Kanal- und Kampagnenanforderungen erfüllen.

Zu den wichtigsten Vorteilen der Inhaltsoptimierung gehören:

* **Mühelose Asset-**: Konvertiert einfache, dialogorientierte Eingabeaufforderungen in präzise Bildoperationen wie Größenanpassung, Scharfzeichnung, Spiegelung oder Neufärbung, sodass keine speziellen Bearbeitungswerkzeuge mehr benötigt werden.

* **Kanaloptimierte Ausgaben**: Erstellt schnell Ausgabedarstellungen, die für bestimmte Plattformen wie Instagram-Stories, Webbanner oder andere Marketing-Touchpoints zugeschnitten sind, und stellt sicher, dass Assets zur sofortigen Verwendung bereit sind.

* **Skalierbare Creative-Verbesserung**: Wendet visuelle Anpassungen und Verbesserungen an, z. B. Änderungen im Hintergrund oder Grafiküberlagerungen, um kreative Workflows mit hohem Volumen zu unterstützen, ohne die Teamleistung zu verlangsamen.

* **[Nahtlose Zusammenarbeit mit dem Discovery Agent](/help/ai-in-aem/agents/discovery/using.md)**: Baut auf den vom Discovery Agent identifizierten Assets auf und ermöglicht den End-to-End-Abruf und die Optimierung von Assets durch natürliche Konversation.

>[!IMPORTANT]
>
>KI-generierte Antworten können ungenau oder irreführend sein. Überprüfen Sie unbedingt die vorgeschlagenen Fehlerbehebungen und Antworten.
>
>Siehe auch [Benutzerhandbücher für die generative KI von Adobe Experience Cloud](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html).

## Voraussetzungen {#prerequisites-content-optimization-agent}

So generieren Sie Varianten oder Optimierungen für Bild-Assets. Sie müssen über Folgendes verfügen:

* Eine gültige Dynamic Media-Lizenz

* Dynamic Media mit aktivierter OpenAPI in der AEM as a Cloud Service-Umgebung.

* Die Assets in [genehmigten Status](/help/assets/manage-organize-assets-view.md#manage-asset-status) in Ihrer AEM as a Cloud Service-Umgebung.


## Kompetenzen {#skills-content-optimization-agent}

Der Inhaltsoptimierungs-Agent bietet die folgenden Fähigkeiten:

* **Verstehen Sie Absicht durch natürliche Sprache**

  Der Inhaltsoptimierungs-Agent interpretiert die Benutzerinteressen aus Eingabeaufforderungen in natürlicher Sprache und berücksichtigt den Kanal-, Kampagnen- und Zielgruppenkontext, um die relevantesten Optimierungsaktionen zu ermitteln.

* **Erzeugt dynamische Inhaltsvarianten**

  Der Content Optimization Agent erstellt optimierte Varianten als dynamische URLs, die auf verschiedene Kanäle und Formattypen zugeschnitten sind.

* **Optimiert den Bildinhalt**

  Der Inhaltsoptimierungsagent wendet Verbesserungen wie Formatkonvertierung, Auflösungsanpassungen, Zuschnitt und Scharfzeichnung an, um die Bildqualität zu verbessern.

* **Asset-Optimierung mit mehreren Varianten**

  Der Content Optimization Agent kann mit einer einzigen natürlichen Sprachaufforderung mehrere optimierte Bildvarianten aus den vom Discovery Agent zurückgegebenen Assets generieren, sodass Benutzer schnell und effizient kanalfertige Ausgabedarstellungen erstellen können.

## Personen {#personas-content-optimization-agent}

Channel-Marketing-Experten, die Schlüsselrolle für den Content Optimization Agent, können die richtigen hochauflösenden Quellinhalte auswählen und optimierte Formate anfordern, die auf ihre Kanäle und Zielgruppensegmente zugeschnitten sind.

Regionale Marketer und Agenturmitarbeiter können auch den Content Optimization Agent verwenden, um schnell kanalfertige Bildvarianten zu generieren, die eine schnellere, konsistentere Inhaltserstellung unterstützen.

## Wie greife ich auf den Content Optimization Agent zu? {#access-content-optimization-agent}

Sie können über den KI-Assistenten auf die Agenten in AEM zugreifen. Melden Sie sich bei experience.adobe.com an und Sie können mit dem KI-Assistenten interagieren, indem Sie Ihre Eingabeaufforderung in natürlicher Sprache über das Feld `Ask AI Assistant anything` angeben:

![Zugriff auf Discovery Agent](/help/ai-in-aem/agents/discovery/assets/access-discovery-agent.png)

## Häufige Anwendungsfälle und Beispielaufforderungen {#use-cases-prompts}

Verwenden Sie Eingabeaufforderungen zur Inhaltsoptimierung, indem Sie über den [Discovery-Agent“ nach den richtigen Assets ](/help/ai-in-aem/agents/discovery/using.md). Sobald die relevanten Bilder angezeigt werden, können Benutzer direkt aus den Suchergebnissen optimierte oder kanalspezifische Varianten für ein oder mehrere Assets generieren. Dieser Workflow sorgt für hochwertige Eingaben und durchgängig bessere Optimierungsergebnisse. [Siehe die vollständige Liste der verfügbaren Optimierungen](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/).

* **Erstellung von Ausgabedarstellungen mit hoher Auflösung**

  Der Agent kann neue Ausgabedarstellungen eines Assets mit einer bestimmten Auflösung und Qualitätsstufe generieren, sodass kanalbereite Varianten ohne manuelle Bearbeitung einfach vorbereitet werden können.


  Eingabeaufforderung für Beispiel:

  Erstellen Sie eine `2000px` Ausgabedarstellung `JPEG` mit `80%`.

  Suchen Sie mit dem [Discovery-Agent](/help/ai-in-aem/agents/discovery/using.md) nach dem richtigen Asset und verwenden Sie dann bei mehreren Suchergebnissen die folgenden Eingabeaufforderungen:

  Erstellen Sie für das dritte Suchergebnis eine `2000px` Ausgabedarstellung `JPEG` mit `80%`.

  ODER

  Generieren Sie `Asset ID` eine Ausgabedarstellung von 2.000 Pixel `JPEG` einer `80%` Qualität

* **Bildverbesserung**

  Der Agent kann visuelle Verbesserungen anwenden, z. B. das Scharfzeichnen, um sicherzustellen, dass Assets gestochen scharf und klar definiert aussehen, bevor sie in Kampagnen verwendet werden.

  Eingabeaufforderung für Beispiel:

  Scharfzeichnen des Bildes.


* **Anpassungen der Hintergrundfarbe**

  Der Agent kann Hintergrundfarben in transparenten Assets aktualisieren oder ersetzen und markenspezifische Farbschemata oder kampagnengesteuerte visuelle Designs unterstützen.

  Eingabeaufforderung für Beispiel:

  Ändern Sie die Hintergrundfarbe des `PNG` in `#ff8932`.

* **Orientierungstransformationen**

  Der Agent kann visuelle Elemente spiegeln oder spiegeln, um sie an die Layout-Anforderungen oder die kreative Richtung anzupassen, ohne dass externe Bearbeitungswerkzeuge erforderlich sind.

  Eingabeaufforderung für Beispiel:

  Spiegeln Sie das Bild horizontal.

* **Kanaloptimierte Ausgabedarstellungen**

  Der Agent kann Ausgabedarstellungen erstellen, die auf plattformspezifische Anforderungen zugeschnitten sind, z. B. Instagram Stories, um sicherzustellen, dass Assets automatisch den Richtlinien für Format, Verhältnis und Qualität entsprechen.

  Eingabeaufforderung für Beispiele:

  Erstellen Sie eine Ausgabedarstellung für eine `Instagram` Story.

* **Markenüberlagerungen und Composite-Generierung**

  Der Agent kann Werbeggrafiken, Überlagerungen oder Abzeichen auf vorhandene Assets mit präziser Platzierung anwenden und so die schnelle Erstellung von kampagnenbereiten Composites unterstützen.

  Eingabeaufforderung für Beispiele:

  Überlagern Sie das Bild mit `30%` Rabattgrafiken über dem Werbebanner und platzieren Sie es `100px` von der Mitte.

  >[!NOTE]
  >
  >Die Überlagerungspositionen sind möglicherweise nicht genau.


## Optimierungsergebnisse {#content-optimization-agent-results}

Wenn Sie eine Optimierungsaufforderung angeben, gibt der Inhaltsoptimierungs-Agent das erweiterte Asset zusammen mit praktischen Zugriffsoptionen je nach Asset-Typ zurück:

* **Bilder**: Die Antwort enthält eine Miniaturvorschau und Optionen zum Öffnen der Dynamic Media-URL oder zum Herunterladen des optimierten Bildes.

* **PDF-Dokumente**: Die Antwort enthält eine Miniaturvorschau und Optionen zum Öffnen der Dynamic Media-URL oder zum Herunterladen der optimierten Datei.

* **Videos**: Die Antwort bietet Optionen zum Öffnen der Dynamic Media-URL oder zum Herunterladen des optimierten Videos.

![Ergebnisse der Inhaltsoptimierung](/help/ai-in-aem/agents/content-optimization/assets/download-content-optimization.png)

Diese Ergebnisse erleichtern die Überprüfung der optimierten Ausgabe und ihre sofortige Verwendung in nachgelagerten Kanälen oder Workflows.

<!--


## Prompting best Practices {#prompting-best-practices-content-optimization-agent}

The following are some of the prompting best practices:

* Be explicit about the enhancement you want the Content Optimization Agent to apply. Clearly state the transformation or adjustment you expect. Precise instructions help the agent produce accurate and predictable results. For example, Instead of `Make it good quality`, specify `Create a JPEG image with 90% quality`.

* Provide detailed parameters whenever possible. The more context you give, such as dimensions, format, quality, placement, or color values, the more tailored the output is.

-->
