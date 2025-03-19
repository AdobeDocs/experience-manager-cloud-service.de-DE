---
title: Universeller Editor – Versionshinweise für 2025.03.10
description: Dies sind die Versionshinweise für die Version 2025.03.10 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: b3c98f5e41dbc5e1714d0ed418a317199c735b73
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 23%

---


# Universeller Editor – Versionshinweise für 2025.03.10 {#release-notes}

Dies sind die Versionshinweise für die Version vom 10. März 2025 des universellen Editors.

>[!TIP]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Neue Funktionen {#what-is-new}

* **Komponenten werden verschoben** Beim [Verschieben von Komponenten zwischen Containern](/help/sites-cloud/authoring/universal-editor/authoring.md#reordering-components) wird jetzt der Komponentenfilter des Ziel-Containers beobachtet.
   * Es ist nicht mehr erforderlich, dieselbe [Filterdefinition](/help/implementing/universal-editor/filtering.md) sowohl für Ziel- als auch für Zielcontainer zu verwenden, um die Komponente zwischen den Containern zu verschieben.
* **Gesperrte Seiten:** universelle Editor-Dienst beobachtet den [Sperrstatus einer Seite](/help/sites-cloud/authoring/sites-console/managing-pages.md#locking-a-page) und schreibt nur in Seiten, die nicht gesperrt sind oder vom Benutzer gesperrt werden.

## Andere Verbesserungen {#other-improvements}

* Es wurden Korrekturen vorgenommen, um die Validierung für die Headless-Arbeitsfläche zu korrigieren.

## Veraltete Version {#deprecation}

* Die über npm oder `https://unviersal-editor-service.experiencecloud.live/corslib/*` bereitgestellte `universal-editor-cors`-Bibliothek sollte nicht mehr verwendet werden.
   * Stattdessen sollte ein Skript-Tag verwendet werden, das auf `https://universal-editor-service.adobe.io/cors.js` verweist.
   * Weitere Informationen [ richtigen Instrumentierung Ihrer Seite für die Verwendung mit dem universellen Editor finden Sie ](/help/implementing/universal-editor/developer-overview.md) „Übersicht über den universellen Editor für AEM-Entwickler“.
   * Benutzern wird einmal täglich eine Meldung angezeigt, dass der Versand eingestellt wurde, wenn die falsche Methode verwendet wird.
