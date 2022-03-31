---
title: Erstellen und Verwalten von Kanälen in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie in Screens as a Cloud Service Kanäle erstellen und verwalten.
exl-id: 3b0bae7a-4a45-485a-ab04-604510ff6578
source-git-commit: afcee8019c9b59f3eb1fdcabd569272eeea76dab
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 50%

---

# Erstellen und Verwalten eines Kanals in Screens as a Cloud Service {#creating-channels-screens-cloud}

Nachdem Sie ein AEM Screens-Projekt erstellt haben, müssen Sie Kanäle erstellen.
***Kanäle*** zeigen eine Sequenz von Inhalten (Bilder und Videos), eine Website oder eine Einzelseiten-Webanwendung an.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie in Screens Content Provider Kanäle für Ihr AEM Screens-Projekt erstellen und verwalten. Nach dem Lesen sollten Sie Folgendes können:

* verstehen, wie man Kanäle für Screens Content Provider erstellt
* Inhalte in Ihren Kanälen verwalten und bearbeiten
* Aktivierungszeitplan für Ihre Kanäle

## Schritte zum Erstellen eines neuen Sequenzkanals in Screens as a Cloud Service {#create-new-channel}

>[!NOTE]
>**Voraussetzungen**
>Bevor Sie mit diesem Abschnitt des Handbuchs beginnen, lesen Sie [Erstellen und Verwalten von Projekten in Screens as a Cloud Service](/help/screens-cloud/creating-content/creating-projects-screens-cloud.md).

Gehen Sie wie folgt vor, um einen neuen Sequenzkanal in Screens as a Cloud Service zu erstellen:

1. Gehen Sie zu Screens Content Provider.

1. Gehen Sie zu Ihrem AEM Screens-Projekt, z. B. *FirstDigitalExperience*.

1. Wählen Sie in Ihrem Projekt den Ordner **Kanäle** aus, z. B. **FirstDigitalExperience** --> **Kanäle** und klicken Sie in der Aktionsleiste auf **Erstellen**.

   ![](/help/screens-cloud/assets/create-content/channel-create1.png)

1. Wählen Sie die Vorlage aus, z. B. **Sequenzkanal** im Assistenten **Erstellen** und klicken Sie auf **Weiter**.

   ![](/help/screens-cloud/assets/create-content/channel-create2.png)
   >[!NOTE]
   > Der Assistent **Erstellen** bietet beim Erstellen eines Kanals verschiedene Arten von Vorlagen. Weitere Informationen finden Sie im Abschnitt [Verfügbare Vorlagen](#available-templates) im Assistenten „Erstellen“.

1. Geben Sie den Namen Ihres Sequenzkanals ein, z. B. **LoopingChannelOne** und klicken Sie auf **Erstellen**.

   ![](/help/screens-cloud/assets/create-content/channel-create3.png)

   Im Ordner „Kanäle“ in Ihrem AEM Screens-Projekt wird nun **LoopingChannelOne** angezeigt.

   Nachdem Sie den Kanal erstellt haben, können Sie nun Inhalte zu Ihrem Kanal hinzufügen. Unter [Hinzufügen von Inhalten zu Kanälen](#add-content) erfahren Sie, wie Sie Assets (Bilder/Videos) zu Ihrem Kanal hinzufügen.

## Verwalten eines Kanals {#managing-channels}

Sie können Änderungen vornehmen, Eigenschaften und Dashboard anzeigen sowie einen Kanal kopieren, in der Vorschau anzeigen und löschen.

Gehen Sie von Ihrem Projekt zum Kanal und wählen Sie den Kanal aus, wie in der Abbildung unten dargestellt. Sie können jetzt Optionen auswählen, z. B. den Kanal bearbeiten, Eigenschaften anzeigen, Inhalte in der Vorschau anzeigen, Veröffentlichung verwalten oder den Kanal aus der Aktionsleiste löschen.

![](/help/screens-cloud/assets/create-content/channelprop1.png)

### Hinzufügen von Inhalten zu Kanälen {#add-content}

Um Inhalt in einem Kanal hinzuzufügen oder zu bearbeiten, gehen Sie wie folgt vor:

1. Klicken Sie auf den Kanal, den Sie bearbeiten möchten (wie in der untenstehenden Abbildung gezeigt). Klicken Sie in der oberen linken Ecke der Aktionsleiste auf **Bearbeiten**, um den Editor zu öffnen.

   ![](/help/screens-cloud/assets/create-content/edit-channel1.png)

1. Mit dem Editor können Sie Assets/Komponenten zu Ihrem Kanal hinzufügen, die Sie veröffentlichen möchten.

1. Ziehen Sie die Assets per Drag-and-Drop aus dem linken Bereich und fügen Sie sie zum Editor hinzu.

   ![](/help/screens-cloud/assets/create-content/edit-channel2.png)

   >[!NOTE]
   >Klicken Sie auf **Vorschau**, um die Inhalte Ihres Kanals in der Vorschau anzuzeigen.
   >![](/help/screens-cloud/assets/create-content/edit-channelpreview.png)

## Verfügbare Vorlagen im Assistenten „Erstellen“. {#available-templates}

Die folgenden Vorlagen sind bei Verwendung des Assistenten zum **Erstellen** eines Kanals verfügbar:

| Verfügbare Vorlagen | Beschreibung |
|--- |--- |
| Kanal-Ordner | Ermöglicht die Erstellung eines Ordners zum Speichern von Kanalsammlungen. |
| Sequenzkanal | Ermöglicht die Erstellung eines Kanals zum sequenziellen Wiedergeben der Komponenten (einzeln in einer Diashow). |
| Splitscreen-Kanal mit L-Balken links oder rechts | Ermöglicht es den Autoren von Inhalten, verschiedene Arten von Assets in entsprechend großen Bereichen anzuzeigen. |

## Standardzuweisungsdetails für Kanäle verwenden {#default-channels}

Mit dieser Funktion können Sie einen standardmäßigen Aktivierungsplan für einen Kanal definieren und ihn standardmäßig für jede Zuweisung für eine Anzeige verwenden. Dies bietet eine Methode, sodass die umständliche Zeitplandefinition nicht wiederholt werden muss.

### Erstellen von Standardzuweisungsdetails für einen Kanal {#create-default}

1. Navigieren Sie zur Detailseite für den Kanal, den Sie konfigurieren möchten.
1. Suchen Sie die **Standardzuweisungsdetails** auf der Seite.

   ![image](/help/screens-cloud/assets/display/Assignment1.png)

1. Klicken **Festlegen von Standarddetails**.
1. Konfigurieren Sie die standardmäßigen Zuweisungsdetails, einschließlich Priorität, Start- und Enddaten sowie Wiederholungsmuster für den Kanal und klicken Sie auf **Zuweisen**.

   ![image](/help/screens-cloud/assets/display/Assignments2.png)

1. Beachten Sie, dass die Details der Zuweisung im Abschnitt **Standardzuweisungsdetails** tile:

   ![image](/help/screens-cloud/assets/display/Assignments3.png)

In dieser Kachel werden die folgenden Informationen angezeigt:
* Standardpriorität des Kanals in der Anzeige.
* Beginn und Ende der Aktivierung, wenn die Wiedergabe des Kanals geplant ist.
* Synthetische Ansicht der Wiederholung (stündlich/täglich/wöchentlich/monatlich/jährlich sowie Name der Wiederholung).

### Verwenden Sie beim Zuweisen zu einer Anzeige die standardmäßigen Zuweisungsdetails {#default-display}

Kanäle mit standardmäßigen Zuweisungsdetails können der Anzeige auf die gleiche Weise zugewiesen werden wie normale Kanäle. Die hinzugefügte Option nutzt die standardmäßigen Zuweisungsdetails, anstatt jedes Mal manuell benutzerdefinierte Kanäle zu definieren.

1. Navigieren Sie zur Seite mit den Anzeigedetails, der Sie den Kanal zuweisen möchten, und klicken Sie auf die **Kanal zuweisen**.
Wählen Sie alternativ die gewünschte Anzeige in der Lagerbestandsansicht aus und klicken Sie auf **Kanal zuweisen**.
1. Das Dialogfeld für die Kanalzuweisung wird geöffnet.

   ![image](/help/screens-cloud/assets/display/Assignments4.png)

1. Wählen Sie in der Kanalauswahl den gewünschten Kanal mit den standardmäßigen Zuweisungsdetails aus.
1. Beachten Sie, dass sich das Dialogfeld für die Kanalzuweisung ändert, sodass Sie die standardmäßigen Zuweisungsdetails auswählen oder benutzerdefinierte auswählen können:

   ![image](/help/screens-cloud/assets/display/Assignments5.png)

1. Klicken **Zuweisen** , um die Zuweisung abzuschließen, oder klicken Sie auf **Festlegen benutzerdefinierter Zuweisungsdetails** wenn Sie es vorziehen, die Standardwerte im Kontext dieser Anzeige durch andere Werte zu überschreiben.

   ![image](/help/screens-cloud/assets/display/Assignments6.png)

1. Beachten Sie die **Zugewiesene Kanäle** Die Kachel wird mit der neuen Zuweisung aktualisiert:

   ![image](/help/screens-cloud/assets/display/Assignments7.png)

1. Beachten Sie, dass die Kanäle ein anderes Symbol haben, je nachdem, ob sie benutzerdefinierte Zeitpläne (Uhrensymbol) verwenden oder die Standarddetails übernehmen (Weltuhrsymbol). Wenn Sie auf diese klicken, werden die Planungsdetails angezeigt.
1. Beachten Sie außerdem, dass die verfügbaren Aktionen für jeden Typ unterschiedlich sind.

   ![image](/help/screens-cloud/assets/display/Assignments8.png)

**Hinweis:** Eine Kanalzuweisung, die die standardmäßigen Zuweisungsdetails nutzt, kann im Kontext der Anzeige nicht bearbeitet werden.

* Wenn Sie sie in eine benutzerdefinierte Zuweisung ändern müssen, müssen Sie sie zuerst entfernen und dann erneut mit der **Festlegen benutzerdefinierter Zuweisungsdetails** -Option.
* Wenn Sie die Eigenschaften der Standardzuweisungsdetails ändern müssen, müssen Sie dies direkt auf der Seite mit den Kanaldetails tun.

### Entfernen von Standardzuweisungsdetails aus einem Kanal {#remove-display}

1. Navigieren Sie zur Detailseite für den Kanal, den Sie die standardmäßigen Zuweisungsdetails entfernen möchten.
1. Suchen Sie die **Standardzuweisungsdetails** Kachel auf der Seite
1. Klicken Sie auf **Standard entfernen**.

   ![image](/help/screens-cloud/assets/display/Assignments9.png)

1. Es wird ein Bestätigungsdialogfeld angezeigt, in dem die Details einer der folgenden Bedingungen entsprechen:
   **a.** Der Kanal wird in keiner Anzeige verwendet.

   ![image](/help/screens-cloud/assets/display/Assignments10.png)

**b.** Der Kanal wird in einer einzigen Anzeige verwendet.

![image](/help/screens-cloud/assets/display/Assignment11.png)

**c.** Der Kanal wird in mehreren Anzeigen verwendet.

![image](/help/screens-cloud/assets/display/Assignments12.png)

1. Klicken Sie auf *Entfernen* , um die Änderung zu validieren.

**Hinweis:** Wenn Sie die standardmäßigen Zuweisungsdetails aus einem Kanal entfernen, werden die entsprechenden Zuweisungen auf allen Anzeigen entfernt, die ihn verwendet haben.
Daher kann dies zu leeren Bildschirmen führen, wenn auf diesen Anzeigen kein alternativer Inhalt wiedergegeben werden soll.

## Wie geht es weiter {#whats-next}

Nachdem Sie jetzt einen AEM Screens-Kanal in Ihrem Projekt eingerichtet haben, müssen Sie Ihren Kanal veröffentlichen. Lesen Sie [Veröffentlichen von Kanälen in Screens as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/create-content/manage-publish.html?lang=de), bevor Sie Ihre Player über Screens Services Provider verwalten.
