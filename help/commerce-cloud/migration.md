---
title: Migration zum Add-on für das AEM Commerce Integration Framework (CIF)
description: Migrieren zum Add-on für das AEM Commerce Integration Framework (CIF) von einer alten Version
exl-id: 0db03a05-f527-4853-b52f-f113bce929cf
feature: Commerce Integration Framework
role: Admin
index: false
source-git-commit: 173b70aa6f9ad848d0f80923407bf07540987071
workflow-type: ht
source-wordcount: '470'
ht-degree: 100%

---

# Leitfaden zur Migration für Experience Manager Cloud Service {#cif-migration}

Dieser Leitfaden hilft bei der Identifizierung von Bereichen, die für die Experience Manager Cloud Service-Migration aktualisiert werden müssen.

## CIF-Add-on

Für Experience Manager as a Cloud Service ist das CIF-Add-on die einzige unterstützte Commerce-Integrationslösung für Adobe Commerce und Commerce-Lösungen von Drittanbietern. Das CIF-Add-on wird für Kunden automatisch für Experience Manager as a Cloud Service bereitgestellt. Es ist keine manuelle Implementierung erforderlich. Siehe [Erste Schritte mit AEM Commerce as a Cloud Service](getting-started.md).

Um Projekte mit CIF-Bereitstellung zu unterstützen, stellt Adobe die [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) bereit.

Das CIF-Add-on ist auch für AEM 6.5 über das [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) verfügbar. Es ist kompatibel und bietet dieselben Funktionen wie das CIF-Add-on für Experience Manager as a Cloud Service. Es sind keine Anpassungen erforderlich.

Das klassische CIF mit seinen Abhängigkeiten ist nicht mehr verfügbar. Code, der sich auf diese CIF-Version mit `com.adobe.cq.commerce.api`-Java-APIs stützt, muss an das CIF-Add-on und dessen Prinzipien angepasst werden.

Der zuvor verfügbare CIF-Connector kann nicht mehr installiert werden. Code, der sich auf diesen Connector stützt, muss an das CIF-Add-on und dessen Prinzipien angepasst werden.

## Projektstruktur

Machen Sie sich mit der [AEM-Projektstruktur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=de) und der Funktionsweise von AEM as a Cloud Service vertraut. Passen Sie Ihr Projekt-Setup an das Layout von AEM as a Cloud Service an.
Im Vergleich zu AEM 6.5-Bereitstellungen gibt es hier zwei wesentliche Unterschiede:

* Das GraphQL-Client-OSGi-Bundle **darf nicht** mehr in das AEM-Projekt aufgenommen werden, sondern wird über das CIF-Add-on bereitgestellt.
* OSGi-Konfigurationen für den GraphQL-Client und GraphQL Data Service **dürfen nicht** mehr in das AEM-Projekt aufgenommen werden.

>[!TIP]
>
>Sehen Sie sich das Projekt [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) auf GitHub an. Dieses Projekt bietet Maven-Profile für AEM as a Cloud Service und für On-Premise-Bereitstellungen, die den unterschiedlichen Rahmenbedingungen Rechnung tragen.

## Produktkatalog

Das Importieren von Produktkatalogdaten wird nicht mehr unterstützt. Die Verwendung der CIF-Add-on-Prinzipale für Produkt- und Kataloganforderungen erfolgt über Echtzeit-Aufrufe an eine externe Commerce-Lösung. Wechseln Sie zum Kapitel über Integration, um mehr über die Integration von Commerce-Lösungen zu erfahren.

>[!TIP]
>
>Wenn keine Echtzeit-APIs verfügbar sind, sollte für die Integration ein externer Produkt-Cache mit APIs verwendet werden. Beispiel: [Magento Open Source](https://business.adobe.com/de/products/magento/open-source.html).

## Produktkatalog-Erlebnisse mit AEM-Rendering

Wenn Sie die Katalog-Blueprint mit dem klassischen CIF verwenden, müssen Sie den Workflow für den Produktkatalog aktualisieren. Das CIF-Add-on rendert Produktkatalog-Erlebnisse mithilfe von AEM-Katalogvorlagen nun direkt. Das Replizieren von Produktdaten oder Produktseiten ist nicht mehr erforderlich.

## Nicht Cache-taugliche Daten und Shopping-Interaktionen

Client-seitige Anforderungen für nicht Cache-taugliche Daten und Interaktionen (z. B. Warenkorb-Interaktionen, Suchen) sollten direkt über das CDN bzw. den Dispatcher an den Commerce-Endpunkt (entweder Commerce-Lösung oder Integrationsschicht) gesendet werden. Entfernen Sie alle Aufrufe, bei denen AEM nur als Proxy fungierte.
