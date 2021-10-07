---
title: Invalidierung des CDN (Content Delivery Network)-Cache über Dynamic Media Classic
description: Erfahren Sie, wie Sie zwischengespeicherten Inhalt im CDN (Content Delivery Network) ungültig machen, damit Sie von Dynamic Media bereitgestellte Assets schnell aktualisieren können, anstatt darauf zu warten, dass der Cache abläuft.
feature: Asset Management,Dynamic Media Classic
role: Admin,User
exl-id: 7e488699-5633-437f-9e2e-58c98aa13145
source-git-commit: 7d67bdb5e0571d2bfee290ed47d2d7797a91e541
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 72%

---

# Invalidierung des CDN-Cache über Dynamic Media Classic {#invalidating-your-cdn-cached-content}

Dynamic Media-Assets werden vom CDN (Content Delivery Network) zwischengespeichert, um eine schnelle Bereitstellung zu ermöglichen. Wenn Sie ein Asset aktualisieren, sollen diese Änderungen jedoch sofort wirksam werden. Indem Sie die Inhalte im CDN-Cache ungültig machen, können Sie von Dynamic Media bereitgestellte Assets schnell aktualisieren. Sie müssen dazu also nicht auf einen Ablauf des Cache warten.

>[!NOTE]
>
>Für diese Funktion müssen Sie das im Lieferumfang von Adobe Experience Manager Dynamic Media enthaltene vorkonfigurierte CDN verwenden. Andere benutzerdefinierte CDN werden von dieser Funktion nicht unterstützt.

>[!IMPORTANT]
>
>Diese Schritte gelten nur für Dynamic Media in Adobe Experience Manager 6.5, Service Pack 5 oder früher. <!-- If you are using Dynamic Media in AEM as a Cloud Service, [use the new steps found here](/help/assets/invalidate-cdn-cache-dynamic-media.md). -->

Siehe auch [Überblick über Caching in Dynamic Media Classic](https://helpx.adobe.com/de/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**So machen Sie Ihren CDN-Cache mit Dynamic Media Classic ungültig:**

1. Öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=de#getting-started) und melden Sie sich bei Ihrem Konto an.

   Ihre Benutzer- und Anmeldedaten haben Sie zum Zeitpunkt der Bereitstellung von Adobe erhalten. Wenn Ihnen die Informationen nicht vorliegen, wenden Sie sich an den technischen Support.

1. Gehen Sie zu **[!UICONTROL Setup]** > **[!UICONTROL Anwendungseinstellungen]** > **[!UICONTROL Allgemeine Einstellungen]**.
1. Suchen Sie auf der Seite „Allgemeine Programmeinstellungen“ unter der Überschrift für Server-Gruppen das Textfeld **[!UICONTROL Vorlage für CDN-Invalidierung]**.

1. Geben Sie die Vorlage an, die zur Invalidierung des CDN (Content Delivery Network)-Cache verwendet wird.

   Angenommen Sie geben eine Bild-URL (einschließlich Bildvorgaben oder Modifikatoren) ein, die auf `<ID>` verweist, anstatt auf eine bestimmte Bild-ID wie im folgenden Beispiel:

   `https://server.com/is/image/Company/<ID>?$product$`

   Wenn die Vorlage ausschließlich `<ID>` enthält, füllt Dynamic Media die URL `https://<server>/is/image` auf. Dabei steht `<server>` für den Veröffentlichungsservernamen, der in den allgemeinen Einstellungen definiert ist, und &lt;ID> für die Assets, die ungültig gemacht werden sollen.

1. Wählen Sie in der rechten unteren Ecke der Seite **[!UICONTROL Close]** aus.
1. Wählen Sie in der Benutzeroberfläche von Dynamic Media Classic (Scene7) mindestens ein Asset aus und gehen Sie dann zu **[!UICONTROL Datei]** > **[!UICONTROL Ungültiges CDN]**. Daraufhin wird eine Liste der URLs angezeigt, die anhand der von Ihnen erstellten Vorlage und ausgewählten Assets generiert wurde. Dabei werden die Server-URL-Einträge unter „Veröffentlichungs-Servername“ in den allgemeinen Programmeinstellungen verwendet.

   Angenommen Sie haben mit der im vorherigen Schritt festgelegten Vorlage für CDN-Invalidierung ein Bild-Asset mit der Bezeichnung `Backpack_B` ausgewählt. Wenn Sie zu **[!UICONTROL Datei]** > **[!UICONTROL Ungültiges CDN]** gehen, wird die folgende URL in der Benutzeroberfläche für CDN-Invalidierung generiert:

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. Wählen Sie im URL-Listenfeld **[!UICONTROL Weiter]** aus, um den Cache für jede bestimmte URL zu löschen. Sie können eine URL bearbeiten oder eine URL hinzufügen, indem Sie diese in das URL-Listenfeld eingeben oder einfügen. Es ist nicht erforderlich, die Vorlage für die CDN-Invalidierung vorab festzulegen.

   Nachdem Sie **[!UICONTROL Weiter]** ausgewählt haben, wird ein Indikator angezeigt, der Ihnen eine Schätzung der Dauer gibt, die zum Löschen des Caches erforderlich ist.

   Wenn Sie mehrere Assets ausgewählt und dann zu **[!UICONTROL Datei]** > **[!UICONTROL Ungültiges CDN]** gewechselt haben, wird jedes Asset in der gespeicherten **[!UICONTROL Vorlagen-URL]** referenziert. Daher können Sie eine **[!UICONTROL Vorlage für die CDN-Invalidierung]** definieren, die auf alle auf Ihrer Website referenzierten URL-Bildvorgaben wie Produktdetails, Suchergebnisse usw. verweist. Wenn Sie dann Bilder auswählen, die im Cache ungültig gemacht werden sollen, werden die URLs automatisch in der Oberfläche aufgefüllt.

   >[!NOTE]
   >
   >Wenn Sie Assets auswählen und dann zu **[!UICONTROL Datei]** > **[!UICONTROL Ungültiges CDN]** gehen, verwendet Dynamic Media eine Vorlage für CDN-Invalidierung, um automatisch URLs zu erstellen, die aus dem CDN ungültig gemacht werden. Enthält das Textfeld **[!UICONTROL Vorlage für CDN-Invalidierung]** keinen Eintrag, wird eine leere URL-Liste zurückgegeben. Das Caching im CDN erfolgt nicht auf einem Asset-basierten Element. Es ist URL-basiert. Daher müssen Sie sich der vollständigen URLs auf Ihrer Website bewusst sein. Nachdem Sie diese URLs ermittelt haben, können Sie sie dem in vorherigen Schritten genannten Textfeld **[!UICONTROL Vorlage für CDN-Invalidierung]** hinzufügen. Sie können dann diese Assets auswählen und die URLs in einem Schritt ungültig machen.
   >
   >Eine weitere Möglichkeit besteht darin, komplette URLs der Liste **[!UICONTROL Ungültiges CDN]** hinzuzufügen. Wenn Sie diesem Ansatz folgen, ist es nicht erforderlich, Assets in Dynamic Media Classic auszuwählen, bevor Sie die Option **[!UICONTROL Datei]** > **[!UICONTROL CDN-Invalidierung]** aufrufen.
