---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.2.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.2.0
translation-type: tm+mt
source-git-commit: 3bf7defc9aa36c831e061e7209a765f2d60cfb33
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 19%

---


# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.2.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.2.0.

## Veröffentlichungsdatum {#release-date}

Die Version 2021.2.0 von Cloud Manager in AEM as a Cloud Service wurde am 11. Februar 2021 veröffentlicht.

## Cloud Manager {#cloud-manager}

### Neue Funktionen {#what-is-new}

* Die Cloud Manager-Produktionspipeline umfasst jetzt benutzerdefinierte Testfunktionen für die Benutzeroberfläche.

* Assets, die Kunden jetzt über die Benutzeroberfläche von Cloud Manager auswählen können, wann und wo sie ihre Brand Portal-Instanz auf Self-Service-Weise bereitstellen. Für ein normales (nicht Sandbox-)Programm mit Assets-Lösung kann nun das Markenportal auf der Umgebung Produktion bereitgestellt werden. Die Bereitstellung kann nur einmal auf der Produktions-Umgebung erfolgen.

* Der AEM Projektarchiv, der in Project und Sandbox Creation verwendet wird, wurde auf Version 25 aktualisiert.

* Die Liste veralteter APIs, die während der Codeprüfung identifiziert wurden, wurde optimiert und enthält nun weitere Klassen und Methoden, die in den neuesten Cloud Service SDK-Versionen nicht mehr unterstützt werden.

* SonarQube-Profil für Cloud Manager aktualisiert, um die Sonar-Regel squid:S2142 zu entfernen. Dies steht nicht mehr im Konflikt mit Thread-Unterbrechungsprüfungen.

* Die Benutzeroberfläche von Cloud Manager informiert den Benutzer, der vorübergehend keinen Domänennamen hinzufügen/aktualisieren kann, da an der zugehörigen Umgebung entweder eine laufende Pipeline angehängt ist oder derzeit auf den Genehmigungsvorgang wartet.

* Eigenschaften, die in benutzerdefinierten Dateien mit dem Präfix &quot;sonar&quot;festgelegt sind, werden nun dynamisch entfernt, um Fehler beim Erstellen und Überprüfen von Qualität zu vermeiden.`pom.xml`

* Die Benutzeroberfläche von Cloud Manager informiert den Benutzer, der vorübergehend kein SSL-Zertifikat auswählen kann, wenn es von einem Domänennamen verwendet wird, der derzeit bereitgestellt wird.


### Fehlerbehebungen {#bug-fixes}

* Beim Abgleichen des SSL-Zertifikats mit einem Domänennamen wird nicht mehr zwischen Groß- und Kleinschreibung unterschieden.

* Die Benutzeroberfläche von Cloud Manager informiert nun einen Benutzer, wenn die privaten Schlüssel des Zertifikats die 2048-Bit-Grenze nicht erfüllen, und gibt eine entsprechende Fehlermeldung aus.

* Die Benutzeroberfläche von Cloud Manager informiert den Benutzer, der vorübergehend kein SSL-Zertifikat auswählen kann, wenn es von einem Domänennamen verwendet wird, der derzeit bereitgestellt wird.

* In einigen Fällen kann ein internes Problem dazu führen, dass der Löschvorgang der Umgebung blockiert wird.

* Einige Pipeline-Fehler wurden fälschlicherweise als Pipeline-Fehler gemeldet.
