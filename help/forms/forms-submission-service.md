---
Title: How to use forms submission service for submitting forms?
Description: Learn how to use forms submission service for submitting forms.
Keywords: Use form submission service, Submit form using form submission service
feature: Edge Delivery Services
Role: User, Developer
hide: true
hidefromtoc: true
exl-id: 12b4edba-b7a1-4432-a299-2f59b703d583
source-git-commit: 37b20a97942f381b46ce36a6a3f72ac019bba5b7
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 9%

---

# Forms Submission Service mit Edge Delivery Services Forms

<span class="preview"> Diese Funktion ist über das Early-Access-Programm verfügbar. Um den Zugriff anzufordern, senden Sie eine E-Mail mit dem Namen Ihrer GitHub-Organisation und dem Namen des Repositorys von Ihrer offiziellen Adresse an <a href="mailto:aem-forms-ea@adobe.com">aem-forms-ea@adobe.com</a>. Wenn die Repository-URL beispielsweise https://github.com/adobe/abc lautet, lautet der Name der Organisation „adobe“ und der Name des Repositorys „abc“.</span>

Mit dem Forms-Übermittlungs-Service können Sie Daten aus den Formularübermittlungen in jeder Tabelle speichern, z. B. in OneDrive, SharePoint oder Google Sheets, sodass Sie einfach auf Formulardaten in Ihrer bevorzugten Tabellenplattform zugreifen und diese verwalten können.

![Forms-Sendedienst](/help/forms/assets/form-submission-service.png)

## Vorteile der Verwendung des Forms Submission Service

Einige Vorteile der Verwendung des Forms-Übermittlungs-Service mit Tabellen sind:

* **Direkte Integration**: Sie können Formulare so konfigurieren, dass Daten direkt an ein bestimmtes Arbeitsblatt gesendet werden, sodass keine manuelle Datenübertragung mehr erforderlich ist.
* **Datenstruktur**: Beim Einrichten der Übermittlung können Sie Formularfelder entsprechenden Tabellenspalten zur organisierten Datenspeicherung zuordnen.
* **Zugriffssteuerung**: Sie können bestehende Berechtigungen nutzen, um zu steuern, wer je nach ausgewähltem Tabellen-Service auf gesendete Formulardaten zugreifen und diese ändern kann.

## Voraussetzungen

Im Folgenden finden Sie die Voraussetzungen für die Verwendung des Forms-Übermittlungsdienstes:

* Stellen Sie sicher, dass Ihr AEM-Projekt über den neuesten adaptiven Formularblock verfügt.
* Stellen Sie sicher, dass Ihr Git-Repository zur -Zulassungsliste hinzugefügt wird, um den Forms-Übermittlungs-Service zu verwenden. Bitte [mailto:aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) mit Ihrem GitHub-Organisationsnamen und Repository-Namen angeben, damit diese zur Zulassungsliste hinzugefügt werden, um den Forms Submission Service zu verwenden.

## Konfigurieren des Forms-Sendedienstes

Erstellen Sie ein neues AEM-Projekt, das mit dem adaptiven Forms-Block konfiguriert ist. Weitere Informationen zum Erstellen [ neuen AEM-Projekts finden Sie ](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/tutorial) Artikel Erste Schritte - Entwickler-Tutorial . Aktualisieren Sie die `fstab.yaml` in Ihrem Projekt. Ersetzen Sie den vorhandenen Verweis durch den Pfad zu dem Ordner, den Sie für die `forms@adobe.com` freigegeben haben.

Sie können [den Forms-Übermittlungsdienst manuell konfigurieren](#configuring-the-forms-submission-service-manually) oder [den Forms-Übermittlungsdienst mithilfe der API konfigurieren](#configuring-the-forms-submission-service-using-api).

### Manuelles Konfigurieren des Forms-Übermittlungsdienstes

![Workflow für den Formularübermittlungs-Service](/help/forms/assets/forms-submission-service-workflow.png)

#### &#x200B;1. Erstellen eines Formulars mit einer Formulardefinition

Erstellen Sie ein Formular mit Google Sheets oder Microsoft Excel. Um zu erfahren, wie Sie ein Formular mithilfe einer Formulardefinition in Microsoft Excel oder Google Sheets erstellen, klicken [ hier](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/create-forms).

Im folgenden Screenshot wird die Formulardefinition angezeigt, die zum Erstellen eines Formulars verwendet wird:

![Formulardefinition](/help/forms/assets/form-submission-definition.png)

>[!IMPORTANT]
>
>**Das Blatt, in dem das Formular erstellt wird, unterliegt Einschränkungen in Bezug auf seinen Namen. Nur `helix-default` und `shared-aem` können als Blattnamen verwendet werden.**

#### &#x200B;2. Aktivieren Sie das Arbeitsblatt, um Daten zu akzeptieren.

Nachdem Sie das Formular erstellt und in der Vorschau angezeigt haben, aktivieren Sie die entsprechende Tabelle, um mit dem Empfang von Daten zu beginnen. Fügen Sie wie `incoming` ein neues Blatt hinzu. Sie können [manuell aktivieren, damit die Tabelle Daten akzeptiert](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/submit-forms#manually-enable-the-spreadsheet-to-accept-data).

![Eingehendes Blatt](/help/forms/assets/form-submission-incoming-sheet.png)

>[!WARNING]
>
> Wenn das `incoming` nicht vorhanden ist, sendet AEM keine Daten an diese Arbeitsmappe.

#### &#x200B;3. Freigeben des Arbeitsblatts und Erstellen eines Links.

Führen Sie die folgenden Schritte aus, um das Arbeitsblatt für das `forms@adobe.com`-Konto freizugeben und einen Link zu generieren:

1. Klicken Sie in Excel oder Google Sheets auf die **Freigeben**-Schaltfläche oben rechts.
1. Fügen Sie das `forms@adobe.com` hinzu und
Klicken Sie auf das Augensymbol, wählen Sie **Bearbeiten** aus und klicken Sie auf **Senden**.

   ![Freigeben eingehender Arbeitsblätter](/help/forms/assets/form-submission-share-incoming.png)

1. Um den Tabellenlink zu kopieren, klicken Sie auf die Schaltfläche **Freigeben** in der oberen rechten Ecke und wählen Sie **Link kopieren**.

   ![Link des eingehenden Blatts kopieren](/help/forms/assets/form-submission-copy-link.png)

#### &#x200B;4. Verknüpfen des Arbeitsblatts in der Formulardefinition

Führen Sie die folgenden Schritte aus, um den Forms Submission Service mit den Google Sheets oder Microsoft Excel zu konfigurieren:

1. Öffnen Sie das Arbeitsblatt, das die Formulardefinition enthält.
1. Fügen Sie in der Zeile, die dem Feld **Senden** entspricht, den kopierten Tabellenlink in die Spalte **Aktion** ein.

   ![Verknüpfen einer Tabelle](/help/forms/assets/form-submission-sheet-linking.png)

1. Zeigen Sie eine Vorschau an und veröffentlichen Sie die Tabelle mit dem [AEM Sidekick](https://www.aem.live/docs/sidekick) mit aktualisiertem Formularübermittlungs-Service.

>[!NOTE]
>
> Sie können auf das [Arbeitsblatt) verweisen](/help/forms/assets/spreadsheet.xlsx) um den Forms-Übermittlungs-Service zu verwenden.

### Konfigurieren des Forms-Übermittlungsdienstes mithilfe der API

Sie können auch eine **POST**-Anfrage an das Formular senden, um das `incoming` mit Daten zu aktualisieren.

>[!NOTE]
>
> * Wenn das `incoming` nicht vorhanden ist, sendet AEM keine Daten an diese Arbeitsmappe.
> * Geben Sie das `incoming` für die Adobe Experience Manager-`forms@adobe.com` frei und gewähren Sie Bearbeitungszugriff.
> * Anzeigen einer Vorschau und Veröffentlichen des `incoming` im Sidekick.

Informationen zum Formatieren der POST-Anfrage zur Einrichtung Ihres Blatts finden Sie in der [API-Dokumentation](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/references/aem-forms-submission-service/). Sie können sich das folgende Beispiel ansehen:

Sie können Tools wie curl oder Postman verwenden, um diese POST-Anfrage auszuführen, wie unten gezeigt.

* **Verwenden von Postman**:

Senden Sie beispielsweise nach dem Ersetzen die folgende Anfrage in Postman:
* `{id}` mit Ihrer Formular-ID
* `site or repository` mit Ihrem GitHub-Repository oder Site-Namen
* `organization` mit Ihrem GitHub-Benutzernamen

  ```json
  POST 'https://forms.adobe.com/adobe/forms/af/submit/{id}' \
  --header 'Content-Type: application/json' \
  --header 'x-adobe-routing: tier=live,bucket=main--[site/repository]--[organization]' \
  --data '{
      "data": {
          "startDate": "2025-01-10",
          "endDate": "2025-01-25",
          "destination": "Australia",
          "class": "First Class",
          "budget": "2000",
          "amount": "1000000",
          "name": "Mary",
          "age": "35",
          "subscribe": null,
          "email": "mary@gmail.com"
              }
          }'
  ```

Postman Wenn Sie in **auf die Schaltfläche** Senden“ klicken, wird eine `201 Created` Antwort zurückgegeben, und das `incoming` wird mit den gesendeten Daten aktualisiert.

![Postman-Bildschirm](/help/forms/assets/postman-api.png)

* **Verwenden des curl-Befehls**:

Führen Sie beispielsweise den folgenden Befehl nach dem Ersetzen im Terminal oder in der Eingabeaufforderung aus:
* `{id}` mit Ihrer Formular-ID
* `site or repository` mit Ihrem GitHub-Repository oder Site-Namen
* `organization` mit Ihrem GitHub-Benutzernamen


>[!BEGINTABS]

>[!TAB Für macOS]

    „json
    curl -X POST &quot;https://forms.adobe.com/adobe/forms/af/submit/{id}&quot; \
    —header „Content-Type: application/json“ \
    —header „x-adobe-routing: tier=live,bucket=main—[site/repository]—[organization]&quot; \
    —data &#39;&lbrace;
    „data“: &lbrace;
    „startDate“: „2025-01-10“,
    „endDate“: „2025-01-25“,
    „destination“: „Australia“,
    „class“: „First Class“,
    „budget“: „2000“,
    „Betrag“: „1000000“,
    „Name“: „Joe“,
    „Alter“: „35“,
    „Abonnieren“: null,
    „EMail“: &quot;mary@gmail.com&quot;
    &rbrace;
    &rbrace;
    
    &quot;

>[!TAB Für Windows-Betriebssysteme]

    „json
    
    curl -X POST &quot;https://forms.adobe.com/adobe/forms/af/submit/{id}&quot; ^
    —Header „Content-Type: application/json“ ^
    —Header „x-adobe-routing: tier=live,bucket=main—[site/repository]—[organisation]&quot; ^
    —data &quot;&lbrace;\„data\&quot;: {\„startDate\&quot;: \„2025-01-10\&quot;, \„endDate\&quot;: \„2025-01-25\&quot;, \„destination\&quot;: \„Australia\&quot;, \„class\&quot; \„Erste Klasse\&quot;, \„budget\&quot;: \„2000\&quot;, \„amount\&quot;: \„1000000\&quot;, \„name\&quot;: \„Joe\&quot;, \„age\&quot;: \„35\&quot;, \„subscribe\&quot;: null, \„email\&quot;: \&quot;mary@gmail.com\&quot;}&quot;
    
    &quot;

>[!ENDTABS]

Die oben genannte POST-Anfrage aktualisiert das `incoming` mit der folgenden Antwort:

```json
    < HTTP/1.1 201 Created
    < Connection: keep-alive
    < Content-Length: 0
    < X-Request-Id: 02a53839-2340-56a5-b238-67c23ec28f9f
    < X-Message-Id: 42ecb4dd-b63a-4674-8f1a-05a4a5b0372c
    < Accept-Ranges: bytes
    < Date: Fri, 10 Jan 2025 13:06:10 GMT
    < Via: 1.1 varnish
    < Access-Control-Allow-Origin: *
    < X-Served-By: cache-del21750-DEL
    < X-Cache: MISS
    < X-Cache-Hits: 0
    < X-Timer: S1736514370.704084,VS0,VE1234
```

Im folgenden Bildschirm wird der Screenshot des `incoming`-Blatts angezeigt, das von der mit der -API gesendeten Daten aktualisiert wurde:

![Aktualisiertes Blatt](/help/forms/assets/updated-sheet.png)

## Siehe auch

{{see-more-forms-eds}}