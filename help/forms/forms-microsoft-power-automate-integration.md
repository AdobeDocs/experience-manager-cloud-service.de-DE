---
title: Integrieren eines adaptiven Formulars mit Microsoft® Power Automate
description: Integrieren Sie ein adaptives Formular in Microsoft® Power Automate.
hide: true
hidefromtoc: true
exl-id: a059627b-df12-454d-9e2c-cc56986b7de6
source-git-commit: 27aa5016d6bdc4a101ba044bf9e49c483ecdae13
workflow-type: tm+mt
source-wordcount: '1197'
ht-degree: 9%

---

# Verbinden eines adaptiven Formulars mit Microsoft® Power Automate {#connect-adaptive-form-with-power-automate}

>[!NOTE]
>
>Die Funktion befindet sich im Vorabversionsprogramm und kann sich vor der Veröffentlichung erheblich ändern.

Sie können ein adaptives Formular so konfigurieren, dass bei der Übermittlung ein Microsoft® Power Automate Cloud-Fluss ausgeführt wird. Das konfigurierte adaptive Formular sendet erfasste Daten, Anhänge und Datensatzdokument zur Verarbeitung an Power Automate Cloud Flow zur Verarbeitung. Dies hilft Ihnen beim Erstellen benutzerdefinierter Datenerfassungserlebnisse und nutzt gleichzeitig die Leistungsfähigkeit von Microsoft® Power Automate, um Geschäftslogiken zu erfassten Daten zu erstellen und Kundenworkflows zu automatisieren. Im Folgenden finden Sie einige Beispiele dafür, was Sie nach der Integration eines adaptiven Formulars in Microsoft® Power Automate tun können:

* Verwenden adaptiver Forms-Daten in einem Power Automated-Geschäftsprozess
* Power Automate verwenden, um erfasste Daten an mehr als 500 Datenquellen oder eine öffentlich verfügbare API zu senden
* Komplexe Berechnungen für erfasste Daten durchführen
* Speichern adaptiver Forms-Daten in Speichersystemen nach einem vordefinierten Zeitplan

Der adaptive Forms-Editor stellt die **Aufrufen eines Microsoft® Power Automate-Flusses** Übermittlungsaktion zum Senden von Daten, Anlagen und Datensatzdokumenten für adaptive Formulare werden an Power Automate Cloud Flow gesendet. So senden Sie mit der Übermittlungsaktion erfasste Daten an Microsoft® Power Automate: [Verbinden Ihrer as a Cloud Service Forms-Instanz mit Microsoft® Power Automate](forms-microsoft-power-automate-integration.md#connect-forms-server-with-power-automate)

## Voraussetzungen

Um ein adaptives Formular mit Microsoft® Power Automate zu verbinden, ist Folgendes erforderlich:

* Microsoft® Power Automate Premium-Lizenz.
* Microsoft® [Stromautomatisierungsfluss](https://docs.microsoft.com/en-us/power-automate/create-flow-solution) mit dem `When an HTTP request is received` Trigger zum Akzeptieren der Übermittlungsdaten für adaptive Formulare.


* Ein Experience Manager mit Forms Author- und Forms Admin-Berechtigungen.
* Stellen Sie sicher, dass das für die Verbindung mit Power Automate verwendete Konto Eigentümer des Stromautomatisierungsflusses ist.


## Verbinden Ihrer as a Cloud Service Forms-Instanz mit Microsoft® Power Automate {#connect-forms-server-with-power-automate}

Führen Sie die folgenden Schritte aus, um Ihre as a Cloud Service Forms-Instanz mit Microsoft® Power Automate zu verbinden:

1. Erstellen einer Microsoft® Azure Active Directory-Anwendung
1. Erstellen Sie eine Microsoft® Power Automate Data Cloud-Konfiguration.
1. Erstellen der Cloud-Konfiguration des Microsoft® Power Automate Flow Service
1. Veröffentlichen Sie die Microsoft® Power Automate Data Cloud-Konfiguration.

### Erstellen einer Microsoft® Azure Active Directory-Anwendung {#ms-power-automate-application}

1. Anmelden bei [Azure Portal](https://portal.azure.com/).
1. Auswählen [!UICONTROL Azure Active Directory] über die linke Navigation.
1. Wählen Sie auf der Seite &quot;Standardordner&quot;die Option [!UICONTROL App-Registrierungen] aus dem linken Bereich.
1. Klicken Sie auf der Seite App-Registrierungen auf Neue Registrierungen .
1. Geben Sie den Namen, die unterstützten Kontotypen und den Umleitungs-URI auf der Seite an. Geben Sie im Umleitungs-URI Folgendes an und klicken Sie auf &quot;Speichern&quot;.
   * `https://[Forms as a Cloud Service Server]/libs/fd/powerautomate/content/dataverse/config.html`
   * `https://[Forms as a Cloud Service Server]/libs/fd/powerautomate/content/flowservice/config.html`

   ![Registrieren einer Azure Active Directory-Anwendung](assets/power-automate-application.png)

   >[!NOTE]
   >Sie können bei Bedarf auch zusätzliche Umleitungs-URIs auf der Seite &quot;Authentifizierung&quot;angeben.
   > Wählen Sie für unterstützte Kontotypen je nach Anwendungsfall einen einzelnen Mandanten, mehrere Mandanten oder ein persönliches Microsoft-Konto aus.


1. Aktivieren Sie auf der Seite &quot;Authentifizierung&quot;die folgenden Optionen und klicken Sie auf &quot;Speichern&quot;.


   * Zugriffstoken (für implizite Flüsse verwendet)
   * ID-Token (für implizite und hybride Flüsse verwendet)

1. Klicken Sie auf der Seite mit den API-Berechtigungen auf Berechtigung hinzufügen .
1. Wählen Sie unter &quot;Microsoft® APIs&quot;den Flussdienst und dann die folgenden Berechtigungen aus.
   * Flows.Manage.All
   * Flows.Read.All

   Klicken Sie auf Berechtigungen hinzufügen , um die Berechtigungen zu speichern.
1. Klicken Sie auf der Seite mit den API-Berechtigungen auf Berechtigung hinzufügen . APIs auswählen, die mein Unternehmen verwendet und durchsucht `DataVerse`.
1. Aktivieren Sie &quot;user_impersonation&quot;und klicken Sie auf &quot;Berechtigungen hinzufügen&quot;.
1. (Optional) Klicken Sie auf der Seite &quot;Zertifikate und Geheimnisse&quot;auf Neues Client-Geheimnis. Geben Sie im Bildschirm &quot;Client-Geheimnis hinzufügen&quot;eine Beschreibung und einen Zeitraum ein, nach dem das Geheimnis ablaufen soll, und klicken Sie auf Hinzufügen . Es wird eine geheime Zeichenfolge generiert.
1. Hinweis zu organisationsspezifischen [URL der Dynamics-Umgebung](https://docs.microsoft.com/en-us/power-automate/web-api#compose-http-requests).

### Microsoft® Power Automate Data Cloud-Konfiguration erstellen {#microsoft-power-automate-dataverse-cloud-configuration}

1. Navigieren Sie auf der AEM Forms-Autoreninstanz zu **[!UICONTROL Tools]** ![hammer](assets/hammer.png) > **[!UICONTROL Allgemein]** > **[!UICONTROL Konfigurations-Browser]**.
1. Tippen Sie auf der Seite **[!UICONTROL Konfigurations-Browser]** auf **[!UICONTROL Erstellen]**.
1. Legen Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen **[!UICONTROL Titel]** für die Konfiguration fest und aktivieren Sie **[!UICONTROL Cloud-Konfigurationen]**. Anschließend tippen Sie auf **[!UICONTROL Erstellen]**. Es wird ein Konfigurations-Container für Cloud Services erstellt. Stellen Sie sicher, dass der Ordnername keine Leerzeichen enthält.
1. Navigieren Sie zu **[!UICONTROL Instrumente]** ![Hammer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® Power Automated Data]** und öffnen Sie den Konfigurationscontainer, den Sie im vorherigen Schritt erstellt haben.

   >[!NOTE]
   >
   >Wenn Sie ein adaptives Formular erstellen, geben Sie den Namen des Containers im Feld **[!UICONTROL Konfigurations-Container]** an.
1. Tippen Sie auf der Konfigurationsseite auf **[!UICONTROL Erstellen]**, um die [!DNL Microsoft® Power Automate Flow Service]-Konfiguration in AEM Forms zu erstellen.
1. Im **[!UICONTROL Konfigurieren des Datenaustauschdienstes für Microsoft® Power Automated]** Seite, geben Sie die **[!UICONTROL Client-ID]** (auch als Bewerbungs-ID bezeichnet), **[!UICONTROL Client Secret]**, **[!UICONTROL OAuth-URL]** und **[!UICONTROL URL der dynamischen Umgebung]**. Verwenden Sie die Client-ID, das Client Secret, die OAuth-URL und die dynamische Umgebungs-URL von [Microsoft® Azure Active Directory Application](#ms-power-automate-application) die Sie im vorherigen Abschnitt erstellt haben. Verwenden Sie die Option Endpunkte in der Benutzeroberfläche der Microsoft® Azure Active Directory-Anwendung, um OAuth-URL zu finden.

![Option &quot;Endpunkte verwenden&quot;in der Benutzeroberfläche der Microsoft Power Automate-Anwendung, um OAuth-URL zu finden](assets/endpoints.png)
Option &quot;Endpunkte verwenden&quot;in der Benutzeroberfläche der Microsoft® Power Automate-Anwendung, um OAuth-URL zu finden

1. Tippen **[!UICONTROL Verbinden]** . Melden Sie sich auf Anfrage bei Ihrem Microsoft® Azure-Konto an. Tippen Sie auf **[!UICONTROL Speichern]**.

### Erstellen Sie die Cloud-Konfiguration des Microsoft® Power Automate Flow Service.

1. Navigieren Sie zu **[!UICONTROL Instrumente]** ![Hammer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® Power Automated Flow Service]** und öffnen Sie den Konfigurationscontainer, den Sie im vorherigen Abschnitt erstellt haben.

   >[!NOTE]
   >
   >Wenn Sie ein adaptives Formular erstellen, geben Sie den Namen des Containers im Feld **[!UICONTROL Konfigurations-Container]** an.
1. Tippen Sie auf der Konfigurationsseite auf **[!UICONTROL Erstellen]**, um die [!DNL Microsoft® Power Automate Flow Service]-Konfiguration in AEM Forms zu erstellen.
1. Im **[!UICONTROL Konfigurieren von Daten für Microsoft® Power Automated]** Seite, geben Sie die **[!UICONTROL Client-ID]** (auch als Bewerbungs-ID bezeichnet), **[!UICONTROL Client Secret]**, **[!UICONTROL OAuth-URL]** und **[!UICONTROL URL der dynamischen Umgebung]**. Verwenden Sie die Client-ID, das Client-Geheimnis, die OAuth-URL und die Dynamics-Umgebungs-ID. Verwenden Sie die Option Endpunkte in der Benutzeroberfläche der Microsoft® Azure Active Directory-Anwendung, um OAuth-URL zu finden. Öffnen Sie die [Meine Flüsse](https://us.flow.microsoft.com) verknüpfen und auf Eigene Flüsse tippen, verwenden Sie die in URL als Dynamics-Umgebungs-ID aufgeführte ID.
1. Tippen **[!UICONTROL Verbinden]**. Melden Sie sich auf Anfrage bei Ihrem Microsoft® Azure-Konto an. Tippen Sie auf **[!UICONTROL Speichern]**.

### Veröffentlichen Sie sowohl die Cloud-Konfigurationen des Microsoft® Power Automate DataVersions- als auch des Microsoft® Power Automate Flow Service . {#publish-microsoft-power-automate-dataverse-cloud-configuration}

1. Navigieren Sie zu **[!UICONTROL Instrumente]** ![Hammer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® Power Automated Data]** und öffnen Sie den Konfigurationscontainer, den Sie zuvor erstellt haben [Microsoft® Power Automate Data Cloud-Konfiguration erstellen](#microsoft-power-automate-dataverse-cloud-configuration) Abschnitt.
1. Wählen Sie die `dataverse` Konfiguration und tippen Sie auf **[!UICONTROL Veröffentlichen]**.
1. Wählen Sie auf der Seite Veröffentlichen die Option **[!UICONTROL Alle Konfigurationen]** und tippen **[!UICONTROL Veröffentlichen]**. Veröffentlichen Sie sowohl die Cloud-Konfigurationen Power Automate Dataverse als auch Power Automate Flow Service .

Ihre as a Cloud Service Forms-Instanz ist jetzt mit Microsoft® Power Automate verbunden. Sie können jetzt adaptive Forms-Daten an einen Stromautomatisierungsfluss senden.

## Verwenden Sie die Übermittlungsaktion &quot;Microsoft® Power Automate Flow aufrufen&quot;, um Daten an einen Power Automate Flow zu senden. {#use-the-invoke-microsoft-power-automate-flow-submit-action}

Nach [Verbinden Ihrer as a Cloud Service Forms-Instanz mit Microsoft® Power Automate](#connect-forms-server-with-power-automate)Führen Sie die folgende Aktion aus, um Ihr adaptives Formular so zu konfigurieren, dass erfasste Daten beim Senden des Formulars an einen Microsoft®-Fluss gesendet werden.

1. Melden Sie sich bei Ihrer Autoreninstanz an, wählen Sie Ihr adaptives Formular aus und klicken Sie auf **[!UICONTROL Eigenschaften]**.
1. Suchen Sie im Konfigurations-Container den im Abschnitt erstellten Container und wählen Sie ihn aus. [Microsoft® Power Automate Data Cloud-Konfiguration erstellen](#microsoft-power-automate-dataverse-cloud-configuration)und tippen Sie auf **[!UICONTROL Speichern und schließen]**.
1. Öffnen Sie das adaptive Formular zur Bearbeitung und navigieren Sie zu **[!UICONTROL Einsendung]** Abschnitt der Eigenschaften des Containers für adaptive Formulare.
1. Im Eigenschaftencontainer, für **[!UICONTROL Übermittlungsaktionen]** wählen Sie die **[!UICONTROL Netzautomatisierungsfluss aufrufen]** -Option. Eine Liste der verfügbaren Stromautomatisierungsflüsse wird verfügbar **[!UICONTROL Stromautomatisierungsfluss]** -Option. Wählen Sie den erforderlichen Fluss aus und Adaptive Forms-Daten werden bei der Übermittlung übermittelt.

![Konfigurieren der Übermittlungsaktion](assets/submission.png)

>[!NOTE]
>
> Stellen Sie vor dem Senden des adaptiven Formulars sicher, dass das `When an HTTP Request is received` Trigger mit dem folgenden JSON-Schema wird Ihrem Power Automate-Fluss hinzugefügt.

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

