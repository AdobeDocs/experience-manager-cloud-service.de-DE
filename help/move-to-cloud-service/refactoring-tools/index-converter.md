---
title: Index Converter
description: Index Converter
exl-id: e6a3ec6d-cc02-4f5b-8b1d-ea481d6884ca
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 100%

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

Wenn [Ensure Oak Index](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) verwendet wurde, beachten Sie bitte, dass in AEM as a Cloud Service Ensure-Definitionen nicht unterstützt werden. Daher müssen sie zuerst in Oak-Indexdefinitionen konvertiert und dann zu benutzerdefinierten Oak-Indexdefinitionen migriert werden, die gemäß den folgenden Richtlinien mit AEM as a Cloud Service kompatibel sind:

* Wenn die Eigenschaft „ignore“ auf `true` festgelegt ist, ignorieren bzw. überspringen Sie die Ensure-Definition.
* Aktualisieren Sie den `jcr:primaryType` auf `oak:QueryIndexDefinition`.
* Entfernen Sie alle Eigenschaften, die gemäß OSGi-Konfigurationen ignoriert werden sollen.
* Entfernen Sie die Unterstruktur `/facets/jcr:content` aus der Ensure-Definition.

## Verwenden von Index Converter {#using-index-converter}

* Über die Adobe I/O-CLI: Es wird empfohlen, Index Converter via `aio-cli-plugin-aem-cloud-service-migration` (AEM as a Cloud Service-Code-Refactoring-Plug-in für die Adobe I/O-CLI) zu verwenden.

   Siehe **[Git-Ressource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)**, um zu erfahren, wie Sie das Plug-in installieren und verwenden.

* Als eigenständiges Dienstprogramm: Index Converter kann auch als eigenständiges Dienstprogramm ausgeführt werden.

   Unter **[Git-Ressource: aem-cs-source-migration-index-converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)** erfahren Sie, wie dieses Tool verwendet wird.
