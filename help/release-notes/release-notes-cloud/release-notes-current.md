---
title: Adobe Experience Manager als Cloud-Dienst - Versionshinweise für 2020.4.0
description: Versionshinweise zu Experience Manager für 2020.4.0
translation-type: tm+mt
source-git-commit: 49137535f4f6a6b62e697de6a7a9934f5b861bbc

---


# Release Notes for Adobe Experience Manager as a Cloud Service 2020.4.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise [!DNL Experience Manager] als Cloud Service 2020.4.0 beschrieben.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für [!DNL Experience Manager] den Cloud-Dienst 2020.4.0 ist der 9. April 2020.

## What&#39;s New in Assets {#assets}

Erfahren Sie mehr über neue Funktionen, Verbesserungen und Fehlerkorrekturen für [!DNL Experience Manager Assets] und [!DNL Dynamic Media] in der aktuellen Version.

* [Markenportal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) unterstützt die Anwendungsfälle für die Asset-Verteilung für Experience Manager Assets. [!DNL Brand Portal] unterstützt Unternehmen dabei, ihre Marketing-Anforderungen zu erfüllen, indem zugelassene Marken- und Produktressourcen sicher an externe Agenturen, Partner, interne Teams und Wiederverkäufer zum Herunterladen verteilt werden.
   * [!DNL Brand Portal] die Konfiguration über [!DNL Adobe I/O] Konsole abgeschlossen wurde.
   * Die Asset-Beschaffung in [!DNL Brand Portal] wird mit [!DNLEExperience Manager] als Cloud-Dienst noch nicht unterstützt.

* [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) Version 2.0 funktioniert [!DNL Experience Manager] als Cloud-Dienst. [!DNL Adobe Asset Link] optimiert die Zusammenarbeit zwischen Kreativen und Marketingexperten bei der Inhaltserstellung durch die Verbindung [!DNL Experience Manager Assets] mit [!DNL Creative Cloud] Desktop-Apps [!DNL Adobe Photoshop], [!DNL Adobe Illustrator]und [!DNL Adobe InDesign] über das In-App- [!DNL Asset Link] Bedienfeld.
   * [!DNL Experience Manager] ist vorkonfiguriert für [!DNL Adobe Asset Link], was zu einer [einfachen Konfiguration](https://helpx.adobe.com/enterprise/using/configure-aem-assets-for-asset-link.html) und einer schnelleren Einführung in Kreativprofis führt.
   * [!DNL Asset Link] unterstützt jetzt einen [Experience Manager Umgebung-Umschalter](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink) , mit dem sich Kreativbenutzer problemlos mit einer anderen [!DNL Experience Manager] Umgebung verbinden können. Ein Beispiel, bei dem diese Funktion nützlich ist, sind Agenturdesigner, die mit mehreren Kunden arbeiten und verschiedene [!DNL Experience Manager Assets] Bereitstellungen verwenden.

* Die Benutzer können die [Nachbearbeitung Workflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) für den automatischen Beginn in der Benutzeroberfläche &quot; [!UICONTROL Eigenschaften] &quot;für die jeweiligen Ordnerhierarchien konfigurieren.
   * Die Benutzeroberfläche &quot;Ordnereigenschaften [!UICONTROL &quot;wurde vereinfacht. Die neue Registerkarte &quot;] Asset-Verarbeitung  &quot;enthält Metadaten-Profil, Profil zur Verarbeitung und die neue Workflow-Konfiguration für den automatischen Beginn.
   * Im Dialogfeld zur Asset-Wiederaufbereitung können Sie ein bestimmtes Profil auswählen und entscheiden, es in Unterordnern erneut zu verarbeiten.
   * [!DNL Dynamic Media]: Es wurde eine selektive Veröffentlichungskonfiguration hinzugefügt, sodass Assets nur für sichere Vorschau automatisch veröffentlicht werden. Außerdem können die Assets explizit in Experience Manager veröffentlicht werden, ohne sie für Versände in der öffentlichen Domäne in DMS7 zu veröffentlichen.

### Fehlerbehebungen {#assets-bug-fixes}

* Fehlerbehebungen bei Problemen mit der Asset-Verarbeitung.
* Fehlerbehebungen in [!DNL Dynamic Media] Konfiguration und Veröffentlichung von Assets im [!DNL Dynamic Media] Versand-Dienst.

>[!MORELIKETHIS]
>
>* [Info zu Adobe Asset Link](https://www.adobe.com/de/creativecloud/business/enterprise/adobe-asset-link.html)
>* [Markenportal konfigurieren](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html)
>* [Experience Manager für die Verwendung mit Asset Link konfigurieren](https://helpx.adobe.com/enterprise/using/configure-aem-assets-for-asset-link.html)
>* [Erstellen von Arbeitsabläufen in Experience Manager mithilfe von Assets Microservices](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/manage/asset-microservices-configure-and-use.html#post-processing-workflows)


## Neue Funktionen in Cloud Manager {#whats-new-cloud-manager}

* Herausgeber-URLs sind jetzt auf der Seite &quot;Umgebung&quot;in der Benutzeroberfläche von Cloud Manager verfügbar.
* Änderungen an der Navigation, die es dem Benutzer ermöglichen, ein Programm von der Cloud Manager-Übersichtsseite zu bearbeiten, zu wechseln oder hinzuzufügen.
* Änderungen, die es dem Benutzer erlauben, Programm von der Programm-Karte in der Cloud Manager-Landingpage zu bearbeiten.
* Neue Pipeline-Status- **Pipeline, die mit der Umgebung, mit der sie verbunden ist, ausgeführt** wird.
* Verbesserte Verständlichkeit der Pipeline-Ausführungsseite. Dazu gehören die Anzeige des Pipeline-Namens (nur nicht in der Produktion) und des Typs sowie eine Markierung, mit der angegeben wird, ob der Pipeline-Status in Bearbeitung/Abgebrochen/Fehlgeschlagen ist.
* QuickInfos zur Verbesserung der Benutzerfreundlichkeit und Verständlichkeit, weshalb Hinzufügen Schaltfläche &quot;Programm/Umgebung&quot;deaktiviert ist.
* Fehlgeschlagene Umgebung können jetzt über die Benutzeroberfläche und die API gelöscht werden.
* Der zur Erstellung von Git-Passwörtern verwendete Prozess wurde für Probleme in der zugrunde liegenden Service-Ebene widerstandsfähiger gemacht.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Die Links zur Umgebung &quot;Stage&quot;auf der Seite mit Details zur Pipelineausführung navigierten nicht einheitlich zum richtigen Ort.
* Einzelne Schritte innerhalb des Umgebung-Erstellungsprozesses werden schneller als nötig ausgeführt, sodass der Vorgang fehlschlägt.
* Die Maven-Konfiguration, die im Build-Container verwendet wird, wurde aktualisiert, um Deadlocks beim Herunterladen von Artefaktmetadaten zu vermeiden.
* In einigen Fällen kann der Schritt Image erstellen nicht erfolgreich zum Herunterladen von Kundenpaketen führen.
* Bestimmte selten auftretende Umstände würden verhindern, dass Umgebung gelöscht werden.
* Experience Cloud-Benachrichtigungen wurden nicht konsistent empfangen.
