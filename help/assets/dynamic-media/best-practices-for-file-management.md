---
title: Best Practices zum Organisieren digitaler Assets für die Verwendung von Dynamic Media-Bildprofilen oder -Videoprofilen
description: '"Tipps und Best Practices für die Benennung, Organisation und Verwaltung von Dynamic Media-Bilddateien und -Video-Asset-Dateien."'
contentOwner: Rick Brough
feature: Asset-Management, Bildprofile, Videoprofile
role: Administrator,Business Practitioner
exl-id: 82ab5432-088c-4442-a9db-9f4e0184febf
source-git-commit: 1fe6ce1259972c1805d934327aa2f24cdcdc0bc8
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 44%

---

# Best Practices zum Organisieren digitaler Assets für die Verwendung von Bild- oder Videoprofilen{#best-practices-for-organizing-your-digital-assets-for-using-profiles}

Wichtig für die Verwendung von Dynamic Media-Bildprofilen oder -Videoprofilen ist, dass sie Ordnern zugewiesen werden. In einem Profil befinden sich Einstellungen für ein Bild oder Video. Diese Einstellungen verarbeiten den Inhalt eines Ordners zusammen mit seinen Unterordnern. Wie Sie Dateien und Ordner benennen, Unterordner anordnen und die Dateien in diesen Ordnern verarbeiten, wirkt sich daher darauf aus, wie diese Assets vom Profil verarbeitet werden.

Durch die Verwendung konsistenter und angemessener Strategien zur Datei- und Ordnernamen sowie einer guten Metadatenpraxis können Sie die digitale Asset-Sammlung optimal nutzen und sicherstellen, dass die richtigen Dateien vom richtigen Profil verarbeitet werden.

Siehe [Informationen zu Dynamic Media-Bildprofilen und -Videoprofilen](about-image-video-profiles.md).

Beachten Sie die folgenden Best Practices für die Organisation Ihrer digitalen Asset-Dateien.

* Organisieren Sie Ihre Dateien auf Grundlage der von Ihnen hinzugefügten Metadaten und nicht basierend auf den Ordnern, in denen sie enthalten sind. Sie können diese Vorgehensweise durch Hinzufügen von Metadatenprofilen umsetzen.

   * Siehe [Metadatenprofile](/help/assets/metadata-profiles.md).
   * Informationen hierzu finden Sie unter [Metadaten für die Verwaltung digitaler Assets](/help/assets/manage-metadata.md).

* Normalerweise wächst Ihre Sammlung digitaler Assets immer weiter. Daher ist es wichtig, dass die Metadatennutzung, die Ordnerstruktur und die Dateibenennung für alle hochgeladenen Assets bereits frühzeitig formalisiert werden. Indem Sie diese Aspekte standardisieren, wird sichergestellt, dass Sie auch bei einem stets wachsenden Pool mit digitalen Assets Verarbeitungsprofile präziser und konsistenter auf Ordner anwenden können.
* Verwenden Sie Ordner, um eine konsistente Speicherstruktur für die digitalen Assets durchzusetzen. Ordnerstrukturen, mit denen Sie verfeinern können, welche Profile zugewiesen werden sollen, können beispielsweise Folgendes umfassen:

   * **Entwicklungsordner**  - enthalten digitale Assets, an denen Sie derzeit arbeiten.
   * **** Kundenordner: Enthalten digitale Assets basierend auf Kunden oder Projektnamen.
   * **Primäre Quellordner**  - enthalten digitale Quell-Assets in Originalform.
   * **** Ausgabeformatordner: Enthalten Ausgabeformate und Kopien der digitalen Quell-Assets in Originalform.
   * **** Dateigrößenordner: Enthalten digitale Assets basierend auf kleinen, mittleren oder großen Dateien.
   * **Staging-Ordner**  - enthalten digitale Assets, die live auf Ihrer Website veröffentlicht werden können.
   * **MIME-Typ-Ordner**  - enthalten digitale Assets, die für MIME-Typen spezifisch sind, z. B. Bilder, Dokumente und Multimedia.
   * **Archivordner**  - enthalten veraltete digitale Assets.
   * **Datumsbasierte Ordner**  - enthalten digitale Assets basierend auf einem Erstellungsdatum oder einem Datum der letzten Änderung.

* Erstellen Sie ein Ordnerverzeichnis, das voraussichtlich nicht geändert werden muss, damit zugewiesene Profile nicht ungültig werden.
* Angenommen, ein Asset ist bereits veröffentlicht, verwenden Sie Adobe Experience Manager, um das Asset in einen anderen Ordner zu verschieben und von seinem neuen Speicherort aus erneut zu veröffentlichen. Der ursprünglich veröffentlichte Asset-Speicherort ist weiterhin verfügbar, zusammen mit dem neu veröffentlichten Asset. Das ursprünglich veröffentlichte Asset geht jedoch an Experience Manager verloren und kann nicht rückgängig gemacht werden. Daher empfiehlt es sich, die Veröffentlichung von Assets zuerst rückgängig zu machen, bevor Sie sie in einen anderen Ordner verschieben.
