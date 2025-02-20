---
title: Verwenden von reCAPTCHA mit Edge Delivery Services für AEM Forms as a Cloud Service
description: Verwenden von Google reCAPTCHA in einem Formular für Edge Delivery Services für AEM Forms
feature: Edge Delivery Services
keywords: reCAPTCHA in Formularen, Verwendung von reCAPTCHA im universellen Editor, Hinzufügen von reCAPTCHA in Formularen
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
exl-id: 1f28bd13-133f-487e-8b01-334be7c08a3f
source-git-commit: ba42a99e6138616ab6a7564c4bf58400844bdcc4
workflow-type: tm+mt
source-wordcount: '1225'
ht-degree: 13%

---


# Verwenden von reCAPTCHA beim WYSIWYG-Authoring

CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart) ist ein beliebtes Tool zum Schutz von Websites vor betrügerischen Aktivitäten, Spam und Missbrauch.

Nehmen wir zum Beispiel ein Formular, das die Steuer auf der Grundlage zusätzlicher Abzüge und des Steuersatzes berechnet. In solchen Fällen besteht die Gefahr, dass böswillige Personen das Formular für Zwecke wie den Versand von Phishing-E-Mails oder die Überflutung mit irrelevanten oder schädlichen Inhalten durch Spambots nutzen. Die Integration von CAPTCHA bietet zusätzliche Sicherheit, da überprüft wird, ob die Übermittlungen von echten Benutzern stammen, wodurch Spam-Einträge effektiv minimiert werden.

![Google reCAPTCHA](/help/edge/docs/forms/universal-editor/assets/google-recaptcha.png)

In Edge Delivery Services Forms ermöglicht Ihnen der Formularblock die [Verbindung von Google reCAPTCHA mit Formularen](#connect-forms-with-recaptcha-service-by-google) mithilfe der Komponente **CAPTCHA(Invisible)**, um zwischen Menschen und Bots zu unterscheiden. Diese Funktion hilft Autoren, ihre Formulare vor Spam und Missbrauch zu schützen.

## Verbinden von Forms mit dem reCAPTCHA-Service von Google

Sie können Edge Delivery Services Forms erstellen , um den von Google bereitgestellten reCAPTCHA-Service zu implementieren. Je nach Bedarf können Sie einen der folgenden reCAPTCHA-Services für Ihre Edge Delivery Services Forms konfigurieren:

* [reCAPTCHA Enterprise](#configure-recaptcha-enterprise)
* [reCAPTCHA](#configure-recaptcha)

>[!NOTE]
>
> Weitere Informationen zur Funktionsweise von reCAPTCHA finden Sie unter [Google reCAPTCHA](https://developers.google.com/recaptcha/).

### Konfigurieren von reCAPTCHA Enterprise

reCAPTCHA Enterprise ist ein Premium-Service zur Betrugserkennung und -prävention im Unternehmensmaßstab, der von Google angeboten wird. Es baut auf dem reCAPTCHA-System (Score-basiert) auf, bietet jedoch zusätzliche Funktionen, Skalierbarkeit und Anpassung, um die komplexen Anforderungen von Unternehmen zu erfüllen.

#### Bevor Sie beginnen

Stellen Sie vor dem Konfigurieren von Google reCAPTCHA Enterprise für Edge Delivery Services Forms sicher, dass Sie die folgenden Schritte ausgeführt haben:

1. Erstellen oder wählen Sie ein [Google Cloud-Projekt](https://cloud.google.com/recaptcha/docs/prepare-environment#before-you-begin) und rufen Sie die [Projekt-ID](https://support.google.com/googleapi/answer/7014113?hl=en#:~:text=To%20locate%20your%20project%20ID,a%20member%20of%20are%20displayed) ab.

1. [Aktivieren Sie die reCAPTCHA Enterprise-](https://cloud.google.com/recaptcha/docs/prepare-environment#enable-api) für Ihr Google Cloud-Projekt und [ Sie einen API-Schlüssel](https://console.cloud.google.com/apis/credentials).

1. Erstellen Sie [Site-Schlüssel für Ihr Google Cloud-Projekt](https://console.cloud.google.com/security/recaptcha) und kopieren Sie den Site-Schlüssel.

Sobald Sie über diese Anmeldeinformationen verfügen, können Sie mit der Konfiguration von reCAPTCHA Enterprise für Ihre Formulare fortfahren:

1. [Cloud-Konfigurations-Container erstellen](#1-create-cloud-configuration-container)
1. [Erstellen der Cloud-Service-Konfiguration für reCAPTCHA Enterprise](#2-create-the-cloud-service-configuration-for-recaptcha-enterprise)

#### 1. Erstellen eines Cloud-Konfigurations-Containers

Um den Cloud-Konfigurations-Container zu erstellen, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Ihrer Autoreninstanz an.
1. Wechseln Sie zu **[!UICONTROL Tools]** ![tools-1](/help/forms/assets/tools-1.png) > **[!UICONTROL Allgemein]** > **[!UICONTROL Konfigurations-Browser]**.

   ![Cloud-Konfigurations-Container](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)

1. Navigieren Sie im **[!UICONTROL Konfigurationsbrowser]** zu Ihrem Formular und wählen Sie **[!UICONTROL Eigenschaften]** aus.

   ![Cloud-Konfigurationseigenschaften](/help/edge/docs/forms/universal-editor/assets/general-configuration-properties.png)

1. Aktivieren Sie im Dialogfeld **[!UICONTROL Konfigurationseigenschaften]** die Option **[!UICONTROL Cloud-Konfigurationen]**.

1. Wählen Sie **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

   ![Eigenschaften der Cloud-Konfiguration aktivieren](/help/edge/docs/forms/universal-editor/assets/enable-cloud-configurations.png)
&quot;
Nachdem Sie den Cloud-Konfigurations-Container erstellt haben, veröffentlichen Sie ihn.

   ![Cloud-Konfiguration veröffentlichen](/help/edge/docs/forms/universal-editor/assets/publish-cloud-configuration.png)

#### 2. Erstellen der Cloud-Service-Konfiguration für reCAPTCHA Enterprise

Um die Cloud-Service-Konfiguration für reCAPTCHA Enterprise zu erstellen, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Ihrer Autoreninstanz an.
1. Navigieren Sie zu **[!UICONTROL Tools]** ![tools-1](/help/forms/assets/tools-1.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL reCAPTCHA]**.

   ![reCAPTCHA-Cloud-Konfiguration](/help/edge/docs/forms/universal-editor/assets/recaptcha-cloud-configuration.png)

   Das **Konfigurationen** wird geöffnet.

1. Navigieren Sie zu Ihrem Formular und wählen Sie **[!UICONTROL Erstellen]** aus.

   ![CAPTCHA-Konfiguration](/help/edge/docs/forms/universal-editor/assets/create-captcha-confguration.png)

   Der **[!UICONTROL Create reCAPTCHA Configuration]** wird geöffnet.

   ![reCaptcha Enterprise](/help/edge/docs/forms/universal-editor/assets/recaptcha-enterprise.png)

1. Wählen Sie Version als [!DNL ReCAPTCHA Enterprise] aus und geben Sie Titel, Namen, Projekt-ID, Site-Schlüssel und API-Schlüssel an.

   >[!NOTE]
   >
   > Sie können die Projekt-ID, den Site-Schlüssel und den API-Schlüssel aus dem Abschnitt [Vor dem Start](#before-you-start) für reCAPTCHA Enterprise abrufen.

1. Wählen Sie **[!UICONTROL Schlüsseltyp]** als **Bewertungsbasierter Site-Schlüssel**.
1. Geben Sie einen [Schwellenwert im Bereich von 0 bis 1](https://cloud.google.com/recaptcha/docs/interpret-assessment-website#interpret_scores) an. Scores, die größer oder gleich den Schwellenwerten sind, identifizieren menschliche Interaktionen, die ansonsten als Bot-Interaktion betrachtet werden.
1. Wählen Sie **[!UICONTROL Erstellen]** aus, um die Cloud-Service-Konfiguration zu erstellen.

   Nachdem Sie die reCAPTCHA-Cloud-Konfiguration erstellt haben, veröffentlichen Sie sie.

   ![Veröffentlichen der reCAPTCHA-Konfiguration](/help/edge/docs/forms/universal-editor/assets/publisg-recaptcha-configuration.png)

Sie können jetzt ein Formular erstellen oder bearbeiten und die reCAPTCHA-Komponente mithilfe der WYSIWYG-basierten Inhaltserstellung hinzufügen. Detaillierte Anweisungen zur Integration von Google reCAPTCHA in Ihr Formular finden Sie unter [Verwenden von reCAPTCHA in Ihrem Formular](#use-recaptcha-in-your-form).

## Konfigurieren von reCAPTCHA

reCAPTCHA ist ein kostenloser Service von Google, der Websites dabei hilft, missbräuchlichen Traffic, einschließlich Bots und Spam, zu erkennen und zu verhindern. Sie unterstützt eine auf Bewertungen basierende Version, die im Hintergrund arbeitet, und weist jeder Benutzerinteraktion eine Risikobewertung (von 0,0 bis 1,0) zu. Scores, die größer oder gleich den Schwellenwerten sind, identifizieren menschliche Interaktionen, die ansonsten als Bot-Interaktion betrachtet werden.

#### Bevor Sie beginnen

Bevor Sie Google reCAPTCHA für Edge Delivery Services Forms konfigurieren, rufen Sie das [reCAPTCHA-API-Schlüsselpaar von der Google-Konsole ](https://www.google.com/recaptcha/admin). Das Paar enthält einen Site- und einen Secret-Schlüssel.

>[!NOTE]
>
> * Edge Delivery Services Forms unterstützt nur **reCAPTCHA-basierte** Version.

Sobald Sie über das API-Schlüsselpaar verfügen, können Sie mit der Konfiguration von reCAPTCHA für Ihre Formulare fortfahren:

1. [Cloud-Konfigurations-Container erstellen](#1-create-cloud-configuration-container-1)
1. [Erstellen der Cloud-Service-Konfiguration für reCAPTCHA](#2-create-the-cloud-service-configuration-for-recaptcha)

#### 1. Erstellen eines Cloud-Konfigurations-Containers

Um den Cloud-Konfigurations-Container zu erstellen, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Ihrer Autoreninstanz an.
1. Wechseln Sie zu **[!UICONTROL Tools]** ![tools-1](/help/forms/assets/tools-1.png) > **[!UICONTROL Allgemein]** > **[!UICONTROL Konfigurations-Browser]**.

   ![Cloud-Konfigurations-Container](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)

1. Navigieren Sie im **[!UICONTROL Konfigurationsbrowser]** zu Ihrem Formular und wählen Sie **[!UICONTROL Eigenschaften]** aus.

   ![Cloud-Konfigurationseigenschaften](/help/edge/docs/forms/universal-editor/assets/general-configuration-properties.png)

1. Aktivieren Sie im Dialogfeld **[!UICONTROL Konfigurationseigenschaften]** die Option **[!UICONTROL Cloud-Konfigurationen]**.

1. Wählen Sie **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

   ![Eigenschaften der Cloud-Konfiguration aktivieren](/help/edge/docs/forms/universal-editor/assets/enable-cloud-configurations.png)

   Nachdem Sie den Cloud-Konfigurations-Container erstellt haben, veröffentlichen Sie ihn.

   ![Cloud-Konfiguration veröffentlichen](/help/edge/docs/forms/universal-editor/assets/publish-cloud-configuration.png)

#### 2. Erstellen der Cloud-Service-Konfiguration für reCAPTCHA

Um die Cloud-Service-Konfiguration für reCAPTCHA zu erstellen, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei Ihrer Autoreninstanz an.
1. Navigieren Sie zu **[!UICONTROL Tools]** ![tools-1](/help/forms/assets/tools-1.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL reCAPTCHA]**.

   ![reCAPTCHA-Cloud-Konfiguration](/help/edge/docs/forms/universal-editor/assets/recaptcha-cloud-configuration.png)

   Das **Konfigurationen** wird geöffnet.

1. Navigieren Sie zu Ihrem Formular und wählen Sie **[!UICONTROL Erstellen]** aus.

   ![CAPTCHA-Konfiguration](/help/edge/docs/forms/universal-editor/assets/create-captcha-confguration.png)

   Der **[!UICONTROL Create reCAPTCHA Configuration]** wird geöffnet.

   ![reCaptcha Enterprise](/help/edge/docs/forms/universal-editor/assets/recaptcha.png)

1. Wählen Sie Version als [!DNL ReCAPTCHA v2] aus und geben Sie Titel und Namen an.
1. Geben Sie den Site- und Geheimschlüssel an.

   >[!NOTE]
   >
   > Sie können den Site- und Geheimschlüssel aus dem Abschnitt &quot;[ vor dem Start](#before-you-begin) für reCAPTCHA abrufen.

1. Wählen Sie **[!UICONTROL Erstellen]** aus, um die Cloud-Service-Konfiguration zu erstellen.

   Nachdem Sie die reCAPTCHA-Cloud-Konfiguration erstellt haben, veröffentlichen Sie sie.

   ![Veröffentlichen der reCAPTCHA-Konfiguration](/help/edge/docs/forms/universal-editor/assets/publisg-recaptcha-configuration.png)

Sie können jetzt ein Formular erstellen und bearbeiten und die reCAPTCHA-Komponente mithilfe der WYSIWYG-basierten Inhaltserstellung hinzufügen. Detaillierte Anweisungen zur Integration von Google reCAPTCHA in Ihr Formular finden Sie unter [Verwenden von reCAPTCHA in Ihrem Formular](#use-recaptcha-in-your-form).

### Verwenden von reCAPTCHA im Formular

Um ein Formular zu erstellen und die Komponente reCAPTCHA (unsichtbar) hinzuzufügen, führen Sie die folgenden Schritte aus:

1. Öffnen Sie ein Formular im universellen Editor zur Bearbeitung.
1. Navigieren Sie in der Inhaltsstruktur zum hinzugefügten Abschnitt „Adaptives Formular“.
1. Klicken Sie auf **[!UICONTROL Hinzufügen]** und fügen Sie die Komponente **[!UICONTROL CAPTCHA (Unsichtbar]** aus der Liste **Komponenten adaptiver Formulare** hinzu.

   ![Hinzufügen der reCAPTCHA-Komponente](/help/edge/docs/forms/universal-editor/assets/add-recaptcha-component.png)

   Sie können die erforderliche adaptive Forms-Komponente auch per Drag-and-Drop verschieben, da der universelle Editor eine intuitive Drag-and-Drop-Funktion bietet.

1. Klicken Sie **Veröffentlichen**, um das Formular nach dem Hinzufügen der Komponente **[!UICONTROL CAPTCHA (Unsichtbar)]** erneut zu veröffentlichen.

   ![Formular erneut veröffentlichen](/help/edge/docs/forms/universal-editor/assets/publish-form.png)

Sie können das Formular mit dem reCAPTCHA-Dienst jetzt unter der folgenden URL anzeigen:
`https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form-name`.

![Formular mit reCAPTCHA](/help/edge/docs/forms/universal-editor/assets/form-with-recaptcha.png)

## Häufig gestellte Fragen

* **Was passiert, wenn ein Benutzer keine reCAPTCHA-Cloud-Konfiguration erstellt?**

  **A**: Wenn ein(e) Benutzende(r) keine reCAPTCHA-Cloudkonfiguration erstellt, sucht der AEM-Server im globalen Konfigurations-Container nach der reCAPTCHA-Cloudkonfiguration. Wenn im globalen Konfigurations-Container keine Konfiguration vorhanden ist, gibt der AEM-Server einen Fehler aus.

* **Was passiert, wenn ein Benutzer mehrere reCAPTCHA-Cloud-Konfigurationen erstellt?**
  **A**: Wenn ein Benutzer mehr als eine reCAPTCHA-Cloud-Konfigurationen erstellt, wählt das System automatisch die erste erstellte reCAPTCHA-Konfiguration aus.

* **Warum sind Änderungen oder Änderungen an der veröffentlichten URL nicht sichtbar?**
Wenn Änderungen oder Änderungen an der veröffentlichten URL nicht sichtbar sind, stellen Sie sicher, dass das Formular erneut veröffentlicht wird, um die Aktualisierungen anzuwenden.

* **Welchen reCAPTCHA-Service unterstützt Edge Delivery Services Forms?**
  **A**: Edge Delivery Services Forms unterstützt nur den Score-basierten reCAPTCHA-Service, der von Google bereitgestellt wird.


## Siehe auch

{{universal-editor-see-also}}

