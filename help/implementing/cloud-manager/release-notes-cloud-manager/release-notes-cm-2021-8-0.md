---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.8.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.8.0
feature: Release Information
source-git-commit: f9f24fb4cdf1a98aeb08248f027e2df40d844337
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 62%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.8.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.8.0.

>[!NOTE]
>Klicken Sie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de), um die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service anzuzeigen.

## Veröffentlichungsdatum {#release-date}

Die Version 2021.8.0 von Cloud Manager in AEM as a Cloud Service wurde am 12. August 2021 veröffentlicht.
Die nächste Version wird am 9. September 2021 veröffentlicht.

### Neue Funktionen {#what-is-new}

* Cloud Service können jetzt Berichte zur Service Level Agreement (SLA) in Cloud Manager anzeigen. Dies wird in den nächsten Monaten schrittweise bereitgestellt.
Weitere Informationen finden Sie unter [SLA Reporting](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sla-reporting.html) .

* Typ und Schweregrad der Qualitätsregeln IndexType und `IndexDamAssetLucene` wurden geändert. Dies sind nun beide Fehler von Blocker *serverity*.

* Neue Qualitätsregeln für Oak-Indizes wurden eingeführt, um asynchrone und tika-Konfigurationen abzudecken.

* Erhöhen Sie die maximale Anzahl von SSL-Zertifikaten pro Programm auf 50.

* Self-Service-Funktion, mit der Benutzer über die Cloud Manager-Benutzeroberfläche mehrere Repositorys erstellen und verwalten können.

* SonarQube liest unnötigerweise Git-Verlaufsdaten. Auf großen Code-Basen konnte dies zu einer unnötigen Build-Leistungsbeeinträchtigung führen.

* Es ist jetzt eine API verfügbar, um den Maven-Abhängigkeits-Cache pro Pipeline zu invalidieren.

* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 29 aktualisiert.

### Fehlerbehebungen {#bug-fixes}

* Fehlerkorrektur – Der Status Update verfügbar wird nicht mehr angezeigt, wenn die neueste Version kleiner als die aktuelle Version ist.

* Das anfängliche Onboarding schlug bei neuen Unternehmen mit sehr langen Namen fehl.

* Wenn eine Pipeline gelegentlich aus irgendeinem Grund zweimal ausgelöst wird, führt dies nicht mehr dazu, dass eine der Ausführungen mit dem Fehler *Pipeline-Ausführungsstatus konnte nicht aktualisiert werden* fehlschlägt.
