---
title: Erstellen von eigenständigen Formularen basierend auf Kernkomponenten- oder Edge Delivery Services-Vorlagen und Veröffentlichen in Edge Delivery Services
description: In diesem Artikel wird erläutert, wie Sie adaptive Formulare erstellen, indem Sie im Assistenten zur Formularerstellung eine auf Kernkomponenten oder Edge Delivery Services basierende Vorlage auswählen. Sie können die Formulare auch in AEM Edge Delivery Services veröffentlichen.
feature: Edge Delivery Services
role: User
exl-id: 1eab3a3d-5726-4ff8-90b9-947026c17e22
source-git-commit: e1ead9342fadbdf82815f082d7194c9cdf6d799d
workflow-type: tm+mt
source-wordcount: '1687'
ht-degree: 95%

---


# Von der Erstellung bis zur Veröffentlichung: AEM Forms auf Edge Delivery Services

<span class="preview"> Diese Funktion ist über das Early-Access-Programm verfügbar. Um den Zugriff anzufordern, senden Sie eine E-Mail mit dem Namen Ihrer GitHub-Organisation und dem Namen des Repositorys von Ihrer offiziellen Adresse an <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a>. Wenn die Repository-URL beispielsweise https://github.com/adobe/abc lautet, lautet der Name der Organisation „adobe“ und der Name des Repositorys „abc“.</span>

Mit Adobe Experience Manager (AEM) können Sie Formulare erstellen, die ansprechend, reaktionsfähig und dynamisch sind. Es bietet mehrere Authoring-Methoden, die jeweils für unterschiedliche Anforderungen und Benutzerkompetenzen geeignet sind.

Dieser Artikel konzentriert sich auf den Ansatz, bei dem Formulare in der AEM-Umgebung erstellt und über Edge Delivery Services veröffentlicht werden. Formulare, die mit auf Kernkomponenten basierenden Vorlagen erstellt wurden, können sowohl in AEM als auch in Edge Delivery Services veröffentlicht werden, was eine flexible Bereitstellung ermöglicht. Formulare, die mit auf Edge Delivery Services basierenden Vorlagen erstellt wurden, können hingegen nur in Edge Delivery Services veröffentlicht werden.

![Erstellen und Veröffentlichen von adaptiven Formularen](/help/edge/docs/forms/universal-editor/assets/author-publish-af.png){width=50% align=center}

## Vorteile der Erstellung von Formularen in AEM und der Veröffentlichung mit Edge Delivery Services:

* **Beibehaltung bestehender AEM-Workflows**: Organisationen können weiterhin ihre etablierten AEM-Workflows und Governance-Strukturen nutzen, um Konsistenz und Kontrolle über die Inhaltserstellung sicherzustellen.

* **Verbesserte Leistung**: Die Veröffentlichung über Edge Delivery Services führt zu schnelleren Rendering-Zeiten, einem verbesserten Benutzererlebnis und kürzeren Seitenladezeiten.

* **Verbessertes SEO**: Edge Delivery Services wurde entwickelt, um Inhalte mit hohen Google Lighthouse-Bewertungen bereitzustellen, was zu einer besseren Suchmaschinenoptimierung und einer erhöhten Sichtbarkeit führen kann.

* **Flexible Bereitstellungsoptionen**: Formulare, die mit Kernkomponenten erstellt wurden, können sowohl in AEM als auch in Edge Delivery Services veröffentlicht werden, was Flexibilität bei Bereitstellungsstrategien bietet.

## Bevor Sie beginnen

Bevor Sie mit dem Erstellen von Formularen in AEM und deren Veröffentlichung über Edge Delivery Services beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

* Stellen Sie sicher, dass Sie ein GitHub-Repository für Edge Delivery Services konfiguriert haben.
   * Wenn Sie kein Repository haben, benötigen Sie ein [neues AEM-Projekt mit vorkonfiguriertem adaptiven Formularbaustein](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block).
   * Wenn Sie über ein Repository verfügen, fügen Sie den adaptiven Formularbaustein zu Ihrem vorhandenen Repository hinzu. Detaillierte Anweisungen finden Sie unter [Erste Schritte mit Edge Delivery Services für AEM Forms](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project).
* Stellen Sie eine Verbindung zwischen Ihrer AEM-Umgebung und dem GitHub-Repository her. [Wie wird sie hergestellt?](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template)

Ein Entscheidungsflussdiagramm, das die Einrichtung und Veröffentlichung von adaptiven Formularen erklärt:

![GitHub-Repository-Workflow](/help/forms/assets/repo-workflow.png){width=auto}

## Erstellen von Formularen in AEM und Veröffentlichen in Edge Delivery Services

Führen Sie die folgenden Schritte aus, um Formulare in AEM zu erstellen und in Edge Delivery Services zu veröffentlichen:

[&#x200B;1. Vorlage auswählen und Formular erstellen](#choose-a-template-and-create-the-form)

[&#x200B;2. Formular gestalten](#author-the-form)

[&#x200B;3. Formular veröffentlichen](#publish-a-form)

### Auswählen einer Vorlage und Erstellen des Formulars

Sie können Formulare in einer AEM-Instanz zur Veröffentlichung in Edge Delivery Services erstellen, indem Sie Folgendes verwenden:

>[!BEGINTABS]

>[!TAB Vorlage von Edge Delivery Services]

Führen Sie die folgenden Schritte aus, um die Vorlage auszuwählen und das Formular zu erstellen:

1. Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Autoreninstanz an.
1. Wählen Sie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.
1. Wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptive Formulare]**. Der Assistent wird geöffnet.
1. Wählen Sie auf der Registerkarte **Quelle** eine **Edge Delivery Services-basierte Vorlage** aus:

   ![Erstellen von EDS-Formularen](/help/edge/assets/create-eds-forms.png)

   Wenn Sie eine **Edge Delivery Services-basierte Vorlage** auswählen, ist die Schaltfläche **[!UICONTROL Erstellen]** aktiviert.
1. (Optional) Auf der Registerkarte **[!UICONTROL Datenquelle]** oder **[!UICONTROL Übermittlung]** können Sie eine Datenquelle oder eine Übermittlungsaktion auswählen.
1. (Optional) Auf der Registerkarte **[!UICONTROL Versand]** können Sie ein Datum für die Veröffentlichung oder das Rückgängigmachen der Veröffentlichung eines Formulars angeben.
1. Klicken Sie auf **[!UICONTROL Erstellen]**. Daraufhin wird der Assistent **Formular erstellen** angezeigt.

   1. Geben Sie den **Namen** und den **Titel** an.
   1. Geben Sie die **GitHub-URL** an. Wenn Ihr GitHub-Repository beispielsweise `edsforms` heißt und sich unter dem Konto `wkndforms` befindet, lautet die URL wie folgt:
      `https://github.com/wkndforms/edsforms`

   ![Assistent für die Formularerstellung](/help/edge/assets/create-form-wizard.png)

   Wenn Sie auf **[!UICONTROL Erstellen]** klicken, wird das Formular zur Erstellung im universellen Editor geöffnet.

   ![Screenshot des universellen Editors, der ein in Bearbeitung befindliches Formular mit der Komponentenpalette auf der linken Seite, der Formulararbeitsfläche in der Mitte und dem Bedienfeld „Eigenschaften“ auf der rechten Seite zeigt](/help/edge/assets/author-form.png)
1. Klicken Sie auf **[!UICONTROL Erstellen]**, um das Formular zu erstellen. Jetzt können Sie das [Formular mit dem universellen Editor erstellen](#author-the-form).

>[!TAB Kernkomponentenbasierte Vorlage]

Führen Sie die folgenden Schritte aus, um die Vorlage auszuwählen und das Formular zu erstellen:

1. Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Autoreninstanz an.
1. Wählen Sie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.
1. Wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptive Formulare]**. Der Assistent wird geöffnet.
1. Wählen Sie auf der Registerkarte **Quelle** eine **Kernkomponentenbasierte Vorlage** sowie ein **Design** aus. Die Schaltfläche **[!UICONTROL Erstellen]** ist aktiviert:

   ![Kernkomponentenbasierte Vorlage](/help/forms/assets/core-component-based-template.png)

1. (Optional) Auf der Registerkarte **[!UICONTROL Datenquelle]** oder **[!UICONTROL Übermittlung]** können Sie eine Datenquelle oder eine Übermittlungsaktion auswählen.
1. (Optional) Auf der Registerkarte **[!UICONTROL Versand]** können Sie ein Datum für die Veröffentlichung oder das Rückgängigmachen der Veröffentlichung eines Formulars angeben.
1. Klicken Sie auf **[!UICONTROL Erstellen]**. Daraufhin wird der Assistent **Formular erstellen** angezeigt.
   1. Geben Sie den **Namen** und den **Titel** an.
   1. Geben Sie den Speicherort für das adaptive Formular im Feld **Pfad** an.

   ![Assistent für die Formularerstellung](/help/forms/assets/create-cc-form.png)

   Wenn Sie auf **[!UICONTROL Erstellen]** klicken, wird das Formular im Editor zur Bearbeitung geöffnet.

   ![Editor für adaptive Formulare](/help/forms/assets/af-editor-form.png)

1. Klicken Sie auf **[!UICONTROL Erstellen]**, um das Formular zu erstellen. Jetzt können Sie [das Formular mit dem Editor für adaptive Formulare gestalten](#author-the-form).

>[!ENDTABS]

### Gestalten des Formulars

Die Formulare, die mit der Edge Delivery Services-basierten Vorlage erstellt wurden, werden zur Bearbeitung im [universellen Editor](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) geöffnet. Die Formulare, die mit der auf Kernkomponenten basierenden Vorlage erstellt wurden, werden jedoch im Editor für adaptive Formulare zur Bearbeitung geöffnet.

Führen Sie die folgenden Schritte aus, um Formulare mit dem universellen Editor für Edge Delivery Services-basierte Vorlagen oder mit dem Editor für adaptive Formulare für kernkomponentenbasierte Vorlagen zu erstellen:

>[!BEGINTABS]

>[!TAB Edge Delivery Services-basierte Vorlage]


1. Öffnen Sie den Inhalts-Browser und navigieren Sie in der **Inhaltsstruktur** zur Komponente **[!UICONTROL Adaptives Formular]**.

   ![Inhaltsstruktur](/help/edge/assets/content-tree.png)

1. Klicken Sie auf das Symbol **[!UICONTROL Hinzufügen]** und fügen Sie die gewünschten Komponenten aus der Liste der **adaptiven Formularkomponenten** hinzu.
   ![Hinzufügen der Komponente](/help/edge/assets/add-component.png)

   Im folgenden Screenshot sehen Sie das `Registration Form`, das im universellen Editor erstellt wurde:

   ![Screenshot eines ausgefüllten Kontaktformulars im universellen Editor mit Formularfeldern für Name, E-Mail, Telefon und Nachricht mit korrektem Stil und Layout](/help/edge/assets/contact-us.png)

>[!NOTE]
>
> Detaillierte Anweisungen zum Erstellen eines adaptiven Formulars mit dem universellen Editor finden Sie [hier](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg).

Nun können Sie [die Übermittlungsaktionen für Formulare konfigurieren und anpassen](/help/edge/docs/forms/universal-editor/submit-action.md).

>[!TAB Kernkomponentenbasierte Vorlage]

1. Klicken Sie im Abschnitt **Komponenten hierher ziehen** auf **[!UICONTROL Komponente einfügen]**.

   ![Komponenten hierher ziehen](/help/forms/assets/drag-components-af-editor.png)

1. Wählen Sie die gewünschten Komponenten aus der Liste **Adaptive Formularkomponenten**.

   ![Hinzufügen von Komponenten](/help/forms/assets/add-component-af.png)

Im folgenden Screenshot wird das im Editor für adaptive Formulare erstellte `Enrollment Form` angezeigt:

![Editor für adaptive Formulare](/help/forms/assets/af-editor-form.png)

>[!NOTE]
>
> Eine ausführliche Anleitung zum Erstellen eines adaptiven Formulars auf der Grundlage der Kernkomponentenvorlage finden Sie [hier](/help/forms/creating-adaptive-form-core-components.md).

Nun können Sie [die Übermittlungsaktionen für Formulare konfigurieren und anpassen](/help/forms/configure-submit-actions-core-components.md).

>[!ENDTABS]

### Veröffentlichen des Formulars

Um ein adaptives Formular in Edge Delivery Services zu veröffentlichen, müssen Sie [eine Edge Delivery Services-Konfiguration auf einer AEM-Instanz erstellen](#create-an-edge-delivery-services-configuration).

#### Erstellen einer Edge Delivery Services-Konfiguration

Führen Sie die folgenden Schritte aus, um die Edge Delivery Services-Konfiguration zu erstellen:

>[!BEGINTABS]
>[!TAB Edge Delivery Services-basierte Vorlage]


Die Edge Delivery Services-Konfiguration für die Formulare, die auf Edge Delivery Services basieren, wird automatisch im Konfigurations-Container des jeweiligen Formulars erstellt.

![Edge Delivery Services-Konfiguration](/help/edge/assets/aem-instance-eds-configuration.png)

>[!TAB Kernkomponentenbasierte Vorlage]

1. Navigieren Sie in Ihrer Autoreninstanz in AEM Forms as a Cloud Service zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud-Services]** > **[!UICONTROL Edge Delivery Services-Konfiguration]**.

   ![Auswählen der Edge Delivery Services-Konfiguration](/help/edge/assets/select-eds-conf.png)

2. Wählen Sie den Ordner aus, der dem Namen des Formulars entspricht. Wenn Ihr Formular beispielsweise `enrollment-form` heißt, wählen Sie den Ordner `forms/enrollment-form` aus und klicken Sie auf **[!UICONTROL Erstellen]** > **[!UICONTROL Konfiguration]**:

   ![Edge Delivery Services-Konfiguration](/help/forms/assets/create-eds-conf.png)

3. Klicken Sie auf die **[!UICONTROL Edge Delivery Services-Konfiguration]** und anschließend auf **[!UICONTROL Eigenschaften]**, um die Eigenschaften zu öffnen:

   ![Automatisch erstellte Konfiguration](/help/forms/assets/eds-conf.png)

   Die Edge Delivery Services-Konfiguration wird angezeigt.

4. Geben Sie in der Edge Delivery Services-Konfiguration Folgendes an:

   * **Organisation**: Geben Sie Ihren GitHub-Organisationsnamen an.

   * **Site-Name**: Geben Sie Ihren GitHub-Repository-Namen an.
   * **Verzweigung**: Geben Sie den Namen der Verzweigung an. Lassen Sie das Textfeld leer, wenn die Hauptverzweigung verwendet wird.
   * **(Optional) Edge Host**: Belassen Sie die Option „Edge Host“, wie sie ist. Das Formular wird in der Vorschau-Umgebung (.page) und in der Live-Umgebung (.live) veröffentlicht.
   * **(Optional) Site-Authentifizierungs-Token**: Verwenden Sie das Site-Authentifizierungs-Token, um Anfragen zwischen Ihrer AEM-Instanz und Edge Delivery Services sicher zu authentifizieren.

5. Klicken Sie auf **[!UICONTROL Speichern und schließen]**. Die Konfiguration wird erstellt. 

>[!ENDTABS]

#### Zugriff auf das Formular in Edge Delivery Services

Um in Edge Delivery Services auf das Formular zuzugreifen, muss das Formular veröffentlicht werden. Führen Sie zur Veröffentlichung des Formulars folgende Schritte aus:

>[!BEGINTABS]
>[!TAB Im universellen Editor]

1. Veröffentlichen Sie das Formular nun in Edge Delivery Services, indem Sie oben rechts im universellen Editor auf die Schaltfläche **[!UICONTROL Veröffentlichen]** klicken.

![Screenshot des universellen Editors mit dem Dialogfeld „Veröffentlichen“ mit Formularveröffentlichungsoptionen und Bestätigungsschaltflächen](/help/edge/assets/publish-form.png)

>[!NOTE]
>
> Informationen zum Veröffentlichen eines Formulars in Edge Delivery Services finden Sie im Artikel [Veröffentlichen und Bereitstellen](/help/edge/docs/forms/universal-editor/publish-forms.md).

>[!TAB Im Editor für adaptive Formulare]

1. Navigieren Sie in der Experience Manager Forms-Konsole zum übergeordneten Ordner und wählen Sie ein Formular aus, das Sie veröffentlichen möchten.

1. Klicken Sie auf die Option **[!UICONTROL Veröffentlichen]** auf der Symbolleiste, um alle Referenz-Assets anzuzeigen, die mit dem Formular veröffentlicht werden sollen.

![Veröffentlichen eines Formulars im Editor für adaptive Formulare](/help/forms/assets/publish-af-editor.png)

>[!NOTE]
>
> Informationen zum Veröffentlichen eines im Editor für adaptive Formulare erstellten Formulars finden Sie im Artikel [ Verwalten der Veröffentlichung in Experience Manager Forms](/help/forms/manage-publication.md).

>[!ENDTABS]

* **Staging-Version (für Tests)**: Die Staging-Version zeigt die unveröffentlichte, funktionierende Version des Formulars zu Testzwecken an. Verwenden Sie das folgende URL-Format, um eine Vorschau des Formulars anzuzeigen, bevor es live geschaltet wird:

  `https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>`



* **Live-Version (veröffentlichtes Formular)**: Die Live-Version zeigt die zuletzt veröffentlichte Version des Formulars an, auf die Endbenutzende zugreifen können. Verwenden Sie das folgende URL-Format, um auf die veröffentlichte Live-Version des Formulars zuzugreifen:

  `https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>`

  Die URL-Struktur bleibt für Staging- und Live-Versionen gleich. Der angezeigte Inhalt unterscheidet sich jedoch je nach Kontext.

In den folgenden Screenshots werden URLs von Staging- und Live-Formularen sowie visuelle Vorschauen für Formulare verglichen, die mit Edge Delivery Services-basierten und kernkomponentenbasierten Vorlagen erstellt wurden:

>[!BEGINTABS]
>[!TAB Edge Delivery Services-basierte Vorlage]

<table border="1" style="width: 100%; border-collapse: collapse; text-align: left;">
    <thead>
    <tr>
      <th style="width: 20%;"><strong>Version</strong></th>
      <th style="width: 80%;"><strong>Bild</strong></th>
    </tr>
    </thead>
    <tbody>
    <tr>
      <td>Staging-Version</td>
      <td><img src="/help/forms/assets/registration-form-staged-version.png" alt="Staging-Version des Registrierungsformulars" style="width: 100%; height: auto;" /></td>
    </tr>
    <tr>
      <td>Live-Version</td>
      <td><img src="/help/forms/assets/registration-form-live-version.png" alt="Live-Version des Registrierungsformulars" style="width: 100%; height: auto;" /></td>
    </tr>
    </tbody>
  </table>

>[!TAB Kernkomponentenbasierte Vorlage]

<table border="1" style="width: 100%; border-collapse: collapse; text-align: left;">
  <thead>
    <tr>
      <th style="width: 20%;"><strong>Version</strong></th>
      <th style="width: 80%;"><strong>Bild</strong></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Staging-Version</td>
      <td><img src="/help/forms/assets/enrollment-form-staged-version.png" alt="Staging-Version des Anmeldungsformulars" style="width: 100%; height: auto;" /></td>
    </tr>
    <tr>
      <td>Live-Version</td>
      <td><img src="/help/forms/assets/enrollment-form-live-version.png" alt="Live-Version des Anmeldungsformulars" style="width: 100%; height: auto;" /></td>
    </tr>
  </tbody>
  </table>

>[!ENDTABS]

## Fehlerbehebung

Haben Sie Probleme beim Laden Ihres Formulars? Im Folgenden finden Sie einige häufige Probleme und Lösungswege:

* **Formular-URL**: Vergewissern Sie sich, dass die URL Ihres Formulars nicht auf der Erweiterung „.html“ endet. Edge Deliver Service benötigt diese Erweiterung nicht.

* **AEM Author-URL**: Stellen Sie sicher, dass die in der Datei `fstab.yaml` aufgeführte AEM Author-URL korrekt formatiert ist. Sie sollte die folgenden Details enthalten:

   * die korrekte verantwortliche GitHub-Person
   * den korrekten Repository-Namen
   * die spezifische Verzweigung, die Sie für Edge Delivery Services verwenden

## Beginnen mit dem Erstellen von Formularen

{{universal-editor-see-also}}

<!-- * **JSON Display**: If you see only JSON data instead of the actual form, your form block might be outdated. You can update it to the latest version available on https://github.com/adobe-rnd/aem-boilerplate-forms.

### Managing a form

You can perform several operations on form using the AEM Forms user interface.

1. Login into your AEM Forms as a Cloud Service author instance.
1. Select **[!UICONTROL Adobe Experience Manager]** &gt; **[!UICONTROL Forms]** &gt; **[!UICONTROL Forms & Documents]**.

1. Select a form and the toolbar displays the following operations you can perform on the selected form.

<table>
 <tbody>
  <tr>
   <td><p><strong>Operation</strong></p> </td>
   <td><p><strong>Description</strong></p> </td>
  </tr>
  <tr>
   <td><p>Edit</p> </td>
   <td><p>Opens the form in edit mode.<br /> <br /> </p> </td>
  </tr>
    <tr>
   <td><p>Properties</p> </td>
   <td><p>Provides options to modify the properties of the form.<br /> <br /> </p> </td>
  </tr>
  <td><p>Copy</p> </td>
   <td><p> Provides options to copy the form  and paste it at the desired location. <br /> <br /> </p> </td>
  </tr>
   <tr>
   <td><p>Preview</p> </td>
   <td><p>Provides options to preview the form as HTML or perform a custom preview by merging data from an XML file with the form. <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Download</p> </td>
   <td><p>Downloads the selected form.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Start Review/Manage Review</p> </td>
   <td><p>Allows initiating and managing a review of the selected form.<br /> <br /> </p> </td>
  </tr>
  <!--<tr>
   <td><p>Add Dictionary</p> </td>
   <td><p>Generates a dictionary for localizing the selected fragment. For more information, see <a>Localizing Adaptive Forms</a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Publish / Unpublish</p> </td>
   <td><p>Publishes / unpublishes the selected form.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Delete</p> </td>
   <td><p>Deletes the selected form.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Compare</p> </td>
   <td><p>Compares two different form for previewing purposes.<br /> <br /> </p> </td>
  </tr>
 </tbody>
</table> 


## How Edge Delivery Services Forms Work?

Users can author Edge Delivery Services Forms using document-based authoring tools such as Google Drive, SharePoint, or the Universal Editor (WYSIWYG authoring), while leveraging the basic styling, behaviour and components available in the GitHub repository. Once authored, Edge Delivery Services Forms can send data to any platform using the Forms Submission Service.

![How Edge Delivery Services Forms works](/help/edge/docs/forms/assets/eds-forms-working.png)

### Key components of Edge Delivery Services Forms

The key components of Edge Delivery Servies Forms are:

* **GitHub Repository**: The GitHub repository serves as a boilerplate for creating Edge Delivery Services Forms. The forms leverage basic styling and functionality from the repository and allow users to add customizations and custom components to the Edge Delivery Services Forms.

* **Form Authoring**: Edge Delivery Services Forms support two types of authoring: WYSIWYG and document-based authoring. Document-based authoring enables users to create forms using familiar tools like Google Docs and Microsoft Office. WYSIWYG authoring allows users to design forms visually using the Universal Editor, making it easy for non-technical users to create and manage forms. Universal Editor offers an intuitive form creation experience and provides access to numerous form capabilities.

* **Forms Submission Service**: The Forms Submission Service allows you to store data from forms submissions on any platform, such as OneDrive, SharePoint, or Google Sheets, making it easy to access and manage form data within your preferred system.-->
