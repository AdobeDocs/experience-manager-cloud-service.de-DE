---
title: AEM-Knotentypen
description: AEM basiert auf Sling und verwendet ein JCR-Repository mit Knotentypen, die von beiden angeboten werden, aber AEM bietet auch eine Reihe von eigenen Knotentypen.
exl-id: 82cc28ca-37e2-4ca3-b3e4-cc03bbc5bdf5
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 100%

---

# AEM-Knotentypen {#aem-node-types}

Da AEM auf Sling basiert und ein JCR-Repository verwendet, sind von beiden Standards bereitgestellte Knotentypen für die Verwendung in AEM verfügbar:

* [JCR-Knotentypen](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/3_Repository_Model.html#3.1.7-Node-Types)
* [Sling-Knotentypen](https://cwiki.apache.org/confluence/display/SLING/Sling+Node+Types)

Darüber hinaus stellt AEM stellt eine Reihe benutzerdefinierter Knotentypen bereit. Um die aktuelle Liste mit allen zugehörigen Eigenschaften zu erhalten, [verwenden Sie CRXDE](/help/implementing/developing/tools/crxde.md), um den folgenden Pfad im AEM-Repository zu durchsuchen:

`/jcr:system/jcr:nodeTypes`
