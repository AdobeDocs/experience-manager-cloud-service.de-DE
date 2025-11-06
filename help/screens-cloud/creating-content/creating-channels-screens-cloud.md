---
title: Erstellen und Verwalten von Kanälen in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie in Screens as a Cloud Service Kanäle erstellen und verwalten.
exl-id: 3b0bae7a-4a45-485a-ab04-604510ff6578
feature: Authoring Screens
role: Admin, Developer, User
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1102'
ht-degree: 100%

---

# Erstellen und Verwalten eines Kanals in Screens as a Cloud Service {#creating-channels-screens-cloud}

Nachdem Sie ein AEM Screens-Projekt erstellt haben, müssen Sie Kanäle erstellen.
***Kanäle*** zeigen eine Sequenz von Inhalten (Bilder und Videos), eine Website oder eine Einzelseiten-Webanwendung an.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie in Screens Content Provider Kanäle für Ihr AEM Screens-Projekt erstellen und verwalten. Nach dem Lesen sollten Sie Folgendes können:

* verstehen, wie man Kanäle für Screens Content Provider erstellt
* Inhalte in Ihren Kanälen verwalten und bearbeiten
* den Zeitplan für die Zuweisung und Aktivierung Ihrer Kanäle in [Screens Service Provider](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/navigating-to-screens-services-provider.html?lang=de) verwalten

## Schritte zum Erstellen eines neuen Sequenzkanals in Screens as a Cloud Service {#create-new-channel}

>[!NOTE]
>**Voraussetzungen**
>Bevor Sie mit diesem Abschnitt des Handbuchs beginnen, lesen Sie [Erstellen und Verwalten von Projekten in Screens as a Cloud Service](/help/screens-cloud/creating-content/creating-projects-screens-cloud.md).

Gehen Sie wie folgt vor, um einen Sequenzkanal in Screens as a Cloud Service zu erstellen:

1. Gehen Sie zu Screens Content Provider.

1. Gehen Sie zu Ihrem AEM Screens-Projekt, z. B. *FirstDigitalExperience*.

1. Wählen Sie den Ordner **Kanäle** in Ihrem Projekt aus, z. B. **ErstesDigitalesErlebnis** > **Kanäle**, und klicken Sie in der Aktionsleiste auf **Erstellen**.

   ![channel-create1](/help/screens-cloud/assets/create-content/channel-create1.png)

1. Wählen Sie im Assistenten **Erstellen** die Vorlage aus, z. B. **Sequenzkanal**, und klicken Sie auf **Weiter**.

   ![channel-create2](/help/screens-cloud/assets/create-content/channel-create2.png)

   >[!NOTE]
   > Der Assistent **Erstellen** bietet beim Erstellen eines Kanals verschiedene Arten von Vorlagen. Siehe [Verfügbare Vorlagen](#available-templates) im Erstellungsassistenten für weitere Details.

1. Geben Sie den Namen Ihres Sequenzkanals ein, z. B. **SchleifeKanalEins**, und klicken Sie auf **Erstellen**.

   ![channel-create3](/help/screens-cloud/assets/create-content/channel-create3.png)

   Im Ordner „Kanäle“ in Ihrem AEM Screens-Projekt wird nun **LoopingChannelOne** angezeigt.

   Nachdem Sie den Kanal erstellt haben, können Sie nun Inhalte zu Ihrem Kanal hinzufügen. Unter [Hinzufügen von Inhalten zu Kanälen](#add-content) erfahren Sie, wie Sie Assets (Bilder/Videos) zu Ihrem Kanal hinzufügen.

## Verwalten eines Kanals {#managing-channels}

Sie können Änderungen vornehmen, Eigenschaften und Dashboard anzeigen sowie einen Kanal kopieren, in der Vorschau anzeigen und löschen.

Gehen Sie von Ihrem Projekt zum Kanal und wählen Sie den Kanal aus, wie in der Abbildung unten dargestellt. Sie können jetzt Optionen auswählen, z. B. den Kanal bearbeiten, Eigenschaften anzeigen, Inhalte in der Vorschau anzeigen, Veröffentlichung verwalten oder den Kanal aus der Aktionsleiste löschen.

![channelprop1](/help/screens-cloud/assets/create-content/channelprop1.png)

### Hinzufügen von Inhalten zu Kanälen {#add-content}

Um Inhalt in einem Kanal hinzuzufügen oder zu bearbeiten, gehen Sie wie folgt vor:

1. Klicken Sie auf den Kanal, den Sie bearbeiten möchten (wie in der untenstehenden Abbildung gezeigt). Klicken Sie oben links in der Aktionsleiste auf **Bearbeiten**, um den Editor zu öffnen.

   ![edit-channel1](/help/screens-cloud/assets/create-content/edit-channel1.png)

1. Mit dem Editor können Sie Assets/Komponenten zu Ihrem Kanal hinzufügen, die veröffentlicht werden sollen.

1. Ziehen Sie die Assets per Drag-and-Drop aus dem linken Bereich und fügen Sie sie zum Editor hinzu.

   ![edit-channel2](/help/screens-cloud/assets/create-content/edit-channel2.png)

   >[!NOTE]
   >Klicken Sie auf **Vorschau**, um die Inhalte Ihres Kanals in einer Vorschau anzuzeigen.
   >![Bearbeiten – Kanalvorschau](/help/screens-cloud/assets/create-content/edit-channelpreview.png)

## Verfügbare Vorlagen im Assistenten „Erstellen“. {#available-templates}

Die folgenden Vorlagen sind bei Verwendung des Assistenten zum **Erstellen** eines Kanals verfügbar:

| Verfügbare Vorlagen | Beschreibung |
|--- |--- |
| Kanal-Ordner | Ermöglicht die Erstellung eines Ordners zum Speichern von Kanalsammlungen. |
| Sequenzkanal | Ermöglicht die Erstellung eines Kanals zum sequenziellen Wiedergeben der Komponenten (einzeln in einer Diashow). |
| Splitscreen-Kanal mit L-Balken links oder rechts | Ermöglicht es den Autoren von Inhalten, verschiedene Arten von Assets in entsprechend großen Bereichen anzuzeigen. |

## Verwenden von Standardzuweisungsdetails für Kanäle {#default-channels}

Mit dieser Funktion können Sie einen standardmäßigen Aktivierungsplan für einen Kanal definieren und ihn standardmäßig für jede Zuweisung für ein Display verwenden. Mit dieser Methode muss die umständliche Zeitplandefinition nicht wiederholt werden.

1. Navigieren Sie zu [Screens Services Provider](https://experience.adobe.com/screens).

### Erstellen von Standardzuweisungsdetails für einen Kanal {#create-default}

1. Navigieren Sie zur Detailseite für den Kanal, den Sie konfigurieren möchten.
1. Suchen Sie die Kachel **Standardzuweisungsdetails** auf der Seite.

   ![image](/help/screens-cloud/assets/display/Assignment1.png)

1. Klicken Sie auf **Standarddetails festlegen**.
1. Konfigurieren Sie die standardmäßigen Zuweisungsdetails, einschließlich Priorität, Start/Enddaten und Wiederholungsmuster, für den Kanal und klicken Sie auf **Zuweisen**.

   ![image](/help/screens-cloud/assets/display/Assignments2.png)

1. Beachten Sie, dass die Details der Zuweisung auf der Kachel **Standardzuweisungsdetails** angezeigt werden:

   ![image](/help/screens-cloud/assets/display/Assignments3.png)

Auf dieser Kachel werden die folgenden Informationen angezeigt:

* Standardpriorität des Kanals im Display.
* Start- und Enddatum der Aktivierung für die Wiedergabe des Kanals.
* Synthetische Ansicht des Intervall (stündlich/täglich/wöchentlich/monatlich/jährlich und Name des Intervall).

### Verwenden der Standardzuweisungsdetails beim Zuweisen zu einem Display {#default-display}

Kanäle mit Standardzuweisungsdetails können dem Display auf die gleiche Weise zugewiesen werden wie normale Kanäle. Es besteht die zusätzliche Option, die Standardzuweisungsdetails zu verwenden, statt jedes Mal manuell benutzerdefinierte Zuweisungsdetails zu definieren.

1. Navigieren Sie zur Detailseite des Displays, dem Sie den Kanal zuweisen möchten, und klicken Sie auf **Kanal zuweisen**.
Wählen Sie alternativ die gewünschte Anzeige in der [Bestandsansicht](https://experience.adobe.com/screens/displays) aus und klicken Sie auf **Kanal zuweisen**.
1. Daraufhin wird das Dialogfeld für die Kanalzuweisung geöffnet.

   ![image](/help/screens-cloud/assets/display/Assignments4.png)

1. Wählen Sie in der Kanalauswahl den gewünschten Kanal mit den Standardzuweisungsdetails aus.
1. Beachten Sie, dass sich das Dialogfeld für die Kanalzuweisung ändert, sodass Sie die Standardzuweisungsdetails oder benutzerdefinierte Zuweisungsdetails auswählen können:

   ![image](/help/screens-cloud/assets/display/Assignments5.png)

1. Klicken Sie auf **Zuweisen**, um die Zuweisung abzuschließen, oder klicken Sie auf **Benutzerdefinierte Zuweisungsdetails festlegen**, wenn Sie es vorziehen, die Standardwerte im Kontext dieses Displays durch andere Werte zu überschreiben.

   ![image](/help/screens-cloud/assets/display/Assignments6.png)

1. Beachten Sie, dass die Kachel **Zugewiesene Kanäle** mit der neuen Zuweisung aktualisiert wird:

   ![image](/help/screens-cloud/assets/display/Assignments7.png)

1. Beachten Sie, dass die Kanäle ein anderes Symbol haben, je nachdem, ob sie benutzerdefinierte Zeitpläne (Uhrensymbol) verwenden oder die Standarddetails übernehmen (Weltuhrsymbol). Wenn Sie auf darauf klicken, werden die Zeitplandetails angezeigt.
1. Beachten Sie außerdem, dass die verfügbaren Aktionen für jeden Typ unterschiedlich sind.

   ![image](/help/screens-cloud/assets/display/Assignments8.png)

**Hinweis:** Eine Kanalzuweisung, die die standardmäßigen Zuweisungsdetails nutzt, kann im Kontext des Displays nicht bearbeitet werden.

* Wenn Sie sie in eine benutzerdefinierte Zuweisung ändern müssen, müssen Sie sie zuerst entfernen und dann erneut mit der Option **Benutzerdefinierte Zuweisungsdetails festlegen** hinzufügen.
* Wenn Sie die Eigenschaften der Standardzuweisungsdetails ändern müssen, tun Sie dies direkt auf der Seite mit den Kanaldetails.

### Entfernen von Standardzuweisungsdetails aus einem Kanal {#remove-display}

1. Navigieren Sie zur Detailseite für den Kanal, von dem Sie die Standardzuweisungsdetails entfernen möchten.
1. Suchen Sie die Kachel **Standardzuweisungsdetails** auf der Seite.
1. Klicken Sie auf **Standard entfernen**.

   ![image](/help/screens-cloud/assets/display/Assignments9.png)

1. Es wird ein Bestätigungsdialogfeld angezeigt und die Details entsprechen einer der folgenden Bedingungen:
   **a.** Der Kanal wird in keinem Display verwendet.

   ![image](/help/screens-cloud/assets/display/Assignments10.png)

**b.** Der Kanal wird in einem einzigen Display verwendet.

![image](/help/screens-cloud/assets/display/Assignment11.png)

**c.** Der Kanal wird in mehreren Displays verwendet.

![image](/help/screens-cloud/assets/display/Assignments12.png)

1. Klicken Sie auf *Entfernen*, um die Änderung zu validieren.

**Hinweis:** Wenn Sie die Standardzuweisungsdetails aus einem Kanal entfernen, werden die entsprechenden Zuweisungen auf allen Displays entfernt, die sie verwendet haben.
Dies kann zu leeren Bildschirmen führen, wenn es für die Wiedergabe auf diesen Displays keinen alternativen Inhalt gibt.

## Wie geht es weiter {#whats-next}

Nachdem Sie jetzt einen AEM Screens-Kanal in Ihrem Projekt eingerichtet haben, müssen Sie Ihren Kanal veröffentlichen. Lesen Sie [Veröffentlichen von Kanälen in Screens as a Cloud Service](manage-publish.md), bevor Sie Ihre Player über Screens Services Provider verwalten.
