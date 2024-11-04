---
title: Universal Editor 2024.09.3 - Versionshinweise
description: Dies sind die Versionshinweise für die Version 2024.09.3 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: b70acef8dc259fff3041617abe0a89f7eb73dfab
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 1%

---


# Universal Editor 2024.09.3 - Versionshinweise {#release-notes}

Dies sind die Versionshinweise für die Version des universellen Editors vom 3. September 2024.

>[!TIP]
>
>Die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service finden Sie auf [dieser Seite.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## Neue Funktionen {#what-is-new}

* **`rootPath`jetzt für die Inhaltsauswahl verfügbar**: Die Inhaltsauswahl kann jetzt mit einem `rootPath` versehen werden, um dem Benutzer bei Verwendung der Feldtypen [AEM Inhalt, ](/help/implementing/universal-editor/field-types.md#aem-content) [Inhaltsfragment, ](/help/implementing/universal-editor/field-types.md#content-fragment) und [Erlebnisfragment](/help/implementing/universal-editor/field-types.md#experience-fragment) eine gezielte Auswahl an Inhalten anzuzeigen.
   * Die Inhaltsauswahl ist daher auf Inhalte im angegebenen Pfad und auf Unterverzeichnisse beschränkt.

## Frühzeitige Annahme des Programms für 6.5-Unterstützung {#early-adoption}

Der Universal Editor ist jetzt für Headless-Anwendungsfälle verfügbar, wenn AEM 6.5 im Rahmen eines Programms für frühe Anwender verwendet wird.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte eine E-Mail an Ihren Adobe-Support-Mitarbeiter aus der E-Mail-Adresse, die mit Ihrer Adobe ID verknüpft ist.

## Fehlerbehebungen {#bug-fixes}

* **Container-übergreifendes Ziehen und Ablegen**: [Beim Verschieben von Komponenten zwischen verschiedenen Containern per Drag &amp; Drop](/help/sites-cloud/authoring/universal-editor/authoring.md#reordering-components) wird beim Verschieben von Komponenten zwischen verschiedenen Containern jetzt sowohl in der Quelle als auch in der Zielgruppe [Komponentenfilter](/help/implementing/universal-editor/customizing.md#filtering-components) berücksichtigt.
