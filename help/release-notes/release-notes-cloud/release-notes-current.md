---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 0ad1218ceb486a5b0feebebecece741eea2148cd
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 27%

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

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] Die aktuelle Version (2022.1.0) ist der 3. Februar 2022.
Die folgende Version (2022.2.0) wurde am 24. Februar 2022 veröffentlicht.

## Video zur Version {#release-video}

Sehen Sie sich die [Versionsübersicht Januar 2022](https://video.tv.adobe.com/v/340120) Video mit einer Zusammenfassung der Funktionen, die in der Version 2022.1.0 hinzugefügt wurden.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* [!DNL Dynamic Media] - Sie können jetzt AEM Dynamic Media-Benutzeroberfläche verwenden, um allgemeine Einstellungen und Veröffentlichungseinstellungen zu konfigurieren, anstatt die Dynamic Media Classic-Desktop-Applikation durchlaufen zu müssen.

* [!DNL Dynamic Media] unterstützt jetzt Erfassung, Vorschau, Wiedergabe und Veröffentlichung für MXF-Videos. Anmerkungen und Videos mit Shopping-Funktion für MXF-Videos werden noch nicht unterstützt.

* Nach dem Konfigurieren einer Verbindung zwischen Remote-DAM- und Sites-Bereitstellungen werden die Assets auf Remote-DAM in der Sites-Bereitstellung verfügbar gemacht. Sie können jetzt die [Vorgänge aktualisieren, löschen, umbenennen und verschieben](/help/assets/use-assets-across-connected-assets-instances.md) auf den Remote-DAM-Assets oder -Ordnern. Die Aktualisierungen sind mit einiger Verzögerung automatisch in der Sites-Bereitstellung verfügbar.

### Neue Funktionen in [!DNL Assets] Vorabversionskanal {#assets-prerelease-features}

* [!DNL AEM Dynamic Media] bietet jetzt die Flexibilität, [ein Alias-Konto konfigurieren](../../assets/dynamic-media/dm-alias-account.md) in der Benutzeroberfläche, um sicherzustellen, dass native Dynamic Media-URLs und der Viewer-Einbettungscode aktualisiert werden. Dies wirkt sich positiv auf SEO aus, um Aktualisierungen an Ihrem Geschäftskontext widerzuspiegeln, wie z. B. Rebranding.

* Sie können jetzt die [!DNL Experience Manager Assets] Benutzeroberfläche für:

   * Konfigurieren Sie die Erkennung doppelter Assets in einem Repository.

   * Konfigurieren Sie das Hinzufügen digitaler Wasserzeichen zu Bildern.

* Administratoren können jetzt den E-Mail-Dienst für große Downloads konfigurieren. Dadurch können Benutzer [E-Mail-Benachrichtigungen für große Downloads aktivieren](/help/assets/download-assets-from-aem.md#enable-email-notifications-for-large-downloads) von [!DNL Experience Manager Assets] -Schnittstelle. Nach Abschluss des Download-Prozesses erhält der Benutzer eine E-Mail-Benachrichtigung mit dem Download-Link des archivierten ZIP-Ordners.


* Die [Veröffentlichung verwalten](/help/assets/manage-publication.md) wurde um eine verbesserte Benutzeroberfläche erweitert. Die Benutzer können Inhalte in dem ausgewählten Ziel veröffentlichen oder dessen Veröffentlichung rückgängig machen. [Inhalt hinzufügen](/help/assets/manage-publication.md#add-content) zur Veröffentlichungsliste aus dem gesamten DAM-Repository [Ordnereinstellungen einschließen](/help/assets/manage-publication.md#include-folder-settings) zum Veröffentlichen des Inhalts der ausgewählten Ordner und zum Anwenden von Filtern und [Veröffentlichung planen](/help/assets/manage-publication.md#publish-assets-later) zu einem späteren Zeitpunkt.

### Fehlerbehebungen {#bug-fixes}

* Nicht verarbeitete Assets ohne ursprüngliche Ausgabedarstellung werden zur Verarbeitung an Asset compute gesendet, während Assets von AEM On-Premise zu Cloud-Services migriert werden.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [Kommunikations-APIs](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html) helfen Ihnen, eine Vorlage und XML-Daten zu kombinieren, um Print-Dokumente in verschiedenen Formaten zu erzeugen. Mit dem Service können Sie Dokumente im synchronen Modus und im Batch-Modus generieren. Dabei können Sie mit den APIs Anwendungen mit folgenden Funktionen erstellen:

   * Erzeugen von Dokumenten durch Füllen von Vorlagendateien mit XML-Daten
   * Generieren von Formularen in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Printstreams.
   * Generieren von druckbaren PDFs aus XFA-Formular-PDFs.
   * Generieren von PDF-, PostScript-, PCL- und ZPL-Dokumenten in großen Mengen durch Zusammenführen mehrerer Datensätze mit den Quellvorlagen.

* **Benutzerdefinierte Schriftarten für Datensatzdokument- und PDF-Dokumente, die mit Kommunikations-APIs erstellt wurden**: Sie können jetzt markengenehmigte Schriftarten in PDF-Dokumenten verwenden, die mithilfe von Kommunikations-APIs generiert wurden, um Ihre organisatorischen Anforderungen zu erfüllen.

### Neue Funktionen in [!DNL Forms] im Kanal für die Vorabversion {#prerelease-features-forms}

* **[Assembler-API](https://www.adobe.io/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/)**: Assembler-APIs zum Kombinieren, Neuanordnen, Erweitern und Abrufen von Informationen zu PDF-Dokumenten.


## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Verbesserte myAccount-Komponenten
* Die Komponente &quot;Produktempfehlung&quot;unterstützt zusätzliche Seitentypen (Homepage, Warenkorb, Bestellbestätigung).
* **Wunschliste**
   * Angemeldete Besucher können Produkte zu einer Wunschliste hinzufügen
   * Die Verwaltung der Wunschliste und ihrer Produkte ist über myAccount möglich.
   * Die Schaltfläche &quot;Zur Wunschliste hinzufügen&quot;kann auf Komponentenebene über eine Richtlinie (z. B. Produkt-Teaser, Produktdetails) aktiviert/deaktiviert werden
   * Verfügbar als Kernkomponente und in der Venia-Storefront AEM

![Wunschliste](/help/assets/CIF/wishlist.png)

## Cloud Manager {#cloud-manager}

Auf dieser Seite werden die Versionshinweise für Cloud Manager in AEM as a Cloud Service Version 2022.01.0 beschrieben.

>[!NOTE]
>
>Siehe [diese Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) für die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

### Veröffentlichungsdatum {#release-date-cm}

Die Version von Cloud Manager in AEM as a Cloud Service Version 2022.01.0 wurde am 20. Januar 2022 veröffentlicht. Die nächste Version soll am 10. Februar 2022 veröffentlicht werden.

### Neue Funktionen {#what-is-new-cm}

* Cloud Manager wird [Vermeiden Sie die Neuerstellung der Code-Basis, wenn festgestellt wird, dass dieselbe Git-Bestätigung verwendet wird.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) in mehreren vollständigen Pipelineausführungen.
* Für den Zugriff auf das AEM-Umgebungsprotokoll ist jetzt die **Bereitstellungsmanager** Produktprofil. Benutzern ohne dieses Profil wird in der Benutzeroberfläche eine deaktivierte Schaltfläche angezeigt.
* Die Benutzeroberfläche lässt keine Konfiguration der Frontend-Pipeline für ein Programm zu, bei dem Sites nicht als Lösung aktiviert ist.
* Beim Generieren eines Git-Kennworts wird das Ablaufdatum angezeigt.

### Fehlerbehebungen {#bug-fixes-cm}

* Null-Zeiger-Ausnahmen, die bei einigen Frontend-Pipeline-Bereitstellungen aufgetreten sind, wurden korrigiert.
* Umgebungsvariablen können jetzt hinzugefügt, aktualisiert und gelöscht werden, wenn eine Umgebung eine veraltete Version von AEM ausführt.
* Der Schritt zum Erstellen eines Bildes wird nicht mehr als FEHLER für Pipelines markiert, die den geplanten Schritt in bestimmten seltenen Fällen verwendet haben.
* Bei Programmen mit nur einem Repository zeigt der Bildschirm zur Pipeline-Ausführung jetzt den Namen des Repositorys an.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer 2.1.24 wurde am 01. Februar 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* Möglichkeit, die Anzahl der Assets mit und ohne Smart-Tags zu erkennen und darüber zu berichten.
* Möglichkeit, die Version der verwendeten Kernkomponente zu erkennen und darüber zu berichten.
* Möglichkeit, den Typ der Quellebene (Autor oder Veröffentlichung) zu erkennen und darüber zu berichten, in der BPA ausgeführt wurde.

### Fehlerbehebungen {#bug-fixes-bpa}

* Die BPA-Skalierungslogik wurde schneller und effizienter gestaltet.
* In einigen Szenarien inkrementierte BPA die analysierte Anzahl nicht, als sie ausgeführt wurde. Dieses Problem wurde behoben.
