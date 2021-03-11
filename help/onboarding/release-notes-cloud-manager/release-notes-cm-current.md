---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.3.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.3.0
translation-type: tm+mt
source-git-commit: 238ce5ea4327947694851bd0fae5be84614501c9
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 18%

---


# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.3.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.3.0.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für Cloud Manager in AEM als Cloud Service 2021.3.0 ist der 11. März 2021.

## Cloud Manager {#cloud-manager}

### Neue Funktionen {#what-is-new}

* Kunden mit Umgebung mit bereits vorhandenen CDN-Konfigurationen für IP-Auf die Zulassungsliste setzte, SSL-Zertifikate und benutzerdefinierte Domänennamen sehen die folgende Meldung und können sich über die Benutzeroberfläche selbst bedienen.

* Benutzer mit entsprechender Berechtigung können jetzt Programm bearbeiten, sodass sie Folgendes selbstständig ausführen können.

* AEM &quot;Push Update&quot;-Beschriftung wird jetzt sowohl für die Ausführung als auch für die Aktivität der Pipeline angezeigt.

* Wenn eine Umgebung ausgeblendet wird, aber auch ein AEM Update verfügbar ist, hat der Status &quot;Hibernated&quot;Vorrang vor &quot;Update available&quot;.

* Die Benutzer können nun ihre Cloud Manager-Rolle(en) anzeigen, indem sie die Option &quot;Ansicht Cloud Manager-Rolle(en)&quot;wählen, nachdem sie zum Symbol &quot;User Profil&quot;(oben rechts) von Unified Shell navigiert sind.

* Das Etikett &quot;Antrag auf Genehmigung&quot;wurde aus Gründen der Klarheit in &quot;Genehmigung für die Produktion&quot;umbenannt.

* Das Etikett &quot;Version&quot;wurde im Produktionsbildschirm in &quot;Git-Tag&quot;umbenannt.

* Die Beschriftungen, die das Verhalten definieren, wenn wichtige Metriken den definierten Schwellenwert nicht erreichen, wurden umbenannt, um ihr wahres Verhalten widerzuspiegeln - Sofort abbrechen und Sofort genehmigen.

* Die Listen zum Entfernen von Klassen und Methoden wurden auf der Grundlage der Version `2021.3.4997.20210303T022849Z-210225` des AEM Cloud Service SDK aktualisiert.

* Die Cloud Manager-Produktionspipeline umfasst jetzt benutzerdefinierte Testfunktionen für die Benutzeroberfläche.

### Fehlerbehebungen {#bug-fixes}

* Die Paketversion wurde in einigen Fällen während AEM Push-Aktualisierung übersprungen.

* Einige Qualitätsprobleme wurden nicht richtig erkannt, wenn Pakete in andere Pakete eingebettet wurden.

* In undurchsichtigen Situationen kann der beim Öffnen des Dialogfelds &quot;Hinzufügen Programm&quot;generierte Standardname für das Programm ein Duplikat eines vorhandenen Programms sein.

* Wenn der Benutzer unmittelbar nach dem Start einer Pipeline von der Seite für die Ausführung der Pipeline wegnavigiert, wird gelegentlich eine Fehlermeldung angezeigt, die besagt, dass die Aktion fehlgeschlagen ist, obwohl die Ausführung tatsächlich Beginn ist.

* Der Build-Schritt wurde unnötigerweise neu gestartet, wenn Kundenbuilds zu ungültigen Paketen führten.

* Gelegentlich wird dem Benutzer auch dann ein grüner &quot;aktiver&quot;Status neben einer IP-Zulassungsliste angezeigt, wenn diese Konfiguration nicht bereitgestellt wurde.

* Alle vorhandenen Produktions-Pipelines werden automatisch mit dem Experience Audit-Schritt aktiviert.