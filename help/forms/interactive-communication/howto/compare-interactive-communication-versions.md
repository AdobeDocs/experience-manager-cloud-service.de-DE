---
title: Versionen der interaktiven Kommunikation vergleichen
description: Erfahren Sie, wie Sie zwei Versionen einer interaktiven Kommunikation nebeneinander als PDF-Vorschau öffnen, um Layout- und Inhaltsunterschiede vor der Veröffentlichung zu untersuchen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="Gilt für AEM Forms."
exl-id: compare-interactive-communication-versions
source-git-commit: b11e1b28aabba9e03553dc9e9394bff111facfee
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 2%

---


# Versionen der interaktiven Kommunikation vergleichen

Wenn eine interaktive Kommunikation mehrere Bearbeitungsdurchgänge durchläuft, kann es schwierig sein, genau zu wissen, was sich zwischen zwei gespeicherten Zuständen geändert hat. Sie können jede beliebige Version in der PDF-Vorschau nebeneinander öffnen, sodass Sie Layout-Verschiebungen, Komponenten-Hinzufügungen oder -Entfernungen und statische Inhaltsänderungen problemlos erkennen können, ohne jede Version einzeln öffnen oder Screenshots manuell vergleichen zu müssen.

| Wer? | Vorteil |
|-----|---------|
| **Autor (Designer für interaktive Kommunikation / Inhaber)** | Überprüfen Sie vor der Veröffentlichung, ob die Änderungen zwischen den Überprüfungszyklen die erwarteten Änderungen erzeugt haben. |
| **Inhaltsvalidierer** | Bestätigen Sie, dass in den Autorenüberarbeitungen das Feedback von einer früheren Version berücksichtigt wurde, ohne dass neue Probleme eingeführt wurden. |

>[!NOTE]
>
> Dieser Vergleich behandelt **nur Layout und statische Inhalte**. Dynamische Feldwerte, die zur Laufzeit ausgefüllt werden, werden in der Vergleichsansicht nicht gerendert.

## Bevor Sie beginnen

Stellen Sie sicher, dass Sie mindestens eine Version der interaktiven Kommunikation gespeichert haben, die Sie mit dem aktuellen Design vergleichen möchten.

Um eine Version zu erstellen, öffnen Sie **Forms und Dokumente**, wählen Sie die interaktive Kommunikation aus, öffnen Sie das Bedienfeld **Zeitleiste** in der linken Leiste und klicken Sie auf **Als Version speichern**. Eine [ Anleitung finden Sie unter „Versionierung und Kommentare ](/help/forms/interactive-communication/versioning-and-commenting-in-interactive-communication-editor.md) Editor für interaktive Kommunikation“.

Aktualisieren Sie nach dem Speichern der Version die interaktive Kommunikation im Editor, sodass sich das aktuelle Design von der gespeicherten Version unterscheidet. Sie benötigen sowohl eine gespeicherte Version als auch einen geänderten aktuellen Status, bevor Sie sie vergleichen können.

## Aktualisieren der interaktiven Kommunikation

Öffnen Sie nach dem Erstellen einer Version die interaktive Kommunikation im Editor für interaktive Kommunikation und nehmen Sie Ihre Design-Aktualisierungen vor.

Nach dem Speichern von **Version 1 der interaktiven Bankkommunikation** können Sie beispielsweise das Banklogo aktualisieren, die Darlehensdetails überarbeiten und die Fahrzeuginformationen in der Tabelle ändern:

- Ersetzen Sie den textbasierten Bankheader durch ein Banklogo-Bild.
- Aktualisieren Sie Darlehensdetails wie die Referenznummer des Antrags, den genehmigten Darlehensbetrag, die Darlehensdauer und das EWI-Startdatum
- Aktualisieren Sie den **Hersteller und Modell** und den Händlernamen in der Tabelle „Fahrzeugdetails“

![Interaktive Kommunikation aktualisiert](/help/forms/interactive-communication/assets/compare-ic1.png)

Klicken Sie **Bearbeitung** Speichern“. Das aktuelle Design kann jetzt mit der gespeicherten Version verglichen werden.

## Vergleichen von zwei Versionen

1. Navigieren Sie zu **Forms und Dokumente** und wählen Sie die interaktive Kommunikation aus, die Sie vergleichen möchten.

1. Öffnen Sie **Bedienfeld** Zeitleiste“ in der linken Leiste.

1. Suchen Sie in der Zeitleiste die gespeicherte Version, die Sie vergleichen möchten. Wählen Sie beispielsweise **Bank Interactive Communication Version 1** mit dem Kommentar **Diese Version enthält ein neues Banklogo und aktualisierte Details**.

1. Klicken Sie **Mit aktueller Version vergleichen**.

   ![Mit aktueller Version vergleichen](/help/forms/interactive-communication/assets/compare-ic2.png)

   Eine neue Registerkarte wird geöffnet, auf der beide Versionen nebeneinander als PDF-Vorschau angezeigt werden. Die gespeicherte Version wird auf der linken Seite und die aktuelle Version auf der rechten Seite angezeigt.

   ![Seitenvergleich](/help/forms/interactive-communication/assets/comapre-ic3.png)

   Scrollen Sie durch beide Vorschaubilder, um Layout- und Inhaltsunterschiede Seite für Seite zu überprüfen. Der Vergleich hebt beispielsweise Änderungen am Banklogo, an den Darlehensdetails und an Fahrzeuginformationen wie dem Automodell und dem Händlernamen hervor.

## Überlegungen

- **Große Textblöcke:** Wenn ein Absatz oder Textblock neu geschrieben oder angeordnet wurde, werden beide Seiten identisch mit ihrer Quell-PDF gerendert. Es gibt keinen Inline-Textvergleich, der Vergleich ist nur visuell und geänderter Text ist nicht gekennzeichnet.

- **Dynamische Daten:** Dynamische Feldwerte sind nicht im Vergleich enthalten. Nur das statische Layout und der Inhalt jeder Version sind sichtbar.

## Häufig gestellte Fragen

**Wie viele Versionen kann ich gleichzeitig vergleichen?**
Sie können zwei Versionen gleichzeitig vergleichen - die ausgewählte Version und die aktuelle Version. Sie werden nebeneinander in einer neuen Registerkarte geöffnet.

**Kann ich eine Version mit einer anderen Version als der aktuellen vergleichen?**
Der Versionsselektor vergleicht immer mit der aktuellen Version. Um zwei nicht aktuelle Versionen zu vergleichen, stellen Sie vorübergehend die ältere Version wieder her und verwenden Sie dann erneut **Mit aktueller Version vergleichen**.

**Ist es möglich, die Vergleichsansicht herunterzuladen oder zu exportieren?**
Anzahl Der Seitenvergleich ist nur ein visuelles Überprüfungswerkzeug - er kann nicht aus dem Editor exportiert werden.

## Siehe auch

- [Versionierung und Kommentare im Editor für interaktive Kommunikation](/help/forms/interactive-communication/versioning-and-commenting-in-interactive-communication-editor.md)
- [Überprüfen und Kommentieren einer interaktiven Kommunikation](/help/forms/interactive-communication/howto/review-and-annotate-interactive-communication.md)
- [Erstellen einer interaktiven Kommunikation](/help/forms/interactive-communication/create-interactive-communication.md)

