---
title: Arbeiten mit Projekt-Workflows
description: Standardmäßig sind zahlreiche vorkonfigurierte Projekt-Workflows verfügbar.
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: a5c9a6df-7def-43f3-b41b-524a4f4211e9
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 99%

---

# Arbeiten mit Projekt-Workflows {#working-with-project-workflows}

Folgende vorkonfigurierte Projekt-Workflows sind im Lieferumfang enthalten:

* **Projektgenehmigungs-Workflow** – Mit diesem Workflow können Sie Inhalte einer Benutzerin bzw. einem Benutzer zuzuweisen, prüfen und bestätigen.
* **Launch anfragen** - Ein Workflow, der einen Launch anfordert.
* **Einstiegsseite anfragen** - Dieser Workflow fragt eine Landingpage an.
* **E-Mail anfordern** - Workflow zum Anfordern einer E-Mail.
* **DAM-Kopie erstellen und übersetzen und DAM-Sprachkopie erstellen**: Erstellt übersetzte Binärdateien, Metadaten und Tags für Assets und Ordner.

Je nachdem, welche Projektvorlage Sie auswählen, stehen Ihnen bestimmte Workflows zur Verfügung:

|   | **Einfaches Projekt** | **Übersetzungsprojekt** |
|---|:-:|:-:|
| Projektgenehmigungs-Workflow | x |  |
| Launch anfragen | x |  |
| Landingpage anfragen | x |  |
| E-Mail anfragen | x | |
| DAM-Sprachkopie erstellen&amp;ast; |  | x |
| DAM-Sprachkopie erstellen und übersetzen&amp;ast; |   | x |

>[!NOTE]
>
>&amp;ast; Diese Workflows werden nicht auf der Kachel **Workflow** in Projekten gestartet. Weitere Informationen finden Sie unter [Erstellen von Sprachkopien für Assets](/help/sites-cloud/administering/translation/managing-projects.md).

Das Starten und Abschließen eines Workflows ist unabhängig vom gewählten Workflow immer gleich. Nur die Schritte ändern sich.

Sie starten einen Workflow direkt in Projekten (mit Ausnahme von „DAM-Kopie erstellen und übersetzen“ und „DAM-Sprachkopie erstellen“). Informationen zu ausstehenden Aufgaben in einem Projekt finden Sie in der Kachel **Aufgaben**. Benachrichtigungen für Aufgaben, die ausgeführt werden müssen, werden neben dem Benutzersymbol angezeigt.

Weitere Informationen zum Arbeiten mit Workflows in AEM finden Sie unter:

* [Teilnehmen an Workflows](/help/sites-cloud/authoring/workflows/participating.md)
* [Anwenden von Workflows auf Seiten](/help/sites-cloud/authoring/workflows/applying.md)
* [Konfigurieren von Workflows](/help/sites-cloud/administering/workflows-administering.md)

Dieser Abschnitt beschreibt die Workflows, die für Projekte verfügbar sind.

## Workflow für Projektbestätigung {#project-approval-workflow}

Im Workflow für Projektbestätigung weisen Sie Inhalte einem Benutzer zu, überprüfen diese und genehmigen sie dann.

1. Wählen Sie in Ihrem einfachen Projekt das **`+`**-Symbol in der Kachel **Workflows** aus und wählen Sie dann **Workflow für Projektbestätigung** aus.
1. Geben Sie einen Titel ein und wählen Sie aus, welchem Mitglied der Teamliste Sie den Workflow zuweisen möchten. Geben Sie bei Bedarf eine Beschreibung, einen Inhaltspfad, eine Aufgabenpriorität und ein Fälligkeitsdatum ein.

   ![Bestätigung anfordern](/help/sites-cloud/authoring/assets/projects-approval.png)

1. Klicken Sie auf **Erstellen**. Der Workflow startet. Die Aufgabe wird in der Kachel **Aufgaben** angezeigt.

## Workflow „Launch anfordern“ {#request-launch-workflow}

Mit diesem Workflow können Sie einen Launch anfordern.

1. Wählen Sie in Ihrem einfachen Projekt das **Plussymbol** in der Kachel **Workflows** aus und wählen Sie dann **Workflow „Launch anfordern“** aus.
1. Geben Sie einen Titel für den Launch ein und geben Sie den Launch-Quellpfad an. Sie können bei Bedarf auch eine Beschreibung und ein Live-Datum hinzufügen. Wählen Sie „Quellseiten-Live-Daten erben“ oder „Unterseiten ausschließen“ aus, je nachdem, wie der Launch sich verhalten soll.

   ![Launch anfordern](/help/sites-cloud/authoring/assets/projects-request-launch.png)

1. Klicken Sie auf **Erstellen**. Der Workflow startet. Der Workflow wird in der Liste **Workflows** angezeigt (klicken Sie auf das Auslassungszeichen **…** auf der Kachel **Workflows**, um auf diese Liste zugreifen).

## Workflow „Sprachkopie erstellen (und übersetzen)“ für Assets {#create-and-translate-language-copy-workflow-for-assets}

Die Workflows **Sprachkopie erstellen** und **Sprachkopie erstellen und übersetzen** [werden in „Erstellen von Sprachkopien für Assets“ genauer erläutert](/help/assets/translate-assets.md).
