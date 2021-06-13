---
title: Erstellen und Verwalten von Kanälen in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie Kanäle in Screens as a Cloud Service erstellen und verwalten.
hide: true
hidefromtoc: true
index: false
source-git-commit: ece3fae8b65b4dbdc38e63a211a3f55f4eb91333
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 16%

---


# Erstellen und Verwalten von Kanälen in Screens als Cloud Service {#creating-channels-screens-cloud}

Nachdem Sie ein AEM Screens-Projekt erstellt haben, müssen Sie Kanäle erstellen.
***Kanäle***, zeigen eine Sequenz von Inhalten (Bilder und Videos), eine Website oder eine Einzelseitenanwendung an.

## Vorgabe {#objective}

In diesem Dokument erfahren Sie, wie Sie Kanäle für Ihr AEM Screens-Projekt in Screens Content Provider erstellen und verwalten. Nach dem Lesen sollten Sie:

* Erfahren Sie, wie Sie Kanäle für den Screens Content Provider erstellen.
* Sie können Ihre Kanäle in einem AEM Screens-Projekt verwalten, bezogen auf den Umfang.

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
   > Der Assistent **Erstellen** bietet beim Erstellen eines Kanals verschiedene Arten von Vorlagen. Weitere Informationen finden Sie im Abschnitt Verfügbare Vorlagen im Assistenten zum Erstellen .

1. Geben Sie den Namen Ihres Sequenzkanals ein, z. B. **LoopingChannelOne** und klicken Sie auf **Erstellen**.

   ![](/help/screens-cloud/assets/create-content/channel-create3.png)

   Im Ordner Kanäle in Ihrem AEM Screens-Projekt wird nun **LoopingChannelOne** angezeigt.

1. Nachdem Sie den Kanal erstellt haben, können Sie nun Inhalte zu Ihrem Kanal hinzufügen. Unter [Hinzufügen von Inhalten zu Kanälen](#add-content) erfahren Sie, wie Sie Assets (Bilder/Videos) zu Ihrem Kanal hinzufügen.

## Verwalten eines Kanals {#managing-channels}

Sie können Änderungen vornehmen, Eigenschaften und Dashboard anzeigen sowie einen Kanal kopieren, in der Vorschau anzeigen und löschen.

Navigieren Sie von Ihrem Projekt zum Kanal und wählen Sie den Kanal aus, wie in der folgenden Abbildung dargestellt. Sie können jetzt Optionen auswählen, z. B. den Kanal bearbeiten, Eigenschaften anzeigen, Inhalte in der Vorschau anzeigen, Veröffentlichung verwalten oder den Kanal aus der Aktionsleiste löschen.

![](/help/screens-cloud/assets/create-content/channelprop1.png)

### Hinzufügen von Inhalten zu Kanälen {#add-content}

Um Inhalt in einem Kanal hinzuzufügen oder zu bearbeiten, gehen Sie wie folgt vor:

1. Wählen Sie den Kanal aus, den Sie bearbeiten möchten, wie in der folgenden Abbildung dargestellt. Klicken Sie in der oberen linken Ecke der Aktionsleiste auf **Bearbeiten** , um den Editor zu öffnen.

   ![](/help/screens-cloud/assets/create-content/edit-channel1.png)

1. Mit dem Editor können Sie Assets/Komponenten zu Ihrem Kanal hinzufügen, den Sie veröffentlichen möchten.

1. Ziehen Sie die Assets aus dem linken Bereich und fügen Sie sie zum Editor hinzu.

   ![](/help/screens-cloud/assets/create-content/edit-channel2.png)

   >[!NOTE]
   >Klicken Sie auf **Vorschau** , um die Inhalte Ihres Kanals in der Vorschau anzuzeigen.
   >![](/help/screens-cloud/assets/create-content/edit-channelpreview.png)

## Verfügbare Vorlagen im Assistenten zum Erstellen {#available-templates}

Die folgenden Vorlagen sind bei Verwendung des Kanalassistenten **Create** verfügbar, z. B.:

| Verfügbare Vorlagen | Beschreibung |
|--- |--- |
| Kanal-Ordner | Ermöglicht die Erstellung eines Ordners zum Speichern von Kanalsammlungen. |
| Sequenzkanal | Ermöglicht die Erstellung eines Kanals zum sequenziellen Wiedergeben der Komponenten (einzeln in einer Diashow). |
| Splitscreen-Kanal mit L-Balken links oder rechts | Ermöglicht es den Autoren von Inhalten, verschiedene Arten von Assets in entsprechend großen Bereichen anzuzeigen. |


## Wie geht es weiter {#whats-next}

Nachdem Sie jetzt einen AEM Screens-Kanal in Ihrem Projekt eingerichtet haben, müssen Sie Ihren Kanal veröffentlichen. Lesen Sie [Veröffentlichungskanäle in Screens als Cloud Service](/help/screens-cloud/creating-content/manage-publish.md) , bevor Sie Ihre Player über den Screens-Dienstleister verwalten.