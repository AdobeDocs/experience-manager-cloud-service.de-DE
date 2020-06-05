---
title: Versionshinweise für Adobe Experience Manager as a Cloud Service 2020.5.0
description: Versionshinweise für Experience Manager 2020.5.0
translation-type: tm+mt
source-git-commit: 06a56b0ca8000a41fe4e492206459b1525aae59d
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 49%

---


# Versionshinweise für AEM as a Cloud Service 2020.5.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager as a Cloud Service 2020.5.0 beschrieben.

## Veröffentlichungsdatum {#release-date}

The release date for [!DNL Experience Manager] as a Cloud Service 2020.5.0 is May 07, 2020.

## What&#39;s New in AEM Sites {#aem-sites}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für AEM-Sites in AEM als Cloud-Service-Version 2020.5.0.

* Detaillierte Auftragsinformationen sind jetzt verfügbar, nachdem Massenvorgänge und Rollover als asynchrone Aufträge verarbeitet wurden.
* Beim Kopieren/Einfügen eines Seitenbaums bieten Sie jetzt an, zwischen dem Einfügen nur der Stammseite oder auch der Unterseiten des Baums zu wählen.
* AEM Experience Fragments, die in Adobe Zielgruppe-Arbeitsbereiche exportiert wurden, werden jetzt als eindeutige Angebot- und Angebot-Quellen in der Zielgruppe angezeigt.
* MSM - Mit *Veröffentlichungs* -Trigger werden nun Löschkomponenten für Komponenten in Live-Kopierquellen erfolgreich entfernt, d. h., Ereignis in einer Live-Kopie, die in Live-Kopierquellen gelöscht wurden, werden gelöscht.
* MSM - Live-Copy-Komponenten werden jetzt nach dem Rollout derselben Komponente aus der Live-Kopierquelle in *_msm_move* umbenannt.


## Neue Funktionen in Cloud Manager {#cloud-manager}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und Updates für Cloud Manager in Version 2020.5.0 von AEM as a Cloud Service.

### Neuerungen {#what-is-new}

* Sechs zusätzliche Regeln zur Code-Qualität wurden hinzugefügt, die Kunden bei der Planung einer Migration auf Cloud Service bei der Ermittlung potenzieller Probleme unterstützen.
* Die neue Metrik *Cloud Service-Kompatibilität* wurde hinzugefügt, um die Zahl der Kompatibilitätsprobleme zusammenzufassen.
* Umgebung, die nicht erstellt werden konnten, werden nun ca. 24 Stunden nach dem Erstellungsfehler automatisch gelöscht, es sei denn, sie wurden bereits gelöscht.
* Die Leistung der Seite „Aktivität“ und der Pipeline Execution List-API wurde verbessert.
* Das Code-Qualitätsprotokoll enthält jetzt vollständige Stacktraces für Ausnahmen.

### Fehlerbehebungen {#bug-fixes}

* Während der Ausführung der Produktions-Pipeline wurde eine irreführende Karte auf der Übersichtsseite angezeigt.
* Die Code-Qualitätsregel *DontImplementOrExtendProviderTypesPomCheck* rief manchmal eine Nullzeiger-Ausnahme hervor.
* Einige Dokumentations-Links auf der Übersichtsseite funktionierten nicht ordnungsgemäß.
* Das Dialogfeld &quot;Umgebung erstellen&quot;wurde in Safari nicht korrekt dargestellt.
* Auf bestimmten Karten auf der Übersichtsseite wurden die Entitätsnamen nicht korrekt angezeigt.
* In einigen Fällen kann das Build Image nicht erfolgreich vom Kunden heruntergeladen werden.


