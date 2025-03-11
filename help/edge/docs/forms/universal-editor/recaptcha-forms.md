---
title: Schützen von Forms mit reCAPTCHA - Eine visuelle Anleitung
description: Erfahren Sie, wie Sie Ihren Edge Delivery Services-Formularen einfach Google reCAPTCHA hinzufügen können, um Spam- und Bot-Übermittlungen zu verhindern
feature: Edge Delivery Services
keywords: reCAPTCHA in Formularen, Verwendung von reCAPTCHA im universellen Editor, Hinzufügen von reCAPTCHA in Formularen, Formularsicherheit, Spam-Schutz
role: Developer
exl-id: 1f28bd13-133f-487e-8b01-334be7c08a3f
source-git-commit: babddee34b486960536ce7075684bbe660b6e120
workflow-type: tm+mt
source-wordcount: '1085'
ht-degree: 3%

---


# Schützen Ihres Forms vor Spam mit Google reCAPTCHA

<span class="preview"> Diese Funktion ist über das Early-Access-Programm verfügbar. Um den Zugriff anzufordern, senden Sie eine E-Mail von Ihrer offiziellen Adresse an <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a> mit dem Namen Ihrer GitHub-Organisation und dem Repository-Namen.</span>



## Warum sollten Sie reCAPTCHA in Ihren Formularen verwenden?

| ![Sicherheit](/help/edge/docs/forms/universal-editor/assets/security.svg) | ![Bot-Schutz](/help/edge/docs/forms/universal-editor/assets/bot-protection.svg) | ![Anwendererlebnis](/help/edge/docs/forms/universal-editor/assets/user-experience.svg) |
|:-------------:|:-------------:|:-------------:|
| **Erweiterte Sicherheit** | **Bot- und Spam-Schutz** | **Nahtloses Benutzererlebnis** |
| Schützen Sie Ihre Formulare vor betrügerischen Aktivitäten und böswilligen Angriffen | Verhindern Sie, dass automatisierte Bots Ihre Formulare mit irrelevanten oder schädlichen Inhalten überfluten | Das unsichtbare reCAPTCHA funktioniert hinter den Kulissen, ohne rechtmäßige Benutzer zu stören |

Beispielsweise muss ein Steuerberechnungsformular mit sensiblen Finanzinformationen vor Missbrauch geschützt werden. reCAPTCHA stellt sicher, dass die Einsendungen von echten Benutzern und nicht von automatisierten Systemen stammen.

## Wählen Sie Ihre reCAPTCHA-Lösung

Edge Delivery Services Forms unterstützt zwei Google reCAPTCHA-Optionen:

| ![ReCaptcha Enterprise](/help/edge/docs/forms/universal-editor/assets/enterprise.svg) | ![reCAPTCHA-Standard](/help/edge/docs/forms/universal-editor/assets/standard.svg) |
|:-------------:|:-------------:|
| [**ReCaptcha Enterprise**](#set-up-recaptcha-enterprise) | [**reCAPTCHA-Standard**](#set-up-recaptcha-standard) |
| Erstklassige Betrugserkennung im Unternehmensmaßstab mit zusätzlichen Funktionen und Anpassungen | Kostenloser Service mit Score-basierter Erkennung, der im Hintergrund unsichtbar funktioniert |
| Optimiert für: Große Unternehmen mit komplexen Sicherheitsanforderungen | Optimal geeignet für: Kleine bis mittlere Projekte mit grundlegenden Schutzanforderungen |

Bei beiden Optionen wird die Score-basierte Erkennung (0,0 bis 1,0) verwendet, um Interaktionen zwischen Mensch und Bot zu identifizieren, ohne das Benutzererlebnis zu stören.

## Einrichten von reCAPTCHA Enterprise

### Schritt 1: Google Cloud-Anmeldedaten abrufen

Bevor Sie reCAPTCHA Enterprise konfigurieren, benötigen Sie Folgendes:

- Ein [Google Cloud-Projekt](https://cloud.google.com/recaptcha/docs/prepare-environment#before-you-begin) mit Ihrer [Projekt-ID](https://support.google.com/googleapi/answer/7014113)
- [reCAPTCHA Enterprise API aktiviert](https://cloud.google.com/recaptcha/docs/prepare-environment#enable-api) für Ihr Projekt
- Ein [API-Schlüssel](https://console.cloud.google.com/apis/credentials) für die Authentifizierung
- Ein [Site-Schlüssel](https://console.cloud.google.com/security/recaptcha) für Ihre Domain

### Schritt 2: Erstellen eines Cloud-Konfigurations-Containers

![Schrittweise Einrichtung der Cloud-Konfiguration](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an
2. Navigieren Sie zu **Tools** > **Allgemein** > **Konfigurations-Browser**
3. Suchen Sie Ihr Formular und wählen Sie **Eigenschaften**
4. Aktivieren **Cloud-Konfigurationen** im Dialogfeld
5. Speichern und Veröffentlichen der Konfiguration

### Schritt 3: Konfigurieren des reCAPTCHA Enterprise-Service

![reCAPTCHA Enterprise-Konfigurationsbildschirm](/help/edge/docs/forms/universal-editor/assets/recaptcha-enterprise.png)

1. Navigieren Sie **Tools** > **Cloud Services** > **reCAPTCHA**
2. Navigieren Sie zu Ihrem Formular und klicken Sie auf **Erstellen**
3. Im Dialogfeld:
   - Wählen Sie **reCAPTCHA Enterprise**-Version aus
   - Titel und Namen eingeben
   - Fügen Sie Ihre Projekt-ID, Ihren Site- und API-Schlüssel hinzu
   - Wählen Sie **Bewertungsbasierter Site-Schlüssel** als Schlüsseltyp aus.
   - Setzen Sie einen Schwellenwert (0-1), um Menschen von Bots zu unterscheiden
4. Klicken Sie **Erstellen** und veröffentlichen Sie Ihre Konfiguration

## Einrichten von reCAPTCHA Standard

### Schritt 1: API-Schlüssel abrufen

Bevor Sie beginnen[ rufen Sie über die Google-reCAPTCHA-Konsole ](https://www.google.com/recaptcha/admin)ein reCAPTCHA-API-Schlüsselpaar) (Site- und Geheimschlüssel) ab.

>[!IMPORTANT]
>
>Edge Delivery Services Forms unterstützt nur die **reCAPTCHA-punktzahlbasierte** Version.

### Schritt 2: Erstellen eines Cloud-Konfigurations-Containers

Führen Sie dieselben Schritte wie in der Enterprise-Version aus, um einen Cloud-Konfigurations-Container zu erstellen und zu veröffentlichen.

### Schritt 3: Konfigurieren des reCAPTCHA-Standarddienstes

![reCAPTCHA-Standardkonfigurationsbildschirm](/help/edge/docs/forms/universal-editor/assets/recaptcha.png)

1. Navigieren Sie **Tools** > **Cloud Services** > **reCAPTCHA**
2. Navigieren Sie zu Ihrem Formular und klicken Sie auf **Erstellen**
3. Im Dialogfeld:
   - Auswählen **ReCAPTCHA v2**-Version
   - Titel und Namen eingeben
   - Hinzufügen von Site- und Geheimschlüssel
4. Klicken Sie **Erstellen** und veröffentlichen Sie Ihre Konfiguration

## Hinzufügen von reCAPTCHA zu einem Formular

Nachdem Sie reCAPTCHA konfiguriert haben, können Sie es jetzt dem Formular hinzufügen:

![Hinzufügen der reCAPTCHA-Komponente zu einem Formular](/help/edge/docs/forms/universal-editor/assets/add-recaptcha-component.png)

1. Öffnen Sie das Formular im universellen Editor
2. Navigieren Sie in der Inhaltsstruktur zum Abschnitt „Adaptives Formular“
3. Klicken Sie auf **Hinzufügen** und wählen Sie **CAPTCHA (unsichtbar)** aus der Liste Adaptive Formularkomponenten aus
   - *Alternativ können Sie die Komponente per Drag-and-Drop in das Formular ziehen*
4. Klicken Sie auf **Veröffentlichen**, um Ihr Formular mit dem reCAPTCHA-Schutz zu aktualisieren

Ihr Formular ist jetzt geschützt! Anzeigen unter:
`https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form-name>`

![Formular mit aktiviertem reCAPTCHA-Schutz](/help/edge/docs/forms/universal-editor/assets/form-with-recaptcha.png)

## Validieren der reCAPTCHA-Integration

Nachdem Sie reCAPTCHA zu Ihrem Formular hinzugefügt haben, müssen Sie sicherstellen, dass es ordnungsgemäß funktioniert. So validieren Sie Ihre Implementierung:

### Visuelle Überprüfung

Während reCAPTCHA v2 (Score-basiert) unsichtbar funktioniert, können Sie sein Vorhandensein durch Folgendes bestätigen:

1. **Überprüfen der Seitenquelle**: Klicken Sie mit der rechten Maustaste auf die Formularseite und wählen Sie &quot;Source anzeigen“.
   - Suchen Sie nach der Aufnahme des reCAPTCHA-Skripts mit Ihrem Site-Schlüssel
   - Beispiel: `<script src="https://www.google.com/recaptcha/api.js?render=YOUR_SITE_KEY"></script>`

2. **Prüfen von Netzwerkanfragen**: Verwenden von Browser-Entwickler-Tools (F12)
   - Senden Sie Ihr Formular und suchen Sie nach Netzwerkanfragen an `google.com/recaptcha`
   - Diese Anfragen zeigen an, dass reCAPTCHA in Ihrem Formular aktiv ist

### Funktionsprüfung

So überprüfen Sie, ob reCAPTCHA Ihr Formular tatsächlich schützt:

1. **Normale Übermittlungsprüfung**:
   - Füllen Sie Ihr Formular mit gültigen Daten aus
   - Formular in normalem Tempo an einen Benutzer senden
   - Überprüfen, ob das Formular erfolgreich gesendet wurde

2. **Bot-like Behavior Test**:
   - Öffnen Sie das Formular in einem inkognito-/privaten Browserfenster
   - Füllen Sie das Formular extrem schnell aus (automatisiertes Verhalten)
   - Mehrfaches Senden in schneller Folge
   - Wenn reCAPTCHA funktioniert, werden diese Übermittlungen möglicherweise blockiert oder markiert

3. **Überprüfen Sie die Datensätze für die Formularübermittlung**:
   - Überprüfen der Formularübermittlungsdaten
   - Jede Übermittlung sollte einen reCAPTCHA-Wert enthalten
   - Werte nahe bei 1,0 deuten auf mögliche menschliche Nutzer hin
   - Werte nahe 0,0 weisen auf eine potenzielle Bot-Aktivität hin

### Verwenden der Google reCAPTCHA Admin Console

Für Enterprise-Anwender bietet die Google Cloud Console detaillierte Analysen:

1. Wechseln Sie zur [Google Cloud-Konsole](https://console.cloud.google.com/)
2. Navigieren Sie zu **Sicherheit** > **reCAPTCHA**
3. Site-Schlüssel auswählen
4. Überprüfen der Bewertungsdiagramme und Statistiken
5. Suchen Sie nach:
   - Traffic-Muster
   - Score-Verteilungen
   - Potenziell betrügerische Aktivitäten

Für Standard-reCAPTCHA-Benutzende sind grundlegende Statistiken in der [reCAPTCHA-Admin Console](https://www.google.com/recaptcha/admin/) verfügbar.

### Anpassen der Implementierung

Basierend auf Ihren Validierungsergebnissen:

- Wenn rechtmäßige Benutzer blockiert werden, sollten Sie den Schwellenwert senken
- Wenn Sie immer noch Spam erhalten, sollten Sie den Schwellenwert erhöhen
- Überprüfen Sie bei anhaltenden Problemen Ihre reCAPTCHA-Konfiguration und stellen Sie sicher, dass alle Schlüssel korrekt eingegeben wurden

Denken Sie daran, dass reCAPTCHA maschinelles Lernen verwendet, um im Laufe der Zeit zu verbessern, sodass seine Effektivität steigen kann, wenn es die Traffic-Muster Ihrer Site erlernt.

## Fehlerbehebung und häufig gestellte Fragen

| ![Frage](/help/edge/docs/forms/universal-editor/assets/question.svg) | ![Antwort](/help/edge/docs/forms/universal-editor/assets/answer.svg) |
|:-------------:|:-------------:|
| **Was passiert, wenn ich keine reCAPTCHA-Konfiguration erstelle?** | Das System sucht im globalen Container nach einer Konfiguration. Wenn keines vorhanden ist, wird ein Fehler angezeigt. |
| **Was passiert, wenn ich mehrere Konfigurationen erstelle?** | Das System verwendet automatisch die zuerst erstellte Konfiguration. |
| **Warum sind meine Änderungen nicht in der veröffentlichten URL sichtbar?** | Veröffentlichen Sie das Formular erneut, nachdem Sie Änderungen vorgenommen haben. |
| **Welche reCAPTCHA-Services werden unterstützt?** | Edge Delivery Services Forms unterstützt nur Score-basierte reCAPTCHA-Services. |

## Nächste Schritte

Nachdem Sie Ihr Formular mit reCAPTCHA geschützt haben:

- **Implementierung validieren**: Befolgen Sie die [Validierungsschritte](#-validating-your-recaptcha-integration) um sicherzustellen, dass reCAPTCHA ordnungsgemäß funktioniert
- **Leistung überwachen**: Überprüfen Sie Ihr Google reCAPTCHA-Dashboard regelmäßig auf verdächtige Aktivitäten und Score-Verteilungen
- **Einstellungen anpassen**: Passen Sie Ihren Schwellenwert an Ihre Sicherheitsanforderungen und Ihr Benutzererlebnis-Feedback an
- **Auf dem Laufenden**: Halten Sie Ihre reCAPTCHA-Implementierung mit den neuesten Sicherheitsempfehlungen von Google auf dem neuesten Stand
- **Team schulen**: Wissen über die Funktionsweise von reCAPTCHA und die Interpretation der Analysen austauschen
- **Feedback einholen**: Überwachen des Benutzererlebnisses, um sicherzustellen, dass rechtmäßige Benutzer nicht blockiert werden

Denken Sie daran, dass der effektive Formularschutz ein fortlaufender Prozess ist, der regelmäßige Überwachung und Anpassungen erfordert.


