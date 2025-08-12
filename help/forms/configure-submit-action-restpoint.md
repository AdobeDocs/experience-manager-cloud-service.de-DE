---
title: Konfigurieren der Sendeaktion „An REST-Endpunkt übermitteln“ für ein adaptives Formular
description: Erfahren Sie, wie Sie beim Senden eines adaptiven Formulars einen REST-Endpunkt einrichten.
keywords: AEM Forms REST-Endpunkt, An REST-Endpunkt übermitteln, Daten an REST-URL posten, REST-Endpoint-Aktion konfigurieren
feature: Adaptive Forms, Core Components, Foundation Components, Edge Delivery Services
role: User, Developer
exl-id: 58c63ba6-aec5-4961-a70a-265990ab9cc8
source-git-commit: 44a8d5d5fdd2919d6d170638c7b5819c898dcefe
workflow-type: tm+mt
source-wordcount: '1471'
ht-degree: 98%

---

# Konfigurieren eines adaptiven Formulars für die REST-Endpunkt-Übermittlungsaktion

<span class="preview"> Die Funktion zum Angeben des REST-Endpunkts per Konfiguration ist ein Early-Adopter-Programm und gilt nur für Kernkomponenten- und Edge Delivery Services-Formulare. Sie können von Ihrer offiziellen E-Mail-ID aus an `aem-forms-ea@adobe.com` schreiben, um dem Early-Adopter-Programm beizutreten und Zugriff auf die Funktion anzufordern. </span>

Verwenden Sie die Aktion **[!UICONTROL An REST-Endpunkt übermitteln]**, um die übertragenen Daten an eine Rest-URL zu veröffentlichen. Die URL kann sich auf einem internen Server (dem Server, auf dem das Formular gerendert wird) oder auf einem externen Server befinden.

AEM as a Cloud Service bietet verschiedene vordefinierte Übermittlungsaktionen für die Verarbeitung von Formularübermittlungen. Weitere Informationen zu diesen Optionen finden Sie im Artikel [Übermittlungsaktion für adaptive Formulare](/help/forms/aem-forms-submit-action.md).

## Vorteile

Einige Vorteile der Konfiguration der Übermittlungsaktion **[!UICONTROL An REST-Endpunkt übermitteln]** für adaptive Formulare sind:

* Sie ermöglicht die nahtlose Integration von Formulardaten in externe Systeme und Dienste über RESTful-APIs.
* Sie bietet Flexibilität bei der Verarbeitung von Datenübermittlungen aus adaptiven Formularen und unterstützt dynamische und komplexe Datenstrukturen.
* Sie unterstützt die dynamische Zuordnung von Formularfeldern zu Parametern in der REST-Endpunkt-URL, was eine anpassbare und benutzerdefinierte Datenübermittlung ermöglicht.


## Konfigurieren der Übermittlungsaktion als „An REST-Endpunkt übermitteln“ {#steps-to-configure-submit-to-restendpoint-submit-action}

>[!BEGINTABS]

>[!TAB Foundation-Komponente]

So konfigurieren Sie eine Übermittlungsaktion basierend auf der Swagger Open API-Spezifikation für ein auf Foundation-Komponenten basierendes adaptives Formular:

1. Öffnen Sie das adaptive Formular zur Bearbeitung und navigieren Sie zum Abschnitt **[!UICONTROL Übermittlung]** der Eigenschaften des Containers für adaptive Formulare.
1. Wählen Sie aus der Dropdown-Liste **[!UICONTROL Übermittlungsaktion]** die Option **[!UICONTROL An REST-Endpunkt übermitteln]**.

   ![Aktionskonfiguration für „An REST-Endpunkt übermitteln“](/help/forms/assets/submit-action-restendpoint.png)

   Um Daten auf einem internen Server zu senden, geben Sie den Pfad der Ressource an. Die Daten werden an den Pfad der Ressource gesendet. Beispiel: `/content/restEndPoint`. Für solche Sende-Anfragen werden die Authentifizierungsinformationen der Versandanfrage verwendet.
Mit dieser Option können Sie den Ziel-REST-Endpunkt direkt eingeben.
Geben Sie eine URL an, um Daten an einen externen Server zu senden. Das Format der URL ist `https://host:port/path_to_rest_end_point`. Stellen Sie sicher, dass Sie den Pfad zum Handhaben der POST-Anforderung anonym konfigurieren.
   ![Zuordnung zur Weitergabe von Feldwerten als Anforderungsparameter für die Dankeseite](assets/post-enabled-actionconfig.png)

   Im obigen Beispiel hat der Benutzer Informationen in die `textbox` eingegeben, die mithilfe von Parameter `param1` erfasst werden. Die Syntax zur Veröffentlichung erfasster Daten mithilfe von `param1` lautet:

   `String data=request.getParameter("param1");`

   Auch Parameter, die Sie für die Veröffentlichung von XML-Daten und Anlagen verwenden, sind `dataXml` und `attachments`.

   Beispielsweise können Sie diese beiden Parameter in Ihrem Skript verwenden, um Daten an einem REST-Endpunkt zu analysieren. Verwenden Sie die folgende Syntax, um Daten zu speichern und zu analysieren:

   `String data=request.getParameter("dataXml");`
   `String att=request.getParameter("attachments");`

   In diesem Beispiel speichert `data` die XML-Daten, und `att` speichert Anhangdaten.
Die Übermittlungsoption **[!UICONTROL An REST-Endpunkt übermitteln]** übermittelt die im Formular eingetragenen Daten zu einer konfigurierten Bestätigungsseite im Rahmen der HTTP-GET-Anfrage. Sie können den Namen der anzufordernden Felder hinzufügen. Das Format der Anfrage lautet:
   `{fieldName}={request parameter name}`

   Wie in der folgenden Abbildung dargestellt, werden `param1` und `param2` als Parameter mit Werten, die aus den Feldern **textbox** und **numericbox** kopiert wurden, für die nächste Aktion weitergeleitet.

   ![Konfigurieren der Übermittlungsaktion „An REST-Endpunkt übermitteln“](assets/action-config.png)

   Sie können auch **[!UICONTROL POST-Anforderungen aktivieren]** und eine URL eingeben, um die Anforderung zu veröffentlichen. Um Daten an den AEM-Server, auf dem sich das Formular befindet, zu senden, verwenden Sie einen relativen Pfad entsprechend dem Stammpfad des AEM-Servers. Beispiel: `/content/forms/af/SampleForm.html`. Wenn Sie Daten an irgendeinen anderen Server senden, verwenden Sie den absoluten Pfad.

1. Klicken Sie auf **[!UICONTROL Fertig]**.

>[!TAB Kernkomponente]

So konfigurieren Sie eine Übermittlungsaktion basierend auf der Swagger Open API-Spezifikation für ein auf Kernkomponenten basierendes adaptives Formular:

1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Übermittlung]**.
1. Wählen Sie aus der Dropdown-Liste **[!UICONTROL Übermittlungsaktion]** die Option **[!UICONTROL An REST-Endpunkt übermitteln]**.

   ![Konfigurieren des REST-Endpunkts](assets/rest-service-endpoint-config.png)

   Um Daten auf einem internen Server zu senden, geben Sie den Pfad der Ressource an. Die Daten werden an den Pfad der Ressource gesendet. Beispiel: `/content/restEndPoint`. Für solche Sende-Anfragen werden die Authentifizierungsinformationen der Versandanfrage verwendet.

   Sie haben zwei Möglichkeiten, den REST-Endpunkt anzugeben:

   +++URL

   Mit dieser Option können Sie den Ziel-REST-Endpunkt direkt eingeben.
Geben Sie eine URL an, um Daten an einen externen Server zu senden. Das Format der URL ist `https://host:port/path_to_rest_end_point`. Stellen Sie sicher, dass Sie den Pfad zum Handhaben der POST-Anforderung anonym konfigurieren.

   ![Zuordnung zur Weitergabe von Feldwerten als Anforderungsparameter für die Dankeseite](assets/post-enabled-actionconfig.png)

   Im obigen Beispiel hat der Benutzer Informationen in die `textbox` eingegeben, die mithilfe von Parameter `param1` erfasst werden. Die Syntax zur Veröffentlichung erfasster Daten mithilfe von `param1` lautet:

   `String data=request.getParameter("param1");`

   Auch Parameter, die Sie für die Veröffentlichung von XML-Daten und Anlagen verwenden, sind `dataXml` und `attachments`.

   Beispielsweise können Sie diese beiden Parameter in Ihrem Skript verwenden, um Daten an einem REST-Endpunkt zu analysieren. Verwenden Sie die folgende Syntax, um Daten zu speichern und zu analysieren:

   `String data=request.getParameter("dataXml");`
   `String att=request.getParameter("attachments");`

   In diesem Beispiel speichert `data` die XML-Daten, und `att` speichert Anlagendaten.

   Die Übermittlungsoption **[!UICONTROL An REST-Endpunkt übermitteln]** übermittelt die im Formular eingetragenen Daten zu einer konfigurierten Bestätigungsseite im Rahmen der HTTP-GET-Anfrage. Sie können den Namen der anzufordernden Felder hinzufügen. Das Format der Anfrage lautet:

   `{fieldName}={request parameter name}`

   Wie in der folgenden Abbildung dargestellt, werden `param1` und `param2` als Parameter mit Werten, die aus den Feldern **textbox** und **numericbox** kopiert wurden, für die nächste Aktion weitergeleitet.

   ![Konfigurieren der Übermittlungsaktion „An REST-Endpunkt übermitteln“](assets/action-config.png)

   Sie können auch **[!UICONTROL POST-Anforderungen aktivieren]** und eine URL eingeben, um die Anforderung zu veröffentlichen. Um Daten an den AEM-Server, auf dem sich das Formular befindet, zu senden, verwenden Sie einen relativen Pfad entsprechend dem Stammpfad des AEM-Servers. Beispiel: `/content/forms/af/SampleForm.html`. Wenn Sie Daten an irgendeinen anderen Server senden, verwenden Sie den absoluten Pfad.

   +++

   +++Konfiguration

   Mit dieser Option können Sie eine vordefinierte HTTP-Konfiguration hinzufügen, die über den Konfigurations-Browser von AEM verwaltet wird. Sie können die Konfiguration auswählen, die Sie für den Authentifizierungstyp Ihres Dienst-REST-Endpunkts und die Inhaltstypen erstellt haben. Weitere Informationen zum Authentifizierungstyp und zu den Inhaltstypen finden Sie unter [Konfigurieren von Datenquellen](/help/forms/configure-data-sources.md#configure-restful-services-using-service-endpoint-configure-restful-services-service-endpoint).

   +++

1. Klicken Sie auf **[!UICONTROL Fertig]**.

>[!TAB Universeller Editor]

So konfigurieren Sie eine Übermittlungsaktion basierend auf der Swagger Open API-Spezifikation für ein im universellen Editor erstelltes adaptives Formular:

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Klicken Sie im Editor auf die Erweiterung **Formulareigenschaften bearbeiten**.
Das Dialogfeld **Formulareigenschaften** wird angezeigt.
   >[!NOTE]
   >
   > * Wenn das Symbol **Formulareigenschaften bearbeiten** in der Benutzeroberfläche des universellen Editors nicht angezeigt wird, aktivieren Sie die Erweiterung **Formulareigenschaften bearbeiten** im Extension Manager.
   > * Informationen zum Aktivieren und Deaktivieren von Erweiterungen im universellen Editor finden Sie im Artikel [Extension Manager – Highlights der Funktionen](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).
1. Klicken Sie auf **Übermittlung** und wählen Sie die Übermittlungsaktion **[!UICONTROL An REST-Endpunkt übermitteln]** aus.

   Um Daten auf einem internen Server zu senden, geben Sie den Pfad der Ressource an. Die Daten werden an den Pfad der Ressource gesendet. Beispiel: `/content/restEndPoint`. Für solche Sende-Anfragen werden die Authentifizierungsinformationen der Versandanfrage verwendet.

   Sie haben zwei Möglichkeiten, den REST-Endpunkt anzugeben:

   +++URL

   Mit dieser Option können Sie den Ziel-REST-Endpunkt direkt eingeben.
Geben Sie eine URL an, um Daten an einen externen Server zu senden. Das Format der URL ist `https://host:port/path_to_rest_end_point`. Stellen Sie sicher, dass Sie den Pfad zum Handhaben der POST-Anforderung anonym konfigurieren.

   ![Zuordnung zur Weitergabe von Feldwerten als Anforderungsparameter für die Dankeseite](assets/post-enabled-actionconfig.png)

   Im obigen Beispiel hat der Benutzer Informationen in die `textbox` eingegeben, die mithilfe von Parameter `param1` erfasst werden. Die Syntax zur Veröffentlichung erfasster Daten mithilfe von `param1` lautet:

   `String data=request.getParameter("param1");`

   Auch Parameter, die Sie für die Veröffentlichung von XML-Daten und Anlagen verwenden, sind `dataXml` und `attachments`.

   Beispielsweise können Sie diese beiden Parameter in Ihrem Skript verwenden, um Daten an einem REST-Endpunkt zu analysieren. Verwenden Sie die folgende Syntax, um Daten zu speichern und zu analysieren:

   `String data=request.getParameter("dataXml");`
   `String att=request.getParameter("attachments");`

   In diesem Beispiel speichert `data` die XML-Daten, und `att` speichert Anlagendaten.

   Die Übermittlungsoption **[!UICONTROL An REST-Endpunkt übermitteln]** übermittelt die im Formular eingetragenen Daten zu einer konfigurierten Bestätigungsseite im Rahmen der HTTP-GET-Anfrage. Sie können den Namen der anzufordernden Felder hinzufügen. Das Format der Anfrage lautet:

   `{fieldName}={request parameter name}`

   Wie in der folgenden Abbildung dargestellt, werden `param1` und `param2` als Parameter mit Werten, die aus den Feldern **textbox** und **numericbox** kopiert wurden, für die nächste Aktion weitergeleitet.

   ![Konfigurieren der Übermittlungsaktion „An REST-Endpunkt übermitteln“](/help/forms/assets/submit-to-rest-endpoint-ue.png)

   Sie können auch **[!UICONTROL POST-Anforderungen aktivieren]** und eine URL eingeben, um die Anforderung zu veröffentlichen. Um Daten an den AEM-Server, auf dem sich das Formular befindet, zu senden, verwenden Sie einen relativen Pfad entsprechend dem Stammpfad des AEM-Servers. Beispiel: `/content/forms/af/SampleForm.html`. Wenn Sie Daten an irgendeinen anderen Server senden, verwenden Sie den absoluten Pfad.

   +++

   +++Konfiguration

   Mit dieser Option können Sie eine vordefinierte HTTP-Konfiguration hinzufügen, die über den Konfigurations-Browser von AEM verwaltet wird. Sie können die Konfiguration auswählen, die Sie für den Authentifizierungstyp Ihres Dienst-REST-Endpunkts und die Inhaltstypen erstellt haben. Weitere Informationen zum Authentifizierungstyp und zu den Inhaltstypen finden Sie unter [Konfigurieren von Datenquellen](/help/forms/configure-data-sources.md#configure-restful-services-using-service-endpoint-configure-restful-services-service-endpoint).

   +++

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

>[!ENDTABS]

<!-- ### Configure submit action based on Service Rest Endpoint {#config-service-endpoint-auth}



1. Open the Content browser, and select the **[!UICONTROL Guide Container]** component of your Adaptive Form.
2. Click the Guide Container properties ![Guide properties](/help/forms/assets/configure-icon.svg) icon. The Adaptive Form Container dialog box opens. 
3. Click the  **[!UICONTROL Submission]** tab. 
4. From the **[!UICONTROL Submit Action]** drop-down list, select **[!UICONTROL Submit to Rest endpoint]**.
5. Enable the POST request.
6. Specify the REST endpoint URL.
7. Select the Configuration you have created for your Service Rest Endpoint Authentication Type and the Content Types. To know more about Authentication Type and the Content Types, visit [configure data sources](/help/forms/configure-data-sources.md#configure-restful-services-using-service-endpoint-configure-restful-services-service-endpoint).
    ![Configuring Rest Endpoint](assets/rest-service-endpoint-config.png)
8. Click Done. -->



## Best Practices

* Stellen Sie beim Senden von Daten an einen externen Server sicher, dass die URL sicher ist, und konfigurieren Sie den Pfad, um die POST-Anforderung anonym zu verarbeiten und dadurch vertrauliche Informationen zu schützen.
* Alle Felder müssen über verschiedene Elementnamen verfügen, um als Parameter in der REST-URL weitergeleitet zu werden, und zwar auch dann, wenn die Felder in verschiedene Bereiche platziert wurden.

## Verwandte Artikel

{{af-submit-action}}
