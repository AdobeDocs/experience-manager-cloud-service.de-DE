---
title: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.7.0
description: Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.7.0
feature: Versionshinweise
exl-id: 42cc9cab-6e66-4976-a3b1-ecb9dbaaabf4
source-git-commit: 06dca3b3e94b27f592681e661cd5c9883c0f6422
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 19%

---

# Versionshinweise für Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.7.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.7.0.

>[!NOTE]
>Um die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service anzuzeigen, klicken Sie auf [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Die Version 2021.7.0 von Cloud Manager in AEM as a Cloud Service wurde am 15. Juli 2021 veröffentlicht.
Die nächste Version ist für den 12. August 2021 geplant.

### Neue Funktionen {#what-is-new}

* Kunden können jetzt Azul 8- und 11-JDKs für ihre Cloud Manager-Build-Prozesse verwenden und entweder festlegen, eines dieser JDKs für toolchain-kompatible Maven-Plug-ins *oder* für die gesamte Maven-Prozessausführung zu verwenden.

* Die ausgehende Ausgangs-IP wird jetzt in der Protokolldatei des Buildschritts protokolliert.

* Staging- und Produktionsumgebungen, die alte Versionen von AEM ausführen, melden jetzt den Status &quot;Update verfügbar&quot;.

* Die maximal unterstützten SSL-Zertifikate wurden auf 20 pro Programm erhöht.

* Erhöhen Die maximale Anzahl der Domänen, die konfiguriert werden können, wurde auf 500 pro Umgebung erhöht.

* Die Schaltflächen Git verwalten wurden eingestellt und das Dialogfeld Git-Informationen wurde visuell aktualisiert.

### Fehlerbehebungen {#bug-fixes}

* In einigen Fällen war die Vorschau keine verfügbare Option beim Binden einer IP-Zulassungsliste an eine Umgebung.

* Beim manuellen Navigieren zur Seite mit den Ausführungsdetails für eine nicht vorhandene Ausführung wurde kein Fehler angezeigt, sondern nur ein Bildschirm mit endlosen Ladevorgängen.

* Die Fehlermeldung, die angezeigt wird, wenn die maximale Anzahl von SSL-Zertifikaten erreicht wurde, war nicht hilfreich.

* Unter bestimmten Umständen kann es zu einer Diskrepanz in der Release-Version kommen, die auf der Pipeline-Karte auf der Übersichtsseite angezeigt wird.

* Der Assistent Programm hinzufügen hat fälschlicherweise angegeben, dass der Name nach der Erstellung nicht mehr geändert werden kann.

* In einigen Fällen war die Vorschau keine verfügbare Option beim Binden einer IP-Zulassungsliste an eine Umgebung.

### Bekannte Probleme {#known-issues}

Kunden, die zur Verwendung der Azul JDKs wechseln, sollten beachten, dass nicht alle vorhandenen Anwendungen ohne Fehler auf Azul JDK kompiliert werden. Es wird dringend empfohlen, vor dem Wechsel lokal zu testen.

