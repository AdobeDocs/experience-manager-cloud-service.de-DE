---
title: Verbinden einer Datenbank mit [!DNL AEM Forms] as a Cloud Service
description: Rufen Sie Daten von einem adaptiven Formular oder einem AEM-Workflow ab und speichern Sie sie in RESTful-Web-Services, SOAP-basierten Web-Services und OData-Services.
feature: Adaptive Forms, Form Data Model
role: Admin, User
exl-id: 9d146275-de0a-4861-b060-d205ed6305f3
source-git-commit: 7b31a2ea016567979288c7a8e55ed5bf8dfc181d
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 68%

---

# Verbinden von AEM Forms mit einer Datenbank {#aem-forms-data-integration}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/data-integration.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |



![Datenintegration](do-not-localize/data-integeration.png)

Unternehmensinfrastrukturen umfassen unterschiedliche Back-End-Systeme oder Datenquellen wie Datenbanken, Webservices, REST-Services, OData-Services und CRM-Lösungen. Zusammen bilden sie ein Informationssystem, das Daten für Unternehmensanwendungen zur Abwicklung des Tagesgeschäfts bereitstellt. Umgekehrt erfassen die Anwendungen Daten und senden sie zurück, um die Datenquellen zu aktualisieren.

Wenn Sie das adaptive Formular mit einer Datenbank verbinden, ist die Integration mit Datenquellen erforderlich, um Kundendaten beim Rendern von Formularen abzurufen. Es gibt Anwendungsfälle, bei denen Daten basierend auf Benutzereingaben in adaptiven Formularen aus Datenquellen abgerufen werden. Wenn Sie ein adaptives Formular an eine Datenbank senden, können die gesendeten Daten des adaptiven Formulars außerdem zur Aktualisierung der entsprechenden Datenquellen zurückgeschrieben werden.

Ein verteiltes, modulares System hat seine eigenen Vorteile, aber die Herausforderung besteht darin, Datenverknüpfungen über Datenquellen hinweg zu integrieren und zu erstellen. Datenintegration ist der Schlüssel zu einer funktionsfähigen und effizienten Unternehmensinfrastruktur mit unterschiedlichen Datenquellen, die für den Austausch von Geschäftsdaten mit Anwendungen verbunden sind.

## Übersicht über die Datenintegration {#data-integration-overview}

![aem-forms-data-integeration](assets/aem-forms-data-integeration.png)

[!DNL AEM Forms]-Datenintegration ermöglicht die Konfiguration und Verbindung verschiedener Datenquellen mit [!DNL AEM Forms]. In der intuitiven Benutzeroberfläche können Sie eine einheitliche Datendarstellung der Geschäftsbereiche und Services für sämtliche verbundenen Datenquellen erstellen. Die einheitliche Darstellung wird als Formulardatenmodell (FDM) bezeichnet, eine Erweiterung des JSON-Schemas. Die Entitäten in einem Formulardatenmodell (FDM) werden als Datenmodellobjekte bezeichnet. Mit einem Formulardatenmodell (FDM) können Sie:

* Zugreifen auf Datenmodellobjekte, Eigenschaften und Services aus verbundenen Datenquellen.
* Erstellen benutzerdefinierter Datenmodellobjekten und -eigenschaften.
* Erstellen von Verknüpfungen zwischen Datenmodellobjekten innerhalb und zwischen Datenquellen.
* Aufrufen von Services für Datenmodellobjekte zum Abfragen von Daten aus und Schreiben von Daten in Datenquellen.

Nachdem Sie ein Formulardatenmodell (FDM) erstellt haben, können Sie es wie folgt verwenden:

* Adaptive Forms basierend auf einem Formulardatenmodell (FDM) erstellen
* Vorbefüllen adaptiver Formulare aus konfigurierten Datenquellen
* Aufrufen von Datenquellen-Serivices/-vorgängen mithilfe von Regeln für adaptive Formulare
* Schreiben von Daten übermittelten adaptiven Formulardaten in Datenquellen

## Erste Schritte mit der Datenintegration {#get-started-with-data-integration}

Der erste Schritt zur Implementierung der Datenintegration zum Senden des adaptiven Formulars an eine Datenbank besteht darin, Datenquellen zu identifizieren und zu konfigurieren, in denen Informationen gespeichert werden, die Sie in adaptiven Formularen verwenden möchten. Als Nächstes erstellen Sie ein Formulardatenmodell (FDM), das Datenmodellobjekte, Eigenschaften und Dienste aus einer oder mehreren Datenquellen verwendet. Sie können adaptive Forms auf Grundlage eines Formulardatenmodells (FDM) erstellen, bei dem Felder für adaptive Formulare an die entsprechenden Datenquelleneigenschaften gebunden sind.

[!DNL AEM Forms] Sie können auch ein Formulardatenmodell (FDM) erstellen, das unabhängig von Datenquellen ist, und Datenmodellobjekte und -eigenschaften im Formulardatenmodell (FDM) später mit der Datenquelle verknüpfen oder verknüpfen. Dadurch werden alle Abhängigkeiten von Datenquellen entfernt, während Sie an einem Formulardatenmodell (FDM) arbeiten.

Lesen Sie folgende Informationen für die ersten Schritte mit der Datenintegration, um sie zu verstehen und zu implementieren:

* [Konfigurieren von Datenquellen](configure-data-sources.md)
* [Formulardatenmodell (FDM) erstellen](create-form-data-models.md)
* [Arbeiten mit dem Formulardatenmodell (FDM)](work-with-form-data-model.md)
* [Formulardatenmodell (FDM) verwenden](using-form-data-model.md)

>[!NOTE]
>
>[!UICONTROL Experience Manager Forms] unterstützt keine relationalen Datenbanken.