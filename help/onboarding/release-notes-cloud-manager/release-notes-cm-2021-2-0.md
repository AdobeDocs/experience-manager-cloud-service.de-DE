---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.2.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.2.0
exl-id: 281f9523-dec2-44f1-9459-5a45d48489d9
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 100%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.2.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.2.0.

## Veröffentlichungsdatum {#release-date}

Die Version 2021.2.0 von Cloud Manager in AEM as a Cloud Service wurde am 11. Februar 2021 veröffentlicht.

## Cloud Manager {#cloud-manager}

### Neue Funktionen {#what-is-new}

* Assets-Kunden können jetzt selbst entscheiden, wann und wo sie ihre Brand Portal-Instanz über die Cloud Manager-Benutzeroberfläche bereitstellen möchten. Für ein reguläres (nicht Sandbox-)Programm mit Assets-Lösung kann Brand Portal jetzt in der Produktionsumgebung bereitgestellt werden. Die Bereitstellung kann nur einmal in der Produktionsumgebung durchgeführt werden.

* Der AEM-Projektarchetyp, der bei der Projekt- und Sandbox-Erstellung verwendet wird, wurde auf Version 25 aktualisiert.

* Die Liste der veralteten APIs, die beim Code-Scanning identifiziert wurden, wurde verfeinert und enthält nun zusätzliche Klassen und Methoden, die in den neuesten Cloud Service SDK-Versionen nicht mehr unterstützt werden.

* Das SonarQube-Profil für Cloud Manager wurde aktualisiert, um die Sonar-Regel squid:S2142 zu entfernen. Diese führt nicht mehr zu Konflikten mit Thread-Unterbrechungsprüfungen.

* Die Cloud Manager-Benutzeroberfläche informiert den Benutzer, der möglicherweise vorübergehend keinen Domain-Namen hinzufügen/aktualisieren kann, weil der zugehörigen Umgebung entweder eine laufende Pipeline angehängt ist oder sie sich derzeit im Schritt „Warten auf die Genehmigung“ befindet.

* Eigenschaften, die in den `pom.xml`-Dateien des Kunden mit dem Präfix „sonar“ festgelegt wurden, werden jetzt dynamisch entfernt, um Fehler beim Build und beim Scannen der Qualität zu vermeiden.

* Die Cloud Manager-Benutzeroberfläche informiert den Benutzer, der möglicherweise vorübergehend ein SSL-Zertifikat nicht auswählen kann, wenn es von einem Domain-Namen verwendet wird, der gerade bereitgestellt wird.

* Es wurden zusätzliche Regeln zur Code-Qualität hinzugefügt, um Probleme mit der Kompatibilität von Cloud Services abzudecken.

### Fehlerbehebungen {#bug-fixes}

* Beim Abgleichen des SSL-Zertifikats mit einem Domain-Namen wird nicht mehr zwischen Groß- und Kleinschreibung unterschieden.

* Die Cloud Manager-Benutzeroberfläche informiert jetzt einen Benutzer mit einer entsprechenden Fehlermeldung, wenn die privaten Schlüssel des Zertifikats nicht dem 2048-Bit-Limit entsprechen.

* Die Cloud Manager-Benutzeroberfläche informiert den Benutzer, der möglicherweise vorübergehend ein SSL-Zertifikat nicht auswählen kann, wenn es von einem Domain-Namen verwendet wird, der gerade bereitgestellt wird.

* In einigen Fällen kann ein internes Problem dazu führen, dass der Löschvorgang der Umgebung stecken bleibt.

* Einige Pipeline-Ausfälle wurden fälschlicherweise als Pipeline-Fehler gemeldet.
