---
title: Versionshinweise für Version 2023.6.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2023.6.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 29cf9548-e413-4e4f-b233-d6bb04918b22
source-git-commit: ecf4c06fd290d250c14386b3135250633b26c910
workflow-type: ht
source-wordcount: '1357'
ht-degree: 100%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2023.6.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2023.6.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2021 oder 2022 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2023.6.0) war der 29. Juni 2023. Die nächste Version (2023.7.0) ist für den 27. Juli 2023 geplant.

## Video zur Version {#release-video}

Eine Zusammenfassung der in der Version 2023.6.0 hinzugefügten Funktionen finden Sie im Übersichtsvideo zur Version Juni 2023:

>[!VIDEO](https://video.tv.adobe.com/v/3420971/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Experience Manager Sites] {#sites-features}

* Inhaltsfragmente und ihre Referenzen können jetzt mithilfe der [Inhaltsfragmentkonsole](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) im [AEM-Vorschau-Service](/help/implementing/cloud-manager/manage-environments.md#access-preview-service) veröffentlicht werden, sodass Benutzerinnen und Benutzer eine Vorschau des endgültigen Erlebnisses in einer entkoppelten Vorschau-App anzeigen können, bevor sie live gehen.

![Vorschau in der Inhaltsfragmentkonsole](/help/assets/content-fragments-console-preview.png)

* Bilder können jetzt dynamisch für die Web-Bereitstellung in Headless-Szenarien mit AEM GraphQL optimiert werden. [Abfragevariablen](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/images.html?lang=de#query-variables) können in GraphQL-Abfragen definiert werden, um zuzulassen, dass entkoppelte Client-Anwendungen entsprechend optimierte Bilder von AEM anfordern können.
* Tags für [Inhaltsfragmentvarianten](https://experienceleague.adobe.com/docs/experience-manager-65/assets/content-fragments/content-fragments-variations.html?lang=de) können jetzt über die Inhaltsbereitstellungs-API von AEM GraphQL an JSON ausgegeben werden.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

**Verfügbarkeit der neuen Assets-Ansicht**

Die [neue Assets-Ansicht](/help/assets/assets-view-introduction.md) ist jetzt in Experience Manager Assets verfügbar. Die vereinfachte Benutzeroberfläche der Assets-Ansicht erleichtert das Verwalten, Erkennen und Verteilen Ihrer digitalen Assets. Das Erlebnis richtet sich an Kreative, Nutzerinnen und Nutzer von schreibgeschützten Assets und einfache DAM-Benutzerinnen und -Benutzer.

![Tagging-Verwaltung](/help/assets/assets/my-workspace.png)

**Verbesserungen des Sucherlebnisses**

Mit Experience Manager Assets können Sie jetzt über die Benutzeroberfläche für Suchergebnisse mehr tun: Sie können jetzt:

* [Standardmäßig wird die Suche innerhalb des aktuellen Repository-Speicherorts durchgeführt](/help/assets/search-assets.md), anstatt im gesamten Repository nach dem Schlüsselwort zu suchen.

* [Navigieren Sie zum Speicherort des Ordners](/help/assets/search-assets.md#aftersearch) für Assets, die in den Suchergebnissen angezeigt werden.

**Vorschau von Miniaturansichten für 3D-Assets**

[!DNL Experience Manager Assets] generiert jetzt eine [Vorschau von Miniaturansichten für gängige 3D-Dateiformate](/help/assets/file-format-support.md), einschließlich gLB, USDz, FBX, 3DS, OBJ und SBSAR. Wenn diese Dateien hochgeladen werden, werden automatisch Miniaturansichten generiert.

**Konfiguration der Link-Freigabe**

Ein neues, verbessertes Benutzererlebnis für das [Erstellen von Link-Freigaben](/help/assets/share-assets.md), zusammen mit einem brandneuen Satz von Konfigurationen, mit denen Admins das Standardverhalten dieser Funktion für Ihre Benutzerinnen und Benutzer anpassen können.

![Tagging-Verwaltung](/help/assets/assets/config-email-service.png)

**Dynamic Media: Aktualisierte Felder für smartes Zuschneiden im Bildprofil**

Die Benutzeroberfläche für einige Felder mit Bezug auf smartes Zuschneiden in einem Bildprofil wurde aktualisiert und spiegelt jetzt die aktuellen Richtlinien zum Definieren eines smarten Zuschnitts wider. Siehe [Optionen für das Zuschneiden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles.html?lang=de#crop-options).

### Neue Funktionen in der Assets-Ansicht {#assets-view-features}

**Hierarchisches Tagging von Assets für ein schnelleres Sucherlebnis**

Flache Listen mit kontrolliertem Vokabular werden im Laufe der Zeit immer unübersichtlicher. Die Assets-Ansicht unterstützt jetzt eine [hierarchische Tagging-Struktur](/help/assets/tagging-management-assets-view.md), was die Anwendung relevanter Metadaten, die Kategorisierung von Assets, die Unterstützung der Suche, die Wiederverwendung von Tags, die Verbesserung der Auffindbarkeit usw. erleichtert.

![Tagging-Verwaltung](/help/assets/assets/tags-hierarchy.png)

**Anheften von Dateien, Ordnern und Sammlungen für schnellen Zugriff**

Sie können jetzt [Dateien, Ordner und Sammlungen für einen schnelleren Zugriff anheften](/help/assets/my-workspace-assets-view.md), wenn sie Sie später benötigen. Die angehefteten Elemente werden im Abschnitt **Schnellzugriff** von „Mein Arbeitsbereich“ angezeigt. Sie können über „Mein Arbeitsbereich“ darauf zugreifen, anstatt zu dem Speicherort zu navigieren, an dem sie im Repository gespeichert sind.

![Aufgaben in Workspace](/help/assets/assets/quick-access.png)

**Filtern von Assets im Papierkorb-Ordner**

Die Assets-Ansicht ermöglicht es Ihnen jetzt, [Assets im Papierkorb-Ordner zu filtern](/help/assets/navigate-assets-view.md). Sie können standardmäßige oder benutzerdefinierte Filter anwenden, um geeignete Assets im Papierkorb-Ordner zu suchen, um sie wiederherzustellen oder dauerhaft zu löschen.

**Vorschau von Miniaturansichten für 3D-Assets**

Die Asset-Ansicht generiert jetzt eine Vorschau für Miniaturansichten für gängige 3D-Dateiformate wie gLB, USDz, FBX, 3DS, OBJ und SBSAR. Wenn diese Dateien in die Assets-Ansicht hochgeladen werden, werden vom System standardmäßig automatisch Miniaturansichten generiert.

![Aufgaben in Workspace](/help/assets/assets/3d-preview.png)

**Anzeigen der am häufigsten gesuchten Begriffe**

Die Assets-Ansicht unterstützt jetzt das [Anzeigen der am häufigsten gesuchten Begriffe in Ihrer Implementierung](/help/assets/my-workspace-assets-view.md) mithilfe des Abschnitt **Einblicke** von „Mein Arbeitsbereich“. Sie können auch zu detaillierten Einblicken navigieren, um die häufigsten Suchbegriffe der letzten 30 Tage oder 12 Monate anzuzeigen.

![Aufgaben in Workspace](/help/assets/assets/insights-top-searches.png)

**Verbesserungen bei Metadaten-Formularen**

Die Assets-Ansicht ermöglicht es Ihnen jetzt, [Eigenschaftenkomponenten von Text und Dropdown-Listen mit mehreren Werten](/help/assets/metadata-assets-view.md#property-components) zu den Metadaten-Formularen hinzuzufügen.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#new-features-available-in-channel}

* [Adaptive Formulare im AEM-Seiteneditor](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md): Sie können jetzt den AEM-Seiteneditor verwenden, um schnell mehrere Formulare zu erstellen und sie zu Ihren Sites-Seiten hinzuzufügen. Diese Funktion ermöglicht es Inhaltsautorinnen und -autoren, nahtlose Datenerfassungserlebnisse innerhalb von Sites-Seiten zu erstellen, indem sie die Möglichkeiten der Komponenten adaptiver Formulare nutzen, einschließlich dynamisches Verhalten, Überprüfungen, Datenintegration, Generierung von Datensatzdokumenten und Automatisierung von Geschäftsprozessen. Sie haben folgende Möglichkeiten:

   * Erstellen Sie ein adaptives Formular, indem Sie Formularkomponenten per Drag-and-Drop in die Container-Komponente für adaptive Formulare im AEM Sites-Editor oder in Experience Fragments ziehen.
   * Verwenden Sie den Assistenten für adaptive Formulare im AEM Sites-Editor, damit Sie unabhängig von einer Sites-Seite Formulare erstellen können. So können Sie solche Formulare auf mehreren Seiten wiederverwenden.
   * Fügen Sie mehrere Formulare zu einer Sites-Seite hinzu, was das Benutzererlebnis optimiert und mehr Flexibilität bietet.

     >[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

* [Adobe Acrobat Sign Solutions für Behörden](/help/forms/adobe-sign-integration-adaptive-forms.md): AEM Forms können jetzt in Adobe Acrobat Sign Solutions für Behörden integriert werden. Diese Integration bietet eine erweiterte Kompatibilität und Sicherheit für E-Signaturen bei Einreichungen von adaptiven Formularen für behördliche Konten (Regierungsstellen und -agenturen).

  Durch die Integration mit Adobe Acrobat Sign Solutions für Behörden können Partner und Regierungskunden von Adobe elektronische Signaturen in adaptiven Formularen für einige der wichtigsten und sensibelsten Geschäftsbereiche verwenden. Diese zusätzliche Sicherheitsschicht stellt sicher, dass alle E-Signaturen vollständig konform mit der Richtlinie „FedRAMP Moderate“ sind, was Regierungskunden von Adobe Gewissheit bietet.

* [Verbesserte Fehlerhandhabung mit benutzerdefinierten Fehler-Handlern im Regeleditor](/help/forms/add-custom-error-handler-adaptive-forms.md): Sie können jetzt eine benutzerdefinierte Funktion (mithilfe der Client-Bibliothek) aufrufen, wenn ein von einem externen Dienst zurückgegebener Fehler auftritt, und eine maßgeschneiderte Antwort für Endbenutzerinnen und -benutzer bereitstellen. Oder Sie können bestimmte Aktionen für Fehler ausführen, die von einem Dienst zurückgegeben werden. Sie können beispielsweise einen benutzerdefinierten Workflow im Back-End für bestimmte Fehler-Codes aufrufen oder die Kundin bzw. den Kunden darüber informieren, dass der Dienst nicht verfügbar ist.

  Diese Funktion hilft bei der Verbesserung Ihrer gesamten Fehlerhandhabung, indem standardbasierte Fehlerantworten eingeführt werden, die abwärtskompatibel mit OOTB-Fehler-Handlern sind, und bietet mehr Flexibilität und Kontrolle.

* [Erweiterte Authentifizierungsmethoden für Formulardatenmodell](/help/forms/configure-data-sources.md): Erleben Sie mehr Sicherheit mit der Einführung einer auf Client-Anmeldedaten basierenden Authentifizierung für die Verbindung von AEM Forms mit kompatiblen Datenquellen. Durch diese Verbesserung entfällt die Notwendigkeit für Identitätswechsel oder Benutzeranmeldung, wodurch der Schutz Ihrer Daten verbessert wird.

* [Adaptive Formulare mit wiederholbaren Abschnitten](/help/forms/create-forms-repeatable-sections.md): Sie können jetzt die Komponenten [Akkordeon](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html?lang=de), [Assistent](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html?lang=de), [Bedienfeld](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html?lang=de) und [horizontale Registerkarten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html?lang=de) in einem auf Kernkomponenten basierenden adaptiven Formular verwenden, um wiederholbare Abschnitte zu erstellen.

  >[!VIDEO](https://video.tv.adobe.com/v/3421052/adaptive-forms-repeatable-sections-repeat-sections/?quality=12&learn=on)

  Mit diesen wiederholbaren Abschnitten können Sie eine unbegrenzte Anzahl von Einträgen ohne feste Feldanzahl bereitstellen. Dies ist nützlich, wenn die erforderlichen Dateninstanzen im Voraus unbekannt sind. Benutzerinnen und Benutzer von Formularen können problemlos Abschnitte hinzufügen oder entfernen, Formulare an verschiedene Dateneingabeszenarien anpassen und die Erfassung mehrfacher Vorkommen derselben Daten vereinfachen.

* **[Senden von adaptiven Formularen an Microsoft® SharePoint und Microsoft® OneDrive](/help/forms/configuring-submit-actions.md)**: Verbessern Sie die Agilität von Business-Anwenderinnen und -Anwendern, neue Formulare schnell zu starten und gesendete Daten in alltäglichen Tools zu speichern, die sie verwenden, wie z. B. die Microsoft® SharePoint-Site oder der OneDrive-Ordner.

### Early-Adopter-Programm für adaptive Headless-Formulare {#forms-early-adopter}

Die Benutzung von [adaptiven Headless-Formularen](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=de) ermöglicht es Entwicklerinnen und Entwicklern, interaktive Formulare zu erstellen, zu veröffentlichen und zu verwalten, für die der Zugriff und die Interaktion über APIs und nicht über eine herkömmliche grafische Benutzeroberfläche möglich ist. Adaptive Headless-Formulare unterstützen Sie bei Folgendem:

* Erstellen hochwertiger Mehrkanal-Formulare in der gewünschten Programmiersprache
* Native Integration von Formularen in Ihre Desktop- und Mobile Apps, Websites und Chat-Anwendungen
* Wiederverwenden Ihrer proprietären UI-Komponenten mit Formularanwendungen
* Nutzung der Leistungsfähigkeit von Adobe Experience Manager Forms

Sie können von Ihrer offiziellen E-Mail-ID eine E-Mail an `aem-forms-headless@adobe.com` senden, um am Early-Adopter-Programm teilzunehmen.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
