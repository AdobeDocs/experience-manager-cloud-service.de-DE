---
title: Konfigurieren einer Umleitungsseite oder Dankesnachricht
description: Erfahren Sie, wie Benutzenden eine Dankesnachricht angezeigt oder sie auf eine Webseite weitergeleitet werden können, die Formularautorinnen bzw. -autoren bei der Erstellung des Formulars konfigurieren können.
feature: Adaptive Forms, Edge Delivery Services
role: User
level: Intermediate
source-git-commit: cfff846e594b39aa38ffbd3ef80cce1a72749245
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 3%

---


# Konfigurieren von Dankesnachrichten und Umleitungs-URLs

Erfahrungen nach der Übermittlung beeinflussen die Benutzerzufriedenheit und die Formularausfüllungsraten erheblich. Der universelle Editor von Adobe bietet umfangreiche Optionen zum Konfigurieren dessen, was Benutzende nach dem Senden von Formularen sehen, sei es durch personalisierte Dankesnachrichten oder strategische Umleitungen zu bestimmten Seiten.

Dieser Artikel enthält detaillierte Anleitungen zur Implementierung von Dankesnachrichten und Umleitungs-URLs, einschließlich technischer Überlegungen, Best Practices und Richtlinien für das Benutzererlebnis, um die Effektivität Ihrer Formularübermittlungen zu maximieren.

## Voraussetzungen

Bevor Sie Erlebnisse nach der Übermittlung konfigurieren, stellen Sie sicher, dass die folgenden Punkte erfüllt sind:

**Technische Einrichtung:**

- Zugriff auf den universellen Editor mit entsprechenden Berechtigungen
- Ein vorhandenes adaptives Formular, das im universellen Editor erstellt wurde
- Informationen zu den Anforderungen Ihres Unternehmens an Umleitungs-URLs

**Überlegungen zur Planung:**

- **Nachrichtenstrategie**: Definieren Sie den Ton, die Länge und spezifische Informationen, die in Dankesnachrichten aufgenommen werden sollen
- **Umleitungsstrategie**: Zielseiten identifizieren und sicherstellen, dass sie für Erlebnisse nach dem Ausfüllen des Formulars optimiert sind
- **Analytics-Integration**: Planen Sie, wie Sie Benutzerinteraktionen mit Dankesnachrichten oder Umleitungszielen verfolgen.

## Konfigurieren von Dankesnachrichten

Dankesnachrichten bieten eine sofortige Bestätigung einer erfolgreichen Formularübermittlung und können personalisierte Inhalte, nächste Schritte oder wichtige Informationen enthalten, die für die Übermittlung des Benutzers relevant sind.

### Verwendung von Dankesnachrichten

Dankesnachrichten funktionieren am besten, wenn:

- **Einfache Bestätigung**: Benutzer benötigen eine Bestätigung ohne zusätzliche Navigationsanforderungen
- **Anleitungsinhalt**: Sie müssen spezifische nächste Schritte oder wichtige Informationen angeben
- **Markenkonsistenz**: Die Botschaft kann entsprechend dem Kommunikationsstil Ihres Unternehmens gestaltet werden
- **Einseitiges Erlebnis**: Benutzer sollten zur Kontinuität des Workflows auf der aktuellen Seite bleiben

### Implementierungsschritte

**1. Zugriff auf Formulareigenschaften**

Öffnen Sie Ihr adaptives Formular im universellen Editor und klicken Sie auf das Symbol **Formulareigenschaften bearbeiten** in der Symbolleiste. Dadurch wird das Dialogfeld für die Formulareigenschaften geöffnet.

**2. Navigieren Sie zur Dankeskonfiguration**

Wählen Sie im Dialogfeld „Formulareigenschaften“ die Registerkarte **Vielen Dank**, um auf die Konfigurationsoptionen nach der Übermittlung zuzugreifen.

**3. Konfigurieren Sie die Nachrichtenanzeige**

Wählen Sie **Nachricht anzeigen** aus den verfügbaren Optionen aus. Dadurch wird der Nachrichteninhalt-Editor mit Rich-Text-Funktionen aktiviert.

**4. Nachrichteninhalt erstellen**

Erstellen **im Feld** Nachrichteninhalt“ Ihre Dankesnachricht mit dem Rich-Text-Editor. Der Editor unterstützt:

- **Textformatierung**: Fett, Kursiv, Unterstrichen und Farboptionen
- **Listen**: Aufzählungs- und nummerierte Listen zum Organisieren von Informationen
- **Links**: Direkte Links zu relevanten Ressourcen oder nächste Schritte
- **Bearbeitung im Vollbildmodus**: Klicken Sie auf das Erweiterungssymbol, um einen größeren Bearbeitungsarbeitsbereich anzuzeigen

### Technische Überlegungen

**Anzeigeverhalten von Nachrichten:**

- Nachrichten werden unmittelbar nach der Formularübermittlung in einer modalen Überlagerung angezeigt
- Inhalte unterstützen HTML-Formatierung und behalten responsives Design bei
- Nachrichten können von Benutzern verworfen oder mit automatisch schließenden Timern konfiguriert werden

**Inhaltsrichtlinien:**

- Halten Sie die Nachrichten kurz, während Sie die erforderlichen Informationen bereitstellen
- Gegebenenfalls klare nächste Schritte einschließen
- Erwägen Sie, Referenznummern oder Bestätigungsdetails einzuschließen
- Sicherstellen einer mobilfreundlichen Formatierung

### Beispielimplementierung

    Vielen Dank für Ihre Übermittlung!
    
    Ihre Bewerbung ist eingegangen und erhält die Referenznummer #REF-2024-001234.
    
    **Was passiert als Nächstes:**
    - Sie erhalten innerhalb von 15 Minuten eine Bestätigungs-E-Mail
    - Unser Team wird Ihre Übermittlung innerhalb von 2 Werktagen überprüfen
    - Wir werden Sie direkt kontaktieren, wenn zusätzliche Informationen benötigt werden
    
    **Hilfe benötigen?** Kontaktieren Sie unser Support-Team unter support@example.com

## Konfigurieren von Umleitungs-URLs

Umleitungs-URLs navigieren Benutzer nach der Formularübermittlung automatisch zu bestimmten Seiten, was eine nahtlose Integration in vorhandene Workflows ermöglicht oder Benutzer zu relevanten Inhalten weiterleitet.

### Verwendung von Umleitungs-URLs

Umleitungs-URLs sind optimal für:

- **Workflow-Integration**: Weiterleitung von Benutzern zu Dashboards, Kontoseiten oder zu den nächsten Schritten in einem Prozess
- **Inhaltsbereitstellung**: Anzeigen relevanter Produkte, Services oder Informationen basierend auf Formularantworten
- **Analytics-Tracking**: Weiterleitung zu Seiten mit bestimmten Tracking-Implementierungen
- **Mehrstufige Prozesse**: Übergang von Benutzern zur nächsten Phase komplexer Workflows

### Implementierungsschritte

**1. Zugriff auf Formulareigenschaften**

Öffnen Sie Ihr adaptives Formular im universellen Editor und klicken Sie auf das Symbol **Formulareigenschaften bearbeiten**, um das Dialogfeld für die Formularkonfiguration zu öffnen.

**2. Navigieren Sie zur Dankeskonfiguration**

Wählen Sie die **Vielen Dank** im Dialogfeld Formulareigenschaften , um auf die Optionen für die Umleitungskonfiguration zuzugreifen.

**3. Umleitungsfunktion aktivieren**

Wählen Sie **Umleiten zur URL** aus den verfügbaren Optionen nach der Übermittlung aus.

**4. Konfigurieren der Ziel-URL**

Geben Sie Ihre Ziel-URL in das bereitgestellte Feld ein. Das System unterstützt mehrere URL-Formate für eine flexible Implementierung.

### URL-Konfigurationsoptionen

**Absolute URLs**

Vollständige Web-Adressen, einschließlich Protokoll und Domain:

    https://www.example.com/thank-you
    https://dashboard.example.com/user/profile

**Relative Pfade**

Relative Pfade zu Ihrer aktuellen Domain:

    /thank-you
    /dashboard/user-profile
    ../confirmation-page.html

**AEM Sites-Seitenverweise**

Verweise auf andere Seiten innerhalb Ihrer AEM Sites-Implementierung:

    /content/mysite/en/thank-you
    /content/mysite/en/next-step

### Technische Überlegungen

**Umleitungsverhalten:**

- Umleitungen erfolgen unmittelbar nach erfolgreicher Formularübermittlung
- Der Browser-Verlauf enthält die Umleitung für eine ordnungsgemäße Backbutton-Funktionalität
- Der Umleitungs-Timing kann mit optionalen Verzögerungen konfiguriert werden.

**URL-Validierung:**

- Das System überprüft das URL-Format, bevor die Konfiguration zugelassen wird
- Relative URLs werden für die aktuelle Domain aufgelöst.
- Externe URLs erfordern bei Bedarf eine ordnungsgemäße CORS-Konfiguration

## Best Practices und Empfehlungen

### Richtlinien für das Benutzererlebnis

**Nachrichtenoptimierung:**

- **Klarheit zuerst**: Stellen Sie sicher, dass Benutzer sofort verstehen, dass ihre Übermittlung erfolgreich war
- **Wertschöpfung**: Bereitstellung von Informationen, die den Benutzern bei den nächsten Schritten helfen
- **Konsistentes Branding**: Behalten Sie die Stimme und den visuellen Stil Ihres Unternehmens bei
- **Überlegungen zum Mobilgerät** Testen von Nachrichten in verschiedenen Bildschirmgrößen

**Umleitungsoptimierung:**

- **Seitenoptimierung**: Stellen Sie sicher, dass Umleitungsziele für Post-Formular-Besucher optimiert sind
- **Leistung wird geladen** Überprüfen Sie, ob Umleitungsseiten schnell geladen werden, um das Benutzererlebnis zu erhalten.
- **Inhaltsrelevanz**: Stellen Sie sicher, dass der Umleitungsinhalt für den Formularkontext relevant ist

### Sicherheitsaspekte

**URL-Validierung:**

- Gültige Validierung für Umleitungs-URLs implementieren, um bösartige Umleitungen zu verhindern
- Erwägen von Ansätzen zur Whitelist für zulässige Umleitungs-Domains
- Überwachen von Umleitungsmustern für ungewöhnliche Aktivitäten

**Inhaltssicherheit:**

- Bereinigen des Inhalts der Dankesnachricht, um das Einfügen von Skripten zu verhindern
- Implementieren von korrekten Inhaltssicherheitsrichtlinien für Rich-Text-Inhalte
- Regelmäßige Sicherheitsüberprüfungen von Umleitungszielen

### Analyse und Tracking

**Überlegungen zur Implementierung:**

- **Zielverfolgung**: Einrichten von Analysezielen sowohl für die Ansichten der Dankesnachricht als auch für die Weiterleitung
- **User Journey Mapping**: Verfolgen Sie, wie Benutzer mit Erlebnissen nach der Übermittlung interagieren
- **Konversionsoptimierung**: A/B-Test verschiedener Dankesnachrichten und Umleitungsziele

**Messstrategien:**

- Überwachen der Besuchszeit für Dankesnachrichten vor der Kündigung
- Tracking der Klickraten für Links in Dankesnachrichten
- Analysieren des Benutzerverhaltens auf Umleitungszielseiten

## Validierungs-Checkpoints

Nach der Konfiguration des Erlebnisses nach der Übermittlung:

**Konfigurationsüberprüfung:**

- Formulareigenschaften zeigen die ausgewählte Dankesoption korrekt an
- Nachrichteninhalt wird im Vorschaumodus korrekt angezeigt
- Umleitungs-URLs sind ordnungsgemäß formatiert und zugänglich
- Alle Links in Nachrichten funktionieren ordnungsgemäß

**Benutzererlebnistests:**

- Senden von Testformularen zur Überprüfung der korrekten Anzeige von Dankesnachrichten
- Testen der Weiterleitungsfunktion über verschiedene Browser hinweg
- Überprüfen der mobilen Reaktionsfähigkeit von Dankesnachrichten
- Überprüfen, ob Umleitungsziele ordnungsgemäß geladen werden

**Analytics-Einrichtung:**

- Trackingcodes für Dankesnachrichten richtig implementiert
- Tracking des Umleitungsziels konfiguriert
- Richtige Auslösung von Zielabschlussereignissen

## Nächste Schritte

Nach erfolgreicher Konfiguration des Erlebnisses nach der Übermittlung:

- **Leistung überwachen**: Überprüfen Sie die Analysen, um die Benutzerinteraktion mit Dankesnachrichten oder Umleitungsseiten zu verstehen
- **Iterieren und verbessern**: Verwenden Sie Benutzer-Feedback und Dateneinblicke, um Ihre Strategie nach der Übermittlung zu verfeinern
- **Implementierung skalieren**: Wenden Sie erfolgreiche Muster auf andere Formulare in Ihrer Organisation an

**Verwandte Dokumentation:**

- [Konfigurationshandbuch für die Formularübermittlung](submit-action.md)
- [Best Practices für das Benutzererlebnis](responsive-layout.md)

