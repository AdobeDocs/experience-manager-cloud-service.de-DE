---
title: Versionshinweise für Version 2020.12.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2020.12.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 16875180-1f23-477d-9d4d-e220998c4983
feature: Release Information
role: Admin
source-git-commit: 64344b9b2cce8d7c7f05d3e5ba94049346308a9d
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 51%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!DNL Experience Manager] as a Cloud Service beschrieben.

## Veröffentlichungsdatum {#release-date}

Die Version 2020.12.0 von [!DNL Adobe Experience Manager] as a Cloud Service wurde am 17. Dezember 2020 veröffentlicht.
Die folgende Version (2021.1.0) wurde am 28. Januar 2021 veröffentlicht.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* **[HTTP-API für Inhaltsfragmente](/help/assets/content-fragments/assets-api-content-fragments.md)**: Hinzufügen der Möglichkeit zum Hinzufügen/Aktualisieren und Löschen von Varianten von Inhaltsfragmenten über die HTTP-API.

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

* Die Integration mit [!DNL Adobe InDesign Server] ist jetzt für [!DNL Experience Manager] as a [!DNL Cloud Service] verfügbar. Sie bietet Automatisierung zur Verarbeitung von [!DNL Adobe InDesign]-Dateien mithilfe von [!DNL Adobe InDesign Server]-Skripten und ermöglicht Benutzern die Verwendung der [!DNL Assets]-Vorlagen-Benutzeroberfläche zum Erstellen von Prospekten oder Anzeigen. Nur der von [!DNL Adobe Managed Services] gehostete [!DNL InDesign Server] wird für [!DNL Experience Manager as a Cloud Service] unterstützt. <!-- TBD: Add link to article. -->

* [!DNL Experience Manager] wurde erweitert, um Asset-Referenzen zu verfolgen und anzuzeigen, wenn ein Asset in einer Remote-Bereitstellung von [!DNL Experience Manager Sites] mithilfe der Funktion für Connected Assets verwendet wird. Die neue [!UICONTROL Verweise] auf der Seite [!UICONTROL Eigenschaften] des Assets listet jetzt lokale und Remote-Verweise des Assets auf. Anhand der Referenzen können DAM-Benutzer die Asset-Nutzung auf [!DNL Sites]-Seiten und in zusammengesetzten Assets in [!DNL Assets] verfolgen. Weitere Informationen finden Sie unter [Konfigurieren und Verwenden von Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md).

* [!DNL Dynamic Media] Funktionen sind jetzt über AEM- [!DNL Sites] bildbasierte Kernkomponenten verfügbar. Autoren können Komponenten schnell konfigurieren, um Bildvorgaben, smarte Zuschnitte und Bildmodifikatoren beim Erstellen von Web-Seiten zu verwenden. Weitere Informationen finden Sie unter [Kernkomponenten Version 2.13.0](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.13.0).

* Mit dem [!DNL Experience Manager] Desktop-Programm können Benutzer Dateien und Ordner hochladen, indem sie die Dateien aus dem Windows Explorer oder Mac Finder auf die Benutzeroberfläche des Desktop-Programms ziehen. Siehe [Hinzufügen von Assets mit dem Desktop-Programm](https://experienceleague.adobe.com/en/docs/experience-manager-desktop-app/using/using#upload-and-add-new-assets-to-aem).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Freigabe der CIF Venia-Referenz-Website 2020.12.01, die die aktuelle CIF-Kernkomponenten Version 1.6.0 enthält. Weitere Informationen finden Sie unter [CIF Venia](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.12.01)Referenz-Site .

* Version 1.6.0 von CIF-Kernkomponenten veröffentlicht. Weitere Informationen finden Sie unter {](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.6.0)}CIF-Kernkomponenten.[

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Die Version as a Cloud Service 2020.12.0 von Cloud Manager in Adobe Experience Manager (AEM) wurde am 10. Dezember 2020 veröffentlicht.

### Neue Funktionen in [!DNL Cloud Manager] {#what-is-new-cm}

* Self-Service-Management von [SSL-](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md)) und [Einführung in benutzerdefinierte Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/introduction.md).

* Self-Service-Verwaltung von [IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

* Auf der aktualisierten Seite mit den Informationen zur **Umgebung** können Benutzerinnen und Benutzer jetzt benutzerdefinierte Domain-Namen und IP-Zulassungslisten für ihre Umgebungen verwalten.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Einige Fehler beim Scannen von Code ohne Bereitstellung von Ergebnissen werden behoben.

* Die Schaltfläche **Hinzufügen** wurde auf der Umgebungskarte nicht konsistent angezeigt.

## Code-Refaktorierungs-Tools {#code-refactoring-tools}

### Neue Funktionen in [!DNL Code Refactoring Tools] {#what-is-new-crt}

* Neue Version des AIO-CLI-Plug-ins veröffentlicht. Die neueste Version dieses Plug-ins enthält Fehlerbehebungen für AEM Dispatcher Converter und Repository Modernizer und unterstützt außerdem ein neues Dienstprogramm: Index Converter. Weitere [ zu diesem Plug-in finden ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/migration-journey/refactoring-tools/unified-experience#benefits) unter „Einheitliches“.

* Index Converter ist ein Dienstprogramm, mit dem Sie die benutzerdefinierten Oak-Indexdefinitionen eines Kunden in AEM as a Cloud Service-kompatible Oak-Indexdefinitionen umwandeln können. Weitere Informationen finden [ unter ](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)Index Converter“.

* Neue Funktion zu [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) hinzugefügt, die ein separates Paket `ui.config` erstellt, das alle OSGi-Konfigurationen enthält.

### Fehlerbehebungen {#crt-bug-fixes}

* Mehrere Fehlerbehebungen wurden in den AEM Dispatcher Converter- und Repository Modernizer-Tools vorgenommen. Siehe [AEM Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) und [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).

### Veröffentlichungsdatum {#release-date-ctt}

Die Version 1.1.20 von Content Transfer Tool wurde am 8. Januar 2021 veröffentlicht.

### Neue Funktionen in [!DNL Content Transfer Tool] {#what-is-new-ctt}

* Benutzer können nun erfahren, ob ihr Zugriffs-Token abgelaufen ist, indem sie den Mauszeiger auf das Statussymbol in der CTT-Benutzeroberfläche (Content Transfer Tool) bewegen. Sie werden auch in der Benutzeroberfläche „Details zum Migrationssatz“ darüber informiert, dass sie keine Verbindung zu ihrer Cloud Service-Instanz herstellen können.

### Fehlerbehebungen {#ctt-bug-fixes}

* Der Status der CTT-Benutzeroberfläche (Content Transfer Tool) für einen Migrationssatz blieb nicht bestehen und wurde nach einer gewissen Zeit der Inaktivität geändert. Dieses Problem wurde jetzt behoben.
* Die Option zum Anzeigen von Protokollen war deaktiviert, wenn die Protokolle nicht verfügbar waren. Dieses Problem wurde behoben und jetzt wird eine Meldung hinzugefügt, die Benutzer darüber informiert, warum Protokolle fehlen.
* Der Benutzeroberflächenstatus des Content Transfer Tools *FEHLGESCHLAGEN) angezeigt,* der Benutzer eine Aufnahme gestoppt hat. Dieses Problem wurde nun behoben und zeigt stattdessen *STOPPED* an.
