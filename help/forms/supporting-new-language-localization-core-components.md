---
title: Wie füge ich einem adaptiven Formular, das auf Kernkomponenten basiert, Unterstützung für neue Gebietsschemata hinzu?
description: Erfahren Sie, wie Sie neue Gebietsschemata für ein adaptives Formular hinzufügen.
feature: Adaptive Forms, Core Components
exl-id: bc06542b-84c8-4c6a-a305-effbd16d5630
source-git-commit: 559b4afa975dcd2204cd06c95f19ed38da00033e
workflow-type: ht
source-wordcount: '1333'
ht-degree: 100%

---

# Hinzufügen eines Gebietsschemas für auf Kernkomponenten basierende adaptive Formulare {#supporting-new-locales-for-adaptive-forms-localization}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| Foundation-Komponenten | [Hier klicken](supporting-new-language-localization.md) |
| Kernkomponenten | Dieser Artikel |

<span class="preview"> Die Unterstützungsfunktion für Sprachen von rechts nach links ist im Rahmen des Early-Adopter-Programms verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugang zu dieser Funktion zu beantragen. </span>

AEM Forms bietet vorkonfiguriert Unterstützung für die Gebietsschemata Englisch (en), Spanisch (es), Französisch (fr), Italienisch (it), Deutsch (de), Japanisch (ja), brasilianisches Portugiesisch (pt-BR), Chinesisch (zh-CN), Chinesisch – Taiwan (zh-TW) und Koreanisch (ko-KR). Sie können auch Unterstützung für weitere Gebietsschemata hinzufügen, wie Hindi (hi_IN). Sie können adaptive Formulare auch in einer RTL-Sprache (Right-to-Left, rechts nach links) wie Arabisch, Persisch und Urdu präsentieren, indem Sie diese Gebietsschemata hinzufügen.

## Wie wird das Gebietsschema für ein adaptives Formular ausgewählt?

Bevor Sie mit dem Hinzufügen eines Gebietsschemas für adaptive Formulare beginnen, sollten Sie wissen, wie ein Gebietsschema für ein adaptives Formular ausgewählt wird. Es gibt zwei Methoden zum Identifizieren und Auswählen des Gebietsschemas für ein adaptives Formular, wenn es gerendert wird:

* **Verwenden des `locale`-Selektors in der URL**: Beim Rendern eines adaptiven Formulars identifiziert das System das angeforderte Gebietsschema, indem es den [Gebietschema]-Selektor in der URL des adaptiven Formulars überprüft. Die URL hat folgendes Format: http:/[AEM Forms Server URL]/content/forms/af/[afName].[locale].html?wcmmode=disabled. Die Verwendung des [Gebietsschema]-Selektors ermöglicht die Zwischenspeicherung des adaptiven Formulars. Beispielsweise die gibt die URL `www.example.com/content/forms/af/contact-us.hi.html?wcmmmode=disabled` das Formular in der Sprache Hindi aus.

* Abrufen der Parameter in der unten aufgeführten Reihenfolge:

   * **Verwenden der `afAcceptLang`Anfrageparameter**: Um das Browser-Gebietsschema der Benutzerin bzw. des Benutzers zu überschreiben, können Sie den Anforderungsparameter „afAcceptLang“ übergeben. Zum Beispiel erzwingt die URL `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ca-fr` vom AEM Forms-Server die Wiedergabe des Formulars im Gebietsschema „kanadisches Französisch“.

   * **Verwenden des Browser-Gebietsschemas (Accept-Language-Header)**: Das System berücksichtigt auch das Browser-Gebietsschema der Benutzerin bzw. des Benutzers, das in der Anfrage mit dem `Accept-Language`-Header angegeben ist.

  Wenn eine Client-Bibliothek (der Prozess zum Erstellen und Verwenden der Bibliothek wird später in diesem Artikel erläutert) für das angeforderte Gebietsschema nicht verfügbar ist, überprüft das System, ob eine Client-Bibliothek für den Sprach-Code im Gebietsschema vorhanden ist. Wenn das angeforderte Gebietsschema beispielsweise `en_ZA` (südafrikanisches Englisch) ist und keine Client-Bibliothek für `en_ZA` vorhanden ist, verwendet das adaptive Formular die Client-Bibliothek für „en“ (Englisch), sofern verfügbar. Wenn keines davon gefunden wird, greift das adaptive Formular auf das Wörterbuch für das Gebietsschema `en` zurück.

  Nachdem das Gebietsschema identifiziert wurde, wählt das adaptive Formular das formularspezifische Wörterbuch aus. Wenn das Wörterbuch für das angeforderte Gebietsschema nicht gefunden wird, wird standardmäßig das Wörterbuch in der Sprache verwendet, in der das adaptive Formular verfasst wurde.

  Wenn keine Sprachinformationen verfügbar sind, wird das adaptive Formular in der Originalsprache angezeigt, die bei der Entwicklung des Formulars verwendet wurde.


## Voraussetzungen {#prerequistes}

Bevor Sie mit dem Hinzufügen eines Gebietsschemas beginnen:

* Installieren Sie einen Nur-Text-Editor (IDE) für eine einfachere Bearbeitung. Die Beispiele in diesem Dokument basieren auf [Microsoft® Visual Studio Code](https://code.visualstudio.com/download).
* Installieren Sie eine Version von [Git](https://git-scm.com), falls dies auf Ihrem Computer nicht vorhanden ist.
* Klonen Sie das Repository [Kernkomponenten für adaptive Formulare](https://github.com/adobe/aem-core-forms-components). So klonen Sie das Repository:
   1. Öffnen Sie die Befehlszeile oder ein Terminal-Fenster und navigieren Sie zu einem Speicherort für das Repository. Beispiel: `/adaptive-forms-core-components`
   1. Führen Sie den folgenden Befehl aus, um das Repository zu klonen:

      ```SHELL
          git clone https://github.com/adobe/aem-core-forms-components.git
      ```

  Das Repository enthält eine Client-Bibliothek, die zum Hinzufügen eines Gebietsschemas erforderlich ist.

  Bei erfolgreicher Ausführung des Befehls wird das Repository im `aem-core-forms-components`-Ordner auf Ihrem Computer geklont. Im Rest des Artikels wird der Ordner als [Repository „Kernkomponenten für adaptive Formulare“] bezeichnet.


## Hinzufügen eines Gebietsschemas {#add-localization-support-for-non-supported-locales}

Gehen Sie wie folgt vor, um Unterstützung für ein neues Gebietsschema hinzuzufügen:

![Hinzufügen eines Gebietsschemas zu einem Repository](add-a-locale-adaptive-form-core-components.png)

### 1. Klonen des Git-Repositorys von AEM as a Cloud Service {#clone-the-repository}

1. Öffnen Sie die Befehlszeile und wählen Sie einen Ordner zum Speichern des AEM Forms as a Cloud Service-Repositorys aus, z. B. `/cloud-service-repository/`.

1. Führen Sie den folgenden Befehl aus, um das Repository zu klonen:

   ```SHELL
   git clone https://git.cloudmanager.adobe.com/<my-org>/<my-program>/
   ```

   Ersetzen Sie `<my-org>` und `<my-program>` in der obigen URL durch Ihren Organisationsnamen und Programmnamen. Detaillierte Anweisungen zum Abrufen des Organisationsnamens, Programmnamens oder des vollständigen Pfads Ihres Git-Repositorys sowie der zum Klonen des Repositorys erforderlichen Anmeldeinformationen finden Sie im Artikel [Zugreifen auf Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git).

   Nach erfolgreichem Abschluss des Befehls wird der Ordner `<my-program>` erstellt. Er enthält den Inhalt, der aus dem Git-Repository geklont wurde. Im Rest des Artikels wird der Ordner als `[AEM Forms as a Cloud Service Git repository]` bezeichnet.


### 2. Hinzufügen eines Gebietsschemas zum Handbuch-Lokalisierungsdienst {#add-a-locale-to-the-guide-localization-service}

1. Öffnen Sie den im vorherigen Abschnitt geklonten Repository-Ordner in einem einfachen Texteditor.
1. Navigieren Sie zum Ordner `[AEM Forms as a Cloud Service Git repository]/ui.config/src/main/content/jcr_root/apps/<appid>/osgiconfig/config`. Sie finden die `<appid>` in den `archetype.properties`-Dateien des Projekts.
1. Öffnen Sie die Datei `[AEM Forms as a Cloud Service Git repository]/ui.config/src/main/content/jcr_root/apps/<appid>/osgiconfig/config/Guide Localization Service.cfg.json`, um sie zu bearbeiten. Wenn die Datei nicht vorhanden ist, erstellen Sie sie. Eine Beispieldatei mit unterstützten Gebietsschemata sieht wie folgt aus:

   ![Beispiel für „Guide Localization Service.cfg.json“](locales.png)

1. Fügen Sie den [Gebietsschema-Code für die Sprache](https://de.wikipedia.org/wiki/Liste_der_ISO-639-1-Codes) hinzu, die Sie hinzufügen möchten, z. B. „hi“ für Hindi.
1. Speichern und schließen Sie die Datei.

### 3. Erstellen einer Client-Bibliothek zum Hinzufügen eines Gebietsschemas

AEM Forms bietet eine Beispiel-Client-Bibliothek, mit der Sie einfach neue Gebietsschemata hinzufügen können. Sie können die Client-Bibliothek `clientlib-it-custom-locale` aus dem [Repository der Kernkomponenten für adaptive Formulare] auf GitHub zu Ihrem Forms as a Cloud Service-Repository hinzufügen. Gehen Sie wie folgt vor, um die Client-Bibliothek hinzuzufügen:

1. Öffnen Sie Ihr [Repository der Kernkomponenten für adaptive Formulare] in einem einfachen Texteditor. Wenn Sie das Repository nicht geklont haben, sehen Sie sich die [Voraussetzungen](#prerequistes) an, um Anweisungen zum Klonen des Repositorys zu erhalten.
1. Wechseln Sie in das Verzeichnis `/aem-core-forms-components/it/apps/src/main/content/jcr_root/apps/forms-core-components-it/clientlibs`.
1. Kopieren Sie das Verzeichnis `clientlib-it-custom-locale`.
1. Navigieren Sie zu `[AEM Forms as a Cloud Service Git repository]/ui.apps/src/main/content/jcr_root/apps/moonlightprodprogram/clientlibs` und fügen Sie das Verzeichnis `clientlib-it-custom-locale` ein.


### 4. Erstellen einer gebietsschemaspezifischen Datei {#locale-specific-file}

1. Navigieren Sie zu `[AEM Forms as a Cloud Service Git repository]/ui.apps/src/main/content/jcr_root/apps/<program-id>/clientlibs/clientlib-it-custom-locale/resources/i18n/`
1. Suchen Sie die [JSON-Datei des englischen Gebietsschemas auf GitHub](https://github.com/adobe/aem-core-forms-components/blob/master/ui.af.apps/src/main/content/jcr_root/apps/core/fd/af-clientlibs/core-forms-components-runtime-all/resources/i18n/en.json), die den neuesten Satz von Standardzeichenfolgen enthält, die im Produkt enthalten sind.
1. Erstellen Sie eine JSON-Datei für Ihr spezielles Gebietsschema.
1. Spiegeln Sie in der neu erstellten JSON-Datei die Struktur der englischen Gebietsschemadatei.
1. Ersetzen Sie in Ihrer JSON-Datei die Zeichenfolgen für die englische Sprache durch die entsprechenden lokalisierten Zeichenfolgen für Ihre Sprache.
1. Speichern und schließen Sie die Datei.


### 5. Hinzufügen der Gebietsschemaunterstützung für das Wörterbuch {#add-locale-support-for-the-dictionary}

Führen Sie diesen Schritt nur dann durch, wenn das `<locale>`, das Sie hinzufügen möchten, nicht zu den Gebietsschemata `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja` oder `ko-kr` gehört.

1. Navigieren Sie zum Ordner `[AEM Forms as a Cloud Service Git repository]/ui.content/src/main/content/jcr_root/etc/`.

1. Erstellen Sie den Ordner `etc` im Ordner `jcr_root`, falls er noch nicht vorhanden ist.

1. Erstellen Sie den Ordner `languages` im Ordner `etc`, falls er noch nicht vorhanden ist.

   ![Alt-Text](etc-content-xml.png)

1. Erstellen Sie eine `.content.xml`-Datei im Ordner `languages`. Fügen Sie der Datei den folgenden Inhalt hinzu:

   ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
   jcr:primaryType="nt:unstructured"
   languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr]"/>
   ```

1. Fügen Sie den Gebietsschema-Code zur Eigenschaft `languages` hinzu. Zum Beispiel wird „hi“ für Hindi zum folgenden Beispiel-Code hinzugefügt.


   ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
   jcr:primaryType="nt:unstructured"
   languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr,hi]"/>
   ```

1. Fügen Sie die neu erstellten Ordner in `filter.xml` unter `/ui.content/src/main/content/meta-inf/vault/filter.xml` wie folgt hinzu:

   ```
   <filter root="/etc/languages"/>
   ```

   ![Fügen Sie die erstellten Ordner in `filter.xml` unter `/ui.content/src/main/content/meta-inf/vault/filter.xml`](langauge-filter.png) hinzu

### 6. Übertragen der Änderungen und Bereitstellen der Pipeline {#commit-changes-in-repo-deploy-pipeline}

Übertragen Sie die Änderungen an das GIT-Repository, nachdem Sie ein neues Gebietsschema hinzugefügt haben. Stellen Sie Ihren Code mithilfe der Full-Stack-Pipeline bereit. Erfahren Sie, wie Sie [eine Pipeline einrichten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline), um eine neue Gebietsschema-Unterstützung hinzuzufügen.

Sobald die Pipeline-Ausführung erfolgreich war, kann das neu hinzugefügte Gebietsschema verwendet werden.

## Vorschau eines adaptiven Formulars mit dem neu hinzugefügten Gebietsschema {#use-added-locale-in-af}

Führen Sie die folgenden Schritte aus, um die Vorschau eines adaptiven Formulars mit einem neu hinzugefügten Gebietsschema anzuzeigen:

1. Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Instanz an.
1. Gehen Sie zu **Formulare** > **Formulare und Dokumente**.
1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **Wörterbuch hinzufügen**. Daraufhin wird der Assistent **Wörterbuch zum Übersetzungsprojekt hinzufügen** geöffnet.
1. Geben Sie den **Projekttitel** an und wählen Sie die **Zielsprachen** aus dem Dropdown-Menü im Assistenten **Wörterbuch zum Übersetzungsprojekt hinzufügen**.
1. Klicken auf **Fertig** und führen Sie das erstellte Übersetzungsprojekt aus.
1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **Vorschau als HTML**.
1. Fügen Sie `&afAcceptLang=<locale-name>` in der URL eines adaptiven Formulars hinzu.
1. Aktualisieren Sie die Seite. Das adaptive Formular wird daraufhin im angegebenen Gebietsschema dargestellt.

## Best Practices zur Unterstützung neuer Lokalisierungen {#best-practices}

* Adobe empfiehlt, ein Übersetzungsprojekt erst nach dem Erstellen eines adaptiven Formulars durchzuführen.

* Wenn neue Felder in einem vorhandenen adaptiven Formular hinzugefügt werden:
   * **Für maschinelle Übersetzung**[: Erstellen Sie das Wörterbuch neu und führen Sie das Übersetzungsprojekt aus](/help/forms/using-aem-translation-workflow-to-localize-adaptive-forms-core-components.md). Felder, die einem adaptiven Formular nach dem Erstellen eines Übersetzungsprojekts hinzugefügt wurden, bleiben unübersetzt.
   * **Für die menschliche Übersetzung**: Exportieren Sie das Wörterbuch mithilfe der UI unter `[AEM Forms Server]/libs/cq/i18n/gui/translator.html`. Aktualisieren Sie das Wörterbuch für die neu hinzugefügten Felder und laden Sie es hoch.

## Mehr anzeigen

* [Generieren eines Datensatzdokuments für adaptive Formulare](/help/forms/generate-document-of-record-core-components.md)
* [Hinzufügen eines adaptiven Formulars zu einer AEM Sites-Seite oder einem Experience Fragment](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)


## Siehe auch {#see-also}

{{see-also}}