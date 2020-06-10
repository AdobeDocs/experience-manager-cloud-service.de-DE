---
title: Verwenden von Cloud Readiness Analyzer
description: Verwenden von Cloud Readiness Analyzer
translation-type: tm+mt
source-git-commit: 3d818278c53f3d3b4c5b53aa5b78d06d876bf05f
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 6%

---


# Verwenden von Cloud Readiness Analyzer {#using-cloud-readiness-analyzer}

## Wichtige Überlegungen zur Verwendung von Cloud Readiness Analyzer {#imp-considerations}

Gehen Sie wie folgt vor, um die wichtigen Überlegungen beim Ausführen des Cloud Readiness Analyzer (CRA) zu verstehen:

* CRA wird auf AEM-Quellinstanzen mit Version 6.1 und höher unterstützt.
* CRA kann auf jeder Umgebung ausgeführt werden.

   >[!NOTE]
   >Um die Erkennungsrate zu erhöhen und eine Verlangsamung bei geschäftskritischen Instanzen zu vermeiden, wird empfohlen, CRA auf den Staging-Umgebung des Quellautors auszuführen, die den Produktionsbereichen Anpassungen, Konfigurationen, Inhalts- und Benutzeranwendungen so nahe wie möglich sind. Alternativ kann es auch auf einem Klon der Veröffentlichungsdatei ausgeführt werden.

## Verfügbarkeit {#availability}

Der Cloud Readiness Analyzer (CRA) kann als ZIP-Datei vom Software Distribution Portal heruntergeladen werden. Sie können das Paket über Package Manager in Ihrer Quelldistanz von Adobe Experience Manager (AEM) installieren.

>[!NOTE]
>Laden Sie den Cloud Readiness Analyzer (CRA) aus der *ausstehenden Datei herunter*.

## Ausführen des Cloud Readiness Analyzer {#running-tool}

In diesem Abschnitt erfahren Sie, wie Sie Cloud Readiness Analyzer ausführen:

1. Select the Adobe Experience Manager and navigate to tools -> **Operations** -> **Cloud Readiness Analyzer**.

### Anzeigen der Ergebnisse {#viewing-the-results}

Die Ausgabe der Ratingagentur kann auf zweierlei Weise Ansicht werden:

1. Verwenden des organisierten Berichts

   >[!NOTE]
   >Der organisierte Bericht ist in AEM Version 6.3 und höher verfügbar.

Informationen zu den wichtigen Ebenen im Bericht finden Sie unter CRA-Dokument-Planung und -Status

1. Ansicht der Ausgabe der CRA (kann mit AEM Version 6.1 und höher verwendet werden):

   1. Navigieren Sie zur AEM Web Console, indem Sie zu navigieren.

   1. Wählen Sie Status - Cloud Readiness Analyzer, wie in der Abbildung unten dargestellt.

#### Informationen zu wichtigen Ebenen im Bericht {#importance-levels}

In der folgenden Tabelle wird die Bedeutung der verschiedenen Stufen &quot;Mustererkennung&quot;und &quot;Cloud-Bereitschaftsanalysator&quot;beschrieben.

| Wichtigkeitsstufe | Beschreibung |
|--- |--- |
| INFO/0 | Diese Ergebnisse werden zu Informationszwecken bereitgestellt. |
| BERATUNG/1 | Diese Feststellung stellt möglicherweise ein Problem bei der Aktualisierung dar. Weitere Untersuchungen werden empfohlen. |
| MAJOR/2 | Diese Feststellung ist wahrscheinlich ein Aktualisierungsfehler, der behoben werden sollte. |
| KRITISCH/3 | Diese Feststellung ist wahrscheinlich ein Aktualisierungsfehler, der behoben werden muss, um Funktionsverlust oder Leistungseinbußen zu vermeiden. |