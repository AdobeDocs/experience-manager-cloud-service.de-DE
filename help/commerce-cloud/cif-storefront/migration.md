---
title: Migration zum Add-on für das AEM Commerce Integration Framework (CIF)
description: Migrieren zum Add-on für das AEM Commerce Integration Framework (CIF) von einer alten Version
exl-id: 0db03a05-f527-4853-b52f-f113bce929cf
feature: Commerce Integration Framework
role: Admin
index: false
source-git-commit: 0664e5dc4a7619a52cd28c171a44ba02c592ea3d
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 73%

---


# Leitfaden zur Migration für Experience Manager Cloud Service {#cif-migration}

Dieser Leitfaden hilft bei der Identifizierung von Bereichen, die für die Experience Manager Cloud Service-Migration aktualisiert werden müssen.

## CIF-Add-on {#cif-add-on}

Für Experience Manager as a Cloud Service ist das CIF-Add-on die einzige unterstützte Commerce-Integrationslösung für Adobe Commerce und Commerce-Lösungen von Drittanbietern. Das CIF-Add-on wird für Kunden automatisch für Experience Manager as a Cloud Service bereitgestellt. Es ist keine manuelle Implementierung erforderlich. Siehe [Erste Schritte mit AEM Commerce as a Cloud Service.](/help/commerce-cloud/cif-storefront/getting-started.md)

Um Projekte mit CIF Adobe zu unterstützen, stellen Sie [AEM CIF-Kernkomponenten bereit.](https://github.com/adobe/aem-core-cif-components)

Das CIF-Add-on ist auch für AEM 6.5 über das [Software Distribution-Portal verfügbar.](/help/implementing/developing/tools/package-manager.md) Es ist kompatibel und bietet dieselben Funktionen wie das CIF-Add-on für Experience Manager as a Cloud Service. Es sind keine Anpassungen erforderlich.

Das klassische CIF mit seinen Abhängigkeiten ist nicht mehr verfügbar. Code, der sich auf diese CIF-Version mit `com.adobe.cq.commerce.api`-Java-APIs stützt, muss an das CIF-Add-on und dessen Prinzipien angepasst werden.

Der zuvor verfügbare CIF-Connector kann nicht mehr installiert werden. Code, der sich auf diesen Connector stützt, muss an das CIF-Add-on und dessen Prinzipien angepasst werden.

## Projektstruktur {#project-structure}

Machen Sie sich mit der [AEM-Projektstruktur](/help/implementing/developing/introduction/aem-project-content-package-structure.md) und der Funktionsweise von AEM as a Cloud Service vertraut. Passen Sie Ihr Projekt-Setup an das AEM as a Cloud Service-Layout an.

Im Vergleich zu AEM 6.5-Bereitstellungen gibt es zwei wesentliche Unterschiede:

* Das GraphQL Client OSGi **Bundle darf nicht** mehr in das AEM-Projekt aufgenommen werden, es wird über das CIF-Add-on bereitgestellt
* OSGi-Konfigurationen für den GraphQL-Client und den GraphQL **Datendienst** nicht mehr in das AEM-Projekt aufgenommen werden.

>[!TIP]
>
>Sehen Sie sich das Projekt [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) auf GitHub an. Dieses Projekt bietet Maven-Profile für AEM as a Cloud Service und für On-Premise-Bereitstellungen, die den unterschiedlichen Rahmenbedingungen Rechnung tragen.

## Produktkatalog {#product-catalog}

Das Importieren von Produktkatalogdaten wird nicht mehr unterstützt. Die Verwendung der CIF-Add-on-Prinzipale für Produkt- und Kataloganforderungen erfolgt über Echtzeit-Aufrufe an eine externe Commerce-Lösung. Wechseln Sie zum Kapitel über Integration, um mehr über die Integration von Commerce-Lösungen zu erfahren.

>[!TIP]
>
>Wenn keine Echtzeit-APIs verfügbar sind, sollte für die Integration ein externer Produkt-Cache mit APIs verwendet werden. Beispiel: [Magento Open-Source.](https://business.adobe.com/de/products/magento/open-source.html)

## Produktkatalog-Erlebnisse mit AEM-Rendering {#aem-rendering}

Wenn Sie die Katalog-Blueprint mit dem klassischen CIF verwenden, müssen Sie den Workflow für den Produktkatalog aktualisieren. Das CIF-Add-on rendert Produktkatalog-Erlebnisse mithilfe von AEM-Katalogvorlagen nun direkt. Das Replizieren von Produktdaten oder Produktseiten ist nicht mehr erforderlich.

## Nicht Cache-taugliche Daten und Shopping-Interaktionen {#non-cacheable}

Client-seitige Anforderungen für nicht Cache-taugliche Daten und Interaktionen (z. B. Warenkorb-Interaktionen, Suchen) sollten direkt über das CDN bzw. den Dispatcher an den Commerce-Endpunkt (entweder Commerce-Lösung oder Integrationsschicht) gesendet werden. Entfernen Sie alle Aufrufe, bei denen AEM nur als Proxy fungierte.
