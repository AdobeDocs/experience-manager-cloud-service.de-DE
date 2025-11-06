---
title: Wie lassen sich Marketo Engage-Daten für adaptive Formulare konfigurieren?
description: Erfahren Sie, wie Sie das Marketo Engage-Schema in adaptiven Formularen verwenden können.
keywords: Verwenden einer Marketo Engage-Datenquelle in adaptiven Formularen, Verbinden einer Marketo-Instanz-Datenquelle mit einem Formular, Formular mit Marketo verbinden.
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 4656ec65-f1ad-4e97-8d93-25933cdc7f7b
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 100%

---

# Konfigurieren von Marketo Engage-Datenquellen für vorhandene adaptive Formulare

<span class="preview"> Die Funktion ist im Rahmen des Early-Adopter-Programms verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

![Workflow](/help/forms/assets/workflow-marketo-2.png)

Nachdem Sie die Cloud-Service-Konfiguration erstellt haben, um Marketo Engage mit einer vorhandenen AEM Forms-Version zu integrieren, können Sie die Datenquelle für Formulare konfigurieren.

Durch die Konfiguration der Datenintegration können Benutzende eine Verbindung zu verschiedenen Datenquellen oder Schemata herstellen. Die Integration mit der Marketo Engage-Datenquelle und deren Verwendung in verschiedenen Formularen vereinfacht Vorgänge bei diesen Daten. Die unterstützten vorkonfigurierten Datenquellen für ein adaptives Formular finden Sie im Artikel [Konfigurieren von Datenquellen](/help/forms/configure-data-sources.md).

## Voraussetzung zur Verwendung der Marketo Engage-Datenquelle für Formulare

Voraussetzung zur Verwendung der Marketo Engage-Datenquelle mit Formularen:

* Erstellen Sie die [Cloud-Service-Konfiguration, um Marketo Engage mit Formularen zu integrieren](/help/forms/integrate-form-to-marketo-engage.md).

## Konfigurieren eines vorhandenen adaptiven Formulars für eine Marketo Engage-Datenquelle

>[!VIDEO](https://video.tv.adobe.com/v/3442871/marketo-aem-forms-aem-marketo-engage)

<span> Dieses Video gilt nur für Kernkomponenten. Informationen zu UE/Foundation-Komponenten finden Sie im Artikel.</span>

>[!BEGINTABS]

>[!TAB Foundation-Komponente]

Führen Sie die folgenden Schritte aus, um ein auf Foundation-Komponenten basierendes adaptives Formular mit der Marketo Engage-Datenquelle zu konfigurieren:

1. Melden Sie sich bei Ihrer [!DNL Experience Manager Forms]-Autoreninstanz an.
1. Öffnen Sie das adaptive Formular zur Bearbeitung, navigieren Sie in den Eigenschaften des Containers für das adaptive Formular zum Abschnitt **[!UICONTROL Datenmodell]** und wählen Sie ein Formularmodell als **Connector** aus.
1. Wählen Sie den **[!UICONTROL Connector]** aus der Dropdown-Liste aus.
1. Nach Auswahl des **[!UICONTROL Connectors]** können Sie die Cloud-Konfiguration auswählen.

   ![Auswählen des Marketo-Connectors](/help/forms/assets/select-marketo-connector-af1.png){width=50%, height=50%}

   Je nach ausgewählter Marketo Engage-Konfiguration werden die Formularelemente auf der Registerkarte **[!UICONTROL Datenmodellobjekte]** des **[!UICONTROL Inhalts-Browsers]** in der Seitenleiste angezeigt. Sie können diese Elemente per Drag-and-Drop in das zu erstellende adaptive Formular ziehen.

   ![Marketo-Datenquelle](/help/forms/assets/marketo-engage-data-source-af1.png){width=50%, height=50%}

1. Klicken Sie auf **[!UICONTROL Fertig]**.

Alternativ können Sie auch die Eigenschaften des adaptiven Formulars bearbeiten, um die zugehörige Konfiguration zu ändern.

Das adaptive Formular ist nun mit der Datenquelle aus der verbundenen Marketo Engage-Instanz konfiguriert. Konfigurieren Sie es jetzt so, dass Daten an Adobe Marketo Engage gesendet werden.

>[!TAB Kernkomponente]

Führen Sie die folgenden Schritte aus, um ein auf Kernkomponenten basierendes adaptives Formular mit der Marketo Engage-Datenquelle zu konfigurieren:

1. Melden Sie sich bei Ihrer [!DNL Experience Manager Forms]-Autoreninstanz an.

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Guide-Container]**.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ zum Konfigurieren der Datenquelle wird geöffnet.
1. Öffnen Sie die Registerkarte **[!UICONTROL Datenmodell]** und wählen Sie ein Formularmodell als **Connector** aus.
1. Wählen Sie den **[!UICONTROL Connector]** aus der Dropdown-Liste aus.

1. Nach Auswahl des **[!UICONTROL Connectors]** können Sie die Cloud-Konfiguration auswählen.

   ![Auswählen des Marketo-Connectors](/help/forms/assets/select-marketo-connector.png){width=50%, height=50%}

   Je nach ausgewählter Marketo Engage-Konfiguration werden die Formularelemente auf der Registerkarte **[!UICONTROL Datenmodellobjekte]** des **[!UICONTROL Inhalts-Browsers]** in der Seitenleiste angezeigt. Sie können diese Elemente per Drag-and-Drop in das zu erstellende adaptive Formular ziehen.

   ![Marketo-Datenquelle](/help/forms/assets/marketo-engage-data-source.png){width=50%, height=50%}

1. Klicken Sie auf **[!UICONTROL Fertig]**.

Alternativ können Sie auch die Eigenschaften des adaptiven Formulars bearbeiten, um die zugehörige Konfiguration zu ändern.

Das adaptive Formular ist nun mit der Datenquelle aus der verbundenen Marketo Engage-Instanz konfiguriert. Konfigurieren Sie es jetzt so, dass Daten an Adobe Marketo Engage gesendet werden.

>[!TAB Universeller Editor]

Führen Sie die folgenden Schritte aus, um ein im universellen Editor erstelltes adaptives Formular mit der Marketo Engage-Datenquelle zu konfigurieren:

1. Öffnen Sie die Eigenschaften des Formulars zum Bearbeiten. 
1. Wählen Sie das **[!UICONTROL Formularmodell]** aus.
1. Wählen Sie **Connector** im **[!UICONTROL Formularmodell]** aus.
1. Nach Auswahl des **[!UICONTROL Connectors]** können Sie die Cloud-Konfiguration auswählen.

   ![Auswählen des Marketo-Connectors](/help/forms/assets/select-marketo-connector-ue.png)

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

Je nach ausgewählter Marketo Engage-Konfiguration werden die Formularelemente auf der Registerkarte **[!UICONTROL Datenquelle]** des Inhalts-Browsers im Panel „Eigenschaften“ angezeigt. Sie können diese Elemente per Drag-and-Drop in das zu erstellende adaptive Formular ziehen.

![Marketo-Datenquelle](/help/forms/assets/marketo-engage-data-source-ue.png)

Das Formular ist nun mit der Datenquelle aus der verbundenen Marketo Engage-Instanz konfiguriert. Konfigurieren Sie es jetzt so, dass Daten an Adobe Marketo Engage gesendet werden.

>[!ENDTABS]

## Häufig gestellte Fragen (FAQs)

**F: Was passiert, wenn Sie den Connector des Formulars ändern?**\
**A:** Wenn Sie den Connector des Formulars ändern, werden die vorhandenen Bindungen ungültig.

**F: Welche drei Vorgänge sind im Aufruf-Service des Regeleditors für Formulare verfügbar, die in Marketo Engage integriert sind?**

**A:** Die drei folgenden vorkonfigurierten Vorgänge sind im **Aufruf-Service** für Formulare verfügbar, die in Marketo Engage integriert sind:

* Lead synchronisieren
* Lead nach ID abrufen
* Lead nach Filtertyp abrufen

## Nächster Schritt

Nun haben Sie die Marketo Engage-Datenquelle für adaptive Formulare konfiguriert. Als Nächstes können Sie [ein adaptives Formular zum Senden von Daten an Marketo Engage konfigurieren](/help/forms/submit-adaptive-form-to-marketo-engage.md).

## Verwandte Artikel

{{af-submit-action}}

## Siehe auch

{{marketo-engage-see-also}}
