---
title: AEM-Systemübersicht
description: AEM-Systemübersicht
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 3%

---


# AEM-Systemübersicht {#aem-system}

Auf dieser Seite wird die Systemübersicht zu Adobe Experience Manager (AEM) beschrieben.

## Hintergrund {#background}

Dieses Muster wird zur Identifizierung allgemeiner Informationen verwendet, die einen Überblick über das AEM-System bieten. Informationen können Elemente wie:

AEM-VersionVerwendete AEM-Produkte (Sites, Assets, Formulare usw.)Anzahl der Knoten (Seiten, Assets usw.)

## Musterdaten {#pattern-data}

Die folgenden Objekte sind in der JSON-Darstellung des Musters enthalten:

* **item.message**: bezieht sich auf die Meldung des Musters.
* **item.context**: bezieht sich auf zusätzliche Informationen über die Übersichtsinformationen:
   * *type*: Der Typ der Kontextdaten, entweder &quot;aem.version&quot;, &quot;aem.product&quot;oder &quot;node.count&quot;.
   * *data*: Ein JSON-Objekt, das die dem Typ entsprechenden Daten enthält: &quot;version&quot;(Zeichenfolge), &quot;product&quot;(Zeichenfolge) oder &quot;count&quot;(Ganzzahl).

### Mögliche Auswirkungen und Risiken {#possible-implications}

Nicht zutreffend.

### Mögliche Lösungen  {#possible-solutions}

Nicht zutreffend.
