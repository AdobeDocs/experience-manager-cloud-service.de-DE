---
title: Forms Experience Builder – Handbuch zur Fehlerbehebung
description: Umfassendes Handbuch zur Fehlerbehebung in Forms Experience Builder, das allgemeine Probleme, Lösungen und Debugging-Techniken zur Formularerstellung und -verwaltung behandelt.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
exl-id: 6a7810fd-2860-410b-867d-8d29afd5297d
source-git-commit: fe34b44d02c308e7d18a08dd05f21abc67bd0cb2
workflow-type: tm+mt
source-wordcount: '2282'
ht-degree: 100%

---


# Forms Experience Builder – Handbuch zur Fehlerbehebung

>[!NOTE]
>
> Forms Experience Builder ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Dieses Handbuch zur Problemlösung wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Probleme, Lösungen und Debugging-Techniken können sich ändern, wenn Forms Experience Builder während des Early-Adopter-Programms weiterentwickelt wird.

Dieses umfassende Handbuch zur Fehlerbehebung hilft Ihnen bei der Identifizierung, Diagnose und Lösung häufiger Probleme bei der Arbeit mit Forms Experience Builder. Das Handbuch ist nach Problemkategorien mit Schnellkorrekturen und detaillierten Lösungen geordnet.

## Kurzanleitung – Häufige Probleme

| Problem | Schnellkorrektur |
|-------|-----------|
| **Oberfläche wird nicht geladen** | Browser aktualisieren, Internet-Verbindung prüfen, Early-Access-Berechtigungen prüfen |
| **Befehle funktionieren nicht** | Befehl `/help` versuchen oder natürliche Sprache statt Schrägstrichbefehlen verwenden |
| **@fieldName nicht erkannt** | Rechtschreibung prüfen, zuerst sicherstellen, dass das Feld vorhanden ist, Syntax des Feldnamens prüfen |
| **Datei-Upload schlägt fehl** | PDF/JPG/PNG mit weniger als 10 MB verwenden, Kompatibilität des Dateiformats prüfen |
| **Formular sieht falsch aus** | Spezifischer werden: „Mach es mobilfreundlich“, statt „Repariere das Layout“ |
| **Integration schlägt fehl** | API-Anmeldeinformationen und -Berechtigungen prüfen, Verfügbarkeit des Endpunkts prüfen |
| **Formular wird nicht übermittelt** | Konfiguration der Übermittlungsaktion und Validierungsregeln prüfen |
| **Validierungsfehler werden nicht angezeigt** | Einstellungen der Feldvalidierung und Platzierung von Fehlermeldungen prüfen |
| **Layout-Probleme bei Mobilgeräten** | Responsive Design-Einstellungen und Feldgröße prüfen |
| **Felder werden nicht angezeigt** | Bedingte Logik und Sichtbarkeitsregeln prüfen |
| **Fehler beim Import** | Kompatibilität des Dateiformats und Größenbeschränkungen prüfen |
| **Leistungsprobleme** | Anzahl der Felder optimieren und unnötige Validierungen entfernen |
| **Probleme mit der Barrierefreiheit** | Feld-Label, ARIA-Attribute und Registerkartenreihenfolge prüfen |

**Brauchen Sie noch Hilfe?** Geben Sie `/help` ein, gefolgt von Ihrer spezifischen Frage, oder wenden Sie sich an Ihren Systemadmin, um technische Unterstützung zu erhalten.

## Zugriffs- und Authentifizierungsprobleme

### Zugriff auf Forms Experience Builder nicht möglich

**Symptome:**

- Forms Experience Builder-Benutzeroberfläche nicht sichtbar
- Fehlermeldungen des Typs „Zugriff verweigert“ oder ähnlich
- Fehlendes Forms Experience Builder-Symbol im Editor

**Lösungen:**

1. **Early-Access-Programmregistrierung prüfen**
   - Prüfen, ob Ihre Teilnahme beim Early-Adopter-Programm genehmigt wurde
   - Sicherstellen, dass Ihre Anfrage von Ihrer offiziellen geschäftlichen E-Mail-Adresse gesendet wurde
   - `aem-forms-ea@adobe.com` kontaktieren, wenn der Zugriff noch aussteht

2. **Setup der Umgebung prüfen**
   - Prüfen, ob AEM Forms für Ihre Umgebung aktiviert ist
   - Sicherstellen, dass Sie einen unterstützten Browser verwenden (Chrome, Firefox, Safari, Edge)
   - Browsercache leeren und Cookies löschen
   - Browser-Erweiterungen deaktivieren, die zu Störungen führen könnten

3. **Benutzerberechtigungen prüfen**
   - Sicherstellen, dass Sie über geeignete Benutzerrollen und Berechtigungen verfügen
   - Beim Systemadmin nach Zugriffsrechten fragen
   - Sicherstellen, dass Sie mit dem richtigen Konto angemeldet sind

### Probleme beim Laden der Benutzeroberfläche

**Symptome:**

- Leere oder unvollständig geladene Oberfläche
- Rotierende Ladeanzeigen, die nicht abgeschlossen werden
- JavaScript-Fehler in der Browser-Konsole

**Lösungen:**

1. **Fehlerbehebung im Browser**
   - Seite aktualisieren (Strg+F5 oder Befehl+Umschalt+R)
   - Anderen Browser oder Inkognito-/privaten Modus versuchen
   - Browser-Updates suchen und installieren, falls verfügbar
   - Anzeigenblocker und Datenschutzerweiterungen vorübergehend deaktivieren

2. **Netzwerkverbindung**
   - Stabile Internetverbindung sicherstelln
   - Prüfen, ob die Unternehmens-Firewall erforderliche Domains blockiert
   - Nach Möglichkeit mit einer anderen Netzwerkverbindung testen
   - Bei Problemen mit der Netzwerkkonfiguration an den IT-Support wenden

3. **Cache- und Speicherprobleme**
   - Browsercache und lokalen Speicher löschen
   - Browser-Einstellungen auf Standard zurücksetzen
   - Verfügbaren Speicherplatz auf dem Gerät prüfen
   - Zugriff von einem anderen Gerät aus versuchen

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
   - Alternative in natürlicher Sprache verwenden: „Erstelle ein Kontaktformular“
   - `/help` eingeben, um die Befehlsverfügbarkeit zu prüfen

2. **Kontextspezifische Befehle**
   - Sicherstellen, dass Sie sich im richtigen Editor-Kontext befinden (universeller Editor vs. Editor für adaptive Formulare)
   - Einige Befehle funktionieren nur in bestimmten Umgebungen
   - Befehlsreferenz auf Kontextanforderungen prüfen

3. **Alternative Ansätze**
   - Natürliche Sprache anstelle von Schrägstrichbefehlen verwenden
   - Komplexe Befehle in kleinere, einfachere Anfragen unterteilen
   - Formular Schritt für Schritt erstellen, statt mit einem einzigen komplexen Befehl

### Feldverweise funktionieren nicht

**Symptome:**

- `@fieldName`-Verweise nicht erkannt
- Fehlermeldungen zu unbekannten Feldern
- Feldänderungen werden nicht korrekt angewendet

**Lösungen:**

1. **Überprüfung von Feldnamen**
   - Exakte Schreibweise von Feldnamen prüfen (unter Berücksichtigung von Groß- und Kleinschreibung)
   - Sicherstellen, dass das Feld vorhanden ist, bevor darauf verwiesen wird
   - Den exakten Feldnamen wie erstellt verwenden, nicht das Anzeige-Label
   - Konventionen zur Feldbenennung prüfen (camelCase, snake_case usw.)

2. **Syntax von Feldverweisen**
   - Korrekte `@fieldName`-Syntax ohne Leerzeichen verwenden
   - Sonderzeichen in Feldverweisen vermeiden
   - Auf unsichtbare Zeichen oder Formatierungsprobleme prüfen
   - Feldverweis manuell neu erstellen

3. **Debugging von Feldverweisen**
   - Zunächst alle vorhandenen Felder auflisten: „Zeige alle aktuellen Formularfelder an“
   - Felder erstellen, bevor in Regeln darauf verwiesen wird
   - Einfache Feldnamen ohne komplexe Zeichen erstellen
   - Feldverweise einzeln testen

## Probleme bei der Formularerstellung und dem Design

### Formular wird nicht erwartungsgemäß erstellt

**Symptome:**

- Im generierten Formular fehlen angeforderte Felder
- Falsche Feldtypen oder Layouts
- Formularstruktur stimmt nicht mit Beschreibung überein

**Lösungen:**

1. **Verbessern der Prompt-Spezifität**
   - Formularbeschreibungen detaillierter formulieren
   - Exakte Feldtypen und Validierungsanforderungen angeben
   - Layout-Voreinstellungen und Anforderungen an das Benutzererlebnis einschließen
   - Komplexe Formulare in kleinere, inkrementelle Anforderungen unterteilen

2. **Iterativer Entwicklungsansatz**
   - Mit der allgemeinen Formularstruktur beginnen
   - Felder und Funktionen inkrementell hinzufügen
   - Jede Ergänzung vor dem Fortfahren testen
   - Mit Dialog optimieren, statt eine einzelne komplexe Anfrage zu verwenden

3. **Beispiel für bessere Prompts**

   Anstelle von:

       Erstelle ein Formular für Kundschaft
   
   Verwenden Sie:

       Erstelle ein Kundenkontaktformular mit:
       – Vollständiger Name (Pflichtfeld)
       – E-Mail-Adresse (bei Validierung erforderlich)
       – Telefonnummer (optional, formatiert)
       – Nachricht (Textfeld erforderlich, max. 500 Zeichen)
       – An E-Mail-Benachrichtigung übermitteln
   
### Probleme mit Layout und Stil

**Symptome:**

- Formular wird auf Mobilgeräten fehlerhaft angezeigt
- Inkonsistente Abstände oder Ausrichtung
- Felder werden nicht korrekt angezeigt
- Schlechte grafische Hierarchie

**Lösungen:**

1. **Reaktionsfähigkeit auf Mobilgeräten**
   - Mobilgerätespezifische Optimierungen anfordern: „Mach dieses Formular mobilfreundlich“
   - Anforderungen für responsives Design festlegen
   - Auf Mobilgeräten testen
   - Einspaltige Layouts für Mobilgeräte verwenden

2. **Layout-Verbesserungen**
   - Spezifische Angaben bei Layout-Anforderungen machen: „Ordne Adressfelder in zwei Spalten an“
   - Spezifischen Stil anfordern: „Verwende professionelle Farben und saubere Typografie“
   - Abstands- und Ausrichtungsanforderungen festlegen
   - Konformität mit Barrierefreiheitsvorschriften fordern

3. **Markenkonsistenz**
   - Markenrichtlinien vor der Formularerstellung vorbereiten
   - Bestimmte Farb-Codes und Schriftarten in Anfragen einschließen
   - Konsistente Stile in allen Formularen verwenden
   - Markenvorlagen zur Wiederverwendung erstellen

### Probleme mit bedingter Logik

**Symptome:**

- Regeln werden nicht erwartungsgemäß ausgelöst
- Felder werden falsch angezeigt/ausgeblendet
- Validierungslogik funktioniert nicht
- Komplexe Geschäftsregeln schlagen fehl

**Lösungen:**

1. **Regelvereinfachung**
   - Komplexe Regeln in kleinere, einfachere Bedingungen aufteilen
   - Jede Regel einzeln testen, bevor sie kombiniert wird
   - Klare, spezifische Bedingungen verwenden: „Zeige @spouseInfo an, wenn @maritalStatus gleich &#39;Verheiratet&#39; ist“
   - Verschachtelte oder übermäßig komplexe Logik zunächst vermeiden

2. **Testen und Debugging von Regeln**
   - Alle möglichen Benutzerpfade und Szenarien testen
   - Feldnamen und Werte in Bedingungen prüfen
   - Groß-/Kleinschreibung in Regelbedingungen prüfen
   - Debug-Modus verwenden, um die Regelausführung zu verfolgen

3. **Geschäftslogik-Implementierung**
   - Geschäftsanforderungen vor der Implementierung dokumentieren
   - Regeln inkrementell implementieren und jeden Schritt testen
   - Eindeutiges Benutzer-Feedback bereitstellen, wenn Regeln ausgelöst werden
   - Grenzfälle und Ausnahmeszenarien behandeln

## Probleme beim Import und bei der Konvertierung von Dateien

### PDF-Importfehler

**Symptome:**

- PDF-Dateien werden nicht hochgeladen oder verarbeitet
- In konvertierten Formularen fehlen Felder oder Inhalte
- Fehlermeldungen während der PDF-Konvertierung
- Schlechte Felderkennung durch PDF

**Lösungen:**

1. **Dateiformat und -größe**
   - Sicherstellen, dass PDF-Dateien unter 10 MB groß sind
   - Hochwertige, textbasierte PDFs verwenden (keine gescannten Bilder)
   - Prüfen, ob PDF kennwortgeschützt oder verschlüsselt ist
   - PDF in Bildformat konvertieren, wenn die Textextraktion fehlschlägt

2. **PDF-Qualitätsoptimierung**
   - PDFs mit eindeutigen, klar definierten Formularfeldern verwenden
   - Guten Kontrast und lesbaren Text sicherstellen
   - Komplexe Layouts oder überlappende Elemente vermeiden
   - Zusätzlichen Kontext in der Konvertierungsanfrage angeben

3. **Verbessern der Konvertierung**
   - Erwartete Formularstruktur detailliert beschreiben
   - Feldtypen und Validierungsanforderungen angeben
   - Spezifische Verbesserungen anfordern: „Füge Reaktionsfähigkeit und Validierung für Mobilgeräte hinzu“
   - Konvertierte Formulare manuell prüfen und optimieren

### Konvertierungsprobleme bei Bildern und Screenshots

**Symptome:**

- Schlechte Felderkennung bei Bildern
- Falsche Feldtypen oder Layouts
- Fehlende Formularelemente
- Konvertierungsfehler oder Zeitüberschreitungen

**Lösungen:**

1. **Bildqualitätsanforderungen**
   - Hochauflösende Bilder verwenden (mindestens 300 DPI)
   - Gute Beleuchtung und Kontrast sicherstellen
   - Schatten, Blendeffekte oder Verzerrungen vermeiden
   - Bilder zuschneiden, um den Fokus auf die Formularinhalte zu legen

2. **Optimale Bildformate**
   - PNG- oder JPG-Format für optimale Ergebnisse verwenden
   - GIF- oder komprimierte Bilder mit niedriger Qualität vermeiden
   - Sicherstellen, dass der Text im Bild gut lesbar ist
   - Bei Bedarf verschiedene Bildausrichtungen probieren

3. **Anleitungen zur Konvertierung**
   - Detaillierte Beschreibungen der Formularstruktur angeben
   - Feldtypen und Anforderungen explizit angeben
   - Spezifische Verbesserungen während der Konvertierung anfordern
   - Auf manuelle Anpassungen nach der Konvertierung vorbereitet sein

## Probleme bei Integration und Übermittlung

### Fehlgeschlagene Formularübermittlung

**Symptome:**

- Formulare werden nicht erfolgreich übermittelt
- Fehlermeldungen während der Übermittlung
- Daten erreichen nicht die beabsichtigten Ziele
- Zeitüberschreitungsfehler bei der Übermittlung

**Lösungen:**

1. **Konfiguration der Übermittlungsaktion**
   - Ordnungsgemäße Konfiguration der Übermittlungsaktion prüfen
   - API-Endpunkte und Authentifizierungsdaten prüfen
   - Zunächst mit einfacher E-Mail-Übermittlung testen
   - Datenformatanforderungen validieren

2. **Netzwerk und Verbindung**
   - Internetverbindung und Netzwerkstabilität prüfen
   - Sicherstellen, dass Firewall-Einstellungen Formularübermittlungen zulassen
   - Verschiedene Netzwerkverbindungen testen
   - Unternehmens-Proxy- oder Sicherheitsbeschränkungen prüfen

3. **Probleme bei der Datenvalidierung**
   - Sicherstellen, dass alle erforderlichen Felder ausgefüllt sind
   - Überprüfen, ob Datenformate den API-Anforderungen entsprechen
   - Auf Sonderzeichen oder Kodierungsprobleme prüfen
   - Zuerst mit minimalem Datensatz testen

### Probleme bei der API-Integration

**Symptome:**

- REST-API-Endpunkte reagieren nicht
- Authentifizierungsfehler
- Nicht übereinstimmende Datenformate
- Zeitüberschreitungen oder Fehler bei der Integration

**Lösungen:**

1. **Prüfen der API-Konfiguration**
   - Prüfen, ob API-Endpunkt-URLs korrekt und zugänglich sind
   - Authentifizierungsdaten und -berechtigungen prüfen
   - API-Endpunkte unabhängig voneinander mit Tools wie Postman testen
   - Prüfen, ob die API das richtige Datenformat akzeptiert (JSON, XML usw.)

2. **Probleme bei der Datenzuordnung**
   - Sicherstellen, dass Formularfeldnamen mit API-Parameteranforderungen übereinstimmen
   - Auf erforderliche Felder prüfen, die möglicherweise fehlen
   - Datentypkompatibilität (Zeichenfolgen, Zahlen, Daten) prüfen
   - Mit Beispieldaten testen, um Zuordnungsprobleme zu identifizieren

3. **Fehlerbehandlung und Debugging**
   - Detaillierte Fehlerprotokollierung für API-Aufrufe aktivieren
   - API-Antwort-Codes und Fehlermeldungen prüfen
   - Wiederholungslogik für temporäre Fehler implementieren
   - Fallback-Optionen für Benutzende bereitstellen, wenn die API fehlschlägt

### Probleme bei der E-Mail-Integration

**Symptome:**

- Bestätigungs-E-Mails werden nicht gesendet
- E-Mails landen in Spam-Ordnern
- Falsche E-Mail-Formatierung
- Fehlende Formulardaten in E-Mails

**Lösungen:**

1. **E-Mail-Konfiguration**
   - Prüfen, ob E-Mail-Adressen korrekt formatiert sind
   - SMTP-Einstellungen und -Authentifizierung prüfen
   - Zuerst mit einfachen E-Mail-Adressen testen
   - E-Mail-Server-Berechtigungen und -Kontingente prüfen

2. **Optimierung des E-Mail-Versands**
   - Korrekte E-Mail-Kopfzeilen und Absenderinformationen verwenden
   - Spam-Trigger-Wörter in Betreffzeilen vermeiden
   - Korrekte Abmeldemechanismen einschließen
   - E-Mail-Versand an verschiedene Anbieter testen

3. **Inhalt und Formatierung**
   - Prüfen, ob Formulardaten in E-Mails ordnungsgemäß formatiert sind
   - Auf Sonderzeichen oder Kodierungsprobleme prüfen
   - E-Mail-Vorlagen mit verschiedenen Datenkombinationen testen
   - Sicherstellen, dass E-Mail-Inhalte barrierefrei und lesbar sind

## Leistungs- und Ladeprobleme

### Langsames Laden von Formularen

**Symptome:**

- Das Laden von Formularen dauert zu Beginn sehr lange
- Träge Benutzerinteraktionen
- Zeitüberschreitungen bei Formularvorgängen
- Schlechte Leistung auf Mobilgeräten

**Lösungen:**

1. **Formularoptimierung**
   - Anzahl der Felder und Komplexität reduzieren
   - Verzögertes Laden für nicht kritische Abschnitte implementieren
   - Bilder und Assets für die Web-Bereitstellung optimieren
   - Unnötige Validierungsregeln oder -logik entfernen

2. **Browser- und Geräteoptimierung**
   - Browsercache und temporäre Dateien löschen
   - Unnötige Browser-Registerkarten und Anwendungen schließen
   - Verfügbaren Gerätespeicher und Speicherplatz prüfen
   - Verschiedene Browser zum Leistungsvergleich verwenden

3. **Netzwerkoptimierung**
   - Mit verschiedenen Netzwerkverbindungen testen
   - Auf Netzwerküberlastung oder Bandbreitenbeschränkungen prüfen
   - Nach Möglichkeit kabelgebundene Verbindungen anstelle von WLAN verwenden
   - Bei Problemen mit der Netzwerkleistung an den IT-Support wenden

### Validierung von Leistungsproblemen

**Symptome:**

- Langsame Validierungsreaktionen
- Verzögerte Anzeige von Fehlermeldungen
- Formulare frieren während der Validierung ein
- Zeitüberschreitungsfehler bei der Feldvalidierung

**Lösungen:**

1. **Validierungsoptimierung**
   - Häufigkeit der Echtzeit-Validierung reduzieren
   - Debouncing für Validierungsaufrufe implementieren
   - Komplexe Validierungsregeln vereinfachen
   - Nach Möglichkeit Client-seitige Validierung verwenden

2. **Regelvereinfachung**
   - Komplexe Validierung in kleinere Regeln aufteilen
   - Unnötige feldübergreifende Validierungen entfernen
   - Bedingte Logik für Leistung optimieren
   - Validierungsergebnisse zwischenspeichern, wenn möglich

3. **Verbessern der Benutzererlebnisse**
   - Sofortiges Feedback für einfache Validierungen geben
   - Für komplexe Regeln progressive Validierung anstelle von Echtzeit-Validierung verwenden
   - Ladeanzeigen während Validierungsprozessen anzeigen
   - Benutzenden erlauben, während der Hintergrund-Validierungsprozesse fortzufahren

## Erweiterte Fehlerbehebung

### Debug-Modus und Diagnose

**Aktivieren von Debug-Informationen**

Verwenden Sie folgende Prompts, um detailliertere Informationen zu Formularproblemen zu erhalten:

    Aktiviere den Debug-Modus, um Probleme bei der Formularübermittlung und Feldüberprüfung zu identifizieren
    
    Analysiere Formularfehler: Prüfe Validierungsregeln, API-Antworten und Benutzereingabemuster
    
    Zeige detaillierte Informationen zur Formularstruktur und Feldkonfiguration an

### Methoden bei der Fehleranalyse

**Systematischer Debugging-Ansatz**

1. **Isolieren des Problems**
   - Mit minimaler Formularkonfiguration testen
   - Komplexe Funktionen vorübergehend entfernen
   - Einzelne Komponenten separat testen
   - Ausschlussverfahren zur Ermittlung der Grundursache verwenden

2. **Erfassen von Diagnoseinformationen**
   - Browser-Konsole auf JavaScript-Fehler prüfen
   - Netzwerkanfragen und -antworten prüfen
   - Exakte Schritte zum Reproduzieren des Problems dokumentieren
   - Screenshots und Fehlermeldungen sammeln

3. **Testen der Umgebungsvariablen**
   - Verschiedene Browser und Geräte verwenden
   - Mit verschiedenen Benutzerkonten und Berechtigungen testen
   - In verschiedenen Netzwerkumgebungen prüfen
   - Mit funktionierenden Formularen oder Konfigurationen vergleichen

### Analyse und Überwachung protokollieren

**Debugging der Browser-Konsole**

1. Browser-Entwickler-Tools öffnen (F12)
2. Konsole auf JavaScript-Fehler prüfen
3. Tab „Netzwerk“ auf fehlgeschlagene Anfragen prüfen
4. Tab „Leistung“ auf langsame Vorgänge prüfen

**Häufige Fehlermuster**

- **CORS-Fehler**: Probleme mit ursprungsübergreifenden Anfragen bei API-Integrationen
- **Authentifizierungsfehler**: Ungültige Anmeldeinformationen oder abgelaufene Token
- **Validierungsfehler**: Konflikte bei Regeln für die Feldvalidierung oder Syntaxfehler
- **Netzwerkzeitüberschreitungen**: Langsame oder unzuverlässige Netzwerkverbindungen

## Abrufen zusätzlicher Hilfe

### Self-Service-Ressourcen

**Integriertes Hilfesystem**

- Befehl `/help` gefolgt von spezifischen Fragen verwenden
- Kontextbezogene Hilfe in der Forms Experience Builder-Benutzeroberfläche aufrufen
- Fehlermeldungen sorgfältig auf spezifische Anleitungen prüfen
- [Forms Experience Builder – Erste Schritte](forms-ai-assistant-getting-started.md) lesen

**Dokumentationsressourcen**

- [Forms Experience Builder – Prompt-Bibliothek](ai-assistant-prompt-library.md)
- [Forms Experience Builder – Best Practices](aem-forms-ai-assistant-best-practices.md)
- [AEM Forms-Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html\lang=de)

### Eskalation und Support

**Wann sollte ich den Support kontaktieren?**

- Probleme bleiben auch nach Ausprobieren der dokumentierten Lösungen bestehen
- Systemweite Probleme, die mehrere Benutzende betreffen
- Bedenken hinsichtlich der Sicherheit oder Datenintegrität
- Integrationsprobleme, die eine Konfiguration auf Systemebene erfordern

**Bereitzustellende Informationen**

- Detaillierte Beschreibung des Problems und Schritte zur Reproduktion
- Screenshots oder Bildschirmaufzeichnungen des Problems
- Browser- und Systeminformationen
- Fehlermeldungen und Konsolenprotokolle
- Details zur Formularkonfiguration und -integration

**Kontaktmethoden**

- Systemadmin: Für Probleme mit Umgebung und Zugriff
- Technischer Support: Für komplexe Integrations- und Konfigurationsprobleme
- EARLY ACCESS-PROGRAMM: `aem-forms-ea@adobe.com` für programmspezifische Fragen

### Community und Wissensaustausch

**Best Practices für die Problemlösung**

- Lösungen als Referenz für die Zukunft dokumentieren
- Erfolgreiche Ansätze zur Fehlerbehebung mit Team-Mitgliedern austauschen
- Beiträge in der Wissensdatenbank des Unternehmens verfassen
- In Benutzer-Communities und Foren teilnehmen

**Kontinuierliche Verbesserung**

- Regelmäßige Überprüfung häufiger Probleme und ihrer Lösungen
- Aktualisierung der Fehlerbehebungsverfahren auf Grundlage neuer Erkenntnisse
- Schulungen und Wissensaustausch
- Feedback an das Produkt-Team für Funktionsverbesserungen

Dieses Handbuch zur Fehlerbehebung wird auf Basis von Benutzer-Feedback und neuen Funktionen des KI-Assistenten fortlaufend aktualisiert. Die neuesten Informationen und weitere Ressourcen finden Sie in der [Dokumentation zu AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html\lang=de).
