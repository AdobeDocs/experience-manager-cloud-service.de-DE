---
title: Unterstützung neuer Gebietsschemas zum Lokalisieren von adaptiven Formularen
seo-title: Supporting new locales for Adaptive Forms localization
description: Mit AEM Forms können Sie neue Gebietsschemas zum Lokalisieren von adaptiven Formularen hinzufügen. Die unterstützten Gebietsschemas sind standardmäßig Englisch, Französisch, Deutsch und Japanisch.
seo-description: AEM Forms allows you to add new locales for localizing Adaptive Forms. The supported locales by default are English, French, German, and Japanese.
uuid: 7f9fab6b-8d93-46bb-8c7c-7b723d5159ea
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: d4e2acb0-8d53-4749-9d84-15b8136e610b
docset: aem65
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 100%

---


# Unterstützung neuer Gebietsschemas zum Lokalisieren von adaptiven Formularen{#supporting-new-locales-for-adaptive-forms-localization}

## Informationen zu Gebietsschema-Wörterbüchern {#about-locale-dictionaries}

Die Lokalisierung von adaptiven Formularen beruht auf zwei Arten von Gebietsschema-Wörterbüchern:

**Formularspezifisches Wörterbuch** Enthält Zeichenfolgen, die in adaptiven Formularen verwendet werden. Zum Beispiel Beschriftungen, Feldnamen, Fehlermeldungen, Hilfebeschreibungen usw. Wird für jedes Gebietsschema in Form eines Satzes von XLIFF-Dateien für die einzelnen Gebietsschemas verwaltet und ist unter `https://<host>:<port>/libs/cq/i18n/translator.html` verfügbar.

**Globale Wörterbücher** In der AEM-Client-Bibliothek gibt es zwei globale Wörterbücher, die als JSON-Objekte verwaltet werden. Diese Wörterbücher enthalten Standardfehlermeldungen, Monatsnamen, Währungssymbole, Datums- und Uhrzeitmuster usw. Diese Wörterbücher finden Sie in CRXDe Lite unter /libs/fd/xfaforms/clientlibs/I18N. Diese Speicherorte enthalten für jedes Gebietsschema separate Ordner. Da globale Wörterbücher in der Regel nicht oft aktualisiert werden, können Browser so separate JavaScript-Dateien für jedes Gebietsschema im Cache zwischenspeichern, was die Beanspruchung der Netzwerkbandbreite reduziert, wenn auf verschiedene adaptive Formulare auf demselben Server zugegriffen wird.

### So funktioniert die Lokalisierung von adaptiven Formularen {#how-localization-of-adaptive-form-works}

Es gibt zwei Methoden, das Gebietsschema eines adaptiven Formulars zu identifizieren. Wenn ein adaptives Formular dargestellt wird, wird das angeforderte Gebietsschema durch Folgendes identifiziert:

* Überprüfung der `[local]`-Auswahl in der URL des adaptiven Formulars. Das Format der URL ist `http://host:port/content/forms/af/[afName].[locale].html?wcmmode=disabled`. Mithilfe der `[local]`-Auswahl können adaptive Formulare zwischengespeichert werden.

* Überprüfung der folgenden Parameter in der angegebenen Reihenfolge:

   * Abfrageparameter `afAcceptLang`
Um das Browser-Gebietsschema von Benutzern zu überschreiben, können Sie den 
`afAcceptLang`-Abfrageparameter übergeben, um das Gebietsschema zu erzwingen. Beispielsweise erzwingt die folgende URL die Wiedergabe des Formulars im japanischen Gebietsschema:
      `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ja`

   * Das für den Benutzer festgelegte Browser-Gebietsschema, das in der Abfrage mit dem `Accept-Language`-Header angegeben ist.

   * Die in AEM angegebene Spracheinstellung des Benutzers.

   * Das Browser-Gebietsschema ist standardmäßig aktiviert. Gehen Sie wie folgt vor, um das im Browser eingestellte Gebietsschema zu ändern:
      * Öffnen Sie den Configuration Manager. Die URL lautet `http://[server]:[port]/system/console/configMgr`.
      * Suchen und öffnen Sie die Konfiguration **[!UICONTROL Webkanal für adaptive Formulare und Interaktive Kommunikation]**.
      * Ändern Sie den Status der Option **[!UICONTROL Browser-Gebietsschema verwenden]** und **[!UICONTROL speichern]** Sie die Konfiguration.

Sobald das Gebietsschema identifiziert ist, wählt das adaptive Formular das formularspezifische Wörterbuch aus. Wenn das formularspezifische Wörterbuch für das angeforderte Gebietsschema nicht gefunden wird, verwendet es das Wörterbuch für die Sprache, in der das adaptive Formular verfasst wurde.

Wenn keine Informationen zum Gebietsschema vorhanden sind, wird das adaptive Formular in der Originalsprache des Formulars übermittelt. Die Originalsprache ist die Sprache, die bei der Entwicklung des adaptiven Formulars verwendet wurde.

Wenn für das angeforderte Gebietsschema keine Client-Bibliothek vorhanden ist, wird nach einer Client-Bibliothek für den im Gebietsschema vorhandenen Sprach-Code gesucht. Beispiel: Wenn das angeforderte Gebietsschema `en_ZA` (Englisch (Südafrika)) lautet und die Client-Bibliothek für `en_ZA` nicht vorhanden ist, verwendet das adaptive Formular die Client-Bibliothek für `en` (Englisch), sofern vorhanden. Wenn jedoch keine davon vorhanden ist, verwendet das adaptive Formular das Wörterbuch für das Gebietsschema `en`.

## Hinzufügen von Lokalisierungsunterstützung für nicht unterstützte Gebietsschemas {#add-localization-support-for-non-supported-locales}

[!DNL AEM Forms] unterstützt die Lokalisierung von Inhalten adaptiver Formulare derzeit für die Gebietsschemas Englisch (en), Spanisch (es), Französisch (fr), Italienisch (it), Deutsch (de), Japanisch (ja), Portugiesisch – Brasilien (pt-BR), Chinesisch (zh-CN), Chinesisch – Taiwan (zh-TW) und Koreanisch (ko-KR).

So fügen Sie während der Laufzeit adaptiver Formulare Unterstützung für ein neues Gebietsschema hinzu:

1. [Hinzufügen eines Gebietsschemas zum GuideLocalizationService-Service](supporting-new-language-localization.md#p-add-a-locale-to-the-guide-localization-service-br-p)

1. [Hinzufügen der XFA-Client-Bibliothek für ein Gebietsschema](supporting-new-language-localization.md#p-add-xfa-client-library-for-a-locale-br-p)

1. [Hinzufügen der Client-Bibliothek für adaptive Formulare für ein Gebietsschema](supporting-new-language-localization.md#p-add-adaptive-form-client-library-for-a-locale-br-p)
1. [Hinzufügen von Gebietsschema-Unterstützung für das Wörterbuch](supporting-new-language-localization.md#p-add-locale-support-for-the-dictionary-br-p)
1. [Starten Sie den Server neu](supporting-new-language-localization.md#p-restart-the-server-p)

### Hinzufügen eines Gebietsschemas zum Guide-Localization-Service {#add-a-locale-to-the-guide-localization-service-br}

1. Rufen Sie `https://'[server]:[port]'/system/console/configMgr` auf.
1. Klicken Sie, um die Komponente **Guide-Localization-Service** zu bearbeiten.
1. Fügen Sie der Liste der unterstützen Gebietsschemas das gewünschte Gebietsschema hinzu.

![GuideLocalizationService](assets/configservice.png)

### Hinzufügen der XFA-Client-Bibliothek für ein Gebietsschema {#add-xfa-client-library-for-a-locale-br}

Erstellen Sie einen Knoten vom Typ `cq:ClientLibraryFolder` unter `etc/<folderHierarchy>` mit der Kategorie `xfaforms.I18N.<locale>` und fügen Sie der Client-Bibliothek die folgenden Dateien hinzu:

* **I18N.js**, die `xfalib.locale.Strings` für das `<locale>` definiert, wie in `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N` festgelegt.

* **js.txt**, die Folgendes enthält:

```text
/libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js
```

### Hinzufügen der Client-Bibliothek für adaptive Formulare für ein Gebietsschema {#add-adaptive-form-client-library-for-a-locale-br}

Erstellen Sie einen Knoten vom Typ `cq:ClientLibraryFolder` unter `etc/<folderHierarchy>` mit der Kategorie `guides.I18N.<locale>` und den Abhängigkeiten `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` und `guide.common`.

Fügen Sie die folgenden Dateien der Client-Bibliothek hinzu:

* **i18n.js** die `guidelib.i18n` definiert, mit Mustern von „calendarSymbols“, `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols`, `typefaces` für das `<locale>` gemäß den XFA-Spezifikationen, die in der [Spezifikation für Gebietsschema-Sätze](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf) beschrieben sind. Sie können auch sehen, wie sie für andere unterstützte Gebietsschemas in `/etc/clientlibs/fd/af/I18N/fr/javascript/i18n.js` definiert ist.
* **LogMessages.js**, die `guidelib.i18n.strings` und `guidelib.i18n.LogMessages` für das `<locale>` wie in `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js` festgelegt definiert.
* **js.txt**, die Folgendes enthält:

```text
i18n.js
LogMessages.js
```

### Hinzufügen von Gebietsschema-Unterstützung für das Wörterbuch {#add-locale-support-for-the-dictionary-br}

Führen Sie diesen Schritt nur dann durch, wenn das `<locale>`, das Sie hinzufügen möchten, nicht eines der Gebietsschemas `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja` oder `ko-kr` ist.

1. Erstellen Sie einen `nt:unstructured`-Knoten `languages` unter `etc`, falls nicht bereits vorhanden.

1. Falls noch nicht vorhanden, fügen Sie dem Knoten eine Eigenschaft `languages` vom Typ „Zeichenfolge“ hinzu, die mehrere Werte aufnehmen kann.
1. Fügen Sie die `<locale>`-Standardgebietsschema-Werte `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja` und `ko-kr` hinzu, falls noch nicht vorhanden.

1. Fügen Sie das `<locale>` den Werten der Eigenschaft `languages` von `/etc/languages` hinzu.

Das `<locale>` wird unter `https://'[server]:[port]'/libs/cq/i18n/translator.html` angezeigt.

### Starten Sie den Server neu {#restart-the-server}

Starten Sie den AEM-Server neu, damit das hinzugefügte Gebietsschema in Kraft tritt.

## Beispielbibliotheken für das Hinzufügen von Unterstützung für Spanisch {#sample-libraries-for-adding-support-for-spanish}

Client-Beispielbibliotheken für das Hinzufügen von Unterstützung für Spanisch

[Datei laden](assets/sample.zip)
