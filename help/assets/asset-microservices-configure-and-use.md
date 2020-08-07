---
title: Konfigurieren und Verwenden von Asset-Microservices für die Asset-Verarbeitung
description: Erfahren Sie, wie Sie die Cloud-nativen Asset-Microservices konfigurieren und verwenden, um Assets skaliert zu verarbeiten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 568e5d2906fe6c9415eebcab7e3e4e1fb4a738fa
workflow-type: tm+mt
source-wordcount: '2537'
ht-degree: 44%

---


# Asset-Mikrodienste und verarbeitende Profil verwenden {#get-started-using-asset-microservices}

<!--
* Current capabilities of asset microservices offered. If applications have names then list the names and give a one-liner description. (The feature-set is limited for now and continues to grow. So will this article continue to be updated.)
* How to access the microservices. UI. API. Is extending possible right now?
* Detailed list of what file formats and what processing is supported by which workflows/application process.
* How/where can admins check what's already configured and provisioned.
* How to create new config or request for new provisioning/purchase.

* [DO NOT COVER?] Exceptions or limitations or link back to lack of parity with AEM 6.5.
-->

Asset-Mikrodienste bieten eine skalierbare und widerstandsfähige Verarbeitung von Assets mithilfe von Cloud-Diensten. Adobe verwaltet die Dienste für eine optimale Handhabung verschiedener Asset-Typen und Verarbeitungsoptionen.

Asset processing depends on the configuration in **[!UICONTROL Processing Profiles]**, which provide a default set up, and let an administrator to add more specific asset processing configuration. Administratoren können die Konfigurationen von Nachbearbeitungs-Workflows erstellen und verwalten, einschließlich optionaler Anpassungen. Die Anpassung von Workflows ermöglicht Erweiterbarkeit und vollständige Anpassung.

Asset microservices lets you process a [broad range of file types](/help/assets/file-format-support.md) covering more formats out-of-the-box than what is possible with previous versions of Experience Manager. Beispielsweise ist jetzt das Extrahieren von Miniaturansichten von PSD- und PSB-Formaten möglich, für die zuvor Lösungen von Drittanbietern wie ImageMagick erforderlich waren.

<!-- Proposed DRAFT diagram for asset microservices flow - see section "asset-microservices-flow.png (asset-microservices-configure-and-use.md)" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![Eine allgemeine Ansicht der Asset-Verarbeitung](assets/asset-microservices-flow.png "Eine allgemeine Ansicht der Asset-Verarbeitung")

>[!NOTE]
>
>The asset processing described here replaces the `DAM Update Asset` workflow model that exists in the previous versions of [!DNL Experience Manager]. Die meisten Schritte zum Generieren von Standardausgaben und zum Erstellen von Metadaten werden durch die Verarbeitung von Asset-Microservices ersetzt. Die verbleibenden Schritte können, falls vorhanden, durch die Konfiguration des Nacharbeitungs-Workflows ersetzt werden.

## Optionen für die Verarbeitung von Assets {#get-started}

Experience Manager ermöglicht die folgenden Verarbeitungsstufen.

| Option | Beschreibung | Anwendungsfälle |
|---|---|---|
| [Standardkonfiguration](#default-config) | Es ist verfügbar und kann nicht geändert werden. Diese Konfiguration bietet eine sehr einfache Funktion zur Darstellung. | <ul> <li>Standard thumbnails used by [!DNL Assets] user interface (48, 140, and 319 px) </li> <li> Große Vorschau (Web-Ausgabe - 1280 Pixel) </li><li> Metadaten und Text-Extraktion.</li></ul> |
| [Custom configuration](#standard-config) | Configured by administrators via user interface. Provides more options for rendition generation by extending the default option. Extend the out-of-the-box option to provide different formats and renditions. | <ul><li>FPO-Darstellung. </li> <li>Change file format and resolution of images</li> <li> Conditionally apply to configured file types. </li> </ul> |
| [Custom profile](#custom-config) | Konfiguriert von Administratoren über die Benutzeroberfläche zur Verwendung von benutzerspezifischem Code über benutzerdefinierte Anwendungen zum Aufrufen des [Asset Compute-Dienstes](https://docs.adobe.com/content/help/en/asset-compute/using/introduction.html). Supports more complex requirements in a cloud-native and scalable method. | Siehe [Zulässige Anwendungsfälle](#custom-config). |

<!-- To create custom processing profiles specific to your custom requirements, say to integrate with other systems, see [post-processing workflows](#post-processing-workflows).
-->

## Unterstützte Dateiformate {#supported-file-formats}

Asset Microservices bieten Unterstützung für eine Vielzahl von Dateiformaten, um Metadaten zu verarbeiten, zu generieren oder zu extrahieren. Unter [Unterstützte Dateiformate](file-format-support.md) finden Sie die vollständige Liste der MIME-Typen und die für jeden Typ unterstützten Funktionen.

## Standardkonfiguration {#default-config}

Einige Standardwerte sind vorkonfiguriert, um sicherzustellen, dass die in Experience Manager erforderlichen Standarddarstellungen verfügbar sind. The default configuration also ensure that metadata extraction and text extraction operations are available. Benutzer können sofort mit dem Hochladen oder Aktualisieren von Assets beginnen. Die grundlegende Verarbeitung ist standardmäßig verfügbar.

With the default configuration, only the most basic processing profile is configured. Ein solches Profil ist auf der Benutzeroberfläche nicht sichtbar und Sie können es nicht ändern. Es wird immer ausgeführt, um hochgeladene Assets zu verarbeiten. Such a default processing profile ensures that the basic processing required by [!DNL Experience Manager] is completed on all assets.

<!-- ![processing-profiles-standard](assets/processing-profiles-standard.png)
-->

## Standardkonfiguration {#standard-config}

[!DNL Experience Manager] bietet Funktionen zum Generieren speziellerer Darstellungen für gängige Formate gemäß den Anforderungen des Benutzers. Ein Administrator kann zusätzliche [!UICONTROL Verarbeitungsfunktionen] erstellen, um die Erstellung solcher Darstellungen zu erleichtern. Die Benutzer weisen dann einem oder mehreren der verfügbaren Profil bestimmten Ordnern zu, um die zusätzliche Verarbeitung abzuschließen. Beispielsweise kann die zusätzliche Verarbeitung Darstellungen für Web, Mobil und Tablet generieren. Das folgende Video zeigt, wie Sie [!UICONTROL Verarbeitungsprofile] erstellen und anwenden und auf die erstellten Ausgabeformate zugreifen.

* **Darstellungsbreite und -höhe**: Die Angabe der Breite und Höhe der Darstellung bietet die maximale Größe des generierten Ausgabebilds. Asset Microservices versucht, die größtmögliche Darstellung zu erstellen, deren Breite und Höhe nicht größer als die angegebene Breite bzw. Höhe ist. Das Seitenverhältnis wird beibehalten, d. h. es entspricht dem Original. Ein leerer Wert bedeutet, dass bei der Asset-Verarbeitung die Pixelabmessungen des Originals berücksichtigt werden.

* **MIME type inclusion rules**: When an asset with a specific MIME type is processed, the MIME type is first checked against the excluded MIME types value for the rendition specification. Wenn es mit dieser Liste übereinstimmt, wird dieses spezifische Ausgabeformat nicht für das Asset generiert (Blockierungsliste). Andernfalls wird der Mime-Typ mit dem eingeschlossenen Mime-Typ verglichen. Wenn er mit der Liste übereinstimmt, wird das Ausgabeformat generiert (Zulassungsliste).

* **Spezielle FPO-Darstellung**: Beim Platzieren großer Assets aus [!DNL Experience Manager] in [!DNL Adobe InDesign] Dokumente wartet ein Kreativprofi eine Weile, nachdem er ein Asset [platziert](https://helpx.adobe.com/de/indesign/using/placing-graphics.html)hat. Meanwhile, the user is blocked from using [!DNL InDesign]. Dies unterbricht den kreativen Fluss und wirkt sich negativ auf das Kundenerlebnis aus. Adobe enables temporarily placing small-sized renditions in [!DNL InDesign] documents to begin with, which can be replaced with full-resolution assets on-demand later. [!DNL Experience Manager] bietet Ausgabeversionen, die nur für die Platzierung (FPO) verwendet werden. Diese FPO-Darstellungen haben eine kleine Dateigröße, weisen aber dasselbe Seitenverhältnis auf.

Das Verarbeitungsprofil kann eine FPO-Wiedergabe (nur für Platzierung) enthalten. In der -[!DNL Adobe Asset Link][Dokumentation](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html) erfahren Sie, ob Sie das Programm für Ihr Verarbeitungsprofil aktivieren müssen. Weitere Informationen finden Sie in der [vollständigen Dokumentation von Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html).

### Standardmäßiges Profil erstellen {#create-standard-profile}

Gehen Sie wie folgt vor, um ein Profil für die Standardverarbeitung zu erstellen:

1. Administratoren greifen auf **[!UICONTROL Werkzeuge]** > **[!UICONTROL Assets]** > **[!UICONTROL VerarbeitungsProfil]** zu. Klicken Sie auf **[!UICONTROL Erstellen]**.
1. Geben Sie einen Namen ein, der Ihnen beim Anwenden auf einen Ordner hilft, das Profil eindeutig zu identifizieren.
1. To generate FPO renditions, on the **[!UICONTROL Standard]** tab, enable **[!UICONTROL Create FPO Rendition]**. Input a **[!UICONTROL Quality]** value between 1 and 100.
1. Um andere Darstellungen zu erstellen, klicken Sie auf **[!UICONTROL Hinzufügen Neu]** und geben Sie die folgenden Informationen ein:

   * Dateiname jeder Darstellung.
   * Dateiformat (PNG, JPEG oder GIF) jeder Darstellung.
   * Breite und Höhe der einzelnen Darstellungen in Pixel. Wenn die Werte nicht angegeben werden, wird die vollständige Pixelgröße des Originalbilds verwendet.
   * Qualität in Prozent jeder JPEG-Darstellung.
   * Eingeschlossene und ausgeschlossene MIME-Typen zur Definition der Anwendbarkeit eines Profils.

   ![processing-profiles-adding](assets/processing-profiles-adding.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

<!-- TBD: Update the video link when a new video is available from Tech Marketing.

The following video demonstrates the usefulness and usage of standard profile.

>[!VIDEO](https://video.tv.adobe.com/v/29832?quality=9)
-->

<!-- This image was removed per cqdoc-15624, as requested by engineering.
 ![processing-profiles-list](assets/processing-profiles-list.png) 
 -->

## Benutzerspezifische Profil- und Anwendungsfälle {#custom-config}

Das [!DNL Asset Compute Service] unterstützt eine Vielzahl von Anwendungsfällen, z. B. Standardverarbeitung, Verarbeitung von Adoben-spezifischen Formaten wie Photoshop-Dateien und Implementierung benutzerspezifischer oder organisationsspezifischer Verarbeitungsformate. Die zuvor erforderliche Anpassung des DAM Update Asset-Workflows wird entweder automatisch oder über die Konfiguration der verarbeitenden Profil durchgeführt. If the business needs are not met by these processing options, Adobe recommends developing and using [!DNL Asset Compute Service] to extend the default capabilities. Eine Übersicht finden Sie unter Erweiterbarkeit [und Verwendungszeitpunkt](https://docs.adobe.com/content/help/en/asset-compute/using/extend/understand-extensibility.html).

>[!NOTE]
>
>Adobe recommends using a custom application only when the business requirements cannot be accomplished using the default configurations or the standard profile.

Sie können Bild-, Video-, Dokument- und andere Dateiformate in verschiedene Darstellungen umwandeln, einschließlich Miniaturansichten, extrahiertem Text und Metadaten sowie Archiven.

Developers can use the [!DNL Asset Compute Service] to [create custom applications](https://docs.adobe.com/content/help/en/asset-compute/using/extend/develop-custom-application.html) that cater to the supported use cases. [!DNL Experience Manager] Sie können diese benutzerdefinierten Anwendungen über die Benutzeroberfläche aufrufen, indem Sie benutzerdefinierte Profil verwenden, die Administratoren konfigurieren. [!DNL Asset Compute Service] unterstützt die folgenden Anwendungsfälle beim Aufrufen externer Dienste:

* Verwenden Sie [!DNL Adobe Photoshop]die [ImageCutout-API](https://github.com/AdobeDocs/photoshop-api-docs-pre-release#imagecutout) und speichern Sie das Ergebnis als Darstellung.
* Rufen Sie Drittanbietersysteme auf, um Daten zu aktualisieren, z. B. ein PIM-System.
* Verwenden Sie die [!DNL Photoshop] API, um verschiedene Darstellungen basierend auf der Photoshop-Vorlage zu generieren.
* Verwenden Sie die Lightroom-API [der](https://github.com/AdobeDocs/lightroom-api-docs#supported-features) Adobe, um die erfassten Assets zu optimieren und als Darstellungen zu speichern.

>[!NOTE]
>
>Sie können die Standardmetadaten nicht mit den benutzerdefinierten Anwendungen bearbeiten. Sie können nur benutzerdefinierte Metadaten ändern.

### Create a custom profile {#create-custom-profile}

Gehen Sie wie folgt vor, um ein benutzerdefiniertes Profil zu erstellen:

1. Administratoren greifen auf **[!UICONTROL Werkzeuge > Assets > Profil]** für die Verarbeitung zu. Klicken Sie auf **[!UICONTROL Erstellen]**.
1. Click **[!UICONTROL Custom]** tab. Click **[!UICONTROL Add New]**. Provide the desired file name of the rendition.
1. Geben Sie die folgenden Informationen ein.

   * Dateiname jeder Darstellung und eine unterstützte Dateierweiterung.
   * [Endpunkt-URL einer benutzerdefinierten Firefly-App](https://docs.adobe.com/content/help/en/asset-compute/using/extend/deploy-custom-application.html). Die App muss aus demselben Unternehmen stammen wie das Experience Manager-Konto.
   * hinzufügen Service-Parameter, um zusätzliche Informationen oder Parameter an die benutzerdefinierte Anwendung [zu](https://docs.adobe.com/content/help/en/asset-compute/using/extend/develop-custom-application.html#pass-custom-parameters)übergeben.
   * MIME-Typen wurden eingeschlossen und ausgeschlossen, um die Verarbeitung auf einige bestimmte Dateiformate zu beschränken.

   Klicken Sie auf **[!UICONTROL Speichern]**.

Bei den benutzerdefinierten Anwendungen handelt es sich um kopflose [Project Firefly](https://github.com/AdobeDocs/project-firefly) -Apps. Die benutzerdefinierte Anwendung ruft alle angegebenen Dateien ab, wenn sie mit einem verarbeitenden Profil eingerichtet wurden. Die Anwendung muss die Dateien filtern.

>[!CAUTION]
>
>Wenn die Firefly-App und das [!DNL Experience Manager] -Konto nicht aus demselben Unternehmen stammen, funktioniert die Integration nicht.

### Beispiel für ein benutzerdefiniertes Profil {#custom-profile-example}

Zur Veranschaulichung der Verwendung von benutzerdefiniertem Profil sollten wir einen Verwendungsfall erwägen, um Kampagnen mit benutzerdefiniertem Text zu versehen. You can create a processing profile that leverages the Photoshop API to edit the images.

Asset Compute Service integration allows Experience Manager to pass these parameters to the custom application using the [!UICONTROL Service Parameters] field. The custom application then invokes Photoshop API and passes these values to the API. For example, you can pass font name, text color, text weight and text size to add the custom text to campaign images.

![custom-processing-profile](assets/custom-processing-profile.png)

*Figure: Use[!UICONTROL Service Parameters]field to pass added information to predefined parameters build into the custom application.*

When campaign images are uploaded to the folder on which this processing profile is applied, the images are updated with `Jumanji` text in `Arial-BoldMT` font.

## Use processing profiles to process assets {#use-profiles}

Erstellen Sie die zusätzlichen benutzerdefinierten Verarbeitungsprofile und wenden Sie sie auf bestimmte Ordner an, damit Experience Manager sie für Assets verarbeitet, die in diese Ordner hochgeladen oder in diesen aktualisiert wurden. Das standardmäßige integrierte Verarbeitungsprofil wird immer ausgeführt, ist jedoch auf der Benutzeroberfläche nicht sichtbar. Wenn Sie ein benutzerdefiniertes Profil hinzufügen, werden beide Profil zur Verarbeitung der hochgeladenen Assets verwendet.

Wenden Sie verarbeitende Profil auf Ordner mit einer der folgenden Methoden an:

* Administrators can select a processing profile definition in **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Processing Profiles]**, and use **[!UICONTROL Apply Profile to Folder(s)]** action. Dadurch wird ein Inhalts-Browser geöffnet, mit dem Sie zu bestimmten Ordnern navigieren, diese auswählen und die Anwendung des Profils bestätigen können.
* Users can select a folder in the Assets user interface, use **[!UICONTROL Properties]** action to open folder properties screen, click on the **[!UICONTROL Processing Profiles]** tab, and in the popup list, select the correct processing profile for that folder. Um die Änderungen zu speichern, klicken Sie auf **[!UICONTROL Speichern &amp; Schließen]**.

>[!NOTE]
>
>Nur ein Verarbeitungsprofil kann auf einen bestimmten Ordner angewendet werden. Um weitere Darstellungen zu generieren, fügen Sie dem bestehenden Profil weitere Darstellungsdefinitionen hinzu.

Nachdem ein Verarbeitungsprofil auf einen Ordner angewendet wurde, werden alle neuen Assets, die in diesen Ordner oder in dessen Unterordnern hochgeladen (oder aktualisiert) werden, mit dem konfigurierten zusätzlichen Verarbeitungsprofil verarbeitet. This processing is in addition to the standard, default profile. Wenn Sie mehrere Profile auf einen Ordner anwenden, werden die hochgeladenen oder aktualisierten Elemente mit jedem dieser Profile verarbeitet.

>[!NOTE]
>
>A processing profile applied to a folder works for the entire tree, but can be over-ridden with another profile applied to a sub-folder. Wenn Assets in einen Ordner hochgeladen werden, prüft Experience Manager die Eigenschaften des zugehörigen Ordners auf ein Verarbeitungsprofil. Wenn keine Anwendung erfolgt, wird ein übergeordneter Profil in der Hierarchie auf die Anwendung eines Verarbeitungsordners überprüft.

Alle generierten Darstellungen sind in der Ansicht [!UICONTROL Darstellungen] in der linken Leiste verfügbar. Öffnen Sie die Asset-Vorschau und öffnen Sie die linke Leiste, um auf die Ansicht **[!UICONTROL Ausgabeformate]** zuzugreifen. Die spezifischen Ausgabeformate im Verarbeitungsprofil, für die der Typ des jeweiligen Assets mit den Einschlussregeln des MIME-Typs übereinstimmt, sollten sichtbar und zugänglich sein.

![additional-renditions](assets/renditions-additional-renditions.png)

*Abbildung: Beispiel für zwei zusätzliche Darstellungen, die von einem verarbeitenden Profil generiert wurden, das auf den übergeordneten Ordner angewendet wurde.*

## Nachbearbeitungs-Workflows {#post-processing-workflows}

In Fällen, in denen zusätzliche Verarbeitung von Assets erforderlich ist, die mit den Verarbeitungsprofilen nicht erreicht werden können, können der Konfiguration zusätzliche Nachbearbeitungs-Workflows hinzugefügt werden. Dies ermöglicht es, zusätzlich zu der konfigurierbaren Verarbeitung mithilfe von Asset-Microservices eine vollständig angepasste Verarbeitung hinzuzufügen.

Nachbearbeitungs-Workflows werden, falls konfiguriert, automatisch von AEM ausgeführt, nachdem die Verarbeitung der Microservices abgeschlossen ist. Es ist nicht notwendig, Workflow-Starter manuell hinzuzufügen, um sie auszulösen. Zu den Beispielen gehören:

* Benutzerdefinierte Workflow-Schritte zur Verarbeitung von Assets.
* Integrationen, um Assets von externen Systemen Metadaten oder Eigenschaften hinzuzufügen, z. B. Produkt- oder Prozessinformationen.
* Zusätzliche Verarbeitung durch externe Dienste.

Das Hinzufügen einer Workflow-Konfiguration für die Nachbearbeitung zu Experience Manager umfasst die folgenden Schritte:

* Erstellen eines oder mehrerer Workflow-Modelle. In den Dokumenten wird dies als *Workflow-Modelle für die Nachbearbeitung* erwähnt, bei denen es sich jedoch um normale Workflow-Modelle für Experience Manager handelt.
* Hinzufügen spezifischer Workflow-Schritte zu diesen Modellen. Die Schritte werden basierend auf einer Workflow-Modellkonfiguration für die Assets ausgeführt.
* Fügen Sie am Ende den Schritt [!UICONTROL Abgeschlosser Prozess zum DAM-Workflow eines Asset-Updates] hinzu. Durch Hinzufügen dieses Schritts wird sichergestellt, dass Experience Manager weiß, wann die Verarbeitung abgeschlossen ist, und das Asset als verarbeitet markiert werden kann, d. h., dass beim Asset der Wert *Neu* angezeigt wird.
* Erstellen Sie eine Konfiguration für den Custom Workflow Runner Service, mit der die Ausführung eines Nachbearbeitungs-Workflow-Modells entweder nach Pfad (Speicherort für Ordner) oder nach regulären Ausdrücken konfiguriert werden kann.

### Erstellen von Nachbearbeitungs-Workflow-Modellen {#create-post-processing-workflow-models}

Nachbearbeitungs-Workflow-Modelle sind normale AEM-Workflow-Modelle. Erstellen Sie verschiedene Modelle, wenn Sie für verschiedene Repository-Standorte oder Asset-Typen eine unterschiedliche Verarbeitung benötigen.

Verarbeitungsschritte sollten je nach Bedarf hinzugefügt werden. Sie können alle verfügbaren unterstützten Schritte sowie alle benutzerdefinierten Workflow-Schritte verwenden.

Stellen Sie sicher, dass der letzte Schritt jedes Nachbearbeitungs-Workflows `DAM Update Asset Workflow Completed Process` ist. Der letzte Schritt stellt sicher, dass Experience Manager weiß, wann die Asset-Verarbeitung abgeschlossen ist.

### Konfigurieren der Ausführung von Nachbearbeitungs-Workflows {#configure-post-processing-workflow-execution}

Um die Nachbearbeitungs-Workflow-Modelle zu konfigurieren, die für Assets ausgeführt werden sollen, die nach Abschluss der Verarbeitung der Asset-Microservices in das System hochgeladen oder aktualisiert werden, muss der Custom Workflow Runner-Dienst konfiguriert werden.

Der Custom Workflow Runner Service (`com.adobe.cq.dam.processor.nui.impl.workflow.CustomDamWorkflowRunnerImpl`) ist ein OSGi-Dienst und bietet zwei Konfigurationsoptionen:

* Nachbearbeitungs-Workflows nach Pfad (`postProcWorkflowsByPath`): Es können mehrere Workflow-Modelle basierend auf unterschiedlichen Repository-Pfaden aufgeführt werden. Pfade und Modelle sollten durch einen Doppelpunkt voneinander getrennt werden. Einfache Repository-Pfade werden unterstützt und sollten einem Workflow-Modell im `/var`-Pfad zugeordnet werden. Beispiel: `/content/dam/my-brand:/var/workflow/models/my-workflow`.
* Nachbearbeitungs-Workflows nach Ausdruck (`postProcWorkflowsByExpression`): Es können mehrere Workflow-Modelle basierend auf unterschiedlichen regulären Ausdrücken aufgelistet werden. Ausdrücke und Modelle sollten durch einen Doppelpunkt getrennt werden. Der reguläre Ausdruck sollte direkt auf den Asset-Knoten verweisen und nicht auf eine der Ausgaben oder Dateien. Beispiel: `/content/dam(/.*/)(marketing/seasonal)(/.*):/var/workflow/models/my-workflow`.

>[!NOTE]
>
>Die Konfiguration von Custom Workflow Runner ist eine Konfiguration eines OSGi-Dienstes. Informationen zum Bereitstellen einer OSGi-Konfiguration finden Sie unter [Bereitstellung in Experience Manager](/help/implementing/deploying/overview.md).
>Die OSGi-Web-Konsole ist im Gegensatz zu On-Premise- und Managed Services-Bereitstellungen von AEM nicht direkt in den Cloud Services-Bereitstellungen verfügbar.

Weitere Informationen dazu, welcher standardmäßige Workflow-Schritt im Nachbearbeitungs-Workflow verwendet werden kann, finden Sie unter [Workflow-Schritte im Nachbearbeitungs-Workflow](developer-reference-material-apis.md#post-processing-workflows-steps) in der Entwicklerreferenz.

## Best Practices und Einschränkungen {#best-practices-limitations-tips}

* Berücksichtigen Sie beim Entwickeln von Workflows Ihre Anforderungen für alle Arten von Ausgabedarstellungen. Wenn Sie der Meinung sind, dass eine Ausgabedarstellung in Zukunft nicht erforderlich sein wird, entfernen Sie den Erstellungsschritt aus dem Workflow. Ausgabedarstellungen können später nicht mehr stapelweise gelöscht werden. Unerwünschte Ausgabedarstellungen können nach längerer Nutzung von [!DNL Experience Manager] viel Speicherplatz beanspruchen. Bei einzelnen Assets können Sie Ausgabedarstellungen manuell aus der Benutzeroberfläche entfernen. Bei mehreren Assets können Sie [!DNL Experience Manager] so anpassen, dass entweder bestimmte Ausgabedarstellungen gelöscht oder die Assets gelöscht und die gelöschten Assets erneut hochgeladen werden.
* Derzeit ist die Unterstützung auf das Generieren von Darstellungen beschränkt. Das Generieren neuer Assets wird nicht unterstützt.

>[!MORELIKETHIS]
>
>* [Einführung in den Asset Compute-Dienst](https://docs.adobe.com/content/help/en/asset-compute/using/introduction.html).
>* [Verstehen Sie die Erweiterbarkeit und wann sie](https://docs.adobe.com/content/help/en/asset-compute/using/extend/understand-extensibility.html)verwendet werden soll.
>* [Erstellen benutzerdefinierter Anwendungen](https://docs.adobe.com/content/help/en/asset-compute/using/extend/develop-custom-application.html).

