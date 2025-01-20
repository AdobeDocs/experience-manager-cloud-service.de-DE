---
title: Veröffentlichen von Forms für Edge Delivery Services
description: Erfahren Sie, wie die Veröffentlichung von Formularen mit Edge Delivery Services funktioniert und wie Sie AEM-Formulare mit Edge Delivery Services veröffentlichen.
feature: Edge Delivery Services
role: User
hide: true
hidefromtoc: true
source-git-commit: bdc0e51a8b16df432f1f1aeabed11135fb8c8e0c
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 1%

---


# Veröffentlichen von Forms für Edge Delivery Services

Dieser Artikel führt Sie durch den Prozess der Veröffentlichung von Formularen in AEM-Edge Delivery Services.
Um Formulare auf Edge Delivery Services zu veröffentlichen, müssen Sie zunächst eine Verbindung zwischen Ihrer AEM-Umgebung und Ihrem GitHub-Repository herstellen. Sobald die Verbindung hergestellt ist, können Sie die Formulare mit dem universellen Editor erstellen, der einem Ansatz von WYSIWYG (What You See Is What You Get) folgt, um ein nahtloses und konsistentes Benutzererlebnis mit Sites zu gewährleisten.

## Voraussetzungen

* Neu bei Adaptive Forms? Richten Sie Ihr GitHub-Repository gemäß dem bereitgestellten [ ein](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project).
* Wenn Sie bereits Edge Delivery Services verwenden, fügen Sie die neueste Version des [Adaptive Forms-Blocks](/help/edge/docs/forms/tutorial.md#) zu Ihrem GitHub-Repository hinzu.
* Die AEM Forms-Autoreninstanz enthält eine Vorlage, die auf Edge Delivery Services basiert. Stellen Sie sicher[ dass die neueste Version der ](https://github.com/adobe/aem-core-forms-components) in Ihrer Umgebung installiert ist.
* Halten Sie die URL Ihrer AEM Forms as a Cloud Service-Autoreninstanz und Ihres GitHub-Repositorys bereit.

## Publish Forms für Edge Delivery Services

Gehen Sie wie folgt vor, um Formulare für Edge Delivery Services zu veröffentlichen:

[1. Verknüpfen des GitHub-Repositorys mit der AEM-Instanz](#link-github-repository-to-aem-instance)

[2. AEM-Instanz mit GitHub-Repository verknüpfen](#link-aem-instance-to-github-repository)

### GitHub-Repository mit AEM-Instanz verknüpfen

Um [Ihr Projekt im GitHub-Repository](/help/edge/docs/forms/tutorial.md) mit der AEM Forms-Autoreninstanz zu verknüpfen, führen Sie die folgenden Schritte aus:

1. Gehen Sie zu Ihrem GitHub-Repository, das Sie für Ihre Edge Delivery Services erstellt oder konfiguriert haben.
1. Öffnen Sie die Datei `fstab.yaml`, um sie zu bearbeiten.
1. Aktualisieren Sie die `fstab.yaml`-Datei in Ihrem GitHub-Repository mit der URL Ihrer AEM Forms as a Cloud Service-Instanz.

   ```javascript
    mountpoints:
    /:
        url: [author-instance-url]/bin/franklin.delivery/[Github owner]/[Github Repository]/[Github branch] 
        type: "markup"
        suffix: ".html"
   ```

   Wenn Ihr GitHub-Repository beispielsweise „aemcrosswalk“ heißt, es sich unter dem Konto „wkndForm“ befindet und Sie die „Haupt“-Verzweigung verwenden, sieht die URL der Autoreninstanz wie folgt aus:

   ```
        mountpoints:
            /:
            url: https://author-p133911-e1313554.adobeaemcloud.com/bin/franklin.delivery/wkndform/aemcrosswalk/main
            type: "markup"
            suffix: ".html"
   ```

1. Übertragen Sie die Änderungen in die `fstab.yaml`.

### AEM-Instanz mit GitHub-Repository verknüpfen

Um die AEM Forms-Autoreninstanz mit [Ihrem Projekt im GitHub-Repository](/help/edge/docs/forms/tutorial.md) zu verknüpfen, führen Sie die folgenden Schritte aus:

[1. Erstellen eines adaptiven Formulars basierend auf der Edge Delivery Services-Vorlage](#1-create-an-adaptive-form-based-on-the-edge-delivery-services-template)

[2. Suchen Sie den Konfigurations-Container Ihres Formulars in der AEM-Autoreninstanz](#2-locate-your-forms-configuration-container-in-aem-author-instance)

[3. Erstellen Sie das Formular im universellen Editor](#3-author-the-form-in-the-universal-editor)

[4. Publish und Vorschau des Formulars](#4-publish-and-preview-the-form)

#### 1. Erstellen eines adaptiven Formulars basierend auf der Edge Delivery Services-Vorlage

1. Greifen Sie auf Ihre AEM Forms as a Cloud Service-Autoreninstanz zu.
1. Wählen Sie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms und Dokumente]**.1. Wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptive Forms]**. Der Assistent wird geöffnet. Wählen Sie auf der Registerkarte Source eine Edge Delivery Services-basierte Formularvorlage aus:

   ![EDS-Forms erstellen](/help/edge/assets/create-eds-forms.png){width=50%, align-center}

1. Klicken Sie **[!UICONTROL Erstellen]** und der Assistent **Formular erstellen** wird angezeigt.
1. Geben Sie die **GitHub-URL** an. Wenn Ihr GitHub-Repository beispielsweise „aemcrosswalk“ heißt und sich unter dem Konto „wkndForm“ befindet, lautet die URL:
   `https://github.com/wkndform/aemcrosswalk`
1. Klicken Sie auf **[!UICONTROL Erstellen]**.

   ![Assistent zum Erstellen von Formularen](/help/edge/assets/create-form-wizard.png){width=50%, align-center}

   Sobald Sie auf **[!UICONTROL Erstellen]** klicken, wird das Formular im universellen Editor für das Authoring geöffnet.

   ![Formular erstellen](/help/edge/assets/author-form.png){width=50%, align-center}

   >[!NOTE]
   >
   > Die Edge Delivery Services-Konfiguration für die Forms-Vorlage, die auf Edge Delivery Services basiert, wird automatisch im Konfigurations-Container des Formulars erstellt.

#### 2. Suchen Sie den Konfigurations-Container Ihres Formulars in der AEM-Autoreninstanz

1. Navigieren Sie **[!UICONTROL Ihrer AEM Forms]** as a Cloud Service-Autoreninstanz zu ]**Tools]** > **[!UICONTROL Cloud Service >**[!UICONTROL  Edge Delivery Services-.
1. Wählen Sie den Ordner aus, der dem Namen des Formulars entspricht. Wenn Ihr Formular beispielsweise „contact-us“ heißt, wählen Sie den `forms/contact-us` aus, wählen Sie die Konfiguration aus und veröffentlichen Sie die Konfiguration:

   ![Edge Delivery Services-Konfiguration](/help/forms/assets/aem-instance-eds-configuration.png){width=50%, align-center}

1. Klicken Sie **[!UICONTROL Eigenschaften]**, um die Konfiguration anzuzeigen.\
   ![Automatisch erstellte Konfiguration](/help/edge/assets/aem-forms-create-configuration-github.png){width=50%, align-center}

   Sie können die Edge-Host-Option so lassen, wie sie ist. Das Formular wird in der Vorschau-Umgebung (.page) und in der Live-Umgebung (.live) veröffentlicht.

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**. Die Konfiguration wird gespeichert.

#### 3. Erstellen Sie das Formular im universellen Editor

Wenn Sie auf **[!UICONTROL Erstellen]** klicken, wird das Formular im universellen Editor für das Authoring geöffnet.

1. Öffnen Sie den Inhaltsbrowser und navigieren Sie zur Komponente **[!UICONTROL adaptives Formular]** in der **Inhaltsstruktur**.

   ![Inhaltsstruktur](/help/edge/assets/content-tree.png){width=50%, align-center}

1. Klicken Sie auf **[!UICONTROL Hinzufügen]** und fügen Sie die gewünschten Komponenten aus der Liste **Adaptive Formularkomponenten** hinzu.

   ![Komponente hinzufügen](/help/edge/assets/add-component.png){width=50%, align-center}

1. Wählen Sie die hinzugefügte Komponente des adaptiven Formulars aus und aktualisieren Sie ihre Eigenschaften mithilfe von **[!UICONTROL Eigenschaften]**.

   ![Eigenschaften öffnen](/help/edge/assets/component-properties.png){width=50%, align-center}

   Im folgenden Screenshot sehen Sie das einfache Formular „Contact Us“, das im universellen Editor verfasst wurde:

   ![Formular für Kontakt](/help/edge/assets/contact-us.png){width=50%, align-center}

#### 4. Publish und Vorschau des Formulars

Veröffentlichen Sie das Formular jetzt in Edge Delivery Services, indem Sie auf die Schaltfläche **[!UICONTROL Publish]** oben rechts im universellen Editor klicken.

![Formular veröffentlichen](/help/edge/assets/publish-form.png){width=50%, align-center}


So greifen Sie auf das Formular in Edge Delivery Services zu:

* **Staging-Version (für Tests)**: Die Staging-Version zeigt zu Testzwecken die unveröffentlichte, funktionierende Version des Formulars an. Verwenden Sie das folgende URL-Format, um eine Vorschau des Formulars anzuzeigen, bevor es live geschaltet wird:

  `https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>`

  Wenn sich beispielsweise das Repository Ihres Projekts namens „aemcrosswalk“ unter dem Konto „wkndForm“ befindet und Sie die Verzweigung „main“ und das Formular als „Contact us“ verwenden, sieht die URL der Staging-Version wie folgt aus:
https://main--aemcrosswalk--wkndform.aem.page/content/forms/af/contact-us

* **Live-Version (veröffentlichtes Formular)**:   Die Live-Version zeigt die zuletzt veröffentlichte Version des Formulars an, auf die Endbenutzer zugreifen können. Verwenden Sie das folgende URL-Format, um auf die veröffentlichte Live-Version des Formulars zuzugreifen:

  `https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>`

  Wenn sich beispielsweise das Repository Ihres Projekts namens „aemcrosswalk“ unter dem Konto „wkndForm“ befindet und Sie die Verzweigung „main“ und das Formular als „Contact us“ verwenden, sieht die URL der Staging-Version wie folgt aus:
https://main--aemcrosswalk--wkndform.aem.live/content/forms/af/contact-us

Die URL-Struktur bleibt für Staging- und Live-Versionen gleich. Der angezeigte Inhalt unterscheidet sich jedoch je nach Kontext:

![Veröffentlichtes Formular anzeigen](/help/edge/assets/eds-view-publish-form.png){width=50%, align-center}

## Fehlerbehebung

Haben Sie Probleme beim Laden Ihres Formulars? Im Folgenden finden Sie einige häufige Probleme und deren Behebung:

* **Formular-URL**: Vergewissern Sie sich, dass die URL Ihres Formulars am Ende nicht die Erweiterung &quot;.html“ enthält. Edge Deliver Service benötigt diese Erweiterung nicht.

* **AEM-Autoren-URL**: Stellen Sie sicher, dass die in Ihrer `fstab.yaml` aufgeführte AEM-Autoren-URL korrekt formatiert ist. Sie sollte die folgenden Details enthalten:

   * Der richtige GitHub-Besitzer
   * Der richtige Repository-Name
   * Die spezifische Verzweigung, die Sie für Edge Delivery Services verwenden

<!-- * **JSON Display**: If you see only JSON data instead of the actual form, your form block might be outdated. You can update it to the latest version available on https://github.com/adobe-rnd/aem-boilerplate-forms.
-->

## Siehe auch

{{see-more-forms-eds}}