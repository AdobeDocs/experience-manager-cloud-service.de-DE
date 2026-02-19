---
title: LINE-Komponente im Editor für interaktive Kommunikation
description: Mit der Linienkomponente im Editor für interaktive Kommunikation in AEM Forms können Autorinnen und Autoren horizontale oder vertikale Linien in ein Kommunikationslayout einfügen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: 1ff5ac22-d8c8-4109-8334-217dbc239f1f
source-git-commit: cdaceaabb8eeeec931b1897e1161f408606540b9
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 3%

---

# LINE-Komponente im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

## &#x200B;1. Einführung

Mit der Linienkomponente im Editor für interaktive Kommunikation (IC) können Autorinnen und Autoren horizontale oder vertikale Linien in ein Kommunikationslayout einfügen. Diese Linien helfen bei der visuellen Segmentierung von Inhalten, der Verbesserung der Lesbarkeit oder der Hervorhebung der Formularstruktur. Mit anpassbaren Stilen wie durchgezogenen Linien oder Unterstrichen und flexibler Positionierung kann die Linienkomponente sowohl für funktionale als auch für ästhetische Zwecke im Formularentwurf verwendet werden.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/line.png)

## &#x200B;2. Eigenschaften

Die Linienkomponente verfügt über eine Reihe konfigurierbarer Eigenschaften, um ihre Identität, ihr Erscheinungsbild, ihre Platzierung und Sichtbarkeit innerhalb des Dokuments zu definieren.

2.1. Grundfeld

- **Name:** Eine eindeutige Kennung, die intern verwendet wird, um auf die LINE-Komponente in Datenmodellen, Regeln oder Skripten zu verweisen.

- **Darstellungstyp** Wählen Sie aus, wie die Linie im Formular angezeigt werden soll.

   - **Keine:** Es wird keine Zeile angezeigt.

   - **Durchgezogenes Feld** Rendert die Linie als durchgezogenes Feld, das normalerweise als Trennzeichen verwendet wird.

   - **Unterstreichen:** Zeichnet eine Unterstreichung, die normalerweise unter Überschriften oder Feldern verwendet wird.

2.2. Lage

- **Beschreibung:** Definiert die physische Platzierung der Zeile im Formular-Layout.

- **Einstellungen:**

   - **X- und Y-Koordinaten:** Legt die horizontale und vertikale Positionierung fest.

   - **Höhe und Breite:** Legen Sie die Länge und Stärke der Linie (in mm) fest.

2.3. Spanne

- **Beschreibung:** Fügt einen Abstand um die Linienkomponente hinzu, um die Layoutdichte zu steuern.

- **Optionen:**

   - Oben

   - Unten

   - Linksbündig

   - Rechtsbündig

2.4. Erscheinungsbild

- **Beschreibung:** Ermöglicht die Gestaltung der Zeile entsprechend dem Dokumententwurf.

- **Optionen:**

   - **Strich** Definiert die Farbe und Stärke des Strichs.

   - **Breite:** Legt fest, wie breit sich die Linie über das Formular erstreckt.

   - **Style:** Sie zwischen den Stilen Gestrichelt, Punkte oder Durchgezogene Linien.

2.5. Vorhandensein

- **Beschreibung:** Steuert die Sichtbarkeit der Linienkomponente während der Laufzeit.

- **Optionen:**

   - **Sichtbar:** Die Zeile wird in der endgültigen Ausgabe gerendert.

   - **Ausgeblendet:** Die Zeile wird nicht angezeigt, ihr Layout-Bereich bleibt jedoch erhalten.

## &#x200B;3. Verwendung

Die LINE-Komponente wird häufig verwendet, um:

- Abschnitte in einer langen Form visuell unterteilen

- Kopfzeilen oder Beschriftungen zur Hervorhebung unterstreichen

- Erstellen von Rahmen oder Feldern um Feldergruppen

- Verbessern der visuellen Hierarchie des Kommunikationslayouts

## 4. Best Practices

- Verwenden Sie im gesamten Formular konsistente Linienstile, um ein professionelles Erscheinungsbild beizubehalten.

- Passen Sie die Ränder an, um visuelles Durcheinander zu vermeiden und die Ausrichtung sicherzustellen.

- Wählen Sie die passenden Strich- und Stileinstellungen für das Marken- oder Dokumentendesign.

- Unnötige Linien ausblenden, um Ablenkungen zu vermeiden und gleichzeitig den Layout-Abstand beizubehalten.

Die LINE-Komponente im Editor für interaktive Kommunikation ist ein einfaches, aber leistungsstarkes Design-Element. Bei strategischer Verwendung verbessert es die visuelle Struktur von Kommunikationsdokumenten, unterstützt Benutzende dabei, besser durch Inhalte zu navigieren, und sorgt für ein saubereres, klareres Layout.
