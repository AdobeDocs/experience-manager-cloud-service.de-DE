---
title: Verwenden von hCAPTCHA&reg; in Kernkomponenten für adaptive AEM-Formulare
description: Mit dem hCaptcha®-Dienst können Sie die Formularsicherheit optimieren. Schrittweise Anleitung enthalten!
topic-tags: Adaptive Forms, author
keywords: CAPTCHA&reg; -Service, Adaptive Forms, CAPTCHA-Herausforderung, Bot-Prävention, Kernkomponenten, Sicherheit bei der Formularübermittlung, Spam-Abwehr bei Formularen
feature: Adaptive Forms, Core Components
exl-id: 6c559df2-7b6a-42fe-b44c-29a782570a0c
role: User, Developer
source-git-commit: 553f456f0eab43cee11fb9e66ce9e1dbacdc2b5c
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 42%

---

# Verbinden Ihrer AEM Forms-Umgebung mit hCaptcha® {#connect-your-forms-environment-with-hcaptcha-service}

<span class="preview"> Diese Funktion befindet sich im Early-Adopter-Programm. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

CAPTCHA („Completely Automated Public Turing test to tell Computers and Humans Apart“ – „vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen“) ist ein Programm, das bei Onlinetransaktionen eingesetzt wird, um zwischen Menschen und Bots oder automatisierten Programmen zu unterscheiden. Es stellt eine herausfordernde Aufgabe und bewertet die Benutzerantwort, um festzustellen, ob es sich um einen Menschen oder einen Bot handelt, der mit der Site interagiert. Dabei wird verhindert, dass der Benutzer fortfährt, wenn der Test fehlschlägt, wodurch Onlinetransaktionen sicherer werden, da Bots keinen Spam senden oder andere bösartige Zwecke verfolgen können.

AEM Forms as a Cloud Service unterstützt die folgenden CAPTCHA-Lösungen:
* [hCaptcha](#integrate-aem-forms-environment-with-hcaptcha-captcha)
* [Google reCAPTCHA](/help/forms/captcha-adaptive-forms-core-components.md)
* [hCaptcha](/help/forms/integrate-adaptive-forms-hcaptcha-core-components.md)

## Integrieren der AEM Forms-Umgebung mit hCAPTCHA

Der hCaptcha®-Dienst schützt Ihre Formulare vor Bots, Spam und automatisiertem Missbrauch. Er führt einen Kontrollkästchen-Widget-Test durch und ermittelt anhand der Benutzerantwort, ob ein Mensch oder ein Bot mit dem Formular interagiert. Dabei wird verhindert, dass Benutzende fortfahren, wenn der Test fehlschlägt. Dies erhöht die Sicherheit von Online-Transaktionen, indem Bots keinen Spam senden oder andere bösartige Aktivitäten durchführen können.

AEM Forms as a Cloud Service unterstützt hCAPTCHA® in adaptiven Forms-Kernkomponenten. Sie können damit beim Übermitteln eines Formulars eine Herausforderung für ein Kontrollkästchen-Widget darstellen.

<!-- ![hCaptcha&reg;](assets/hCaptcha&reg;-challenge.png)-->


### Voraussetzungen für die Integration der AEM Forms-Umgebung mit hCaptcha® {#prerequisite}

Um hCAPTCHA® mit AEM Forms zu konfigurieren, müssen Sie den [hCAPTCHA®-SiteKey und den geheimen Schlüssel](https://docs.hcaptcha.com/switch/#get-your-hcaptcha-sitekey-and-secret-key) von der hCAPTCHA®-Website abrufen.

### Konfigurieren von hCAPTCHA® {#steps-to-configure-hcaptcha}

Um AEM Forms mit dem hCAPTCHA®-Service zu integrieren, führen Sie die folgenden Schritte aus:

1. Erstellen Sie einen Konfigurations-Container in Ihrer AEM Forms as a Cloud Service-Umgebung. Ein Konfigurations-Container enthält Cloud-Konfigurationen, mit denen AEM mit externen Diensten verbunden wird. So erstellen und konfigurieren Sie einen Konfigurations-Container, um Ihre AEM Forms-Umgebung mit hCAPTCHA zu verbinden®:
   1. Öffnen Sie Ihre AEM Forms as a Cloud Service-Instanz.
   1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurations-Browser]**.
   1. Im Konfigurations-Browser können Sie einen vorhandenen Ordner auswählen oder einen Ordner erstellen. Sie können einen Ordner erstellen und die Cloud-Konfigurationsoption dafür aktivieren oder die Option „Cloud-Konfigurationen“ für einen vorhandenen Ordner aktivieren:

      * Erstellen eines Ordners und Aktivieren der entsprechenden Cloud-Konfigurationsoption:
         1. Klicken Sie im Konfigurations-Browser auf **[!UICONTROL Erstellen]**.
         1. Geben Sie im Dialogfeld „Konfiguration erstellen“ einen Namen und einen Titel an und wählen Sie die Option **[!UICONTROL Cloud-]**&quot;.
         1. Klicken Sie auf **[!UICONTROL Erstellen]**.
      * So aktivieren Sie die Option „Cloud-Konfigurationen“ für einen vorhandenen Ordner:
         1. Wählen Sie im Konfigurations-Browser den Ordner aus und wählen Sie **[!UICONTROL Eigenschaften]**.
         1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloud-Konfigurationen]**.
         1. Wählen Sie **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

1. Konfigurieren des Cloud-Service:
   1. Wechseln Sie in Ihrer AEM-Autoreninstanz zu ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Service]** und wählen Sie **[!UICONTROL hCaptcha®]**.
      ![hCaptcha® in der Benutzeroberfläche](assets/hcaptcha-in-ui.png)
   1. Wählen Sie einen erstellten oder aktualisierten Konfigurations-Container aus, wie im vorherigen Abschnitt beschrieben. Wählen Sie **[!UICONTROL Erstellen]** aus.
      ![Konfiguration hCAPTCHA®](assets/config-hcaptcha.png)
   1. Geben Sie **[!UICONTROL Titel]**, **[!UICONTROL Name]**, **[!UICONTROL Site-Schlüssel]** und **[!UICONTROL Geheimer Schlüssel]** für den hCAPTCHA®-Service [erhalten in PREREQUISITE](#prerequisite) an. Wählen Sie **[!UICONTROL Erstellen]** aus.

      ![Konfigurieren Sie den Cloud Service für die Verbindung Ihrer AEM Forms-Umgebung mit hCaptcha®](assets/create-hcaptcha-config.png)

   >[!NOTE]
   > Benutzende müssen die Client[seitige JavaScript-Validierungs-URL ](https://docs.hcaptcha.com/#add-the-hcaptcha-widget-to-your-webpage) die [Server-seitige Validierungs-URL](https://docs.hcaptcha.com/#verify-the-user-response-server-side) nicht ändern, da sie bereits für die hCAPTCHA®-Validierung vorausgefüllt sind.

   Sobald der hCAPTCHA-Service konfiguriert ist, kann er in einem ([ Formular, das auf Kernkomponenten basiert) verwendet ](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/introduction).

## Verwenden von hCAPTCHA® in einem {#using-hCaptcha®-core-components} für adaptive Forms-Kernkomponenten

1. Öffnen Sie Ihre AEM Forms as a Cloud Service-Instanz.
1. Gehen Sie zu **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie ein adaptives Formular und dann **[!UICONTROL Eigenschaften]** aus. Wählen Sie für die **[!UICONTROL Konfigurations-Container]** den Konfigurations-Container aus, der die Cloud-Konfiguration enthält, die AEM Forms mit hCAPTCHA® verbindet, und wählen Sie **[!UICONTROL Speichern und schließen]**.

   Wenn Sie keinen solchen Konfigurations-Container haben, erfahren Sie im Abschnitt [Verbinden Ihrer AEM Forms-Umgebung mit hCAPTCHA®](#connect-your-forms-environment-with-hcaptcha-service), wie Sie einen Konfigurations-Container erstellen.

   ![Auswählen eines Konfigurations-Containers](/help/forms/assets/captcha-properties.png)

1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **[!UICONTROL Bearbeiten]**. Das adaptive Formular wird im Editor für adaptive Formulare geöffnet.
1. Ziehen Sie im Komponenten-Browser per Drag-and-Drop die Komponente **[!UICONTROL Adaptives Formular hCAPTCHA®]** auf das adaptive Formular und fügen Sie sie hinzu.
1. Wählen Sie die Komponente **[!UICONTROL Adaptives Formular hCAPTCHA®]** aus und klicken Sie auf das Symbol ![Eigenschaften](assets/configure-icon.svg). Dadurch wird das Dialogfeld „Eigenschaften“ geöffnet. Geben Sie die folgenden Eigenschaften an:

   ![hCaptcha® v2](assets/config-hcaptcha-v2.png)

   * **[!UICONTROL Name]:** Geben Sie den Namen für Ihre CAPTCHA-Komponente an. Sie können eine Formularkomponente sowohl im Formular als auch im Regeleditor einfach mit ihrem eindeutigen Namen identifizieren.
   * **[!UICONTROL Titel]:** Geben Sie den Titel für die CAPTCHA-Komponente an.
   * **[!UICONTROL Konfigurationseinstellungen]:** Wählen Sie eine für hCaptcha® konfigurierte Cloud-Konfiguration aus.
   * **CAPTCHA-Größe** Sie können die Anzeigegröße des Dialogfelds für die hCAPTCHA®-Abfrage auswählen. Verwenden Sie die Option **[!UICONTROL Kompakt]** zur Anzeige eines kleinen und die Option **[!UICONTROL Normal]** zur Anzeige eines relativ großen Dialogfelds für den hCaptcha®-Test.<!-- or **[!UICONTROL Invisible]** to validate hCaptcha&reg; without explicitly rendering the checkbox widget on the user interface. -->
   * **[!UICONTROL Validierungsmeldung]:** Geben Sie bei der Formularübermittlung eine Validierungsmeldung für Ihre CAPTCHA-Validierung ein.
   * **[!UICONTROL Meldung zur Skriptvalidierung]**: Mit dieser Option können Sie eine Meldung eingeben, die angezeigt werden soll, wenn die Skriptvalidierung fehlschlägt.
     >[!NOTE]
     >Sie können in Ihrer Umgebung mehrere Cloud-Konfigurationen für einen ähnlichen Zweck verwenden. Wählen Sie den Dienst daher sorgfältig aus. Wenn kein Service aufgeführt ist, erfahren Sie unter [Verbinden Ihrer AEM Forms-Umgebung mit hCAPTCHA®](#connect-your-forms-environment-with-hcaptcha-service), wie Sie einen Cloud Service erstellen, der Ihre AEM Forms-Umgebung mit dem hCAPTCHA®-Service verbindet.
     <!--* **Error Message:** Provide the error message to display to the user when the Captcha submission fails.-->

1. Wählen Sie **[!UICONTROL Fertig]**.


Jetzt sind nur noch legitime Formulare für die Formularübermittlung zulässig, bei denen der Formularausfüller die vom hCAPTCHA®-Service ausgehende Herausforderung erfolgreich löscht. hCaptcha®

**hCaptcha® ist eine eingetragene Marke von Intuition Machines, Inc.**


## Häufig gestellte Fragen

* **F: Kann ich mehr als eine CAPTCHA-Komponente in einem adaptiven Formular verwenden?**
* **A:** Die Verwendung von mehr als einer CAPTCHA-Komponente in einem adaptiven Formular wird nicht unterstützt. Außerdem wird nicht empfohlen, eine CAPTCHA-Komponente in einem Fragment oder einem Bereich zu verwenden, der für verzögertes Laden markiert ist.

## Siehe auch {#see-also}

{{see-also}}
