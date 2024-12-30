---
title: Versionshinweise für Version 2022.1.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Versionshinweise für Version 2022.1.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 1c40ab67-8fd7-4f29-b8c9-dd98b6d5b490
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1065'
ht-degree: 93%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2022.1.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den Funktionen der Version 2022.1.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2022.1.0) war der 3. Februar 2022.
Die folgende Version (2022.3.0) wurde am 31. März 2022 veröffentlicht.

## Video zur Version {#release-video}

Sehen Sie sich das Video [Versionsübersicht Januar 2022](https://video.tv.adobe.com/v/340120) an, das eine Zusammenfassung der Funktionen bietet, die der Version 2022.1.0 hinzugefügt wurden.

## Adobe Experience Manager Sites as a Cloud Service {#sites}

* Die Schaltfläche **[Frontend-Pipeline aktivieren](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md)** in der Leiste **Site** der Sites-Konsole ist für Sites verfügbar, die die v2 der Seitenkernkomponente verwenden. Mit dieser Schaltfläche wird die Site so konfiguriert, dass die Designs, die mit der Frontend-Pipeline bereitgestellt werden, über die vorhandenen Client-Bibliotheken geladen werden.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* [!DNL Dynamic Media]: Sie können jetzt die AEM Dynamic Media-Benutzeroberfläche verwenden, um allgemeine Einstellungen und Veröffentlichungseinstellungen zu konfigurieren, anstatt das Dynamic Media Classic-Desktop-Programm verwenden zu müssen.

* [!DNL Dynamic Media] unterstützt jetzt Aufnahme, Vorschau, Wiedergabe und Veröffentlichung von MXF-Videos. Anmerkungen und Shop-fähige Videos für MXF-Videos werden noch nicht unterstützt.

* Nach dem Konfigurieren einer Verbindung zwischen Remote-DAM- und Sites-Bereitstellungen werden die Assets auf Remote-DAM in der Sites-Bereitstellung verfügbar gemacht. Sie können jetzt Remote-DAM-Assets oder -Ordner [aktualisieren, löschen, umbenennen und verschieben](/help/assets/use-assets-across-connected-assets-instances.md). Die Aktualisierungen stehen mit etwas Verzögerung automatisch in der Sites-Bereitstellung zur Verfügung.

### Neue Funktionen im Vorabversionskanal von [!DNL Assets] {#assets-prerelease-features}

* [!DNL AEM Dynamic Media] bietet jetzt die Flexibilität, in der Benutzeroberfläche [ein Alias-Konto zu konfigurieren](/help/assets/dynamic-media/dm-alias-account.md), um sicherzustellen, dass vorkonfigurierte Dynamic Media-URLs und der Viewer-Einbettungs-Code aktualisiert werden. Dies wirkt sich positiv auf die SEO aus, die nun Aktualisierungen an Ihrem Geschäftskontext, wie z. B. Rebranding, widerspiegelt.

* Sie können die Benutzeroberfläche von [!DNL Experience Manager Assets] für folgende Vorgänge verwenden:

   * Konfigurieren der Erkennung doppelter Assets in einem Repository.

   * Konfigurieren des Hinzufügens digitaler Wasserzeichen zu Bildern.

* Administratoren können jetzt den E-Mail-Service für große Downloads konfigurieren. Dadurch können Benutzer von der [!DNL Experience Manager Assets]-Benutzeroberfläche aus [E-Mail-Benachrichtigungen für große Downloads aktivieren](/help/assets/download-assets-from-aem.md#enable-email-notifications-for-large-downloads). Nach Abschluss des Download-Prozesses erhält der Benutzer eine E-Mail-Benachrichtigung mit dem Download-Link des archivierten ZIP-Ordners.


* Die Funktion [Veröffentlichung verwalten](/help/assets/manage-publication.md) wurde um eine verbesserte Benutzeroberfläche erweitert. Die Benutzer können Inhalte in dem ausgewählten Ziel veröffentlichen oder dessen Veröffentlichung rückgängig machen. [Inhalt hinzufügen](/help/assets/manage-publication.md#add-content) zur Veröffentlichungsliste aus dem gesamten DAM-Repository [Ordnereinstellungen einschließen](/help/assets/manage-publication.md#include-folder-settings) zum Veröffentlichen des Inhalts der ausgewählten Ordner und zum Anwenden von Filtern und [Veröffentlichung planen](/help/assets/manage-publication.md#publish-assets-later) zu einem späteren Zeitpunkt.

### Fehlerbehebungen {#bug-fixes}

* Nicht verarbeitete Assets ohne ursprüngliche Ausgabedarstellung werden zur Verarbeitung an Asset Compute gesendet, während Assets von AEM On-Premise zu Cloud-Services migriert werden.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [Kommunikations-APIs](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html?lang=de) helfen Ihnen, eine Vorlage und XML-Daten zu kombinieren, um Print-Dokumente in verschiedenen Formaten zu erzeugen. Mit dem Service können Sie Dokumente im synchronen Modus und im Batch-Modus generieren. Dabei können Sie mit den APIs Anwendungen mit folgenden Funktionen erstellen:

   * Erzeugen von Dokumenten durch Füllen von Vorlagendateien mit XML-Daten
   * Generieren von Formularen in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Printstreams.
   * Generieren von druckbaren PDFs aus XFA-Formular-PDFs.
   * Generieren von PDF-, PostScript-, PCL- und ZPL-Dokumenten in großen Mengen durch Zusammenführen mehrerer Datensätze mit den Quellvorlagen.

* **Benutzerdefinierte Schriftarten für Datensatzdokument- und PDF-Dokumente, die mit Kommunikations-APIs erstellt wurden**: Sie können jetzt markengeprüfte Schriftarten in PDF-Dokumenten verwenden, die mithilfe von Kommunikations-APIs generiert wurden, um sie an die Anforderungen Ihres Unternehmens anzupassen.

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Forms] verfügbar {#prerelease-features-forms}

* **[Assembler-API](https://www.adobe.io/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/)**: Assembler-APIs zum Kombinieren, Neuanordnen, Erweitern und Abrufen von Informationen zu PDF-Dokumenten.


## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Verbesserte myAccount-Komponenten
* Die Komponente „Produktempfehlung“ unterstützt zusätzliche Seitentypen (Homepage, Warenkorb, Bestellbestätigung).
* **Wunschliste**
   * Angemeldete Besucher können Produkte zu einer Wunschliste hinzufügen
   * Die Verwaltung der Wunschliste und ihrer Produkte ist über myAccount möglich
   * Die Schaltfläche „Zur Wunschliste hinzufügen“ kann auf Komponentenebene über eine Richtlinie (z. B. Produkt-Teaser, Produktdetails) aktiviert/deaktiviert werden
   * Verfügbar als Kernkomponente und in der Venia-Storefront von AEM

<!-- Image was not found during PR validation despite correct path ![Wishlist](/help/assets/CIF/wantlist.png) -->

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Die Version 2022.01.0 von Cloud Manager in AEM as a Cloud Service wurde am 20. Januar 2022 veröffentlicht. Die nächste Version soll am 10. Februar 2022 veröffentlicht werden.

### Neue Funktionen {#what-is-new-cm}

* Cloud Manager [vermeidet die Neuerstellung der Code-Basis, wenn festgestellt wird, dass derselbe Git-Commit in mehreren Full-Stack-Pipeline-Ausführungen verwendet wird](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse).
* Für den Zugriff auf das AEM-Umgebungsprotokoll ist jetzt das Produktprofil **Bereitstellungs-Manager** erforderlich. Benutzenden ohne dieses Profil wird in der Benutzeroberfläche eine deaktivierte Schaltfläche angezeigt.
* Die Benutzeroberfläche lässt keine Konfiguration der Frontend-Pipeline für ein Programm zu, bei dem Sites nicht als Lösung aktiviert ist.
* Beim Generieren eines Git-Kennworts wird das Ablaufdatum angezeigt.

### Fehlerbehebungen {#bug-fixes-cm}

* Null-Pointer-Ausnahmen, die bei einigen Frontend-Pipeline-Bereitstellungen aufgetreten sind, wurden korrigiert.
* Umgebungsvariablen können jetzt hinzugefügt, aktualisiert und gelöscht werden, wenn eine Umgebung eine veraltete Version von AEM ausführt.
* Der Schritt zum Erstellen eines Bildes wird in bestimmten seltenen Fällen für Pipelines, die den geplanten Schritt verwendet haben, nicht mehr als FEHLER markiert.
* Bei Programmen mit nur einem Repository zeigt der Bildschirm zur Pipeline-Ausführung jetzt den Repository-Namen an.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool 1.8.6 wurde am 03. Februar 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Inhaltsvalidierung: Benutzende können zuverlässig feststellen, ob der gesamte vom Content Transfer Tool extrahierte Inhalt erfolgreich in die Zielinstanz aufgenommen wurde. Um diese Funktion verwenden zu können, aktivieren Sie sie in der `System Console` der AEM-Quellumgebung. Weitere Informationen finden Sie unter [Validieren von Inhaltsübertragungen – Erste Schritte](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers.html?lang=de#getting-started).

### Fehlerbehebungen {#bug-fixes-ctt}

* Einige Benutzer wurden nicht zugeordnet, da bei der Benutzerzuordnung zwischen Groß- und Kleinschreibung unterschieden wurde. Dieses Problem wurde behoben. Bei der Benutzerzuordnung wird nicht mehr zwischen Groß- und Kleinschreibung unterschieden.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer 2.1.24 wurde am 01. Februar 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* Die Möglichkeit, die Anzahl der Assets mit und ohne Smart-Tags zu erkennen und darüber zu berichten.
* Die Möglichkeit, die verwendete Version von Kernkomponenten zu erkennen und darüber zu berichten.
* Die Möglichkeit, den Typ der Quellebene (Autor oder Veröffentlichung), in der der BPA ausgeführt wurde, zu erkennen und darüber zu berichten.

### Fehlerbehebungen {#bug-fixes-bpa}

* Die BPA-Skalierungslogik wurde schneller und effizienter gestaltet.
* In einigen Szenarien inkrementierte der BPA die analysierte Anzahl nicht, als er ausgeführt wurde. Dieses Problem wurde behoben.
