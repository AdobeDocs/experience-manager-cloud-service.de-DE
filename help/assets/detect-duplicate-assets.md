---
title: Verwalten digitaler Assets
description: Erfahren Sie, wie Sie doppelte Assets erkennen
contentOwner: KK
mini-toc-levels: 3
feature: Asset Management,Publishing,Collaboration,Asset Processing
role: User,Architect,Admin
source-git-commit: bd0981b262f645653723f1b35d871808506d47ba
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 96%

---


# Erkennen doppelter Assets {#detect-duplicate-assets}

Wenn ein DAM-Benutzer ein oder mehrere Assets hochlädt, die bereits im Repository vorhanden sind, erkennt [!DNL Experience Manager] das Duplikat und benachrichtigt den Benutzer. Die Erkennung von Duplikaten ist standardmäßig deaktiviert, da sie je nach Größe des Repositorys und der Anzahl der hochgeladenen Assets die Leistung beeinträchtigen kann.

So aktivieren Sie die Funktion:

1. Gehen Sie zu **[!UICONTROL Tools > Assets > Assets-Konfigurationen]**.

1. Klicken Sie auf **[!UICONTROL Asset-Duplikaterkennung]**.

1. Klicken Sie auf der [!UICONTROL Seite zur Asset-Duplikaterkennung] auf **[!UICONTROL Aktiviert]**.

   Der `dam:sha1`-Wert für das Feld „Metadaten erkennen“ stellt sicher, dass doppelte Assets erkannt werden, auch wenn die Dateinamen unterschiedlich sind.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

   ![Asset-Duplikations-Detektor](assets/asset-duplication-detector.png)

>[!NOTE]
>
>Wenn Sie die Duplikaterkennung mit der Konfigurationsdatei `/apps/example/config.author/com.adobe.cq.assetcompute.impl.assetprocessor.AssetDuplicationDetector.cfg.json` (OSGi-Konfiguration) verwenden, können Sie sie weiterhin verwenden. Adobe empfiehlt jedoch die Verwendung der neuen Methode.


Nach der Aktivierung sendet Experience Manager Benachrichtigungen über doppelte Assets an den Posteingang von Experience Manager. Dabei handelt es sich um ein aggregiertes Ergebnis für mehrere Duplikate. Benutzer können die Assets anhand der Ergebnisse entfernen.

![Posteingangsbenachrichtigung für doppelte Assets](assets/duplicate-detect-inbox-notification.png)

>[!NOTE]
>
>Wenn Sie Assets in das Repository hochladen, erkennt Experience Manager Duplikate und benachrichtigt Sie über die ersten 100 doppelt vorhandenen Assets.

