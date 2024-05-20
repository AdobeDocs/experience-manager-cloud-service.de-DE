---
title: Wie wird Captcha® in einem AEM adaptiven Formular verwendet?
description: Verbessern Sie die Formularsicherheit mit dem hCaptcha®-Dienst mühelos. Schrittweise Anleitung enthalten!
topic-tags: Adaptive Forms, author
keywords: hCaptcha®-Dienst, Adaptive Forms, CAPTCHA-Herausforderung, Bot-Prävention, Formularübermittlungssicherheit, Form-Spam-Prävention
feature: Adaptive Forms, Foundation Components
hide: true
hidefromtoc: true
source-git-commit: a8a31bae0f937aa8941d258af648d6be030a9fac
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 17%

---


# Verbinden Ihrer AEM Forms-Umgebung mit Captcha® {#connect-your-forms-environment-with-hcaptcha-service}

<span class="preview"> Diese Funktion ist im Rahmen des Programms für frühzeitige Anmeldung verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

Der Captcha®-Dienst schützt Ihre Formulare vor Bots, Spam und automatisiertem Missbrauch. Es stellt eine Checkbox-Widget-Herausforderung dar und wertet die Benutzerantwort aus, um festzustellen, ob es sich um einen Menschen oder einen Bot handelt, der mit dem Formular interagiert. Dies verhindert, dass der Benutzer fortfährt, wenn der Test fehlschlägt, und hilft, Online-Transaktionen sicher zu machen, indem Bots davon abgehalten werden, Spam oder böswillige Aktivitäten zu posten.

<!-- ![hCaptcha®](assets/hCaptcha®-challenge.png)-->

AEM Forms as a Cloud Service unterstützt Captcha® in Adaptive Forms. Sie können es verwenden, um dem Benutzer bei der Formularübermittlung eine Herausforderung für das Kontrollkästchen-Widget zu stellen.

## Voraussetzungen für die Integration der AEM Forms-Umgebung in Captcha® {#prerequisite}

Um Captcha® mit AEM Forms zu konfigurieren, müssen Sie den [Captcha®-Site-Schlüssel und geheimer Schlüssel](https://docs.hcaptcha.com/switch/#get-your-hcaptcha-sitekey-and-secret-key) von der Captcha®-Website.

## Schritte zum Konfigurieren von Captcha® {#steps-to-configure-hcaptcha}

1. Erstellen Sie einen Konfigurations-Container in Ihrer as a Cloud Service AEM Forms-Umgebung. Ein Konfigurations-Container enthält Cloud-Konfigurationen, mit denen AEM mit externen Diensten verbunden wird. So erstellen und konfigurieren Sie einen Konfigurations-Container, um Ihre AEM Forms-Umgebung mit Captcha® zu verbinden:
   1. Öffnen Sie Ihre AEM Forms as a Cloud Service-Instanz.
   1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurations-Browser]**.
   1. Im Konfigurationsbrowser können Sie einen vorhandenen Ordner auswählen oder einen Ordner erstellen. Sie können einen Ordner erstellen und die Option Cloud-Konfigurationen dafür aktivieren oder die Option Cloud-Konfigurationen für einen vorhandenen Ordner aktivieren:

      * **So erstellen Sie einen Ordner und aktivieren die entsprechende Cloud-Konfigurationsoption**:
         1. Klicken Sie im Konfigurations-Browser auf **[!UICONTROL Erstellen]**.
         1. Geben Sie im Dialogfeld &quot;Konfiguration erstellen&quot;einen Namen und einen Titel ein und wählen Sie die **[!UICONTROL Cloud-Konfigurationen]** -Option.
         1. Klicken Sie auf **[!UICONTROL Erstellen]**.
      * So aktivieren Sie die Option „Cloud-Konfigurationen“ für einen vorhandenen Ordner:
         1. Wählen Sie im Konfigurations-Browser den Ordner aus und wählen Sie **[!UICONTROL Eigenschaften]**.
         1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloud-Konfigurationen]**.
         1. Wählen Sie **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

1. Konfigurieren des Cloud-Service:
   1. Wechseln Sie in Ihrer AEM-Autoreninstanz zu ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Service]** und wählen **[!UICONTROL hCaptcha®]**.
      ![hCaptcha® in ui](assets/hcaptcha-in-ui.png)
   1. Wählen Sie einen Konfigurations-Container aus, der erstellt oder aktualisiert wurde, wie im vorherigen Abschnitt beschrieben. Wählen Sie **[!UICONTROL Erstellen]** aus.
      ![Konfiguration Captcha®](assets/config-hcaptcha.png)
   1. Angeben **[!UICONTROL Titel]**, **[!UICONTROL Name]**, **[!UICONTROL Site-Schlüssel]**, und **[!UICONTROL Geheimer Schlüssel]** für den hCaptcha®-Dienst [in Voraussetzung erhalten](#prerequisite). Wählen Sie **[!UICONTROL Erstellen]** aus.

      ![Konfigurieren des Cloud Service für die Verbindung Ihrer AEM Forms-Umgebung mit Captcha®](assets/create-hcaptcha-config.png)

>[!NOTE]
> Benutzer müssen [Clientseitige URL zur JavaScript-Überprüfung](https://docs.hcaptcha.com/#add-the-hcaptcha-widget-to-your-webpage) und [URL zur serverseitigen Validierung](https://docs.hcaptcha.com/#verify-the-user-response-server-side) da sie bereits für die hCaptcha®-Validierung vorausgefüllt sind. Für einige Länder können die Endpunkte unterschiedlich sein, siehe [Häufig gestellte Fragen zu Captcha®](https://docs.hcaptcha.com/faq#does-hcaptcha-support-access-by-users-in-china) für weitere Informationen.

Sobald der hCAPTCHA-Dienst konfiguriert ist, steht er zur Verwendung in einem adaptiven Formular zur Verfügung.

## Verwenden von Captcha® in einem adaptiven Formular{#using-hCaptcha®-foundation-components}

1. Öffnen Sie Ihre AEM Forms as a Cloud Service-Instanz.
1. Gehen Sie zu **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie ein adaptives Formular aus und wählen Sie **[!UICONTROL Eigenschaften]**. Für **[!UICONTROL Konfigurations-Container]** Wählen Sie den Konfigurationscontainer aus, der die Cloud-Konfiguration enthält, die AEM Forms mit Captcha® verbindet, und wählen Sie **[!UICONTROL Speichern und schließen]**.

   Wenn Sie keinen solchen Konfigurations-Container haben, finden Sie weitere Informationen im Abschnitt . [Verbinden Ihrer AEM Forms-Umgebung mit Captcha®](#connect-your-forms-environment-with-hcaptcha-service) , um zu erfahren, wie Sie einen Konfigurations-Container erstellen.

   ![Auswählen eines Konfigurations-Containers](/help/forms/assets/captcha-properties.png)

1. Wählen Sie ein adaptives Formular aus und wählen Sie **[!UICONTROL Bearbeiten]**. Das adaptive Formular wird im Editor für adaptive Formulare geöffnet.
1. Ziehen Sie die **[!UICONTROL CAPTCHA]**-Komponente im Komponentenbrowser in das adaptive Formular und legen Sie sie dort ab.
1. Wählen Sie die **[!UICONTROL Captcha]** Komponente und auf Eigenschaften klicken ![Eigenschaften-Symbol](assets/configure-icon.svg) Symbol. Dadurch wird das Dialogfeld &quot;Eigenschaften&quot;geöffnet.

   ![Alternativtext](assets/hcaptcha-properties.png)

   Geben Sie die folgenden Eigenschaften an:

   * **[!UICONTROL Titel]:** Geben Sie den Titel für Ihre Captcha-Komponente an. Sie können eine Formularkomponente sowohl im Formular als auch im Regeleditor leicht mit ihrem eindeutigen Namen identifizieren.
   * **[!UICONTROL Validierungsmeldung]:** Stellen Sie eine Validierungsmeldung für Ihre Captcha-Validierung bei der Formularübermittlung bereit.
   * **[!UICONTROL Captcha überprüfen]:** Sie können eine der Optionen zum Validieren von Captcha auswählen:
      * Formular-Übermittlung
      * Bei einer Benutzeraktion.
   * **[!UICONTROL Captcha Service]:** Wählen Sie Ihren Captcha-Dienst aus, hier wählen Sie Captcha®-Dienst.
   * **[!UICONTROL Captcha-Konfiguration]:** Wählen Sie eine für Captcha® konfigurierte Cloud-Konfiguration.
     >[!NOTE]
     >Sie können für einen ähnlichen Zweck mehrere Cloud-Konfigurationen in Ihrer Umgebung haben. Wählen Sie den Dienst daher sorgfältig aus. Wenn kein Dienst aufgelistet ist, lesen Sie [Verbinden Ihrer AEM Forms-Umgebung mit Captcha®](#connect-your-forms-environment-with-hcaptcha-service) Erfahren Sie, wie Sie einen Cloud Service erstellen, der Ihre AEM Forms-Umgebung mit dem Captcha®-Dienst verbindet.

   * **Fehlermeldung:** Geben Sie die Fehlermeldung an, die dem Benutzer angezeigt werden soll, wenn die Captcha-Übermittlung fehlschlägt.
   * **Captcha Size:** Sie wählen die Anzeigegröße des Challenge-Dialogfelds. Verwenden Sie die **[!UICONTROL Kompakt]** Option zur Anzeige einer kleinen Größe und **[!UICONTROL Normal]** Option zum Anzeigen eines relativ großen Chaptcha®-Challenger-Challenger-Dialogfelds oder **[!UICONTROL Unsichtbar]** um hCaptcha® zu validieren, ohne das Kontrollkästchen-Widget in der Benutzeroberfläche explizit zu rendern.

1. Wählen Sie **[!UICONTROL Fertig]**.

Jetzt sind nur legitime Formulare für die Formularübermittlung zulässig, bei denen der Formularbenutzer die vom Captcha®-Dienst ausgehende Herausforderung erfolgreich löscht.

**hCaptcha® ist eine eingetragene Marke von Intuition Machines, Inc.**

## Häufig gestellte Fragen

* **F: Kann ich mehrere Captcha-Komponenten in einem adaptiven Formular verwenden?**
* **Ans:** Die Verwendung von mehr als einer Captcha-Komponente in einem adaptiven Formular wird nicht unterstützt. Es wird außerdem nicht empfohlen, eine Captcha-Komponente in einem Fragment oder in einem Bereich zu verwenden, der für verzögertes Laden markiert ist.

## Siehe auch {#see-also}

{{see-also}}
