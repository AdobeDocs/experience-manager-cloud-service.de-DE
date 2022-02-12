---
title: Erstellen eines Asset-Ordners - Headless-Einrichtung
description: Verwenden Sie AEM-Inhaltsfragmentmodelle, um die Struktur von Inhaltsfragmenten zu definieren – die Grundlage für Ihren Headless-Content.
exl-id: 9a156a17-8403-40fc-9bd0-dd82fb7b2235
source-git-commit: 65c20293f2b5481d9c7fdd050af4bee5f64a33e6
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 90%

---

# Erstellen eines Asset-Ordners - Headless-Einrichtung {#creating-an-assets-folder}

Verwenden Sie AEM-Inhaltsfragmentmodelle, um die Struktur von Inhaltsfragmenten zu definieren – die Grundlage für Ihren Headless-Content. Inhaltsfragmente werden dann in Asset-Ordnern gespeichert.

## Was ist ein Asset-Ordner?  {#what-is-an-assets-folder}

[Nachdem Sie nun Inhaltsfragmentmodelle erstellt haben](create-content-model.md), die die Struktur definieren, die Sie für Ihre künftigen Inhaltsfragmente verwenden möchten, würden Sie sicher gern einige Fragmente erstellen.

Zunächst müssen Sie jedoch einen Ordner für Assets erstellen, in dem Sie diese speichern.

Asset-Ordner werden verwendet, um [herkömmliche Inhalts-Assets](/help/assets/manage-digital-assets.md) wie Bilder und Videos sowie Inhaltsfragmente zu organisieren.

## Erstellen eines Asset-Ordners {#how-to-create-an-assets-folder}

Administratoren müssen nur gelegentlich Ordner erstellen, um Inhalte bei der Erstellung zu organisieren. Für die Zwecke dieser Anleitung für den Einstieg müssen wir nur einen Ordner erstellen.

1. Melden Sie sich bei AEM as a Cloud Service an und wählen Sie im Hauptmenü **Tools > Assets > Dateien** aus.
1. Tippen oder klicken Sie auf **Erstellen > Ordner**.
1. Geben Sie einen **Titel** und einen **Namen** für Ihren Ordner an.
   * Der **Titel** sollte beschreibend sein.
   * Der **Name** wird zum Knotennamen im Repository.
      * Er wird automatisch auf der Grundlage des Titels generiert und gemäß den [AEM-Benennungskonventionen](/help/implementing/developing/introduction/naming-conventions.md) angepasst.
      * Er kann bei Bedarf angepasst werden.

   ![Ordner erstellen](../assets/assets-folder-create.png)
1. Wählen Sie den soeben erstellten Ordner aus, indem Sie den Mauszeiger darauf bewegen und auf das Häkchen tippen. Wählen Sie anschließend **Eigenschaften** über die Symbolleiste (oder verwenden Sie die `p` [Tastaturbefehl verwenden.](/help/sites-cloud/authoring/getting-started/keyboard-shortcuts.md))
1. Wählen Sie im Fenster **Eigenschaften** die Registerkarte **Cloud Services** aus.
1. Wählen Sie für die **Cloud-Konfiguration** die zuvor erstellte [Konfiguration aus.](create-configuration.md)

   ![Konfigurieren des Asset-Ordners](../assets/assets-folder-configure.png)
1. Tippen oder klicken Sie auf **Speichern und schließen**.
1. Tippen oder klicken Sie im Bestätigungsfenster auf **OK**.

   ![Bestätigungsfenster](../assets/assets-folder-confirmation.png)

Sie können im soeben erstellten Ordner weitere Unterordner erstellen. Die Unterordner übernehmen die **Cloud-Konfiguration** des übergeordneten Ordners. Dies kann jedoch überschrieben werden, wenn Sie Modelle aus einer anderen Konfiguration verwenden möchten.

Wenn Sie eine lokalisierte Site-Struktur verwenden, können Sie unter Ihrem neuen Ordner [einen Sprach-Stamm](/help/assets/translate-assets.md) erstellen.

## Nächste Schritte {#next-steps}

Nachdem Sie nun einen Ordner für Ihre Inhaltsfragmente erstellt haben, können Sie zum vierten Teil der Anleitung für den Einstieg übergehen und [Inhaltsfragmente erstellen](create-content-fragment.md).

>[!TIP]
>
>Ausführliche Informationen zur Verwaltung von Inhaltsfragmenten finden Sie in der [Dokumentation zu Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md).
