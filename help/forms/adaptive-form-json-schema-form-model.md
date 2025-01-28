---
title: Entwerfen eines JSON-Schemas für ein adaptives Formular
description: Erfahren Sie, wie Sie ein JSON-Schema für ein adaptives Formular erstellen und basierend auf dem Schema ein adaptives Formular erstellen, um Schema-konforme Daten zu erstellen.
feature: Adaptive Forms, Foundation Components
role: User, Developer
level: Beginner, Intermediate
exl-id: 8eeb9c5e-6866-4bfe-b922-1f028728ef0d
source-git-commit: b5340c23f0a2496f0528530bdd072871f0d70d62
workflow-type: tm+mt
source-wordcount: '1389'
ht-degree: 97%

---

# Entwerfen eines JSON-Schemas für ein adaptives Formular {#creating-adaptive-forms-using-json-schema}


| Version | Artikel-Link |
| -------- | ---------------------------- |
| Kernkomponenten | [Hier klicken](/help/forms/adaptive-form-core-components-json-schema-form-model.md) |
| Foundation | Dieser Artikel |

>[!NOTE]
>
> Adobe empfiehlt die Verwendung der modernen und erweiterbaren Datenerfassung [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zum [Erstellen eines neuen adaptiven Forms](/help/forms/creating-adaptive-form-core-components.md) oder [Hinzufügen von adaptivem Forms zu AEM Sites-Seiten](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Forms mithilfe von Foundation-Komponenten beschrieben.

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/adaptive-form-json-schema-form-model.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |


## Voraussetzungen {#prerequisites}

Für das Erstellen eines adaptiven Formulars mit einem JSON-Schema als Formularmodell sind grundlegende Kenntnisse zu JSON-Schemas erforderlich. Es wird empfohlen, den folgenden Inhalt vor diesem Artikel durchzulesen.

* [Erstellen eines adaptiven Formulars](creating-adaptive-form.md)
* [JSON-Schema](https://json-schema.org/)

## Verwenden eines JSON-Schemas als Formularmodell  {#using-a-json-schema-as-form-model}

Adobe Experience Manager Forms unterstützt die Erstellung eines adaptiven Formulars mit einem vorhandenen JSON-Schema als Formularmodell. Dieses JSON-Schema stellt die Struktur dar, in der Daten vom Back-End-System in Ihrem Unternehmen produziert oder genutzt werden. Das JSON-Schema, das Sie verwenden, sollte mit den [Spezifikationen der Version 4](https://json-schema.org/draft-04/schema) konform sein.

Die wichtigsten Funktionen bei Verwendung eines JSON-Schemas sind wie folgt:

* Die Struktur der JSON-Datei wird als Baumstruktur in der Registerkarte für die Content-Suche im Authoring-Modus für ein adaptives Formular angezeigt. Sie können Elemente aus der JSON-Hierarchie in das adaptive Formular ziehen.
* Sie können das Formular mithilfe von JSON, das mit dem zugehörigen Schema konform ist, vorbefüllen.
* Bei der Übermittlung werden die benutzerseitig eingegebenen Daten in einem JSON-Format gesendet, das dem zugehörigen Schema entspricht.
* Sie können das Formular auch basierend auf dem JSON-Schema gemäß den Spezifikationen der [Version 2012-20](https://json-schema.org/draft/2020-12/release-notes) erstellen.

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
     <li>Die in „enumNames“ aufgeführten Werte werden in der Dropbox angezeigt.</li>
     <li>Die in „enum“ aufgeführten Werte werden zur Berechnung verwendet.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Zeichenfolgen-Eigenschaft mit format-Beschränkung, Zum Beispiel „email“ oder „date“.</p> <p>Syntax,</p> <p><code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>"format" : "email"</code></p> <p><code>}</code></p> <p> </p> </td>
   <td>
    <ul>
     <li>E-Mail-Komponente wird zugeordnet, wenn der Typ „string“ lautet und das Format „email“.</li>
     <li>Textfeld-Komponente mit Validierung wird zugeordnet, wenn der Typ „string“ lautet und das Format „hostname“.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>{</code></p> <p><code>"type" : "string",</code></p> <p><code>}</code></p> </td>
   <td><br /> <br /> Textfeld<br /> <br /> <br /> </td>
  </tr>
  <tr>
   <td>Zahleneigenschaft<br /> </td>
   <td>Numerisches Feld mit Subtyp „float“<br /> </td>
  </tr>
  <tr>
   <td>Ganzzahl-Eigenschaft<br /> </td>
   <td>Numerisches Feld mit Subtyp „integer“<br /> </td>
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
   <td>Wiederholbares Bedienfeld mit „min“ und „max“ gleich „minItems“ und „maxItems“. Nur homogene Arrays werden unterstützt. Daher muss die Elementbeschränkung ein Objekt sein, kein Array.<br /> </td>
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

>[!BEGINTABS]

>[!TAB JSON-Schema v4]

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


>[!TAB JSON-Schema 2012-20]


```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://example.com/employee.schema.json",
  "$defs": {
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
          "$ref": "#/$defs/personalDetails"
        },
        "projectDetails": {
          "$ref": "#/$defs/projectDetails"
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
          "$ref": "#/$defs/GeneralDetails"
        },
        "Family": {
          "$ref": "#/$defs/Family"
        },
        "Income": {
          "$ref": "#/$defs/Income"
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
            "$ref": "#/$defs/projects"
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
            "$ref": "#/$defs/projectsAdditional"
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
      }
  }
  }
```

>[!ENDTABS]

Die wichtigsten Änderungen zwischen den Spezifikationen des JSON-Schemas v4 und des JSON-Schemas 2020-12 lauten wie folgt:
* Die ID ist als `$id` deklariert
* Definitionen sind als `$defs` deklariert

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

Das obige Beispiel definiert einen Kundendatensatz, bei dem jede Kundin und jeder Kunde über eine Versand- und eine Rechnungsadresse verfügt. Die Struktur der beiden Adressen ist gleich: Straße, Ort und Land. Daher sollten Sie die Adressen nicht duplizieren. Das erleichtert auch das Hinzufügen und Löschen von Feldern, wodurch zukünftige Änderungen einfach sind.

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
   <td><p>Legt die Obergrenze für numerische Werte und Daten fest. Standardmäßig ist der Höchstwert enthalten.</p> </td>
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
   <td><p>Legt die Untergrenze für numerische Werte und Daten fest. Standardmäßig ist der Mindestwert enthalten.</p> </td>
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
   <td><p>Wenn „true“, muss der numerische Wert oder das Datum, der bzw. das in der Komponente des Formulars festgelegt ist, kleiner sein als der numerische Wert oder das Datum, der bzw. das für die Eigenschaft „maximum“ angegeben ist.</p> <p>Wenn „false“, muss der numerische Wert oder das Datum, der bzw. das in der Komponente des Formulars festgelegt ist, kleiner oder gleich dem numerischen Wert oder Datum sein, der bzw. das für die Eigenschaft „maximum“ angegeben ist.</p> </td>
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
   <td><p>Wenn „true“, muss der numerische Wert oder das Datum, der bzw. das in der Komponente des Formulars festgelegt ist, größer sein als der numerische Wert oder das Datum, der bzw. das für die Eigenschaft „minimum“ angegeben ist.</p> <p>Wenn „false“, muss der numerische Wert oder das Datum, der bzw. das in der Komponente des Formulars festgelegt ist, größer oder gleich dem numerischen Wert oder Datum sein, der bzw. das für die Eigenschaft „minimum“ angegeben ist.</p> </td>
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
   <td><p>Legt die zulässige Mindestanzahl von Zeichen in einer Komponente fest. Die minimale Länge muss größer oder gleich null sein.</p> </td>
   <td>
    <ul>
     <li>Textfeld</li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>maxLength</code></td>
   <td>Zeichenfolge</td>
   <td>Legt die zulässige Höchstzahl von Zeichen in einer Komponente fest. Die maximale Länge muss größer oder gleich null sein.</td>
   <td>
    <ul>
     <li>Textfeld</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p><code>pattern</code></p> </td>
   <td><p>Zeichenfolge</p> </td>
   <td><p>Legt die Reihenfolge der Zeichen fest. Eine Komponente akzeptiert die Zeichen, wenn sie dem angegebenen Muster entsprechen.</p> <p>Die Eigenschaft „pattern“ ist dem Überprüfungsmuster der entsprechenden Komponente des adaptiven Formulars zugeordnet.</p> </td>
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


## Aktivieren von schemakonformen Daten {#enablig-schema-compliant-data}

Gehen Sie wie folgt vor, damit alle auf einem JSON-Schema basierenden adaptiven Formulare bei der Formularübermittlung schemakonforme Daten generieren können:

1. Navigieren Sie zur Experience Manager-Web-Konsole unter `https://server:host/system/console/configMgr`.
1. Suchen Sie nach der **[!UICONTROL Web-Kanal-Konfiguration für adaptive Formulare und interaktive Kommunikation]**.
1. Wählen Sie die Konfiguration aus, um sie im Bearbeitungsmodus zu öffnen.
1. Aktivieren Sie das Kontrollkästchen zum **[!UICONTROL Generieren schemakonformer Daten]**.
1. Speichern Sie die Einstellungen.

![Web-Kanal-Konfiguration für adaptive Formulare und interaktive Kommunikation](/help/forms/assets/af-ic-web-channel-configuration.png)


## Nicht unterstützte Konstrukte  {#non-supported-constructs}

Adaptive Formulare bieten keine Unterstützung für folgende JSON-Schemakonstrukte:

* Null-Typ
* Union-Typen wie „any“ und „and“
* „OneOf“, „AnyOf“, „AllOf“ und „NOT“;
* Nur homogene Arrays werden unterstützt. Daher muss die Elementbeschränkung ein Objekt sein, kein Array.
* URI-Verweise in $ref

## Häufig gestellte Fragen {#frequently-asked-questions}

**Warum kann ich nicht einzelne Elemente eines Teilformulars (Struktur aus einem komplexen Typ generiert) für wiederholbare Teilformulare ziehen (Wert von „minOccurs“ oder „maxOccurs“ ist größer als 1)?**

In einem wiederholbaren Teilformular müssen Sie das gesamte Teilformular verwenden. Wenn Sie nur einzelne Felder nutzen möchten, verwenden Sie die gesamte Struktur und löschen Sie unerwünschte Felder.

**Ich habe eine lange komplexe Struktur in der Inhaltssuche. Wie kann ich ein bestimmtes Element suchen?**

Es gibt zwei Optionen:

* Scrollen Sie durch die Baumstruktur
* Verwenden Sie das Suchfeld, um ein Element zu finden

**Welche Erweiterung sollte die JSON-Schema-Datei aufweisen?**

Für eine JSON-Schema-Datei muss immer die Erweiterung .schema.json verwendet werden. Beispiel: &lt;filename>.schema.json.

## Siehe auch {#see-also}

{{see-also}}

<!--

>[!MORELIKETHIS]
>
>* [Design XML Schema for an Adaptive Form](/help/forms/adaptive-form-xml-schema-form-model.md)

-->
