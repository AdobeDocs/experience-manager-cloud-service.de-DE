---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.5.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.5.0
feature: Versionshinweise
translation-type: tm+mt
source-git-commit: e2d4bb7649fad3ee172c6f049ecfdedc71417ee2
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 16%

---


# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.5.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.5.0.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für Cloud Manager in AEM als Cloud Service 2021.5.0 ist der 06. Mai 2021.
Die nächste Version ist für den 03. Juni 2021 geplant.

### Neue Funktionen {#what-is-new}

* Die PackageOverlaps-Qualitätsregel erkennt jetzt Fälle, in denen dasselbe Paket mehrmals bereitgestellt wurde, d. h. an mehreren eingebetteten Speicherorten, und zwar in demselben bereitgestellten Paketsatz.

* Der Repository-Endpunkt in der öffentlichen API enthält jetzt die Git-URL.

* Das von einem Cloud Manager-Benutzer heruntergeladene Bereitstellungsprotokoll enthält jetzt Details zu Fehlern und Erfolgsszenarien.

* Zwischenweise auftretende Fehler beim Verschieben von Code in Adobe git wurden nun behoben.

* Das Commerce-Add-on kann jetzt während des Workflows Programm bearbeiten auf Sandbox-Programm angewendet werden.

* Das Erlebnis &quot;Programm bearbeiten&quot;wurde aktualisiert.

* Die Tabelle &quot;Domänennamen&quot;auf der Seite &quot;Umgebung-Details&quot;zeigt bis zu 250 Domänennamen per Paginierung an.

* Auf der Registerkarte &quot;Lösungen&quot;in Hinzufügen Programm und im Workflows &quot;Programm bearbeiten&quot;wird die Lösung angezeigt, auch wenn nur eine Lösung für das Programm verfügbar ist.

* Die Fehlermeldung im Protokoll des Buildschritts, wenn der Build keine bereitgestellten Inhaltspakete generiert hat, war unklar.

### Fehlerbehebungen {#bug-fixes}

* Gelegentlich wird dem Benutzer neben einer IP-Zulassungsliste ein grüner &quot;Aktiv&quot;-Status angezeigt, selbst wenn diese Konfiguration nicht bereitgestellt wurde.

* Statt &#39;gelöschte&#39; Variablen zu entfernen, markiert die Pipeline-Variablen-API sie nur mit dem Status **DELETED**.

* Einige Qualitätsprobleme mit Code-Geruch haben die Zuverlässigkeitsbewertung fälschlicherweise beeinflusst.

* Da Platzhalterdomänen nicht unterstützt werden, verhindert die Benutzeroberfläche, dass der Benutzer eine Platzhalterdomäne sendet.

* Wenn eine Pipeline-Ausführung zwischen Mitternacht und 1am UTC gestartet wurde, war nicht garantiert, dass die von Cloud Manager generierte Artefaktversion größer ist als eine Version, die am Vortag erstellt wurde.

* Während der Einrichtung des Sandbox-Programms wird nach erfolgreicher Erstellung des Projekts mit Beispielcode Git verwalten als Link von der Heldenkarte auf der Seite Überblick angezeigt.