---
title: Anpassen des Designs und Stils für Edge Delivery Services für AEM Forms
description: Passen Sie effektiv das Design und den Stil für AEM Forms-Assets an, die über Edge Delivery Services bereitgestellt werden, und sorgen Sie so für ein kohärentes Benutzererlebnis mit Branding.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: ac780399-34fe-457d-aaf4-b675656c024d
source-git-commit: 9127c58a72dc4942312907f9e8f0cdcc8de9aa4b
workflow-type: tm+mt
source-wordcount: '1876'
ht-degree: 98%

---

# Anpassen des Erscheinungsbilds Ihrer Formulare

<span class="preview"> Diese Funktion ist über das Early-Access-Programm verfügbar. Um den Zugriff anzufordern, senden Sie eine E-Mail mit dem Namen Ihrer GitHub-Organisation und dem Repository-Namen von Ihrer offiziellen Adresse an <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a> . Wenn die Repository-URL beispielsweise https://github.com/adobe/abc lautet, lautet der Name der Organisation „adobe“ und der Name des Repositorys „abc“.</span>


Formulare sind von entscheidender Bedeutung für die Benutzerinteraktion auf Websites, da sie die Eingabe von Daten ermöglichen. Sie können Cascading Style Sheets (CSS) verwenden, um Felder eines Formulars zu formatieren und so die visuelle Darstellung Ihrer Formulare und das Anwendererlebnis zu verbessern.

Der Baustein „Adaptives Formular“ sorgt für eine einheitliche Struktur für alle Formularfelder. Die konsistente Struktur erleichtert die Entwicklung der CSS-Auswahl zur Auswahl und Formatierung von Formularfeldern basierend auf Feldtyp und Feldnamen.

In diesem Dokument wird die HTML-Struktur für verschiedene Formularkomponenten beschrieben. Sie erhalten ein Verständnis dafür, wie Sie die CSS-Auswahlen für verschiedene Formularfelder erstellen, um Formularfelder in einem adaptiven Formularbaustein zu formatieren.

Am Ende des Artikels werden Sie Folgendes erreicht haben:

* Sie gewinnen ein Verständnis der Struktur der standardmäßigen CSS-Datei, die im adaptiven Formularbaustein enthalten ist.
* Sie gewinnen ein Verständnis der HTML-Struktur von Formularkomponenten, die vom adaptiven Formularbaustein bereitgestellt werden, einschließlich allgemeiner Komponenten und spezifischer Komponenten wie Dropdown-Listen, Optionsfeld- und Kontrollkästchengruppen.
* Sie lernen, wie Sie Formularfelder mithilfe der CSS-Auswahlen basierend auf dem Feldtyp und den Feldnamen formatieren, was eine konsistente oder eindeutige Formatierung basierend auf Anforderungen ermöglicht.

## Grundlagen zu Formularfeldtypen

Bevor wir uns mit der Formatierung befassen, sollten wir die allgemeinen [Formularfeldtypen](/help/edge/docs/forms/universal-editor/create-custom-component.md#supported-fieldtypes) besprechen, die vom adaptiven Formularbaustein unterstützt werden:

* Eingabefelder: Dazu gehören Texteingaben, E-Mail-Eingaben, Kennworteingaben usw.
* Kontrollkästchengruppen: Dienen zum Auswählen mehrerer Optionen.
* Optionsfeldgruppen: Dienen zum Auswählen einer einzelnen Option aus einer Gruppe.
* Dropdown-Listen: Werden auch als Auswahlfelder bezeichnet und dienen zum Auswählen einer Option aus einer Liste.
* Bedienfelder/Container: Dienen zum Gruppieren zugehöriger Formularelemente.

## Standard-Formatierungsgrundsätze

Das Verstehen [grundlegender CSS-Konzepte](https://www.w3schools.com/css/css_intro.asp) vor der Formatierung bestimmter Formularfelder ist von entscheidender Bedeutung:

* [Auswahlen](https://www.w3schools.com/css/css_selectors.asp): Mit einer CSS-Auswahl können Sie bestimmte HTML-Elemente für die Formatierung auswählen. Sie können die Elementauswahl, Klassenauswahl oder ID-Auswahl verwenden.
* [Eigenschaften](https://www.w3schools.com/css/css_syntax.asp): CSS-Eigenschaften definieren das visuelle Erscheinungsbild von Elementen. Zu den allgemeinen Eigenschaften für die Formatierung von Formularfeldern gehören u. a. Farbe, Hintergrundfarbe, Rahmen, Abstand und Rand.
* [Box-Modell](https://www.w3schools.com/css/css_boxmodel.asp): Das CSS-Box-Modell beschreibt die Struktur von HTML-Elementen als Inhaltsbereich, der von Abstand, Rahmen und Rändern umgeben ist.
* Flexbox/Raster: CSS [Flexbox](https://www.w3schools.com/css/css3_flexbox.asp)- und [Raster-Layouts](https://www.w3schools.com/css/css_grid.asp) sind leistungsstarke Tools zum Erstellen responsiver und flexibler Designs.


## Formatieren eines Formulars für den adaptiven Formularbaustein

Der adaptive Formularbaustein bietet eine standardisierte HTML-Struktur, die die Auswahl und Formatierung von Formularkomponenten vereinfacht:

* **Aktualisieren von Standardstilen**: Sie können die Standardstile eines Formulars ändern, indem Sie die `/blocks/form/form.css file` bearbeiten. Diese Datei bietet eine umfassende Formatierung für ein Formular, das mehrstufige Assistentenformulare unterstützt. Der Schwerpunkt liegt auf der Verwendung benutzerdefinierter CSS-Variablen für eine einfache Anpassung, Wartung und einheitliche Formatierung in allen Formularen.

* **CSS-Stile für Formulare**: Um sicherzustellen, dass Ihre Stile richtig angewendet werden, schließen Sie Ihren formularspezifischen CSS-Stil in die Auswahl `main .form form` ein. Dadurch wird sichergestellt, dass Ihre Stile nur auf die Formularelemente innerhalb des Hauptinhaltsbereichs angewendet werden, wodurch Konflikte mit anderen Teilen der Website vermieden werden.
Zum Beispiel:

  ```css
    main .form form input {
        /* Add styles specific to input fields inside the form */
    }
  
    main .form form button {
        /* Add styles specific to buttons inside the form */
    }
  
    main .form form label {
        /* Add styles specific to labels inside the form */
    }
  
## Komponentenstruktur

Der adaptive Formularbaustein bietet eine konsistente HTML-Struktur für verschiedene Formularelemente, wodurch Formatierungen und die Verwaltung vereinfacht werden. Sie können die Komponenten mithilfe von CSS für Formatierungszwecke bearbeiten.

### Allgemeine Komponenten (außer Dropdown-Listen, Optionsfeldgruppen und Kontrollkästchengruppen):

Alle Formularfelder mit Ausnahme von Dropdown-Listen, Optionsfeldgruppen und Kontrollkästchengruppen haben die folgende HTML-Struktur:

+++ HTML-Struktur der allgemeinen Komponenten

```HTML

  <div class="{Type}-wrapper field-{Name}   field-wrapper" data-required={Required}>
     &lt;label for="{FieldId}" class="field-label">First   Name&lt;/label>
     &lt;input type="{Type}" placeholder="{Placeholder}"   maxlength="{Max}" id={FieldId}" name="{Name}"   aria-describedby="{FieldId}-description">
     <div class="field-description" aria-live="polite"  id="{FieldId}-description">
      Hint - First name should be minimum 3 characters  and a maximum of 10 characters.
     </div>
  </div>

```

* Klassen: Das div-Element verfügt über mehrere Klassen, die auf bestimmte Elemente und die Formatierung abzielen. Sie benötigen die Klassen `{Type}-wrapper` oder `field-{Name}` zum Entwickeln einer CSS-Auswahl, um ein Formularfeld zu formatieren:
* {Type}: Identifiziert die Komponente nach Feldtyp. Zum Beispiel: text (text-wrapper), number (number-wrapper), date (date-wrapper).
* {Name}: Identifiziert die Komponente anhand des Namens. Der Name des Felds darf nur alphanumerische Zeichen enthalten. Mehrere aufeinander folgende Gedankenstriche im Namen werden durch einen einzigen Bindestrich ersetzt `(-)`, und die Start- und Endabstände in einem Feldnamen werden entfernt. Zum Beispiel: first-name (field-first-name field-wrapper).
* {FieldId}: Eine eindeutige Kennung für das Feld, die automatisch generiert wird.
* {Required}: Ein boolescher Wert, der angibt, ob das Feld erforderlich ist.
* Titel: Das Element `label` liefert einen beschreibenden Text für das Feld und ordnet ihn dem Eingabeelement mithilfe des `for`-Attributs zu.
* Eingabe: Das `input`-Element definiert den einzugebenden Datentyp. Zum Beispiel : text, number, email.
* Beschreibung (optional): `div` mit der Klasse `field-description` stellt zusätzliche Informationen oder Anweisungen für Benutzende bereit.

**Beispiel einer HTML-Struktur**

```HTML

<div class="text-wrapper field-first-name field-wrapper" data-required="true">
  &lt;label for="firstName" class="field-label">First Name&lt;/label>
  &lt;input type="text" placeholder="Enter your first name" maxlength="50" id="firstName" name="firstName" aria-describedby="firstName-description">
  <div class="field-description" aria-live="polite" id="firstName-description">
    Please enter your legal first name.
  </div>
</div>

```

+++

+++ CSS-Auswahl für allgemeine Komponenten

```CSS

  
  /* Target all input fields within any .{Type}-wrapper  */
  main .form form .{Type}-wrapper  &lbrace;
    /* Add your styles here */
    border: 1px solid #ccc;
    padding: 8px;
    border-radius: 4px;
  &rbrace;
  
  /* Target all input fields within any .{Type}-wrapper  */
  main .form form .{Type}-wrapper input &lbrace;
    /* Add your styles here */
    border: 1px solid #ccc;
    padding: 8px;
    border-radius: 4px;
  &rbrace;
  
  /* Target any element with the class field-{Name}  */
  main .form form .field-{Name} &lbrace;
    /* Add your styles here */
    /* This could be used for styles specific to all elements with   field-{Name} class, not just inputs */
  &rbrace;
  
```
* `.{Type}-wrapper`: Wählt das äußere `div`-Element basierend auf dem Feldtyp als Ziel aus. Zum Beispiel wählt `.text-wrapper` alle Textfelder als Ziel aus.
* `.field-{Name}`: Wählt das Element weiter auf Grundlage des spezifischen Feldnamens aus. Beispielsweise wählt `.field-first-name` das Textfeld „Vorname“ als Ziel aus. Diese Auswahl kann für das Abzielen auf Elemente mit der Klasse „field-{Name}“ verwendet werden. Sie müssen jedoch vorsichtig sein. In diesem speziellen Fall wäre es für die Formatierung von Eingabefeldern nicht hilfreich, da nicht nur die Eingabe selbst, sondern auch die Titel- und Beschreibungselemente ausgewählt würden. Es empfiehlt sich, eine spezifischere Auswahl zu verwenden, z. B. eine, die für das Abzielen auf Texteingabefelder verfügbar ist (.text-wrapper-Eingabe).

**Beispiel einer CSS-Auswahl für allgemeine Komponenten**

```CSS

/*Target all text input fields */
main .form form .text-wrapper input &lbrace;
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
  color: red;
&rbrace;

/*Target all fields with name first-name*/
main .form form .field-first-name input &lbrace;
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 4px;
&rbrace;

```

+++

### Dropdown-Komponente

Bei Dropdown-Menüs wird das `select`-Element anstelle des `input`-Elements verwendet:

+++ HTML-Struktur der Dropdown-Komponente

```HTML

<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   &lt;label for="{FieldId}" class="field-label">First Name&lt;/label>
   &lt;input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
   </div>
</div>

```

**Beispiel einer HTML-Struktur**

```HTML

<div class="drop-down-wrapper field-country field-wrapper" data-required="true">
  &lt;label for="country" class="field-label">Country&lt;/label>
  &lt;select id="country" name="country">
    &lt;option value="">Select Country&lt;/option>
    &lt;option value="US">United States&lt;/option>
    &lt;option value="CA">Canada&lt;/option>
  &lt;/select>
  <div class="field-description" aria-live="polite" id="country-description">
    Please select your country of residence.
  </div>
</div>

```

+++

+++ CSS-Auswahlen für Dropdown-Komponenten

Im folgenden CSS sind einige Beispiele von CSS-Auswahlen für Dropdown-Komponenten aufgeführt.

```CSS

/* Target the outer wrapper */
main .form form .drop-down-wrapper &lbrace;
  /* Add your styles here */
  display: flex;
  flex-direction: column;
  margin-bottom: 15px;
&rbrace;

/* Style the label */
main .form form .drop-down-wrapper .field-label &lbrace;
  margin-bottom: 5px;
  font-weight: bold;
&rbrace;

```
* Auswählen des Wrappers als Ziel: Die erste Auswahl (`.drop-down-wrapper`) wählt das äußere Wrapper-Element als Ziel aus, wodurch sichergestellt wird, dass die Stile auf die gesamte Dropdown-Komponente angewendet werden.
* Flexbox-Layout: Flexbox ordnet Beschriftung, Dropdown-Liste und Beschreibung vertikal für ein sauberes Layout an.
* Beschriftungsformatierung: Die Beschriftung zeichnet sich durch eine fette Schriftstärke und einen leichten Rand aus.
* Formatierung der Dropdown-Liste: Das ausgewählte `select`-Element erhält einen Rahmen, einen Abstand und gerundete Ecken für einen hochwertigen Look.
* Hintergrundfarbe: Für visuelle Harmonie wird eine konsistente Hintergrundfarbe festgelegt.
* Pfeilanpassung: Optionale Stile blenden den standardmäßigen Dropdown-Pfeil aus und erstellen einen benutzerdefinierten Pfeil mit einem Unicode-Zeichen und einer Positionierung.

+++

---

### Optionsfeldgruppen

Ähnlich wie bei Dropdown-Komponenten haben Optionsfeldgruppen ihre eigene HTML- und CSS-Struktur:

+++ HTML-Struktur der Optionsfeldgruppe

```HTML

&lt;fieldset class="radio-group-wrapper field-{Name} field-wrapper" id="{FieldId}" name="{Name}" data-required="{Required}">
   &lt;legend for="{FieldId}" class="field-label">....&lt;/legend>
   <% for each radio in Group %>
   <div class="radio-wrapper field-{Name}">
      &lt;input type="radio" value="" id="{UniqueId}" data-field-type="radio-group" name="{FieldId}">
      &lt;label for="{UniqueId}" class="field-label">...&lt;/label>
   </div>
   <% end for %>
&lt;/fieldset>

```

**Beispiel einer HTML-Struktur**

```HTML

&lt;fieldset class="radio-group-wrapper field-color field-wrapper" id="color_preference" name="color_preference" data-required="true">
  &lt;legend for="color_preference" class="field-label">Favorite Color:&lt;/legend>
  <% for each radio in Group %>
    <div class="radio-wrapper field-color">
      &lt;input type="radio" value="red" id="color_red" data-field-type="radio-group" name="color_preference">
      &lt;label for="color_red" class="field-label">Red&lt;/label>
    </div>
    <div class="radio-wrapper field-color">
      &lt;input type="radio" value="green" id="color_green" data-field-type="radio-group" name="color_preference">
      &lt;label for="color_green" class="field-label">Green&lt;/label>
    </div>
    <div class="radio-wrapper field-color">
      &lt;input type="radio" value="blue" id="color_blue" data-field-type="radio-group" name="color_preference">
      &lt;label for="color_blue" class="field-label">Blue&lt;/label>
    </div>
  <% end for %>
&lt;/fieldset>

```

+++

+++ CSS-Auswahlen für Optionsfeldgruppen

* Abzielen auf den Feldsatz

```CSS

  main .form form .radio-group-wrapper &lbrace;
    border: 1px solid #ccc;
    padding: 10px;
  &rbrace;

```
Dieser Selektor wählt alle Feldsätze mit dem Klassen-Optionsfeldgruppen-Wrapper aus.  Dies wäre nützlich, um allgemeine Stile auf die gesamte Optionsfeldgruppe anzuwenden.

* Targeting von Optionsfeldbezeichnungen

```CSS

main .form form .radio-wrapper label &lbrace;
    font-weight: normal;
    margin-right: 10px;
  &rbrace;

```

* Targeting aller Optionsfeldbezeichnungen innerhalb eines bestimmten Feldsatzes basierend auf seinem Namen

```CSS

main .form form .field-color .radio-wrapper label &lbrace;
  /* Your styles here */
&rbrace;

```

+++

### Kontrollkästchengruppe

+++ HTML-Struktur der Kontrollkästchengruppe

```HTML

&lt;fieldset class="checkbox-group-wrapper field-{Name} field-wrapper" id="{FieldId}" name="{Name}" data-required="{Required}">
   &lt;legend for="{FieldId}" class="field-label">....&lt;/legend>
   <% for each radio in Group %>
   <div class="radio-wrapper field-{Name}">
      &lt;input type="checkbox" value="" id="{UniqueId}" data-field-type="checkbox-group" name="{FieldId}">
      &lt;label for="{UniqueId}" class="field-label">...&lt;/label>
   </div>
   <% end for %>
&lt;/fieldset>

```

**Beispiel einer HTML-Struktur**

```HTML

&lt;fieldset class="checkbox-group-wrapper field-topping field-wrapper" id="topping_preference" name="topping_preference" data-required="false">
  &lt;legend for="topping_preference" class="field-label">Pizza Toppings:&lt;/legend>
  <div class="checkbox-wrapper field-topping">
    &lt;input type="checkbox" value="pepperoni" id="topping_pepperoni" data-field-type="checkbox-group" name="topping_preference">
    &lt;label for="topping_pepperoni" class="field-label">Pepperoni&lt;/label>
  </div>
  <div class="checkbox-wrapper field-topping">
    &lt;input type="checkbox" value="mushrooms" id="topping_mushrooms" data-field-type="checkbox-group" name="topping_preference">
    &lt;label for="topping_mushrooms" class="field-label">Mushrooms&lt;/label>
  </div>
  <div class="checkbox-wrapper field-topping">
    &lt;input type="checkbox" value="onions" id="topping_onions" data-field-type="checkbox-group" name="topping_preference">
    &lt;label for="topping_onions" class="field-label">Onions&lt;/label>
  </div>
&lt;/fieldset>

```

+++

+++ CSS-Auswahl für Kontrollkästchengruppen

* Auf den äußeren Wrapper abzielen: Diese Auswahl wählt die äußersten Container von Optionsfeld- und Kontrollkästchengruppen als Ziel aus, sodass Sie allgemeine Stile auf die gesamte Gruppenstruktur anwenden können. Dies ist nützlich zum Festlegen von Abstand, Ausrichtung oder anderen Layout-bezogenen Eigenschaften.

```CSS

  
  /* Targets radio group wrappers */
  main .form form .radio-group-wrapper &lbrace;
    margin-bottom: 20px; /* Adds space between radio groups */  
  &rbrace;

  /* Targets checkbox group wrappers */
  main .form form .checkbox-group-wrapper &lbrace;
    margin-bottom: 20px; /* Adds space between checkbox groups */
  &rbrace;

```

* Bezeichnungen der Zielgruppe: Diese Auswahl wählt das `.field-label`-Element sowohl in Optionsfeld- als auch in Kontrollkästchengruppen-Wrappern als Ziel aus. Dadurch können Sie die Beschriftungen speziell für diese Gruppen formatieren und sie ggf. auffälliger gestalten.

```CSS

main .form form .radio-group-wrapper legend,
main .form form .checkbox-group-wrapper legend &lbrace;
  font-weight: bold; /* Makes the group label bold */
&rbrace;

```

* Targeting einzelner Eingaben und Beschriftungen: Diese Auswahl bietet eine präzisere Kontrolle über einzelne Optionsfelder, Kontrollkästchen und die zugehörigen Beschriftungen. Sie können diese verwenden, um Größe und Abstand anzupassen oder spezifischere visuelle Stile anzuwenden.

```CSS

/* Styling radio buttons */
main .form form .radio-group-wrapper input[type="radio"] &lbrace;
  margin-right: 5px; /* Adds space between the input and its label */
&rbrace;

/* Styling radio button labels */
main .form form .radio-group-wrapper label &lbrace;
  font-size: 15px; /* Changes the label font size */
&rbrace;

/* Styling checkboxes */
main .form form .checkbox-group-wrapper input[type="checkbox"] &lbrace;
  margin-right: 5px; /* Adds space between the input and its label */
&rbrace;

/* Styling checkbox labels */
main .form form .checkbox-group-wrapper label &lbrace;
  font-size: 15px; /* Changes the label font size */
&rbrace;

```

* Anpassen des Erscheinungsbilds von Optionsfeldern und Kontrollkästchen: Diese Methode blendet die Standardeingabe aus und verwendet die Pseudo-Elemente `:before` und `:after`, um benutzerdefinierte Visualisierungen zu erstellen, die das Erscheinungsbild basierend auf dem Status „aktiviert“ ändern.

```CSS

/* Hide the default radio button or checkbox */
main .form form .radio-group-wrapper input[type="radio"],
main .form form .checkbox-group-wrapper input[type="checkbox"] &lbrace;
  opacity: 0;
  position: absolute;
&rbrace;

/* Create a custom radio button */
main .form form .radio-group-wrapper input[type="radio"] + label::before &lbrace;
  /* ... styles for custom radio button ... */
&rbrace;

main .form form .radio-group-wrapper input[type="radio"]:checked + label::before &lbrace;
  /* ... styles for checked radio button ... */
&rbrace;

/* Create a custom checkbox */
main .form form .checkbox-group-wrapper input[type="checkbox"] + label::before &lbrace;
  /* ... styles for custom checkbox ... */
&rbrace;

main .form form .checkbox-group-wrapper input[type="checkbox"]:checked + label::before &lbrace;
  /* ... styles for checked checkbox ... */
&rbrace;

```

+++

### Bedienfeld-/Container-Komponenten

+++ HTML-Struktur von Bedienfeld-/Container-Komponenten

```HTML

&lt;fieldset class="panel-wrapper field-{PanelName} field-wrapper">
  &lt;legend for="{id}" class="field-label" data-visible="false">bannerComponent&lt;/legend>
  <div class="{Type}-wrapper field-{Name} field-wrapper">
    &lt;label for="{FieldId}" class="field-label">First Name&lt;/label>
    &lt;input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}">
    <div class="field-description" aria-live="polite" id="{FieldId}-description">
      Hint - First name should be minimum 3 characters and a maximum of 10 characters.
    </div>
  </div>
&lt;/fieldset>

```

**Beispiel einer HTML-Struktur**

```HTML

&lt;fieldset class="panel-wrapper field-login field-wrapper">
  &lt;legend for="login" class="field-label" data-visible="false">Login Information&lt;/legend>
  <div class="text-wrapper field-username field-wrapper">
    &lt;label for="username" class="field-label">Username&lt;/label>
    &lt;input type="text" placeholder="Enter your username" maxlength="50" id="username" name="username">
    <div class="field-description" aria-live="polite" id="username-description">
      Please enter your username or email address.
    </div>
  </div>
  <div class="password-wrapper field-password field-wrapper">
    &lt;label for="password" class="field-label">Password&lt;/label>
    &lt;input type="password" placeholder="Enter your password" maxlength="20" id="password" name="password">
    <div class="field-description" aria-live="polite" id="password-description">
      Your password must be at least 8 characters long.
    </div>
  </div>
&lt;/fieldset>

```

* Das fieldset-Element dient als Bedienfeld-Container mit dem Klassen-Bedienfeld-Wrapper und zusätzlichen Klassen zur Gestaltung basierend auf dem Bedienfeldnamen (Feldanmeldung).
* Das legend-Element (<legend>) dient als Bedienfeldtitel mit dem Text „Anmeldeinformationen“ und der Klassenfeldbezeichnung. Das data-visible=&quot;false&quot;-Attribut kann mit JavaScript verwendet werden, um die Sichtbarkeit des Titels zu steuern.
* In diesem Feldsatz gibt es mehrere.{Type}-Wrapper-Elemente (in diesem Fall „.text-wrapper“ und „.password-wrapper“x) für einzelne Formularfelder im Bedienfeld.
* Jeder Wrapper enthält eine Bezeichnung, ein Eingabefeld und eine Beschreibung, ähnlich wie bei den vorherigen Beispielen.

+++

+++ Beispiel zur CSS-Auswahl für Bedienfeld-/Container-Komponenten

1. Targeting des Bedienfelds:

```CSS

  /* Target the entire panel container */
  main .form form .panel-wrapper &lbrace;
    /* Add your styles here (e.g., border, padding, background color) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
 &rbrace;

```

* Die `.panel-wrapper`-Auswahl gestaltet alle Elemente mit dem Klassenbedienfeld-Wrapper, wodurch ein einheitlicher Look für alle Bedienfelder entsteht.

1. Targeting des Bedientitels:

```CSS

  /* Target the legend element (panel title) */
  .panel-wrapper legend &lbrace;
    /* Add your styles here (e.g., font-weight, font-size) */
    font-weight: bold;
    font-size: 16px;
    padding-bottom: 5px;
    margin-bottom: 10px;
    border-bottom: 1px solid #ddd; /* Optional: create a separation line */
  &rbrace;

```

* Die `.panel-wrapper legend`-Auswahl gestaltet das legend-Element im Bedienfeld, sodass der Titel optisch hervorgehoben wird.


1. Targeting einzelner Felder im Bedienfeld:

```CSS

/* Target all form field wrappers within a panel */
main .form form .panel-wrapper .{Type}-wrapper &lbrace;
  /* Add your styles here (e.g., margin) */
  margin-bottom: 10px;
&rbrace;

```

* Die Auswahl `.panel-wrapper .{Type}-wrapper` wählt alle Wrapper mit der Klasse `.{Type}-wrapper` innerhalb des Bedienfelds als Ziel aus, sodass Sie den Abstand zwischen Formularfeldern festlegen können.

1. Targeting bestimmter Felder (optional):

```CSS

  /* Target the username field wrapper */
  main .form form .panel-wrapper .text-wrapper.field-username &lbrace;
    /* Add your styles here (specific to username field) */
  &rbrace;

  /* Target the password field wrapper */
  main .form form .panel-wrapper .password-wrapper.field-password &lbrace;
    /* Add your styles here (specific to password field) */
  &rbrace;

```

* Mit diesen optionalen Auswahlen können Sie bestimmte Feld-Wrapper innerhalb des Bedienfelds als Ziel auswählen, um einen eindeutigen Stil zu ermöglichen, z. B. zur Hervorhebung des Felds „Benutzername“.

+++

### Wiederholbares Bedienfeld

+++ HTML-Struktur eines wiederholbaren Bedienfelds

```HTML

&lt;fieldset class="panel-wrapper field-{PanelName} field-wrapper">
  &lt;legend for="{id}" class="field-label" data-visible="false">bannerComponent&lt;/legend>
  <div class="{Type}-wrapper field-{Name} field-wrapper">
    &lt;label for="{FieldId}" class="field-label">First Name&lt;/label>
    &lt;input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}">
    <div class="field-description" aria-live="polite" id="{FieldId}-description">
      Hint - First name should be minimum 3 characters and a maximum of 10 characters.
    </div>
&lt;/fieldset>

```

**Beispiel einer HTML-Struktur**

```HTML

&lt;fieldset class="panel-wrapper field-contact field-wrapper" data-repeatable="true">
  &lt;legend for="contact-1" class="field-label" data-visible="false">Contact Information&lt;/legend>
  <div class="text-wrapper field-name field-wrapper">
    &lt;label for="name-1" class="field-label">Name&lt;/label>
    &lt;input type="text" placeholder="Enter your name" maxlength="50" id="name-1" name="contacts[0].name">
    <div class="field-description" aria-live="polite" id="name-1-description">
      Please enter your full name.
    </div>
  </div>
  <div class="email-wrapper field-email field-wrapper">
    &lt;label for="email-1" class="field-label">Email&lt;/label>
    &lt;input type="email" placeholder="Enter your email address" maxlength="100" id="email-1" name="contacts[0].email">
    <div class="field-description" aria-live="polite" id="email-1-description">
      Please enter a valid email address.
    </div>
  </div>
&lt;/fieldset>

&lt;fieldset class="panel-wrapper field-contact field-wrapper" data-repeatable="true">
  &lt;legend for="contact-2" class="field-label" data-visible="false">Contact Information&lt;/legend>
  <div class="text-wrapper field-name field-wrapper">
    &lt;label for="name-2" class="field-label">Name&lt;/label>
    &lt;input type="text" placeholder="Enter your name" maxlength="50" id="name-2" name="contacts[1].name">
    <div class="field-description" aria-live="polite" id="name-2-description">
      Please enter your full name.
    </div>
  </div>
  <div class="email-wrapper field-email field-wrapper">
    &lt;label for="email-2" class="field-label">Email&lt;/label>
    &lt;input type="email" placeholder="Enter your email address" maxlength="100" id="email-2" name="contacts[1].email">
    <div class="field-description" aria-live="polite" id="email-2-description">
      Please enter a valid email address.
    </div>
  </div>
&lt;/fieldset>

```

Jedes Bedienfeld weist dieselbe Struktur wie das Beispiel eines einzelnen Bedienfelds auf, allerdings mit zusätzlichen Attributen:

* data-repeatable=&quot;true&quot;: Dieses Attribut gibt an, dass das Bedienfeld dynamisch mit JavaScript oder einem Framework wiederholt werden kann.

* Eindeutige IDs und Namen: Jedes Element im Bedienfeld verfügt über eine eindeutige ID (z. B. name-1, email-1) und ein eindeutiges name-Attribut, das auf dem Index des Bedienfelds basiert (z. B. nname=&quot;contacts[0].name&quot;). Dies ermöglicht eine korrekte Datenerfassung bei der Übermittlung mehrerer Bedienfelder.

+++

+++ CSS-Auswahl für ein wiederholbares Bedienfeld

* Targeting aller wiederholbaren Bedienfelder:

```CSS

  /* Target all panels with the repeatable attribute */
 main .form form .panel-wrapper[data-repeatable="true"] &lbrace;
    /* Add your styles here (e.g., border, margin) */
    border: 1px solid #ccc;
    padding: 15px;
    border-radius: 4px;
    margin-bottom: 20px;
  &rbrace;

```

Die Auswahl gestaltet alle wiederholbaren Bedienfelder und sorgt so für ein einheitliches Look-and-Feel.


* Targeting einzelner Felder in einem Bedienfeld:

```CSS

/* Target all form field wrappers within a repeatable panel */
main .form form .panel-wrapper[data-repeatable="true"] .{Type}-wrapper &lbrace;
  /* Add your styles here (e.g., margin) */
  margin-bottom: 10px;
&rbrace;

```
Diese Auswahl gestaltet alle Feld-Wrapper in einem wiederholbaren Bedienfeld, wobei ein konsistenter Abstand zwischen Feldern beibehalten wird.

* Targeting bestimmter Felder (in einem Bedienfeld):

```CSS

/* Target the name field wrapper within the first panel */
main .form form .panel-wrapper[data-repeatable="true"][data-index="0"] .text-wrapper.field-name &lbrace;
  /* Add your styles here (specific to first name field) */
&rbrace;

/* Target all

```

+++

### Dateianhang

+++ HTML-Struktur für Dateianhänge

```HTML

<div class="file-wrapper field-{FileName} field-wrapper">
  &lt;legend for="{id}" class="field-label" data-visible="false"> File Attachment &lt;/legend>
  <div class="file-drag-area">
    <div class="file-dragIcon"></div>
    <div class="file-dragText">Drag and Drop To Upload</div>
    &lt;button class="file-attachButton" type="button">Attach&lt;/button>
    &lt;input type="file" accept="audio/*, video/*, image/*, text/*, application/pdf" id="{id}" name="{FileName}" autocomplete="off" multiple="" required="required">
  </div>
  <div class="files-list">
    <div data-index="0" class="file-description">
      <span class="file-description-name">ClaimForm.pdf</span>
      <span class="file-description-size">26 kb</span>
      &lt;button class="file-description-remove" type="button">&lt;/button>
    </div>
  </div>
</div>

```

**Beispiel einer HTML-Struktur**


```HTML

<div class="file-wrapper field-claim_form field-wrapper">
  &lt;legend for="claim_form" class="field-label" data-visible="false">File Attachment&lt;/legend>
  <div class="file-drag-area">
    <div class="file-dragIcon"></div>
    <div class="file-dragText">Drag and Drop To Upload</div>
    &lt;button class="file-attachButton" type="button">Attach&lt;/button>
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
main .form form .file-wrapper &lbrace;
  /* Add your styles here (e.g., border, padding) */
  border: 1px solid #ccc;
  padding: 15px;
  border-radius: 4px;
  margin-bottom: 20px;
&rbrace;

```

Diese Auswahl gestaltet die gesamte Dateianhangskomponente, einschließlich Legende, Ziehbereich, Eingabefeld und Liste.

* Targeting bestimmter Elemente:

```CSS

/* Target the drag and drop area */
main .form form .file-wrapper .file-drag-area &lbrace;
  /* Add your styles here (e.g., background color, border) */
  background-color: #f0f0f0;
  border: 1px dashed #ddd;
  padding: 10px;
  text-align: center;
&rbrace;

/* Target the file input element */
main .form form .file-wrapper input[type="file"] &lbrace;
  /* Add your styles here (e.g., hide the default input) */
  display: none;
&rbrace;

/* Target individual file descriptions within the list (populated dynamically) */
main .form form .file-wrapper .files-list .file-description &lbrace;
  /* Add your styles here (e.g., margin, display) */
  display: flex;
  justify-content: space-between;
  margin-bottom: 5px;
&rbrace;

/* Target the file name within the description */
main .form form .file-wrapper .files-list .file-description .file-description-name &lbrace;
  /* Add your styles here (e.g., font-weight) */
  font-weight: bold;
&rbrace;

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
   &lt;label for="{FieldId}" class="field-label">First Name&lt;/label>
   &lt;input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id={FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - First name should be minimum 3 characters and a maximum of 10 characters.
   </div>
</div>

```

**Beispiel einer HTML-Struktur**

```HTML

<div class="text-wrapper field-name field-wrapper" data-required="true">
  &lt;label for="name" class="field-label">Name&lt;/label>
  &lt;input type="text" placeholder="Enter your name" maxlength="50" id="name" name="name">
</div>

<div class="number-wrapper field-age field-wrapper" data-required="true">
  &lt;label for="age" class="field-label">Age&lt;/label>
  &lt;input type="number" placeholder="Enter your age" id="age" name="age">
</div>

<div class="email-wrapper field-email field-wrapper" data-required="true">
  &lt;label for="email" class="field-label">Email Address&lt;/label>
  &lt;input type="email" placeholder="Enter your email" id="email" name="email">
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
main .form form .text-wrapper input &lbrace;
  /* Add your styles here */
&rbrace;

/* Target all number input fields */
main .form form .number-wrapper input &lbrace;
  /* Add your styles here */
  letter-spacing: 2px; /* Example for adding letter spacing to all number fields */
&rbrace;

```

+++

### Formatierung basierend auf Feldnamen

Sie können auch einzelne Felder nach Namen als Ziel auswählen, um eindeutige Stile anzuwenden.

+++ HTML-Struktur

```HTML

<div class="{Type}-wrapper field-{Name} field-wrapper" data-required={Required}>
   &lt;label for="{FieldId}" class="field-label">First Name&lt;/label>
   &lt;input type="{Type}" placeholder="{Placeholder}" maxlength="{Max}" id="{FieldId}" name="{Name}" aria-describedby="{FieldId}-description">
   <div class="field-description" aria-live="polite" id="{FieldId}-description">
    Hint - Enter the 6 digit number sent to your mobile number.
   </div>
</div>

```

**Beispiel einer HTML-Struktur**

```HTML

<div class="number-wrapper field-otp field-wrapper" data-required="true">
  &lt;label for="otp" class="field-label">OTP&lt;/label>
  &lt;input type="number" placeholder="Enter your OTP" maxlength="6" id="otp" name="otp" aria-describedby="otp-description">
  <div class="field-description" aria-live="polite" id="otp-description">
    Hint - Enter the 6 digit number sent to your mobile number.
   </div>
</div>

```

+++

+++ Beispiel einer CSS-Auswahl

```CSS

main .form form .field-otp input &lbrace;
   letter-spacing: 2px
&rbrace;

```

Diese CSS-Datei wählt alle Eingabeelemente als Ziel aus, die sich in einem Element mit der Klasse `field-otp` befinden. Die HTML-Struktur Ihres Formulars entspricht den Konventionen des adaptiven Formularblocks. Dies bedeutet, dass ein mit der Klasse „field-otp“ markierter Container das Feld mit dem Namen „otp“ enthält.

+++




## Siehe auch

{{universal-editor-see-also}}
