---
title: Learn Content Modeling Basics
description: Learn the basic of modeling content for your Headless CMS using Content Fragments.
exl-id: dc460490-dfc8-4a46-a468-3d03e593447d
source-git-commit: 3f6c96da3fd563b4c8db91ab1bc08ea17914a8c1
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 46%

---

# Learn the Content Modeling Basics for Headless with AEM {#content-modeling-headless-basics}

## The Story so Far {#story-so-far}

[](overview.md)[](introduction.md)

This article builds on these so you understand how to model your content for your AEM headless project.

## Ziel {#objective}

* **Zielgruppe**: Anfänger
* ****

## Content Modeling with Content Fragment Models {#architect-content-fragment-models}

Content (Data) Modeling is a set of established techniques, often used when developed relationship databases, so what does Content Modeling mean for AEM Headless?

### Vorteile {#why}

Um sicherzustellen, dass Ihr Programm die erforderlichen Inhalte konsistent und effizient von AEM anfragen und empfangen kann, müssen diese Inhalte strukturiert sein.

Das bedeutet, dass Ihr Programm die Form der Antwort im Voraus kennt und daher weiß, wie sie verarbeitet wird. Dies ist viel einfacher als das Empfangen von Freiforminhalten, die geparst werden müssen, um festzustellen, was sie enthalten und wie sie daraus folgend verwendet werden können.

### Einführung in das Wie? {#how}

AEM verwendet Inhaltsfragmente, um die Strukturen bereitzustellen, die für die Headless-Bereitstellung Ihrer Inhalte an Ihre Programme erforderlich sind.

Die Struktur Ihres Inhaltsmodells wird:

* durch die Definition Ihres Inhaltsfragmentmodells umgesetzt,
* als Grundlage der Inhaltsfragmente verwendet, die für die Inhaltserstellung verwendet werden.

>[!NOTE]
>
>The Content Fragment Models are also used as the basis of the AEM GraphQL Schemas, used for retrieving your content - more about that in the Developer Journey.

Anfragen für Ihre Inhalte werden mit der AEM-GraphQL-API gestellt, einer angepassten Implementierung der standardmäßigen GraphQL-API. The AEM GraphQL API allows applications to perform (complex) queries on your Content Fragments, with each query being according to a specific model type.

Die zurückgegebenen Inhalte können dann von Ihren Programmen verwendet werden.

## Erstellen der Struktur mit Inhaltsfragmentmodellen {#create-structure-content-fragment-models}

Inhaltsfragmentmodelle bieten verschiedene Mechanismen, mit denen Sie die Struktur Ihrer Inhalte definieren können.

Ein Inhaltsfragmentmodell beschreibt eine Entität.

>[!NOTE]
>Content Fragment functionality must be enabled in the Configuration Browser so that you can create new models.

>[!TIP]
>
>Das Modell sollte so benannt werden, dass der Inhaltsautor weiß, welches Modell er beim Erstellen eines Inhaltsfragments auswählen soll.

Innerhalb eines Modells:

1. Mit **Datentypen** können Sie die einzelnen Attribute definieren.
Definieren Sie beispielsweise das Feld mit dem Namen eines Lehrers als **Text** und dessen Dienstjahre als **Zahl**.
1. Mit den Datentypen **Inhaltsreferenz** und **Fragmentreferenz** können Sie Beziehungen zu anderen Inhalten in AEM erstellen.
1. Mit dem Datentyp **Fragmentreferenz** können Sie mehrere Ebenen der Struktur umsetzen, indem Sie Ihre Inhaltsfragmente verschachteln (je nach Modelltyp). Dies ist für Ihre Inhaltsmodellierung von entscheidender Bedeutung.

Beispiel:

![](assets/headless-modeling-01.png "")

## Datentypen {#data-types}

AEM stellt die folgenden Datentypen bereit, mit denen Sie Ihren Inhalt modellieren können:

* Einzeilentext
* Mehrzeilentext
* Zahl
* Boolesch
* Datum und Uhrzeit
* Aufzählung
* Tags
* Inhaltsreferenz
* Fragmentreferenz
* JSON-Objekt

>[!NOTE]
>
>Further details are available under Content Fragment Models - Data Types.

## Verweise und verschachtelte Inhalte {#references-nested-content}

Zwei Datentypen bieten Verweise auf Inhalte außerhalb eines bestimmten Fragments:

* **Inhaltsreferenz**
Dies bietet einen einfachen Verweis auf andere Inhalte beliebigen Typs.
Sie können beispielsweise auf ein Bild an einer bestimmten Stelle verweisen.

* **Fragmentreferenz**
Dies bietet Verweise auf andere Inhaltsfragmente.
Dieser Referenztyp wird verwendet, um verschachtelte Inhalte zu erstellen und die Beziehungen einzuführen, die zum Modellieren Ihres Inhalts erforderlich sind.
Der Datentyp kann so konfiguriert werden, dass Fragmentautoren folgende Möglichkeiten haben:
   * Direktes Bearbeiten des referenzierten Fragments
   * Erstellen eines neuen Inhaltsfragments basierend auf dem entsprechenden Modell

>[!NOTE]
>
>You can also create ad hoc references by using links within Text blocks.

## Levels of Structure (Nested Fragments) {#levels-of-structure-nested-fragments}

****

** This allows the headless application to follow the connections and access the content as necessary.

>[!NOTE]
>
>**

Fragment References do just that - they allow you to reference another fragment.

For example, you might have the following Content Fragment Models defined:

* Stadt
* Unternehmen
* Person
* Auszeichnungen

Seems pretty straightforward, but of course a Company has both a CEO and Employees....and these are all people, each defined as a Person.

And a Person can have an Award (or maybe two).

* My Company - Company
   * CEO - Person
   * Employee(s) - Person
      * Personal Award(s) - Award

And that&#39;s just for starters. Depending on the complexity, an Award could be Company-specific, or a Company could have its main office in a specific City.

Representing these interrelationships can be achieved with Fragment References, as they are understood by you (the architect), your content author and the headless applications.

## Wie geht es weiter {#whats-next}

[](model-structure.md) This will introduce and discuss the various references available, and how to create levels of structure with the Fragment References - a key part of modeling for headless.

## Zusätzliche Ressourcen {#additional-resources}

* [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)

   * [Content Fragment Models - Data Types](/help/assets/content-fragments/content-fragments-models.md#data-types)

* [Authoring – Konzepte](/help/sites-cloud/authoring/getting-started/concepts.md)

* [](/help/sites-cloud/authoring/getting-started/basic-handling.md)************

* [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md)
