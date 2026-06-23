---
title: Konfigurieren von gebundenen und ungebundenen Variablen für die Associate-Benutzeroberfläche
description: Erfahren Sie, wie Sie gebundene und ungebundene Variablen in Textkomponenten für die Benutzeroberfläche „Verknüpfen“ konfigurieren - den gesamten Textblock in der Dokumentvorschau bearbeiten oder einzelne Variablen im Dateneingabefeld bearbeiten.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="Gilt für AEM Forms)."
exl-id: configure-bound-unbound-variables-associate-ui
source-git-commit: 7619c18a771191a1491447484195bc480b1d2708
workflow-type: tm+mt
source-wordcount: '1405'
ht-degree: 1%

---


# Konfigurieren von gebundenen und ungebundenen Variablen für die Associate-Benutzeroberfläche

Gebundene und ungebundene Variablen in **Text**-Komponenten ermöglichen es Associates, Werte in der Benutzeroberfläche „Associate“ einzugeben oder zu bestätigen. Eine **gebundene Variable** ist mit einem Feld im Formulardatenmodell verknüpft. Eine **ungebundene Variable** wird im Dokument definiert und ist nicht an das Datenmodell gebunden.

Autoren aktivieren die Bearbeitung in Verbindung **„Bearbeitung zulassen nach**&quot; entweder für die Komponente **Text** oder für einzelne Variablen - nicht beide in derselben Komponente **Text**.

| Wer? | Vorteil |
|-----|---------|
| **Author (Interactive Communication Designer)** | Wählen Sie aus, ob Verknüpfungen inline in der Vorschau oder Feld für Feld im Dateneingabefeld bearbeiten sollen. |
| **Mitarbeiter (Agent/Service-Vertreter)** | Geben Sie Daten in den Workflow ein, der am besten zur Kommunikation passt - Inline-Bearbeitung oder strukturierter Bedienfeldeintrag. |

## Bevor Sie beginnen

Aktivieren Sie **Ansicht zuordnen** auf der interaktiven Kommunikation, bevor Sie Variablen für die Benutzeroberfläche „Zuordnen“ konfigurieren. Siehe [Zuordnen der Benutzeroberfläche im Editor für interaktive Kommunikation](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md).

Associates müssen Mitglieder der Gruppe **forms-Associates** sein.

## Gebundene Variablen

Eine gebundene Variable wird einem Feld im Formulardatenmodell zugeordnet (z. B. `deptName` unter `GMFletter`).

- Einfügen durch Ziehen eines Felds aus dem Bedienfeld **Datenmodell** in eine **Text**-Komponente.
- Das Bedienfeld **Feld** Eigenschaften zeigt **Name**, **Wert**, **Anzeigetyp** und **Bindung**.

## Ungebundene Variablen

Eine ungebundene Variable wird direkt in einer **Text**-Komponente erstellt und nicht mit dem Formulardatenmodell verknüpft (z. B. `unboundvar`).

- Das Bedienfeld **Feld** Eigenschaften zeigt **Name**, **Wert**, **Anzeigetyp** und **Bindung**.
- Unter **Eigenschaften zuordnen** können Sie **QuickInfo** und **Validierungen** konfigurieren.

## Gesamte Textkomponente in der Dokumentvorschau bearbeiten

Aktivieren Sie **Bearbeitung durch Verknüpfung zulassen** für die Komponente **Text** und lassen Sie sie für jede gebundene und ungebundene Variable im Text deaktiviert. In der Verknüpfungsansicht wählt der Verknüpfte den Textblock in der Dokumentvorschau aus. Die gesamte **Text**-Komponente wird mit einer violetten Umrandung und einer Formatierungssymbolleiste angezeigt.

### Konfigurieren

1. Öffnen Sie die interaktive Kommunikation im Editor für interaktive Kommunikation auf der Registerkarte **Design**.

1. Wählen Sie im **Komponentenhierarchie** die Komponente **Text** aus, die Ihre gebundenen und ungebundenen Variablen enthält - z. B. **Text7**.

1. Bestätigen Sie, dass der Text gebundene und ungebundene Variablen enthält. Beispiel:

   - **Datengebunden: deptName**
   - **UnboundVar: unboundVar**

   ![Textkomponente mit gebundenen und ungebundenen Variablen auswählen](/help/forms/interactive-communication/assets/bound-unbound-variable1.png)

1. Bestätigen Sie im **Text**-Eigenschaftenbereich, dass **Bearbeitung durch** zulassen für jede gebundene und **Variable im Text** Aus“ ist.

1. Wenn die **Text**-Komponente weiterhin ausgewählt ist, aktivieren Sie **Bearbeitung durch Verknüpfen zulassen** im Bedienfeld **Text**-Eigenschaften.

1. Klicken Sie **Speichern** und veröffentlichen Sie die interaktive Kommunikation.

### Überprüfen in der Associate-Benutzeroberfläche

1. Öffnen Sie die interaktive Kommunikation in **Verknüpfungsansicht**.

1. Wählen Sie den Textblock in der Dokumentvorschau aus. Bestätigen Sie, **die Komponente** Text“ mit einer violetten Umrandung und einer Formatierungssymbolleiste angezeigt wird.

1. Bearbeiten Sie Inhalte direkt in der Vorschau, z. B. aktualisieren Sie **Datengebunden: App-Abteilung** und geben Sie einen Wert nach **Unbound:** ein. Bestätigen der Aktualisierung von gebundenen und ungebundenen Variablen.

   ![Bearbeiten der gesamten Textkomponente inline in der Benutzeroberfläche „Verknüpfen“](/help/forms/interactive-communication/assets/bound-unbound-variable2.png)

1. Wählen Sie optional **Druckvorschau**, um zu bestätigen, dass die generierte Ausgabe mit der Vorschau übereinstimmt.

## Bearbeiten einzelner Variablen im Dateneingabefeld

Deaktivieren Sie **Bearbeitung durch Verknüpfung zulassen** in der Komponente **Text**. Aktivieren Sie sie für jede gebundene oder ungebundene Variable, die Verknüpfungen bearbeiten sollen. In der Verknüpfungsansicht wird jede aktivierte Variable als separates Feld im linken Dateneingabefeld angezeigt.

### Konfigurieren

1. Öffnen Sie die interaktive Kommunikation im Editor für interaktive Kommunikation auf der Registerkarte **Design**.

1. Wählen Sie **Bedienfeld** Komponentenhierarchie“ die gebundene Variable aus, z. B. **deptName[1]**.

1. Im Bedienfeld **Feld** Eigenschaften :

   - Bestätigen Sie **dass** Name“ auf `deptName` gesetzt ist.
   - Legen Sie **Anzeigetyp** nach Bedarf fest (z. B **„Kein Muster**).
   - Aktivieren Sie **Bearbeitung durch Mitarbeiter zulassen**.

   ![Konfigurieren der gebundenen Variablen „deptName“ für die Benutzeroberfläche „Associate“](/help/forms/interactive-communication/assets/bound-unbound-variable3.png)

1. Wählen Sie **Bedienfeld** Komponentenhierarchie“ die ungebundene Variable aus, z. B. **unboundVar**.

1. Im Bedienfeld **Feld** Eigenschaften :

   - Bestätigen Sie **dass** Name“ auf `unboundvar` gesetzt ist.
   - Aktivieren Sie **Bearbeitung durch Mitarbeiter zulassen**.
   - Konfigurieren Sie optional **QuickInfo** und **Validierungen** unter **Eigenschaften verknüpfen**.

   ![Konfigurieren der ungebundenen Variablen „unboundVar“ für die Associate-Benutzeroberfläche](/help/forms/interactive-communication/assets/bound-unbound-variable4.png)

1. Bestätigen Sie **dass „Bearbeitung durch** zulassen **in** übergeordneten **Text**-Komponente deaktiviert ist.

1. Klicken Sie **Speichern** und veröffentlichen Sie die interaktive Kommunikation.

### Überprüfen in der Associate-Benutzeroberfläche

1. Öffnen Sie die interaktive Kommunikation in **Verknüpfungsansicht**.

1. Bestätigen Sie jede Variable, **im linken Dateneingabefeld die Option** Bearbeitung von Assoziierten zulassen) angezeigt wird - beispielsweise **deptName** und **unboundVar**.

1. Geben Sie **APP-Abteilung** für **deptName** ein. Lassen Sie **unboundVar** leer und bestätigen Sie, dass die Dokumentvorschau den Variablennamen als Platzhalter anzeigt - z. B. **unboundVar: unboundVar**.

   ![Überprüfen von gebundenen und ungebundenen Variablen im Dateneingabefeld der zugehörigen Benutzeroberfläche](/help/forms/interactive-communication/assets/bound-unbound-variable5.png)

1. Geben Sie **Ungebundene Variable** für **unboundVar** ein und bestätigen Sie die Aktualisierungen der Dokumentvorschau in Echtzeit:

   - **Datengebunden: App-Abteilung** spiegelt den für die gebundene Variable eingegebenen Wert wider.
   - **Ungebunden: Ungebundene Variable** spiegelt den Wert wider, der für die ungebundene Variable eingegeben wurde.

   ![Überprüfen des Werts der ungebundenen Variablen in der zugehörigen Benutzeroberfläche](/help/forms/interactive-communication/assets/bound-unbound-variable6.png)

1. Wählen Sie optional **Druckvorschau**, um zu bestätigen, dass die generierte Ausgabe mit der Vorschau übereinstimmt.

## Doppelte Variablennamen (gebunden und ungebunden)

Wenn gebundene und ungebundene Variablen mit demselben Namen an mehreren Stellen auf der Design-Arbeitsfläche angezeigt werden, wird im linken Dateneingabefeld nur eine Instanz jedes Variablennamens angezeigt. Der Associate gibt jeden Wert einmal ein. Er wird automatisch an alle entsprechenden Vorkommen in der Dokumentvorschau weitergegeben.

### Konfigurieren

1. Öffnen Sie die interaktive Kommunikation im Editor für interaktive Kommunikation auf der Registerkarte **Design**.

1. Fügen Sie ein **Teilformular** oder zusätzliche **Text**-Komponenten auf der Arbeitsfläche des Designs hinzu und fügen Sie doppelte gebundene und ungebundene Variablen an jeder Position ein. Fügen Sie beispielsweise zwei Blöcke hinzu, die jeweils Folgendes enthalten:

   - **Datengebunden: deptName**
   - **UnboundVar: unboundVar**

   ![Konfigurieren doppelter gebundener und ungebundener Variablen in Teilformularen](/help/forms/interactive-communication/assets/bound-unbound-variable7.png)

1. Wählen Sie im Bedienfeld **Komponentenhierarchie** jede gebundene und jede ungebundene Variable aus und aktivieren Sie **Bearbeitung durch Verknüpfen zulassen** im Bedienfeld **Feld** Eigenschaften.

1. Bestätigen Sie **dass „Bearbeitung durch** zulassen **in** übergeordneten **Text**-Komponenten deaktiviert ist.

1. Klicken Sie **Speichern** und veröffentlichen Sie die interaktive Kommunikation.

### Überprüfen in der Associate-Benutzeroberfläche

1. Öffnen Sie die interaktive Kommunikation in **Verknüpfungsansicht**.

1. Bestätigen Sie, dass nur **Feld** deptName) und ein Feld **unboundVar** im linken Dateneingabefeld angezeigt werden, auch wenn jede Variable an mehreren Stellen auf der Design-Arbeitsfläche auftritt.

1. Geben Sie **APP-Abteilung** für **deptName** ein. Lassen Sie **unboundVar** leer und bestätigen Sie beide Vorkommnisse in der Dokumentvorschau-Aktualisierung, z. B. zeigt jeder Block **Datengebunden: App-Abteilung** und **Ungebunden: unboundVar**.

   ![Überprüfen der Übertragung doppelter Variablen in der Associate-Benutzeroberfläche](/help/forms/interactive-communication/assets/bound-unbound-variable8.png)

1. Wählen Sie optional **Druckvorschau**, um zu bestätigen, dass die generierte Ausgabe mit der Vorschau übereinstimmt.

## Überlegungen

**Doppelte Variablennamen (gebunden und ungebunden)**

Wenn gebundene und ungebundene Variablen denselben Variablennamen haben:

- Im linken Dateneingabefeld wird nur eine Instanz angezeigt.
- Nur Variablen, für die die Bearbeitung von Zuordnungen aktiviert ist, werden in der Dokumentvorschau aktualisiert.
- Der Associate gibt den Wert einmal im Dateneingabefeld ein. Er wird automatisch an alle entsprechenden Vorkommen in der Dokumentvorschau weitergegeben.

**Ungebundene Variablen mit demselben Namen, aber unterschiedlichen Standardwerten**

Wenn mehrere ungebundene Variablen einen Variablennamen gemeinsam haben, aber unterschiedliche Standardwerte verwenden, zeigt die Benutzeroberfläche „Verknüpfen“ den Standardwert der ersten Variablen an, für die die Bearbeitung von Verknüpfungen im linken Dateneingabefeld aktiviert ist.

**Gebundene Variablen mit demselben Namen, aber unterschiedlichen Datenreferenzpfaden**

Wenn mehrere gebundene Variablen einen Variablennamen gemeinsam haben, aber unterschiedliche Datenverweispfade verwenden, wird im linken Dateneingabefeld der Wert der ersten Variablen angezeigt, für die die Bearbeitung von verknüpften Daten aktiviert ist. Jeder vom Associate im Dateneingabefeld eingegebene oder aktualisierte Wert wird unabhängig von den Datenreferenzpfaden auf alle Variablen mit diesem Namen übertragen.

**Gegenseitige Exklusivität**

**Bearbeitung durch Verknüpfung zulassen** schließen sich die **Text**-Komponente und darin enthaltene gebundene oder ungebundene Variablen gegenseitig aus. Aktivieren Sie einen Ansatz pro **-**-Komponente.

**Ungebundene Variablen ohne Wert**

Wenn für eine ungebundene Variable die Bearbeitung aktiviert ist, aber kein Wert eingegeben wird, kann die Dokumentvorschau den Variablennamen anzeigen (z. B. `unboundvar`), bis der Associate im Dateneingabefeld einen Wert bereitstellt.

## Häufig gestellte Fragen

**Was ist der Unterschied zwischen der Bearbeitung der gesamten Textkomponente und der Bearbeitung einzelner Variablen?**
Wenn Sie die Bearbeitung verknüpfter Dokumente für die Komponente **Text** aktivieren, bearbeitet der verknüpfte Benutzer den gesamten Textblock in der Dokumentvorschau inline (violette Begrenzung). Wenn Sie die Bearbeitung verknüpfter Daten für einzelne Variablen aktivieren, wird jede aktivierte Variable als separates Feld im linken Dateneingabefeld angezeigt.

**Warum kann ich die Bearbeitung von Verknüpfungen nicht sowohl für die Textkomponente als auch für einzelne Variablen aktivieren?**
Die Bearbeitung von Verknüpfungen für **Text**-Komponente und darin enthaltene gebundene oder ungebundene Variablen schließen sich gegenseitig aus. Bearbeitung für den gesamten Textblock oder für einzelne Variablen aktivieren - nicht beides.

**Warum zeigt meine ungebundene Variable in der Vorschau den Variablennamen anstelle eines Werts an?**
Der Associate hat wahrscheinlich noch keinen Wert eingegeben. Wenn die Bearbeitung verknüpfter Daten für einzelne Variablen aktiviert ist und kein **Wert** konfiguriert ist, kann die Vorschau den Variablennamen anzeigen, bis die Daten im Dateneingabefeld eingegeben werden.

**Was ist der Unterschied zwischen einer gebundenen und einer ungebundenen Variablen?**
Eine gebundene Variable ist mit einem Formulardatenmodellfeld über die Konfiguration **Bindung** verknüpft. Eine ungebundene Variable ist im Dokument definiert und nicht an das Datenmodell gebunden.

**Was passiert, wenn zwei Variablen denselben Namen haben?**
Im linken Dateneingabefeld wird nur eine Instanz angezeigt. Der Associate gibt den Wert einmal im Dateneingabefeld ein und propagiert ihn automatisch an alle entsprechenden Vorkommen in der Dokumentvorschau.

## Siehe auch

- [Zuordnen der Benutzeroberfläche im Editor für interaktive Kommunikation](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md)
- [Konfigurieren von Dropdown-Optionen für die Benutzeroberfläche „Verknüpfen“](/help/forms/interactive-communication/associateui/configure-dropdown-options-binding.md)
- [Aktivieren und Konfigurieren der Associate-Benutzeroberfläche für interaktive Kommunikation](/help/forms/interactive-communication/enable-configure-associate-ui.md)
- [Komponente „Ungebundene Variable“ im Editor für interaktive Kommunikation](/help/forms/interactive-communication/unbound-variable.md)
