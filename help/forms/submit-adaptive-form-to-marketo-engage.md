---
Title: How to configure submit action to Marketo Engage for forms?
Description: Learn how to configure the submit action of Adaptive Form to send data to Marketo Engage.
Keywords: Submit data to Marketo engage, Configure submit action as Submit to Marketo Engage
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
exl-id: 0683564b-1ac4-42b4-bc08-101c4fdef286
source-git-commit: e46c5afac945620cc44e9064956848acecc786bf
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 20%

---

# Konfigurieren der Aktion „An Marketo Engage senden“ für vorhandene Formulare

<span class="preview"> Die Funktion ist im Rahmen des Early-Adopter-Programms verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

![Arbeitsablauf](/help/forms/assets/workflow-marketo-3.png)

Der Editor für adaptive Forms bietet die Übermittlungsaktion **An Marketo Engage übermitteln** um adaptive Forms-Daten zur Verarbeitung an Adobe Marketo Engage zu senden. Sie können ein vorhandenes adaptives Formular so konfigurieren, dass beim Senden Daten an [Adobe Marketo Engage](https://experienceleague.adobe.com/de/docs/marketo/using/home) gesendet werden.

Verschiedene vordefinierte Übermittlungsaktionen für die Verarbeitung von Formularübermittlungen sind verfügbar. Weitere Informationen zu diesen Optionen finden Sie im Artikel [Übermittlungsaktion für adaptive Formulare](/help/forms/configure-submit-actions-core-components.md).

## Überlegungen beim Konfigurieren der Übermittlungsaktion für das Formular an Marketo Engage

* Stellen Sie sicher, dass das adaptive Formular mit der Marketo Engage-Datenquelle konfiguriert ist, um Daten bei der Formularübermittlung an Marketo Engage zu senden. Sie können die Übermittlungsaktion jedoch in Alternativen ändern, z. B. **An OneDrive übermitteln** oder **An SharePoint übermitteln**, auch wenn das Formular mit dem Marketo Engage-Datenschema konfiguriert ist.

## Voraussetzung für die Konfiguration der Übermittlungsaktion für ein bestehendes Formular zum Marketo Engage

Voraussetzung für die Konfiguration der Übermittlungsaktion für Marketo Engage:

* Konfigurieren Sie die [Marketo Engage-Datenquelle für das adaptive Formular](/help/forms/use-marketo-engage-data-source-in-form.md) und binden Sie die Formularelemente mit Marketo Engage-Feldern.

## Konfigurieren der Übermittlungsaktion für bestehende Formulare für Marketo Engage

>[!VIDEO](https://video.tv.adobe.com/v/3442866/submit-action-marketo-engage-marketo-aem-aem-forms-engage)

Sie können die Übermittlungsaktion eines adaptiven Formulars so konfigurieren, dass Daten an Adobe Marketo Engage gesendet werden. Gehen Sie wie folgt vor, um die Übermittlungsaktion für Marketo Engage zu konfigurieren:

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
2. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Guide-Container]**.
3. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg). Das Dialogfeld Container für adaptive Formulare zum Konfigurieren der Übermittlungsaktion wird geöffnet.
4. Öffnen Sie die **[!UICONTROL Übermittlung]** und wählen Sie eine Sendeaktion als **An Marketo Engage senden** aus.
5. Klicken Sie auf **[!UICONTROL Fertig]**.

![Marketo-Übermittlungsaktion](/help/forms/assets/marketo-engage-submit-action.png){width=50%, height=50%}


Nachdem Sie die Übermittlungsaktion für das adaptive Formular als &quot;**an Marketo Engage senden** konfiguriert haben, können Sie Daten zur Verarbeitung an Adobe Marketo Engage senden. Die Daten können verwendet werden, um Marketing-Kampagnen zu analysieren und zu optimieren, Follow-up-E-Mails zu automatisieren und Trigger-Workflows auf der Grundlage von Formularübermittlungen zu erstellen.

## Häufig gestellte Fragen (FAQ)

**F: Kann man die Übermittlungsaktion für Formulare ändern, die für die Verbindung mit dem Marketo Engage-Schema konfiguriert sind?**
**A:** Standardmäßig ist die Aktion **An Marketo senden** ausgewählt, wenn ein Formular für die Verbindung mit dem Marketo Engage-Schema konfiguriert ist. Sie können jedoch bei Bedarf die Übermittlungsaktion für die Formulare ändern.

## Nächster Schritt

Sie können ein adaptives Formular auch mit der [Munchkin-](https://experienceleague.adobe.com/de/docs/marketo/using/product-docs/administration/setup/munchkin) verbinden, um die Anzahl der Besuche, Klicks und Formularübermittlungen zu verfolgen.

## Verwandte Artikel

{{af-submit-action}}

## Siehe auch

{{marketo-engage-see-also}}
