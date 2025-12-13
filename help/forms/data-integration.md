---
title: Verbinden einer Datenbank mit [!DNL AEM Forms] as a Cloud Service
description: Rufen Sie Daten von einem adaptiven Formular oder einem AEM-Workflow ab und speichern Sie sie in RESTful-Web-Services, SOAP-basierten Web-Services und OData-Services.
feature: Adaptive Forms, Form Data Model
role: Admin, User
exl-id: 9d146275-de0a-4861-b060-d205ed6305f3
source-git-commit: 8f39bffd07e3b4e88bfa200fec51572e952ac837
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 81%

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

[!DNL AEM Forms]-Datenintegration ermöglicht die Konfiguration und Verbindung verschiedener Datenquellen mit [!DNL AEM Forms]. In der intuitiven Benutzeroberfläche können Sie ein einheitliches Datendarstellungsschema der Geschäftsbereiche und Services für sämtliche verbundenen Datenquellen erstellen. Diese einheitliche Darstellung wird als Formulardatenmodell (FDM) bezeichnet. Es handelt sich um eine Erweiterung des JSON-Schemas. Die Entitäten in einem Formulardatenmodell (FDM) werden als Datenmodellobjekte bezeichnet. Ein Formulardatenmodell (FDM) ermöglicht Ihnen:

* Zugreifen auf Datenmodellobjekte, Eigenschaften und Services aus verbundenen Datenquellen.
* Erstellen benutzerdefinierter Datenmodellobjekten und -eigenschaften.
* Erstellen von Verknüpfungen zwischen Datenmodellobjekten innerhalb und zwischen Datenquellen.
* Aufrufen von Services für Datenmodellobjekte zum Abfragen von Daten aus und Schreiben von Daten in Datenquellen.

Wenn Sie ein Formulardatenmodell (FDM) erstellt haben, können Sie es für Folgendes verwenden:

* Erstellen adaptiver Formulare auf Grundlage eines Formulardatenmodells (FDM)
* Vorbefüllen adaptiver Formulare aus konfigurierten Datenquellen
* Aufrufen von Datenquellen-Serivices/-vorgängen mithilfe von Regeln für adaptive Formulare
* Schreiben von Daten übermittelten adaptiven Formulardaten in Datenquellen

## Anwendbarkeit und Anwendungsfälle

### Versicherung

## Kann AEM Forms für Anwendungen von Versicherungspolicen verwendet werden?

Ja. AEM Forms kann verwendet werden, um digitale Versicherungsformulare zu erstellen, die Bewerberinformationen erfassen, Eingaben validieren und mit Backend-Underwriting-Systemen integrieren.

## Unterstützt AEM Forms Underwriting-Workflows?

Ja, mit Workflows und Integrationen. AEM Forms unterstützt Workflow-gesteuerte Prozesse und Backend-Integrationen, die es Anwendungsdaten ermöglichen, in Underwriting- und Entscheidungssysteme zu fließen.

## Kann AEM Forms mit Versicherungs-Kernsystemen integriert werden?

Ja. AEM Forms unterstützt die Integration mithilfe von REST- und SOAP-APIs und ermöglicht so die Verbindung zu Richtlinienverwaltungssystemen, Schadenregulierungssystemen und CRMs.

## Kann AEM Forms Formulardaten zurück in Versicherungssysteme schreiben?

Ja. AEM Forms unterstützt das Zurückschreiben von Daten an Backend-Systeme im Rahmen der Formularübermittlung und der Workflow-Ausführung.

## Erste Schritte mit der Datenintegration {#get-started-with-data-integration}

Der erste Schritt zur Implementierung der Datenintegration zum Senden des adaptiven Formulars an eine Datenbank besteht darin, Datenquellen zu identifizieren und zu konfigurieren, in denen Informationen gespeichert werden, die Sie in adaptiven Formularen verwenden möchten. Als Nächstes erstellen Sie ein Formulardatenmodell (FDM), das Datenmodellobjekte, Eigenschaften und Services aus mindestens einer Datenquelle verwendet. Sie können adaptive Formulare auf Grundlage eines Formulardatenmodells (FDM) erstellen, bei dem adaptive Formularfelder an die entsprechenden Datenquelleneigenschaften gebunden sind.

Mit [!DNL AEM Forms] können Sie auch ein von Datenquellen unabhängiges Formulardatenmodell (FDM) erstellen und später Datenmodellobjekte und Eigenschaften im Formulardatenmodell (FDM) mit der Datenquelle verknüpfen oder sie daran binden. Dadurch werden alle Abhängigkeiten von Datenquellen entfernt, während Sie an einem Formulardatenmodell (FDM) arbeiten.

Lesen Sie folgende Informationen für die ersten Schritte mit der Datenintegration, um sie zu verstehen und zu implementieren:

* [Konfigurieren von Datenquellen](configure-data-sources.md)
* [Erstellen eines Formulardatenmodells (FDM)](create-form-data-models.md)
* [Arbeiten mit einem Formulardatenmodell (FDM)](work-with-form-data-model.md)
* [Verwenden eines Formulardatenmodells (FDM)](using-form-data-model.md)

<!--

>[!NOTE]
>
>[!UICONTROL Experience Manager Forms] does not support relational database.

-->