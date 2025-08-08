---
title: Integrieren des Formulardatenmodells (FDM) für ein Formular mit einem adaptiven Formular
description: Erfahren Sie, wie Sie Formulare basierend auf einem Formulardatenmodell (FDM) zu erstellen. Erstellen und bearbeiten Sie Beispieldaten für Datenmodellobjekte im FDM.
feature: Edge Delivery Services, Adaptive Forms, Form Data Model
role: Admin, User
source-git-commit: 62134c5b67d610f801c407e696e761ed05e02c87
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 31%

---

# Integrieren von Formularen in das Formulardatenmodell

Durch die Integration von Formularen mit einem Formulardatenmodell (FDM) können Sie verschiedene Backend-Datenquellen verwenden, um ein Formulardatenmodell (FDM) zu erstellen. Sie können das Formulardatenmodell (FDM) als Schema in verschiedenen Formular-Workflows verwenden. Konfigurieren Sie die Datenquellen und erstellen Sie ein Formulardatenmodell (FDM) basierend auf den Datenmodellobjekten und Diensten, die in den Datenquellen verfügbar sind. 

## Vorteile der Integration von Forms mit dem Formulardatenmodell (FDM)

* **Nahtlose Backend-Konnektivität**: Verbinden von Formularen mit verschiedenen Backend-Systemen (z. B. Datenbanken, REST-APIs, SOAP-Services, CRMs) ohne benutzerdefinierten Code. Dies ermöglicht den Datenaustausch in Echtzeit und reduziert den Integrationsaufwand.
* **Zentralisiertes Datenschema** Das Formulardatenmodell dient als einheitliches Datenschema, das die Zuordnung und Verwaltung von Datenobjekten und Services vereinfacht, die in mehreren Formularen und Workflows verwendet werden.

* **Verbessertes Vorbefüllen und Senden von Formularen**: Einfaches Konfigurieren von Vorbefüllen und Übermitteln mithilfe von Formulardatendiensten, um sicherzustellen, dass die Daten korrekt und aktuell abgerufen und gespeichert werden.

* **Unterstützung dynamischer Workflows**: Das Formulardatenmodell kann in Workflows integriert werden, um Geschäftsprozesse auf der Grundlage gesendeter oder abgerufener Daten zu automatisieren und so die Gesamteffizienz zu verbessern.

## Voraussetzungen

Bevor Sie Ihr Formular mit dem Formulardatenmodell konfigurieren, stellen Sie sicher, dass Sie die folgenden Schritte ausgeführt haben:

* [Konfigurieren der Datenquelle](/help/forms/configure-data-sources.md): Richten Sie die Datenquelle so ein, dass Ihr Formular mit Backend-Daten verbunden wird.
* [Erstellen eines Formulardatenmodells (FDM)](/help/forms/create-form-data-models.md): Erstellen Sie ein Datenmodell mithilfe von Datenobjekten und Diensten aus der konfigurierten Datenquelle.
* [Konfigurieren von Datenmodellobjekten und Diensten](/help/forms/work-with-form-data-model.md): Ordnen Sie die Datenmodellobjekte und Dienste zu, um einen reibungslosen Datenfluss zwischen dem Formular und der Datenquelle sicherzustellen.

>[!BEGINTABS]

>[!TAB Foundation-Komponente]

Führen Sie die folgenden Schritte aus, um das Formulardatenmodell mit einem auf der Foundation-Komponente basierenden adaptiven Formular zu konfigurieren:

1. Öffnen Sie das adaptive Formular zur Bearbeitung und navigieren Sie zum Abschnitt **[!UICONTROL Übermittlung]** der Eigenschaften des Containers für adaptive Formulare.
1. Wählen Sie aus **[!UICONTROL Dropdown]** Liste „Übermittlungsaktion“ die Option **[!UICONTROL Senden mit Formulardatenmodell]**.

   ![Senden mit Formulardatenmodell](/help/forms/assets/submit-uisng-fdm-fc.png)

1. Wählen Sie die erstellte Konfiguration **[!UICONTROL Datenmodell zum Senden]** aus.
Um Anhänge an die Datenbank zu senden, wählen Sie **Formularanhänge übermitteln**. Das Datensatzdokument (DoR) wird in der Datenbank gespeichert, indem Sie **Datensatzdokument senden** auswählen.
1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Sendeeinstellungen zu speichern.

>[!TAB Kernkomponente]

Führen Sie die folgenden Schritte aus, um das Formulardatenmodell basierend auf der Kernkomponente mit einem adaptiven Formular zu konfigurieren:

1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Übermittlung]**.
1. Wählen Sie aus **[!UICONTROL Dropdown]** Liste „Übermittlungsaktion“ die Option **[Senden mit Formulardatenmodell]**.

   ![Senden mit Formulardatenmodell](/help/forms/assets/submit-uisng-fdm-cc.png)

1. Wählen Sie die erstellte Konfiguration **[!UICONTROL Datenmodell zum Senden]** aus.
Um Anhänge an die Datenbank zu senden, wählen Sie **Formularanhänge übermitteln**. Das Datensatzdokument (DoR) wird in der Datenbank gespeichert, indem Sie **Datensatzdokument senden** auswählen.
1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Sendeeinstellungen zu speichern.

>[!TAB Universeller Editor]

Führen Sie die folgenden Schritte aus, um das Formulardatenmodell mit einem adaptiven Formular zu konfigurieren, das in Universal verfasst wurde:

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Klicken Sie im Editor **die Erweiterung** Formulareigenschaften bearbeiten“.

   Das **Formulareigenschaften** wird angezeigt.

   >[!NOTE]
   >
   > * Wenn das Symbol **Formulareigenschaften bearbeiten** in der Benutzeroberfläche des universellen Editors nicht angezeigt wird, aktivieren Sie die Erweiterung **Formulareigenschaften bearbeiten** in der Extension Manager.
   > * Informationen zum Aktivieren oder Deaktivieren von Erweiterungen im universellen Editor finden [ im Artikel ](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)Extension Manager-Feature-Highlights&rbrace;.

1. Klicken Sie auf **Übermittlung** und wählen Sie **[!UICONTROL Senden mit Formulardatenmodell]** aus.

   ![OneDrive GIF](/help/forms/assets/submit-uisng-fdm-ue.png)
Wenn Sie **Anlagen mit Originalnamen speichern** wählen, werden die Anlagen unter Verwendung ihrer Originaldateinamen im Ordner gespeichert. Sie können auch das Datensatzdokument (DoR) im Azure Blob-Speicher speichern.

1. Wählen Sie die **[!UICONTROL Speicherkonfiguration]**, in der Sie Ihre Daten speichern möchten.
1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**

Detaillierte Anweisungen zum Integrieren von im universellen Editor erstellten Formularen finden Sie im Artikel [Integrieren von Forms mit dem Formulardatenmodell im universellen Editor](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md).

>[!ENDTABS]

## Verwandte Artikel

{{af-submit-action}}
