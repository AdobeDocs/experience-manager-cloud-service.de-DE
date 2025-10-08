---
title: Barcode-Komponente im Editor für interaktive Kommunikation
description: Die Barcode-Komponente im Editor für interaktive Kommunikation in AEM Forms ermöglicht es Autorinnen und Autoren, kodierte Daten in Kommunikationsvorlagen visuell darzustellen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: bd8992792afddb2243736578acd24bc47efad842
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 7%

---


# Barcode-Komponente im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Prompts, Beispiele und Best Practices können sich ändern, da Forms Experience Builder im Verlauf des Early-Adopter-Programms weiterentwickelt wird.

## &#x200B;1. Einführung

Mit der Barcode-Komponente im Editor für interaktive Kommunikation können Autoren kodierte Daten in Kommunikationsvorlagen visuell darstellen. Dies ist besonders für Anwendungen nützlich, die Tracking, Identifizierung, Abrechnung oder Automatisierung beinhalten. Mit Unterstützung für verschiedene Barcode-Standards wie Code 128, QR und mehr bietet diese Komponente flexible Stile, Positionierungs- und Datenbindungsoptionen für eine Vielzahl von Geschäftsanforderungen.

Unabhängig davon, ob Sie Kundenrechnungen, Versandaufkleber oder Mitgliedskarten erstellen, vereinfacht die Barcode-Komponente den Prozess, indem sie maschinenlesbare Daten direkt in Ihr Dokument einbettet.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/barcode.png)

## &#x200B;2. Eigenschaften

Die Barcode-Komponente verfügt über einen umfassenden Satz konfigurierbarer Optionen zur Steuerung von Verhalten und Erscheinungsbild:

2.1 Basisfeld

**Name:** Eindeutige Kennung für den Barcode. Er wird verwendet, um auf die Komponente in Datenmodellen und Regelsätzen zu verweisen.

**Speicherort** Gibt an, wo der Barcodetext relativ zum Barcodesymbol angezeigt werden soll.

**Optionen:**

- **None:** Blendet den Text aus.

- **Oberhalb:** Zeigt den Text über dem Barcode an.

- **Unten:** Zeigt den Text unterhalb des Barcodes an.

- **Über Eingebettet** Bettet den Text im oberen Bereich des Barcodes ein.

- **Unterhalb eingebettet:** Bettet den Text im unteren Bereich des Barcodes ein.

- **Type:** Gibt den Barcode-Standard an (z. B. Code 128, Code 39, QR-Code usw.).

- **Standard:** Ein vordefinierter Wert, der angezeigt wird, wenn keine Daten bereitgestellt werden.

- **Datenlänge:** Gibt die erwartete oder maximale Anzahl von Zeichen an, die der Barcode enthalten kann.

- **Prüfsumme:** Validiert Barcode-Daten auf Korrektheit.

   - **Optionen:**

      - **Keine** Keine Prüfsummenvalidierung.

      - **Auto:** berechnet die Prüfsumme automatisch anhand des Typs.

- **Breite/Schmal-Verhältnis:** Definiert die relative Breite der breiten Balken zu den schmalen (in einigen 1D-Barcodes verwendet).

2.2 Standort

Bestimmt, wo der Barcode in Bezug auf den Inhalt angezeigt wird:

- **Keine** Keine zusätzliche Positionierung.

- **Oberhalb:** Platziert den Barcode über dem zugehörigen Inhalt.

- **Unten:** Platziert den Barcode unter dem Inhalt.

- **Über dem Eingebetteten** Der Barcode ist eingebettet und schwebt über dem Inhalt.

- **Unter eingebettet:** Unter Inhalt eingebettet.

2.3 Position

Definiert die genaue Platzierung des Barcodes innerhalb des Layouts:

- **X- und Y-Koordinaten** Positionieren Sie den Barcode mithilfe von Millimetereinheiten innerhalb des Formulars.

- **Höhe und Breite** Legen Sie die physischen Abmessungen des Barcodes fest.

2.4 Spanne

Fügt Leerzeichen um den Barcode hinzu, um eine bessere visuelle Trennung zu ermöglichen:

- Oben

- Unten

- Linksbündig

- Rechtsbündig

Diese Ränder helfen bei der Konsistenz und Lesbarkeit des Layouts.

2.5 Erscheinungsbild

Den visuellen Stil des Barcodes anpassen:

- **Fill** Hintergrundfarbe des Barcodebereichs.

- **Kontur:** Rahmenfarbe.

- **Breite** Definiert die Stärke der Strichcodelinien.

- **Style:** Sie aus Vorgaben wie „flach“, „umrandet“ oder „erhöht“ aus.

- **Kanten** Wählen Sie für das Barcode-Feld zwischen abgerundeten und scharfen Ecken.

2.6 Vorhandensein

Steuert, ob der Barcode zur Laufzeit ein- oder ausgeblendet wird:

- **Sichtbar:** Barcode wird in der endgültigen Ausgabe angezeigt.

- **Ausgeblendet:** ist reserviert, aber der Barcode wird nicht angezeigt.

2.7 Datenbindung

Datenbindung: Verbindet den Barcode mit einem Backend-Datenmodell (XML oder JSON). Dadurch wird sichergestellt, dass der Barcode dynamisch eindeutige Daten pro Dokumentinstanz widerspiegelt, z. B. eine Bestell-ID oder eine Tracking-Nummer.

## &#x200B;3. Verwendung

Die Barcode-Komponente ist besonders hilfreich bei der Automatisierung von Prozessen, die auf gescannten Daten basieren. Sie kann zu Kommunikationsvorlagen hinzugefügt werden, wie zum Beispiel:

- Rechnungen (für Kundenreferenz und Schnellscannzahlungen)

- Versand-Labels (für Package-Tracking)

- Mitgliedschafts- oder Treuekarten (zur scan-basierten Identifizierung)

- Coupons und Gutscheine (zur Validierung am Point of Sale)

Autoren können den Barcode in Layout-Container einbetten und entsprechend dem Marken- oder Dokumentdesign formatieren.

## 4. Best Practices

- Verwenden Sie einen geeigneten Barcodetyp für den Anwendungsfall, z. B. QR-Code für URLs oder Code 128 für alphanumerische IDs.

- Prüfen Sie die Lesbarkeit der Strichcodes, indem Sie Testversionen drucken und scannen.

- Stellen Sie die Datenintegrität mithilfe der Option Prüfsumme sicher, wenn der Barcode-Standard dies unterstützt.

- Wählen Sie lesbare Größen und Linienbreiten, um Probleme beim Scannen zu vermeiden.

- Achten Sie auf ausreichende Ränder, um beim Drucken ein Abschneiden zu vermeiden.

Mit der Barcode-Komponente im Editor für interaktive Kommunikation können Dokumentersteller die Lücke zwischen digitalen und physischen Systemen schließen. Bei effektiver Implementierung verbessert es die Automatisierung, verbessert die Benutzerfreundlichkeit und unterstützt die nahtlose Integration mit Scangeräten und -Workflows.
