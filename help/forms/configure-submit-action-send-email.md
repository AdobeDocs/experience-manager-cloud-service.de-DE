---
Title: How to send an email on submission of an Adaptive Form?
Description: Explore the process to set up email notifications when submitting an Adaptive Form.
keywords: So senden Sie eine E-Mail für ein adaptives Formular, E-Mail-Übermittlungsaktion, E-Mail für adaptive Formulare, E-Mail für Formularübermittlung, E-Mail-Anleitung senden
feature: Adaptive Forms, Core Components
exl-id: 70386e57-345b-4edb-97f1-3fd52ea9ff4f
title: Konfigurieren einer Übermittlungsaktion für ein adaptives Formular
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 100%

---

# Konfigurieren der Sendeaktion „E-Mail senden“ für ein adaptives Formular

Bei der Übermittlungsaktion **[!UICONTROL E-Mail senden]** wird nach erfolgreicher Übermittlung des Formulars eine E-Mail an die Empfängerinnen und Empfänger gesendet. Mit dieser Sendeaktion können Sie eine E-Mail erstellen, die Formulardaten in einem vordefinierten Format enthalten kann. Betrachten Sie beispielsweise die folgende Vorlage, bei der Kundenname, Versandadresse, Statusname und Postleitzahl aus den übermittelten Formulardaten abgerufen werden:


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

Einige Vorteile der Konfiguration eines adaptiven Formulars mit der Sendeaktion „E-Mail senden“ sind:

* Sie ermöglicht eine schnelle Kommunikation, da Formulardaten direkt an bestimmte E-Mail-Empfängerinnen und -Empfänger gesendet werden.
* Dies trägt zur Optimierung des Workflows bei, indem Formularübermittlungen direkt in E-Mail-Benachrichtigungen integriert werden.
* Es hilft Unternehmen, die E-Mail-Inhalte individuell anzupassen, sodass sie für spezifische Kommunikationsanforderungen geeignet sind.

## Konfigurieren der Sendeaktion „E-Mail senden“ {#steps-to-configure-send-email-submit-action}

So konfigurieren Sie die Sendeaktion:

1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Übermittlung]**.
1. Wählen Sie **[!UICONTROL E-Mail senden]** aus der Dropdown-Liste **[!UICONTROL Übermittlungsaktion]** aus.

   ![Aktionskonfiguration von „E-Mail senden“](/help/forms/assets/send-email-action-configuration.gif)
1. Geben Sie die E-Mail-ID der Absenderin bzw. des Absenders im Textfeld **[!UICONTROL Von]** ein.
1. Fügen Sie die E-Mail-ID der der Empfängerin bzw. des Empfängers  im Textfeld **[!UICONTROL Nach]** ein. Sie können mehrere Empfängerinnen und Empfänger hinzufügen, indem Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** klicken.
1. [Optional] Fügen Sie die Empfängerinnen und Empfänger für CC und BCC hinzu, indem Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** klicken.
1. Legen Sie die Betreffzeile im Textfeld **[!UICONTROL Betreff]** fest.
1. Fügen Sie eine E-Mail-Vorlage hinzu, um die Sendeaktion „E-Mail senden“ zu konfigurieren.
   * Sie können den Pfad zur externen E-Mail-Vorlage angeben, die in Ihren AEM-Assets gespeichert ist, indem Sie die Option **[!UICONTROL Externer Vorlagenpfad]** verwenden.
   * Sie können auch eine benutzerdefinierte E-Mail-Vorlage für die Formularübermittlung im Textfeld **[!UICONTROL E-Mail-Vorlage]** hinzufügen.
1. [Optional] Die Sendeaktion **[!UICONTROL E-Mail senden]** bietet die Möglichkeit, Anhänge und ein [Datensatzdokument (Document of Record, DoR)](generate-document-of-record-core-components.md) in die E-Mail aufzunehmen.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

## Best Practices {#best-practices}

* Es wird empfohlen, den E-Mail-Inhalt klar und prägnant zu halten. Benutzerinnen und Benutzer sollten den Zweck der E-Mail verstehen und wissen, welche Maßnahmen sie ergreifen müssen.
* Es ist wichtig, dass alle Formularfelder eindeutige Elementnamen haben, auch wenn sie in verschiedenen Bereichen innerhalb eines adaptiven Formulars platziert werden.
* Bei der Verwendung von AEM as a Cloud Service ist eine Verschlüsselung für ausgehendene E-Mails erforderlich. Die Funktion für ausgehende E-Mails ist standardmäßig deaktiviert. Senden Sie zur Aktivierung ein Support-Ticket, um [Zugriff anzufordern](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=de#sending-email).


## Ähnliche Artikel

{{af-submit-action}}
