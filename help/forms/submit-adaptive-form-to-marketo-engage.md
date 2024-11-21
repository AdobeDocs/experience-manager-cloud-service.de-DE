---
Title: How to configure submit action to Marketo Engage for forms?
Description: Learn how to configure the submit action of Adaptive Form to send data to Marketo Engage.
Keywords: Submit data to Marketo engage, Configure submit action as Submit to Marketo Engage
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
source-git-commit: 681c194f997ab66f93beedad4eea273614e6797d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 18%

---


# Konfigurieren der Sendeaktion auf Marketo Engage für vorhandene Formulare

<span class="preview"> Die Funktion ist im Rahmen des Early-Adopter-Programms verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

![Arbeitsablauf](/help/forms/assets/workflow-marketo-3.png)

Der adaptive Forms-Editor bietet die Übermittlungsaktion **An Marketo Engage übermitteln** , um adaptive Forms-Daten zur Verarbeitung an Adobe Marketo Engage zu senden. Sie können ein vorhandenes adaptives Formular so konfigurieren, dass bei der Übermittlung Daten an [Adobe Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home) gesendet werden.

Es stehen verschiedene vordefinierte Übermittlungsaktionen zur Verarbeitung von Formularübermittlungen zur Verfügung. Weitere Informationen zu diesen Optionen finden Sie im Artikel [Übermittlungsaktion für adaptive Formulare](/help/forms/configure-submit-actions-core-components.md).

## Überlegungen beim Konfigurieren der Sendeaktion für das Formular an Marketo Engage

* Stellen Sie sicher, dass das adaptive Formular mit der Marketo Engage-Datenquelle konfiguriert ist, um Daten beim Senden des Formulars an Marketo Engage zu senden. Sie können die Sendeaktion jedoch in Alternativen ändern, z. B. &quot;**An OneDrive übermitteln**&quot;oder &quot;**Senden an SharePoint**&quot;, selbst wenn das Formular mit dem Marketo Engage-Datenschema konfiguriert ist.

## Voraussetzung für die Konfiguration der Sendeaktion an Marketo Engage für ein vorhandenes Formular

Voraussetzung für die Konfiguration der Sendeaktion an Marketo Engage:

* Konfigurieren Sie die [Marketo Engage-Datenquelle für das adaptive Formular](/help/forms/use-marketo-engage-data-source-in-form.md) und binden Sie die Formularelemente an Marketo Engage-Felder.

## Wie konfiguriere ich Übermittlungsaktionen an Marketo Engage für bestehende Formulare?

Sie können die Sendeaktion eines adaptiven Formulars konfigurieren, um Daten an Adobe Marketo Engage zu senden. Führen Sie die folgenden Schritte aus, um die Sendeaktion an Marketo Engage zu konfigurieren:

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Guide-Container]**.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg). Das Dialogfeld Container für adaptive Formulare zum Konfigurieren der Sendeaktion wird geöffnet.
1. Öffnen Sie die Registerkarte **[!UICONTROL Übermittlung]** und wählen Sie eine Sendeaktion als **An Marketo Engage übermitteln** aus.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

![Marketo-Übermittlungsaktion](/help/forms/assets/marketo-engage-submit-action.png){width=50%, height=50%}


Nachdem Sie die Sendeaktion für das adaptive Formular als **An Marketo Engage übermitteln** konfiguriert haben, können Sie Daten zur Verarbeitung an Adobe Marketo Engage senden. Die Daten können verwendet werden, um Marketingkampagnen zu analysieren und zu optimieren, Folgenachrichten zu automatisieren und Trigger-Workflows basierend auf Formularübermittlungen zu erstellen.

## Häufig gestellte Fragen (FAQ)

**Q: Können Sie die Sendeaktion für Formulare ändern, die für die Verbindung mit dem Marketo Engage-Schema konfiguriert sind?**
**A:** Standardmäßig wird die Aktion **An Marketo übermitteln** ausgewählt, wenn ein Formular für die Verbindung mit dem Marketo Engage-Schema konfiguriert ist. Sie können die Sendeaktion für die Formulare jedoch bei Bedarf ändern.

## Nächster Schritt

Sie können ein adaptives Formular auch mit der [Munchkin-Bibliothek](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/setup/munchkin) verbinden, um die Anzahl der Besuche, Klicks und Formularübermittlungen zu verfolgen.

## Verwandte Artikel

{{af-submit-action}}

## Siehe auch

{{marketo-engage-see-also}}
