---
title: Erstellen und Verwalten von Angeboten (Angebotskonsole)
description: Mit der Angebotskonsole lassen sich Angebote erstellen, die für Erlebnisse in Aktivitäten eingesetzt werden können.
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: 81d2fda2-06a9-48f6-820a-dd9e11d94fcc
solution: Experience Manager Sites
feature: Authoring, Personalization
role: User
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '1357'
ht-degree: 99%

---

# Erstellen und Verwalten von Angeboten (Angebotskonsole) {#creating-and-managing-offers}

Die **Angebotskonsole** wird in Zukunft nicht mehr unterstützt. Von nun an ist es also:

* Nur für Kundinnen und Kunden verfügbar, die bereits definierte *veraltete* (d. h. bereits existierende) Angebote haben.
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
>Dies ist der empfohlene Workflow zum Konvertieren veralteter Angebote in Experience Fragments.

>[!NOTE]
>
>Sie können auch selbst ein Experience Fragment erstellen, den Inhalt aus Ihrem alten Angebot manuell an das Fragment übertragen und dann das alte Angebot löschen.

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

Für Kundinnen und Kunden mit bereits vorhandenen älteren Angeboten sind die Optionen **Angebotsvorlage verwenden** beim Targeting von Komponenten, die **nicht** Experience Fragments sind, sichtbar:

![Dialogfeld „In Experience Fragment-Variante konvertieren“](/help/sites-cloud/authoring/assets/offers-legacy-target-non-experience-fragment.png)

## Die Angebotskonsole {#offers-console}

>[!CAUTION]
>
>Diese Konsole wird in Zukunft nicht mehr unterstützt, da sie eine veraltete Möglichkeit zur Personalisierung von Inhalten bietet.
>
>Sie haben etwas Zeit zur Vorbereitung. Erfahren Sie, wie Sie [vorhandene ältere Angebote in Experience Fragments-Angebote konvertieren können](#convert-legacy-offer-to-experience-fragment).

Mit der Angebotskonsole lassen sich Angebote erstellen, die für [Erlebnisse in Aktivitäten eingesetzt werden können](/help/sites-cloud/authoring/personalization/targeted-content.md). Durch das Erstellen von Angeboten mithilfe der Konsole sparen Sie Zeit, wenn ein Angebot für mehrere Erlebnisse benötigt wird:

* Erstellen Sie das Angebot zunächst in der Bibliothek und verwenden Sie es für verschiedene Erlebnisse Ihrer Markenaktivitäten.
* Ändern Sie das Angebot in der Bibliothek. Die Änderung wirkt sich dann auf alle Erlebnisse aus, die dieses Angebot verwenden.

In der Angebotskonsole werden Angebote nach Marken sortiert. Jede Marke verfügt über eine Angebotsbibliothek, die für die Erlebnisse dieser Marke verwendet werden kann. Verwenden Sie Ordner, um eine Hierarchie der Angebote einer Bibliothek festzulegen. Mithilfe logischer Ordnerstrukturen können Autorinnen und Autoren Angebote beim Durchsuchen leichter auffinden. Tagging- und Such-Tools vereinfachen die Suche für Autorinnen und Autoren zusätzlich.

### Hinzufügen von Marken mithilfe der Angebotskonsole {#add-a-brand-using-the-offers-console}

Erstellen Sie eine Marke, mit der Angebote verknüpft werden sollen. Öffnen Sie eine Marke in der Angebotskonsole, um auf deren Angebotsbibliothek zuzugreifen, in der Sie Ordner und Angebote erstellen können.

Wenn Sie eine Marke mithilfe der Angebotskonsole erstellen, wird diese Marke auch in der [Aktivitätskonsole](/help/sites-cloud/authoring/personalization/activities.md) angezeigt, in der Sie Aktivitäten für die Marke hinzufügen und verwalten können.

1. Wählen Sie in der Navigationskonsole **Personalisierung** > **Angebote** aus.

   ![Navigieren zur Angebotskonsole](/help/sites-cloud/authoring/assets/offers-navigation.png)

1. Wählen Sie **Erstellen** und dann **Marke** **erstellen** aus.
1. Wählen Sie die Markenvorlage und dann **Weiter** aus.
1. Geben Sie den Namen der Marke an, der in Angebots- und Aktivitätskonsole angezeigt werden soll. Optional können Sie eins oder mehrere Tags eingeben oder auswählen, die mit der Marke verknüpft werden sollen.
1. Wählen Sie **Erstellen** aus.

### Hinzufügen von Ordnern zu Angebotsbibliotheken {#add-a-folder-to-an-offer-library}

Fügen Sie der Angebotsbibliothek einer Marke einen Ordner hinzu, um Angebote zu ordnen und zu speichern. Sie können einen Ordner unterhalb der Marke oder unter anderen Ordnern erstellen.

1. Navigieren Sie in der Angebotskonsole zu dem Speicherort, an dem der Ordner erstellt werden soll. Öffnen Sie beispielsweise die Marke, um einen Ordner auf der obersten Ebene zu erstellen, oder öffnen Sie einen anderen Ordner in der Bibliothek.
1. Wählen Sie **Erstellen** > **Ordner oder Angebot erstellen** aus.

   ![Erstellen eines Angebotsordners](/help/sites-cloud/authoring/assets/offers-create-folder.png)

1. Wählen Sie **Ordner** aus und klicken Sie auf **Weiter**.
1. Geben Sie den Ordnernamen ein, der in der Angebotsbibliothek angezeigt werden soll, und geben Sie Tags ein oder wählen Sie diese aus.

   ![Definieren von Ordnereigenschaften](/help/sites-cloud/authoring/assets/offers-folder-properties.png)

1. Wählen Sie **Erstellen** aus.

### Hinzufügen von Angeboten zu Angebotsbibliotheken {#add-an-offer-to-an-offer-library}

Fügen Sie ein Angebot in der Angebotsbibliothek einer Marke hinzu, sodass es zu den Erlebnissen der Marke hinzugefügt werden kann. Wenn Sie ein Angebot hinzufügen, müssen Sie einen Titel eingeben. Sie können das Angebot auch mit einem oder mehreren Tags verknüpfen, damit einfacher danach gesucht werden kann.

Nach Erstellung des Angebots können Sie es öffnen, um Inhalte zu verfassen.

1. Navigieren Sie in der Angebotskonsole zu dem Speicherort, an dem das Angebot erstellt werden soll. Öffnen Sie beispielsweise eine Marke, um ein übergeordnetes Angebot zu erstellen, oder öffnen Sie einen Ordner der Bibliothek.
1. Wählen Sie **Erstellen** > **Ordner oder Angebot erstellen** aus.

   ![Erstellen eines Angebotsordners](/help/sites-cloud/authoring/assets/offers-create-folder.png)

1. Wählen Sie die Vorlage der **Angebotsseite** und anschließend **Weiter** aus.
1. Geben Sie einen Titel für das Angebot ein. Sie können dann optional ein oder mehrere Tags auswählen oder eingeben, die mit dem Angebot verknüpft werden sollen. Wählen Sie anschließend **Erstellen** aus.
1. Wählen Sie im Dialogfeld die Option **Seite öffnen** aus, um das Angebot für die Bearbeitung zu öffnen.

### Bearbeiten von Angeboten {#editing-an-offer}

Öffnen Sie ein Angebot und bearbeiten Sie den Inhalt so, wie er in den Erlebnissen, die es verwenden, erscheinen soll. Wenn Sie ein Angebot bearbeiten, das in beliebigen Erlebnissen verwendet wird, werden Ihre Änderungen in den Erlebnissen angezeigt.

Sie können Angebote über den Ordner in der Angebotsbibliothek oder direkt über die Suchergebnisse öffnen. Außerdem können Sie ein Angebot über das Erlebnis öffnen, mit dem es verknüpft ist.

1. Wählen Sie in der Angebotskonsole das Symbol neben dem Angebot und anschließend **Bearbeiten** aus.
1. Fügen Sie dem Angebot Komponenten hinzu und bearbeiten Sie den Komponenteninhalt wie üblich.

### Löschen von Angeboten {#deleting-an-offer}

Wird ein Angebot nicht länger benötigt, können Sie es löschen. Sollten Sie versuchen, ein Angebot zu löschen, das von einem Erlebnis verwendet wird, werden Sie zur Bestätigung des Löschvorgangs aufgefordert. Wenn Sie bestätigen, dass das Angebot gelöscht werden soll, wird es aus den entsprechenden Erlebnissen entfernt.

Sie können Angebote löschen, wenn Sie entweder Ordnerinhalte der Angebotsbibliothek oder Suchergebnisse anzeigen.

1. Wählen Sie in der Angebotskonsole das Symbol neben dem Angebot und anschließend **Löschen** aus.

   Wählen Sie das Angebot und anschließend **Löschen** aus.

1. Wählen Sie im daraufhin eingeblendeten Dialogfeld die Option **Löschen** aus, um den Löschvorgang zu bestätigen.
1. Wird das Angebot von einem oder mehreren Erlebnissen verwendet, sehen Sie ein Dialogfeld, das auf die Referenzierung des Angebots hinweist:

   * Soll das Angebot gelöscht und aus den Erlebnissen entfernt werden, wählen Sie **Löschen erzwingen** aus.
   * Soll das Angebot nicht gelöscht werden, wählen Sie **Abbrechen** aus.

### Suchen nach Angeboten {#searching-for-offers}

Suchen Sie in den Angeboten Ihrer Marken mithilfe von Keywords nach passenden Titeln.

![Suchen nach Angeboten](/help/sites-cloud/authoring/assets/offers-search.png)

Die derzeit angewendeten Suchkriterien werden neben den Suchergebnissen eingeblendet. Sie können die Ergebnisse zudem nach Spalten in auf- oder absteigender Reihenfolge sortieren. Sie können beliebige Ordner einer Bibliothek durchsuchen. Die Suchergebnisse sind unabhängig vom ausgewählten Ordner immer die gleichen.

So durchsuchen Sie Angebote:

1. Wählen Sie oben in der Angebotskonsole das Lupensymbol aus. Die Suche wird standardmäßig auf Angebote beschränkt.
1. Geben Sie einen Suchbegriff ein, um nach Angeboten zu suchen. Wählen Sie aus den Ergebnissen das passende aus.
