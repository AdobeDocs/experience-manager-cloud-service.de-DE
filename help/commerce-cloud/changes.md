---
title: Wesentliche Änderungen des CIF-Add-ons (Commerce Integration Framework)
description: Wesentliche Änderungen des CIF-Add-ons im Vergleich zu alten CIF-Versionen.
exl-id: 5a526960-96a1-421e-9fb0-0825e7df8f32,c136763f-56aa-450e-8796-bc84bf6c205d
source-git-commit: ac64ca485391d843c0ebefcf86e80b4015b72b2f
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 98%

---

# Wesentliche Änderungen des CIF-Add-ons{#notable-changes}

Adobe Experience Manager as a Cloud Service bietet eine Vielzahl neuer Funktionen und Möglichkeiten für die Verwaltung Ihrer AEM-Projekte. Weitere Informationen zu diesen Funktionen finden Sie unter [Änderungen an Experience Manager as a Cloud Service](/help/release-notes/aem-cloud-changes.md).

In diesem Dokument werden die wichtigen Unterschiede zwischen dem CIF-Add-on und alten CIF-Versionen, hauptsächlich bekannt als CIF Classic (Schnellstart) und CIF Open-Source, erläutert.

## Installation und Updates

Das AEM CIF-Add-on wird über Cloud Manager installiert. Die Installation erfordert eine CIF-Gutschrift, außer für Sandboxes, in denen CIF ohne Gutschriften installiert werden kann. Sie erhalten Gutschriften automatisch über die Bereitstellung des CIF-Add-ons in Ihrem AEM-Vertrag.

Das Add-on wird im Rahmen des regulären AEM as a Cloud Service automatisch aktualisiert.

**Vorherige CIF-Versionen**

* CIF Classic: Keine Installation erforderlich, CIF war Teil des Schnellstarts. CIF-Updates waren Teil regelmäßiger AEM- oder Service Pack-Updates.
* CIF Open-Source für AEM On-Premise: Installation über GitHub. Updates waren Teil der manuellen Aktualisierung/Wartung.
* CIF Open-Source für AEM Adobe Managed Services: Installation über Customer Success Manager. Updates waren Teil der manuellen Aktualisierung/Wartung.

## Konfiguration des Endpunkts

Der Endpunkt wird entweder über die Cloud Manager-Benutzeroberfläche oder die zugehörige CLI konfiguriert und aktualisiert.

**Vorherige CIF-Versionen**

* CIF Classic: Über die OSGi-Konfiguration in AEM
* CIF Open-Source: Über den CIF-Konfigurations-Browser

## Implementierung des CIF-Venia-Projekts

Projekt ist im [Cloud Manager-Git-Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/managing-code/integrating-with-git.html) verfügbar und Implementierung erfolgt über [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=de).

**Vorherige CIF-Versionen**

* CIF Classic: Über AEM Package-Installation
* CIF Open-Source: Über [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=de)

## Produktkatalogdaten

Produktkatalogdaten werden bei Bedarf über Echtzeitaufrufe an einen externen Endpunkt, der die erforderlichen GraphQL-APIs unterstützt, angefragt. Diese APIs unterstützen den Zugriff auf Live- oder Staging-Daten zu einem beliebigen Zeitpunkt. Es ist keine Replikation erforderlich.

**Vorherige CIF-Versionen**

* CIF Classic: Live- und Staging-Produktdaten werden in JCR in der AEM-Autoreninstanz über den vollständigen oder einen Delta-Produktimport importiert und beibehalten. Live-Produktdaten werden in die AEM-Veröffentlichungsinstanz repliziert.

## Produktkatalogerlebnisse mit AEM-Rendering

AEM rendert Produktkatalog-Erlebnisse direkt mithilfe von AEM-Katalogvorlagen, die Produkten und Kategorien zugewiesen wurden. Es ist keine Replikation erforderlich.

**Vorherige CIF-Versionen**

* CIF Classic: Die AEM-Autoreninstanz erstellt mit dem Katalog-Blueprint-Tool eine AEM-Seite für jede Kategorie / jedes Produkt. Diese Seiten werden zur AEM-Veröffentlichungsinstanz repliziert.

>[!NOTE]
>
>Weitere Dokumentationen zur Verwendung von CIF mit AEM Managed Service oder AEM On-Premise finden Sie unter [Commerce Integration Framework](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html).
