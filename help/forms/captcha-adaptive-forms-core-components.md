---
title: Verwenden von Google reCAPTCHA in einem adaptiven AEM-Formular
description: Mit dem Google reCAPTCHA-Dienst können Sie die Formularsicherheit verbessern. Schrittweise Anleitung enthalten!
topic-tags: Adaptive Forms, author
keywords: Google reCAPTCHA-Dienst, adaptive Formulare, CAPTCHA-Herausforderung, Bot-Prävention, Kernkomponenten, Formularübermittlungssicherheit, Spam-Prävention für Formulare
feature: Adaptive Forms, Core Components
exl-id: d116f979-efb6-4fac-8202-89afd1037b2c
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: ht
source-wordcount: '939'
ht-degree: 100%

---

# Verwenden von Google reCAPTCHA in einem adaptiven AEM-Formular, das auf Kernkomponenten basiert {#using-reCAPTCHA-in-adaptive-forms}

| Gilt für | Artikel-Link |
| -------- | ---------------------------- |
| Auf Kernkomponenten basierendes adaptives Formular | Dieser Artikel |
| Auf Foundation-Komponenten basierendes adaptives Formular | [Hier klicken](/help/forms/captcha-adaptive-forms.md) |

CAPTCHA („Completely Automated Public Turing test to tell Computers and Humans Apart“ – „vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen“) ist ein Programm, das bei Onlinetransaktionen eingesetzt wird, um zwischen Menschen und Bots oder automatisierten Programmen zu unterscheiden. Es stellt eine herausfordernde Aufgabe und bewertet die Benutzerantwort, um festzustellen, ob es sich um einen Menschen oder einen Bot handelt, der mit der Site interagiert. Dabei wird verhindert, dass der Benutzer fortfährt, wenn der Test fehlschlägt, wodurch Onlinetransaktionen sicherer werden, da Bots keinen Spam senden oder andere bösartige Zwecke verfolgen können.

AEM Forms as a Cloud Service unterstützt die folgenden CAPTCHA-Lösungen:

* [Google reCAPTCHA](#connect-your-aem-forms-environment-with-recaptcha-service-by-google)
* [Cloudflare Turnstile](/help/forms/integrate-adaptive-forms-turnstile-core-components.md)
* [hCaptcha](/help/forms/integrate-adaptive-forms-hcaptcha-core-components.md)


## Verbinden Ihrer AEM Forms-Umgebung mit dem reCAPTCHA-Dienst von Google {#connect-your-forms-environment-with-recaptcha-service-by-google}

Formularautorinnen und -autoren können den reCAPTCHA-Service von Google nutzen, um reCAPTCHA in adaptive Formulare zu implementieren. Er bietet erweiterte reCAPTCHA-Funktionen zum Schutz Ihrer Site. Weitere Informationen zur Funktionsweise von reCAPTCHA finden Sie unter [Google reCAPTCHA](https://developers.google.com/recaptcha/). [!DNL AEM Forms] as a [!DNL Cloud Service] unterstützt Google reCAPTCHA v2 in adaptiven Formularen. Sie können es verwenden, um eine CAPTCHA-Herausforderung bei der Formularübermittlung zu stellen. Verbinden Ihrer AEM Forms-Umgebung mit dem reCAPTCHA-Dienst von Google

1. Rufen Sie ein [reCAPTCHA-API-Schlüsselpaar](https://www.google.com/recaptcha/admin) von Google ab. Er enthält einen **Site-Schlüssel** und einen **geheimen Schlüssel**.

   ![Erstellen der Google reCAPTCHA-Konfiguration der Website von Google zum Abrufen von reCAPTCHA-Schlüsseln](/help/forms/assets/google-captcha.gif)
1. Erstellen Sie einen Konfigurations-Container in Ihrer AEM Forms as a Cloud Service-Umgebung. Ein Konfigurations-Container enthält Cloud-Konfigurationen, mit denen AEM mit externen Diensten verbunden wird. So erstellen und konfigurieren Sie einen Konfigurations-Container zum Verbinden Ihrer AEM Forms-Umgebung mit dem reCAPTCHA-Dienst von Google:
   1. Öffnen Sie Ihre AEM Forms as a Cloud Service-Instanz.
   1. Wählen Sie **[!UICONTROL „Tools“ > „Allgemein“ > „Konfigurations-Browser“]**. Im Konfigurations-Browser haben Sie folgende Möglichkeiten:
   1. Wählen Sie einen vorhandenen Ordner aus oder erstellen Sie einen Ordner. Sie können einen Ordner erstellen und die Cloud-Konfigurationsoption dafür aktivieren oder die Option „Cloud-Konfigurationen“ für einen vorhandenen Ordner aktivieren:

      * Erstellen eines Ordners und Aktivieren der entsprechenden Cloud-Konfigurationsoption:
         1. Klicken Sie im Konfigurations-Browser auf **[!UICONTROL Erstellen]**.
         1. Geben Sie im Dialogfeld „Konfiguration erstellen“ einen Namen und Titel an und wählen Sie die Option **[!UICONTROL Cloud-Konfigurationen]** aus.
         1. Klicken Sie auf **[!UICONTROL Erstellen]**.
      * So aktivieren Sie die Option „Cloud-Konfigurationen“ für einen vorhandenen Ordner:
         1. Wählen Sie im Konfigurations-Browser den Ordner aus und wählen Sie **[!UICONTROL Eigenschaften]**.
         1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloud-Konfigurationen]**.
         1. Wählen Sie **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

1. Konfigurieren des Cloud-Service:
   1. Navigieren Sie in Ihrer AEM-Autoreninstanz zu ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud-Services]** und wählen Sie **[!UICONTROL reCAPTCHA]**.
   1. Wählen Sie einen Konfigurations-Container aus, der im vorherigen Abschnitt erstellt oder aktualisiert wurde. Wählen Sie **[!UICONTROL Erstellen]** aus.
   1. Geben Sie **[!UICONTROL Titel]**, **[!UICONTROL Namen]**, **[!UICONTROL Site-Schlüssel]** und den **[!UICONTROL geheimen Schlüssel]** für den reCAPTCHA-Dienst (abgerufen in Schritt 1) an. Wählen Sie **[!UICONTROL Erstellen]** aus.

   ![Konfigurieren des Cloud Service für die Verbindung Ihrer AEM Forms-Umgebung mit dem reCAPTCHA-Dienst von Google](/help/forms/assets/captcha-configuration.gif)

   Sobald der reCAPTCHA-Dienst konfiguriert ist, kann er in adaptiven Formularen verwendet werden. Weitere Informationen finden Sie unter [Verwenden von Google reCAPTCHA in einem adaptiven Formular](#using-reCAPTCHA).

## Verwenden von Google reCAPTCHA in einem adaptiven Formular {#using-reCAPTCHA}

Verwenden von reCAPTCHA in adaptiven Formularen:

1. Öffnen Sie Ihre AEM Forms as a Cloud Service-Instanz.
1. Gehen Sie zu **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie ein adaptives Formular aus und wählen Sie **[!UICONTROL Eigenschaften]**. Wählen Sie für die Option **[!UICONTROL Konfigurations-Container]** den Konfigurations-Container aus, der die Cloud-Konfiguration enthält, die AEM Forms mit dem reCAPTCHA-Dienst von Google verbindet, und wählen Sie **[!UICONTROL Speichern und schließen]**.

   Wenn Sie über keinen solchen Konfigurations-Container verfügen, erfahren Sie im Abschnitt [Verbinden Ihrer AEM Forms-Umgebung mit dem reCAPTCHA-Dienst von Google](#connect-your-forms-environment-with-recaptcha-service-by-google), wie Sie einen solchen Konfigurations-Container erstellen.

   ![Auswählen eines Konfigurations-Containers](/help/forms/assets/captcha-properties.png)

1. Wählen Sie ein adaptives Formular aus und wählen Sie dann **[!UICONTROL Bearbeiten]**. Das adaptive Formular wird im Editor für adaptive Formulare geöffnet.
1. Ziehen Sie im Komponenten-Browser die Komponente **[!UICONTROL reCAPTCHA für adaptive Formulare]** per Drag-and-Drop auf das adaptive Formular.

   Die reCAPTCHA-Validierung von Google ist zeitabhängig und läuft nach einigen Minuten ab. Daher empfiehlt Adobe, die Komponente **[!UICONTROL reCAPTCHA für adaptive Formulare]** direkt vor der Schaltfläche **[!UICONTROL Senden]** zu platzieren.

1. Wählen Sie die Komponente **[!UICONTROL reCAPTCHA für adaptive Formulare]** aus und wählen Sie dann das Symbol „Eigenschaften“ ![Eigenschaften-Symbol](assets/configure-icon.svg). Dadurch wird das Dialogfeld „Eigenschaften“ geöffnet. Geben Sie die folgenden obligatorischen Eigenschaften an:
   * **[!UICONTROL Name]:** Sie können sowohl im Formular als auch im Regeleditor eine Formularkomponente leicht mit ihrem eindeutigen Namen identifizieren. Der Name darf jedoch keine Leerzeichen oder Sonderzeichen enthalten.
   * **[!UICONTROL CAPTCHA-Konfiguration]:** Wählen Sie eine Cloud-Konfiguration aus, die zur Anzeige des Google reCAPTCHA-Dialogfelds für das Formular konfiguriert ist. Es kann sein, dass Sie für ähnliche Zwecke über mehrere Cloud-Konfigurationen in Ihrer Umgebung verfügen. Wählen Sie den Dienst daher sorgfältig aus. Wenn kein Dienst aufgeführt ist, lesen Sie [Verbinden Ihrer AEM Forms-Umgebung mit dem reCAPTCHA-Dienst von Google](#connect-your-forms-environment-with-recaptcha-service-by-google), um zu erfahren, wie Sie einen Cloud Service erstellen, der Ihre AEM Forms-Umgebung mit dem reCAPTCHA-Dienst von Google verbindet.
   * **Captcha-Größe:** Sie können die Anzeigegröße des Dialogfelds für die Google reCAPTCHA-Herausforderung auswählen. Verwenden Sie die Option **[!UICONTROL Kompakt]** zur Anzeige eines kleinen und die Option **[!UICONTROL Normal]**  zur Anzeige eines relativ großen Dialogfelds für die Google reCAPTCHA-Herausforderung.

1. Wählen Sie **[!UICONTROL Fertig]**.

   Jetzt wird **geschützt durch reCAPTCHA** in Ihrem adaptiven Formular angezeigt. Dies wird in allen adaptiven Formularen angezeigt, die für die Verwendung des Google reCAPTCHA-Dienstes konfiguriert sind.

   Jetzt sind nur legitime Formulare zur Übermittlung zulässig, bei denen die Person, die das Formular ausfüllt, die vom Google-reCAPTCHA-Dienst ausgehende Herausforderung erfolgreich löst.
   ![Badge „Durch Google geschützt mit reCAPTCHA“](/help/forms/assets/google-recaptcha-v2.png)

<!--
### Show or hide CAPTCHA component based on rules {#show-hide-captcha}

You can select to show or hide the CAPTCHA component based on rules that you apply on a component in an Adaptive Form. Select the component, select ![edit rules](assets/edit-rules-icon.svg), and select **[!UICONTROL Create]** to create a rule. For more information on creating rules, see [Rule Editor](rule-editor.md).

For example, the CAPTCHA component must display in an Adaptive Form only if the Currency Value field in the form has a value of more than 25000.

Select the **[!UICONTROL Currency Value]** field in the form and create the following rules:

![Show or hide rules](assets/rules-show-hide-captcha.png)

   >[!NOTE]
   >
   > When you select a reCAPTCHA v2 configuration and the size is set to [!UICONTROL Invisible], the show/hide option remains disabled.

   -->

## Häufig gestellte Fragen

**F: Kann ich mehr als eine Captcha-Komponente in einem adaptiven Formular verwenden?**
**Antwort:** Die Verwendung von mehr als einer Captcha-Komponente in einem adaptiven Formular wird nicht unterstützt. Außerdem wird davon abgeraten, die Captcha-Komponente in einem Fragment oder einem Bereich zu verwenden, das bzw. der für verzögertes Laden markiert ist.

## Siehe auch {#see-also}

{{see-also}}