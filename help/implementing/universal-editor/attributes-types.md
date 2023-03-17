---
title: Attribute und Typen
description: Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
source-git-commit: f454475b65da8f410812bbbe30ca5fc393be410a
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 7%

---


# Attribute und Typen {#attributes-types}

Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.

## Einführung {#introduction}

Damit eine App vom universellen Editor bearbeitet werden kann, muss sie ordnungsgemäß instrumentiert werden. Dazu gehören auch die korrekten Metadaten, damit der Editor den Inhalt der App bearbeiten kann. In diesem Dokument werden die Attribute und Typen dieser Metadaten beschrieben.

>[!NOTE]
>
>Die Inhaltsvalidierung erfolgt serverseitig. Der universelle Editor arbeitet einfach mit den Datenattributen. Die Überprüfung, ob sie dem Modell/der Struktur entsprechen, muss auf API-Ebene durchgeführt werden.

## Dateneigenschaften {#data-properties}

| Dateneigenschaft | Beschreibung |
|---|---|
| `itemid` | Weiterführende Informationen zur Ressource finden Sie im Abschnitt . [Instrumentieren der Seite des Dokuments Erste Schritte mit dem universellen Editor in AEM](getting-started.md#instrument-thepage) |
| `itemprop` | Das Attribut der Ressource, siehe Abschnitt [Instrumentieren der Seite des Dokuments Erste Schritte mit dem universellen Editor in AEM](getting-started.md#instrument-thepage) |
| `itemtype` | Typ des bearbeitbaren Elements (z. B. Text, Bild, Referenz usw.) |
| `data-editor-itemfilter` | Definiert, welche Verweise verwendet werden können |
| `data-editor-itemlabel` | Definiert eine benutzerdefinierte Bezeichnung für ein auswählbares Element, das im Editor angezeigt wird <br>In diesem Fall `itemmodel` festgelegt ist, wird die Bezeichnung über das Modell abgerufen |
| `data-editor-itemmodel` | Definiert ein Modell, das für die formularbasierte Bearbeitung in der Eigenschaftenleiste verwendet wird |
| `data-editor-behavior` | Definiert das Verhalten einer Instrumentierung, z. B. kann eigenständiger Text oder Bild auch eine Komponente imitieren, um sie beweglich oder lödbar zu machen |

## Elementtypen {#item-types}

| `itemtype` | Beschreibung | `itemid` | `itemprop` | `data-editor-itemfilter` | `data-editor-itemlabel` | `data-editor-itemmodel` | `data-editor-behvior` |
|---|---|---|---|---|---|---|---|
| `text` | Text kann innerhalb der HTML-Tags bearbeitet werden, jedoch nur im einfachen Textformat, ohne verfügbare Rich-Text-Formatierung. Dies wird häufig bei Titelkomponenten verwendet, z. B. | Optional | Erforderlich | Nicht zutreffend | Optional | Nicht zutreffend | Optional |
| `richtext` | Text kann mit Volltext-Funktionen bearbeitet werden. Der RTE wird im rechten Bereich angezeigt | Optional | Erforderlich | Nicht zutreffend | Optional | Nicht zutreffend | Optional |
| `media` | Die bearbeitbare Komponente ist ein Asset, z. B. Bild oder Video. | Optional | Erforderlich | Optional<br>Liste der Kriterien für Bild- oder Videofilter, die an die Asset-Auswahl übergeben werden | Optional | Nicht zutreffend | Optional |
| `container` | Die bearbeitbare Komponente verhält sich wie ein Container für Komponenten, auch Absatzsystem genannt. | Abhängig <br>siehe unten | Abhängig <br>siehe unten | Optional<br>eine Liste der zulässigen Komponenten | Optional | Nicht zutreffend | Nicht zutreffend |
| `component` | Die bearbeitbare Komponente ist eine Komponente. Fügt keine zusätzlichen Funktionen hinzu, ist erforderlich, um bewegliche/löschbare Teile des DOM anzuzeigen und die Eigenschaftenleiste und ihre Felder zu öffnen | Erforderlich | Nicht zutreffend | Nicht zutreffend | Optional | Optional | Nicht zutreffend |
| `reference` | Die bearbeitbare ist eine Referenz, z. B. Inhaltsfragment, Experience Fragment oder Produkt | Abhängig <br>siehe unten | Abhängig <br>siehe unten | Optional<br>Liste der Filterkriterien für Inhaltsfragmente, Produkte oder Experience Fragment , die an die Referenzauswahl übergeben werden | Optional | Optional | Nicht zutreffend |

Je nach Anwendungsfall `itemprop` oder `itemid` nicht erforderlich sein. Beispiel:

* `itemid` ist erforderlich, wenn Sie Inhaltsfragmente über GraphQL abfragen und die Liste kontextbezogen bearbeitbar machen möchten.
* `itemprop` ist erforderlich, wenn Sie eine Komponente haben, die den Inhalt eines referenzierten Inhaltsfragments rendert, und die Referenz innerhalb der Komponente aktualisieren möchten.

## Verhalten {#behaviors}

| `data-editor-behavior` | Beschreibung |
|---|---|
| `component` | Kann verwendet werden, um eigenständige Text-, Rich-Text- und Medienimikkomponenten so zu lassen, dass sie auch auf der Seite bewegt und gelöscht werden können |

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zum universellen Editor finden Sie in diesen Dokumenten.

* [Einführung in den universellen Editor](introduction.md) - Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Inhalte in jeder Implementierung ermöglicht, um außergewöhnliche Erlebnisse bereitzustellen, die Inhaltsgeschwindigkeit zu erhöhen und ein modernes Entwicklererlebnis zu bieten.
* [Inhaltserstellung mit dem universellen Editor](authoring.md) - Erfahren Sie, wie einfach und intuitiv es für Inhaltsautoren ist, Inhalte mit dem universellen Editor zu erstellen.
* [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) - Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM App beginnen, um ihn zu verwenden.
* [Architektur des universellen Editors](architecture.md) - Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
* [Universelle Editor-Authentifizierung](authentication.md) - Erfahren Sie, wie der universelle Editor authentifiziert wird.
