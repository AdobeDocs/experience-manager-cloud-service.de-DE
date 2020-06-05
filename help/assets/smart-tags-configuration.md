---
title: Optimierte Smart-Tags
description: Wenden Sie mithilfe der KI- und ML-Services von Adobe Sensei kontextbezogene und beschreibende Unternehmens-Tags an, um die Asset-Erkennung und Content Velocity zu verbessern.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 41684858f1fe516046b9601c1d869fff180320e0
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 22%

---


# Experience Manager für intelligentes Tagging von Assets konfigurieren {#configure-aem-for-smart-tagging}

Durch das Taggen von Assets mit einem taxonomisch gesteuerten Vokabular wird sichergestellt, dass die Assets durch tag-basierte Suchen leicht identifiziert und abgerufen werden können. Adobe stellt intelligente Tags bereit, die künstliche Intelligenz und maschinelle Lernalgorithmen verwenden, um Bilder zu trainieren. Smart Tags verwenden ein künstliches Intelligenzkonzept von [Adobe Sensei](https://www.adobe.com/de/sensei/experience-cloud-artificial-intelligence.html) , um den Bilderkennungsalgorithmus in Ihrer Tag-Struktur und Ihrer Geschäftstaxonomie zu schulen.

The Smart Tags functionality is available for purchase as an add-on to [!DNL Experience Manager]. Nach dem Kauf wird eine E-Mail mit einem Link zur Adobe Developer Console an den Administrator Ihres Unternehmens gesendet. Der Administrator greift auf den Link zu, um die Smart-Tags mit der Adobe Developer Console zu integrieren. [!DNL Experience Manager]

<!-- TBD: 
1. Can a similar flowchart be created about how training works in CS? ![flowchart](assets/flowchart.gif)
2. Is there a link to buy SCS or initiate a sales call.
3. Keystroke all steps and check all screenshots.
4. Post-GA, if time permits, create a video.
-->

## Integration mit der Adobe Developer Console {#aio-integration}

Bevor Sie die Bilder mit SCS taggen können, müssen Sie sie mit der Adobe Developer Console in [!DNL Adobe Experience Manager] den Smart Tags-Dienst integrieren. At the back end, the [!DNL Experience Manager] server authenticates your service credentials with the Adobe Developer Console gateway before forwarding your request to the service.

* Create a configuration in [!DNL Experience Manager] to generate a public key. Erhalten Sie ein öffentliches Zertifikat für die OAuth-Integration.
* Erstellen Sie eine Integration in Adobe Developer Console und laden Sie den generierten öffentlichen Schlüssel hoch.
* Configure your [!DNL Experience Manager] instance using the API key and other credentials from Adobe Developer Console.
* Aktivieren Sie optional das automatische Tagging beim Hochladen eines Assets.

### Voraussetzungen für die Integration der Adobe Developer Console {#prerequisite-for-aio-integration}

Bevor Sie die intelligenten Tags verwenden können, stellen Sie Folgendes sicher, um eine Integration in der Adobe Developer Console zu erstellen:

* Es ist ein Adobe ID-Konto mit Administratorrechten für die Organisation vorhanden.
* Die intelligenten Tags sind für Ihr Unternehmen aktiviert.

### Obtain a public certificate {#obtain-public-certificate}

Mit einem öffentlichen Zertifikat können Sie Ihr Profil in der Adobe Developer Console authentifizieren. Sie erstellen ein Zertifikat von innen [!DNL Experience Manager].

1. Rufen Sie in der [!DNL Experience Manager] Benutzeroberfläche **[!UICONTROL Werkzeuge]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Adobe IMS-Konfigurationen]** auf.

1. Klicken Sie auf der Seite &quot; [!UICONTROL Adobe IMS-Konfigurationen] &quot;auf **[!UICONTROL Erstellen]**. Wählen Sie im Menü **[!UICONTROL Cloud-Lösung]** die Option **[!UICONTROL Smart-Tags]**.

1. Select **[!UICONTROL Create new certificate]**. Geben Sie einen Namen ein und klicken Sie auf Zertifikat **[!UICONTROL erstellen]**. Klicken Sie auf **[!UICONTROL OK]**.

1. Click **[!UICONTROL Download Public Key]**.

   ![Smart-Tags in Experience Manager erstellen öffentlichen Schlüssel](assets/aem_smarttags-config1.png)

### Bei Ablauf eines Zertifikats neu konfigurieren {#certrenew}

Wenn das Zertifikat abläuft, wird es nicht mehr als vertrauenswürdig eingestuft. Um ein neues Zertifikat hinzuzufügen, führen Sie diese Schritte aus. Sie können ein abgelaufenes Zertifikat nicht verlängern.

1. Log in your [!DNL Experience Manager] deployment as an administrator. Klicken Sie auf **[!UICONTROL Werkzeuge]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.

1. Suchen und finden Sie **[!UICONTROL dam-update-service]**-Benutzer und klicken Sie darauf. Klicken Sie auf die Registerkarte **[!UICONTROL Keystore]**.
1. Löschen Sie den vorhandenen **[!UICONTROL similaritysearch]**-Keystore mit dem abgelaufenen Zertifikat. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

   ![Löschen Sie den vorhandenen Eintrag „similaritysearch“ (Ähnlichkeitssuche) in Keystore, um ein neues Sicherheitszertifikat hinzuzufügen.](assets/smarttags_delete_similaritysearch_keystore.png)

   *Abbildung: Löschen Sie den vorhandenen`similaritysearch`Eintrag in Keystore, um ein neues Sicherheitszertifikat hinzuzufügen.*

1. Rufen Sie in der [!DNL Experience Manager] Benutzeroberfläche **[!UICONTROL Werkzeuge]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Adobe IMS-Konfigurationen]** auf. Öffnen Sie die verfügbare Smart-Tags-Konfiguration. To download a public certificate, click **[!UICONTROL Download Public Certificate]**.

1. Rufen Sie [https://console.adobe.io](https://console.adobe.io) auf und navigieren Sie zum vorhandenen Dienst im Projekt. Laden Sie das neue Zertifikat hoch und konfigurieren Sie es. Weitere Informationen zur Konfiguration finden Sie in den Anweisungen unter Adobe Developer Console-Integration [erstellen](#create-aio-integration).

### Eine Integration erstellen {#create-aio-integration}

Um intelligente Tags zu verwenden, erstellen Sie eine Integration in der Adobe Developer Console, um den API-Schlüssel, die technische Konto-ID, die Organisations-ID und den geheimen Clientschlüssel zu generieren.

1. Rufen Sie [https://console.adobe.io](https://console.adobe.io/) in einem Browser auf. Wählen Sie das entsprechende Konto aus und vergewissern Sie sich, dass die zugehörige Rolle Systemadministrator ist.
1. Erstellen Sie ein Projekt mit einem beliebigen Namen. Klicken Sie auf **[!UICONTROL Hinzufügen API]**.
1. Wählen Sie auf der Seite **[!UICONTROL Hinzufügen API]** die Option **[!UICONTROL Experience Cloud]** und dann **[!UICONTROL Smart Content]**. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie den öffentlichen Schlüssel **[!UICONTROL hochladen]**. Geben Sie die Zertifikatsdatei an, von der Sie heruntergeladen [!DNL Experience Manager]haben. Es wird eine Meldung [!UICONTROL Öffentliche Schlüssel (Schlüssel) angezeigt, die erfolgreich] hochgeladen wurden. Klicken Sie auf **[!UICONTROL Weiter]**.
1. [!UICONTROL Auf der Seite &quot;Neue Dienstkontoberechtigung] erstellen&quot;wird der öffentliche Schlüssel für das soeben konfigurierte Dienstkonto angezeigt. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie auf der Seite &quot; **[!UICONTROL Produktseiten]** auswählen&quot;die Option **[!UICONTROL &quot;Smart Content Services]**&quot;aus. Klicken Sie auf Konfigurierte API **[!UICONTROL speichern]**. Auf einer Seite werden weitere Informationen zur Konfiguration angezeigt. Lassen Sie diese Seite geöffnet, um diese Werte zu kopieren und in Experience Manager hinzuzufügen, wenn Sie Smart-Tags in weiter konfigurieren [!DNL Experience Manager].

   ![Auf der Registerkarte „Übersicht“ können Sie die für die Integration bereitgestellten Informationen überprüfen.](assets/integration_details.png)

### Intelligente Tags konfigurieren {#configure-smart-content-service}

Verwenden Sie zum Konfigurieren der Integration die Werte der Felder Payload, geheimer Clientschlüssel, Autorisierungsserver und API-Schlüssel aus der Adobe Developer Console-Integration.

1. Rufen Sie in der [!DNL Experience Manager] Benutzeroberfläche **[!UICONTROL Werkzeuge]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Adobe IMS-Konfigurationen]** auf.
1. Rufen Sie die Seite **[!UICONTROL Adobe IMS Technical Account Configuration]** auf und geben Sie einen gewünschten **[!UICONTROL Titel]** ein.
1. Geben Sie im Feld **[!UICONTROL Autorisierungsserver]** die `https://ims-na1.adobelogin.com` URL ein.
1. Geben Sie im Feld **[!UICONTROL API-Schlüssel]** die **[!UICONTROL Client-ID]** aus der [!DNL Adobe Developer Console].
1. Geben Sie im Feld **[!UICONTROL Clientgeheimnis]** den geheimen **[!UICONTROL Clientschlüssel]** aus dem Feld [!DNL Adobe Developer Console]ein. Klicken Sie auf **[!UICONTROL Clientgeheimnis]** abrufen, um es anzuzeigen.
1. Klicken Sie [!DNL Adobe Developer Console]im Projekt auf **[!UICONTROL Dienstkonto (JWT)]** am linken Rand. Klicken Sie auf die Registerkarte JWT **[!UICONTROL generieren]** . Klicken Sie auf **[!UICONTROL Kopieren]** , um die angezeigte **[!UICONTROL JWT-Nutzlast]** zu kopieren. Geben Sie diesen Wert im Feld **[!UICONTROL Nutzlast]** in [!DNL Experience Manager]. Klicken Sie auf **[!UICONTROL Erstellen]**.

### Überprüfen der Konfiguration {#validate-the-configuration}

Nachdem Sie die Konfiguration abgeschlossen haben, führen Sie die folgenden Schritte aus, um die Konfiguration zu validieren.

1. Rufen Sie in der [!DNL Experience Manager] Benutzeroberfläche **[!UICONTROL Werkzeuge]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Adobe IMS-Konfigurationen]** auf.

1. Wählen Sie die Konfiguration für intelligente Tags aus. Klicken Sie in der Symbolleiste auf **[!UICONTROL Überprüfen Sie den Zustand]** . Klicken Sie auf **[!UICONTROL Prüfen]**. Ein Dialogfeld mit der Meldung [!UICONTROL Gesunde Konfiguration] bestätigt, dass die Konfiguration funktioniert.

![Konfiguration von intelligenten Tags überprüfen](assets/smart-tag-config-validation.png)

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

