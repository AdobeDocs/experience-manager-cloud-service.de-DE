---
title: Verbinden einer Datenbank mit [!DNL AEM Forms] as a Cloud Service
description: Rufen Sie Daten von einem adaptiven Formular oder einem AEM Workflow ab und speichern Sie sie in RESTful-Webdiensten, SOAP-basierten Webdiensten und OData-Diensten.
exl-id: 9d146275-de0a-4861-b060-d205ed6305f3
source-git-commit: defeee2fee42c6274c71438d6f9fde6e49a05081
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 75%

---

# Verbinden von AEM Forms mit einer Datenbank {#aem-forms-data-integration}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/data-integration.html) |
| AEM as a Cloud Service | Dieser Artikel |


![Datenintegration](do-not-localize/data-integeration.png)

Unternehmensinfrastrukturen umfassen unterschiedliche Back-End-Systeme oder Datenquellen wie Datenbanken, Webservices, REST-Services, OData-Services und CRM-Lösungen. Zusammen bilden sie ein Informationssystem, das Daten für Unternehmensanwendungen zur Abwicklung des Tagesgeschäfts bereitstellt. Umgekehrt erfassen die Anwendungen Daten und senden sie zurück, um die Datenquellen zu aktualisieren.

Für [!DNL AEM Forms]-Anwendungen wie adaptive Formulare und interaktive Kommunikation ist die Integration in Datenquellen erforderlich, damit Kundendaten abgerufen, Formulare gerendert und interaktive Kommunikation erstellt werden können. Es gibt Anwendungsfälle, bei denen Daten basierend auf Benutzereingaben in adaptiven Formularen aus Datenquellen abgerufen werden. Zusätzlich können die übermittelten Daten im adaptiven Formular in die jeweiligen Datenquellen zurückgeschrieben werden, um diese zu aktualisieren.

Ein verteiltes, modulares System hat seine eigenen Vorteile, aber die Herausforderung besteht darin, Datenverknüpfungen über Datenquellen hinweg zu integrieren und zu erstellen. Datenintegration ist der Schlüssel zu einer funktionsfähigen und effizienten Unternehmensinfrastruktur mit unterschiedlichen Datenquellen, die für den Austausch von Geschäftsdaten mit Anwendungen verbunden sind.

## Übersicht über die Datenintegration {#data-integration-overview}

![aem-forms-data-integeration](assets/aem-forms-data-integeration.png)

[!DNL AEM Forms]-Datenintegration ermöglicht die Konfiguration und Verbindung verschiedener Datenquellen mit [!DNL AEM Forms]. In der intuitiven Benutzeroberfläche können Sie eine einheitliche Datendarstellung der Geschäftsbereiche und Services für sämtliche verbundenen Datenquellen erstellen. Diese einheitliche Darstellung wird als Formulardatenmodell bezeichnet. Es handelt sich um eine Erweiterung des JSON-Schemas. Die Entitäten in einem Formulardatenmodell werden als Datenmodellobjekte bezeichnet. Mit einem Formulardatenmodell können Sie:

* Zugreifen auf Datenmodellobjekte, Eigenschaften und Services aus verbundenen Datenquellen.
* Erstellen benutzerdefinierter Datenmodellobjekten und -eigenschaften.
* Erstellen von Verknüpfungen zwischen Datenmodellobjekten innerhalb und zwischen Datenquellen.
* Aufrufen von Services für Datenmodellobjekte zum Abfragen von Daten aus und Schreiben von Daten in Datenquellen.

Nachdem Sie ein Formulardatenmodell erstellt haben, können Sie es in verschiedenen Workflows für adaptive Formulare und interaktive Kommunikation verwenden, zum Beispiel:

* Erstellen adaptiver Formulare und interaktiver Kommunikation basierend auf dem Formulardatenmodell
* Ausfüllen adaptiver Formulare und interaktiver Kommunikation aus konfigurierten Datenquellen
* Aufrufen von Datenquellen-Serivices/-vorgängen mithilfe von Regeln für adaptive Formulare
* Schreiben von Daten übermittelten adaptiven Formulardaten in Datenquellen

## Erste Schritte mit der Datenintegration {#get-started-with-data-integration}

Der erste Schritt zur Implementierung der Datenintegration besteht darin, Datenquellen zu identifizieren und zu konfigurieren, die Informationen speichern, die Sie in Anwendungsfällen für adaptive Forms und interaktive Kommunikation verwenden möchten. Als Nächstes erstellen Sie ein Formulardatenmodell, das Datenmodellobjekte, Eigenschaften und Services aus mindestens einer Datenquelle verwendet. Sie können adaptive Formulare und interaktive Kommunikation auf Grundlage eines Formulardatenmodells erstellen, bei dem Felder adaptiver Formulare oder Platzhalter in interaktiver Kommunikation an die jeweiligen Datenquelleneigenschaften gebunden sind.

[!DNL AEM Forms] Sie können auch ein Formulardatenmodell erstellen, das unabhängig von Datenquellen ist, und Datenmodellobjekte und Eigenschaften im Formulardatenmodell später mit der Datenquelle verknüpfen oder verknüpfen. Dadurch werden alle Abhängigkeiten von Datenquellen entfernt, während Sie an einem Formulardatenmodell arbeiten.

Lesen Sie folgende Informationen für die ersten Schritte mit der Datenintegration, um sie zu verstehen und zu implementieren.

* [Konfigurieren von Datenquellen](configure-data-sources.md)
* [Erstellen des Formulardatenmodells](create-form-data-models.md)
* [Arbeiten mit einem Formulardatenmodell](work-with-form-data-model.md)
* [Verwenden eines Formulardatenmodells](using-form-data-model.md)

>[!NOTE]
>
>[!UICONTROL Experience Manager Forms] unterstützt keine relationalen Datenbanken.
