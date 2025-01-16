---
title: Universeller Editor – Versionshinweise für 2054.01.16
description: Dies sind die Versionshinweise für die Version 2025.01.16 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 14bc45917f56ecf358278848e7e830afb1fedccd
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 19%

---


# Universeller Editor – Versionshinweise für 2025.01.16 {#release-notes}

Dies sind die Versionshinweise für die Version vom 16. Januar 2025 des universellen Editors.

>[!TIP]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Neue Funktionen {#what-is-new}

* **Einstellung der CORS-Bibliothek &lt; 3.0.0** - Um für die zukünftige Kompatibilität zu sorgen und die Sicherheit zu verbessern, unterstützt der universelle Editor jetzt ausschließlich Version 3.0.0 oder höher des
  Bibliothek `@Adobe Express/universal-editor-cors`.
   * Die Bibliothek wird jetzt ausschließlich über [`universal-editor-service.adobe.io/cors.js` bereitgestellt.](http://universal-editor-service.adobe.io/cors.js)
   * Benutzer werden beim Öffnen einer Seite, die ältere Versionen der CORS-Bibliothek verwendet, über das Verwerfen informiert und aufgefordert, sie zu aktualisieren.
* **Erweiterungspunkt für Landingpage** - [Ein neuer Erweiterungspunkt](/help/implementing/universal-editor/customizing.md#extending) wurde eingeführt, damit Erweiterungen in der Seitenleiste der Landingpage des universellen Editors angezeigt werden.
   * Jetzt können Entwickler angeben, ob Erweiterungen für den Editor, die Landingpage oder beides gelten, was eine bessere Anpassung und Benutzerfreundlichkeit bietet.

## Andere Verbesserungen {#other-improvements}

* **Ungültige URLs in „Zuletzt ausgewertet“ auf der Landingpage wurden behoben** Es wurden Probleme behoben, bei denen die in der Liste „Zuletzt ausgewertet“ auf der Landingpage des universellen Editors angezeigten URLs beschädigt waren.
* **Design-Synchronisation in Unified Shell** - Der universelle Editor synchronisiert das Design jetzt dynamisch mit den Unified Shell-Einstellungen des Systems und passt sich automatisch zwischen dem hellen und dem dunklen Modus an.
   * Dadurch wird ein konsistentes visuelles Erscheinungsbild über Mikro-Frontends hinweg sichergestellt, einschließlich Fragment- und Asset-Selektoren.
