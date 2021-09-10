---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.7.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.7.0
feature: Release Information
source-git-commit: a707968483dc1196628b737ad207bfefe63ca94b
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 64%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.7.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.7.0.

>[!NOTE]
>Klicken Sie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de), um die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service anzuzeigen.

## Veröffentlichungsdatum {#release-date}

Die Version 2021.7.0 von Cloud Manager in AEM as a Cloud Service wurde am 15. Juli 2021 veröffentlicht.
Die nächste Version wird am 12. August 2021 veröffentlicht.

### Neue Funktionen {#what-is-new}

* Kunden können jetzt Azul 8- und 11-JDKs für ihre Cloud Manager-Build-Prozesse verwenden und entweder festlegen, eines dieser JDKs für Toolchain-kompatible Maven-Plug-ins *oder* für die gesamte Maven-Prozessausführung zu verwenden.

* Die ausgehende Austritts-IP wird jetzt in der Protokolldatei des Build-Schritts protokolliert.

* Staging- und Produktionsumgebungen, die alte Versionen von AEM ausführen, melden jetzt den Status **Update Verfügbar**.

* Die maximal unterstützten SSL-Zertifikate wurden auf 20 pro Programm erhöht.

* Die maximale Anzahl der Domänen, die konfiguriert werden können, wurde auf 500 pro Umgebung erhöht.

* Die Schaltfläche **Git verwalten** wurde in **Git-Info öffnen** umbenannt und das Dialogfeld wurde visuell überarbeitet.

* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 28 aktualisiert.

### Fehlerbehebungen {#bug-fixes}

* In einigen Fällen war die Vorschau beim Binden einer IP-Zulassungsliste an eine Umgebung keine verfügbare Option.

* Beim manuellen Navigieren zur Seite mit den Ausführungsdetails für eine nicht vorhandene Ausführung wird nicht mehr ein Bildschirm mit endlosen Ladevorgängen, sondern ein Fehler angezeigt.

* Die Fehlermeldung, die angezeigt wird, wenn die maximale Anzahl von SSL-Zertifikaten erreicht wurde, war nicht hilfreich.

* Unter bestimmten Umständen kann es zu einer Diskrepanz in der Release-Version kommen, die auf der Pipeline-Karte auf der Seite **Übersicht** angezeigt wird.

* Der Assistent Programm hinzufügen hat fälschlicherweise angegeben, dass der Name nach der Erstellung nicht mehr geändert werden kann.

### Bekannte Probleme {#known-issues}

Kunden, die zur Verwendung der Azul-JDKs wechseln, sollten beachten, dass nicht alle vorhandenen Anwendungen ohne Fehler auf Azul-JDK kompiliert werden. Es wird dringend empfohlen, vor dem Wechsel lokal zu testen.

