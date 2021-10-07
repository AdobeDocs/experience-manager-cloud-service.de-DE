---
title: Inhaltsautomatisierung für die Creative Cloud-Integration
description: Generieren von Varianten von Assets mithilfe der Creative Cloud-Integration
contentOwner: AG
feature: Upload,Asset Processing,Publishing,Asset Compute Microservices,Workflow
role: User,Admin
exl-id: 4cff355e-d12c-44c7-b519-4cc37f49e396
source-git-commit: d37193833d784f3f470780b8f28e53b473fd4e10
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 0%

---

# Generieren von Varianten von Assets mithilfe der Integration von [!DNL Adobe Creative Cloud] {#content-automation}

Das Add-on zur Inhaltsautomatisierung integriert [!DNL Adobe Experience Manager Assets] als [!DNL Cloud Service]- und [!DNL Adobe Creative Cloud]-APIs zur kreativen Verarbeitung Ihrer Assets im Maßstab. [!DNL Experience Manager] verwendet Cloud-basierte  [Asset-](/help/assets/asset-microservices-overview.md) Microservices, um die  [!DNL Adobe Creative Cloud] Funktionen zu verwenden und die Asset-Erstellung und Medienverarbeitung zu automatisieren.

Um Assets in [!DNL Adobe Photoshop] und [!DNL Adobe Lightroom] zu bearbeiten, müssen Sie keine Assets von [!DNL Experience Manager Assets] herunterladen, sie bearbeiten und erneut hochladen. Sie erstellen und konfigurieren ein Verarbeitungsprofil in [!DNL Experience Manager], wenden das Profil auf einen Ordner an und laden die Assets in den Ordner hoch. Ihre hochgeladenen Assets werden basierend auf den Verarbeitungsprofilen erneut verarbeitet und Sie erhalten Varianten dieser Assets. Die konsistente und mühelose Massenverarbeitung spart manuelle Arbeit und erhöht die Content-Geschwindigkeit, auch das ohne die Notwendigkeit von kreativen Fähigkeiten. Außerdem können die Entwickler und Partner die Asset-Microservices mit direktem Zugriff auf diese APIs erweitern und benutzerdefinierte Logik einschließen.

Benutzer können Verarbeitungsprofile erstellen, um die folgenden kreativen Vorgänge für ihre Assets zu automatisieren:

* **Auto-Ton**: Verwendet künstliche Intelligenz, um den Inhalt des Bildes zu analysieren und basierend auf den einzigartigen Eigenschaften des Bildes intelligent Licht- und Farbkorrekturen vorzunehmen.

* **Auto-Upright**: Verwendet künstliche Intelligenz, um den Inhalt des Bildes zu analysieren und verzerrte Perspektiven in Bildern zu korrigieren. So erstellen Sie beispielsweise Horizonte auf Ebene.

   ![Auto-Ton](/help/assets/assets/content-automation-autotone.png)

   *Abbildung: Auto-Ton und automatische Ausrichtung können dazu beitragen, verzerrte Bilder zu verbessern.*

* **Lightroom-Vorgaben**: Wendet einen benutzerdefinierten Look auf Bilder an, um ein konsistentes Erscheinungsbild mit benutzerdefinierten Vorgaben zu erzielen.

   ![Lightroom-Vorgabe](/help/assets/assets/content-automation-lrpresets.png)

   *Abbildung: Adobe Lightroom-Voreinstellung zur konsistenten Verbesserung der Bildqualität für viele Bilder.*

* **Bild-Cutout**: Verwendet künstliche Intelligenz, um Auswahlmöglichkeiten für Alison-Objekte zu erstellen und Hintergrund mit einem einzigen Befehl zu entfernen.

   ![Entfernen Sie den Hintergrund und schneiden Sie ein Bild aus einem Foto aus](/help/assets/assets/content-automation-backgroundremove.png)

* **Bildmaske**: Verwendet künstliche Intelligenz zum Erstellen von Masken um visuelle Objekte mit einem einzigen Befehl.

   ![Bild mit AI maskieren](/help/assets/assets/content-automation-mask.png)

* **Photoshop-Aktionen**: Wendet eine Reihe von  [!DNL Adobe Photoshop] Aufgaben auf eine Datei oder einen Stapel von Dateien an.

   ![Photoshop-Aktionen](/help/assets/assets/content-automation-psactions.png)

* **Smart Object Replacement**: Personalisierung in großem Maßstab, indem Sie Bilder austauschen können, während alle Effekte und Anpassungen beibehalten werden, die innerhalb einer PSD-Datei vorgenommen werden.

   ![Objekte intelligent ersetzen](/help/assets/assets/content-automation-objectreplace.png)

## Verwenden eines Verarbeitungsprofils, um Ihre kreativen Assets stapelweise zu bearbeiten {#process-assets}

Gehen Sie wie folgt vor, um mithilfe von Verarbeitungsprofilen automatisch Varianten zu erstellen:

1. Wenden Sie sich an [Adobe Customer Support](https://experienceleague.adobe.com/#support) , um die Lizenz zu erhalten.

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Verarbeitungsprofile]**.

1. Wählen Sie **[!UICONTROL Erstellen]** und geben Sie einen **[!UICONTROL Namen]** an.

1. Wählen Sie die Registerkarte **[!UICONTROL Creative]** aus, geben Sie den Ausgabeordner an und wählen Sie **[!UICONTROL Neu hinzufügen]** aus, um eine kreative Konfiguration hinzuzufügen.

1. Geben Sie **[!UICONTROL Ausgabedarstellungsname]** (oder Ausgabename), **[!UICONTROL Erweiterung]** (oder Dateityp), wählen Sie **[!UICONTROL Qualität]** (oder Ausgabeparameter), wählen Sie **[!UICONTROL Includes]** und **[!UICONTROL Excludes]** MIME-Listen (oder Eingabe-Asset-Filter) und wählen Sie die erforderlichen Vorgang.

   ![ Registerkarte &quot;Creative&quot;im  [!UICONTROL Verarbeitungsprofil]](assets/creative-processing-profile.png)

1. Einige Vorgänge erfordern zusätzliche Parameter (Asset). Geben Sie bei Bedarf Werte für diese zusätzlichen Parameter an.

1. Fügen Sie weitere kreative Vorgänge als Teil desselben Verarbeitungsprofils hinzu oder speichern Sie das Profil.

1. Wenden Sie das Verarbeitungsprofil auf einen Ordner an. Wählen Sie auf der Seite **[!UICONTROL Eigenschaften]** eines Ordners **[!UICONTROL Asset-Verarbeitung]** und wählen Sie das anzuwendende Verarbeitungsprofil aus.

Nachdem Sie das Verarbeitungsprofil auf einen DAM-Ordner angewendet haben, führen alle Assets, die in diesen Ordner hochgeladen oder aktualisiert wurden, zusätzlich zur Standardverarbeitung die definierten Vorgänge aus. Die Unterordner übernehmen dieselben Profile wie auf die übergeordneten Ordner angewendet. Benutzer können diese Vererbung überschreiben.

Um die vorhandenen Assets zu verarbeiten, wählen Sie die Assets aus, wählen Sie die Option **[!UICONTROL Neu verarbeiten]** und wählen Sie dann das erforderliche Verarbeitungsprofil aus.

## Tipps und Einschränkungen {#limitations-best-practices}

* [!DNL Experience Manager] begrenzt die Asset-Verarbeitung auf 300 Anforderungen pro Minute und 700 Anforderungen pro Minute und Organisation.
* Die Dateigröße ist bei API-Vorgängen von [!DNL Adobe Photoshop] auf 4 GB und bei [!DNL Adobe Lightroom]-Vorgängen auf 1 GB beschränkt.

>[!MORELIKETHIS]
>
>* [Konfigurieren und verwenden Sie Asset-Microservices über Verarbeitungsprofile](/help/assets/asset-microservices-configure-and-use.md).
>* [ [!DNL Experience Manager] Integrieren mit [!DNL Creative Cloud]](/help/assets/aem-cc-integration-best-practices.md).
>* [Asset-Erfassung und -Verarbeitung mit Asset-Microservices: Eine Übersicht](/help/assets/asset-microservices-overview.md).

