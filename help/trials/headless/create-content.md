---
title: Erstellen von Headless-Inhalten
description: Nutzen Sie ihr zuvor erstelltes Inhaltsfragmentmodell, um Inhalte zu erstellen, die für die Seitenbearbeitung oder als Grundlage für den Headless-Content verwendet werden können.
hidefromtoc: true
index: false
exl-id: d74cf5fb-4c4a-4363-a500-6e2ef6811e60
feature: Headless
role: Admin, User, Developer
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 100%

---


# Erstellen von Headless-Inhalten {#create-content}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_create_content"
>title="Erstellen von Headless-Inhalten"
>abstract="Sie erfahren, wie Sie unter Verwendung des im vorherigen Modul erstellten Modells Inhalte erstellen können, die für die Seitenbearbeitung oder als Grundlage für Headless-Inhalte verwendet werden können."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_create_content_guide"
>title="Inhaltsfragmentkonsole starten"
>abstract="Die Erstellung konsistenter, qualitativ hochwertiger Inhalte, die nahtlos in all Ihren Apps und auf Ihren Websites funktionieren, liefert hervorragende Kundenerlebnisse. Dieses Modul führt Sie durch die Erstellung Ihres ersten Headless-Inhalts mithilfe der Inhaltsfragmentkonsole.<br><br>Klicken Sie unten auf die Schaltfläche, um dieses Modul in einer neuen Registerkarte zu starten. Folgen Sie danach diesem Handbuch."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_create_content_guide_footer"
>title="Gut gemacht! In diesem Modul haben Sie erfahren, wie Sie auf der Grundlage des zuvor erstellten Modells Headless-Inhalte als Inhaltsfragment erstellen können. Sie wissen jetzt, wie Content-Teams Inhalte für Apps und Websites unabhängig von Entwicklungszyklen erstellen und verwalten können."
>abstract=""

## Erstellen eines Inhaltsfragments {#create-fragment}

Inhaltsfragmente stellen Ihren Headless-Inhalt dar und basieren auf vordefinierten Strukturen, den sogenannten Inhaltsfragmentmodellen. Sie haben ein Modell bereits in einem vorherigen Modul erstellt.

In diesem Modul erstellen Sie mithilfe der Inhaltsfragmentkonsole ein Inhaltsfragment, das auf diesem Modell basiert. Stellen Sie sich die Inhaltsfragmentkonsole als Ihre Bibliothek vor, in der Headless-Content verfügbar ist. Verwenden Sie die Inhaltsfragmentkonsole, um neue Inhaltsfragmente zu erstellen und vorhandene Fragmente zu verwalten.

Die Inhaltsfragmentkonsole wird verwendet, um Headless-Inhalte über Bereitstellungskanäle hinweg und unabhängig vom Kontext zu erstellen und zu bearbeiten. In vielen Authoring-Fällen kann dies die effektivste Methode sein. In einem späteren Modul wird die Bearbeitung von Headless-Inhalten im Kontext und an Ort und Stelle erkundet.

1. Wählen Sie oben rechts in der Konsole die Schaltfläche **Erstellen** aus.

1. Das Dialogfeld **Neues Inhaltsfragment** wird geöffnet, in dem Sie mit der Erstellung eines Inhaltsfragments beginnen können. **Speicherort** wird automatisch mit dem Speicherort des neuen Inhalts befüllt.

1. Wählen Sie in der Dropdown-Liste **Inhaltsfragmentmodell** das zuvor erstellte Inhaltsfragmentmodell **Abenteuer**.

1. Fügen Sie `Tuscany` als beschreibenden **Titel** für das Inhaltsfragment hinzu. Dadurch wird Ihr Fragment in der Konsole identifiziert.

1. Wählen Sie **Erstellen und öffnen** aus.

![Erstellen eines neuen Inhaltsfragments](assets/do-not-localize/create-content.png)

>[!TIP]
>
>Abhängig von Ihren Browser-Einstellungen wird die neue Browser-Registerkarte möglicherweise durch einen Popup-Blocker unterdrückt. Wenn sich Ihr neues Fragment nicht öffnet, nachdem Sie auf **Erstellen und öffnen** geklickt haben, überprüfen Sie bitte Ihre Browser-Einstellungen.

## Hinzufügen von Inhalt zu Ihrem Inhaltsfragment {#add-content}

Wenn Sie Ihr neues Inhaltsfragment speichern und öffnen, wird der Inhaltsfragment-Editor auf einer neuen Registerkarte geöffnet. Hier können Sie den Inhalt des neuen Fragments hinzufügen.

1. Der Inhaltsfragment-Editor enthält die Felder, die Sie im ausgewählten Modell definiert haben. Hier können Sie jedem Feld Inhalt hinzufügen, um Ihr Inhaltsfragment zu vervollständigen. Ihr Fortschritt wird automatisch gespeichert.

1. Geben Sie einen **Titel** für Ihr Fragment an, indem Sie `Tuscan Adventure` eingeben.

1. Geben Sie eine **Beschreibung** für Ihr Fragment an, indem Sie den folgenden Text einfügen.

   ```text
   Visiting Tuscany on a bicycle is about experiencing the old world charm of Italy on your own terms. Your efforts on the climbs of Italy's rolling hills during this tour are rewarded with sunny Mediterranean landscapes and unmatched Italian hospitality. Tuscany's natural wonders have always been a well of inspiration for arts and culture. Find out why as you explore the Italian countryside and coastline on bicycle.
   ```

1. Geben Sie einen **Preis** für Ihr Fragment an, indem Sie `$700` eingeben.

1. Geben Sie ein **Bild** an, das für die Reise repräsentativ ist, indem Sie auf **Asset hinzufügen** im Feld **Bild** tippen oder klicken.

1. Wählen Sie im Popup-Fenster des Assets **Assets durchsuchen** aus, um ein vorhandenes Asset aus der Asset-Bibliothek auszuwählen.

   ![Asset hinzufügen](assets/do-not-localize/add-asset.png)

1. Das Dialogfeld **Asset auswählen** wird geöffnet. Navigieren Sie mit dem Navigationsbaum im linken Bereich zu **Alle Assets** > **aem-demo-assets** > **de** > **Abenteuer** > **Radfahren-Toskana**.

1. Der Inhalt des Ordners **Radfahren-Toskana** wird auf der rechten Seite angezeigt. Wählen Sie das Bild `ADOBESTOCK_141786166.JPEG` aus.

1. Wählen Sie **Auswählen** aus.

   ![Asset auswählen](assets/do-not-localize/select-asset.png)

1. Das ausgewählte Bild wird im Inhaltsfragment angezeigt. Der Editor speichert die Änderungen automatisch.

1. Nachdem Sie den gesamten Inhalt hinzugefügt haben, wählen Sie die Schaltfläche **Veröffentlichen** oben rechts im Editor aus. Dadurch kann Ihr Inhaltsfragment von externen Apps verwendet werden. Wählen Sie dann **Jetzt** aus der Dropdown-Liste aus. Sie können die Veröffentlichung auch zu einem späteren Zeitpunkt planen.

   ![Inhalt veröffentlichen](assets/do-not-localize/publish.png)

1. Der Dialog **Inhaltsfragmente veröffentlichen** wird angezeigt. AEM führt automatisch eine Verweisprüfung durch, um sicherzustellen, dass alle erforderlichen Ressourcen für Ihr Inhaltsfragment veröffentlicht werden. In diesem Fall müssen Sie auch das von Ihnen erstellte Modell veröffentlichen. Wählen Sie **Veröffentlichen** aus.

   ![Veröffentlichungs- und Verweisprüfung](assets/do-not-localize/publish-confirm.png)

1. Die Veröffentlichung wird in einem Banner bestätigt.

Ihr Inhalt wird veröffentlicht und kann als Inhaltsfragment für Ihre App oder Website bereitgestellt werden.
