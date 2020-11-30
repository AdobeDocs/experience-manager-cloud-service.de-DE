---
title: Häufig gestellte Fragen zur Integration von AEM mit Magento mithilfe des Commerce Integration Framework
description: Häufig gestellte Fragen zur Integration von AEM mit Magento mithilfe des Commerce Integration Framework
translation-type: tm+mt
source-git-commit: cafe8825fe34f158c74b94b95b7252394de26e4d
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 100%

---


# Häufig gestellte Fragen zur Integration von AEM mit Magento mithilfe des Commerce Integration Framework


## 1. Wird GraphQL nur für Magento verwendet oder kann die Sprache auch für die Abfrage von Inhalten verwendet werden, die im JCR von AEM erstellt wurden?

Adobe hat die GraphQL-APIs von Magento als offizielle Commerce-APIs für alle Commerce-bezogenen Daten übernommen. Daher verwendet AEM GraphQL zum Austausch von Commerce-Daten mit Magento und mit einer beliebigen Commerce-Engine über I/O Runtime.

## 2. Wie kommt Adobe I/O ins Spiel? Kommuniziert AEM direkt mit Magento?

AEM kann ohne I/O Runtime-Ebene direkt eine Verbindung zu Magento herstellen. Wenn ein Commerce-Backend, das nicht von Magento stammt (Drittanbieterlösung), mit AEM integriert werden muss, kann die Adobe I/O Runtime-Plattform verwendet werden, um die Zuordnungsschicht zu hosten und die Magento GraphQL-APIs mit beliebigen APIs von Drittanbieterlösungen zu verbinden. Weitere Informationen hierzu finden Sie in dieser [Referenzimplementierung](https://github.com/adobe/commerce-cif-graphql-integration-reference). Für Lösungen, die nicht von Magento stammen, wurde AEM mit einem Verweis auf den Adobe I/O Runtime-Endpunkt konfiguriert.

Die Adobe I/O Runtime-Plattform kann auch zum Erweitern oder Anpassen von Commerce-Services verwendet werden. Für diese Anwendungsfälle rufen Sie den Adobe I/O Runtime-Endpunkt auf, der dann eine anwenderdefinierte Implementierung des entsprechenden Service hostet. Integration- und Erweiterungsanwendungsfälle können kombiniert werden.

## 3. Können Produkt-Assets (Bilder) von AEM über die Magento-Administration gespeichert und referenziert werden? Wie können Assets aus Dynamic Media genutzt werden?

Derzeit ist eine Integration von AEM Assets mit Magento nicht möglich. Als Problemumgehung können Sie Produkt-Assets (Bilder) in AEM Assets speichern. Sie müssen die Asset-URLs jedoch manuell in Magento speichern. Dynamic Media ist jetzt Teil von AEM Assets. Die Funktionalität der Lösung bleibt unverändert bestehen.

## 4. Ist es wichtig, wo Magento bereitgestellt wird? (Lokal oder in der Cloud)

Es spielt keine Rolle, wo Magento bereitgestellt wird. Die Integration und die neue Venia-Storefront von AEM funktionieren unabhängig vom Implementierungsmodell. Wenn die Implementierung jedoch auf Basis der genehmigten E2E-Referenzarchitektur erfolgt, werden E2E-Tests mit erfassten Leistungs-KPIs durchgeführt, die das Profil eines Unternehmenskunden repräsentieren. Dadurch erhalten Sie zusätzliche Informationen, die Sie als Benchmark verwenden können.

## 5. Wie werden in AEM Katalogseiten oder Produktseiten erstellt? Wie können sie in AEM beibehalten werden?

Katalogseiten und Produktseiten werden in AEM dynamisch basierend auf generischen Katalog- und Produktseitenvorlagen erstellt und zwischengespeichert. In AEM werden keine Produkt- oder Katalogdaten importiert und gespeichert.

## 6. Werden über AEM Dispatcher auch Preise und andere Daten zwischengespeichert? Führt dies zu Problemen im Zusammenhang mit häufig durchgeführten Cache-Invalidierungen?

Dynamische Daten wie Preis- oder Bestandsdaten werden in AEM Dispatcher nicht zwischengespeichert. Dynamische Daten werden Client-seitig mit Web-Komponenten direkt über GraphQL-APIs abgerufen. Nur statische Daten (wie Produkt- oder Kategoriedaten) werden im Dispatcher zwischengespeichert. Wenn sich die Produktdaten ändern, muss der Cache invalidiert werden.

## 7. Wie funktioniert die Cache-Invalidierung für AEM Dispatcher mit AEM Magento?

Es wird empfohlen, eine TTL-basierte Cache-Invalidierung für Seiten einzurichten, die in AEM Dispatcher zwischengespeichert werden. Für dynamische Informationen wie Preis- oder Bestandsdaten empfiehlt es sich, das Datum Client-seitig zu rendern. Weitere Informationen zur TTL-basierten Cache-Invalidierung finden Sie unter [AEM Dispatcher](https://helpx.adobe.com/de/experience-manager/kb/optimizing-the-dispatcher-cache.html).

## 8. Warum kommt We.Retail nicht zum Einsatz?

Es wird das von Magento entwickelte Venia-Design verwendet, bei dem die mobile Nutzung an erster Stelle steht („Mobile first“) und welches auf Magento Progressive Web Applications (PWA) abgestimmt ist. Das Venia-Design ist in puncto CSS-Stile und AEM-Kernkomponenten auf dem neuesten Stand der Technik.

## 9. Wenn Produktdaten in Magento aktualisiert werden, wird die Aktualisierung dann in Echtzeit an AEM gepusht? Oder erfolgt dies per Batch-Prozess?

Das CIF-Add-on, das mit AEM Cloud Service verwendet wird, ermöglicht den Datenfluss von Magento zum On-Demand-Service von AEM. Daher handelt es sich bei diesem Vorgang nicht um einen Push-Vorgang in Echtzeit oder einen Batch-Prozess, wenn eine Aktualisierung in Magento erfolgt.

## 10. Gibt es Empfehlungen zur einheitlichen Suche in AEM-Inhalten mit Commerce?

Es wird eine Referenzimplementierung für die Produktsuche bereitgestellt, jedoch keine einheitliche Suche in Inhalten. Diese Funktion ist in der Regel sehr kundenspezifisch und lässt sich besser auf projektspezifischer Ebene bereitstellen.

## 11. Wie funktioniert die Suche mit Integrationen von AEM mit Magento mithilfe des CIF?

Das CIF stellt die Komponenten „Suchleiste“ und „Suchergebnis“ bereit. Die Komponente „Suchleiste“ sendet eine GraphQL-Anfrage mit dem jeweiligen Suchbegriff an Magento. Magento gibt dann eine Produktliste zurück, die Produktname, Preis, Slug usw. umfasst. Die Komponente „Suchergebnis“ zeigt dann die Suchergebnisse in einer Galerie-Ansicht auf einer Suchergebnisseite an, die in AEM erstellt wurde. Die Suche unterstützt einfache Volltextsuchen. Wir verwenden den Slug-/URL-Schlüssel, um einen Verweis auf die Produktdetailseite zu erstellen.

## 11. Wie können Produktdaten in MSM oder Übersetzungen verwendet werden?

Produktdaten werden in der Regel bereits im PIM-System oder in Magento übersetzt. Die Integration von AEM und Magento unterstützt die Verbindung zu mehreren Magento-Stores und Store-Ansichten. Bei einem MSM-Setup ist normalerweise eine AEM-Site mit einer Magento-Store-Ansicht verknüpft.

## 13. Wie lässt sich das CIF mit anderen Commerce-Plattformen verwenden?

Die Integration mit Lösungen von Drittanbietern, beispielsweise anderen Commerce-Lösungen (nicht Magento), erfolgt über die Adobe I/O Runtime-Plattform.  Zur Veranschaulichung dieses Vorgehens haben wir eine [Referenzimplementierung](https://github.com/adobe/commerce-cif-graphql-integration-reference) erstellt. Dies ermöglicht die Wiederverwendung des [AEM CIF Cloud Connector](https://github.com/adobe/commerce-cif-connector) und der [AEM-CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components), indem die Magento GraphQL-API auf jeglichen Commerce-Plattformen von Drittanbietern verfügbar gemacht wird. Um maximale Flexibilität und Skalierbarkeit zu bieten, wird diese Integrationsschicht auf der Server-losen [Adobe I/O Runtime-Plattform](https://www.adobe.io/apis/experienceplatform/runtime.html) bereitgestellt.

## 14. Gibt es eine Möglichkeit, die Produktdaten durch Commerce-spezifischen Text zu optimieren? Wo kann dies geschehen? In AEM oder im Magento?

Es gibt mehrere Möglichkeiten, die vom jeweiligen Anwendungsfall abhängig sind. Eine Möglichkeit wäre, mit anwenderdefinierten Attributen zu arbeiten. Ermöglichen Sie es AEM-Autoren, diese Felder im Produkteditor von AEM zu verändern und die Daten wieder mit dem PIM-System zu synchronisieren. Eine weitere Option wäre die Nutzung von AEM Experience Fragments, die in die Produktseiten eingefügt werden.

## 15. Ändert sich die Integration zwischen AEM und Magento, wenn die Adobe I/O Runtime-Plattform verwendet wird?

Kunden, die Commerce-Services erweitern möchten, können dieselben Abfolgen von Integrations- und Schreibaktionen verwenden, die auf der Adobe I/O Runtime-Plattform gehostet werden, um eine Geschäftslogik einzufügen und die Commerce-Services zu erweitern.

## 16. AEM erstellt Produkt- und Katalogseiten dynamisch auf der Grundlage einer generischen Vorlage in AEM. Was würde ich also sehen, wenn ich CRXDE Lite öffne und unter „Content“ nachsehe? Würde ich eine ganze Produktstruktur sehen, die auf den Produkten im Magento basiert? Falls nicht, wie würde ein Autor diese Seiten optimieren?

Es gibt keinen JCR-Katalog und keine Produktseiten mehr. Siehe Frage 12.

## 17. Lässt sich eine SPA-Storefront mit dem SPA-Editor von AEM verwenden?

AEM kann als Authoring-Tool für jede Art von Storefront verwendet werden. Derzeit wird Hybrid-Rendering für die neue Storefront verwendet. Künftig wird AEM zum Authoring mit SPAs und PWAs verwendet.

## 18. Welche Rolle spielt PIM bei diesem Framework?

PIM-Daten werden über GraphQL-Anfragen für AEM und Clients bereitgestellt. Wir empfehlen, PIM in die Commerce-Engine (von Magento oder anderen Anbietern) zu integrieren, sodass die PIM-Daten dann von der Commerce-Engine abgerufen werden können.

## 19. Wie lässt sich PCI-Compliance sicherstellen, wenn AEM für die gesamte Präsentationschicht verwendet wird?

Bei Verwendung von AEM in AMS- und Magento-Cloud-Implementierungen ist die Verwendung abstrahierter Zahlungsmethoden obligatorisch. Dadurch kommuniziert der Browser-Client direkt mit dem Payment Gateway Provider, sodass weder Adobe noch Magento-Clouds Daten von Karteninhabern speichern oder weitergeben. Dieser Ansatz ermöglicht PCI-Compliance für Technologie-Stacks und Rechenzentren. Es gibt jedoch noch weitere Aspekte, die Sie im Hinblick auf umfassende PCI-Compliance berücksichtigen sollten, beispielsweise die Art und Weise, wie Mitarbeiter mit dem System und den Daten interagieren. Weitere Informationen zur PCI-Compliance von Magento finden Sie unter https://magento.com/pci-compliance.

## 20. Wie kann ich eine Adobe I/O Runtime-Testlizenz anfordern?

Sie können [hier](https://github.com/AdobeDocs/adobeio-runtime/blob/master/overview/request_a_trial.md) eine Testlizenz für die Nutzung von Adobe I/O Runtime anfordern.



