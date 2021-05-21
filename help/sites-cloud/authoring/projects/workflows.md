---
title: Arbeiten mit Projekt-Workflows
description: Eine Vielzahl von Projekt-Workflows ist bereits vorkonfiguriert.
exl-id: a5c9a6df-7def-43f3-b41b-524a4f4211e9
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 100%

---

# Arbeiten mit Projekt-Workflows {#working-with-project-workflows}

Folgende Projekt-Workflows sind im Lieferumfang enthalten:

* **Workflow für Projektbestätigung** - Dieser Workflow ermöglicht es Ihnen, Inhalte einem Benutzer zuzuweisen, sie zu prüfen und dann zu bestätigen.
* **Launch anfordern** - Ein Workflow, der einen Launch anfordert.
* **Einstiegsseite anfordern** - Dieser Workflow fordert eine Landingpage an.
* **E-Mail anfordern** - Workflow zum Anfordern einer E-Mail.
* **DAM-Kopie erstellen und übersetzen und DAM-Sprachkopie erstellen** - Erstellt übersetzte Binärdateien, Metadaten und Tags für Assets und Ordner.

Je nachdem, welche Projektvorlage Sie auswählen, sind bestimmte Workflows verfügbar:

|  | **Einfaches Projekt** | **Medienprojekt** | **Übersetzungsprojekt** |
|---|:-:|:-:|:-:|
| Kopie anfordern |  | x |  |
| Produkt-Fotoshooting |  | x |  |
| Projekt-Genehmigung | x |  |  |
| Launch anfordern | x |  |  |
| Einstiegsseite anfordern | x |  |  |
| E-Mail anfordern | x |  |  |
| DAM-Sprachkopie erstellen&amp;ast; |  |  | x |
| DAM-Sprachkopie erstellen und übersetzen&amp;ast; |  |  | x |

>[!NOTE]
>
>&amp;ast; Diese Workflows werden nicht auf der Kachel **Workflow** in Projekten gestartet. Weitere Informationen finden Sie unter [Erstellen von Sprachkopien für Assets](/help/sites-cloud/administering/translation/managing-projects.md).

Das Starten und Abschließen eines Workflows ist unabhängig vom gewählten Workflow immer gleich. Nur die Schritte dazwischen ändern sich.

Sie starten einen Workflow direkt in Projekten (mit Ausnahme von „DAM-Sprachkopie erstellen“ bzw. „DAM-Sprachkopie erstellen und übersetzen“). Informationen über alle ausstehenden Aufgaben in einem Projekt werden in der Kachel **Aufgaben** aufgeführt. Benachrichtigungen für Aufgaben, die ausgeführt werden müssen, werden neben dem Benutzersymbol angezeigt.

Weitere Informationen zum Arbeiten mit Workflows in AEM finden Sie unter:

* [Teilnehmen an Workflows](/help/sites-cloud/authoring/workflows/participating.md)
* [Anwenden von Workflows auf Seiten](/help/sites-cloud/authoring/workflows/applying.md)
* [Konfigurieren von Workflows](/help/sites-cloud/administering/workflows-administering.md)

Dieser Abschnitt beschreibt die Workflows, die für Projekte verfügbar sind.

## Workflow „Kopie anfordern“  {#request-copy-workflow}

Mit diesem Workflow können Sie ein Manuskript von einem Benutzer anfordern und es dann genehmigen. So starten Sie den Workflow „Kopie anfordern“:

1. Wählen Sie in Ihrem Medienprojekt das **Plussymbol** in der Kachel **Workflows** aus und wählen Sie dann **Workflow „Kopie anfordern“** aus.
1. Geben Sie einen Manuskripttitel und eine kurze Zusammenfassung dazu ein, was Sie anfordern. Geben Sie bei Bedarf eine Zielwortanzahl, eine Aufgabenpriorität und ein Fälligkeitsdatum ein.

   ![Workflow „Kopie anfordern“](/help/sites-cloud/authoring/assets/projects-request-copy.png)

1. Klicken Sie auf **Erstellen**. Der Workflow startet. Die Aufgabe wird in der Kachel **Aufgaben** angezeigt.

   ![Kopie anfordern hinzugefügt](/help/sites-cloud/authoring/assets/projects-request-copy-add.png)

## Workflow für Projektbestätigung {#project-approval-workflow}

Im Workflow für Projektbestätigung weisen Sie Inhalte einem Benutzer zu, überprüfen diese und genehmigen sie dann.

1. Wählen Sie in Ihrem einfachen Projekt das **`+`**-Symbol in der Kachel **Workflows** aus und wählen Sie dann **Workflow für Projektbestätigung** aus.
1. Geben Sie einen Titel ein und wählen Sie aus, welchem Mitglied der Teamliste Sie den Workflow zuweisen möchten. Geben Sie bei Bedarf eine Beschreibung, einen Inhaltspfad, eine Aufgabenpriorität und ein Fälligkeitsdatum ein.

   ![Bestätigung anfordern](/help/sites-cloud/authoring/assets/projects-approval.png)

1. Klicken Sie auf **Erstellen**. Der Workflow startet. Die Aufgabe wird in der Kachel **Aufgaben** angezeigt.

   ![Bestätigung anfordern hinzugefügt](/help/sites-cloud/authoring/assets/projects-approval-add.png)

## Workflow „Launch anfordern“ {#request-launch-workflow}

Mit diesem Workflow können Sie einen Launch anfordern.

1. Wählen Sie in Ihrem einfachen Projekt das **Plussymbol** in der Kachel **Workflows** aus und wählen Sie dann **Workflow „Launch anfordern“** aus.
1. Geben Sie einen Titel für den Launch ein und geben Sie den Launch-Quellpfad an. Sie können bei Bedarf auch eine Beschreibung und ein Live-Datum hinzufügen. Wählen Sie „Quellseiten-Live-Daten erben“ oder „Unterseiten ausschließen“ aus, je nachdem, wie der Launch sich verhalten soll.

   ![Launch anfordern](/help/sites-cloud/authoring/assets/projects-request-launch.png)

1. Klicken Sie auf **Erstellen**. Der Workflow startet. Der Workflow wird in der Liste **Workflows** angezeigt (klicken Sie auf das Auslassungszeichen **…** auf der Kachel **Workflows**, um auf diese Liste zugreifen).

## Workflow „Sprachkopie erstellen (und übersetzen)“ für Assets {#create-and-translate-language-copy-workflow-for-assets}

Die Workflows **Sprachkopie erstellen** und **Sprachkopie erstellen und übersetzen** werden in „Erstellen von Sprachkopien für Assets“ genauer erläutert.
