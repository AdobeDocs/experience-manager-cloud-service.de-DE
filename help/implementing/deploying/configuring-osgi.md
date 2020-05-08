---
title: OSGi für AEM als Cloud-Dienst konfigurieren
description: 'OSGi-Konfiguration mit geheimen Werten und Umgebung-spezifischen Werten '
translation-type: tm+mt
source-git-commit: 2ab998c7acedecbe0581afe869817a9a56ec5474
workflow-type: tm+mt
source-wordcount: '2689'
ht-degree: 4%

---


# OSGi für AEM als Cloud-Dienst konfigurieren {#configuring-osgi-for-aem-as-a-cloud-service}

[OSGi ist ein wesentlicher Bestandteil der Technologien von Adobe Experience Manager (AEM). ](https://www.osgi.org/) Es wird zur Steuerung der Composite-Bundles von AEM und seinen Konfigurationen verwendet.

OSGi bietet die standardisierten Primitive, mit denen Anwendungen aus kleinen, wiederverwendbaren und kollaborativen Komponenten aufgebaut werden können. Diese Komponenten können in einer Anwendung zusammengestellt und bereitgestellt werden. Dies ermöglicht eine einfache Verwaltung der OSGi-Pakete, da diese einzeln angehalten, installiert und gestartet werden können. Die gegenseitigen Abhängigkeiten werden automatisch verwaltet. Jede OSGi-Komponente ist in einem der verschiedenen Pakete enthalten. Weitere Informationen finden Sie in der [OSGi-Spezifikation](https://www.osgi.org/Specifications/HomePage).

Sie können die Konfigurationseinstellungen für OSGi-Komponenten mithilfe von Konfigurationsdateien verwalten, die Teil eines AEM-Codeprojekts sind.

## OSGi-Konfigurationsdateien {#osgi-configuration-files}

Konfigurationsänderungen werden in den Codepaketen (`ui.apps`) des AEM-Projekts als Konfigurationsdateien (`.cfg.json`) unter runmode-spezifischen Konfigurationsordnern definiert:

`/apps/example/config.<runmode>`

Das Format der OSGi-Konfigurationsdateien ist JSON-basiert und verwendet das vom Apache Sling-Projekt definierte `.cfg.json` Format.

OSGi-Konfigurationen Zielgruppe OSGi-Komponenten über ihre Persistent Idenity (PID), die standardmäßig den Java-Klassennamen der OSGi-Komponente verwendet. So stellen Sie beispielsweise die OSGi-Konfiguration für einen OSGi-Dienst bereit, der implementiert wird von:

`com.example.workflow.impl.ApprovalWorkflow.java`

Eine OSGi-Konfigurationsdatei wird definiert unter:

`/apps/example/config/com.example.workflow.impl.ApprovalWorkflow.cfg.json`

dem Konfigurationsformat cfg.json OSGi folgen.

> [!NOTE]
>
> Frühere Versionen von AEM unterstützten OSGi-Konfigurationsdateien unter Verwendung verschiedener Dateiformate wie .cfg., .config und als XML sling:OsgiConfig-Ressourcendefinitionen. Diese Formate werden durch das Konfigurationsformat cfg.json OSGi ersetzt.

## Runmode-Auflösung {#runmode-resolution}

Spezifische OSGi-Konfigurationen können mithilfe von Runmodi auf bestimmte AEM-Instanzen ausgerichtet werden. Um den Ausführungsmodus zu verwenden, erstellen Sie Konfigurationsordner im folgenden Format unter `/apps/example` (wo beispielsweise Ihr Projektname steht):

`/apps/example/config.<author|publish>.<dev|stage|prod>/`

Alle OSGi-Konfigurationen in diesen Ordnern werden verwendet, wenn die im Konfigurationsordnernamen definierten Ausführungsmodi mit den von AEM verwendeten Ausführungsmodi übereinstimmen.

Wenn AEM beispielsweise den Parameter &quot;author&quot;und &quot;dev&quot;verwendet, werden Konfigurationsknoten in `/apps/example/config.author/` und `/apps/example/config.author.dev/` angewendet, während Konfigurationsknoten in `/apps/example/config.publish/` `/apps/example/config.author.stage/` und nicht angewendet werden.

Wenn mehrere Konfigurationen für dieselbe PID anwendbar sind, wird die Konfiguration mit der höchsten Anzahl an passenden Ausführungsmodi angewendet.

Die Granularität dieser Regel liegt auf PID-Ebene. This means you cannot define some properties for the same PID in `/apps/example/config.author/` and more specific ones in `/apps/example/config.author.dev/` for the same PID.  Die Konfiguration mit der höchsten Anzahl übereinstimmender Ausführungsmodi ist für die gesamte PID wirksam.

Bei der lokalen Entwicklung kann ein Runmode-Startparameter übergeben werden, um anzugeben, welche Runmode-OSGI-Konfiguration verwendet werden soll.

## Typen von OSGi-Konfigurationswerten {#types-of-osgi-configuration-values}

Es gibt drei verschiedene OSGi-Konfigurationswerte, die mit AEM als Cloud-Dienst verwendet werden können.

1. **Inline-Werte**, d. h. Werte, die in der OSGi-Konfiguration fest codiert und in Git gespeichert werden. Beispiel:

   ```json
   {
      "connection.timeout": 1000
   }
   ```

1. **Geheime Werte**, die Werte sind, die aus Sicherheitsgründen nicht in Git gespeichert werden sollten. Beispiel:

   ```json
   {
   "api-key": "$[secret:server-api-key]"
   } 
   ```

1. **Umgebung-spezifische Werte**, die sich von Umgebung zu  unterscheiden und daher nicht genau auf den Ausführungsmodus ausgerichtet werden können (da es in AEM als Cloud-Dienst einen einzelnen `dev` Ausführungsmodus gibt). Beispiel:

   ```json
   {
    "url": "$[env:server-url]"
   }
   ```

   Beachten Sie, dass eine einzelne OSGi-Konfigurationsdatei eine beliebige Kombination dieser Konfigurationswerttypen zusammen verwenden kann. Beispiel:

   ```json
   {
   "connection.timeout": 1000,
   "api-key": "$[secret:server-api-key]",
   "url": "$[env:server-url]"
   }
   ```

## Auswählen des entsprechenden OSGi-Konfigurationswerttyps {#how-to-choose-the-appropriate-osgi-configuration-value-type}

Der gängige Fall für OSGi verwendet Inline-OSGi-Konfigurationswerte. Umgebung-spezifische Konfigurationen werden nur für spezifische Anwendungsfälle verwendet, bei denen sich ein Wert zwischen dev-Umgebung unterscheidet.

![](assets/choose-configuration-value-type_res1.png)

Umgebung-spezifische Konfigurationen erweitern die herkömmlichen, statisch definierten OSGi-Konfigurationen, die Inline-Werte enthalten, und ermöglichen so die externe Verwaltung der OSGi-Konfigurationswerte über die Cloud Manager-API. Es ist wichtig zu verstehen, wann der gängige und herkömmliche Ansatz der Definition von Inline-Werten und deren Speicherung in Git verwendet werden sollte, anstatt die Werte in Umgebung-spezifische Konfigurationen abzustrahieren.

In den folgenden Leitlinien wird beschrieben, wann nicht geheime und geheime Umgebung-spezifische Konfigurationen verwendet werden sollen:

### Verwendung von Inline-Konfigurationswerten {#when-to-use-inline-configuration-values}

Inline-Konfigurationswerte werden als Standardansatz betrachtet und sollten nach Möglichkeit verwendet werden. Inline-Konfigurationen bieten folgende Vorteile:

* Sie bleiben erhalten, mit Governance und Versionsgeschichte in Git
* Werte sind implizit an Codebereitstellungen gebunden.
* Sie erfordern keine zusätzlichen Überlegungen zur Bereitstellung oder Koordinierung

Beim Definieren eines OSGi-Konfigurationswerts, Beginn mit Inline-Werten, wählen Sie nur geheime oder Umgebung-spezifische Konfigurationen aus, wenn dies für den Anwendungsfall erforderlich ist.

### Verwenden von nicht geheimen Konfigurationswerten für Umgebung {#when-to-use-non-secret-environment-specific-configuration-values}

Verwenden Sie für nicht geheime Konfigurationswerte nur Umgebung-spezifische Konfigurationen (`$[env:ENV_VAR_NAME]`), wenn die Werte je nach Umgebung variieren. Dazu gehören lokale Entwicklungsinstanzen und alle AEM als Cloud Service Development-Umgebung. Vermeiden Sie die Verwendung von nicht geheimen Umgebung-spezifischen Konfigurationen für AEM als Cloud-Service-Phase oder Produktions-Umgebung.

* Verwenden Sie für Konfigurationswerte, die sich zwischen Entwicklungs-Umgebung, einschließlich lokaler Entwicklungsinstanzen, unterscheiden, nur nicht geheime Umgebung.
* Verwenden Sie stattdessen die standardmäßigen Inline-Werte in den OSGi-Konfigurationen für nicht geheime Werte für &quot;Stage&quot;und &quot;Production&quot;.  Es wird daher nicht empfohlen, Umgebung-spezifische Konfigurationen zu verwenden, um Konfigurationsänderungen zur Laufzeit zu Stage- und Production-Umgebung zu erleichtern. Diese Änderungen sollten über das Quellcode-Management eingeführt werden.

### Verwendung geheimer Konfigurationswerte für die Umgebung {#when-to-use-secret-environment-specific-configuration-values}

AEM als Cloud-Dienst erfordert die Verwendung von Umgebung-spezifischen Konfigurationen (`$[secret:SECRET_VAR_NAME]`) für alle geheimen OSGi-Konfigurationswerte, wie z. B. Kennwörter, private API-Schlüssel oder andere Werte, die aus Sicherheitsgründen nicht in Git gespeichert werden können.

Verwenden Sie für geheime Umgebung spezifische Konfigurationen, um den Wert für Geheimnisse in allen AEM-Umgebung als Cloud-Dienst zu speichern, einschließlich Stage und Produktion.

<!-- ### Adding a New Configuration to the Repository {#adding-a-new-configuration-to-the-repository}

#### What You Need to Know {#what-you-need-to-know}

To add a new configuration to the repository you need to know the following:

1. The **Persistent Identity** (PID) of the service.

   Reference the **Configurations** field in the Web console. The name is shown in brackets after the bundle name (or in the **Configuration Information** towards the bottom of the page).

   For example, create a node `com.day.cq.wcm.core.impl.VersionManagerImpl.` to configure **AEM WCM Version Manager**.

   ![chlimage_1-141](assets/chlimage_1-141.png)

1. Whether a specific runmode is required. Create the folder:

    * `config` - for all run modes
    * `config.author` - for the author environment
    * `config.publish` - for the publish environment
    * `config.<run-mode>` - as appropriate

1. Whether a **Configuration** or **Factory Configuration** is necessary.
1. The individual parameters to be configured; including any existing parameter definitions that will need to be recreated.

   Reference the individual parameter field in the Web console. The name is shown in brackets for each parameter.

   For example, create a property
   `versionmanager.createVersionOnActivation` to configure **Create Version on Activation**.

   ![chlimage_1-142](assets/chlimage_1-142.png)

1. Does a configuration already exist in `/libs`? To list all configurations in your instance, use the **Query** tool in CRXDE Lite to submit the following SQL query:

   `select * from sling:OsgiConfig`

   If so, this configuration can be copied to ` /apps/<yourProject>/`, then customized in the new location. -->

## Erstellen von OSGi-Konfigurationen

Es gibt zwei Möglichkeiten, neue OSGi-Konfigurationen zu erstellen, wie nachfolgend beschrieben. Der erste Ansatz wird normalerweise zur Konfiguration benutzerdefinierter OSGi-Komponenten verwendet, die über bekannte OSGi-Eigenschaften und -Werte des Entwicklers verfügen, und der zweite für AEM-bereitgestellte OSGi-Komponenten.

### Schreiben von OSGi-Konfigurationen

OSGi-Konfigurationsdateien im JSON-Format können manuell direkt im AEM-Projekt geschrieben werden. Dies ist häufig die schnellste Möglichkeit, OSGi-Konfigurationen für bekannte OSGi-Komponenten und insbesondere benutzerdefinierte OSGi-Komponenten zu erstellen, die von demselben Entwickler entwickelt und entwickelt wurden, der die Konfigurationen definiert. Dieser Ansatz kann auch zum Kopieren/Einfügen und Aktualisieren von Konfigurationen für dieselbe OSGi-Komponente in verschiedenen Ordnern im Laufzeitmodus genutzt werden.

1. Öffnen Sie in Ihrer IDE das `ui.apps` Projekt, suchen oder erstellen Sie den Konfigurationsordner (`/apps/.../config.<runmode>`), in dem die Ausführungsmodi Zielgruppe werden, die die neue OSGi-Konfiguration durchführen soll.
1. Erstellen Sie in diesem Konfigurationsordner eine neue `<PID>.cfg.json` Datei. Die PID ist die Persistente Identität der OSGi-Komponente ist normalerweise der vollständige Klassenname der OSGi-Komponentenimplementierung. Beispiel:
   `/apps/.../config/com.example.workflow.impl.ApprovalWorkflow.cfg.json`
Beachten Sie, dass die Werksdateinamen der OSGi-Konfiguration die `<PID>-<factory-name>.cfg.json` Benennungskonvention verwenden.
1. Öffnen Sie die neue `.cfg.json` Datei und definieren Sie die Schlüssel/Wert-Kombinationen für die OSGi-Eigenschafts- und -Wertpaare entsprechend dem [JSON OSGi-Konfigurationsformat](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-cfgjson-1).
1. Speichern Sie Ihre Änderungen in der neuen `.cfg.json` Datei
1. Hinzufügen und bestätigen Sie Ihre neue OSGi-Konfigurationsdatei auf Git

### Generieren von OSGi-Konfigurationen mit AEM SDK QuickStart

Die AEM SDK QuickStart Jar-Web-Konsole von AEM SDK kann verwendet werden, um OSGi-Komponenten zu konfigurieren und OSGi-Konfigurationen als JSON zu exportieren. Dies ist nützlich für die Konfiguration von AEM-bereitgestellten OSGi-Komponenten, deren OSGi-Eigenschaften und deren Wertformate vom Entwickler, der die OSGi-Konfigurationen im AEM-Projekt definiert, möglicherweise nicht richtig verstanden werden. Beachten Sie, dass in der Konfigurationsoberfläche von AEM Web Console Dateien in das Repository geschrieben werden. Achten Sie daher darauf, dass dies zu vermeiden ist, dass während der lokalen Entwicklung möglicherweise unerwartete Verhaltensweisen auftreten, wenn die vom AEM-Projekt definierten OSGi-Konfigurationen von den generierten Konfigurationen abweichen können. `.cfg.json`

1. Melden Sie sich bei der AEM SDK QuickStart Jar-AEM-Webkonsole als Admin-Benutzer an
1. Navigieren Sie zu OSGi > Konfiguration
1. Suchen Sie die zu konfigurierende OSGi-Komponente und tippen Sie zum Bearbeiten auf ihren Titel
   ![OSGi-Konfiguration](./assets/configuring-osgi/configuration.png)
1. Bearbeiten Sie die OSGi-Konfigurationseigenschaftswerte nach Bedarf über die Web-Benutzeroberfläche
1. Notieren Sie die Persistente Identität (PID) an einem sicheren Ort. Dies wird später zum Generieren der OSGi-Konfigurations-JSON verwendet
1. Tippen Sie auf Speichern
1. Navigieren Sie zu OSGi > OSGi-Installationskonfigurationsdrucker.
1. Fügen Sie die in Schritt 5 kopierte PID ein, stellen Sie sicher, dass das Serialisierungsformat auf &quot;OSGi Configurator JSON&quot;eingestellt ist.
1. Tippen Sie auf Drucken,
1. Die OSGi-Konfiguration im JSON-Format wird im Abschnitt &quot;Serialisierte Konfigurationseigenschaften&quot;angezeigt
   ![OSGi-Installationskonfigurationsdrucker](./assets/configuring-osgi/osgi-installer-configurator-printer.png)
1. Öffnen Sie in Ihrer IDE das `ui.apps` Projekt, suchen oder erstellen Sie den Konfigurationsordner (`/apps/.../config.<runmode>`), in dem die Ausführungsmodi der neuen OSGi-Konfiguration Zielgruppe werden sollen.
1. Erstellen Sie in diesem Konfigurationsordner eine neue `<PID>.cfg.json` Datei. Die PID ist der gleiche Wert aus Schritt 5.
1. Fügen Sie die serialisierten Konfigurationseigenschaften aus Schritt 10 in die `.cfg.json` Datei ein.
1. Speichern Sie Ihre Änderungen in der neuen `.cfg.json` Datei.
1. Hinzufügen und speichern Sie die neue OSGi-Konfigurationsdatei auf Git.


## OSGi-Konfigurationseigenschaftsformate

### Inline-Werte {#inline-values}

Inline-Werte werden wie erwartet als Standard-Name/Wert-Paare gemäß der JSON-Standardsyntax formatiert. Beispiel:

```json
{
   "my_var1": "val",
   "my_var2": [ "abc", "def" ],
   "my_var3": 500
}
```

### Umgebung-spezifische Konfigurationswerte {#environment-specific-configuration-values}

Die OSGi-Konfiguration sollte einen Platzhalter für die Variable zuweisen, die pro Umgebung definiert werden soll:

```
use $[env:ENV_VAR_NAME]
```

Kunden sollten diese Technik nur für OSGI-Konfigurationseigenschaften im Zusammenhang mit ihrem benutzerspezifischen Code verwenden. Es sollte nicht verwendet werden, um die von Adobe definierte OSGI-Konfiguration zu überschreiben.

### Geheime Konfigurationswerte {#secret-configuration-values}

Die OSGi-Konfiguration sollte einen Platzhalter für das Geheimnis zuweisen, das pro Umgebung definiert werden soll:

```
use $[secret:SECRET_VAR_NAME]
```

### Variablenbenennung {#variable-naming}

Folgendes gilt sowohl für die Konfigurationswerte für Umgebung als auch für geheime Werte.

Variablennamen sollten die folgenden Regeln befolgen:

* Mindestlänge: 2
* maximale Länge: 100
* muss mit regex übereinstimmen: `[a-zA-Z_][a-zA-Z_0-9]*`

Die Werte für die Variablen dürfen 2048 Zeichen nicht überschreiten.

### Standardwerte {#default-values}

Folgendes gilt sowohl für die Konfigurationswerte für Umgebung als auch für geheime Werte.

Wenn kein Wert pro Umgebung festgelegt ist, wird der Platzhalter zur Laufzeit nicht ersetzt und an seiner Stelle gelassen, da keine Interpolation stattgefunden hat. Um dies zu vermeiden, kann ein Standardwert als Teil des Platzhalters mit der folgenden Syntax bereitgestellt werden:

```
$[env:ENV_VAR_NAME;default=<value>]
```

Wenn ein Standardwert angegeben ist, wird der Platzhalter entweder durch den pro Umgebung angegebenen Wert oder durch den bereitgestellten Standardwert ersetzt.

### Lokale Entwicklung {#local-development}

Folgendes gilt sowohl für die Konfigurationswerte für Umgebung als auch für geheime Werte.

Variablen können in der lokalen Umgebung definiert werden, damit sie zur Laufzeit von dem lokalen AEM abgerufen werden. Beispiel: unter Linux:

```bash
export ENV_VAR_NAME=my_value
```

Es wird empfohlen, ein einfaches Bash-Skript zu erstellen, das die in den Konfigurationen verwendeten Umgebung festlegt und vor dem Starten von AEM ausführt. Tools wie [https://direnv.net/](https://direnv.net/) helfen bei der Vereinfachung dieses Ansatzes. Abhängig vom Typ der Werte können sie bei der Quellcodeverwaltung überprüft werden, wenn sie für alle freigegeben werden können.

Die Werte für Geheimnisse werden aus Dateien gelesen. Daher muss für jeden Platzhalter, der einen geheimen Schlüssel verwendet, eine Textdatei mit dem geheimen Wert erstellt werden.

Wenn beispielsweise `$[secret:server_password]` eine Textdatei mit dem Namen **server_password** verwendet wird, muss sie erstellt werden. Alle diese geheimen Dateien müssen im selben Ordner gespeichert werden und die Framework-Eigenschaft muss mit diesem lokalen Ordner konfiguriert werden. `org.apache.felix.configadmin.plugin.interpolation.secretsdir`

### Konfiguration &quot;Autor&quot;oder &quot;Veröffentlichungskonfiguration&quot; {#author-vs-publish-configuration}

Wenn für eine OSGI-Eigenschaft unterschiedliche Werte für &quot;author&quot;und &quot;publish&quot;erforderlich sind:

* Es sollten separate `config.author` und `config.publish` OSGi-Ordner verwendet werden, wie im Abschnitt [Runmode Resolution beschrieben](#runmode-resolution).
* Es sollten unabhängige Variablennamen verwendet werden. Es wird empfohlen, ein Präfix zu verwenden, z. B. `author_<variablename>` und `publish_<variablename>` bei dem die Variablennamen identisch sind

### Konfigurationsbeispiele {#configuration-examples}

Gehen Sie in den folgenden Beispielen davon aus, dass es neben der stage- und prod-Umgebung 3 dev-Umgebung gibt.

**Beispiel 1**

Der Wert der OSGI-Eigenschaft muss für stage und prod gleich sein, jedoch für jede der 3 dev-Umgebung unterschiedlich sein. `my_var1`

<table>
<tr>
<td>
<b>Folder</b>
</td>
<td>
<b>Inhalt von "myfile.cfg.json"</b>
</td>
</tr>
<tr>
<td>
config
</td>
<td>
<pre>
{ "my_var1": "val", "my_var2": "abc", "my_var3": 500}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ "my_var1" : "$[env:my_var1]" "my_var2": "abc", "my_var3": 500}
</pre>
</td>
</tr>
</table>

**Beispiel 2**

Der Zweck besteht darin, dass sich der Wert der OSGI-Eigenschaft für &quot;stage&quot;, &quot;prod&quot;und für jede der 3 dev-Umgebung `my_var1` unterscheidet. Daher muss die Cloud Manager-API aufgerufen werden, um den Wert für `my_var1` jedes dev-env festzulegen.

<table>
<tr>
<td>
<b>Folder</b>
</td>
<td>
<b>Inhalt von "myfile.cfg.json"</b>
</td>
</tr>
<tr>
<td>
config.stage
</td>
<td>
<pre>
{ "my_var1": "val1", "my_var2": "abc", "my_var3": 500}
</pre>
</td>
</tr>
<tr>
<td>
config.prod
</td>
<td>
<pre>
{ "my_var1": "val2", "my_var2": "abc", "my_var3": 500}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ "my_var1" : "$[env:my_var1]" "my_var2": "abc", "my_var3": 500}
</pre>
</td>
</tr>
</table>

**Beispiel 3**

Der Wert der OSGi-Eigenschaft muss für stage-, production- und nur eine dev-Umgebung gleich sein, für die anderen beiden dev-Umgebung jedoch unterschiedlich sein. `my_var1` In diesem Fall muss die Cloud Manager-API aufgerufen werden, um den Wert `my_var1` für jede dev-Umgebung festzulegen, einschließlich für die dev-Umgebung, die denselben Wert wie stage und production haben sollte. Der in der **Konfiguration** des Ordners festgelegte Wert wird nicht übernommen.

<table>
<tr>
<td>
<b>Folder</b>
</td>
<td>
<b>Inhalt von "myfile.cfg.json"</b>
</td>
</tr>
<tr>
<td>
config
</td>
<td>
<pre>
{ "my_var1": "val1", "my_var2": "abc", "my_var3": 500}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ "my_var1" : "$[env:my_var1]" "my_var2": "abc", "my_var3": 500}
</pre>
</td>
</tr>
</table>

Eine andere Möglichkeit wäre, einen Standardwert für das Ersetzungstoken im Ordner &quot;config.dev&quot;festzulegen, der mit dem im Ordner &quot; **config** &quot;identisch ist.

<table>
<tr>
<td>
<b>Folder</b>
</td>
<td>
<b>Inhalt von "myfile.cfg.json"</b>
</td>
</tr>
<tr>
<td>
config
</td>
<td>
<pre>
{ "my_var1": "val1", "my_var2": "abc", "my_var3": 500}
</pre>
</td>
</tr>
<tr>
<td>
config.dev
</td>
<td>
<pre>
{ "my_var1": "$[env:my_var1;default=val1]" "my_var2": "abc", "my_var3": 500}
</pre>
</td>
</tr>
</table>

## Cloud Manager-API-Format zum Festlegen von Eigenschaften {#cloud-manager-api-format-for-setting-properties}

### Festlegen von Werten über API {#setting-values-via-api}

Durch Aufruf der API werden die neuen Variablen und Werte in einer Cloud-Umgebung bereitgestellt, ähnlich wie bei einer typischen Bereitstellungspipeline für Kundencode. Der Autor- und der Veröffentlichungsdienst werden neu gestartet und referenziert die neuen Werte, was in der Regel einige Minuten dauert.

```
PATCH /program/{programId}/environment/{environmentId}/variables
```

```
]
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

Beachten Sie, dass Standardvariablen nicht über die API festgelegt werden, sondern in der OSGi-Eigenschaft selbst.

Weitere Informationen finden Sie auf [dieser Seite](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Environment_Variables/patchEnvironmentVariables).

### Abrufen von Werten über API {#getting-values-via-api}

```
GET /program/{programId}/environment/{environmentId}/variables
```

Weitere Informationen finden Sie auf [dieser Seite](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Environment_Variables/getEnvironmentVariables).

### Löschen von Werten über API {#deleting-values-via-api}

```
PATCH /program/{programId}/environment/{environmentId}/variables
```

Um eine Variable zu löschen, fügen Sie sie mit einem leeren Wert ein.

Weitere Informationen finden Sie auf [dieser Seite](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Environment_Variables/patchEnvironmentVariables).

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

> [!NOTE]
>
> Weitere Informationen zum Konfigurieren von Werten mithilfe des Cloud Manager-Plugins für die Adobe I/O-CLI finden Sie auf [dieser Seite](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) .

### Anzahl der Variablen {#number-of-variables}

Es können bis zu 20 Variablen deklariert werden.

## Überlegungen zur Bereitstellung für die spezifischen Konfigurationswerte für &quot;Geheim&quot;und &quot;Umgebung&quot; {#deployment-considerations-for-secret-and-environment-specific-configuration-values}

Da die für geheime und Umgebung spezifischen Konfigurationswerte außerhalb von Git liegen und daher nicht Teil des formalen AEM als Bereitstellungsmechanismus für Cloud-Dienste sind, sollte der Kunde AEM als Bereitstellungsprozess für Cloud-Dienste verwalten, steuern und integrieren.

Wie oben erwähnt, werden durch Aufrufen der API die neuen Variablen und Werte in Cloud-Umgebung bereitgestellt, ähnlich wie bei einer typischen Bereitstellungspipeline für den Kundencode. Der Autor- und der Veröffentlichungsdienst werden neu gestartet und referenziert die neuen Werte, was in der Regel einige Minuten dauert. Beachten Sie, dass die Qualitätsstufen und Tests, die von Cloud Manager während einer regulären Codebereitstellung ausgeführt werden, während dieses Prozesses nicht ausgeführt werden.

In der Regel rufen Kunden die API auf, um Umgebung festzulegen, bevor Code bereitgestellt wird, der auf sie in Cloud Manager basiert. In einigen Situationen kann es sinnvoll sein, eine vorhandene Variable zu ändern, nachdem der Code bereits bereitgestellt wurde.

Beachten Sie, dass die API bei Verwendung einer Pipeline möglicherweise nicht erfolgreich ist. Entweder ein AEM-Update oder eine Kundenbereitstellung, je nachdem, welcher Teil der End-to-End-Pipeline zu diesem Zeitpunkt ausgeführt wird. Die Fehlerantwort zeigt an, dass die Anforderung nicht erfolgreich war, obwohl sie den spezifischen Grund nicht angibt.

Es kann Situationen geben, in denen eine geplante Bereitstellung von Kundencode auf vorhandenen Variablen basiert, um neue Werte zu erhalten, was mit dem aktuellen Code nicht übereinstimmen würde. Wenn dies Besorgnis erregend ist, wird empfohlen, die Variablenänderungen in additiver Weise vorzunehmen. Erstellen Sie dazu neue Variablennamen, anstatt nur den Wert alter Variablen zu ändern, sodass der alte Code nie auf den neuen Wert verweist. Wenn das neue Release stabil aussieht, können Sie dann die älteren Werte entfernen.

Da die Werte einer Variablen nicht versioniert sind, kann ein Rückgängigmachen des Codes dazu führen, dass sie auf neuere Werte verweisen, die Probleme verursachen. Die oben genannte Strategie für eine additive Variable würde auch hier helfen.

Diese zusätzliche Variablenstrategie ist auch für Szenarien der Disaster Recovery nützlich, bei denen die Variablennamen und -werte, auf die sie Bezug nehmen, bei Bedarf mehrere Tage vor der Bereitstellung unverändert bleiben. Dies beruht auf einer Strategie, bei der ein Kunde einige Tage wartet, bevor diese älteren Variablen entfernt werden, da andernfalls der ältere Code nicht über geeignete Variablen zum Verweisen verfügt.