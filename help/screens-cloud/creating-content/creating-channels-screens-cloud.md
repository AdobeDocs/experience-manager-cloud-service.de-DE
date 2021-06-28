---
title: Erstellen und Verwalten von Kanälen in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie Kanäle in Screens as a Cloud Service erstellen und verwalten.
source-git-commit: b9b27c09b1f4a1799a8c974dfb846295664be998
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 16%

---


# Erstellen und Verwalten von Kanälen in Screens as a Cloud Service {#creating-channels-screens-cloud}

Nachdem Sie ein AEM Screens-Projekt erstellt haben, müssen Sie Kanäle erstellen.
***Kanäle***, zeigen eine Sequenz von Inhalten (Bilder und Videos), eine Website oder eine Einzelseitenanwendung an.

## Zielsetzung {#objective}

In diesem Dokument erfahren Sie, wie Sie Kanäle für Ihr AEM Screens-Projekt in Screens Content Provider erstellen und verwalten. Nach dem Lesen sollten Sie Folgendes tun:

* Informationen zum Erstellen von Kanälen für Screens Content Provider
* Verwalten und Bearbeiten von Inhalten in Ihren Kanälen

## Schritte zum Erstellen eines neuen Sequenzkanals in Screens als Cloud Service {#create-new-channel}

>[!NOTE]
>**Voraussetzungen**
>Bevor Sie mit diesem Abschnitt des Handbuchs beginnen, lesen Sie [Erstellen und Verwalten von Projekten in Screens as a Cloud Service](/help/screens-cloud/creating-content/creating-projects-screens-cloud.md).

Gehen Sie wie folgt vor, um einen neuen Sequenzkanal in Screens als Cloud Service zu erstellen:

1. Navigieren Sie zum Screens Content Provider.

1. Navigieren Sie zu Ihrem AEM Screens-Projekt, z. B. *FirstDigitalExperience*.

1. Wählen Sie in Ihrem Projekt den Ordner **Kanäle** aus, z. B. **FirstDigitalExperience** —> **Kanäle** und klicken Sie in der Aktionsleiste auf **Erstellen** .

   ![](/help/screens-cloud/assets/create-content/channel-create1.png)

1. Wählen Sie die Vorlage aus, z. B. **Sequenzkanal** im Assistenten **Erstellen** und klicken Sie auf **Weiter**.

   ![](/help/screens-cloud/assets/create-content/channel-create2.png)
   >[!NOTE]
   > Der Assistent **Erstellen** bietet beim Erstellen eines Kanals verschiedene Arten von Vorlagen. Weitere Informationen finden Sie im Abschnitt [Verfügbare Vorlagen](#available-templates) im Assistenten zum Erstellen .

1. Geben Sie den Namen Ihres Sequenzkanals ein, z. B. **LoopingChannelOne** und klicken Sie auf **Erstellen**.

   ![](/help/screens-cloud/assets/create-content/channel-create3.png)

   Im Ordner Kanäle in Ihrem AEM Screens-Projekt wird nun **LoopingChannelOne** angezeigt.

   Nachdem Sie den Kanal erstellt haben, können Sie nun Inhalte zu Ihrem Kanal hinzufügen. Unter [Hinzufügen von Inhalten zu Kanälen](#add-content) erfahren Sie, wie Sie Assets (Bilder/Videos) zu Ihrem Kanal hinzufügen.

## Verwalten eines Kanals {#managing-channels}

Sie können Änderungen vornehmen, Eigenschaften und Dashboard anzeigen sowie einen Kanal kopieren, in der Vorschau anzeigen und löschen.

Navigieren Sie von Ihrem Projekt zum Kanal und wählen Sie den Kanal aus, wie in der folgenden Abbildung dargestellt. Sie können jetzt Optionen auswählen, z. B. den Kanal bearbeiten, Eigenschaften anzeigen, Inhalte in der Vorschau anzeigen, Veröffentlichung verwalten oder den Kanal aus der Aktionsleiste löschen.

![](/help/screens-cloud/assets/create-content/channelprop1.png)

### Hinzufügen von Inhalten zu Kanälen {#add-content}

Um Inhalt in einem Kanal hinzuzufügen oder zu bearbeiten, gehen Sie wie folgt vor:

1. Wählen Sie den Kanal aus, den Sie bearbeiten möchten, wie in der folgenden Abbildung dargestellt. Klicken Sie oben links in der Aktionsleiste auf **Bearbeiten** , um den Editor zu öffnen.

   ![](/help/screens-cloud/assets/create-content/edit-channel1.png)

1. Mit dem Editor können Sie Assets/Komponenten zu Ihrem Kanal hinzufügen, den Sie veröffentlichen möchten.

1. Ziehen Sie die Assets aus dem linken Bereich und fügen Sie sie zum Editor hinzu.

   ![](/help/screens-cloud/assets/create-content/edit-channel2.png)

   >[!NOTE]
   >Klicken Sie auf **Vorschau** , um die Inhalte Ihres Kanals in der Vorschau anzuzeigen.
   >![](/help/screens-cloud/assets/create-content/edit-channelpreview.png)

## Verfügbare Vorlagen im Assistenten zum Erstellen {#available-templates}

Die folgenden Vorlagen sind bei Verwendung des Kanalassistenten **Erstellen** verfügbar:

| Verfügbare Vorlagen | Beschreibung |
|--- |--- |
| Kanal-Ordner | Ermöglicht die Erstellung eines Ordners zum Speichern von Kanalsammlungen. |
| Sequenzkanal | Ermöglicht die Erstellung eines Kanals zum sequenziellen Wiedergeben der Komponenten (einzeln in einer Diashow). |
| Splitscreen-Kanal mit L-Balken links oder rechts | Ermöglicht es den Autoren von Inhalten, verschiedene Arten von Assets in entsprechend großen Bereichen anzuzeigen. |


## Wie geht es weiter {#whats-next}

Nachdem Sie jetzt einen AEM Screens-Kanal in Ihrem Projekt eingerichtet haben, müssen Sie Ihren Kanal veröffentlichen. Lesen Sie [Veröffentlichungskanäle in Screens als Cloud Service](/help/screens-cloud/creating-content/manage-publish.md) , bevor Sie Ihre Player über den Screens-Dienstleister verwalten.