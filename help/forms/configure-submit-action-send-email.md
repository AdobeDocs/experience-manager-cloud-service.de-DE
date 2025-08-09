---
title: Senden einer E-Mail bei Übermittlung eines adaptiven Formulars
description: Erkunden Sie den Prozess zum Einrichten von E-Mail-Benachrichtigungen beim Senden eines adaptiven Formulars.
keywords: So senden Sie eine E-Mail für ein adaptives Formular, E-Mail-Übermittlungsaktion, E-Mail für adaptive Formulare, E-Mail für Formularübermittlung, E-Mail-Anleitung senden
feature: Adaptive Forms, Core Components, Foundation Components, Edge Delivery Services
exl-id: 70386e57-345b-4edb-97f1-3fd52ea9ff4f
role: User, Developer
source-git-commit: 44a8d5d5fdd2919d6d170638c7b5819c898dcefe
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 84%

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

>[!BEGINTABS]

>[!TAB Foundation-Komponente]

So konfigurieren Sie eine Übermittlungsaktion „E-Mail senden“ für die Foundation-Komponente:

1. Öffnen Sie das adaptive Formular zur Bearbeitung und navigieren Sie zum Abschnitt **[!UICONTROL Übermittlung]** der Eigenschaften des Containers für adaptive Formulare.
1. Wählen Sie **[!UICONTROL E-Mail senden]** aus der Dropdown-Liste **[!UICONTROL Übermittlungsaktion]** aus.

   ![Aktionskonfiguration von „E-Mail senden“](/help/forms/assets/send-email-fc.png)

1. Geben Sie die E-Mail-ID der Absenderin bzw. des Absenders im Textfeld **[!UICONTROL Von]** ein.
1. Fügen Sie die E-Mail-ID der der Empfängerin bzw. des Empfängers  im Textfeld **[!UICONTROL Nach]** ein. Sie können mehrere Empfängerinnen und Empfänger hinzufügen, indem Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** klicken.
1. [Optional] Fügen Sie die Empfängerinnen und Empfänger für CC und BCC hinzu, indem Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** klicken.
1. Legen Sie die Betreffzeile im Textfeld **[!UICONTROL Betreff]** fest.
1. Fügen Sie eine E-Mail-Vorlage hinzu, um die Sendeaktion „E-Mail senden“ zu konfigurieren.
   * Sie können den Pfad zur externen E-Mail-Vorlage angeben, die in Ihren AEM-Assets gespeichert ist, indem Sie die Option **[!UICONTROL Externer Vorlagenpfad]** verwenden.
   * Sie können auch eine benutzerdefinierte E-Mail-Vorlage für die Formularübermittlung im Textfeld **[!UICONTROL E-Mail-Vorlage]** hinzufügen.
1. [Optional] Die Sendeaktion **[!UICONTROL E-Mail senden]** bietet die Möglichkeit, Anhänge und ein [Datensatzdokument (Document of Record, DoR)](generate-document-of-record-core-components.md) in die E-Mail aufzunehmen.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

>[!TAB Kernkomponente]

So konfigurieren Sie die Übermittlungsaktion E-Mail senden für die Kernkomponente:

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

>[!TAB Universeller Editor]

So konfigurieren Sie die Übermittlungsaktion E-Mail senden im universellen Editor:

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Klicken Sie im Editor **die Erweiterung**Formulareigenschaften bearbeiten“.
Das **Formulareigenschaften** wird angezeigt.

   >[!NOTE]
   >
   > * Wenn das Symbol **Formulareigenschaften bearbeiten** in der Benutzeroberfläche des universellen Editors nicht angezeigt wird, aktivieren Sie die Erweiterung **Formulareigenschaften bearbeiten** in der Extension Manager.
   > * Informationen zum Aktivieren oder Deaktivieren von Erweiterungen im universellen Editor finden [ im Artikel ](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)Extension Manager-Feature-Highlights}.


1. Klicken Sie auf **Übermittlung** und wählen Sie **[!UICONTROL E-Mail senden]** Übermittlungsaktion aus.

   ![Universeller E-Mail-Editor senden](/help/forms/assets/send-email-ue.png)

1. Geben Sie die E-Mail-ID der Absenderin bzw. des Absenders im Textfeld **[!UICONTROL Von]** ein.
1. Fügen Sie die E-Mail-ID der der Empfängerin bzw. des Empfängers  im Textfeld **[!UICONTROL Nach]** ein. Sie können mehrere Empfängerinnen und Empfänger hinzufügen, indem Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** klicken.
1. [Optional] Fügen Sie die Empfängerinnen und Empfänger für CC und BCC hinzu, indem Sie auf die Schaltfläche **[!UICONTROL Hinzufügen]** klicken.
1. Legen Sie die Betreffzeile im Textfeld **[!UICONTROL Betreff]** fest.
1. Fügen Sie eine E-Mail-Vorlage hinzu, um die Sendeaktion „E-Mail senden“ zu konfigurieren.
   * Sie können den Pfad zur externen E-Mail-Vorlage angeben, die in Ihren AEM-Assets gespeichert ist, indem Sie die Option **[!UICONTROL Externer Vorlagenpfad]** verwenden.
   * Sie können auch eine benutzerdefinierte E-Mail-Vorlage für die Formularübermittlung im Textfeld **[!UICONTROL E-Mail-Vorlage]** hinzufügen.
1. [Optional] Die Sendeaktion **[!UICONTROL E-Mail senden]** bietet die Möglichkeit, Anhänge und ein [Datensatzdokument (Document of Record, DoR)](generate-document-of-record-core-components.md) in die E-Mail aufzunehmen.
1. Klicken Sie **[!UICONTROL Speichern und schließen]**.

>[!ENDTABS]

## Best Practices {#best-practices}

* Es wird empfohlen, den E-Mail-Inhalt klar und prägnant zu halten. Benutzerinnen und Benutzer sollten den Zweck der E-Mail verstehen und wissen, welche Maßnahmen sie ergreifen müssen.
* Es ist wichtig, dass alle Formularfelder eindeutige Elementnamen haben, auch wenn sie in verschiedenen Bereichen innerhalb eines adaptiven Formulars platziert werden.
* Bei der Verwendung von AEM as a Cloud Service ist eine Verschlüsselung für ausgehendene E-Mails erforderlich. Die Funktion für ausgehende E-Mails ist standardmäßig deaktiviert. Senden Sie zur Aktivierung ein Support-Ticket, um [Zugriff anzufordern](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=de#sending-email).

## Ähnliche Artikel

{{af-submit-action}}
