---
Title: How to integrate Marketo Engage with AEM Forms using Form wizard?
Description: Learn how to integrate your Marketo Engage instance with AEM Forms using form wizard.
Keywords: How to connect a Marketo instance with form? , Connect a form to Marketo, Integrate a form with Marketo Engage, Integrate an Adaptive Form with a Marketo instance.
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
exl-id: 1fcba628-ffd8-416a-a8b5-76b35d4aabd4
source-git-commit: ce4646d8db1870f8ec85faddeb4e0a6a04f4c46e
workflow-type: tm+mt
source-wordcount: '1012'
ht-degree: 23%

---

# Integrieren eines adaptiven Formulars mit Marketo Engage

<span class="preview"> Die Funktion ist im Rahmen des Early-Adopter-Programms verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

![Workflow](/help/forms/assets/workflow-marketo-4.png)

Nachdem Sie die Cloud-Service-Konfiguration für die Integration von Marketo Engage mit AEM Forms erstellt haben, können Sie ein adaptives Formular für die Integration mit [Adobe Marketo Engage konfigurieren](https://experienceleague.adobe.com/de/docs/marketo/using/home).

Sie können Marketo Engage mithilfe des Formular-Assistenten mit einem adaptiven Formular verbinden, wodurch der Konfigurationsprozess vereinfacht wird, indem Sie durch die einzelnen Schritte geführt werden. Dazu gehört die Auswahl von Vorlagen, Stilen und Datenfeldern sowie die Einrichtung der Datenzuordnung, um sicherzustellen, dass Ihr Formular nach der Erstellung für die Kommunikation mit Marketo Engage bereit ist. Mithilfe des Formular-Assistenten können Sie das adaptive Formular auch so konfigurieren, dass Daten bei der Übermittlung direkt an Adobe Marketo Engage gesendet werden.

## Aspekte beim Konfigurieren der Marketo Engage-Datenquelle für Formulare

Beim Konfigurieren der Marketo Engage-Datenquelle für Formulare ist Folgendes zu berücksichtigen:

* Es ist nicht möglich, Edge Delivery Services-Formulare mit Marketo Engage zu verbinden.

## Voraussetzung für die Verbindung von Marketo Engage mit Formularen

Voraussetzung für die Verbindung von Marketo Engage mit Formularen:

* Erstellen Sie die [Cloud-Service-Konfiguration, um Marketo Engage mit Formularen zu integrieren](/help/forms/integrate-form-to-marketo-engage.md).

## Konfigurieren eines neuen adaptiven Formulars zur Integration mit Marketo Engage

>[!VIDEO](https://video.tv.adobe.com/v/3442867/marketo-aem-marketo-engage-engage-aem-forms)

>[!BEGINTABS]

>[!TAB Foundation-Komponente]

Um ein neues adaptives Formular zu konfigurieren, das auf Foundation-Komponenten basiert, die in Marketo Engage integriert werden sollen, führen Sie die folgenden Schritte aus:

1. Wählen Sie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.

   ![Forms und Dokumente auswählen](/help/forms/assets/select-forms.png)

1. Klicken Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptives Formular]**. Der Assistent zur Formularerstellung wird geöffnet.

   ![AF auswählen](/help/forms/assets/select-create-forms.png)

1. Wählen Sie auf der Registerkarte {**[!UICONTROL }Source eine Vorlage aus]**

   ![Vorlagen auswählen](/help/forms/assets/select-template-af1.png)

1. Wählen Sie in **[!UICONTROL Stil]** das Design aus.

   ![Design auswählen](/help/forms/assets/select-form-theme-af1.png)
1. Wählen Sie auf der **[!UICONTROL Daten]**-Registerkarte ein Datenmodell als **Marketo Engage** aus.
1. Wählen Sie **[!UICONTROL Cloud-Konfiguration]** aus der Dropdown-Liste im rechten Bereich des Bildschirms aus.
Standardmäßig werden alle Felder der zugehörigen Konfiguration angezeigt. Der Assistent bietet den Komfort, dass Sie mithilfe von Kontrollkästchen selektiv auswählen können, welche Felder in das adaptive Formular aufgenommen werden sollen.

   ![Datenmodell auswählen](/help/forms/assets/select-marketo-data-af1.png)

1. Wählen Sie auf **[!UICONTROL Registerkarte]**&#x200B;Übermittlung“ die Übermittlungsaktion **[!UICONTROL An Marketo übermitteln]**.

   Wenn Sie das Datenmodell als **Marketo Engage** auswählen, wird die Übermittlungsaktion **An Marketo übermitteln** automatisch ausgewählt. Sie können auf der Registerkarte **[!UICONTROL Übermittlung“ eine andere]** auswählen. Auf **[!UICONTROL Registerkarte]**&#x200B;Übermittlung“ werden alle verfügbaren Übermittlungsaktionen angezeigt.

   ![An Marketo Engage übermitteln](/help/forms/assets/select-marketo-engage.png)

1. Wählen Sie **[!UICONTROL Erstellen]**. Geben Sie Titel, Namen und Speicherort für das adaptive Formular an.

   ![Formular erstellen](/help/forms/assets/create-marketo-form.png)

1. Wählen Sie **[!UICONTROL Erstellen]** aus.

Das adaptive Formular ist jetzt für die Verbindung mit der Marketo Engage-Instanz konfiguriert. Alternativ können Sie auch die Eigenschaften des adaptiven Formulars bearbeiten, um die zugehörige Konfiguration zu ändern

>[!TAB Kernkomponente]

Um ein neues adaptives Formular zu konfigurieren, das auf Kernkomponenten basiert, die in Marketo Engage integriert werden sollen, führen Sie die folgenden Schritte aus:

1. Wählen Sie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.

   ![Forms und Dokumente auswählen](/help/forms/assets/select-forms.png)

1. Klicken Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptives Formular]**. Der Assistent zur Formularerstellung wird geöffnet.

   ![AF auswählen](/help/forms/assets/select-create-forms.png)

1. Wählen Sie auf der Registerkarte {**[!UICONTROL }Source eine Vorlage aus]**

   ![Vorlagen auswählen](/help/forms/assets/select-template.png)

1. Wählen Sie in **[!UICONTROL Stil]** das Design aus.

   ![Design auswählen](/help/forms/assets/select-form-theme.png)


1. Wählen Sie auf der **[!UICONTROL Daten]**-Registerkarte ein Datenmodell als **Marketo Engage** aus.

1. Wählen Sie **[!UICONTROL Cloud-Konfiguration]** aus der Dropdown-Liste im rechten Bereich des Bildschirms aus.
Standardmäßig werden alle Felder der zugehörigen Konfiguration angezeigt. Der Assistent bietet den Komfort, dass Sie mithilfe von Kontrollkästchen selektiv auswählen können, welche Felder in das adaptive Formular aufgenommen werden sollen.

   ![Datenmodell auswählen](/help/forms/assets/select-marketo-data.png)

1. Wählen Sie auf **[!UICONTROL Registerkarte]**&#x200B;Übermittlung“ die Übermittlungsaktion **[!UICONTROL An Marketo übermitteln]**.

   Wenn Sie das Datenmodell als **Marketo Engage** auswählen, wird die Übermittlungsaktion **An Marketo übermitteln** automatisch ausgewählt. Sie können auf der Registerkarte **[!UICONTROL Übermittlung“ eine andere]** auswählen. Auf **[!UICONTROL Registerkarte]**&#x200B;Übermittlung“ werden alle verfügbaren Übermittlungsaktionen angezeigt.

   ![An Marketo Engage übermitteln](/help/forms/assets/select-marketo-engage.png)

1. Wählen Sie **[!UICONTROL Erstellen]**. Geben Sie Titel, Namen und Speicherort für das adaptive Formular an.

   ![Formular erstellen](/help/forms/assets/create-marketo-form.png)

1. Wählen Sie **[!UICONTROL Erstellen]** aus.

Das adaptive Formular ist jetzt für die Verbindung mit der Marketo Engage-Instanz konfiguriert. Alternativ können Sie auch die Eigenschaften des adaptiven Formulars bearbeiten, um die zugehörige Konfiguration zu ändern.

>[!TAB Universeller Editor]

Führen Sie die folgenden Schritte aus, um ein neues adaptives Formular, das im universellen Editor erstellt wurde, für die Integration mit Marketo Engage zu konfigurieren:

1. Wählen Sie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.

   ![Forms und Dokumente auswählen](/help/forms/assets/select-forms.png)

1. Klicken Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptives Formular]**. Der Assistent zur Formularerstellung wird geöffnet.

   ![AF auswählen](/help/forms/assets/select-create-forms.png)

1. Wählen Sie auf der Registerkarte {**[!UICONTROL }Source eine Vorlage aus]**

   ![Vorlagen auswählen](/help/forms/assets/select-template-ue.png)

1. Wählen Sie auf der **[!UICONTROL Daten]**-Registerkarte ein Datenmodell als **Marketo Engage** aus.

1. Wählen Sie **[!UICONTROL Cloud-Konfiguration]** aus der Dropdown-Liste im rechten Bereich des Bildschirms aus.
Standardmäßig werden alle Felder der zugehörigen Konfiguration angezeigt. Der Assistent bietet den Komfort, dass Sie mithilfe von Kontrollkästchen selektiv auswählen können, welche Felder in das adaptive Formular aufgenommen werden sollen.

   ![Datenmodell auswählen](/help/forms/assets/select-marketo-data-ue.png)

1. Wählen Sie auf **[!UICONTROL Registerkarte]**&#x200B;Übermittlung“ die Übermittlungsaktion **[!UICONTROL An Marketo übermitteln]**.

   Wenn Sie das Datenmodell als **Marketo Engage** auswählen, wird die Übermittlungsaktion **An Marketo übermitteln** automatisch ausgewählt. Sie können auf der Registerkarte **[!UICONTROL Übermittlung“ eine andere]** auswählen. Auf **[!UICONTROL Registerkarte]**&#x200B;Übermittlung“ werden alle verfügbaren Übermittlungsaktionen angezeigt.

   ![An Marketo Engage übermitteln](/help/forms/assets/select-marketo-engage-ue.png)

1. Wählen Sie **[!UICONTROL Erstellen]**. Geben Sie Titel, Namen und Speicherort für das adaptive Formular an.

   ![Formular erstellen](/help/forms/assets/create-marketo-form.png)

1. Wählen Sie **[!UICONTROL Erstellen]** aus.

Das adaptive Formular ist jetzt für die Verbindung mit der Marketo Engage-Instanz konfiguriert. Alternativ können Sie auch die Eigenschaften des adaptiven Formulars bearbeiten, um die zugehörige Konfiguration zu ändern.

>[!ENDTABS]

## Häufig gestellte Fragen (FAQs)

**F: Kann man die Übermittlungsaktion für Formulare ändern, die für die Verbindung mit dem Marketo Engage-Schema konfiguriert sind?**
**A:** Standardmäßig ist die Aktion **An Marketo senden** ausgewählt, wenn ein Formular für die Verbindung mit dem Marketo Engage-Schema konfiguriert ist. Sie können jedoch bei Bedarf die Übermittlungsaktion für die Formulare ändern.


**F: Was passiert, wenn Sie den Connector des Formulars ändern?**\
**A:** Wenn Sie den Connector des Formulars ändern, werden die vorhandenen Bindungen ungültig.

**F: Welche drei Vorgänge sind im Aufruf-Service des Regeleditors für Formulare verfügbar, die in Marketo Engage integriert sind?**\
**A:** Die drei folgenden vorkonfigurierten Vorgänge sind im **Aufruf-Service** für Formulare verfügbar, die in Marketo Engage integriert sind:

* Lead synchronisieren
* Lead nach ID abrufen
* Lead nach Filtertyp abrufen

## Nächster Schritt

Sie können ein adaptives Formular auch mit der [Munchkin-](https://experienceleague.adobe.com/de/docs/marketo/using/product-docs/administration/setup/munchkin) verbinden, um die Anzahl der Besuche, Klicks und Formularübermittlungen zu verfolgen.

## Verwandte Artikel

{{af-submit-action}}

## Siehe auch

{{marketo-engage-see-also}}
