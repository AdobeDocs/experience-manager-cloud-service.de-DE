---
title: Versionshinweise für die Version 2020.9.0 [!DNL Adobe Experience Manager] von als Cloud Service.
description: '[!DNL Adobe Experience Manager] als Cloud Service-Versionshinweise für 2020.9.0.'
translation-type: tm+mt
source-git-commit: f39b03455fc03104932952b892b88403d0c9eca7
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 15%

---


# Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service 2020.9.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager as a Cloud Service 2020.9.0 beschrieben.

## Veröffentlichungsdatum {#release-date}

The Release Date for [!DNL Adobe Experience Manager] as a Cloud Service 2020.9.0 is September 24, 2020.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### What is new in [!DNL Sites] {#what-is-new-sites}

* Das Single Page Application (SPA) Editor JavaScript SDK [ist jetzt Open Source.](/help/implementing/developing/spa/reference-materials.md)

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### What is new in [!DNL Assets] {#what-is-new-assets}

* Das Wasserzeichen eines PNG-Bildes wird für Darstellungen unterstützt, die mit Asset-Mikrodiensten generiert wurden. Es kann als verarbeitendes Profil konfiguriert werden.

* Verbesserungen in [!DNL Dynamic Media]

   * Selektive Veröffentlichung - Ein Marketingteam kann nun auf [!DNL Dynamic Media] intelligente Schnittbilder und dynamische Darstellungen zugreifen, mit denen synchronisiert wird, [!DNL Dynamic Media] [!DNL Dynamic Media] sodass sie Werbematerialien erstellen können, ohne diese Assets für den weltweiten Versand veröffentlichen zu müssen. AEM und [!DNL Dynamic Media] Verlagswesen sind entkoppelt und können dazu separat durchgeführt werden.
   * Administratoren können das Kennwort für [!DNL Dynamic Media] Cloud Service, das bei der Bereitstellung direkt in AEM Benutzeroberfläche erhalten wurde, ohne dass die [!DNL Dynamic Media Classic] Desktop-App verwendet werden muss, zurücksetzen.

* Weitere Informationen zu den folgenden Verbesserungen finden Sie unter [Neue Funktionen im Markenportal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/whats-new.html).

   * Verbesserte PDF-Vorschau mit Adobe Document Cloud Ansicht SDK-Integration.
   * Download-Funktion mit einem Klick.
   * Neue Verwaltungskonfigurationen für das Download-Erlebnis.

<!--
### Bugs Fixed {#bugs-fixed-assets}

TBD: list of Assets aaCS bugs that are fixed.
-->

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Version 1.3.0 der CIF-Kernkomponenten Weitere Informationen finden Sie unter [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.3.0) .

* Vorschau mit Produkt/Kategorie für Produkt- und Kategorie-Vorlagen ist jetzt verfügbar. Auf diese Weise können Geschäftsbenutzer/Marketingexperten in AEM die Produkt-/Kategorie-Vorlagen mit echten Daten Ansicht werden.

* Eigenschaftenseite zu Produkten und Kategorien hinzugefügt, damit Geschäftsbenutzer Details zur Ansicht der Produkt-SKU/Kategorien-ID eingeben können.

* Sortierungsfunktion, die der Produktkonsole hinzugefügt wurde, um das Sortieren von Produkten/Kategorien nach Namen oder Preisattributen zu ermöglichen.

* Produktsuchfunktion hinzugefügt.

### Fehlerbehebungen {#bug-fixes-commerce}

* Bei den Commerce Cloud-Konfigurationen wurde die Vererbung nicht berücksichtigt. Dieser Fehler wurde behoben, um sicherzustellen, dass die Konfiguration Werte erbt.

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Die Version 2020.9.0 von [!UICONTROL Cloud Manager] wurde am 03. September 2020 veröffentlicht.

### Neuerungen {#what-is-new-cloud-manager}

* Content Audit wurde als Experience Audit umbenannt.
* Der Build-Prozess wurde in drei separate Maven-Befehle unterteilt.
* Wenn das Git-Repository nicht geklont werden kann, wird es bis zu dreimal erneut versucht.

### Fehlerbehebungen {#bug-fixes-cm}

* Auf der Registerkarte &quot;Content Audit&quot;wurde die Basis-URL fälschlicherweise unter Verwendung der Autorendomäne und nicht der Veröffentlichungsdomäne angezeigt.

## Cloud Readiness Analyzer {#cloud-readiness-analyzer}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für Cloud Readiness Analyzer Version 1.1.0.

### Neue Funktionen {#what-is-new-cra}

* Die CRA (Cloud Readiness Analyzer) verfügt über eine Beginn-Statuskonsole, die eine explizite Schaltfläche zum **Generieren eines Berichts** anzeigt, auf die der Benutzer klicken kann, um die CRA auszuführen.

* Die CRA-Benutzeroberfläche zeigt den Fortschritt während der Ausführung an. Es zeigt Elemente an, die analysiert werden, und die während der Ausführung gefundenen Ergebnisse.

* Der CRA-Bericht enthält eine Zusammenfassung und die Anzahl der Ergebnisse in Tabellenform, die nach Art der Befunde und der Wichtigkeitsstufe geordnet sind. Wenn Sie auf die Anzahl dieser Suche klicken, wird automatisch ein Bildlauf zur Position dieser Suche im Bericht durchgeführt.

### Fehlerbehebungen {#cra-bug-fixes}

* In bestimmten Fällen wurde der CRA-Bericht nach der erzwungenen Aktualisierung nicht aktualisiert. Dieses Problem wurde in dieser Version behoben.

## Content Transfer-Tool {#content-transfer-tool}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für Content Transfer Tool Release v1.1.10.

### Neue Funktionen {#what-is-new-ctt}

* Das Content Transfer Tool (CTT) unterstützt den Blue Blob Store Data Store.

* Die CTT-Benutzeroberfläche verfügt über eine Funktion zum automatischen Neuladen, mit der die Übersichtsseite alle 30 Sekunden neu geladen wird.

* Schaltfläche zur CTT-Benutzeroberfläche hinzugefügt, um *Zugriffstoken* einfach abzurufen.

* Beschreibende Überprüfungsmeldung hinzugefügt für *URL* und *Migrationssatzname*.
