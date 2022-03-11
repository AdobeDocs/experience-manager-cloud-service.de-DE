---
title: Testen der Code-Qualität
description: Erfahren Sie, wie das Testen der Code-Qualität von Pipelines funktioniert und wie damit die Qualität Ihrer Bereitstellungen verbessert werden kann.
exl-id: e2981be9-fb14-451c-ad1e-97c487e6dc46
source-git-commit: 15fb2823d231048885a140edfaa904527a026aae
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 77%

---

# Testen der Code-Qualität {#code-quality-testing}

Erfahren Sie, wie das Testen der Code-Qualität von Pipelines funktioniert und wie damit die Qualität Ihrer Bereitstellungen verbessert werden kann.

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_codequalitytests"
>title="Testen der Code-Qualität"
>abstract="Beim Code-Qualitätstest wird Ihr Anwendungscode anhand eines Satzes von Qualitätsregeln bewertet. Dies ist der Hauptzweck einer reinen Codequalitäts-Pipeline und wird unmittelbar nach dem Build-Schritt in allen Produktions- und Nicht-Produktions-Pipelines ausgeführt."

## Einführung {#introduction}

Beim Code-Qualitätstest wird Ihr Anwendungscode anhand eines Satzes von Qualitätsregeln bewertet. Dies ist der Hauptzweck einer reinen Codequalitäts-Pipeline und wird unmittelbar nach dem Build-Schritt in allen Produktions- und Nicht-Produktions-Pipelines ausgeführt.

Siehe Dokument . [Konfigurieren der CI/CD-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) , um mehr über verschiedene Pipelinetypen zu erfahren.

## Code-Qualitätsregeln {#understanding-code-quality-rules}

Beim Testen der Code-Qualität wird der Quell-Code gescannt, um sicherzustellen, dass er bestimmte Qualitätskriterien erfüllt. Dies wird durch eine Kombination aus SonarQube und der Prüfung auf Inhaltspaketebene mit OakPAL implementiert. Es gibt über 100 Regeln, die generische Java-Regeln und AEM-spezifische Regeln kombinieren. Einige der AEM-spezifischen Regeln werden auf der Grundlage der Best Practices von AEM Engineering erstellt und werden als [benutzerspezifische Code-Qualitätsregeln](/help/implementing/cloud-manager/custom-code-quality-rules.md).

>[!NOTE]
>
>Sie können die vollständige Liste der Regeln herunterladen [mit diesem Link.](/help/implementing/cloud-manager/assets/CodeQuality-rules-latest-CS.xlsx)

### Dreistufige Bewertungen {#three-tiered-gate}

Probleme, die durch Code-Qualitätstests identifiziert werden, werden einer von drei Kategorien zugewiesen.

* **Kritisch**: Hierbei handelt es sich um vom Test identifizierte Probleme, die zu einem sofortigen Pipeline-Fehler führen.

* **Wichtig**: Hierbei handelt es sich um Probleme, durch die die Pipeline angehalten wird. Implementierungs-Manager, Projekt-Manager oder Geschäftsinhaber können die Probleme außer Kraft setzen. In diesem Fall wird die Pipeline fortgesetzt. Sie können die Probleme aber auch akzeptieren. In diesem Fall stoppt die Pipeline mit einem Fehler.

* **Info** - Hierbei handelt es sich um Probleme, die ausschließlich zu Informationszwecken bereitgestellt werden und keine Auswirkungen auf die Pipelineausführung haben

Die Ergebnisse dieses Schritts werden als **Bewertung** bereitgestellt.

Die folgende Tabelle fasst die Bewertungen und Fehlerschwellen für die einzelnen kritischen, wichtigen und Informationskategorien zusammen.

| Name | Definition | Kategorie | Fehlerschwellenwert |
|--- |--- |--- |--- |
| Sicherheitsbewertung | A = Keine Schwachstellen <br/>B = mindestens 1 kleinere Schwachstelle <br/>C = mindestens 1 größere Schwachstelle <br/>D = mindestens 1 kritische Schwachstelle <br/>E = mindestens 1 Schwachstelle der Kategorie „Blocker“ | Kritisch | &lt; B |
| Zuverlässigkeitsbewertung | A = Keine Fehler <br/>B = mindestens 1 kleinerer Fehler <br/>C = mindestens 1 größerer Fehler <br/>D = mindestens 1 kritischer Fehler<br>E = mindestens 1 Fehler der Kategorie „Blocker“ | Kritisch | &lt; D |
| Wartbarkeitsbewertung | Definiert durch die ausstehenden Kosten für die Behebung von Code-Fehlern als Prozentsatz der Zeit, die bereits in das Programm investiert wurde<br/><ul><li>A = &lt;=5 %</li><li>B = 6-10 %</li><li>C = 11-20 %</li><li>D = 21-50 %</li><li>E = >50 %</li></ul> | Wichtig | &lt; A |
| Abdeckung | Definiert durch eine Mischung aus Zeilenabdeckung der Einheitstests und Bedingungsabdeckung nach der Formel: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`  <ul><li>`CT` = Bedingungen wurden mindestens einmal während der Ausführung der Einheitentests zu `true` ausgewertet</li><li>`CF` = Bedingungen wurden mindestens einmal während der Ausführung der Einheitentests zu `false` ausgewertet</li><li>`LC` = abgedeckte Zeilen = lines_to_cover - uncovered_lines</li><li>`B` = Gesamtzahl der Bedingungen</li><li>`EL` = Gesamtzahl der ausführbaren Zeilen (lines_to_cover)</li></ul> | Wichtig | &lt; 50 % |
| Übersprungene Einheitentests | Anzahl der übersprungenen Einheitentests | Info | > 1 |
| Offene Probleme | Allgemeine Problemtypen – Schwachstellen (Vulnerability), Fehler (Bug) und Code-Smells (Code Smell) | Info | > 0 |
| Duplizierte Zeilen | Definiert als die Anzahl der Zeilen, die in doppelten Blöcken enthalten sind. Ein Code-Block gilt unter den folgenden Bedingungen als dupliziert.<br>Nicht-Java-Projekte:<ul><li>Es sollten mindestens 100 aufeinanderfolgende und duplizierte Token vorhanden sein.</li><li>Diese Token sollten sich mindestens wie folgt verteilen: </li><li>30 Codezeilen für COBOL </li><li>20 Codezeilen für ABAP </li><li>10 Codezeilen für andere Sprachen</li></ul>Java-Projekte:<ul></li><li> Unabhängig von der Anzahl der Token und Zeilen sollte es mindestens 10 aufeinanderfolgende und duplizierte Anweisungen geben.</li></ul>Unterschiede bei Einzügen sowie Zeichenfolgenliteralen werden beim Erkennen von Duplikaten ignoriert. | Info | > 1 % |
| Kompatibilität mit Cloud Service | Anzahl der festgestellten Kompatibilitätsprobleme mit Cloud Service | Info | > 0 |

>[!NOTE]
>
>Siehe [Metrikdefinitionen von SonarQube](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) für detailliertere Definitionen.

>[!NOTE]
>
>Weitere Informationen zu den benutzerdefinierten Regeln zur Code-Qualität, die von [!UICONTROL Cloud Manager] ausgeführt werden, finden Sie unter [Benutzerspezifische Regeln für Code-Qualität](/help/implementing/cloud-manager/custom-code-quality-rules.md).

## Umgang mit falsch positiven Treffern {#dealing-with-false-positives}

Das Verfahren zur Qualitätsprüfung ist nicht perfekt. Mitunter werden fälschlicherweise Probleme identifiziert, die eigentlich nicht problematisch sind. Dies wird als **falsch positiv** bezeichnet.

In diesen Fällen kann der Quell-Code mit der standardmäßigen `@SuppressWarnings`-Java-Anmerkung kommentiert werden. Dabei wird die Regel-ID als Anmerkungsattribut angegeben. Ein häufiges Problem besteht etwa darin, dass die SonarQube-Regel zur Erkennung hartcodierter Kennwörter in Bezug auf die Identifizierung eines hartcodierten Kennworts „aggressiv“ sein kann.

Der folgende Code ist in einem AEM-Projekt, das eine Verbindung zu einem externen Service herstellen soll, relativ häufig.

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

Wenn der Code allerdings tatsächlich so lautete:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Dann bestünde die richtige Lösung darin, das hartcodierte Kennwort zu entfernen.

>[!NOTE]
>
>Obwohl sich möglichst spezifische `@SuppressWarnings`-Anmerkungen bewährt haben, also nur eine bestimmte Anweisung oder den Block zu kommentieren, der das Problem verursacht, können Anmerkungen auf Klassenebene hinzugefügt werden.

>[!NOTE]
>Es gibt zwar keinen expliziten Sicherheitstestschritt, doch gibt es sicherheitsrelevante Code-Qualitätsregeln, die während des Codequalitätsschritts bewertet werden. Siehe Dokument . [Sicherheitsübersicht für AEM as a Cloud Service](/help/security/cloud-service-security-overview.md) um mehr über die Sicherheit in Cloud Service zu erfahren.

## Optimierung der Inhaltspaketüberprüfung {#content-package-scanning-optimization}

Im Rahmen des Qualitätsanalyseprozesses führt Cloud Manager eine Analyse der vom Maven-Build erzeugten Inhaltspakete durch. Cloud Manager bietet Optimierungen zur Beschleunigung dieses Prozesses an, die wirksam sind, wenn bestimmte Verpackungseinschränkungen beachtet werden. Am wichtigsten ist die Optimierung, die für Projekte durchgeführt wird, die ein einzelnes Inhaltspaket ausgeben, das im Allgemeinen als „all“-Paket bezeichnet wird und eine Reihe andere Inhaltspakete enthält, die durch den Build erzeugt und als übersprungen markiert wurden. Wenn Cloud Manager dieses Szenario erkennt, wird nicht das gesamte Paket entpackt, sondern die einzelnen Inhaltspakete werden direkt gescannt und auf der Grundlage von Abhängigkeiten sortiert. Betrachten Sie zum Beispiel die folgende Build-Ausgabe.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (Inhaltspaket)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (übersprungenes Inhaltspaket)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (übersprungenes Inhaltspaket)

Wenn die beiden übersprungenen Inhaltspakete die einzigen Elemente innerhalb von `myco-all-1.0.0-SNAPSHOT.zip` sind, werden die beiden eingebetteten Pakete anstelle des gesamten Inhaltspakets (all) gescannt.

Bei Projekten, die Dutzende von eingebetteten Paketen produzieren, kann diese Optimierung nachweislich bis zu 10 Minuten pro Pipeline-Ausführung einsparen.

Ein Sonderfall kann eintreten, wenn das Inhaltspaket „all“ eine Kombination aus übersprungenen Inhaltspaketen und OSGi-Bundles enthält. Wenn `myco-all-1.0.0-SNAPSHOT.zip` beispielsweise die beiden zuvor erwähnten eingebetteten Pakete sowie ein oder mehrere OSGi-Bundles enthält, wird ein neues, minimales Inhaltspaket nur mit den OSGi-Bundles erstellt. Dieses Paket hat immer die Bezeichnung `cloudmanager-synthetic-jar-package` und die darin enthaltenen Bundles werden in `/apps/cloudmanager-synthetic-installer/install` abgelegt.

>[!NOTE]
>
>* Diese Optimierung hat keine Auswirkungen auf die Pakete, die in AEM bereitgestellt werden.
>* Da der Abgleich zwischen den eingebetteten Inhaltspaketen und den übersprungenen Inhaltspaketen auf Dateinamen basiert, kann diese Optimierung nicht durchgeführt werden, wenn mehrere übersprungene Inhaltspakete genau denselben Dateinamen haben oder wenn der Dateiname während des Einbettens geändert wird.

