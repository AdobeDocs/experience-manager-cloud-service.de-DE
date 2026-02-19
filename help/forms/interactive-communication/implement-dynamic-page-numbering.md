---
title: Dynamische Seitennummerierung im Editor für interaktive Kommunikation
description: Mit der dynamischen Seitennummerierung im Editor für interaktive Kommunikation können Autorinnen und Autoren automatisch Seitennummern in ihrer PDF-Ausgabe anzeigen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: 9f29da7d-72ad-4737-9ae3-d5cdc4f5ed25
source-git-commit: cdaceaabb8eeeec931b1897e1161f408606540b9
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 4%

---

# Dynamische Seitennummerierung im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

## Einführung

Mit der Funktion für die dynamische Seitennummerierung in der interaktiven Kommunikation (IC) können Autoren automatisch Seitennummern in ihrer PDF-Ausgabe anzeigen. Die Seitennummerierung kann auf der Masterseitenebene aktiviert werden, um eine konsistente Nummerierung über alle zugehörigen Designseiten hinweg sicherzustellen. Dies hilft, während der mehrseitigen Kommunikation ein klares Seiten-Tracking und ein professionelles Layout beizubehalten.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/dynamic-page.png)

## Verwenden der dynamischen Seitennummerierung im Editor für interaktive Kommunikation

1. Öffnen Sie den Editor für interaktive Kommunikation
Öffnen Sie Ihr Projekt Interaktive Kommunikation im IC-Editor.

1. Zur Hauptseite
Die Seitennummerierung kann nur auf der Musterseite aktiviert werden. Navigieren Sie zur primären Seite Ihrer Kommunikation.

1. Seitennummerierung aktivieren
Aktivieren Sie im Bedienfeld Eigenschaften den Umschalter Seitenzahl aktivieren . Dadurch werden automatisch Seitenzahlen zu allen zugehörigen Seiten hinzugefügt.

1. Platzierung anpassen
Die Seitenzahl-Komponente kann an einer beliebigen Stelle auf der Arbeitsfläche platziert werden, nachdem sie mithilfe von Standardtexteigenschaften abgelegt und angepasst wurde.

1. Vorschau in PDF
Seitenzahlen werden nur während der PDF-Vorschau angezeigt, wobei die dynamische Nummerierung auf jeder Seite angezeigt wird.

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
