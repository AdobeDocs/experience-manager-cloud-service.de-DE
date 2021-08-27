---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 6277325b80f1cdb8735f88b5ad856e405572bffe
workflow-type: tm+mt
source-wordcount: '1367'
ht-degree: 27%

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
Die folgende Version (2021.9.0) wurde am 30. September 2021 veröffentlicht.

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

<!-- * Automated Forms Conversion service can [convert PDF Forms in Italian and Portuguese language](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) to Adaptive Forms. -->

* AEM Archetypprojekt für Forms as a Cloud Service enthält jetzt das [Canvas 3.0-Design und die Formulardatenmodelle für Microsoft Dynamics und Salesforce.com](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/setup-environment/setup-local-development-environment.html?#forms-cloud-service-local-development-environment).

* **Acroform-based Document of Record**: AEM Forms as a Cloud Service unterstützt die Verwendung von  [Adobe Acrobat Form PDF (Acroform PDF)](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html?lang=de)  als Vorlage für Datensatzdokument neben XFA-basierten Formularvorlagen.

* **Microsoft Azure-Datenspeicher-Connector**: Sie können jetzt das [Formulardatenmodell mit dem Microsoft Azure-Speicher verbinden](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html?lang=de). Dadurch können Sie Daten adaptiver Formulare abrufen und im Microsoft Azure-Speicher als BLOB speichern.

### Beta-Funktion von [!DNL Forms] {#aug-what-is-new-forms-prerelease}

* **Unified Storage Connector:** Verwenden Sie Unified Storage Connector, um In-Process-Daten in kundenverwalteten Repositorys zu externalisieren. Sie können beispielsweise
   * Aktivieren Sie die Funktion zum Speichern und Fortsetzen von Forms Portal und speichern Sie adaptive Formularentwürfe in einem kundenverwalteten Datenrepository.
   * Speichern Sie AEM Workflow-Daten (AEM Workflow-Variablen-Daten), die vertrauliche personenbezogene Daten (EPPD) enthalten, in einem kundenverwalteten Repository.

* **[!DNL AEM Forms as a Cloud Service - Communications]**: Mithilfe von [Kommunikations-APIs](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/aem-forms-cloud-service-communications.html?lang=de) können Sie XDP-Vorlagen und XML-Daten kombinieren, um Print-Dokumente in verschiedenen Formaten zu erzeugen. Mit diesem Service können Sie Dokumente im synchronen Modus erstellen. Dabei können Sie mit den APIs Programme mit folgenden Funktionen erstellen:
   * Generieren von Dokumenten durch Füllen von Vorlagendateien mit XML-Daten
   * Generieren von Ausgabeformularen in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Printstreams.
   * Generieren von PDF-Print-Dateien aus einem PDF-XFA-Formular und einem Adobe Acrobat-Formular.

Sie können sich an [!DNL formscsbeta@adobe.com] wenden, um sich für das Beta-Programm anzumelden.

### Neue Funktionen im Kanal für die [!DNL Forms]-Vorabversion {#prerelease-features-forms}

* **Verwenden Sie Adobe Sign-Rollen in einem adaptiven Formular**: Die Service-Levels von Adobe Sign für Unternehmen und Unternehmen bieten die Möglichkeit, die Rollen von Vertragsempfängern über den Unterzeichner hinaus zu erweitern und so ihren Workflow-Anforderungen besser zu entsprechen. Sie können jetzt [jedem Empfänger der Vereinbarung die Möglichkeit geben, seine Rolle in einem adaptiven Formular](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/use-adobe-sign/working-with-adobe-sign.html?#addsignerstoanadaptiveform) zu konfigurieren, wobei &quot;Unterzeichner&quot;die Standardrolle ist.

* **Analytics für adaptive Forms**: Sie können jetzt das Endbenutzerverhalten über Adobe Analytics für Adaptive Forms erfassen und verfolgen, um Einblicke von Endbenutzern zu sammeln. Es hilft, informierte, datenbasierte Entscheidungen zu treffen, um das Endbenutzererlebnis zu verbessern.

* **Verbinden Sie AEM Forms einfach mit Microsoft Dynamics und Salesforce.com**: Der Dienst bietet vordefinierte Datenquellenkonfigurationen und Datenmodelle für Microsoft Dynamics und Salesforce.com, wodurch es Entwicklern  [schneller und einfacher wird, Microsoft Dynamics und Salesforce.com als Datenquellen für ein adaptives Formular](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-msdynamics-salesforce.html) zu konfigurieren.

## [!DNL Screens] as a  [!DNL Cloud Service] {#screens}

### Neue Funktionen {#what-is-new-screens}

* Als Inhaltsautor können Sie jetzt eine Miniaturansicht für Videos definieren, damit Sie dieses Bild als Platzhalter verwenden und die Inhaltswiedergabe und das Targeting ordnungsgemäß testen können, während das eigentliche Video vom entsprechenden Team fertig gestellt wird.
Weitere Informationen finden Sie unter [Grundlegende Wiedergabe-Überwachung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/manage-player-registration/installing-screens-cloud-player.html?lang=en#playback-monitoring) .

* Unterstützung von Miniaturbildern für Videos in wird jetzt in Screens as a Cloud Service unterstützt. Ein Inhaltsautor kann eine Miniaturansicht für Videos definieren, sodass das Bild als Platzhalter verwendet und die Inhaltswiedergabe und das Targeting ordnungsgemäß getestet werden kann, während das eigentliche Video vom entsprechenden Team fertig gestellt wird. Das Bild kann auch verwendet werden, falls die Wiedergabe des Videos fehlschlägt.

### Fehlerbehebungen {#bug-fixes-screens}

* Der Player konnte keine Inhalte von der eingebetteten Seite anzeigen. Dieses Problem wurde behoben.

* Nach erfolgreicher Anmeldung wurde die Seite &quot;Interner Server-Fehler&quot;angezeigt, auf der die Standardseite (Kanäle) aufgerufen wurde.

* Zugehörige Tag-Einträge wurden beim Entfernen der Wiedergabeliste(n) nicht entfernt.


## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Neue Kategorieauswahl-Benutzeroberfläche für verbesserte Benutzererfahrung, höhere Effizienz und bessere Unterstützung komplexer Produktkataloge

   ![Neue Kategorieauswahl](/help/assets/CIF/category-picker.png)

* Bessere A11Y-Unterstützung für CIF-Kernkomponenten

## Cloud Manager  {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.8.0 und 2021.7.0.

## Veröffentlichungsdatum {#release-date-cm-aug}

Die Version 2021.8.0 von Cloud Manager in AEM as a Cloud Service wurde am 12. August 2021 veröffentlicht.
Die nächste Version wird am 9. September 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-aug}

* Cloud Service können jetzt Berichte zur Service Level Agreement (SLA) in Cloud Manager anzeigen. Dies wird in den nächsten Monaten schrittweise bereitgestellt.
Weitere Informationen finden Sie unter [SLA Reporting](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sla-reporting.html) .

* Typ und Schweregrad der Qualitätsregeln IndexType und `IndexDamAssetLucene` wurden geändert. Dies sind nun beide Fehler von Blocker *serverity*.

* Neue Qualitätsregeln für Oak-Indizes wurden eingeführt, um asynchrone und tika-Konfigurationen abzudecken.

* Erhöhen Sie die maximale Anzahl von SSL-Zertifikaten pro Programm auf 50.

* Self-Service-Funktion, mit der Benutzer über die Cloud Manager-Benutzeroberfläche mehrere Repositorys erstellen und verwalten können.

* SonarQube liest unnötigerweise Git-Verlaufsdaten. Auf großen Code-Basien konnte dies zu einer unnötigen Build-Leistungsbeeinträchtigung führen.

* Es ist jetzt eine API verfügbar, um den Maven-Abhängigkeits-Cache pro Pipeline zu invalidieren.

* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 29 aktualisiert.

### Fehlerbehebungen {#bug-fixes-aug}

* Fehlerkorrektur – Der Status Update verfügbar wird nicht mehr angezeigt, wenn die neueste Version kleiner als die aktuelle Version ist.

* Das anfängliche Onboarding schlug bei neuen Unternehmen mit sehr langen Namen fehl.

* Fehlerkorrektur – Wenn eine Pipeline gelegentlich aus irgendeinem Grund zweimal ausgelöst wird, führt dies nicht mehr dazu, dass eine der Ausführungen mit dem Fehler *Pipeline-Ausführungsstatus konnte nicht aktualisiert werden* fehlschlägt.

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt-latest}

Die Version 1.5.6 des Content Transfer Tool wurde am 11. August 2021 veröffentlicht.

### Fehlerbehebungen {#bug-fixes-ctt}

* In einigen Fällen wurden nicht alle Benutzer in die Zielinstanz migriert. Um diese Fehlerbehebung zu erhalten, ist die CTT-Version 1.5.6 zusammen mit AEM-ethos-Tools 1.2.354 oder einer höheren Version auf der Ziel-AEM als Cloud Service-Instanz erforderlich.

* Die Schaltfläche **Aufnahme stoppen** wurde während der Aufnahme in die Veröffentlichungsinstanz deaktiviert. Dies ist nicht erforderlich, da es während der Aufnahme der Veröffentlichung keinen mongo restore -Schritt gibt.

* Die CTT hat das Verzeichnis `/tmp` nach einer erfolgreichen Extraktion nicht bereinigt. Dies führte manchmal zu Problemen mit dem Festplattenspeicher.

