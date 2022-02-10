---
title: Testen der Code-Qualität
description: Erfahren Sie, wie das Testen der Codequalität von Pipelines funktioniert und wie es die Qualität Ihrer Implementierungen verbessern kann.
exl-id: e2981be9-fb14-451c-ad1e-97c487e6dc46
source-git-commit: ca3c1f255b8441a8d376a55a5353d58848384b8b
workflow-type: tm+mt
source-wordcount: '1106'
ht-degree: 20%

---

# Testen der Code-Qualität {#code-quality-testing}

Erfahren Sie, wie das Testen der Codequalität von Pipelines funktioniert und wie es die Qualität Ihrer Implementierungen verbessern kann.

>[!CONTEXTUALHELP]
>
>
## Einführung {#introduction}

Beim Code-Qualitätstest wird Ihr Anwendungscode anhand eines Satzes von Qualitätsregeln bewertet. Dies ist der Hauptzweck einer reinen Codequalitäts-Pipeline und wird unmittelbar nach dem Build-Schritt in allen Produktions- und Nicht-Produktions-Pipelines ausgeführt.

Siehe Dokument . [Konfigurieren der CI/CD-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) , um mehr über verschiedene Pipelinetypen zu erfahren.

## Code-Qualitätsregeln {#understanding-code-quality-rules}

Codequalitätstests scannen den Quellcode, um sicherzustellen, dass er bestimmte Qualitätskriterien erfüllt. Dies wird durch eine Kombination aus SonarQube und der Prüfung auf Inhaltspaketebene mit OakPAL implementiert. Es gibt über 100 Regeln, die generische Java-Regeln und AEM-spezifische Regeln kombinieren. Einige der AEM-spezifischen Regeln werden auf der Grundlage der Best Practices von AEM Engineering erstellt und werden als [benutzerspezifische Code-Qualitätsregeln](/help/implementing/cloud-manager/custom-code-quality-rules.md).

>[!NOTE]
Sie können die vollständige Liste der Regeln herunterladen [mit diesem Link.](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest-CS.xlsx)

### Dreistufige Bewertungen {#three-tiered-gate}

Probleme, die durch Code-Qualitätstests identifiziert werden, werden einer von drei Kategorien zugewiesen.

* **Kritisch** - Hierbei handelt es sich um Probleme, die zu einem sofortigen Pipelinefehler führen.

* **Wichtig** - Hierbei handelt es sich um Probleme, durch die die Pipeline angehalten wird. Implementierungs-Manager, Projekt-Manager oder Geschäftsinhaber können die Probleme außer Kraft setzen. In diesem Fall wird die Pipeline fortgesetzt. Sie können die Probleme aber auch akzeptieren. In diesem Fall stoppt die Pipeline mit einem Fehler.

* **Info** - Hierbei handelt es sich um Probleme, die ausschließlich zu Informationszwecken bereitgestellt werden und keine Auswirkungen auf die Pipelineausführung haben

Die Ergebnisse dieses Schritts werden als **Bewertung** bereitgestellt.

Die folgende Tabelle fasst die Bewertungen und Fehlerschwellen für die einzelnen kritischen, wichtigen und Informationskategorien zusammen.

| Name | Definition | Kategorie | Fehlerschwellenwert |
|--- |--- |--- |--- |
| Sicherheitsbewertung | A = Keine Schwachstellen <br/>B = Mindestens 1 kleinere Schwachstelle<br/> C = Mindestens 1 größere Schwachstelle <br/>D = Mindestens 1 kritische Schwachstelle <br/>E = Mindestens 1 Blocker-Schwachstelle | Kritisch | &lt; B |
| Zuverlässigkeitsbewertung | A = Keine Fehler <br/>B = Mindestens 1 kleinerer Fehler <br/>C = Mindestens 1 größerer Fehler <br/>D = Mindestens 1 kritischer Fehler<br>E = Mindestens 1 Blockerfehler | Kritisch | &lt; D |
| Wartbarkeitsbewertung | Definiert durch die ausstehenden Sanierungskosten für Code-Smell als Prozentsatz der Zeit, die bereits in die Anwendung gegangen ist<br/><ul><li>A = &lt; = 5 %</li><li>B = 6-10 %</li><li>C = 11-20 %</li><li>D = 21-50 %</li><li>E = > 50 %</li></ul> | Wichtig | &lt; A |
| Abdeckung | Definiert durch eine Mischung aus Unit-Test-Line-Abdeckung und Bedingungsabdeckung anhand der Formel: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <ul><li>`CT` = Bedingungen, die als `true` mindestens einmal während der Durchführung von Komponententests</li><li>`CF` = Bedingungen, die als `false` mindestens einmal während der Durchführung von Komponententests</li><li>`LC` = Überdeckte Zeilen = lines_to_cover - uncover_lines</li><li>`B` = Gesamtzahl der Bedingungen</li><li>`EL` = Gesamtzahl ausführbarer Zeilen (lines_to_cover)</li></ul> | Wichtig | &lt; 50 % |
| Übersprungene Unit-Tests | Anzahl der übersprungenen Komponententests | Info | > 1 |
| Offene Probleme | Allgemeine Problemtypen – Schwachstellen (Vulnerability), Fehler (Bug) und Code-Smells (Code Smell) | Info | > 0 |
| Duplizierte Zeilen | Definiert als Anzahl der Zeilen, die an duplizierten Blöcken beteiligt sind. Ein Codeblock wird unter den folgenden Bedingungen als dupliziert betrachtet.<br>Nicht-Java-Projekte:<ul><li>Es sollte mindestens 100 aufeinanderfolgende und duplizierte Token geben.</li><li>Diese Token sollten sich mindestens auf Folgendes erstrecken: </li><li>30 Codezeilen für COBOL </li><li>20 Codezeilen für ABAP </li><li>10 Codezeilen für andere Sprachen</li></ul>Java-Projekte:<ul></li><li> Unabhängig von der Anzahl der Token und Zeilen sollten mindestens 10 aufeinander folgende und duplizierte Anweisungen vorhanden sein.</li></ul>Unterschiede bei Einzügen sowie Zeichenfolgenliteralen werden beim Erkennen von Duplikaten ignoriert. | Info | > 1 % |
| Kompatibilität mit Cloud Service | Anzahl der festgestellten Kompatibilitätsprobleme mit Cloud Service | Info | > 0 |

>[!NOTE]
Siehe [Metrikdefinitionen von SonarQube](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) für detailliertere Definitionen.

>[!NOTE]
Weitere Informationen zu benutzerspezifischen Regeln für die Code-Qualität, die von [!UICONTROL Cloud Manager], siehe Dokument [Benutzerspezifische Regeln für Code-Qualität](/help/implementing/cloud-manager/custom-code-quality-rules.md).

## Umgang mit falsch positiven Treffern {#dealing-with-false-positives}

Das Verfahren zur Qualitätsprüfung ist nicht perfekt. Mitunter werden fälschlicherweise Probleme identifiziert, die eigentlich nicht problematisch sind. Dies wird als **falsch positiv** bezeichnet.

In diesen Fällen kann der Quell-Code mit der standardmäßigen `@SuppressWarnings`-Java-Anmerkung kommentiert werden. Dabei wird die Regel-ID als Anmerkungsattribut angegeben. Ein gängiges Falsch-Positiv-Ergebnis besteht beispielsweise darin, dass die SonarQube-Regel zur Erkennung hartcodierter Kennwörter in Bezug auf die Identifizierung eines hartcodierten Kennworts aggressiv sein kann.

Der folgende Code ist recht häufig in einem AEM Projekt enthalten, das über Code verfügt, um eine Verbindung zu einem externen Dienst herzustellen.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube weist dann eine Blocker-Schwachstelle auf. Nach der Überprüfung des Codes erkennen Sie jedoch, dass dies keine Schwachstelle ist, und können den Code mit der entsprechenden Regel-ID kommentieren.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Wenn der Code jedoch tatsächlich Folgendes war:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Dann bestünde die richtige Lösung darin, das hartcodierte Kennwort zu entfernen.

>[!NOTE]
Obwohl sich möglichst spezifische `@SuppressWarnings`-Anmerkungen bewährt haben, also nur eine bestimmte Anweisung oder den Block zu kommentieren, der das Problem verursacht, können Anmerkungen auf Klassenebene hinzugefügt werden.

>[!NOTE]
Es gibt zwar keinen expliziten Sicherheitstestschritt, doch gibt es sicherheitsrelevante Code-Qualitätsregeln, die während des Codequalitätsschritts bewertet werden. Siehe Dokument . [Sicherheitsübersicht für AEM as a Cloud Service](/help/security/cloud-service-security-overview.md) um mehr über die Sicherheit in Cloud Service zu erfahren.

## Optimierung der Inhaltspaketsuche {#content-package-scanning-optimization}

Im Rahmen des Qualitätsanalyseprozesses führt Cloud Manager die Analyse der Inhaltspakete durch, die vom Maven-Build erstellt wurden. Cloud Manager bietet Optimierungen, um diesen Prozess zu beschleunigen, der bei der Einhaltung bestimmter Paketbeschränkungen wirksam ist. Am wichtigsten ist die Optimierung, die für Projekte durchgeführt wird, die ein einzelnes Inhaltspaket ausgeben, das allgemein als &quot;all&quot;-Paket bezeichnet wird und eine Reihe anderer Inhaltspakete enthält, die vom Build erstellt wurden und als übersprungen markiert sind. Wenn Cloud Manager dieses Szenario erkennt, anstatt das Paket &quot;all&quot;zu entpacken, werden die einzelnen Inhaltspakete direkt gescannt und basierend auf Abhängigkeiten sortiert. Betrachten Sie beispielsweise die folgende Build-Ausgabe.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (content-package)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (skipped-content-package)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (skipped-content-package)

Wenn die einzigen Elemente in `myco-all-1.0.0-SNAPSHOT.zip` die beiden übersprungenen Inhaltspakete sind, werden die beiden eingebetteten Pakete anstelle des Inhaltspakets &quot;all&quot;gescannt.

Bei Projekten, die Dutzende von eingebetteten Paketen produzieren, wird diese Optimierung nachweislich pro Pipeline-Ausführung um bis zu 10 Minuten reduziert.

Ein spezieller Fall kann auftreten, wenn das Inhaltspaket &quot;all&quot;eine Kombination aus übersprungenen Inhaltspaketen und OSGi-Bundles enthält. Wenn beispielsweise `myco-all-1.0.0-SNAPSHOT.zip` die beiden zuvor erwähnten eingebetteten Pakete sowie eines oder mehrere OSGi-Pakete enthielt, wird ein neues, minimales Inhaltspaket nur mit den OSGi-Bundles erstellt. Dieses Paket erhält immer den Namen `cloudmanager-synthetic-jar-package` und die enthaltenen Bundles in `/apps/cloudmanager-synthetic-installer/install`.

>[!NOTE]
* Diese Optimierung wirkt sich nicht auf die Pakete aus, die in AEM bereitgestellt werden.
* Da die Übereinstimmung zwischen den eingebetteten Inhaltspaketen und den übersprungenen Inhaltspaketen auf Dateinamen basiert, kann diese Optimierung nicht durchgeführt werden, wenn mehrere übersprungene Inhaltspakete genau denselben Dateinamen haben oder wenn der Dateiname beim Einbetten geändert wird.

