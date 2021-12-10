---
title: Senden einer Formularsendebestätigung per E-Mail
seo-title: Sending a form submission acknowledgement via email
description: Mit AEM Forms können Sie die E-Mail-Übermittlungsaktion so konfigurieren, dass bei der Formularübermittlung eine Bestätigung an den Benutzer gesendet wird.
seo-description: AEM Forms allows you to configure the email Submit Action that sends an acknowledgement to a user on submitting the form.
uuid: c80b1ef4-8fe3-48e0-8fc6-3032dc022a38
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 574de3d5-69ba-4e2f-a8ab-c59f357e4386
docset: aem65
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 100%

---


# Senden einer Formularsendebestätigung per E-Mail {#sending-a-form-submission-acknowledgement-via-email}

## Übermittlung der Daten adaptiver Formulare {#adaptive-form-data-submission}

Adaptive Formulare bieten mehrere standardmäßige Workflows für [Übermittlungsaktionen](configuring-submit-actions.md), um die Formulardaten an verschiedene Endpunkte zu senden.

Beispiel: Bei der Übermittlungsaktion **[!UICONTROL E-Mail senden]** wird eine E-Mail nach erfolgreicher Übermittlung eines adaptiven Formulars gesendet. Sie kann auch so konfiguriert werden, dass die Formulardaten und die PDF-Datei in die E-Mail eingefügt werden.

In diesem Artikel werden die Schritte erläutert, mit denen die E-Mail-Aktion für ein adaptives Formular aktiviert wird, und die verschiedenen bereitgestellten Konfigurationen beschrieben.

>[!NOTE]
>
>Sie können auch die Option **[!UICONTROL PDF per E-Mail senden]** verwenden, um das ausgefüllte Formular per E-Mail als PDF-Anlage zu senden. Die Konfigurationsoptionen für diese Aktion sind mit den Optionen identisch, die für die Aktion **[!UICONTROL E-Mail senden]** verfügbar sind. Die E-Mail-PDF-Aktion ist nur für XFA-basierte adaptive Formulare verfügbar.

## Aktion „E-Mail senden“  {#email-action}

Mit der Aktion „E-Mail senden“ kann ein Autor automatisch eine E-Mail an einen oder mehrere Empfänger senden, wenn das adaptive Formular erfolgreich gesendet wurde.

<!-- >>[!NOTE]
>
>To use the Send email action, you need to configure the AEM mail service as described in [Configuring the mail service](/help/sites-administering/notification.md#configuring-the-mail-service).

### Enabling Send email action on an Adaptive Form {#enabling-email-action-on-an-adaptive-form}

1. Open an Adaptive Form in **[!UICONTROL edit]** mode.

1. In the **[!UICONTROL Content]** tab, tap **[!UICONTROL Form Container]** and tap ![configure](assets/configure-icon.svg) to view the Adaptive Form properties.  

1. In the **[!UICONTROL Submission]** section, select **[!UICONTROL Send email]** from the **[!UICONTROL Submit Action]** drop-down list.  

   ![Submit Actions](assets/submission-actions.png)

1. Specify valid email IDs in the **[!UICONTROL To]**, **[!UICONTROL CC]**, and **[!UICONTROL BCC]** fields.

   Specify the subject and the body of the email in the **[!UICONTROL Subject]** and **[!UICONTROL Email Template]** fields, respectively.

   You can also specify variable placeholders in the fields, in which case, the values of the fields are processed when the form is successfully submitted by an end user. For more information, see [Using Adaptive Form field names to dynamically create email content](form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p).

   Select **[!UICONTROL Include attachments]** if the form includes file attachments and you want to attach these files in the email.

   >[!NOTE]
   >
   >If you choose the **[!UICONTROL Send PDF via Email]** option, you must select the Include attachments option.

1. Click ![save](assets/save_icon.svg) to save the changes. -->

### Verwenden von Feldnamen aus adaptiven Formularen zur dynamischen Erstellung von E-Mail-Inhalt {#using-adaptive-form-field-names-to-dynamically-create-email-content}

Die Feldnamen in einem adaptiven Formular werden als Platzhalter bezeichnet, die bei Übermittlung des Formulars durch den Wert dieses Felds ersetzt werden.

In der Aktion **[!UICONTROL E-Mail senden]** können Sie Platzhalter verwenden, die verarbeitet werden, wenn die Aktion ausgeführt wird. Das bedeutet, dass die Header der E-Mail (**[!UICONTROL An]**, **[!UICONTROL CC]**, **[!UICONTROL BCC]**, **[!UICONTROL Betreff]**) dann erstellt werden, wenn der Benutzer das Formular sendet.

Um einen Platzhalter zu definieren, geben Sie `${<field name>}` in ein Feld ein, nachdem Sie **[!UICONTROL E-Mail senden]** als Übermittlungsaktion ausgewählt haben.

Beispiel: Wenn das Formular das Feld **[!UICONTROL E-Mail-Adresse]** mit dem Namen `email_addr` zur Abfrage der E-Mail-ID eines Benutzers enthält, können Sie Folgendes in den Feldern **[!UICONTROL An]**, **[!UICONTROL CC]** oder **[!UICONTROL BCC]** angeben.

`${email_addr}`

Wenn ein Benutzer das Formular sendet, wird eine E-Mail an die E-Mail-Adresse gesendet, die in das Feld `email_addr` des Formulars eingegeben wurde.

>[!NOTE]
>
>Sie finden den Namen eines Felds im Dialogfeld **[!UICONTROL Bearbeiten]** für das Feld.

Variable Platzhalter können auch in den Feldern **[!UICONTROL Betreff]** und **[!UICONTROL E-Mail-Vorlage]** verwendet werden.

Beispiel:

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>Felder in wiederholbaren Bereichen können nicht als variable Platzhalter verwendet werden.

