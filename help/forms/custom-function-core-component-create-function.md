---
title: Erstellen und Hinzufügen von benutzerdefinierten Funktionen in einem adaptiven Formular
description: AEM Forms unterstützt benutzerdefinierte Funktionen, mit denen Benutzer eigene Funktionen im Regeleditor erstellen und verwenden können.
keywords: Im Regeleditor können Sie eine benutzerdefinierte Funktion hinzufügen, eine benutzerdefinierte Funktion verwenden, eine benutzerdefinierte Funktion erstellen oder eine benutzerdefinierte Funktion verwenden.
feature: Adaptive Forms, Core Components
role: User, Developer
exl-id: e7ab4233-2e91-45c6-9377-0c9204d03ee9
source-git-commit: 249c60c6b4a888b8d32bbb6bebf159c972f82f94
workflow-type: tm+mt
source-wordcount: '1340'
ht-degree: 56%

---

# Erstellen einer benutzerdefinierten Funktion für ein auf Kernkomponenten basierendes adaptives Formular

Adaptive Forms auf der Basis von Kernkomponenten bieten dynamische Benutzererlebnisse, indem Inhalt und Verhalten basierend auf der Benutzereingabe angepasst werden. Benutzerdefinierte Funktionen ermöglichen es Entwicklern, die Funktionalität zu erweitern und sicherzustellen, dass Formulare bestimmte Anforderungen erfüllen können. Durch die Integration benutzerdefinierter Funktionen können Entwickler komplexe Logik implementieren, Prozesse automatisieren und einzigartige Interaktionen einführen, die spezifischen Geschäftsanforderungen oder Benutzererwartungen entsprechen. Dadurch wird sichergestellt, dass sich die Formulare nicht nur an unterschiedliche Bedingungen anpassen, sondern auch eine präzisere und effektivere Lösung für verschiedene Anwendungsfälle bieten.
Dieser Artikel führt Sie durch die Schritte zum Erstellen benutzerdefinierter Funktionen für adaptive Forms mithilfe von Kernkomponenten.

## Überlegungen

* Der `parameter type` und der `return type` unterstützen `None` nicht.

* Folgende Funktionen werden in der Liste der benutzerdefinierten Funktionen nicht unterstützt:
   * Generator-Funktionen
   * Async/Await-Funktionen
   * Methodendefinitionen
   * Klassenmethoden
   * Standardparameter
   * Rest-Parameter:

## Voraussetzungen zum Erstellen einer benutzerdefinierten Funktion.

Bevor Sie mit dem Hinzufügen einer benutzerdefinierten Funktion zu Ihrem adaptiven Forms beginnen, stellen Sie Folgendes sicher:

**Software:**

* **Nur-Text-Editor (IDE)**: Zwar kann jeder einfache Nur-Text-Editor verwendet werden, aber eine integrierte Entwicklungsumgebung (IDE) wie Microsoft Visual Studio Code bietet erweiterte Funktionen für eine einfachere Bearbeitung.

* **Git:**: Dieses Versionskontrollsystem ist für die Verwaltung von Code-Änderungen erforderlich. Wenn Sie nicht über das Programm verfügen, laden Sie es von https://git-scm.com herunter.


## Erstellen einer benutzerdefinierten Funktion

Erstellen Sie eine Client-Bibliothek, um benutzerdefinierte Funktionen im Regeleditor aufzurufen. Weitere Informationen finden Sie unter [Verwenden Client-seitiger Bibliotheken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html?lang=de#developing).

Die Schritte zum Erstellen benutzerdefinierter Funktionen sind die Folgenden:
1. [Erstellen einer Client-Bibliothek](#create-client-library)
1. [Hinzufügen einer Client-Bibliothek zu einem adaptiven Formular](#use-custom-function)

### Erstellen einer Client-Bibliothek {#create-client-library}

Sie können benutzerdefinierte Funktionen hinzufügen, indem Sie eine Client-Bibliothek hinzufügen. Um eine Client-Bibliothek zu erstellen, führen Sie die folgenden Schritte aus:

**Repository klonen**

Klonen Sie Ihr [AEM Forms as a Cloud Service-Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git):

1. Öffnen Sie die Befehlszeile oder ein Terminal-Fenster.

1. Navigieren Sie zum gewünschten Speicherort auf Ihrem Computer, auf dem Sie das Repository speichern möchten.

1. Führen Sie den folgenden Befehl aus, um das Repository zu klonen:

   `git clone [Git Repository URL]`

Mit diesem Befehl wird das Repository heruntergeladen und ein lokaler Ordner des geklonten Repositorys auf Ihrem Computer erstellt. In diesem Handbuch wird dieser Ordner als das AEMaaCS-Projektverzeichnis ] bezeichnet.[

**Hinzufügen eines Client-Bibliotheksordners**

Gehen Sie wie folgt vor, um den neuen Client-Bibliotheksordner zum AEMaaCS-Projektverzeichnis ] hinzuzufügen:[

1. Öffnen Sie das Verzeichnis [AEMaaCS-Projekt] in einem Editor.

   ![Ordnerstruktur der benutzerdefinierten Funktion](/help/forms/assets/custom-library-folder-structure.png)

1. Suchen Sie `ui.apps`.
1. Fügen Sie einen neuen Ordner hinzu. Erstellen Sie beispielsweise einen Ordner mit dem Namen `experience-league`.
1. Navigieren Sie zum Ordner `/experience-league/` und fügen Sie einen `ClientLibraryFolder` hinzu. Erstellen Sie beispielsweise einen Client-Bibliotheksordner mit dem Namen `customclientlibs`.

   `Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/`

**Hinzufügen von Dateien und Ordnern zum Client-Bibliotheksordner**

Fügen Sie dem hinzugefügten Client-Bibliotheksordner Folgendes hinzu:

* .content.xml-Datei
* js.txt-Datei
* js-Ordner

`Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/experience-league/customclientlibs/`

1. Fügen Sie in `.content.xml` die folgenden Code-Zeilen hinzu:

   ```javascript
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="cq:ClientLibraryFolder"
   categories="[customfunctionscategory]"/>
   ```

   >[!NOTE]
   >
   > Sie können für die Eigenschaften `client library folder` und `categories` beliebige Namen auswählen.

1. Fügen Sie in `js.txt` die folgenden Code-Zeilen hinzu:

   ```javascript
         #base=js
       function.js
   ```
1. Fügen Sie im Ordner `js` die JavaScript-Datei, die die benutzerdefinierten Funktionen enthält, als `function.js` hinzu:

   ```javascript
    /**
        * Calculates Age
        * @name calculateAge
        * @param {object} field
        * @return {string} 
    */
   
    function calculateAge(field) {
    var dob = new Date(field);
    var now = new Date();
   
    var age = now.getFullYear() - dob.getFullYear();
    var monthDiff = now.getMonth() - dob.getMonth();
   
    if (monthDiff < 0 || (monthDiff === 0 && now.getDate() < dob.getDate())) {
    age--;
    }
   
    return age;
    }
   ```
1. Speichern Sie die Dateien.

![Ordnerstruktur der benutzerdefinierten Funktionen](/help/forms/assets/custom-function-added-files.png)

**Schließen Sie den neuen Ordner in filter.xml ein**:

1. Navigieren Sie zur Datei `/ui.apps/src/main/content/META-INF/vault/filter.xml` in Ihrem [AEMaaCS-Projektverzeichnis].

1. Öffnen Sie die Datei und fügen Sie die folgende Zeile am Ende ein:

   `<filter root="/apps/experience-league" />`
1. Speichern Sie die Datei.

![Benutzerdefinierte Funktion Filter XML](/help/forms/assets/custom-function-filterxml.png)

**Stellen Sie den neu erstellten Client-Bibliotheksordner in Ihrer AEM-Umgebung bereit**

Stellen Sie das [AEMaaCS Projektverzeichnis] von AEM as a Cloud Service in Ihrer Cloud Service-Umgebung bereit. So stellen Sie es in Ihrer Cloud Service-Umgebung bereit:

1. Übergeben Sie die Änderungen

   1. Fügen Sie die Änderungen mit den folgenden Befehlen hinzu, übertragen Sie sie und pushen Sie sie in das Repository:

   ```javascript
       git add .
       git commit -a -m "Adding custom functions"
       git push
   ```

1. Stellen Sie den aktualisierten Code bereit:

   1. Trigger einer Bereitstellung Ihres Codes über die vorhandene Vollstapelpipeline. Dadurch wird der aktualisierte Code automatisch erstellt und bereitgestellt.

Wenn Sie noch keine Pipeline eingerichtet haben, lesen Sie das Handbuch zur [Einrichtung einer Pipeline für AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline).

Sobald die Pipeline erfolgreich ausgeführt wurde, ist die benutzerdefinierte Funktion, die in der Client-Bibliothek hinzugefügt wurde, im Regeleditor für adaptive Formulare [verfügbar.](/help/forms/rule-editor-core-components.md)

### Hinzufügen einer Client-Bibliothek zu einem adaptiven Formular{#use-custom-function}

Nachdem Sie Ihre Client-Bibliothek in Ihrer Forms CS-Umgebung bereitgestellt haben, verwenden Sie die zugehörigen Funktionen in Ihrem adaptiven Formular. Hinzufügen der Client-Bibliothek zu einem adaptiven Formular

1. Öffnen Sie das Formular im Bearbeitungsmodus. Um ein Formular im Bearbeitungsmodus zu öffnen, wählen Sie ein Formular aus und wählen Sie dann **[!UICONTROL Bearbeiten]**.
1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für adaptive Formulare“ wird geöffnet.
1. Öffnen Sie die Registerkarte **[!UICONTROL Einfach]** und wählen Sie den Namen der **[!UICONTROL Client-Bibliothekskategorie]** aus der Dropdown-Liste aus (in diesem Fall `customfunctionscategory`).

   ![Hinzufügen der benutzerdefinierten Funktion zur Client-Bibliothek](/help/forms/assets/clientlib-custom-function.png)

   >[!NOTE]
   >
   > Es können mehrere Kategorien hinzugefügt werden, indem eine kommagetrennte Liste innerhalb des Felds **[!UICONTROL Kategorie der Client-Bibliothek]** angegeben wird.

1. Klicken Sie auf **[!UICONTROL Fertig]**.

Sie können die benutzerdefinierte Funktion im Regeleditor [eines adaptiven Formulars](/help/forms/rule-editor-core-components.md) mit den Anmerkungen in [JavaScript](##js-annotations) verwenden.

## Verwenden einer benutzerdefinierten Funktion in einem adaptiven Formular

In einem adaptiven Formular können Sie [benutzerdefinierte Funktionen im Regeleditor](/help/forms/rule-editor-core-components.md) verwenden. Fügen Sie der JavaScript-Datei (`Function.js`) den folgenden Code hinzu, um das Alter basierend auf dem Geburtsdatum (JJJ-MM-TT) zu berechnen. Erstellen Sie eine benutzerdefinierte Funktion als `calculateAge()`, die das Geburtsdatum als Eingabe annimmt und das Alter zurückgibt:

```javascript
    /**
        * Calculates Age
        * @name calculateAge
        * @param {object} field
        * @return {string} 
    */

    function calculateAge(field) {
    var dob = new Date(field);
    var now = new Date();

    var age = now.getFullYear() - dob.getFullYear();
    var monthDiff = now.getMonth() - dob.getMonth();

    if (monthDiff < 0 || (monthDiff === 0 && now.getDate() < dob.getDate())) {
    age--;
    }

    return age;
    }
```

Wenn Benutzende im obigen Beispiel das Geburtsdatum im Format JJJJ-MM-TT eingeben, wird die benutzerdefinierte Funktion `calculateAge` aufgerufen und das Alter zurückgegeben.

![Benutzerdefinierte Funktion &quot;Seite berechnen&quot;im Regeleditor](/help/forms/assets/custom-function-calculate-age.png)

Sehen wir uns das Formular in der Vorschau an, um zu sehen, wie die benutzerdefinierten Funktionen über den Regeleditor implementiert werden:

![Benutzerdefinierte Funktion &quot;Seite berechnen&quot;in der Formularvorschau des Regeleditors](/help/forms/assets/custom-function-age-calculate-form.png)

>[!NOTE]
>
> Sie können auf den folgenden Ordner [Benutzerdefinierte Funktion](/help/forms/assets//customfunctions.zip) verweisen. Laden Sie diesen Ordner herunter und installieren Sie ihn mithilfe von [Package Manager](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager) in Ihrer AEM-Instanz.

## Funktionen von benutzerdefinierten Funktionen

Benutzerdefinierte Funktionen in AEM Formularen bieten eine zuverlässige Lösung zum Erweitern und Personalisieren der Funktionalität Ihrer Formulare. Sie können die benutzerdefinierten Funktionen verwenden, um die spezifischen Anforderungen Ihres Unternehmens zu erfüllen.

Diese Funktionen unterstützen verschiedene Funktionen, einschließlich der Arbeit mit bestimmten Feldern, der Verwendung globaler Felder und asynchroner Vorgänge sowie der Integration von Zwischenspeicherungsmechanismen. Diese Flexibilität stellt sicher, dass Formulare sich an komplexe Anforderungen anpassen und ein effizientes, benutzerspezifisches Erlebnis bieten können. Mithilfe dieser erweiterten Funktionen können Sie die Interaktionen mit Formularen verbessern und die Leistung optimieren, sodass Ihre AEM-Formulare funktionaler und reaktionsfähiger werden.

Im Folgenden werden die Merkmale von benutzerdefinierten Funktionen vorgestellt.

### Asynchrone Unterstützung in benutzerdefinierten Funktionen {#support-of-async-functions}

Sie können asynchrone Funktionen im Regeleditor mit benutzerdefinierten Funktionen implementieren. Eine Anleitung dazu finden Sie im Artikel [Verwenden asynchroner Funktionen in einem adaptiven Formular](/help/forms/using-async-funct-in-rule-editor.md).

### Felder und globale Objekte unterstützen benutzerdefinierte Funktionen {#support-field-and-global-objects}

Feldobjekte beziehen sich auf die einzelnen Komponenten oder Elemente in einem Formular, z. B. Textfelder und Kontrollkästchen. Das Globals-Objekt enthält schreibgeschützte Variablen wie Formularinstanz, Zielfeldinstanz und Methoden zum Durchführen von Formularänderungen in benutzerdefinierten Funktionen.

>[!NOTE]
>
> Der `param {scope} globals` muss der letzte Parameter sein und wird nicht im Regeleditor eines adaptiven Formulars angezeigt.

Weitere Informationen zu Scope-Objekten finden Sie im Artikel [Scope-Objekte in benutzerdefinierten Funktionen](/help/forms/custom-function-core-component-scope-function.md) .

### Caching-Unterstützung in benutzerdefinierten Funktionen

Adaptive Formulare nutzen Caching für benutzerdefinierte Funktionen, um die Antwortzeit beim Abrufen der Liste der benutzerdefinierten Funktionen im Regeleditor zu verbessern. In der Datei `error.log` wird eine Meldung `Fetched following custom functions list from cache` angezeigt.

![benutzerdefinierte Funktion mit Cache-Unterstützung](/help/forms/assets/custom-function-cache-error.png)

Wenn die benutzerdefinierten Funktionen geändert werden, wird das Caching invalidiert, und es wird analysiert.

## Fehlerbehebung

* Wenn die JavaScript-Datei mit dem Code für benutzerdefinierte Funktionen einen Fehler enthält, werden die benutzerdefinierten Funktionen nicht im Regeleditor eines adaptiven Formulars aufgeführt. Um die Liste der benutzerdefinierten Funktionen zu überprüfen, können Sie für den Fehler zur Datei `error.log` navigieren. Im Fall eines Fehlers wird die Liste der benutzerdefinierten Funktionen leer angezeigt:

  ![Fehlerprotokolldatei](/help/forms/assets/custom-function-list-error-file.png)

  Wenn kein Fehler auftritt, wird die benutzerdefinierte Funktion abgerufen und in der Datei `error.log` angezeigt. In der Datei `error.log` wird eine Meldung mit dem Wert `Fetched following custom functions list` angezeigt:

  ![Fehlerprotokolldatei mit ordnungsgemäßer benutzerdefinierter Funktion](/help/forms/assets/custom-function-list-fetched-in-error.png)

## Nächster Schritt

Sehen wir uns nun verschiedene [Beispiele für benutzerdefinierte Funktionen für ein adaptives Formular an, das auf Kernkomponenten basiert](/help/forms/custom-function-core-components-use-cases.md).

## Siehe auch

{{see-also-rule-editor}}
