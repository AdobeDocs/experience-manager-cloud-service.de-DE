---
title: Versionshinweise für Version 2021.8.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Versionshinweise für Version 2021.8.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
source-git-commit: d37193833d784f3f470780b8f28e53b473fd4e10
workflow-type: ht
source-wordcount: '1032'
ht-degree: 100%

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

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2021.8.0) war der 26. August 2021.
Die folgende Version (2021.9.0) wurde am 6. Oktober 2021 veröffentlicht.

## Video zur Version {#release-video}

Sehen Sie sich das Video [Versionsübersicht August 2021](https://video.tv.adobe.com/v/336277) an, um eine Zusammenfassung der hinzugefügten Funktionen zu erhalten.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Beim Freigeben digitaler Assets als Link können Benutzer die URL sofort in die Zwischenablage kopieren. Dank der Verbesserung können Sie Assets schneller und bequemer freigeben. Diese Funktion ermöglicht eine schnellere und bequeme Asset-Freigabe.

   ![Option „URL kopieren“ beim Freigeben eines Assets als Link](/help/assets/assets/link-share-copy-URL-option.png)
   *Abbildung: Beim Freigeben eines Assets als Link können Sie jetzt die URL kopieren, um sie separat freizugeben.*

* Beim Hochladen von TXT-Dateien erzeugt der Asset-Microservice automatisch eine Miniaturansicht. Die PNG-Miniaturansicht ist eine Ausgabedarstellung der TXT-Datei, die Benutzern dabei hilft, Inhalte oder Dateien in einem gewissen Umfang zu identifizieren, ohne die Dateien zu öffnen. Diese Funktion erfordert keine Konfiguration und funktioniert standardmäßig.

   ![Eine Ausgabedarstellung einer TXT-Datei wird von [!DNL Assets] automatisch im PNG-Format erzeugt](/help/assets/assets/thumbnail-rendition-txt-file.png)
   *Abbildung: Es wird automatisch eine Ausgabedarstellung einer TXT-Datei erzeugt, damit Sie die Datei identifizieren können, ohne sie zu öffnen.*

### Neue Funktion im [!DNL Assets]-Vorabversionskanal {#assets-prerelease-features}

* Benutzer können jetzt die in den Suchergebnissen angezeigten Assets in Spalten- und Kartenansichten sortieren. Die Sortierung funktioniert bei den Spalten „Name“, „Erstellt“, „Geändert“ oder „Keine“.

   ![Sortieren der Suchergebnisse in [!DNL Assets] in Spalten- und Kartenansichten](/help/assets/assets/sort-searched-assets.png)
   *Abbildung: Sortieren Sie die Suchergebnisse in [!DNL Assets] in Spalten- und Kartenansichten.*

### Fehlerbehebungen in [!DNL Assets] {#assets-bugs-fixed}

* Wenn ein Mitglied der Beitragendengruppe zur [!DNL Assets]-Konsole navigierte, wurde eine zusätzliche `POST`-Anfrage erzeugt und versucht, eine Sammlung zu erstellen. Diese Anfrage war nicht erforderlich, schlug aufgrund von Berechtigungsproblemen fehl und führte zu vielen Fehlern in den Protokollen. (CQ-4328856)
* Wenn Benutzer ein Asset anzeigten und die [!UICONTROL Zeitleiste] im Popup-Menü im linken Bereich auswählten, wurde ein Fehler angezeigt. In den Protokollen wurden viele Warnungen aufgrund einer fehlerhaften Abfrage protokolliert. (CQ-4328919)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* Der Service Automated Forms Conversion kann [PDF-Formulare in italienischer und portugiesischer Sprache](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=de?#language-specific-meta-model) in adaptive Formulare konvertieren.

* **AcroForm-basiertes Datensatzdokument**: AEM Forms as a Cloud Service unterstützt neben XFA-basierten Formularvorlagen die Verwendung von [Adobe Acrobat Form PDF (AcroForm PDF)](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html?lang=de) als Vorlage für Datensatzdokumente (DoR, Documents of Record).

* **Microsoft Azure-Datenspeicherungs-Connector**: Sie können jetzt das [Formulardatenmodell mit der Microsoft Azure-Datenspeicherung verbinden](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html?lang=de). Dadurch können Sie Daten aus adaptiven Formularen abrufen und in der Microsoft Azure-Datenspeicherung als BLOB speichern.

### Neue Funktionen im Kanal für die [!DNL Forms]-Vorabversion {#prerelease-features-forms}

* **Verwenden von Adobe Sign-Rollen in einem adaptiven Formular**: Die Service-Levels von Adobe Sign für Unternehmen bieten die Möglichkeit, die Rollen von Empfängern von Vereinbarungen über die unterschreibende Person hinaus zu erweitern und so ihren Workflow-Anforderungen besser zu entsprechen. Sie können jetzt jedem Empfänger der Vereinbarung die Möglichkeit geben, seine Rolle in einem adaptiven Formular zu konfigurieren, wobei „Unterschreibende Person“ die Standardrolle ist.

* **Analytics für adaptive Formulare**: Sie können jetzt das Endbenutzerverhalten über Adobe Analytics für adaptive Formulare erfassen und verfolgen, um Erkenntnisse über Endbenutzer zu sammeln. Es hilft dabei, fundierte Entscheidungen auf der Grundlage von Daten zu treffen, um das Erlebnis der Endbenutzer zu verbessern.

* **Einfaches Verbinden von AEM Forms mit Microsoft Dynamics und Salesforce.com**: Der Service stellt vorkonfigurierte Datenquellenkonfigurationen und Datenmodelle für Microsoft Dynamics und Salesforce.com bereit, sodass Entwickler Microsoft Dynamics und Salesforce.com schneller und einfacher als Datenquellen für adaptive Formulare konfigurieren können.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Neue Kategorieauswahl-Benutzeroberfläche für ein verbessertes Benutzererlebnis, höhere Effizienz und bessere Unterstützung komplexer Produktkataloge

   ![Neue Kategorieauswahl](/help/assets/CIF/category-picker.png)

* Bessere A11Y-Unterstützung für CIF-Kernkomponenten

## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.8.0 und 2021.7.0.

## Veröffentlichungsdatum {#release-date-cm-aug}

Die Version 2021.8.0 von Cloud Manager in AEM as a Cloud Service wurde am 12. August 2021 veröffentlicht.
Die nächste Version wird am 9. September 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-aug}

* Cloud Service-Kunden können jetzt Berichte zum Service Level Agreement (SLA) in Cloud Manager anzeigen. Dies wird in den nächsten Monaten schrittweise bereitgestellt.
Weitere Informationen finden Sie im Abschnitt [SLA-Reporting](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sla-reporting.html?lang=de).

* Typ und Schweregrad des IndexType und der `IndexDamAssetLucene`-Qualitätsregeln haben sich geändert. Dies sind nun beides Fehler vom *Schweregrad* „Blocker“.

* Neue Qualitätsregeln für Oak-Indizes wurden eingeführt, um asynchrone und tika-Konfigurationen abzudecken.

* Die maximale Anzahl von SSL-Zertifikaten pro Programm wurde auf 50 erhöht.

* Self-Service-Funktion, mit der Benutzer über die Cloud Manager-Benutzeroberfläche mehrere Repositorys erstellen und verwalten können.

* SonarQube hat unnötigerweise Git-Verlaufsdaten gelesen. Auf großen Code-Basen konnte dies zu einer unnötigen Build-Leistungsbeeinträchtigung führen.

* Es ist jetzt eine API verfügbar, um den Maven-Abhängigkeits-Cache pro Pipeline zu invalidieren.

* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 29 aktualisiert.

### Fehlerbehebungen {#bug-fixes-aug}

* Der Status „Update verfügbar“ wird nicht mehr angezeigt, wenn die neueste Version niedriger als die aktuelle Version ist.

* Das anfängliche Onboarding schlägt bei neuen Organisationen mit sehr langen Namen nicht mehr fehl.

* Wenn eine Pipeline gelegentlich aus irgendeinem Grund zweimal ausgelöst wird, führt dies nicht mehr dazu, dass eine der Ausführungen mit dem Fehler *Pipeline-Ausführungsstatus konnte nicht aktualisiert werden* fehlschlägt.

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt-latest}

Die Version 1.5.6 von Content Transfer Tool wurde am 11. August 2021 veröffentlicht.

### Fehlerbehebungen {#bug-fixes-ctt}

* In einigen Fällen wurden nicht alle Benutzer in die Zielinstanz migriert. Um diesen Fehler zu beheben, ist die CTT-Version 1.5.6 zusammen mit aem-ethos-tools 1.2.354 oder einer höheren Version auf der AEM as a Cloud Service-Zielinstanz erforderlich.

* Die Schaltfläche **Aufnahme stoppen** wird jetzt während der Aufnahme in die Veröffentlichungsinstanz nicht mehr deaktiviert. Dies war nicht erforderlich, da es während der Aufnahme der Veröffentlichung keinen Schritt „mongo restore“ gibt.

* Das CTT bereinigte das `/tmp`-Verzeichnis nach erfolgreicher Extraktion nicht. Dies führte manchmal zu Problemen mit dem Festplattenspeicher.
