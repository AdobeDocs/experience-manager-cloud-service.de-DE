---
title: Wie füge ich einem adaptiven Formular, das auf Foundation-Komponenten basiert, Unterstützung für neue Gebietsschemata hinzu?
description: Bei adaptiven Formularen können Sie Gebietsschemata für weitere Sprachen zusätzlich zu den vorkonfigurierten Sprachen hinzufügen.
feature: Adaptive Forms, Foundation Components
badgeSaas: label="AEM Forms" type="Positive" tooltip="Gilt für AEM Forms)."
exl-id: 4c7d6caa-1adb-4663-933f-b09129b9baef
role: User, Developer
source-git-commit: 89b0f2a8ca9d2f60365a5c3962b0b4e826f79b3e
workflow-type: tm+mt
source-wordcount: '1226'
ht-degree: 99%

---

# Unterstützung neuer Gebietsschemata zum Lokalisieren von adaptiven Formularen {#supporting-new-locales-for-adaptive-forms-localization}

>[!NOTE]
>
> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) für die Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/creating-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von adaptiven Formularen mithilfe von Foundation-Komponenten beschrieben.


| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/supporting-new-language-localization.html?lang=de) |
| Kernkomponenten | [Hier klicken](supporting-new-language-localization-core-components.md) |
| Foundation-Komponenten | Dieser Artikel |

AEM Forms bietet vorkonfiguriert Unterstützung für die Gebietsschemata Englisch (en), Spanisch (es), Französisch (fr), Italienisch (it), Deutsch (de), Japanisch (ja), brasilianisches Portugiesisch (pt-BR), Chinesisch (zh-CN), Chinesisch – Taiwan (zh-TW) und Koreanisch (ko-KR). Sie können auch Unterstützung für weitere Gebietsschemata hinzufügen, wie Hindi (hi_IN).

## Gebietsschema-Wörterbücher {#about-locale-dictionaries}

Die Lokalisierung von adaptiven Formularen beruht auf zwei Arten von Gebietsschema-Wörterbüchern:

* **Formularspezifisches Wörterbuch** Enthält Zeichenfolgen, die in adaptiven Formularen verwendet werden. Beispielsweise Beschriftungen, Feldnamen, Fehlermeldungen und Hilfebeschreibungen. Wird für jedes Gebietsschema in Form eines Satzes von XLIFF-Dateien für die einzelnen Gebietsschemata verwaltet und ist unter `[author-instance]/libs/cq/i18n/gui/translator.html` verfügbar.

* **Globale Wörterbücher** In der AEM-Client-Bibliothek gibt es zwei globale Wörterbücher, die als JSON-Objekte verwaltet werden. Diese Wörterbücher enthalten Standardfehlermeldungen, Monatsnamen, Währungssymbole, Datums- und Uhrzeitmuster usw. Sie finden diese Wörterbücher unter `[author-instance]/libs/fd/xfaforms/clientlibs/I18N`. Für jedes Gebietsschema gibt es einen separaten Ordner. Globale Wörterbücher werden nicht oft aktualisiert. Durch die separaten JavaScript-Dateien für jedes Gebietsschema können Browser diese im Cache zwischenspeichern. Dies reduziert den Netzwerk-Traffic, wenn auf demselben Server auf verschiedene adaptive Formulare zugegriffen wird.

## Hinzufügen von Unterstützung für neue Gebietsschemata {#add-support-for-new-locales}

Führen Sie die folgenden Schritte aus, um Unterstützung für ein neues Gebietsschema hinzuzufügen:

1. [Hinzufügen von Lokalisierungsunterstützung für nicht unterstützte Gebietsschemata](#add-localization-support-for-non-supported-locales)
1. [Hinzugefügte Gebietsschemata in adaptiven Formularen verwenden](#use-added-locale-in-af)

### Hinzufügen von Lokalisierungsunterstützung für nicht unterstützte Gebietsschemata {#add-localization-support-for-non-supported-locales}

AEM Forms unterstützt die Lokalisierung von Inhalten in adaptiven Formulare in den Gebietsschemata Englisch (en), Spanisch (es), Französisch (fr), Italianisch (it), Deutsch (de), Japanisch (ja), brasilianisches Portugiesisch (pt-BR), Chinesisch (zh-CN), Chinesisch – Taiwan (zh-TW) und Koreanisch (ko-KR).

So fügen Sie während der Laufzeit in adaptiven Formularen Unterstützung für ein neues Gebietsschema hinzu:

1. [Klonen Sie Ihr Repository.](#clone-the-repository)
1. [Fügen Sie ein Gebietsschema zum GuideLocalizationService hinzu.](#add-a-locale-to-the-guide-localization-service)
1. [Fügen Sie einen Ordner mit einem Gebietsschema-spezifischen Namen hinzu.](#add-locale-name-specific-folder)
1. [Fügen Sie Gebietsschema-Unterstützung für das Wörterbuch hinzu.](#add-locale-support-for-the-dictionary)
1. [Übertragen Sie die Änderungen im Repository und stellen Sie die Pipeline bereit.](#commit-changes-in-repo-deploy-pipeline)

#### &#x200B;1. Klonen Sie das Repository. {#clone-the-repository}

1. Navigieren Sie über die Befehlszeile an die Stelle, an der Sie das Forms Cloud Service-Repository klonen möchten.
1. Führen Sie den Befehl aus, den Sie [von Cloud Manager abgerufen haben](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git). Er sieht in etwa so aus: `git clone https://git.cloudmanager.adobe.com/<my-org>/<my-program>/`.
1. Verwenden Sie den Git-Benutzernamen und das Passwort, um das Repository zu klonen.
1. Öffnen Sie den geklonten Forms Cloud Service-Repository-Ordner im Editor Ihrer Wahl.

#### &#x200B;2. Fügen Sie ein Gebietsschema zum Handbuch-Lokalisierungsdienst hinzu. {#add-a-locale-to-the-guide-localization-service}

1. Suchen Sie die Datei `Guide Localization Service.cfg.json` und fügen Sie das gewünschte Gebietsschema in die Liste der unterstützten Gebietsschemata ein.

   >[!NOTE]
   >
   > Erstellen Sie eine Datei mit dem Namen `Guide Localization Service.cfg.json`, falls noch nicht vorhanden.

#### &#x200B;3. Fügen Sie die Client-Bibliothek für Ordner mit Gebietsschema-spezifischen Namen hinzu {#add-locale-name-specific-folder}

1. Erstellen Sie im Ordner „UI.content“ den Ordner `etc/clientlibs`.
1. Erstellen Sie außerdem einen Ordner mit dem Namen `locale-name` unter `etc/clientlibs`, der als Container für xfa- und af-clientlibs dient.

##### 3.1 Fügen Sie die XFA-Client-Bibliothek für ein Gebietsschema in einem Ordner „locale-name“ hinzu.

Erstellen Sie einen Knoten mit dem Namen `[locale-name]_xfa` und dem Typ `cq:ClientLibraryFolder` unter `etc/clientlibs/locale_name`, mit der Kategorie `xfaforms.I18N.<locale>`, und fügen Sie die folgenden Dateien hinzu:

* **I18N.js**, die `xfalib.locale.Strings` für das `<locale>` definiert, wie in `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N` festgelegt.
* **js.txt**, die Folgendes enthält:
  */libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js*

##### 3.2. Fügen Sie die Client-Bibliothek für adaptive Formulare für einen Ordner mit dem Gebietsschema „locale-name“ hinzu.

1. Erstellen Sie einen Knoten mit dem Namen `[locale-name]_af` und dem Typ `cq:ClientLibraryFolder` unter `etc/clientlibs/locale_name`, mit der Kategorie `guides.I18N.<locale>` und den Abhängigkeiten `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` und `guide.common`.
1. Erstellen Sie einen Ordner mit dem Namen `javascript` und fügen Sie die folgenden Dateien hinzu:

   * **i18n.js** die `guidelib.i18n` definiert, mit Mustern von „calendarSymbols“, `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols`, `typefaces` für das `<locale>` gemäß den XFA-Spezifikationen, die in der [Spezifikation für Gebietsschema-Sätze](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf) beschrieben sind.
   * **LogMessages.js**, die `guidelib.i18n.strings` und `guidelib.i18n.LogMessages` für das `<locale>` wie in `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js` festgelegt definiert.

1. Fügen Sie **js.txt** mit folgendem Inhalt hinzu:

   ```
     i18n.js
     LogMessages.js
   ```

#### &#x200B;4. Fügen Sie Gebietsschema-Unterstützung für das Wörterbuch hinzu. {#add-locale-support-for-the-dictionary}

Führen Sie diesen Schritt nur dann durch, wenn das `<locale>`, das Sie hinzufügen möchten, nicht unter den Gebietsschemata `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja` oder `ko-kr` ist.

1. Erstellen Sie den Ordner `languages` unter `etc`, falls noch nicht vorhanden.

1. Falls noch nicht vorhanden, fügen Sie dem Knoten eine Eigenschaft `languages` vom Typ „Zeichenfolge“ hinzu, die mehrere Werte aufnehmen kann.
1. Fügen Sie die `<locale-name>`-Standardgebietsschema-Werte `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja` und `ko-kr` hinzu, falls noch nicht vorhanden.

1. Fügen Sie das `<locale>` den Werten der Eigenschaft `languages` von `/etc/languages` hinzu.
1. Fügen Sie die erstellten Ordner in der Datei `filter.xml` unter etc/META-INF/[Ordnerhierarchie] wie folgt hinzu:

   ```
   <filter root="/etc/clientlibs/[locale-name]"/>
   <filter root="/etc/languages"/>
   ```

Bevor Sie die Änderungen in das AEM Git-Repository übernehmen, müssen Sie auf Ihre [Git-Repository-Informationen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git) zugreifen.

#### &#x200B;5. Übertragen Sie die Änderungen an das Repository und stellen Sie die Pipeline bereit. {#commit-changes-in-repo-deploy-pipeline}

Übertragen Sie die Änderungen an das GIT-Repository, nachdem Sie eine Gebietsschema-Unterstützung hinzugefügt haben. Stellen Sie Ihren Code mithilfe der Full-Stack-Pipeline bereit. Erfahren Sie, wie Sie [eine Pipeline einrichten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline), um Unterstützung für ein neues Gebietsschema hinzuzufügen.
Sobald die Pipeline-Einrichtung abgeschlossen ist, wird das neu hinzugefügte Gebietsschema in der AEM-Umgebung angezeigt.

### Verwenden eines hinzugefügten Gebietsschemas in adaptiven Formularen {#use-added-locale-in-af}

Führen Sie die folgenden Schritte aus, um ein adaptives Formular mit einem neu hinzugefügten Gebietsschema zu verwenden und zu rendern:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an.
1. Gehen Sie zu **Formulare** > **Formulare und Dokumente**.
1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **Wörterbuch hinzufügen**. Daraufhin wird der Assistent **Wörterbuch zum Übersetzungsprojekt hinzufügen** geöffnet.
1. Geben Sie den **Projekttitel** an und wählen Sie die **Zielsprachen** aus dem Dropdown-Menü im Assistenten **Wörterbuch zum Übersetzungsprojekt hinzufügen**.
1. Klicken auf **Fertig** und führen Sie das erstellte Übersetzungsprojekt aus.
1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **Vorschau als HTML**.
1. Fügen Sie `&afAcceptLang=<locale-name>` in der URL eines adaptiven Formulars hinzu.
1. Aktualisieren Sie die Seite. Das adaptive Formular wird daraufhin im angegebenen Gebietsschema dargestellt.

Es gibt zwei Methoden, das Gebietsschema eines adaptiven Formulars zu identifizieren. Beim Rendern identifiziert ein adaptives Formular das angeforderte Gebietsschema folgendermaßen:

* Durch Abrufen des `[local]`-Selektors in der URL des adaptiven Formulars. Das Format der URL ist `http://host:[port]/content/forms/af/[afName].[locale].html?wcmmode=disabled`. Mithilfe der `[local]`-Auswahl können adaptive Formulare zwischengespeichert werden.

* Durch Abrufen der folgenden Parameter in der angegebenen Reihenfolge:

   * Anforderungsparameter `afAcceptLang`
Um das Browser-Gebietsschema der Benutzenden zu überschreiben, können Sie den Anfrageparameter `afAcceptLang` übergeben, um das Gebietsschema zu erzwingen. So erzwingt beispielsweise die folgende URL die Darstellung des Formulars im kanadisch-französischen Gebietsschema:
     `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ca-fr`

   * Das für den Benutzer bzw. die Benutzerin festgelegte Browser-Gebietsschema, das in der Abfrage über den Header `Accept-Language` spezifiziert wird.

Wenn für das angeforderte Gebietsschema keine Client-Bibliothek vorhanden ist, wird nach einer Client-Bibliothek für den im Gebietsschema vorhandenen Sprach-Code gesucht. Beispiel: Wenn das angeforderte Gebietsschema `en_ZA` (südafrikanisches Englisch) lautet und die Client-Bibliothek für `en_ZA` nicht vorhanden ist, verwendet das adaptive Formular die Client-Bibliothek für `en` (Englisch), sofern vorhanden. Wenn jedoch keines davon vorhanden ist, verwendet das adaptive Formular das Wörterbuch für das Gebietsschema `en`.


Nachdem das Gebietsschema identifiziert ist, wählt das adaptive Formular das formularspezifische Wörterbuch aus. Wenn es das formularspezifische Wörterbuch für das angeforderte Gebietsschema nicht findet, verwendet es das Wörterbuch für die Sprache, in der das adaptive Formular verfasst wurde.

Wenn keine Informationen zum Gebietsschema vorhanden sind, wird das adaptive Formular in der Originalsprache des Formulars übermittelt. Die Originalsprache ist die Sprache, die bei der Entwicklung des adaptiven Formulars verwendet wurde.

Holen Sie sich die [Muster-Client-Bibliothek](/help/forms/assets/locale-support-sample.zip), um die Unterstützung für neue Gebietsschemata hinzuzufügen. Sie müssen den Inhalt des Ordners im erforderlichen Gebietsschema ändern.

## Best Practices zur Unterstützung neuer Lokalisierungen {#best-practices}

* Adobe empfiehlt, ein Übersetzungsprojekt erst nach dem Erstellen eines adaptiven Formulars durchzuführen.

* Wenn neue Felder in einem vorhandenen adaptiven Formular hinzugefügt werden:
   * **Für maschinelle Übersetzung**: Erstellen Sie das Wörterbuch neu und führen Sie das Übersetzungsprojekt aus. Felder, die einem adaptiven Formular nach dem Erstellen eines Übersetzungsprojekts hinzugefügt wurden, bleiben unübersetzt.
   * **Für die menschliche Übersetzung**: Exportieren Sie das Wörterbuch über `[server:port]/libs/cq/i18n/gui/translator.html`. Aktualisieren Sie das Wörterbuch für die neu hinzugefügten Felder und laden Sie es hoch.


## Siehe auch {#see-also}

{{see-also}}