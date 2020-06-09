---
title: Verwenden von Cloud Readiness Analyzer
description: Verwenden von Cloud Readiness Analyzer
translation-type: tm+mt
source-git-commit: 317dd08600df9c7127cf8502341f93758ac8ce0b
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 1%

---


# Verwenden von Cloud Readiness Analyzer {#using-cloud-readiness-analyzer}

## Wichtige Überlegungen zur Verwendung von Cloud Readiness Analyzer {#imp-considerations}

Gehen Sie wie folgt vor, um die wichtigen Überlegungen beim Ausführen des Cloud Readiness Analyzer (CRA) zu verstehen:

* CRA wird auf AEM-Quellinstanzen mit Version 6.1 und höher unterstützt.
* CRA kann auf jeder Umgebung ausgeführt werden. Um die Erkennungsrate zu erhöhen und eine Verlangsamung bei geschäftskritischen Instanzen zu vermeiden, wird jedoch empfohlen, diese auf den Staging-Umgebung des Quellautors auszuführen, die den Produktionsbereichen Anpassungen, Konfigurationen, Inhalts- und Benutzeranwendungen so nahe wie möglich sind. Alternativ kann es auch auf einem Klon der Publish-Umgebung ausgeführt werden.

## Verfügbarkeit {#availability}

Der Cloud Readiness Analyzer (CRA) kann als ZIP-Datei vom Software Distribution Portal heruntergeladen werden. Sie können das Paket über Package Manager auf der Quell-Instanz von Adobe Experience Manager (AEM) installieren.

>[!NOTE]
>Laden Sie den Cloud Readiness Analyzer (CRA) aus der ausstehenden Version herunter.

## Ausführen des Cloud Readiness Analyzer {#running-tool}

In diesem Abschnitt erfahren Sie, wie Sie Cloud Readiness Analyzer ausführen:

1. Wählen Sie Adobe Experience Manager und navigieren Sie zu Tools -> **Vorgänge** -> **Cloud-Bereitstellungsanalyse**.

### Anzeigen der Ergebnisse {#viewing-the-results}

Die Ausgabe der Ratingagentur kann auf zweierlei Weise Ansicht werden:

1. Verwenden des organisierten Berichts (verfügbar ab AEM Version 6.3) Informationen zu den Stufen der Wichtigkeit im Bericht finden Sie unter CRA-Dokument-Planung und -Status

So Ansicht der Ausgabe der CRA (kann mit AEM Version 6.1 und höher verwendet werden):

1. Navigieren Sie zur AEM Web Console, indem Sie zu navigieren.

1. Wählen Sie Status - Cloud Readiness Analyzer, wie in der Abbildung unten dargestellt.