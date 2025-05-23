---
title: Anpassen von Designs und Stilen für Edge Delivery Services für AEM Forms
description: Anpassen von Designs und Stilen für Edge Delivery Services für AEM Forms
feature: Edge Delivery Services
exl-id: c214711c-979b-4833-9541-8e35b2aa8e09
role: Admin, Architect, Developer
source-git-commit: babddee34b486960536ce7075684bbe660b6e120
workflow-type: tm+mt
source-wordcount: '1909'
ht-degree: 72%

---


# Anpassen des Erscheinungsbilds Ihrer Formulare

Formulare sind von entscheidender Bedeutung für die Benutzerinteraktion auf Websites, da sie die Eingabe von Daten ermöglichen. Sie können Cascading Style Sheets (CSS) verwenden, um Formularfelder zu formatieren, die visuelle Darstellung Ihrer Formulare zu verbessern und das Benutzererlebnis zu verbessern.

Der Baustein „Adaptives Formular“ sorgt für eine einheitliche Struktur für alle Formularfelder. Diese konsistente Struktur erleichtert die Entwicklung von CSS-Selektoren zur Auswahl und Gestaltung von Formularfeldern anhand von Feldtypen und Feldnamen.

In diesem Dokument wird die HTML-Struktur für verschiedene Formularkomponenten erläutert und Ihnen dabei geholfen, ein Verständnis dafür aufzubauen, wie Sie CSS-Selektoren für verschiedene Formularfelder erstellen, um Formularfelder eines adaptiven Forms-Blocks zu gestalten.

Am Ende des Artikels werden Sie:

* Machen Sie sich mit der Struktur der im adaptiven Forms-Block enthaltenen Standard-CSS-Datei vertraut
* Machen Sie sich mit der HTML-Struktur der Formularkomponenten vertraut, die vom adaptiven Forms-Block bereitgestellt werden, einschließlich allgemeiner Komponenten und spezifischer Komponenten wie Dropdown-Listen, Optionsfeldgruppen und Kontrollkästchengruppen
* Erfahren Sie, wie Sie Formularfelder mithilfe von CSS-Selektoren basierend auf Feldtypen und Feldnamen formatieren, um eine konsistente oder eindeutige Formatierung auf der Grundlage von Anforderungen zu ermöglichen


## Grundlagen zu Formularfeldtypen

Bevor wir uns mit der Formatierung befassen, sollten wir die allgemeinen [Formularfeldtypen](/help/edge/docs/forms/form-components.md) besprechen, die vom adaptiven Formularbaustein unterstützt werden:

* Eingabefelder: Dazu gehören Texteingaben, E-Mail-Eingaben, Kennworteingaben und mehr
* Kontrollkästchen-Gruppen: Dient zur Auswahl mehrerer Optionen.
* Optionsfeldgruppen: Dient zur Auswahl nur einer Option aus einer Gruppe
* Dropdown-Listen: werden auch als Auswahlfelder bezeichnet und zur Auswahl einer Option aus einer Liste verwendet
* Bedienfelder/Container: Dient zur Gruppierung verwandter Formularelemente

## Standard-Formatierungsgrundsätze

Das Verstehen [grundlegender CSS-Konzepte](https://www.w3schools.com/css/css_intro.asp) vor der Formatierung bestimmter Formularfelder ist von entscheidender Bedeutung:

* [Auswahlen](https://www.w3schools.com/css/css_selectors.asp): Mit einer CSS-Auswahl können Sie bestimmte HTML-Elemente für die Formatierung auswählen. Sie können Element-, Klassen- oder ID-Selektoren verwenden
* [Eigenschaften](https://www.w3schools.com/css/css_syntax.asp): CSS-Eigenschaften definieren das visuelle Erscheinungsbild von Elementen. Zu den gebräuchlichen Eigenschaften für die Formatierung von Formularfeldern gehören Farbe, Hintergrundfarbe, Rahmen, Abstand, Rand und mehr
* [Box-Modell](https://www.w3schools.com/css/css_boxmodel.asp): Das CSS-Box-Modell beschreibt die Struktur von HTML-Elementen als von Abstand, Rahmen und Rändern umgebenen Inhaltsbereich
* Flexbox/Grid: CSS [Flexbox](https://www.w3schools.com/css/css3_flexbox.asp)- und [Grid-Layouts](https://www.w3schools.com/css/css_grid.asp) sind leistungsstarke Tools zum Erstellen responsiver und flexibler Designs

## Formatieren eines Formulars für den adaptiven Formularbaustein

Der adaptive Formularbaustein bietet eine standardisierte HTML-Struktur, die die Auswahl und Formatierung von Formularkomponenten vereinfacht:

* **Standardstile aktualisieren**: Sie können die Standardstile eines Formulars ändern, indem Sie die `/blocks/form/form.css` Datei bearbeiten. Diese Datei bietet eine umfassende Formatierung für ein Formular, das mehrstufige Assistentenformulare unterstützt. Der Schwerpunkt liegt auf der Verwendung benutzerdefinierter CSS-Variablen für eine einfache Anpassung, Wartung und einheitliche Formatierung in allen Formularen. Anweisungen zum Hinzufügen des adaptiven Formularbausteins zu Ihrem Projekt finden Sie unter [Erstellen eines Formulars](/help/edge/docs/forms/create-forms.md).

* **Anpassung**: Verwenden Sie die `forms.css` als Grundlage und passen Sie sie an, um das Erscheinungsbild Ihrer Formularkomponenten zu ändern und sie visuell ansprechend und benutzerfreundlich zu gestalten. Die Dateistruktur fördert die Organisation und verwaltet Stile für Formulare, wodurch konsistente Designs auf Ihrer Website gefördert werden.

## Aufschlüsselung der forms.css-Struktur

* **Globale Variablen:** Diese Variablen (`--variable-name`) werden auf der `:root`-Ebene definiert und speichern Werte, die im gesamten Stylesheet verwendet werden, um die Konsistenz und einfache Aktualisierung zu gewährleisten. Diese Variablen definieren Farben, Schriftgrößen, Abstände und andere Eigenschaften. Sie können Ihre eigenen globalen Variablen deklarieren oder vorhandene ändern, um den Stil des Formulars zu ändern.

* **Universelle Auswahlstile:** Die `*`-Auswahl stimmt mit jedem Element im Formular überein, wodurch sichergestellt wird, dass Stile standardmäßig auf alle Komponenten angewendet werden, einschließlich der Festlegung der Eigenschaft `box-sizing` auf `border-box`.

* **Formatierung von Formularen:** Dieser Abschnitt konzentriert sich auf die Formatierung von Formularkomponenten mithilfe der Auswahlen für das Targeting bestimmter HTML-Elemente. Sie definiert Stile für Eingabefelder, Textbereiche, Kontrollkästchen, Optionsfelder, Dateieingaben, Formularbeschriftungen und Beschreibungen.

* **Formatierung des Assistenten (falls zutreffend):** Dieser Abschnitt dient der Formatierung des Assistenten-Layouts, eines aus mehreren Schritten bestehenden Formulars, in dem jeder Schritt einzeln angezeigt wird. Sie definiert Stile für den Assistenten-Container, Feldsätze, Legenden, Navigationsschaltflächen und responsive Layouts.

* **Medienabfragen:** Diese bieten Stile für unterschiedliche Bildschirmgrößen und passen das Layout und die Formatierung entsprechend an.

* **Verschiedene Stile:** In diesem Abschnitt werden Stile für Erfolgs- oder Fehlermeldungen, Bereiche für Datei-Uploads und andere Elemente behandelt, auf die Sie in einem Formular stoßen können.


## Komponentenstruktur

Der adaptive Formularbaustein bietet eine konsistente HTML-Struktur für verschiedene Formularelemente, wodurch Formatierungen und die Verwaltung vereinfacht werden. Sie können die Komponenten mithilfe von CSS für Formatierungszwecke bearbeiten.

### Allgemeine Komponenten (außer Dropdown-Listen, Optionsfeldgruppen und Kontrollkästchengruppen):

Alle Formularfelder mit Ausnahme von Dropdown-Menüs, Optionsfeldgruppen und Kontrollkästchen-Gruppen haben die folgende HTML-Struktur:

+++ HTML-Struktur der allgemeinen Komponenten

```HTML
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">First Name</label>
   <input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id="{FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be a minimum of 3 characters and a maximum of 10 characters.
   </div>
</div>
```

* Klassen: Das div-Element verfügt über mehrere Klassen, die auf bestimmte Elemente und die Formatierung abzielen. Sie benötigen die Klassen `{Type}-wrapper` oder `field-{Name}` zum Entwickeln einer CSS-Auswahl, um ein Formularfeld zu formatieren:
   * {Type}: Identifiziert die Komponente nach Feldtyp. Beispiel: Text (Text-Wrapper), Zahl (Zahl-Wrapper), Datum (Datum-Wrapper)
   * {Name}: Identifiziert die Komponente anhand des Namens. Der Name des Felds darf nur alphanumerische Zeichen enthalten. Mehrere aufeinander folgende Bindestriche im Namen werden durch einen einzelnen `(-)` ersetzt, und Anfangs- und Endstriche in einem Feldnamen werden entfernt. Beispiel: Vorname (field-first-name field-wrapper)
   * {FieldId}: Dies ist eine eindeutige Kennung für das Feld, die automatisch generiert wird
   * {Required}: Ein boolescher Wert, der angibt, ob das Feld erforderlich ist
* Beschriftung: Das `label`-Element liefert beschreibenden Text für das Feld und verknüpft es mit dem Eingabeelement unter Verwendung des `for`-Attributs
* Eingabe: Das `input`-Element definiert den einzugebenden Datentyp. Beispiel: Text, Zahl, E-Mail
* Beschreibung (Optional): Das `div` mit der Klasse `field-description` bietet zusätzliche Informationen oder Anweisungen für den Benutzer

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
/* Target all input fields within any .{Type}-wrapper */
.{Type}-wrapper {
  /* Add your styles here */
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}

/* Target all input fields within any .{Type}-wrapper */
.{Type}-wrapper input {
  /* Add your styles here */
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}

/* Target any element with the class field-{Name} */
.field-{Name} {
  /* Add your styles here */
  /* This could be used for styles specific to all elements with field-{Name} class, not just inputs */
}
```

* `.{Type}-wrapper`: Wählt das äußere `div`-Element basierend auf dem Feldtyp als Ziel aus. Beispielsweise ist `.text-wrapper` auf alle Textfelder ausgerichtet
* `.field-{Name}`: Wählt das Element weiter auf Grundlage des spezifischen Feldnamens aus. Beispielsweise wählt `.field-first-name` das Textfeld „Vorname“ als Ziel aus. Diese Auswahl kann für das Abzielen auf Elemente mit der Klasse „field-{Name}“ verwendet werden. Sie müssen jedoch vorsichtig sein. In diesem speziellen Fall wäre es für die Formatierung von Eingabefeldern nicht hilfreich, da nicht nur die Eingabe selbst, sondern auch die Titel- und Beschreibungselemente ausgewählt würden. Es wird empfohlen, spezifischere Selektoren zu verwenden, wie Sie sie zum Targeting von Texteingabefeldern haben (.text-wrapper input)

**Beispiel einer CSS-Auswahl für allgemeine Komponenten**

```CSS
/* Target all text input fields */
.text-wrapper input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
}

/* Target all fields with name first-name */
.field-first-name input {
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
<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   <label for="{FieldId}" class="field-label">Country</label>
   <select id="{FieldId}" name="{Name}"><option></option><option></option></select>
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Please select your country from the list.
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

+++ CSS-Selektoren für Dropdown-Komponente

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
}
```

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

+++ CSS-Auswahlen für Optionsfeldgruppen

* Abzielen auf den Feldsatz

```CSS
  .radio-group-wrapper {
    border: 1px solid #ccc;
    padding: 10px;
  }
```

Dieser Selektor wählt alle Feldsätze mit dem Klassen-Optionsfeldgruppen-Wrapper aus.  Dies wäre nützlich, um allgemeine Stile auf die gesamte Optionsfeldgruppe anzuwenden.

* Targeting von Optionsfeldbezeichnungen

```CSS
.radio-wrapper label {
    font-weight: normal;
    margin-right: 10px;
  }
```

* Targeting aller Optionsfeldbezeichnungen innerhalb eines bestimmten Feldsatzes basierend auf seinem Namen

```CSS
.field-color .radio-wrapper label {
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

+++ CSS-Auswahl für Kontrollkästchengruppen

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




* Anpassen des Erscheinungsbilds von Optionsfeldern und Kontrollkästchen: Diese Methode blendet die Standardeingabe aus und verwendet die Pseudo-Elemente `:before` und `:after`, um benutzerdefinierte Visualisierungen zu erstellen, die das Erscheinungsbild basierend auf dem Status „aktiviert“ ändern.

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

* Das fieldset-Element dient als Bedienfeld-Container mit dem Klassen-Bedienfeld-Wrapper und zusätzlichen Klassen zur Gestaltung basierend auf dem Bedienfeldnamen (Feldanmeldung).
* Das legend-Element (&lt;legend>) dient als Bedienfeldtitel mit dem Text „Anmeldeinformationen“ und der Klassenfeldbezeichnung. Das data-visible=&quot;false&quot;-Attribut kann mit JavaScript verwendet werden, um die Sichtbarkeit des Titels zu steuern.
* In diesem Feldsatz stehen mehrere .{Type}-Wrapper-Elemente (in diesem Fall „.text-wrapper“ und „.password-wrapper“x) für einzelne Formularfelder im Bedienfeld.
* Jeder Wrapper enthält eine Bezeichnung, ein Eingabefeld und eine Beschreibung, ähnlich wie bei den vorherigen Beispielen.

+++

+++ Beispiel zur CSS-Auswahl für Bedienfeld-/Container-Komponenten

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

* Die `.panel-wrapper`-Auswahl gestaltet alle Elemente mit dem Klassenbedienfeld-Wrapper, wodurch ein einheitlicher Look für alle Bedienfelder entsteht.

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

* Die `.panel-wrapper legend`-Auswahl gestaltet das legend-Element im Bedienfeld, sodass der Titel optisch hervorgehoben wird.


1. Targeting einzelner Felder im Bedienfeld:

```CSS
/* Target all form field wrappers within a panel */
.panel-wrapper .{Type}-wrapper {
  /* Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```

* Die Auswahl `.panel-wrapper .{Type}-wrapper` wählt alle Wrapper mit der Klasse `.{Type}-wrapper` innerhalb des Bedienfelds als Ziel aus, sodass Sie den Abstand zwischen Formularfeldern festlegen können.

1. Targeting bestimmter Felder (optional):

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

* Mit diesen optionalen Auswahlen können Sie bestimmte Feld-Wrapper innerhalb des Bedienfelds als Ziel auswählen, um einen eindeutigen Stil zu ermöglichen, z. B. zur Hervorhebung des Felds „Benutzername“.

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

* data-repeatable=&quot;true&quot;: Dieses Attribut gibt an, dass das Bedienfeld dynamisch mit JavaScript oder einem Framework wiederholt werden kann.

* Eindeutige IDs und Namen: Jedes Element im Bedienfeld verfügt über eine eindeutige ID (z. B. name-1, email-1) und ein eindeutiges name-Attribut, das auf dem Index des Bedienfelds basiert (z. B. nname=&quot;contacts[0].name&quot;). Dies ermöglicht eine korrekte Datenerfassung bei der Übermittlung mehrerer Bedienfelder.

+++

+++ CSS-Auswahl für ein wiederholbares Bedienfeld

* Targeting aller wiederholbaren Bedienfelder:

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

Die Auswahl gestaltet alle wiederholbaren Bedienfelder und sorgt so für ein einheitliches Look-and-Feel.


* Targeting einzelner Felder in einem Bedienfeld:

```CSS
/* Target all form field wrappers within a repeatable panel */
.panel-wrapper[data-repeatable="true"] .{Type}-wrapper {
  /* Add your styles here (e.g., margin) */
  margin-bottom: 10px;
}
```

Diese Auswahl gestaltet alle Feld-Wrapper in einem wiederholbaren Bedienfeld, wobei ein konsistenter Abstand zwischen Feldern beibehalten wird.

* Targeting bestimmter Felder (in einem Bedienfeld):

```CSS
/* Target the name field wrapper within the first panel */
.panel-wrapper[data-repeatable="true"][data-index="0"] .text-wrapper.field-name {
  /* Add your styles here (specific to first name field) */
}

/* Target all
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

* Das class-Attribut verwendet den angegebenen Namen für den Dateianhang (claim_form).
* Die id- und name-Attribute des Eingabeelements stimmen mit dem Dateianhangsnamen (claim_form) überein.
* Der Abschnitt „files-list“ ist zunächst leer. Er wird dynamisch mit JavaScript aufgefüllt, wenn Dateien hochgeladen werden.

+++

+++ CSS-Auswahl für die Dateianhangskomponente

* Targeting der gesamten Dateianhangskomponente:

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

Diese Auswahl gestaltet die gesamte Dateianhangskomponente, einschließlich Legende, Ziehbereich, Eingabefeld und Liste.

* Targeting bestimmter Elemente:

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

* Jedes Feld wird in ein `div`-Element mit mehreren Klassen eingebettet:
   * `{Type}-wrapper`: Identifiziert den Feldtyp. Beispiel: `form-text-wrapper`, `form-number-wrapper`, `form-email-wrapper`.
   * `field-{Name}`: Identifiziert das Feld anhand seines Namens. Beispiel: `form-name`, `form-age`, `form-email`.
   * `field-wrapper`: Eine allgemeine Klasse für alle Feld-Wrapper.
* Das Attribut `data-required` gibt an, ob das Feld erforderlich oder optional ist.
* Jedes Feld verfügt über eine entsprechende Beschriftung, ein Eingabeelement und potenzielle zusätzliche Elemente wie Platzhalter und Beschreibungen.


+++


+++ Beispiel einer CSS-Auswahl

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

+++ Beispiel einer CSS-Auswahl

```CSS
.field-otp input {
   letter-spacing: 2px
}
```



Diese CSS-Datei wählt alle Eingabeelemente als Ziel aus, die sich in einem Element mit der Klasse `field-otp` befinden. Die HTML-Struktur Ihres Formulars entspricht den Konventionen des adaptiven Formularblocks. Dies bedeutet, dass ein mit der Klasse „field-otp“ markierter Container das Feld mit dem Namen „otp“ enthält.

+++

## Siehe auch

{{see-more-forms-eds}}