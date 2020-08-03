---
title: AEM - Integration von Magentos mit Commerce Integration Framework - Häufig gestellte Fragen
description: AEM - Integration von Magentos mit Commerce Integration Framework - Häufig gestellte Fragen
translation-type: tm+mt
source-git-commit: cafe8825fe34f158c74b94b95b7252394de26e4d
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 0%

---


# AEM - Integration von Magentos mit Commerce Integration Framework - Häufig gestellte Fragen


## 1. Wird GraphQL nur zum Magento verwendet oder ist dies für die Abfrage von Inhalten verfügbar, die mit AEM JCR erstellt wurden?

Adobe hat die GraphQL APIs von Magento als offizielle Commerce-API für alle handelsbezogenen Daten übernommen. Daher verwendet AEM GraphQL zum Austausch von Commerce-Daten mit Magento und mit jeder Commerce-Engine über I/O Runtime.

## 2. Wie kommt die Adobe I/O ins Spiel? Spricht AEM direkt mit Magento?

AEM können direkt eine Verbindung zu Magento ohne I/O-Laufzeitebene herstellen. Wenn ein Commerce-Back-End (Drittanbieter-Lösung) nicht mit AEM integriert werden muss, kann die I/O-Laufzeitplattform verwendet werden, um die Zuordnungsebene zu hosten und die Magento-GraphQL-APIs mit beliebigen Lösungen-APIs von Drittanbietern zu verbinden. Weitere Informationen hierzu finden Sie in dieser [Referenzimplementierung](https://github.com/adobe/commerce-cif-graphql-integration-reference). Bei Nicht-Magento-Lösungen wurde AEM so konfiguriert, dass sie auf den E/A-Laufzeitendpunkt zeigen.

Die I/O-Laufzeitplattform kann auch zum Erweitern oder Anpassen von Commerce-Diensten verwendet werden. Für diese Anwendungsfälle rufen Sie den E/A-Laufzeitendpunkt auf, der dann eine benutzerdefinierte Implementierung des entsprechenden Dienstes hostet. Anwendungsfälle für Integration und Erweiterung können kombiniert werden.

## 3. Können Produkt-Assets (Images) von AEM über den Magento-Administrator gespeichert und referenziert werden? Wie können Assets aus Dynamic Media genutzt werden?

Es gibt derzeit keine AEM Assets - Magento-Integration. Um dies zu umgehen, können Sie Produkt-Assets (Bilder) in AEM Assets speichern. Sie müssen die Asset-URLs jedoch manuell in Magento speichern. Dynamic Media gehören jetzt zu den AEM Assets und werden genauso funktionieren.

## 4. Ist es wichtig, wo Magento eingesetzt wird? (In der Vorschau oder in der Cloud)

Es spielt keine Rolle, wo Magento bereitgestellt wird. Die Integration und die neue AEM Venia Store Front funktioniert unabhängig vom Bereitstellungsmodell. Wenn sie jedoch auf der Grundlage der genehmigten E2E-Referenzarchitektur bereitgestellt wird, werden E2E-Tests mit Performance-KPIs durchgeführt, die gesammelt wurden und das Profil eines Unternehmenskunden repräsentieren. Dadurch erhalten Sie zusätzliche Informationen, die Sie als Benchmark verwenden können.

## 5. Wie werden Katalogseiten oder Produktseiten in AEM erstellt? Wie bleiben sie in AEM bestehen?

Katalogseiten und Produktseiten werden dynamisch in AEM basierend auf generischen Katalog- und Produktseitenvorlagen erstellt und zwischengespeichert. Es werden keine Produkt- oder Katalogdaten in AEM importiert und gespeichert.

## 6. Zwischenspeichern Sie auch Preise und andere Daten über Dispatcher. Führt dies zu einer häufigen Cache-Invalidierung?

Dynamische Daten wie Preis oder Bestand werden nicht auf dem Dispatcher zwischengespeichert. Dynamische Daten werden clientseitig mit Webkomponenten direkt über GraphQL APIs abgerufen. Nur statische Daten (wie Produkt- oder Kategorie-Daten) werden auf dem Dispatcher zwischengespeichert. Wenn sich die Produktdaten ändern, muss der Cache ungültig gemacht werden.

## 7. Wie funktioniert die Cache-Ungültigmachung für AEM Dispatcher mit AEM-Magento?

Es wird empfohlen, eine TTL-basierte Cache-Ungültigmachung für auf dem Dispatcher zwischengespeicherte Seiten einzurichten. Für dynamische Informationen wie Preis oder Bestand wird empfohlen, das Datum clientseitig zu rendern. Weitere Informationen zur TTL-basierten Cache-Ungültigmachung finden Sie im [AEM Dispatcher](https://helpx.adobe.com/experience-manager/kb/optimizing-the-dispatcher-cache.html)

## 8. Warum verwenden Sie We.Retail nicht?

Das Venia-Thema (entwickelt von Magento) wird verwendet, das zuerst mobil ist und an der PWA des Magentos ausgerichtet ist. Das Thema Venia stellt die neuesten CSS-Stile und AEM Kernkomponenten dar.

## 9. Wenn Sie Produktdaten in Magento aktualisieren, ist das ein Echtzeit-AEM? Oder handelt es sich um einen Stapelprozess?

Das CIF-Add-on, das mit AEM Cloud Service verwendet wird, ermöglicht den Datenfluss von Magento zu AEM On-Demand. Daher handelt es sich bei diesem Vorgang nicht um einen Push- oder Batch-Vorgang in Echtzeit, wenn ein Magento aktualisiert wird.

## 10. Gibt es Empfehlungen zur einheitlichen Suche in AEM Inhalten mit Commerce?

Es wird eine Referenzimplementierung für die Produktsuche bereitgestellt, jedoch keine einheitliche Suche mit Inhalten. Diese Funktion ist in der Regel sehr kundenspezifisch und auf projektspezifischer Ebene besser zu lösen.

## 11. Wie funktioniert Search mit AEM-Magento mit CIF?

CIF stellt die Komponenten Suchleiste und Suchergebnis bereit. Die Suchleistenkomponente sendet eine GraphQL-Anforderung mit dem Suchbegriff an Magento. Magento gibt dann eine Produkt-Liste zurück, die Produktname, Preis, SLUG usw. enthält. Die Suchergebniskomponente zeigt dann die Suchergebnisse in einer Galerie-Ansicht auf einer Suchergebnisseite an, die in AEM erstellt wurde. Die Suche unterstützt die einfache Volltextsuche. Wir verwenden den SLUG/url-Schlüssel, um einen Verweis auf den PDP zu erstellen.

## 11. Wie können Produktdaten in MSM oder Übersetzungen verwendet werden?

Produktdaten werden in der Regel bereits in PIM oder in Magento übersetzt. Die AEM - Magento-Integration unterstützt die Verbindung zu mehreren Magento Stores &amp; Store-Ansichten. Bei einem MSM-Setup ist normalerweise eine AEM mit einer Magento Store-Ansicht verknüpft.

## 13. Wie funktioniert CIF mit anderen Commerce-Plattformen?

Die Integration mit Lösungen von Drittanbietern wie anderen Commerce-Lösungen (nicht Magento) erfolgt über die I/O Runtime-Plattform.  Wir haben eine [Referenzimplementierung](https://github.com/adobe/commerce-cif-graphql-integration-reference) erstellt, um zu zeigen, wie dies geschieht. Dies ermöglicht die Wiederverwendung des [AEM CIF Cloud Connector](https://github.com/adobe/commerce-cif-connector) und der [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) , indem die Magento GraphQL-API auf jeder kommerziellen Plattform eines Drittanbieters verfügbar gemacht wird. Um maximale Flexibilität und Skalierbarkeit Angebot, wird diese Integrationsebene auf der serverllosen [Adobe I/O Runtime-Plattform](https://www.adobe.io/apis/experienceplatform/runtime.html)bereitgestellt.

## 14. Gibt es eine Möglichkeit, die Produktdaten durch kommerziellen Text zu verbessern? Wo machst du das? In AEM oder im Magento?

Es gibt mehrere Möglichkeiten, dies zu erreichen, und es hängt vom Anwendungsfall ab. Eine Möglichkeit wäre, mit benutzerdefinierten Attributen zu arbeiten. Erlauben Sie AEM Autoren, diese Felder im Produkt-Editor AEM auszublenden und die Daten wieder mit dem PIM zu synchronisieren. Eine andere Option wäre die Nutzung AEM Erlebnisfragmente, die in die Produktseiten eingefügt werden.

## 15. Ändert sich die Integration zwischen AEM und Magento, wenn die Adobe I/O Runtime-Plattform verwendet wird?

Kunden, die Commerce-Dienste erweitern möchten, können dieselben Integrations- und Schreibaktionen-Sequenzen verwenden, die auf der I/O Runtime-Plattform gehostet werden, um eine Geschäftslogik einzuführen und die Commerce-Dienste zu bereichern.

## 16. Da AEM Produkt- und Katalogseiten dynamisch auf der Grundlage einer generischen Vorlage in AEM erstellt, was würde ich dann sehen, wenn ich die CRXDE Lite öffnen und unter Inhalt überprüfen würde? Würde ich eine ganze Produktstruktur sehen, die auf den Produkten im Magento basiert? Wenn nicht, wie würde ein Autor diese Seiten verbessern?

Es gibt keine JCR-Katalog- oder Produktseiten mehr. Siehe Frage 12.

## 17. Funktioniert der SPA Store Frontend mit AEM SPA-Editor?

AEM kann als Authoring-Tool für jede Art von Schaufenster verwendet werden. Derzeit wird Hybrid-Rendering für die neue Schaufenster verwendet. Künftig werden AEM für das Authoring mit SPA und PWA verwendet.

## 18. Wie spielt PIM in diesem Rahmen eine Rolle?

PIM-Daten werden über GraphQL-Anforderungen an AEM und Clients offen gelegt. Unsere Empfehlung ist, PIM in die Commerce-Engine (Magento oder andere) zu integrieren, damit PIM-Daten dann von der Commerce-Engine abgerufen werden können.

## 19. Wie können wir die PCI-Kompatibilität sicherstellen, wenn AEM für die gesamte Präsentationsschicht verwendet werden?

Bei Verwendung von AEM für die Bereitstellung von AMS und Magento Cloud ist die Verwendung abstrakter Zahlungsmethoden obligatorisch. Dadurch kommuniziert der Browser-Client direkt mit dem Payment Gateway Provider, sodass weder Adobe- noch Magento-Clouds Karteninhaberdaten speichern oder weitergeben. Dieser Ansatz bietet PCI-Compliance für die Technologiestapel und Rechenzentren. Es gibt jedoch noch weitere Dinge, die als vollständig PCI-konform betrachtet werden sollten, wie z.B. die Interaktion der Mitarbeiter mit dem System und den Daten. Weitere Informationen zur PCI-Kompatibilität mit Magento finden Sie unter https://magento.com/pci-compliance

## 20. Wie kann ich eine I/O Runtime-Testlizenz anfordern?

Sie können [hier](https://github.com/AdobeDocs/adobeio-runtime/blob/master/overview/request_a_trial.md)eine Testlizenz anfordern, um die I/O-Laufzeitumgebung zu verwenden.



