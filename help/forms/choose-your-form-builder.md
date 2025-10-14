---
title: 'Formular-Builder: Wählen Sie Ihren Ansatz'
description: Vergleichen Sie Formular-Builder und finden Sie den richtigen Ansatz für die Erstellung adaptiver Formulare. Unabhängig davon, ob Sie Vorlagen für die Formularerstellung benötigen oder komplexe Formulare erstellen, wählen Sie den Formular-Builder aus, der Ihren Anforderungen am besten entspricht.
keywords: Form Builder, AEM Forms, Formularersteller, Erstellen von Formularen, Formularersteller, adaptive Formulare, Kernkomponenten, Foundation-Komponenten, Edge-Bereitstellungs-Services, Erstellen von Formularen
feature: Adaptive Forms, Core Components, Edge Delivery Services
role: User, Developer, Admin
level: Beginner
exl-id: choose-form-builder-guide
source-git-commit: ab84a96d0e206395063442457a61f274ad9bed23
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 9%

---


# Formular-Builder: Wählen Sie Ihren Ansatz {#choose-your-form-builder}

Adobe Experience Manager (AEM) Forms bietet drei leistungsstarke Ansätze zur Formularerstellung, die jeweils für verschiedene Anwendungsfälle, technische Anforderungen und Veröffentlichungsziele entwickelt wurden. Unabhängig davon, ob Sie als Formularersteller nach Vorlagen suchen oder als Entwickler komplexe Formulare erstellen, hilft Ihnen dieses Handbuch bei der Auswahl des richtigen Formular-Builders für Ihr Projekt.

## Schnellentscheidungshandbuch

Verwenden Sie diese Kurzreferenz, um den Formular-Builder zu ermitteln, der Ihren Anforderungen am besten entspricht:

| **Wenn Sie…** | **Auswählen** |
|-------------------|------------|
| **Moderne, skalierbare Formulare mit den neuesten Funktionen** | Kernkomponenten |
| **Blitzschnelle Formulare für Websites mit hohem Traffic** | Universeller Editor |
| **Vorhandene Formulare oder Legacy-Integrationen beibehalten** | Foundation-Komponenten |
| **Visuelles Drag-and-Drop-Authoring** | Kernkomponenten für den universellen Editor |
| **Tabellenkalkulationsbasierte Formularerstellung** | Dokumentenbasiertes Authoring |
| **Omni-Channel-Bereitstellung (Web, Mobile, Kiosks)** | Kernkomponenten (mit Headless-APIs) |
| **Benutzerdefinierte Frontend-Anwendungen (React, Angular)** | Kernkomponenten (mit Headless-APIs) |
| **Vollständige Kontrolle über das Formular-Rendering** | Kernkomponenten (mit Headless-APIs) |

## Grundlegendes zu den Optionen von Form Builder

AEM Forms bietet drei Ansätze zur Formularerstellung, die jeweils für verschiedene Typen von Formularerstellern und Anwendungsfällen entwickelt wurden. Ganz gleich, ob Sie einen einfachen Formularersteller für schnelle Aufgaben oder erweiterte Formularerstellungsfunktionen für komplexe Projekte benötigen, es gibt einen Ansatz, der Ihren Anforderungen entspricht:

### Foundation-Komponente Formular-Builder

Foundation-Komponenten stellen das klassische AEM Forms-Authoring-Erlebnis dar. Sie werden zwar weiterhin unterstützt, werden aber in erster Linie dafür empfohlen, vorhandene Formulare beizubehalten, anstatt neue zu erstellen.

**Hauptmerkmale:**

- Herkömmliche Authoring-Oberfläche für AEM
- Bewährte Stabilität für bestehende Workflows
- Auf AEM-Publishing beschränkt
- Grundlegende Komponentenbibliothek

### Kernkomponente für den Formular-Builder

Kernkomponenten bieten die neuesten AEM Forms-Funktionen mit verbesserter Leistung, Barrierefreiheit und Flexibilität. Dieser Formularersteller eignet sich ideal für Formularersteller, die professionelle Ergebnisse mit modernen Funktionen benötigen. Es unterstützt sowohl die AEM- als auch die Edge Delivery Services-Veröffentlichung und erstellt automatisch Headless-Formulare für die API-gesteuerte Bereitstellung auf mehreren Plattformen.

**Hauptmerkmale:**

- Moderne, standardisierte Komponenten
- Verbesserte Leistung und Zugänglichkeit
- Flexible Veröffentlichungsoptionen (AEM + Edge Delivery)
- Erweiterte Anpassungsfunktionen
- Zukunftssichere Architektur
- Automatische Headless-Formulargenerierung für die Omni-Channel-Bereitstellung

### Universeller Editor (Edge Delivery Services)

Der universelle Editor bietet zwei leistungsstarke Authoring-Ansätze für Edge Delivery Services: visuelles Authoring in WYSIWYG und dokumentbasiertes Authoring mit Tabellen. Dieser Formularerstelleransatz ist perfekt für Benutzer, die Formulare schnell und mit außergewöhnlicher Leistung erstellen möchten.

**Hauptmerkmale:**

- Außergewöhnliche Leistung (hohe Lighthouse-Werte)
- Zwei Authoring-Methoden: WYSIWYG und dokumentbasiert
- Optimiert für Edge Delivery Services
- Außergewöhnliche Leistung und SEO
- Schnelle Entwicklung und Bereitstellung


## Detailvergleich

### Technische Funktionen

| **Funktion** | **Foundation** | **Core** | **Universeller Editor** | **Dokumentbasiert** |
|----------------|----------------|----------|---------------------|-------------------|
| **Formularkomplexität** | Allgemein | Erweitert | Erweitert | Einfach bis mäßig |
| **Regel-Engine** | Erweitert | Erweitert | Erweitert | Limitiert |
| **Benutzerdefinierte Komponenten** | ✅ | ✅ | ✅ | ✅ |
| **Designs** | ✅ | ✅ | Projektebene | Projektebene |
| **Vorlagen** | ✅ | ✅ | Nur anfänglicher Inhalt |  |
| **Fragmente** | ✅ | ✅ | ✅ | ✅ |
| **Lokalisierung** | ✅ | ✅ | Über AEM Sites | Manuell/Funktionen |

### Integration und Übermittlung

| **Funktion** | **Foundation** | **Core** | **Universeller Editor** | **Dokumentbasiert** |
|-------------|----------------|----------|---------------------|-------------------|
| **Datenmodelle** | FDM, benutzerdefiniert | FDM, benutzerdefiniert | FDM, benutzerdefiniert | Benutzerdefiniert |
| **Übermittlungsaktionen** | Mehrere Optionen | Mehrere Optionen | Mehrere Optionen | Nur Tabellenkalkulation |
| **Vorausfüllen** | ✅ | ✅ | Über den Assistenten | ✅ |
| **CAPTCHA** | Mehrere Typen | reCAPTCHA, chaptcha | reCAPTCHA Enterprise | reCAPTCHA Enterprise |
| **Anlagen** | ✅ | ✅ | ✅ | Früher Zugang |
| **Digitale Signaturen** | ✅ |  |  |  |

### Veröffentlichung und Leistung

| **Aspect** | **Foundation** | **Core** | **Universeller Editor** | **Dokumentbasiert** |
|------------|----------------|----------|---------------------|-------------------|
| **Veröffentlichen** | Nur AEM | AEM + Edge Delivery + Headless-APIs | Edge-Bereitstellung | Edge-Bereitstellung |
| **Leistung** | Standard | Verbessert | Beste Lighthouse-Werte | Beste Lighthouse-Werte |
| **SEO-Optimierung** | Allgemein | Gut | Exzellent | Exzellent |
| **Reaktionsgeschwindigkeit auf Mobilgeräten** | Gut | Exzellent | Exzellent | Exzellent |

## Auswählen des richtigen Builders

### Wählen Sie Foundation-Komponenten aus, wenn:

- Bestehende Foundation-basierte Formulare werden verwaltet
- Integration digitaler Signaturen erforderlich
- Ihr Workflow hängt von den bewährten Foundation-Funktionen ab
- Sie arbeiten mit Veröffentlichungsanforderungen, die nur AEM betreffen

**Ideal für:** Formularwartung, Integration älterer Systeme, etablierte Workflows

### Wählen Sie Kernkomponenten aus, wenn:

- Man baut neue, moderne Formen
- Sie benötigen Flexibilität bei der Veröffentlichung auf AEM oder Edge Delivery Services
- Sie benötigen die neuesten Funktionen
- Sie benötigen erweiterte Anpassungen und Designs
- Barrierefreiheit und Leistung haben Priorität
- Sie wollen zukunftssichere Technologie

**Ideal für:** neue Projekte, skalierbare Lösungen, moderne Web-Erlebnisse

### Wählen Sie den universellen Editor, wenn:

- Sie benötigen außergewöhnliche Leistung und SEO
- Sie erstellen für Edge Delivery Services Sites
- Sie benötigen komplexe Formulare mit benutzerdefinierten Aktionen
- Integration mit externen Systemen ist erforderlich

**Ideal für:** Hochleistungs-Sites, Edge Delivery Services, Workflows für die visuelle Bearbeitung

### Wählen Sie das dokumentbasierte Authoring, wenn:

- Business-Anwender bevorzugen tabellenbasiertes Authoring
- Sie benötigen schnelle Prototypen und Bereitstellung
- Forms sind relativ einfach aufgebaut (Umfragen, Registrierungen, Feedback)
- Datenerfassung in Arbeitsblättern erfüllt Ihre Anforderungen
- Keine erweiterten Übermittlungs-Workflows erforderlich

**Ideal für:** schnelle Bereitstellung, Business-User-Authoring, einfache Datenerfassung


## Überlegungen zur Migration

### Von Foundation zu Kernkomponenten

- **Empfohlener Ansatz:** Verwenden des [Migrationsdienstprogramm-Tools](/help/forms/migration-utility-tool-for-af-core-components.md)
- **Vorteile:** Funktionen, bessere Leistung, Funktion zur Veröffentlichung auf zwei Ebenen
- **Aufwand** Je nach Formularkomplexität mittel bis hoch

### Vom traditionellen zum universellen Editor

- **Ansatz:** Formulare mithilfe von WYSIWYG oder dokumentbasiertem Authoring im universellen Editor neu erstellen
- **Vorteile:** Außergewöhnliche Leistung, moderne Entwicklungserfahrung, hohe SEO-Werte
- **Aufwand:** Hoch für komplexe Formulare, niedrig für einfache Formulare

## Erste Schritte

Nachdem Sie Ihren Formular-Builder ausgewählt haben:

### Foundation-Komponenten

1. [Erstellen eines adaptiven Formulars (Foundation-Komponenten)](/help/forms/creating-adaptive-form.md)
2. [Authoring-Handbuch für Foundation-Komponenten](/help/forms/introduction-forms-authoring.md)

### Kernkomponenten

1. [Erstellen eines adaptiven Formulars (Kernkomponenten)](/help/forms/creating-adaptive-form-core-components.md)
2. [Übersicht über die Kernkomponentenfunktionen](/help/forms/adaptive-form-core-components-json-schema-form-model.md)

### Universeller Editor (Edge Delivery Services)

1. **WYSIWYG-Authoring:** [Erste Schritte mit dem universellen Editor](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
2. **Dokumentenbasiertes Authoring:** Erstellen [&#x200B; ersten Formulars mit Tabellen](/help/edge/docs/forms/tutorial.md)


## Benötigen Sie Hilfe bei der Entscheidungsfindung?

Sie sind sich noch nicht sicher, welchen Formular-Builder Sie auswählen sollen? Berücksichtigen Sie die folgenden Faktoren:

- **Team-Expertise:** Wie hoch ist die technische Kompetenz Ihres Teams?
- **Projektzeitplan:** schnell müssen Sie bereitstellen?
- **Leistungsanforderungen:** sind Geschwindigkeit und SEO entscheidend?
- **Zukünftige Skalierbarkeit:** Müssen Sie Formulare häufig erweitern oder ändern?
- **Veröffentlichungsziel:** Wo werden Ihre Formulare veröffentlicht?

Wenden Sie sich für personalisierte Anleitungen an Ihr AEM Forms-Implementierungsteam oder den Adobe-Support.

## Verwandte Artikel

- [Detaillierter Vergleich der Formularerstellung](/help/edge/docs/forms/authoring-a-form.md)
- Übersicht über die [AEM Forms-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de)
- [Übersicht über Edge Delivery Services für Forms](/help/edge/docs/forms/overview.md)
- [Headless Adaptive Forms mit Kernkomponenten](https://experienceleague.adobe.com/de/docs/experience-manager-headless-adaptive-forms/using/tutorial/build-engaging-forms-using-core-components-and-headless-adaptive-forms-aem-forms-cloud-service)
