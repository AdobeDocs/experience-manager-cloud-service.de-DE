---
title: Häufig gestellte Fragen - Interaktive Kommunikation
description: Häufig gestellte Fragen zu interaktiven Kommunikationen in AEM Forms as a Cloud Service, zu Anzeigemustern, Anmerkungen, Versionsvergleichen und mehr.
feature: Interactive Communication
role: User, Developer, Admin
exl-id: 4cc1bff3-edfb-4826-b914-2a2231b703f9
source-git-commit: 53ff71c82d35b9ec9b20b521ef469d3f0abd79df
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 5%

---

# Häufig gestellte Fragen - Interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

## Allgemein

**F: Kann ich eine vorhandene XDP in den Editor für interaktive Kommunikation importieren?**
Ja, Sie können eine vorhandene XDP-Datei importieren und als Ausgangspunkt verwenden. Alle nicht unterstützten Funktionen werden während des Importvorgangs hervorgehoben.

**F: Ist der Editor für interaktive Kommunikation für On-Premise-Bereitstellungen verfügbar?**
Nein, der Editor ist nur für Forms as a Cloud Service-Bereitstellungen verfügbar.

## Anzeigemuster

**F: Was ist ein Anzeigemuster und wie unterscheidet es sich von der Datenbindung?**
Ein Anzeigemuster steuert, wie ein Feldwert in der Arbeitsflächenvorschau und in der generierten Ausgabe *präsentiert* dargestellt wird - z. B. das Formatieren einer Zahl als Währung ($1.234,21) oder einer Textzeichenfolge als Telefonnummer ((555) 123-4567). Der zugrunde liegende gespeicherte Wert ist unverändert. Im Gegensatz dazu steuert die Datenbindung, *wo* Feldwert herkommt - und verbindet das Feld mit einem Datenmodell oder Schemaelement.

**F: Welche Feldtypen unterstützen Anzeigemuster?**
Anzeigemuster werden für die Komponenten „Textfeld“, „Numerisches Feld“, „Datumsfeld“, „Datum/Uhrzeit-Feld“ und „Ungebundene Variable“ unterstützt. Jeder Feldtyp verwendet eine seinem Datentyp entsprechende XFA-Picture-Klauselsyntax.

**F: Mein Datumsanzeigemuster funktioniert nicht - das Feld zeigt den Rohwert anstelle der formatierten Ausgabe an. Was ist los?**
Für Datums- und Datums-/Uhrzeitfelder muss der zugrunde liegende Wert dem ISO 8601&#x200B;**Format**. Geben Sie für Datumsfelder Werte im `YYYY-MM-DD` an (z. B. `2007-04-01`). Verwenden Sie für Datums-/Uhrzeitfelder `YYYY-MM-DDTHH:MM` Format (z. B. `2007-04-01T14:30`). Werte, die nicht ISO 8601 entsprechen, werden unverändert angezeigt, ohne dass das Anzeigemuster angewendet wird.

**F: Kann ich ein benutzerdefiniertes Muster definieren, das nicht in der vordefinierten Liste enthalten ist?**
Ja. Sie können eine benutzerdefinierte **XFA-Bildklausel** direkt im Feld Anzeigemuster im Bedienfeld Eigenschaften eingeben. Siehe die Picture-Klauselsymbole für jeden Feldtyp auf den entsprechenden Komponenten-Referenzseiten.

## Überprüfen und Anmerkungen

**F: Was ist der Unterschied zwischen Kommentaren und Anmerkungen in interaktiver Kommunikation?**
**Kommentare** sind allgemeine Anmerkungen, die einer IC im Bedienfeld „Kommentare“ hinzugefügt werden - sie werden dem Dokument als Ganzes und nicht bestimmten Komponenten beigefügt. **Anmerkungen** werden positioniert und auf Komponentenebene an die Prüfpunkte angeheftet: Ein Reviewer öffnet eine schreibgeschützte Anmerkungsarbeitsfläche, klickt auf eine beliebige Komponente im Design und hinterlässt einen Kommentar, der an genau diese Stelle angeheftet ist. Alle Reviewer verwenden dieselbe Anmerkungsansicht. Autoren können dann jede Anmerkung im IC-Editor als „Aufgelöst“ markieren.

**F: Kann ein Reviewer beim Verlassen von Anmerkungen versehentlich den IC bearbeiten?**
Anzahl Die Arbeitsfläche für Anmerkungen ist eine dedizierte schreibgeschützte Ansicht. Reviewer können nur Kommentar-Pins hinzufügen oder anzeigen und keine Komponente im IC ändern.

**F: Was passiert mit einer Anmerkung, nachdem sie als „Gelöst“ markiert wurde?**
Aufgelöste Anmerkungen bleiben zu Verlaufszwecken sichtbar, werden jedoch als geschlossene (graue) Pins angezeigt, was sie visuell von offenen (aktiven) Feedback-Elementen unterscheidet. Auf diese Weise können Teams den Überprüfungsfortschritt verfolgen, ohne das Audit-Protokoll zu verlieren.

**F: Werden Anmerkungen auf allen Komponenten unterstützt?**
Noch nicht. Anmerkungen zu Fragmentteilen eines Dokuments und zur Tabellenkomponente werden derzeit nicht unterstützt. Anmerkungen zu anderen Komponenten werden vollständig unterstützt.

## Versionsvergleich

**F: Was kann ich sehen, wenn ich zwei Versionen vergleiche?**
Beide Versionen werden nebeneinander geöffnet, während PDF eine Vorschau anzeigt, sodass Sie Layout- und statische Inhaltsunterschiede visuell überprüfen können. Dynamische Feldwerte werden nicht einbezogen, sondern nur das gerenderte Layout und der statische Text werden verglichen.

**F: Wie starte ich einen Versionsvergleich?**
Navigieren Sie zu **Forms > Forms und Dokumente** wählen Sie die IC-**aus, klicken Sie** der Aktionssymbolleiste auf Version vergleichen und wählen Sie die zu vergleichende Version aus. Eine neue Registerkarte wird geöffnet, auf der beide Versionen nebeneinander angezeigt werden.

**F: Kann ich bestimmte Textänderungen innerhalb eines Absatzes sehen, wenn ich Versionen vergleiche?**
Anzahl Wenn ein Absatz neu geschrieben oder angeordnet wurde, werden beide Seiten identisch mit ihrer Quell-PDF dargestellt. Es gibt keinen Inline-Textvergleich - der Vergleich ist nur visuell.

## Tabellen

**F: Kann ich Zellen in einer Tabelle zusammenführen?**
Ja. Wählen Sie zwei oder mehr aufeinander folgende Zellen in derselben Zeile aus, klicken Sie mit der rechten Maustaste darauf und wählen Sie **Zellen verbinden**. Es können nur aufeinander folgende Zellen innerhalb derselben Zeile zusammengeführt werden. Zeilenübergreifende Zusammenführungen werden nicht vollständig unterstützt. Siehe [Zusammenführen und Aufteilen von &#x200B;](/help/forms/interactive-communication/howto/merge-and-split-table-cells.md).

**F: Kann ich eine Zellzusammenführung rückgängig machen?**
Ja. Klicken Sie mit der rechten Maustaste auf die zusammengeführte Zelle, wählen Sie **Zelle teilen** und geben Sie die Anzahl der Spalten an, in die aufgeteilt werden soll (bis zur ursprünglichen Anzahl der zusammengeführten Zellen).

## Musterseite

**F: Wie lasse ich eine Komponente auf jeder Seite einer interaktiven Kommunikation erscheinen?**
Verschieben Sie die Komponente auf die Musterseite. Klicken Sie mit der rechten Maustaste auf eine geeignete Komponente auf einer Design-Seite und wählen Sie **Verschieben nach > Musterseite**. Die Komponente wird aus der Designseite entfernt und an derselben visuellen Position auf der Musterseite platziert, sodass sie konsistent auf allen Seiten angezeigt wird, die diese Musterseite gemeinsam nutzen. Siehe [Verschieben einer Komponente auf die Musterseite](/help/forms/interactive-communication/howto/move-component-to-master-page.md).

**F: Welche Komponententypen können nicht auf die Musterseite verschoben werden?**
Die folgenden Typen sind nicht für die Aktion Zur primären Seite wechseln geeignet: Inhaltsbereiche, Seitenbereiche, Seitensätze, Fragmente, Teilformulare, Tabellenzeilen, Tabellenzellen und Optionsfelder. Komponenten mit angewendeter Inhalts- oder Layout-Sperre sind ebenfalls nicht zulässig.

