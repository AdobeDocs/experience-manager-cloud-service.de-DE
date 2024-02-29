---
title: Erste Schritte mit dem AEM Forms Edge Delivery Service. Erstellen Sie ein Formular.
description: Handwerkliche perfekte Formen, schnell! ⚡ AEM Forms Edge Delivery doc-basiertes Authoring = Blazing Speed & SEO-freundliche Formulare für glücklichere Benutzer und Suchmaschinen.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 3b24d0cd4099e0b8eb48c977f460b25c168af220
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 1%

---


# Erstellen eines Formulars für eine Edge Delivery Service-Site (EDS)

Im heutigen digitalen Zeitalter ist die Erstellung benutzerfreundlicher Formulare für jedes Unternehmen von entscheidender Bedeutung. Mit AEM Forms Edge Delivery können Sie Formulare mit vertrauten Tools wie Word- oder Google-Dokumenten erstellen.

Diese Formulare senden Daten direkt an eine Microsoft Excel- oder Google Tabellen-Datei, sodass Sie ein dynamisches Ökosystem und robuste APIs von Google Tabellen, Microsoft Excel und Microsoft SharePoint verwenden können, um gesendete Daten einfach zu verarbeiten oder einen bestehenden Geschäftsarbeitsablauf zu initiieren.

AEM Forms Edge Delivery bietet einen Formularblock, mit dem Sie mühelos Formulare erstellen können, um erfasste Daten zu erfassen und zu speichern. Sie können den Formularblock in Ihr AEM EDS-Projekt einbeziehen, um mit der Erstellung eines Formulars zu beginnen. Fangen wir an:


## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie die folgenden Schritte ausgeführt haben:

* Richten Sie das GitHub-Projekt des Edge Delivery Service (EDS) mithilfe AEM Textbausteine ein und klonen Sie das entsprechende GitHub-Repository auf Ihrem lokalen Computer. Siehe [Entwickler-Tutorial](https://www.aem.live/developer/tutorial) für Details. In diesem Dokument wird der lokale Ordner Ihres Edge Delivery Service-Projekts (EDS) als `[EDS Project repository]` .
* Klonen Sie die [Forms Block-Repository](https://github.com/adobe/afb) auf Ihrem lokalen Computer. Es enthält den Code zum Rendern des Formulars auf einer EDS-Webseite. In diesem Dokument wird der lokale Ordner Ihres Forms Block-Repositorys als `[Forms Block repository]`.
* Stellen Sie sicher, dass Sie Zugriff auf Google Tabellen oder Microsoft SharePoint haben. Informationen zum Einrichten von Microsoft SharePoint als Inhaltsquelle finden Sie unter [Verwendung von Sharepoint](https://www.aem.live/docs/setup-customer-sharepoint)



## Formular erstellen

+++ Schritt 1: Fügen Sie den Formularblock zu Ihrem EDS-Projekt (Edge Delivery Service) hinzu.

Mit dem Formularblock können Benutzer Formulare für eine Edge Delivery Service-Site erstellen. Dieser Baustein ist jedoch nicht in der standardmäßigen AEM-Bausteinvorlage enthalten (die zum Erstellen eines Projekts mit dem Edge Delivery Service verwendet wird). So integrieren Sie den Formularblock nahtlos in Ihr Edge Delivery Service-Projekt:

1. **Suchen Sie das Formularblock-Repository:** Zugriff auf [Forms Block-Repository]/blocks auf Ihrem lokalen Computer und kopieren Sie den Ordner `form` Ordner.
1. **Fügen Sie den Formularblock in Ihr EDS-Projekt ein:**
Navigieren Sie zum [EDS-Projekt-Repository]/blocks/ Ordner auf Ihrem lokalen Computer und fügen Sie den Formularordner ein.
1. **Übertragen Sie Änderungen auf GitHub:** Checken Sie den Formularordner und die zugrunde liegenden Dateien in Ihr Edge Delivery Service-Projekt auf GitHub ein.

Nach Abschluss dieser Schritte ist der Formularblock erfolgreich in Ihr Edge Delivery Service(EDS)-Projekt-Repository auf GitHub integriert.


**Beheben von GitHub-Build-Problemen**

Stellen Sie einen reibungslosen GitHub-Build-Prozess sicher, indem Sie potenzielle Probleme beheben:

* **Fehler: Modulpfad auflösen:**
Wenn der Fehler &quot;Pfad zum Modul kann nicht aufgelöst werden &quot;&#39;../../scripts/lib-franklin.js&#39;&quot; auftritt, navigieren Sie zum [EDS-Projekt]/blocks/forms/form.js. Aktualisieren Sie die Importanweisung, indem Sie die Datei &quot;lib-franken.js&quot;durch die Datei &quot;aem.js&quot;ersetzen.

* **Linking-Fehler beheben:**
Sollten Sie auf Linkingfehler stoßen, können Sie diese umgehen. Öffnen Sie die [EDS-Projekt]/package.json und ändern Sie das Skript &quot;lint&quot;von &quot;lint&quot;: &quot;npm run lint:js &amp;&amp; npm run lint:css&quot; in &quot;lint&quot;: &quot;echo &#39;skipping linting for now&#39;&quot;. Speichern Sie die Datei und übertragen Sie die Änderungen auf Ihr GitHub-Projekt.



+++

+++ Schritt 2: Erstellen Sie ein Formular mit Microsoft Excel oder Google Sheet.

Anstatt durch komplexe Prozesse zu navigieren, kann das Erstellen eines Formulars mühelos mithilfe einer Tabelle erfolgen. Zunächst können Sie die Zeilen- und Spaltenüberschriften zu einem Arbeitsblatt hinzufügen, wobei jede Zeile ein Formularfeld darstellt, während jede Spaltenüberschrift die Eigenschaften des entsprechenden Felds definiert.

Betrachten Sie beispielsweise die folgende Tabelle, in der die Zeilen Felder für eine `enquiry` Formular- und Spaltenüberschriften definieren ihre Eigenschaften:

![Abfragetabelle](/help/edge/assets/enquiry-form-spreadsheet.png)

So fahren Sie mit der Formularerstellung fort:

1. Rufen Sie den Ordner AEM Edge-Bereitstellungsprojekt auf Microsoft SharePoint oder Google Drive auf.

1. Erstellen Sie eine Microsoft Excel-Arbeitsmappe oder ein Google-Blatt an einer beliebigen Stelle in Ihrem AEM Edge-Bereitstellungsprojektverzeichnis. Erstellen Sie beispielsweise eine Tabelle mit dem Namen `enquiry` im Projektverzeichnis AEM Edge-Bereitstellung auf Google Drive.

1. Stellen Sie sicher, dass das Blatt für den entsprechenden AEM Benutzer freigegeben ist (z. B. `helix@adobe.com`) [gemäß den für Ihr Projekt angegebenen Konfigurationen](https://www.aem.live/docs/setup-customer-sharepoint). Gewähren Sie der Benutzer Bearbeitungsberechtigung für das Blatt.

1. Öffnen Sie die erstellte Tabelle und benennen Sie das Standardblatt in &quot;Standard freigegeben&quot; um.

   ![Standard-Arbeitsblatt in &quot;shared-default&quot;umbenennen](/help/edge/assets/rename-sheet-to-shared-default.png)

1. Fügen Sie zum Hinzufügen der Formularfelder Zeilen und Spaltenüberschriften in das &quot;shared-default&quot;-Blatt ein. Jede Zeile sollte ein Formularfeld darstellen, wobei Spaltenüberschriften das entsprechende Feld definieren [properties](/help/edge/docs/forms/eds-form-field-properties).

   Für einen schnellen Start sollten Sie den Inhalt der [Abfragetabelle](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0) in Ihre Tabelle ein. Nachdem Sie den Inhalt kopiert haben, speichern Sie das Arbeitsblatt.

   >[!VIDEO](https://video.tv.adobe.com/v/3427468?quality=12&learn=on)


1. Verwendung [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) um eine Vorschau des Blattes anzuzeigen.

   ![Verwenden Sie AEM Sidekick, um eine Vorschau der Tabelle anzuzeigen](/help/edge/assets/preview-form.png)

   Nach der Vorschau und Veröffentlichung werden die Inhalte im JSON-Format in neuen Browserregisterkarten angezeigt. Stellen Sie sicher, dass Sie die Vorschau-URL erfassen, da dies für die Wiedergabe des Formulars im nächsten Abschnitt erforderlich ist. Die URL hat das folgende Format:


   ```JSON
       https://<branch>--<repository>--<owner>.hlx.live/<form>.json
   ```

   * `<branch>` bezieht sich auf die Verzweigung Ihres GitHub-Repository.
   * `<repository>` bezeichnet Ihr GitHub-Repository.
   * `<owner>` bezieht sich auf den Benutzernamen Ihres GitHub-Kontos, das Ihr GitHub-Repository hostet.

   Wenn das Repository Ihres Projekts beispielsweise &quot;Portal&quot;heißt, befindet es sich unter dem Konto &quot;wkndforms&quot;und Sie die Verzweigung &quot;main&quot;verwenden, sieht die URL wie folgt aus:

   `https://main--portal--wkndforms.hlx.page/enquiry.json`


+++

+++ Schritt 3: Anzeigen einer Vorschau des Formulars mit Ihrer Edge Delivery Service-Seite (EDS).


Bis jetzt haben Sie den Formularblock zu Ihrem EDS-Projekt hinzugefügt und die Struktur des Formulars vorbereitet. Nun können Sie eine Vorschau des Formulars anzeigen:

1. **Zugriff auf Ihr Projektverzeichnis:** Öffnen Sie Ihr Microsoft SharePoint- oder Google Drive-Konto und navigieren Sie zu Ihrem AEM Edge Delivery-Projektverzeichnis.

1. **Betten Sie das Formular in ein Dokument ein:** Öffnen Sie eine Dokumentdatei (z. B. eine Indexdatei), um das Formular einzubetten. Alternativ können Sie ein neues Dokument erstellen.

1. **Navigieren Sie zum gewünschten Speicherort:** Wechseln Sie an die gewünschte Stelle im Dokument, an der Sie das Formular hinzufügen möchten.

1. **Fügen Sie den Formularblock hinzu:** Fügen Sie einen Block mit dem Namen &quot;Formular&quot;in die Datei ein, wie unten dargestellt:

   | Formular |
   |---|
   | [https://main—portal—wkndforms.hlx.live/inquiry.json](https://main--portal--wkndforms.hlx.live/enquiry.json) |

   Dieser Block dient als Platzhalter, in den das Formular eingebettet ist. Fügen Sie in der zweiten Zeile des Blocks die Vorschau-URL Ihrer `<form>.json` als Hyperlink.

   >[!IMPORTANT]
   >
   >
   > Stellen Sie sicher, dass die URL als Hyperlink formatiert ist, anstatt als Nur-Text angezeigt zu werden.


1. Verwendung [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) , um eine Vorschau des Dokuments anzuzeigen. Auf der Seite wird nun das Formular angezeigt. Hier ist beispielsweise das Formular, das auf der Variablen [Fragenübersicht](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0):


   [![Beispiel-EDS-Formular](/help/edge/assets/eds-form.png)](https://main--portal--wkndforms.hlx.live/)

   Füllen Sie nun das Formular aus und klicken Sie auf die Senden-Schaltfläche. Es tritt ein Fehler ähnlich dem folgenden auf, da die Tabelle noch nicht für die Annahme der Daten konfiguriert ist.

   ![Fehler bei Formularübermittlung](/help/edge/assets/form-error.png)

+++


## Nächster Schritt

[Tabellenkalkulation vorbereiten](/help/edge/docs/forms/submit-forms.md) , um Daten bei der Formularübermittlung zu akzeptieren.



## Mehr anzeigen

* [Formularfeldeigenschaften](/help/edge/docs/forms/eds-form-field-properties)
* [Erstellen und Anzeigen einer Vorschau eines Formulars](/help/edge/docs/forms/create-forms.md)
* [Formular zum Senden von Daten aktivieren](/help/edge/docs/forms/submit-forms.md)
* [Veröffentlichen eines Formulars auf der Siteseite](/help/edge/docs/forms/publish-eds-forms.md)
* [Hinzufügen von Überprüfungen zu Formularfeldern](/help/edge/docs/forms/validate-forms.md)
* [Designs und Formularstil ändern](/help/edge/docs/forms/style-theme-forms.md)
