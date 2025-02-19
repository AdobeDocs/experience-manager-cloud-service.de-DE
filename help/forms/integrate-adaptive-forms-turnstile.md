---
title: Verwenden von Drehkreuz in einem adaptiven Formular von AEM
description: Verbessern Sie die Formularsicherheit mit dem Drehkreuz-Service mühelos. Schrittweise Anleitung enthalten!
topic-tags: Adaptive Forms, author
feature: Adaptive Forms, Foundation Components
role: User, Developer
exl-id: 644c351b-a167-4d18-8b99-b7cae6be48d5
source-git-commit: 914139a6340f15ee77024793bf42fa30c913931e
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 26%

---

# Integrieren von Turnstile CAPTCHA mit Adaptive Forms

<span class="preview"> Diese Funktion befindet sich im Early-Adopter-Programm. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

CAPTCHA („Completely Automated Public Turing test to tell Computers and Humans Apart“ – „vollautomatischer öffentlicher Turing-Test zur Unterscheidung von Computern und Menschen“) ist ein Programm, das bei Onlinetransaktionen eingesetzt wird, um zwischen Menschen und Bots oder automatisierten Programmen zu unterscheiden. Es stellt eine herausfordernde Aufgabe und bewertet die Benutzerantwort, um festzustellen, ob es sich um einen Menschen oder einen Bot handelt, der mit der Site interagiert. Dabei wird verhindert, dass der Benutzer fortfährt, wenn der Test fehlschlägt, wodurch Onlinetransaktionen sicherer werden, da Bots keinen Spam senden oder andere bösartige Zwecke verfolgen können.

AEM Forms as a Cloud Service unterstützt die folgenden CAPTCHA-Lösungen:

* [Cloudflare Turnstile](#integrate-aem-forms-environment-with-turnstile-captcha)
* [Google reCAPTCHA](/help/forms/captcha-adaptive-forms.md)
* [hCaptcha](/help/forms/integrate-adaptive-forms-hcaptcha.md)

## Integrieren der AEM Forms-Umgebung mit Turnstile Captcha

Cloudflare&#39;s Turnstile Captcha ist eine Sicherheitsmaßnahme, die darauf abzielt, Formulare und Websites vor automatischen Bots, bösartigen Angriffen, Spam und unerwünschtem automatisierten Traffic zu schützen. Bei der Formularübermittlung wird ein Kontrollkästchen angezeigt, mit dem Sie überprüfen können, ob es sich um menschliche Daten handelt, bevor Sie ihnen das Senden des Formulars ermöglichen. AEM Forms as a Cloud Service unterstützt Drehkreuz-Captcha in adaptivem Forms.

<!-- ![Turnstile](assets/Turnstile-challenge.png)-->

### Voraussetzungen für die Integration der AEM Forms-Umgebung mit Turnstile Captcha {#prerequisite}

Um das Drehkreuz für AEM Forms zu konfigurieren, müssen Sie den [Standortschlüssel und geheimen Schlüssel des Drehkreuzes](https://developers.cloudflare.com/turnstile/get-started/) von der Website des Drehkreuzes abrufen.

### Schritte zum Konfigurieren des Drehkreuzes für AEM Forms{#steps-to-configure-turnstile}

1. Erstellen Sie einen Konfigurations-Container in Ihrer AEM Forms as a Cloud Service-Umgebung. Ein Konfigurations-Container enthält Cloud-Konfigurationen, mit denen AEM mit externen Diensten verbunden wird. So erstellen und konfigurieren Sie einen Konfigurations-Container, um Ihre AEM Forms-Umgebung mit Turnstile zu verbinden:
   1. Öffnen Sie Ihre AEM Forms as a Cloud Service-Instanz.
   1. Wählen Sie **[!UICONTROL Tools > Allgemein > Konfigurations-Browser]**.
   1. Im Konfigurations-Browser können Sie einen vorhandenen Ordner auswählen oder einen Ordner erstellen. Sie können einen Ordner erstellen und die Option Cloud-Konfigurationen dafür aktivieren oder die Option Cloud-Konfigurationen für einen vorhandenen Ordner aktivieren:

      * **So erstellen Sie einen Ordner und aktivieren die Option Cloud-Konfigurationen**:
         1. Klicken Sie im Konfigurations-Browser auf **[!UICONTROL Erstellen]**.
         1. Geben Sie im Dialogfeld „Konfiguration erstellen“ einen Namen und einen Titel an und wählen Sie die Option **[!UICONTROL Cloud-]**&quot;.
         1. Klicken Sie auf **[!UICONTROL Erstellen]**.
      * So aktivieren Sie die Option „Cloud-Konfigurationen“ für einen vorhandenen Ordner:
         1. Wählen Sie im Konfigurations-Browser den Ordner aus und wählen Sie **[!UICONTROL Eigenschaften]**.
         1. Aktivieren Sie im Dialogfeld „Konfigurationseigenschaften“ die Option **[!UICONTROL Cloud-Konfigurationen]**.
         1. Wählen Sie **[!UICONTROL Speichern und schließen]**, um die Konfiguration zu speichern und das Dialogfeld zu schließen.

1. Konfigurieren des Cloud-Service:
   1. Navigieren Sie in Ihrer AEM-Autoreninstanz zu ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Services]** und wählen Sie **[!UICONTROL Drehkreuz]**.
      ![Drehkreuz in der Benutzeroberfläche](assets/turnstile-in-ui.png)
   1. Wählen Sie einen erstellten oder aktualisierten Konfigurations-Container aus, wie im vorherigen Abschnitt beschrieben. Wählen Sie **[!UICONTROL Erstellen]** aus.
      ![Konfigurations-Drehkreuz](assets/config-hcaptcha.png)
   1. Geben Sie **[!UICONTROL Widget-Typ]** als verwaltet an. Der Widget-Typ kann sich ändern, was von dem Schlüssel abhängt, der in den Voraussetzungen **[!UICONTROL Titel]**, **[!UICONTROL Name]**, **[!UICONTROL Site-Schlüssel]** und **[!UICONTROL Geheimer Schlüssel]** für den Drehkreuz-Dienst [erhalten in Voraussetzung](#prerequisite) wurde. Wählen Sie **[!UICONTROL Erstellen]** aus.

      ![Konfigurieren Sie den Cloud Service, um Ihre AEM Forms-Umgebung mit Turnstile zu verbinden](assets/config-turntstile.png)

>[!NOTE]
> Benutzende müssen die Client-seitige JavaScript-Validierungs-URL und die Server-seitige Validierungs-URL nicht ändern, da sie bereits für die Drehkreuz-Validierung vorausgefüllt sind.

Sobald der Service „Drehkreuz-CAPTCHA“ konfiguriert ist, kann er in einem adaptiven Formular verwendet werden.

## Verwenden von Turnstile in einem adaptiven Formular{#using-turnstile-foundation-components}

1. Öffnen Sie Ihre AEM Forms as a Cloud Service-Instanz.
1. Gehen Sie zu **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie ein adaptives Formular und dann **[!UICONTROL Eigenschaften]** aus. Wählen Sie für die **[!UICONTROL Konfigurations-Container]** den Konfigurations-Container aus, der die Cloud-Konfiguration enthält, die AEM Forms mit Turnstile verbindet, und wählen Sie **[!UICONTROL Speichern und schließen]**.

   Wenn Sie keinen solchen Konfigurations-Container haben, erfahren Sie im Abschnitt [Verbinden Ihrer AEM Forms-Umgebung mit Turnstile](#connect-your-forms-environment-with-turnstile-service), wie Sie einen Konfigurations-Container erstellen.

   ![Auswählen eines Konfigurations-Containers](/help/forms/assets/captcha-properties.png)

1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **[!UICONTROL Bearbeiten]**. Das adaptive Formular wird im Editor für adaptive Formulare geöffnet.
1. Ziehen Sie die **[!UICONTROL CAPTCHA]**-Komponente im Komponentenbrowser in das adaptive Formular und legen Sie sie dort ab.
1. Wählen Sie die **[!UICONTROL CAPTCHA]**-Komponente aus und klicken Sie auf das Symbol ![Eigenschaften](assets/configure-icon.svg). Dadurch wird das Dialogfeld „Eigenschaften“ geöffnet.

   ![Einstellungen](assets/turnstile-setting-v1.png)

   Geben Sie die folgenden Eigenschaften an:

   * **[!UICONTROL Titel]:** Geben Sie den Titel für Ihre CAPTCHA-Komponente an. Sie können eine Formularkomponente sowohl im Formular als auch im Regeleditor einfach mit ihrem eindeutigen Namen identifizieren.
   * **[!UICONTROL Validierungsmeldung]:** Geben Sie eine Validierungsmeldung zur Validierung von CAPTCHA bei der Formularübermittlung ein.
   * **[!UICONTROL CAPTCHA validieren]:** Sie können eine der Optionen auswählen, um CAPTCHA zu validieren:
      * Bei Formularübermittlung
      * Bei einer Benutzeraktion.
   * **[!UICONTROL CAPTCHA-]:** Wählen Sie Ihren CAPTCHA-Dienst aus, hier wählen Sie Cloudfare Turnstile CAPTCHA-Dienst.
   * **[!UICONTROL CAPTCHA-Konfiguration]:** Wählen Sie eine Cloud-Konfiguration aus, die für Drehkreuz konfiguriert ist. Hier wählen Sie beispielsweise den **verwalteten Schlüssel** aus.

     >[!NOTE]
     >
     > Sie können in Ihrer Umgebung mehrere Cloud-Konfigurationen für einen ähnlichen Zweck verwenden. Wählen Sie den Dienst daher sorgfältig aus. Wenn kein Service aufgeführt ist, erfahren Sie unter [Verbinden Ihrer AEM Forms-Umgebung mit Turnstile](#connect-your-forms-environment-with-turnstile-service), wie Sie einen Cloud Service erstellen, der Ihre AEM Forms-Umgebung mit dem Turnstile-Service verbindet.

   * **Fehlermeldung:** Geben Sie die Fehlermeldung an, die Benutzern angezeigt werden soll, wenn die CAPTCHA-Übermittlung fehlschlägt.
   * **CAPTCHA-Größe** Sie wählen die Anzeigegröße des Dialogfelds „Drehkreuz-Herausforderung“ aus. Verwenden Sie die Option **[!UICONTROL Kompakt]**, um eine kleine Größe anzuzeigen, und die Option **[!UICONTROL Normal]**, um ein relativ großes Dialogfeld für die Drehkreuz-Herausforderung anzuzeigen.


     >[!NOTE]
     >Dies gilt für den Widget-Typ „Verwaltet“ und „Nicht interaktiv“. Wenn der Widget-Typ nicht sichtbar ist, ist die Größeneigenschaft nicht erforderlich und sie ist deaktiviert.

1. Wählen Sie **[!UICONTROL Fertig]**.

Für die Formularübermittlung sind jetzt nur noch Formulare zulässig, in denen der Formularbenutzer die vom Dienst „Drehkreuz“ ausgehende Herausforderung erfolgreich löscht.

![Turnstile Challenge](assets/turnstile-challenge.png)

## Häufig gestellte Fragen

* **F: Kann ich mehr als eine CAPTCHA-Komponente in einem adaptiven Formular verwenden?**
* **A:** Die Verwendung von mehr als einer CAPTCHA-Komponente in einem adaptiven Formular wird nicht unterstützt. Außerdem wird nicht empfohlen, eine CAPTCHA-Komponente in einem Fragment oder einem Bereich zu verwenden, der für verzögertes Laden markiert ist.

## Siehe auch {#see-also}

{{see-also}}
