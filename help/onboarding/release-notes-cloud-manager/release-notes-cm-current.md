---
title: Versionshinweise für Cloud Manager in AEM als Cloud Service Release 2020.11.0
description: Versionshinweise für Cloud Manager in AEM als Cloud Service Release 2020.11.0
translation-type: tm+mt
source-git-commit: 727dfd1d16a80620fba6db00289021ee5efae0fc
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 32%

---


# Release Notes for Cloud Manager in Adobe Experience Manager as a Cloud Service 2020.11.0 {#release-notes}

Auf dieser Seite werden die Versionshinweise für Cloud Manager in AEM als Cloud Service 2020.11.0 erläutert.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für Cloud Manager in AEM als Cloud Service 2020.11.0 ist der 12. November 2020.

## Cloud Manager {#cloud-manager}

### Neue Funktionen {#what-is-new}

* Eine neue Menüoption &quot; **Lokale Anmeldung** &quot;steht nun den Benutzern über die Menüoptionen &quot;Umgebung&quot;auf den Seiten &quot;Umgebung&quot;und &quot;Umgebung - Zusammenfassung&quot;zur Verfügung.
Refer to [Managing Environments](/help/implementing/cloud-manager/manage-environments.md##login-locally) for more details.

* The **Learn** tab in Cloud Manager has been refreshed with new images in the UI.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Das Laden von Abhängigkeiten vor der Ausführung des Builds erforderte den Download eines Maven-Plug-ins.
* Über den Link in der Fußzeile von Cloud Manager zur Sprachauswahl wird jetzt an die richtige Stelle navigiert.
* Manchmal startete der SonarQube-Prozess während des Code-Scannens nicht. Dies wird nun automatisch erkannt und ein Neustart wird versucht.
* Alle vorhandenen Produktionslinien werden automatisch mit dem Experience Audit-Schritt aktiviert.