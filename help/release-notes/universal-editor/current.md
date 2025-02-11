---
title: Universeller Editor – Versionshinweise für 2054.01.16
description: Dies sind die Versionshinweise für die Version 2025.01.16 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: ht
source-wordcount: '236'
ht-degree: 100%

---


# Universeller Editor – Versionshinweise für 2025.01.16 {#release-notes}

Dies sind die Versionshinweise für die Version vom 16. Januar 2025 des universellen Editors.

>[!TIP]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Neue Funktionen {#what-is-new}

* **Einstellung der CORS-Bibliothek &lt; 3.0.0**: Um die zukünftige Kompatibilität sicherzustellen und die Sicherheit zu verbessern, unterstützt der universelle Editor nun ausschließlich die Version 3.0.0 oder höher der
  `@Adobe Express/universal-editor-cors`-Bibliothek.
   * Die Bibliothek wird jetzt ausschließlich über [`universal-editor-service.adobe.io/cors.js`](http://universal-editor-service.adobe.io/cors.js) bereitgestellt.
   * Benutzende werden beim Öffnen einer Seite, die ältere Versionen der CORS-Bibliothek verwendet, über die Einstellung dieser Version informiert und aufgefordert, sie zu aktualisieren.
* **Erweiterungspunkt für Landingpage**: [Ein neuer Erweiterungspunkt](/help/implementing/universal-editor/customizing.md#extending) wurde eingeführt, damit Erweiterungen in der Seitenleiste der Landingpage des universellen Editors angezeigt werden.
   * Nun können Entwickelnde angeben, ob Erweiterungen für den Editor, die Landingpage oder beides gelten. Dies sorgt für bessere Anpassungsmöglichkeiten und eine größere Benutzerfreundlichkeit.

## Andere Verbesserungen {#other-improvements}

* **Ungültige URLs unter „Zuletzt verwendet“ auf der Landingpage korrigiert**: Es wurde ein Problem behoben, durch das die URLs, die in der Liste „Zuletzt verwendet“ auf der Landingpage des universellen Editors angezeigt wurden, beschädigt waren.
* **Design-Synchronisation in Unified Shell**: Der universelle Editor synchronisiert das Design nun dynamisch mit den Unified Shell-Einstellungen des Systems und führt eine automatische Anpassung zwischen hellem und dunklem Modus durch.
   * Dadurch wird ein konsistentes visuelles Erscheinungsbild über Mikro-Frontends hinweg sichergestellt, einschließlich Fragment- und Asset-Auswahl.
