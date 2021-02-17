---
title: Best Practices zum Organisieren digitaler Assets für die Verwendung von Dynamic Media-Bildprofilen oder -Videoprofilen
description: Tipps und Best Practices für das Benennen, Organisieren und Verwalten von Dynamic Media-Bild- und -Videodateien.
contentOwner: Rick Brough
translation-type: tm+mt
source-git-commit: a64a7274f0037789be1a5e2f7427aba551f14ed7
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 67%

---


# Best Practices zum Organisieren digitaler Assets für die Verwendung von Bild- oder Videoprofilen{#best-practices-for-organizing-your-digital-assets-for-using-profiles}

Wichtig für die Verwendung von Dynamic Media-Bildprofilen oder -Videoprofilen ist, dass sie Ordnern zugewiesen werden. In einem Profil befinden sich Einstellungen für ein Bild oder Video. Diese Einstellungen verarbeiten den Inhalt eines Ordners zusammen mit einem seiner Unterordner. Die Benennung von Dateien und Ordnern, die Anordnung von Unterordnern und die Handhabung der Dateien in diesen Ordnern wirken sich daher darauf aus, wie diese Assets vom Profil verarbeitet werden.

Indem Sie konsistente und geeignete Datei- und Ordnernamensstrategien zusammen mit angemessenen Metadatenpraktiken einsetzen, können Sie die Sammlung Ihrer digitalen Assets optimal nutzen und sicherstellen, dass die richtigen Dateien vom richtigen Profil verarbeitet werden.

Siehe [Informationen zu Dynamic Media-Bildprofilen und -Videoprofilen](about-image-video-profiles.md).

Beachten Sie die folgenden Best Practices für die Organisation Ihrer digitalen Asset-Dateien.

* Organisieren Sie Ihre Dateien auf Grundlage der von Ihnen hinzugefügten Metadaten und nicht basierend auf den Ordnern, in denen sie enthalten sind. Sie können dies durch Hinzufügen von Metadaten-Profilen erreichen.

   * Siehe [Metadatenprofile](/help/assets/metadata-profiles.md).
   * Informationen hierzu finden Sie unter [Metadaten für die Verwaltung digitaler Assets](/help/assets/manage-metadata.md).

* Normalerweise wächst Ihre Sammlung digitaler Assets immer. Daher ist es wichtig, dass die Metadatennutzung, die Ordnerstruktur und die Dateibenennung für alle hochgeladenen Assets bereits frühzeitig formalisiert werden. Indem Sie diese Aspekte standardisieren, wird sichergestellt, dass Sie auch bei einem stets wachsenden Pool mit digitalen Assets Verarbeitungsprofile präziser und konsistenter auf Ordner anwenden können.
* Verwenden Sie Ordner, um eine konsistente Speicherstruktur für die digitalen Assets durchzusetzen. Zu den Ordnerstrukturen, die Ihnen dabei helfen können, die zuzuweisenden Profil zu verfeinern, gehören beispielsweise die folgenden:

   * **Entwicklungsordner** – enthalten digitale Assets, an denen Sie derzeit arbeiten.
   * **Kundenordner** – enthalten digitale Assets basierend auf Kunden oder Projektnamen.
   * **Primäre Ordner:** enthalten digitale Quell-Assets in ihrer Originalform.
   * **Ausgabeformatordner** – enthalten Ausgabeformate und Kopien der digitalen Quell-Assets in Originalform.
   * **Dateigrößenordner** – enthalten digitale Assets basierend auf kleinen, mittleren oder großen Dateien.
   * **Bereitstellungsordner** – enthalten digitale Assets, die für die Veröffentlichung auf Ihrer Website bereit sind.
   * **Mime-Type-Ordner**  - enthält digitale Assets, die für MIME-Typen wie Bilder, Dokumente und Multimedia spezifisch sind.
   * **Archivordner** – enthalten veraltete digitale Assets.
   * **Datumsbasierte Ordner** – enthalten digitale Assets basierend auf einem Erstellungsdatum oder dem letzten Änderungsdatum.

* Erstellen Sie ein Ordnerverzeichnis, das voraussichtlich nicht geändert werden muss, damit zugewiesene Profile nicht ungültig werden.
* Angenommen, ein Asset wurde bereits veröffentlicht. Anschließend verschieben Sie das Asset mit Adobe Experience Manager in einen anderen Ordner und veröffentlichen es erneut. Der ursprüngliche Speicherort des veröffentlichten Assets sowie das neu veröffentlichte Asset sind weiterhin verfügbar. Das ursprünglich veröffentlichte Asset geht jedoch an den Experience Manager verloren und kann nicht rückgängig gemacht werden. Daher sollten Sie die Veröffentlichung von Assets zuerst rückgängig machen, bevor Sie sie in einen anderen Ordner verschieben.

