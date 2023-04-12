---
title: Versionshinweise für Version 2022.8.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Versionshinweise für Version 2022.8.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 0eff8100-5990-4553-8373-445fb7e6fb27
source-git-commit: 599f924465552b2ef43827da8e139c239e47baed
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 61%

---

# Versionshinweise für 2022.8.0 für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise für Funktionen der Version 2022.8.0 von [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] aktuelle Version (2022.8.0) ist der 1. September 2022.
Die nächste Version (2022.10.0) ist für den 10. November 2022 geplant.

## Video zur Version {#release-video}

Sehen Sie sich das Video Versionsübersicht vom August 2022 an, um eine Zusammenfassung der Funktionen zu erhalten, die in der Version 2022.8.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/346608/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Sites] {#sites-features}

* Die E-Mail-Komponente ermöglicht die Erstellung von Inhalten in AEM, die dann per Campaign Classic als E-Mails gesendet werden. Die Kernkomponente &quot;E-Mail&quot;:
   * basiert auf der [WCM-Kernkomponente](https://github.com/adobe/aem-core-wcm-components) unterstützt bearbeitbare Vorlagen und das Stilsystem.
   * bietet 10 für E-Mails optimierte produktionsbereite Komponenten (Seite, Container, Titel, Text, Bild, Schaltfläche, Teaser, Experience Fragment, Inhaltsfragment, Segmentierung).
   * bietet erweiterte Personalisierung und Segmentierung dank der [Einfügen von Campaign-Variablen](https://github.com/adobe/aem-core-email-components/wiki/RTE-Personalization) in den meisten Dialogfeldern und zur flexiblen [Segmentierungskomponente](https://github.com/adobe/aem-core-email-components/wiki/Segmentation-component-(Technical-Documentation)).
   * bietet dank der [CSS-Stile in Liner](https://github.com/adobe/aem-core-email-components/wiki/HTML-Inliner:-Technical-documentation), die [HTML-Attribut inliner](https://github.com/adobe/aem-core-email-components/wiki/HTML-Inliner:-Technical-documentation)und die [HTML sanitizer](https://github.com/adobe/aem-core-email-components/wiki/HTML-sanitizing:-Technical-documentation).
   * ermöglicht die Erstellung von E-Mails überall.

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Sites] verfügbar {#prerelease-features-sites}

* Die [Inhaltsfragmentkonsole](/help/sites-cloud/administering/content-fragments/content-fragments-console.md) bietet Benutzern die Möglichkeit, die Gesamtzahl der Sprachkopien anzuzeigen, die mit einem Inhaltsfragment verknüpft sind. Über einen 1-Klick-Zugriff können auch alle Sprachkopien angezeigt werden. Benutzende können die Tabellenansicht auch nach der Region filtern, die sie interessiert.

![Sprachen von Inhaltsfragmenten](/help/release-notes/assets/cfconsole-languages.png)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#features-assets}

* Sie können Adobe Experience Manager Assets jetzt so konfigurieren, dass [den Typ der Assets einschränken, die Benutzer basierend auf dem MIME-Typ hochladen können](/help/assets/configure-asset-upload-restrictions.md).

   ![Einschränkungen beim Hochladen von Assets](/help/assets/assets/asset-upload-restrictions.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Forms] verfügbar {#prerelease-features-forms}

* [Assistent für adaptive Formulare](/help/forms/creating-adaptive-form.md): AEM Forms bietet einen benutzerfreundlichen Assistenten für Unternehmen, mit dem sich adaptive Formulare schnell erstellen lassen. Der Assistent bietet eine schnelle Navigation zwischen den Registerkarten, mit der Sie einfach vorkonfigurierte Vorlagen, Stile, Felder und Übermittlungsoptionen auswählen können, um ein adaptives Formular zu erstellen. Diese Version bietet die folgenden Verbesserungen für den Assistenten:

   * Auswählen oder Aufheben der Auswahl von Feldern: Mit dem Assistenten können Sie ein adaptives Formular erstellen, das auf JSON und Modellschemata von Formulardaten basiert. Sie können jetzt eine Teilmenge von Feldern innerhalb eines Schemas auswählen, um sie in ein adaptives Formular einzuschließen. Die ausgewählten Felder werden in die entsprechenden Datenerfassungskomponenten für adaptive Formulare konvertiert, um die gewünschten adaptiven Formulare schnell zu erstellen.

   * Verwenden von statischen Vorlagen: Benutzende, die bereits ältere statische Vorlagen erstellt haben, können ihre Umstellung auf die Cloud fortsetzen, indem sie statische Vorlagen im Assistenten zur Erstellung adaptiver Formulare verwenden. Dadurch erhalten die Benutzenden zusätzliche Zeit, um alte statische Vorlagen in moderne bearbeitbare Vorlagen zu migrieren.

* [Entfernen ausgeblendeter Felder aus einem Datensatzdokument (DoR) während der Server-seitigen Verarbeitung](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md): Sie können für Endbenutzende eine PDF-Datei aus Datensatzdokumenten generieren, die nur die Felder enthält, die für sie während der Datenerfassung sichtbar waren. Bei der Formularübermittlung überprüft der Server basierend auf gesendeten Daten, welche Felder für den Endbenutzenden ausgeblendet wurden, und schließt sie aus dem Datensatzdokument aus, um Konsistenz zu gewährleisten.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Zuordnung von AEM-Seiten zu Produkten und Kategorien über AEM-Seiteneigenschaften plus Übersicht im Produkt-Cockpit
   ![Produkt-Cockpit-Seitenzuordnung](/help/assets/CIF/product_cockpit_page_association.png)

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier.](/help/implementing/cloud-manager/release-notes/current.md)

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
