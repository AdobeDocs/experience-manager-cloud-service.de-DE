---
title: Verwenden von Google reCAPTCHA in einem adaptiven Formular basierend auf Kernkomponenten
description: Verbessern der Formularsicherheit mit dem Google reCAPTCHA-Dienst. Schrittweise Anleitung innen!
topic-tags: Adaptive Forms, author
hide: true
hidefromtoc: true
Keywords: Google reCAPTCHA service, Adaptive Forms, CAPTCHA challenge, Bot prevention, Core Components, Form submission security, Form spam prevention
source-git-commit: 4f2a51502202fba3792cde370180d127f8e17418
workflow-type: tm+mt
source-wordcount: '868'
ht-degree: 13%

---

# Verwenden von reCAPTCHA in Adaptive Forms basierend auf Kernkomponenten {#using-reCAPTCHA-in-adaptive-forms}

CAPTCHA („Completely Automated Public Turing test to tell Computers and Humans Apart“ – „vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen“) ist ein Programm, das bei Onlinetransaktionen eingesetzt wird, um zwischen Menschen und Bots oder automatisierten Programmen zu unterscheiden. Es stellt eine Herausforderung dar und bewertet die Benutzerantwort, um festzustellen, ob es sich um einen Menschen oder einen Bot handelt, der mit der Site interagiert. Dabei wird verhindert, dass der Benutzer fortfährt, wenn der Test fehlschlägt, wodurch Onlinetransaktionen sicherer werden, da Bots keinen Spam senden oder andere bösartige Zwecke verfolgen können.

[!DNL AEM Forms] as a [!DNL Cloud Service] unterstützt Google reCAPTCHA v2 in Adaptive Forms. Sie können es verwenden, um eine CAPTCHA-Herausforderung bei der Formularübermittlung zu stellen. So verwenden Sie reCAPTCHA in einem adaptiven Formular:

1. [Verbinden Ihrer AEM Forms-Umgebung mit dem reCAPTCHA-Dienst von Google](#connect-your-forms-environment-with-recaptcha-service-by-google)
1. [Konfigurieren Sie Ihr adaptives Formular, um die CAPTCHA-Herausforderung bei der Formularübermittlung anzuzeigen](#using-reCAPTCHA)

## Verbinden Ihrer AEM Forms-Umgebung mit dem reCAPTCHA-Dienst von Google {#connect-your-forms-environment-with-recaptcha-service-by-google}

So verbinden Sie Ihre AEM Forms-Umgebung mit dem reCAPTCHA-Dienst von Google

1. Erhalten [reCAPTCHA API-Schlüsselpaar](https://www.google.com/recaptcha/admin) aus Google. Er enthält eine **Site-Schlüssel** und **geheimer Schlüssel**.

   ![Erstellen Sie die Google reCAPTCHA-Konfiguration der Website von Google, um reCAPTCHA-Schlüssel zu erhalten.](/help/forms/assets/google-captcha.gif)
1. Erstellen Sie einen Konfigurations-Container in Ihrer as a Cloud Service AEM Forms-Umgebung. Ein Konfigurations-Container enthält Cloud-Konfigurationen, mit denen AEM mit externen Diensten verbunden werden. So erstellen und konfigurieren Sie einen Konfigurations-Container, um Ihre AEM Forms-Umgebung mit dem reCAPTCHA-Dienst von Google zu verbinden:
   1. Öffnen Sie Ihre as a Cloud Service AEM Forms-Instanz.
   1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurationsbrowser]**. Im Konfigurationsbrowser haben Sie folgende Möglichkeiten:
   1. Wählen Sie einen vorhandenen Ordner aus oder erstellen Sie einen Ordner. Sie haben folgende Möglichkeiten
      * Erstellen Sie einen Ordner und aktivieren Sie dafür die Option Cloud-Konfigurationen :
         1. Klicken Sie im Konfigurationsbrowser auf **[!UICONTROL Erstellen]**.
         1. Geben Sie im Dialogfeld &quot;Konfiguration erstellen&quot;den Namen und den Titel ein und wählen Sie die **[!UICONTROL Cloud-Konfigurationen]** -Option.
         1. Klicken Sie auf **[!UICONTROL Erstellen]**.
            ![Erstellen Sie eine Cloud-Konfiguration, um Ihre AEM Forms-Umgebung mit dem reCAPTCHA-Dienst von Google zu verbinden](/help/forms/assets/create-configuration.png){width="50%"}
      * Aktivieren Sie die Option Cloud-Konfigurationen für einen vorhandenen Ordner:
         1. Wählen Sie im Konfigurationsbrowser den Ordner  aus und tippen Sie auf **[!UICONTROL Eigenschaften]**.
         1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloudkonfigurationen]**.
         1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

1. Konfigurieren des Cloud Service:
   1. Wechseln Sie in Ihrer AEM-Autoreninstanz zu ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Services]** und tippen **[!UICONTROL reCAPTCHA]**.
   1. Wählen Sie einen Konfigurations-Container aus, der im vorherigen Abschnitt erstellt oder aktualisiert wurde. Tippen Sie auf **[!UICONTROL Erstellen]**.
   1. Angeben **[!UICONTROL Titel]**, **[!UICONTROL Name]**, **[!UICONTROL Site-Schlüssel]**, und **[!UICONTROL Geheimer Schlüssel]** für den reCAPTCHA-Dienst (abgerufen in Schritt 1). Tippen Sie auf **[!UICONTROL Erstellen]**.
      ![Konfigurieren des Cloud Service für die Verbindung Ihrer AEM Forms-Umgebung mit dem reCAPTCHA-Dienst von Google](/help/forms/assets/captcha-configuration.gif)

   Sobald der reCAPTCHA-Dienst konfiguriert ist, steht er zur Verwendung in einem adaptiven Formular zur Verfügung. Weitere Informationen finden Sie unter [Verwenden von Google reCAPTCHA in einem adaptiven Formular](#using-reCAPTCHA).


## Verwenden von Google reCAPTCHA in einem adaptiven Formular {#using-reCAPTCHA}

So verwenden Sie reCAPTCHA in Adaptive Forms:

1. Öffnen Sie Ihre as a Cloud Service AEM Forms-Instanz.
1. Gehen Sie zu **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie eine adaptive Forms aus und tippen Sie auf **[!UICONTROL Eigenschaften]**. Für **[!UICONTROL Konfigurations-Container]** Wählen Sie den Konfigurationscontainer aus, der die Cloud-Konfiguration enthält, die AEM Forms mit dem reCAPTCHA-Dienst von Google verbindet, und tippen Sie auf **[!UICONTROL Speichern und schließen]**.

   Wenn Sie keinen solchen Konfigurations-Container haben, finden Sie weitere Informationen im Abschnitt . [Verbinden Ihrer AEM Forms-Umgebung mit dem reCAPTCHA-Dienst von Google](#connect-your-forms-environment-with-recaptcha-service-by-google) , um zu erfahren, wie Sie einen solchen Konfigurations-Container erstellen.

   ![Konfigurationscontainer auswählen](/help/forms/assets/captcha-properties.png)
1. Wählen Sie eine adaptive Forms aus und tippen Sie auf **[!UICONTROL Bearbeiten]**. Das adaptive Formular wird im adaptiven Forms-Editor geöffnet.
1. Ziehen Sie aus dem Komponenten-Browser die **[!UICONTROL Adaptives Formular reCAPTCHA]** auf das adaptive Formular.

   Die reCAPTCHA-Validierung von Google ist zeitabhängig und läuft in etwa einer Minute ab. Daher empfiehlt Adobe, die **[!UICONTROL Adaptives Formular reCAPTCHA]** -Komponente direkt vor dem **[!UICONTROL Einsenden]** Schaltfläche.

1. Wählen Sie die **[!UICONTROL Adaptives Formular reCAPTCHA]** Komponente und tippen Sie auf die Eigenschaften ![Eigenschaften-Symbol](assets/configure-icon.svg) Symbol. Dadurch wird das Dialogfeld &quot;Eigenschaften&quot;geöffnet. Geben Sie die folgenden obligatorischen Eigenschaften an:
   * **[!UICONTROL Name]:** Sie können eine Formularkomponente sowohl im Formular als auch im Regeleditor leicht mit ihrem eindeutigen Namen identifizieren, der Name darf jedoch keine Leerzeichen oder Sonderzeichen enthalten.
   * **[!UICONTROL CAPTCHA-Konfiguration]:** Wählen Sie eine Cloud-Konfiguration aus, die zur Anzeige des Google reCAPTCHA-Dialogfelds für das Formular konfiguriert ist. Sie können für ähnliche Zwecke über mehrere Cloud-Konfigurationen in Ihrer Umgebung verfügen. Wählen Sie also den Dienst sorgfältig aus. Wenn kein Dienst aufgelistet ist, lesen Sie [Verbinden Ihrer AEM Forms-Umgebung mit dem reCAPTCHA-Dienst von Google](#connect-your-forms-environment-with-recaptcha-service-by-google) Erfahren Sie, wie Sie einen Cloud Service erstellen, der Ihre AEM Forms-Umgebung mit dem reCAPTCHA-Dienst von Google verbindet.
   * **Captcha Size:** Sie können die Anzeigegröße des Google reCAPTCHA-Challenge-Dialogfelds auswählen. Verwenden Sie die **[!UICONTROL Kompakt]** Option zur Anzeige einer kleinen Größe und **[!UICONTROL Normal]** -Option, um ein relativ großes Google reCAPTCHA-Anforderungsdialogfeld anzuzeigen.

1. Tippen Sie auf **[!UICONTROL Fertig]**.

   Nun, die **geschützt durch reCAPTCHA** wird in Ihrem adaptiven Formular angezeigt. Sie wird auf allen adaptiven Forms angezeigt, die für die Verwendung des Google reCAPTCHA-Dienstes konfiguriert sind.

   Jetzt sind nur legitime Formulare zur Übermittlung zulässig, bei denen der Benutzer die vom Google-reCAPTCHA-Dienst ausgehende Herausforderung erfolgreich löscht.
   ![Durch Google geschützt mit reCAPTCHA-Badge](/help/forms/assets/google-recaptcha-v2.png)

<!--
### Show or hide CAPTCHA component based on rules {#show-hide-captcha}

You can select to show or hide the CAPTCHA component based on rules that you apply on a component in an Adaptive Form. Tap the component, select ![edit rules](assets/edit-rules-icon.svg), and tap **[!UICONTROL Create]** to create a rule. For more information on creating rules, see [Rule Editor](rule-editor.md).

For example, the CAPTCHA component must display in an Adaptive Form only if the Currency Value field in the form has a value of more than 25000.

Tap the **[!UICONTROL Currency Value]** field in the form and create the following rules:

![Show or hide rules](assets/rules-show-hide-captcha.png)

   >[!NOTE]
   >
   > When you select a reCAPTCHA v2 configuration and the size is set to [!UICONTROL Invisible], the show/hide option remains disabled.

   -->

## Häufig gestellte Fragen

**F: Kann ich mehrere Captcha-Komponenten in einem adaptiven Formular verwenden?**
**Ans:** Die Verwendung von mehr als einer Captcha-Komponente in einem adaptiven Formular wird nicht unterstützt. Es wird außerdem nicht empfohlen, die Captcha-Komponente in einem Fragment oder einem Bereich zu verwenden, das für verzögertes Laden markiert ist.

