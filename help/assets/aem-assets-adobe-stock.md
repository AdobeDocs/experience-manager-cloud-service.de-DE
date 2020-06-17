---
title: Verwenden von digitalen Adobe Stock-Assets in AEM Assets
description: Sie können Adobe Stock-Assets in Experience Manager suchen, abrufen und verwalten. Behandeln Sie die lizenzierten Assets wie jedes andere Experience Manager-Asset.
contentOwner: AG
translation-type: tm+mt
source-git-commit: b0436c74389ad0b3892d1258d993c00aa470c3ab
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 97%

---


# Verwenden von Adobe Stock-Assets in AEM Assets {#use-adobe-stock-assets-in-aem-assets}

Organisationen können ihr Adobe Stock-Unternehmensabo in AEM Assets integrieren, damit lizenzierte Assets umfassend für kreative und Marketing-Projekte verfügbar sind und mit den leistungsstarken Asset-Management-Funktionen von AEM verwaltet werden können.

Der Adobe Stock-Service bietet Designern und Unternehmen Zugang zu Millionen von hochwertigen, kuratierten und gebührenfreien Fotos, Vektorgrafiken, Illustrationen, Videos, Vorlagen und 3D-Assets für sämtliche Kreativprojekte. AEM-Benutzer können Adobe Stock-Assets, die in AEM gespeichert sind, schnell finden, eine Vorschau anzeigen und die Lizenz abrufen, ohne ihren AEM-Arbeitsbereich zu verlassen.

## Integrieren von AEM und Adobe Stock {#integrate-aem-and-adobe-stock}

Um die Kommunikation zwischen AEM und Adobe Stock zu ermöglichen, erstellen Sie in AEM eine IMS- sowie eine Adobe Stock-Konfiguration.

>[!NOTE]
>
>Nur AEM- und Admin Console-Administratoren einer Organisation können die Integration durchführen, da hierfür Administratorrechte erforderlich sind.

### Erstellen einer IMS-Konfiguration   {#create-an-ims-configuration}

1. Klicken Sie auf das AEM-Logo. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Adobe IMS-Konfigurationen]**. Klicken Sie auf **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL Cloudlösung]** > **[!UICONTROL Adobe Stock]**.
1. Verwenden Sie entweder ein bestehendes Zertifikat oder wählen Sie **[!UICONTROL Neues Zertifikat erstellen]** aus.
1. Klicken Sie auf **[!UICONTROL Zertifikat erstellen]**. Laden Sie nach der Erstellung den öffentlichen Schlüssel herunter. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie die entsprechenden Werte in den Feldern **[!UICONTROL Titel]**, **[!UICONTROL Autorisierungsserver]**, **[!UICONTROL API-Schlüssel]**, **[!UICONTROL Geheimer Clientschlüssel]** und **[!UICONTROL Nutzlast]** ein. See [JWT authentication quick start](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWT.md), for detailed information to fetch these values from Adobe Developer Console.
1. Hinzufügen Sie den heruntergeladenen öffentlichen Schlüssel in Ihr Adobe Developer Console-Dienstkonto ein.

<!--
TBD: Update this instance when AIO updates their documentation publish URL.
-->

### Erstellen einer Adobe Stock-Konfiguration in AEM   {#create-adobe-stock-configuration-in-aem}

1. Navigieren Sie in der AEM-Benutzeroberfläche zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Stock]**.
1. Klicken Sie auf **[!UICONTROL Erstellen]**, um eine Konfiguration zu erstellen und sie Ihrer bestehenden IMS-Konfiguration zuzuordnen. Wählen Sie `PROD` als Umgebungsparameter aus.
1. Lassen Sie den Speicherort im Feld **[!UICONTROL Pfad lizenzierter Assets]** unverändert. Ändern Sie den Speicherort nicht in den Pfad, in dem Sie die Adobe Stock-Assets speichern möchten.
1. Schließen Sie die Erstellung ab, indem Sie alle erforderlichen Eigenschaften hinzufügen. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.
1. Fügen Sie AEM-Benutzer oder Gruppen hinzu, die die Assets lizenzieren können.

>[!NOTE]
>
>Wenn mehrere Adobe Stock-Konfigurationen vorhanden sind, wählen Sie die gewünschte Konfiguration im Bedienfeld [!UICONTROL Benutzereinstellungen] aus, indem Sie auf das AEM-Logo in der AEM-Benutzeroberfläche klicken.

## Verwenden und Verwalten von Adobe Stock-Assets in AEM {#usemanage}

Mit dieser Funktion können Organisationen ihren Benutzern die Arbeit mit Adobe Stock-Assets in AEM Assets ermöglichen. Benutzer können aus der AEM-Benutzeroberfläche heraus Adobe Stock-Assets suchen und die erforderlichen Assets lizenzieren.

Sobald ein Adobe Stock-Asset in AEM lizenziert ist, kann es wie ein typisches Asset verwendet und verwaltet werden. Benutzer können die Assets in AEM suchen und eine Vorschau zu diesen anzeigen, Assets kopieren und veröffentlichen, die Assets in Brand Portal teilen, die Assets per AEM-Desktop-Programm aufrufen und verwenden und vieles mehr.

<!--  ![Search for Adobe Stock assets and filter results from your AEM workspace](assets/adobe-stock-search-results-workspace.png)
*Figure: Search for Adobe Stock assets and filter results from your AEM workspace* -->

**A.** Nach Assets suchen, die denen ähneln, deren Adobe Stock-ID angegeben wurde. **B.** Nach Assets suchen, die Ihrer Form- und Ausrichtungswahl entsprechen. **C.** Einen oder mehrere unterstützte Asset-Typen suchen **D.** Filterbereich anzeigen oder ausblenden **E.** Ausgewähltes Asset in AEM lizenzieren und speichern **F.** Asset mit Wasserzeichen in AEM speichern **G.** Assets auf der Adobe Stock-Website suchen, die dem ausgewählten Asset ähneln **H.** Ausgewählte Assets auf der Adobe Stock-Website anzeigen **I.** Anzahl ausgewählter Assets aus den Suchergebnissen **J.** Zwischen Karten- und Listenansicht wechseln

### Suchen von Assets {#find-assets}

Ihre AEM-Benutzer können nach Assets in AEM und Adobe Stock suchen. Wenn die Suche nicht auf Adobe Stock beschränkt ist, werden Suchergebnisse aus AEM und Adobe Stock angezeigt.

* Um nach Adobe Stock-Assets zu suchen, klicken Sie auf **[!UICONTROL Navigation]** > **[!UICONTROL Assets]** > **[!UICONTROL Adobe Stock durchsuchen]**.

* Um in Adobe Stock und AEM Assets nach Assets zu suchen, klicken Sie auf das Suchsymbol ![Suchsymbol](assets/do-not-localize/search_icon.png).

Geben Sie alternativ `Location: Adobe Stock` in die Suchleiste ein, um Adobe Stock-Assets auszuwählen. AEM bietet erweiterte Filterfunktionen, mit denen Benutzer schnell die gewünschten Assets finden können. Hierzu stehen Filter, wie z. B. unterstützte Asset-Typen, Bildausrichtung und Lizenzstatus, zur Verfügung.

>[!NOTE]
>
>In Adobe Stock durchsuchte Assets werden in AEM nur angezeigt. Adobe Stock-Assets werden nur dann abgerufen und im AEM-Repository gespeichert, wenn Benutzer [Assets speichern](/help/assets/aem-assets-adobe-stock.md#saveassets) oder [Assets lizenzieren](/help/assets/aem-assets-adobe-stock.md#licenseassets). Assets, die bereits in AEM gespeichert sind, werden angezeigt und hervorgehoben, um einfachen Zugriff und schnelle Referenzierung zu ermöglichen. Außerdem werden solche Assets mit einigen zusätzlichen Metadaten gespeichert, um die Quelle als Adobe Stock anzugeben.

![Suchfilter in AEM und hervorgehobene Adobe Stock Assets in Suchergebnissen](assets/aem-search-filters2.jpg)*Abbildung: Suchfilter in AEM und hervorgehobene Adobe Stock-Assets in Suchergebnissen*

### Speichern und Anzeigen erforderlicher Assets {#saveassets}

Wählen Sie ein Asset aus, das Sie in AEM speichern möchten. Klicken Sie in der oberen Symbolleiste auf „Speichern“ und geben Sie den Namen und Speicherort des Assets an. Unlizenzierte Assets werden lokal mit Wasserzeichen gespeichert.

Wenn Sie erneut nach Assets suchen, werden die gespeicherten Assets durch ein Symbol hervorgehoben, um anzuzeigen, dass diese Assets in AEM Assets verfügbar sind.

>[!NOTE]
>
>Bei den kürzlich hinzugefügten Assets wird das Symbol „Neu“ anstelle des Symbols „Lizenziert“ angezeigt.

### Lizenzieren von Assets {#licenseassets}

Benutzer können Adobe Stock-Assets lizenzieren, indem sie das Kontingent ihres Adobe Stock-Unternehmensabos nutzen. Wenn Sie ein Asset lizenzieren, wird es ohne Wasserzeichen gespeichert und ist in der Suche sowie für die Verwendung in AEM Assets verfügbar.

![Dialogfeld zum Lizenzieren und Speichern von Adobe Stock-Assets in AEM Assets](assets/aem-stock_licenseandsave.jpg)*Abbildung: Dialogfeld zum Lizenzieren und Speichern von Adobe Stock-Assets in AEM Assets*

### Anzeigen von Metadaten und Asset-Eigenschaften {#access-metadata-and-asset-properties}

Benutzer können Metadaten, einschließlich der Adobe Stock-Metadateneigenschaften für Assets, die in AEM gespeichert wurden, öffnen bzw. eine Vorschau dieser Daten anzeigen und **[!UICONTROL Lizenzreferenzen]** für Assets hinzufügen. Die Änderungen an der Lizenzreferenz werden jedoch nicht zwischen AEM und der Adobe Stock-Website synchronisiert.

Benutzer können die Eigenschaften für lizenzierte und unlizenzierte Assets anzeigen.

![Anzeigen von und Zugreifen auf Metadaten und Lizenzverweise zu gespeicherten Assets](assets/metadata_properties.jpg)*Abbildung: Anzeigen von und Zugreifen auf Metadaten und Lizenzverweise gespeicherter Assets*

## Bekannte Einschränkungen {#known-limitations}

### Fehlende Warnung zu redaktionellen Bildern

Bei der Lizenzierung eines Bildes können Benutzer nicht überprüfen, ob das Bild nur zur redaktionellen Verwendung bestimmt ist. Um zu verhindern, dass Bilder falsch verwendet werden, können Administratoren den Zugriff auf redaktionelle Assets über die Admin Console deaktivieren.

### Anzeige des falschen Lizenztyps

Es ist möglich, dass in AEM ein falscher Lizenztyp für Assets angezeigt wird. Benutzer können sich bei der Adobe Stock-Website anmelden, um den richtigen Lizenztyp zu ermitteln.

### Fehlende Synchronisation von Feldern und Metadaten

Wenn ein Benutzer ein Lizenzreferenzfeld bearbeitet, werden die Lizenzreferenz-Informationen in AEM, aber nicht auf der Adobe Stock-Website aktualisiert. Ebenso werden Änderungen, die Benutzer an den Referenzfeldern auf der Adobe Stock-Website vornehmen, nicht mit AEM synchronisiert.

## Verwandte Ressourcen {#related-resources}

[Video-Tutorial zur Verwendung von Adobe Stock-Assets mit AEM Assets](https://helpx.adobe.com/de/experience-manager/kt/assets/using/stock-assets-feature-video-use.html)

[Hilfe zum Adobe Stock-Unternehmensplan](https://helpx.adobe.com/de/enterprise/using/adobe-stock-enterprise.html)

[Häufig gestellte Fragen zu Adobe Stock](https://helpx.adobe.com/de/stock/faq.html)
