---
title: Importieren von Metadatenformularen aus [!DNL Admin View] in [!DNL Assets View]
description: In diesem Artikel wird beschrieben, wie Sie das Metadatenformular aus [!DNL Admin View] in [!DNL Assets View]importieren
contentOwner: AG
feature: Metadata
role: User, Admin
badgeSaas: label="AEM Assets" type="Positive" tooltip="Gilt für AEM Assets)."
exl-id: 5fb4fe97-486a-4a91-af60-a7182efcc2f9
source-git-commit: d37ebf94f617e8424799757c18037a73e97820b4
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 95%

---

# Importieren von Metadatenformularen aus [!DNL Admin View] in [!DNL Assets View] {#import-metadata-forms-from-admin-view-to-assets-view}

Mit [!DNL Adobe Experience Manager Assets] können Sie Metadatenformulare und ihre Ordnerzuordnungen aus [!DNL Admin View] in [!DNL Assets View] importieren.

## Voraussetzungen{#prerequisites-for-importing-metadata-forms-to-assets-view}

Stellen Sie sicher, dass Sie über Administratorrechte verfügen, um die Metadatenformulare und ihre Ordnerzuordnungen aus [!DNL Admin View] in [!DNL Assets View] importieren zu können.

## Importieren von Metadatenformularen in [!DNL Assets View]{#import-metadata-forms-to-assets-view}

Führen Sie als Admin die folgenden Schritte aus, um die in [!DNL Admin View] verfügbaren Metadatenformulare in [!DNL Assets View] zu importieren:

1. Navigieren Sie zur [!DNL Assets View]-Startseite und klicken Sie unter **[!UICONTROL Einstellungen]** auf **[!UICONTROL Metadatenformulare]**, um die Seite **[!UICONTROL Metadatenformulare]** mit der Liste der in [!DNL Assets View] verfügbaren Metadatenformulare anzuzeigen.

   ![Seite „Metadatenformulare“](/help/assets/assets/metadata-forms-page.png)

1. Wählen Sie **[!UICONTROL Importieren]**, wird eine Verarbeitungsmeldung angezeigt (z. B. *Verarbeitung von 2 Metadatenformularen … Bitte warten.*) Während des Imports. Nach Abschluss der Verarbeitung wird die Tabelle **[!UICONTROL Metadatenformulare importieren]** angezeigt, die eine Liste der in [!DNL Admin View] verfügbaren Metadatenformulare enthält. Die Tabellenzeile enthält Metadatenformularnamen (unter **[!UICONTROL Name]**), mit diesem Formular verknüpfte Ordner (unter **[!UICONTROL Ordnerzuordnung]**) und eine Option zum Anzeigen einer Vorschau ![Vorschau](/help/assets/assets/Preview.svg) des Formulars vor dem Importieren.

   ![Seite „Metadatenformulare importieren“](/help/assets/assets/import-metadata-forms-page.png)

   >[!NOTE]
   > 
   > In der Tabelle **[!UICONTROL Metadatenformulare importieren]** zeigt das Label **[!UICONTROL Duplizieren]** neben einem Formularnamen an, dass das Formular bereits auf einen Ordner in [!DNL Assets View] angewendet wurde. Beim Importieren dieses doppelten Formulars wird das vorhandene Formular überschrieben, das auf den Ordner angewendet wurde. Um diese Überschreibung zu vermeiden, benennen Sie das Formular um, bevor Sie es importieren. Klicken Sie auf den Formularnamen, um ihn zu ändern.

1. Klicken Sie ![Ordner auswählen](/help/assets/assets/x.svg) neben einem Ordnernamen (unter [!UICONTROL Ordnerzuordnung]), um die Ordnerzuordnung des Formulars zu entfernen.
1. Klicken Sie ![Ordner auswählen](/help/assets/assets/add-to-folder.svg), um einen Ordner auszuwählen und ihm das entsprechende Metadatenformular zuzuweisen.
1. Klicken Sie auf den roten Kreis, um Details zu nicht unterstützten Metadatenkomponenten oder Zuordnungen im Formular anzuzeigen, die vom Import ausgeschlossen sind.

   ![Seite „Metadatenformulare importieren“](/help/assets/assets/unsupported-import-elements.png)

1. Wählen Sie ein oder mehrere Formulare in der Tabelle aus und klicken Sie auf **[!UICONTROL Import starten]**, um die Metadatenformulare und die zugehörigen Ordner in [!DNL Assets View] zu importieren. Eine Verarbeitungsmeldung wird angezeigt (z. B. *3 Metadatenformulare werden importiert. Bitte warten Sie!*). Nach Abschluss des Imports wird in einer Erfolgsmeldung bestätigt, dass die Formulare erfolgreich importiert wurden. Auf der Seite **[!UICONTROL Metadatenformulare]** (von [!DNL Assets View]) werden sowohl kürzlich importierte als auch vorhandene Formulare angezeigt, die in [!DNL Assets View] verfügbar sind. Auf dieser Seite haben Sie folgende Möglichkeiten:

   * Klicken Sie auf die Spaltenkopfzeile, um die Tabelle nach [!UICONTROL Name], [!UICONTROL Geändert] oder [!UICONTROL Autorin bzw. Autor] zu sortieren.
   * Wählen Sie das importierte Formular aus und klicken Sie auf **[!UICONTROL Aus Ordner(n) entfernen]**. Überprüfen Sie dann den Ordnernamen im Ordnerpfad, um sicherzustellen, dass der Ordner korrekt portiert wurde.
     ![Seite „Metadatenformulare überprüfen“](/help/assets/assets/confirm-ported-folder.png)
   * Wählen Sie das importierte Formular aus und klicken Sie auf **[!UICONTROL Bearbeiten]**, um alle unterstützten Konfigurationen des Metadatenformulars anzuzeigen. Weitere Informationen zu den Metadatenformularen, ihren Komponenten und Feldern finden Sie unter [Einrichten von Metadatenformulare](https://experienceleague.adobe.com/de/docs/experience-manager-assets-essentials/help/metadata#metadata-forms).

   ![Seite „Metadatenformulare überprüfen“](/help/assets/assets/verify-metadata-forms-page.png)

## Überprüfen der importierten Metadatenformulare{#Verify-the-imported-metadata-forms}

Führen Sie nach dem Import der Metadatenformulare aus [!DNL Admin View] in [!DNL Assets View] die folgenden Schritte aus, um den Import zu überprüfen:

1. Navigieren Sie zu einem der zugehörigen Ordner des importierten Metadatenformulars.
1. Navigieren Sie zur [Detailseite eines Assets](/help/assets/navigate-assets-view.md#preview-assets) und überprüfen Sie, ob die unterstützten Metadatenkomponenten, Komponentenfelder und Feldwerte mit [!DNL Admin View] synchronisiert werden. Weitere Informationen zu Metadatenkomponenten, Komponentenfeldern und Feldwerten finden Sie im Artikel zu [Metadaten in Assets Essentials](https://experienceleague.adobe.com/de/docs/experience-manager-assets-essentials/help/metadata).

   >[!NOTE]
   >
   > Auf der [[!DNL Assets View] -Detailseite](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/assets-view/metadata-assets-view#metadata-forms) oder der [[!DNL Admin View] -Eigenschaftenseite](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/assets/administer/metadata-schemas) werden Änderungen an den Metadateneigenschaftswerten automatisch zwischen den beiden Benutzeroberflächen synchronisiert. Strukturänderungen im Formular, z. B. das Hinzufügen oder Entfernen von Feldern oder andere Änderungen, werden jedoch nicht synchronisiert.


**Siehe auch**

* [Assets übersetzen](/help/assets/translate-assets.md)
* [Assets-HTTP-API](/help/assets/mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](/help/assets/file-format-support.md)
* [Suchen von Assets](/help/assets/search-assets.md)
* [Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](/help/assets/asset-reports.md)
* [Metadatenschemata](/help/assets/metadata-schemas.md)
* [Herunterladen von Assets](/help/assets/download-assets-from-aem.md)
* [Verwalten von Metadaten](/help/assets/manage-metadata.md)
* [Verwalten von Dynamic Media-Vorlagen](/help/assets/dynamic-media/manage-dynamic-media-templates.md)
* [Verwalten von Berichten](/help/assets/manage-reports-assets-view.md)
* [Suchfacetten](/help/assets/search-facets.md)
* [Verwalten von Sammlungen](/help/assets/manage-collections.md)
* [Massenimport von Metadaten](/help/assets/metadata-import-export.md)
* [Veröffentlichen von Assets in AEM und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

