---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.5.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.5.0
feature: Versionshinweise
source-git-commit: 13d45a02169fc99be60d73dde91dbc8c2ce03ef8
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 17%

---


# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.5.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.5.0.

>[!NOTE]
>Um die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service anzuzeigen, klicken Sie auf [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Die Version 2021.5.0 von Cloud Manager in AEM as a Cloud Service wurde am 6. Mai 2021 veröffentlicht.
Die nächste Version ist für den 10. Juni 2021 geplant.

### Neue Funktionen {#what-is-new}

* Die Qualitätsregel PackageOverlaps erkennt jetzt Fälle, in denen dasselbe Paket mehrmals bereitgestellt wurde, d. h. an mehreren eingebetteten Speicherorten, in demselben bereitgestellten Paketsatz.

* Der Repository-Endpunkt in der öffentlichen API enthält jetzt die Git-URL.

* Das von einem Cloud Manager-Benutzer heruntergeladene Bereitstellungsprotokoll enthält jetzt Details zu Fehlern und Erfolgsszenarios.

* Beim Pushen von Code an Adobe Git wurden zeitweise auftretende Fehler behoben.

* Das Commerce-Add-on kann jetzt während des Workflows Programm bearbeiten auf Sandbox-Programme angewendet werden.

* Das Erlebnis *Programm bearbeiten* wurde aktualisiert.

* In der Tabelle &quot;Domänennamen&quot;auf der Seite &quot;Umgebungsdetails&quot;werden bis zu 250 Domänennamen per Paginierung angezeigt.

* Auf der Registerkarte **Lösungen und Add-ons** in **Hinzufügen von Programmen** und **Programm bearbeiten** -Workflows wird die Lösung angezeigt, auch wenn für das Programm nur eine Lösung verfügbar ist.

* Die Fehlermeldung im Build-Schrittprotokoll, wenn der Build keine bereitgestellten Inhaltspakete generiert hat, war unklar.

### Fehlerbehebungen {#bug-fixes}

* Gelegentlich kann der Benutzer neben einer IP-Zulassungsliste einen grünen &quot;aktiven&quot;Status sehen, selbst wenn diese Konfiguration nicht bereitgestellt wurde.

* Anstatt &quot;gelöschte&quot;Variablen zu entfernen, markiert die Pipeline-Variablen-API sie nur mit dem Status **DELETED**.

* Einige Qualitätsprobleme vom Typ Code Smell wirkten sich fälschlicherweise auf die Zuverlässigkeitsbewertung aus.

* Da Wildcard-Domänen nicht unterstützt werden, verhindert die Benutzeroberfläche das Senden einer Wildcard-Domäne durch den Benutzer.

* Wenn die Pipelineausführung zwischen Mitternacht und 1 Uhr UTC gestartet wurde, war nicht garantiert, dass die von Cloud Manager generierte Artefaktversion größer ist als die am Vortag erstellte Version.

* Während der Einrichtung des Sandbox-Programms wird nach erfolgreicher Erstellung des Projekts mit Beispielcode Git verwalten auf der Seite Überblick als Link von der Heldenkarte angezeigt.
