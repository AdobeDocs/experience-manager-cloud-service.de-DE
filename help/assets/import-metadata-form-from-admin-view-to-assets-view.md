---
title: Importieren von Metadatenformularen aus [!DNL Admin View] nach [!DNL Assets View]
description: In diesem Artikel wird beschrieben, wie Sie das Metadatenformular von nach  [!DNL Admin View]  [!DNL Assets View]
contentOwner: AG
feature: Metadata
role: User, Admin
exl-id: 5fb4fe97-486a-4a91-af60-a7182efcc2f9
source-git-commit: fdd74e4d9b74600fd462e951046abfb1bb8e203b
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 8%

---

# Importieren von Metadatenformularen aus [!DNL Admin View] nach [!DNL Assets View] {#import-metadata-forms-from-admin-view-to-assets-view}

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

Mit [!DNL Adobe Experience Manager Assets] können Sie Metadatenformulare und ihre Ordnerzuordnungen aus [!DNL Admin View] in [!DNL Assets View] importieren.

## Bevor Sie beginnen{#prerequisites-for-importing-metadata-forms-to-assets-view}

Stellen Sie sicher, dass Sie über Administratorrechte verfügen, um die Metadatenformulare und ihre Ordnerzuordnungen aus [!DNL Admin View] in [!DNL Assets View] zu importieren.

## Importieren von Metadatenformularen in [!DNL Assets View]{#import-metadata-forms-to-assets-view}

Führen Sie als Administrator die folgenden Schritte aus, um die in [!DNL Admin View] verfügbaren Metadatenformulare in [!DNL Assets View] zu importieren:

1. Forms Navigieren Sie zur [!DNL Assets View]-Startseite und klicken Sie auf **[!UICONTROL Metadaten-]** unter **[!UICONTROL Einstellungen]**, um die Seite **[!UICONTROL Metadaten-Forms]** mit der Liste der in [!DNL Assets View] verfügbaren Metadatenformulare anzuzeigen.

   ![Metadatenformularseite](/help/assets/assets/metadata-forms-page.png)

1. Wählen Sie **[!UICONTROL Importieren]**, wird eine Verarbeitungsmeldung angezeigt (z. B. *Verarbeitung von 2 Metadatenformularen … Bitte warten.*), während der Import läuft. Nach Abschluss der Verarbeitung wird die Tabelle **[!UICONTROL Metadatenformulare importieren]** angezeigt, die eine Liste der in [!DNL Admin View] verfügbaren Metadatenformulare enthält. Die Tabellenzeile enthält Metadatenformularnamen (unter **[!UICONTROL Name]**), mit diesem Formular verknüpfte Ordner (unter **[!UICONTROL Ordnerzuordnung]**) und eine Option, das Formular vor dem Importieren ![Vorschau](/help/assets/assets/Preview.svg) anzuzeigen.

   ![Seite Metadaten-Forms importieren](/help/assets/assets/import-metadata-forms-page.png)

   >[!NOTE]
   > 
   > In der **[!UICONTROL Importieren von Metadaten-Forms]** zeigt eine Beschriftung **[!UICONTROL Duplizieren]** neben einem Formularnamen an, dass das Formular bereits auf einen Ordner in [!DNL Assets View] angewendet wurde. Beim Importieren dieses doppelten Formulars wird das vorhandene Formular überschrieben, das auf den Ordner angewendet wurde. Um diese Überschreibung zu vermeiden, benennen Sie das Formular um, bevor Sie es importieren. Klicken Sie auf den Namen des Formulars, um es umzubenennen.

1. Klicken Sie ![Ordner auswählen](/help/assets/assets/x.svg) neben einem Ordnernamen (unter [!UICONTROL Ordnerzuordnung]), um die Ordnerzuordnung zum Formular zu entfernen.
1. Klicken Sie ![Ordner auswählen](/help/assets/assets/add-to-folder.svg), um einen Ordner auszuwählen und ihm das entsprechende Metadatenformular zuzuweisen.
1. Klicken Sie auf den roten Kreis, um Details zu nicht unterstützten Metadatenkomponenten oder Zuordnungen im Formular anzuzeigen, die vom Import ausgeschlossen sind.

   ![Seite Metadaten-Forms importieren](/help/assets/assets/unsupported-import-elements.png)

1. Wählen Sie ein oder mehrere Formulare in der Tabelle aus und klicken Sie auf **[!UICONTROL Import starten]**, um die Metadatenformulare und die zugehörigen Ordner in [!DNL Assets View] zu importieren. Eine Verarbeitungsmeldung wird angezeigt (z. B. *Importieren von drei Metadatenformularen). Bitte warten!*). Nach Abschluss des Imports wird in einer Erfolgsmeldung bestätigt, dass die Formulare erfolgreich importiert wurden, und auf der Seite **[!UICONTROL Metadaten-Forms]** (von [!DNL Assets View]) werden sowohl kürzlich importierte als auch vorhandene Formulare angezeigt, die in [!DNL Assets View] verfügbar sind. Auf dieser Seite haben Sie folgende Möglichkeiten:

   * Klicken Sie auf die Spaltenüberschrift, um die Tabelle nach [!UICONTROL Name], [!UICONTROL Geändert] oder [!UICONTROL Autor] zu sortieren.
   * Wählen Sie das importierte Formular aus **[!UICONTROL klicken Sie auf „Aus Ordner(n) entfernen]** und überprüfen Sie dann den Ordnernamen im Ordnerpfad, um sicherzustellen, dass der Ordner korrekt portiert wurde.

     ![Seite Metadatenformulare überprüfen](/help/assets/assets/confirm-ported-folder.png)
   * Wählen Sie das importierte Formular aus und klicken Sie **[!UICONTROL Bearbeiten]**, um alle unterstützten Konfigurationen des Metadatenformulars anzuzeigen. Weitere [ zu den Metadatenformularen, ihren Komponenten ](https://experienceleague.adobe.com/de/docs/experience-manager-assets-essentials/help/metadata#metadata-forms) Feldern finden Sie unter „Einrichten von Metadaten-Forms&quot;.

   ![Seite Metadatenformulare überprüfen](/help/assets/assets/verify-metadata-forms-page.png)

## Überprüfen der importierten Metadatenformulare{#Verify-the-imported-metadata-forms}

Führen Sie nach dem Import der Metadatenformulare aus [!DNL Admin View] in [!DNL Assets View] die folgenden Schritte aus, um den Import zu überprüfen:

1. Navigieren Sie zu einem der zugehörigen Ordner des importierten Metadatenformulars.
1. Navigieren Sie zur [Detailseite eines Assets](/help/assets/navigate-assets-view.md#preview-assets) und überprüfen Sie, ob die unterstützten Metadatenkomponenten, Komponentenfelder und Feldwerte mit [!DNL Admin View] synchronisiert werden. Weitere [ zu Metadatenkomponenten, Komponentenfeldern und Feldwerten finden Sie ](https://experienceleague.adobe.com/de/docs/experience-manager-assets-essentials/help/metadata) Artikel zu Metadaten in Assets Essentials .

   >[!NOTE]
   >
   > Auf [[!DNL Assets View] Detailseite](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/assets-view/metadata-assets-view#metadata-forms) oder [[!DNL Admin View] Eigenschaftenseite](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/assets/administer/metadata-schemas) werden Änderungen an den Metadateneigenschaftswerten automatisch zwischen den beiden Benutzeroberflächen synchronisiert. Strukturänderungen im Formular, z. B. das Hinzufügen oder Entfernen von Feldern oder andere Änderungen, werden jedoch nicht synchronisiert.
