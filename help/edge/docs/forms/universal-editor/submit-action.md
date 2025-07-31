---
title: Übermittlungsaktionen
description: Konfigurieren Sie Übermittlungsaktionen für ein adaptives Formular.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: beee9be7-8215-496b-9fb9-61fba000a055
hide: true
hidefromToC: true
source-git-commit: 565336d96a718a46f23d0acfa6155a6fd78ad87d
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 100%

---

# Übermittlungsaktion für adaptive Formulare

## Überblick

Die Formularübermittlung ist der wichtige letzte Schritt der Benutzer-Journey. Dort werden die erfassten Daten verarbeitet und Aktionen durchgeführt. Dieses Dokument enthält eine umfassende Anleitung zum Konfigurieren und Verwalten von Übermittlungsaktionen für adaptive Formulare im universellen Editor.

### Lerninhalte

Am Ende dieses Dokuments werden Sie Folgendes beherrschen:

* Konfigurieren verschiedener Arten von Übermittlungsaktionen für Ihre Formulare
* Einrichten von REST-Endpunktübermittlungen für die Integration mit externen Systemen
* Konfigurieren von E-Mail-Sendungen für Formularantworten
* Implementieren benutzerdefinierter Übermittlungsaktionen für bestimmte Unternehmensanforderungen
* Bearbeitung der Formularvalidierung und Fehlerszenarien bei der Übermittlung

### Zielgruppe

Dieses Handbuch wurde für folgende Rollen entwickelt:

* **Formularentwicklerinnen und -entwickler**, die Übermittlungslogik implementieren
* **Systemintegratorinnen und -integratoren**, die Formulare mit Backend-Systemen verknüpfen
* **Geschäftsanalystinnen und -analysten**, die Formular-Workflows definieren
* **Technische Architektinnen und Architekten**, die Formularübermittlungsprozesse erstellen

### Verfügbare Übermittlungsaktionen

Der universelle Editor bietet zwei primäre Arten von Übermittlungsaktionen:

1. **An REST-Endpunkt übermitteln** * Formulardaten an API-Endpunkte senden
2. **E-Mail senden** * Formularantworten per E-Mail versenden

### Voraussetzungen

Bevor Sie Übermittlungsaktionen konfigurieren, müssen Sie:

* Zugriff auf den universellen Editor haben
* Ordnungsgemäße Berechtigungen für die Formularkonfiguration besitzen
* Den Zielübermittlungsendpunkt oder die E-Mail-Konfiguration verstanden haben

Eine Übermittlungsaktion gibt das Ziel für die Daten an, die über ein adaptives Formular erfasst werden. Der Übermittlungsprozess beginnt, wenn die Benutzenden im Formular auf die Schaltfläche **[!UICONTROL Senden]** klicken. AEM Forms bietet zwei Arten von Übermittlungsaktionen, die unten beschrieben werden, und ermöglicht es Ihnen, benutzerdefinierte Übermittlungsaktionen zu erstellen und zu verwenden, die Ihre spezifischen Anforderungen erfüllen. Vordefinierte Übermittlungsaktionen:

<!--To define a Submit Action for an Adaptive Form, you use the Properties dialog of the **Adaptive Form block** in the **Editor**-->

* [An REST-Endpunkt senden](#rest-endpoint-submission-ue)
* [E-Mail senden](#email-submission-ue)


### An REST-Endpunkt senden {#rest-endpoint-submission-ue}

Die Aktion „An REST-Endpunkt senden“ wird verwendet, um die übermittelten Formulardaten an einen angegebenen REST-Endpunkt zu senden. Der Endpunkt kann entweder zu einem internen Server gehören, auf dem das Formular gehostet wird, er kann aber auch zu einem externen Server gehören, indem ein relativer Pfad oder ein absoluter Pfad verwendet wird. Um Daten an den AEM-Server, auf dem sich das Formular befindet, zu senden, verwenden Sie einen relativen Pfad entsprechend dem Stammpfad des AEM-Servers. Beispiel: `/content/forms/af/SampleForm.html`. Wenn Sie Daten an einen Server senden, verwenden Sie den absoluten Pfad.

<!--Configuring the Submit Action to REST Endpoint for Adaptive Forms offers several benefits such as:  
* It facilitates seamless integration of form data with external systems and services via RESTful APIs.  
* Offers flexibility in managing data submissions from Adaptive Forms, accommodating dynamic and complex data structures.  
* Allows dynamic mapping of form fields to parameters within the REST endpoint URL, enabling adaptable and customizable data submissions.
-->



So konfigurieren Sie einen REST-Endpunkt:

1. Öffnen Sie das adaptive Formular im **[!UICONTROL Editor]**.
1. Wählen Sie **[!UICONTROL Adaptiver Formularblock]** aus.
1. Klicken Sie auf das Symbol „Eigenschaften“ ![Eigenschaften](/help/forms/assets/Smock_Properties_18_N.svg).
1. Wählen Sie **[!UICONTROL An REST-Endpunkt senden]** aus der Dropdown-Liste **[!UICONTROL Übermittlungsaktion]** aus.
1. Geben Sie die URL des REST-Endpunkts an.
1. Sie können auch **POST-Anforderungen aktivieren** und eine URL eingeben, um die Anforderung zu veröffentlichen.

![Screenshot des Panels mit den Einstellungen für den universellen Editor mit den REST-Endpunktkonfigurationsfeldern, einschließlich URL-Eingabe und Umschalter „POST-Anforderung aktivieren“ für die Formularübermittlung](/help/forms/assets/enable-post-request-ue.png)

>[!NOTE]
>
> * Um Daten an einen internen Server zu senden, geben Sie den Pfad der Ressource an. Die Daten werden an den Pfad der Ressource gesendet. Beispiel: `/content/restEndPoint`. Für solche Sende-Anfragen werden die Authentifizierungsinformationen der Versandanfrage verwendet.
> * Geben Sie eine URL an, um Daten an einen externen Server zu senden. Das Format der URL ist `https://host:port/path_to_rest_end_point`. Stellen Sie sicher, dass Sie den Pfad zum Handhaben der POST-Anforderung anonym konfigurieren.

### E-Mail senden {#email-submission-ue}

Bei der Übermittlungsaktion „E-Mail senden“ können Sie nach erfolgreicher Übermittlung des Formulars eine E-Mail an die Empfängerinnen und Empfänger senden. Mit der Konfiguration „E-Mail senden“ können Sie eine E-Mail erstellen, die Formulardaten in einem vordefinierten Format enthalten kann. Betrachten Sie beispielsweise die folgende Vorlage, bei der Kundenname, Versandadresse, Ländername und Postleitzahl aus den übermittelten Formulardaten abgerufen werden. [Weitere Informationen zu E-Mail-Vorlagen in adaptiven Formularen](/help/forms/html-email-templates-in-adaptive-forms.md). Einige Vorteile der Konfiguration eines adaptiven Formulars mit der Sendeaktion „E-Mail senden“ sind:

1. Sie ermöglicht eine schnelle Kommunikation, da Formulardaten direkt an bestimmte E-Mail-Empfängerinnen und -Empfänger gesendet werden.
1. Dies trägt zur Optimierung des Workflows bei, indem Formularübermittlungen direkt in E-Mail-Benachrichtigungen integriert werden.
1. Es hilft Unternehmen, die E-Mail-Inhalte individuell anzupassen, sodass sie für spezifische Kommunikationsanforderungen geeignet sind.

![Eigenschaften adaptiver Formulare im universellen Editor](/help/forms/assets/submit-actions-ue.png)


So konfigurieren Sie für die Übermittlung Ihres Formulars eine Übermittlungsaktion als E-Mail:

1. Öffnen Sie das adaptive Formular im **Editor**.
1. Wählen Sie Ihren **[!UICONTROL adaptiven Formularblock]** aus.
1. Klicken Sie auf das Symbol „Eigenschaften“ ![Eigenschaften](/help/forms/assets/Smock_Properties_18_N.svg).
1. Wählen Sie die Option **[!UICONTROL E-Mail senden]** aus der Dropdown-Liste **[!UICONTROL Übermittlungsaktion]** aus.
1. Nachdem Sie die Option „E-Mail senden“ ausgewählt haben, können Sie die folgenden Eigenschaften konfigurieren, wie in der Abbildung unten dargestellt.

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
    <td>Geben Sie die E-Mail-Adresse des Absenders oder der Absenderin an.</td>
    </tr>
    <tr>
      <td><b>An</td>
      <td>Geben Sie die primären Empfängerinnen und Empfänger der E-Mail an. Es können mehrere E-Mail-Adressen hinzugefügt werden, indem sie durch Kommas getrennt werden.</td>
    </tr>
    <tr>
      <td><b>CC</td>
      <td>Geben Sie die Empfängerinnen und Empfänger an, die eine Kopie (CC) der E-Mail erhalten sollen.</td>
    </tr>
    <tr>
      <td><b>BCC</td>
      <td>Geben Sie die Empfängerinnen und Empfänger an, die eine Blindkopie (BCC) der E-Mail erhalten sollen.</td>
    </tr>
    <tr>
      <td><b>Betreff</td>
      <td>Geben Sie die Betreffzeile der E-Mail an.</td>
    </tr>
    <tr>
      <td><b>Externe Vorlage verwenden</td>
      <td>Ermöglicht die Verwendung einer externen E-Mail-Vorlage zum Formatieren des E-Mail-Inhalts. Geben Sie die URL oder den Pfad zur externen Vorlage an, um eine vordefinierte E-Mail-Vorlage zu integrieren, die in Ihrem AEM Assets-Ordner gehostet wird.</td>
    </tr>
    <tr>
      <td><b>Anlagen einschließen</td>
      <td>Gibt an, ob die übermittelten Formulardaten eine Anlage enthalten sollen, die mit dem Formular in der E-Mail übermittelt wird. Unterstützte Anlagenformate sind PDF, XML und JSON.</td>
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

    ![Screenshot of the Universal Editor email configuration panel showing fields for From, To, CC, BCC, Subject, and options for external templates and attachments](/help/forms/assets/email-config-ue.png)

-->

## Anzeigen einer benutzerdefinierten Dankesnachricht nach der Übermittlung des adaptiven Formulars {#submit-action-message-ue}

Mit der Option „Beim Senden“ können Sie eine Nachricht für die Übermittlungsaktion bei der Übermittlung eines adaptiven Formulars konfigurieren. So konfigurieren Sie eine Nachricht für die Übermittlungsaktion für Ihr Formular:

1. Öffnen Sie das adaptive Formular im **Editor**.
1. Wählen Sie Ihren **[!UICONTROL adaptiven Formularblock]** aus.
1. Klicken Sie auf das Symbol „Eigenschaften“ ![Eigenschaften](/help/forms/assets/Smock_Properties_18_N.svg).
1. Beim Klicken wird die folgende Option angezeigt:
   * **[!UICONTROL Beim Senden]**: Mit „Beim Senden“ können Sie eine Nachricht anpassen, die beim Senden eines Formulars angezeigt werden soll. Standardmäßig bekommen die Benutzenden bei erfolgreicher Übermittlung eines Formulars die benutzerdefinierte Nachricht „Vielen Dank für die Übermittlung des Formulars“ angezeigt.
Sie können die Dankesnachricht bei der Formularübermittlung auch anpassen, indem Sie die Option **[!UICONTROL Nachricht anzeigen]** auswählen und Ihre Nachricht im **Rich-Text-Editor** hinzufügen/bearbeiten.


## Siehe auch

{{universal-editor-see-also}}

