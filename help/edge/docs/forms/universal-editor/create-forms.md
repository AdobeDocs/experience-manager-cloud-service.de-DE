---
title: Erstellen von eigenständigen adaptiven Formularen mit dem universellen Editor?
description: In diesem Artikel wird erläutert, wie Sie adaptive Formulare mit dem Assistenten zur Formularerstellung in der AEM-Autoreninstanz erstellen und Formulare in AEM Edge Delivery Services veröffentlichen.
feature: Edge Delivery Services
role: User
hide: true
hidefromtoc: true
exl-id: 1eab3a3d-5726-4ff8-90b9-947026c17e22
source-git-commit: 3db311812f6c4521baf1364523a0e0b1134fee65
workflow-type: tm+mt
source-wordcount: '1215'
ht-degree: 85%

---

# Erstellen eigenständiger Formulare mit dem universellen Editor (WYSIWYG)

<span class="preview"> Diese Funktion ist über das Early-Access-Programm verfügbar. Um den Zugriff anzufordern, senden Sie eine E-Mail mit dem Namen Ihrer GitHub-Organisation und dem Namen des Repositorys von Ihrer offiziellen Adresse an <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a>. Wenn die Repository-URL beispielsweise https://github.com/adobe/abc lautet, lautet der Name der Organisation „adobe“ und der Name des Repositorys „abc“.</span>

Dieser Artikel führt Sie durch den Prozess zum Erstellen der eigenständigen Formulare mit dem universellen Editor, indem Sie eine auf Edge Delivery Services basierende Vorlage aus dem Assistenten zur Formularerstellung auswählen. Sie können die erstellten Formulare auch mit dem universellen Editor in AEM Edge Delivery Services veröffentlichen.

<!--To publish forms to Edge Delivery Services, you must first establish a connection between your AEM environment and your GitHub repository. Once connected, you can author the forms using the Universal Editor, which follows a WYSIWYG (What You See Is What You Get) approach for a seamless and consistent user experience with Sites.-->

Bevor Sie beginnen, erfahren Sie mehr über die Arten der Formular-Komponenten, die Ihnen zur Verfügung stehen:

* [Edge Delivery Services für AEM Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) ist ein zusammenstellbarer Satz von Diensten, der eine schnelle Entwicklungsumgebung ermöglicht, in der Autorinnen und Autoren (neue) Formulare mit dem universellen Editor schnell aktualisieren, veröffentlichen und live schalten können.  Der universelle Editor vereinfacht die Formularerstellung für Adobe Edge Delivery Services mit einer benutzerfreundlichen, visuellen WYSIWYG-Oberfläche.

* [Kernkomponenten adaptiver Formulare](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de): Dies sind standardisierte Datenerfassungskomponenten. Diese Komponenten bieten Anpassungsfunktionen, kürzere Entwicklungszeiten und niedrigere Wartungskosten für Ihre Erlebnisse bei der digitalen Registrierung. Entwickelnde können diese Komponenten einfach anpassen und gestalten. Sie können unter [https://aemcomponents.dev/](https://aemcomponents.dev/) die verfügbaren Kernkomponenten in Aktion anzeigen **Adobe empfiehlt die Verwendung dieser modernen und erweiterbaren Komponenten zur Entwicklung von adaptiven Formularen**.

* [Foundation-Komponenten adaptiver Formulare](/help/forms/creating-adaptive-form.md): Hierbei handelt es sich um klassische (alte) Datenerfassungskomponenten. Sie können diese weiterhin verwenden, um Ihre vorhandenen Foundation-Komponenten auf Grundlage des adaptiven Formulars zu bearbeiten. Wenn Sie neue Formulare erstellen, empfiehlt Adobe die Verwendung von  [Kernkomponenten von adaptiven Formularen, um ein adaptives Formular zu erstellen](#create-an-adaptive-form-core-components).

AEM Forms umfasst einen Block, der als adaptiver Formularblock bezeichnet wird und mit dem Sie mühelos Edge Delivery Services-Formulare erstellen können, um Daten zu erfassen und zu speichern. Sie können [ein neues AEM-Projekt vorkonfiguriert mit einem adaptiven Formularblock erstellen](#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) oder [den adaptiven Formularblock zu einem bestehenden AEM-Projekt hinzufügen](#add-adaptive-forms-block-to-your-existing-aem-project).

![GitHub-Repository-Workflow](/help/edge/assets/repo-workflow.png)

## Voraussetzungen

* [Richten Sie Ihr GitHub-Repository so ein](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template), dass eine Verbindung zwischen Ihrer AEM-Umgebung und dem GitHub-Repository hergestellt wird.
* Wenn Sie bereits Edge Delivery Services verwenden, fügen Sie Ihrem GitHub-Repository die neueste Version des [adaptiven Formularblocks](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) hinzu.
* Die AEM Forms-Autoreninstanz enthält eine Vorlage, die auf Edge Delivery Services basiert. Stellen Sie sicher, dass die [neueste Version der Kernkomponenten](https://github.com/adobe/aem-core-forms-components) in Ihrer Umgebung installiert ist.
* Halten Sie die URL Ihrer AEM Forms as a Cloud Service-Autoreninstanz und Ihres GitHub-Repositorys bereit.

## Erstellen eines adaptiven Formulars mit dem universellen Editor

Mit dem universellen Editor können Sie responsive und interaktive, eigenständige Formulare schnell mithilfe vorgefertigter Komponenten wie Textfeldern, Kontrollkästchen und Optionsfeldern entwerfen. Er bietet leistungsstarke Funktionen wie dynamische Regeln, reibungslose Datenintegration und Anpassungsoptionen, mit denen Sie Formulare entsprechend Ihren genauen Anforderungen erstellen können.

>[!NOTE]
>
> Sie können auch [ein Formular in AEM Sites mithilfe der Site-Vorlage von Edge Delivery Services Site im universellen Editor erstellen und in Edge Delivery Services veröffentlichen](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project).

Um ein eigenständiges adaptives Formular mit dem universellen Editor zu erstellen, führen Sie die folgenden Schritte aus:

1. **Erstellen eines adaptiven Formulars auf der AEM Forms-Autoreninstanz**

   1. Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Autoreninstanz an.
   1. Wählen Sie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.
   1. Wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptive Formulare]**. Der Assistent wird geöffnet.
   1. Wählen Sie auf der Registerkarte **Quelle** eine auf Edge Delivery Services basierende Formularvorlage aus:

      ![Erstellen von EDS-Formularen](/help/edge/assets/create-eds-forms.png)


      Wenn Sie eine Edge Delivery Services-basierte Vorlage auswählen, ist **[!UICONTROL Schaltfläche]** aktiviert.
   1. Source (Optional) Auf den Registerkarten **[!UICONTROL Daten]** oder **[!UICONTROL Übermittlung]** können Sie eine Datenquelle oder eine Übermittlungsaktion auswählen.
   1. (Optional) Auf der Registerkarte **[!UICONTROL Versand]** können Sie ein Datum für die Veröffentlichung oder das Rückgängigmachen der Veröffentlichung eines adaptiven Formulars angeben.

   1. Klicken Sie auf **[!UICONTROL Erstellen]**. Daraufhin wird der Assistent **Formular erstellen** angezeigt.
   1. Geben Sie die **Name** und **Title** an.
   1. Geben Sie die **GitHub-URL** an. Wenn Ihr GitHub-Repository beispielsweise `edsforms` heißt und sich unter dem Konto `wkndforms` befindet, lautet die URL wie folgt:
      `https://github.com/wkndforms/edsforms`
   1. Klicken Sie auf **[!UICONTROL Erstellen]**.

      ![Assistent für die Formularerstellung](/help/edge/assets/create-form-wizard.png)

      Wenn Sie auf **[!UICONTROL Erstellen]** klicken, wird das Formular zwecks Erstellung im universellen Editor geöffnet.

      ![Erstellen des Formulars](/help/edge/assets/author-form.png)

      <!-- >[!NOTE]
        >
        > The Edge Delivery Services configuration for the forms based on Edge Delivery Services template is created automatically at the form's configuration container.-->

      Wenn Sie auf **[!UICONTROL Erstellen]** klicken, wird das Formular zwecks Erstellung im universellen Editor geöffnet.

1. **Erstellen des Formulars im universellen Editor**

   1. Öffnen Sie den Inhalts-Browser und navigieren Sie in der **Inhaltsstruktur** zur Komponente **[!UICONTROL Adaptives Formular]**.

      ![Inhaltsstruktur](/help/edge/assets/content-tree.png)

   1. Klicken Sie auf das Symbol **[!UICONTROL Hinzufügen]** und fügen Sie die gewünschten Komponenten aus der Liste der **adaptiven Formularkomponenten** hinzu.

      ![Hinzufügen der Komponente](/help/edge/assets/add-component.png)

   1. Wählen Sie die hinzugefügte adaptive Formularkomponente aus und aktualisieren Sie ihre Eigenschaften mithilfe von **[!UICONTROL Eigenschaften]**.

      ![Öffnen von Eigenschaften](/help/edge/assets/component-properties.png)

      Im folgenden Screenshot sehen Sie das einfache Formular `Registration Form`, das im universellen Editor erstellt wurde:

      ![Kontaktformular](/help/edge/assets/contact-us.png)

      Nun können Sie [Übermittlungsaktionen für Formulare konfigurieren und anpassen](/help/edge/docs/forms/universal-editor/submit-action.md).


<!--
## **Edge Delivery Services configuration of form**



   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** >  **[!UICONTROL Edge Delivery Services Configuration]** on your AEM Forms as a Cloud Service author instance.

        ![Select Edge Delivery Services Configuration](/help/edge/assets/select-eds-conf.png)
   1. Select the folder that matches the form's name. For example, if your form is called 'registration-form' choose the folder `forms/registration-form` and selct the configuration and publish the configuration:

        ![Edge Delivery Services Configuration](/help/edge/assets/aem-instance-eds-configuration.png)

   1. Click **[!UICONTROL Properties]** to see the configuration.   
        ![Automatically created configuration](/help/edge/assets/aem-forms-create-configuration-github.png)

        You can leave the Edge Host option as it is. The form would be published to both preview (.page) and live (.live) environments. 

   1. Click **[!UICONTROL Save and Close]**. The configuration is saved. -->

## Veröffentlichen des Formulars

Veröffentlichen Sie das eigenständige Formular nun in Edge Delivery Services, indem Sie oben rechts im universellen Editor auf die Schaltfläche **[!UICONTROL Veröffentlichen]** klicken.

![Veröffentlichen des Formulars](/help/edge/assets/publish-form.png)

>[!NOTE]
>
> Informationen zum Veröffentlichen eines Formulars in Edge Delivery Services finden Sie im Artikel [Veröffentlichen und Bereitstellen](/help/edge/docs/forms/universal-editor/publish-forms.md).

So greifen Sie auf das Formular in Edge Delivery Services zu:

* **Staging-Version (für Tests)**: Die Staging-Version zeigt die unveröffentlichte, funktionierende Version des Formulars zu Testzwecken an. Verwenden Sie das folgende URL-Format, um eine Vorschau des Formulars anzuzeigen, bevor es live geschaltet wird:

  `https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>`

  Wenn das Repository Ihres Projekts beispielsweise „edsforms“ heißt, sich unter dem Konto „wkndforms“ befindet und Sie die Verzweigung „main“ sowie das Formular „Registration Form“ verwenden, sieht die URL der Staging-Version wie folgt aus:
  `https://main--edsforms--wkndforms.aem.page/content/forms/af/registration-form`

* **Live-Version (veröffentlichtes Formular)**: Die Live-Version zeigt die zuletzt veröffentlichte Version des Formulars an, auf die Endbenutzende zugreifen können. Verwenden Sie das folgende URL-Format, um auf die veröffentlichte Live-Version des Formulars zuzugreifen:

  `https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>`

  Wenn das Repository Ihres Projekts beispielsweise „edsforms“ heißt, sich unter dem Konto „wkndforms“ befindet und Sie die Verzweigung „main“ sowie das Formular „Registration Form“ verwenden, sieht die URL der Staging-Version wie folgt aus:
  `https://main--edsforms--wkndforms.aem.live/content/forms/af/registration-form`

Die URL-Struktur bleibt für Staging- und Live-Versionen gleich. Der angezeigte Inhalt unterscheidet sich jedoch je nach Kontext:

![Anzeigen veröffentlichter Formulare](/help/edge/assets/eds-view-publish-form.png)

## Verwalten von Formularen

Sie können über die Benutzeroberfläche von AEM Forms mehrere Vorgänge mit einem Formular durchführen.

1. Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Autoreninstanz an.
1. Wählen Sie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** aus.

1. Wenn Sie ein Formular auswählen, werden in der Symbolleiste die folgenden Vorgänge angezeigt, die Sie mit dem ausgewählten Formular durchführen können.

<table>
 <tbody>
  <tr>
   <td><p><strong>Vorgang</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p>Bearbeiten</p> </td>
   <td><p>Öffnet das Formular im Bearbeitungsmodus.<br /> <br /> </p> </td>
  </tr>
    <tr>
   <td><p>Eigenschaften</p> </td>
   <td><p>Bietet Optionen zum Ändern der Eigenschaften des Formulars.<br /> <br /> </p> </td>
  </tr>
  <td><p>Kopieren</p> </td>
   <td><p> Bietet Optionen zum Kopieren des Formulars und Einfügen an der gewünschten Position. <br /> <br /> </p> </td>
  </tr>
   <tr>
   <td><p>Vorschau</p> </td>
   <td><p>Bietet Optionen zum Anzeigen einer Vorschau des Formulars als HTML oder zum Ausführen einer benutzerdefinierten Vorschau, indem Daten aus einer XML-Datei mit dem Formular zusammengeführt werden. <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Herunterladen</p> </td>
   <td><p>Lädt das ausgewählte Formular herunter.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Review starten/verwalten</p> </td>
   <td><p>Initiieren und Verwalten einer Überprüfung des ausgewählten Formulars.<br /> <br /> </p> </td>
  </tr>
  <!--<tr>
   <td><p>Add Dictionary</p> </td>
   <td><p>Generates a dictionary for localizing the selected fragment. For more information, see <a>Localizing Adaptive Forms</a>.<br /> <br /> </p> </td>
  </tr>-->
  <tr>
   <td><p>Veröffentlichen/Veröffentlichung rückgängig machen</p> </td>
   <td><p>Veröffentlicht das ausgewählte Formular bzw. hebt die Veröffentlichung auf<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Löschen</p> </td>
   <td><p>Löscht das ausgewählte Formular.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Vergleichen</p> </td>
   <td><p>Vergleicht zwei verschiedene Formulare zu Vorschauzwecken.<br /> <br /> </p> </td>
  </tr>
 </tbody>
</table>

## Fehlerbehebung

Haben Sie Probleme beim Laden Ihres Formulars? Im Folgenden finden Sie einige häufige Probleme und Lösungswege:

* **Formular-URL**: Vergewissern Sie sich, dass die URL Ihres Formulars nicht auf der Erweiterung „.html“ endet. Edge Deliver Service benötigt diese Erweiterung nicht.

* **AEM Author-URL**: Stellen Sie sicher, dass die in der Datei `fstab.yaml` aufgeführte AEM Author-URL korrekt formatiert ist. Sie sollte die folgenden Details enthalten:

   * die korrekte verantwortliche GitHub-Person
   * den korrekten Repository-Namen
   * die spezifische Verzweigung, die Sie für Edge Delivery Services verwenden

<!-- * **JSON Display**: If you see only JSON data instead of the actual form, your form block might be outdated. You can update it to the latest version available on https://github.com/adobe-rnd/aem-boilerplate-forms.
-->

## Beginnen mit dem Erstellen von Formularen

{{universal-editor-see-also}}
