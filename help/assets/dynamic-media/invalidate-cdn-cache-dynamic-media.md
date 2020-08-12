---
title: Ungültigmachen des CDN-Cache über dynamische Medien
description: Indem Sie die Inhalte im CDN (Content Delivery Network)-Cache ungültig machen, können Sie von Dynamic Media bereitgestellte Assets schnell aktualisieren. Sie müssen dazu also nicht auf einen Ablauf des Caches warten.
translation-type: tm+mt
source-git-commit: 68ee2c58588ad519aac673652349e0fefd20ee57
workflow-type: tm+mt
source-wordcount: '1194'
ht-degree: 4%

---


# Invalidating the CDN cache by way of Dynamic Media {#invalidating-cdn-cache-for-dm-assets-in-aem-cs}

Dynamic Media-Assets werden vom CDN (Content Versand Network) zwischengespeichert, um einen schnellen Versand zu Ihren Kunden zu ermöglichen. However, when you make updates to those assets, you may want those changes to take effect immediately on your website. Purging or invalidating the CDN cache lets you quickly update assets that are delivered by Dynamic Media. Instead of waiting for the cache to expire using a TTL (Time To Live) value (default is 10 hours), you can send a request from within Dynamic Media user interface to have the cache expire within minutes.

>[!IMPORTANT]
>
>Die folgenden Schritte gelten nur für dynamische Medien auf AEM als Cloud Service. You must also use the out-of-the-box CDN that is bundled with AEM Dynamic Media. Andere benutzerdefinierte CDN werden von dieser Funktion nicht unterstützt. <!-- If you are using Dynamic Media in AEM 6.5, Service Pack 5 or earlier to invalidate the CDN cache [use the steps found here](/help/assets/invalidate-cdn-cache-dm-classic.md). -->

See also [Caching overview in Dynamic Media](https://helpx.adobe.com/de/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**So machen Sie den CDN-Cache über dynamische Medien ungültig**

*Teil 1: Erstellen einer Vorlage zum Ungültigmachen eines CDN*

1. Tippen Sie in AEM als Cloud Service auf **[!UICONTROL Werkzeuge > Assets > Vorlage für CDN-Ungültigmachung.]**

   ![CDN Validation feature](/help/assets/assets-dm/cdn-invalidation-template.png)

1. Führen Sie auf der Seite &quot; **[!UICONTROL CDN-Vorlage]** für die Ungültigmachung&quot;je nach Szenario eine der folgenden Optionen aus:

   | Szenario | Option |
   | --- | --- |
   | Ich habe mit Dynamic Media Classic bereits eine Vorlage für die Ungültigmachung von CDN erstellt. | Das Textfeld Vorlage **[!UICONTROL erstellen]** wird vorab mit Ihren Vorlagendaten ausgefüllt. In such case, you can either edit the template, or continue to the next step. |
   | Ich muss eine Vorlage erstellen. Was gebe ich ein? | Geben Sie im Textfeld Vorlage **** erstellen eine Bild-URL (einschließlich Bildvorgaben oder Modifikatoren) ein, die auf `<ID>`eine bestimmte Bild-ID verweist, wie im folgenden Beispiel gezeigt:<br><br>`https://my.publishserver.com/is/image/company_name/<ID>?$product$`<br><br>Wenn die Vorlage nur enthält `<ID>`, dann werden dynamische Medien ausgefüllt, `https://<publishserver_name>/is/image` wobei `<publishserver_name>` der Name des Publish-Servers und die ausgewählten Assets ungültig `ID` sind.<br><br>Nur Bilder, das heißt, `/is/image`können automatisch basierend auf der Vorlage erstellt werden. Beim Hinzufügen von Assets wie Videos oder PDFs mit der Asset-Auswahl werden keine URLs automatisch generiert. `/is/content/` Stattdessen müssen Sie diese Assets entweder in der Vorlage &quot;CDN-Ungültigmachung&quot;angeben oder Sie können die URL zu diesen Assets in *Teil 2 manuell hinzufügen: Festlegen von Optionen* für die CDN-Ungültigmachung.<br>Asset-Formate, die in dynamischen Medien unterstützt werden, können ungültig gemacht werden. Assets wie PowerPoints oder Textdateien werden nicht für die CDN-Ungültigmachung unterstützt.<br>Wenn Sie die Vorlage erstellen, achten Sie jedoch darauf, dass Sie die Syntax und die Schreibweise genau beachten; Bei dynamischen Medien wird keine Vorlagenüberprüfung durchgeführt.<br>The following template example is for illustration purposes only. |

   ![Vorlage für die Ungültigmachung von CDN - Erstellen](/help/assets/assets-dm/cdn-invalidation-template-create-2.png)

1. In the upper-right corner of the CDN Invalidation Template page, tap **[!UICONTROL Save]**, then tap **[!UICONTROL OK]**.

   *Part 2: Setting CDN Invalidation options*

1. Tippen Sie in AEM als Cloud Service auf **[!UICONTROL Werkzeuge > Assets > CDN-Ungültigmachung.]**

   ![CDN-Validierungsfunktion](/help/assets/assets-dm/cdn-invalidation-path.png)

1. Wählen Sie auf der Seite &quot; **[!UICONTROL CDN-Ungültigmachung]** - **[!UICONTROL Hinzufügen Details]** &quot;die Assets für die Ungültigmachung des CDN aus.

   ![CDN-Ungültigerklärung - Hinzufügen](/help/assets/assets-dm/cdn-invalidation-add-details-2.png)

   >[!NOTE]
   >
   >Wenn Sie die Optionen Asset- **[!UICONTROL verknüpfte Bildvorgaben im CDN]** *ungültig machen* und **[!UICONTROL auf der Grundlage der Vorlage]** ungültig machen möchten, wird die Basis-URL der ausgewählten Assets zur Ungültigmachung formatiert. Sie sollten diese Option nur für Bilder verwenden.


   | Option | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Invalidierungs-Asset hat Bildvorgaben in CDN zugeordnet]** | (Optional) Wenn Sie diese Option aktivieren, können Sie ein oder mehrere dynamische Medien-Assets auswählen, unabhängig vom MIME-Typ und den zugehörigen Bildvorgaben für die Cache-Ungültigmachung.<br>Assets und die zugehörigen vordefinierten URLs werden automatisch zur Ungültigmachung erstellt. Diese Option funktioniert nur für Bild-<br>Assets. Sie können zwar einen oder mehrere Ordner mit Assets auswählen, jedoch wird diese Vorgehensweise von Adobe nicht empfohlen. Stattdessen sollten Sie einzelne Asset-Dateien auswählen. |
   | **[!UICONTROL Auf Vorlage basierende Ungültigmachung]** | (Optional) Aktivieren Sie diese Option, um nur die definierte Vorlage für die URL-Bildung zu verwenden. |
   | **[!UICONTROL Assets hinzufügen]** | Verwenden Sie die Asset-Auswahl, um Assets auszuwählen, die ungültig gemacht werden sollen. Sie können veröffentlichte oder unveröffentlichte Assets auswählen.<br>You may get a blank list when you add assets. Dynamische Medien verwenden die Vorlage &quot;Ungültiges CDN&quot;, um automatisch eine URL zu erstellen, um das CDN für ungültig zu erklären. If no CDN Invalidate Template was created, then you get a blank list.<br>Die Zwischenspeicherung im CDN erfolgt URL-basiert und nicht Asset-basiert. Daher müssen Sie sich über die vollständigen URLs auf Ihrer Website im Klaren sein. After you determine those URLs, you can add them to the template.Then, you can select and add those assets and invalidate the URLs in one step. Die andere Option besteht darin, der Liste zur Ungültigmachung von CDN URLs hinzuzufügen. Wenn Sie diesen Ansatz bevorzugen, müssen Sie keine Assets auswählen und hinzufügen, bevor Sie auf **[!UICONTROL Weiter]** tippen und dann zur Ungültigmachung **[!UICONTROL senden]** .<br>Verwenden Sie diese Option in Verbindung mit **[!UICONTROL Ungültigmachen von Asset-zugeordneten Bildvorgaben im CDN]**, **[!UICONTROL Ungültigmachen auf der Grundlage einer Vorlage]** oder beidem. |
   | **[!UICONTROL URL hinzufügen]** | Fügen Sie Dynamischen Medien-Assets, deren CDN-Cache Sie ungültig machen möchten, manuell vollständige URL-Pfade hinzu oder fügen Sie sie ein. Verwenden Sie diese Option, wenn Sie in ***Teil 1 keine Vorlage für die Ungültigmachung eines CDN erstellt haben: Arbeiten mit der Vorlage*** für die Ungültigmachung von CDN und nur wenige Assets zum Ungültigmachen.<br> |

1. Near the upper-right corner of the page, tap **[!UICONTROL Next]**.
1. Auf der Seite &quot; **[!UICONTROL CDN-Ungültigmachung]** - **[!UICONTROL Bestätigen]** &quot;wird im Feld &quot;Liste der **[!UICONTROL URLs]** &quot;eine Liste einer oder mehrerer URLs angezeigt, die aus der zuvor erstellten Vorlage zur Ungültigmachung des CDN und den soeben hinzugefügten Assets generiert wurden.

   Beispiel: Wenn die Vorlage für die CDN-Ungültigmachung zuvor erstellt wurde, nehmen Sie an, dass Sie ein einzelnes Asset namens hinzugefügt haben `spinset`. Wenn Sie auf **[!UICONTROL Extras > Assets > CDN-Ungültigmachung]** tippen, werden die folgenden fünf generierten URLs in der Benutzeroberfläche &quot; **[!UICONTROL CDN-Ungültigmachung - Bestätigen]** &quot;angezeigt:

   ![CDN Invalidation - Confirm](/help/assets/assets-dm/cdn-invalidation-confirm-2.png)

   If necessary, tap the **X** to the right of a URL to delete it from invalidation process. You can have up to 1000 URLs at a given time.

1. Tippen Sie in der rechten oberen Ecke der Seite auf **[!UICONTROL Senden]** , um den CDN-Ungültigkeitsprozess zu starten.

## Troubleshooting CDN Invalidation errors

* Mit dieser Funktion können Sie bis zu 1000 URLs zu einem bestimmten Zeitpunkt für ungültig erklären. A number greater than 1000 results in an error which you can resolve by deleting URLs in the **[!UICONTROL CDN Invalidation – Confirm]** page.
* In allen Fällen wird entweder der gesamte Stapel zur Ungültigmachung verarbeitet oder der gesamte Stapel ist fehlgeschlagen.

| Fehler | Erklärung |
| --- | --- |
| *Failed to retrieve URL(s) for selected asset(s).* | Tritt auf, wenn eines der folgenden Szenarien erfüllt ist:<br>- Eine Konfiguration für dynamische Medien wurde nicht gefunden.<br>– There is a exception while retrieving a service user through which the Dynamic Media configuration is read.<br>- Der Veröffentlichungsserver bzw. der Firma-Stammordner, der zum Erstellen der URLs verwendet wird, fehlen in der Konfiguration für dynamische Medien. |
| *Some URLs are not defined correctly. Bitte korrigieren und erneut einreichen.* | Tritt auf, wenn die IPS CDN-Cache-Ungültigungs-API einen Fehler zurückgibt, dass die URL auf eine andere Firma verweist, oder wenn die URL gemäß der von der IPS cdnCacheInvalidation API durchgeführten Überprüfung ungültig ist. |
| *CDN-Cache konnte nicht ungültig gemacht werden.* | Tritt auf, wenn die Anforderung zum Ungültigmachen des CDN-Cache aus einem anderen Grund fehlschlägt. |
| *Keine URL(s) eingegeben, um ungültig zu werden.* | Tritt auf, wenn auf der Seite &quot; **[!UICONTROL CDN-Ungültigmachung - Bestätigen&quot;keine URLs vorhanden sind und Sie auf]** Senden **** tippen. |


<!--  | I do not want to create a template. | Near the upper-right corner of the page, tap **[!UICONTROL Cancel]**, then continue with ***Part 2: Working with CDN Invalidation***. Note that while you are not required to create a template to use CDN Invalidation, Adobe recommends that you create one, especially if you have numerous assets that you need to update immediately, on a regular basis. The template is used at the time you set CDN invalidation options. | -->