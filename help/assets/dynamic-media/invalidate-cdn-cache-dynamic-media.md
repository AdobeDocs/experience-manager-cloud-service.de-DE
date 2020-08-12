---
title: Ungültigmachen des CDN-Cache über dynamische Medien
description: Indem Sie die Inhalte im CDN (Content Delivery Network)-Cache ungültig machen, können Sie von Dynamic Media bereitgestellte Assets schnell aktualisieren. Sie müssen dazu also nicht auf einen Ablauf des Caches warten.
translation-type: tm+mt
source-git-commit: aae3dcb0f44ef8e8d1401274fbf1fd47ea718b09
workflow-type: tm+mt
source-wordcount: '1194'
ht-degree: 4%

---


# Ungültigmachen des CDN-Cache über dynamische Medien {#invalidating-cdn-cache-for-dm-assets-in-aem-cs}

Dynamic Media-Assets werden vom CDN (Content Versand Network) zwischengespeichert, um einen schnellen Versand zu Ihren Kunden zu ermöglichen. Wenn Sie jedoch Aktualisierungen an diesen Assets vornehmen, möchten Sie möglicherweise, dass diese Änderungen sofort auf Ihrer Website wirksam werden. Purging or invalidating the CDN cache lets you quickly update assets that are delivered by Dynamic Media. Anstatt darauf zu warten, dass der Cache mit einem TTL-Wert (Time To Live) abläuft (Standard ist 10 Stunden), können Sie eine Anforderung von der Benutzeroberfläche von Dynamic Media senden, damit der Cache innerhalb von Minuten abläuft.

>[!IMPORTANT]
>
>The following steps apply only to Dynamic Media on AEM as a Cloud Service. You must also use the out-of-the-box CDN that is bundled with AEM Dynamic Media. Andere benutzerdefinierte CDN werden von dieser Funktion nicht unterstützt. <!-- If you are using Dynamic Media in AEM 6.5, Service Pack 5 or earlier to invalidate the CDN cache [use the steps found here](/help/assets/invalidate-cdn-cache-dm-classic.md). -->

See also [Caching overview in Dynamic Media](https://helpx.adobe.com/de/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**So machen Sie den CDN-Cache über dynamische Medien ungültig**

*Teil 1: Erstellen einer Vorlage zum Ungültigmachen eines CDN*

1. Tippen Sie in AEM als Cloud Service auf **[!UICONTROL Werkzeuge > Assets > Vorlage für CDN-Ungültigmachung.]**

   ![CDN-Validierungsfunktion](/help/assets/assets-dm/cdn-invalidation-template.png)

1. Führen Sie auf der Seite &quot; **[!UICONTROL CDN-Vorlage]** für die Ungültigmachung&quot;je nach Szenario eine der folgenden Optionen aus:

   | Szenario | Option |
   | --- | --- |
   | Ich habe mit Dynamic Media Classic bereits eine Vorlage für die Ungültigmachung von CDN erstellt. | Das Textfeld Vorlage **[!UICONTROL erstellen]** wird vorab mit Ihren Vorlagendaten ausgefüllt. In diesem Fall können Sie entweder die Vorlage bearbeiten oder mit dem nächsten Schritt fortfahren. |
   | Ich muss eine Vorlage erstellen. Was gebe ich ein? | Geben Sie im Textfeld Vorlage **** erstellen eine Bild-URL (einschließlich Bildvorgaben oder Modifikatoren) ein, die auf `<ID>`eine bestimmte Bild-ID verweist, wie im folgenden Beispiel gezeigt:<br><br>`https://my.publishserver.com/is/image/company_name/<ID>?$product$`<br><br>Wenn die Vorlage nur enthält `<ID>`, dann werden dynamische Medien ausgefüllt, `https://<publishserver_name>/is/image` wobei `<publishserver_name>` der Name des Publish-Servers und die ausgewählten Assets ungültig `ID` sind.<br><br>Nur Bilder, das heißt, `/is/image`können automatisch basierend auf der Vorlage erstellt werden. For `/is/content/`, adding assets such as videos or PDFs using the asset picker does not auto generate URLs. Stattdessen müssen Sie diese Assets entweder in der Vorlage &quot;CDN-Ungültigmachung&quot;angeben oder Sie können die URL zu diesen Assets in *Teil 2 manuell hinzufügen: Festlegen von Optionen* für die CDN-Ungültigmachung.<br>Asset formats that are supported in Dynamic Media are eligible for invalidation. Assets wie PowerPoints oder Textdateien werden nicht für die CDN-Ungültigmachung unterstützt.<br>When you create the template, but sure you pay careful attention to syntax and typos; Dynamic Media does not do any template validation.<br>Das folgende Beispiel dient nur zur Veranschaulichung. |

   ![Vorlage für die Ungültigmachung von CDN - Erstellen](/help/assets/assets-dm/cdn-invalidation-template-create-2.png)

1. Tippen Sie in der rechten oberen Ecke der Seite &quot;Vorlage für CDN-Ungültigmachung&quot;auf **[!UICONTROL Speichern]** und dann auf **[!UICONTROL OK]**.<br>

   ***Teil 2: Festlegen von Optionen für die CDN-Ungültigkeit***
<br>

1. Tippen Sie in AEM als Cloud Service auf **[!UICONTROL Werkzeuge > Assets > CDN-Ungültigmachung.]**

   ![CDN-Validierungsfunktion](/help/assets/assets-dm/cdn-invalidation-path.png)

1. Wählen Sie auf der Seite &quot; **[!UICONTROL CDN-Ungültigmachung]** - **[!UICONTROL Hinzufügen Details]** &quot;die Assets für die Ungültigmachung des CDN aus.

   ![CDN-Ungültigerklärung - Hinzufügen](/help/assets/assets-dm/cdn-invalidation-add-details-2.png)

   >[!NOTE]
   >
   >Wenn Sie die Optionen Asset- **[!UICONTROL verknüpfte Bildvorgaben im CDN]** *ungültig machen* und **[!UICONTROL auf der Grundlage der Vorlage]** ungültig machen möchten, wird die Basis-URL der ausgewählten Assets zur Ungültigmachung formatiert. You should use this option arrangement for images only.


   | Option | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Invalidierungs-Asset hat Bildvorgaben in CDN zugeordnet]** | (Optional) Wenn Sie diese Option aktivieren, können Sie ein oder mehrere dynamische Medien-Assets auswählen, unabhängig vom MIME-Typ und den zugehörigen Bildvorgaben für die Cache-Ungültigmachung.<br>Assets and their associated pre-defined preset URLs are auto formed for invalidation. This option works only for image assets<br>While you can select one or more folders containing assets, Adobe does not recommend this approach. Instead, you should select individual asset files. |
   | **[!UICONTROL Auf Vorlage basierende Ungültigmachung]** | (Optional) Aktivieren Sie diese Option, um nur die definierte Vorlage für die URL-Bildung zu verwenden. |
   | **[!UICONTROL Assets hinzufügen]** | Use the Asset Picker to select assets you want to invalidate. You can select either published or unpublished assets.<br>You may get a blank list when you add assets. Dynamische Medien verwenden die Vorlage &quot;Ungültiges CDN&quot;, um automatisch eine URL zu erstellen, um das CDN für ungültig zu erklären. Wenn keine Vorlage für &quot;Ungültiges CDN&quot;erstellt wurde, erhalten Sie eine leere Liste.<br>Die Zwischenspeicherung im CDN erfolgt URL-basiert und nicht Asset-basiert. Daher müssen Sie sich über die vollständigen URLs auf Ihrer Website im Klaren sein. Nachdem Sie diese URLs ermittelt haben, können Sie sie der Vorlage hinzufügen. Anschließend können Sie diese Elemente auswählen und hinzufügen und die URLs in einem Schritt ungültig machen. Die andere Option besteht darin, der Liste zur Ungültigmachung von CDN URLs hinzuzufügen. If you prefer this approach, it is not necessary to select and add assets before you tap **[!UICONTROL Next]** and then **[!UICONTROL Submit]** for invalidation.<br>Verwenden Sie diese Option in Verbindung mit **[!UICONTROL Ungültigmachen von Asset-zugeordneten Bildvorgaben im CDN]**, **[!UICONTROL Ungültigmachen auf der Grundlage einer Vorlage]** oder beidem. |
   | **[!UICONTROL URL hinzufügen]** | Fügen Sie Dynamischen Medien-Assets, deren CDN-Cache Sie ungültig machen möchten, manuell vollständige URL-Pfade hinzu oder fügen Sie sie ein. Verwenden Sie diese Option, wenn Sie in ***Teil 1 keine Vorlage für die Ungültigmachung eines CDN erstellt haben: Arbeiten mit der Vorlage*** für die Ungültigmachung von CDN und nur wenige Assets zum Ungültigmachen.<br> |

1. Near the upper-right corner of the page, tap **[!UICONTROL Next]**.
1. Auf der Seite &quot; **[!UICONTROL CDN-Ungültigmachung]** - **[!UICONTROL Bestätigen]** &quot;wird im Feld &quot;Liste der **[!UICONTROL URLs]** &quot;eine Liste einer oder mehrerer URLs angezeigt, die aus der zuvor erstellten Vorlage zur Ungültigmachung des CDN und den soeben hinzugefügten Assets generiert wurden.

   For example, with the CDN Invalidation Template previously created, suppose you added single asset named `spinset`. Wenn Sie auf **[!UICONTROL Extras > Assets > CDN-Ungültigmachung]** tippen, werden die folgenden fünf generierten URLs in der Benutzeroberfläche &quot; **[!UICONTROL CDN-Ungültigmachung - Bestätigen]** &quot;angezeigt:

   ![CDN-Ungültigerklärung - Bestätigen](/help/assets/assets-dm/cdn-invalidation-confirm-2.png)

   Falls erforderlich, tippen Sie auf das **X** rechts neben einer URL, um sie aus dem Ungültigkeitsprozess zu löschen. Sie können bis zu 1000 URLs gleichzeitig haben.

1. Tippen Sie in der rechten oberen Ecke der Seite auf **[!UICONTROL Senden]** , um den CDN-Ungültigkeitsprozess zu starten.

## Fehlerbehebung bei CDN-Ungültigkeitsfehlern

* Mit dieser Funktion können Sie bis zu 1000 URLs zu einem bestimmten Zeitpunkt für ungültig erklären. Eine Zahl über 1000 führt zu einem Fehler, den Sie durch Löschen von URLs auf der Seite &quot; **[!UICONTROL CDN-Ungültigmachung - Bestätigen]** &quot;beheben können.
* In allen Fällen wird entweder der gesamte Stapel zur Ungültigmachung verarbeitet oder der gesamte Stapel ist fehlgeschlagen.

| Fehler | Erklärung |
| --- | --- |
| *Failed to retrieve URL(s) for selected asset(s).* | Occurs if the any of the following scenarios are met:<br>– A Dynamic Media configuration is not found.<br>- Beim Abrufen eines Dienstbenutzers, über den die Konfiguration für dynamische Medien gelesen wird, gibt es eine Ausnahme.<br>- Der Veröffentlichungsserver bzw. der Firma-Stammordner, der zum Erstellen der URLs verwendet wird, fehlen in der Konfiguration für dynamische Medien. |
| *Some URLs are not defined correctly. Bitte korrigieren und erneut einreichen.* | Tritt auf, wenn die IPS CDN-Cache-Ungültigungs-API einen Fehler zurückgibt, dass die URL auf eine andere Firma verweist, oder wenn die URL gemäß der von der IPS cdnCacheInvalidation API durchgeführten Überprüfung ungültig ist. |
| *CDN-Cache konnte nicht ungültig gemacht werden.* | Tritt auf, wenn die Anforderung zum Ungültigmachen des CDN-Cache aus einem anderen Grund fehlschlägt. |
| *Keine URL(s) eingegeben, um ungültig zu werden.* | Tritt auf, wenn auf der Seite &quot; **[!UICONTROL CDN-Ungültigmachung - Bestätigen&quot;keine URLs vorhanden sind und Sie auf]** Senden **** tippen. |


<!--  | I do not want to create a template. | Near the upper-right corner of the page, tap **[!UICONTROL Cancel]**, then continue with ***Part 2: Working with CDN Invalidation***. Note that while you are not required to create a template to use CDN Invalidation, Adobe recommends that you create one, especially if you have numerous assets that you need to update immediately, on a regular basis. The template is used at the time you set CDN invalidation options. | -->