---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.3.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.3.0
translation-type: tm+mt
source-git-commit: 7059f0868fec3bbc665725c9ad2cc252805d8916
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 16%

---


# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.3.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.3.0.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für Cloud Manager in AEM als Cloud Service 2021.3.0 ist der 11. März 2021.
Die nächste Version ist für den 08. April 2021 geplant.

## Cloud Manager {#cloud-manager}

### Neue Funktionen {#what-is-new}

* Kunden mit Umgebung mit bereits vorhandenen Konfigurationen für benutzerdefinierte Domänennamen für [IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/check-ip-allow-list-status.md#pre-existing-cdn), [SSL-Zertifikate](/help/implementing/cloud-manager/managing-ssl-certifications/check-status-ssl-certificate.md#pre-existing-cdn) und [Benutzerspezifische Domänennamen](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#pre-existing-cdn) erhalten eine Meldung über ihre vorherigen Konfigurationen und können sich über die Benutzeroberfläche selbst versorgen.

* Benutzer mit erforderlichen Berechtigungen können jetzt ein Programm bearbeiten, sodass sie Folgendes selbstständig ausführen können:
   * hinzufügen Sites-Lösung auf ein vorhandenes Programm mit Assets oder umgekehrt.
   * Entfernen Sie Sites oder Assets aus einem vorhandenen Programm mit sowohl Sites als auch Assets.
   * hinzufügen zweite, nicht verwendete Lösungsberechtigung entweder für ein vorhandenes Programm oder als neues Programm.

* **AEM Push-** Aktualisierungsbildschirm wird jetzt sowohl für die Ausführung als auch für die Aktivität der Pipeline angezeigt.

* Wenn eine Umgebung ausgeblendet wird, aber auch ein AEM Update verfügbar ist, hat der Status **Hibernated** Vorrang vor **Update available**.

* Die Benutzer können nun ihre Cloud Manager-Rolle(en) anzeigen, indem sie die Option &quot;Ansicht Cloud Manager-Rolle(en)&quot;wählen, nachdem sie zum Symbol &quot;User Profil&quot;(oben rechts) von Unified Shell navigiert sind.

* Die Beschriftung **Antrag auf Genehmigung** wurde zur besseren Klarheit in **Produktionsgenehmigung** umbenannt.

* Die Beschriftung **Version** wurde im Bildschirm &quot;Produktions-Pipeline-Ausführung&quot;in **Git-Tag** umbenannt.

* Die Beschriftungen, die das Verhalten definieren, wenn wichtige Metriken den definierten Schwellenwert nicht erreichen, wurden umbenannt, um ihr wahres Verhalten widerzuspiegeln: **Sofort abbrechen** und **Sofort genehmigen**.

* Die Listen zum Entfernen von Klassen und Methoden wurden auf der Grundlage der Version `2021.3.4997.20210303T022849Z-210225` des AEM Cloud Service SDK aktualisiert.

* Die Cloud Manager-Produktionspipeline umfasst jetzt die Funktion [Benutzerdefinierte UI-Tests](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing).

### Fehlerbehebungen {#bug-fixes}

* Die Paketversion wurde in einigen Fällen während AEM Push-Aktualisierung übersprungen.

* Einige Qualitätsprobleme wurden nicht richtig erkannt, wenn Pakete in andere Pakete eingebettet wurden.

* In undurchsichtigen Situationen kann der beim Öffnen des Dialogfelds &quot;Hinzufügen Programm&quot;generierte Standardname für das Programm ein Duplikat eines vorhandenen Programms sein.

* Wenn der Benutzer unmittelbar nach dem Start einer Pipeline von der Seite für die Ausführung der Pipeline wegnavigiert, wird gelegentlich eine Fehlermeldung angezeigt, die besagt, dass die Aktion fehlgeschlagen ist, obwohl die Ausführung tatsächlich Beginn ist.

* Der Build-Schritt wurde unnötigerweise neu gestartet, wenn Kundenbuilds zu ungültigen Paketen führten.

* Gelegentlich wird dem Benutzer auch dann ein grüner &quot;aktiver&quot;Status neben einer IP-Zulassungsliste angezeigt, wenn diese Konfiguration nicht bereitgestellt wurde.

* Alle vorhandenen Produktions-Pipelines werden automatisch mit dem Experience Audit-Schritt aktiviert.