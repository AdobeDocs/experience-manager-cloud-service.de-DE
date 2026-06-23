---
title: Verschieben einer Komponente auf die Musterseite
description: Erfahren Sie, wie Sie eine Komponente von einer Design-Seite auf die Master-Seite verschieben können, damit sie konsistent auf allen Seiten einer interaktiven Kommunikation angezeigt wird.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="Gilt für AEM Forms)."
exl-id: move-component-to-master-page-ic-editor
source-git-commit: 38a10bc5caaa1615188d2e6623b9d432bd4c3d69
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 2%

---


# Verschieben einer Komponente auf die Musterseite

Die Musterseite in einer interaktiven Kommunikation definiert Elemente, die sich auf jeder Seite wiederholen, Kopfzeilen, Fußzeilen, Wasserzeichen, Seitenzahlen und alle anderen Inhalte, die im gesamten Dokument konsistent angezeigt werden müssen. Komponenten, die sich auf einzelnen Design-Seiten befinden, werden dagegen nur auf diesen spezifischen Seiten angezeigt.

Wenn Sie eine Komponente auf einer regulären Seite entwerfen und später entscheiden, dass sie zu jeder Seite gehört, können Sie sie direkt von der Arbeitsfläche auf die Musterseite verschieben, ohne sie löschen und neu erstellen zu müssen. Die Komponente wird an der gleichen visuellen Position platziert wie auf der Design-Seite.

| Wer? | Vorteil |
|-----|---------|
| **Author (Interactive Communication Designer)** | Eine Komponente auf jeder Seite in einer Aktion hochstufen, anstatt sie auf allen Design-Seiten manuell zu duplizieren. |
| **Vorlagen-Designer** | Verfeinern Sie die Vorlagenstruktur nach dem ersten Design, ohne Komponenten von Grund auf neu zu erstellen. |

## Verschieben einer Komponente auf die Musterseite

Ein gängiges Anwendungsbeispiel ist das Verschieben von sich wiederholenden Kopfzeilenelementen - wie **Banklogo** und **Bankadresse** - von einer Design-Seite auf die Musterseite, damit sie auf jeder Seite der interaktiven Kommunikation angezeigt werden.

1. Öffnen Sie die interaktive Kommunikation im Editor für interaktive Kommunikation.

1. Navigieren Sie auf **Registerkarte** Design“ zur Design-Seite, die die zu verschiebenden Komponenten enthält.

1. Klicken Sie mit der rechten Maustaste auf die Komponente auf der Arbeitsfläche.

   Klicken Sie beispielsweise mit der rechten Maustaste auf den Textblock Bankadresse .

1. Wählen Sie im Kontextmenü die Option **Verschieben nach** und dann **Musterseite** aus.

   ![Zur Musterseite wechseln](/help/forms/interactive-communication/assets/move-to-master-page.png)

   Die Komponente wird aus der Designseite entfernt und der Musterseite an derselben visuellen Position hinzugefügt. Er wird jetzt auf jeder Seite angezeigt, die diese Musterseite verwendet.

1. Wiederholen Sie die Schritte 3 und 4 für jede Komponente, die Sie auf der Musterseite verwenden möchten.

   Wenn Sie beispielsweise die Bankadresse verschoben haben, wiederholen Sie die gleichen Schritte, um das Banklogo zu verschieben.

1. Wählen Sie die Registerkarte **Master** aus, um zu überprüfen, ob das Banklogo und die Bankadresse an den erwarteten Positionen angezeigt werden.

   ![Zur Musterseite wechseln](/help/forms/interactive-communication/assets/move-to-master-page2.png)

## Mögliche Komponenten

Nicht alle Komponententypen können auf die Musterseite verschoben werden. Die folgenden Typen sind **nicht geeignet** für diese Aktion:

| Nicht auswählbarer Komponententyp | Grund |
|---------------------------|--------|
| Inhaltsbereiche | Definieren der Regionen, in denen der Inhalt der Design-Seite fließt; muss auf Design-Seiten bleiben |
| Seitenbereiche | Strukturelle Seitencontainer, die mit einzelnen Seiten verknüpft sind |
| Seitensätze | Mehrseitige Gruppierungen; kann nicht unabhängig verschoben werden |
| Fragmente | Wiederverwendbare Dokumentblöcke werden unabhängig verwaltet |
| Teilformular | Container-Komponenten mit ihrem eigenen Layout-Umfang |
| Tabellenzeilen | Elemente auf Zeilenebene, die zu einer Tabellenstruktur gehören |
| Tabellenzellen | Elemente auf Zellenebene, die zu einer Tabellenstruktur gehören |
| Optionsschalter | Auswahlsteuerelemente, die Teil einer Formulardatenstruktur sind |

Komponenten mit einer **Inhaltssperre** oder **Layout-Sperre** sind ebenfalls nicht zulässig. Entfernen Sie die Sperre, bevor Sie sie verschieben, oder planen Sie die Platzierung der Komponente auf der Musterseite, wenn Sie die Vorlage entwerfen. Siehe [Vorlagensperre im Editor für interaktive Kommunikation](/help/forms/interactive-communication/enable-template-lock.md).

## Häufig gestellte Fragen

**Was ist der Unterschied zwischen der Platzierung einer Komponente auf der Musterseite und dem Kopieren auf jeder Designseite?**
Eine Komponente auf der Musterseite wird an einer Stelle verwaltet - jede Bearbeitung, die Sie dort vornehmen, gilt automatisch für jede Seite, die diese Musterseite verwendet. Kopien auf einzelnen Design-Seiten müssen separat aktualisiert werden, was die Wartung fehleranfällig und zeitaufwendig macht.

**Kann ich eine Komponente von der primären Seite zurück auf eine Design-Seite verschieben?**
Es gibt keine direkte Aktion „Zurück“. Um eine Komponente an eine bestimmte Designseite zurückzugeben, fügen Sie eine neue Instanz dieses Komponententyps zur Designseite hinzu und löschen Sie sie von der Masterseite.

**Warum wird im Kontextmenü meiner Komponente nicht „Verschieben nach > Musterseite“ angezeigt?**
Der Komponententyp ist möglicherweise nicht qualifiziert (siehe Tabelle „Eignung“ oben) oder auf die Komponente wurde eine Inhalts- oder Layout-Sperre angewendet. Überprüfen Sie beide Bedingungen und entfernen Sie alle Sperren, bevor Sie es erneut versuchen. Verschieben Sie jede geeignete Komponente separat, z. B. das Banklogo und die Bankadresse einzeln.

## Siehe auch

- [Implementieren der dynamischen Seitennummerierung im Editor für interaktive Kommunikation](/help/forms/interactive-communication/implement-dynamic-page-numbering.md)
- [Vorlagensperre im Editor für interaktive Kommunikation](/help/forms/interactive-communication/enable-template-lock.md)
- [Erstellen einer Vorlage für interaktive Kommunikation](/help/forms/interactive-communication/create-interactive-communication-template.md)
- [Erstellen einer interaktiven Kommunikation](/help/forms/interactive-communication/create-interactive-communication.md)
