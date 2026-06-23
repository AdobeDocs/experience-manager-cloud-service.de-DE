---
title: Aktivieren und Konfigurieren der Associate-Benutzeroberfläche für interaktive Kommunikation
description: Erfahren Sie, wie Sie in den Einstellungen für interaktive Kommunikation die Option „Associate View“ aktivieren und Workflows für Aktualisierungen konfigurieren, damit Associates die Associate-Benutzeroberfläche verwenden können.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: 5f8371f9-b4a6-4cae-a9d3-cfd744b66702
source-git-commit: 53ff71c82d35b9ec9b20b521ef469d3f0abd79df
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---

# Aktivieren und Konfigurieren der Associate-Benutzeroberfläche für interaktive Kommunikation


In diesem Artikel wird beschrieben, wie Sie die Benutzeroberfläche „Verknüpfen“ für eine interaktive Kommunikation (IC) aktivieren und optional einen AEM-Workflow für Übermittlungen konfigurieren. Autoren führen diese Schritte in **Einstellungen für interaktive Kommunikation** aus.

Einen Überblick über die Associate-Benutzeroberfläche und Benutzerrollen finden Sie unter [Associate-Benutzeroberfläche im Editor für interaktive Kommunikation](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md).

## Voraussetzungen

Bevor Sie die Associate-Benutzeroberfläche aktivieren und konfigurieren, sollten Sie Folgendes sicherstellen:

- **Autorenzugriff** auf den Editor für interaktive Kommunikation.
- Eine **interaktive Kommunikation**, die mit dem erforderlichen Layout und den erforderlichen Datenbindungen erstellt wurde.
- **Benutzer verknüpfen** wurde zur Gruppe **forms-associations** hinzugefügt (erforderlich, damit Associates auf die Associate-Benutzeroberfläche zugreifen können).
- **Autoren** wurde zur Gruppe **forms-associations** hinzugefügt (erforderlich, damit Autoren auf die Associate-Benutzeroberfläche zugreifen können).

Wenn Sie bereit sind, die Benutzeroberfläche „Verknüpfen“ in Ihr Programm zu integrieren und sie in der Veröffentlichungsinstanz aufzurufen, benötigen Sie auch einen Browser mit aktivierter Popup-Unterstützung und der IC veröffentlicht. Siehe [Integrieren der Benutzeroberfläche von Associate in Ihr Programm](/help/forms/interactive-communication/invoke-associate-ui.md) für vollständige Integrationsvoraussetzungen.

## Associate-Ansicht aktivieren (Associate-Benutzeroberfläche)

Aktivieren Sie die Benutzeroberfläche „Verknüpfen“ auf Dokumentebene, damit die interaktive Kommunikation von Verknüpfungen verwendet werden kann.

1. Öffnen Sie Ihre interaktive Kommunikation im Editor.
1. Öffnen Sie in der oberen Aktionsleiste oder in den Dokumentoptionen **Einstellungen für interaktive Kommunikation** (oder **Einstellungen**).

   ![Einstellungen für interaktive Kommunikation - Eigenschaften mit verknüpfen, um die Bearbeitung verknüpfter Ansichten zu aktivieren](/help/forms/assets/associate-ui-settings.png)

1. Stellen Sie sicher, dass im linken Bedienfeld **Eigenschaften verknüpfen** ausgewählt ist.
1. Aktivieren Sie rechts die Option **Bearbeitung verknüpfter Ansichten aktivieren**.
1. Klicken Sie **Änderungen übernehmen** und speichern Sie dann das Dokument.

   ![Einstellungen für interaktive Kommunikation - Eigenschaften mit verknüpfen, um die Bearbeitung verknüpfter Ansichten zu aktivieren](/help/forms/assets/associate-ui-enable-view.png)

Eine Meldung kann Sie daran erinnern, Änderungen anzuwenden und das Dokument zu speichern, um die zugehörige Ansicht zu aktivieren. Nach dem Speichern ist der IC für den Associate-Einsatz verfügbar.

### Bearbeiten der zugehörigen Benutzeroberfläche pro Komponente zulassen

Sobald die Verknüpfungsansicht für die IC aktiviert ist, müssen Sie &quot;**nach Verknüpfen zulassen** für jede Komponente aktivieren, die Verknüpfungen bearbeiten können sollen. Komponenten, für die diese Einstellung nicht aktiviert ist, bleiben in der zugehörigen Benutzeroberfläche schreibgeschützt.

1. Wählen Sie im IC-Editor die Komponente (z. B. ein Textfeld) auf der Arbeitsfläche oder in der Komponentenhierarchie aus.
1. Erweitern Sie im rechten Bedienfeld **Eigenschaften** die Option **Eigenschaften verknüpfen**.
1. Aktivieren **„Bearbeitung durch** zulassen **für** Komponente.
1. Wiederholen Sie den Vorgang für jede Komponente, die zugeordnet werden muss, und speichern Sie dann das Dokument.

![Bearbeitung durch Zugehörige in den Komponenteneigenschaften zulassen](/help/forms/assets/associate-ui-allow-editing-by-associate.png)

>[!NOTE]
>
> **Eigenschaften zuordnen** enthält auch Optionen wie **Typografie** (Schriftart, Größe und Stil für das Feld in der Benutzeroberfläche „Zuordnen„), **QuickInfo** und **Muster** (Validierungen). Verwenden Sie diese Elemente, um zu steuern, wie die Komponente aussieht und sich verhält, wenn sie von Verknüpfungen bearbeitet wird. Legen Sie beispielsweise Validierungsmuster fest, damit Verknüpfungen Daten im erforderlichen Format eingeben.

## Workflow für die Associate-Benutzeroberfläche konfigurieren

Um einen AEM-Workflow auszuführen, wenn Benutzer Daten über die Benutzeroberfläche von „Associate“ senden oder aktualisieren, konfigurieren Sie Folgendes:

1. Wählen **in den Einstellungen für** interaktive Kommunikation **Workflow** im linken Bereich (unter „Eigenschaften verknüpfen„) aus.
1. Aktivieren **Workflow für Aktualisierung konfigurieren** **Ein**.
1. Wählen **unter „Workflow-** auswählen“ das auszuführende AEM-Workflow-Modell aus (z. B. `conversionWorkflow` oder einen Pfad wie `/var/workflow/models/submit-workflow-1`).
1. Wählen Sie optional **Erfolgsmeldung zum Workflow** (wird den Benutzenden nach Abschluss des Workflows angezeigt).
1. Optional können Sie **Umleitungs-URL** festlegen, um den Benutzer nach der Übermittlung an eine bestimmte Seite zu senden.
1. Klicken Sie **Änderungen übernehmen** und speichern Sie das Dokument.

   ![Einstellungen für interaktive Kommunikation - Workflow-Konfiguration für die Benutzeroberfläche von Associate](/help/forms/assets/associate-ui-configure-workflow.png)

Wenn Sie einen Workflow aktivieren, wird er immer dann ausgeführt, wenn Benutzer ihn über die Benutzeroberfläche „Verknüpfen“ übermitteln. Informationen zur Funktionsweise von Übermittlung und Workflow - wo sie ausgeführt werden, wer welche Instanz verwendet und wichtige Überlegungen - finden Sie unter [Übermittlungs-Workflow für die Benutzeroberfläche von Associate](/help/forms/interactive-communication/submission-workflow-associate-ui-ic-pdf.md#submission-and-workflow-behavior). Dieser Artikel enthält auch ein Beispiel für einen Workflow, der PDF aus IC-Übermittlungen generiert.

## Fertigstellen der Einrichtung der zugehörigen Benutzeroberfläche

Nach Aktivierung der Associate-Ansicht und optionaler Konfiguration des Workflows:

1. **Bearbeitbare Felder aktivieren** Aktivieren Sie in den erforderlichen Abschnitten der IC die Felder, die Verknüpfungen bearbeiten dürfen. Legen Sie bei Bedarf Validierungen und obligatorisches/schreibgeschütztes Verhalten fest.
1. **Veröffentlichen Sie die IC**, damit sie für Associates in der Veröffentlichungsinstanz verfügbar ist.
1. Freigeben des veröffentlichten IC-Links für Partner. Sie authentifizieren sich (z. B. über [Microsoft Entra ID](https://www.microsoft.com/en-us/security/business/identity-access/microsoft-entra-id)) und öffnen die Benutzeroberfläche „Associate“, geben Kundendaten ein oder bestätigen sie und generieren die endgültige Kommunikation. Wenn Sie einen Workflow konfiguriert haben, wird er bei der Übermittlung ausgeführt. Informationen zur Funktionsweise von Übermittlung und Workflow finden Sie unter [Übermittlungs-Workflow für die Benutzeroberfläche von Associate](/help/forms/interactive-communication/submission-workflow-associate-ui-ic-pdf.md#submission-and-workflow-behavior).

## Siehe auch

- [Zuordnen der Benutzeroberfläche im Editor für interaktive Kommunikation](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md)
- [Integrieren der Associate-Benutzeroberfläche in Ihr Programm](/help/forms/interactive-communication/invoke-associate-ui.md)
- [Übermittlungs-Workflow für die Associate-Benutzeroberfläche - IC Generate PDF Output](/help/forms/interactive-communication/submission-workflow-associate-ui-ic-pdf.md) - Funktionsweise von Übermittlung und Workflow sowie ein Beispiel-Workflow, der PDF aus IC-Übermittlungen generiert.

