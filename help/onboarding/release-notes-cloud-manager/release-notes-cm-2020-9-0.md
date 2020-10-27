---
title: Versionshinweise für Cloud Manager in AEM als Cloud Service Release 2020.9.0
description: Versionshinweise für Cloud Manager in AEM als Cloud Service Release 2020.9.0
translation-type: tm+mt
source-git-commit: ca690144a8254d5ffba354f0f96d9ef1c5202533
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 13%

---


# Release Notes for Cloud Manager in Adobe Experience Manager as a Cloud Service 2020.9.0 {#release-notes}

Auf dieser Seite werden die Versionshinweise für Cloud Manager in AEM als Cloud Service 2020.9.0 erläutert.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für Cloud Manager in AEM als Cloud Service 2020.9.0 ist der 3. September 2020.

## Neue Funktionen {#whats-new-cloud-manager}

* Content Audit wurde als Experience Audit umbenannt.
* Der Build-Prozess wurde in drei separate Maven-Befehle unterteilt.
* Wenn das Git-Repository nicht geklont werden kann, wird es bis zu dreimal erneut versucht.

### Fehlerbehebungen {#bug-fixes-cm}

* Auf der Registerkarte &quot;Content Audit&quot;wurde die Basis-URL fälschlicherweise unter Verwendung der Autorendomäne und nicht der Veröffentlichungsdomäne angezeigt.