---
title: Erstellen der ersten interaktiven Kommunikation
description: Entwickeln Sie mit AEM Forms Interactive Communications auf einfache Weise dynamische, datengesteuerte Kommunikationen
feature: Release Information
role: Admin
hide: true
hidefromtoc: true
source-git-commit: a771aa7e683cfbcacc8a9d5765c63d50169a2756
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 52%

---


# Erstellen der ersten interaktiven Kommunikation


>[!VIDEO](https://video.tv.adobe.com/v/3444094/)

## Schritt 1: Planen Sie die interaktive Kommunikation

Der erste Schritt bei der Planung einer interaktiven Kommunikation besteht darin, den Inhalt der interaktiven Kommunikation fertigzustellen. Anschließend müssen Sie den Inhalt analysieren, um die verschiedenen Asset-Typen zu ermitteln, die zum Erstellen der interaktiven Kommunikation erforderlich sind.

### Aspekte bei der Planung

Eine interaktive Kommunikation enthält die folgenden Elemente:

* **Statischer Text** umfasst im Wesentlichen die generischen Teile der interaktiven Kommunikation, die in die Kommunikation mit der gesamten Kundschaft einbezogen werden. Zum Beispiel Kopfzeile, Fußzeile, Anrede oder Haftungsausschluss.

* **Daten aus einem Backend-System (Formulardatenmodell)** sind kundenspezifisch und werden dynamisch mit der interaktiven Kommunikation zusammengeführt. Beispielsweise kann die Richtliniennummer oder Adresse mithilfe eines Formulardatenmodells bezogen werden.

* **Layout oder Vorlagen** für die Druck- und Web-Version der interaktiven Kommunikation.

* **Reihenfolge**, in der die verschiedenen Textabsätze in der interaktiven Kommunikation angezeigt werden.

* **Bedingte Daten**, die basierend auf vordefinierten Bedingungen befüllt werden. Beispielsweise das Datum, an dem die interaktive Kommunikation generiert wird.

* **In einem Repository gespeicherte Bilder** wie Logos und Signaturbilder. Bilder wie das Unternehmenslogo sind in den meisten Fällen bzw. in jeder interaktiven Kommunikation unverändert enthalten.

* **Diagramme und Tabellen** sind erforderlich, um die Darstellung komplexer Daten in einer interaktiven Kommunikation zu vereinfachen.

### Anatomie der interaktiven Kommunikation

Nachdem Sie den Inhalt und die Elemente festgelegt haben, die zum Erstellen Ihrer interaktiven Kommunikation verwendet werden, können Sie eine Anatomie der interaktiven Kommunikation erstellen. Die Anatomie muss über die Details verfügen, die im Abschnitt Planungsüberlegungen aufgeführt sind. Zum Beispiel eine Anatomie der monatlichen Rechnung, die ein Telekommunikationsbetreiber an seine Kunden sendet.

Die Anatomie enthält Daten mit den folgenden Eingabemodi:

* Statischer Text
* Formulardatenmodell
* Bedingte Daten
* Bilder


## Schritt 2: Erstellen eines Formulardatenmodells

Mit einem Formulardatenmodell können Sie eine interaktive Kommunikation mit unterschiedlichen Datenquellen verbinden, z. B. mit AEM-Benutzerprofilen, RESTful-Web-Diensten, SOAP-basierten Web-Diensten, OData-Diensten und relationalen Datenbanken. Ein Formulardatenmodell ist ein einheitliches Datenrepräsentationsschema von Geschäftseinheiten und Diensten, die in verbundenen Datenquellen verfügbar sind. Sie können das Formulardatenmodell mit einer interaktiven Kommunikation verwenden, um Daten aus verbundenen Datenquellen abzurufen. Weitere Informationen zum Formulardatenmodell finden Sie unter [AEM Forms-Datenintegration](/help/forms/data-integration.md).

## Schritt 3: Erstellen Sie Fragmente

Dokumentfragmente sind wiederverwendbare Komponenten einer Korrespondenz, die zum Erstellen einer interaktiven Kommunikation verwendet werden. Dokumentfragmente sind vom Typ „Text“, „Liste“ und „Bedingung“.


## Schritt 4: Erstellen Sie Vorlagen

Der Editor für interaktive Kommunikation bietet mehrere vorkonfigurierte Vorlagen. Sie können diese Vorlagen gemäß den Anforderungen Ihres Unternehmens ändern oder von Grund auf neu erstellen.


## Schritt 5: Erstellen Sie interaktive Kommunikation

Nachdem Sie alle Bausteine wie Formulardatenmodell, Dokumentfragmente und Vorlagen für die Web-Version erstellt haben, können Sie mit dem Erstellen einer interaktiven Kommunikation beginnen. So erstellen Sie eine interaktive Kommunikation:

1. Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Umgebung an.
1. Wechseln Sie zu Forms > Forms und Dokumente
1. Klicken Sie **Erstellen** und wählen Sie **Kommunikationsdokument**. Es wird ein Konfigurationsbildschirm angezeigt, in dem die folgenden Optionen eingerichtet werden:

   | Feld | Beschreibung | Mandatory |
   |-------|-------------|----------|
   | Name | Eindeutige Kennung für die Kommunikation | Ja |
   | Titel | Anzeigename Ihrer Kommunikation | Ja |
   | Beschreibung | Kurze Beschreibung des Zwecks der Mitteilung | Nein |
   | Vorlage | Eine vorkonfigurierte Vorlage auswählen oder von Grund auf neu beginnen | Ja |
   | Tags | Hinzufügen von Metadaten-Tags für eine bessere Organisation | Nein |

1. Wechseln Sie zur Registerkarte „Voreinstellungen“ und konfigurieren Sie die folgenden Optionen:

   | Feld | Beschreibung |
   |-------|-------------|
   | Voreinstellungsliste | Wählen Sie eine vorkonfigurierte Vorgabe für die Größe des Dokuments aus. Zu den gebräuchlichen Optionen gehören A4, Letter und mehr. |
   | Voreinstellung – Breite | Zeigt die Voreinstellungsbreite für die ausgewählte Voreinstellungsliste an. |
   | Voreinstellung – Höhe | Zeigt die voreingestellte Höhe für die ausgewählte Voreinstellungsliste an. |
   | Vorgabeneinheit | Wählen Sie die Maßeinheit für die Abmessungen des Dokuments (z. B. Millimeter, Zoll). |
   | Ausrichtung voreinstellen | Wählen Sie die Ausrichtung des Dokuments - Hochformat oder Querformat. |

1. Klicken Sie auf **Erstellen**. Die Mitteilung wird im Editor geöffnet.
1. Ziehen Sie Komponenten und Fragmente per Drag-and-Drop, um die interaktive Kommunikation zu entwerfen.

   * Verwenden Sie **Musterseite** für den Inhalt, der für alle Seiten gleich ist. Musterseiten dienen der Formatierung von Seiten und helfen, die Designkonsistenz zu erhöhen, da sie Hintergrund- und Layoutformate für mehr als eine Seite in einem Dokumententwurf bereitstellen können.

   * Verwenden **Seiten**, um Inhalt und Layout Ihres Dokuments zu gestalten. Jede Seite wird von einer Musterseite abgeleitet, und standardmäßig ist jede Seite mit der von Designer erstellten Musterseite verknüpft.


1. Verwenden Sie die `@` Notation, um Datenfelder basierend auf dem verbundenen Datenmodell automatisch zu vervollständigen.
1. Verwenden Sie die Option `PDF Preview` , um eine Vorschau des Dokuments zusammen mit Daten anzuzeigen. Sie benötigen die Datendatei im JSON-Format.
