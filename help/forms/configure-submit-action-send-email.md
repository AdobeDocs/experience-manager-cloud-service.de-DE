---
Title: How to send an email on submission of an Adaptive Form?
Description: Explore the process to set up email notifications when submitting an Adaptive Form.
keywords: So senden Sie eine E-Mail für ein adaptives Formular, E-Mail-Übermittlungsaktion, E-Mail für adaptive Formulare, E-Mail für Formularübermittlung, E-Mail-Anleitung senden
feature: Adaptive Forms, Core Components
source-git-commit: f1db04e6cd1f78c1530aefd29f5f036ca5e70873
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 24%

---


# Konfigurieren der Sendeaktion &quot;E-Mail senden&quot;für ein adaptives Formular

Die **[!UICONTROL E-Mail senden]** Mit der Übermittlungsaktion können Sie nach erfolgreicher Übermittlung des Formulars eine E-Mail an einen oder mehrere Empfänger senden. Mit dieser Übermittlungsaktion können Sie eine E-Mail erstellen, die Formulardaten in einem vordefinierten Format enthalten kann. Betrachten Sie beispielsweise die folgende Vorlage, bei der Kundenname, Versandadresse, Statusname und Postleitzahl aus den übermittelten Formulardaten abgerufen werden:


    „
    Hallo ${customer_Name},
    
    Ihre Standard-Versandadresse lautet:
    ${customer_Name},
    ${customer_Shipping_Address},
    ${customer_State},
    ${customer_ZIPCode}
    
    Mit freundlichen Grüßen
    WKND
    
    “


## Vorteile

Einige Vorteile der Konfiguration eines adaptiven Formulars mit der Sendeaktion E-Mail senden sind:

* Sie ermöglicht eine schnelle Kommunikation, da Formulardaten direkt an bestimmte E-Mail-Empfänger gesendet werden.
* Dies trägt zur Optimierung des Workflows bei, indem Formularübermittlungen direkt in E-Mail-Benachrichtigungen integriert werden.
* Es hilft Unternehmen, den E-Mail-Inhalt anzupassen und ihn so an bestimmte Kommunikationsanforderungen anzupassen.

## Konfigurieren der Sendeaktion &quot;E-Mail senden&quot; {#steps-to-configure-send-email-submit-action}

Konfigurieren der Sendeaktion:

1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Übermittlung]**.
1. Aus dem **[!UICONTROL Übermittlungsaktion]** Dropdown-Liste auswählen **[!UICONTROL E-Mail senden]**.

   ![Aktionskonfiguration von E-Mail senden](/help/forms/assets/send-email-action-configuration.gif)
1. Geben Sie die E-Mail-ID des Absenders im **[!UICONTROL Von]** Textfeld.
1. Fügen Sie die E-Mail-Adresse des Empfängers im **[!UICONTROL nach]** Textfeld. Sie können mehrere Empfänger hinzufügen, indem Sie auf **[!UICONTROL Hinzufügen]** Schaltfläche.
1. [Optional] Fügen Sie den Empfänger für CC und BCC hinzu, indem Sie auf die **[!UICONTROL Hinzufügen]** Schaltfläche.
1. Festlegen einer Betreffzeile im **[!UICONTROL Betreff]** Textfeld.
1. Fügen Sie eine E-Mail-Vorlage hinzu, um die Sendeaktion für E-Mails zu konfigurieren.
   * Sie können den Pfad zur externen E-Mail-Vorlage angeben, die in Ihren AEM-Assets gespeichert ist, indem Sie die **[!UICONTROL Externer Vorlagenpfad]** -Option.
   * Sie können auch eine benutzerdefinierte E-Mail-Vorlage für die Formularübermittlung im **[!UICONTROL E-Mail-Vorlage]** Textfeld.
1. [Optional] Die **[!UICONTROL E-Mail senden]** Übermittlungsaktion bietet die Option, Anlagen und eine [Datensatzdokument (DoR)](generate-document-of-record-core-components.md) mit der E-Mail.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

## Best Practices {#best-practices}

* Es wird empfohlen, den E-Mail-Inhalt klar und prägnant zu halten. Benutzer sollten den Zweck der E-Mail und die erforderlichen Maßnahmen verstehen.
* Es wird empfohlen, dass alle Formularfelder eindeutige Elementnamen aufweisen, auch wenn sie in verschiedenen Bereichen in einem adaptiven Formular platziert werden.
* Bei der Verwendung von AEM as a Cloud Service ist eine Verschlüsselung für ausgehendene E-Mails erforderlich. Die Funktion für ausgehende E-Mails ist standardmäßig deaktiviert. Senden Sie zum Aktivieren ein Support-Ticket an [Zugriff anfordern](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=de#sending-email).


## Ähnliche Artikel

{{af-submit-action}}


