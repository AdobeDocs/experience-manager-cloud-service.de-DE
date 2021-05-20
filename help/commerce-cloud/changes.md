---
title: Wesentliche Änderungen des CIF-Add-ons (Commerce Integration Framework)
description: Wesentliche Änderungen des Commerce Integration Framework (CIF) im Vergleich zu alten CIF-Versionen.
exl-id: 5a526960-96a1-421e-9fb0-0825e7df8f32,c136763f-56aa-450e-8796-bc84bf6c205d
source-git-commit: 7a52e4b62f5a18f9c68e5afb0d464bd11be732d2
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 15%

---

# Wesentliche Änderungen am Commerce Integration Framework (CIF) Add-on{#notable-changes}

Adobe Experience Manager as a Cloud Service bietet eine Vielzahl neuer Funktionen und Möglichkeiten für die Verwaltung Ihrer AEM-Projekte. Weitere Informationen zu diesen Funktionen finden Sie unter [Änderungen an Experience Manager as a Cloud Service](/help/release-notes/aem-cloud-changes.md).

In diesem Dokument werden die wichtigen Unterschiede zwischen dem Commerce Integration Framework (CIF)-Add-on und alten CIF-Versionen, hauptsächlich CIF Classic (Quickstart) und CIF Open Source, erläutert.

## Installation und Updates

Das AEM CIF-Add-on wird über Cloud Manager installiert. Die Installation erfordert eine CIF-Gutschrift, außer für Sandboxes, in denen CIF ohne Gutschriften installiert werden kann. Kredit werden automatisch über die Bereitstellung des CIF-Add-ons in Ihrem AEM-Vertrag erhalten.

Das Add-on wird im Rahmen der regulären AEM automatisch aktualisiert, wenn ein Cloud Service aktualisiert wird.

**Vorherige CIF-Versionen**

* CIF Classic: Keine Installation erforderlich, CIF war Teil des Schnellstarts. CIF-Aktualisierungen waren Teil regelmäßiger AEM- oder Service Pack-Aktualisierungen
* CIF Open Source für AEM On-Premise: Installation über GitHub. Aktualisierungen waren Teil der manuellen Aktualisierung/Wartung.
* CIF Open Source für AEM Adobe Managed Services: Installation über Customer Success Manager. Aktualisierungen waren Teil der manuellen Aktualisierung/Wartung.

## Endpunktkonfiguration

Der Endpunkt wird entweder über die Cloud Manager-Benutzeroberfläche oder die zugehörige CLI konfiguriert und aktualisiert.

**Vorherige CIF-Versionen**

* CIF Classic: Über die OSGi-Konfiguration in AEM
* CIF Open Source: Über den CIF-Konfigurationsbrowser

## Implementierung des CIF-Venia-Projekts

Projekt verfügbar im [Cloud Manager-Git-Repository](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html) und Bereitstellung über [Cloud Manager](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/deploying/overview.html)

**Vorherige CIF-Versionen**

* CIF Classic: Über AEM Paketinstallation
* CIF Open Source: Über [Cloud Manager](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)

## Produktkatalogdaten

Produktkatalogdaten werden bei Bedarf über Echtzeitaufrufe an einen externen Endpunkt angefordert, der die erforderlichen GraphQL-APIs unterstützt. Diese APIs unterstützen den Zugriff auf Live- oder Staging-Daten zu einem beliebigen Zeitpunkt. Keine Replikation erforderlich.

**Vorherige CIF-Versionen**

* CIF Classic: Live- und gestaffelte Produktdaten werden in JCR in der AEM-Autoreninstanz über den vollständigen oder Delta-Produktimport importiert und beibehalten. Live-Produktdaten werden in AEM Publish repliziert.

## Produktkatalogerlebnisse mit AEM Rendering

AEM rendert Produktkatalog-Erlebnisse direkt mithilfe AEM Katalogvorlagen, die Produkten und Kategorien zugewiesen wurden. Keine Replikation erforderlich.

**Vorherige CIF-Versionen**

* CIF Classic: Die AEM-Autoreninstanz erstellt mit dem Katalog-Blueprint-Tool eine AEM für jede Kategorie/jedes Produkt. Diese Seiten werden in AEM Publish repliziert.

>[!NOTE]
>
>Weitere Dokumentationen zur Verwendung von CIF mit AEM Managed Service oder AEM On-Premise finden Sie unter [Commerce Integration Framework](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html).
