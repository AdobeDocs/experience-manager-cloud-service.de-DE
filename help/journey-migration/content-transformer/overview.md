---
title: Übersicht über Content Transformer
description: Erfahren Sie, wie Sie mit Content Transformer von BPA gemeldete inhaltsbezogene Probleme erkennen und beheben können.
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 4%

---

# Übersicht {#overview-ct}

Der Content Transformer (CT) ist ein von Adobe entwickeltes Tool, mit dem von der [Best Practices Analyzer (BPA)](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md) vor der Migration von Inhalten von Ihrer aktuellen AEM-Implementierung (On-Premise oder Managed Services) zu AEM as a Cloud Service.

Der Content Transformer kann Ihnen bei der Lösung von Problemen helfen, die unter Folgendes fallen: [BPA-Musterkategorien](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html?lang=de) (siehe Tabelle unten), indem Benutzer Massenaktionen wie Verschieben oder Löschen durchführen können. Dies kann die Zeit erheblich reduzieren und die mit einem Migrationsprojekt verbundene Komplexität reduzieren.

## Musterkategorien, die von Content Transformer und vorgeschlagenen Lösungen abgedeckt werden {#pattern-categories-and-benefits}

| Muster-Code | Suspensionstyp/Subtyp | Potenzielle Fehlerbehebung vor der Migration von Inhalten zu AEM as a Cloud Service |
|--------------|--------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| ACV | missing.jcrcontent <br> missing.original.rendition <br> metadata.downendants.Brexit | Verschieben Sie diese Assets an einen anderen Speicherort oder löschen Sie sie, um sicherzustellen, dass sie nicht zu AEM as a Cloud Service migriert werden. |
| CAV | content.area.violation | Verschieben Sie die Pfade vorübergehend zu `/etc/packages/content-transformation/paths` um sicherzustellen, dass sie nicht auf AEM as a Cloud Service migriert werden. |
| DOPI | deprecated.ordered.index | Entfernen Sie die veralteten Indizes. |
| OAUI | non.migrated.oauth.users | Entfernen Sie diese Benutzer, um sicherzustellen, dass sie nicht zu AEM as a Cloud Service migriert werden. |
| PCX | page.complex.medium <br> page.complex.high | Löschen Sie die Seiten/untergeordneten Elemente oder verschieben Sie sie an einen anderen Ort, um sicherzustellen, dass sie nicht zu AEM as a Cloud Service migriert werden. |
| REP | forward.replication <br> reverse.replication <br> standard.replication.agent.modification <br> custom.replication.agent.detection | Entfernen Sie die neu erstellten Replikationsagenten. <br> ODER <br> Entfernen Sie die geänderten/hinzugefügten Eigenschaften. |
| URS | clientlibs.location <br> file.location <br> node.location <br> workflow.location | Wechseln Sie zum richtigen Speicherort, um Probleme während der Migration zu vermeiden. |
| URS | node.size | Verschieben Sie die Knoten vorübergehend in`/etc/packages/content-transformation/paths` um sicherzustellen, dass sie nicht auf AEM as a Cloud Service migriert werden. |

## Vorteile des Content Transformer {#benefits}

Der Content Transformer bietet die folgenden Vorteile:

* Fail-safe: Ein Paket wird vom Content Transformer jedes Mal erstellt, wenn er Änderungen am Repository vornimmt, um Probleme zu beheben. Bei Bedarf können Sie den vorherigen Status wiederherstellen, indem Sie das Paket installieren.
* Benutzerfreundlich: Der Content Transformer wurde in das Content Transfer Tool integriert und verfügt über eine intuitive, einfache Benutzeroberfläche.
* Zeit sparen: Wenn Sie eine große Anzahl von Inhaltsproblemen haben, die unter eine Musterkategorie fallen, können Sie alle mit nur wenigen Klicks mit dem Content Transformer beheben.
