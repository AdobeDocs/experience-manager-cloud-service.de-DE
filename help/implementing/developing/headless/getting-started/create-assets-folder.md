---
title: Erstellen eines Asset-Ordners - Kurzanleitung ohne Kopfzeilen im Beginn
description: Inhaltsfragmentmodelle definieren die Struktur von Inhaltsfragmenten. Inhaltsfragmente werden dann in Asset-Ordnern gespeichert.
translation-type: tm+mt
source-git-commit: 9c801af38142434a5a0302b73b6fc1469a0eaab2
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 1%

---


# Erstellen eines Asset-Ordners ohne Kopfzeile - Schnellanleitung für Beginn{#creating-an-assets-folder}

Inhaltsfragmentmodelle definieren die Struktur von Inhaltsfragmenten. Inhaltsfragmente werden dann in Asset-Ordnern gespeichert.

##  Was ist ein Asset-Ordner? {#what-is-an-assets-folder}

[Nachdem Sie jetzt Inhaltsfragmentmodelle erstellt haben, ](create-content-model.md) die die Struktur definieren, die Sie für Ihre zukünftigen Inhaltsfragmente verwenden möchten, freuen Sie sich wahrscheinlich, einige Fragmente zu erstellen.

Zunächst müssen Sie jedoch einen Ordner für Assets erstellen, in dem Sie diese speichern.

Assets-Ordner werden verwendet, um herkömmliche Content-Assets wie Bilder und Videos sowie Inhaltsfragmente zu organisieren.[](/help/assets/manage-digital-assets.md)

## Erstellen eines Asset-Ordners {#how-to-create-an-assets-folder}

Ein Administrator muss nur gelegentlich Ordner erstellen, um Inhalte während der Erstellung zu organisieren. Für die Zwecke dieses Beginns-Handbuchs müssen wir nur einen Ordner erstellen.

1. Melden Sie sich bei AEM als Cloud Service an und wählen Sie im Hauptmenü **Navigation -> Assets -> Files** Files.
1. Tippen oder klicken Sie auf **Erstellen -> Ordner**.
1. Geben Sie einen **Titel** und einen **Namen** für Ihren Ordner an.
   * Der **Titel** sollte beschreibend sein.
   * Der Knoten **Name** wird zum Knotennamen im Repository.
      * Sie wird automatisch basierend auf dem Titel generiert und entsprechend den Benennungskonventionen [AEM angepasst.](/help/implementing/developing/introduction/naming-conventions.md)
      * Er kann bei Bedarf angepasst werden.

   ![Ordner erstellen](../assets/assets-folder-create.png)
1. Wählen Sie den soeben erstellten Ordner aus und wählen Sie dann **Eigenschaften** in der Symbolleiste aus (oder verwenden Sie den `p` [Tastaturbefehl.](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md))
1. Wählen Sie im Fenster **Eigenschaften** die Registerkarte **Cloud Services**.
1. Wählen Sie für die **Cloud-Konfiguration** die zuvor erstellte [Konfiguration aus.](create-configuration.md)

   ![Asset-Ordner konfigurieren](../assets/assets-folder-configure.png)
1. Tippen oder klicken Sie auf **Speichern und Schließen**.
1. Tippen oder klicken Sie im Bestätigungsfenster auf **OK**.

   ![Bestätigungsfenster](../assets/assets-folder-confirmation.png)

Sie können weitere Unterordner im soeben erstellten Ordner erstellen. Die Unterordner übernehmen die **Cloud-Konfiguration** des übergeordneten Ordners. Dies kann jedoch überschrieben werden, wenn Sie Modelle aus einer anderen Konfiguration verwenden möchten.

Wenn Sie eine lokalisierte Sitestruktur verwenden, können Sie unter Ihrem neuen Ordner [einen Sprachstamm](/help/assets/translate-assets.md) erstellen.

## Nächste Schritte {#next-steps}

Nachdem Sie jetzt einen Ordner für Ihre Inhaltsfragmente erstellt haben, können Sie zum vierten Teil des Beginns-Handbuchs wechseln und [Inhaltsfragmente erstellen.](create-content-fragment.md)

>!![TIP]
Ausführliche Informationen zum Verwalten von Inhaltsfragmenten finden Sie in der [Dokumentation zu Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md)
