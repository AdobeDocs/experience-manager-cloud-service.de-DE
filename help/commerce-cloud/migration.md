---
title: Migration zum AEM Commerce Integration Framework (CIF)-Add-on
description: Migrieren zum AEM Commerce Integration Framework (CIF)-Add-on von einer alten Version
exl-id: 0db03a05-f527-4853-b52f-f113bce929cf
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 21%

---

# Migrationshandbuch für den Experience Manager Cloud Service {#cif-migration}

Dieses Handbuch hilft dabei, die Bereiche zu identifizieren, die für die Migration von Experience Manager Cloud Services aktualisiert werden müssen.

## CIF-Add-on

Für Experience Manager as a Cloud Service ist das CIF-Add-on die einzige unterstützte Commerce-Integrationslösung für Adobe Commerce- und Drittanbieter-Commerce-Lösungen. Das CIF-Add-on wird automatisch für Kunden auf dem Experience Manager als Cloud Service bereitgestellt. Es ist keine manuelle Bereitstellung erforderlich. Siehe [Erste Schritte mit AEM Commerce as a Cloud Service](getting-started.md).

Um Projekte zu unterstützen, die CIF-Adobe bereitstellen, stellen Sie [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) bereit.

Das CIF-Add-on ist auch für AEM 6.5 über das [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) verfügbar. Es ist kompatibel und bietet dieselben Funktionen wie das CIF-Add-on für Experience Manager als Cloud Service - es sind keine Anpassungen erforderlich.

Classic CIF mit seinen Abhängigkeiten ist nicht mehr verfügbar. Code, der auf diese CIF-Version mit `com.adobe.cq.commerce.api` Java-APIs angewiesen ist, muss an das CIF-Add-on und dessen Prinzipien angepasst werden.

Der zuvor verfügbare CIF-Connector kann nicht mehr installiert werden. Der auf diesen Connector bezogene Code muss an das CIF-Add-on und dessen Prinzipien angepasst werden.

## Projektstruktur

Lernen Sie die [AEM Projektstruktur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=de) und die Eigenschaften von AEM als Cloud Service kennen. Passen Sie Ihr Projekt-Setup an das Layout von AEM as a Cloud Service an.
Im Vergleich zu AEM 6.5-Implementierungen gibt es hier zwei Hauptunterschiede:

* Das GraphQL-Client-OSGi-Bundle **darf nicht** mehr in das AEM-Projekt aufgenommen werden, sondern wird über das CIF-Add-on bereitgestellt.
* OSGi-Konfigurationen für den GraphQL-Client und GraphQL Data Service **dürfen nicht** mehr in das AEM-Projekt aufgenommen werden.

>[!TIP]
>
>Sehen Sie sich das Projekt [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) auf GitHub an. Dieses Projekt bietet Maven-Profile für AEM as a Cloud Service und für On-Premise-Implementierungen, die den unterschiedlichen Rahmenbedingungen Rechnung tragen.

## Produktkatalog

Der Import von Produktkatalogdaten wird nicht mehr unterstützt. Die Verwendung der CIF-Add-on-Prinzipale für Produkt- und Kataloganforderungen erfolgt über Echtzeitaufrufe an eine externe Commerce-Lösung. Gehen Sie zu Kapitel-Integration , um mehr über die Integration einer Commerce-Lösung zu erfahren.

>[!TIP]
>
>Wenn keine Echtzeit-APIs verfügbar sind, sollte für die Integration ein externer Produkt-Cache mit APIs verwendet werden. Beispiel [Magento open-source](https://magento.com/products/magento-open-source).

## Produktkatalogerlebnisse mit AEM Rendering

Wenn Sie den Katalog-Blueprint mit Classic CIF verwenden, müssen Sie den Workflow für den Produktkatalog aktualisieren. Das CIF-Add-on rendert jetzt Produktkatalog-Erlebnisse mithilfe AEM Katalogvorlagen direkt. Es ist keine Replikation von Produktdaten oder Produktseiten mehr erforderlich.

## Nicht zwischenspeicherbare Daten und Interaktionen mit Einkäufen

Clientseitige Anforderungen für nicht zwischenspeicherbare Daten und Interaktionen (z. B. Add-to-Warenkorb, Suche) sollten direkt über CDN/Dispatcher an den Commerce-Endpunkt (entweder Commerce-Lösung oder Integrationsschicht) gesendet werden. Entfernen Sie alle Aufrufe, bei denen AEM nur ein Proxy war.
