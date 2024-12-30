---
title: Überblick über Content Hub
description: Erfahren Sie mehr über Content Hub, seine wichtigsten Vorteile, den Zugriff darauf und das Feedback zu den in Content Hub verfügbaren Optionen.
exl-id: c5908058-f1ad-4aaa-9e8e-c0157e107ed1
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 100%

---

# Überblick über Content Hub {#overview-content-hub}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |----|-----|

![Überblick über Content Hub](assets/content-hub-overview.png)

>[!AVAILABILITY]
>
>Das Content Hub-Handbuch ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den KI-Assistenten von Adobe Acrobat, um Ihre Fragen zu beantworten.
>
>[!BADGE Content Hub-Handbuch als PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Content Hub ist als Teil von Experience Manager Assets as a Cloud Service für die Demokratisierung des Zugriffs auf Markeninhalte für Unternehmen und ihre Geschäftspartner verfügbar. Der Schwerpunkt liegt auf der Verteilung von Assets zur skalierten Aktivierung und der Erstellung von Markeninhaltsvarianten, um die Marketing-Agilität zu verbessern.

## Warum Content Hub?

Content Hub bietet die folgenden Hauptvorteile:

**Suchen und Freigeben aller markenkonformen genehmigten Assets, die in einem intuitiven Portal verfügbar sind**

AEM Assets dient als zentrale Datenquelle, und alle genehmigten Assets sind in Content Hub automatisch in einer flachen Hierarchie verfügbar, um das Sucherlebnis zu verbessern.

**Konfigurierbare Benutzeroberfläche**

Die gängigsten Eigenschaften in Content Hub, z. B. Filter für die Suche, die beim Hinzufügen oder Importieren von Assets verfügbaren Felder, Asset-Eigenschaften und Bannerinhalte für das Branding, sind konfigurierbar, und Admins können die Content Hub-Benutzeroberfläche problemlos entsprechend ihren Anforderungen konfigurieren.

**Ermöglichen Sie es auch Nichtkreativen, Inhalte zu bearbeiten und neu zu mischen, während sie markenkonform bleiben**

Mit Content Hub können Sie neue Inhalte mit Adobe Express erstellen (falls Sie über Adobe Express-Berechtigungen verfügen). Sie können vorhandene Inhalte mit anwenderfreundlichen Tools bearbeiten, Markenvarianten mit Vorlagen und Markenelementen erstellen und neue Inhalte mit den neuesten GenAI-Funktionen von Adobe Firefly erstellen.

**Gewinnen Sie Einblicke in die Verwendung von Inhalten in verschiedenen Teams**

[!DNL Content Hub] bietet wertvolle Einblicke in Assets und geht eine Herausforderung an, auf die Marketing-Stakeholder häufig stoßen: Asset-Nutzungsstatistiken, die in Marketing-Kampagnen, Kanälen und verschiedenen Regionen verwendet werden. Durch das Erlangen eines klaren Verständnisses der Leistung und Beliebtheit der Assets, liefert es verwertbare Einblicke, die für die Verbesserung des Benutzererlebnisses unerlässlich sind.

## Voraussetzungen {#prerequisites-content-hub}

Content Hub erfordert eine Produktions-Autorenumgebung von Experience Manager as a Cloud Service, Version 2024.6 oder höher (mindestens Version 2024.6.16799).

## Wie erfolgt der Zugriff auf Content Hub? {#access-content-hub}

[Nachdem Sie Content Hub eingerichtet](/help/assets/deploy-content-hub.md) und eine Benutzerin oder einen Benutzer zum [Content Hub-Produktprofil](/help/assets/deploy-content-hub.md#content-hub-instance-product-profile) hinzugefügt haben, können Sie wie folgt auf Content Hub zugreifen:

* Zugriff auf Content Hub über den folgenden Link:

  `https://experience.adobe.com/#/assets/contenthub`

* Melden Sie sich bei experience.adobe.com an und klicken Sie im Abschnitt **[!UICONTROL Schnellzugriff]** auf **[!UICONTROL Experience Manager Assets Content Hub]** :
  ![Zugriff auf Content Hub](assets/access-content-hub.png)

* Melden Sie sich bei experience.adobe.com an und klicken Sie im Produktumschalter auf **[!UICONTROL Experience Manager Assets Content Hub]**:
  ![Methode 3 für den Zugriff auf Content Hub](assets/access-content-hub-alternate.png)



## Bereitstellen von Feedback in Content Hub {#provide-content-hub-feedback}

Um produktbezogene Verbesserungen zu empfehlen, klicken Sie in der Benutzeroberfläche von Content Hub oben neben dem Namen Ihres Unternehmens auf **[!UICONTROL Feedback]**.

Geben Sie einen Betreff und eine Beschreibung der Empfehlung an und fügen Sie bei Bedarf Dateien hinzu. Klicken Sie auf **[!UICONTROL Senden]**, um das Feedback an Adobe zu senden.

![Content Hub-Feedback](assets/content-hub-feedback.png)

## Einrichten von Content Hub für Ihr Team {#setup-content-hub}

Führen Sie die folgenden Schritte aus, um Content Hub für Ihr Team einzurichten:

1. [Aktivieren Sie Content Hub für Experience Manager Assets mithilfe von Cloud Manager](deploy-content-hub.md#enable-content-hub).

1. [Integrieren Sie eine Person als Content Hub-Admin](deploy-content-hub.md#onboard-content-hub-administrator).

1. [Fügen Sie wichtige Content Hub-Benutzende hinzu](deploy-content-hub.md#onboard-content-hub-consumer-users).

1. [DAM-Autorinnen bzw. DAM-Autoren oder -Admins genehmigen Assets mithilfe von Experience Manager-Assets](approve-assets.md).

1. [Admins können die Content Hub-Benutzeroberfläche für andere Benutzende konfigurieren](configure-content-hub-ui-options.md).

1. [Gewähren Sie Content Hub Zugriff auf weitere Benutzende aus dem Team](deploy-content-hub.md#onboard-content-hub-consumer-users).

1. [Greifen Sie auf das Content Hub-Portal zu](#access-content-hub).

1. [Geben Sie Feedback in Content Hub](#provide-content-hub-feedback).


## Weitere Informationen zu wichtigen Funktionen {#key-capabilities-content-module}

<table>
<td>
   <a href="/help/assets/configure-content-hub-ui-options.md">
   <img alt="Bereitstellen von Content Hub" src="./assets/configure-assets.png" />
   </a>
   <div>
      <a href="/help/assets/configure-content-hub-ui-options.md">
<strong>Konfigurieren der Benutzeroberfläche von Content Hub</strong>
</a>
   </div>
   <p>
      <em>Erfahren Sie, wie Admins die Benutzeroberfläche von Content Hub konfigurieren können. </em>
   </p>
</td>


<td>
   <a href="/help/assets/search-assets-content-hub.md">
   <img alt="Suchen nach in Content Hub verfügbaren Assets" src="./assets/search.png" />
   </a>
   <div>
      <a href="/help/assets/search-assets-content-hub.md">
<strong>Suchen nach in Content Hub verfügbaren Assets</strong>
</a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie verschiedene Funktionen nutzen können, um Ihre Suchergebnisse einzugrenzen.</em>
   </p>
</td>
<td>
   <a href="/help/assets/edit-images-content-hub.md">
   <img alt="Bearbeiten von Bildern mit Adobe Express" src="./assets/edit-images-content-hub.png" />
   </a>
   <div>
      <a href="/help/assets/edit-images-content-hub.md">
<strong>Bearbeiten von Bildern mit Adobe Express</strong>
</a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie mit Adobe Express Varianten von Bildern in Content Hub erstellen</em>
   </p>
</td>
</table>
<table>
<td>
   <a href="/help/assets/share-assets-content-hub.md">
   <img alt="Freigeben von in Content Hub verfügbaren Assets" src="./assets/share-assets-banner.png" />
   </a>
   <div>
      <a href="/help/assets/share-assets-content-hub.md">
<strong>Freigeben von in Content Hub verfügbaren Assets</strong>
</a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie ein oder mehrere Assets als Link freigeben und dann darauf zugreifen.</em>
   </p>
</td>
<td>
   <a href="/help/assets/collections-content-hub.md">
   <img alt="Verwalten von Sammlungen in Content Hub" src="./assets/manage-collection.png" />
   </a>
   <div>
      <a href="/help/assets/collections-content-hub.md">
<strong>Verwalten von Sammlungen in Content Hub</strong>
</a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie Sammlungen mithilfe von Assets erstellen und diese dann verwalten.</em>
   </p>
</td>
<td>
   <a href="/help/assets/insights-content-hub.md">
   <img alt="Freigeben von in Content Hub verfügbaren Assets" src="./assets/asset-insights-banner.jpg" />
   </a>
   <div>
      <a href="/help/assets/insights-content-hub.md">
<strong>Anzeigen von Asset-Einblicken in Content Hub</strong>
</a>
   </div>
   <p>
      <em> Das Inhaltsmodul bietet wertvolle Einblicke in Assets und geht eine Herausforderung an, auf die Marketing-Stakeholder häufig stoßen</em>
   </p>
</td>
</table>
