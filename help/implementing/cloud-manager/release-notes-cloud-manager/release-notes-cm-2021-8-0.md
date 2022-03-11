---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.8.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.8.0
feature: Release Information
exl-id: cf1d5c4f-404a-4ced-90f2-273c710adc0f
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 100%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.8.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.8.0.

>[!NOTE]
>Klicken Sie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de), um die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service anzuzeigen.

## Veröffentlichungsdatum {#release-date}

Die Version 2021.8.0 von Cloud Manager in AEM as a Cloud Service wurde am 12. August 2021 veröffentlicht.

### Neue Funktionen {#what-is-new}

* Cloud Service-Kunden können jetzt Berichte zum Service Level Agreement (SLA) in Cloud Manager anzeigen. Dies wird in den nächsten Monaten schrittweise bereitgestellt.
Weitere Informationen finden Sie im Abschnitt [SLA-Reporting](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sla-reporting.html?lang=de).

* Typ und Schweregrad des IndexType und der `IndexDamAssetLucene`-Qualitätsregeln haben sich geändert. Dies sind nun beides Fehler vom *Schweregrad* „Blocker“.

* Neue Qualitätsregeln für Oak-Indizes wurden eingeführt, um asynchrone und tika-Konfigurationen abzudecken.

* Die maximale Anzahl von SSL-Zertifikaten pro Programm wurde auf 50 erhöht.

* Self-Service-Funktion, mit der Benutzer über die Cloud Manager-Benutzeroberfläche mehrere Repositorys erstellen und verwalten können.

* SonarQube hat unnötigerweise Git-Verlaufsdaten gelesen. Auf großen Code-Basen konnte dies zu einer unnötigen Build-Leistungsbeeinträchtigung führen.

* Es ist jetzt eine API verfügbar, um den Maven-Abhängigkeits-Cache pro Pipeline zu invalidieren.

* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 29 aktualisiert.

### Fehlerbehebungen {#bug-fixes}

* Der Status „Update verfügbar“ wird nicht mehr angezeigt, wenn die neueste Version niedriger als die aktuelle Version ist.

* Das anfängliche Onboarding schlägt bei neuen Organisationen mit sehr langen Namen nicht mehr fehl.

* Wenn eine Pipeline gelegentlich aus irgendeinem Grund zweimal ausgelöst wird, führt dies nicht mehr dazu, dass eine der Ausführungen mit dem Fehler *Pipeline-Ausführungsstatus konnte nicht aktualisiert werden* fehlschlägt.
