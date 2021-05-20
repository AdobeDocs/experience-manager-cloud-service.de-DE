---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.4.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.4.0
feature: Versionshinweise
source-git-commit: e2d4bb7649fad3ee172c6f049ecfdedc71417ee2
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 18%

---


# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.4.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.4.0.

## Veröffentlichungsdatum {#release-date}

Die Version 2021.4.0 von Cloud Manager in AEM as a Cloud Service wurde am 8. April 2021 veröffentlicht.
Die nächste Version ist für den 6. Mai 2021 geplant.

### Neue Funktionen {#what-is-new-april}

* Die Benutzeroberfläche aktualisiert die Workflows Programm hinzufügen und bearbeiten , um sie intuitiver zu gestalten.

* Ein Benutzer mit den erforderlichen Berechtigungen kann jetzt den Commerce-Endpunkt über die Benutzeroberfläche senden.

* Umgebungsvariablen können jetzt auf einen bestimmten Dienst übertragen werden, entweder auf Autoren- oder auf Veröffentlichungsinstanz. Erfordert AEM Version `2021.03.5104.20210328T185548Z` oder höher.

* Die Schaltfläche **Git** verwalten wird auch dann auf der Pipelines-Karte angezeigt, wenn keine Pipelines konfiguriert wurden.

* Die Version des von Cloud Manager verwendeten AEM Projektarchetyps wurde auf Version 27 aktualisiert.

* Projekte, die in der Adobe I/O Developer Console von Cloud Manager erstellt wurden, können nicht mehr unbeabsichtigt bearbeitet oder gelöscht werden.

* Wenn ein Benutzer eine neue Umgebung hinzufügt, wird er darüber informiert, dass eine Umgebung nach ihrer Erstellung nicht mehr in eine andere Region verschoben werden kann.

* Umgebungsvariablen können jetzt auf einen bestimmten Dienst übertragen werden, entweder auf Autoren- oder auf Veröffentlichungsinstanz. Erfordert AEM Version 2021.03.5104.20210328T185548Z oder höher.

* Die Fehlermeldung beim Starten einer Pipeline beim Löschen einer Umgebung wurde geklärt.

* Von Eclipse-Projekten bereitgestellte OSGi-Bundles sind jetzt von der Regel `CQBP-84--dependencies` ausgeschlossen.

### Fehlerbehebungen {#bug-fixes-cm-april}

* Beim Bearbeiten der Seite Erlebnisprüfung einer Pipeline führt ein Eingabepfad, der mit einem Schrägstrich `( / )` beginnt, nicht mehr dazu, dass der Schritt im Status &quot;Ausstehend&quot;feststeckt.

* Wenn beim Erstellen einer neuen Produktions-Pipeline vom Benutzer keine Überschreibung bei der Inhaltsprüfung hinzugefügt wird, wurde die standardmäßige Homepage nicht geprüft.

* Probleme für `CloudServiceIncompatibleWorkflowProcess` hatten den falschen Schweregrad in der herunterladbaren CSV-Datei des Problems.

* Die `Runmode`-Prüfung erzeugte Fehlalarme auf Nicht-Ordner-Knoten.