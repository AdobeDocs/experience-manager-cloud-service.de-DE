---
title: HTML von E-Mail-Vorlagen in Adaptive Forms auf Forms as a Cloud Service
description: Erfahren Sie, wie Sie E-Mail-Vorlagen mit adaptiven Formularen verwenden.
feature: Adaptive Forms, Core Components
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: ef6f00203241c12fce08cf81495b36f47e64613e
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 4%

---

# E-Mail-Vorlagen in Adaptive Forms

Adaptive Forms ermöglicht die Verwendung von HTML- und E-Mail-Vorlagen im Klartext. HTML-E-Mail-Vorlagen ermöglichen es Ihnen, beim Senden eines Formulars ansprechende, personalisierte und visuell ansprechende E-Mails zu senden. Diese E-Mails können mit Formulardaten angepasst und mit verschiedenen E-Mail-Tags, wie Bildern und Links, erweitert werden. Bei Adaptive Forms können Sie entweder eine Datei hochladen, die eine HTML-Vorlage enthält, oder einen Texteditor verwenden, um diese Vorlagen zu erstellen.

![HTML-E-Mail-Vorlagen](/help/forms/assets/html-email.png)

Dieser Artikel hilft Ihnen bei der Konfiguration und Verwendung von E-Mail-Vorlagen in adaptiven Forms. Am Ende werden Sie in der Lage sein,

* [Konfigurieren einer HTML-Vorlage für ein adaptives Formular](#configure-an-html-template-for-an-adaptive-form)
* [Konfigurieren einer Nur-Text-E-Mail-Vorlage für ein adaptives Formular](#configure-a-plain-text-template-for-an-adaptive-form)
* [Verwenden von Formulardaten in Ihren E-Mail-Vorlagen](#use-form-data-in-your-email-templates)


Im Folgenden finden Sie einen kurzen Überblick über die erforderlichen Schritte:

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Konfigurieren der Übermittlungsaktion [E](/help/forms/configure-submit-action-send-email.md)Mail senden“.
1. Wählen Sie eine HTML-Vorlage aus oder laden Sie sie hoch oder geben Sie die E-Mail-Vorlage manuell ein.
1. Testen Sie Ihre E-Mail-Konfiguration.

## Konfigurieren einer HTML-Vorlage für ein adaptives Formular

Sie können ein adaptives Formular so einrichten, dass eine E-Mail nach dem Senden gesendet wird, indem Sie die Übermittlungsaktion [**E-Mail**) ](/help/forms/configure-submit-action-send-email.md). Die Aktion bietet zwei Methoden zum Konfigurieren einer HTML-Vorlage:

### Option 1: Eine Datei mit der HTML-Vorlage auswählen

Bevor Sie fortfahren, stellen Sie sicher, dass Sie die HTML-Vorlage in Ihre AEM Forms-Umgebung hochgeladen haben.

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Wechseln Sie zum **Inhaltsbrowser**, wählen Sie den **Guide-Container** und tippen Sie auf das Symbol Eigenschaften . Ein Dialogfeld mit dem Titel &quot;`Adaptive Form Container`&quot; wird angezeigt.
1. Wechseln Sie zur Registerkarte **Übermittlung** und wählen Sie die Übermittlungsaktion **E-Mail senden** aus.
1. Aktivieren Sie die Option **Externe Vorlage verwenden**.
1. Aktivieren Sie die **HTML-Vorlage verwenden**.
1. Klicken Sie auf das Ordnersymbol für die Option Pfad für externe Vorlage und wählen Sie Ihre HTML-Vorlage aus.
1. Klicken Sie auf Fertig , um die Konfiguration zu speichern.

Ihre HTML-Vorlage ist jetzt für das adaptive Formular konfiguriert.

### Option 2: Manuelles Eingeben oder Einfügen einer HTML-Vorlage

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Wechseln Sie zum **Inhaltsbrowser**, wählen Sie den **Guide-Container** und tippen Sie auf das Symbol Eigenschaften . Ein Dialogfeld mit dem Titel &quot;`Adaptive Form Container`&quot; wird angezeigt.
1. Wechseln Sie zur Registerkarte **Übermittlung** und wählen Sie die Übermittlungsaktion **E-Mail senden** aus.
1. Aktivieren Sie die Option **Externe Vorlage verwenden**.
1. Aktivieren Sie die **HTML-Vorlage verwenden**.
1. Geben Sie Ihren HTML-Code direkt in das bereitgestellte Feld **E-Mail-Vorlage** ein.


## Konfigurieren einer Nur-Text-Vorlage für ein adaptives Formular

Sie können ein adaptives Formular so einrichten, dass eine E-Mail nach dem Senden gesendet wird, indem Sie die Übermittlungsaktion [**E-Mail**) ](/help/forms/configure-submit-action-send-email.md). Die Aktion bietet zwei Methoden zum Konfigurieren einer Nur-Text-Vorlage:

### Option 1: Wählen Sie eine Datei aus, die die Vorlage enthält

Bevor Sie fortfahren, stellen Sie sicher, dass Sie die HTML-Vorlage in Ihre AEM Forms-Umgebung hochgeladen haben.

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Wechseln Sie zum **Inhaltsbrowser**, wählen Sie den **Guide-Container** und tippen Sie auf das Symbol Eigenschaften . Ein Dialogfeld mit dem Titel &quot;`Adaptive Form Container`&quot; wird angezeigt.
1. Wechseln Sie zur Registerkarte **Übermittlung** und wählen Sie die Übermittlungsaktion **E-Mail senden** aus.
1. Aktivieren Sie die Option **Externe Vorlage verwenden**.
1. Klicken Sie auf das Ordnersymbol für die Option **Pfad für externe Vorlage** und wählen Sie Ihre Nur-Text-Vorlage aus.
1. Klicken Sie auf Fertig , um die Konfiguration zu speichern.

Ihre Vorlage ist jetzt für das adaptive Formular konfiguriert.

### Option 2: Manuelles Eingeben oder Einfügen einer HTML-Vorlage

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Wechseln Sie zum **Inhaltsbrowser**, wählen Sie den **Guide-Container** und tippen Sie auf das Symbol Eigenschaften . Ein Dialogfeld mit dem Titel &quot;`Adaptive Form Container`&quot; wird angezeigt.
1. Wechseln Sie zur Registerkarte **Übermittlung** und wählen Sie die Übermittlungsaktion **E-Mail senden** aus.
1. Geben Sie den Code Ihrer Textvorlage direkt in das bereitgestellte Feld **E-Mail-Vorlage** ein oder fügen Sie ihn ein.

## Verwenden von Formulardaten in E-Mail-Vorlagen

Sie können Formulardaten mithilfe von Platzhaltern in Ihre E-Mail-Vorlagen einfügen. Diese Platzhalter werden beim Senden der E-Mail dynamisch durch die tatsächlichen Formularfeldwerte ersetzt. Zum Beispiel:

* ${name}: Der Wert des Felds mit dem Namen „name“.
* ${email}: Der Wert des Felds mit dem Namen „email“.
* ${message}: Der Wert des Felds mit dem Namen „message“.

### Beispiel einer HTML-E-Mail-Vorlage

Im Folgenden finden Sie ein Beispiel für eine HTML-E-Mail-Vorlage, die Platzhalter für Formulardaten verwendet:

```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <title>Form Submission</title>
        <style>
            body {
                font-family: Arial, sans-serif;
                line-height: 1.6;
                color: #333;
            }
            h2 {
                color: #0056b3;
            }
        </style>
    </head>
    <body>
        <h2>Thank You for Your Submission</h2>
        <p>Dear ${name},</p>
        <p>We have received your submission with the following details:</p>
        <ul>
            <li><strong>Email:</strong> ${email}</li>
            <li><strong>Phone Number:</strong> ${phone_number}</li>
            <li><strong>Message:</strong> ${message}</li>
        </ul>
        <p>We will get back to you soon!</p>
        <p>Best regards,</p>
        <p>Your Team</p>
    </body>
    </html>
```

### Beispielvorlage für Nur-Text-E-Mails

Im Folgenden finden Sie ein Beispiel für eine Nur-Text-E-Mail-Vorlage:

```TXT
    
    Subject: Thank You for Your Submission
    
    Dear ${name},
    
    We have received your submission with the following details:
    
    - Email: ${email}
    - Phone Number: ${phone_number}
    - Message: ${message}
    
    We will get back to you soon!
    
    Best regards,
    Your Team
```

Ersetzen Sie die Platzhalter (${name}, ${email} usw.) durch die entsprechenden Formularfeldnamen in Ihrem adaptiven Formular.

## Best Practices für das HTML von E-Mail-Vorlagen

* Stellen Sie sicher, dass Ihre Stile inline sind, um eine bessere Kompatibilität mit E-Mail-Clients zu gewährleisten.
* Gestalten Sie Ihre Vorlage responsiv, um ein besseres Erlebnis auf Mobilgeräten zu erzielen.
* Verwenden Sie Tools wie Litmus oder Email on Acid, um eine Vorschau Ihrer E-Mail über verschiedene E-Mail-Clients hinweg anzuzeigen.
* Stellen Sie sicher, dass die Platzhalternamen genau mit den Formularfeldnamen übereinstimmen.
* Prüfen Sie Ihre HTML-Vorlage auf fehlende oder falsche Tags.
* Überprüfen Sie, ob [ Übermittlungsaktion ](/help/forms/configure-submit-action-send-email.md)E-Mail senden“ korrekt konfiguriert ist.
