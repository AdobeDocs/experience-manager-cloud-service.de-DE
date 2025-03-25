---
title: Universeller Editor – Versionshinweise für 2025.03.10
description: Dies sind die Versionshinweise für die Version 2025.03.10 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: b3c98f5e41dbc5e1714d0ed418a317199c735b73
workflow-type: ht
source-wordcount: '200'
ht-degree: 100%

---


# Universeller Editor – Versionshinweise für 2025.03.10 {#release-notes}

Dies sind die Versionshinweise für die Version des universellen Editors vom 10. März 2025.

>[!TIP]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Neue Funktionen {#what-is-new}

* **Verschieben von Komponenten:** [Beim Verschieben von Komponenten zwischen Containern](/help/sites-cloud/authoring/universal-editor/authoring.md#reordering-components) wird jetzt der Komponentenfilter des Ziel-Containers angewendet.
   * Es ist nicht mehr erforderlich, dieselbe [Filterdefinition](/help/implementing/universal-editor/filtering.md) sowohl für Target- als auch für Ziel-Container zu verwenden, um die Komponente zwischen den Containern zu verschieben.
* **Gesperrte Seiten:** Der Dienst „Universeller Editor“ hält sich an den [Sperrstatus einer Seite](/help/sites-cloud/authoring/sites-console/managing-pages.md#locking-a-page) und schreibt nur in Seiten, die nicht gesperrt sind oder von Benutzerseite gesperrt werden.

## Andere Verbesserungen {#other-improvements}

* Es wurden Fehlerbehebungen vorgenommen, um die Validierung für die Headless-Arbeitsfläche zu korrigieren.

## Abschaffung {#deprecation}

* Die über npm oder `https://unviersal-editor-service.experiencecloud.live/corslib/*` bereitgestellte Bibliothek `universal-editor-cors` sollte nicht mehr verwendet werden.
   * Stattdessen sollte ein Skript-Tag verwendet werden, das auf `https://universal-editor-service.adobe.io/cors.js` verweist.
   * Weitere Informationen zur richtigen Instrumentierung Ihrer Seite für die Verwendung mit dem universellen Editor finden Sie in der [Übersicht über den universellen Editor für AEM-Entwicklerinnen und -entwickler](/help/implementing/universal-editor/developer-overview.md).
   * Benutzenden wird einmal täglich eine Meldung zur kommenden Abschaffung angezeigt, wenn die falsche Methode verwendet wird.
