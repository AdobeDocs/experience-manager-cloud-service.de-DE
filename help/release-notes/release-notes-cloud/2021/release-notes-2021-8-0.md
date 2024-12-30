---
title: Versionshinweise für Version 2021.8.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Versionshinweise für Version 2021.8.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 8b041934-1c4a-4670-9b03-d38f683b99e5
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1011'
ht-degree: 62%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. Zum Beispiel für die Jahre 2020 und 2021.

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

* Beim Hochladen von TXT-Dateien generieren die Asset-Microservices automatisch eine Miniaturansicht. Die PNG-Miniaturansicht ist eine Ausgabedarstellung einer TXT-Datei, die Benutzern das Identifizieren von Inhalten oder Dateien erleichtert, ohne die Dateien zu öffnen. Diese Funktion erfordert keine Konfiguration und funktioniert standardmäßig.

  ![Eine Ausgabedarstellung einer TXT-Datei wird von [!DNL Assets] automatisch im PNG-Format erzeugt](/help/assets/assets/thumbnail-rendition-txt-file.png)
  *Abbildung: Es wird automatisch eine Ausgabedarstellung einer TXT-Datei erzeugt, damit Sie die Datei identifizieren können, ohne sie zu öffnen.*

### Neue Funktion im [!DNL Assets]-Vorabversionskanal {#assets-prerelease-features}

* Benutzer können jetzt die in den Suchergebnissen angezeigten Assets in Spalten- und Kartenansichten sortieren. Die Sortierung funktioniert bei den Spalten „Name“, „Erstellt“, „Geändert“ oder „Keine“.

  ![Sortieren der Suchergebnisse in [!DNL Assets] in Spalten- und Kartenansichten](/help/assets/assets/sort-searched-assets.png)
  *Abbildung: Sortieren Sie die Suchergebnisse in [!DNL Assets] in Spalten- und Kartenansichten.*

### Fehlerbehebungen in [!DNL Assets] {#assets-bugs-fixed}

* Wenn ein Mitglied der Beitragendengruppe zur [!DNL Assets] Console navigiert, wird eine zusätzliche `POST` generiert, um eine Sammlung zu erstellen. Diese Anfrage ist nicht erforderlich, schlägt aufgrund von Berechtigungsproblemen fehl und verursacht viele Fehler in den Protokollen. (CQ-4328856)
* Wenn Benutzende ein Asset anzeigen und die [!UICONTROL Zeitleiste] im Popup-Menü im linken Bereich auswählen, wird ein Fehler angezeigt. In den Protokollen wurden viele Warnungen aufgrund einer fehlerhaften Abfrage protokolliert. (CQ-4328919)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* Der Service Automated Forms Conversion kann [PDF-Formulare in italienischer und portugiesischer Sprache](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=de?#language-specific-meta-model) in adaptive Formulare konvertieren.

* **AcroForm-basiertes Datensatzdokument**: AEM Forms as a Cloud Service unterstützt neben XFA-basierten Formularvorlagen die Verwendung von [Adobe Acrobat Form PDF (AcroForm PDF)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/generate-document-of-record-for-non-xfa-based-adaptive-forms.html?lang=de) als Vorlage für Datensatzdokumente (DoR, Documents of Record).

* **Microsoft® Azure-Datenspeicher-Connector**: Sie können jetzt [Formulardatenmodell mit Microsoft verbinden® Azure-Speicher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-azure-storage.html). Damit können Sie Daten adaptiver Formulare abrufen und im Microsoft® Azure-Speicher als BLOB speichern.

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Forms] verfügbar {#prerelease-features-forms}

* **Verwenden von Adobe Sign-Rollen in einem adaptiven Formular** - Adobe Sign für Business- und Enterprise Service-Levels kann optional die Rollen für Empfangende von Vereinbarungen über die unterschreibende Person hinaus erweitern, um deren Workflow-Anforderungen besser zu erfüllen. Sie können jetzt jedem Empfänger der Vereinbarung die Möglichkeit geben, seine Rolle in einem adaptiven Formular zu konfigurieren, wobei „Unterschreibende Person“ die Standardrolle ist.

* **Analytics für Adaptive Forms** - Sie können jetzt das Endbenutzerverhalten über Adobe Analytics für Adaptive Forms erfassen und verfolgen, um Erkenntnisse über Endbenutzern zu sammeln. Es hilft dabei, fundierte Entscheidungen auf der Grundlage von Daten zu treffen, um das Endbenutzererlebnis zu verbessern.

* **Einfaches Verbinden von AEM Forms mit Microsoft® Dynamics und Salesforce.com** - Der Service stellt vorkonfigurierte Datenquellenkonfigurationen und Datenmodelle für Microsoft® Dynamics und Salesforce.com bereit. Dadurch können Entwickler Microsoft® Dynamics und Salesforce.com schneller und einfacher als Datenquellen für adaptive Formulare konfigurieren.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Neue Benutzeroberfläche zur Kategorieauswahl für ein verbessertes Benutzererlebnis, höhere Effizienz und bessere Unterstützung bei komplexen Produktkatalogen

  ![Neue Kategorieauswahl](/help/assets/CIF/category-picker.png)

* Bessere A11Y-Unterstützung für CIF-Kernkomponenten

## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.8.0 und 2021.7.0.

## Veröffentlichungsdatum {#release-date-cm-aug}

Die Version 2021.8.0 von Cloud Manager in AEM as a Cloud Service wurde am 12. August 2021 veröffentlicht.
Die nächste Version wird am 9. September 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-aug}

* Cloud Service-Kunden können jetzt Berichte zum Service Level Agreement (SLA) in Cloud Manager anzeigen. Dies wird in den nächsten Monaten schrittweise zur Verfügung gestellt.
Siehe [SLA-Berichte](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/sla-reporting.html).

* Typ und Schweregrad des IndexType und der `IndexDamAssetLucene`-Qualitätsregeln haben sich geändert. Dies sind nun beide Bugs of Blocker *Schweregrad*.

* Neue Qualitätsregeln für Oak-Indizes wurden eingeführt, um asynchrone und Tika-Konfigurationen abzudecken.

* Die maximale Anzahl von SSL-Zertifikaten pro Programm wurde auf 50 erhöht.

* Eine Self-Service-Funktion, die es Benutzenden ermöglicht, über die Cloud-Manager-Benutzeroberfläche mehrere Repositorys zu erstellen und zu verwalten.

* SonarQube las unnötigerweise Git-Verlaufsdaten. Auf großen Code-Basen konnte dies zu einer unnötigen Build-Leistungsbeeinträchtigung führen.

* Es ist jetzt eine API verfügbar, um den Maven-Abhängigkeits-Cache pro Pipeline zu invalidieren.

* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 29 aktualisiert.

### Fehlerbehebungen {#bug-fixes-aug}

* Der Status Update verfügbar wird nicht mehr angezeigt, wenn die neueste Version kleiner als die aktuelle Version ist.

* Das anfängliche Onboarding schlägt bei neuen Organisationen mit langen Namen nicht mehr fehl.

* Wenn eine Pipeline aus irgendeinem Grund zweimal ausgelöst wird, schlägt eine der Ausführungen gelegentlich mit einem Fehler *`cannot update pipeline execution status`* fehl.

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt-latest}

Die Version 1.5.6 von Content Transfer Tool wurde am 11. August 2021 veröffentlicht.

### Fehlerbehebungen {#bug-fixes-ctt}

* Manchmal wurden nicht alle Benutzer zur Zielinstanz migriert. Um diese Fehlerbehebung vorzunehmen, ist CTT v1.5.6 zusammen mit aem-ethos-tools 1.2.354 oder einer neueren Version auf der AEM as a Cloud Service-Zielinstanz erforderlich.

* Die Schaltfläche **Aufnahme stoppen** wird jetzt während der Aufnahme in die Veröffentlichungsinstanz nicht mehr deaktiviert. Dies war nicht erforderlich, da es während der Aufnahme der Veröffentlichung keinen Schritt „mongo restore“ gibt.

* Das CTT bereinigte das `/tmp`-Verzeichnis nach erfolgreicher Extraktion nicht. Dies führte manchmal zu Problemen mit dem Festplattenspeicher.
