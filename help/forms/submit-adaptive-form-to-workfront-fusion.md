---
title: Integration von Adobe Workfront Fusion mit AEM Forms Submission
description: Mit Adobe Workfront Fusion können Sie sich auf neue Aufgaben konzentrieren, anstatt sich auf sich wiederholende Aufgaben zu konzentrieren. Sie können Adobe Workfront Fusion über die Formularübermittlung mit einem adaptiven Formular verbinden.
keywords: Senden Sie ein adaptives Formular an Adobe Workfront Fusion, Integration von Adobe Workfront Fusion mit AEM Forms Submission, Adobe Workfront Fusion mit AEM Forms, Workfront Fusion mit AEM Forms, Verbinden von Workfront Fusion mit AEM Forms, AEM Forms und Workfront Fusion, Wie verbinden Sie Workfront Fusion mit AEM Forms? Verbinden Sie Workfront Fusion mit einem Formular?
topic-tags: author, developer
feature: Adaptive Forms
role: Admin, User
exl-id: d3efb450-a879-40ae-8958-0040f99bdafc
source-git-commit: 8923bfbb0e46961485ff360c0135ebdde6d8cab3
workflow-type: tm+mt
source-wordcount: '1255'
ht-degree: 4%

---

# Senden eines adaptiven Formulars an Adobe Workfront Fusion

<span class="preview"> Die Funktion ist im Rahmen des Programms für frühe Anwender verfügbar. Sie können von Ihrer offiziellen E-Mail-ID aus an aem-forms-early-adopter-program@adobe.com schreiben, um dem frühen Adopter-Programm beizutreten und Zugriff auf die Funktion anzufordern. </span>

[Adobe Workfront Fusion](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/get-started-with-workfront-fusion/workfront-fusion-overview.html) automatisiert die Wiederholung der gleichen Aufgaben, wie z. B. Workflows zur Dokumentenvalidierung, E-Mail-Filterung und -Sortierung, sodass Sie sich auf neue Aufgaben anstatt auf wiederkehrende Aufgaben konzentrieren können. Adobe Workfront Fusion umfasst mehrere Szenarien. Ein Szenario besteht aus einer Reihe von Modulen, die die Datenübertragung zwischen Anwendungen und Webdiensten durchführen. In einem Szenario fügen Sie verschiedene Schritte (Module) hinzu, um eine Aufgabe zu automatisieren.

Beispielsweise können Sie mit Workfront Fusion ein Szenario erstellen, um Daten mit dem adaptiven Formular zu erfassen, die Daten zu verarbeiten und die Daten zur Archivierung an einen Datenspeicher zu senden. Nachdem ein Szenario eingerichtet wurde, führt Workfront Fusion die Aufgaben automatisch aus, sobald ein Benutzer ein Formular ausfüllt, wodurch der Datenspeicher nahtlos aktualisiert wird.

AEM Forms as a Cloud Service bietet einen OOTB-Connector zum Verbinden und Senden eines adaptiven Formulars an Adobe Workfront Fusion. Die Übermittlung eines Formulars an Adobe Workfront Fusion kann mehrere Vorteile bieten:
* Sie ermöglichte die nahtlose Übertragung von Formulardaten an Workfront Fusion-Workflows.
* Dies hilft bei der Automatisierung verschiedener Aufgaben, die durch Formularübermittlungen ausgelöst werden. Dazu können das Initiieren von Projekten, das Zuweisen von Aufgaben zu bestimmten Team-Mitgliedern, das Senden von Benachrichtigungen und das Aktualisieren des Projektstatus gehören - alles ohne manuelles Eingreifen.
* Alle in Workfront Fusion erfassten Formularübermittlungen bieten eine zentrale &quot;Source of Truth&quot; für projektbezogene Informationen.


<!--  AEM as a Cloud Service offers various out of the box submit actions for handling form submissions. You can learn more about these options in the [Adaptive Form Submit Action](/help/forms/configure-submit-actions-core-components.md)  article.-->

>[!VIDEO](https://video.tv.adobe.com/v/3427145/adaptive-forms-adobe-workfront-af-workfront-workfront-aem-forms/?quality=12&learn=on)

## Voraussetzungen für die Integration von AEM Forms in Adobe Workfront Fusion {#prerequisites}

Um eine Verbindung zwischen Workfront Fusion und AEM Forms herzustellen, ist Folgendes erforderlich:

* Eine gültige [Workfront- und Workfront Fusion-Lizenz](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/get-started-with-workfront-fusion/license-automation-vs-integration.html).
* Ein AEM Benutzer mit Zugriffsrechten [Entwicklerkonsole](https://my.cloudmanager.adobe.com/) nach [Dienstanmeldeinformationen abrufen](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=de).

## Integrieren von AEM Forms mit Adobe Workfront Fusion

### 1. Erstellen eines Workfront-Szenarios {#workflow-scenario}

Um ein Workfront-Szenario zu erstellen, führen Sie die folgenden Schritte aus:

1. [Erstellen eines Szenarios](#create-scenario)
1. [Hinzufügen eines Web-Hooks zu einem Szenario](#add-webhook)
1. [Herstellen einer Verbindung zu einem Webhook](#add-connection)

#### Erstellen eines Szenarios {#create-scenario}

So erstellen Sie ein Szenario:
1. Anmelden bei [Workfront Fusion-Konto](https://app-qa.workfrontfusion.com/).
1. Klicks **[!UICONTROL Szenarien]** ![Freigabesymbol](/help/forms/assets/Smock_ShareAndroid_18_N.svg) im linken Bereich.
1. Klicks **[!UICONTROL Neues Szenario erstellen]** in der oberen rechten Ecke der Seite. Eine Seite zum Erstellen eines neuen Szenarios wird auf dem Bildschirm angezeigt.
1. Auswählen **[!UICONTROL Neues Szenario]** in der linken oberen Ecke der Seite und geben Sie einen geeigneten Namen für das Szenario ein.
1. Klicken Sie auf das Fragezeichen und stellen Sie sicher, dass Sie das erste Modul als **[!UICONTROL AEM Forms]**.

   ![AEM Forms-Modul hinzufügen](/help/forms/assets/workfront-aemforms.png)

   Die **[!UICONTROL Formularereignisse beobachten]** angezeigt.

   >[!NOTE]
   >
   > Es ist erforderlich, das erste Modul als **[!UICONTROL AEM Forms]**.

1. Wählen Sie die **[!UICONTROL Formularereignisse beobachten]** und ein Fenster zum Hinzufügen eines Webhooks angezeigt.

#### Webhook hinzufügen {#add-webhook}

![Webhook hinzufügen](/help/forms/assets/workfront-add-webhook.png)

Hinzufügen eines Webhooks:

1. Klicks **[!UICONTROL Hinzufügen]** und **[!UICONTROL Webhook hinzufügen]** angezeigt.
1. Geben Sie einen Webhook-Namen an.

   >[!NOTE]
   >
   > Es wird empfohlen, Ihren Webhook-Namen sorgfältig auszuwählen, da der angegebene Webhook-Name in der AEM-Instanz angezeigt wird.

1. Klicks **[!UICONTROL Hinzufügen]** , um eine neue Verbindung hinzuzufügen. Die **[!UICONTROL Verbindung erstellen]** angezeigt.

#### Verbindung zu einem Webhook hinzufügen {#add-connection}

![Verbindung hinzufügen](/help/forms/assets/workfront-add-connection.png)

So fügen Sie eine Verbindung hinzu:

1. Geben Sie eine **[!UICONTROL Verbindungsname]** im **[!UICONTROL Verbindung erstellen]** Dialogfeld.

1. Auswählen **Umgebung** und **Typ** aus der Dropdown-Liste.

1. Geben Sie die **Instanz-URL**.

   >[!NOTE]
   >
   > Die Instanz-URL ist die eindeutige Webadresse, die auf eine bestimmte AEM Forms-Instanz verweist.

   Sie können die [Dienstanmeldeinformationen aus der Developer Console](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=de) erforderlich, um eine Verbindung zu erstellen.

1. Ersetzen `ims-na1.adobelogin.com` im **IMS-Endpunkt** mit dem Wert von **imsEndpoint** über die Dienstanmeldeinformationen in der Entwicklerkonsole.

   >[!NOTE]
   >
   > Speichern Sie die `https://` im **IMS-Endpunkt** Textfeld beim Hinzufügen `imsEndpoint` URL.

1. Geben Sie die folgenden Werte in der **[!UICONTROL Verbindung erstellen]** Dialogfeld:
   * Angeben **Client-ID** mit dem Wert von **clientId** über die Dienstanmeldeinformationen in der Entwicklerkonsole.
   * Angeben **Client Secret** mit dem Wert von **clientSecret** über die Dienstanmeldeinformationen in der Entwicklerkonsole.
   * Angeben **Technische Konto-ID**  mit dem Wert von **id** über die Dienstanmeldeinformationen in der Entwicklerkonsole.
   * Angeben **Organisations-ID**  mit dem Wert von **org** über die Dienstanmeldeinformationen in der Entwicklerkonsole.
   * **Meta-Bereiche**  mit dem Wert von **Metaskope** über die Dienstanmeldeinformationen in der Entwicklerkonsole.
   * **Private Schlüssel**  mit dem Wert von **privateKey** über die Dienstanmeldeinformationen in der Entwicklerkonsole.

   >[!NOTE]
   >
   >* Für **Privater Schlüssel**, entfernen `\r\n` aus dem Wert.
   >  Wenn der Wert des privaten Schlüssels beispielsweise:
   >`\r\nIJAVO8GDYAOZ9jMA0GCSqGSIb3DQEBCwUAMDAxL\r\nMy1lMTUxODMxLWNtc3RnLWludGVncmF0aW9uLTAw`nach dem Entfernen der `\r\n` aus dem privaten Schlüssel würde der Schlüssel wie folgt aussehen, wobei beide Werte in einer separaten Zeile angezeigt werden:
   >
   >   `IJAVO8GDYAOZ9jMA0GCSqGSIb3DQEBCwUAMDAxL`
   >
   >   `My1lMTUxODMxLWNtc3RnLWludGVncmF0aW9uLTAw`
   > 
   >* Sie können auch einen privaten Schlüssel oder ein Zertifikat aus der Datei abrufen, indem Sie die **Extract** Schaltfläche.

1. Klicken Sie auf **Weiter**.

   Die erstellte Verbindung wird in der Dropdown-Liste der **[!UICONTROL Verbindung]** im **[!UICONTROL Webhook hinzufügen]** Dialogfeld.

1. Auswählen der erstellten Verbindung **[!UICONTROL Verbindung]** aus der Dropdown-Liste.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Klicks **[!UICONTROL OK]** und speichern Sie die Änderungen für das Szenario.
1. Um das Szenario zu aktivieren, klicken Sie im Szenario-Editor auf die Schaltfläche Ein/Aus .

>[!NOTE]
>
> Wenn Sie das Workfront-Szenario nicht aktivieren, wird die Formularübermittlung nicht erkannt, und die Einstellung der Sendeaktion auf Workfront führt zu einer fehlgeschlagenen Übermittlung.

### 2. Konfigurieren der Sendeaktion eines adaptiven Formulars für Workfront Fusion

Sie können die Sendeaktion für Workfront Fusion konfigurieren für:
* [Neue adaptive Forms](#new-af-submit-action)
* [Vorhandene adaptive Formulare](#existing-af-submit-action)

#### Konfigurieren der Sendeaktion für das neue adaptive Formular für Workfront Fusion {#new-af-submit-action}

So konfigurieren Sie die Sendeaktion des neuen adaptiven Formulars für Workfront Fusion:

1. Melden Sie sich bei Ihrer AEM-Instanz an.
1. Navigieren Sie zu **[!UICONTROL Forms]** > **[!UICONTROL Forms und Dokumente]** > **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptives Formular]**. Die **[!UICONTROL Formular erstellen]** wird angezeigt.
1. Wählen Sie eine Vorlage für ein adaptives Formular aus der **[!UICONTROL Quelle]** Registerkarte.
1. Wählen Sie ein Design aus dem **[!UICONTROL Stil]** Registerkarte.

   ![Übermittlungsaktion für Workfront Fusion](/help/forms/assets/workfront-scenario-new-af.png)

1. Wählen Sie die **[!UICONTROL Aufrufen eines Workfront Fusion-Szenarios]** aus dem **[!UICONTROL Einsendung]** Registerkarte.
1. Wählen Sie den erstellten Webhook aus dem **[!UICONTROL Optionen]** im **[!UICONTROL Eigenschaften]** Fenster.

   >[!NOTE]
   >
   > Der Webhook-Name des Workfront-Szenarios wird im **Optionen** Dropdown-Liste.

1. Klicken Sie auf **[!UICONTROL Erstellen]**.
1. Geben Sie den Namen für das neue adaptive Formular an und klicken Sie auf **[!UICONTROL Erstellen]**.

#### Konfigurieren der Sendeaktion des vorhandenen adaptiven Formulars für Workfront Fusion {#existing-af-submit-action}

So konfigurieren Sie die Sendeaktion des vorhandenen adaptiven Formulars für Workfront Fusion:

1. Melden Sie sich bei Ihrer AEM-Instanz an.
1. Gehen Sie zu **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie ein adaptives Formular aus und öffnen Sie es in einem Bearbeitungsmodus.
1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.

   ![Übermittlungsaktion für Workfront Fusion](/help/forms/assets/workfront-scenario-existing-af.png)

1. Öffnen Sie die Registerkarte **[!UICONTROL Übermittlung]**.
1. Wählen Sie die **[!UICONTROL Übermittlungsaktion]** as **[!UICONTROL Aufrufen eines Workfront Fusion-Szenarios]**
1. Auswählen **[!UICONTROL Workfront Fusion-Szenario]** aus der Dropdown-Liste.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

## Best Practices {#best-practices}

* Es wird empfohlen, Ihren Webhook-Namen sorgfältig auszuwählen, da es nicht möglich ist, den Namen des Szenarios in der AEM-Instanz zu erhalten. Falls Sie den Webhook-Namen in Zukunft ändern, wird er nicht in der Dropdown-Liste für die Übermittlungsaktion für AEM Forms angezeigt.
* Ein Szenario kann über mehrere Webhook-Links verfügen, gleichzeitig ist jedoch nur ein Webhook-Link aktiv. Es wird empfohlen, den nicht verknüpften Webhook zu löschen, damit er nicht in der Dropdown-Liste für Übermittlungsaktionen in AEM Forms angezeigt wird.

<!-- During testing or development of Workfront, add the Author URL to the instance URL. However, when deploying Workfront Fusion in a production environment, it is recommended to replicate the scenario URLs for the Publish instance. -->

## Ähnliche Artikel

{{af-submit-action}}