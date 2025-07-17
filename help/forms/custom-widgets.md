---
title: Erstellen von benutzerspezifischen Erscheinungsbildern in HTML5-Formularen
description: Sie können mit Mobile-Formularen benutzerdefinierte Widgets einsetzen.  Sie können vorhandene jQuery Widgets erweitern oder Ihre eigenen benutzerdefinierten Widgets entwickeln.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: HTML5 Forms,Mobile Forms
exl-id: 76bd1e2d-9e65-452c-8cef-123d28886a62
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 22aeedaaf4171ad295199a989e659b6bf5ce9834
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 95%

---

# Erstellen von benutzerspezifischen Erscheinungsbildern in HTML5-Formularen{#create-custom-appearances-in-html-forms}

<span class="preview"> Die HTML5 Forms-Funktion wird als Teil des Early Access-Programms angeboten. Um den Zugriff anzufordern, senden Sie eine E-Mail von Ihrer offiziellen (geschäftlichen) E-Mail-ID an aem-forms-ea@adobe.com.
</span>

Sie können mit Mobile-Formularen benutzerdefinierte Widgets einsetzen.  Sie können mithilfe des Erscheinungsbild-Framework vorhandene jQuery Widgets erweitern oder Ihre eigenen benutzerdefinierten Widgets entwickeln. Die XFA-Engine verwendet verschiedene Widgets. Detaillierte Informationen finden Sie unter [Erscheinungsbild-Framework für adaptive und HTML5-Formulare](/help/forms/custom-widgets.md).

![Beispiel für ein standardmäßiges und benutzerdefiniertes Widget](assets/custom-widgets.jpg)

Beispiel für ein standardmäßiges und ein benutzerdefiniertes Widget

## Integrieren benutzerdefinierter Widgets mit HTML5-Formularen {#integrating-custom-widgets-with-html-forms}

### Erstellen eines Profils  {#create-a-profile-nbsp}

Erstellen Sie ein Profil oder wählen Sie ein vorhandenes Profil, um ein benutzerdefiniertes Widget hinzuzufügen.  Weitere Informationen über das Erstellen benutzerdefinierter Profile finden Sie unter [Erstellen eines benutzerfreundlichen Profils](/help/forms/custom-profile.md).

### Erstellen eines Widgets {#create-a-widget}

HTML5-Formulare bieten eine Implementierung des Widget-Frameworks, die zum Erstellen neuer Widgets erweitert werden kann. Die Implementierung ist ein jQuery-Widget *abstractWidget*, das zum Schreiben eines neuen Widgets erweitert werden kann. Das neue Widget kann nur durch Erweitern bzw. Überschreiben der unten erwähnten Funktionen ordnungsgemäß laufen.

<table>
 <tbody>
  <tr>
   <td>Funktion/Klasse</td>
   <td>Beschreibung</td>
  </tr>
  <tr>
   <td>render</td>
   <td>Die Render-Funktion gibt das jQuery-Objekt für das standardmäßige HTML-Element des Widgets zurück.  Das standardmäßige HTML-Element sollte fokussierbar sein. Zum Beispiel &lt;a&gt;, &lt;input&gt; und &lt;li&gt;.  Das zurückgegebene Element wird als „$userControl“ verwendet.  Wenn $userControl die oben stehende Bedingung erfüllt, laufen die Funktionen der Klasse „AbstractWidget“ ordnungsgemäß. Ansonsten müssen einige allgemeine APIs (focus, click) geändert werden. </td>
  </tr>
  <tr>
   <td>getEventMap</td>
   <td>Gibt eine Zuordnung zur Konvertierung von HTML-Elementen zu XFA-Ereignissen zurück.  <br /> {<br /> blur: XFA_EXIT_EVENT,<br /> }<br /> Dieses Beispiel zeigt, dass „blur“ ein HTML-Ereignis und XFA_EXIT_EVENT das entsprechende XFA-Ereignis ist. </td>
  </tr>
  <tr>
   <td>getOptionsMap</td>
   <td>Gibt eine Zuordnung mit detaillierten Informationen zurück, wie eine Option geändert werden kann.  Die Schlüssel sind die Optionen, die dem Widget übergeben werden, und die Werte sind die Funktionen, die aufgerufen werden, wenn eine Änderung in der jeweiligen Option erkannt wird. Das Widget verfügt über Handler für alle allgemeinen Optionen (außer „value“ und „displayValue“).</td>
  </tr>
  <tr>
   <td>getCommitValue</td>
   <td>Das Widget-Framework lädt Funktionen, sobald der Wert des Widgets im XFAModel gespeichert wird (beispielsweise bei einem exit-Ereignis für ein textField).  Die Implementierung sollte den Wert zurückgeben, der im Widget gespeichert wird. Der Handler erhält den neuen Wert für die Option.</td>
  </tr>
  <tr>
   <td>showValue</td>
   <td>Standardmäßig wird in XFA beim Ereignis „enter“ der rawValue des Felds angezeigt.  Diese Funktion wird aufgerufen, um der Benutzerin oder dem Benutzer den „rawValue“ zu zeigen. </td>
  </tr>
  <tr>
   <td>showDisplayValue</td>
   <td>Standardmäßig wird in XFA beim Ereignis „exit“ der formattedValue des Felds angezeigt. Diese Funktion wird aufgerufen, um der Benutzerin oder dem Benutzer den „formattedValue“ zu zeigen. </td>
  </tr>
 </tbody>
</table>

Um ein eigenes Widget im oben erstellen Profil zu erstellen, müssen Sie die Verweise der JavaScript-Datei einschließen, die die überschriebenen und neu hinzugefügten Funktionen enthält. Das *sliderNumericFieldWidget* ist beispielsweise ein Widget für numerische Felder. Um das Widget in Ihrem Profil in der Kopfzeile zu verwenden, fügen Sie die folgende Zeile hinzu:

```javascript
window.formBridge.registerConfig("widgetConfig" , widgetConfigObject);
```

### Registrieren von benutzerdefinierten Widgets mit XFA Scripting Engine  {#register-custom-widget-with-xfa-scripting-engine-nbsp}

Wenn der Code des benutzerdefinierten Widgets fertig ist, registrieren Sie das Widget mit der Skripterstellungs-Engine, indem Sie die `registerConfig`-API für [Form Bridge](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/forms/developer-reference/form-bridge-apis) verwenden. Als Eingabe ist „widgetConfigObject“ erforderlich.

```javascript
window.formBridge.registerConfig("widgetConfig",
        {
        ".<field-identifier>":"<name-of-the-widget>"
        }
    );
```

#### widgetConfigObject {#widgetconfigobject}

Die Widget-Konfiguration wird als JSON-Objekt bereitgestellt (eine Sammlung von Schlüssel-Wert-Paaren), bei dem der Schlüssel die Felder identifiziert und der Wert für das Widget steht, das mit den Feldern verwendet werden soll.  Eine Beispielkonfiguration sieht wie folgt aus:

```
*{*

*"identifier1" : "customwidgetname",
"identifier2" : "customwidgetname2",
..
}*
```

wobei „Kennung“ eine jQuery-CSS-Auswahl ist, die ein bestimmtes Feld, eine Gruppe von Feldern eines bestimmten Typs oder alle Felder darstellt. Im Folgenden ist der Wert des Bezeichners in verschiedenen Fällen aufgeführt:

| Typ des Bezeichners | ID | Beschreibung |
|---|---|---|
| Bestimmtes Feld mit dem Namen „fieldname“ | Kennung: &quot;div.fieldname&quot; | Alle Felder mit dem Namen „fieldname“ werden mithilfe des Widgets gerendert. |
| Alle Felder des Typs „type“ („type“ ist hier „NumericField“, „DateField“ usw.): | Kennung: &quot;div.type&quot; | Für „TimeField“ und „DateTimeField“ ist der Typ „textfield“, da diese Felder nicht unterstützt werden. |
| Alle Felder | Kennung: &quot;div.field&quot; |  |
