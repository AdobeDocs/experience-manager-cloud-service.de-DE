---
title: Verwenden von reCAPTCHA mit Edge Delivery Services für AEM Forms as a Cloud Service
description: Verwenden von Google reCAPTCHA in einem Formular für Edge Delivery Services für AEM Forms
feature: Edge Delivery Services
exl-id: ac104e23-f175-435f-8414-19847efa5825
role: Admin, Architect, Developer
source-git-commit: 4a8153ffbdbc4da401089ca0a6ef608dc2c53b22
workflow-type: tm+mt
source-wordcount: '848'
ht-degree: 100%

---


# Verwenden von reCAPTCHA mit Edge Delivery Services für AEM Forms as a Cloud Service

<span>Die **reCAPTCHA**-Funktion befindet sich im Vorabversionsprogramm. Um Zugriff auf die **reCAPTCHA**-Funktion für Edge Delivery Services für AEM Forms anzufordern, senden Sie eine E-Mail von Ihrer Dienstadresse an mailto:aem-forms-ea@adobe.com.</span>

reCAPTCHA ist ein beliebtes Tool zum Schutz von Websites vor betrügerischen Aktivitäten, Spam und Missbrauch. In Edge Delivery Services bietet der adaptive Formularbaustein die Möglichkeit, Google reCAPTCHA hinzuzufügen, um zwischen Menschen und Bots zu unterscheiden. Mit dieser Funktion können Benutzende ihre Website vor Spam und Missbrauch schützen.
Denken Sie beispielsweise an ein Anfrageformular, das Daten wie Start- und Endreisedaten, Zimmerbudget, geschätzte Reisekosten und Reiseinformationen erfasst. In solchen Fällen besteht die Gefahr, dass böswillige Personen das Formular für Zwecke wie den Versand von Phishing-E-Mails oder die Überflutung mit irrelevanten oder schädlichen Inhalten durch Spambots nutzen. Die Integration von reCAPTCHA bietet zusätzliche Sicherheit, indem überprüft wird, ob die Sendungen von echten Personen stammen, wodurch Spam-Einträge effektiv minimiert werden.

<!-- ![Recaptcha Image](/help/edge/docs/forms/assets/recaptcha-image.png){width="300" align="center"} -->

Edge Delivery Services unterstützt nur **punktebasiertes reCAPTCHA (v3)** für den adaptiven Formularbaustein.

![Recaptcha v2](/help/forms/assets/recaptcha-v2-invisible.png){width="300" align="center"}


Am Ende dieses Artikels werden Sie Folgendes gelernt haben:
* [Aktivieren von Google reCAPTCHA für ein einzelnes Formular](#enable-google-recaptchas-for-a-single-form)
* [Aktivieren von reCAPTCHA für alle Formulare auf Ihrer Site](#enable-recaptcha-for-all-the-forms)

## Voraussetzungen

* Beginnen Sie mit der Entwicklung von Edge Delivery Services-Formularen, indem Sie die unter [Erstellen eines Formulars mithilfe des adaptiven Formularbausteins](/help/edge/docs/forms/create-forms.md) erläuterten Schritte befolgen.
* Registrieren Sie Ihre Domain bei [Google reCAPTCHA und beziehen Sie die Anmeldeinformationen](https://www.google.com/recaptcha/admin/create).

## Aktivieren von Google reCAPTCHA für ein einzelnes Formular {#enable-google-recaptchas-for-a-single-form}

Die Aktivierung von Google reCAPTCHA für ein einzelnes Formular beinhaltet die Integration des reCAPTCHA-Diensts von Google in ein bestimmtes Web-Formular, um automatisierten Missbrauch oder Spam-Übermittlungen zu verhindern.

So aktivieren Sie Google reCAPTCHA für ein einzelnes Formular:
1. [Konfigurieren Sie den geheimen reCAPTCHA-Schlüssel in der Projektkonfigurationsdatei](#configure-secret-key)
1. [Fügen Sie den reCAPTCHA-Site-Schlüssel zu Ihrem Formular hinzu](#add-site-key)

Um mit dem Konfigurieren von reCaptcha in Edge Delivery Services-Formularen zu beginnen, sehen Sie sich die folgende [Tabelle](/help/edge/docs/forms/assets/recaptcha.xlsx) an, die die Formulardefinition für ein Formular enthält.

### Konfigurieren Sie den geheimen reCAPTCHA-Schlüssel in der Projektkonfigurationsdatei {#configure-secret-key}

Das Site-Geheimnis für die bei Google reCAPTCHA registrierte Domain wird hinzugefügt, um die Konfigurationsdatei (`.helix/config`) in Ihrem AEM-Projektordner in Microsoft SharePoint oder Google Drive zu projizieren. So fügen Sie das Site-Geheimnis zur Konfigurationsdatei hinzu:

1. Navigieren Sie zu Ihrem AEM-Projektordner auf Microsoft® SharePoint oder zum Google Drive-Ordner.
1. Erstellen Sie die Datei `.helix/config.xlsx` in Ihrem AEM-Projektordner auf der Microsoft SharePoint-Site oder die Datei `.helix/config` im AEM-Projektordner auf Ihrem Google Drive.

   >[!NOTE]
   >
   > Die [Projektkonfigurationsdatei](https://www.aem.live/docs/configuration) ist eine Tabelle, die sich unter `/.helix/config` befindet. Wenn die Datei nicht vorhanden ist, erstellen Sie sie.

1. Öffnen Sie die `config`-Datei und fügen Sie ihr den folgenden Schlüssel und die folgenden Wertpaare hinzu:

   * **captcha.secret**: Wert des geheimen Google-reCAPTCHA-Schlüssels
   * **captcha.type**: reCAPTCHA v2

   >[!NOTE]
   >
   >  * Sie können die reCAPTCHA-Schlüssel aus der [Google reCAPTCHA-Admin-Konsole](https://www.google.com/recaptcha/admin) abrufen.
   >  * Sie müssen den Wert von **captcha.type** in der `config`-Datei als **reCAPTCHA v2** angeben.

   Sehen Sie sich den Screenshot einer Projektkonfigurationsdatei unten an:

   ![Projektkonfigurationsdatei](/help/forms/assets/recaptcha-config-file.png)

1. Speichern Sie die `config`-Datei.

1. Erstellen Sie eine Vorschau und veröffentlichen Sie die `config`-Datei unter Verwendung von [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

### Hinzufügen des reCAPTCHA-Site-Schlüssels zum Formular {#add-site-key}

Der Site-Schlüssel für eine bei Google reCAPTCHA registrierte Domain wird der Tabelle des Formulars hinzugefügt, das geschützt werden soll. So fügen Sie den Site-Schlüssel zu einem Formular hinzu:

1. Wechseln Sie in Microsoft® SharePoint oder Google Drive zu Ihrem AEM-Projektordner und öffnen Sie die Kalkulationstabelle. Sie können auch eine neue Kalkulationstabelle für ein Formular erstellen.
1. Fügen Sie eine Zeile in die Tabelle ein, um ein neues Feld als CAPTCHA hinzuzufügen, wobei Sie die folgenden Details einschließen:
   * **type**: captcha
   * **value**: Wert des Google-reCAPTCHA-Site-Schlüssels

   Im folgenden Screenshot sehen Sie die Tabelle mit dem neuen Zeilentyp CAPTCHA:

   ![Recaptcha-Tabelle](/help/edge/docs/forms/assets/recaptcha-spreadsheet.png)

   >[!NOTE]
   >
   >  Sie können die reCAPTCHA-Schlüssel aus der [Google reCAPTCHA-Admin-Konsole](https://www.google.com/recaptcha/admin) abrufen.

1. Speichern Sie die Tabelle.
1. Verwenden Sie [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content), um das Blatt in der Vorschau anzuzeigen und zu veröffentlichen.

Nach dem Hinzufügen einer neuen Zeile zur Formulardefinition wird in der unteren rechten Ecke des Formulars ein reCAPTCHA-Zeichen angezeigt. Dadurch wird sichergestellt, dass das Formular jetzt vor betrügerischen Aktivitäten, Spam und Missbrauch geschützt ist.

![recaptcha-form](/help/edge/docs/forms/assets/recaptcha-form.png)

## Aktivieren von reCAPTCHA für alle Formulare auf Ihrer Site{#enable-recaptcha-for-all-the-forms}

Um Google reCAPTCHA auf alle Formulare auf Ihrer Site anzuwenden, die den adaptiven Formularbaustein verwenden, überspringen Sie die vorherigen Schritte und betten Sie den `sitekey`-Wert direkt in die Datei `recaptcha.js` ein. So fügen Sie den Wert des Site-Schlüssels in die Datei `recaptcha.js` ein:

1. [Aktualisieren Sie den Google reCAPTCHA-Site-Schlüssel in der Datei „recaptcha.js“](#1-update-google-recaptcha-site-key-in-recaptchajs-file)
1. [Stellen Sie die Datei bereit und erstellen Sie das Projekt](#2-deploy-the-file-and-build-the-project)
1. [Zeigen Sie mit dem AEM-Sidekick eine Vorschau der Site an](#3-preview-the-site-using-the-aem-sidekick)

### Aktualisieren des Google reCAPTCHA-Site-Schlüssels in der Datei „recaptcha.js“

1. Öffnen Sie das entsprechende GitHub-Repository auf Ihrem lokalen Computer.
1. Navigieren Sie zum Ordner `[../Form Block/integrations]` und öffnen Sie die Datei `recaptcha.js`.
1. Ersetzen Sie den `siteKey` durch den Wert des Google reCAPTCHA Site-Schlüssels.

   ![Recaptcha gilt für alle Formulare](/help/forms/assets/recaptcha-apply-to-all-forms.png)

   >[!NOTE]
   >
   >  Sie können die reCAPTCHA-Schlüssel aus der [Google reCAPTCHA-Admin-Konsole](https://www.google.com/recaptcha/admin) abrufen.

1. Speichern Sie die Datei `recaptcha.js`.

### Stellen Sie die Datei bereit und erstellen Sie das Projekt

Stellen Sie die aktualisierte Datei `recaptcha.js` in Ihrem GitHub-Projekt bereit und überprüfen Sie, ob der Build erfolgreich war.

### Zeigen Sie mit dem AEM-Sidekick eine Vorschau der Site an

Verwenden Sie [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content), um die Site in der Vorschau anzuzeigen und zu veröffentlichen.

Das reCAPTCHA-Zeichen wird für alle Formulare auf Ihrer Site angezeigt.

## Siehe auch

{{see-more-forms-eds}}

