---
title: Implementieren eines benutzerdefinierten Prädikat-Auswerters für den Query Builder
description: Der Abfrage Builder in AEM Angeboten bietet eine einfache und anpassbare Möglichkeit zur Abfrage des Inhalts-Repository
translation-type: tm+mt
source-git-commit: 21a0e6967a17ea30435d0343c4aa497f54134cda
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 49%

---


# Implementieren eines benutzerdefinierten Prädikat-Auswerters für den Query Builder {#implementing-a-custom-predicate-evaluator-for-the-query-builder}

In diesem Dokument wird beschrieben, wie Sie den [Abfrage-Builder](query-builder-api.md) durch Implementierung eines benutzerdefinierten Prädikat-Evaluators erweitern.

## Überblick{#overview}

Der [Abfrage Builder](query-builder-api.md)-Angebot bietet eine einfache Möglichkeit, das Inhalts-Repository Abfrage. AEM enthält [eine Reihe von Prognoseauswertern](#query-builder-predicates.md), die Ihnen bei der Abfrage Ihrer Daten helfen.

Sie möchten jedoch vielleicht Abfragen vereinfachen, indem Sie einen benutzerdefinierten Prädikat-Auswerter implementieren, der weniger komplex ist und für eine bessere Semantik sorgt.

Ein benutzerdefiniertes Prädikat ist auch für andere Aufgaben nützlich, die nicht direkt mit XPath ausgeführt werden können, z. B.:

* Daten von einem anderen Dienst abfragen
* Benutzerdefinierte Filterung basierend auf einer Berechnung

>[!NOTE]
>
>Beim Implementieren eines benutzerdefinierten Prädikats müssen Leistungsaspekte berücksichtigt werden.

>[!TIP]
>
>Beispiele für Abfragen finden Sie im Dokument [Abfrage-Aufbau](query-builder-api.md).

>[!TIP]
>
>Den Code dieser Seite finden Sie auf GitHub
>
>* [Öffnen Sie das Projekt aem-search-custom-Predicate-evaluation auf GitHub](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator)
>* Laden Sie das Projekt als [ZIP-Datei](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/archive/master.zip) herunter.


>[!NOTE]
>
>Dieser verknüpfte Code auf GitHub und die Codeausschnitte in diesem Dokument dienen nur zu Demonstrationszwecken.

### Prädikat-Auswerter im Detail {#predicate-evaluator-in-detail}

Ein Prädikat-Auswerter ist für die Auswertung bestimmter Prädikate zuständig, die eine Abfrage einschränken.

Es ordnet eine übergeordnete Sucheinschränkung (z. B. `width>200`) einer bestimmten JCR-Abfrage zu, die dem eigentlichen Inhaltsmodell (z. B. `metadata/@width > 200`). Es können auch Knoten manuell gefiltert und deren Einschränkungen überprüft werden.

>[!TIP]
>
>Weitere Informationen zum `PredicateEvaluator`- und zum `com.day.cq.search`-Paket finden Sie in der [Java-Dokumentation](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/search/package-summary.html).

### Implementieren eines benutzerdefinierten Prädikat-Auswerters für Replikationsmetadaten {#implementing-a-custom-predicate-evaluator-for-replication-metadata}

In diesem Beispiel wird in diesem Abschnitt beschrieben, wie ein benutzerdefinierter Prädikate-Evaluator erstellt wird, der Daten basierend auf den Replikationsmetadaten unterstützt:

* `cq:lastReplicated` speichert die Daten der letzten Replikationsaktion.
* `cq:lastReplicatedBy` speichert die ID des Benutzers, der die letzte Replikationsaktion ausgelöst hat.
* `cq:lastReplicationAction` speichert die letzte Replikationsaktion (z. B. Aktivierung, Deaktivierung).

#### Abfragen von Replikationsmetadaten mit Standard-Prädikat-Auswertern {#querying-replication-metadata-with-default-predicate-evaluators}

Die folgende Abfrage ruft die Liste der Knoten in der `/content`-Verzweigung ab, die seit Jahresbeginn von `admin` aktiviert wurden.

```xml
path=/content

1_property=cq:lastReplicatedBy
1_property.value=admin

2_property=cq:lastReplicationAction
2_property.value=Activate

daterange.property=cq:lastReplicated
daterange.lowerBound=2013-01-01T00:00:00.000+01:00
daterange.lowerOperation=>=
```

Diese Abfrage ist zwar gültig, jedoch schwer zu lesen. Außerdem wird die Beziehung zwischen den drei Replikationseigenschaften nicht hervorgehoben. Das Implementieren eines benutzerdefinierten Prädikat-Auswerters reduziert die Komplexität und verbessert die Semantik dieser Abfrage.

#### Ziele {#objectives}

Ziel des `ReplicationPredicateEvaluator` ist die Unterstützung der obigen Abfrage durch folgende Syntax:

```xml
path=/content

replic.by=admin
replic.since=2013-01-01T00:00:00.000+01:00
replic.action=Activate
```

Durch die Gruppierung von Replikationsmetadaten wird eine aussagekräftige Abfrage mit einem benutzerdefinierten Prädikat-Evaluator ermöglicht.

#### Aktualisieren von Maven-Abhängigkeiten {#updating-maven-dependencies}

>[!TIP]
>
>Die Einrichtung neuer AEM Projekte, einschließlich der Verwendung von maven, wird im Detail durch [das WKND-Tutorial erklärt.](develop-wknd-tutorial.md)

Sie müssen zunächst die Maven-Abhängigkeiten Ihres Projekts aktualisieren. `PredicateEvaluator` ist Teil des `cq-search`-Artefakts und muss zur POM-Datei von Maven hinzugefügt werden.

>[!NOTE]
>
>Der Gültigkeitsbereich der `cq-search`-Abhängigkeit ist auf `provided` eingestellt, da `cq-search` vom `OSGi`-Container bereitgestellt wird.

Das folgende Codefragment zeigt die Unterschiede in der Datei `pom.xml` im Format [Unified Diff](https://en.wikipedia.org/wiki/Diff#Unified_format)

```text
@@ -120,6 +120,12 @@
             <scope>provided</scope>
         <dependency>
+            <groupid>com.day.cq</groupid>
+            <artifactid>cq-search</artifactid>
+            <version>5.6.4</version>
+            <scope>provided</scope>
+        </dependency>
+        <dependency>
             <groupid>junit</groupid>
             <artifactid>junit</artifactid>
             <version>3.8.1</version></dependency>
```

#### Schreiben von ReplicationPredicateEvaluator {#writing-the-replicationpredicateevaluator}

Das `cq-search`-Projekt enthält die abstrakte Klasse `AbstractPredicateEvaluator`. Dies kann um einige Schritte erweitert werden, um Ihre eigenen benutzerdefinierten Prognoseauswerter `(PredicateEvaluator` zu implementieren.

>[!NOTE]
>
>Im folgenden Abschnitt wird erläutert, wie Sie einen `Xpath`-Ausdruck zum Filtern von Daten erstellen. Eine andere Möglichkeit wäre die Implementierung der `includes`-Methode, mit der Daten auf Zeilenbasis ausgewählt werden. Weitere Informationen finden Sie in der [Java-Dokumentation](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/PredicateEvaluator.html#includes28comdaycqsearchpredicatejavaxjcrqueryrowcomdaycqsearchevalevaluationcontext29).

1. Erstellen Sie eine neue Java-Klasse zum Erweitern von `com.day.cq.search.eval.AbstractPredicateEvaluator`
1. Kommentieren Sie Ihre Klasse mit einem `@Component`-ähnlichen Codefragment in [Unified Diff-Format](https://en.wikipedia.org/wiki/Diff#Unified_format)

   ```text
   @@ -19,8 +19,11 @@
     */
    package com.adobe.aem.docs.search;
   
   +import org.apache.felix.scr.annotations.Component;
   +import com.day.cq.search.eval.AbstractPredicateEvaluator;
   
   +@Component(metatype = false, factory = "com.day.cq.search.eval.PredicateEvaluator/repli")
    public class ReplicationPredicateEvaluator extends AbstractPredicateEvaluator {
   
    }
   ```

   >[!NOTE]
   >
   >Die `factory`muss eine eindeutige Zeichenfolge sein, die mit `com.day.cq.search.eval.PredicateEvaluator/`beginnt und mit dem Namen Ihres benutzerspezifischen `PredicateEvaluator` endet.

   >[!NOTE]
   >
   >Der Name des `PredicateEvaluator` ist der Name des Prädikats, das zum Erstellen von Abfragen verwendet wird.

1. Überschreibung:

   ```java
   public String getXPathExpression(Predicate predicate, EvaluationContext context)
   ```

   Bei der Überschreibmethode erstellen Sie einen `Xpath`-Ausdruck basierend auf dem im Argument angegebenen `Predicate`.

### Beispiel für einen benutzerdefinierten Predicate-Evaluator für Replikationsmetadaten {#example-of-a-custom-predicate-evaluator-for-replication-metadata}

Die vollständige Implementierung dieses `PredicateEvaluator` kann der folgenden Klasse ähnlich sein.

```java
/*
 * #%L
 * aem-docs-custom-predicate-evaluator
 * %%
 * Copyright (C) 2013 Adobe Research
 * %%
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *      http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 * #L%
 */

package com.adobe.aem.docs.search;

import org.apache.felix.scr.annotations.Component;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.day.cq.search.Predicate;
import com.day.cq.search.eval.AbstractPredicateEvaluator;
import com.day.cq.search.eval.EvaluationContext;

@Component(metatype = false, factory = "com.day.cq.search.eval.PredicateEvaluator/repli")

public class ReplicationPredicateEvaluator extends AbstractPredicateEvaluator {

    static final String PE_NAME = "replic";


    static final String PN_LAST_REPLICATED_BY = "cq:lastReplicatedBy";
    static final String PN_LAST_REPLICATED = "cq:lastReplicated";
    static final String PN_LAST_REPLICATED_ACTION = "cq:lastReplicationAction";

    static final String PREDICATE_BY = "by";
    static final String PREDICATE_SINCE = "since";
    static final String PREDICATE_SINCE_OP = " >= ";
    static final String PREDICATE_ACTION = "action";

    Logger log = LoggerFactory.getLogger(getClass());

    /**
     * Returns a XPath expression filtering by replication metadata.
     *
     * @see com.day.cq.search.eval.AbstractPredicateEvaluator#getXPathExpression(com.day.cq.search.Predicate,
     *      com.day.cq.search.eval.EvaluationContext)
     */

    @Override

    public String getXPathExpression(Predicate predicate,
            EvaluationContext context) {

        log.debug("predicate {}", predicate);

        String date = predicate.get(PREDICATE_SINCE);
        String user = predicate.get(PREDICATE_BY);
        String action = predicate.get(PREDICATE_ACTION);

        StringBuilder sb = new StringBuilder();

        if (date != null) {

            sb.append(PN_LAST_REPLICATED).append(PREDICATE_SINCE_OP);
            sb.append("xs:dateTime('").append(date).append("')");

        }

        if (user != null) {

            addAndOperator(sb);
            sb.append(PN_LAST_REPLICATED_BY);
            sb.append("='").append(user).append("'");

        }

        if (action != null) {

            addAndOperator(sb);
            sb.append(PN_LAST_REPLICATED_ACTION);
            sb.append("='").append(action).append("'");

        }

        String xpath = sb.toString();

        log.debug("xpath **{}**", xpath);

        return xpath;

    }

    /**
     * Add an and operator if the builder is not empty.
     *
     * @param sb a {@link StringBuilder} containing the query under construction
     */

    private void addAndOperator(StringBuilder sb) {

        if (sb.length() != 0) {

            sb.append(" and ");

        }

    }

}
```
