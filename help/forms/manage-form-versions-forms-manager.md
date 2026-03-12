---
title: Verwalten von Formularversionen in Forms Manager
description: Erfahren Sie, wie Sie Versionen von adaptivem Forms, Formularfragmenten, Designs und anderen Assets in der Forms Manager-Benutzeroberfläche erstellen und verwalten.
feature: Adaptive Forms, Core Components, Foundation Components
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="Gilt für AEM Forms)."
exl-id: cd2c6e15-99a6-4b4e-bfd1-8291a2001ebe
source-git-commit: 89b0f2a8ca9d2f60365a5c3962b0b4e826f79b3e
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 7%

---

# Verwalten von Formularversionen in Assets in der Benutzeroberfläche von Forms Manager

<span class="preview"> Diese Funktion ist über das Early Access-Programm verfügbar. Um den Zugriff anzufordern, senden Sie eine E-Mail von Ihrer offiziellen Adresse an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com). </span>

Forms Manager unterstützt jetzt die Versionierung für Formular-Assets. Sie können Versionen erstellen, den Versionsverlauf anzeigen und frühere Versionen Ihrer Assets über die Forms Manager-Benutzeroberfläche wiederherstellen.

## Unterstützte Asset-Typen {#supported-asset-types}

Sie können Versionen für die folgenden Asset-Typen erstellen und verwalten:

| Asset-Typ | Beschreibung |
|---|---|
| Adaptive Forms (Kernkomponenten) | Adaptive Forms mit Kernkomponenten |
| Adaptive Forms (Foundation-Komponenten) | Adaptive Forms, die mit Foundation-Komponenten erstellt wurden |
| Formularfragmente | Wiederverwendbare Formularabschnitte, die für mehrere Formulare freigegeben sind |
| Designs | Auf adaptive Forms angewendete visuelle Stildefinitionen |
| XDP-Vorlagen | XFA-basierte Formularvorlagen |
| Binäre Assets | Andere Dateien, die unter dem Forms DAM-Repository gespeichert sind |

## Erstellen einer Version {#create-version-forms-manager}

So erstellen Sie eine Version eines Formular-Assets:

1. Gehen Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie das Formular oder Asset aus.
1. Wählen Sie im linken Bereich die Option **[!UICONTROL Zeitleiste]**.
1. Klicken Sie **[!UICONTROL der Zeitleistensymbolleiste]**Als Version speichern“.
   ![Als Version speichern](/help/forms/assets/create-version.png)
1. Geben Sie einen **[!UICONTROL Titel]** und einen optionalen **[!UICONTROL Kommentar]** ein, um die Änderungen zu beschreiben.
1. Klicken Sie auf **[!UICONTROL Erstellen]**.
   ![Als Version2 speichern](/help/forms/assets/create-version1.png)

Die Version wird im Zeitleistenfenster mit Titel, Kommentar und Zeitstempel angezeigt.

## Versionieren eines Assets beim Hochladen {#version-on-upload}

Wenn Sie ein Asset mit demselben Namen wie ein vorhandenes Asset hochladen, zeigt Forms Manager das Dialogfeld **Datei-Upload** an, in dem die zu aktualisierenden Assets aufgeführt sind. Das Dialogfeld zeigt den Asset-Namen, den Abschnitt und den Pfad an.

Wenn bereits ein Asset mit demselben Namen vorhanden ist, ersetzt der Upload das vorhandene Asset und erstellt automatisch eine neue Version. Sie können die erstellte Version in der Zeitleiste anzeigen.

![Dialogfeld „Datei-Upload“ mit versioniertem Upload](/help/forms/assets/version-upload.png)

## Versionsverlauf anzeigen {#view-version-history}

So zeigen Sie den Versionsverlauf eines Assets an:

1. Wählen Sie das Asset in Forms Manager aus.
1. Wählen Sie im linken Bereich die Option **[!UICONTROL Zeitleiste]**.
   ![Versionsverlauf](/help/forms/assets/version-history.png)

In der Zeitleiste werden alle Versionseinträge zusammen mit Aktivitätsereignissen angezeigt. Jeder Eintrag zeigt die Bezeichnung, den Kommentar, den Autor und den Zeitstempel an.

## Wiederherstellen einer früheren Version {#restore-version}

So stellen Sie ein Asset auf eine frühere Version zurück:

1. Wählen Sie das Asset in Forms Manager aus.
1. Wählen Sie im linken Bereich die Option **[!UICONTROL Zeitleiste]**.
1. Wählen Sie die Version aus, die Sie wiederherstellen möchten.
1. Klicken Sie auf **[!UICONTROL Auf diese Version zurück]**.
   ![Version zurücksetzen](/help/forms/assets/revert-version.png)

>[!NOTE]
>
>Bilder können nicht auf eine frühere Version zurückgesetzt werden. Alle anderen Asset-Typen, einschließlich adaptiver Forms, Formularfragmenten, Designs und XDP-Vorlagen, unterstützen die Versionswiederherstellung.

## Siehe auch {#see-also}

* [Versionieren, Überprüfen und Kommentieren von adaptiven Formularen](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md)
* [Importieren und Exportieren von Formularen und zugehörigen Assets](/help/forms/import-export-forms-templates.md)
* [Veröffentlichen und Rückgängigmachen der Veröffentlichung von Formularen](/help/forms/publishing-unpublishing-forms.md)
