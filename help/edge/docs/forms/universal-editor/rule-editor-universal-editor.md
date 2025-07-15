---
title: Wie kann der Regeleditor verwendet werden, um Regeln auf Formularfelder anzuwenden und so dynamisches Verhalten und komplexe Logik für Formulare zu ermöglichen, die mit WYSIWYG-Authoring erstellt wurden?
description: Der Regeleditor im universellen Editor ermöglicht es Ihnen, ohne Programmierung oder Skripterstellung ein dynamisches Verhalten und komplexe Logik in Ihre Formulare zu integrieren.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 846f56e1-3a98-4a69-b4f7-40ec99ceb348
source-git-commit: e1ead9342fadbdf82815f082d7194c9cdf6d799d
workflow-type: tm+mt
source-wordcount: '2253'
ht-degree: 98%

---


# Einführung in den Regeleditor im WYSIWYG-Authoring

<span class="preview"> Diese Funktion ist über das Early-Access-Programm verfügbar. Um den Zugriff anzufordern, senden Sie eine E-Mail mit dem Namen Ihrer GitHub-Organisation und dem Namen des Repositorys von Ihrer offiziellen Adresse an <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a>. Wenn die Repository-URL beispielsweise https://github.com/adobe/abc lautet, lautet der Name der Organisation „adobe“ und der Name des Repositorys „abc“.</span>


Sie können ein dynamisches Formularverhalten mit dem Regeleditor hinzufügen, mit dem Sie Regeln erstellen können. Diese Regeln ermöglichen eine bedingte Sichtbarkeit von Feldern oder die Automatisierung von Berechnungen auf der Grundlage von Benutzereingaben, was das allgemeine Anwendererlebnis verbessert. Durch das Optimieren der Formularausfüllung trägt der Regeleditor zur Genauigkeit und Effizienz bei.

Der Regeleditor bietet eine intuitive visuelle Benutzeroberfläche zum Erstellen und Verwalten von Regeln. Sein anwenderfreundlicher Ansatz macht ihn für alle Benutzenden zugänglich, auch für diejenigen ohne umfangreiches technisches Fachwissen, sodass sie mühelos Logik in ihren Formularen implementieren können.

## Grundlegendes zu Regeln

Regeln sind Anweisungen, die den Benutzenden Anleitungen geben, welche Aktionen unter bestimmten Bedingungen ausgeführt werden sollen.

* **Bedingung**: Eine Bedingung ist eine Prüfung oder Regel, die auswertet, ob etwas erfüllt oder nicht erfüllt ist. Sie beantwortet die Frage: „Erfüllt dies die Anforderung?“

* **Aktion**: Eine Aktion erfolgt, wenn die Bedingung erfüllt ist. Es handelt sich um die Aufgabe oder das Verhalten, die bzw. das durch die Auswertung der Bedingung ausgelöst wird.

Eine Regel folgt normalerweise einem der folgenden Konstrukte:

* **Bedingung-Aktion**: Zuerst wird eine Bedingung geprüft und dann eine Aktion durchgeführt. Im Regeleditor wird das Konstrukt `condition-action` durch den Regeltyp `When` erzwungen.
* **Aktion-Bedingung**: Zuerst wird eine Aktion durchgeführt und dann eine Bedingung geprüft. Die Regeltypen `Set Value Of` und `Validate` im Regeleditor erzwingen das Konstrukt `action-condition`.
* **Aktion-Bedingung-alternative Aktion**: Es wird eine Aktion ausgeführt, eine Bedingung geprüft und dann basierend auf der Bedingung entweder die Hauptaktion oder eine alternative Aktion ausgeführt. Die alternative Aktion für `Show` ist beispielsweise standardmäßig `Hide` und für `Enable` ist sie `Disable`.

Eine Bedingung könnte beispielsweise überprüfen, ob jemand einen bestimmten Wert in ein Feld eingegeben hat, und die Aktion könnte darin bestehen, ein Feld ein- oder auszublenden.
* **Bedingung**: Es wird überprüft, ob das Einkommen mehr als 50.000 US-Dollar beträgt.
* **Aktion**: Wenn die Bedingung erfüllt ist, wird das Feld `Additional Deduction` angezeigt; andernfalls wird die alternative Aktion ausgeführt, nämlich das Feld `Additional Deduction` auszublenden.

Detaillierte Schritt-für-Schritt-Anweisungen finden Sie unter [Hinzufügen einer bedingten Regel](#2-add-a-conditional-rule).

## Wie wird die Erweiterung des Regeleditors aktiviert?

Im universellen Editor ist die Regeleditor-Erweiterung nicht standardmäßig aktiviert. Um die Regeleditor-Erweiterung zu aktivieren, schreiben Sie uns über Ihre offizielle E-Mail-ID an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com).

Nachdem die Erweiterung des Regeleditors für Ihre Umgebung aktiviert wurde, wird das Symbol ![Regeln bearbeiten](/help/forms/assets/edit-rules-icon.svg) in der oberen rechten Ecke des Editors angezeigt.

![Regeleditor des universellen Editors](/help/edge/docs/forms/assets/universal-editor-rule-editor.png)

Wählen Sie die Formularkomponente aus, für die Sie eine Regel schreiben möchten, und klicken Sie auf das Symbol ![Regeln bearbeiten](/help/forms/assets/edit-rules-icon.svg). Die Benutzeroberfläche des Regeleditors wird angezeigt.

![Benutzeroberfläche des Regeleditors](/help/edge/docs/forms/assets/rule-editor-for-field.png)

In diesem Artikel werden `form object` und `form component` synonym verwendet.

Jetzt können Sie mit dem Schreiben von Regeln oder Geschäftslogik für das ausgewählte Formularfeld beginnen, indem Sie die [verfügbaren Regeltypen im Regeleditor](#available-rule-types-in-rule-editor) verwenden.

## Grundlegendes zur Benutzeroberfläche des Regeleditors

Der Editor des Regeleditors wird geöffnet, wenn Sie auf das Symbol ![Regeln bearbeiten](/help/forms/assets/edit-rules-icon.svg) klicken:

![Benutzeroberfläche des Regeleditors](/help/edge/docs/forms/assets/rule-editor-interface.png)

<table border="1">
  <thead>
    <tr>
      <th>Komponente des Regeleditors</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1. Titel</td>
      <td>Zeigt den Titel der Formularkomponente und den ausgewählten Regeltyp an. Beispielsweise ist „Bruttogehalt eingeben“ eine Textfeldkomponente, für die der Regeltyp „Wann“ ausgewählt ist. </td>
    </tr>
    <tr>
      <td>2. Formularobjekte und Funktionen</td>
      <td>Die Registerkarte <b>Formularobjekte</b> zeigt eine hierarchische Ansicht aller Komponenten an, die im Formular enthalten sind. Die Registerkarte <b>Funktionen</b> enthält eine Reihe integrierter Funktionen im Regeleditor.</td>
    </tr>
    <tr>
      <td>3. Umschalten zwischen Formularobjekten und Funktionen</td>
      <td>Ein Klick auf die Umschaltfläche blendet die Bereiche für Formularobjekte und Funktionen abwechselnd ein und aus. </td>
    </tr>
    <tr>
      <td>4. Visueller Regeleditor</td>
      <td>Der visuelle Regeleditor ist die Oberfläche, auf der Sie Regeln für die Formularkomponenten erstellen können.</td>
    </tr>
    <tr>
      <td>5. Schaltflächen „Fertig“ und „Abbrechen“</td>
      <td>Die Schaltfläche <b>Fertig</b> wird verwendet, um eine Regel zu speichern. Über die Schaltfläche <b>Abbrechen</b> verwerfen Sie alle Änderungen, die Sie an einer Regel vorgenommen haben, und der Regeleditor wird geschlossen.</td>
    </tr>
  </tbody>
</table>

Wenn Sie die Komponente auswählen, werden alle vorhandenen Regeln für eine Formularkomponente aufgelistet. Sie können den Titel und eine Vorschau der Regelzusammenfassung im Regeleditor anzeigen. Außerdem können Sie die Reihenfolge der Regeln ändern, Regeln bearbeiten, Regeln aktivieren/deaktivieren oder Regeln löschen.

![Anzeigen der verfügbaren Regeln eines Formularobjekts](/help/edge/docs/forms/assets/rule-editor15.png)

## Verfügbare Regeltypen

Der Regeleditor bietet eine Reihe vordefinierter Regeltypen, mit denen Sie Regeln schreiben können, wie in der nachfolgenden Tabelle zu sehen: 

<table border="1">
  <thead>
    <tr>
      <th>Regeltyp</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Wert festlegen</td>
      <td>Legt den Wert einer Formularkomponente in Abhängigkeit davon fest, ob die angegebene Bedingung erfüllt ist oder nicht.</td>
    </tr>
    <tr>
      <td>Wert löschen von</td>
      <td>Löscht den Wert der angegebenen Formularkomponente.</td>
    </tr>
    <tr>
      <td>Ausblenden/Anzeigen</td>
      <td>Blendet eine Formularkomponente in Abhängigkeit davon aus oder ein, ob eine Bedingung erfüllt ist oder nicht.</td>
    </tr>
    <tr>
      <td>Aktivieren/Deaktivieren</td>
      <td>Aktiviert oder deaktiviert eine Formularkomponente in Abhängigkeit davon, ob eine Bedingung erfüllt ist oder nicht.</td>
    </tr>
    <tr>
      <td>Validieren</td>
      <td>Überprüft die Formularkomponente auf Grundlage einer Bedingung und zeigt einen Fehler an, wenn die Bedingung nicht erfüllt ist. </td>
    </tr>
    <tr>
      <td>Wenn</td>
      <td>Gibt eine auszuwertende Bedingung an und dann eine Aktion, die ausgelöst werden soll, wenn die Bedingung erfüllt ist. Folgt dem Aktionsregelkonstrukt <i>Bedingung-Aktion-Alternative</i> oder dem Regelkonstrukt <i>Bedingung-Aktion</i>. </td>
    </tr>
    <tr>
      <td>Format</td>
      <td> Ändert den Anzeigewert der Formularkomponente mithilfe des angegebenen Ausdrucks, wenn sich ihr Wert ändert.</td>
    </tr>
    <tr>
      <td>Dienst aufrufen</td>
      <td>Ruft einen Dienst auf, der mithilfe externer APIs, eines Formulardatenmodells oder RESTful-Web-Diensten konfiguriert wurde.</td>
    </tr>
    <tr>
      <td>Eigenschaft festlegen</td>
      <td>Legt den Wert einer Eigenschaft der angegebenen Formularkomponente in Abhängigkeit von einer Bedingung fest.</td>
    </tr>
    <tr>
      <td>Fokus festlegen</td>
      <td>Legt den Eingabefokus auf die angegebene Formularkomponente.</td>
    </tr>
    <tr>
      <td>Formular speichern</td>
      <td>Ermöglicht es Benutzenden, das Formular mithilfe der Formularportalkomponente für Entwürfe und Übermittlungen als Entwurf zu speichern. </td>
    </tr>
    <tr>
      <td>Formular senden</td>
      <td>Sendet das Formular.</td>
    </tr>
    <tr>
      <td>Formular zurücksetzen</td>
      <td>Setzt das Formular zurück.</td>
    </tr>
    <tr>
      <td>Instanz hinzufügen/entfernen</td>
      <td>Fügt eine Instanz des angegebenen wiederholbaren Bereichs oder der Tabellenzeile hinzu oder entfernt diese.</td>
    </tr>
    <tr>
      <td>Navigieren zu</td>
      <td>Navigiert zu anderen adaptiven Formularen, anderen Assets wie Bildern oder Dokumentfragmenten oder zu einer externen URL.</td>
    </tr>
    <tr>
      <td>Dispatch-Ereignis</td>
      <td>Löst bestimmte Aktionen in Abhängigkeit von vordefinierten Bedingungen oder Ereignissen aus.</td>
    </tr>
    <tr>
      <td>Zwischen Panels navigieren</td>
      <td>Ermöglicht eine Fokusverschiebung zwischen verschiedenen Bedienfeldern in einem Formular.</td>
    </tr>
  </tbody>
</table>


Sehen wir uns nun an, wie [Regeln im Regeleditor geschrieben werden](#write-rules).

## Schreiben von Regeln

Um zu verstehen, wie Regeln im visuellen Regeleditor geschrieben werden, sehen wir uns ein einfaches Beispiel für ein Steuerberechnungsformular an:

![Screenshot der Benutzeroberfläche des Regeleditors, der die Erstellung einer bedingten Regel mit Wenn-Dann-Logik für die Sichtbarkeit des Formularfelds zeigt](/help/edge/docs/forms/assets/rule-editor-1.png)

In der oben beschriebenen Form geben Benutzende das Bruttogehalt ein. Basierend auf dieser Eingabe wird ein bedingtes Feld angezeigt und die fällige Steuer berechnet.

**Formularfelder:**
* Bruttogehalt (Benutzereingabe)
* Zusätzlicher Abzug (bedingtes Feld)
* Steuerpflichtiges Einkommen (berechnetes Feld)
* Zu zahlende Steuer (berechnetes Feld)

**Bedingte Regel:**
* Bedingung: Bruttogehalt > 50.000
* Aktion: Feld „Zusätzlicher Abzug“ anzeigen

**Berechnungsregeln:**

* Steuerpflichtiges Einkommen = Bruttogehalt - zusätzlicher Abzug (falls zutreffend)
* Zu zahlende Steuer = Steuerpflichtiges Einkommen * Steuersatz (nehmen wir zur Einfachheit einen festen Satz von 10 % an)

Gehen Sie wie folgt vor, um Regeln zu erstellen:

### &#x200B;1. Formular erstellen

So erstellen Sie ein Formular im universellen Editor:

1. Öffnen Sie ein Formular im universellen Editor zur Bearbeitung.
1. Fügen Sie die folgenden Formularkomponenten hinzu:
   * Steuerberechnungsformular (Titel)
   * Bruttogehalt (Zahleneingabe)
   * Zusätzlicher Abzug (Zahleneingabe)
   * Steuerpflichtiges Einkommen (Zahleneingabe)
   * Zu zahlende Steuer (Zahleneingabe)
   * Senden (Schaltfläche „Senden“)
1. Blenden Sie das Formularfeld `Additional Deduction` aus, indem Sie dessen `Properties` öffnen.

   ![Screenshot eines Steuerberechnungsformulars mit Eingabefeldern für Bruttogehalt, Familienstand und unterhaltsberechtigte Kinder, auf denen die Formularstruktur vor der Anwendung von Regeln veranschaulicht wird](/help/edge/docs/forms/assets/rule-editor2.png)

### &#x200B;2. Eine bedingte Regel für ein Formularfeld hinzufügen

Nachdem Sie das Formular erstellt haben, schreiben Sie die erste Regel, damit das Feld `Additional Deduction` nur angezeigt wird, wenn das Bruttogehalt 50.000 US-Dollar überschreitet. So fügen Sie eine bedingte Regel hinzu:

1. Öffnen Sie ein Formular im universellen Editor zur Bearbeitung und wählen Sie in der Inhaltsstruktur das Feld **[!UICONTROL Bruttogehalt]** und dann ![Regeln bearbeiten](/help/forms/assets/edit-rules-icon.svg) aus. Alternativ können Sie das Feld **[!UICONTROL Bruttogehalt]** direkt im Bereich **[!UICONTROL Formularobjekt]** auswählen.
   ![Beispiel1 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor3.png)
Die Benutzeroberfläche des visuellen Regeleditors wird angezeigt.
1. Klicken Sie auf **[!UICONTROL Erstellen]**, um Regeln zu erstellen.
   ![Beispiel2 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor4.png)
Standardmäßig ist der Regeltyp `Set Value Of` ausgewählt. Sie können zwar das ausgewählte Objekt nicht bearbeiten oder ändern, es ist jedoch möglich, über die Dropdown-Liste für Regeln einen anderen Regeltyp auszuwählen.\
   ![Beispiel3 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor5.png)
1. Öffnen Sie die Dropdown-Liste „Regeltyp“ und wählen Sie den Regeltyp **[!UICONTROL Wenn]** aus.
   ![Beispiel4 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor6.png)
1. Wählen Sie die Dropdown-Liste **[!UICONTROL Status auswählen]** und wählen Sie dann **[!UICONTROL Ist größer als]**. Das Feld **[!UICONTROL Zahl eingeben]** wird angezeigt.
   ![Beispiel5 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor7.png)
1. Geben Sie im Feld **[!UICONTROL Zahl eingeben]** in der Regel `50000` ein.
   ![Beispiel6 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor8.png)
Sie haben die Bedingung als `When Gross Salary is greater than 50000` definiert. Definieren Sie anschließend die Aktion, die ausgeführt werden soll, wenn diese Bedingung `True` ist.
1. Wählen Sie in der Anweisung `Then` aus der Dropdown-Liste **[!UICONTROL Aktion auswählen]** die Option **[!UICONTROL Anzeigen]** aus.
   ![Beispiel7 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor9.png)
1. Ziehen Sie das Feld **[!UICONTROL Zusätzlicher Abzug]** aus der Registerkarte „Formularobjekte“ in das Feld **[!UICONTROL Objekt hier einfügen oder auswählen]**. Stattdessen können Sie auch das Feld **[!UICONTROL Objekt hier einfügen oder auswählen]** auswählen und das Feld **[!UICONTROL Zusätzlicher Abzug]** aus dem Popup-Menü wählen, in dem sämtliche Formularobjekte im Formular aufgeführt sind.
   ![Beispiel8 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor10.png)
1. Klicken Sie auf **[!UICONTROL Abschnitt „Andernfalls“ hinzufügen]**, um eine weitere Bedingung für das Feld **[!UICONTROL Bruttogehalt]** hinzuzufügen, falls ein Gehalt von weniger als `50000` eingegeben wird.
   ![Beispiel9 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor11.png)
1. Wählen Sie in der Anweisung `Else` aus der Dropdown-Liste **[!UICONTROL Aktion auswählen]** die Option **[!UICONTROL Ausblenden]** aus.
   ![Beispiel10 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor12.png)
1. Ziehen Sie das Feld **[!UICONTROL Zusätzlicher Abzug]** aus der Registerkarte „Formularobjekte“ in das Feld **[!UICONTROL Objekt hier einfügen oder auswählen]**. Stattdessen können Sie auch das Feld **[!UICONTROL Objekt hier einfügen oder auswählen]** auswählen und das Feld **[!UICONTROL Zusätzlicher Abzug]** aus dem Popup-Menü wählen, in dem sämtliche Formularobjekte im Formular aufgeführt sind.
   ![Beispiel11 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor13.png)
1. Wählen Sie **[!UICONTROL Fertig]** aus, um die Regel zu speichern.
Die Regel wird im Regeleditor wie folgt angezeigt.
   ![Beispiel12 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor14.png)

>[!NOTE]
>
> Alternativ können Sie dieses Verhalten auch implementieren, indem Sie eine Anzeige-Regel für das Feld „Zusätzlicher Abzug“ anstelle einer Wenn-Regel für das Feld „Bruttogehalt“ erstellen.

### &#x200B;3. Hinzufügen von Berechnungsregeln für die Formularfelder

Als Nächstes schreiben Sie eine Regel, um das `Taxable Income` zu berechnen. Dies ist die Differenz zwischen `Gross Salary` und `Additional Deduction` (falls vorhanden). Um eine Berechnungsregel für das Feld **[!UICONTROL Steuerpflichtiges Einkommen]** hinzuzufügen, führen Sie die folgenden Schritte aus:

1. Wählen Sie im Autorenmodus das Feld **[!UICONTROL Steuerpflichtiges Einkommen]** und dann das Symbol ![Regeln bearbeiten](/help/forms/assets/edit-rules-icon.svg) aus. Alternativ können Sie das Feld **[!UICONTROL Steuerpflichtiges Einkommen]** direkt im Bereich **[!UICONTROL Formularobjekt]** auswählen.
1. Wählen Sie dann **[!UICONTROL Erstellen]** aus, um die Regel zu erstellen.
   ![Beispiel13 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor16.png)
1. Wählen Sie **[!UICONTROL Option auswählen]** und dann **[!UICONTROL Mathematischer Ausdruck]** aus. Ein Feld, in das Sie mathematische Ausdrücke schreiben können, wird geöffnet.
   ![Beispiel14 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor17.png)

1. Gehen Sie im Feld „Mathematischer Ausdruck“ wie folgt vor:

   * Wählen Sie das Feld **[!UICONTROL Bruttogehalt]** auf der Registerkarte „Formularobjekt“ aus oder ziehen Sie es in das erste Feld **[!UICONTROL Objekt hier einfügen oder auswählen]**.

   * Wählen Sie **[!UICONTROL Minus]** aus dem Feld **[!UICONTROL Operator wählen]**.

   * Wählen Sie das Feld **[!UICONTROL Zusätzlicher Abzug]** auf der Registerkarte „Formularobjekt“ aus oder ziehen Sie es in das andere Feld **[!UICONTROL Objekt hier einfügen oder auswählen]**.
     ![Beispiel15 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor18.png)

1. Wählen Sie **[!UICONTROL Fertig]** aus, um die Regel zu speichern.

   Fügen Sie nun eine Regel für das Feld `Tax Payable ` hinzu, das durch die Multiplikation des steuerpflichtigen Einkommens mit dem Steuersatz bestimmt wird. Zur Einfachheit nehmen wir einen festen Steuersatz von `10%` an.

1. Wählen Sie im Autorenmodus das Feld **[!UICONTROL Steuerpflichtiges Einkommen]** und dann das Symbol ![Regeln bearbeiten](/help/forms/assets/edit-rules-icon.svg) aus. Wählen Sie anschließend **[!UICONTROL Erstellen]** aus, um Regeln zu erstellen.
   ![Beispiel16 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor19.png)
1. Wählen Sie **[!UICONTROL Option auswählen]** und dann **[!UICONTROL Mathematischer Ausdruck]** aus. Ein Feld, in das Sie mathematische Ausdrücke schreiben können, wird geöffnet.
   ![Beispiel17 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor20.png)
1. Gehen Sie im Feld „Mathematischer Ausdruck“ wie folgt vor:

   * Wählen Sie das Feld **[!UICONTROL Steuerpflichtiges Einkommen]** auf der Registerkarte „Formularobjekt“ aus oder ziehen Sie es in das erste Feld **[!UICONTROL Objekt hier einfügen oder auswählen]**.

   * Wählen Sie **[!UICONTROL Multipliziert mit]** aus dem Feld **[!UICONTROL Operator wählen]**.

   * Wählen Sie **Zahl** aus dem Feld **[!UICONTROL Option auswählen]** und geben Sie den Wert als `10` in das Feld **[!UICONTROL Zahl eingeben]** ein.
     ![Beispiel18 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor21.png)
1. Klicken Sie als Nächstes in den hervorgehobenen Bereich um das Ausdrucksfeld und wählen Sie dann **[!UICONTROL Ausdruck erweitern]** aus.
   ![Beispiel19 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor22.png)
1. Wählen Sie im Feld für den erweiterten Ausdruck im Feld **[!UICONTROL Operator auswählen]** die Option **[!UICONTROL geteilt durch]** und im Feld **[!UICONTROL Option auswählen]** die Option **[!UICONTROL Zahl]** aus. Geben Sie `100` in das Zahlenfeld ein.
   ![Beispiel20 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor23.png)
1. Wählen Sie **[!UICONTROL Fertig]** aus, um die Regel zu speichern.

### &#x200B;4. Anzeigen der Vorschau eines Formulars

Wenn Sie jetzt das Formular in der Vorschau anzeigen und das **Bruttogehalt** als `60,000` eingeben, wird das Feld **Zusätzlicher Abzug** angezeigt und **Steuerpflichtiges Einkommen** und **Zu zahlende Steuer** werden entsprechend berechnet.

![Auswählen eines Formulars](/help/edge/docs/forms/assets/rule-editor-form.png)

Zusätzlich zu den vorkonfigurierten Funktionen wie Summe und Durchschnitt, die unter „Funktionsausgabe“ aufgeführt sind, können Sie auch [benutzerdefinierte Funktionen](#create-a-custom-function) erstellen, um komplexe Geschäftslogik zu implementieren. 

## Benutzerdefinierte Funktion im Regeleditor

Edge Delivery Services Forms unterstützt benutzerdefinierte Funktionen, mit denen Benutzende JavaScript-Funktionen für die Implementierung komplexer Geschäftsregeln definieren können. Die benutzerdefinierten Funktionen erweitern die Funktionen von Formularen, indem sie die Bearbeitung und Verarbeitung der eingegebenen Daten erleichtern, um bestimmten Anforderungen gerecht zu werden. 

### Erstellen einer benutzerdefinierten Funktion

Um eine benutzerdefinierte Funktion zu erstellen, bearbeiten Sie die Datei `../[blocks]/form/functions.js`. Der Erstellungsprozess umfasst im Allgemeinen die folgenden Schritte:

* **Funktionsdeklaration**: Definieren Sie den Funktionsnamen und die zugehörigen Parameter (die Eingaben, die akzeptiert werden).
* **Logikimplementierung**: Schreiben Sie den Code, der die spezifischen Berechnungen oder Manipulationen beschreibt, die von der Funktion ausgeführt werden.
* **Funktionsexport**: Ermöglichen Sie, dass die Funktion innerhalb Ihrer Regeln zugänglich ist, indem Sie sie aus der entsprechenden Datei exportieren.


In diesem Beispiel werden zwei benutzerdefinierte Funktionen veranschaulicht, nämlich `getFullName` und `days`:

```JavaScript
/**
 * Get Full Name
 * @name getFullName Concats first name and last name
 * @param {string} firstname in Stringformat
 * @param {string} lastname in Stringformat
 * @return {string}
 */
function getFullName(firstname, lastname) {
  return `${firstname} ${lastname}`.trim();
}

/**
 * Calculate the number of days between two dates.
 * @param {*} endDate
 * @param {*} startDate
 * @name days Calculates the numebr of days between two dates
 * @returns {number} returns the number of days between two dates
 */
function days(endDate, startDate) {
  const start = typeof startDate === 'string' ? new Date(startDate) : startDate;
  const end = typeof endDate === 'string' ? new Date(endDate) : endDate;

  // return zero if dates are valid
  if (Number.isNaN(start.getTime()) || Number.isNaN(end.getTime())) {
    return 0;
  }

  const diffInMs = Math.abs(end.getTime() - start.getTime());
  return Math.floor(diffInMs / (1000 * 60 * 60 * 24));
}

// eslint-disable-next-line import/prefer-default-export
export { getFullName, days };
```
![Hinzufügen einer benutzerdefinierten Funktion](/help/edge/docs/forms/assets/create-custom-function.png)

### Verwenden einer benutzerdefinierten Funktion im Regeleditor

So verwenden Sie die benutzerdefinierte Funktion im Regeleditor:

1. **Hinzufügen der Funktion**: Fügen Sie Ihre benutzerdefinierte Funktion in die Datei `../[blocks]/form/functions.js` ein. Denken Sie daran, sie der `export`-Anweisung in der Datei hinzuzufügen.
1. **Bereitstellen der Datei**: Stellen Sie die aktualisierte Datei `functions.js` in Ihrem GitHub-Projekt bereit und überprüfen Sie, ob der Build erfolgreich war.
1. **Funktionsverwendung**: Greifen Sie auf die Funktion im Regeleditor Ihres Formulars zu, indem Sie im Feld **[!UICONTROL Aktion auswählen]** die Option `Function Output` auswählen.

   ![Benutzerdefinierte Funktion im Regeleditor](/help/edge/docs/forms/assets/custom-function-rule-editor.png)

1. **Vorschau des Formulars**: Zeigt das Formular mit der neu implementierten Funktion in einer Vorschau an.

## Zusätzliche Informationen

>[!NOTE]
>
> Im universellen Editor werden statische und dynamische Importe in benutzerdefinierten Funktionsskripten nicht unterstützt. Sie müssen den vollständigen Code in der Datei `../[blocks]/form/functions.js` hinzufügen.

Dieser Artikel enthält eingeschränkte Informationen zum Regeleditor, der im universellen Editor verfügbar ist. Weitere Informationen zum Regeleditor und zu benutzerdefinierten Funktionen finden Sie in den folgenden Artikeln:

{{see-also-rule-editor}}

## Siehe auch

{{universal-editor-see-also}}
