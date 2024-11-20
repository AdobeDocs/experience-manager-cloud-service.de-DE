---
title: Asset-Eigenschaften in [!DNL the Content Hub]
description: Erfahren Sie, wie Sie Asset-Eigenschaften in [!DNL Content Hub] anzeigen und verwalten.
role: User
exl-id: a85af980-4c51-4d30-9fad-afd16370e9db
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 95%

---

# Verwalten von Asset-Eigenschaften in Content Hub {#asset-properties}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

![Metadaten-Bannerbild](assets/metadata-banner-image.png)

>[!AVAILABILITY]
>
>Das Content Hub-Handbuch ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den Adobe Acrobat AI-Assistenten, um Ihre Fragen zu beantworten.
>
>[!BADGE Content Hub Guide PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

[!DNL The Content Hub] ermöglicht Ihnen das Anzeigen von Informationen über das Asset, was für eine effiziente Asset-Verteilung von entscheidender Bedeutung ist. Es handelt sich um die Sammlung aller für ein Asset verfügbaren Daten.

Durch die Anzeige der Asset-Eigenschaften können Sie Assets genauer einteilen. Außerdem erweist es sich als nützlich, wenn die Menge digitaler Daten ansteigt. Es ist möglich, mehrere Hundert Dateien zu verwalten, basierend nur auf den Dateinamen, den Miniaturbildern und dem Speicherbedarf. Dieser Ansatz ist jedoch nicht skalierbar, wenn die Zahl der beteiligten Personen und die Zahl der verwalteten Assets steigt. Darüber hinaus steigt der Wert eines digitalen Assets, da sich das Asset in den folgenden Punkten verbessert:

* besser zugänglich – Systeme und Benutzende können es leicht finden.
* einfacher zu verwalten – Sie können Assets mit denselben Eigenschaften einfacher finden und Änderungen auf sie anwenden.
* vollständig – das Asset enthält mehr Informationen und Kontext.

## Voraussetzungen {#prerequisites}

[Content Hub-Benutzende](deploy-content-hub.md#onboard-content-hub-users) können die in diesem Artikel genannten Aktionen ausführen.

## Anzeigen der Eigenschaften eines Assets {#properties-ui}

Bevor Sie ein Asset verwenden, freigeben oder herunterladen, können Sie es sich genauer ansehen. Mit der Vorschaufunktion können Sie nicht nur die Bilder, sondern auch einige andere unterstützte Asset-Typen anzeigen. Sie können nicht nur das Asset, sondern auch seine detaillierten Informationen anzeigen und andere Aktionen durchführen. Um Informationen zu einem Asset anzuzeigen, navigieren Sie zum Asset oder [suchen](search-assets.md) Sie nach dem Asset und klicken Sie dann darauf, um seine Eigenschaften zu öffnen. Die folgende Abbildung zeigt die Felder, die auf einer Seite mit Asset-Eigenschaften verfügbar sind:

![Eigenschaften einer Asset-Benutzeroberfläche](assets/properties-ui.png)

* **A:** Titel eines Assets
* **B:** Zoom-Prozentsatz eingeben oder die Asset-Vorschau zur genaueren Ansicht vergrößern bzw. verkleinern
* **C:** Den Zoom auf den zuvor ausgewählten Prozentsatz zurücksetzen
* **D:** Zum vorherigen oder nächsten Asset wechseln
* **E:** Assets zählen
* **F:** Das Asset herunterladen
* **G:** Asset mit [!DNL Adobe Express] bearbeiten
* **H:** Informationen für ein Asset ausblenden oder in der Vorschau anzeigen
* **I:** Das Asset freigeben
* **J:** Asset zu [!DNL Collection] hinzufügen
* **K:** Vorschaufenster schließen
* **L:** Informationen zu einem Asset, einschließlich Titel, Format, Größe, Auflösung, Tags, Farb-Tags und Smart-Tags.

## Unterstützte Formate {#supported-formats}

Die folgende Tabelle zeigt die unterstützten Dateiformate in [!DNL the Content Hub]:

<table> 
    <tbody>
     <tr>
      <th><strong>Dateityp</strong></th>
      <th><strong>Unterstützte Formate</strong></th>
     </tr>
     <tr>
      <td>Bild</td>
      <td>
        <ul>
            <li>[!UICONTROL JPEG]</li> 
            <li>[!UICONTROL PNG]</li> 
            <li>[!UICONTROL SVG]</li>
        </ul>
      </td>
     </tr>
     <tr>
      <td>Video</td>
      <td>
        <ul>
            <li>[!UICONTROL Quicktime]</li>  
            <li>[!UICONTROL MP4]</li> 
        </ul>
      </td>
     </tr>
      <tr>
      <td>Dokument</td>
      <td>
        <ul>
            <li>[!UICONTROL txt] (Einfach)</li>  
            <li>[!UICONTROL Doc/Docx]</li> 
            <li>[!UICONTROL XML]</li>
        </ul>
      </td>
     </tr>
     <tr>
      <td>Print-Medien</td>
      <td>
        <ul>
            <li>[!UICONTROL PDF]</li>  
        </ul>
      </td>
     </tr>  
    </tbody>
   </table>

### Abgeleitete Eigenschaften nach dem Hochladen eines Assets {#derived-properties}

Nachdem Sie ein Asset hochgeladen haben, leitet der Content Hub einige automatisch generierte Eigenschaften ab. Im Folgenden finden Sie eine Liste solcher Eigenschaften:

* **Größe:** Die Größe gibt den logischen Wert eines Assets gemäß seinen Dimensionen an. Dadurch wird klargestellt, wie viel Speicherplatz ein Asset in einem Repository belegt. [!DNL The Content Hub] unterstützt Assets mit einer Größe von bis zu 2 GB.

<!--* **Tags:** Tags help you categorize assets that can be browsed and searched more efficiently. Tagging helps in propagating the appropriate taxonomy to other users and workflows. -->

* **Smart-Tags:** [!DNL The Content Hub] verwendet die Smart Content-Dienste von Adobe Sensei, um Assets mithilfe des Erkennungsalgorithmus für die Tags-basierte Struktur zu trainieren. Diese Content-Intelligenz wird dann verwendet, um relevante Tags auf einen anderen Satz von Assets anzuwenden. Smart-Tags erhöhen die Inhaltsgeschwindigkeit Ihrer Projekte, da Sie relevante Assets schnell finden können. Die Smart-Tags sind ein Beispiel für Asset-Informationen, die nicht im Bild enthalten sind. [!DNL The Content Hub] wendet standardmäßig automatisch Smart-Tags auf Assets an.

* **Farb-Tags:** [Farb-Tags](#https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/color-tag-images.html?lang=en) helfen Ihnen dabei, ein Asset anhand von Farben zu erkennen, die mithilfe der KI-Funktionen von Adobe Sensei automatisch in einem Asset identifiziert werden.

* Upload-Datum

* Hochgeladen von

* Zuletzt geändert

* Zuletzt geändert von

Es gibt auch Eigenschaften, die beim Hinzufügen von Assets zu Content Hub angegeben werden. Weitere Informationen finden Sie unter [Hinzufügen markenkonformer Assets zu Content Hub](upload-brand-approved-assets.md). Diese Eigenschaften werden ebenfalls auf der Seite mit den Asset-Eigenschaften angezeigt.

Admins können auch die Eigenschaften konfigurieren, die für jedes Asset angezeigt werden. Weitere Informationen finden Sie unter [Konfigurieren der Benutzeroberfläche von Content Hub](configure-content-hub-ui-options.md#configure-asset-details-content-hub).

<!--

### Date range {#date-range} 

The date range allows you to select dates you want to see the assets. You can customize date range by choosing the start and end dates. 

-->
