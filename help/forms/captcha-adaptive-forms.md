---
title: Verwenden von CAPTCHA in adaptiven Formularen
seo-title: Using CAPTCHA in Adaptive Forms
description: Erfahren Sie, wie Sie AEM CAPTCHA oder Google reCAPTCHA in adaptiven Formularen konfigurieren.
seo-description: Learn how to configure AEM CAPTCHA or Google reCAPTCHA service in Adaptive Forms.
uuid: 0e11e98a-12ac-484c-b77f-88ebdf0f40e5
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: adaptive_forms, author
discoiquuid: 4c53dfc0-25ca-419d-abfe-cf31fc6ebf61
docset: aem65
exl-id: 3fdbe5a3-5c3c-474d-b701-e0182da4191a
source-git-commit: 580ab2731bc277bcd53c4863b3b22f5e44dc8406
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 94%

---

# Verwenden von CAPTCHA in adaptiven Formularen {#using-captcha-in-adaptive-forms}

CAPTCHA („Completely Automated Public Turing test to tell Computers and Humans Apart“ – „vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen“) ist ein Programm, das bei Onlinetransaktionen eingesetzt wird, um zwischen Menschen und Bots oder automatisierten Programmen zu unterscheiden. Es bewertet die Benutzerantwort, um zu ermitteln, ob ein Mensch oder ein Bot mit der Website interagiert. Dabei wird verhindert, dass der Benutzer fortfährt, wenn der Test fehlschlägt, wodurch Onlinetransaktionen sicherer werden, da Bots keinen Spam senden oder andere bösartige Zwecke verfolgen können.

[!DNL AEM Forms] unterstützt CAPTCHA in adaptiven Formularen. Sie können den reCAPTCHA-Service von Google verwenden, um CAPTCHA zu implementieren.

>[!NOTE]
>
>* [!DNL AEM Forms] unterstützt nur reCaptcha v2. Es werden keine anderen Versionen unterstützt.
>* Im Offline-Modus der [!DNL AEM Forms]-Mobile-App wird CAPTCHA in adaptiven Formularen nicht unterstützt.
>


## Konfigurieren des reCAPTCHA-Service von Google {#google-recaptcha}

Formularautoren können den reCAPTCHA-Service von Google verwenden, um ein CAPTCHA in adaptiven Formularen zu implementieren. Er bietet erweiterte CAPTCHA-Fähigkeiten, um Ihre Website zu schützen. Weitere Informationen dazu, wie reCAPTCHA funktioniert, finden Sie unter [Google reCAPTCHA](https://developers.google.com/recaptcha/).

![reCAPTCHA](assets/recaptcha_new.png)

Implementieren des reCAPTCHA-Service in [!DNL AEM Forms]:

1. Rufen Sie ein [reCAPTCHA-API-Schlüsselpaar](https://www.google.com/recaptcha/admin) von Google ab. Er enthält einen Site- und einen Geheimschlüssel.
1. Erstellen Sie einen Konfigurations-Container für Cloud Services.

   1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurationsbrowser]**.
      * Weitere Informationen finden Sie in der Dokumentation zum [Konfigurationsbrowser](https://experienceleague.adobe.com/docs/experience-manager-65/administering/introduction/configurations.html?lang=de#introduction).
   1. Gehen Sie folgendermaßen vor, um den globalen Ordner für Cloudkonfigurationen zu aktivieren, oder überspringen Sie diesen Schritt, um einen anderen Ordner für Cloud Service-Konfigurationen zu erstellen und zu konfigurieren.

      1. Wählen Sie im Konfigurationsbrowser den Ordner **[!UICONTROL global]** und tippen Sie auf **[!UICONTROL Eigenschaften]**.

      1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloudkonfigurationen]**.
      1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.
   1. Tippen Sie im Konfigurationsbrowser auf **[!UICONTROL Erstellen]**.
   1. Legen Sie im Dialogfeld „Konfiguration erstellen“ einen Titel für den Ordner fest und aktivieren Sie **[!UICONTROL Cloudkonfigurationen]**.
   1. Tippen Sie auf **[!UICONTROL Erstellen]**, um den für Cloud Service-Konfigurationen aktivierten Ordner zu erstellen.


1. Konfigurieren Sie den Cloud Service für reCAPTCHA.

   1. Navigieren Sie in Ihrer Experience Manager-Autoreninstanz zu ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Services]**.
   1. Tippen Sie auf **[!UICONTROL reCAPTCHA]**. Die Konfigurationsseite wird geöffnet. Wählen Sie den im vorherigen Schritt erstellten Konfigurations-Container und tippen Sie auf **[!UICONTROL Erstellen]**.
   1. Geben Sie Namen, Site- und Geheimschlüssel für den reCAPTCHA-Service an und tippen Sie auf **[!UICONTROL Erstellen]**, um die Cloud Service-Konfiguration zu erstellen.
   1. Geben Sie im Dialogfeld „Komponente bearbeiten“ die Site- und Geheimschlüssel an, die Sie in Schritt 1 erhalten haben. Tippen Sie auf **[!UICONTROL Einstellungen speichern]** und anschließend auf **[!UICONTROL OK]**, um die Konfiguration abzuschließen.

   Sobald der reCAPTCHA-Service konfiguriert ist, kann er in adaptiven Formularen verwendet werden. Weitere Informationen finden Sie unter [Verwenden von CAPTCHA in adaptiven Formularen](#using-captcha).

## Verwenden von CAPTCHA in adaptiven Formularen  {#using-captcha}

So verwenden Sie CAPTCHA in adaptiven Formularen:

1. Öffnen Sie ein adaptives Formular im Bearbeitungsmodus.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass der beim Erstellen des adaptiven Formulars ausgewählte Konfigurations-Container den reCAPTCHA-Cloud Service enthält. Sie können auch die Eigenschaften adaptiver Formulare bearbeiten, um den Konfigurations-Container zu ändern, der dem Formular zugeordnet ist.

1. Ziehen Sie die **[!UICONTROL CAPTCHA]**-Komponente im Komponentenbrowser in das adaptive Formular und legen Sie sie dort ab.

   >[!NOTE]
   >
   >Die Verwendung von mehr als einer CAPTCHA-Komponente in einem adaptiven Formular wird nicht unterstützt. Es wird nicht empfohlen, CAPTCHA in einem Fragment oder in einem Bedienfeld zu verwenden, für das verzögertes Laden konfiguriert wurde.

   >[!NOTE]
   >
   >Captcha ist zeitabhängig und läuft in etwa einer Minute ab. Daher wird empfohlen, die CAPTCHA-Komponente unmittelbar vor der Schaltfläche zum Übermitteln im adaptiven Formular zu platzieren.

1. Wählen Sie die CAPTCHA-Komponente aus, die Sie hinzugefügt haben, und tippen Sie auf ![cmppr](assets/configure-icon.svg), um ihre Eigenschaften zu bearbeiten.
1. Geben Sie einen Titel für das CAPTCHA-Widget an. Der Standardwert ist **[!UICONTROL CAPTCHA]**. Wählen Sie **[!UICONTROL Titel ausblenden]**, wenn der Titel nicht angezeigt werden soll.
1. Wählen Sie aus der Dropdown-Liste des **[!UICONTROL CAPTCHA-Service]** die Option **[!UICONTROL reCAPTCHA]** aus, um den reCAPTCHA-Service zu aktivieren, wenn Sie ihn wie in [reCAPTCHA-Service von Google](#google-recaptcha) beschrieben konfiguriert haben. Wählen Sie eine Konfiguration aus der Dropdown-Liste „Einstellungen“. 
1. Wählen Sie den Typ als **[!UICONTROL Normal]** oder **[!UICONTROL Kompakt]** für das reCAPTCHA-Widget. Sie können auch die **[!UICONTROL Unsichtbar]** Option, um die CAPTCHA-Herausforderung nur im Falle einer verdächtigen Aktivität anzuzeigen. Der unten dargestellte, durch reCAPTCHA geschützte Badge wird auf den geschützten Formularen angezeigt.

   ![Von reCAPTCHA-Zeichen verarbeitetes Google](assets/google-recaptcha-v2.png)

   >[!NOTE]
   >
   >Nicht auswählen **[!UICONTROL Standard]** aus der Dropdown-Liste Captcha-Dienst , da der standardmäßige Experience Manager-CAPTCHA-Dienst nicht mehr unterstützt wird.

1. Speichern Sie die Eigenschaften.

Der reCAPTCHA-Service wird im adaptiven Formular aktiviert. Sie können das Formular in der Vorschau anzeigen und die CAPTCHA-Funktionsweise sehen.

### Ein- oder Ausblenden der CAPTCHA-Komponente auf Grundlage von Regeln {#show-hide-captcha}

Sie können die CAPTCHA-Komponente auf Grundlage von Regeln, die Sie auf eine Komponente in einem adaptiven Formular anwenden, ein- oder ausblenden. Tippen Sie auf die Komponente, wählen Sie ![Regeln bearbeiten](assets/edit-rules-icon.svg) aus und tippen Sie auf **[!UICONTROL Erstellen]**, um eine Regel zu erstellen. Weitere Informationen zum Erstellen von Regeln finden Sie im [Regeleditor](rule-editor.md).

Beispielsweise darf die CAPTCHA-Komponente nur dann in einem adaptiven Formular angezeigt werden, wenn das Feld „Währungswert“ im Formular einen Wert von mehr als 25000 aufweist.

Tippen Sie im Formular auf das Feld **[!UICONTROL Währungswert]** und erstellen Sie folgende Regeln:

![Regeln zum Ein- oder Ausblenden](assets/rules-show-hide-captcha.png)

### Validieren von CAPTCHA {#validate-captcha}

Sie können CAPTCHA in einem adaptiven Formular entweder beim Übermitteln des Formulars validieren oder angeben, dass die CAPTCHA-Validierung auf Benutzeraktionen und -bedingungen basiert.

#### Validieren von CAPTCHA bei der Formularübermittlung  {#validation-form-submission}

So validieren Sie CAPTCHA beim Übermitteln eines adaptiven Formulars automatisch:

1. Tippen Sie auf die CAPTCHA-Komponente und wählen Sie ![cmppr](assets/configure-icon.svg) aus, um die Komponenteneigenschaften anzuzeigen.
1. Wählen Sie im Abschnitt **[!UICONTROL Validieren von CAPTCHA]** **[!UICONTROL CAPTCHA bei Formularübermittlung validieren]**.
1. Tippen Sie auf ![Fertig](assets/save_icon.svg), um die Komponenteneigenschaften zu speichern.

#### Validieren von CAPTCHA bei Benutzeraktionen und -bedingungen {#validate-captcha-user-action}

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

### Bearbeiten der reCAPTCHA-Servicedomain {#recaptcha-service-domain}

Der reCAPTCHA-Service verwendet `https://www.recaptcha.net/` als Standard-Domain. Sie können die Einstellungen ändern, um `https://www.google.com/` oder einen beliebigen benutzerdefinierten Domain-Namen zum Laden, Rendern und Validieren des reCAPTCHA-Service festzulegen.

Legen Sie die Eigenschaft **[!UICONTROL af.cloudservices.recaptcha.domain]** der Konfiguration **[!UICONTROL Adaptives Formular und Webkanal für interaktive Kommunikation]** fest, um `https://www.google.com/` oder einen anderen benutzerdefinierten Domain-Namen anzugeben. Folgende JSON-Datei zeigt ein Beispiel:

```json
{
  "af.cloudservices.recaptcha.domain": "https://www.google.com/"
}
```

Um Konfigurationswerte festzulegen, [generieren Sie OSGi-Konfigurationen mit dem AEM-SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=de#generating-osgi-configurations-using-the-aem-sdk-quickstart) und [stellen Sie die Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=de#deployment-process) in Ihrer Cloud Service-Instanz bereit.
