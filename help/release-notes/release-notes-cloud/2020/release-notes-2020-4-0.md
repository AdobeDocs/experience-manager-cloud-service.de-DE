---
title: Versionshinweise für Adobe Experience Manager as a Cloud Service 2020.4.0
description: '[!DNL Adobe Experience Manager] as a Cloud Service-Versionshinweise für 2020.4.0.'
exl-id: d98a3862-76fa-4b5b-b81a-333f5f532b67
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 98%

---

# Versionshinweise für Adobe Experience Manager as a Cloud Service 2020.4.0 {#release-notes}

Auf dieser Seite werden die allgemeinen Versionshinweise für [!DNL Experience Manager] as a Cloud Service 2020.4.0 beschrieben.

## Veröffentlichungsdatum {#release-date}

Die Version 2020.4.0 von [!DNL Experience Manager] as a Cloud Service wurde am 9. April 2020 veröffentlicht.

## Neue Funktionen in Assets {#assets}

Erfahren Sie mehr über neue Funktionen, Verbesserungen und Fehlerkorrekturen für [!DNL Experience Manager Assets] und [!DNL Dynamic Media] in der aktuellen Version.

* [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html?lang=de) unterstützt die Anwendungsfälle der Asset-Verteilung für Experience Manager Assets. [!DNL Brand Portal] unterstützt Unternehmen dabei, ihre Marketing-Anforderungen zu erfüllen, indem zugelassene Marken- und Produktressourcen sicher an externe Agenturen, Partner, interne Teams und Wiederverkäufer zum Herunterladen verteilt werden.
   * [!DNL Brand Portal] wird über die [!DNL Adobe I/O]-Konsole konfiguriert. Siehe [Konfigurieren von Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html?lang=de).
   * Die Asset-Beschaffung in [!DNL Brand Portal] wird von [!DNL Experience Manager] as a Cloud Service noch nicht unterstützt.

* [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html)-Version 2.0 funktioniert mit [!DNL Experience Manager]as a Cloud Service. [!DNL Adobe Asset Link] optimiert die Zusammenarbeit zwischen Kreativen und Marketern bei der Inhaltserstellung durch die Verbindung von [!DNL Experience Manager Assets] mit den [!DNL Creative Cloud]-Desktop-Programmen [!DNL Adobe Photoshop], [!DNL Adobe Illustrator] und [!DNL Adobe InDesign] über das interne [!DNL Asset Link]-Bedienfeld.
   * [!DNL Experience Manager] ist vorkonfiguriert für [!DNL Adobe Asset Link], was zu einer [einfachen Konfiguration](https://helpx.adobe.com/de/enterprise/using/configure-aem-assets-for-asset-link.html) und einer schnelleren Einführung für Kreativschaffende führt.
   * [!DNL Asset Link] unterstützt jetzt einen [Schalter für Experience Manager-Umgebungen](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink), mit dem sich Kreativschaffende problemlos mit einer anderen [!DNL Experience Manager]-Umgebung verbinden können. Ein Beispiel, bei dem diese Funktion nützlich ist, sind Agentur-Designer, die mit mehreren Kunden arbeiten und verschiedene [!DNL Experience Manager Assets]-Bereitstellungen verwenden.

* Die Benutzer können [Nachbearbeitungs-Workflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) konfigurieren, um automatisch in der Benutzeroberfläche des Ordners [!UICONTROL Eigenschaften] der jeweiligen Ordnerhierarchien zu starten.
   * Die Benutzeroberfläche des Ordners [!UICONTROL Eigenschaften] wurde vereinfacht. Die neue Registerkarte [!UICONTROL Asset-Verarbeitung] enthält das Metadaten-Profil, das Verarbeitungsprofil und die neue Workflow-Konfiguration für den automatischen Start.

     ![Die Verarbeitungsprofile können problemlos auf Ordner angewendet werden. Damit werden alle in die Ordner hochgeladenen Assets mit diesen Profilen verarbeitet.](/help/assets/assets/asset-processing-folder-properties.png)

   * Mit der Option zur erneuten Verarbeitung von Assets können Sie ein bestimmtes Verarbeitungsprofil auswählen, um vom Benutzer ausgewählte Assets in den Unterordnern erneut zu verarbeiten.

     ![Ausgewählte Assets mit einem bestimmten Verarbeitungsprofil erneut verarbeiten](/help/assets/assets/fpo-existing-asset-reprocess.gif)

   * [!DNL Dynamic Media]: Es wurde eine selektive Veröffentlichungskonfiguration hinzugefügt, sodass Assets automatisch nur zur sicheren Vorschau veröffentlicht werden. Außerdem können die Assets explizit in Experience Manager veröffentlicht werden, ohne dass sie in DMS7 zur öffentlich zugänglichen Bereitstellung veröffentlicht werden müssen.

### Fehlerbehebungen {#assets-bug-fixes}

* Fehlerbehebungen bei Problemen mit der Asset-Verarbeitung.
* Fehlerbehebungen bei der [!DNL Dynamic Media]-Konfiguration und der Veröffentlichung von Assets im [!DNL Dynamic Media]-Bereitstellungs-Service.

>[!MORELIKETHIS]
>
>* [Über Adobe Asset Link](https://www.adobe.com/de/creativecloud/business/enterprise/adobe-asset-link.html)
>* [Konfigurieren von Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html?lang=de)
>* [Konfigurieren von Experience Manager für die Verwendung mit Asset Link](https://helpx.adobe.com/de/enterprise/using/configure-aem-assets-for-asset-link.html)
>* [Erstellen von Workflows in Experience Manager unter Verwendung von Asset-Microservices](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/asset-microservices-configure-and-use.html?lang=de#post-processing-workflows)

## Neue Funktionen in Cloud Manager {#whats-new-cloud-manager}

* Herausgeber-URLs sind jetzt auf der Seite „Umgebung“ in der Benutzeroberfläche von Cloud Manager verfügbar.
* Änderungen an der Navigation, die es dem Benutzer ermöglichen, ein Programm von der Cloud Manager-Übersichtsseite aus zu bearbeiten, zu wechseln oder hinzuzufügen.
* Änderungen, die es Benutzern erlauben, das Programm über die Programmkarte auf der Landingpage von Cloud Manager zu bearbeiten.
* Neuer Pipeline-Status: **Pipeline wird ausgeführt** wird in der Umgebung angezeigt, der sie zugewiesen ist.
* Bessere Verständlichkeit der Pipeline-Ausführungsseite. Dazu gehören die Anzeige des Pipeline-Namens (nur produktionsfremde Pipelines) und des Typs sowie ein Abzeichen mit dem Pipeline-Status (In Bearbeitung/Abgebrochen/Fehlgeschlagen).
* QuickInfos zur Verbesserung des Kundenerlebnisses und der Verständlichkeit, warum die Schaltfläche „Programm/Umgebung hinzufügen“ deaktiviert ist.
* Fehlgeschlagene Umgebungen können jetzt über die Benutzeroberfläche und die API gelöscht werden.
* Der zur Erstellung von Git-Kennwörtern verwendete Prozess ist jetzt weniger anfällig für Probleme in der zugrunde liegenden Service-Ebene.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Die Links zur Staging-Umgebung auf der Seite mit Details zur Pipeline-Ausführung führten nicht konsistent zum richtigen Speicherort.
* Einzelne Schritte innerhalb des Prozesses der Umgebungserstellung setzten früher als nötig aus und brachten den Prozess zum Scheitern.
* Die Maven-Konfiguration, die im Build-Container verwendet wird, wurde aktualisiert, um Deadlocks beim Download von Artefaktmetadaten zu vermeiden.
* In einigen Fällen konnte der Schritt zur Bilderstellung die Kundenpakete nicht erfolgreich herunterladen.
* Bestimmte selten auftretende Bedingungen verhinderten, dass Umgebungen gelöscht wurden.
* Experience Cloud-Benachrichtigungen wurden nicht konsistent empfangen.
