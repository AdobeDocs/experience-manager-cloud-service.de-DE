---
title: Versionshinweise für die Version 2020.8.0 [!DNL Adobe Experience Manager] von als Cloud Service.
description: '[!DNL Adobe Experience Manager] als Cloud Service-Versionshinweise für 2020.8.0.'
translation-type: tm+mt
source-git-commit: dafdbffa96cd565379a700c696586222f43022c2
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 8%

---


# Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service 2020.8.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager as a Cloud Service 2020.8.0 beschrieben.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neuerungen {#what-is-new-commerce}

* Product Console feature is now available. Auf diese Weise können Marketingexperten/Autoren in AEM Ansicht und Navigation in Kategorien und Produkten durchführen, die im Commerce-Backend gespeichert sind. Support for properties for catogories and products in the Product Console also provided.

* Product and Category Pickers improved to allow marketers to select product via SKU or select category via category ID.

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Die [!UICONTROL Cloud Manager]-Version 2020.8.0 wurde am 06. August 2020 veröffentlicht.

### Neuerungen {#what-is-new-cloud-manager}

* Content Audit is a feature enabled on Cloud Manager Sites Production Pipelines. The Production Pipeline configuration for programs with Sites now includes a third tab named **Content Audit**. Whenever a production pipeline is run, a new Content Audit step will be included in the pipeline after custom functional testing which will evaluate the site against a number of dimensions including performance, SEO (Search Engine Optimization), accessibility, best practices and PWA (Progressive Web App).

   Refer to [Content Audit Testing](/help/implementing/developing/introduction/understand-test-results.md#content-audit-testing) for more details.

* Neu erstellte Umgebung in Assets-Programmen werden jetzt automatisch mit Smart Content Services konfiguriert.

* Hibernated-Umgebung können auf der Seite &quot; **Übersicht** &quot;von Cloud Manager entfernt werden.

* Authentication-bound Private Maven Repositories are now supported.

### Fehlerbehebungen {#bug-fixes-cm}

* Einige unnötige und unerwünschte SonarQube-Plugins wurden im Rahmen der Überprüfung der Codequalität ausgeführt.

* Auf der Seite zur Ausführung der Pipeline wurde der Zweigname falsch formatiert.

* In einigen Fällen wurden abgeschlossene Pipeline-Hinrichtungen nicht erfolgreich als abgeschlossen aufgezeichnet, wodurch neue Hinrichtungen der Pipeline verhindert wurden.

* Pipeline executions would occasionally get *stuck* due to internal communication issues.

* Bei der Bereitstellung einer neuen Organisation erhielten einige Benutzer mit Administratorrollen, die keine Systemadministratoren waren, fälschlicherweise Zugriff auf Cloud Manager.

* Unter bestimmten Umständen wurde der Aktualisierungsindexauftrag mehrmals parallel gestartet, was zu einem Bereitstellungsfehler führte.

* Die QuickInfo auf den Programm-Karten waren nicht einheitlich korrekt.

* Die Benutzeroberfläche erlaubte irrtümlicherweise den Versuch, Vorgänge auf einer Umgebung auszuführen, während diese gelöscht wurde.

* Auf der Seite &quot; **Übersicht** &quot;des Cloud-Managers wurde eine Farbabweichung festgestellt.

### Bekannte Probleme {#known-issues-cm}

* Es sind ungültige Seiten enthalten, die die durchschnittliche Inhaltsprüfung unter den gewünschten Werten bringen.

* Auf der Registerkarte &quot;Content Audit&quot;wird die Basis-URL fälschlicherweise unter Verwendung der Autorendomäne anstelle der Veröffentlichungsdomäne angezeigt.

* Um den Schritt &quot;Content Audit&quot;zu aktivieren, müssen Benutzer die Pipeline bearbeiten und optional Seiten hinzufügen. Wenn keine Seiten hinzugefügt werden, wird die Homepage geprüft.

## Content Transfer-Tool {#content-transfer-tool}

Follow this section to learn about what is new and the updates for Content Transfer Tool Release v1.0.4.

### Neuerungen {#what-is-new-ctt}

* Content Transfer Tool unterstützt jetzt den freigegebenen S3 DataStore.

### Fehlerbehebungen {#ctt-bug-fixes}

* Zusätzliche Timeouts, die hinzugefügt wurden, damit das Tool Aktionen abschließen kann.

* In früheren Versionen der Benutzeroberfläche wurde manchmal eine erfolgreiche Extraktion angezeigt, obwohl Fehler im Protokoll auftraten.

