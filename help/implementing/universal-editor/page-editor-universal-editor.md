---
title: Seiten-Editor und universeller Editor
description: Der Seiteneditor wird weiterhin von Adobe unterstützt, aber der universelle Editor bietet aufregende Möglichkeiten für Ihre neuen Projekte.
feature: Developing
role: Admin, Architect, Developer
exl-id: 0a13fb52-623e-4aff-b254-186d8d117e4d
source-git-commit: fd52e51c336e65ae698c5102cbe00b90e7038b5e
workflow-type: tm+mt
source-wordcount: '1068'
ht-degree: 15%

---

# Seiten-Editor und universeller Editor {#page-editor-universal-editor}

Der Seiteneditor wird weiterhin von Adobe unterstützt, aber der universelle Editor bietet aufregende Möglichkeiten für Ihre neuen Projekte.

## Hintergrund {#background}

Adobe führte den [universellen Editor](/help/implementing/universal-editor/introduction.md) im Jahr 2024 als optimierten Editor ein, der einen modernen JavaScript-basierten Entwicklungsansatz verwendete. Der universelle Editor ist Adobes Vision für ein nahtloses und erweiterbares Erlebnis beim Erstellen visueller Inhalte.

In Anerkennung der [ Funktionen des ](/help/sites-cloud/authoring/page-editor/introduction.md)-Editors und der unzähligen Projekte, in die er im Laufe des langen Bestehens von AEM investiert hat, unterstützt Adobe weiterhin den Seiteneditor vollständig, obwohl sich die Innovation auf den universellen Editor konzentrieren wird.

## Empfehlung {#recommendation}

Trotz der schnellen Reduzierung besteht weiterhin eine Funktionslücke zwischen dem universellen Editor und dem Seiteneditor ([ein Funktionsvergleich ist im nächsten Abschnitt zu finden](#feature-comparison)).

Als Faustregel gilt:

* **Neue Projekte** sollte standardmäßig auf die Verwendung des universellen Editors eingestellt sein.
* **Vorhandene Projekte** sollten weiterhin den Seiteneditor verwenden und den universellen Editor berücksichtigen, wenn Sie Edge Delivery oder Headless starten.

**Welchen Editor Sie auswählen, sollte vollständig von den Anforderungen Ihres individuellen Projekts gesteuert werden.**

## Funktionsvergleich {#feature-comparison}

Da die Funktionslücke zwischen den beiden Editoren ständig kleiner wird, lesen Sie in den [Versionshinweisen des universellen Editors](/help/release-notes/universal-editor/current.md) die neuesten Entwicklungen.

### Bereitstellung {#delivery}

|  | Seiteneditor | Anmerkungen | Universeller Editor | Anmerkungen |
|---|---|---|---|---|
| [Versand veröffentlichen](/help/sites-cloud/authoring/author-publish.md) | [!BADGE Verfügbar]{type=Positive} | Empfohlen für die Verwendung mit den Kernkomponenten und herkömmlichen AEM-Projekten | [!BADGE nicht verfügbar]{type=Negative} | Herkömmliche AEM-Seiten basieren in der Regel auf mehreren Seiteneditor-spezifischen Funktionen, die mit dem universellen Editor nur schwer unverändert repliziert werden können. |
| [Edge Delivery](/help/edge/overview.md) | [!BADGE nicht verfügbar]{type=Negative} |  | [!BADGE Verfügbar]{type=Positive} |  |
| [Headless-Bereitstellung](/help/headless/introduction.md) | [!BADGE Teilweise verfügbar]{type=Caution} | Nur mit [dem SPA-Editor](/help/implementing/developing/hybrid/introduction.md) der [veraltet](/help/implementing/developing/hybrid/spa-editor-deprecation.md) zugunsten des universellen Editors eingestellt wurde | [!BADGE Verfügbar]{type=Positive} | Der universelle Editor ermöglicht es Entwicklern, ihre eigene Web-App zu verwenden, ohne spezielle Framework-Anforderungen oder Implementierungsbeschränkungen aufzuerlegen. |

### Persistenz {#persistence}

|  | Seiteneditor | Anmerkungen | Universeller Editor | Anmerkungen |
|---|---|---|---|---|
| Bearbeiten von Seitenkomponenten | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} |  |
| Bearbeiten [Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md) | [!BADGE nicht verfügbar]{type=Negative} |  | [!BADGE Verfügbar]{type=Positive} | Einschließen neuer Fragmente und Neuanordnung der Fragmente |

### Funktionen {#capabilities}

|  | Seiteneditor | Anmerkungen | Universeller Editor | Anmerkungen |
|---|---|---|---|---|
| Seitenvorlagen | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} | Der universelle Editor ist unabhängig vom verwendeten Vorlagensystem. Das typische Implementierungsmuster begünstigt jedoch Entwicklerdefinierte Vorlagen, da moderne Frontend-Tools es Entwicklerinnen und Entwicklern viel einfacher machen, Vorlagenlogik direkt im Code zu definieren und zu verwalten. |
| WYSIWYG-Bearbeitung | [!BADGE Verfügbar]{type=Positive} | Auf Seiten beschränkt | [!BADGE Verfügbar]{type=Positive} | Unterstützende Seiten und Inhaltsfragmente |
| [Varianten generieren](/help/generative-ai/generate-variations.md) | [!BADGE nicht verfügbar]{type=Negative} |  | [!BADGE Verfügbar]{type=Positive} | [Verfügbar als Erweiterung](/help/implementing/universal-editor/extending.md) |
| Neuen Block einfügen | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} |  |
| Block neu anordnen | [!BADGE Verfügbar]{type=Positive} | Möglich mit Drag-and-Drop im Kontext, aber nicht im Seitenbereich „Baumansicht“ | [!BADGE Verfügbar]{type=Positive} | Möglich per Drag-and-Drop im Seitenbereich „Baumansicht“, aber noch nicht im Kontext (geplant) |
| Block ausschneiden/kopieren/einfügen | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE nicht verfügbar]{type=Negative} | Geplant |
| Anwenden von Stilen | [!BADGE Verfügbar]{type=Positive} | Stile können mithilfe des Stilsystems auf [ Komponenten angewendet werden](/help/sites-cloud/authoring/page-editor/style-system.md) | [!BADGE Verfügbar]{type=Positive} | Stile können mit den Eigenschaften regulärer Komponenten (oder Inhaltsfragmente) angewendet werden. Die gleiche Stilauswahl ist im universellen Editor nicht verfügbar, jedoch kann mit einem multiselect-Widget eine sehr ähnliche Benutzeroberfläche erreicht werden. |
| Layout anwenden | [!BADGE Verfügbar]{type=Positive} | Sites muss das [responsive Raster von AEM implementieren](/help/implementing/developing/introduction/responsive-design.md) damit Autorinnen und Autoren die Größe von Komponenten über drei vordefinierte Haltepunkte hinweg ändern können. | [!BADGE Verfügbar]{type=Positive} | Layouts können mithilfe regulärer Komponenten- (oder Inhaltsfragment)-Eigenschaften angewendet werden, das responsive Raster wird jedoch nicht unterstützt. |
| Rückgängig-Wiederholen | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} |  |
| Veröffentlichen (auch in der Vorschau) | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} |  |
| [Workflow starten](/help/sites-cloud/authoring/workflows/overview.md) | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} | Verfügbar als Erweiterung |
| Kommentieren | [!BADGE Verfügbar]{type=Positive} | Verwenden von [Anmerkungen](/help/sites-cloud/authoring/page-editor/annotations.md) | [!BADGE nicht verfügbar]{type=Negative} | Geplant |
| Workfront-Integration | [!BADGE nicht verfügbar]{type=Negative} |  | [!BADGE Verfügbar]{type=Positive} | Verfügbar als Erweiterung |
| [MSM und Launches](/help/sites-cloud/administering/msm-and-translation.md) | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} | Verfügbar für Seiten als Erweiterung |
| Experimentieren und Personalisieren | [!BADGE Verfügbar]{type=Positive} | Verwenden [Target-Modus](/help/sites-cloud/authoring/personalization/targeted-content.md) | [!BADGE Verfügbar]{type=Positive} | Verfügbar als Erweiterung für Edge Delivery Services |
| Inhaltsstruktur | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} | Ermöglicht auch die Neuanordnung innerhalb der Baumstruktur |
| Simulation von Geräten | [!BADGE Verfügbar]{type=Positive} | [Konfigurierte Geräte können simuliert werden](/help/sites-cloud/administering/responsive-layout.md) der Benutzer kann jedoch nicht manuell andere Bildschirmabmessungen eingeben, um sie zu simulieren. | [!BADGE Verfügbar]{type=Positive} | [Alle zu simulierenden Bildschirmabmessungen können manuell eingegeben werden](/help/sites-cloud/authoring/universal-editor/navigation.md#emulator) Standardhaltepunkte können jedoch nicht konfiguriert werden. |
| [Seitensperre](/help/sites-cloud/authoring/sites-console/managing-pages.md) | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} | Berücksichtigt den in der Sites-Konsole festgelegten Sperrstatus mit der Erweiterung, die zum Sperren/Entsperren von Seiten im Editor verfügbar ist |
| [Seiteneigenschaften](/help/sites-cloud/authoring/sites-console/edit-page-properties.md) | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} | Verfügbar von der Site-Admin mit der Erweiterung , um auch über den Editor auf die Eigenschaften von Seiten zuzugreifen |
| Eigenschaften für mehrere Felder | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE nicht verfügbar]{type=Negative} | Geplant |
| [Remote-DAM](/help/assets/dynamic-media-open-apis-overview.md) | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} |  |
| [Seitenversionierung](/help/sites-cloud/authoring/sites-console/page-versions.md) | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} |  |
| [TimeWarp](/help/sites-cloud/authoring/sites-console/page-versions.md#timewarp) und [Diff View](/help/sites-cloud/authoring/sites-console/page-diff.md) | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE nicht verfügbar]{type=Negative} | Geplant |
| In Admin anzeigen | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE Verfügbar]{type=Positive} | Verfügbar als Erweiterung für Seiten |
| Anzeigen des Seitenstatus | [!BADGE Verfügbar]{type=Positive} |  | [!BADGE nicht verfügbar]{type=Negative} | In der Sites-Konsole verfügbar |
| Erweiterbarkeit | [!BADGE Verfügbar]{type=Positive} | Als AEM-Überlagerungen | [!BADGE Verfügbar]{type=Positive} | Als klar definierte Erweiterungspunkte unter Verwendung der App Builder und sehr wenig AEM-spezifisches Wissen |

## Übernehmen des universellen Editors {#adopt-ue}

Der universelle Editor bietet viele Vorteile und ist daher eine hervorragende Lösung für neue Projekte.

* **Visuelle Bearbeitung** Wie beim Seiteneditor können Autoren Inhalte direkt in der Vorschau bearbeiten und sofort sehen, wie sich ihre Änderungen auf das Besuchererlebnis auswirken.
* **Zukunftssicher:** AEMs Roadmap priorisiert den universellen Editor als visuellen Editor. Indem Sie ihn übernehmen, wird der Zugriff auf die neuesten Innovationen und Verbesserungen sichergestellt.
* **Einfachere Integration:** Für die Verwendung des universellen Editors ist kein AEM-spezifisches SDK erforderlich, wodurch die Festlegung auf bestimmte Technologiedienste verringert wird.
* **Eigene App einbringen:** Der universelle Editor unterstützt jedes Web-Framework und jede Architektur, sodass ein Übernehmen ohne komplexe Umgestaltung möglich ist.
* **Erweiterbarkeit:** Der universelle Editor profitiert von einem robusten [Erweiterungs-Framework](/help/implementing/universal-editor/extending.md), einschließlich Integrationen mit GenAI, Workfront und mehr.

### Migration zum universellen Editor {#migrate-ue}

Es gibt keinen direkten Migrationspfad vom Seiteneditor zum universellen Editor. Dies liegt an den grundlegenden Unterschieden zwischen den beiden Technologien.

* Durch den universellen Editor werden keine Funktionen wie der Vorlageneditor, das Stilsystem oder das responsive Raster wieder neu eingeführt.
   * Diese Anwendungsfälle können jetzt effizienter mit Lean-Frontend-CSS und JavaScript in Edge Delivery Services oder Headless-Projekten bearbeitet werden.
* Da der universelle Editor ein Editor-as-a-Service ist, kann er es Implementierern nicht erlauben, CSS oder JS in die Komponentendialogfelder einzufügen.
   * Dies verhindert eine automatische Konvertierung von Komponentendialogfeldern aus dem Seiten-Editor.
   * Dies wirkt sich auf viele Bereiche der Dialogfelder aus, z. B. auf benutzerdefinierte Widgets, Feldvalidierungen, Regeln zum Ein-/Ausblenden und vorlagenbasierte Anpassungen.
      * Obwohl solche Funktionen weiterhin möglich sind, löst der universelle Editor sie durch Konfiguration, anstatt durch benutzerdefinierte JavaScript, die in Dialogfeldern bereitgestellt werden.

Während der universelle Editor die Bearbeitung von Seiten für herkömmliche AEM-Projekte (z. B. aus den Kernkomponenten) technisch aktivieren kann, sind diese Websites in der Regel auf mehrere Seiteneditor-spezifische Funktionen wie das Stilsystem, das responsive Raster, bearbeitbare Vorlagen und benutzerdefiniertes JavaScript in Dialogfeldern angewiesen.

Da der universelle Editor einem rationelleren, modernen Ansatz folgt, der diese alten Funktionen nicht unterstützt, würde die Migration solcher Sites eine erhebliche Überarbeitung erfordern. Aus diesem Grund wird **Migrieren von Seiteneditor-Sites in den universellen Editor nur für Projekte empfohlen, die auf Edge Delivery Services umgestellt werden.**
