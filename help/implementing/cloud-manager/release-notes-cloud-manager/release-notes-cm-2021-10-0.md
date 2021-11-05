---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.10.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.10.0
feature: Release Information
exl-id: null
source-git-commit: c6c1d3bef85afda0ff86ec073d0ac91ad532c93b
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 20%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.10.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.10.0.

>[!NOTE]
>Klicken Sie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de), um die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service anzuzeigen.

## Veröffentlichungsdatum {#release-date}

Die Cloud Manager-Version AEM as a Cloud Service Version 2021.10.0 wurde am 14. Oktober 2021 veröffentlicht.


### Neue Funktionen {#what-is-new}

* In Vorbereitung auf einige bevorstehende Änderungen werden bestehende Implementierungs-Pipelines nun in der Benutzeroberfläche als **Voller Stapel** Pipelines.

* Die Pipeline-Karte wurde aktualisiert und zeigt jetzt ein einziges, integriertes Gesicht, das sowohl Produktions- als auch Nicht-Produktions-Pipelines anzeigt, und der Benutzer kann Ausführen/Aussetzen/Fortsetzen direkt aus dem Aktionsmenü auswählen, das mit jeder Pipeline verknüpft ist.

* Ein Benutzer mit der Rolle &quot;Bereitstellungsmanager&quot;kann nun die Produktions-Pipeline über die Benutzeroberfläche auf Self-Service-Weise löschen.

* Das Hinzufügen und Bearbeiten von Pipeline-Erlebnissen wurde aktualisiert und verwendet jetzt vertraute, moderne Modale.

* Benutzer von Cloud Manager können jetzt Feedback direkt über die Benutzeroberfläche über die **Feedback** rechts oben auf der Landingpage.

* Jährliche SLA-Diagramme können jetzt von der Benutzeroberfläche von Cloud Manager heruntergeladen werden.

* Code-Qualitäts- und Nicht-Produktions-Pipeline-Ausführungen verwenden jetzt während des Build-Schritts einen effizienteren Prozess zum Klonen von flachen Elementen, was zu einer schnelleren Build-Zeit für Kunden mit besonders großen Git-Repositorys führt.

* Der Assistent IP-Zulassungsliste hinzufügen informiert den Benutzer jetzt darüber, ob die maximal zulässige Anzahl von IP-Zulassungslisten erreicht wurde.

* Die Dokumentation zur Cloud Manager-API enthält jetzt einen interaktiven Spielplatz, auf dem angemeldete Benutzer über ihren Browser mit der API experimentieren können. Siehe [Cloud Manager-API-Wiedergabe](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) für weitere Details.

* Die QuickInfo auf der Programmkarte ist beschreibender, wenn eine Auswahloption unter &quot;Navigieren zu&quot;deaktiviert ist. Jetzt wird &quot;Es gibt keine Produktionsumgebung mehr&quot; angezeigt.

### Fehlerbehebungen {#bug-fixes}

* In seltenen Fällen, in denen Mitarbeiter der Adobe die Umgebung eines Kunden wiederherstellen, wurde die Wiederherstellung als abgeschlossen angesehen, bevor die Umgebung voll funktionsfähig war.

* Bestimmte interne Anforderungen, die während der Erstellung der Umgebung gestellt wurden, wurden nicht erneut versucht.

* Wenn nach der Verifizierung des Domain-Namens ein Fehler bei der Bereitstellung auftritt, wurde die Fehlermeldung korrigiert, um den Kunden aufzufordern, sich an seinen Kundenbetreuer zu wenden.

