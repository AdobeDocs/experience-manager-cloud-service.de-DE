---
title: Index Converter
description: Index Converter
exl-id: ac02ca41-eb35-4f24-bf17-d00ce318423d
source-git-commit: 92c123817a654d0103d0f7b8e457489d9e82c2ce
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 70%

---

# Index Converter {#index-converter}

Index Converter ist ein Dienstprogramm, das entwickelt wurde, um die Indexdefinitionen eines Kunden zu migrieren, um die Umstellung auf AEM as a Cloud Service vorzubereiten.

## Einführung {#introduction}

Mit Index Converter können AEM-Entwickler bestehende benutzerdefinierte Oak-Indexdefinitionen in AEM as a Cloud Service-kompatible benutzerdefinierte Oak-Indexdefinitionen migrieren.

>[!NOTE]
>Index Converter transformiert nur Oak-Indexdefinitionen des Typs *lucene*, die unter `/apps` oder `/oak:index` vorhanden sind. Es werden keine *lucene*-Typindizes transformiert, die für `nt:base` erstellt werden.

Es gibt zwei Möglichkeiten, benutzerdefinierte Oak-Indexdefinitionen zu erstellen:

* `under /apps` (über ein beliebiges benutzerdefiniertes Inhaltspaket)
* direkt unter dem Pfad `/oak:index`

Wenn [Oak-Index sicherstellen](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) verwendet wurde, stellen Sie sicher, dass Definitionen auf AEM as a Cloud Service nicht unterstützt werden. Daher müssen sie zuerst in Oak-Indexdefinitionen konvertiert und dann gemäß den folgenden Richtlinien zu benutzerdefinierten Oak-Indexdefinitionen migriert werden, die mit AEM as a Cloud Service kompatibel sind:

* Wenn die Eigenschaft „ignore“ auf `true` festgelegt ist, ignorieren bzw. überspringen Sie die Ensure-Definition.
* Aktualisieren Sie den `jcr:primaryType` auf `oak:QueryIndexDefinition`.
* Entfernen Sie alle Eigenschaften, die gemäß OSGi-Konfigurationen ignoriert werden sollen.
* Entfernen Sie die Unterstruktur `/facets/jcr:content` aus der Ensure-Definition.

## Verwenden von Index Converter {#using-index-converter}

* Über Adobe I/O CLI : Es wird empfohlen, den Index Converter über `aio-cli-plugin-aem-cloud-service-migration` (AEM as a Cloud Service Code-Refaktorierungs-Plug-in für die Adobe I/O-CLI).

  Unter **[Git-Ressource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** erfahren Sie, wie Sie das Plug-in installieren und verwenden.

* Als eigenständiges Dienstprogramm: Index Converter kann auch als eigenständiges Dienstprogramm ausgeführt werden.

  Unter **[Git-Ressource: aem-cs-source-migration-index-converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)** erfahren Sie, wie dieses Tool verwendet wird.
