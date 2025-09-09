---
title: Einführung in Bereichsobjekte in benutzerdefinierten Funktionen
description: Form unterstützt Bereichsobjekte in benutzerdefinierten Funktionen, die als letztes Argument an Funktionen übergeben werden, wenn die Regel ausgeführt wird.
keywords: Bereichsobjekte in benutzerdefinierten Funktionen, globalen Objekten, Feldobjekten.
feature: Adaptive Forms, Core Components
role: User, Developer
exl-id: 248c75a5-6335-41d2-aa0a-28a20a710f88
source-git-commit: e2bc958104bd9b75845ad2c213eec18d2560a3a4
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 3%

---

# Umfangsobjekt in benutzerdefinierten Funktionen

In der adaptiven Forms wird ein Bereichsobjekt als letztes Argument an Funktionen übergeben, wenn eine Regel ausgeführt wird. Es kann verwendet werden, um Formular-/Feldeigenschaften zu lesen und das Formular innerhalb der Funktionen zu ändern. Das Bereichsobjekt enthält ein schreibgeschütztes Proxy-Objekt für das Formular, das ausgelöste Ereignis und das Zielfeld. Auf Formular- und Feldeigenschaften kann über das Objekt „Umfang“ zugegriffen werden, indem `$`, z. B. `scope.form.$id` bzw. `scope.field.$id`, angehängt werden.

## Formularänderungsfunktionen mit dem Bereichsobjekt

Das Bereichsobjekt verfügt über folgende Funktionen zum Ändern des Formulars:

| Funktion | Syntax | Beschreibung | Code-Beispiel |
|-----------------|--------|-------------|-------------|
| **setProperty** | `setProperty(any $element, any $payload)` | Legt eine Eigenschaft im Zielfeld mithilfe der `$payload` fest. | [Hier klicken](/help/forms/custom-function-core-components-use-cases.md#show-a-panel-using-the-setproperty-rule) um das Beispiel anzuzeigen. |
| **Validieren** | `validate([any $element])` | Führt die Validierung für das Zielfeld durch. Führt die Validierung für das gesamte Formular aus, wenn keine Zielgruppe angegeben ist, und gibt ein Array von Validierungsfehlern zurück. | [Hier klicken](/help/forms/custom-function-core-components-use-cases.md#validate-the-field) um das Beispiel anzuzeigen. |
| **Zurücksetzen** *(veraltet)* | `reset([any $element])` | Nicht mehr unterstützt. Verwenden Sie stattdessen `dispatchEvent($target, 'reset')` . Setzt das Zielfeld zurück oder, wenn kein Ziel angegeben wird, das gesamte Formular. | [Hier klicken](/help/forms/custom-function-core-components-use-cases.md#reset-a-panel) um das Beispiel anzuzeigen. |
| **importData** | `importData(any $payload)` | Importiert Daten in das Formular und ersetzt alle vorhandenen Formulardaten. Wenn `qualifiedName` angegeben ist, werden nur die Daten in dieses Container-Feld importiert. | [Hier klicken](/help/forms/custom-function-core-components-use-cases.md#pre-fill-the-field-with-a-value-when-the-form-loads) um das Beispiel anzuzeigen. |
| **exportData** | `exportData()` | Gibt die Daten des Formulars zurück. | [Hier klicken](/help/forms/custom-function-core-components-use-cases.md#submit-altered-data-to-the-server) um das Beispiel anzuzeigen. |
| **submitForm** | `submitForm(any $data [, boolean $validate_form = true, string $submit_as = 'multipart/form-data'])` | Trigger für eine Formularübermittlung. Über den Parameter `$payload` können Sie angeben, was gesendet werden soll, und über den Parameter `$contentType` den Inhaltstyp festlegen. Die Daten werden standardmäßig als `multipart/form-data` übermittelt. Der optionale `$validateForm` gibt an, ob das Formular vor der Übermittlung validiert werden soll (Standard: true). Bei Erfolg wird `submitSuccess` ausgelöst; bei Misserfolg wird `submitError` ausgelöst. | [Hier klicken](/help/forms/custom-function-core-components-use-cases.md#submit-altered-data-to-the-server) um das Beispiel anzuzeigen. |
| **setFocus** | `setFocus(any $element [, FocusOption $focusOption])` | Setzt den Fokus auf das Zielfeld, das ein Bedienfeld oder Formularfeld sein kann. Wenn keine Zielgruppe angegeben wird, wird der Fokus auf das Feld gesetzt, das die Regel ausgelöst hat. Der optionale `$focusOption` gibt an, ob das nächste oder vorherige Element relativ zur Zielgruppe fokussiert werden soll. Unterstützte Werte: `'nextItem'`, `'previousItem'`. Bei Verwendung mit einem Bedienfeld ist die Navigation auf dieses Bedienfeld beschränkt. Bei Verwendung mit einem Feld erfolgt die Navigation innerhalb des übergeordneten Bereichs dieses Felds. | [Hier klicken](/help/forms/custom-function-core-components-use-cases.md#set-focus-on-the-specific-field) um das Beispiel anzuzeigen. |
| **dispatchevent** | `dispatchEvent(any $element, string $eventName [, any $payload])` | Löst ein Ereignis vom Typ `$eventName` für das von `$target` bestimmte Element aus. Wenn keine Zielgruppe angegeben wird, wird das Ereignis auf dem Formular gesendet. Die optionale `$payload` steht für Ausdrücke zur Verfügung, die das Ereignis behandeln. Der optionale Parameter `$dispatch` steuert das Verhalten bei Ereignisweitergabe. | [Hier klicken](/help/forms/custom-function-core-components-use-cases.md#add-or-delete-repeatable-panel-using-the-dispatchevent-property) um das Beispiel anzuzeigen. |
| **markFieldAsInvalid** | `markFieldAsInvalid(string $fieldIdentifier, string $validationMessage [, any $option = {useId: true}])` | Markiert das von `$fieldIdentifier` als ungültig identifizierte Feld und zeigt das `$validationMessage` an. Der optionale `$option` gibt an, ob `$fieldIdentifier` als `id`, `dataRef` oder `qualifiedName` interpretiert wird. Der Standardwert ist `{useId: true}`. Unterstützte Werte: `{useId: true}`, `{useDataRef: true}`, `{useQualifiedName: true}`. | [Hier klicken](/help/forms/custom-function-core-components-use-cases.md#to-display-a-custom-message-at-the-field-level-and-marking-the-field-as-invalid) um das Beispiel anzuzeigen. |

## Siehe auch

{{see-also-rule-editor}}

