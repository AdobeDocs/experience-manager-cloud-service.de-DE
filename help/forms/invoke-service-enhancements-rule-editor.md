---
title: Welche Verbesserungen wurden an der VRE für den Invoke-Dienst für Formulare vorgenommen, die auf Kernkomponenten basieren?
description: Verbesserungen beim Aufrufdienst für den Regeleditor
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
keywords: Dienstverbesserungen in VRE aufrufen, Dropdown-Optionen mit dem invoke-Dienst ausfüllen, wiederholbares Bedienfeld mit Ausgabe des invoke-Dienstes festlegen, Bedienfeld mit Ausgabe des invoke-Dienstes festlegen und Ausgabeparameter des invoke-Dienstes zum Überprüfen anderer Felder verwenden.
source-git-commit: f77e0cd03a63200cb86fada780f2fecff5fadf94
workflow-type: tm+mt
source-wordcount: '1582'
ht-degree: 4%

---


# Verwenden des Aufrufdienstes im Visual Rule Editor für Formulare, die auf Kernkomponenten basieren

<span class="preview"> Dies ist eine Vorabveröffentlichungsfunktion, auf die über unseren [Vorabveröffentlichungskanal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=de#new-features) zugegriffen werden kann. </span>

Der Visual Rule Editor in einem adaptiven Formular unterstützt die Funktion **Dienst aufrufen** , mit der Sie einen Dienst aus der Liste der für Ihre Instanz konfigurierten Formulardatenmodelle (FDM) auswählen können. Sie können Formularfelder direkt den Eingabeparametern des Dienstes zuordnen. Um Formularfelder den Ausgabeparametern zuzuordnen, verwenden Sie die Ereignis-Payload-Option für den angegebenen Formulardatenmodelldienst. Darüber hinaus können Sie mit dem visuellen Regeleditor Regeln für Erfolgs- und Fehler-Handler für Vorgänge vom Typ **Dienst aufrufen** erstellen, die auf den Ausgabeantworten basieren. Erfolgshandler verwalten die erfolgreiche Ausführung des Vorgangs **Dienst aufrufen** , während Fehler-Handler alle aufgetretenen Fehler beheben.

### Vorteile der Verwendung des Aufrufdienstes im Regeleditor des Formulars

Im Folgenden finden Sie einige Vorteile der Verwendung des Vorgangs &quot;Invoke Service&quot;im Regeleditor eines Adaotive-Formulars:

* **Optimierte Integration**: Der Visual Rule Editor vereinfacht die Integration externer Dienste oder APIs in Ihre adaptive Forms. Mit dem **Aufrufdienst** können Sie Formulare einfach mit verschiedenen Datenquellen und Diensten verbinden, ohne dass eine komplexe Codierung erforderlich ist, wodurch die Formularintegration effizienter wird.

* **Dynamische Reaktionsverarbeitung**: Sie können Erfolgs- und Fehlerantworten basierend auf den Ausgabeantworten des **Aufrufdienstes** verwalten, sodass Formulare dynamisch auf verschiedene Szenarien reagieren können. Dadurch wird sichergestellt, dass Formulare unterschiedliche Bedingungen angemessen handhaben, was die Flexibilität und Kontrolle verbessert.

* **Verbesserte Benutzerinteraktion**: Durch die Verwendung des **Aufrufdienstes** im Regeleditor wird eine Echtzeitüberprüfung in Ihren Formularen ermöglicht, was eine bessere Benutzererfahrung ermöglicht. Außerdem wird sichergestellt, dass Daten serverseitig genau validiert werden, wodurch Fehler reduziert und die Formularzuverlässigkeit verbessert wird.

## Aufrufen von Service-Handlern für Erfolgs- und Fehlerantworten

>[!NOTE]
>
> Sie können die Erfolgs- und Fehler-Handler für den **Aufrufdienst** nur für Formulare verwenden, die auf Kernkomponenten basieren. Forms, die auf Foundation-Komponenten basiert, unterstützt keine Erfolgs- und Fehler-Handler für **Aufrufdienst**.

Mit dem visuellen Regeleditor können Sie Regeln für Erfolgs- und Fehler-Handler für Vorgänge vom Typ **Dienst aufrufen** erstellen, die auf den Ausgabeantworten basieren. Die folgende Abbildung zeigt den **Aufrufdienst** im visuellen Regeleditor für ein adaptives Formular:

![Dienst-Handler aufrufen](/help/forms/assets/invoke-service-rule-editor.png)

Um den Erfolgs- oder Fehler-Handler hinzuzufügen, klicken Sie auf **[!UICONTROL Erfolgshandler hinzufügen]** bzw. auf **[!UICONTROL Fehler-Handler hinzufügen]** .

Wenn Sie auf **[!UICONTROL Erfolgshandler hinzufügen]** klicken, wird der Regeleditor **[!UICONTROL Aufrufdienst-Erfolgshandler]** angezeigt, mit dem Sie Regeln oder Logik zur Verwaltung der Ausgabedarstellung für den **Aufrufdienst** festlegen können, wenn der Vorgang erfolgreich war. Sie können Regeln auch ohne Bedingungen angeben. Sie können jedoch Bedingungen für den Erfolgshandler hinzufügen, indem Sie auf die Option **[!UICONTROL Bedingung hinzufügen]** klicken.

![Aufrufen des Erfolgshadlers des Dienstes](/help/forms/assets/invoke-service-success-handler.png)

Sie können mehrere Regeln hinzufügen, um erfolgreiche Antworten für den Vorgang **Dienst aufrufen** zu verarbeiten:

![Mehrere Erfolgshandler](/help/forms/assets/invoke-service-multiple-success-handlers.png){width=50%, height=50%}

Auf ähnliche Weise können Sie Regeln hinzufügen, um die Ausgabeantwort **Dienst aufrufen** zu verarbeiten, wenn der Vorgang nicht erfolgreich ist. Die folgende Abbildung zeigt den Regeleditor **[!UICONTROL Dienst-Fehler-Handler aufrufen]** :

![Aufrufen des Fehler-Handlers des Dienstes](/help/forms/assets/invoke-service-failue-handler.png)

Sie können auch mehrere Regeln hinzufügen, um nicht erfolgreiche Antworten aus dem Vorgang **Dienst aufrufen** zu verarbeiten.

Mit der Funktion **Fehlervalidierung auf Server aktivieren** können vom Autor hinzugefügte Validierungen beim Entwerfen eines adaptiven Formulars auch auf dem Server ausgeführt werden.

## Voraussetzungen für die Verwendung des Aufrufdienstes im Regeleditor

Im Folgenden finden Sie die Voraussetzungen, die Sie erfüllen müssen, bevor Sie den **Aufrufdienst** im Regeleditor verwenden:

* Stellen Sie sicher, dass Sie eine Datenquelle konfiguriert haben. Anweisungen zum Konfigurieren einer Datenquelle finden Sie [hier klicken](/help/forms/configure-data-sources.md).
* Erstellen Sie ein Formulardatenmodell mit der konfigurierten Datenquelle. Eine Anleitung zum Erstellen eines Formulardatenmodells finden Sie [hier klicken](/help/forms/create-form-data-models.md).
* Stellen Sie sicher, dass Kernkomponenten für Ihre Umgebung aktiviert sind. Ausführliche Anweisungen zum Aktivieren von Kernkomponenten für Ihre Umgebung finden Sie, indem Sie [hier klicken](/help/forms/enable-adaptive-forms-core-components.md).

## Untersuchen von Invoke Service durch verschiedene Anwendungsfälle

Mit dem **Aufrufdienst** des Visual Rule Editors können Sie mehrere nützliche Vorgänge ausführen. Sie können sie zum Ausfüllen von Dropdown-Optionen, zum Festlegen wiederholbarer oder einfacher Bedienfelder und zum Überprüfen von Formularfeldern verwenden, die alle auf der Ausgabeantwort des **Aufrufdienstes** basieren. So erhöhen Sie die Flexibilität und Interaktivität Ihrer Formulare.

In der folgenden Tabelle werden einige Szenarien beschrieben, in denen der **Aufrufdienst** verwendet werden kann:

| **Nutzungsszenario** | **Beschreibung** |
|----------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| **Füllen von Dropdown-Optionen mithilfe der Ausgabe des Aufrufdienstes** | Füllt Dropdown-Optionen dynamisch basierend auf Daten, die aus der Ausgabe des Aufrufdienstes abgerufen wurden. [Klicken Sie hier](#use-case-1-populate-dropdown-values-using-the-output-of-invoke-service), um die Implementierung anzuzeigen. |
| **Festlegen eines wiederholbaren Bereichs mithilfe der Ausgabe des Aufrufdienstes** | Konfiguriert ein wiederholbares Bedienfeld mithilfe von Daten aus der Ausgabe des Aufrufdienstes, was dynamische Bedienfelder ermöglicht. [Klicken Sie hier](#use-case-2-set-repeatable-panel-using-output-of-invoke-service), um die Implementierung anzuzeigen. |
| **Bereich mithilfe der Ausgabe des Aufrufdienstes festlegen** | Legt den Inhalt oder die Sichtbarkeit eines Bedienfelds mithilfe bestimmter Werte aus der Ausgabe des Aufrufdienstes fest. [Klicken Sie hier](#use-case-3-set-panel-using-output-of-invoke-service), um die Implementierung anzuzeigen. |
| **Verwenden Sie den Ausgabeparameter des Aufrufdienstes, um andere Felder zu validieren** | Verwendet bestimmte Ausgabeparameter aus dem Aufrufdienst , um die Formularfelder zu überprüfen. [Klicken Sie hier](#use-case-4-use-output-parameter-of-invoke-service-to-validate-other-fields), um die Implementierung anzuzeigen. |

Erstellen Sie ein `Get Information` -Formular, das Werte basierend auf der Eingabe im Textfeld `Pet ID` abruft. Der folgende Screenshot zeigt das in diesen Anwendungsfällen verwendete Formular:

![Informationsformular abrufen](/help/forms/assets/get-information-form.png)

**Formularfelder**

Fügen Sie dem Formular die folgenden Felder hinzu:
* **Pet-ID eingeben**: Textfeld
* **Foto-URLs auswählen**: Dropdown
* **Tags**: Bedienfeld
   * Name: Textbox
   * ID: Textbox
* **Kategorie**: Bedienfeld
   * Name: Textbox
* **Senden**: Senden-Schaltfläche

>[!NOTE]
>
> Wählen Sie im Feld **Bindungsverweis** im Dialogfeld **Eigenschaften** der Formularfelder die Option ![folderSearch_18](assets/folder-search-icon.svg) und navigieren Sie zu der binären Eigenschaft, die Sie im Formulardatenmodell (FDM) hinzugefügt haben.

**Konfigurieren von Bedienfeldern**

Legen Sie die Bedienfelder mit den folgenden Einschränkungen als wiederholend fest:
* Mindestwert: 1
* Höchstwert: 4

Sie können die Werte der sich wiederholenden Bedienfelder an Ihre Anforderungen anpassen.

**Datenquelle**

In diesem Beispiel wird die API [Swagger Petstore](https://petstore.swagger.io/) verwendet, um eine Datenquelle zu konfigurieren. Das [Formulardatenmodell](/help/forms/create-form-data-models.md) ist für den Dienst [getPetById](https://petstore.swagger.io/#/pet/getPetById) konfiguriert, der die Heimtierdetails basierend auf der eingegebenen ID abruft.

Posten wir die folgende JSON mit dem Dienst [addPet](https://petstore.swagger.io/#/pet/addPet) in der API [Swagger Petstore](https://petstore.swagger.io/) :

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


Regeln und Logiken werden mithilfe der Aktion **Dienst aufrufen** im Regeleditor im Textfeld `Pet ID` implementiert, um die erwähnten Anwendungsfälle zu demonstrieren.

Im Folgenden wird die Implementierung der einzelnen Anwendungsfälle detailliert beschrieben.

### Anwendungsfall 1: Füllen von Dropdown-Werten mithilfe der Ausgabe des Invoke Service

Dieser Anwendungsfall zeigt, wie Dropdown-Optionen dynamisch basierend auf der Ausgabe eines `Invoke Service` gefüllt werden.

#### Implementierung

Erstellen Sie dazu eine Regel im Textfeld `Pet ID` , um den Dienst `getPetById` aufzurufen. Setzen Sie in der Regel die Eigenschaft `enum` des Dropdown-Menüs `photo-url` in **[!UICONTROL Erfolgshandler hinzufügen]** auf `photoUrls`.

![Dropdown-Wert festlegen](/help/forms/assets/set-dropdownoption.png)

#### Ausgabe

Geben Sie `101` in das Textfeld `Pet ID` ein, um die Dropdown-Optionen basierend auf dem eingegebenen Wert dynamisch auszufüllen.

![Ergebnis](/help/forms/assets/output1.png)

### Anwendungsfall 2: Festlegen eines wiederholbaren Bereichs mithilfe der Ausgabe des Invoke Service

Dieser Anwendungsfall zeigt, wie wiederholbare Bedienfelder dynamisch basierend auf der Ausgabe eines **Aufrufdienstes** gefüllt werden.

#### Überlegungen

* Stellen Sie sicher, dass der Name des wiederholbaren Bereichs mit dem Parameter des **Aufrufdienstes** übereinstimmt, für den Sie den Bereich festlegen möchten.
* Das Bedienfeld wiederholt sich für die Anzahl der Werte, die vom entsprechenden Feld **Dienst aufrufen** zurückgegeben werden.

#### Implementierung

Erstellen Sie eine Regel im Textfeld `Pet ID` , um den Dienst `getPetById` aufzurufen. Fügen Sie in **[!UICONTROL Erfolgshandler hinzufügen]** eine weitere Antwort des Erfolgshandlers hinzu. Setzen Sie den Wert des Bereichs `tags` in der Regel auf `tags`.

![Regel für wiederholbaren Bereich erstellen](/help/forms/assets/create-rule-repeatable-panel.png)

#### Ausgabe

Geben Sie `101` in das Textfeld `Pet ID` ein, um den wiederholbaren Bereich dynamisch basierend auf dem Eingabewert zu füllen.

![Ausgabe](/help/forms/assets/output2.png)

### Nutzungsszenario 3: Bedienfeld mithilfe der Ausgabe des Invoke-Dienstes festlegen

Dieser Anwendungsfall zeigt, wie Sie den Wert eines Bedienfelds dynamisch festlegen, basierend auf der Ausgabe eines **Aufrufdienstes**.

#### Überlegungen

* Stellen Sie sicher, dass der Name des Bedienfelds mit dem Parameter des **Aufrufdienstes** übereinstimmt, für den Sie den Bereich festlegen möchten.
* Das Bedienfeld wiederholt sich für die Anzahl der Werte, die vom entsprechenden Feld &quot;Dienst aufrufen&quot;zurückgegeben werden.

#### Implementierung

Erstellen Sie eine Regel im Textfeld `Pet ID` , um den Dienst `getPetById` aufzurufen. Fügen Sie in **[!UICONTROL Erfolgshandler hinzufügen]** eine weitere Antwort des Erfolgshandlers hinzu. Setzen Sie den Wert des Textfelds `categoryname` in der Regel auf `category.name`.

![Regel für wiederholbaren Bereich erstellen](/help/forms/assets/set-panel-values.png)

#### Ausgabe

Geben Sie `101` in das Textfeld `Pet ID` ein, um den Bereich dynamisch basierend auf dem Eingabewert zu füllen.

![Ausgabe](/help/forms/assets/output3.png)

### Nutzungsszenario 4: Verwenden Sie den Ausgabeparameter des Aufrufdienstes, um andere Felder zu validieren

Dieser Anwendungsfall zeigt, wie Sie die Ausgabe eines **Aufrufdienstes** verwenden, um andere Formularfelder dynamisch zu überprüfen.

#### Implementierung

Erstellen Sie eine Regel im Textfeld `Pet ID` , um den Dienst `getPetById` aufzurufen. Fügen Sie in **[!UICONTROL Fehler-Handler hinzufügen]** eine Antwort des Fehler-Handlers hinzu. Blenden Sie die Schaltfläche **Senden** aus, wenn ein falscher `Pet ID` eingegeben wird.

![Fehler-Handler](/help/forms/assets/create-rule-failure-handler.png)

#### Ausgabe

Geben Sie `102` in das Textfeld `Pet ID` ein, und die Schaltfläche **Senden** ist ausgeblendet.

![Ausgabe](/help/forms/assets/output4.png)

## Häufig gestellte Fragen

**F: Was passiert, wenn ich eine Regel mit dem Invoke-Dienst erstellt und dann auf die neueste Version der Kernkomponenten aktualisiert habe?**

**A:** Wenn Sie auf die neueste Version der Kernkomponenten aktualisieren, wird die Regel **Dienst aufrufen** automatisch auf die neueste Benutzeroberfläche aktualisiert, da sie abwärtskompatibel ist.

**Q: Kann ich mehrere Regeln hinzufügen, um erfolgreiche oder fehlgeschlagene Antworten für den Vorgang &quot;Invoke Service&quot;zu verarbeiten?**

**A:** Ja, Sie können mehrere Regeln hinzufügen, um erfolgreiche oder fehlgeschlagene Antworten für den Vorgang **Dienst aufrufen** zu verarbeiten.

## Verwandte Artikel

* [Konfigurieren von Datenquellen](configure-data-sources.md)
* [Erstellen eines Formulardatenmodells (FDM)](create-form-data-models.md)
* [Arbeiten mit einem Formulardatenmodell (FDM)](work-with-form-data-model.md)
* [Verwenden eines Formulardatenmodells (FDM)](using-form-data-model.md)


## Zusätzliche Ressourcen

{{see-also-rule-editor}}

