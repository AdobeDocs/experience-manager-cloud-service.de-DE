---
title: Erstellen und Verwalten von Angeboten (Angebotskonsole)
description: Mit der Angebotskonsole lassen sich Angebote erstellen, die für Erlebnisse in Aktivitäten eingesetzt werden können.
exl-id: 81d2fda2-06a9-48f6-820a-dd9e11d94fcc
source-git-commit: 635f4c990c27a7646d97ebd08b453c71133f01b3
workflow-type: tm+mt
source-wordcount: '1392'
ht-degree: 55%

---

# Erstellen und Verwalten von Angeboten (Angebotskonsole) {#creating-and-managing-offers}

Die **Angebotskonsole** wird in Zukunft nicht mehr unterstützt. Von nun an ist es also:

* Nur für Kunden verfügbar, die bereits definierte *veraltete* (d. h. bereits existierende) Angebote haben
* Es wird empfohlen, solche veralteten Angebote in Experience Fragment-Angebote zu konvertieren
   * Sobald das letzte alte Angebot konvertiert/entfernt wurde, wird die **Angebotskonsole** nicht mehr verfügbar sein.

![Personalisierungskonsolen](/help/sites-cloud/authoring/assets/offers-consoles.png)

>[!NOTE]
>
>Kunden, die bereits vorhandene, veraltete Angebote haben, können weiterhin die **Angebotskonsole** nutzen, um sowohl vorhandene, veraltete Angebote zu sehen als auch neue zu erstellen.
>
>Kunden ohne bereits vorhandene veraltete Angebote bekommen die **Angebotskonsole** nicht zu sehen.
>
>Alle Kunden können **Experience Fragments-Angebote** verwenden, um Angebote zu erstellen und zu verwalten.

## Konvertieren eines veralteten Angebots in ein Experience Fragment {#convert-legacy-offer-to-experience-fragment}

Es wurde eine Option **In Experience Fragment-Variante konvertieren** sowie ein Workflow implementiert, um Sie bei der Konvertierung Ihres veralteten Angebots in ein Experience Fragment zu unterstützen:

>[!NOTE]
>
>Dies ist der empfohlene Arbeitsablauf zum Konvertieren veralteter Angebote in Experience Fragments.

>[!NOTE]
>
>Sie können auch selbst ein neues Experience Fragment erstellen, den Inhalt aus Ihrem alten Angebot manuell an das Fragment übertragen und dann das alte Angebot löschen.

>[!CAUTION]
>
>Die Option **In Experience Fragment-Variante konvertieren** ist für alle Kernkomponenten verfügbar.
>
>Diese Option wird für benutzerdefinierte Komponenten nicht unterstützt. Für solche Komponenten müssen Sie den Inhalt manuell in ein Experience Fragment konvertieren.

>[!CAUTION]
>
>Sobald das letzte alte Angebot konvertiert/entfernt wurde:
>
>* Die **Angebotskonsole** wird nicht mehr verfügbar sein.
>* Das Zielsymbol in der Symbolleiste aller anderen betroffenen Komponenten wird nicht mehr angezeigt.

1. Öffnen Sie eine Seite, die das Angebot zur Bearbeitung enthält.

1. Wechseln Sie zum **Targeting**-Modus für diese Seite.

1. Klicken Sie auf **Targeting starten**.

1. Wählen Sie die entsprechende (zielgerichtete) Komponente aus.

1. Die Komponentensymbolleiste bietet eine Option zum **Konvertieren in eine Experience Fragment-Variante**:

   ![Konvertieren eines veralteten Angebots in ein Experience Fragment](/help/sites-cloud/authoring/assets/offers-convert-legacy-icon.png)

1. Ein Dialogfeld wird angezeigt. Hier können Sie die erforderliche **Aktion** auswählen:

   * Erstellen eines neuen Experience Fragment
   * Den Inhalt zum einem bestehenden Experience Fragment hinzufügen

   Wählen Sie für dieses Szenario **Neues Experience Fragment erstellen**.

   ![Dialogfeld „In Experience Fragment-Variante konvertieren“](/help/sites-cloud/authoring/assets/offers-convert-dialog.png)

1. Füllen Sie die erforderlichen Felder im Dialogfeld aus:

   * **Übergeordneter Pfad**
Geben Sie den übergeordneten Pfad des neuen Experience Fragments an.
   * **Vorlage**
Wählen Sie die Vorlage aus, die zum Erstellen des Experience Fragments verwendet werden soll.
   * **Fragmenttitel**
Geben Sie den Titel an.
   * **Fragment-Tags**
Fügen Sie bei Bedarf Tags hinzu.

1. Bestätigen Sie mit **Fertig**.

   Wenn Sie jetzt zur Konsole der **Experience Fragment-Angebote** navigieren, sehen Sie Ihr neues Experience Fragment zusammen mit den zugehörigen Varianten.

### Targeting mit der Angebotsvorlage {#targeting-offers-template}

>[!CAUTION]
>
>Diese Option steht nur Kunden mit bereits vorhandenen Legacy-Angeboten zur Verfügung.
>
>Wie bei **Angeboten** wird die Konsole ebenfalls nicht mehr verfügbar sein:
>
>* nachdem das letzte alte Angebot in Experience Fragments konvertiert wurde
>* wenn Legacy-Angebote veraltet sind (in der Zukunft)
>
>Daher wird empfohlen, Experience Fragments und nicht diese Option zu verwenden.

Für Kunden mit bereits vorhandenen älteren Angeboten wird die Variable **Angebotsvorlage verwenden** Optionen sind beim Targeting von Komponenten sichtbar, die **not** Experience Fragments:

![Dialogfeld „In Experience Fragment-Variante konvertieren“](/help/sites-cloud/authoring/assets/offers-legacy-target-non-experience-fragment.png)

## Die Angebotskonsole {#offers-console}

>[!CAUTION]
>
>Diese Konsole wird in Zukunft nicht mehr unterstützt, da sie eine veraltete Möglichkeit zur Personalisierung von Inhalten bietet.
>
>Sie haben etwas Zeit zur Vorbereitung. Erfahren Sie, wie Sie [vorhandene ältere Angebote in Experience Fragments-Angebote konvertieren können](#convert-legacy-offer-to-experience-fragment).

Verwenden Sie die Angebotskonsole, um Angebote zu erstellen, die Sie [Verwendung in Aktivitätserlebnissen](/help/sites-cloud/authoring/personalization/targeted-content.md). Das Erstellen von Angeboten in der Angebotskonsole spart Zeit, wenn mehrere Erlebnisse dasselbe Angebot erfordern:

* Erstellen Sie das Angebot zunächst in der Bibliothek und verwenden Sie es für verschiedene Erlebnisse Ihrer Markenaktivitäten.
* Ändern Sie das Angebot in der Bibliothek, und die Änderung wirkt sich auf alle Erlebnisse aus, die es verwenden.

Die Angebotskonsole organisiert Angebote nach Marken. Jede Marke enthält eine Bibliothek von Angeboten, die in den Erlebnissen einer Marke verwendet werden können. Verwenden Sie Ordner, um eine Hierarchie der Angebote einer Bibliothek festzulegen. Eine logische Ordnerstruktur ermöglicht es Autoren, Angebote einfach zu finden, indem sie durchsuchen. Tagging- und Suchwerkzeuge ermöglichen es Autoren auch, Angebote zu finden.

### Hinzufügen von Marken mithilfe der Angebotskonsole {#add-a-brand-using-the-offers-console}

Erstellen Sie eine Marke, mit der Angebote verknüpft werden sollen. Öffnen Sie eine Marke in der Angebotskonsole, um auf deren Angebotsbibliothek zuzugreifen, in der Sie Ordner und Angebote erstellen können.

Wenn Sie eine Marke mithilfe der Angebotskonsole erstellen, wird sie auch in der [Aktivitätskonsole](/help/sites-cloud/authoring/personalization/activities.md) wo Sie Aktivitäten für die Marke hinzufügen und verwalten können.

1. Tippen/klicken Sie in der Navigationskonsole auf **Personalisierung** > **Angebote**.

   ![Navigieren zur Angebotskonsole](/help/sites-cloud/authoring/assets/offers-navigation.png)

1. Klicken oder tippen Sie auf **Erstellen** und anschließend auf **Marke** **erstellen**.
1. Wählen Sie die Markenvorlage aus und klicken oder tippen Sie auf **Weiter**.
1. Geben Sie einen Titel für die Marke ein, wie er in den Konsolen Angebote und Aktivitäten angezeigt werden soll. Optional können Sie eins oder mehrere Tags eingeben oder auswählen, die mit der Marke verknüpft werden sollen.
1. Klicken oder tippen Sie auf **Erstellen**.

### Hinzufügen von Ordnern zu Angebotsbibliotheken {#add-a-folder-to-an-offer-library}

Fügen Sie der Angebotsbibliothek einer Marke einen Ordner hinzu, um Angebote zu organisieren und zu speichern. Sie können einen Ordner unter der Marke oder unter anderen Ordnern erstellen.

1. Öffnen Sie in der Angebotskonsole den Speicherort, an dem Sie den Ordner erstellen möchten. Öffnen Sie beispielsweise die Marke, um einen Ordner der obersten Ebene zu erstellen, oder öffnen Sie einen anderen Ordner in der Bibliothek.
1. Klicken oder tippen Sie auf **Erstellen** > **Ordner oder Angebot erstellen**.

   ![Erstellen von Angebotsordnern](/help/sites-cloud/authoring/assets/offers-create-folder.png)

1. Wählen Sie **Ordner** aus und klicken Sie auf **Weiter**.
1. Geben Sie den Ordnernamen ein, der in der Angebotsbibliothek angezeigt werden soll, und geben Sie Tags ein oder wählen Sie diese aus.

   ![Definieren von Ordnereigenschaften](/help/sites-cloud/authoring/assets/offers-folder-properties.png)

1. Klicken oder tippen Sie auf **Erstellen**.

### Hinzufügen von Angeboten zu Angebotsbibliotheken {#add-an-offer-to-an-offer-library}

Fügen Sie der Angebotsbibliothek einer Marke ein Angebot hinzu, damit es den Erlebnissen der Marke hinzugefügt werden kann. Wenn Sie ein Angebot hinzufügen, geben Sie einen Titel ein. Sie können das Angebot auch mit einem oder mehreren Tags verknüpfen, um die Suchbarkeit zu verbessern.

Nachdem Sie das Angebot erstellt haben, können Sie es öffnen, um den Inhalt zu erstellen.

1. Öffnen Sie in der Angebotskonsole den Ort, an dem Sie das Angebot erstellen möchten. Öffnen Sie beispielsweise die Marke, um ein Angebot der obersten Ebene zu erstellen, oder öffnen Sie einen Ordner in der Bibliothek.
1. Klicken oder tippen Sie auf **Erstellen** > **Ordner oder Angebot erstellen**.

   ![Erstellen von Angebotsordnern](/help/sites-cloud/authoring/assets/offers-create-folder.png)

1. Wählen Sie die **Angebotsseite** und klicken oder tippen Sie auf **Nächste**.
1. Geben Sie einen Titel für das Angebot ein und wählen Sie optional ein oder mehrere Tags aus, die mit dem Angebot verknüpft werden sollen. Klicken oder tippen Sie dann auf **Erstellen**.
1. Klicken oder tippen Sie im Bestätigungsdialogfeld auf **Seite öffnen**, um das Angebot zur Bearbeitung zu öffnen.

### Bearbeiten von Angeboten {#editing-an-offer}

Öffnen Sie ein Angebot und bearbeiten Sie den Inhalt so, wie er in den Erlebnissen angezeigt werden soll, die es verwenden. Wenn Sie ein Angebot bearbeiten, das in Erlebnissen verwendet wird, erscheinen Ihre Änderungen in den Erlebnissen.

Sie können Angebote aus einem Ordner in einer Angebotsbibliothek oder aus Suchergebnissen öffnen. Sie können auch ein Angebot aus einem Erlebnis öffnen, das das Angebot verwendet.

1. Tippen oder klicken Sie in der Angebotskonsole auf das Symbol neben dem Angebot und klicken oder tippen Sie auf **Bearbeiten**.
1. Fügen Sie dem Angebot Komponenten hinzu und bearbeiten Sie den Komponenteninhalt wie gewohnt.

### Löschen von Angeboten {#deleting-an-offer}

Löschen Sie ein Angebot, das nicht mehr benötigt wird. Wenn Sie versuchen, ein Angebot zu löschen, das in einem Erlebnis verwendet wird, werden Sie aufgefordert, den Löschvorgang zu bestätigen. Durch die Bestätigung wird das Angebot gelöscht und aus den Erlebnissen entfernt.

Sie können Angebote löschen, indem Sie entweder Ordnerinhalte in einer Angebotsbibliothek anzeigen oder Suchergebnisse anzeigen.

1. Tippen oder klicken Sie in der Angebotskonsole auf das Symbol neben dem Angebot und klicken oder tippen Sie auf **Löschen**.

   Wählen Sie das Angebot aus und klicken oder tippen Sie auf **Löschen**.

1. Klicken oder tippen Sie im angezeigten Dialogfeld auf **Löschen** , um den Löschvorgang zu bestätigen.
1. Wenn das Angebot in einem oder mehreren Erlebnissen verwendet wird, erscheint ein Dialogfeld, das angibt, dass auf das Angebot verwiesen wird:

   * Um das Angebot zu löschen und aus den Erlebnissen zu entfernen, klicken oder tippen Sie auf **Löschen erzwingen**.
   * Um das Angebot beizubehalten, klicken oder tippen Sie auf **Abbrechen**.

### Suchen nach Angeboten {#searching-for-offers}

Suchen Sie in den Angeboten Ihrer Marken mithilfe von Keywords nach passenden Titeln.

![Suchen nach Angeboten](/help/sites-cloud/authoring/assets/offers-search.png)

Die aktuellen Suchkriterien werden neben den Suchergebnissen angezeigt. Sie können die Ergebnisse auch in auf- oder absteigender Reihenfolge nach Spalten sortieren. Sie können beliebige Ordner einer Bibliothek durchsuchen. Die Suchergebnisse sind unabhängig vom aktuellen Ordner identisch.

So suchen Sie Angebote:

1. Klicken oder tippen Sie oben in der Angebotskonsole auf das Lupensymbol. Die Suche wird standardmäßig auf Angebote beschränkt.
1. Geben Sie Ihren Suchbegriff ein, um nach Angeboten zu suchen. Wählen Sie aus den Ergebnissen aus.
