---
title: Migration zum AEM Commerce Integration Framework (CIF)-Add-on
description: So migrieren Sie von einer alten Version zum AEM Commerce Integration Framework (CIF)-Add-On
translation-type: tm+mt
source-git-commit: cda25048e171f6aacd5349706ad4192965e703db
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 22%

---

# Migrationshandbuch für den Experience Manager Cloud Service {#cif-migration}

Dieses Handbuch hilft Ihnen dabei, die Bereiche zu identifizieren, die Sie für die Migration von Experience Manager Cloud Services aktualisieren müssen.

## CIF-Add-on

Für Experience Manager als Cloud Service ist das CIF-Add-on die einzige unterstützte Commerce-Integrationslösung für Adobe Commerce- und Drittanbieter-Commerce-Lösungen. Das CIF-Add-on wird für Kunden auf dem Experience Manager als Cloud Service automatisch bereitgestellt. Eine manuelle Bereitstellung ist nicht erforderlich. Siehe [Erste Schritte mit AEM Commerce als Cloud Service](getting-started.md).

Zur Unterstützung von Projekten, die CIF-Adoben bereitstellen, stellen Sie [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) bereit.

CIF-Add-on ist für AEM 6.5 sowie über das [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) verfügbar. Es ist kompatibel und bietet dieselben Funktionen wie das CIF-Add-on für Experience Manager als Cloud Service - es sind keine Anpassungen erforderlich.

Classic CIF mit seinen Abhängigkeiten ist nicht mehr verfügbar. Code, der auf diese CIF-Version mit `com.adobe.cq.commerce.api` Java-APIs basiert, muss an das CIF-Add-on und seine Prinzipien angepasst werden.

Der zuvor verfügbare CIF-Anschluss kann nicht mehr installiert werden. Der auf diesem Anschluss basierende Code muss an das CIF-Add-on und seine Prinzipien angepasst werden.

## Projektstruktur

Lernen Sie die [AEM Projektstruktur](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) und die Eigenschaften von AEM als Cloud Service kennen. Passen Sie Ihr Projekt-Setup an das Layout von AEM as a Cloud Service an.
Im Vergleich zu AEM 6.5-Bereitstellungen gibt es hier zwei Hauptunterschiede:

* Das GraphQL-Client-OSGi-Bundle **darf nicht** mehr in das AEM-Projekt aufgenommen werden, sondern wird über das CIF-Add-on bereitgestellt.
* OSGi-Konfigurationen für den GraphQL-Client und GraphQL Data Service **dürfen nicht** mehr in das AEM-Projekt aufgenommen werden.

>[!TIP]
>
>Sehen Sie sich das Projekt [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) auf GitHub an. Dieses Projekt bietet Maven-Profile für AEM as a Cloud Service und für On-Premise-Implementierungen, die den unterschiedlichen Rahmenbedingungen Rechnung tragen.

## Produktkatalog

Das Importieren von Produktkatalogdaten wird nicht mehr unterstützt. Die Verwendung der CIF-Add-On-Prinzipale für Produkt- und Kataloganforderungen erfolgt bei Bedarf über Echtzeitaufrufe an eine externe Commerce-Lösung. Gehen Sie zu Kapitel Integration, um mehr über die Integration einer Commerce-Lösung zu erfahren.

>[!TIP]
>
>Wenn keine Echtzeit-APIs verfügbar sind, sollte für die Integration ein externer Produkt-Cache mit APIs verwendet werden. Beispiel [Magento open-source](https://magento.com/products/magento-open-source).

## Produktkatalog-Erlebnisse mit AEM Rendering

Wenn Sie Katalogvorlagen mit Classic CIF verwenden, müssen Sie den Arbeitsablauf für Produktkataloge aktualisieren. Das CIF-Add-on rendert jetzt Produktkatalog-Erlebnisse im Handumdrehen mithilfe AEM Katalogvorlagen. Es ist keine Replikation von Produktdaten oder Produktseiten mehr erforderlich.

## Nicht zwischenspeicherbare Daten und Interaktionen beim Einkauf

Clientseitige Anfragen für nicht zwischengespeicherte Daten und Interaktionen (z.B. Add-to-cart, Suche) sollten direkt über CDN/Dispatcher an den Commerce-Endpunkt (entweder Commerce-Lösung oder Integrationsebene) gesendet werden. Entfernen Sie alle Aufrufe, bei denen AEM nur ein Proxy war.
