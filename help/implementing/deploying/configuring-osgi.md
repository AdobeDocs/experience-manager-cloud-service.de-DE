---
title: OSGi für Adobe Experience Manager als Cloud Service konfigurieren
description: 'OSGi-Konfiguration mit geheimen Werten und umgebungsspezifischen Werten '
feature: Deploying
translation-type: tm+mt
source-git-commit: a91743ba97f9b18c7f67208e7f1dcd873a3bbd65
workflow-type: tm+mt
source-wordcount: '2737'
ht-degree: 60%

---


# OSGi für Adobe Experience Manager als Cloud Service {#configuring-osgi-for-aem-as-a-cloud-service} konfigurieren

[OSGi](https://www.osgi.org/) ist ein wesentlicher Bestandteil der Technologien von Adobe Experience Manager (AEM). OSGi wird zur Steuerung der AEM-Bundles und ihrer Konfigurationen verwendet.

OSGi bietet die standardisierten Primitive, mit denen Anwendungen aus kleinen, wiederverwendbaren und kollaborativen Komponenten aufgebaut werden können. Diese Komponenten können zu einer Anwendung zusammengefügt und bereitgestellt werden. Dies ermöglicht die einfache Verwaltung von OSGi-Bundles, da diese einzeln angehalten, installiert und gestartet werden können. Die gegenseitigen Abhängigkeiten werden automatisch verwaltet. Jede OSGi-Komponente ist in einem der verschiedenen Bundles enthalten. Weitere Informationen finden Sie in der [OSGi-Spezifikation](https://www.osgi.org/Specifications/HomePage).

Sie können die Konfigurationseinstellungen für OSGi-Komponenten mithilfe von Konfigurationsdateien verwalten, die Teil eines AEM-Code-Projekts sind.

## OSGi-Konfigurationsdateien {#osgi-configuration-files}

Konfigurationsänderungen werden in den Code-Paketen (`ui.apps`) des AEM-Projekts als Konfigurationsdateien (`.cfg.json`) unter Runmode-spezifischen Konfigurationsordnern definiert:

`/apps/example/config.<runmode>`

Das Format der OSGi-Konfigurationsdateien ist JSON-basiert und verwendet das vom Apache Sling-Projekt definierte Format `.cfg.json`.

OSGi-Konfigurationen Zielgruppe OSGi-Komponenten über ihre Persistent Identity (PID), die standardmäßig den Java™-Klassennamen der OSGi-Komponente verwendet. Um zum Beispiel eine OSGi-Konfiguration für einen von

`com.example.workflow.impl.ApprovalWorkflow.java`

implementierten OSGi-Service bereitzustellen, wird eine OSGi-Konfigurationsdatei unter

`/apps/example/config/com.example.workflow.impl.ApprovalWorkflow.cfg.json`

nach dem OSGi-Konfigurationsformat cfg.json definiert.

>[!NOTE]
>
>Frühere Versionen von AEM unterstützten OSGi-Konfigurationsdateien unter Verwendung verschiedener Dateiformate wie .cfg., .config und als XML sling:OsgiConfig-Ressourcendefinitionen. Diese Formate werden durch das OSGi-Konfigurationsformat cfg.json ersetzt.

## Runmode-Auflösung {#runmode-resolution}

Spezifische OSGi-Konfigurationen können mithilfe von Runmodes auf bestimmte AEM-Instanzen ausgerichtet werden. Um Runmode zu verwenden, erstellen Sie unter `/apps/example` (wobei „example“ Ihr Projektname ist) Konfigurationsordner im folgenden Format:

`/apps/example/config.<author|publish>.<dev|stage|prod>/`

Alle OSGi-Konfigurationen in diesen Ordnern werden verwendet, wenn die im config-Ordnernamen definierten Ausführungsmodi mit den von AEM verwendeten Ausführungsmodi übereinstimmen.

Wenn AEM beispielsweise den Parameter &quot;author&quot;und &quot;dev&quot;verwenden, werden Konfigurationsknoten in `/apps/example/config.author/` und `/apps/example/config.author.dev/` angewendet, während Konfigurationsknoten in `/apps/example/config.publish/` und `/apps/example/config.author.stage/` nicht angewendet werden.

Wenn mehrere Konfigurationen für dieselbe PID anwendbar sind, wird die Konfiguration mit der höchsten Anzahl an passenden Ausführungsmodi angewendet.

Die Granularität dieser Regel liegt auf PID-Ebene. Es ist daher nicht möglich, für dieselbe PID einige Eigenschaften in `/apps/example/config.author/` und spezifischere in `/apps/example/config.author.dev/` zu definieren. Die Konfiguration mit der höchsten Anzahl passender Runmodi ist für die gesamte PID wirksam.

Bei der lokalen Entwicklung kann ein Startparameter des Ausführungsmodus übergeben werden, um anzugeben, welche OSGI-Konfiguration im Ausführungsmodus verwendet wird.

## Typen von OSGi-Konfigurationswerten {#types-of-osgi-configuration-values}

Es gibt drei verschiedene OSGi-Konfigurationswerte, die mit Adobe Experience Manager als Cloud Service verwendet werden können.

1. **Inline-Werte**, d. h. Werte, die in der OSGi-Konfiguration fest codiert und in Git gespeichert werden. Beispiel:

   ```json
   {
      "connection.timeout": 1000
   }
   ```

1. **Geheime Werte**, die Werte sind, die aus Sicherheitsgründen nicht in Git gespeichert werden dürfen. Beispiel:

   ```json
   {
   "api-key": "$[secret:server-api-key]"
   } 
   ```

1. **Umgebung-spezifische Werte**, die sich von Umgebung zu  unterscheiden und daher nicht genau auf den Ausführungsmodus ausgerichtet werden können (da es in Adobe Experience Manager einen einzigen  `dev` Runmode als Cloud Service gibt). Beispiel:

   ```json
   {
    "url": "$[env:server-url]"
   }
   ```

   Beachten Sie, dass eine einzelne OSGi-Konfigurationsdatei eine beliebige Kombination dieser Konfigurationswerttypen verwenden kann. Beispiel:

   ```json
   {
   "connection.timeout": 1000,
   "api-key": "$[secret:server-api-key]",
   "url": "$[env:server-url]"
   }
   ```

## Auswählen des entsprechenden OSGi-Konfigurationswerttyps {#how-to-choose-the-appropriate-osgi-configuration-value-type}

Normalerweise werden für OSGi Inline-OSGi-Konfigurationswerte verwendet. Umgebungsspezifische Konfigurationen werden nur für bestimmte Anwendungsfälle verwendet, in denen sich ein Wert zwischen Entwicklungsumgebungen unterscheidet.

![](assets/choose-configuration-value-type_res1.png)

Umgebung-spezifische Konfigurationen erweitern die herkömmlichen, statisch definierten OSGi-Konfigurationen, die Inline-Werte enthalten, und ermöglichen so die externe Verwaltung der OSGi-Konfigurationswerte über die Cloud Manager-API. Es ist wichtig zu verstehen, wann der übliche und traditionelle Ansatz zum Definieren und Speichern von Inline-Werten in Git verwendet werden sollte, anstatt die Werte in umgebungsspezifischen Konfigurationen zu abstrahieren.

In den folgenden Anleitungen wird beschrieben, wann nicht geheime und geheime umgebungsspezifische Konfigurationen verwendet werden müssen:

### Verwendung von Inline-Konfigurationswerten {#when-to-use-inline-configuration-values}

Inline-Konfigurationswerte werden als Standardansatz betrachtet und sollten nach Möglichkeit verwendet werden. Inline-Konfigurationen bieten folgende Vorteile:

* Sie werden mit Governance und Versionsverlauf in Git aufbewahrt.
* Werte sind implizit an Code-Bereitstellungen gebunden.
* Sie erfordern keine zusätzlichen Überlegungen zur Bereitstellung oder Koordinierung.

Beim Definieren eines OSGi-Konfigurationswerts sollten Sie Beginn mit Inline-Werten verwenden und nur geheime oder Umgebung-spezifische Konfigurationen auswählen, wenn dies für den Anwendungsfall erforderlich ist.

### Verwendung nicht geheimer umgebungsspezifischer Konfigurationswerte {#when-to-use-non-secret-environment-specific-configuration-values}

Verwenden Sie für nicht geheime Konfigurationswerte nur umgebungsspezifische Konfigurationen (`$[env:ENV_VAR_NAME]`), wenn die Werte in den Entwicklungsumgebungen variieren. Dazu gehören auch lokale Entwicklungsinstanzen und alle Adobe Experience Manager-Umgebung als Cloud Service-Entwicklungs-. Vermeiden Sie die Verwendung von nicht geheimen Umgebung-spezifischen Konfigurationen für Adobe Experience Manager als Cloud Service-Stage- oder Produktions-Umgebung.

* Verwenden Sie nicht geheime umgebungsspezifische Konfigurationen nur für Konfigurationswerte, die sich zwischen Entwicklungsumgebungen, einschließlich lokaler Entwicklungsinstanzen, unterscheiden.
* Verwenden Sie stattdessen die standardmäßigen Inline-Werte in den OSGi-Konfigurationen für nicht geheime Werte in Staging- und Produktionsumgebungen. Es wird daher nicht empfohlen, Umgebung-spezifische Konfigurationen zu verwenden, um Konfigurationsänderungen zur Laufzeit zu Stage- und Production-Umgebung zu erleichtern. Diese Änderungen sollten über das Quellcode-Management eingeführt werden.

### Verwendung geheimer umgebungsspezifischer Konfigurationswerte {#when-to-use-secret-environment-specific-configuration-values}

Adobe Experience Manager als Cloud Service erfordert die Verwendung von Umgebung-spezifischen Konfigurationen (`$[secret:SECRET_VAR_NAME]`) für alle geheimen OSGi-Konfigurationswerte wie Kennwörter, private API-Schlüssel oder andere Werte, die aus Sicherheitsgründen nicht in Git gespeichert werden können.

Verwenden Sie für die geheime Umgebung spezifische Konfigurationen, um den Wert für Geheimnisse auf allen Adobe Experience Manager als Cloud Service-Umgebung, einschließlich Stage und Produktion, zu speichern.

## Erstellen von OSGi-Konfigurationen {#creating-sogi-configurations}

Es gibt zwei Möglichkeiten, OSGi-Konfigurationen zu erstellen, wie nachfolgend beschrieben. Der erste Ansatz wird typischerweise für die Konfiguration von benutzerdefinierten OSGi-Komponenten verwendet, die dem Entwickler bekannte OSGi-Eigenschaften und -Werte haben, und der zweite für von AEM bereitgestellte OSGi-Komponenten.

### Schreiben von OSGi-Konfigurationen {#writing-osgi-configurations}

OSGi-Konfigurationsdateien im JSON-Format können manuell direkt im AEM-Projekt geschrieben werden. Dies ist häufig die schnellste Möglichkeit, OSGi-Konfigurationen für bekannte OSGi-Komponenten und insbesondere benutzerdefinierte OSGi-Komponenten zu erstellen, die von demselben Entwickler entwickelt und entwickelt wurden, der die Konfigurationen definiert. Dieser Ansatz kann auch zum Kopieren/Einfügen und Aktualisieren von Konfigurationen für dieselbe OSGi-Komponente über verschiedene Runmode-Ordner hinweg verwendet werden.

1. Öffnen Sie in Ihrer IDE das Projekt `ui.apps`, suchen oder erstellen Sie den Konfigurationsordner (`/apps/.../config.<runmode>`), in dem die Ausführungsmodi Zielgruppe werden, die die neue OSGi-Konfiguration durchführen muss.
1. Erstellen Sie in diesem Konfigurationsordner eine neue `<PID>.cfg.json`-Datei. Die PID ist die Persistente Identität der OSGi-Komponente. Normalerweise ist die OSGi-Komponentenimplementierung der vollständige Klassenname. Beispiel:
   `/apps/.../config/com.example.workflow.impl.ApprovalWorkflow.cfg.json`
Beachten Sie, dass die Fabrikdateinamen der OSGi-Konfiguration die  `<PID>-<factory-name>.cfg.json` Benennungskonvention verwenden.
1. Öffnen Sie die neue `.cfg.json`-Datei und definieren Sie die Schlüssel/Wert-Kombinationen für die OSGi-Eigenschafts- und -Wertpaare entsprechend dem [JSON OSGi-Konfigurationsformat](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-cfgjson-1).
1. Speichern Sie Ihre Änderungen in der neuen `.cfg.json`-Datei
1. Fügen Sie Ihre neue OSGi-Konfigurationsdatei hinzu und übertragen Sie sie auf Git

### Generieren von OSGi-Konfigurationen mit AEM SDK QuickStart  {#generating-osgi-configurations-using-the-aem-sdk-quickstart}

Die AEM Web-Konsole von AEM SDK QuickStart Jar kann verwendet werden, um OSGi-Komponenten zu konfigurieren und OSGi-Konfigurationen als JSON zu exportieren. Dies ist nützlich, um von AEM bereitgestellte OSGi-Komponenten zu konfigurieren, deren OSGi-Eigenschaften und deren Werteformate vom Entwickler, der die OSGi-Konfigurationen im AEM-Projekt definiert, möglicherweise nicht gut verstanden werden.

>[!NOTE]
>
>Die Konfigurationsoberfläche der AEM Web-Konsole schreibt `.cfg.json`-Dateien in das Repository. Achten Sie daher darauf, dass dies zu vermeiden ist, um ein unerwartetes Verhalten während der lokalen Entwicklung zu vermeiden, wenn die AEM Project-definierten OSGi-Konfigurationen von den generierten Konfigurationen abweichen können.

1. Melden Sie sich bei der AEM-Web-Konsole von AEM SDK QuickStart Jar als Administrator an
1. Navigieren Sie zu „OSGi“ > „Konfiguration“
1. Zur Konfiguration suchen Sie die OSGi-Komponente und tippen Sie zum Bearbeiten auf ihren Titel
   ![OSGi-Konfiguration](./assets/configuring-osgi/configuration.png)
1. Bearbeiten Sie die OSGi-Konfigurationseigenschaftswerte nach Bedarf über die Web-Benutzeroberfläche
1. Notieren Sie die PID (Persistent Identity) an einem sicheren Ort. Dies wird später zum Generieren der OSGi-Konfigurations-JSON verwendet
1. Tippen Sie auf „Speichern“
1. Gehen Sie zu „OSGi“ > „OSGi Installer-Konfigurationsdrucker“
1. Fügen Sie die in Schritt 5 kopierte PID ein. Stellen Sie sicher, dass das Serialisierungsformat auf „OSGi Configurator JSON“ eingestellt ist
1. Tippen Sie auf Drucken
1. Die OSGi-Konfiguration im JSON-Format wird im Abschnitt „Serialisierte Konfigurationseigenschaften“ angezeigt
   ![OSGi Installer-Konfigurationsdrucker](./assets/configuring-osgi/osgi-installer-configurator-printer.png)
1. Öffnen Sie in Ihrer IDE das Projekt `ui.apps`, suchen oder erstellen Sie den Konfigurationsordner (`/apps/.../config.<runmode>`), in dem die Ausführungsmodi Zielgruppe werden, die die neue OSGi-Konfiguration durchführen muss.
1. Erstellen Sie in diesem Konfigurationsordner eine neue `<PID>.cfg.json`-Datei. Die PID ist der Wert aus Schritt 5.
1. Fügen Sie die serialisierten Konfigurationseigenschaften aus Schritt 10 in die `.cfg.json`-Datei ein.
1. Speichern Sie Ihre Änderungen in der neuen `.cfg.json`-Datei.
1. Fügen Sie Ihre neue OSGi-Konfigurationsdatei hinzu und übertragen Sie sie auf Git.


## OSGi-Konfigurationseigenschaftsformate  {#osgi-configuration-property-formats}

### Inline-Werte {#inline-values}

Inline-Werte werden gemäß der standardmäßigen JSON-Syntax als Name-Wert-Paare formatiert. Beispiel:

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

Kunden sollten diese Technik nur für OSGI-Konfigurationseigenschaften im Zusammenhang mit ihrem benutzerspezifischen Code verwenden. darf nicht verwendet werden, um die von der Adobe definierte OSGI-Konfiguration zu überschreiben.

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

Variablennamen müssen den folgenden Regeln entsprechen:

* Mindestlänge: 2
* Höchstlänge: 100
* Muss mit regex übereinstimmen: `[a-zA-Z_][a-zA-Z_0-9]*`

Die Werte für die Variablen dürfen 2048 Zeichen nicht überschreiten.

### Standardwerte {#default-values}

Folgendes gilt sowohl für umgebungsspezifische als auch für geheime Konfigurationswerte.

Wenn kein Wert pro Umgebung festgelegt ist, wird der Platzhalter zur Laufzeit nicht ersetzt und bleibt erhalten, da keine Interpolation stattgefunden hat. Um dies zu vermeiden, kann ein Standardwert als Teil des Platzhalters mit der folgenden Syntax bereitgestellt werden:

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

Wenn beispielsweise `$[secret:server_password]` verwendet wird, muss eine Textdatei mit dem Namen **server_password** erstellt werden. Alle diese geheimen Dateien müssen im selben Ordner gespeichert werden und die Framework-Eigenschaft `org.apache.felix.configadmin.plugin.interpolation.secretsdir` muss mit diesem lokalen Ordner konfiguriert werden.

### Vergleich von Autoren- und Veröffentlichungskonfiguration {#author-vs-publish-configuration}

Wenn eine OSGi-Eigenschaft unterschiedliche Werte für Autoren- und Verffentlichungsumgebung erfordert:

* Es müssen separate Ordner `config.author` und `config.publish` OSGi verwendet werden, wie im Abschnitt [Runmode-Auflösung](#runmode-resolution) beschrieben.
* Es sollten unabhängige Variablennamen verwendet werden. Es wird empfohlen, ein Präfix zu verwenden, z. B. `author_<variablename>` und `publish_<variablename>`, wobei die Variablennamen dieselben sind.

### Konfigurationsbeispiele {#configuration-examples}

Gehen Sie in den folgenden Beispielen davon aus, dass es neben der stage- und prod-Umgebung drei dev-Umgebung gibt.

**Beispiel 1**

Der Wert der OSGI-Eigenschaft `my_var1` muss für stage und prod gleich sein, für jede der drei dev-Umgebung jedoch unterschiedlich sein.

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

Der Zweck besteht darin, dass der Wert der OSGI-Eigenschaft `my_var1` für &quot;stage&quot;, &quot;prod&quot;und für jede der drei dev-Umgebung unterschiedlich ist. Daher muss die Cloud Manager-API aufgerufen werden, um den Wert für `my_var1` für jedes dev-env festzulegen.

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

Der Wert der OSGi-Eigenschaft `my_var1` soll für die Staging-, Produktions- und eine der Entwicklungsumgebungen gleich und für die anderen zwei Entwicklungsumgebungen unterschiedlich sein. In diesem Fall muss die Cloud Manager-API aufgerufen werden, um den Wert `my_var1` für jede dev-Umgebung festzulegen, einschließlich für die dev-Umgebung, die denselben Wert wie stage und production aufweisen sollte. Der im Ordner **config** festgelegte Wert wird nicht vererbt.

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

Auf [dieser Seite](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/create-api-integration.md) finden Sie Informationen zum Konfigurieren der API.
>[!NOTE]
>
>Stellen Sie sicher, dass der verwendeten Cloud Manager-API die Rolle „Deployment Manager - Cloud Service“ zugewiesen wurde. Andere Rollen können nicht alle folgenden Befehle ausführen.

### Festlegen von Werten über API {#setting-values-via-api}

Durch Aufruf der API werden die neuen Variablen und Werte ähnlich wie bei einer typischen Bereitstellungspipeline für Kundencodes in einer Cloud-Umgebung bereitgestellt. Die Autoren- und Veröffentlichungs-Services werden neu gestartet und verweisen auf die neuen Werte. Dies dauert normalerweise einige Minuten.

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

>[!NOTE]
>Standardvariablen werden nicht über die API festgelegt, sondern in der OSGi-Eigenschaft selbst.
>
>Weitere Informationen finden Sie auf [dieser Seite](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Environment_Variables/patchEnvironmentVariables).

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

>[!NOTE]
>
>Weitere Informationen zum Konfigurieren von Werten mithilfe des Cloud Manager-Plug-ins für Adobe I/O-CLI finden Sie auf [dieser Seite](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid).

### Anzahl der Variablen {#number-of-variables}

Pro Umgebung können bis zu 200 Variablen deklariert werden.

## Überlegungen zur Bereitstellung für geheime und Umgebung-spezifische Konfigurationswerte {#deployment-considerations-for-secret-and-environment-specific-configuration-values}

Da die geheimen und Umgebung-spezifischen Konfigurationswerte außerhalb von Git liegen und daher nicht Teil des formalen Adobe Experience Manager als Cloud Service-Bereitstellungsmechanismus sind, sollte der Kunde als Cloud Service-Bereitstellungsprozess die Adobe Experience Manager verwalten, steuern und integrieren.

Wie oben erwähnt, stellt der Aufruf der API die neuen Variablen und Werte in Cloud-Umgebung bereit, ähnlich wie bei einer typischen Implementierung des Kundencodes. Die Autoren- und Veröffentlichungs-Services werden neu gestartet und verweisen auf die neuen Werte. Dies dauert normalerweise einige Minuten. Beachten Sie, dass die Qualitäts-Gates und Tests, die von Cloud Manager während einer regulären Code-Bereitstellung ausgeführt werden, während dieses Prozesses nicht ausgeführt werden.

Normalerweise würden Kunden die API aufrufen, um Umgebungsvariablen zu setzen, bevor sie Code bereitstellen, der sich in Cloud Manager auf diese Variablen verlässt. In einigen Situationen kann es sinnvoll sein, eine vorhandene Variable zu ändern, nachdem der Code bereits bereitgestellt wurde.

>[!NOTE]
>
>Die API kann nicht erfolgreich sein, wenn eine Pipeline verwendet wird, entweder eine AEM oder eine Kundenbereitstellung, je nachdem, welcher Teil der End-to-End-Pipeline zu diesem Zeitpunkt ausgeführt wird. Die Fehlerantwort zeigt an, dass die Anfrage nicht erfolgreich war, obwohl sie den spezifischen Grund nicht angibt.

Es kann Situationen geben, in denen sich eine geplante Bereitstellung von Kunden-Code darauf verlässt, dass vorhandene Variablen neue Werte haben, die mit dem aktuellen Code nicht übereinstimmen würden. Wenn dies Besorgnis erregend ist, wird empfohlen, Variablenänderungen in additiver Weise vorzunehmen. Erstellen Sie dazu neue Variablennamen, anstatt nur den Wert alter Variablen zu ändern, sodass der alte Code nie auf den neuen Wert verweist. Wenn die neue Kundenversion dann stabil aussieht, können Sie die älteren Werte entfernen.

Da die Werte einer Variablen nicht versioniert sind, kann ein Rollback des Codes dazu führen, dass sie auf neuere Werte verweisen, die Probleme verursachen. Die zuvor erwähnte Strategie für die Verwendung von Zusatzstoffen würde auch hier helfen.

Diese additive Variablenstrategie ist auch für Disaster-Recovery-Szenarien nützlich, bei denen die Variablennamen und -werte, auf die sie verweisen, auch dann noch intakt sind, wenn Code von mehreren Tagen zuvor neu verteilt werden musste. Dies beruht auf einer Strategie, bei der ein Kunde einige Tage wartet, bevor er diese älteren Variablen entfernt. Andernfalls hätte der ältere Code keine geeigneten Variablen, auf die er verweisen könnte.
