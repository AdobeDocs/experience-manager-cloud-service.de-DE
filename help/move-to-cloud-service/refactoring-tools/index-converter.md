---
title: Indexkonverter
description: Indexkonverter
translation-type: tm+mt
source-git-commit: fecbd0b4d5cfd8aa970c235c79158bea44403c09
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 4%

---


# Indexkonverter {#index-converter}

Index Converter ist ein Dienstprogramm, das entwickelt wurde, um die Indexdefinition eines Kunden zu migrieren, um den Übergang zu AEM als Cloud Service vorzubereiten.

## Einführung {#introduction}

Mit dem Index-Konverter können AEM Entwickler bestehende Custom Oak Index-Definitionen migrieren, um sie als Cloud Service-kompatible Custom Oak-Indexdefinitionen zu AEM.

>[!NOTE]
>Index Converter transformiert nur *lucene* den Typ Custom Oak Index Definitions, die unter `/apps` oder `/oak:index` vorhanden sind. Es werden keine *lucene*-Typindizes transformiert, die für `nt:base` erstellt werden.

Es gibt zwei Möglichkeiten, benutzerdefinierte Oak-Indexdefinitionen zu erstellen:

* `under /apps` (über ein beliebiges benutzerdefiniertes Inhaltspaket)
* direkt unter dem Pfad `/oak:index`

>[!NOTE]
>Informationen zum Definieren und Erstellen von Eichendefinitionen finden Sie unter [Eichenindex](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html)

## Verwenden des Indexkonverters {#using-index-converter}

>[!NOTE]
>Es wird empfohlen, das Index Converter-Tool über das [AIO CLI-Plugin für die Quellmigration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) zu verwenden. Es kann aber auch eigenständig ausgeführt werden.

Siehe **[Git-Ressource: aem-cs-source-migration-index-converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)**, um zu erfahren, wie das Plugin installiert und verwendet wird.

