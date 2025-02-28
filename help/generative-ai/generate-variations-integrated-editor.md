---
title: Varianten generieren
description: Erfahren Sie mehr über „Varianten generieren“, auf die verschiedene Editoren in AEM as a Cloud Service zugreifen können
feature: Generate Variations
role: Admin, Architect, Developer, User
source-git-commit: 257fcd8df8bf216deec1fe96e64dd38e52f3ebe1
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 34%

---


# Varianten generieren - in AEM-Editoren integriert {#generate-variations-integrated-in-aem-editors}

Wenn Sie nach einer Möglichkeit suchen, Ihre Digitalkanäle zu optimieren und die Inhaltserstellung zu beschleunigen, können Sie die Funktion „Varianten generieren“ verwenden, die in die AEM-Editoren integriert ist.

Varianten generieren nutzt generative künstliche Intelligenz (KI), um Inhaltsvarianten basierend auf Ihren Eingaben zu erstellen. Nachdem Sie Varianten erstellt haben, können Sie den Inhalt auf Ihrer Website verwenden und deren Erfolg außerdem mithilfe der Funktion [Experimente](https://www.aem.live/docs/experimentation) von [Edge Delivery Services](/help/edge/overview.md) messen.

Dies beschleunigt die Geschwindigkeit von Inhalten, indem Markeninhalte in Minutenschnelle erstellt werden. Dies wiederum verbessert die Konvertierung mit neuen Kopiervarianten.

Sie können [Varianten generieren](#access-generate-variations) über die folgenden Editoren zugreifen ([nachdem sie konfiguriert wurden](#access-generate-variations)):

* [innerhalb der Sidekick von AEM Edge Delivery Services; für dokumentbasiertes Authoring](#access-aem-sidekick)
* [im universellen Editor](#access-aem-universal-editor)
* [im Inhaltsfragmenteditor](#access-aem-content-fragment-editor)

>[!IMPORTANT]
>
>Auf dieser Seite wird die dokumentbasierte Bearbeitung als Grundlage für Beispiele verwendet, die Prinzipien gelten jedoch für die anderen Editoren.

>[!NOTE]
>
>In allen Fällen müssen Sie zur Verwendung von „Varianten generieren“ sicherstellen, dass die [Voraussetzungen für den Zugriff](#access-prerequisites) erfüllt sind.

>[!NOTE]
>
>Auf die eigenständige Version von [Varianten generieren“ kann weiterhin direkt zugegriffen ](/help/generative-ai/generate-variations.md).

Sie haben dann folgende Möglichkeiten:

* [Wählen Sie den Inhalt aus, mit dem Sie arbeiten möchten](#select-the-content) - aus vorhandenen Inhaltsblöcken
   * Der ausgewählte Block steuert, was angezeigt wird und welche Aktionen verfügbar sind
* [Beschreiben Sie die gewünschten Änderungen](#describe-the-changes-you-want)
* [Generieren Sie Varianten Ihrer Inhalte](#generate-copy) und [führen Sie dann bei Bedarf weitere Aktionen durch](#take-further-action-on-a-variation)
* [Auswahl und Verwendung einer Variante](#use-a-generated-variation)
* Überprüfen des [Verlaufs](#history)
* Anzeigen Ihrer [Favoriten](#favorites)

## Rechtlicher Hinweis und Nutzungshinweis {#legal-usage-note}

<!--
Generative AI and Generate Variations for AEM are powerful tools – but **you** are responsible for use of the output.

Your inputs to the service should be tied to a context. This context can be your branding materials, website content, data, schemas for such data, templates, or other trusted documents.

You must evaluate the accuracy of any output as appropriate to your use case.

Before using Generate Variations you are recommended to read the [Adobe Experience Cloud Generative AI User Guidelines](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html).
-->

Die [Verwendung von „Varianten generieren“](#generative-action-usage) ist an den Verbrauch generativer Aktionen gebunden.

## Überblick {#overview}

Wenn Sie Varianten erzeugen öffnen, die in einen Editor integriert sind, sehen Sie die Erweiterung als unverankertes Bedienfeld mit drei Registerkarten.

![Generieren von Varianten - Übersicht über die dokumentbasierte Bearbeitung](assets/generate-variations-doc-based-overview.png)

* Der Editor:
   * Zeigt den Inhaltsfluss im Editor an.
   * Hier können Sie einen Inhaltsblock zur Verwendung in „Varianten **&quot;**.
* **Varianten generieren**:
   * ist ein schwebendes Bedienfeld mit drei Registerkarten, die beliebig verschoben werden können
   * [Generieren](#get-started-with-generate-variations):
      * Zeigt den [ausgewählten Inhalt](#select-the-content) an.
      * Bietet **(**) für Änderungen.
      * Ermöglicht es Ihnen[ die gewünschten Änderungen zu ](#describe-the-changes-you-want).
      * Ermöglicht das [ (Erzeugen](#generate-copy) neuer Varianten.
      * Zeigt die erzeugten Varianten an. <!--, together with their [brand score](#the-brand-score).-->
      * [Weitere Aktionen für eine Variante ](#take-further-action-on-a-variation).
      * [Verwenden Sie eine generierte Variante](#use-a-generated-variation).
   * [Verlauf](#history):
      * Zeigt die jüngste Geschichte von Generationen an.
   * [Favoriten](#favorites):
      * Zeigt Ergebnisse früherer Generationen an, die Sie als Favoriten markiert haben.
   * **Adobe Generative AI-Bedingungen**: Links zu [Adobe Experience Cloud Generative AI-](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html).

## Erste Schritte mit dem Generieren von Varianten {#get-started-with-generate-variations}

Die Benutzeroberfläche führt Sie durch den Prozess der Inhaltserstellung. Nach dem Öffnen der Benutzeroberfläche besteht der erste Schritt darin, den Inhaltsblock auszuwählen, den Sie verwenden möchten.

### Inhalt auswählen {#select-the-content}

Wählen Sie aus dem Hauptinhaltsfluss des Editors den Inhalt aus, für den Sie Varianten generieren möchten. Diese **Auswahl** wird auf der Registerkarte **Generieren** angezeigt.

### Beschreiben Sie die gewünschten Änderungen {#describe-the-changes-you-want}

Um Varianten des Inhalts zu erzeugen, müssen Sie die gewünschten Änderungen beschreiben. Sie können entweder eine der **Vorschläge** auswählen oder Ihre eigene Beschreibung angeben.

Sie können auch &quot;**&quot; angeben** um mehr Kontext bereitzustellen:

* **Referenzieren einer Web-Seite**
Geben Sie eine URL für mehr Kontext an.
* **Inhaltsübersicht hochladen**
Aktualisieren Sie eine `.docx` Datei mit Details zur Inhaltsbeschreibung (10 MB oder weniger).

### Generieren einer Kopie {#generate-copy}

Nachdem Sie die gewünschten Änderungen beschrieben haben, klicken Sie auf **Generieren**, um die Antworten von generativer KI anzuzeigen.

![Varianten generieren - Dokumentbasierte Kopie generieren](assets/generate-variations-doc-based-generate-copy.png)

<!--
### The Brand Score {#the-brand-score}

The brand score shows you how on-brand the generated variation is.
-->

### Weitere Maßnahmen bei einer Variante {#take-further-action-on-a-variation}

Wenn Sie eine einzelne Variante auswählen, können Sie die folgenden Aktionen verwenden:

* **Bearbeiten**
   * Sie können den Text der generierten Variante bearbeiten.

      * Ihre Aktualisierungen können in der Vorschau auf der Web-Seite angezeigt werden.

   * Speichern Sie Ihre Änderungen zur späteren Verwendung.
* **Favorit**
   * Markieren Sie diese Variante zur zukünftigen Verwendung.
   * Sobald es gekennzeichnet ist, wird es auf der Registerkarte [Favoriten](#favorites) angezeigt.
* **KI-Begründung**
   * Um für zusätzliche Transparenz zu sorgen, wird hier kurz beschrieben, warum generative KI diese bestimmte Variante erzeugt hat.

### Verwenden einer generierten Variante {#use-a-generated-variation}

Um den mit generativer KI generierten Inhalt zu verwenden, müssen Sie zunächst „In CSV **&quot;**.

Nach dem Export können Sie den Inhalt an einer anderen Stelle verwenden, z. B. beim Erstellen von Inhalten für Ihre Website. Sie können auch ein [Experiment](https://www.aem.live/docs/experimentation) durchführen.

>[!NOTE]
>
>Wenn über den universellen Editor von AEM [oder den ](#access-aem-universal-editor)-Editor von [AEM](#access-aem-content-fragment-editor) zugegriffen wird, wird der ausgewählte generierte Inhalt automatisch in AEM gespeichert.

## Verlauf {#history}

Auf dieser Registerkarte werden Ihre vergangenen Aktivitäten wie nach dem Klicken auf **Generieren** angezeigt. Ein **History**-Eintrag wird hinzugefügt.

Wenn Sie zu einem späteren Zeitpunkt denselben Inhalt im Hauptfluss auswählen und die Registerkarte **Verlauf** öffnen, werden alle für diesen Block generierten Varianten angezeigt.

## Favoriten {#favorites}

Nach der Überprüfung des Inhalts können Sie ausgewählte Varianten als Favoriten speichern.

Nach dem Speichern werden sie unter &quot;**&quot;**. Favoriten werden beibehalten (bis Sie **Favoriten** oder den Browser-Cache löschen).

* Sie können **Bearbeiten**, **Unfavorisiert** oder die **KI-Begründung** für einen Eintrag anzeigen.
* Sobald eine Variante ausgewählt ist, können Sie auch **In CSV exportieren**.

## Nutzung generischer Aktionen {#generative-action-usage}

Die Verwaltung der Nutzung hängt von der durchgeführten Aktion ab:

* Varianten generieren

  Jede Generierung einer Kopiervariante entspricht einer generativen Aktion. Als Kundin oder Kunde verfügen Sie über eine bestimmte Anzahl von generativen Aktionen, die mit Ihrer AEM-Lizenz einhergehen. Sobald das Basiskontingent aufgebraucht ist, können Sie zusätzliche Aktionen erwerben.

  >[!NOTE]
  >
  >Weitere Informationen zum Basiskontingent finden Sie unter [Adobe Experience Manager: Cloud Service | Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/aem-cloud-service.html). Wenn Sie weitere generative Aktionen erwerben möchten, können Sie sich an Ihr Accountteam wenden.

## Zugriff auf „Varianten generieren“ {#access-generate-variations}

Sobald die Voraussetzungen erfüllt sind, können Sie über AEM as a Cloud Service oder den Sidekick von Edge Delivery Services auf „Varianten generieren“ zugreifen.

### Voraussetzungen für den Zugriff {#access-prerequisites}

Um „Varianten generieren“ zu verwenden, müssen Sie sicherstellen, dass die Voraussetzungen erfüllt sind:

* [Zugriff auf Experience Manager as a Cloud Service mit Edge Delivery Services](#access-to-aemaacs-with-edge-delivery-services)

#### Zugriff auf Experience Manager as a Cloud Service mit Edge Delivery Services{#access-to-aemaacs-with-edge-delivery-services}

Benutzende, die Zugriff auf die Funktion „Varianten generieren“ benötigen, müssen über die Berechtigung für eine Experience Manager as a Cloud Service-Umgebung mit Edge Delivery Services verfügen.

>[!NOTE]
>
>Wenn Ihr Vertrag für AEM Sites as a Cloud Service keine Edge Delivery Services umfasst, müssen Sie einen neuen Vertrag unterzeichnen, um Zugriff zu erhalten.
>
>Wenden Sie sich an Ihr Accountteam, um zu besprechen, wie Sie zu AEM Sites as a Cloud Service mit Edge Delivery Services wechseln können.

Um bestimmten Benutzenden Zugriff zu gewähren, weisen Sie ihr Benutzerkonto dem jeweiligen Produktprofil zu. Weitere Informationen finden Sie unter [Zuweisen von AEM-Produktprofilen](/help/journey-onboarding/assign-profiles-cloud-manager.md).

### Zugriff über AEM Sidekick für die dokumentbasierte Bearbeitung {#access-aem-sidekick}

Der Zugriff über die AEM Sidekick wird für die [dokumentbasierte Bearbeitung“ ](/help/edge/wysiwyg-authoring/authoring.md).

Bevor Sie über den Sidekick (von Edge Delivery Services) auf „Varianten generieren“ zugreifen können, müssen bestimmte Konfigurationen vorgenommen werden.

>[!NOTE]
>
>Informationen zum Installieren und Konfigurieren des Sidekicks finden Sie im Dokument [Installieren des AEM Sidekicks](https://www.aem.live/docs/sidekick-extension).

Um die Funktion „Varianten in Sidekick generieren“ (von Edge Delivery Services) zu verwenden, schließen Sie die folgenden Konfigurationen in Ihre Edge Delivery Services-Projekte ein.

1. Aktivieren Sie Ihre App in:

   * `tools/sidekick/config.json`

   Diese muss mit Ihrer vorhandenen Konfiguration zusammengeführt und dann bereitgestellt werden.

   Zum Beispiel:

   ```prompt
   {
     "plugins": [
       {
         "id": "aem-genai-variations",
         "titleI18n": {
           "en": "Generate with AI"
         },
         "environments": [
           "preview"
         ],
         "includePaths": [
           "**.docx**"
         ],
         "event": "aem-genai-variations-sidekick"
       }
     ]
   }
   ```

1. Erstellen:

   * `/tools/sidekick/aem-genai-variations.js`

   Sie müssen diese Datei mit folgendem Inhalt erstellen:

   ```prompt
   (function () {
     let isAEMGenAIVariationsAppLoaded = false;
     function loadAEMGenAIVariationsApp() {
       const script = document.createElement('script');
       script.src = 'https://experience.adobe.com/solutions/aem-sites-genai-aem-genai-variations-mfe/static-assets/resources/sidekick/client.js?source=plugin';
       script.onload = function () {
         isAEMGenAIVariationsAppLoaded = true;
       };
       script.onerror = function () {
         console.error('Error loading AEMGenAIVariationsApp.');
       };
       document.head.appendChild(script);
     }
   
     function handlePluginButtonClick() {
       if (!isAEMGenAIVariationsAppLoaded) {
         loadAEMGenAIVariationsApp();
       }
     }
   
     // The code snippet for the Sidekick V1 extension, https://chromewebstore.google.com/detail/aem-sidekick/ccfggkjabjahcjoljmgmklhpaccedipo?hl=en
     const sidekick = document.querySelector('helix-sidekick');
     if (sidekick) {
       // sidekick already loaded
       sidekick.addEventListener('custom:aem-genai-variations-sidekick', handlePluginButtonClick);
     } else {
       // wait for sidekick to be loaded
       document.addEventListener('sidekick-ready', () => {
         document.querySelector('helix-sidekick')
           .addEventListener('custom:aem-genai-variations-sidekick', handlePluginButtonClick);
       }, { once: true });
     }
   
     // The code snippet for the Sidekick V2 extension, https://chromewebstore.google.com/detail/aem-sidekick/igkmdomcgoebiipaifhmpfjhbjccggml?hl=en
     const sidekickV2 = document.querySelector('aem-sidekick');
     if (sidekickV2) {
       // sidekick already loaded
       sidekickV2.addEventListener('custom:aem-genai-variations-sidekick', handlePluginButtonClick);
     } else {
       // wait for sidekick to be loaded
       document.addEventListener('sidekick-ready', () => {
         document.querySelector('aem-sidekick')
           .addEventListener('custom:aem-genai-variations-sidekick', handlePluginButtonClick);
       }, { once: true });
     }
   }());
   ```

1. Aktualisieren:

   * `/scripts/scripts.js`

   Dies muss aktualisiert werden, um die folgende Anweisung in die Funktion `loadLazy()`einzuschließen:

   ```prompt
     import('../tools/sidekick/aem-genai-variations.js');
   ```

   Dadurch wird sichergestellt, dass `/tools/sidekick/aem-genai-variations.js` im Rahmen des Lazy-Loading-Vorgangs geladen wird.

   ![Varianten generieren - Lazy Loader](assets/generate-variations-sidekick-lazyloader.png)

1. Anschließend müssen Sie möglicherweise sicherstellen, dass Benutzende Zugriff auf [Experience Manager as a Cloud Service mit Edge Delivery Services](#access-to-aemaacs-with-edge-delivery-services) haben.

1. Sie können dann auf die Funktion zugreifen, indem Sie **Mit KI generieren** in der Symbolleiste der Sidekick auswählen:

   ![Varianten generieren – Zugriff über AEM-Sidekick](assets/generate-variations-doc-based-sidekick.png)

### Zugriff über den universellen Editor von AEM {#access-aem-universal-editor}

Der Zugriff über den universellen Editor {](/help/sites-cloud/authoring/universal-editor/authoring.md)} von AEM wird als Erweiterung implementiert. [ Weitere Informationen finden Sie unter [Extension Manager ](https://developer.adobe.com/uix/docs/extension-manager/) AEM Experience Manager.

### Zugriff über den AEM-Inhaltsfragment-Editor {#access-aem-content-fragment-editor}

Der Zugriff über den [AEM](/help/sites-cloud/administering/content-fragments/authoring.md#generate-variations-ai)Inhaltsfragment-Editor wird als Erweiterung implementiert. Weitere Informationen finden Sie unter [Extension Manager ](https://developer.adobe.com/uix/docs/extension-manager/) AEM Experience Manager.

## Weiterführende Informationen {#further-information}

Weitere Informationen finden Sie auch unter:

* [GenAI – Generieren von Varianten auf GitHub](https://github.com/adobe/aem-genai-assistant#setting-up-aem-genai-assistant)
* [Experimente mit Edge Delivery Services](https://www.aem.live/docs/experimentation)

## Versionsverlauf {#release-history}

Weitere Informationen zu aktuellen und früheren Versionen finden Sie in den [Versionshinweisen für „Varianten generieren“](/help/generative-ai/release-notes-generate-variations.md)
