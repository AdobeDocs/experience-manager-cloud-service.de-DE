---
title: Vorlagensperre im Editor für interaktive Kommunikation
description: Vorlagensperre im Editor für interaktive Kommunikation bietet den Vorlagenautoren die Möglichkeit, das Layout oder den Inhalt für die Dokumentautoren zu sperren.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: 371838c77beafa8c67259a865b25325632bea0b0
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 11%

---


# Vorlagensperre im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Prompts, Beispiele und Best Practices können sich ändern, da Forms Experience Builder im Verlauf des Early-Adopter-Programms weiterentwickelt wird.

## &#x200B;1. Einführung

Mit der Vorlagensperrfunktion im Editor für interaktive Kommunikation (IC) können Vorlagenautoren Änderungen auf bestimmte Elemente einer Kommunikationsvorlage beschränken. Dadurch wird die Konsistenz des Designs sichergestellt, kritische Inhalte geschützt und die Governance in Teams durchgesetzt, die Vorlagen zur Erstellung personalisierter Kommunikation wiederverwenden.

Wenn sie angewendet werden, erscheinen gesperrte Komponenten visuell unterschiedlich und können von nachgelagerten Autoren oder Mitwirkenden nicht geändert werden, abhängig vom festgelegten Sperrtyp. Diese Funktion hilft bei der Aufrechterhaltung von Markenstandards, Datenintegrität und Einheitlichkeit des Layouts in allen abgeleiteten Kommunikationen.

## &#x200B;2. Sperrtypen

Vorlagenautoren können Inhalts- und Layout-Sperren einzeln oder gemeinsam anwenden, um Inhalts- und Layout-Änderungen in Vorlagen für interaktive Kommunikation zu steuern:

### 2.1 Inhaltssperre

Eine Inhaltssperre beschränkt alle Änderungen am Inhalt oder an den Eigenschaften des ausgewählten Elements. Dieser Sperrtyp stellt sicher, dass wichtige Daten-, Text- oder Designeigenschaften unverändert bleiben, auch wenn sie in mehreren Kommunikationen wiederverwendet werden.

Wenn angewendet, können Autoren Folgendes nicht ändern:

- Textinhalt oder Beschriftungen

- Einstellungen für das Erscheinungsbild (Schriftart, Farbe, Hintergrund, Rahmen usw.)

- Konfigurationen für die Datenbindung

- Bestandteile innerhalb einer Container-Komponente (z. B. Teilformulare)

### 2.2 Layoutsperre

Eine Layout-Sperre schränkt Änderungen in Bezug auf die Position und Größe eines Elements ein. Dadurch wird sichergestellt, dass die visuelle Ausrichtung und Design-Hierarchie mit Marken- oder Dokumentstandards konsistent bleiben.

Wenn sie angewendet werden, können Autoren:

- Element an eine neue Position auf der Seite verschieben

- Ändern der Breite oder Höhe des Elements

## &#x200B;3. Verhalten in abgeleiteten Kommunikationen

- Wenn eine Kommunikation über eine gesperrte Vorlage erstellt wird, werden die gesperrten Elemente im IC-Editor für Kommunikationsautoren als schreibgeschützt angezeigt.

- Bei Komponenten mit Inhaltssperre können die inneren Eigenschaften oder Bindungen nicht geändert werden.

- Komponenten mit Layout-Sperre können nicht verschoben oder in der Größe verändert werden.

Auf diese Weise können Vorlagenersteller die Kontrolle über Design und Struktur behalten und gleichzeitig anderen Benutzern die Möglichkeit geben, sich auf variable Inhalte und datengesteuerte Anpassungen zu konzentrieren.

## 4. Best Practices

- **Kritische Komponenten frühzeitig sperren** Verwenden Sie Sperren für Kopf- und Fußzeilen, Haftungsausschlüsse und Logos, um die Einhaltung von Vorschriften und die Markenidentität zu wahren.

- **Inhaltsblöcke für Genauigkeit verwenden** Schützen Sie Felder, die an zentrale Datenmodelle oder Gesetzestexte gebunden sind.

- **Verwenden Sie Layout-Sperren, um Konsistenz zu gewährleisten**: Vermeiden Sie falsche Ausrichtung oder visuelle Verzerrungen in häufig wiederverwendeten Vorlagen.

- **Nutzung von Sperren mitteilen:** Stellen Sie sicher, dass nachgelagerten Benutzern bewusst ist, welche Abschnitte absichtlich eingeschränkt sind, um Verwirrung zu vermeiden.
