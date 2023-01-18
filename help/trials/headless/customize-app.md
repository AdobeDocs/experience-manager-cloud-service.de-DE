---
title: Anpassen von Inhalten in einer Beispiel-React-App
description: Verwenden Sie eine React-Beispielanwendung, um zu erfahren, wie Sie Inhalte mithilfe des Headless-Funktionssatzes in AEM as a Cloud Service anpassen können.
hidefromtoc: true
index: false
exl-id: 32290ad4-d915-41b7-a073-2637eb38e978
source-git-commit: bcab02cbd84955ecdc239d4166ae38e5f79b3264
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 0%

---


# Anpassen von Inhalten in einer Beispiel-React-App {#customize-app}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_react_app"
>title="Inhalt in einer React-Beispielanwendung anpassen"
>abstract="Ihre AEM Headless-Testversion ist mit einer React-Beispielanwendung integriert, die Sie anpassen können."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_react_app_guide"
>title="Starten des Inhaltsfragmente-Editors"
>abstract="Ihre AEM Headless-Testversion ist mit einer React-Beispielanwendung integriert, sodass Sie sehen können, wie einfach es für jeden ist, Inhalte ohne Entwicklungszeit unabhängig zu verwalten.<br><br>Starten Sie dieses Modul in einer neuen Registerkarte, indem Sie unten klicken und diesem Handbuch folgen."
>additional-url="https://video.tv.adobe.com/v/328618?captions=ger" text="Video Anpassen des App-Starts"

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_react_app_guide_footer"
>title="In diesem Modul haben Sie erfahren, wie Sie eine React-Beispielanwendung anpassen können.<br><br>Time to Market: Beschleunigen!<br>Entwicklungszyklen: Reduziert!<br><br>Jetzt wissen Sie, wie einfach die Verwaltung von Headless Content für Websites und Apps ist, die auf AEM Headless-Funktionen basieren."
>abstract=""

## Vorschau der App {#preview}

Klicken Sie auf **Starten des Inhaltsfragmente-Editors** über die Schaltfläche oben wird der Inhaltsfragment-Editor in einer neuen Registerkarte geöffnet.

![Inhaltsfragmente-Editor](assets/customize-app/content-fragment-editor.png)

Die Beispielanwendung, die mit Ihrer AEM Headless-Testversion bereitgestellt wird, basiert auf Inhaltsfragmenten, die über GraphQL bereitgestellt werden. Verwenden Sie den Inhaltsfragment-Editor, um sich mit dem Inhalt vertraut zu machen, indem Sie eine Vorschau des Beispiels anzeigen.

1. Tippen oder klicken Sie auf **Vorschau** rechts oben im Editor-Bildschirm.

1. Die Demo-App wird in einer neuen Registerkarte geöffnet. Die App ist für die fiktive WKND Outdoor Lifestyle-Marke. Klicken Sie auf die Schaltfläche, um zum Beispielinhalt zu navigieren.

   ![Vorschau der Demo-App](assets/customize-app/preview-demo-app.png)

1. Kehren Sie zur Registerkarte &quot;Browser&quot;des Inhaltsfragment-Editors zurück, um fortzufahren.

## Bearbeiten einer Kopfzeile in der App {#edit-app}

Der Inhaltsfragment-Editor zeigt das grundlegende Layout der App als ein Seiteninhaltsfragment an. Die **Bedienfelder** verschiedene Seiten der App darstellen, von denen jede ein eigenes Inhaltsfragment ist. Durch Ändern dieser Fragmente können Sie den Inhalt der App ändern.

1. Tippen oder klicken Sie auf **Mtn Biker in Canyon** im **Bedienfelder** Abschnitt.

   ![Tippen Sie auf Mtn Biker im Canyon-Fragment](assets/customize-app/mtn-biker-in-canyon.png)

1. Der Editor öffnet das Kopfzeilenbedienfeld der App für den Mountainbiker. Jedes Bedienfeld besteht aus Ebenen, die verschiedene Bilder und Text darstellen, aus denen sich das Erlebnis zusammensetzt.

   ![Bedienfelder](assets/customize-app/panels.png)

1. Auswählen der Textebene **Mtn Biker in Canyon Textebene**. Dadurch wird die Detailansicht der Ebene im Editor geöffnet. Die Ebene besteht aus mehreren Inhaltsfragmenten, die den Text steuern, der in diesem Bereich der App angezeigt wird.

   ![Wählen Sie Mtn Biker im Canyon-Titel aus.](assets/customize-app/mtn-biker-in-canyon-text-layer.png)

1. Wählen Sie die **Mtn Biker in Canyon-Titel** Textelement. Dadurch wird der Inhaltsfragment-Editor geöffnet.

   ![Wählen Sie das Textelement &quot;Mtn Biker&quot;im Textelement &quot;Canyon Title&quot;](assets/customize-app/mtn-biker-in-canyon-title.png)

1. Text ändern von `Your next great adventure is calling` nach `Choose your own adventure`. Die Änderung wird automatisch vom Editor gespeichert.

1. Tippen oder klicken Sie auf **Vorschau** oben rechts im Fenster, um Ihre Änderungen zu sehen. Die Vorschau der Demo-App wird in einer neuen Registerkarte geöffnet.

   ![Vorschau der Demo-App](assets/customize-app/preview-demo-app-text.png)

So einfach ist es, Inhalte in einer React-App zu aktualisieren, wenn sie in AEM Headless-CMS integriert sind.

## Bild in der App tauschen {#change-image}

Nachdem Sie eine Überschrift in der App geändert haben, versuchen Sie, ein Bild zu ändern.

1. Kehren Sie zur Registerkarte &quot;Browser&quot;des Inhaltsfragment-Editors zurück.

1. Sie müssen zur richtigen Stelle im Inhaltsfragment-Editor zurückkehren. Die Breadcrumbs oben links im Editor zeigen an, wo Sie sich in Ihrer Inhaltshierarchie befinden. Tippen oder klicken Sie auf **Mtn Biker in Canyon** in den Breadcrumbs, um zu dieser Seite zurückzukehren.

   ![Breadcrumb](assets/customize-app/breadcrumbs.png)

1. Wählen Sie die **Mtn Biking - Biker** Bildebene. Dadurch wird der Inhaltsfragment-Editor geöffnet

   ![Bildfragment bearbeiten](assets/customize-app/mtn-biking-biker.png)

1. Tippen oder klicken Sie auf **X** , um das Biker-Bild zu entfernen. Das Bild verschwindet und der Editor zeigt einen Fehler an, da das Bild für dieses Inhaltsfragmentmodell erforderliche Daten ist.

   ![Bild aus Fragment entfernt](assets/customize-app/mtn-biking-biker-no-image.png)

1. Tippen oder klicken Sie auf **Asset hinzufügen**.

1. Die **Asset auswählen** wird geöffnet und der Pfad **sample-wknd-app** > **en** > **image-files** automatisch für Sie ausgewählt.

1. Bild auswählen `biker-yellow.png` und tippen oder klicken Sie dann auf **Auswählen**.

   ![Asset auswählen](assets/customize-app/select-asset.png)

1. Das Bild des Fahrers wird durch das ausgewählte Bild ersetzt. Der Editor speichert die Änderungen automatisch.

   ![Bearbeitetes Fragment des Biker-Bildes](assets/customize-app/mtn-biking-biker-edited.png)

1. Tippen oder klicken Sie auf **Vorschau** oben rechts im Fenster, um Ihre Änderungen zu sehen. Die Vorschau der Demo-App wird in einer neuen Registerkarte geöffnet. Klicken Sie im Browser auf &quot;Aktualisieren&quot;. Ihr neues Biker-Bild mit gelben Shorts sollte in der App angezeigt werden.

So einfach ist es, Bilder und Assets in Ihren Apps mit AEM Headless-CMS zu aktualisieren.

## Hinzufügen eines Verweises zu einem neuen Inhaltsfragment in der App {#create-moment}

Nachdem Sie jetzt das Bild des Bikers aktualisiert haben, gehen wir durch, wie wir neue Inhalte zu einer App hinzufügen können, indem wir ein neues Inhaltsfragment erstellen und darauf verweisen. Sie fügen dem zweiten Bereich der App einen durch einen &quot;Shop-fähigen Moment&quot;-Inhaltsfragment verwalteten Produktabruf hinzu.

![Beispiel für einen Moment mit Shopping-Funktion](assets/customize-app/example-shoppable-moment.png)

1. Kehren Sie zur Registerkarte &quot;Browser&quot;des Inhaltsfragment-Editors zurück.

1. Sie müssen zur richtigen Stelle im Inhaltsfragment-Editor zurückkehren. Die Breadcrumbs oben links im Editor zeigen an, wo Sie sich in Ihrer Inhaltshierarchie befinden. Tippen oder klicken Sie auf **WKND-Homepage** in den Breadcrumbs, um zu dieser Seite zurückzukehren.

   ![Navigieren Sie zurück zum Layoutbildschirm.](assets/customize-app/breadcrumbs-2.png)

1. Wählen Sie die **Mtn Biker auf WKND Gelb** Bereich.

   ![Einen Shop-fähigen Moment erstellen](assets/customize-app/mtn-biker-on-wknd-yellow.png)

1. Wählen Sie die **Mtn Biking - Shoppable** Ebene.

   ![Auswählen einer Shop-fähigen Momentschicht](assets/customize-app/mtn-biking-shoppable.png)

1. Um einen neuen Abruf in diesem Bedienfeld zu erstellen, müssen Sie einen neuen Moment mit Shopping-Funktion für Inhaltsfragmente erstellen. Tippen oder klicken Sie auf **+ Neues Fragment erstellen** Schaltfläche.

   ![Einen Shop-fähigen Moment hinzufügen](assets/customize-app/create-new-fragment.png)

1. Sie müssen zunächst ein Modell auswählen, auf dem das neue Inhaltsfragment basieren soll. Wählen Sie die **Shopping-Moment-Element** -Modell aus **Inhaltsfragmentmodell** Dropdown-Liste.

1. Geben Sie dem Inhaltsfragment einen Namen. Geben Sie beispielsweise `Shorts` in **Name** -Feld.

   ![Benennen Sie den Shop-fähigen Moment.](assets/customize-app/new-content-fragment.png)

1. Tippen oder klicken Sie auf **Erstellen und öffnen**.

1. Der Editor wird für Ihr neues Inhaltsfragment geöffnet.

1. Benennen Sie den Shop-fähigen Moment im **Text** -Feld, z. B. `Yellow shorts`.

1. Festlegen von Werten für **X** und **Y**. Hier sollte dieser Aufruf im Bedienfeld überlagert werden. Änderungen am Fragment werden vom Editor automatisch gespeichert
   * **X**: `-18`
   * **Y**: `-28`

   ![Den Shop-fähigen Moment bearbeiten](assets/customize-app/edit-shoppable-moment.png)

1. Tippen oder klicken Sie auf **Vorschau** oben rechts im Fenster, um Ihre Änderungen zu sehen. Die Vorschau der Demo-App wird in einer neuen Registerkarte geöffnet. Klicken Sie im Browser auf Aktualisieren , um die Positionierung zu testen und im Editor nach Bedarf Anpassungen vorzunehmen.

Jetzt wissen Sie, wie das Erstellen neuer Inhalte und das Referenzieren als Inhaltsfragment in Ihrer App ohne Entwicklungszyklen abgeschlossen werden können.
