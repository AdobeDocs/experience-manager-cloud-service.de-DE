---
title: Design-JSON-Schema für ein adaptives Formular
description: Erfahren Sie, wie Sie adaptive Formulare mit JSON-Schema als Formularmodell erstellen. Sie können bestehende JSON-Schemas verwenden, um adaptive Formulare zu erstellen. Vertiefen Sie Ihre Kenntnisse anhand eines Beispiels für ein JSON-Schema, vorkonfigurieren Sie Felder in der JSON-Schema-Definition, beschränken Sie den zulässigen Wertbereich für eine Komponente des adaptiven Formulars und machen Sie sich mit nicht unterstützten Konstrukten vertraut.
feature: Adaptive Forms
role: User, Developer
level: Beginner, Intermediate
exl-id: 8eeb9c5e-6866-4bfe-b922-1f028728ef0d
source-git-commit: b6dcb6308d1f4af7a002671f797db766e5cfe9b5
workflow-type: tm+mt
source-wordcount: '1248'
ht-degree: 64%

---

# Entwerfen eines JSON-Schemas für ein adaptives Formular {#creating-adaptive-forms-using-json-schema}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/adaptive-form-json-schema-form-model.html) |
| AEM as a Cloud Service | Dieser Artikel |


## Voraussetzungen {#prerequisites}

Für das Erstellen eines adaptiven Formulars mit einem JSON-Schema als Formularmodell sind grundlegende Kenntnisse zu JSON-Schemas erforderlich. Es wird empfohlen, den folgenden Inhalt vor diesem Artikel durchzulesen.

* [Erstellen eines adaptiven Formulars](creating-adaptive-form.md)
* [JSON-Schema](https://json-schema.org/)

## Verwenden eines JSON-Schemas als Formularmodell  {#using-a-json-schema-as-form-model}

Adobe Experience Manager Forms unterstützt die Erstellung eines adaptiven Formulars mit einem vorhandenen JSON-Schema als Formularmodell. Dieses JSON-Schema stellt die Struktur dar, in der Daten vom Back-End-System in Ihrem Unternehmen produziert oder genutzt werden. Das JSON-Schema, das Sie verwenden, sollte mit den [Spezifikationen der Version 4](https://json-schema.org/draft-04/schema) konform sein.

Die wichtigsten Funktionen bei Verwendung eines JSON-Schemas sind wie folgt:

* Die Struktur der JSON-Datei wird als Baumstruktur in der Registerkarte für die Content-Suche im Authoring-Modus für ein adaptives Formular angezeigt. Sie können Elemente aus der JSON-Hierarchie in das adaptive Formular ziehen.
* Sie können das Formular mit JSON im Voraus ausfüllen, das mit dem zugehörigen Schema konform ist.
* Bei der Übermittlung werden die vom Benutzer eingegebenen Daten als JSON gesendet, das dem zugehörigen Schema entspricht.

Ein JSON-Schema besteht aus einfachen und komplexen Elementtypen. Die Elemente weisen Attribute auf, die dem Element Regeln hinzufügen. Wenn diese Elemente und Attribute in ein adaptives Formular gezogen werden, werden sie automatisch der entsprechenden Komponente des adaptiven Formulars zugeordnet.

Diese Zuordnung von JSON-Elementen zu Komponenten adaptiver Formulare ist wie folgt:

```json
"birthDate": {
              "type": "string",
              "format": "date",
              "pattern": "date{DD MMMM, YYYY}",
              "aem:affKeyword": [
                "DOB",
                "Date of Birth"
              ],
              "description": "Date of birth in DD MMMM, YYYY",
              "aem:afProperties": {
                "displayPictureClause": "date{DD MMMM, YYYY}",
                "displayPatternType": "date{DD MMMM, YYYY}",
                "validationPatternType": "date{DD MMMM, YYYY}",
                "validatePictureClause": "date{DD MMMM, YYYY}",
                "validatePictureClauseMessage": "Date must be in DD MMMM, YYYY format."
              }
```

<table>
 <tbody>
  <tr>
   <th><strong>JSON-Element, -Eigenschaften oder -Attribute</strong></th>
   <th><strong>Komponente des adaptiven Formulars</strong></th>
  </tr>
  <tr>
   <td><p>Zeichenfolgen-Eigenschaften mit enum- und enumNames-Beschränkung.</p> <p>Syntax,</p> <p> <code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"enum" : ["M", "F"]</code></p> <p><code>"enumNames" : ["Male", "Female"]</code></p> <p><code>}</code></p> <p> </p> </td>
   <td><p>Dropdown-Komponente:</p>
    <ul>
     <li>Die in enumNames aufgeführten Werte werden in der Dropbox angezeigt.</li>
     <li>Die in der Aufzählung aufgeführten Werte werden zur Berechnung verwendet.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Zeichenfolgeneigenschaft mit Formateinschränkung. Beispielsweise E-Mail und Datum.</p> <p>Syntax,</p> <p><code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"format" : "email"</code></p> <p><code>}</code></p> <p> </p> </td>
   <td>
    <ul>
     <li>Die E-Mail-Komponente wird zugeordnet, wenn der Typ Zeichenfolge und das Format E-Mail ist.</li>
     <li>Textbox-Komponente mit Validierung wird zugeordnet, wenn der Typ Zeichenfolge ist und das Format der Hostname ist.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>}</code></p> </td>
   <td><br /> <br /> Textfeld<br /> <br /> <br /> </td>
  </tr>
  <tr>
   <td>number-Eigenschaft<br /> </td>
   <td>Numerisches Feld mit Untertyp auf Gleitkommazahl eingestellt<br /> </td>
  </tr>
  <tr>
   <td>Ganzzahl-Eigenschaft<br /> </td>
   <td>Numerisches Feld mit Untertyp "integer"<br /> </td>
  </tr>
  <tr>
   <td>Boolesche Eigenschaft<br /> </td>
   <td>Schalter<br /> </td>
  </tr>
  <tr>
   <td>Objekteigenschaft<br /> </td>
   <td>Bedienfeld<br /> </td>
  </tr>
  <tr>
   <td>Array-Eigenschaft</td>
   <td>Wiederholbares Bedienfeld mit Mindest- und Höchstwert gleich "minItems"bzw. "maxItems". Nur homogene Arrays werden unterstützt. Daher muss die Elementbeschränkung ein Objekt sein, kein Array.<br /> </td>
  </tr>
 </tbody>
</table>

### Allgemeine Schema-Eigenschaften {#common-schema-properties}

Das adaptive Formular verwendet die im JSON-Schema verfügbaren Informationen, um jedes generierte Feld zuzuordnen. Führen Sie insbesondere die folgenden Aufgaben aus:

* Die `title`-Eigenschaft dient als Bezeichnung für die Komponenten des adaptiven Formulars.
* Die `description`-Eigenschaft ist als lange Beschreibung für Komponenten von adaptiven Formularen festgelegt.
* Die `default`-Eigenschaft dient als Ausgangswert für ein Feld in einem adaptiven Formular.
* Die `maxLength`-Eigenschaft wird dem `maxlength`-Attribut einer Textfeldkomponente zugewiesen.
* Die Eigenschaften `minimum`, `maximum`, `exclusiveMinimum` und `exclusiveMaximum` werden für Komponenten vom Typ „numerisches Feld“ verwendet.
* Um Bereiche für eine `DatePicker component`-Komponente zu unterstützen, werden die zusätzlichen JSON-Schemaeigenschaften `minDate` und `maxDate` bereitgestellt.
* Mithilfe der Eigenschaften `minItems` und `maxItems` wird die Anzahl der Elemente/Felder eingeschränkt, die einer Bedienfeldkomponente hinzugefügt oder daraus entfernt werden können.
* Die `readOnly`-Eigenschaft legt das `readonly`-Attribut einer Komponente eines adaptiven Formulars fest.
* Die `required`-Eigenschaft kennzeichnet ein adaptives Formularfeld als obligatorisch, während im Falle eines Bedienfelds (wobei „type“ ein Objekt ist) die endgültigen übermittelten JSON-Daten Felder mit leerem Wert entsprechend diesem Objekt enthalten.
* Die `pattern`-Eigenschaft ist als Validierungsmuster (regulärer Ausdruck) im adaptiven Formular festgelegt.
* Die Erweiterung der JSON-Schema-Datei „.schema.json“ muss beibehalten werden. Beispiel: &lt;filename>.schema.json.

## Beispiel für ein JSON-Schema {#sample-json-schema}

Im Folgenden finden Sie ein Beispiel für ein JSON-Schema.

```json
{
 "$schema": "https://json-schema.org/draft-04/schema#",
 "definitions": {
  "employee": {
   "type": "object",
   "properties": {
    "userName": {
     "type": "string"
    },
    "dateOfBirth": {
     "type": "string",
     "format": "date"
    },
    "email": {
     "type": "string",
     "format": "email"
    },
    "language": {
     "type": "string"
    },
    "personalDetails": {
     "$ref": "#/definitions/personalDetails"
    },
    "projectDetails": {
     "$ref": "#/definitions/projectDetails"
    }
   },
   "required": [
    "userName",
    "dateOfBirth",
    "language"
   ]
  },
  "personalDetails": {
   "type": "object",
   "properties": {
    "GeneralDetails": {
     "$ref": "#/definitions/GeneralDetails"
    },
    "Family": {
     "$ref": "#/definitions/Family"
    },
    "Income": {
     "$ref": "#/definitions/Income"
    }
   }
  },
  "projectDetails": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     },
     "projects": {
      "$ref": "#/definitions/projects"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "projects": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     },
     "projectsAdditional": {
      "$ref": "#/definitions/projectsAdditional"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "projectsAdditional": {
   "type": "array",
   "items": {
    "properties": {
     "Additional_name": {
      "type": "string"
     },
     "Additional_areacode": {
      "type": "number"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  },
  "GeneralDetails": {
   "type": "object",
   "properties": {
    "age": {
     "type": "number"
    },
    "married": {
     "type": "boolean"
    },
    "phone": {
     "type": "number",
     "aem:afProperties": {
      "sling:resourceType": "/libs/fd/af/components/guidetelephone",
      "guideNodeClass": "guideTelephone"
     }
    },
    "address": {
     "type": "string"
    }
   }
  },
  "Family": {
   "type": "object",
   "properties": {
    "spouse": {
     "$ref": "#/definitions/spouse"
    },
    "kids": {
     "$ref": "#/definitions/kids"
    }
   }
  },
  "Income": {
   "type": "object",
   "properties": {
    "monthly": {
     "type": "number"
    },
    "yearly": {
     "type": "number"
    }
   }
  },
  "spouse": {
   "type": "object",
   "properties": {
    "name": {
     "type": "string"
    },
    "Income": {
     "$ref": "#/definitions/Income"
    }
   }
  },
  "kids": {
   "type": "array",
   "items": {
    "properties": {
     "name": {
      "type": "string"
     },
     "age": {
      "type": "number"
     }
    }
   },
   "minItems": 1,
   "maxItems": 4
  }
 },
 "type": "object",
 "properties": {
  "employee": {
   "$ref": "#/definitions/employee"
  }
 }
}
```

### Wiederverwendbare Schemadefinitionen {#reusable-schema-definitions}

Definitionsschlüssel kennzeichnen wiederverwendbare Schemas. Die wiederverwendbaren Schemadefinitionen werden verwendet, um Fragmente zu erstellen. <!-- It is similar to identifying complex types in XSD.--> Ein JSON-Beispielschema mit Definitionen wird unten angezeigt:

```json
{
  "$schema": "https://json-schema.org/draft-04/schema#",

  "definitions": {
    "address": {
      "type": "object",
      "properties": {
        "street_address": { "type": "string" },
        "city":           { "type": "string" },
        "state":          { "type": "string" }
      },
      "required": ["street_address", "city", "state"]
    }
  },

  "type": "object",

  "properties": {
    "billing_address": { "$ref": "#/definitions/address" },
    "shipping_address": { "$ref": "#/definitions/address" }
  }
}
```

Im obigen Beispiel wird ein Kundendatensatz definiert, in dem jeder Kunde über eine Versand- und eine Rechnungsadresse verfügt. Die Struktur beider Adressen ist identisch - Adressen haben eine Straße, eine Stadt und einen Bundesstaat - daher ist es empfehlenswert, die Adressen nicht zu duplizieren. Außerdem wird das Hinzufügen und Löschen von Feldern für künftige Änderungen vereinfacht.

## Vorkonfigurieren von Feldern in JSON-Schemadefinitionen {#pre-configuring-fields-in-json-schema-definition}

Mit der Eigenschaft **aem:afProperties** können Sie ein JSON-Schemafeld so vorkonfigurieren, dass es einer benutzerdefinierten Komponente des adaptiven Formulars zugeordnet wird. Ein Beispiel wird unten angezeigt:

```json
{
    "properties": {
        "sizeInMB": {
            "type": "integer",
            "minimum": 16,
            "maximum": 512,
            "aem:afProperties" : {
                 "sling:resourceType" : "/apps/fd/af/components/guideTextBox",
                 "guideNodeClass" : "guideTextBox"
             }
        }
    },
    "required": [ "sizeInMB" ],
    "additionalProperties": false
}
```

<!--- ## Configure scripts or expressions for form objects  {#configure-scripts-or-expressions-for-form-objects}

JavaScript is the expression language of Adaptive Forms. All the expressions are valid JavaScript expressions and use Adaptive Forms scripting model APIs. You can pre-configure form objects to [evaluate an expression](adaptive-form-expressions.md) on a form event.

Use the aem:afproperties property to preconfigure Adaptive Form expressions or scripts for Adaptive Form components. For example, when the initialize event is triggered, the below code sets value of telephone field and prints a value to the log :

```json
"telephone": {
  "type": "string",
  "pattern": "/\\d{10}/",
  "aem:affKeyword": ["phone", "telephone","mobile phone", "work phone", "home phone", "telephone number", "telephone no", "phone number"],
  "description": "Telephone Number",
  "aem:afProperties" : {
    "sling:resourceType" : "fd/af/components/guidetelephone",
    "guideNodeClass" : "guideTelephone",
    "events": {
      "Initialize" : "this.value = \"1234567890\"; console.log(\"ef:gh\") "
    }
  }
}
```

You should be a member of the [forms-power-user group](forms-groups-privileges-tasks.md) to configure scripts or expressions for form object. The below table lists all the script events supported for an Adaptive Form component.

<table>
 <tbody>
  <tr>
   <th><strong></strong>Component \ Event</th>
   <th>initialize <br /> </th>
   <td>Calculate</td>
   <td>Visibility</td>
   <td>Validate</td>
   <td>Enabled</td>
   <td>Value Commit</td>
   <td>Click </td>
   <td>Options</td>
  </tr>
  <tr>
   <td>Text Field</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Numeric Field</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Numeric Stepper</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Radio Button</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Telephone</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Switch</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Button</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
  </tr>
  <tr>
   <td>Check Box</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
  </tr>
  <tr>
   <td>Drop-down</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
  </tr>
  <tr>
   <td>Image Choice</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
  </tr>
  <tr>
   <td>Date Input Field</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Date Picker</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Email</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>File Attachment</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Image</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Draw</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Panel</td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td><img alt="" src="assets/yes_tick.png" /></td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

Some examples of using events in a JSON are hiding a field on initialize event and configure value of another field on value commit event. For detailed information about creating expressions for the script events, see [Adaptive Form Expressions](adaptive-form-expressions.md).

Here is the sample JSON code for previously mentioned examples.

### Hiding a field on initialize event {#hiding-a-field-on-initialize-event}

```json

"name": {
    "type": "string",
    "aem:afProperties": {
        "events" : {
            "Initialize" : "this.visible = false;"
        }
    }
}
```

#### Configure value of another field on value commit event {#configure-value-of-another-field-on-value-commit-event}

```json
"Income": {
    "type": "object",
    "properties": {
        "monthly": {
            "type": "number",
            "aem:afProperties": {
                "events" : {
                    "Value Commit" : "IncomeYearly.value = this.value * 12;"
                }
            }
        },
        "yearly": {
            "type": "number",
            "aem:afProperties": {
                "name": "IncomeYearly"
            }
        }
    }
}

```
-->

## Einschränken der gültigen Werte für eine Komponente eines adaptiven Formulars {#limit-acceptable-values-for-an-adaptive-form-component}

Sie können folgende Einschränkungen zu JSON-Schemaelementen hinzufügen, um den Wertebereich zu begrenzen, der für eine Komponente des adaptiven Formulars akzeptiert wird:

<table>
 <tbody>
  <tr>
   <td><p><strong> Schemaeigenschaft</strong></p> </td>
   <td><p><strong>Datentyp</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
   <td><p><strong>Komponente</strong></p> </td>
  </tr>
  <tr>
   <td><p><code>maximum</code></p> </td>
   <td><p>Zeichenfolge</p> </td>
   <td><p>Gibt die Obergrenze für numerische Werte und Daten an. Standardmäßig ist der Maximalwert enthalten.</p> </td>
   <td>
    <ul>
     <li>Numerisches Feld</li>
     <li>Numerische Schritte<br /> </li>
     <li>Datumsauswahl</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>minimum</code></p> </td>
   <td><p>Zeichenfolge</p> </td>
   <td><p>Gibt die Untergrenze für numerische Werte und Daten an. Standardmäßig ist der Mindestwert enthalten.</p> </td>
   <td>
    <ul>
     <li>Numerisches Feld</li>
     <li>Numerische Schritte</li>
     <li>Datumsauswahl</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>exclusiveMaximum</code></p> </td>
   <td><p>Boolesch</p> </td>
   <td><p>Wenn "true", muss der numerische Wert oder das Datum, der bzw. das in der Komponente des Formulars angegeben wird, kleiner als der numerische Wert oder das Datum sein, der bzw. das für die Eigenschaft "maximum"angegeben ist.</p> <p>Bei "false"muss der numerische Wert oder das Datum, der bzw. das in der Komponente des Formulars angegeben wird, kleiner oder gleich dem numerischen Wert oder Datum sein, der bzw. das für die Eigenschaft "maximum"angegeben ist.</p> </td>
   <td>
    <ul>
     <li>Numerisches Feld</li>
     <li>Numerische Schritte</li>
     <li>Datumsauswahl</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>exclusiveMinimum</code></p> </td>
   <td><p>Boolesch</p> </td>
   <td><p>Wenn "true", muss der in der Komponente des Formulars angegebene numerische Wert oder das Datum größer sein als der numerische Wert oder das Datum, der bzw. das für die Eigenschaft "minimum"angegeben wurde.</p> <p>Bei "false"muss der in der Komponente des Formulars angegebene numerische Wert oder das Datum größer oder gleich dem numerischen Wert oder Datum sein, der bzw. das für die Eigenschaft "minimum"angegeben wurde.</p> </td>
   <td>
    <ul>
     <li>Numerisches Feld</li>
     <li>Numerische Schritte</li>
     <li>Datumsauswahl</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>minLength</code></p> </td>
   <td><p>Zeichenfolge</p> </td>
   <td><p>Gibt die Mindestanzahl von Zeichen an, die in einer Komponente zulässig sind. Die minimale Länge muss größer oder gleich null sein.</p> </td>
   <td>
    <ul>
     <li>Textfeld</li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>maxLength</code></td>
   <td>Zeichenfolge</td>
   <td>Gibt die maximal zulässige Anzahl von Zeichen in einer Komponente an. Die maximale Länge muss größer oder gleich null sein.</td>
   <td>
    <ul>
     <li>Textfeld</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>pattern</code></p> </td>
   <td><p>Zeichenfolge</p> </td>
   <td><p>Gibt die Reihenfolge der Zeichen an. Eine Komponente akzeptiert die Zeichen, wenn die Zeichen dem angegebenen Muster entsprechen.</p> <p>Die Eigenschaft „pattern“ ist dem Überprüfungsmuster der entsprechenden Komponente des adaptiven Formulars zugeordnet.</p> </td>
   <td>
    <ul>
     <li>Alle adaptiven Formulare, die einem XSD-Schema zugeordnet sind </li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>maxItems</code></td>
   <td>Zeichenfolge</td>
   <td>Gibt die maximale Anzahl von Elementen in einem Array an. Die maximale Anzahl von Elementen muss größer oder gleich null sein.</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>minItems</code></td>
   <td>Zeichenfolge</td>
   <td>Gibt die Mindestanzahl von Elementen in einem Array an. Die Mindestanzahl von Elementen muss größer oder gleich null sein.</td>
   <td> </td>
  </tr>
 </tbody>
</table>

## Nicht unterstützte Konstrukte  {#non-supported-constructs}

Adaptive Formulare bieten keine Unterstützung für folgende JSON-Schemakonstrukte:

* Null-Typ
* Unionstypen, z. B. und
* OneOf, AnyOf, AllOf und NOT
* Nur homogene Arrays werden unterstützt. Die Elementbegrenzung muss also ein Objekt und kein Array sein.

## Häufig gestellte Fragen {#frequently-asked-questions}

**Warum kann ich nicht einzelne Elemente eines Teilformulars (Struktur aus einem komplexen Typ generiert) für wiederholbare Teilformulare ziehen (Wert von „minOccurs“ oder „maxOccurs“ ist größer als 1)?**

In einem wiederholbaren Teilformular müssen Sie das vollständige Teilformular verwenden. Wenn Sie nur einzelne Felder nutzen möchten, verwenden Sie die gesamte Struktur und löschen Sie unerwünschte Felder.

**Ich habe eine lange komplexe Struktur in der Inhaltssuche. Wie finde ich ein bestimmtes Element?**

Sie haben zwei Optionen:

* Scrollen Sie durch die Baumstruktur
* Verwenden Sie das Suchfeld, um ein Element zu finden

**Welche Erweiterung sollte die JSON-Schema-Datei aufweisen?**

Für eine JSON-Schema-Datei muss immer die Erweiterung .schema.json verwendet werden. Beispiel: &lt;filename>.schema.json.
