---
Title: How to integrate Marketo Engage with AEM Forms using Form wizard?
Description: Learn how to integrate your Marketo Engage instance with AEM Forms using form wizard.
Keywords: How to connect a Marketo instance with form? , Connect a form to Marketo, Integrate a form with Marketo Engage, Integrate an Adaptive Form with a Marketo instance.
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
source-git-commit: 681c194f997ab66f93beedad4eea273614e6797d
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 9%

---


# Konfigurieren eines neuen Formulars zur Integration mit Marketo Engage

<span class="preview"> Die Funktion ist im Rahmen des Early-Adopter-Programms verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

![Arbeitsablauf](/help/forms/assets/workflow-marketo-4.png)

Nachdem Sie die Cloud-Service-Konfiguration zur Integration von Marketo Engage in AEM Forms erstellt haben, können Sie ein adaptives Formular konfigurieren, um es in [Adobe Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home) zu integrieren.

Sie können Marketo Engage mit dem Formularassistenten mit einem adaptiven Formular verbinden, was den Konfigurationsprozess vereinfacht, indem Sie die einzelnen Schritte durchlaufen. Dazu gehören die Auswahl von Vorlagen, Stilen und Datenfeldern sowie die Einrichtung des Daten-Mappings, um sicherzustellen, dass Ihr Formular nach seiner Erstellung für die Kommunikation mit der Marketo Engage bereit ist. Mit dem Formularassistenten können Sie das adaptive Formular auch so konfigurieren, dass Daten bei der Übermittlung direkt an Adobe Marketo Engage gesendet werden.

## Überlegungen zum Konfigurieren der Marketo Engage-Datenquelle für Formulare

Beachten Sie beim Konfigurieren der Marketo Engage-Datenquelle für Formulare Folgendes:

* Es ist nicht möglich, Edge Delivery Services Forms mit Marketo Engage zu verbinden.

## Voraussetzung für die Verbindung von Marketo Engage mit Formularen

Voraussetzung für die Verbindung von Marketo Engage mit Formularen:

* Erstellen Sie die [Cloud-Service-Konfiguration zur Integration von Marketo Engage in Formulare](/help/forms/integrate-form-to-marketo-engage.md).

## Wie konfiguriere ich ein neues adaptives Formular für die Integration mit Marketo Engage?

Um das neue adaptive Formular für die Integration mit Marketo Engage zu konfigurieren, führen Sie die folgenden Schritte aus:

1. Wählen Sie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.

   ![Forms und Dokumente auswählen](/help/forms/assets/select-forms.png)

1. Klicken Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptives Formular]**. Der Formularerstellungs-Assistent wird geöffnet.

   ![Wählen Sie AF](/help/forms/assets/select-create-forms.png)

1. Wählen Sie auf der Registerkarte **[!UICONTROL Source]** eine Vorlage aus.

   ![Vorlagen auswählen](/help/forms/assets/select-template.png)

1. Wählen Sie im Bereich **[!UICONTROL Stil]** das Design aus.

   ![Design auswählen](/help/forms/assets/select-form-theme.png)


1. Wählen Sie auf der Registerkarte **[!UICONTROL Daten]** ein Datenmodell als **Marketo Engage** aus.

1. Wählen Sie die **[!UICONTROL Cloud-Konfiguration]** aus der Dropdown-Liste aus, die im rechten Bereich des Bildschirms angezeigt wird.
Standardmäßig werden alle Felder der zugehörigen Konfiguration angezeigt. Der Assistent bietet Ihnen die Möglichkeit, mithilfe von Kontrollkästchen selektiv zu wählen, welche Felder im adaptiven Formular enthalten sein sollen.

   ![Datenmodell auswählen](/help/forms/assets/select-marketo-data.png)

1. Wählen Sie auf der Registerkarte **[!UICONTROL Übermittlung]** die Sendeaktion als **[!UICONTROL An Marketo übermitteln]** aus.

   Wenn Sie das Datenmodell als **Marketo Engage** auswählen, wird die Sendeaktion als **An Marketo übermitteln** automatisch ausgewählt. Sie können auf der Registerkarte **[!UICONTROL Übermittlung]** eine andere Sendeaktion auswählen. Auf der Registerkarte **[!UICONTROL Übermittlung]** werden alle verfügbaren Sendeaktionen angezeigt.

   ![Senden an Marketo engage](/help/forms/assets/select-marketo-engage.png)

1. Wählen Sie **[!UICONTROL Erstellen]**. Geben Sie Titel, Namen und Speicherort für das adaptive Formular an.

   ![Formular erstellen](/help/forms/assets/create-marketo-form.png)

1. Wählen Sie **[!UICONTROL Erstellen]** aus.

Das adaptive Formular ist jetzt für die Verbindung mit der Marketo Engage-Instanz konfiguriert. Alternativ können Sie auch die Eigenschaften des adaptiven Formulars bearbeiten, um die zugehörige Konfiguration zu ändern.

## Häufig gestellte Fragen (FAQ)

**Q: Können Sie die Sendeaktion für Formulare ändern, die für die Verbindung mit dem Marketo Engage-Schema konfiguriert sind?**
**A:** Standardmäßig wird die Aktion **An Marketo übermitteln** ausgewählt, wenn ein Formular für die Verbindung mit dem Marketo Engage-Schema konfiguriert ist. Sie können die Sendeaktion für die Formulare jedoch bei Bedarf ändern.


**Q: Was passiert, wenn Sie den Connector des Formulars ändern?**\
**A:** Wenn Sie den Connector des Formulars ändern, werden die vorhandenen Bindungen ungültig.

**Q: Welche drei Vorgänge sind im Aufrufdienst des Regeleditors für in Marketo Engage integrierte Formulare verfügbar?**\
**A:** Die drei nativen Vorgänge, die im **Aufrufdienst** für mit Marketo Engage integrierte Formulare verfügbar sind, sind:
* Synchronisierungsleitung
* Lead nach ID abrufen
* Lead nach Filtertyp abrufen

## Nächster Schritt

Sie können ein adaptives Formular auch mit der [Munchkin-Bibliothek](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/setup/munchkin) verbinden, um die Anzahl der Besuche, Klicks und Formularübermittlungen zu verfolgen.

## Verwandte Artikel

{{af-submit-action}}

## Siehe auch

{{marketo-engage-see-also}}
