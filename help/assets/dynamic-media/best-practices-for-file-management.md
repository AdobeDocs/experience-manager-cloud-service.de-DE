---
title: Best Practices zum Organisieren digitaler Assets für die Verwendung von Dynamic Media-Bildprofilen oder -Videoprofilen
description: Tipps und Best Practices für das Benennen, Organisieren und Verwalten von Dynamic Media-Bild- und -Videodateien.
contentOwner: Rick Brough
translation-type: tm+mt
source-git-commit: 58aa2f416aac6fa6b260e846fc5265bdf62a1949
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 100%

---


# Best Practices zum Organisieren digitaler Assets für die Verwendung von Bild- oder Videoprofilen{#best-practices-for-organizing-your-digital-assets-for-using-profiles}

Wichtig für die Verwendung von Dynamic Media-Bildprofilen oder -Videoprofilen ist, dass sie Ordnern zugewiesen werden. In einem Profil befinden sich Einstellungen für ein Bild oder Video. Mit diesen Einstellungen wird der Inhalt eines Ordners und seiner zugehörigen Unterordner verarbeitet. Wie Sie Ihre Dateien und Ordner benennen, wie Sie Unterordner anordnen und wie Sie die Dateien in diesen Ordnern behandeln, hat daher eine erhebliche Auswirkung darauf, wie diese Assets durch ein Profil verarbeitet werden.

Indem Sie konsistente und geeignete Datei- und Ordnernamensstrategien zusammen mit angemessenen Metadatenpraktiken einsetzen, können Sie die Sammlung Ihrer digitalen Assets optimal nutzen und sicherstellen, dass die richtigen Dateien vom richtigen Profil verarbeitet werden.

Siehe [Informationen zu Dynamic Media-Bildprofilen und -Videoprofilen](about-image-video-profiles.md).

Beachten Sie die folgenden Best Practices für die Organisation Ihrer digitalen Asset-Dateien.

* Organisieren Sie Ihre Dateien auf Grundlage der von Ihnen hinzugefügten Metadaten und nicht basierend auf den Ordnern, in denen sie enthalten sind. Sie können dies erreichen, indem Sie Metadatenprofile hinzufügen.

   * Siehe [Metadatenprofile](/help/assets/metadata-profiles.md).
   * Informationen hierzu finden Sie unter [Metadaten für die Verwaltung digitaler Assets](/help/assets/manage-metadata.md).

* In den meisten Fällen wächst die Sammlung mit digitalen Assets stets weiter an. Daher ist es wichtig, dass die Metadatennutzung, die Ordnerstruktur und die Dateibenennung für alle hochgeladenen Assets bereits frühzeitig formalisiert werden. Indem Sie diese Aspekte standardisieren, wird sichergestellt, dass Sie auch bei einem stets wachsenden Pool mit digitalen Assets Verarbeitungsprofile präziser und konsistenter auf Ordner anwenden können.
* Verwenden Sie Ordner, um eine konsistente Speicherstruktur für die digitalen Assets durchzusetzen. Ordnerstrukturen, mit deren Hilfe Sie verfeinern können, welche Profile zugewiesen werden sollen, können beispielsweise Folgendes umfassen:

   * **Entwicklungsordner** – enthalten digitale Assets, an denen Sie derzeit arbeiten.
   * **Kundenordner** – enthalten digitale Assets basierend auf Kunden oder Projektnamen.
   * **Primäre Ordner:** enthalten digitale Quell-Assets in ihrer Originalform.
   * **Ausgabeformatordner** – enthalten Ausgabeformate und Kopien der digitalen Quell-Assets in Originalform.
   * **Dateigrößenordner** – enthalten digitale Assets basierend auf kleinen, mittleren oder großen Dateien.
   * **Bereitstellungsordner** – enthalten digitale Assets, die für die Veröffentlichung auf Ihrer Website bereit sind.
   * **MIME-Typ-Ordner** – enthalten digitale Assets entsprechend den MIME-Typen, z. B. Bilder, Dokumente und Multimedia.
   * **Archivordner** – enthalten veraltete digitale Assets.
   * **Datumsbasierte Ordner** – enthalten digitale Assets basierend auf einem Erstellungsdatum oder dem letzten Änderungsdatum.

* Erstellen Sie ein Ordnerverzeichnis, das voraussichtlich nicht geändert werden muss, damit zugewiesene Profile nicht ungültig werden.
* Wenn Sie ein bereits veröffentlichtes Asset in AEM in einen anderen Ordner verschieben und anschließend aus dem neuen Speicherort erneut veröffentlichen, ist der ursprünglich veröffentlichte Asset-Speicherort weiterhin zusammen mit dem neu veröffentlichten Asset verfügbar. Das ursprünglich veröffentlichte Asset ist allerdings für AEM nicht mehr zugänglich. Daher kann dessen Veröffentlichung nicht rückgängig gemacht werden. Deshalb wird empfohlen, dass Sie die Veröffentlichung von Assets zunächst rückgängig machen, bevor Sie sie in einen anderen Ordner verschieben.

