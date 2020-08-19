---
title: Codequalitätstests - Cloud Services
description: Codequalitätstests - Cloud Services
translation-type: tm+mt
source-git-commit: 25ba5798de175b71be442d909ee5c9c37dcf10d4
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Testen der Codequalität {#code-quality-testing}

Die Codequalitätsprüfung bewertet die Qualität Ihres Anwendungscodes. Es ist das Kernziel einer reinen Code-Quality-Pipeline und wird unmittelbar nach dem Bauschritt in allen Nicht-Produktions- und Produktionsleitungen ausgeführt.

Weitere Informationen zu den verschiedenen Pipelines finden Sie unter [Konfigurieren der CI-CD-Pipeline](/help/implementing/cloud-manager/configure-pipeline.md) .

## Grundlegendes zu benutzerspezifischen Regeln für die Code-Qualität {#understanding-code-quality-rules}

Bei der Codequalitätsprüfung wird der Quellcode gescannt, um sicherzustellen, dass er bestimmte Qualitätskriterien erfüllt. Derzeit ist dies durch eine Kombination aus SonarQube und der Prüfung auf Inhaltspaketebene mithilfe von OakPAL implementiert. Es gibt über 100 Regeln, die generische Java-Regeln und AEM-spezifische Regeln kombinieren. Einige der AEM-spezifischen Regeln werden auf der Grundlage der Best Practices von AEM Engineering erstellt und werden als [benutzerspezifische Code-Qualitätsregeln](/help/implementing/cloud-manager/custom-code-quality-rules.md)bezeichnet.

>[!NOTE]
>You can download the complete list of rules [here](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest.xlsx).

Die Ergebnisse dieses Schritts werden als *Bewertung* bereitgestellt. In der folgenden Tabelle finden Sie eine Zusammenfassung der Testkriterienbewertung:

| Name | Definition | Kategorie | Fehlerschwellenwert |
|--- |--- |--- |--- |
| Sicherheitsbewertung | A = 0 Schwachstellen <br/>B = mindestens 1 kleinere Schwachstelle<br/> C = mindestens 1 größere Schwachstelle <br/>D = mindestens 1 kritische Schwachstelle <br/>E = mindestens 1 Schwachstelle der Kategorie „Blocker“ | Kritisch | &lt; B |
| Zuverlässigkeitsbewertung | A = 0 Fehler <br/>B = mindestens 1 kleinerer Fehler <br/>C = mindestens 1 größerer Fehler <br/>D = mindestens 1 kritischer Fehler E = mindestens 1 Fehler der Kategorie „Blocker“ | Wichtig | &lt; C |
| Wartbarkeitsbewertung | Wenn die ausstehenden Kosten zur Code-Smell-Behebung …<br/><ul><li>&lt;= 5 % der Zeit ausmachen, die bereits in die Anwendung investiert wurde, lautet die Bewertung A. </li><li>zwischen 6 und 10 % dieser Zeit ausmachen, lautet die Bewertung B. </li><li>zwischen 11 und 20 % dieser Zeit ausmachen, lautet die Bewertung C. </li><li>zwischen 21 und 50 % dieser Zeit ausmachen, lautet die Bewertung D.</li><li>mehr als 50 % dieser Zeit ausmachen, lautet die Bewertung E.</li></ul> | Wichtig | &lt; A |
| Abdeckung | Mix aus Zeilen- und Bedingungsabdeckung mit dieser Formel: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`<br/> Dabei gilt Folgendes: CT = Bedingungen, bei denen die Auswertung während der Durchführung von Unit-Tests mindestens einmal „true“ ergeben hat <br/>CF = Bedingungen, bei denen die Auswertung während der Durchführung von Unit-Tests mindestens einmal „false“ ergeben hat <br/>LC = abgedeckte Zeilen = abzudeckende_Zeilen - nicht_abgedeckte_Zeilen <br/><br/> B = Gesamtanzahl der Bedingungen <br/>EL = Gesamtzahl ausführbarer Zeilen (abzudeckende_Zeilen) | Wichtig | &lt; 50% |
| Übersprungene Unit-Tests | Zahl der übersprungenen Unit-Tests | Info | > 1 |
| Offene Probleme | Allgemeine Problemtypen – Schwachstellen (Vulnerability), Fehler (Bug) und Code-Smells (Code Smell) | Info | > 0 |
| Duplizierte Zeilen | Anzahl der Zeilen, die an duplizierten Blöcken beteiligt sind. <br/>Voraussetzungen, damit ein Codeblock als dupliziert gilt: <br/><ul><li>**Nicht-Java-Projekte:**</li><li>Es sollte mindestens 100 aufeinanderfolgende und duplizierte Token geben.</li><li>Diese Token sollten sich mindestens wie folgt verteilen: </li><li>30 Codezeilen für COBOL </li><li>20 Codezeilen für ABAP </li><li>10 Codezeilen für andere Sprachen</li><li>**Java-Projekte:**</li><li> Unabhängig von der Anzahl der Token und Zeilen sollte es mindestens 10 aufeinanderfolgende und duplizierte Anweisungen geben.</li></ul> <br/>Unterschiede bei Einzügen sowie Zeichenfolgenliteralen werden beim Erkennen von Duplizierungen ignoriert. | Info | > 1% |
| Kompatibilität mit Cloud Service | Anzahl der festgestellten Kompatibilitätsprobleme mit Cloud Service. | Info | > 0 |

>[!NOTE]
>
>Genauere Definitionen finden Sie unter [Metrikdefinitionen](https://docs.sonarqube.org/display/SONAR/Metric+Definitions).


>[!NOTE]
>
>Weitere Informationen zu den benutzerdefinierten Regeln zur Code-Qualität, die von [!UICONTROL Cloud Manager] ausgeführt werden, finden Sie unter [Benutzerspezifische Regeln für Code-Qualität](/help/implementing/cloud-manager/custom-code-quality-rules.md).

## Umgang mit falsch positiven Werten {#dealing-with-false-positives}

Das Verfahren zur Qualitätsprüfung ist nicht perfekt. Mitunter werden fälschlicherweise Probleme identifiziert, die eigentlich nicht problematisch sind. Dies wird als „falsch positiv“ bezeichnet.

In diesen Fällen kann der Quellcode mit der standardmäßigen `@SuppressWarnings`-Java-Anmerkung kommentiert werden. Dabei wird die Regel-ID als Anmerkungsattribut angegeben. Ein häufiges Problem besteht etwa darin, dass die SonarQube-Regel zur Erkennung hartcodierter Kennwörter in Bezug auf die Identifizierung eines hartcodierten Kennworts „aggressiv“ sein kann.

Sehen wir uns ein konkretes Beispiel mit Code an, der in AEM-Projekten relativ häufig vorkommt, wenn eine Verbindung zu einem externen Dienst hergestellt werden soll:

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube weist dann auf eine Schwachstelle der Kategorie „Blocker“ hin. Nach Prüfung des Codes erkennen Sie, dass es sich nicht um eine Schwachstelle handelt, und kommentieren dies mit der entsprechenden Regel-ID.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Aber was wäre bei diesem Code?

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Dann bestünde die richtige Lösung darin, das hartcodierte Kennwort zu entfernen.

>[!NOTE]
>
>Obwohl sich möglichst spezifische `@SuppressWarnings`-Anmerkungen bewährt haben, also nur eine bestimmte Anweisung oder den Block zu kommentieren, der das Problem verursacht, können Anmerkungen auf Klassenebene hinzugefügt werden.

>[!NOTE]
>Es gibt zwar keinen expliziten Sicherheitstestschritt, es gibt jedoch weiterhin sicherheitsbezogene Code-Qualitätsregeln, die während des Codequalitätsschritts bewertet werden. Weitere Informationen zur Sicherheit in Cloud Service finden Sie in der [Sicherheitsübersicht AEM als Cloud Service](/help/security/cloud-service-security-overview.md) .
