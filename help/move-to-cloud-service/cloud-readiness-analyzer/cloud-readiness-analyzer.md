---
title: Bewertung der Komplexität des Wechsels zum Cloud-Dienst
description: Bewertung der Komplexität des Wechsels zum Cloud-Dienst
translation-type: tm+mt
source-git-commit: 83f7a1d57fae92e6ce15e4d9d6e00682d4596d05

---


# Bewertung der Komplexität des Wechsels zum Cloud-Dienst {#accesing-complexity}

## Überblick {#overview}

Mit dem Cloud Readiness Analyzer (CRA) können Sie vorhandene AEM-Instanzen auf ihre Bereitschaft überprüfen, zum Cloud-Dienst zu wechseln, indem Sie Muster erkennen, die:

* Verwenden Sie eine AEM 6.x-Funktion, die derzeit nicht vom Cloud-Dienst unterstützt wird

* Verletzung bestimmter Regeln, die vom Wechsel zum Cloud-Dienst betroffen sein werden

>[!NOTE]
>Die Ergebnisse der CRA beschleunigen die Bewertung des Entwicklungsaufwands, der für den Wechsel zum Cloud-Dienst erforderlich ist.

## Einrichten von Cloud Readiness Analyzer {#setting-up-cra}

Die CRA wird als Paket veröffentlicht, das an allen AEM-Quellversionen ab XX und höher arbeitet und einen Umstieg auf den Cloud-Dienst erforscht.

Es ist im Software Distribution Portal verfügbar und kann mit Package Manager installiert werden.

### Verwenden von Cloud Readiness Analyzer {#using-cra}

>[!NOTE]
> CRA kann auf jeder Umgebung ausgeführt werden, einschließlich lokaler Entwicklungsinstanzen.

>[WICHTIG]
>Um jedoch die Erkennungsrate zu erhöhen und eine Verlangsamung bei geschäftskritischen Instanzen zu vermeiden, wird empfohlen, diese auf Staging-Umgebung auszuführen, die den Produktionsbereichen Benutzeranwendungen, Inhalte und Konfigurationen so nahe wie möglich sind

### Anzeigen der Ausgabe in Cloud-Bereitstellungsanalysator {#viewing-output-cra}


1. Navigieren Sie zur AEM Web Console, indem Sie zu **Adobe Experience Manager Web Console Configuration** mit `https://serveraddress:serverport/system/console/configMgr`.

1. Wählen Sie Status - Cloud Readiness Analyzer, wie in der Abbildung unten dargestellt.

1. Sie können die Ausgabe auch über eine reaktive textbasierte oder reguläre JSON-Schnittstelle Ansicht werden.

>[!NOTE]
> Weitere Informationen zu diesen Methoden finden Sie im [Musterdetektor](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html) . Dieser Abschnitt muss hinzugefügt werden, sobald CRA einsatzbereit ist.

## Nächste Schritte zur Cloud-Bereitschaft {#the-next-steps}

Um weitere Informationen über Ihre Bereitschaft zum Cloud-Dienst zu erhalten, muss Adobe die Ausgabe der CRA auswerten.

Gehen Sie wie folgt vor, um die Datei zurückzusenden:

1. Navigieren Sie zur AEM Web Console und laden Sie die xx-Datei herunter, wie in der Abbildung unten dargestellt.

1. Öffnen Sie ein DayCare-Ticket, um die Datei an Adobe zu senden, indem Sie:
   1. Protokollieren eines Support-Tickets in Daycare mit dem Titel &quot; **Cloud Readiness Analyzer Output&quot;**
   1. Anhängen einer Ausgabedatei an das Ticket

