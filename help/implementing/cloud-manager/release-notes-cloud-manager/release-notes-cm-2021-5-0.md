---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.5.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.5.0
feature: Versionshinweise
exl-id: 8ae3cf2f-1865-427a-b612-bdf56e2f0304
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: ht
source-wordcount: '379'
ht-degree: 100%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.5.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.5.0.

>[!NOTE]
>Klicken Sie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de), um die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service anzuzeigen.

## Veröffentlichungsdatum {#release-date}

Die Version 2021.5.0 von Cloud Manager in AEM as a Cloud Service wurde am 6. Mai 2021 veröffentlicht.

### Neue Funktionen {#what-is-new}

* Die PackageOverlaps-Qualitätsregel erkennt jetzt Fälle, in denen dasselbe Paket mehrmals bereitgestellt wurde, d. h. an mehreren eingebetteten Speicherorten, im selben bereitgestellten Paketsatz.

* Der Repository-Endpunkt in der öffentlichen API enthält jetzt die Git-URL.

* Das von Cloud Manager-Anwendern heruntergeladene Bereitstellungsprotokoll ist nun aufschlussreicher und enthält Details zu Fehlern und Erfolgsszenarios.

* Beim Pushen von Code an Adobe Git wurden treten jetzt keine Fehler mehr auf.

* Das Commerce-Add-on kann jetzt während des Workflows „Programm bearbeiten“ auf Sandbox-Programme angewendet werden.

* Das Erlebnis *Programm bearbeiten* wurde aktualisiert.

* In der Tabelle „Domain-Names“ auf der Seite mit den Umgebungsdetails werden bis zu 250 Domain-Namen mit Seitenumbruch angezeigt.

* Auf der Registerkarte **Lösungen und Add-ons** in den Workflows **Programm hinzufügen** und **Programm bearbeiten** wird die Lösung angezeigt, auch wenn für das Programm nur eine Lösung verfügbar ist.

* Die Fehlermeldung, die im Build-Schritt-Protokoll aufgeführt wurde, wenn der Build keine bereitgestellten Inhaltspakete generiert hat, war unklar.

### Fehlerbehebungen {#bug-fixes}

* Dem Benutzer wird neben einer IP-Zulassungsliste kein grüner „aktiver“ Status mehr angezeigt, wenn diese Konfiguration nicht bereitgestellt wurde.

* Anstatt „gelöschte“ Variablen zu entfernen, markiert die Pipeline-Variablen-API sie nur mit dem Status **GELÖSCHT**.

* Einige Code-Smell-Qualitätsprobleme haben sich fälschlicherweise auf die Zuverlässigkeitsbewertung ausgewirkt.

* Da Platzhalter-Domains nicht unterstützt werden, verhindert die Benutzeroberfläche das Senden von Platzhalter-Domains durch Anwender.

* Wenn die Pipeline-Ausführung zwischen Mitternacht und 1:00 Uhr UTC gestartet wurde, war nicht garantiert, dass die von Cloud Manager generierte Artefaktversion größer ist als die am Vortag erstellte Version.

* Während des Setups des Sandbox-Programms wird nach erfolgreicher Erstellung des Projekts mit Beispielcode auf der Übersichtsseite „Git verwalten“ als Link von der Hero-Karte angezeigt.
