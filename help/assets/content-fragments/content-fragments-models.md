---
title: Inhaltsfragmentmodelle (Assets – Inhaltsfragmente)
description: Erfahren Sie, inwiefern Inhaltsfragmentmodelle als Grundlage für Ihre Headless-Inhalte in AEM dienen und es Ihnen ermöglichen, Inhaltsfragmente mit strukturierten Inhalten zu erstellen.
exl-id: fd706c74-4cc1-426d-ab56-d1d1b521154b
feature: Content Fragments, GraphQL API
role: User, Admin, Architect
solution: Experience Manager Sites
source-git-commit: 883eadc8ce2c84eba526b081ef90c678845989aa
workflow-type: ht
source-wordcount: '3120'
ht-degree: 100%

---

# Inhaltsfragmentmodelle {#content-fragment-models}

Inhaltsfragmentmodelle in AEM definieren die Inhaltsstruktur für Ihre [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md) und dienen als Grundlage für Ihre Headless-Inhalte.

So verwenden Sie Inhaltsfragmentmodelle:

1. [Aktivieren Sie die Funktion für Inhaltsfragmentmodelle für Ihre Instanz.](/help/assets/content-fragments/content-fragments-configuration-browser.md)
1. [Erstellen](#creating-a-content-fragment-model) und [konfigurieren](#defining-your-content-fragment-model) Sie Ihre Inhaltsfragmentmodelle.
1. [Aktivieren Ihrer Inhaltsfragmentmodelle](#enabling-disabling-a-content-fragment-model) zur Verwendung beim Erstellen von Inhaltsfragmenten
1. [Lassen Sie Ihre Inhaltsfragmentmodelle in den erforderlichen Asset-Ordnern zu](#allowing-content-fragment-models-assets-folder), indem Sie **Richtlinien** konfigurieren.

## Erstellen eines Inhaltsfragmentmodells {#creating-a-content-fragment-model}

1. Navigieren Sie zu **Tools** > **Allgemein** und öffnen Sie dann **Inhaltsfragmentmodelle**.
1. Navigieren Sie zu dem Ordner, der Ihrer [Konfiguration oder Unterkonfiguration](/help/assets/content-fragments/content-fragments-configuration-browser.md) entspricht.
1. Verwenden Sie **Erstellen**, um den Assistenten zu öffnen.

   >[!CAUTION]
   >
   >Wenn die [Verwendung von Inhaltsfragmentmodellen nicht aktiviert wurde](/help/assets/content-fragments/content-fragments-configuration-browser.md), ist die Option **Erstellen** nicht verfügbar.

1. Geben Sie den **Modelltitel** an.
Sie können auch verschiedene Eigenschaften definieren, zum Beispiel: **Tags**, und eine **Beschreibung** hinzufügen sowie **Modell aktivieren** auswählen, um ggf. [das Modell zu aktivieren](#enabling-disabling-a-content-fragment-model).

   >[!NOTE]
   >
   >Weitere Details zum **Standard-URL-Vorschaumuster** finden Sie unter [Inhaltsfragmentmodell – Eigenschaften](#content-fragment-model-properties).

   ![Titel und Beschreibung](assets/cfm-models-02.png)

1. Verwenden Sie **Erstellen**, um das leere Modell zu speichern. Eine Meldung weist auf den Erfolg der Aktion hin. Sie können **Öffnen** auswählen, um das Modell sofort zu bearbeiten oder **Fertig**, um zur Konsole zurückzukehren.

## Definieren des Inhaltsfragmentmodells {#defining-your-content-fragment-model}

Das Inhaltsfragmentmodell definiert effektiv die Struktur der resultierenden Inhaltsfragmente unter Verwendung unterschiedlicher **[Datentypen](#data-types)**. Mithilfe des Modell-Editors können Sie Instanzen der Datentypen hinzufügen und diese dann so konfigurieren, dass die erforderlichen Felder erstellt werden:

>[!CAUTION]
>
>Die Bearbeitung eines vorhandenen Inhaltsfragmentmodells kann sich auf abhängige Fragmente auswirken.

1. Navigieren Sie zu **Tools** > **Allgemein** und öffnen Sie dann **Inhaltsfragmentmodelle**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Öffnen Sie das zu **bearbeitende** Modell; nutzen Sie dazu entweder die entsprechende Schnellaktion oder wählen Sie das Modell und anschließend die Aktion aus der Symbolleiste aus.

   Nach dem Öffnen zeigt der Modell-Editor Folgendes an:

   * Links: Felder bereits definiert
   * Rechts: verfügbare **Datentypen** für das Erstellen von Feldern (und **Eigenschaften**, die für erstellte Felder verwendet werden können)

   >[!NOTE]
   >
   >Wenn ein Feld ein **Pflichtfeld** ist, wird die **Bezeichnung** im linken Bereich mit einem Stern markiert (**&#42;**).

![Eigenschaften](assets/cfm-models-03.png)

1. **So fügen Sie ein Feld hinzu**

   * Ziehen Sie einen erforderlichen Datentyp an die entsprechende Stelle für ein Feld:

     ![Datentyp zum Feld](assets/cfm-models-04.png)

   * Wenn ein Feld zum Modell hinzugefügt wurde, werden im rechten Fenster die **Eigenschaften** angezeigt, die für diesen speziellen Datentyp definiert werden können. Hier können Sie festlegen, was für dieses Feld erforderlich ist.

      * Viele Eigenschaften sind selbsterklärend. Weitere Informationen finden Sie unter [Eigenschaften](#properties).
      * Wenn Sie eine **Feldbeschriftung** eingeben, wird **Eigenschaftsname** automatisch gefüllt, wenn das Feld leer ist, und kann anschließend manuell aktualisiert werden.

        >[!CAUTION]
        >
        >Wenn Sie die Eigenschaft **Eigenschaftsname** für einen Datentyp manuell aktualisieren, beachten Sie, dass Namen nur A–Z, a–z, 0–9 und den Unterstrich „_“ als Sonderzeichen enthalten dürfen.
        >
        >Wenn in früheren Versionen von AEM erstellte Modelle unzulässige Zeichen enthalten, entfernen oder ändern Sie diese Zeichen.

     Zum Beispiel:

     ![Feldeigenschaften](assets/cfm-models-05.png)

1. **So entfernen Sie ein Feld**

   Wählen Sie das entsprechende Feld aus und wählen Sie das Papierkorb-Symbol aus. Sie werden aufgefordert, die Aktion zu bestätigen.

   ![remove](assets/cfm-models-06.png)

1. Fügen Sie alle erforderlichen Felder hinzu und legen Sie bei Bedarf die zugehörigen Eigenschaften fest. Zum Beispiel:

   ![Speichern](assets/cfm-models-07.png)

1. Wählen Sie **Speichern**, um die Definition beizubehalten.

## Datentypen {#data-types}

Zum Definieren Ihres Modells stehen unterschiedliche Datentypen zur Verfügung:

* **Einzeilentext**
   * Fügt ein Feld für eine einzelne Textzeile hinzu; die maximale Länge kann definiert werden.
   * Das Feld kann so konfiguriert werden, dass Fragmentautorinnen und -autoren neue Instanzen des Felds erstellen können.

* **Mehrzeilentext**
   * Ein Textbereich, der Rich Text, Nur Text oder Markdown sein kann
   * Das Feld kann so konfiguriert werden, dass Fragmentautorinnen und -autoren neue Instanzen des Felds erstellen können.

  >[!NOTE]
  >
  >Ob es sich bei dem Textbereich um Rich Text, Nur Text oder Markdown handelt, wird im Modell durch die Eigenschaft **Standardtyp** definiert.
  >
  >Dieses Format kann nicht über den [Inhaltsfragmenteditor](/help/sites-cloud/administering/content-fragments/authoring.md), sondern nur vom Modell aus geändert werden.

* **Zahl**
   * Fügt ein numerisches Feld hinzu.
   * Das Feld kann so konfiguriert werden, dass Fragmentautorinnen und -autoren neue Instanzen des Felds erstellen können.

* **Boolesch**
   * Fügen Sie ein boolesches Kontrollkästchen hinzu.

* **Datum und Uhrzeit**
   * Fügt ein Datums- und/oder Zeitfeld hinzu.

* **Aufzählung**
   * Fügt einen Satz Kontrollkästchen, Optionsfelder oder Dropdown-Felder hinzu.
      * Sie können die für Fragmentautorinnen und -autoren verfügbaren Optionen festlegen.

* **Tags**
   * Ermöglicht Fragmentautoren den Zugriff auf und die Auswahl von Tag-Bereichen.

* **Inhaltsreferenz**
   * Verweist auf andere Inhalte jeden Typs. Kann zum [Erstellen verschachtelter Inhalte](#using-references-to-form-nested-content) verwendet werden.
   * Wenn ein Bild referenziert wird, kann wahlweise eine Miniatur angezeigt werden.
   * Das Feld kann so konfiguriert werden, dass Fragmentautorinnen und -autoren neue Instanzen des Felds erstellen können.

* **Fragmentreferenz**
   * Verweist auf andere Inhaltsfragmente. Kann zum [Erstellen verschachtelter Inhalte](#using-references-to-form-nested-content) verwendet werden.
   * Das Feld kann so konfiguriert werden, dass es den Fragmentautorinnen und -autoren Folgendes ermöglicht:
      * Direktes Bearbeiten des referenzierten Fragments
      * Erstellen eines neuen Inhaltsfragments basierend auf dem entsprechenden Modell
      * Erstellen neuer Instanzen des Felds

* **JSON-Objekt**
   * Ermöglicht es der Autorin bzw. dem Autor des Inhaltsfragments, JSON-Syntax in die entsprechenden Elemente eines Fragments einzugeben.
      * Damit AEM direktes JSON speichern kann, das Sie von einem anderen Service kopiert/eingefügt haben.
      * Das JSON wird weitergegeben und als JSON in GraphQL ausgegeben.
      * Umfasst JSON-Syntaxhervorhebung, automatische Vervollständigung und Fehlerhervorhebung im Inhaltsfragmenteditor.

* **Registerkarten-Platzhalter**
   * Ermöglicht die Einführung von Registerkarten zur Bearbeitung des Inhalts von Inhaltsfragmenten.
      * Dies wird als Trennzeichen im Modell-Editor angezeigt, das Abschnitte der Liste der Inhaltsdatentypen trennt. Jede Instanz stellt den Beginn einer neuen Registerkarte dar.
      * Im Fragment-Editor wird jede Instanz als Registerkarte angezeigt.

     >[!NOTE]
     >
     >Dieser Datentyp dient ausschließlich zur Formatierung und wird vom GraphQL-Schema von AEM ignoriert.

## Eigenschaften {#properties}

Viele Eigenschaften sind selbsterklärend. Im Folgenden finden Sie weitere Informationen zu bestimmten Eigenschaften:

* **Eigenschaftsname**

  Wenn Sie diese Eigenschaft für einen Datentyp manuell aktualisieren, beachten Sie, *dass* Namen **nur** A–Z, a–z, 0–9 und den Unterstrich „_“ als Sonderzeichen enthalten dürfen.

  >[!CAUTION]
  >
  >Wenn in früheren Versionen von AEM erstellte Modelle unzulässige Zeichen enthalten, entfernen oder ändern Sie diese Zeichen.

* **Rendern als**
Die verschiedenen Möglichkeiten, das Feld in einem Fragment zu erstellen/zu rendern. Mit dieser Eigenschaft können Sie oft festlegen, ob die Autorin bzw. der Autor nur eine einzige Instanz des Feldes sieht oder ob mehrere Instanzen erstellt werden dürfen. Wenn **Mehrere Felder** verwendet wird, können Sie die minimale und maximale Anzahl von Einträgen festlegen. Siehe [Validierung](#validation) für weitere Informationen.

* **Feldtitel**
Bei Eingabe eines **Feldtitels** wird automatisch ein **Eigenschaftsname** generiert, der dann ggf. manuell aktualisiert werden kann.

* **Validierung**
Die grundlegende Basic ist mittels Mechanismen wie etwa die Eigenschaft **Erforderlich** verfügbar. Einige Datentypen verfügen über zusätzliche Validierungsfelder. Weitere Informationen finden Sie unter [Validierung](#validation).

* Beim Datentyp **Mehrzeilentext** können Sie den **Standardtyp** folgendermaßen definieren:

   * **Rich-Text**
   * **Markdown**
   * **Nur Text**

  Wenn Sie keinen Typ angeben, wird der Standardwert **Rich-Text** in diesem Feld verwendet.

  Änderungen am **Standardtyp** in einem Fragmentmodell werden erst dann auf vorhandene, zugehörige Inhaltsfragmente angewendet, wenn das Fragment im Editor geöffnet und gespeichert wurde.

* **Eindeutiger**
Content (für das spezifische Feld) muss für alle Inhaltsfragmente, die anhand des aktuellen Modells erstellt werden, eindeutig sein.

  Dadurch wird sichergestellt, dass Inhaltsersteller Content, der bereits einem anderen Fragment desselben Modells hinzugefügt wurde, nicht wiederholen können.

  Beispielsweise kann ein **einzeiliges Textfeld** mit dem Namen `Country` im Inhaltsfragmentmodell nicht den Wert `Japan` in zwei abhängigen Inhaltsfragmenten haben. Eine Warnung wird ausgegeben, wenn versucht wird, eine zweite Instanz zu erstellen.

  >[!NOTE]
  >
  >Die Eindeutigkeit wird pro Sprachstamm gewährleistet.

  >[!NOTE]
  >
  >Varianten können denselben *eindeutigen* Wert haben wie Varianten desselben Fragments, jedoch nicht denselben Wert wie Varianten anderer Fragmente.

  >[!CAUTION]
  >
  >Wenn Sie MSM verwenden möchten (wodurch Kopien von Inhaltsfragmenten erstellt werden), sollten Sie alle **Eindeutig**-Einschränkungen aus allen Datentypen entfernen, die in den jeweiligen Inhaltsfragmentmodellen verwendet werden.

* Weitere Informationen zu diesem bestimmten Datentyp und seinen Eigenschaften finden Sie unter **[Inhaltsreferenz](#content-reference)**.

* Weitere Informationen zu diesem bestimmten Datentyp und seinen Eigenschaften finden Sie unter **[Fragmentreferenz (verschachtelte Fragmente)](#fragment-reference-nested-fragments)**.

* **Übersetzbar**

  Durch Aktivieren des Kontrollkästchens **Übersetzbar** für ein Feld im Editor für Inhaltsfragmentmodelle geschieht Folgendes:

   * Es wird sichergestellt, dass der Eigenschaftsname zur Übersetzungskonfiguration im Kontext `/content/dam/<sites-configuration>` hinzugefügt wird, falls er noch nicht vorhanden ist.
   * Für GraphQL: Im Inhaltsfragmentfeld wird die Eigenschaft `<translatable>` auf `yes` festgelegt, um den GraphQL-Abfragefilter für die JSON-Ausgabe nur mit übersetzbarem Inhalt zuzulassen.

## Validierung {#validation}

Verschiedene Datentypen bieten jetzt die Möglichkeit, Validierungsanforderungen für den Zeitpunkt zu definieren, an dem Inhalt in das resultierende Fragment eingefügt wird:

* **Einzeilentext**
   * Führen Sie einen Vergleich mit einem vordefinierten Regex durch.
* **Zahl**
   * Suchen Sie nach bestimmten Werten.
* **Inhaltsreferenz**
   * Testen Sie, ob bestimmte Content-Typen vorhanden sind.
   * Es können nur Assets bis zur angegebenen maximalen Dateigröße referenziert werden.
   * Es können nur Bilder in einem vordefinierten Bereich von Breite und/oder Höhe (in Pixel) referenziert werden.
* **Fragmentreferenz**
   * Testen Sie, ob ein bestimmtes Inhaltsfragmentmodell vorhanden ist.
* **Mindestanzahl der Elemente**/**Maximale Anzahl der Elemente**

  Felder, die als **Mehrere Felder** festgelegt wurden (mit **Rendern als**) haben die Optionen:

   * **Mindestanzahl der Elemente**
   * **Maximale Anzahl der Elemente**

  Diese werden wie folgt validiert:

   * Der Maximalwert wird im [originalen Inhaltsfragmenteditor](/help/assets/content-fragments/content-fragments-variations.md) validiert.
   * Beide werden im [Inhaltsfragmenteditor](/help/sites-cloud/administering/content-fragments/authoring.md) validiert.

## Verwenden von Verweisen, um verschachtelten Inhalt zu bilden {#using-references-to-form-nested-content}

Inhaltsfragmente können mit einem der folgenden Datentypen verschachtelte Inhalte bilden:

* **[Inhaltsreferenz](#content-reference)**
   * Bietet einen einfachen Verweis auf anderen Content jedes Typs.
   * Kann für einen oder mehrere Verweise konfiguriert werden (im resultierenden Fragment).

* **[Fragmentreferenz](#fragment-reference-nested-fragments)** (verschachtelte Fragmente)
   * Verweist auf andere Fragmente, abhängig von den angegebenen Modellen.
   * Ermöglicht das Einschließen/Abrufen strukturierter Daten.

     >[!NOTE]
     >
     >Diese Methode ist in Verbindung mit der [Headless-Bereitstellung mithilfe von Inhaltsfragmenten mit GraphQL](/help/assets/content-fragments/content-fragments-graphql.md) besonders interessant.
   * Kann für einen oder mehrere Verweise konfiguriert werden (im resultierenden Fragment).

>[!NOTE]
>
>AEM bietet einen Wiederholungsschutz für:
>
>* Inhaltsreferenzen
>Verhindert, dass der Benutzer dem aktuellen Fragment einen Verweis hinzufügt. Dies kann zu einem leeren Dialogfeld für die Auswahl von Fragmentreferenzen führen.
>
>* Fragmentreferenzen in GraphQL
>Wenn Sie eine Deep-Abfrage erstellen, die mehrere Inhaltsfragmente zurückgibt, die gegenseitig aufeinander verweisen, gibt sie beim ersten Auftreten NULL zurück.

### Inhaltsreferenz {#content-reference}

Mit der Inhaltsreferenz können Sie Inhalte aus einer anderen Quelle rendern, zum Beispiel ein Bild oder Inhaltsfragment.

Zusätzlich zu den Standardeigenschaften können Sie Folgendes angeben:

* Den **Stammpfad** für referenzierte Inhalte
* Die Inhaltstypen, auf die verwiesen werden kann
* Einschränkungen bezüglich der Dateigrößen
* Wenn ein Bild referenziert wird:
   * Miniatur anzeigen
   * Bildeinschränkungen hinsichtlich Höhe und Breite

![Inhaltsreferenz](assets/cfm-content-reference.png)

### Fragmentreferenz (verschachtelte Fragmente) {#fragment-reference-nested-fragments}

Die Fragmentreferenz verweist auf mindestens ein Inhaltsfragment. Diese Funktion ist besonders beim Abrufen von Inhalten für die Verwendung in Ihrer Anwendung interessant, da sie Ihnen das Abrufen strukturierter Daten mit mehreren Ebenen ermöglicht.

Zum Beispiel:

* Ein Modell, das Details für einen Mitarbeiter definiert, beispielsweise:
   * Ein Verweis auf das Modell, das den Arbeitgeber (Firma) definiert

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
>
>Dies ist besonders in Verbindung mit der [Headless-Bereitstellung mithilfe von Inhaltsfragmenten mit GraphQL](/help/assets/content-fragments/content-fragments-graphql.md) von Interesse.

Zusätzlich zu den Standardeigenschaften können Sie Folgendes definieren:

* **Rendern als**:

   * **multifield**: Der Fragmentautor kann mehrere einzelne Verweise erstellen.

   * **fragmentreference**: Der Fragmentautor kann einen einzelnen Verweis auf ein Fragment auswählen.

* **Modelltyp**
Es können mehrere Modelle ausgewählt werden. Beim Erstellen des Inhaltsfragments müssen alle referenzierten Fragmente mit diesen Modellen erstellt worden sein.

* **Stammpfad**
Gibt einen Stammpfad für referenzierte Fragmente an.

* **Fragmenterstellung zulassen**

  Auf diese Weise kann die Autorin oder der Autor des Fragments ein Fragment auf der Grundlage des entsprechenden Modells erstellen.

   * **fragmentreferencecomposite**: Ermöglicht dem Fragmentautor das Erstellen einer Composite-Datei durch Auswahl mehrerer Fragmente.

  ![Fragmentreferenz](assets/cfm-fragment-reference.png)

>[!NOTE]
>
>Es gibt einen Mechanismus zum Wiederholungsschutz. Dieser verhindert, dass Benutzer in der Fragmentreferenz das aktuelle Inhaltsfragment auswählen. Dies kann zu einem leeren Dialogfeld für die Auswahl von Fragmentreferenzen führen.
>
>Es gibt auch einen Wiederholungsschutz für Fragmentreferenzen in GraphQL. Wenn Sie eine Deep-Abfrage über zwei Inhaltsfragmente erstellen, die gegenseitig aufeinander verweisen, wird NULL zurückgegeben.

## Inhaltsfragmentmodell – Eigenschaften {#content-fragment-model-properties}

Sie können die **Eigenschaften** eines Inhaltsfragmentmodells bearbeiten:

* **Allgemein**
   * **Modell-Titel**
   * **Tags**
   * **Beschreibung**
   * **Bild hochladen**
   * **Standardmäßige Echtzeitansicht für URL-Muster**

     >[!NOTE]
     >
     >Dies wird nur vom *neuen* Inhaltsfragment-Editor verwendet. Weitere Informationen finden Sie unter [Inhaltsfragmentmodelle](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#content-fragment-model-properties).


## Aktivieren oder Deaktivieren von Inhaltsfragmentmodellen {#enabling-disabling-a-content-fragment-model}

Zur vollständigen Kontrolle über die Verwendung Ihrer Inhaltsfragmentmodelle können Sie deren Status festlegen.

### Aktivieren eines Inhaltsfragmentmodells {#enabling-a-content-fragment-model}

Wenn ein Modell erstellt wird, muss es aus folgenden Gründen aktiviert werden:

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

Zur Implementierung der Inhaltsverwaltung können Sie **Richtlinien** im Asset-Ordner konfigurieren, um zu steuern, welche Inhaltsfragmentmodelle für die Fragmenterstellung in diesem Ordner zulässig sind.

>[!NOTE]
>
>Der Mechanismus ähnelt dem [Zulassen von Seitenvorlagen](/help/sites-cloud/authoring/page-editor/templates.md#allowing-a-template-author) für eine Seite und deren untergeordnete Elemente in den erweiterten Eigenschaften einer Seite.

So konfigurieren Sie die **Richtlinien** für **Zulässige Inhaltsfragmentmodelle**:

1. Navigieren Sie zum gewünschten Asset-Ordner und öffnen Sie **Eigenschaften**.

1. Öffnen Sie die Registerkarte **Richtlinien**, in der Sie Folgendes konfigurieren können:

   * **Vererbt von`<folder>`**

     Richtlinien werden beim Erstellen neuer untergeordneter Ordner automatisch übernommen. Die Richtlinie kann neu konfiguriert (und die Vererbung aufgehoben) werden, wenn Unterordner Modelle zulassen müssen, die vom übergeordneten Ordner abweichen.

   * **Zugelassene Inhaltsfragmentmodelle nach Pfad**

     Es können mehrere Modelle zugelassen werden.

   * **Zugelassene Inhaltsfragmentmodelle nach Tag**

     Es können mehrere Modelle zugelassen werden.

   ![Richtlinie für Inhaltsfragmentmodell](assets/cfm-model-policy-assets-folder.png)

1. **Speichern** Sie die Änderungen.

Die für einen Ordner zulässigen Inhaltsfragmentmodelle werden wie folgt aufgelöst:

* Die **Richtlinien** für **Zulässige Inhaltsfragmentmodelle**.
* Falls leer, versuchen Sie, die Richtlinie mithilfe der Vererbungsregeln zu bestimmen.
* Wenn die Vererbungskette kein Ergebnis liefert, prüfen Sie die **Cloud Services**-Konfiguration für diesen Ordner (auch zuerst direkt und dann über Vererbung).
* Wenn keines der oben genannten Verfahren Ergebnisse liefert, gibt es keine zulässigen Modelle für diesen Ordner.

## Löschen eines Inhaltsfragmentmodells {#deleting-a-content-fragment-model}

>[!CAUTION]
>
>Das Löschen eines Inhaltsfragmentmodells kann sich auf abhängige Fragmente auswirken.

So löschen Sie ein Inhaltsfragmentmodell:

1. Navigieren Sie zu **Tools** > **Allgemein** und öffnen Sie dann **Inhaltsfragmentmodelle**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Wählen Sie Ihr Modell und anschließend die Option **Löschen** aus der Symbolleiste aus.

   >[!NOTE]
   >
   >Wenn auf das Modell verwiesen wird, wird eine Warnung angezeigt. Ergreifen Sie entsprechende Maßnahmen.

## Veröffentlichen eines Inhaltsfragmentmodells {#publishing-a-content-fragment-model}

Inhaltsfragmentmodelle müssen zeitgleich mit oder im Vorfeld der Veröffentlichung abhängiger Inhaltsfragmente veröffentlicht werden.

So veröffentlichen Sie ein Inhaltsfragmentmodell:

1. Navigieren Sie zu **Tools** > **Allgemein** und öffnen Sie dann **Inhaltsfragmentmodelle**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Wählen Sie Ihr Modell und anschließen die Option **Veröffentlichen** aus der Symbolleiste aus.
Der Status „Veröffentlicht“ wird in der Konsole angezeigt.

   >[!NOTE]
   >
   >Wenn Sie ein Inhaltsfragment veröffentlichen, dessen Modell noch nicht veröffentlicht wurde, wird dies in einer Auswahlliste angezeigt und das Modell wird mit dem Fragment veröffentlicht.

## Rückgängigmachen der Veröffentlichung eines Inhaltsfragmentmodells {#unpublishing-a-content-fragment-model}

Die Veröffentlichung von Inhaltsfragmentmodellen kann rückgängig gemacht werden, sofern sie nicht von Fragmenten referenziert werden.

So machen Sie die Veröffentlichung eines Inhaltsfragmentmodells rückgängig:

1. Navigieren Sie zu **Tools** > **Allgemein** und öffnen Sie dann **Inhaltsfragmentmodelle**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Wählen Sie Ihr Modell und anschließen die Option **Veröffentlichung aufheben** aus der Symbolleiste aus.
Der Status „Veröffentlicht“ wird in der Konsole angezeigt.

Wenn Sie versuchen, die Veröffentlichung eines Modells aufzuheben, das aktuell von einem oder mehreren Fragmenten verwendet wird, werden Sie über eine Fehlermeldung über Folgendes informiert:

![Fehlermeldung zum Inhaltsfragmentmodell beim Rückgängigmachen der Veröffentlichung eines verwendeten Modells](assets/cfm-model-unpublish-error.png)

In der Meldung wird vorgeschlagen, dass Sie das Bedienfeld [Verweise](/help/sites-cloud/authoring/basic-handling.md#references) überprüfen, um weitere Nachforschungen anzustellen:

![Inhaltsfragmentmodell in Verweisen](assets/cfm-model-references.png)

## Gesperrte (veröffentlichte) Inhaltsfragmentmodelle {#locked-published-content-fragment-models}

Diese Funktion bietet Governance für Inhaltsfragmentmodelle, die veröffentlicht wurden.

### Die Herausforderung {#the-challenge}

* Inhaltsfragmentmodelle bestimmen das Schema für GraphQL-Abfragen in AEM.

   * AEM GraphQL-Schemas werden erstellt, sobald ein Inhaltsfragmentmodell erstellt wird, und sie können in der Autoren- und Veröffentlichungsumgebung vorhanden sein.

   * Schemas in der Veröffentlichungsinstanz sind die wichtigsten, da sie die Grundlage für die Live-Bereitstellung von Inhaltsfragmentinhalten im JSON-Format bieten.

* Probleme können auftreten, wenn Inhaltsfragmentmodelle geändert oder bearbeitet werden. Das bedeutet, dass sich das Schema ändert, was wiederum vorhandene GraphQL-Abfragen beeinflussen kann.

* Das Hinzufügen neuer Felder zu einem Inhaltsfragmentmodell sollte (in der Regel) keine schädlichen Auswirkungen haben. Wenn Sie jedoch vorhandene Datenfelder (z. B. deren Namen) ändern oder Felddefinitionen löschen, werden vorhandene GraphQL-Abfragen bei der Anforderung dieser Felder beschädigt.

### Die Voraussetzungen {#the-requirements}

* Die Benutzenden wurden auf die Risiken aufmerksam gemacht, die bei der Bearbeitung von Modellen auftreten, die bereits für die Bereitstellung von Live-Inhalten verwendet werden (d. h. von Modellen, die veröffentlicht wurden).

* Außerdem die Vermeidung von unbeabsichtigten Änderungen.

In beiden Fällen können Abfragen beschädigt werden, wenn die geänderten Modelle erneut veröffentlicht werden.

### Die Lösung {#the-solution}

Um diese Probleme zu lösen, werden die Inhaltsfragmentmodelle in der Autorenumgebung durch einen SCHREIBGESCHÜTZTEN Modus *gesperrt*, sobald sie veröffentlicht wurden. Dies wird durch **Gesperrt** angezeigt:

![Karte des gesperrten Inhaltsfragmentmodells](assets/cfm-model-locked.png)

Wenn das Modell **Gesperrt** ist (im schreibgeschützten Modus), können Sie die Inhalte und die Struktur der Modelle anzeigen, sie jedoch nicht bearbeiten.

Sie können **Gesperrte** Modelle entweder aus der Konsole heraus oder im Modell-Editor verwalten:

* Konsole

  In der Konsole können Sie den SCHREIBGESCHÜTZTEN Modus mit den Aktionen **Entsperren** und **Sperren** in der Symbolleiste verwalten:

  ![Symbolleiste des gesperrten Inhaltsfragmentmodells](assets/cfm-model-locked.png)

   * Sie können ein Modell zum Aktivieren von Bearbeitungen **Entsperren**.

     Wenn Sie **Entsperren** wählen, wird eine Warnung angezeigt, und Sie müssen die **Entsperren**-Aktion bestätigen:
     ![Meldung beim Entsperren des Inhaltsfragmentmodells](assets/cfm-model-unlock-message.png)

     Anschließend können Sie das Modell zum Bearbeiten öffnen.

   * Sie können das Modell anschließend auch wieder **Sperren**.
   * Wenn Sie das Modell erneut veröffentlichen, wird es sofort wieder in den Modus **Gesperrt** (SCHREIBGESCHÜTZT) versetzt.

* Modell-Editor

   * Wenn Sie ein gesperrtes Modell öffnen, werden Sie gewarnt und es werden Ihnen drei Aktionen angezeigt: **Abbrechen**, **Schreibgeschützt anzeigen**, **Bearbeiten**:

     ![Meldung beim Anzeigen eines gesperrten Inhaltsfragmentmodells](assets/cfm-model-editor-lock-message.png)

   * Wenn Sie **Schreibgeschützt anzeigen** auswählen, können Sie den Inhalt und die Struktur des Modells sehen:

     ![Schreibgeschützt anzeigen – gesperrtes Inhaltsfragmentmodell](assets/cfm-model-editor-locked-view-only.png)

   * Wenn Sie **Bearbeiten** auswählen, können Sie Ihre Änderungen bearbeiten und speichern:

     ![Bearbeiten – gesperrtes Inhaltsfragmentmodell](assets/cfm-model-editor-locked-edit.png)

     >[!NOTE]
     >
     >Oben kann noch eine Warnung angezeigt werden. In diesem Fall wird das Modell jedoch bereits von vorhandenen Inhaltsfragmenten verwendet.

   * Über **Abbrechen** kehren Sie zur Konsole zurück.
