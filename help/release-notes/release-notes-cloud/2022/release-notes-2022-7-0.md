---
title: Versionshinweise für Version 2022.7.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2022.7.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: b339ab48-e836-4589-a573-9c50917b9280
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '935'
ht-degree: 27%

---

# Versionshinweise für 20278.0 für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt finden Sie Versionshinweise zu Funktionen für die Version 2022.7.0 von [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2022.7.0) war der Dienstag, 8. August 2022.

Die nächste Version (2022.8.0) ist für den 1. September 2022 geplant.

## Video zur Version {#release-video}

Eine Zusammenfassung der in der Version 2022.7.0 hinzugefügten Funktionen finden Sie im Übersichtsvideo zur Version Juli 2022:

>[!VIDEO](https://video.tv.adobe.com/v/345409/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Sites] {#sites-features}

* Die [Inhaltsfragmentkonsole](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) unterstützt jetzt [Tastaturbefehle](/help/sites-cloud/administering/content-fragments/keyboard-shortcuts.md).

* AEM der Web-optimierten Bildbereitstellung ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/web-optimized-image-delivery.html?lang=de) des Cloud Service ermöglicht eine deutliche Verbesserung der Seitengeschwindigkeit durch die Bereitstellung von Formaten wie WebP. [ Dieser neue Dienst bietet außerdem flexiblere Optionen zur Größenanpassung und Umwandlung von Bildern. In allen Versionen der [Kernbildkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/image.html?lang=de) können Sie diesen Dienst verwenden und Bilder per Klick auf eine Option in der Bildkomponente als WebP bereitstellen.

* AEM Personalisierungsaktivitäten können jetzt Erlebnisfragmente anstelle unserer veralteten Angebote verwenden. Diese Funktion:
   * ermöglicht einen Migrationspfad, bei dem AEM Inhalt anstelle von Legacy-Bibliotheksangeboten Erlebnisfragmentangebote weiterleiten würde, um entsprechend formatierten Inhalt bereitzustellen, der künftig mit der Personalisierung skaliert übereinstimmt.
   * verhindert, dass Inhaltsautoren versehentlich unformatierten Inhalt auf ihrer Site bereitstellen.
   * ermöglicht die Konvertierung des Targeting-Modus einer beliebigen Komponente in ein Experience Fragment (JSON- und HTML-Typ), das bearbeitbare Vorlagen verwendet.

>[!NOTE]
>
>Bestehende Personalisierungsaktivitäten, die bereits Legacy-Angebote verwenden, können dies weiterhin tun, aber neue Personalisierungsaktivitäten sollten als Experience Fragments erstellt werden, da dies der empfohlene Ansatz für die Zukunft ist.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Assets] verfügbar {#prerelease-features-assets}

Sie können Adobe Experience Manager Assets jetzt so konfigurieren, dass der Typ der Assets, die Benutzer hochladen können, anhand des MIME-Typs ](/help/assets/configure-asset-upload-restrictions.md) auf [beschränkt wird.

![Einschränkungen beim Hochladen von Assets](/help/assets/assets/asset-upload-restrictions.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#forms-features}

* **[Unterstützung der Tastatureingabe für Scribble-Signaturen](/help/forms/signing-forms-using-scribble.md)**: Adaptive Forms wird zunehmend auf Touch-Geräten verwendet. Eine gängige Voraussetzung ist die Unterstützung von Signaturen. Das Unterschreiben von Dokumenten auf Touch-Geräten ist zu einer akzeptierten Methode zum Unterschreiben von Formularen geworden. Adaptive Forms bietet native Unterstützung für Scribble-Signaturen und Adobe Sign für solche Anwendungsfälle. Jetzt können Sie zusammen mit anderen bereits unterstützten Optionen auch die Tastatur für Scribble-Signaturen in einem adaptiven Formular verwenden. Darüber hinaus wird die Einhaltung von Vorschriften zur Barrierefreiheit verbessert.

![Unterstützung der Tastatureingabe für Scribble-Signaturen auf iPhone](/help/release-notes/assets/scribble-keyboard-mobile.png)

* **Verwenden Sie den Assistenten für adaptive Forms in Landessprache**: Sie können den Assistenten in einer Sprache Ihrer Wahl verwenden. Es unterstützt jetzt alle von Adobe Experience Manager unterstützten Sprachen.

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Forms] verfügbar {#prerelease-features-forms}

<!-- 

* **[Launch Adaptive Form creation wizard from embed form component](/help/forms/using/embed-adaptive-form-aem-sites.md)**: You can now launch Adaptive Form creation wizard from embed form component. It helps improve content and forms authoring workflows for Sites and Forms practitioners trying to add enrollment experiences to a web page. 

![Keyboard input support for Scribble signatures on iphone](/help/release-notes/assets/froms-container.png) 

-->

* **[DDX aufrufen - Ein AEM Workflow-Schritt](/help/forms/aem-forms-workflow-step-reference.md#invokeddx)**: Document Description XML (DDX) ist eine deklarative Markup-Sprache, deren Elemente Bausteine von Dokumenten darstellen. Diese Bausteine umfassen PDF-Seiten, XDP-Dokumente sowie andere Elemente wie Kommentare, Lesezeichen und formatierten Text. DDX-Dokumente sind Vorlagen für die Dokumente und beschreiben die gewünschten Eigenschaften von Quelldokumenten, die in den Zieldokumenten angezeigt werden sollen. Eine einzelne DDX kann mit einer Reihe von Quelldokumenten verwendet werden. Sie können den Schritt &quot;Aufrufen&quot;und einen AEM Workflow verwenden, um verschiedene Vorgänge auszuführen, z. B. das Zusammenstellen von Dokumenten, das Erstellen und Ändern von Acrobat und XFA Forms sowie andere Vorgänge, die in der Dokumentation [DDX-Referenz](https://helpx.adobe.com/content/dam/help/en/experience-manager/forms-cloud-service/ddxRef.pdf) beschrieben sind.

* **[Nach PDF/A konvertieren - Ein AEM Workflow-Schritt](/help/forms/aem-forms-workflow-step-reference.md##convert-pdfa)**: PDF/A ist ein Archivformat für die langfristige Beibehaltung des Dokumentinhalts, alle Schriftarten werden eingebettet und die Datei ist unkomprimiert. Jetzt können Sie den Schritt In PDF/A konvertieren und einen AEM Workflow verwenden, um Ihre Dokumente oder Dateien in einem beliebigen Format in das PDF/A-Format zu konvertieren.


## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Die Produktkataloganreicherung unterstützt jetzt AEM-Seiten. Dadurch können Autorinnen und Autoren die Zuordnung von Seite und Produkt verwalten.

* Verschiedene Verbesserungen der CIF-Kernkomponenten

### Fehlerbehebungen {#bug-fixes-cif}

* Login-Token zur Client-seitigen Preisabfrage hinzufügen

* Falsche Seitenkomponente in der Datenschicht

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Neue Funktionen {#what-is-new-foundation}

* Der [Repository-Browser](/help/implementing/developing/tools/repository-browser.md) verfügt jetzt über ein Pfadeingabefeld, das es ermöglicht, direkt zu einem bestimmten Ordner in der Repository-Hierarchie zu springen
* Sling Content Distribution (SCD) unterstützt jetzt eine explizite &quot;Invalidierung&quot;, um Inhalte ungültig zu machen, ohne dass dieser Inhalt veröffentlicht wird. Weitere Informationen finden Sie auf der Seite [Caching in AEM as a Cloud Service](/help/implementing/dispatcher/caching.md#explicit-invalidation) .
* mod_macro ist jetzt in AEM as a Cloud Service verfügbar. Eine Liste der unterstützten Apache-Module finden Sie in [dieser Tabelle](/help/implementing/dispatcher/disp-overview.md) .

### AEM as a Cloud Service SDK Dispatcher Tools-Verbesserungen {#dispatcher-tools-enhancements}

* Apache kann mit dem `docker_run_hot_reload.sh` -Skript gestartet werden, das alle nachfolgenden Änderungen an der Apache- und Dispatcher-Konfiguration automatisch lädt und validiert und damit die Entwicklergeschwindigkeit verbessert. Wird nur für den flexiblen Modus der Dispatcher-Tools unterstützt. Weitere Informationen zum automatischen Neuladen und zur Validierung finden Sie unter [Debugging der Apache- und Dispatcher-Konfiguration](/help/implementing/dispatcher/validation-debug.md#automatic-reloading) .
* Die lokale Apache-/Dispatcher-Konfiguration verfolgt Änderungen in Cloud-Umgebungen genauer, wodurch die Parität zwischen den beiden Umgebungen erhöht wird.

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Experience Manager] verfügbar {#prerelease-features-foundation}

* AEM as a Cloud Service ist jetzt in Unified Shell integriert, um das Benutzererlebnis zu verbessern und es mit allen anderen Experience Cloud-Programmen zu vereinheitlichen. Weitere Informationen finden Sie unter [AEM as a Cloud Service unter Unified Shell](/help/overview/aem-cloud-service-on-unified-shell.md) .

## Adobe Learning Manager Connectors {#learn-manage}

* Die neue Adobe Learning Manager verfügt über Connectoren für Adobe Experience Manager Sites, Marketo Engage und Adobe Commerce. Weitere Informationen finden Sie unter: [Adobe Learning Manager-Benutzerhandbuch](https://helpx.adobe.com/learning-manager/user-guide.html).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
