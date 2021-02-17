---
title: Inhaltsfragmentmodelle
description: Inhaltsfragmentmodelle werden verwendet, um Inhaltsfragmente mit strukturierten Inhalten zu erstellen.
translation-type: tm+mt
source-git-commit: 3538c03a6a455cd22423ca5a4fd69c1fe57b3e5e
workflow-type: tm+mt
source-wordcount: '2156'
ht-degree: 55%

---


# Inhaltsfragmentmodelle {#content-fragment-models}

Inhaltsfragmentmodelle definieren die Struktur des Inhalts für Ihre [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md).

So verwenden Sie Inhaltsfragmentmodelle:

1. [Aktivieren Sie die Funktion für Inhaltsfragmentmodelle für Ihre Instanz](/help/assets/content-fragments/content-fragments-configuration-browser.md).
1. [Erstellen](#creating-a-content-fragment-model) und [konfigurieren](#defining-your-content-fragment-model) Sie Ihre Inhaltsfragmentmodelle.
1. [Aktivieren Sie Ihre Inhaltsfragmentmodelle](#enabling-disabling-a-content-fragment-model) zur Verwendung bei der Erstellung von Inhaltsfragmenten.
1. [Lassen Sie Ihre Inhaltsfragmentmodelle in den erforderlichen Asset-](#allowing-content-fragment-models-assets-folder) Ordnern zu, indem Sie  **Richtlinien** konfigurieren.

## Erstellen eines Inhaltsfragmentmodells {#creating-a-content-fragment-model}

1. Navigieren Sie zu **Tools** > **Assets** und öffnen Sie dann **Inhaltsfragmentmodelle**.
1. Navigieren Sie zu dem entsprechenden Ordner für Ihre [Konfiguration](/help/assets/content-fragments/content-fragments-configuration-browser.md).
1. Öffnen Sie den Assistenten über **Erstellen**.

   >[!CAUTION]
   >
   >Wenn die [Verwendung von Inhaltsfragmentmodellen nicht aktiviert wurde](/help/assets/content-fragments/content-fragments-configuration-browser.md), ist die Option **Erstellen** nicht verfügbar.

1. Geben Sie den **Modell-Titel** an. Sie können auch **Tags**, eine **Beschreibung** hinzufügen und **Modell** aktivieren, um [das Modell](#enabling-disabling-a-content-fragment-model) bei Bedarf zu aktivieren.

   ![Titel und Beschreibung](assets/cfm-models-02.png)

1. Speichern Sie das leere Modell über **Erstellen**. Eine Benachrichtigung zeigt an, dass der Vorgang erfolgreich abgeschlossen wurde. Daraufhin können Sie das Modell über die Option **Öffnen** direkt bearbeiten oder über **Fertig** zur Konsole zurückkehren.

## Definieren des Inhaltsfragmentmodells  {#defining-your-content-fragment-model}

Das Inhaltsfragmentmodell definiert effektiv die Struktur der resultierenden Inhaltsfragmente unter Verwendung unterschiedlicher **[Datentypen](#data-types)**. Mithilfe des Modell-Editors können Sie Instanzen der Datentypen hinzufügen und diese dann so konfigurieren, dass die erforderlichen Felder erstellt werden:

>[!CAUTION]
>
>Die Bearbeitung eines vorhandenen Inhaltsfragmentmodells kann sich auf abhängige Fragmente auswirken.

1. Navigieren Sie zu **Tools** > **Assets** und öffnen Sie dann **Inhaltsfragmentmodelle**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Öffnen Sie das zu **bearbeitende** Modell; nutzen Sie dazu entweder die entsprechende Schnellaktion oder wählen Sie das Modell und anschließend die Aktion aus der Symbolleiste aus.

   Wenn das Modell geöffnet ist, finden Sie Folgendes im Editor:

   * Links: bereits definierte Felder
   * Rechts: verfügbare **Datentypen** für das Erstellen von Feldern (und **Eigenschaften**, die für erstellte Felder verwendet werden können)

   >[!NOTE]
   >
   >Wenn ein Feld ein **Pflichtfeld** ist, wird die **Bezeichnung** im linken Bereich mit einem Stern markiert (*****).

   ![Eigenschaften](assets/cfm-models-03.png)

1. **So fügen Sie ein Feld hinzu**

   * Ziehen Sie einen erforderlichen Datentyp an die entsprechende Stelle für ein Feld:

      ![Datentyp zum Feld](assets/cfm-models-04.png)

   * Wenn ein Feld zum Modell hinzugefügt wurde, werden im rechten Fenster die **Eigenschaften** angezeigt, die für diesen speziellen Datentyp definiert werden können. Hier können Sie festlegen, was für dieses Feld erforderlich ist.

      * Viele Eigenschaften sind selbsterklärend. Weitere Informationen finden Sie unter [Eigenschaften](#properties).
      * Wenn Sie eine **Feldbeschriftung** eingeben, wird **Eigenschaftsname** automatisch gefüllt - wenn leer, und sie kann anschließend manuell aktualisiert werden.

      Beispiel:

      ![Feldeigenschaften](assets/cfm-models-05.png)


1. **So entfernen Sie ein Feld**

   Wählen Sie das entsprechende Feld aus und klicken/tippen Sie auf das Papierkorb-Symbol. Sie werden aufgefordert, den Vorgang zu bestätigen.

   ![Entfernen](assets/cfm-models-06.png)

1. Fügen Sie alle erforderlichen Felder hinzu und legen Sie bei Bedarf die zugehörigen Eigenschaften fest. Beispiel:

   ![Speichern](assets/cfm-models-07.png)

1. Wählen Sie **Speichern**, um die Definition beizubehalten.

## Datentypen {#data-types}

Zum Definieren Ihres Modells stehen unterschiedliche Datentypen zur Verfügung:

* **Einzeilentext**
   * Fügen Sie ein oder mehrere Felder mit einer einzelnen Textzeile hinzu. Die maximale Länge kann festgelegt werden.
* **Mehrzeilentext**
   * Ein Textbereich, der den Modus „Rich-Text“, „Nur-Text“ oder „Markdown“ aufweisen kann.
* **Zahl**
   * Fügen Sie ein oder mehrere numerische Felder hinzu.
* **Boolesch**
   * Fügen Sie ein boolesches Kontrollkästchen hinzu.
* **Datum und Uhrzeit**
   * Fügen Sie ein Datum und/oder eine Uhrzeit hinzu.
* **Aufzählung**
   * Fügen Sie eine Reihe von Kontrollkästchen, Optionsfeldern oder Dropdown-Feldern hinzu.
* **Tags**
   * Ermöglicht Fragmentautoren den Zugriff auf und die Auswahl von Tag-Bereichen.
* **Inhaltsreferenz**
   * Verweist auf andere Inhalte jeden Typs. Kann zum [Erstellen verschachtelter Inhalte](#using-references-to-form-nested-content) verwendet werden.
* **Fragmentreferenz**
   * Verweise auf andere Inhaltsfragmente; kann für [Erstellung verschachtelter Inhalte](#using-references-to-form-nested-content) verwendet werden
   * Der Datentyp kann so konfiguriert werden, dass Fragmentautoren Folgendes zulassen:
      * Bearbeiten Sie das referenzierte Fragment direkt.
      * Erstellen Sie ein neues Inhaltsfragment, basierend auf dem entsprechenden Modell
* **JSON-Objekt**
   * Ermöglicht dem Autor des Inhaltsfragments, die JSON-Syntax in die entsprechenden Elemente eines Fragments einzugeben.
      * Damit AEM direkte JSON speichern können, die Sie von einem anderen Dienst kopiert/eingefügt haben.
      * Der JSON wird übergeben und als JSON in GraphQL ausgegeben.
      * Schließt JSON-Syntaxhervorhebung, automatische Vervollständigung und Fehlerhervorhebung im Inhaltsfragmenteditor ein.

## Eigenschaften {#properties}

Viele Eigenschaften sind selbsterklärend. Im Folgenden finden Sie weitere Informationen zu bestimmten Eigenschaften:

* **Rendern als**
Die verschiedenen Möglichkeiten, das Feld in einem Fragment zu erstellen/zu rendern. Oft können Sie damit festlegen, ob dem Autor nur eine einzige Instanz des Feldes angezeigt wird oder ob er mehrere Instanzen erstellen darf.

* **Feldbezeichnung**
Durch die Eingabe einer 
**Feldbezeichnungen** wird automatisch ein **Eigenschaftsnamen** generiert, der bei Bedarf manuell aktualisiert werden kann.

* **Validierung**
Die grundlegende Basic ist mittels Mechanismen wie etwa die Eigenschaft **Erforderlich** verfügbar. Einige Datentypen verfügen über zusätzliche Validierungsfelder. Weitere Informationen finden Sie unter [Validierung](#validation).

* Beim Datentyp **Mehrzeilentext** können Sie den **Standardtyp** folgendermaßen definieren:

   * **Rich-Text**
   * **Markdown**
   * **Nur Text**

   Wenn Sie keinen Typ angeben, wird der Standardwert **Rich-Text** in diesem Feld verwendet.

   Änderungen am **Standardtyp** in einem Fragmentmodell werden erst dann auf vorhandene, zugehörige Inhaltsfragmente angewendet, wenn das Fragment im Editor geöffnet und gespeichert wurde.

* ****
UniqueContent (für das spezifische Feld) muss für alle Inhaltsfragmente, die vom aktuellen Modell erstellt werden, eindeutig sein.

   Dadurch wird sichergestellt, dass Inhaltsersteller Inhalte, die bereits in einem anderen Fragment desselben Modells hinzugefügt wurden, nicht wiederholen können.

   Beispielsweise kann ein **Einzelzeilentext**-Feld mit dem Namen `Country` im Inhaltsfragmentmodell nicht den Wert `Japan` in zwei abhängigen Inhaltsfragmenten haben. Eine Warnung wird ausgegeben, wenn der Versuch der zweiten Instanz unternommen wird.

   >[!NOTE]
   Die Eindeutigkeit ist pro Sprachstamm gewährleistet.

   >[!NOTE]
   Variationen können denselben Wert haben wie Varianten desselben Fragments, jedoch nicht denselben Wert wie bei anderen Fragmenten.**

* ****
TranslatableKontrollkästchen &quot;Translatable&quot;in einem Feld im CF-Modell-Editor aktivieren

   * Stellen Sie sicher, dass der Eigenschaftsname des Felds in der Konvertierungskonfiguration hinzugefügt wird, Kontext `/content/dam/<tenant>`, falls nicht bereits vorhanden.
   * Für GraphQL: Legen Sie im Feld Inhaltsfragment die Eigenschaft `<translatable>` auf `yes` fest, um den GraphQL-Abfrage-Filter für die JSON-Ausgabe mit nur übersetzbarem Inhalt zuzulassen.

* Weitere Informationen zu diesem bestimmten Datentyp und seinen Eigenschaften finden Sie unter **[Fragmentverweis (Verschachtelte Fragmente)](#fragment-reference-nested-fragments)**.

## Validierung {#validation}

Verschiedene Datentypen bieten jetzt die Möglichkeit, Validierungsanforderungen für den Zeitpunkt zu definieren, an dem Inhalt in das resultierende Fragment eingefügt wird:

* **Einzeilentext**
   * Führen Sie einen Vergleich mit einem vordefinierten Regex durch.
* **Zahl**
   * Suchen Sie nach bestimmten Werten.
* **Inhaltsreferenz**
   * Testen Sie, ob bestimmte Inhaltstypen vorhanden sind.
   * Es können nur Assets mit einer bestimmten Dateigröße oder einer kleineren Größe referenziert werden.
   * Es können nur Bilder in einem vordefinierten Bereich von Breite und/oder Höhe (in Pixel) referenziert werden.
* **Fragmentreferenz**
   * Testen Sie, ob ein bestimmtes Inhaltsfragmentmodell vorhanden ist.

<!--
  * Only predefined file types can be referenced.
  * No more than the predefined number of assets can be referenced. 
  * No more than the predefined number of fragments can be referenced.
-->

## Verwenden von Verweisen zum Formular &quot;Verschachtelter Inhalt&quot;{#using-references-to-form-nested-content}

Inhaltsfragmente können verschachtelte Inhalte mit einem der folgenden Datentypen bilden:

* **[Inhaltsreferenz](#content-reference)**
   * Bietet einen einfachen Verweis auf andere Inhalte; jedes Typs.
   * Kann für eine oder mehrere Verweise konfiguriert werden (im resultierenden Fragment).

* **[Fragmentverweis](#fragment-reference-nested-fragments)** (Verschachtelte Fragmente)
   * Verweist auf andere Fragmente, abhängig von den angegebenen Modellen.
   * Ermöglicht Ihnen, strukturierte Daten einzuschließen/abzurufen.

      >[!NOTE]
      Diese Methode ist in Verbindung mit [Headless Content Versand, der Inhaltsfragmente mit GraphQL](/help/assets/content-fragments/content-fragments-graphql.md) verwendet, besonders interessant.
   * Kann für eine oder mehrere Verweise konfiguriert werden (im resultierenden Fragment).

>[!NOTE]
AEM hat einen wiederkehrenden Schutz für:
* Inhaltsreferenzen
Dadurch wird verhindert, dass der Benutzer dem aktuellen Fragment einen Verweis hinzufügt. Dies kann zu einem leeren Dialogfeld für die Auswahl von Fragmentverweisen führen.

* Fragmentverweise in GraphQL
Wenn Sie eine Deep-Abfrage erstellen, die mehrere Inhaltsfragmente zurückgibt, auf die sich gegenseitig verwiesen wird, gibt sie beim ersten Auftreten null zurück.


### Inhaltsreferenz {#content-reference}

Mit der Inhaltsreferenz können Sie Inhalte aus einer anderen Quelle rendern. zum Beispiel Bild oder Inhaltsfragment.

Zusätzlich zu den Standardeigenschaften können Sie Folgendes angeben:

* Der **Stammpfad** für alle referenzierten Inhalte.
* Die Inhaltstypen, auf die verwiesen werden kann.
* Einschränkungen für Dateigrößen.
* Bildeinschränkungen.
   <!-- Check screenshot - might need update -->
   ![Inhaltsreferenz](assets/cfm-content-reference.png)

### Fragmentverweis (Verschachtelte Fragmente) {#fragment-reference-nested-fragments}

Der Fragmentverweis verweist auf ein oder mehrere Inhaltsfragmente. Diese Funktion ist besonders beim Abrufen von Inhalten für die Verwendung in Ihrer App interessant, da sie es Ihnen ermöglicht, strukturierte Daten mit mehreren Ebenen abzurufen.

Beispiel:

* Ein Modell, das Details für einen Mitarbeiter definiert; Dazu gehören:
   * Ein Verweis auf das Modell, das den Arbeitgeber definiert (Firma)

```xml
type EmployeeModel {
    name: String
    firstName: String
    company: CompanyModel
}

type CompanyModel {
    name: String
    street: String
    city: String
}
```

>[!NOTE]
Dies ist besonders in Verbindung mit [Headless Content Versand, der Inhaltsfragmente mit GraphQL](/help/assets/content-fragments/content-fragments-graphql.md) verwendet, von Interesse.

Zusätzlich zu den Standardeigenschaften können Sie Folgendes definieren:

* **Rendern als**:

   * **multifield**  - der Fragmentautor kann mehrere, einzelne Verweise erstellen

   * **Fragmentverweis** : Hiermit kann der Fragmentautor einen einzelnen Verweis auf ein Fragment auswählen

* **Modelltyp**
Es können mehrere Modelle ausgewählt werden. Beim Authoring des Inhaltsfragments müssen alle referenzierten Fragmente mit diesen Modellen erstellt worden sein.

* **Stammpfad**
Gibt einen Stammpfad für alle referenzierten Fragmente an.

* **Fragmenterstellung zulassen**

   Auf diese Weise kann der Fragmentautor ein neues Fragment erstellen, das auf dem entsprechenden Modell basiert.

   * **fragmentreferencecomposite** : Ermöglicht dem Fragmentautor das Erstellen einer Composite-Datei durch Auswahl mehrerer Fragmente

   <!-- Check screenshot - might need update -->
   ![Fragmentreferenz](assets/cfm-fragment-reference.png)

>[!NOTE]
Es gibt einen Mechanismus zum Wiederholungsschutz. Er untersagt dem Benutzer, das aktuelle Inhaltsfragment in der Fragmentreferenz auszuwählen. Dies kann zu einem leeren Dialogfeld für die Auswahl von Fragmentverweisen führen.
Es gibt auch einen Wiederholungsschutz für Fragmentverweise in GraphQL. Wenn Sie eine tiefe Abfrage über zwei Inhaltsfragmente erstellen, die sich gegenseitig referenzieren, wird null zurückgegeben.

## Aktivieren oder Deaktivieren von Inhaltsfragmentmodellen {#enabling-disabling-a-content-fragment-model}

Zur vollständigen Kontrolle über die Verwendung Ihrer Inhaltsfragmentmodelle können Sie deren Status festlegen.

### Aktivieren eines Inhaltsfragmentmodells {#enabling-a-content-fragment-model}

Nachdem ein Modell erstellt wurde, muss es aus folgenden Gründen aktiviert werden:

* Damit es zur Auswahl steht, wenn ein neues Inhaltsfragment erstellt wird.
* Damit es in einem Inhaltsfragmentmodell referenziert werden kann.
* Damit es für GraphQL verfügbar ist, sodass das Schema generiert wird.

So aktivieren Sie ein Modell, das folgendermaßen gekennzeichnet ist:

* **Entwurf**: neu (noch nie aktiviert).
* **Deaktiviert**: wurde eigens deaktiviert.

Sie verwenden die Option **Aktivieren** aus einem der folgenden Bereiche:

* Die obere Symbolleiste, wenn das erforderliche Modell ausgewählt ist.
* Die entsprechende Schnellaktion (bewegen Sie den Mauszeiger über das entsprechende Modell).

![Aktivieren eines Entwurfs oder deaktivierten Modells](assets/cfm-status-enable.png)

### Deaktivieren eines Inhaltsfragmentmodells {#disabling-a-content-fragment-model}

Ein Modell lässt sich auch aus folgenden Gründen deaktivieren:

* Das Modell ist nicht mehr als Grundlage für die Erstellung *neuer* Inhaltsfragmente verfügbar.
* Beachten Sie jedoch Folgendes:
   * Das GraphQL-Schema wird weiterhin generiert und kann weiterhin abgefragt werden (um eine Beeinträchtigung der JSON-API zu vermeiden).
   * Inhaltsfragmente, die auf dem Modell basieren, können weiterhin abgefragt und vom GraphQL-Endpunkt zurückgegeben werden.
* Das Modell kann nicht mehr referenziert werden. Vorhandene Referenzen bleiben jedoch unverändert und können weiterhin abgefragt und vom GraphQL-Endpunkt zurückgegeben werden.

Um ein Modell zu deaktivieren, das als **Aktiviert** gekennzeichnet ist, verwenden Sie die Option **Deaktivieren** aus einem der folgenden Bereiche:

* Die obere Symbolleiste, wenn das erforderliche Modell ausgewählt ist.
* Die entsprechende Schnellaktion (bewegen Sie den Mauszeiger über das entsprechende Modell).

![Deaktivieren eines aktivierten Modells](assets/cfm-status-disable.png)

## Zulassen von Inhaltsfragmentmodellen im Asset-Ordner {#allowing-content-fragment-models-assets-folder}

Zur Implementierung der Inhaltsverwaltung können Sie **Richtlinien** im Ordner &quot;Assets&quot;konfigurieren, um zu steuern, welche Inhaltsfragmentmodelle für die Fragmenterstellung in diesem Ordner zulässig sind.

>[!NOTE]
Der Mechanismus ähnelt [dem Zulassen von Seitenvorlagen](/help/sites-cloud/authoring/features/templates.md#allowing-a-template-author) für eine Seite und deren untergeordnete Elemente in erweiterten Eigenschaften einer Seite.

So konfigurieren Sie die **Richtlinien** für **Zulässige Inhaltsfragmentmodelle**:

1. Navigieren Sie zum gewünschten Asset-Ordner und öffnen Sie **Eigenschaften**.

1. Öffnen Sie die Registerkarte **Richtlinien**, in der Sie Folgendes konfigurieren können:

   * **Vererbt von`<folder>`**

      Richtlinien werden beim Erstellen neuer untergeordneter Ordner automatisch übernommen. Die Richtlinie kann neu konfiguriert werden (und die Vererbung ist beschädigt), wenn Unterordner Modelle zulassen müssen, die vom übergeordneten Ordner abweichen.

   * **Zugelassene Inhaltsfragmentmodelle nach Pfad**

      Es können mehrere Modelle zugelassen werden.

   * **Zulässige Inhaltsfragmentmodelle nach Tag**

      Es können mehrere Modelle zugelassen werden.
   ![Richtlinie zum Inhaltsfragmentmodell](assets/cfm-model-policy-assets-folder.png)

1. **Änderungen** speichern.

Die für einen Ordner zulässigen Inhaltsfragmentmodelle werden wie folgt aufgelöst:
* Die **Richtlinien** für **Zulässige Inhaltsfragmentmodelle**.
* Falls leer, versuchen Sie, die Richtlinie mithilfe der Vererbungsregeln zu bestimmen.
* Wenn die Vererbungskette kein Ergebnis liefert, prüfen Sie die **Cloud Services**-Konfiguration für diesen Ordner (auch zuerst direkt und dann über Vererbung).
* Wenn keine der oben genannten Ergebnisse zu liefern ist, gibt es keine zulässigen Modelle für diesen Ordner.

## Löschen eines Inhaltsfragmentmodells {#deleting-a-content-fragment-model}

>[!CAUTION]
Das Löschen eines Inhaltsfragmentmodells wirkt sich unter Umständen auf abhängige Fragmente aus.

So löschen Sie ein Inhaltsfragmentmodell:

1. Navigieren Sie zu **Tools** > **Assets** und öffnen Sie dann **Inhaltsfragmentmodelle**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Wählen Sie Ihr Modell und anschließend die Option **Löschen** aus der Symbolleiste aus.

   >[!NOTE]
   Wenn es Verweise auf das Modell gibt, wird Ihnen ein Warnhinweis angezeigt. Ergreifen Sie die entsprechenden Maßnahmen.

## Veröffentlichen eines Inhaltsfragmentmodells   {#publishing-a-content-fragment-model}

Inhaltsfragmentmodelle müssen zeitgleich mit oder im Vorfeld der Veröffentlichung abhängiger Inhaltsfragmente veröffentlicht werden.

So veröffentlichen Sie ein Inhaltsfragmentmodell:

1. Navigieren Sie zu **Tools** > **Assets** und öffnen Sie dann **Inhaltsfragmentmodelle**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Wählen Sie Ihr Modell und anschließen die Option **Veröffentlichen** aus der Symbolleiste aus.
Der Status „Veröffentlicht“ wird in der Konsole angezeigt.

   >[!NOTE]
   Wenn Sie Inhaltsfragmente veröffentlichen, deren Modell noch nicht veröffentlicht wurde, wird dies in der Auswahlliste angezeigt und das Modell wird mit dem Fragment veröffentlicht.

## Rückgängigmachen der Veröffentlichung eines Inhaltsfragmentmodells {#unpublishing-a-content-fragment-model}

Die Veröffentlichung von Inhaltsfragmentmodellen kann rückgängig gemacht werden, wenn sie nicht von Fragmenten referenziert werden.

So machen Sie die Veröffentlichung eines Inhaltsfragmentmodells rückgängig:

1. Navigieren Sie zu **Tools** > **Assets** und öffnen Sie dann **Inhaltsfragmentmodelle**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Wählen Sie Ihr Modell und anschließen die Option **Veröffentlichung rückgängig machen** aus der Symbolleiste aus.
Der Status „Veröffentlicht“ wird in der Konsole angezeigt.
