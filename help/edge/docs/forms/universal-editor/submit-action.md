---
title: Übermittlungsaktionen
description: Konfigurieren von Übermittlungsaktionen für adaptive Formulare.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
exl-id: beee9be7-8215-496b-9fb9-61fba000a055
source-git-commit: ba42a99e6138616ab6a7564c4bf58400844bdcc4
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 19%

---

# Übermittlungsaktion für adaptive Formulare

Eine Sende-Aktion gibt das Ziel für die Daten an, die über ein adaptives Formular erfasst werden. Der Übermittlungsprozess beginnt, wenn der Benutzer im Formular auf **[!UICONTROL Schaltfläche]** Senden“ klickt. AEM Forms bietet zwei Arten von Übermittlungsaktionen, die unten beschrieben werden, und ermöglicht es Ihnen, benutzerdefinierte Übermittlungsaktionen zu erstellen und zu verwenden, um Ihre spezifischen Anforderungen zu erfüllen. Die vordefinierten Übermittlungsaktionen sind:

<!--To define a Submit Action for an Adaptive Form, you use the Properties dialog of the **Adaptive Form block** in the **Editor**-->

* [An REST-Endpunkt übermitteln](#rest-endpoint-submission-ue)
* [E-Mail senden](#email-submission-ue)


### An REST-Endpunkt senden {#rest-endpoint-submission-ue}

Die Aktion An REST-Endpunkt übermitteln wird verwendet, um die übermittelten Formulardaten an einen angegebenen REST-Endpunkt zu senden. Der Endpunkt kann entweder zu einem internen Server, auf dem das Formular gehostet wird, oder zu einem externen Server gehören, indem ein relativer Pfad oder ein absoluter Pfad verwendet wird. Um Daten an den AEM-Server, auf dem sich das Formular befindet, zu senden, verwenden Sie einen relativen Pfad entsprechend dem Stammpfad des AEM-Servers. Beispiel: `/content/forms/af/SampleForm.html`. Um Daten an einen anderen Server zu senden, verwenden Sie den absoluten Pfad.

<!--Configuring the Submit Action to REST Endpoint for Adaptive Forms offers several benefits such as:  
* It facilitates seamless integration of form data with external systems and services via RESTful APIs.  
* Offers flexibility in managing data submissions from Adaptive Forms, accommodating dynamic and complex data structures.  
* Allows dynamic mapping of form fields to parameters within the REST endpoint URL, enabling adaptable and customizable data submissions.
-->



So konfigurieren Sie einen REST-Endpunkt:

1. Öffnen Sie Ihr adaptives Formular in **[!UICONTROL Editor]**.
1. Wählen Sie **[!UICONTROL Adaptiver Formularblock]**.
1. Klicken Sie auf das Symbol ![Eigenschaften](/help/forms/assets/Smock_Properties_18_N.svg).
1. Wählen Sie **[!UICONTROL An einen REST-Endpunkt übermitteln]** aus der Dropdown-Liste **[!UICONTROL Übermittlungsaktion]** aus.
1. Geben Sie die REST-Endpunkt-URL an.
1. Sie können auch **POST-Anfrage aktivieren** und eine URL eingeben, um die Anfrage zu veröffentlichen.

![Aktivieren einer POST-Anfrage für adaptive Formulare](/help/forms/assets/enable-post-request-ue.png)

>[!NOTE]
>
> * Um Daten an einen internen Server zu senden, geben Sie den Pfad der Ressource an. Die Daten werden an den Pfad der Ressource gesendet. Beispiel: `/content/restEndPoint`. Für solche Sende-Anfragen werden die Authentifizierungsinformationen der Versandanfrage verwendet.
> * Geben Sie eine URL an, um Daten an einen externen Server zu senden. Das Format der URL ist `https://host:port/path_to_rest_end_point`. Stellen Sie sicher, dass Sie den Pfad zum Handhaben der POST-Anforderung anonym konfigurieren.

### E-Mail senden {#email-submission-ue}

Mit der Übermittlungsaktion E-Mail senden können Sie nach erfolgreicher Übermittlung des Formulars eine E-Mail an einen oder mehrere Empfänger senden. Mit der Konfiguration E-Mail senden können Sie eine E-Mail erstellen, die Formulardaten in einem vordefinierten Format enthalten kann. Betrachten Sie beispielsweise die folgende Vorlage, bei der Kundenname, Versandadresse, Bundesland und Postleitzahl aus den übermittelten Formulardaten abgerufen werden. [Weitere Informationen zu E-Mail-Vorlagen finden Sie in Adaptive Forms](/help/forms/html-email-templates-in-adaptive-forms.md). Einige Vorteile der Konfiguration eines adaptiven Formulars mit der Sendeaktion „E-Mail senden“ sind:

1. Dies ermöglicht eine schnelle Kommunikation, da Formulardaten direkt an bestimmte E-Mail-Empfänger gesendet werden.
1. Dies trägt zur Optimierung des Workflows bei, indem Formularübermittlungen direkt in E-Mail-Benachrichtigungen integriert werden.
1. Es hilft Unternehmen, die E-Mail-Inhalte individuell anzupassen, sodass sie für spezifische Kommunikationsanforderungen geeignet sind.

![Eigenschaften adaptiver Formulare im universellen Editor](/help/forms/assets/submit-actions-ue.png)


So konfigurieren Sie eine Übermittlungsaktion als E-Mail für die Übermittlung Ihres Formulars:

1. Öffnen Sie Ihr adaptives Formular in **Editor**.
1. Wählen Sie Ihren **[!UICONTROL adaptiven Formularblock]**.
1. Klicken Sie auf das Symbol ![Eigenschaften](/help/forms/assets/Smock_Properties_18_N.svg).
1. Wählen Sie die **[!UICONTROL E-Mail senden]** aus der Dropdown **[!UICONTROL Liste „Übermittlungsaktion]** aus.
1. Nachdem Sie die Option E-Mail senden ausgewählt haben, können Sie die folgenden Eigenschaften konfigurieren, wie in der Abbildung unten dargestellt.

<table>
  <thead>
    <tr>
      <th>Bild</th>
      <th>Eigenschaft</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
    <tr>
    <td rowspan="7"><img src="/help/forms/assets/email-config-ue.png" alt="E-Mail-Konfiguration"></td> 
    <td><b>Von</td>
    <td>Geben Sie die E-Mail-Adresse des Absenders an.</td>
    </tr>
    <tr>
      <td><b>To</td>
      <td>Geben Sie die primären Empfänger der E-Mail an. Mehrere E-Mail-Adressen können hinzugefügt werden, indem sie durch Kommas getrennt werden.</td>
    </tr>
    <tr>
      <td><b>CC</td>
      <td>Geben Sie die Empfänger an, die eine Kopie (CC) der E-Mail erhalten sollen.</td>
    </tr>
    <tr>
      <td><b>BCC</td>
      <td>Geben Sie die Empfänger an, die eine Blindkopie (BCC) der E-Mail erhalten sollen.</td>
    </tr>
    <tr>
      <td><b>Betreff</td>
      <td>Geben Sie die Betreffzeile der E-Mail an.</td>
    </tr>
    <tr>
      <td><b>Externe Vorlage verwenden</td>
      <td>Aktiviert die Verwendung einer externen E-Mail-Vorlage zum Formatieren des E-Mail-Inhalts. Geben Sie die URL oder den Pfad zur externen Vorlage an, um eine vordefinierte E-Mail-Vorlage zu integrieren, die in Ihrem AEM Assets-Ordner gehostet wird.</td>
    </tr>
    <tr>
      <td><b>Anhang einschließen</td>
      <td>Gibt an, ob die übermittelten Formulardaten eine Anlage enthalten sollen, die über das Formular in der E-Mail übermittelt wurde. Unterstützte Anlagenformate sind PDF, XML und JSON.</td>
    </tr>
  </tbody>
</table>






<!--
        
        * **From**: The email address of the sender.
        * **To**: Specify the primary recipients of the email, multiple email addresses can be added, separated by commas.
        * **CC**: Specify the recipients who should receive a carbon copy (CC) of the email.
        * **BCC**: Specify the recipients who should receive a blind carbon copy (BCC) of the email.
        * **Subject**: Specify the subject line of the email.
        * **Use External Template**: Enables the use of an external email template for formatting the email content. Provide the URL or path to the External template path to integrate a pre-designed email template hosted in your AEM Assets folder.
        * **Include Attachment**: Specifies whether the submitted form data should include an attachment submitted through the form in the email.

    {width=50%,height=50%}![Enable post request for adaptive forms](/help/forms/assets/email-config-ue.png)

-->

## Eine benutzerdefinierte Dankesnachricht beim Senden des adaptiven Formulars anzeigen {#submit-action-message-ue}

Mit der Option Bei Übermittlung können Sie eine Nachricht mit einer Übermittlungsaktion konfigurieren, die bei Übermittlung eines adaptiven Formulars erscheint, um eine Nachricht mit einer Übermittlungsaktion für Ihr Formular zu konfigurieren:

1. Öffnen Sie Ihr adaptives Formular in **Editor**.
1. Wählen Sie Ihren **[!UICONTROL adaptiven Formularblock]**.
1. Klicken Sie auf das Symbol ![Eigenschaften](/help/forms/assets/Smock_Properties_18_N.svg).
1. Beim Klicken wird die folgende Option angezeigt:
   * **[!UICONTROL Beim Senden]**: Mit dem Senden können Sie eine Nachricht anpassen, die beim Senden eines Formulars angezeigt werden soll. Standardmäßig wird dem Benutzer bei erfolgreicher Übermittlung eines Formulars die benutzerdefinierte Meldung „Vielen Dank für die Übermittlung des Formulars“ angezeigt.
Sie können die Dankesnachricht beim Absenden des Formulars auch anpassen, indem Sie die Option **[!UICONTROL Nachricht anzeigen]** auswählen und Ihre Nachricht im Rich-Text-**Editor) hinzufügen/**.


## Siehe auch

{{universal-editor-see-also}}

