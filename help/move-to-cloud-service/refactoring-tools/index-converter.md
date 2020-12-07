---
title: Indexkonverter
description: Indexkonverter
translation-type: tm+mt
source-git-commit: 21bd9392d913369a5e8e0ebd9badbbe30fd4bba3
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 5%

---


# Indexkonverter {#index-converter}

Index Converter ist ein Dienstprogramm, das entwickelt wurde, um die Indexdefinition eines Kunden zu migrieren, um den Übergang zu AEM als Cloud Service vorzubereiten.

## Einführung {#introduction}

Mit dem Index-Konverter können AEM Entwickler bestehende Custom Oak Index-Definitionen migrieren, um sie als Cloud Service-kompatible Custom Oak-Indexdefinitionen zu AEM.

>[!NOTE]
>Indexkonverter transformieren nur *lucene* Geben Sie Custom Oak Index Definitions ein, die unter `/apps` oder `/oak:index` vorhanden sind. Es werden keine *lucene*-Typindizes transformiert, die für `nt:base` erstellt werden.

## Verwenden des Indexkonverters {#using-index-converter}

Siehe **[Git-Ressource: aem-cs-source-migration-index-converter](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)**, um zu erfahren, wie das Plugin installiert und verwendet wird.

