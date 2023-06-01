---
title: Erstellen oder Hinzufügen eines adaptiven Formulars zur AEM Sites-Seite
description: Erfahren Sie, wie Sie mühelos ein adaptives Formular erstellen oder nahtlos zu Ihrer AEM Sites-Seite hinzufügen können. Lernen Sie schrittweise Techniken und Best Practices für die Integration dynamischer und anpassbarer Formulare in Ihre Website kennen, um Ihre digitalen Erlebnisse für eine maximale Wirkung zu optimieren.
feature: Adaptive Forms
hide: true
hidefromtoc: true
source-git-commit: 7dc36220c1f12177037aaa79d864c1ec2209a301
workflow-type: tm+mt
source-wordcount: '1230'
ht-degree: 0%

---


# Erstellen oder Hinzufügen eines adaptiven Formulars zur AEM Sites-Seite {#create-or-add-an-adaptive-form-to-aem-sites-page}

Mit AEM Forms können Sie adaptive Formulare nahtlos in Ihre Webseiten integrieren. Dadurch können Ihre Besucher bequem Formulare ausfüllen und senden, ohne jemals die Seite verlassen zu müssen, auf der sie sich befinden. Dadurch können sie mühelos mit anderen Elementen der Website interagieren und gleichzeitig aktiv mit dem Formular interagieren.

Sie können diese Funktion voll nutzen, indem Sie die folgenden Optionen verwenden:

* **Fügen Sie ein benutzerdefiniertes Formular hinzu:** Erstellen Sie ein ganz neues Formular, passen Sie es speziell an Ihre Anforderungen und Designvorlieben an.

* **Experience Fragments verbessern:** Erweitern Sie die Reichweite Ihrer Formulare, indem Sie sie zu AEM Experience Fragments hinzufügen, sodass sie nahtlos über mehrere Seiten oder Sites hinweg wiederverwendet werden können.

* **Verwenden Sie genehmigte Vorlagen:** Nutzen Sie vorab genehmigte Vorlagen, um schnell Formulare zu erstellen, die den Branding-Richtlinien und Designstandards Ihres Unternehmens entsprechen.

* **Hinzufügen vorhandener Formulare:** Einfache Integration von bereits erstellten Formularen in Ihre Websites, sodass Besucher direkt mit ihnen interagieren können.

* **Mehrere Formulare hinzufügen:**  Fügen Sie einer Seite mehrere Formulare hinzu, um Benutzern basierend auf ihren Voreinstellungen und Anforderungen mehrere Optionen zur Verfügung zu stellen. Diese können eine Kombination aus neuen und vorhandenen Formularen darstellen.

Mit dem AEM Sites-Editor können Sie schnell mehrere Formulare erstellen und zu Ihren AEM Sites-Seiten hinzufügen. Mithilfe des AEM Sites-Editors können Inhaltsautoren nahtlose Erlebnisse zur Datenerfassung innerhalb einer Sites-Seite erstellen, indem sie die Leistung adaptiver Formularkomponenten nutzen, einschließlich dynamischer Verhaltensweisen, Überprüfungen, Datenintegration, Generierung von Datensatzdokumenten und Automatisierung von Geschäftsprozessen. Außerdem können Sie damit verschiedene Funktionen von AEM Sites-Seiten verwenden, z. B. Versionierung, Targeting, Übersetzung und Multi-Site-Manager.

## Ziel

* Erfahren Sie, wie Sie ein adaptives Formular mit dem AEM Sites-Editor und Experience Fragment erstellen
* Erfahren Sie, wie Sie das Layout und Design für ein adaptives Formular festlegen, das zu einer AEM Sites-Seite hinzugefügt wird, und
* Erstellen eines adaptiven Formulars mit dem AEM Sites-Editor und Experience Fragment


## Überlegungen {#consideration}

AEM Forms bietet Container für adaptive Formulare und Komponenten für adaptive Forms - Einbetten. Sie können den Container für adaptive Formulare verwenden, um ein neues Formular in einem Experience Fragment oder einer AEM Sites-Seite zu erstellen und hinzuzufügen, während Sie mit der Komponente Adaptive Forms - Embed ein vorhandenes adaptives Formular hinzufügen oder ein neues Formular mit dem Adaptive Forms-Editor erstellen können.

Wenn Sie den Container für adaptive Formulare verwenden, um ein Formular zu erstellen oder hinzuzufügen, werden die Formulare über den AEM Sites-Übersetzungsfluss übersetzt und lokalisiert. Für jede Sprache wird eine separate Kopie (Sprachkopie) der Siteseite und der entsprechenden Formulare generiert. Wenn ein Inhaltsautor eine Regel in einem Formular auf der übergeordneten Seite ändert, müssen dieselben Änderungen in allen Sprachkopien des Formulars vorgenommen werden. Mit dem Container für adaptive Formulare können Sie auch verschiedene Funktionen von AEM Sites-Seiten verwenden, z. B. Versionierung, Targeting, Übersetzung und Multi-Site-Manager.

Wenn Sie ein Formular mithilfe der Einbettungskomponente für adaptive Formulare erstellen oder hinzufügen, werden die Formulare mithilfe des AEM Forms-Übersetzungsflusses übersetzt und lokalisiert. In diesem Fall wird ein einzelnes Formular beibehalten und in allen Sprachkopien der Sites-Seiten referenziert. Die Einbettungskomponente für adaptive Formulare bietet keinen Zugriff auf verschiedene Funktionen von AEM Sites-Seiten wie Versionierung, Targeting, Übersetzung und Multi-Site-Manager.


## Bevor Sie beginnen {#before-you-start}

+++  Aktivieren der adaptiven Forms-Kernkomponenten für Ihre Umgebung

Stellen Sie sicher, dass [Adaptive Forms-Kernkomponenten sind für Ihre as a Cloud Service AEM Forms-Umgebung aktiviert](enable-adaptive-forms-core-components.md).

+++

+++ ** aktivieren[!UICONTROL Adaptiver Forms-Container]

Aktivieren [!UICONTROL Adaptiver Forms-Container] -Komponente in der Richtlinie der Vorlage ausführen, führen Sie die folgenden Schritte aus:

1. Öffnen Sie die AEM Sites-Seite zur Bearbeitung. Um die Seite zur Bearbeitung zu öffnen, wählen Sie die Seite aus und klicken Sie auf &quot;Bearbeiten&quot;.
1. Öffnen Sie die Vorlage Ihrer Sites-Seite. Um die Vorlage zu öffnen, navigieren Sie zum [!UICONTROL Seiteninformationen] ![Seiteninformationen](/help/forms/assets/Smock_Properties_18_N.svg) > [!UICONTROL Vorlage bearbeiten]. Die entsprechende Vorlage wird im Vorlageneditor geöffnet.
1. Klicken Sie in der Strukturansicht auf die **[!UICONTROL Politik]** ![Politik](/help/forms/assets/Smock_FeedManagement_18_N.svg) in der Menüleiste. Im **[!UICONTROL Zugelassene Komponenten]** und wählen Sie die **[!UICONTROL Adaptiver Forms-Container]**  Kontrollkästchen unter dem **[AEM Archetyp Projektname] - Adaptives Formular**.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

+++


+++  Adaptive Forms-Client-Bibliotheken zu Ihrer AEM Sites-Seite hinzufügen

Um die vollständige Funktionalität der Komponente Adaptiver Forms-Container zu aktivieren, fügen Sie die Client-Bibliotheken &quot;customHeaderlibs&quot;und &quot;customfooterlibs&quot;mithilfe der Bereitstellungs-Pipeline zu Ihrer AEM Sites-Seite hinzu. Hinzufügen der Bibliotheken:

1. Zugriff und Klonen Sie Ihre [AEM Cloud Service Git Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/repositories.html).
1. Öffnen Sie den Ordner AEM Cloud Service Git Repository in einem Texteditor für Pläne. Beispielsweise Microsoft Visual Code.
1. Öffnen Sie die `ui.apps/src/main/content/jcr_root/apps/[your-project]/components/page/.content.xml` Datei zur Bearbeitung und notieren Sie den Wert von `sling:resourceSuperType`. Notieren Sie beispielsweise den Wert `core/wcm/components/page/v3/page`.


   ![Sling-Ressource](/help/forms/assets/slingresource.png)

1. Navigieren Sie zu `  ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\` `ui.apps/src/main/content/jcr_root/apps` und erstellen Sie eine Ordnerstruktur, die mit dem im vorherigen Schritt angegebenen Wert identisch ist. Wenn der Wert beispielsweise dem Beispiel im vorherigen Schritt ähnelt, lautet die endgültige Knotenstruktur . `ui.apps/src/main/content/jcr_root/apps/core/wcm/components/page/v3/page`

   ![Überlagerungsstruktur](/help/forms/assets/overlaystructure.png)

1. Erstellen `customheaderlibs.html` und `customfooterlibs.html` -Dateien in der Knotenstruktur, die im vorherigen Schritt erstellt wurde, und fügen Sie den Dateien den folgenden Inhalt hinzu:

   ```
        //Customheaderlibs.html
        <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
        <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
        </sly> 
   
        //customfooterlibs.html
        <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
        <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
        </sly> 
   ```

1. [Ausführen der Bereitstellungspipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) , um die Client-Bibliotheken in Ihrer AEM as a Cloud Service Umgebung bereitzustellen.

+++

## Erstellen eines adaptiven Formulars {#create-an-adaptive-form-in-sites-editor-or-experience-fragment}

Sie können ein brandneues Formular von Grund auf neu erstellen und es speziell an Ihre Anforderungen und Designvoreinstellungen anpassen, und zwar direkt auf einer AEM Site-Seite oder im Experience Fragment. Bei Formularen mit nur einer Verwendungsmöglichkeit wird empfohlen, eine Site-Seite mit AEM direkt zu erstellen, während Experience Fragments sich ideal für Formulare eignen, die auf mehreren Seiten auf Ihrer Website wiederverwendet werden müssen.

* [Erstellen eines Formulars auf einer AEM Sites-Seite](#create-an-adaptive-form-in-sites-editor)
* [Erstellen eines Formulars in einem Experience Fragment](#create-an-adaptive-form-in-experience-fragment)

### Erstellen eines Formulars auf einer AEM Sites-Seite {#create-an-adaptive-form-in-sites-editor}

Sie können die Komponente Container für adaptive Formulare im AEM Sites-Editor verwenden, um ein benutzerdefiniertes Formular zu erstellen. Mit der Komponente können Sie ein Formular erstellen, indem Sie die Formularkomponenten per Drag &amp; Drop verschieben. Die Formularkomponenten basieren auf Kernkomponenten. Sie können diese einfach entsprechend den Anforderungen Ihrer Organisation anpassen.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

So erstellen Sie ein adaptives Formular auf einer Siteseite:

1. Öffnen Sie die AEM Sites-Seite im Bearbeitungsmodus.
1. Ziehen Sie die **[!UICONTROL Adaptiver Forms-Container]** -Komponente vom Komponenten-Browser zur Seite &quot;Sites&quot;hinzugefügt. Dadurch wird ein Leerzeichen auf der Seite für das Formular erstellt. Sie können den Layout-Modus verwenden, um die Größe des Containerraums zu ändern.
1. Ziehen Sie Kernkomponenten des adaptiven Formulars per Drag-and-Drop in den Container-Bereich, um das Formular zu erstellen.
1. Fügen Sie die Senden -Schaltfläche hinzu.

Als Nächstes legen Sie die Übermittlungsaktion und erweiterte Eigenschaften fest.

### Erstellen eines Formulars in einem Experience Fragment {#create-an-adaptive-form-in-experience-fragment}

Sie können die Reichweite Ihrer Formulare erweitern, indem Sie sie zu AEM Experience Fragments hinzufügen, wodurch eine nahtlose Wiederverwendung über mehrere Seiten oder Sites hinweg ermöglicht wird. Sie können beispielsweise ein Newsletter-Anmeldeformular in ein Experience Fragment einfügen. Dadurch können Sie das Fragment bequem über mehrere Seiten Ihrer Website hinweg wiederverwenden, sodass das Formular nicht wiederholt neu erstellt werden muss. Alle Aktualisierungen oder Änderungen, die im Experience Fragment am Newsletter-Anmeldeformular vorgenommen werden, werden automatisch auf alle Seiten übertragen, auf denen es verwendet wird. Dadurch wird der Prozess optimiert und ein nahtloses Benutzererlebnis bei gleichzeitiger Vereinfachung der Verwaltung von Formularen auf Ihrer Website sichergestellt.

So erstellen Sie ein adaptives Formular in einem Experience Fragment:

## Layout eines adaptiven Formulars ändern {#change-layout-of-an-adaptive-form}

Verwenden Sie auf der AEM Sites-Seite die [Layout-Modus](/help/sites-cloud/authoring/features/responsive-layout.md) , um die Größe einer Container-Komponente für adaptive Formulare zu ändern, die zu einer AEM Sites-Seite hinzugefügt wurde.
