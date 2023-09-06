---
title: Verwenden von reCAPTCHA in Adaptive Forms
description: Erfahren Sie, wie Sie den Google reCAPTCHA-Dienst in Adaptive Forms konfigurieren.
topic-tags: adaptive_forms, author
source-git-commit: 58451648b120991a5e204044f8dd6aeeaf655d81
workflow-type: tm+mt
source-wordcount: '1933'
ht-degree: 74%

---

# Verwenden von reCAPTCHA in Adaptive Forms {#using-reCAPTCHA-in-adaptive-forms}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren Datenerfassung [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) für [Erstellen neuer adaptiver Forms](/help/forms/creating-adaptive-form-core-components.md) oder [Hinzufügen von Adaptive Forms zu AEM Sites-Seiten](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Forms dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von Adaptive Forms mithilfe von Foundation-Komponenten beschrieben. </span>

| Gilt für | Artikel-Link |
| -------- | ---------------------------- |
| Adaptives Formular basierend auf Foundation-Komponenten | Dieser Artikel |
| Adaptives Formular basierend auf Kernkomponenten | [Hier klicken](/help/forms/captcha-adaptive-forms-core-components.md) |

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/captcha-adaptive-forms.html) |
| AEM as a Cloud Service | Dieser Artikel |

CAPTCHA („Completely Automated Public Turing test to tell Computers and Humans Apart“ – „vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen“) ist ein Programm, das bei Onlinetransaktionen eingesetzt wird, um zwischen Menschen und Bots oder automatisierten Programmen zu unterscheiden. Es stellt eine Herausforderung dar und bewertet die Benutzerantwort, um festzustellen, ob es sich um einen Menschen oder einen Bot handelt, der mit der Site interagiert. Dabei wird verhindert, dass der Benutzer fortfährt, wenn der Test fehlschlägt, wodurch Onlinetransaktionen sicherer werden, da Bots keinen Spam senden oder andere bösartige Zwecke verfolgen können.

[!DNL AEM Forms] unterstützt reCAPTCHA in Adaptive Forms. Sie können den reCAPTCHA-Service von Google verwenden, um CAPTCHA zu implementieren.

>[!NOTE]
>
>* [!DNL AEM Forms] unterstützt reCaptcha v2 und reCaptcha Enterprise. Es werden keine anderen Versionen unterstützt.
>* reCAPTCHA im adaptiven Forms wird im Offline-Modus nicht unterstützt in [!DNL AEM Forms] App.
>

## reCAPTCHA-Dienst von Google konfigurieren {#google-reCAPTCHA}

Formularautoren können den reCAPTCHA-Dienst von Google verwenden, um reCAPTCHA in Adaptive Forms zu implementieren. Es bietet erweiterte CAPTCHA-Funktionen zum Schutz Ihrer Site. Weitere Informationen zur Funktionsweise von reCAPTCHA finden Sie unter [Google reCAPTCHA](https://developers.google.com/recaptcha/). Der reCAPTCHA-Dienst umfasst [!DNL reCAPTCHA v2] und [!DNL reCAPTCHA Enterprise] in die integriert werden kann [!DNL AEM Forms]. Je nach Ihren Anforderungen können Sie den reCAPTCHA-Service konfigurieren, um Folgendes zu aktivieren:

![reCAPTCHA](/help/forms/assets/recaptcha_new.png)

* [reCAPTCHA Enterprise in AEM Forms](#steps-to-implement-reCAPTCHA-enterprise-in-forms)
* [reCAPTCHA v2 in AEM Forms](#steps-to-implement-reCAPTCHA-v2-in-forms)


### Konfigurieren von reCAPTCHA Enterprise  {#steps-to-implement-reCAPTCHA-enterprise-in-forms}

1. Erstellen oder Auswählen einer [Google Cloud-Projekt](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#before-you-begin) und aktivieren [reCAPTCHA Enterprise API](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#enable-the-recaptcha-enterprise-api).
1. Erhalten Sie die [Projekt-ID](https://support.google.com/googleapi/answer/7014113?hl=en#:~:text=To%20locate%20your%20project%20ID,a%20member%20of%20are%20displayed) und erstellen Sie eine [API-Schlüssel](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#create_an_api_key) und [Site-Schlüssel für Websites](https://cloud.google.com/recaptcha-enterprise/docs/create-key#create-key).
1. Erstellen Sie einen Konfigurations-Container für Cloud Services.

   1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurationsbrowser]**.
   1. Wählen Sie einen Ordner aus oder erstellen Sie einen Ordner und aktivieren Sie den Ordner für Cloud-Konfigurationen, indem Sie folgende Schritte ausführen:
      1. Wählen Sie im Konfigurationsbrowser den Ordner  aus und tippen Sie auf **[!UICONTROL Eigenschaften]**.
      1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloudkonfigurationen]**.
      1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

1. Konfigurieren Sie den Cloud Service für [!DNL reCAPTCHA Enterprise].

   1. Gehen Sie in der Experience Manager-Autoreninstanz zu ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Services]**.
   1. Tippen Sie auf **[!UICONTROL reCAPTCHA]**. Die Konfigurationsseite öffnet sich. Wählen Sie den erstellten Konfigurationscontainer aus und tippen Sie auf **[!UICONTROL Erstellen]**.
   1. Wählen Sie Version als [!DNL reCAPTCHA Enterprise] und geben Sie den Namen, die Projekt-ID, den Site-Schlüssel und den API-Schlüssel (abgerufen in Schritt 2) für den reCAPTCHA Enterprise-Dienst an.
   1. Wählen Sie den Schlüsseltyp aus. Der Schlüsseltyp sollte mit dem Site-Schlüssel übereinstimmen, den Sie in der [Google Cloud-Projekt](https://cloud.google.com/recaptcha-enterprise/docs/set-up-non-google-cloud-environments-api-keys#before-you-begin), beispielsweise **Checkbox-Site-Schlüssel** oder **Score-basierter Site-Schlüssel**.
   1. Geben Sie eine [Schwellenwert im Bereich von 0 bis 1](https://cloud.google.com/recaptcha-enterprise/docs/interpret-assessment#interpret_scores). Werte, die größer oder gleich den Schwellenwerten sind, kennzeichnen menschliche Interaktionen, die ansonsten als Bot-Interaktion betrachtet werden.
   1. Tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud-Service-Konfiguration zu erstellen.

<!--
    1. In the Edit Component dialog, specify the name, project ID, site key, API key (obtained in steps 2 and 3), select the key type, and enter the threshold score. Tap **[!UICONTROL Save Settings]** and then tap **[!UICONTROL OK]** to complete the configuration.
-->

Sobald der reCAPTCHA Enterprise-Dienst aktiviert ist, kann er in adaptiven Formularen verwendet werden. Siehe [Verwenden von CAPTCHA in adaptiven Formularen](#using-reCAPTCHA).

<!--
![reCAPTCHA Enterprise](/help/forms/assets/recaptcha1-enterprise.png)
-->

### Konfigurieren von Google reCAPTCHA v2 {#steps-to-implement-reCAPTCHA-v2-in-forms}

1. Rufen Sie ein [reCAPTCHA-API-Schlüsselpaar](https://www.google.com/recaptcha/admin) von Google ab. Er enthält einen **Site-Schlüssel** und einen **geheimen Schlüssel**.
1. Erstellen Sie einen Konfigurations-Container für Cloud-Dienste.
   1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurationsbrowser]**.
   1. Wählen Sie einen Ordner aus oder erstellen Sie einen Ordner und aktivieren Sie den Ordner für Cloud-Konfigurationen, indem Sie folgende Schritte ausführen:
      1. Wählen Sie im Konfigurationsbrowser den Ordner  aus und tippen Sie auf **[!UICONTROL Eigenschaften]**.
      1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloudkonfigurationen]**.
      1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

1. Konfigurieren Sie den Cloud Service für reCAPTCHA v2.

   1. Navigieren Sie in der AEM-Autoreninstanz zu ![tools-1](assets/tools-1.png) > **Cloud Services**.
   1. Tippen Sie auf **[!UICONTROL reCAPTCHA]**. Die Konfigurationsseite öffnet sich. Wählen Sie den erstellten Konfigurationscontainer aus und tippen Sie auf **[!UICONTROL Erstellen]**.
   1. Wählen Sie Version als [!DNL reCAPTCHA v2] , geben Sie den Namen, den Site-Schlüssel und den geheimen Schlüssel für den reCAPTCHA-Dienst an (abgerufen in Schritt 1) und tippen Sie auf **[!UICONTROL Erstellen]** , um die Cloud Service-Konfiguration zu erstellen.
   1. Geben Sie im Dialogfeld „Komponente bearbeiten“ die Site- und Geheimschlüssel an, die Sie in Schritt 1 erhalten haben. Tippen Sie auf **[!UICONTROL Einstellungen speichern]** und anschließend auf **OK**, um die Konfiguration abzuschließen.

   Sobald der reCAPTCHA-Service konfiguriert ist, kann er in adaptiven Formularen verwendet werden. Weitere Informationen finden Sie unter [Verwenden von CAPTCHA in adaptiven Formularen](#using-reCAPTCHA).

<!--![reCAPTCHA v2](/help/forms/assets/recaptcha-v2.png)-->


## Verwenden von reCAPTCHA in adaptiven Formularen {#using-reCAPTCHA}

So verwenden Sie reCAPTCHA in adaptiven Formularen:

1. Öffnen Sie ein adaptives Formular im Bearbeitungsmodus.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass der beim Erstellen des adaptiven Formulars ausgewählte Konfigurations-Container den reCAPTCHA-Cloud Service enthält. Sie können auch adaptive Formulareigenschaften bearbeiten, um den Konfigurationscontainer zu ändern, der dem Formular zugeordnet ist.

1. Ziehen Sie die **CAPTCHA**-Komponente im Komponenten-Browser in das adaptive Formular und legen Sie sie dort ab.

   >[!NOTE]
   >
   >* Die Verwendung von mehr als einer CAPTCHA-Komponente in einem adaptiven Formular wird nicht unterstützt. Es wird nicht empfohlen, CAPTCHA in einem Fragment oder in einem Bedienfeld zu verwenden, das für das verzögerte Laden konfiguriert wurde.
   >* reCaptcha ist zeitkritisch und läuft in ein paar Minuten ab. Daher wird empfohlen, die Captcha-Komponente unmittelbar vor der Sendeschaltfläche im adaptiven Formular zu platzieren.

1. Wählen Sie die hinzugefügte Captcha-Komponente aus und tippen Sie auf ![cmppr](assets/cmppr.png), um ihre Eigenschaften zu bearbeiten.
1. Geben Sie einen Titel für das CAPTCHA-Widget an. Der Standardwert ist **CAPTCHA**. Wählen Sie **Titel ausblenden**, wenn der Titel nicht angezeigt werden soll.
1. Wählen Sie aus der Dropdown-Liste **Captcha-Service** die Option **reCAPTCHA**, um den reCAPTCHA-Service zu aktivieren, wenn Sie ihn wie unter [reCAPTCHA-Service von Google](#google-reCAPTCHA) beschrieben konfiguriert haben.
1. Wählen Sie eine Konfiguration aus der Dropdown-Liste Einstellungen für **reCAPTCHA Enterprise** oder **reCAPTCHA v2**
   1. Wenn Sie **reCAPTCHA Enterprise** -Version, kann der Schlüsseltyp **Kontrollkästchen** oder **Ergebnisbasiert** festgelegt ist, hängt es von Ihrer Auswahl ab, wenn Sie [Site-Schlüssel für Websites](https://cloud.google.com/recaptcha-enterprise/docs/create-key#create-key):

   >[!NOTE]
   >
   >* In der Cloud-Konfiguration mit **Schlüsseltyp** as **Kontrollkästchen**, wird die angepasste Fehlermeldung als Inline-Meldung angezeigt, wenn die Captcha-Validierung fehlschlägt.
   >* In der Cloud-Konfiguration mit **Schlüsseltyp** as **Ergebnisbasiert**, wird die angepasste Fehlermeldung als Popup-Meldung angezeigt, wenn die Captcha-Validierung fehlschlägt.

   1. Sie können zwischen den Größen **[!UICONTROL Normal]** und **[!UICONTROL Kompakt]** wählen.
   1. Sie können eine **[!UICONTROL Bindungsverweis]**, in **[!UICONTROL Bindungsverweis]** die übermittelten Daten sind gebundene Daten, andernfalls sind sie ungebundene Daten. Im Folgenden finden Sie XML-Beispiele für ungebundene Daten und gebundene Daten (mit Bindungsverweis als SSN), wenn ein Formular gesendet wird.

   ```xml
           <?xml version="1.0" encoding="UTF-8" standalone="no"?>
           <afData>
           <afUnboundData>
               <data>
                   <captcha16820607953761>
                       <captchaType>reCaptchaEnterprise</captchaType>
                       <captchaScore>0.9</captchaScore>
                   </captcha16820607953761>
               </data>
           </afUnboundData>
           <afBoundData>
               <Root
                   xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/"
                   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                   <PersonalDetails>
                       <SSN>371237912</SSN>
                       <FirstName>Sarah </FirstName>
                       <LastName>Smith</LastName>
                   </PersonalDetails>
                   <OtherInfo>
                       <City>California</City>
                       <Address>54 Residency</Address>
                       <State>USA</State>
                       <Zip>123112</Zip>
                   </OtherInfo>
               </Root>
           </afBoundData>
           <afSubmissionInfo>
               <stateOverrides/>
               <signers/>
               <afPath>/content/dam/formsanddocuments/captcha-form</afPath>
               <afSubmissionTime>20230608034928</afSubmissionTime>
           </afSubmissionInfo>
           </afData>
   ```

   ```xml
           <?xml version="1.0" encoding="UTF-8" standalone="no"?>
           <afData>
           <afUnboundData>
               <data/>
           </afUnboundData>
           <afBoundData>
               <Root
                   xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/"
                   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                   <PersonalDetails>
                       <SSN>
                           <captchaType>reCaptchaEnterprise</captchaType>
                           <captchaScore>0.9</captchaScore>
                       </SSN>
                       <FirstName>Sarah</FirstName>
                       <LastName>Smith</LastName>
                   </PersonalDetails>
                   <OtherInfo>
                       <City>California</City>
                       <Address>54 Residency</Address>
                       <State>USA</State>
                       <Zip>123112</Zip>
                   </OtherInfo>
               </Root>
           </afBoundData>
           <afSubmissionInfo>
               <stateOverrides/>
               <signers/>
               <afPath>/content/dam/formsanddocuments/captcha-form</afPath>
               <afSubmissionTime>20230608035111</afSubmissionTime>
           </afSubmissionInfo>
           </afData>
   ```

   Wenn Sie **reCAPTCHA v2** version:
   1. Sie können die Größe als **[!UICONTROL Normal]** oder **[!UICONTROL Kompakt]** für das reCAPTCHA-Widget.
   1. Sie können die **[!UICONTROL Unsichtbar]** Option, um die CAPTCHA-Herausforderung nur im Falle einer verdächtigen Aktivität anzuzeigen.

   Der reCAPTCHA-Dienst wird im adaptiven Formular aktiviert. Sie können das Formular in der Vorschau anzeigen und die CAPTCHA-Funktionsweise sehen. Das unten abgebildete Abzeichen **mit reCAPTCHA geschützt** wird auf den geschützten Formularen angezeigt.
   ![Durch Google geschützt mit reCAPTCHA-Badge](/help/forms/assets/google-recaptcha-v2.png)

1. Speichern Sie die Eigenschaften.

>[!NOTE]
> 
> Wählen Sie nicht **[!UICONTROL Standard]** aus der Dropdown-Liste „CAPTCHA-Service“ aus, da der standardmäßige AEM-CAPTCHA-Service nicht mehr unterstützt wird.

>[!VIDEO](https://video.tv.adobe.com/v/3422641/recaptcha-google-adaptive-forms/?quality=12&learn=on)

### Ein- oder Ausblenden der CAPTCHA-Komponente auf Grundlage von Regeln {#show-hide-captcha}

Sie können die CAPTCHA-Komponente auf Grundlage von Regeln, die Sie auf eine Komponente in einem adaptiven Formular anwenden, ein- oder ausblenden. Tippen Sie auf die Komponente, wählen Sie ![Regeln bearbeiten](assets/edit-rules-icon.svg) aus und tippen Sie auf **[!UICONTROL Erstellen]**, um eine Regel zu erstellen. Weitere Informationen zum Erstellen von Regeln finden Sie im [Regeleditor](rule-editor.md).

Beispielsweise darf die CAPTCHA-Komponente nur dann in einem adaptiven Formular angezeigt werden, wenn das Feld „Währungswert“ im Formular einen Wert von mehr als 25000 aufweist.

Tippen Sie im Formular auf das Feld **[!UICONTROL Währungswert]** und erstellen Sie folgende Regeln:

![Regeln zum Ein- oder Ausblenden](assets/rules-show-hide-captcha.png)

>[!NOTE]
>
> Wenn Sie eine reCAPTCHA v2-Konfiguration auswählen und die Größe auf [!UICONTROL Unsichtbar], bleibt die Ein-/Ausblenden-Option deaktiviert.

### CAPTCHA validieren {#validate-captcha}

Sie können CAPTCHA in einem adaptiven Formular entweder beim Übermitteln des Formulars validieren oder angeben, dass die CAPTCHA-Validierung auf Benutzeraktionen und -bedingungen basiert.

#### CAPTCHA bei Formularübermittlung validieren {#validation-form-submission}

So validieren Sie CAPTCHA beim Übermitteln eines adaptiven Formulars automatisch:

1. Tippen Sie auf die CAPTCHA-Komponente und wählen Sie ![cmppr](assets/configure-icon.svg) aus, um die Komponenteneigenschaften anzuzeigen.
1. Wählen Sie im Abschnitt **[!UICONTROL Validieren von CAPTCHA]** **[!UICONTROL CAPTCHA bei Formularübermittlung validieren]**.
1. Tippen Sie auf ![Fertig](assets/save_icon.svg), um die Komponenteneigenschaften zu speichern.

#### Validieren von CAPTCHA mit Benutzeraktionen und -bedingungen {#validate-captcha-user-action}

Validieren von CAPTCHA basierend auf Bedingungen und Benutzeraktionen:

1. Tippen Sie auf die CAPTCHA-Komponente und wählen Sie ![cmppr](assets/configure-icon.svg) aus, um die Komponenteneigenschaften anzuzeigen.
1. Wählen Sie im Abschnitt **[!UICONTROL Validieren von CAPTCHA]** **[!UICONTROL CAPTCHA mit Benutzeraktion validieren]**.
1. Tippen Sie auf ![Fertig](assets/save_icon.svg), um die Komponenteneigenschaften zu speichern.

[!DNL Experience Manager Forms] stellt die `ValidateCAPTCHA`-API zur Validierung von CAPTCHA unter Verwendung vordefinierter Bedingungen bereit. Sie können die API mit einer benutzerdefinierten Übermittlungsaktion oder durch Definieren von Regeln für Komponenten in einem adaptiven Formular aufrufen.

Im Folgenden finden Sie ein Beispiel für eine `ValidateCAPTCHA`-API zur Validierung von CAPTCHA unter Verwendung vordefinierter Bedingungen:

```javascript
if (slingRequest.getParameter("numericbox1614079614831").length() >= 5) {
     GuideCaptchaValidatorProvider apiProvider = sling.getService(GuideCaptchaValidatorProvider.class);
        String formPath = slingRequest.getResource().getPath();
        String captchaData = slingRequest.getParameter(GuideConstants.GUIDE_CAPTCHA_DATA);
        if (!apiProvider.validateCAPTCHA(formPath, captchaData).isCaptchaValid()){
            response.setStatus(400);
            return;
        }
    }
```

Das Beispiel zeigt an, dass die `ValidateCAPTCHA`-API CAPTCHA im Formular nur dann validiert, wenn die Anzahl der Stellen im numerischen Feld, die der Benutzer beim Ausfüllen des Formulars angegeben hat, größer als 5 ist.

**Option 1: Verwenden Sie die [!DNL Experience Manager Forms] ValidateCAPTCHA-API, um CAPTCHA mithilfe einer benutzerdefinierten Übermittlungsaktion zu validieren.**

Führen Sie folgende Schritte aus, um die `ValidateCAPTCHA`-API zur Validierung von CAPTCHA mit einer benutzerdefinierten Übermittlungsaktion zu verwenden:

1. Fügen Sie das Skript, das die `ValidateCAPTCHA`-API enthält, zur benutzerdefinierten Übermittlungsaktion hinzu. Weitere Informationen zu benutzerdefinierten Übermittlungsaktionen finden Sie unter [Erstellen einer benutzerdefinierten Übermittlungsaktion für adaptive Formulare](custom-submit-action-form.md).
1. Wählen Sie den Namen der benutzerdefinierten Übermittlungsaktion aus der Dropdown-Liste **[!UICONTROL Übermittlungsaktion]** in den Eigenschaften für die **[!UICONTROL Übermittlung]** eines adaptiven Formulars.
1. Tippen Sie auf **[!UICONTROL Übermitteln]**. CAPTCHA wird auf Grundlage der Bedingungen validiert, die in der `ValidateCAPTCHA`-API der benutzerdefinierten Übermittlungsaktion definiert sind.

**Option 2: Verwenden Sie die [!DNL Experience Manager Forms] ValidateCAPTCHA-API, um CAPTCHA vor dem Übermitteln des Formulars bei einer Benutzeraktion zu validieren.**

Sie können die `ValidateCAPTCHA`-API auch aufrufen, indem Sie Regeln auf eine Komponente in einem adaptiven Formular anwenden.

Sie fügen beispielsweise die Schaltfläche **[!UICONTROL CAPTCHA validieren]** in einem adaptiven Formular hinzu und erstellen eine Regel, um beim Klick auf eine Schaltfläche einen Service aufzurufen.

Folgende Abbildung zeigt, wie Sie beim Klick auf die Schaltfläche **[!UICONTROL CAPTCHA validieren]** einen Service aufrufen können:

![CAPTCHA validieren](assets/captcha-validation1.gif)

Sie können das benutzerdefinierte Servlet, das die `ValidateCAPTCHA`-API enthält, mit dem Regeleditor aufrufen und die Schaltfläche zum Übermitteln des adaptiven Formulars basierend auf dem Validierungsergebnis aktivieren oder deaktivieren.

Ebenso können Sie mithilfe des Regeleditors eine benutzerdefinierte Methode zur Validierung von CAPTCHA in ein adaptives Formular aufnehmen.

### Hinzufügen benutzerdefinierter CAPTCHA-Services {#add-custom-captcha-service}

[!DNL Experience Manager Forms] stellt reCAPTCHA als CAPTCHA-Service bereit. Sie können jedoch einen benutzerdefinierten Service hinzufügen, der in der Dropdown-Liste **[!UICONTROL CAPTCHA-Service]** angezeigt wird.

Im Folgenden finden Sie eine Beispielimplementierung der Oberfläche zum Hinzufügen eines zusätzlichen CAPTCHA-Service zu Ihrem adaptiven Formular:

```javascript
package com.adobe.aemds.guide.service;

import org.osgi.annotation.versioning.ConsumerType;

/**
 * An interface to provide captcha validation at server side in Adaptive Form
 * This interface can be used to provide custom implementation for different captcha services.
 */
@ConsumerType
public interface GuideCaptchaValidator {
    /**
     * This method should define the actual validation logic of the captcha
     * @param captchaPropertyNodePath path to the node with CAPTCHA configurations inside form container
     * @param userResponseToken  The user response token provided by the CAPTCHA from client-side
     *
     * @return  {@link GuideCaptchaValidationResult} validation result of the captcha
     */
     GuideCaptchaValidationResult validateCaptcha(String captchaPropertyNodePath, String userResponseToken);

    /**
     * Returns the name of the captcha validator. This should be unique among the different implementations
     * @return  name of the captcha validator
     */
     String getCaptchaValidatorName();
}
```

`captchaPropertyNodePath` verweist auf den Ressourcenpfad der CAPTCHA-Komponente im Sling-Repository. Verwenden Sie diese Eigenschaft, um spezifische Details zur CAPTCHA-Komponente aufzunehmen. Beispielsweise enthält `captchaPropertyNodePath` Informationen zur reCAPTCHA-Cloudkonfiguration, die für die CAPTCHA-Komponente eingestellt ist. Die Informationen zur Cloudkonfiguration enthalten die Einstellungen **[!UICONTROL Siteschlüssel]** und **[!UICONTROL Geheimschlüssel]** für die Implementierung des reCAPTCHA-Service.

`userResponseToken` bezieht sich auf `g_recaptcha_response`, die nach dem Lösen eines CAPTCHA in einem Formular generiert wird.

### Bearbeiten der reCAPTCHA-Servicedomain {#reCAPTCHA-service-domain}

Der reCAPTCHA-Service verwendet `https://www.recaptcha.net/` als Standard-Domain. Sie können die Einstellungen ändern, um `https://www.google.com/` oder einen beliebigen benutzerdefinierten Domain-Namen zum Laden, Rendern und Validieren des reCAPTCHA-Service festzulegen.

Legen Sie die Eigenschaft **[!UICONTROL af.cloudservices.recaptcha.domain]** der Konfiguration **[!UICONTROL Adaptives Formular und Webkanal für interaktive Kommunikation]** fest, um `https://www.google.com/` oder einen anderen benutzerdefinierten Domain-Namen anzugeben. Folgende JSON-Datei zeigt ein Beispiel:

```json
{
  "af.cloudservices.recaptcha.domain": "https://www.google.com/"
}
```

Um Konfigurationswerte festzulegen, [generieren Sie OSGi-Konfigurationen mit dem AEM-SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=de#generating-osgi-configurations-using-the-aem-sdk-quickstart) und [stellen Sie die Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=de#deployment-process) in Ihrer Cloud Service-Instanz bereit.
