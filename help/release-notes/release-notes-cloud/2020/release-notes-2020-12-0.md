---
title: Versionshinweise für Version 2020.12.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2020.12.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 16875180-1f23-477d-9d4d-e220998c4983
source-git-commit: ecf4c06fd290d250c14386b3135250633b26c910
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 50%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!DNL Experience Manager] as a Cloud Service beschrieben.

## Veröffentlichungsdatum {#release-date}

Die Version 2020.12.0 von [!DNL Adobe Experience Manager] as a Cloud Service wurde am 17. Dezember 2020 veröffentlicht.
Die folgende Version (2021.1.0) ist der 28. Januar 2021.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* **[HTTP-API für Inhaltsfragmente](/help/assets/content-fragments/assets-api-content-fragments.md)**: Hinzufügen der Möglichkeit zum Hinzufügen/Aktualisieren und Löschen von Varianten von Inhaltsfragmenten über die HTTP-API.

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

* Die Integration mit [!DNL Adobe InDesign Server] ist jetzt für [!DNL Experience Manager] as a [!DNL Cloud Service] verfügbar. Sie bietet Automatisierung zur Verarbeitung von [!DNL Adobe InDesign]-Dateien mithilfe von [!DNL Adobe InDesign Server]-Skripten und ermöglicht Benutzern die Verwendung der [!DNL Assets]-Vorlagen-Benutzeroberfläche zum Erstellen von Prospekten oder Anzeigen. Nur der von [!DNL Adobe Managed Services] gehostete [!DNL InDesign Server] wird für [!DNL Experience Manager as a Cloud Service] unterstützt. <!-- TBD: Add link to article. -->

* [!DNL Experience Manager] wurde erweitert, um Asset-Referenzen zu verfolgen und anzuzeigen, wenn ein Asset in einer Remote-Bereitstellung von [!DNL Experience Manager Sites] mithilfe der Funktion für Connected Assets verwendet wird. Eine neue [!UICONTROL Verweise] Registerkarte im Asset [!UICONTROL Eigenschaften] Seite listet jetzt lokale und Remote-Referenzen des Assets auf. Anhand der Referenzen können DAM-Benutzer die Asset-Nutzung auf [!DNL Sites]-Seiten und in zusammengesetzten Assets in [!DNL Assets] verfolgen. Weitere Informationen finden Sie unter [Konfigurieren und Verwenden von Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md).

* [!DNL Dynamic Media] -Funktionen sind jetzt über AEM verfügbar. [!DNL Sites] bildbasierte Kernkomponenten. Autoren können Komponenten schnell konfigurieren, um Bildvorgaben, smarte Zuschnitte und Bildmodifikatoren beim Erstellen von Web-Seiten zu verwenden. Weitere Informationen finden Sie unter [Kernkomponenten Version 2.13.0](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.13.0).

* Die [!DNL Experience Manager] Mit dem -Desktop-Programm können Benutzer Dateien und Ordner hochladen, indem sie die Dateien aus Windows Explorer oder Mac Finder in die Benutzeroberfläche des -Desktop-Programms ziehen. Siehe [Hinzufügen von Assets mithilfe des Desktop-Programms](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de#upload-and-add-new-assets-to-aem).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Veröffentlicht CIF Venia-Referenz-Site 2020.12.01, die die neueste Version der CIF Kernkomponenten Version 1.6.0 enthält. Siehe [Venia-Referenz-Website CIF](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.12.01) für weitere Details.

* Version 1.6.0 CIF Kernkomponenten veröffentlicht. Siehe [CIF Kernkomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.6.0) für weitere Details.

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Die Version 2020.12.0 von Cloud Manager in Adobe Experience Manager (AEM) wurde am Donnerstag, 10. Dezember 2020 veröffentlicht.

### Neue Funktionen in [!DNL Cloud Manager] {#what-is-new-cm}

* Self-Service-Verwaltung von [SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) und [benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/introduction.md).

* Self-Service-Verwaltung von [IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

* Die aktualisierten **Umgebung** Auf der Detailseite können Benutzer jetzt benutzerdefinierte Domänennamen und IP-Zulassungslisten in ihren Umgebungen verwalten.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Einige Fälle von Fehlern im Codescans-Schritt ohne Angabe von Ergebnissen werden behoben.

* Auf der Umgebungskarte wird die **Hinzufügen** Schaltfläche.

## Code-Refaktorierungs-Tools {#code-refactoring-tools}

### Neue Funktionen in [!DNL Code Refactoring Tools] {#what-is-new-crt}

* Neue Version des AIO-CLI-Plug-ins veröffentlicht. Die neueste Version dieses Plug-ins enthält Fehlerbehebungen für den AEM Dispatcher Converter und den Repository Modernizer und unterstützt auch ein neues Dienstprogramm - Index Converter. Siehe [Einheitliches Experience](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/refactoring-tools/unified-experience.html#benefits) wo Sie mehr über dieses Plug-in erfahren können.

* Index Converter ist ein Dienstprogramm, mit dem die benutzerdefinierten Oak-Indexdefinitionen eines Kunden in AEM as a Cloud Service kompatible Oak-Indexdefinitionen umgewandelt werden können. Siehe [Index Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter) für weitere Details.

* Neue Funktion zu [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) hinzugefügt, die ein separates Paket `ui.config` erstellt, das alle OSGi-Konfigurationen enthält.

### Fehlerbehebungen {#crt-bug-fixes}

* Bei den AEM Dispatcher Converter- und Repository Modernizer-Tools wurden mehrere Fehlerkorrekturen vorgenommen. Siehe [AEM Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) und [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).

### Veröffentlichungsdatum {#release-date-ctt}

Die Version 1.1.20 von Content Transfer Tool wurde am 8. Januar 2021 veröffentlicht.

### Neue Funktionen in [!DNL Content Transfer Tool] {#what-is-new-ctt}

* Benutzer können nun erfahren, ob ihr Zugriffs-Token abgelaufen ist, indem sie den Mauszeiger auf das Statussymbol in der CTT-Benutzeroberfläche (Content Transfer Tool) bewegen. Sie werden auch in der Benutzeroberfläche &quot;Details zum Migrationssatz&quot;darüber informiert, dass sie keine Verbindung zu ihrer Cloud Service-Instanz herstellen können.

### Fehlerbehebungen {#ctt-bug-fixes}

* Der Status der CTT-Benutzeroberfläche (Content Transfer Tool) für einen Migrationssatz blieb nicht bestehen und wurde nach einer gewissen Zeit der Inaktivität geändert. Dieses Problem wurde behoben.
* Die Option zum Anzeigen von Protokollen wurde deaktiviert, wenn die Protokolle nicht verfügbar waren. Dieser Fehler wurde behoben und es wurden Nachrichten hinzugefügt, um Benutzer darüber zu informieren, warum Protokolle fehlen.
* Status der Benutzeroberfläche des Content Transfer Tool wurde angezeigt *FEHLGESCHLAGEN* wenn der Benutzer die Aufnahme angehalten hat. Dieses Problem wurde behoben, stattdessen wird jetzt *GESTOPPT* angezeigt.
