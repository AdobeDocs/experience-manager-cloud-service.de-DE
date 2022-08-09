---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: a3e18349c3cf2240cc68275a3862abeb75ea372a
workflow-type: tm+mt
source-wordcount: '955'
ht-degree: 19%

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

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2022.7.0) war der 8. August 2022.

Die nächste Version (2022.8.0) ist für den 25. August 2022 geplant.

## Video zur Version {#release-video}

Sehen Sie sich das Video Versionsübersicht vom Juli 2022 an, um eine Zusammenfassung der Funktionen zu erhalten, die in der Version 2022.7.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/345409/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Sites] {#sites-features}

* Die [Inhaltsfragmentkonsole](/help/sites-cloud/administering/content-fragments/content-fragments-console.md) unterstützt jetzt [Tastaturbefehle](/help/sites-cloud/administering/content-fragments/content-fragments-console-keyboard-shortcuts.md).

* AEM als Cloud Service [Web-optimierte Bildbereitstellung](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/web-optimized-image-delivery.html) ermöglicht eine deutliche Verbesserung der Seitengeschwindigkeit durch die Bereitstellung von Formaten wie WebP. Dieser neue Dienst bietet außerdem flexiblere Optionen zur Größenanpassung und Umwandlung von Bildern. Alle Versionen der [Kernbildkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/image.html?lang=de) ermöglichen die Nutzung dieses Dienstes und die Bereitstellung von Bildern als WebP durch Klicken auf eine Option in der Richtlinie der Bildkomponente.

* AEM Personalisierungsaktivitäten können jetzt Erlebnisfragmente anstelle von Legacy-Angeboten nutzen. Diese Funktion:
   * ermöglicht einen Migrationspfad, bei dem AEM Inhalt anstelle von Legacy-Bibliotheksangeboten Erlebnisfragmentangebote weiterleiten würde, um entsprechend formatierten Inhalt bereitzustellen, der künftig mit der Personalisierung skaliert übereinstimmt.
   * verhindert, dass Inhaltsautoren versehentlich unformatierten Inhalt auf ihrer Site bereitstellen.
   * ermöglicht die Konvertierung des Targeting-Modus einer beliebigen Komponente in ein Experience Fragment (JSON- und HTML-Typ), das bearbeitbare Vorlagen verwendet.

>[!NOTE]
>
>Bestehende Personalisierungsaktivitäten, die bereits Legacy-Angebote verwenden, können dies weiterhin tun, aber neue Personalisierungsaktivitäten sollten als Experience Fragments erstellt werden, da dies der empfohlene Ansatz für die Zukunft ist.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Assets] verfügbar {#prerelease-features-assets}

Sie können Adobe Experience Manager Assets jetzt so konfigurieren, dass [den Typ der Assets einschränken, die Benutzer basierend auf dem MIME-Typ hochladen können](/help/assets/configure-asset-upload-restrictions.md).

![Einschränkungen beim Asset-Upload](/help/assets/assets/asset-upload-restrictions.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#forms-features}

* **Unterstützung für Tastatureingaben für Scribble-Signaturen**: Adaptive Forms werden zunehmend auf Touch-Geräten verwendet. Eine gängige Voraussetzung ist die Unterstützung von Signaturen. Das Unterschreiben von Dokumenten auf Touch-Geräten ist zu einer akzeptierten Methode zur Unterzeichnung von Formularen geworden. Adaptive Forms bietet native Unterstützung für Scribble-Signaturen und Adobe Sign für solche Anwendungsfälle. Jetzt können Sie zusammen mit anderen bereits unterstützten Optionen auch die Tastatur für Scribble-Signaturen in einem adaptiven Formular verwenden. Darüber hinaus wird die Einhaltung von Barrierefreiheitsregeln verbessert.

![Unterstützung für Tastatureingaben auf Scribble-Signaturen auf dem iPhone](/help/release-notes/assets/scribble-keyboard-mobile.png)

* **Verwenden des Adaptive Forms-Assistenten in der Landessprache**: Sie können den Assistenten in der Sprache Ihrer Wahl verwenden. Es unterstützt jetzt alle von Adobe Experience Manager unterstützten Sprachen.

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Forms] verfügbar {#prerelease-features-forms}

<!-- * **[Launch Adaptive Form creation wizard from embed form component](/help/forms/using/embed-adaptive-form-aem-sites.md)**: You can now launch Adaptive Form creation wizard from embed form component. It helps improve content and forms authoring workflows for Sites and Forms practitioners trying to add enrollment experiences to a web page. 

![Keyboard input support for Scribble signatures on iphone](/help/release-notes/assets/froms-container.png) -->

* **Aufrufen - Ein AEM Workflow-Schritt**: Document Description XML (DDX) ist eine deklarative Markup-Sprache, deren Elemente Bausteine von Dokumenten darstellen. Diese Bausteine umfassen PDF- und XDP-Dokumente sowie andere Elemente wie Kommentare, Lesezeichen und formatierten Text. DDX-Dokumente sind Vorlagen für die Dokumente und beschreiben die gewünschten Eigenschaften von Quelldokumenten, die in den Zieldokumenten angezeigt werden sollen. Ein DDX kann mit einer Reihe von Quelldokumenten verwendet werden. Sie können den Aufrufschritt und einen AEM Workflow verwenden, um verschiedene Vorgänge auszuführen, z. B. das Zusammenstellen von Dokumenten, das Erstellen und Ändern von Acrobat und XFA Forms und andere Vorgänge, die unter [DDX-Referenz](https://helpx.adobe.com/content/dam/help/en/experience-manager/forms-cloud-service/ddxRef.pdf) Dokumentation.

* **Nach PDF/A konvertieren - Ein AEM Workflow-Schritt**: PDF/A ist ein Archivierungsformat für die Langzeitarchivierung des Dokumentinhalts, alle Schriftarten werden eingebettet und die Datei ist unkomprimiert. Jetzt können Sie den Schritt In PDF/A konvertieren und einen AEM Workflow verwenden, um Ihre Dokumente oder Dateien in einem beliebigen Format in das PDF/A-Format zu konvertieren.


## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Die Anreicherung von Produktkatalogen unterstützt jetzt AEM Seiten. Dadurch können Autoren die Zuordnung von Seite und Produkt verwalten.

* Verschiedene Verbesserungen der CIF-Kernkomponenten

### Fehlerbehebungen {#bug-fixes-cif}

* Anmeldetoken zum clientseitigen Preisabruf hinzufügen

* Falsche Seitenkomponente in der Datenschicht

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Neue Funktionen {#what-is-new-foundation}

* Die [Repository-Browser](/help/implementing/developing/tools/repository-browser.md) verfügt jetzt über ein Pfadeingabefeld, das es ermöglicht, direkt zu einem bestimmten Ordner in der Repository-Hierarchie zu springen
* Sling Content Distribution (SCD) unterstützt jetzt die explizite Aktion &quot;Invalidierung&quot;, um Inhalte ungültig zu machen, ohne dass dieser Inhalt veröffentlicht wird. Siehe Abschnitt [Zwischenspeicherung in AEM as a Cloud Service](/help/implementing/dispatcher/caching.md#explicit-invalidation) für weitere Details.
* mod_macro ist jetzt in AEM as a Cloud Service verfügbar. Siehe [diese Tabelle](/help/implementing/dispatcher/disp-overview.md) für eine Liste der unterstützten Apache-Module.

### AEM as a Cloud Service SDK Dispatcher Tools-Verbesserungen {#dispatcher-tools-enhancements}

* Apache kann mit `update_sdk.sh` -Skript, das automatisch alle nachfolgenden Änderungen an der Apache- und Dispatcher-Konfiguration lädt und validiert und so die Geschwindigkeit der Entwickler verbessert. Wird nur für den flexiblen Modus der Dispatcher-Tools unterstützt. Siehe auch [Debuggen der Apache- und Dispatcher-Konfiguration](/help/implementing/dispatcher/validation-debug.md#automatic-loading) für weitere Details zum automatischen Laden und Validieren.
* Die lokale Apache-/Dispatcher-Konfiguration verfolgt Änderungen in Cloud-Umgebungen genauer, was die Parität zwischen den beiden Umgebungen erhöht.

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Experience Manager] verfügbar {#prerelease-features-foundation}

* AEM as a Cloud Service ist jetzt in Unified Shell integriert, um das Benutzererlebnis zu verbessern und es mit allen anderen Experience Cloud-Anwendungen zu vereinheitlichen. Siehe [Auf Unified Shell as a Cloud Service AEM](/help/overview/aem-cloud-service-on-unified-shell.md) für weitere Details.

## Connectoren für Adobe Learning Manager {#learn-manage}

* Der neue Adobe Learning Manager verfügt über Connectoren für Adobe Experience Manager Sites, Marketo Engage und Adobe Commerce. Weitere Informationen finden Sie unter: [Benutzerhandbuch für Adobe Learning Manager](https://helpx.adobe.com/learning-manager/user-guide.html).


## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
