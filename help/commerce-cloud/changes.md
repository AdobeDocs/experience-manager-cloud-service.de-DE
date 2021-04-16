---
title: Wichtige Änderungen des CIF-Add-ons (Commerce Integration Framework)
description: Bemerkenswerte Änderungen des Commerce Integration Framework (CIF) im Vergleich zu alten CIF-Versionen.
exl-id: c136763f-56aa-450e-8796-bc84bf6c205d
translation-type: tm+mt
source-git-commit: 97574c964e757ffa4d108340f6a4d1819050d79a
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 15%

---

# Wichtige Änderungen am Commerce Integration Framework (CIF) Hinzufügen-on{#notable-changes}

Adobe Experience Manager as a Cloud Service bietet eine Vielzahl neuer Funktionen und Möglichkeiten für die Verwaltung Ihrer AEM-Projekte. Weitere Informationen zu diesen Funktionen finden Sie unter [Änderungen am Experience Manager als Cloud Service](/help/release-notes/aem-cloud-changes.md).

Dieses Dokument hebt die wichtigen Unterschiede zwischen dem Commerce Integration Framework (CIF) Add-On und alten CIF-Versionen hervor, die hauptsächlich CIF Classic (Quickstart) als CIF Open Source bezeichnet werden.

## Installation und Updates

Das AEM CIF-Add-on wird über Cloud Manager installiert. Die Installation erfordert eine CIF-Gutschrift, außer bei Sandboxen, in denen CIF ohne Gutschriften installiert werden kann. Die Gutschrift erfolgt automatisch über die Bereitstellung des CIF-Add-ons in Ihrem AEM.

Das Add-on wird im Rahmen des regulären AEM automatisch aktualisiert, wenn ein Cloud Service aktualisiert wird.

**Vorherige CIF-Versionen**

* CIF Classic: Keine Installation erforderlich, CIF war Teil des Quickstart. CIF-Aktualisierungen waren Teil regelmäßiger AEM- oder Service Pack-Aktualisierungen.
* CIF Open-Source für AEM On-Promis: Installation über GitHub. Aktualisierungen waren Teil der manuellen Aktualisierungs-/Wartungsarbeiten.
* CIF Open Source for AEM Adobe Managed Services: Installation über Customer Success Manager. Aktualisierungen waren Teil der manuellen Aktualisierungs-/Wartungsarbeiten.

## Endpunktkonfiguration

Der Endpunkt wird entweder über die Benutzeroberfläche von Cloud Manager oder die zugehörige CLI konfiguriert und aktualisiert.

**Vorherige CIF-Versionen**

* CIF Classic: Über OSGi-Konfiguration in AEM
* CIF Open Source: Über den CIF-Konfigurationsbrowser

## Bereitstellung des CIF-Venia-Projekts

Projekt verfügbar in [Cloud Manager Git Repository](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html) und Bereitstellung über [Cloud Manager](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/deploying/overview.html)

**Vorherige CIF-Versionen**

* CIF Classic: Über AEM Paketinstallation
* CIF Open Source: Über [Cloud Manager](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)

## Produktkatalogdaten

Produktkatalogdaten werden bei Bedarf über Echtzeitaufrufe an einen externen Endpunkt angefordert, der die erforderlichen GraphQL-APIs unterstützt. Diese APIs unterstützen den Zugriff auf Live- oder Stage-Daten zu jedem beliebigen Datum. Keine Replikation erforderlich.

**Vorherige CIF-Versionen**

* CIF Classic: Live- und Stage-Produktdaten werden über den vollständigen oder Delta-Produktimport in JCR unter AEM Author importiert und beibehalten. Live-Produktdaten werden in AEM Publish repliziert.

## Produktkatalog-Erlebnisse mit AEM Rendering

AEM rendert Produktkatalog-Erlebnisse spontan mit AEM Katalogvorlagen, die Produkten und Kategorien zugewiesen wurden. Keine Replikation erforderlich.

**Vorherige CIF-Versionen**

* CIF Classic: AEM Author erstellt mithilfe des Katalogentwurfstools eine AEM für jede Kategorie/jedes Produkt. Diese Seiten werden in AEM Publish repliziert.

>[!NOTE]
>
>Weitere Dokumentationen zur Verwendung von CIF mit AEM Managed Service oder AEM On-Premise finden Sie unter [Commerce Integration Framework](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html).
