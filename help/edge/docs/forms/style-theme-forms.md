---
title: Design und Stil für ein AEM Forms Edge Delivery Service-Formular anpassen
description: Design und Stil für ein AEM Forms Edge Delivery Service-Formular anpassen
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 4a3ebcf7985253ebca24e90ab57ae7eaf3e924e9
workflow-type: tm+mt
source-wordcount: '1285'
ht-degree: 0%

---


# Formularfelder formatieren

Forms ist von entscheidender Bedeutung für die Benutzerinteraktion auf Websites, sodass sie Daten eingeben können. In diesem Handbuch werden die Grundlagen für die Formatierung verschiedener Formularfelder im [Formularblock](/help/edge/docs/forms/create-forms.md), mit dem Sie visuell ansprechende und benutzerfreundliche Formulare erstellen können.

## Grundlagen zu Formularfeldtypen

Bevor wir uns mit der Formatierung befassen, sollten wir die allgemeinen Formularfeldtypen überprüfen, die vom Formularblock unterstützt werden:

* Eingabefelder: Dazu gehören Texteingaben, E-Mail-Eingaben, Kennworteingaben und mehr.
* Kontrollkästchengruppen: Dient zum Auswählen mehrerer Optionen.
* Optionsfeldgruppen: Dient zum Auswählen nur einer Option aus einer Gruppe.
* Dropdowns: Wird auch als Auswahlfelder bezeichnet und dient zum Auswählen einer Option aus einer Liste.
* Bedienfelder/Container: Dient zum Gruppieren verwandter Formularelemente.

## Grundlegende Stilgrundsätze

Grundlegende CSS-Konzepte sind vor der Formatierung bestimmter Formularfelder von entscheidender Bedeutung:

* Selektoren: Mit CSS-Selektoren können Sie bestimmte HTML-Elemente für die Formatierung auswählen. Sie können Elementselektoren, Klassenselektoren oder ID-Selektoren verwenden.
* Eigenschaften: CSS-Eigenschaften definieren das visuelle Erscheinungsbild von Elementen. Zu den gebräuchlichen Eigenschaften für die Formatierung von Formularfeldern gehören Farbe, Hintergrundfarbe, Rahmen, Abstand, Rand und mehr.
* Box Model: Das CSS-Box-Modell beschreibt die Struktur von HTML-Elementen als Inhaltsbereich, der von Abstand, Rahmen und Rändern umgeben ist.
* Flexbox/Grid: CSS Flexbox- und Rasterlayouts sind leistungsstarke Tools zum Erstellen responsiver und flexibler Designs.

## Formatieren eines Formulars für Formularblöcke

Der Formularblock bietet eine standardisierte HTML-Struktur, die die Auswahl und Formatierung von Formularkomponenten vereinfacht:

* **Standardstile aktualisieren**: Sie können die Standardstile eines Formulars ändern, indem Sie `/blocks/form/form.css file`. Diese Datei bietet einen umfassenden Stil für ein Formular, der mehrstufige Assistentenformulare unterstützt. Die Verwendung benutzerdefinierter CSS-Variablen ermöglicht eine einfache Anpassung, Wartung und einheitliche Formatierung in allen Formularen. Anweisungen zum Hinzufügen des Formularblocks zu Ihrem Projekt finden Sie unter [Formular erstellen](/help/edge/docs/forms/create-forms.md).

* **Anpassung**: Verwenden Sie die Standardeinstellung `forms.css` als Basis verwenden und anpassen, um das Erscheinungsbild Ihrer Formularkomponenten zu ändern, sodass es visuell ansprechend und benutzerfreundlich ist. Die Dateistruktur fördert die Organisation und verwaltet Stile für Formulare, wodurch konsistente Designs auf Ihrer Website gefördert werden.

## Aufschlüsselung der Struktur von forms.css

* **Globale Variablen:** Definiert unter `:root` Ebene, diese Variablen (`--variable-name`) speichern Werte, die im gesamten Stylesheet verwendet werden, um die Konsistenz und einfache Aktualisierung zu gewährleisten. Diese Variablen definieren Farben, Schriftgrößen, Abstände und andere Eigenschaften. Sie können Ihre eigenen globalen Variablen deklarieren oder vorhandene ändern, um den Stil des Formulars zu ändern.

* **Universelle Auswahlstile:** Die `*` Auswahl stimmt mit jedem Element im Formular überein, wobei sichergestellt wird, dass Stile standardmäßig auf alle Komponenten angewendet werden, einschließlich der Festlegung der `box-sizing` Eigenschaft auf `border-box`.

* **Formularstile:** Dieser Abschnitt konzentriert sich auf die Formatierung von Formularkomponenten mithilfe von Selektoren für das Targeting bestimmter HTML-Elemente. Sie definiert Stile für Eingabefelder, Textbereiche, Kontrollkästchen, Optionsfelder, Dateieingaben, Formularbeschriftungen und Beschreibungen.

* **Stil des Assistenten (falls zutreffend):** Dieser Abschnitt dient der Formatierung des Assistenten-Layouts, eines aus mehreren Schritten bestehenden Formulars, in dem jeder Schritt einzeln angezeigt wird. Sie definiert Stile für den Assistentencontainer, Feldsätze, Legenden, Navigationsschaltflächen und responsive Layouts.

* **Medienabfragen:** Diese bieten Stile für unterschiedliche Bildschirmgrößen, passen das Layout und die Formatierung entsprechend an.

* **Verschiedene Stile:**: In diesem Abschnitt werden Stile für Erfolgs- oder Fehlermeldungen, Dateiupload-Bereiche und andere Elemente behandelt, auf die Sie in einem Formular stoßen können.


## Komponentenstruktur

Der Formularblock bietet eine konsistente HTML-Struktur für verschiedene Formularelemente, wodurch Stile und Verwaltung vereinfacht werden. Sie können die Komponenten mithilfe von CSS für Stilzwecke bearbeiten.

### Allgemeine Komponenten (außer Dropdown, Optionsfeldgruppen und Kontrollkästchengruppen):

Alle Formularfelder mit Ausnahme von Dropdown-Listen, Optionsfeldgruppen und Kontrollkästchengruppen haben die folgende HTML-Struktur:

#### HTML Stucture

```HTML
<div class="form-{Type}-wrapper form-{Name} field-wrapper" data-required={Required}>
  <label for="{FieldId}" class="field-label">Field Label</label>
  <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id="{FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
  <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - Description of the field.
  </div>
</div>
```

* Klassen: Das div -Element verfügt über mehrere Klassen für das Targeting bestimmter Elemente und für die Formatierung. Sie benötigen die `form-{Type}-wrapper` oder `form-{Name}` Klassen zum Entwickeln eines CSS-Selektors, um ein Formularfeld zu formatieren:
   * {Type}: Identifiziert die Komponente nach Feldtyp. Beispiel: Text (form-text-wrapper), Zahl (form-number-wrapper), Datum (form-date-wrapper).
   * {Name}: Identifiziert die Komponente nach Name. Der Name des Felds darf nur alphanumerische Zeichen enthalten. Die mehreren aufeinander folgenden Gedankenstriche im Namen werden durch einen einzigen Bindestrich ersetzt `(-)`, und die Start- und Endabstände in einem Feldnamen werden entfernt. Beispiel: Vorname (Feld-Wrapper für Formular-Vorname).
   * {FieldId}: Es handelt sich um eine eindeutige Kennung für das Feld, die automatisch generiert wird.
   * {Required}: Ein boolescher Wert, der angibt, ob das Feld erforderlich ist.
* Titel: Die `label` -Element liefert einen beschreibenden Text für das Feld und ordnet ihn dem Eingabeelement mithilfe der `for` -Attribut.
* Eingabe: Die `input` -Element definiert den Datentyp, der eingegeben werden soll. Zum Beispiel Text, Zahl, E-Mail.
* Beschreibung (optional): Die `div` with class `field-description` stellt zusätzliche Informationen oder Anweisungen für den Benutzer bereit.

**Beispiel**

```HTML
<div class="form-text-wrapper form-first-name field-wrapper" data-required="true">
  <label for="firstName" class="field-label">First Name</label>
  <input type="text" placeholder="Enter your first name" maxlength="50" id="firstName" name="firstName" aria-describedby="firstName-description">
  <div class="field-description" aria-live="polite" id="firstName-description">
    Please enter your legal first name.
  </div>
</div>
```

#### CSS-Selektor für allgemeine Komponenten

```CSS
.form-{Type}-wrapper input {
  /* Add your styles here */
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}


.form-{Name} input {
  /* Add your styles here */
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}
```

* `.form-{Type}-wrapper`: Targeting des äußeren `div` -Element basierend auf dem Feldtyp. Beispiel: `.form-text-wrapper` Alle Texteingabefelder werden als Ziel ausgewählt.
* `.form-{Name}`: Wählt das Element weiter auf Grundlage des spezifischen Feldnamens aus. Beispiel: `.form-first-name` gibt das Textfeld &quot;Vorname&quot;als Ziel an.

**Beispiel:**

```CSS
/*Target all text input fields */

.form-text-wrapper input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}

/*Target all fields with name first-name*/

.form-first-name input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}
```


### Dropdown-Komponente

Bei Dropdown-Menüs wird die `select` -Element anstelle von `input` element:


#### HTML Stucture

```HTML
<div class="form-drop-down-wrapper form-{Name} field-wrapper" data-required={required}>
  <label for="{FieldId}" class="field-label">First Name</label>
  <select id="{FieldId}" name="{Name}"><option></option><option></option></select>
  <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
  </div>
</div>
```

**Beispiel**

```HTML
    <div class="form-drop-down-wrapper form-country field-wrapper" data-required="true">
      <label for="country" class="field-label">Country</label>
      <select id="country" name="country">
         <option value="">Select Country</option>
         <option value="US">United States</option>
         <option value="CA">Canada</option>
    </select>
   <div class="field-description" aria-live="polite" id="country-description">Please select your country of residence.</div>
   </div>
```

#### CSS-Selektoren für Dropdown-Komponenten

```CSS
/* Target the outer wrapper */
.form-drop-down-wrapper {
  /* Add your styles here */
  display: flex;
  flex-direction: column;
  margin-bottom: 15px;
}

/* Style the label */
.form-drop-down-wrapper .field-label {
  margin-bottom: 5px;
  font-weight: bold;
}

/* Style the dropdown itself */
.form-drop-down-wrapper select {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
  background-color: white; /* Ensure a consistent background */
  /* Adjust arrow appearance as needed */
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}

/* Optional: Style the dropdown arrow */
.form-drop-down-wrapper select::-ms-expand {
  display: none; /* Hide the default arrow for IE11 */
}

.form-drop-down-wrapper select::after {
  content: "\25BC";
  font-size: 12px;
  color: #ccc;
  /* Adjust positioning as needed */
  position: absolute;
  right: 10px;
  top: 50%;
  transform: translateY(-50%);
}
```

* Wrapper als Ziel auswählen: Die erste Auswahl (`.form-drop-down-wrapper`) dient dem äußeren Wrapper-Element, wobei sichergestellt wird, dass Stile auf die gesamte Dropdown-Komponente angewendet werden.
* Flexbox-Layout: Flexbox ordnet Beschriftung, Dropdown-Liste und Beschreibung vertikal für ein sauberes Layout an.
* Beschriftungsstile: Die Beschriftung zeichnet sich durch eine fett abgestufte Schriftgröße und einen leichten Rand aus.
* Dropdown-Stil: Das ausgewählte Element erhält einen Rahmen, einen Abstand und gerundete Ecken, um einen polierten Look zu erhalten.
* Hintergrundfarbe: Für visuelle Harmonie wird eine konsistente Hintergrundfarbe festgelegt.
* Pfeilanpassung: Optionale Stile blenden den standardmäßigen Dropdown-Pfeil aus und erstellen einen benutzerdefinierten Pfeil mit einem Unicode-Zeichen und einer Positionierung.

### Optionsfeld- und Kontrollkästchen-Gruppen

Ähnlich wie bei Dropdown-Komponenten haben Optionsfeld- und Kontrollkästchengruppen ihre eigene HTML-Struktur und CSS-Überlegungen:

#### HTML-Struktur von Optionsfeldern

```HTML
<div class="form-checkbox-group-wrapper form-{Name} field-wrapper" data-required={required}>
  <label class="field-label">{Label Text}</label>
  <div class="checkbox-group">
    <input type="checkbox" id="{FieldId}-1" name="{Name}" value="{Value1}">
    <label for="{FieldId}-1">{Option 1 Text}</label>
    <input type="checkbox" id="{FieldId}-2" name="{Name}" value="{Value2}">
    <label for="{FieldId}-2">{Option 2 Text}</label>
    </div>
  <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - Select multiple options (if applicable).
  </div>
</div>
```


#### HTML-Struktur von Optionsfeldern

```HTML
<div class="form-checkbox-group-wrapper form-{Name} field-wrapper" data-required={required}>
  <label class="field-label">{Label Text}</label>
  <div class="checkbox-group">
    <input type="checkbox" id="{FieldId}-1" name="{Name}" value="{Value1}">
    <label for="{FieldId}-1">{Option 1 Text}</label>
    <input type="checkbox" id="{FieldId}-2" name="{Name}" value="{Value2}">
    <label for="{FieldId}-2">{Option 2 Text}</label>
    </div>
  <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - Select multiple options (if applicable).
  </div>
</div>
```

#### CSS-Selektoren für Optionsfelder und Kontrollkästchengruppen

**Targeting des äußeren Wrappers**


```CSS
   /* Targets all radio group wrappers */
.form-radio-group-wrapper {
  margin-bottom: 20px; /* Adds space between radio groups */
}

/* Targets all checkbox group wrappers */
.form-checkbox-group-wrapper {
  margin-bottom: 20px; /* Adds space between checkbox groups */
}
```

Diese Selektoren richten sich an die äußersten Container von Optionsfeld- und Kontrollkästchengruppen, sodass Sie allgemeine Stile auf die gesamte Gruppenstruktur anwenden können. Dies ist nützlich zum Festlegen von Abstand, Ausrichtung oder anderen layoutbezogenen Eigenschaften.

**Bezeichnungen von Zielgruppen**

```CSS
.form-radio-group-wrapper .field-label,
.form-checkbox-group-wrapper .field-label {
 font-weight: bold; /* Makes the group label bold */
}
```

Diese Auswahl dient als Ziel für die `.field-label` -Element sowohl in Optionsfeld- als auch in Kontrollkästchen-Gruppenwrappern. Dadurch können Sie die Beschriftungen speziell für diese Gruppen gestalten und sie möglicherweise auffälliger gestalten.

**Targeting einzelner Eingaben und Beschriftungen**

```CSS
/* Styling radio buttons */
.form-radio-group-wrapper input[type="radio"] {
  margin-right: 5px; /* Adds space between the input and its label */
} 

/* Styling radio button labels */
.form-radio-group-wrapper label {
  font-size: 15px; /* Changes the label font size */
}

/* Styling checkboxes */
.form-checkbox-group-wrapper input[type="checkbox"] {
  margin-right: 5px;  /* Adds space between the input and its label */ 
}

/* Styling checkbox labels */
.form-checkbox-group-wrapper label {
  font-size: 15px; /* Changes the label font size */
}
```

Diese Selektoren bieten eine detailliertere Steuerung einzelner Optionsfelder, Kontrollkästchen und der zugehörigen Beschriftungen. Sie können diese verwenden, um Größenangaben, Abstände oder spezifischere visuelle Stile anzupassen.


**Anpassen der Darstellung von Optionsfeldern und Kontrollkästchen**

```CSS
/* Hide the default radio button or checkbox */
.form-radio-group-wrapper input[type="radio"],
.form-checkbox-group-wrapper input[type="checkbox"] {
  opacity: 0; 
  position: absolute; 
}

/* Create a custom radio button */
.form-radio-group-wrapper input[type="radio"] + label::before { 
  content: "";
  display: inline-block;
  width: 16px; 
  height: 16px; 
  border: 2px solid #ccc; 
  border-radius: 50%;
  margin-right: 5px;
}

.form-radio-group-wrapper input[type="radio"]:checked + label::before {
  background-color: #007bff; 
}

/* Create a custom checkbox */
/* Similar styling as above, with adjustments for a square shape */
```

Diese Technik blendet die Standardeingabe aus und verwendet :before und :after Pseudoelemente, um benutzerdefinierte Visuals zu erstellen, die das Erscheinungsbild basierend auf dem Status &quot;aktiviert&quot;ändern.


## Stilfelder

Zusätzlich zu den zuvor erläuterten allgemeinen Stiltechniken können Sie Formularfelder auch nach dem jeweiligen Typ oder nach einzelnen Namen formatieren. Dies ermöglicht eine präzisere Steuerung und Anpassung des Erscheinungsbilds Ihres Formulars.

### Formatierung basierend auf Feldtyp

Sie können CSS-Selektoren verwenden, um bestimmte Feldtypen als Ziel auszuwählen und Stile konsistent anzuwenden.

**HTML-Struktur**

```HTML
<div class="form-text-wrapper form-name field-wrapper" data-required="true">
  <label for="name" class="field-label">Name</label>
  <input type="text" placeholder="Enter your name" maxlength="50" id="name" name="name">
</div>

<div class="form-number-wrapper form-age field-wrapper" data-required="true">
  <label for="age" class="field-label">Age</label>
  <input type="number" placeholder="Enter your age" id="age" name="age">
</div>

<div class="form-email-wrapper form-email field-wrapper" data-required="true">
  <label for="email" class="field-label">Email Address</label>
  <input type="email" placeholder="Enter your email" id="email" name="email">
</div>
```

* Jedes Feld wird in ein `div` -Element mit mehreren Klassen:
   * `form-{Type}-wrapper`: Identifiziert den Feldtyp. Beispiel: `form-text-wrapper`, `form-number-wrapper`, `form-email-wrapper`.
   * `form-{Name}`: Identifiziert das Feld anhand seines Namens. Beispiel `form-name`, `form-age`, `form-email`.
   * `field-wrapper`: Eine allgemeine Klasse für alle Feld-Wrapper.
* Die `data-required` -Attribut gibt an, ob das Feld erforderlich oder optional ist.
* Jedes Feld verfügt über eine entsprechende Beschriftung, ein Eingabeelement und potenzielle zusätzliche Elemente wie Platzhalter und Beschreibungen.

Zum Beispiel:

```CSS
/* Target all text input fields */
.form-text-wrapper input {
  /* Add your styles here */
}

/* Target all number input fields */
.form-number-wrapper input {
  /* Add your styles here */
  letter-spacing: 2px; /* Example for adding letter spacing to all number fields */
}
```

### Formatieren bestimmter Feldtypen

Sie können auch einzelne Felder nach Namen ausrichten, um eindeutige Stile anzuwenden.

**HTML-Struktur**

```HTML
<div class="form-number-wrapper form-otp field-wrapper" data-required="true">
  <label for="otp" class="field-label">OTP</label>
  <input type="number" placeholder="Enter your OTP" maxlength="6" id="otp" name="otp">
</div>
```

**CSS-Selektor**

```CSS
.form-otp input {
   letter-spacing: 2px
}
```

* Selektor: Diese CSS-Datei enthält alle Eingabeelemente, die sich in einem Element mit der Klasse befinden `form-otp`. Ihre HTML-Struktur folgt den Konventionen des Formularblocks. Dies bedeutet, dass ein Container mit der Klasse &quot;form-otp&quot;markiert ist, der das Feld mit dem Namen &quot;otp&quot;enthält.

* Eigenschaft und Wert: Der Code wird angewendet `letter-spacing: 2px`. Diese CSS-Eigenschaft steuert den Abstand zwischen einzelnen Buchstaben im Textinhalt des Eingabefelds.