---
title: Einführung in den Umfang von Objekten in benutzerdefinierten Funktionen
description: Form unterstützt Scope-Objekte in benutzerdefinierten Funktionen, die bei Ausführung der Regel als letztes Argument an Funktionen übergeben werden.
keywords: Objekte in benutzerdefinierten Funktionen, globalen Objekten, Feldobjekten.
feature: Adaptive Forms, Core Components
role: User, Developer
source-git-commit: af211649a4f22d06f4e8669335a8267ee948a408
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 1%

---


# Scope-Objekt in benutzerdefinierten Funktionen

In Adaptive Forms wird bei Ausführung einer Regel ein Perimeter-Objekt als letztes Argument an Funktionen übergeben. Sie kann verwendet werden, um die Formular-/Feldeigenschaften zu lesen und das Formular in den Funktionen zu ändern. Das scope -Objekt enthält ein schreibgeschütztes Proxy-Objekt für das Formular, das ausgelöste Ereignis und das Zielfeld. Auf die Formular- und Feldeigenschaften kann über das scope -Objekt zugegriffen werden, indem `$`, z. B. `scope.form.$id` und `scope.field.$id` angehängt werden.

## Funktionen zum Ändern von Formularen mit dem Objekt &quot;scope&quot;

Das Scope-Objekt verfügt über die folgenden Funktionen für die Formularänderung:

| Funktion | Syntax | Beschreibung | Code-Beispiel |
|-----------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|-----------------------------|
| **setProperty** | `setProperty(any $element, any $payload)` | Legt eine Eigenschaft von `$element` mit dem Wert `$payload` fest. | [Klicken Sie hier](/help/forms/custom-function-core-components-use-cases.md#show-a-panel-using-the-setproperty-rule) , um das Beispiel anzuzeigen. |
| **validate** | `validate([any $element])` | Führt eine Überprüfung für `$element` aus. Wenn kein Element bereitgestellt wird, wird das gesamte Formular validiert. | [Klicken Sie hier](/help/forms/custom-function-core-components-use-cases.md#validate-the-field) , um das Beispiel anzuzeigen. |
| **reset** | `reset([any $element])` | Setzt den `$element` zurück. Wenn kein Element bereitgestellt wird, wird das gesamte Formular zurückgesetzt. | [Klicken Sie hier](/help/forms/custom-function-core-components-use-cases.md#reset-a-panel) , um das Beispiel anzuzeigen. |
| **importData** | `importData(any $payload)` | Importiert Daten in das Formular und ersetzt vorhandene Formulardaten. | [Klicken Sie hier](/help/forms/custom-function-core-components-use-cases.md#pre-fill-the-field-with-a-value-when-the-form-loads) , um das Beispiel anzuzeigen. |
| **exportData** | `exportData()` | Gibt die Daten des Formulars zurück. | [Klicken Sie hier](/help/forms/custom-function-core-components-use-cases.md#submit-altered-data-to-the-server) , um das Beispiel anzuzeigen. |
| **submitForm** | `submitForm(any $data [, boolean $validate_form = true, string $submit_as = 'multipart/form-data'])` | Trigger einer Formularübermittlung. Der Parameter `$data` gibt an, was gesendet werden soll, und `$submit_as` definiert den Inhaltstyp (standardmäßig &#39;multipart/form-data&#39;). Der optionale Wert `$validate_form` bestimmt, ob das Formular validiert werden soll (Standard: true). Bei Erfolg wird `submitSuccess` ausgelöst; bei einem Fehler wird `submitError` ausgelöst. | [Klicken Sie hier](/help/forms/custom-function-core-components-use-cases.md#submit-altered-data-to-the-server) , um das Beispiel anzuzeigen. |
| **setFocus** | `setFocus(any $element [, FocusOption $focusOption])` | Legt den Fokus auf `$element` fest, bei dem es sich um ein Bedienfeld oder ein Feld handeln kann. Wenn kein Element bereitgestellt wird, wird der Fokus auf das Feld festgelegt, das die Regel ausgelöst hat. Der optionale Parameter `$focusOption` (vom Enumtyp `FocusOption`) gibt an, ob der Fokus auf &quot;nextItem&quot;oder &quot;previousItem&quot;relativ zu `$element` liegen soll. Wenn ein Bedienfeld angegeben ist, ist die Navigation auf dieses Bedienfeld beschränkt. Mit einem Feld erfolgt die Navigation im übergeordneten Bedienfeld. | [Klicken Sie hier](/help/forms/custom-function-core-components-use-cases.md#set-focus-on-the-specific-field) , um das Beispiel anzuzeigen. |
| **patchEvent** | `dispatchEvent(any $element, string $eventName [, any $payload])` | Sendet ein Ereignis des Typs `$eventName` für das von `$element` angegebene Element. Wenn kein Element bereitgestellt wird, wird das Ereignis im Formular gesendet. Das optionale `$payload` wird Ausdrücken zur Verfügung gestellt, die das Ereignis verarbeiten. | [Klicken Sie hier](/help/forms/custom-function-core-components-use-cases.md#add-or-delete-repeatable-panel-using-the-dispatchevent-property) , um das Beispiel anzuzeigen. |
| **markFieldAsInvalid** | `markFieldAsInvalid(string $fieldIdentifier, string $validationMessage [, any $option = {useId: true}])` | Markiert das von `$fieldIdentifier` als ungültig identifizierte Feld und setzt die Validierungsmeldung auf `$validationMessage`. Der optionale Parameter `$option` gibt an, ob `$fieldIdentifier` als `id`, `name` oder `dataRef` interpretiert wird. Der Standardwert ist `{useId: true}` und die unterstützten Werte sind `{useId: true}`, `{useDataRef: true}` und `{useQualifiedName: true}`. | [Klicken Sie hier](/help/forms/custom-function-core-components-use-cases.md#to-display-a-custom-message-at-the-field-level-and-marking-the-field-as-invalid) , um das Beispiel anzuzeigen. |

## Siehe auch

{{see-also-rule-editor}}