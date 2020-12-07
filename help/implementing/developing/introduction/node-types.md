---
title: AEM
description: AEM basiert auf Sling und verwendet ein JCR-Repository mit Knotentypen, die von beiden angeboten werden, AEM bietet aber auch eine Reihe von eigenen Node-Typen.
translation-type: tm+mt
source-git-commit: 020cebfa714c098f032df963b7105503c741e748
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 15%

---


# AEM Node Types {#aem-node-types}

Da AEM auf Sling basiert und ein JCR-Repository verwendet, stehen Knotentypen, die beide dieser Standards bieten, zur Verwendung in AEM zur Verfügung:

* [JCR-Knotentypen](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/3_Repository_Model.html#3.1.7-Node-Types)
* [Sling-Knotentypen](https://cwiki.apache.org/confluence/display/SLING/Sling+Node+Types)

Darüber hinaus stellt AEM bietet eine Reihe von benutzerdefinierten Knotentypen. Für die aktuellste Liste mit allen zugehörigen Eigenschaften verwenden Sie [CRXDE](/help/implementing/developing/tools/crxde.md), um den folgenden Pfad im AEM Repository zu durchsuchen:

`/jcr:system/jcr:nodeTypes`
