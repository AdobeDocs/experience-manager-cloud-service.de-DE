---
title: Wie kann Turnstile in AEM Kernkomponenten adaptiver Formulare verwendet werden?
description: Verbessern Sie die Formularsicherheit mit dem Turnstile-Dienst mühelos. Schrittweise Anleitung enthalten!
topic-tags: Adaptive Forms, author
feature: Adaptive Forms, Core Components
hide: true
hidefromtoc: true
source-git-commit: d2c6514eb1f38b06dfa58daa03b781920b8928f6
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 29%

---

# AEM Forms-Umgebung mit Turnstile verbinden {#connect-your-forms-environment-with-turnstile-service}

<span class="preview"> Diese Funktion ist im Rahmen des Programms für frühzeitige Anmeldung verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

CAPTCHA („Completely Automated Public Turing test to tell Computers and Humans Apart“ – „vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen“) ist ein Programm, das bei Onlinetransaktionen eingesetzt wird, um zwischen Menschen und Bots oder automatisierten Programmen zu unterscheiden. Es stellt eine herausfordernde Aufgabe und bewertet die Benutzerantwort, um festzustellen, ob es sich um einen Menschen oder einen Bot handelt, der mit der Site interagiert. Dabei wird verhindert, dass der Benutzer fortfährt, wenn der Test fehlschlägt, wodurch Onlinetransaktionen sicherer werden, da Bots keinen Spam senden oder andere bösartige Zwecke verfolgen können.

AEM Forms as a Cloud Service unterstützt die folgenden CAPTCHA-Lösungen:


* [Cloudflare Turnstile](#integrate-aem-forms-environment-with-turnstile-captcha)
* [Google reCAPTCHA](/help/forms/captcha-adaptive-forms-core-components.md)
* [Captcha](/help/forms/integrate-adaptive-forms-hcaptcha-core-components.md)



<!-- ![Turnstile](assets/Turnstile-challenge.png)-->

## Integrieren der AEM Forms-Umgebung mit dem Turnstile Captcha

Das Turnstile Captcha von Cloudflare ist eine Sicherheitsmaßnahme, um Formulare und Sites vor automatisierten Bots, bösartigen Angriffen, Spam und unerwünschtem automatisierten Traffic zu schützen. Es wird ein Kontrollkästchen bei der Formularübermittlung angezeigt, mit dem überprüft wird, ob es sich um menschliche Formulare handelt, bevor sie das Formular senden können. AEM Forms as a Cloud Service unterstützt das Turnstile Captcha in den adaptiven Forms-Kernkomponenten.

### Voraussetzungen für die Integration der AEM Forms-Umgebung mit Turnstile Captcha {#prerequisite}

Um die Turnstile für AEM Forms-Kernkomponenten zu konfigurieren, müssen Sie [Turnstile-Site-Schlüssel und geheimer Schlüssel](https://developers.cloudflare.com/turnstile/get-started/) von der Turnstile-Website aus.

### Turnstile konfigurieren {#steps-to-configure-hcaptcha}

Führen Sie die folgenden Schritte aus, um AEM Forms mit dem Turnstile-Dienst zu integrieren:

1. Erstellen Sie einen Konfigurations-Container in Ihrer as a Cloud Service AEM Forms-Umgebung. Ein Konfigurations-Container enthält Cloud-Konfigurationen, mit denen AEM mit externen Diensten verbunden wird. So erstellen und konfigurieren Sie einen Konfigurations-Container, um Ihre AEM Forms-Umgebung mit Turnstile zu verbinden:
   1. Öffnen Sie Ihre AEM Forms as a Cloud Service-Instanz.
   1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurations-Browser]**.
   1. Im Konfigurationsbrowser können Sie einen vorhandenen Ordner auswählen oder einen Ordner erstellen. Sie können einen Ordner erstellen und die Cloud-Konfigurationsoption dafür aktivieren oder die Option „Cloud-Konfigurationen“ für einen vorhandenen Ordner aktivieren:

      * Erstellen eines Ordners und Aktivieren der entsprechenden Cloud-Konfigurationsoption:
         1. Klicken Sie im Konfigurations-Browser auf **[!UICONTROL Erstellen]**.
         1. Geben Sie im Dialogfeld &quot;Konfiguration erstellen&quot;einen Namen und einen Titel ein und wählen Sie die **[!UICONTROL Cloud-Konfigurationen]** -Option.
         1. Klicken Sie auf **[!UICONTROL Erstellen]**.
      * So aktivieren Sie die Option „Cloud-Konfigurationen“ für einen vorhandenen Ordner:
         1. Wählen Sie im Konfigurations-Browser den Ordner aus und wählen Sie **[!UICONTROL Eigenschaften]**.
         1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloud-Konfigurationen]**.
         1. Wählen Sie **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

1. Konfigurieren des Cloud-Service:
   1. Wechseln Sie in Ihrer AEM-Autoreninstanz zu ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Service]** und wählen **[!UICONTROL Turnstile]**.
      ![Turnstile in ui](assets/turnstile-in-ui.png)
   1. Wählen Sie einen Konfigurations-Container aus, der erstellt oder aktualisiert wurde, wie im vorherigen Abschnitt beschrieben. Wählen Sie **[!UICONTROL Erstellen]** aus.
      ![Konfigurationsumgebung](assets/config-hcaptcha.png)
   1. Angeben **[!UICONTROL Widget-Typ]** wie verwaltet, **[!UICONTROL Titel]**, **[!UICONTROL Name]**, **[!UICONTROL Site-Schlüssel]**, und **[!UICONTROL Geheimer Schlüssel]** für Turnstile-Dienst [in Voraussetzung erhalten](#prerequisite).
   1. Klicken Sie auf **[!UICONTROL Erstellen]**.

      ![Konfigurieren des Cloud Service für die Verbindung Ihrer AEM Forms-Umgebung mit Turnstile](assets/config-turntstile.png)

   >[!NOTE]
   > Benutzer müssen die URL für die clientseitige JavaScript-Validierung und die serverseitige Validierungs-URL nicht ändern, da sie bereits für die Turnstile-Validierung vorausgefüllt sind.

   Sobald der Turnstile Captcha-Dienst konfiguriert ist, kann er in einer [Adaptives Formular basierend auf Kernkomponenten](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/introduction).

## Verwenden von Turnstile in einem adaptiven Formular {#using-turnstile-core-components}

1. Öffnen Sie Ihre AEM Forms as a Cloud Service-Instanz.
1. Gehen Sie zu **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie ein adaptives Formular aus und wählen Sie **[!UICONTROL Eigenschaften]**. Für **[!UICONTROL Konfigurations-Container]** -Option wählen Sie den Konfigurationscontainer aus, der die Cloud-Konfiguration enthält, die AEM Forms mit der Turnstile verbindet, und wählen Sie **[!UICONTROL Speichern und schließen]**.

   Wenn Sie keinen solchen Konfigurations-Container haben, finden Sie weitere Informationen im Abschnitt . [AEM Forms-Umgebung mit Turnstile verbinden](#connect-your-forms-environment-with-turnstile-service) , um zu erfahren, wie Sie einen Konfigurations-Container erstellen.

   ![Auswählen eines Konfigurations-Containers](/help/forms/assets/captcha-properties.png)

1. Wählen Sie ein adaptives Formular aus und wählen Sie **[!UICONTROL Bearbeiten]**. Das adaptive Formular wird im Editor für adaptive Formulare geöffnet.
1. Ziehen Sie aus dem Komponenten-Browser die **[!UICONTROL Turnstile für adaptive Formulare]** auf das adaptive Formular.
1. Wählen Sie die **[!UICONTROL Turnstile für adaptive Formulare]** Komponenten- und Klickeigenschaften ![Eigenschaften-Symbol](assets/configure-icon.svg) Symbol. Dadurch wird das Dialogfeld „Eigenschaften“ geöffnet. Geben Sie die folgenden Eigenschaften an:

   ![Turnstile v2](assets/turnstile-settings-v2.png)

   * **[!UICONTROL Name]:** Geben Sie den Namen für Ihre Captcha-Komponente an. Sie können eine Formularkomponente sowohl im Formular als auch im Regeleditor leicht mit ihrem eindeutigen Namen identifizieren.
   * **[!UICONTROL Titel]:** Geben Sie den Titel für Ihre Captcha-Komponente an.
   * **[!UICONTROL Konfigurationseinstellungen]:** Wählen Sie eine für die Turnstile konfigurierte Cloud-Konfiguration aus.
   * **[!UICONTROL Validierungsmeldung]:** Stellen Sie eine Validierungsmeldung für die Validierung von Captcha bei der Formularübermittlung bereit.
   * **[!UICONTROL Überprüfungsmeldung für Skripten]**: Mit dieser Option können Sie eine Meldung eingeben, die angezeigt werden soll, wenn die Skriptvalidierung fehlschlägt.
     >[!NOTE]
     >Sie können für einen ähnlichen Zweck mehrere Cloud-Konfigurationen in Ihrer Umgebung haben. Wählen Sie den Dienst daher sorgfältig aus. Wenn kein Dienst aufgelistet ist, lesen Sie [AEM Forms-Umgebung mit Turnstile verbinden](#connect-your-forms-environment-with-turnstile-service) , um zu erfahren, wie Sie einen Cloud Service erstellen, der Ihre AEM Forms-Umgebung mit dem Turnstile-Dienst verbindet.
   * **Fehlermeldung:** Geben Sie die Fehlermeldung an, die dem Benutzer angezeigt werden soll, wenn die Captcha-Übermittlung fehlschlägt.

1. Wählen Sie **[!UICONTROL Fertig]**.


Jetzt sind nur legitime Formulare für die Formularübermittlung zulässig, bei denen der Benutzer die vom Turnstile-Dienst ausgehende Herausforderung erfolgreich löscht.

![Turnstile Challenge](assets/turnstile-challenge.png)


## Häufig gestellte Fragen

* **F: Kann ich mehrere Captcha-Komponenten in einem adaptiven Formular verwenden?**
* **Ans:** Die Verwendung von mehr als einer Captcha-Komponente in einem adaptiven Formular wird nicht unterstützt. Es wird außerdem nicht empfohlen, eine Captcha-Komponente in einem Fragment oder in einem Bereich zu verwenden, der für verzögertes Laden markiert ist.

## Siehe auch {#see-also}

{{see-also}}
