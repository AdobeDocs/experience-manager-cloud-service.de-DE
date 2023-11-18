---
title: Verwenden von Content Transformer
description: Erfahren Sie, wie Sie Ihre Inhaltsstruktur bei der Vorbereitung der Migration auf AEM as a Cloud Service umwandeln.
exl-id: 40516ff7-5686-42e6-bdd1-c9c6de432b09
source-git-commit: 6bb7b2d056d501d83cf227adb239f7f40f87d0ce
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 87%

---

# Verwenden von Content Transformer {#using-ct}

## Wichtige Überlegungen zur Verwendung von Content Transformer {#imp-considerations-ct}

Im folgenden Abschnitt finden Sie wichtige Überlegungen zur Verwendung von Content Transformer (CT):

* Um Content Transformer zu verwenden, müssen Sie zunächst den Best Practices Analyzer in Ihrer Adobe Experience Manager (AEM)-Umgebung ausführen.
* Obwohl Sie den Content Transformer in Ihrer Produktionsumgebung ausführen können, wird empfohlen, den Content Transformer in einem Klon Ihrer Produktionsumgebung auszuführen. Vor allem müssen Sie sicherstellen, dass BPA und CT in derselben Umgebung ausgeführt werden.
* Sie müssen ein Admin in der Umgebung sein, in der Sie den Content Transformer ausführen möchten.
* Jeder Vorgang, der den Quellinhalt ändern kann (Verschieben/Entfernen/Umbenennen), erstellt vor der Umwandlung standardmäßig ein Backup-Paket der Quellpfade unter `/etc/packages/content-transformation`. Obwohl jedes Vorgangsdialogfeld über eine Option zum Deaktivieren/Aktivieren der Erstellung von Backup-Paketen verfügt, wird dringend empfohlen, die Erstellung von Paketen immer zu aktivieren.
* Jede Seite im Content Transformer ist so konfiguriert, dass sie maximal 50 Ergebnisse auflistet, sodass gleichzeitig maximal 50 Ergebnisse umgewandelt werden können. Dies geschieht, um eine pünktliche Antwort auf der Benutzeroberfläche bereitzustellen.

## Verfügbarkeit {#availability-ct}

Der Content Transformer ist mit dem [Content Transfer Tool](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md) gebündelt, das als Zip-Datei vom Software Distribution-Portal heruntergeladen werden kann. Sie können das Paket mit Package Manager auf Ihrer Quellinstanz von (AEM) installieren.

>[!NOTE]
>Der Content Transformer ist mit dem Content Transfer Tool v2.0.20 oder höher verfügbar.

## Öffnen von Content Transformer {#opening-ct}

1. Melden Sie sich bei der Quell-AEM-Instanz als Admin an und rufen Sie die folgende Startseite auf: https://host:port/aem/start.html
1. Navigieren Sie zu Tools > Vorgänge > Inhaltsmigration

   ![Bild](/help/journey-migration/content-transformer/assets/ct-1.png)

   >[!NOTE]
   > Stellen Sie sicher, dass Sie den BPA-Bericht bereits ausgeführt haben, und überprüfen Sie ihn mit der URL http://host:port/apps/best-practices-analyzer/content/BestPracticesReport.html.

1. Klicken Sie auf die Karte mit dem Titel **Content Transformer für BPA-Bericht**

   ![Bild](/help/journey-migration/content-transformer/assets/ct-2.png)

   Im Folgenden finden Sie ein Beispiel dafür, wie die Übersichtsseite zu Content Transformer aussehen wird, wenn die Erstellung des BPA-Berichts erfolgreich war und inhaltliche Probleme auftraten.

   Die für den BPA-Bericht verbleibende Ablaufzeit wird in der Seitenleiste angezeigt. Es wird empfohlen, den Content Transformer mit dem neuesten BPA-Bericht auszuführen, um zu vermeiden, dass inhaltsbezogene Ergebnisse fehlen.

   ![Bild](/help/journey-migration/content-transformer/assets/ct-3.png)

1. Sie können die Probleme auf der Grundlage von `Pattern Code`, `Subtype`, `Importance` und `Source` filtern.

   ![Bild](/help/journey-migration/content-transformer/assets/ct-4.png)

1. Sie können alle oder bestimmte Probleme auswählen und diese verschieben, entfernen oder umbenennen. Benutzerdefinierte Pfade können auch über die Schaltfläche **Pfade hinzufügen** in der oberen rechten Ecke hinzugefügt werden.

   >[!NOTE]
   > Bei Verwendung des Verschiebevorgangs wird empfohlen, alle Pfade in nur einen Ordner zu verschieben (z. B. unter `/etc/packages/content-transformation/paths`). Wenn also die Backup-Pakete installiert sind, um die Instanz wieder in den Originalzustand zu versetzen, kann der Ordner (`/etc/packages/content-transformation/paths`) mithilfe des Vorgangs zum Entfernen gelöscht werden, um die Repository-Größe zu reduzieren.

   ![image](/help/journey-migration/content-transformer/assets/ct-5.png)
   ![image](/help/journey-migration/content-transformer/assets/ct-6.png)

   >[!NOTE]
   > Jeder Vorgang, der den Quellinhalt ändern kann (`move`/`remove`/`rename`), erstellt vor der Umwandlung standardmäßig ein Backup-Paket der Quellpfade unter `/etc/packages/content-transformation`. Obwohl jedes Vorgangsdialogfeld über eine Option zum Deaktivieren/Aktivieren der Erstellung von Backup-Paketen verfügt, wird dringend empfohlen, die Erstellung von Paketen immer zu aktivieren.

1. Ein Beispiel für ein Backup-Paket, das für den Verschiebevorgang der Pfade erstellt wurde, ist unten abgebildet. Klicken Sie auf „Installieren“, um die Quellpfade wiederherzustellen. Bei der Installation werden nur die Quellpfade wieder an ihren ursprünglichen Speicherort zurückgeführt, nicht jedoch die Pfade, auf denen sie während der Transformation verschoben wurden. Um die Pfade an dem verschobenen Speicherort zu löschen, klicken Sie auf die Schaltfläche **Pfade hinzufügen**, um den Speicherort hinzuzufügen (zum Beispiel `/etc/packages/content-transformation/paths`), wählen Sie den Speicherort aus und klicken Sie auf **Entfernen**.

   >[!CAUTION]
   > Löschen Sie nicht `/etc/packages/content-transformation`, da dies der Speicherort ist, an dem sich die Backup-Pakete befinden. Nur wenn Sie sicher sind, dass Sie diese Pakete nicht mehr benötigen, können Sie diesen Speicherort löschen, um die Repository-Größe zu reduzieren.

   ![image](/help/journey-migration/content-transformer/assets/ct-7.png)
   ![image](/help/journey-migration/content-transformer/assets/ct-8.png)
