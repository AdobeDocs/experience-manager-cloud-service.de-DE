---
title: In diesem Artikel werden verschiedene Anwendungsfälle für den Regeleditor in einem adaptiven Formular beschrieben, die auf Kernkomponenten basieren.
description: In diesem Artikel werden verschiedene Anwendungsfälle für den Regeleditor in einem adaptiven Formular basierend auf Kernkomponenten untersucht. Außerdem wird gezeigt, wie benutzerdefinierte Funktionen zum Erstellen benutzerdefinierter Regeln für Formulare verwendet werden können.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
exl-id: 062ed441-6e1f-4279-9542-7c0fedc9b200
source-git-commit: 85555ebe4bfa41bf01d7c5610fa5760551830b5c
workflow-type: tm+mt
source-wordcount: '1975'
ht-degree: 0%

---

# Verbesserungen des Regeleditors und Anwendungsfälle

<span class="preview"> Dies sind Vorabversionsfunktionen, die über unseren <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=de#new-features">Vorabversionskanal“ verfügbar </a>. Diese Verbesserungen gelten auch für Edge Delivery Services Forms.

In diesem Artikel werden die neuesten Verbesserungen am Regeleditor in Adaptive Forms vorgestellt. Diese Aktualisierungen sollen Ihnen helfen, das Formularverhalten einfacher zu definieren, ohne benutzerdefinierten Code zu schreiben, und dynamischere, reaktionsfähigere und personalisiertere Formularerlebnisse zu erstellen.

In der folgenden Tabelle sind die jüngsten Verbesserungen am Regeleditor in Adaptive Forms zusammen mit einer kurzen Beschreibung und den wichtigsten Vorteilen der einzelnen Funktionen aufgeführt:

| Verbesserung | Beschreibung | Vorteile |
|---|----|---|
| **Validierung mithilfe der `validate()` Methode** | In der Funktionsliste verfügbar, um einzelne Felder, Bereiche oder das gesamte Formular zu überprüfen. | - Granulare Validierung auf Bedienfeld-, Feld- oder <br> auf Formularebene - Besseres Benutzererlebnis mit zielgerichtetem <br> für Fehlermeldungen - Verhindert das Fortschreiten bei unvollständigen <br> - Reduziert Fehler bei der Formularübermittlung |
| **DOR herunterladen** | Im Regeleditor verfügbare vordefinierte Funktion zum Herunterladen des Datensatzdokuments (DoR). | - Keine benutzerdefinierte Entwicklung für das Herunterladen von DoR-<br> erforderlich - Konsistentes Download-Erlebnis in allen Formularen |
| **Dynamische Variablen** | Erstellen Sie Regeln mithilfe von Variablen, die sich je nach Benutzereingabe oder anderen Bedingungen ändern. | - Ermöglicht flexible Regelbedingungen <br> - Reduziert den Bedarf an doppelten <br> - Beseitigt die Notwendigkeit, ausgeblendete Felder zu erstellen |
| **Benutzerdefinierte ereignisbasierte Regeln** | Definieren Sie Regeln, die über die standardmäßigen Trigger hinaus auf benutzerspezifische Ereignisse reagieren. | - Unterstützt erweiterte Anwendungsfälle <br> - Bessere Kontrolle darüber, wann und wie Regeln ausgeführt werden <br> - Verbesserte Interaktivität |
| **Kontextabhängige wiederholbare Bereichsausführung** | Regeln werden jetzt für jeden wiederholten Bereich im richtigen Kontext ausgeführt, anstatt nur für die letzte Instanz. | - Präzise Regelanwendung für jede Wiederholungsinstanz <br> - Reduziert Fehler in dynamischen Abschnitten <br> - Verbessert das Benutzererlebnis mit wiederholten Inhalten |
| **Unterstützung für Abfragezeichenfolgen-, UTM- und Browser-Parameter** | Erstellen Sie Regeln, die das Formularverhalten basierend auf URL-Parametern oder browserspezifischen Werten anpassen. | - Ermöglicht Personalisierung basierend auf Quell- oder <br> - Nützlich für Marketing- oder Tracking-spezifische Abläufe <br> - keine zusätzliche Skripterstellung oder Anpassung erforderlich |

>[!NOTE]
>
> Die Verbesserungen am Regeleditor gelten auch für Edge Delivery Services Forms.

Im Folgenden werden die einzelnen Methoden im Detail mit spezifischen Anwendungsfällen untersucht, um zu verstehen, wie diese Funktionen verwendet werden können, um Benutzern ein personalisiertes Erlebnis zu bieten

## Validate-Methode in der Funktionsliste

Verbesserte Validierungsfunktionen, mit denen die **validate()**-Methode in der Funktionsliste verwendet werden kann, um Bereiche, Felder oder ganze Formulare zu validieren. In einem mehrstufigen Kreditantragsformular müssen Sie beispielsweise verschiedene Abschnitte validieren, bevor Sie Benutzerinnen und Benutzern ermöglichen, mit dem nächsten Schritt fortzufahren.

**Szenario:** Ein Finanzinstitut bietet ein mehrstufiges Kreditantragsformular an, in dem Benutzer verschiedene Abschnitte ausfüllen müssen, z. B.:

* Persönliche Informationen
* Details zur Beschäftigung
* Details zum Darlehen
* Überprüfen und senden

Bevor ein Benutzer von einem Schritt zum nächsten wechselt, muss das Formular nur die Felder innerhalb des aktuellen Abschnitts überprüfen. Beispielsweise sollte es dem Benutzer nicht gestattet sein, mit „Beschäftigungsdetails“ fortzufahren, es sei denn, alle erforderlichen Felder unter „Persönliche Details“ sind korrekt ausgefüllt.

**Implementierung mithilfe von validate() im Regeleditor**

Bei einer **Weiter**-Schaltfläche in jedem Bedienfeld wird eine Regel mithilfe der Methode **validate()** Trigger. Die Regel prüft, ob alle Felder im aktuellen Bedienfeld gültig sind. Wenn die Validierung erfolgreich war, navigiert das Formular zum nächsten Bedienfeld. Andernfalls werden Fehlermeldungen angezeigt, die den Benutzer anweisen, die Eingabe zu korrigieren.

Im folgenden Screenshot wird die Regel angezeigt, die auf die Schaltfläche **Weiter** angewendet wurde:

![Schaltfläche „Weiter validieren](/help/forms/assets/validate-next.png)

In der obigen Regel überprüft die Schaltfläche **Weiter**, ob die Felder im Abschnitt **Persönliche**) gültig sind. Wenn die Details ungültig sind, wechselt der Fokus auf das Feld **Name** im Bedienfeld **Persönliche Details**.

![Ausgabe](/help/forms/assets/valid-output.png)

>[!NOTE]
>
>Sie können die Methode **validate()** für Formulare, Fragmente oder einzelne Felder verwenden. Wenn ein Fragment in einem Formular enthalten ist, werden sowohl das Formular als auch das Fragment im Validierungskontext als Optionen angezeigt. In diesem Fall bezieht sich das Fragment auf die darin enthaltenen Felder, während sich das Formular auf das übergeordnete Formular bezieht, in dem das Fragment eingebettet ist.

## DownloadDoR als OOTB-Funktion im Regeleditor

Mithilfe der **DownloadDor()** vordefinierten Funktion (OOTB) im Regeleditor können Benutzer das Datensatzdokument herunterladen , wenn das Formular zum Generieren des Datensatzdokuments konfiguriert ist.

>[!NOTE]
>
>Wenn das Formular nicht für das Datensatzdokument konfiguriert ist, wird eine Fehlermeldung angezeigt, wenn die Regel mit der Funktion **downloadDoR()** auf die Schaltfläche angewendet wird.

**Szenario**: Eine Regierungsbehörde stellt ein digitales Antragsformular für die Ausstellung von Zertifikaten bereit. Nach dem Absenden des Formulars benötigen Antragsteller oft eine Kopie des ausgefüllten Formulars für ihre Aufzeichnungen oder um es einer anderen Abteilung zur Verfügung zu stellen. Um das Anwendererlebnis zu verbessern, möchte die Agentur Antragstellern die Möglichkeit geben, ein Datensatzdokument (DoR) sofort nach der Einreichung oder zu einem beliebigen Zeitpunkt vor der endgültigen Einreichung herunterzuladen.

**Implementierung mithilfe von DownloadDor() im Regeleditor**

Wenn **Formular mithilfe des Regeleditors eine Schaltfläche** Herunterladen“ hinzugefügt wird, wird eine Regel so konfiguriert, dass beim Klicken auf die Schaltfläche die Funktion **DownloadDor()** Trigger wird.

Im folgenden Screenshot wird die Regel angezeigt, die auf die Schaltfläche **Herunterladen** angewendet wurde:

![Schaltflächenregel herunterladen](/help/forms/assets/download-button-rule.png)

>[!NOTE]
>
> Über **Feld** Eingabe“ können Benutzer den Dateinamen für ein herunterladbares Dokument angeben. Dies ist ein optionaler Parameter.

Wenn das Formular für die DoR-Generierung konfiguriert ist, generiert diese Funktion die PDF sofort und lädt sie herunter, ohne dass eine benutzerdefinierte Funktion erforderlich ist.

![Datensatzdokument (Document of Record, DoR)](/help/forms/assets/download-dor-output.png)

## Unterstützung dynamischer Variablen in Regeln

Der erweiterte Regeleditor unterstützt die Erstellung und Verwendung dynamischer (temporärer) Variablen. Diese Variablen können während des gesamten Lebenszyklus des Formulars mithilfe der integrierten Funktionen **Variablenwert festlegen“ und**&#x200B;**Variablenwert abrufen** festgelegt werden.
Diese Variablen:

* werden nicht mit den Formulardaten gesendet.
* Kann Zwischenwerte oder berechnete Werte enthalten.
* Kann in bedingter Logik und Aktionen verwendet werden.

**Szenario**: Benutzende können über ein Online-Einkaufsformular ein Produkt auswählen, eine Menge eingeben und ein Land für den Versand auswählen. Der Produktpreis ist ein fester Wert, der über ein Formularfeld erfasst wird, während die Versandkosten je nach ausgewähltem Land dynamisch variieren.

Um das Formular nicht mit ausgeblendeten Feldern zu überladen, entscheidet sich das Unternehmen, die Versandkosten in einer temporären Variablen zu speichern und sie für Echtzeit-Berechnungen zu verwenden.

**Implementierung mithilfe der Funktionen Variablenwert festlegen und Variablenwert abrufen im Regeleditor**

Eine Regel wird für das Fragment **Adresse** mit der Funktion **Variablenwert festlegen** konfiguriert, um eine temporäre Variable mit dem Namen **extraCharge** zuzuweisen. Der Wert dieser Variablen ändert sich dynamisch je nach ausgewähltem Land. Beispiel:

* Wenn der Benutzer die Option USA auswählt **wird** extraCharge) auf 500 gesetzt.
* Für jedes andere Land **extraCharge** auf 100 gesetzt.

![Variablenwert festlegen](/help/forms/assets/setvalue.png)

Später, wenn die **Gesamtkosten der Sendung** berechnet wird, wird die Funktion **Variablenwert abrufen** verwendet, um den Wert von **extraCharge** abzurufen. Dieser Wert wird dem **Produktpreis × Produktmenge) hinzugefügt,** den endgültigen zu zahlenden Betrag beim Klick auf die Schaltfläche zu berechnen.

![Variablenwert abrufen](/help/forms/assets/getvalue.png)

Das Feld **Gesamtversandkosten** wird dynamisch aktualisiert, um sowohl die Produktkosten als auch die Versandkosten widerzuspiegeln, wenn der Benutzer das Land oder die Menge ändert.
![Ausgabe](/help/forms/assets/getsetvalue-output.png)

>[!NOTE]
>
> Sie können auch eine Funktion **Wert der Variablen abrufen** in der Wenn-Bedingung hinzufügen.
> &#x200B;> ![Funktion „Variablenwert abrufen“ in Wenn](/help/forms/assets/when-get-variable.png){width=50%,height=50%, align=center}

Dieser Ansatz ermöglicht dynamische Echtzeit-Berechnungen, ohne dem Formular zusätzliche Felder hinzuzufügen, wodurch die Struktur sauber und benutzerfreundlich bleibt.

## Unterstützung benutzerdefinierter ereignisbasierter Regeln

Der erweiterte Regeleditor unterstützt die benutzerdefinierte Ereignisbehandlung mit den Funktionen **Dispatch** und **On Trigger Event**. Diese Funktionen ermöglichen es verschiedenen Teilen des Formulars, durch Senden und Abhören benutzerdefinierter Ereignisse zu kommunizieren, was eine sauberere, modulare Logik ermöglicht, ohne Aktionen eng mit bestimmten Feldern zu verknüpfen.

**Szenario**: Ein Anmeldeformular wird mit einem wiederverwendbaren Anmeldefragment erstellt, das die Felder **Benutzername eingeben** und **Kennwort eingeben** enthält. Wenn ein Benutzer gültige Anmeldeinformationen bereitstellt, validiert das Formular die Eingabe und initiiert den **OTP abrufen**-Prozess. Nachdem der Benutzer einen gültigen OTP eingegeben hat, wird er zur entsprechenden Seite weitergeleitet.

Anstatt die Logik direkt an die Felder zu binden, verwendet das Formular einen ereignisbasierten Ansatz mit **Dispatch-** und **On Trigger Event**, um die Modularität und Wartbarkeit zu verbessern.

**Implementierung mithilfe des Dispatch-Ereignisses und des On-Trigger-Ereignisses**

Das Anmeldungsfragment wird dem Formular hinzugefügt und enthält vordefinierte Felder für Benutzername und Kennwort. Auf der Schaltfläche **OTP abrufen** wird eine Regel zum Anzeigen des **Validierungsbereichs** konfiguriert, der das Eingabefeld zum Eingeben und Validieren des OTP enthält.

![OTP-Regel abrufen](/help/forms/assets/get-otp-rule.png)

Im **Validierungsbereich** wird eine Regel für die Schaltfläche Validieren konfiguriert. Die API-Integration wird verwendet, um den im Feld „OTP eingeben **eingegebenen OTP zu**. Wenn die Validierung erfolgreich ist **wird ein &quot;**&quot; mit dem Namen **LoggedIn** ausgelöst, wobei die Ereignis-Payload die API-Antwort enthält.

![Ereignisregel „In Trigger&quot;](/help/forms/assets/trigger-event-rule.png)

Auf Formularebene wird eine Regel konfiguriert, die auf das „LoggedIn **-Ereignis**. Wenn dieses Ereignis ausgelöst wird, zeigt die Regel die Umleitungsmeldung an und bringt den Benutzer zur Dashboard-Seite.

![Dispatch-Ereignisregel](/help/forms/assets/dispatch-event-rule.png)

Wenn der Benutzer das Formular mit den richtigen Anmeldeinformationen und einem gültigen OTP sendet, ist die Anmeldung erfolgreich und der Benutzer wird zu seinem Dashboard weitergeleitet.

Unterstützung benutzerdefinierter Ereignisse, mit denen Entwickelnde benutzerdefinierte Ereignisse erstellen und Trigger erstellen können, die als Bedingungen im Regeleditor verwendet werden können.

## Kontextbasierte Regelausführung für wiederholbare Bereiche

Adaptive Forms unterstützt die kontextabhängige Regelausführung für wiederholbare Bereiche. Auf diese Weise können Regeln speziell auf die Bedienfeldinstanz angewendet werden, in der der Benutzer interagiert, anstatt alle Instanzen zu beeinflussen oder auf die letzte zu verweisen.

**Szenario**: Benutzende können mit einem Produktbestellungsformular mehrere Produkte in separaten Bereichen hinzufügen. Jedes Bedienfeld enthält ein Feld **Anzahl der Produkte** und ein Feld **Gesamtkosten**. Wenn ein(e) Benutzende(r) die Menge für ein Produkt aktualisiert, sollte das Formular den Gesamtpreis neu berechnen, aber nur für dieses bestimmte Bedienfeld und nicht für alle anderen.

**Implementierung mithilfe von kontextabhängigen Regeln im Regeleditor**

Eine Regel wird für das Feld **Anzahl der Produkte** innerhalb des wiederholbaren Produktbereichs konfiguriert.

Im folgenden Screenshot wird die Regel für das Feld **Number of Product** im Bereich Wiederholbares Produkt angezeigt:

![Anzahl der Produktregel](/help/forms/assets/number-of-product-rule.png)

Wenn die Menge geändert wird, ruft die Regel den Stückpreis des ausgewählten Produkts ab und berechnet nur die Gesamtkosten für dieses Bedienfeld.

![Kontextabhängige Regelausgabe](/help/forms/assets/context-aware-rule-output.png)

## Auf URL- und Browser-Parametern basierende Regeln in Adaptive Forms

Adaptive Forms unterstützen die Ausführung dynamischer Regeln mithilfe externer Parameter, die über die Formular-URL übergeben oder von der Browser-Umgebung des Benutzers abgeleitet werden. Dies ermöglicht personalisierte und kontextbezogene Formularerlebnisse, die davon abhängen, woher der Besucher kam oder welches Gerät er verwendet.

## Zulässige Parametertypen

| Parametertyp | Unterstützte Optionen | Beschreibung | Beispielwert |
| --- | --- | --- | ---|
| Abfrageparameter | `ref` (nur Zeichenfolgen) | Generisches Schlüssel-Wert-Paar in der URL nach der `?` | `?ref=partner123` |
| UTM-Parameter | UTM Source<br>UTM Medium<br>UTM Campaign<br>UTM Term<br>UTM Content | Spezielle Abfrageparameter für das Kampagnen-Tracking | `?utm_source=google&utm_medium=email` |
| URL-Parameter | Host-<br> | Extrahiert Strukturkomponenten der Formular-URL | `hostname=www.example.com`, `path=/signup` |
| Browser-Parameter | Browser-Agent<br>Browser-Sprache<br>Browser-Plattform | Vom Browser oder Gerät des Benutzers abgeleitete Werte | `Browser Agent=Mozilla`, `Language=en-US` |

**Szenario**: Ein Formular zur Lead-Generierung muss die Willkommensnachricht entsprechend der Traffic-Quelle anpassen. Wenn ein(e) Benutzende(r) über eine Google-Anzeigenkampagne (mithilfe von utm_source=google in der URL) in das Formular gelangt, sollte das Formular eine benutzerdefinierte Begrüßung enthalten.

**Implementierung mithilfe des UTM-Parameters**

Eine Regel wird für ein Textfeld konfiguriert, das Google-Benutzern eine benutzerdefinierte Nachricht anzeigt und den Parameter **utm_source** verwendet.

Im folgenden Screenshot wird die für Textnachrichten konfigurierte Regel angezeigt:

![Regel für Textnachricht](/help/forms/assets/utm-param-rule.png)

Wenn der Parameterwert **utm_source** gleich „google“ ist, wird eine benutzerdefinierte Nachricht als „Hallo Google-Benutzer, Willkommen bei der Campaign-Anzeige!“ angezeigt. wird angezeigt.

![utm-param-output](/help/forms/assets/utm-param-output.png)

Auf diese Weise können Marketing-Fachleute den Benutzenden relevante Inhalte bereitstellen, die auf der Kampagne basieren, mit der sie zum Formular gebracht wurden, ohne dass eine manuelle Feldeingabe oder benutzerdefinierte Skripterstellung erforderlich ist.

Durch diese Verbesserungen werden die Funktionen des Regeleditors für adaptive Forms erheblich erweitert, sodass Entwicklerinnen und Entwickler leistungsstarke Tools erhalten, um dynamischere, interaktivere und intelligentere Formulare zu erstellen. Jede Verbesserung berücksichtigt spezifische Geschäftsanforderungen, erhält dabei aber die Benutzerfreundlichkeit, die den Regeleditor für technische und nicht-technische Benutzende zugänglich macht.

## Zusätzliche Ressourcen

{{see-also-rule-editor}}
