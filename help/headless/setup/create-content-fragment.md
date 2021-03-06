---
title: Erstellen von Inhaltsfragmenten – Headless-Einrichtung
description: Erfahren Sie, wie Sie mit den Inhaltsfragmenten von AEM seitenunabhängige Inhalte für die Headless-Bereitstellung entwerfen, erstellen, kuratieren und verwenden können.
exl-id: a227ae2c-f710-4968-8a00-bfe48aa66145
source-git-commit: d6038920a5866c19a94980cc14fa46dec48daf51
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 78%

---

# Erstellen von Inhaltsfragmenten – Headless-Einrichtung {#creating-content-fragments}

Erfahren Sie, wie Sie mit den Inhaltsfragmenten von AEM seitenunabhängige Inhalte für die Headless-Bereitstellung entwerfen, erstellen, kuratieren und verwenden können.

## Was sind Inhaltsfragmente? {#what-are-content-fragments}

[Nachdem Sie einen Asset-Ordner erstellt haben](create-assets-folder.md), in dem Ihre Inhaltsfragmente gespeichert werden sollen, können Sie nun Fragmente erstellten.

Inhaltsfragmente ermöglichen Ihnen das Entwerfen, Erstellen, Kuratieren und Verwenden von seitenunabhängigen Inhalten. Außerdem können Sie Inhalte zur Verwendung an mehreren Orten und über mehrere Kanäle hinweg vorbereiten.

Inhaltsfragmente enthalten strukturierten Inhalt und können im JSON-Format bereitgestellt werden.

## Erstellen eines Inhaltsfragments {#how-to-create-a-content-fragment}

Inhaltsersteller können eine beliebige Anzahl von Inhaltsfragmenten für ihre Inhalte erstellen. Das die zentrale Aufgabe, die sie in AEM ausführen. Für die Zwecke dieser Anleitung für den Einstieg müssen wir nur ein Fragment erstellen.

1. Melden Sie sich bei AEM as a Cloud Service an und wählen Sie im Hauptmenü die Option **Navigation** -> **Inhaltsfragmente**.

1. Tippen oder klicken Sie auf den [zuvor von Ihnen erstellten Ordner](create-assets-folder.md).
1. Tippen oder klicken Sie auf **Erstellen**.
1. Die Erstellung eines Inhaltsfragments wird als Dialogfeld angezeigt.
Wählen Sie den Speicherort und das Modell aus, die Sie zum Erstellen Ihres Inhaltsfragments verwenden möchten.

   * Die verfügbaren Modelle hängen von der [**Cloud-Konfiguration** ab, die Sie für den Asset-Ordner](create-assets-folder.md) definiert haben, in dem Sie das Inhaltsfragment erstellen.
   * Wenn Ihr Modell nicht verfügbar ist, überprüfen Sie die Konfiguration Ihres Asset-Ordners.

   Fügen Sie den Titel, den Namen und ggf. die Beschreibung hinzu.

   ![Dialogfeld &quot;Neues Inhaltsfragment erstellen&quot;](/help/sites-cloud/administering/content-fragments/assets/cfc-console-create.png)

1. Tippen oder klicken Sie auf **Erstellen** oder  **Erstellen und öffnen**.

Inhaltsfragmente können auf andere Inhaltsfragmente verweisen, was bei Bedarf eine verschachtelte Inhaltsstruktur ermöglicht.

Inhaltsfragmente können auch auf andere Assets in AEM verweisen. [Diese Assets müssen in AEM gespeichert werden](/help/assets/manage-digital-assets.md), bevor ein Verweis auf das Inhaltsfragment erstellt wird.

## Nächste Schritte {#next-steps}

Nachdem Sie nun ein Inhaltsfragment erstellt haben, können Sie zum letzten Teil der Anleitung für den Einstieg übergehen und [API-Anfragen erstellen, um auf Inhaltsfragmente zuzugreifen und diese bereitzustellen](create-api-request.md).

>[!TIP]
>
>Ausführliche Informationen zur Verwaltung von Inhaltsfragmenten finden Sie in der [Dokumentation zu Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/content-fragments.md).
