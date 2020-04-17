---
title: Inhaltsfragmentmodelle
description: Inhaltsfragmentmodelle werden verwendet, um Inhaltsfragmente mit strukturierten Inhalten zu erstellen.
translation-type: ht
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6

---


# Inhaltsfragmentmodelle{#content-fragment-models}

Inhaltsfragmentmodelle definieren die Struktur des Inhalts für Ihre [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md).

## Aktivieren von Inhaltsfragmentmodellen   {#enable-content-fragment-models}

>[!CAUTION]
>
>Wenn Sie **Inhaltsfragmentmodelle** nicht aktivieren, haben Sie keinen Zugriff auf die Option **Erstellen** für das Erstellen neuer Modelle.

Gehen Sie wie folgt vor, um Inhaltsfragmentmodelle zu aktivieren:

* Aktivieren Sie die Verwendung von Inhaltsfragmentmodellen im Konfigurations-Manager
* Wenden Sie die Konfiguration auf Ihren Assets-Ordner an

### Aktivieren Sie Inhaltsfragmentmodelle in Configuration Manager   {#enable-content-fragment-models-in-configuration-manager}

Um [ein neues Inhaltsfragmentmodell zu erstellen](#creating-a-content-fragment-model), **müssen** Sie Inhaltsfragmentmodelle zunächst über Configuration Manager aktivieren:

1. Navigieren Sie zu **Tools** > **Allgemein** und öffnen Sie dann den **Konfigurations-Browser**.
2. Wählen Sie den entsprechenden Speicherort für Ihre Web-Seite aus.
3. Öffnen Sie über **Erstellen** das Dialogfeld, in dem Sie:

   1. einen **Titel** angeben,
   2. **Inhaltsfragmentmodelle** auswählen, um deren Verwendung zu aktivieren.
   ![Konfiguration](assets/cfm-models-01.png)

4. Wählen Sie **Erstellen** aus, um die Definition zu speichern.

### Wenden Sie die Konfiguration auf Ihren Assets-Ordner an {#apply-the-configuration-to-your-assets-folder}

Wenn die Konfiguration **Global** für Inhaltsfragmentmodelle aktiviert wurde, können alle von Benutzern erstellten Modelle in jedem beliebigen Assets-Ordner verwendet werden.

Um eine andere Konfiguration (d. h. nicht „Global“) mit einem vergleichbaren Assets-Ordner zu verwenden, müssen Sie die Verbindung definieren. Wählen Sie dazu die entsprechende **Konfiguration** in der Registerkarte **Cloud Services** der **Ordnereigenschaften** des entsprechenden Ordners aus.

## Erstellen eines Inhaltsfragmentmodells {#creating-a-content-fragment-model}

1. Navigieren Sie zu **Tools** > **Assets** und öffnen Sie dann **Inhaltsfragmentmodelle**.
1. Navigieren Sie zu dem entsprechenden Ordner für Ihre [Konfiguration](#enable-content-fragment-models).
1. Öffnen Sie den Assistenten über **Erstellen**.

   >[!CAUTION]
   >
   >Wenn die [Verwendung von Inhaltsfragmentmodellen nicht aktiviert wurde](#enable-content-fragment-models), ist die Option **Erstellen** nicht verfügbar.

1. Legen Sie den **Modell-Titel** fest. Bei Bedarf können Sie auch **eine Beschreibung** hinzufügen.

   ![Titel und Beschreibung](assets/cfm-models-02.png)

1. Speichern Sie das leere Modell über **Erstellen**. Eine Benachrichtigung zeigt an, dass der Vorgang erfolgreich abgeschlossen wurde. Daraufhin können Sie das Modell über die Option **Öffnen** direkt bearbeiten oder über **Fertig** zur Konsole zurückkehren.

## Definieren des Inhaltsfragmentmodells   {#defining-your-content-fragment-model}

Das Inhaltsfragmentmodell definiert effektiv die Struktur des daraus entstehenden Inhaltsmodells. Mit dem Modell-Editor können Sie die erforderlichen Felder hinzufügen und konfigurieren:

>[!CAUTION]
>
>Die Bearbeitung eines vorhandenen Inhaltsfragmentmodells kann sich auf abhängige Fragmente auswirken.

1. Navigieren Sie zu **Tools** > **Assets** und öffnen Sie dann **Inhaltsfragmentmodelle**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Öffnen Sie das zu **bearbeitende** Modell; nutzen Sie dazu entweder die entsprechende Schnellaktion oder wählen Sie das Modell und anschließend die Aktion aus der Anwendungssymbolleiste aus.

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

   * Wenn ein Feld zum Modell hinzugefügt wurde, werden im rechten Fenster die **Eigenschaften** angezeigt, die für diesen speziellen Datentyp definiert werden können. Hier können Sie festlegen, was für dieses Feld erforderlich ist. Beispiel:
   ![Feldeigenschaften](assets/cfm-models-05.png)

   >[!NOTE]
   Beim Datentyp **Mehrzeilentext** können Sie den **Standardtyp** folgendermaßen definieren:
   * **Rich-Text**
   * **Markdown**
   * **Nur Text**
   Wenn Sie keinen Typ angeben, wird der Standardwert **Rich-Text** in diesem Feld verwendet.
   Änderungen am **Standardtyp** in einem Fragmentmodell werden erst dann auf vorhandene, zugehörige Inhaltsfragmente angewendet, wenn das Fragment im Editor geöffnet und gespeichert wurde.

1. **So entfernen Sie ein Feld**

   Wählen Sie das entsprechende Feld aus und klicken/tippen Sie auf das Papierkorb-Symbol. Sie werden aufgefordert, den Vorgang zu bestätigen.

   ![Entfernen](assets/cfm-models-06.png)

1. Wenn Sie alle erforderlichen Felder festgelegt und deren Eigenschaften definiert haben, speichern Sie die Definition über **Speichern**. Beispiel:

   ![Speichern](assets/cfm-models-07.png)

## Löschen eines Inhaltsfragmentmodells {#deleting-a-content-fragment-model}

>[!CAUTION]
Das Löschen eines Inhaltsfragmentmodells wirkt sich unter Umständen auf abhängige Fragmente aus.

So löschen Sie ein Inhaltsfragmentmodell:

1. Navigieren Sie zu **Tools** > **Assets** und öffnen Sie dann **Inhaltsfragmentmodelle**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Wählen Sie Ihr Modell und anschließend die Option **Löschen** aus der Anwendungssymbolleiste aus.

   >[!NOTE]
   Wenn es Verweise auf das Modell gibt, wird Ihnen ein Warnhinweis angezeigt. Ergreifen Sie die entsprechenden Maßnahmen.

## Veröffentlichen eines Inhaltsfragmentmodells   {#publishing-a-content-fragment-model}

Inhaltsfragmentmodelle müssen zeitgleich mit oder im Vorfeld der Veröffentlichung abhängiger Inhaltsfragmente veröffentlicht werden.

So veröffentlichen Sie ein Inhaltsfragmentmodell:

1. Navigieren Sie zu **Tools** > **Assets** und öffnen Sie dann **Inhaltsfragmentmodelle**.

1. Navigieren Sie zu dem Ordner, der Ihr Inhaltsfragmentmodell enthält.
1. Wählen Sie Ihr Modell und anschließen die Option **Löschen** aus der Anwendungssymbolleiste aus.

   >[!NOTE]
   Wenn Sie Inhaltsfragmente veröffentlichen, deren Modell noch nicht veröffentlicht wurde, wird dies in der Auswahlliste angezeigt und das Modell wird mit dem Fragment veröffentlicht.
