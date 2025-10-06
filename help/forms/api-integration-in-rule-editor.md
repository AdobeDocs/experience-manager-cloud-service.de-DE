---
title: Integrieren der API im Regeleditor für Forms
description: Erfahren Sie mehr über die neuesten Verbesserungen beim Aufrufen des Service im Regeleditor, einschließlich der Integration von APIs für adaptive Forms auf der Grundlage von Kernkomponenten ohne Verwendung eines Formulardatenmodells.
feature: Adaptive Forms, Core Components, Edge Delivery Services
role: User, Developer
level: Beginner, Intermediate
keywords: Integrieren der API im Regeleditor, Aufrufen von Service-Verbesserungen
exl-id: fc51f86d-e672-4513-b473-6700757a0c3d
source-git-commit: 962e31769c013c87bd3089b20601c258fec22baa
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 2%

---

# Integrieren der API im Regeleditor

<span>Die Integration der API im Regeleditor erfolgt im Rahmen des Early-Adopter-Programms. Sie können von Ihrer offiziellen E-Mail-ID an `aem-forms-ea@adobe.com` schreiben, um dem Early-Adopter-Programm beizutreten und Zugriff auf die Funktion anzufordern.</span>

>[!NOTE]
>
> Der Visual Rule Editor unterstützt die API-Integration in adaptiven Forms auf der Grundlage von Kernkomponenten und Edge Delivery Services Forms.

Der Visual Rule Editor in Adaptive Forms unterstützt die direkte API-Integration ohne Erstellen eines Formulardatenmodells. Sie können eine Verbindung zu einem API-Endpunkt herstellen, indem Sie entweder die API-URL (im JSON-Format) eingeben oder die Konfiguration über einen cURL-Befehl importieren. Nach der Integration kann **Aktion „Service**&quot; verwendet werden, um die API aufzurufen.

Formularfelder können direkt den Eingabeparametern zugeordnet werden, die in der API-Konfiguration definiert sind. Ebenso können Ausgabeparameter mithilfe der Option **Ereignis-Payload“ für die entsprechende API-Antwort Formularfeldern** werden.

Darüber hinaus können Sie mit dem visuellen Regeleditor beim Aufrufen **Services** Erfolgs **und** Fehlerhandler“ definieren. Erfolgs-Handler geben die Aktionen an, die nach einem erfolgreichen API-Aufruf ausgeführt werden sollen, während Fehler-Handler definieren, wie das Formular auf einen Fehler reagieren soll.

>[!NOTE]
>
> Die API-Integration im Regeleditor gilt auch für im universellen Editor erstellte [Edge Delivery Services Forms](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md).

## Vergleich: API-Integrationsmethoden

| Aspekt | API-Integration mit dem Formulardatenmodell (FDM) | Direkte API-Integration (über *API-Integration erstellen*) |
|--------------------------------|---------------------------------------------------------------------|-----------------------------------------------------------|
| **Zweck** | Zentralisierte, wiederverwendbare API-Integration über mehrere Formulare hinweg | Schnelle, formularspezifische API-Integration |
| **Setup-Speicherort** | Im Formulardatenmodell-Editor (AEM-Konsole) erstellt und bearbeitet | Direkt im Regeleditor für adaptive Formulare erstellt und bearbeitet |
| **Komplexität** | Höherer Setup-Aufwand (Zuordnung und Konfiguration erforderlich) | Einfach und leicht |
| **Am besten geeignet für** | Anwendungsfälle für Unternehmen oder großen Umfang mit mehreren Formularen | Kleine Formulare, Prototypen oder einmalige API-Aufrufe |

## Konfiguration der API-Integration

Im folgenden Screenshot sehen Sie das Konfigurationsfenster für die API-Integration:

![API-Integrationskonfiguration](/help/forms/assets/api-integration-configuration.png)

### Wichtige Konfigurationsoptionen

**API-Integrationskonfiguration**

* **Import aus cURL**: Konfigurieren Sie Ihre API-Integration, indem Sie einen vorgefertigten cURL-Befehl einfügen, anstatt Details wie API-URL, HTTP-Methode, Kopfzeilen und Parameter manuell einzugeben.
* **Anzeigename**: Benutzerdefinierter Name für den API-Service.
* **API URL**: Endpunkt des API-Services.
* **HTTP-Methode auswählen**: Die HTTP-Anfragemethode, die zum Aufrufen der API verwendet wird.
* **Content-**: Definiert das Anfrage- und Antwortformat.
* **Verschlüsselung erforderlich**: (Optional) Stellt sicher, dass vertrauliche Daten während der Übertragung verschlüsselt werden.
* **Auf Client ausführen**: Wenn diese Option aktiviert ist, erfolgt der API-Aufruf vom Client (Browser) anstelle vom Server.

**Authentifizierungstyp**

* **Optionen**: Keine, Standard, API-Schlüssel, OAuth 2.0.

**Eingabeparameter**

* **JSON für Eingabe hochladen**: Laden Sie eine JSON-Beispieldatei hoch, um Eingabezuordnungen automatisch auszufüllen.
   * **Name**: Name des Eingabeparameters, der für die API erforderlich ist.
   * **Type**: Datentyp der Eingabe (Zeichenfolge, Zahl, Boolesch usw.).
   * **In**: Speicherort des Parameters (Abfrage, Kopfzeile oder Hauptteil).
   * **Standardwert**: Vorausgefüllter Wert, wenn er nicht vom Benutzer angegeben wird.
   * **Hinzufügen**: Option zum Hinzufügen zusätzlicher Eingabeparameter.

**Ausgabeparameter**

* **JSON für Ausgabe hochladen**: Laden Sie eine Beispiel-API-Antwort hoch, um Zuordnungen automatisch zu generieren.
   * **Name**: Name des Ausgabeparameters aus der API-Antwort.
   * **Type**: Erwarteter Datentyp des Ausgabeparameters (Zeichenfolge, Zahl usw.).
   * **In**: Definiert, wo der zugeordnete Wert erwartet wird.
   * **Hinzufügen/Löschen**: Hinzufügen neuer Zuordnungen oder Entfernen vorhandener Zuordnungen.

## Anwendungsfall: Ausfüllen von Länderfeldern in einem Visumantragsformular

>[!VIDEO](https://video.tv.adobe.com/v/3471606/rule-editor-api-integration/?quality=12&learn=on)

**Szenario**: Eine Regierungsbehörde stellt ein Online-Antragsformular für ein Visum mit den folgenden Feldern bereit:

1. Vollständiger Name (Text)
2. Geburtsdatum (Datum)
3. Land der Staatsbürgerschaft (Dropdown)
4. Passnummer (Text)
5. Ausstellungsland des Passes (Dropdown)
6. Zielland (Dropdown)
7. Vorgesehenes Anreisedatum (Datum)

Anstatt eine statische Liste von Ländern zu verwalten, ruft das Formular Länderinformationen (Kontinent, Hauptstadt, ISO-Alpha-Codes usw.) mithilfe der **getCountryName-API**:

`https://secure.geonames.org/countryInfoJSON?username=aemforms`

Dadurch wird sichergestellt, dass Antragsteller beim Ausfüllen des Formulars stets eine aktuelle und genaue Liste der Länder erhalten.

### Implementierung mithilfe der API-Integration im Regeleditor

Sie können eine API integrieren, ohne ein Formulardatenmodell zu erstellen, indem Sie im Regeleditor auf **API-Integration erstellen** klicken.

![API-Integration erstellen](/help/forms/assets/create-api-integration.png)

Ein API-Service mit dem **getCountryName** wird unter **API-Integrationskonfiguration** im Regeleditor konfiguriert:

![API-REST-Endpunktkonfiguration](/help/forms/assets/api-restendpoint.png)

* **API-Endpunkt-URL** → `https://secure.geonames.org/countryInfoJSON?username=aemforms`
* **HTTP-Methode** → GET
* **Content-Typ** → JSON
* **Eingabe** → `username` als Abfrageparameter (`aemforms`) übergeben.
* **Ausgabe** → Antwortfelder wie `continent`, `capital`, `countrynames`, `isoAlpha3` und `languages` werden Formularfeldern zugeordnet.

Im **Visumantragsformular** sind die drei Dropdown-Felder **Land der**, **Land der Passausstellung** und **Zielland** an die Aktion **Dienst aufrufen** gebunden.

Beim Laden des Formulars ruft **Dienst aufrufen** die Liste der Länder aus der API ab. Die Antwort wird dann zugeordnet, um die Dropdown-Optionen automatisch auszufüllen.

Wenn der/die Benutzende beispielsweise **Land der Staatsangehörigkeit** öffnet, wird die Liste der Länder dynamisch aus der API-Antwort angezeigt.

![invoke-service-api-integration](/help/forms/assets/invoke-service-api-integration.png)

![API-Integrationsausgabe](/help/forms/assets/api-integration-output.png)

Ebenso verwenden **Land der Passausstellung** und **Zielland** denselben API-Aufruf, um konsistente und aktuelle Daten in allen drei Feldern sicherzustellen.

## Implementieren des Wiederholungsmechanismus bei API-Fehlern

Wenn eine API-Anfrage fehlschlägt, ist es oft nützlich, die Anfrage erneut auszuführen, bevor dem Benutzer ein Fehler gemeldet wird. Sie können einen Abruf- und Wiederholungsmechanismus implementieren, indem Sie benutzerdefinierten Code in die Datei **function.js** schreiben.

Das folgende Beispiel zeigt, wie API-Fehler mit bis zu zwei Wiederholungsversuchen und einem exponentiellen Backoff zwischen Wiederholungsversuchen gehandhabt werden:

```javascript
/**
 * Handles request retries with up to 2 retry attempts
 * @param {function} requestFn - The request function to execute
 * @return {Promise} A promise that resolves with the response or rejects after all retries
 */
function retryHandler(requestFn) {
    const MAX_RETRIES = 2;
    
    /**
     * Attempts the request with retry metadata
     * @param {number} retryCount - Current retry attempt count
     * @return {Promise} The request promise
     */
    function attemptRequest(retryCount = 0) {
        // Include retry metadata if this is a retry
        const requestOptions = retryCount > 0 ? {
            headers: {
                'X-Retry': 'true',
                'X-Retry-Count': retryCount.toString(),
                'X-Retry-Time': new Date().toISOString()
            },
            body: {
                retry: true,
                retryCount: retryCount,
                timestamp: Date.now()
            }
        } : undefined;

        return requestFn(requestOptions)
            .then(function(response) {
                if (response && response.status >= 400) {
                    console.warn('Request failed with status ' + response.status);
                    throw new Error('Request failed with status ' + response.status);
                }
                return response;
            })
            .catch(function(error) {
                console.warn('Request attempt ' + (retryCount + 1) + ' failed:', error.message);
                
                // Retry if max attempts not reached
                if (retryCount < MAX_RETRIES) {
                    console.log('Retrying request, attempt ' + (retryCount + 2) + ' of ' + (MAX_RETRIES + 1));
                    
                    // Exponential backoff delay: 1s, 2s, 4s...
                    const delay = Math.pow(2, retryCount) * 1000;
                    
                    return new Promise(function(resolve) {
                        setTimeout(resolve, delay);
                    }).then(function() {
                        return attemptRequest(retryCount + 1);
                    });
                } else {
                    // All retries exhausted
                    console.error('All retry attempts failed. Final error:', error.message);
                    throw new Error('Request failed after ' + (MAX_RETRIES + 1) + ' attempts: ' + error.message);
                }
            });
    }
    
    // Start the first attempt
    return attemptRequest(0);
}
```

Im obigen Code verwaltet die Funktion **retryHandler** API-Anfragen mit automatischen Wiederholungsversuchen im Falle eines Fehlers. Es dauert eine Anfragefunktion (requestFn) und versucht die Anfrage bis zu zweimal, wobei für jeden erneuten Versuch Metadaten hinzugefügt werden.

>[!NOTE]
>
> Ausführliche Anweisungen zum Hinzufügen benutzerdefinierter Funktionen finden Sie im Artikel [Einführung in benutzerdefinierte Funktionen für adaptive Forms auf der Grundlage &#x200B;](/help/forms/create-and-use-custom-functions.md) Kernkomponenten“.

## Häufig gestellte Fragen

* **Muss ich ein Formulardatenmodell erstellen, um eine API in adaptive Forms zu integrieren?**\
  Nein. Mit dem visuellen Regeleditor können Sie APIs direkt mit der Option **API-Integration erstellen** integrieren, ohne ein Formulardatenmodell zu erstellen. Dieser Ansatz eignet sich am besten für einfache oder formularspezifische Anwendungsfälle.

* **Kann ich API-Aufrufe über den Regeleditor sichern?**\
  Ja. Die API-Integrationskonfiguration bietet Authentifizierungsoptionen wie **Standard, API-Schlüssel und OAuth 2.0**. Sie können auch **Verschlüsselung erforderlich** aktivieren, um sicherzustellen, dass vertrauliche Daten sicher übertragen werden.
