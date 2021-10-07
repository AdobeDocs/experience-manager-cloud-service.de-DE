---
title: Versionshinweise für Version 2021.8.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2021.8.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: d37193833d784f3f470780b8f28e53b473fd4e10
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 39%

---


# Aktuelle Versionshinweise für[!DNL Adobe Experience Manager]as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen navigieren. z. B. für die 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] als [!DNL Cloud Service] aktuelle Version (2021.8.0) ist der 26. August 2021.
Die folgende Version (2021.9.0) wurde am 6. Oktober 2021 veröffentlicht.

## Release Video {#release-video}

Sehen Sie sich das Video [Versionsübersicht August 2021](https://video.tv.adobe.com/v/336277) an, um eine Zusammenfassung der hinzugefügten Funktionen zu erhalten.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Beim Freigeben digitaler Assets als Link können Benutzer die URL sofort in die Zwischenablage kopieren. Dank der Verbesserung können Sie Assets schneller und bequemer freigeben. Diese Funktion ermöglicht eine schnellere und bequeme Asset-Freigabe.

   ![Option &quot;URL kopieren&quot;, wenn ein Asset als Link freigegeben wird](/help/assets/assets/link-share-copy-URL-option.png)
   *Abbildung: Beim Freigeben eines Assets als Link können Sie jetzt die URL kopieren, um sie separat freizugeben.*

* Beim Hochladen von TXT-Dateien generiert der Asset-Microservice automatisch eine Miniaturansicht. Die PNG-Miniaturansicht ist eine Ausgabe der TXT-Datei, die Benutzern dabei hilft, Inhalte oder Dateien in einem gewissen Umfang zu identifizieren, ohne die Dateien zu öffnen. Diese Funktion erfordert keine Konfiguration und funktioniert standardmäßig.

   ![Eine Ausgabe einer TXT-Datei wird automatisch von  [!DNL Assets] im PNG-Format generiert](/help/assets/assets/thumbnail-rendition-txt-file.png)
   *Abbildung: Eine TXT-Datei wird automatisch in einer Ausgabedarstellung erzeugt, damit Sie die Datei ohne Öffnen identifizieren können.*

### Neue Funktion im Kanal [!DNL Assets] der Vorabversion {#assets-prerelease-features}

* Benutzer können nun die in den Suchergebnissen in den Spalten- und Kartenansichten angezeigten Assets sortieren. Die Sortierung funktioniert mit den Spalten &quot;Name&quot;, &quot;Erstellt&quot;, &quot;Geändert&quot;oder &quot;Keine&quot;.

   ![Sortieren Sie die Suchergebnisse  [!DNL Assets] in Spalten- und Kartenansichten.](/help/assets/assets/sort-searched-assets.png)
   *Abbildung: Sortieren Sie die Suchergebnisse  [!DNL Assets] in Spalten- und Kartenansichten.*

### Fehlerbehebungen in [!DNL Assets] {#assets-bugs-fixed}

* Wenn ein Mitglied der Gruppe &quot;Mitarbeiter&quot;zur Konsole [!DNL Assets] navigiert, wird eine zusätzliche `POST` -Anfrage generiert, um zu versuchen, eine Sammlung zu erstellen. Diese Anfrage ist nicht erforderlich, schlägt aufgrund von Berechtigungsproblemen fehl und führt zu vielen Fehlern in den Protokollen. (CQ-4328856)
* Wenn Benutzer ein Asset anzeigen und [!UICONTROL Timeline] aus dem Popup-Menü im linken Bereich auswählen, wird ein Fehler angezeigt. In den Protokollen werden viele Warnungen aufgrund einer fehlerhaften Abfrage protokolliert. (CQ-4328919)

## [!DNL Experience Manager Forms] as a  [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* Der automated forms conversion-Dienst kann [PDF forms in italienischer und portugiesischer Sprache](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=de#language-specific-meta-model) in adaptive Forms konvertieren.

* **AcroForm-basiertes Datensatzdokument**: AEM Forms as a Cloud Service unterstützt neben XFA-basierten Formularvorlagen die Verwendung von [Adobe Acrobat Form PDF (AcroForm PDF)](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html?lang=de) als Vorlage für Datensatzdokumente (DoR, Documents of Record).

* **Microsoft Azure-Datenspeicher-Connector**: Sie können jetzt das [Formulardatenmodell mit dem Microsoft Azure-Speicher verbinden](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html?lang=de). Dadurch können Sie Daten adaptiver Formulare abrufen und im Microsoft Azure-Speicher als BLOB speichern.

### Neue Funktionen im Kanal für die [!DNL Forms]-Vorabversion {#prerelease-features-forms}

* **Verwenden von Adobe Sign-Rollen in einem adaptiven Formular**: Die Service-Levels von Adobe Sign für Unternehmen bieten die Möglichkeit, die Rollen von Empfängern von Vereinbarungen über die unterschreibende Person hinaus zu erweitern und so ihren Workflow-Anforderungen besser zu entsprechen. Sie können jetzt jedem Empfänger der Vereinbarung die Möglichkeit geben, seine Rolle in einem adaptiven Formular zu konfigurieren, wobei „Unterschreibende Person“ die Standardrolle ist.

* **Analytics für adaptive Formulare**: Sie können jetzt das Endbenutzerverhalten über Adobe Analytics für adaptive Formulare erfassen und verfolgen, um Erkenntnisse über Endbenutzer zu sammeln. Es hilft dabei, fundierte Entscheidungen auf der Grundlage von Daten zu treffen, um das Erlebnis der Endbenutzer zu verbessern.

* **Verbinden Sie AEM Forms einfach mit Microsoft Dynamics und Salesforce.com**: Der Dienst stellt vordefinierte Datenquellenkonfigurationen und Datenmodelle für Microsoft Dynamics und Salesforce.com bereit, sodass Entwickler Microsoft Dynamics und Salesforce.com schneller und einfacher als Datenquellen für adaptive Formulare konfigurieren können.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Neue Kategorieauswahl-Benutzeroberfläche für verbesserte Benutzererfahrung, höhere Effizienz und bessere Unterstützung komplexer Produktkataloge

   ![Neue Kategorieauswahl](/help/assets/CIF/category-picker.png)

* Bessere A11Y-Unterstützung für CIF-Kernkomponenten

## Cloud Manager  {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.8.0 und 2021.7.0.

## Veröffentlichungsdatum {#release-date-cm-aug}

Die Cloud Manager -Version AEM as a Cloud Service Version 2021.8.0 wurde am 12. August 2021 veröffentlicht.
Die nächste Version wird am 9. September 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-aug}

* Cloud Service können jetzt Berichte zur Service Level Agreement (SLA) in Cloud Manager anzeigen. Dies wird in den nächsten Monaten schrittweise bereitgestellt.
Weitere Informationen finden Sie unter [SLA Reporting](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sla-reporting.html) .

* Typ und Schweregrad der Qualitätsregeln IndexType und `IndexDamAssetLucene` wurden geändert. Dies sind nun beide Fehler von Blocker *serverity*.

* Neue Qualitätsregeln für Oak-Indizes wurden eingeführt, um asynchrone und tika-Konfigurationen abzudecken.

* Erhöhen Sie die maximale Anzahl von SSL-Zertifikaten pro Programm auf 50.

* Self-Service-Funktion, mit der Benutzer über die Cloud Manager-Benutzeroberfläche mehrere Repositorys erstellen und verwalten können.

* SonarQube liest unnötigerweise Git-Verlaufsdaten. Auf großen Code-Basen konnte dies zu einer unnötigen Build-Leistungsbeeinträchtigung führen.

* Es ist jetzt eine API verfügbar, um den Maven-Abhängigkeits-Cache pro Pipeline zu invalidieren.

* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 29 aktualisiert.

### Fehlerbehebungen {#bug-fixes-aug}

* Fehlerkorrektur – Der Status Update verfügbar wird nicht mehr angezeigt, wenn die neueste Version kleiner als die aktuelle Version ist.

* Das anfängliche Onboarding schlug bei neuen Unternehmen mit sehr langen Namen fehl.

* Wenn eine Pipeline gelegentlich aus irgendeinem Grund zweimal ausgelöst wird, führt dies nicht mehr dazu, dass eine der Ausführungen mit dem Fehler *Pipeline-Ausführungsstatus konnte nicht aktualisiert werden* fehlschlägt.

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt-latest}

Die Version 1.5.6 des Content Transfer Tool wurde am 11. August 2021 veröffentlicht.

### Fehlerbehebungen {#bug-fixes-ctt}

* In einigen Fällen wurden nicht alle Benutzer in die Zielinstanz migriert. Um diese Fehlerbehebung zu erhalten, ist die CTT-Version 1.5.6 zusammen mit AEM-ethos-Tools 1.2.354 oder einer höheren Version auf der as a Cloud Service Zielinstanz AEM erforderlich.

* Die Schaltfläche **Aufnahme stoppen** wurde während der Aufnahme in die Veröffentlichungsinstanz deaktiviert. Dies ist nicht erforderlich, da es während der Aufnahme der Veröffentlichung keinen mongo restore -Schritt gibt.

* Die CTT hat das Verzeichnis `/tmp` nach einer erfolgreichen Extraktion nicht bereinigt. Dies führte manchmal zu Problemen mit dem Festplattenspeicher.
