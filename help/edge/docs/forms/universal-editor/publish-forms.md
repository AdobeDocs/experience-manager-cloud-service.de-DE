---
title: Veröffentlichen adaptiver Formulare mit Edge Delivery Services
description: Erfahren Sie, wie Sie adaptive Formulare mit Edge Delivery Services zum Einsatz in der Produktion veröffentlichen, konfigurieren und aufrufen können.
feature: Edge Delivery Services
role: Admin, Developer
level: Intermediate
keywords: Formulare veröffentlichen, Edge Delivery Services, Formularkonfiguration, CORS, Referrer-Filter
exl-id: ba1c608d-36e9-4ca1-b87b-0d1094d978db
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 100%

---

# Veröffentlichen adaptiver Formulare mit Edge Delivery Services

Durch das Veröffentlichen eines adaptiven Formulars wird es in Edge Delivery Services für Endbenutzerinnen und -benutzer verfügbar, die es aufrufen und versenden möchten. Dieser Prozess beinhaltet drei Hauptphasen: Veröffentlichen des Formulars, Konfigurieren der Sicherheitseinstellungen und Zugreifen auf das Live-Formular.

**Was Sie erreichen werden:**

- Veröffentlichen Ihres Formulars mit Edge Delivery Services
- Konfigurieren der Sicherheitseinstellungen für die Formularübermittlung
- Aufrufen und Überprüfen des veröffentlichten Formulars
- Einrichten von korrektem URL-Routing und CORS-Richtlinien

## Voraussetzungen

- Ein adaptives Formular, das mithilfe der Vorlage „Edge Delivery Services“ erstellt wurde 
- Formular getestet und produktionsbereit
- AEM Forms-Autorenberechtigungen
- Zugriff auf Cloud Manager (für Produktionskonfiguration)
- Entwicklerzugriff auf den Formularblock-Code (für die Einrichtung der Übermittlung)

## Veröffentlichungsprozess – Übersicht

Das Veröffentlichen von Formularen in Edge Delivery Services erfolgt in drei Phasen:

- **Phase 1: Formularveröffentlichung** – Veröffentlichen Sie Ihr Formular im CDN und überprüfen Sie den Veröffentlichungsstatus.
- **Phase 2: Sicherheitskonfiguration** – Richten Sie CORS-Richtlinien und Referrer-Filter für sichere Übermittlungen ein.
- **Phase 3: Zugriff und Validierung** – Testen Sie die Formularfunktionalität und validieren Sie den gesamten Workflow.

Jede Phase baut auf der vorherigen auf, um eine sichere, funktionale Bereitstellung zu gewährleisten.

### Phase 1: Formular veröffentlichen

+++ Schritt 1: Veröffentlichung starten

1. **Zugriff auf Ihr Formular**: Öffnen Sie Ihr adaptives Formular im universellen Editor.
2. **Veröffentlichung starten**: Klicken Sie in der Symbolleiste auf das Symbol **Veröffentlichen**.

   ![Klicken auf „Veröffentlichen“](/help/edge/docs/forms/universal-editor/assets/publish-form-ue.png)

+++


+++ Schritt 2: Überprüfen und bestätigen

1. **Zu veröffentlichende Assets prüfen**: Das System zeigt alle Assets an, die veröffentlicht werden sollen, einschließlich Ihres Formulars.

   ![Beim Klicken auf „Veröffentlichen“](/help/edge/docs/forms/universal-editor/assets/publish-form-ue-review.png)

2. **Veröffentlichung bestätigen**: Klicken Sie auf **Veröffentlichen**, um fortzufahren.
3. **Erfolg überprüfen**: Suchen Sie nach der Bestätigungsmeldung.

   ![Erfolgreiche Veröffentlichung](/help/edge/docs/forms/universal-editor/assets/publish-form-ue-success.png)

+++


+++ Schritt 3: Veröffentlichungsstatus überprüfen

**Status überprüfen**: Klicken Sie erneut auf das Symbol **Veröffentlichen**, um den aktuellen Status anzuzeigen.

![Veröffentlichungsstatus](/help/edge/docs/forms/universal-editor/assets/publish-form-ue-validate.png)

**Validierungs-Checkpoint:**

- Das Formular weist im Editor den Status „Veröffentlicht“ auf
- Keine Fehlermeldungen während des Veröffentlichungsprozesses
- Formular erscheint in der Liste der veröffentlichten Assets

+++


+++ Verwalten von veröffentlichten Formularen

**So heben Sie die Veröffentlichung eines Formulars auf:**

1. Öffnen Sie das Formular im universellen Editor.
2. Klicken Sie auf das Dreipunkt-Menü (⋯) oben rechts.
3. Wählen Sie **Veröffentlichung aufheben** aus.

![Heben Sie die Veröffentlichung des Formulars auf.](/help/edge/docs/forms/universal-editor/assets/unpublish-ue.png)

+++


### Phase 2: Sicherheitseinstellungen konfigurieren

+++ Warum eine Sicherheitskonfiguration erforderlich ist

Für sichere Formularübermittlungen müssen Sie Sicherheitseinstellungen konfigurieren, die:

- Es Edge Delivery Services erlauben, Daten an AEM zu senden
- Nicht autorisierten Zugriff auf Ihre AEM-Instanz verhindern
- CORS (Cross-Origin Resource Sharing) für Formularübermittlungen aktivieren
- Anfragen so filtern, dass nur rechtmäßige Edge Delivery-Domains zugelassen werden

>[!IMPORTANT]
>
>**Für Produktion erforderlich**: Diese Konfigurationen sind obligatorisch, damit Formularübermittlungen in Produktionsumgebungen funktionieren.

+++



+++ Schritt 1: URL für Formularübermittlung konfigurieren

**Zweck**: Direkte Formularübermittlungen an Ihre AEM-Instanz

**Dateispeicherort**: `blocks/form/constant.js` in Ihrem Edge Delivery Services-Projekt

**Konfigurationsbeispiele:**

```javascript
// Production Environment
export const submitBaseUrl = 'https://publish-p120-e12.adobeaemcloud.com';

// Local Development Environment  
export const submitBaseUrl = 'http://localhost:4503';

// Staging Environment
export const submitBaseUrl = 'https://publish-staging-p120-e12.adobeaemcloud.com';
```

**Validierungs-Checkpoint:**

- `constant.js` Datei wurde mit der richtigen AEM-Veröffentlichungs-URL aktualisiert
- URL entspricht Ihrer Umgebung (Produktion, Staging oder lokal)
- Kein abschließender Schrägstrich in der URL

+++



+++ Schritt 2: CORS-Einstellungen konfigurieren

**Zweck**: Anfragen zur Formularübermittlung von Edge Delivery Services-Domains zulassen

**Implementierung**: Hinzufügen der CORS-Konfiguration zu Ihrer AEM Dispatcher- oder Apache-Konfiguration

```apache
# Local Development Environment
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true

# Edge Delivery Services - Preview/Stage Environment  
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true

# Edge Delivery Services - Production Environment
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```

**Validierungs-Checkpoint:**

- CORS-Regeln auf die Dispatcher-Konfiguration angewendet
- Alle erforderlichen Domains (localhost, hlx.page, hlx.live) sind enthalten
- Konfiguration in der Zielumgebung bereitgestellt

**Referenzdokumentation:**

- [CORS-Konfigurationshandbuch](https://experienceleague.adobe.com/de/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors)
- [Dokumentation zum Referrer-Filter](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/headless/deployment/referrer-filter)

+++



+++ Schritt 3: Referrer-Filter konfigurieren

**Zweck**: Schreibvorgänge auf autorisierte Edge Delivery Services-Domains beschränken

**Implementierungsmethode**: Konfigurieren über Cloud Manager in AEM as a Cloud Service

**Konfigurationsdatei**: Zur OSGi-Konfiguration Ihres Projekts hinzufügen

```json
{
  "allow.empty": false,
  "allow.hosts": [],
  "allow.hosts.regexp": [
    "https://.*\\.hlx\\.page:443",
    "https://.*\\.hlx\\.live:443"
  ],
  "filter.methods": [
    "POST",
    "PUT", 
    "DELETE",
    "COPY",
    "MOVE"
  ],
  "exclude.agents.regexp": [
    ""
  ]
}
```

**Konfigurationsaufschlüsselung:**

- **`allow.empty`**: Lehnt Anfragen ohne Referrer-Kopfzeilen ab
- **`allow.hosts.regexp`**: Lässt Anfragen von Edge Delivery Services-Domains zu
- **`filter.methods`**: Wendet Filterung auf diese HTTP-Methoden an
- **`exclude.agents.regexp`**: Benutzeragenten von der Filterung ausgeschlossen

**Validierungs-Checkpoint:**

- Konfiguration des Referrer-Filters, bereitgestellt über Cloud Manager
- Konfiguration in der AEM-Veröffentlichungsinstanz aktiv
- Übermittlung des Testformulars erfolgt über die Edge Delivery Services-Domain
- Nicht autorisierte Domains können keine Formulare senden

**Referenzdokumentation:**

- [Konfigurieren des Referrer-Filters über Cloud Manager](https://experienceleague.adobe.com/de/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing)

+++


### Phase 3: Das veröffentlichte Formular aufrufen



+++ URL-Struktur für Edge Delivery Services

**Standard-URL-Format:**

```
https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>
```

**URL-Komponenten:**

- **`<branch>`**: Name der Git-Verzweigung (normalerweise `main`)
- **`<repo>`**:Repository-Name
- **`<owner>`**: GitHub-Organisation oder -Benutzername
- **`<form_name>`**: Name Ihres Formulars (in Kleinbuchstaben, mit Bindestrich)

**Umgebungsspezifische URLs:**

```
# Production Environment (.aem.live)
https://main--universaleditor--wkndforms.aem.live/content/forms/af/wknd-form

# Preview Environment (.aem.page) 
https://main--universaleditor--wkndforms.aem.page/content/forms/af/wknd-form
```

+++



+++ Abschließende Validierungsschritte

**Ein-/Ausgabehilfe von Formularen überprüfen:**

1. **Laden von Formularen testen**: Besuchen Sie Ihre Formular-URL und prüfen Sie, ob sie ordnungsgemäß geladen wird.
2. **Formularübermittlung testen**: Füllen Sie das Formular aus und senden Sie es, um die Datenverarbeitung zu überprüfen.
3. **Responsives Design prüfen**: Testen Sie das Formular mit verschiedenen Geräten und Bildschirmgrößen.
4. **Sicherheit überprüfen**: Stellen Sie sicher, dass CORS und Referrer-Filter ordnungsgemäß funktionieren.

**Erwartete Ergebnisse:**

- Formular wird fehlerfrei geladen
- Alle Formularfelder werden korrekt wiedergegeben
- Formularübermittlungsprozesse erfolgreich
- Daten werden im konfigurierten Ziel (Tabelle, E-Mail usw.) angezeigt
- Keine Konsolenfehler im Zusammenhang mit CORS oder Sicherheitsrichtlinien

+++


## Nächste Schritte


- [Konfigurieren von Formularübermittlungsaktionen](/help/edge/docs/forms/universal-editor/submit-action.md)
- [Gestalten und Gestalten von Formularen](/help/edge/docs/forms/universal-editor/style-theme-forms.md)
- [Erstellen von responsiven Formular-Layouts](/help/edge/docs/forms/universal-editor/responsive-layout.md)
- [Hinzufügen von reCAPTCHA-Schutz](/help/edge/docs/forms/universal-editor/recaptcha-forms.md)



