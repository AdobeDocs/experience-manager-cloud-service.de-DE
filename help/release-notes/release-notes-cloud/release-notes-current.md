---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 6d343e539be05a13bb2a3eaeba1da5656dc54f1a
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 23%

---


# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] aktuelle Version (2022.8.0) ist der 1. September 2022.
Die nächste Version (2022.10.0) ist für den 27. Oktober 2022 geplant.

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

* Die [Inhaltsfragmentkonsole](/help/sites-cloud/administering/content-fragments/content-fragments-console.md) bietet Benutzern die Möglichkeit, die Gesamtzahl der Sprachkopien anzuzeigen, die mit einem Inhaltsfragment verknüpft sind. Es wurde ein 1-Klick-Zugriff bereitgestellt, um auch alle Sprachkopien anzuzeigen. Benutzer können die Tabellenansicht auch nach dem Gebietsschema ihrer Interessen filtern.

![Inhaltsfragmentsprachen](/help/release-notes/assets/cfconsole-languages.png)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#features-assets}

* Sie können Adobe Experience Manager Assets jetzt so konfigurieren, dass [den Typ der Assets einschränken, die Benutzer basierend auf dem MIME-Typ hochladen können](/help/assets/configure-asset-upload-restrictions.md).

   ![Einschränkungen beim Asset-Upload](/help/assets/assets/asset-upload-restrictions.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Forms] verfügbar {#prerelease-features-forms}

* [Adaptiver Forms-Assistent](/help/forms/creating-adaptive-form.md): AEM Forms bietet einen benutzerfreundlichen Assistenten für Unternehmen, mit dem sich Adaptive Forms schnell erstellen lässt. Der Assistent verfügt über eine schnelle Registerkartennavigation, mit der Sie einfach vorkonfigurierte Vorlagen, Stile, Felder und Übermittlungsoptionen auswählen können, um ein adaptives Formular zu erstellen. Diese Version bringt die folgenden Verbesserungen am Assistenten:

   * Auswählen oder Aufheben der Auswahl von Feldern: Mit dem Assistenten können Sie ein adaptives Formular erstellen, das auf JSON- und Formulardatenmodellschemata basiert. Sie können jetzt eine Teilmenge von Feldern innerhalb eines Schemas auswählen, um sie in ein adaptives Formular einzuschließen. Die ausgewählten Felder werden in die entsprechenden Datenerfassungskomponenten für adaptive Formulare konvertiert, um die gewünschten adaptiven Formulare schnell zu erstellen.

   * Statische Vorlagen verwenden: Kunden, die bereits in ältere statische Vorlagen investiert haben, können ihre Journey der Cloud-Akzeptanz fortsetzen, indem sie statische Vorlagen im Assistenten verwenden, um adaptive Formulare zu erstellen. Dadurch erhalten Kunden zusätzliche Zeit, alte statische Vorlagen in moderne bearbeitbare Vorlagen zu migrieren.

* [Entfernen ausgeblendeter Felder aus einem Datensatzdokument (DoR) bei der serverseitigen Verarbeitung](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md): Sie können das Datensatzdokument-PDF für Endbenutzer generieren, die nur die Felder enthalten, die für sie während der Datenerfassung sichtbar waren. Bei Formularübermittlung überprüft der Server, welche Felder dem Endbenutzer basierend auf gesendeten Daten ausgeblendet wurden, und schließt sie aus dem Datensatzdokument aus, um Konsistenz zu gewährleisten.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Zuordnung AEM Seiten zu Produkten und Kategorien über AEM Seiteneigenschaften plus Übersicht im Produkt-Cockpit
   ![Produktcockpit-Seitenzuordnung](/help/assets/CIF/product_cockpit_page_association.png)

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
