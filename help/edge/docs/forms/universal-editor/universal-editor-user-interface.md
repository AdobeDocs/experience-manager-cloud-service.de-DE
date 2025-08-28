---
title: Navigieren in der Benutzeroberfläche des universellen Editors für AEM Forms
description: Beherrschen Sie die Benutzeroberfläche des universellen Editors zum Erstellen von AEM-Formularen mit Edge Delivery Services. In diesem umfassenden Handbuch zur Benutzeroberfläche erfahren Sie mehr über die wichtigsten Tools, Verknüpfungen und Workflows zum effizienten Erstellen von Formularen.
keywords: Universeller Editor, AEM Forms, Edge Delivery Services, Handbuch zur Benutzeroberfläche, Formularerstellung, WYSIWYG-Editor, Formular-Builder-Tools, Navigation in der Benutzeroberfläche
feature: Edge Delivery Services
role: User, Developer, Admin
level: Beginner
exl-id: 90321e81-bb55-48b2-b329-4944bf926309
source-git-commit: 07160248d5b5817d155a118475878ce04a687a32
workflow-type: tm+mt
source-wordcount: '2355'
ht-degree: 97%

---


# Navigieren in der Benutzeroberfläche des universellen Editors für AEM Forms

Der [universelle Editor](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) bietet eine visuelle Oberfläche zum Erstellen von AEM-Formularen mit Edge Delivery Services. Sie bietet ein **What You See Is What You Get-Erlebnis (WYSIWYG**, das Benutzern genau anzeigt, wie Ihre Formulare angezeigt werden.

![Überblick über die Benutzeroberfläche des universellen Editors](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface.png)

Dieses Handbuch hilft Ihnen, die Schnittstelle zum effizienten Erstellen von Formularen zu verstehen. Unabhängig davon, ob Sie mit der Erstellung von Formularen noch nicht vertraut sind oder bereits Entwicklungserfahrung haben, hilft Ihnen dieses Handbuch bei Folgendem:

**Erwerben grundlegender Kenntnisse:**

- Sicheres und effizientes Navigieren in der Benutzeroberfläche
- Verwenden der entsprechenden Tools für allgemeine Aufgaben zum Erstellen von Formularen
- Nutzung von Tastaturbefehlen zur Steigerung der Produktivität
- Fehlerbehebung bei häufigen Problemen mit der Oberfläche

**Beherrschen der zentralen Workflows:**

- Einrichten Ihres Arbeitsbereichs für optimale Produktivität
- Erstellen von Formularen vom Konzept bis zur Veröffentlichung
- Testen und Vorschau von Formularen auf allen Geräten
- Zusammenarbeit mit Team-Mitgliedern bei Formularprojekten



## Für einen schnellen Einstieg

**Erstmalige Benutzende:** Beginnen Sie mit [Grundlegende Tools](#essential-tools-for-form-building), um die Kernfunktionen kennenzulernen, die Sie am häufigsten verwenden werden.

**Erfahrene Benutzende:** Springen Sie zu [Erweiterte Funktionen](#advanced-features-and-integrations), um mehr über spezielle Tools und Integrationen zu erfahren.

**Kurzanleitung:** Verwenden Sie die Abschnitte [Überblick über die Benutzeroberfläche](#interface-overview) und [Tastaturbefehle](#keyboard-shortcuts) für schnelles Suchen.

>[!NOTE]
>
> Ist die Entwicklung von Formularen für Sie neu? Eine schrittweise Anleitung zur Erstellung von Formularen finden Sie unter [Erste Schritte mit Edge Delivery Services für AEM Forms](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md).

## Überblick über die Oberfläche

Die Benutzeroberfläche des universellen Editors ist in vier Hauptbereiche unterteilt, von denen jeder für bestimmte Aufgaben entwickelt wurde:

![Layout der Benutzeroberfläche des universellen Editors](/help/edge/docs/forms/universal-editor/assets/universal-editor-interface1.png)

| **Bereich** | **Zweck** | **Primäre Verwendung** |
|----------|-------------|----------------|
| **[A: Kopfzeile von Experience Cloud](#experience-cloud-header)** | Navigation und Kontoverwaltung | Zwischen Adobe-Tools, Zugriff auf die Hilfe und Verwalten von Benachrichtigungen wechseln |
| **[B: Symbolleiste des universellen Editors](#universal-editor-toolbar)** | Formulare bearbeiten und veröffentlichen | Formulare erstellen, bearbeiten, als Vorschau anzeigen und veröffentlichen |
| **[C: Bedienfeld „Eigenschaften“](#properties-panel)** | Komponenten konfigurieren | Formularfelder konfigurieren, Inhaltsstruktur verwalten und auf erweiterte Funktionen zugreifen |
| **[D: Editor-Arbeitsfläche](#editor-canvas)** | Visuelle Formularerstellung | Komponenten hinzufügen, Layout anordnen, Echtzeitvorschau anzeigen |

**Schnittstellenfluss:** meisten Benutzenden arbeiten hauptsächlich in der **Editor-Arbeitsfläche** (D) und im **Bedienfeld „Eigenschaften“** (C) und verwenden die **Symbolleiste** (B) für Aktionen wie Vorschau und Veröffentlichung.

## Wichtige Tools zum Erstellen von Formularen

Beginnen Sie hier, wenn Sie mit dem universellen Editor noch nicht vertraut sind. Das sind die wichtigsten Tools, die Sie für die meisten Aufgaben beim Erstellen von Formularen verwenden werden:

### **1. Die Arbeitsfläche des Editors – Ihr Hauptarbeitsbereich**

Auf der **Arbeitsfläche des Editors** erstellen Sie Ihre Formulare auf visuelle Weise. Sie stellt genau dar, wie Ihr Formular für Benutzende aussehen wird.

![Arbeitsfläche des Editors](/help/edge/docs/forms/universal-editor/assets/ue-editor.png)

**Wichtige Aktionen:**

- **Fügen Sie Komponenten hinzu**, indem Sie im Bedienfeld „Eigenschaften“ auf die Schaltfläche **Hinzufügen** klicken.
- **Wählen Sie Elemente aus**, indem Sie in der Arbeitsfläche direkt darauf klicken. 
- **Zeigen Sie Echtzeit-Änderungen an**, während Sie Komponenten konfigurieren.
- **Testen Sie Interaktionen** im Vorschaumodus.

### **2. Bedienfeld „Eigenschaften“ – Komponenten konfigurieren**

Im **Bedienfeld „Eigenschaften“** (auf der rechten Seite) können Sie ausgewählte Komponenten anpassen und Ihre Formularstruktur verwalten.

![Bedienfeld „Eigenschaften“](/help/edge/docs/forms/universal-editor/assets/ue-properties-panel.png)

**Grundlegende Funktionen:**

- **Eigenschaftenmodus** (Tastaturbefehl `d`): Konfigurieren von ausgewählten Komponenteneinstellungen
- **Inhaltsstruktur** (Tastaturbefehl `f`): Navigieren in der Formularstruktur
- **Komponenten hinzufügen** (Tastaturbefehl `a`): Einfügen neuer Formularfelder
- **Komponentenaktionen**: Duplizieren oder Löschen ausgewählter Elemente

### **3. Grundlagen der Symbolleiste – Vorschau und Veröffentlichung**

Die **Symbolleiste des universellen Editors** verfügt über wichtige Aktionen zum Testen und Veröffentlichen Ihrer Formulare.

![Symbolleiste des universellen Editors](/help/edge/docs/forms/universal-editor/assets/ue-toolbar.png)

**Die wichtigsten Tools:**

- **Vorschaumodus** (Tastaturbefehl `p`): Testen Sie Ihr Formular so, wie es Benutzenden angezeigt wird.
- **Responsiver Modus**: Überprüfen Sie, wie Ihr Formular auf Mobilgeräten aussieht.
- **Seite öffnen** (Tastaturbefehl `o`): Zeigen Sie das Formular auf einer neuen Registerkarte an.
- **Veröffentlichen**: Schalten Sie Ihr Formular für Benutzende frei.

### **4. Schnellstart-Workflow**

**Für Ihr erstes Formular:**

1. **Mit dem Erstellen beginnen** – Fügen Sie Komponenten mithilfe der Schaltfläche **Hinzufügen** hinzu(`a`).
2. **Felder konfigurieren** – Wählen Sie Komponenten aus und nutzen Sie den **Eigenschaftenmodus** (`d`).
3. **Formular testen** – Nutzen Sie den **Vorschaumodus** (`p`), um mit Ihrem Formular zu interagieren.
4. **Ansicht auf Mobilgeräten überprüfen** – Wechseln Sie in den **responsiven Modus**, um für Mobilgeräte zu testen.
5. **Live schalten** – Klicken Sie auf **Veröffentlichen**, sobald Sie bereit sind.

**Validierungs-Checkpoints:**

- Können Sie Formularfelder hinzufügen und konfigurieren?
- Funktioniert der Vorschaumodus ordnungsgemäß?
- Sind alle erforderlichen Felder ordnungsgemäß eingerichtet?
- Wird das Formular auf Mobilgeräten richtig angezeigt?

## Experience Cloud-Header

Der **Experience Cloud-Header** stellt Tools für Navigation und Account-Management bereit. Die meisten Formular-Builder nutzen sie gelegentlich, um zwischen Adobe-Tools zu wechseln oder auf die Hilfe zuzugreifen.

![Experience Cloud-Header](/help/edge/docs/forms/universal-editor/assets/universal-editor-experience-manager-header.png)

**Schlüsselelemente:**

| **Element** | **Zweck** | **Wann ist er einzusetzen?** |
|-------------|-------------|----------------|
| **Adobe Experience Cloud** | Navigieren zu anderen Adobe-Tools | Wechseln zwischen Sites, Assets, Formularen |
| **Organisation** | Wechseln zwischen Organisationen | Szenarien für den Zugriff auf mehrere Organisationen |
| **Hilfe** | Zugriff auf Dokumentation und Support | Wenn Sie Anleitungen benötigen oder Feedback senden möchten |
| **Benachrichtigungen** | Anzeigen von zugewiesenen Aufgaben und Warnhinweisen | Überprüfen des Workflow-Status |
| **Lösungen** | Schnellzugriff auf andere Adobe-Lösungen | Wechseln zwischen verschiedenen Adobe-Produkten |
| **Benutzerprofil** | Kontoeinstellungen und Abmeldung | Verwalten des Kontos oder Wechseln zwischen Benutzenden |

**Häufigste Verwendungszwecke:**

- **Hilfe aufrufen** – Klicken Sie auf das Hilfesymbol, um Dokumentation und Support zu erhalten.
- **Organisationen wechseln** – Verwenden Sie das Dropdown-Menü „Organisationen“, wenn Sie Zugriff auf mehrere Organisationen haben.

## Symbolleiste des universellen Editors

Die **Symbolleiste des universellen Editors** enthält die wichtigsten Bearbeitungs- und Veröffentlichungs-Tools für Formulare. Diese sind nach Häufigkeit der Verwendung und typischem Workflow angeordnet.

![Symbolleiste des universellen Editors](/help/edge/docs/forms/universal-editor/assets/ue-toolbar.png)

### **Tägliche Workflow-Tools**

**Diese Tools werden in den meisten Sitzungen zum Erstellen von Formularen verwendet:**

#### **Vorschaumodus** (Tastaturbefehl `p`)

**Zweck:** Testen Sie Ihr Formular genau so, wie es Benutzenden angezeigt wird.\
**Verwendung:** Vor der Veröffentlichung, nach dem Vornehmen von Änderungen, um die Formularfunktionalität zu testen.

![Vorschaumodus](/help/edge/docs/forms/universal-editor/assets/ue-preview.png)

**Best Practice:** Vorschau nach jeder größeren Änderung, um Probleme frühzeitig zu erkennen.

#### **Responsiver Modus**

**Zweck:** Überprüfen, wie das Formular auf Mobilgeräten angezeigt wird.\
**Verwendung:** Nach dem Erstellen des Formulars, vor der Veröffentlichung.

![Responsiver Modus](/help/edge/docs/forms/universal-editor/assets/ue-responsivemode.png)

**Best Practice:** Ansicht auf Mobilgeräten immer testen – viele Benutzende greifen über Mobiltelefone auf Formulare zu.

#### **Seite öffnen** (Tastaturbefehl `o`)

**Zweck:** Formular auf einer neuen Registerkarte ohne Editor-Oberfläche anzeigen.\
**Verwendung:** Für Vollbildtests, Freigabe für Stakeholder zur Überprüfung

![Seite öffnen](/help/edge/docs/forms/universal-editor/assets/ue-openpage.png)

#### **Veröffentlichen**

**Zweck** Formular freischalten und für Benutzende zugänglich machen.\
**Verwendung:** Nach gründlichen Tests im Vorschau- und responsiven Modus.

![Veröffentlichen](/help/edge/docs/forms/universal-editor/assets/ue-publish.png)

**Validierungs-Checkliste vor der Veröffentlichung:**

- Im Vorschaumodus getestetes Formular
- Reaktionsfähigkeit auf Mobilgeräten geprüft
- Alle erforderlichen Felder konfiguriert
- Übermittlungsaktionen funktionieren ordnungsgemäß

### **Navigations-Tools**

#### **Schaltfläche „Startseite“**

**Zweck:** Rückkehr zur Startseite des universellen Editors\
**Verwendung:** Beginn der Arbeit an einem anderen Formular.

![Schaltfläche „Startseite“](/help/edge/docs/forms/universal-editor/assets/ue-home.png)

#### **Speicherortleiste** (Tastaturbefehl `l`)

**Zweck:** Direktes Navigieren zu einem beliebigen Formular über die URL.\
**Verwendung:** Schnelles Wechseln zwischen einzelnen Formularen.

![Speicherortleiste](/help/edge/docs/forms/universal-editor/assets/ue-locationbar.png)

### **Erweiterte Konfigurations-Tools**

**Diese Tools werden für bestimmte Szenarien oder erweiterte Setups verwendet:**

#### **AEM-Formulareigenschaften**

**Zweck:** Konfigurieren von Einstellungen auf Formularebene wie Formulardatenmodell (FDM) und Veröffentlichungsdaten.\
**Verwendung:** Einrichten von Datenintegrationen, Planen der Veröffentlichung.

![Formulareigenschaften](/help/edge/docs/forms/universal-editor/assets/ue-formproperties.png)

![Assistent für Formulareigenschaften](/help/edge/docs/forms/universal-editor/assets/form-properties-ue.png)

Das Bedienfeld „Formulareigenschaften“ enthält die folgenden Abschnitte:

- **Übermittlung**: Definieren Sie, was geschieht, nachdem eine Benutzerin bzw. ein Benutzer das Formular gesendet hat. Sie können zwischen verschiedenen Übermittlungsaktionen wählen, z. B. Senden von Daten per E-Mail, Senden an SharePoint, Verwenden eines Formulardatenmodells oder Integration mit Services wie Adobe Experience Platform oder Microsoft Power Automate. Eine vollständige Liste der unterstützten Übermittlungsaktionen finden Sie im Artikel [Übermittlungsaktion](/help/edge/docs/forms/universal-editor/submit-action.md).

- **Vorbefüllen**: Konfigurieren Sie, wie Formularfelder automatisch ausgefüllt werden, bevor die Benutzerin bzw. der Benutzer mit dem Formular interagiert. Sie können eine Verbindung zu Datenquellen herstellen, z. B. zu einem Formulardatenmodell (FDM), oder URL-Parameter verwenden, um Felder im Voraus auszufüllen, wodurch das Anwendererlebnis verbessert und manuelle Eingaben reduziert werden. Weitere Informationen finden Sie im Artikel [Vorbefüllungsdienst](/help/edge/docs/forms/universal-editor/prefill-form.md).

- **Vielen Dank**: Passen Sie an, was Benutzende nach dem Übermitteln des Formulars sehen. Sie können eine Bestätigungsnachricht anzeigen oder auf eine andere Web-Seite umleiten, um einen reibungslosen und professionellen Abschluss zu gewährleisten. Informationen zum Konfigurieren einer Dankesnachricht für Formulare finden Sie im Artikel [Konfigurieren von Dankesnachrichten](/help/edge/docs/forms/universal-editor/configure-thankyou-message.md).

#### **Regeleditor** (frühzeitiger Zugriff)

**Zweck:** Hinzufügen von dynamischen Verhaltensweisen, Validierungen und bedingter Logik.\
**Verwendung:** Erstellen interaktiver Formulare mit komplexer Geschäftslogik.

![Regeleditor](/help/edge/docs/forms/universal-editor/assets/ue-ruleeditor.png)

>[!IMPORTANT]
>
> **Funktion mit frühzeitigem Zugriff:** Der Regeleditor erfordert einen speziellen Zugriff. Kontaktieren Sie [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com), um diese Funktion aktivieren zu lassen.
>
> **Weitere Informationen:** Detaillierte Anweisungen finden Sie im [Handbuch zum Regeleditor](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md).

#### **Einstellungen „Kopfzeile für die Authentifizierung“**

**Zweck:** Festlegen benutzerdefinierter Authentifizierungskopfzeilen für Entwicklungstests.\
**Verwendung:** Lokale Entwicklung mit authentifizierungspflichtigen Formularen.

![Kopfzeilen für die Authentifizierung](/help/edge/docs/forms/universal-editor/assets/ue-authenticationheader.png)

#### **Zusätzliche Optionen** (Menü mit Auslassungspunkten)

**Zweck:** Zugriff auf weniger gängige Aktionen wie das Aufheben einer Veröffentlichung.\
**Verwendung:** Offline-Schaltung von Formularen, Zugriff auf erweiterte Optionen.

![Zusätzliche Optionen](/help/edge/docs/forms/universal-editor/assets/ue-ellipsis.png)

## Bedienfeld „Eigenschaften“

Das **Bedienfeld „Eigenschaften“** (auf der rechten Seite) ist Ihr Kontrollzentrum für das Erstellen und Konfigurieren von Formularen. Es ändert sich je nach Auswahl und bietet verschiedene Tools für verschiedene Aufgaben.

![Bedienfeld „Eigenschaften“](/help/edge/docs/forms/universal-editor/assets/ue-properties-panel.png)

### **Zentrale Tools für die Formularerstellung**

**Diese Tools sind für die Erstellung und Organisation Ihrer Formulare unverzichtbar:**

#### **Hinzufügen von Komponenten** (Tastaturbefehl `a`)

**Zweck:** Einfügen von neuen Formularfeldern und -elementen.\
**Funktionsweise:** Zeigt verfügbare Komponenten für den ausgewählten Container an.

![Hinzufügen von Komponenten](/help/edge/docs/forms/universal-editor/assets/ue-add.png)

**Allgemeine Komponenten:**

- Texteingabe, E-Mail, Telefonfelder
- Dropdown, Optionsfelder, Kontrollkästchen
- Datei-Upload, Datumsauswahl
- Bedienfelder und Abschnitte für Organisation

#### **Eigenschaftenmodus** (Tastaturbefehl `d`)

**Zweck:** Konfigurieren von Einstellungen für ausgewählte Komponenten.\
**Verwendung:** Nach dem Hinzufügen einer beliebigen Komponente, um ihr Verhalten anzupassen.

![Modus „Eigenschaften“](/help/edge/docs/forms/universal-editor/assets/ue-properties.png)

**Schlüsseleinstellungen:**

- Feldbezeichnungen und Platzhaltertext
- Validierungsregeln (erforderlich, Format, Länge)
- Standardwerte und Hilfetext
- Regeln für bedingte Sichtbarkeit

#### **Inhaltsstruktur** (Tastaturbefehl `f`)

**Zweck**: Navigieren und Organisieren der Formularstruktur.\
**Verwendung:** Komplexe Formulare mit mehreren Abschnitten, Auffinden spezifischer Komponenten.

![Inhaltsstruktur](/help/edge/docs/forms/universal-editor/assets/ue-contenttree.png)

**Vorteile:**

- Schnellnavigation zu einer beliebigen Komponente
- Visuelle Formularhierarchie
- Einfache Neuanordnung von Elementen

#### **Komponenten-Aktionen**

**Zweck:** Verwalten vorhandener Komponenten.\
**Verfügbare Aktionen:**

- **Duplizieren** – Schnelles Kopieren von Komponenten ![Duplizieren](/help/edge/docs/forms/universal-editor/assets/ue-duplicate.png)
- **Löschen** – Entfernen von Komponenten (ohne Bestätigungs-Prompt) ![Löschen](/help/edge/docs/forms/universal-editor/assets/ue-delete.png)

### **Erweiterte Funktionen und Integrationen**

**Diese Tools unterstützen ausgefeilte Formularfunktionen:**

+++-Datenintegration

#### **Datenquelle**

**Zweck:** Verbinden von Formularen mit Backend-Datensystemen.\
**Verwendung:** Formulare, die in Datenbanken oder externen Diensten lesen/schreiben müssen.

![Datenquelle](/help/edge/docs/forms/universal-editor/assets/ue-datasource.png)

**Funktionen:**

- Konfiguration des Formulardatenmodells (FDM)
- Dynamische Datenpopulation
- Übermittlung an externe Systeme

+++

+++KI-gestützte Tools

#### **Varianten generieren**

**Zweck** Verwenden von KI zum Erstellen verschiedener Versionen von Formularinhalten.\
**Verwendung:** Experimentieren mit verschiedenen Texten, Layouts oder Ansätzen.

    ![Varianten generieren](/help/edge/docs/forms/universal-editor/assets/ue-variations.png)

**Weitere Informationen:** [Handbuch zum Generieren von Varianten](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/generative-ai/generate-variations)

#### **Inhaltsentwürfe**

**Zweck:** Erstellen und Speichern von vorläufigen Textversionen.\
**Verwendung:** Iterieren beim Kopieren von Formularen, Speichern von Optionen für alternativen Text.

![Inhaltsentwürfe](/help/edge/docs/forms/universal-editor/assets/ue-contentdraft.png)

+++

+++Tests und Optimierung

#### **A/B-Tests**

**Zweck:** Vergleichen von Formularvarianten zur Leistungsoptimierung.\
**Verwendung:** Optimieren von Konversionsraten, Testen verschiedener Designs.

![A/B-Tests](/help/edge/docs/forms/universal-editor/assets/ue-abtesting.png)

#### **Experimente**

**Zweck:** Durchführen kontrollierter Tests für Formularentwürfe.\
**Verwendung:** Datengesteuerte Formularoptimierung, Tests des Anwendererlebnisses.

    ![Experimente](/help/edge/docs/forms/universal-editor/assets/ue-experimentation.png)

+++

+++Collaboration-Tools

#### **Aufgaben-Management**

**Zweck:** Organisation des Team-Workflows für Formularprojekte.\
**Verwendung:** Entwicklung von Formularen durch mehrere Personen, Projektüberwachung.

![Aufgaben-Management](/help/edge/docs/forms/universal-editor/assets/ue-taskmanagement.png)

#### **Personalisierung**

**Zweck:** Verbindung mit Adobe Experience Platform für maßgeschneiderte Erlebnisse.\
**Verwendung:** Erstellen personalisierter Formulare auf der Grundlage von Benutzerdaten.

    ![Personalisierung](/help/edge/docs/forms/universal-editor/assets/ue-personalizaton.png)

+++

## Arbeitsfläche des Editors

Die **Arbeitsfläche des Editors** ist Ihr Hauptarbeitsbereich, in dem Sie Formulare visuell erstellen. Sie stellt genau dar, wie Ihr Formular für Benutzende aussehen wird, und liefert Echtzeit-Feedback, wenn Sie Änderungen vornehmen.

![Arbeitsfläche des Editors](/help/edge/docs/forms/universal-editor/assets/ue-editor.png)

**Wichtigste Funktionen:**

- **WYSIWYG-Bearbeitung** – Zeigen Sie Änderungen sofort beim Vornehmen an.
- **Direkte Interaktion** – Klicken Sie auf eine beliebige Komponente, um sie auszuwählen und zu bearbeiten.
- **Echtzeitvorschau** – Wechseln Sie in den Vorschaumodus, um die Funktionalität zu testen.
- **Responsive Anzeige** – Schalten Sie Geräteansichten um, um die Kompatibilität mit Mobilgeräten zu überprüfen.

**Best Practices:**

- **Mit der Struktur beginnen** – Fügen Sie Hauptabschnitte vor detaillierten Komponenten hinzu.
- **Häufig testen** – Verwenden Sie regelmäßig den Vorschaumodus, um Probleme frühzeitig zu erkennen.
- **Mobilgeräte stets im Blick** – Prüfen Sie den responsiven Modus während des gesamten Gestaltungsprozesses.

## Tastaturbefehle

Merken Sie sich die folgenden Tastaturbefehle, um Formulare schneller und effizienter erstellen zu können:

| **Tastaturbefehl** | **Aktion** | **Wann ist er einzusetzen?** |
|--------------|------------|----------------|
| `a` | Öffnen der Komponentenliste | Hinzufügen neuer Formularfelder |
| `d` | Öffnen der Komponenteneigenschaften | Konfigurieren von ausgewählten Elementen |
| `f` | Umschalten der Inhaltsstruktur | Navigieren in komplexen Formularen |
| `p` | Umschalten in Vorschaumodus | Testen von Formularfunktionen |
| `o` | Öffnen von Formular in neuer Registerkarte | Vollbildtests |
| `l` | Fokussieren auf Speicherortleiste | Wechseln zu verschiedenen Formularen |

**Profi-Tipp** Nutzen Sie die Tastaturbefehle in Kombination: Wählen Sie beispielsweise eine Komponente aus, drücken Sie auf `d` zum Konfigurieren und drücken Sie dann auf `p`, um die Änderungen testen.

## Allgemeine Workflows

### **Erstellen Ihres ersten Formulars**

1. **Struktur hinzufügen** – Verwenden Sie `a`, um ein Bedienfeld für Formularabschnitte hinzuzufügen.
2. **Felder hinzufügen** – Fügen Sie Texteingabe, E-Mail und andere Komponenten ein.
3. **Eigenschaften konfigurieren** – Wählen Sie die einzelnen Felder aus und drücken Sie `d`, um Bezeichnungen und Validierungen festzulegen.
4. **Testfunktion** – Drücken Sie `p`, um das Formular in der Vorschau anzuzeigen und zu testen.
5. **Mobile Ansicht überprüfen** – Verwenden Sie den responsiven Modus, um die mobile Ansicht zu überprüfen.
6. **Veröffentlichen** – Klicken Sie auf „Veröffentlichen“, sobald Sie bereit für die Live-Schaltung sind.

### **Bearbeiten vorhandener Formulare**

1. **Navigationsstruktur** – Verwenden Sie die Inhaltsstruktur (`f`), um Komponenten schnell zu finden.
2. **Auswählen und ändern** – Klicken Sie direkt auf Komponenten oder nutzen Sie die Inhaltsstruktur.
3. **Teständerungen** – Zeigen Sie nach jeder wesentlichen Änderung eine Vorschau (`p`) an.
4. **Workflow validieren** – Testen Sie vor der erneuten Veröffentlichung den gesamten Formularfluss.

### **Zusammenarbeit mit Teams**

1. **Aufgaben-Management verwenden** – Weisen Sie Team-Mitgliedern bestimmte Formularabschnitte zu.
2. **Für Review freigeben** – Verwenden Sie „Seite öffnen“ (`o`), um saubere Vorschauen freizugeben.
3. **Gemeinsam testen** – Verwenden Sie den Vorschaumodus für gemeinsame Testsitzungen.
4. **Fortschritt verfolgen** – Prüfen Sie Benachrichtigungen auf aktualisierte Aufgaben.

## Fehlerbehebung bei gängigen Problemen

### **Schnittstellenprobleme**

+++Schnittstellenelemente werden nicht geladen

**Problem** Schaltflächen der Symbolleiste, das Bedienfeld „Eigenschaften“ oder andere Elemente der Benutzeroberfläche werden nicht angezeigt

**Lösungen:**

- **Seite aktualisieren** – Eine einfache Aktualisierung des Browsers kann Ladeprobleme häufig beheben
- **Kompatibilität des Browsers überprüfen** – Verwenden von Chrome, Firefox oder Safari
- **Browsercache löschen** – Entfernt zwischengespeicherte Dateien, die möglicherweise veraltet sind
- **Berechtigungen überprüfen** – Stellen Sie sicher, dass Sie angemessenen Zugriff für das Bearbeiten von Formularen haben

+++

+++Komponenten reagieren nicht

**Problem:** Komponenten können nicht ausgewählt werden oder das Bedienfeld „Eigenschaften“ wird nicht aktualisiert

**Lösungen:**

- **Direkt auf Komponenten klicken** – Vermeiden Sie es, auf leere Bereiche zu klicken
- **Inhaltsstruktur verwenden** – Drücken Sie `f` und wählen Sie Komponenten aus der Baumstruktur aus
- **Auf überlappende Elemente prüfen** – Einige Komponenten blockieren möglicherweise andere
- **Formular neu laden** – Verwenden Sie die Speicherortleiste (`l`), um das aktuelle Formular neu zu laden

+++

+++Probleme mit dem Vorschaumodus

**Problem** Der Vorschaumodus funktioniert nicht ordnungsgemäß oder zeigt Fehler an

**Lösungen:**

- **Formularvalidierung überprüfen** – Stellen Sie sicher, dass alle erforderlichen Felder ordnungsgemäß konfiguriert sind
- **Zuerst im Bearbeitungsmodus testen** – Überprüfen Sie, ob Komponenten vor der Vorschau funktionieren
- **Browsercache löschen** – Zwischengespeicherte Skripte können die Vorschau beeinträchtigen
- **Komponentenkonfiguration überprüfen** – Prüfen Sie die Einstellungen für den Eigenschaftenmodus auf Fehler

+++

## Best Practices für eine effiziente Formularerstellung

### **Tipps für Unternehmen**

- **Beschreibende Namen verwenden** – Beschriften Sie Komponenten im Eigenschaftenmodus klar
- **Verwandte Felder gruppieren** – Verwenden Sie Bedienfelder, um Formularabschnitte logisch anzuordnen
- **Vor dem Erstellen planen** – Skizzieren Sie die Formularstruktur, bevor Sie beginnen
- **Einfach halten** – Vermeiden Sie es, Benutzende mit zu vielen Feldern zu überfordern

### **Anwendererlebnis**

- **Häufig testen** – Verwenden Sie den Vorschaumodus nach jeder größeren Änderung
- **Wie Benutzende denken** - Denken Sie an das Ausfüllen des vollständigen Formulars
- **Klare Bezeichnungen geben** – Machen Sie den Zweck von Feldern für Benutzende offensichtlich
- **Hilfreichen Text hinzufügen** – Verwenden Sie Hilfetext bei komplexen Feldern

### **Leistungsoptimierung**

- **Komponenten minimieren** – Verwenden Sie nur erforderliche Formularfelder
- **Bilder optimieren** – Komprimieren Sie alle Bilder, die in Formularen verwendet werden
- **Auf Mobilgeräten testen** – Stellen Sie gute Leistung bei langsameren Mobilfunkverbindungen sicher
- **Frühzeitig validieren** – Richten Sie eine angemessene Validierung ein, um Übermittlungsfehler zu verhindern

## Nächste Schritte

Nachdem Sie sich mit der Benutzeroberfläche des universellen Editors vertraut gemacht haben:

1. **Üben Sie mit einem einfachen Formular** – Beginnen Sie mit einfachen Feldern, um sich vertraut zu machen
2. **Erkunden Sie erweiterte Funktionen** – Testen Sie KI-gestützte Tools und Integrationen, sobald Sie bereit sind
3. **Erfahren Sie mehr über das Erstellen von Formularen** – Konsultieren Sie das[Handbuch mit ersten Schritten](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
4. **Erlernen Sie den Regeleditor** – Fügen Sie mit dem [Handbuch zum Regeleditor](/help/edge/docs/forms/universal-editor/rule-editor-universal-editor.md) dynamische Verhaltensweisen hinzu

**Denken Sie daran:** Der universelle Editor wurde entwickelt, um die Formularerstellung intuitiv zu gestalten. Beginnen Sie mit den Grundlagen und erkunden Sie nach und nach erweiterte Funktionen, sobald Ihre Anforderungen steigen.
