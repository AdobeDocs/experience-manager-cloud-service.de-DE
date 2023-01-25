---
title: Unterstützung neuer Gebietsschemata zum Lokalisieren von adaptiven Formularen
seo-title: Supporting new locales for adaptive forms localization
description: Mit AEM Forms können Sie neue Gebietsschemata zum Lokalisieren adaptiver Formulare hinzufügen. Englisch (en), Spanisch (es), Französisch (fr), Italienisch (it), Deutsch (de), Japanisch (ja), Portugiesisch-Brasilianisch (pt-BR), Chinesisch (zh-CN), Chinesisch-Taiwan (zh-TW) und Koreanisch (ko-KR).
seo-description: AEM Forms allows you to add new locales for localizing adaptive forms. We support 10 locales out of the box curently, as  "en","fr","de","ja","pt-br","zh-cn","zh-tw","ko-kr","it","es".
source-git-commit: eb722054f6a51320a7772bf666f656418f8392cd
workflow-type: tm+mt
source-wordcount: '1141'
ht-degree: 33%

---

# Unterstützung neuer Gebietsschemas zum Lokalisieren von adaptiven Formularen{#supporting-new-locales-for-adaptive-forms-localization}

## Informationen zu Gebietsschema-Wörterbüchern {#about-locale-dictionaries}

Die Lokalisierung von adaptiven Formularen beruht auf zwei Arten von Gebietsschemawörterbüchern:

* **Formularspezifisches Wörterbuch** Enthält Zeichenfolgen, die in adaptiven Formularen verwendet werden. Zum Beispiel Beschriftungen, Feldnamen, Fehlermeldungen, Hilfebeschreibungen usw. Wird für jedes Gebietsschema in Form eines Satzes von XLIFF-Dateien für die einzelnen Gebietsschemas verwaltet und ist unter `[author-instance]/libs/cq/i18n/gui/translator.html` verfügbar.

* **Globale Wörterbücher** In der AEM-Client-Bibliothek gibt es zwei globale Wörterbücher, die als JSON-Objekte verwaltet werden. Diese Wörterbücher enthalten Standardfehlermeldungen, Monatsnamen, Währungssymbole, Datums- und Uhrzeitmuster usw. Sie finden diese Wörterbücher unter `[author-instance]/libs/fd/xfaforms/clientlibs/I18N`. Diese Speicherorte enthalten separate Ordner für jedes Gebietsschema. Da globale Wörterbücher nicht häufig aktualisiert werden, können Browser separate JavaScript-Dateien für jedes Gebietsschema zwischenspeichern und die Nutzung der Netzwerkbandbreite reduzieren, wenn auf demselben Server auf verschiedene adaptive Formulare zugegriffen wird.

Schritte zur Unterstützung der neuen Lokalisierung für AEM Forms:

1. [Hinzufügen von Lokalisierungsunterstützung für nicht unterstützte Gebietsschemas](#add-localization-support-for-non-supported-locales-add-localization-support-for-non-supported-locales)
1. [Hinzugefügte Gebietsschemata in Adaptive Forms verwenden](#use-added-locale-in-adaptive-forms-use-added-locale-in-af)

## Hinzufügen von Lokalisierungsunterstützung für nicht unterstützte Gebietsschemas {#add-localization-support-for-non-supported-locales}

AEM Forms unterstützt derzeit die Lokalisierung von Adaptive Forms-Inhalten in den Gebietsschemata Englisch (en), Spanisch (es), Französisch (fr), Italienisch (it), Deutsch (de), Japanisch (ja), Portugiesisch-Brasilianisch (pt-BR), Chinesisch (zh-CN), Chinesisch-Taiwan (zh-TW) und Koreanisch (ko-KR).

So fügen Sie während der Laufzeit adaptiver Formulare Unterstützung für ein neues Gebietsschema hinzu:

1. [Repository klonen](#1-clone-the-repository-clone-the-repository)
1. [Hinzufügen eines Gebietsschemas zum GuideLocalizationService-Service](#1-add-a-locale-to-the-guide-localization-service-add-a-locale-to-the-guide-localization-service-br)
1. [Gebietsschema-Namen-spezifischen Ordner hinzufügen](#3-add-locale-name-specific-folder-add-locale-name-specific-folder)
3,1 [XFA-Client-Bibliothek für ein Gebietsschema hinzufügen](#3-add-xfa-client-library-for-a-locale)
3,2 [Clientbibliothek für adaptives Formular für ein Gebietsschema hinzufügen](#4-add-adaptive-form-client-library-for-a-locale-add-adaptive-form-client-library-for-a-locale-br)
1. [Hinzufügen von Gebietsschema-Unterstützung für das Wörterbuch](#5-add-locale-support-for-the-dictionary-add-locale-support-for-the-dictionary-br)
1. [Übertragen der Änderungen im Repository und Bereitstellen der Pipeline](#7-commit-the-changes-in-the-repository-and-deploy-the-pipeline-commit-changes-in-repo-deploy-pipeline)

### 1. Repository klonen {#clone-the-repository}

1. Navigieren Sie in der Befehlszeile zu der Stelle, an der Sie das Forms-Cloud Service-Repository klonen möchten.
1. Führen Sie den Befehl aus, den Sie [wird von Cloud Manager abgerufen.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git) Sie ähnelt `git clone https://git.cloudmanager.adobe.com/<my-org>/<my-program>/`.
1. Verwenden Sie den Git-Benutzernamen und das Kennwort, um das Repository zu klonen.
1. Öffnen Sie den geklonten Forms-Cloud Service-Repository-Ordner in Ihrem bevorzugten Editor.

### 2. Gebietsschema zum Guide Localization-Dienst hinzufügen {#add-a-locale-to-the-guide-localization-service-br}

1. Suchen Sie die `Guide Localization Service.cfg.json` und fügen Sie das Gebietsschema hinzu, das Sie zur Liste der unterstützten Gebietsschemata hinzufügen möchten.

   >[!NOTE]
   >
   >* Erstellen Sie eine Datei mit dem Namen `Guide Localization Service.cfg.json` , falls noch nicht vorhanden.


### 3. Fügen Sie die Client-Bibliothek für Gebietsschema-Namen-spezifische Ordner hinzu {#add-locale-name-specific-folder}

1. Erstellen Sie im Ordner &quot;UI.content&quot; `etc/clientlibs` Ordner.
1. Erstellen Sie außerdem einen Ordner mit dem Namen `locale-name` under `etc/clientlibs` , um als Container für xfa und af clientlibs zu dienen.

#### 3.1 XFA-Client-Bibliothek für ein Gebietsschema im Ordner &quot;locale name&quot;hinzufügen

1. Erstellen Sie einen Knoten mit dem Namen `[locale-name]_xfa` und geben Sie als `cq:ClientLibraryFolder` under `etc/clientlibs/locale_name`, mit Kategorie `xfaforms.I18N.<locale>`und fügen Sie die folgenden Dateien hinzu:
* **I18N.js**, die `xfalib.locale.Strings` für das `<locale>` definiert, wie in `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N` festgelegt.
* **js.txt**, die Folgendes enthält:
   */libs/fd/xfaforms/clientlibs/I18N/Namespace.js I18N.js /etc/clientlibs/fd/xfaforms/I18N/LogMessages.js*

#### 3.2. Adaptive Formular-Client-Bibliothek für Gebietsschema-Ordner &quot;locale name&quot; hinzufügen {#add-adaptive-form-client-library-for-a-locale-br}

1. Erstellen Sie einen Knoten mit dem Namen `[locale-name]_af` und geben Sie als `cq:ClientLibraryFolder` under `etc/clientlibs/locale_name`, wobei Kategorie `guides.I18N.<locale>` und Abhängigkeiten als `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` und `guide.common`.
1. Erstellen Sie einen Ordner mit dem Namen `javascript` und fügen Sie die folgenden Dateien hinzu:

   * **i18n.js** die `guidelib.i18n` definiert, mit Mustern von „calendarSymbols“, `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols`, `typefaces` für das `<locale>` gemäß den XFA-Spezifikationen, die in der [Spezifikation für Gebietsschema-Sätze](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf) beschrieben sind.
   * **LogMessages.js**, die `guidelib.i18n.strings` und `guidelib.i18n.LogMessages` für das `<locale>` wie in `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js` festgelegt definiert.

1. Hinzufügen **js.txt** enthält Folgendes:

   ```text
     i18n.js
       LogMessages.js
   ```

### 4. Gebietsschema-Unterstützung für das Wörterbuch hinzufügen {#add-locale-support-for-the-dictionary-br}

Führen Sie diesen Schritt nur dann durch, wenn das `<locale>`, das Sie hinzufügen möchten, nicht eines der Gebietsschemas `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja` oder `ko-kr` ist.

1. Ordner erstellen `languages` under `etc`, falls nicht bereits vorhanden.

1. Falls noch nicht vorhanden, fügen Sie dem Knoten eine Eigenschaft `languages` vom Typ „Zeichenfolge“ hinzu, die mehrere Werte aufnehmen kann.
1. Fügen Sie die `<locale-name>`-Standardgebietsschema-Werte `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja` und `ko-kr` hinzu, falls noch nicht vorhanden.

1. Fügen Sie das `<locale>` den Werten der Eigenschaft `languages` von `/etc/languages` hinzu.


```text
Add the newly created folders in the `filter.xml` under etc/META-INF/[folder hierarchy] as:
<filter root="/etc/clientlibs/[locale-name]"/>
<filter root="/etc/languages"/>
```

Bevor Sie die Änderungen in das AEM Git-Repository übernehmen, müssen Sie auf Ihre [Git-Repository-Informationen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#accessing-git).

### 5. Übertragen Sie die Änderungen im Repository und stellen Sie die Pipeline bereit. {#commit-chnages-in-repo-deploy-pipeline}

Übertragen Sie die Änderungen an das GIT-Repository, nachdem Sie eine neue Gebietsschema-Unterstützung hinzugefügt haben. Stellen Sie Ihren Code mithilfe der vollständigen Stack-Pipeline bereit. Lernen [Einrichten einer Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#setup-pipeline) um neue Gebietsschema-Unterstützung hinzuzufügen.

Sobald die Pipeline abgeschlossen ist, wird das neu hinzugefügte Gebietsschema in der AEM-Umgebung angezeigt.

### Hinzugefügtes Gebietsschema in Adaptive Forms verwenden {#use-added-locale-in-af}

Schritte zum Verwenden und Rendern eines adaptiven Formulars mit einem neu hinzugefügten Gebietsschema:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an.
1. Navigieren Sie zu **Forms** >  **Forms und Dokumente**.
1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **Wörterbuch hinzufügen** und **Wörterbuch zum Übersetzungsprojekt hinzufügen** wird angezeigt.
1. Geben Sie die **Projekttitel** und wählen Sie die **Zielsprachen** aus dem Dropdown-Menü im **Wörterbuch zum Übersetzungsprojekt hinzufügen** Assistent.
1. Klicken **Fertig** und führen Sie das erstellte Übersetzungsprojekt aus.
1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **Vorschau als HTML**.
1. Hinzufügen `&afAcceptLang=<locale-name>` in der URL eines adaptiven Formulars.
1. Aktualisieren Sie die Seite und das adaptive Formular wird in einem angegebenen Gebietsschema wiedergegeben.

Es gibt zwei Methoden, um das Gebietsschema eines adaptiven Formulars zu identifizieren. Wenn ein adaptives Formular dargestellt wird, wird das angeforderte Gebietsschema durch Folgendes identifiziert:

* Überprüfung der `[local]`-Auswahl in der URL des adaptiven Formulars. Das Format der URL ist `http://host:[port]/content/forms/af/[afName].[locale].html?wcmmode=disabled`. Mithilfe der `[local]`-Auswahl können adaptive Formulare zwischengespeichert werden.

* Überprüfung der folgenden Parameter in der angegebenen Reihenfolge:

   * Abfrageparameter `afAcceptLang`
Um das Browser-Gebietsschema von Benutzern zu überschreiben, können Sie den 
`afAcceptLang`-Abfrageparameter übergeben, um das Gebietsschema zu erzwingen. Beispielsweise erzwingt die folgende URL die Wiedergabe des Formulars im kanadisch-französischen Gebietsschema:
      `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ca-fr`

   * Das für den Benutzer festgelegte Browser-Gebietsschema, das in der Abfrage mit dem `Accept-Language`-Header angegeben ist.

Wenn für das angeforderte Gebietsschema keine Client-Bibliothek vorhanden ist, wird nach einer Client-Bibliothek für den im Gebietsschema vorhandenen Sprach-Code gesucht. Wenn das angeforderte Gebietsschema beispielsweise `en_ZA` (Südafrikanisches Englisch) und die Client-Bibliothek für `en_ZA` nicht vorhanden ist, verwendet das adaptive Formular die Client-Bibliothek für `en` (Englisch) Sprache, sofern vorhanden. Wenn jedoch keine davon vorhanden ist, verwendet das adaptive Formular das Wörterbuch für das Gebietsschema `en`.


Sobald das Gebietsschema identifiziert wurde, wählt das adaptive Formular das formularspezifische Wörterbuch aus. Wenn das formularspezifische Wörterbuch für das angeforderte Gebietsschema nicht gefunden wird, wird das Wörterbuch für die Sprache verwendet, in der das adaptive Formular erstellt wird.

Wenn keine Informationen zum Gebietsschema vorhanden sind, wird das adaptive Formular in der Originalsprache des Formulars übermittelt. Die Originalsprache ist die Sprache, die bei der Entwicklung des adaptiven Formulars verwendet wurde.

Get [Beispiel-Client-Bibliothek](/help/forms/assets/locale-support-sample.zip) , um Unterstützung für neues Gebietsschema hinzuzufügen. Sie müssen den Inhalt des Ordners im erforderlichen Gebietsschema ändern.

### Best Practices zur Unterstützung neuer Lokalisierungen {#best-practices}

* Adobe empfiehlt, ein Übersetzungsprojekt nach dem Erstellen eines adaptiven Formulars zu erstellen.

* Wenn neue Felder in einem vorhandenen adaptiven Formular hinzugefügt werden:
   * **Für maschinelle Übersetzung**: Erstellen Sie das Wörterbuch neu und führen Sie das Übersetzungsprojekt aus. Felder, die einem adaptiven Formular nach dem Erstellen eines Übersetzungsprojekts hinzugefügt wurden, bleiben unübersetzt.
   * **für die menschliche Übersetzung**: Wörterbuch exportieren über `[server:port]/libs/cq/i18n/gui/translator.html`. Aktualisieren Sie das Wörterbuch für die neu hinzugefügten Felder und laden Sie es hoch.
