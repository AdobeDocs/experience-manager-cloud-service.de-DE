---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.12.0
description: Dies sind die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.12.0.
feature: Release Information
exl-id: ee920bc5-cad7-4fac-bf73-bc1178699f90
source-git-commit: 1b7183421b9acd30697f1dc228dd9e2728d24ba6
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 95%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.12.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.12.0.

>[!NOTE]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Version von Cloud Manager in AEM as a Cloud Service Version 2021.12.0 wurde am 16. Dezember 2021 veröffentlicht. Die nächste Version ist für den 20. Januar 2022 geplant.

## Neue Funktionen {#what-is-new}

* Der Commit-Hash, der bereits in der Benutzeroberfläche sichtbar ist, wird jetzt auch in der API bereitgestellt.
* Die Seite „Aktivitäten“ enthält jetzt ein Popup für die Ausführung von Pipelines, das eine Zusammenfassung der Pipelinedetails auf einen Blick bietet.
* Es wurden Aktualisierungen hinzugefügt, die zusätzliche Details enthalten, die auf der Seite „Aktivitäten“ beschrieben werden.
* Die Registerkarte „Lernen“ in Cloud Manager bietet jetzt schnellen Zugriff auf API-Handbücher und zugehörige Ressourcen.
* Ein Benutzer mit der Rolle „Implementierungs-Manager“ kann jetzt den Erstellungsassistenten für ein Projekt/eine Verzweigung für ein Repository ohne Verzweigungen über das Aktionsmenü auf der Seite „Repositorys“ starten.
* Der Implementierungs-Manager, der sich im Workflow zum Hinzufügen oder Bearbeiten einer Pipeline befindet, wird jetzt darüber informiert, wie eine Verzweigung oder ein Projekt erstellt werden kann, wenn das ausgewählte Repository keine Verzweigungen aufweist.
* Eine neue Cloud Manager-Selbstbedienungsfunktion wurde hinzugefügt, um [das Hinzufügen von Freiformvariablen und Geheimnissen auf der Umgebungsebene](/help/implementing/cloud-manager/environment-variables.md) zu ermöglichen.
* Mit dem neuen [Referenzdemo-Add-on](/help/journey-sites/demos-add-on/overview.md) (ab dem 17. Dezember 2021 verfügbar) kann die neueste Demo-Code-Basis für AEM-Produkte installiert werden und über das neue [Tool für die schnelle Site-Erstellung](/help/journey-sites/quick-site/overview.md) in Sites bereitgestellt werden.
* Frontend-Pipelines unterstützen jetzt Pipeline-Variablen.
* Screens kann jetzt im Dialog „Programmbearbeitung“ für alle Sandboxes aktiviert werden.
* Die Anleitungen, die von der Aktionsaufruf-Karte auf der Übersichtsseite bereitgestellt werden, wurden aktualisiert, und geben nun ihre Verbindung mit der Full-Stack-Produktions-Pipeline genau wieder.
* Die Aktivitätsseite wurde erweitert, sodass zusätzliche Details zu Pipelines aufgerufen werden können, einschließlich Quell-Code, Commit-ID usw.
* Beim Kopieren von TXT-Einträgen („TXT-Wert“ anstatt „TXT-Eintrag“) wurde die UI geringfügig aktualisiert, um potenzielle Verwirrung zu vermeiden.
* [Die Dokumentation zu Zertifikatfehlern](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#certificate-errors) wurde aktualisiert, um weitere Beispiele sowie Problembehebungsschritte abzudecken.
* In der Ausführung der Frontend-Pipeline ist jetzt eine Option verfügbar, mit der sie vor der Bereitstellung in der Produktion abgelehnt oder genehmigt werden kann.
* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 32 aktualisiert.


## Fehlerbehebungen {#bug-fixes}

* Funktionale Testartefakte und Testartefakte in der Benutzeroberfläche wurden nicht in das Build-Schritt-Protokoll aufgenommen.
* Die Protokolle für die Testschritte „Produkt“, „Funktionen“ und „Benutzeroberfläche“ konnten nicht über die öffentliche API erreicht werden.
* In seltenen Fällen funktioniert der Link von der Umgebungsdetailseite zum Veröffentlichungs- oder Vorschau-Service nicht.
* Full-Stack-Produktions-Pipelines erhalten weiterhin den Namen „Produktions-Pipeline“, selbst wenn der Benutzer einen anderen Namen in das Namensfeld eingibt.
