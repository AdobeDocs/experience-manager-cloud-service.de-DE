---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] als Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] als Cloud Service.
translation-type: tm+mt
source-git-commit: 539fa16396519b66d53b91745bf69c819c5d5ea1
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 16%

---


# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!DNL Experience Manager] als Cloud Service beschrieben.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für [!DNL Adobe Experience Manager] als Cloud Service 2020.12.0 ist der 17. Dezember 2020.
Die folgende Version (2021.1.0) wird am 28. Januar 2020 veröffentlicht.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* **[Content Fragment HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md)**: hinzufügen die Möglichkeit, Inhaltsfragmentvarianten mithilfe der HTTP-API hinzuzufügen/zu aktualisieren und zu löschen.

## [!DNL Adobe Experience Manager Assets] als  [!DNL Cloud Service] {#assets}

* Die Integration mit [!DNL Adobe InDesign Server] ist jetzt für [!DNL Experience Manager] als [!DNL Cloud Service] verfügbar. Es bietet Automatisierung zur Verarbeitung von [!DNL Adobe InDesign]-Dateien mithilfe von [!DNL Adobe InDesign Server]-Skripten und ermöglicht Benutzern die Verwendung der [!DNL Assets]-Vorlagen-Benutzeroberfläche zum Erstellen von Prospekten oder Anzeigen. Für [!DNL Experience Manager as a Cloud Service] wird nur [!DNL InDesign Server] unterstützt, wenn [!DNL Adobe Managed Services] gehostet wird. <!-- TBD: Add link to article. -->

* [!DNL Experience Manager] wurde erweitert, um Asset-Verweise zu verfolgen und anzuzeigen, wenn ein Asset in einer Remote- [!DNL Experience Manager Sites] Bereitstellung mithilfe der Funktion &quot;Connected Assets&quot;verwendet wird. Die neue Registerkarte [!UICONTROL Referenzen] auf der Seite [!UICONTROL Eigenschaften] des Assets Liste jetzt lokale und Remote-Referenzen des Assets. Anhand der Referenzen können DAM-Benutzer die Asset-Nutzung auf [!DNL Sites]-Seiten und in zusammengesetzten Assets auf [!DNL Assets] verfolgen. Siehe [Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md) konfigurieren und verwenden.

* [!DNL Dynamic Media] Funktionen sind jetzt über  [!DNL Sites] bildbasierte Core-Komponenten verfügbar. Autoren können Komponenten beim Erstellen von Webseiten schnell für die Verwendung von Bildvorgaben, intelligentem Beschneiden und Bildmodifikatoren konfigurieren. Siehe [Kernkomponenten 2.13.0 Release](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.13.0).

* [!DNL Experience Manager] Mit der Desktop-App können Benutzer Dateien und Ordner hochladen, indem sie die Dateien aus dem Windows Explorer oder dem Mac Finder in die Benutzeroberfläche der Desktop-App ziehen. Siehe [Hinzufügen von Assets mit der Desktop-App](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* CIF Venia-Referenzseite - 2020.12.01, die die aktuellste CIF-Core-Komponenten Version v1.6.0 enthält. Weitere Informationen finden Sie unter [CIF Venia Reference Site](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.12.01).

* Version 1.6.0 von CIF-Kernkomponenten veröffentlicht. Weitere Informationen finden Sie unter [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.6.0).

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Das Veröffentlichungsdatum für Cloud Manager in AEM als Cloud Service 2020.12.0 ist der 10. Dezember 2020.

### Neue Funktionen in [!DNL Cloud Manager] {#what-is-new-cm}

* Selbstbedienungs-Management von [SSL-Zertifikate](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) und [Benutzerspezifische Domänennamen](/help/implementing/cloud-manager/custom-domain-names/introduction.md).

* Selbstbedienungs-Management von [IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

* Die Detailseite **Umgebung** wurde aktualisiert und ermöglicht Benutzern nun, benutzerdefinierte Domänennamen und IP-Zulassungslisten auf ihren Umgebung zu verwalten.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Einige Fehler beim Scannen von Code, ohne Ergebnisse bereitzustellen, wurden behoben.

* Die Schaltfläche **Hinzufügen** wurde auf der Umgebung nicht einheitlich angezeigt.

## Code-Refaktorierungs-Tools {#code-refactoring-tools}

### Neue Funktionen in [!DNL Code Refactoring Tools] {#what-is-new-crt}

* Neue Version des AIO-CLI Plugins veröffentlicht. Die neueste Version dieses Plugins enthält Fehlerbehebungen für den AEM Dispatcher Converter und den Repository Modernizer und unterstützt auch ein neues Dienstprogramm - den Index Converter. Weitere Informationen zu diesem Plugin finden Sie unter [Unified Experience](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=en#benefits).

* Index Converter ist ein Dienstprogramm, das verwendet werden kann, um die benutzerdefinierten OAK-Indexdefinitionen eines Kunden in AEM als Cloud Service kompatible OAK-Indexdefinitionen umzuwandeln. Weitere Informationen finden Sie unter [Indexkonverter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter).

* Neue Funktion zu [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) hinzugefügt, die ein separates Paket `ui.config` erstellt, das alle OSGi-Konfigurationen enthält.

### Fehlerbehebungen {#crt-bug-fixes}

* Mehrere Fehlerkorrekturen, die mit den Werkzeugen AEM Dispatcher Converter und Repository Modernizer vorgenommen wurden. Weitere Informationen finden Sie unter [AEM Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) und [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).
