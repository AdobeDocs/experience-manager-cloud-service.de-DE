---
title: Anpassen des Designs und Stils für Edge Delivery Services für AEM Forms
description: Passen Sie effektiv das Design und den Stil für AEM Forms-Assets an, die über Edge Delivery Services bereitgestellt werden, und sorgen Sie so für ein kohärentes Benutzererlebnis mit Branding.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: ac780399-34fe-457d-aaf4-b675656c024d
source-git-commit: 44a8d5d5fdd2919d6d170638c7b5819c898dcefe
workflow-type: tm+mt
source-wordcount: '2493'
ht-degree: 55%

---

# Anpassen des Erscheinungsbilds Ihrer Formulare

Formularstile in Edge Delivery Services für AEM Forms erfordern ein komplexes Verständnis von benutzerdefinierten CSS-Eigenschaften, blockbasierter Architektur und komponentenspezifischen Zielgruppenbestimmungsstrategien. Im Gegensatz zu herkömmlichen Ansätzen zur Formulargestaltung implementiert der adaptive Forms-Block ein systematisches Design-Token-System, das ein konsistentes Design ermöglicht und gleichzeitig die Leistungs- und Barrierefreiheitsvorteile von Edge Delivery Services beibehält.

Die Architektur des adaptiven Forms-Blocks generiert standardisierte HTML-Strukturen für alle Formularkomponenten und erstellt vorhersehbare Muster für CSS-Targeting und -Anpassung. Diese Konsistenz ermöglicht es Entwicklerinnen und Entwicklern, umfassende Stilsysteme zu implementieren, die über komplexe Formularimplementierungen hinweg skalierbar sind, während die blockbasierten Leistungsoptimierungen beibehalten werden, die Edge Delivery Services außergewöhnlich schnell machen.

In diesem umfassenden Handbuch werden die technischen Grundlagen der Formularformatierung im Edge Delivery Services-Ökosystem behandelt, einschließlich benutzerdefinierten CSS-Eigenschaftensystemen, Strukturmustern für Komponenten-HTML und erweiterten Stiltechniken. Die Dokumentation bietet sowohl theoretisches Verständnis als auch praktische Implementierungsleitfäden für die Erstellung komplexer, markenbezogener Formularerlebnisse.

## Was ihr beherrschen werdet

**Beherrschung benutzerdefinierter CSS-Eigenschaften**: Machen Sie sich mit dem vollständigen Variablensystem vertraut, das das Erscheinungsbild von Formularen steuert, einschließlich Farbschemata, Typografie-Skalierungen, Abstandssystemen und Layout-Parametern. Erfahren Sie, wie Sie diese Eigenschaften überschreiben und erweitern können, um umfassende Markenthemen zu implementieren.

**Verständnis der Komponentenarchitektur**: Vertiefen Sie Ihre Kenntnisse über die HTML-Strukturmuster, die von den einzelnen Formularkomponentententypen verwendet werden, und ermöglichen Sie so präzises CSS-Targeting und -Anpassung, ohne die zugrunde liegenden Funktionen oder Barrierefreiheitsfunktionen zu beeinträchtigen.

**Erweiterte Stiltechniken**: Implementieren Sie anspruchsvolle Stilmuster, einschließlich zustandsbasierter Stile, responsiver Designintegration und leistungsoptimierter Anpassungsstrategien, die die Schnellladeeigenschaften von Edge Delivery Services beibehalten.

**Professionelle Implementierungsstrategien**: Lernen Sie branchenübliche Ansätze zur Formularformatierung kennen, einschließlich Design-Systemintegration, verwaltbarer CSS-Architektur und Fehlerbehebungstechniken für komplexe Stilszenarien.

## Grundlagen zu Formularfeldtypen

Bevor wir uns mit der Formatierung befassen, sollten wir die allgemeinen [Formularfeldtypen](/help/edge/docs/forms/universal-editor/create-custom-component.md#supported-fieldtypes) besprechen, die vom adaptiven Formularbaustein unterstützt werden:

- Eingabefelder: Dazu gehören Texteingaben, E-Mail-Eingaben, Kennworteingaben usw.
- Kontrollkästchengruppen: Dienen zum Auswählen mehrerer Optionen.
- Optionsfeldgruppen: Dienen zum Auswählen einer einzelnen Option aus einer Gruppe.
- Dropdown-Listen: Werden auch als Auswahlfelder bezeichnet und dienen zum Auswählen einer Option aus einer Liste.
- Bedienfelder/Container: Dienen zum Gruppieren zugehöriger Formularelemente.

## Standard-Formatierungsgrundsätze

Das Verstehen [grundlegender CSS-Konzepte](https://www.w3schools.com/css/css_intro.asp) vor der Formatierung bestimmter Formularfelder ist von entscheidender Bedeutung:

- [Auswahlen](https://www.w3schools.com/css/css_selectors.asp): Mit einer CSS-Auswahl können Sie bestimmte HTML-Elemente für die Formatierung auswählen. Sie können die Elementauswahl, Klassenauswahl oder ID-Auswahl verwenden.
- [Eigenschaften](https://www.w3schools.com/css/css_syntax.asp): CSS-Eigenschaften definieren das visuelle Erscheinungsbild von Elementen. Zu den allgemeinen Eigenschaften für die Formatierung von Formularfeldern gehören u. a. Farbe, Hintergrundfarbe, Rahmen, Abstand und Rand.
- [Box-Modell](https://www.w3schools.com/css/css_boxmodel.asp): Das CSS-Box-Modell beschreibt die Struktur von HTML-Elementen als Inhaltsbereich, der von Abstand, Rahmen und Rändern umgeben ist.
- Flexbox/Raster: CSS [Flexbox](https://www.w3schools.com/css/css3_flexbox.asp)- und [Raster-Layouts](https://www.w3schools.com/css/css_grid.asp) sind leistungsstarke Tools zum Erstellen responsiver und flexibler Designs.




## Umfassende Formularformatierung mit benutzerdefinierten CSS-Eigenschaften

Der adaptive Forms-Block verwendet eine ausgefeilte CSS-Architektur, die auf benutzerdefinierten Eigenschaften (CSS-Variablen) basiert und systematisches Design und konsistente Formatierung für alle Formularkomponenten ermöglicht. Das Verständnis dieser Struktur ist für eine effektive Formularanpassung und ein effektives Branding unerlässlich.

### Grundlegendes zur „forms.css“-Architektur

Die Standardformularstile befinden sich im Projekt-Repository unter `/blocks/form/form.css` und folgen einem strukturierten Ansatz, bei dem die Wartbarkeit, Konsistenz und Anpassungsflexibilität Vorrang haben. Die Architektur besteht aus mehreren Hauptkomponenten:

**CSS Custom Properties Foundation**: Das Stilsystem basiert auf benutzerdefinierten CSS-Eigenschaften, die auf `:root` Ebene definiert sind, und bietet ein zentralisiertes Design-System, das an alle Formularkomponenten kaskadiert. Diese Variablen legen Design-Token für Farben, Typografie, Abstände und Layout-Eigenschaften fest.

**Blockbasierte CSS-Struktur**: Edge Delivery Services verwendet eine blockbasierte Architektur, bei der die `.form`-Klasse als primärer Namespace für alle formularbezogenen Stile dient, um eine ordnungsgemäße Isolierung des Bereichs sicherzustellen und CSS-Konflikte mit anderen Seitenkomponenten zu verhindern.

**Komponentenspezifische Formatierung**: Einzelne Formularkomponenten werden mit konsistenten Wrapper-Mustern (`.{Type}-wrapper`) formatiert, die eine vorhersehbare Zielgruppenbestimmung für verschiedene Feldtypen ermöglichen und gleichzeitig die Integrität des gesamten Designsystems wahren.

### Referenz zu benutzerdefinierten CSS-Eigenschaften und Anpassung

Das Formularformatierungssystem enthält über 50 benutzerdefinierte CSS-Eigenschaften, die alle Aspekte des Erscheinungsbilds und Verhaltens eines Formulars steuern. Das Verständnis dieser Eigenschaften ermöglicht eine umfassende Anpassung bei gleichzeitiger Wahrung der Designkonsistenz.

+++ Farb- und Design-Variablen

Das Farbsystem bildet mithilfe sorgfältig organisierter benutzerdefinierter Eigenschaften eine vollständige visuelle Grundlage für Formulare:

```css
:root {
    /* Primary color system */
    --background-color-primary: #fff;
    --label-color: #666;
    --border-color: #818a91;
    --form-error-color: #ff5f3f;
    
    /* Button color system */
    --button-primary-color: #5F8DDA;
    --button-secondary-color: #666;
    --button-primary-hover-color: #035fe6;
    
    /* Form-specific color applications */
    --form-background-color: var(--background-color-primary);
    --form-input-border-color: var(--border-color);
    --form-invalid-border-color: #ff5f3f;
    --form-label-color: var(--label-color);
}
```

**Praktisches Anpassungsbeispiel**: Um ein dunkles Design für Ihre Formulare zu implementieren, überschreiben Sie die Grundfarbvariablen:

```css
:root {
    --background-color-primary: #1a1a1a;
    --label-color: #e0e0e0;
    --border-color: #404040;
    --form-error-color: #ff6b6b;
    --button-primary-color: #4a9eff;
}
```

Diese einzelne Änderung wird auf alle Formularkomponenten angewendet, da das System Variablenverweise anstelle hartcodierter Werte verwendet.

+++

+++ Typografie- und Abstandsvariablen

Typografie- und Abstandsvariablen ermöglichen eine umfassende Steuerung der Textdarstellung und des Layoutabstands:

```css
:root {
    /* Font size system */
    --form-font-size-m: 22px;
    --form-font-size-s: 18px;
    --form-font-size-xs: 16px;
    
    /* Component-specific typography */
    --form-label-font-size: var(--form-font-size-s);
    --form-label-font-weight: 400;
    --form-title-font-weight: 600;
    --form-input-font-size: 1rem;
    
    /* Spacing system */
    --form-field-horz-gap: 40px;
    --form-field-vert-gap: 20px;
    --form-input-padding: 0.75rem 0.6rem;
    --form-padding: 0 10px;
}
```

**Praxisbeispiel für die Anpassung**: So erstellen Sie ein kompakteres Formular-Layout mit kleinerer Typografie:

```css
:root {
    --form-font-size-m: 18px;
    --form-font-size-s: 14px;
    --form-font-size-xs: 12px;
    --form-field-horz-gap: 20px;
    --form-field-vert-gap: 15px;
    --form-input-padding: 0.5rem 0.4rem;
}
```

+++

+++ Layout- und Strukturvariablen

Layout-Variablen steuern die Formularabmessungen, das Rasterverhalten und die Komponentenanordnung:

```css
:root {
    /* Form layout */
    --form-width: 100%;
    --form-columns: 12;
    --form-submit-width: 100%;
    
    /* Card-based components */
    --form-card-border-radius: 4px;
    --form-card-padding: 0.6rem 0.8rem;
    --form-card-shadow: 0 1px 2px rgb(0 0 0 / 3%);
    --form-card-hover-shadow: 0 2px 4px rgb(0 0 0 / 6%);
    
    /* Wizard-specific layout */
    --form-wizard-padding: 0px;
    --form-wizard-padding-bottom: 160px;
    --form-wizard-step-legend-padding: 10px;
}
```

**Beispiel für eine praktische Anpassung**: So erstellen Sie ein kartenförmiges Formular mit verbesserter visueller Tiefe:

```css
:root {
    --form-card-border-radius: 12px;
    --form-card-padding: 1.5rem 2rem;
    --form-card-shadow: 0 4px 12px rgb(0 0 0 / 8%);
    --form-card-hover-shadow: 0 8px 24px rgb(0 0 0 / 12%);
    --form-background-color: #f8f9fa;
}

.form {
    background: var(--form-background-color);
    border-radius: var(--form-card-border-radius);
    box-shadow: var(--form-card-shadow);
    padding: var(--form-card-padding);
    max-width: 600px;
    margin: 2rem auto;
}
```

+++

### CSS-Stilmuster und Best Practices

Der adaptive Forms-Block folgt bestimmten CSS-Mustern, die verwaltbare, leistungsstarke und konsistente Stile für alle Komponenten sicherstellen.

+++ Primäre Stilmuster

**Formular-Container auf Blockebene**: Targeting des primären Formular-Containers für das gesamte Layout und die Hintergrundformatierung:

```css
.form {
    /* Form-wide styles */
    max-width: 800px;
    margin: 0 auto;
    background-color: var(--form-background-color);
    padding: var(--form-padding);
    border-radius: var(--form-card-border-radius);
}
```

**Komponenten-Wrapper-Muster**: Targeting bestimmter Feldtypen mithilfe konsistenter Wrapper-Klassen:

```css
/* Text input fields */
.form .text-wrapper input {
    padding: var(--form-input-padding);
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    font-size: var(--form-input-font-size);
    border-radius: 4px;
    width: 100%;
}

/* Email input fields */
.form .email-wrapper input {
    padding: var(--form-input-padding);
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    font-size: var(--form-input-font-size);
}

/* Button styling */
.form .button-wrapper button {
    background-color: var(--form-button-background-color);
    color: var(--form-button-color);
    padding: var(--form-button-padding);
    border: var(--form-button-border);
    font-size: var(--form-button-font-size);
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.2s ease;
}

.form .button-wrapper button:hover {
    background-color: var(--form-button-background-hover-color);
}
```

+++

+++ Erweiterte Anpassungsmuster

**Feldspezifisches Targeting**: Targeting einzelner Felder nach Namen für eindeutige Stilanforderungen:

```css
/* Style specific fields */
.form .field-email input {
    background-image: url('data:image/svg+xml;...'); /* Email icon */
    background-repeat: no-repeat;
    background-position: right 12px center;
    padding-right: 40px;
}

.form .field-phone input {
    text-align: center;
    letter-spacing: 1px;
    font-family: monospace;
}
```

**Zustandsbasierte Formatierung**: Implementieren des Validierungs- und Interaktionsstatus:

```css
/* Validation states */
.form .field-wrapper[data-valid="false"] input {
    border-color: var(--form-error-color);
    box-shadow: 0 0 0 2px rgba(255, 95, 63, 0.1);
}

.form .field-wrapper[data-valid="true"] input {
    border-color: #28a745;
    box-shadow: 0 0 0 2px rgba(40, 167, 69, 0.1);
}

/* Focus states */
.form .text-wrapper input:focus,
.form .email-wrapper input:focus {
    outline: none;
    border-color: var(--button-primary-color);
    box-shadow: 0 0 0 2px rgba(95, 141, 218, 0.2);
}
```

+++


## Komponentenstruktur

Der adaptive Formularbaustein bietet eine konsistente HTML-Struktur für verschiedene Formularelemente, wodurch Formatierungen und die Verwaltung vereinfacht werden. Sie können die Komponenten mithilfe von CSS für Formatierungszwecke bearbeiten.

+++ Allgemeine Komponenten (außer Dropdown-Listen, Optionsfeldgruppen und Kontrollkästchengruppen):

Alle Formularfelder mit Ausnahme von Dropdown-Listen, Optionsfeldgruppen und Kontrollkästchengruppen haben die folgende HTML-Struktur:

#### HTML-Struktur der allgemeinen Komponenten

```HTML
  <div class="{Type}-wrapper field-{Name}   field-wrapper" data-required={Required}>
     <label for="{FieldId}" class="field-label">First   Name</label>
     <input type="{Type}" placeholder="{Placeholder}"   maxlength="{Max}" id={FieldId}" name="{Name}"   aria-describedby="{FieldId}-description">
     <div class="field-description" aria-live="polite"  id="{FieldId}-description">
      Hint - First name should be minimum 3 characters  and a maximum of 10 characters.
     </div>
  </div>
```

- Klassen: Das div-Element verfügt über mehrere Klassen, die auf bestimmte Elemente und die Formatierung abzielen. Sie benötigen die Klassen `{Type}-wrapper` oder `field-{Name}` zum Entwickeln einer CSS-Auswahl, um ein Formularfeld zu formatieren:
- {Type}: Identifiziert die Komponente nach Feldtyp. Zum Beispiel: text (text-wrapper), number (number-wrapper), date (date-wrapper).
- {Name}: Identifiziert die Komponente anhand des Namens. Der Name des Feldes darf nur alphanumerische Zeichen enthalten. Mehrere aufeinander folgende Gedankenstriche im Namen werden durch einen einzigen Bindestrich ersetzt `(-)`, und die Start- und Endabstände in einem Feldnamen werden entfernt. Zum Beispiel: first-name (field-first-name field-wrapper).
- {FieldId}: Eine eindeutige Kennung für das Feld, die automatisch generiert wird.
- {Required}: Ein boolescher Wert, der angibt, ob das Feld erforderlich ist.
- Titel: Das Element `label` liefert einen beschreibenden Text für das Feld und ordnet ihn dem Eingabeelement mithilfe des `for`-Attributs zu.
- Eingabe: Das `input`-Element definiert den einzugebenden Datentyp. Zum Beispiel : text, number, email.
- Beschreibung (optional): `div` mit der Klasse `field-description` stellt zusätzliche Informationen oder Anweisungen für Benutzende bereit.

**Beispiel einer HTML-Struktur**

```HTML
<div class="text-wrapper field-first-name field-wrapper" data-required="true">
  <label for="firstName" class="field-label">First Name</label>
  <input type="text" placeholder="Enter your first name" maxlength="50" id="firstName" name="firstName" aria-describedby="firstName-description">
  <div class="field-description" aria-live="polite" id="firstName-description">
    Please enter your legal first name.
  </div>
</div>
```

#### CSS-Auswahl für allgemeine Komponenten

```css
/* Primary Pattern: Target field wrapper by type */
.form .{Type}-wrapper {
    /* Container styling for specific field types */
    margin-bottom: 1rem;
    border-radius: 4px;
}

/* Primary Pattern: Target input fields within wrapper */
.form .{Type}-wrapper input {
    /* Input field styling using CSS custom properties */
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    padding: var(--form-input-padding);
    border-radius: 4px;
    width: 100%;
    font-size: var(--form-input-font-size);
}

/* Context-specific: Target element by field name when higher specificity needed */
.form .field-{Name} input {
    /* Field-specific customizations */
    /* Use this pattern for unique styling requirements */
}
```

- `.form .{Type}-wrapper`: Targeting des Feld-Wrapper-Elements basierend auf dem Feldtyp. Beispielsweise ist `.form .text-wrapper` auf alle Textfeld-Container ausgerichtet.
- `.form .{Type}-wrapper input`: Targeting der tatsächlichen Eingabeelemente im Wrapper. Dies ist das empfohlene Muster für die Formatierung von Formulareingaben.
- `.form .field-{Name}`: Targeting von Elementen basierend auf dem spezifischen Feldnamen. Beispielsweise zielt `.form .field-first-name` auf den Feld-Container „Vorname“ ab. Verwenden Sie `.form .field-{Name} input` , um das Eingabeelement gezielt anzusprechen.
- **Vermeiden**: `main .form form .{Type}-wrapper` - Dies führt zu einer unnötigen CSS-Spezifität und ist schwieriger zu pflegen.

**Beispiel einer CSS-Auswahl für allgemeine Komponenten**

```css
/* Primary Pattern: Target all text input fields */
.form .text-wrapper input {
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    padding: var(--form-input-padding);
    border-radius: 4px;
    width: 100%;
    font-size: var(--form-input-font-size);
    background-color: var(--form-input-background-color);
}

/* Context-specific: Target field by name when higher specificity needed */
.form .field-first-name input {
    text-transform: capitalize;
    border-color: var(--button-primary-color);
}

/* Alternative with main context if needed */
main .form .text-wrapper input {
    /* Use only when you need higher specificity */
    color: var(--form-label-color);
}
```

+++

+++ Dropdown-Komponente

Bei Dropdown-Menüs wird das `select`-Element anstelle des `input`-Elements verwendet:

#### HTML-Struktur der Dropdown-Komponente

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
   </div>
</div>
```

**Beispiel einer HTML-Struktur**

```HTML
<div class="drop-down-wrapper field-country field-wrapper" data-required="true">
  <label for="country" class="field-label">Country</label>
  <select id="country" name="country">
    <option value="">Select Country</option>
    <option value="US">United States</option>
    <option value="CA">Canada</option>
  </select>
  <div class="field-description" aria-live="polite" id="country-description">
    Please select your country of residence.
  </div>
</div>
```

#### CSS-Auswahlen für Dropdown-Komponenten

Im folgenden CSS sind einige Beispiele von CSS-Auswahlen für Dropdown-Komponenten aufgeführt.

```css
/* Primary Pattern: Target the dropdown wrapper */
.form .drop-down-wrapper {
    /* Container layout using flexbox */
    display: flex;
    flex-direction: column;
    margin-bottom: var(--form-field-vert-gap);
}

/* Target the select element */
.form .drop-down-wrapper select {
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    padding: var(--form-input-padding);
    border-radius: 4px;
    background-color: var(--form-input-background-color);
    font-size: var(--form-input-font-size);
    color: var(--form-label-color);
}

/* Style the label */
.form .drop-down-wrapper .field-label {
    margin-bottom: 5px;
    font-weight: var(--form-label-font-weight);
    color: var(--form-label-color);
    font-size: var(--form-label-font-size);
}
```

- Auswählen des Wrappers als Ziel: Die erste Auswahl (`.drop-down-wrapper`) wählt das äußere Wrapper-Element als Ziel aus, wodurch sichergestellt wird, dass die Stile auf die gesamte Dropdown-Komponente angewendet werden.
- Flexbox-Layout: Flexbox ordnet Beschriftung, Dropdown-Liste und Beschreibung vertikal für ein sauberes Layout an.
- Beschriftungsformatierung: Die Beschriftung zeichnet sich durch eine fette Schriftstärke und einen leichten Rand aus.
- Formatierung der Dropdown-Liste: Das ausgewählte `select`-Element erhält einen Rahmen, einen Abstand und gerundete Ecken für einen hochwertigen Look.
- Hintergrundfarbe: Für visuelle Harmonie wird eine konsistente Hintergrundfarbe festgelegt.
- Pfeilanpassung: Optionale Stile blenden den standardmäßigen Dropdown-Pfeil aus und erstellen einen benutzerdefinierten Pfeil mit einem Unicode-Zeichen und einer Positionierung.

+++

+++ Optionsfeldgruppen

Ähnlich wie bei Dropdown-Komponenten haben Optionsfeldgruppen ihre eigene HTML- und CSS-Struktur:

#### HTML-Struktur der Optionsfeldgruppe

```HTML
<fieldset class="radio-group-wrapper field-{Name} field-wrapper" id="{FieldId}" name="{Name}" data-required="{Required}">
   <legend for="{FieldId}" class="field-label">....</legend>
   <% for each radio in Group %>
   <div class="radio-wrapper field-{Name}">
      <input type="radio" value="" id="{UniqueId}" data-field-type="radio-group" name="{FieldId}">
      <label for="{UniqueId}" class="field-label">...</label>
   </div>
   <% end for %>
</fieldset>
```

**Beispiel einer HTML-Struktur**

```HTML
<fieldset class="radio-group-wrapper field-color field-wrapper" id="color_preference" name="color_preference" data-required="true">
  <legend for="color_preference" class="field-label">Favorite Color:</legend>
  <% for each radio in Group %>
    <div class="radio-wrapper field-color">
      <input type="radio" value="red" id="color_red" data-field-type="radio-group" name="color_preference">
      <label for="color_red" class="field-label">Red</label>
    </div>
    <div class="radio-wrapper field-color">
      <input type="radio" value="green" id="color_green" data-field-type="radio-group" name="color_preference">
      <label for="color_green" class="field-label">Green</label>
    </div>
    <div class="radio-wrapper field-color">
      <input type="radio" value="blue" id="color_blue" data-field-type="radio-group" name="color_preference">
      <label for="color_blue" class="field-label">Blue</label>
    </div>
  <% end for %>
</fieldset>
```

#### CSS-Auswahlen für Optionsfeldgruppen

- Abzielen auf den Feldsatz

```css
/* Target radio group container */
.form .radio-group-wrapper {
    border: var(--form-input-border-size) solid var(--form-input-border-color);
    padding: var(--form-input-padding);
    border-radius: 4px;
    margin-bottom: var(--form-field-vert-gap);
}
```

Dieser Selektor wählt alle Feldsätze mit dem Klassen-Optionsfeldgruppen-Wrapper aus.  Dies wäre nützlich, um allgemeine Stile auf die gesamte Optionsfeldgruppe anzuwenden.

- Targeting von Optionsfeldbezeichnungen

```css
/* Target radio button labels */
.form .radio-wrapper label {
    font-weight: var(--form-label-font-weight);
    margin-right: 10px;
    color: var(--form-label-color);
    font-size: var(--form-label-font-size);
    cursor: pointer;
}
```

- Targeting aller Optionsfeldbezeichnungen innerhalb eines bestimmten Feldsatzes basierend auf seinem Namen

```css
/* Target all radio button labels within a specific fieldset based on its name */
.form .field-color .radio-wrapper label {
    /* Field-specific radio label customizations */
    /* Add your custom styles here */
}
```

+++

+++ Kontrollkästchengruppe

#### HTML-Struktur der Kontrollkästchengruppe

```HTML
<fieldset class="checkbox-group-wrapper field-{Name} field-wrapper" id="{FieldId}" name="{Name}" data-required="{Required}">
   <legend for="{FieldId}" class="field-label">....</legend>
   <% for each radio in Group %>
   <div class="checkbox-wrapper field-{Name}">
      <input type="checkbox" value="" id="{UniqueId}" data-field-type="checkbox-group" name="{FieldId}">
      <label for="{UniqueId}" class="field-label">...</label>
   </div>
   <% end for %>
</fieldset>
```

**Beispiel einer HTML-Struktur**

```HTML
<fieldset class="checkbox-group-wrapper field-topping field-wrapper" id="topping_preference" name="topping_preference" data-required="false">
  <legend for="topping_preference" class="field-label">Pizza Toppings:</legend>
  <div class="checkbox-wrapper field-topping">
    <input type="checkbox" value="pepperoni" id="topping_pepperoni" data-field-type="checkbox-group" name="topping_preference">
    <label for="topping_pepperoni" class="field-label">Pepperoni</label>
  </div>
  <div class="checkbox-wrapper field-topping">
    <input type="checkbox" value="mushrooms" id="topping_mushrooms" data-field-type="checkbox-group" name="topping_preference">
    <label for="topping_mushrooms" class="field-label">Mushrooms</label>
  </div>
  <div class="checkbox-wrapper field-topping">
    <input type="checkbox" value="onions" id="topping_onions" data-field-type="checkbox-group" name="topping_preference">
    <label for="topping_onions" class="field-label">Onions</label>
  </div>
</fieldset>
```

#### CSS-Auswahl für Kontrollkästchengruppen

- Auf den äußeren Wrapper abzielen: Diese Auswahl wählt die äußersten Container von Optionsfeld- und Kontrollkästchengruppen als Ziel aus, sodass Sie allgemeine Stile auf die gesamte Gruppenstruktur anwenden können. Dies ist nützlich zum Festlegen von Abstand, Ausrichtung oder anderen Layout-bezogenen Eigenschaften.

```css
/* Primary Pattern: Targets radio group wrappers */
.form .radio-group-wrapper {
    margin-bottom: var(--form-field-vert-gap); /* Adds space between radio groups */
    display: flex;
    flex-direction: column;
    border: var(--form-fieldset-border);
    padding: var(--form-input-padding);
}

/* Primary Pattern: Targets checkbox group wrappers */
.form .checkbox-group-wrapper {
    margin-bottom: var(--form-field-vert-gap); /* Adds space between checkbox groups */
    display: flex;
    flex-direction: column;
    border: var(--form-fieldset-border);
    padding: var(--form-input-padding);
}
```

- Bezeichnungen der Zielgruppe: Diese Auswahl wählt das `.field-label`-Element sowohl in Optionsfeld- als auch in Kontrollkästchengruppen-Wrappern als Ziel aus. Dadurch können Sie die Beschriftungen speziell für diese Gruppen formatieren und sie ggf. auffälliger gestalten.

```css
/* Primary Pattern: Target group labels */
.form .radio-group-wrapper legend,
.form .checkbox-group-wrapper legend {
    font-weight: var(--form-title-font-weight); /* Makes the group label bold */
    margin-bottom: 0.5rem;
    font-size: var(--form-fieldset-legend-font-size);
    color: var(--form-fieldset-legend-color);
    padding: var(--form-fieldset-legend-padding);
    border: var(--form-fieldset-legend-border);
}
```

- Targeting einzelner Eingaben und Beschriftungen: Diese Auswahl bietet eine präzisere Kontrolle über einzelne Optionsfelder, Kontrollkästchen und die zugehörigen Beschriftungen. Sie können diese verwenden, um Größe und Abstand anzupassen oder spezifischere visuelle Stile anzuwenden.

```css
/* Primary Pattern: Styling radio buttons */
.form .radio-group-wrapper input[type="radio"] {
    margin-right: 8px; /* Adds space between the input and its label */
    margin-bottom: 4px;
    cursor: pointer;
}

/* Primary Pattern: Styling radio button labels */
.form .radio-group-wrapper label {
    font-size: var(--form-label-font-size); /* Changes the label font size */
    color: var(--form-label-color);
    font-weight: var(--form-label-font-weight);
    display: flex;
    align-items: center;
    cursor: pointer;
}

/* Primary Pattern: Styling checkboxes */
.form .checkbox-group-wrapper input[type="checkbox"] {
    margin-right: 8px; /* Adds space between the input and its label */
    margin-bottom: 4px;
    cursor: pointer;
}

/* Primary Pattern: Styling checkbox labels */
.form .checkbox-group-wrapper label {
    font-size: var(--form-label-font-size); /* Changes the label font size */
    color: var(--form-label-color);
    font-weight: var(--form-label-font-weight);
    display: flex;
    align-items: center;
    cursor: pointer;
}
```

- Anpassen des Erscheinungsbilds von Optionsfeldern und Kontrollkästchen: Diese Methode blendet die Standardeingabe aus und verwendet die Pseudo-Elemente `:before` und `:after`, um benutzerdefinierte Visualisierungen zu erstellen, die das Erscheinungsbild basierend auf dem Status „aktiviert“ ändern.

```css
/* Hide the default radio button or checkbox */
.form .radio-group-wrapper input[type="radio"],
.form .checkbox-group-wrapper input[type="checkbox"] {
    opacity: 0;
    position: absolute;
    width: 1px;
    height: 1px;
}

/* Create a custom radio button */
.form .radio-group-wrapper input[type="radio"] + label::before {
    content: '';
    display: inline-block;
    width: 16px;
    height: 16px;
    border: 2px solid var(--form-input-border-color);
    border-radius: 50%;
    margin-right: 8px;
    background-color: var(--form-input-background-color);
    transition: all 0.2s ease;
}

.form .radio-group-wrapper input[type="radio"]:checked + label::before {
    background-color: var(--button-primary-color);
    border-color: var(--button-primary-color);
    box-shadow: inset 0 0 0 3px var(--form-input-background-color);
}

/* Create a custom checkbox */
.form .checkbox-group-wrapper input[type="checkbox"] + label::before {
    content: '';
    display: inline-block;
    width: 16px;
    height: 16px;
    border: 2px solid var(--form-input-border-color);
    border-radius: 2px;
    margin-right: 8px;
    background-color: var(--form-input-background-color);
    transition: all 0.2s ease;
}

.form .checkbox-group-wrapper input[type="checkbox"]:checked + label::before {
    background-color: var(--button-primary-color);
    border-color: var(--button-primary-color);
    background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16"><path fill="white" d="M13.854 3.646a.5.5 0 0 1 0 .708l-7 7a.5.5 0 0 1-.708 0l-3.5-3.5a.5.5 0 1 1 .708-.708L6.5 10.293l6.646-6.647a.5.5 0 0 1 .708 0z"/></svg>');
    background-repeat: no-repeat;
    background-position: center;
}
```

+++

+++ Bedienfeld-/Container-Komponenten

#### HTML-Struktur von Bedienfeld-/Container-Komponenten

```HTML
<fieldset class="panel-wrapper field-{PanelName} field-wrapper">
  <legend for="{id}" class="field-label" data-visible="false">bannerComponent</legend>
  <div class="{Type}-wrapper field-{Name} field-wrapper">
    <label for="{FieldId}" class="field-label">First Name</label>
    <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}">
    <div class="field-description" aria-live="polite" id="{FieldId}-description">
      Hint - First name should be minimum 3 characters and a maximum of 10 characters.
    </div>
  </div>
</fieldset>
```

**Beispiel einer HTML-Struktur**

```HTML
<fieldset class="panel-wrapper field-login field-wrapper">
  <legend for="login" class="field-label" data-visible="false">Login Information</legend>
  <div class="text-wrapper field-username field-wrapper">
    <label for="username" class="field-label">Username</label>
    <input type="text" placeholder="Enter your username" maxlength="50" id="username" name="username">
    <div class="field-description" aria-live="polite" id="username-description">
      Please enter your username or email address.
    </div>
  </div>
  <div class="password-wrapper field-password field-wrapper">
    <label for="password" class="field-label">Password</label>
    <input type="password" placeholder="Enter your password" maxlength="20" id="password" name="password">
    <div class="field-description" aria-live="polite" id="password-description">
      Your password must be at least 8 characters long.
    </div>
  </div>
</fieldset>
```

- Das fieldset-Element dient als Bedienfeld-Container mit dem Klassen-Bedienfeld-Wrapper und zusätzlichen Klassen zur Gestaltung basierend auf dem Bedienfeldnamen (Feldanmeldung).
- Das Legendenelement (`<legend>`) dient als Bereichstitel mit dem Text „Login Information“ und der Klassenfeldbeschriftung. Das data-visible=&quot;false&quot;-Attribut kann mit JavaScript verwendet werden, um die Sichtbarkeit des Titels zu steuern.
- In diesem Feldsatz gibt es mehrere.{Type}-Wrapper-Elemente (in diesem Fall „.text-wrapper“ und „.password-wrapper“) für einzelne Formularfelder im Panel.
- Jeder Wrapper enthält eine Bezeichnung, ein Eingabefeld und eine Beschreibung, ähnlich wie bei den vorherigen Beispielen.


#### Beispiel zur CSS-Auswahl für Bedienfeld-/Container-Komponenten

1. Targeting des Bedienfelds:

```CSS
  /- Target the entire panel container */
  main .form form .panel-wrapper {
    /- Add your styles here (e.g., border, padding, background color) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
 }
```

- Die `.panel-wrapper`-Auswahl gestaltet alle Elemente mit dem Klassenbedienfeld-Wrapper, wodurch ein einheitlicher Look für alle Bedienfelder entsteht.

1. Targeting des Bedientitels:

```CSS
  /- Target the legend element (panel title) */
  .panel-wrapper legend {
    /- Add your styles here (e.g., font-weight, font-size) */
    font-weight: bold;
    font-size: 16px;
    padding-bottom: 5px;
    margin-bottom: 10px;
    border-bottom: 1px solid #ddd; /- Optional: create a separation line */
  }
```

- Die `.panel-wrapper legend`-Auswahl gestaltet das legend-Element im Bedienfeld, sodass der Titel optisch hervorgehoben wird.


1. Targeting einzelner Felder im Bedienfeld:

```CSS
/- Target all form field wrappers within a panel */
main .form form .panel-wrapper .{Type}-wrapper {
  /- Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```

- Die Auswahl `.panel-wrapper .{Type}-wrapper` wählt alle Wrapper mit der Klasse `.{Type}-wrapper` innerhalb des Bedienfelds als Ziel aus, sodass Sie den Abstand zwischen Formularfeldern festlegen können.

1. Targeting bestimmter Felder (optional):

```CSS
  /- Target the username field wrapper */
  main .form form .panel-wrapper .text-wrapper.field-username {
    /- Add your styles here (specific to username field) */
  }

  /- Target the password field wrapper */
  main .form form .panel-wrapper .password-wrapper.field-password {
    /- Add your styles here (specific to password field) */
  }
```

- Mit diesen optionalen Auswahlen können Sie bestimmte Feld-Wrapper innerhalb des Bedienfelds als Ziel auswählen, um einen eindeutigen Stil zu ermöglichen, z. B. zur Hervorhebung des Felds „Benutzername“.


+++

+++ Wiederholbares Bedienfeld

#### HTML-Struktur eines wiederholbaren Bedienfelds

```HTML
<fieldset class="panel-wrapper field-{PanelName} field-wrapper">
  <legend for="{id}" class="field-label" data-visible="false">bannerComponent</legend>
  <div class="{Type}-wrapper field-{Name} field-wrapper">
    <label for="{FieldId}" class="field-label">First Name</label>
    <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}">
    <div class="field-description" aria-live="polite" id="{FieldId}-description">
      Hint - First name should be minimum 3 characters and a maximum of 10 characters.
    </div>
</fieldset>
```

**Beispiel einer HTML-Struktur**

```HTML
<fieldset class="panel-wrapper field-contact field-wrapper" data-repeatable="true">
  <legend for="contact-1" class="field-label" data-visible="false">Contact Information</legend>
  <div class="text-wrapper field-name field-wrapper">
    <label for="name-1" class="field-label">Name</label>
    <input type="text" placeholder="Enter your name" maxlength="50" id="name-1" name="contacts[0].name">
    <div class="field-description" aria-live="polite" id="name-1-description">
      Please enter your full name.
    </div>
  </div>
  <div class="email-wrapper field-email field-wrapper">
    <label for="email-1" class="field-label">Email</label>
    <input type="email" placeholder="Enter your email address" maxlength="100" id="email-1" name="contacts[0].email">
    <div class="field-description" aria-live="polite" id="email-1-description">
      Please enter a valid email address.
    </div>
  </div>
</fieldset>

<fieldset class="panel-wrapper field-contact field-wrapper" data-repeatable="true">
  <legend for="contact-2" class="field-label" data-visible="false">Contact Information</legend>
  <div class="text-wrapper field-name field-wrapper">
    <label for="name-2" class="field-label">Name</label>
    <input type="text" placeholder="Enter your name" maxlength="50" id="name-2" name="contacts[1].name">
    <div class="field-description" aria-live="polite" id="name-2-description">
      Please enter your full name.
    </div>
  </div>
  <div class="email-wrapper field-email field-wrapper">
    <label for="email-2" class="field-label">Email</label>
    <input type="email" placeholder="Enter your email address" maxlength="100" id="email-2" name="contacts[1].email">
    <div class="field-description" aria-live="polite" id="email-2-description">
      Please enter a valid email address.
    </div>
  </div>
</fieldset>
```

Jedes Bedienfeld weist dieselbe Struktur wie das Beispiel eines einzelnen Bedienfelds auf, allerdings mit zusätzlichen Attributen:

- data-repeatable=&quot;true&quot;: Dieses Attribut gibt an, dass das Bedienfeld dynamisch mit JavaScript oder einem Framework wiederholt werden kann.

- Eindeutige IDs und Namen: Jedes Element im Bedienfeld verfügt über eine eindeutige ID (z. B. name-1, email-1) und ein eindeutiges name-Attribut, das auf dem Index des Bedienfelds basiert (z. B. nname=&quot;contacts[0].name&quot;). Dies ermöglicht eine korrekte Datenerfassung bei der Übermittlung mehrerer Bedienfelder.


#### CSS-Auswahl für ein wiederholbares Bedienfeld

- Targeting aller wiederholbaren Bedienfelder:

```CSS
  /- Target all panels with the repeatable attribute */
 main .form form .panel-wrapper[data-repeatable="true"] {
    /- Add your styles here (e.g., border, margin) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
  }
```

Die Auswahl gestaltet alle wiederholbaren Bedienfelder und sorgt so für ein einheitliches Look-and-Feel.


- Targeting einzelner Felder in einem Bedienfeld:

```CSS
/- Target all form field wrappers within a repeatable panel */
main .form form .panel-wrapper[data-repeatable="true"] .{Type}-wrapper {
  /- Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```

Diese Auswahl gestaltet alle Feld-Wrapper in einem wiederholbaren Bedienfeld, wobei ein konsistenter Abstand zwischen Feldern beibehalten wird.

- Targeting bestimmter Felder (in einem Bedienfeld):

```CSS
/- Target the name field wrapper within the first panel */
main .form form .panel-wrapper[data-repeatable="true"][data-index="0"] .text-wrapper.field-name {
  /- Add your styles here (specific to first name field) */
}

/- Target all
```


+++


+++ Dateianhang

#### HTML-Struktur für Dateianhänge

```HTML
<div class="file-wrapper field-{FileName} field-wrapper">
  <legend for="{id}" class="field-label" data-visible="false"> File Attachment </legend>
  <div class="file-drag-area">
    <div class="file-dragIcon"></div>
    <div class="file-dragText">Drag and Drop To Upload</div>
    <button class="file-attachButton" type="button">Attach</button>
    <input type="file" accept="audio/*, video/*, image/*, text/*, application/pdf" id="{id}" name="{FileName}" autocomplete="off" multiple="" required="required">
  </div>
  <div class="files-list">
    <div data-index="0" class="file-description">
      <span class="file-description-name">ClaimForm.pdf</span>
      <span class="file-description-size">26 kb</span>
      <button class="file-description-remove" type="button"></button>
    </div>
  </div>
</div>
```

**Beispiel einer HTML-Struktur**


```HTML
<div class="file-wrapper field-claim_form field-wrapper">
  <legend for="claim_form" class="field-label" data-visible="false">File Attachment</legend>
  <div class="file-drag-area">
    <div class="file-dragIcon"></div>
    <div class="file-dragText">Drag and Drop To Upload</div>
    <button class="file-attachButton" type="button">Attach</button>
  </div>
  <input type="file" accept="audio/*, video/*, image/*, text/*, application/pdf" id="claim_form"
         name="claim_form" autocomplete="off" multiple="" required="required" data-max-file-size="2MB">
  <div class="files-list">
    </div>
</div>
```

- Das class-Attribut verwendet den angegebenen Namen für den Dateianhang (claim_form).
- Die id- und name-Attribute des Eingabeelements stimmen mit dem Dateianhangsnamen (claim_form) überein.
- Der Abschnitt „files-list“ ist zunächst leer. Er wird dynamisch mit JavaScript aufgefüllt, wenn Dateien hochgeladen werden.


#### CSS-Auswahl für die Dateianhangskomponente

- Targeting der gesamten Dateianhangskomponente:

```CSS
/- Target the entire file attachment component */
main .form form .file-wrapper {
  /- Add your styles here (e.g., border, padding) */
  border: 1px solid #ccc;
  padding: 15px;
  border-radius: 4px;
  margin-bottom: 20px;
}
```

Diese Auswahl gestaltet die gesamte Dateianhangskomponente, einschließlich Legende, Ziehbereich, Eingabefeld und Liste.

- Targeting bestimmter Elemente:

```CSS
/- Target the drag and drop area */
main .form form .file-wrapper .file-drag-area {
  /- Add your styles here (e.g., background color, border) */
  background-color: #f0f0f0;
  border: 1px dashed #ddd;
  padding: 10px;
  text-align: center;
}

/- Target the file input element */
main .form form .file-wrapper input[type="file"] {
  /- Add your styles here (e.g., hide the default input) */
  display: none;
}

/- Target individual file descriptions within the list (populated dynamically) */
main .form form .file-wrapper .files-list .file-description {
  /- Add your styles here (e.g., margin, display) */
  display: flex;
  justify-content: space-between;
  margin-bottom: 5px;
}

/- Target the file name within the description */
main .form form .file-wrapper .files-list .file-description .file-description-name {
  /- Add your styles here (e.g., font-weight) */
  font-weight: bold;
}
```

Mit diesen Auswahlen können Sie verschiedene Teile der Dateianhangskomponente individuell gestalten. Sie können die Stile entsprechend Ihren Design-Voreinstellungen anpassen.

+++



## Formatieren von Komponenten

Sie können Formularfelder nach dem jeweiligen Typ (`{Type}-wrapper`) oder nach einzelnen Namen (`field-{Name}`) gestalten. Dies ermöglicht eine präzisere Steuerung und Anpassung des Erscheinungsbilds Ihres Formulars.

+++ Formatierung basierend auf Feldtyp

Sie können CSS-Auswahlen verwenden, um bestimmte Feldtypen als Ziel auszuwählen und Stile konsistent anzuwenden.

#### HTML-Struktur

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
   </div>
</div>
```

**Beispiel einer HTML-Struktur**

```HTML
<div class="text-wrapper field-name field-wrapper" data-required="true">
  <label for="name" class="field-label">Name</label>
  <input type="text" placeholder="Enter your name" maxlength="50" id="name" name="name">
</div>

<div class="number-wrapper field-age field-wrapper" data-required="true">
  <label for="age" class="field-label">Age</label>
  <input type="number" placeholder="Enter your age" id="age" name="age">
</div>

<div class="email-wrapper field-email field-wrapper" data-required="true">
  <label for="email" class="field-label">Email Address</label>
  <input type="email" placeholder="Enter your email" id="email" name="email">
</div>
```

- Jedes Feld wird in ein `div`-Element mit mehreren Klassen eingebettet:
   - `{Type}-wrapper`: Identifiziert den Feldtyp. Beispiel: `form-text-wrapper`, `form-number-wrapper`, `form-email-wrapper`.
   - `field-{Name}`: Identifiziert das Feld anhand seines Namens. Beispiel: `form-name`, `form-age`, `form-email`.
   - `field-wrapper`: Eine allgemeine Klasse für alle Feld-Wrapper.
- Das Attribut `data-required` gibt an, ob das Feld erforderlich oder optional ist.
- Jedes Feld verfügt über eine entsprechende Beschriftung, ein Eingabeelement und potenzielle zusätzliche Elemente wie Platzhalter und Beschreibungen.




#### Beispiel einer CSS-Auswahl

```CSS
/- Primary Pattern: Target all text input fields */
.form .text-wrapper input {
  /- Add your styles here */
  width: 100%;
  padding: var(--form-input-padding);
}

/- Primary Pattern: Target all number input fields */
.form .number-wrapper input {
  /- Add your styles here */
  letter-spacing: 2px; /- Example for adding letter spacing to all number fields */
  text-align: center;
}
```

+++

+++ Formatierung basierend auf Feldnamen

Sie können auch einzelne Felder nach Namen als Ziel auswählen, um eindeutige Stile anzuwenden.

#### HTML-Struktur

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id="{FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - Enter the 6 digit number sent to your mobile number.
   </div>
</div>
```

**Beispiel einer HTML-Struktur**

```HTML
<div class="number-wrapper field-otp field-wrapper" data-required="true">
  <label for="otp" class="field-label">OTP</label>
  <input type="number" placeholder="Enter your OTP" maxlength="6" id="otp" name="otp" aria-describedby="otp-description">
  <div class="field-description" aria-live="polite" id="otp-description">
    Hint - Enter the 6 digit number sent to your mobile number.
   </div>
</div>
```


#### Beispiel einer CSS-Auswahl

```CSS
/- Primary Pattern: Target specific field by name */
.form .field-otp input {
   letter-spacing: 2px;
   text-align: center;
   font-family: monospace;
}

/- Context-specific: Use higher specificity when needed */
main .form .field-otp input {
   /- Use only when you need to override other styles */
   font-weight: bold;
}
```

Diese CSS-Datei wählt alle Eingabeelemente als Ziel aus, die sich in einem Element mit der Klasse `field-otp` befinden. Die Formularstruktur von Edge Delivery Services folgt den Konventionen für adaptive Forms-Blöcke, bei denen Container mit feldspezifischen Klassen wie „field-otp“ für Felder mit dem Namen „otp“ markiert sind.


## CSS-Dateistruktur und -implementierung

### **Referenzimplementierung**

Die vollständige Formularstil-Referenz ist im AEM Forms Boilerplate-Repository verfügbar:

```
https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/blocks/form/form.css
```

Diese Datei dient als kanonische Implementierung des benutzerdefinierten CSS-Eigenschaftensystems und bildet die Grundlage für alle Formularstile. Es enthält umfassende Definitionen für alle CSS-Variablen, Komponentenformatierungsmuster und responsive Design-Implementierungen.

+++

+++ Projektintegration

Implementieren Sie in Ihrem Edge Delivery Services-Projekt die Formularformatierung mit diesem strukturierten Ansatz:

```
/blocks/form/form.css          // Core form block styles (copied from boilerplate)
/styles/styles.css             // Global site styles and CSS variable overrides
/styles/lazy-styles.css        // Additional component enhancements
```

+++

+++ Implementierungsstrategie

**CSS Custom Property Overrides**: Überschreiben von Formularvariablen in Ihren globalen Stilen, um markenspezifisches Design zu implementieren:

```css
/* In /styles/styles.css */
:root {
    /* Brand-specific overrides */
    --button-primary-color: #your-brand-color;
    --form-background-color: #your-background;
    --label-color: #your-text-color;
}
```

**Komponentenspezifische Anpassungen**:
Fügen Sie komponentenspezifische Stile hinzu, während Sie das CSS-Variablensystem beibehalten:

```css
/* Enhanced component styling */
.form .text-wrapper input {
    border-radius: var(--form-card-border-radius);
    transition: all 0.2s ease;
}

.form .text-wrapper input:focus {
    transform: translateY(-1px);
    box-shadow: 0 0 0 3px rgba(var(--button-primary-color), 0.1);
}
```

**Responsive Design-Integration**: Verwenden Sie benutzerdefinierte CSS-Eigenschaften in Medienabfragen für ein konsistentes responsives Verhalten:

```css
@media (max-width: 768px) {
    :root {
        --form-input-padding: 0.875rem;
        --form-field-vert-gap: 1rem;
        --form-padding: 1rem;
    }
}
```

+++

### Beispiel für eine vollständige Stilimplementierung

In diesem Abschnitt wird gezeigt, wie Sie mithilfe von benutzerdefinierten CSS-Eigenschaften ein modernes, markenspezifisches Formular erstellen. Die Implementierung ist zur besseren Übersicht und Navigation in übersichtliche Unterabschnitte unterteilt.



+++ &#x200B;1. Variablen des Markendesigns

Definieren Sie die Farbpalette, den Abstand und die Typografie Ihrer Marke mithilfe von benutzerdefinierten CSS-Eigenschaften.

```css
/* Custom brand theme */
:root {
  /* Brand color system */
  --brand-primary: #2563eb;
  --brand-secondary: #64748b;
  --brand-success: #059669;
  --brand-error: #dc2626;
  --brand-background: #f8fafc;
  
  /* Override form variables */
  --background-color-primary: #ffffff;
  --button-primary-color: var(--brand-primary);
  --button-primary-hover-color: #1d4ed8;
  --form-error-color: var(--brand-error);
  --form-background-color: var(--brand-background);
  --label-color: var(--brand-secondary);
  --border-color: #d1d5db;
  
  /* Enhanced spacing */
  --form-input-padding: 1rem;
  --form-field-vert-gap: 1.5rem;
  --form-padding: 2rem;
  
  /* Modern typography */
  --form-font-size-s: 16px;
  --form-label-font-weight: 500;
}
```


+++

+++ &#x200B;2. Formular-Container-Stile

Wenden Sie einen modernen Hintergrund, einen Rahmenradius und einen Schatten auf den Formular-Container an, um ein visuell ansprechendes Layout zu erzielen.


```css
/* Enhanced form container */
.form {
    background: linear-gradient(135deg, #f8fafc 0%, #f1f5f9 100%);
    border-radius: 12px;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.05);
    max-width: 600px;
    margin: 2rem auto;
    overflow: hidden;
}
```




+++

+++ &#x200B;3. Formatierung der Eingabefelder

Formatieren Sie Text-, E-Mail- und Zahleneingabefelder für einen sauberen, modernen Look.


```css
/* Modern input styling */
.form .text-wrapper input,
.form .email-wrapper input,
.form .number-wrapper input {
    background: white;
    border: 2px solid var(--border-color);
    border-radius: 8px;
    padding: var(--form-input-padding);
    font-size: 16px;
    transition: all 0.2s ease;
    width: 100%;
}
```


+++

+++ &#x200B;4. Zusätzliche Anpassung

Sie können die Formularformatierung weiter erweitern, indem Sie nach Bedarf auf bestimmte Felder, Status oder Komponenten abzielen. Erweiterte Muster finden Sie in früheren Abschnitten.

```css
/* Custom brand theme */
:root {
    /* Brand color system */
    --brand-primary: #2563eb;
    --brand-secondary: #64748b;
    --brand-success: #059669;
    --brand-error: #dc2626;
    --brand-background: #f8fafc;
    
    /* Override form variables */
    --background-color-primary: #ffffff;
    --button-primary-color: var(--brand-primary);
    --button-primary-hover-color: #1d4ed8;
    --form-error-color: var(--brand-error);
    --form-background-color: var(--brand-background);
    --label-color: var(--brand-secondary);
    --border-color: #d1d5db;
    
    /* Enhanced spacing */
    --form-input-padding: 1rem;
    --form-field-vert-gap: 1.5rem;
    --form-padding: 2rem;
    
    /* Modern typography */
    --form-font-size-s: 16px;
    --form-label-font-weight: 500;
}

/* Enhanced form container */
.form {
    background: linear-gradient(135deg, #f8fafc 0%, #f1f5f9 100%);
    border-radius: 12px;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.05);
    max-width: 600px;
    margin: 2rem auto;
    overflow: hidden;
}

/* Modern input styling */
.form .text-wrapper input,
.form .email-wrapper input,
.form .number-wrapper input {
    background: white;
    border: 2px solid var(--border-color);
    border-radius: 8px;
    padding: var(--form-input-padding);
    font-size: 16px;
    transition: all 0.2s ease;
    width: 100%;
}

.form .text-wrapper input:focus,
.form .email-wrapper input:focus,
.form .number-wrapper input:focus {
    border-color: var(--brand-primary);
    box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
    transform: translateY(-1px);
}

/* Enhanced button styling */
.form .button-wrapper button[type="submit"] {
    background: linear-gradient(135deg, var(--brand-primary) 0%, #1d4ed8 100%);
    color: white;
    border: none;
    border-radius: 8px;
    padding: 1rem 2rem;
    font-size: 16px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s ease;
    width: 100%;
    box-shadow: 0 4px 12px rgba(37, 99, 235, 0.3);
}

.form .button-wrapper button[type="submit"]:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(37, 99, 235, 0.4);
}
```

Dieser umfassende Ansatz zeigt, wie benutzerdefinierte CSS-Eigenschaften ein anspruchsvolles Design ermöglichen und gleichzeitig die strukturelle Integrität und die Barrierefreiheitsfunktionen des Blocksystems von Adaptive Forms beibehalten.

+++

## Beheben von CSS-Problemen

+++ CSS-Spezifitätsprobleme

```css
/- ❌ Problem: Styles not applying */
.text-wrapper input {
  color: red;
}

/- ✅ Solution: Match or exceed existing specificity */
.form .text-wrapper input {
  color: red;
}

/- ✅ Alternative: Use higher specificity when needed */
main .form .text-wrapper input {
  color: red;
}
```

+++

+++ Probleme mit der Überschreibung von CSS-Variablen

```css
/- ❌ Problem: Variables not working */
.form {
  --form-border-color: blue; /- Local scope only */
}

/- ✅ Solution: Define in root scope */
:root {
  --form-border-color: blue; /- Global scope */
}
```

+++

+++ Häufige Selektorfehler

```css
/- ❌ Incorrect: Assumes direct nesting */
.form form input {
  /- This might miss inputs in wrappers */
}

/- ✅ Correct: Target actual structure */
.form .text-wrapper input {
  /- Targets actual HTML structure */
}

/- ❌ Avoid: Unnecessary specificity */
main .form form .text-wrapper input {
  /- Too specific, harder to override */
}

/- ✅ Preferred: Balanced specificity */
.form .text-wrapper input {
  /- Easier to maintain and override */
}
```

+++

+++ Formularstatus-Formatierung

```css
/- Validation states */
.form .field-wrapper.error input {
  border-color: var(--form-error-color);
}

.form .field-wrapper.success input {
  border-color: var(--form-success-color);
}

/- Loading state */
.form[data-submitting="true"] {
  opacity: 0.7;
  pointer-events: none;
}

/- Disabled state */
.form input:disabled {
  background-color: var(--form-input-disabled-background);
  cursor: not-allowed;
}
```

+++

### **Komponentenspezifische Best Practices**


+++ Schaltflächenstil

```css
/- Primary buttons */
.form .button-wrapper button[type="submit"] {
  background-color: var(--form-focus-color);
  color: white;
  border: none;
  padding: var(--form-input-padding);
  border-radius: var(--form-border-radius);
}

/- Secondary buttons */
.form .button-wrapper button[type="reset"] {
  background-color: transparent;
  color: var(--form-text-color);
  border: 1px solid var(--form-border-color);
}
```

+++

+++ Responsives Formulardesign

```css
/- Mobile-first approach */
.form {
  width: 100%;
  padding: 1rem;
}

/- Tablet and up */
@media (min-width: 768px) {
  .form {
    max-width: var(--form-max-width);
    padding: var(--form-padding);
  }
}
```

+++

## Zusammenfassung der Best Practices

1. **Benutzerdefinierte CSS-Eigenschaften verwenden**: Variablen für ein konsistentes Design nutzen
2. **Blockbasierte Architektur befolgen**: `.form` als primären Blockselektor verwenden
3. **Überspezifität vermeiden**: Verwenden Sie `main .form form` nicht, es sei denn, dies ist notwendig
4. **Target-Wrapper**: Verwenden von `.{Type}-wrapper` für das Komponenten-Targeting
5. **Konsistenz wahren**: Verwenden Sie dieselben Selektormuster im gesamten Projekt
6. **Geräteübergreifend testen**: Stellen Sie sicher, dass Formulare auf Mobilgeräten, Tablets und Desktop einwandfrei funktionieren
7. **Barrierefreiheit überprüfen**: Stellen Sie sicher, dass Stile Bildschirmlesehilfen oder die Tastaturnavigation nicht beeinträchtigen


