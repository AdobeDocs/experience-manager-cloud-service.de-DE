---
title: Aufzeichnen einer Transaktion für benutzerdefinierte Implementierungen
description: Verwenden der TransactionRecorder-API, um Aktionen aufzuzeichnen, die nicht automatisch als Transaktionen gezählt werden
feature: Adaptive Forms, Foundation Components
exl-id: cb584f78-30af-4a58-be99-843352e8249c
role: Admin, Developer, User
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 93%

---

# Aufzeichnen einer Transaktion für benutzerdefinierte Implementierungen {#record-a-transaction-for-custom-implementations}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/transaction-reports/transaction-reports-osgi/record-transaction-custom-implementation) |
| AEM as a Cloud Service | Dieser Artikel |

Verwenden der TransactionRecorder-API, um Aktionen aufzuzeichnen, die nicht automatisch als Transaktionen gezählt werden.

Sie können benutzerdefinierten Code verwenden, um ein PDF-Formular zu senden. Oder Sie senden ein Formular mit benutzerdefinierten Methoden ab, anstatt die mit AEM Forms bereitgestellten Übermittlungsmethoden zu verwenden. Alle oben genannten Aktionen und benutzerdefinierten Implementierungen von AEM Forms-APIs werden nicht als Transaktionen gezählt. AEM Forms stellt eine API namens [TransactionRecorder](https://javadoc.io/doc/com.adobe.aem/aem-forms-sdk-api/latest/com/adobe/aem/transaction/core/ITransactionRecorder.html) bereit, um Aktionen wie etwa Transaktionen aufzuzeichnen.

Um eine Transaktion aufzuzeichnen, schreiben Sie das [Standard-Sling-Servlet](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/store-and-retrieve-af-with-2fa/create-servlet.html?lang=de) und rufen das Servlet von einem Client aus auf, um eine Transaktion aufzuzeichnen. Sie können das Servlet mithilfe von AJAX oder einer anderen Standardmethode aufrufen.

## Beispiel für Server-seitigen Code {#sample-server-sided-code}

Sie können den folgenden Beispiel-Code verwenden, um die TransactionRecorder-API von einer Java™-Klasse aus mithilfe eines benutzerdefinierten OSGi-Bundles auszuführen.

```java
import com.adobe.aem.transaction.core.ITransactionRecorder;
import com.adobe.aem.transaction.core.model.TransactionRecord;
import com.adobe.aem.transaction.core.exception.TransactionException;
import com.adobe.aem.transaction.core.FormsTransactionConstants;

@Reference
private ITransactionRecorder transactionRecorder;

doPost (SlingHttpServletRequest request, SlingHttpServletResponse response) {
    transactionRecorder.startContext();
    TransactionRecord txRecord = extractTxRecordFromRequest(request); //extract transaction relevant data from request
    try {
        bool success = doBillableWork();
        if (success) {
            transactionRecorder.recordTransaction(txRecord);
        }
    } catch (Exception e) {
        //exception handling
    } finally {
        transactionRecorder.endContext();
    }
}

//Here, it is assumed that txInfo is passed in Stringified json form in the ajax call (in data parameter). You can pass txInfo from client in any way that you find suitable.
private TransactionRecord extractTxRecordFromRequest(SlingHttpServletRequest request) {
    BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(request.getInputStream()));
    Map<String, Object> txDataMap = new HashMap<String, Object>();
    String txData = bufferedReader.readLine();
    JSONObject txInfo= new JSONObject(txData );
    try {
        String resourceType= txInfo.getString("resourceType");
        String transactionType = txInfo.getString("transactionType");
        Integer transactionCount = (Integer)txInfo.get("transactionCount");
        //Extract all the relevant tx record attributes similarly and pass them in Transaction Record constructor as per the java doc}
        return new TransactionRecord(transactionCount, transactionType, resourceType, ..);
    } catch (JSONException e) {
        //exception handling
    } finally {
        bufferedReader.close();
    }
}
```

## Beispiel für Client-seitigen Code {#sample-client-side-code}

Sie können den folgenden Beispiel-Code verwenden, um das Servlet aufzurufen, das die `TransactionRecorder`-API hat.

```javascript
$.ajax({
   type: 'POST',
   url: url, //servlet url
   contentType: 'application/json; UTF-8',
   data: JSON.stringify({transactionCount : 1,
                        transactionType: "SUBMIT",
                        resourceType: "FORM",
                        resourceSubType: "ADAPTIVE-FORM"}),
   success: successHandler,
   error: faultHandler
})
```

## Ähnliche Artikel {#related-articles}

* [Abrechenbare APIs für Transaktionsberichte](/help/forms/transaction-reports-billable-apis.md)
