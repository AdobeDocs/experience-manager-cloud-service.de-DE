---
title: Versionshinweise für Cloud Manager 2026.1.0
description: Erfahren Sie mehr über Version 2026.1.0 von Cloud Manager in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 2ea076c42a6406548bf48cd246227fc8ddb3a080
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 46%

---

# Versionshinweise für Cloud Manager 2026.1.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

Erfahren Sie mehr über Version 2026.1.0 von Cloud Manager in AEM (Adobe Experience Manager) as a Cloud Service.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Die Version 2026.1.0 von Cloud Manager in AEM as a Cloud Service wurde am Freitag, 22. Januar 2026 veröffentlicht.

Die Veröffentlichung der nächsten Version ist für Donnerstag, den Freitag, 5. Februar 2026 geplant.

## Neue Funktionen - Cloud Manager {#cloud-manager-whats-new}

* **Konfigurations-Pipelines unterstützen jetzt verwaltete Geheimnisse**

  Benutzende können jetzt Geheimnisse direkt in Cloud Manager-Konfigurations-Pipelines hinzufügen und verwalten. Diese geheimen Daten überschreiben sicher Werte in der Pipeline-Konfigurationsspezifikation und unterstützen flexible, umgebungsspezifische Bereitstellungen.

  ![Option „Variablen anzeigen/bearbeiten“ im Dropdown-Menü für eine ausgewählte Pipeline](/help/implementing/cloud-manager/release-notes/assets/view-edit-variables-option.png)
  *Option „Variablen anzeigen/bearbeiten“ im Dropdown-Menü für eine ausgewählte Pipeline.*

  ![Dialogfeld „Variablenkonfiguration ](/help/implementing/cloud-manager/release-notes/assets/view-edit-variables-variablesconfig-dialogbox.png)*Dialogfeld „Variablenkonfiguration“.*

* **Verbesserte Stabilität, Leistung und Zuverlässigkeit**

  Diese Version umfasst Optimierungs- und Wartungsaktualisierungen, die die Stabilität, Leistung und Zuverlässigkeit von Cloud Manager verbessert haben.




## Beta-Programme {#private-beta-program}

Nehmen Sie am Beta-Programm von Cloud Manager teil, um exklusiven Zugriff auf bevorstehende Funktionen vor ihrer regulären Veröffentlichung zu erhalten.

>[!IMPORTANT]
>
>Beta-Versionen können Mängel enthalten und werden „wie besehen“ ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen (durch Adobe Support Services oder anderweitig). Adobe empfiehlt Kunden, Vorsicht walten zu lassen und sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung von Beta-Versionen oder auf begleitende Dokumentationen oder Materialien zu verlassen. Funktionen und APIs in der Beta-Version können ohne Vorankündigung geändert werden. Jede Nutzung der Beta-Versionen erfolgt daher ausschließlich auf eigene Gefahr des Kunden.

Siehe auch [AEM Beta-Programme](/help/release-notes/release-notes-cloud/release-notes-current.md#aem-beta-programs)

Derzeit stehen die folgenden Möglichkeiten zur Verfügung:
<!--
### Support for Custom Author Domains in Cloud Service

AEM Cloud Service is going to soon support one custom domain per Author environment.-->

### Erweiterbarkeit und Anpassung von Experience Hub {#exp-hub-extensibility}

[Experience Hub](/help/experience-hub.md) dient als Einstiegspunkt für AEM und ist an die Anforderungen Ihres Unternehmens angepasst. Teilen Sie Adobe Ihre bestehenden Erweiterungen der AEM-Benutzeroberfläche mit, damit Sie sie mit minimalem Aufwand in Experience Hub aktivieren können.

![Diagramm des Erweiterbarkeits- und Anpassungs-Workflows von Experience Hub](/help/implementing/cloud-manager/release-notes/assets/experience-hub-extensibility-customization.png)

Betten Sie benutzerdefinierte Erlebnisse in Experience Hub ein, um das Dashboard Ihres Unternehmens zu erweitern und zu personalisieren. Zusätzlich zu den integrierten Widgets von Adobe können Sie Ihre eigenen mit dem Framework für die [Erweiterbarkeit der Benutzeroberfläche](https://developer.adobe.com/uix/docs/) hinzufügen. Erstellen Sie auf JavaScript basierte Benutzeroberflächen-Apps und stellen Sie sie Ihren Benutzenden zur Verfügung, um geschäftsspezifische Anforderungen und Workflows zu erfüllen.

Sie interessieren sich für die Beta-Version? Senden Sie eine E-Mail an [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) mit Ihrer Adobe-OrgID und einer kurzen Beschreibung der Anpassung, die Sie vornehmen möchten.

### Schnellere Builds mit Modul-Caching {#quick-build-cm-pipelines}

Ein neues Build-Modell kompiliert nur geänderte Module (nicht das gesamte Repository) mithilfe des Caching auf Modulebene, um die Erstellungszeiten zu verkürzen. Es kann für Code-Qualitäts-, Full-Stack- und reine Staging-Pipelines angewendet werden.

![Dialogfeld „Produktionsfremde Pipeline bearbeiten“ mit den beiden Optionen für die Build-Strategie „Vollständiger Build“ und „Intelligenter Build“](/help/implementing/cloud-manager/release-notes/assets/non-production-pipeline-edit.png)
*Dialogfeld „Produktionsfremde Pipeline bearbeiten“ mit den beiden Optionen für die Build-Strategie „Vollständiger Build“ und „Intelligenter Build“.*

Im Dialogfeld **Pipeline hinzufügen/bearbeiten** auf der Registerkarte **Source-Code** können Sie mit dem Abschnitt **Erstellen-Strategie** eine der folgenden Build-Optionen auswählen:

* **Vollständiger Build** - Erstellt bei jeder Ausführung alle Module im Repository.
* **Smarter Build** - Erstellt nur Module, die seit dem letzten Commit geändert wurden, was die Erstellungszeit insgesamt verkürzt.

Sie steuern, welche Pipelines „Smart **Build“**. Während der Beta-Phase wird diese Option nur für Pipelines **Code-Qualität** und **Bereitstellung durch Entwicklung** angezeigt.

Sie sind interessiert? Senden Sie eine E-Mail an [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) mit Ihrer Adobe-OrgID und Programm-ID.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline Variables in Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md).-->

## Fehlerbehebungen {#bug-fixes}

In der Cloud Manager-Version vom Dezember 2025 gibt es keine signifikanten Fehlerbehebungen.


<!-- ## Known issues {#known-issues} -->

