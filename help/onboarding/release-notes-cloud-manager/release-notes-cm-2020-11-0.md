---
title: Versionshinweise für Cloud Manager in AEM als Cloud Service Release 2020.11.0
description: Versionshinweise für Cloud Manager in AEM als Cloud Service Release 2020.11.0
translation-type: tm+mt
source-git-commit: 79af82d1589108e7a8953e29a5d0f0169920585c
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 36%

---


# Versionshinweise für Cloud Manager in Adobe Experience Manager als Cloud Service 2020.11.0 {#release-notes}

Auf dieser Seite werden die Versionshinweise für Cloud Manager in AEM als Cloud Service 2020.11.0 erläutert.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für Cloud Manager in AEM als Cloud Service 2020.11.0 ist der 12. November 2020.

## Cloud Manager {#cloud-manager}

### Neue Funktionen {#what-is-new}

* Eine neue Menüoption **Lokale Anmeldung** steht nun den Benutzern über die Menüoptionen auf der Umgebung und den Zusammenfassungsseiten der Umgebung zur Verfügung.
Weitere Informationen finden Sie unter [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md#login-locally).

* Die Registerkarte **Lernen** in Cloud Manager wurde mit neuen Bildern in der Benutzeroberfläche aktualisiert.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Das Laden von Abhängigkeiten vor der Ausführung des Builds erforderte den Download eines Maven-Plug-ins.
* Über den Link in der Fußzeile von Cloud Manager zur Sprachauswahl wird jetzt an die richtige Stelle navigiert.
* Manchmal startete der SonarQube-Prozess während des Code-Scannens nicht. Dies wird nun automatisch erkannt und ein Neustart wird versucht.
* Alle vorhandenen Produktionslinien werden automatisch mit dem Experience Audit-Schritt aktiviert.
