---
title: Anpassen des Designs und Stils für Edge Delivery Services für AEM Forms
description: Passen Sie effektiv das Design und den Stil für AEM Forms-Assets an, die über Edge Delivery Services bereitgestellt werden, und sorgen Sie so für ein kohärentes Benutzererlebnis mit Branding.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: ac780399-34fe-457d-aaf4-b675656c024d
source-git-commit: f843a7c91c3d47610580a3787a96e7e3bd49ba09
workflow-type: tm+mt
source-wordcount: '1916'
ht-degree: 83%

---

# Anpassen des Erscheinungsbilds Ihrer Formulare

Formulare sind von entscheidender Bedeutung für die Benutzerinteraktion auf Websites, da sie die Eingabe von Daten ermöglichen. Sie können Cascading Style Sheets (CSS) verwenden, um Felder eines Formulars zu formatieren und so die visuelle Darstellung Ihrer Formulare und das Anwendererlebnis zu verbessern.

Der adaptive Formularblock sorgt für eine einheitliche Struktur aller Formularfelder. Die konsistente Struktur erleichtert die Entwicklung der CSS-Auswahl zur Auswahl und Formatierung von Formularfeldern basierend auf Feldtyp und Feldnamen.

In diesem Dokument wird die HTML-Struktur für verschiedene Formularkomponenten beschrieben. Sie erhalten ein Verständnis dafür, wie Sie die CSS-Auswahlen für verschiedene Formularfelder erstellen, um Formularfelder in einem adaptiven Formularbaustein zu formatieren.

Am Ende des Artikels werden Sie Folgendes erreicht haben:

- Sie gewinnen ein Verständnis der Struktur der standardmäßigen CSS-Datei, die im adaptiven Formularbaustein enthalten ist.
- Sie gewinnen ein Verständnis der HTML-Struktur von Formularkomponenten, die vom adaptiven Formularbaustein bereitgestellt werden, einschließlich allgemeiner Komponenten und spezifischer Komponenten wie Dropdown-Listen, Optionsfeld- und Kontrollkästchengruppen.
- Sie lernen, wie Sie Formularfelder mithilfe der CSS-Auswahlen basierend auf dem Feldtyp und den Feldnamen formatieren, was eine konsistente oder eindeutige Formatierung basierend auf Anforderungen ermöglicht.

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


## Formatieren eines Formulars für den adaptiven Formularbaustein

Der adaptive Formularbaustein bietet eine standardisierte HTML-Struktur, die die Auswahl und Formatierung von Formularkomponenten vereinfacht:

- **Standardstile aktualisieren**: Sie können die Standardstile eines Formulars ändern, indem Sie die CSS-Datei des Formulars bearbeiten. Die Standardstile sind im GitHub-Repository Ihres Projekts verfügbar, in der Regel unter: `https://github.com/<your-github-username>/<your-repository>/tree/main/blocks/form/form.css`. Diese Datei bietet umfassende Stile für Formulare, unterstützt mehrstufige Assistentenformulare und betont die Verwendung benutzerdefinierter CSS-Eigenschaften für eine einfache Anpassung.

- **CSS-Stilmuster**: Edge Delivery Services verwendet eine blockbasierte CSS-Architektur. Verwenden Sie die folgenden empfohlenen Selektormuster:

  **Primäre Muster (empfohlen):**

  ```css
  /* Block-level styling - Form container */
  .form {
      /* Styles for the entire form block */
      max-width: 600px;
      margin: 0 auto;
  }
  
  /* Form element styling */
  .form form {
      /* Styles for the actual <form> element */
      padding: 2rem;
  }
  
  /* Field wrapper styling by type */
  .form .{Type}-wrapper input {
      /* Styles for input fields */
      padding: 0.75rem;
      border: 1px solid #ccc;
  }
  ```

  **Kontextspezifische Muster (wenn eine höhere Spezifität erforderlich ist):**

  ```css
  /* When you need higher specificity for main content area */
  main .form .{Type}-wrapper input {
      /* More specific targeting */
      border-color: #007cba;
  }
  ```

## Komponentenstruktur

Der adaptive Formularbaustein bietet eine konsistente HTML-Struktur für verschiedene Formularelemente, wodurch Formatierungen und die Verwaltung vereinfacht werden. Sie können die Komponenten mithilfe von CSS für Formatierungszwecke bearbeiten.

### Allgemeine Komponenten (außer Dropdown-Listen, Optionsfeldgruppen und Kontrollkästchengruppen):

Alle Formularfelder mit Ausnahme von Dropdown-Listen, Optionsfeldgruppen und Kontrollkästchengruppen haben die folgende HTML-Struktur:

+++ HTML-Struktur der allgemeinen Komponenten

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

+++

+++ CSS-Auswahl für allgemeine Komponenten

```CSS
  
  /* Primary Pattern: Target field wrapper by type */
  .form .{Type}-wrapper {
    /* Add your styles here */
    margin-bottom: 1rem;
    border-radius: 4px;
  }
  
  /* Primary Pattern: Target input fields within wrapper */
  .form .{Type}-wrapper input {
    /* Add your styles here */
    border: 1px solid #ccc;
    padding: 8px;
    border-radius: 4px;
    width: 100%;
  }
  
  /* Context-specific: Target element by field name when higher specificity needed */
  .form .field-{Name} input {
    /* Add your styles here */
    /* Use this pattern for specific field customization */
  }
  
```

- `.form .{Type}-wrapper`: Targeting des Feld-Wrapper-Elements basierend auf dem Feldtyp. Beispielsweise ist `.form .text-wrapper` auf alle Textfeld-Container ausgerichtet.
- `.form .{Type}-wrapper input`: Targeting der tatsächlichen Eingabeelemente im Wrapper. Dies ist das empfohlene Muster für die Formatierung von Formulareingaben.
- `.form .field-{Name}`: Targeting von Elementen basierend auf dem spezifischen Feldnamen. Beispielsweise zielt `.form .field-first-name` auf den Feld-Container „Vorname“ ab. Verwenden Sie `.form .field-{Name} input` , um das Eingabeelement gezielt anzusprechen.
- **Vermeiden**: `main .form form .{Type}-wrapper` - Dies führt zu einer unnötigen CSS-Spezifität und ist schwieriger zu pflegen.

**Beispiel einer CSS-Auswahl für allgemeine Komponenten**

```CSS
/* Primary Pattern: Target all text input fields */
.form .text-wrapper input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
  width: 100%;
}

/* Context-specific: Target field by name when higher specificity needed */
.form .field-first-name input {
  text-transform: capitalize;
  border-color: #007cba;
}

/* Alternative with main context if needed */
main .form .text-wrapper input {
  /* Use only when you need higher specificity */
  color: #333;
}
```

+++

### Dropdown-Komponente

Bei Dropdown-Menüs wird das `select`-Element anstelle des `input`-Elements verwendet:

+++ HTML-Struktur der Dropdown-Komponente

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

+++

+++ CSS-Auswahlen für Dropdown-Komponenten

Im folgenden CSS sind einige Beispiele von CSS-Auswahlen für Dropdown-Komponenten aufgeführt.

```CSS
/* Primary Pattern: Target the dropdown wrapper */
.form .drop-down-wrapper {
  /* Add your styles here */
  display: flex;
  flex-direction: column;
  margin-bottom: 15px;
}

/* Target the select element */
.form .drop-down-wrapper select {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
  background-color: #fff;
}

/* Style the label */
.form .drop-down-wrapper .field-label {
  margin-bottom: 5px;
  font-weight: bold;
}
```

- Auswählen des Wrappers als Ziel: Die erste Auswahl (`.drop-down-wrapper`) wählt das äußere Wrapper-Element als Ziel aus, wodurch sichergestellt wird, dass die Stile auf die gesamte Dropdown-Komponente angewendet werden.
- Flexbox-Layout: Flexbox ordnet Beschriftung, Dropdown-Liste und Beschreibung vertikal für ein sauberes Layout an.
- Beschriftungsformatierung: Die Beschriftung zeichnet sich durch eine fette Schriftstärke und einen leichten Rand aus.
- Formatierung der Dropdown-Liste: Das ausgewählte `select`-Element erhält einen Rahmen, einen Abstand und gerundete Ecken für einen hochwertigen Look.
- Hintergrundfarbe: Für visuelle Harmonie wird eine konsistente Hintergrundfarbe festgelegt.
- Pfeilanpassung: Optionale Stile blenden den standardmäßigen Dropdown-Pfeil aus und erstellen einen benutzerdefinierten Pfeil mit einem Unicode-Zeichen und einer Positionierung.

+++

### Optionsfeldgruppen

Ähnlich wie bei Dropdown-Komponenten haben Optionsfeldgruppen ihre eigene HTML- und CSS-Struktur:

+++ HTML-Struktur der Optionsfeldgruppe

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

+++

+++ CSS-Auswahlen für Optionsfeldgruppen

- Abzielen auf den Feldsatz

```CSS
  main .form form .radio-group-wrapper {
    border: 1px solid #ccc;
    padding: 10px;
  }
```

Dieser Selektor wählt alle Feldsätze mit dem Klassen-Optionsfeldgruppen-Wrapper aus.  Dies wäre nützlich, um allgemeine Stile auf die gesamte Optionsfeldgruppe anzuwenden.

- Targeting von Optionsfeldbezeichnungen

```CSS
main .form form .radio-wrapper label {
    font-weight: normal;
    margin-right: 10px;
  }
```

- Targeting aller Optionsfeldbezeichnungen innerhalb eines bestimmten Feldsatzes basierend auf seinem Namen

```CSS
main .form form .field-color .radio-wrapper label {
  /* Your styles here */
}
```

+++

### Kontrollkästchengruppe

+++ HTML-Struktur der Kontrollkästchengruppe

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

+++

+++ CSS-Auswahl für Kontrollkästchengruppen

- Auf den äußeren Wrapper abzielen: Diese Auswahl wählt die äußersten Container von Optionsfeld- und Kontrollkästchengruppen als Ziel aus, sodass Sie allgemeine Stile auf die gesamte Gruppenstruktur anwenden können. Dies ist nützlich zum Festlegen von Abstand, Ausrichtung oder anderen Layout-bezogenen Eigenschaften.

```CSS
  
  /* Primary Pattern: Targets radio group wrappers */
  .form .radio-group-wrapper {
    margin-bottom: 20px; /* Adds space between radio groups */  
    display: flex;
    flex-direction: column;
  }

  /* Primary Pattern: Targets checkbox group wrappers */
  .form .checkbox-group-wrapper {
    margin-bottom: 20px; /* Adds space between checkbox groups */
    display: flex;
    flex-direction: column;
  }
```

- Bezeichnungen der Zielgruppe: Diese Auswahl wählt das `.field-label`-Element sowohl in Optionsfeld- als auch in Kontrollkästchengruppen-Wrappern als Ziel aus. Dadurch können Sie die Beschriftungen speziell für diese Gruppen formatieren und sie ggf. auffälliger gestalten.

```CSS
/* Primary Pattern: Target group labels */
.form .radio-group-wrapper legend,
.form .checkbox-group-wrapper legend {
  font-weight: bold; /* Makes the group label bold */
  margin-bottom: 0.5rem;
  font-size: var(--form-font-size-base);
}
```

- Targeting einzelner Eingaben und Beschriftungen: Diese Auswahl bietet eine präzisere Kontrolle über einzelne Optionsfelder, Kontrollkästchen und die zugehörigen Beschriftungen. Sie können diese verwenden, um Größe und Abstand anzupassen oder spezifischere visuelle Stile anzuwenden.

```CSS
/* Primary Pattern: Styling radio buttons */
.form .radio-group-wrapper input[type="radio"] {
  margin-right: 8px; /* Adds space between the input and its label */
  margin-bottom: 4px;
}

/* Primary Pattern: Styling radio button labels */
.form .radio-group-wrapper label {
  font-size: var(--form-font-size-base); /* Changes the label font size */
  display: flex;
  align-items: center;
}

/* Primary Pattern: Styling checkboxes */
.form .checkbox-group-wrapper input[type="checkbox"] {
  margin-right: 8px; /* Adds space between the input and its label */
  margin-bottom: 4px;
}

/* Primary Pattern: Styling checkbox labels */
.form .checkbox-group-wrapper label {
  font-size: var(--form-font-size-base); /* Changes the label font size */
  display: flex;
  align-items: center;
}
```

- Anpassen des Erscheinungsbilds von Optionsfeldern und Kontrollkästchen: Diese Methode blendet die Standardeingabe aus und verwendet die Pseudo-Elemente `:before` und `:after`, um benutzerdefinierte Visualisierungen zu erstellen, die das Erscheinungsbild basierend auf dem Status „aktiviert“ ändern.

```CSS
/* Hide the default radio button or checkbox */
main .form form .radio-group-wrapper input[type="radio"],
main .form form .checkbox-group-wrapper input[type="checkbox"] {
  opacity: 0;
  position: absolute;
}

/* Create a custom radio button */
main .form form .radio-group-wrapper input[type="radio"] + label::before {
  /* ... styles for custom radio button ... */
}

main .form form .radio-group-wrapper input[type="radio"]:checked + label::before {
  /* ... styles for checked radio button ... */
}

/* Create a custom checkbox */
main .form form .checkbox-group-wrapper input[type="checkbox"] + label::before {
  /* ... styles for custom checkbox ... */
}

main .form form .checkbox-group-wrapper input[type="checkbox"]:checked + label::before {
  /* ... styles for checked checkbox ... */
}
```

+++

### Bedienfeld-/Container-Komponenten

+++ HTML-Struktur von Bedienfeld-/Container-Komponenten

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

+++

+++ Beispiel zur CSS-Auswahl für Bedienfeld-/Container-Komponenten

1. Targeting des Bedienfelds:

```CSS
  /* Target the entire panel container */
  main .form form .panel-wrapper {
    /* Add your styles here (e.g., border, padding, background color) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
 }
```

- Die `.panel-wrapper`-Auswahl gestaltet alle Elemente mit dem Klassenbedienfeld-Wrapper, wodurch ein einheitlicher Look für alle Bedienfelder entsteht.

1. Targeting des Bedientitels:

```CSS
  /* Target the legend element (panel title) */
  .panel-wrapper legend {
    /* Add your styles here (e.g., font-weight, font-size) */
    font-weight: bold;
    font-size: 16px;
    padding-bottom: 5px;
    margin-bottom: 10px;
    border-bottom: 1px solid #ddd; /* Optional: create a separation line */
  }
```

- Die `.panel-wrapper legend`-Auswahl gestaltet das legend-Element im Bedienfeld, sodass der Titel optisch hervorgehoben wird.


1. Targeting einzelner Felder im Bedienfeld:

```CSS
/* Target all form field wrappers within a panel */
main .form form .panel-wrapper .{Type}-wrapper {
  /* Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```

- Die Auswahl `.panel-wrapper .{Type}-wrapper` wählt alle Wrapper mit der Klasse `.{Type}-wrapper` innerhalb des Bedienfelds als Ziel aus, sodass Sie den Abstand zwischen Formularfeldern festlegen können.

1. Targeting bestimmter Felder (optional):

```CSS
  /* Target the username field wrapper */
  main .form form .panel-wrapper .text-wrapper.field-username {
    /* Add your styles here (specific to username field) */
  }

  /* Target the password field wrapper */
  main .form form .panel-wrapper .password-wrapper.field-password {
    /* Add your styles here (specific to password field) */
  }
```

- Mit diesen optionalen Auswahlen können Sie bestimmte Feld-Wrapper innerhalb des Bedienfelds als Ziel auswählen, um einen eindeutigen Stil zu ermöglichen, z. B. zur Hervorhebung des Felds „Benutzername“.

+++

### Wiederholbares Bedienfeld

+++ HTML-Struktur eines wiederholbaren Bedienfelds

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

+++

+++ CSS-Auswahl für ein wiederholbares Bedienfeld

- Targeting aller wiederholbaren Bedienfelder:

```CSS
  /* Target all panels with the repeatable attribute */
 main .form form .panel-wrapper[data-repeatable="true"] {
    /* Add your styles here (e.g., border, margin) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
  }
```

Die Auswahl gestaltet alle wiederholbaren Bedienfelder und sorgt so für ein einheitliches Look-and-Feel.


- Targeting einzelner Felder in einem Bedienfeld:

```CSS
/* Target all form field wrappers within a repeatable panel */
main .form form .panel-wrapper[data-repeatable="true"] .{Type}-wrapper {
  /* Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```

Diese Auswahl gestaltet alle Feld-Wrapper in einem wiederholbaren Bedienfeld, wobei ein konsistenter Abstand zwischen Feldern beibehalten wird.

- Targeting bestimmter Felder (in einem Bedienfeld):

```CSS
/* Target the name field wrapper within the first panel */
main .form form .panel-wrapper[data-repeatable="true"][data-index="0"] .text-wrapper.field-name {
  /* Add your styles here (specific to first name field) */
}

/- Target all
```

+++

### Dateianhang

+++ HTML-Struktur für Dateianhänge

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

+++

+++ CSS-Auswahl für die Dateianhangskomponente

- Targeting der gesamten Dateianhangskomponente:

```CSS
/* Target the entire file attachment component */
main .form form .file-wrapper {
  /* Add your styles here (e.g., border, padding) */
  border: 1px solid #ccc;
  padding: 15px;
  border-radius: 4px;
  margin-bottom: 20px;
}
```

Diese Auswahl gestaltet die gesamte Dateianhangskomponente, einschließlich Legende, Ziehbereich, Eingabefeld und Liste.

- Targeting bestimmter Elemente:

```CSS
/* Target the drag and drop area */
main .form form .file-wrapper .file-drag-area {
  /* Add your styles here (e.g., background color, border) */
  background-color: #f0f0f0;
  border: 1px dashed #ddd;
  padding: 10px;
  text-align: center;
}

/* Target the file input element */
main .form form .file-wrapper input[type="file"] {
  /* Add your styles here (e.g., hide the default input) */
  display: none;
}

/* Target individual file descriptions within the list (populated dynamically) */
main .form form .file-wrapper .files-list .file-description {
  /* Add your styles here (e.g., margin, display) */
  display: flex;
  justify-content: space-between;
  margin-bottom: 5px;
}

/* Target the file name within the description */
main .form form .file-wrapper .files-list .file-description .file-description-name {
  /* Add your styles here (e.g., font-weight) */
  font-weight: bold;
}
```

Mit diesen Auswahlen können Sie verschiedene Teile der Dateianhangskomponente individuell gestalten. Sie können die Stile entsprechend Ihren Design-Voreinstellungen anpassen.

+++


## Formatieren von Komponenten

Sie können Formularfelder nach dem jeweiligen Typ (`{Type}-wrapper`) oder nach einzelnen Namen (`field-{Name}`) gestalten. Dies ermöglicht eine präzisere Steuerung und Anpassung des Erscheinungsbilds Ihres Formulars.

### Formatierung basierend auf Feldtyp

Sie können CSS-Auswahlen verwenden, um bestimmte Feldtypen als Ziel auszuwählen und Stile konsistent anzuwenden.

+++ HTML-Struktur

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


+++


+++ Beispiel einer CSS-Auswahl

```CSS
/* Primary Pattern: Target all text input fields */
.form .text-wrapper input {
  /* Add your styles here */
  width: 100%;
  padding: var(--form-input-padding);
}

/* Primary Pattern: Target all number input fields */
.form .number-wrapper input {
  /* Add your styles here */
  letter-spacing: 2px; /* Example for adding letter spacing to all number fields */
  text-align: center;
}
```

+++

### Formatierung basierend auf Feldnamen

Sie können auch einzelne Felder nach Namen als Ziel auswählen, um eindeutige Stile anzuwenden.

+++ HTML-Struktur

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

+++

+++ Beispiel einer CSS-Auswahl

```CSS
/* Primary Pattern: Target specific field by name */
.form .field-otp input {
   letter-spacing: 2px;
   text-align: center;
   font-family: monospace;
}

/* Context-specific: Use higher specificity when needed */
main .form .field-otp input {
   /* Use only when you need to override other styles */
   font-weight: bold;
}
```

Diese CSS-Datei wählt alle Eingabeelemente als Ziel aus, die sich in einem Element mit der Klasse `field-otp` befinden. Die Formularstruktur von Edge Delivery Services folgt den Konventionen für adaptive Forms-Blöcke, bei denen Container mit feldspezifischen Klassen wie „field-otp“ für Felder mit dem Namen „otp“ markiert sind.

+++

## CSS-Dateistruktur und Verweise

### **Standardstile - Speicherort**

Die Standardstile für Formulare befinden sich unter:

```
https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/blocks/form/form.css
```

### **Lokale Projektstruktur**

In Ihrem Edge Delivery Services-Projekt:

```
/blocks/form/form.css          // Main form block styles
/styles/styles.css             // Global site styles
/styles/lazy-styles.css        // Additional component styles
```

### **Benutzerdefinierte CSS-Integration**

1. **Anpassung auf Projektebene**: Stile zu `/styles/styles.css` hinzufügen
2. **Formularspezifische Anpassung**: `/blocks/form/form.css` ändern
3. **Komponentenüberschreibungen**: Verwenden Sie in Ihrem benutzerdefinierten CSS die entsprechenden Spezifitätsselektoren

## Beheben von CSS-Problemen

### **CSS-Spezifitätsprobleme**

```css
/* ❌ Problem: Styles not applying */
.text-wrapper input {
  color: red;
}

/* ✅ Solution: Match or exceed existing specificity */
.form .text-wrapper input {
  color: red;
}

/* ✅ Alternative: Use higher specificity when needed */
main .form .text-wrapper input {
  color: red;
}
```

### **Probleme mit der Überschreibung von CSS-Variablen**

```css
/* ❌ Problem: Variables not working */
.form {
  --form-border-color: blue; /* Local scope only */
}

/* ✅ Solution: Define in root scope */
:root {
  --form-border-color: blue; /* Global scope */
}
```

### **Häufige Selektorfehler**

```css
/* ❌ Incorrect: Assumes direct nesting */
.form form input {
  /* This might miss inputs in wrappers */
}

/* ✅ Correct: Target actual structure */
.form .text-wrapper input {
  /* Targets actual HTML structure */
}

/* ❌ Avoid: Unnecessary specificity */
main .form form .text-wrapper input {
  /* Too specific, harder to override */
}

/* ✅ Preferred: Balanced specificity */
.form .text-wrapper input {
  /* Easier to maintain and override */
}
```

### **Formularstatus-Formatierung**

```css
/* Validation states */
.form .field-wrapper.error input {
  border-color: var(--form-error-color);
}

.form .field-wrapper.success input {
  border-color: var(--form-success-color);
}

/* Loading state */
.form[data-submitting="true"] {
  opacity: 0.7;
  pointer-events: none;
}

/* Disabled state */
.form input:disabled {
  background-color: var(--form-input-disabled-background);
  cursor: not-allowed;
}
```

### **Komponentenspezifische Best Practices**

#### **Schaltflächenstile**

```css
/* Primary buttons */
.form .button-wrapper button[type="submit"] {
  background-color: var(--form-focus-color);
  color: white;
  border: none;
  padding: var(--form-input-padding);
  border-radius: var(--form-border-radius);
}

/* Secondary buttons */
.form .button-wrapper button[type="reset"] {
  background-color: transparent;
  color: var(--form-text-color);
  border: 1px solid var(--form-border-color);
}
```

#### **Responsiver Formularentwurf**

```css
/* Mobile-first approach */
.form {
  width: 100%;
  padding: 1rem;
}

/* Tablet and up */
@media (min-width: 768px) {
  .form {
    max-width: var(--form-max-width);
    padding: var(--form-padding);
  }
}
```

## Zusammenfassung der Best Practices

1. **Benutzerdefinierte CSS-Eigenschaften verwenden**: Variablen für ein konsistentes Design nutzen
2. **Blockbasierte Architektur befolgen**: `.form` als primären Blockselektor verwenden
3. **Überspezifität vermeiden**: Verwenden Sie `main .form form` nicht, es sei denn, dies ist notwendig
4. **Target-Wrapper**: Verwenden von `.{Type}-wrapper` für das Komponenten-Targeting
5. **Konsistenz wahren**: Verwenden Sie dieselben Selektormuster im gesamten Projekt
6. **Geräteübergreifend testen**: Stellen Sie sicher, dass Formulare auf Mobilgeräten, Tablets und Desktop einwandfrei funktionieren
7. **Barrierefreiheit überprüfen**: Stellen Sie sicher, dass Stile Bildschirmlesehilfen oder die Tastaturnavigation nicht beeinträchtigen


