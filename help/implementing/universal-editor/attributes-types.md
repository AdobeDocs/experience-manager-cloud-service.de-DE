---
title: Attribute und Elementtypen
description: Erfahren Sie mehr über die Datenattribute und Elementtypen, die der universelle Editor erfordert.
exl-id: 02795a31-244a-42b4-8297-2649125d7777
source-git-commit: 11a244b7dd4810fbfec92b3effc362102e7322dc
workflow-type: tm+mt
source-wordcount: '686'
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
| `data-aue-filter` | Definiert, welche Verweise verwendet werden können |
| `data-aue-label` | Definiert eine benutzerdefinierte Beschriftung für ein auswählbares Element, das im Editor angezeigt wird. <br>Wenn `data-aue-model` festgelegt ist, wird die Beschriftung über das Modell abgerufen |
| `data-aue-model` | Definiert ein Modell, das für die formularbasierte Bearbeitung in der Eigenschaftenleiste verwendet wird |
| `data-aue-behavior` | Definiert das [Verhalten einer Instrumentierung](#behaviors). Zum Beispiel kann ein eigenständiger Text oder ein eigenständiges Bild auch eine Komponente imitieren, um sie verschiebbar oder löschbar zu machen |

## Elementtypen {#item-types}

| `data-aue-type` | Beschreibung | `data-aue-resource` | `data-aue-prop` | `data-aue-filter` | `data-aue-label` | `data-aue-model` | `data-aue-behavior` |
|---|---|---|---|---|---|---|---|
| `text` | Text kann innerhalb der HTML-Tags bearbeitet werden, jedoch nur im einfachen Textformat, ohne verfügbare Rich-Text-Formatierung. Dies wird häufig bei Titelkomponenten verwendet, z. B. | Optional | Erforderlich | Nicht zutreffend | Optional | Nicht zutreffend | Optional |
| `richtext` | Der Text kann mit allen Rich-Text-Funktionen bearbeitet werden. RTE wird im rechten Bedienfeld angezeigt | Optional | Erforderlich | Nicht zutreffend | Optional | Nicht zutreffend | Optional |
| `media` | Das bearbeitbare Element ist ein Asset, zum Beispiel ein Bild oder Video | Optional | Erforderlich | Optional<br>Liste der Kriterien für Bild- oder Videofilter, die an den Asset-Selektor übergeben werden | Optional | Nicht zutreffend | Optional |
| `container` | Das bearbeitbare Element verhält sich als Container für Komponenten, auch bekannt als Absatzsystem. | Abhängig von <br>siehe unten | Abhängig von <br>siehe unten | Optional<br>eine Liste der zulässigen Komponenten | Optional | Nicht zutreffend | Nicht zutreffend |
| `component` | Das bearbeitbare Element ist eine Komponente. Es werden keine zusätzlichen Funktionen hinzugefügt. Es ist erforderlich, um bewegliche/löschbare Teile des DOM anzuzeigen und die Eigenschaftenleiste und ihre Felder zu öffnen | Erforderlich | Nicht zutreffend | Nicht zutreffend | Optional | Optional | Nicht zutreffend |
| `reference` | Das bearbeitbare Element ist ein Verweis, zum Beispiel ein Inhaltsfragment, Experience Fragment oder Produkt | Abhängig von <br>siehe unten | Abhängig von <br>siehe unten | Optional<br>Liste der Filterkriterien für Inhaltsfragmente, Produkte oder Experience Fragments, die an den Referenz-Selektor übergeben werden | Optional | Optional | Nicht zutreffend |

Je nach Anwendungsfall kann `data-aue-prop` oder `data-aue-resource` erforderlich sein oder nicht. Zum Beispiel:

* `data-aue-resource` ist erforderlich, wenn Sie Inhaltsfragmente über GraphQL abfragen und die Liste im Kontext bearbeitbar machen möchten.
* `data-aue-prop` ist erforderlich, wenn Sie eine Komponente haben, die den Inhalt eines referenzierten Inhaltsfragments rendert, und die Referenz innerhalb der Komponente aktualisieren möchten.

## Verhaltensweisen {#behaviors}

| `data-aue-behavior` | Beschreibung |
|---|---|
| `component` | Kann verwendet werden, um eigenständigen Text, Rich-Text und Medien das Verhalten von Komponenten nachahmen zu lassen, sodass sie auch auf der Seite verschiebbar und löschbar sind. |
| `container` | Kann verwendet werden, damit Container als ihre eigenen Komponenten behandelt werden, sodass sie auf der Seite verschiebbar und löschbar sind. |

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zum universellen Editor finden Sie in diesen Dokumenten.

* [Einführung in den universellen Editor](introduction.md) – Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Inhalte in jeder Implementierung ermöglicht, um außergewöhnliche Erlebnisse bereitzustellen, die Inhaltsgeschwindigkeit zu erhöhen und ein modernes Entwicklererlebnis zu bieten.
* [Inhaltserstellung mit dem universellen Editor](/help/sites-cloud/authoring/universal-editor/authoring.md) – Erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und Inhaltsautoren ist, Inhalte mit dem universellen Editor zu erstellen.
* [Veröffentlichen von Inhalten mit dem universellen Editor](/help/sites-cloud/authoring/universal-editor/publishing.md) – Erfahren Sie, wie mit dem universellen Editor Inhalte veröffentlicht werden und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.
* [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) – Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.
* [Architektur des universellen Editors](architecture.md) – Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
* [Authentifizierung beim universellen Editor](authentication.md) – Erfahren Sie, wie beim universellen Editor authentifiziert wird.

