---
title: Konfigurieren von OSGi für Adobe Experience Manager as a Cloud Service
description: OSGi-Konfiguration mit geheimen Werten und umgebungsspezifischen Werten
feature: Deploying
exl-id: f31bff80-2565-4cd8-8978-d0fd75446e15
role: Admin
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: ht
source-wordcount: '3321'
ht-degree: 100%

---


# Konfigurieren von OSGi für Adobe Experience Manager as a Cloud Service {#configuring-osgi-for-aem-as-a-cloud-service}

[OSGi](https://www.osgi.org/) ist ein wesentlicher Bestandteil der Technologien von Adobe Experience Manager (AEM). OSGi wird zur Steuerung der AEM-Bundles und ihrer Konfigurationen verwendet.

OSGi bietet standardisierte Grundbausteine – kleine, wiederverwendbare, gemeinsame genutzte Komponenten. Diese Komponenten können zu einem Programm zusammengefügt und bereitgestellt werden. Dies ermöglicht die einfache Verwaltung von OSGi-Bundles, da diese einzeln angehalten, installiert und gestartet werden können. Die gegenseitigen Abhängigkeiten werden automatisch verwaltet. Jede OSGi-Komponente ist in einem der verschiedenen Bundles enthalten. Weitere Informationen finden Sie in der [OSGi-Spezifikation](https://help.eclipse.org/latest/index.jsp).

Sie können die Konfigurationseinstellungen für OSGi-Komponenten mithilfe von Konfigurationsdateien verwalten, die Teil eines AEM-Code-Projekts sind.

>[!TIP]
>
>Sie können Cloud Manager verwenden, um Umgebungsvariablen zu konfigurieren. Weitere Informationen finden Sie in der Dokumentation [hier](/help/implementing/cloud-manager/environment-variables.md).

## OSGi-Konfigurationsdateien {#osgi-configuration-files}

Konfigurationsänderungen werden in den Code-Paketen (`ui.config`) des AEM-Projekts als Konfigurationsdateien (`.cfg.json`) unter Ausführungsmodus-spezifischen Konfigurationsordnern definiert:

`/apps/example/config.<runmode>`

Das Format der OSGi-Konfigurationsdateien ist JSON-basiert und verwendet das im Apache Sling-Projekt definierte `.cfg.json`-Format.

OSGi-Konfigurationen zielen auf OSGi-Komponenten über ihre PID (Persistent Identity) ab, die standardmäßig den Java-Klassennamen der OSGi-Komponente verwendet. Um zum Beispiel eine OSGi-Konfiguration für einen von

`com.example.workflow.impl.ApprovalWorkflow.java`

implementierten OSGi-Service bereitzustellen, wird eine OSGi-Konfigurationsdatei unter

`/apps/example/config/com.example.workflow.impl.ApprovalWorkflow.cfg.json`

nach dem `cfg.json` OSGi-Konfigurationsformat definiert.

>[!NOTE]
>
>Frühere Versionen von AEM unterstützten OSGi-Konfigurationsdateien unter Verwendung verschiedener Dateiformate wie `.cfg`, `.config` und als XML`sling:OsgiConfig`-Ressourcendefinitionen. Diese Formate werden durch das `.cfg.json`-OSGi-Konfigurationsformat ersetzt.

>[!NOTE]
>
>Die OSGi-Konfigurationen werden nicht wie typische AEM-Instanzen in Cloud unter /apps gespeichert, sondern an einem externen Speicherort. Überprüfen Sie in der [Developer Console](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console#configurations) von Cloud Manager die OSGi-Konfigurationen.

## Ausführungsmodus-Auflösung {#runmode-resolution}

>[!TIP]
>
>AEM 6.x unterstützt benutzerdefinierte Ausführungsmodi, AEM as a Cloud Service jedoch nicht. AEM as a Cloud Service unterstützt einen [exakten Satz von Ausführungsmodi](./overview.md#runmodes). Jede Änderung der OSGi-Konfigurationen zwischen Umgebungen in AEM as a Cloud Service muss mit [Variablen der OSGi-Konfigurationsumgebung](#environment-specific-configuration-values) vorgenommen werden.

Spezifische OSGi-Konfigurationen können mithilfe von Ausführungsmodi auf bestimmte AEM-Instanzen ausgerichtet werden. Um den Ausführungsmodus zu verwenden, erstellen Sie unter `/apps/example` (wobei „example“ Ihr Projektname ist) Konfigurationsordner im folgenden Format:

`/apps/example/config.<author|publish>.<dev|stage|prod>/`

Alle OSGi-Konfigurationen in diesen Ordnern werden verwendet, wenn die im config-Ordnernamen definierten Ausführungsmodi mit den von AEM verwendeten Ausführungsmodi übereinstimmen.

Wenn AEM beispielsweise die Ausführungsmodi „author“ und „dev“ verwendet, werden Konfigurationsknoten in `/apps/example/config.author/` und `/apps/example/config.author.dev/` angewendet, während Konfigurationsknoten in `/apps/example/config.publish/` und `/apps/example/config.author.stage/` nicht angewendet werden.

Wenn mehrere Konfigurationen für dieselbe PID anwendbar sind, wird die Konfiguration mit der höchsten Anzahl an passenden Ausführungsmodi angewendet.

Die Granularität dieser Regel liegt auf PID-Ebene. Es ist daher nicht möglich, für dieselbe PID einige Eigenschaften in `/apps/example/config.author/` und spezifischere in `/apps/example/config.author.dev/` zu definieren. Die Konfiguration mit der höchsten Anzahl von übereinstimmenden Ausführungsmodi ist für die gesamte PID wirksam.

>[!NOTE]
>
>Ein `config.preview`-OSG-Konfigurationsordner kann **nicht** auf dieselbe Weise deklariert werden, wie `config.publish` als Ordner deklariert werden kann. Stattdessen übernimmt die Vorschauebene ihre OSGi-Konfiguration von den Werten der Veröffentlichungsebene.

Bei der lokalen Entwicklung wird ein Ausführungsmodus-Startparameter `-r` verwendet, um die OSGi-Konfiguration für den Ausführungsmodus anzugeben.

```shell
$ java -jar aem-sdk-quickstart-xxxx.x.xxx.xxxx-xxxx.jar -r publish,dev
```

### Überprüfen der Ausführungsmodi

Ausführungsmodi von AEM as a Cloud Service sind basierend auf dem Umgebungstyp und Service klar definiert. Überprüfen Sie die [vollständige Liste der verfügbaren Ausführungsmodi von AEM as a Cloud Service](./overview.md#runmodes).

Die vom Ausführungsmodus bestimmten OSGi-Konfigurationswerte können wie folgt überprüft werden:

1. Öffnen der [Entwicklerkonsole](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=de) für die Umgebung in AEM as a Cloud Service
1. Auswählen der zu prüfenden Service-Ebene(n) mithilfe des Dropdown-Menüs __Pod__
1. Auswählen der Registerkarte __Status__
1. Auswählen von __Konfigurationen__ im Dropdown-Menü __Status-Dump__
1. Auswählen der Schaltfläche __Status abrufen__

In der resultierenden Ansicht werden alle OSGi-Komponentenkonfigurationen für die ausgewählte(n) Ebene(n) mit den entsprechenden OSGi-Konfigurationswerten angezeigt. Diese Werte können mit den OSGi-Konfigurationswerten im Quellcode des AEM-Projekts unter `/apps/example/osgiconfig/config.<runmode(s)>` abgeglichen werden.


So überprüfen Sie, ob die entsprechenden OSGi-Konfigurationswerte angewendet werden:

1. In der Konfigurationsausgabe der Entwicklerkonsole:
1. Suchen Sie die `pid` für die zu überprüfende OSGi-Konfiguration. Dies ist der Name der OSGi-Konfigurationsdatei im Quell-Code des AEM-Projekts.
1. Sehen Sie in der `properties`-Liste für die `pid` nach, ob der Schlüssel und die Werte mit der OSGi-Konfigurationsdatei im Quell-Code des AEM Projekts für den zu verifizierenden Ausführungsmodus übereinstimmen.


## Typen von OSGi-Konfigurationswerten {#types-of-osgi-configuration-values}

Es gibt drei verschiedene OSGi-Konfigurationswerte, die mit Adobe Experience Manager as a Cloud Service verwendet werden können.

1. **Inline-Werte**, d. h. Werte, die in der OSGi-Konfiguration fest codiert und in Git gespeichert werden. Zum Beispiel:

   ```json
   {
      "connection.timeout": 1000
   }
   ```

1. **Geheime Werte**, d. h. Werte, die aus Sicherheitsgründen nicht in Git gespeichert werden dürfen. Zum Beispiel:

   ```json
   {
   "api-key": "$[secret:server-api-key]"
   } 
   ```

1. **Umgebungsspezifische Werte**, also Werte, die von Entwicklungsumgebung zu Entwicklungsumgebung variieren und vom Ausführungsmodus nicht genau anvisiert werden können (da es in Adobe Experience Manager as a Cloud Service einen einzigen `dev`-Ausführungsmodus gibt). Zum Beispiel:

   ```json
   {
    "url": "$[env:server-url]"
   }
   ```

   Eine einzelne OSGi-Konfigurationsdatei kann eine beliebige Kombination dieser Konfigurationswerttypen gleichzeitig verwenden. Zum Beispiel:

   ```json
   {
   "connection.timeout": 1000,
   "api-key": "$[secret:server-api-key]",
   "url": "$[env:server-url]"
   }
   ```

## Auswählen des entsprechenden OSGi-Konfigurationswerttyps {#how-to-choose-the-appropriate-osgi-configuration-value-type}

Normalerweise werden für OSGi Inline-OSGi-Konfigurationswerte verwendet. Umgebungsspezifische Konfigurationen werden nur für bestimmte Anwendungsfälle verwendet, in denen sich ein Wert zwischen Entwicklungsumgebungen unterscheidet.

![Entscheidungsstruktur für die Verwendung des richtigen Konfigurationswerttyps](assets/choose-configuration-value-type_res1.png)

Umgebungsspezifische Konfigurationen erweitern die traditionellen, statisch definierten OSGi-Konfigurationen, die Inline-Werte enthalten, und bieten die Möglichkeit, die OSGi-Konfigurationswerte extern über die Cloud Manager-API zu verwalten. Es ist wichtig zu verstehen, wann der übliche und traditionelle Ansatz zum Definieren und Speichern von Inline-Werten in Git verwendet werden sollte, anstatt die Werte in umgebungsspezifischen Konfigurationen zu abstrahieren.

In den folgenden Anleitungen wird beschrieben, wann nicht geheime und geheime umgebungsspezifische Konfigurationen verwendet werden müssen:

### Verwendung von Inline-Konfigurationswerten {#when-to-use-inline-configuration-values}

Inline-Konfigurationswerte werden als Standardansatz betrachtet und sollten nach Möglichkeit verwendet werden. Inline-Konfigurationen bieten folgende Vorteile:

* Sie werden mit Governance und Versionsverlauf in Git aufbewahrt.
* Werte sind implizit an Code-Bereitstellungen gebunden.
* Sie erfordern keine zusätzlichen Überlegungen zur Bereitstellung oder Koordinierung.

Beginnen Sie bei der Definition eines OSGi-Konfigurationswerts mit Inline-Werten und wählen Sie nur geheime oder umgebungsspezifische Konfigurationen aus, wenn dies für den Anwendungsfall erforderlich ist.

### Verwendung nicht geheimer umgebungsspezifischer Konfigurationswerte {#when-to-use-non-secret-environment-specific-configuration-values}

Verwenden Sie nur umgebungsspezifische Konfigurationen (`$[env:ENV_VAR_NAME]`) für nicht geheime Konfigurationswerte, wenn die Werte für die Vorschauebene variieren oder in den Entwicklungsumgebungen variieren. Dazu gehören lokale Entwicklungsinstanzen und alle Entwicklungsumgebungen von Adobe Experience Manager as a Cloud Service. Vermeiden Sie außer zum Festlegen eindeutiger Werte für die Vorschauebene die Verwendung nicht geheimer umgebungsspezifischer Konfigurationen für Adobe Experience Manager as a Cloud Service-Staging- oder -Produktionsumgebungen.

* Verwenden Sie nicht geheime umgebungsspezifische Konfigurationen nur für Konfigurationswerte, die sich zwischen Veröffentlichungs- und Vorschauebene unterscheiden, oder für Werte, die sich zwischen Entwicklungsumgebungen, einschließlich lokaler Entwicklungsinstanzen, unterscheiden.
* Verwenden Sie abgesehen von dem Szenario, in dem die Vorschauebene von der Veröffentlichungsebene abweichen muss, die standardmäßigen Inline-Werte in den OSGi-Konfigurationen für nicht geheime Werte der Staging- und Produktionsumgebung. In diesem Zusammenhang wird von der Verwendung umgebungsspezifischer Konfigurationen abgeraten, um die Durchführung von Konfigurationsänderungen zur Laufzeit in Staging- und Produktionsumgebungen zu erleichtern. Diese Änderungen sollten über die Quell-Code-Verwaltung eingeführt werden.

### Verwendung geheimer umgebungsspezifischer Konfigurationswerte {#when-to-use-secret-environment-specific-configuration-values}

Adobe Experience Manager as a Cloud Service erfordert die Verwendung umgebungsspezifischer Konfigurationen (`$[secret:SECRET_VAR_NAME]`) für geheime OSGi-Konfigurationswerte wie Passwörter, private API-Schlüssel oder andere Werte, die aus Sicherheitsgründen nicht in Git gespeichert werden können.

Verwenden Sie geheime umgebungsspezifische Konfigurationen, um den Wert für Geheimnisse in allen Adobe Experience Manager as a Cloud Service-Umgebungen zu speichern, einschließlich Staging- und Produktionsumgebungen.

## Erstellen von OSGi-Konfigurationen {#creating-osgi-configurations}

Es gibt zwei Möglichkeiten, OSGi-Konfigurationen zu erstellen, wie unten beschrieben. Der erste Ansatz wird typischerweise für die Konfiguration von benutzerdefinierten OSGi-Komponenten verwendet, die dem Entwickler bekannte OSGi-Eigenschaften und -Werte haben, und der zweite für von AEM bereitgestellte OSGi-Komponenten.

### Schreiben von OSGi-Konfigurationen {#writing-osgi-configurations}

OSGi-Konfigurationsdateien im JSON-Format können manuell direkt im AEM-Projekt geschrieben werden. Dies ist häufig die schnellste Möglichkeit, OSGi-Konfigurationen für bekannte OSGi-Komponenten und insbesondere benutzerdefinierte OSGi-Komponenten zu erstellen, die von demselben Entwickler entworfen und entwickelt wurden, der die Konfigurationen definiert. Dieser Ansatz kann auch genutzt werden, um Konfigurationen für dieselbe OSGi-Komponente in verschiedenen Ausführungsmodus-Ordnern zu kopieren, einzufügen und zu aktualisieren.

1. Öffnen Sie in Ihrer IDE das `ui.apps`-Projekt, suchen oder erstellen Sie den Konfigurationsordner (`/apps/.../config.<runmode>`), der für die Ausführungsmodi bestimmt ist, auf die die neue OSGi-Konfiguration wirken soll.
1. Erstellen Sie in diesem Konfigurationsordner eine `<PID>.cfg.json`-Datei. Die PID ist die persistente Identität der OSGi-Komponente. Normalerweise ist dies der vollständige Klassenname der OSGi-Komponentenimplementierung. Zum Beispiel:
   `/apps/.../config/com.example.workflow.impl.ApprovalWorkflow.cfg.json`
Die Werksdateinamen der OSGi-Konfiguration verwenden die `<factoryPID>-<name>.cfg.json`-Namenskonvention.
1. Öffnen Sie die neue `.cfg.json`-Datei und definieren Sie die Schlüssel/Wert-Kombinationen für die OSGi-Eigenschafts- und -Wertpaare entsprechend dem [JSON OSGi-Konfigurationsformat](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-cfgjson-1).
1. Speichern Sie Ihre Änderungen in der neuen `.cfg.json`-Datei
1. Fügen Sie Ihre neue OSGi-Konfigurationsdatei hinzu und übertragen Sie sie auf Git

### Generieren von OSGi-Konfigurationen mit AEM SDK QuickStart {#generating-osgi-configurations-using-the-aem-sdk-quickstart}

Die AEM Web-Konsole von AEM SDK QuickStart Jar kann verwendet werden, um OSGi-Komponenten zu konfigurieren und OSGi-Konfigurationen als JSON zu exportieren. Dies ist nützlich, um von AEM bereitgestellte OSGi-Komponenten zu konfigurieren, deren OSGi-Eigenschaften und deren Werteformate vom Entwickler, der die OSGi-Konfigurationen im AEM-Projekt definiert, möglicherweise nicht gut verstanden werden.

>[!NOTE]
>
>Die Konfigurationsoberfläche der AEM Web-Konsole schreibt `.cfg.json`-Dateien in das Repository. Beachten Sie daher diesen Workflow, um potenziell unerwartetes Verhalten während der lokalen Entwicklung zu vermeiden, wenn die vom AEM-Projekt definierten OSGi-Konfigurationen von den generierten Konfigurationen abweichen können.

1. Melden Sie sich bei der AEM-Web-Konsole von AEM SDK Quickstart Jar unter `https://<host>:<port>/system/console` als Admin-Benutzerin bzw. -Benutzer an.
1. Navigieren Sie zu **OSGi** > **Konfiguration**
1. Zur Konfiguration suchen Sie die OSGi-Komponente und wählen Sie den Titel zum Bearbeiten aus.
   ![OSGi-Konfiguration](./assets/configuring-osgi/configuration.png)
1. Bearbeiten Sie die OSGi-Konfigurationseigenschaftswerte nach Bedarf über die Web-Benutzeroberfläche
1. Bewahren Sie die PID (Persistent Identity) an einem sicheren Ort auf. Diese wird später zum Generieren der OSGi-Konfigurations-JSON verwendet.
1. Wählen Sie „Speichern“ aus
1. Gehen Sie zu „OSGi“ > „OSGi Installer-Konfigurationsdrucker“
1. Fügen Sie die in Schritt 5 kopierte PID ein. Stellen Sie sicher, dass das Serialisierungsformat auf „OSGi Configurator JSON“ eingestellt ist
1. Wählen Sie „Drucken“ aus
1. Die OSGi-Konfiguration im JSON-Format wird im Abschnitt „Serialisierte Konfigurationseigenschaften“ angezeigt
   ![OSGi Installer-Konfigurationsdrucker](./assets/configuring-osgi/osgi-installer-configurator-printer.png)
1. Öffnen Sie in Ihrer IDE das `ui.apps`-Projekt, suchen oder erstellen Sie den Konfigurationsordner (`/apps/.../config.<runmode>`), der für die Ausführungsmodi bestimmt ist, auf die die neue OSGi-Konfiguration wirken soll.
1. Erstellen Sie in diesem Konfigurationsordner eine `<PID>.cfg.json`-Datei. Die PID ist der Wert aus Schritt 5.
1. Fügen Sie die serialisierten Konfigurationseigenschaften aus Schritt 10 in die `.cfg.json`-Datei ein.
1. Speichern Sie Ihre Änderungen in der neuen `.cfg.json`-Datei.
1. Fügen Sie Ihre neue OSGi-Konfigurationsdatei hinzu und übertragen Sie sie auf Git.


## OSGi-Konfigurationseigenschaftsformate {#osgi-configuration-property-formats}

### Inline-Werte {#inline-values}

Inline-Werte werden gemäß der standardmäßigen JSON-Syntax als Name-Wert-Paare formatiert. Zum Beispiel:

```json
{
   "my_var1": "val",
   "my_var2": [ "abc", "def" ],
   "my_var3": 500
}
```

### Umgebungsspezifische Konfigurationswerte {#environment-specific-configuration-values}

Die OSGi-Konfiguration sollte einen Platzhalter für die Variable zuweisen, die pro Umgebung definiert werden soll:

```
use $[env:ENV_VAR_NAME]
```

Kundinnen und Kunden sollten diese Technik nur für OSGI-Konfigurationseigenschaften im Zusammenhang mit ihrem benutzerdefinierten Code verwenden. Sie darf nicht verwendet werden, um die von Adobe definierte OSGI-Konfiguration zu überschreiben.

>[!NOTE]
>
>Platzhalter können nicht in [repoinit-Anweisungen](/help/implementing/deploying/overview.md#repoinit) verwendet werden.

### Geheime Konfigurationswerte {#secret-configuration-values}

Die OSGi-Konfiguration sollte einen Platzhalter für das Geheimnis zuweisen, das pro Umgebung definiert werden soll:

```
use $[secret:SECRET_VAR_NAME]
```

### Variablenbenennung {#variable-naming}

Folgendes gilt sowohl für umgebungsspezifische als auch für geheime Konfigurationswerte.

Variablennamen müssen die folgenden Regeln befolgen:

* Mindestlänge: 2
* Maximale Länge: 100
* Müssen mit Regex übereinstimmen: `[a-zA-Z_][a-zA-Z_0-9]*`

Die Variablenwerte dürfen 2048 Zeichen nicht überschreiten.

>[!CAUTION]
>
>Es gibt Regeln für die Verwendung bestimmter Präfixe für Variablennamen:
>
>1. Variablennamen, die mit dem Präfix `INTERNAL_`, `ADOBE_` oder `CONST_` beginnen, sind durch Adobe reserviert. Alle kundenseitig festgelegten Variablen, die mit diesen Präfixen beginnen, werden ignoriert.
>
>1. Kunden dürfen keine Variablen referenzieren, die das Präfix `INTERNAL_` oder `ADOBE_` haben.
>
>1. Umgebungsvariablen mit dem Präfix `AEM_` werden vom Produkt als öffentliche API definiert, die von Kunden verwendet und festgelegt wird.
>   Während Kunden Umgebungsvariablen verwenden und festlegen können, die mit dem Präfix `AEM_` beginnen, sollten sie keine eigenen Variablen mit diesem Präfix definieren.

### Standardwerte {#default-values}

Folgendes gilt sowohl für umgebungsspezifische als auch für geheime Konfigurationswerte.

Wenn kein Wert pro Umgebung festgelegt ist, wird der Platzhalter zur Laufzeit nicht ersetzt und an Ort und Stelle belassen, da keine Interpolation stattgefunden hat. Um dies zu vermeiden, kann ein Standardwert als Teil des Platzhalters mit der folgenden Syntax bereitgestellt werden:

```
$[env:ENV_VAR_NAME;default=<value>]
```

Wenn ein Standardwert angegeben ist, wird der Platzhalter entweder durch den pro Umgebung angegebenen Wert oder durch den bereitgestellten Standardwert ersetzt.

### Lokale Entwicklung {#local-development}

Folgendes gilt sowohl für umgebungsspezifische als auch für geheime Konfigurationswerte.

Variablen können in der lokalen Umgebung definiert werden, damit sie zur Laufzeit von der lokalen AEM-Instanz abgerufen werden. Zum Beispiel unter Linux®:

```bash
export ENV_VAR_NAME=my_value
```

Es wird empfohlen, ein einfaches Bash-Skript zu schreiben, das die in den Konfigurationen verwendeten Umgebungsvariablen festlegt, und dieses Skript vor dem Starten von AEM auszuführen. Tools wie [https://direnv.net/](https://direnv.net/) helfen bei der Vereinfachung dieses Ansatzes. Abhängig vom Typ der Werte können sie in die Quell-Code-Verwaltung eingecheckt werden, wenn sie von allen gemeinsam genutzt werden können.

Die Werte für Geheimnisse werden aus Dateien gelesen. Daher muss für jeden Platzhalter, der einen geheimen Schlüssel verwendet, eine Textdatei mit dem geheimen Wert erstellt werden.

Wenn beispielsweise `$[secret:server_password]` verwendet wird, muss eine Textdatei mit dem Namen **server_password** erstellt werden. Alle diese geheimen Dateien müssen im selben Ordner gespeichert werden, und die Framework-Eigenschaft `org.apache.felix.configadmin.plugin.interpolation.secretsdir` muss mit diesem lokalen Ordner konfiguriert werden.

>[!CAUTION]
>
>Dateierweiterungen sind für die Textdatei nicht zulässig.
>
>Für das obige Beispiel muss die Textdatei also **server_password** heißen (ohne Dateierweiterung).

`org.apache.felix.configadmin.plugin.interpolation.secretsdir` ist eine Sling-Framework-Eigenschaft. Diese Eigenschaft wird nicht in der Felix-Konsole (/system/console) festgelegt, sondern in der Datei „sling.properties“, die beim Starten des Systems verwendet wird. Diese Datei finden Sie im Unterverzeichnis „/conf“ des extrahierten Ordners „Jar/install“ (crx-quickstart/conf).

Beispiel: Fügen Sie diese Zeile am Ende der Datei „crx-quickstart/conf/sling.properties“ hinzu, um „crx-quickstart/secretsdir“ als geheimen Ordner zu konfigurieren:

```
org.apache.felix.configadmin.plugin.interpolation.secretsdir=${sling.home}/secretsdir
```

### Vergleich von Autoren- und Veröffentlichungskonfiguration {#author-vs-publish-configuration}

Wenn eine OSGi-Eigenschaft unterschiedliche Werte für Autoren- und Veröffentlichungsumgebung erfordert:

* Es müssen getrennte `config.author`- und `config.publish`-OSGi-Ordner verwendet werden, wie im [Abschnitt zur Ausführungsmodus-Auflösung](#runmode-resolution) beschrieben.
* Es gibt zwei Möglichkeiten, unabhängige Variablennamen zu erstellen:
   * Die erste Option, die empfohlen wird: Verwenden Sie in allen OSGi-Ordnern (z. B. `config.author` und `config.publish`), die dazu deklariert sind, unterschiedliche Werte zu definieren, denselben Variablennamen. Beispiel
     `$[env:ENV_VAR_NAME;default=<value>]`, wobei der Standardwert dem Standardwert für diese Ebene (Autor oder Veröffentlichung) entspricht. Beim Festlegen der Umgebungsvariablen über die [Cloud Manager-API](#cloud-manager-api-format-for-setting-properties) oder einen Client sollten Sie mithilfe des Parameters „service“ zwischen den Ebenen unterscheiden, wie in der [Cloud Manager API-Referenzdokumentation](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/) beschrieben. Der Parameter „service“ bindet den Wert der Variablen an die entsprechende OSGi-Ebene. Es kann „author“, „publish“ oder „preview“ sein.
   * Die zweite Option besteht darin, mithilfe eines Präfixes wie `author_<samevariablename>` und `publish_<samevariablename>` eindeutige Variablen zu deklarieren.

### Konfigurationsbeispiele {#configuration-examples}

Gehen Sie in den folgenden Beispielen davon aus, dass es neben der Staging- und der Produktionsumgebung drei Entwicklungsumgebungen gibt.

**Beispiel 1**

Der Wert der OSGi-Eigenschaft `my_var1` soll für die Staging- und die Produktionsumgebung gleich und für jede der drei Entwicklungsumgebungen unterschiedlich sein.

<table>
<tr>
<td>
<b>Ordner</b>
</td>
<td>
<b>Inhalt von myfile.cfg.json</b>
</td>
</tr>
<tr>
<td>
config
</td>
<td>
<pre>
{ 
 "my_var1": "val",
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ 
 "my_var1" : "$[env:my_var1]"
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
</table>

**Beispiel 2**

Der Wert der OSGi-Eigenschaft `my_var1` soll für die Staging-, Produktions- und für jede der drei Entwicklungsumgebungen unterschiedlich sein. Daher muss die Cloud Manager-API aufgerufen werden, um den Wert für `my_var1` für jede Entwicklungsumgebung festzulegen.

<table>
<tr>
<td>
<b>Ordner</b>
</td>
<td>
<b>Inhalt von myfile.cfg.json</b>
</td>
</tr>
<tr>
<td>
config.stage
</td>
<td>
<pre>
{ 
 "my_var1": "val1",
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
<tr>
<td>
config.prod
</td>
<td>
<pre>
{ 
 "my_var1": "val2",
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ 
 "my_var1" : "$[env:my_var1]"
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
</table>

**Beispiel 3**

Der Wert der OSGi-Eigenschaft `my_var1` soll für die Staging-, Produktions- und eine der Entwicklungsumgebungen gleich und für die anderen zwei Entwicklungsumgebungen unterschiedlich sein. In diesem Fall muss die Cloud Manager-API aufgerufen werden, um den Wert von `my_var1` für jede Entwicklungsumgebung festzulegen, einschließlich der Entwicklungsumgebung, die denselben Wert wie die Staging- und die Produktionsumgebung haben soll. Der im Ordner **config** festgelegte Wert wird nicht vererbt.

<table>
<tr>
<td>
<b>Ordner</b>
</td>
<td>
<b>Inhalt von myfile.cfg.json</b>
</td>
</tr>
<tr>
<td>
config
</td>
<td>
<pre>
{ 
 "my_var1": "val1",
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ 
 "my_var1" : "$[env:my_var1]"
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
</table>

Eine andere Möglichkeit, dies zu erreichen, besteht darin, einen Standardwert für das Ersatz-Token im Ordner „config.dev“ so festzulegen, dass er denselben Wert wie im Ordner **config** hat.

<table>
<tr>
<td>
<b>Ordner</b>
</td>
<td>
<b>Inhalt von myfile.cfg.json</b>
</td>
</tr>
<tr>
<td>
config
</td>
<td>
<pre>
{ 
 "my_var1": "val1",
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ 
 "my_var1": "$[env:my_var1;default=val1]"
 "my_var2": "abc",
 "my_var3": 500
}
</pre>
</td>
</tr>
</table>

## Cloud Manager-API-Format zum Festlegen von Eigenschaften {#cloud-manager-api-format-for-setting-properties}

Informationen zur Cloud Manager-API und deren Konfiguration finden Sie unter [Adobe Cloud Manager auf der Adobe Developer-Website](https://developer.adobe.com/experience-cloud/cloud-manager/docs/).

>[!NOTE]
>
>Stellen Sie sicher, dass der verwendeten Cloud Manager-API die Rolle „Bereitstellungs-Manager - Cloud Service“ zugewiesen wurde. Andere Rollen können nicht alle folgenden Befehle ausführen.

>[!TIP]
>
>Sie können auch Cloud Manager verwenden, um Umgebungsvariablen zu konfigurieren. Weitere Informationen finden Sie unter [Cloud Manager-Umgebungsvariablen](/help/implementing/cloud-manager/environment-variables.md).

### Festlegen von Werten über API {#setting-values-via-api}

Durch den Aufruf der API werden die neuen Variablen und Werte in einer Cloud-Umgebung bereitgestellt, ähnlich wie bei einer typischen Bereitstellungs-Pipeline für Kunden-Code. Die Authoring- und Publishing-Services werden neu gestartet und verweisen auf die neuen Werte. Dies dauert normalerweise einige Minuten.

```
PATCH /program/{programId}/environment/{environmentId}/variables
```

```json
[
        {
                "name" : "MY_VAR1",
                "value" : "plaintext value",
                "type" : "string"  <---default
        },
        {
                "name" : "MY_VAR2",
                "value" : "<secret value>",
                "type" : "secretString"
        }
]
```

>[!NOTE]
>Die Standardvariablen werden nicht über die API festgelegt, sondern in der OSGi-Eigenschaft selbst.
>
>Weitere Informationen finden Sie unter [Cloud Manager-API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/).

### Abrufen von Werten über API {#getting-values-via-api}

```
GET /program/{programId}/environment/{environmentId}/variables
```

Weitere Informationen finden Sie unter [Cloud Manager-API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/).

### Löschen von Werten über API {#deleting-values-via-api}

```
PATCH /program/{programId}/environment/{environmentId}/variables
```

Um eine Variable zu löschen, fügen Sie sie mit einem leeren Wert ein.

Weitere Informationen finden Sie unter [Cloud Manager-API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/).

### Abrufen von Werten über die Befehlszeile {#getting-values-via-cli}

```bash
$ aio cloudmanager:list-environment-variables ENVIRONMENT_ID
Name     Type         Value
MY_VAR1  string       plaintext value 
MY_VAR2  secretString ****
```


### Festlegen von Werten über die Befehlszeile {#setting-values-via-cli}

```bash
$ aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable MY_VAR1 "plaintext value" --secret MY_VAR2 "some secret value"
```

### Löschen von Werten über die Befehlszeile {#deleting-values-via-cli}

```bash
$ aio cloudmanager:set-environment-variables ENVIRONMENT_ID --delete MY_VAR1 MY_VAR2
```

>[!NOTE]
>
>Weitere Informationen zum Konfigurieren von Werten mithilfe des Cloud Manager-Plug-ins für Adobe I/O CLI finden Sie unter [aio-cli-plugin-cloudmanager auf GitHub](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid).

### Anzahl der Variablen {#number-of-variables}

Pro Umgebung können bis zu 200 Variablen deklariert werden.

## Bereitstellungsaspekte für geheime und umgebungsspezifische Konfigurationswerte {#deployment-considerations-for-secret-and-environment-specific-configuration-values}

Da die geheimen und umgebungsspezifischen Konfigurationswerte außerhalb von Git bestehen und daher nicht Teil der formellen Adobe Experience Manager as a Cloud Service-Bereitstellungsmechanismen sind, sollte der Kunde sie verwalten, steuern und in den Adobe Experience Manager as a Cloud Service-Bereitstellungsprozess integrieren.

Wie oben erwähnt, werden durch den Aufruf der API die neuen Variablen und Werte in Cloud-Umgebungen bereitgestellt, ähnlich wie bei einer typischen Bereitstellungs-Pipeline für Kunden-Code. Die Authoring- und Publishing-Services werden neu gestartet und verweisen auf die neuen Werte. Dies dauert normalerweise einige Minuten. Die Qualitäts-Gates und Tests, die von Cloud Manager während einer regulären Code-Bereitstellung ausgeführt werden, werden während dieses Prozesses nicht ausgeführt.

Normalerweise würden Kunden die API aufrufen, um Umgebungsvariablen zu setzen, bevor sie Code bereitstellen, der sich in Cloud Manager auf diese Variablen verlässt. In einigen Situationen kann es sinnvoll sein, eine vorhandene Variable zu ändern, nachdem der Code bereits bereitgestellt wurde.

>[!NOTE]
>
>Die API ist möglicherweise nicht erfolgreich, wenn eine Pipeline verwendet wird. Es läuft entweder ein AEM-Update oder eine Kundenbereitstellung, je nachdem, welcher Teil der End-to-End-Pipeline zu diesem Zeitpunkt ausgeführt wird. Die Fehlerantwort zeigt an, dass die Anfrage nicht erfolgreich war, obwohl sie den spezifischen Grund nicht angibt.

Es kann Situationen geben, in denen sich eine geplante Bereitstellung von Kunden-Code darauf verlässt, dass vorhandene Variablen neue Werte haben, die mit dem aktuellen Code nicht übereinstimmen würden. Wenn dies ein Problem darstellt, wird empfohlen, variable Änderungen auf additive Weise vorzunehmen. Erstellen Sie dazu neue Variablennamen, anstatt nur den Wert alter Variablen zu ändern, sodass der alte Code nie auf den neuen Wert verweist. Wenn die neue Kundenversion dann stabil aussieht, können Sie die älteren Werte entfernen.

Da die Werte einer Variablen nicht versioniert sind, kann ein Rollback des Codes dazu führen, dass sie auf neuere Werte verweisen, die Probleme verursachen. Auch hier würde die zuvor erwähnte additive Variablenstrategie helfen.

Diese additive Variablenstrategie ist auch für Disaster-Recovery-Szenarien nützlich, bei denen die Variablennamen und -werte, auf die sie verweisen, auch dann noch intakt sind, wenn Code von mehreren Tagen zuvor erneut bereitgestellt werden musste. Dies beruht auf einer Strategie, bei der ein Kunde einige Tage wartet, bevor er diese älteren Variablen entfernt. Andernfalls hätte der ältere Code keine geeigneten Variablen, auf die er verweisen könnte.
