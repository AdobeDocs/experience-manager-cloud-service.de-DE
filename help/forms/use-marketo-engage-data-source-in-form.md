---
Title: How to configure Marketo Engage data for Adaptive Forms?
Description: Learn how to use Marketo Engage schema in Adaptive Forms.
Keywords: Use Marketo Engage data source in Adaptive Forms, How to connect a Marketo instance data source with form? , Connect a form to Marketo.
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
source-git-commit: 681c194f997ab66f93beedad4eea273614e6797d
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 15%

---


# Marketo Engage-Datenquelle für vorhandene adaptive Forms konfigurieren

<span class="preview"> Die Funktion ist im Rahmen des Early-Adopter-Programms verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

![Arbeitsablauf](/help/forms/assets/workflow-marketo-2.png)

Nachdem Sie die Cloud-Service-Konfiguration erstellt haben, um Marketo Engage in bestehende AEM Forms zu integrieren, können Sie die Datenquelle für Formulare konfigurieren.

Durch die Konfiguration der Datenintegration können Benutzer eine Verbindung zu verschiedenen Datenquellen oder Schemata herstellen. Die Integration in die Marketo Engage-Datenquelle und deren Verwendung in verschiedenen Formularen erleichtern den Betrieb dieser Daten. Informationen zu den unterstützten nativen Datenquellen für ein adaptives Formular finden Sie im Artikel [Konfigurieren von Datenquellen](/help/forms/configure-data-sources.md) .

## Überlegungen zum Konfigurieren der Marketo Engage-Datenquelle für Formulare

Beachten Sie beim Konfigurieren der Marketo Engage-Datenquelle für Formulare Folgendes:

* Es ist nicht möglich, Edge Delivery Services Forms mit Marketo Engage zu verbinden.

## Voraussetzung für die Verwendung der Marketo Engage-Datenquelle für Formulare

Voraussetzung für die Verwendung der Marketo Engage-Datenquelle mit Formularen:

* Erstellen Sie die [Cloud-Service-Konfiguration zur Integration von Marketo Engage in Formulare](/help/forms/integrate-form-to-marketo-engage.md).

## Wie konfiguriere ich ein vorhandenes adaptives Formular für eine Marketo Engage-Datenquelle?

So konfigurieren Sie ein adaptives Formular mit der Marketo Engage-Datenquelle:
1. Melden Sie sich bei Ihrer [!DNL Experience Manager Forms]-Autoreninstanz an. 

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Guide-Container]**.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg). Das Dialogfeld Container für adaptive Formulare zum Konfigurieren der Datenquelle wird geöffnet.
1. Öffnen Sie die Registerkarte **[!UICONTROL Datenmodell]** und wählen Sie ein Formularmodell als **Connector** aus.
1. Wählen Sie den **[!UICONTROL Connector]** aus der Dropdownliste aus.

1. Nachdem Sie den **[!UICONTROL Connector]** ausgewählt haben, können Sie die Cloud-Konfiguration auswählen.

   ![Marketo Connector auswählen](/help/forms/assets/select-marketo-connector.png)

   Basierend auf der ausgewählten Marketo Engage-Konfiguration werden die Formularelemente auf der Registerkarte **[!UICONTROL Datenmodellobjekte]** des **[!UICONTROL Inhaltsbrowsers]** in der Seitenleiste angezeigt. Sie können diese Elemente per Drag-and-Drop verschieben, um Ihr adaptives Formular zu erstellen.

   ![Marketo Data Source](/help/forms/assets/marketo-engage-data-source.png)

1. Klicken Sie auf **[!UICONTROL Fertig]**.

Alternativ können Sie auch die Eigenschaften des adaptiven Formulars bearbeiten, um die zugehörige Konfiguration zu ändern.

Das adaptive Formular wird jetzt mit der Datenquelle aus der verbundenen Marketo Engage-Instanz konfiguriert. Konfigurieren Sie sie nun zum Senden von Daten an Adobe Marketo Engage.

## Häufig gestellte Fragen (FAQ)

**Q: Was passiert, wenn Sie den Connector des Formulars ändern?**\
**A:** Wenn Sie den Connector des Formulars ändern, werden die vorhandenen Bindungen ungültig.

**Q: Welche drei Vorgänge sind im Aufrufdienst des Regeleditors für in Marketo Engage integrierte Formulare verfügbar?**\
**A:** Die drei nativen Vorgänge, die im **Aufrufdienst** für mit Marketo Engage integrierte Formulare verfügbar sind, sind:
* Synchronisierungsleitung
* Lead nach ID abrufen
* Lead nach Filtertyp abrufen

## Nächster Schritt

Jetzt haben Sie die Marketo Engage-Datenquelle für Adaptive Forms konfiguriert. Als Nächstes können Sie [ein adaptives Formular konfigurieren, um Daten an Marketo Engage](/help/forms/submit-adaptive-form-to-marketo-engage.md) zu senden.

## Verwandte Artikel

{{af-submit-action}}

## Siehe auch

{{marketo-engage-see-also}}


