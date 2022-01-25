---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 35f153a6f094f558b6a5e1d880dde9f33dcd92fb
workflow-type: tm+mt
source-wordcount: '1053'
ht-degree: 51%

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

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] Die aktuelle Version (2021.11.0) ist der 16. Dezember 2021.
Die folgende Version (2022.1.0) wurde am 3. Februar 2022 veröffentlicht.

## Video zur Version {#release-video}

Sehen Sie sich die [Versionsübersicht Dezember 2021](https://video.tv.adobe.com/v/339278) Video mit einer Zusammenfassung der Funktionen, die in der Version 2021.11.0 (November 2021) hinzugefügt wurden.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Dynamic Media Image Smart Crop und Swatch basieren jetzt auf den neuesten Sensei-Diensten, die verbesserte Zuschnitte und Farb-/Bildmuster generieren. Außerdem wurde eine Erweiterung gestartet, um unterschiedliche Zuschnittinhalte zu generieren, für das gleiche Seitenverhältnis aber über verschiedene Auflösungen hinweg. Darüber hinaus bleiben manuelle Bearbeitungen bei der Neuverarbeitung erhalten, wenn sich die Breite und Höhe des Bildprofils nicht ändern.

### Neue Funktionen in [!DNL Assets] Vorabversionskanal {#assets-prerelease-features}

* [!DNL Dynamic Media] - Sie können jetzt AEM Dynamic Media-Benutzeroberfläche verwenden, um allgemeine Einstellungen und Veröffentlichungseinstellungen zu konfigurieren, anstatt die Dynamic Media Classic-Desktop-Applikation durchlaufen zu müssen.

* [!DNL Dynamic Media] unterstützt jetzt Erfassung, Vorschau, Wiedergabe und Veröffentlichung für MXF-Videos. Anmerkungen und Videos mit Shopping-Funktion für MXF-Videos werden noch nicht unterstützt.

* Nach dem Konfigurieren einer Verbindung zwischen Remote-DAM- und Sites-Bereitstellungen werden die Assets auf Remote-DAM in der Sites-Bereitstellung verfügbar gemacht. Sie können jetzt die [Vorgänge aktualisieren, löschen, umbenennen und verschieben](../../assets/use-assets-across-connected-assets-instances.md) auf den Remote-DAM-Assets oder -Ordnern. Die Aktualisierungen sind mit einiger Verzögerung automatisch in der Sites-Bereitstellung verfügbar.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* **Externalisieren von AEM-Workflow-Daten für eine sichere Verarbeitung**: Sie können prozessinterne AEM-Workflow-Daten (AEM-Workflow-Variablendaten), die sensible personenbezogene Daten (SPD) beinhalten, zur sicheren Verarbeitung in einem vom Kunden verwalteten Repository speichern. Die Datenelemente und Workflow-Variablen werden nicht im AEM-Repository gespeichert, sondern bei der Verarbeitung des Workflows bei Bedarf aus dem vom Kunden verwalteten Repository abgerufen.

### Neue Funktionen in [!DNL Forms] im Kanal für die Vorabversion {#prerelease-features-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [Kommunikations-APIs](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html) helfen Ihnen, eine Vorlage und XML-Daten zu kombinieren, um Print-Dokumente in verschiedenen Formaten zu erzeugen. Mit dem Service können Sie Dokumente im synchronen Modus und im Batch-Modus generieren. Dabei können Sie mit den APIs Programme mit folgenden Funktionen erstellen:

   * Erzeugen von Dokumenten durch Ausfüllen von Vorlagendateien (PDF und XDP) mit XML-Daten.
   * Erzeugen von Ausgabeformularen in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Print-Datenströme.

* **Benutzerdefinierte Schriftarten für Datensatzdokument- und PDF-Dokumente, die mit Kommunikations-APIs erstellt wurden**: Sie können jetzt markengenehmigte Schriftarten in PDF-Dokumenten verwenden, die mithilfe von Kommunikations-APIs generiert wurden, um Ihre organisatorischen Anforderungen zu erfüllen.

* **Forms Portal**: Sie können [Forms Portal](/help/forms/configure-forms-portal.md) , um Ihre veröffentlichten adaptiven Formulare auf einer AEM Sites-Seite aufzulisten. Dies hilft einem Site-Besucher, alle verfügbaren Formulare zu finden. Darüber hinaus kann der Besucher das Formularportal verwenden, um Entwürfe eines adaptiven Formulars zu speichern und darauf zuzugreifen und sich die PDF-Version eines gesendeten adaptiven Formulars anzusehen.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Erweiterte myAccount-Komponenten, die auf den erweiterbaren Peregrine-Komponenten von Commerce basieren

![Erweiterte myAccount-Komponenten](/help/assets/CIF/extended-myAccount-components.png)

* Autoren können Ad-hoc-Commerce Product Recommendations mithilfe zusätzlicher Empfehlungstypen erstellen

* Unterstützung für Geschenkgutscheine in AEM Storefront

## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.11.0.

### Veröffentlichungsdatum {#release-date-cm-nov}

Die Version 2021.11.0 von Cloud Manager in AEM as a Cloud Service wurde am 04. November 2021 veröffentlicht.
Die nächste Version soll am 09. Dezember 2021 veröffentlicht werden.

### Neue Funktionen {#what-is-new-cm-nov}

* Benutzer können jetzt neue Front-End-Pipelines nutzen, um Frontend-Code exklusiv schneller bereitzustellen. Siehe [Cloud Manager-Frontend-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) , um mehr zu erfahren.

   >[!IMPORTANT]
   >Sie müssen AEM Version verwenden `2021.10.5933.20211012T154732Z` oder höher , um neue Front-End-Pipelines zu nutzen.

* Die Dauer der Code-Qualitäts-Pipeline wird erheblich reduziert, indem die Codeanalyse effizienter durchgeführt wird, ohne dass ein ganzes AEM Bild erstellt werden muss. Diese Änderung wird in den Wochen nach der Veröffentlichung schrittweise eingeführt.

* Die Git-Commit-ID wird jetzt in den Details zur Pipeline-Ausführung angezeigt, was die Verfolgung des erstellten Codes erleichtert.

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

* Bestimmte unorthodoxe Build-Konfigurationen führten dazu, dass unnötige Dateien im Maven-Artefakt-Cache der Pipeline gespeichert wurden, was beim Starten und Beenden des Build-Containers zu überflüssigem Netzwerk-I/O führte.

* Die Pipeline-PATCH-API schlägt fehl, wenn keine Bereitstellungsphase vorhanden ist.

* Die Qualitätsregel `ClientlibProxyResourceCheck` meldete falsch positive Probleme, wenn Client-Bibliotheken mit gemeinsamen Basispfaden vorhanden waren.

* In der Fehlermeldung beim Erreichen der maximalen Anzahl von Repositorys war kein Grund für den Fehler angegeben.

* In seltenen Fällen schlugen Pipelines aufgrund einer unangemessenen Wiederholungsverarbeitung bestimmter Antwort-Codes fehl.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Die Version 2.1.22 von Best Practices Analyzer wurde am Donnerstag, 1. Dezember 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* Möglichkeit, die Version der verwendeten ACS-Commons zu erkennen und darüber zu berichten.
* Möglichkeit, die Anzahl der Benutzer und Untergruppen in einer Gruppe zu erkennen und darüber zu berichten.
* Möglichkeit zur Erkennung und Berichterstellung von Knoteneigenschaftswerten in MongoDB, die 16 MB überschreiten.

### Fehlerbehebungen {#bug-fixes-bpa}

* Die Erkennung von Foundation-Komponenten wurde optimiert, um falsche negative Werte zu reduzieren.
* Für AEM Forms-Kunden: BPA-Nachrichten zu `EMAIL_PDF_SUBMIT_ACTION` nicht verfügbar auf AEM as a Cloud Service wurde behoben.
