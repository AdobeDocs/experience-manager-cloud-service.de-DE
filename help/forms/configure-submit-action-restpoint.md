---
Title: How to configure submit to Rest Endpoint submit action for an Adaptive Form?
Description: Discover the steps to set up Rest Endpoint when submitting an Adaptive Form.
keywords: AEM Forms REST Endpoint, An REST-Endpunkt übermitteln, Daten an REST-URL posten, REST-Endpoint-Aktion konfigurieren
feature: Adaptive Forms, Core Components
source-git-commit: 8784c0bcd05eeae41a472faa5ecad03cbdd8a9b6
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 62%

---


# Konfigurieren einer Sendeaktion &quot;Adaptives Formular für REST-Endpunkt&quot;

Verwenden Sie die **[!UICONTROL An REST-Endpunkt übermitteln]** Aktion zum Posten der gesendeten Daten an eine REST-URL. Die URL kann sich auf einem internen (dem Server, auf dem das Formular gerendert wird) oder auf einem externen Server befinden.

AEM as a Cloud Service bietet verschiedene vordefinierte Übermittlungsaktionen für die Verarbeitung von Formularübermittlungen. Weitere Informationen zu diesen Optionen finden Sie im Abschnitt [Übermittlungsaktion für adaptive Formulare](/help/forms/configure-submit-actions-core-components.md)  Artikel.

## Vorteile

Einige Vorteile der Konfiguration der **[!UICONTROL An REST-Endpunkt übermitteln]** Übermittlungsaktion für Adaptive Forms sind:

* Sie ermöglicht die nahtlose Integration von Formulardaten in externe Systeme und Dienste über RESTful-APIs.
* Es bietet Flexibilität bei der Verarbeitung von Datenübermittlungen aus Adaptive Forms und unterstützt dynamische und komplexe Datenstrukturen.
* Es unterstützt die dynamische Zuordnung von Formularfeldern zu Parametern in der REST-Endpunkt-URL, sodass anpassbare und anpassbare Datenübermittlungen möglich sind.


## Konfigurieren der Sendeaktion &quot;An REST-Endpunkt übermitteln&quot; {#steps-to-configure-submit-to-restendpoint-submit-action}

So konfigurieren Sie die Sendeaktion:

1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Übermittlung]**.
1. Aus dem **[!UICONTROL Übermittlungsaktion]** Dropdown-Liste auswählen **[!UICONTROL An REST-Endpunkt übermitteln]**.
   ![Aktionskonfiguration für &quot;An REST-Endpunkt übermitteln&quot;](/help/forms/assets/submit-action-restendpoint.png)

   Um Daten auf einem internen Server zu senden, geben Sie den Pfad der Ressource an. Die Daten werden an den Pfad der Ressource gesendet. Beispiel: `/content/restEndPoint`. Für solche Sende-Anfragen werden die Authentifizierungsinformationen der Versandanfrage verwendet.

   Geben Sie eine URL an, um Daten an einen externen Server zu senden. Das Format der URL ist `https://host:port/path_to_rest_end_point`. Stellen Sie sicher, dass Sie den Pfad zum Handhaben der POST-Anforderung anonym konfigurieren.

   ![Zuordnung zur Weitergabe von Feldwerten als Anforderungsparameter für die Dankeseite](assets/post-enabled-actionconfig.png)

   Im obigen Beispiel hat der Benutzer Informationen in die `textbox` eingegeben, die mithilfe von Parameter `param1` erfasst werden. Die Syntax zur Veröffentlichung erfasster Daten mithilfe von `param1` lautet:

   `String data=request.getParameter("param1");`

   Auch Parameter, die Sie für die Veröffentlichung von XML-Daten und Anlagen verwenden, sind `dataXml` und `attachments`.

   Beispielsweise können Sie diese beiden Parameter in Ihrem Skript verwenden, um Daten an einem REST-Endpunkt zu analysieren. Verwenden Sie die folgende Syntax, um Daten zu speichern und zu analysieren:

   `String data=request.getParameter("dataXml");`
   `String att=request.getParameter("attachments");`

   In diesem Beispiel speichert `data` die XML-Daten, und `att` speichert Anlagendaten.

   Die Übermittlungsoption **[!UICONTROL An REST-Endpunkt übermitteln]** wird verwendet, wenn Sie die im Formular eingetragenen Daten zu einer konfigurierten Bestätigungsseite im Rahmen der HTTP GET-Anforderung weiterleiten möchten. Sie können den Namen des anzufragenden Felds hinzufügen. Das Format der Anfrage lautet:

   `{fieldName}={request parameter name}`

   Wie in der folgenden Abbildung dargestellt, werden `param1` und `param2` als Parameter mit Werten, die aus den Feldern **textbox** und **numericbox** kopiert wurden, für die nächste Aktion weitergeleitet.

   ![Konfigurieren der Übermittlungsaktion „An REST-Endpunkt übermitteln“](assets/action-config.png)

   Sie können auch **[!UICONTROL POST-Anforderungen aktivieren]** und eine URL eingeben, um die Anforderung zu veröffentlichen. Um Daten an den AEM-Server, auf dem sich das Formular befindet, zu senden, verwenden Sie einen relativen Pfad entsprechend dem Stammpfad des AEM-Servers. Beispiel: `/content/forms/af/SampleForm.html`. Wenn Sie Daten an irgendeinen anderen Server senden, verwenden Sie den absoluten Pfad.

1. Klicken Sie auf **[!UICONTROL Fertig]**.

## Best Practices

* Stellen Sie beim Senden von Daten an einen externen Server sicher, dass die URL sicher ist, und konfigurieren Sie den Pfad, um die POST-Anforderung anonym zu verarbeiten, um vertrauliche Informationen zu schützen.
* Alle Felder müssen über verschiedene Elementnamen verfügen, um als Parameter in der REST-URL weitergeleitet zu werden, auch dann, wenn die Felder in verschiedenen Bereichen platziert sind.

## Ähnliche Artikel

{{af-submit-action}}

