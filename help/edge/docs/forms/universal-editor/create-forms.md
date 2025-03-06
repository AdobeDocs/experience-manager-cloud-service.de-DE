---
title: Erstellen einer eigenständigen adaptiven Forms mit dem universellen Editor
description: In diesem Artikel wird erläutert, wie Sie adaptive Forms mit dem Assistenten zur Formularerstellung in der AEM-Autoreninstanz erstellen und Formulare in AEM Edge Delivery Services veröffentlichen.
feature: Edge Delivery Services
role: User
hide: true
hidefromtoc: true
exl-id: 1eab3a3d-5726-4ff8-90b9-947026c17e22
source-git-commit: 9127c58a72dc4942312907f9e8f0cdcc8de9aa4b
workflow-type: tm+mt
source-wordcount: '1016'
ht-degree: 49%

---

# Erstellen eigenständiger Formulare mit dem universellen Editor (WYSIWYG)

<span class="preview"> Diese Funktion ist über das Early-Access-Programm verfügbar. Um den Zugriff anzufordern, senden Sie eine E-Mail mit dem Namen Ihrer GitHub-Organisation und dem Repository-Namen von Ihrer offiziellen Adresse an <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a> . Wenn die Repository-URL beispielsweise https://github.com/adobe/abc lautet, lautet der Organisationsname adobe und der Repository-Name abc.</span>

Dieser Artikel führt Sie durch den Prozess des Verfassens der eigenständigen Formulare mit dem universellen Editor, indem Sie eine Edge Delivery Services-basierte Vorlage aus dem Assistenten zur Formularerstellung auswählen. Sie können die erstellten Formulare auch mit dem universellen Editor in AEM Edge Delivery Services veröffentlichen.

<!--To publish forms to Edge Delivery Services, you must first establish a connection between your AEM environment and your GitHub repository. Once connected, you can author the forms using the Universal Editor, which follows a WYSIWYG (What You See Is What You Get) approach for a seamless and consistent user experience with Sites.-->

Bevor Sie beginnen, erfahren Sie mehr über die Arten der Formular-Komponenten, die Ihnen zur Verfügung stehen:

* [Edge Delivery Services für AEM Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) ist ein zusammenstellbarer Satz von Services, der eine schnelle Entwicklungsumgebung ermöglicht, in der Autoren neue Formulare schnell mit dem universellen Editor aktualisieren, veröffentlichen und starten können. Der universelle Editor vereinfacht die Formularerstellung für Adobe Edge Delivery Services mit einer benutzerfreundlichen, visuellen WYSIWYG-Oberfläche.

* [Kernkomponenten adaptiver Formulare](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de): Dies sind standardisierte Datenerfassungskomponenten. Diese Komponenten bieten Anpassungsfunktionen, kürzere Entwicklungszeiten und niedrigere Wartungskosten für Ihre Erlebnisse bei der digitalen Registrierung. Entwickelnde können diese Komponenten einfach anpassen und gestalten. Sie können unter [https://aemcomponents.dev/](https://aemcomponents.dev/) die verfügbaren Kernkomponenten in Aktion anzeigen **Adobe empfiehlt die Verwendung dieser modernen und erweiterbaren Komponenten zur Entwicklung von adaptiven Formularen**.

* [Foundation-Komponenten adaptiver Formulare](/help/forms/creating-adaptive-form.md): Hierbei handelt es sich um klassische (alte) Datenerfassungskomponenten. Sie können diese weiterhin verwenden, um Ihre vorhandenen Foundation-Komponenten auf Grundlage des adaptiven Formulars zu bearbeiten. Wenn Sie neue Formulare erstellen, empfiehlt Adobe die Verwendung von  [Kernkomponenten von adaptiven Formularen, um ein adaptives Formular zu erstellen](#create-an-adaptive-form-core-components).

AEM Forms umfasst einen Block, der als adaptiver Formularblock bezeichnet wird und mit dem Sie mühelos Edge Delivery Services-Formulare erstellen können, um Daten zu erfassen und zu speichern. Sie können [ein neues AEM-Projekt erstellen, das mit dem adaptiven Forms-Block vorkonfiguriert ist](#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) oder [den adaptiven Forms-Block zu einem vorhandenen AEM Site-Projekt hinzufügen](#add-adaptive-forms-block-to-your-existing-aem-project).

![GitHub-Repository-Workflow](/help/edge/assets/repo-workflow.png)

## Voraussetzungen

* [Richten Sie Ihr GitHub-Repository ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template), um eine Verbindung zwischen Ihrer AEM-Umgebung und dem GitHub-Repository herzustellen.
* Wenn Sie bereits Edge Delivery Services verwenden, fügen Sie Ihrem GitHub-Repository die neueste Version des [adaptiven Formularblocks](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) hinzu.
* Die AEM Forms-Autoreninstanz enthält eine Vorlage, die auf Edge Delivery Services basiert. Stellen Sie sicher, dass die [neueste Version der Kernkomponenten](https://github.com/adobe/aem-core-forms-components) in Ihrer Umgebung installiert ist.
* Halten Sie die URL Ihrer AEM Forms as a Cloud Service-Autoreninstanz und Ihres GitHub-Repositorys bereit.

## Erstellen eines adaptiven Formulars mit dem universellen Editor

Mit dem universellen Editor können Sie einfach responsive und interaktive eigenständige Formulare erstellen, indem Sie vorgefertigte Komponenten wie Textfelder, Kontrollkästchen und Optionsfelder verwenden. Es bietet leistungsstarke Funktionen wie dynamische Regeln, reibungslose Datenintegration und Anpassungsoptionen, mit denen Sie Formulare entsprechend Ihren genauen Anforderungen erstellen können.

>[!NOTE]
>
> Sie können ein [ in AEM Site auch mithilfe der Edge Delivery Services Site-Vorlage im universellen Editor erstellen und es in Edge Delivery Services veröffentlichen](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project).

Um ein eigenständiges adaptives Formular mit dem universellen Editor zu erstellen, führen Sie die folgenden Schritte aus:

1. **Erstellen eines adaptiven Formulars auf der AEM Forms-Autoreninstanz**

   1. Greifen Sie auf Ihre Autoreninstanz in AEM Forms as a Cloud Service zu.
   1. Wählen Sie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** und dann **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptive Formulare]** aus. Der Assistent wird geöffnet.
   1. Wählen Sie auf der Registerkarte {**}Source eine Edge Delivery Services-basierte Formularvorlage aus:**

      ![EDS-Forms erstellen](/help/edge/assets/create-eds-forms.png)

   1. Klicken Sie auf **[!UICONTROL Erstellen]**. Daraufhin wird der Assistent **Formular erstellen** angezeigt.
   1. Geben Sie die **GitHub-URL** an. Wenn sich Ihr GitHub-Repository beispielsweise `edsforms` heißt und sich unter der `wkndforms` befindet, lautet die URL:
      `https://github.com/wkndforms/edsforms`
   1. Klicken Sie auf **[!UICONTROL Erstellen]**.

      ![Assistent für die Formularerstellung](/help/edge/assets/create-form-wizard.png)

      Wenn Sie auf **[!UICONTROL Erstellen]** klicken, wird das Formular zwecks Erstellung im universellen Editor geöffnet.

      ![Formular erstellen](/help/edge/assets/author-form.png)

      <!-- >[!NOTE]
        >
        > The Edge Delivery Services configuration for the forms based on Edge Delivery Services template is created automatically at the form's configuration container.-->

      Wenn Sie auf **[!UICONTROL Erstellen]** klicken, wird das Formular im universellen Editor zwecks Erstellung geöffnet.

1. **Erstellen Sie das Formular im universellen Editor**

   1. Öffnen Sie den Inhalts-Browser und navigieren Sie in der **Inhaltsstruktur** zur Komponente **[!UICONTROL Adaptives Formular]**.

      ![Inhaltsstruktur](/help/edge/assets/content-tree.png)

   1. Klicken Sie auf das Symbol **[!UICONTROL Hinzufügen]** und fügen Sie die gewünschten Komponenten aus der Liste der **adaptiven Formularkomponenten** hinzu.

      ![Hinzufügen der Komponente](/help/edge/assets/add-component.png)

   1. Wählen Sie die hinzugefügte adaptive Formularkomponente aus und aktualisieren Sie ihre Eigenschaften mithilfe von **[!UICONTROL Eigenschaften]**.

      ![Öffnen von Eigenschaften](/help/edge/assets/component-properties.png)

      Im folgenden Screenshot sehen Sie das einfache `Registration Form` Formular, das im universellen Editor verfasst wurde:

      ![Kontaktformular](/help/edge/assets/contact-us.png)

      Jetzt können Sie [Übermittlungsaktionen für Formulare konfigurieren und anpassen](/help/edge/docs/forms/universal-editor/submit-action.md).


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

## Formular veröffentlichen

Veröffentlichen Sie nun das eigenständige Formular in Edge Delivery Services, indem Sie auf die Schaltfläche **[!UICONTROL Veröffentlichen]** oben rechts im universellen Editor klicken.

![Veröffentlichen des Formulars](/help/edge/assets/publish-form.png)

>[!NOTE]
>
> Informationen zum Veröffentlichen eines [ in Edge Delivery Services finden ](/help/edge/docs/forms/universal-editor/publish-forms.md) im Artikel Veröffentlichen und Bereitstellen von Formularen .

So greifen Sie auf das Formular in Edge Delivery Services zu:

* **Staging-Version (für Tests)**: Die Staging-Version zeigt die unveröffentlichte, funktionierende Version des Formulars zu Testzwecken an. Verwenden Sie das folgende URL-Format, um eine Vorschau des Formulars anzuzeigen, bevor es live geschaltet wird:

  `https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>`

  Wenn das Repository Ihres Projekts beispielsweise „deforms“ heißt, es sich unter dem Konto „wkforms“ befindet und Sie die „Haupt“-Verzweigung und das Formular als „Registrierungsformular“ verwenden, sieht die URL der Staging-Version wie folgt aus:
  `https://main--edsforms--wkndforms.aem.page/content/forms/af/registration-form`

* **Live-Version (veröffentlichtes Formular)**: Die Live-Version zeigt die zuletzt veröffentlichte Version des Formulars an, auf die Endbenutzende zugreifen können. Verwenden Sie das folgende URL-Format, um auf die veröffentlichte Live-Version des Formulars zuzugreifen:

  `https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>`

  Wenn das Repository Ihres Projekts beispielsweise „deforms“ heißt, es sich unter dem Konto „wkforms“ befindet und Sie die „Haupt“-Verzweigung und das Formular als „Registrierungsformular“ verwenden, sieht die URL der Staging-Version wie folgt aus:
  `https://main--edsforms--wkndforms.aem.live/content/forms/af/registration-form`

Die URL-Struktur bleibt für Staging- und Live-Versionen gleich. Der angezeigte Inhalt unterscheidet sich jedoch je nach Kontext:

![Veröffentlichtes Formular anzeigen](/help/edge/assets/eds-view-publish-form.png)

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
