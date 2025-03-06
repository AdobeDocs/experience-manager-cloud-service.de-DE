---
title: Grundlegendes zum universellen Editor – responsiver Modus
description: In diesem Artikel wird erläutert, wie Sie mit verschiedenen Emulatoren im universellen Editor eine Vorschau von Formularen anzeigen können, um während des Authorings ihr Erscheinungsbild zu visualisieren.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 0c7fb491-4bad-4202-a472-87e6e6d9ab40
source-git-commit: 9127c58a72dc4942312907f9e8f0cdcc8de9aa4b
workflow-type: tm+mt
source-wordcount: '1285'
ht-degree: 8%

---


# Responsiver Modus beim WYSIWYG-Authoring

<span class="preview"> Diese Funktion ist über das Early-Access-Programm verfügbar. Um den Zugriff anzufordern, senden Sie eine E-Mail mit dem Namen Ihrer GitHub-Organisation und dem Repository-Namen von Ihrer offiziellen Adresse an <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a> . Wenn die Repository-URL beispielsweise https://github.com/adobe/abc lautet, lautet der Organisationsname adobe und der Repository-Name abc.</span>

## Einführung in Responsive Forms

In der heutigen Welt mit mehreren Geräten müssen Ihre Formulare auf Bildschirmen aller Größen - von Desktop-Monitoren bis hin zu Smartphones - großartig aussehen und gut funktionieren. Der responsive Modus im universellen Editor hilft Ihnen dabei, indem Sie Ihre Formulare während des Erstellungsprozesses über verschiedene Gerätegrößen hinweg in der Vorschau anzeigen und testen können.

Der [universelle Editor](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) ermöglicht es Ihnen, Formulare zu erstellen, die sich automatisch an verschiedene Bildschirmgrößen anpassen und ein optimales Benutzererlebnis unabhängig vom verwendeten Gerät bieten.

## Anzeigen einer Vorschau von Formularen im responsiven Modus für unterschiedliche Geräte

Der universelle Editor bietet ein **Emulator**-Symbol oben rechts im Bildschirm, mit dem Sie Seiten über verschiedene Gerätegrößen hinweg in der Vorschau anzeigen und das Verhalten Ihres responsiven Designs testen können, um ein besseres Benutzererlebnis zu erzielen.

So zeigen Sie eine Vorschau eines Formulars im responsiven Modus an:

1. Öffnen Sie das Formular im universellen Editor zur Bearbeitung.
2. Klicken Sie auf das ![Emulator-Symbol mit einem Gerätevorschau](/help/edge/docs/forms/universal-editor/assets/emulator.png){height=2%,width=2%}-Symbol in der Symbolleiste.
3. Geräteformat auswählen:
   - Desktop (Standard)
   - Tablet
   - Mobilgerät
   - Benutzerdefiniert (Breite und Höhe angeben)

![Screenshot des universellen Editors mit Optionen für den responsiven Modus für verschiedene Geräte](/help/edge/docs/forms/universal-editor/assets/universal-editor-emulator.png)

Sie können auch das Symbol **Screen Rotator** verwenden, um bei der Vorschau auf Tablet- oder Mobilgeräten zwischen Hoch- und Querformat umzuschalten.

Der universelle Editor bietet verschiedene Emulatoren zum Anzeigen einer Vorschau von Formularen auf unterschiedlichen Geräten. In der folgenden Tabelle sind die verfügbaren Emulatortypen zusammen mit den entsprechenden Gerätedarstellungen aufgeführt:

<table border="1" style="text-align:" left; border-collapse: collapse;">
    <tr>
        <th style="width: 20%">Emulatortyp</th>
        <th style="width: 80%">Gerätebild</th>
    </tr>
    <tr>
        <td style="width: 20%">Desktop</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-desktop.png" alt="Desktop-Ansicht eines Formulars mit Layout in voller Breite" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Tablet</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-tab.png" alt="Tabellenansicht eines Formulars mit einem Layout mit mittlerer Breite mit angepassten Komponenten" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Mobilgerät</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-mobile.png" alt="Mobilgeräteansicht eines Formulars mit schmalem Layout mit gestapelten Komponenten" style="width: auto; height: auto"></td>
    </tr>
    <tr>
        <td style="width: 20%">Benutzerdefiniertes Gerät</td>
        <td style="width: 80%"><img src="/help/edge/docs/forms/universal-editor/assets/universal-editor-custom.png" alt="Benutzerdefinierte Geräteansicht eines Formulars mit benutzerdefinierten Abmessungen" style="width: auto; height: auto"></td>
    </tr>
</table>

## Layout-Funktionen

Mit dem universellen Editor können Sie benutzerfreundliche Formulare erstellen, die Endbenutzern dynamische Erlebnisse bieten. Das Formular-Layout steuert, wie Elemente oder Komponenten in einem Formular angezeigt werden.

Der universelle Editor unterstützt die folgenden Arten von Layouts für Formulare:

- [Bereichslayout](#panel-layout)
- [Assistenten-Layout](#wizard-layout)
- [Akkordeon-Layout](#accordion-layout)

### Bedienfeldlayout

Das Bereichslayout ist nützlich, um verwandte Felder so zu organisieren, dass die Navigation und das Auffinden entsprechender Inhalte erleichtert werden. Das Bereichslayout ordnet Formularkomponenten in separaten Abschnitten oder Bereichen in Formularen an.

![Bereichslayout mit mehreren unterschiedlichen Abschnitten innerhalb eines Formulars](/help/edge/docs/forms/universal-editor/assets/panel-layout.png)

**Beispiel** Ein Bewerbungsformular kann Bedienfelder verwenden, um „Persönliche Informationen“, „Bildung“, „Berufserfahrung“ und „Verweise“ in verschiedene Abschnitte zu unterteilen.

**Responsives Verhalten:** Auf kleineren Bildschirmen werden Bedienfelder normalerweise vertikal gestapelt, wobei ihre unterschiedlichen Gruppierungen beibehalten und gleichzeitig die schmalere Breite angepasst wird.

Sie können die [Bedienfeld-Komponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) verwenden, um das Bedienfeld-Layout einem Formular hinzuzufügen. Detaillierte Anweisungen zum Konfigurieren verschiedener Eigenschaften der Bedienfeldkomponente finden Sie im Artikel [Bedienfeldkomponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) .

### Assistenten-Layout

Das Assistenten-Layout vereinfacht ein komplexes Formular, indem es in verschiedene Schritte unterteilt wird. Jeder Schritt stellt einen anderen Teil des Prozesses dar, und Benutzende navigieren nacheinander durch die Schritte, häufig mit den Schaltflächen **Weiter** und **Zurück**. Sie können das Assistenten-Layout verwenden, um ein Formular zu erstellen, das mehrere Abschnitte oder Schritte umfasst.

![Assistentenlayout mit einem mehrstufigen Formular mit Navigationssteuerelementen](/help/edge/docs/forms/universal-editor/assets/wizard-layout.png)

**Beispiel** Ein Versicherungsantragsformular kann einen Assistenten verwenden, der Benutzer durch die Bereitstellung von Details zu Vorfällen, das Hochladen von Beweismitteln, die Eingabe persönlicher Informationen und die Überprüfung der Übermittlung führt.

**Responsives Verhalten:** Auf Mobilgeräten behält der Assistent seinen Schritt-für-Schritt-Ansatz bei, passt den Inhalt jedoch in jedem Schritt an den schmaleren Bildschirm an und stapelt häufig Elemente, die auf größeren Bildschirmen nebeneinander angezeigt würden.

Sie können die Komponente [Assistent](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) verwenden, um das Assistenten-Layout einem Formular hinzuzufügen. Detaillierte Anweisungen zum Konfigurieren der verschiedenen Eigenschaften der Assistenten-Komponente finden Sie im Artikel [Assistenten-Komponente](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) .

### Akkordeon-Layout

Das Akkordeon-Layout zeigt Inhalte in ausblendbaren Abschnitten oder Bereichen in einem adaptiven Formular an. Wenn ein Abschnitt erweitert wird, wird der Inhalt darin angezeigt, während andere Abschnitte reduziert bleiben. Dieses Layout ist ideal für die Anzeige großer Informationsmengen in kompakter Form.

![Akkordeon-Layout mit erweiterbaren Abschnitten in einem Formular](/help/edge/docs/forms/universal-editor/assets/accordion-layout.png)

**Beispiel** Ein Produktkonfigurationsformular kann Akkordeon-Abschnitte für „Grundlegende Optionen“, „Erweiterte Funktionen“, „Zubehör“ und „Zahlungspläne“ verwenden, sodass sich Benutzende auf einen Aspekt auf einmal konzentrieren können.

**Responsives Verhalten:** Akkordeons eignen sich besonders gut für Mobilgeräte, da sie auf natürliche Weise vertikalen Raum sparen, indem sie nur den erweiterten Inhaltsbereich anzeigen, was sie ideal für kleinere Bildschirme macht.

Sie können die [Akkordeon-Komponente](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) verwenden, um das Akkordeon-Layout in einem Formular hinzuzufügen. Detaillierte Anweisungen zum Konfigurieren der verschiedenen Eigenschaften der Akkordeon-Komponente finden Sie im Artikel [Akkordeon-Komponente](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) .

### Wie wählt man das richtige Layout?

Es ist wichtig, das richtige Layout auszuwählen, um das Benutzererlebnis und die Formularfunktionen zu optimieren. Die Tabelle hilft Ihnen, die verschiedenen verfügbaren Layout-Optionen zu verstehen, und führt Sie bei der Auswahl des am besten geeigneten Layouts basierend auf Ihren spezifischen Anforderungen und Anwendungsfällen:

| Funktion | Bedienfeldlayout | Assistenten-Layout | Akkordeon-Layout |
|----------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
| **Zweck** | Gruppiert verwandte Inhalte in separate Abschnitte | Führt Benutzer durch einen mehrstufigen Prozess oder ein mehrstufiges Formular | Organisiert Inhalte in ausblendbaren Abschnitten |
| **Struktur** | Unterschiedliche Abschnitte | Sequenzielle Schritte/Seiten | Reduzierbare Bereiche/Abschnitte |
| **Navigation** | Klicken Sie auf die Panel-Kopfzeilen, um zu navigieren | - Vorwärts: „Weiter“-Taste<br>- Rückwärts: „Zurück“-Schaltfläche<br>- Optionale Schritte überspringen | Auf Kopfzeilen klicken, um Abschnitte zu erweitern/reduzieren |
| **Benutzererlebnis** | Organisiert große Inhaltsmengen auf überschaubare Weise | Schritt-für-Schritt-Anleitung zur Verringerung der Überlastung | Kompakte Ansicht mit erweiterten/reduzierten Abschnitten |
| **Nutzungsszenario** | Komplexe Formulare mit kategorisierten Abschnitten | Einrichtungsprozesse, komplexe Formulare | Häufig gestellte Fragen, Einstellungsmenüs, detaillierte Inhaltsabschnitte |
| **Am besten für Mobilgeräte** | Mittelgroß - Panels werden vertikal gestapelt | Gut - Fokus bleibt nur auf aktuellen Schritt | Hervorragend - Platz sparend mit ausklappbaren Abschnitten |

## Best Practices für Responsive Forms

Befolgen Sie die folgenden Best Practices, um sicherzustellen, dass Ihre Formulare auf allen Geräten die beste Funktionalität bieten:

1. **Zuerst für Mobilgeräte entwickeln** Beginnen Sie mit der Gestaltung Ihres Formulars für Mobilgeräte und erweitern Sie es dann für größere Bildschirme. Dadurch wird sichergestellt, dass die Kernfunktionalität auch auf kleinsten Bildschirmen funktioniert.

2. **Verwenden geeigneter Feldtypen:** Wählen Sie Feldtypen aus, die auf Touch-Geräten gut funktionieren:
   - Verwenden von Dropdown-Listen anstelle von Optionsfeldern, wenn viele Optionen verfügbar sind
   - Verwenden der Datumsauswahl für die Touch-Eingabe
   - Stellen Sie sicher, dass Tasten und Touch-Targets mindestens 44 Pixel x 44 Pixel groß sind.

3. **Vereinfachung für kleinere Bildschirme:**
   - Anzeigen von weniger Feldern pro Zeile auf Mobilgeräten
   - Erwägen, optionale Felder hinter einer Option „Mehr anzeigen“ auszublenden
   - Aufteilen komplexer Formulare in mehrere Schritte auf Mobilgeräten

4. **Gründlich testen:** Testen Sie Ihre Formulare immer auf tatsächlichen Geräten oder verwenden Sie den Emulatormodus im universellen Editor, um sicherzustellen, dass sie in allen Bildschirmgrößen ordnungsgemäß funktionieren.

5. **Erwägen Sie Ladezeiten:** Optimieren Sie Bildgrößen und minimieren Sie die erforderlichen Ressourcen, insbesondere für mobile Benutzer, die langsamere Verbindungen haben können.

## Fehlerbehebung bei responsivem Forms

| Problem | Mögliche Ursache | Lösung |
|-------|---------------|----------|
| Formular erscheint auf Mobilgeräten abgeschnitten | Feste Breiteneinstellungen für Überlaufprobleme | Verwenden Sie relative Einheiten (%, rem) anstelle von Pixeln und überprüfen Sie auf Überlauf:ausgeblendete Eigenschaften |
| Touch-Elemente, mit denen schwer interagiert werden kann | Touch-Ziele zu klein oder zu nah beieinander | Vergrößern Sie die Taste/den Eingang auf mindestens 44 Pixel x 44 Pixel und fügen Sie mehr Platz zwischen den interaktiven Elementen hinzu |
| Inhaltsüberläufe auf kleinen Bildschirmen | Keine responsiven Regeln für kleinere Darstellungsfelder | Hinzufügen von Medienabfragen oder responsiven Klassen, um das Layout für verschiedene Bildschirmgrößen anzupassen |
| Formular auf Mobilgeräten zu langsam | Große Bilder oder zu viele Skripte | Optimieren Sie Bilder, minimieren Sie JavaScript und erwägen Sie verzögertes Laden für nicht kritische Elemente |
| Unterschiedliches Aussehen zwischen Emulator und echten Geräten | Browser-spezifisches Rendering oder Gerätevarianten | Testen Sie nach Möglichkeit auf tatsächlichen Geräten, nicht nur auf Emulatoren |

## Siehe auch

{#see-more-eds-forms}
