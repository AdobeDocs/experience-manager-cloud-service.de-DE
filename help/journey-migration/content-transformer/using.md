---
title: Verwenden von Content Transformer
description: Erfahren Sie, wie Sie Ihre Inhaltsstruktur bei der Vorbereitung der Migration auf AEM as a Cloud Service umwandeln.
source-git-commit: 8c73805b6ed1b7a03c65b4d21a4252c1412a5742
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 2%

---

# Verwenden von Content Transformer {#using-ct}

## Wichtige Überlegungen zur Verwendung von Content Transformer {#imp-considerations-ct}

Im folgenden Abschnitt finden Sie wichtige Überlegungen zur Verwendung von Content Transformer (CT):

* Um den Content Transformer zu verwenden, müssen Sie zunächst den Best Practices Analyzer in Ihrer Adobe Experience Manager (AEM)-Umgebung ausführen.
* Obwohl Sie den Content Transformer in Ihrer Produktionsumgebung ausführen können, wird empfohlen, den Content Transformer in einem Klon Ihrer Produktionsumgebung auszuführen. Vor allem müssen Sie sicherstellen, dass die BPA und die CT in derselben Umgebung ausgeführt werden.
* Sie müssen ein Administrator in der Umgebung sein, in der Sie den Content Transformer ausführen möchten.
* Jeder Vorgang, der den Quellinhalt ändern kann ( Verschieben/Entfernen/Umbenennen ), erstellt standardmäßig ein Backup-Paket der Quellpfade unter `/etc/packages/content-transformation` vor der Umwandlung. Obwohl jedes Vorgangsdialogfeld über eine Option zum Deaktivieren/Aktivieren der Erstellung von Backup-Paketen verfügt, wird dringend empfohlen, die Erstellung von Paketen immer zu aktivieren.
* Jede Seite im Content Transformer ist so konfiguriert, dass sie maximal 50 Ergebnisse auflistet, sodass gleichzeitig maximal 50 Ergebnisse umgewandelt werden können. Dies geschieht, um eine pünktliche Antwort auf der Benutzeroberfläche bereitzustellen.

## Verfügbarkeit {#availability-ct}

Der Content Transformer wird mit dem [Content Transfer Tool](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md) die als ZIP-Datei vom Software Distribution-Portal heruntergeladen werden können. Sie können das Paket über Package Manager auf Ihrer AEM-Quellinstanz installieren.

>[!NOTE]
>Der Content Transformer ist mit dem Content Transfer Tool v2.0.20 oder höher verfügbar.

## Öffnen von Content Transformer {#opening-ct}

1. Melden Sie sich bei der Quell-AEM-Instanz als Administrator an und rufen Sie die Startseite auf: https://host:port/aem/start.html.
1. Navigieren Sie zu Tools > Vorgänge > Inhaltsmigration

   ![Bild](/help/journey-migration/content-transformer/assets/ct-1.png)

   >[!NOTE]
   > Stellen Sie sicher, dass Sie den BPA-Bericht bereits ausgeführt haben, und überprüfen Sie ihn mit der URL http://host:port/apps/best-practices-analyzer/content/BestPracticesReport.html .

1. Klicken Sie auf die Karte mit Titel **Bericht &quot;Content Transformer für BPA&quot;**

   ![Bild](/help/journey-migration/content-transformer/assets/ct-2.png)

   Im Folgenden finden Sie ein Beispiel dafür, wie die Übersichtsseite zu Content Transformer aussehen wird, wenn die Erstellung des BPA-Berichts erfolgreich war und inhaltliche Probleme auftraten.

   Die für den BPA-Bericht verbleibende Ablaufzeit wird in der Seitenleiste angezeigt. Es wird empfohlen, den Content Transformer mit dem neuesten BPA-Bericht auszuführen, um zu vermeiden, dass inhaltsbezogene Ergebnisse fehlen.

   ![Bild](/help/journey-migration/content-transformer/assets/ct-3.png)

1. Sie können die Probleme nach `Pattern Code`, `Subtype`, `Importance`, und `Source`.

   ![Bild](/help/journey-migration/content-transformer/assets/ct-4.png)

1. Sie können alle oder bestimmte Probleme auswählen und Aktionen wie Verschieben, Entfernen und Umbenennen durchführen, um sie zu beheben. Benutzerdefinierte Pfade können auch mit **Pfade hinzufügen** -Schaltfläche oben rechts.

   >[!NOTE]
   > Bei Verwendung des Verschiebevorgangs wird empfohlen, alle Pfade in nur einen Ordner zu verschieben (z. B. unter `/etc/packages/content-transformation/paths`). Wenn also die Backup-Pakete installiert sind, um die Instanz wieder in den Originalzustand zu versetzen, wird der Ordner (`/etc/packages/content-transformation/paths`) kann mithilfe des Entfernen-Vorgangs gelöscht werden, um die Repository-Größe zu reduzieren.

   ![image](/help/journey-migration/content-transformer/assets/ct-5.png)
   ![image](/help/journey-migration/content-transformer/assets/ct-6.png)

   >[!NOTE]
   > Jeder Vorgang, der den Quellinhalt ändern kann (`move`/`remove`/`rename`) erstellt standardmäßig ein Backup-Paket der Quellpfade unter `/etc/packages/content-transformation` vor der Umwandlung. Obwohl jedes Vorgangsdialogfeld über eine Option zum Deaktivieren/Aktivieren der Erstellung von Backup-Paketen verfügt, wird dringend empfohlen, die Erstellung von Paketen immer zu aktivieren.

1. Ein Beispiel für ein Backup-Paket, das für den Verschiebevorgang der Pfade erstellt wurde, finden Sie unten. Klicken Sie auf Installieren , um die Quellpfade wiederherzustellen. Beachten Sie, dass die Installation nur die Quellpfade an ihren ursprünglichen Speicherort zurückbringt und nicht die Pfade löscht, auf denen sie während der Transformation verschoben wurden. Um die Pfade am verschobenen Speicherort zu löschen, klicken Sie auf **Pfade hinzufügen** Schaltfläche zum Hinzufügen des Standorts (z. B. `/etc/packages/content-transformation/paths`), wählen Sie den Ort aus und klicken Sie auf **Entfernen**.

   >[!CAUTION]
   > Nicht löschen `/etc/packages/content-transformation` da dies der Speicherort ist, an dem sich die Backup-Pakete befinden. Nur wenn Sie sicher sind, dass Sie diese Pakete nicht mehr benötigen, können Sie diesen Speicherort löschen, um die Repository-Größe zu reduzieren.

   ![image](/help/journey-migration/content-transformer/assets/ct-7.png)
   ![image](/help/journey-migration/content-transformer/assets/ct-8.png)
