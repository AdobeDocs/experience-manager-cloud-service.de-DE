---
title: Einführung in Bereichsobjekte in benutzerdefinierten Funktionen
description: Form unterstützt Bereichsobjekte in benutzerdefinierten Funktionen, die als letztes Argument an Funktionen übergeben werden, wenn die Regel ausgeführt wird.
keywords: Bereichsobjekte in benutzerdefinierten Funktionen, globalen Objekten, Feldobjekten.
feature: Adaptive Forms, Core Components
role: User, Developer
exl-id: 248c75a5-6335-41d2-aa0a-28a20a710f88
source-git-commit: 4eb0feecbc5d0f090789bd3023e366ef4eb620db
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 2%

---

# Umfangsobjekt in benutzerdefinierten Funktionen

In der adaptiven Forms wird ein Bereichsobjekt als letztes Argument an Funktionen übergeben, wenn eine Regel ausgeführt wird. Es kann verwendet werden, um Formular-/Feldeigenschaften zu lesen und das Formular innerhalb der Funktionen zu ändern. Das Bereichsobjekt enthält ein schreibgeschütztes Proxy-Objekt für das Formular, das ausgelöste Ereignis und das Zielfeld. Auf Formular- und Feldeigenschaften kann über das Objekt „Umfang“ zugegriffen werden, indem `$`, z. B. `scope.form.$id` bzw. `scope.field.$id`, angehängt werden.

## Formularänderungsfunktionen mit dem Bereichsobjekt

Das Bereichsobjekt verfügt über folgende Funktionen zum Ändern des Formulars:

| Funktion | Syntax | Beschreibung | Code-Beispiel |
|-----------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|-----------------------------|
| **setProperty** | `setProperty(any $element, any $payload)` | Legt eine Eigenschaft des `$element` mithilfe des `$payload` fest. | [Hier klicken](/help/forms/custom-function-core-components-use-cases.md#show-a-panel-using-the-setproperty-rule) um das Beispiel anzuzeigen. |
| **Validieren** | `validate([any $element])` | Führt die Validierung auf `$element` durch. Wenn kein -Element angegeben ist, wird das gesamte Formular validiert. | [Hier klicken](/help/forms/custom-function-core-components-use-cases.md#validate-the-field) um das Beispiel anzuzeigen. |
| **Zurücksetzen** | `reset([any $element])` | Setzt die `$element` zurück. Wenn kein -Element bereitgestellt wird, wird das gesamte Formular zurückgesetzt. | [Hier klicken](/help/forms/custom-function-core-components-use-cases.md#reset-a-panel) um das Beispiel anzuzeigen. |
| **importData** | `importData(any $payload)` | Importiert Daten in das Formular und ersetzt alle vorhandenen Formulardaten. | [Hier klicken](/help/forms/custom-function-core-components-use-cases.md#pre-fill-the-field-with-a-value-when-the-form-loads) um das Beispiel anzuzeigen. |
| **exportData** | `exportData()` | Gibt die Daten des Formulars zurück. | [Hier klicken](/help/forms/custom-function-core-components-use-cases.md#submit-altered-data-to-the-server) um das Beispiel anzuzeigen. |
| **submitForm** | `submitForm(any $data [, boolean $validate_form = true, string $submit_as = 'multipart/form-data'])` | Trigger für eine Formularübermittlung. Der `$data` gibt an, was gesendet werden soll, und definiert `$submit_as` den Inhaltstyp (standardmäßig „multipart/form-data„). Die optionale `$validate_form` bestimmt, ob das Formular validiert werden soll (Standard: true). Bei Erfolg wird `submitSuccess` ausgelöst; bei Misserfolg wird `submitError` ausgelöst. | [Hier klicken](/help/forms/custom-function-core-components-use-cases.md#submit-altered-data-to-the-server) um das Beispiel anzuzeigen. |
| **setFocus** | `setFocus(any $element [, FocusOption $focusOption])` | Setzt den Fokus auf den `$element`, der ein Bedienfeld oder ein Feld sein kann. Wenn kein Element bereitgestellt wird, wird der Fokus auf das Feld festgelegt, das die Regel ausgelöst hat. Der optionale `$focusOption`-Parameter (vom Aufzählungstyp `FocusOption`) gibt an, ob der Fokus auf „nextItem“ oder „previousItem“ relativ zu `$element` erfolgen soll. Wenn ein Bedienfeld angegeben ist, ist die Navigation auf dieses Bedienfeld beschränkt. Bei einem Feld erfolgt die Navigation im übergeordneten Bedienfeld. | [Hier klicken](/help/forms/custom-function-core-components-use-cases.md#set-focus-on-the-specific-field) um das Beispiel anzuzeigen. |
| **dispatchevent** | `dispatchEvent(any $element, string $eventName [, any $payload])` | Löst ein Ereignis vom Typ `$eventName` für das von `$element` angegebene Element aus. Wenn kein -Element bereitgestellt wird, wird das -Ereignis auf dem Formular gesendet. Die optionale `$payload` wird für Ausdrücke verfügbar gemacht, die das Ereignis behandeln. | [Hier klicken](/help/forms/custom-function-core-components-use-cases.md#add-or-delete-repeatable-panel-using-the-dispatchevent-property) um das Beispiel anzuzeigen. |
| **markFieldAsInvalid** | `markFieldAsInvalid(string $fieldIdentifier, string $validationMessage [, any $option = {useId: true}])` | Markiert das von `$fieldIdentifier` als ungültig identifizierte Feld und setzt die Überprüfungsmeldung auf `$validationMessage`. Der optionale `$option` gibt an, ob `$fieldIdentifier` als `id`, `name` oder `dataRef` interpretiert wird. Der Standardwert ist `{useId: true}`, und zu den unterstützten Werten gehören `{useId: true}`, `{useDataRef: true}` und `{useQualifiedName: true}`. | [Hier klicken](/help/forms/custom-function-core-components-use-cases.md#to-display-a-custom-message-at-the-field-level-and-marking-the-field-as-invalid) um das Beispiel anzuzeigen. |

## Siehe auch

{{see-also-rule-editor}}
