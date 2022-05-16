---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2022.01.0
description: Dies sind die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2022.01.0.
feature: Release Information
exl-id: 2dfdc943-0518-40ea-8712-1dabb97eeaa9
source-git-commit: 6e394aaabcb123aea53fba49684aaade3e6c87a6
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2022.01.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2022.01.0.

>[!NOTE]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Cloud Manager-Version in AEM as a Cloud Service Version 2022.01.0 wurde am 20. Januar 2022 veröffentlicht. Die Veröffentlichung der nächsten Version war für den 10. Februar 2022 geplant.

## Neue Funktionen {#what-is-new}

* Cloud Manager [vermeidet die Neuerstellung der Code-Basis, wenn festgestellt wird, dass derselbe Git-Commit in mehreren Full-Stack-Pipeline-Ausführungen verwendet wird](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse).
* Für den Zugriff auf das AEM-Umgebungsprotokoll ist jetzt das Produktprofil **Bereitstellungs-Manager** erforderlich. Benutzern ohne dieses Profil wird in der Benutzeroberfläche eine deaktivierte Schaltfläche angezeigt.
* Die Benutzeroberfläche lässt keine Konfiguration der Frontend-Pipeline für ein Programm zu, bei dem Sites nicht als Lösung aktiviert ist.
* Beim Generieren eines Git-Passworts wird das Ablaufdatum angezeigt.

## Fehlerbehebungen {#bug-fixes}

* Null-Pointer-Ausnahmen, die bei einigen Frontend-Pipeline-Implementierungen aufgetreten sind, wurden korrigiert.
* Umgebungsvariablen können jetzt hinzugefügt, aktualisiert und gelöscht werden, wenn eine Umgebung eine veraltete Version von AEM ausführt.
* Der Schritt zum Erstellen eines Bildes wird in bestimmten seltenen Fällen für Pipelines, die den geplanten Schritt verwendet haben, nicht mehr als FEHLER markiert.
* Bei Programmen mit nur einem Repository zeigt der Bildschirm zur Pipeline-Ausführung jetzt den Repository-Namen an.
