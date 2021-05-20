---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.2.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.2.0
exl-id: 281f9523-dec2-44f1-9459-5a45d48489d9
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 19%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.2.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.2.0.

## Veröffentlichungsdatum {#release-date}

Die Version 2021.2.0 von Cloud Manager in AEM as a Cloud Service wurde am 11. Februar 2021 veröffentlicht.

## Cloud Manager {#cloud-manager}

### Neue Funktionen {#what-is-new}

* Assets-Kunden können jetzt über die Cloud Manager-Benutzeroberfläche festlegen, wann und wo sie ihre Brand Portal-Instanz auf Self-Service-Weise bereitstellen. Für ein reguläres (Nicht-Sandbox-)Programm mit Assets-Lösung kann Brand Portal jetzt in der Produktionsumgebung bereitgestellt werden. Die Bereitstellung kann nur einmal in der Produktionsumgebung erfolgen.

* Der AEM Projektarchetyp, der bei der Projekt- und Sandbox-Erstellung verwendet wird, wurde auf Version 25 aktualisiert.

* Die Liste veralteter APIs, die beim Codescan identifiziert werden, wurde verfeinert und enthält jetzt zusätzliche Klassen und Methoden, die in den neuesten Cloud Service SDK-Versionen nicht mehr unterstützt werden.

* Das SonarQube-Profil für Cloud Manager wurde aktualisiert, um die Sonar-Regel squid:S2142 zu entfernen. Dies steht nicht mehr in Konflikt mit den Thread-Unterbrechungsprüfungen.

* Die Cloud Manager-Benutzeroberfläche informiert den Benutzer, der vorübergehend nicht in der Lage ist, den Domänennamen hinzuzufügen/zu aktualisieren, da der zugehörigen Umgebung entweder eine laufende Pipeline angehängt ist oder sich derzeit auf den Genehmigungsschritt wartet.

* Eigenschaften, die in kundenspezifischen `pom.xml` -Dateien mit dem Präfix sonar festgelegt sind, werden jetzt dynamisch entfernt, um Fehler bei der Build- und Qualitätsprüfung zu vermeiden.

* Die Benutzeroberfläche von Cloud Manager informiert den Benutzer, der möglicherweise vorübergehend kein SSL-Zertifikat auswählen kann, wenn dieses von einem Domänennamen verwendet wird, der derzeit bereitgestellt wird.

* Es wurden zusätzliche Regeln für die Codequalität hinzugefügt, um Probleme mit der Kompatibilität von Cloud Services abzudecken.

### Fehlerbehebungen {#bug-fixes}

* Beim Abgleichen des SSL-Zertifikats mit einem Domänennamen wird nicht mehr zwischen Groß- und Kleinschreibung unterschieden.

* Die Benutzeroberfläche von Cloud Manager informiert Benutzer jetzt darüber, ob die privaten Zertifikatschlüssel die 2048-Bit-Grenze nicht mit einer entsprechenden Fehlermeldung erfüllen.

* Die Benutzeroberfläche von Cloud Manager informiert den Benutzer, der möglicherweise vorübergehend kein SSL-Zertifikat auswählen kann, wenn es von einem Domänennamen verwendet wird, der derzeit bereitgestellt wird.

* In einigen Fällen kann ein internes Problem dazu führen, dass der Löschvorgang der Umgebung blockiert wird.

* Einige Pipeline-Fehler wurden fälschlicherweise als Pipeline-Fehler gemeldet.
