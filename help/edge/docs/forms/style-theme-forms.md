---
title: Anpassen des Designs und Stils für ein AEM Forms Edge Delivery Services-Formular
description: Anpassen des Designs und Stils für ein AEM Forms Edge Delivery Services-Formular
feature: Edge Delivery Services
exl-id: c214711c-979b-4833-9541-8e35b2aa8e09
source-git-commit: 5eee563a9a425ef187afed69a8159d8b1298dad7
workflow-type: tm+mt
source-wordcount: '2014'
ht-degree: 41%

---


# Anpassen des Erscheinungsbilds Ihrer Formulare

Formulare sind von entscheidender Bedeutung für die Benutzerinteraktion auf Websites, da sie die Eingabe von Daten ermöglichen. Sie können Cascading Style Sheets (CSS) verwenden, um Felder eines Formulars zu formatieren, die visuelle Darstellung Ihrer Formulare zu verbessern und das Benutzererlebnis zu verbessern.

Der Adaptive Forms-Block erzeugt eine einheitliche Struktur für alle Formularfelder. Die konsistente Struktur erleichtert die Entwicklung von CSS-Selektoren zur Auswahl und Formatierung von Formularfeldern basierend auf Feldtyp und Feldnamen.

In diesem Dokument wird die HTML-Struktur für verschiedene Formularkomponenten beschrieben. Sie erhalten ein Verständnis dafür, wie Sie CSS-Selektoren für verschiedene Formularfelder erstellen, um Formularfelder in einem adaptiven Forms-Block zu formatieren.

Am Ende des Artikels:

* Sie erstellen ein Verständnis der Struktur der standardmäßigen CSS-Datei, die im Adaptive Forms Block enthalten ist.
* Sie erstellen ein Verständnis der HTML-Struktur von Formularkomponenten, die vom Adaptive Forms-Block bereitgestellt werden, einschließlich allgemeiner Komponenten und bestimmter Komponenten wie Dropdown-Listen, Optionsfeldgruppen und Kontrollkästchengruppen.
* Sie erfahren, wie Sie Formularfelder mithilfe von CSS-Selektoren basierend auf dem Feldtyp und den Feldnamen formatieren und so eine konsistente oder eindeutige Formatierung basierend auf Anforderungen ermöglichen.


## Grundlagen zu Formularfeldtypen

Bevor wir uns mit der Formatierung befassen, sollten wir das gemeinsame Formular lesen [Feldtypen](/help/edge/docs/forms/form-components.md) unterstützt durch den Adaptive Forms-Block:

* Eingabefelder: Dazu gehören Texteingaben, E-Mail-Eingaben, Kennworteingaben usw.
* Kontrollkästchengruppen: Dienen zum Auswählen mehrerer Optionen.
* Optionsfeldgruppen: Dienen zum Auswählen einer einzelnen Option aus einer Gruppe.
* Dropdown-Listen: Werden auch als Auswahlfelder bezeichnet und dienen zum Auswählen einer Option aus einer Liste.
* Bedienfelder/Container: Dienen zum Gruppieren zugehöriger Formularelemente.

## Standard-Formatierungsgrundsätze

Grundlagen [CSS-Grundkonzepte](https://www.w3schools.com/css/css_intro.asp) ist vor der Formatierung bestimmter Formularfelder von entscheidender Bedeutung:

* [Selektoren](https://www.w3schools.com/css/css_selectors.asp): Mit CSS-Selektoren können Sie bestimmte HTML-Elemente für die Formatierung auswählen. Sie können die Elementauswahl, Klassenauswahl oder ID-Auswahl verwenden.
* [Eigenschaften](https://www.w3schools.com/css/css_syntax.asp): CSS-Eigenschaften definieren das visuelle Erscheinungsbild von Elementen. Zu den allgemeinen Eigenschaften für die Formatierung von Formularfeldern gehören u. a. Farbe, Hintergrundfarbe, Rahmen, Abstand und Rand.
* [Box-Modell](https://www.w3schools.com/css/css_boxmodel.asp): Das CSS-Box-Modell beschreibt die Struktur von HTML-Elementen als Inhaltsbereich, der von Abstand, Rahmen und Rändern umgeben ist.
* Flexbox/Raster: CSS [Flexbox](https://www.w3schools.com/css/css3_flexbox.asp) und [Rasterlayouts](https://www.w3schools.com/css/css_grid.asp) sind leistungsstarke Tools zum Erstellen responsiver und flexibler Designs.

## Formatieren eines Formulars für adaptiven Forms-Block

Der Adaptive Forms Block bietet eine standardisierte HTML-Struktur, die die Auswahl und Formatierung von Formularkomponenten vereinfacht:

* **Aktualisieren von Standardstilen**: Sie können die Standardstile eines Formulars ändern, indem Sie die `/blocks/form/form.css file` bearbeiten. Diese Datei bietet eine umfassende Formatierung für ein Formular, das mehrstufige Assistentenformulare unterstützt. Der Schwerpunkt liegt auf der Verwendung benutzerdefinierter CSS-Variablen für eine einfache Anpassung, Wartung und einheitliche Formatierung in allen Formularen. Anweisungen zum Hinzufügen des adaptiven Forms-Blocks zu Ihrem Projekt finden Sie unter [Formular erstellen](/help/edge/docs/forms/create-forms.md).

* **Anpassen**: Verwenden Sie die das Standard-`forms.css` als Basis und passen Sie es an, um das Look-and-Feel Ihrer Formularkomponenten zu ändern, sodass es visuell ansprechend und benutzerfreundlich ist. Die Dateistruktur fördert die Organisation und verwaltet Stile für Formulare, wodurch konsistente Designs auf Ihrer Website gefördert werden.

## Aufschlüsselung der Struktur von forms.css

* **Globale Variablen:** Definiert unter `:root` Ebene, diese Variablen (`--variable-name`) speichern Werte, die im gesamten Stylesheet verwendet werden, um Konsistenz und einfache Aktualisierung zu gewährleisten. Diese Variablen definieren Farben, Schriftgrößen, Abstände und andere Eigenschaften. Sie können Ihre eigenen globalen Variablen deklarieren oder vorhandene ändern, um den Stil des Formulars zu ändern.

* **Universelle Auswahlstile:** Die `*`-Auswahl stimmt mit jedem Element im Formular überein, wodurch sichergestellt wird, dass Stile standardmäßig auf alle Komponenten angewendet werden, einschließlich der Festlegung der Eigenschaft `box-sizing` auf `border-box`.

* **Formatierung von Formularen:** Dieser Abschnitt konzentriert sich auf die Formatierung von Formularkomponenten mithilfe der Auswahlen für das Targeting bestimmter HTML-Elemente. Sie definiert Stile für Eingabefelder, Textbereiche, Kontrollkästchen, Optionsfelder, Dateieingaben, Formularbeschriftungen und Beschreibungen.

* **Formatierung des Assistenten (falls zutreffend):** Dieser Abschnitt dient der Formatierung des Assistenten-Layouts, eines aus mehreren Schritten bestehenden Formulars, in dem jeder Schritt einzeln angezeigt wird. Sie definiert Stile für den Assistenten-Container, Feldsätze, Legenden, Navigationsschaltflächen und responsive Layouts.

* **Medienabfragen:** Diese bieten Stile für unterschiedliche Bildschirmgrößen und passen das Layout und die Formatierung entsprechend an.

* **Verschiedene Formatierungen:** In diesem Abschnitt werden Stile für Erfolgs- oder Fehlermeldungen, Datei-Upload-Bereiche und andere Elemente behandelt, auf die Sie in einem Formular stoßen können.


## Komponentenstruktur

Der Adaptive Forms-Block bietet eine konsistente HTML-Struktur für verschiedene Formularelemente, die eine einfachere Formatierung und Verwaltung ermöglicht. Sie können die Komponenten mithilfe von CSS für Formatierungszwecke bearbeiten.

### Allgemeine Komponenten (außer Dropdown-Listen, Optionsfeldgruppen und Kontrollkästchengruppen):

Alle Formularfelder mit Ausnahme von Dropdown-Listen, Optionsfeldgruppen und Kontrollkästchengruppen haben die folgende HTML-Struktur:

+++ HTML-Struktur der allgemeinen Komponenten

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
   </div>
</div>
```

* Klassen: Das div-Element verfügt über mehrere Klassen für das Targeting bestimmter Elemente und für die Formatierung. Sie benötigen die `{Type}-wrapper` oder `field-{Name}` Klassen zum Entwickeln eines CSS-Selektors, um ein Formularfeld zu formatieren:
   * {Type}: Identifiziert die Komponente nach Feldtyp. Zum Beispiel Text (Text-Wrapper), Zahl (Nummer-Wrapper), Datum (Datum-Wrapper).
   * {Name}: Identifiziert die Komponente anhand des Namens. Der Name des Felds darf nur alphanumerische Zeichen enthalten. Mehrere aufeinander folgende Gedankenstriche im Namen werden durch einen einzigen Bindestrich ersetzt `(-)`, und die Start- und Endabstände in einem Feldnamen werden entfernt. Beispiel: Vorname (field-first-name field-wrapper).
   * {FieldId}: Eine eindeutige Kennung für das Feld, die automatisch generiert wird.
   * {Required}: Ein boolescher Wert, der angibt, ob das Feld erforderlich ist.
* Titel: Das Element `label` liefert einen beschreibenden Text für das Feld und ordnet ihn dem Eingabeelement mithilfe des `for`-Attributs zu.
* Eingabe: Das `input`-Element definiert den einzugebenden Datentyp. Zum Beispiel : text, number, email.
* Beschreibung (optional): `div` mit der Klasse `field-description` stellt zusätzliche Informationen oder Anweisungen für Benutzende bereit.

**HTML-Struktur**

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

+++ CSS-Selektor für allgemeine Komponenten

```CSS
  
  /* Target all input fields within any .{Type}-wrapper  */
  .{Type}-wrapper  {
    /* Add your styles here */
    border: 1px solid #ccc;
    padding: 8px;
    border-radius: 4px;
  }
  
  /* Target all input fields within any .{Type}-wrapper  */
  .{Type}-wrapper input {
    /* Add your styles here */
    border: 1px solid #ccc;
    padding: 8px;
    border-radius: 4px;
  }
  
  /* Target any element with the class field-{Name}  */
  .field-{Name} {
    /* Add your styles here */
    /* This could be used for styles specific to all elements with   field-{Name} class, not just inputs */
  }
  
  
```

* `.{Type}-wrapper`: Targeting des äußeren `div` -Element basierend auf dem Feldtyp. Beispiel: `.text-wrapper` Alle Textfelder als Zielgruppe festlegen.
* `.field-{Name}`: Wählt das Element weiter auf Grundlage des spezifischen Feldnamens aus. Beispiel: `.field-first-name` gibt das Textfeld &quot;Vorname&quot;als Ziel an. Dieser Selektor kann für das Targeting von Elementen mit dem Feld-{Name} Klasse, es ist wichtig, vorsichtig zu sein. In diesem speziellen Fall wäre es nicht hilfreich, Eingabefelder zu formatieren, da nicht nur die Eingabe selbst, sondern auch die Titel- und Beschreibungselemente ausgewählt werden. Es wird empfohlen, spezifischere Selektoren wie diejenigen zu verwenden, die für die Zielgruppenbestimmung von Texteingabefeldern verfügbar sind (.text-wrapper-Eingabe).



**Beispiel-CSS-Selektoren für allgemeine Komponenten**

```CSS
/*Target all text input fields */

text-wrapper input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}

/*Target all fields with name first-name*/

first-name input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}
```
+++

### Dropdown-Komponente

Bei Dropdown-Menüs wird das `select`-Element anstelle des `input`-Elements verwendet:



+++ HTML-Struktur der Dropdown-Komponente

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <select id="{FieldId}" name="{Name}"><option></option><option></option></select>
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

+++ CSS-Selektoren für Dropdown-Komponenten

Im folgenden CSS sind einige Beispiele für CSS-Selektoren für Dropdown-Komponenten aufgeführt.

```CSS
/* Target the outer wrapper */
.drop-down-wrapper {
  /* Add your styles here */
  display: flex;
  flex-direction: column;
  margin-bottom: 15px;
}

/* Style the label */
.drop-down-wrapper .field-label {
  margin-bottom: 5px;
  font-weight: bold;
}

/* Style the dropdown itself */
.drop-down-wrapper select {
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
.drop-down-wrapper select::-ms-expand {
  display: none; /* Hide the default arrow for IE11 */
}

.drop-down-wrapper select::after {
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

* Auswählen des Wrappers als Ziel: Die erste Auswahl (`.drop-down-wrapper`) wählt das äußere Wrapper-Element als Ziel aus, wodurch sichergestellt wird, dass die Stile auf die gesamte Dropdown-Komponente angewendet werden.
* Flexbox-Layout: Flexbox ordnet Beschriftung, Dropdown-Liste und Beschreibung vertikal für ein sauberes Layout an.
* Beschriftungsformatierung: Die Beschriftung zeichnet sich durch eine fette Schriftstärke und einen leichten Rand aus.
* Dropdown-Stile: Der `select` -Element erhält einen Rahmen, einen Abstand und abgerundete Ecken, um ein poliertes Erscheinungsbild zu erhalten.
* Hintergrundfarbe: Für visuelle Harmonie wird eine konsistente Hintergrundfarbe festgelegt.
* Pfeilanpassung: Optionale Stile blenden den standardmäßigen Dropdown-Pfeil aus und erstellen einen benutzerdefinierten Pfeil mit einem Unicode-Zeichen und einer Positionierung.

+++

### Optionsfeldgruppen

Ähnlich wie bei Dropdown-Komponenten verfügen Optionsfeldgruppen über eine eigene HTML- und CSS-Struktur:

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

#### HTML-Strukturbeispiel

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

+++ CSS-Selektoren für Optionsfeldgruppen

* Targeting des Felds

```CSS
  .radio-group-wrapper {
    border: 1px solid #ccc;
    padding: 10px;
  }
```

Dieser Selektor wendet sich an alle Feldsätze mit dem Funkgruppen-Wrapper der Klasse. Dies wäre nützlich, um allgemeine Stile auf die gesamte Optionsfeldgruppe anzuwenden.

* Optionsfeldbeschriftungen für Targeting

```CSS
.radio-wrapper label {
    font-weight: normal;
    margin-right: 10px;
  }
```

* Targeting aller Optionsfeld-Beschriftungen innerhalb eines bestimmten Felds basierend auf seinem Namen

```CSS
.field-color .radio-wrapper label {
  /* Your styles here */
}
```

+++

### Kontrollkästchen &quot;Gruppen&quot;

+++ HTML-Struktur der Kontrollkästchengruppe

```HTML
<fieldset class="checkbox-group-wrapper field-{Name} field-wrapper" id="{FieldId}" name="{Name}" data-required="{Required}">
   <legend for="{FieldId}" class="field-label">....</legend>
   <% for each radio in Group %>
   <div class="radio-wrapper field-{Name}">
      <input type="checkbox" value="" id="{UniqueId}" data-field-type="checkbox-group" name="{FieldId}">
      <label for="{UniqueId}" class="field-label">...</label>
   </div>
   <% end for %>
</fieldset>
```

#### HTML-Strukturbeispiel

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

+++ CSS-Selektoren für Kontrollkästchengruppen

* Targeting des äußeren Wrappers: Diese Auswahl wählt die äußersten Container von Optionsfeld- und Kontrollkästchengruppen als Ziel aus, sodass Sie allgemeine Stile auf die gesamte Gruppenstruktur anwenden können. Dies ist nützlich zum Festlegen von Abstand, Ausrichtung oder anderen Layout-bezogenen Eigenschaften.


  ```CSS
     /* Targets radio group wrappers */
       .radio-group-wrapper {
       margin-bottom: 20px; /* Adds space between radio groups */  
     }
  
     /* Targets checkbox group wrappers */
     .checkbox-group-wrapper {
     margin-bottom: 20px; /* Adds space between checkbox groups */
     }
  ```


* Bezeichnungen der Zielgruppe: Diese Auswahl wählt das `.field-label`-Element sowohl in Optionsfeld- als auch in Kontrollkästchengruppen-Wrappern als Ziel aus. Dadurch können Sie die Beschriftungen speziell für diese Gruppen formatieren und sie ggf. auffälliger gestalten.

  ```CSS
   .radio-group-wrapper legend,
   .checkbox-group-wrapper legend {
     font-weight: bold; /* Makes the group label bold */
   }
  ```



* Targeting einzelner Eingaben und Beschriftungen: Diese Auswahl bietet eine präzisere Kontrolle über einzelne Optionsfelder, Kontrollkästchen und die zugehörigen Beschriftungen. Sie können diese verwenden, um Größe und Abstand anzupassen oder spezifischere visuelle Stile anzuwenden.

  ```CSS
  /* Styling radio buttons */
   .radio-group-wrapper input[type="radio"] {
     margin-right: 5px; /* Adds space between the input and its label */
   }
  
   /* Styling radio button labels */
   .radio-group-wrapper label {
     font-size: 15px; /* Changes the label font size */
   }
  
  /* Styling checkboxes */
   .checkbox-group-wrapper input[type="checkbox"] {
     margin-right: 5px; /* Adds space between the input and its label */
   }
  
   /* Styling checkbox labels */
   .checkbox-group-wrapper label {
     font-size: 15px; /* Changes the label font size */
   }
  ```




* Anpassen des Erscheinungsbilds von Optionsfeldern und Kontrollkästchen: Diese Methode blendet die Standardeingabe aus und verwendet `:before` und `:after` Pseudoelemente zum Erstellen benutzerdefinierter Visualisierungen, die das Erscheinungsbild basierend auf dem Status &quot;aktiviert&quot;ändern.

  ```CSS
  /* Hide the default radio button or checkbox */
     .radio-group-wrapper input[type="radio"],
     .checkbox-group-wrapper input[type="checkbox"] {
       opacity: 0;
       position: absolute;
     }
  
     /* Create a custom radio button */
     .radio-group-wrapper input[type="radio"] + label::before {
       /* ... styles for custom radio button ... */
     }
  
     .radio-group-wrapper input[type="radio"]:checked + label::before {
       /* ... styles for checked radio button ... */
     }
  
     /* Create a custom checkbox */
     /* Similar styling as above, with adjustments for a square shape  */
     .checkbox-group-wrapper input[type="checkbox"] + label::before {
       /* ... styles for custom checkbox ... */
     }
  
     .checkbox-group-wrapper input[type="checkbox"]:checked + label::before {
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

* Das fieldset -Element dient als Bereichscontainer mit dem Klassenbereichswrapper und zusätzlichen Klassen für die Formatierung basierend auf dem Bereichsnamen (Feldanmeldung).
* Das Legendenelement (<legend>) dient als Bereichstitel mit dem Text &quot;Anmeldeinformationen&quot;und der Klassenfeldbeschriftung. Das Attribut data-visible=&quot;false&quot; kann mit JavaScript verwendet werden, um die Sichtbarkeit des Titels zu steuern.
* Innerhalb des Feldsatzes mehrere .{Type}-wrapper-Elemente (.text-wrapper und .password-wrapper in diesem Fall) stellen einzelne Formularfelder im Bereich dar.
* Jeder Wrapper enthält eine Beschriftung, ein Eingabefeld und eine Beschreibung, die den vorherigen Beispielen ähnelt.

+++

+++ Beispiel-CSS-Selektoren für Bedienfeld-/Container-Komponenten

1. Targeting des Bedienfelds:

```CSS
  /* Target the entire panel container */
  .panel-wrapper {
    /* Add your styles here (e.g., border, padding, background color) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
 }
```

* Die `.panel-wrapper` Auswahl formatiert alle Elemente mit dem Klassenbedienfeld-Wrapper, wodurch ein konsistentes Erscheinungsbild für alle Bedienfelder entsteht.

1. Targeting des Bereichstitels:

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

* Die `.panel-wrapper legend` Auswahl formatiert das Legendenelement im Bereich, wodurch der Titel visuell hervorgehoben wird.


1. Targeting einzelner Felder im Bereich:

```CSS
/* Target all form field wrappers within a panel */
.panel-wrapper .{Type}-wrapper {
  /* Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```

* Die `.panel-wrapper .{Type}-wrapper` Auswahl dient allen Wrappern mit `.{Type}-wrapper` -Klasse innerhalb des Bedienfelds, sodass Sie den Abstand zwischen Formularfeldern formatieren können.

1. Zielgruppenspezifische Felder (optional):

```CSS
  /* Target the username field wrapper */
  .panel-wrapper .text-wrapper.field-username {
    /* Add your styles here (specific to username field) */
  }

  /* Target the password field wrapper */
  .panel-wrapper .password-wrapper.field-password {
    /* Add your styles here (specific to password field) */
  }
```

* Mit diesen optionalen Selektoren können Sie bestimmte Feld-Wrapper innerhalb des Bedienfelds für die eindeutige Formatierung auswählen, z. B. um das Feld &quot;Benutzername&quot;hervorzuheben.

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

Jedes Bedienfeld weist dieselbe Struktur wie das Beispiel eines einzelnen Bedienfelds mit zusätzlichen Attributen auf:

* data-repeatable=&quot;true&quot;: Dieses Attribut gibt an, dass das Bedienfeld dynamisch mit JavaScript oder einem Framework wiederholt werden kann.

* Eindeutige IDs und Namen: Jedes Element im Bereich verfügt über eine eindeutige ID (z. B. name-1, email-1) und ein Attribut name, die auf dem Index des Bedienfelds basieren (z. B. name=&quot;contact&quot;)[0].name&quot;). Dies ermöglicht eine korrekte Datenerfassung, wenn mehrere Bedienfelder gesendet werden.

+++

+++ CSS-Selektoren für ein wiederholbares Bedienfeld

* Targeting aller wiederholbaren Bereiche:

```CSS
  /* Target all panels with the repeatable attribute */
  .panel-wrapper[data-repeatable="true"] {
    /* Add your styles here (e.g., border, margin) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
  }
```

Der Selektor formatiert alle Bedienfelder, die wiederholt werden können, und sorgt so für ein einheitliches Erscheinungsbild.


* Targeting einzelner Felder in einem Bereich:

```CSS
/* Target all form field wrappers within a repeatable panel */
.panel-wrapper[data-repeatable="true"] .{Type}-wrapper {
  /* Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```
Dieser Selektor formatiert alle Feld-Wrapper in einem wiederholbaren Bereich, wobei ein konsistenter Abstand zwischen Feldern beibehalten wird.

* Zielgruppenspezifische Felder (in einem Bereich):

```CSS
/* Target the name field wrapper within the first panel */
.panel-wrapper[data-repeatable="true"][data-index="0"] .text-wrapper.field-name {
  /* Add your styles here (specific to first name field) */
}

/* Target all
```

+++

### Dateianhang

+++ HTML-Struktur für Dateianlagen

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

* Das class -Attribut verwendet den angegebenen Namen für den Dateianhang (claim_form).
* Die ID- und Namensattribute des Eingabeelements stimmen mit dem Dateinamenanlagennamen (claim_form) überein.
* Der Dateilistenabschnitt ist zunächst leer. Es wird dynamisch mit JavaScript ausgefüllt, wenn Dateien hochgeladen werden.

+++

+++ CSS-Selektoren für die Dateianlagenkomponente

* Targeting der gesamten Dateianlagenkomponente:

```CSS
/* Target the entire file attachment component */
.file-wrapper {
  /* Add your styles here (e.g., border, padding) */
  border: 1px solid #ccc;
  padding: 15px;
  border-radius: 4px;
  margin-bottom: 20px;
}
```

Dieser Selektor formatiert die gesamte Dateianlagenkomponente, einschließlich Legende, Drag-Bereich, Eingabefeld und Liste.

* Targeting-spezifische Elemente:

```CSS
/* Target the drag and drop area */
.file-wrapper .file-drag-area {
  /* Add your styles here (e.g., background color, border) */
  background-color: #f0f0f0;
  border: 1px dashed #ddd;
  padding: 10px;
  text-align: center;
}

/* Target the file input element */
.file-wrapper input[type="file"] {
  /* Add your styles here (e.g., hide the default input) */
  display: none;
}

/* Target individual file descriptions within the list (populated dynamically) */
.file-wrapper .files-list .file-description {
  /* Add your styles here (e.g., margin, display) */
  display: flex;
  justify-content: space-between;
  margin-bottom: 5px;
}

/* Target the file name within the description */
.file-wrapper .files-list .file-description .file-description-name {
  /* Add your styles here (e.g., font-weight) */
  font-weight: bold;
}

/* Target the file size within the description */
.file-wrapper .files-list .file-description .file-description-size {
  /* Add your styles here (e.g., font-size) */
  font-size: 0.8em;
}

/* Target the remove button within the description */
.file-wrapper .files-list .file-description .file-description-remove {
  /* Add your styles here (e.g., background color, hover effect) */
  background-color: transparent;
  border: none;
  cursor: pointer;
}
```

Mit diesen Selektoren können Sie verschiedene Teile der Dateianlagenkomponente einzeln formatieren. Sie können die Stile entsprechend Ihren Designvoreinstellungen anpassen.

+++


## Formatieren von Komponenten

Sie können Formularfelder anhand ihres spezifischen Typs (`{Type}-wrapper`) oder einzelnen Namen (`field-{Name}`). Dies ermöglicht eine präzisere Steuerung und Anpassung des Erscheinungsbilds Ihres Formulars.

### Formatierung basierend auf Feldtyp

Sie können CSS-Selektoren verwenden, um bestimmte Feldtypen gezielt anzusprechen und Stile konsistent anzuwenden.

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

* Jedes Feld wird in ein `div`-Element mit mehreren Klassen eingebettet:
   * `{Type}-wrapper`: Identifiziert den Feldtyp. Beispiel: `form-text-wrapper`, `form-number-wrapper`, `form-email-wrapper`.
   * `field-{Name}`: Identifiziert das Feld anhand seines Namens. Beispiel: `form-name`, `form-age`, `form-email`.
   * `field-wrapper`: Eine allgemeine Klasse für alle Feld-Wrapper.
* Das Attribut `data-required` gibt an, ob das Feld erforderlich oder optional ist.
* Jedes Feld verfügt über eine entsprechende Beschriftung, ein Eingabeelement und potenzielle zusätzliche Elemente wie Platzhalter und Beschreibungen.


+++


+++ Beispiel-CSS-Selektoren

```CSS
/* Target all text input fields */
.text-wrapper input {
  /* Add your styles here */
}

/* Target all number input fields */
.number-wrapper input {
  /* Add your styles here */
  letter-spacing: 2px; /* Example for adding letter spacing to all number fields */
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

+++ Beispiel-CSS-Selektor

```CSS
.field-otp input {
   letter-spacing: 2px
}
```



Diese CSS-Datei wählt alle Eingabeelemente als Ziel aus, die sich in einem Element mit der Klasse `field-otp` befinden. Die HTML-Struktur Ihres Formulars entspricht den Konventionen des Bausteins Adaptive Forms . Dies bedeutet, dass ein Container mit der Klasse &quot;field-otp&quot;markiert ist, der das Feld mit dem Namen &quot;otp&quot;enthält.

+++

## Siehe auch

{{see-more-forms-eds}}