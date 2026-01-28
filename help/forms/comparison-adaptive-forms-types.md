---
title: Adaptive Forms-Kernkomponenten vs. Edge Delivery Services Forms vs. Foundation-Komponenten
description: Technischer Vergleich der Authoring-Ansätze von AEM Forms - Kernkomponenten, Edge Delivery Services Forms und Foundation-Komponenten. Architektur, Rendering, Funktionen und Anwendungsfälle.
keywords: Vergleich adaptiver Formulare, Kernkomponenten, Foundation-Komponenten, Edge-Bereitstellungs-Services und Formulare, Vergleich von AEM-Formularen, Vergleich von Forms Builder
role: Architect, Developer, Admin
level: Intermediate
feature: Adaptive Forms, Core Components, Edge Delivery Services
exl-id: adaptive-forms-comparison
source-git-commit: 37799555babb15809409ec5cda8a1c46ceff24f2
workflow-type: tm+mt
source-wordcount: '1953'
ht-degree: 10%

---


# Adaptive Forms: Kernkomponenten vs. Edge Delivery Services Forms vs. Foundation-Komponenten

Adobe Experience Manager (AEM) Forms bietet drei verschiedene Ansätze zum Erstellen von Datenerfassungserlebnissen: Adaptive Forms auf der Grundlage von Kernkomponenten, Edge Delivery Services Forms und Adaptive Forms auf der Grundlage von Foundation-Komponenten. Jeder Ansatz verfügt über eine andere Architektur, ein anderes Rendering-Modell und einen anderen Zielanwendungsfall. Dieser Artikel enthält einen technischen Vergleich, der Lösungsarchitekten, Entwicklern und AEM-Kunden bei der Auswahl des geeigneten Ansatzes für ihre Anforderungen unterstützt.

## Übersicht

Alle drei Formulartypen dienen dem Zweck der Erfassung von Benutzerdaten und der Integration mit Backend-Systemen. Sie unterscheiden sich jedoch in ihrer zugrunde liegenden Architektur, wo Formulare gerendert werden, wie sie bereitgestellt werden und welche Funktionen sie unterstützen.

| Ansatz | Status | Primärer Anwendungsfall |
|----------|--------|------------------|
| **Kernkomponenten** | Empfohlen für neue Formulare | Moderne, skalierbare Formulare, die AEM Authoring mit flexiblen Veröffentlichungsoptionen erfordern |
| **Edge Delivery Services Forms** | Empfohlen für leistungskritische Sites | Leistungsstarke Formulare, die vom Edge bereitgestellt werden, mit schneller Bereitstellung |
| **Foundation-Komponenten** | Wartungsmodus | Vorhandene Formulare, für die Unterstützung älterer Funktionen erforderlich ist |

## Adaptive Forms basierend auf Kernkomponenten

### Definition

Adaptive Forms-Kernkomponenten sind eine Gruppe von 30 BEM-kompatiblen Open-Source-Komponenten, die auf der Grundlage von Adobe Experience Manager WCM-Kernkomponenten erstellt wurden. Sie stellen den von Adobe empfohlenen Ansatz für die Erstellung eines neuen adaptiven Forms dar, der eine moderne Architektur, eine verbesserte Leistung und die automatische Headless-Formulargenerierung bietet.

### Architektur

Kernkomponenten verwenden eine standardisierte, modulare Komponentenarchitektur:

- **Component Foundation**: Basierend auf AEM WCM-Kernkomponenten
- **Stilmethodik**: BEM (Block Element Modifier)-CSS-Konventionen
- **Inhaltsspeicher**: JCR-Repository mit strukturierten Inhaltsknoten
- **Rendering**: Server-seitiges Rendering in AEM mit optionalem Client-seitigem Headless-Rendering
- **Source**: Open-Source (verfügbar auf [GitHub](https://github.com/adobe/aem-core-forms-components))

### Rendering-Modell

Kernkomponenten unterstützen mehrere Rendering-Modelle:

1. **Server-seitiges Rendering (SSR)**: Forms wird auf dem AEM-Server gerendert und der vollständige HTML wird im Browser bereitgestellt
2. **Headless-**: Forms stellt JSON-Darstellungen über APIs für Client-seitiges Rendering in React, Angular oder anderen Frameworks bereit
3. **Hybrid-Rendering**: Kombination aus Server- und Client-Rendering für optimale Leistung

### Veröffentlichungsoptionen

- AEM-Veröffentlichungsinstanzen
- Edge Delivery Services (falls konfiguriert)
- Headless-APIs für benutzerdefinierte Frontend-Anwendungen

### Wichtigste Funktionen

| Kategorie | Funktionen |
|----------|-------------|
| **Komponenten** | 30 standardisierte Komponenten, einschließlich Textfeld, numerisches Feld, Datumsauswahl, Dropdown, Kontrollkästchen-Gruppe, Optionsfeld, Dateianhang, Assistent, Akkordeon, horizontale/vertikale Registerkarten |
| **Formularmodelle** | JSON-Schema (v4 und 2020-12), Formulardatenmodell (FDM), XDP-/XFA-Vorlagen (begrenzt) |
| **Regel-Engine** | Visueller Regeleditor mit bedingter Logik, Validierung, Service-Aufruf, benutzerdefinierten Funktionen |
| **Aktionen übermitteln** | REST-Endpunkt, E-Mail, AEM Workflow, SharePoint, OneDrive, Azure Blob Storage, Power Automate, Workfront Fusion, Formulardatenmodell |
| **Vorausfüllen** | Vorbefüllungs-Service für Formulardatenmodelle, benutzerdefinierte Vorbefüllungs-Services |
| **CAPTCHA** | reCAPTCHA, chaptcha, Drehkreuz |
| **Datensatzdokument (Document of Record, DoR)** | PDF-Generierung mit benutzerdefinierten oder vorkonfigurierten Vorlagen |
| **Erreichbarkeit** | WCAG-kompatibel, ARIA-Bezeichnungen, Tastaturnavigation, Unterstützung für Bildschirmlesehilfen |
| **Lokalisierung** | Unterstützung mehrerer Sprachen über den Übersetzungs-Workflow von AEM |
| **Versionierung** | Von AEM Sites übernommene Inhaltsversionierung |

### Voraussetzungen

- **AEM Forms as a Cloud Service**: Kernkomponenten sind standardmäßig aktiviert
- **AEM 6.5 Forms**: Erfordert die Aktivierung über den AEM-Archetyp
- **Benutzerberechtigungen**: Benutzer muss `forms-users` Gruppe angehören
- **Vorlage**: Vorlage für adaptive Formulare (Kernkomponente) erforderlich
- **Design**: Canvas-Design (OOTB) oder benutzerdefiniertes Design

### Einschränkungen

- **JSON-**: Null-Typ, Vereinigungstypen (any), OneOf/AnyOf/AllOf/NOT-Konstrukte werden nicht unterstützt
- **Komponentenlücken**: Adobe Sign-Block, Freihandsignatur, Diagramm, Bildauswahl nicht verfügbar (in Foundation-Komponenten verfügbar)
- **Benutzerdefinierte Funktionen**: Generatorfunktionen, asynchron/await, Klassenmethoden werden nicht unterstützt
- **Digitale Signaturen**: nativ nicht verfügbar (im Gegensatz zu Foundation-Komponenten)

### Wann ist sie einzusetzen?

**Empfohlen für:**

- Neue Formularentwicklungsprojekte
- Organisationen, die eine moderne, verwaltbare Architektur benötigen
- Projekte, die eine flexible Veröffentlichung erfordern (AEM + Edge Delivery + Headless)
- Benutzerdefinierte Frontend-Anwendungen (React, Angular) über Headless-APIs
- Projekte, die Leistung und Barrierefreiheit priorisieren
- Omni-Channel-Bereitstellungsanforderungen (Web, Mobile, Kiosks)

**Nicht empfohlen für:**

- Forms, das eine Adobe Sign-Integration erfordert (Foundation-Komponenten verwenden)
- Einfache Formulare, bei denen die Edge Delivery Services-Leistung entscheidend ist
- Vorhandene auf Foundation-Komponenten basierende Formulare (werden in Foundation beibehalten, es sei denn, sie werden migriert)

## Edge Delivery Services Forms

### Definition

Edge Delivery Services (EDS) Forms ist ein zusammenstellbarer Satz von Services zum Erstellen und Bereitstellen von Formularen über Adobe Experience Manager Edge Delivery Services. Sie ermöglichen durch Edge-basierte Bereitstellung, Client-seitiges Rendering und mehrere Authoring-Methoden eine schnelle Formularentwicklung mit außergewöhnlicher Leistung.

### Architektur

EDS Forms verwendet eine entkoppelte „Edge-First“-Architektur:

- **Inhaltsquellen**: Microsoft SharePoint, Google Drive (dokumentbasiert) oder Universal Editor (WYSIWYG)
- **Code-Repository**: GitHub
- **Inhaltsbereitstellung**: Edge Delivery Services CDN
- **Rendering**: Client-seitiges Rendering mit Vanilla JavaScript
- **Formularblock**: Adaptiver Forms-Block verarbeitet Formulardefinitionen und generiert HTML

### Rendering-Modell

EDS Forms verwendet ausschließlich Client-seitiges Rendering:

1. Formulardefinition als JSON gespeichert (aus einer Tabelle konvertiert oder im universellen Editor verfasst)
2. JSON abgerufen von Edge: `https://<branch>--<repo>--<owner>.aem.live/<form>.json`
3. Adaptive Forms Block JavaScript verarbeitet JSON
4. Dynamisch im Browser generierte HTML-Struktur
5. CSS für Formatierung angewendet

**HTML-Strukturmuster:**

```html
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required="{Required}">
   <label for="{FieldId}" class="field-label">Label</label>
   <input type="{Type}" id="{FieldId}" name="{Name}">
   <div class="field-description" id="{FieldId}-description">Help text</div>
</div>
```

### Methoden für die Inhaltserstellung

EDS Forms unterstützt zwei Authoring-Ansätze:

#### Universeller Editor (WYSIWYG)

- Visuelle Drag-and-Drop-Oberfläche
- Echtzeitvorschau mit Gerätesimulation
- Erweiterter Regeleditor für bedingte Logik
- Integration des Formulardatenmodells (FDM)
- Integration von AEM-Workflows
- Unterstützung benutzerdefinierter Komponenten
- Vorlagenbasierte Erstellung

#### Dokumentenbasiertes Authoring

- Erstellen von Microsoft Excel- oder Google Sheets
- Tabellenbasierte Formulardefinition
- Sofortige Veröffentlichung (Änderungen werden sofort übernommen)
- Geeignet für einfache bis mäßig komplexe Formulare

### Übermittlungsoptionen

**Forms Submission Service (FSS):**

- An Google Sheets senden
- An Microsoft Excel senden (OneDrive/SharePoint)
- E-Mail-Benachrichtigungen

**AEM-Veröffentlichungs-Übermittlungsaktionen:**

- REST-Endpunkt
- AEM-E-Mail-Services
- Formulardatenmodell
- AEM-Workflow
- SharePoint/OneDrive
- Azure Blob Storage
- Microsoft Power Automate
- Adobe Workfront Fusion
- Adobe Marketo Engage

### Wichtigste Funktionen

| Kategorie | Funktionen |
|----------|-------------|
| **Komponenten** | Alle HTML5-Eingabetypen, Kontrollkästchen-Gruppen, Optionsfeldgruppen, Dropdown, Bedienfelder, wiederholbare Abschnitte, Dateianhang, Akkordeon, Assistent, Modal |
| **Validierung** | Validierung auf Feldebene (erforderlich, Min./Max., Muster), benutzerdefinierte Validierungsmeldungen |
| **Regeln** | Bedingte Sichtbarkeit, Wertausdrücke, ereignisgesteuerte Regeln |
| **Integrationen** | Adobe Sign, Salesforce, Microsoft Dynamics, A/B-Tests |
| **Sicherheit** | reCAPTCHA Enterprise, chaptcha, CORS-Konfiguration |
| **Analytics** | Adobe Experience Platform Web SDK, Formularansichten und Tracking der Übermittlung |

### Voraussetzungen

**Für das dokumentbasierte Authoring:**

- GitHub-Konto
- Google Drive- oder Microsoft SharePoint-Konto
- Knoten/npm für lokale Entwicklung
- AEM-Projekt mit konfiguriertem adaptiven Forms-Block
- Ordner für `forms@adobe.com` freigeben (Bearbeitungsberechtigungen)

**Für universellen Editor:**

- AEM Forms as a Cloud Service-Instanz
- Edge Delivery Services-Projekt konfiguriert
- Erforderliche Berechtigungen für Target-Ziele

**Für AEM-Veröffentlichungsübermittlung:**

- AEM Cloud Service-Instanz-URL konfiguriert
- Konfiguration des OSGi Referrer-Filters
- CORS-Konfiguration für Edge Delivery-Site-Domains

### Einschränkungen

**Dokumentenbasiertes Authoring:**

- Blattbenennung beschränkt auf `helix-default` und `shared-aem`
- Am besten geeignet für Formulare mit geringer Komplexität
- Eingeschränkte Regelfunktionen
- Keine AEM-Workflows (ohne Übermittlung der AEM-Veröffentlichung)
- Keine Integration des Formulardatenmodells

**Universeller Editor:**

- Statische/dynamische Importe werden in benutzerdefinierten Funktionen nicht unterstützt
- Formularfragmente können nur eigenständig bearbeitet werden
- Funktion zum Einbetten von Formularen in die Entwicklung

**Allgemein:**

- `shared-aem` sollten keine personenbezogenen Daten enthalten (öffentlich zugänglich)
- CORS-Konfiguration für Cross-Origin Submissions erforderlich
- Für AEM Publish-Übermittlungen ist ein OSGi-Referrer-Filter erforderlich

### Wann ist sie einzusetzen?

**Empfohlen für:**

- Leistungskritische Websites, die hohe Lighthouse-Werte erfordern
- Sites, die bereits Edge Delivery Services verwenden
- Schnelle Formularentwicklung und -bereitstellung
- Einfache bis moderate Datenerfassung
- Teams bevorzugen tabellenbasiertes Authoring (dokumentbasiert)
- Projekte, die eine schnelle Markteinführung erfordern

**Nicht empfohlen für:**

- Forms erfordert umfangreiche Server-seitige Verarbeitung
- Tiefe Integration mit Legacy-Systemen ohne REST-APIs
- Offline-Formularanforderungen
- Organisationen, die bestimmte JavaScript-Frameworks (React, Angular) mit uneingeschränktem Zugriff benötigen

## Adaptive Forms basierend auf Foundation-Komponenten

### Definition

Foundation-Komponenten stellen den klassischen Authoring-Ansatz von AEM Forms dar. Hierbei handelt es sich um die ursprünglichen adaptiven Forms-Komponenten, die seit vielen Jahren in AEM Forms verfügbar sind. Obwohl es weiterhin unterstützt wird, empfiehlt Adobe Foundation-Komponenten hauptsächlich zum Verwalten vorhandener Formulare und nicht zum Erstellen neuer.

### Architektur

Foundation-Komponenten verwenden die herkömmliche AEM-Architektur:

- **Inhaltsmodell**: WCM-`cq:Page` mit JCR-Inhaltsstruktur
- **Stammstruktur**: `guideContainer` (Stamm) → `rootPanel` → `items` (Formularfelder)
- **Rendering**: Server-seitiges Rendering mit Client-seitigem JavaScript
- **SOM-Ausdrücke**: Skriptobjektmodell für Verweise auf Formularobjekte

### Rendering-Modell

Foundation-Komponenten verwenden Server-seitiges Rendering:

1. Im JCR-Repository gespeicherte Formularinhalte
2. Formularstruktur für AEM-Serverprozesse
3. Vollständige HTML gerendert und an Browser gesendet
4. Client-seitige JavaScript übernimmt die Interaktivität und Validierung

### Wichtigste Funktionen

| Kategorie | Funktionen |
|----------|-------------|
| **Komponenten** | Über 40 Komponenten, einschließlich aller Kernkomponentenäquivalente plus: Adobe Sign-Block, Diagramm, Scribble-Signatur, Bildauswahl, Zusammenfassungsschritt, Dateianhang-Auflistung |
| **Formularmodelle** | Formulardatenmodell (FDM), XDP-/XFA-Vorlagen, XML-Schema (XSD), JSON-Schema |
| **Regel-Engine** | Visual Editor + Code-Editor (für die Gruppe „forms-power-users„) |
| **Digitale Signaturen** | Adobe Sign-Integration, Freihandsignatur |
| **Aktionen übermitteln** | Mehrere vordefinierte Aktionen ähnlich den Kernkomponenten |

### Komponenten exklusiv für Foundation

Die folgenden Komponenten sind **nur verfügbar** in Foundation-Komponenten:

- Adobe Sign Block
- Diagramm
- Auflistung der Dateianhänge
- Fußnoten-Platzhalter
- Bildauswahl
- Freihändige Unterschrift
- Zusammenfassungsschritt
- Turnstile Captcha

### Voraussetzungen

- AEM Forms as a Cloud Service oder AEM 6.5 Forms
- Adaptive Formularvorlage (Foundation)
- Benutzer in `forms-users` Gruppe

### Einschränkungen

- **Publishing**: Nur AEM (keine Edge Delivery Services- oder Headless-APIs)
- **Performance**: Standardleistung (nicht für Lighthouse-Werte optimiert)
- **Architektur**: Legacy-Architektur ohne BEM-Compliance
- **Open Source**: Nicht Open-Source
- **Zukünftige Entwicklung**: Wartungsmodus; neue Funktionen, die hauptsächlich zu Kernkomponenten hinzugefügt wurden

### Wann ist sie einzusetzen?

**Empfohlen für:**

- Beibehalten vorhandener Foundation-basierter Formulare
- Forms, das die Integration von Adobe Sign oder Freihandsignatur erfordert
- Workflows, die von etablierten Foundation-Funktionen abhängen
- Projekte mit Veröffentlichungsanforderungen nur für AEM
- Forms, für das Foundation-exklusive Komponenten erforderlich sind (Diagramm, Bildauswahl)

**Nicht empfohlen für:**

- Entwicklung neuer Formulare (verwenden Sie Kernkomponenten)
- Projekte, die eine Veröffentlichung in Edge Delivery Services erfordern
- Headless-Formular-APIs
- Leistungskritische Implementierungen
- Projekte, die zukunftssichere Architektur priorisieren

## Vergleichstabelle

| Parameter | Kernkomponenten | Edge Delivery Services Forms | Foundation-Komponenten |
|-----------|-----------------|-----------------------------|-----------------------|
| **Status** | Empfohlen für neue Formulare | Empfohlen für Hochleistungs-Websites | Wartungsmodus |
| **Architektur** | Modular, BEM-kompatibel | Edge-First, entkoppelt | Traditionelles WCM |
| **Rendern** | Server-seitig + Headless | Nur Client-seitig | Server-seitig |
| **Veröffentlichen** | AEM + Edge Delivery + Headless-APIs | Nur Edge Delivery Services | Nur AEM |
| **Authoring** | AEM Forms-Editor | Universeller Editor für Tabellen | AEM Forms-Editor |
| **Leistung** | Gut (gegenüber Foundation verbessert) | Hervorragend (hohe Lighthouse-Werte) | Standard |
| **Anzahl der Komponenten** | 30 | 20+ (alle HTML5-Eingabetypen) | 40+ |
| **Source öffnen** | Ja (GitHub) | Ja | Nein |
| **Formulardatenmodell** | ✅ | ✅ (nur universeller Editor) | ✅ |
| **JSON-Schema** | ✅ | Limitiert | ✅ |
| **XDP-/XFA-Unterstützung** | Limitiert | ❌ | ✅ |
| **XML-Schema** | ❌ | ❌ | ✅ |
| **Regel-Engine** | Erweiterter visueller Editor | Erweitert (universeller Editor) / Eingeschränkt (dokumentbasiert) | Erweiterter Visual + Code-Editor |
| **Digitale Signaturen** | ❌ | ❌ | ✅ |
| **Adobe Sign** | ❌ | Über die Integration | ✅ (Nativer Block) |
| **Datensatzdokument (Document of Record, DoR)** | ✅ | ✅ | ✅ |
| **CAPTCHA-Optionen** | reCAPTCHA, chaptcha | reCAPTCHA Enterprise, hCAPTCHA | reCAPTCHA, chaptcha, Drehkreuz |
| **AEM-Workflow** | ✅ | ✅ (über AEM Publish) | ✅ |
| **Headless-APIs** | ✅ (automatisch) | ❌ | ❌ |
| **Erreichbarkeit** | WCAG-kompatibel | WCAG-kompatibel | Einfach |
| **Bereitstellungsgeschwindigkeit** | Pipeline-basiert | Sofort (Live-Commit) | Pipeline-basiert |
| **Stile** | BEM-CSS, Designs | CSS, Designs auf Projektebene | CSS, Designs |
| **Versionierung** | ✅ (von Sites übernommen) | Git-basiert | ✅ |
| **Lokalisierung** | AEM-Übersetzungs-Workflow | Manueller/AEM Sites-Workflow | AEM-Übersetzungs-Workflow |

## Entscheidungsmatrix

| Anforderung | Empfohlener Ansatz |
|-------------|---------------------|
| Entwicklung neuer Formulare | Kernkomponenten |
| Vorhandene Formulare verwalten | Foundation-Komponenten (bis zur Migration) |
| Leistungskritisch (hohe Lighthouse-Werte) | Edge Delivery Services Forms |
| Headless-/Omni-Channel-Bereitstellung | Kernkomponenten |
| Adobe Sign-Integration | Foundation-Komponenten |
| Tabellenbasiertes Authoring | Edge Delivery Services (dokumentbasiert) |
| Visual WYSIWYG-Authoring mit Edge-Bereitstellung | Edge Delivery Services (universeller Editor) |
| Komplexe Unternehmensintegrationen | Kernkomponenten oder Foundation-Komponenten |
| Rapid Prototyping | Edge Delivery Services (dokumentbasiert) |
| Unterstützung von XFA-/XDP-Vorlagen | Foundation-Komponenten |
| Benutzerdefiniertes React-/Angular-Frontend | Kernkomponenten (Headless-APIs) |

## Überlegungen zur Migration

### Foundation-Komponenten in Kernkomponenten

- **Tool**: AEM-Modernisierungs-Tools (Forms Conversion Utility)
- **Aufwand**: Mittel bis hoch, je nach Formularkomplexität
- **Überlegungen**:
   - Regeln erfordern manuelle Neuerstellung
   - Foundation-exklusive Komponenten (Adobe Sign Block, Freihandsignatur, Diagramm) werden während der Migration gelöscht
   - Übersetzungsparameter nicht übernommen
   - Benutzerdefinierte Funktionen müssen umgeschrieben werden

### Traditionell für Edge Delivery Services

- **Ansatz**: Erstellen Sie Formulare mit dem universellen Editor oder der dokumentbasierten Bearbeitung neu
- **Aufwand**: Hoch für komplexe Formulare, niedrig für einfache Formulare
- **Vorteile**: Erhebliche Leistungsverbesserung, moderne Entwicklungserfahrung

## Dokumentationslücken und Mehrdeutigkeiten

Für die folgenden Bereiche ist die Dokumentation unvollständig oder mehrdeutig:

1. **XDP-/XFA-Unterstützung für Kernkomponenten**: In der Dokumentation wird eine „begrenzte“ Unterstützung angegeben, es werden jedoch keine genauen Einschränkungen angegeben
2. **Einbetten eines Edge Delivery Services-**: In der Dokumentation als „In Kürze verfügbar“ gekennzeichnet; aktueller Status unklar
3. **Foundation Components Future**: Keine explizite Zeitleiste zur Einstellung; wird als „Wartungsmodus“ beschrieben
4. **Headless-API-Abdeckung**: Exakte Funktionsparität zwischen Server-gerenderten und Headless-Formularen nicht dokumentiert
5. **Leistungs-Benchmarks**: Spezifische Lighthouse-Score-Vergleiche zwischen Ansätzen nicht angegeben

## Verwandte Ressourcen

- [Erstellen eines adaptiven Formulars (Kernkomponenten)](/help/forms/creating-adaptive-form-core-components.md)
- [Erstellen eines adaptiven Formulars (Foundation-Komponenten)](/help/forms/creating-adaptive-form.md)
- [Übersicht über Edge Delivery Services Forms](/help/edge/docs/forms/overview.md)
- [Universeller Editor - Erste Schritte](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
- [Dokumentbasiertes Authoring-Tutorial](/help/edge/docs/forms/tutorial.md)
- [Migrationsdienstprogramm](/help/forms/migration-utility-tool-for-af-core-components.md)
- [AEM Forms-Kernkomponenten auf GitHub](https://github.com/adobe/aem-core-forms-components)
