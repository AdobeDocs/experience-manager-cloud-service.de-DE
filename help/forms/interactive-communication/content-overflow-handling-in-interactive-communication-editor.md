---
title: Umgang mit Inhaltsüberläufen im Editor für interaktive Kommunikation
description: Die Handhabung von Inhaltsüberläufen im Editor für interaktive Kommunikation verbessert das Verhalten von Text in Layouts mit Flüssen und Positionen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: 371838c77beafa8c67259a865b25325632bea0b0
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 17%

---


# Umgang mit Inhaltsüberläufen im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Prompts, Beispiele und Best Practices können sich ändern, da Forms Experience Builder im Verlauf des Early-Adopter-Programms weiterentwickelt wird.

## Einführung

Die Funktion zur Handhabung von Inhaltsüberläufen im Editor für interaktive Kommunikation verbessert das Verhalten von Text in fließenden und positionierten Layouts. Es sorgt für eine reibungslose Inhaltskontinuität für fortlaufende Layouts und bietet visuelle Warnhinweise für positionierte Layouts, sodass Autoren beim Entwerfen von Nachrichten bessere Kontrolle und Flexibilität haben.

## Schlüsselfunktionen

### Flusslayout

- **Neue Option:**
Fügt eine Eigenschaft **Seitenumbrüche zulassen** innerhalb von Inhalten hinzu, um das Überlaufverhalten zu steuern. Diese Option ist nur sichtbar, wenn das übergeordnete Teilformular auf Fluss eingestellt ist und die Eigenschaft **Seitenumbrüche zulassen** aktiviert ist.

- **Automatische Seitenfortsetzung:**
Wenn der Inhalt den verfügbaren Platz überschreitet, wird automatisch eine neue Seite erstellt, und die Bearbeitung wird nahtlos fortgesetzt.

- **Unterstützung für Kopieren und Einfügen:**
Großer Text, der in den Editor eingefügt wird, fließt automatisch über Seiten, wodurch die Layout-Konsistenz gewahrt bleibt.

### Positioniertes Layout

- **Überlaufanzeige:**
Wenn der Inhalt den Container (Teilformular oder Seite) überschreitet, wird der Texteditor zur Bearbeitung erweitert, die Elementhöhe bleibt jedoch unverändert.

- **Visueller Warnhinweis:**
Am Boden des Containers wird ein roter Rand angezeigt, um den Überlauf anzuzeigen.

- **Manuelle Einstellung:**
Autoren ändern die Größe des Containers manuell, um zusätzliche Inhalte einzupassen.

>[!NOTE]
>
> Für diese Funktion muss die gesamte übergeordnete Hierarchie (z. B. Teilformulare) auf Fluss festgelegt sein. Wenn ein übergeordnetes Teilformular in der Hierarchie positioniert ist, funktioniert **Option „Seitenumbrüche** Inhalt zulassen“ nicht wie erwartet.

## Vorteile

- Verbessert die Effizienz und Kontrolle bei der Inhaltserstellung.

- Gewährleistet ein konsistentes Layout und Lesbarkeit auf allen Seiten.

- Hilft bei der schnellen Identifizierung von Überläufen durch visuelle Indikatoren.

- Verbessert die Flexibilität beim Kommunikationsdesign für beide Layouttypen.
