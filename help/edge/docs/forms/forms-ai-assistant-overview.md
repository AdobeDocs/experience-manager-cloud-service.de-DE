---
title: Forms Experience Builder
description: Schnelleres Erstellen leistungsstarker Formulare mithilfe von Formularfragmenten
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: 9996bc602ae6169dd1aade622d5dbc5b1addeb54
workflow-type: tm+mt
source-wordcount: '1113'
ht-degree: 3%

---


# Einführung in Forms Experience Builder

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Dokumentation wird derzeit mit dem Produkt getestet und unterliegt möglichen Aktualisierungen und Überarbeitungen. Funktionen, Befehle und Beispiele können sich ändern, wenn Forms Experience Builder während des Early-Adopter-Programms weiterentwickelt wird.

Der Forms Experience Builder bringt die Leistungsfähigkeit von künstlicher Intelligenz in Adobe Experience Manager (AEM) Forms. Diese innovative Lösung verändert die Art und Weise, wie Unternehmen ihre digitalen Formulare durch Interaktionen in natürlicher Sprache und intelligente Automatisierung erstellen, verwalten und optimieren.

Forms Experience Builder basiert auf modernen Web-Technologien und basiert auf fortschrittlichen KI-Services. Dadurch können sowohl technische als auch nicht-technische Anwender über konversationelle Benutzeroberflächen anspruchsvolle, professionelle Formulare erstellen. Unabhängig davon, ob Sie als Unternehmensanalyst ein einfaches Registrierungsformular benötigen oder ob Sie als Entwickler komplexe mehrstufige Workflows erstellen, optimiert Forms Experience Builder den gesamten Prozess der Formularerstellung.

## Dialogschnittstelle

Forms Experience Builder bietet eine intuitive chatbasierte Oberfläche, die die Formularerstellung so einfach macht wie eine Konversation:

```
┌─────────────────────────────────────────────────────────┐
│ Forms Experience Builder                               │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  👤 User: Create a customer feedback form              │
│                                                         │
│  🤖 AI: I'll help you create a feedback form. What    │
│       type of feedback do you want to collect?         │
│                                                         │
│  👤 User: Product reviews with ratings and comments    │
│                                                         │
│  🤖 AI: Perfect! I've created a feedback form with:   │
│       * Product rating (1-5 stars)                     │
│       * Comment field                                   │
│       * Customer email (optional)                       │
│       * Submit to email notification                    │
│                                                         │
│  👤 User: Add a field for product category             │
│                                                         │
│  🤖 AI: Added a dropdown field with common categories  │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

## Kernfunktionen

### KI-gestützte Formularerstellung

**Erzeugung natürlicher Formulare**

Erstellen Sie vollständige Formulare von Grund auf mit einfachen englischen Beschreibungen. Beschreiben Sie einfach Ihre Anforderungen, z. B. „Erstellen eines Kunden-Feedback-Formulars mit Bewertungs- und Kommentarfeldern“, und Forms Experience Builder generiert die entsprechende Formularstruktur, die entsprechenden Feldtypen und die entsprechenden Validierungsregeln.

**Dynamische Feldverwaltung**

Hinzufügen, Ändern oder Entfernen von Formularfeldern über Dialogbefehle. Die KI versteht den Kontext und kann basierend auf Ihren Anforderungen intelligent Feldtypen, Validierungsregeln und Verbesserungen der Benutzeroberfläche vorschlagen.

**Layout-Optimierung**

Formularlayouts und -konfigurationen mit natürlicher Sprache aktualisieren. Anforderungsänderungen wie „Das Formular mobiler gestalten“ oder „Felder in einem logischen Fluss neu organisieren“, und Forms Experience Builder wendet geeignete Stil- und Layout-Anpassungen an.

### Intelligente Import- und Konvertierungsfunktionen

**Konvertierung von PDF in ein Formular**

Wandeln Sie statische PDF-Dokumente in interaktive, dynamische Formulare um. Laden Sie ein beliebiges PDF-Dokument hoch. Forms Experience Builder analysiert die Struktur, um ein entsprechendes digitales Formular mit den entsprechenden Feldtypen und der entsprechenden Validierung zu erstellen.

**URL-Formular-Konvertierung**

Konvertieren bestehender Web-Formulare oder -Seiten in AEM Forms. Geben Sie einfach eine URL an, und Forms Experience Builder extrahiert Formularelemente und erstellt sie mit erweiterten Funktionen als native AEM Forms neu.

**Unterstützung von Multiformat-Dateien**

Verschiedene Dateitypen für die Formularerstellung, einschließlich PDFs, Bilder, Screenshots und vorhandene Formularvorlagen, können verarbeitet werden. Forms Experience Builder kann diese verarbeiten und in funktionale AEM Forms konvertieren.

### Erweiterte Formularlogik und -integration

**Intelligente Regelgenerierung**

Erstellen Sie komplexe Regeln für Formularvalidierung und Geschäftslogik mit natürlicher Sprache. Forms Experience Builder kann anspruchsvolle Bedingungslogik, Feldabhängigkeiten und Validierungsregeln generieren, die normalerweise umfangreiche Programmierkenntnisse erfordern würden.

**Umfassende Konfiguration der Übermittlungsaktion**

Konfigurieren Sie die Formularübermittlung für die Integration mit Ihren vorhandenen Geschäftssystemen:

- **E-Mail-Integration**: Einrichten automatisierter E-Mail-Benachrichtigungen und -Bestätigungen
- **REST-API-Endpunkte**: Verbinden mit benutzerdefinierten Programmen und Services
- **Cloud-**: Integration mit Azure Blob Storage, SharePoint und OneDrive
- **Workflow-**: Verbindung zu Power Automate und Workfront Fusion herstellen
- **Marketing-Plattformen**: Direkte Integration mit Marketo für Lead-Management
- **AEM-Workflows**: Vorhandene AEM-Workflow-Funktionen nutzen

**Leistungsanalyse**

Analysieren Sie die Leistung der Formularkonvertierung und die Interaktionsmuster der Benutzer. Forms Experience Builder bietet Einblicke in die Effektivität von Formularen und schlägt Optimierungen vor, um die Abschlussraten und das Anwendererlebnis zu verbessern.

## Funktionsweise

Forms Experience Builder folgt einem einfachen, dialogorientierten Ansatz:

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│  1. Describe    │───▶│  2. AI Creates  │───▶│  3. Refine &    │
│  Your Form      │    │  Initial Form   │    │  Configure      │
│  Requirements   │    │                 │    │                 │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         │                       │                       │
         ▼                       ▼                       ▼
┌─────────────────────────────────────────────────────────────────┐
│  "Create a loan application form"  →  Form with relevant        │
│  "Add conditional logic"           →  fields and basic          │
│  "Connect to CRM system"           →  validation rules          │
└─────────────────────────────────────────────────────────────────┘
```

## Anwendungsbeispiele

### Darlehensantrag

```
┌─────────────────────────────────────────────────────────┐
│ Loan Application - Multi-Step Form                    │
├─────────────────────────────────────────────────────────┤
│ Step 1: Personal Information                           │
│  🏠 Property Type: [Primary] [Investment] [Commercial] │
│  💰 Loan Amount: [$_______] (triggers different paths) │
│  📊 Income Verification: [W2] [Self-Employed] [Other]  │
│                                                         │
│ Step 2: Financial Details (conditional based on above) │
│  ↳ If Self-Employed: Show tax returns, profit/loss     │
│  ↳ If W2: Show employment history, pay stubs           │
│  ↳ Complex debt-to-income calculations                 │
│                                                         │
│ Step 3: Compliance & Review                            │
│  📋 Regulatory disclosures, digital signatures         │
│  🔍 Automated eligibility pre-screening                │
└─────────────────────────────────────────────────────────┘
```

### Versicherungsformular

```
┌─────────────────────────────────────────────────────────┐
│ Insurance Claim - Adaptive Form                        │
├─────────────────────────────────────────────────────────┤
│ 🚗 Claim Type: [Auto] [Property] [Health] [Business]   │
│                                                         │
│ ↳ Auto Selected: Shows accident details, police report │
│ ↳ Property: Shows damage assessment, repair estimates  │
│ ↳ Health: Shows medical provider network, pre-auth     │
│                                                         │
│ 📎 Dynamic Document Requirements:                       │
│   * Photos/videos of damage                            │
│   * Police reports (auto only)                         │
│   * Medical records (health only)                      │
│   * Repair estimates (property only)                   │
│                                                         │
│ 🔄 Real-time claim status updates                      │
└─────────────────────────────────────────────────────────┘
```

### Migrations- und Konversionsszenarien

Wandeln Sie Ihre vorhandenen Formulare mit KI-gestützter Konvertierung in leistungsstarke digitale Erlebnisse um.


#### PDF forms in Digital Forms umwandeln

Transformieren Sie PDF forms mit mehreren Feldern in dynamische digitale Erlebnisse mit automatisierten Berechnungen und einem auf Mobilgeräte reagierenden Design.

**Wichtigste Vorteile:**

- Automatisierte Steuerberechnungen und Feldabhängigkeiten
- Integration digitaler Signaturen und E-Filing
- Optimierung des responsiven Layouts für Mobilgeräte
- 95 % weniger Verarbeitungsfehler


#### Modernisierung älterer XFA-basierter Formulare

Sie können komplexe XFA-Anwendungen in moderne mehrstufige Assistenten mit Echtzeit-Validierung und Barrierefreiheit konvertieren.

**Wichtigste Vorteile:**

- Optimierte Benutzeroberfläche des mehrstufigen Assistenten
- Echtzeit-Validierung mit kontextueller Hilfe
- Integration der staatlichen Datenbank
- Vollständige Einhaltung der WCAG 2.1-Barrierefreiheit


#### Konvertieren eines Screenshots eines Formulars in ein digitales Formular

Sie können jedes Papierformular in ein digitales Erlebnis verwandeln. AEM Forms optimiert automatisch das Layout und erstellt aus einem Screenshot integrationsbereite digitale Formulare.

**Wichtigste Vorteile:**

- Intelligente Erkennung von Feldtypen
- Optimierte Erzeugung responsiver Layouts
- Verbesserte Validierung über das Originalpapier hinaus
- Integrationsfähige Architektur

#### Importieren und Erweitern vorhandener Web-Formulare

Sie können Ihr vorhandenes Web-Formular importieren und Ihren Formularen erweiterte Validierung, bedingte Logik und Multi-Channel-Übermittlung hinzufügen, ohne die vorhandene Funktionalität zu beeinträchtigen.

**Wichtigste Vorteile:**

- Erweiterte Validierungslogik und Regeln
- Verhalten und Workflows von bedingten Feldern
- Optionen für die Multi-Channel-Übermittlung
- Integrierte Analyse und Leistungsüberwachung

## Forms Experience Builder im Vergleich zur herkömmlichen Entwicklung

| Aspekt | Erstellung herkömmlicher Formulare | Forms Experience Builder |
|--------|---------------------------|----------------------|
| **Zeit zum Erstellen** | 2-3 Tage | 2-3 Stunden |
| **Technisches Wissen** | Erforderlich | Nicht erforderlich |
| **Validierungsregeln** | Manuelle Kodierung | Natürliche Sprache |
| **Optimierung für Mobilgeräte** | Manuelles CSS/JS | Automatisch |
| **Barrierefreiheit** | Manuelle Implementierung | Integrierte Compliance |
| **Updates** | Code-Änderungen erforderlich | Natürliche Sprache |


## Vorteile für Organisationen

### Demokratisierte Formularerstellung

Nicht-technische Benutzende in die Lage versetzen, anspruchsvolle Formulare ohne Programmierkenntnisse zu erstellen. Geschäftsanalysten, Fachexperten und Autoren von Inhalten können ihre Anforderungen durch Gespräche in natürlicher Sprache direkt in funktionale Formen übersetzen.

### Verkürzte Time-to-Value (TTV)

Drastische Beschleunigung der Formularentwicklung von Tagen auf Stunden. Was bisher umfangreiche Entwicklungszyklen erforderte, kann jetzt in einer einzigen Sitzung durch konversative KI erreicht werden, was eine schnellere Markteinführung für digitale Initiativen ermöglicht.

### Einfachheit der Benutzeroberfläche

Eliminieren Sie die Lernkurve mit einer intuitiven Gesprächsoberfläche. Benutzer können komplexe Formulare in natürlicher Sprache erstellen, anstatt technische Tools zum Erstellen von Formularen zu lernen, wodurch die Schulungszeit verkürzt und die Akzeptanz erhöht wird.

### Skalierung der Modernisierungsmaßnahmen

Effiziente Modernisierung älterer Formularportfolios. Konvertieren Sie bestehende PDF-, XFA- und HTML-Formulare in responsive digitale Erlebnisse, während Sie die Geschäftslogik beibehalten und das Anwendererlebnis im gesamten Formular-Ökosystem verbessern.

## Erste Schritte

Informationen zu den ersten Schritten mit Forms Experience Builder finden Sie in der [Dokumentation zu Forms Experience Builder](forms-ai-assistant-getting-started.md). Sie können auf Forms Experience Builder je nach bevorzugtem Workflow über den AEM Forms-Editor oder den universellen Editor zugreifen.

Für Unternehmen, die ihre Formularerstellungsprozesse umgestalten möchten, bietet Forms Experience Builder eine leistungsstarke, intuitive Lösung, die die Flexibilität der konversativen KI mit der Robustheit der Formularverwaltung auf Unternehmensebene kombiniert.

## Onboarding und Early Access

Forms Experience Builder ist derzeit als Teil des Early Access (EA)-Programms verfügbar. Gehen Sie wie folgt vor, um teilzunehmen und Zugriff zu erhalten:

1. Stellen Sie sicher, dass Sie die offizielle geschäftliche E-Mail-Adresse Ihres Unternehmens verwenden.
2. Senden Sie eine E-Mail an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com), um Zugriff auf Forms Experience Builder anzufordern.
3. Fügen Sie Ihren Organisationsnamen und alle relevanten Projektdetails in Ihre Anfrage ein, um den Onboarding-Prozess zu beschleunigen.

>[!NOTE]
>
> Der Zugriff auf Forms Experience Builder ist auf genehmigte Teilnehmer am Early Access-Programm beschränkt. Adobe prüft Ihre Anfrage und stellt weitere Onboarding-Anweisungen bereit, sofern Sie berechtigt sind.

Weitere Informationen zum Early-Access-Programm und seinen Funktionen finden Sie in der [AEM Forms Early Access-Dokumentation](/help/forms/early-access-ea-features.md).

