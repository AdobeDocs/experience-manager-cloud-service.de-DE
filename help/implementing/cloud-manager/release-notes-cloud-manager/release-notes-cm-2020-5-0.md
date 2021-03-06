---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service Version 2020.5.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service Version 2020.5.0
feature: Release Information
exl-id: 9f534858-d18f-4224-8b94-9583a05aed95
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 100%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2020.5.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2020.5.0.

## Veröffentlichungsdatum {#release-date}

Die Version 2020.5.0 von Cloud Manager in AEM as a Cloud Service wurde am 7. Mai 2020 veröffentlicht.

## Neue Funktionen {#whats-new-cloud-manager}

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
