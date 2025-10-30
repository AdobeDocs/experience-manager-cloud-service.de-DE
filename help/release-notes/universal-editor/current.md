---
title: Universeller Editor – Versionshinweise für 2025.10.30
description: Dies sind die Versionshinweise für die Version 2025.10.30 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: e3e571bef450ddc09eb30ab7d73b144ea521a87b
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 58%

---


# Universeller Editor – Versionshinweise für 2025.10.30 {#release-notes}

Dies sind die Versionshinweise für die Version vom 30. Oktober 2025 des universellen Editors.

>[!TIP]
>
>Informationen zum Testen von **zukünftigen** Funktionen des universellen Editors vor ihrer Veröffentlichung finden Sie in den [Vorschauversionshinweisen zum universellen Editor](/help/release-notes/universal-editor/preview.md).

>[!TIP]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Neue Funktionen {#what-is-new}

* [Der neue RTE](#new-rte) kann jetzt Bilder einfügen.
   * Diese Funktion ist OTb deaktiviert und muss explizit über eine [Filterdefinition aktiviert werden](/help/implementing/universal-editor/configure-rte.md#toolbar)

## Funktionen des Early-Adoption-Programms {#early-adopter}

Wenn Sie diese kommenden Funktionen testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an Ihren Adobe-Kontakt für Customer Success.

### Neuer RTE {#new-rte}

Der neue ProseMirror-RTE mit Seitenauswahl im Link-Dialog ist jetzt im rechten Panel verfügbar. [Dieser RTE bietet flexible Konfigurationsoptionen.](/help/implementing/universal-editor/configure-rte.md)

## Andere Verbesserungen {#other-improvements}

* Das Aktualisierungsereignis wird jetzt darüber informiert, ob die Aktion rückgängig gemacht wurde.
* `No results` Zeichenfolge hängt jetzt vom Browsergebietsschema in universellen Editor-Tags ab.
* Ein zusätzlicher Zeilenumbruch in der Veröffentlichungsschaltfläche des universellen Editors wurde korrigiert.
* Die Bereinigung wurde für die Patch-API durchgeführt.
* Die Schaltfläche „Inhalt auswählen“ ist jetzt in Safari sichtbar.
* RPM-Build wurde korrigiert.
* CORS-Aktualisierung, um zu vermeiden, dass bearbeiteter Text nach dem Speichern erneut aktualisiert wird.
