---
title: Hinzufügen von Google reCAPTCHA zu Formularen im universellen Editor
description: Handbuch zur Implementierung von Google reCAPTCHA-Schutz in Edge Delivery Services-Formularen zur Verhinderung von Spam und automatischen Angriffen
feature: Edge Delivery Services
keywords: reCAPTCHA in Formularen, Verwenden von reCAPTCHA im universellen Editor, Hinzufügen von reCAPTCHA in Formularen, Formularsicherheit, Spam-Schutz
role: Developer, Admin
level: Intermediate
exl-id: 1f28bd13-133f-487e-8b01-334be7c08a3f
source-git-commit: fd3c53cf5a6d1c097a5ea114a831ff626ae7ad7e
workflow-type: tm+mt
source-wordcount: '1281'
ht-degree: 90%

---


# Hinzufügen von Google reCAPTCHA zu Formularen im universellen Editor

Google reCAPTCHA hilft beim Schutz von Formularen, indem es zwischen menschlichen Benutzenden und automatisierten Bots unterscheidet. In diesem Handbuch wird erläutert, wie Sie im universellen Editor sowohl Enterprise- als auch Standard-Versionen von reCAPTCHA implementieren können.

**Ziele:**

- Auswählen der passenden reCAPTCHA-Lösung
- Konfigurieren von reCAPTCHA Enterprise oder Standard
- Hinzufügen von reCAPTCHA zu Ihren Formularen
- Validieren und Testen der Implementierung
- Überwachen und Optimieren der Leistung

## Voraussetzungen

Bevor Sie beginnen, sollten Sie folgende Anforderungen erfüllen:

### Zugriffsanforderungen

- Authoring-Zugriff auf AEM as a Cloud Service
- Zugriff auf den universellen Editor mit Berechtigungen zur Formularbearbeitung

### Technische Anforderungen

- Aktives Google-Konto
- Bei Enterprise: Google Cloud Platform-Projekt mit aktivierter Abrechnung
- Bei Standard: Google reCAPTCHA-Konto
- Inhaberschaft der Domain für Ihre Formulare verifiziert

### Erforderliche Kenntnisse

- Grundlegendes Verständnis von AEM Forms und dem universellen Editor
- Vertrautheit mit Cloud-Service-Konfigurationen
- Verständnis der Konzepte zur Formularsicherheit

## Was für reCAPTCHA in Formularen spricht

| ![Sicherheit](/help/edge/docs/forms/universal-editor/assets/security.svg) | ![Bot-Schutz](/help/edge/docs/forms/universal-editor/assets/bot-protection.svg) | ![Anwendererlebnis](/help/edge/docs/forms/universal-editor/assets/user-experience.svg) |
|:-------------:|:-------------:|:-------------:|
| **Erweiterte Sicherheit** | **Bot- und Spam-Abwehr** | **Nahtloses Anwendererlebnis** |
| Schützt Formulare vor betrügerischen Aktivitäten und Angriffen | Verhindert, dass automatisierte Bots Formulare übermitteln | Unsichtbares reCAPTCHA stört keine legitimen Benutzenden |

**Schlüsselkonzept:** reCAPTCHA nutzt maschinelles Lernen, um das Benutzerverhalten zu analysieren, und weist einen Wert (von 0,0 bis 1,0) zu, um die Wahrscheinlichkeit einer menschlichen Interaktion anzugeben. Höhere Werte stehen für menschliche Benutzende, niedrigere Werte deuten auf Bots hin.

**Beispiel** Ein Steuerberechnungsformular, das sensible Daten verarbeitet, muss vor automatischen Angriffen geschützt werden. reCAPTCHA prüft, ob die Übermittlungen von echten Benutzenden und nicht von Bots stammen.

## Wählen Ihrer reCAPTCHA-Lösung

Edge Delivery Services-Formulare unterstützen zwei Google reCAPTCHA-Optionen. Verwenden Sie die folgenden Kriterien, um die richtige Lösung auszuwählen:

### Leitfaden für schnelle Entscheidungen

**Verwenden Sie reCAPTCHA Enterprise, wenn Sie Folgendes haben:**

- Formulare mit hohem Traffic (>10.000 Anfragen/Monat)
- Hohe Compliance-Anforderungen (DSGVO, SOX, HIPAA)
- Bedarf an erweiterten Analysen und Berichten
- Budget für Premium-Sicherheitsfunktionen
- Komplexe Multi-Domain-Bereitstellungen

**Verwenden Sie reCAPTCHA Standard, wenn Sie Folgendes haben:**

- Geringer bis moderater Traffic (&lt; 10.000 Anfragen/Monat)
- Grundlegende Sicherheitsanforderungen
- Eingeschränktes Budget (kostenlose Version)
- Einfache Einrichtung einer Domain
- Neuling bei reCAPTCHA

### Detailvergleich

| **Funktion** | **ReCaptcha Enterprise** | **reCAPTCHA Standard** |
|-------------|--------------------------|------------------------|
| **Kosten** | Kostenpflichtig (nutzungsbasierte Preise) | Kostenlos |
| **Zahl der Anfragen** | Unbegrenzt | 1 Million Anfragen/Monat |
| **Erweiterte Analysen** | Detaillierte Berichte | Lediglich einfache Statistiken |
| **Benutzerdefinierte Regeln** | Kontospezifische Regeln | Lediglich globale Regeln |
| **Unterstützung für mehrere Domains** | Erweiterte Verwaltung | Grundlegender Support |
| **SLA** | Garantierte Verfügbarkeit von 99,9 % | Nach bestem Bemühen |
| **Support** | Enterprise Support | Unterstützung durch Community |
| **Compliance** | Enterprise-Klasse | Standardkonformität |

**Beide Lösungen bieten:**

- Score-basierte Erkennung (Skala 0,0 bis 1,0)
- Unsichtbare Bedienung (keine Benutzerinteraktion erforderlich)
- Erkennung von Bots durch maschinelles Lernen
- Echtzeit-Risikobewertung

## Einrichten von reCAPTCHA Enterprise


+++ Schritt 1: Vorbereiten der Google Cloud-Umgebung

**Voraussetzungen:**

1. Google Cloud-Projekt mit aktivierter Abrechnung
2. Projekt-ID (aus dem GCP-Dashboard)
3. Domain-Überprüfung für Ihre Formulare
4. Administratorzugriff auf GCP und AEM

**Setup:**

1. Erstellen oder wählen Sie ein Google Cloud-Projekt aus.
   - Navigieren Sie zur [Google Cloud Console](https://console.cloud.google.com/).
   - Erstellen Sie ein neues Projekt oder öffnen Sie ein vorhandenes.
   - Notieren Sie sich Ihre Projekt-ID.

2. Aktivieren Sie die reCAPTCHA Enterprise-API.
   - Navigieren Sie zu „APIs und Services > Bibliothek“.
   - Suchen Sie nach „reCAPTCHA Enterprise-API“.
   - Klicken Sie auf „Aktivieren“.

3. Erstellen Sie Anmeldedaten für die API.
   - Navigieren Sie zu „APIs und Services > Anmeldedaten“.
   - Klicken Sie auf „Anmeldedaten erstellen > API-Schlüssel“.
   - Kopieren und speichern Sie Ihren API-Schlüssel.

4. Erstellen Sie einen Site-Schlüssel.
   - Gehen Sie zu „Sicherheit > reCAPTCHA Enterprise“.
   - Klicken Sie auf „Schlüssel erstellen“.
   - Wählen Sie je nach Punktzahl einen passenden Schlüsseltyp aus.
   - Fügen Sie Ihre Domains hinzu.
   - Legen Sie den Schwellenwert fest (empfohlen: 0,5).

**Validierungs-Checkpoint:** Stellen Sie sicher, dass Sie über Folgendes verfügen:

- Projekt-ID
- API-Schlüssel
- Site-Schlüssel
- Verifizierte Domain in Google Cloud

+++

+++ Schritt 2: Konfigurieren eines AEM Cloud-Konfigurations-Containers

![Schrittweise Einrichtung der Cloud-Konfiguration](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)
*Abbildung: Aktivieren von Cloud-Konfigurationen für Ihren Formular-Container*

**Setup:**

1. Zugriff auf den Konfigurations-Browser
   - Melden Sie sich bei Ihrer AEM-Autoreninstanz an.
   - Wählen Sie „Tools > Allgemein > Konfigurations-Browser“.

2. Aktivieren Sie „Cloud-Konfigurationen“.
   - Suchen Sie den Konfigurations-Container Ihres Formulars.
   - Wählen Sie „Eigenschaften“ aus.
   - Überprüfen Sie „Cloud-Konfigurationen“.
   - Klicken Sie auf „Speichern und schließen“.

3. Überprüfen der Konfiguration
   - Prüfen Sie, ob „Cloud-Konfigurationen“ in den Container-Eigenschaften angezeigt wird.

**Validierungs-Checkpoint:**

- Cloud-Konfigurationen für Ihren Container aktiviert
- Container wird im Konfigurations-Browser angezeigt
- Eigenschaften zeigen „Cloud-Konfigurationen“ als aktiviert an

+++

+++ Schritt 3: Konfigurieren des reCAPTCHA Enterprise-Dienstes in AEM

![reCAPTCHA Enterprise-Konfigurationsbildschirm](/help/edge/docs/forms/universal-editor/assets/recaptcha-enterprise.png)
*Abbildung: reCAPTCHA Enterprise-Konfigurationsoberfläche in AEM*

**Konfiguration:**

1. Rufen Sie die reCAPTCHA-Konfiguration auf.
   - Navigieren Sie zu „Tools > Cloud-Dienste > reCAPTCHA“.
   - Wählen Sie den Konfigurations-Container Ihres Formulars.
   - Klicken Sie auf „Erstellen“.

2. Konfigurieren Sie die Enterprise-Einstellungen.
   - Titel: Beschreibender Name (z. B. „Production reCAPTCHA“)
   - Name: Systemname (automatisch generiert oder benutzerdefiniert)
   - Version: Wählen Sie reCAPTCHA Enterprise aus
   - Projekt-ID: Geben Sie Ihre Google Cloud-Projekt-ID ein
   - Site-Schlüssel: Geben Sie den Site-Schlüssel aus Google Cloud ein
   - API-Schlüssel: Geben Sie Ihren Google Cloud-API-Schlüssel ein
   - Schlüsseltyp: Wählen Sie „Punktzahlbasierter Site-Schlüssel“

3. Legen Sie den Sicherheitsschwellenwert fest
   - Schwellenwert: Festgelegt zwischen 0,0 und 1,0
   - Empfohlene Werte:
      - 0,7 bis 0,9: Hohe Sicherheit (kann manche legitime Benutzende blockieren)
      - 0,5 bis 0,7: Ausgewogene Sicherheit (empfohlen)
      - 0,1 bis 0,5: Geringere Sicherheit (lässt mehr Benutzende zu)

4. Speichern und veröffentlichen
   - Klicken Sie auf „Erstellen“, um die Konfiguration zu speichern.
   - Klicken Sie auf „Veröffentlichen“, um sie verfügbar zu machen.

**Validierungs-Checkpoint:**

- Die Konfiguration wurde erfolgreich gespeichert
- Alle erforderlichen Felder ausgefüllt
- Konfiguration veröffentlicht und sichtbar
- Keine Fehlermeldungen

+++

## Einrichten von reCAPTCHA Standard

+++Schritt 1: Abrufen von reCAPTCHA-API-Schlüsseln (siehe Details)

>[!IMPORTANT]
>
> Edge Delivery Services-Formulare unterstützen nur reCAPTCHA v2 (punktzahlbasiert). Verwenden Sie nicht die Checkbox-Version.

**Schlüsselgenerierung:**

1. Greifen Sie auf die Google reCAPTCHA Console zu.

   - Wechseln Sie zu [Google reCAPTCHA Admin Console](https://www.google.com/recaptcha/admin).
   - Melden Sie sich mit Ihrem Google-Konto an.

2. Erstellen Sie eine neue Site.

   - Klicken Sie auf das &#39;+&#39;-Symbol, um eine neue Site hinzuzufügen.
   - Titel: Geben Sie einen beschreibenden Namen ein.
   - reCAPTCHA-Typ: Wählen Sie reCAPTCHA v2 > „Ich bin kein Roboter“ Unsichtbar.
   - Domains: Fügen Sie die Domains Ihres Formulars hinzu.
   - Akzeptieren Sie die Bedingungen und klicken Sie auf „Senden“.

3. Rufen Sie Ihre Schlüssel ab.

   - Site-Schlüssel: Kopieren Sie den Site-Schlüssel (öffentlicher Schlüssel).
   - Geheimer Schlüssel: Kopieren Sie den geheimen Schlüssel (privater Schlüssel).

**Validierungs-Checkpoint:**

- In der reCAPTCHA-Konsole erstellte Site

- Site-Schlüssel erhalten

- Geheimer Schlüssel erhalten

- Domains hinzugefügt und verifiziert

+++

+++Schritt 2: Konfigurieren des AEM-Cloud-Konfigurations-Containers (siehe Details)

Folgen Sie dem gleichen Prozess wie bei der Einrichtung von Enterprise:

1. Aktivieren Sie im Konfigurations-Browser die Option „Cloud-Konfigurationen“.

2. Überprüfen Sie die Konfiguration des Containers.

3. Bestätigen Sie, dass die Einstellungen gespeichert wurden.

+++

+++Schritt 3: Konfigurieren des reCAPTCHA-Standarddienstes in AEM (siehe Details)

![reCAPTCHA-Standard-Konfigurationsbildschirm](/help/edge/docs/forms/universal-editor/assets/recaptcha.png)
*Abbildung: reCAPTCHA Standard-Konfigurationsoberfläche in AEM*

**Konfiguration:**

1. Rufen Sie die reCAPTCHA-Konfiguration auf.

   - Navigieren Sie zu „Tools > Cloud-Dienste > reCAPTCHA“.
   - Wählen Sie den Konfigurations-Container Ihres Formulars.
   - Klicken Sie auf „Erstellen“.

2. Konfigurieren Sie die Standard-Einstellungen.

   - Titel: Beschreibender Name (z. B. „Standard reCAPTCHA“)
   - Name: Systemname (automatisch generiert oder benutzerdefiniert)
   - Version: Wählen Sie reCAPTCHA v2
   - Site-Schlüssel: Geben Sie Ihren Google reCAPTCHA-Site-Schlüssel ein
   - Geheimschlüssel: Geben Sie Ihren Google reCAPTCHA-Geheimschlüssel ein

3. Speichern und veröffentlichen

   - Klicken Sie auf „Erstellen“, um die Konfiguration zu speichern.
   - Klicken Sie auf „Veröffentlichen“, um sie verfügbar zu machen.

**Validierungs-Checkpoint:**

- Konfiguration ohne Fehler erstellt

- Beide Schlüssel wurden korrekt eingegeben

- Konfiguration erfolgreich veröffentlicht

- Konfiguration wird in der Liste angezeigt

+++

## Hinzufügen von reCAPTCHA zu einem Formular

Fügen Sie nach dem Konfigurieren des reCAPTCHA-Dienstes den folgenden Schutz für Ihr Formular hinzu:

![Hinzufügen der reCAPTCHA-Komponente zu einem Formular](/help/edge/docs/forms/universal-editor/assets/add-recaptcha-component.png)
*Abbildung: Hinzufügen der unsichtbaren CAPTCHA-Komponente zu einem Formular*

+++&#x200B;1. Formular im universellen Editor öffnen
Wechseln Sie zu Ihrem Formular in AEM Sites und klicken Sie auf Bearbeiten , um es im universellen Editor zu öffnen. Warten Sie, bis der Editor geladen wurde.

- Wechseln Sie zu Ihrem Formular in AEM Sites.
- Klicken Sie auf „Bearbeiten“, um es im universellen Editor zu öffnen.
- Warten Sie, bis der Editor geladen wurde
+++

+++&#x200B;2. Suchen Sie die Formularstruktur
Suchen Sie in der Inhaltsstruktur (linker Bereich) den Abschnitt für Ihr adaptives Formular und erweitern Sie die Formularstruktur, um Einfügepunkte anzuzeigen.

- Suchen Sie in der Inhaltsstruktur (linker Bereich) den Abschnitt Ihres adaptiven Formulars.
- Erweitern Sie die Formularstruktur, um Einfügepunkte anzuzeigen.
+++

+++&#x200B;3. Hinzufügen der reCAPTCHA-Komponente
Fügen Sie die CAPTCHA-Komponente (unsichtbar) zu Ihrem Formular hinzu.

- Klicken Sie auf das Symbol „Hinzufügen“ (+) im Formularabschnitt.
- Wählen Sie aus der Komponentenliste „Captcha (Unsichtbar)“ aus.
- Alternativ können Sie die Komponente auch aus dem Bedienfeld „Komponenten“ ziehen.
+++

+++&#x200B;4. Konfigurieren der Komponente (optional)
Wählen Sie die neu hinzugefügte CAPTCHA-Komponente aus und überprüfen Sie, ob sie Ihre reCAPTCHA-Konfiguration verwendet.

- Wählen Sie die neu hinzugefügte CAPTCHA-Komponente aus.
- Überprüfen Sie im Bedienfeld „Eigenschaften“, ob Ihre reCAPTCHA-Konfiguration verwendet wird.
- Für die grundlegende Einrichtung ist keine zusätzliche Konfiguration erforderlich.
+++

+++&#x200B;5. Veröffentlichen Sie Ihre Änderungen
Veröffentlichen Sie Ihre Änderungen und stellen Sie sicher, dass keine Fehler vorliegen.

- Klicken Sie im universellen Editor auf „Veröffentlichen“.
- Warten Sie auf eine Bestätigung.
- Überprüfen Sie, ob Fehler angezeigt werden.
+++

### Überprüfen Sie die Implementierung.

Ihr geschütztes Formular ist jetzt verfügbar unter:

```
https://<branch>--<repo>--<owner>.aem.live/content/forms/af/
<form-name>
```

**Beispiel-URL:**

```
https://main--my-forms--company.aem.live/content/forms/af/
contact-us-form
```
