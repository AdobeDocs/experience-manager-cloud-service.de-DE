---
title: Indexkonverter
description: Indexkonverter
translation-type: tm+mt
source-git-commit: 1117f03b2eff37f8b25726c3dc60d5a3fe98a5d1
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 9%

---


# Indexkonverter {#index-converter}

Index Converter ist ein Dienstprogramm, das entwickelt wurde, um die Indexdefinitionen eines Kunden zu migrieren, um die Umstellung auf AEM als Cloud Service vorzubereiten.

## Einführung {#introduction}

Mit dem Indexkonverter können AEM Entwickler bestehende Custom Oak Index-Definitionen in AEM als Cloud Service kompatible Custom Oak Index-Definitionen migrieren.

>[!NOTE]
>Index Converter transformiert nur *lucene* den Typ Custom Oak Index Definitions, die unter `/apps` oder `/oak:index` vorhanden sind. Es werden keine *lucene*-Typindizes transformiert, die für `nt:base` erstellt werden.

Es gibt zwei Möglichkeiten, benutzerdefinierte Oak-Indexdefinitionen zu erstellen:

* `under /apps` (über ein beliebiges benutzerdefiniertes Inhaltspaket)
* direkt unter dem Pfad `/oak:index`

Wenn [Sicherstellen, dass Oak-Index](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) verwendet wurde, beachten Sie bitte, dass Sicherheitsdefinitionen auf AEM als Cloud Service nicht unterstützt werden und daher zuerst in Oak-Indexdefinitionen konvertiert werden müssen und dann zu Custom Oak-Indexdefinitionen migriert werden müssen, die gemäß den folgenden Richtlinien mit AEM als Cloud Service kompatibel sind:

* Wenn die Eigenschaft ignore auf `true` festgelegt ist, ignorieren Sie die Option &quot;Sicherheitsdefinition&quot;
* `jcr:primaryType` auf `oak:QueryIndexDefinition` aktualisieren
* Entfernen Sie alle Eigenschaften, die gemäß OSGi-Konfigurationen ignoriert werden sollen
* Entfernen Sie die Unterstruktur `/facets/jcr:content` aus der Sicherheitsdefinition

## Verwenden des Indexkonverters {#using-index-converter}

* Über Adobe I/O CLI: Es wird empfohlen, den Index-Konverter über `aio-cli-plugin-aem-cloud-service-migration` (AEM als Cloud Service-Code-Refactoring-Plugin für die Adobe I/O-CLI) zu verwenden.

Siehe **[Git-Ressource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)**, um zu erfahren, wie Sie das Plug-in installieren und verwenden.

* Als eigenständiges Dienstprogramm: Der Index Converter kann auch als eigenständiges Dienstprogramm ausgeführt werden.

Siehe **[Git-Ressource: aem-cs-source-migration-index-converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)**, um zu erfahren, wie dieses Tool verwendet wird.



