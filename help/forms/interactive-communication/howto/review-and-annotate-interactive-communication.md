---
title: Überprüfen und Kommentieren einer interaktiven Kommunikation
description: Erfahren Sie, wie Reviewer Feedback direkt an Komponenten auf der Arbeitsfläche für interaktive Kommunikation anheften können und wie Autoren dieses Feedback verfolgen und auflösen können, ohne den Editor für interaktive Kommunikation verlassen zu müssen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="Gilt für AEM Forms."
exl-id: review-annotate-interactive-communication
source-git-commit: b11e1b28aabba9e03553dc9e9394bff111facfee
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 2%

---


# Überprüfen und Kommentieren einer interaktiven Kommunikation

Das Überprüfen einer interaktiven Kommunikation bedeutet in der Regel das Freigeben von Screenshots, das Erstellen von E-Mails oder das Abhalten von Seitengesprächen, von denen keine auf das genaue Feld oder den Abschnitt, über das bzw. den gesprochen wird, zurückgeführt werden kann. Anmerkungen ermöglichen dies, indem sie Prüferinnen und Prüfern eine dedizierte, schreibgeschützte Ansicht der interaktiven Kommunikation geben, in der sie auf eine beliebige Komponente klicken und einen Kommentar an genau diese Stelle auf der Arbeitsfläche anheften können.

Alle Reviewer verwenden dieselbe Anmerkungsansicht, sodass das Feedback für alle an einer Stelle sichtbar ist. Anmerkungen sind nur während des Autoren- und Überprüfungsprozesses vorhanden und werden nie in veröffentlichten oder kundenorientierten Ausgaben angezeigt.

| Wer? | Vorteil |
|-----|---------|
| **Prüfer** | Geben Sie präzises, kontextbezogenes Feedback, ohne die interaktive Kommunikation zu bearbeiten oder versehentliche Änderungen zu riskieren. |
| **Autor (Designer für interaktive Kommunikation / Inhaber)** | Erhalten Sie umsetzbares Feedback, das mit bestimmten Komponenten verknüpft ist, mit einer klaren Möglichkeit, jedes Überprüfungselement zu verfolgen und zu schließen. |

## Bevor Sie beginnen

Reviewer und Autoren müssen jeweils den entsprechenden vorkonfigurierten Reviewern und Autorengruppen zugewiesen werden, bevor sie auf die Arbeitsfläche für Anmerkungen zugreifen oder den Workflow zum Auflösen aufrufen können.

>[!NOTE]
>
> Überprüfen Sie die genauen Gruppennamen für Ihre Umgebung mit Ihrem AEM-Administrator, bevor Sie Zugriff zuweisen.

## Anmerkung hinzufügen

Führen Sie diese Schritte als Prüferin bzw. Prüfer aus.

1. Navigieren Sie zu **Forms und Dokumente** wählen Sie die interaktive Kommunikation aus, die Sie überprüfen möchten, und klicken Sie auf **Anmerken** in der Symbolleiste.

   ![Anmerken 1](/help/forms/interactive-communication/assets/add-annotate1.png)

   Die schreibgeschützte **Anmerkungsansicht** wird geöffnet, wobei die interaktive Kommunikation auf der Arbeitsfläche angezeigt wird.

   ![Anmerken 2](/help/forms/interactive-communication/assets/add-annotate2.png)

1. Um einen Kommentar an eine bestimmte Komponente anzuhängen, klicken Sie auf diese Komponente auf der Arbeitsfläche.

   ![Anmerken 3](/help/forms/interactive-communication/assets/add-annotate3.png)

1. Geben Sie Ihr Feedback in das Kommentarfeld ein und klicken Sie dann auf die blaue Post-Schaltfläche, um den Kommentar zu speichern.

   ![Anmerken 4](/help/forms/interactive-communication/assets/add-annotate4.png)

1. Wiederholen Sie die Schritte 2 und 3 für jede Komponente, die Feedback benötigt.

   Klicken Sie beispielsweise auf den Block Bankadresse und fügen Sie **Adresse aktualisieren** hinzu. Klicken Sie dann in der Tabelle Fahrzeugdetails auf die Zelle **Marke und Modell** und fügen Sie **Fahrzeugmodell aktualisieren** hinzu.

1. Wenn Sie alle Kommentare hinzugefügt haben, klicken Sie auf **Feedback senden**.

   ![Anmerken 5](/help/forms/interactive-communication/assets/add-annotate5.png)

   Eine Erfolgsmeldung bestätigt, dass Ihr Feedback gesendet wurde. Jeder Kommentar wird als Anmerkungs-Pin an der ausgewählten Position angezeigt, und alle anderen Reviewer können ihn sofort sehen.

## Überprüfen der Anmerkungen

Führen Sie diese Schritte als Autor aus.

1. Navigieren Sie zu **Forms und Dokumente** wählen Sie die interaktive Kommunikation aus und klicken Sie auf **Bearbeiten**, um sie im Editor für interaktive Kommunikation zu öffnen.

   ![Resolve 1](/help/forms/interactive-communication/assets/add-annotate6.png)

1. Wählen Sie eine Komponente aus, die einen Reviewer-Anmerkungs-Pin anzeigt.

   Wählen Sie beispielsweise den Block Bankadresse aus. Erweitern Sie im **Eigenschaften** den Abschnitt **Kommentare**, um die angehängte Anmerkung anzuzeigen. Der Reviewer-Kommentar **Aktualisierungsadresse** wird hier angezeigt.

   ![Resolve 2](/help/forms/interactive-communication/assets/add-annotate7.png)

1. Überprüfen Sie jeden Kommentar und nehmen Sie die erforderlichen Änderungen am Design vor.

   Aktualisieren Sie beispielsweise den Text der Bankadresse, wie vom Prüfer angefordert.

   ![Resolve 3](/help/forms/interactive-communication/assets/add-annotate8.png)

1. Nachdem Sie einen Kommentar beantwortet haben, klicken Sie im Abschnitt ******Kommentare** auf „Auflösen“.

1. Wiederholen Sie die Schritte 2 bis 4 für jede verbleibende Anmerkung.

   Wählen Sie beispielsweise die Zelle **Marke und Modell** in der Tabelle Fahrzeugdetails aus, aktualisieren Sie den Wert wie im Kommentar **Fahrzeugmodell aktualisieren** angefordert auf **Creta SX(O)** und markieren Sie ihn als **Resolved**.

   ![Resolve 4](/help/forms/interactive-communication/assets/add-annotate9.png)

1. Klicken Sie auf **Speichern**.

   ![Resolve 5](/help/forms/interactive-communication/assets/add-annotate10.png)

   Eine aufgelöste Anmerkungspin ändert sich von offen in geschlossen (grau), wodurch abgeschlossene Prüfelemente von den noch ausstehenden unterschieden werden. Der aufgelöste Kommentar bleibt in der Historie sichtbar, sodass das vollständige Überprüfungsprotokoll beibehalten wird.

## Überlegungen

- Reviewer und Autoren müssen den entsprechenden vorkonfigurierten Gruppen zugewiesen werden. Benutzerdefinierte Gruppenkonfigurationen werden nicht unterstützt.

- Wenn Sie die Größe einer Komponente verringern, nachdem eine Anmerkung darauf platziert wurde, bleibt der Stift an der ursprünglichen Position, anstatt sich mit der Komponentenbegrenzung zu bewegen.

- Anmerkungen zu Fragmenten in einem Dokument werden nicht unterstützt.

- Anmerkungen in der **table**-Komponente werden noch nicht unterstützt.

## Häufig gestellte Fragen

**Wie kann ich einen Kommentar an ein bestimmtes Feld statt an einen allgemeinen Bereich anhängen?**
Klicken Sie direkt auf die Komponente in der Arbeitsfläche für Anmerkungen. Die Nadel ist mit dieser Komponente verbunden und wird allen Reviewern in derselben Anmerkungsansicht angezeigt.

**Woher weiß ein Autor, welche Komponenten offene Anmerkungen haben?**
Anmerkungspins sind direkt auf der Arbeitsfläche im Editor für interaktive Kommunikation sichtbar. Wenn Sie eine Komponente auswählen, werden alle angehängten Kommentare im Bedienfeld Eigenschaften angezeigt.

**Werden Anmerkungen in der veröffentlichten PDF-Ausgabe angezeigt?**
Anzahl Anmerkungen sind nur Teil des Authoring- und Review-Workflows. Sie werden nie in veröffentlichte oder kundenorientierte Ausgaben aufgenommen.

**Was ist der Unterschied zwischen einer Anmerkung und einem Kommentar?**
Eine Anmerkung ist ein positionierter Pin, der an eine bestimmte Komponente auf der Arbeitsfläche gebunden und in der schreibgeschützten Anmerkungsansicht sichtbar ist. Ein Kommentar ist ein allgemeiner Hinweis, der an die interaktive Kommunikation als Ganzes angehängt und im Bedienfeld „Kommentare“ im Editor hinzugefügt wird. Einzelheiten [ Kommentare finden Sie unter ](/help/forms/interactive-communication/versioning-and-commenting-in-interactive-communication-editor.md) und Kommentare .

## Siehe auch

- [Erstellen einer interaktiven Kommunikation](/help/forms/interactive-communication/create-interactive-communication.md)
- [Vorlagensperre im Editor für interaktive Kommunikation](/help/forms/interactive-communication/enable-template-lock.md)
- [Versionierung und Kommentare im Editor für interaktive Kommunikation](/help/forms/interactive-communication/versioning-and-commenting-in-interactive-communication-editor.md)

