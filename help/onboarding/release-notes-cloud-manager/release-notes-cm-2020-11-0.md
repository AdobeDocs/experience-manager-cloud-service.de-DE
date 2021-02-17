---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service Version 2020.11.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service Version 2020.11.0
translation-type: tm+mt
source-git-commit: 79af82d1589108e7a8953e29a5d0f0169920585c
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 100%

---


# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2020.11.0 {#release-notes}

Auf dieser Seite werden die allgemeinen Versionshinweise für Cloud Manager in AEM as a Cloud Service 2020.11.0 beschrieben.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von Cloud Manager in AEM as a Cloud Service Version 2020.11.0 ist der 12. November 2020.

## Cloud Manager {#cloud-manager}

### Neuerungen {#what-is-new}

* Die neue Menüoption **Lokale Anmeldung** steht nun den Anwendern über die Menüoptionen auf der Umgebungskarte und den Zusammenfassungsseiten für die Umgebungen zur Verfügung.
Weitere Informationen finden Sie unter [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md#login-locally).

* Die Registerkarte **Lernen** in Cloud Manager wurde mit neuen Bildern in der Benutzeroberfläche aktualisiert.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Das Laden von Abhängigkeiten vor der Ausführung des Builds erforderte den Download eines Maven-Plug-ins.
* Über den Link in der Fußzeile von Cloud Manager zur Sprachauswahl wird jetzt an die richtige Stelle navigiert.
* Manchmal startete der SonarQube-Prozess während des Code-Scannens nicht. Dies wird nun automatisch erkannt und ein Neustart wird versucht.
* Alle vorhandenen Produktions-Pipelines werden automatisch mit dem Experience Audit-Schritt aktiviert.
