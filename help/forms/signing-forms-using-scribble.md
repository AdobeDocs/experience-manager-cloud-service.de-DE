---
title: Wie wende ich elektronische Signaturen auf ein Formular mithilfe von Freihandsignaturen an?
description: Lernen Sie, wie man elektronische Signaturen auf ein Formular mithilfe einer Freihandsignatur anwendet.
uuid: ffeba886-9b24-4ed1-95c0-e19356ff2f23
products: SG_EXPERIENCEMANAGER/FORMS
topic-tags: author
feature: Adaptive Forms, Foundation Components
exl-id: dc89ecb1-2d9e-4d1d-b85b-af90c550e7d8
role: User, Developer
source-git-commit: b5340c23f0a2496f0528530bdd072871f0d70d62
workflow-type: tm+mt
source-wordcount: '1318'
ht-degree: 97%

---

# E-Signieren eines Formulars mithilfe von Freihandsignaturen{#apply-electronic-signatures-to-a-form-using-deprecated-scribble-signatures}

>[!NOTE]
>
> Adobe empfiehlt die Verwendung der modernen und erweiterbaren Datenerfassung [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zum [Erstellen eines neuen adaptiven Forms](/help/forms/creating-adaptive-form-core-components.md) oder [Hinzufügen von adaptivem Forms zu AEM Sites-Seiten](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Forms mithilfe von Foundation-Komponenten beschrieben.

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/signing-forms-using-scribble.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |


Sie können die Komponente **Freihandsignatur** verwenden, um eine Signatur (per Freihandfunktion) in ein adaptives Formular zu schreiben. <!-- The Signature step component displays a PDF version of the Adaptive Form. You require a Document of Record option enabled or form template based Adaptive Forms to use the Signature step component. -->

![Dialogfeld für Freihandsignatur](assets/scribble-signature.png)

## Verfügbare Optionen im Signaturfenster

* **A:** Klicken Sie auf das **Pinselsymbol**, um Ihre Signatur auf der Arbeitsfläche zu zeichnen.
* **B:** Klicken Sie auf das Symbol **Löschen**, um die Signatur auf der Arbeitsfläche zu löschen.
* **C:** Klicken Sie auf das Symbol **Geolocation**, um die Geolocation zusammen mit der Signatur hinzuzufügen.
* **D:** Klicken Sie auf das **Tastatursymbol**, um Ihren Namen auf der Arbeitsfläche einzugeben.

Sobald Sie auf das Symbol „Fertig“ ![aem_forms_save](assets/aem_forms_save.png) im Freihandsignaturfenster klicken, können Sie die Signatur nicht mehr bearbeiten. Wenn Sie die Signatur bearbeiten möchten, müssen Sie die aktuelle Signatur ignorieren und mit der obigen Option „Pinsel“/„Tastatur“ erneut signieren.

Sie können auf das Symbol **Konfigurieren** ![configure icon](assets/configure.png) klicken, um das Seitenverhältnis der Arbeitsfläche für Freihandsignaturen festzulegen.
* Wenn das Seitenverhältnis der Arbeitsfläche für Freihandsignaturen kleiner als 1 ist, werden die Geolocation-Informationen am unteren Rand der Arbeitsfläche für die Freihandsignatur hinzugefügt.


* Wenn das Seitenverhältnis der Arbeitsfläche für Freihandsignaturen größer als 1 ist, werden die Geolocation-Informationen auf der rechten Seite der Arbeitsfläche für Freihandsignaturen hinzugefügt.


![scribble signature-bottom](assets/scribble-signature-aspectratio.PNG)



>[!NOTE]
>
>Signaturen werden immer im PNG-Format gespeichert.
>

## Konfigurieren eines adaptiven Formulars zur Verwendung der Freihandsignatur {#configure-an-adaptive-form-to-use-scribble-signature}

1. Öffnen Sie ein adaptives Formular im Bearbeitungsmodus.
1. Ziehen Sie die Komponente **Freihandsignatur** aus dem Komponenten-Browser in das adaptive Formular.
1. Klicken Sie auf das Symbol **Konfigurieren** ![configure](assets/configure.png). Dadurch wird der Eigenschaften-Browser geöffnet und es werden die Eigenschaften der Komponente „Freihandsignatur“ angezeigt. [Konfigurieren Sie die Eigenschaften der Freihandsignatur](#properties-of-scribble-signature-component), wie im nächsten Abschnitt beschrieben.

   ![Freihandsignatur](/help/forms/assets/scribblesig.png)

1. Wählen Sie das Symbol „Fertig“ ![aem_forms_save](assets/aem_forms_save.png) aus, um die Änderungen zu speichern. Die Signatur wurde erfolgreich konfiguriert.

## Konfigurieren Sie die Eigenschaften der Komponente „Freihandsignatur“.

Im Dialogfeld „Konfigurieren“ können Sie die Komponente „Freihandsignatur“ für Besuchende ganz einfach anpassen.

### Registerkarte „Allgemein“

![Registerkarte „Allgemein“](/help/forms/assets/scribblesig-basic.png)

* **Name**: Sie können eine Formularkomponente sowohl im Formular als auch im Regeleditor durch ihren eindeutigen Namen identifizieren. Der Name darf keine Leerzeichen oder Sonderzeichen enthalten.

* **Titel**: Mit dem Titel können Sie eine Komponente in einem Formular leicht identifizieren. Standardmäßig wird der Titel oberhalb der Komponente angezeigt. Wenn Sie keinen Titel hinzufügen, wird der Name der Komponente anstelle des Titeltexts angezeigt.

* **Rich-Text für Titel zulassen**: Diese Funktionen ermöglichen es Benutzenden, einfache Texttitel zu formatieren, die Funktionen wie fett, kursiv, unterstrichener Text, verschiedene Schriftarten, Schriftgrößen, Farben und zusätzliche Optionen enthalten und so die visuelle Darstellung und Anpassung zu verbessern. Sie bietet mehr Flexibilität und kreative Kontrolle bei der Hervorhebung von Titeln in Dokumenten, Websites oder Anwendungen.\
  Durch Aktivieren des Kontrollkästchens **Rich-Text für Titel zulassen** werden Formatierungsoptionen sichtbar, mit denen Sie den Titel der Komponente gestalten können. Um auf alle verfügbaren Formatierungsoptionen zuzugreifen, können Sie auf die Registerkarte ![Vollbildsymbol](/help/forms/assets/fullscreen-icon.png) klicken.

  ![Rich-Text-Unterstützung](/help/forms/assets/richtext-support-title.png)

* **Titel ausblenden**: Wählen Sie die Option aus, um den Titel der Komponente auszublenden.
* **Erforderliches Feld**: Wählen Sie diese Option aus, um das Feld als Pflichtfeld festzulegen.
* **Meldung zu erforderlichem Feld**: Die **Meldung zu erforderlichem Feld** ist eine anpassbare Meldung, die Benutzenden angezeigt wird, wenn sie versuchen, ein Formular zu senden, ohne ein Pflichtfeld auszufüllen.
* **Datenmodell-Objektverweis**: Ein Objekt- oder Bindungsverweis referenziert ein Datenelement, das in einer externen Datenquelle gespeichert ist und in einem Formular verwendet wird. Sie können mit dem Bindungsverweis Daten dynamisch an Formularfelder binden, sodass das Formular die aktuellsten Daten aus der Datenquelle anzeigen kann. Beispielsweise kann ein Bindungsverweis verwendet werden, um den Namen und die Adresse von Kundinnen und Kunden in einem Formular anzuzeigen, basierend auf der im Formular eingegebenen Kunden-ID. Der Bindungsverweis kann auch verwendet werden, um die Datenquelle mit den im Formular eingegebenen Daten zu aktualisieren. Auf diese Weise können Sie mit AEM Forms Formulare erstellen, die mit externen Datenquellen interagieren und so eine nahtlose Benutzererfahrung bei der Datenerfassung und Datenverwaltung bieten.
* **Objekt ausblenden**: Wählen Sie diese Option aus, um die Komponente im Formular auszublenden. Die Komponente bleibt für andere Zwecke verfügbar, z. B. für Berechnungen im Regel-Editor. Dies ist nützlich, wenn Sie Informationen speichern müssen, die Benutzende nicht sehen oder direkt ändern müssen.
* **Objekt deaktivieren**: Wählen Sie diese Option aus, um die Komponente zu deaktivieren. Die deaktivierte Komponente ist nicht aktiv und Endbenutzende können sie nicht bearbeiten. Benutzende können den Wert des Felds anzeigen, ihn jedoch nicht ändern. Die Komponente bleibt für andere Zwecke verfügbar, z. B. für Berechnungen im Regel-Editor.
* **Seitenverhältnis**: Das Seitenverhältnis in einer Komponente „Freihandsignatur“ definiert die proportionale Beziehung zwischen Breite und Höhe.
* **Feld-Layout**: Die Option **Feld-Layout** bestimmt, wie Formularelemente, einschließlich Labels (Beschriftungen) und Fehlermeldungen, relativ zur Komponente positioniert werden. Mit **Beschriftung und Fehler oben im Widget** werden die Beschriftung (das Label) des Felds und Fehlermeldungen über der Komponente positioniert. Die Option **Aus Konfiguration des adaptiven Formulars übernehmen** nutzt für das Layout der Felder die standardmäßigen Einstellungen, die in der Konfiguration des adaptiven Formulars angegeben sind.
* **CSS-Klasse**: Mit der **CSS-Klasse** können Sie benutzerdefinierte Stile auf eine Komponente anwenden, indem Sie eine oder mehrere in Ihrem Stylesheet definierte CSS-Klassen zuweisen. Sie ermöglicht eine konsistente Formatierung und Layout-Anpassung im gesamten adaptiven Formular.

### Hilfe-Inhalt

![Registerkarte „Hilfe-Inhalt“](/help/forms/assets/scribblesig-help.png)

* **Kurzbeschreibung**: Eine Kurzbeschreibung ist eine kurze Erklärung, die zusätzliche Informationen oder Klarstellungen über den Zweck eines Formularfelds bietet. Es hilft Benutzenden zu verstehen, welcher Datentyp in das Feld eingegeben werden soll, und kann Richtlinien oder Beispiele bereitstellen, um sicherzustellen, dass die eingegebenen Informationen gültig sind und die gewünschten Kriterien erfüllen. Standardmäßig bleiben kurze Beschreibungen ausgeblendet. Aktivieren Sie die Option **Kurzbeschreibung immer anzeigen**, um sie unterhalb der Komponente anzuzeigen.

* **Kurzbeschreibung immer anzeigen**: Aktivieren Sie diese Option, um die Kurzbeschreibung unterhalb der Komponente anzuzeigen.

* **Lange Beschreibung**: Diese bezieht sich auf zusätzliche Informationen oder Anleitungen, die den Benutzenden bereitgestellt werden, um sie beim korrekten Ausfüllen eines Formularfelds zu unterstützen. Sie erscheint, wenn Benutzende auf das Hilfesymbol (i) neben der Komponente klicken. Sie enthält detailliertere Informationen als der Label- oder Platzhaltertext eines Formularfelds und soll den Benutzenden dabei helfen, die Anforderungen oder Einschränkungen des Felds zu verstehen. Er kann auch Vorschläge oder Beispiele anbieten, um das Ausfüllen des Formulars einfacher und genauer zu gestalten.

### Registerkarte „Barrierefreiheit“ {#accessibility}

![Registerkarte „Barrierefreiheit“](/help/forms/assets/scribblesig-acc.png)

Auf der Registerkarte **„Barrierefreiheit“** werden Werte für [ARIA-Barrierefreiheitsbeschriftungen](https://www.w3.org/WAI/standards-guidelines/aria/) für die Komponente festgelegt. Es stehen verschiedene Optionen zur Verfügung für die Verwendung des Textes für die Bildschirmlesehilfe:

* **Bildschirmlesehilfen-Rangfolge**: Die Bildschirmlesehilfen-Rangfolge bezieht sich auf zusätzlichen Text, der von Hilfstechnologien wie etwa Bildschirmlesehilfen für sehbehinderte Personen vorgelesen wird. Dieser Text enthält eine Audiobeschreibung des Zwecks des Formularfelds und kann Informationen über den Titel, die Beschreibung, den Namen und alle relevanten Nachrichten (benutzerdefinierten Text) des Felds enthalten. Der Text der Bildschirmlesehilfe hilft sicherzustellen, dass das Formular allen Benutzenden zugänglich ist, auch Personen mit Sehschwäche, und bietet ihnen ein umfassendes Verständnis des Formularfelds und seiner Anforderungen.

   * **Benutzerdefinierter Text**: Wählen Sie diese Option aus, um den benutzerdefinierten Text für ARIA-Barrierefreiheitsbeschriftungen zu verwenden. Wenn Sie diese Option auswählen, wird das Benutzerdefinierter Dialogfeld „Text“ angezeigt. Sie können relevante Informationen im Benutzerdefinierter Dialogfeld „Text“ hinzufügen.
   * **Kurzbeschreibung**: Wählen Sie diese Option aus, um die Beschreibung für ARIA-Barrierefreiheitsbeschriftungen zu verwenden.
   * **Titel**: Wählen Sie diese Option aus, um den Titel für ARIA-Barrierefreiheitsbeschriftungen zu verwenden.
   * **Name**: Wählen Sie diese Option aus, um den Namen für ARIA-Barrierefreiheitsbeschriftungen zu verwenden.
   * **Keine**: Wählen Sie diese Option aus, wenn Sie keine ARIA-Barrierefreiheitsbezeichnungen hinzufügen möchten.

<!--

 * **Element Name**: Specify name of the component.

    * **Title:** Specify unique title of the component.
    * **Template message:** Specify the message to be displayed while the signature PDF is being loaded. Adobe Sign services take some time to prepare and load signature PDF.
    * **Signing Service:** Select the **Scribble Signature** option.

    * **CSS Class**: Specify CSS class of the client library, if any. Adobe recommends using [themes](themes.md) and [in-line styles](inline-style-adaptive-forms.md) instead of CSS Class.
## Sign an Adaptive Form using Scribble Signature {#sign-an-adaptive-form-using-scribble-signature}

1. After you fill an Adaptive Form and reach the Signature Step page, the signature screen is displayed.

   ![Signature screen for EchoSign page](assets/esignscribblesign.jpg)

1. Click **[!UICONTROL Sign]**. The scribble sign dialog appears. Sign the form and click the Done ![aem_forms_save](assets/aem_forms_save.png) icon to save the signature.

   ![Scribble sign dialog](assets/scribblewidget.png)

1. Click complete to finish the signing process.

   ![Complete the signing process](assets/scribblecomplete.jpg)

The signatures are added to the form and the form control moves to the next panel. -->

## Siehe auch {#see-also}

{{see-also}}