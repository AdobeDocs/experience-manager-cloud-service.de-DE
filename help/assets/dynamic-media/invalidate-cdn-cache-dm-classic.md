---
title: Invalidierung des CDN (Content Delivery Network)-Cache über Dynamic Media Classic
description: In diesem Abschnitt erfahren Sie, wie Sie Inhalte im CDN (Content Delivery Network)-Cache ungültig machen, um von Dynamic Media bereitgestellte Assets schnell zu aktualisieren. So müssen Sie nicht auf einen Ablauf des Cache warten.
contentOwner: Rick Brough
feature: Asset Management,Dynamic Media Classic
role: Admin,User
exl-id: 7e488699-5633-437f-9e2e-58c98aa13145
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 96%

---

# Invalidierung des CDN-Cache mithilfe von Dynamic Media Classic {#invalidating-your-cdn-cached-content}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime und Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>AEM Assets-Integration mit Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Erweiterbarkeit der Benutzeroberfläche</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Aktivieren von Dynamic Media Prime und Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Best Practices für die Suche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Best Practices für Metadaten</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Dynamic Media mit OpenAPI-Funktionen</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Entwicklerdokumentation zu AEM Assets</b></a>
        </td>
    </tr>
</table>

Dynamic Media-Assets werden vom CDN (Content Delivery Network) zwischengespeichert, um eine schnelle Bereitstellung zu ermöglichen. Wenn Sie ein Asset aktualisieren, sollen diese Änderungen jedoch sofort wirksam werden. Indem Sie die Inhalte im CDN-Cache ungültig machen, können Sie von Dynamic Media bereitgestellte Assets schnell aktualisieren. Sie müssen dazu also nicht auf einen Ablauf des Cache warten.

>[!NOTE]
>
>Für diese Funktion müssen Sie das im Lieferumfang von Adobe Experience Manager Dynamic Media enthaltene vorkonfigurierte CDN verwenden. Andere benutzerdefinierte CDN werden von dieser Funktion nicht unterstützt.

>[!IMPORTANT]
>
>Diese Schritte gelten nur für Dynamic Media in Adobe Experience Manager 6.5, Service Pack 5 oder früher. <!-- If you are using Dynamic Media in AEM as a Cloud Service, [use the new steps found here](/help/assets/invalidate-cdn-cache-dynamic-media.md). -->

<!-- REMOVED MARCH 28, 2022 BECAUSE OF 404; NO REDIRECT WAS PUT IN PLACE BY SUPPORT See also [Cache overview in Dynamic Media Classic](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html). -->

**So machen Sie Ihren CDN-Cache mit Dynamic Media Classic ungültig:**

1. Öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=de#getting-started) und melden Sie sich bei Ihrem Konto an.

   Ihre Benutzer- und Anmeldedaten haben Sie zum Zeitpunkt der Bereitstellung von Adobe erhalten. Wenn Sie nicht über diese Informationen verfügen, wenden Sie sich an den Support.

1. Gehen Sie zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Anwendungseinrichtung]** > **[!UICONTROL Allgemeine Einstellungen]**.
1. Suchen Sie auf der Seite „Allgemeine Programmeinstellungen“ unter der Überschrift für Server-Gruppen das Textfeld **[!UICONTROL Vorlage für CDN-Invalidierung]**.

1. Geben Sie die Vorlage an, die zur Invalidierung des CDN (Content Delivery Network)-Cache verwendet wird.

   Angenommen Sie geben eine Bild-URL (einschließlich Bildvorgaben oder Modifikatoren) ein, die auf `<ID>` verweist, anstatt auf eine bestimmte Bild-ID wie im folgenden Beispiel:

   `https://server.com/is/image/Company/<ID>?$product$`

   Wenn die Vorlage ausschließlich `<ID>` enthält, füllt Dynamic Media die URL `https://<server>/is/image` auf. Dabei steht `<server>` für den Veröffentlichungsservernamen, der in den allgemeinen Einstellungen definiert ist, und &lt;ID> für die Assets, die ungültig gemacht werden sollen.

1. Klicken Sie unten rechts auf der Seite auf **[!UICONTROL Schließen]**.
1. Wählen Sie in der Benutzeroberfläche von Dynamic Media Classic (Scene7) mindestens ein Asset aus und gehen Sie zu **[!UICONTROL Datei]** > **[!UICONTROL CDN-Invalidierung]**. Daraufhin wird eine Liste der URLs angezeigt, die anhand der von Ihnen erstellten Vorlage und ausgewählten Assets generiert wurde. Dabei werden die Server-URL-Einträge unter „Veröffentlichungs-Servername“ in den allgemeinen Programmeinstellungen verwendet.

   Angenommen Sie haben mit der im vorherigen Schritt festgelegten Vorlage für CDN-Invalidierung ein Bild-Asset mit der Bezeichnung `Backpack_B` ausgewählt. Wenn Sie dann auf **[!UICONTROL Datei]** > **[!UICONTROL CDN-Invalidierung]** klicken, wird die folgende URL in der Benutzeroberfläche zur Invalidierung des CDN generiert:

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. Klicken Sie im URL-Listenfeld auf **[!UICONTROL Weiter]**, um den Cache für jede einzelne URL zu löschen. Sie können eine URL bearbeiten oder eine URL hinzufügen, indem Sie diese in das URL-Listenfeld eingeben oder einfügen. Es ist nicht erforderlich, die Vorlage für die CDN-Invalidierung vorab festzulegen.

   Wenn Sie auf **[!UICONTROL Weiter]** klicken, werden Sie über eine Anzeige informiert, wie lange es ungefähr dauert, bis der Cache gelöscht ist.

   Wenn Sie mehrere Assets ausgewählt und dann auf **[!UICONTROL Datei]** > **[!UICONTROL CDN-Invalidierung]** geklickt haben, wird jedes Asset in der gespeicherten **[!UICONTROL Vorlagen-URL]** referenziert. Daher können Sie eine **[!UICONTROL Vorlage für die CDN-Invalidierung]** definieren, die auf alle auf Ihrer Website referenzierten URL-Bildvorgaben wie Produktdetails, Suchergebnisse usw. verweist. Wenn Sie dann Bilder auswählen, die im Cache ungültig gemacht werden sollen, werden die URLs automatisch in der Oberfläche aufgefüllt.

   >[!NOTE]
   >
   >Wenn Sie Assets auswählen und dann zu **[!UICONTROL Datei]** > **[!UICONTROL CDN-Invalidierung]** gehen, erstellt Dynamic Media mithilfe einer Vorlage für die Invalidierung von CDNs automatisch die URLs, die im CDN ungültig gemacht werden sollen. Enthält das Textfeld **[!UICONTROL Vorlage für CDN-Invalidierung]** keinen Eintrag, wird eine leere URL-Liste zurückgegeben. Das Caching im CDN erfolgt nicht auf einem Asset-basierten Element. Es ist URL-basiert. Daher müssen Sie sich der vollständigen URLs auf Ihrer Website bewusst sein. Nachdem Sie diese URLs ermittelt haben, können Sie sie dem in vorherigen Schritten genannten Textfeld **[!UICONTROL Vorlage für CDN-Invalidierung]** hinzufügen. Sie können dann diese Assets auswählen und die URLs in einem Schritt ungültig machen.
   >
   >Eine weitere Möglichkeit besteht darin, komplette URLs der Liste **[!UICONTROL Ungültiges CDN]** hinzuzufügen. Wenn Sie diesem Ansatz folgen, ist es nicht erforderlich, Assets in Dynamic Media Classic auszuwählen, bevor Sie die Option **[!UICONTROL Datei]** > **[!UICONTROL CDN-Invalidierung]** aufrufen.
