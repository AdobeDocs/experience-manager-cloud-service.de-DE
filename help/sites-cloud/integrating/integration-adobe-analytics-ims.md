---
title: IMS-Konfiguration zur Verwendung bei der Integration mit Adobe Analytics
description: Erfahren Sie mehr über die IMS-Konfiguration zur Verwendung bei der Integration mit Adobe Analytics
exl-id: 12bd1573-373a-4001-be71-c8f155ef6896
source-git-commit: d59559d38eef182723a8791c6614d03930f64a85
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 96%

---

# IMS-Konfiguration zur Verwendung bei der Integration mit Adobe Analytics {#ims-configuration-for-integration-with-adobe-analytics}

Die Integration von Adobe Experience Manager as a Cloud Service (AEMaaCS) mit Adobe Analytics über die Analytics Standard-API erfordert die Konfiguration von Adobe IMS (Identity Management System). Die Konfiguration wird mit der Adobe-Entwicklerkonsole durchgeführt.

>[!NOTE]
>
>Die Unterstützung für die Adobe Analytics Standard API 2.0 ist neu in AEMaaCS 2022.2.0. Diese API-Version unterstützt die IMS-Authentifizierung.
>
>Die API-Auswahl wird von der Authentifizierungsmethode gesteuert, die für die AEM/Analytics-Integration verwendet wird.
>
>Weitere Informationen finden Sie unter [Migration zu den 2.0-APIs](https://developer.adobe.com/analytics-apis/docs/2.0/guides/migration/).

## Voraussetzungen {#prerequisites}

Bevor Sie mit diesem Verfahren beginnen:

* Der [Adobe-Support](https://helpx.adobe.com/de/contact/enterprise-support.ec.html) muss Ihr Konto für Folgendes bereitstellen:

   * Adobe Console
   * Adobe-Entwicklerkonsole
   * Adobe Analytics und
   * Adobe IMS (Identity Management System)

* Der Systemadministrator Ihres Unternehmens sollte die Admin Console verwenden, um die erforderlichen Entwickler in Ihrem Unternehmen den relevanten Produktprofilen hinzuzufügen.

   * Dadurch erhalten bestimmte Entwickler Berechtigungen, Integrationen mithilfe der Adobe-Entwicklerkonsole zu ermöglichen.
   * Weitere Informationen finden Sie unter [Verwalten von Entwicklern](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html).


## Konfigurieren einer IMS-Konfiguration – Generieren eines öffentlichen Schlüssels {#configuring-ims-generating-a-public-key}

Der erste Schritt der Konfiguration besteht darin, in AEM eine IMS-Konfiguration zu erstellen und den öffentlichen Schlüssel zu generieren.

1. Öffnen Sie in AEM das Menü **Tools**.
1. Wählen Sie im Abschnitt **Sicherheit** die Option **Adobe IMS-Konfigurationen** aus.
1. Wählen Sie **Erstellen** aus, um **Technische Kontokonfiguration für Adobe IMS** zu öffnen.
1. Wählen Sie in der Dropdown-Liste unter **Cloud-Konfiguration** den Eintrag **Adobe Analytics** aus.
1. Aktivieren Sie **Neues Zertifikat erstellen** und geben Sie einen neuen Alias ein.
1. Bestätigen Sie mit **Zertifikat erstellen**.

   ![Zertifikat erstellen](assets/integrate-analytics-ims-01.png)

1. Wählen Sie **Herunterladen** (oder **Öffentlichen Schlüssel herunterladen**) aus, um die Datei auf Ihr lokales Laufwerk herunterzuladen, damit sie einsatzbereit ist, wenn Sie [IMS für die Adobe Analytics-Integration mit AEM konfigurieren](#configuring-ims-adobe-analytics-integration-with-aem).

   >[!CAUTION]
   >
   >Lassen Sie diese Konfiguration geöffnet, denn sie wird beim [Abschließen der IMS-Konfiguration in AEM](#completing-the-ims-configuration-in-aem) wieder benötigt.

   ![Zertifikat herunterladen](assets/integrate-analytics-ims-02.png)

## Konfigurieren von IMS für die Adobe Analytics-Integration mit AEM {#configuring-ims-adobe-analytics-integration-with-aem}

Mithilfe der Adobe-Entwicklerkonsole müssen Sie ein Projekt (Integration) mit Adobe Analytics erstellen (zur Verwendung durch AEM) und dann die erforderlichen Berechtigungen zuweisen.

### Erstellen des Projekts {#creating-the-project}

Öffnen Sie die Adobe-Entwicklerkonsole, um ein Projekt mit Adobe Analytics zu erstellen, das AEM verwenden wird:

>[!CAUTION]
>
>Derzeit unterstützen wir nur die **Dienstkonto (JWT)** Berechtigungstyp.
>
>Verwenden Sie nicht das **OAuth Server-zu-Server** Berechtigungstyp, der in Zukunft unterstützt wird.

1. Öffnen Sie die Adobe-Entwicklerkonsole für Projekte:

   [https://developer.adobe.com/console/projects](https://developer.adobe.com/console/projects)

1. Alle vorhandenen Projekte werden angezeigt. Wählen Sie **Neues Projekt erstellen** aus. Position und Verwendung hängen von Folgendem ab:

   * Wenn Sie noch kein Projekt haben, befindet sich **Neues Projekt erstellen** unten in der Mitte.

     ![Neues Projekt erstellen – Erstes Projekt](assets/integration-analytics-ims-02.png)
   * Wenn Sie bereits über vorhandene Projekte verfügen, werden diese aufgelistet und **Neues Projekt erstellen** wird oben rechts angezeigt.

     ![Neues Projekt erstellen – Mehrere Projekte](assets/integration-analytics-ims-03.png)


1. Wählen Sie **Zum Projekt hinzufügen** und dann **API** aus:

   ![Erste Schritte mit Ihrem neuen Projekt](assets/integration-analytics-ims-10.png)

1. Wählen Sie **Adobe Analytics** und dann **Weiter** aus:

   >[!NOTE]
   >
   >Wenn Sie Adobe Analytics abonniert haben, es jedoch nicht aufgeführt wird, sollten Sie die [Voraussetzungen](#prerequisites) prüfen.

   ![Hinzufügen einer API](assets/integration-analytics-ims-12.png)

1. Wählen Sie **Dienstkonto (JWT)** als Authentifizierungstyp aus und setzen Sie den Vorgang mit **Weiter** fort:

   ![Authentifizierungstyp auswählen](assets/integration-analytics-ims-12a.png)

1. **Laden Sie Ihren öffentlichen Schlüssel hoch** und setzen Sie den Vorgang anschließend mit **Weiter** fort:

   ![Öffentlichen Schlüssel hochladen](assets/integration-analytics-ims-13.png)

1. Überprüfen Sie die Anmeldeinformationen und setzen Sie den Vorgang mit **Weiter** fort:

   ![Anmeldeinformationen überprüfen](assets/integration-analytics-ims-15.png)

1. Wählen Sie die erforderlichen Produktprofile aus und setzen Sie den Vorgang mit **Konfigurierte API speichern** fort:

   ![Erforderliche Produktprofile auswählen](assets/integration-analytics-ims-16.png)

1. Die Konfiguration wird bestätigt.

### Zuweisen von Berechtigungen zur Integration {#assigning-privileges-to-the-integration}

Sie müssen der Integration jetzt die erforderlichen Berechtigungen zuweisen:

1. Öffnen Sie die Adobe **Admin Console**:

   * [https://adminconsole.adobe.com](https://adminconsole.adobe.com/)

1. Navigieren Sie zu **Produkte** (obere Symbolleiste) und wählen Sie **Adobe Analytics - &lt;*Ihre-Mandanten-ID*>** (im linken Bereich) aus.
1. Wählen Sie **Produktprofile** und dann den gewünschten Arbeitsbereich aus der angezeigten Liste aus. Beispielsweise den Standardarbeitsbereich.
1. Wählen Sie **API-Anmeldeinformationen** und dann die erforderliche Integrationskonfiguration aus.
1. Wählen Sie **Editor** als **Produktrolle** aus anstelle von **Beobachter**.

## Für das Integrationsprojekt in der Adobe-Entwicklerkonsole gespeicherte Details {#details-stored-for-the-ims-integration-project}

In der Adobe-Entwicklerkonsole wird eine Liste aller Integrationsprojekte angezeigt:

* [https://developer.adobe.com/console/projects](https://developer.adobe.com/console/projects)

Wählen Sie einen bestimmten Projekteintrag aus, um weitere Details zur Konfiguration anzuzeigen. Dazu gehören:

* Projektübersicht
* Insights
* Berechtigungen
   * Dienstkonto (JWT)
      * Details zu Anmeldedaten
      * JWT generieren
* APIs
   * Beispiel: Adobe Analytics

Einige dieser Details benötigen Sie, um die Integration von Adobe Analytics in AEM basierend auf IMS abzuschließen.

## Abschließen der IMS-Konfiguration in AEM {#completing-the-ims-configuration-in-aem}

Wenn Sie zu AEM zurückkehren, können Sie die IMS-Konfiguration abschließen, indem Sie die erforderlichen Werte aus der IMS-Integration für Analytics hinzufügen:

1. Kehren Sie zur [in AEM geöffneten IMS-Konfiguration](#configuring-ims-generating-a-public-key) zurück.
1. Wählen Sie **Weiter** aus.

1. Hier können Sie die [Details aus der Projektkonfiguration in der Adobe-Entwicklerkonsole](#details-stored-for-the-ims-integration-project) verwenden:

   * **Titel**: Ihr Text.
   * **Autorisierungs-Server**: Übernehmen Sie diese Angabe per Kopieren und Einfügen aus der `aud`-Zeile im Abschnitt **Payload** unten, z. B. `https://ims-na1.adobelogin.com` im nachstehenden Beispiel.
   * **API-Schlüssel**: Kopieren Sie dies aus dem Abschnitt **Anmeldedaten** in der [Projektübersicht](#details-stored-for-the-ims-integration-project).
   * **Client-Geheimnis**: Generieren Sie dies auf der [Registerkarte „Client-Geheimnis“ im Abschnitt „Dienstkonto (JWT)“](#details-stored-for-the-ims-integration-project) und kopieren Sie es.
   * **Payload**: Kopieren Sie dies von der [Registerkarte „JWT generieren“ im Abschnitt „Dienstkonto (JWT)“](#details-stored-for-the-ims-integration-project).

   ![AEM IMS-Konfigurationsdetails](assets/integrate-analytics-ims-10.png)

1. Bestätigen Sie mit **Erstellen**.

1. Ihre Adobe Analytics-Konfiguration wird in der AEM-Konsole angezeigt.

   ![IMS-Konfiguration](assets/integrate-analytics-ims-11.png)

## Überprüfen der IMS-Konfiguration {#confirming-the-ims-configuration}

So überprüfen Sie, ob die Konfiguration erwartungsgemäß funktioniert:

1. Öffnen Sie:

   * `https://localhost<port>/libs/cq/adobeims-configuration/content/configurations.html`

   Beispiel:

   * `https://localhost:4502/libs/cq/adobeims-configuration/content/configurations.html`

1. Wählen Sie Ihre Konfiguration aus.
1. Wählen **Konsistenzprüfung** auf der Symbolleiste aus, gefolgt von **Überprüfen**.

   ![IMS-Konfiguration – Konsistenzprüfung](assets/integrate-analytics-ims-12.png)

1. Bei erfolgreicher Ausführung wird eine Bestätigungsmeldung angezeigt.

## Abschließen der Integration mit Adobe Analytics {#complete-the-integration-with-adobe-analytics}

Sie können jetzt diese IMS-Konfiguration verwenden, um die [Integration mit Adobe Analytics](/help/sites-cloud/integrating/integrating-adobe-analytics.md) abzuschließen.

<!--
## Configuring the Adobe Analytics Cloud Service {#configuring-the-adobe-analytics-cloud-service}

The configuration can now be referenced for a Cloud Service to use the Analytics Standard API:

1. Open the **Tools** menu. Then, within the **Cloud Services** section, select **Legacy Cloud Services**.
1. Scroll down to **Adobe Analytics** and select **Configure now**.

   The **Create Configuration** dialog will open.

1. Enter a **Title** and, if you want, a **Name** (if left blank, it is generated from the title).

   You can also select the required template (if more than one is available).

1. Confirm with **Create**.

   The **Edit Component** dialog will open.

1. Enter the details in the **Analytics Settings** tab:

    * **Authentication**: IMS

    * **IMS Configuration**: select the name of the IMS Configuration

1. Click **Connect to Analytics** to initialize the connection with Adobe Analytics.

   If the connection is successful, the message **Connection successful** is displayed.

1. Select **OK** on the message.

1. Complete other parameters as required, followed by **OK** on the dialog to confirm the configuration.

1. You can now proceed to [Adding an Analytics Framework](/help/sites-administering/adobeanalytics-connect.md) to configure parameters that are sent to Adobe Analytics. 
-->
