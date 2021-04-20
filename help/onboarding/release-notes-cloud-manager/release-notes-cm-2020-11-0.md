---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2020.11.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2020.11.0
feature: Release Information
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 100%

---


# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2020.11.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2020.11.0.

## Veröffentlichungsdatum {#release-date}

Die Version 2020.11.0 von Cloud Manager in AEM as a Cloud Service wurde am 12. November 2020 veröffentlicht.

## Cloud Manager {#cloud-manager}

### Neue Funktionen {#what-is-new}

* Die neue Menüoption **Lokale Anmeldung** steht nun den Anwendern über die Menüoptionen auf der Umgebungskarte und den Zusammenfassungsseiten für die Umgebungen zur Verfügung.
Weitere Informationen finden Sie unter [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md#login-locally).

* Die Registerkarte **Lernen** in Cloud Manager wurde mit neuen Bildern in der Benutzeroberfläche aktualisiert.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Das Laden von Abhängigkeiten vor der Ausführung des Builds erforderte den Download eines Maven-Plug-ins.
* Über den Link in der Fußzeile von Cloud Manager zur Sprachauswahl wird jetzt an die richtige Stelle navigiert.
* Manchmal startete der SonarQube-Prozess während des Code-Scannens nicht. Dies wird nun automatisch erkannt und ein Neustart wird versucht.
* Alle vorhandenen Produktions-Pipelines werden automatisch mit dem Experience Audit-Schritt aktiviert.
