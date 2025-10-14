---
title: PDF-Vorschau im Editor für interaktive Kommunikation mit verschiedenen Datenoptionen
description: PDF-Vorschau im Editor für interaktive Kommunikation mit verschiedenen Datenoptionen zur Vorschau der interaktiven Kommunikation auf drei verschiedene Arten.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
index: false
hidefromtoc: true
source-git-commit: f772a193cce35a1054f5c6671557a6ec511671a9
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 14%

---


# PDF-Vorschau im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Prompts, Beispiele und Best Practices können sich ändern, da Forms Experience Builder im Verlauf des Early-Adopter-Programms weiterentwickelt wird.

Die PDF-Vorschaufunktion ermöglicht Benutzenden die Vorschau von interaktiver Kommunikation auf drei verschiedene Arten: ohne Daten, mit lokalen JSON-basierten Daten oder mit Beispieldaten aus dem konfigurierten Datenmodell.

## Wichtigste Vorteile

- Zeigen Sie eine Vorschau der interaktiven Kommunikation mit Beispieldaten an, um zu sehen, wie Live-Daten beim Zusammenführen mit der Kommunikation aussehen werden.

- Laden Sie lokale JSON-Datendateien hoch, um datengesteuerte Vorschauen ohne Backend-Einrichtung zu generieren.

- Verwenden Sie verbundene Formulardatenmodelle (FDM), um die Echtzeit-Datenintegration mit Beispieldaten während des Designs zu simulieren.

- Wechseln Sie einfach zwischen Datenoptionen (keine Daten, lokale Daten, FDM), um Layout, Struktur und Personalisierung zu validieren.

## PDF-Vorschau im Editor für interaktive Kommunikation mit verschiedenen Datenoptionen

Zeigen Sie eine Vorschau der interaktiven Kommunikation ohne Daten, lokale Daten oder Beispieldaten aus dem konfigurierten Datenmodell an, um flexible Tests und Validierungen zu ermöglichen.

+++&#x200B;1. Vorschau ohne Daten.

1.1. Öffnen Sie Ihre interaktive Kommunikation im IC-Editor.

1.2. Verwenden Sie die PDF-Vorschauoption und wählen Sie die Option **Keine Daten** aus, um eine Kommunikation ohne Daten anzuzeigen.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/nodata.png)

+++

+++&#x200B;2. Vorschau mit lokalen JSON-Daten

2.1. Bereiten Sie eine strukturierte JSON-Datei vor. Als Referenz können Sie die Beispieldaten aus dem für die Kommunikation verwendeten JSON-[&#x200B; (FDM](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/work-with-form-data-model) kopieren.

2.2. Wechseln Sie im IC-Editor zu **PDF-Vorschau** > Lokale Daten verwenden.

2.3. Wählen Sie Ihre JSON-Datei aus und laden Sie sie hoch, um eine PDF-Vorschau mit den bereitgestellten Daten zu rendern.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/localdata.png)

+++

+++&#x200B;3. Vorschau mit Datenmodell 

3.1. Wählen Sie **Mit Datenmodell** aus, um Beispieldaten aus einem bereits konfigurierten Formulardatenmodell (FDM) der IC zu verwenden.

3.2. Die Vorschau füllt automatisch Daten aus Modellfeldern. Stellen Sie sicher, dass die Beispieldaten bei der ersten Verwendung in FDM gespeichert werden oder die Vorschau als Nicht-Daten angezeigt wird.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/datamodel.png)

+++

