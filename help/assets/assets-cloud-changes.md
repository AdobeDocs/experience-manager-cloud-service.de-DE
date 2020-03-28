---
title: Wichtige Änderungen in Adobe Experience Manager Assets als Cloud-Dienst
description: Die Änderungen an Adobe Experience Manager-Assets im AEM Cloud-Dienst im Vergleich zu Adobe Experience Manager 6.5 sind erheblich.
translation-type: tm+mt
source-git-commit: ab79c3dabb658e242df08ed065ce99499c9b7357

---


# Notable changes to Experience Manager Assets as a Cloud Service {#notable-changes}

Adobe Experience Manager als Cloud-Dienst bietet viele neue Funktionen und Möglichkeiten zur Verwaltung Ihrer AEM-Projekte. Es gibt jedoch viele Unterschiede zwischen Experience Manager Assets vor Ort oder in Adobe Managed Service im Vergleich zu Experience Manager als Cloud-Dienst. Dieses Dokument hebt die wichtigen Unterschiede hervor.

>[!NOTE]
>
>In diesem Dokument werden die bemerkenswerten Änderungen hervorgehoben, die speziell für Experience Manager Assets als Cloud-Dienst gelten. Siehe die allgemeinen [Änderungen an Experience Manager als Cloud-Dienst](/help/release-notes/aem-cloud-changes.md).

Die Hauptunterschiede zu Experience Manager 6.5 bestehen in den folgenden Bereichen:

* [Asset-Erfassung](#asset-ingestion)
* [Entfernen der klassischen Benutzeroberfläche](#classic-ui)

## Asset-Erfassung {#asset-ingestion}

Das Hochladen von Assets wurde für Effizienz optimiert, da die Asset-Erfassung besser skaliert und die Uploads beschleunigt werden konnten. Produktfunktionen (Web-Benutzeroberflächen, Desktop-Clients) wurden aktualisiert. Dies kann sich jedoch auf einige bestehende Anpassungen auswirken.

* Experience Manager verwendet das Prinzip des direkten binären Zugriffs für Upload- und Download- und Asset-Mikrodienste für die Asset-Verarbeitung. Siehe [Übersicht über die Asset-Erfassung](/help/assets/asset-microservices-overview.md).
   * Asset-Upload [mit direktem binären Zugriff](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * Technische Informationen finden Sie unter [direktes binäres Upload-Protokoll und APIs](/help/assets/developer-reference-material-apis.md#overview-binary-upload).
* Die standardmäßige Workflow- **[!UICONTROL DAM-Asset-Aktualisierung]** in früheren Versionen von AEM ist nicht mehr verfügbar. Stattdessen bieten Asset-Mikrodienste einen skalierbaren, leicht verfügbaren Dienst, der den Großteil der standardmäßigen Asset-Verarbeitung abdeckt (Darstellungen, Metadaten-Extraktion, Extraktion für die Indexierung).
   * Siehe [Konfigurieren und Verwenden von Asset Microservices](/help/assets/asset-microservices-configure-and-use.md)
   * Um bei der Verarbeitung benutzerdefinierte Workflow-Schritte durchführen zu können, können [Nachbearbeitungs-Workflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) verwendet werden.
* Für Assets, die über Package Manager eingehen, ist eine manuelle Neuverarbeitung mithilfe der Aktion &quot;Asset **[!UICONTROL neu verarbeiten]** &quot;in der Assets-Oberfläche erforderlich.

Mit Asset-Mikrodiensten generierte Standarddarstellungen werden auf abwärtskompatible Weise in den Asset-Repository-Knoten gespeichert (gleiche Benennungskonventionen).

## Entwickeln und Testen von Asset-Mikrodiensten {#developing-testing-asset-microservices}

Asset Microservices ist ein nativer Cloud-Dienst, der automatisch für Experience Manager bereitgestellt wird und in Programmen und Umgebung, die in Cloud Manager verwaltet werden, verkabelt wird. Entwickler, die Experience Manager erweitern oder Anpassungen vornehmen, können den vorhandenen Inhalt (oder die Assets mit in einer Cloud-Umgebung generierten Darstellungen) verwenden, um den Code zu testen und zu validieren, indem sie Assets anzeigen, herunterladen und anzeigen.

Um den Code und den Prozess einschließlich der Asset-Erfassung und -Verarbeitung einer End-to-End-Validierung zu unterziehen, stellen Sie die Codeänderungen mithilfe der Pipeline auf einer Cloud-Dev-Umgebung bereit und testen Sie diese mit der vollständigen Ausführung der Asset-Mikrodienste-Verarbeitung.

## Entfernen der klassischen Benutzeroberfläche {#classic-ui}

Die klassische Benutzeroberfläche ist in Experience Manager nicht mehr als Cloud-Dienst verfügbar.
