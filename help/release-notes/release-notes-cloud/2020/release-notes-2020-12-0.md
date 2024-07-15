---
title: Versionshinweise für Version 2020.12.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2020.12.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 16875180-1f23-477d-9d4d-e220998c4983
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
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

* [!DNL Experience Manager] wurde erweitert, um Asset-Referenzen zu verfolgen und anzuzeigen, wenn ein Asset in einer Remote-Bereitstellung von [!DNL Experience Manager Sites] mithilfe der Funktion für Connected Assets verwendet wird. Auf der neuen Registerkarte [!UICONTROL Verweise] auf der Seite [!UICONTROL Eigenschaften] des Assets werden jetzt lokale und Remote-Verweise des Assets aufgelistet. Anhand der Referenzen können DAM-Benutzer die Asset-Nutzung auf [!DNL Sites]-Seiten und in zusammengesetzten Assets in [!DNL Assets] verfolgen. Weitere Informationen finden Sie unter [Konfigurieren und Verwenden von Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md).

* Die Funktionen von [!DNL Dynamic Media] sind jetzt über AEM bildbasierte Kernkomponenten [!DNL Sites] verfügbar. Autoren können Komponenten schnell konfigurieren, um Bildvorgaben, smarte Zuschnitte und Bildmodifikatoren beim Erstellen von Web-Seiten zu verwenden. Weitere Informationen finden Sie unter [Kernkomponenten Version 2.13.0](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.13.0).

* Mit dem Desktop-Programm [!DNL Experience Manager] können Benutzer Dateien und Ordner hochladen, indem sie die Dateien aus Windows Explorer oder Mac Finder in die Benutzeroberfläche des Desktop-Programms ziehen. Siehe [Hinzufügen von Assets mit dem Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de#upload-and-add-new-assets-to-aem).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Veröffentlicht CIF Venia-Referenz-Site 2020.12.01, die die neueste Version der CIF Kernkomponenten Version 1.6.0 enthält. Weitere Informationen finden Sie unter [CIF Venia-Referenz-Site](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.12.01) .

* Version 1.6.0 CIF Kernkomponenten veröffentlicht. Weitere Informationen finden Sie unter [CIF Kernkomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.6.0) .

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Die Version 2020.12.0 von Cloud Manager in Adobe Experience Manager (AEM) wurde am 10. Dezember 2020 veröffentlicht.

### Neue Funktionen in [!DNL Cloud Manager] {#what-is-new-cm}

* Self-Service-Verwaltung von [SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) und [benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/introduction.md).

* Self-Service-Verwaltung von [IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

* Auf der aktualisierten Detailseite **Umgebung** können Benutzer jetzt benutzerdefinierte Domänennamen und IP-Zulassungslisten in ihren Umgebungen verwalten.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Einige Fälle von Fehlern im Codescans-Schritt ohne Angabe von Ergebnissen werden behoben.

* Auf der Umgebungskarte wurde die Schaltfläche **Hinzufügen** nicht einheitlich angezeigt.

## Code-Refaktorierungs-Tools {#code-refactoring-tools}

### Neue Funktionen in [!DNL Code Refactoring Tools] {#what-is-new-crt}

* Neue Version des AIO-CLI-Plug-ins veröffentlicht. Die neueste Version dieses Plug-ins enthält Fehlerbehebungen für den AEM Dispatcher Converter und den Repository Modernizer und unterstützt auch ein neues Dienstprogramm - Index Converter. Weitere Informationen zu diesem Plug-in finden Sie unter [Einheitliches Erlebnis](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/refactoring-tools/unified-experience.html#benefits) .

* Index Converter ist ein Dienstprogramm, mit dem die benutzerdefinierten Oak-Indexdefinitionen eines Kunden in AEM as a Cloud Service-kompatible Oak-Indexdefinitionen umgewandelt werden können. Weitere Informationen finden Sie unter [Indexkonverter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter) .

* Neue Funktion zu [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) hinzugefügt, die ein separates Paket `ui.config` erstellt, das alle OSGi-Konfigurationen enthält.

### Fehlerbehebungen {#crt-bug-fixes}

* Mehrere Fehlerbehebungen wurden für die AEM Dispatcher Converter- und Repository Modernizer-Tools vorgenommen. Siehe [AEM Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) und [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).

### Veröffentlichungsdatum {#release-date-ctt}

Die Version 1.1.20 von Content Transfer Tool wurde am 8. Januar 2021 veröffentlicht.

### Neue Funktionen in [!DNL Content Transfer Tool] {#what-is-new-ctt}

* Benutzer können nun erfahren, ob ihr Zugriffs-Token abgelaufen ist, indem sie den Mauszeiger auf das Statussymbol in der CTT-Benutzeroberfläche (Content Transfer Tool) bewegen. Sie werden auch in der Benutzeroberfläche &quot;Details zum Migrationssatz&quot;darüber informiert, dass sie keine Verbindung zu ihrer Cloud Service-Instanz herstellen können.

### Fehlerbehebungen {#ctt-bug-fixes}

* Der Status der CTT-Benutzeroberfläche (Content Transfer Tool) für einen Migrationssatz blieb nicht bestehen und wurde nach einer gewissen Zeit der Inaktivität geändert. Dieses Problem wurde behoben.
* Die Option zum Anzeigen von Protokollen wurde deaktiviert, wenn die Protokolle nicht verfügbar waren. Dieser Fehler wurde behoben und es wurden Nachrichten hinzugefügt, um Benutzer darüber zu informieren, warum Protokolle fehlen.
* Der Benutzeroberflächenstatus des Content Transfer Tool zeigte *FEHLGESCHLAGEN* an, wenn der Benutzer eine Aufnahme angehalten hatte. Dieses Problem wurde behoben, stattdessen wird jetzt *GESTOPPT* angezeigt.
