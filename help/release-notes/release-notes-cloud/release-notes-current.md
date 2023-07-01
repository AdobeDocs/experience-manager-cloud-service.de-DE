---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 5a37f237d04d19f3c4113c2ea3e37ab447bf3b0c
workflow-type: tm+mt
source-wordcount: '1372'
ht-degree: 16%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen wie 2021 oder 2022 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] Die aktuelle Version der Funktion (2023.6.0) ist der 29. Juni 2023. Die nächste Version der Funktion (2023.7.0) ist für den 27. Juli 2023 geplant.

## Video zur Version {#release-video}

Eine Zusammenfassung der in der Version 2023.6.0 hinzugefügten Funktionen finden Sie im Übersichtsvideo zur Version Juni 2023:

>[!VIDEO](https://video.tv.adobe.com/v/3420971/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Experience Manager Sites] {#sites-features}

* Inhaltsfragmente und ihre Referenzen können jetzt in der [AEM-Vorschaudienst](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments.html?lang=en#access-preview-service) mithilfe der [Inhaltsfragmentkonsole](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html?lang=en), sodass Benutzer eine Vorschau des finalen Erlebnisses in einer entkoppelten Vorschau-App anzeigen können, bevor sie live gehen.
* Bilder können jetzt dynamisch für die Web-Bereitstellung in Headless-Szenarien mit AEM GraphQL optimiert werden. [Abfragevariablen](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/images.html?lang=en#query-variables) kann in GraphQL-Abfragen definiert werden, um entkoppelte Clientanwendungen zu ermöglichen, entsprechend optimierte Bilder von AEM anzufordern.
* Tags auf [Inhaltsfragmentvarianten](https://experienceleague.adobe.com/docs/experience-manager-65/assets/content-fragments/content-fragments-variations.html?lang=en) kann jetzt über die AEM GraphQL Content Delivery API an JSON ausgegeben werden.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

**Verfügbarkeit der Ansicht &quot;New Assets&quot;**

Die [neue Asset-Ansicht](/help/assets/assets-view-introduction.md) ist jetzt in Experience Manager Assets verfügbar. Die Asset-Ansicht bietet eine vereinfachte Benutzeroberfläche, die die Verwaltung, Erkennung und Verteilung digitaler Assets erleichtert. Das Erlebnis richtet sich an Kreative, schreibgeschützte Asset-Verbraucher und einfache DAM-Benutzer.

![Tagging-Verwaltung](/help/assets/assets/my-workspace.png)

**Verbesserungen bei der Suche**

Mit Experience Manager Assets können Sie jetzt über die Benutzeroberfläche für Suchergebnisse mehr tun: Sie können jetzt:

* Führen Sie standardmäßig eine Suche innerhalb des aktuellen Repository-Speicherorts durch, anstatt nach dem Keyword im gesamten Repository zu suchen.

* Navigieren Sie zum Ordnerspeicherort für Assets, die in den Suchergebnissen angezeigt werden.

**Miniaturansichten für 3D-Assets**

[!DNL Experience Manager Assets] generiert [Miniaturansichten für gängige 3D-Dateiformate](/help/assets/file-format-support.md) einschließlich gLB, USDz, FBX, 3DS, OBJ und SBSAR. Wenn diese Dateien hochgeladen werden, werden automatisch Miniaturansichten generiert.

**Konfiguration der Linkfreigabe**

Ein neues verbessertes Benutzererlebnis für [Erstellen von Linkfreigaben](/help/assets/share-assets.md) zusammen mit einem brandneuen Satz von Konfigurationen, mit denen Administratoren das Standardverhalten dieser Funktion für Ihre Benutzer anpassen können.

![Tagging-Verwaltung](/help/assets/assets/config-email-service.png)

**Dynamic Media: Aktualisierte Felder für smartes Zuschneiden im Bildprofil**

Die Benutzeroberfläche für einige Felder mit Bezug auf smartes Zuschneiden in einem Bildprofil wird jetzt aktualisiert und spiegelt die aktuellen Richtlinien zum Definieren eines smarten Zuschnitts wider. Siehe [Optionen für das Zuschneiden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles.html?lang=en#crop-options).

### Neue Funktionen in der Asset-Ansicht {#assets-view-features}

**Hierarchisches Tagging von Assets für schnelleres Sucherlebnis**

Einfache Listen kontrollierter Vokabeln werden im Laufe der Zeit nicht mehr zu handhaben. Die Asset-Ansicht unterstützt jetzt [Hierarchische Tagging-Struktur](/help/assets/tagging-management-assets-view.md), was die Anwendung relevanter Metadaten, die Kategorisierung von Assets, die Unterstützung der Suche, die Wiederverwendung von Tags, die Verbesserung der Auffindbarkeit usw. erleichtert.

![Tagging-Verwaltung](/help/assets/assets/tags-hierarchy.png)

**Dateien, Ordner und Sammlungen für den schnellen Zugriff fixieren**

Sie können jetzt [Pin-Dateien, Ordner und Sammlungen für schnelleren Zugriff](/help/assets/my-workspace-assets-view.md) zu diesen Elementen hinzu, wenn Sie sie später benötigen. Die fixierten Elemente werden im **Schnellzugriff** Abschnitt &quot;Mein Arbeitsbereich&quot;. Sie können über den Arbeitsbereich darauf zugreifen, anstatt zu dem Speicherort zu navigieren, an dem sie im Repository gespeichert sind.

![Aufgaben in Workspace](/help/assets/assets/quick-access.png)

**Filtern von Assets im Ordner &quot;Papierkorb&quot;**

Die Asset-Ansicht ermöglicht jetzt Folgendes: [Filtern von Assets, die im Ordner &quot;Papierkorb&quot;verfügbar sind](/help/assets/navigate-assets-view.md). Sie können standardmäßige oder benutzerdefinierte Filter anwenden, um geeignete Assets im Ordner &quot;Papierkorb&quot;zu suchen, um sie wiederherzustellen oder dauerhaft zu löschen.

**Miniaturansichten für 3D-Assets**

Die Asset-Ansicht generiert jetzt eine Miniaturansicht für gängige 3D-Dateiformate wie gLB, USDz, FBX, 3DS, OBJ und SBSAR. Wenn diese Dateien in die Asset-Ansicht hochgeladen werden, werden vom System standardmäßig automatisch Miniaturansichten generiert.

![Aufgaben in Workspace](/help/assets/assets/3d-preview.png)

**Anzeigen der am häufigsten gesuchten Begriffe**

Die Asset-Ansicht unterstützt jetzt [Anzeigen der am häufigsten gesuchten Begriffe in Ihrer Implementierung](/help/assets/my-workspace-assets-view.md) mithilfe der **Insights** Abschnitt &quot;Mein Arbeitsbereich&quot;. Sie können auch zu detaillierten Insights navigieren, um die wichtigsten Suchvorgänge der letzten 30 Tage oder 12 Monate anzuzeigen.

![Aufgaben in Workspace](/help/assets/assets/insights-top-searches.png)

**Verbesserungen bei Metadatenformularen**

Die Asset-Ansicht ermöglicht jetzt Folgendes: [Mehrwert-Text und Dropdown-Listen-Eigenschaftenkomponenten hinzufügen](/help/assets/metadata-assets-view.md#property-components) zu den Metadatenformularen.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#new-features-available-in-channel}

* [Adaptives Forms in AEM Seiteneditor und Experience Fragment](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md): Sie können jetzt AEM Seiteneditor und Experience Fragment verwenden, um schnell mehrere Formulare zu Ihren AEM Sites-Seiten zu erstellen und hinzuzufügen. Diese Funktion ermöglicht es Inhaltsautoren, nahtlose Datenerfassungserlebnisse innerhalb von Sites-Seiten zu erstellen, indem sie adaptive Forms-Komponenten wie dynamisches Verhalten, Überprüfungen, Datenintegration, Generierung von Datensatzdokumenten und Automatisierung von Geschäftsprozessen nutzen.

      >[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&amp;learn=on)
  
* [Verwenden von Adobe Acrobat Sign Solutions for Government (HIPPA-Beschwerde) mit AEM Forms](/help/forms/adobe-sign-integration-adaptive-forms.md): AEM Forms ist jetzt in Adobe Acrobat Sign Solutions für Regierungsbehörden integriert. Diese Integration bietet eine erweiterte Kompatibilität und Sicherheit für e-Signaturen mit adaptiven Formularen für staatlich verbundene Konten (Regierungsabteilungen und Behörden).

  Durch die Integration mit Adobe Acrobat Sign Solutions for Government können Partner und Regierungskunden der Adobe elektronische Signaturen in Adaptive Forms für einige der wichtigsten und sensibelsten Geschäftsbereiche verwenden. Diese zusätzliche Sicherheitsschicht stellt sicher, dass alle E-Signaturen vollständig mit der Einhaltung der FedRAMP Moderate-Richtlinien konform sind, was den Regierungskunden der Adobe einen gesunden Menschenverstand verschafft.

* [Verbesserte Fehlerbehebung mit benutzerdefinierten Fehler-Handlern im Regeleditor](/help/forms/add-custom-error-handler-adaptive-forms.md): Sie können jetzt eine benutzerdefinierte Funktion (mithilfe der Client-Bibliothek) aufrufen, wenn ein von einem externen Dienst zurückgegebener Fehler auftritt, und eine maßgeschneiderte Antwort für Endbenutzer bereitstellen. Sie können auch bestimmte Aktionen für Fehler ausführen, die von einem Dienst zurückgegeben werden. Sie können beispielsweise einen benutzerdefinierten Workflow im Backend für bestimmte Fehlercodes aufrufen oder den Kunden darüber informieren, dass der Dienst ausgefallen ist.

  Diese Funktion hilft bei der Verbesserung Ihrer gesamten Fehlerbearbeitungsfunktion, indem standardbasierte Fehlerantworten eingeführt werden, die abwärtskompatibel mit OOTB-Fehler-Handlern sind, und bietet mehr Flexibilität und Kontrolle.

* [Erweiterte Authentifizierungsmethoden für Formulardatenmodell](/help/forms/configure-data-sources.md): Erfahren Sie mehr Sicherheit mit der Einführung einer Client-Anmeldedaten-basierten Authentifizierung, um AEM Forms (Formulardatenmodelle) mit kompatiblen Datenquellen zu verbinden. Durch diese Verbesserung entfällt der Bedarf an Identitätswechsel oder Benutzeranmeldung, wodurch der Schutz Ihrer Daten verbessert wird.

* [Adaptive Forms mit wiederholbaren Abschnitten erstellen](/help/forms/create-forms-repeatable-sections.md): Sie können jetzt [Akkordeon](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion.html), [Assistent](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard.html), [Bedienfeld](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel-container.html)und [Horizontale Registerkarten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs.html) Komponenten in einem auf Kernkomponenten basierenden adaptiven Formular verwenden, um wiederholbare Abschnitte zu erstellen.

  >[!VIDEO](https://video.tv.adobe.com/v/3421052/adaptive-forms-repeatable-sections-repeat-sections/?quality=12&learn=on)

  Mit diesen wiederholbaren Abschnitten können Sie eine unbegrenzte Anzahl von Einträgen ohne feste Feldanzahl bereitstellen. Dies ist nützlich, wenn die erforderlichen Dateninstanzen im Voraus unbekannt sind. Forms-Benutzer können problemlos Abschnitte hinzufügen oder entfernen, Formulare an verschiedene Dateneingabeszenarien anpassen und die Erfassung mehrerer Vorkommen derselben Daten vereinfachen.

* **[Senden Sie Adaptive Forms an Microsoft® SharePoint und Microsoft® OneDrive](/help/forms/configuring-submit-actions.md)**: Sie können jetzt adaptive Forms-Daten an alltägliche Tools wie Microsoft® SharePoint Site oder Microsoft® OneDrive senden.

### Early-Adopter-Programm für adaptive Headless-Formulare {#forms-early-adopter}

Verwendung [Headless Adaptive Forms](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=de) , damit Ihre Entwickler interaktive Formulare erstellen, veröffentlichen und verwalten können, auf die über APIs und nicht über eine herkömmliche grafische Benutzeroberfläche zugegriffen und mit denen interagiert werden kann. Adaptive Headless-Formulare unterstützen Sie bei Folgendem:

* Erstellen hochwertiger Mehrkanal-Formulare in der gewünschten Programmiersprache
* Native Integration von Formularen in Ihre Desktop- und Mobile Apps, Websites und Chat-Anwendungen
* Wiederverwenden Ihrer proprietären UI-Komponenten mit Formularanwendungen
* Nutzung der Leistungsfähigkeit von Adobe Experience Manager Forms

Sie können eine E-Mail an senden `aem-forms-headless@adobe.com` von Ihrer offiziellen E-Mail-ID, um dem frühen Adopter-Programm beizutreten.


## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
