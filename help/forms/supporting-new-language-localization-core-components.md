---
title: Wie füge ich einem adaptiven Formular, das auf Kernkomponenten basiert, Unterstützung für neue Gebietsschemata hinzu?
description: Erfahren Sie, wie Sie neue Gebietsschemata für ein adaptives Formular hinzufügen.
feature: Adaptive Forms, Core Components
Role: Developer, Author
exl-id: bc06542b-84c8-4c6a-a305-effbd16d5630
role: User, Developer
source-git-commit: 8f39bffd07e3b4e88bfa200fec51572e952ac837
workflow-type: tm+mt
source-wordcount: '2154'
ht-degree: 98%

---

# Hinzufügen eines Gebietsschemas für auf Kernkomponenten basierende adaptive Formulare {#supporting-new-locales-for-adaptive-forms-localization}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| Foundation-Komponenten | [Hier klicken](supporting-new-language-localization.md) |
| Kernkomponenten | Dieser Artikel |

<span class="preview"> Die Unterstützungsfunktion für Sprachen von rechts nach links ist im Rahmen des Early-Adopter-Programms verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugang zu dieser Funktion zu beantragen. </span>

AEM Forms bietet vorkonfiguriert Unterstützung für die Gebietsschemata Englisch (en), Spanisch (es), Französisch (fr), Italienisch (it), Deutsch (de), Japanisch (ja), brasilianisches Portugiesisch (pt-BR), Chinesisch (zh-CN), Chinesisch – Taiwan (zh-TW) und Koreanisch (ko-KR). Sie können auch Unterstützung für weitere Gebietsschemata hinzufügen, wie Hindi (hi_IN). Sie können adaptive Formulare auch in einer RTL-Sprache (Right-to-Left, rechts nach links) wie Arabisch, Persisch und Urdu präsentieren, indem Sie diese Gebietsschemata hinzufügen.

>[!VIDEO](https://video.tv.adobe.com/v/3433132/adaptive-forms-rtl--arabic-hebrew-farsi)

## Anwendbarkeit und Anwendungsfälle

### Versicherung

## Unterstützt AEM Forms mehrsprachige Anwendungsfälle für Versicherungen?

Ja. AEM Forms unterstützt mehrsprachige Formularerlebnisse. Dies ist für Versicherer, die in verschiedenen Regionen und Sprachen arbeiten, wichtig.

## Wie bestimmt AEM Forms das Gebietsschema für ein adaptives Formular?

Die Auswahl des Gebietsschemas für die Wiedergabe eines adaptiven Formulars durch AEM Forms ist für eine ordnungsgemäße Lokalisierung von entscheidender Bedeutung. Im Folgenden finden Sie eine Aufschlüsselung des Auswahlprozesses:

### Prioritätsbasierte Gebietsschemaauswahl

AEM Forms priorisiert die folgenden Methoden zur Bestimmung des Gebietsschemas für ein adaptives Formular:

1. **URL-Gebietsschema-Auswahl ([locale])**:

   Das System priorisiert das in der URL angegebene Gebietsschema mithilfe der Auswahlmöglichkeit [locale]. Dieses Format ermöglicht die Zwischenspeicherung für eine bessere Leistung.

   Format: Die URL hat folgendes Format: http:/[AEM Forms-Server-URL]/content/forms/af/[afName].[locale].html?wcmmode=disabled.

   Beispiel: https://[server]/content/forms/af/contact-us.hi.html rendert das Formular in Hindi.


1. **Anfrageparameter „afAcceptLang“**:

   Um das Browser-Gebietsschema der Benutzerin bzw. des Benutzers zu überschreiben, können Sie den Parameter `afAcceptLang` in der URL verwenden.

   Beispiel: https://[server]/forms/af/survey.ca-fr.html?afAcceptLang=ca-fr erzwingt die Wiedergabe des Formulars auf kanadischem Französisch.

1. **Gebietsschema des Browsers der Benutzenden (Accept-Language-Header)**:

   Wenn kein anderes Gebietsschema angegeben ist, berücksichtigt AEM Forms das Gebietsschema des Browsers der Benutzenden, das über die Kopfzeile `Accept-Language` übermittelt wird.


### Ausweichmechanismus:


* Wenn eine Client-Bibliothek (Prozess zum Hinzufügen eines neuen Gebietsschemas, der später in diesem Dokument erläutert wird) für das angeforderte Gebietsschema nicht verfügbar ist, sucht AEM Forms anhand des Sprach-Codes im Gebietsschema nach einer Bibliothek.

  Beispiel: Wenn en_ZA (südafrikanisches Englisch) angefordert wird und keine en_ZA-Bibliothek vorhanden ist, wird en (Englisch) verwendet, sofern verfügbar.

  Wenn keine geeignete Client-Bibliothek gefunden wird, wird das Standardwörterbuch (meist `en`) für die Authoring-Sprache des Formulars verwendet.

  Wenn keine Gebietsschema-Informationen vorhanden sind, wird das adaptive Formular in der während der Entwicklung verwendeten Originalsprache angezeigt.


## Voraussetzungen für das Hinzufügen eines Gebietsschemas

Bevor Sie mit dem Hinzufügen eines neuen Gebietsschemas für Ihre adaptiven Formulare beginnen, stellen Sie Folgendes sicher:

**Software:**

* Nur-Text-Editor (IDE): Zwar kann jeder einfache Nur-Text-Editor verwendet werden, aber eine integrierte Entwicklungsumgebung (IDE) wie [Microsoft Visual Studio Code](https://code.visualstudio.com/download) bietet erweiterte Funktionen zur einfacheren Bearbeitung.

* Git: Dieses Versionskontrollsystem ist für die Verwaltung von Code-Änderungen erforderlich. Wenn Sie nicht über das Programm verfügen, laden Sie es von [https://git-scm.com](https://git-scm.com) herunter.


**Code-Repository:**

Klonen Sie das Repository der Kernkomponenten für adaptive Formulare: Sie benötigen eine Client-Bibliothek aus diesem Repository, um ein Gebietsschema hinzuzufügen. So klonen Sie das Repository:

1. Öffnen Sie die Befehlszeile oder ein Terminal-Fenster.

1. Navigieren Sie zum gewünschten Speicherort auf Ihrem Computer, auf dem Sie das Repository speichern möchten (z. B. /adaptive-forms-core-components).

1. Führen Sie den folgenden Befehl aus, um das Repository zu klonen:

   ```
   git clone https://github.com/adobe/aem-core-forms-components.git
   ```

   Mit diesem Befehl wird das Repository heruntergeladen und ein Ordner mit dem Namen `aem-core-forms-components` auf Ihrem Computer erstellt. In diesem Handbuch wird dieser Ordner als `[Adaptive Forms Core Components repository]` bezeichnet.


## Hinzufügen eines Gebietsschemas {#add-localization-support-for-non-supported-locales}

Gehen Sie wie folgt vor, um einem adaptiven Formular, das auf Kernkomponenten basiert, Unterstützung für neue Gebietsschemata hinzuzufügen:

### Klonen des Git-Repositorys von AEM as a Cloud Service

1. Öffnen Sie die Befehlszeile und wählen Sie einen Ordner zum Speichern des AEM as a Cloud Service-Repositorys aus, z. B. `/cloud-service-repository/`.

1. Führen Sie den folgenden Befehl aus, um das Repository zu klonen:

   ```SHELL
   git clone https://git.cloudmanager.adobe.com/<organization-name>/<program id>/
   ```

   Zum Klonen Ihres Git-Repositorys benötigen Sie einige Informationen:

   * **Organisationsname**: Identifiziert Ihr Team oder Projekt in Adobe Experience Manager as a Cloud Service (AEM as a Cloud Service).

   * **Programm-ID**: Gibt das mit Ihrem Repository verknüpfte Programm an.

   * **Anmeldeinformationen**: Sie benötigen einen Benutzernamen und ein Kennwort (oder ein persönliches Zugriffstoken), um sicher auf das Repository zugreifen zu können.

   **Wo finden Sie diese Informationen?**

   Eine schrittweise Anleitung zum Auffinden dieser Details finden Sie im Adobe Experience League-Artikel [Zugriff auf Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git).

   **Ihr Projekt ist bereit.**

   Wenn der Befehl erfolgreich abgeschlossen wurde, wird in Ihrem lokalen Verzeichnis ein neuer Ordner erstellt. Dieser Ordner wird nach Ihrem Programm benannt (z. B. program-id). Dieser Ordner enthält alle Dateien und den Code, die von Ihrem AEM as a Cloud Service-Git-Repository heruntergeladen wurden.

   In diesem Handbuch wird dieser Ordner als `[AEMaaCS project directory]` bezeichnet.


### Hinzufügen eines Gebietsschemas zum Handbuch-Lokalisierungsdienst

1. Öffnen Sie den Repository-Ordner in einem Editor.

   ![Repository-Ordner in einem Editor](/help/forms/assets/repository-folder-in-an-editor.png)

1. Suchen Sie die Datei `Guide Localization Service.cfg.json`. Diese Datei steuert die von Ihrer AEM Forms-Anwendung unterstützten Gebietsschemata. Sie können diese Datei bearbeiten, um ein neues Gebietsschema hinzuzufügen.

   * **Vorhandene Datei**: Wenn die Datei bereits vorhanden ist, suchen Sie sie in Ihrem AEM Forms-Projektverzeichnis. Der Standardspeicherort lautet:

     ```Shell
     [AEMaaCS project directory]/ui.config/src/main/content/jcr_root/apps/<appid>/osgiconfig/config`. 
     ```

     Ersetzen Sie `<appid>` mit Ihrer projektspezifischen Anwendungs-ID. Sie finden `<appid>` für Ihr AEM-Projekt in der Datei `archetype.properties`.

     ![Archetyp-Eigenschaften](/help/forms/assets/archetype-properties.png)

   * **Neue Datei**: Wenn die Datei nicht vorhanden ist, müssen Sie sie an dem gleichen oben genannten Speicherort erstellen. Kopieren Sie den Dateinamen nicht aus diesem Dokument, sondern geben Sie ihn manuell ein. Der Dateiname `Guide Localization Service.cfg.json` enthält Leerzeichen. Dies ist beabsichtigt und kein Tippfehler in der Dokumentation.

     Eine Beispieldatei mit der Liste der vorkonfigurierten unterstützten Gebietsschemata ist:

     ```
         {
             "supportedLocales":[
             "en",
             "fr",
             "de",
             "ja",
             "pt-br",
             "zh-cn",
             "zh-tw",
             "ko-kr",
             "it",
             "es"
             ]
         }
     ```

1. Fügen Sie der Datei den Gebietsschema-Code für die gewünschte Sprache hinzu.
   1. Suchen Sie anhand der [Liste der ISO 639-1-Codes](https://de.wikipedia.org/wiki/Liste_der_ISO-639-Sprachcodes) den aus zwei Buchstaben bestehenden Code, der die gewünschte Sprache darstellt.

   1. Fügen Sie den Gebietsschema-Code zur Datei `Guide Localization Service.cfg.json` hinzu. Im Folgenden einige Beispiele:

      * Sprachen mit Links-nach-rechts-Schreibrichtung:
         * Englisch (Vereinigte Staaten): en-US
         * Spanisch (Spanien): es-ES
         * Französisch (Frankreich): fr-FR
      * Sprachen mit Rechts-nach-links-Schreibrichtung:
         * Arabisch (Vereinigte Arabische Emirate): ar-ae
         * Hebräisch: he (oder iw als historische Referenz)
         * Farsi: fa

1. Stellen Sie nach den Änderungen sicher, dass die Datei `Guide Localization Service.cfg.json` korrekt als gültige JSON-Datei formatiert ist. Fehler in der JSON-Formatierung können das ordnungsgemäße Funktionieren verhindern. Speichern Sie die Datei.



### Nutzen der Beispiel-Client-Bibliothek zum einfachen Hinzufügen von Gebietsschemata

AEM Forms bietet eine hilfreiche Beispiel-Client-Bibliothek namens `clientlib-it-custom-locale`, die das Hinzufügen neuer Gebietsschemata vereinfacht. Diese Bibliothek ist Teil des [Repositorys für adaptive Formular-Kernkomponenten](https://github.com/adobe/aem-core-forms-components), verfügbar auf GitHub.


Bevor wir beginnen, stellen Sie sicher, dass Sie über eine lokale Kopie der [Repositorys für adaptive Formular-Kernkomponenten] verfügen. Wenn nicht, können Sie sie einfach mithilfe von Git mit dem folgenden Befehl klonen:

```SHELL
git clone https://github.com/adobe/aem-core-forms-components.git
```

Mit diesem Befehl wird das gesamte Repository, einschließlich der Bibliothek clientlib-it-custom-locale, in einen Ordner mit dem Namen „aem-core-forms-components“ auf Ihrem Computer heruntergeladen.

![Repository-Verzeichnis für adaptive Formular-Kernkomponenten auf einem lokalen Computer](/help/forms/assets/core-forms-components-repo-on-local-machine.png)

### Integrieren der Beispiel-Client-Bibliothek

Lassen Sie uns nun die `clientlib-it-custom-locale`-Bibliothek in Ihr AEM as a Cloud Service [AEMaaCS-Projektverzeichnis] einbinden:

1. Lokalisieren Sie die Beispiel-Client-Bibliothek:

   Navigieren Sie in Ihrer lokalen Kopie des [Repositorys für adaptive Formular-Kernkomponenten] zum folgenden Pfad:

   ```
       /aem-core-forms-components/it/apps/src/main/content/jcr_root/apps/forms-core-components-it/clientlibs
   ```

1. Kopieren Sie die Bibliothek und fügen Sie sie ein:

   1. Kopieren Sie den Ordner `clientlib-it-custom-locale`:

      ![Kopieren von clientlib-it-custom-locale](/help/forms/assets/clientlib-it-custom-locale-copy.png)

   1. Wechseln Sie in das folgende Verzeichnis in Ihrem [AEMaaCS-Projektverzeichnis]:

      ```
      /ui.apps/src/main/content/jcr_root/apps/<app-id>/clientlib
      ```

      **Wichtig**: Ersetzen Sie `<app-id>` durch die tatsächliche ID Ihrer Anwendung.

   1. Fügen Sie den kopierten Ordner `clientlib-it-custom-locale` in dieses Verzeichnis ein.

      ![Einfügen von clientlib-it-custom-locale](/help/forms/assets/clientlib-it-custom-locale-paste.png)

1. Aktualisieren des Pfads `aemLangUrl` in `languageinit.js`

   1. Wechseln Sie in das folgende Verzeichnis in Ihrem [AEMaaCS-Projektverzeichnis]:

      ```
      /ui.apps/src/main/content/jcr_root/apps/<app-id>/clientlib/clientlib-it-custom-locale/js
      ```

   1. Öffnen Sie die Datei `languageinit.js` in ihrem Editor.
   1. Suchen Sie die folgende Zeile in der Datei `languageinit.js`:

      `const aemLangUrl = /etc.clientlibs/forms-core-components-it/clientlibs/clientlib-it-custom-locale/resources/i18n/${lang}.json;`

   1. Ersetzen Sie `forms-core-components-it` durch Ihre `<app-id>` (die tatsächliche ID Ihrer Anwendung) in der obigen Zeile.

      `const aemLangUrl = '/etc.clientlibs/<app-id>/clientlibs/clientlib-it-custom-locale/resources/i18n/${lang}.json';`

      ![language-init-file](/help/forms/assets/language-init-name-change.png)

>[!NOTE]
>  
> Wenn Sie `forms-core-components-it` nicht durch Ihren Projektnamen oder `<app-id>` ersetzen, kann die Datumsauswahlkomponente nicht übersetzt werden.

### Erstellen Sie eine Datei für Ihr neues Gebietsschema:

1. Navigieren Sie zum Verzeichnis Ihres Gebietsschemas:

   Navigieren Sie innerhalb Ihres `[AEMaaCS project directory]` zu folgendem Pfad:

   ```
       /ui.apps/src/main/content/jcr_root/apps/<program-id>/clientlibs/clientlib-it-custom-locale/resources/i18n/
   ```

   **Wichtig**: Ersetzen Sie `<program-id>` durch Ihre tatsächliche Anwendungs-ID.

1. Suchen Sie die englischsprachige Beispieldatei:

   AEM Forms stellt auf GitHub](https://github.com/adobe/aem-core-forms-components/blob/master/ui.af.apps/src/main/content/jcr_root/apps/core/fd/af-clientlibs/core-forms-components-runtime-all/resources/i18n/en.json) eine [beispielhafte englische Gebietsschema-Datei (.json) zur Verfügung.

   Die englische Sprachdatei enthält den Standardsatz von Zeichenfolgen als Referenz. Ihre gebietsschemaspezifische Datei sollte die Struktur der englischsprachigen Datei imitieren.

   In Sprachen wie Arabisch, Hebräisch und Farsi wird der Text von rechts nach links (RTL) und nicht wie im Englischen von links nach rechts (LTR) geschrieben. Um sicherzustellen, dass Ihre Formulare in diesen Sprachen korrekt angezeigt werden, empfehlen wir die Verwendung unserer Gebietsschema-Beispieldateien als Anleitung. Diese Dateien bieten eine Referenz für die Formatierung von Text, Daten und anderen Elementen für RTL-Sprachen. Sie finden Beispiele für Gebietsschemadateien für:

   * [Arabisch](/help/forms/assets/ar-ae.json)
   * [Hebräisch](/help/forms/assets/he.json)
   * [Farsi](/help/forms/assets/fa.json)

   Mit Hilfe dieser Beispieldateien können Sie sicherstellen, dass Ihre Formulare Benutzenden, die in RTL-Sprachen arbeiten, ein nahtloses Erlebnis bieten.


1. Erstellen Sie Ihre Gebietsschema-Datei:

   1. Erstellen Sie eine neue .json-Datei im Verzeichnis `i18n`.
   1. Benennen Sie die Datei mit dem entsprechenden Gebietsschema-Code für die gewünschte Sprache (z. B. fr-FR.json für Französisch und ar-ae.json für Arabisch). Die Struktur dieser Datei sollte die englische Gebietsschema-Datei widerspiegeln.


1. Struktur und Übersetzung:

   1. Öffnen Sie die neu erstellte Datei in einem Texteditor.

   1. Ersetzen Sie die englischen Werte durch die entsprechenden Übersetzungen für Ihre Zielsprache.

   1. Nachdem Sie mit der Übersetzung der Strings fertig sind, speichern Sie die Datei.




### Hinzufügen von Gebietsschema-Unterstützung zum Wörterbuch

Dieser Schritt gilt nur für andere Gebietsschemata als die folgenden, häufig unterstützten Sprachen: Englisch (en), Deutsch (de), Spanisch (es), Französisch (fr), Italienisch (it), brasilianisches Portugiesisch (pt-br), Chinesisch (vereinfacht – zh_cn), Chinesisch (traditionell – zh_tw), Japanisch (ja) und Koreanisch (ko_kr).

1. Lokalisieren Sie den Konfigurationsordner:

   Wechseln Sie in das folgende Verzeichnis in Ihrem [AEMaaCS-Projektverzeichnis]:

   ```
   /ui.content/src/main/content/jcr_root/etc
   ```

1. Erstellen Sie die erforderlichen Ordner (falls noch nicht vorhanden):

   Wenn der Ordner `etc` im Ordner `jcr_root` nicht vorhanden ist, erstellen Sie ihn. Erstellen Sie innerhalb von `etc` einen weiteren Ordner mit dem Namen `languages`, falls dieser noch nicht vorhanden ist.

1. Erstellen Sie die Konfigurationsdatei des Gebietsschemas:

   Erstellen Sie im Ordner `languages` eine neue Datei namens `.content.xml`. Kopieren Sie den Dateinamen nicht aus diesem Dokument, sondern geben Sie ihn manuell ein.

   ![Erstellen Sie eine neue Datei namens `.content.xml`](etc-content-xml.png)

   Öffnen Sie diese Datei und fügen Sie den folgenden Inhalt ein. Ersetzen Sie dabei [LOCALE_CODE] durch den tatsächlichen Gebietsschema-Code (zum Beispiel ar-ae für Arabisch).


   ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
         jcr:primaryType="nt:unstructured"
         languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr,hi]"/>
   ```

   WARNUNG: Ersetzen Sie nicht die vorhandene Liste. Hängen Sie stattdessen Ihren neuen Gebietsschema-Code in eckigen Klammern und durch Kommas getrennt an, wie z. B. (unter Verwendung von ar-ae als Beispiel):

   ```XML
   languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr,hi,ar-ae]"
   ```

1. Schließen Sie die neuen Ordner in filter.xml ein:

   Navigieren Sie zur Datei `/ui.content/src/main/content/meta-inf/vault/filter.xml` in Ihrem [AEMaaCS-Projektverzeichnis].

   Öffnen Sie die Datei und fügen Sie die folgende Zeile am Ende ein:

   ```
   <filter root="/etc/languages"/>
   ```

   ![Fügen Sie die erstellten Ordner in `filter.xml` unter `/ui.content/src/main/content/meta-inf/vault/filter.xml`](langauge-filter.png) hinzu

1. Speichern Sie die Datei.

### Bereitstellen des neu erstellten Gebietsschemas in Ihrer AEM-Umgebung

Sie sind nun bereit, das neue Gebietsschema mit Ihren adaptiven Formularen zu verwenden. Sie haben folgende Möglichkeiten:

* Bereitstellung des [AEMaaCS-Projektverzeichnisses] von AEM as a Cloud Service, um die neue Gebietsschema-Konfiguration auf Ihrem lokalen Computer auszuprobieren. Für die Bereitstellung in Ihrer lokalen Entwicklungsumgebung:

   1. Stellen Sie sicher, dass Ihre lokale Entwicklungsumgebung betriebsbereit ist. Wenn Sie noch keine lokale Entwicklungsumgebung eingerichtet haben, lesen Sie die Anleitung [Einrichten einer lokalen Entwicklungsumgebung für AEM Forms](/help/forms/setup-local-development-environment.md).

   1. Öffnen Sie das Terminal-Fenster oder eine Eingabeaufforderung.

   1. Navigieren Sie zum [AEMaaCS-Projektverzeichnis]

   1. Führen Sie den folgenden Befehl aus:

      ```
      mvn -PautoInstallPackage clean install
      ```

* Stellen Sie das [AEMaaCS Projektverzeichnis] von AEM as a Cloud Service in Ihrer Cloud Service-Umgebung bereit. So stellen Sie es in Ihrer Cloud Service-Umgebung bereit:

   1. Bestätigen Sie Ihre Änderungen:

      Nachdem Sie die neue Gebietsschema-Konfiguration hinzugefügt haben, übergeben Sie Ihre Änderungen mit einer eindeutigen Git-Meldung, die die Hinzufügung des Gebietsschemas beschreibt (z. B. „Unterstützung für [Gebietsschema-Name] hinzugefügt“).

   1. So stellen Sie den Beispiel-Code bereit:

      Lösen Sie eine Bereitstellung Ihres Codes durch die [vorhandene Full-Stack-Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline) aus. Dadurch wird automatisch der aktualisierte Code mit der neuen Gebietsschema-Unterstützung erstellt und bereitgestellt.

      Wenn Sie noch keine Pipeline eingerichtet haben, lesen Sie das Handbuch zur [Einrichtung einer Pipeline für AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline).


## Vorschau eines adaptiven Formulars mit dem neu hinzugefügten Gebietsschema

Diese folgenden Schritte führen Sie durch die Vorschau eines adaptiven Formulars mit dem neu hinzugefügten Gebietsschema:

1. Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Instanz an.
1. Gehen Sie zu **Formulare** > **Formulare und Dokumente**.
1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **Wörterbuch hinzufügen**. Daraufhin wird der Assistent **Wörterbuch zum Übersetzungsprojekt hinzufügen** geöffnet.
1. Geben Sie den **Projekttitel** an und wählen Sie die **Zielsprachen** aus dem Dropdown-Menü im Assistenten **Wörterbuch zum Übersetzungsprojekt hinzufügen**.
1. Klicken auf **Fertig** und führen Sie das erstellte Übersetzungsprojekt aus.
1. Gehen Sie zu **Formulare** > **Formulare und Dokumente**.
1. Wählen Sie das adaptive Formular und wählen Sie die Option **Vorschau als HTML**.
1. Hängen Sie `&afAcceptLang=<locale-name>` an die Vorschau-URL an und drücken Sie die Eingabetaste. Ersetzen Sie `<locale-name>` durch Ihren tatsächlichen Gebietsschema-Code. Das adaptive Formular wird in dem angegebenen Gebietsschema angezeigt.

## Best Practices zur Unterstützung neuer Lokalisierungen {#best-practices}

* Adobe empfiehlt, ein Übersetzungsprojekt erst nach dem Erstellen eines adaptiven Formulars durchzuführen. Dadurch wird der Lokalisierungsprozess optimiert.
* Wenn die Komponenten „Numerisches Feld“ und „Datumsauswahl“ in ein bestimmtes Gebietsschema übersetzt werden, kann es zu Formatierungsproblemen kommen. Um diese zu reduzieren, wurde eine Option **Sprache** in das Dialogfeld „Konfigurieren“ der [Komponente „Datumsauswahl“](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/date-picker#format-tab) und [Komponente „Numerisches Feld“](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/numeric-box#formats-configure-tab) eingefügt.


* Umgang mit neuen Feldern:

   * **Maschinelle Übersetzung**: Wenn Sie die maschinelle Übersetzung verwenden, müssen Sie das Wörterbuch neu erstellen und das [Übersetzungsprojekt neu starten](/help/forms/using-aem-translation-workflow-to-localize-adaptive-forms-core-components.md), nachdem Sie neue Felder zu einem bestehenden adaptiven Formular hinzugefügt haben. Neue Felder, die nach dem ersten Übersetzungsprojekt hinzugefügt werden, bleiben unübersetzt.

   * **Menschliche Übersetzung**: Für Workflows mit menschlicher Übersetzung exportieren Sie das Wörterbuch über die Benutzeroberfläche unter `[AEM Forms Server]/libs/cq/i18n/gui/translator.html`. Aktualisieren Sie das Wörterbuch für die neuen Felder und laden Sie die überarbeitete Version hoch.


## Siehe auch {#see-also}

{{see-also}}

* [Generieren eines Datensatzdokuments für adaptive Formulare](/help/forms/generate-document-of-record-core-components.md)
* [Hinzufügen eines adaptiven Formulars zu einer AEM Sites-Seite oder einem Experience Fragment](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)

