---
title: Internationalisierung von UI-Zeichenfolgen
description: Mit Java™- und JavaScript-APIs können Sie Zeichenfolgen internationalisieren
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 913b1beceb974243f0aa7486ddd195998d5e9439
workflow-type: ht
source-wordcount: '1095'
ht-degree: 100%

---

# Internationalisierung von UI-Zeichenfolgen {#internationalizing-ui-strings}

Mit Java™- und JavaScript-APIs können Sie Zeichenfolgen in folgenden Ressourcen internationalisieren:

* Java™-Quelldateien.
* JSP-Skripte.
* JavaScript in Client-seitigen Bibliotheken oder im Seitenquelltext.
* JCR-Knoten-Eigenschaftswerte, die in Dialogfeldern verwendet werden, und Konfigurationseigenschaften von Komponenten.

Einen Überblick über Internationalisierung und Lokalisierung finden Sie unter [Internationalisierung von Komponenten](/help/implementing/developing/extending/i18n/components.md).

## Internationalisierung von Zeichenfolgen in Java™- und JSP-Code {#internationalizing-strings-in-java-and-jsp-code}

Mit dem Java™-Paket `com.day.cq.i18n` können Sie lokalisierte Zeichenfolgen in Ihrer Benutzeroberfläche anzeigen. Die `I18n`-Klasse stellt die `get`-Methode zur Verfügung, die lokalisierte Zeichenfolgen aus dem Adobe Experience Manager-Wörterbuch abruft. Der einzige erforderliche Parameter der `get`-Methode ist das Literal der Zeichenfolgen in englischer Sprache. Englisch ist die standardmäßige Sprache der UI. Im folgenden Beispiel wird das Wort `Search` lokalisiert:

`i18n.get("Search");`

Die Benennung der englischsprachigen Zeichenfolgen unterscheidet sich von herkömmlichen Internationalisierungs-Frameworks, wo die Zeichenfolge über eine ID benannt wird, mit der die Zeichenfolge zur Laufzeit referenziert wird.  Die Verwendung des englischen Zeichenfolgenliterals bietet folgende Vorteile:

* Der Code lässt sich leicht verstehen.
* Die Zeichenfolge in der Standardsprache ist immer verfügbar.

### Bestimmung der Sprache der Benutzerin oder des Benutzers {#determining-the-user-s-language}

Es gibt zwei Möglichkeiten, die bevorzugte Sprache der Benutzenden zu bestimmen:

* Bei authentifizierten Benutzenden können Sie die Sprache in den Einstellungen im Benutzerkonto abrufen.
* Das Gebietsschema der angeforderten Seite.

Die Spracheinstellung des Benutzerkontos ist die bevorzugte Methode, da sie zuverlässiger ist.  Allerdings muss die Benutzerin bzw. der Benutzer dafür angemeldet sein.

#### Erstellen des I18n-Java™-Objekts {#creating-the-i-n-java-object}

Die I18n-Klasse stellt zwei Konstruktoren bereit.  Der zu verwendende Konstruktor hängt davon ab, wie Sie die bevorzugte Sprache der Benutzerin oder des Benutzers bestimmen.

Um die Zeichenfolge in der Sprache darzustellen, die im Benutzerkonto angegeben ist, verwenden Sie den folgenden Konstruktor (nachdem Sie `com.day.cq.i18n.I18n)` importiert haben):

```java
I18n i18n = new I18n(slingRequest);
```

Der Konstruktor verwendet `SlingHTTPRequest`, um die Spracheinstellung des Benutzers abzurufen.

Um das Gebietsschema der Seite zum Festlegen der Sprache zu verwenden, müssen Sie zunächst das ResourceBundle für die Sprache der angeforderten Seite abrufen:

```java
Locale pageLang = currentPage.getLanguage(false);
ResourceBundle resourceBundle = slingRequest.getResourceBundle(pageLang);
I18n i18n = new I18n(resourceBundle);
```

#### Internationalisierung einer Zeichenfolge {#internationalizing-a-string}

Verwenden Sie die `get`-Methode des `I18n`-Objekts, um eine Zeichenfolge zu internationalisieren. Der einzige erforderliche Parameter der `get`-Methode ist die Zeichenfolge, die internationalisiert werden soll. Die Zeichenfolge entspricht einer Zeichenfolge in einem Übersetzerwörterbuch.  Die get-Methode schlägt die Zeichenfolge im Wörterbuch nach und gibt die Übersetzung in der aktuellen Sprache zurück.

Das erste Argument der `get`-Methode muss folgende Regeln einhalten:

* Der Wert muss ein Zeichenfolgenliteral sein. Eine Variable des Typs `String` ist nicht zulässig.
* Das Zeichenfolgenliteral muss in einer Zeile ausgeschrieben sein.
* Die Zeichenfolge unterscheidet zwischen Groß- und Kleinschreibung.

```xml
i18n.get("Enter a search keyword");
```

#### Verwenden von Übersetzungshinweisen {#using-translation-hints}

Geben Sie den Übersetzungshinweis der internationalisierten Zeichenfolge an, um zwischen mehrfach vorhandenen Zeichenfolgen im Wörterbuch zu unterscheiden. Geben Sie den Übersetzungshinweis mit dem zweiten, optionalen Parameter der `get`-Methode an. Der Übersetzungshinweis muss mit der Kommentareigenschaft des Elements im Wörterbuch genau übereinstimmen.

Beispielsweise enthält das Wörterbuch die Zeichenfolge `Request` zweimal: einmal als Verb und einmal als Substantiv. Der folgende Code enthält den Übersetzungshinweis als Argument in der `get`-Methode:

```java
i18n.get("Request","A noun, as in a request for a web page");
```

#### Einfügen von Variablen in lokalisierte Sätze {#including-variables-in-localized-sentences}

Sie können Variablen in die lokalisierte Zeichenfolge einfügen, um dem Satz Kontextbedeutung zu geben. Ein Beispiel: Nach der Anmeldung bei einer Webanwendung wird auf der Homepage folgende Nachricht angezeigt: „Willkommen zurück, Administrator. Sie haben zwei Nachrichten in Ihrem Posteingang.“ Der Seitenkontext bestimmt den Benutzernamen und die Anzahl der Nachrichten.

Im Wörterbuch werden die Variablen in Zeichenfolgen als eingeklammerte Indizes dargestellt. Geben Sie die Werte der Variablen als Argumente der `get`-Methode an. Die Argumente werden nach dem Übersetzungshinweis platziert und die Indizes entsprechen der Reihenfolge der Argumente:

```xml
i18n.get("Welcome back {0}. You have {1} messages.", "user name, number of messages", user.getDisplayName(), numItems);
```

Die internationalisierte Zeichenfolge und der Übersetzungshinweis müssen genau mit der Zeichenfolge bzw. dem Kommentar im Wörterbuch übereinstimmen.  Sie können den Lokalisierungshinweis auslassen, indem Sie einen `null`-Wert als zweites Argument angeben.

#### Verwendung der statischen get-Methode {#using-the-static-get-method}

Die `I18N`-Klasse definiert eine statische `get`-Methode, die sich zur Lokalisierung einer kleinen Anzahl von Zeichenfolgen eignet. Zusätzlich zu den Parametern der `get`-Methode eines Objekts benötigt die statische Methode das Objekt `SlingHttpRequest` oder das `ResourceBundle`, das Sie verwenden, je nachdem, wie Sie die bevorzugte Sprache des Nutzers bestimmen:

* Wenn Sie die Spracheinstellungen des Nutzers verwenden, geben Sie das SlingHttpRequest-Objekt als ersten Parameter an.

  `I18n.get(slingHttpRequest, "Welcome back {}. You have {} messages.", "user name, number of messages", user.getDisplayName(), numItems);`
* Wenn Sie die Seitensprache verwenden, geben Sie das ResourceBundle als ersten Parameter an.

  `I18n.get(resourceBundle,"Welcome back {}. You have {} messages.", "user name, number of messages", user.getDisplayName(), numItems);`

### Internationalisierung von Zeichenfolgen in JavaScript-Code {#internationalizing-strings-in-javascript-code}

Die JavaScript-API ermöglicht es Ihnen, Zeichenfolgen im Client zu lokalisieren.  Wie bei [Java™- und JSP](#internationalizing-strings-in-java-and-jsp-code)-Code können Sie mit der JavaScript-API zu lokalisierende Zeichenfolgen benennen, Lokalisierungshinweise angeben und Variablen in die lokalisierten Zeichenfolgen einfügen.

Der `granite.utils`[-Client-Bibliotheksordner](/help/implementing/developing/introduction/clientlibs.md) stellt die JavaScript-API bereit. Um die API zu verwenden, fügen Sie diesen Client-Bibliotheksordner in Ihre Seite ein. Lokalisierungsfunktionen verwenden den `Granite.I18n`-Namespace.

Bevor Sie lokalisierte Zeichenfolgen darstellen, müssen Sie das Gebietsschema mithilfe der `Granite.I18n.setLocale`-Funktion festlegen. Diese Funktion erfordert den Sprach-Code des Gebietsschemas als Argument:

```
Granite.I18n.setLocale("fr");
```

Um eine lokalisierte Zeichenfolge darzustellen, verwenden Sie die Funktion `Granite.I18n.get`:

```
Granite.I18n.get("string to localize");
```

Im folgenden Beispiel wird die Zeichenfolge „Welcome back“ internationalisiert:

```
Granite.I18n.setLocale("fr");
Granite.I18n.get("string to localize", [variables], "localization hint");
```

Die Funktionsparameter unterscheiden sich von der Java™-I18n.get-Methode:

* Der erste Parameter ist das zu lokalisierende Zeichenfolgenliteral.
* Der zweite Parameter ist ein Array mit Werten, die in das Zeichenfolgenliteral eingefügt werden sollen.
* Der dritte Parameter ist der Lokalisierungshinweis.

Das folgende Beispiel verwendet JavaScript, um den Satz „Welcome back Administrator. Sie haben zwei Nachrichten in Ihrem Posteingang.“ zu lokalisieren:

```
Granite.I18n.setLocale("fr");
Granite.I18n.get("Welcome back {0}. You have {1} new messages in your inbox.", [username, numMsg], "user name, number of messages");
```

### Internationalisierung von Zeichenfolgen aus JCR-Knoten {#internationalizing-strings-from-jcr-nodes}

UI-Zeichenfolgen basieren häufig auf JCR-Knoteneigenschaften.  Die Eigenschaft `jcr:title` einer Seite wird beispielsweise häufig als Inhalt des `h1`-Elements im Seiten-Code verwendet. Die `I18n`-Klasse stellt die `getVar`-Methode zur Lokalisierung dieser Zeichenfolgen bereit.

Das folgende JSP-Skriptbeispiel ruft die `jcr:title`-Eigenschaft aus dem Repository ab und zeigt die folgende lokalisierte Zeichenfolge auf der Seite an:

```java
<% title = properties.get("jcr:title", String.class);%>
<h1><%=i18n.getVar(title) %></h1>
```

#### Angeben von Übersetzungshinweisen für JCR-Knoten {#specifying-translation-hints-for-jcr-nodes}

Ähnlich wie [Übersetzungshinweise in der Java™-API](#using-translation-hints) können Sie Übersetzungshinweise bereitstellen, um zwischen mehrfach vorhandenen Zeichenfolgen im Wörterbuch zu unterscheiden.  Geben Sie den Übersetzungshinweis als Eigenschaft des Knotens an, der die internationalisierte Eigenschaft enthält.  Der Name der Hinweiseigenschaft besteht aus dem Namen der internationalisierten Eigenschaft mit dem Suffix `_commentI18n`:

`${prop}_commentI18n`

Ein `cq:page`-Knoten enthält beispielsweise die Eigenschaft jcr:title, die lokalisiert wird. Der Hinweis wird als Wert der Eigenschaft mit dem Namen jcr:title_commentI18n angegeben.

### Prüfung der Internationalisierungsabdeckung {#testing-internationalization-coverage}

Prüfen Sie, ob Sie alle Zeichenfolgen in Ihrer Benutzeroberfläche internationalisiert haben.  Um festzustellen, welche Zeichenfolgen abgedeckt sind, setzen Sie die Benutzersprache auf zz_ZZ und öffnen Sie die Benutzeroberfläche im Webbrowser.  Die internationalisierten Zeichenfolgen werden mit einer Platzhalterübersetzung im folgenden Format angezeigt:

`USR_*Default-String*_尠`

Die folgende Abbildung zeigt die Platzhalterübersetzung für die AEM-Startseite:

![Platzhalterübersetzung für die AEM-Startseite](/help/implementing/developing/extending/assets/i18n-dev1.jpeg)

Um die Sprache für Benutzende festzulegen, konfigurieren Sie die Spracheigenschaft des Präferenzknotens für das Benutzerkonto.

Der Pfad des Präferenzknotens einer Benutzerin oder eines Benutzers sieht wie folgt aus:

`/home/users/<letter>/<hash>/preferences`
