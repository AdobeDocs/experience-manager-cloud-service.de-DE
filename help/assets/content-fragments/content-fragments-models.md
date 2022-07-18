---
title: Inhaltsfragmentmodelle
description: Erfahren Sie, wie Inhaltsfragmentmodelle in AEM als Grundlage für Ihren Headless-Content dienen und wie Sie Inhaltsfragmente mit strukturierten Inhalten erstellen.
feature: Content Fragments
role: User
exl-id: fd706c74-4cc1-426d-ab56-d1d1b521154b
source-git-commit: a5a5ec2211fe51bb04a1016f34fdac2f25cfe4e1
workflow-type: tm+mt
source-wordcount: '2890'
ht-degree: 94%

---

# Inhaltsfragmentmodelle {#content-fragment-models}

Inhaltsfragmentmodelle in AEM definieren die Inhaltsstruktur für Ihre [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md), die als Grundlage für Ihren Headless-Content dienen.

So verwenden Sie Inhaltsfragmentmodelle:

1. [Aktivieren Sie die Funktion für Inhaltsfragmentmodelle für Ihre Instanz.](/help/assets/content-fragments/content-fragments-configuration-browser.md)
1. [Erstellen](#creating-a-content-fragment-model) und [konfigurieren](#defining-your-content-fragment-model) Sie Ihre Inhaltsfragmentmodelle.
1. [Aktivieren Sie Ihre Inhaltsfragmentmodelle](#enabling-disabling-a-content-fragment-model) zur Verwendung bei der Erstellung von Inhaltsfragmenten.
1. [Lassen Sie Ihre Inhaltsfragmentmodelle in den erforderlichen Asset-Ordnern zu](#allowing-content-fragment-models-assets-folder), indem Sie **Richtlinien** konfigurieren.

## Erstellen eines Inhaltsfragmentmodells {#creating-a-content-fragment-model}

1. Navigieren Sie zu **Instrumente**, **Allgemein**, dann öffnen **Inhaltsfragmentmodelle**.
1. Navigieren Sie zu dem Ordner, der Ihrer [Konfiguration oder Unterkonfiguration](/help/assets/content-fragments/content-fragments-configuration-browser.md).
1. Öffnen Sie den Assistenten über **Erstellen**.

   >[!CAUTION]
   >
   >Wenn die [Verwendung von Inhaltsfragmentmodellen nicht aktiviert wurde](/help/assets/content-fragments/content-fragments-configuration-browser.md), ist die Option **Erstellen** nicht verfügbar.

1. Geben Sie den **Modell-Titel** an. Sie können auch **Tags** und eine **Beschreibung** hinzufügen sowie **Modell aktivieren** auswählen, um das [Modell bei Bedarf zu aktivieren](#enabling-disabling-a-content-fragment-model).

   ![Titel und Beschreibung](assets/cfm-models-02.png)

1. Speichern Sie das leere Modell über **Erstellen**. Eine Benachrichtigung zeigt an, dass der Vorgang erfolgreich abgeschlossen wurde. Daraufhin können Sie das Modell über die Option **Öffnen** direkt bearbeiten oder über **Fertig** zur Konsole zurückkehren.

## Definieren des Inhaltsfragmentmodells {#defining-your-content-fragment-model}

Das Inhaltsfragmentmodell definiert effektiv die Struktur der resultierenden Inhaltsfragmente unter Verwendung unterschiedlicher **[Datentypen](#data-types)**. Mithilfe des Modell-Editors können Sie Instanzen der Datentypen hinzufügen und diese dann so konfigurieren, dass die erforderlichen Felder erstellt werden:

>[!CAUTION]
>
>Die Bearbeitung eines vorhandenen Inhaltsfragmentmodells kann sich auf abhängige Fragmente auswirken.

1. Navigieren Sie zu **Instrumente**, **Allgemein**, dann öffnen **Inhaltsfragmentmodelle**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Öffnen Sie das zu **bearbeitende** Modell; nutzen Sie dazu entweder die entsprechende Schnellaktion oder wählen Sie das Modell und anschließend die Aktion aus der Symbolleiste aus.

   Wenn das Modell geöffnet ist, finden Sie Folgendes im Editor:

   * Links: bereits definierte Felder
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
         >Beim manuellen Aktualisieren der Eigenschaft **Eigenschaftsname** Beachten Sie bei Datentypen, dass Namen nur A-Z, a-z, 0-9 und Unterstriche &quot;_&quot;als Sonderzeichen enthalten dürfen.
         >
         >Wenn in früheren Versionen von AEM erstellte Modelle unzulässige Zeichen enthalten, entfernen oder ändern Sie diese Zeichen.
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
   * Wenn ein Bild referenziert wird, kann wahlweise eine Miniatur angezeigt werden.
* **Fragmentreferenz**
   * Verweist auf andere Inhaltsfragmente. Kann zum [Erstellen verschachtelter Inhalte](#using-references-to-form-nested-content) verwendet werden.
   * Der Datentyp kann so konfiguriert werden, dass Fragmentautoren folgende Möglichkeiten haben:
      * Direktes Bearbeiten des referenzierten Fragments
      * Erstellen eines neuen Inhaltsfragments basierend auf dem entsprechenden Modell
* **JSON-Objekt**
   * Ermöglicht es dem Autor des Inhaltsfragments, JSON-Syntax in die entsprechenden Elemente eines Fragments einzugeben.
      * Damit AEM direktes JSON speichern kann, das Sie von einem anderen Service kopiert/eingefügt haben.
      * Das JSON wird weitergegeben und als JSON in GraphQL ausgegeben.
      * Umfasst JSON-Syntaxhervorhebung, automatische Vervollständigung und Fehlerhervorhebung im Inhaltsfragmente-Editor.
* **Registerkarten-Platzhalter**
   * Ermöglicht die Einführung von Registerkarten zur Bearbeitung des Inhalts von Inhaltsfragmenten.
Dies wird als Trennzeichen im Modell-Editor angezeigt, der Abschnitte der Liste der Inhaltsdatentypen trennt. Jede Instanz stellt den Beginn einer neuen Registerkarte dar.
Im Fragment-Editor wird jede Instanz als Registerkarte angezeigt.

      >[!NOTE]
      >
      >Dieser Datentyp dient ausschließlich zur Formatierung und wird vom GraphQL-Schema von AEM ignoriert.

## Eigenschaften {#properties}

Viele Eigenschaften sind selbsterklärend. Im Folgenden finden Sie weitere Informationen zu bestimmten Eigenschaften:

* **Eigenschaftsname**

   Beachten Sie beim manuellen Aktualisieren dieser Eigenschaft für einen Datentyp Folgendes: **must** contain *only* A-Z, a-z, 0-9 und Unterstrich &quot;_&quot;als Sonderzeichen.

   >[!CAUTION]
   >
   >Wenn in früheren Versionen von AEM erstellte Modelle unzulässige Zeichen enthalten, entfernen oder ändern Sie diese Zeichen.

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

* Weitere Informationen zu diesem bestimmten Datentyp und seinen Eigenschaften finden Sie unter **[Inhaltsreferenz](#content-reference)**.

* Weitere Informationen zu diesem bestimmten Datentyp und seinen Eigenschaften finden Sie unter **[Fragmentreferenz (verschachtelte Fragmente)](#fragment-reference-nested-fragments)**.

* **Übersetzbar**

   Überprüfen der **Übersetzbar** in einem Feld im Editor für Inhaltsfragmentmodelle Folgendes aktivieren:

   * Stellen Sie sicher, dass der Eigenschaftsname des Felds zur Übersetzungskonfiguration, zum Kontext hinzugefügt wird. `/content/dam/<sites-configuration>`, falls nicht bereits vorhanden.
   * Für GraphQL: Legen Sie im Inhaltsfragmentfeld die Eigenschaft `<translatable>` auf `yes` fest, um den GraphQL-Abfragefilter für die JSON-Ausgabe nur mit übersetzbarem Content zuzulassen.

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
   >  Dadurch wird verhindert, dass der Benutzer dem aktuellen Fragment einen Verweis hinzufügt. Dies kann zu einem leeren Dialogfeld für die Auswahl von Fragmentreferenzen führen.
>
>* Fragmentverweise in GraphQL
   >  Wenn Sie eine Deep-Abfrage erstellen, die mehrere Inhaltsfragmente zurückgibt, die von einander referenziert werden, wird beim ersten Auftreten null zurückgegeben.


### Inhaltsreferenz {#content-reference}

Mit der Inhaltsreferenz können Sie Content aus einer anderen Quelle rendern, zum Beispiel ein Bild oder Inhaltsfragment.

Zusätzlich zu den Standardeigenschaften können Sie Folgendes angeben:

* Den **Stammpfad** für referenzierte Inhalte
* Die Inhaltstypen, auf die verwiesen werden kann
* Einschränkungen bezüglich der Dateigrößen
* Wenn ein Bild referenziert wird:
   * Miniatur anzeigen
   * Bildeinschränkungen hinsichtlich Höhe und Breite

![Inhaltsreferenz](assets/cfm-content-reference.png)

### Fragmentreferenz (verschachtelte Fragmente) {#fragment-reference-nested-fragments}

Die Fragmentreferenz verweist auf mindestens ein Inhaltsfragment. Diese Funktion ist besonders beim Abrufen von Content für die Verwendung in Ihrem Programm interessant, da sie es Ihnen ermöglicht, strukturierte Daten mit mehreren Ebenen abzurufen.

Beispiel:

* Ein Modell, das Details für einen Mitarbeiter definiert, beispielsweise:
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

   Auf diese Weise kann der Fragmentautor ein neues Fragment erstellen, das auf dem entsprechenden Modell basiert.

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

Zur Implementierung der Inhaltsverwaltung können Sie **Richtlinien** im Asset-Ordner konfigurieren, um zu steuern, welche Inhaltsfragmentmodelle für die Fragmenterstellung in diesem Ordner zulässig sind.

>[!NOTE]
>
>Der Mechanismus ähnelt dem [Zulassen von Seitenvorlagen](/help/sites-cloud/authoring/features/templates.md#allowing-a-template-author) für eine Seite und deren untergeordnete Elemente in den erweiterten Eigenschaften einer Seite.

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
>Das Löschen eines Inhaltsfragmentmodells wirkt sich unter Umständen auf abhängige Fragmente aus.

So löschen Sie ein Inhaltsfragmentmodell:

1. Navigieren Sie zu **Instrumente**, **Allgemein**, dann öffnen **Inhaltsfragmentmodelle**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Wählen Sie Ihr Modell und anschließend die Option **Löschen** aus der Symbolleiste aus.

   >[!NOTE]
   >
   >Wenn es Verweise auf das Modell gibt, wird Ihnen ein Warnhinweis angezeigt. Ergreifen Sie die entsprechenden Maßnahmen.

## Veröffentlichen eines Inhaltsfragmentmodells {#publishing-a-content-fragment-model}

Inhaltsfragmentmodelle müssen zeitgleich mit oder im Vorfeld der Veröffentlichung abhängiger Inhaltsfragmente veröffentlicht werden.

So veröffentlichen Sie ein Inhaltsfragmentmodell:

1. Navigieren Sie zu **Instrumente**, **Allgemein**, dann öffnen **Inhaltsfragmentmodelle**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Wählen Sie Ihr Modell und anschließen die Option **Veröffentlichen** aus der Symbolleiste aus.
Der Status „Veröffentlicht“ wird in der Konsole angezeigt.

   >[!NOTE]
   >
   >Wenn Sie Inhaltsfragmente veröffentlichen, deren Modell noch nicht veröffentlicht wurde, wird dies in der Auswahlliste angezeigt und das Modell wird mit dem Fragment veröffentlicht.

## Rückgängigmachen der Veröffentlichung eines Inhaltsfragmentmodells {#unpublishing-a-content-fragment-model}

Die Veröffentlichung von Inhaltsfragmentmodellen kann rückgängig gemacht werden, wenn sie nicht von Fragmenten referenziert werden.

So machen Sie die Veröffentlichung eines Inhaltsfragmentmodells rückgängig:

1. Navigieren Sie zu **Instrumente**, **Allgemein**, dann öffnen **Inhaltsfragmentmodelle**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Wählen Sie Ihr Modell und anschließen die Option **Veröffentlichung aufheben** aus der Symbolleiste aus.
Der Status „Veröffentlicht“ wird in der Konsole angezeigt.

Wenn Sie versuchen, die Veröffentlichung eines Modells aufzuheben, das aktuell von einem oder mehreren Fragmenten verwendet wird, werden Sie über eine Fehlermeldung über Folgendes informiert:

![Fehlermeldung zum Inhaltsfragmentmodell beim Rückgängigmachen der Veröffentlichung eines verwendeten Modells](assets/cfm-model-unpublish-error.png)

In der Meldung wird vorgeschlagen, dass Sie das Bedienfeld [Verweise](/help/sites-cloud/authoring/getting-started/basic-handling.md#references) überprüfen, um weitere Nachforschungen anzustellen:

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

* Anwender wurden auf die Risiken aufmerksam gemacht, die bei der Bearbeitung von Modellen auftreten, die bereits für die Bereitstellung von Live-Inhalten verwendet werden (d. h. von Modellen, die veröffentlicht wurden).

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

      Wenn Sie **Entsperren** wählen, wird eine Warnung angezeigt, und Sie müssen die Aktion **Entsperren** bestätigen:
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
