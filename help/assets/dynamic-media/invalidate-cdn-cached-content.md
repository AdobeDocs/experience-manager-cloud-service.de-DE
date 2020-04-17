---
title: 'Ungültigmachen von Inhalten im CDN-Cache '
description: Indem Sie die Inhalte im CDN (Content Delivery Network)-Cache ungültig machen, können Sie von Dynamic Media bereitgestellte Assets schnell aktualisieren. Sie müssen dazu also nicht auf einen Ablauf des Caches warten.
translation-type: ht
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6

---


# Ungültigmachen von Inhalten im CDN-Cache   {#invalidating-your-cdn-cached-content}

Dynamic Media-Assets werden vom CDN zwecks schneller Bereitstellung im Cache gespeichert. Wenn Sie ein Asset aktualisieren, sollen diese Änderungen jedoch möglicherweise sofort wirksam werden. Indem Sie die Inhalte im CDN (Content Delivery Network)-Cache ungültig machen, können Sie von Dynamic Media bereitgestellte Assets schnell aktualisieren. Sie müssen dazu also nicht auf einen Ablauf des Caches warten.

Siehe auch [Übersicht über Caching in Dynamic Media Classic (Scene7)](https://helpx.adobe.com/de/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**So machen Sie Inhalte im CDN-Cache ungültig:** 

1. Melden Sie sich bei Ihrem Dynamic Media Classic (Scene7)-Konto an: 

   [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Ihre Anmeldedaten haben Sie zum Zeitpunkt der Bereitstellung von Adobe erhalten. Wenn Ihnen die Informationen nicht vorliegen, wenden Sie sich an den technischen Support.

1.  Klicken Sie auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen]**.
1. Suchen Sie auf der Seite „Allgemeine Programmeinstellungen“ unter der Überschrift für Server-Gruppen das Textfeld **[!UICONTROL CDN-Ungültigmachen-Vorlage]**.

1. Geben Sie die Vorlage an, die zum Ungültigmachen des CDN (Content Delivery Network)-Caches verwendet wird.

   Angenommen Sie geben eine Bild-URL (einschließlich Bildvorgaben oder Modifikatoren) ein, die auf `<ID>` verweist, anstatt auf eine bestimmte Bild-ID wie im folgenden Beispiel:

   `https://server.com/is/image/Company/<ID>?$product$`

   Wenn die Vorlage ausschließlich `<ID>` enthält, füllt Dynamic Media die URL `https://<server>/is/image` auf. Dabei steht `<server>` für den Veröffentlichungs-Server-Namen, der in den allgemeinen Einstellungen definiert ist, und &lt;ID> für die Assets, die ungültig gemacht werden sollen.

1. Klicken Sie in der rechten unteren Ecke der Seite auf **[!UICONTROL Schließen]**.
1. Wählen Sie in der Dynamic Media Classic (Scene7)-Benutzeroberfläche mindestens ein Asset aus und klicken Sie auf **[!UICONTROL Datei > Ungültiges CDN]**. Daraufhin wird eine Liste der URL(s) angezeigt, die anhand der von Ihnen erstellten Vorlage und ausgewählten Assets generiert wurde.  Dabei werden die Server-URL-Einträge unter „Veröffentlichungsservername“ in den allgemeinen Programmeinstellungen verwendet. 

   Angenommen Sie haben mit der im vorherigen Schritt festgelegten CDN-Ungültigmachen-Vorlage ein Bild-Asset mit der Bezeichnung `Backpack_B` ausgewählt. Wenn Sie dann auf **[!UICONTROL Datei > Ungültiges CDN]** klicken, wird die folgende URL in der Benutzeroberfläche zum Ungültigmachen des CDN-Caches generiert:

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. Klicken Sie im URL-Listenfeld auf **[!UICONTROL Weiter]**, um den Cache für jede einzelne URL zu löschen.  Sie können eine URL bearbeiten oder eine URL hinzufügen, indem Sie diese in das URL-Listenfeld eingeben oder einfügen; es ist nicht erforderlich, die CDN-Ungültigmachen-Vorlage vorab festzulegen  

   Wenn Sie auf **[!UICONTROL Weiter]** klicken, werden Sie über eine Anzeige informiert, wie lange es ungefähr dauert, bis der Cache gelöscht ist. 

   Wenn Sie mehrere Assets ausgewählt und dann auf **[!UICONTROL Datei > Ungültiges CDN]** geklickt haben, wird jedes Asset in der gespeicherten **[!UICONTROL Vorlagen-URL]** referenziert. Daher können Sie eine **[!UICONTROL CDN-Ungültigmachen-Vorlage]** definieren, die auf alle auf Ihrer Website referenzierten URL-Bildvorgaben (wie Produktdetails, Suchergebnisse usw.) verweist. Wenn Sie dann Bilder auswählen, die im Cache ungültig gemacht werden sollen, werden die URLs automatisch in der Oberfläche aufgefüllt.

   >[!NOTE]
   >
   >Wenn Sie Assets auswählen und dann auf **[!UICONTROL Datei > Ungültiges CDN]** klicken, erstellt Dynamic Media mithilfe einer CDN-Ungültigmachen-Vorlage automatisch die URLs, die für das Content Delivery Network (CDN) ungültig gemacht werden sollen. Enthält das Textfeld **[!UICONTROL CDN-Ungültigmachen-Vorlage]** keinen Eintrag, wird eine leere URL-Liste zurückgegeben. Die Speicherung im CDN-Cache erfolgt nicht Asset-basiert, sondern URL-basiert.  Daher müssen Sie über alle URLs auf Ihrer Website informiert sein.  Nachdem Sie diese URLs ermittelt haben, können Sie sie dem in vorherigen Schritten genannten Textfeld **[!UICONTROL CDN-Ungültigmachen-Vorlage]** hinzufügen. Sie können dann diese Assets auswählen und die URLs in einem Schritt ungültig machen.
   >
   >Eine weitere Möglichkeit besteht darin, komplette URLs der Liste **[!UICONTROL Ungültiges CDN]** hinzuzufügen. Wenn Sie diesem Ansatz folgen, ist es nicht erforderlich, Assets in Dynamic Media Classic auszuwählen, bevor Sie die Option **[!UICONTROL Datei > Ungültiges CDN]** aufrufen.

