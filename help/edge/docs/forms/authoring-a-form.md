---
Title: Authoring a Form
Description: This article provides information on various form authoring platforms, including the Universal Editor, document-based authoring, and Adaptive Forms editors (Core Components and Foundation Components).
Keywords: Universal Editor for WYSIWYG authoring, document-based authoring, Adaptive Forms editors, Adaptive Forms editors for Core Components authoring, Adaptive Forms editors for Foundation Components authoring
feature: Edge Delivery Services
Role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: bdc0e51a8b16df432f1f1aeabed11135fb8c8e0c
workflow-type: ht
source-wordcount: '877'
ht-degree: 100%

---


# Erstellen eines Formulars

Adobe Experience Manager bietet und unterstützt mehrere Editoren zur Formularerstellung. Sie können Folgendes verwenden:
* Universeller Editor (zum WYSIWYG-Authoring)
* Microsoft Excel oder Google Tabellen (auch als dokumentbasiertes Authoring bezeichnet)
* Editoren für adaptive Formulare (zum auf Kern- oder Foundation-Komponenten basierenden Authoring)

**[Abbildung hinzuzufügen]**

## Universeller Editor (zum WYSIWYG-Authoring)

Der universelle Editor ist ein vielseitiger visueller Editor mit WYSIWYG(What You See Is What You Get)-Funktion bietet, der eine intuitive Formularerstellung ermöglicht. Es wird empfohlen, beim Erstellen neuer Formulare den universellen Editor zu verwenden, da dieser ein modernes, benutzerfreundliches Design und eine praktische Drag-and-Drop-Oberfläche bietet.

Um Formulare mit dem universellen Editor zu erstellen, werden die in der AEM-Umgebung verfügbaren Edge Delivery Services-Vorlagen verwendet. Diese Formulare übernehmen ihr Look-and-Feel von den Konfigurationen im Edge Delivery Services-GitHub-Repository. [Eine Verbindung zwischen Ihrer AEM-Umgebung und dem Edge Delivery Services-GitHub-Repository](/help/edge/docs/forms/publishing-forms.md) wird hergestellt, um die Veröffentlichung dieser Formulare in Edge Delivery Services zu ermöglichen.

Ausführliche Anweisungen zum Authoring mit dem universellen Editor finden Sie unter [Inhaltserstellung mit dem universellen Editor](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/sites/authoring/universal-editor/authoring).

## Microsoft Excel oder Google Tabellen (auch als dokumentbasiertes Authoring bezeichnet)

Sie können Formulare durch dokumentbasiertes Authoring mit Microsoft Excel- oder Google Tabellen-Dateien erstellen, sodass Sie die robusten Ökosysteme und APIs von Google Tabellen, Microsoft Excel und Microsoft SharePoint nutzen können. Dieser Ansatz ist besonders nützlich, wenn es darum geht, einfache Formulare ohne erweiterte Übermittlungsdienste zu erstellen.

Um ein Formular mit Microsoft Excel oder Google Tabellen zu erstellen, [richten Sie ein AEM-Projekt mit der AEM Forms-Bausteinvorlage ein](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) und klonen Sie das entsprechende GitHub-Repository auf Ihrem lokalen Computer. AEM Forms Edge Delivery bietet eine Funktion für adaptive Formularblöcke, die die Erstellung von Formularen zum Erfassen und Speichern von Daten vereinfacht. Informationen zum Erstellen und Veröffentlichen von Formularen mit einem adaptiven Formularblock in Edge Delivery Services finden Sie unter [Erstellen eines Formulars](/help/edge/docs/forms/create-forms.md).

## Editoren für adaptive Formulare (zum auf Kern- oder Foundation-Komponenten basierenden Authoring)

Sie können Formulare erstellen, die ansprechend, responsiv und dynamisch sind. Der Editor für adaptive Formulare bietet einen benutzerfreundlichen Assistenten, mit dem Sie adaptive Formulare schnell erstellen können. Der Formularassistent ermöglicht eine einfache Registerkartennavigation, durch die Sie vorkonfigurierte Vorlagen für Foundation- oder Kernkomponenten, Designs, Datenmodelle und Übermittlungsoptionen auswählen und so Formulare effizient erstellen können.

Die [Erstellung von Formularen mit Kernkomponenten](/help/forms/creating-adaptive-form-core-components.md) ermöglicht die Nutzung anpassbarer standardisierter Datenerfassungskomponenten. Dies verkürzt nicht nur die Entwicklungszeit, sondern senkt zudem die Wartungskosten für digitale Anmeldeerlebnisse. Diese Formulare können mit dem Block für adaptive Formulare in Edge Delivery Services oder über die AEM-Veröffentlichungsinstanz veröffentlicht werden.

Beim [Erstellen von Formularen mit Foundation-Komponenten](/help/forms/create-an-adaptive-form.md) kommen klassische Datenerfassungskomponenten zum Einsatz. Diese Formulare können nur mit der AEM-Veröffentlichungsinstanz veröffentlicht werden.

Sie können Formulare, die mit Editoren für adaptive Formulare erstellt wurden, auch in Edge Delivery Services veröffentlichen. Hierzu ist eine [Verbindung zwischen Ihrer AEM-Umgebung und dem Edge Delivery Services-GitHub-Repository](/help/edge/docs/forms/publishing-forms.md) erforderlich.

## Auswählen zwischen verschiedenen Typen zur Formularerstellung

In der folgenden Tabelle sind die Funktionen und Anwendungsfälle für jeden Authoring-Editor aufgeführt, sodass Sie die richtige Wahl basierend auf Ihren Bedürfnissen und den Anforderungen an die Formularübermittlung treffen können.

| **Editor zur Formularerstellung** | **Zentraler Ansatz** | **Funktionen** | **Veröffentlichungsmethode** | **Anwendungsfälle** |
|--------|-----------|-------|-------|------------------------------------------------|
| **Dokumentenbasiertes Authoring** | Nutzt vertraute Tools wie Google Docs und Microsoft Office zur Formularerstellung. | Formulare werden mithilfe von Tabellen erstellt, wobei die Daten direkt an Google Tabellen- oder Microsoft Excel-Blätter übermittelt werden. </br> </br> Diese Formulare lassen sich schneller erstellen und bereitstellen. Sie benötigen keine AEM-Vorkenntnisse, um benutzerdefinierte Komponenten und Stile für diese Formulare zu entwickeln. | Diese Formulare werden in Edge Delivery Services veröffentlicht und haben einen sehr hohen Google Lighthouse Score. </br> </br> Dieser hohe Score führt zu schnellerem Rendern und besserer SEO. | Diese Formulare eignen sich ideal für schnelle Prototypen oder einfache Formulare, bei denen keine erweiterten Übermittlungsdienste benötigt werden. </br> </br> Sie sind für Umfragen, Registrierungen oder Feedback-Formulare geeignet, für die eine Datenspeicherung in Tabellen erforderlich ist. Diese Formulare werden in Edge Delivery Services veröffentlicht |
| **Universeller Editor**  </br> </br> Wenn Sie ein neues Formular erstellen, verwenden Sie den universellen Editor. | Bietet eine WYSIWYG-Oberfläche zur intuitiven Formularerstellung. | Formulare werden über eine intuitive Drag-and-Drop-Oberfläche entwickelt. </br> </br> Diese Formulare übernehmen das Look-and-Feel des konfigurierten Edge Delivery Services-GitHub-Repositorys für das entsprechende Formular. | Diese Formulare werden in Edge Delivery Services veröffentlicht und haben einen sehr hohen Google Lighthouse Score. </br> </br> Dieser hohe Score führt zu schnellerem Rendern und besserer SEO. | Diese Formulare sind ideal zum Erstellen von Formularen für Edge Delivery Service-Sites und -Seiten geeignet. Diese Formularszenarien umfassen komplexe Formulare, komplexe Workflows, benutzerdefinierte Aktionen oder Integrationen mit externen Systemen |
| **Editoren für adaptive Formulare** | Bieten einen assistentengestützten Ansatz, um mit der Formularerstellung schnell beginnen zu können, indem Vorlagen, Stile und vordefinierte Felder verwendet werden. | Verwenden Sie diese Editoren, um auf Kern- oder Foundation-Komponenten basierende Formulare zu erstellen. | Diese Formulare können in Edge Delivery Services oder über AEM-Veröffentlichungsinstanzen veröffentlicht werden. | Verwenden Sie diese Editoren, um auf Kern- oder Foundation-Komponenten basierende Formulare zu erstellen. Ideal für Szenarien mit komplexen Formularen, komplexen Workflows, benutzerdefinierten Aktionen oder Integrationen mit externen Systemen. |


>[!NOTE]
>
>
> Sollten Funktionen im universellen Editor fehlen, die zuvor im Editor für adaptive Formulare verfügbar gewesen sind, können Sie diese per E-Mail an mailto:aem-forms-ea@adobe.com unter Angabe Ihrer offiziellen E-Mail-Adresse anfordern.

## Verwandte Artikel

* [Dokumentbasiertes Authoring mit Microsoft Excel oder Google Tabellen](/help/edge/docs/forms/create-forms.md)
* [Universeller Editor zum WYSIWYG-Authoring](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring)
* [Erstellen eines adaptiven Formulars (Foundation-Komponenten)](/help/forms/creating-adaptive-form.md)
* [Erstellen eines adaptiven Formulars (Kernkomponenten)](/help/forms/create-an-adaptive-form.md)

## Siehe auch

{{see-more-forms-eds}}