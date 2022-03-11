---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.10.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.10.0
feature: Release Information
exl-id: f8a87b00-52ce-42a6-a955-45cb14703b40
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 100%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.10.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.10.0.

>[!NOTE]
>Klicken Sie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de), um die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service anzuzeigen.

## Veröffentlichungsdatum {#release-date}

Die Version 2021.10.0 von Cloud Manager in AEM as a Cloud Service wurde am 14. Oktober 2021 veröffentlicht.


### Neue Funktionen {#what-is-new}

* In Vorbereitung auf einige bevorstehende Änderungen werden bestehende Implementierungs-Pipelines nun in der Benutzeroberfläche als **Full Stack**-Pipelines referenziert und benannt.

* Die Pipeline-Karte wurde aktualisiert und zeigt jetzt ein einziges, integriertes Gesicht, das sowohl Produktions-Pipelines als auch produktionsfremde Pipelines anzeigt, und der Benutzer kann Ausführen/Aussetzen/Fortsetzen direkt aus dem Aktionsmenü auswählen, das mit jeder Pipeline verknüpft ist.

* Ein Benutzer mit der Rolle „Implementierungs-Manager“ kann nun die Produktions-Pipeline über die Benutzeroberfläche im Self-Service löschen.

* Das Hinzufügen und Bearbeiten von Pipeline-Erlebnissen wurde aktualisiert und verwendet jetzt vertraute, moderne Modale.

* Benutzer von Cloud Manager können jetzt Feedback direkt über die Benutzeroberfläche über die Schaltfläche **Feedback** rechts oben auf der Landingpage übermitteln.

* Von der Benutzeroberfläche von Cloud Manager können jetzt jährliche SLA-Diagramme heruntergeladen werden.

* Ausführungen von Code-Qualitäts-Pipelines und produktionsfremden Pipelines verwenden jetzt während des Build-Schritts einen effizienteren Prozess zum Klonen von flachen Elementen, was zu einer schnelleren Build-Zeit für Kunden mit besonders großen Git-Repositorys führt.

* Der Assistent „IP-Zulassungsliste hinzufügen“ informiert den Benutzer jetzt darüber, ob die maximal zulässige Anzahl von IP-Zulassungslisten erreicht wurde.

* Die Dokumentation zur Cloud Manager-API enthält jetzt einen interaktiven Spielplatz, auf dem angemeldete Benutzer über ihren Browser mit der API experimentieren können. Weitere Einzelheiten finden Sie unter [Cloud Manager API Playground](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/).

* Die QuickInfo auf der Programmkarte ist aussagekräftiger, wenn eine Auswahloption unter „Navigieren zu“ deaktiviert ist. Jetzt wird „Es ist keine Produktionsumgebung vorhanden“ angezeigt.

### Fehlerbehebungen {#bug-fixes}

* In den seltenen Fällen, in denen Mitarbeiter von Adobe die Umgebung eines Kunden wiederherstellen, wird jetzt die Wiederherstellung nicht mehr als abgeschlossen angesehen, bevor die Umgebung voll funktionsfähig ist.

* Bestimmte interne Anfragen, die während der Erstellung der Umgebung gestellt wurden, werden jetzt erneut ausgeführt.

* Die Fehlermeldung für den Fall, dass nach der Überprüfung des Domain-Namens ein Fehler bei der Bereitstellung auftritt, wurde dahingehend korrigiert, dass der Kunde aufgefordert wird, sich an seinen Adobe-Support-Mitarbeiter zu wenden.
