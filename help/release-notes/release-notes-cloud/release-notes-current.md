---
title: Versionshinweise für die Version 2020.8.0 [!DNL Adobe Experience Manager] von als Cloud Service.
description: '[!DNL Adobe Experience Manager] als Cloud Service-Versionshinweise für 2020.8.0.'
translation-type: tm+mt
source-git-commit: 5a53e13a3692fbb8ab3ae7760f13b6908d15db3a
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 24%

---


# Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service 2020.8.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager as a Cloud Service 2020.8.0 beschrieben.

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

* Die neuen [!DNL Experience Manager Assets] Implementierungen sind standardmäßig in [!DNL Adobe Developer Console] integriert. Dadurch wird die Konfiguration der Smart-Tags-Funktion beschleunigt. Bei den vorhandenen Bereitstellungen [konfigurieren Administratoren wie bisher die Integration](/help/assets/smart-tags-configuration.md#aio-integration) von Smarttags.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neuerungen {#what-is-new-commerce}

* Die Funktion Produktkonsole ist jetzt verfügbar. Auf diese Weise können Marketingexperten/Autoren in AEM Ansicht und Navigation in Kategorien und Produkten durchführen, die im Commerce-Backend gespeichert sind. Die Unterstützung von Eigenschaften für Kategorien und Produkte in der Produktkonsole wird ebenfalls bereitgestellt.

* Produkt- und Kategorie-Picker wurden verbessert, damit Marketingexperten Produkte über SKU auswählen oder Kategorien über Kategorien-ID auswählen können.

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Die [!UICONTROL Cloud Manager]-Version 2020.8.0 wurde am 06. August 2020 veröffentlicht.

### Neuerungen {#what-is-new-cloud-manager}

* Content Audit is a feature enabled on Cloud Manager Sites Production Pipelines. The Production Pipeline configuration for programs with Sites now includes a third tab named **Content Audit**. Bei jeder Ausführung einer Produktions-Pipeline wird nach benutzerdefinierten Funktionstests ein neuer Content-Audit-Schritt in die Pipeline aufgenommen, der die Site anhand einer Reihe von Dimensionen wie Leistung, SEO (Suchmaschinenoptimierung), Barrierefreiheit, Best Practices und PWA (Progressive Web App) bewertet.

   Refer to [Content Audit Testing](/help/implementing/developing/introduction/understand-test-results.md#content-audit-testing) for more details.

* Newly created environments in Assets programs will now be automatically configured with Smart Content Services.

* Hibernated-Umgebung können auf der Seite &quot; **Übersicht** &quot;von Cloud Manager entfernt werden.

* Authentifizierungsgebundene Private Maven-Repositorys werden jetzt unterstützt.

* Der Cloud Manager-Build-Container unterstützt jetzt sowohl Java 8 als auch Java 11.
Refer to [Using Java 11 Support](/help/onboarding/getting-access-to-aem-in-cloud/creating-aem-application-project.md#using-java-support) for more details.

### Fehlerbehebungen {#bug-fixes-cm}

* Einige unnötige und unerwünschte SonarQube-Plug-ins wurden im Rahmen der Überprüfung der Codequalität ausgeführt.

* Auf der Seite zur Ausführung der Pipeline wurde der Verzweigungsname falsch formatiert.

* In einigen Fällen wurden abgeschlossene Pipeline-Ausführungen nicht erfolgreich als abgeschlossen aufgezeichnet, wodurch neue Ausführungen der Pipeline verhindert wurden.

* Pipeline-Ausführungen blieben gelegentlich aufgrund interner Kommunikationsprobleme *stecken*.

* Upon provisioning a new organization, some users with administrative roles other than system administrators were erroneously given access to Cloud Manager.

* Under certain conditions, the update indexes job was started multiple times in parallel resulting in a deployment failure.

* Die QuickInfo auf den Programmkarten war nicht immer korrekt.

* The user interface erroneously allowed for operations to be attempted on an environment while it was being deleted.

* There was a color mismatch on the Cloud Manager&#39;s **Overview** page.

### Bekannte Probleme {#known-issues-cm}

* Invalid pages are included bringing the Content Audit Average Score below what they should be.

* The Content Audit tab incorrectly displays the base URL using the author domain instead of the publish domain.

* In order to activate the Content Audit step, users must edit the pipeline and, optionally, add pages. If no pages are added, the homepage will be audited.

## Content Transfer-Tool {#content-transfer-tool}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für Content Transfer Tool Version 1.0.4.

### Neuerungen {#what-is-new-ctt}

* Content Transfer Tool unterstützt jetzt den freigegebenen S3 DataStore.

### Fehlerbehebungen {#ctt-bug-fixes}

* Zusätzliche Timeouts, die hinzugefügt wurden, damit das Tool Aktionen abschließen kann.

* In früheren Versionen der Benutzeroberfläche wurde manchmal eine erfolgreiche Extraktion angezeigt, obwohl Fehler im Protokoll auftraten.

