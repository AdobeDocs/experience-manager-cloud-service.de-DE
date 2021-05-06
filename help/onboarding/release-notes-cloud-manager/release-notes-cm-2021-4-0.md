---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.4.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.4.0
feature: Versionshinweise
translation-type: tm+mt
source-git-commit: e2d4bb7649fad3ee172c6f049ecfdedc71417ee2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.4.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.4.0.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für Cloud Manager in AEM als Cloud Service 2021.4.0 ist der 08. April 2021.
Die nächste Version ist für den 06. Mai 2021 geplant.

### Neue Funktionen {#what-is-new-april}

* Die Benutzeroberfläche wird aktualisiert, um das Hinzufügen- und Bearbeiten-Programm-Workflows intuitiver zu gestalten.

* Ein Benutzer mit erforderlichen Berechtigungen kann jetzt den Commerce-Endpunkt über die Benutzeroberfläche senden.

* Umgebung können jetzt auf einen bestimmten Dienst übertragen werden, entweder auf Autor oder auf Veröffentlichung. Erfordert AEM Version `2021.03.5104.20210328T185548Z` oder höher.

* Die Schaltfläche **Git** verwalten wird auf der Pipelines-Karte angezeigt, auch wenn keine Pipelines konfiguriert wurden.

* Die Version des von Cloud Manager verwendeten AEM Projektarchivs wurde auf Version 27 aktualisiert.

* Projekte, die in der Adobe I/O Developer Console von Cloud Manager erstellt wurden, können nicht mehr unbeabsichtigt bearbeitet oder gelöscht werden.

* Wenn ein Benutzer eine neue Umgebung hinzufügt, wird ihm mitgeteilt, dass eine Umgebung nach dem Erstellen nicht in einen anderen Bereich verschoben werden kann.

* Umgebung können jetzt auf einen bestimmten Dienst übertragen werden, entweder auf Autor oder auf Veröffentlichung. Erfordert AEM Version 2021.03.5104.20210328T185548Z oder höher.

* Die Fehlermeldung beim Starten einer Pipeline beim Löschen einer Umgebung wurde geklärt.

* OSGi-Pakete, die von Eclipse-Projekten bereitgestellt werden, sind nun von der Regel `CQBP-84--dependencies` ausgeschlossen.

### Fehlerbehebungen {#bug-fixes-cm-april}

* Beim Bearbeiten der Experience Audit-Seite einer Pipeline führt ein Eingabepfad, der mit einem Schrägstrich `( / )` beginnt, nicht mehr dazu, dass der Schritt im ausstehenden Status blockiert wird.

* Wenn eine neue Produktions-Pipeline erstellt wird und der Benutzer keine Überschreibung der Inhaltsprüfung hinzufügt, wurde die Standard-Homepage nicht geprüft.

* Bei Problemen mit `CloudServiceIncompatibleWorkflowProcess` war die CSV-Datei für die herunterladbare Ausgabe nicht korrekt.

* Die `Runmode`-Prüfung ergab Falsch-Positiv-Werte für Nicht-Ordner-Knoten.