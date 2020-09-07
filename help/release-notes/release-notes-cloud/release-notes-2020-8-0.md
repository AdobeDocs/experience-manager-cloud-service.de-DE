---
title: Versionshinweise für die Version 2020.8.0 [!DNL Adobe Experience Manager] von als Cloud Service.
description: '[!DNL Adobe Experience Manager] als Cloud Service-Versionshinweise für 2020.8.0.'
translation-type: tm+mt
source-git-commit: 5a3a8638bbb9fc8c0b28929bcc9c91c404d608d3
workflow-type: tm+mt
source-wordcount: '1058'
ht-degree: 12%

---


# Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service 2020.8.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager as a Cloud Service 2020.8.0 beschrieben.

## Veröffentlichungsdatum {#release-date}

The release date for [!DNL Experience Manager] as a Cloud Service 2020.8.0 is August 27, 2020.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### What is new in [!DNL Sites] {#what-is-new-sites}

* Möglichkeit, Seiten und Unterseiten (Seitenbäume) auf eine frühere Version [wiederherzustellen](/help/sites-cloud/authoring/features/page-versions.md#reinstating-versions).

* Möglichkeit, Launches [in AEM](/help/sites-cloud/authoring/launches/overview.md) SPA-Editor zu [erstellen.](/help/implementing/developing/spa/introduction.md)

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### What is new in [!DNL Assets] {#what-is-new-assets}

* Die Videotranskodierung wird jetzt mit Asset-Mikrodiensten unterstützt. Im Anzeigebereich &quot; [!UICONTROL Verarbeitungsvorgänge für Profile] &quot;finden Sie einen neuen Abschnitt zur Video-Bitrate und -Dimensionen (das Ausgabeformat ist MP4 mit H.264-Codec). For details, see [manage video assets](/help/assets/manage-video-assets.md#transcode-video). Für weitere Transkodierungsoptionen und Video-Versand- [!DNL Dynamic Media] Add-On können verwendet werden.

* Bei neuen [!DNL Experience Manager Assets] Bereitstellungen ist die Funktion für intelligentes Tagging jetzt standardmäßig konfiguriert. Die manuelle Integration mit [!DNL Adobe Developer Console]ist nicht erforderlich. Bei vorhandenen Implementierungen [konfigurieren Administratoren wie bisher die Integration](/help/assets/smart-tags-configuration.md#aio-integration) von Smarttags.

* Eine neue [Asset-Download-Erfahrung](/help/assets/download-assets-from-aem.md) ermöglicht,

   * Asynchroner Download für große Downloads, damit die Benutzer nicht warten müssen.

   * Eine neue modulare API für Entwicklererweiterbarkeit.

* [!DNL Experience Manager] hat die Leistung der Metadaten-Extraktion für Asset-Mikrodienste verbessert. Sie erhöht den Gesamtdurchsatz der Asset-Erfassung.

* Verwenden Sie Process Profil, um benutzerdefinierte Metadaten mit dem Compute Service zu generieren. Siehe [Benutzerdefinierte Metadaten mithilfe des Verarbeitungs-Profils](/help/assets/manage-metadata.md#metadata-compute-service)

* Eine einfachere Download-Funktion für Brand Portal-Benutzer, die von Administratoren konfiguriert werden können. Siehe Überblick über [das Herunterladen](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/whats-new.html#download-configurations).

* Im Markenportal sind jetzt native und hochwertige PDF-Dokument-Vorschauen verfügbar. Siehe Übersicht über den [Dokument-Viewer](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/whats-new.html#doc-viewer).

* Sie können jetzt den CDN (Content Versand Network)-Cache direkt von [!DNL Dynamic Media] in AEM als Cloud Service ungültig machen (im Gegensatz zur Verwendung [!DNL Dynamic Media Classic]), um sicherzustellen, dass die neuesten Assets innerhalb von Minuten statt stundenweise bereitgestellt werden. Siehe [Ungültigmachen des CDN-Cache über dynamische Medien](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md)

* Die Benutzeroberflächensteuerelemente, Navigation, Durchsuchen und Sucherfahrung in [!DNL Assets]werden jetzt noch besser unterstützt.

   * Wenn Sie nach Auswahl der Option [!UICONTROL Hinzufügen Darstellung] die Escape-Taste drücken, kehrt der Fokus zur Symbolleiste zurück. <!-- via CQ-4293594-->
   * Der Tastaturfokus funktioniert wie erwartet, wenn das Kombinationsfeld &quot;E-Mail&quot;verwendet wird. <!-- via CQ-4286215 -->
   * Die Akkordeonelemente im Abschnitt &quot;Filter suchen&quot;werden als standardmäßige erweiterbare Akkordeons interpretiert. <!-- via CQ-4273103 -->
   * Beim Anwenden eines Tags auf ein Asset werden Tags im Dialogfeld als drei Elemente angezeigt. ARIA-Attribute werden auf die Bausteinelemente angemessen angewendet, damit sie jetzt verfügbar sind. <!-- via CQ-4272964 -->

* [!DNL AEM Desktop app] Version 2.0.3 ist jetzt verfügbar, was die Kompatibilität mit [!DNL AEM] 6.5.5 verbessert [!DNL Service Pack] und die Client OS-Kompatibilitätsversion aktualisiert (Entfernen von [!DNL Windows] 7 und [!DNL MacOS] Versionen vor 10.14).

### Fehlerbehebungen in [!DNL Assets] {#bugs-fixed}

* Die Option &quot;Relate&quot;und &quot;Disrelation&quot;reagiert nicht, wenn zum ersten Mal darauf geklickt wird. (CQ-4299022)
* Wenn Sie beim Herunterladen eines Assets die Option zum Empfangen des Assets per E-Mail auswählen, wird die E-Mail nicht gesendet. (CQ-4299146)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neuerungen {#what-is-new-commerce}

* Die Funktion Produktkonsole ist jetzt verfügbar. Auf diese Weise können Marketingexperten/Autoren in AEM Ansicht und Navigation in Kategorien und Produkten durchführen, die im Commerce-Backend gespeichert sind. Die Produktkonsole unterstützt auch Eigenschaften für Kategorien und Produkte.

* Produkt- und Kategorie-Picker wurden verbessert, damit Marketingexperten Produkte über SKU auswählen oder Kategorien über Kategorien-ID auswählen können.

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Die [!UICONTROL Cloud Manager]-Version 2020.8.0 wurde am 06. August 2020 veröffentlicht.

### Neuerungen {#what-is-new-cloud-manager}

* Content Audit ist eine Funktion, die auf den Produktionslinien der Cloud Manager-Sites aktiviert ist. Die Konfiguration der Produktionspipeline für Programm mit Sites enthält jetzt eine dritte Registerkarte mit dem Namen **Content Audit**. Bei jeder Ausführung einer Produktions-Pipeline wird nach benutzerdefinierten Funktionstests ein neuer Content-Audit-Schritt in die Pipeline aufgenommen, der die Site anhand einer Reihe von Dimensionen wie Leistung, SEO (Suchmaschinenoptimierung), Barrierefreiheit, Best Practices und PWA (Progressive Web App) bewertet.

   >[!NOTE]
   >Content Audit wurde seither in Experience Audit umbenannt.

   Refer to [Experience Audit Testing](/help/implementing/cloud-manager/experience-audit-testing.md) for more details.

* Neu erstellte Umgebung in Assets-Programmen werden jetzt automatisch mit Smart Content Services konfiguriert.

* Hibernated-Umgebung können auf der Seite &quot; **Übersicht** &quot;von Cloud Manager entfernt werden.

* Möglichkeit zur Durchführung von Erlebnisprüfungen auf Seiten, powered by Google Lighthouse. Im Rahmen der Cloud Manager-Pipeline können bis zu 25 Seiten überprüft und anhand von Erlebnis-KPIs validiert werden. Die Ergebnisse werden in der Benutzeroberfläche von Cloud Manager angezeigt.

### Fehlerbehebungen {#bug-fixes-cm}

* Einige unnötige und unerwünschte SonarQube-Plug-ins wurden im Rahmen der Überprüfung der Codequalität ausgeführt.

* Auf der Seite zur Ausführung der Pipeline wurde der Verzweigungsname falsch formatiert.

* In einigen Fällen wurden abgeschlossene Pipeline-Ausführungen nicht erfolgreich als abgeschlossen aufgezeichnet, wodurch neue Ausführungen der Pipeline verhindert wurden.

* Pipeline-Ausführungen blieben gelegentlich aufgrund interner Kommunikationsprobleme *stecken*.

* Bei der Bereitstellung einer neuen Organisation erhielten einige Benutzer mit Administratorrollen, die keine Systemadministratoren waren, fälschlicherweise Zugriff auf Cloud Manager.

* Unter bestimmten Umständen wurde der Aktualisierungsindexauftrag mehrmals parallel gestartet, was zu einem Bereitstellungsfehler führte.

* Die QuickInfo auf den Programmkarten war nicht immer korrekt.

* Die Benutzeroberfläche erlaubte irrtümlicherweise den Versuch, Vorgänge auf einer Umgebung auszuführen, während diese gelöscht wurde.

* There was a color mismatch on the Cloud Manager&#39;s **Overview** page.

### Bekannte Probleme {#known-issues-cm}

* Es sind ungültige Seiten enthalten, die die durchschnittliche Inhaltsprüfung unter den gewünschten Werten bringen.

* Auf der Registerkarte &quot;Content Audit&quot;wird die Basis-URL fälschlicherweise unter Verwendung der Autorendomäne anstelle der Veröffentlichungsdomäne angezeigt.

* Um den Schritt &quot;Content Audit&quot;zu aktivieren, müssen Benutzer die Pipeline bearbeiten und optional Seiten hinzufügen. Wenn keine Seiten hinzugefügt werden, wird die Homepage geprüft.

## Content Transfer-Tool {#content-transfer-tool}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für Content Transfer Tool Version 1.0.4.

### Neuerungen {#what-is-new-ctt}

* Content Transfer Tool unterstützt jetzt den freigegebenen S3 DataStore.

### Fehlerbehebungen {#ctt-bug-fixes}

* Zusätzliche Timeouts, die hinzugefügt wurden, damit das Tool Aktionen abschließen kann.

* In früheren Versionen der Benutzeroberfläche wurde manchmal eine erfolgreiche Extraktion angezeigt, obwohl Fehler im Protokoll auftraten.

## Code-Refaktorierungs-Tools {#code-refactoring-tools}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für die Code Refactoring Tools.

### Neuerungen {#what-is-new-refactoring}

* Das AIO-CLI-Plugin wurde veröffentlicht, um Code-Refactoring-Tools zu vereinheitlichen, damit Entwickler Code-Refactoring-Tools von einem Ort aus aufrufen und ausführen können. Refer to [Git Resource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) for more details.

* AEM Dispatcher Converter wurde erweitert, um Konvertierungen von On-Premise- und Adobe Managed Services Dispatcher-Konfigurationen in AEM als Cloud Service-kompatible Dispatcher-Konfigurationen zu unterstützen. Siehe [Git-Ressource: AEM Cloud Service Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) .

* AEM Dispatcher Converter neu geschrieben ` node.js ` und mit dem AIO-CLI Plugin integriert.
