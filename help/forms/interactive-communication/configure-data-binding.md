---
title: Erstellen eines interaktiven Kommunikationsfragments
description: Erstellen Sie interaktive Kommunikationsfragmente in AEM Forms, um modulare, wiederverwendbare Inhaltsbausteine zu erstellen, die Konsistenz gewährleisten, Zeit sparen und personalisierte, datengesteuerte Kommunikation unterstützen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
index: false
hidefromtoc: true
source-git-commit: 9adc7a5669d8bf1e64cc93998cb2f91ffa9d3dd6
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 10%

---


# Datenbindung im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Prompts, Beispiele und Best Practices können sich ändern, da Forms Experience Builder im Verlauf des Early-Adopter-Programms weiterentwickelt wird.

## &#x200B;1. Einführung

Datenbindung im Editor für interaktive Kommunikation verbindet Felder auf der Arbeitsfläche mit einer gesteuerten Datenschicht, sodass Kommunikationen mit echten, kontextuellen Informationen gerendert werden. Durch die Verknüpfung von Komponenten mit einem Formulardatenmodell (FDM) können Autoren Genauigkeit sicherstellen, die manuelle Arbeit reduzieren und dynamische, personalisierte Erlebnisse bereitstellen.

Über die einfache Verbindung von Werten hinaus unterstützt die Datenbindung in IC visuelles Mapping, Vorbefüllen und Synchronisieren, sodass Autoren schneller entwerfen können und gleichzeitig mit Backend-Systemen und Datenmodellen im Einklang bleiben.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/data-binding1.png)

## &#x200B;2. Eigenschaften

2.1 Verwalten von Datenverbindungen (FDM)

- **FDM auswählen:** Wählen Sie das entsprechende Formulardatenmodell (z. B. Kunden, Konten oder Richtlinien). Dadurch wird das autoritative Schema für Felder, Arrays und Objekte festgelegt, die in der Kommunikation verwendet werden.

- **Datenbindung erstellen:** Sobald die Bindungen aktiviert sind, kann jedes Feld mit FDM-Pfaden verknüpft werden, wodurch Fehler minimiert und eine konsistente Integration sichergestellt werden.

- **Binden von Feldern an ein Datenmodell:** Verweisen Sie Felder auf bestimmte Knoten (z. B. customer.name, policy.holder.id), um das Rendering mit Live-Daten zu unterstützen und Validierungen oder bedingte Logik zu unterstützen.

2.2 Datenbindung erstellen

- **Visuelles Mapping** Drag-and-Drop-Zuordnung zwischen Feldern und FDM-Knoten hilft technisch nicht versierten Benutzern, Fehler zu vermeiden.

- **Feldverknüpfung:** den Zielpfad, den Datentyp (Text, Zahl, Datum, boolescher Wert, Bild) und optionale Formatierer (z. B. Datumsmaske, Währung).

- **Bindungsvorschau:** Testen Sie Bindungen mit Beispieldatensätzen, um die Formatierung und Korrektheit vor der Veröffentlichung zu überprüfen.

## &#x200B;3. Verwendung

Die Datenbindung wird häufig verwendet, wenn Kommunikationen autorisierende Datensätze anzeigen oder Benutzereingaben erfassen müssen. Beispiele:

- **Personalization:** Geben Sie Kundendaten wie Namen, Adresse oder Kontostand ein.

- **Bedingter Inhalt:** Ein-/Ausblenden von Abschnitten basierend auf Modellwerten (z. B. aktive oder inaktive Kundinnen und Kunden).

- **Sammlungen und Tabellen:** Wiedergeben von Verläufen, Transaktionen oder Einzelauflistungen aus Arrays.

- **Bilder und Medien:** Binden Sie Profilfotos, Firmenlogos oder Produktbilder.

- **Überprüfen und eSign:** Formulare mit Daten vorab ausfüllen und Aktualisierungen durch bidirektionale Synchronisierung ermöglichen.

Autoren wählen das FDM normalerweise zu Beginn des Projekts aus, ordnen Felder während des Designs visuell zu und testen es vor der Veröffentlichung mit Beispieldaten.

## 4. Best Practices

- **Frühzeitiges Definieren des Schemas:** FDM vor der Bindung abschließen, um eine spätere Neuzuordnung zu vermeiden.

- **Visuelles Mapping verwenden** Vermeiden Sie Tippfehler und nicht übereinstimmende Pfade durch Drag-and-Drop.

- **Datentypen validieren** Wenden Sie Formatierer für Währungen, Datumsangaben oder Telefonnummern an, um Konsistenz zu gewährleisten.

- **Bindungen explizit beibehalten** Jedes Feld sollte eindeutig einem einzelnen Datenknoten zugeordnet sein.

- **Testen mit Beispieldaten:** Vorschau von allgemeinen und Edge-Fällen (z. B. leere Werte, lange Arrays).

- **Zwei-Wege-Synchronisierung begrenzen:** Nur verwenden, wenn Bearbeitungen oder Genehmigungen erforderlich sind.

- **Sammlungen modularisieren** Verwenden Sie Vorlagenzeilen für wiederholbare Strukturen.

- **Vertrauliche Daten schützen** Maskieren, Verschlüsselung und Zugriff mit den geringsten Rechten für personenbezogene Daten oder Zahlungsdetails anwenden.

Durch die sorgfältige Konfiguration der Datenbindung schaffen Autoren eine zuverlässige Brücke zwischen Design und Daten - durch die Beschleunigung der Kommunikationserstellung, die Sicherstellung der Genauigkeit und die Bereitstellung hochgradig personalisierter Erlebnisse in großem Umfang.

