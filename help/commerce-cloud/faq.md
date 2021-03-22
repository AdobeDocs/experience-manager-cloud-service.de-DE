---
title: AEM - Commerce-Integration unter Verwendung von Commerce Integration Framework - Häufig gestellte Fragen
description: AEM - Commerce-Integration unter Verwendung von Commerce Integration Framework - Häufig gestellte Fragen
translation-type: tm+mt
source-git-commit: ad831b2cc3657666678662eeff0eaf371ce4da49
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 68%

---


# AEM - Commerce-Integration unter Verwendung von Commerce Integration Framework - Häufig gestellte Fragen


## 1. Wird CIF GraphQL nur für den Handel verwendet oder ist dies für die Abfrage von Inhalten verfügbar, die mit AEM JCR erstellt wurden?

Adobe hat die GraphQL-APIs von Magento als offizielle Commerce-APIs für alle Commerce-bezogenen Daten übernommen. Daher verwendet AEM GraphQL zum Austausch von Commerce-Daten mit Magento und mit einer beliebigen Commerce-Engine über I/O Runtime. Diese GraphQL API ist unabhängig von AEM GraphQL API für den Zugriff auf Inhaltsfragmente.

## 2. Wie kommt Adobe I/O ins Spiel? Kommuniziert AEM direkt mit Magento?

AEM kann ohne I/O Runtime-Ebene direkt eine Verbindung zu Magento herstellen. Wenn ein Commerce-Backend, das nicht von Magento stammt (Drittanbieterlösung), mit AEM integriert werden muss, kann die Adobe I/O Runtime-Plattform verwendet werden, um die Zuordnungsschicht zu hosten und die Magento GraphQL-APIs mit beliebigen APIs von Drittanbieterlösungen zu verbinden. Weitere Informationen hierzu finden Sie in dieser [Referenzimplementierung](https://github.com/adobe/commerce-cif-graphql-integration-reference). Für Lösungen, die nicht von Magento stammen, wurde AEM mit einem Verweis auf den Adobe I/O Runtime-Endpunkt konfiguriert.

Die Adobe I/O Runtime-Plattform kann auch zum Erweitern oder Anpassen von Commerce-Services verwendet werden. Für diese Anwendungsfälle rufen Sie den Adobe I/O Runtime-Endpunkt auf, der dann eine anwenderdefinierte Implementierung des entsprechenden Service hostet. Integration- und Erweiterungsanwendungsfälle können kombiniert werden.

## 3. Können Produkt-Assets (Bilder) von AEM über die Magento-Administration gespeichert und referenziert werden? Wie können Assets aus Dynamic Media genutzt werden?

Derzeit ist eine Integration von AEM Assets mit Magento nicht möglich. Als Problemumgehung können Sie Produkt-Assets (Bilder) in AEM Assets speichern. Sie müssen die Asset-URLs jedoch manuell in Magento speichern. Dynamic Media ist jetzt Teil von AEM Assets. Die Funktionalität der Lösung bleibt unverändert bestehen.

## 4. Ist es wichtig, wo die Commerce-Lösung bereitgestellt wird? (Lokal oder in der Cloud)

Es spielt keine Rolle, wo Ihre Commerce-Lösung bereitgestellt wird. Die Integration und die neue Venia-Storefront von AEM funktionieren unabhängig vom Implementierungsmodell. Wenn die Implementierung jedoch auf Basis der genehmigten E2E-Referenzarchitektur erfolgt, werden E2E-Tests mit erfassten Leistungs-KPIs durchgeführt, die das Profil eines Unternehmenskunden repräsentieren. Dadurch erhalten Sie zusätzliche Informationen, die Sie als Benchmark verwenden können.

## 5. Wie werden in AEM Katalogseiten oder Produktseiten erstellt? Wie können sie in AEM beibehalten werden?

Katalogseiten und Produktseiten werden in AEM dynamisch basierend auf generischen Katalog- und Produktseitenvorlagen erstellt und zwischengespeichert. In AEM werden keine Produkt- oder Katalogdaten importiert und gespeichert.

## 6. Wenn Sie Produktdaten in Ihrer Commerce-Lösung aktualisieren, ist das ein Echtzeit-AEM? Oder erfolgt dies per Batch-Prozess?

Das mit AEM Cloud Service verwendete CIF-Add-on ermöglicht den Datenfluss von der Commerce-Lösung zu AEM On-Demand. Daher handelt es sich bei diesem Vorgang nicht um einen Push- oder Batch-Vorgang in Echtzeit, wenn Ihre Commerce-Lösung aktualisiert wird.

## 7. Welche Kataloggröße AEM mit CIF-Unterstützung?

Dies hängt von einigen zusätzlichen Aspekten ab, die Sie berücksichtigen müssen. Wie hoch ist das Cache-Verhältnis Ihrer Katalogdaten und Seiten? Wie viele gleichzeitige Anforderungen erwarten Sie während der Stoßzeiten? Wie skalierbar sind die APIs Ihrer Commerce-Lösungen?

## 8. Welche Rolle spielt PIM bei diesem Framework?

PIM-Daten werden über GraphQL-Anfragen für AEM und Clients bereitgestellt. Unsere Empfehlung ist, PIM in die Commerce-Engine (Magento oder andere) zu integrieren, damit PIM-Daten dann von der Commerce-Engine abgerufen werden können.

## 9. Werden über AEM Dispatcher auch Preise und andere Daten zwischengespeichert? Führt dies zu Problemen im Zusammenhang mit häufig durchgeführten Cache-Invalidierungen?

Dynamische Daten wie Preis- oder Bestandsdaten werden in AEM Dispatcher nicht zwischengespeichert. Dynamische Daten werden Client-seitig mit Web-Komponenten direkt über GraphQL-APIs abgerufen. Nur statische Daten (wie Produkt- oder Kategoriedaten) werden im Dispatcher zwischengespeichert. Wenn sich die Produktdaten ändern, muss der Cache invalidiert werden.

## 10. Wie funktioniert die Cache-Ungültigmachung für AEM Dispatcher mit AEM und Commerce?

Es wird empfohlen, eine TTL-basierte Cache-Invalidierung für Seiten einzurichten, die in AEM Dispatcher zwischengespeichert werden. Für dynamische Informationen wie Preis- oder Bestandsdaten empfiehlt es sich, das Datum Client-seitig zu rendern. Weitere Informationen zur TTL-basierten Cache-Invalidierung finden Sie unter [AEM Dispatcher](https://helpx.adobe.com/de/experience-manager/kb/optimizing-the-dispatcher-cache.html).

## 11. Gibt es Empfehlungen zur einheitlichen Suche in AEM-Inhalten mit Commerce?

Es wird eine Referenzimplementierung für die Produktsuche bereitgestellt, jedoch keine einheitliche Suche in Inhalten. Diese Funktion ist in der Regel sehr kundenspezifisch und lässt sich besser auf projektspezifischer Ebene bereitstellen.

## 12. Wie funktioniert die Suche mit AEM und dem Handel mit CIF?

Das CIF stellt die Komponenten „Suchleiste“ und „Suchergebnis“ bereit. Die Suchleistenkomponente sendet eine GraphQL-Anforderung mit dem Suchbegriff an die Commerce-Lösung, die dann eine Liste mit Produktname, Preis, SLUG usw. zurückgibt. Die Komponente „Suchergebnis“ zeigt dann die Suchergebnisse in einer Galerie-Ansicht auf einer Suchergebnisseite an, die in AEM erstellt wurde. Die Suche unterstützt einfache Volltextsuchen. Wir verwenden den Slug-/URL-Schlüssel, um einen Verweis auf die Produktdetailseite zu erstellen.

## 13. Wie können Produktdaten in MSM oder Übersetzungen verwendet werden?

Produktdaten werden in der Regel bereits im PIM-System oder in Magento übersetzt. Die Integration von AEM und Magento unterstützt die Verbindung zu mehreren Magento-Stores und Store-Ansichten. Bei einem MSM-Setup ist normalerweise eine AEM-Site mit einer Magento-Store-Ansicht verknüpft.

## 14. Wie funktioniert CIF mit Nicht-Magento-Commerce-Plattformen?

Die Integration mit Lösungen von Drittanbietern, beispielsweise anderen Commerce-Lösungen (nicht Magento), erfolgt über die Adobe I/O Runtime-Plattform.  Zur Veranschaulichung dieses Vorgehens haben wir eine [Referenzimplementierung](https://github.com/adobe/commerce-cif-graphql-integration-reference) erstellt. Dies ermöglicht die Wiederverwendung des [AEM CIF Cloud Connector](https://github.com/adobe/commerce-cif-connector) und der [AEM-CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components), indem die Magento GraphQL-API auf jeglichen Commerce-Plattformen von Drittanbietern verfügbar gemacht wird. Um maximale Flexibilität und Skalierbarkeit zu bieten, wird diese Integrationsschicht auf der Server-losen [Adobe I/O Runtime-Plattform](https://www.adobe.io/apis/experienceplatform/runtime.html) bereitgestellt.

## 15. Gibt es eine Möglichkeit, die Produktdaten durch Commerce-spezifischen Text zu optimieren? Wo kann dies geschehen? In AEM oder in der Commerce-Lösung?

Wir empfehlen, Marketing-bezogene Daten und Inhalte in AEM zu verwalten. Dekorieren Sie Produktdaten aus Ihrer Commerce-Lösung mit zusätzlichen Attributen mithilfe von Inhaltsfragmenten oder erstellen und verknüpfen Sie Erlebnisfragmente für nicht strukturierte Inhalte mit Ihren Produkten.

## 16. Ändert sich die Integration zwischen AEM und Magento, wenn die Adobe I/O Runtime-Plattform verwendet wird?

Kunden, die Commerce-Services erweitern möchten, können dieselben Abfolgen von Integrations- und Schreibaktionen verwenden, die auf der Adobe I/O Runtime-Plattform gehostet werden, um eine Geschäftslogik einzufügen und die Commerce-Services zu erweitern.

## 17. Lässt sich eine SPA-Storefront mit dem SPA-Editor von AEM verwenden?

AEM kann als Authoring-Tool für jede Art von Storefront verwendet werden. Derzeit wird serverseitiges und clientseitiges Rendering (Hybrid) im AEM Store verwendet. Die PWA-Unterstützung für das kostenlose und kostenlose Authoring von Inhalten wird im Laufe des Jahres 2021 veröffentlicht.


## 18. Wie lässt sich PCI-Compliance sicherstellen, wenn AEM für die gesamte Präsentationschicht verwendet wird?

Es wird empfohlen, abstrakte Zahlungsmethoden zu verwenden. Dadurch wird der Browser-Client direkt mit dem Payment Gateway Provider kommuniziert, sodass weder die Adobe noch die Commerce-Lösungen Karteninhaberdaten speichern oder weitergeben. Dieser Ansatz erfordert nur die PCI-Kompatibilität der Stufe 3. Es gibt jedoch noch weitere Aspekte, die Sie im Hinblick auf umfassende PCI-Compliance berücksichtigen sollten, beispielsweise die Art und Weise, wie Mitarbeiter mit dem System und den Daten interagieren. Weitere Informationen zur PCI-Compliance von Magento finden Sie unter https://magento.com/pci-compliance.

## 19. Wenn ich AEM und Magento Cloud-Versionen verwende, ist diese gemeinsame Lösung PCI-konform?

Ja, Selbstbewertungsfragebogen D und Konformitätsbescheinigung sind auf Anfrage erhältlich.


## 20. Wie kann ich eine Adobe I/O Runtime-Testlizenz anfordern?

Sie können [hier](https://adobeio.typeform.com/to/obqgRm) eine Testlizenz für die Nutzung von Adobe I/O Runtime anfordern.
