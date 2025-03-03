---
title: Verwenden von reCAPTCHA mit Edge Delivery Services für AEM Forms as a Cloud Service
description: Verwenden von Google reCAPTCHA in einem Formular für Edge Delivery Services für AEM Forms
feature: Edge Delivery Services
keywords: reCAPTCHA in Formularen, Verwenden von reCAPTCHA im universellen Editor, Hinzufügen von reCAPTCHA in Formularen
role: Admin, Architect, Developer
exl-id: 1f28bd13-133f-487e-8b01-334be7c08a3f
source-git-commit: 0c6f024594e1b1fd98174914d2c0714dffecb241
workflow-type: tm+mt
source-wordcount: '1273'
ht-degree: 96%

---


# Verwenden von reCAPTCHA beim WYSIWYG-Authoring

<span class="preview"> Diese Funktion ist über das Early-Access-Programm verfügbar. Um den Zugriff anzufordern, senden Sie eine E-Mail von Ihrer offiziellen Adresse an <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a> mit dem Namen Ihrer GitHub-Organisation und dem Repository-Namen. Wenn die Repository-URL beispielsweise https://github.com/adobe/abc lautet, lautet der Organisationsname adobe und der Repository-Name abc.</span>


CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart, vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen) ist ein beliebtes Tool zum Schutz von Websites vor betrügerischen Aktivitäten, Spam und Missbrauch.

Nehmen wir beispielsweise ein Formular, das die Steuer auf der Grundlage zusätzlicher Abzüge und des Steuersatzes berechnet. In solchen Fällen besteht die Gefahr, dass böswillige Personen das Formular für Zwecke wie den Versand von Phishing-E-Mails oder die Überflutung mit irrelevanten oder schädlichen Inhalten durch Spambots nutzen. Die Integration von CAPTCHA bietet zusätzliche Sicherheit, indem überprüft wird, ob die Einreichungen von echten Personen stammen, wodurch Spam-Einträge effektiv minimiert werden.

![Google reCAPTCHA](/help/edge/docs/forms/universal-editor/assets/google-recaptcha.png)

In Edge Delivery Services Forms ermöglicht Ihnen der Formularblock, [Google reCAPTCHA mit Formularen zu verbinden](#connect-forms-with-recaptcha-service-by-google), um zwischen Menschen und Bots zu unterscheiden. Dazu wird die Komponente **CAPTCHA(Invisible)** verwendet. Durch diese Funktion können Formulare vor Spam und Missbrauch geschützt werden.

## Verbinden von Formularen mit dem reCAPTCHA-Service von Google

Sie können Edge Delivery Services Forms erstellen und den von Google bereitgestellten reCAPTCHA-Service implementieren. Je nach Bedarf können Sie einen der folgenden reCAPTCHA-Services für Ihre Edge Delivery Services Forms konfigurieren:

* [reCAPTCHA Enterprise](#configure-recaptcha-enterprise)
* [reCAPTCHA](#configure-recaptcha)

>[!NOTE]
>
> Weitere Informationen zur Funktionsweise von reCAPTCHA finden Sie unter [Google reCAPTCHA](https://developers.google.com/recaptcha/).

### Konfigurieren von reCAPTCHA Enterprise

reCAPTCHA Enterprise ist ein Premium-Service zur Betrugserkennung und -prävention auf Unternehmensniveau, der von Google angeboten wird. Er baut auf der Grundlage von reCAPTCHA auf (punktzahlbasiert), bietet jedoch zusätzliche Funktionen, Skalierbarkeit und Anpassung, um die komplexen Anforderungen von Unternehmen zu erfüllen.

#### Bevor Sie beginnen

Vor dem Konfigurieren von Google reCAPTCHA Enterprise für Edge Delivery Services Forms müssen Sie die folgenden Schritte ausgeführt haben:

1. Erstellen oder wählen Sie ein [Google Cloud-Projekt](https://cloud.google.com/recaptcha/docs/prepare-environment#before-you-begin) und rufen Sie die [Projekt-ID](https://support.google.com/googleapi/answer/7014113?hl=en#:~:text=To%20locate%20your%20project%20ID,a%20member%20of%20are%20displayed) ab.

1. [Aktivieren Sie die reCAPTCHA Enterprise-API](https://cloud.google.com/recaptcha/docs/prepare-environment#enable-api) für Ihr Google Cloud-Projekt und [erstellen Sie einen API-Schlüssel](https://console.cloud.google.com/apis/credentials).

1. Erstellen Sie einen [Site-Schlüssel für Ihr Google Cloud-Projekt](https://console.cloud.google.com/security/recaptcha) und kopieren Sie den Site-Schlüssel.

Sobald Sie über diese Anmeldeinformationen verfügen, können Sie reCAPTCHA Enterprise für Ihre Formulare konfigurieren:

1. [Erstellen eines Cloud-Konfigurations-Containers](#1-create-cloud-configuration-container)
1. [Erstellen der Cloud-Service-Konfiguration für reCAPTCHA Enterprise](#2-create-the-cloud-service-configuration-for-recaptcha-enterprise)

#### 1. Erstellen eines Cloud-Konfigurations-Containers

Um den Cloud-Konfigurations-Container zu erstellen, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Ihrer Autoreninstanz an. 
1. Wechseln Sie zu **[!UICONTROL Tools]** ![Tools-1](/help/forms/assets/tools-1.png) > **[!UICONTROL Allgemein]** > **[!UICONTROL Konfigurations-Browser]**.

   ![Cloud-Konfigurations-Container](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)

1. Navigieren Sie im **[!UICONTROL Konfigurations-Browser]** zu Ihrem Formular und wählen Sie **[!UICONTROL Eigenschaften]** aus.

   ![Eigenschaften der Cloud-Konfiguration](/help/edge/docs/forms/universal-editor/assets/general-configuration-properties.png)

1. Aktivieren Sie im Dialogfeld **[!UICONTROL Konfigurationseigenschaften]** die Option **[!UICONTROL Cloud-Konfigurationen]**.

1. Wählen Sie **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

   ![Aktivieren der Eigenschaften der Cloud-Konfiguration](/help/edge/docs/forms/universal-editor/assets/enable-cloud-configurations.png)
&quot;
Nachdem Sie den Cloud-Konfigurations-Container erstellt haben, veröffentlichen Sie ihn.

   ![Veröffentlichen der Cloud-Konfiguration](/help/edge/docs/forms/universal-editor/assets/publish-cloud-configuration.png)

#### 2. Erstellen der Cloud-Service-Konfiguration für reCAPTCHA Enterprise

Um die Cloud-Service-Konfiguration für reCAPTCHA Enterprise zu erstellen, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Ihrer Autoreninstanz an. 
1. Navigieren Sie zu **[!UICONTROL Tools]** ![Tools-1](/help/forms/assets/tools-1.png) > **[!UICONTROL Cloud-Services]** > **[!UICONTROL reCAPTCHA]**.

   ![reCAPTCHA-Cloud-Konfiguration](/help/edge/docs/forms/universal-editor/assets/recaptcha-cloud-configuration.png)

   Das Dialogfeld **Konfigurationen** wird geöffnet.

1. Navigieren Sie zu Ihrem Formular und wählen Sie **[!UICONTROL Erstellen]** aus.

   ![CAPTCHA-Konfiguration](/help/edge/docs/forms/universal-editor/assets/create-captcha-confguration.png)

   Das Dialogfeld **[!UICONTROL reCAPTCHA-Konfiguration erstellen]** wird geöffnet.

   ![reCAPTCHA Enterprise](/help/edge/docs/forms/universal-editor/assets/recaptcha-enterprise.png)

1. Wählen Sie als Version [!DNL ReCAPTCHA Enterprise] aus und geben Sie Titel, Namen, Projekt-ID, Site-Schlüssel und API-Schlüssel an.

   >[!NOTE]
   >
   > Sie können die Projekt-ID, den Site-Schlüssel und den API-Schlüssel aus dem Abschnitt [Bevor Sie beginnen](#before-you-start) für reCAPTCHA Enterprise entnehmen.

1. Wählen Sie als **[!UICONTROL Schlüsseltyp]** die Option **Punktzahlbasierter Site-Schlüssel** aus.
1. Geben Sie einen [Schwellenwert im Bereich von 0 bis 1](https://cloud.google.com/recaptcha/docs/interpret-assessment-website#interpret_scores) an. Werte, die größer oder gleich den Schwellenwerten sind, kennzeichnen menschliche Interaktionen, ansonsten wird von einer Bot-Interaktion ausgegangen.
1. Wählen Sie **[!UICONTROL Erstellen]** aus, um die Cloud-Service-Konfiguration zu erstellen.

   Nachdem Sie die reCAPTCHA-Cloud-Konfiguration erstellt haben, veröffentlichen Sie sie.

   ![Veröffentlichen der reCAPTCHA-Konfiguration](/help/edge/docs/forms/universal-editor/assets/publisg-recaptcha-configuration.png)

Sie können jetzt ein Formular erstellen oder bearbeiten und die reCAPTCHA-Komponente mithilfe von WYSIWYG-Authoring hinzufügen. Detaillierte Anweisungen zur Integration von Google reCAPTCHA in Ihr Formular finden Sie unter [Verwenden von reCAPTCHA in Ihrem Formular](#use-recaptcha-in-your-form).

## Konfigurieren von reCAPTCHA

reCAPTCHA ist ein kostenloser Service von Google, mit dem Websites missbräuchlichen Traffic, einschließlich Bots und Spam, erkennen und verhindern können. Es unterstützt eine punktzahlbasierte Version, die im Hintergrund arbeitet, und weist jeder Benutzerinteraktion eine Risikobewertung (von 0,0 bis 1,0) zu. Werte, die größer oder gleich den Schwellenwerten sind, kennzeichnen menschliche Interaktionen, ansonsten wird von einer Bot-Interaktion ausgegangen.

#### Voraussetzungen

Bevor Sie Google reCAPTCHA für Edge Delivery Services Forms konfigurieren, rufen Sie das [reCAPTCHA-API-Schlüsselpaar von der Google-Konsole ab](https://www.google.com/recaptcha/admin). Das Paar enthält einen Site-Schlüssel und einen geheimen Schlüssel.

>[!NOTE]
>
> * Edge Delivery Services Forms unterstützt nur die **reCAPTCHA-punktzahlbasierte** Version.

Sobald Sie über das API-Schlüsselpaar verfügen, können Sie reCAPTCHA für Ihre Formulare konfigurieren:

1. [Erstellen eines Cloud-Konfigurations-Containers](#1-create-cloud-configuration-container-1)
1. [Erstellen der Cloud-Service-Konfiguration für reCAPTCHA](#2-create-the-cloud-service-configuration-for-recaptcha)

#### 1. Erstellen eines Cloud-Konfigurations-Containers

Um den Cloud-Konfigurations-Container zu erstellen, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Ihrer Autoreninstanz an. 
1. Wechseln Sie zu **[!UICONTROL Tools]** ![Tools-1](/help/forms/assets/tools-1.png) > **[!UICONTROL Allgemein]** > **[!UICONTROL Konfigurations-Browser]**.

   ![Cloud-Konfigurations-Container](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)

1. Navigieren Sie im **[!UICONTROL Konfigurations-Browser]** zu Ihrem Formular und wählen Sie **[!UICONTROL Eigenschaften]** aus.

   ![Eigenschaften der Cloud-Konfiguration](/help/edge/docs/forms/universal-editor/assets/general-configuration-properties.png)

1. Aktivieren Sie im Dialogfeld **[!UICONTROL Konfigurationseigenschaften]** die Option **[!UICONTROL Cloud-Konfigurationen]**.

1. Wählen Sie **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

   ![Aktivieren der Eigenschaften der Cloud-Konfiguration](/help/edge/docs/forms/universal-editor/assets/enable-cloud-configurations.png)

   Nachdem Sie den Cloud-Konfigurations-Container erstellt haben, veröffentlichen Sie ihn.

   ![Veröffentlichen der Cloud-Konfiguration](/help/edge/docs/forms/universal-editor/assets/publish-cloud-configuration.png)

#### 2. Erstellen der Cloud-Service-Konfiguration für reCAPTCHA

Um die Cloud-Service-Konfiguration für reCAPTCHA zu erstellen, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Ihrer Autoreninstanz an. 
1. Navigieren Sie zu **[!UICONTROL Tools]** ![Tools-1](/help/forms/assets/tools-1.png) > **[!UICONTROL Cloud-Services]** > **[!UICONTROL reCAPTCHA]**.

   ![reCAPTCHA-Cloud-Konfiguration](/help/edge/docs/forms/universal-editor/assets/recaptcha-cloud-configuration.png)

   Das Dialogfeld **Konfigurationen** wird geöffnet.

1. Navigieren Sie zu Ihrem Formular und wählen Sie **[!UICONTROL Erstellen]** aus.

   ![CAPTCHA-Konfiguration](/help/edge/docs/forms/universal-editor/assets/create-captcha-confguration.png)

   Das Dialogfeld **[!UICONTROL reCAPTCHA-Konfiguration erstellen]** wird geöffnet.

   ![reCAPTCHA Enterprise](/help/edge/docs/forms/universal-editor/assets/recaptcha.png)

1. Wählen Sie als Version [!DNL ReCAPTCHA v2] aus und geben Sie Titel und Namen an.
1. Geben Sie Site-Schlüssel und geheimen Schlüssel an.

   >[!NOTE]
   >
   > Sie können den Site-Schlüssel und den geheimen Schlüssel aus dem Abschnitt [Voraussetzungen](#before-you-begin) für reCAPTCHA entnehmen.

1. Wählen Sie **[!UICONTROL Erstellen]** aus, um die Cloud-Service-Konfiguration zu erstellen.

   Nachdem Sie die reCAPTCHA-Cloud-Konfiguration erstellt haben, veröffentlichen Sie sie.

   ![Veröffentlichen der reCAPTCHA-Konfiguration](/help/edge/docs/forms/universal-editor/assets/publisg-recaptcha-configuration.png)

Sie können jetzt ein Formular erstellen und bearbeiten und die reCAPTCHA-Komponente mithilfe von WYSIWYG-Authoring hinzufügen. Detaillierte Anweisungen zur Integration von Google reCAPTCHA in Ihr Formular finden Sie unter [Verwenden von reCAPTCHA in Ihrem Formular](#use-recaptcha-in-your-form).

### Verwenden von reCAPTCHA in Ihrem Formular

Um ein Formular zu erstellen und die Komponente „reCAPTCHA (unsichtbar)“ hinzuzufügen, führen Sie die folgenden Schritte aus:

1. Öffnen Sie ein Formular im universellen Editor zur Bearbeitung.
1. Navigieren Sie in der Inhaltsstruktur zum hinzugefügten Abschnitt „Adaptives Formular“.
1. Klicken Sie auf das Symbol **[!UICONTROL Hinzufügen]** und fügen Sie die Komponente **[!UICONTROL Captcha (unsichtbar)]** aus der Liste der **adaptiven Formularkomponenten** hinzu.

   ![Hinzufügen einer reCaptcha-Komponente](/help/edge/docs/forms/universal-editor/assets/add-recaptcha-component.png)

   Sie können die erforderliche adaptive Formularkomponente auch einfach ziehen und ablegen. Der universelle Editor verfügt nämlich über eine intuitive Drag-and-Drop-Funktion.

1. Klicken Sie auf **Veröffentlichen**, um das Formular nach dem Hinzufügen der Komponente **[!UICONTROL Captcha (unsichtbar)]** erneut zu veröffentlichen.

   ![Erneutes Veröffentlichen des Formulars](/help/edge/docs/forms/universal-editor/assets/publish-form.png)

Sie können das Formular mit dem reCAPTCHA-Service jetzt unter der folgenden URL anzeigen:
`https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form-name`.

![Formular mit reCAPTCHA](/help/edge/docs/forms/universal-editor/assets/form-with-recaptcha.png)

## Häufig gestellte Fragen

* **Was passiert, wenn keine reCAPTCHA-Cloud-Konfiguration erstellt wird?**

  **A**: Wenn keine reCAPTCHA-Cloud-Konfiguration erstellt wird, sucht der AEM-Server im globalen Konfigurations-Container nach der reCAPTCHA-Cloud-Konfiguration. Wenn im globalen Konfigurations-Container keine Konfiguration vorhanden ist, gibt der AEM-Server einen Fehler aus.

* **Was passiert, wenn mehrere reCAPTCHA-Cloud-Konfigurationen erstellt werden?**
  **A**: Wenn mehr als eine reCAPTCHA-Cloud-Konfigurationen erstellt wird, wählt das System automatisch die zuerst erstellte reCAPTCHA-Konfiguration aus.

* **Warum sind Modifikationen oder Änderungen an der veröffentlichten URL nicht sichtbar?**
Wenn Modifikationen oder Änderungen an der veröffentlichten URL nicht sichtbar sind, müssen Sie das Formular erneut veröffentlichen, um die Aktualisierungen anzuwenden.

* **Welchen reCAPTCHA-Service unterstützt Edge Delivery Services Forms?**
  **A**: Edge Delivery Services Forms unterstützt nur den punktzahlbasierten reCAPTCHA-Service, der von Google bereitgestellt wird.


## Siehe auch

{{universal-editor-see-also}}

