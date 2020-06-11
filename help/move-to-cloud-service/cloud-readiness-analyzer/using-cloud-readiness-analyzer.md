---
title: Verwenden von Cloud Readiness Analyzer
description: Verwenden von Cloud Readiness Analyzer
translation-type: tm+mt
source-git-commit: 47773a56f8bb24342281068a8c4d03d6edfb9277
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 5%

---


# Verwenden von Cloud Readiness Analyzer {#using-cloud-readiness-analyzer}

## Wichtige Überlegungen zur Verwendung von Cloud Readiness Analyzer {#imp-considerations}

Gehen Sie wie folgt vor, um die wichtigen Überlegungen beim Ausführen des Cloud Readiness Analyzer (CRA) zu verstehen:

* CRA wird auf AEM-Quellinstanzen mit Version 6.1 und höher unterstützt
* CRA kann auf jeder Umgebung ausgeführt werden (vorzugsweise *Stage* -Umgebung)

   >[!NOTE]
   >Um die Erkennungsrate zu erhöhen und eine Verlangsamung bei geschäftskritischen Instanzen zu vermeiden, wird empfohlen, CRA auf den Staging-Umgebung des Quellautors auszuführen, die den Produktionsbereichen Anpassungen, Konfigurationen, Inhalts- und Benutzeranwendungen so nahe wie möglich sind. Alternativ kann es auch auf einem Klon der *Publish* -Umgebung ausgeführt werden.

## Verfügbarkeit {#availability}

Der Cloud Readiness Analyzer kann als ZIP-Datei vom Software Distribution Portal heruntergeladen werden. Sie können das Paket über Package Manager in Ihrer Quelldistanz von Adobe Experience Manager (AEM) installieren.

>[!NOTE]
>Laden Sie den Cloud Readiness Analyzer aus dem Software Distribution Portal *ausstehend* herunter.

## Ausführen des Cloud Readiness Analyzer {#running-tool}

In diesem Abschnitt erfahren Sie, wie Sie Cloud Readiness Analyzer ausführen:

1. Select the Adobe Experience Manager and navigate to tools -> **Operations** -> **Cloud Readiness Analyzer**.

### Anzeigen der Ergebnisse {#viewing-the-results}

>[!IMPORTANT]
>Die Berichte, die mit Cloud Readiness Analyzer erstellt wurden, basieren auf Musterdetektoren. Weitere Informationen finden Sie unter [Musterdetektoren](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html) .

Es gibt zwei Möglichkeiten, die Ausgabe aus dem Cloud-Bereitschaftsanalysator Ansicht:

1. **Verwenden des Organisierten Berichts**

   >[!NOTE]
   >Der organisierte Bericht ist in AEM Version 6.3 und höher verfügbar.

   Oder

1. **Ausgabe der CRA anzeigen**

   Gehen Sie wie folgt vor, um die Ausgabe aus dem Cloud-Bereitschaftsanalyzer Ansicht:

   >[!NOTE]
   >Die folgenden Schritte gelten für AEM Version 6.1 und höher.

   1. Navigieren Sie mit **AEM Web Console** zu `https://serveraddress:serverport/system/console/configMgr`.

   1. Select **Status - Pattern Detector** as shown in the figure below.

#### Ansicht des Berichts in AEM 6.1-Instanzen {#aem-instances-report}

Sie können den CSV-Bericht für AEM 6.1 herunterladen. Dies steht noch aus.

#### Informationen zu wichtigen Ebenen im Bericht {#importance-levels}

In der folgenden Tabelle wird die Bedeutung der verschiedenen Stufen &quot;Mustererkennung&quot;und &quot;Cloud-Bereitschaftsanalysator&quot;beschrieben.

| Wichtigkeitsstufe | Beschreibung |
|--- |--- |
| INFO/0 | Diese Ergebnisse werden zu Informationszwecken bereitgestellt. |
| BERATUNG/1 | Diese Feststellung stellt möglicherweise ein Problem bei der Aktualisierung dar. Weitere Untersuchungen werden empfohlen. |
| MAJOR/2 | Diese Feststellung ist wahrscheinlich ein Aktualisierungsfehler, der behoben werden sollte. |
| KRITISCH/3 | Diese Feststellung ist wahrscheinlich ein Aktualisierungsfehler, der behoben werden muss, um Funktionsverlust oder Leistungseinbußen zu vermeiden. |