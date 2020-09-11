---
title: Versionshinweise für die Version 2020.9.0 [!DNL Adobe Experience Manager] von als Cloud Service.
description: '[!DNL Adobe Experience Manager] als Cloud Service-Versionshinweise für 2020.9.0.'
translation-type: tm+mt
source-git-commit: cca8aff3ada327252bfabd2207e7aa86fdf00033
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 20%

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
