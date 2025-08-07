---
Title: How to configure submit action to Marketo Engage for forms?
Description: Learn how to configure the submit action of Adaptive Form to send data to Marketo Engage.
Keywords: Submit data to Marketo engage, Configure submit action as Submit to Marketo Engage
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
exl-id: 0683564b-1ac4-42b4-bc08-101c4fdef286
source-git-commit: dabf8029577c5fb6bb5eebdbf10d77f3d4d95a5d
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 15%

---

# Konfigurieren der Aktion „An Marketo Engage senden“ für vorhandene Formulare

<span class="preview"> Die Funktion ist im Rahmen des Early-Adopter-Programms verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

![Workflow](/help/forms/assets/workflow-marketo-3.png)

Der Editor für adaptive Forms bietet die Übermittlungsaktion **An Marketo Engage übermitteln** um Daten für adaptive Forms zur Verarbeitung an Adobe Marketo Engage zu senden. Sie können ein vorhandenes adaptives Formular so konfigurieren, dass beim Senden Daten an [Adobe Marketo Engage](https://experienceleague.adobe.com/de/docs/marketo/using/home) gesendet werden.

Verschiedene vordefinierte Übermittlungsaktionen für die Verarbeitung von Formularübermittlungen sind verfügbar. Weitere Informationen zu diesen Optionen finden Sie im Artikel [Übermittlungsaktion für adaptive Formulare](/help/forms/configure-submit-actions-core-components.md).

## Überlegungen beim Konfigurieren der Übermittlungsaktion für ein Formular an Marketo Engage

* Stellen Sie sicher, dass das adaptive Formular mit der Marketo Engage-Datenquelle konfiguriert ist, um Daten bei der Formularübermittlung an Marketo Engage zu senden. Sie können die Übermittlungsaktion jedoch in Alternativen ändern, z. B. **An OneDrive übermitteln** oder **An SharePoint übermitteln**, auch wenn das Formular mit dem Marketo Engage-Datenschema konfiguriert ist.

## Voraussetzung für die Konfiguration der Übermittlungsaktion an Marketo Engage für ein bestehendes Formular

Voraussetzung für die Konfiguration der Übermittlungsaktion an Marketo Engage:

* Konfigurieren Sie die [Marketo Engage-Datenquelle für adaptive Formulare](/help/forms/use-marketo-engage-data-source-in-form.md) und binden Sie die Formularelemente an Marketo Engage-Felder.

## Konfigurieren der Übermittlungsaktion an Marketo Engage für vorhandene Formulare

>[!VIDEO](https://video.tv.adobe.com/v/3442866/submit-action-marketo-engage-marketo-aem-aem-forms-engage)

<span> Dieses Video gilt nur für Kernkomponenten. Informationen zu UE/Foundation-Komponenten finden Sie im Artikel</span>


>[!BEGINTABS]

>[!TAB Foundation-Komponente]

Sie können die Übermittlungsaktion eines adaptiven Formulars auf der Grundlage von Foundation-Komponenten konfigurieren, um Daten an Adobe Marketo Engage zu übermitteln. Um die Übermittlungsaktion an Marketo Engage zu konfigurieren, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Ihrer [!DNL Experience Manager Forms]-Autoreninstanz an.
1. Öffnen Sie das adaptive Formular zur Bearbeitung und navigieren Sie zum Abschnitt **[!UICONTROL Übermittlung]** der Eigenschaften des Containers für adaptive Formulare und wählen Sie eine Übermittlungsaktion als **An Marketo Engage übermitteln** aus.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

![Marketo-Übermittlungsaktion](/help/forms/assets/marketo-engage-submit-action-af.png){width=50%, height=50%}

Nachdem Sie die Übermittlungsaktion für das adaptive Formular als &quot;**an Marketo Engage senden** konfiguriert haben, können Sie Daten zur Verarbeitung an Adobe Marketo Engage senden. Die Daten können verwendet werden, um Marketing-Kampagnen zu analysieren und zu optimieren, Follow-up-E-Mails zu automatisieren und Trigger-Workflows auf der Grundlage von Formularübermittlungen zu erstellen.

>[!TAB Kernkomponente]

Sie können die Übermittlungsaktion eines adaptiven Formulars basierend auf Kernkomponenten konfigurieren, um Daten an Adobe Marketo Engage zu übermitteln. Um die Übermittlungsaktion an Marketo Engage zu konfigurieren, führen Sie die folgenden Schritte aus:

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Guide-Container]**.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg). Das Dialogfeld Container für adaptive Formulare zum Konfigurieren der Übermittlungsaktion wird geöffnet.
1. Öffnen Sie die **[!UICONTROL Übermittlung]** und wählen Sie eine Übermittlungsaktion als **An Marketo Engage übermitteln** aus.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

![Marketo-Übermittlungsaktion](/help/forms/assets/marketo-engage-submit-action.png){width=50%, height=50%}

Nachdem Sie die Übermittlungsaktion für das adaptive Formular als &quot;**an Marketo Engage senden** konfiguriert haben, können Sie Daten zur Verarbeitung an Adobe Marketo Engage senden. Die Daten können verwendet werden, um Marketing-Kampagnen zu analysieren und zu optimieren, Follow-up-E-Mails zu automatisieren und Trigger-Workflows auf der Grundlage von Formularübermittlungen zu erstellen.

>[!TAB Universeller Editor]

Sie können die Übermittlungsaktion eines im universellen Editor erstellten adaptiven Formulars so konfigurieren, dass Daten an Adobe Marketo Engage gesendet werden. Um die Übermittlungsaktion an Marketo Engage zu konfigurieren, führen Sie die folgenden Schritte aus:

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Klicken Sie im Editor **die Erweiterung**&#x200B;Formulareigenschaften bearbeiten“.
Das **Formulareigenschaften** wird angezeigt.

   >[!NOTE]
   >
   > * Wenn das Symbol **Formulareigenschaften bearbeiten** in der Benutzeroberfläche des universellen Editors nicht angezeigt wird, aktivieren Sie die Erweiterung **Formulareigenschaften bearbeiten** in der Extension Manager.
   > * Informationen zum Aktivieren oder Deaktivieren von Erweiterungen im universellen Editor finden [ im Artikel ](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)Extension Manager-Feature-Highlights&rbrace;.

1. Klicken Sie auf **Übermittlung** und wählen Sie **[!UICONTROL An Marketo Engage übermitteln]** Übermittlungsaktion aus.

   ![Marketo-Übermittlungsaktion](/help/forms/assets/marketo-engage-submit-action-ue.png)

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

Nachdem Sie die Übermittlungsaktion für das adaptive Formular als &quot;**an Marketo Engage senden** konfiguriert haben, können Sie Daten zur Verarbeitung an Adobe Marketo Engage senden. Die Daten können verwendet werden, um Marketing-Kampagnen zu analysieren und zu optimieren, Follow-up-E-Mails zu automatisieren und Trigger-Workflows auf der Grundlage von Formularübermittlungen zu erstellen.

>[!ENDTABS]

## Häufig gestellte Fragen (FAQ)

**F: Kann man die Übermittlungsaktion für Formulare ändern, die für die Verbindung mit dem Marketo Engage-Schema konfiguriert sind?**
**A:** Standardmäßig ist die Aktion **An Marketo senden** ausgewählt, wenn ein Formular für die Verbindung mit dem Marketo Engage-Schema konfiguriert ist. Sie können jedoch bei Bedarf die Übermittlungsaktion für die Formulare ändern.

## Nächster Schritt

Sie können ein adaptives Formular auch mit der [Munchkin-](https://experienceleague.adobe.com/de/docs/marketo/using/product-docs/administration/setup/munchkin) verbinden, um die Anzahl der Besuche, Klicks und Formularübermittlungen zu verfolgen.

## Verwandte Artikel

{{af-submit-action}}

## Siehe auch

{{marketo-engage-see-also}}
