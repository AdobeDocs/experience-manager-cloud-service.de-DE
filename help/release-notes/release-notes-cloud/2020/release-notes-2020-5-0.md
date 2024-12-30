---
title: Versionshinweise für Adobe Experience Manager as a Cloud Service 2020.5.0
description: '[!DNL Adobe Experience Manager] as a Cloud Service-Versionshinweise für 2020.5.0.'
exl-id: 8570d2c3-6d55-4914-94b2-f5d162e0c285
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 97%

---

# Versionshinweise für AEM as a Cloud Service 2020.5.0 {#release-notes}

Auf dieser Seite werden die allgemeinen Versionshinweise für Experience Manager as a Cloud Service 2020.5.0 beschrieben.

## Veröffentlichungsdatum {#release-date}

Die Version 2020.5.0 von [!DNL Experience Manager] as a Cloud Service wurde am 7. Mai 2020 veröffentlicht.

## Neue Funktionen in AEM Sites {#aem-sites}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und Updates für AEM Sites in Version 2020.5.0 von AEM as a Cloud Service.

* Nach der Stapelverarbeitung von Seitenverschiebungen und Rollouts als asynchrone Aufträge stehen jetzt detaillierte Auftragsinformationen zur Verfügung.
* Beim Kopieren/Einfügen eines Seitenbaums können Sie jetzt auswählen, ob Sie nur die Stammseite oder auch die Unterseiten des Baums einfügen möchten.
* AEM-Experience Fragments, die in Workspaces von Adobe Target exportiert werden, erscheinen nun als einzigartige Angebotstypen und Angebotsquellen in Target.
* MSM – Mit dem *Publish*-Trigger werden nun erfolgreich Löschereignisse für Komponenten in der Live Copy-Quelle implementiert, d. h. das Löschen von Komponenten in einer Live Copy, die in der Live Copy-Quelle gelöscht wurden.
* MSM – Live Copy-Komponenten werden jetzt nach dem Rollout derselben Komponente aus der Live Copy-Quelle in *_msm_moved* umbenannt.


## Neue Funktionen in Cloud Manager {#cloud-manager}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und Updates für Cloud Manager in Version 2020.5.0 von AEM as a Cloud Service.

### Neue Funktionen {#what-is-new}

* Sechs zusätzliche Regeln zur Code-Qualität wurden hinzugefügt, die Kunden bei der Planung einer Migration auf Cloud Service bei der Ermittlung potenzieller Probleme unterstützen.
* Die neue Metrik *Cloud Service-Kompatibilität* wurde hinzugefügt, um die Zahl der Kompatibilitätsprobleme zusammenzufassen.
* Umgebungen, deren Erstellung fehlgeschlagen ist, werden nun ca. 24 Stunden nach der fehlgeschlagenen Erstellung automatisch gelöscht, sofern sie nicht bereits gelöscht worden sind.
* Die Leistung der Seite „Aktivität“ und der Pipeline Execution List-API wurde verbessert.
* Das Code-Qualitätsprotokoll enthält jetzt vollständige Stacktraces für Ausnahmen.

### Fehlerbehebungen  {#bug-fixes}

* Während der Ausführung der Produktions-Pipeline wurde eine irreführende Karte auf der Übersichtsseite angezeigt.
* Die Code-Qualitätsregel *DontImplementOrExtendProviderTypesPomCheck* rief manchmal eine Nullzeiger-Ausnahme hervor.
* Einige Dokumentations-Links auf der Übersichtsseite funktionierten nicht ordnungsgemäß.
* Das Dialogfeld „Umgebung erstellen“ wurde in Safari nicht korrekt dargestellt.
* Auf bestimmten Karten auf der Übersichtsseite wurden die Entitätsnamen nicht korrekt angezeigt.
* In einigen Fällen konnte die Bilderstellung die Kundenpakete nicht erfolgreich herunterladen.
