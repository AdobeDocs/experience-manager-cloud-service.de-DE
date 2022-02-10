---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2022.01.0
description: Dies sind die Versionshinweise für Cloud Manager in AEM as a Cloud Service Version 2022.01.0.
feature: Release Information
source-git-commit: 6b0fd14fb2038e09b59fa487427b3202d8f129dc
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 26%

---


# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2022.01.0 {#release-notes}

Auf dieser Seite werden die Versionshinweise für Cloud Manager in AEM as a Cloud Service Version 2022.01.0 beschrieben.

>[!NOTE]
>
>Siehe [diese Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) für die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Version von Cloud Manager in AEM as a Cloud Service Version 2022.01.0 wurde am 20. Januar 2022 veröffentlicht. Die nächste Version soll am 10. Februar 2022 veröffentlicht werden.

## Neue Funktionen {#what-is-new}

* Cloud Manager wird [Vermeiden Sie die Neuerstellung der Code-Basis, wenn festgestellt wird, dass dieselbe Git-Bestätigung verwendet wird.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) in mehreren vollständigen Pipelineausführungen.
* Für den Zugriff auf das AEM-Umgebungsprotokoll ist jetzt die **Bereitstellungsmanager** Produktprofil. Benutzern ohne dieses Profil wird in der Benutzeroberfläche eine deaktivierte Schaltfläche angezeigt.
* Die Benutzeroberfläche lässt keine Konfiguration der Frontend-Pipeline für ein Programm zu, bei dem Sites nicht als Lösung aktiviert ist.
* Beim Generieren eines Git-Kennworts wird das Ablaufdatum angezeigt.

## Fehlerbehebungen {#bug-fixes}

* Null-Zeiger-Ausnahmen, die bei einigen Frontend-Pipeline-Bereitstellungen aufgetreten sind, wurden korrigiert.
* Umgebungsvariablen können jetzt hinzugefügt, aktualisiert und gelöscht werden, wenn eine Umgebung eine veraltete Version von AEM ausführt.
* Der Schritt zum Erstellen eines Bildes wird nicht mehr als FEHLER für Pipelines markiert, die den geplanten Schritt in bestimmten seltenen Fällen verwendet haben.
* Bei Programmen mit nur einem Repository zeigt der Bildschirm zur Pipeline-Ausführung jetzt den Namen des Repositorys an.
