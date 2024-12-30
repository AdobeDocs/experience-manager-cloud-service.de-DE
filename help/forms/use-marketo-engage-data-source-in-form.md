---
Title: How to configure Marketo Engage data for Adaptive Forms?
Description: Learn how to use Marketo Engage schema in Adaptive Forms.
Keywords: Use Marketo Engage data source in Adaptive Forms, How to connect a Marketo instance data source with form? , Connect a form to Marketo.
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
exl-id: 4656ec65-f1ad-4e97-8d93-25933cdc7f7b
source-git-commit: 10de700e5e4b352051b8b77dfd0825bb9b6e0219
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 17%

---

# Konfigurieren von Marketo Engage-Datenquellen für vorhandene adaptive Formulare

<span class="preview"> Die Funktion ist im Rahmen des Early-Adopter-Programms verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

![Arbeitsablauf](/help/forms/assets/workflow-marketo-2.png)

Nachdem Sie die Cloud Service-Konfiguration erstellt haben, um Marketo Engage in bestehende AEM Forms zu integrieren, können Sie die Datenquelle für Forms konfigurieren.

Durch die Konfiguration der Datenintegration können Benutzer eine Verbindung zu verschiedenen Datenquellen oder Schemata herstellen. Die Integration mit der Marketo Engage-Datenquelle und deren Verwendung in verschiedenen Formularen erleichtert Vorgänge bei diesen Daten. Die unterstützten vordefinierten Datenquellen für ein adaptives Formular finden Sie im Artikel [Konfigurieren von Datenquellen](/help/forms/configure-data-sources.md) .

## Überlegungen zum Konfigurieren der Marketo Engage-Datenquelle für Formulare

Beim Konfigurieren einer Marketo Engage-Datenquelle für Formulare sind folgende Aspekte zu berücksichtigen:

* Es ist nicht möglich, Edge Delivery Services Forms mit Marketo Engage zu verbinden.

## Voraussetzung für die Verwendung der Marketo Engage-Datenquelle für Formulare

Voraussetzung für die Verwendung von Marketo Engage-Datenquellen mit Formularen:

* Erstellen Sie die [Cloud-Service-Konfiguration, um Marketo Engage mit Forms zu integrieren](/help/forms/integrate-form-to-marketo-engage.md).

## Konfigurieren eines vorhandenen adaptiven Formulars zum Marketo Engage einer Datenquelle

Um ein adaptives Formular mit der Marketo Engage-Datenquelle zu konfigurieren, führen Sie die folgenden Schritte aus:
1. Melden Sie sich bei Ihrer [!DNL Experience Manager Forms]-Autoreninstanz an. 

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Guide-Container]**.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg). Das Dialogfeld Container für adaptive Formulare zum Konfigurieren der Datenquelle wird geöffnet.
1. Öffnen Sie die Registerkarte **[!UICONTROL Datenmodell]** und wählen Sie ein Formularmodell als **Connector** aus.
1. Wählen Sie den **[!UICONTROL Connector]** aus der Dropdown-Liste aus.

1. Nach Auswahl von **[!UICONTROL Connector]** können Sie die Cloud-Konfiguration auswählen.

   ![Marketo-Connector auswählen](/help/forms/assets/select-marketo-connector.png)

   Basierend auf der ausgewählten Marketo Engage-Konfiguration werden die Formularelemente auf der Registerkarte **[!UICONTROL Datenmodellobjekte]** des **[!UICONTROL Inhaltsbrowsers]** in der Seitenleiste angezeigt. Sie können diese Elemente per Drag-and-Drop in das zu erstellende adaptive Formular ziehen.

   ![Marketo Data Source](/help/forms/assets/marketo-engage-data-source.png)

1. Klicken Sie auf **[!UICONTROL Fertig]**.

Alternativ können Sie auch die Eigenschaften des adaptiven Formulars bearbeiten, um die zugehörige Konfiguration zu ändern.

Das adaptive Formular ist jetzt mit der Datenquelle aus der verbundenen Marketo Engage-Instanz konfiguriert. Konfigurieren Sie ihn jetzt so, dass Daten an Adobe Marketo Engage gesendet werden.

## Häufig gestellte Fragen (FAQ)

**F: Was passiert, wenn Sie den Connector des Formulars ändern?**\
**A:** Wenn Sie den Connector des Formulars ändern, werden die vorhandenen Bindungen ungültig.

**F: Welche drei Vorgänge sind im Aufrufdienst des Regeleditors für Formulare verfügbar, die in Marketo Engage integriert sind?**\
**A:** Im Abschnitt „Service aufrufen“ stehen für Formulare, die in **Marketo Engage integriert sind** drei vorkonfigurierte Vorgänge zur Verfügung:
* Lead synchronisieren
* Lead nach ID abrufen
* Lead nach Filtertyp abrufen

## Nächster Schritt

Jetzt haben Sie die Marketo Engage-Datenquelle für das adaptive Forms konfiguriert. Als Nächstes können Sie [ein adaptives Formular konfigurieren, um Daten an Marketo Engage zu senden](/help/forms/submit-adaptive-form-to-marketo-engage.md).

## Verwandte Artikel

{{af-submit-action}}

## Siehe auch

{{marketo-engage-see-also}}
