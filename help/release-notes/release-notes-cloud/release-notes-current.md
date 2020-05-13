---
title: Versionshinweise für Adobe Experience Manager as a Cloud Service 2020.5.0
description: Versionshinweise für Experience Manager 2020.5.0
translation-type: tm+mt
source-git-commit: 94a732f56929ad4af23855152e258f82ad61ee2c
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 29%

---


# Versionshinweise für AEM as a Cloud Service 2020.5.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager as a Cloud Service 2020.5.0 beschrieben.

## Cloud Manager {#cloud-manager}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und Updates für Cloud Manager in Version 2020.5.0 von AEM as a Cloud Service.

### Neuerungen {#what-is-new}

* Es wurden sechs zusätzliche Regeln zur Codequalität hinzugefügt, die Kunden bei der Planung einer Migration auf den Cloud-Dienst bei der Ermittlung potenzieller Probleme unterstützen.
* Eine neue Metrik *Cloud-Dienstkompatibilität* wurde hinzugefügt, um die Anzahl der Kompatibilitätsprobleme zusammenzufassen.
* Umgebung, die nicht erstellt werden konnten, werden nun ca. 24 Stunden nach dem Erstellungsfehler automatisch gelöscht, es sei denn, sie wurden bereits gelöscht.
* Die Leistung der Aktivität-Seite und der Pipeline Execution Liste API wurde verbessert.
* Das Codequalitätsprotokoll enthält jetzt vollständige Stapelspuren für Ausnahmen.

### Fehlerbehebungen {#bug-fixes}

* Während der Ausführung der Produktionsleitung wurde eine irreführende Karte auf der Übersichtsseite angezeigt.
* Die *Code-Qualitätsregel DontImplementOrExtendProviderTypesPomCheck* kann manchmal eine Null-Zeiger-Ausnahme hervorrufen.
* Einige Links zur Dokumentation auf der Übersichtsseite funktionierten nicht ordnungsgemäß.
* Das Dialogfeld &quot;Umgebung erstellen&quot;wurde in Safari nicht korrekt dargestellt.
* Auf bestimmten Karten auf der Übersichtsseite wurden die Entitätsnamen nicht korrekt angezeigt.
* In einigen Fällen kann das Build Image nicht erfolgreich vom Kunden heruntergeladen werden.

