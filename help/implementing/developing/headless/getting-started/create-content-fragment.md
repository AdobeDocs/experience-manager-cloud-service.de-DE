---
title: Erstellen von Inhaltsfragmenten - Kurzanleitung ohne Kopfzeilen im Beginn
description: Inhaltsfragmente ermöglichen Ihnen das Entwerfen, Erstellen, Kuratieren und Verwenden seitenunabhängiger Inhalte, die AEM ohne Probleme bereitstellen können.
translation-type: tm+mt
source-git-commit: fa2fee3139acd60ea96222752785cf397978a2bc
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 2%

---


# Erstellen von Inhaltsfragmenten - Kurzanleitung zum Beginn ohne Kopfzeilen {#creating-content-fragments}

Inhaltsfragmente ermöglichen Ihnen das Entwerfen, Erstellen, Kuratieren und Verwenden seitenunabhängiger Inhalte, die AEM ohne Probleme bereitstellen können.

## Was sind Inhaltsfragmente? {#what-are-content-fragments}

[Nachdem Sie einen Asset-](create-assets-folder.md) Ordner erstellt haben, in dem Sie Ihre Inhaltsfragmente speichern können, können Sie die Fragmente jetzt erstellen!

Mit Inhaltsfragmenten können Sie seitenunabhängige Inhalte entwerfen, erstellen, kuratieren und veröffentlichen. Sie ermöglichen Ihnen die Vorbereitung von Inhalten, die an mehreren Orten und über mehrere Kanal hinweg verwendet werden können.

Inhaltsfragmente enthalten strukturierten Inhalt und können im JSON-Format bereitgestellt werden.

## Erstellen eines Inhaltsfragments {#how-to-create-a-content-fragment}

Inhaltsersteller erstellen eine beliebige Anzahl von Inhaltsfragmenten, um den von ihnen erstellten Inhalt darzustellen. Das wird ihre wichtigste Aufgabe in AEM sein. Für die Zwecke dieses Beginns-Leitfadens müssen wir nur einen erstellen.

1. Melden Sie sich bei AEM als Cloud Service an und wählen Sie im Hauptmenü **Navigation -> Assets**.
1. Tippen Sie auf den zuvor erstellten Ordner [oder klicken Sie auf diesen.](create-assets-folder.md)
1. Tippen oder klicken Sie auf **Erstellen -> Inhaltsfragment**.
1. Die Erstellung eines Inhaltsfragments wird in zwei Schritten als Assistent dargestellt. Wählen Sie zuerst das Modell aus, das Sie zum Erstellen des Inhaltsfragments verwenden möchten, und tippen oder klicken Sie auf **Weiter**.
   * Die verfügbaren Modelle hängen von der [**Cloud-Konfiguration** ab, die Sie für den Elementordner](create-assets-folder.md) definiert haben, in dem Sie das Inhaltsfragment erstellen.
   * Wenn Sie die Meldung `We could not find any models` erhalten, überprüfen Sie die Konfiguration Ihres Elementordners.

   ![Inhaltsfragmentmodell auswählen](../assets/content-fragment-model-select.png)
1. Geben Sie nach Bedarf **Title**, **Description** und **Tags** ein und tippen oder klicken Sie auf **Create**.

   ![Inhaltsfragment erstellen](../assets/content-fragment-create.png)
1. Tippen oder klicken Sie im Bestätigungsfenster auf **Öffnen**.

   ![Inhaltsfragment-erstellte Bestätigung](../assets/content-fragment-confirmation.png)
1. Geben Sie die Details des Inhaltsfragments im Inhaltsfragment-Editor an.

   ![Inhaltsfragmente-Editor](../assets/content-fragment-edit.png)
1. Tippen oder klicken Sie auf **Speichern und Schließen**.

Inhaltsfragmente können auf andere Inhaltsfragmente verweisen, was bei Bedarf eine verschachtelte Inhaltsstruktur ermöglicht.

Inhaltsfragmente können auch auf andere Assets in AEM verweisen. [Diese Assets müssen in ](/help/assets/manage-digital-assets.md) AEM gespeichert werden, bevor ein Verweis auf das Inhaltsfragment erstellt wird.

## Nächste Schritte {#next-steps}

Nachdem Sie jetzt ein Inhaltsfragment erstellt haben, können Sie zum letzten Teil des Handbuchs &quot;Erste Schritte&quot;wechseln und [API-Anforderungen erstellen, um auf Inhaltsfragmente zuzugreifen und diese bereitzustellen.](create-api-request.md)

>[!TIP]
>
>Ausführliche Informationen zum Verwalten von Inhaltsfragmenten finden Sie in der [Dokumentation zu Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md)
