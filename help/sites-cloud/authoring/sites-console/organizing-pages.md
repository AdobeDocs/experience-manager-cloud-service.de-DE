---
title: Organisieren von Seiten
description: Erfahren Sie, wie Sie Ihre Website mit AEM organisieren.
exl-id: c57096ca-34fe-4b19-98e0-8f3cd43cf24e
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 7adfe0ca7fbab1f8a5bd488e524a48be62584966
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 100%

---


# Organisieren von Seiten {#creating-and-organizing-pages}

Erfahren Sie, wie Sie Ihre Website mit AEM organisieren.  Sobald Sie wissen, wie Sie Ihre Seiten organisieren müssen, können Sie [neue Seiten erstellen](/help/sites-cloud/authoring/sites-console/creating-pages.md) und [existierende Seiten verwalten](/help/sites-cloud/authoring/sites-console/managing-pages.md).

{{edge-delivery-authoring}}

## Organisieren Ihrer Site {#organizing-your-site}

Als Autorin oder Autor müssen Sie Ihre Site in AEM organisieren. Dazu gehört die Erstellung und Benennung von Inhaltsseiten, sodass Folgendes zutrifft:

* Sie müssen leicht in der Authoring-Umgebung auffindbar sein.
* Besucher der Website müssen sie einfach in der Veröffentlichungsumgebung durchsuchen können.

Sie können Ihre Inhalte auch mithilfe von [Ordnern](#creating-a-new-folder) organisieren.

Die Struktur einer Website kann als Baumstruktur gesehen werden, die die Inhaltsseiten enthält. Die Namen dieser Inhaltsseiten werden zur Bildung der URLs verwendet. Die Titel werden zusammen mit dem Seiteninhalt angezeigt.

Im Folgenden sehen Sie als Beispiel die Site [WKND Tutorial](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de), auf der ein Artikel über Skateparks (`la-skateparks`) aufgerufen wird:

`http://<host>:<port>/editor.html/content/wknd/en/sports/la-skateparks.html`

```xml
 /content
 /wknd
  /en
   /music
    /...
   /sports
    /la-skateparks
    /five-gyms-la
    /mountain-bike-routes
   /shopping
    /...
   /art
    /...
   /...
```

Diese Struktur kann über die [**Sites-Konsole** angezeigt werden.](/help/sites-cloud/authoring/sites-console/introduction.md) Von dort aus können Sie durch die Seiten Ihrer Website navigieren und Aktionen auf den Seiten durchführen. 

## Seitenbenennungskonventionen {#page-naming-conventions}

Beim Erstellen einer Seite gibt es zwei wichtige Felder:

* **[Titel](#title)**:
   * Dieses Feld wird dem Benutzer bei der Bearbeitung im oberen Teil des Seiteninhalts in der Konsole angezeigt.
   * Dieses Feld ist obligatorisch.
* **[Name](#name)**:
   * Mit diesem Wert wird der URI generiert.
   * Benutzereingaben sind für dieses Feld optional. Wenn kein Name angegeben ist, wird der Name vom Titel abgeleitet. Weitere Informationen finden Sie unter [Seitennamen-Einschränkungen und Best Practices](#page-name-restrictions-and-best-practices).

### Einschränkungen und Best Practices bei der Seitenbenennung {#page-name-restrictions-and-best-practices}

Der **Seitentitel** und der **Seitenname** können separat erstellt werden, sind aber verwandt:

* Beim Erstellen einer Seite ist nur das **Titelfeld** erforderlich. Wenn bei der Erstellung von Seiten kein **Name** angegeben wird, generiert AEM einen Namen aus den ersten 64 Zeichen des Titels (entsprechend der nachfolgenden Validierung). Nur die ersten 64 Zeichen werden verwendet, um gängige Best Practices für kurze Seitennamen zu unterstützen.
* Wenn ein Seitenname manuell vom Autor angegeben wird, gilt die Beschränkung von 64 Zeichen nicht, aber andere technische Einschränkungen gelten unter Umständen für die Länge des Seitennamens.

>[!TIP]
>
>Beim Definieren eines Seitennamens ist es sinnvoll, den Seitennamen so kurz wie möglich zu halten, aber so ausdruckstark und erinnerungsstark wie möglich, um ihn für den Leser verständlich zu machen. Weitere Informationen zum `title`-Element finden Sie im [W3C-Styleguide](https://www.w3.org/Provider/Style/TITLE.html).
>
>Denken Sie auch daran, dass einige Browser (z. B. ältere Versionen von IE) nur URLs bis zu einer bestimmten Länge akzeptieren, sodass auch technische Gründe für die Verwendung von kurzen Seitennamen bestehen.

Beim Erstellen einer Seite [validiert AEM den Seitennamen entsprechend den von AEM und JCR vorgegebenen Konventionen](/help/implementing/developing/introduction/naming-conventions.md).

Mindestens zulässig sind die folgenden Zeichen:

* `a` bis `z`
* `A` bis `Z`
* `0` bis `9`
* `_` (Unterstrich)
* `-` (Bindestrich/Minus)

Umfassende Informationen zu allen zulässigen Zeichen finden Sie in den [Benennungskonventionen](/help/implementing/developing/introduction/naming-conventions.md).

>[!NOTE]
>
>Seitennamen sind auf 150 Zeichen begrenzt.

### Titel {#title}

Wenn Sie für eine neu erstellte Seite nur den **Titel** angeben, leitet AEM den **Namen** für die Seite von dieser Zeichenfolge ab und [validiert den Namen entsprechend den Konventionen](/help/implementing/developing/introduction/naming-conventions.md) von AEM und JCR.

Im Feld **Titel** werden ungültige Zeichen akzeptiert, wobei die ungültigen Zeichen im abgeleiteten Namen jedoch ersetzt werden. Zum Beispiel:

| Titel | Abgeleiteter Name |
|---|---|
| Schön | `schoen.html` |
| SC%&amp;&#42;ç+ | `sc---c-.html` |

### Name {#name}

Wenn Sie beim Erstellen einer neuen Seite einen **Namen** für die Seite angeben, [validiert AEM den Namen gemäß den Konventionen von AEM und JCR](/help/implementing/developing/introduction/naming-conventions.md). Die Eingabe von ungültigen Zeichen im Feld **Name** ist nicht zulässig. Wenn AEM ungültige Zeichen erkennt, wird das Feld mit einer erläuternden Meldung hervorgehoben.

![Beispiel für die Eingabe eines ungültigen Seitennamens](/help/sites-cloud/authoring/assets/organizing-invalid-name.png)

>[!TIP]
>
>Sie sollten es vermeiden, einen Zwei-Buchstaben-Code gemäß ISO-639-1 als Seitennamen zu verwenden, sofern es sich nicht um einen Sprachstamm handelt.
>
>Weitere Informationen finden Sie unter [Vorbereiten von Inhalten für die Übersetzung](/help/sites-cloud/administering/translation/preparation.md).

## Vorlagen {#templates}

In AEM sind bestimmte Seitentypen in [Vorlagen](/help/sites-cloud/authoring/page-editor/templates.md) gespeichert, die als Basis für jede neue erstellte Seite verwendet werden.

Die Vorlage definiert die Seitenstruktur, u. a. eine Miniaturansicht und andere Eigenschaften. Beispielsweise könnten Sie unterschiedliche Vorlagen für Produktseiten, Sitemaps und Kontaktangaben verwenden. Vorlagen bestehen aus [Komponenten](#components).

Im Lieferumfang von AEM sind diverse Vorlagen enthalten. Welche Vorlagen verfügbar sind, hängt von der jeweiligen Website ab. Die wichtigsten Felder sind:

* **Titel**: Der Titel, der auf der resultierenden Web-Seite angezeigt wird.
* **Name**: Wird beim Benennen der Seite verwendet.
* **Vorlage**: Eine Liste von Vorlagen, die für das Erstellen neuer Seiten verwendet werden können.

## Komponenten {#components}

[Komponenten](/help/implementing/developing/components/overview.md) sind die Elemente, die von AEM bereitgestellt werden, damit Sie bestimmte Inhaltstypen hinzufügen können. AEM enthält eine Reihe vordefinierter Komponenten, die als [die Kernkomponenten,](/help/implementing/developing/components/overview.md#core-components) bezeichnet werden und die eine umfassende Funktionalität bieten. Beispiele für die Komponenten sind:

* Text
* Bild
* Titel
* Karussell
* Und vieles mehr

Sobald Sie eine Seite erstellt und geöffnet haben, können Sie [Inhalte mithilfe der Komponenten hinzufügen](/help/sites-cloud/authoring/page-editor/edit-content.md#inserting-a-component), die im [Komponenten-Browser](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser) verfügbar sind.

>[!TIP]
>
>Die [Komponentenkonsole](/help/sites-cloud/authoring/components-console.md) bietet einen Überblick über die Komponenten in Ihrer Instanz.
