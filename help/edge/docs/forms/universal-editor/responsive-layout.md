---
title: Erstellen einer responsiven Forms mit einem universellen Editor
description: Erfahren Sie, wie Sie mit dem universellen Editor responsive Formulare für alle Geräte entwerfen, testen und optimieren können. Übergeordnete Gerätetests, Layout-Muster und Mobiloptimierungstechniken für AEM Forms mit Edge Delivery Services.
keywords: Responsive Formulare, Formulare für Mobilgeräte, Gerätetests, universeller Editor, adaptives Layout, Formularoptimierung, mobiles Design, responsives Design, Formularlayouts, Geräteemulator
feature: Edge Delivery Services
role: User, Developer
level: Beginner
exl-id: 0c7fb491-4bad-4202-a472-87e6e6d9ab40
source-git-commit: 44a8d5d5fdd2919d6d170638c7b5819c898dcefe
workflow-type: tm+mt
source-wordcount: '2383'
ht-degree: 1%

---


# Erstellen einer responsiven Forms mit einem universellen Editor

Die moderne Web-Landschaft erfordert Formulare, die über ein immer breiteres Spektrum von Geräten und Bildschirmgrößen hinweg nahtlos funktionieren. Von großen Desktop-Monitoren bis hin zu kompakten Smartphone-Bildschirmen erwarten die Benutzer unabhängig vom gewählten Gerät konsistente, intuitive Erlebnisse. Das Erstellen responsiver Formulare ist nicht mehr optional. Es ist eine grundlegende Voraussetzung für die Bereitstellung professioneller, barrierefreier und konversionsoptimierter digitaler Erlebnisse.

Der universelle Editor bietet umfassende Tools und Methoden zum Entwickeln responsiver Formulare, die sich intelligent an verschiedene Bildschirmabmessungen, Eingabemethoden und Benutzerkontexte anpassen. In diesem Handbuch werden die technischen Grundlagen, Implementierungsstrategien und Optimierungstechniken untersucht, die zum Erstellen von Formularen erforderlich sind, die eine außergewöhnliche Leistung auf allen Geräten erbringen und gleichzeitig die Benutzerfreundlichkeit, Barrierefreiheit und visuelle Attraktivität aufrechterhalten.

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

Das Bedienfeldlayout organisiert verwandte Inhalte in visuell unterschiedliche Abschnitte, sodass Benutzende mehrere Abschnitte gleichzeitig anzeigen können. Dieses Layout eignet sich ideal für Formulare mit kategorisierten Informationen, die von einer Side-by-Side-Präsentation auf größeren Bildschirmen profitieren.

![Beispiel für ein Bedienfeld-Layout](/help/edge/docs/forms/universal-editor/assets/panel-layout.png)

**Responsives Verhalten**

- **Desktop (1200 Pixel und höher):** Bedienfelder werden nebeneinander oder in einem Raster angezeigt, um eine maximale Sichtbarkeit zu erzielen.
- **Tablet (768px-1199px):** Panels werden vertikal mit angemessenem Abstand gestapelt, um die Klarheit zu wahren.
- **Mobil (320px-767px):** Bedienfelder werden in einem einspaltigen Layout mit einer klaren Trennung zwischen Abschnitten für eine einfache Navigation präsentiert.

**Implementierung**

1. Fügen Sie die [Bedienfeldkomponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) zu Ihrem Formular hinzu.
2. Gruppieren Sie verwandte Felder innerhalb jedes Bedienfelds, um die logische Organisation beizubehalten.
3. Weisen Sie jedem Bedienfeldabschnitt klare, beschreibende Überschriften zu.
4. Stellen Sie sicher, dass ausreichend Abstand zwischen den Bereichen vorhanden ist, um visuelle Übersichtlichkeit zu vermeiden.

**Best Practices**

- Begrenzen Sie die Anzahl der Bedienfelder auf dem Desktop auf 3 oder 4, um zu vermeiden, dass Benutzer überfordert werden.
- Verwenden Sie knappe, beschreibende Titel für jedes Bedienfeld, um das Verständnis der Benutzer zu verbessern.
- Organisieren Sie Felder in Bedienfeldern logisch, um kognitive Belastung zu minimieren.
- Testfeld-Navigation auf Touch-Geräten, um die Benutzerfreundlichkeit auf allen Plattformen sicherzustellen.

**Häufige Anwendungsfälle**

- **Bewerbung:** Abschnitte für persönliche Informationen, Bildung, Erfahrung und Referenzen.
- **Produktregistrierung:** für grundlegende Details, technische Spezifikationen und Garantieinformationen.
- **Umfrage Forms:** Gruppierungen für Demografie, Voreinstellungen, Feedback und Kontaktinformationen.

### Assistenten-Layout

Der Assistenten-Layout führt Benutzende durch einen mehrstufigen Prozess und zeigt jeweils einen Abschnitt an. Dieses Layout ist besonders bei komplexen Formularen effektiv, da es die kognitive Belastung reduziert und die Abschlussraten erhöht, indem der Prozess in überschaubare Schritte unterteilt wird.

![Beispiel für Assistentenlayout](/help/edge/docs/forms/universal-editor/assets/wizard-layout.png)

**Responsives Verhalten**

- **Alle Geräte:** Behält den einstufigen Fokus bei, der für mobile Benutzer optimal ist.
- **Schrittinhalt:** Jeder Schritt passt sich responsiv an, stapelt Felder oder ordnet sie je nach Bildschirmgröße nebeneinander an.
- **Navigation:** Verfügt über berührungsfreundliche Schaltflächen mit ausreichendem Abstand für eine einfache Interaktion.
- **Fortschrittsanzeige:** Fortschrittsbalken oder Schrittanzeigen werden für verschiedene Geräte entsprechend skaliert und bieten ein klares Feedback zum Abschlussstatus.

**Implementierung**

1. Fügen Sie die [Assistenten-Komponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) in Ihr Formular ein.
2. Teilt das Formular in logische Schritte auf, idealerweise zwischen 3 und 7, damit jeder Schritt fokussiert und verwaltbar bleibt.
3. Fügen Sie Fortschrittsindikatoren hinzu, um Benutzenden zu helfen, ihre Position im Prozess zu verstehen.
4. Stellen Sie klare Navigationssteuerelemente wie die Schaltflächen „Weiter“, „Zurück“ und „Speichern“ bereit.

**Tipps zur Optimierung von Mobilgeräten**

- Verwenden Sie große Touch-Targets (mindestens 44 Pixel hoch) für Navigationssteuerelemente, um die Barrierefreiheit zu verbessern.
- Stellen Sie sicher, dass die Schrittmarkierungen auf kleinen Bildschirmen sichtbar und lesbar sind.
- Begrenzen Sie die Anzahl der Felder pro Schritt, um den Bildlauf zu minimieren und den Fokus zu verbessern.
- Aktivieren Sie die Funktion zum automatischen Speichern, um Datenverlust zu verhindern, wenn Benutzer das Formular verlassen.

**Best Practices**

- Entwickeln Sie Schritte, um einem logischen Fortschritt zu folgen, wobei jeder Schritt auf dem vorherigen aufbaut.
- Verwenden Sie klare, beschreibende Titel für jeden Schritt, um die Erwartungen der Benutzenden festzulegen.
- Überprüfen Sie die Benutzereingabe bei jedem Schritt, um Fehler frühzeitig zu erkennen und Frustration zu reduzieren.
- Ermöglichen Sie Benutzern, rückwärts zu navigieren, um frühere Informationen zu überprüfen oder zu bearbeiten, ohne Daten zu verlieren.

**Häufige Anwendungsfälle**

- **Versicherungsansprüche:** Schritte für Details zu Vorfällen, Übermittlung von Beweismitteln, persönliche Informationen und Überprüfung.
- **Kontoeinrichtung:** Schritte für grundlegende Informationen, Voreinstellungen, Sicherheitseinstellungen und Bestätigung.
- **Bestellvorgang:** Schritte für die Produktauswahl, Versandinformationen, Zahlungsdetails und die Bestellübersicht.

### Akkordeon-Layout

Das Akkordeon-Layout spart Platz, indem Inhalte in ausblendbaren Abschnitten organisiert werden, was es ideal für optionale oder sekundäre Informationen macht. Dieses Layout ist besonders effektiv für Formulare mit Inhalten, die logisch gruppiert werden können und nicht alle gleichzeitig angezeigt werden müssen.

![Beispiel für ein Akkordeon-Layout](/help/edge/docs/forms/universal-editor/assets/accordion-layout.png)

**Responsives Verhalten**

- **Leistung für Mobilgeräte:** Nur der relevante Abschnitt wird erweitert, wodurch der Bedarf an Scrollen verringert und die Ladezeiten verbessert werden.
- **Touch-optimierte Kopfzeilen:** Kopfzeilen von Abschnitten können einfach angetippt und erweitert werden, wodurch natürliche Gesten auf Mobilgeräten unterstützt werden.
- **Smooth Animations** Das Erweitern und Reduzieren von Abschnitten bietet visuelles Feedback für Benutzerinteraktionen.
- **Platzeffizienz:** ausgeblendete Abschnitte minimieren den vertikalen Platz, sodass das Formular auf allen Geräten einfacher navigiert werden kann.

**Implementierung**

1. Fügen Sie die [Akkordeon-Komponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) zu Ihrem Formular hinzu.
2. Gruppieren Sie verwandte optionale oder sekundäre Inhalte in jedem Akkordeon-Abschnitt.
3. Verwenden Sie für jeden Abschnitt klare, beschreibende Kopfzeilen, damit Benutzer verstehen, welche Informationen darin enthalten sind.
4. Legen Sie die entsprechenden standardmäßigen offenen oder geschlossenen Status für jeden Abschnitt basierend auf Wichtigkeit und Benutzeranforderungen fest.

**Vorteile für Mobilgeräte**

- Reduziert den Bildlauf durch Reduzieren nicht verwendeter Abschnitte, sodass sich Benutzende jeweils auf einen Abschnitt konzentrieren können.
- Die Touch-optimierte Interaktion unterstützt natürliche Gesten zum Erweitern/Reduzieren.
- Schnelleres Laden, da nur der aktive Inhalt sichtbar ist.
- Der Fokus wurde verbessert, da Benutzende immer nur die Informationen sehen, die sie zu einem bestimmten Zeitpunkt benötigen.

**Best Practices**

- Verwenden Sie klare Abschnittsüberschriften, damit Benutzer wissen, was sie erwarten können, bevor sie einen Abschnitt erweitern.
- Gruppieren Sie verwandte Inhalte logisch in jedem Abschnitt, um das Verständnis zu erleichtern.
- Legen Sie wichtige Abschnitte fest, um mit einem erweiterten Fenster zu beginnen, wenn sofortiges Eingreifen erforderlich ist.
- Stellen Sie kurze Abschnittsvorschauen oder Zusammenfassungen bereit, damit Benutzende entscheiden können, welche Abschnitte erweitert werden sollen.

**Häufige Anwendungsfälle**

- **Produktkonfiguration:** Abschnitte für grundlegende Optionen, erweiterte Einstellungen, Zubehör und Support.
- **FAQ Forms:** Gruppierungen für Konto-, Abrechnungs-, technische und allgemeine Fragen.
- **Einstellungen Forms:** Abschnitte für Datenschutz, Benachrichtigungen, Darstellung und erweiterte Optionen.


## Teil 3: Best Practices für responsives Design

### Best Practices nach Gerätetyp

+++Optimierung für Mobilgeräte (320 Pixel - 767 Pixel)

**Layout und Interaktion:**

- Verwenden Sie ein einspaltiges Layout für alle Formularinhalte, um die Lesbarkeit und Benutzerfreundlichkeit zu maximieren.
- Stellen Sie sicher, dass alle Schaltflächen und interaktiven Elemente mindestens 44 Pixel hoch sind, um eine zuverlässige Touch-Interaktion zu gewährleisten.
- Bieten Sie eine klare, einfache Navigation mit sichtbaren Schaltflächen für „Zurück“ und „Weiter“.
- Die langen Formulare müssen nicht in jedem Abschnitt gescrollt werden.
- Automatisch auf das erste Eingabefeld fokussieren, um die mobile Tastatur anzuzeigen.

**Feldrichtlinien:**

- Textfelder sollten sich über die gesamte Breite des Bildschirms erstrecken und über einen für die Touch-Eingabe ausreichenden Abstand verfügen.
- Verwenden Sie native Dropdown-/Auswahlelemente für eine optimale Mobile-Nutzung.
- Native Datumsauswahl für ein konsistentes mobiles Erlebnis implementieren
- Erstellen Sie große und klar beschriftete Bereiche für den Datei-Upload, um einen einfachen Zugriff zu ermöglichen.

+++

+++Tablet-Optimierung (768px-1199px)

**Layout und Benutzerfreundlichkeit:**

- Verwenden Sie zweispaltige Layouts für verwandte Felder, um mehr Platz auf dem Bildschirm zu nutzen.
- Testen Sie das Aussehen und die Benutzerfreundlichkeit der Formulare sowohl im Hoch- als auch im Querformat.
- Design für Touch- und Mauseingabe, sodass alle Bedienelemente leicht zugänglich sind.
- Vergrößern Sie den Inhaltsbereich unter Beibehaltung einer klaren visuellen Hierarchie und Lesbarkeit.

+++

+++Desktop-Optimierung (1200 px+)

**Erweiterte Funktionen und Layout:**

- Verwenden Sie mehrspaltige Layouts, um horizontalen Platz effizient zu nutzen und den vertikalen Bildlauf zu reduzieren.
- Bereitstellen von Tastaturbefehlen für häufige Aktionen zur Unterstützung von Power-Benutzern.
- Implementieren Sie Hover-Status und visuelles Feedback für interaktive Elemente.
- Bieten Sie eine erweiterte Validierung mit klaren, detaillierten Fehlermeldungen für komplexe Formulare.

+++

## Umfassende Fehlerbehebung

### Layout-Probleme

+++Umbrüche des Formularlayouts auf Mobilgeräten

**Mögliche Ursachen:**

- Elemente mit fester Breite, die sich nicht an kleinere Bildschirme anpassen
- Desktop-First-CSS, das Mobile-Stile überschreibt
- Bilder oder Inhalte überlaufen ihre Container

**Fehlerbehebung:**

- Stellen Sie sicher, dass alle Bilder und Container eine relative oder prozentuale Größe verwenden.
- Beginnen Sie mit einem Mobile-First-CSS-Ansatz und fügen Sie Verbesserungen für größere Bildschirme hinzu.
- Testen Sie Formulare mit Geräteemulatoren und echten Geräten.
- Vermeiden Sie feste Abmessungen und verwenden Sie flexible Layouts.

+++

+++Touch-Ziele zu klein

**Mögliche Ursachen:**

- Schaltflächen oder Links kleiner als 44 x 44 Pixel
- Interaktive Elemente zu nahe beieinander platziert
- Benutzerdefiniertes CSS zur Reduzierung der standardmäßigen Touch-Zielgröße

**Fehlerbehebung:**

- Stellen Sie sicher, dass jedes interaktive Element mindestens 44 Pixel x 44 Pixel groß ist.
- Fügen Sie einen ausreichenden Abstand zwischen Schaltflächen, Links und anderen Steuerelementen hinzu.
- Testen Sie mit echten Touch-Geräten, nicht nur mit einer Maus.
- Erweitern Sie die Touch-Zielbereiche nach Bedarf für die Barrierefreiheit.

+++

+++Probleme mit Inhaltsüberläufen

**Mögliche Ursachen:**

- Langer Text oder Beschriftungen, die nicht umbrechen
- Behälter mit festen Breiten
- Bilder, die nicht responsiv skaliert werden

**Fehlerbehebung:**

- Aktivieren Sie den Textumbruch für alle Beschriftungen und Inhalte.
- Verwenden Sie responsive Bilder, die mit dem Container skaliert werden.
- Entwerfen Sie flexible Layouts, die sich an unterschiedliche Inhaltslängen anpassen lassen.
- Testen Sie mit kurzen und langen Inhalten, um die Anpassungsfähigkeit sicherzustellen.

+++

### Leistungsprobleme

+++Langsames Laden auf Mobilgeräten

**Mögliche Ursachen:**

- Große, nicht optimierte Bilder
- Starkes oder übermäßiges JavaScript
- Zu viele Formularfelder gleichzeitig geladen

**Fehlerbehebung:**

- Optimieren Sie Bilder für Mobilgeräte und verwenden Sie geeignete Dateiformate.
- Nicht kritische Inhalte aufschieben oder verzögert laden.
- Minimieren Sie die Verwendung von Skripten und Widgets von Drittanbietern.
- Formularfelder optimieren, um nur das zu laden, was erforderlich ist.

+++

### Test- und Validierungsprobleme

+++Emulator im Vergleich zu echten Geräteunterschieden

**Mögliche Ursachen:**

- Unterschiede bei Browser-Rendering-Engines
- Touch-Interaktion mit der Maus nicht genau simuliert
- Diskrepanzen bei der Netzwerkgeschwindigkeit

**Fehlerbehebung:**

- Testen Sie immer auf echten Geräten zusätzlich zu den Emulatoren.
- Verwenden Sie mehrere Browser und Geräte für umfassende Tests.
- Simulieren Sie verschiedene Netzwerkgeschwindigkeiten, um Leistungsengpässe zu identifizieren.
- Sammeln Sie Feedback von echten Benutzern in Ihrer Zielgruppe.

+++

## Erfolgsmetriken für responsive Forms

+++Wichtige Leistungsindikatoren

**Benutzererlebnis:**

- **Formularausfüllungsrate:** Sie auf Mobilgeräten 85 % oder mehr an.
- **Zeit bis zum Abschluss:** Benutzer von Mobilgeräten sollten Formulare innerhalb von 20 % der Desktop-Ausführungszeiten ausfüllen.
- **Fehlerrate:** Validierungsfehler unter 5 %.
- **Abbruchpunkte:** Identifizieren und Beheben von Schritten, bei denen Benutzer abbrechen.

**Technische Leistung:**

- **Seitenladezeit:** als 3 Sekunden bei einer 3G-Verbindung.
- **Core Web Vitals** Die von Google empfohlenen Schwellenwerte erreichen oder überschreiten.
- **Barrierefreiheit:** Einhaltung der WCAG 2.1 AA-Richtlinien.
- **Browser-Kompatibilität:** Stellen Sie sicher, dass in allen gängigen Browsern mehr als 98 % Funktionalität verfügbar ist.

+++

+++Checkliste testen

**Checkliste vor der Veröffentlichung:**

- Testen Sie das Formular auf tatsächlichen Mobilgeräten (nicht nur Emulatoren).
- Stellen Sie sicher, dass alle Touch-Ziele mindestens 44 Pixel × 44 Pixel groß sind.
- Überprüfen Sie die Lesbarkeit des Texts in allen unterstützten Bildschirmgrößen.
- Bestätigen, dass die Formularvalidierung über Geräte und Browser hinweg konsistent funktioniert.
- Stellen Sie sicher, dass die Ladezeit für Mobilgeräte unter 3 Sekunden liegt.
- Überprüfen Sie, ob über Tastatur und Bildschirmlesehilfen auf alle interaktiven Elemente zugegriffen werden kann.
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


