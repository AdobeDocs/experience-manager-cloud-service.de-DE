---
title: So konfigurieren Sie eine Umleitungsseite oder eine Dankesnachricht
description: Erfahren Sie, wie den Benutzenden eine Dankesnachricht angezeigt wirds oder wie sie auf eine Webseite weitergeleitet werden können, die Formularautorinnen bzw. -autoren bei der Erstellung des Formulars konfigurieren können.
feature: Adaptive Forms, Edge Delivery Services
role: User
level: Intermediate
exl-id: cacd7b0a-aad0-4b5d-a6a0-e4bac4cb196d
source-git-commit: fd3c53cf5a6d1c097a5ea114a831ff626ae7ad7e
workflow-type: tm+mt
source-wordcount: '1139'
ht-degree: 99%

---

# Konfigurieren von Dankesnachrichten und Umleitungs-URLs

Die Erfahrungen im Anschluss an die Übermittlung beeinflussen die Benutzerzufriedenheit und die Formularausfüllungsraten erheblich. Der universelle Editor von Adobe bietet umfangreiche Optionen zum Konfigurieren dessen, was Benutzende nach dem Senden von Formularen zu sehen bekommen, sei es durch personalisierte Dankesnachrichten oder strategische Umleitungen zu bestimmten Seiten.

Dieser Artikel enthält detaillierte Anleitungen zur Implementierung von Dankesnachrichten und Umleitungs-URLs, einschließlich technischer Überlegungen, Best Practices und Richtlinien für das Benutzererlebnis, um die Effektivität Ihrer Formularübermittlungen zu maximieren.

## Voraussetzungen

Bevor Sie Erlebnisse im Anschluss an die Übermittlung konfigurieren, müssen Sie über Folgendes verfügen:

**Technisches Setup:**

- Zugriff auf den universellen Editor mit entsprechenden Berechtigungen
- Ein vorhandenes adaptives Formular, das im universellen Editor erstellt wurde
- Informationen zu den Anforderungen Ihres Unternehmens an Umleitungs-URLs

**Aspekte bei der Planung:**

- **Nachrichtenstrategie**: Definieren Sie den Ton, die Länge und spezifische Informationen, die in Dankesnachrichten aufgenommen werden sollen.
- **Umleitungsstrategie**: Identifizieren Sie die Zielseiten und stellen Sie sicher, dass sie für Erlebnisse nach dem Ausfüllen des jeweiligen Formulars optimiert sind.
- **Analyseintegration**: Planen Sie, wie Sie Benutzerinteraktionen mit Dankesnachrichten oder Umleitungszielen verfolgen können.

## Konfigurieren von Dankesnachrichten

Dankesnachrichten bieten eine sofortige Bestätigung einer erfolgreichen Formularübermittlung und können personalisierte Inhalte, nächste Schritte oder wichtige Informationen enthalten, die für die Übermittlung der Person relevant sind.

### Verwendung von Dankesnachrichten

Dankesnachrichten funktionieren am besten bei:

- **Einfacher Bestätigung**: Benutzende benötigen eine Bestätigung ohne zusätzliche Navigationsanforderungen.
- **Anleitenden Inhalten**: Sie müssen spezifische nächste Schritte oder wichtige Informationen angeben.
- **Markenkonsistenz**: Die Botschaft kann entsprechend dem Kommunikationsstil Ihres Unternehmens gestaltet werden.
- **Erlebnis auf einer Seite**: Benutzende sollten zur Kontinuität des Workflows auf der aktuellen Seite bleiben.

### Implementierungsschritte

**1. Zugriff auf Formulareigenschaften**

Öffnen Sie Ihr adaptives Formular im universellen Editor und klicken Sie in der Symbolleiste auf das Symbol **Formulareigenschaften bearbeiten**. Dadurch wird das Dialogfeld für die umfassenden Formulareigenschaften geöffnet.

![Symbol „Formulareigenschaften“](/help/forms/assets/ue-form-properties-icon.png)

**2. Navigieren zur Dankeskonfiguration**

Wählen Sie im Dialogfeld „Formulareigenschaften“ die Registerkarte **Vielen Dank**, um auf die Konfigurationsoptionen nach der Übermittlung zuzugreifen.

![Formulareigenschaften des universellen Editors](/help/forms/assets/ue-form-properties.png)

**3. Konfigurieren der Nachrichtenanzeige**

Wählen Sie **Nachricht anzeigen** aus den verfügbaren Optionen aus.

![Danke](/help/edge/docs/forms/universal-editor/assets/thankyou-ue.png)

**4. Erstellen des Nachrichteninhalts**

Erstellen Sie im Feld **Nachrichteninhalt** mit dem Rich-Text-Editor Ihre Dankesnachricht. Der Editor unterstützt:

- **Textformatierung**: Fett, kursiv, unterstrichen und Farboptionen
- **Listen**: Aufzählungs- und nummerierte Listen zum Organisieren von Informationen
- **Links**: Direkte Links zu relevanten Ressourcen oder nächsten Schritten
- **Bearbeitung im Vollbildmodus**: Klicken Sie auf das Erweiterungssymbol, um einen größeren Bearbeitungsbereich anzuzeigen

### Technische Überlegungen

**Anzeigeverhalten von Nachrichten:**

- Nachrichten werden unmittelbar nach der Formularübermittlung in einer modalen Überlagerung angezeigt.
- Inhalte unterstützen HTML-Formatierung und behalten responsives Design bei.
- Nachrichten können von Benutzenden verworfen oder mit automatisch schließenden Timern konfiguriert werden.

**Inhaltsrichtlinien:**

- Halten Sie Nachrichten kurz, während Sie die erforderlichen Informationen bereitstellen.
- Schließen Sie gegebenenfalls klare nächste Schritte ein.
- Erwägen Sie, Referenznummern oder Bestätigungsdetails einzuschließen.
- Sicherstellen einer mobilfreundlichen Formatierung

### Beispielimplementierung

    Danke für Ihre Übermittlung.
    
    Ihre Bewerbung ist eingegangen und erhält die Referenznummer #REF-2024-001234.
    
    **Was geschieht als Nächstes:**
    – Sie erhalten innerhalb von 15 Minuten eine Bestätigungs-E-Mail
    – Unser Team wird Ihre Übermittlung innerhalb von 2 Werktagen überprüfen
    – Wir werden Sie direkt kontaktieren, wenn zusätzliche Informationen benötigt werden
    
    **Sie benötigen Hilfe?** Kontaktieren Sie unser Support-Team unter support@example.com

## Konfigurieren von Umleitungs-URLs

Umleitungs-URLs navigieren Benutzende nach der Formularübermittlung automatisch zu bestimmten Seiten, was eine nahtlose Integration in vorhandene Workflows ermöglicht oder Benutzende zu relevanten Inhalten weiterleitet.

### Verwendung von Umleitungs-URLs

Umleitungs-URLs sind optimal für:

- **Workflow-Integration**: Umleitung von Benutzenden zu Dashboards, Kontoseiten oder den nächsten Schritten in einem Prozess
- **Inhaltsbereitstellung**: Anzeige relevanter Produkte, Dienstleistungen oder Informationen basierend auf Formularantworten
- **Analyse-Tracking**: Umleitung zu Seiten mit bestimmten Tracking-Implementierungen
- **Mehrstufige Prozesse**: Überleitung von Benutzenden zur nächsten Phase komplexer Workflows

### Implementierungsschritte

**1. Zugriff auf Formulareigenschaften**

Öffnen Sie Ihr adaptives Formular im universellen Editor und klicken Sie auf das Symbol **Formulareigenschaften bearbeiten**, um das Dialogfeld für die Formularkonfiguration zu öffnen.

![Symbol „Formulareigenschaften“](/help/forms/assets/ue-form-properties-icon.png)

**2. Navigieren zur Dankeskonfiguration**

Wählen Sie die Registerkarte **Vielen Dank** im Dialogfeld „Formulareigenschaften“, um auf die Optionen für die Umleitungskonfiguration zuzugreifen.

![Formulareigenschaften des universellen Editors](/help/forms/assets/ue-form-properties.png)

**3. Aktivieren der Umleitungsfunktion**

Wählen Sie den Eintrag **Zu URL umleiten** aus den verfügbaren Optionen nach der Übermittlung aus.

![redirect](/help/edge/docs/forms/universal-editor/assets/redirect-ue.png)

**4. Konfigurieren der Ziel-URL**

Geben Sie Ihre Ziel-URL in das angegebene Feld ein. Das System unterstützt für eine flexible Implementierung verschiedene URL-Formate.

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

**AEM-Sites – Seitenreferenzen**

Verweise auf andere Seiten innerhalb Ihrer AEM Sites-Implementierung:

    /content/mysite/en/thank-you
    /content/mysite/en/next-step

### Technische Überlegungen

**Umleitungsverhalten:**

- Umleitungen erfolgen unmittelbar nach erfolgreicher Formularübermittlung.
- Der Browser-Verlauf enthält die Umleitung für ein ordnungsgemäßes Funktionieren der Schaltfläche „Zurück“.
- Das Umleitungs-Timing kann mit optionalen Verzögerungen konfiguriert werden.

**URL-Validierung:**

- Das System überprüft das URL-Format, bevor die Konfiguration zugelassen wird.
- Relative URLs werden für die aktuelle Domain aufgelöst.
- Externe URLs erfordern bei Bedarf eine ordnungsgemäße CORS-Konfiguration.

## Best Practices und Empfehlungen

### Richtlinien Prototypen für das Benutzererlebnis

**Nachrichtenoptimierung:**

- **Klarheit zuerst**: Sorgen Sie dafür, dass Benutzende sofort wissen, dass ihre Übermittlung erfolgreich war.
- **Wertschöpfung**: Stellen Sie Informationen bereit, die Benutzenden bei den nächsten Schritten helfen.
- **Konsistentes Branding**: Behalten Sie den Ton und den visuellen Stil Ihres Unternehmens bei.
- **Überlegungen zu Mobilgeräten**: Testen Sie Nachrichten auf verschiedenen Bildschirmgrößen.

**Optimierte Umleitungen:**

- **Seitenoptimierung**: Stellen Sie sicher, dass Umleitungsziele für Besuchende nach einer Formularübermittlung optimiert sind.
- **Ladeleistung**: Überprüfen Sie, ob Umleitungsseiten schnell geladen werden, um ein gutes Benutzererlebnis zu wahren.
- **Inhaltsrelevanz**: Stellen Sie sicher, dass der Umleitungsinhalt für den Formularkontext relevant ist.

### Sicherheitsaspekte

**URL-Validierung:**

- Implementieren Sie eine angemessene Validierung für Umleitungs-URLs, um bösartige Umleitungen zu verhindern.
- Erwägen Sie eine Verwendung von Ansätzen mit Zulassungslisten für zulässige Umleitungs-Domains.
- Überwachen Sie Umleitungsmuster auf ungewöhnliche Aktivitäten.

**Inhaltssicherheit:**

- Bereinigen Sie den Inhalt der Dankesnachricht, um ein Injizieren von Skripten zu verhindern.
- Implementieren Sie angemessene Inhaltssicherheitsrichtlinien für Rich-Text-Inhalte.
- Nehmen Sie regelmäßig Sicherheitsprüfungen für Umleitungsziele vor.

### Analyse und Tracking

**Überlegungen zur Implementierung:**

- **Zielverfolgung**: Richten Sie Analyseziele sowohl für Ansichten der Dankesnachricht als auch für die Umleitung ein.
- **User-Journey-Mapping**: Verfolgen Sie, wie Benutzende mit Erlebnissen nach der Übermittlung interagieren.
- **Konversionsoptimierung**: Führen Sie A/B-Tests für verschiedene Dankesnachrichten und Umleitungsziele durch.

**Messstrategien:**

- Überwachen Sie die Besuchsdauer von Dankesnachrichten, bevor diese geschlossen werden.
- Verfolgen Sie die Clickthrough-Raten für Links in Dankesnachrichten.
- Analysieren Sie das Benutzerverhalten auf Umleitungszielseiten.

## Validierungs-Checkpoints

Nach der Konfiguration des Erlebnisses im Anschluss an die Übermittlung:

**Konfigurationsüberprüfung:**

- Formulareigenschaften zeigen die ausgewählte Dankesoption korrekt an
- Nachrichteninhalt wird im Vorschaumodus korrekt angezeigt
- Umleitungs-URLs sind ordnungsgemäß formatiert und aufrufbar
- Alle Links in Nachrichten funktionieren ordnungsgemäß

**Test des Anwendererlebnisses:**

- Senden Sie Testformulare zur Überprüfung der korrekten Anzeige von Dankesnachrichten.
- Testen Sie die Umleitungsfunktion über verschiedene Browser hinweg.
- Überprüfen Sie die Reaktionsfähigkeit von Dankesnachrichten auf Mobilgeräten.
- Überprüfen Sie, ob Umleitungsziele ordnungsgemäß geladen werden.

**Analyse-Setup:**

- Trackingcodes für Dankesnachrichten richtig implementiert
- Tracking des Umleitungsziels konfiguriert
- Richtige Auslösung von Zielabschlussereignissen

## Nächste Schritte

Nach erfolgreicher Konfiguration des Erlebnisses im Anschluss an die Übermittlung:

- **Leistung überwachen**: Überprüfen Sie die Analysen, um die Benutzerinteraktion mit Dankesnachrichten oder Umleitungsseiten genau zu verstehen.
- **Iterieren und verbessern**: Verwenden Sie Benutzer-Feedback und Datenerkenntnisse, um Ihre Strategie nach der Übermittlung zu verfeinern.
- **Implementierung skalieren**: Wenden Sie erfolgreiche Muster auf andere Formulare in Ihrem Unternehmen an.

**Verwandte Dokumentation:**

- [Konfigurationshandbuch für die Formularübermittlung](submit-action.md)
- [Best Practices für das Benutzererlebnis](responsive-layout.md)
