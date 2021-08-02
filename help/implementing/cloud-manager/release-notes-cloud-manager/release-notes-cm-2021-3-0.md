---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.3.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.3.0
feature: Versionshinweise
exl-id: 42cc9cab-6e66-4976-a3b1-ecb9dbaaabf4
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 85%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.3.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.3.0.

## Veröffentlichungsdatum {#release-date}

Die Version 2021.3.0 von Cloud Manager in AEM as a Cloud Service wurde am 11. März 2021 veröffentlicht.

## Cloud Manager {#cloud-manager}

### Neue Funktionen {#what-is-new}

* Kunden mit Umgebungen mit bereits bestehenden Konfigurationen für benutzerdefinierte Domain-Namen für [IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md#pre-existing-cdn), [SSL-Zertifikate](/help/implementing/cloud-manager/managing-ssl-certifications/check-status-ssl-certificate.md#pre-existing-cdn) und [benutzerdefinierte Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) erhalten eine Meldung über ihre bereits bestehenden Konfigurationen und können diese über die Benutzeroberfläche selbst verwalten.

* Benutzer mit den erforderlichen Berechtigungen können jetzt ein Programm bearbeiten, sodass sie Folgendes selbstständig ausführen können:
   * Fügen Sie Sites-Lösungen zu einem vorhandenen Programm mit Assets hinzu oder umgekehrt.
   * Entfernen Sie Sites oder Assets aus einem vorhandenen Programm mit sowohl Sites als auch Assets.
   * Hinzufügen einer zweiten, nicht verwendeten Lösungsberechtigung entweder für ein vorhandenes Programm oder als neues Programm.

* Die Bezeichnung **AEM-Push-Updates** wird jetzt sowohl für die Bildschirme Pipeline-Ausführung als auch Aktivität angezeigt.

* Wenn eine Umgebung in den Ruhezustand versetzt wurde, aber auch ein AEM-Update verfügbar ist, hat der Status **Ruhezustand** Vorrang vor **Update verfügbar**.

* Die Benutzer können nun ihre Cloud Manager-Rolle(n) anzeigen, indem sie die Option „Cloud Manager-Rolle(n) anzeigen“ auswählen, nachdem sie zum Symbol „Benutzerprofil“ (oben rechts) der Unified Shell navigiert sind.

* Die Bezeichnung **Antrag auf Genehmigung** wurde aus Gründen der Klarheit in **Produktionsgenehmigung** umbenannt.

* Die Beschriftung **Version** wurde im Bildschirm zur Ausführung der Produktions-Pipeline in **Git-Tag** umbenannt.

* Die Bezeichnungen, die das Verhalten definieren, wenn wichtige Metriken den definierten Schwellenwert nicht erreichen, wurden umbenannt, um ihr tatsächliches Verhalten widerzuspiegeln: **Sofort abbrechen** und **Sofort genehmigen**.

* Die Listen veralteter Klassen und Methoden wurden auf Grundlage von Version `2021.3.4997.20210303T022849Z-210225` des AEM Cloud Service SDK aktualisiert.

* Die Cloud Manager-Produktions-Pipeline enthält jetzt die Funktion [Benutzerdefinierte UI-Tests](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing).

### Fehlerbehebungen  {#bug-fixes}

* Die Paketversionierung wurde in einigen Fällen während AEM-Push-Aktualisierung übersprungen.

* Einige Qualitätsprobleme wurden nicht richtig erkannt, wenn Pakete in andere Pakete eingebettet wurden.

* In unklaren Situationen kann der Standardprogrammname, der beim Öffnen des Dialogfelds „Programm hinzufügen“ generiert wird, ein Duplikat eines vorhandenen Programmnamens sein.

* Wenn der Benutzer unmittelbar nach dem Start einer Pipeline von der Seite für die Pipeline-Ausführung weg navigiert, wird gelegentlich eine Fehlermeldung angezeigt, die besagt, dass die Aktion fehlgeschlagen ist, obwohl die Ausführung tatsächlich startet.

* Der Build-Schritt wurde unnötigerweise neu gestartet, wenn Kunden-Builds zu ungültigen Paketen führten.

* Gelegentlich wird dem Benutzer neben einer IP-Zulassungsliste möglicherweise ein grüner „aktiver“ Status angezeigt, auch wenn diese Konfiguration nicht bereitgestellt wurde.

* Alle vorhandenen Produktions-Pipelines werden automatisch mit dem Experience Audit-Schritt aktiviert.
