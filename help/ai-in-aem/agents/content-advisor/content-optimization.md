---
title: Auftrag zur Inhaltsoptimierung
description: Erfahren Sie, wie Sie mit dem Auftrag zur Inhaltsoptimierung transformieren können, wie Benutzer Assets verfeinern und anpassen, indem sie Anweisungen in natürlicher Sprache anwenden, um kanalfertige Varianten zu erstellen.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: 896fc25b-7f60-47b8-9264-2ef6b85d954c
source-git-commit: a31cd8ea0ae02a51efb748097c195d68dc8b554d
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---


# Auftrag zur Inhaltsoptimierung {#content-optimization-job}

Im Rahmen des Content Advisor-Agenten von [AEM transformiert &#x200B;](/help/ai-in-aem/agents/content-advisor/overview.md) Auftrag zur Inhaltsoptimierung die Art und Weise, wie Benutzende Assets verfeinern und anpassen, indem sie Anweisungen in natürlicher Sprache anwenden, um kanalfertige Varianten zu erstellen. Unabhängig davon, ob neue Ausgabedarstellungen erstellt, visuelle Eigenschaften angepasst, Hintergründe geändert oder Assets für bestimmte digitale Kanäle vorbereitet werden, interpretiert der Vorgang die Benutzerabsicht und führt komplexe Bearbeitungsaufgaben automatisch aus. Es funktioniert nahtlos mit [dem Auftrag zur Inhaltssuche“, &#x200B;](/help/ai-in-aem/agents/content-advisor/discovery.md) die gefundenen Assets zu nehmen und optimierte Varianten mithilfe von [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) zu erstellen, die Marken-, Kanal- und Kampagnenanforderungen ohne manuellen Design-Aufwand erfüllen.

Zu den wichtigsten Vorteilen des Auftrags zur Inhaltsoptimierung gehören:

* **Mühelose Asset-**: Konvertiert einfache, dialogorientierte Eingabeaufforderungen in präzise Bildoperationen wie Größenanpassung, Scharfzeichnung, Spiegelung oder Neufärbung, sodass keine speziellen Bearbeitungswerkzeuge mehr benötigt werden.

* **Kanaloptimierte Ausgaben**: Erstellt schnell Ausgabedarstellungen, die für bestimmte Plattformen wie Instagram-Stories, Webbanner oder andere Marketing-Touchpoints zugeschnitten sind, und stellt sicher, dass Assets zur sofortigen Verwendung bereit sind.

* **Skalierbare Creative-Verbesserung**: Wendet visuelle Anpassungen und Verbesserungen an, z. B. Änderungen im Hintergrund oder Grafiküberlagerungen, um kreative Workflows mit hohem Volumen zu unterstützen, ohne die Teamleistung zu verlangsamen.

* **[Nahtlose Zusammenarbeit mit dem Inhaltserkennungsauftrag](/help/ai-in-aem/agents/content-advisor/discovery.md)**: Baut auf den durch den Inhaltserkennungsauftrag identifizierten Assets auf und ermöglicht den durchgängigen Abruf und die Optimierung von Assets durch natürliche Konversation.

>[!IMPORTANT]
>
>KI-generierte Antworten können ungenau oder irreführend sein. Überprüfen Sie unbedingt die vorgeschlagenen Fehlerbehebungen und Antworten.
>
>Siehe auch [Benutzerhandbücher für die generative KI von Adobe Experience Cloud.](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html)

>[!VIDEO](https://video.tv.adobe.com/v/3480078)

## Voraussetzungen {#prerequisites-content-optimization-job}

So generieren Sie Varianten oder Optimierungen für Bild-Assets. Sie müssen über Folgendes verfügen:

* Eine gültige Dynamic Media-Lizenz

* Dynamic Media mit aktivierter OpenAPI in der AEM as a Cloud Service-Umgebung.

* Die Assets in [genehmigten Status](/help/assets/manage-organize-assets-view.md#manage-asset-status) in Ihrer AEM as a Cloud Service-Umgebung.

## Kompetenzen {#skills-content-optimization-job}

Der Auftrag zur Inhaltsoptimierung bietet die folgenden Fähigkeiten:

* **Verstehen Sie Absicht durch natürliche Sprache**

  Der Auftrag zur Inhaltsoptimierung interpretiert die Benutzerinteressen aus Eingabeaufforderungen in natürlicher Sprache und berücksichtigt den Kanal-, Kampagnen- und Zielgruppenkontext, um die relevantesten Optimierungsaktionen zu ermitteln.

* **Erzeugt dynamische Inhaltsvarianten**

  Der Auftrag zur Inhaltsoptimierung erstellt optimierte Varianten als dynamische URLs, die auf verschiedene Kanäle und Formattypen zugeschnitten sind.

* **Optimiert den Bildinhalt**

  Der Auftrag zur Inhaltsoptimierung wendet Verbesserungen wie Formatkonvertierung, Auflösungsanpassungen, Zuschnitt und Scharfzeichnung an, um die Bildqualität zu verbessern.

* **Asset-Optimierung mit mehreren Varianten**

  Der Auftrag zur Inhaltsoptimierung kann mithilfe einer einzigen natürlichen Sprachaufforderung mehrere optimierte Bildvarianten aus den vom Inhaltserkennungsauftrag zurückgegebenen Assets generieren, sodass Benutzende kanalfertige Ausgabedarstellungen schnell und effizient erstellen können.

## Personen {#personas-content-optimization-job}

Channel-Marketing-Experten, die Schlüsselrolle für den Auftrag zur Inhaltsoptimierung, können die richtigen hochauflösenden Quellinhalte auswählen und optimierte Formate anfordern, die auf ihre Kanäle und Zielgruppensegmente zugeschnitten sind.

Regionale Marketer und Agenturmitarbeiter können den Auftrag zur Inhaltsoptimierung auch verwenden, um schnell kanalfertige Bildvarianten zu generieren, die eine schnellere, konsistentere Inhaltserstellung unterstützen.

## Zugriff {#access-content-optimization-job}

Sie können über den KI-Assistenten auf den Inhaltsoptimierungsauftrag in AEM zugreifen. Melden Sie sich bei [`experience.adobe.com`](https://experience.adobe.com) an und Sie können mit dem KI-Assistenten interagieren, indem Sie Ihre Eingabeaufforderung in natürlicher Sprache mithilfe des `Ask AI Assistant anything` Felds angeben:

![Zugriff auf Inhaltsoptimierungsaufträge](/help/ai-in-aem/agents/content-advisor/assets/access-discovery-agent.png)

## Häufige Anwendungsfälle und Beispiel-Eingabeaufforderungen {#use-cases-prompts}

Verwenden Sie den Auftrag zur Inhaltsoptimierung, indem Sie über den Auftrag zur [Inhaltssuche“ nach den richtigen Assets suchen.](/help/ai-in-aem/agents/content-advisor/discovery.md) die relevanten Bilder angezeigt werden, können Benutzer direkt aus den Suchergebnissen optimierte oder kanalspezifische Varianten für ein oder mehrere Assets generieren. Dieser Workflow sorgt für hochwertige Eingaben und durchgängig bessere Optimierungsergebnisse. [Weitere Informationen finden Sie in der vollständigen Liste &#x200B;](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/) verfügbaren Optimierungen.

* **Erstellung von Ausgabedarstellungen mit hoher Auflösung**

  Der Auftrag kann neue Ausgabedarstellungen eines Assets mit einer bestimmten Auflösung und Qualitätsstufe generieren, sodass kanalbereite Varianten ohne manuelle Bearbeitung einfach vorbereitet werden können.


  Eingabeaufforderung für Beispiel:

  Erstellen Sie eine `2000px` Ausgabedarstellung `JPEG` mit `80%`.

  Suchen Sie mithilfe des [Inhaltssuchauftrags“ nach dem richtigen Asset &#x200B;](/help/ai-in-aem/agents/content-advisor/discovery.md) verwenden Sie dann bei mehreren Suchergebnissen die folgenden Eingabeaufforderungen:

  Erstellen Sie für das dritte Suchergebnis eine `2000px` Ausgabedarstellung `JPEG` mit `80%`.

  ODER

  Generieren Sie `Asset ID` eine Ausgabedarstellung von 2.000 Pixel `JPEG` einer `80%` Qualität

* **Bildverbesserung**

  Der Auftrag kann visuelle Verbesserungen anwenden, z. B. das Scharfzeichnen, um sicherzustellen, dass Assets gestochen scharf und klar definiert aussehen, bevor sie in Kampagnen verwendet werden.

  Eingabeaufforderung für Beispiel:

  Scharfzeichnen des Bildes.


* **Anpassungen der Hintergrundfarbe**

  Der Auftrag kann Hintergrundfarben in transparenten Assets aktualisieren oder ersetzen und markenspezifische Farbschemata oder kampagnengesteuerte visuelle Designs unterstützen.

  Eingabeaufforderung für Beispiel:

  Ändern Sie die Hintergrundfarbe des `PNG` in `#ff8932`.

* **Orientierungstransformationen**

  Der Auftrag kann visuelle Elemente spiegeln oder spiegeln, um sie an die Layout-Anforderungen oder die kreative Richtung anzupassen, ohne dass externe Bearbeitungswerkzeuge erforderlich sind.

  Eingabeaufforderung für Beispiel:

  Spiegeln Sie das Bild horizontal.

* **Kanaloptimierte Ausgabedarstellungen**

  Der Auftrag kann Ausgabedarstellungen erstellen, die auf plattformspezifische Anforderungen zugeschnitten sind, z. B. Instagram Stories, um sicherzustellen, dass Assets automatisch den Richtlinien für Format, Verhältnis und Qualität entsprechen.

  Eingabeaufforderung für Beispiele:

  Erstellen Sie eine Ausgabedarstellung für eine `Instagram` Story.

* **Markenüberlagerungen und Composite-Generierung**

  Der Auftrag kann Werbeggrafiken, Überlagerungen oder Abzeichen auf vorhandene Assets mit präziser Platzierung anwenden und so die schnelle Erstellung von kampagnenbereiten Composites unterstützen.

  Eingabeaufforderung für Beispiele:

  Überlagern Sie das Bild mit `30%` Rabattgrafiken über dem Werbebanner und platzieren Sie es `100px` von der Mitte.

  >[!NOTE]
  >
  >Die Überlagerungspositionen sind möglicherweise nicht genau.


## Optimierungsergebnisse {#content-optimization-job-results}

Wenn Sie eine Optimierungsaufforderung angeben, gibt der Auftrag zur Inhaltsoptimierung das erweiterte Asset zusammen mit praktischen Zugriffsoptionen je nach Asset-Typ zurück:

* **Bilder**: Die Antwort enthält eine Miniaturvorschau und Optionen zum Öffnen der Dynamic Media-URL oder zum Herunterladen des optimierten Bildes.

* **PDF-Dokumente**: Die Antwort enthält eine Miniaturvorschau und Optionen zum Öffnen der Dynamic Media-URL oder zum Herunterladen der optimierten Datei.

* **Videos**: Die Antwort bietet Optionen zum Öffnen der Dynamic Media-URL oder zum Herunterladen des optimierten Videos.

![Ergebnisse der Inhaltsoptimierung](/help/ai-in-aem/agents/content-advisor/assets/download-content-optimization.png)

Diese Ergebnisse erleichtern die Überprüfung der optimierten Ausgabe und ihre sofortige Verwendung in nachgelagerten Kanälen oder Workflows.


## Einschränkungen {#limitations-content-optimization}

* Das Festlegen der Hintergrundfarbe wird nicht unterstützt.

<!--


## Prompting best Practices {#prompting-best-practices-content-optimization-job}

The following are some prompting best practices:

* Be explicit about the enhancement you want the content optimization job to apply. Clearly state the transformation or adjustment you expect. Precise instructions help the agent produce accurate and predictable results. For example, Instead of `Make it good quality`, specify `Create a JPEG image with 90% quality`.

* Provide detailed parameters whenever possible. The more context you give, such as dimensions, format, quality, placement, or color values, the more tailored the output is.

-->
