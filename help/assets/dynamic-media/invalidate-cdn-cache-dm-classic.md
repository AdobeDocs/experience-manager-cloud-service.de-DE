---
title: Invalidierung des CDN (Content Delivery Network)-Cache über Dynamic Media Classic
description: '"Erfahren Sie, wie Sie zwischengespeicherten Inhalt in CDN (Content Delivery Network) ungültig machen, damit Sie von Dynamic Media bereitgestellte Assets schnell aktualisieren können, anstatt darauf zu warten, dass der Cache abläuft."'
feature: Asset Management, Dynamic Media Classic
role: Administrator,Business Practitioner
exl-id: 7e488699-5633-437f-9e2e-58c98aa13145
source-git-commit: d3ee23917eba4a2e4ae1f2bd44f5476d2ff7dce1
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 42%

---

# Invalidierung des CDN-Cache mithilfe von Dynamic Media Classic {#invalidating-your-cdn-cached-content}

Dynamic Media-Assets werden vom CDN (Content Delivery Network) zur schnellen Bereitstellung zwischengespeichert. Wenn Sie jedoch ein Asset aktualisieren, sollen diese Änderungen sofort wirksam werden. Durch die Invalidierung Ihres im CDN-Cache zwischengespeicherten Inhalts können Sie von Dynamic Media bereitgestellte Assets schnell aktualisieren, anstatt darauf zu warten, dass der Cache abläuft.

>[!NOTE]
>
>Für diese Funktion müssen Sie das vordefinierte CDN verwenden, das im Lieferumfang von Adobe Experience Manager Dynamic Media enthalten ist. Mit dieser Funktion werden keine anderen benutzerdefinierten CDNs unterstützt.

>[!IMPORTANT]
>
>Diese Schritte gelten nur für Dynamic Media in Adobe Experience Manager 6.5, Service Pack 5 oder früher. <!-- If you are using Dynamic Media in AEM as a Cloud Service, [use the new steps found here](/help/assets/invalidate-cdn-cache-dynamic-media.md). -->

Siehe auch [Überblick über Caching in Dynamic Media Classic](https://helpx.adobe.com/de/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**So machen Sie Ihren CDN-Cache mit Dynamic Media Classic ungültig:**

1. Öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=de#getting-started) und melden Sie sich bei Ihrem Konto an.

   Ihre Anmeldedaten und Anmeldedaten wurden von Adobe zum Zeitpunkt der Bereitstellung bereitgestellt. Wenn Ihnen die Informationen nicht vorliegen, wenden Sie sich an den technischen Support.

1. Klicken Sie auf **[!UICONTROL Einstellungen]** > **[!UICONTROL Anwendungseinstellungen]** > **[!UICONTROL Allgemeine Einstellungen]**. 
1. Suchen Sie auf der Seite „Allgemeine Programmeinstellungen“ unter der Überschrift für Server-Gruppen das Textfeld **[!UICONTROL Vorlage für CDN-Invalidierung]**.

1. Geben Sie die Vorlage an, die zur Invalidierung des CDN (Content Delivery Network)-Cache verwendet wird.

   Angenommen Sie geben eine Bild-URL (einschließlich Bildvorgaben oder Modifikatoren) ein, die auf `<ID>` verweist, anstatt auf eine bestimmte Bild-ID wie im folgenden Beispiel:

   `https://server.com/is/image/Company/<ID>?$product$`

   Wenn die Vorlage nur `<ID>` enthält, füllt Dynamic Media `https://<server>/is/image` auf, wobei `<server>` der Veröffentlichungsservername ist, der in den allgemeinen Einstellungen definiert ist, und &lt;ID> die Assets ist, die ungültig gemacht werden sollen.

1. Tippen Sie in der rechten unteren Ecke der Seite auf **[!UICONTROL Close]**.
1. Wählen Sie in der Benutzeroberfläche von Dynamic Media Classic (Scene7) mindestens ein Asset aus und tippen Sie dann auf **[!UICONTROL Datei]** > **[!UICONTROL Ungültiges CDN]**. Es wird eine Liste mit einer oder mehreren URLs angezeigt, die aus der von Ihnen erstellten Vorlage und den von Ihnen ausgewählten Assets generiert wurden. Dabei werden die Server-URL-Einträge unter „Veröffentlichungs-Servername“ in den allgemeinen Programmeinstellungen verwendet.

   Angenommen Sie haben mit der im vorherigen Schritt festgelegten Vorlage für CDN-Invalidierung ein Bild-Asset mit der Bezeichnung `Backpack_B` ausgewählt. Wenn Sie auf **[!UICONTROL Datei]** > **[!UICONTROL Ungültiges CDN]** tippen, wird die folgende generierte URL in der Benutzeroberfläche für CDN-Invalidierung generiert:

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. Tippen Sie im URL-Listenfeld auf **[!UICONTROL Weiter]** , um den Cache für jede bestimmte URL zu löschen. Sie können eine URL bearbeiten oder eine URL hinzufügen, indem Sie sie in das URL-Listenfeld eingeben oder einfügen. Sie müssen die Vorlage für CDN-Invalidierung nicht vorab festlegen.

   Wenn Sie auf **[!UICONTROL Weiter]** tippen, wird ein Indikator angezeigt, der Ihnen eine Schätzung der Dauer gibt, die zum Löschen des Caches erforderlich ist.

   Wenn Sie mehrere Assets ausgewählt und dann auf **[!UICONTROL Datei]** > **[!UICONTROL Ungültiges CDN]** getippt haben, wird jedes Asset in der gespeicherten **[!UICONTROL Vorlagen-URL]** referenziert. Daher können Sie eine **[!UICONTROL Vorlage für CDN-Invalidierung]** definieren, die auf jede URL-Bildvorgabe verweist, auf die auf Ihrer Website verwiesen wird, z. B. Produktdetails und Suchergebnisse. Wenn Sie dann Bilder auswählen, die im Cache ungültig gemacht werden sollen, werden die URLs automatisch in der Oberfläche aufgefüllt.

   >[!NOTE]
   >
   >Wenn Sie Assets auswählen und dann auf **[!UICONTROL Datei]** > **[!UICONTROL Ungültiges CDN]** tippen, verwendet Dynamic Media eine ungültige CDN-Vorlage, um automatisch URLs zu erstellen, die aus dem CDN ungültig gemacht werden. Enthält das Textfeld **[!UICONTROL Vorlage für CDN-Invalidierung]** keinen Eintrag, wird eine leere URL-Liste zurückgegeben. Das Caching im CDN erfolgt nicht auf einem Asset-basierten Element. Es ist URL-basiert. Daher müssen Sie sich der vollständigen URLs auf Ihrer Website bewusst sein. Nachdem Sie diese URLs ermittelt haben, können Sie sie dem in vorherigen Schritten genannten Textfeld **[!UICONTROL Vorlage für CDN-Invalidierung]** hinzufügen. Sie können dann diese Assets auswählen und die URLs in einem Schritt ungültig machen.
   >
   >Eine weitere Möglichkeit besteht darin, komplette URLs der Liste **[!UICONTROL Ungültiges CDN]** hinzuzufügen. Wenn Sie diesem Ansatz folgen, ist es nicht erforderlich, Assets in Dynamic Media Classic auszuwählen, bevor Sie die Option **[!UICONTROL Datei]** > **[!UICONTROL Ungültiges CDN]** aufrufen. 
