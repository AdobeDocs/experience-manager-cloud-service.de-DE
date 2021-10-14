---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.10.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.10.0
feature: Release Information
exl-id: null
source-git-commit: a519b5bd774506f50f49c8309b14d4a62c7e7ba5
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 21%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.10.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.10.0.

>[!NOTE]
>Klicken Sie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de), um die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service anzuzeigen.

## Veröffentlichungsdatum {#release-date}

Die Cloud Manager-Version AEM as a Cloud Service Version 2021.10.0 wurde am 14. Oktober 2021 veröffentlicht.
Die nächste Version ist für den 4. November 2021 geplant.

### Neue Funktionen {#what-is-new}

* In Vorbereitung auf einige bevorstehende Änderungen werden bestehende Implementierungs-Pipelines nun als **Vollständige Pipelines** in der Benutzeroberfläche referenziert und gekennzeichnet.

* Die Pipeline-Karte wurde aktualisiert und zeigt jetzt ein einziges, integriertes Gesicht, das sowohl Produktions- als auch Nicht-Produktions-Pipelines anzeigt, und der Benutzer kann Ausführen/Aussetzen/Fortsetzen direkt aus dem Aktionsmenü auswählen, das mit jeder Pipeline verknüpft ist.

* Ein Benutzer mit der Rolle &quot;Bereitstellungsmanager&quot;kann nun die Produktions-Pipeline über die Benutzeroberfläche auf Self-Service-Weise löschen.

* Das Hinzufügen und Bearbeiten von Pipeline-Erlebnissen wurde aktualisiert und verwendet jetzt vertraute, moderne Modale.

* Benutzer von Cloud Manager können jetzt über die Schaltfläche **Feedback** oben rechts auf der Landingpage Feedback direkt aus der Benutzeroberfläche senden.

* Jährliche SLA-Diagramme können jetzt von der Benutzeroberfläche von Cloud Manager heruntergeladen werden.

* Code-Qualitäts- und Nicht-Produktions-Pipeline-Ausführungen verwenden jetzt während des Build-Schritts einen effizienteren Prozess zum Klonen von flachen Elementen, was zu einer schnelleren Build-Zeit für Kunden mit besonders großen Git-Repositorys führt.

* Der Assistent IP-Zulassungsliste hinzufügen informiert den Benutzer jetzt darüber, ob die maximal zulässige Anzahl von IP-Zulassungslisten erreicht wurde.

* Die Dokumentation zur Cloud Manager-API enthält jetzt einen interaktiven Spielplatz, auf dem angemeldete Benutzer über ihren Browser mit der API experimentieren können. Weitere Informationen finden Sie unter [Cloud Manager API Playground](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) .

* Die QuickInfo auf der Programmkarte ist beschreibender, wenn eine Auswahloption unter &quot;Navigieren zu&quot;deaktiviert ist. Jetzt wird &quot;Es gibt keine Produktionsumgebung mehr&quot; angezeigt.

### Fehlerbehebungen {#bug-fixes}

* In seltenen Fällen, in denen Mitarbeiter der Adobe die Umgebung eines Kunden wiederherstellen, wurde die Wiederherstellung als abgeschlossen angesehen, bevor die Umgebung voll funktionsfähig war.

* Bestimmte interne Anforderungen, die während der Erstellung der Umgebung gestellt wurden, wurden nicht erneut versucht.

