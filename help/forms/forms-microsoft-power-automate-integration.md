---
title: Integrieren eines adaptiven Formulars mit Microsoft® Power Automate
description: Integrieren Sie ein adaptives Formular mit Microsoft Power Automate.
hide: true
hidefromtoc: true
exl-id: a059627b-df12-454d-9e2c-cc56986b7de6
source-git-commit: 7e3eb3426002408a90e08bee9c2a8b7a7bfebb61
workflow-type: tm+mt
source-wordcount: '1171'
ht-degree: 79%

---

# Verbinden eines adaptiven Formulars mit Microsoft® Power Automate {#connect-adaptive-form-with-power-automate}

Sie können ein adaptives Formular so konfigurieren, dass bei der Übermittlung ein Cloud-Fluss bei Microsoft® Power Automate ausgeführt wird. Das konfigurierte adaptive Formular sendet erfasste Daten, Anhänge und das Datensatzdokument zur Verarbeitung an den Cloud-Fluss von Power Automate. Dies hilft Ihnen beim Erstellen benutzerdefinierter Datenerfassungsprozesse und nutzt gleichzeitig die Leistungsfähigkeit von Microsoft® Power Automate, um Geschäftslogiken zu erfassten Daten zu erstellen und Kunden-Workflows zu automatisieren. Im Folgenden finden Sie einige Beispiele dafür, was Sie nach der Integration eines adaptiven Formulars in Microsoft® Power Automate tun können:

* Verwenden Sie Daten von adaptiven Formularen in einem Power Automate-Geschäftsprozess
* Verwenden Sie Power Automate, um erfasste Daten an mehr als 500 Datenquellen oder eine beliebige öffentlich verfügbare API zu senden
* Führen Sie komplexe Berechnungen für erfasste Daten durch
* Speichern Sie die Daten von adaptiven Formularen in Speichersystemen nach einem vordefinierten Zeitplan

Der Editor für adaptive Formulare verfügt über die Übermittlungsaktion **Aufrufen eines Microsoft® Power Automate-Flusses** zum Senden von Daten, Anhängen und Datensatzdokumenten für adaptive Formulare an den Cloud-Fluss von Power Automate. Um mithilfe der Übermittlungsaktion erfasste Daten an Microsoft® Power Automate zu senden, [verbinden Sie Ihre Instanz von Forms as a Cloud Service mit Microsoft® Power Automate](forms-microsoft-power-automate-integration.md#connect-forms-server-with-power-automate).

## Voraussetzungen

Um ein adaptives Formular mit Microsoft® Power Automate zu verbinden, ist Folgendes erforderlich:

* Premium-Lizenz von Microsoft® Power Automate.
* Der Microsoft® [Power Automate-Fluss](https://docs.microsoft.com/de-de/power-automate/create-flow-solution) mit dem `When an HTTP request is received`-Trigger zum Akzeptieren der Übermittlungsdaten für adaptive Formulare.
* Ein Experience Manager mit [Forms Author](/help/forms/forms-groups-privileges-tasks.md) und [Forms Admin](/help/forms/forms-groups-privileges-tasks.md) permissions
* Konto, das für die Verbindung mit Microsoft® Power Automate verwendet wird, ist Eigentümer des Stromautomatisierungsflusses, der für den Empfang von Daten aus dem adaptiven Formular konfiguriert ist.


## Verbinden Ihrer Instanz von Forms as a Cloud Service mit Microsoft® Power Automate {#connect-forms-server-with-power-automate}

Führen Sie die folgenden Schritte aus, um Ihre Instanz von Forms as a Cloud Service mit Microsoft® Power Automate zu verbinden:

1. [Erstellen einer Microsoft](#ms-power-automate-application)
1. [Microsoft erstellen](#microsoft-power-automate-dataverse-cloud-configuration)
1. [Microsoft erstellen](#create-microsoft-power-automate-flow-cloud-configuration)
1. [Microsoft veröffentlichen](#publish-microsoft-power-automate-dataverse-cloud-configuration)

### Erstellen einer Microsoft® Azure Active Directory-Anwendung {#ms-power-automate-application}

1. Melden Sie sich beim [Azure Portal](https://portal.azure.com/) an.
1. Wählen Sie in der linken Navigationsleiste die Option [!UICONTROL Azure Active Directory].
1. Wählen Sie auf der Seite „Standardverzeichnis“ aus dem linken Bereich die Option [!UICONTROL App-Registrierungen].
1. Klicken Sie auf der Seite „App-Registrierungen“ auf „Neue Registrierungen“.
1. Geben Sie auf der Seite den Namen, die unterstützten Kontotypen und den Umleitungs-URI an. Geben Sie im Umleitungs-URI Folgendes an und klicken Sie auf „Speichern“.
   * `https://[Forms as a Cloud Service Server]/libs/fd/powerautomate/content/dataverse/config.html`
   * `https://[Forms as a Cloud Service Server]/libs/fd/powerautomate/content/flowservice/config.html`

   ![Registrieren einer Azure Active Directory-Anwendung](assets/power-automate-application.png)

   >[!NOTE]
   >Sie können auf der Seite „Authentifizierung“ bei Bedarf auch zusätzliche Umleitungs-URIs angeben.
   > Wählen Sie für unterstützte Kontotypen je nach Anwendungsfall einen einzelnen Mandanten, mehrere Mandanten oder ein persönliches Microsoft®-Konto aus.


1. Aktivieren Sie auf der Seite „Authentifizierung“ die folgenden Optionen und klicken Sie auf „Speichern“.


   * Zugriffs-Token (für implizite Flüsse verwendet)
   * ID-Token (für implizite und hybride Flüsse verwendet)

1. Klicken Sie auf der Seite mit den API-Berechtigungen auf „Berechtigung hinzufügen“.
1. Wählen Sie unter den Microsoft® APIs den Flow Service und dann die folgenden Berechtigungen aus.
   * Flows.Manage.All
   * Flows.Read.All

   Klicken Sie auf „Berechtigungen hinzufügen“, um die Berechtigungen zu speichern.
1. Klicken Sie auf der Seite mit den API-Berechtigungen auf „Berechtigung hinzufügen“. Wählen Sie „APIs, die meine Organisation verwendet“ und suchen Sie nach `DataVerse`.
1. Aktivieren Sie „user_impersonation“ und klicken Sie auf „Berechtigungen hinzufügen“.
1. (Optional) Klicken Sie auf der Seite „Zertifikate und geheime Schlüssel“ auf „Neuer geheimer Client-Schlüssel“. Geben Sie im Bildschirm „Geheimen Client-Schlüssel hinzufügen“ eine Beschreibung und einen Zeitraum ein, nach dem das Geheimnis ablaufen soll, und klicken Sie auf „Hinzufügen“. Es wird eine geheime Zeichenfolge generiert.
1. Notieren Sie sich Ihre organisationsspezifischen [URL der Dynamics-Umgebung](https://docs.microsoft.com/de-de/power-automate/web-api#compose-http-requests).

### Erstellen einer Cloud-Konfiguration des Microsoft® Power Automate Dataverse {#microsoft-power-automate-dataverse-cloud-configuration}

1. Navigieren Sie auf der AEM Forms-Autoreninstanz zu **[!UICONTROL Tools]** ![hammer](assets/hammer.png) > **[!UICONTROL Allgemein]** > **[!UICONTROL Konfigurations-Browser]**.
1. Tippen Sie auf der Seite **[!UICONTROL Konfigurations-Browser]** auf **[!UICONTROL Erstellen]**.
1. Legen Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen **[!UICONTROL Titel]** für die Konfiguration fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**. Anschließend tippen Sie auf **[!UICONTROL Erstellen]**. Es wird ein Konfigurations-Container für Cloud Services erstellt. Stellen Sie sicher, dass der Ordnername keine Leerzeichen enthält.
1. Navigieren Sie zu **[!UICONTROL Tools]** ![Hammersymbol](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® Power Automate Dataverse]** und öffnen Sie den Konfigurations-Container, den Sie im vorherigen Schritt erstellt haben.


   >[!NOTE]
   >
   Wenn Sie ein adaptives Formular erstellen, geben Sie den Namen des Containers im Feld **[!UICONTROL Konfigurations-Container]** an.

1. Tippen Sie auf der Konfigurationsseite auf **[!UICONTROL Erstellen]**, um die [!DNL Microsoft®® Power Automate Flow Service]-Konfiguration in AEM Forms zu erstellen.
1. Im **[!UICONTROL Konfigurieren des Datenversand-Dienstes für Microsoft® Power Automated]** Seite, geben Sie die **[!UICONTROL Client-ID]** (auch als Bewerbungs-ID bezeichnet), **[!UICONTROL Client Secret]**, **[!UICONTROL OAuth-URL]** und **[!UICONTROL URL der dynamischen Umgebung]**. Verwenden Sie die Client-ID, den geheimen Client-Schlüssel, die OAuth-URL und die URL der Dynamics-Umgebung der [Microsoft® Azure Active Directory-Anwendung](#ms-power-automate-application), die Sie im vorherigen Abschnitt erstellt haben. Verwenden Sie die Option „Endpunkte“ in der Benutzeroberfläche der Microsoft® Azure Active Directory-Anwendung, um die OAuth-URL zu finden.

   ![Option &quot;Endpunkte verwenden&quot;in der Benutzeroberfläche der Microsoft Power Automate-Anwendung, um OAuth-URL zu finden](assets/endpoints.png)

1. Tippen Sie auf **[!UICONTROL Verbinden]**. Wenn Sie dazu aufgefordert werden, melden Sie sich bei Ihrem Microsoft® Azure-Konto an. Tippen Sie auf **[!UICONTROL Speichern]**.

### Erstellen Sie eine Cloud-Konfiguration für den Microsoft® Power Automate Flow Service {#create-microsoft-power-automate-flow-cloud-configuration}

1. Navigieren Sie zu **[!UICONTROL Instrumente]** ![Hammer](assets/hammer.png) > **[!UICONTROL Cloud Service]** > **[!UICONTROL Microsoft® Power Automated Flow Service]** und öffnen Sie den Konfigurationscontainer, den Sie im vorherigen Abschnitt erstellt haben.


   >[!NOTE]
   >
   Wenn Sie ein adaptives Formular erstellen, geben Sie den Namen des Containers im Feld **[!UICONTROL Konfigurations-Container]** an.

1. Tippen Sie auf der Konfigurationsseite auf **[!UICONTROL Erstellen]**, um die [!DNL Microsoft®® Power Automate Flow Service]-Konfiguration in AEM Forms zu erstellen.
1. Im **[!UICONTROL Konfigurieren von Datenquellen für Microsoft® Power Automated]** Seite, geben Sie die **[!UICONTROL Client-ID]** (auch als Bewerbungs-ID bezeichnet), **[!UICONTROL Client Secret]**, **[!UICONTROL OAuth-URL]** und **[!UICONTROL URL der dynamischen Umgebung]**. Verwenden Sie die Client-ID, den geheimen Client-Schlüssel, die OAuth-URL und die ID der Dynamics-Umgebung. Verwenden Sie die Option „Endpunkte“ in der Benutzeroberfläche der Microsoft® Azure Active Directory-Anwendung, um die OAuth-URL zu finden. Öffnen Sie den Link [Meine Flüsse](https://powerautomate.microsoft.com/de-de/), tippen Sie auf „Meine Flüsse“ und verwenden Sie die in „URL als Dynamics-Umgebungs-ID“ aufgeführte ID.
1. Tippen Sie auf **[!UICONTROL Verbinden]**. Wenn Sie dazu aufgefordert werden, melden Sie sich bei Ihrem Microsoft® Azure-Konto an. Tippen Sie auf **[!UICONTROL Speichern]**.

### Veröffentlichen Sie sowohl die Cloud-Konfigurationen des Microsoft® Power Automate Dataverse als auch des Microsoft® Power Automate Flow Service. {#publish-microsoft-power-automate-dataverse-cloud-configuration}

1. Navigieren Sie zu **[!UICONTROL Instrumente]** ![Hammer](assets/hammer.png) > **[!UICONTROL Cloud Service]** > **[!UICONTROL Microsoft® Power Automated Data]** und öffnen Sie den Konfigurationscontainer, den Sie zuvor erstellt haben [Microsoft® Power Automate Data Cloud-Konfiguration erstellen](#microsoft-power-automate-dataverse-cloud-configuration) Abschnitt.
1. Wählen Sie die `dataverse`-Konfiguration und tippen Sie auf **[!UICONTROL Veröffentlichen]**.
1. Wählen Sie auf der Seite „Veröffentlichen“ die Option **[!UICONTROL Alle Konfigurationen]** und tippen Sie auf **[!UICONTROL Veröffentlichen]**. Veröffentlichen Sie sowohl die Cloud-Konfigurationen des Power Automate Dataverse als auch die des Power Automate Flow Service.

Ihre Instanz von Forms as a Cloud Service ist jetzt mit Microsoft® Power Automate verbunden. Sie können jetzt Daten von adaptiven Formularen an einen Power Automate-Fluss senden.

## Verwenden der Übermittlungsaktion „Microsoft® Power Automate-Fluss aufrufen“, um Daten an einen Power Automate-Fluss zu senden {#use-the-invoke-microsoft-power-automate-flow-submit-action}

Nachdem Sie [Ihre Instanz von Forms as a Cloud Service mit Microsoft® Power Automate verbunden haben](#connect-forms-server-with-power-automate), führen Sie die folgende Aktion durch, um Ihr adaptives Formular so zu konfigurieren, dass die erfassten Daten bei der Formularübermittlung an einen Microsoft®-Fluss gesendet werden.

1. Melden Sie sich bei Ihrer Autoreninstanz an, wählen Sie Ihr adaptives Formular aus und klicken Sie auf **[!UICONTROL Eigenschaften]**.
1. Suchen Sie im Konfigurations-Container den im Abschnitt [Erstellen einer Cloud-Konfiguration des Microsoft® Power Automate Dataverse](#microsoft-power-automate-dataverse-cloud-configuration) erstellten Container, wählen Sie ihn aus und tippen Sie auf **[!UICONTROL Speichern und schließen]**.
1. Öffnen Sie das adaptive Formular zur Bearbeitung und navigieren Sie zum Abschnitt **[!UICONTROL Übermittlung]** der Eigenschaften des Containers für adaptive Formulare.
1. Im Eigenschaftencontainer, für **[!UICONTROL Sendeaktionen]** wählen Sie **[!UICONTROL Netzautomatisierungsfluss aufrufen]** und wählen Sie eine **[!UICONTROL Stromautomatisierungsfluss]**. Wählen Sie den erforderlichen Fluss aus, und die Daten von adaptiven Formularen werden bei der Übermittlung übermittelt.

   ![Konfigurieren der Übermittlungsaktion](assets/submission.png)

>[!NOTE]
>
Stellen Sie vor dem Übermitteln des adaptiven Formulars sicher, dass der Trigger `When an HTTP Request is received` mit dem folgenden JSON-Schema zu Ihrem Power Automate-Fluss hinzugefügt wurde.

```
        {
            "type": "object",
            "properties": {
                "attachments": {
                    "type": "array",
                    "items": {
                        "type": "object",
                        "properties": {
                            "filename": {
                                "type": "string"
                            },
                            "data": {
                                "type": "string"
                            },
                            "contentType": {
                                "type": "string"
                            },
                            "size": {
                                "type": "integer"
                            }
                        },
                        "required": [
                            "filename",
                            "data",
                            "contentType",
                            "size"
                        ]
                    }
                },
                "templateId": {
                    "type": "string"
                },
                "templateType": {
                    "type": "string"
                },
                "data": {
                    "type": "string"
                },
                "document": {
                    "type": "object",
                    "properties": {
                        "filename": {
                            "type": "string"
                        },
                        "data": {
                            "type": "string"
                        },
                        "contentType": {
                            "type": "string"
                        },
                        "size": {
                            "type": "integer"
                        }
                    }
                }
            }
        }
```

## Siehe auch,

* [Erstellen eines adaptiven Formulars](creating-adaptive-form-core-components.md)
* [Konfigurieren einer Sendeaktion](configure-submit-actions-core-components.md)
* [Adobe Experience Manager Connector für Microsoft® Power Automate](https://learn.microsoft.com/en-us/connectors/adobeexperiencemanag/)

