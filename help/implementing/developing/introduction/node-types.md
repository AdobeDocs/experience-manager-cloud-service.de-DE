---
title: AEM-Knotentypen
description: AEM basiert auf Sling und verwendet ein JCR-Repository mit Knotentypen, die von beiden angeboten werden, aber AEM bietet auch eine Reihe von eigenen Knotentypen.
exl-id: 82cc28ca-37e2-4ca3-b3e4-cc03bbc5bdf5
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 100%

---

# AEM-Knotentypen {#aem-node-types}

Da AEM auf Sling basiert und ein JCR-Repository verwendet, sind von beiden Standards bereitgestellte Knotentypen für die Verwendung in AEM verfügbar:

* [JCR-Knotentypen](https://www.adobe.io/experience-manager/reference-materials/spec/jcr/2.0/3_Repository_Model.html#3.1.7-Node-Types)
* [Sling-Knotentypen](https://cwiki.apache.org/confluence/display/SLING/Sling+Node+Types)

Darüber hinaus stellt AEM stellt eine Reihe benutzerdefinierter Knotentypen bereit. Um die aktuelle Liste mit allen zugehörigen Eigenschaften zu erhalten, [verwenden Sie CRXDE](/help/implementing/developing/tools/crxde.md), um den folgenden Pfad im AEM-Repository zu durchsuchen:

`/jcr:system/jcr:nodeTypes`
