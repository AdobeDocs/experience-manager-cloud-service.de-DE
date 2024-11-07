---
title: Hinzufügen wiederholbarer Abschnitte zu einem Formular
description: Hinzufügen wiederholbarer Abschnitte zu einem EDS-Formular
feature: Edge Delivery Services
exl-id: 062d5a88-48ca-421f-bf0d-1483e3cfee28
role: Admin, Architect, Developer
source-git-commit: 6612abbd95599791ff9571b59154aa8ab34fb5f8
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 100%

---

# Hinzufügen wiederholbarer Abschnitte zu einem Formular

Der Baustein „Adaptives Formular“ bietet die Möglichkeit, einen Abschnitt oder eine Komponente eines Formulars hinzuzufügen oder wiederholbar zu machen.  Dadurch können Benutzende Informationen für denselben Datentyp mehrmals eingeben, was die Erfassung von Informationen wie Arbeitserfahrung oder Bildungshintergrund erleichtert.

Dies könnte beispielsweise ein Formular sein, mit dem Informationen über die Arbeitserfahrung einer Person erfasst werden. Sie könnten einen wiederholbaren Abschnitt zum Erfassen der Details jeder vorherigen Beschäftigung haben. Der wiederholbare Abschnitt enthält normalerweise Felder wie Unternehmensname, Stellenbezeichnung, Beschäftigungsdauer und Arbeitsverantwortlichkeiten. Die Benutzerin bzw. der Benutzer kann mehrere Instanzen des wiederholbaren Abschnitts hinzufügen, um Informationen zu den einzelnen Beschäftigungen einzugeben, die sie bzw. er in der Vergangenheit hatte.

Am Ende dieses Artikels werden Sie Folgendes gelernt haben:

* [Erstellen eines wiederholbaren Abschnitts in einem Formular](#add-repeatable-sections-to-a-form)
* [Festlegen der Mindest- oder Höchstanzahl von Wiederholungen in einem Formular](#set-minimum-or-maximum-number-of-repetitions-for-a-repeatable-section)

## Erstellen eines wiederholbaren Abschnitts

Das Erstellen eines wiederholbaren Abschnitts in einem Formular bietet Benutzenden die Möglichkeit, mehrere Instanzen desselben Datensatzes einzugeben, sodass sich wiederholende Informationen effizient erfassen lassen. So erstellen Sie einen wiederholbaren Abschnitt in einem Formular:

1. Wechseln Sie in Microsoft SharePoint oder Google Workspace zum Projektordner „Edge Delivery“ und öffnen Sie die Tabelle.

1. Fügen Sie ein Formularfeld hinzu, dessen `type`-Eigenschaft auf `fieldset` festgelegt ist.
1. Geben Sie den `Name` des Felds an. Die Name-Eigenschaft wird verwendet, um einen wiederholbaren Abschnitt zu erstellen.
1. Aktivieren Sie die Wiederholbarkeit, indem Sie `repeatable` auf `true` festlegen.
1. Geben Sie eine beschreibendes `label` für das Feld an. Es dient als Überschrift für den wiederholbaren Abschnitt.

   In der Abbildung unten finden Sie eine Abbildung eines Abschnitts über den Beschäftigungsverlauf in einem Bewerbungsformular.

   ![](/help/edge/assets/repeatable-section-example-job-application-form.png)

1. Legen Sie bei jedem Feld, das Sie in den Abschnitt aufnehmen möchten, für dessen `Fieldset`-Eigenschaft denselben Namen fest, den Sie in Schritt 3 ausgewählt haben.

   Geben Sie beispielsweise `experience` in der Eigenschaft „Fieldset“ aller relevanten Felder ein, die in den Abschnitt `employment history` eingefügt werden sollen.

   ![Beispiel für das Feld eines wiederholbaren Abschnitts und dessen Eigenschaften](/help/edge/assets/repeatable-section--mention-fieldset-name-example-job-application-form.png)

1. Verwenden Sie [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content), um das Blatt in der Vorschau anzuzeigen und zu veröffentlichen. Der wiederholbare Abschnitt wird dem Formular hinzugefügt.

   Unter dem wiederholbaren Abschnitt finden Benutzende eine intuitive Schaltfläche **Hinzufügen**, wodurch das Hinzufügen mehrerer Abschnitte erleichtert wird.

   ![wiederholbarer Abschnitt, Schaltfläche „Hinzufügen“, um mehrere Abschnitte hinzuzufügen ](/help/edge/assets/repeatable-section-example.png)


## Festlegen der Mindest- oder Höchstanzahl von Wiederholungen

Bei der Gestaltung von Formularen ist es von Vorteil, eine Mindest- oder Höchstanzahl von Wiederholungen für wiederholbare Abschnitte festzulegen. Auf diese Weise stellen Sie Kontrolle und Konsistenz sicher und lenken Benutzende gleichzeitig effektiv. So legen Sie eine Mindest- oder Höchstanzahl von Wiederholungen fest:

1. Wechseln Sie in Microsoft SharePoint oder Google Workspace zum Projektordner „Edge Delivery“ und öffnen Sie die Tabelle.

1. Bei einem Feld der Eigenschaft `type` `fieldset` und `repeatable`, für das `true` festgelegt ist:

   * Legen Sie die Eigenschaft `min` fest, um anzugeben, wie oft der Abschnitt mindestens wiederholt werden soll.

   * Legen Sie die Eigenschaft `max` fest, um anzugeben, wie oft der Abschnitt maximal wiederholt werden kann.

   ![Festlegen der Eigenschaft „Mindest“ und „Höchst“, um anzugeben, wie oft der Abschnitt wiederholt werden kann](/help/edge/assets/repeatable-section-set-min-max.png)

1. Verwenden Sie [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content), um das Blatt in der Vorschau anzuzeigen und zu veröffentlichen.

   Beim Hinzufügen eines wiederholbaren Abschnitts finden Benutzende ein intuitives Symbol **Löschen**, wodurch das Entfernen wiederholbarer Abschnitte vereinfacht wird. Nach dem Hinzufügen können diese Abschnitte nicht auf weniger Instanzen reduziert werden, als durch die Eigenschaft `min` angegeben. Dadurch wird sichergestellt, dass die festgelegte Mindestanforderung für das Ausfüllen des Formulars eingehalten wird.

<!--

For example, consider a form used to collect information from users applying for a loan. . You may have a repeatable section for capturing details of each co-applicant. The repeatable section would typically contain fields such as co-co-applicant

The form allows users to provide personal information, including details of the co-applicants. Users can enter details for co-applicants, with this section being repeatable.

![Repeatable sections in forms](/help/forms/assets/eds-repeatable.png)

## Prerequisites

The [Adaptive Forms Block is enabled](/help/edge/docs/forms/create-forms.md) for your Edge Delivery Services project. 

## Add a repeatable section to a form 

Let's take an example of a loan application form. The form enables users to submit personal information. You can include co-applicant details using repeatable sections, with the option to add a minimum and maximum of three co-applicant sections.

"_You can use a Microsoft Excel file on your SharePoint Site or Google Sheet file on Google Drive to develop a form. Examples in this document are based on a [Microsoft Excel file on your SharePoint Site](https://www.aem.live/docs/setup-customer-SharePoint)._" 


To add repeatable sections in Edge Delivery:

1. [Author a form using Microsoft Excel](#author-form)
2. [Preview and publish the form](#preview-form)

### Author a form using Microsoft Excel {#author-form}

1. Go to your Edge Deliver project folder on Microsoft SharePoint or Google Workspace and open your spreadsheet. For example, open an a spreadsheet named `loan-application.xlsx`.

1. Add a new columns labeled `Repeatable` to the sheet contaning your form fields. By default, the `shared-default` sheet contains the form fields.  

1. Add new columns labeled as `Repeatable`, `Min`, and `Max` in your Microsoft Excel file.
1. Specify the value for the `Repeatable` column as `True` for the fieldset that you want to make repeatable.
1. Specify the values for the `Min` and `Max` columns. The `Min` value represents the minimum number of occurrences for which the panel repeats, while the `Max` value represents the maximum number of occurrences for which the panel repeats.
1. Save your Microsoft Excel file.
     
>[!NOTE]
>
> Here is the [Loan application](/help/forms/assets/loan-application.xlsx) excel sheet for your reference. 

### Preview/Publish the form using your Edge Delivery Service

1. Open or create new document file in a Microsft SharePoint Site to embed the Excel sheet  in it using a `Form Block`. For example, open the `index` file and add a `Form Block`.
2. Open the command prompt, navigate to your AEM Edge Delivery project directory on your local machine, and execute the command as `aem up`.

The form is accessible at `https://localhost:3000`, where clicking the `Add` button adds new repeatable section for entering co-applicant details. You can also delete the repeatable section by clicking the `Delete` button. 

>[!NOTE]
>
> If you encounter a "Page Not Found" error while accessing your form at localhost, add the directory name of the Microsoft SharePoint Site in front of the URL where your form is located. For example, `http://localhost:3000/<dir-name>/`

-->


## Siehe auch

{{see-more-forms-eds}}
