---
title: Forms Experience Builder - Handbuch zur Fehlerbehebung
description: Umfassendes Handbuch zur Fehlerbehebung in Forms Experience Builder, das allgemeine Probleme, Lösungen und Debugtechniken zur Formularerstellung und -verwaltung behandelt.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: 9996bc602ae6169dd1aade622d5dbc5b1addeb54
workflow-type: tm+mt
source-wordcount: '2282'
ht-degree: 0%

---


# Forms Experience Builder - Handbuch zur Fehlerbehebung

>[!NOTE]
>
> Der Forms Experience Builder ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie eine E-Mail von Ihrer Geschäftsadresse an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Dieses Handbuch zur Fehlerbehebung wird derzeit für das Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Probleme, Lösungen und Debugtechniken können sich ändern, wenn Forms Experience Builder während des Early-Adopter-Programms weiterentwickelt wird.

Dieses umfassende Handbuch zur Fehlerbehebung hilft Ihnen bei der Identifizierung, Diagnose und Lösung häufiger Probleme bei der Arbeit mit Forms Experience Builder. Das Handbuch ist nach Problemkategorien mit schnellen Lösungen und detaillierten Lösungen geordnet.

## Kurzanleitung - Häufige Probleme

| Problem | Schnellkorrektur |
|-------|-----------|
| **Schnittstelle wird nicht geladen** | Browser aktualisieren, Internetverbindung prüfen, Frühzugriffsberechtigungen prüfen |
| **Befehle funktionieren nicht** | Versuchen Sie es `/help` oder verwenden Sie eine natürliche Sprache anstelle von Schrägstrichen |
| **@fieldName nicht erkannt** | Schreibweise überprüfen, zuerst sicherstellen, dass das Feld vorhanden ist, Feldnamenssyntax überprüfen |
| **Datei-Upload schlägt fehl** | Verwenden Sie PDF/JPG/PNG unter 10 MB, um die Kompatibilität der Dateiformate zu überprüfen |
| **Formular sieht falsch aus** | Genauer gesagt: „Mobilgerät benutzerfreundlich machen“ anstelle von „Layout korrigieren“ |
| **Integration schlägt fehl** | Überprüfen der API-Anmeldeinformationen und -Berechtigungen, Überprüfen der Endpunktverfügbarkeit |
| **Formular wird nicht gesendet** | Konfiguration der Übermittlungsaktion und Validierungsregeln überprüfen |
| **Validierungsfehler werden nicht angezeigt** | Überprüfen der Feldüberprüfungseinstellungen und der Platzierung von Fehlermeldungen |
| **Layoutprobleme für Mobilgeräte** | Überprüfen der responsiven Designeinstellungen und der Feldgröße |
| **Felder werden nicht angezeigt** | Überprüfen von bedingten Logik- und Sichtbarkeitsregeln |
| **Fehler beim Importieren** | Überprüfen der Dateiformatkompatibilität und der Größenbeschränkungen |
| **Leistungsprobleme** | Optimieren Sie die Anzahl der Felder und entfernen Sie unnötige Validierungen |
| **Probleme mit der Barrierefreiheit** | Feldbezeichnungen, ARIA-Attribute und Registerkartenreihenfolge überprüfen |

**Brauchen Sie noch Hilfe?** Geben Sie `/help` ein, gefolgt von Ihrer spezifischen Frage, oder wenden Sie sich an Ihren Systemadministrator, um technische Unterstützung zu erhalten.

## Zugriffs- und Authentifizierungsanfragen

### Zugriff auf Forms Experience Builder nicht möglich

**Symptome:**

- Forms Experience Builder-Benutzeroberfläche nicht sichtbar
- Fehlermeldungen des Typs „Zugriff verweigert“ oder ähnlich
- Fehlendes Forms Experience Builder-Symbol im Editor

**Lösungen:**

1. **Early Access Program Enrollment überprüfen**
   - Bestätigen Sie, dass Sie für das Early-Adopter-Programm zugelassen wurden
   - Vergewissern Sie sich, dass Ihre Anforderung von Ihrer offiziellen E-Mail gesendet wurde.
   - `aem-forms-ea@adobe.com` kontaktieren, wenn der Zugriff noch aussteht

2. **Überprüfen Sie die Einrichtung der Umgebung**
   - Überprüfen, ob AEM Forms für Ihre Umgebung aktiviert ist
   - Stellen Sie sicher, dass Sie einen unterstützten Browser verwenden (Chrome, Firefox, Safari, Edge)
   - Browser-Cache und Cookies löschen
   - Deaktivieren von Browser-Erweiterungen, die zu Störungen führen könnten

3. **Überprüfen von Benutzerberechtigungen**
   - Vergewissern Sie sich, dass Sie über geeignete Benutzerrollen und Berechtigungen verfügen
   - Fragen Sie Ihren Systemadministrator nach Zugriffsrechten
   - Überprüfen Sie, ob Sie mit dem richtigen Konto angemeldet sind

### Probleme beim Laden der Benutzeroberfläche

**Symptome:**

- Leere oder teilweise geladene Schnittstelle
- Drehen von Ladeindikatoren, die nicht abgeschlossen werden
- JavaScript-Fehler in der Browser-Konsole

**Lösungen:**

1. **Fehlerbehebung beim Browser**
   - Seite aktualisieren (Strg+F5 oder Befehl+Umschalt+R)
   - Verwenden Sie einen anderen Browser oder einen anderen Inkognito-/privaten Modus.
   - Browser-Updates suchen und installieren, falls verfügbar
   - Anzeigenblocker und Datenschutzerweiterungen vorübergehend deaktivieren

2. **Netzwerkkonnektivität**
   - Überprüfen der stabilen Internetverbindung
   - Überprüfen, ob die Unternehmens-Firewall erforderliche Domains blockiert
   - Testen Sie nach Möglichkeit mit einer anderen Netzwerkverbindung
   - Wenden Sie sich bei Problemen mit der Netzwerkkonfiguration an den IT-Support

3. **Cache- und Speicherprobleme**
   - Löschen des Browser-Cache und des lokalen Speichers
   - Browser-Einstellungen auf Standard zurücksetzen
   - Überprüfen des verfügbaren Speicherplatzes auf dem Gerät
   - Versuchen Sie, von einem anderen Gerät aus zuzugreifen

## Probleme mit Befehlen und Interaktionen

### Schrägstrichbefehle funktionieren nicht

**Symptome:**

- `/create-form` oder andere Schrägstrichbefehle nicht erkannt
- Keine Vorschläge zur automatischen Vervollständigung angezeigt
- Befehle führen zu Fehlermeldungen

**Lösungen:**

1. **Überprüfung der Befehlssyntax**
   - Sicherstellen, dass das Befehlsformat korrekt ist: `/command-name description`
   - Auf Tippfehler in Befehlsnamen prüfen
   - Alternative: „Kontaktformular erstellen“
   - `/help` versuchen, die Befehlsverfügbarkeit zu überprüfen

2. **Kontextspezifische Befehle**
   - Stellen Sie sicher, dass Sie sich im richtigen Editor-Kontext befinden (universeller Editor vs. adaptiver Forms-Editor)
   - Einige Befehle funktionieren nur in bestimmten Umgebungen
   - Überprüfen der Befehlsreferenz auf Kontextanforderungen

3. **Alternative Ansätze**
   - Natürliche Sprache anstelle von Schrägstrichen verwenden
   - Unterteilen komplexer Befehle in kleinere, einfachere Anfragen
   - Versuchen Sie, ein Formular schrittweise anstelle eines einzelnen komplexen Befehls zu erstellen

### Feldverweise funktionieren nicht

**Symptome:**

- `@fieldName` Verweise nicht erkannt
- Fehlermeldungen zu unbekannten Feldern
- Feldänderungen werden nicht korrekt angewendet

**Lösungen:**

1. **Feldnamenüberprüfung**
   - Überprüfen der exakten Schreibweise von Feldnamen (unter Berücksichtigung von Groß- und Kleinschreibung)
   - Stellen Sie sicher, dass das Feld vorhanden ist, bevor darauf verwiesen wird
   - Verwenden Sie den genauen Feldnamen wie erstellt, nicht die Anzeigebezeichnung
   - Konventionen zur Feldbenennung überprüfen (CamelCase, Snake_Case usw.)

2. **Feldverweissyntax**
   - Verwenden der richtigen `@fieldName` ohne Leerzeichen
   - Vermeiden von Sonderzeichen in Feldverweisen
   - Auf unsichtbare Zeichen oder Formatierungsprobleme prüfen
   - Versuchen Sie, den Feldverweis manuell neu zu erstellen

3. **Debuggen von Feldverweisen**
   - Auflisten aller vorhandenen Felder als Erstes: „Alle aktuellen Formularfelder anzeigen“
   - Erstellen Sie Felder, bevor Sie in Regeln darauf verweisen
   - Verwenden einfacher Feldnamen ohne komplexe Zeichen
   - Testfeld verweist jeweils auf einen

## Probleme bei der Formularerstellung und dem Design

### Formular wird nicht erwartungsgemäß erstellt

**Symptome:**

- Im generierten Formular fehlen angeforderte Felder
- Falsche Feldtypen oder Layouts
- Formularstruktur stimmt nicht mit Beschreibung überein

**Lösungen:**

1. **Verbessern der Eingabeaufforderungsspezifität**
   - Ausführlichere Beschreibungen in Formularen
   - Spezifizieren Sie genaue Feldtypen und Validierungsanforderungen
   - Layout-Voreinstellungen und Anforderungen an das Benutzererlebnis einschließen
   - Aufteilen komplexer Formulare in kleinere, inkrementelle Anfragen

2. **Iterativer Entwicklungsansatz**
   - Beginn mit der allgemeinen Formularstruktur
   - Inkrementelles Hinzufügen von Feldern und Funktionen
   - Testen Sie jede Ergänzung, bevor Sie fortfahren
   - Verfeinern durch Konversation anstelle einer einzelnen komplexen Anfrage

3. **Beispiel für bessere Eingabeaufforderungen**

   Anstelle von:

       Erstellen eines Formulars für Kunden
   
   Verwenden Sie:

       Erstellen Sie ein Kundenkontaktformular mit:
       - Vollständiger Name (Pflichtfeld)
       - E-Mail-Adresse (bei Validierung erforderlich)
        - Telefonnummer (optional, formatiert)
       - Nachricht (TextArea erforderlich, max. 500 Zeichen)
       - An E-Mail-Benachrichtigung senden
   

### Probleme mit Layout und Stil

**Symptome:**

- Formular erscheint auf Mobilgeräten fehlerhaft
- Inkonsistente Abstände oder Ausrichtung
- Felder werden nicht korrekt angezeigt
- Schlechte visuelle Hierarchie

**Lösungen:**

1. **Reaktionsfähigkeit auf Mobilgeräten**
   - Mobilgerätespezifische Optimierungen anfordern: „Dieses Formular mobilfreundlich gestalten“
   - Festlegen von responsiven Design-Anforderungen
   - Testen auf tatsächlichen Mobilgeräten
   - Verwenden von einspaltigen Layouts für Mobilgeräte

2. **Layout-Verbesserungen**
   - Seien Sie spezifisch bei Layout-Anforderungen: „Adressfelder in zwei Spalten anordnen“
   - Spezifischen Stil anfordern: „Verwenden Sie professionelle Farben und saubere Typografie“
   - Abstands- und Ausrichtungsanforderungen festlegen
   - Nachfragen zur Einhaltung von Barrierefreiheitsvorschriften

3. **Markenkonsistenz**
   - Vorbereiten von Markenrichtlinien vor der Formularerstellung
   - Bestimmte Farb-Codes und Schriftarten in Anfragen einschließen
   - Verwenden von konsistenten Stilen in allen Formularen
   - Erstellen von Markenvorlagen zur Wiederverwendung

### Bedingte Logikprobleme

**Symptome:**

- Regeln werden nicht erwartungsgemäß ausgelöst
- Falsch angezeigte/ausgeblendete Felder
- Validierungslogik funktioniert nicht
- Fehlschlagen komplexer Geschäftsregeln

**Lösungen:**

1. **Regelvereinfachung**
   - Aufspaltung komplexer Regeln in kleinere, einfachere Bedingungen
   - Jede Regel einzeln testen, bevor sie kombiniert wird
   - Verwenden Sie klare, spezifische Bedingungen: &quot;@spouseInfo anzeigen, wenn @maritalStatus gleich „Verheiratet“ ist“.
   - Verschachtelte oder übermäßig komplexe Logik zunächst vermeiden

2. **Regeltests und Debugging**
   - Testen aller möglichen Benutzerpfade und Szenarien
   - Überprüfen von Feldnamen und Werten in Bedingungen
   - Prüfen der Groß-/Kleinschreibung in Regelbedingungen
   - Debug-Modus verwenden, um die Regelausführung zu verfolgen

3. **Business-Logik-Implementierung**
   - Dokumentieren der Geschäftsanforderungen vor der Implementierung
   - Inkrementelles Implementieren von Regeln und Testen der einzelnen Schritte
   - Eindeutiges Benutzerfeedback geben, wenn Regeln ausgelöst werden
   - Handhabung von Edge-Fällen und Ausnahmeszenarien

## Probleme beim Import und bei der Konvertierung von Dateien

### PDF-Importfehler

**Symptome:**

- PDF-Dateien werden nicht hochgeladen oder verarbeitet
- Konvertierte Formulare ohne Felder oder Inhalt
- Fehlermeldungen während der PDF-Konvertierung
- Schlechte Felderkennung durch PDF

**Lösungen:**

1. **Dateiformat und -größe**
   - Stellen Sie sicher, dass PDF-Dateien unter 10 MB groß sind
   - Verwenden Sie hochwertige, textbasierte PDFs (keine gescannten Bilder).
   - Überprüfen Sie, ob PDF kennwortgeschützt oder verschlüsselt ist
   - Konvertieren von PDF in das Bildformat, wenn die Textextraktion fehlschlägt

2. **PDF-Qualitätsoptimierung**
   - Verwenden von PDFs mit klaren, klar definierten Formularfeldern
   - Sicherstellen von gutem Kontrast und lesbarem Text
   - Vermeiden komplexer Layouts oder überlappender Elemente
   - Zusätzlichen Kontext in der Konvertierungsanfrage angeben

3. **Konversionsverbesserung**
   - Beschreiben Sie die erwartete Formularstruktur im Detail.
   - Angeben von Feldtypen und Validierungsanforderungen
   - Spezifische Verbesserungen anfordern: „Reaktionsfähigkeit und Validierung für Mobilgeräte hinzufügen“
   - Manuelles Überprüfen und Verfeinern konvertierter Formulare

### Konvertierungsprobleme von Bildern und Screenshots

**Symptome:**

- Schlechte Felderkennung durch Bilder
- Falsche Feldtypen oder Layouts
- Fehlende Formularelemente
- Konvertierungsfehler oder Zeitüberschreitungen

**Lösungen:**

1. **Bildqualitätsanforderungen**
   - Verwenden Sie hochauflösende Bilder (mindestens 300 DPI)
   - Gute Beleuchtung und Kontrast
   - Vermeiden von Schatten, Blendung oder Verzerrungen
   - Bilder beschneiden, damit sie nur auf den Formularinhalt ausgerichtet sind

2. **Optimale Bildformate**
   - Verwenden von PNG- oder JPG-Formaten für optimale Ergebnisse
   - GIF oder komprimierte Bilder von niedriger Qualität vermeiden
   - Sicherstellen, dass der Text im Bild gut lesbar ist
   - Versuchen Sie bei Bedarf verschiedene Bildausrichtungen

3. **Konversionsanleitung**
   - Angeben detaillierter Beschreibungen der Formularstruktur
   - Geben Sie Feldtypen und Anforderungen explizit an
   - Spezifische Verbesserungen während der Konvertierung anfordern
   - Seien Sie darauf vorbereitet, nach der Konvertierung manuelle Anpassungen vorzunehmen

## Probleme bei Integration und Übermittlung

### Fehlgeschlagene Formularübermittlung

**Symptome:**

- Forms wird nicht erfolgreich gesendet
- Fehlermeldungen während der Übermittlung
- Daten erreichen nicht die beabsichtigten Ziele
- Zeitüberschreitungsfehler bei Übermittlung

**Lösungen:**

1. **Konfiguration der Übermittlungsaktion**
   - Überprüfen, ob die Sendeaktion ordnungsgemäß konfiguriert ist
   - API-Endpunkte und Authentifizierungsdaten überprüfen
   - Testen Sie zunächst mit einfacher E-Mail-Übermittlung
   - Validieren von Datenformatanforderungen

2. **Netzwerk und Konnektivität**
   - Überprüfen der Internetverbindung und Netzwerkstabilität
   - Überprüfen der Firewall-Einstellungen, um Formularübermittlungen zuzulassen
   - Testen von verschiedenen Netzwerkverbindungen
   - Überprüfen auf Unternehmens-Proxy- oder Sicherheitsbeschränkungen

3. **Probleme bei der Datenvalidierung**
   - Sicherstellen, dass alle erforderlichen Felder ausgefüllt sind
   - Überprüfen, ob Datenformate den API-Anforderungen entsprechen
   - Auf Sonderzeichen oder Kodierungsprobleme prüfen
   - Zuerst mit minimalem Datensatz testen

### Probleme bei der API-Integration

**Symptome:**

- REST-API-Endpunkte reagieren nicht
- Authentifizierungsfehler
- Datenformat stimmt nicht überein
- Integrations-Timeouts oder -Fehler

**Lösungen:**

1. **API-Konfigurationsüberprüfung**
   - Überprüfen, ob API-Endpunkt-URLs korrekt und zugänglich sind
   - Authentifizierungsdaten und -berechtigungen überprüfen
   - Testen Sie API-Endpunkte unabhängig voneinander mithilfe von Tools wie Postman
   - Überprüfen Sie, ob die API das richtige Datenformat akzeptiert (JSON, XML usw.)

2. **Probleme bei der Datenzuordnung**
   - Sicherstellen, dass Formularfeldnamen mit API-Parameteranforderungen übereinstimmen
   - Auf erforderliche Felder prüfen, die möglicherweise fehlen
   - Überprüfen der Datentypkompatibilität (Zeichenfolgen, Zahlen, Daten)
   - Testen mit Beispieldaten, um Zuordnungsprobleme zu identifizieren

3. **Fehlerbehandlung und Debugging**
   - Aktivieren der detaillierten Fehlerprotokollierung für API-Aufrufe
   - Überprüfen von API-Antwort-Codes und Fehlermeldungen
   - Implementieren von Wiederholungslogik für temporäre Fehler
   - Fallback-Optionen für Benutzende bereitstellen, wenn die API fehlschlägt

### E-Mail-Integrationsprobleme

**Symptome:**

- Bestätigungs-E-Mails werden nicht gesendet
- E-Mails an Spam-Ordner
- Falsche E-Mail-Formatierung
- Fehlende Formulardaten in E-Mails

**Lösungen:**

1. **E-Mail-Konfiguration**
   - Überprüfen, ob E-Mail-Adressen korrekt formatiert sind
   - SMTP-Einstellungen und -Authentifizierung überprüfen
   - Zuerst mit einfachen E-Mail-Adressen testen
   - Überprüfen von E-Mail-Server-Berechtigungen und -Kontingenten

2. **Optimierung des E-Mail-Versands**
   - Verwenden von korrekten E-Mail-Kopfzeilen und Absenderinformationen
   - Vermeiden Sie Spam-Trigger-Wörter in den Betreffzeilen
   - Einschließen von korrekten Abmeldemechanismen
   - Testen des E-Mail-Versands an verschiedene Anbieter

3. **Inhalt und Formatierung**
   - Überprüfen, ob Formulardaten in E-Mails ordnungsgemäß formatiert sind
   - Auf Sonderzeichen oder Kodierungsprobleme prüfen
   - Testen von E-Mail-Vorlagen mit verschiedenen Datenkombinationen
   - Sicherstellen, dass E-Mail-Inhalte barrierefrei und lesbar sind

## Leistungs- und Ladeprobleme

### Langsames Laden von Formularen

**Symptome:**

- Das Laden von Forms dauert zu Beginn sehr lange
- Trägheit bei Benutzerinteraktionen
- Zeitüberschreitungen bei Formularvorgängen
- Schlechte Leistung auf Mobilgeräten

**Lösungen:**

1. **Formularoptimierung**
   - Anzahl der Felder und Komplexität reduzieren
   - Implementieren von verzögertem Laden für nicht kritische Abschnitte
   - Optimieren von Bildern und Assets für die Web-Bereitstellung
   - Entfernen unnötiger Validierungsregeln oder -logiken

2. **Browser- und Geräteoptimierung**
   - Browser-Cache und temporäre Dateien löschen
   - Schließen unnötiger Browser-Registerkarten und Anwendungen
   - Überprüfen des verfügbaren Gerätespeichers und -speichers
   - Verwenden verschiedener Browser zum Leistungsvergleich

3. **Netzwerkoptimierung**
   - Testen mit verschiedenen Netzwerkverbindungen
   - Prüfen auf Netzwerküberlastung oder Bandbreitenbeschränkungen
   - Verwenden Sie nach Möglichkeit Kabelverbindungen anstelle von WLAN.
   - Wenden Sie sich bei Problemen mit der Netzwerkleistung an den IT-Support

### Probleme mit der Validierungsleistung

**Symptome:**

- Langsame Validierungsantworten
- Verzögerte Anzeige von Fehlermeldungen
- Einfrieren von Formularen während der Validierung
- Zeitüberschreitungsfehler bei der Feldüberprüfung

**Lösungen:**

1. **Validierungsoptimierung**
   - Häufigkeit der Echtzeit-Validierung reduzieren
   - Implementieren des Bounces für Validierungsaufrufe
   - Vereinfachung komplexer Validierungsregeln
   - Verwenden Sie nach Möglichkeit Client-seitige Validierung

2. **Regelvereinfachung**
   - Komplexe Validierung in kleinere Regeln aufteilen
   - Entfernen von unnötigen feldübergreifenden Validierungen
   - Bedingte Logik für Leistung optimieren
   - Cache-Validierungsergebnisse, sofern zutreffend

3. **Verbesserungen des Benutzererlebnisses**
   - Sofortiges Feedback für einfache Validierungen geben
   - Verwenden Sie für komplexe Regeln progressive Validierung anstelle von Echtzeit
   - Ladeindikatoren während Validierungsprozessen anzeigen
   - Benutzern erlauben, während der Validierungsprozesse im Hintergrund fortzufahren

## Erweiterte Fehlerbehebung

### Debug-Modus und Diagnose

**Debug-Informationen aktivieren**

Verwenden Sie diese Eingabeaufforderungen, um detailliertere Informationen zu Formularproblemen zu erhalten:

    Debug-Modus aktivieren, um Probleme bei der Formularübermittlung und Feldüberprüfung zu identifizieren
    
    Formularfehler analysieren: Validierungsregeln, API-Antworten und Benutzereingabemuster überprüfen
    
    Detaillierte Informationen zur Formularstruktur und Feldkonfiguration anzeigen

### Techniken zur Fehleranalyse

**Systematischer Debugging-Ansatz**

1. **Isolieren Sie das Problem**
   - Testen mit minimaler Formularkonfiguration
   - Komplexe Funktionen vorübergehend entfernen
   - Einzelne Komponenten separat testen
   - Ausschlussverfahren zur Ermittlung der Grundursache verwenden

2. **Sammeln von Diagnoseinformationen**
   - Überprüfen der Browser-Konsole auf JavaScript-Fehler
   - Prüfen von Netzwerkanfragen und -antworten
   - Dokumentieren der genauen Schritte zur Reproduktion des Problems
   - Erfassen von Screenshots und Fehlermeldungen

3. **Testumgebungsvariablen**
   - Verwenden verschiedener Browser und Geräte
   - Testen mit verschiedenen Benutzerkonten und Berechtigungen
   - Überprüfen in verschiedenen Netzwerkumgebungen
   - Vergleich mit Arbeitsformularen oder Konfigurationen

### Protokollanalyse und -überwachung

**Debugging der Browser-Konsole**

1. Browser-Entwickler-Tools öffnen (F12)
2. Registerkarte „Konsole“ auf JavaScript-Fehler überprüfen
3. Registerkarte „Netzwerk“ auf fehlgeschlagene Anfragen überprüfen
4. Registerkarte „Leistung überwachen“ für langsame Vorgänge

**Häufige Fehlermuster**

- **CORS-**: Probleme mit ursprungsübergreifenden Anfragen bei API-Integrationen
- **Authentifizierungsfehler**: Ungültige Anmeldeinformationen oder abgelaufene Token
- **Validierungsfehler**: Konflikt bei Regeln für die Feldvalidierung oder Syntaxfehler
- **Netzwerk-Timeouts**: Langsame oder unzuverlässige Netzwerkverbindungen

## Abrufen zusätzlicher Hilfe

### Self-Service-Ressourcen

**Integriertes Hilfesystem**

- Verwenden Sie `/help` Befehl gefolgt von bestimmten Fragen.
- Zugriff auf die kontextuelle Hilfe in der Benutzeroberfläche von Forms Experience Builder
- Prüfen Sie die Fehlermeldungen sorgfältig auf spezifische Anleitungen.
- Lesen Sie die Informationen zu den ersten Schritten mit Forms Experience Builder [&#128279;](forms-ai-assistant-getting-started.md)

**Dokumentationsressourcen**

- [Forms Experience Builder-Eingabeaufforderungsbibliothek](ai-assistant-prompt-library.md)
- [Best Practices für Forms Experience Builder](aem-forms-ai-assistant-best-practices.md)
- [Dokumentation zu AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html?lang=de)

### Eskalation und Support

**Wann sollte ich den Support kontaktieren**

- Probleme nach dem Ausprobieren dokumentierter Lösungen bestehen
- Systemweite Probleme, die mehrere Benutzer betreffen
- Bedenken hinsichtlich der Sicherheit oder Datenintegrität
- Integrationsprobleme, die eine Konfiguration auf Systemebene erfordern

**Zu liefernde Informationen**

- Detaillierte Beschreibung des Problems und Schritte zur Reproduktion
- Screenshots oder Bildschirmaufzeichnungen des Problems
- Browser- und Systeminformationen
- Fehlermeldungen und Konsolenprotokolle
- Details zur Formularkonfiguration und -integration

**Kontaktmethoden**

- Systemadministrator: Für Probleme mit Umgebung und Zugriff
- Technischer Support: Für komplexe Integrations- und Konfigurationsprobleme
- EARLY ACCESS-PROGRAMM: `aem-forms-ea@adobe.com` für programmspezifische Fragen

### Community und Wissensaustausch

**Best Practices für die Problembehebung**

- Dokumentenlösungen als Referenz für die Zukunft
- Austausch erfolgreicher Ansätze zur Fehlerbehebung mit Team-Mitgliedern
- Beitrag zur organisatorischen Wissensdatenbank
- Teilnehmen an Benutzergruppen und Foren

**Kontinuierliche Verbesserung**

- Regelmäßige Überprüfung häufiger Probleme und Lösungen
- Aktualisierung der Fehlerbehebungsverfahren auf der Grundlage neuer Erkenntnisse
- Schulungen und Wissensaustausch
- Feedback an das Produkt-Team zur Verbesserung der Funktionen

Dieses Handbuch zur Fehlerbehebung wird laufend auf der Grundlage von Benutzer-Feedback und neuen Forms Experience Builder-Funktionen aktualisiert. Die neuesten Informationen und zusätzlichen Ressourcen finden Sie in der Dokumentation zu [AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html?lang=de).
