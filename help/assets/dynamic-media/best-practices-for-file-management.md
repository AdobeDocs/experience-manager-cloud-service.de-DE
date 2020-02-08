---
title: Best Practices für die Organisation Ihrer digitalen Assets zur Verwendung von Profilen
description: Tipps und Best Practices für das Benennen, Organisieren und Verwalten von Metadaten für digitale Asset-Dateien.
translation-type: tm+mt
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6

---


# Bewährte Verfahren zum Organisieren digitaler Assets für die Verwendung von Profilen {#best-practices-for-organizing-your-digital-assets-for-using-profiles}

Ein wichtiges Konzept zur Verwendung von Profilen in AEM Assets ist deren Zuweisung zu Ordnern. In einem Profil sind Einstellungen in Form von Metadatenprofilen zusammen mit Videoprofilen oder Bildprofilen enthalten. Mit diesen Einstellungen wird der Inhalt eines Ordners und seiner zugehörigen Unterordner verarbeitet. Wie Sie Ihre Dateien und Ordner benennen, wie Sie Unterordner anordnen und wie Sie die Dateien in diesen Ordnern verarbeiten, hat daher eine erhebliche Auswirkung darauf, wie diese Assets durch ein Profil verarbeitet werden.

Indem Sie konsistente und geeignete Datei- und Ordnernamensstrategien zusammen mit angemessenen Metadatenpraktiken einsetzen, können Sie die Sammlung Ihrer digitalen Assets optimal nutzen und sicherstellen, dass die richtigen Dateien vom richtigen Profil verarbeitet werden.

Weitere Informationen finden Sie unter [Profile für die Verarbeitung von Videos, Metadaten und Bildern](processing-profiles.md).

Im Folgenden finden Sie Tipps zu Best Practices zum Organisieren Ihrer digitalen Asset-Dateien.

* Organisieren Sie Ihre Dateien auf Grundlage der von Ihnen hinzugefügten Metadaten und nicht basierend auf den Ordnern, in denen sie enthalten sind. Sie können dies erreichen, indem Sie Metadatenprofile hinzufügen.

   * Siehe hierzu [Metadatenprofile.](/help/assets/metadata-profiles.md)
   * Informationen hierzu finden Sie unter [Metadaten für die Verwaltung digitaler Assets](/help/assets/manage-metadata.md).

* In den meisten Fällen wächst die Sammlung mit digitalen Assets stets weiter an. Daher ist es wichtig, dass Sie die Verwendung von Metadaten, die Ordnerstruktur und die Dateibenennung für alle hochgeladenen Assets vorher formalisieren. Indem Sie diese Aspekte standardisieren, wird sichergestellt, dass Sie auch bei einem stets wachsenden Pool mit digitalen Assets Verarbeitungsprofile präziser und konsistenter auf Ordner anwenden können.
* Verwenden Sie Ordner nur, um eine einheitliche Speicherstruktur für Ihre digitalen Assets zu gewährleisten. Zu den Ordnerstrukturen, die Ihnen dabei helfen können, die zuzuweisenden Profile zu verfeinern, zählen beispielsweise die folgenden:

   * **Entwicklungsordner** - enthält digitale Assets, an denen Sie derzeit arbeiten.
   * **Clientordner** - enthält digitale Assets, die auf Clients oder Projektnamen basieren.
   * **Hauptordner** - enthält digitale Originalelemente.
   * **Ausgabeordner** - enthält Darstellungen und Kopien der digitalen Originalelemente.
   * **Dateigrößenordner** : Enthält digitale Assets, die auf kleinen, mittleren oder großen Dateigrößen basieren.
   * **Staging-Ordner** - enthält digitale Assets, die live auf Ihrer Website veröffentlicht werden können.
   * **Mime-Type-Ordner** : enthält digitale Assets, die für Mime-Typen wie Bilder, Dokumente und Multimedia spezifisch sind.
   * **Archivordner** - enthält zurückgestellte digitale Assets.
   * **Datumsbasierte Ordner** - enthält digitale Assets basierend auf einem Erstellungsdatum oder einem Datum der letzten Änderung.

* Erstellen Sie ein Ordnerverzeichnis, das voraussichtlich nicht geändert werden muss, damit zugewiesene Profile nicht ungültig werden.
* Wenn ein Asset bereits veröffentlicht wurde, dann verwenden Sie AEM, um das Asset in einen anderen Ordner zu verschieben und erneut zu veröffentlichen, dann ist der ursprüngliche Speicherort des veröffentlichten Assets zusammen mit dem neu veröffentlichten Asset weiterhin verfügbar. Das ursprünglich veröffentlichte Asset geht jedoch an AEM verloren und kann nicht rückgängig gemacht werden. Daher sollten Sie die Veröffentlichung von Assets zuerst rückgängig machen, bevor Sie sie in einen anderen Ordner verschieben.

