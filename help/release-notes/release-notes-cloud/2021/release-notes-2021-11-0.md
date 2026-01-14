---
title: Versionshinweise für Version 2021.11.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2021.11.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 86f8ddd1-af51-4874-9111-0935b5a162c1
feature: Release Information
role: Admin
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '1059'
ht-degree: 94%

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

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2021.11.0) war der 16. Dezember 2021.
Die folgende Version (2022.1.0) wurde am 3. Februar 2022 veröffentlicht

## Video zur Version {#release-video}

Sehen Sie sich das Video [Versionsübersicht Dezember 2021](https://video.tv.adobe.com/v/339278) an, das eine Zusammenfassung der Funktionen bietet, die der Version 2021.11.0 (November 2021) hinzugefügt wurden.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Das smarte Zuschneiden von Dynamic Media-Bildern und die Farbfelder basieren jetzt auf den neuesten Adobe-KI-Services, die verbesserte Zuschnitte und Farbfelder generieren. Außerdem wurde eine Verbesserung eingeführt, um unterschiedliche zugeschnittene Inhalte für dasselbe Seitenverhältnis, aber für verschiedene Auflösungen zu erzeugen. Darüber hinaus bleiben manuelle Bearbeitungen bei der erneuten Verarbeitung erhalten, wenn sich die Breite und Höhe des Bildprofils nicht ändern.

### Neue Funktionen im Kanal der Vorabversion von [!DNL Assets] {#assets-prerelease-features}

* [!DNL Dynamic Media]: Sie können jetzt die AEM Dynamic Media-Benutzeroberfläche verwenden, um allgemeine Einstellungen und Veröffentlichungseinstellungen zu konfigurieren, anstatt das Dynamic Media Classic-Desktop-Programm verwenden zu müssen.

* [!DNL Dynamic Media] unterstützt jetzt Aufnahme, Vorschau, Wiedergabe und Veröffentlichung von MXF-Videos. Anmerkungen und Shop-fähige Videos für MXF-Videos werden noch nicht unterstützt.

* Nach dem Konfigurieren einer Verbindung zwischen Remote-DAM- und Sites-Bereitstellungen werden die Assets auf Remote-DAM in der Sites-Bereitstellung verfügbar gemacht. Sie können jetzt Remote-DAM-Assets oder -Ordner [aktualisieren, löschen, umbenennen und verschieben](/help/assets/use-assets-across-connected-assets-instances.md). Die Aktualisierungen stehen mit etwas Verzögerung automatisch in der Sites-Bereitstellung zur Verfügung.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* **Externalisieren von AEM-Workflow-Daten für eine sichere Verarbeitung**: Sie können prozessinterne AEM-Workflow-Daten (AEM-Workflow-Variablendaten), die sensible personenbezogene Daten (SPD) beinhalten, zur sicheren Verarbeitung in einem vom Kunden verwalteten Repository speichern. Die Datenelemente und Workflow-Variablen werden nicht im AEM-Repository gespeichert, sondern bei der Verarbeitung des Workflows bei Bedarf aus dem vom Kunden verwalteten Repository abgerufen.

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Forms] verfügbar {#prerelease-features-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [Kommunikations-APIs](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html?lang=de) helfen Ihnen, eine Vorlage und XML-Daten zu kombinieren, um Print-Dokumente in verschiedenen Formaten zu erzeugen. Mit dem Service können Sie Dokumente im synchronen Modus und im Batch-Modus generieren. Dabei können Sie mit den APIs Anwendungen mit folgenden Funktionen erstellen:

   * Erzeugen von Dokumenten durch Ausfüllen von Vorlagendateien (PDF und XDP) mit XML-Daten.
   * Erzeugen Sie Ausgabeformulare in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Druckdatenströme.

* **Benutzerdefinierte Schriftarten für Datensatzdokument- und PDF-Dokumente, die mit Kommunikations-APIs erstellt wurden**: Sie können jetzt markengeprüfte Schriftarten in PDF-Dokumenten verwenden, die mithilfe von Kommunikations-APIs generiert wurden, um sie an die Anforderungen Ihres Unternehmens anzupassen.

* **Formularportal**: Sie können das [Formularportal](/help/forms/configure-forms-portal.md) nutzen, um Ihre veröffentlichten adaptiven Formulare auf einer AEM Sites-Seite aufzulisten. Damit wird es Site-Besuchern erleichtert, alle verfügbaren Formulare zu finden. Darüber hinaus kann der Besucher das Formularportal verwenden, um Entwürfe eines adaptiven Formulars zu speichern und darauf zuzugreifen und sich die PDF-Version eines gesendeten adaptiven Formulars anzusehen.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Erweiterte myAccount-Komponenten, die auf den erweiterbaren Peregrine-Komponenten von Commerce basieren

![Erweiterte myAccount-Komponenten](/help/assets/CIF/extended-myAccount-components.png)

* Autoren können Ad-hoc-Commerce-Produktempfehlungen mithilfe zusätzlicher Empfehlungstypen erstellen

* Unterstützung für Geschenkgutscheine in der AEM-Storefront

## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise zu Cloud Manager in AEM as a Cloud Service 2021.11.0.

### Veröffentlichungsdatum {#release-date-cm-nov}

Die Version 2021.11.0 von Cloud Manager in AEM as a Cloud Service wurde am 04. November 2021 veröffentlicht.
Die nächste Version wurde am 09. Dezember 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-cm-nov}

* Benutzende können jetzt neue Frontend-Pipelines nutzen, um Frontend-Code exklusiv schneller bereitzustellen. Weitere Informationen finden Sie unter [Cloud Manager-Frontend-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end).

  >[!IMPORTANT]
  >Sie müssen AEM Version `2021.10.5933.20211012T154732Z` oder höher verwenden, um neue Frontend-Pipelines verwenden zu können.

* Die Dauer der Code-Qualitäts-Pipeline wird erheblich reduziert, indem die Code-Analyse effizienter durchgeführt wird, ohne dass ein ganzes AEM-Bild erstellt werden muss. Diese Änderung wird in den Wochen nach der Veröffentlichung schrittweise eingeführt.

* Die Git-Commit-ID wird jetzt in den Details zur Pipeline-Ausführung angezeigt, was die Nachverfolgung des erstellten Codes erleichtert.

* Die Erstellung von Programmen ist jetzt über öffentlich zugängliche APIs verfügbar.

* Die Erstellung von Umgebungen ist jetzt über öffentlich zugängliche APIs verfügbar.

* Der Antwort-Header `x-request-id` ist jetzt im API Playground auf [www.adobe.io](https://www.adobe.io/) sichtbar. Dieser Header ist beim Senden von Problemen an die Kundenunterstützung zur Fehlerbehebung nützlich.

* Als Benutzer sehe ich die Pipeline-Karte mit null Pipelines, die mir eine entsprechende Anleitung bieten.

* Auf einer neuen Aktivitätsseite können jetzt Aktivitäten wie Pipeline- und Code-Ausführungen zusammen mit den zugehörigen Details angezeigt werden. Im Laufe der Zeit werden auf dieser Seite immer mehr Aktivitäten und Details aufgelistet.

* Die neue Pipelines-Seite enthält ein Status-Popover, in dem eine Zusammenfassung der Details eingeblendet wird, sobald der Mauszeiger über eine Aktivität bewegt wird. Pipeline-Ausführungen können zusammen mit den zugehörigen Details angezeigt werden.

* Außerdem unterstützt sie jetzt das Ändern der in den Bereitstellungsphasen verwendeten Umgebung.

* Für große Pakete wurde eine Optimierung des OakPal-Scan-Prozesses eingeführt.

* Die CSV-Datei mit Qualitätsproblemen enthält jetzt für jedes Qualitätsproblem einen Zeitstempel.

### Fehlerbehebungen {#bug-fixes-nov}

* Bestimmte unorthodoxe Build-Konfigurationen führten dazu, dass unnötige Dateien im Maven-Artefakt-Cache der Pipeline gespeichert wurden, was beim Starten und Stoppen des Build-Containers zu überflüssigem Netzwerk-I/O führte.

* Die Pipeline-PATCH-API schlägt fehl, wenn keine Bereitstellungsphase vorhanden ist.

* Die Qualitätsregel `ClientlibProxyResourceCheck` meldete falsch positive Probleme, wenn Client-Bibliotheken mit gemeinsamen Basispfaden vorhanden waren.

* In der Fehlermeldung beim Erreichen der maximalen Anzahl von Repositorys war kein Grund für den Fehler angegeben.

* In seltenen Fällen schlugen Pipelines aufgrund einer unangemessenen Wiederholungsverarbeitung bestimmter Antwort-Codes fehl.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer 2.1.22 wurde am 01. Dezember 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* Die Möglichkeit, die verwendete Version von ACS Commons zu erkennen und darüber zu berichten.
* Die Möglichkeit, die Anzahl der Benutzer und Untergruppen in einer Gruppe zu erkennen und darüber zu berichten.
* Die Möglichkeit, Knoteneigenschaftswerte in MongoDB, die 16 MB überschreiten, zu erkennen und darüber zu berichten.

### Fehlerbehebungen {#bug-fixes-bpa}

* Die Erkennung von Foundation-Komponenten wurde optimiert, um falsche negative Werte zu reduzieren.
* Für AEM Forms-Kunden: Die Nichtverfügbarkeit von BPA-Nachrichten zu `EMAIL_PDF_SUBMIT_ACTION` in AEM as a Cloud Service wurde behoben.
