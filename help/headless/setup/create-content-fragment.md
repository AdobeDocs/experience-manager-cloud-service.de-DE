---
title: Erstellen von Inhaltsfragmenten – Headless-Einrichtung
description: Erfahren Sie, wie Sie mit den Inhaltsfragmenten von AEM seitenunabhängige Inhalte für die Headless-Bereitstellung entwerfen, erstellen, kuratieren und verwenden können.
exl-id: a227ae2c-f710-4968-8a00-bfe48aa66145
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 85%

---

# Erstellen von Inhaltsfragmenten – Headless-Einrichtung {#creating-content-fragments}

Erfahren Sie, wie Sie mit den Inhaltsfragmenten von AEM seitenunabhängige Inhalte für die Headless-Bereitstellung entwerfen, erstellen, kuratieren und verwenden können.

## Was sind Inhaltsfragmente? {#what-are-content-fragments}

[Nachdem Sie einen Asset-Ordner erstellt haben](create-assets-folder.md), in dem Ihre Inhaltsfragmente gespeichert werden sollen, können Sie nun Fragmente erstellten.

Inhaltsfragmente ermöglichen Ihnen das Entwerfen, Erstellen, Kuratieren und Verwenden von seitenunabhängigen Inhalten. Außerdem können Sie Inhalte zur Verwendung an mehreren Orten und über mehrere Kanäle hinweg vorbereiten.

Inhaltsfragmente enthalten strukturierte Inhalte und können im JSON-Format bereitgestellt werden.

## Erstellen eines Inhaltsfragments {#how-to-create-a-content-fragment}

Inhaltsautorinnen und -autoren können eine beliebige Anzahl von Inhaltsfragmenten für ihre Inhalte erstellen. Das die zentrale Aufgabe, die sie in AEM ausführen. Für die Zwecke dieses Erste-Schritte-Handbuchs brauchen wir nur eines zu erstellen.

1. Melden Sie sich bei AEM as a Cloud Service an und wählen Sie im Hauptmenü **Navigation** > **Inhaltsfragmente** aus.

1. Wählen Sie den [zuvor erstellten Ordner](create-assets-folder.md) aus.
1. Wählen Sie **Erstellen** aus.
1. Die Erstellung eines Inhaltsfragments wird als Dialogfeld angezeigt.
Wählen Sie den Speicherort und das Modell aus, das Sie zum Erstellen Ihres Inhaltsfragments verwenden möchten.

   * Die verfügbaren Modelle hängen von der [**Cloud-Konfiguration** ab, die Sie für den Asset-Ordner](create-assets-folder.md) definiert haben, in dem Sie das Inhaltsfragment erstellen.
   * Wenn Ihr Modell nicht verfügbar ist, überprüfen Sie die Konfiguration Ihres Asset-Ordners.

   Fügen Sie den Titel, den Namen und ggf. eine Beschreibung hinzu.

   ![Dialogfeld „Neues Inhaltsfragment erstellen“](/help/sites-cloud/administering/content-fragments/assets/cfc-console-create.png)

1. Wählen Sie **Erstellen** oder **Erstellen und öffnen** aus.

Inhaltsfragmente können auf andere Inhaltsfragmente verweisen, was bei Bedarf eine verschachtelte Inhaltsstruktur ermöglicht.

Inhaltsfragmente können auch auf andere Assets in AEM verweisen. [Diese Assets müssen in AEM gespeichert werden](/help/assets/manage-digital-assets.md), bevor ein Verweis auf das Inhaltsfragment erstellt wird.

## Nächste Schritte {#next-steps}

Nachdem Sie nun ein Inhaltsfragment erstellt haben, können Sie mit dem letzten Teil der ersten Schritte fortfahren und [API-Anfragen für den Zugriff auf und die Bereitstellung von Inhaltsfragmenten erstellen](create-api-request.md).

>[!TIP]
>
>Ausführliche Informationen zur Verwaltung von Inhaltsfragmenten finden Sie in der [Dokumentation zu Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/overview.md).
