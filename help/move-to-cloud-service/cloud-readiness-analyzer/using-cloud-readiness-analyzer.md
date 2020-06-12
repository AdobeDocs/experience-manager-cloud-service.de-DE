---
title: Verwenden von Cloud Readiness Analyzer
description: Verwenden von Cloud Readiness Analyzer
translation-type: tm+mt
source-git-commit: f0e69dba5d670d141c82e762069f4831c2527dbe
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 4%

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

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-1.png)

1. Wenn Sie auf **Cloud Readiness Analyzer** klicken, werden die Tool-Beginn, die den Bericht generieren, und nach einigen Minuten wird der erstellte Bericht angezeigt.

   >[!NOTE]
   >Sie müssen einen Bildlauf nach unten durchführen, um den vollständigen Bericht Ansicht.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-2.png)

### Ansicht der Ergebnisse im Zusammenfassungsbericht {#viewing-the-results}

>[!IMPORTANT]
>Die Berichte, die mit Cloud Readiness Analyzer erstellt wurden, basieren auf Musterdetektoren. Weitere Informationen finden Sie unter [Musterdetektoren](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html) .

Wenn Sie nach unten blättern, um den vollständigen Zusammenfassungsbericht Ansicht, sehen Sie die folgenden Informationen zu jeder im Bericht hervorgehobenen Kategorie:

1. **Wichtigkeitsstufe**

   In der folgenden Tabelle wird die Bedeutung der verschiedenen Stufen &quot;Mustererkennung&quot;und &quot;Cloud-Bereitschaftsanalysator&quot;beschrieben.

   | Wichtigkeitsstufe | Beschreibung |
   |--- |--- |
   | INFO/0 | Diese Ergebnisse werden zu Informationszwecken bereitgestellt. |
   | BERATUNG/1 | Diese Feststellung stellt möglicherweise ein Problem bei der Aktualisierung dar. Weitere Untersuchungen werden empfohlen. |
   | MAJOR/2 | Diese Feststellung ist wahrscheinlich ein Aktualisierungsfehler, der behoben werden sollte. |
   | KRITISCH/3 | Diese Feststellung ist wahrscheinlich ein Aktualisierungsfehler, der behoben werden muss, um Funktionsverlust oder Leistungseinbußen zu vermeiden. |

1. **Beschreibung** Die Beschreibung enthält Informationen zur gemeldeten Kategorie.

1. **Dokumentations-URL** Die Dokumentations-URL ermöglicht die Ansicht der technischen Dokumentation für den jeweiligen Typ.

1. **Meldung** Eine Beschreibung der Suche in einer einzelnen Meldung.

### Ansicht der Ergebnisse in einem CSV-Format {#viewing-the-results-csv}

Der Zusammenfassungsbericht ist in der AEM-Benutzeroberfläche verfügbar. Sie können den vollständigen Bericht in einem CSV-Format (kommagetrennte Werte) herunterladen, das während des Umgestaltungsprozesses hilfreich ist.

Gehen Sie wie folgt vor, um ein CSV-Format für Ihren Zusammenfassungsbericht zu erstellen:

1. 
   1. Select the Adobe Experience Manager and navigate to tools -> **Operations** -> **Cloud Readiness Analyzer**.

1. Klicken Sie nach der Berichterstellung auf **CSV** , um den vollständigen Zusammenfassungsbericht im CSV-Format (CSV) herunterzuladen, wie in der folgenden Abbildung dargestellt.

![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-3.png)


#### Ansicht des Berichts in AEM 6.1-Instanzen {#aem-instances-report}

Sie können den CSV-Bericht für AEM 6.1 herunterladen. Dies steht noch aus.

