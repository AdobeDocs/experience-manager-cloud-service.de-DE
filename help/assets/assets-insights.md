---
title: Asset Insights
description: Erfahren Sie, wie Sie mit der Funktion „Asset Insights“ Benutzerbewertungen und Nutzungsstatistiken von Bildern nachverfolgen können, die auf Drittanbieter-Websites, in Marketingkampagnen und den Kreativlösungen von Adobe verwendet werden.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 100%

---


# Asset Insights {#asset-insights}

Mit der Funktion „Asset Insights“ verfolgen Sie Benutzerbewertungen und Nutzungsstatistiken von Bildern, die auf Drittanbieter-Websites, in Marketing-Kampagnen und den Kreativlösungen von Adobe verwendet werden. Sie bietet Einblicke in die Leistung und Beliebtheit der Bilder.

Assets Insights hält Details zu Benutzeraktivitäten wie Anzahl der Bildbewertungen, Klickraten und Impressionen (Häufigkeit des Ladens eines Bildes auf einer Website) fest. Basierend auf diesen Statistiken werden Bildern Bewertungen zugewiesen. Sie können Bewertungs- und Leistungsstatistiken nutzen, um beliebte Bilder für Kataloge, Marketing-Kampagnen usw. auszuwählen. Sie können außerdem Richtlinien zu Archivierungen und Lizenzerneuerungen anhand dieser Statistiken formulieren.

Damit Assets Insights Nutzungsstatistiken für Bilder von einer Website festhalten kann, müssen Sie den eingebetteten Code für das Bild im Website-Code einfügen.

Damit Asset Insights Nutzungsstatistiken für Assets anzeigen kann, konfigurieren Sie zunächst die Funktion für den Abruf von Berichtsdaten aus Adobe Analytics. Weitere Details finden Sie unter [Asset Insights konfigurieren](#configure-asset-insights).

>[!NOTE]
>
>Einblicke werden nur für Bilder unterstützt und bereitgestellt.

## Anzeigen von Statistiken für Bilder {#viewing-statistics-for-an-image}

Sie können die Asset Insights-Bewertungen über die Metadatenseite anzeigen.

1. Wählen Sie auf der Assets-Benutzeroberfläche das Bild aus und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Eigenschaften]**.
1. Tippen Sie auf der Seite „Eigenschaften“ auf **[!UICONTROL Insights]**.
1. Überprüfen Sie die Nutzungsdetails für das Asset auf der Registerkarte **[!UICONTROL Insights]**. Der Abschnitt **[!UICONTROL Bewertung]** beschreibt die gesamte Asset-Nutzung und die Leistungsbewertungen eines Assets.

   Die Nutzungsbewertung beschreibt, wie oft ein Asset in verschiedenen Lösungen verwendet wird.

   Die Bewertung **[!UICONTROL Impressionen]** beschreibt, wie oft das Asset auf der Website geladen wurde. Die unter **[!UICONTROL Klicks]** angezeigte Zahl beschreibt, wie oft Benutzer auf das Asset geklickt haben.

1. Im Abschnitt **[!UICONTROL Nutzungsstatistiken]** können Sie ermitteln, in welchen Elementen das Asset enthalten war und in welchen Kreativlösungen es vor Kurzem verwendet wurde. Je höher die Nutzung, desto größer ist die Wahrscheinlichkeit, dass das Asset bei Benutzern beliebt ist. Nutzungsdaten werden unter den folgenden Überschriften angezeigt:

   * **[!UICONTROL Asset]**: Wie oft war das Asset Teil einer Sammlung oder eines zusammengesetzten Assets.
   * **[!UICONTROL Web und Mobile]**: Wie oft wurde das Asset in Websites und Apps verwendet.
   * **[!UICONTROL Social]**: Wie oft wurde das Asset in Lösungen wie Adobe Social und Adobe Campaign verwendet.
   * **[!UICONTROL E-Mail]**: Wie oft wurde das Asset in E-Mail-Kampagnen verwendet.
   ![Nutzungsstatistiken](assets/usage_statistics.png)

   >[!NOTE]
   >
   >Da die Asset Insights-Funktion normalerweise in bestimmten Abständen die Lösungsdaten aus Adobe Analytics abruft, werden im Abschnitt „Lösungen“ möglicherweise nicht die neuesten Daten angezeigt. Der Zeitraum, für den die Daten angezeigt werden, hängt vom Zeitplan des Abholvorgangs ab, mit dem Asset Insights ausgeführt wird, um Daten aus Analytics abzurufen.

1. Um Leistungsstatistiken für das Asset für einen bestimmten Zeitraum grafisch anzuzeigen, wählen Sie den gewünschten Zeitraum im Abschnitt **[!UICONTROL Leistungsstatistiken]** aus. Details wie Klicks und Impressions werden als Trend-Linien eines Diagramms angezeigt.

   ![chlimage_1-3](assets/chlimage_1-3.jpeg)

   >[!NOTE]
   >
   >Im Gegensatz zu den Daten im Abschnitt „Lösungen“ zeigt der Abschnitt „Leistungsstatistiken“ die neuesten Daten an.

1. Um den Einbettungs-Code für das Asset zu erhalten, das Sie zu Websites hinzufügen, um Leistungsdaten zu gewinnen, tippen oder klicken Sie unter der Asset-Miniaturansicht auf **[!UICONTROL Einbettungs-Code abrufen]**. <!-- For more information on how to include your Embed code in third-party web pages, see [Using Page Tracker and Embed code in web pages](/help/assets/use-page-tracker.md). -->

   ![chlimage_1-98](assets/chlimage_1-98.png)

## Anzeigen von zusammengefassten Statistiken für Bilder {#viewing-aggregate-statistics-for-images}

Mit der **[!UICONTROL Insights-Ansicht]** können Sie Bewertungen aller Assets in einem Ordner gleichzeitig anzeigen.

1. Navigieren Sie in der Assets-Benutzeroberfläche zum Ordner, in dem die Assets enthalten sind, für die Sie Statistiken anzeigen möchten.
1. Tippen oder klicken Sie auf das Layout-Symbol und wählen Sie **[!UICONTROL Insight-Ansicht]** aus.
1. Die Seite zeigt die Nutzungsbewertungen für die Assets an. Vergleichen Sie die Bewertungen der verschiedenen Assets und ziehen Sie Ihre Erkenntnisse daraus.

## Planen von Hintergrundaufträgen {#scheduling-background-job}

Asset Insights ruft regelmäßig Nutzungsdaten für Assets aus den Adobe Analytics-Report Suites ab. Standardmäßig führt Asset Insights alle 24 Stunden um 2 Uhr Hintergrundjobs aus, um Daten abzurufen. Sie können jedoch die Häufigkeit und die Zeit ändern, indem Sie den Dienst **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]** von der Web-Konsole aus konfigurieren.

1. Tippen Sie auf das AEM-Logo und navigieren Sie anschließend zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Öffnen Sie die Service-Konfiguration **[!UICONTROL Adobe CQ DAM Asset Performance Report Sync Job]**.

   ![chlimage_1-99](assets/chlimage_1-99.png)

1. Geben Sie die gewünschte Terminplaner-Häufigkeit und Startzeit für den Auftrag im Eigenschaftsplanerausdruck ein. Speichern Sie die Änderungen.

## Konfigurieren von Asset Insights {#configure-asset-insights}

Adobe Experience Manager (AEM) Assets ruft Nutzungsdaten rund um AEM-Assets von Websites von Drittanbietern aus Adobe Analytics ab. Um Asset Insights zu aktivieren und diese Daten abzurufen und Statistiken zu erzeugen, konfigurieren Sie zuerst die Funktion zur Integration mit Adobe Analytics.

>[!NOTE]
>
>Einblicke werden nur für Bilder unterstützt und bereitgestellt.

1. Klicken Sie in AEM auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-72](assets/chlimage_1-72.png)

1. Klicken Sie auf die Karte **[!UICONTROL Insights-Konfiguration]**.
1. Wählen Sie im Assistenten ein Rechenzentrum aus und geben Sie Ihre Anmeldedaten an, z. B. den Namen Ihres Unternehmens, den Benutzernamen und gemeinsamen geheimen Schlüssel.

   ![Konfigurieren von Adobe Analytics für Asset Insights in AEM](assets/insights_config2.png)

   *Abbildung: Konfigurieren von Adobe Analytics für Asset Insights in AEM*

1. Klicken/tippen Sie auf **[!UICONTROL Authentifizieren]**. Nachdem AEM Ihre Anmeldedaten authentifiziert hat, wählen Sie aus der Liste **[!UICONTROL Report Suite]** eine Adobe Analytics Report Suite aus, aus der Asset Insights Daten abrufen soll. Klicken Sie auf **[!UICONTROL Hinzufügen]**.
1. Nach der Report Suite-Einrichtung durch AEM tippen Sie auf **[!UICONTROL Fertig]**.

### Seitenverfolgung {#page-tracker}

Nachdem Sie Ihr Adobe Analytics-Konto konfiguriert haben, wird der Seitenverfolgungs-Code für Sie erzeugt. Um Asset Insights zur Verfolgung von AEM-Assets in Websites von Drittanbietern zu aktivieren, beziehen Sie den Seitenverfolgungscode in den Website-Code ein. Verwenden Sie das Seitenverfolgungs-Dienstprogramm in AEM Assets, um den Seitenverfolgungscode zu erzeugen. <!--  For more information on how to include your Page Tracker code in third-party web pages, see [Using Page Tracker and Embed code in web pages](/help/assets/use-page-tracker.md). -->

1. Klicken Sie in AEM auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]**.

   ![chlimage_1-73](assets/chlimage_1-73.png)

1. Klicken Sie in der **[!UICONTROL Navigationsseite]** auf die Karte **[!UICONTROL Insights-Seitenverfolgung]**.
1. Klicken Sie auf **[!UICONTROL Herunterladen]**, um den Seitenverfolgungs-Code herunterzuladen.

<!--

## Using demo package for Asset Insights {#using-demo-package-for-asset-insights}

Using the demo package, you can enable Adobe Asset Insights to capture data from and generate insights for a sample web page.

1. Configure Asset Insights using the instructions in [Configure Asset Insights](#configure-asset-insights).
1. Download the sample AEM Assets package from below and install the package from CRXDE package manager.

   [Get File](assets/insightsdemo.zip)

1. Download the ZIP file containing the sample web page from below and extract on your local file system.

   [Get File](assets/demosite.zip)

1. Click the web page to open it in the web browser.

   >[!CAUTION]
   >
   >Web Page is configured to load asset from the localhost server . In case your server is running somewhere else change server address from localhost to server address in the HTML content of the web page.

   >[!NOTE]
   >
   >The external web page can be in AEM itself.

-->
