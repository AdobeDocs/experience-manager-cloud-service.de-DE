---
title: Dynamische Seitennummerierung im Editor für interaktive Kommunikation
description: Mit der dynamischen Seitennummerierung im Editor für interaktive Kommunikation können Autorinnen und Autoren automatisch Seitennummern in ihrer PDF-Ausgabe anzeigen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
index: false
hidefromtoc: true
source-git-commit: dae482e1f57a3504bf08926b57b89ca9266bd36a
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 19%

---


# Dynamische Seitennummerierung im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Prompts, Beispiele und Best Practices können sich ändern, da Forms Experience Builder im Verlauf des Early-Adopter-Programms weiterentwickelt wird.

## Einführung

Mit der Funktion für die dynamische Seitennummerierung in der interaktiven Kommunikation (IC) können Autoren automatisch Seitennummern in ihrer PDF-Ausgabe anzeigen. Die Seitennummerierung kann auf der Masterseitenebene aktiviert werden, um eine konsistente Nummerierung über alle zugehörigen Designseiten hinweg sicherzustellen. Dies hilft, während der mehrseitigen Kommunikation ein klares Seiten-Tracking und ein professionelles Layout beizubehalten.

## Schlüsselfunktionen

- **Konfiguration der Musterseite:**
Die Seitennummerierung kann auf der Masterseitenebene aktiviert werden. Die Komponente kann an einer beliebigen Stelle auf der Arbeitsfläche platziert werden, nachdem sie abgelegt und frei angepasst wurde, da sie alle in der Textkomponente verfügbaren Eigenschaften unterstützt.

- **Automatische Platzierung:**
Unten in der Mitte jeder Seite wird eine Seitennummerierungskomponente im folgenden Format angezeigt:
&quot;**Page # of ##**&quot;

   - Die erste **#** stellt die aktuelle Seitenzahl dar.

   - Die zweite **##** stellt die Gesamtzahl der Seiten in der Kommunikation dar.

- **Dynamische Anzeige in der PDF-Vorschau:**
Die Seitenzahlen werden während der PDF-Vorschau dynamisch gerendert, sodass in der endgültigen Ausgabe eine genaue Seitennummerierung angezeigt wird.

### Beispiel

Bei der Vorschau einer 5-seitigen interaktiven Kommunikation wird jede Seite angezeigt:

Seite 1 von 5

Seite 2 von 5

… und so weiter, die während der PDF-Generierung dynamisch aktualisiert werden.

## Wichtigste Vorteile

- Verbessert die Lesbarkeit und Professionalität von Dokumenten.

- Automatisiert die Seitennummerierung ohne manuelles Eingreifen.

- Konsistenz über alle mit einer Musterseite verknüpften Seiten hinweg.
