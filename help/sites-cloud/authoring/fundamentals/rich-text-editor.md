---
title: Use the Rich Text Editor in [!DNL Adobe Experience Manager] to author content.
description: Use the [!DNL Experience Manager] Rich Text Editor to author content.
translation-type: tm+mt
source-git-commit: 5437329c55bd7da6d8b966a7f01c9e57ff1feb59
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 42%

---


# Verwenden des Rich-Text-Editors zum Erstellen von Inhalten {#use-rich-text-editor-to-author-content}

Der Rich Text Editor (RTE) ist ein einfacher Baustein zum Hinzufügen von Textinhalten zu [!DNL Adobe Experience Manager]Texten. Darüber hinaus basieren viele andere Komponenten, die Authoring ermöglichen, auf RTE. Experience Manager-Entwickler können RTE anpassen und Administratoren konfigurieren RTE für die Verwendung durch Autoren.

## Bearbeitung im Kontext {#in-place-editing}

Auswählen einer textbasierten Komponente mit einem einzigen Klick, um die [Komponentensymbolleiste](/help/sites-cloud/authoring/fundamentals/editing-content.md#component-toolbar)anzuzeigen.

![Die Komponenten-Symbolleiste](/help/sites-cloud/authoring/assets/editing-component-toolbar.png)

Durch erneutes Klicken oder erstmaliges Auswählen der Komponente mit einem langsamen Klick auf die Dublette wird die ersetzende Bearbeitung geöffnet. Der Bearbeitungsmodus enthält eine Symbolleiste. Sie können den Inhalt bearbeiten und grundlegende Änderungen an der Formatierung vornehmen.

![Bearbeiten im Kontext mit dem RTE](/help/sites-cloud/authoring/assets/rte-in-place-editing.png)

In der Regel bietet die Symbolleiste die folgenden Optionen:

* **Format**: Markieren Sie den Text fett oder kursiv oder unterstreichen Sie ihn.
* **Listen**: Erstellen Sie Listen mit Aufzählungszeichen oder Nummerierungen und legen Sie den Einzug fest.
* **Hyperlink**: Erstellen Sie Links.
* **Verknüpfung aufheben**: Entfernen Sie Hyperlinks.
* **Vollbild**: Öffnen Sie den Editor im Vollbildmodus.
* **Schließen**: Beenden Sie die Bearbeitung.
* **Speichern**: Speichern Sie die Änderungen.

## Bearbeitung im Vollbildmodus {#full-screen-editing}

For text-based components, click the full-screen mode ![RTE full screen button](/help/sites-cloud/authoring/assets/editing-full-screen.png) from the [toolbar](/help/sites-cloud/authoring/fundamentals/editing-content.md#component-toolbar) to open the rich text editor and hides the rest of the page content.

Im Vollbildmodus werden alle konfigurierten Optionen angezeigt, die Sie zum Bearbeiten verwenden können. Die Verfügbarkeit der Optionen hängt von der Konfiguration ab. <!--Full screen mode displays all the configured options that you can use for authoring. The availability of options [depends on the configuration](/help/sites-administering/rich-text-editor.md).-->

![RTE im Vollbildmodus](/help/sites-cloud/authoring/assets/rte-full-screen.png)

Zu den weiteren Optionen des Rich-Text-Editors gehören:

* **Anker**: Erstellen Sie einen Anker im Text, zu dem Sie später eine Verknüpfung/einen Verweis herstellen können.
* **Text links ausrichten**.
* **Text zentrieren**.
* **Text rechts ausrichten**.

Klicken Sie auf „Minimieren“, um den Vollbildmodus zu schließen.

>[!Tipp]
>
>Copying nested lists from [!DNL Microsoft Word] into the RTE can give inconsistent results. Fügen Sie sie stattdessen als Text ein und passen Sie das Format manuell an.

>[!MORELIKETHIS]
>
>* [Rich-Text-Editoren konfigurieren](/help/implementing/developing/extending/rich-text-editor.md)

