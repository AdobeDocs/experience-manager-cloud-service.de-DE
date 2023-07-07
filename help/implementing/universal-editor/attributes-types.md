---
title: Attribute und Typen
description: Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
exl-id: 02795a31-244a-42b4-8297-2649125d7777
source-git-commit: 0f62245d31074ab7a64d86b97ef3b1a8d7533001
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 82%

---

# Attribute und Typen {#attributes-types}

Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.

## Einführung {#introduction}

Damit eine Anwendung mit dem universellen Editor bearbeitet werden kann, muss sie ordnungsgemäß instrumentiert sein. Dazu gehören auch die korrekten Metadaten, damit der Editor den Inhalt der Anwendung bearbeiten kann. In diesem Dokument werden die Attribute und Typen dieser Metadaten beschrieben.

>[!NOTE]
>
>Die Inhaltsvalidierung erfolgt Server-seitig. Der universelle Editor arbeitet einfach mit den Datenattributen. Die Validierung, ob sie dem Modell/der Struktur entsprechen, muss auf API-Ebene durchgeführt werden.

## Dateneigenschaften {#data-properties}

| Dateneigenschaft | Beschreibung |
|---|---|
| `itemid` | URN zur Ressource, siehe den Abschnitt [„Instrumentieren der Seite“ im Dokument „Erste Schritte mit dem universellen Editor in AEM“](getting-started.md#instrument-thepage) |
| `itemprop` | Attribut der Ressource, siehe den Abschnitt [„Instrumentieren der Seite“ im Dokument „Erste Schritte mit dem universellen Editor in AEM“](getting-started.md#instrument-thepage) |
| `itemtype` | Typ des bearbeitbaren Elements (z. B. Text, Bild und Verweis) |
| `data-editor-itemfilter` | Definiert, welche Verweise verwendet werden können |
| `data-editor-itemlabel` | Definiert eine benutzerdefinierte Bezeichnung für ein auswählbares Element, das im Editor angezeigt wird <br>In diesem Fall `itemmodel` festgelegt ist, wird die Bezeichnung über das Modell abgerufen |
| `data-editor-itemmodel` | Definiert ein Modell, das für die formularbasierte Bearbeitung in der Eigenschaftenleiste verwendet wird |
| `data-editor-behavior` | Definiert das Verhalten einer Instrumentierung, z. B. kann ein eigenständiger Text oder ein Bild auch eine Komponente imitieren, um sie verschiebbar oder löschbar zu machen |

## Elementtypen {#item-types}

| `itemtype` | Beschreibung | `itemid` | `itemprop` | `data-editor-itemfilter` | `data-editor-itemlabel` | `data-editor-itemmodel` | `data-editor-behvior` |
|---|---|---|---|---|---|---|---|
| `text` | Text kann innerhalb der HTML-Tags bearbeitet werden, jedoch nur im einfachen Textformat, ohne verfügbare Rich-Text-Formatierung. Dies wird häufig bei Titelkomponenten verwendet, z. B. | Optional | Erforderlich | Nicht zutreffend | Optional | Nicht zutreffend | Optional |
| `richtext` | Der Text kann mit allen Rich-Text-Funktionen bearbeitet werden. Der RTE wird im rechten Bereich angezeigt | Optional | Erforderlich | Nicht zutreffend | Optional | Nicht zutreffend | Optional |
| `media` | Das bearbeitbare Element ist ein Asset, z. B. Bild oder Video | Optional | Erforderlich | Optional<br>Liste der Kriterien für Bild- oder Videofilter, die an den Asset-Selektor übergeben werden | Optional | Nicht zutreffend | Optional |
| `container` | Das bearbeitbare Element verhält sich als Container für Komponenten, auch bekannt als Absatzsystem. | Abhängig von <br>siehe unten | Abhängig von <br>siehe unten | Optional<br>eine Liste der zulässigen Komponenten | Optional | Nicht zutreffend | Nicht zutreffend |
| `component` | Das bearbeitbare Element ist eine Komponente. Es werden keine zusätzlichen Funktionen hinzugefügt. Es ist erforderlich, bewegliche/löschbare Teile des DOM anzugeben und die Eigenschaftenleiste und ihre Felder zu öffnen | Erforderlich | Nicht zutreffend | Nicht zutreffend | Optional | Optional | Nicht zutreffend |
| `reference` | Das bearbeitbare Element ist eine Referenz, z. B. Inhaltsfragment, Experience Fragment oder Produkt | Abhängig von <br>siehe unten | Abhängig von <br>siehe unten | Optional<br>Liste der Filterkriterien für Inhaltsfragmente, Produkte oder Experience Fragments, die an den Referenz-Selektor übergeben werden | Optional | Optional | Nicht zutreffend |

Je nach Anwendungsfall kann `itemprop` oder `itemid` erforderlich sein oder nicht. Beispiel:

* `itemid` ist erforderlich, wenn Sie Inhaltsfragmente über GraphQL abfragen und die Liste im Kontext bearbeitbar machen möchten.
* `itemprop` ist erforderlich, wenn Sie eine Komponente haben, die den Inhalt eines referenzierten Inhaltsfragments rendert, und die Referenz innerhalb der Komponente aktualisieren möchten.

## Verhaltensweisen {#behaviors}

| `data-editor-behavior` | Beschreibung |
|---|---|
| `component` | Kann verwendet werden, um eigenständigen Text, Rich-Text und Medien das Verhalten von Komponenten nachahmen zu lassen, sodass sie auch auf der Seite verschiebbar und löschbar sind. |

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zum universellen Editor finden Sie in diesen Dokumenten.

* [Einführung in den universellen Editor](introduction.md) - Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Inhalte in jeder Implementierung ermöglicht, sodass Sie außergewöhnliche Erlebnisse bereitstellen, die Inhaltsgeschwindigkeit erhöhen und ein modernes Entwicklererlebnis bieten können.
* [Inhaltserstellung mit dem universellen Editor](authoring.md) – Erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und -autoren ist, Inhalte mit dem universellen Editor zu erstellen.
* [Veröffentlichen von Inhalten mit dem universellen Editor](publishing.md) – Erfahren Sie, wie der universelle visuelle Editor Inhalte veröffentlicht und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.
* [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) – Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.
* [Architektur des universellen Editors](architecture.md) – Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
* [Authentifizierung beim universellen Editor](authentication.md) – Erfahren Sie, wie beim universellen Editor authentifiziert wird.
