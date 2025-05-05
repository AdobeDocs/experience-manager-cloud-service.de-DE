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

# Versionshinweise zu 202278.0 für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den Funktionen der Version 2022.7.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

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

* AEM as a Cloud Service [Web-optimierte Bildbereitstellung](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/web-optimized-image-delivery.html?lang=de) ermöglicht es, die Seitengeschwindigkeit durch die Bereitstellung von Formaten wie WebP erheblich zu verbessern. Dieser neue Service bietet außerdem flexiblere Optionen zur Größenanpassung und Umwandlung von Bildern. In allen Versionen der [Kernbildkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/image.html?lang=de) können Sie diesen Service verwenden und Bilder als WebP durch Klicken auf eine Option in der Richtlinie der Bildkomponente bereitstellen.

* AEM-Personalisierungsaktivitäten können jetzt Experience Fragments anstelle unserer veralteten Angebote verwenden. Diese Funktion:
   * ermöglicht einen Migrationspfad, bei dem AEM-Inhalte Experience Fragment-Angebote anstelle der veralteten Bibliotheksangebote fördern, um entsprechend gestaltete Inhalte bereitzustellen, die mit der künftigen Personalisierung in Einklang stehen.
   * verhindert, dass Inhaltsautorinnen und -autoren versehentlich unformatierte Inhalte auf ihrer Website bereitstellen.
   * ermöglicht die Konvertierung des Targeting-Modus einer beliebigen Komponente in ein Experience Fragment (sowohl JSON- als auch HTML-Typen), das bearbeitbare Vorlagen verwendet.

>[!NOTE]
>
>Bestehende Personalisierungsaktivitäten, die bereits veraltete Angebote verwenden, können dies weiterhin tun, aber neue Personalisierungsaktivitäten sollten als Experience Fragments erstellt werden, da dies der empfohlene Ansatz für die Zukunft ist.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Assets] verfügbar {#prerelease-features-assets}

Sie können Adobe Experience Manager Assets jetzt so konfigurieren[ dass der Typ der Assets, die Benutzerinnen und Benutzer hochladen können, auf der Grundlage des MIME-Typs eingeschränkt ](/help/assets/configure-asset-upload-restrictions.md).

![Einschränkungen beim Hochladen von Assets](/help/assets/assets/asset-upload-restrictions.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#forms-features}

* **[Unterstützung für Tastatureingaben für Scribble-Signaturen](/help/forms/signing-forms-using-scribble.md)**: Adaptive Forms werden zunehmend auf Touch-Geräten verwendet. Eine gängige Voraussetzung dabei ist die Unterstützung von Signaturen. Das Signieren von Dokumenten auf Touch-Geräten hat sich als gängige Methode zum Signieren von Formularen etabliert. Adaptive Forms bietet native Unterstützung für Scribble-Signaturen und Adobe Sign für solche Anwendungsfälle. Jetzt können Sie neben anderen bereits unterstützten Optionen auch die Tastatur verwenden, um Freihandsignaturen in einem adaptiven Formular zu verfassen. Dies trägt auch zur Verbesserung der Barrierefreiheit bei.

![Unterstützung für Tastatureingaben für Scribble-Signaturen auf dem iPhone](/help/release-notes/assets/scribble-keyboard-mobile.png)

* **Verwenden des Assistenten für adaptive Forms in der Landessprache**: Sie können den Assistenten in der Sprache Ihrer Wahl verwenden. Es werden nun alle von Adobe Experience Manager unterstützten Sprachen unterstützt.

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Forms] verfügbar {#prerelease-features-forms}

<!-- 

* **[Launch Adaptive Form creation wizard from embed form component](/help/forms/using/embed-adaptive-form-aem-sites.md)**: You can now launch Adaptive Form creation wizard from embed form component. It helps improve content and forms authoring workflows for Sites and Forms practitioners trying to add enrollment experiences to a web page. 

![Keyboard input support for Scribble signatures on iphone](/help/release-notes/assets/froms-container.png) 

-->

* **[DDX aufrufen - Ein AEM-Workflow-Schritt](/help/forms/aem-forms-workflow-step-reference.md#invokeddx)**: Dokumentbeschreibungs-XML (DDX) ist eine deklarative Markup-Sprache, deren Elemente Bausteine von Dokumenten darstellen. Diese Bausteine umfassen PDF-Seiten, XDP-Dokumente sowie andere Elemente wie Kommentare, Lesezeichen und formatierten Text. DDX-Dokumente sind Vorlagen für die Dokumente und beschreiben die gewünschten Eigenschaften von Quelldokumenten, die in den Zieldokumenten angezeigt werden sollen. Eine einzelne DDX kann mit einer Reihe von Quelldokumenten verwendet werden. Sie können den Schritt zum Aufrufen eines AEM-Workflows verwenden, um verschiedene Vorgänge auszuführen, z. B. das Zusammenstellen von Dokumenten, das Erstellen und Ändern von Acrobat und XFA Forms und andere Vorgänge, die in der Dokumentation [DDX-Referenz](https://helpx.adobe.com/content/dam/help/en/experience-manager/forms-cloud-service/ddxRef.pdf) beschrieben sind.

* **[Nach PDF/A konvertieren - Ein AEM-Workflow-Schritt](/help/forms/aem-forms-workflow-step-reference.md##convert-pdfa)**: PDF/A ist ein Archivierungsformat für die Langzeitarchivierung des Dokumentinhalts, bei dem alle Schriftarten eingebettet sind und die Datei unkomprimiert ist. Jetzt können Sie den Schritt Nach PDF/A konvertieren in einem AEM-Workflow verwenden, um Ihre Dokumente oder Dateien in jedem Format in das PDF/A-Format zu konvertieren.


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
* Sling Content Distribution (SCD) unterstützt jetzt eine explizite Aktion zur „Invalidierung“, um Inhalte ungültig zu machen, ohne dass diese Inhalte veröffentlicht werden. Weitere [ finden Sie auf ](/help/implementing/dispatcher/caching.md#explicit-invalidation) Seite „Caching in AEM as a Cloud Service&quot;.
* mod_macro ist jetzt in AEM as a Cloud Service verfügbar. In [dieser Tabelle](/help/implementing/dispatcher/disp-overview.md) finden Sie eine Liste der unterstützten Apache-Module.

### Verbesserungen an AEM as a Cloud Service SDK Dispatcher-Tools {#dispatcher-tools-enhancements}

* Apache kann mit `docker_run_hot_reload.sh` Skript gestartet werden, das alle nachfolgenden Änderungen an der Apache- und Dispatcher-Konfiguration automatisch lädt und validiert, was die Geschwindigkeit der Entwicklung erhöht. Wird nur für den flexiblen Modus der Dispatcher-Tools unterstützt. Siehe auch [Debuggen der Apache- und Dispatcher-Konfiguration](/help/implementing/dispatcher/validation-debug.md#automatic-reloading) für weitere Informationen zum automatischen Neuladen und Validieren.
* Die lokale Apache-/Dispatcher-Konfiguration verfolgt Änderungen in Cloud-Umgebungen genauer und erhöht so die Parität zwischen den beiden Umgebungen.

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Experience Manager] verfügbar {#prerelease-features-foundation}

* AEM as a Cloud Service ist jetzt in Unified Shell integriert, um das Benutzererlebnis zu verbessern und es mit allen anderen Experience Cloud-Programmen zu vereinheitlichen. Weitere Informationen finden Sie unter [AEM as a Cloud Service ](/help/overview/aem-cloud-service-on-unified-shell.md) Unified Shell.

## Adobe Learning Manager-Connectoren {#learn-manage}

* Der neue Adobe Learning Manager verfügt über Connectoren für Adobe Experience Manager Sites, Marketo Engage und Adobe Commerce. Weitere Informationen finden Sie unter: [Adobe Learning Manager-Benutzerhandbuch](https://helpx.adobe.com/de/learning-manager/user-guide.html).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
