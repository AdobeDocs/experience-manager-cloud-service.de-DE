---
title: Rechteckkomponente im Editor für interaktive Kommunikation
description: Die Rechteckkomponente im Editor für interaktive Kommunikation in AEM Forms ermöglicht es Autorinnen und Autoren, geformte grafische Elemente hinzuzufügen, die als Layout-Trennzeichen, visuelle Akzente oder Inhalts-Container dienen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: d2af7706-2b2a-4a40-a4a4-375b5f2b08fb
source-git-commit: cdaceaabb8eeeec931b1897e1161f408606540b9
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 4%

---

# Rechteckkomponente im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

## &#x200B;1. Einführung

Mit der Komponente Rechteck im Editor für interaktive Kommunikation (IC) können Autorinnen und Autoren geformte grafische Elemente hinzufügen, die als Layout-Trennzeichen, visuelle Akzente oder Inhalts-Container dienen. Rechtecke verbessern die visuelle Hierarchie und lenken die Aufmerksamkeit der Benutzenden in strukturierten Kommunikations-Layouts.
Diese Komponente ist nicht an Daten gebunden, sondern dient der Verbesserung der Designklarheit, der Gruppierung verwandter Felder und der Verbesserung der allgemeinen Präsentation.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/rectangle.png)

## &#x200B;2. Eigenschaften

Die Komponente Rechteck enthält mehrere anpassbare Eigenschaften:

2.1. Name

Name: Eine eindeutige Kennung für das Rechteck. Wird hauptsächlich für die Referenzierung in Layout-Hierarchien oder die konsistente Anwendung von Stilen verwendet.

2.2. Lage

- **Beschreibung:** Bestimmt, wo das Rechteck im Dokument-Layout angezeigt wird.

- **Einstellungen:**

   - **X- und Y-Koordinaten** Definieren Sie die horizontale und vertikale Platzierung.

   - **Höhe und Breite (in mm):** die Größe des Rechtecks.

2.3. Spanne

Definiert den Abstand um die Rechteckkomponente, um sie von anderen Benutzeroberflächenelementen zu trennen:

- Auffüllen (oben)

- Unten (unten)

- Linksbündig

- Rechtsbündig

2.4. Erscheinungsbild

- **Beschreibung:** Steuert die visuelle Formatierung des Rechtecks.

- **Anpassungsoptionen:**

   - **Fill** Die interne Farbe des Rechtecks.

   - **Kontur** Die Konturfarbe des Rechtecks.

   - **Strichbreite** Die Stärke des Rechteckrahmens.

   - **Style:** voreingestellte Stile wie flach, umrandet oder erhöht.

   - **Kanten:** Steuert das Erscheinungsbild der Ecke (z. B. abgerundete oder scharfe Kanten).

2.5. Vorhandensein

- **Beschreibung:** Gibt an, ob das Rechteck beim Rendern der Kommunikation angezeigt wird.

- **Optionen:**

   - **Sichtbar:** Zeigt das Rechteck zur Laufzeit an.

   - **Ausgeblendet:** Behält den Layout-Bereich bei, ohne das Rechteck anzuzeigen.

## &#x200B;3. Verwendung

Die Komponente „Rechteck“ wird normalerweise für Layout- und Stilzwecke und nicht für die Inhaltseingabe verwendet. Häufige Anwendungsszenarien umfassen:

- Erstellen einer visuellen Trennung zwischen Abschnitten

- Gruppierte Elemente hervorheben

- Verbesserung der Lesbarkeit und des visuellen Gleichgewichts

- Einrahmen von Kopfzeilen, Fußzeilen oder Aufrufabschnitten

Rechtecke können mit anderen Layout-Elementen wie Teilformularen oder Containern für komplexe visuelle Design-Strukturen kombiniert werden.

## 4. Best Practices

- Verwenden Sie konsistente Stile für Rechtecke in Ihrem Layout, um visuelle Harmonie zu gewährleisten.

- Legen Sie ausreichende Ränder und Abstände an, um zu verhindern, dass sich benachbarte Felder überfüllen.

- Wählen Sie Füllungs- und Strichfarben, die mit Ihrer Marke oder Ihrem Dokumentdesign übereinstimmen.

- Verwenden Sie abgerundete Kanten subtil, um die Ästhetik in modernen Benutzeroberflächen-Layouts zu verbessern.

- Blenden Sie Rechtecke aus, wenn sie nur für Entwurfszwecke während der Bearbeitung benötigt werden, aber in der endgültigen Ausgabe nicht erforderlich sind.

Die Rechteckkomponente ist ein nicht interaktives, aber leistungsstarkes Tool im IC-Editor. Wenn sie gestaltet und effektiv positioniert sind, verbessert sie die Layout-Genauigkeit, den visuellen Fluss und das Benutzererlebnis, ohne die Datenbindung oder Interaktivität zu vereinfachen.
