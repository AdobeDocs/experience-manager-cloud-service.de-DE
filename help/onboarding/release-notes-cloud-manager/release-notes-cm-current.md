---
title: Versionshinweise für Cloud Manager in AEM als Cloud Service Release 2020.11.0
description: Versionshinweise für Cloud Manager in AEM als Cloud Service Release 2020.11.0
translation-type: tm+mt
source-git-commit: 1d71788a84bb3c680ad4045454db00cfb345469d
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 4%

---


# Release Notes for Cloud Manager in Adobe Experience Manager as a Cloud Service 2020.11.0 {#release-notes}

Auf dieser Seite werden die Versionshinweise für Cloud Manager in AEM als Cloud Service 2020.11.0 erläutert.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für Cloud Manager in AEM als Cloud Service 2020.11.0 ist der 12. November 2020.

## Cloud Manager {#cloud-manager}

### Neue Funktionen {#what-is-new}

* Eine neue Menüoption &quot; **Lokale Anmeldung** &quot;steht nun den Benutzern über die Menüoptionen &quot;Umgebung&quot;auf den Seiten &quot;Umgebung&quot;und &quot;Umgebung - Zusammenfassung&quot;zur Verfügung.

* Die Registerkarte &quot; **Lernen** &quot;in Cloud Manager wurde mit neuen Bildern in der Benutzeroberfläche aktualisiert.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Das Laden von Abhängigkeiten vor der Ausführung des Builds erforderte den Download eines Maven-Plugins.
* Über den Link in der Fußzeile von Cloud Manager zur Auswahl einer Sprache navigieren Sie jetzt zum richtigen Speicherort.
* Während der Codeprüfung wird der SonarQube-Vorgang manchmal nicht Beginn. Dies wird nun automatisch erkannt und ein Neustart wird versucht.
* Alle vorhandenen Produktionslinien werden automatisch mit dem Experience Audit-Schritt aktiviert.