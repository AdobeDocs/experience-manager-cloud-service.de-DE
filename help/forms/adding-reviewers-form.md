---
title: Übermittlung eines adaptiven Formulars zur Überprüfung
description: Freigeben eines adaptiven Formulars zur Überprüfung für ein oder mehrere Prüferinnen oder Prüfer.
uuid: 58c8c8fb-9262-4c37-b9b2-e46fe21b77d9
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 71d1aa10-d191-49bc-a50f-1098324f1cfe
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 27c52969-1213-4fd3-8e16-988caafb4ad6
source-git-commit: a9adbb1886dcfedfc3fccb6f56939c46ba1365ee
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 100%

---

# Zuweisen von Übermittlungsprüfern mit einem Formular {#associating-submission-reviewers-with-a-form}

Wenn Sie ein Formular erstellen, können Sie Benutzer angeben, die die Übermittlungen des Formulars über das Formularportal überprüfen und Feedback geben. Ihr Unternehmen kann Feedback erfassen und in die übermittelten Formulare einarbeiten.

Mit [!DNL AEM Forms] können Sie eine Prüfergruppe mit einem Formular verknüpfen. Benutzer, die einer Reviewer-Gruppe eines Formulars hinzugefügt wurden, können Übermittlungen dieses Formulars sehen und Feedback hinterlassen.

Die Reviewer-Gruppen, die mit einem Formular verknüpft sind, können nur die Übermittlungen der angegebenen Formulare überprüfen.

## Voraussetzung {#prerequisite}

### Aktivieren der Eigenschaft „Übermittlungs-Prüfergruppen“ für adaptive Formulare mithilfe des Metadatenschema-Editors {#enabling-submission-reviewer-groups-property-for-adaptive-forms-using-metadata-schema-editor}

Um eine Reviewer-Gruppe mit einem Formular zu verknüpfen, bearbeiten Sie das Metadatenschema adaptiver Formulare. Standardmäßig können Sie eine Reviewer-Gruppe nicht zu einem übermittelten Formular hinzufügen.

So bearbeiten Sie das Metadatenschema:

1. Klicken Sie im Autorenmodus unter Experience Manager auf **Extras** > **Assets** > **Metadatenschemas**.
1. Navigieren Sie auf der Seite für die Schemaformulare zu **Formulare** > **Formularen, die in AEM verfasst wurden.**

   Die URL der Seite lautet:

   ```html
   https://<hostname>:<port>/mnt/overlay/dam/gui/content/metadataschemaeditor/
    schemalist.html/forms/aem-authored
   ```

1. Wählen Sie **adaptives Formular** und klicken Sie auf **Bearbeiten**.
1. Klicken Sie auf der Seite „Formular bearbeiten“ auf **Erweitert**.
1. Ziehen Sie die Komponente **Einzeiliger Text**, die unter „Formular erstellen“ verfügbar ist, auf die Registerkarte „Erweitert“ und legen Sie sie dort ab.
1. Wählen Sie die hinzugefügte Textkomponente aus, um die Einstellungen zu überprüfen.

   Geben Sie unter „Einstellungen“ im Feld „Zu Eigenschaft zuordnen“ `./jcr:content/metadata/form-submission-reviewer-group` ein.

   Das Feld für die Reviewer-Gruppe in den erweiterten Eigenschaften des adaptiven Formulars wird mit dem Namen aktiviert, den Sie unter „Feldbeschriftung“ angeben.

## Zuweisen von Übermittlungsprüfern mit einem Formular {#associating-submission-reviewers-with-a-form-1}

Um Reviewer mit einem adaptiven Formular zu verknüpfen, erstellen Sie eine Reviewer-Gruppe und fügen Sie ihr Benutzer hinzu. Fügen Sie die erstellte Reviewer-Gruppe unter dem Reviewer-Feld für Formularübermittlungen in den erweiterten Eigenschaften des Formulars hinzu.
Mit Benutzergruppen können Sie verschiedene Sätze von Übermittlungs-Reviewern mit verschiedenen adaptiven Formularen hinzufügen. Diese Funktion verhindert eine Übermittlungsüberprüfung durch nicht autorisierte Benutzer.

Bevor Sie folgende Schritte ausführen, lesen Sie die [Voraussetzung](adding-reviewers-form.md#prerequisite).

Um eine Gruppe zu erstellen und ihr Mitglieder hinzuzufügen, navigieren Sie zu **Tools** > **Vorgänge** > **Sicherheit** > **Gruppen**.
Weitere Informationen finden Sie unter [Benutzerverwaltung und Services](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html?lang=de).
Stellen Sie sicher, dass Sie die von Ihnen erstellte Gruppe als Mitglied der standardmäßigen Benutzergruppe hinzufügen: **forms-submission-reviewers**. Diese Benutzergruppe ist bereits in [!DNL AEM Forms] vorhanden. Mit ihr wird sichergestellt, dass Benutzer als Übermittlungs-Reviewer hinzugefügt werden.

Verknüpfen von Benutzergruppen mit einem adaptiven Formular:

1. Navigieren Sie im Bearbeitungsmodus zu **Formulare** > **Formulare und Dokumente**.
1. Verwenden Sie die Option **Auswählen**, um ein adaptives Formular auszuwählen, und klicken Sie auf **Eigenschaften anzeigen**.
1. Klicken Sie im Fenster „Eigenschaften“ des Formulars auf **Bearbeiten** und dann auf **ERWEITERT**.
1. Geben Sie die Gruppe im Feld „Übermittlungs-Reviewer-Gruppe“ ein und klicken Sie auf **Fertig**.

   Das Feld „Übermittlungs-Reviewer-Gruppe“ wird mit dem Namen angezeigt, den Sie im bearbeiteten Metadatenschema adaptiver Formulare angegeben haben.

>[!NOTE]
>
>Replizieren Sie Benutzer und Formulare, um die Verfügbarkeit der Benutzer und Formulare in der Remote-Implementierung von [!DNL AEM Forms] sicherzustellen.
>
>Stellen Sie sicher, dass alle Benutzer als Review-Mitglieder der Benutzergruppen in der Remote-Implementierung repliziert werden.

>[!MORELIKETHIS]
>
>* [Erstellen und Verwalten von Überprüfungen in Formularen](/help/forms/create-reviews-forms.md)
>* [Erstellen und Verwalten von Überprüfungen eines adaptiven Formulars](/help/forms/review-adaptiveforms-in-sites-page.md)
