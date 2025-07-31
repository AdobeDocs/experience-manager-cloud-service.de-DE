---
title: Grundlegendes zum universellen Editor – responsiver Modus
description: In diesem Artikel wird erläutert, wie Sie mit verschiedenen Emulatoren im universellen Editor eine Vorschau von Formularen anzeigen können, um während des Authorings ihr Erscheinungsbild zu visualisieren.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 0c7fb491-4bad-4202-a472-87e6e6d9ab40
source-git-commit: 9ef4c5638c2275052ce69406f54dda3ea188b0ef
workflow-type: ht
source-wordcount: '1247'
ht-degree: 100%

---


# Responsiver Modus beim WYSIWYG-Authoring

<span class="preview"> Dies ist eine Vorabveröffentlichungsfunktion, die über unseren <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=de#new-features">Vorabveröffentlichungskanal</a> verfügbar ist. </span>

## Einführung in responsive Formulare

In der heutigen Welt, in der zahlreiche Geräte verwendet werden, müssen Ihre Formulare auf Bildschirmen aller Größen – von Desktop-Monitoren bis hin zu Smartphones – großartig aussehen und gut funktionieren. Dies erreichen Sie mit dem responsiven Modus im universellen Editor, indem Sie Ihre Formulare während des Erstellungsprozesses über verschiedene Gerätegrößen hinweg in der Vorschau anzeigen und testen können.

Im [universellen Editor](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) können Sie Formulare erstellen, die sich automatisch an verschiedene Bildschirmgrößen anpassen und unabhängig vom verwendeten Gerät ein optimales Anwendererlebnis bieten.

## Anzeigen einer Vorschau von Formularen im responsiven Modus für unterschiedliche Geräte

Der universelle Editor bietet ein **Emulator**-Symbol oben rechts auf dem Bildschirm, mit dem Sie Seiten in unterschiedlichen Gerätegrößen in der Vorschau anzeigen und das Verhalten Ihres responsiven Designs testen können, um das Benutzererlebnis zu verbessern.

So zeigen Sie ein Formular im responsiven Modus in der Vorschau an:

1. Öffnen Sie das Formular im universellen Editor zur Bearbeitung.
2. Klicken Sie auf das Symbol ![Emulator-Symbol mit einem Gerätevorschausymbol](/help/edge/docs/forms/universal-editor/assets/emulator.png){height=2%,width=2%} in der Symbolleiste.
3. Wählen Sie ein Geräteformat aus:
   - Desktop (Standard)
   - Tablet
   - Mobilgerät
   - Benutzerdefiniert (Breite und Höhe angeben)

![Screenshot des universellen Editors mit Optionen für den responsiven Modus für verschiedene Geräte](/help/edge/docs/forms/universal-editor/assets/universal-editor-emulator.png)

Mit dem Symbol **Bildschirmdrehung** können Sie bei der Vorschau auf Tablets oder Mobilgeräten Geräten zwischen Hoch- und Querformat umschalten. 

Der universelle Editor bietet verschiedene Emulatoren zum Anzeigen einer Vorschau von Formularen auf unterschiedlichen Geräten. In der folgenden Tabelle sind die verfügbaren Emulatortypen zusammen mit den entsprechenden Gerätedarstellungen aufgeführt:

<table border="1" style="text-align:" left; border-collapse: collapse;">
    <tr>
        <th style="width: 20%">Emulatortyp</th>
        <th style="width: 80%">Gerätebild</th>
    </tr>
    <tr>
        <td style="width: 20%">Desktop</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-desktop.png" alt="Desktop-Ansicht eines Formulars mit dem Layout mit voller Breite" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Tablet</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-tab.png" alt="Tabellenansicht eines Formulars mit dem Layout mit mittlerer Breite und angepassten Komponenten" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Mobilgerät</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-mobile.png" alt="Mobilgeräteansicht eines Formulars mit schmalem Layout und gestapelten Komponenten" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Benutzerdefiniertes Gerät</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-custom.png" alt="Benutzerdefinierte Geräteansicht eines Formulars mit benutzerdefinierten Dimensionen" style="width: auto; height: auto"></td>
    </tr>
</table>

## Layout-Möglichkeiten

Mit dem universellen Editor können Sie benutzerfreundliche Formulare erstellen, die Endbenutzenden dynamische Erlebnisse bieten. Das Formular-Layout steuert, wie Elemente oder Komponenten in einem Formular angezeigt werden.

Der universelle Editor unterstützt die folgenden Arten von Layouts für Formulare:

- [Panel-Layout](#panel-layout)
- [Assistenten-Layout](#wizard-layout)
- [Akkordeon-Layout](#accordion-layout)

### Panel-Layout

Das Bedienfeld-Layout ist nützlich, um verwandte Felder so zu organisieren, dass die Navigation und das Auffinden entsprechender Inhalte erleichtert werden. Das Panel-Layout ordnet Formularkomponenten in verschiedenen Abschnitten oder Panels in Formularen an.

![Panel-Layout mit mehreren unterschiedlichen Abschnitten innerhalb eines Formulars](/help/edge/docs/forms/universal-editor/assets/panel-layout.png)

**Beispiel:** Ein Bewerbungsformular kann Panels verwenden, um „Persönliche Daten“, „Ausbildung“, „Berufserfahrung“ und „Referenzen“ in verschiedene Abschnitte zu unterteilen.

**Responsives Verhalten:** Auf kleineren Bildschirmen werden Panels normalerweise vertikal gestapelt. Dabei werden die unterschiedlichen Gruppierungen beibehalten und gleichzeitig eine Anpassung an die schmalere Breite durchgeführt.

Sie können die [Bedienfeldkomponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) verwenden, um das Bedienfeld-Layout einem Formular hinzuzufügen. Detaillierte Anweisungen zum Konfigurieren verschiedener Eigenschaften der Bedienfeldkomponente finden Sie im Artikel [Bedienfeldkomponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel).

### Assistenten-Layout

Das Assistenten-Layout vereinfacht ein komplexes Formular, indem es in verschiedene Schritte unterteilt wird. Jeder Schritt stellt einen anderen Teil des Prozesses dar, und Benutzende navigieren häufig mit den Schaltflächen **Weiter** und **Zurück** nacheinander durch die Schritte. Sie können das Assistenten-Layout verwenden, um ein Formular zu erstellen, das mehrere Abschnitte oder Schritte umfasst.

![Assistenten-Layout mit einem mehrstufigen Formular mit Navigationssteuerelementen](/help/edge/docs/forms/universal-editor/assets/wizard-layout.png)

**Beispiel:** Ein Antragsformular für Versicherungsleistungen kann Benutzende über einen Assistenten durch die Schritte zum Bereitstellen von Details zu einem Vorfall, Hochladen von Belegen, Eingeben persönlicher Daten und Überprüfen der Einreichung führen.

**Responsives Verhalten:** Auf Mobilgeräten behält der Assistent seinen Schritt-für-Schritt-Ansatz bei, passt den Inhalt jedoch in jedem Schritt an den schmaleren Bildschirm an und stapelt häufig Elemente, die auf größeren Bildschirmen nebeneinander angezeigt würden.

Sie können die [Assistenten-Komponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) verwenden, um das Assistenten-Layout in einem Formular hinzuzufügen. Detaillierte Anweisungen zum Konfigurieren der verschiedenen Eigenschaften der Assistenten-Komponente finden Sie im Artikel [Assistenten-Komponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard).

### Akkordeon-Layout

Das Akkordeon-Layout zeigt Inhalte in reduzierbaren Abschnitten oder Bedienfeldern in einem adaptiven Formular an. Wenn ein Abschnitt erweitert wird, wird der Inhalt darin angezeigt, während andere Abschnitte reduziert bleiben. Dieses Layout eignet sich ideal für das Anzeigen großer Informationsmengen in kompakter Form.

![Akkordeon-Layout mit erweiterbaren Abschnitten in einem Formular](/help/edge/docs/forms/universal-editor/assets/accordion-layout.png)

**Beispiel:** Ein Formular zur Produktkonfiguration kann Akkordeon-Abschnitte für „Grundlegende Optionen“, „Erweiterte Funktionen“, „Zubehör“ und „Zahlungspläne“ verwenden, sodass sich Benutzende jeweils auf einen Aspekt konzentrieren können.

**Responsives Verhalten:** Akkordeons eignen sich besonders gut für Mobilgeräte, da sie auf natürliche Weise vertikalen Raum sparen, indem sie nur den erweiterten Inhaltsbereich anzeigen. Dadurch sind sie ideal für kleinere Bildschirme.

Sie können die [Akkordeon-Komponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) verwenden, um das Akkordeon-Layout in einem Formular hinzuzufügen. Detaillierte Anweisungen zum Konfigurieren der verschiedenen Eigenschaften der Akkordeon-Komponente finden Sie im Artikel [Akkordeon-Komponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion).

### Auswählen des richtigen Layouts?

Für die Optimierung des Benutzererlebnisses und der Formularfunktionen ist die Auswahl des richtigen Layouts von entscheidender Bedeutung. Die Tabelle hilft Ihnen, die verschiedenen verfügbaren Layout-Optionen zu verstehen, und dient Ihnen als Orientierung bei der Auswahl des am besten geeigneten Layouts basierend auf Ihren spezifischen Anforderungen und Anwendungsszenarien:

| Funktion | Panel-Layout | Assistenten-Layout | Akkordeon-Layout |
|----------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
| **Zweck** | Gruppiert verwandte Inhalte in unterschiedliche Abschnitte | Führt Benutzende durch einen mehrstufigen Prozess oder ein mehrstufiges Formular | Organisiert Inhalte in reduzierbare Abschnitte |
| **Struktur** | Unterschiedliche Abschnitte | Sequenzielle Schritte/Seiten | Reduzierbare Bedienfelder/Abschnitte |
| **Navigation** | Klicken Sie zum Navigieren auf die Bedienfeldkopfzeilen | - Vorwärts: Schaltfläche „Weiter“<br>- Rückwärts: Schaltfläche „Zurück“<br>- Optionales Überspringen von Schritten | Anklickbare Kopfzeilen zum Erweitern/Reduzieren von Abschnitten |
| **Anwendererlebnis** | Organisiert große Inhaltsmengen auf überschaubare Weise | Schrittweise Anleitung zur Verringerung der Überlastung | Kompakte Ansicht mit erweiterten/reduzierten Abschnitten |
| **Nutzungsszenario** | Komplexe Formulare mit kategorisierten Abschnitten | Einrichtungsprozesse, komplexe Formulare | Häufig gestellte Fragen, Einstellungsmenüs, detaillierte Inhaltsabschnitte |
| **Optimiert für Mobilgeräte** | Moderat – vertikales Stapeln der Panels | Gut – Fokus ausschließlich auf aktuellem Schritt | Hervorragend – platzsparend mit reduzierbaren Abschnitten |

## Best Practices für responsive Formulare

Stellen Sie mithilfe der folgenden Best Practices sicher, dass Ihre Formulare auf allen Geräten ein optimales Erlebnis bieten:

1. **Zuerst für Mobilgeräte entwickeln:** Gestalten Sie Ihr Formular zunächst für Mobilgeräte und erweitern Sie es dann für größere Bildschirme. Dadurch wird sichergestellt, dass die Kernfunktionen auch auf sehr kleinen Bildschirmen verwendet werden können.

2. **Geeignete Feldtypen verwenden:** Wählen Sie Feldtypen aus, die auf Touch-Geräten gut funktionieren:
   - Verwenden Sie Dropdown-Listen anstelle von Optionsfeldern, wenn viele Optionen vorhanden sind.
   - Verwenden Sie eine Datumsauswahl zur Touch-Eingabe.
   - Stellen Sie sicher, dass Schaltflächen und Touch-Ziele mindestens 44 x 44 Pixel groß sind.

3. **Für kleinere Bildschirme vereinfachen:**
   - Lassen Sie auf Mobilgeräten weniger Felder pro Zeile anzeigen.
   - Ziehen Sie in Betracht, optionale Felder hinter einer Option „Mehr anzeigen“ zu verbergen.
   - Teilen Sie auf Mobilgeräten komplexe Formulare in mehrere Schritte auf.

4. **Gründlich testen:** Testen Sie Ihre Formulare immer auf den eigentlichen Geräten oder stellen Sie mit dem Emulatormodus im universellen Editor sicher, dass sie in allen Bildschirmgrößen ordnungsgemäß funktionieren.

5. **Ladezeiten berücksichtigen:** Optimieren Sie Bildgrößen und minimieren Sie die erforderlichen Ressourcen, insbesondere für mobile Benutzende, die ggf. über langsamere Verbindungen verfügen.

## Fehlerbehebung bei responsiven Formularen

| Problem | Mögliche Ursache | Lösung |
|-------|---------------|----------|
| Formular wird auf Mobilgeräten abgeschnitten angezeigt | Feste Breiteneinstellungen oder Überlaufprobleme | Relative Einheiten (%, rem) anstelle von Pixeln verwenden und auf overflow:hidden-Eigenschaften prüfen |
| Touch-Elemente mit schwieriger Interaktion | Touch-Ziele zu klein oder zu nah beieinander | Schaltfläche/Eingabegröße auf mindestens 44 x 44 Pixel vergrößern und mehr Platz zwischen interaktiven Elementen einfügen |
| Inhaltsüberläufe auf kleinen Bildschirmen | Keine responsiven Regeln für kleinere Viewports | Medienabfragen oder responsive Klassen hinzufügen, um das Layout für verschiedene Bildschirmgrößen anzupassen |
| Formular auf Mobilgeräten zu langsam | Große Bilder oder zu viele Skripte | Bilder optimieren, JavaScript minimieren und Lazy Loading für nicht kritische Elemente in Betracht ziehen |
| Unterschiedliches Erscheinungsbild bei Emulator und echten Geräten | Browser-spezifisches Rendering oder Gerätevarianten | Nach Möglichkeit auf den eigentlichen Geräten testen, nicht nur auf Emulatoren |

## Siehe auch

{#see-more-eds-forms}
