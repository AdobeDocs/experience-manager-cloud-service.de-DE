---
title: Zugehörige Inhalte (Assets – Inhaltsfragmente)
description: Erfahren Sie, wie die zugehörige Inhaltsfunktion für AEM Inhaltsfragmente die Verbindung bereitstellt, damit Assets optional mit dem Fragment verwendet werden können.
exl-id: 8c8ad768-a210-4d34-bb47-2347599bcac9
source-git-commit: 62ede258711d0cb8d0b72479559c37221509e23f
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 59%

---

# Zugehörige Inhalte{#associated-content}

Für as a Cloud Service Inhaltsfragmente von Adobe Experience Manager (AEM) stellt die zugehörige Inhaltsfunktion (verfügbar im Original-Editor) die Verbindung bereit, damit Assets optional mit dem Fragment verwendet werden können. Dies bietet Flexibilität durch [Bereitstellung einer Reihe von Assets, auf die bei Verwendung des Inhaltsfragments zugegriffen werden kann](/help/assets/content-fragments/content-fragments.md#using-associated-content), während gleichzeitig dazu beiträgt, die für die Suche nach dem entsprechenden Asset erforderliche Zeit zu reduzieren. Diese Funktion kann sowohl für Ihre Headless Content-Bereitstellung als auch für die Seitenbearbeitung verwendet werden.

>[!NOTE]
>
>Inhaltsfragmente sind eine Sites-Eigenschaft, werden jedoch als **Assets** gespeichert.
>
>Es gibt zwei Editoren für die Erstellung von Inhaltsfragmenten. In diesem Abschnitt wird der ursprüngliche Editor beschrieben, auf den Sie hauptsächlich über das **Assets** Konsole.

## Hinzufügen von zugehörigen Inhalten {#adding-associated-content}

>[!NOTE]
>
>Es gibt diverse Methoden, um [visuelle Assets (zum Beispiel Fotos)](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets) zum Fragment und/oder der Seite hinzuzufügen.

Um zugehörige Inhalte zu verknüpfen, müssen zunächst [Medien-Assets zu einer Sammlung hinzugefügt werden](/help/assets/manage-collections.md). Danach können Sie Folgendes tun:

1. Öffnen Sie das Fragment und wählen Sie im seitlichen Bedienfeld **Zugehörige Inhalte** aus.

   ![Zugehörige Inhalte](assets/cfm-assoc-content-01.png)

1. Je nachdem, ob bereits Sammlungen zugeordnet wurden oder nicht, wählen Sie eine der folgenden Optionen aus:

   * **Inhalt verknüpfen**: Die erste verknüpfte Sammlung
   * **Sammlung verknüpfen**: Zugeordnete Sammlungen sind bereits konfiguriert

1. Wählen Sie die erforderliche Sammlung aus.

   Optional können Sie das eigentliche Fragment zur ausgewählten Sammlung hinzufügen. Dies hilft bei der Nachverfolgung.

   ![Sammlung auswählen](assets/cfm-assoc-content-02.png)

1. Bestätigen (mit **Auswählen**). Die Sammlung wird als zugeordnet aufgelistet.

   ![Bestätigte Verknüpfung](assets/cfm-assoc-content-03.png)

## Bearbeiten zugehöriger Inhalte {#editing-associated-content}

Nachdem Sie eine Sammlung zugewiesen haben, können Sie Folgendes tun:

* Die Verknüpfung **aufheben**.
* **Assets zur Sammlung hinzufügen**.
* Ein Asset für weitere Aktionen auswählen.
* Das ausgewählte Asset bearbeiten.
