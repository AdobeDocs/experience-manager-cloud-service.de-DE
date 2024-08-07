---
title: Generieren von Varianten
description: Erfahren Sie mehr über das Generieren von Varianten, auf die über AEM as a Cloud Service und das Sidekick von Edge Delivery Services zugegriffen werden kann.
exl-id: 9114037f-37b9-4b2f-a714-10933f69b2c3
feature: Generate Variations
role: Admin, Architect, Developer
source-git-commit: bbc51796c610af02b5260c063213cde2ef610ba2
workflow-type: tm+mt
source-wordcount: '3262'
ht-degree: 1%

---


# Generieren von Varianten {#generate-variations}

Wenn Sie nach einer Möglichkeit suchen, Ihre digitalen Kanäle zu optimieren und die Inhaltserstellung zu beschleunigen, können Sie Varianten generieren verwenden. Varianten generieren verwendet generative künstliche Intelligenz (AI), um Inhaltsvarianten basierend auf Eingabeaufforderungen zu erstellen. Diese Aufforderungen werden entweder vom Adobe bereitgestellt oder von Benutzern erstellt und verwaltet. Nachdem Sie Varianten erstellt haben, können Sie den Inhalt auf Ihrer Website verwenden und deren Erfolg auch mithilfe der [Experimentation](https://www.aem.live/docs/experimentation) -Funktion von [Edge Delivery Services](/help/edge/overview.md) messen.

Sie können [ auf Varianten generieren](#access-generate-variations) aus folgenden Quellen zugreifen:

* [innerhalb von Adobe Experience Manager (AEM) as a Cloud Service](#access-aemaacs)
* [Sidekick von AEM Edge Delivery Services](#access-aem-sidekick)
* [im Inhaltsfragmente-Editor](/help/sites-cloud/administering/content-fragments/authoring.md#generate-variations-ai)

>[!NOTE]
>
>In allen Fällen müssen Sie zur Verwendung von Generate Variations sicherstellen, dass die [Zugriffsvoraussetzungen](#access-prerequisites) erfüllt sind.

Sie haben dann folgende Möglichkeiten:

* [Erste Schritte](#get-started) mit einer Eingabeaufforderungsvorlage, die von Adobe für einen bestimmten Anwendungsfall erstellt wurde.
* Sie können eine vorhandene Eingabeaufforderung ](#edit-the-prompt) bearbeiten[
* Oder [erstellen und verwenden Sie Ihre eigenen Eingabeaufforderungen](#create-prompt):
   * [Speichern Sie Ihre Eingabeaufforderungen](#save-prompt) für die zukünftige Verwendung
   * [Zugreifen auf und Verwenden freigegebener Eingabeaufforderungen](#select-prompt) aus Ihrem gesamten Unternehmen
* Definieren Sie die [audience](#audiences) -Segmente, die in der Eingabeaufforderung beim [ Generieren personalisierter zielgruppenspezifischer Inhalte ](#generate-copy) verwendet werden sollen.
* Zeigen Sie die Ausgabe neben der Eingabeaufforderung in der Vorschau an, bevor Sie bei Bedarf Änderungen vornehmen und die Ergebnisse verfeinern.
* Verwenden Sie den Adobe Expreß [, um Bilder zu generieren](#generate-image), die auf den Kopiervarianten basieren. Dabei werden die generativen KI-Funktionen von Firefly verwendet.
* Wählen Sie Inhalte aus, die Sie auf Ihrer Website oder in einem Experiment verwenden möchten.

## Rechtlicher und Gebrauchshinweis {#legal-usage-note}

Generative KI und Generate Variations for AEM sind leistungsstarke Tools - für die Verwendung der Ausgabe sind jedoch **Sie** verantwortlich.

Ihre Eingaben für den Dienst sollten an einen Kontext gebunden sein. Dieser Kontext kann Ihre Branding-Materialien, Website-Inhalte, Daten, Schemata für solche Daten, Vorlagen oder andere vertrauenswürdige Dokumente sein.

Sie müssen die Genauigkeit jeder Ausgabe entsprechend Ihrem Anwendungsfall bewerten.

Bevor Sie Varianten generieren verwenden, müssen Sie den [Adobe Generative AI-Benutzerrichtlinien](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html) zustimmen.

[Verwendung von Generate Variations](#generative-action-usage) ist an den Verbrauch generativer Aktionen gebunden.

## Überblick {#overview}

Wenn Sie Varianten generieren (und den linken Bereich erweitern) öffnen, sehen Sie Folgendes:

![Varianten generieren - Hauptbereich](assets/generate-variations-main-panel.png)

* Rechter Bereich
   * Dies hängt von der Auswahl ab, die Sie im linken Navigationsbereich vornehmen.
   * Standardmäßig werden **Eingabeaufforderungsvorlagen** angezeigt.
* Linke Navigation
   * Links von **Varianten generieren** befindet sich die Option (Sandwich-Menü), das linke Navigationsfenster ein- oder auszublenden.
   * **Eingabeaufforderungsvorlagen**:
      * Zeigt Links zu den verschiedenen Eingabeaufforderungen an. Dazu können Eingabeaufforderungen gehören:
         * Wird von Adobe bereitgestellt, um Ihnen bei der Erstellung von Inhalten zu helfen, die mit dem Adobe-Symbol gekennzeichnet sind.
         * Erstellt von selbst.
         * Erstellt innerhalb Ihrer IMS-Organisation; mit einem Symbol gekennzeichnet, das mehrere Überschriften anzeigt.
      * Enthält den Link [Neue Eingabeaufforderung](#create-prompt) zum Erstellen Ihrer eigenen Eingabeaufforderung.
      * Sie können von Ihnen oder innerhalb Ihrer IMS-Organisation erstellte **Löschaufforderungen** löschen. Dies geschieht über das Menü, auf das mit den Auslassungspunkten auf der entsprechenden Karte zugegriffen wird.
   * [Favoriten](#favorites): Zeigt Ergebnisse früherer Generationen an, die Sie als Favoriten gekennzeichnet haben.
   * [Zuletzt verwendet](#recents): Enthält Links zu Eingabeaufforderungen und deren Eingaben, die Sie vor Kurzem verwendet haben.
   * **Hilfe und FAQ**: Links zur Dokumentation, einschließlich häufig gestellter Fragen.
   * **Benutzerrichtlinien**: Links zu den gesetzlichen Richtlinien.

## Erste Schritte {#get-started}

Die Benutzeroberfläche führt Sie durch den Prozess der Inhaltserstellung. Nach dem Öffnen der Benutzeroberfläche besteht der erste Schritt darin, die Eingabeaufforderung auszuwählen, die Sie verwenden möchten.

### Eingabeaufforderung auswählen {#select-prompt}

Im Hauptbereich können Sie Folgendes auswählen:

* eine Eingabeaufforderung, die von Adobe bereitgestellt wird, um mit der Erstellung von Inhalten zu beginnen;
* die [neue Eingabeaufforderung](#create-prompt), um eine eigene Eingabeaufforderung zu erstellen,
* eine Vorlage, die Sie ausschließlich für Ihre Verwendung erstellt haben,
* eine Vorlage, die Sie oder eine Person in Ihrer Organisation erstellt haben.

So unterscheiden Sie:

* Die vom Adobe bereitgestellten Eingabeaufforderungen werden mit dem Adobe-Symbol gekennzeichnet
* In Ihrer IMS-Organisation verfügbare Eingabeaufforderungen werden mit einem Symbol mit mehreren Kopfzeilen gekennzeichnet.
* Ihre privaten Aufforderungen werden nicht speziell gekennzeichnet.

![Varianten generieren - Eingabeaufforderungsvorlagen](assets/generate-variations-prompt-templates.png)

### Bereitstellen von Inputs {#provide-inputs}

Für jede Eingabeaufforderung müssen Sie bestimmte Informationen angeben, damit die entsprechenden Inhalte von der generativen KI abgerufen werden können.

Die Eingabefelder führen Sie durch die benötigten Informationen. Bestimmte Felder haben Standardwerte, die Sie verwenden oder nach Bedarf ändern können, sowie Beschreibungen, die die Anforderungen erläutern.

Es gibt mehrere wichtige Eingabefelder, die für mehrere Eingabeaufforderungen verwendet werden (bestimmte Felder sind nicht immer verfügbar):

* **Anzahl der**/**Anzahl der**
   * Sie können auswählen, wie viele Inhaltsvarianten Sie in einer Generation erstellen möchten.
   * Abhängig von der Eingabeaufforderung kann dies eine von verschiedenen Beschriftungen aufweisen, z. B. Anzahl, Anzahl der Varianten, Anzahl der Ideen und andere.
* **Audience Source**/**Target Audience**
   * Hilft bei der Erstellung personalisierter Inhalte für eine bestimmte Zielgruppe.
   * Adobe bietet Standardzielgruppen, oder Sie können zusätzliche Zielgruppen angeben, siehe [Zielgruppen](#audiences).
* **Zusätzlicher Kontext**
   * Fügen Sie relevante Inhalte ein, um Generative AI bei der Erstellung einer besseren Antwort auf der Basis der Eingabe zu unterstützen. Wenn Sie beispielsweise ein Webbanner für eine bestimmte Seite oder ein bestimmtes Produkt erstellen, können Sie Informationen über die Seite/das Produkt einbeziehen.
* **Temperatur**
Zur Änderung der Temperatur von Adobe Generative AI:
   * Eine höhere Temperatur wird von der Eingabeaufforderung entfernt und führt zu mehr Variation, Zufälligkeit und Kreativität.
   * Eine niedrigere Temperatur ist deterministischer und bleibt näher an dem, was in der Eingabeaufforderung ist.
   * Standardmäßig ist die Temperatur auf 1 eingestellt. Sie können mit unterschiedlichen Temperaturen experimentieren, wenn die erzeugten Ergebnisse nicht Ihren Vorstellungen entsprechen.
* **Aufforderung zum Bearbeiten**
   * Die zugrunde liegende [Eingabeaufforderung kann bearbeitet werden](#edit-the-prompt), um die generierten Ergebnisse zu verfeinern.

### Kopie erstellen {#generate-copy}

Nachdem Sie die Eingabefelder ausgefüllt und/oder die Eingabeaufforderung geändert haben, können Sie Inhalte generieren und die Antworten überprüfen.

Wählen Sie **Generate** aus, um die von generativer KI generierten Antworten anzuzeigen. Die generierten Inhaltsvarianten werden unter der Eingabeaufforderung angezeigt, die sie generiert hat.

![Varianten generieren - Kopie generieren](assets/generate-variations-generate-content.png)

>[!NOTE]
>
>Die meisten Adobe-Eingabeaufforderungsvorlagen enthalten in der Variantenantwort ein **AI Rationale** . Dies bietet Transparenz darüber, warum generative KI diese bestimmte Variante generiert hat.

Wenn Sie eine Variante auswählen, sind die folgenden Aktionen verfügbar:

* **Favorit**
   * Flag als **Favorit** für die zukünftige Verwendung (wird in [Favoriten](#favorites) angezeigt).
* Nach oben/unten drehen
   * Verwenden Sie die Daumen nach oben/unten-Indikatoren, um Adobe über die Qualität der Antworten zu informieren.
* **Kopieren**
   * Kopieren Sie in die Zwischenablage, um Inhalte auf Ihrer Website oder in einem [Experiment](https://www.aem.live/docs/experimentation) zu erstellen.
* **Entfernen**

Wenn Sie die Eingaben oder Eingabeaufforderungen verfeinern müssen, können Sie Anpassungen vornehmen und erneut **Generate** auswählen, um eine Reihe neuer Antworten zu erhalten. Die neue Eingabeaufforderung und Antwort werden unter der ersten Eingabeaufforderung und Antwort angezeigt. Sie können nach oben und unten scrollen, um die verschiedenen Inhaltssätze anzuzeigen.

Über jedem Variantensatz befindet sich die Eingabeaufforderung, die sie erstellt hat, zusammen mit der Option **Wiederverwenden** . Wenn Sie eine Eingabeaufforderung je erneut ausführen müssen, wählen Sie **Erneut verwenden** aus, um sie in **Eingaben** erneut zu laden.

### Bild generieren {#generate-image}

Nachdem Sie Textvarianten generiert haben, können Sie in Adobe Express Bilder mithilfe der Generative KI-Funktionen von Firefly generieren.

>[!NOTE]
>
>**Bild generieren** ist nur verfügbar, wenn Sie über eine Berechtigung für Adobe Expreß im Rahmen Ihrer IMS-Organisation verfügen und Ihnen Zugriff in der Admin Console gewährt wurde.

Wählen Sie eine Variante, gefolgt von **Bild generieren**, um **Text in Bild** direkt in [Adobe Expreß](https://www.adobe.com/de/express/) zu öffnen. Die Eingabeaufforderung wird entsprechend Ihrer Variantenauswahl vorausgefüllt und die Bilder werden automatisch entsprechend dieser Eingabeaufforderung generiert.

![Varianten generieren - Bilder ausdrücken](assets/generate-variations-express-images.png)

Sie können weitere Änderungen vornehmen:

* [schreiben Sie Ihre eigene Eingabeaufforderung in Adobe Expreß](https://helpx.adobe.com/firefly/using/tips-and-tricks.html), indem Sie beschreiben, was Sie sehen möchten.
* die Optionen **Text auf image** anpassen,
* dann **Aktualisieren** die generierten Bilder.

Sie können auch **Mehr erkunden** für weitere Möglichkeiten verwenden.

Wählen Sie nach Abschluss des Vorgangs das gewünschte Bild und **Speichern** , um den Adobe Expreß zu schließen. Das Bild wird zurückgegeben und mit der Variante gespeichert.

![Varianten generieren - Express-Bild gespeichert](assets/generate-variations-express-image-saved.png)

Hier können Sie mit dem Mauszeiger über das Bild fahren, um Aktionselemente für Folgendes anzuzeigen:

* **Kopieren**: [Kopieren Sie das Bild zur Verwendung an anderer Stelle in die Zwischenablage](#use-content)
* **Bearbeiten**: Öffnen Sie den Adobe Expreß, damit Sie Änderungen am Bild vornehmen können.
* **Download**: Laden Sie das Bild auf Ihren lokalen Computer herunter.
* **Löschen**: Entfernen Sie das Bild aus der Variante

>[!NOTE]
>
>[Content credentials](https://helpx.adobe.com/creative-cloud/help/content-credentials.html) werden bei der Verwendung in der dokumentbasierten Bearbeitung nicht beibehalten.

### Inhalt verwenden {#use-content}

Um den mit generativer KI generierten Inhalt zu verwenden, müssen Sie den Inhalt zur Verwendung an anderer Stelle in die Zwischenablage kopieren.

Dies geschieht mithilfe der Kopiersymbole:

* Für Text: Verwenden Sie das Kopiersymbol, das im Varianten-Bedienfeld angezeigt wird.
* Für das Bild: Bewegen Sie die Maus über das Bild, um das Kopiersymbol zu sehen.

Nachdem Sie die Informationen in die Zwischenablage kopiert haben, können Sie sie zur Erstellung von Inhalten für Ihre Website einfügen. Sie können auch ein [Experiment](https://www.aem.live/docs/experimentation) ausführen.

## Favoriten {#favorites}

Nach der Überprüfung des Inhalts können Sie ausgewählte Varianten als Favoriten speichern.

Nach dem Speichern werden sie im linken Navigationsbereich unter **Favoriten** angezeigt. Favoriten werden beibehalten (bis Sie diese löschen **1} oder den Browser-Cache löschen).**

* Favoriten und Varianten können kopiert/in die Zwischenablage eingefügt werden, um sie in Ihren Website-Inhalten zu verwenden.
* Favoriten können **entfernt** sein.

## Zuletzt verwendet {#recents}

Dieser Abschnitt enthält Links zu Ihrer aktuellen Aktivität. Ein Eintrag **Zuletzt verwendet** wird hinzugefügt, nachdem Sie **Erzeugen** ausgewählt haben. Er hat den Namen der Eingabeaufforderung und einen Zeitstempel. Wenn Sie einen Link auswählen, wird die Eingabeaufforderung geladen, die Eingabefelder entsprechend ausgefüllt und die generierten Varianten angezeigt.

## Eingabeaufforderung bearbeiten {#edit-the-prompt}

Die zugrunde liegende Eingabeaufforderung kann bearbeitet werden. Sie können dies tun:

* Wenn die generierten Ergebnisse, die Sie erhalten, weiter verfeinert werden müssen
* Sie möchten die Eingabeaufforderung](#save-prompt) ändern und [speichern, um sie für die zukünftige Verwendung zu verwenden

Wählen Sie **Aufforderung bearbeiten** aus:

![Varianten generieren - Eingabeaufforderung bearbeiten](assets/generate-variations-prompt-edit.png)

Dadurch wird der Eingabeaufforderungseditor geöffnet, in dem Sie Ihre Änderungen vornehmen können:

![Varianten generieren - Eingabeaufforderungs-Editor](assets/generate-variations-prompt-editor.png)

### Hinzufügen von Eingabeaufforderungen {#add-prompt-inputs}

Beim Erstellen oder Bearbeiten einer Eingabeaufforderung können Sie Eingabefelder hinzufügen. Eingabefelder dienen als Variablen in der Eingabeaufforderung und bieten die Flexibilität, dieselbe Eingabeaufforderung in verschiedenen Szenarien zu verwenden. Sie ermöglichen es Benutzern, bestimmte Elemente der Eingabeaufforderung zu definieren, ohne die gesamte Eingabeaufforderung schreiben zu müssen.

* Ein Feld wird mit doppelten geschweiften Klammern `{{ }}` definiert, die einen Platzhalternamen enthalten.
Zum Beispiel: `{{tone_of_voice}}`.

  >[!NOTE]
  >
  >Zwischen den geschweiften Klammern sind keine Leerzeichen zulässig.

* Sie wird auch unter `METADATA` mit den folgenden Parametern definiert:
   * `label`
   * `description`
   * `default`
   * `type`

#### Beispiel: Neues Textfeld hinzufügen - Tone of Voice {#example-add-new-text-field-tone-of-voice}

Um ein neues Textfeld mit dem Titel **Tone of Voice** hinzuzufügen, verwenden Sie die folgende Syntax in Ihrer Eingabeaufforderung:

```prompt
{{@tone_of_voice, 
  label="Tone of voice",
  description="Indicate the desired tone of voice",
  default="optimistic, smart, engaging, human, and creative",
  type=text
}}
```

![Varianten generieren - Eingabeaufforderung mit Sprachton bearbeitet](assets/generate-variations-prompt-edited.png)

<!--
#### Example: Add new dropdown field - Page Type {#example-add-new-dropdown-field-page-type}

To create an input field Page Type providing a dropdown selection:

1. Create a spreadsheet named `pagetype.xls` in the top-level directory of your folder structure.
1. Edit the spreadsheet:

   1. Create two columns: **Key** and **Value**.
   1. In the **Key** column, enter labels that will appear in the dropdown.
   1. In the **Value** column, describe the key value so the generative AI has context.

1. In your prompt, refer to the title of the spreadsheet along with the appropriate type. 

   ```prompt
   {{@page_type, 
     label="Page Type",
     description="Describes the type of page",
     spreadsheet=pagetype
   }}
   ```
-->

## Erstellen einer Eingabeaufforderung {#create-prompt}

Wenn Sie unter **Eingabeaufforderung** die Option **Neue Eingabeaufforderung** auswählen, können Sie in einem neuen Bedienfeld eine neue Eingabeaufforderung eingeben. Sie können diese dann zusammen mit der **Temperatur** in den Inhalt **Erzeugen** festlegen.

Weitere Informationen zum Speichern der Eingabeaufforderung für die Zukunft finden Sie unter [Eingabeaufforderung speichern](#save-prompt) .

Weitere Informationen zum Hinzufügen eigener Eingabeaufforderungen finden Sie unter [Eingabeaufforderungen hinzufügen](#add-prompt-inputs) .

Wenn Sie die Formatierung sowohl in der Benutzeroberfläche als auch beim Kopieren und Einfügen in den dokumentbasierten Authoring-Fluss beibehalten möchten, fügen Sie Folgendes in die Eingabeaufforderung ein:

<!-- CHECK - are the double-quotes needed? -->

* `"Format the response as an array of valid, iterable RFC8259 compliant JSON"`

Die folgende Abbildung zeigt die Vorteile, die dies bietet:

* Im ersten Beispiel werden die `Title` und die `Description` kombiniert
* während sie im zweiten Beispiel separat formatiert werden: Dies geschieht durch Einbeziehung der JSON-Anfrage in die Eingabeaufforderung.

![Varianten generieren - Eingabeaufforderung mit Titel und Beschreibung, die separat formatiert sind](assets/generate-variations-prompt-formatted.png)

## Prompt speichern {#save-prompt}

Nach der Bearbeitung oder Erstellung von Eingabeaufforderungen können Sie diese für die zukünftige Verwendung speichern, entweder für Ihre IMS-Organisation oder für Sie selbst. Die gespeicherte Eingabeaufforderung wird als Karte **Eingabeaufforderung für Vorlage** angezeigt.

Wenn Sie die Eingabeaufforderung bearbeitet haben, ist die Option **Speichern** am unteren Rand des Bereichs &quot;Einstiege&quot;links neben **Erzeugen** verfügbar.

Wenn ausgewählt, wird das Dialogfeld **Eingabeaufforderung speichern** geöffnet:

![Varianten generieren - Dialogfeld für Speicheraufforderung](assets/generate-variations-prompt-save-dialog.png)

1. Fügen Sie einen eindeutigen **Eingabeaufforderungsnamen** hinzu, der verwendet wird, um die Eingabeaufforderung in **Eingabeaufforderungsvorlagen** zu identifizieren.
   1. Ein neuer, eindeutiger Name erstellt eine neue Eingabeaufforderungsvorlage.
   1. Ein vorhandener Name überschreibt diese Eingabeaufforderung. Es wird eine Meldung angezeigt.
1. Fügen Sie optional eine Beschreibung hinzu.
1. Aktivieren oder deaktivieren Sie die Option **In der gesamten Organisation freigegeben**, je nachdem, ob die Eingabeaufforderung für Sie privat sein soll oder in Ihrer IMS-Organisation verfügbar gemacht wird. Dieser Status wird auf der Karte [angezeigt, die in den Eingabeaufforderungsvorlagen angezeigt wird](#select-prompt).
1. **Speichern** Sie die Eingabeaufforderung oder **Abbrechen** Sie die Aktion.

>[!NOTE]
>
>Sie werden informiert (gewarnt), wenn Sie eine vorhandene Eingabeaufforderung überschreiben/aktualisieren.

>[!NOTE]
>
>Von **Eingabeaufforderungsvorlagen** aus können Sie Aufforderungen löschen (mithilfe des Menüs, auf das mit den Ellipsen zugegriffen wird), die von Ihnen oder in Ihrer IMS-Organisation erstellt wurden.

## Zielgruppen {#audiences}

Um personalisierte Inhalte zu generieren, muss die generative KI über Kenntnisse der Audience verfügen. Adobe bietet eine Reihe von Standardzielgruppen, oder Sie können Ihre eigenen hinzufügen.

Beim Hinzufügen einer Zielgruppe sollten Sie die Zielgruppe in natürlicher Sprache beschreiben. Zum Beispiel:

* , um eine Zielgruppe zu erstellen:
   * `Student`
* Sie könnten sagen:
   * `The audience consists of students, typically individuals who are pursuing education at various academic levels, such as primary, secondary, or tertiary education. They are engaged in learning and acquiring knowledge in diverse subjects, seeking academic growth, and preparing for future careers or personal development.`

Es werden zwei Zielgruppenquellen unterstützt:

* [Adobe Target](#audience-adobe-target)
* [CSV-Datei](#audience-csv-file)

![Generieren von Varianten - Zielgruppenquellen](assets/generate-variations-audiences.png)

### Audience - Adobe Target {#audience-adobe-target}

Durch Auswahl einer Audience vom Typ **Adobe Target** in der Eingabeaufforderung kann die Inhaltserstellung für diese Audience personalisiert werden.

>[!NOTE]
>
>Um diese Option verwenden zu können, muss Ihre IMS-Organisation Zugriff auf Adobe Target haben.

1. Wählen Sie **Adobe Target** aus.
1. Wählen Sie dann die erforderliche **Zielgruppe** aus der bereitgestellten Liste aus.

   >[!NOTE]
   >
   >Um eine Audience vom Typ **Adobe Target** zu verwenden, muss das Beschreibungsfeld ausgefüllt werden. Wenn nicht, wird die Zielgruppe in der Dropdown-Liste als nicht verfügbar angezeigt. Um eine Beschreibung hinzuzufügen, gehen Sie zu Target und [fügen Sie eine Zielgruppenbeschreibung hinzu](https://experienceleague.adobe.com/en/docs/target-learn/tutorials/audiences/create-audiences).

   ![Generieren von Varianten - Zielgruppenquelle - Adobe Target](assets/generate-variations-audiences-adobe-target.png)

#### Hinzufügen von Adobe Target-Zielgruppen {#add-adobe-target-audience}

Siehe [Erstellen von Zielgruppen](https://experienceleague.adobe.com/en/docs/target-learn/tutorials/audiences/create-audiences) , um eine Zielgruppe in Adobe Target zu erstellen.

### Audience - CSV-Datei {#audience-csv-file}

Wenn Sie in der Eingabeaufforderung eine Audience vom Typ **CSV-Datei** auswählen, kann die Inhaltserstellung für die ausgewählte **Target-Zielgruppe** personalisiert werden.

Adobe bietet eine Reihe von zu verwendenden Zielgruppen.

1. Wählen Sie **CSV-Datei** aus.
1. Wählen Sie dann die erforderliche **Zielgruppe** aus der bereitgestellten Liste aus.

   ![Generieren von Varianten - Zielgruppenquelle - CSV-Datei](assets/generate-variations-audiences-csv-file.png)

#### Audience CSV-Datei hinzufügen {#add-audience-csv-file}

Sie können eine CSV-Datei von verschiedenen Plattformen hinzufügen (z. B. Google Drive, Dropbox, Sharepoint), die eine URL für die Datei bereitstellen können, sobald sie öffentlich verfügbar gemacht wird.

>[!NOTE]
>
>In den Freigabeplattformen müssen Sie *1} die Möglichkeit haben, die Datei öffentlich zugänglich zu machen.*

So fügen Sie beispielsweise eine Audience aus einer Datei auf dem Google-Laufwerk hinzu:

1. Erstellen Sie in Google Drive eine Tabellendatei mit zwei Spalten:
   1. Die erste Spalte wird im Dropdown-Menü angezeigt.
   1. Die zweite Spalte ist die Zielgruppenbeschreibung.
1. Publish der Datei:
   1. Datei -> Freigeben -> Im Web veröffentlichen -> CSV
1. Kopieren Sie die URL in die veröffentlichte Datei.
1. Navigieren Sie zu Varianten generieren .
1. Öffnen Sie den Eingabeaufforderungseditor.
1. Suchen Sie die Audience **Adobe Target** in den Metadaten und ersetzen Sie die URL.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass die doppelten Anführungszeichen (&quot;) an beiden Enden der URL beibehalten werden.

   Zum Beispiel:

   ![Generieren von Varianten - Hinzufügen einer CSV-Zielgruppendatei](assets/generate-variations-audiences-csv-save.png)

## Nutzung generischer Aktionen {#generative-action-usage}

Die Verwaltung der Nutzung hängt von den getroffenen Maßnahmen ab:

* Generieren von Varianten

  Eine Generation einer Kopiervariante entspricht einer generativen Aktion. Als Kunde verfügen Sie über eine bestimmte Anzahl von generativen Aktionen, die mit Ihrer AEM Lizenz einhergehen. Sobald die grundlegende Berechtigung verwendet wurde, können Sie zusätzliche Aktionen erwerben.

  >[!NOTE]
  >
  >Siehe [Adobe Experience Manager: Cloud Service | Produktbeschreibung](https://helpx.adobe.com/legal/product-descriptions/aem-cloud-service.html) finden Sie weitere Informationen zu den grundlegenden Berechtigungen. Wenden Sie sich außerdem an Ihr Account-Team, wenn Sie generativere Aktionen erwerben möchten.

* Adobe Express

  Die Nutzung der Bildgenerierung erfolgt über Adobe Expreß-Berechtigungen und [generative Gutschriften](https://helpx.adobe.com/firefly/using/generative-credits-faq.html).

## Zugriff auf Generieren von Varianten {#access-generate-variations}

Nach Erfüllung der Voraussetzungen können Sie auf Varianten aus AEM as a Cloud Service generieren oder auf die Sidekick der Edge Delivery Services zugreifen.

### Voraussetzungen für den Zugriff {#access-prerequisites}

Um Varianten generieren zu verwenden, müssen Sie sicherstellen, dass die Voraussetzungen erfüllt sind:

* [Zugriff auf Experience Manager as a Cloud Service mit Edge Delivery Services](#access-to-aemaacs-with-edge-delivery-services)

#### Zugriff auf Experience Manager as a Cloud Service mit Edge Delivery Services{#access-to-aemaacs-with-edge-delivery-services}

Benutzer, die Zugriff auf die Option Varianten generieren benötigen, müssen über die Berechtigung für eine Experience Manager as a Cloud Service-Umgebung mit Edge Delivery Services verfügen.

>[!NOTE]
>
>Wenn Ihr Vertrag für AEM Sites as a Cloud Service keine Edge Delivery Services enthält, müssen Sie einen neuen Vertrag unterzeichnen, um Zugriff zu erhalten.
>
>Wenden Sie sich an Ihr Account-Team, um zu besprechen, wie Sie mit Edge Delivery Services zu AEM Sites as a Cloud Service wechseln können.

Um bestimmten Benutzern Zugriff zu gewähren, weisen Sie ihr Benutzerkonto dem jeweiligen Produktprofil zu. Weitere Informationen finden Sie unter [Zuweisen AEM Produktprofile](/help/journey-onboarding/assign-profiles-cloud-manager.md).

### Zugriff über AEM as a Cloud Service {#access-aemaacs}

Der Zugriff auf Varianten generieren erfolgt über das [Navigationsfenster](/help/sites-cloud/authoring/basic-handling.md#navigation-panel) von AEM as a Cloud Service:

![Navigationsfenster](/help/sites-cloud/authoring/assets/basic-handling-navigation.png)

### Zugriff über die AEM Sidekick {#access-aem-sidekick}

Bevor Sie auf die Option Varianten generieren über die Sidekick (der Edge Delivery Services) zugreifen können, ist eine gewisse Konfiguration erforderlich.

1. Informationen zum Installieren und Konfigurieren des Sidekick finden Sie im Dokument [Installieren der AEM Sidekick](https://www.aem.live/docs/sidekick-extension) .

1. Um die Option Varianten generieren im Sidekick (von Edge Delivery Services) zu verwenden, schließen Sie die folgende Konfiguration in Ihre Edge Delivery Services-Projekte unter ein:

   * `tools/sidekick/config.json`

   Dies muss mit Ihrer vorhandenen Konfiguration zusammengeführt und dann bereitgestellt werden.

   Zum Beispiel:

   ```prompt
   {
     // ...
     "plugins": [
       // ...
       {
         "id": "generate-variations",
         "title": "Generate Variations",
         "url": "https://experience.adobe.com/aem/generate-variations",
         "passConfig": true,
         "environments": ["preview","live", "edit"],
         "includePaths": ["**.docx**"]
       }
       // ...
     ]
   }
   ```

1. Sie müssen dann möglicherweise sicherstellen, dass Benutzer mit Edge Delivery Services ](#access-to-aemaacs-with-edge-delivery-services) über [Zugriff auf Experience Manager-as a Cloud Services verfügen.

1. Sie können dann auf die Funktion zugreifen, indem Sie in der Symbolleiste der Sidekick die Option **Varianten generieren** auswählen:

   ![Varianten generieren - Zugriff von AEM Sidekicj](assets/generate-variations-sidekick-toolbar.png)

## Weiterführende Informationen {#further-information}

Weitere Informationen finden Sie unter:

* [GenAI Generate Variations on GitHub](https://github.com/adobe/aem-genai-assistant#setting-up-aem-genai-assistant)
* [Edge Delivery Services-Experimentierung](https://www.aem.live/docs/experimentation)

## Häufig gestellte Fragen {#faqs}

### Formatierte Ausgabe {#formatted-outpu}

**Die generierte Antwort gibt mir nicht die formatierte Ausgabe, die ich brauche. Wie kann ich das Format ändern? z. B.: Ich benötige einen Titel und einen Untertitel, aber die Antwort lautet nur title**

1. Öffnen Sie die tatsächliche Eingabeaufforderung im Bearbeitungsmodus.
1. Gehen Sie zu Anforderungen.
1. Sie finden Anforderungen, die über die Ausgabe sprechen.
   1. Beispiel: &quot;Der Text muss aus drei Teilen bestehen: einem Titel, einem Hauptteil und einer Schaltflächenbeschriftung.&quot; oder &quot;Formatieren Sie die Antwort als gültiges JSON-Array von Objekten mit den Attributen &quot;Title&quot;, &quot;Body&quot;und &quot;ButtonLabel&quot;.
1. Passen Sie die Anforderungen an Ihre Anforderungen an.

   >[!NOTE]
   >
   >Wenn Sie für die neu eingegebene Ausgabe Beschränkungen hinsichtlich der Wort-/Zeichenanzahl haben, erstellen Sie eine Anforderung.

   Beispiel: &quot;Der Titeltext darf 10 Wörter oder 50 Zeichen (einschließlich Leerzeichen) nicht überschreiten.&quot;
1. Speichern Sie die Eingabeaufforderung für die zukünftige Verwendung.

### Reaktionsdauer {#length-of-response}

**Die generierte Antwort ist zu lang oder zu kurz. Wie ändere ich die Länge?**

1. Öffnen Sie die tatsächliche Eingabeaufforderung im Bearbeitungsmodus.
1. Gehen Sie zu Anforderungen.
1. Für jede Ausgabe gibt es eine entsprechende Wort-/Zeichenbeschränkung.
   1. Beispiel: &quot;Der Titeltext darf 10 Wörter oder 50 Zeichen (einschließlich Leerzeichen) nicht überschreiten.&quot;
1. Passen Sie die Anforderungen an Ihre Anforderungen an.
1. Speichern Sie die Eingabeaufforderung für die zukünftige Verwendung.

### Verbessern der Antworten {#improve-responses}

**Die Antworten, die ich erhalte, sind nicht genau das, was ich suche. Was kann ich tun, um sie zu verbessern?**

1. Versuchen Sie, die Temperatur unter Erweiterte Einstellungen zu ändern.
   1. Eine höhere Temperatur wird von der Eingabeaufforderung entfernt und führt zu mehr Variation, Zufälligkeit und Kreativität.
   1. Eine niedrigere Temperatur ist deterministischer und hält sich an das, was in der Eingabeaufforderung ist.
1. Öffnen Sie die tatsächliche Eingabeaufforderung im Bearbeitungsmodus und rufen Sie die Überprüfungsaufforderung auf. Achten Sie besonders auf den Anforderungsabschnitt, der den Ton der Stimme und andere wichtige Kriterien beschreibt.

### Kommentare in einer Eingabeaufforderung {#comments-in-prompt}

**Wie kann ich Kommentare in einer Eingabeaufforderung verwenden?**

Kommentare in einer Eingabeaufforderung werden verwendet, um Notizen, Erklärungen oder Anweisungen einzuschließen, die nicht Teil der tatsächlichen Ausgabe sein sollen. Diese Kommentare sind in einer bestimmten Syntax eingeschlossen: Sie beginnen und enden mit doppelten geschweiften Klammern und beginnen mit einem Hash (z. B. `{{# Comment Here }}`). Kommentare helfen, die schnelle Struktur oder Absicht zu verdeutlichen, ohne dass sich dies auf die generierte Antwort auswirkt.

### Geteilte Eingabeaufforderung suchen {#find-a-shared-prompt}

**Was kann ich tun, wenn ich keine Eingabeaufforderungsvorlage finden kann, die jemand freigegeben hat?**

In diesem Fall sind verschiedene Details zu überprüfen:

1. Verwenden Sie die URL für Ihre Umgebung.
Beispiel: https://experience.adobe.com/#/aem/generate-variations
1. Stellen Sie sicher, dass die ausgewählte IMS-Organisation korrekt ist.
1. Vergewissern Sie sich, dass die Eingabeaufforderung als freigegeben gespeichert wurde.

### Benutzerdefinierte Eingabeaufforderungen in v2.0.0 {#custom-prompts-v200}

**In Version 2.0.0 sind meine benutzerdefinierten Eingabeaufforderungen verschwunden - was kann ich tun?**

Wenn Sie zur Version 2.0.0 wechseln, werden benutzerdefinierte Eingabeaufforderungsvorlagen beschädigt, sodass sie nicht verfügbar sind.

So rufen Sie sie ab:

1. Wechseln Sie zum Ordner &quot;Eingabeaufforderung-Vorlage&quot;in Sharepoint.
1. Kopieren Sie die Eingabeaufforderung.
1. Öffnen Sie die Anwendung Varianten generieren .
1. Wählen Sie die Karte Neue Eingabeaufforderung aus.
1. Fügen Sie die Eingabeaufforderung ein.
1. Überprüfen Sie, ob die Eingabeaufforderung funktioniert.
1. Speichern Sie die Eingabeaufforderung.

## Versionsverlauf {#release-history}

Weitere Informationen zu aktuellen und vorherigen Versionen finden Sie in den [Versionshinweisen für Generate Variations](/help/generative-ai/release-notes-generate-variations.md) .
