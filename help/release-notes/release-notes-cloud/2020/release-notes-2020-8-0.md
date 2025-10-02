---
title: Versionshinweise für Version 2020.8.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2020.8.0
exl-id: 83413130-ae90-4419-bcf7-42fdc740452b
feature: Release Information
role: Admin
source-git-commit: 2aea79d42ef9627a8fc758077a7ee012592888d7
workflow-type: tm+mt
source-wordcount: '1031'
ht-degree: 92%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2020.8.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager as a Cloud Service 2020.8.0 beschrieben.


## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Neue Funktionen in [!DNL Sites] {#what-is-new-sites}

* Möglichkeit der [Wiederherstellung einer früheren Version von Seiten und Unterseiten (Seitenbäume)](/help/sites-cloud/authoring/sites-console/page-versions.md#reinstating-versions).

* Möglichkeit zum [Erstellen von Launches](/help/sites-cloud/authoring/launches/overview.md) in AEM [SPA-Editor](/help/implementing/developing/hybrid/introduction.md).


## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### Neue Funktionen in [!DNL Assets] {#what-is-new-assets}

* Die Videotranscodierung wird jetzt mit Asset-Microservices unterstützt. In einem neuen Abschnitt in der Konfiguration der [!UICONTROL Verarbeitungsprofile] können Sie die Bitrate und die Abmessungen des Videos festlegen. Das Ausgabeformat ist MP4 mit H.264-Codec. Weitere Informationen finden Sie unter [Verwalten von Video-Assets](/help/assets/manage-video-assets.md#transcode-video). Verwenden Sie das [!DNL Dynamic Media]-Add-on für weitere Transkodierungsoptionen und den Videoversand.

* Bei neuen [!DNL Experience Manager Assets]-Bereitstellungen ist die Funktion für Smart-Tagging jetzt standardmäßig konfiguriert. Die manuelle Integration mit [!DNL Adobe Developer Console] ist nicht erforderlich. Bei vorhandenen Bereitstellungen konfigurieren Administratoren die Integration von Smart-Tags wie zuvor.

* Ein neues [Asset-Download-Erlebnis](/help/assets/download-assets-from-aem.md) ermöglicht Folgendes:

   * Asynchrone Downloads für große Downloads, sodass Benutzer nicht warten müssen.
   * Eine neue modulare API für die Erweiterbarkeit für Entwickler.

* Die Leistung der Metadatenextraktion für Asset-Microservices wurde verbessert. Sie erhöht den Gesamtdurchsatz der Asset-Erfassung.

* Verwenden eines Verarbeitungsprofils, um benutzerdefinierte Metadaten mithilfe des Compute Service zu generieren. Weitere Informationen finden Sie unter [Benutzerdefinierte Metadaten mithilfe eines Verarbeitungsprofils](/help/assets/manage-metadata.md#metadata-compute-service).

* Ein einfacheres Download-Erlebnis für Brand Portal-Benutzer, das von Administratoren konfiguriert werden kann. Weitere Informationen finden Sie unter [Überblick über das Download-Erlebnis](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html?lang=de#download-configurations).

* In Brand Portal sind jetzt native und hochwertige PDF-Dokumentvorschauen verfügbar. Weitere Informationen finden Sie unter [Überblick über den Dokument-Viewer](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html?lang=de#doc-viewer).

* Sie können den CDN (Content Delivery Network)-Cache jetzt direkt von [!DNL Dynamic Media] in AEM as a Cloud Service deaktivieren (im Gegensatz zur Verwendung von [!DNL Dynamic Media Classic]). Dadurch wird sichergestellt, dass die neuesten Assets innerhalb von Minuten statt Stunden bereitgestellt werden. Weitere Informationen finden Sie unter [Invalidieren des CDN-Cache mithilfe von Dynamic Media](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md).

* Den Steuerelementen sowie den Navigations-, Durchsuch- und Sucherlebnissen in der Benutzeroberfläche in [!DNL Assets] wurde eine verbesserte Unterstützung für die Barrierefreiheit hinzugefügt.

   * Wenn Sie die Esc-Taste drücken, nachdem Sie die Option [!UICONTROL Ausgabedarstellung hinzufügen] gewählt haben, kehrt der Fokus zur Symbolleiste zurück. <!-- via CQ-4293594-->
   * Der Tastaturfokus funktioniert wie erwartet, wenn Sie das E-Mail-Kombinationsfeld verwenden. <!-- via CQ-4286215 -->
   * Die Akkordeonelemente im Abschnitt mit den Suchfiltern werden als erweiterbare Standardakkordeons interpretiert. <!-- via CQ-4273103 -->
   * Beim Anwenden eines Tags auf ein Asset zeigt das Dialogfeld Tags als Baumelemente an. ARIA-Attribute werden entsprechend auf die Baumelemente angewendet, damit sie jetzt verfügbar sind. <!-- via CQ-4272964 -->

* Version 2.0.3 von [!DNL AEM Desktop app] ist jetzt verfügbar. Sie verbessert die Kompatibilität mit dem Service Pack [!DNL Experience Manager] 6.5.5 und verfügt über eine aktualisierte Kompatibilitätsliste für Client-Betriebssysteme. [!DNL Windows] 7-Versionen und [!DNL macOS]-Versionen älter als 10.14 werden nicht unterstützt.

### Fehlerbehebungen in [!DNL Assets] {#bugs-fixed}

* Die Option „Verknüpfen“ bzw. „Nicht verknüpfen“ reagiert nicht, wenn zum ersten Mal darauf geklickt wird. (CQ-4299022)
* Wenn Sie beim Herunterladen eines Assets die Option zum Empfangen des Assets per E-Mail auswählen, wird die E-Mail nicht gesendet. (CQ-4299146)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Die Funktion Product Console ist jetzt verfügbar. Damit können Marketing-Experten/Autoren in AEM Kategorien und Produkte, die im Handels-Backend gespeichert sind, anzeigen und durchsuchen. Die Product Console unterstützt auch Eigenschaften für Kategorien und Produkte.

* Die Produkt- und Kategorieauswahl wurde verbessert, damit Marketing-Experten Produkte über die SKU oder die Kategorie über die Kategorie-ID auswählen können.

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Die [!UICONTROL Cloud Manager]-Version 2020.8.0 wurde am 6. August 2020 veröffentlicht.

### Neue Funktionen {#what-is-new-cloud-manager}

* Content Audit ist eine Funktion, die in den Produktions-Pipelines von Cloud Manager Sites aktiviert ist. Die Konfiguration der Produktions-Pipeline für Programm mit Sites enthält jetzt eine dritte Registerkarte mit dem Namen **Content Audit**. Bei jeder Ausführung einer Produktions-Pipeline wird nach benutzerdefinierten Funktionstests ein neuer Schritt zur Inhaltsprüfung in die Pipeline aufgenommen, wodurch die Site anhand mehrerer Dimensionen wie Leistung, SEO (Suchmaschinenoptimierung), Barrierefreiheit, Best Practices und PWA (Progressive Web App) bewertet wird.


  >[!NOTE]
  >Content Audit wurde inzwischen in Erlebnis-Audit umbenannt.

  Weitere Details finden Sie unter [Erlebnis-Audit-Tests](/help/implementing/cloud-manager/reports/report-experience-audit.md).

* Neu erstellte Umgebungen in Assets-Programmen werden jetzt automatisch mit Smart Content Services konfiguriert.

* Der Ruhezustand von im Ruhezustand befindlichen Umgebungen kann auf der Seite **Überblick** von Cloud Manager aufgehoben werden.

* Möglichkeit zur Durchführung von Erlebnisprüfungen auf Seiten, die über Google Lighthouse bereitgestellt werden. Als Teil der Cloud Manager-Pipeline können bis zu 25 Seiten anhand von Erlebnis-KPIs geprüft und validiert werden. Die Bewertungen werden in der Cloud Manager-Benutzeroberfläche angezeigt.

### Fehlerbehebungen {#bug-fixes-cm}

* Einige unnötige und unerwünschte SonarQube-Plug-ins wurden im Rahmen der Überprüfung der Code-Qualität ausgeführt.

* Auf der Seite zur Ausführung der Pipeline wurde der Verzweigungsname falsch formatiert.

* In einigen Fällen wurden abgeschlossene Pipeline-Ausführungen nicht erfolgreich als abgeschlossen aufgezeichnet, wodurch neue Ausführungen der Pipeline verhindert wurden.

* Pipeline-Ausführungen blieben gelegentlich aufgrund interner Kommunikationsprobleme *stecken*.

* Bei der Bereitstellung einer neuen Organisation erhielten einige Benutzer mit anderen administrativen Rollen als Systemadministratoren fälschlicherweise Zugriff auf Cloud Manager.

* Unter bestimmten Umständen wurde der Vorgang zur Indexaktualisierung mehrmals parallel gestartet, was zu einem Bereitstellungsfehler führte.

* Die QuickInfo auf den Programmkarten war nicht immer korrekt.

* Die Benutzeroberfläche erlaubte fälschlicherweise, dass Vorgänge in einer Umgebung gestartet wurden, während sie gelöscht wurde.

* Auf der **Übersichtsseite von Cloud Manager** traten Farbabweichungen auf.

### Bekannte Probleme {#known-issues-cm}

* Es sind ungültige Seiten enthalten, die den Content Audit-Durchschnittswert unter den erwarteten Wert bringen.

* Auf der Registerkarte „Inhaltsprüfung“ wird die Basis-URL unter Verwendung der Autoren-Domain anstelle der Veröffentlichungs-Domain falsch angezeigt.

* Um den Schritt „Content Audit“ zu aktivieren, müssen Benutzende die Pipeline bearbeiten und optional Seiten hinzufügen. Wenn keine Seiten hinzugefügt werden, wird das Audit auf die Homepage angewendet.

## Content Transfer Tool {#content-transfer-tool}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und Updates für das Content Transfer Tool Version 1.0.4.

### Neue Funktionen {#what-is-new-ctt}

* Das Content Transfer Tool unterstützt jetzt den freigegebenen S3-Datenspeicher.

### Fehlerbehebungen {#ctt-bug-fixes}

* Es wurden zusätzliche Timeouts für das Tool hinzugefügt, um Aktionen abzuschließen.

* Die Benutzeroberfläche früherer Versionen zeigte manchmal eine erfolgreiche Extraktion an, obwohl das Protokoll Fehler enthielt.

## Code-Refaktorierungs-Tools {#code-refactoring-tools}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und Updates für die Code-Refaktorierungs-Tools.

### Neue Funktionen {#what-is-new-refactoring}

* Das AIO-CLI-Plugin wurde veröffentlicht, um Code-Refaktorierungs-Tools zu vereinheitlichen, damit Entwickler Code-Refaktorierungs-Tools von einem Ort aus aufrufen und ausführen können. Weitere [ finden Sie unter „Git-Ressource: aio-cli-plugin-aem-cloud-service](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration)migration“.

* AEM Dispatcher Converter wurde erweitert, um die Konvertierung von On-Premise- und Adobe Managed Services-Dispatcher-Konfigurationen in AEM as a Cloud Service-kompatible Dispatcher-Konfigurationen zu unterstützen. Weitere [ finden Sie unter „Git-Ressource: AEM Cloud Service](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter)Dispatcher-Konvertierer“.

* AEM Dispatcher Converter wurde in ` node.js ` neu geschrieben und in das AIO-CLI-Plug-in integriert.
