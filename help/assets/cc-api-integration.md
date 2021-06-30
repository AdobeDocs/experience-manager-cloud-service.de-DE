---
title: Inhaltsautomatisierung für die Creative Cloud-Integration
description: Generieren von Varianten von Assets mithilfe der Creative Cloud-Integration
contentOwner: AG
feature: Hochladen,Asset-Verarbeitung,Veröffentlichung,Asset compute-Microservices,Workflow
role: Business Practitioner,Administrator
source-git-commit: ffca94ef8d93cf95011d7e3128c49929f69cdc28
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 0%

---


# Generieren von Varianten von Assets mithilfe der Integration von [!DNL Adobe Creative Cloud] {#content-automation}

Das Add-on zur Inhaltsautomatisierung integriert Experience Manager Assets as a Cloud Service und Adobe Creative Cloud-APIs, um Ihre Assets skaliert kreativ zu verarbeiten. Experience Manager verwendet Cloud-basierte [Asset-Microservices](/help/assets/asset-microservices-overview.md), um die Adobe Creative Cloud-Funktionen zu nutzen und die Asset-Erstellung und Medienverarbeitung zu automatisieren.

Um Assets in [!DNL Adobe Photoshop] und [!DNL Adobe Lightroom] zu bearbeiten, müssen Sie sie nicht herunterladen, bearbeiten und in [!DNL Experience Manager Assets] hochladen. Erstellen und konfigurieren Sie einfach ein Verarbeitungsprofil, wenden Sie das Profil auf einen Ordner an und laden Sie die Assets in den Ordner hoch. Die in den Ordner hochgeladenen Assets werden verarbeitet, um verschiedene Varianten dieses Assets zu erstellen. Die konsistente und mühelose Massenverarbeitung und -bearbeitung von Assets spart manuelle Arbeit und erhöht die Content-Geschwindigkeit. Darüber hinaus können Entwickler und Partner die Asset-Microservices mit direktem Zugriff auf diese APIs erweitern und benutzerdefinierte Logik einschließen.

Benutzer können Verarbeitungsprofile erstellen, um die folgenden kreativen Vorgänge für ihre Assets zu automatisieren:

* **Auto-Ton**: Verwendet künstliche Intelligenz, um den Inhalt des Bildes zu analysieren und basierend auf den einzigartigen Eigenschaften des Bildes intelligent Licht- und Farbkorrekturen vorzunehmen.
* **Auto-Upright**: Verwendet künstliche Intelligenz, um den Inhalt des Bildes zu analysieren und verzerrte Perspektiven in Bildern zu korrigieren. So erstellen Sie beispielsweise Horizonte auf Ebene.
* **Lightroom-Vorgaben**: Wendet einen benutzerdefinierten Look auf Bilder an, um ein konsistentes Erscheinungsbild mit benutzerdefinierten Vorgaben zu erzielen.
* **Bild-Cutout**: Verwendet künstliche Intelligenz, um Auswahlmöglichkeiten um visuelle Objekte zu erstellen und Hintergrund mit einem einzigen Befehl zu entfernen.
* **Bildmaske**: Verwendet künstliche Intelligenz, um mit einem einzigen Befehl Masken um visuelle Objekte zu erstellen.
* **Photoshop-Aktionen**: Wendet eine Reihe von Aufgaben (in Photoshop) auf eine Datei oder einen Dateistapel an.
* **Smart Object Replacement**: Personalisierungen werden skaliert durchgeführt, indem Sie Bilder austauschen und dabei alle in einer PSD-Datei angewendeten Effekte und Anpassungen beibehalten.

## Verarbeitungsprofil zur Verarbeitung von Assets verwenden {#process-assets}

Gehen Sie wie folgt vor, um mithilfe von Verarbeitungsprofilen automatisch Varianten zu erstellen:

1. Wenden Sie sich an [Adobe Customer Care](https://experienceleague.adobe.com/#support), um die Lizenz zu erhalten.

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Verarbeitungsprofile]**.

1. Wählen Sie **[!UICONTROL Erstellen]** und geben Sie einen **[!UICONTROL Namen]** an.

1. Wählen Sie die Registerkarte **[!UICONTROL Creative]**, geben Sie den Ausgabeordner an und wählen Sie **[!UICONTROL Neu hinzufügen]** aus, um kreative Konfigurationen hinzuzufügen.

1. Geben Sie **[!UICONTROL Ausgabedarstellungsname]** (oder den Ausgabenamen), **[!UICONTROL Erweiterung]** (oder Dateityp), wählen Sie **[!UICONTROL Qualität]** (oder Ausgabeparameter), wählen Sie Listen vom Typ MIME ein- und ausschließen (oder den Asset-Eingabefilter) und wählen Sie den gewünschten kreativen Vorgang aus.

1. Einige Vorgänge erfordern einen zusätzlichen Parameter (Asset). Geben Sie bei Bedarf Werte für diese zusätzlichen Parameter an.

1. Fügen Sie weitere kreative Vorgänge als Teil desselben Verarbeitungsprofils hinzu oder speichern Sie das Profil.

1. Wenden Sie das Verarbeitungsprofil auf einen Ordner an. Wählen Sie auf der Seite **[!UICONTROL Eigenschaften]** eines Ordners **[!UICONTROL Asset-Verarbeitung]** und wählen Sie das anzuwendende Verarbeitungsprofil aus.

Nachdem das Verarbeitungsprofil auf einen DAM-Ordner angewendet wurde, führen alle in diesen Ordner hochgeladenen oder aktualisierten Assets zusätzlich zur Standardverarbeitung die definierten Vorgänge aus. Die Unterordner übernehmen dieselben Profile wie auf die übergeordneten Ordner angewendet. Benutzer können diese Vererbung überschreiben.

Um die vorhandenen Assets zu verarbeiten, wählen Sie die Assets aus, wählen Sie die Option **[!UICONTROL Neu verarbeiten]** und wählen Sie dann das erforderliche Verarbeitungsprofil aus.

## Tipps und Einschränkungen {#limitations-best-practices}

* [!DNL Experience Manager] begrenzt die Asset-Verarbeitung auf 300 Anforderungen pro Minute und 700 Anforderungen pro Minute und Organisation.
* Die Dateigröße ist bei API-Vorgängen von [!DNL Adobe Photoshop] auf 4 GB und bei [!DNL Adobe Lightroom]-Vorgängen auf 1 GB beschränkt.

>[!MORELIKETHIS]
>
>* [Konfigurieren und verwenden Sie Asset-Microservices über Verarbeitungsprofile](/help/assets/asset-microservices-configure-and-use.md).
>* [ [!DNL Experience Manager] Integrieren mit [!DNL Creative Cloud]](/help/assets/aem-cc-integration-best-practices.md).

