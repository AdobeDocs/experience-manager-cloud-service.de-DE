---
title: Erstellen einer dynamischen Tabelle im Editor für interaktive Kommunikation
description: Erstellen Sie eine Funktion für dynamische Tabellen, mit der Autoren datengesteuerte Tabellen erstellen können.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="Gilt für AEM Forms)."
source-git-commit: 322183c28719db5b8657d9532ef234e1d18821cd
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---


# Erstellen einer dynamischen Tabelle im Editor für interaktive Kommunikation

## Überblick

Der Editor für interaktive Kommunikation bietet eine dynamische Tabelle
Funktion, mit der Autoren datengesteuerte Tabellen erstellen können, deren Inhalt zur Laufzeit automatisch aus strukturierten Datenquellen gefüllt wird.

Im Gegensatz zu statischen Tabellen, bei denen Zeilen manuell erstellt werden müssen, werden dynamische Tabellen basierend auf den aus einer gebundenen Datenquelle zurückgegebenen Datensätzen automatisch erweitert oder kontrahiert. Dies macht sie für Szenarien wie Abrechnungen, Transaktionsverläufe, Produktlisten oder Richtlinienpläne nützlich.

In diesem Artikel wird erläutert, wie Sie eine dynamische Tabelle mit Datenbindung einfügen und konfigurieren, den mehrseitigen Tabellenfluss verwalten und die Zeilenanzahl validieren.

## Dynamische Tabelle einfügen

1. Öffnen Sie den **Editor für interaktive Kommunikation**.
1. Ziehen Sie **Tabellenkomponente** **aus dem Bedienfeld „Komponente** in die
Arbeitsfläche.
1. Geben Sie die **Anzahl der Spalten** und **Anfangszeilen** im Dialogfeld an, stellen Sie sicher, dass die **Kopfzeile** enthalten ist, und klicken Sie dann auf OK , um die Tabelle zu erstellen.

### Binden von Daten an die dynamische Tabelle

Dynamische Tabellen füllen Zeilen automatisch aus, indem sie an eine wiederholbare Datenquelle gebunden werden.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/databinding-in-table.png)

Binden von Daten an die Tabelle:

1. Wählen Sie die **Tabellenzeile** im Bedienfeld Hierarchie aus.

1. Öffnen Sie **Seitenbereich die** Datenbindung“.

1. Stellen Sie sicher, dass das ausgewählte Datenschema vom Array-Typ ist.

1. Ziehen Sie das Array-Datenschema auf die ausgewählte Tabellenzeile, um die Daten zu binden.

### Seitenfluss aktivieren

Dynamische Tabellen können über eine einzelne Seite hinaus erweitert werden. Damit die Tabelle wachsen und sich über Seiten hinweg fortsetzen kann, platzieren Sie sie in einem Container mit **fortlaufenden Inhalten**.

![IC-Dokument suchen](/help/forms/interactive-communication/assets/table-data-binding.png)

So aktivieren Sie den Seitenfluss:

1. Wählen Sie den **übergeordneten Layout-Container** der Tabelle aus.

1. Öffnen Sie das Bedienfeld Eigenschaften und legen Sie für den Inhaltstyp &quot;**&quot;**.

1. Wählen Sie die Tabelle aus und stellen Sie sicher, dass sie auch für die Unterstützung von fortlaufenden Inhalten konfiguriert ist.

1. Zeigen Sie eine Vorschau der Kommunikation an, um sich zu vergewissern, dass die Tabelle beim Rendern zusätzlicher Zeilen auf der nächsten Seite fortgesetzt wird.

### Seitenumbruch in Tabelle zulassen

![IC-Dokument suchen](/help/forms/interactive-communication/assets/table-data-binding.png)

So stellen Sie sicher, dass die Tabelle ordnungsgemäß auf mehrere Seiten aufgeteilt ist:

1. Wählen Sie auf **Arbeitsfläche** Tabelle“ aus.
1. Öffnen Sie das Bedienfeld **Eigenschaften**.
1. Aktivieren **Seitenumbruch im Inhalt zulassen**.

Wenn diese Option aktiviert ist, wird die Tabelle automatisch am Ende einer Seite umgebrochen und auf der nächsten Seite fortgesetzt, wobei die Kopfzeile wiederholt wird.

### Konfigurieren der Zeilenvalidierung

Sie können steuern, wie viele Zeilen die dynamische Tabelle rendern kann.

* **Mindestzeilen:**, dass die Tabelle mindestens die angegebene Anzahl von Zeilen rendert.
* **Maximale Zeilen:** Begrenzt die Gesamtzahl der aus der Datenquelle gerenderten Zeilen.
* **Erste Zeilen:** Legt fest, wie viele Zeilen während der Entwurfszeitvorschau im Editor angezeigt werden.

>[!NOTE]
>
> Das Festlegen **Anfangszeilen** auf etwa **3-5** bietet eine realistischere Layout-Vorschau, bevor Laufzeitdaten angewendet werden.

## Schlüsselfunktionen

* Spaltendatenbindung: Binden Sie jede Spalte an ein Feld im Datenmodell.

* Fließender Inhalt: Ermöglicht die Erweiterung und Fortsetzung der Tabelle über Seiten hinweg.

* Unterstützung für Seitenumbrüche: Aktiviert Seitenumbrüche innerhalb der Tabelle auf Zeilenebene.

* Mindestanzahl von Zeilen: Stellt sicher, dass eine Mindestanzahl von Zeilen gerendert wird.

* Maximale Anzahl von Zeilen: Begrenzt die Gesamtzahl der aus der Datenquelle gerenderten Zeilen.

* Anfangszeilen: Definiert die Standardzeilen, die während der Entwurfszeitvorschau angezeigt werden.

Mit der Funktion „Dynamische Tabelle“ im Editor für interaktive Kommunikation können Autoren flexible, datengesteuerte Tabellen erstellen, ohne benutzerdefinierten Code zu schreiben. Durch Bindung der Tabelle an ein Daten-Array, Aktivierung von fortlaufenden Inhalten, Zulassen von Seitenumbrüchen und Konfiguration der Zeilenvalidierung können Autoren strukturierte Kommunikation erstellen, die sich problemlos an unterschiedliche Datenmengen anpasst, während ein konsistentes Layout beibehalten wird.
