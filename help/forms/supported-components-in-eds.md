---
title: AEM Forms Edge Delivery Service - Formularkomponenten
description: AEM Forms Edge Delivery Service wurde für optimale Leistung entwickelt und ermöglicht es Ihnen, sich die Zukunft einer optimierten Datenerfassung und Benutzerinteraktion vorzustellen. Der Artikel listet alle Formularkomponenten auf, die standardmäßig für EDD-Formulare verfügbar sind.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 3b24d0cd4099e0b8eb48c977f460b25c168af220
workflow-type: tm+mt
source-wordcount: '872'
ht-degree: 5%

---




# HTML-Komponenten, die in der Formularblock-Edge-Bereitstellung unterstützt werden

Die AEM Forms Edge-Bereitstellung umfasst einen Formularblock. Mit dem Formularblock können Sie mühelos Formulare erstellen, um erfasste Daten zu erfassen und zu speichern.

Der Formularblock unterstützt OOTB-HTML-5-Komponenten wie Text, E-Mail, Nummer, Datum und viele mehr. Es unterstützt auch Textbereichs-, Auswahl- und Feldsatzelemente sowie Eingabebesuchungsfunktionen, die nativ in HTML-5 enthalten sind. Der Formularblock erstellt eine einheitliche HTML-Struktur für alle Feldtypen und Container, um die Konsistenz zu gewährleisten. Sie können auch [Formatieren der Feldtypen](https://adobe-rnd.github.io/form-block/customization/styling_form) mithilfe der `form.css` -Datei.

## Unterstützte HTML 5-Eingabetypen im Formularblock

Der Formularblock unterstützt eine Reihe von HTML 5-Eingabetypen und rendert nahtlos Formulare, die mit AEM Kernkomponenten erstellt wurden.

In der folgenden Tabelle wird beschrieben, wie Kernkomponenten ihren HTML-5-Eingabetypen in der Edge-Bereitstellung entsprechen:

<table>
 <tbody>
  <tr>
   <td><b>Kernkomponenten</b> </td>
   <td><b>HTML 5-Eingabetyp</b> </td>
   <td><b>Details</b></td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/form-container.html">Formular-Container</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#form">Formular </td>
   <td> Erstellen Sie ein Formular zur Erfassung von Benutzereingaben.
   </td>
  </tr>
  <tr>
   <td><a herf="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/text-input.html">Texteingabe</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/text">Text</a></td>
   <td> Definiert ein einzeiliges Texteingabefeld. </td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/number-input.html">Zahleneingabe</a></td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/number">Number (Zahl)</a></td>
   <td>Ermöglicht dem Benutzer die Eingabe einer Zahl. Sie können auch eine integrierte Validierung hinzufügen, um nicht numerische Eingaben abzulehnen. Ermöglicht dem Benutzer die Eingabe einer Zahl. Sie können auch eine integrierte Validierung hinzufügen, um nicht numerische Eingaben abzulehnen. Zunächst wird das Eingabefeld als Zahleneingabe angezeigt. Wenn ein Benutzer ein Anzeigemuster anwendet, wird es in Text geändert, sodass der Autor die Zahlenformatierung anwenden kann, da HTML 5 keine Unterstützung für Anzeigemuster bietet. Wenn der Benutzer jedoch darauf klickt, wird er wieder in die Typisierungszahlen zurückgesetzt.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/date-picker.html">Datumsauswahl</a></td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/date">Datum </a></td>
   <td> Erstellen Sie ein Eingabefeld zur Eingabe eines Datums. Sie haben die Möglichkeit, das Datum entweder über ein Textfeld, das den Eintrag validiert, oder über eine spezielle Benutzeroberfläche für die Datumsauswahl einzugeben. Zunächst wird das native Eingabefeld für das Datum angezeigt. Wenn ein Benutzer ein Anzeigemuster anwendet, wird es in Text geändert, sodass der Benutzer Formatierungen anwenden kann, da HTML 5 keine Unterstützung für Anzeigemuster bietet. Wenn der Benutzer jedoch darauf klickt, wird erneut ein Datum eingegeben.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment.html">Dateianhang</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/file">file</a></td>
   <td> Ermöglicht dem Benutzer die Auswahl einer oder mehrerer Dateien aus dem Gerätespeicher. Es unterstützt erweiterte Validierungen der Dateieingabe, wie z. B. akzeptierte Dateitypen, Dateigrößeneinschränkungen und minimale/maximale Dateiauswahlbeschränkungen. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/drop-down.html"> Dropdown-Liste</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select">auswählen</a></td>
   <td> Ermöglicht Benutzern die Auswahl einer oder mehrerer Optionen aus einer Liste vordefinierter Optionen. Die Optionen können vom Typ String, Number oder Boolean sein.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox-group.html">Kontrollkästchen-Gruppe</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox">Mehrfach-Kontrollkästchen</a></td>
   <td> Benutzer können eine oder mehrere Optionen aus einer Liste auswählen. Es werden mehrere Kontrollkästchen mit identischen Namen generiert, von denen jedes einem Element in der -Auflistung entspricht. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/radio-button.html">Optionsfeldgruppe</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/radio">mehrere Radios</a></td>
   <td> Ermöglicht einem Benutzer die Auswahl einer Option aus einer Gruppe verwandter Optionen. Es werden mehrere Optionsfelder mit identischen Namen generiert, von denen jeder einem Element in der Enumeration entspricht.</td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/button.html">Schaltfläche</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/button">Schaltfläche</a></td>
   <td>Ein UI-Element, über das Benutzer beim Klicken auf eine Aktion Trigger ausführen können. </td>
  </tr>
  <tr>
   <td><a href="" https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html">Bedienfeld</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset mit legend</a></td>
   <td> Gruppieren Sie Abschnitte in einem Formular, wobei ein verschachteltes Element *legend* eine Beschriftung für das Formular hinzufügt.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html?lang=de">Assistent</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset">fieldset</a></td>
   <td>Gruppiert verwandte Abschnitte in einem Formular. Es steuert auch die Anordnung und unterstützt Anzeigeoptionen, um sie oben oder links zu positionieren. </td>
  </tr>
    <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/text.html">Text</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/p">S</a></td>
   <td>Ein p -Tag markiert einen Absatz. Absätze im visuellen Inhalt sind Textblöcke, die durch leere Zeilen oder eine eingerückte erste Zeile getrennt sind</td>
  </tr>
     <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/submit-button.html">Schaltfläche „Senden“</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/submit">absenden</a></td>
   <td> Ein UI-Element, über das Benutzer ein Formular beim Klicken an den Server senden können. Wenn ein Benutzer einer Schaltfläche eine Regel zum Senden hinzufügt, fungiert sie als Senden-Schaltfläche. </td>
  </tr>
     <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/reset-button.html">Schaltfläche „Zurücksetzen“</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/reset">Zurücksetzen</a></td>
   <td>Ein UI-Element, das ein Formular beim Klicken zurücksetzt. Wenn ein Benutzer einer Schaltfläche eine Regel zum Zurücksetzen hinzufügt, fungiert sie als Zurücksetzen-Schaltfläche. </td>
  </tr>
    <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/email-input.html">Email Input</td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/email">email</a></td>
   <td> Ermöglicht dem Benutzer die Eingabe und Bearbeitung einer E-Mail-Adresse. Wenn der Benutzer mehrere Attribute hinzufügt, kann eine Liste mit E-Mail-Adressen hinzugefügt oder bearbeitet werden.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/telephone-input.html">Telefoneingabe</a></td>
   <td><a href ="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/tel">tel</a></td>
   <td>Ermöglicht die Eingabe und Bearbeitung einer Telefonnummer.</td>
  </tr>
   <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/header.html">Kopfzeile</td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/header"> Kopfzeile</a></td>
   <td>Es enthält einführende Inhalte, normalerweise eine Gruppe von Einführungszeichen oder Navigationshilfen. Sie wird außerhalb des Formular-Containers unterstützt. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/footer.html">Fußzeile</td>
   <td><a href = "https://developer.mozilla.org/en-US/docs/Web/HTML/Element/footer">Fußzeile</a></td>
   <td> Enthält Informationen wie Copyright-Daten oder Links zu verwandten Dokumenten. Sie wird außerhalb des Formular-Containers unterstützt.</td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html?lang=de">Akkordeon<a></td>
   <td><i>Noch nicht in Formularblock unterstützt</i></td>
   <td> Ermöglicht dem Benutzer das Erstellen erweiterbarer und ausblendbarer Abschnitte in einem Formular. </td>
  </tr>
  <tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html?lang=de">Horizontale Registerkarten</a></td>
   <td><i>Noch nicht in Formularblock unterstützt</i></td>
   <td>Organisiert mehrere Abschnitte eines Formulars in separate Registerkarten, die horizontal angezeigt werden.</td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/image.html">Bild</a></td>
   <td><i>Noch nicht in Formularblock unterstützt</i></td>
   <td> Ermöglicht dem Benutzer, Bilder in ein Formular einzuschließen.</td>
  </tr><tr>
   <td><a href ="https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/title.html">Titel</a></td>
   <td><i>Noch nicht in Formularblock unterstützt</i></td>
   <td> Bezieht sich auf den Text, der oben im Formular angezeigt wird. </td>
  </tr>
  <tr>
   <td><a href = "https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/submit-button.html">Schalter</td>
   <td><i>Noch nicht in Formularblock unterstützt</i></td>
   <td> Ein Umschalter mit zwei Status, mit dem Benutzer zwischen zwei Status auswählen können, z. B. das Aktivieren oder Deaktivieren einer Funktion, Einstellung oder Funktion.</td>
  </tr>
 </tbody>
</table>


