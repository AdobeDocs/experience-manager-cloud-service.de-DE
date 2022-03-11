---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.3.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.3.0
feature: Release Information
exl-id: f826e0c6-3b1d-44f5-99a2-f792f5df3a55
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 100%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.3.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.3.0.

## Veröffentlichungsdatum {#release-date}

Die Version 2021.3.0 von Cloud Manager in AEM as a Cloud Service wurde am 11. März 2021 veröffentlicht.

## Cloud Manager {#cloud-manager}

### Neue Funktionen {#what-is-new}

* Kunden mit Umgebungen mit bereits bestehenden Konfigurationen für benutzerdefinierte Domain-Namen für [IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md#pre-existing-cdn), [SSL-Zertifikate](/help/implementing/cloud-manager/managing-ssl-certifications/check-status-ssl-certificate.md#pre-existing-cdn) und [benutzerdefinierte Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) erhalten eine Meldung über ihre bereits bestehenden Konfigurationen und können diese über die Benutzeroberfläche selbst verwalten.

* Benutzer mit den erforderlichen Berechtigungen können jetzt ein Programm bearbeiten, sodass sie Folgendes selbstständig ausführen können:
   * Hinzufügen der Sites-Lösung zu einem vorhandenen Programm mit Assets oder umgekehrt.
   * Entfernen von Sites oder Assets aus einem vorhandenen Programm, das sowohl Sites als auch Assets umfasst.
   * Hinzufügen einer zweiten, nicht verwendeten Lösungsberechtigung entweder für ein vorhandenes Programm oder als neues Programm.

* Die Bezeichnung **AEM-Push-Updates** wird jetzt sowohl für die Bildschirme „Pipeline-Ausführung“ als auch „Aktivität“ angezeigt.

* Wenn eine Umgebung in den Ruhezustand versetzt wurde, aber auch ein AEM-Update verfügbar ist, hat der Status **Ruhezustand** Vorrang vor **Update verfügbar**.

* Die Benutzer können nun ihre Cloud Manager-Rolle(n) anzeigen, indem sie die Option „Cloud Manager-Rolle(n) anzeigen“ auswählen, nachdem sie zum Symbol „Benutzerprofil“ (oben rechts) der Unified Shell navigiert sind.

* Die Bezeichnung **Antrag auf Genehmigung** wurde aus Gründen der Klarheit in **Produktionsgenehmigung** umbenannt.

* Die Beschriftung **Version** wurde im Bildschirm zur Ausführung der Produktions-Pipeline in **Git-Tag** umbenannt.

* Die Bezeichnungen, die das Verhalten definieren, wenn wichtige Metriken den definierten Schwellenwert nicht erreichen, wurden neu beschriftet, um ihr wahres Verhalten widerzuspiegeln: **Sofort abbrechen** und **Sofort genehmigen**.

* Die Listen zum Entfernen von Klassen und Methoden wurden auf der Grundlage der Version `2021.3.4997.20210303T022849Z-210225` des AEM Cloud Service SDK aktualisiert.

* Die Cloud Manager-Produktions-Pipeline umfasst jetzt [Testfunktionen für die benutzerdefinierte Benutzeroberflächen](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing).

### Fehlerbehebungen  {#bug-fixes}

* Die Paketversionierung wurde in einigen Fällen während AEM-Push-Aktualisierung übersprungen.

* Einige Qualitätsprobleme wurden nicht richtig erkannt, wenn Pakete in andere Pakete eingebettet wurden.

* In unklaren Situationen kann der Standardprogrammname, der beim Öffnen des Dialogfelds „Programm hinzufügen“ generiert wird, ein Duplikat eines vorhandenen Programmnamens sein.

* Wenn der Benutzer unmittelbar nach dem Start einer Pipeline von der Seite für die Pipeline-Ausführung weg navigiert, wird gelegentlich eine Fehlermeldung angezeigt, die besagt, dass die Aktion fehlgeschlagen ist, obwohl die Ausführung tatsächlich startet.

* Der Build-Schritt wurde unnötigerweise neu gestartet, wenn Kunden-Builds zu ungültigen Paketen führten.

* Gelegentlich wird dem Benutzer neben einer IP-Zulassungsliste möglicherweise ein grüner „aktiver“ Status angezeigt, auch wenn diese Konfiguration nicht bereitgestellt wurde.

* Alle vorhandenen Produktions-Pipelines werden automatisch mit dem Experience Audit-Schritt aktiviert.
