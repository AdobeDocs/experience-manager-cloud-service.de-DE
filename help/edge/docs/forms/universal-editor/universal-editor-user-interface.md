---
title: Navigieren in der Benutzeroberfläche des universellen Editors für AEM Forms
description: Beherrschen Sie die Benutzeroberfläche des universellen Editors zum Erstellen von AEM Forms mit Edge Delivery Services. In diesem umfassenden Handbuch zur Benutzeroberfläche erfahren Sie mehr über die wichtigsten Tools, Verknüpfungen und Workflows zum effizienten Erstellen von Formularen.
keywords: Universeller Editor, AEM Forms, Edge-Bereitstellungs-Services, Handbuch zur Benutzeroberfläche, Formularerstellung, WYSIWYG-Editor, Formular-Builder-Tools, Navigation in der Benutzeroberfläche
feature: Edge Delivery Services
role: User, Developer, Admin
level: Beginner
exl-id: 90321e81-bb55-48b2-b329-4944bf926309
source-git-commit: cfff846e594b39aa38ffbd3ef80cce1a72749245
workflow-type: tm+mt
source-wordcount: '2358'
ht-degree: 4%

---


# Navigieren in der Benutzeroberfläche des universellen Editors für AEM Forms

Der [universelle Editor](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) bietet eine visuelle Benutzeroberfläche zum Erstellen von AEM Forms mit Edge Delivery Services. Dieses Handbuch hilft Ihnen, die Schnittstelle zum effizienten Erstellen von Formularen zu verstehen.

![Übersicht über die Benutzeroberfläche des universellen Editors](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface.png)

## Überblick

Der universelle Editor bietet ein **What You See Is What You Get (WYSIWYG**-Erlebnis, das Benutzern genau anzeigt, wie Ihre Formulare angezeigt werden. Unabhängig davon, ob Sie mit der Erstellung von Formularen noch nicht vertraut sind oder ein erfahrener Entwickler sind, hilft Ihnen dieses Handbuch bei Folgendem:

**Grundlegende Kenntnisse erwerben:**

- Sicheres und effizientes Navigieren in der Benutzeroberfläche
- Verwenden der entsprechenden Tools für allgemeine Aufgaben zum Erstellen von Formularen
- Nutzung von Tastaturbefehlen zur Steigerung der Produktivität
- Fehlerbehebung bei häufigen Schnittstellenproblemen

**Hauptschlüssel-Workflows:**

- Richten Sie Ihren Arbeitsbereich ein, um optimale Produktivität zu erzielen
- Erstellen von Formularen vom Konzept bis zur Veröffentlichung
- Testen und Vorschau von Formularen auf allen Geräten
- Zusammenarbeit mit Team-Mitgliedern bei Formularprojekten

## Schneller Einstieg

**Erstmalige Benutzer:** Beginnen Sie mit [grundlegenden Tools](#essential-tools-for-form-building) um die Kernfunktionen zu lernen, die Sie am häufigsten verwenden werden.

**Erfahrene Benutzer:** Zu [erweiterten Funktionen](#advanced-features-and-integrations) für spezielle Tools und Integrationen wechseln.

**Kurzanleitung:** Verwenden Sie die Abschnitte [Übersicht der Benutzeroberfläche](#interface-overview) und [Tastaturbefehle](#keyboard-shortcuts) für schnelle Suchen.

>[!NOTE]
>
> Neu bei der Formularerstellung? Eine [ Anleitung zur Erstellung von Formularen finden Sie unter ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md) mit Edge Delivery Services für AEM Forms .

## Übersicht über die Benutzeroberfläche

Die Benutzeroberfläche des universellen Editors ist in vier Hauptbereiche unterteilt, von denen jeder für bestimmte Aufgaben entwickelt wurde:

![Schnittstellenlayout des universellen Editors](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface1.png)

| **Bereich** | **Zweck** | **Primäre Verwendung** |
|----------|-------------|----------------|
| **[A: Kopfzeile von Experience Cloud](#experience-cloud-header)** | Navigation und Kontoverwaltung | Wechseln zwischen Adobe-Tools, Zugriff auf die Hilfe, Verwalten von Benachrichtigungen |
| **[B: Symbolleiste des universellen Editors](#universal-editor-toolbar)** | Formular bearbeiten und veröffentlichen | Erstellen, Bearbeiten, Anzeigen einer Vorschau und Veröffentlichen von Formularen |
| **[C: Bedienfeld „Eigenschaften“](#properties-panel)** | Komponentenkonfiguration | Formularfelder konfigurieren, Inhaltsstruktur verwalten und auf erweiterte Funktionen zugreifen |
| **[D: Editor-Arbeitsfläche](#editor-canvas)** | Visuelle Formularerstellung | Komponenten hinzufügen, Layout anordnen, Echtzeitvorschau anzeigen |

**Schnittstellenfluss:** meisten Benutzer arbeiten hauptsächlich in der **Editor-Arbeitsfläche** (D) und im **Eigenschaftenbereich** (C) und verwenden die **Symbolleiste** (B) für Aktionen wie Vorschau und Veröffentlichung.

## Wichtige Tools zum Erstellen von Formularen

Beginnen Sie hier, wenn Sie mit dem universellen Editor noch nicht vertraut sind. Dies sind die wichtigsten Tools, die Sie für die meisten Aufgaben zum Erstellen von Formularen verwenden werden:

### **1. Arbeitsfläche des Editors - Ihre Haupt-Workspace**

Auf **Arbeitsfläche des Editors** erstellen Sie Ihre Formulare visuell. Es zeigt genau an, wie das Formular für Benutzende aussieht.

![Editor-Arbeitsfläche](/help/edge/docs/forms/universal-editor/assets/ue-editor.png)

**Wichtige Aktionen:**

- **Komponenten hinzufügen** durch Klicken auf die Schaltfläche **Hinzufügen** im Bedienfeld „Eigenschaften“
- **Elemente auswählen** indem Sie direkt auf sie auf der Arbeitsfläche klicken
- **Echtzeit-Änderungen anzeigen** während der Konfiguration von Komponenten
- **Testinteraktionen** im Vorschaumodus

### **2. Bedienfeld „Eigenschaften“ - Komponenten konfigurieren**

Im **Bedienfeld Eigenschaften** (auf der rechten Seite) können Sie ausgewählte Komponenten anpassen und Ihre Formularstruktur verwalten.

![Panel „Eigenschaften“](/help/edge/docs/forms/universal-editor/assets/ue-properties-panel.png)

**Grundlegende Funktionen:**

- **Eigenschaftenmodus** (`d`): Konfigurieren der ausgewählten Komponenteneinstellungen
- **Inhaltsstruktur** (`f`) - Navigation in der Formularstruktur
- **Komponenten hinzufügen** (`a`): Einfügen neuer Formularfelder
- **Komponentenaktionen** - Duplizieren oder Löschen ausgewählter Elemente

### **3. Symbolleiste - Grundlagen - Vorschau und Veröffentlichung**

Die **Symbolleiste des universellen Editors** bietet wichtige Aktionen zum Testen und Veröffentlichen Ihrer Formulare.

![Symbolleiste des universellen Editors](/help/edge/docs/forms/universal-editor/assets/ue-toolbar.png)

**Wichtige Tools:**

- **Vorschaumodus** (`p`): Testen Sie das Formular so, wie es den Benutzern angezeigt wird
- **Responsiver Modus** - Überprüfen Sie, wie Ihr Formular auf Mobilgeräten aussieht.
- **Seite öffnen** (`o`) - Formular auf einer neuen Registerkarte anzeigen
- **Veröffentlichen** - Formular für Benutzer live schalten

### **4. Schnellstart-Workflow**

**Für Ihr erstes Formular:**

1. **Erstellen beginnen** - Komponenten mithilfe der Schaltfläche **Hinzufügen** hinzufügen (`a`)
2. **Felder konfigurieren** - Komponenten auswählen und **Eigenschaftenmodus** verwenden (`d`)
3. **Formular testen** - Verwenden Sie **Vorschaumodus** (`p`), um mit Ihrem Formular zu interagieren
4. **Ansicht auf Mobilgerät überprüfen** - Zum **responsiven Modus** wechseln, um Mobilgeräte zu testen
5. **Live schalten** - Klicken Sie auf **Veröffentlichen** wenn Sie bereit sind

**Validierungs-Checkpoints:**

- Können Sie Formularfelder hinzufügen und konfigurieren?
- Funktioniert der Vorschaumodus ordnungsgemäß?
- Sind alle erforderlichen Felder ordnungsgemäß eingerichtet?
- Wird das Formular auf Mobilgeräten gut angezeigt?

## Experience Cloud-Header

Die Kopfzeile von **Experience Cloud** stellt Tools für die Navigation und Kontoverwaltung bereit. Die meisten Formular-Builder verwenden sie gelegentlich, um zwischen Adobe-Tools zu wechseln oder auf die Hilfe zuzugreifen.

![Experience Cloud-Kopfzeile](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager-header.png)

**Schlüsselelemente:**

| **Element** | **Zweck** | **Verwendung** |
|-------------|-------------|----------------|
| **Adobe Experience Cloud** | Zu anderen Adobe-Tools navigieren | Wechseln zwischen Sites, Assets, Forms |
| **Organisation** | Wechseln zwischen Organisationen | Szenarien für den Zugriff auf mehrere Organisationen |
| **Hilfe** | Zugriff auf Dokumentation und Support | Wenn Sie Anleitungen benötigen oder Feedback senden möchten |
| **Benachrichtigungen** | Zugewiesene Aufgaben und Warnhinweise anzeigen | Überprüfen des Workflow-Status |
| **Lösungen** | Schneller Zugriff auf andere Adobe-Lösungen | Wechseln zwischen verschiedenen Adobe-Produkten |
| **Benutzerprofil** | Kontoeinstellungen und Abmeldung | Konto verwalten oder Benutzer wechseln |

**Häufigste Verwendungszwecke:**

- **Hilfe aufrufen** - Klicken Sie auf das Hilfesymbol, um Dokumentation und Support anzuzeigen.
- **Wechseln der**: Verwenden Sie das Dropdown-Menü „Organisation“, wenn Sie Zugriff auf mehrere Organisationen haben

## Symbolleiste des universellen Editors

Die **Symbolleiste des universellen Editors** enthält die Bearbeitungs- und Veröffentlichungstools für Primärformulare. Diese sind nach Häufigkeit der Verwendung und typischem Workflow geordnet.

![Symbolleiste des universellen Editors](/help/edge/docs/forms/universal-editor/assets/ue-toolbar.png)

### **Tägliche Workflow-Tools**

**Diese Tools werden in den meisten Sitzungen zum Erstellen von Formularen verwendet:**

#### **Vorschaumodus** (`p`)

**Zweck:** Testen Sie Ihr Formular genau so, wie es den Benutzern angezeigt wird\
**Verwendung:** Vor der Veröffentlichung, nach dem Vornehmen von Änderungen, um die Formularfunktionalität zu testen

![Vorschaumodus](/help/edge/docs/forms/universal-editor/assets/ue-preview.png)

**Best Practice:** Vorschau nach jeder größeren Änderung, um Probleme frühzeitig zu erkennen.

#### **Responsiver Modus**

**Zweck:** Überprüfen Sie, wie das Formular auf Mobilgeräten angezeigt wird.\
**Verwendung:** Nach dem Erstellen des Formulars, vor der Veröffentlichung

![Responsiver Modus](/help/edge/docs/forms/universal-editor/assets/ue-responsivemode.png)

**Best Practice:** Mobilansicht immer testen - viele Benutzer greifen auf Formulare auf Mobiltelefonen zu.

#### **Seite öffnen** (`o`)

**Zweck** Formular auf einer neuen Registerkarte ohne Editor-Oberfläche anzeigen\
**Verwendung:** Für Vollbildtests, Freigabe für Stakeholder zur Überprüfung

![Seite öffnen](/help/edge/docs/forms/universal-editor/assets/ue-openpage.png)

#### **Veröffentlichen**

**Zweck** Formular live schalten und für Benutzer zugänglich machen\
**Verwendung:** Nach gründlichen Tests im Vorschau- und responsiven Modus

![Veröffentlichen](/help/edge/docs/forms/universal-editor/assets/ue-publish.png)

**Validierungs-Checkliste vor der Veröffentlichung:**

- Im Vorschaumodus getestetes Formular
- Reaktionsfähigkeit auf Mobilgeräten überprüft
- Alle erforderlichen Felder konfiguriert
- Übermittlungsaktionen funktionieren ordnungsgemäß

### **Navigationstools**

#### **Schaltfläche „Startseite“**

**Zweck:** Zurück zur Startseite des universellen Editors\
**Verwendung:** Beginn der Arbeit an einem anderen Formular

![Schaltfläche „Startseite“](/help/edge/docs/forms/universal-editor/assets/ue-home.png)

#### **Speicherortleiste** (`l`)

**Zweck:** Direktes Navigieren zu einem Formular über die URL\
**Verwendung:** Schnelles Wechseln zwischen bestimmten Formularen

![Speicherortleiste](/help/edge/docs/forms/universal-editor/assets/ue-locationbar.png)

### **Erweiterte Konfigurationstools**

**Diese Tools werden für bestimmte Szenarien oder erweiterte Setups verwendet:**

#### **AEM-Formulareigenschaften**

**Zweck:** Konfigurieren von Einstellungen auf Formularebene wie Formulardatenmodell (FDM) und Veröffentlichungsdaten\
**Verwendung:** Einrichten von Datenintegrationen, Planen der Veröffentlichung

![Formulareigenschaften](/help/edge/docs/forms/universal-editor/assets/ue-formproperties.png)

![Assistent für Formulareigenschaften](/help/edge/docs/forms/universal-editor/assets/form-properties-ue.png)

Das Bedienfeld Formulareigenschaften enthält die folgenden Abschnitte:

- **Übermittlung**: Definieren, was geschieht, nachdem ein Benutzer das Formular gesendet hat. Sie können aus mehreren Übermittlungsaktionen wählen, z. B. zum Senden von Daten per E-Mail, zum Senden an SharePoint, zum Verwenden eines Formulardatenmodells oder zur Integration mit Services wie Adobe Experience Platform oder Microsoft Power Automate. Eine vollständige Liste der unterstützten Übermittlungsaktionen finden Sie im Artikel [Übermittlungsaktion](/help/edge/docs/forms/universal-editor/submit-action.md) .

- **Vorbefüllen**: Konfigurieren, wie Formularfelder automatisch ausgefüllt werden, bevor der Benutzer mit dem Formular interagiert. Sie können eine Verbindung zu Datenquellen herstellen, z. B. einem Formulardatenmodell (FDM), oder URL-Parameter verwenden, um Felder vorauszufüllen, wodurch das Benutzererlebnis verbessert und manuelle Eingaben reduziert werden. Weitere Informationen finden Sie im Artikel [Vorbefüllungsdienst](/help/edge/docs/forms/universal-editor/prefill-form.md) .

- **Vielen Dank**: Passen Sie an, was Benutzer nach dem Absenden des Formulars sehen. Sie können eine Bestätigungsnachricht anzeigen oder auf eine andere Webseite umleiten, um einen reibungslosen und professionellen Abschluss zu gewährleisten. Informationen zum Konfigurieren einer Dankesnachricht für Formulare finden Sie im Artikel [Konfigurieren einer Dankesnachricht](/help/edge/docs/forms/universal-editor/configure-thankyou-message.md).

#### **Regeleditor** (früher Zugriff)

**Zweck** Dynamische Verhaltensweisen, Validierungen und bedingte Logik hinzufügen\
**Verwendung:** Erstellen interaktiver Formulare mit komplexer Geschäftslogik

![Regeleditor](/help/edge/docs/forms/universal-editor/assets/ue-ruleeditor.png)

>[!IMPORTANT]
>
> **Early-Access-Funktion** Der Regeleditor erfordert einen speziellen Zugriff. Kontaktieren Sie [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com), um diese Funktion zu aktivieren.
>
> **Weitere Informationen:** Detaillierte Anweisungen finden Sie [Handbuch ](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md) Regeleditor).

#### **Einstellungen „Kopfzeile für die Authentifizierung“**

**Zweck:** Festlegen benutzerdefinierter Authentifizierungs-Header für Entwicklungstests\
**Verwendung:** Lokale Entwicklung mit authentifizierungspflichtigen Formularen

![Authentifizierungs-Header](/help/edge/docs/forms/universal-editor/assets/ue-authenticationheader.png)

#### **Zusätzliche Optionen** (Menü mit Auslassungspunkten)

**Zweck:** Greifen Sie auf weniger gängige Aktionen wie das Rückgängigmachen der Veröffentlichung zu.\
**Verwendung:** Offline-Schaltung von Formularen, Zugriff auf erweiterte Optionen

![Zusätzliche Optionen](/help/edge/docs/forms/universal-editor/assets/ue-ellipsis.png)

## Panel „Eigenschaften“

Das **Eigenschaftenbedienfeld** (auf der rechten Seite) ist Ihr Kontrollzentrum zum Erstellen und Konfigurieren von Formularen. Er ändert sich je nach Auswahl und bietet verschiedene Tools für verschiedene Aufgaben.

![Panel „Eigenschaften“](/help/edge/docs/forms/universal-editor/assets/ue-properties-panel.png)

### **Zentrale Tools zur Formularerstellung**

**Diese Tools sind für die Erstellung und Organisation Ihrer Formulare unverzichtbar:**

#### **Komponenten hinzufügen** (`a`)

**Zweck:** Neue Formularfelder und -elemente einfügen\
**Funktionsweise:** Zeigt verfügbare Komponenten für den ausgewählten Container an

![Komponenten hinzufügen](/help/edge/docs/forms/universal-editor/assets/ue-add.png)

**Allgemeine Komponenten:**

- Texteingabe, E-Mail, Telefonfelder
- Dropdown, Optionsfelder, Kontrollkästchen
- Datei-Upload, Datumsauswahl
- Bedienfelder und Abschnitte für die Organisation

#### **Eigenschaften-Modus** (`d`)

**Zweck:** Konfigurieren von Einstellungen für ausgewählte Komponenten\
**Verwendung:** Nach dem Hinzufügen einer Komponente, um ihr Verhalten anzupassen

![Modus „Eigenschaften“](/help/edge/docs/forms/universal-editor/assets/ue-properties.png)

**Schlüsseleinstellungen:**

- Feldbezeichnungen und Platzhaltertext
- Validierungsregeln (erforderlich, Format, Länge)
- Standardwerte und Hilfetext
- Regeln für bedingte Sichtbarkeit

#### **Inhaltsstruktur** (`f`)

**Zweck**: Navigieren und Organisieren der Formularstruktur\
**Verwendung:** Komplexe Formulare mit mehreren Abschnitten, Suchen spezifischer Komponenten

![Inhaltsstruktur](/help/edge/docs/forms/universal-editor/assets/ue-contenttree.png)

**Vorteile:**

- Schnellnavigation zu einer beliebigen Komponente
- Visuelle Formularhierarchie
- Einfache Neuanordnung von Elementen

#### **Komponenten-Aktionen**

**Zweck:** Verwalten vorhandener Komponenten\
**Verfügbare Aktionen:**

- **Duplizieren** - Komponenten schnell kopieren ![Duplizieren](/help/edge/docs/forms/universal-editor/assets/ue-duplicate.png)
- **Löschen** - Entfernen von Komponenten (keine Bestätigungsaufforderung) ![Löschen](/help/edge/docs/forms/universal-editor/assets/ue-delete.png)

### **Erweiterte Funktionen und Integrationen**

**Diese Tools ermöglichen ausgefeilte Formularfunktionen:**

+++Datenintegration

#### **Datenquelle**

**Zweck:** Verbinden von Formularen mit Backend-Datensystemen\
**Verwendung:** Forms, die in Datenbanken oder externe Dienste lesen/schreiben müssen

![Datenquelle](/help/edge/docs/forms/universal-editor/assets/ue-datasource.png)

**Funktionen:**

- Konfiguration des Formulardatenmodells (FDM)
- Dynamische Datenpopulation
- Übermittlung an externe Systeme

+++

+++KI-gestützte Tools

#### **Varianten generieren**

**Zweck** Verwenden von KI zum Erstellen verschiedener Versionen von Formularinhalten\
**Verwendung:** Experimentieren mit verschiedenen Texten, Layouts oder Ansätzen

    ![Varianten generieren](/help/edge/docs/forms/universal-editor/assets/ue-variations.png)

**Weitere Informationen:** [Handbuch zur Generierung von Varianten](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/generative-ai/generate-variations)

#### **Inhaltsentwürfe**

**Zweck:** Erstellen und Speichern von vorläufigen Textversionen\
**Verwendung:** Iterieren beim Kopieren von Formularen, Speichern von Optionen für alternativen Text

![Inhaltsentwürfe](/help/edge/docs/forms/universal-editor/assets/ue-contentdraft.png)

+++

+++Tests und Optimierung

#### **A/B-Tests**

**Zweck:** Vergleichen von Formularvarianten zur Leistungsoptimierung\
**Verwendung:** Konversionsraten optimieren, verschiedene Designs testen

![A/B-Tests](/help/edge/docs/forms/universal-editor/assets/ue-abtesting.png)

#### **Experimente**

**Zweck** Durchführen gesteuerter Tests für Formularentwürfe\
**Verwendung:** Datengesteuerte Formularoptimierung, Benutzererlebnistests

    ![Experimentieren](/help/edge/docs/forms/universal-editor/assets/ue-experimentation.png)

+++

+++Collaboration-Tools

#### **Aufgaben-Management**

**Zweck:** Team-Workflow für Formularprojekte organisieren\
**Verwendung:** Entwicklung von Mehrpersonenformularen, Projekt-Tracking

![Aufgaben-Management](/help/edge/docs/forms/universal-editor/assets/ue-taskmanagement.png)

#### **Personalisierung**

**Zweck:** Verbinden mit Adobe Experience Platform für maßgeschneiderte Erlebnisse\
**Verwendung:** Erstellen personalisierter Formulare auf der Grundlage von Benutzerdaten

    ![Personalization](/help/edge/docs/forms/universal-editor/assets/ue-personalizaton.png)

+++

## Arbeitsfläche des Editors

Die **Editor-Arbeitsfläche** ist Ihr Hauptarbeitsbereich, in dem Sie Formulare visuell erstellen. Es zeigt genau an, wie das Formular für Benutzer aussieht, und bietet Echtzeit-Feedback, wenn Sie Änderungen vornehmen.

![Editor-Arbeitsfläche](/help/edge/docs/forms/universal-editor/assets/ue-editor.png)

**Wichtigste Funktionen:**

- **WYSIWYG-Bearbeitung** - Änderungen sofort bei der Vornahme anzeigen
- **Direkte Interaktion** - Klicken Sie auf eine beliebige Komponente, um sie auszuwählen und zu bearbeiten
- **Echtzeitvorschau** - Wechseln Sie in den Vorschaumodus, um die Funktionalität zu testen
- **Responsive Anzeige** - Schalten Sie Geräteansichten um, um die Kompatibilität von Mobilgeräten zu überprüfen.

**Best Practices:**

- **Mit Struktur beginnen** - Hauptabschnitte vor den detaillierten Komponenten hinzufügen
- **Häufig testen** - Verwenden Sie den Vorschaumodus regelmäßig, um Probleme frühzeitig zu erkennen
- **Think mobile-first** - Überprüfen des responsiven Modus während des gesamten Design-Prozesses

## Tastaturbefehle

Beherrschen Sie diese Tastaturbefehle, um Formulare schneller und effizienter zu erstellen:

| **Tastaturbefehl** | **Aktion** | **Verwendung** |
|--------------|------------|----------------|
| `a` | Komponentenliste öffnen | Hinzufügen neuer Formularfelder |
| `d` | Öffnen der Komponenteneigenschaften | Ausgewählte Elemente konfigurieren |
| `f` | Inhaltsstruktur umschalten | Navigieren in komplexen Formularen |
| `p` | Vorschaumodus umschalten | Formularfunktionen testen |
| `o` | Formular in neuer Registerkarte öffnen | Vollbildprüfung |
| `l` | Fokus-Speicherortleiste | Wechseln zu verschiedenen Formularen |

**Profi-Tipp** Verwenden Sie diese Tastaturbefehle kombiniert - wählen Sie beispielsweise eine Komponente aus, drücken Sie die `d`-Taste zur Konfiguration und `p` Sie dann die Änderungen testen.

## Allgemeine Workflows

### **Erstellen des ersten Formulars**

1. **Struktur hinzufügen** - Verwenden Sie `a`, um ein Bedienfeld für Formularabschnitte hinzuzufügen.
2. **Felder hinzufügen** - Texteingabe, E-Mail und andere Komponenten einfügen
3. **Eigenschaften konfigurieren** - Wählen Sie jedes Feld aus und drücken Sie `d`, um Bezeichnungen und Validierungen festzulegen
4. **Testfunktion**: Drücken Sie die `p`, um das Formular in der Vorschau anzuzeigen und zu testen.
5. **Mobile Ansicht überprüfen** - Verwenden Sie den responsiven Modus, um die mobile Anzeige zu überprüfen.
6. **Veröffentlichen** - Klicken Sie auf Veröffentlichen , wenn Sie bereit für die Live-Schaltung sind.

### **Bearbeiten vorhandener Forms**

1. **Navigationsstruktur** - Verwenden Sie die Inhaltsstruktur (`f`), um Komponenten schnell zu finden
2. **Auswählen und ändern** - Direkt auf Komponenten klicken oder Inhaltsstruktur verwenden
3. **Teständerungen** - Vorschau (`p`) nach jeder wesentlichen Änderung
4. **Workflow validieren** - Testen des gesamten Formularflusses vor der erneuten Veröffentlichung

### **Zusammenarbeit mit Teams**

1. **Aufgabenverwaltung verwenden** - Team-Mitgliedern bestimmte Formularabschnitte zuweisen
2. **Für Überprüfung freigeben** - Verwenden Sie „Seite öffnen“ (`o`), um saubere Vorschauen freizugeben
3. **Gemeinsam testen** - Verwenden des Vorschaumodus für gemeinsame Testsitzungen
4. **Fortschritt verfolgen** - Benachrichtigungen auf Aufgabenaktualisierungen überprüfen

## Beheben häufiger Probleme

### **Schnittstellenprobleme**

+++Schnittstellenelemente werden nicht geladen

**Problem** Schaltflächen der Symbolleiste, das Bedienfeld „Eigenschaften“ oder andere Elemente der Benutzeroberfläche werden nicht angezeigt

**Lösungen:**

- **Seite aktualisieren** - Eine einfache Browser-Aktualisierung behebt häufig Ladeprobleme
- **Browser-Kompatibilität überprüfen** - Verwenden von Chrome, Firefox oder Safari
- **Browsercache löschen** - Entfernt zwischengespeicherte Dateien, die möglicherweise veraltet sind
- **Berechtigungen überprüfen** - Stellen Sie sicher, dass Sie angemessenen Zugriff haben, um Formulare zu bearbeiten

+++

+++Komponenten reagieren nicht

**Problem:** Komponenten können nicht ausgewählt werden oder das Bedienfeld „Eigenschaften“ wird nicht aktualisiert

**Lösungen:**

- **Direkt auf Komponenten klicken** - Vermeiden Sie es, auf leere Bereiche zu klicken
- **Inhaltsstruktur verwenden** - Drücken Sie die `f` und wählen Sie Komponenten aus der Baumstruktur aus.
- **Auf überlappende Elemente prüfen** - Einige Komponenten blockieren möglicherweise andere.
- **Formular neu laden** - Verwenden Sie die Adressleiste (`l`), um das aktuelle Formular neu zu laden

+++

+++Probleme mit dem Vorschaumodus

**Problem** Der Vorschaumodus funktioniert nicht ordnungsgemäß oder zeigt Fehler an

**Lösungen:**

- **Formularvalidierung überprüfen** - Sicherstellen, dass alle erforderlichen Felder ordnungsgemäß konfiguriert sind
- **Zuerst im Bearbeitungsmodus testen** - Überprüfen, ob die Komponenten vor der Vorschau funktionieren
- **Browser-Cache löschen** - Zwischengespeicherte Skripte können die Vorschau beeinträchtigen
- **Komponentenkonfiguration überprüfen** - Einstellungen für den Eigenschaftenmodus auf Fehler überprüfen

+++

## Best Practices für die effiziente Formularerstellung

### **Tipps für die Organisation**

- **Beschreibende Namen verwenden** - Komponenten im Eigenschaftenmodus klar beschriften
- **Gruppieren verwandter Felder** - Verwenden Sie Bedienfelder, um Formularabschnitte logisch zu organisieren
- **Planen vor dem Erstellen** - skizzieren Sie die Formularstruktur, bevor Sie beginnen.
- **Einfach halten** - Vermeiden Sie es, Benutzer mit zu vielen Feldern zu überfordern

### **Anwendererlebnis**

- **Häufig testen** - Verwenden Sie den Vorschaumodus nach jeder größeren Änderung
- **Wie Benutzer denken** - Das vollständige Ausfüllen des Formulars
- **Klare Beschriftungen bereitstellen** - Machen Sie die Feldzwecke für die Benutzer*innen offensichtlich.
- **Hilfreichen Text hinzufügen** - Verwenden Sie Hilfetext für komplexe Felder.

### **Leistungsoptimierung**

- **Komponenten minimieren** - Nur erforderliche Formularfelder verwenden
- **Optimieren von Bildern** - Komprimieren Sie alle Bilder, die in Formularen verwendet werden
- **Test auf Mobilgerät** - Sicherstellen einer guten Leistung bei langsameren Mobilverbindungen
- **Frühe Validierung** - Richten Sie eine ordnungsgemäße Validierung ein, um Übermittlungsfehler zu vermeiden

## Nächste Schritte

Nachdem Sie sich mit der Benutzeroberfläche des universellen Editors vertraut gemacht haben:

1. **Üben Sie mit einem einfachen Formular** - Beginnen Sie mit einfachen Feldern, um sich vertraut zu machen
2. **Erweiterte Funktionen erkunden** - KI-gestützte Tools und Integrationen ausprobieren, wenn sie bereit sind
3. **Erfahren Sie mehr über das** - Siehe [Erste Schritte](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
4. **Übergeordneter Regeleditor** - Dynamische Verhaltensweisen mit dem [Handbuch zum Regeleditor“ ](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md)

**Denken Sie daran** Der universelle Editor wurde entwickelt, um die Formularerstellung intuitiv zu gestalten. Beginnen Sie mit den Grundlagen und erkunden Sie nach und nach erweiterte Funktionen, wenn Ihre Anforderungen wachsen.
