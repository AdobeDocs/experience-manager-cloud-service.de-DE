---
title: Anzeigen einer benutzerdefinierten Dankesnachricht nach der Formularübermittlung
description: Erfahren Sie, wie Sie Dankesseiten und Umleitungen für den Formularbaustein konfigurieren, um das Anwendererlebnis zu optimieren und die Journey der Benutzenden zu optimieren.
feature: Edge Delivery Services
exl-id: e6c66b22-dc52-49e3-a920-059adb5be22f
role: Admin, Architect, Developer
source-git-commit: 4356fcc73a9c33a11365b1eb3f2ebee5c9de24f0
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 100%

---

# Anzeigen einer benutzerdefinierten Dankesnachricht nach der Formularübermittlung

Nachdem Benutzende ein Formular abgesendet haben, ist es entscheidend, ihnen durch eine Dankesnachricht ein nahtloses Erlebnis zu bieten. Dies bestätigt nicht nur die erfolgreiche Übermittlung, sondern verbessert zudem die Zufriedenheit der Benutzenden und führt sie weiter auf ihrer Journey.

* **Dankesnachricht**: Eine Dankesnachricht ist ein Eckpfeiler des Anwendererlebnisses, indem sie eine Rückversicherung bietet, wichtige Informationen vermittelt und gleichzeitig die Markenidentität stärkt. Sie dient als direkte Bestätigung der Aktion der Benutzenden und gibt ihnen das Gefühl, etwas geschafft zu haben, ein Gefühl von Zufriedenheit.

* **Umleitung**: Eine Umleitung spielt eine zentrale Rolle dabei, Benutzende zu relevanten Zielen zu steuern, die Interaktion zu optimieren und letztendlich Konversionsraten zu steigern. Durch eine Umleitung, die Benutzende nahtlos zum nächsten Schritt in der Journey führt, wird ein reibungsloses Navigationserlebnis sichergestellt. Ein Beispiel dafür ist die Weiterleitung einer Person zur Zahlungsseite, nachdem die ersten Details erfasst wurden.

Standardmäßig verhält sich der adaptive Formularbaustein so, dass bei der Übermittlung die folgende Dankesnachricht angezeigt wird. Die Nachricht wird nach erfolgreicher Übermittlung des Formulars oben im Formular angezeigt.

![Standardmäßige Dankesnachricht](/help/edge/assets/thank-you-message.png)

Sie haben jedoch die Flexibilität, dieses Erlebnis an Ihre individuellen Anforderungen anzupassen. Sie haben unter anderem folgende Möglichkeiten:

* Anzeigen einer benutzerdefinierten Dankesnachricht nach der Formularübermittlung
* Umleiten von Benutzenden zu einer anderen Seite nach der Übermittlung zur Durchführung weiterer Aktionen

>[!NOTE]
>
> In der folgenden [Abfragetabelle](/help/edge/docs/forms/assets/enquiry.xlsx) finden Sie Informationen zum Anpassen der Dankesnachricht an Ihre Anforderungen.

## Konfigurieren einer benutzerdefinierten Dankesnachricht

Wenn Sie nach erfolgreicher Übermittlung des Formulars eine personalisierte Dankesnachricht anzeigen möchten, können Sie Ihre Tabelle so konfigurieren, dass diese angezeigt wird.

Führen Sie die folgenden Schritte aus, um eine benutzerdefinierte Dankesnachricht für Ihren adaptiven Formularbaustein zu konfigurieren:

1. Wechseln Sie in Microsoft SharePoint oder Google Workspace zum Projektordner „Edge Delivery“ und öffnen Sie die Tabelle.
1. Fügen Sie in der Spalte `value` eine benutzerdefinierte Dankesnachricht für den Feldtyp `submit` in der Tabelle hinzu.

   ![Benutzerdefinierte Dankesnachricht](/help/edge/docs/forms/assets/thankyou-custommessage.png)

   Fügen Sie beispielsweise für den Feldtyp `submit` die Meldung `Submission Successful!` in die Spalte `value` ein.

1. Erstellen Sie eine Vorschau und veröffentlichen Sie das Blatt mit [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   ![Benutzerdefinierte Dankesnachricht](/help/edge/docs/forms/assets/customized-thank-you-message.png)

## Umleiten von Benutzenden zu einer anderen Seite nach der Übermittlung

Wenn Benutzende nach der Formularübermittlung zu einer anderen Seite umgeleitet werden, kann dies das Anwendererlebnis verbessern, indem relevante Informationen bereitgestellt, Aktionen bestätigt und Benutzende zu gewünschten Ergebnissen angeleitet werden. Beispiel:

* Nachdem eine Person ein Kaufformular ausgefüllt hat, wird sie auf eine Zahlungsseite umgeleitet, um die Transaktion sicher abzuschließen.
* Beim Senden eines Registrierungsformulars für eine Veranstaltung oder ein Webinar werden Benutzende auf eine Bestätigungsseite umgeleitet, auf der Details zu dem Ereignis, z. B. Datum, Uhrzeit und Ort, angezeigt werden.

Gehen Sie wie folgt vor, um Benutzende auf eine andere Seite weiterzuleiten:

1. Wechseln Sie in Microsoft SharePoint oder Google Workspace zum Projektordner „Edge Delivery“ und öffnen Sie die Tabelle.
1. Fügen Sie die URL in die Spalte `value` für den Feldtyp `submit` in der Tabelle ein, um Benutzende bei erfolgreicher Übermittlung des Formulars weiterzuleiten.
Um die Seite auf eine andere Seite umzuleiten, verwenden Sie die URL der Seite [Edge Delivery-Dokumentation](https://www.aem.live/docs/) 

   ![Umleitungs-URL für Dankesnachricht](/help/edge/docs/forms/assets/thankyou-redirecturl.png)

1. Erstellen Sie eine Vorschau und veröffentlichen Sie das Blatt mit [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   ![Umleitungs-Dankesnachricht](/help/edge/docs/forms/assets/thankyou-redirectpage.gif)

Sie können auch eine neue Dokumentdatei erstellen und ihre Vorschau-URL in die Spalte `value` für den Feldtyp `submit` einfügen.

Nachdem Benutzende ein Formular abgesendet haben, ist es wichtig, ihnen eine klare Dankesnachricht zu bieten. Sie bestätigt, dass die Übermittlung erfolgreich war, und steigert die Benutzerzufriedenheit.

## Siehe auch

{{see-more-forms-eds}}

<!--
## Configuring a custom thank you message

The default behavior of Adaptive Forms Block is to display the following thank you message on submission. The message is displayed on the top of the form. 

![default thank you message](/help/edge/assets/thank-you-message.png)


Follow the below steps to configure a custom thank you message for your Adaptive Forms Block:

1. Access your AEM Project on your local machine or GitHub repository.

2. Navigate to [AEM Project Folder]\blocks\form\submit.js file for editing.

3. Locate the following code 

    ```JavaScript

        thankYouMessage.innerHTML = payload?.body?.thankYouMessage || 'Thanks for your submission';

    ```

4. Replace the default message with your custom message. For example, 


    ```JavaScript

        thankYouMessage.innerHTML = payload?.body?.thankYouMessage || 'Your submission has been received and noted.';

    ```


1. Save the file. Commit the updated file to your GitHub Repository. Now, when you submit a form, the custom thank you message is displayed. For example,

![Custom thank you message](/help/edge/assets/custom-thank-you-message.png)

* **Thank you message**: A thank you message is a cornerstone of user experience, offering reassurance and conveying important information while reinforcing brand identity. It serves as a direct acknowledgment of the user's action, fostering a sense of completion and satisfaction.

* **Redirect**: A redirect plays a pivotal role in steering users towards relevant destinations, optimizing engagement, and ultimately boosting conversion rates. By seamlessly guiding users to the next step in their journey, a redirect ensures a smooth navigation experience. For example, redirecting user to payments page after collecting initial details. 

In the Adaptive Forms Block, the default behavior is to display a thank you message. However, you have the flexibility to tailor this experience to meet your specific needs. Options include:

* [Configuring a custom thank you message to align with your brand and communication goals](#configuring-the-thank-you-page-and-message) 
* [Redirecting users to another page post-submission for further action](#redirect-users-to-another-page-post-submission)

## Redirect users to another page post-submission

Redirecting a user to another page after form submission can enhance user experience by providing relevant information, confirming actions, and guiding users towards desired outcomes. For example, 

* after a user completes a purchase form, they are redirected to a payment page to complete the transaction securely. 
* upon submitting a registration form for an event or webinar, users are redirected to a confirmation page displaying event details, such as date, time, and location.

To redirect the "thankyou" page to a different page, use the [website redirects](https://www.aem.live/docs/redirects) spreadsheet. 





1. Access your AEM Edge Delivery project folder on Microsoft SharePoint or Google Workspace.
1. Create a Microsoft Word or Google Docs file named "thankyou" within your project directory.
1. Add your thank you message to the "thankyou" file. </br>
   
    ![Example thank you page](/help/edge/assets/sample-thankyou-page.png) 

1. Use AEM Sidekick to preview and publish the "thankyou" file.

 Your Adaptive Forms Block displays the "thankyou" page on form submission. 

## Redirect users to another page post-submission

By default, the Adaptive Forms Block redirects the users to the "thankyou" page. To redirect users to a page other than the default "thankyou" page, you have two options: 

* [Replace the "thankyou" page with a different page](#replace-the-existing-thankyou-page) 
* [Use website redirects for "thankyou" page redirection](#use-website-redirects-for-thankyou-page-redirection) 

### Replace the "thankyou" page

1. Open the "[EDS Project]/blocks/form/form.js" file for editing.
1. Change the `thankyou` page in the following line to page of your choice:

    ```JavaScript

    window.location.href = form.dataset?.redirect || 'thankyou';

    ```

    For example,

    ```JavaScript

    window.location.href = form.dataset?.redirect || 'payment';
        
    ```
    
    >[!NOTE]
    >
    > Ensure that a page with the same name exists in your Edge Delivery Services project folder on either Microsoft SharePoint or Google Workspace. If the page does not exist, proceed to create and publish it.  

1. Proceed to check in the updated 'form.js' folder and its underlying files to your Edge Delivery Services project on GitHub. This update ensures that the form now redirects to the updated page as specified.

1. Ensure that the page exists in your EDS project folder and publish it.


### Use website redirects for "thankyou" page redirection

Redirecting a user to another page after form submission can enhance user experience by providing relevant information, confirming actions, and guiding users towards desired outcomes. For example, 

* after a user completes a purchase form, they are redirected to a payment page to complete the transaction securely. 
* upon submitting a registration form for an event or webinar, users are redirected to a confirmation page displaying event details, such as date, time, and location.

To redirect the "thankyou" page to a different page, use the [website redirects](https://www.aem.live/docs/redirects) spreadsheet. 



## See also

{{see-more-forms-eds}}