---
title: Optimierte Smart-Tags
description: Wenden Sie mithilfe der KI- und ML-Services von Adobe Sensei kontextbezogene und beschreibende Unternehmens-Tags an, um die Asset-Erkennung und Content Velocity zu verbessern.
contentOwner: AG
translation-type: tm+mt
source-git-commit: bf7bb91dd488f39181a08adc592971d6314817de
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 49%

---


# Experience Manager für intelligentes Tagging von Assets konfigurieren {#configure-aem-for-smart-tagging}

Durch das Taggen von Assets mit einem taxonomisch gesteuerten Vokabular wird sichergestellt, dass die Assets durch tag-basierte Suchen leicht identifiziert und abgerufen werden können. Adobe stellt intelligente Tags bereit, die künstliche Intelligenz und maschinelle Lernalgorithmen verwenden, um Bilder zu trainieren. Smart Tags verwenden ein künstliches Intelligenzkonzept von [Adobe Sensei](https://www.adobe.com/de/sensei/experience-cloud-artificial-intelligence.html) , um den Bilderkennungsalgorithmus in Ihrer Tag-Struktur und Ihrer Geschäftstaxonomie zu schulen.

The Smart Tags functionality is available for purchase as an add-on to [!DNL Experience Manager]. Nach dem Kauf wird eine E-Mail mit einem Link zur Adobe-ID/O an den Administrator Ihres Unternehmens gesendet. Der Administrator greift auf den Link zu, um die intelligenten Tags mit [!DNL Experience Manager] Adobe I/O zu integrieren.

<!-- TBD: 
1. Can a similar flowchart be created about how training works in CS? ![flowchart](assets/flowchart.gif)
2. Is there a link to buy SCS or initiate a sales call.
3. Keystroke all steps and check all screenshots.
4. Post-GA, if time permits, create a video.
-->

## Integration mit Adobe I/O {#aio-integration}

Bevor Sie die Bilder mit SCS taggen können, müssen Sie sie mit dem Smart Tags-Dienst [!DNL Adobe Experience Manager] von Adobe I/O integrieren. Am Back-End authentifiziert der [!DNL Experience Manager] Server Ihre Dienstberechtigungen mit dem Adobe I/O Gateway, bevor Sie Ihre Anforderung an den Dienst weiterleiten.

* Create a configuration in [!DNL Experience Manager] to generate a public key. Erhalten Sie ein öffentliches Zertifikat für die OAuth-Integration.
* Erstellen Sie eine Integration in Adobe I/O und laden Sie den generierten öffentlichen Schlüssel hoch.
* Configure your [!DNL Experience Manager] instance using the API key and other credentials from Adobe I/O.
* Aktivieren Sie optional das automatische Tagging beim Hochladen eines Assets.

### Voraussetzungen für die Adobe I/O-Integration {#prerequisite-for-aio-integration}

Bevor Sie die intelligenten Tags verwenden können, stellen Sie Folgendes sicher, um eine Integration in Adobe I/O zu erstellen:

* Es ist ein Adobe ID-Konto mit Administratorrechten für die Organisation vorhanden.
* Die intelligenten Tags sind für Ihr Unternehmen aktiviert.

### Obtain a public certificate {#obtain-public-certificate}

Ein öffentliches Zertifikat ermöglicht Ihnen die Authentifizierung Ihres Profils in Adobe I/O.

1. Rufen Sie in der [!DNL Experience Manager] Benutzeroberfläche **[!UICONTROL Werkzeuge]** > **[!UICONTROL Cloud-Dienste]** > **[!UICONTROL Legacy Cloud-Dienste]** auf.

1. On the Cloud Services page, click **[!UICONTROL Configure Now]** under **[!UICONTROL Assets Smart Tags]**.

1. Geben Sie im Dialogfeld **[!UICONTROL Konfiguration erstellen]** einen Titel und einen Namen für die Smart-Tags-Konfiguration ein. Klicken Sie auf **[!UICONTROL Erstellen]**.

1. Verwenden Sie im Dialogfeld **[!UICONTROL AEM Smart Content Service]** die folgenden Werte:

   **[!UICONTROL Dienst-URL]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Autorisierungsserver]**: `https://ims-na1.adobelogin.com`

   Lassen Sie die anderen Felder vorerst leer (Werte werden später bereitgestellt). Klicken Sie auf **[!UICONTROL OK]**.

   ![Dialogfeld &quot;Experience Manager Smart Content Service&quot;, um die URL des Inhaltsdienstes bereitzustellen](assets/aem_scs.png)

1. Click **[!UICONTROL Download Public Certificate for OAuth Integration]**, and download the public certificate file `AEM-SmartTags.crt`.

   ![Für den Smart-Tagging-Dienst erstellte Einstellungen](assets/download_link.png)

### Bei Ablauf eines Zertifikats neu konfigurieren {#certrenew}

Wenn das Zertifikat abläuft, wird es nicht mehr als vertrauenswürdig eingestuft. Um ein neues Zertifikat hinzuzufügen, führen Sie diese Schritte aus. Sie können ein abgelaufenes Zertifikat nicht verlängern.

1. Log in your [!DNL Experience Manager] deployment as an administrator. Klicken Sie auf **[!UICONTROL Werkzeuge]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.

1. Suchen und finden Sie **[!UICONTROL dam-update-service]**-Benutzer und klicken Sie darauf. Klicken Sie auf die Registerkarte **[!UICONTROL Keystore]**.
1. Löschen Sie den vorhandenen **[!UICONTROL similaritysearch]**-Keystore mit dem abgelaufenen Zertifikat. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

   ![Löschen Sie den vorhandenen Eintrag „similaritysearch“ (Ähnlichkeitssuche) in Keystore, um ein neues Sicherheitszertifikat hinzuzufügen.](assets/smarttags_delete_similaritysearch_keystore.png)

   *Abbildung: Löschen Sie den vorhandenen`similaritysearch`Eintrag in Keystore, um ein neues Sicherheitszertifikat hinzuzufügen.*

1. Navigieren Sie zu **[!UICONTROL Werkzeuge]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy-Cloud Services]**. Klicken Sie auf **[!UICONTROL Asset-Smart-Tags]** > **[!UICONTROL Konfiguration anzeigen]** > **[!UICONTROL Verfügbare Konfigurationen]**. Klicken Sie auf die gewünschte Konfiguration.

1. Um ein öffentliches Zertifikat herunterzuladen, klicken Sie auf **[!UICONTROL Öffentliches Zertifikat für OAuth-Integration herunterladen]**.

1. Rufen Sie [https://console.adobe.io](https://console.adobe.io) auf und navigieren Sie zum vorhandenen Dienst im Projekt. Laden Sie das neue Zertifikat hoch. Weitere Informationen finden Sie in den Anweisungen unter [Adobe I/O-Integration erstellen](#create-aio-integration).

### Eine Integration erstellen {#create-aio-integration}

Um Smart-Tags-APIs zu verwenden, erstellen Sie eine Integration in Adobe I/O, um den API-Schlüssel, die technische Konto-ID, die Organisations-ID und den geheimen Clientschlüssel zu generieren.

1. Greifen Sie auf [https://console.adobe.io](https://console.adobe.io/) zu.
1. Wählen Sie das entsprechende Konto aus und vergewissern Sie sich, dass die zugehörige Rolle Systemadministrator ist. Erstellen Sie ein Projekt oder öffnen Sie ein vorhandenes Projekt. Klicken Sie auf der Projektseite auf **[!UICONTROL Hinzufügen API]**.
1. Wählen Sie auf der Seite **[!UICONTROL Hinzufügen API]** die Option **[!UICONTROL Experience Cloud]** und dann **[!UICONTROL Smart Content]**. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie auf der nächsten Seite **[!UICONTROL Neue Integration]** aus. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie auf der Seite **[!UICONTROL Integrationsdetails]** einen Namen für das Integrations-Gateway ein und fügen Sie eine Beschreibung hinzu.
1. Laden Sie in den **[!UICONTROL Zertifikaten zu öffentlichen Schlüsseln]** die Datei `AEM-SmartTags.crt` hoch, die Sie weiter oben heruntergeladen haben.
1. Klicken Sie auf **[!UICONTROL Integration erstellen]**.
1. To view the integration information, click **[!UICONTROL Continue to integration details]**.

   ![Auf der Registerkarte „Übersicht“ können Sie die für die Integration bereitgestellten Informationen überprüfen.](assets/integration_details.png)

### Intelligente Tags konfigurieren {#configure-smart-content-service}

Verwenden Sie zum Konfigurieren der Integration die Werte der Felder „ID des technischen Kontos“, „Organisations-ID“, „Client-Geheimnis“, „Autorisierungsserver“ und „API-Schlüssel“ aus der Adobe I/O-Integration. Creating a Smart Tags cloud configuration allows authentication of API requests from the [!DNL Experience Manager] instance.

1. In [!DNL Experience Manager], navigate to **[!UICONTROL Tools > Cloud Service > Legacy Cloud Services]** to open the [!UICONTROL Cloud Services] console.
1. Öffnen Sie unter den **[!UICONTROL Smart-Tags für Assets]** die oben erstellte Konfiguration. Klicken Sie auf der Seite mit den Serviceeinstellungen auf **[!UICONTROL Bearbeiten]**.
1. Verwenden Sie im Dialogfeld **[!UICONTROL AEM Smart Content Service]** die vorausgefüllten Werte für die Felder **[!UICONTROL Service-URL]** und **[!UICONTROL Autorisierungsserver]**.
1. Verwenden Sie für die Felder **[!UICONTROL API-Schlüssel]**, **[!UICONTROL Technische Konto-ID]**, **[!UICONTROL Organisations-ID]** und **[!UICONTROL Geheimer Clientschlüssel]** die oben generierten Werte.

### Überprüfen der Konfiguration {#validate-the-configuration}

Nachdem Sie die Konfiguration abgeschlossen haben, können Sie die Konfiguration mit einem JMX MBean überprüfen. Führen Sie zum Überprüfen die folgenden Schritte aus.

1. Greifen Sie auf Ihren [!DNL Experience Manager] Server unter `https://[aem_server]:[port]`.

1. Öffnen Sie unter **[!UICONTROL Tools > Vorgänge > Web-Konsole]** die OSGi-Konsole. Klicken Sie auf **[!UICONTROL Haupt > JMX]**.
1. Klicken Sie auf **[!UICONTROL com.day.cq.dam.similaritysearch.internal.impl]**. Die Seite **[!UICONTROL SimilaritySearch Miscellaneous Tasks]** wird geöffnet.
1. Klicken Sie auf **[!UICONTROL validateConfigs()]**. In the **[!UICONTROL Validate Configurations]** dialog, click **[!UICONTROL Invoke]**.

   Das Überprüfungsergebnis wird im selben Dialogfeld angezeigt.

## Aktivieren des intelligenten Tagging für neu hochgeladene Assets (optional) {#enable-smart-tagging-for-uploaded-assets}

1. Gehen Sie [!DNL Experience Manager]zu **[!UICONTROL Werkzeuge > Workflow > Modelle]**.
1. Wählen Sie auf der Seite **[!UICONTROL Workflowmodelle]** das **[!UICONTROL DAM Update Asset]**-Workflowmodell.
1. Click **[!UICONTROL Edit]** from the toolbar.
1. Erweitern Sie das Seitenbedienfeld, um die Schritte anzuzeigen. Ziehen Sie den Schritt **[!UICONTROL Smart Tag-Asset]**, der im Abschnitt „DAM-Workflow“ verfügbar ist, und platzieren Sie ihn nach dem Schritt **[!UICONTROL Prozessminiaturansichten]**.

   ![Schritt zum Hinzufügen von Smart Tag Assets nach dem Schritt „Miniaturansichten verarbeiten“ im Workflow „DAM-Update-Asset“](assets/chlimage_1-105.png)

   *Abbildung: Hinzufügen Schritt für Smart-Tag-Assets nach dem Schritt für die Prozessminiaturansicht im DAM-Arbeitsablauf zum Aktualisieren von Assets.*

1. Öffnen Sie den zu konfigurierenden Schritt. Stellen Sie unter **[!UICONTROL Erweiterte Einstellungen]** sicher, dass die Option **[!UICONTROL Handler-Erweiterung]** ausgewählt ist.

   ![Festlegen, dass der Handler zum nächsten Schritt im Workflow weitergeleitet wird.](assets/smart-tags-workflow-handler-setting.png)

1. Wählen Sie auf der Registerkarte &quot; **[!UICONTROL Argumente]** &quot;die Option &quot;Fehler **[!UICONTROL ignorieren&quot;]** , wenn Fehler beim Prädiktieren von Tags ignoriert werden sollen. Um Assets unabhängig davon mit Tags zu versehen, ob die Smart-Tagging-Funktion für Ordner aktiviert ist, wählen Sie **[!UICONTROL Smart-Tag-Flag ignorieren]** aus.

1. Click **[!UICONTROL OK]** to close the process step, and then save the workflow. Klicken Sie auf **[!UICONTROL Synchronisieren]**.

>[!MORELIKETHIS]
>
>* [Taggen von Assets mit dem intelligenten Dienst](smart-tags.md)

