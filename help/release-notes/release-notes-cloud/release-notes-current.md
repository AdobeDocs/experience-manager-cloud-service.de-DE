---
title: Versionshinweise für die Version 2020.9.0 [!DNL Adobe Experience Manager] von als Cloud Service.
description: '[!DNL Adobe Experience Manager] als Cloud Service-Versionshinweise für 2020.9.0.'
translation-type: tm+mt
source-git-commit: 24f7e9c1a99286d38332b1d4fa1b0ff9a7335069
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 17%

---


# Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service 2020.9.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager as a Cloud Service 2020.9.0 beschrieben.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### What is new in [!DNL Sites] {#what-is-new-sites}

* Das JavaScript-SDK für die Einzelseitenanwendung (SPA) Editor [ist jetzt Open Source.](/help/implementing/developing/spa/reference-materials.md)

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
