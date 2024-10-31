---
title: Integration von Adobe Workfront Fusion mit der AEM-Formularübermittlung
description: Adobe Workfront Fusion ermöglicht es Ihnen, sich auf neue Aufgaben zu konzentrieren, anstatt sich auf sich wiederholende Aufgaben zu konzentrieren. Sie können Adobe Workfront Fusion über die Formularübermittlung mit einem adaptiven Formular verbinden.
keywords: Senden eines adaptiven Formulars an Adobe Workfront Fusion, Integration von Adobe Workfront Fusion mit der AEM-Formularübermittlung, Adobe Workfront Fusion mit AEM Forms, Workfront Fusion mit AEM Forms, Verbinden von Workfront Fusion mit AEM Forms, AEM Forms und Workfront Fusion, Wie verbindet man Workfront Fusion mit AEM Forms?, Verbinden von Workfront Fusion mit einem Formular
topic-tags: author, developer
feature: Adaptive Forms
role: Admin, User
exl-id: d3efb450-a879-40ae-8958-0040f99bdafc
source-git-commit: d0d7a10b2c1dadb0f8bfaa654db7993d3e5e6635
workflow-type: ht
source-wordcount: '1272'
ht-degree: 100%

---

# Senden eines adaptiven Formulars an Adobe Workfront Fusion

<span class="preview"> Die Funktion ist im Rahmen des Early-Adopter-Programms verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugriff auf diese Funktion zu beantragen. </span>

[Adobe Workfront Fusion](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/get-started-with-workfront-fusion/workfront-fusion-overview.html?lang=de) automatisiert den Prozess für sich wiederholende Aufgaben, wie z. B. Arbeitsabläufe zur Genehmigung von Dokumenten, E-Mail-Filterung und Sortierung, sodass Sie sich auf neue Aufgaben statt auf wiederkehrende Aufgaben konzentrieren können. Adobe Workfront Fusion umfasst mehrere Szenarien. Ein Szenario besteht aus einer Reihe von Modulen, die die Datenübertragung zwischen Anwendungen und Web-Diensten durchführen. In einem Szenario fügen Sie verschiedene Schritte (Module) hinzu, um eine Aufgabe zu automatisieren.

Beispielsweise können Sie mit Workfront Fusion ein Szenario erstellen, um Daten mit dem adaptiven Formular zu erfassen, die Daten zu verarbeiten und die Daten zur Archivierung an einen Datenspeicher zu senden. Nachdem ein Szenario eingerichtet wurde, führt Workfront Fusion die Aufgaben automatisch aus, sobald eine Person ein Formular ausfüllt, wodurch der Datenspeicher nahtlos aktualisiert wird.

AEM Forms as a Cloud Service bietet einen vorkonfigurierten Connector zum Verbinden und Senden eines adaptiven Formulars an Adobe Workfront Fusion. Die Übermittlung eines Formulars an Adobe Workfront Fusion kann mehrere Vorteile bieten:
* Sie ermöglicht die nahtlose Übertragung von Formularübermittlungsdaten an Workfront Fusion-Workflows.
* Dies hilft bei der Automatisierung verschiedener Aufgaben, die durch Formularübermittlungen ausgelöst werden. Dazu können das Initiieren von Projekten, das Zuweisen von Aufgaben zu bestimmten Team-Mitgliedern, das Senden von Benachrichtigungen und das Aktualisieren des Projektstatus gehören – alles ohne manuelles Eingreifen.
* Alle in Workfront Fusion erfassten Formularübermittlungen bieten eine zentrale Quelle für projektbezogene Informationen.


<!--  AEM as a Cloud Service offers various out of the box submit actions for handling form submissions. You can learn more about these options in the [Adaptive Form Submit Action](/help/forms/configure-submit-actions-core-components.md)  article.-->

>[!VIDEO](https://video.tv.adobe.com/v/3427145/adaptive-forms-adobe-workfront-af-workfront-workfront-aem-forms/?quality=12&learn=on)

## Voraussetzungen für die Integration von AEM Forms mit Adobe Workfront Fusion {#prerequisites}

Um eine Verbindung zwischen Workfront Fusion und AEM Forms herzustellen, ist Folgendes erforderlich:

* Eine gültige [Workfront- und Workfront-Fusion-Lizenz](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-fusion/get-started-with-workfront-fusion/license-automation-vs-integration.html?lang=de).
* Eine AEM-Benutzerin bzw. ein -Benutzer mit Zugriffsrechten auf die [Developer Console](https://my.cloudmanager.adobe.com/), um [die Dienstanmeldeinformationen abzurufen](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=de).

## Integrieren von AEM-Formularen mit Adobe Workfront Fusion

### 1. Erstellen eines Workfront-Szenarios {#workflow-scenario}

Um ein Workfront-Szenario zu erstellen, führen Sie die folgenden Schritte aus:

1. [Erstellen eines Szenarios](#create-scenario)
1. [Hinzufügen eines Webhooks zu einem Szenario](#add-webhook)
1. [Hinzufügen einer Verbindung zu einem Webhook](#add-connection)

#### Erstellen eines Szenarios {#create-scenario}

So erstellen Sie ein Szenario:
1. Melden Sie sich bei Ihrem [Workfront Fusion-Konto](https://app-qa.workfrontfusion.com/) an.
1. Klicken Sie unter **[!UICONTROL Szenarien]** auf das ![Freigabe-Symbol](/help/forms/assets/Smock_ShareAndroid_18_N.svg) in der linken Leiste.
1. Klicken Sie auf **[!UICONTROL Ein neues Szenario erstellen]** in der oberen rechten Ecke der Seite. Eine Seite zum Erstellen eines neuen Szenarios wird auf dem Bildschirm angezeigt.
1. Wählen Sie **[!UICONTROL Neues Szenario]** in der oberen linken Ecke auf der Seite und geben Sie einen passenden Namen für das Szenario ein.
1. Klicken Sie auf das Fragezeichen und stellen Sie sicher, dass Sie das erste Modul als **[!UICONTROL AEM Forms]** hinzufügen.

   ![Hinzufügen eines AEM Forms-Moduls](/help/forms/assets/workfront-aemforms.png)

   Das Dialogfeld **[!UICONTROL Formularereignisse beobachten]** wird angezeigt.

   >[!NOTE]
   >
   > Es ist zwingend erforderlich, das erste Modul als **[!UICONTROL AEM Forms]** hinzuzufügen.

1. Wählen Sie das Dialogfeld **[!UICONTROL Formularereignisse beobachten]**, und ein Fenster zum Hinzufügen eines Webhooks wird angezeigt.

#### Hinzufügen eines Webhooks {#add-webhook}

![Hinzufügen eines Webhooks](/help/forms/assets/workfront-add-webhook.png)

So fügen Sie einen Webhook hinzu:

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**, und ein Dialogfeld **[!UICONTROL Webhook hinzufügen]** wird angezeigt.
1. Angeben eines Webhook-Namens

   >[!NOTE]
   >
   > Es wird empfohlen, Ihren Webhook-Namen sorgfältig auszuwählen, da der angegebene Webhook-Name in der AEM-Instanz angezeigt wird.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**, um eine neue Verbindung hinzuzufügen. Das Dialogfeld **[!UICONTROL Verbindung erstellen]** erscheint.

>[!NOTE]
>
> Vergewissern Sie sich, dass das technische Konto ein Mitglied der Gruppe **Forms-Benutzer** ist. Andernfalls schlägt das Hinzufügen eines Webhooks fehl.

#### Hinzufügen einer Verbindung zu einem Webhook {#add-connection}

![Hinzufügen einer Verbindung](/help/forms/assets/workfront-add-connection.png)

So fügen Sie eine Verbindung hinzu:

1. Geben Sie einen **[!UICONTROL Verbindungsnamen]** im Dialogfeld **[!UICONTROL Verbindung erstellen]** an.

1. Wählen Sie **Umgebung** und **Typ** aus der Dropdown-Liste.

1. Geben Sie die **Instanz-URL** ein.

   >[!NOTE]
   >
   > Die Instanz-URL ist die eindeutige Web-Adresse, die auf eine bestimmte AEM Forms-Instanz verweist.

   Sie können die [Dienstanmeldeinformationen von der Developer Console abrufen](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=de), die zum Erstellen einer Verbindung erforderlich sind.

1. Ersetzen Sie `ims-na1.adobelogin.com` in **IMS-Endpunkt** durch den Wert von **imsEndpoint** aus den Dienstanmeldeinformationen in der Developer Console.

   >[!NOTE]
   >
   > Behalten Sie das `https://` im Textfeld **IMS-Endpunkt** bei, während Sie die `imsEndpoint`-URL hinzufügen.

1. Geben Sie im Dialogfeld **[!UICONTROL Verbindung erstellen]** die folgenden Werte an:
   * Geben Sie die **Client-ID** mit dem Wert **clientId** aus den Dienstanmeldeinformationen in der Developer Console an.
   * Geben Sie das **Client-Geheimnis** mit dem Wert **clientSecret** aus den Dienstanmeldeinformationen in der Developer Console an.
   * Geben Sie die **Technische Konto-ID** mit dem Wert **id** aus den Dienstanmeldeinformationen in der Developer Console an.
   * Geben Sie die **Org-ID** mit dem Wert **org** aus den Dienstanmeldeinformationen in der Developer Console an.
   * Geben Sie die **Meta-Bereiche** mit dem Wert von **metascopes** aus den Dienstanmeldeinformationen in der Developer Console an.
   * Geben Sie die **privaten Schlüssel** mit dem Wert **privateKey** aus den Dienstanmeldeinformationen in der Developer Console an.

   >[!NOTE]
   >
   >* Entfernen Sie bei dem **privaten Schlüssel** `\r\n` aus dem Wert.
   >  Zum Beispiel, wenn der Wert des privaten Schlüssels wie folgt lautet:
   >`\r\nIJAVO8GDYAOZ9jMA0GCSqGSIb3DQEBCwUAMDAxL\r\nMy1lMTUxODMxLWNtc3RnLWludGVncmF0aW9uLTAw`, dann würde der Schlüssel nach dem Entfernen von `\r\n` aus dem privaten Schlüssel wie folgt aussehen, wobei die beiden Werte in einer separaten Zeile erscheinen:
   >
   >   `IJAVO8GDYAOZ9jMA0GCSqGSIb3DQEBCwUAMDAxL`
   >
   >   `My1lMTUxODMxLWNtc3RnLWludGVncmF0aW9uLTAw`
   > 
   >* Sie haben auch die Möglichkeit, einen privaten Schlüssel oder ein Zertifikat aus der Datei abzurufen, indem Sie die Schaltfläche **Extrahieren** wählen.

1. Klicken Sie auf **Weiter**.

   Die erstellte Verbindung wird in der Dropdown-Liste **[!UICONTROL Verbindung]** im Dialogfeld **[!UICONTROL Webhook hinzufügen]** angezeigt.

1. Wählen Sie die erstellte Verbindung **[!UICONTROL Verbindung]** aus der Dropdown-Liste.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Klicken Sie auf **[!UICONTROL OK]** und speichern Sie die Änderungen für das Szenario.
1. Um das Szenario zu aktivieren, klicken Sie im Szenario-Editor auf die Umschalt-Schaltfläche „EIN/AUS“.

>[!NOTE]
>
> Wenn Sie das Workfront-Szenario nicht aktivieren, wird die Formularübermittlung nicht erkannt, und die Einstellung der Übermittlungsaktion auf Workfront führt zu einer fehlgeschlagenen Übermittlung.

### 2. Konfigurieren der Übermittlungsaktion eines adaptiven Formulars für Workfront Fusion

Sie können die Übermittlungsaktion für Workfront Fusion für Folgendes konfigurieren:
* [Neue adaptive Formulare](#new-af-submit-action)
* [Vorhandene adaptive Formulare](#existing-af-submit-action)

#### Konfigurieren der Übermittlungsaktion für das neue adaptive Formular für Workfront Fusion {#new-af-submit-action}

So konfigurieren Sie die Übermittlungsaktion des neuen adaptiven Formulars für Workfront Fusion:

1. Melden Sie sich bei Ihrer AEM-Instanz an. 
1. Gehen Sie zu **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** > **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptives Formular]**. Der **[!UICONTROL Assistent zum Erstellen von Formularen]** erscheint.
1. Wählen Sie auf der Registerkarte **[!UICONTROL Quelle]** eine Vorlage für ein adaptives Formular aus.
1. Wählen Sie ein Design auf der Registerkarte **[!UICONTROL Stil]**.

   ![Übermittlungsaktion für Workfront Fusion](/help/forms/assets/workfront-scenario-new-af.png)

1. Wählen Sie auf der Registerkarte **[!UICONTROL Übermittlungen]** die Option **[!UICONTROL Ein WorkFront Fusion-Szenario aufrufen]**.
1. Wählen Sie den erstellten Webhook auf der Registerkarte **[!UICONTROL Optionen]** im Fenster **[!UICONTROL Eigenschaften]** aus.

   >[!NOTE]
   >
   > Der Webhook-Name des Workfront-Szenarios erscheint in der Dropdown-Liste **Optionen**.

1. Klicken Sie auf **[!UICONTROL Erstellen]**.
1. Geben Sie den Namen für Ihr neues adaptives Formular an und klicken Sie auf **[!UICONTROL Erstellen]**.

#### Konfigurieren der Übermittlungsaktion des vorhandenen adaptiven Formulars für Workfront Fusion {#existing-af-submit-action}

So konfigurieren Sie die Übermittlungsaktion des vorhandenen adaptiven Formulars für Workfront Fusion:

1. Melden Sie sich bei Ihrer AEM-Instanz an. 
1. Gehen Sie zu **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.
1. Wählen Sie ein adaptives Formular aus und öffnen Sie es in einem Bearbeitungsmodus.
1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.

   ![Übermittlungsaktion für Workfront Fusion](/help/forms/assets/workfront-scenario-existing-af.png)

1. Öffnen Sie die Registerkarte **[!UICONTROL Übermittlung]**.
1. Wählen Sie die **[!UICONTROL Übermittlungsaktion]** als **[!UICONTROL Aufruf eines Workfront Fusion-Szenarios]**.
1. Wählen Sie **[!UICONTROL Workfront Fusion Szenario]** aus der Dropdown-Liste.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

## Best Practices {#best-practices}

* Es wird empfohlen, Ihren Webhook-Namen sorgfältig auszuwählen, da es in der AEM-Instanz nicht möglich ist, den Namen des Szenarios zu erhalten. Falls Sie den Webhook-Namen in Zukunft ändern, wird die Änderung nicht in der Dropdown-Liste für die Übermittlungsaktion für AEM Forms angezeigt.
* Ein Szenario kann über mehrere Webhook-Links verfügen, es ist jedoch nur ein Webhook-Link gleichzeitig aktiv. Es wird empfohlen, den nicht verknüpften Webhook zu löschen, damit er nicht in der Dropdown-Liste der Übermittlungsaktionen in AEM Forms angezeigt wird.

<!-- During testing or development of Workfront, add the Author URL to the instance URL. However, when deploying Workfront Fusion in a production environment, it is recommended to replicate the scenario URLs for the Publish instance. -->

## Ähnliche Artikel

{{af-submit-action}}