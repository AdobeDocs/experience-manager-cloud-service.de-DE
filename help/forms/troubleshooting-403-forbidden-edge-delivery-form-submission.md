---
title: Fehlerbehebung für 403 Forbidden Errors in Edge Delivery Services Form Submission
description: Erfahren Sie, wie Sie 403-Fehler (Forbidden) beim Senden von Formularen von Edge Delivery Services an die AEM-Veröffentlichungsinstanz diagnostizieren und beheben können. In diesem Handbuch werden gängige Ursachen wie CORS, Dispatcher-Regeln und Probleme mit Referrer-Filtern behandelt.
feature: Edge Delivery Services, Forms
role: Admin, Developer
source-git-commit: d3ade6ee9216b44b55d6808d8acffe83f1e263c9
workflow-type: tm+mt
source-wordcount: '1117'
ht-degree: 3%

---


# Fehlerbehebung für 403 Forbidden Errors in Edge Delivery Services Form Submission {#troubleshooting-403-forbidden-edge-delivery}

Beim Senden von Formularen von Edge Delivery Services an die AEM-Veröffentlichungsinstanz tritt möglicherweise der Fehler **403 Verboten** auf. Dieser Fehler zeigt an, dass der Server die Verarbeitung der Anfrage ablehnt, normalerweise aufgrund von Sicherheitskonfigurationen. Dieser Artikel hilft Ihnen, die häufigsten Ursachen dieses Problems zu identifizieren und zu beheben.

## Problembeschreibung

Beim Senden von Formularen von Edge Delivery Services an die AEM-**tritt ein** 403 Forbidden&#39;-Fehler auf. Der Fehler wird wie folgt angezeigt:

- HTTP-Status-Code: 403
- Fehlermeldung: „Forbidden“ oder „Access Denied“
- Die Formularübermittlung schlägt fehl, ohne dass das AEM-Übermittlungs-Servlet erreicht wird

Dieses Problem tritt häufig bei Edge Delivery Services-Integrationen auf, bei denen auf Edge-Domains (`.aem.live`, `.aem.page`, `.hlx.page`, `.hlx.live`) gehostete Formulare versuchen, Daten an AEM-Veröffentlichungsinstanzen zu senden.

>[!IMPORTANT]
>
>Bei RepoLess-Setups können mehrere Sites mit demselben Repository gehostet werden. Jede Site-Domain muss einzeln zu den Zulassungslisten hinzugefügt werden, damit Formularübermittlungen ordnungsgemäß funktionieren.
>
>**Beispiel:**
>
>- Repository: `https://github.com/adobe/abc`
>- Site 1: `main--abc--adobe.aem.live`
>- Site 2: `main--abc1--adobe.aem.live`
>
>Auf die Zulassungsliste setzen Beide Domains benötigen separate Formulareinträge, damit die Formularübermittlung von beiden Sites aus funktioniert.

## Häufige Ursachen und Lösungen

Ein 403-Forbidden-Fehler bei der Übermittlung von Edge Delivery Services-Formularen kann mehrere Ursachen haben. Führen Sie die folgenden Schritte zur Fehlerbehebung in der richtigen Reihenfolge aus:

### &#x200B;1. CORS-Probleme (Cross-Origin Resource Sharing)

**Symptome:**

- Die Browser-Konsole zeigt CORS-bezogene Fehlermeldungen an
- Die Registerkarte Netzwerk zeigt an, dass die Anfrage blockiert wird, bevor sie den Server erreicht
- Fehlermeldungen mit Hinweis auf „Cross-Origin Request Blocked“

**Diagnose:**

1. Browser-Entwickler-Tools öffnen (F12)
2. Überprüfen Sie die Registerkarte Konsole auf CORS-Fehlermeldungen.
3. Suchen Sie nach Nachrichten wie: `Access to fetch at 'https://publish-xxx.adobeaemcloud.com' from origin 'https://main--repo--owner.aem.live' has been blocked by CORS policy`

**Lösung:**
Konfigurieren Sie CORS-Einstellungen in AEM, um Anfragen von Ihren spezifischen Edge Delivery-Site-Domains zuzulassen:

```apache
# Developer Localhost
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true

# Edge Delivery Sites - Add each site domain individually
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://main--abc--adobe\.aem\.live$)#" CORSTrusted=true
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://main--abc1--adobe\.aem\.live$)#" CORSTrusted=true

# Legacy Franklin domains (if still in use)
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true  
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```

>[!NOTE]
>
>Ersetzen Sie `main--abc--adobe.aem.live` und `main--abc1--adobe.aem.live` durch Ihre tatsächlichen Site-Domains. Jede Site, die vom selben Repository gehostet wird, erfordert einen separaten CORS-Konfigurationseintrag.

Weitere Informationen zur CORS-Konfiguration finden Sie im [CORS-Konfigurationshandbuch](https://experienceleague.adobe.com/de/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors).

### &#x200B;2. Dispatcher-Regeln

**Symptome:**

- 403-Fehler ohne CORS-Meldungen in Browser-Konsole
- Anfrage gelangt auf den Server, wird aber von Dispatcher blockiert
- Fehler tritt auf, bevor die AEM-Anwendungsebene erreicht wird

**Diagnose:**

1. Überprüfen Sie, ob die Anfrage-URL mit Dispatcher-Filterregeln übereinstimmt
2. Überprüfen Sie die Dispatcher-Konfiguration auf `/filter`, die POST-Anfragen blockieren könnten.
3. Überprüfen Sie, ob der Formularübermittlungsendpunkt in der Dispatcher-Konfiguration zulässig ist

**Lösung:**
Aktualisieren Sie die Dispatcher-Konfiguration, um Formularübermittlungsanfragen zuzulassen:

1. Stellen Sie sicher, dass POST-Anfragen an Formularübermittlungsendpunkte zulässig sind
2. Hinzufügen geeigneter Filterregeln für Edge Delivery-Domains
3. Stellen Sie sicher, dass der Pfad des Übermittlungs-Servlets nicht blockiert ist

Beispiel für eine Dispatcher-Filterkonfiguration:

```apache
/filter {
  # Allow POST requests to form submission servlet
  /0100 { /type "allow" /method "POST" /url "/content/forms/af/*" }
  /0101 { /type "allow" /method "POST" /url "/adobe/forms/af/submit/*" }
  /0102 { /type "allow" /method "POST" /url "/content/forms/portal/submit/adaptiveform" }
}
```

### &#x200B;3. Probleme mit Referrer-Filtern

**Symptome:**

- 403-Fehler ohne CORS-Probleme in der Browser-Konsole
- Anfrage erreicht AEM, wird jedoch vom Sling Referrer-Filter abgelehnt
- Fehler auf der Anwendungsebene von AEM

**Diagnose:**
Überprüfen Sie die AEM-Fehlerprotokolle auf Nachrichten zur Ablehnung des Referrer-Filters:

1. [Zugriff auf AEM Cloud Service-Protokolle über Cloud Manager](/help/implementing/cloud-manager/manage-logs.md)
2. Suchen Sie nach Einträgen in `aemerror.log`, die Folgendes enthalten:
   - „Referrer-Filter abgelehnt“
   - „org.apache.sling.security.impl.ReferrerFilter“
   - Meldungen zu Fehlern bei der Referrer-Validierung

**Beispiel für einen Protokolleintrag:**

```
[ERROR] org.apache.sling.security.impl.ReferrerFilter Referrer filter rejected request with referrer 'https://main--abc--adobe.aem.live' for POST /content/forms/af/submit
```

**Lösung:**
Konfigurieren Sie den Referrer-Filter, um Ihre spezifischen Edge Delivery-Site-Domains zuzulassen:

1. Erstellen oder aktualisieren Sie die OSGi-Konfigurationsdatei: `org.apache.sling.security.impl.ReferrerFilter.cfg.json`

2. Fügen Sie die folgende Konfiguration mit Ihren spezifischen Site-Domains hinzu:

   ```json
   {
     "allow.empty": false,
     "allow.hosts": [
       "main--abc--adobe.aem.live",
       "main--abc1--adobe.aem.live"
     ],
     "allow.hosts.regexp": [
       "https://.*\\.aem\\.live:443",
       "https://.*\\.aem\\.page:443",
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

3. Bereitstellen der Konfiguration über Cloud Manager

>[!IMPORTANT]
>
>**Forrepoless-Setups** Sie müssen jede Website-Domain einzeln zum `allow.hosts`-Array hinzufügen. Die Verwendung von nur Regex-Mustern ist möglicherweise nicht für alle Szenarien ausreichend. Schließen Sie sowohl spezifische Domains als auch Regex-Muster für eine umfassende Abdeckung ein.

>[!WARNING]
>
>Der Referrer-Filter von AEM ist keine OSGi-Konfigurations-Factory, d. h., für einen AEM-Service ist immer nur eine Konfiguration aktiv. Wenn möglich, vermeiden Sie das Hinzufügen benutzerdefinierter Referrer-Filterkonfigurationen, da dies die nativen Konfigurationen von AEM überschreibt und die Produktfunktionalität beeinträchtigen kann.

## Diagnoseschritte

Führen Sie die folgenden Schritte aus, um die spezifische Ursache Ihres 403-Fehlers zu identifizieren:

### Schritt 1: Browser-Konsole überprüfen

1. Browser-Entwickler-Tools öffnen (F12)
2. Navigieren Sie zur Registerkarte Konsole .
3. Formularübermittlung versuchen
4. Suchen nach CORS-bezogenen Fehlermeldungen

**Wenn CORS-Fehler vorhanden sind:** Befolgen Sie die obige CORS-Lösung.
**Wenn keine CORS-Fehler auftreten:** Mit Schritt 2 fortfahren.

### Schritt 2: Prüfen Sie die Registerkarte „Netzwerk“

1. Browser-Entwickler-Tools öffnen (F12)
2. Navigieren Sie zur Registerkarte Netzwerk .
3. Formularübermittlung versuchen
4. Überprüfen der Details zur fehlgeschlagenen Anfrage
5. Antwort-Header und -Status anzeigen

**Wenn die Anfrage den Server nicht erreicht** Wahrscheinlich ein Dispatcher-Problem.
**Wenn die Anfrage den Server erreicht, aber fehlschlägt**: Wahrscheinlich ein Referrer-Filter-Problem.

### Schritt 3: AEM-Protokolle überprüfen

1. Zugreifen auf Cloud Manager
2. Navigieren Sie zu Umgebungen → Ihrer Umgebung → Protokollen
3. Herunterladen oder Anzeigen von `aemerror.log`
4. Suche nach Einträgen zum Zeitpunkt der Formularübermittlung
5. Nach Referrer-Filtern oder sicherheitsrelevanten Nachrichten suchen

## Prävention und Best Practices

### &#x200B;1. Korrekte Konfiguration während der Einrichtung

- Konfigurieren der Einstellungen für CORS, Dispatcher und Referrer-Filter beim ersten Einrichten von Edge Delivery Services
- **Für jede neue Site:** die spezifische Domain zu allen Zulassungslisten hinzu (CORS, Referrer-Filter)
- Testen von Formularübermittlungen in der Entwicklungsumgebung vor der Live-Schaltung

### &#x200B;2. Umgebungsspezifische Konfigurationen

- Verwenden unterschiedlicher Konfigurationen für Entwicklungs-, Staging- und Produktionsumgebungen
- Einschließen von localhost-Domains zum Testen der lokalen Entwicklung
- auf die Zulassungsliste setzen **Alle Website-Domains dokumentieren** auf die das Repository Zugriff benötigt

### &#x200B;3. Überwachung und Protokollierung

- Einrichten der Protokollüberwachung für Zurückweisungen des Referrer-Filters
- Implementieren einer ordnungsgemäßen Fehlerbehandlung im Code für die Formularübermittlung
- Verwenden von Browser-Entwickler-Tools während des Testens

### &#x200B;4. Dokumentation und Team-Kenntnisse

- **Pflegen Sie eine Registrierung** aller Site-Domains, die dasselbe Repository verwenden
- Schulung des Entwicklungsteams in Schritten zur Fehlerbehebung
- Verwalten einer Checkliste für die Einrichtung von Edge Delivery Services-Formularen
- **Zulassungslisten aktualisieren** wenn neue Sites aus vorhandenen Repositorys erstellt werden

## Site-Domain-Verwaltung für responslose Setups

Befolgen Sie bei Helix-5- und Repoless-Architekturen die folgenden Richtlinien:

### Beim Erstellen neuer Sites

1. **Identifizieren der Site-Domain** (z. B. `main--newsite--adobe.aem.live`)
2. **Aktualisieren der CORS-**, um die neue Domain einzuschließen
3. **Referrer-Filter aktualisieren** um die neue Domain in `allow.hosts` einzuschließen
4. **Formularübermittlung testen** von der neuen Website
5. **Dokumentieren der neuen Domain** in Ihrer Site-Registrierung

### Domain-Namensmuster

- Standardmuster: `{branch}--{site}--{owner}.aem.live`
- Jede Site erhält eine eindeutige Domain, selbst wenn sie dasselbe Repository teilt
- Es können sowohl `.aem.live`- als auch `.aem.page`-Domains verwendet werden

### Konfigurationsverwaltung

- Verwenden Sie bestimmte Domäneneinträge in `allow.hosts`, um die Sicherheit zu erhöhen.
- Ergänzung mit Regex-Mustern für eine breitere Abdeckung
- Regelmäßige Prüfung und Aktualisierung von Zulassungslisten, wenn Websites hinzugefügt oder entfernt werden

## Zusätzliche Ressourcen

- [Konfiguration des Referrer-Filters mit AEM Headless](/help/headless/deployment/referrer-filter.md)
- [CORS-Konfigurationshandbuch](https://experienceleague.adobe.com/de/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors)
- [Verstehen von Cross-Origin Resource Sharing](https://experienceleague.adobe.com/de/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing)
- [Dokumentation zu Edge Delivery Services Forms](/help/edge/docs/forms/universal-editor/publish-forms.md)

## Verwandte Themen

- [Konfigurieren von Übermittlungsaktionen](/help/forms/configuring-submit-actions.md)
- [Forms Submission Service](/help/forms/forms-submission-service.md)
- [Überblick über Edge Delivery Services](/help/edge/overview.md)


**Benötigen Sie zusätzliche Hilfe?** Wenn nach Befolgen dieser Schritte weiterhin Probleme auftreten, wenden Sie sich an den Adobe-Kunden-Support unter:

- Spezifische Fehlermeldungen
- Details zur AEM Cloud Service-Umgebung
- **Alle Edge Delivery Services-Site-Domains** auf die Zugriff auf die Formularübermittlung benötigt wird
- Relevante Protokolleinträge zum Zeitpunkt des Fehlers

**Benötigen Sie zusätzliche Hilfe?** Wenn nach Befolgen dieser Schritte weiterhin Probleme auftreten, wenden Sie sich an den Adobe-Kunden-Support unter:

- Spezifische Fehlermeldungen
- Details zur AEM Cloud Service-Umgebung
- Edge Delivery Services-Domäneninformationen
- Relevante Protokolleinträge zum Zeitpunkt des Fehlers
