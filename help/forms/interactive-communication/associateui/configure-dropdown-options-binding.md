---
title: Konfigurieren von Dropdown-Optionen für die Benutzeroberfläche „Verknüpfen“
description: Erfahren Sie, wie Sie Bindungsoptionen oder manuelle statische Optionen für Dropdown-Felder im Editor für interaktive Kommunikation konfigurieren, damit Auswahlmöglichkeiten in der Benutzeroberfläche „Verknüpfen“ korrekt dargestellt werden.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="Gilt für AEM Forms)."
exl-id: configure-dropdown-options-associate-ui
source-git-commit: 7619c18a771191a1491447484195bc480b1d2708
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 2%

---


# Konfigurieren von Dropdown-Optionen für die Benutzeroberfläche „Verknüpfen“

Dropdown-Felder im Editor für interaktive Kommunikation verwenden ein fokussiertes **Options-Binding**-Modell für dynamische, datengesteuerte Entscheidungen in der Benutzeroberfläche „Verknüpfen“. **Datenbindung** wird für Dropdown-Felder nicht mehr unterstützt - Autoren konfigurieren entweder **Aus Daten binden** (gebundene Datenquelle) oder manuelle statische Optionen im **Eigenschaften**-Bedienfeld.

| Wer? | Vorteil |
|-----|---------|
| **Author (Interactive Communication Designer)** | Stellen Sie exakte, datengesteuerte Dropdown-Optionen für Verknüpfungen ohne nicht unterstützte Datenbindungskonfigurationen bereit. |
| **Mitarbeiter (Agent/Service-Vertreter)** | Sehen Sie sich die richtige Optionsliste und den vorab ausgewählten Wert an, wenn Sie die Kundenkommunikation in der Benutzeroberfläche von Associate abschließen. |

## Bevor Sie beginnen

Aktivieren Sie **Verknüpfungsansicht** auf der interaktiven Kommunikation, bevor Sie das Dropdown-Verhalten für die Benutzeroberfläche „Verknüpfen“ konfigurieren. Siehe [Zuordnen der Benutzeroberfläche im Editor für interaktive Kommunikation](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md).

Associates müssen Mitglieder der Gruppe **forms-Associates** sein.

## Bind aus Daten aktiviert (dynamische Optionen)

Wenn **Optionen Source** auf &quot;**aus Daten binden** eingestellt ist:

- Dropdown-Optionen werden vollständig von der gebundenen Datenquelle gesteuert, die in &quot;**&quot; konfiguriert**.
- Optionen werden gerendert und stehen in der Benutzeroberfläche „Verknüpfen“ zur Auswahl.
- **Standardwert** ist nicht verfügbar. Der erste Wert aus den gebundenen Optionen wird automatisch vorausgewählt, wenn das Formular dem Verantwortlichen angezeigt wird.

## Manuelle Optionen (statische Optionen)

Wenn **Optionen Source** nicht auf &quot;**aus Daten binden** eingestellt ist:

- Autoren können Optionen manuell über das Bedienfeld **Eigenschaften** hinzufügen.
- **Standardwert** bleibt verfügbar. Der Formular-Designer kann explizit auswählen, welche Option als vorab ausgewählter Wert in der Benutzeroberfläche „Verknüpfen“ angezeigt wird.

## Dropdown-Optionen konfigurieren

1. Öffnen Sie die interaktive Kommunikation im Editor für interaktive Kommunikation.

1. Wählen Sie auf **Registerkarte** die Komponente **Dropdown** auf der Arbeitsfläche Entwurf aus.

1. Öffnen Sie das Bedienfeld **Eigenschaften**.

1. Konfigurieren Sie das Dropdown-Menü für die Benutzeroberfläche „Verknüpfen“:

   - Legen Sie **Beschriftung** auf die Beschriftung fest, die die Verknüpfungen im linken Dateneingabefeld sehen. Geben Sie beispielsweise &quot;**Monat“**.
   - Wählen Sie **Optionen Source** die Option **Aus Daten binden** aus, um Optionen aus Ihrem Datenmodell auszufüllen, oder fügen Sie manuelle Optionen für eine statische Liste hinzu.
   - Wenn Sie **Aus Daten binden** ausgewählt haben, legen Sie **Options Ref** auf den Datenpfad fest, der die Optionsliste bereitstellt. Binden Sie beispielsweise an `$.GMFletter.installmentDetails.installmentMonth`.

   Konfigurieren Sie **Datenbindung** nicht für Dropdown-Felder - verwenden Sie nur **Bindung aus Daten** oder manuelle Optionen.

   ![Konfigurieren der Bindung für Dropdown-Optionen](/help/forms/interactive-communication/assets/associate-ui-configure-drop-down1.png)

1. Aktivieren Sie **Bearbeitung durch Associate zulassen**, damit Associates einen Wert in der Benutzeroberfläche „Associate“ auswählen können.

1. Konfigurieren Sie optional **QuickInfo** und **Validierungen** unter **Eigenschaften verknüpfen**.

1. Wenn Sie manuelle Optionen verwenden, setzen **Standardwert** nach Bedarf.

1. Klicken Sie **Speichern** und veröffentlichen Sie die interaktive Kommunikation.

## Überprüfen in der Associate-Benutzeroberfläche

1. Öffnen Sie die interaktive Kommunikation in der **Verknüpfungsansicht**.

1. Bestätigen Sie, dass das Dropdown-Menü im linken Dateneingabefeld mit der konfigurierten Beschriftung angezeigt wird. Beispiel: **Monat der**) zeigt die gebundenen Optionen wie **Juni 2026**, **Juli 2026** und **August 2026**.

1. Stellen Sie sicher, dass die erste gebundene Option beim Laden der zugehörigen Benutzeroberfläche vorausgewählt ist.

1. Wählen Sie eine andere Option aus und bestätigen Sie, dass der Wert in der rechten Vorschau aktualisiert wird. Wenn Sie beispielsweise **Juni 2026** auswählen, wird der Dokumenttext auf &quot;**&quot; im Juni 2026**.

   ![Überprüfen Sie die Dropdown-Optionen in der Benutzeroberfläche „Verknüpfen“](/help/forms/interactive-communication/assets/associate-ui-configure-drop-down2.png)

## Überlegungen

- **Datenbindung wird nicht unterstützt** für Dropdown-Felder. Verwenden Sie **Aus Daten binden** für dynamische Listen oder manuelle Optionen für statische Listen.
- Wenn **Aus Daten binden** aktiviert ist, können Verknüpfungen keinen benutzerdefinierten Standardwert festlegen - die erste gebundene Option ist immer vorausgewählt.
- Testen Sie bei manuellen Optionen den **Standardwert) in der Vorschau der**-Benutzeroberfläche, um zu bestätigen, dass die erwartete Option vor der Veröffentlichung angezeigt wird.
- **Bearbeitung durch Associate zulassen** muss aktiviert sein, damit das Dropdown-Menü als bearbeitbares Feld auf der linken Seite der Associate-Benutzeroberfläche angezeigt wird.

## Häufig gestellte Fragen

**Warum ist der Standardwert für mein Dropdown-Menü nicht verfügbar?**
**Standardwert** ist deaktiviert, wenn **Optionen Source** auf &quot;**aus Daten binden“**. Der erste Wert aus der gebundenen Datenquelle wird automatisch in der Benutzeroberfläche „Verknüpfen“ vorausgewählt.

**Kann ich die Optionen Datenbindung und Bindung zusammen in einem Dropdown-Menü verwenden?**
Anzahl Dropdown-Felder unterstützen nur **Aus Daten binden** oder manuelle Optionen. **Datenbindung** wird für Dropdown-Felder nicht unterstützt.

**Was ist Options Ref?**
**Options Ref** ist der Datenverweispfad, der die Liste der Auswahlmöglichkeiten bereitstellt, wenn **Options Source** auf „Bind from **&quot;**. Wählen Sie den Pfad aus, der auf die Sammlung von Optionswerten in Ihrem Formulardatenmodell verweist.

**Wie kann ich Dropdown-Optionen überprüfen, bevor Associates die interaktive Kommunikation verwenden?**
Veröffentlichen Sie die interaktive Kommunikation und öffnen Sie die Vorschau der zugehörigen Benutzeroberfläche. Bestätigen Sie, dass gebundene oder manuelle Optionen im linken Dateneingabefeld angezeigt werden und dass der vorausgewählte Wert mit Ihrer Konfiguration übereinstimmt.

## Siehe auch

- [Zuordnen der Benutzeroberfläche im Editor für interaktive Kommunikation](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md)
- [Konfigurieren von gebundenen und ungebundenen Variablen für die Associate-Benutzeroberfläche](/help/forms/interactive-communication/associateui/configure-bound-unbound-variables-associate-ui.md)
- [Erstellen einer interaktiven Kommunikation](/help/forms/interactive-communication/create-interactive-communication.md)
