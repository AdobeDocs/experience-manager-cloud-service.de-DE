---
title: Kaskadierende Metadaten
description: In diesem Artikel wird beschrieben, wie Sie kaskadierende Metadaten für Assets in der Asset-Ansicht definieren.
feature: Metadata
role: Admin, User
source-git-commit: 2bb309afc372fe18ce274a2813ed25cba22eb4de
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 29%

---


# Kaskadierende Metadaten - Assets-Ansicht{#cascading-metadata-assets-view}

Beim Erfassen der Metadateninformationen eines Assets stellen Benutzende Informationen in den verschiedenen verfügbaren Feldern bereit. Sie können bestimmte Metadatenfelder oder Feldwerte anzeigen, die von den in den anderen Feldern gewählten Optionen abhängig sind. Solche bedingt angezeigten Metadaten werden als „kaskadierende Metadaten“ bezeichnet. Mit anderen Worten: Sie können eine Abhängigkeit zwischen einem bestimmten Metadatenfeld/-wert und einem oder mehreren Feldern und/oder deren Werten schaffen.

Verwenden Sie Metadaten-Forms, um Regeln für die Anzeige kaskadierender Metadaten zu definieren. Wenn Ihr Metadatenformular beispielsweise ein Feld vom Typ Asset enthält, können Sie einen entsprechenden Satz von Feldern definieren, die je nach ausgewähltem Asset-Typ angezeigt werden sollen.

Im Folgenden finden Sie einige Anwendungsfälle, für die Sie kaskadierende Metadaten definieren können:

* Wenn der Benutzerstandort erforderlich ist, können Sie die Namen relevanter Städte basierend auf der von Personen angegebenen Land und Bundesland anzeigen.
* Laden Sie relevante Markennamen basierend auf der von Benutzenden ausgewählten Produktgruppe in einer Liste.
* Aktivieren/Deaktivieren Sie die Sichtbarkeit eines bestimmten Felds, basierend auf dem in einem anderen Feld angegebenen Wert. Zeigen Sie beispielsweise separate Felder für die Versandadresse an, wenn Benutzende die Sendung an eine andere Adresse liefern lassen möchten.
* Legen Sie ein Feld basierend auf dem in einem anderen Feld angegebenen Wert als Pflichtfeld fest.
* Ändern Sie die für ein bestimmtes Feld angezeigten Optionen basierend auf dem in einem anderen Feld angegebenen Wert.
* Legen Sie den standardmäßigen Metadatenwert in einem bestimmten Feld basierend auf dem in einem anderen Feld angegebenen Wert fest.

>[!IMPORTANT]
>
>Die Funktion „Kaskadierende Metadaten“ ist als Funktion für eingeschränkte Verfügbarkeit verfügbar. Sie können [einen Adobe-Support-Fall erstellen und übermitteln](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) um die Funktion für Ihre Bereitstellung zu aktivieren.

## Erstellen kaskadierender Metadaten in [!DNL Experience Manager] {#configure-cascading-metadata-in-aem}

Stellen Sie sich ein Szenario vor, in dem kaskadierende Metadaten basierend auf dem ausgewählten Asset-Typ angezeigt werden sollen. Beispiel-

* Zeigen Sie für ein Video geeignete Felder wie Format, Codec, Dauer usw. an.
* Zeigen Sie für ein Word- oder PDF-Dokument Felder wie Seitenzahl, Autor usw. an.

Wir verwenden ein Dropdown-Feld mit dem Namen `Image` als Beispiel, um Dateien basierend auf ihrem Bildtyp zu kategorisieren. Die Dropdown-Liste enthält Optionen für unterstützte Bilderweiterungen (z. B. JPG/JPEG, GIF usw.). Um die Datenkonsistenz zu gewährleisten und zu verhindern, dass nicht unterstützte Formate ausgewählt oder verarbeitet werden, wird eine Validierungsregel auf dieses Feld angewendet. Die Regel bewertet den ausgewählten Dropdown-Wert und erzwingt Einschränkungen, die mit den akzeptierten Bildformaten übereinstimmen.

>[!IMPORTANT]
>
>Sie können Regeln nur basierend auf Dropdown-Feldern erstellen.

Unabhängig vom ausgewählten Asset-Typ müssen Sie die Copyright-Informationen als erforderliches Feld anzeigen. Sie können die [vordefinierten Metadatenkomponenten“ verwenden &#x200B;](metadata-assets-view.md#property-components)und [einem Ordner Metadaten zuweisen](metadata-assets-view.md#assign-metadata-form-folder).

### Erstellen von Metadaten in Forms {#build-metadata-schema-forms}

Gehen Sie wie folgt vor, um ein neues Metadatenformular zu erstellen:

1. Klicken Sie auf das [!DNL Experience Manager] Logo und gehen Sie zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Metadata Forms]** > **[!UICONTROL Erstellen]**.

1. Wählen Sie im **[!UICONTROL -]** den entsprechenden Formulartyp aus: **[!UICONTROL Datei]**, **[!UICONTROL Ordner]** oder **[!UICONTROL Sammlung]**.

1. Geben Sie den Titel des Metadatenformulars im Feld **[!UICONTROL Name]** an.

1. Alternativ können Sie eine vorhandene Metadatenformularvorlage aus der Dropdown-Liste **[!UICONTROL Aus vorhandener Formularvorlage auswählen]** auswählen.

1. Ein leeres Metadatenformular wird angezeigt. Neue Registerkarte hinzufügen.

   ![Metadatenformular-Benutzeroberfläche](assets/metadata-form-ui.png)

   * **A:** Wechseln zwischen [!UICONTROL Bearbeiten] oder [!UICONTROL Vorschau]
   * **B:** [Komponenten des Metadatenformulars](metadata-assets-view.md#property-components)
   * **C:** Wechseln Sie zu einem anderen Metadatenformular
   * **D:** Neue Registerkarte hinzufügen
   * **E:** Arbeitsfläche
   * **F:** Allgemeine Einstellungen für die ausgewählte Komponente
   * **G:Registerkarte &quot;**&quot;
   * **H:** Komponenteneigenschaften

Sehen Sie sich dieses Video an, um die Sequenz der Schritte anzuzeigen [Einrichten von Metadaten-Forms](https://video.tv.adobe.com/v/341275).

### Ändern eines vorhandenen Metadatenformulars {#modify-existing-metadata-form}

Gehen Sie wie folgt vor, um ein vorhandenes Metadatenformular zu ändern:

1. Öffnen Sie ein vorhandenes Metadatenformular und navigieren Sie zu den [vordefinierten Komponenten](metadata-assets-view.md#property-components) die Sie im Formular hinzufügen möchten, und legen Sie die Elemente auf der Arbeitsfläche ab.

   Fügen Sie entsprechend dem Anwendungsfall **Bild** ein Dropdown-Feld hinzu, um Bild-Asset-Typen zu definieren. Geben Sie den Namen und den Eigenschaftspfad in **Einstellungen** an und konfigurieren Sie das Feld optional als **[!UICONTROL Schreibgeschützt]** oder **[!UICONTROL Mehrfachauswahl]**.

1. Geben Sie die Schlüssel-Wert-Optionen für das Dropdown-Menü an, indem Sie sie manuell eingeben, einen JSON-Pfad angeben oder eine CSV-Datei importieren.

   * Um die Werte manuell anzugeben, wählen Sie **[!UICONTROL Manuell hinzufügen]** unter **[!UICONTROL Wahlen]** aus, klicken Sie auf `Add` und geben Sie die Optionsbeschriftung und den Wert an. Geben Sie beispielsweise die Asset-Typen Video, PDF und Bild an.

     ![Bild-Asset-Typ](assets/image-asset-type.png)

   * Um Werte aus einem JSON-Pfad abzurufen, wählen Sie **[!UICONTROL Über JSON-Pfad hinzufügen]** und geben Sie den Pfad der JSON-Datei an.

     >[!NOTE]
     >
     >Speichern Sie die JSON-Datei an einem freigegebenen Speicherort, auf den alle DAM-Editoren und -Autoren zugreifen können.

     ![Auswahl über JSON-Pfad hinzufügen](assets/add-json-choices.png)

   * Um die Werte dynamisch aus einer CSV abzurufen, klicken Sie **[!UICONTROL CSV importieren]** und geben Sie den Pfad der CSV-Datei an. [!DNL Experience Manager] ruft die Schlüssel-Wert-Paare in Echtzeit ab, wenn das Formular dem Anwender angezeigt wird.

     ![Auswahl über CSV hinzufügen](assets/import-csv-choices.png)

   >[!NOTE]
   > 
   >Sie können die Optionen nicht aus einer CSV-Datei importieren und manuell bearbeiten, da sich beide Optionen gegenseitig ausschließen.

1. Um eine Abhängigkeit zwischen dem Feld Bild und anderen Feldern zu erstellen, wählen Sie das abhängige Feld aus und öffnen Sie die Registerkarte **[!UICONTROL Regeln]**. Jede Komponente unterstützt einen bestimmten Regelsatz. In diesem Anwendungsfall werden die Optionen Bild-Asset-Typ verwendet, um die Regellogik zu definieren.

   <!--![Image Asset Type Rule](assets/image-asset-type-rule.png)-->

   <!--![rule tab](assets/rule-tab.png)-->

1. Wählen **[!UICONTROL unter]** die Option **[!UICONTROL Erforderlich basierend auf neuer Regel]** aus. Klicken Sie auf ![Pluszeichen](assets/do-not-localize/aem_assets_add_icon.png), um eine neue Regel hinzuzufügen.

   ![rule](assets/image-required-rule1.png)

   Im aktuellen Anwendungsfall ist das Feld Asset-Typ erforderlich, wenn das Bild-Asset-Format JPG/JPEG, PNG, GIF, TIFF oder WEBP ist. Klicken Sie außerdem auf ![Symbol „Bearbeiten](assets/do-not-localize/edit.svg), um die Regel neu zu definieren, oder klicken Sie auf ![Symbol „Löschen](assets/do-not-localize/delete.svg), um die definierte Regel zu löschen.

   ![rule](assets/image-required-rule2.png)

1. Wählen **[!UICONTROL unter &quot;]**&quot; die Option **[!UICONTROL Sichtbar, basierend auf neuer Regel]** aus. Klicken Sie auf ![Pluszeichen](assets/do-not-localize/aem_assets_add_icon.png), um eine neue Regel hinzuzufügen.

   >[!NOTE]
   >
   >Sie können die Bedingung **[!UICONTROL Anforderung]** und **[!UICONTROL Sichtbarkeit]** unabhängig voneinander anwenden.

   ![rule](assets/image-visible-rule1.png)

   Im aktuellen Anwendungsfall ist das Feld Asset-Typ sichtbar, wenn das Bild-Asset-Format JPG/JPEG, PNG oder GIF ist. Klicken Sie außerdem auf ![Symbol „Bearbeiten](assets/do-not-localize/edit.svg), um die Regel neu zu definieren, oder klicken Sie auf ![Symbol „Löschen](assets/do-not-localize/delete.svg), um die definierte Regel zu löschen.

   ![rule](assets/image-visible-rule2.png)

1. Wählen Sie **[!UICONTROL Wahlen basierend auf Regel]** aus, um eine Abhängigkeit zu erstellen und eine Regel zu definieren. Klicken Sie auf ![Pluszeichen](assets/do-not-localize/aem_assets_add_icon.png), um eine neue Regel hinzuzufügen.

   ![rule](assets/image-choices-rule1.png)

   Um regelbasierte Auswahlmöglichkeiten für die Dropdown-Liste „Asset-Typ“ zu konfigurieren, erstellen Sie eine Regel und legen Sie „Bild“ als abhängiges Feld fest. Definieren Sie dann die Anzeigewerte für jedes Bildformat, indem Sie Bild für JPG/JPEG, PNG, GIF und TIFF auswählen und Video für WEBP auswählen, um sicherzustellen, dass nur die beabsichtigten Werte für jedes Format aktiviert sind, um die relevanten Optionen dynamisch anzuzeigen. Klicken Sie außerdem auf ![Symbol „Bearbeiten](assets/do-not-localize/edit.svg), um die Regel neu zu definieren, oder klicken Sie auf ![Symbol „Löschen](assets/do-not-localize/delete.svg), um die definierte Regel zu löschen.

   ![rule](assets/image-choices-rule2.png)

1. Wiederholen Sie auf ähnliche Weise die Schritte, um eine Abhängigkeit zwischen den anderen Assets wie PDF und Word im Feld [!UICONTROL Asset-Typ] und Feldern wie [!UICONTROL Seitenzahl] und [!UICONTROL Autor] zu erstellen.

1. Klicken Sie auf **[!UICONTROL Speichern]**. Wenden Sie das Metadatenformular auf einen Ordner an.

1. Navigieren Sie zu dem Ordner, auf den Sie das Metadatenformular angewendet haben, und öffnen Sie die Eigenschaftsseite eines Assets. Je nach Ihrer Auswahl im Feld „Asset-Typ“ werden relevante kaskadierende Metadatenfelder angezeigt.

   ![Kaskadierende Metadatenformularausgabe](assets/cascading-metadata-form-output.png)

>[!NOTE]
> 
>Um frühzeitig auf die kaskadierenden Metadaten in Ihrem Assets View-Konto zugreifen zu können[&#x200B; (erstellen und senden Sie einen Adobe-Support-Fall](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).

## Nächste Schritte {#next-steps}

* [Sehen Sie sich ein Video zum Verwalten von Metadatenformularen in der Assets-Ansicht an](https://experienceleague.adobe.com/docs/experience-manager-learn/assets-essentials/configuring/metadata-forms.html?lang=de)

* Geben Sie Produkt-Feedback über die Option [!UICONTROL Feedback] in der Benutzeroberfläche der Assets-Ansicht

* Geben Sie Feedback zur Dokumentation durch ![Bearbeiten der Seite](assets/do-not-localize/edit-page.png) über die Option [!UICONTROL Diese Seite bearbeiten] oder durch ![Erstellen eines GitHub-Themas](assets/do-not-localize/github-issue.png) über die Option [!UICONTROL Problem protokollieren] in der rechten Seitenleiste

* Kontaktieren Sie die [Kundenunterstützung](https://experienceleague.adobe.com/de?support-solution=General#support)

