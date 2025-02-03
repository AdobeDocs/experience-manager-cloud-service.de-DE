---
title: Veröffentlichung von Formularen für Edge Delivery Services
description: Erfahren Sie, wie die Formularveröffentlichung mit Edge Delivery Services funktioniert und wie Sie AEM-Inhalte mit Edge Delivery Services veröffentlichen.
feature: Edge Delivery Services
role: User
hide: true
hidefromtoc: true
exl-id: b90c27e3-22ea-4b18-b16e-a5c5a0ed58b8
source-git-commit: 67384a9141ced3bf5be63c8489dd5c329a288056
workflow-type: ht
source-wordcount: '993'
ht-degree: 100%

---

# Veröffentlichung von Formularen für Edge Delivery Services

Dieser Artikel führt Sie durch den Prozess zur Veröffentlichung von Formularen in AEM-Edge Delivery Services.
Um Formulare in Edge Delivery Services zu veröffentlichen, müssen Sie zunächst eine Verbindung zwischen Ihrer AEM-Umgebung und Ihrem GitHub-Repository herstellen. Sobald die Verbindung hergestellt ist, können Sie die Formulare mit dem universellen Editor erstellen, der dem WYSIWYG-Ansatz (What You See Is What You Get) folgt, um ein nahtloses und konsistentes Anwendererlebnis mit Sites bereitzustellen.

## Voraussetzungen

* Adaptive Formulare sind etwas Neues für Sie? Richten Sie ein GitHub-Repository anhand dieses [Tutorials](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project) ein.
* Wenn Sie bereits Edge Delivery Services verwenden, fügen Sie Ihrem GitHub-Repository die neueste Version des [adaptiven Formularblocks](/help/edge/docs/forms/tutorial.md#) hinzu.
* Die AEM Forms-Autoreninstanz enthält eine Vorlage, die auf Edge Delivery Services basiert. Stellen Sie sicher, dass die [neueste Version der Kernkomponenten](https://github.com/adobe/aem-core-forms-components) in Ihrer Umgebung installiert ist.
* Halten Sie die URL Ihrer AEM Forms as a Cloud Service-Autoreninstanz und Ihres GitHub-Repositorys bereit.

## Veröffentlichen von Formularen für Edge Delivery Services

Um Formulare für Edge Delivery Services zu veröffentlichen, führen Sie die folgenden Schritte aus:

[1. Verknüpfen des GitHub-Repositorys mit der AEM-Instanz](#link-github-repository-to-aem-instance)

[2. Verknüpfen der AEM-Instanz mit dem GitHub-Repository](#link-aem-instance-to-github-repository)

### Verknüpfen des GitHub-Repositorys mit der AEM-Instanz

Um [Ihr Projekt im GitHub-Repository](/help/edge/docs/forms/tutorial.md) mit der AEM Forms-Autoreninstanz zu verknüpfen, führen Sie die folgenden Schritte aus:

1. Gehen Sie zu Ihrem GitHub-Repository, das Sie für Edge Delivery Services erstellt oder konfiguriert haben.
1. Öffnen Sie die Datei `fstab.yaml`, um sie zu bearbeiten.
1. Aktualisieren Sie die Datei `fstab.yaml` in Ihrem GitHub-Repository mit der URL Ihrer Instanz von AEM Forms as a Cloud Service.

   ```javascript
    mountpoints:
    /:
        url: [author-instance-url]/bin/franklin.delivery/[Github owner]/[Github Repository]/[Github branch] 
        type: "markup"
        suffix: ".html"
   ```

   Wenn Ihr Repository beispielsweise „aemcrosswalk“ heißt, sich unter dem Konto „wkndform“ befindet und Sie die Verzweigung „main“ verwenden, sieht die URL der Autoreninstanz wie folgt aus:

   ```
        mountpoints:
            /:
            url: https://author-p133911-e1313554.adobeaemcloud.com/bin/franklin.delivery/wkndform/aemcrosswalk/main
            type: "markup"
            suffix: ".html"
   ```

1. Übergeben Sie die Änderungen an die Datei `fstab.yaml`.

### Verknüpfen der AEM-Instanz mit dem GitHub-Repository

Um die AEM Forms-Autoreninstanz mit [Ihrem Projekt im GitHub-Repository](/help/edge/docs/forms/tutorial.md) zu verknüpfen, führen Sie die folgenden Schritte aus:

[1. Erstellen eines adaptiven Formulars auf Basis der Edge Delivery Services-Vorlage](#1-create-an-adaptive-form-based-on-the-edge-delivery-services-template)

[2. Suchen des Konfigurations-Containers Ihres Formulars in der AEM-Autoreninstanz](#2-locate-your-forms-configuration-container-in-aem-author-instance)

[3. Erstellen des Formulars im universellen Editor](#3-author-the-form-in-the-universal-editor)

[4. Veröffentlichen und Vorschau des Formulars](#4-publish-and-preview-the-form)

#### 1. Erstellen eines adaptiven Formulars auf Basis der Edge Delivery Services-Vorlage

1. Greifen Sie auf Ihre Autoreninstanz in AEM Forms as a Cloud Service zu.
1. Wählen Sie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** und dann **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptive Formulare]** aus. Der Assistent wird geöffnet. Wählen Sie auf der Registerkarte „Quelle“ eine auf Edge Delivery Services basierende Formularvorlage aus:

   ![Erstellen von EDS-Formularen](/help/edge/assets/create-eds-forms.png){width=50%, align-center}

1. Klicken Sie auf **[!UICONTROL Erstellen]**. Daraufhin wird der Assistent **Formular erstellen** angezeigt.
1. Geben Sie die **GitHub-URL** an. Wenn Ihr GitHub-Repository beispielsweise „aemcrosswalk“ heißt und sich unter dem Konto „wkndform“ befindet, lautet die URL wie folgt:
   `https://github.com/wkndform/aemcrosswalk`
1. Klicken Sie auf **[!UICONTROL Erstellen]**.

   ![Assistent „Formular erstellen“](/help/edge/assets/create-form-wizard.png){width=50%, align-center}

   Wenn Sie auf **[!UICONTROL Erstellen]** klicken, wird das Formular zwecks Erstellung im universellen Editor geöffnet.

   ![Erstellen des Formulars](/help/edge/assets/author-form.png){width=50%, align-center}

   >[!NOTE]
   >
   > Die Edge Delivery Services-Konfiguration für die Formulare, die auf Edge Delivery Services basieren, wird automatisch im Konfigurations-Container des jeweiligen Formulars erstellt.

#### 2. Suchen des Konfigurations-Containers Ihres Formulars in der AEM-Autoreninstanz

1. Navigieren Sie in Ihrer Autoreninstanz in AEM Forms as a Cloud Service- zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud-Services]** > **[!UICONTROL Edge Delivery Services-Konfiguration]**.
1. Wählen Sie den Ordner aus, der dem Namen des Formulars entspricht. Wenn das Formular beispielsweise „contact-us“ heißt, wählen Sie den Ordner `forms/contact-us` und dann die Konfiguration aus und veröffentlichen Sie die Konfiguration:

   ![Edge Delivery Services-Konfiguration](/help/forms/assets/aem-instance-eds-configuration.png){width=50%, align-center}

1. Klicken Sie auf **[!UICONTROL Eigenschaften]**, um die Konfiguration anzuzeigen.\
   ![Automatisch erstellte Konfiguration](/help/edge/assets/aem-forms-create-configuration-github.png){width=50%, align-center}

   Sie können die Edge-Host-Option belassen, wie sie ist. Das Formular wird in der Vorschau-Umgebung (.page) und in der Live-Umgebung (.live) veröffentlicht.

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**. Die Konfiguration wird gespeichert.

#### 3. Erstellen des Formulars im universellen Editor

Wenn Sie auf **[!UICONTROL Erstellen]** klicken, wird das Formular im universellen Editor zwecks Erstellung geöffnet.

1. Öffnen Sie den Inhalts-Browser und navigieren Sie in der **Inhaltsstruktur** zur Komponente **[!UICONTROL Adaptives Formular]**.

   ![Inhaltsstruktur](/help/edge/assets/content-tree.png){width=50%, align-center}

1. Klicken Sie auf das Symbol **[!UICONTROL Hinzufügen]** und fügen Sie die gewünschten Komponenten aus der Liste der **adaptiven Formularkomponenten** hinzu.

   ![Hinzufügen einer Komponente](/help/edge/assets/add-component.png){width=50%, align-center}

1. Wählen Sie die hinzugefügte adaptive Formularkomponente aus und aktualisieren Sie ihre Eigenschaften mithilfe von **[!UICONTROL Eigenschaften]**.

   ![Öffnen von Eigenschaften](/help/edge/assets/component-properties.png){width=50%, align-center}

   Im folgenden Screenshot sehen Sie das einfache Kontaktformular, das im universellen Editor erstellt wurde:

   ![Kontaktformular](/help/edge/assets/contact-us.png){width=50%, align-center}

#### 4. Veröffentlichen und Vorschau des Formulars

Veröffentlichen Sie das Formular nun in Edge Delivery Services, indem Sie oben rechts im universellen Editor auf die Schaltfläche **[!UICONTROL Veröffentlichen]** klicken.

![Veröffentlichen des Formulars](/help/edge/assets/publish-form.png){width=50%, align-center}


So greifen Sie auf das Formular in Edge Delivery Services zu:

* **Staging-Version (für Tests)**: Die Staging-Version zeigt die unveröffentlichte, funktionierende Version des Formulars zu Testzwecken an. Verwenden Sie das folgende URL-Format, um eine Vorschau des Formulars anzuzeigen, bevor es live geschaltet wird:

  `https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>`

  Wenn das Repository Ihres Projekts beispielsweise „aemcrosswalk“ heißt, sich unter dem Konto „wkndform“ befindet und Sie die Verzweigung „main“ sowie das Formular „contact-us“ verwenden, sieht die URL der Staging-Version wie folgt aus:
https://main--aemcrosswalk--wkndform.aem.page/content/forms/af/contact-us

* **Live-Version (veröffentlichtes Formular)**: Die Live-Version zeigt die zuletzt veröffentlichte Version des Formulars an, auf die Endbenutzende zugreifen können. Verwenden Sie das folgende URL-Format, um auf die veröffentlichte Live-Version des Formulars zuzugreifen:

  `https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>`

  Wenn das Repository Ihres Projekts beispielsweise „aemcrosswalk“ heißt, sich unter dem Konto „wkndform“ befindet und Sie die Verzweigung „main“ sowie das Formular „contact-us“ verwenden, sieht die URL der Live-Version wie folgt aus:
https://main--aemcrosswalk--wkndform.aem.live/content/forms/af/contact-us

Die URL-Struktur bleibt für Staging- und Live-Versionen gleich. Der angezeigte Inhalt unterscheidet sich jedoch je nach Kontext:

![Anzeigen des veröffentlichten Formulars](/help/edge/assets/eds-view-publish-form.png){width=50%, align-center}

## Fehlerbehebung

Haben Sie Probleme beim Laden Ihres Formulars? Im Folgenden finden Sie einige häufige Probleme und Lösungswege:

* **Formular-URL**: Vergewissern Sie sich, dass die URL Ihres Formulars nicht auf der Erweiterung „.html“ endet. Edge Deliver Service benötigt diese Erweiterung nicht.

* **AEM Author-URL**: Stellen Sie sicher, dass die in der Datei `fstab.yaml` aufgeführte AEM Author-URL korrekt formatiert ist. Sie sollte die folgenden Details enthalten:

   * die korrekte verantwortliche GitHub-Person
   * den korrekten Repository-Namen
   * die spezifische Verzweigung, die Sie für Edge Delivery Services verwenden

<!-- * **JSON Display**: If you see only JSON data instead of the actual form, your form block might be outdated. You can update it to the latest version available on https://github.com/adobe-rnd/aem-boilerplate-forms.
-->

## Siehe auch

{{see-more-forms-eds}}
