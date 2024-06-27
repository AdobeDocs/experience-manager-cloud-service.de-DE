---
title: Asset-Eigenschaften in [!DNL the Content Hub]
description: Erfahren Sie, wie Sie Asset-Eigenschaften in anzeigen und verwalten [!DNL Content Hub]
role: User
source-git-commit: e590c34c177e6b45b6a52370caa88da54b61ebc0
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 12%

---


# Verwalten von Asset-Eigenschaften in Content Hub {#asset-properties}

![Metadaten-Bannerbild](assets/metadata-banner-image.png)

[!DNL The Content Hub] können Sie Informationen zum Asset anzeigen, das für eine effiziente Asset-Verteilung von entscheidender Bedeutung ist. Es handelt sich um die Sammlung aller für ein Asset verfügbaren Daten.

Die Anzeige von Asset-Eigenschaften hilft Ihnen bei der weiteren Kategorisierung von Assets und ist bei zunehmender Menge digitaler Informationen hilfreich. Es ist möglich, einige Hundert Dateien zu verwalten, die nur auf den Dateinamen, den Miniaturbildern und dem Speicherbedarf basieren. Dieser Ansatz ist jedoch nicht skalierbar, wenn die Anzahl der beteiligten Personen und die Anzahl der verwalteten Assets steigt. Darüber hinaus wächst der Wert eines digitalen Assets, sobald das Asset wie folgt aussieht:

* besser zugänglich – Systeme und Benutzer können es leicht finden.
* Einfachere Verwaltung - Sie können Assets mit denselben Eigenschaften einfach finden und Änderungen darauf anwenden.
* Abgeschlossen - Asset enthält mehr Informationen und Kontext.

## Eigenschaften eines Assets anzeigen {#properties-ui}

Bevor Sie ein Asset verwenden, freigeben oder herunterladen, können Sie es sich genauer ansehen. Mit der Vorschaufunktion können Sie nicht nur die Bilder, sondern auch einige andere unterstützte Asset-Typen anzeigen. Sie können nicht nur das Asset anzeigen, sondern auch seine detaillierten Informationen anzeigen und andere Aktionen durchführen. Um Informationen zu einem Asset anzuzeigen, navigieren Sie zum Asset oder [suchen](search-assets.md) und klicken Sie dann auf das Asset, um seine Eigenschaften zu öffnen. Die folgende Abbildung zeigt die Felder, die auf einer Asset-Eigenschaftsseite verfügbar sind:

![Eigenschaften einer Asset-Benutzeroberfläche](assets/properties-ui.png)

* **A:** Titel eines Assets
* **B:** Prozentsatz des Zoom- oder Vorschau-Assets durch Vergrößern oder Verkleinern
* **C:** Zoom auf den zuvor ausgewählten Prozentsatz rückgängig machen
* **D:** Zum vorherigen oder nächsten Asset wechseln
* **E:** Anzahl der Assets
* **F:** Asset herunterladen
* **G:** Bearbeiten von Assets mit [!DNL Adobe Express]
* **H:** Reduzieren oder Anzeigen einer Vorschau von Asset-Informationen
* **I:** Asset freigeben
* **J:** Asset hinzufügen zu [!DNL Collection]
* **K:** Vorschaufenster schließen
* **L:** Informationen zu einem Asset, das Titel, Format, Größe, Auflösung, Tags, Farb-Tags und Smart-Tags enthält.

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
      <td>Video </td>
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
            <li>[!UICONTROL Text] (Nur verfügbar)</li>  
            <li>[!UICONTROL Doc/Docx]</li> 
            <li>[!UICONTROL XML]</li>
        </ul>
      </td>
     </tr>
     <tr>
      <td>Druckmedien</td>
      <td>
        <ul>
            <li>[!UICONTROL PDF]</li>  
        </ul>
      </td>
     </tr>  
    </tbody>
   </table>

### Abgeleitete Eigenschaften nach dem Hochladen eines Assets {#derived-properties}

Nachdem Sie ein Asset hochgeladen haben, leitet der Content Hub einige automatisch generierte Eigenschaften ab. Im Folgenden finden Sie eine Liste einiger dieser Themen:

* **Größe:** Die Größe zeigt den logischen Wert eines Assets entsprechend seinen Dimensionen. Dadurch wird der Speicherplatz klargestellt, den ein Asset in einem Repository belegt. [!DNL The Content Hub] unterstützt Assets mit einer Größe von bis zu 2 GB.

<!--* **Tags:** Tags help you categorize assets that can be browsed and searched more efficiently. Tagging helps in propagating the appropriate taxonomy to other users and workflows. -->

* **Smart-Tags:** [!DNL The Content Hub] verwendet die Smart Content Services von Adobe Sensei zum Trainieren von Assets mithilfe des Erkennungsalgorithmus für die tags-basierte Struktur. Diese Content-Intelligenz wird dann verwendet, um relevante Tags auf einen anderen Satz von Assets anzuwenden. Smart-Tags steigern die Content-Geschwindigkeit Ihrer Projekte, indem sie Ihnen dabei helfen, relevante Assets schnell zu finden. Die Smart-Tags sind ein Beispiel für Asset-Informationen, die nicht im Bild enthalten sind. [!DNL The Content Hub] wendet standardmäßig Smart-Tags auf Assets automatisch an.

* **Farbtags:** [Farbtags](#https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/color-tag-images.html?lang=en) helfen Ihnen dabei, ein Asset mithilfe von Farben zu erkennen, die in einem Asset mithilfe der AI-Funktionen von Adobe Sensei automatisch identifiziert werden.

* Upload-Datum

* Hochgeladen von

* Zuletzt geändert

* Zuletzt geändert von

Es gibt auch Eigenschaften, die beim Hinzufügen von Assets zu Content Hub angegeben werden. Weitere Informationen finden Sie unter [Hinzufügen von markengenehmigten Assets zu Content Hub](upload-brand-approved-assets.md). Diese Eigenschaften werden auch auf der Seite mit den Asset-Eigenschaften angezeigt.

Administratoren können auch die Eigenschaften konfigurieren, die für jedes Asset angezeigt werden. Weitere Informationen finden Sie unter [Benutzeroberfläche von Content Hub konfigurieren](configure-content-hub-ui-options.md#configure-asset-details-content-hub).

<!--

### Date range {#date-range} 

The date range allows you to select dates you want to see the assets. You can customize date range by choosing the start and end dates. 

-->

