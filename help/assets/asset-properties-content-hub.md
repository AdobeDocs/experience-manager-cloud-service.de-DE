---
title: Vorschau von Assets und ihrer Eigenschaften in  [!DNL the Content Hub]
description: Erfahren Sie, wie Sie in  [!DNL Content Hub] Assets und Eigenschaften in einer Vorschau anzeigen.
role: User
exl-id: a85af980-4c51-4d30-9fad-afd16370e9db
source-git-commit: 45e731d2286b07db5852138ae1ac914a56b13a6a
workflow-type: ht
source-wordcount: '636'
ht-degree: 100%

---

# Vorschau von Assets und ihrer Eigenschaften in Content Hub {#asset-properties}

![Metadaten-Bannerbild](assets/metadata-banner-image.png)

[!DNL The Content Hub] ermöglicht Ihnen das Anzeigen von Informationen über das Asset, was für eine effiziente Asset-Verteilung von entscheidender Bedeutung ist. Es handelt sich um die Sammlung aller für ein Asset verfügbaren Daten.

Durch die Anzeige von Assets und ihrer Eigenschaften in einer Vorschau können Sie Assets genauer einteilen. Außerdem erweist sich dies als nützlich, wenn die Menge digitaler Daten ansteigt. Es ist möglich, mehrere Hundert Dateien zu verwalten, basierend nur auf den Dateinamen, den Miniaturbildern und dem Speicherbedarf. Dieser Ansatz ist jedoch nicht skalierbar, wenn die Zahl der beteiligten Personen und die Zahl der verwalteten Assets steigt. Darüber hinaus steigt der Wert eines digitalen Assets, da sich das Asset in den folgenden Punkten verbessert:

* besser zugänglich – Systeme und Benutzende können es leicht finden.
* einfacheres Handeln – Sie verfügen über umfassende Informationen zu den Visualisierungen von Assets und den zugehörigen Informationen und können so schneller und sicherer mit ihnen verfahren.
* vollständig – das Asset enthält mehr Informationen und Kontext.

## Voraussetzungen {#prerequisites}

[Content Hub-Benutzende](deploy-content-hub.md#onboard-content-hub-users) können die in diesem Artikel genannten Aktionen ausführen.

## Anzeigen von Assets und ihrer Eigenschaften in einer Vorschau {#properties-ui}

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

## Unterstützte Dateiformate {#supported-formats}

[!DNL Content Hub] unterstützt alle Asset-Typen und -Formate, die das zugrunde liegende [!DNL Assets]-Repository unterstützt. In der folgenden Tabelle sind die wichtigsten Dateiformate in [!DNL the Content Hub] aufgeführt, die zusätzliche Unterstützung für eine visuelle Asset-Vorschau bieten:

<table> 
    <tbody>
     <tr>
      <th><strong>Dateityp</strong></th>
      <th><strong>Unterstützte Formate</strong></th>
     </tr>
     <tr>
        <td rowspan="3"> Bild </td>
    </tr>
    </tr>
    <tr>
        <td>[!UICONTROL JPEG]</td>
    </tr>
    <tr>
        <td>[!UICONTROL PNG]</td>
    </tr>
    <tr>
        <td rowspan="4"> Video </td>
    </tr>
    </tr>
    <tr>
        <td>[!UICONTROL Quicktime]</td>
    </tr>
    <tr>
        <td>[!UICONTROL MP4]</td>
    </tr>
    <tr>
        <td>[!UICONTROL MPEG]</td>
    </tr>
    <tr>
        <td rowspan="4"> Dokument </td>
    </tr>
    </tr>
    <tr>
        <td>[!UICONTROL txt] (Einfach)</td>
    </tr>
    <tr>
        <td>[!UICONTROL Doc/Docx]</td>
    </tr>
    <tr>
        <td>[!UICONTROL XML]</td>
    </tr>
    <tr>
        <td rowspan="2"> Print-Medien </td>
    </tr>
    </tr>
    <tr>
        <td>[!UICONTROL PDF]</td>
    </tr>
    </tbody>
</table>

### Abgeleitete Eigenschaften {#derived-properties}

Einige Asset-Eigenschaften, die in [!DNL Content Hub] angezeigt werden, werden abgeleitet oder automatisch generiert, wenn Assets in [!DNL Assets] hochgeladen und dann zur Nutzung in [!DNL Content Hub] genehmigt werden. Im Folgenden finden Sie eine Liste einiger dieser Eigenschaften:

* **Größe:** Die Größe entspricht der Größe der im zugrunde liegenden Repository gespeicherten Asset-Binärdatei.

<!--* **Tags:** Tags help you categorize assets that can be browsed and searched more efficiently. Tagging helps in propagating the appropriate taxonomy to other users and workflows. -->

* **Smart-Tags:** [!DNL The Content Hub] verwendet die Smart Content-Dienste von Adobe Sensei, um Assets mithilfe des Erkennungsalgorithmus für die Tags-basierte Struktur zu trainieren. Diese Content-Intelligenz wird dann verwendet, um relevante Tags auf einen anderen Satz von Assets anzuwenden. Smart-Tags erhöhen die Inhaltsgeschwindigkeit Ihrer Projekte, da Sie relevante Assets schnell finden können. Die Smart-Tags sind ein Beispiel für Asset-Informationen, die nicht im Bild enthalten sind. [!DNL Experience Manager Assets] wendet standardmäßig automatisch Smart-Tags auf Assets an.

* **Farb-Tags:** [Farb-Tags](#https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/color-tag-images.html?lang=en) helfen Ihnen dabei, ein Asset anhand von Farben zu erkennen, die mithilfe der KI-Funktionen von Adobe Sensei automatisch in einem Asset identifiziert werden.

* Upload-Datum

* Hochgeladen von

* Zuletzt geändert

* Zuletzt geändert von

Es gibt auch Eigenschaften, die beim Hinzufügen von Assets zu Content Hub angegeben werden. Weitere Informationen finden Sie unter [Hinzufügen markenkonformer Assets zu Content Hub](upload-brand-approved-assets.md). Diese Eigenschaften werden ebenfalls auf der Seite mit den Asset-Eigenschaften angezeigt.

Admins können auch die Eigenschaften konfigurieren, die für jedes Asset angezeigt werden:

* in der Benutzeroberfläche für die Asset-Vorschau (siehe [Konfigurieren der Benutzeroberfläche von Content Hub](configure-content-hub-ui-options.md#configure-asset-details-content-hub))
* auf Asset-Karten in Suchergebnissen oder Sammlungen (siehe [Konfigurieren der Benutzeroberfläche von Content Hub](configure-content-hub-ui-options.md#asset-card))

<!--

### Date range {#date-range} 

The date range allows you to select dates you want to see the assets. You can customize date range by choosing the start and end dates. 

-->
