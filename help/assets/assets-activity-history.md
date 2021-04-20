---
title: Aktivitäts-Stream in der Zeitleiste
description: Dieser Artikel beschreibt, wie Sie Aktivitätsprotokolle für Assets in der Zeitleiste anzeigen können.
contentOwner: AG
feature: Asset Reports,Asset Management
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 8093f6cec446223af58515fd8c91afa5940f9402
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 96%

---


# Anzeigen von Protokollen zu Vorgängen für Assets {#activity-stream-in-timeline}

Diese Funktion zeigt Aktivitätsprotokolle für Assets in der Zeitleiste an. Wenn Sie einen der folgenden Asset-bezogenen Vorgänge in [!DNL Experience Manager Assets]durchführen, aktualisiert die Aktivitäts-Stream-Funktion die Zeitleiste, um die Aktivität anzuzeigen.

Folgende Vorgänge werden im Aktivitäts-Stream protokolliert:

* Erstellen
* Löschen
* Download (einschließlich Ausgabedarstellungen)
* Veröffentlichen
* Veröffentlichung rückgängig machen
* Genehmigen
* Ablehnen
* Verschieben

Die in der Zeitleiste angezeigten Aktivitätsprotokolle werden aus dem Ordner `/var/audit/com.day.cq.dam/content/dam` in CRX abgerufen, in dem Protokolldateien gespeichert werden.  Außerdem wird die Zeitleisten-Aktivität protokolliert, wenn neue Assets hochgeladen oder vorhandene Assets geändert und in [!DNL Experience Manager] über [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html) oder das [[!DNL Experience Manager] -Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html?lang=de) gespeichert werden.

>[!NOTE]
>
>Übergangsarbeitsabläufe werden nicht in der Zeitleiste angezeigt, da keine Verlaufsinformationen für diese Arbeitsabläufe gespeichert werden.

Um den Aktivitäts-Stream anzuzeigen, führen Sie einen oder mehrere Vorgänge für die Assets aus, wählen Sie das Asset aus und wählen Sie dann **[!UICONTROL Zeitleiste]** aus der GlobalNav-Liste aus.

<!-- ![timeline-2](assets/timeline-2.png) -->

In der Zeitleiste wird der Aktivitäts-Stream für die mit den Assets ausgeführten Vorgänge angezeigt.

<!-- ![activity_stream](assets/activity_stream.png) -->

>[!NOTE]
>
>Der standardmäßige Speicherort für Aufgaben des Typs **[!UICONTROL Veröffentlichen]** und **[!UICONTROL Veröffentlichung rückgängig machen]** befindet sich in `/var/audit/com.day.cq.replication/content`. Für Aufgaben des Typs **[!UICONTROL Verschieben]** ist der standardmäßige Speicherort `/var/audit/com.day.cq.wcm.core.page`.
