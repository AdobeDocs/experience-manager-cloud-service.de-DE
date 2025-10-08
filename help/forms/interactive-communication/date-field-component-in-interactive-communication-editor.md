---
title: Datumsfeldobjekt im Editor für interaktive Kommunikation
description: Mit dem Datumsfeldobjekt im Editor für interaktive Kommunikation in AEM Forms können Autorinnen und Autoren ein kalenderbasiertes Datumsauswahlfeld in ein Dokument einfügen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: bd8992792afddb2243736578acd24bc47efad842
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 8%

---


# Datumsfeldobjekt im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Prompts, Beispiele und Best Practices können sich ändern, da Forms Experience Builder im Verlauf des Early-Adopter-Programms weiterentwickelt wird.

## &#x200B;1. Einführung

Mit **Komponente „Datumsfeld** im Editor für interaktive Kommunikation (IC) können Autoren ein kalenderbasiertes Datumsauswahlfeld in ein Dokument einfügen. Auf diese Weise können Benutzer ein Datum einfach aus einer Datumsauswahl auswählen oder es manuell in einem vordefinierten Format eingeben.

Das Datumsfeld ist ideal zur Erfassung von Geburtsdaten, Terminplänen, Bewerbungsdaten oder Start-/Enddaten von Richtlinien. Es verbessert die Genauigkeit und reduziert Eingabefehler. Es unterstützt Formatierung, Formatierung und Datenbindung für die nahtlose Integration mit Datenmodellen und Backend-Systemen.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/date.png)

## &#x200B;2. Eigenschaften

Das Datumsfeldobjekt enthält mehrere konfigurierbare Eigenschaften:

2.1. Grundfeld

- **Name:** Eindeutige Kennung, die zum Referenzieren des Felds in Regeln, Skripten und Datenmodellen verwendet wird.

- **Beschriftung:** dem Benutzer angezeigte Anzeigebezeichnung (z. B. „Geburtsdatum„).

- **Datum** Der tatsächliche Datumswert, der standardmäßig leer oder mithilfe dynamischer Daten vorausgefüllt sein kann.

- **Reservieren** Ein optionales Fallback-Datum (angezeigt, wenn kein Datum ausgewählt oder keine Daten verfügbar sind).

- **Erscheinungsbild** Eine schnelle Stilvorgabe (z. B. unterstrichen, flach, umrandet) für visuelle Konsistenz.

2.2. Typografie

Steuert, wie das Datum visuell im Feld angezeigt wird:

- **Schriftvariante:** Sie Schriftfamilie, Stärke (z. B. normal, fett) und Stil (z. B. kursiv) aus.

- **Größe:** in der Regel standardmäßig auf 10 pt festgelegt, kann jedoch aus Gründen der Konsistenz mit dem umgebenden Inhalt angepasst werden.

2.3. Lage

Definiert die räumliche Platzierung innerhalb des Dokumentlayouts:

- **X- und Y-Koordinaten** Bestimmt die horizontale und vertikale Position.

- **Breite und Höhe** Legen Sie sie in Millimetern oder Prozentsätzen fest, um sie an anderen Formularelementen auszurichten.

2.4. Spanne

Gibt den Abstand um die Feldgrenzen an:

- Auffüllen (oben)

- Unten (unten)

- Linksbündig

- Rechtsbündig

Diese Werte helfen bei der präzisen Ausrichtung innerhalb von Teilformularen oder Layout-Rastern.

2.5. Erscheinungsbild

Definiert den visuellen Stil des Feld-Containers:

- **Fill:** Hintergrundfarbe des Felds (z. B. weiß, hellgrau).

- **Kontur** Rahmenfarbe oder Kontur.

- **Breite** Die Stärke des Feldrands.

- **Style:** Optionen Durchgehend, Gestrichelt oder gestrichelte Linie.

- **Kanten** Passen Sie Ecken als abgerundet oder scharf für verschiedene Designvoreinstellungen an.

2.6. Vorhandensein

Bestimmt, wie und wann das Feld angezeigt wird:

- **Sichtbar:** Standardeinstellung, bei der das Feld zur Laufzeit angezeigt wird.

- **Ausgeblendet (Platz bleibt):** Feld bleibt unsichtbar, aber der Layout-Raum wird beibehalten.

Dies ist hilfreich, wenn die Sichtbarkeit basierend auf Benutzereingaben oder Regeln dynamisch umgeschaltet werden soll.

2.7. Datenbindung

Verbindet das Datumsfeld mit Datenstrukturen zum Speichern oder Vorausfüllen von Werten.

**Datenbindungstyp:**

- **Benutzername:** das Feld mithilfe seines Namensattributs an das Schema.

- **Globale Daten verwenden** Bindungen mit einem vordefinierten Datenmodell oder Schemaelement.

- **Keine Datenbindung:** Das Feld bleibt statisch und ist mit keiner Datenquelle verbunden.

Dies ermöglicht das Abrufen, Anzeigen oder Speichern dynamischer Datumswerte basierend auf der Anwendungslogik.

## &#x200B;3. Verwendung

Das Datumsfeld ist besonders in folgenden Szenarien nützlich:

- Erfassen des Geburtsdatums oder des Beitrittsdatums in Onboarding-Formularen.

- Start- und Enddatum für Services, Abonnements oder Ereignisse auswählen.

- Eingabe von Bewerbungsfristen, Terminplätzen oder Verifizierungsdaten.

Autoren können das Datumsfeld in Layout-Containern oder Teilformularen platzieren und die Validierung (z. B. Datumsformat, Bereichsbeschränkungen) konfigurieren, um die Datenqualität zu verbessern.

## 4. Best Practices

- Verwenden Sie für bessere Benutzererlebnisse klare Beschriftungen wie „Startdatum“ oder „Termindatum auswählen“.

- Legen Sie minimale und maximale Datumsbereiche fest, um ungültige Eingaben zu verhindern (z. B. zukünftiges Geburtsdatum).

- Verwenden Sie konsistente Schriftstile (10 pt empfohlen) für die Lesbarkeit.

- Binden Sie Felder an das Schema, wo immer eine Backend-Datenintegration erforderlich ist.

- Dynamisches Ausblenden nicht relevanter Datumsfelder mithilfe von Sichtbarkeitsregeln.

Das **Datumsfeld**-Objekt im Editor für interaktive Kommunikation ist ein leistungsstarkes Tool zur präzisen und einfachen Erfassung zeitkritischer Daten. Wenn sie durchdacht gestaltet und mit aussagekräftigen Datenpfaden verbunden sind, unterstützt sie ein nahtloses Benutzererlebnis und eine effiziente Verarbeitung von zeitbasierten Einträgen.


