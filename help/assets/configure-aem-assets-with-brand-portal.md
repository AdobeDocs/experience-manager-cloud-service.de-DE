---
title: Konfigurieren von AEM Assets Cloud Service mit Brand Portal
description: Konfigurieren von AEM Assets Cloud Service mit Brand Portal.
contentOwner: Vishabh Gupta
translation-type: tm+mt
source-git-commit: 00e37e9493bc3dde8a4d83c562a889a67587ada0
workflow-type: tm+mt
source-wordcount: '1336'
ht-degree: 99%

---


# Konfigurieren von AEM Assets mit Brand Portal {#configure-aem-assets-with-brand-portal}

Adobe Experience Manager (AEM) Assets wird über Adobe I/O in Brand Portal konfiguriert. Dadurch wird ein IMS-Token zur Autorisierung Ihres Brand Portal-Mandanten abgerufen.

## Voraussetzungen {#prerequisites}

Sie benötigen Folgendes, um AEM Assets mit Brand Portal zu konfigurieren:

* Eine AEM Assets-Cloud-Instanz, die ausgeführt wird.
* Brand Portal-Mandanten-URL
* Ein Benutzer mit Systemadministrator-Berechtigungen für die IMS-Organisation des Brand Portal-Mandanten

**Wenden Sie sich für weitere Abfragen an den Kundendienst** .

## Erstellen der Konfiguration {#create-new-configuration}

Sie können eine Konfiguration in Adobe I/O erstellen, um Ihre AEM Assets-Cloud-Instanz mit Brand Portal zu konfigurieren.

Führen Sie die folgenden Schritte in der angegebenen Reihenfolge aus:
1. [Abrufen eines öffentlichen Zertifikats](#public-certificate)
1. [Erstellen der Adobe I/O-Integration](#createnewintegration)
1. [Erstellen der Konfiguration des IMS-Kontos](#create-ims-account-configuration)
1. [Konfigurieren von Cloud Service](#configure-the-cloud-service)
1. [Testen der Konfiguration](#test-configuration)

### Erstellen der IMS-Konfiguration {#create-ims-configuration}

Die IMS-Konfiguration authentifiziert Ihren Brand Portal-Mandanten mit der Autoreninstanz von AEM Assets.

Die IMS-Konfiguration umfasst zwei Schritte:

* [Abrufen eines öffentlichen Zertifikats](#public-certificate)
* [Erstellen der Konfiguration des IMS-Kontos](#create-ims-account-configuration)

### Abrufen eines öffentlichen Zertifikats {#public-certificate}

Ein öffentliches Zertifikat ermöglicht Ihnen die Authentifizierung Ihres Profils in Adobe I/O.

1. Melden Sie sich bei Ihrer AEM Assets-Cloud-Instanz an.

1. Navigieren Sie im **Tool** ![Tools](assets/tools.png)-Bedienfeld zu **[!UICONTROL Sicherheit]** > **[!UICONTROL Adobe IMS-Konfigurationen]**.

   ![Benutzeroberfläche der Adobe IMS-Kontokonfiguration](assets/ims-configuration1.png)

1. Die Seite für Adobe IMS-Konfigurationen wird geöffnet.

   Klicken Sie auf **[!UICONTROL Erstellen]**.

   Sie gelangen auf die Seite für die **[!UICONTROL Konfiguration des technischen Adobe IMS-Kontos]**.

1. Standardmäßig wird die Registerkarte **Zertifikat** geöffnet.

   Wählen Sie in **Cloud-Lösung** die Option **[!UICONTROL Adobe Brand Portal]** aus.

1. Markieren Sie das Kontrollkästchen **[!UICONTROL Neues Zertifikat erstellen]** und geben Sie einen **Alias** für das Zertifikat an. Der Alias dient als Name des Dialogfelds.

1. Klicken Sie auf **[!UICONTROL Zertifikat erstellen]**. Ein Dialogfeld wird angezeigt. Klicken Sie auf **[!UICONTROL OK]**, um das öffentliche Zertifikat zu generieren.

   ![Zertifikat erstellen](assets/ims-config2.png)

1. Klicken Sie auf **[!UICONTROL Öffentlichen Schlüssel herunterladen]** und speichern Sie die Zertifikatdatei *AEM-Adobe-IMS.crt* auf Ihrem Computer. Die Zertifikatdatei wird verwendet, um die [Adobe I/O-Integration zu erstellen](#createnewintegration).

   ![Zertifikat herunterladen](assets/ims-config3.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**.

   Um auf der Registerkarte **Konto** das Adobe IMS-Konto zu erstellen, benötigen Sie die Integrationsdetails. Lassen Sie diese Seite vorerst offen.

   Öffnen Sie eine neue Registerkarte und [erstellen Sie die Adobe I/O-Integration](#createnewintegration), um die Integrationsdetails für IMS-Kontokonfigurationen abzurufen.

### Erstellen der Adobe I/O-Integration {#createnewintegration}

Die Adobe-I/O-Integration generiert API-Schlüssel, Client-Geheimnis und Payload (JWT), die zum Einrichten der IMS-Kontokonfigurationen erforderlich sind.

1. Melden Sie sich bei der Adobe I/O-Konsole mit Systemadministrator-Berechtigungen für die IMS-Organisation des Brand Portal-Mandanten an.

   Standard-URL: [https://console.adobe.io/](https://console.adobe.io/)

1. Klicken Sie auf **[!UICONTROL Integration erstellen]**.

1. Wählen Sie **[!UICONTROL Auf API zugreifen]** aus und klicken Sie auf **[!UICONTROL Weiter]**.

   ![Neue Integration erstellen](assets/create-new-integration1.png)

1. Eine neue Integrationsseite wird geöffnet.

   Wählen Sie Ihre Organisation aus der Dropdown-Liste aus.

   Wählen Sie in **[!UICONTROL Experience Cloud]** den Eintrag **[!UICONTROL AEM Brand Portal]** aus und klicken Sie auf **[!UICONTROL Weiter]**.

   Wenn die Option „Brand Portal“ für Sie deaktiviert ist, stellen Sie sicher, dass Sie die richtige Organisation aus dem Dropdown-Feld über der Option **[!UICONTROL Adobe Services]** ausgewählt haben. Wenn Sie Ihre Organisation nicht kennen, wenden Sie sich an Ihren Administrator.

   ![Integration erstellen](assets/create-new-integration2.png)

1. Geben Sie einen Namen und eine Beschreibung für die Integration an. Klicken Sie auf **[!UICONTROL Eine Datei von Ihrem Computer auswählen]** und laden Sie die `AEM-Adobe-IMS.crt`-Datei hoch, die im Abschnitt [Öffentliche Zertifikate erhalten](#public-certificate) heruntergeladen wurde.

1. Wählen Sie das Profil Ihrer Organisation aus.

   Sie können auch das Standardprofil **[!UICONTROL Assets Brand Portal]** auswählen und auf **[!UICONTROL Integration erstellen]** klicken. Die Integration wird erstellt.

1. Klicken Sie auf **[!UICONTROL Weiter zu Integrationsdetails]**, um die Integrationsinformationen anzuzeigen.

   Kopieren Sie den **[!UICONTROL API-Schlüssel]**.

   Klicken Sie auf **[!UICONTROL Client-Geheimnis abrufen]** und kopieren Sie den Client-Geheimnisschlüssel.

   ![API-Schlüssel, Client-Geheimnis und Payload-Daten einer Integration ](assets/create-new-integration3.png)

1. Navigieren Sie zur Registerkarte **[!UICONTROL JWT]** und kopieren Sie die **[!UICONTROL JWT-Payload]**.

   API-Schlüssel, Client-Geheimnisschlüssel und JWT-Payload-Informationen werden verwendet, um eine IMS-Kontokonfiguration zu erstellen.

### Erstellen der Konfiguration des IMS-Kontos {#create-ims-account-configuration}

Stellen Sie sicher, dass Sie die folgenden Schritte ausgeführt haben:

* [Abrufen eines öffentlichen Zertifikats](#public-certificate)
* [Erstellen der Adobe I/O-Integration](#createnewintegration)

**Schritte zum Erstellen der Konfiguration des IMS-Kontos:**

1. Öffnen Sie die Seite „IMS-Konfiguration“, Registerkarte **[!UICONTROL Konten]**. Sie haben die Seite am Ende des Abschnitts [Abrufen eines öffentlichen Zertifikats](#public-certificate) geöffnet gelassen.

1. Geben Sie einen **[!UICONTROL Titel]** für das IMS-Konto an.

   Geben Sie in **[!UICONTROL Autorisierungsserver]** die URL ein: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Fügen Sie den API-Schlüssel, den Client-Geheimnisschlüssel und die JWT-Payload ein, die Sie am Ende von [Erstellen der Adobe I/O-Integration](#createnewintegration) kopiert haben.

   Klicken Sie auf **[!UICONTROL Erstellen]**.

   Die Integration wird erstellt.

   ![IMS-Kontokonfiguration](assets/create-new-integration6.png)


1. Wählen Sie die IMS-Konfiguration aus und klicken Sie auf **[!UICONTROL Systemdiagnose]**. Das folgende Dialogfeld wird angezeigt.

   Klicken Sie auf **[!UICONTROL Prüfen]**. Bei erfolgreicher Verbindung wird die Meldung *Token erfolgreich abgerufen* angezeigt.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>Sie dürfen nur eine IMS-Konfiguration haben. Erstellen Sie nicht mehrere IMS-Konfigurationen.
>
>Vergewissern Sie sich, dass die IMS-Konfiguration die Konsistenzprüfung besteht. Wenn die Konfiguration die Konsistenzprüfung nicht besteht, ist sie ungültig. Sie müssen sie löschen und eine neue gültige Konfiguration erstellen.



### Konfigurieren von Cloud Service {#configure-the-cloud-service}

Führen Sie die folgenden Schritte aus, um eine Cloud Service-Konfiguration für Brand Portal zu erstellen:

1. Melden Sie sich bei Ihrer AEM Assets-Cloud-Instanz an.

1. Navigieren Sie im **Tool** ![Tools](assets/tools.png)-Bedienfeld zu **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**.

   Die Seite zur Brand Portal-Konfiguration wird geöffnet.

1. Klicken Sie auf **[!UICONTROL Erstellen]**.

1. Geben Sie einen **[!UICONTROL Titel]** für die Konfiguration ein.

   Wählen Sie die im Schritt erstellte IMS-Konfiguration aus und [erstellen Sie die IMS-Kontokonfiguration](#create-ims-account-configuration).

   Geben Sie in **[!UICONTROL Dienst-URL]** Ihre Brand Portal-Mandanten-URL ein.

   ![](assets/create-cloud-service.png)

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**. Die Cloud-Konfiguration wird erstellt. Ihre AEM Assets-Cloud-Instanz ist jetzt mit dem Brand Portal-Mandanten konfiguriert.

### Testen der Konfiguration {#test-configuration}

1. Melden Sie sich bei Ihrer AEM Assets-Cloud-Instanz an.

1. Navigieren Sie im **Tool** ![Tools](assets/tools.png)-Bedienfeld zu **[!UICONTROL Bereitstellung]** > **[!UICONTROL Verteilung]**.

   ![](assets/test-bpconfig1.png)

1. Die Seite für die Verteilung wird geöffnet.

   Ein Brand Portal-Verteilungsagent `bpdistributionagent0` wird unter **[!UICONTROL In Brand Portal veröffentlichen]** erstellt.

   Klicken Sie auf **[!UICONTROL In Brand Portal veröffentlichen]**.

   ![](assets/test-bpconfig2.png)

   >[!NOTE]
   >
   >Standardmäßig wird für einen Brand Portal-Mandanten ein Verteilungsagent erstellt.

1. Die Seite für die Verteilungsagenten wird geöffnet. Standardmäßig wird die Registerkarte **[!UICONTROL Status]** geöffnet, in der die Verteilungswarteschlangen gefüllt werden.

   Ein Verteilungsagent enthält zwei Warteschlangen:
   * **Verarbeitungswarteschlange (processing-queue)**: für die Verteilung von Assets an Brand Portal.

   * **Fehlerwarteschlange (error-queue)**: für die Assets, bei denen die Verteilung fehlgeschlagen ist.
   >[!NOTE]
   >
   >Es wird empfohlen, die Fehler zu überprüfen und die **Fehlerwarteschlange** regelmäßig zu löschen.

   ![](assets/test-bpconfig3.png)

1. Um die Verbindung zwischen AEM Assets und Brand Portal zu überprüfen, klicken Sie auf **[!UICONTROL Verbindung testen]**.

   ![](assets/test-bpconfig4.png)

   Unten auf der Seite wird eine Meldung angezeigt, dass Ihr Testpaket erfolgreich bereitgestellt wurde.

   >[!NOTE]
   >
   >Vermeiden Sie das Deaktivieren des Verteilungsagenten, da dies dazu führen kann, dass die Verteilung der Assets (in der Warteschlange) fehlschlägt.


Ihre AEM Assets-Cloud-Instanz wurde erfolgreich mit Brand Portal konfiguriert. Jetzt können Sie Folgendes ausführen:

* [Veröffentlichen von Assets aus AEM Assets in Brand Portal](publish-to-brand-portal.md)
* [Veröffentlichen von Ordnern aus AEM Assets in Brand Portal](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Veröffentlichen von Sammlungen aus AEM Assets in Brand Portal](publish-to-brand-portal.md#publish-collections-to-brand-portal)

Darüber hinaus können Sie Metadatenschemata, Bildvorgaben, Suchfacetten und Tags von AEM Assets in Brand Portal veröffentlichen.

* [Veröffentlichen von Vorgaben, Schemata und Facetten in Brand Portal](https://docs.adobe.com/content/help/de-DE/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [Veröffentlichen von Tags in Brand Portal](https://docs.adobe.com/content/help/de-DE/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)


Weitere Informationen finden Sie in der [Dokumentation zu Brand Portal](https://docs.adobe.com/content/help/de-DE/experience-manager-brand-portal/using/home.html).


## Verteilungsprotokolle {#distribution-logs}

In den Protokollen finden Sie detaillierte Informationen zu den Aktionen, die mit dem Verteilungsagenten ausgeführt werden.

Beispielsweise haben wir ein Asset aus AEM Assets in Brand Portal veröffentlicht, um die Konfiguration zu überprüfen.

1. Führen Sie die Schritte (Schritt 1–4) aus, wie in **[!UICONTROL Verbindung testen]** gezeigt, und navigieren Sie zur Seite des Verteilungsagenten.

1. Klicken Sie auf **[!UICONTROL Protokolle]**, um die Verteilungsprotokolle anzuzeigen. Hier können Sie die Verarbeitungs- und Fehlerprotokolle sehen.

   ![](assets/test-bpconfig5.png)

Der Verteilungsagenten generiert die folgenden Protokolle:

* INFO: Dies ist ein vom System erstelltes Protokoll, das bei einer erfolgreichen Konfiguration ausgelöst wird, die den Verteilungsagenten aktiviert.
* DSTRQ1 (Anfrage 1): Wird bei der Testverbindung ausgelöst.

Beim Veröffentlichen des Assets werden die folgenden Anfrage- und Antwortprotokolle generiert:

**Anfrage des Verteilungsagenten**:
* DSTRQ2 (Anfrage 2): Die Anfrage zur Veröffentlichung des Assets wird ausgelöst.
* DSTRQ3 (Anfrage 3): Das System löst eine weitere Anfrage zum Veröffentlichen des Ordners aus, in dem sich das Asset befindet, und repliziert den Ordner in Brand Portal.

**Antwort des Verteilungsagenten**:
* queue-bpdistributionagent0 (DSTRQ2): Das Asset wird in Brand Portal veröffentlicht.
* queue-bpdistributionagent0 (DSTRQ3): Das System repliziert den Ordner, der das Asset enthält, in Brand Portal.

Im obigen Beispiel werden eine zusätzliche Anfrage und Antwort ausgelöst. Das System konnte den übergeordneten Ordner (auch als Hinzufügen-Pfad bezeichnet) in Brand Portal nicht finden, da das Asset zum ersten Mal veröffentlicht wurde. Daher wird eine zusätzliche Anfrage ausgelöst, einen übergeordneten Ordner mit demselben Namen in Brand Portal zu erstellen, in dem das Asset veröffentlicht wird.

>[!NOTE]
>
>Es wird eine zusätzliche Anfrage generiert, wenn der übergeordnete Ordner nicht in Brand Portal vorhanden ist (im oben stehenden Beispiel) oder der übergeordnete Ordner in AEM Assets geändert wurde.



<!--

## Additional information {#additional-information}

Go to `/system/console/slingmetrics` for statistics related to the distributed content:

1. **Counter metrics**
   * sling: `mac_sync_request_failure`
   * sling: `mac_sync_request_received`
   * sling: `mac_sync_request_success`

1. **Time metrics**
   * sling: `mac_sync_distribution_duration`
   * sling: `mac_sync_enqueue_package_duration`
   * sling: `mac_sync_setup_request_duration`

-->

<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->
