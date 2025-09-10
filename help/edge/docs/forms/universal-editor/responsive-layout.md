---
title: Erstellen von responsiven Formularen mit dem universellen Editor
description: Erfahren Sie, wie Sie mit dem universellen Editor responsive Formulare für alle Geräte entwerfen, testen und optimieren können. Lernen Sie Gerätetests, Layout-Muster und mobile Optimierungsverfahren für AEM Forms mit Edge Delivery Services kennen.
keywords: Responsive Formulare, Formulare für Mobilgeräte, Gerätetests, universeller Editor, adaptives Layout, Formularoptimierung, mobiles Design, responsives Design, Formular-Layouts, Geräteemulator
feature: Edge Delivery Services
role: User, Developer
level: Beginner
exl-id: 0c7fb491-4bad-4202-a472-87e6e6d9ab40
source-git-commit: fd3c53cf5a6d1c097a5ea114a831ff626ae7ad7e
workflow-type: tm+mt
source-wordcount: '2443'
ht-degree: 93%

---


# Erstellen einer responsiven Forms mit dem universellen Editor - Eine vollständige Anleitung

Die moderne Web-Landschaft setzt Formulare voraus, die über ein immer breiteres Spektrum von Geräten und Bildschirmgrößen hinweg nahtlos funktionieren. Von großen Desktop-Monitoren bis hin zu kompakten Smartphone-Bildschirmen erwarten Benutzende unabhängig vom gewählten Gerät konsistente, intuitive Erlebnisse. Die Erstellung responsiver Formulare ist keine Option mehr. Vielmehr ist sie eine grundlegende Voraussetzung für die Bereitstellung professioneller, barrierefreier und konversionsoptimierter digitaler Erlebnisse.

Der universelle Editor bietet umfassende Tools und Methoden zum Entwickeln responsiver Formulare, die sich intelligent an verschiedene Bildschirmabmessungen, Eingabemethoden und Benutzerkontexte anpassen. In diesem Handbuch werden die technischen Grundlagen, Implementierungsstrategien und Optimierungstechniken untersucht, die zum Erstellen von Formularen erforderlich sind, die auf allen Geräten außergewöhnliche Leistung erbringen und gleichzeitig für hohe Benutzerfreundlichkeit, Zugänglichkeit und visuelle Attraktivität sorgen.

Die Erstellung responsiver Formulare umfasst zwei Hauptaktivitäten:

- **Responsive Tests:** Zeigen Sie Ihre Formulare mithilfe von Geräteemulatoren für verschiedene Bildschirmgrößen als Vorschau an und testen Sie sie.
- **Responsives Design** Wählen Sie Layout-Muster aus, die sich nahtlos an verschiedene Geräte anpassen, und implementieren Sie sie.

**In diesem Handbuch lernen Sie Folgendes:**

- Testen von Formularen auf Desktop-, Tablet- und Mobilgeräten
- Auswählen der geeigneten Layout-Muster für Ihren Content
- Anwenden von Best Practices für responsives Design
- Beheben häufiger Problemen, die bei responsiven Formularen auftreten
- Optimieren von Formularen für Mobilgeräte

<!--
## Why Responsive Forms Are Important

**User Experience Impact:**

- Over 60% of users access forms on mobile devices
- Poor mobile experiences result in a 67% higher abandonment rate
- Responsive forms can increase completion rates by up to 25%

**Business Benefits:**

- Higher form completion rates
- Improved user satisfaction
- Enhanced accessibility compliance
- Lower development and maintenance costs-->

>[!TIP]
>
> **Mobile-First-Ansatz:** Beginnen Sie mit der Entwicklung für Mobilgeräte und erweitern Sie dann für größere Bildschirme. So wird sichergestellt, dass die Kernfunktionen in der am stärksten eingeschränkten Umgebung funktionieren.

## Teil 1: Geräteübergreifendes Testen von Formularen

Wenn Sie Ihre Formulare auf verschiedenen Geräten testen, können Sie responsive Probleme identifizieren und lösen, bevor Benutzende darauf stoßen. Der universelle Editor bietet einen Emulatormodus zum Simulieren verschiedener Bildschirmgrößen und -ausrichtungen.

### So können Sie Ihre Formulare testen

**Schritt 1: Öffnen des Geräteemulators**

1. Öffnen Sie Ihr Formular im universellen Editor.
2. Klicken Sie in der Symbolleiste auf das ![Emulatorsymbol](/help/edge/docs/forms/universal-editor/assets/emulator.png){height=2%,width=2%}**Emulator**.
3. Das Menü für die Geräteauswahl wird angezeigt.

![Oberfläche des universellen Editors für responsive Tests](/help/edge/docs/forms/universal-editor/assets/universal-editor-emulator.png)

**Schritt 2: Auswählen eines Geräts zum Testen**

- **Desktop** (Breite: 1.200 px und mehr): Standard-Bearbeitungsansicht
- **Tablet** (Breite: 768 bis 1.199 px): Tests für mittlere Bildschirmgrößen
- **Mobile** (Breite: 320 bis 767 px): Tests für kleine Bildschirmgrößen
- **Benutzerdefiniert**: Angabe genauer Abmessungen für bestimmte Geräte

**Schritt 3: Testen der Geräteausrichtungen**

Verwenden Sie das Symbol **Bildschirmrotator**, um beides zu testen:

- **Hochformat**: Standardausrichtung für Mobilgeräte
- **Querformat**: Gedrehte Tablet- oder Telefonansicht

### Ergebnisse der Gerätetests

Jeder Gerätetyp weist ein eigenes responsives Verhalten auf:

| **Gerätetyp** | **Bildschirmbreite** | **Worauf zu achten ist** | **Häufige Probleme** |
|-----------------|------------------|-------------------|-------------------|
| **Desktop** | 1200 px+ | Vollständiges Layout, alle Funktionen sichtbar | Übermäßige leere Bereiche, zu breite Layouts |
| **Tablet** | 768 px bis 1.199 px | Stapelung von Komponenten, Navigationsfreundlichkeit | Eigenartige Dimensionierung, Probleme bei Berührung des Ziels |
| **Mobilgerät** | 320 px bis 767 px | Einspaltiges Layout, Navigation mit Daumen | Kleiner Text mit eng beieinander liegenden Schaltflächen |
| **Benutzerdefiniert** | Benutzerdefiniert | Gerätespezifische Anforderungen | Breakpoint-Grenzfälle |

### Visuelle Beispiele nach Gerät

**Desktop-Ansicht (1.200 px+):**
![Desktop-Formularansicht](/help/edge/docs/forms/universal-editor/assets/universal-editor-desktop.png)
*Layout mit voller Breite und nebeneinander liegenden Formularfeldern.*

**Tablet-Ansicht (768 px bis 1.199 px):**
![Tablet-Formularansicht](/help/edge/docs/forms/universal-editor/assets/universal-editor-tab.png)
*Layout mit mittlerer Breite und angepasstem Komponentenabstand.*

**Mobilansicht (320 px bis 767 px):**
![Mobile-Formularansicht](/help/edge/docs/forms/universal-editor/assets/universal-editor-mobile.png)
*Einspaltiges Layout mit gestapelten Komponenten.*

**Benutzerdefinierte Geräteansicht:**
![Benutzerdefinierte Geräteansicht](/help/edge/docs/forms/universal-editor/assets/universal-editor-custom.png)
*Benutzerdefinierte Abmessungen für gezielte Tests.*

### Test-Workflow

**Für neue Formulare:**

1. **Erstellung in der Desktop-Ansicht:** Starten Sie mit dem vollen Funktionsumfang.
2. **Test auf dem Tablet** Überprüfen Sie Anpassungen für mittelgroße Bildschirme.
3. **Validierung auf Mobilgeräten:** Stellen Sie Benutzerfreundlichkeit auf kleinen Bildschirmen sicher.
4. **Beheben responsiver Probleme:** Passen Sie Layouts nach Bedarf an.
5. **Erneutes Testen auf allen Geräten:** Überprüfen Sie Fehlerbehebungen für alle Größen.

**Für vorhandene Formulare:**

1. **Schnelle Prüfung auf Mobilgeräten:** Funktioniert das Formular auf Mobiltelefonen?
2. **Identifizieren von Problembereichen:** Achten Sie auf Layout- und Nutzungsprobleme.
3. **Systematische Tests:** Testen Sie jede Gerätegröße gründlich.
4. **Dokumentieren von Problemen:** Verfolgen Sie, was behoben werden muss.
5. **Implementieren von Fehlerkorrekturen:** Beheben Sie Probleme methodisch.

## Teil 2: Auswählen responsiver Layout-Muster

Layout-Muster bestimmen darüber, wie sich der Formularinhalt an verschiedene Bildschirmgrößen anpasst. Das richtige Muster verbessert sowohl das Anwendererlebnis als auch die Leistung auf Mobilgeräten.

### Layout-Muster – Übersicht

| **Layout-Typ** | **Am besten geeignet für** | **Mobile Leistung** | **Komplexität** |
|---------------------|-------------------------------------------|------------------------|----------------|
| **Bedienfeld-Layout** | Kategorisierte Inhalte, Formulare im Dashboard-Stil | Gut | Niedrig |
| **Assistenten-Layout** | Mehrstufige Prozesse, komplexe Workflows | Exzellent | Mittel |
| **Akkordeon-Layout** | FAQ-ähnliche Inhalte, optionale Abschnitte | Exzellent | Niedrig |

### Leitfaden für schnelle Entscheidungen

**Verwenden Sie das Bedienfeld-Layout, wenn:**

- Ihre Inhalte in verschiedene Kategorien unterteilt sind
- Benutzende mehrere Abschnitte gleichzeitig anzeigen müssen
- Der Inhalt relativ einfach ist

**Verwenden Sie das Assistenten-Layout, wenn:**

- Das Formular mehrere logische Schritte aufweist
- Sie die kognitive Belastung reduzieren wollen
- Mobile Benutzende eine primäre Zielgruppe sind

**Verwenden Sie das Akkordeon-Layout, wenn:**

- Das Formular optionalen oder sekundären Inhalt enthält
- Platzsparen wichtig ist
- Inhalte logisch gruppiert werden können

### Bedienfeld-Layout

Das Bedienfeld-Layout organisiert verwandte Inhalte in visuell unterschiedliche Abschnitte, sodass Benutzende mehrere Abschnitte gleichzeitig anzeigen können. Dieses Layout eignet sich ideal für Formulare mit kategorisierten Informationen, die von einer Side-by-Side-Präsentation auf größeren Bildschirmen profitieren.

![Beispiel für ein Bedienfeld-Layout](/help/edge/docs/forms/universal-editor/assets/panel-layout.png)

**Responsives Verhalten**

- **Desktop (1.200 px und mehr):** Bedienfelder werden nebeneinander oder in einem Raster angezeigt, um maximale Sichtbarkeit zu erzielen.
- **Tablet (768 bis 1.199 px):** Bedienfelder werden vertikal mit angemessenem Abstand gestapelt, um Übersichtlichkeit zu wahren.
- **Mobil (320 bis 767 px):** Bedienfelder werden für einfache Navigation in einem einspaltigen Layout mit einer klaren Trennung zwischen Abschnitten präsentiert.

**Vorgehensweise bei der Implementierung**

1. Fügen Sie Ihrem Formular die [Panel-Komponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) hinzu. 
2. Gruppieren Sie verwandte Felder innerhalb jedes Bedienfelds, um die logische Organisation zu wahren.
3. Weisen Sie jedem Bedienfeldabschnitt klare, beschreibende Überschriften zu.
4. Sorgen Sie dafür, dass es ausreichend Abstand zwischen den Bereichen gibt, um Übersichtlichkeit zu gewährleisten.

**Best Practices**

- Begrenzen Sie die Anzahl der Bedienfelder auf dem Desktop auf drei oder vier, um zu vermeiden, dass Benutzende überfordert werden.
- Verwenden Sie für jedes Bedienfeld knappe, beschreibende Titel, um das Verständnis der Benutzenden zu verbessern.
- Organisieren Sie Felder in Bedienfeldern logisch, um kognitive Belastung zu minimieren.
- Testen Sie die Bedienfeldnavigation auf Touch-Geräten, um Anwenderfreundlichkeit auf allen Plattformen sicherzustellen.

**Häufige Anwendungsszenarien**

- **Bewerbung:** Abschnitte für persönliche Daten, Ausbildung, Erfahrung und Referenzen.
- **Produktregistrierung:** Bedienfelder für grundlegende Details, technische Spezifikationen und Garantieinformationen.
- **Umfrageformulare:** Gruppierungen für demografische Daten, Präferenzen, Feedback und Kontaktinformationen.

### Assistenten-Layout

Das Assistenten-Layout führt Benutzende durch einen mehrstufigen Prozess und zeigt jeweils einen Abschnitt an. Dieses Layout eignet sich besonders für komplexe Formulare, da es die kognitive Belastung reduziert und die Fertigstellungsraten erhöht, indem der Prozess in überschaubare Schritte unterteilt wird.

![Beispiel für Assistenten-Layout](/help/edge/docs/forms/universal-editor/assets/wizard-layout.png)

**Responsives Verhalten**

- **Alle Geräte:** Behält den einstufigen Fokus bei, der für mobile Benutzende optimal ist.
- **Schrittweise Inhalte:** Der Inhalt passt sich bei jedem Schritt responsiv an, indem Felder je nach Bildschirmgröße gestapelt oder nebeneinander angeordnet werden.
- **Navigation:** Verfügt über berührungsfreundliche Schaltflächen mit ausreichendem Abstand für einfache Interaktion.
- **Fortschrittsanzeige:** Fortschrittsbalken oder Schrittanzeigen werden für verschiedene Geräte entsprechend skaliert und liefern klares Feedback zum Fertigstellungsstatus.

**Vorgehensweise bei der Implementierung**

1. Fügen Sie die [Assistentenkomponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) in Ihr Formular ein.
2. Teilen Sie das Formular in logische Schritte auf (idealerweise zwischen drei und sieben), damit jeder Schritt fokussiert und überschaubar bleibt.
3. Fügen Sie Fortschrittsindikatoren hinzu, um Benutzenden zu helfen, ihren Fortschritt im Prozess zu verstehen.
4. Stellen Sie für die Navigation klare Steuerelemente wie die Schaltflächen „Weiter“, „Zurück“ und „Speichern“ bereit.

**Tipps zur Optimierung für Mobilgeräte**

- Verwenden Sie für Navigationssteuerelemente große Touch-Targets (mindestens 44 Pixel hoch), um die Zugänglichkeit zu verbessern.
- Stellen Sie sicher, dass die Schrittanzeigen auf kleinen Bildschirmen sichtbar und lesbar sind.
- Begrenzen Sie die Anzahl der Felder pro Schritt, um Scrolling zu minimieren und den Fokus zu verbessern.
- Aktivieren Sie die Funktion zum automatischen Speichern, um Datenverluste zu verhindern, wenn Benutzende das Formular verlassen.

**Best Practices**

- Gestalten Sie Schritte, die einem logischen Fortschritt folgen, wobei jeder Schritt auf dem vorherigen aufbaut.
- Verwenden Sie für jeden Schritt klare, beschreibende Titel, damit Benutzende wissen, was sie erwartet.
- Überprüfen Sie die Benutzereingabe bei jedem Schritt, um Fehler frühzeitig zu erkennen und Frustration zu reduzieren.
- Ermöglichen Sie Benutzenden, rückwärts zu navigieren, damit sie frühere Angaben überprüfen oder bearbeiten können, ohne Daten zu verlieren.

**Häufige Anwendungsszenarien**

- **Versicherungsansprüche:** Schritte für Vorfalldetails, Übermittlung von Beweismitteln, persönliche Daten und Überprüfung.
- **Kontoeinrichtung:** Schritte für grundlegende Daten, Präferenzen, Sicherheitseinstellungen und Bestätigung.
- **Bestellvorgang:** Schritte für Produktauswahl, Versanddaten, Zahlungsdetails und Bestellübersicht.

### Akkordeon-Layout

Das Akkordeon-Layout spart Platz, indem Inhalte in ausblendbaren Abschnitten organisiert werden. Das macht es ideal für optionale oder sekundäre Informationen. Dieses Layout eignet sich besonders für Formulare mit Inhalten, die logisch gruppiert werden können und nicht alle gleichzeitig angezeigt werden müssen.

![Beispiel für ein Akkordeon-Layout](/help/edge/docs/forms/universal-editor/assets/accordion-layout.png)

**Responsives Verhalten**

- **Mobile Leistung:** Nur der relevante Abschnitt wird erweitert, wodurch weniger gescrollt werden muss und die Ladezeiten verbessert werden.
- **Touch-optimierte Kopfzeilen:** Kopfzeilen von Abschnitten können einfach angetippt und erweitert werden, wodurch natürliche Gesten auf Mobilgeräten unterstützt werden.
- **Reibunglose Animationen:** Das Erweitern und Reduzieren von Abschnitten bietet bei Benutzerinteraktionen visuelles Feedback.
- **Platzeffizienz:** Das Ausblenden von Abschnitten minimiert den vertikalen Platzbedarf, sodass sich auf allen Geräten leichter durch das Formular navigieren lässt.

**Vorgehensweise bei der Implementierung**

1. Fügen Sie Ihrem Formular eine [Akkordeonkomponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) hinzu. 
2. Gruppieren Sie verwandte optionale oder sekundäre Inhalte in den einzelnen Akkordeon-Abschnitten.
3. Verwenden Sie für jeden Abschnitt klare, beschreibende Kopfzeilen, damit Benutzende wissen, welche Informationen darin enthalten sind.
4. Legen Sie die entsprechenden standardmäßigen offenen oder geschlossenen Status für einzelne Abschnitte anhand von Wichtigkeit und Benutzeranforderungen fest.

**Vorteile auf Mobilgeräten**

- Reduziert das Scrollen durch Ausblenden nicht verwendeter Abschnitte, sodass sich Benutzende jeweils auf einen Abschnitt konzentrieren können.
- Touch-optimierte Interaktion unterstützt natürliche Gesten zum Erweitern bzw. Reduzieren.
- Schnelleres Laden, da nur der aktive Inhalt sichtbar ist.
- Verbesserter Fokus, da die Benutzenden immer nur die Informationen sehen, die sie zu einem bestimmten Zeitpunkt benötigen.

**Best Practices**

- Verwenden Sie klare Abschnittsüberschriften, damit Benutzende wissen, was sie erwartet, bevor sie einen Abschnitt erweitern.
- Gruppieren Sie verwandte Inhalte logisch in den einzelnen Abschnitten, um das Verständnis zu erleichtern.
- Legen Sie für wichtige Abschnitte fest, dass sie schon zu Beginn erweitert angezeigt werden, wenn sofortige Aufmerksamkeit erforderlich ist.
- Stellen Sie kurze Abschnittsvorschauen oder Zusammenfassungen bereit, damit Benutzende entscheiden können, welche Abschnitte sie erweitern sollen.

**Häufige Anwendungsszenarien**

- **Produktkonfiguration:** Abschnitte für grundlegende Optionen, erweiterte Einstellungen, Zubehör und Support.
- **FAQ-Formulare:** Gruppierungen für Konto-, Abrechnungs-, technische und allgemeine Fragen.
- **Formulare für Einstellungen:** Abschnitte für Datenschutz, Benachrichtigungen, Darstellung und erweiterte Optionen.


## Teil 3: Best Practices für responsives Design

### Best Practices nach Gerätetyp

+++Optimierung für Mobilgeräte (320 Pixel - 767 Pixel)

**Layout und Interaktion:**

- Verwenden Sie ein einspaltiges Layout für alle Formularinhalte, um die Lesbarkeit und Anwenderfreundlichkeit zu maximieren.
- Stellen Sie sicher, dass alle Schaltflächen und interaktiven Elemente mindestens 44 Pixel hoch sind, um eine zuverlässige Touch-Interaktion zu ermöglichen.
- Sorgen Sie mit sichtbaren Schaltflächen für „Zurück“ und „Weiter“ für eine übersichtliche und bequeme Navigation.
- Minimieren Sie den Scrolling-Bedarf in einzelnen Abschnitten, indem Sie lange Formulare aufteilen.
- Fokussieren Sie automatisch auf das erste Eingabefeld, sodass die mobile Tastatur angezeigt wird.

**Richtlinien für Felder:**

- Textfelder sollten sich über die gesamte Breite des Bildschirms erstrecken und über einen für die Touch-Eingabe ausreichenden Abstand verfügen.
- Verwenden Sie native Dropdown-/Auswahlelemente für eine optimale Nutzung auf Mobilgeräten.
- Implementieren Sie eine native Datumsauswahl für ein konsistentes mobiles Erlebnis.
- Richten Sie große und klar beschriftete Bereiche für Datei-Uploads ein, um für einfachen Zugriff zu sorgen.

+++

+++Tablet-Optimierung (768px-1199px)

**Layout und Anwenderfreundlichkeit:**

- Verwenden Sie zweispaltige Layouts für verwandte Felder, um mehr Platz auf dem Bildschirm zu erhalten.
- Testen Sie das Aussehen und die Anwenderfreundlichkeit von Formularen sowohl im Hoch- als auch im Querformat.
- Gestalten Sie für die Touch- und Mauseingabe, sodass alle Bedienelemente leicht zugänglich sind.
- Vergrößern Sie den Inhaltsbereich unter Beibehaltung einer klaren visuellen Hierarchie und Lesbarkeit.

+++

+++Desktop-Optimierung (1200 px+)

**Erweiterte Funktionen und Layout:**

- Verwenden Sie mehrspaltige Layouts, um horizontalen Platz effizient zu nutzen und den vertikalen Bildlauf zu reduzieren.
- Geben Sie zur Unterstützung von Power-Benutzenden Tastaturbefehle für häufige Aktionen an.
- Implementieren Sie bei interaktiven Elementen Mausberührungsstatus und visuelles Feedback.
- Bieten Sie für komplexe Formulare eine erweiterte Validierung mit klaren, detaillierten Fehlermeldungen.

+++

## Konfigurieren von benutzerdefinierten Layouts mit Haltepunkten für Medienabfragen

Beim Erstellen benutzerdefinierter Layouts für Komponenten in adaptivem Forms mit dem **universellen Editor** müssen Sie das responsive Verhalten mithilfe von **CSS Media Query Breakpoints** definieren. Dadurch wird sichergestellt, dass Formulare auf verschiedenen Geräten und Bildschirmgrößen korrekt wiedergegeben werden.

**Empfohlene Haltepunkte (basierend auf AEM-Kernkomponenten)**

| **Gerätetyp** | **Empfohlener Breakpoint** |
|-----------------|---------------------------|
| **Desktop** | `min-width: 1200px` |
| **Tablet** | `min-width: 768px and max-width: 1199px` |
| **Mobilgerät** | `max-width: 767px` |

**Wichtigste Punkte**

- Verwenden Sie diese Haltepunkte, um zu steuern, wie Komponenten die Größe ändern, gestapelt oder auf verschiedenen Geräten ausgeblendet werden.
- Befolgen Sie die responsiven Design-Richtlinien Ihres Unternehmens für eine konsistente Benutzeroberfläche.
- Testen Sie Layouts auf mehreren Geräten und Ausrichtungen, um Benutzerfreundlichkeit und Barrierefreiheit zu gewährleisten.

```css
/* Example: Stack form fields on smaller screens */
@media (max-width: 767px) {
  .custom-form-container {
    display: flex;
    flex-direction: column;
  }
}
```

>[!NOTE]
>
> Der universelle Editor bietet keine Benutzeroberfläche zum Definieren des responsiven Verhaltens. Die gesamte Layout-Anpassung muss über CSS abgewickelt werden.



## Fehlerbehebung

### Layout-Probleme

+++Umbrüche des Formularlayouts auf Mobilgeräten

**Mögliche Ursachen:**

- Elemente mit fester Breite, die sich nicht an kleinere Bildschirme anpassen
- CSS, das zunächst für Desktops ausgelegt ist und mobile Stile überschreibt.
- Bilder oder Inhalte, die ihre Container überlaufen

**Fehlerbehebung:**

- Stellen Sie sicher, dass alle Bilder und Container relative oder prozentuale Größen verwenden.
- Beginnen Sie mit einem Mobile-First-CSS-Ansatz und fügen Sie dann Ergänzungen für größere Bildschirme hinzu.
- Testen Sie Formulare mit Geräteemulatoren und echten Geräten.
- Vermeiden Sie feste Abmessungen und verwenden Sie flexible Layouts.

+++

+++Touch-Ziele zu klein

**Mögliche Ursachen:**

- Schaltflächen oder Links kleiner als 44 x 44 px
- Interaktive Elemente zu nahe beieinander platziert
- Benutzerdefiniertes CSS zur Reduzierung der standardmäßigen Touch-Zielgröße

**Fehlerbehebung:**

- Stellen Sie sicher, dass jedes interaktive Element mindestens 44 x 44 px groß ist.
- Fügen Sie ausreichenden Abstand zwischen Schaltflächen, Links und anderen Steuerelementen hinzu.
- Testen Sie mit echten Touch-Geräten, nicht nur mit einer Maus.
- Erweitern Sie Touch-Zielbereiche nach Bedarf für bessere Zugänglichkeit.

+++

+++Probleme mit Inhaltsüberlauf

**Mögliche Ursachen:**

- Langer Text oder Beschriftungen, die nicht umschlossen sind
- Container mit festen Breiten
- Bilder, die nicht responsiv skaliert werden

**Fehlerbehebung:**

- Aktivieren Sie das Einschließen von Text für alle Beschriftungen und Inhalte.
- Verwenden Sie responsive Bilder, die mit dem Container skaliert werden.
- Gestalten Sie flexible Layouts, die sich an unterschiedliche Inhaltslängen anpassen.
- Testen Sie mit kurzen und langen Inhalten, um die Anpassungsfähigkeit zu prüfen.

+++

### Leistungsprobleme

+++Langsames Laden auf Mobilgeräten

**Mögliche Ursachen:**

- Große, nicht optimierte Bilder
- Intensives oder übermäßiges JavaScript
- Zu viele Formularfelder gleichzeitig geladen

**Fehlerbehebung:**

- Optimieren Sie Bilder für Mobilgeräte und verwenden Sie geeignete Dateiformate.
- Schieben Sie nicht-kritische Inhalte auf oder laden Sie sie verzögert.
- Minimieren Sie die Verwendung von externen Skripten und Widgets.
- Optimieren Sie Formularfelder so, dass nur das geladen wird, was erforderlich ist.

+++

### Test- und Validierungsprobleme

+++Unterschiede zwischen Emulator und tatsächlichem Gerät

**Mögliche Ursachen:**

- Diskrepanzen in Browser-Rendering-Engines
- Touch-Interaktion mit Maus nicht genau simuliert
- Diskrepanzen bei Netzwerkgeschwindigkeit

**Fehlerbehebung:**

- Testen Sie immer auf echten Geräten, nicht nur mit Emulatoren.
- Verwenden Sie für umfassende Tests verschiedene Browser und Geräte.
- Simulieren Sie verschiedene Netzwerkgeschwindigkeiten, um Leistungsengpässe zu identifizieren.
- Sammeln Sie Feedback von echten Benutzenden in Ihrer Zielgruppe.

+++

## Erfolgsmetriken für responsive Formulare

+++Wichtige Performance-Indikatoren

**Anwendererlebnis:**

- **Formularausfüllungsrate:** Zielen Sie bei Mobilgeräten auf 85 % oder mehr ab.
- **Dauer bis zum Abschluss:** Benutzende von Mobilgeräten sollten Formulare innerhalb von 20 % der Desktop-Ausführungszeiten ausfüllen.
- **Fehlerrate:** Sorgen Sie dafür, dass Validierungsfehler unter 5 % bleiben.
- **Abbruchpunkte:** Ermitteln und optimieren Sie Schritte, bei denen Benutzende gerne abbrechen.

**Technische Leistung:**

- **Ladezeit für eine Seite:** Weniger als 3 Sekunden bei einer 3G-Verbindung.
- **Core Web Vitals** Erreichen oder überschreiten Sie die von Google empfohlenen Schwellenwerte.
- **Zugänglichkeit:** Erfüllen Sie die WCAG 2.1 AA-Richtlinien.
- **Browser-Kompatibilität:** Stellen Sie sicher, dass in allen gängigen Browsern mehr als 98 % der Funktionen verfügbar sind.

+++

+++Checkliste für Tests

**Checkliste vor der Veröffentlichung:**

- Testen Sie das Formular auf echten Mobilgeräten (nicht nur mit Emulatoren).
- Stellen Sie sicher, dass alle Touch-Ziele mindestens 44 x 44 Pixel groß sind.
- Überprüfen Sie die Lesbarkeit des Texts in allen unterstützten Bildschirmgrößen.
- Vergewissern Sie sich, dass die Formularvalidierung über Geräte und Browser hinweg konsistent funktioniert.
- Sorgen Sie dafür, dass die Ladezeit bei Mobilgeräten unter 3 Sekunden liegt.
- Überprüfen Sie, ob über Tastatur und Bildschirmlesehilfen auf alle interaktiven Elemente zugegriffen werden kann.
- Testen Sie die Formularübermittlung auf allen unterstützten Geräten.


+++

## Nächste Schritte

**Sofortige Maßnahmen:**

1. **Prüfen Sie Ihre bestehenden Formulare:** Testen Sie vorhandene Formulare mithilfe des Geräteemulators.
2. **Ermitteln Sie schnelle Erfolge:** Beheben Sie zunächst offensichtliche Probleme mit der Anwenderfreundlichkeit auf Mobilgeräten.
3. **Räumen Sie Formularen mit hohem Traffic Priorität ein:** Konzentrieren Sie sich auf Formulare mit der größten Auswirkung auf Benutzende.
4. **Implementieren Sie einen Mobile-First-Ansatz:** Beginnen Sie mit dem kleinsten Bildschirm-Design.

**Erweiterte Optimierung:**

- **Leistungsüberwachung:** Richten Sie Analysen ein, um Formularmetriken zu verfolgen.
- **A/B-Tests:** Experimentieren Sie mit verschiedenen Layouts und Ansätzen.
- **Sammlung von Feedback:** Sammeln Sie Erkenntnisse von echten Benutzenden.
- **Fortlaufende Verbesserung:** Sorgen Sie für eine regelmäßige Überprüfung und Optimierung von Formularen.


