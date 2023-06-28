---
title: Erstellen von Headless-Inhalten
description: Nutzen Sie ihr zuvor erstelltes Inhaltsfragmentmodell, um Inhalte zu erstellen, die für die Seitenbearbeitung oder als Grundlage für den Headless-Content verwendet werden können.
hidefromtoc: true
index: false
exl-id: d74cf5fb-4c4a-4363-a500-6e2ef6811e60
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 54%

---


# Erstellen von Headless-Inhalten {#create-content}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_create_content"
>title="Erstellen neuer Inhalte"
>abstract="Mithilfe des Modells, das Sie im vorherigen Modul erstellt haben, erfahren Sie, wie Sie Inhalte erstellen, die für die Seitenbearbeitung oder als Grundlage für Ihren Headless Content verwendet werden können."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_create_content_guide"
>title="Starten der Inhaltsfragmentkonsole"
>abstract="Die Erstellung konsistenter, qualitativ hochwertiger Inhalte, die nahtlos auf all Ihren Apps und Websites funktionieren, liefert hervorragende Customer Experiences. Dieses Modul führt Sie durch die Erstellung eines ersten Inhaltsfragments.<br><br>Klicken Sie unten auf die Schaltfläche, um dieses Modul in einer neuen Registerkarte zu starten. Folgen Sie danach diesem Handbuch."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_create_content_guide_footer"
>title="Gute gemacht! In diesem Modul haben Sie gelernt, auf der Basis Ihres zuvor erstellten Modells ein Inhaltsfragment zu erstellen. Sie wissen jetzt, wie Content Teams Inhalte für Apps und Websites unabhängig von Entwicklungszyklen erstellen und verwalten können."
>abstract=""

## Erstellen eines Inhaltsfragments {#create-fragment}

Inhaltsfragmente stellen Ihren Headless-Inhalt dar und basieren auf vordefinierten Strukturen, den sogenannten Inhaltsfragmentmodellen. Sie haben ein Modell bereits in einem vorherigen Modul erstellt.

In diesem Modul erstellen Sie mithilfe der Inhaltsfragmentkonsole ein neues Inhaltsfragment, das auf diesem Modell basiert. Stellen Sie sich die Inhaltsfragmentkonsole als Ihre Bibliothek vor, in der Headless-Content verfügbar ist. Verwenden Sie die Inhaltsfragmentkonsole, um neue Inhaltsfragmente zu erstellen und vorhandene Fragmente zu verwalten.

1. Tippen oder klicken Sie oben rechts in der Konsole auf die Schaltfläche **Erstellen**.

1. Die **Neues Inhaltsfragment** wird ein Dialogfeld geöffnet, in dem Sie mit der Erstellung eines neuen Inhaltsfragments beginnen können. **Standort** automatisch mit dem Speicherort des neuen Inhalts gefüllt.

1. Im **Inhaltsfragmentmodell** in der Dropdown-Liste auswählen **Abenteuer** Inhaltsfragmentmodell, das Sie zuvor erstellt haben.

1. Hinzufügen `Tuscany` als Beschreibung **Titel** für das Inhaltsfragment. Dadurch wird Ihr Fragment in der Konsole identifiziert.

1. Tippen oder klicken Sie auf **Erstellen und öffnen**.

![Erstellen eines neuen Inhaltsfragments](assets/do-not-localize/create-content.png)

>[!TIP]
>
>Abhängig von Ihren Browsereinstellungen wird die neue Browser-Registerkarte möglicherweise durch einen Popup-Blocker unterdrückt. Wenn das neue Fragment nach dem Klicken nicht geöffnet wird **Erstellen und öffnen**, überprüfen Sie Ihre Browsereinstellungen.

## Inhalt zu Ihrem Inhaltsfragment hinzufügen {#add-content}

Nachdem Sie das neue Inhaltsfragment gespeichert und geöffnet haben, wird der Inhaltsfragment-Editor auf einer neuen Registerkarte geöffnet. Hier können Sie den Inhalt des neuen Fragments hinzufügen.

1. Der Inhaltsfragment-Editor enthält die Felder, die Sie im ausgewählten Modell definiert haben. Hier können Sie jedem Feld Inhalt hinzufügen, um Ihr Inhaltsfragment zu vervollständigen. Ihr Fortschritt wird automatisch gespeichert.

1. Bereitstellung einer **Titel** für Ihr Fragment durch Eingabe von `Tuscan Adventure`.

1. Bereitstellung einer **Beschreibung** für Ihr Fragment durch Einfügen in den folgenden Text.

   ```text
   Visiting Tuscany on a bicycle is about experiencing the old world charm of Italy on your own terms. Your efforts on the climbs of Italy's rolling hills during this tour are rewarded with sunny Mediterranean landscapes and unmatched Italian hospitality. Tuscany's natural wonders have always been a well of inspiration for arts and culture. Find out why as you explore the Italian countryside and coastline on bicycle.
   ```

1. Bereitstellung einer **Preis** für Ihr Fragment durch Eingabe in `$700`.

1. Stellen Sie eine **Bild** die für die Reise repräsentativ ist, indem Sie auf **Asset hinzufügen** im **Bild** -Feld.

1. Tippen oder klicken Sie im Popup-Fenster des Assets auf **Durchsuchen von Assets** , um aus einem vorhandenen Asset in der Asset-Bibliothek auszuwählen.

   ![Asset hinzufügen](assets/do-not-localize/add-asset.png)

1. Die **Asset auswählen** wird geöffnet. Navigieren Sie mit dem Navigationsbaum im linken Bereich zu **Alle Assets** > **aem-demo-assets** > **en** > **Abenteuer** > **Radfahrer-Toskana**.

1. Der Inhalt der **Radfahrer-Toskana** -Ordner auf der rechten Seite angezeigt. Bild auswählen `ADOBESTOCK_141786166.JPEG`.

1. Tippen oder klicken Sie auf **Auswählen**.

   ![Asset auswählen](assets/do-not-localize/select-asset.png)

1. Das ausgewählte Bild wird im Inhaltsfragment angezeigt. Der Editor speichert die Änderungen automatisch.

1. Nachdem Sie den gesamten Inhalt hinzugefügt haben, tippen oder klicken Sie auf die Schaltfläche **Veröffentlichen** oben rechts im Editor. Dadurch kann Ihr Inhaltsfragment von externen Apps verwendet werden. Wählen Sie anschließend **Jetzt** aus der Dropdown-Liste aus. Sie können die Veröffentlichung auch zu einem späteren Zeitpunkt planen.

   ![Inhalt veröffentlichen](assets/do-not-localize/publish.png)

1. Der Dialog **Inhaltsfragmente veröffentlichen** wird angezeigt. AEM führt automatisch eine Verweisprüfung durch, um sicherzustellen, dass alle erforderlichen Ressourcen für Ihr Inhaltsfragment veröffentlicht werden. In diesem Fall müssen Sie auch das von Ihnen erstellte Modell veröffentlichen. Tippen oder klicken Sie auf **Veröffentlichen**.

   ![Veröffentlichungs- und Verweisprüfung](assets/do-not-localize/publish-confirm.png)

1. Die Veröffentlichung wird in einem Banner bestätigt.

Ihr Inhalt wird veröffentlicht und kann als Inhaltsfragment für Ihre App oder Website bereitgestellt werden.
