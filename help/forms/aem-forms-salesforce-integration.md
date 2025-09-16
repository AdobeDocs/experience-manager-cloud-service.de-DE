---
title: Integration von Salesforce mithilfe des OAuth 2.0-Client-Anmeldedatenflusses mit AEM Forms?
description: Erfahren Sie, wie Sie Salesforce mithilfe des OAuth 2.0-Client-Anmeldedatenflusses mit AEM Forms integrieren. Es werden Schritte für die Integration von AEM Forms Salesforce angezeigt.
Keywords: Integration of Salesforce using OAuth 2.0 client credential flow, salesforce integration with oauth2 using client credential flow, salesforce and client credential integration, AEM Forms Salesforce integration
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 2c2029ab-6fb4-41a6-846c-175c3a79d921
source-git-commit: 9eb15dda5f56938d686d0b863cb1ffa841f8228b
workflow-type: ht
source-wordcount: '552'
ht-degree: 100%

---

# Integrieren eines adaptiven Formulars mit Salesforce {#configure-salesforce-with-ouath-2.0-client-credential}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/oauth2-client-credentials-flow-for-server-to-server-integration.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Die Integration von Adobe Experience Manager (AEM) Forms mit Salesforce ermöglicht es Unternehmen, Prozesse zu optimieren, indem sie ihre Funktionen zur Formularerstellung und -verwaltung mit der Salesforce-Plattform verbinden. Die Verbindung eines adaptiven Formulars mit Salesforce ermöglicht den nahtlosen Datenaustausch zwischen den beiden Plattformen. Wenn Benutzerinnen und Benutzer Formulare senden, werden die Daten automatisch mit Salesforce synchronisiert. Dadurch wird sichergestellt, dass alle Kundeninformationen innerhalb des Systems aktuell und zentralisiert sind.

Sie können OAuth 2.0-Client-Anmeldeinformationen verwenden, um AEM Forms in die Salesforce-Anwendung zu integrieren. OAuth 2.0-Client-Anmeldeinformationen sind eine standardmäßige und sichere Methode für die direkte Kommunikation ohne Benutzerbeteiligung.

![Workflow beim Festlegen der Kommunikation zwischen AEM Forms und der Salesforce-Anwendung](/help/forms/assets/salesforce-workflow.png)

AEM Forms tauscht die in der Salesforce Connect-Anwendung definierten Client-Anmeldeinformationen (Consumer Key und Consumer Secret) aus, um ein Zugriffs-Token zu erhalten.

AEM as a Cloud Service bietet verschiedene vordefinierte Übermittlungsaktionen für die Verarbeitung von Formularübermittlungen. Weitere Informationen zu diesen Optionen finden Sie im Artikel [Übermittlungsaktion für adaptive Formulare](/help/forms/configure-submit-actions-core-components.md).

Die Verwendung von OAuth 2.0-Client-Anmeldeinformationen für die Authentifizierung hat gegenüber Authorization Code Flow mehrere Vorteile:

* Die Authentifizierung mit OAuth 2.0-Client-Anmeldeinformationen ermöglicht mehr als fünf Verbindungen pro Person.
* Die AEM-Datenquellenkonfiguration arbeitet weiterhin an der Deaktivierung, Zugriffsänderungen und Kennwortaktualisierung für AEM-Benutzende.

## Voraussetzungen {#prerequisites}

Tun Sie Folgendes, bevor Sie die Kommunikation zwischen einer Salesforce-Anwendung und einer AEM-Umgebung einrichten:

* Erstellen Sie eine [mit Salesforce verbundene App mit OAuth 2.0 Client Credential Flow](https://help.salesforce.com/s/articleView?id=sf.connected_app_client_credentials_setup.htm&type=5) sowie eine reine API-Benutzerin bzw. einen reinen API-Benutzer für Ihre Organisation und rufen Sie Consumer Key und Consumer Secret für die App ab.

* Stellen Sie sicher, dass Ihre Swagger-Datei entsprechend den APIs Ihrer Organisation konfiguriert ist. Sie können auch eine [Swagger-Datei komplett neu erstellen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/integrate-with-salesforce/describe-rest-api.html?lang=de), die auf die Nutzung in Ihrer AEM-Umgebung zugeschnitten ist.


## Konfigurieren einer Salesforce-Anwendung mithilfe des OAuth 2.0-Client-Anmeldedatenflusses {#steps-to-create-aem-datasource-configuration}

Führen Sie zum Verbinden des adaptiven Formulars mit der Salesforce-Anwendung mithilfe der Einstellungen des OAuth 2.0-Client-Anmeldedatenflusses folgende Schritte aus:

1. Melden Sie sich bei Ihrer Authoring-Instanz an.
1. Wechseln Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Datenquellen]**.
1. Wählen Sie den Konfigurationsordner aus.
1. Klicken Sie auf **[!UICONTROL Erstellen]** und das Bedienfeld **[!UICONTROL Datenquellenkonfiguration erstellen]** erscheint.
1. Geben Sie den **[!UICONTROL Titel]** an und wählen Sie den **[!UICONTROL Diensttyp]** als **[!UICONTROL RESTful-Dienst]**.
1. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie **[!UICONTROL Swagger Source]** als **[!UICONTROL Datei].**

   >[!NOTE]
   >
   > Sobald die Swagger-Datei ausgewählt ist, werden das Schema, der Host-Name und der Basispfad automatisch ausgefüllt.

1. Laden Sie die erstellte Swagger-Datei von Ihrem lokalen Computer hoch, indem Sie auf **[!UICONTROL Durchsuchen]** klicken.
1. Wählen Sie **[!UICONTROL Authentifizierungstyp]** als **[!UICONTROL OAuth 2.0]** und das Bedienfeld **[!UICONTROL Authentifizierungs-Einstellungen]** erscheint.
1. Wählen Sie den **[!UICONTROL Grant-Typ]** als **[!UICONTROL Client-Anmeldedaten]** aus.
1. Geben Sie die **[!UICONTROL Client-ID]** und das **[!UICONTROL Client-Geheimnis]** an, das Sie von der mit Salesforce verbundenen App erhalten haben.
1. Geben Sie die **[!UICONTROL Zugriffstoken-URL]** im folgenden Format an:
   `https://[MyDomainName].my.salesforce.com/services/oauth2/token`.

   >[!NOTE]
   >
   > Jede Organisation hat einen eigenen, spezifischen Domain-Namen.

1. Klicken Sie auf **[!UICONTROL Verbindung testen]**.
1. Wenn die Verbindung erfolgreich hergestellt wurde, klicken Sie auf die Schaltfläche **[!UICONTROL Erstellen]**.


Nachdem Sie die Salesforce-Anwendung konfiguriert haben, können Sie die Konfiguration beim Erstellen von Formulardatenmodellen verwenden. Weitere Informationen finden Sie unter [Erstellen eines Formulardatenmodells (FDM)](create-form-data-models.md). [Konfigurieren Sie die Formulardatenmodell-Übermittlungsaktion](/help/forms/using-form-data-model.md) für ein adaptives Formular, um Daten an Salesforce-Anwendungen zu senden.

Weitere Informationen zur Erstellung und Verwendung eines Formulardatenmodells (FDM) in Unternehmens-Workflows finden Sie unter [Datenintegration](data-integration.md).

## Ähnliche Artikel

{{af-submit-action}}


