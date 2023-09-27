---
title: Versionshinweise für Version 2021.8.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Versionshinweise für Version 2021.8.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 8b041934-1c4a-4670-9b03-d38f683b99e5
source-git-commit: f956b8379b5b93bc00e25f0eec641430c5565e34
workflow-type: tm+mt
source-wordcount: '1024'
ht-degree: 55%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen navigieren. Zum Beispiel für die Jahre 2020 und 2021.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2021.8.0) war der 26. August 2021.
Die folgende Version (2021.9.0) wurde am 6. Oktober 2021 veröffentlicht.

## Video zur Version {#release-video}

Sehen Sie sich das Video [Versionsübersicht August 2021](https://video.tv.adobe.com/v/336277) an, um eine Zusammenfassung der hinzugefügten Funktionen zu erhalten.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Beim Freigeben digitaler Assets als Link kann der Benutzer die URL sofort in die Zwischenablage kopieren. Dank der Verbesserung können Sie Assets schneller und bequemer freigeben. Diese Funktion ermöglicht eine schnellere und bequeme Asset-Freigabe.

  ![Option „URL kopieren“ beim Freigeben eines Assets als Link](/help/assets/assets/link-share-copy-URL-option.png)
  *Abbildung: Beim Freigeben eines Assets als Link können Sie jetzt die URL kopieren, um sie separat freizugeben.*

* Wenn Sie TXT-Dateien hochladen, generieren die Asset-Microservices automatisch eine Miniaturansicht. Die PNG-Miniaturansicht ist ein Ausgabeformat einer TXT-Datei, mit der Benutzer den Inhalt oder die Dateien bis zu einem gewissen Grad identifizieren können, ohne die Dateien zu öffnen. Diese Funktion erfordert keine Konfiguration und funktioniert standardmäßig.

  ![Eine Ausgabedarstellung einer TXT-Datei wird von [!DNL Assets] automatisch im PNG-Format erzeugt](/help/assets/assets/thumbnail-rendition-txt-file.png)
  *Abbildung: Es wird automatisch eine Ausgabedarstellung einer TXT-Datei erzeugt, damit Sie die Datei identifizieren können, ohne sie zu öffnen.*

### Neue Funktion im [!DNL Assets]-Vorabversionskanal {#assets-prerelease-features}

* Benutzer können jetzt die in den Suchergebnissen angezeigten Assets in Spalten- und Kartenansichten sortieren. Die Sortierung funktioniert bei den Spalten „Name“, „Erstellt“, „Geändert“ oder „Keine“.

  ![Sortieren der Suchergebnisse in [!DNL Assets] in Spalten- und Kartenansichten](/help/assets/assets/sort-searched-assets.png)
  *Abbildung: Sortieren Sie die Suchergebnisse in [!DNL Assets] in Spalten- und Kartenansichten.*

### Fehlerbehebungen in [!DNL Assets] {#assets-bugs-fixed}

* Wenn ein Mitglied der Gruppe &quot;Mitarbeiter&quot;zum [!DNL Assets] Konsole, zusätzliche `POST` -Anfrage generiert, um eine Sammlung zu erstellen. Diese Anfrage ist nicht erforderlich. Sie schlägt aufgrund von Berechtigungsproblemen fehl und führt zu vielen Fehlern in den Protokollen. (CQ-4328856)
* Wenn Benutzer ein Asset anzeigten und die [!UICONTROL Zeitleiste] im Popup-Menü im linken Bereich auswählten, wurde ein Fehler angezeigt. In den Protokollen wurden viele Warnungen aufgrund einer fehlerhaften Abfrage protokolliert. (CQ-4328919)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* Der Service Automated Forms Conversion kann [PDF-Formulare in italienischer und portugiesischer Sprache](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=de?#language-specific-meta-model) in adaptive Formulare konvertieren.

* **AcroForm-basiertes Datensatzdokument**: AEM Forms as a Cloud Service unterstützt neben XFA-basierten Formularvorlagen die Verwendung von [Adobe Acrobat Form PDF (AcroForm PDF)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/generate-document-of-record-for-non-xfa-based-adaptive-forms.html?lang=de) als Vorlage für Datensatzdokumente (DoR, Documents of Record).

* **Microsoft® Azure-Datenspeicher-Connector**: Sie können jetzt [Formulardatenmodell mit Microsoft® Azure Storage verbinden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-azure-storage.html). Dadurch können Sie adaptive Formulardaten abrufen und in Microsoft® Azure Storage as a BLOB speichern.

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Forms] verfügbar {#prerelease-features-forms}

* **Verwenden von Adobe Sign-Rollen in adaptiven Formularen** - Adobe Sign für Service-Levels für Unternehmen und Unternehmen kann optional die Rollen für Empfänger von Vereinbarungen über den Unterzeichner hinaus erweitern, um ihre Workflow-Anforderungen besser zu erfüllen. Sie können jetzt jedem Empfänger der Vereinbarung die Möglichkeit geben, seine Rolle in einem adaptiven Formular zu konfigurieren, wobei der Unterzeichner die Standardrolle ist.

* **Analytics für adaptive Forms** - Sie können jetzt das Endbenutzerverhalten über Adobe Analytics für Adaptive Forms erfassen und verfolgen, um Einblicke von Endbenutzern zu sammeln. Es hilft, informierte, datenbasierte Entscheidungen zu treffen, um das Endbenutzererlebnis zu verbessern.

* **Einfaches Verbinden von AEM Forms mit Microsoft® Dynamics und Salesforce.com** - Der Dienst stellt vorkonfigurierte Datenquellenkonfigurationen und Datenmodelle für Microsoft® Dynamics und Salesforce.com bereit. Dies erleichtert Entwicklern die Konfiguration von Microsoft® Dynamics und Salesforce.com als Datenquellen für adaptive Formulare.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Neue Kategorieauswahl-Benutzeroberfläche für verbesserte Benutzererfahrung, höhere Effizienz und bessere Unterstützung für komplexen Produktkatalog

  ![Neue Kategorieauswahl](/help/assets/CIF/category-picker.png)

* Bessere A11Y-Unterstützung für CIF-Kernkomponenten

## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.8.0 und 2021.7.0.

## Veröffentlichungsdatum {#release-date-cm-aug}

Die Version 2021.8.0 von Cloud Manager in AEM as a Cloud Service wurde am 12. August 2021 veröffentlicht.
Die nächste Version wird am 9. September 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-aug}

* Cloud Service-Kunden können jetzt Berichte zum Service Level Agreement (SLA) in Cloud Manager anzeigen. Dies wird in den nächsten Monaten schrittweise bereitgestellt.
Siehe [SLA-Berichte](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/sla-reporting.html).

* Typ und Schweregrad des IndexType und der `IndexDamAssetLucene`-Qualitätsregeln haben sich geändert. Dies sind nun beide Fehler von Blocker *Schweregrad*.

* Neue Qualitätsregeln für Oak-Indizes wurden eingeführt, um asynchrone und Tika-Konfigurationen abzudecken.

* Die maximale Anzahl von SSL-Zertifikaten pro Programm wurde auf 50 erhöht.

* Self-Service-Funktion, mit der Benutzer über die Cloud Manager-Benutzeroberfläche mehrere Repositorys erstellen und verwalten können.

* SonarQube hat unnötigerweise Git-Verlaufsdaten gelesen. Auf großen Code-Basen konnte dies zu einer unnötigen Build-Leistungsbeeinträchtigung führen.

* Es ist jetzt eine API verfügbar, um den Maven-Abhängigkeits-Cache pro Pipeline zu invalidieren.

* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 29 aktualisiert.

### Fehlerbehebungen {#bug-fixes-aug}

* Update Verfügbar sollte nicht angezeigt werden, wenn die neueste Version kleiner als die aktuelle Version ist.

* Das anfängliche Onboarding schlug bei neuen Unternehmen mit langen Namen fehl.

* Wenn eine Pipeline gelegentlich aus irgendeinem Grund zweimal ausgelöst wird, führt dies dazu, dass eine der Ausführungen mit einem *`cannot update pipeline execution status`* Fehler.

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt-latest}

Die Version 1.5.6 von Content Transfer Tool wurde am 11. August 2021 veröffentlicht.

### Fehlerbehebungen {#bug-fixes-ctt}

* Manchmal wurden nicht alle Benutzer in die Zielinstanz migriert. Um diese Fehlerbehebung zu erhalten, ist die CTT-Version 1.5.6 zusammen mit aem-ethos-tools 1.2.354 oder einer höheren Version auf der as a Cloud Service Zielinstanz AEM erforderlich.

* Die Schaltfläche **Aufnahme stoppen** wird jetzt während der Aufnahme in die Veröffentlichungsinstanz nicht mehr deaktiviert. Dies war nicht erforderlich, da es während der Aufnahme der Veröffentlichung keinen Schritt „mongo restore“ gibt.

* Das CTT bereinigte das `/tmp`-Verzeichnis nach erfolgreicher Extraktion nicht. Dies führte manchmal zu Problemen mit dem Festplattenspeicher.
