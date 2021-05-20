---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.3.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.3.0
feature: Versionshinweise
exl-id: 42cc9cab-6e66-4976-a3b1-ecb9dbaaabf4
source-git-commit: 84a97f09402602df33c8f0494feed57fdb510add
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 16%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.3.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.3.0.

## Veröffentlichungsdatum {#release-date}

Die Version 2021.3.0 von Cloud Manager in AEM as a Cloud Service wurde am 11. März 2021 veröffentlicht.

## Cloud Manager {#cloud-manager}

### Neue Funktionen {#what-is-new}

* Kunden mit Umgebungen mit bereits vorhandenen Konfigurationen für benutzerdefinierte Domänennamen für [IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md#pre-existing-cdn), [SSL-Zertifikate](/help/implementing/cloud-manager/managing-ssl-certifications/check-status-ssl-certificate.md#pre-existing-cdn) und [Benutzerdefinierte Domänennamen](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) sehen eine Meldung über ihre bisherigen Konfigurationen und können über die Benutzeroberfläche selbst versorgen.

* Benutzer mit den erforderlichen Berechtigungen können jetzt ein Programm bearbeiten, sodass sie Folgendes selbstständig erledigen können:
   * Fügen Sie Sites-Lösungen zu einem vorhandenen Programm mit Assets hinzu oder umgekehrt.
   * Entfernen Sie Sites oder Assets aus einem vorhandenen Programm mit sowohl Sites als auch Assets.
   * Fügen Sie eine zweite, nicht verwendete Lösungsberechtigung hinzu, entweder zu einem vorhandenen Programm oder als neues Programm.

* **AEM** Aktualisierungsfeld Push wird jetzt sowohl für die Pipelineausführung als auch für die Aktivitätsbildschirme angezeigt.

* Wenn eine Umgebung in den Ruhezustand versetzt wird, aber auch eine AEM Aktualisierung verfügbar ist, hat der Status **Ruhezustand** Vorrang vor **Update verfügbar**.

* Benutzer können nun ihre Cloud Manager-Rollen sehen, indem sie die Option &quot;Cloud Manager-Rolle(n) anzeigen&quot;auswählen, nachdem sie zum Benutzerprofilsymbol (oben rechts) von Unified Shell navigiert sind.

* Der Titel **Antrag auf Genehmigung** wurde zur besseren Übersichtlichkeit in **Produktionsgenehmigung** umbenannt.

* Der Titel **Version** wurde im Bildschirm zur Ausführung der Produktions-Pipeline in **Git-Tag** umbenannt.

* Die Bezeichnungen, die das Verhalten definieren, wenn wichtige Metriken den definierten Schwellenwert nicht erreichen, wurden umbenannt, um ihr tatsächliches Verhalten widerzuspiegeln: **Sofort abbrechen** und **Sofort genehmigen**.

* Die Listen zur veralteten Klasse und Methode wurden basierend auf der Version `2021.3.4997.20210303T022849Z-210225` des AEM Cloud Service SDK aktualisiert.

* Die Cloud Manager-Produktions-Pipeline enthält jetzt die Funktion [Benutzerdefinierte UI-Tests](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing).

### Fehlerbehebungen {#bug-fixes}

* Die Paketversionierung wurde in einigen Fällen während AEM Push-Upgrades übersprungen.

* Einige Qualitätsprobleme wurden nicht richtig erkannt, wenn Pakete in andere Pakete eingebettet wurden.

* In undurchsichtigen Situationen kann der beim Öffnen des Dialogfelds Programm hinzufügen generierte Standard-Programmname ein Duplikat eines vorhandenen Programmnamens sein.

* Wenn der Benutzer die Pipeline-Ausführungsseite gelegentlich unmittelbar nach dem Start einer Pipeline verlässt, wird eine Fehlermeldung angezeigt, die besagt, dass die Aktion fehlgeschlagen ist, obwohl die Ausführung tatsächlich gestartet wird.

* Der Build-Schritt wurde unnötigerweise neu gestartet, wenn Kunden-Builds zu ungültigen Paketen führten.

* Gelegentlich kann der Benutzer einen grünen &quot;aktiven&quot;Status neben einer IP-Zulassungsliste sehen, selbst wenn diese Konfiguration nicht bereitgestellt wurde.

* Alle vorhandenen Produktions-Pipelines werden automatisch mit dem Experience Audit-Schritt aktiviert.
