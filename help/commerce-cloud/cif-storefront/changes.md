---
title: Wesentliche Änderungen des CIF-Add-ons (Commerce Integration Framework)
description: Wesentliche Änderungen des CIF-Add-ons im Vergleich zu alten CIF-Versionen.
exl-id: 5a526960-96a1-421e-9fb0-0825e7df8f32
feature: Commerce Integration Framework
role: Admin
source-git-commit: 856442039fcd25ec675a6258d182f7a35f590c3c
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 84%

---


# Wesentliche Änderungen des CIF-Add-ons {#notable-changes}

Adobe Experience Manager as a Cloud Service bietet eine Vielzahl neuer Funktionen und Möglichkeiten für die Verwaltung Ihrer AEM-Projekte. Weitere Informationen zu diesen Funktionen finden Sie unter dem Link [Änderungen an Experience Manager as a Cloud Service.](/help/release-notes/aem-cloud-changes.md)

In diesem Dokument werden die wichtigsten Unterschiede zwischen dem Add-on Commerce Integration Framework (CIF) und den alten CIF-Versionen, bekannt als CIF Classic (Quickstart) und CIF Open-Source, hervorgehoben.

## Installation und Updates

Das AEM CIF-Add-on wird über Cloud Manager installiert. Die Installation erfordert eine CIF-Gutschrift, außer für Sandboxes, in denen CIF ohne Gutschriften installiert werden kann. Sie erhalten Gutschriften automatisch über die Bereitstellung des CIF-Add-ons in Ihrem AEM-Vertrag.

Das Add-on wird im Rahmen der regulären AEM as a Cloud Service-Aktualisierungen automatisch aktualisiert.

### Frühere CIF-Versionen {#previous-versions-installation}

* CIF Classic: Keine Installation erforderlich, CIF war Teil des Schnellstarts. CIF-Updates waren Teil regelmäßiger AEM- oder Service Pack-Updates.
* CIF Open-Source für AEM On-Premise: Installation über GitHub. Updates waren Teil der manuellen Aktualisierung/Wartung.
* CIF Open-Source für AEM Adobe Managed Services: Installation über das Adobe-Konto-Team. Updates waren Teil der manuellen Aktualisierung/Wartung.

## Konfiguration des Endpunkts {#endpoint-configuration}

Der Endpunkt wird entweder über die Cloud Manager-Benutzeroberfläche oder die zugehörige CLI konfiguriert und aktualisiert.

### Frühere CIF-Versionen {#previous-versions-endpoint}

* CIF Classic: Über die OSGi-Konfiguration in AEM
* CIF Open-Source: Über den CIF-Konfigurations-Browser

## Bereitstellung des CIF-Venia-Projekts {#venia-project}

Projekt verfügbar im [Cloud Manager Git-Repository](/help/implementing/cloud-manager/managing-code/integrating-with-git.md) Bereitstellung erfolgt über [Cloud Manager.](/help/implementing/deploying/overview.md)

### Frühere CIF-Versionen {#previous-versions-venia}

* CIF Classic: Über AEM Paketinstallation
* CIF Open-Source: Über [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html?lang=de)

## Produktkatalogdaten {#product-catalog-data}

Produktkatalogdaten werden bei Bedarf über Echtzeitaufrufe an einen externen Endpunkt, der die erforderlichen GraphQL-APIs unterstützt, angefragt. Diese APIs unterstützen den Zugriff auf Live- oder Staging-Daten zu einem beliebigen Zeitpunkt. Es ist keine Replikation erforderlich.

### Frühere CIF-Versionen {#previous-versions-catalog}

* CIF Classic: Live- und Staging-Produktdaten werden in JCR in der AEM-Autoreninstanz über den vollständigen oder einen Delta-Produktimport importiert und beibehalten. Live-Produktdaten werden in die AEM-Veröffentlichungsinstanz repliziert.

## Produktkatalogerlebnisse mit AEM-Rendering {#catalog-experiences}

AEM rendert Produktkatalog-Erlebnisse direkt mithilfe von AEM-Katalogvorlagen, die Produkten und Kategorien zugewiesen wurden. Es ist keine Replikation erforderlich.

### Frühere CIF-Versionen {#previous-cif-versions}

* CIF Classic: Die AEM-Autoreninstanz erstellt mit dem Katalog-Blueprint-Tool eine AEM-Seite für jede Kategorie / jedes Produkt. Diese Seiten werden zur AEM-Veröffentlichungsinstanz repliziert.

>[!NOTE]
>
>Weitere Dokumentationen zur Verwendung von CIF mit AEM Managed Service oder AEM On-Premise finden Sie unter [Commerce integration framework.](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html)
