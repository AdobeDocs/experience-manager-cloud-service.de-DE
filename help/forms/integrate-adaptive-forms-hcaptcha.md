---
title: Wie wird Captcha&reg; in einem AEM adaptiven Formular verwendet?
description: Mit dem hCaptcha®-Dienst können Sie die Formularsicherheit optimieren. Schrittweise Anleitung enthalten!
topic-tags: Adaptive Forms, author
keywords: hCaptcha&reg; Service, Adaptive Forms, CAPTCHA-Herausforderung, Bot-Prävention, Sicherheit der Formularübermittlung, Form Spam-Prävention
feature: Adaptive Forms, Foundation Components
role: User, Developer
source-git-commit: 553f456f0eab43cee11fb9e66ce9e1dbacdc2b5c
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 33%

---

# Verbinden Ihrer AEM Forms-Umgebung mit Captcha® {#connect-your-forms-environment-with-hcaptcha-service}

<span class="preview"> Diese Funktion ist im Rahmen des Programms für frühzeitige Bearbeitung verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

CAPTCHA („Completely Automated Public Turing test to tell Computers and Humans Apart“ – „vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen“) ist ein Programm, das bei Onlinetransaktionen eingesetzt wird, um zwischen Menschen und Bots oder automatisierten Programmen zu unterscheiden. Es stellt eine herausfordernde Aufgabe und bewertet die Benutzerantwort, um festzustellen, ob es sich um einen Menschen oder einen Bot handelt, der mit der Site interagiert. Dabei wird verhindert, dass der Benutzer fortfährt, wenn der Test fehlschlägt, wodurch Onlinetransaktionen sicherer werden, da Bots keinen Spam senden oder andere bösartige Zwecke verfolgen können.

AEM Forms as a Cloud Service unterstützt die folgenden CAPTCHA-Lösungen:

* [hCaptcha](#integrate-aem-forms-environment-with-hcaptcha-captcha)
* [Cloudflare Turnstile](/help/forms/integrate-adaptive-forms-turnstile.md)
* [Google reCAPTCHA](/help/forms/captcha-adaptive-forms.md)

## Integrieren der AEM Forms-Umgebung mit Captcha Captcha

Der hCaptcha®-Dienst schützt Ihre Formulare vor Bots, Spam und automatisiertem Missbrauch. Er führt einen Kontrollkästchen-Widget-Test durch und ermittelt anhand der Benutzerantwort, ob ein Mensch oder ein Bot mit dem Formular interagiert. Dabei wird verhindert, dass Benutzende fortfahren, wenn der Test fehlschlägt. Dies erhöht die Sicherheit von Online-Transaktionen, indem Bots keinen Spam senden oder andere bösartige Aktivitäten durchführen können.

AEM Forms as a Cloud Service unterstützt Captcha® in Adaptive Forms. Sie können es verwenden, um eine Herausforderung für ein Kontrollkästchen-Widget bei der Formularübermittlung darzustellen.

<!-- ![hCaptcha&reg;](assets/hCaptcha&reg;-challenge.png)-->

## Voraussetzungen für die Integration der AEM Forms-Umgebung in Captcha® {#prerequisite}

Um Captcha® mit AEM Forms zu konfigurieren, müssen Sie den [hCaptcha®-Site-Schlüssel und den geheimen Schlüssel](https://docs.hcaptcha.com/switch/#get-your-hcaptcha-sitekey-and-secret-key) von der hCaptcha®-Website abrufen.

## Schritte zum Konfigurieren von Captcha® {#steps-to-configure-hcaptcha}

1. Erstellen Sie einen Konfigurations-Container in Ihrer AEM Forms as a Cloud Service-Umgebung. Ein Konfigurations-Container enthält Cloud-Konfigurationen, mit denen AEM mit externen Diensten verbunden wird. So erstellen und konfigurieren Sie einen Konfigurations-Container, um Ihre AEM Forms-Umgebung mit Captcha® zu verbinden:
   1. Öffnen Sie Ihre AEM Forms as a Cloud Service-Instanz.
   1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurations-Browser]**.
   1. Im Konfigurationsbrowser können Sie einen vorhandenen Ordner auswählen oder einen Ordner erstellen. Sie können einen Ordner erstellen und die Option Cloud-Konfigurationen dafür aktivieren oder die Option Cloud-Konfigurationen für einen vorhandenen Ordner aktivieren:

      * **So erstellen Sie einen Ordner und aktivieren die Cloud-Konfigurationsoption dafür**:
         1. Klicken Sie im Konfigurations-Browser auf **[!UICONTROL Erstellen]**.
         1. Geben Sie im Dialogfeld &quot;Konfiguration erstellen&quot;einen Namen und einen Titel ein und wählen Sie die Option **[!UICONTROL Cloud-Konfigurationen]** aus.
         1. Klicken Sie auf **[!UICONTROL Erstellen]**.
      * So aktivieren Sie die Option „Cloud-Konfigurationen“ für einen vorhandenen Ordner:
         1. Wählen Sie im Konfigurations-Browser den Ordner aus und wählen Sie **[!UICONTROL Eigenschaften]**.
         1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloud-Konfigurationen]**.
         1. Wählen Sie **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

1. Konfigurieren des Cloud-Service:
   1. Wechseln Sie in Ihrer AEM-Autoreninstanz zu ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Service]** und wählen Sie **[!UICONTROL Captcha®]** aus.
      ![hCaptcha® in ui](assets/hcaptcha-in-ui.png)
   1. Wählen Sie einen Konfigurations-Container aus, der erstellt oder aktualisiert wurde, wie im vorherigen Abschnitt beschrieben. Wählen Sie **[!UICONTROL Erstellen]** aus.
      ![Konfiguration von Captcha®](assets/config-hcaptcha.png)
   1. Geben Sie **[!UICONTROL Titel]**, **[!UICONTROL Name]**, **[!UICONTROL Site-Schlüssel]** und **[!UICONTROL Geheimschlüssel]** für den Captcha®-Dienst [an, der unter Voraussetzung](#prerequisite) abgerufen wurde. Wählen Sie **[!UICONTROL Erstellen]** aus.

      ![Konfigurieren des Cloud Service für die Verbindung Ihrer AEM Forms-Umgebung mit Captcha®](assets/create-hcaptcha-config.png)

>[!NOTE]
> Benutzer müssen die [clientseitige JavaScript-Validierungs-URL](https://docs.hcaptcha.com/#add-the-hcaptcha-widget-to-your-webpage) und die [serverseitige Validierungs-URL](https://docs.hcaptcha.com/#verify-the-user-response-server-side) nicht ändern, da sie bereits für die Captcha®-Validierung vorausgefüllt sind. Für einige Länder können die Endpunkte unterschiedlich sein. Weitere Informationen finden Sie unter [Captcha®-FAQs](https://docs.hcaptcha.com/faq#does-hcaptcha-support-access-by-users-in-china) .

Sobald der hCAPTCHA-Dienst konfiguriert ist, steht er zur Verwendung in einem adaptiven Formular zur Verfügung.

## Verwenden von Captcha® in einem adaptiven Formular{#using-hCaptcha®-foundation-components}

1. Öffnen Sie Ihre AEM Forms as a Cloud Service-Instanz.
1. Gehen Sie zu **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie ein adaptives Formular und dann **[!UICONTROL Eigenschaften]** aus. Wählen Sie für die Option **[!UICONTROL Konfigurations-Container]** den Konfigurationscontainer aus, der die Cloud-Konfiguration enthält, die AEM Forms mit Captcha® verbindet, und wählen Sie **[!UICONTROL Speichern und schließen]**.

   Wenn Sie keinen solchen Konfigurations-Container haben, finden Sie im Abschnitt [Verbinden Ihrer AEM Forms-Umgebung mit Captcha®](#connect-your-forms-environment-with-hcaptcha-service) Informationen zum Erstellen eines Konfigurations-Containers.

   ![Auswählen eines Konfigurations-Containers](/help/forms/assets/captcha-properties.png)

1. Wählen Sie ein adaptives Formular und danach **[!UICONTROL Bearbeiten]** aus. Das adaptive Formular wird im Editor für adaptive Formulare geöffnet.
1. Ziehen Sie die **[!UICONTROL CAPTCHA]**-Komponente im Komponentenbrowser in das adaptive Formular und legen Sie sie dort ab.
1. Wählen Sie die Komponente **[!UICONTROL Captcha]** aus und klicken Sie auf das Symbol für die Eigenschaften ![Symbol Eigenschaften](assets/configure-icon.svg) . Dadurch wird das Dialogfeld &quot;Eigenschaften&quot;geöffnet.

   ![Alt-Text](assets/hcaptcha-properties.png)

   Geben Sie die folgenden Eigenschaften an:

   * **[!UICONTROL Titel]:** Geben Sie den Titel für Ihre Captcha-Komponente an. Sie können eine Formularkomponente einfach mit ihrem eindeutigen Namen sowohl im Formular als auch im Regeleditor identifizieren.
   * **[!UICONTROL Validierungsmeldung]:** Stellen Sie eine Validierungsmeldung für Ihre Captcha-Validierung bei der Formularübermittlung bereit.
   * **[!UICONTROL Captcha validieren]:** Sie können eine der Optionen auswählen, um Captcha zu validieren:
      * Formular-Übermittlung
      * Bei einer Benutzeraktion.
   * **[!UICONTROL Captcha-Dienst]:** Wählen Sie Ihren Captcha-Dienst, hier wählen Sie den Captcha®-Dienst aus.
   * **[!UICONTROL Captcha-Konfiguration]:** Wählen Sie eine für Captcha® konfigurierte Cloud-Konfiguration.
     >[!NOTE]
     >Sie können für einen ähnlichen Zweck mehrere Cloud-Konfigurationen in Ihrer Umgebung haben. Wählen Sie den Dienst daher sorgfältig aus. Wenn kein Dienst aufgeführt ist, finden Sie unter [Verbinden Ihrer AEM Forms-Umgebung mit Captcha®](#connect-your-forms-environment-with-hcaptcha-service) Informationen zum Erstellen eines Cloud Service, der Ihre AEM Forms-Umgebung mit dem Captcha®-Dienst verbindet.

   * **Fehlermeldung:** Geben Sie die Fehlermeldung an, die dem Benutzer angezeigt werden soll, wenn die Captcha-Übermittlung fehlschlägt.
   * **Captcha-Größe:** Sie wählen die Anzeigegröße des Chaptcha®-Challenger-Dialogfelds aus. Verwenden Sie die Option **[!UICONTROL Kompakt]** , um eine kleine Größe anzuzeigen, und die Option **[!UICONTROL Normal]**, um ein relativ großes Chaptcha®-Anforderungsdialogfeld anzuzeigen, oder **[!UICONTROL Unsichtbar]**, um hCaptcha® zu validieren, ohne das Kontrollkästchen-Widget in der Benutzeroberfläche explizit darzustellen.

1. Wählen Sie **[!UICONTROL Fertig]**.

Jetzt sind nur legitime Formulare für die Formularübermittlung zulässig, bei denen der Formularbenutzer die vom Captcha®-Dienst ausgehende Herausforderung erfolgreich löscht.

**hCaptcha® ist eine eingetragene Marke von Intuition Machines, Inc.**

## Häufig gestellte Fragen

* **Q: Kann ich mehrere Captcha-Komponenten in einem adaptiven Formular verwenden?**
* **s:** Die Verwendung von mehr als einer Captcha-Komponente in einem adaptiven Formular wird nicht unterstützt. Es wird außerdem nicht empfohlen, eine Captcha-Komponente in einem Fragment oder in einem Bereich zu verwenden, der für verzögertes Laden markiert ist.

## Siehe auch {#see-also}

{{see-also}}
