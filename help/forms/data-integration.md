---
title: 'Verbinden einer Datenbank mit  [!DNL AEM Forms]  as a Cloud Service '
seo-title: AEM Forms Data Integration
description: Sie können Daten aus  [!DNL AEM Forms]  as a Cloud Service abrufen und sie in RESTful-Webservices, SOAP-basierten Webservices und OData-Services speichern. Der Service bietet ein dediziertes Tool zum Abrufen, Testen, Validieren und Senden von Daten an verschiedene Datenquelltypen.
exl-id: 9d146275-de0a-4861-b060-d205ed6305f3
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 100%

---

# Verbinden von Datenquellen mit Cloud Service {#aem-forms-data-integration}

![Datenintegration](do-not-localize/data-integeration.png)

Unternehmensinfrastrukturen umfassen unterschiedliche Back-End-Systeme oder Datenquellen wie Datenbanken, Webservices, REST-Services, OData-Services und CRM-Lösungen. Zusammen bilden sie ein Informationssystem, das Daten für Unternehmensanwendungen zur Abwicklung des Tagesgeschäfts bereitstellt. Umgekehrt erfassen die Anwendungen Daten und senden sie zurück, um die Datenquellen zu aktualisieren.

Für [!DNL AEM Forms]-Anwendungen wie adaptive Formulare und interaktive Kommunikation ist die Integration in Datenquellen erforderlich, damit Kundendaten abgerufen, Formulare gerendert und interaktive Kommunikation erstellt werden können. Es gibt Anwendungsfälle, bei denen Daten basierend auf Benutzereingaben in adaptiven Formularen aus Datenquellen abgerufen werden. Zusätzlich können die übermittelten Daten im adaptiven Formular in die jeweiligen Datenquellen zurückgeschrieben werden, um diese zu aktualisieren.

Verteilte, modulare Systeme bieten ihre Vorteile, die Herausforderung besteht jedoch darin, Datenverknüpfungen datenquellenübergreifend zu integrieren und zu erstellen. Datenintegration ist der Schlüssel zu einer funktionsfähigen und effizienten Unternehmensinfrastruktur mit unterschiedlichen Datenquellen, die für den Austausch von Geschäftsdaten mit Anwendungen verbunden sind.

## Übersicht über die Datenintegration {#data-integration-overview}

![aem-forms-data-integeration](assets/aem-forms-data-integeration.png)

[!DNL AEM Forms]-Datenintegration ermöglicht die Konfiguration und Verbindung verschiedener Datenquellen mit [!DNL AEM Forms]. In der intuitiven Benutzeroberfläche können Sie eine einheitliche Datendarstellung der Geschäftsbereiche und Services für sämtliche verbundenen Datenquellen erstellen. Diese einheitliche Darstellung wird als Formulardatenmodell bezeichnet. Es handelt sich um eine Erweiterung des JSON-Schemas. Die Entitäten in einem Formulardatenmodell werden als Datenmodellobjekte bezeichnet. Durch ein Formulardatenmodell erhalten Sie folgende Möglichkeiten:

* Zugreifen auf Datenmodellobjekte, Eigenschaften und Services aus verbundenen Datenquellen.
* Erstellen benutzerdefinierter Datenmodellobjekten und -eigenschaften
* Erstellen von Verknüpfungen zwischen Datenmodellobjekten innerhalb und zwischen Datenquellen.
* Aufrufen von Services für Datenmodellobjekte zum Abfragen von Daten aus und Schreiben von Daten in Datenquellen.

Nachdem Sie ein Formulardatenmodell erstellt haben, können Sie es in verschiedenen Workflows für adaptive Formulare und interaktive Kommunikation verwenden, zum Beispiel:

* Erstellen adaptiver Formulare und interaktiver Kommunikation basierend auf dem Formulardatenmodell
* Ausfüllen adaptiver Formulare und interaktiver Kommunikation aus konfigurierten Datenquellen
* Aufrufen von Datenquellen-Serivices/-vorgängen mithilfe von Regeln für adaptive Formulare
* Schreiben von Daten übermittelten adaptiven Formulardaten in Datenquellen

## Erste Schritte mit der Datenintegration {#get-started-with-data-integration}

Der erste Schritt zur Implementierung der Datenintegration besteht darin, Datenquellen, die Informationen speichern und die Sie in Anwendungsfällen für adaptive Formulare sowie interaktive Kommunikation verwenden möchten, zu identifizieren und zu konfigurieren. Als Nächstes erstellen Sie ein Formulardatenmodell, das Datenmodellobjekte, Eigenschaften und Services aus mindestens einer Datenquelle verwendet. Sie können adaptive Formulare und interaktive Kommunikation auf Grundlage eines Formulardatenmodells erstellen, bei dem Felder adaptiver Formulare oder Platzhalter in interaktiver Kommunikation an die jeweiligen Datenquelleneigenschaften gebunden sind.

Mit [!DNL AEM Forms] können Sie auch ein von Datenquellen unabhängiges Formulardatenmodell erstellen und später Datenmodellobjekte und Eigenschaften im Formulardatenmodell mit der Datenquelle verknüpfen oder daran binden. Dadurch werden alle Abhängigkeiten von Datenquellen beseitigt, während Sie an einem Formulardatenmodell arbeiten.

Lesen Sie folgende Informationen für die ersten Schritte mit der Datenintegration, um sie zu verstehen und zu implementieren.

* [Konfigurieren von Datenquellen](configure-data-sources.md)
* [Erstellen des Formulardatenmodells](create-form-data-models.md)
* [Arbeiten mit einem Formulardatenmodell](work-with-form-data-model.md)
* [Verwenden eines Formulardatenmodells](using-form-data-model.md)

>[!NOTE]
>
>[!UICONTROL Experience Manager Forms] unterstützt keine relationalen Datenbanken.
