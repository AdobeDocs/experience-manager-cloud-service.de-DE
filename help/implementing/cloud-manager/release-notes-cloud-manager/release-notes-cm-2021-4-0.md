---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.4.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.4.0
feature: Release Information
exl-id: a11ebe0e-2872-4fde-acc0-5babc6b01e1a
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 100%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.4.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.4.0.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für Cloud Manager in AEM as a Cloud Service 2021.4.0 war der 08. April 2021.
Die folgende Version wurde am 06. Mai 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-april}

* Die Benutzeroberfläche der Workflows „Programm hinzufügen“ und „Programm bearbeiten“ wurde aktualisiert, um sie intuitiver zu gestalten.

* Ein Benutzer mit den erforderlichen Berechtigungen kann jetzt den Commerce-Endpunkt über die Benutzeroberfläche übermitteln.

* Umgebungsvariablen können jetzt auf einen bestimmten Service übertragen werden, entweder in der Autoren- oder der Veröffentlichungsinstanz. Erfordert AEM Version `2021.03.5104.20210328T185548Z` oder später.

* Die Schaltfläche **Git verwalten** wird auch dann auf der Karte „Pipelines“ angezeigt, wenn keine Pipelines konfiguriert wurden.

* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 27 aktualisiert.

* Projekte in der Adobe I/O-Entwickerkonsole, die von Cloud Manager erstellt wurden, können nicht mehr unbeabsichtigt bearbeitet oder gelöscht werden.

* Wenn ein Benutzer eine neue Umgebung hinzufügt, wird er darüber informiert, dass eine Umgebung nach ihrer Erstellung nicht mehr in eine andere Region verschoben werden kann.

* Umgebungsvariablen können jetzt auf einen bestimmten Service übertragen werden, entweder in der Autoren- oder der Veröffentlichungsinstanz. Erfordert AEM Version 2021.03.5104.20210328T185548Z oder später.

* Die Fehlermeldung beim Starten einer Pipeline nach dem Löschen einer Umgebung wurde präzisiert.

* Von Eclipse-Projekten bereitgestellte OSGi-Bundles sind jetzt von der Regel `CQBP-84--dependencies` ausgeschlossen.

### Fehlerbehebungen {#bug-fixes-cm-april}

* Beim Bearbeiten der Seite „Erlebnisprüfung“ einer Pipeline führt ein Eingabepfad, der mit einem Schrägstrich `( / )` beginnt, nicht mehr dazu, dass der Schritt im Status „Ausstehend“ feststeckt.

* Wenn beim Erstellen einer neuen Produktions-Pipeline vom Benutzer keine Überschreibung bei der Inhaltsprüfung hinzugefügt wird, findet jetzt trotzdem eine Überprüfung der standardmäßigen Homepage statt.

* Bei Problemen des Typs `CloudServiceIncompatibleWorkflowProcess` wird jetzt der richtige Schweregrad in der herunterladbaren CSV-Datei des Problems angegeben.

* Die `Runmode`-Prüfung erzeugt jetzt keine Fehlalarme mehr auf Nicht-Ordner-Knoten.
