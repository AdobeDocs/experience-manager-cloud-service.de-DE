---
title: Seiteneditor und universeller Editor
description: Der Seiteneditor wird weiterhin von Adobe unterstützt, aber der universelle Editor bietet spannende Möglichkeiten für Ihre neuen Projekte.
feature: Developing
role: Admin, Architect, Developer
exl-id: 0a13fb52-623e-4aff-b254-186d8d117e4d
source-git-commit: fd52e51c336e65ae698c5102cbe00b90e7038b5e
workflow-type: tm+mt
source-wordcount: '1068'
ht-degree: 99%

---

# Seiteneditor und universeller Editor {#page-editor-universal-editor}

Der Seiteneditor wird weiterhin von Adobe unterstützt, aber der universelle Editor bietet spannende Möglichkeiten für Ihre neuen Projekte.

## Hintergrund {#background}

Adobe führte den [universellen Editor](/help/implementing/universal-editor/introduction.md) im Jahr 2024 als optimierten Editor mit einem modernen JavaScript-basierten Entwicklungsansatz ein. Der universelle Editor ist Adobes Vision eines nahtlosen und erweiterbaren Erlebnisses beim Erstellen visueller Inhalte.

Aufgrund des Funktionsumfangs des [Seiteneditors](/help/sites-cloud/authoring/page-editor/introduction.md) und der unzähligen Projekte, die im Laufe der Jahre in ihn investierten, unterstützt Adobe den Seiteneditor weiterhin vollständig, Innovationen konzentrieren sich nun jedoch auf den universellen Editor.

## Empfehlung {#recommendation}

Trotz der schnellen Entwicklung besteht weiterhin eine Funktionslücke zwischen dem universellen Editor und dem Seiteneditor ([ein Funktionsvergleich ist im nächsten Abschnitt zu finden](#feature-comparison)).

Als Faustregeln gelten:

* **Neue Projekte** sollten standardmäßig den universellen Editor verwenden.
* **Vorhandene Projekte** sollten weiterhin den Seiteneditor verwenden und den Einsatz des universellen Editors erwägen, wenn mit der Nutzung von Edge Delivery oder Headless begonnen wird.

**Welchen Editor Sie auswählen, sollte vollständig von den Anforderungen Ihres individuellen Projekts abhängen.**

## Funktionsvergleich {#feature-comparison}

Da die Funktionslücke zwischen den beiden Editoren ständig kleiner wird, informieren Sie sich stets über die neuesten Entwicklungen in den [Versionshinweisen des universellen Editors](/help/release-notes/universal-editor/current.md).

### Bereitstellung {#delivery}

|  | Seiteneditor | Anmerkungen | Universeller Editor | Anmerkungen |
|---|---|---|---|---|
| [Veröffentlichungsbereitstellung](/help/sites-cloud/authoring/author-publish.md) | [!BADGE Verfügbar]{type=Positive} | Empfohlen für die Verwendung mit den Kernkomponenten und herkömmlichen AEM-Projekten | [!BADGE Nicht verfügbar]{type=Negative} | Herkömmliche AEM-Seiten basieren in der Regel auf mehreren spezifischen Funktionen des Seiteneditors, die mit dem universellen Editor nur schwer unverändert repliziert werden können. |
| [Edge Delivery](/help/edge/overview.md) | [!BADGE Nicht verfügbar]{type=Negative} |  | [!BADGE Verfügbar]{type=Positive} |  |
| [Headless-Bereitstellung](/help/headless/introduction.md) | [!BADGE Teilweise verfügbar]{type=Caution} | Nur mit [dem SPA-Editor](/help/implementing/developing/hybrid/introduction.md) der zugunsten des universellen Editors [eingestellt](/help/implementing/developing/hybrid/spa-editor-deprecation.md) wurde | [!BADGE Verfügbar]{type=Positive} | Der universelle Editor ermöglicht es Entwickelnden, ihre eigene Web-App zu verwenden, ohne spezielle Framework-Anforderungen oder Implementierungsbeschränkungen aufzuerlegen. |

### Persistenz {#persistence}

|  | Seiteneditor | Anmerkungen | Universeller Editor | Anmerkungen |
|---|---|---|---|---|
| Bearbeiten der Seitenkomponenten | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} |  |
| Bearbeiten von [Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md) | [!BADGE Nicht verfügbar]{type=Negative} |  | [!BADGE Verfügbar]{type=Positive} | Einschließen neuer Fragmente und Neuanordnung der Fragmente |

### Funktionen {#capabilities}

|  | Seiteneditor | Anmerkungen | Universeller Editor | Anmerkungen |
|---|---|---|---|---|
| Seitenvorlagen | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} | Der universelle Editor ist unabhängig vom verwendeten Vorlagensystem. Das typische Implementierungsmuster begünstigt jedoch entwicklerdefinierte Vorlagen, da Entwicklerinnen und Entwickler in modernen Frontend-Tools deutlich einfacher Vorlagenlogik direkt im Code definieren und verwalten können. |
| WYSIWYG-Bearbeitung | [!BADGE Verfügbar]{type=Positive} | Auf Seiten beschränkt | [!BADGE Verfügbar]{type=Positive} | Unterstützung von Seiten und Inhaltsfragmenten |
| [Varianten generieren](/help/generative-ai/generate-variations.md) | [!BADGE Nicht verfügbar]{type=Negative} |  | [!BADGE Verfügbar]{type=Positive} | [Verfügbar als Erweiterung](/help/implementing/universal-editor/extending.md) |
| Neuen Block einfügen | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} |  |
| Block neu anordnen | [!BADGE Verfügbar]{type=Positive} | Möglich mit Drag-and-Drop im Kontext, aber nicht im Seiten-Panel „Baumansicht“ | [!BADGE Verfügbar]{type=Positive} | Möglich per Drag-and-Drop im Seiten-Panel „Baumansicht“, aber noch nicht im Kontext (geplant) |
| Block ausschneiden/kopieren/einfügen | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Nicht verfügbar]{type=Negative} | Geplant |
| Stile anwenden | [!BADGE Verfügbar]{type=Positive} | Stile können mithilfe des [Stilsystems](/help/sites-cloud/authoring/page-editor/style-system.md) auf  Komponenten angewendet werden. | [!BADGE Verfügbar]{type=Positive} | Stile können mit den Eigenschaften von regulären Komponenten (oder Inhaltsfragmenten) angewendet werden. Der universelle Editor verfügt nicht über dieselbe Stilauswahl. Sie können jedoch mit einem multiselect-Widget ein sehr ähnliches Benutzererlebnis erzielen. |
| Layout anwenden | [!BADGE Verfügbar]{type=Positive} | Sites muss das [responsive Raster von AEM](/help/implementing/developing/introduction/responsive-design.md) implementieren, damit Autorinnen und Autoren die Größe von Komponenten über drei vordefinierte Haltepunkte hinweg ändern können. | [!BADGE Verfügbar]{type=Positive} | Layouts können mit Eigenschaften von regulären Komponenten (oder Inhaltsfragmenten) angewendet werden, das responsive Raster wird jedoch nicht unterstützt. |
| Rückgängig/Wiederholen | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} |  |
| Veröffentlichen (auch als Vorschau) | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} |  |
| [Workflow starten](/help/sites-cloud/authoring/workflows/overview.md) | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} | Verfügbar als Erweiterung |
| Kommentieren | [!BADGE Verfügbar]{type=Positive} | [Anmerkungen](/help/sites-cloud/authoring/page-editor/annotations.md) verwenden | [!BADGE Nicht verfügbar]{type=Negative} | Geplant |
| Workfront-Integration | [!BADGE Nicht verfügbar]{type=Negative} |  | [!BADGE Verfügbar]{type=Positive} | Verfügbar als Erweiterung |
| [MSM und Launches](/help/sites-cloud/administering/msm-and-translation.md) | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} | Verfügbar für Seiten als Erweiterung |
| Experimente und Personalisierung | [!BADGE Verfügbar]{type=Positive} | [Zielmodus](/help/sites-cloud/authoring/personalization/targeted-content.md) verwenden | [!BADGE Verfügbar]{type=Positive} | Verfügbar als Erweiterung für Edge Delivery Services |
| Inhaltsstruktur | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} | Ermöglicht auch die Neuanordnung in der Baumstruktur |
| Gerätesimulation | [!BADGE Verfügbar]{type=Positive} | [Konfigurierte Geräte können simuliert werden](/help/sites-cloud/administering/responsive-layout.md), Benutzende können jedoch nicht manuell die Bildschirmabmessungen für die Simulation ändern. | [!BADGE Verfügbar]{type=Positive} | [Alle zu simulierenden Bildschirmabmessungen können manuell eingegeben werden](/help/sites-cloud/authoring/universal-editor/navigation.md#emulator), Standardhaltepunkte können jedoch nicht konfiguriert werden. |
| [Seitensperren](/help/sites-cloud/authoring/sites-console/managing-pages.md) | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} | Berücksichtigt den in der Sites-Konsole festgelegten Sperrstatus mit der im Editor verfügbaren Erweiterung zum Sperren/Entsperren von Seiten |
| [Seiteneigenschaften](/help/sites-cloud/authoring/sites-console/edit-page-properties.md) | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} | Verfügbar über Sites Admin, einschließlich Erweiterung zum Zugriff auf die Eigenschaften von Seiten über den Editor |
| Mehrfachfeldeigenschaften | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Nicht verfügbar]{type=Negative} | Geplant |
| [Remote-DAM](/help/assets/dynamic-media-open-apis-overview.md) | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} |  |
| [Seitenversionierung](/help/sites-cloud/authoring/sites-console/page-versions.md) | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} |  |
| [TimeWarp](/help/sites-cloud/authoring/sites-console/page-versions.md#timewarp) und [Differenzansicht](/help/sites-cloud/authoring/sites-console/page-diff.md) | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Nicht verfügbar]{type=Negative} | Geplant |
| In Admin anzeigen | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} | Verfügbar als Erweiterung für Seiten |
| Seitenstatus anzeigen | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Nicht verfügbar]{type=Negative} | Verfügbar in der Sites-Konsole |
| Erweiterbarkeit | [!BADGE Verfügbar]{type=Positive} | Als AEM-Überlagerungen | [!BADGE Verfügbar]{type=Positive} | Als klar definierte Erweiterungspunkte mit dem App Builder ohne umfangreiches AEM-spezifisches Wissen |

## Verwenden des universellen Editors {#adopt-ue}

Der universelle Editor bietet viele Vorteile und eignet sich daher sehr gut für neue Projekte.

* **Visuelle Bearbeitung:** Wie beim Seiteneditor können Autorinnen und Autoren Inhalte direkt in der Vorschau bearbeiten und sehen sofort, wie sich ihre Änderungen auf das Besuchererlebnis auswirken.
* **Zukunftssicher:** AEMs Roadmap priorisiert den universellen Editor als visuellen Editor. Indem Sie ihn übernehmen, wird der Zugriff auf die neuesten Innovationen und Verbesserungen sichergestellt.
* **Einfachere Integration:** Für die Verwendung des universellen Editors ist kein AEM-spezifisches SDK erforderlich, wodurch die Festlegung auf bestimmte Technologiedienste verringert wird.
* **Eigene App einbringen:** Der universelle Editor unterstützt jedes Web-Framework und jede Architektur, sodass ein Übernehmen ohne komplexe Umgestaltung möglich ist.
* **Erweiterbarkeit:** Der universelle Editor profitiert von einem robusten [Erweiterungs-Framework](/help/implementing/universal-editor/extending.md), einschließlich Integrationen mit GenAI, Workfront und mehr.

### Migration zum universellen Editor {#migrate-ue}

Es gibt keinen direkten Migrationspfad vom Seiteneditor zum universellen Editor. Dies liegt an den grundlegenden Unterschieden zwischen den beiden Technologien.

* Durch den universellen Editor werden keine Funktionen wie der Vorlageneditor, das Stilsystem oder das responsive Raster wieder neu eingeführt.
   * Diese Anwendungsfälle können jetzt effizienter mit Lean-Frontend-CSS und JavaScript in Edge Delivery Services- oder Headless-Projekten bearbeitet werden.
* Da der universelle Editor ein Editor-as-a-Service ist, ist das Einfügen von CSS oder JS in die Komponentendialogfelder beim Implementieren nicht zulässig.
   * Dies verhindert eine automatische Konvertierung von Komponentendialogfeldern aus dem Seiten-Editor.
   * Dies wirkt sich auf viele Bereiche der Dialogfelder aus, z. B. auf benutzerdefinierte Widgets, Feldvalidierungen, Regeln zum Ein-/Ausblenden und vorlagenbasierte Anpassungen.
      * Solche Funktionen sind weiterhin möglich, im universellen Editor werden sie jedoch durch Konfiguration umgesetzt und nicht durch in Dialogfeldern bereitgestelltes benutzerdefiniertes JavaScript.

Zwar kann der universelle Editor technisch die Bearbeitung von Seiten für herkömmliche AEM-Projekte (z. B. aus den Kernkomponenten) ermöglichen, doch diese Sites sind in der Regel auf mehrere Seiteneditor-spezifische Funktionen wie das Stilsystem, das responsive Raster, bearbeitbare Vorlagen und benutzerdefiniertes JavaScript in Dialogfeldern angewiesen.

Da der universelle Editor einem optimierten und modernen Ansatz folgt, der diese alten Funktionen nicht unterstützt, würde die Migration solcher Sites eine erhebliche Überarbeitung erfordern. Aus diesem Grund wird die **Migration von Seiteneditor-Sites in den universellen Editor nur für Projekte empfohlen, die auf Edge Delivery Services umgestellt werden.**
