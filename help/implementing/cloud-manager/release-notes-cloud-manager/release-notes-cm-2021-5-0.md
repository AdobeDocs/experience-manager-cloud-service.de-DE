---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.5.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.5.0
feature: Versionshinweise
exl-id: 8ae3cf2f-1865-427a-b612-bdf56e2f0304
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 87%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.5.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.5.0.

>[!NOTE]
>Um die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service anzuzeigen, klicken Sie auf [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von Cloud Manager in AEM as a Cloud Service Version 2021.5.0 war der 6. Mai 2021.

### Neue Funktionen {#what-is-new}

* Die Qualitätsregel PackageOverlaps erkennt jetzt Fälle, in denen dasselbe Package mehrmals bereitgestellt wurde, d. h. an mehreren eingebetteten Speicherorten, in demselben bereitgestellten Package-Satz.

* Der Repository-Endpunkt in der Public-API enthält jetzt die Git-URL.

* Das von einem Cloud Manager-Benutzer heruntergeladene Bereitstellungsprotokoll enthält jetzt Details zu Fehlern und Erfolgsszenarios.

* Beim Pushen von Code an Adobe Git wurden treten jetzt keine Fehler mehr auf.

* Das Commerce-Add-on kann jetzt während des Workflows „Programm bearbeiten“ auf Sandbox-Programme angewendet werden.

* Das Erlebnis *Programm bearbeiten* wurde aktualisiert.

* In der Tabelle „Domain-Namen“ auf der Seite „Umgebungsdetails“ werden bis zu 250 Domain-Namen per Paginierung angezeigt.

* Auf der Registerkarte **Lösungen und Add-ons** in **Hinzufügen von Programmen** und **Programm bearbeiten** -Workflows wird die Lösung angezeigt, auch wenn für das Programm nur eine Lösung verfügbar ist.

* Die Fehlermeldung im Build-Schrittprotokoll, wenn der Build keine bereitgestellten Inhaltspakete generiert hat, ist jetzt klar.

### Fehlerbehebungen {#bug-fixes}

* Dem Benutzer wird neben einer IP-Zulassungsliste kein grüner „aktiver“ Status mehr angezeigt, wenn diese Konfiguration nicht bereitgestellt wurde.

* Die Pipeline-Variablen-API markiert „gelöschte“ Variablen nicht nur mit dem Status **GELÖSCHT**, sondern entfernt sie jetzt tatsächlich.

* Einige Code-Smell-Qualitätsprobleme haben die Zuverlässigkeitsbewertung fälschlicherweise beeinflusst.

* Dank der Unterstützung von Wildcard-Domains kann der Benutzer jetzt Wildcard-Domains über die Benutzeroberfläche senden.

* Wenn eine Pipeline-Ausführung zwischen Mitternacht und 1:00 Uhr UTC gestartet wurde, war nicht garantiert, dass die von Cloud Manager generierte Artefaktversion größer war als eine Version, die am Vortag erstellt wurde.

* Fehlerkorrektur – Während der Einrichtung des Sandbox-Programms wird jetzt, sobald das Projekt mit dem Beispiel-Code erfolgreich erstellt wurde, „Git verwalten“ als Link von der Hero-Karte auf der Übersichtsseite angezeigt.
