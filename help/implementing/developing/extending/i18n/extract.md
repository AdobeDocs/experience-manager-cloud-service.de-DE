---
title: Extrahieren von Zeichenfolgen zum Übersetzen
description: Verwenden Sie xgettext-maven-plugin, um Zeichenfolgen, die übersetzt werden müssen, aus Ihrem Quell-Code zu extrahieren.
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 42b177e6d948a3097bf3edf72362054a10fc8bfb
workflow-type: ht
source-wordcount: '475'
ht-degree: 100%

---

# Extrahieren von Zeichenfolgen zum Übersetzen{#extracting-strings-for-translating}

Verwenden Sie xgettext-maven-plugin, um Zeichenfolgen, die übersetzt werden müssen, aus Ihrem Quell-Code zu extrahieren. Das Maven-Plug-in extrahiert Zeichenfolgen in eine XLIFF-Datei, die Sie zur Übersetzung senden. Zeichenfolgen werden aus den folgenden Quellen extrahiert:

* Java-Quelldateien
* JavaScript-Quelldateien
* XML-Darstellungen von SVN-Ressourcen (JCR-Knoten)

## Konfigurieren der Zeichenfolgenextrahierung {#configuring-string-extraction}

Konfigurieren Sie, wie das xgettext-maven-plugin-Tool Zeichenfolgen für Ihr Projekt extrahiert.

```xml
/filter { }
/parsers {
   /vaultxml { }
   /javascript { }
   /regexp {
      /files {
         /java { }
         /jsp { }
         /extjstemplate { }
      }
   }
}
/potentials { }
```

| Abschnitt | Beschreibung |
|---|---|
| /filter | Identifiziert die analysierten Dateien. |
| /parsers/vaultxml | Konfiguriert das Analysieren von Vault-Dateien. Gibt die JCR-Knoten an, die externalisierte Zeichenfolgen und Lokalisierungshinweise enthalten. Gibt außerdem JCR-Knoten an, die ignoriert werden sollen. |
| /parsers/javascript | Gibt die JavaScript-Funktionen an, die Zeichenfolgen externalisieren. Sie müssen diesen Abschnitt nicht ändern. |
| /parsers/regexp | Konfiguriert das Parsing von Java-, JSP- und ExtJS-Vorlagedateien. Sie müssen diesen Abschnitt nicht ändern. |
| /potentials | Die Formel zur Erkennung von Zeichenfolgen, die internationalisiert werden sollen. |

### Bestimmung der zu parsenden Dateien {#identifying-the-files-to-parse}

Der Abschnitt „/filter“ der Datei „i18n.any“ gibt die Dateien an, die das xgettext-maven-plugin-Tool parst. Fügen Sie mehrere ein- und ausschließende Regeln hinzu, um Dateien anzugeben, die geparst bzw. ignoriert werden sollen. Sie sollten alle Dateien einbeziehen und dann die Dateien ausschließen, die Sie nicht parsen möchten. Normalerweise sollten Dateitypen ausgeschlossen werden, die nicht Teil der Benutzeroberfläche sind oder die die Benutzeroberfläche definieren, jedoch nicht übersetzt werden. Die ein- und ausschließenden Regeln haben das folgende Format:

```
{ /include "pattern" }
{ /exclude "pattern" }
```

Das Muster einer Regel wird verwendet, um die Namen der Dateien abzugleichen, die ein- bzw. ausgeschlossen werden sollen. Das Musterpräfix gibt an, ob Sie einen JCR-Knoten (seine Darstellung in Vault) oder das Dateisystem abgleichen.

| Präfix | Ergebnis |
|---|---|
| / | Gibt einen JCR-Pfad an. Daher gleicht dieses Präfix Dateien unter dem Verzeichnis jcr_root ab. |
| &amp;ast; | Gibt eine reguläre Datei im Dateisystem an. |
| none | Kein Präfix oder ein Muster, das mit einem Ordner oder einem Dateinamen beginnt, gibt eine reguläre Datei im Dateisystem an. |

In einem Muster steht das Zeichen / für ein Unterverzeichnis und das Zeichen &amp;ast; ist ein Platzhalter für eine beliebige Zeichenfolge. In der folgenden Tabelle sind einige Beispielregeln aufgeführt.

<table>
 <tbody>
  <tr>
   <th>Beispielregel</th>
   <th>Ergebnis</th>
  </tr>
  <tr>
   <td><code>{ /include "*" }</code></td>
   <td>Einschließen aller Dateien.</td>
  </tr>
  <tr>
   <td><code>{ /exclude "*.pdf" }</code></td>
   <td>Ausschließen aller PDF-Dateien.</td>
  </tr>
  <tr>
   <td><code> { /exclude "*/pom.xml" }</code></td>
   <td>Ausschließen von POM-Dateien.</td>
  </tr>
  <tr>
   <td><code class="code">{ /exclude "/content/*" }
      { /include "/content/catalogs/geometrixx/templatepages" }
      { /include "/content/catalogs/geometrixx/templatepages/*" }</code></td>
   <td><p>Ausschließen aller Dateien unter dem Knoten /content.</p> <p>Den Knoten /content/catalogs/geometrixx/templatepages einbeziehen.</p> <p>Einschließen aller untergeordneten Knoten von /content/catalogs/geometrixx/templatepages.</p> </td>
  </tr>
 </tbody>
</table>

### Extrahieren der Zeichenfolgen  {#extracting-the-strings}

Ohne POM:

```shell
mvn -N com.adobe.granite.maven:xgettext-maven-plugin:1.2.2:extract  -Dxgettext.verbose=true -Dxgettext.target=out -Dxgettext.rules=i18n.any -Dxgettext.root=.
```

Mit POM: Fügen Sie dies zu POM hinzu:

```xml
<build>
    <plugins>
        <plugin>
            <groupId>com.adobe.granite.maven</groupId>
            <artifactId>xgettext-maven-plugin</artifactId>
            <version>1.1</version>
            <configuration>
                <rules>i18n.any</rules>
                <root>jcr_root</root>
                <xliff>cq.xliff</xliff>
                <verbose>true</verbose>
            </configuration>
        </plugin>
    </plugins>
</build>
```

Der Befehl:

```shell
mvn xgettext:extract
```

### Ausgabedateien {#output-files}

* `raw.xliff`: extrahierte Zeichenfolgen
* `warn.log`: Warnmeldungen (falls vorhanden), wenn die `CQ.I18n.getMessage()`-API falsch verwendet wird. In diesen Fällen ist immer eine Fehlerbehebung und anschließend eine Wiederholung erforderlich.

* `parserwarn.log`: Parser-Warnungen (falls vorhanden), z. B. js-Parser-Probleme
* `potentials.xliff`: „potenzielle“ Kandidaten, die nicht extrahiert werden, aber möglicherweise von Menschen lesbare Zeichenfolgen sind, die übersetzt werden müssen (kann ignoriert werden, da es noch eine große Menge an falsch positiven Ergebnissen findet)
* `strings.xliff`: Zusammengefasste xliff-Datei für den Import in ALF
* `backrefs.txt`: ermöglicht ein schnelles Nachschlagen der Position bestimmter Zeichenfolgen im Quell-Code
