---
title: Versionshinweise für Cloud Manager 2025.3.0 in Adobe Experience Manager as a Cloud Service
description: Erfahren Sie mehr über die Version Cloud Manager 2025.3.0 in AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 663234640f16e6aa653251399751abf5daa17f82
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 31%

---

# Versionshinweise für Cloud Manager 2025.3.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

Erfahren Sie mehr über die Version Cloud Manager 2025.3.0 in AEM (Adobe Experience Manager) as a Cloud Service.


Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Die Version 2025.3.0 von Cloud Manager in AEM as a Cloud Service wurde am Donnerstag, dem Freitag, 13. März 2025 veröffentlicht.

Die Veröffentlichung der nächsten Version ist für Donnerstag, dem Freitag, 10. April 2025 geplant.

## Neue Funktionen {#what-is-new}

* **Mehrere Pipelines ausführen**

  Die Möglichkeit, mehrere Pipelines gleichzeitig auszuführen, wurde auf der Seite Pipelines eingeführt. Benutzer müssen mindestens eine Pipeline, aber nicht mehr als zehn auswählen. Klicken Sie oben rechts auf der Seite Pipelines auf **Ausgewählte ausführen (x)**. Es wird ein modales Dialogfeld angezeigt, in dem alle Pipelines aufgelistet sind, die nicht gestartet werden können. Klicken Sie **Ausführen**, um alle gültigen Pipelines zu starten.

  ![Dialogfeld „Ausgewählte Pipelines ausführen“](/help/implementing/cloud-manager/release-notes/assets/run-selected-pipelines.png)

  Siehe auch [Mehrere Pipelines ausführen](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#run-multiple-pipelines)

* **Die Unterstützung wurde auf Node.js-Versionen erweitert**

  Die Frontend-Build-Umgebung unterstützt jetzt die folgenden `Node.js`:

   * 23
   * 22
   * 20

  Siehe auch [Entwickeln von Sites mit der Frontend-Pipeline](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md#node-versions). <!-- CMGR-65307 -->

<!--
## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


## Fehlerbehebungen

* **(UI)-Fehlerbehebung für Aktualisierungen der „erweiterten Netzwerkkonfiguration“ in Cloud Manager**

  Ein seltenes Problem, das Aktualisierungen der **erweiterten Netzwerkkonfiguration“**, wenn eine Benachrichtigung „Update verfügbar“ vorhanden war, wurde behoben. Zuvor wurden Konfigurationsänderungen, einschließlich erweiterter Netzwerkeinstellungen, von Cloud Manager gesperrt, um Konflikte während eines Updates zu vermeiden. Kunden können jetzt die ausstehende Aktualisierung manuell mit Triggern versehen, um die erforderlichen Änderungen ohne Einschränkungen anzuwenden. <!-- CMGR-65913 and CMGR-65788 -->

* **(UI)-Fehlerbehebung für Aktualisierungen der IP-Zulassungsliste, die im Status „Wird aktualisiert“ stecken bleiben**

  Ein seltenes Problem, bei dem IP-Konfigurationsaktualisierungen in Cloud Manager aufgrund einer doppelten aktiven Domain-Zulassungsliste für eine Umgebung im Status „Wird aktualisiert“ blieben, wurde behoben. Zuvor kam es bei Kunden zu unbegrenzten Verarbeitungsverzögerungen bei der Aktualisierung von IP-Zulassungslisten, was die erforderlichen Anpassungen des Netzwerkzugriffs verhinderte. Durch diese Fehlerbehebung wird sichergestellt, dass Aktualisierungen der IP-Zulassungsliste jetzt erfolgreich abgeschlossen werden können, ohne hängen zu bleiben. <!-- CMGR-65786 -->




<!-- ## Known issues {#known-issues} -->
