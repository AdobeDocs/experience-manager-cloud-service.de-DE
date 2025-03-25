---
title: Einstellung des SPA-Editors
description: Auch wenn der SPA-Editor von Adobe weiterhin unterstützt wird, erfahren Sie, was die Einstellung für Ihr Projekt bedeutet und welche Optionen Sie für zukünftige Projekte haben.
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 7bff178eabdf7e0d89e7195be6ca109db19ee655
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 2%

---


# Einstellung des SPA-Editors {#spa-editor-deprecation}

Auch wenn der SPA-Editor von Adobe weiterhin unterstützt wird, erfahren Sie, was die Einstellung für Ihr Projekt bedeutet und welche Optionen Sie für zukünftige Projekte haben.

## Zusammenfassung {#summary}

Adobe hat den SPA-Editor mit [Version 2025.01 von AEM as a Cloud Service veraltet, was ](/help/release-notes/release-notes-cloud/2025/release-notes-2025-1-0.md#spa-editor) bedeutet, dass an seinen SDKs keine weiteren Verbesserungen oder Aktualisierungen vorgenommen werden. Adobe empfiehlt Ihnen die Verwendung [universellen Editors](/help/implementing/universal-editor/introduction.md) für alle neuen Projekte, um die neuesten Innovationen von AEM nutzen zu können.

## Details zur Einstellung {#details}

Die Einstellung des SPA-Editors **bedeutet keine sofortige Entfernung** und wenn Sie bereits Implementierungen haben, **können Sie ihn so lange verwenden, wie er Ihren Anforderungen entspricht.Beachten Sie** jedoch die folgenden Auswirkungen der Einstellung.

* Künftig wird Adobe nur noch P1- und P2-Probleme und Sicherheitslücken beheben.
* An den SDKs werden keine weiteren Entwicklungen, Verbesserungen oder Aktualisierungen vorgenommen.

Die Einstellung bedeutet, dass die folgenden SDKs jetzt eingefroren sind.

* [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype/)
* [AEM-SPA-Projekt-Kern](https://github.com/adobe/aem-spa-project-core)
* [AEM-SPA-Seitenmodell-Manager](https://github.com/adobe/aem-spa-page-model-manager)
* [AEM-SPA-Komponentenzuordnung](https://github.com/adobe/aem-spa-component-mapping)
* [AEM SPA React Editable Components](https://github.com/adobe/aem-react-editable-components)
   * [AEM React-Kernkomponenten](https://github.com/adobe/aem-react-core-wcm-components)
   * [AEM React-Kernkomponenten-Basis](https://github.com/adobe/aem-react-core-wcm-components-base)
   * [AEM React-Kernkomponenten-SPA](https://github.com/adobe/aem-react-core-wcm-components-spa)
   * [Beispiele für AEM React-Kernkomponenten](https://github.com/adobe/aem-react-core-wcm-components-examples)
* [Bearbeitbare AEM SPA Angular-Komponenten](https://github.com/adobe/aem-angular-editable-components)
   * [AEM Angular-Kernkomponenten](https://github.com/adobe/aem-angular-core-wcm-components)
   * Basis der [AEM Angular-Kernkomponenten](https://github.com/adobe/aem-angular-core-wcm-components-base)
   * [AEM Angular-Kernkomponenten-SPA](https://github.com/adobe/aem-angular-core-wcm-components-spa)
   * [Beispiele für AEM Angular-Kernkomponenten](https://github.com/adobe/aem-angular-core-wcm-components-examples)
* [Bearbeitbare AEM SPA-Vue-Komponenten](https://github.com/mavicellc/aem-vue-editable-components)

## Alternativen zum SPA-Editor {#alternatives}

Der am besten geeignete Ersatz für den SPA-Editor hängt von Ihren Projektanforderungen ab.

* **[Der universelle Editor](/help/edge/wysiwyg-authoring/authoring.md)** ist der beste direkte Ersatz für den SPA-Editor.
   * Der universelle Editor ist ebenfalls ein visueller Editor und wurde speziell für entkoppelte Implementierungen entwickelt, wobei die gesamte Erfahrung von Adobe mit dem SPA-Editor integriert wurde.
   * Der universelle Editor wurde ebenfalls [für AEM 6.5](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction) (mit Version 2024.11.05 von AEM 6.5) veröffentlicht und unterstützt daher neben Cloud Services auch AMS- und On-Premise-Anwendungsfälle.
* **[Der Inhaltsfragment-Editor](/help/assets/content-fragments/content-fragments-managing.md)** ist eine Alternative für diejenigen, die einen formularbasierten Editor bevorzugen.
   * Der Inhaltsfragment-Editor ist am besten geeignet, wenn Ihr Inhalt als Inhaltsfragmente und nicht als Seiten strukturiert ist.

Die Strukturierung von Inhalten mit Inhaltsfragmenten schließt die Verwendung des universellen Editors als visueller Editor nicht aus. Beide Editoren können zusammen verwendet werden.

## Migration zum universellen Editor {#migrate-ue}

Der universelle Editor bietet viele Vorteile, was die Migration zu ihm zu einer großartigen Lösung für neue Projekte macht.

* **Visuelle Bearbeitung:** wie beim SPA-Editor können Autoren Inhalte direkt in der Vorschau bearbeiten und sofort sehen, wie sich ihre Änderungen auf das Besuchererlebnis auswirken.
* **Zukunftssicher:** AEMS Roadmap priorisiert den universellen Editor als visuellen Editor. Durch die Übernahme wird der Zugriff auf die neuesten Innovationen und Verbesserungen sichergestellt.
* **Einfachere Integration:** Für die Verwendung des universellen Editors ist keine AEM-spezifische SDK erforderlich, wodurch die Bindung an den Technologie-Stack verringert wird.
* **Eigene App mitbringen:** Der universelle Editor unterstützt jedes Web-Framework oder jede Architektur, sodass eine Übernahme ohne komplexe Umgestaltung möglich ist.
* **Erweiterbarkeit:** Der universelle Editor profitiert von einem robusten [Erweiterungs-Framework](/help/implementing/universal-editor/extending.md) einschließlich Integrationen mit GenAI, Workfront und mehr.

Es gibt keinen direkten Migrationspfad vom SPA-Editor zum universellen Editor. Dies ist auf grundlegende Unterschiede zwischen den beiden Technologien zurückzuführen.

* Der universelle Editor führt keine Funktionen wie den Vorlageneditor, das Stilsystem oder das responsive Raster wieder ein.
   * Diese Anwendungsfälle können jetzt effizienter mit Lean-Frontend-CSS und -JS in Edge Delivery Services oder Headless-Projekten bearbeitet werden.
* Da der universelle Editor ein Editor-as-a-Service ist, kann er es Implementierern nicht erlauben, CSS oder JS in die Komponentendialogfelder einzufügen.
   * Dies verhindert eine automatische Konvertierung von Komponentendialogfeldern aus dem Seiteneditor.
   * Dies wirkt sich auf viele Bereiche der Dialogfelder aus, z. B. auf benutzerdefinierte Widgets, Feldüberprüfung, Regeln zum Ein-/Ausblenden und vorlagenbasierte Anpassungen.

Vor dem Hintergrund dieser technischen Unterschiede lautet die Empfehlung von Adobe wie folgt:

* Vorhandene SPA-Editor-Sites bleiben so, wie sie sind, da die Unterstützung fortgesetzt wird.
* Verwenden Sie den universellen Editor für alle neuen Entwicklungen, einschließlich neuer Websites, Abschnitte oder Seiten.

Beachten Sie, dass es zwar keine direkte Implementierung bestimmter SPA-Editor-Funktionen im universellen Editor gibt, es jedoch neue Möglichkeiten gibt, dieselben Probleme mit der neuen Flexibilität des universellen Editors zu lösen.

## Vergleich des SPA-Editors und des universellen Editors {#spa-vs-ue}

Der universelle Editor bietet Implementierern von Web-Anwendungen viel mehr Freiheit, wie in diesem Diagramm veranschaulicht.

![Vergleich der Architekturen des universellen Editors und des SPA-Editors](assets/spa-editor-vs-ue.png)

|  | SPA-Editor | Universeller Editor |
|---|---|---|
| **Themen** | Das Programm muss das Layout mit dem Raster-CSS von AEM implementieren. | Die App kann für das Layout jede moderne CSS-Technik verwenden. |
| **Rendering** | Die App muss der Routing-Struktur des SPA-Editors folgen. | App kann frei implementiert werden, ohne dass auferlegte Regeln oder Muster folgen. |
| **SDK** | Die Implementierung muss die SDK eng integrieren. | Auf der Autorenebene lädt die App einfach `corlib.js` und weist den universellen Editor über HTML-Anmerkungen an. |
| **Framework** | Die App muss eine unterstützte Version von React oder Angular verwenden. | Die App kann jedes Framework oder jede Architektur verwenden. |
| **Hosting** | Die App muss auf der AEM-Domain gehostet werden. | App kann vollständig entkoppelt und überall gehostet werden. |
| **API** | Die App muss Inhalte von der `model.json`-API abrufen. | Die Mobile App kann alle -APIs verwenden, einschließlich benutzerdefinierter. |
| **Persistenz** | Der SPA-Editor unterstützt nur Seiteninhalte für die visuelle Bearbeitung. | Der universelle Editor unterstützt nativ die visuelle Bearbeitung von Seiten und Inhaltsfragmenten. |
|  |  | Der universelle Editor kann erweitert werden, um externe Inhalte mit denselben visuellen Funktionen zu bearbeiten. |
|  | Entwickler müssen Sling-Modelle und `cq:Dialog` in AEM bereitstellen. | Entwickler benötigen wenig bis kein AEM-Erlebnis und müssen kein Java schreiben. |
