---
title: Verwenden des Rich-Text-Editors in [!DNL Adobe Experience Manager] , um Inhalte zu erstellen.
description: Verwenden des Rich-Text-Editors, um Inhalte zu erstellen [!DNL Experience Manager] .
exl-id: 15c175f8-11de-4475-87a9-920219a4c004
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: ht
source-wordcount: '286'
ht-degree: 100%

---

# Erstellen von Inhalten mit dem Rich-Text-Editor {#use-rich-text-editor-to-author-content}

Der Rich-Text-Editor (RTE) ist ein einfacher Baustein zum Hinzufügen von Textinhalten in [!DNL Adobe Experience Manager]. Darüber hinaus basieren viele andere Komponenten, die die Inhaltserstellung ermöglichen, auf dem RTE. Experience Manager-Entwickler können den RTE anpassen und Administratoren konfigurieren den RTE für die Verwendung durch Autoren.

## Bearbeitung im Kontext {#in-place-editing}

Auswählen einer textbasierten Komponente mit einem einzigen Klick, um die [Komponentensymbolleiste](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser) anzuzeigen.

![Die Komponentensymbolleiste](/help/sites-cloud/authoring/assets/editing-component-toolbar.png)

Durch erneutes Klicken oder erstmaliges Auswählen der Komponente mit einem langsamen doppelten Klick wird die Bearbeitung im Kontext geöffnet. Der Bearbeitungsmodus enthält eine Symbolleiste. Hier können Sie den Inhalt bearbeiten und die Formatierung ändern.

![Bearbeiten im Kontext mit dem RTE](/help/sites-cloud/authoring/assets/rte-in-place-editing.png)

In der Regel bietet die Symbolleiste die folgenden Optionen:

* **Format**: Markieren Sie den Text fett oder kursiv oder unterstreichen Sie ihn.
* **Listen**: Erstellen Sie Listen mit Aufzählungszeichen oder Nummerierungen und legen Sie den Einzug fest.
* **Hyperlink**: Erstellen Sie Links.
* **Verknüpfung aufheben**: Entfernen Sie Hyperlinks.
* **Vollbild**: Öffnet den Editor im Vollbildmodus.
* **Schließen**: Beendet die Bearbeitung.
* **Speichern**: Speichert die Änderungen.

## Bearbeitung im Vollbildmodus {#full-screen-editing}

Klicken Sie bei textbasierten Komponenten in der [Symbolleiste](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser) auf die Schaltfläche ![RTE-Vollbild](/help/sites-cloud/authoring/assets/editing-full-screen.png) für den Vollbildmodus, um den Rich-Text-Editor zu öffnen und den Rest des Seiteninhalts auszublenden.

Im Vollbildmodus werden alle konfigurierten Optionen angezeigt, die Sie zum Bearbeiten verwenden können. Die Verfügbarkeit der Optionen [hängt von der Konfiguration ab](/help/implementing/developing/extending/rich-text-editor.md).

![RTE im Vollbildmodus](/help/sites-cloud/authoring/assets/rte-full-screen.png)

Zusätzliche Optionen für den Rich-Text-Editor sind:

* **Anker**: Erstellt einen Anker im Text, zu dem Sie später eine Verknüpfung/einen Verweis herstellen können.
* **Text links ausrichten**.
* **Text zentrieren**.
* **Text rechts ausrichten**.

Klicken Sie auf „Minimieren“, um den Vollbildmodus zu schließen.

>[!TIP]
>
>Das Kopieren verschachtelter Listen aus [!DNL Microsoft Word] in den RTE kann zu inkonsistenten Ergebnissen führen. Fügen Sie sie stattdessen als Text ein und passen Sie das Format manuell an.

>[!MORELIKETHIS]
>
>* [Konfigurieren des Rich-Text-Editors](/help/implementing/developing/extending/rich-text-editor.md)
