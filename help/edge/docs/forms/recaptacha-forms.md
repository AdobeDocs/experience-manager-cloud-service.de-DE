---
title: Verwenden von reCAPTCHA mit Edge Delivery Services für AEM Forms as a Cloud Service
description: Verwenden von Google reCAPTCHA in einem EDS-Formular
feature: Edge Delivery Services
exl-id: ac104e23-f175-435f-8414-19847efa5825
role: Admin, Architect, Developer
source-git-commit: fe45123b3aefddaf02bc8584283941db168ba174
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 25%

---


# Verwenden von reCAPTCHA mit Edge Delivery Services für AEM Forms as a Cloud Service

<span>Die Funktion **reCAPTCHA** befindet sich im Vorabversionsprogramm. Um den Zugriff auf die Funktion **reCAPTCHA** für AEM Forms-Edge Delivery Services anzufordern, senden Sie eine E-Mail von Ihrer Arbeitsadresse an mailto:aem-forms-ea@adobe.com</span>.

reCAPTCHA ist ein beliebtes Tool zum Schutz von Websites vor betrügerischen Aktivitäten, Spam und Missbrauch. In Edge Delivery Services bietet der adaptive Formularbaustein die Möglichkeit, Google reCAPTCHA hinzuzufügen, um zwischen Menschen und Bots zu unterscheiden. Mit dieser Funktion können Benutzende ihre Website vor Spam und Missbrauch schützen.
Denken Sie beispielsweise an ein Anfrageformular, das Daten wie Start- und Endreisedaten, Zimmerbudget, geschätzte Reisekosten und Reiseinformationen erfasst. In solchen Fällen besteht die Gefahr, dass böswillige Personen das Formular für Zwecke wie den Versand von Phishing-E-Mails oder die Überflutung mit irrelevanten oder schädlichen Inhalten durch Spambots nutzen. Die Integration von reCAPTCHA bietet zusätzliche Sicherheit, indem überprüft wird, ob die Sendungen von echten Personen stammen, wodurch Spam-Einträge effektiv minimiert werden.

<!-- ![Recaptcha Image](/help/edge/docs/forms/assets/recaptcha-image.png){width="300" align="center"} -->

Edge Delivery Services unterstützt nur den **Score based(v3)-reCAPTCHA** für den adaptiven Formularblock.

![Recaptcha V2](/help/forms/assets/recaptcha-v2-invisible.png){width="300" align="center"}


Am Ende dieses Artikels werden Sie Folgendes gelernt haben:
* [Aktivieren von Google reCAPTCHA für ein einzelnes Formular](#enable-google-recaptchas-for-a-single-form)
* [Aktivieren Sie reCAPTCHA für alle Formulare auf Ihrer Site](#enable-recaptcha-for-all-the-forms)

## Voraussetzungen

* Beginnen Sie mit der Entwicklung von Edge Delivery Services Forms, indem Sie die unter [Erstellen eines Formulars mithilfe des adaptiven Forms-Blocks](/help/edge/docs/forms/create-forms.md) erläuterten Schritte befolgen.
* Registrieren Sie Ihre Domäne bei [Google reCAPTCHA und erhalten Sie Anmeldeinformationen](https://www.google.com/recaptcha/admin/create).

## Aktivieren von Google reCAPTCHA für ein einzelnes Formular {#enable-google-recaptchas-for-a-single-form}

Die Aktivierung von Google reCAPTCHA für ein einzelnes Formular beinhaltet die Integration des reCAPTCHA-Diensts von Google in ein bestimmtes Webformular, um automatisierten Missbrauch oder Spam-Versand zu verhindern.

So aktivieren Sie Google reCAPTCHA für ein einzelnes Formular:
1. [Konfigurieren Sie den geheimen Schlüssel reCAPTCHA in der Projektkonfigurationsdatei](#configure-secret-key)
1. [Den Site-Schlüssel reCAPTCHA zu Ihrem Formular hinzufügen](#add-site-key)

Informationen zum Konfigurieren von reCaptcha in Edge Delivery Services Forms finden Sie im folgenden [Arbeitsblatt](/help/edge/docs/forms/assets/recaptcha.xlsx), das die Formulardefinition für ein Formular enthält.

### Konfigurieren Sie den geheimen Schlüssel reCAPTCHA in der Projektkonfigurationsdatei {#configure-secret-key}

Das Site-Geheimnis für die bei Google reCAPTCHA registrierte Domäne wird hinzugefügt, um die Konfigurationsdatei (`.helix/config`) in Ihrem AEM Projektordner in Microsoft SharePoint oder Google Drive zu projektieren. Hinzufügen des Site-Geheimnisses zur Konfigurationsdatei:

1. Wechseln Sie auf dem Microsoft® SharePoint- oder Google-Laufwerk zu Ihrem AEM Projektordner.
1. Erstellen Sie die Datei &quot;`.helix/config.xlsx`&quot;in Ihrem AEM-Projektordner auf der Microsoft SharePoint-Site oder die Datei &quot;`.helix/config`&quot;in AEM Projektordner auf Ihrem Google-Laufwerk.

   >[!NOTE]
   >
   > Die [Projektkonfigurationsdatei](https://www.aem.live/docs/configuration) ist eine Tabelle unter `/.helix/config`. Wenn die Datei nicht vorhanden ist, erstellen Sie sie.

1. Öffnen Sie die Datei `config` und fügen Sie die folgenden Schlüssel-Wert-Paare hinzu:

   * **captcha.secret**: geheimer Google-Schlüsselwert reCAPTCHA
   * **captcha.type**: reCAPTCHA v2

   >[!NOTE]
   >
   >  * Sie können die reCAPTCHA-Schlüssel aus der [Google reCAPTCHA-Admin Console](https://www.google.com/recaptcha/admin) abrufen.
   >  * Sie müssen den Wert von **captcha.type** in der Datei `config` als **reCAPTCHA v2** angeben.

   Siehe Screenshot einer Projektkonfigurationsdatei unten:

   ![Projektkonfigurationsdatei](/help/forms/assets/recaptcha-config-file.png)

1. Speichern Sie die Datei `config`.

1. Zeigen Sie die `config` -Datei in der Vorschau an und veröffentlichen Sie sie mit [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

### Hinzufügen des reCAPTCHA-Site-Schlüssels zum Formular {#add-site-key}

Der Site-Schlüssel für eine bei Google reCAPTCHA registrierte Domäne wird dem Arbeitsblatt des Formulars hinzugefügt, das geschützt werden soll. So fügen Sie den Site-Schlüssel zu einem Formular hinzu:

1. Wechseln Sie in Microsoft® SharePoint oder Google Drive zu Ihrem AEM-Projektordner und öffnen Sie die Kalkulationstabelle. Sie können auch eine neue Kalkulationstabelle für ein Formular erstellen.
1. Fügen Sie eine Zeile in das Arbeitsblatt ein, um ein neues Feld als CAPTCHA hinzuzufügen, einschließlich der folgenden Details:
   * **type**: captcha
   * **value**: Google reCAPTCHA-Site-Schlüsselwert

   Im folgenden Screenshot sehen Sie die Tabelle mit dem neuen Zeilentyp CAPTCHA:

   ![Reaptcha-Tabelle](/help/edge/docs/forms/assets/recaptcha-spreadsheet.png)

   >[!NOTE]
   >
   >  Sie können die reCAPTCHA-Schlüssel aus der [Google reCAPTCHA-Admin Console](https://www.google.com/recaptcha/admin) abrufen.

1. Speichern Sie die Tabelle.
1. Verwenden Sie [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content), um das Blatt in der Vorschau anzuzeigen und zu veröffentlichen.

Nachdem Sie der Formulardefinition eine neue Zeile hinzugefügt haben, wird unten rechts im Formular ein reCAPTCHA-Zeichen angezeigt. Dadurch wird sichergestellt, dass das Formular jetzt vor betrügerischen Aktivitäten, Spam und Missbrauch geschützt ist.

![recaptcha-form](/help/edge/docs/forms/assets/recaptcha-form.png)

## Aktivieren Sie reCAPTCHA für alle Formulare auf Ihrer Site{#enable-recaptcha-for-all-the-forms}

Um Google reCAPTCHA auf alle Formulare auf Ihrer Site anzuwenden, die den adaptiven Forms-Block verwenden, überspringen Sie die vorherigen Schritte und betten Sie den `sitekey`-Wert direkt in die Datei `recaptcha.js` ein. So fügen Sie den Site-Schlüsselwert in die Datei `recaptcha.js` ein:

1. [Aktualisieren des Google reCAPTCHA-Site-Schlüssels in der Datei &quot;recaptcha.js&quot;](#1-update-google-recaptcha-site-key-in-recaptchajs-file)
1. [Bereitstellen der Datei und Erstellen des Projekts](#2-deploy-the-file-and-build-the-project)
1. [Vorschau der Site mit dem AEM Sidekick](#3-preview-the-site-using-the-aem-sidekick)

### Aktualisieren des Google reCAPTCHA-Site-Schlüssels in der Datei &quot;recaptcha.js&quot;

1. Öffnen Sie das entsprechende GitHub-Repository auf Ihrem lokalen Computer.
1. Navigieren Sie zum Ordner `[../Form Block/integrations]` und öffnen Sie die Datei `recaptcha.js` .
1. Ersetzen Sie den Wert `siteKey` durch den Google reCAPTCHA Site-Schlüsselwert.

   ![Recaptcha gilt für alle Formulare](/help/forms/assets/recaptcha-apply-to-all-forms.png)

   >[!NOTE]
   >
   >  Sie können die reCAPTCHA-Schlüssel aus der [Google reCAPTCHA-Admin Console](https://www.google.com/recaptcha/admin) abrufen.

1. Speichern Sie die Datei `recaptcha.js`.

### Bereitstellen der Datei und Erstellen des Projekts

Stellen Sie die aktualisierte `recaptcha.js` -Datei in Ihrem GitHub-Projekt bereit und überprüfen Sie, ob der Build erfolgreich war.

### Vorschau der Site mit dem AEM Sidekick

Verwenden Sie [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content), um die Site in der Vorschau anzuzeigen und zu veröffentlichen.

Das reCAPTCHA-Zeichen wird für alle Formulare auf Ihrer Site angezeigt.

## Siehe auch

{{see-more-forms-eds}}

