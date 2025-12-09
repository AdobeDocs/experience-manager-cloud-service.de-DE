---
title: Unterstützung der XDP-Bearbeitung im Editor für interaktive Kommunikation
description: Unterstützung der XDP-Bearbeitung im Editor für interaktive Kommunikation ermöglicht die Bearbeitung vorhandener XDPs im Editor für interaktive Kommunikation.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: 9adc7a5669d8bf1e64cc93998cb2f91ffa9d3dd6
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 13%

---


# Unterstützung der XDP-Bearbeitung im Editor für interaktive Kommunikation

>[!NOTE]
>
> Die interaktive Kommunikationsfunktion ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie von Ihrer Geschäftsadresse eine E-Mail an `aem-forms-ea@adobe.com`, um den Zugriff anzufordern.

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Prompt-Bibliothek wird derzeit mit dem Produkt getestet und unterliegt Aktualisierungen und Überarbeitungen. Prompts, Beispiele und Best Practices können sich ändern, da Forms Experience Builder im Verlauf des Early-Adopter-Programms weiterentwickelt wird.

## Einführung

Der Editor für interaktive Kommunikation (IC) bietet jetzt nahtlose **Unterstützung für die Bearbeitung von XDP-Dateien (XML-Datenpaket** innerhalb der Authoring-Umgebung. Diese Verbesserung ermöglicht es Autorinnen und Autoren, XDP-Vorlagen mühelos zu verwalten, zu ändern und zu pflegen, ohne auf externe Tools angewiesen zu sein. Mit dieser Funktion können Benutzer XDP-Dateien direkt im IC-Editor hochladen, anzeigen und bearbeiten, was einen einheitlichen und effizienten Workflow vom Entwurf bis zur Bereitstellung ermöglicht.

## Verwenden der XDP-Bearbeitungsunterstützung im Editor für interaktive Kommunikation

![IC-Dokument suchen](/help/forms/interactive-communication/assets/support-xdp.png)

1. Navigieren Sie zu **Forms > Forms und Dokumente**.

1. Laden Sie Ihre XDP-Datei mit der Option **Erstellen > Datei hochladen** hoch.

1. Öffnen Sie die XDP-Datei **Editor für interaktive Kommunikation**.

1. Nehmen Sie **erforderlichen Änderungen am Design oder** vor.

1. Wenn Sie Ihre Änderungen speichern, werden Aktualisierungen automatisch in der Quell-XDP-Datei übernommen.

## Schlüsselfunktionen

- **Hochladen und Verwalten von XDP-Dateien:**
Hochladen von XDP-Vorlagen über **Forms Manager**. Nach dem Hochladen sind sie für die direkte Bearbeitung im Editor für interaktive Kommunikation verfügbar.

- **Bearbeiten mit IC-Editor:**
Öffnen und bearbeiten Sie XDPs mit dem IC-Editor mit vollem Zugriff auf vorhandene Bearbeitungsfunktionen, einschließlich Layout-Anpassungen, Datenbindung, Stilen und Komponentenkonfiguration.

- **Zurück zu Source speichern:**
Alle über den IC Editor vorgenommenen Änderungen werden direkt in der ursprünglichen XDP-Datei gespeichert, sodass die Versionsintegrität erhalten bleibt und der Design-Workflow vereinfacht wird.

## Fragmentunterstützung

- **Fragmentverweise:**
Wenn eine XDP auf ein Fragment verweist, muss dieses Fragment in **AEM unter demselben relativen Pfad, wie** der XDP-Datei definiert, vorhanden sein.
Wenn ein Fragment fehlt, zeigt der Editor eine **Warnmeldung** an, die angibt, dass das gewünschte Fragment nicht vorhanden ist.

- **Wiederverwendung von Fragmenten im Editor:**
Alle vorhandenen XDP-Fragmente werden im **Bereich „Fragmente** des IC-Editors angezeigt.
Autoren können **Fragmente direkt** die Arbeitsfläche ziehen und dort ablegen. Die Verweise werden beibehalten, um sicherzustellen, dass Aktualisierungen an Fragmenten über alle XDPs hinweg propagiert werden, die sie verwenden.

## Vorteile

- Beseitigt die Abhängigkeit von externen Tools für die XDP-Bearbeitung.

- Behält vorhandene Datenbindungen und Fragmentbeziehungen bei.

- Ermöglicht konsistentes Design und schnellere Iterationszyklen.

## Best Practices

- Stellen Sie vor der Bearbeitung sicher, dass alle referenzierten Fragmente im richtigen relativen Pfad vorhanden sind.

- Verwenden Sie die Versionskontrolle, um Aktualisierungen über XDP- und Fragmentabhängigkeiten hinweg zu verwalten.

- Überprüfen Sie die Datenbindungen nach der Bearbeitung, um das korrekte Rendering zu bestätigen.

