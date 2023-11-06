---
title: Wie füge ich einem adaptiven Formular Unterstützung für neue Gebietsschemata hinzu, basierend auf Kernkomponenten?
description: Erfahren Sie, wie Sie neue Gebietsschemata für ein adaptives Formular hinzufügen.
exl-id: bc06542b-84c8-4c6a-a305-effbd16d5630
source-git-commit: 57e421a865b664c0adb7af93b33bd4b6b32049ab
workflow-type: tm+mt
source-wordcount: '1328'
ht-degree: 23%

---

# Gebietsschema für adaptive Forms auf Basis von Kernkomponenten hinzufügen {#supporting-new-locales-for-adaptive-forms-localization}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| Foundation-Komponenten | [Hier klicken](supporting-new-language-localization.md) |
| Kernkomponenten | Dieser Artikel |

AEM Forms bietet vorkonfiguriert Unterstützung für die Gebietsschemata Englisch (en), Spanisch (es), Französisch (fr), Italienisch (it), Deutsch (de), Japanisch (ja), brasilianisches Portugiesisch (pt-BR), Chinesisch (zh-CN), Chinesisch – Taiwan (zh-TW) und Koreanisch (ko-KR). Sie können auch Unterstützung für weitere Gebietsschemata hinzufügen, wie Hindi (hi_IN).

## Wie wird das Gebietsschema für ein adaptives Formular ausgewählt?

Bevor Sie mit dem Hinzufügen eines Gebietsschemas für adaptive Forms beginnen, sollten Sie wissen, wie ein Gebietsschema für ein adaptives Formular ausgewählt wird. Es gibt zwei Methoden zum Identifizieren und Auswählen des Gebietsschemas für ein adaptives Formular bei der Wiedergabe:

* **Verwenden der `locale` Auswahl in der URL**: Beim Rendern eines adaptiven Formulars gibt das System das angeforderte Gebietsschema durch Überprüfen der [locale] -Selektor in der URL des adaptiven Formulars. Die URL hat folgendes Format: http:/[AEM Forms-Server-URL]/content/forms/af/[afName].[locale].html?wcmmode=disabled. Die Verwendung der [locale] Auswahl ermöglicht die Zwischenspeicherung des adaptiven Formulars. Beispielsweise die URL `www.example.com/content/forms/af/contact-us.hi.html?wcmmmode=disabled` gibt das Formular in Hindi-Sprache aus.

* Abrufen der Parameter in der unten aufgeführten Reihenfolge:

   * **Verwenden der `afAcceptLang`Anforderungsparameter**: Um das Browsergebietsschema des Benutzers zu überschreiben, können Sie den Anforderungsparameter afAcceptLang übergeben. Beispiel: die `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ca-fr` URL erzwingt vom AEM Forms-Server die Wiedergabe des Formulars in kanadischem französischem Gebietsschema.

   * **Verwenden des Browser-Gebietsschemas (Accept-Language-Header)**: Das System berücksichtigt auch das Browser-Gebietsschema des Benutzers, das in der Anfrage mit der `Accept-Language` -Kopfzeile.

  Wenn eine Client-Bibliothek (der Prozess zum Erstellen und Verwenden der Bibliothek wird später in diesem Artikel erläutert) für das angeforderte Gebietsschema nicht verfügbar ist, überprüft das System, ob eine Client-Bibliothek für den Sprachcode im Gebietsschema vorhanden ist. Wenn das angeforderte Gebietsschema beispielsweise `en_ZA` (Südafrikanisches Englisch) und es gibt keine Client-Bibliothek für `en_ZA`verwendet das adaptive Formular die Client-Bibliothek für en (Englisch), sofern verfügbar. Wenn keines von beiden gefunden wird, greift das adaptive Formular auf das Wörterbuch für `en` Gebietsschema.

  Sobald das Gebietsschema identifiziert wurde, wählt das adaptive Formular das entsprechende formularspezifische Wörterbuch aus. Wenn das Wörterbuch für das angeforderte Gebietsschema nicht gefunden wird, wird standardmäßig das Wörterbuch in der Sprache verwendet, in der das adaptive Formular verfasst wurde.

  Wenn keine Sprachinformationen verfügbar sind, wird das adaptive Formular in der Originalsprache angezeigt, die bei der Entwicklung des Formulars verwendet wird


## Voraussetzungen {#prerequistes}

Bevor Sie mit dem Hinzufügen eines Gebietsschemas beginnen:

* Installieren Sie einen Nur-Text-Editor (IDE) für eine einfachere Bearbeitung. Die Beispiele in diesem Dokument basieren auf [Microsoft® Visual Studio Code](https://code.visualstudio.com/download).
* Installieren Sie eine Version von [Git](https://git-scm.com), falls auf Ihrem Computer nicht verfügbar.
* Klonen Sie die [Adaptive Forms-Kernkomponenten](https://github.com/adobe/aem-core-forms-components) Repository. So klonen Sie das Repository:
   1. Öffnen Sie die Befehlszeile oder das Terminal-Fenster und navigieren Sie zu einem Speicherort für das Repository. Beispiel: `/adaptive-forms-core-components`
   1. Führen Sie den folgenden Befehl aus, um das Repository zu klonen:

      ```SHELL
          git clone https://github.com/adobe/aem-core-forms-components.git
      ```

  Das Repository enthält eine Client-Bibliothek, die zum Hinzufügen eines Gebietsschemas erforderlich ist.

  Bei erfolgreicher Ausführung des Befehls wird das Repository auf die `aem-core-forms-components` Ordner auf Ihrem Computer. Im Rest des Artikels wird der Ordner als [Adaptives Forms-Kernkomponenten-Repository].


## Gebietsschema hinzufügen {#add-localization-support-for-non-supported-locales}

Gehen Sie wie folgt vor, um Unterstützung für ein neues Gebietsschema hinzuzufügen:

![Gebietsschema zu einem Repository hinzufügen](add-a-locale-adaptive-form-core-components.png)

### 1. Klonen Sie Ihr AEM as a Cloud Service Git-Repository {#clone-the-repository}

1. Öffnen Sie die Befehlszeile und wählen Sie einen Ordner zum Speichern des as a Cloud Service AEM Forms-Repositorys aus, z. B. `/cloud-service-repository/`.

1. Führen Sie den folgenden Befehl aus, um das Repository zu klonen:

   ```SHELL
   git clone https://git.cloudmanager.adobe.com/<my-org>/<my-program>/
   ```

   Ersetzen `<my-org>` und `<my-program>` in der obigen URL mit Ihrem Organisationsnamen und Programmnamen. Detaillierte Anweisungen zum Abrufen des Organisationsnamens, Programmnamens oder des vollständigen Pfads Ihres Git-Repositorys sowie der zum Klonen des Repositorys erforderlichen Anmeldeinformationen finden Sie im Abschnitt [Zugriff auf Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git) Artikel.

   Nach erfolgreichem Abschluss des Befehls wird ein Ordner `<my-program>` erstellt wird. Sie enthält den Inhalt, der aus dem Git-Repository geklont wurde. Im Rest des Artikels wird der Ordner als `[AEM Forms as a Cloud Service Git repository]`.


### 2. Fügen Sie dem Guide Localization Service das neue Gebietsschema hinzu. {#add-a-locale-to-the-guide-localization-service}

1. Öffnen Sie den im vorherigen Abschnitt geklonten Repository-Ordner in einem Texteditor.
1. Navigieren Sie zum Ordner `[AEM Forms as a Cloud Service Git repository]/ui.config/src/main/content/jcr_root/apps/<appid>/osgiconfig/config`. Sie finden die `<appid>` im `archetype.properties` -Dateien des Projekts.
1. Öffnen Sie die Datei `[AEM Forms as a Cloud Service Git repository]/ui.config/src/main/content/jcr_root/apps/<appid>/osgiconfig/config/Guide Localization Service.cfg.json`, um sie zu bearbeiten. Wenn die Datei nicht vorhanden ist, erstellen Sie sie. Eine Beispieldatei mit unterstützten Gebietsschemata sieht wie folgt aus:

   ![Beispiel für einen Guide Localization Service.cfg.json](locales.png)

1. Fügen Sie die [Gebietsschema-Code für die Sprache](https://de.wikipedia.org/wiki/Liste_der_ISO-639-1-Codes) , die Sie hinzufügen möchten, z. B. &quot;hi&quot;für &quot;nachträglich&quot;.
1. Speichern und schließen Sie die Datei.

### 3. Erstellen einer Client-Bibliothek zum Hinzufügen eines Gebietsschemas

AEM Forms bietet eine Beispiel-Client-Bibliothek, mit der Sie neue Gebietsschemata einfach hinzufügen können. Sie können die `clientlib-it-custom-locale` Client-Bibliothek aus [Adaptives Forms-Kernkomponenten-Repository] auf GitHub zu Ihrem as a Cloud Service Forms-Repository hinzufügen. Gehen Sie wie folgt vor, um die Client-Bibliothek hinzuzufügen:

1. Öffnen Sie Ihre [Adaptives Forms-Kernkomponenten-Repository] in Ihrem Texteditor verwenden. Wenn Sie das Repository nicht geklont haben, lesen Sie [Voraussetzungen](#prerequistes) für Anweisungen zum Klonen des Repositorys.
1. Wechseln Sie in das Verzeichnis `/aem-core-forms-components/it/apps/src/main/content/jcr_root/apps/forms-core-components-it/clientlibs`.
1. Kopieren Sie die `clientlib-it-custom-locale` Verzeichnis.
1. Navigieren Sie zu `[AEM Forms as a Cloud Service Git repository]/ui.apps/src/main/content/jcr_root/apps/moonlightprodprogram/clientlibs` und fügen Sie die `clientlib-it-custom-locale` Verzeichnis.


### 4. Gebietsschemaspezifische Datei erstellen {#locale-specific-file}

1. Navigieren Sie zu `[AEM Forms as a Cloud Service Git repository]/ui.apps/src/main/content/jcr_root/apps/<program-id>/clientlibs/clientlib-it-custom-locale/resources/i18n/`
1. Suchen Sie die [Englisch locale .json file on GitHub](https://github.com/adobe/aem-core-forms-components/blob/master/ui.af.apps/src/main/content/jcr_root/apps/core/fd/af-clientlibs/core-forms-components-runtime-all/resources/i18n/en.json), der den neuesten Satz von Standardzeichenfolgen enthält, die im Produkt enthalten sind.
1. Erstellen Sie eine JSON-Datei für Ihr bestimmtes Gebietsschema.
1. Spiegeln Sie in der neu erstellten JSON-Datei die Struktur der englischen Gebietsschema-Datei.
1. Ersetzen Sie die englischen Sprachzeichenfolgen in Ihrer JSON-Datei durch die entsprechenden lokalisierten Zeichenfolgen für Ihre Sprache.
1. Speichern und schließen Sie die Datei.


### 5. Gebietsschema-Unterstützung zum Wörterbuch hinzufügen {#add-locale-support-for-the-dictionary}

Führen Sie diesen Schritt nur dann durch, wenn das `<locale>`, das Sie hinzufügen möchten, nicht unter den Gebietsschemata `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja` oder `ko-kr` ist.

1. Navigieren Sie zum Ordner `[AEM Forms as a Cloud Service Git repository]/ui.content/src/main/content/jcr_root/etc/`.

1. Erstellen Sie eine `etc` Ordner unter `jcr_root` Ordner, falls noch nicht vorhanden.

1. Ordner erstellen `languages` unter `etc` Ordner, falls noch nicht vorhanden.

   ![Alternativtext](etc-content-xml.png)

1. Erstellen Sie eine `.content.xml` Datei unter `languages` Ordner. Fügen Sie der Datei den folgenden Inhalt hinzu:

   ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
   jcr:primaryType="nt:unstructured"
   languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr]"/>
   ```

1. Fügen Sie den Gebietsschema-Code zum `languages` -Eigenschaft. Zum Beispiel hat hi für das Eingabefeld zum folgenden Beispielcode hinzugefügt.


   ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
   jcr:primaryType="nt:unstructured"
   languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr,hi]"/>
   ```

1. Fügen Sie die neu erstellten Ordner im `filter.xml` under `/ui.content/src/main/content/meta-inf/vault/filter.xml` as:

   ```
   <filter root="/etc/languages"/>
   ```

   ![Fügen Sie die neu erstellten Ordner im `filter.xml` under `/ui.content/src/main/content/meta-inf/vault/filter.xml`](langauge-filter.png)

### 6. Zusagen der Änderungen und Bereitstellen der Pipeline {#commit-changes-in-repo-deploy-pipeline}

Übertragen Sie die Änderungen an das GIT-Repository, nachdem Sie das neue Gebietsschema hinzugefügt haben. Stellen Sie Ihren Code mithilfe der Full-Stack-Pipeline bereit. Erfahren Sie, wie Sie [eine Pipeline einrichten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline), um eine neue Gebietsschema-Unterstützung hinzuzufügen.

Sobald die Pipeline-Ausführung erfolgreich war, kann das neu hinzugefügte Gebietsschema verwendet werden.

## Vorschau eines adaptiven Formulars mit dem neu hinzugefügten Gebietsschema {#use-added-locale-in-af}

Führen Sie die folgenden Schritte aus, um eine Vorschau eines adaptiven Formulars mit dem neu hinzugefügten Gebietsschema anzuzeigen:

1. Melden Sie sich bei Ihrer as a Cloud Service AEM Forms-Instanz an.
1. Gehen Sie zu **Formulare** > **Formulare und Dokumente**.
1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **Wörterbuch hinzufügen**. Daraufhin wird der Assistent **Wörterbuch zum Übersetzungsprojekt hinzufügen** geöffnet.
1. Geben Sie den **Projekttitel** an und wählen Sie die **Zielsprachen** aus dem Dropdown-Menü im Assistenten **Wörterbuch zum Übersetzungsprojekt hinzufügen**.
1. Klicken auf **Fertig** und führen Sie das erstellte Übersetzungsprojekt aus.
1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **Vorschau als HTML**.
1. Fügen Sie `&afAcceptLang=<locale-name>` in der URL eines adaptiven Formulars hinzu.
1. Aktualisieren Sie die Seite. Das adaptive Formular wird daraufhin im angegebenen Gebietsschema dargestellt.

## Best Practices zur Unterstützung neuer Lokalisierungen {#best-practices}

* Adobe empfiehlt die Erstellung eines Übersetzungsprojekts nach der Erstellung eines adaptiven Formulars.

* Wenn neue Felder in einem vorhandenen adaptiven Formular hinzugefügt werden:
   * **Für maschinelle Übersetzung**[: Erstellen Sie das Wörterbuch neu und führen Sie das Übersetzungsprojekt aus](/help/forms/using-aem-translation-workflow-to-localize-adaptive-forms-core-components.md). Felder, die einem adaptiven Formular nach dem Erstellen eines Übersetzungsprojekts hinzugefügt wurden, bleiben unübersetzt.
   * **für die menschliche Übersetzung**: Exportieren Sie das Wörterbuch über die Benutzeroberfläche unter `[AEM Forms Server]/libs/cq/i18n/gui/translator.html`. Aktualisieren Sie das Wörterbuch für die neu hinzugefügten Felder und laden Sie es hoch.

## Weitere Informationen

* [Generieren eines Datensatzdokuments für adaptive Formulare](/help/forms/generate-document-of-record-core-components.md)
* [Hinzufügen eines adaptiven Formulars zu einer AEM Sites-Seite oder einem Experience Fragment](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)


## Siehe auch {#see-also}

{{see-also}}