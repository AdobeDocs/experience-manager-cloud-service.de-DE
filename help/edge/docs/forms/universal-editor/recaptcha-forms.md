---
title: Hinzufügen von Google reCAPTCHA zu Forms im universellen Editor
description: Anleitung zur Implementierung des Google reCAPTCHA-Schutzes in Edge Delivery Services Forms zur Verhinderung von Spam und automatischen Angriffen
feature: Edge Delivery Services
keywords: reCAPTCHA in Formularen, Verwenden von reCAPTCHA im universellen Editor, Hinzufügen von reCAPTCHA in Formularen, Formularsicherheit, Spam-Schutz
role: Developer, Admin
level: Intermediate
exl-id: 1f28bd13-133f-487e-8b01-334be7c08a3f
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 5%

---


# Hinzufügen von Google reCAPTCHA zu Forms im universellen Editor

Google reCAPTCHA hilft beim Schutz von Formularen, indem es zwischen menschlichen Benutzern und automatisierten Bots unterscheidet. In diesem Handbuch wird erläutert, wie Sie sowohl reCAPTCHA Enterprise- als auch Standardversionen im universellen Editor implementieren.

**Ziele:**

- Auswählen der entsprechenden reCAPTCHA-Lösung
- Konfigurieren von reCAPTCHA Enterprise oder Standard
- Hinzufügen von reCAPTCHA zu Formularen
- Validieren und Testen der Implementierung
- Überwachen und Optimieren der Leistung

## Voraussetzungen

Bevor Sie beginnen, stellen Sie Folgendes sicher:

### Zugriffsanforderungen

- AEM as a Cloud Service Authoring-Zugriff
- Universeller Editor-Zugriff mit Berechtigungen zur Formularbearbeitung
- Registrierung für das Early-Access-Programm für reCAPTCHA-Funktionen

### Technische Anforderungen

- Active Google Account
- Für Unternehmen: Google Cloud Platform-Projekt mit aktivierter Abrechnung
- Für Standard: Google reCAPTCHA-Konto
- Eigentümerschaft der Domain für Ihre Formulare verifiziert

### Anforderungen an das Wissen

- Grundlegendes zu AEM Forms und dem universellen Editor
- Vertrautheit mit Cloud Service-Konfigurationen
- Grundlagen der Konzepte zur Formularsicherheit

## Warum sollten Sie reCAPTCHA in Ihrer Forms verwenden?

| ![Sicherheit](/help/edge/docs/forms/universal-editor/assets/security.svg) | ![Bot-Schutz](/help/edge/docs/forms/universal-editor/assets/bot-protection.svg) | ![Anwendererlebnis](/help/edge/docs/forms/universal-editor/assets/user-experience.svg) |
|:-------------:|:-------------:|:-------------:|
| **Erweiterte Sicherheit** | **Bot- und Spam-Abwehr** | **Nahtloses Anwendererlebnis** |
| Schützen von Formularen vor betrügerischen Aktivitäten und Angriffen | Verhindern, dass automatisierte Bots Formulare senden | Unsichtbares reCAPTCHA stört keine rechtmäßigen Benutzer |

**Schlüsselkonzept:** reCAPTCHA nutzt maschinelles Lernen, um das Benutzerverhalten zu analysieren, und weist einen Wert (0,0 bis 1,0) zu, der die Wahrscheinlichkeit menschlicher Interaktion angibt. Höhere Werte zeigen menschliche Benutzer an, niedrigere Werte deuten auf Bots hin.

**Beispiel** Ein Steuerberechnungsformular, das sensible Daten verarbeitet, muss vor automatischen Angriffen geschützt werden. reCAPTCHA überprüft, ob die Einreichungen von echten Benutzern und nicht von Bots stammen.

## Wählen Ihrer reCAPTCHA-Lösung

Edge Delivery Services Forms unterstützt zwei Google reCAPTCHA-Optionen. Verwenden Sie die folgenden Kriterien, um die richtige Lösung auszuwählen:

### Schnellentscheidungsleitfaden

**Verwenden Sie reCAPTCHA Enterprise, wenn Sie Folgendes haben:**

- Formulare mit hohem Traffic (>10.000 Anfragen/Monat)
- Strenge Compliance-Anforderungen (DSGVO, SOX, HIPAA)
- Bedarf an erweiterten Analysen und Berichten
- Budget für Premium-Sicherheitsfunktionen
- Komplexe Multi-Domain-Bereitstellungen

**Verwenden Sie reCAPTCHA Standard, wenn Sie Folgendes haben:**

- Geringer bis moderater Traffic (&lt; 10.000 Anfragen/Monat)
- Grundlegende Sicherheitsanforderungen
- Eingeschränktes Budget (Free Tier)
- Einfache Einrichtung einer Domain
- Neu bei reCAPTCHA

### Detailvergleich

| **Funktion** | **ReCaptcha Enterprise** | **reCAPTCHA Standard** |
|-------------|--------------------------|------------------------|
| **Kosten** | Bezahlt (nutzungsbasierte Preise) | Kostenlos |
| **Anfragelimit** | Unbegrenzt | 1 Million Anfragen/Monat |
| **Erweiterte** | Detaillierte Berichte | Nur einfache Statistiken |
| **Benutzerdefinierte Regeln** | Kontospezifische Regeln | Nur globale Regeln |
| **Multi-Domain-Unterstützung** | Erweiterte Verwaltung | Grundlegende Unterstützung |
| **SLA** | 99,9 % Uptime-Garantie | Beste Anstrengung |
| **Support** | Enterprise-Support | Unterstützung durch die Gemeinschaft |
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
3. Domain-Überprüfung für Formulare
4. Administratorzugriff auf GCP und AEM

**Setup:**

1. Erstellen oder Auswählen eines Google Cloud-Projekts
   - Zur [Google Cloud-Konsole](https://console.cloud.google.com/)
   - Neues Projekt erstellen oder vorhandenes Projekt auswählen
   - Notieren Sie Ihre Projekt-ID

2. Aktivieren der reCAPTCHA Enterprise API
   - Navigieren Sie zu APIs und Services > Bibliothek
   - Suchen Sie nach „reCAPTCHA Enterprise API“
   - Klicken Sie auf Aktivieren

3. API-Anmeldedaten erstellen
   - Navigieren Sie zu APIs und Services > Anmeldedaten .
   - Klicken Sie auf Anmeldedaten erstellen > API-Schlüssel
   - Kopieren und Speichern des API-Schlüssels

4. Site-Schlüssel erstellen
   - Gehen Sie zu Sicherheit > reCAPTCHA Enterprise
   - Klicken Sie auf Schlüssel erstellen
   - Auf der Punktzahl basierenden Schlüsseltyp auswählen
   - Domain(s) hinzufügen
   - Schwellenwert festlegen (empfohlen: 0,5)

**Validierungs-Checkpoint:** Stellen Sie sicher, dass Sie über Folgendes verfügen:

- Projekt-ID
- API-Schlüssel
- Site-Schlüssel
- Verifizierte Domain in Google Cloud

+++

+++ Schritt 2: Konfigurieren des AEM Cloud-Konfigurations-Containers

![Schrittweise Einrichtung der Cloud-Konfiguration](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)
*Abbildung: Aktivieren von Cloud-Konfigurationen für Ihren Formular-Container*

**Setup:**

1. Zugriff auf Konfigurations-Browser
   - Melden Sie sich bei Ihrer AEM-Autoreninstanz an.
   - Navigieren Sie zu Tools > Allgemein > Konfigurationsbrowser

2. Aktivieren von Cloud-Konfigurationen
   - Suchen Sie den Konfigurations-Container Ihres Formulars
   - Eigenschaften auswählen
   - Überprüfen von Cloud-Konfigurationen
   - Klicken Sie auf Speichern und schließen

3. Überprüfen der Konfiguration
   - Bestätigen Sie, dass „Cloud-Konfigurationen“ in den Container-Eigenschaften angezeigt wird

**Validierungs-Checkpoint:**

- Für Ihren Container aktivierte Cloud-Konfigurationen
- Container wird im Konfigurations-Browser angezeigt
- Eigenschaften zeigen „Cloud-Konfigurationen“ als aktiviert an

+++

+++ Schritt 3: Konfigurieren des reCAPTCHA Enterprise-Service in AEM

![reCAPTCHA Enterprise-Konfigurationsbildschirm](/help/edge/docs/forms/universal-editor/assets/recaptcha-enterprise.png)
*Abbildung: reCAPTCHA Enterprise-Konfigurationsschnittstelle in AEM*

**Konfiguration:**

1. Zugreifen auf die reCAPTCHA-Konfiguration
   - Navigieren Sie zu Tools > Cloud Services > reCAPTCHA
   - Wählen Sie den Konfigurations-Container Ihres Formulars
   - Klicken Sie auf Erstellen

2. Konfigurieren von Unternehmenseinstellungen
   - Titel: Beschreibender Name (z. B. „Production reCAPTCHA„)
   - Name: Systemname (automatisch generiert oder benutzerdefiniert)
   - Version: reCAPTCHA Enterprise auswählen
   - Projekt-ID: Geben Sie Ihre Google Cloud-Projekt-ID ein
   - Site-Schlüssel: Geben Sie den Site-Schlüssel aus Google Cloud ein
   - API-Schlüssel: Geben Sie Ihren Google Cloud-API-Schlüssel ein
   - Schlüsseltyp: Wählen Sie den Bewertungsbasierten Site-Schlüssel

3. Sicherheitsschwellenwert festlegen
   - Schwellenwert: Zwischen 0,0 und 1,0 festgelegt
   - Empfohlene Werte:
      - 0.7-0.9: Hohe Sicherheit (kann einige legitime Benutzer blockieren)
      - 0.5-0.7: Ausgewogene Sicherheit (empfohlen)
      - 0.1-0.5: Geringere Sicherheit (ermöglicht mehr Benutzer)

4. Speichern und veröffentlichen
   - Klicken Sie auf Erstellen , um die Konfiguration zu speichern
   - Klicken Sie auf Veröffentlichen , um sie verfügbar zu machen

**Validierungs-Checkpoint:**

- Konfiguration erfolgreich gespeichert
- Alle erforderlichen Felder ausgefüllt
- Konfiguration veröffentlicht und sichtbar
- Keine Fehlermeldungen

+++

## Einrichten von reCAPTCHA Standard

+++Schritt 1: Abrufen von reCAPTCHA-API-Schlüsseln (siehe Details)

>[!IMPORTANT]
>
> Edge Delivery Services Forms unterstützt nur reCAPTCHA v2 (Score-basiert). Checkbox-Version nicht verwenden.

**Schlüsselgenerierung:**

1. Zugriff auf die Google reCAPTCHA-Konsole

   - Wechseln Sie zu [Google reCAPTCHA Admin Console](https://www.google.com/recaptcha/admin)
   - Mit Google-Konto anmelden

2. Neue Site erstellen

   - Klicken Sie auf + , um eine neue Site hinzuzufügen
   - Titel: Geben Sie einen beschreibenden Namen ein
   - reCAPTCHA-Typ: Wählen Sie reCAPTCHA v2 > „Ich bin kein Roboter“ Unsichtbar
   - Domains: Formular-Domain(s) hinzufügen
   - Akzeptieren Sie die Bedingungen und klicken Sie auf Senden

3. Schlüssel abholen

   - Site-Schlüssel: Kopieren Sie den Site-Schlüssel (öffentlicher Schlüssel).
   - Geheimer Schlüssel: Kopieren Sie den geheimen Schlüssel (privaten Schlüssel).

**Validierungs-Checkpoint:**

- In der reCAPTCHA-Konsole erstellte Site

- Erhaltener Site-Schlüssel

- Erhaltener geheimer Schlüssel

- Domain(s) hinzugefügt und verifiziert

+++

+++Schritt 2: Konfigurieren des AEM-Cloud-Konfigurations-Containers (siehe Details)

Folgen Sie dem gleichen Prozess wie bei der Einrichtung von Enterprise:

1. Aktivieren von Cloud-Konfigurationen im Konfigurations-Browser

2. Container-Konfiguration überprüfen

3. Speichern der Einstellungen bestätigen

+++

+++Schritt 3: Konfigurieren des reCAPTCHA-Standarddienstes in AEM (siehe Details)

![reCAPTCHA-Standardkonfigurationsbildschirm](/help/edge/docs/forms/universal-editor/assets/recaptcha.png)
*Abbildung: Standardkonfigurationsschnittstelle von reCAPTCHA in AEM*

**Konfiguration:**

1. Zugreifen auf die reCAPTCHA-Konfiguration

   - Navigieren Sie zu Tools > Cloud Services > reCAPTCHA
   - Wählen Sie den Konfigurations-Container Ihres Formulars
   - Klicken Sie auf Erstellen

2. Konfigurieren von Standardeinstellungen

   - Titel: Beschreibender Name (z. B. „Standard reCAPTCHA„)
   - Name: Systemname (automatisch generiert oder benutzerdefiniert)
   - Version: reCAPTCHA v2 auswählen
   - Site-Schlüssel: Geben Sie Ihren Google reCAPTCHA-Site-Schlüssel ein
   - Geheimschlüssel: Geben Sie den Google reCAPTCHA-Geheimschlüssel ein.

3. Speichern und veröffentlichen

   - Klicken Sie auf Erstellen , um die Konfiguration zu speichern
   - Klicken Sie auf Veröffentlichen , um sie verfügbar zu machen

**Validierungs-Checkpoint:**

- Konfiguration ohne Fehler erstellt

- Beide Schlüssel wurden korrekt eingegeben

- Konfiguration erfolgreich veröffentlicht

- Konfiguration wird in der Liste angezeigt

+++

## Hinzufügen von reCAPTCHA zu einem Formular

Fügen Sie nach dem Konfigurieren des reCAPTCHA-Service den folgenden Schutz für Ihr Formular hinzu:

![Hinzufügen der reCAPTCHA-Komponente zu einem Formular](/help/edge/docs/forms/universal-editor/assets/add-recaptcha-component.png)
*Abbildung: Hinzufügen der unsichtbaren CAPTCHA-Komponente zu einem Formular*

+++1. Formular im universellen Editor öffnen
Wechseln Sie zu Ihrem Formular in AEM Sites und klicken Sie auf Bearbeiten , um es im universellen Editor zu öffnen. Warten Sie, bis der Editor geladen wurde.

- Wechseln Sie zu Ihrem Formular in AEM Sites
- Klicken Sie auf Bearbeiten , um im universellen Editor zu öffnen
- Warten Sie, bis der Editor geladen wird
+++

+++2. Suchen der Formularstruktur
Suchen Sie in der Inhaltsstruktur (linker Bereich) den Abschnitt für Ihr adaptives Formular und erweitern Sie die Formularstruktur, um Einfügepunkte anzuzeigen.

- Suchen Sie in der Inhaltsstruktur (linker Bereich) den Abschnitt für Ihr adaptives Formular
- Erweitern Sie die Formularstruktur, um Einfügepunkte anzuzeigen
+++

+++3. Hinzufügen der reCAPTCHA-Komponente
Fügen Sie die CAPTCHA-Komponente (unsichtbar) zu Ihrem Formular hinzu.

- Klicken Sie auf das Symbol Hinzufügen (+) im Abschnitt Formular .
- Wählen Sie aus der Komponentenliste CAPTCHA (Unsichtbar) aus
- Alternativ können Sie die Komponente auch aus dem Bedienfeld „Komponenten“ ziehen
+++

+++4. Komponente konfigurieren (optional)
Wählen Sie die neu hinzugefügte CAPTCHA-Komponente aus und überprüfen Sie, ob sie Ihre reCAPTCHA-Konfiguration verwendet.

- Auswählen der neu hinzugefügten CAPTCHA-Komponente
- Überprüfen Sie im Bedienfeld Eigenschaften , ob Ihre reCAPTCHA-Konfiguration verwendet wird
- Für die grundlegende Einrichtung ist keine zusätzliche Konfiguration erforderlich
+++

+++5. Veröffentlichen der Änderungen
Veröffentlichen Sie Ihre Änderungen und stellen Sie sicher, dass keine Fehler vorliegen.

- Klicken Sie im universellen Editor auf Veröffentlichen .
- Auf Bestätigung warten
- Überprüfen, ob keine Fehler angezeigt werden
+++

### Überprüfen der Implementierung

Ihr geschütztes Formular ist jetzt verfügbar unter:

```
https://<branch>--<repo>--<owner>.aem.live/content/forms/af/
<form-name>
```

**Beispiel-URL:**

```
https://main--my-forms--company.aem.live/content/forms/af/
contact-form
```
