---
title: Inhaltsautomatisierung für die Creative Cloud-Integration
description: Erzeugen von Varianten von Assets mithilfe der Creative Cloud-Integration
contentOwner: AG
feature: Upload, Asset Processing, Publishing, Asset Compute Microservices
role: User, Admin
exl-id: 4cff355e-d12c-44c7-b519-4cc37f49e396
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '801'
ht-degree: 100%

---

# Erzeugen von Varianten von Assets mithilfe der [!DNL Adobe Creative Cloud]-Integration {#content-automation}

Das Add-on zur Inhaltsautomatisierung integriert [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] und [!DNL Adobe Creative Cloud]-APIs zur kreativen und skalierten Verarbeitung Ihrer Assets. [!DNL Experience Manager] verwendet Cloud-basierte [Asset-Microservices](/help/assets/asset-microservices-overview.md), um die [!DNL Adobe Creative Cloud]-Funktionen zu verwenden und die Asset-Erstellung und die Medienbearbeitung zu automatisieren.

Um Assets in [!DNL Adobe Photoshop] und [!DNL Adobe Lightroom] zu bearbeiten, müssen Sie keine Assets von [!DNL Experience Manager Assets] herunterladen, sie bearbeiten und erneut hochladen. Sie erstellen und konfigurieren ein Verarbeitungsprofil in [!DNL Experience Manager], wenden das Profil auf einen Ordner an und laden die Assets in den Ordner hoch. Ihre hochgeladenen Assets werden basierend auf den Verarbeitungsprofilen erneut verarbeitet und Sie erhalten Varianten dieser Assets. Die konsistente und mühelose Massenverarbeitung spart manuelle Arbeit und erhöht die Content-Geschwindigkeit, und das ohne die Notwendigkeit von kreativen Fähigkeiten. Außerdem können die Entwickler und Partner die Asset-Microservices mit direktem Zugriff auf diese APIs erweitern und benutzerdefinierte Logik hinzufügen.

Benutzer können Verarbeitungsprofile erstellen, um die folgenden kreativen Vorgänge für ihre Assets zu automatisieren:

* **Auto-Ton**: Verwendet künstliche Intelligenz, um den Inhalt des Bildes zu analysieren und basierend auf den einzigartigen Eigenschaften des Bildes intelligent Licht- und Farbkorrekturen vorzunehmen.

* **Auto-Upright**: Verwendet künstliche Intelligenz, um den Inhalt des Bildes zu analysieren und verzerrte Perspektiven in Bildern zu korrigieren. Beispielsweise, um Horizonte gerade auszurichten.

  ![Auto-Ton](/help/assets/assets/content-automation-autotone.png)

  *Abbildung: Auto-Ton und automatische Ausrichtung können dazu beitragen, verzerrte Bilder zu verbessern.*

* **Lightroom-Vorgaben**: Gibt Bildern einen benutzerdefinierten Look, indem über benutzerdefinierte Vorgaben ein konsistentes Erscheinungsbild erzielt wird.

  ![Lightroom-Vorgabe](/help/assets/assets/content-automation-lrpresets.png)

  *Abbildung: Adobe Lightroom-Vorgabe zur konsistenten Verbesserung der Bildqualität für viele Bilder.*

* **Bild-Freistellen**: Wendet künstliche Intelligenz an, um eine Auswahl um sich abhebende Objekte zu erstellen und den Hintergrund mit einem einzigen Befehl zu entfernen.

  ![Entfernen des Hintergrunds und Ausschneiden des Bildes aus einem Foto](/help/assets/assets/content-automation-backgroundremove.png)

* **Bildmaske**: Verwendet künstliche Intelligenz zum Erstellen von Masken um sich abhebende Objekte mit einem einzigen Befehl.

  ![Bild mit KI maskieren](/help/assets/assets/content-automation-mask.png)

* **Photoshop-Aktionen**: Wendet eine Reihe von [!DNL Adobe Photoshop]-Aufgaben auf eine Datei oder einen Satz von Dateien an.

  ![Photoshop-Aktionen](/help/assets/assets/content-automation-psactions.png)

* **Intelligentes Ersetzen von Objekten**: Skalierte Personalisierung, indem Sie Bilder austauschen und dabei alle Effekte und Anpassungen beibehalten, die in einer PSD-Datei vorgenommen wurden.

  ![Intelligentes Ersetzen von Objekten](/help/assets/assets/content-automation-objectreplace.png)

## Aktivieren der Inhaltsautomatisierung für ein AEM as a Cloud Service-Programm {#enable-content-automation}

So aktivieren Sie das Inhaltsautomatisierungs-Add-on für ein AEM as a Cloud Service-Programm mithilfe von Cloud Manager:

1. Wenden Sie sich an Ihren Kundenbetreuer, um das Inhaltsautomatisierungs-Add-on zu lizenzieren.
1. Rufen Sie Cloud Manager auf und wechseln Sie mithilfe der Organisationsauswahl zu Ihrer Organisation.
1. Klicken Sie auf **[!UICONTROL Programm hinzufügen]** und geben Sie einen Programmnamen an.
1. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Erweitern Sie **[!UICONTROL Assets]** und wählen Sie **[!UICONTROL Inhaltsautomatisierung]**.
1. Klicken Sie auf **[!UICONTROL Erstellen]**.
1. Führen Sie die Pipeline aus, um [die Änderungen in Cloud Manager bereitzustellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html?lang=de).

Wenn Sie einem bestehenden AEM as a Cloud Service-Programm in Cloud Manager das Add-on zur Inhaltsautomatisierung hinzufügen müssen:

1. Klicken Sie auf „...“ auf der Programmkarte.

1. Wählen Sie **[!UICONTROL Programm bearbeiten]** aus und wählen Sie dann die Registerkarte **[!UICONTROL Lösungen und Add-ons]** aus.

1. Erweitern Sie **[!UICONTROL Assets]** und wählen Sie **[!UICONTROL Inhaltsautomatisierung]**.
1. Klicken Sie auf **[!UICONTROL Aktualisieren]**.
1. Führen Sie die Pipeline aus, um [die Änderungen in Cloud Manager bereitzustellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html?lang=de).

## Verwenden eines Verarbeitungsprofils, um Ihre kreativen Assets massenhaft zu bearbeiten {#process-assets}

Gehen Sie wie folgt vor, um mithilfe von Verarbeitungsprofilen automatisch Varianten zu erstellen:

1. Gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Verarbeitungsprofile]**.

1. Klicken Sie auf **[!UICONTROL Erstellen]** und geben Sie einen **[!UICONTROL Namen]** an.

1. Wählen Sie die Registerkarte **[!UICONTROL Creative]** aus, geben Sie den Ausgabeordner an und klicken Sie auf **[!UICONTROL Neue hinzufügen]**, um eine kreative Konfiguration hinzuzufügen.

1. Geben Sie den **[!UICONTROL Namen der Ausgabedarstellung]** (oder Ausgabename), **[!UICONTROL Erweiterung]** (oder Dateityp) an, wählen Sie **[!UICONTROL Qualität]** (oder Ausgabeparameter), wählen Sie die MIME-Typ-Listen **[!UICONTROL Einschlüsse]** und **[!UICONTROL Ausschlüsse]** (oder Eingabe-Asset-Filter) aus und wählen Sie den erforderlichen Kreativ-Vorgang aus.

   Registerkarte ![[!UICONTROL Creative] im [!UICONTROL Verarbeitungsprofil]](assets/creative-processing-profile.png)

1. Einige Vorgänge erfordern zusätzliche Parameter (Asset). Geben Sie bei Bedarf Werte für diese zusätzlichen Parameter an.

1. Fügen Sie weitere kreative Vorgänge als Teil desselben Verarbeitungsprofils hinzu oder speichern Sie das Profil.

1. Wenden Sie das Verarbeitungsprofil auf einen Ordner an. Wählen Sie auf der Seite **[!UICONTROL Eigenschaften]** eines Ordners **[!UICONTROL Asset-Verarbeitung]** und wählen Sie das anzuwendende Verarbeitungsprofil aus.

Nachdem Sie das Verarbeitungsprofil auf einen DAM-Ordner angewendet haben, führen alle Assets, die in diesen Ordner hochgeladen oder aktualisiert wurden, zusätzlich zur Standardverarbeitung die definierten Vorgänge aus. Die Unterordner übernehmen dieselben Profile, die auf die übergeordneten Ordner angewendet wurden. Benutzer können diese Vererbung außer Kraft setzen.

Um die vorhandenen Assets zu verarbeiten, wählen Sie die Assets aus, klicken Sie auf die Option **[!UICONTROL Erneut verarbeiten]** und wählen Sie dann das erforderliche Verarbeitungsprofil aus.

## Tipps und Einschränkungen {#limitations-best-practices}

* [!DNL Experience Manager] begrenzt die Asset-Verarbeitungen auf 300 Anforderungen pro Minute und 700 Anforderungen pro Minute für die gesamte Organisation.
* Die Dateigröße ist bei [!DNL Adobe Photoshop]-API-Vorgängen auf 4 GB und bei [!DNL Adobe Lightroom]-Vorgängen auf 1 GB beschränkt.
* PDF-Ausgabedarstellungen von Microsoft Office-Dokumenten („.docx“, „.doc“, „.ppt“, „.pptx“, „.xls“, „.xlsx“) sind auf Dateien mit einer Größe von maximal 100 MB beschränkt.
* Die Videotranscodierung ist auf Eingabedateien mit maximal 15 GB beschränkt.

**Siehe auch**

* [Assets übersetzen](translate-assets.md)
* [Assets-HTTP-API](mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](file-format-support.md)
* [Suchen von Assets](search-assets.md)
* [Connected Assets](use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](asset-reports.md)
* [Metadatenschemata](metadata-schemas.md)
* [Herunterladen von Assets](download-assets-from-aem.md)
* [Verwalten von Metadaten](manage-metadata.md)
* [Suchfacetten](search-facets.md)
* [Verwalten von Sammlungen](manage-collections.md)
* [Massenimport von Metadaten](metadata-import-export.md)
* [Veröffentlichen von Assets in AEM und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [Konfigurieren und verwenden Sie Asset-Microservices über Verarbeitungsprofile](/help/assets/asset-microservices-configure-and-use.md).
>* [Integrieren Sie [!DNL Experience Manager] mit [!DNL Creative Cloud]](/help/assets/aem-cc-integration-best-practices.md).
>* [Asset-Aufnahme und -Verarbeitung mit Asset-Microservices: Ein Überblick](/help/assets/asset-microservices-overview.md).
