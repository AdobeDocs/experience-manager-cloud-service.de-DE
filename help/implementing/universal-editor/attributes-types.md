---
title: Attribute und Elementtypen
description: Erfahren Sie mehr über die Datenattribute und Elementtypen, die der universelle Editor erfordert.
exl-id: 02795a31-244a-42b4-8297-2649125d7777
feature: Developing
role: Admin, Architect, Developer
source-git-commit: edef86c67becf3b8094196d39baa9e69d6c81777
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 100%

---


# Attribute und Typen {#attributes-types}

Erfahren Sie mehr über die Datenattribute und Elementtypen, die der universelle Editor erfordert.

## Einführung {#introduction}

Damit eine Anwendung mit dem universellen Editor bearbeitet werden kann, muss sie ordnungsgemäß instrumentiert sein. Dazu gehören auch die korrekten Metadaten, damit der Editor den Inhalt der Anwendung bearbeiten kann. In diesem Dokument werden die Attribute und Elementtypen dieser Metadaten beschrieben.

>[!NOTE]
>
>Die Inhaltsvalidierung erfolgt Server-seitig. Der universelle Editor arbeitet einfach mit den Datenattributen. Die Validierung, ob sie dem Modell/der Struktur entsprechen, muss auf API-Ebene durchgeführt werden.

## Dateneigenschaften {#data-properties}

| Dateneigenschaft | Beschreibung |
|---|---|
| `data-aue-resource` | URN zur Ressource, siehe den Abschnitt [„Instrumentieren der Seite“ im Dokument „Erste Schritte mit dem universellen Editor in AEM“](getting-started.md#instrument-thepage) |
| `data-aue-prop` | Attribut der Ressource, siehe den Abschnitt [„Instrumentieren der Seite“ im Dokument „Erste Schritte mit dem universellen Editor in AEM“](getting-started.md#instrument-thepage) |
| `data-aue-type` | [Typ des bearbeitbaren Elements](#item-types) (z. B. Text, Bild, Verweis usw.) |
| `data-aue-filter` | Definiert:<br>- Welche RTE-Funktionalität aktiviert ist<br>- Welche Komponenten einem Container hinzugefügt werden können<br>- Welche Assets einem Medientyp hinzugefügt werden können |
| `data-aue-label` | Definiert ein benutzerdefiniertes Label für ein auswählbares Element, das im Editor angezeigt wird |
| `data-aue-model` | Definiert ein Modell, das für die formularbasierte Bearbeitung im Bedienfeld „Eigenschaften“ verwendet wird |
| `data-aue-behavior` | Definiert das [Verhalten einer Instrumentierung](#behaviors); zum Beispiel kann ein eigenständiger Text oder ein eigenständiges Bild auch eine Komponente imitieren, um sie verschiebbar oder löschbar zu machen |

## Elementtypen {#item-types}

| `data-aue-type` | Beschreibung | `data-aue-resource` | `data-aue-prop` | `data-aue-filter` | `data-aue-label` | `data-aue-model` | `data-aue-behavior` |
|---|---|---|---|---|---|---|---|
| `text` | Text kann innerhalb der HTML-Tags bearbeitet werden, jedoch nur im einfachen Textformat, ohne verfügbare Rich-Text-Formatierung. Dies wird häufig bei Titelkomponenten verwendet, z. B. | Optional | Erforderlich | Nicht zutreffend | Optional | Nicht zutreffend | Optional |
| `richtext` | Der Text kann mit allen Rich-Text-Funktionen bearbeitet werden. RTE wird im rechten Bedienfeld angezeigt | Optional | Erforderlich | Nicht zutreffend | Optional | Nicht zutreffend | Optional |
| `media` | Das bearbeitbare Element ist ein Asset, zum Beispiel ein Bild oder Video | Optional | Erforderlich | Optional<br>Liste der Kriterien für Bild- oder Videofilter, die an den Asset-Selektor übergeben werden | Optional | Nicht zutreffend | Optional |
| `container` | Das bearbeitbare Element verhält sich als Container für Komponenten, auch bekannt als Absatzsystem. | Abhängig von <br>siehe unten | Abhängig von <br>siehe unten | Optional<br>eine Liste der zulässigen Komponenten | Optional | Nicht zutreffend | Nicht zutreffend |
| `component` | Das bearbeitbare Element ist eine Komponente. Es werden keine zusätzlichen Funktionen hinzugefügt. Es ist erforderlich, um bewegliche/löschbare Teile des DOM anzuzeigen und um das Bedienfeld „Eigenschaften“ sowie seine Felder zu öffnen | Erforderlich | Nicht zutreffend | Nicht zutreffend | Optional | Optional | Nicht zutreffend |
| `reference` | Das bearbeitbare Element ist ein Verweis, zum Beispiel ein Inhaltsfragment, Experience Fragment oder Produkt | Abhängig von <br>siehe unten | Abhängig von <br>siehe unten | Optional<br>Liste der Filterkriterien für Inhaltsfragmente, Produkte oder Experience Fragments, die an den Referenz-Selektor übergeben werden | Optional | Optional | Nicht zutreffend |

`data-aue-resource` ist immer erforderlich, da dies der Primärschlüssel ist, der angibt, wohin Inhaltsänderungen geschrieben werden.

* Er ist nicht direkt auf dem Tag erforderlich, wo der `data-aue-type` festgelegt ist.
* Ist er nicht festgelegt, wird das Attribut `data-aue-resource` des nächsten übergeordneten Elements verwendet.

`data-aue-prop` ist immer dann erforderlich, wenn Sie eine Bearbeitung im Kontext vornehmen möchten, außer bei einem Container, bei dem dies optional ist (falls festgelegt, ist der Container ein Inhaltsfragment und die Eigenschaft verweist auf ein Feld mit mehreren Verweisen).

* Die `data-aue-prop` ist das Attribut, das für den Primärschlüssel von `data-aue-resource` aktualisiert werden soll.

## Verhaltensweisen {#behaviors}

| `data-aue-behavior` | Beschreibung |
|---|---|
| `component` | Kann verwendet werden, um eigenständigen Text, Rich-Text und Medien das Verhalten von Komponenten nachahmen zu lassen, sodass sie auch auf der Seite verschiebbar und löschbar sind. |
| `container` | Kann verwendet werden, damit Container als ihre eigenen Komponenten behandelt werden, sodass sie auf der Seite verschiebbar und löschbar sind. |
