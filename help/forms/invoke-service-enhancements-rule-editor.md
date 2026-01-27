---
title: Welche Verbesserungen gibt es beim VRE-Dienst aufrufen für Formulare, die auf Kernkomponenten basieren?
description: Verbesserungen am Aufruf-Service für den Regeleditor
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
keywords: Service-Verbesserungen in VRE aufrufen, Dropdown-Optionen mit Service aufrufen, wiederholbares Bedienfeld mit Ausgabe von Service aufrufen festlegen, Bedienfeld mit Ausgabe von Service aufrufen, Ausgabeparameter von Service aufrufen verwenden, um andere Felder zu validieren.
exl-id: 2ff64a01-acd8-42f2-aae3-baa605948cdd
source-git-commit: 5b55a280c5b445d366c7bf189b54b51e961f6ec2
workflow-type: tm+mt
source-wordcount: '1835'
ht-degree: 2%

---

# Integrieren von externen APIs mit dem visuellen Regeleditor in der Kernkomponente Forms

Der visuelle Regeleditor in einem adaptiven Formular unterstützt die Funktion **Service aufrufen**, mit der Sie über für Ihre Instanz konfigurierte Formulardatenmodelle (FDM) eine Verbindung zu externen APIs herstellen können. Sie können Formularfelder direkt den Eingabeparametern des Service zuordnen und die Payload-Option „Ereignis“ verwenden, um die Ausgabeparameter zuzuordnen. Mit dem visuellen Regeleditor können Sie auch Regeln für Erfolgs- und Fehlerhandler definieren, die auf der Antwort des Diensts basieren: Erfolgs-Handler verarbeiten erfolgreiche API-Aufrufe, während Fehler-Handler Fehler verwalten.

Auf diese Weise können Sie API-Anfragen aus Ihrem Formular einfach senden, die API-Antworten verarbeiten und die zurückgegebenen Daten dynamisch im Formular anzeigen oder verwenden. Dadurch wird eine nahtlose Integration zwischen Ihrem adaptiven Formular und externen Systemen oder Datenquellen sichergestellt.


## Vorteile der Verwendung des Service „Invoke“ im Regeleditor des Formulars

Die Verwendung des Vorgangs „Service aufrufen“ im Regeleditor eines adaptiven Formulars bietet folgende Vorteile:

* **Optimierte API-Integration**: Der Visual Rule Editor vereinfacht die Integration externer Services oder APIs in Ihren adaptiven Forms. Durch die Verwendung von **Dienst aufrufen** können Sie Formulare einfach mit verschiedenen Datenquellen und Diensten verbinden, ohne dass eine komplexe Codierung erforderlich ist, was die Formularintegration effizienter macht.

* **Dynamische Antwortverarbeitung**: Sie können Erfolgs- und Fehlerantworten basierend auf den Ausgabeantworten des **Service aufrufen** verwalten, sodass Formulare dynamisch auf verschiedene Szenarien reagieren können. Dadurch wird sichergestellt, dass Formulare verschiedene Bedingungen ordnungsgemäß verarbeiten, was die Flexibilität und Kontrolle verbessert.

* **Verbesserte Benutzerinteraktion**: Die Verwendung von **Service aufrufen** im Regeleditor ermöglicht die Echtzeit-Validierung innerhalb Ihrer Formulare und bietet ein besseres Benutzererlebnis. Außerdem wird sichergestellt, dass die Daten Server-seitig genau validiert werden, was Fehler reduziert und die Zuverlässigkeit der Formulare verbessert.

## Aufrufen von Service-Handlern für Erfolgs- und Fehlerantworten

>[!NOTE]
>
> Sie können die Handler **Dienst aufrufen** Erfolg und Fehler nur für Formulare verwenden, die auf Kernkomponenten basieren. Auf Foundation-Komponenten basierende Forms unterstützen keine **Service aufrufen** Erfolgs- und Fehlerhandler.

Mit dem visuellen Regeleditor können Sie basierend auf den Ausgabeantworten Regeln für Erfolgs **und Fehlerhandler für Vorgänge** Dienst aufrufen“ erstellen. Die folgende Abbildung zeigt den **Service aufrufen** im visuellen Regeleditor für ein adaptives Formular:

![Service-Handler aufrufen](/help/forms/assets/invoke-service-rule-editor.png)

### Hinzufügen von Erfolgs-Handler und Fehler-Handler

Um einen Erfolgs- oder Fehlerhandler hinzuzufügen, klicken Sie **[!UICONTROL Erfolgs-Handler hinzufügen]** bzw **[!UICONTROL auf]** Fehler-Handler hinzufügen.

Wenn Sie auf **[!UICONTROL Add Success Handler]** klicken, wird der Regeleditor **[!UICONTROL Invoke Service Success Handler]** angezeigt, in dem Sie Regeln oder Logiken angeben können, um die Antwort **Invoke Service** zu verwalten, wenn der Vorgang erfolgreich war. Sie können Regeln auch ohne Definition von Bedingungen angeben. Sie können jedoch Bedingungen für den Erfolgshandler hinzufügen, indem Sie auf die Option **[!UICONTROL Bedingung hinzufügen]** klicken.

![Service-Erfolgs-Handler aufrufen](/help/forms/assets/invoke-service-success-handler.png)

Sie können mehrere Regeln hinzufügen, um erfolgreiche Antworten für den Vorgang **Service aufrufen** zu verarbeiten:

![Multiple Success Handler](/help/forms/assets/invoke-service-multiple-success-handlers.png){width=50%, height=50%}

Auf ähnliche Weise können Sie Regeln hinzufügen, um die **Service aufrufen**-Ausgabeantwort zu verarbeiten, wenn der Vorgang nicht erfolgreich ist. In der folgenden Abbildung wird der Regeleditor **[!UICONTROL Invoke Service Failure Handler]** angezeigt:

![Service-Fehler-Handler aufrufen](/help/forms/assets/invoke-service-failue-handler.png)

Sie können auch mehrere Regeln hinzufügen, um nicht erfolgreiche Antworten aus dem Vorgang **Service aufrufen** zu verarbeiten.

Die Funktion **Fehlervalidierung auf dem Server aktivieren** ermöglicht Validierungen, die vom Autor beim Entwerfen eines adaptiven Formulars hinzugefügt wurden, um auch auf dem Server ausgeführt zu werden.

## Voraussetzungen für die Verwendung des Aufrufdienstes im Regeleditor

Im Folgenden finden Sie die Voraussetzungen, die Sie erfüllen müssen, bevor Sie **Service aufrufen** im Regeleditor verwenden:

* Stellen Sie sicher, dass Sie eine Datenquelle konfiguriert haben. Anweisungen zum Konfigurieren einer Datenquelle finden Sie [hier &#x200B;](/help/forms/configure-data-sources.md).
* Erstellen Sie ein Formulardatenmodell mithilfe der konfigurierten Datenquelle. Eine Anleitung zum Erstellen eines Formulardatenmodells finden Sie [hier](/help/forms/create-form-data-models.md).

## Erkunden von Invoke Service durch verschiedene Anwendungsfälle

Mit dem Service „Invoke **des visuellen Regeleditors** Sie mehrere nützliche Vorgänge ausführen. Sie können damit Dropdown-Optionen ausfüllen, wiederholbare oder einfache Bereiche festlegen und Formularfelder validieren, und zwar alles basierend auf der Ausgabeantwort des **Service aufrufen**. Dadurch wird die Flexibilität und Interaktivität Ihrer Formulare verbessert.

In der folgenden Tabelle werden einige Szenarien beschrieben, in denen der **Service aufrufen** verwendet werden kann:

| **Anwendungsfall** | **Beschreibung** |
|----------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| **Füllen von Dropdown-Optionen mithilfe der Ausgabe von „Service aufrufen“** | Dynamisches Füllen der Dropdown-Optionen auf der Grundlage der Daten, die aus der Ausgabe des Service aufrufen abgerufen wurden. [Klicken Sie hier](#use-case-1-populate-dropdown-values-using-the-output-of-invoke-service), um die Implementierung zu sehen. |
| **Festlegen eines wiederholbaren Bereichs mithilfe der Ausgabe von „Service aufrufen“** | Konfiguriert ein wiederholbares Bedienfeld mithilfe von Daten aus der Ausgabe des Aufrufdienstes und ermöglicht so dynamische Bedienfelder. [Klicken Sie hier](#use-case-2-set-repeatable-panel-using-output-of-invoke-service), um die Implementierung zu sehen. |
| **Bereich mithilfe der Ausgabe von „Service aufrufen“** | Legt den Inhalt oder die Sichtbarkeit eines Bedienfelds anhand bestimmter Werte aus der Ausgabe des aufrufenden Services fest. [Klicken Sie hier](#use-case-3-set-panel-using-output-of-invoke-service), um die Implementierung zu sehen. |
| **Verwenden Sie den Ausgabeparameter von „Service aufrufen“, um andere Felder zu überprüfen** | Verwendet bestimmte Ausgabeparameter aus dem Service „Invoke“, um die Formularfelder zu validieren. [Klicken Sie hier](#use-case-4-use-output-parameter-of-invoke-service-to-validate-other-fields), um die Implementierung zu sehen. |
| **Verwenden der Ereignis-Payload in der Aktion „Navigieren zu“ im Dienst „Aufrufen“** | Verwendet die Ereignis-Payload, um Erfolgs- und Fehlerantworten zu verarbeiten und während der Navigation Daten an die Aktion „Navigieren zu“ zu übergeben. [Hier klicken](#use-case-5-use-event-payload-in-navigate-to-action-in-invoke-service) um die Implementierung zu sehen. |

Erstellen Sie ein `Get Information` Formular, das Werte basierend auf der Eingabe abruft, die in das Textfeld `Pet ID` eingegeben wurde. Der folgende Screenshot zeigt das Formular, das in diesen Anwendungsfällen verwendet wird:

![Formular abrufen](/help/forms/assets/get-information-form.png)

**Formularfelder**

Fügen Sie die folgenden Felder zum Formular hinzu:

* **Haustier-ID eingeben**: textbox
* **Foto-URLs auswählen**: Dropdown
* **Tags**: Bedienfeld
   * Name: textbox
   * ID: Textfeld
* **Kategorie**: Bedienfeld
   * Name: textbox
* **Senden**: Senden-Schaltfläche

>[!NOTE]
>
> Wählen Sie im Feld **Bindungsverweis** im Dialogfeld **Eigenschaften** der Formularfelder ![foldersearch_18](assets/folder-search-icon.svg) aus und navigieren Sie zur binären Eigenschaft, die Sie im Formulardatenmodell (FDM) hinzugefügt haben.

**Konfigurieren von Bedienfeldern**

Legen Sie die Bereiche mit den folgenden Einschränkungen als repetitiv fest:

* Mindestwert: 1
* Höchstwert: 4

Sie können die Werte der sich wiederholenden Bereiche an Ihre Anforderungen anpassen.

**Datenquelle**

In diesem Beispiel wird die [Swagger Petstore](https://petstore.swagger.io/)-API zum Konfigurieren einer Datenquelle verwendet. Das [Formulardatenmodell](/help/forms/create-form-data-models.md) ist für den Service [getPetById](https://petstore.swagger.io/#/pet/getPetById) konfiguriert, der je nach eingegebener ID Heimtierdetails abruft.

Posten wir die folgende JSON mit dem Service [addPet](https://petstore.swagger.io/#/pet/addPet) in der API [Swagger Petstore](https://petstore.swagger.io/):

```
{
        "id": 101,
        "category": {
            "id": 1,
            "name": "Labrador"
        },
        "name": "Lisa",
        "photoUrls": [
            "https://example.com/photos/lisa1.jpg",
            "https://example.com/photos/lisa2.jpg"
        ],
        "tags": [
            {
                "id": 1,
                "name": "vaccinated"
            },
            {
                "id": 2,
                "name": "friendly"
            },
            {
                "id": 3,
                "name": "house-trained"
            }
        ],
        "status": "available"
    }
```

Regeln und Logik werden mithilfe der Aktion **Service aufrufen** im Regeleditor im `Pet ID`-Textfeld implementiert, um die erwähnten Anwendungsfälle zu demonstrieren.

Im Folgenden wird nun die Implementierung der einzelnen Anwendungsfälle im Detail untersucht.

### Anwendungsfall 1: Auffüllen von Dropdown-Werten mithilfe der Ausgabe von „Service aufrufen“

Dieses Anwendungsbeispiel zeigt, wie Dropdown-Optionen basierend auf der Ausgabe eines `Invoke Service` dynamisch aufgefüllt werden.

#### Implementierung

Erstellen Sie dazu eine Regel im `Pet ID` Textfeld, um den `getPetById`-Service aufzurufen. Legen Sie in der Regel die `enum`-Eigenschaft des `photo-url`-Dropdown-Menüs unter &quot;`photoUrls` hinzufügen“ auf **[!UICONTROL fest]**.

![Dropdown-Wert festlegen](/help/forms/assets/set-dropdownoption.png)

>[!NOTE]
>
> Siehe den Abschnitt [Hinzufügen von Erfolgs-Handlern und Fehler-Handlern](#adding-success-handler-and-failure-handler), um zu erfahren, wie Sie Erfolgs- und Fehler-Handler festlegen.

#### Ausgabe

Geben Sie `101` in das Textfeld `Pet ID` ein, um die Dropdown-Optionen basierend auf dem eingegebenen Wert dynamisch zu füllen.

![Ergebnis](/help/forms/assets/output1.png)

### Anwendungsfall 2: Festlegen eines wiederholbaren Bereichs mithilfe der Ausgabe von „Service aufrufen“

Dieses Anwendungsbeispiel zeigt, wie wiederholbare Bereiche basierend auf der Ausgabe eines „Service **&quot; dynamisch** werden.

#### Überlegungen

* Stellen Sie sicher, dass der Name des wiederholbaren Bereichs mit dem Parameter des **Service aufrufen** übereinstimmt, für den Sie den Bereich festlegen möchten.
* Das Bedienfeld wiederholt sich für die Anzahl der Werte, die vom entsprechenden Feld **Dienst aufrufen** zurückgegeben werden.

#### Implementierung

Erstellen Sie eine Regel für das `Pet ID` Textfeld, um den `getPetById`-Service aufzurufen. Fügen **[!UICONTROL in &quot;]** hinzufügen“ eine weitere Erfolgshandler-Antwort hinzu. Legen Sie in der Regel den Wert des `tags` Bedienfelds auf `tags` fest.

![Regel für wiederholbare Bereiche erstellen](/help/forms/assets/create-rule-repeatable-panel.png)

>[!NOTE]
>
> Siehe den Abschnitt [Hinzufügen von Erfolgs-Handlern und Fehler-Handlern](#adding-success-handler-and-failure-handler), um zu erfahren, wie Sie Erfolgs- und Fehler-Handler festlegen.

#### Ausgabe

Geben Sie `101` in das Textfeld `Pet ID` ein, um den wiederholbaren Bereich basierend auf dem Eingabewert dynamisch zu füllen.

![Ausgabe](/help/forms/assets/output2.png)

### Anwendungsfall 3: Festlegen des Bedienfelds mit der Ausgabe von „Service aufrufen“

Dieser Anwendungsfall zeigt, wie Sie den Wert eines Bedienfelds basierend auf der Ausgabe eines „Service **&quot; dynamisch**.

#### Überlegungen

* Stellen Sie sicher, dass der Name des Bedienfelds mit dem Parameter des **Service aufrufen** übereinstimmt, für den Sie das Bedienfeld festlegen möchten.
* Das Bedienfeld wiederholt sich für die Anzahl der Werte, die vom entsprechenden Feld „Service aufrufen“ zurückgegeben werden.

#### Implementierung

Erstellen Sie eine Regel für das `Pet ID` Textfeld, um den `getPetById`-Service aufzurufen. Fügen **[!UICONTROL in &quot;]** hinzufügen“ eine weitere Erfolgshandler-Antwort hinzu. Legen Sie in der Regel den Wert des `categoryname` Textfelds auf `category.name` fest.

>[!NOTE]
>
> Siehe den Abschnitt [Hinzufügen von Erfolgs-Handlern und Fehler-Handlern](#adding-success-handler-and-failure-handler), um zu erfahren, wie Sie Erfolgs- und Fehler-Handler festlegen.

![Regel für wiederholbare Bereiche erstellen](/help/forms/assets/set-panel-values.png)

#### Ausgabe

Geben Sie `101` in das Textfeld `Pet ID` ein, um den Bereich basierend auf dem Eingabewert dynamisch zu füllen.

![Ausgabe](/help/forms/assets/output3.png)

### Anwendungsfall 4: Verwenden des Ausgabeparameters „Service aufrufen“, um andere Felder zu validieren

Dieser Anwendungsfall zeigt, wie Sie die Ausgabe eines **Service aufrufen** zur dynamischen Validierung anderer Formularfelder verwenden.

#### Implementierung

Erstellen Sie eine Regel für das `Pet ID` Textfeld, um den `getPetById`-Service aufzurufen. Fügen **[!UICONTROL in „Fehler-Handler]**&quot; eine Fehler-Handler-Antwort hinzu. Blenden Sie die **Senden** aus, wenn eine falsche `Pet ID` eingegeben wurde.

![Fehlerhandler](/help/forms/assets/create-rule-failure-handler.png)

#### Ausgabe

Geben Sie `102` in das `Pet ID` Textfeld ein, und die Schaltfläche **Senden** ist ausgeblendet.

![Ausgabe](/help/forms/assets/output4.png)

### Anwendungsfall 5: Verwenden der Ereignis-Payload in „Zur Aktion navigieren“ im Dienst „aufrufen“

In diesem Anwendungsbeispiel wird gezeigt, wie eine Regel auf der Schaltfläche **Senden** konfiguriert wird, die einen **Service aufrufen** und den Benutzer dann mithilfe der Aktion **Navigieren zu“ zu einer anderen**.

#### Implementierung

Erstellen Sie eine Regel für die Schaltfläche **Senden**, um den `redirect-api`-API-Service aufzurufen. Dieser Service ist für die Weiterleitung des Benutzers zum Formular **Kontakt** verantwortlich.

Sie können eine API mithilfe der unten bereitgestellten JSON-Daten direkt als `redirect-api`-API-Service in Ihren Regeleditor integrieren:

```json
{
  "id": "1",
  "path": "/content/dam/formsanddocuments/contact-detail/jcr:content?wcmmode=disabled"
}
```

>[!NOTE]
>
> Um zu erfahren, wie Sie die -API direkt in die Benutzeroberfläche des Regeleditors integrieren können[&#x200B; klicken Sie &#x200B;](/help/forms/api-integration-in-rule-editor.md) hier, ohne ein vordefiniertes Formulardatenmodell zu verwenden.

Konfigurieren **[!UICONTROL in &quot;]** hinzufügen“ die Aktion **Navigieren zu**, um den Benutzer mithilfe des **-Parameters zur Seite** Kontaktieren `Event Payload` umzuleiten. Hier kann der Benutzer seine Kontaktdaten übermitteln.

![Ereignis-Payload](/help/edge/docs/forms/assets/navigate-to-eventpayload.png)

Optional können Sie einen Fehler-Handler konfigurieren, der eine Fehlermeldung anzeigt, wenn der Service-Aufruf fehlschlägt.

#### Ausgabe

Wenn auf **Senden**-Schaltfläche geklickt wird, wird der `redirect-api`-API-Service aufgerufen. Nach erfolgreicher Ausführung wird der Benutzer zur Seite **Kontakt** weitergeleitet.

![Payload-Ausgabe des Ereignisses](/help/forms/assets/output5.gif)

## Häufig gestellte Fragen

**F: Was passiert, wenn ich eine Regel mit dem Service „Invoke“ erstellt und dann auf die neueste Version der Kernkomponenten aktualisiert habe?**

**A:** Wenn Sie ein Upgrade auf die neueste Version der Kernkomponenten durchführen, wird die Regel **Service aufrufen** automatisch auf die neueste Benutzeroberfläche aktualisiert, da sie abwärtskompatibel ist.

**F: Kann ich mehrere Regeln hinzufügen, um erfolgreiche oder fehlgeschlagene Antworten für den Vorgang „Service aufrufen“ zu verarbeiten?**

**A:** Ja, Sie können mehrere Regeln hinzufügen, um erfolgreiche oder fehlgeschlagene Antworten für den Vorgang **Service aufrufen** zu verarbeiten.

## Verwandte Artikel

* [Konfigurieren von Datenquellen](configure-data-sources.md)
* [Erstellen eines Formulardatenmodells (FDM)](create-form-data-models.md)
* [Arbeiten mit einem Formulardatenmodell (FDM)](work-with-form-data-model.md)
* [Verwenden eines Formulardatenmodells (FDM)](using-form-data-model.md)


## Zusätzliche Ressourcen

{{see-also-rule-editor}}
