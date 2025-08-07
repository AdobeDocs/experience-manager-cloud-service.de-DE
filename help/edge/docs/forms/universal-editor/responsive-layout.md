---
title: Erstellen einer responsiven Forms mit einem universellen Editor
description: Erfahren Sie, wie Sie mit dem universellen Editor responsive Formulare für alle Geräte entwerfen, testen und optimieren können. Übergeordnete Gerätetests, Layout-Muster und Mobiloptimierungstechniken für AEM Forms mit Edge Delivery Services.
keywords: Responsive Formulare, Formulare für Mobilgeräte, Gerätetests, universeller Editor, adaptives Layout, Formularoptimierung, mobiles Design, responsives Design, Formularlayouts, Geräteemulator
feature: Edge Delivery Services
role: User, Developer
level: Beginner
exl-id: 0c7fb491-4bad-4202-a472-87e6e6d9ab40
source-git-commit: ccfb85da187e828b5f7e8b1a8bae3f483209368d
workflow-type: tm+mt
source-wordcount: '1815'
ht-degree: 1%

---


# Erstellen einer responsiven Forms mit einem universellen Editor

Benutzer greifen auf Formulare auf einer Vielzahl von Geräten zu, einschließlich Desktops, Tablets und Smartphones. Das Entwerfen responsiver Formulare stellt ein optimales Erlebnis für alle Benutzenden sicher, unabhängig vom Gerät. In diesem Handbuch wird erläutert, wie Sie mit dem universellen Editor Formulare für jede Bildschirmgröße entwerfen, testen und optimieren können.


Die Erstellung responsiver Formulare umfasst zwei Hauptaktivitäten:

- **Responsive Tests:** Sie Ihre Formulare mithilfe von Geräteemulatoren auf verschiedenen Bildschirmgrößen in der Vorschau an und testen Sie sie.
- **Responsives Design** Wählen Sie Layout-Muster aus, die sich nahtlos an verschiedene Geräte anpassen, und implementieren Sie sie.

**In diesem Handbuch erfahren Sie mehr über Folgendes:**

- Testen von Formularen auf Desktop-, Tablet- und Mobilgeräten
- Auswählen der geeigneten Layoutmuster für Ihren Inhalt
- Anwenden von Best Practices für responsives Design
- Fehlerbehebung bei häufigen Problemen mit responsiven Formularen
- Optimieren von Formularen für mobile Leistung

## Warum Responsive Forms wichtig sind

**Auswirkungen auf das Benutzererlebnis:**

- Über 60 % der Benutzer greifen auf Formulare auf Mobilgeräten zu
- Schlechte mobile Erlebnisse führen zu einer 67 % höheren Abbruchrate
- Responsive Formulare können die Abschlussrate um bis zu 25 % erhöhen

**Geschäftsvorteile:**

- Höhere Formularausfüllungsraten
- Verbesserte Benutzerzufriedenheit
- Verbesserte Barrierefreiheit
- Niedrigere Entwicklungs- und Wartungskosten

>[!TIP]
>
> **Mobile-First-Ansatz:** Sie mit der Entwicklung für Mobilgeräte und erweitern Sie sie dann für größere Bildschirme. Dadurch wird sichergestellt, dass die Kernfunktionalität in der am stärksten eingeschränkten Umgebung funktioniert.

## Teil 1: Geräteübergreifendes Testen von Forms

Wenn Sie Ihre Formulare auf verschiedenen Geräten testen, können Sie responsive Probleme identifizieren und lösen, bevor sie Benutzern begegnen. Der universelle Editor bietet einen Emulatormodus zum Simulieren verschiedener Bildschirmgrößen und -ausrichtungen.

### Testen von Forms

**Schritt 1: Geräteemulator öffnen**

1. Öffnen Sie das Formular im universellen Editor.
2. Klicken Sie auf ![ Symbolleiste auf ](/help/edge/docs/forms/universal-editor/assets/emulator.png)Emulatorsymbol **{height=2%,width=2%}** Emulator.
3. Das Geräteauswahl-Menü wird angezeigt.

![Universelle Editor-Schnittstelle für responsive Tests](/help/edge/docs/forms/universal-editor/assets/universal-editor-emulator.png)

**Schritt 2: Gerät zum Testen auswählen**

- **Desktop** (Breite 1200 px+): Standard-Bearbeitungsansicht
- **Tablet** (768px-1199px Breite): Medium-Bildschirmtests
- **Mobile** (Breite 320 Pixel bis 767 Pixel): Tests auf kleinen Bildschirmen
- **Benutzerdefiniert**: Geben Sie genaue Abmessungen für bestimmte Geräte an

**Schritt 3: Ausrichtung des Testgeräts**

Verwenden Sie das Symbol **Screen Rotator**, um beides zu testen:

- **Hochformat**: Standardausrichtung für Mobilgeräte
- **Querformat**: Gedrehte Tablet- oder Telefonansicht

### Ergebnisse der Gerätetests

Jeder Gerätetyp zeigt ein einzigartiges responsives Verhalten:

| **Gerätetyp** | **Bildschirmbreite** | **Was zu überprüfen** | **Häufige Probleme** |
|-----------------|------------------|-------------------|-------------------|
| **Desktop** | 1200 px+ | Vollständiges Layout, alle Funktionen sichtbar | Übermäßige Leerzeichen, zu breite Layouts |
| **Tablet** | 768 px-1199 px | Komponenten-Stacking, Navigation und Benutzerfreundlichkeit | Unhandliche Dimensionierung, Touch-Target-Probleme |
| **Mobilgerät** | 320 px-767 px | Einspaltiges Layout, Miniaturnavigation | Kleiner Text mit eng beieinander liegenden Schaltflächen |
| **Benutzerdefiniert** | Benutzerdefiniert | Gerätespezifische Anforderungen | Breakpoint-Randfälle |

### Visuelle Beispiele nach Gerät

**Desktop-Ansicht (1200 px+):**
![Desktop-Formularansicht](/help/edge/docs/forms/universal-editor/assets/universal-editor-desktop.png)
*Layout mit voller Breite mit nebeneinander liegenden Formularfeldern.*

**Tablet-Ansicht (768 Pixel-1199 Pixel):**
![Tablet-Formularansicht](/help/edge/docs/forms/universal-editor/assets/universal-editor-tab.png)
*Layout mit Medium-Breite und angepasstem Komponentenabstand.*

**Mobilansicht (320 px-767 px):**
![Mobile-Formularansicht](/help/edge/docs/forms/universal-editor/assets/universal-editor-mobile.png)
*Einspaltiges Layout mit gestapelten Komponenten.*

**Benutzerdefinierte Geräteansicht:**
![Benutzerdefinierte Geräteansicht](/help/edge/docs/forms/universal-editor/assets/universal-editor-custom.png)
*Benutzerdefinierte Dimensionen für zielgerichtete Tests.*

### Test-Workflow

**Für neue Forms:**

1. **Build in der Desktop-Ansicht:** Mit vollem Funktionsumfang beginnen.
2. **Test auf dem Tablet** Überprüfen Sie die Anpassungen für mittlere Bildschirme.
3. **Validieren auf Mobilgeräten:** Benutzerfreundlichkeit auf kleinen Bildschirmen sicherstellen.
4. **Responsive Probleme beheben:** Passen Sie Layouts nach Bedarf an.
5. **Alle Geräte erneut testen:** Fehlerbehebungen für alle Größen bestätigen.

**Für bestehende Forms:**

1. **Schnelle Prüfung auf Mobilgeräten:** Funktioniert das Formular auf Mobiltelefonen?
2. **Problembereiche identifizieren:** Layout und Nutzungsprobleme beachten.
3. **Systematische Tests:** Testen Sie jede Gerätegröße gründlich.
4. **Dokumentprobleme:** Verfolgen Sie, was behoben werden muss.
5. **Fehlerkorrekturen implementieren** Beheben Sie Probleme methodisch.

## Teil 2: Auswählen responsiver Layout-Muster

Layout-Muster bestimmen, wie sich der Formularinhalt an verschiedene Bildschirmgrößen anpasst. Das richtige Muster verbessert sowohl das Benutzererlebnis als auch die Leistung auf Mobilgeräten.

### Layout-Muster - Übersicht

| **Layouttyp** | **Am besten geeignet für** | **Leistung für Mobilgeräte** | **Komplexität** |
|---------------------|-------------------------------------------|------------------------|----------------|
| **Bedienfeld-Layout** | Kategorisierte Inhalte, Formulare im Dashboard-Stil | Gut | Niedrig |
| **Assistenten-Layout** | Mehrstufige Prozesse, komplexe Workflows | Exzellent | Mittel |
| **Akkordeon-Layout** | FAQ-ähnliche Inhalte, optionale Abschnitte | Exzellent | Niedrig |

### Schnellentscheidungsleitfaden

**Verwenden des Bereichslayouts bei:**

- Ihre Inhalte sind in verschiedene Kategorien unterteilt
- Benutzende müssen mehrere Abschnitte gleichzeitig anzeigen
- Der Inhalt ist relativ einfach

**Verwenden des Assistenten-Layouts bei:**

- Das Formular weist mehrere logische Schritte auf
- Man will kognitive Belastung reduzieren
- Mobile Benutzer sind eine primäre Zielgruppe

**Akkordeon-Layout verwenden, wenn:**

- Das Formular enthält optionalen oder sekundären Inhalt
- Weltraumerhaltung ist wichtig
- Inhalte können logisch gruppiert werden

### Panel-Layout

**Zweck:** Organisiert verwandte Inhalte in visuell unterschiedliche Abschnitte, die gleichzeitig angezeigt werden können.

![Beispiel für ein Bedienfeld-Layout](/help/edge/docs/forms/universal-editor/assets/panel-layout.png)

**Responsives Verhalten:**

- **Desktop (1200 px+):** Bedienfelder werden nebeneinander oder in einem Raster angezeigt
- **Tablet (768px-1199px):** Panels stapeln vertikal mit Abstand
- **Mobil (320px-767px):** Einspaltiges Layout mit klaren Abschnittsumbrüchen

**Implementierungsschritte:**

1. Verwenden Sie die [Bedienfeldkomponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel).
2. Gruppieren Sie verwandte Felder in jedem Bedienfeld.
3. Fügen Sie für jeden Abschnitt klare Überschriften hinzu.
4. Stellen Sie einen ausreichenden Abstand zwischen den Bereichen sicher.

**Best Practices:**

- Beschränken Sie den Arbeitsbereich auf 3-4 Bedienfelder, um die Benutzer nicht zu überfordern.
- Verwenden Sie beschreibende Titel für jedes Bedienfeld.
- Gruppieren Sie verwandte Felder logisch, um die kognitive Belastung zu reduzieren.
- Navigation im Testfeld auf Touch-Geräten.

**Anwendungsbeispiele:**

- **Bewerbung:** Persönliche Informationen, Bildung, Erfahrung, Referenzen
- **Produktregistrierung:** grundlegende Details, technische Spezifikationen, Garantieinformationen
- **Umfrage Forms:** Demografie, Voreinstellungen, Feedback, Kontakt

### Assistenten-Layout

**Zweck:** Führt Benutzer Schritt für Schritt durch komplexe Prozesse, reduziert die kognitive Belastung und verbessert die Abschlussraten.

![Beispiel für Assistentenlayout](/help/edge/docs/forms/universal-editor/assets/wizard-layout.png)

**Responsives Verhalten:**

- **Alle Geräte:** Behält den Fokus auf einem Schritt bei, um ein optimales mobiles Erlebnis zu gewährleisten.
- **Schrittinhalt:** passt sich bei jedem Schritt an (Stapeln oder nebeneinander).
- **Navigation** Touch-optimierte Schaltflächen mit ausreichendem Abstand.
- **Fortschrittsanzeige:** Skaliert entsprechend der Bildschirmgröße.

**Implementierungsschritte:**

1. Verwenden Sie die [Assistenten-Komponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard).
2. Unterteilen Sie komplexe Formulare in logische Schritte (3-7 Schritte sind optimal).
3. Schließen Sie Fortschrittsanzeigen zur Benutzerorientierung ein.
4. Bereitstellen klarer Navigationssteuerelemente (Weiter, Zurück, Speichern).

**Optimierung für Mobilgeräte:**

- Verwenden Sie große Touch-Targets (mindestens 44 Pixel) für Navigationstasten.
- Stellen Sie sicher, dass die Schrittanzeigen auf kleinen Bildschirmen klar und sichtbar sind.
- Anzahl der Felder pro Schritt begrenzen, um den Bildlauf zu reduzieren
- Aktivieren Sie die automatische Speicherung, um Datenverlust zu vermeiden.

**Best Practices:**

- Sicherstellen des logischen Schrittverlaufs - jeder Schritt sollte auf dem vorherigen aufbauen.
- Verwenden Sie klare Schritttitel, damit Benutzer wissen, was zu erwarten ist.
- Validieren Sie die Eingabe bei jedem Schritt, um Fehler frühzeitig zu erkennen.
- Benutzern die Möglichkeit geben, rückwärts zu navigieren, um Informationen zu überprüfen oder zu bearbeiten.

**Anwendungsbeispiele:**

- **Versicherungsansprüche:** Vorfall → Beweismittel → persönliche →
- **Kontoeinrichtung:** Basic Info → Preferences → Security → Confirmation
- **Bestellvorgang:** Produkte → Versand → Zahlung → Zusammenfassung

### Akkordeon-Layout

**Zweck:** Platzeinsparung durch die Organisation von Inhalten in ausblendbaren Bereichen, ideal für optionale oder sekundäre Informationen.

![Beispiel für ein Akkordeon-Layout](/help/edge/docs/forms/universal-editor/assets/accordion-layout.png)

**Responsives Verhalten:**

- **Hervorragende mobile Leistung:** Es werden nur relevante Inhalte angezeigt.
- **Touch-optimierte Kopfzeilen:** Einfaches Tippen und Erweitern von Abschnitten.
- **Smooth Animations** Bieten Sie visuelles Feedback für Interaktionen.
- **Platzsparend:** Minimiert den Bildlauf auf allen Geräten.

**Implementierungsschritte:**

1. Verwenden Sie die [Akkordeon-Komponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion).
2. Gruppieren Sie in jedem Abschnitt verwandte optionale Inhalte.
3. Verwenden Sie beschreibende Abschnittsüberschriften.
4. Legen Sie die entsprechenden standardmäßigen offenen/geschlossenen Status fest.

**Vorteile für Mobilgeräte:**

- Reduziert den Bildlauf durch Reduzieren nicht verwendeter Abschnitte.
- Touch-freundliche Interaktion mit natürlichen Gesten zum Erweitern/Reduzieren.
- Schnelleres Laden - nur aktive Inhalte sind sichtbar.
- Verbesserter Fokus - Benutzer sehen nur das, was sie brauchen.

**Best Practices:**

- Verwenden Sie klare Abschnittsüberschriften, damit Benutzer wissen, was drin ist, bevor sie den Bereich erweitern.
- Gruppieren Sie verwandte Inhalte logisch in jedem Abschnitt.
- Legen Sie wichtige Abschnitte fest, um bei Bedarf erweitert zu beginnen.
- Bieten Sie eine kurze Abschnittsvorschau, die Benutzern bei der Entscheidung hilft, was erweitert werden soll.

**Anwendungsbeispiele:**

- **Produktkonfiguration:** Basic → Advanced → Accessories → Support
- **FAQ Forms:** Account → Billing → Technical → General
- **Einstellungen Forms:** Privacy →-Benachrichtigungen → Erscheinungsbild → Erweitert

## Teil 3: Best Practices für responsives Design

### Best Practices nach Gerätetyp

+++Optimierung für Mobilgeräte (320 Pixel - 767 Pixel)

**Grundlegende Praktiken:**

- Verwenden Sie ein einspaltiges Layout für alle Inhalte.
- Große, Touch-optimierte Tasten (minimale Höhe 44 Pixel).
- Vereinfachen Sie die Navigation mit klaren Zurück-/Weiter-Optionen.
- Scrollen Sie in jedem Abschnitt auf ein Minimum.
- Autofokus auf das erste Feld, das die Tastatur anzeigen soll.

**Feldspezifische Richtlinien:**

- **Texteingaben:** Breite mit Beispielabstand.
- **Dropdown-Listen** Verwenden Sie native Auswahlelemente für ein besseres Touch-Erlebnis.
- **Datumsauswahl:** Verwenden Sie native Datumseingaben für die Mobile-Kompatibilität.
- **Datei-Uploads** Stellen Sie große, übersichtliche Upload-Bereiche bereit.

+++

+++Tablet-Optimierung (768px-1199px)

**Layout-Strategien:**

- Verwenden Sie zweispaltige Layouts für verwandte Felder.
- Testen Sie sowohl Hoch- als auch Querformat.
- Unterstützt sowohl Touch- als auch Mausinteraktionen.
- Bereitstellen größerer Inhaltsbereiche bei Beibehaltung der Lesbarkeit.

+++

+++Desktop-Optimierung (1200 px+)

**Erweiterte Funktionen:**

- Verwenden Sie mehrspaltige Layouts für eine effiziente Platzierungsnutzung.
- Bieten Sie Tastaturbefehle für Power-User an.
- Implementieren Sie Hover-Status für interaktives Feedback.
- Bieten Sie eine erweiterte Validierung mit detaillierten Fehlermeldungen.

+++

## Umfassende Fehlerbehebung

### Layout-Probleme

+++Umbrüche des Formularlayouts auf Mobilgeräten

**Häufige Ursachen:**

- Elemente fester Breite, die nicht skaliert werden können
- CSS für Layouts, in denen der Desktop zuerst aufgerufen wird
- Bilder oder Inhalte, die über ihre Container hinausreichen

**Lösungen:**

- Stellen Sie sicher, dass Bilder und Container an die Bildschirmgröße skaliert werden.
- Verwenden Sie ein Mobile-First-Design mit progressiver Verbesserung.
- Testen Sie sowohl mit Geräteemulatoren als auch mit echten Geräten.
- Flexible Dimensionierung statt fester Abmessungen verwenden.

+++

+++Touch-Ziele zu klein

**Häufige Ursachen:**

- Tasten kleiner als 44 Pixel × 44 Pixel
- Interaktive Elemente zu nahe beieinander platziert
- Benutzerdefinierte CSS-Einstellungen überschreiben Touch-optimierte Standardeinstellungen

**Lösungen:**

- Stellen Sie sicher, dass alle interaktiven Elemente mindestens 44 Pixel × 44 Pixel groß sind.
- Abstand zwischen Schaltflächen und Links hinzufügen.
- Testen Sie die Touch-Interaktion mit den tatsächlichen Fingern, nicht nur mit der Maus.
- Erhöhen Sie die Anzahl der Touch-Zielbereiche, um das Tippen zu erleichtern.

+++

+++Probleme mit Inhaltsüberläufen

**Häufige Ursachen:**

- Langer Text oder Beschriftungen, die nicht umbrechen
- Container mit fester Breite
- Bilder, die nicht richtig skaliert werden

**Lösungen:**

- Aktivieren Sie den Textumbruch für langen Inhalt.
- Verwenden Sie responsive Bilder, die entsprechend skaliert werden.
- Implementieren Sie flexible Layouts, die sich an Inhalte anpassen.
- Testen Sie mit verschiedenen Inhaltslängen.

+++

### Leistungsprobleme

+++Langsames Laden auf Mobilgeräten

**Häufige Ursachen:**

- Große Bilder nicht für Mobilgeräte optimiert
- Übermäßige Ausführung von JavaScript
- Zu viele Formularfelder gleichzeitig geladen

**Lösungen:**

- Optimieren Sie Bilder für verschiedene Bildschirmgrößen.
- Laden Sie nicht kritische Inhalte nur bei Bedarf.
- Verwenden Sie Techniken, um das Laden auf Mobilgeräten zu beschleunigen.
- Minimieren Sie Skripte und Widgets von Drittanbietern.

+++

### Test- und Validierungsprobleme

+++Emulator im Vergleich zu echten Geräteunterschieden

**Häufige Ursachen:**

- Browser-spezifische Rendering-Unterschiede
- Unterschiede zwischen Touch- und Mausinteraktion
- Variationen der Netzwerkgeschwindigkeit

**Lösungen:**

- Tests an tatsächlichen Geräten, wann immer möglich.
- Verwenden Sie mehrere Browser für das Testen von Emulatoren.
- Simulieren Sie beim Testen unterschiedliche Netzwerkgeschwindigkeiten.
- Validieren Sie mit echten Benutzern in Zielumgebungen.

+++

## Erfolgsmetriken für responsive Forms

+++Wichtige Leistungsindikatoren

**Benutzererlebnismetriken:**

- **Formularausfüllungsrate:** Target ab 85 % auf Mobilgeräten
- **Zeit bis zum Abschluss:** Die mobile Abschlusszeit sollte nicht mehr als 20 % vom Desktop entfernt sein
- **Fehlerrate:** als 5 % Validierungsfehler
- **Abbruchpunkte:** Stellen Sie fest, an denen Benutzer abbrechen

**Technische Leistung:**

- **Seitenladezeit:** Unter 3 Sekunden in 3G-Netzwerken
- **Core Web Vitals:** Bestehen Sie alle Google-Leistungsbenchmarks
- **Barrierefreiheitswert:** WCAG 2.1 AA-Konformität
- **Browser-übergreifende Kompatibilität:** mehr als 98 % Funktionalität in allen gängigen Browsern

+++

+++Checkliste testen

**Vor der Veröffentlichung:**

- Testen Sie das Formular auf tatsächlichen Mobilgeräten.
- Stellen Sie sicher, dass alle Touch-Ziele mindestens 44 Pixel × 44 Pixel groß sind.
- Überprüfen Sie die Lesbarkeit des Textes auf allen Bildschirmgrößen.
- Überprüfen, ob die Formularvalidierung auf allen Geräten funktioniert.
- Stellen Sie sicher, dass die Ladezeit auf einem Mobilgerät unter 3 Sekunden liegt.
- Überprüfen Sie, ob alle interaktiven Elemente verfügbar sind.
- Übermitteln von Testformularen auf allen unterstützten Geräten

+++

## Nächste Schritte

**Sofortige Aktionen:**

1. **Prüfen Sie Ihre aktuellen Formulare:** Testen Sie vorhandene Formulare mithilfe des Geräteemulators.
2. **Ermitteln Sie schnelle Erfolge:** Beheben Sie zunächst offensichtliche Probleme mit der Benutzerfreundlichkeit von Mobilgeräten.
3. **Priorisieren Sie Formulare mit hohem Traffic:** Konzentrieren Sie sich auf Formulare mit der größten Auswirkung auf den Benutzer.
4. **Implementieren Sie einen Mobile-First-Ansatz** Beginnen Sie mit dem kleinsten Bildschirmdesign.

**Erweiterte Optimierung:**

- **Leistungsüberwachung:** Sie die Analyse ein, um Formularmetriken zu verfolgen.
- **A/B-Tests** Experimentieren Sie mit verschiedenen Layouts und Ansätzen.
- **Benutzer-Feedback-Sammlung** Sammeln Sie Einblicke von echten Benutzern.
- **Fortlaufende Verbesserung** Regelmäßige Überprüfung und Optimierung der Formulare.


