---
Title: Authoring a Form
Description: This article provides information on various form authoring platforms, including the Universal Editor, document-based authoring, and Adaptive Forms editors (Core Components and Foundation Components).
Keywords: Universal Editor for WYSIWYG authoring, document-based authoring, Adaptive Forms editors, Adaptive Forms editors for Core Components authoring, Adaptive Forms editors for Foundation Components authoring
feature: Edge Delivery Services
Role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: bdc0e51a8b16df432f1f1aeabed11135fb8c8e0c
workflow-type: tm+mt
source-wordcount: '877'
ht-degree: 2%

---


# Erstellen eines Formulars

Adobe Experience Manager bietet und unterstützt mehrere Editoren zum Erstellen eines Formulars. Sie können Folgendes verwenden:
* Universeller Editor (für die Bearbeitung in WYSIWYG)
* Microsoft Excel oder Google Sheets (Dokumentenbasiertes Authoring)
* Editoren für adaptive Forms (für auf Kernkomponenten oder Foundation-Komponenten basierendes Authoring)

**[Bild zum Hinzufügen]**

## Universeller Editor (für die Bearbeitung in WYSIWYG)

Der universelle Editor ist ein vielseitiger visueller Editor, der eine WYSIWYG-Funktion (What-you-see-is-what-you-get) bietet, die eine intuitive Formularerstellung gewährleistet. Es wird empfohlen, beim Erstellen neuer Formulare den universellen Editor zu verwenden, da dieser ein modernes, benutzerfreundliches Design und eine praktische Drag-and-Drop-Oberfläche bietet.

Um Formulare mit dem universellen Editor zu erstellen, werden Edge Delivery Services-Vorlagen verwendet, die in der AEM-Umgebung verfügbar sind. Diese Formulare übernehmen ihr Erscheinungsbild von den Konfigurationen im GitHub-Repository von Edge Delivery Services. [Eine Verbindung zwischen Ihrer AEM-Umgebung und dem Edge Delivery Services-GitHub-Repository](/help/edge/docs/forms/publishing-forms.md) wird hergestellt, um die Veröffentlichung dieser Formulare auf Edge Delivery Services zu ermöglichen.

Ausführliche Anweisungen zum Erstellen von Inhalten mit dem universellen Editor finden Sie im Artikel [Authoring von Inhalten mit dem universellen Editor](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/sites/authoring/universal-editor/authoring) .

## Microsoft Excel oder Google Sheets (Dokumentenbasiertes Authoring)

Sie können die Formulare mithilfe der dokumentbasierten Bearbeitung mit Microsoft Excel- oder Google Sheets-Dateien erstellen, sodass Sie die robusten Ökosysteme und APIs von Google Sheets, Microsoft Excel und Microsoft SharePoint nutzen können. Dieser Ansatz ist besonders nützlich, um einfache Formulare ohne erweiterte Übermittlungsdienste zu erstellen.

Um mit der Erstellung eines Formulars mit Microsoft Excel oder Google Sheets zu beginnen, [richten Sie ein AEM-Projekt mit dem AEM Forms-Textbaustein ein](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) und klonen Sie das entsprechende GitHub-Repository auf Ihrem lokalen Computer. AEM Forms Edge Delivery bietet eine Funktion namens „Adaptive Forms-Block“, die das Erstellen von Formularen zum Erfassen und Speichern von Daten vereinfacht. Informationen zum Erstellen und Veröffentlichen von Formularen mit dem adaptiven Forms-Block auf Edge Delivery Services finden Sie unter [Erstellen eines Formulars](/help/edge/docs/forms/create-forms.md).

## Editoren für adaptive Forms (für auf Kernkomponenten oder Foundation-Komponenten basierendes Authoring)

Sie können Formulare erstellen, die ansprechend, responsiv und dynamisch sind. Der Editor für adaptive Formulare bietet einen benutzerfreundlichen Assistenten, mit dem Sie schnell adaptive Forms erstellen können. Der Formular-Assistent bietet eine einfache Registerkartennavigation, mit der Sie vorkonfigurierte Vorlagen für Foundation- oder Kernkomponenten, Designs, Datenmodelle und Übermittlungsoptionen auswählen können, um ein Formular effizient zu erstellen.

[Erstellen von Formularen mit Kernkomponenten](/help/forms/creating-adaptive-form-core-components.md) ermöglicht es Ihnen, standardisierte Datenerfassungskomponenten zu nutzen, die angepasst werden können, wodurch die Entwicklungszeit verkürzt und die Wartungskosten für digitale Registrierungserlebnisse gesenkt werden. Diese Formulare können mit dem adaptiven Forms-Block auf Edge Delivery Services oder über die AEM-Publish-Instanz veröffentlicht werden.

[Erstellen von Formularen mit Foundation-Komponenten](/help/forms/create-an-adaptive-form.md) verwendet klassische Datenerfassungskomponenten. Diese Formulare können nur mit der AEM Publish-Instanz veröffentlicht werden.

Sie können Formulare, die mit den Editoren für adaptive Forms erstellt wurden, auch auf Edge Delivery Services veröffentlichen, indem Sie [Verbindung zwischen Ihrer AEM-Umgebung und dem Edge Delivery Services-GitHub-Repository herstellen](/help/edge/docs/forms/publishing-forms.md).

## Auswahl zwischen verschiedenen Typen für die Formularerstellung

In der folgenden Tabelle sind die Funktionen und Anwendungsfälle für jeden Authoring-Editor aufgeführt, sodass Sie basierend auf Ihren Anforderungen und den Anforderungen an die Formularübermittlung das richtige Tool auswählen können.

| **Editor für die Formularerstellung** | **Schlüsselansatz** | **Funktionen** | **Veröffentlichungsmethode** | **Anwendungsfälle** |
|--------|-----------|-------|-------|------------------------------------------------|
| **Dokumentbasiertes Authoring** | Verwendet vertraute Tools wie Google Docs und Microsoft Office für die Formularerstellung. | Forms werden mithilfe von Kalkulationstabellen erstellt, wobei die Daten direkt an Google Sheets oder Microsoft Excel Sheets übermittelt werden. </br> </br> Diese Formulare lassen sich schneller erstellen und bereitstellen. Sie benötigen keine Vorkenntnisse in AEM, um benutzerdefinierte Komponenten und Stile für diese Formulare zu entwickeln. | Diese Formulare werden auf Edge Delivery Services veröffentlicht und haben einen sehr hohen Google Lighthouse-Wert. </br> </br> Die Highscore führt zu schnellerem Rendering und besserer SEO. | Diese Formulare eignen sich ideal für schnelle Prototypen oder einfache Formulare, bei denen keine erweiterten Übermittlungsdienste erforderlich sind. </br> </br> Diese sind für Umfragen, Registrierungen oder Feedback-Formulare geeignet, die eine Datenspeicherung in Tabellen erfordern. Diese Formulare werden auf Edge Delivery-Services veröffentlicht |
| **Universeller Editor** </br> </br> Wenn Sie ein neues Formular erstellen, verwenden Sie den universellen Editor, um Formulare zu erstellen. | Bietet eine WYSIWYG-Oberfläche für die intuitive Formularerstellung. | Forms sind über eine intuitive Drag-and-Drop-Oberfläche entwickelt worden. </br> </br> Diese Formulare übernehmen das Erscheinungsbild des konfigurierten Edge Delivery Services-GitHub-Repositorys für das entsprechende Formular. | Diese Formulare werden auf Edge Delivery Services veröffentlicht und haben einen sehr hohen Google Lighthouse-Wert. </br> </br> Die Highscore führt zu schnellerem Rendering und besserer SEO. | Diese Formulare eignen sich ideal zum Erstellen von Formularen für Edge Delivery Service-Sites und -Seiten. Diese Formularszenarien umfassen komplexe Formulare, komplexe Workflows, benutzerdefinierte Aktionen oder Integrationen mit externen Systemen |
| **Adaptive Forms-Editoren** | bietet einen assistentengesteuerten Ansatz, um mit der Formularerstellung schnell zu beginnen, indem Vorlagen, Stile und vordefinierte Felder verwendet werden. | Verwenden Sie diese Editoren, um auf Kernkomponenten basierende Formulare oder auf Foundation-Komponenten basierende Formulare zu erstellen. | Diese Formulare können auf Edge Delivery Services oder über AEM-Publish-Instanzen veröffentlicht werden. | Verwenden Sie diese Editoren, um auf Kernkomponenten basierende Formulare oder auf Foundation-Komponenten basierende Formulare zu erstellen. Ideal für Szenarien mit komplexen Formularen, komplexen Workflows, benutzerdefinierten Aktionen oder Integrationen mit externen Systemen. |


>[!NOTE]
>
>
> Sollten Funktionen im universellen Editor fehlen, die zuvor im adaptiven Forms-Editor verfügbar waren, können Sie diese per E-Mail an mailto:aem-forms-ea@adobe.com unter Ihrer offiziellen E-Mail-Adresse anfordern.

## Verwandter Artikel

* [Dokumentenbasiertes Authoring mit Microsoft Excel oder Google Sheets](/help/edge/docs/forms/create-forms.md)
* [Universeller Editor für das WYSIWYG-Authoring](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring)
* [Erstellen eines adaptiven Formulars (Foundation-Komponenten)](/help/forms/creating-adaptive-form.md)
* [Erstellen eines adaptiven Formulars (Kernkomponenten)](/help/forms/create-an-adaptive-form.md)

## Siehe auch

{{see-more-forms-eds}}