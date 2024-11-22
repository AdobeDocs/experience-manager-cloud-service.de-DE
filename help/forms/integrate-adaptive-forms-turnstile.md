---
title: Wie wird Turnstile in einem AEM adaptiven Formular verwendet?
description: Verbessern Sie die Formularsicherheit mit dem Turnstile-Dienst mühelos. Schrittweise Anleitung enthalten!
topic-tags: Adaptive Forms, author
feature: Adaptive Forms, Foundation Components
role: User, Developer
source-git-commit: 553f456f0eab43cee11fb9e66ce9e1dbacdc2b5c
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 26%

---


# Integrieren von Turnstile CAPTCHA mit Adaptive Forms

<span class="preview"> Diese Funktion ist im Rahmen des Programms für frühzeitige Bearbeitung verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

CAPTCHA („Completely Automated Public Turing test to tell Computers and Humans Apart“ – „vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen“) ist ein Programm, das bei Onlinetransaktionen eingesetzt wird, um zwischen Menschen und Bots oder automatisierten Programmen zu unterscheiden. Es stellt eine herausfordernde Aufgabe und bewertet die Benutzerantwort, um festzustellen, ob es sich um einen Menschen oder einen Bot handelt, der mit der Site interagiert. Dabei wird verhindert, dass der Benutzer fortfährt, wenn der Test fehlschlägt, wodurch Onlinetransaktionen sicherer werden, da Bots keinen Spam senden oder andere bösartige Zwecke verfolgen können.

AEM Forms as a Cloud Service unterstützt die folgenden CAPTCHA-Lösungen:

* [Cloudflare Turnstile](#integrate-aem-forms-environment-with-turnstile-captcha)
* [Google reCAPTCHA](/help/forms/captcha-adaptive-forms.md)
* [hCaptcha](/help/forms/integrate-adaptive-forms-hcaptcha.md)

## Integrieren der AEM Forms-Umgebung mit dem Turnstile Captcha

Das Turnstile Captcha von Cloudflare ist eine Sicherheitsmaßnahme, um Formulare und Sites vor automatisierten Bots, bösartigen Angriffen, Spam und unerwünschtem automatisierten Traffic zu schützen. Es wird ein Kontrollkästchen bei der Formularübermittlung angezeigt, mit dem überprüft wird, ob es sich um menschliche Formulare handelt, bevor sie das Formular senden können. AEM Forms as a Cloud Service unterstützt das Turnstile Captcha in Adaptive Forms.

<!-- ![Turnstile](assets/Turnstile-challenge.png)-->

### Voraussetzungen für die Integration der AEM Forms-Umgebung mit Turnstile Captcha {#prerequisite}

Um die Turnstile für AEM Forms zu konfigurieren, müssen Sie den [Turnstile-SiteKey und den geheimen Schlüssel](https://developers.cloudflare.com/turnstile/get-started/) von der Turnstile-Website abrufen.

### Schritte zum Konfigurieren der Turnstile für AEM Forms{#steps-to-configure-turnstile}

1. Erstellen Sie einen Konfigurations-Container in Ihrer AEM Forms as a Cloud Service-Umgebung. Ein Konfigurations-Container enthält Cloud-Konfigurationen, mit denen AEM mit externen Diensten verbunden wird. So erstellen und konfigurieren Sie einen Konfigurations-Container, um Ihre AEM Forms-Umgebung mit Turnstile zu verbinden:
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
   1. Wechseln Sie in Ihrer AEM-Autoreninstanz zu ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Service]** und wählen Sie **[!UICONTROL Turnstile]** aus.
      ![Turnstile in ui](assets/turnstile-in-ui.png)
   1. Wählen Sie einen Konfigurations-Container aus, der erstellt oder aktualisiert wurde, wie im vorherigen Abschnitt beschrieben. Wählen Sie **[!UICONTROL Erstellen]** aus.
      ![Konfigurations-Turnstile](assets/config-hcaptcha.png)
   1. Geben Sie den **[!UICONTROL Widget-Typ]** als verwalteten Widget-Typ an. Der Widget-Typ kann sich ändern, je nach dem Schlüssel, der in der Voraussetzung abgerufen wurde, **[!UICONTROL Titel]**, **[!UICONTROL Name]**, **[!UICONTROL Site-Schlüssel]** und **[!UICONTROL Geheimschlüssel]** für den Turnstile-Dienst [, der unter Voraussetzung ](#prerequisite) abgerufen wurde. Wählen Sie **[!UICONTROL Erstellen]** aus.

      ![Konfigurieren des Cloud Service für die Verbindung Ihrer AEM Forms-Umgebung mit der Turnstile](assets/config-turntstile.png)

>[!NOTE]
> Benutzer müssen die clientseitige JavaScript-Validierungs-URL und die serverseitige Validierungs-URL nicht ändern, da sie bereits für die Turnstile-Validierung vorausgefüllt sind.

Sobald der Turnstile Captcha-Dienst konfiguriert ist, ist er zur Verwendung in einem adaptiven Formular verfügbar.

## Verwenden von Turnstile in einem adaptiven Formular{#using-turnstile-foundation-components}

1. Öffnen Sie Ihre AEM Forms as a Cloud Service-Instanz.
1. Gehen Sie zu **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie ein adaptives Formular und dann **[!UICONTROL Eigenschaften]** aus. Wählen Sie für die Option **[!UICONTROL Konfigurations-Container]** den Konfigurationscontainer aus, der die Cloud-Konfiguration enthält, die AEM Forms mit der Turnstile verbindet, und wählen Sie **[!UICONTROL Speichern und schließen]** aus.

   Wenn Sie über keinen solchen Konfigurations-Container verfügen, finden Sie im Abschnitt [Verbinden Ihrer AEM Forms-Umgebung mit Turnstile](#connect-your-forms-environment-with-turnstile-service) Informationen zum Erstellen eines Konfigurations-Containers.

   ![Auswählen eines Konfigurations-Containers](/help/forms/assets/captcha-properties.png)

1. Wählen Sie ein adaptives Formular und danach **[!UICONTROL Bearbeiten]** aus. Das adaptive Formular wird im Editor für adaptive Formulare geöffnet.
1. Ziehen Sie die **[!UICONTROL CAPTCHA]**-Komponente im Komponentenbrowser in das adaptive Formular und legen Sie sie dort ab.
1. Wählen Sie die Komponente **[!UICONTROL Captcha]** aus und klicken Sie auf das Symbol für die Eigenschaften ![Symbol Eigenschaften](assets/configure-icon.svg) . Dadurch wird das Dialogfeld &quot;Eigenschaften&quot;geöffnet.

   ![Einstellungen](assets/turnstile-setting-v1.png)

   Geben Sie die folgenden Eigenschaften an:

   * **[!UICONTROL Titel]:** Geben Sie den Titel für Ihre Captcha-Komponente an. Sie können eine Formularkomponente einfach mit ihrem eindeutigen Namen sowohl im Formular als auch im Regeleditor identifizieren.
   * **[!UICONTROL Validierungsmeldung]:** Stellen Sie eine Validierungsmeldung für die Validierung von Captcha bei Formularübermittlung bereit.
   * **[!UICONTROL Captcha validieren]:** Sie können eine der Optionen auswählen, um Captcha zu validieren:
      * Formular-Übermittlung
      * Bei einer Benutzeraktion.
   * **[!UICONTROL Captcha-Dienst]:** Wählen Sie Ihren Captcha-Dienst, hier wählen Sie den Cloudfare Turnstile Captcha-Dienst aus.
   * **[!UICONTROL Captcha-Konfiguration]:** Wählen Sie eine Cloud-Konfiguration, die für die Turnstile konfiguriert ist. Hier wählen Sie beispielsweise den Schlüssel **managed** aus.
     >[!NOTE]
     >Sie können für einen ähnlichen Zweck mehrere Cloud-Konfigurationen in Ihrer Umgebung haben. Wählen Sie den Dienst daher sorgfältig aus. Wenn kein Dienst aufgelistet ist, finden Sie unter [Verbinden Ihrer AEM Forms-Umgebung mit Turnstile](#connect-your-forms-environment-with-turnstile-service) Informationen zum Erstellen eines Cloud Service, der Ihre AEM Forms-Umgebung mit dem Turnstile-Dienst verbindet.

   * **Fehlermeldung:** Geben Sie die Fehlermeldung an, die dem Benutzer angezeigt werden soll, wenn die Captcha-Übermittlung fehlschlägt.
   * **Captcha Size:** Sie wählen die Anzeigegröße des Dialogfelds &quot;Turnstile-Herausforderung&quot;aus. Verwenden Sie die Option **[!UICONTROL Kompakt]** , um eine kleine Größe anzuzeigen, und die Option **[!UICONTROL Normal]** , um ein relativ großes Dialogfeld mit der Turnstile-Herausforderung anzuzeigen.


     >[!NOTE]
     >Dies gilt für den Widget-Typ &quot;Managed&quot;und &quot;Non-Interactive&quot;. Wenn der Widget-Typ nicht sichtbar ist, ist die size-Eigenschaft nicht erforderlich und deaktiviert.

1. Wählen Sie **[!UICONTROL Fertig]**.

Jetzt sind nur legitime Formulare für die Formularübermittlung zulässig, bei denen der Benutzer die vom Turnstile-Dienst ausgehende Herausforderung erfolgreich löscht.

![Turnstile-Herausforderung](assets/turnstile-challenge.png)

## Häufig gestellte Fragen

* **Q: Kann ich mehrere Captcha-Komponenten in einem adaptiven Formular verwenden?**
* **s:** Die Verwendung von mehr als einer Captcha-Komponente in einem adaptiven Formular wird nicht unterstützt. Es wird außerdem nicht empfohlen, eine Captcha-Komponente in einem Fragment oder in einem Bereich zu verwenden, der für verzögertes Laden markiert ist.

## Siehe auch {#see-also}

{{see-also}}
