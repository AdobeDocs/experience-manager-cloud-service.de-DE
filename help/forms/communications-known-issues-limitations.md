---
title: 'Bekannte Probleme '
description: Best Practices für die Kommunikation, bekannte Probleme und Einschränkungen
source-git-commit: 06da7d2a5063e163aa1534bedbc79ae50ef27515
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 79%

---


# Häufig gestellte Fragen, Best Practices, bekannte Probleme und Einschränkungen {#best-practices-known-issues-and-limitations}

Bevor Sie mit der Verwendung von Kommunikations-APIs beginnen, sollten Sie die folgenden bekannten Probleme und Einschränkungen lesen:

## Bekannte Probleme

- Sie können einen bestimmten Rendertyp (PDF, PRINT) nur einmal in der Liste der Druckoptionen verwenden. Beispielsweise können Sie nicht über zwei PRINT-Optionen verfügen, die jeweils einen PCL-Rendertyp angeben.

- Für eine Batch-Konfiguration ist nur eine Instanz der Kombination von Werten von OutputType (PDF, PRINT) und RenderType (PostScript, PCL, IPL, ZPL usw.) zulässig.

## Best Practices

- Adobe empfiehlt, Datendateien im Blob-Container-Store in der von AEM Cloud Service verwendeten Cloud-Region zu hosten.

## Häufig gestellte Fragen  {#faq}

**Kann ich einen überwachten Ordner oder andere Speichermechanismen verwenden, um Eingabe und Ausgabe zu speichern?**

Derzeit können Sie den Microsoft Azure-Speicher verwenden, um Eingabedaten und generierte Dokumente zu speichern. Der Microsoft Azure-Speicher bietet verschiedene Optionen zur [Automatisierung von Datenverschiebungsvorgängen](https://docs.microsoft.com/de-de/azure/storage/common/storage-use-azcopy-v10).

**Ist ein Microsoft Azure-Speicherkonto in der Experience Manager Forms Cloud Service-Lizenz enthalten?**

Das Microsoft Azure-Speicherkonto ist unabhängig von der Experience Manager Forms Cloud Service-Lizenz.

**Speichern Kommunikation-APIs Daten auf Experience Manager Forms Cloud Service-Servern?**

Eingabe- und Ausgabedaten werden nur im Microsoft Azure-Speicher gespeichert.

**Sind Kommunikations-APIs nur für Experience Manager Forms Cloud Service verfügbar? Kann ich ähnliche Funktionen in der On-Premise-Umgebung erhalten?**

Sie können den AEM Forms Output-Service verwenden, um eine Vorlage (XFA oder PDF) mit Kundendaten zu kombinieren und Dokumente in den Formaten PDF, PS, PCL und ZPL zu generieren.

Im Vergleich zur On-Premise-Umgebung bietet Cloud Service zusätzliche Vorteile durch automatische Skalierung und Kosteneffizienz.

<!--**Where is data processed?**

**Who has access to data?**

**Is data encrypted?**

**Where is data hosted?** -->

**Kann ich mehrere Batch-Vorgänge gleichzeitig ausführen?**
Ja, Sie können mehrere Batch-Vorgänge gleichzeitig ausführen. Verwenden Sie immer unterschiedliche Quell- und Zielordner für jeden Vorgang, um Konflikte zu vermeiden.
