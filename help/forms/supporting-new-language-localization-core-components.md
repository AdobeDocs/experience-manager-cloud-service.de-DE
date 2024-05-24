---
title: Wie füge ich einem adaptiven Formular, das auf Kernkomponenten basiert, Unterstützung für neue Gebietsschemata hinzu?
description: Erfahren Sie, wie Sie neue Gebietsschemata für ein adaptives Formular hinzufügen.
feature: Adaptive Forms, Core Components
Role: Developer, Author
exl-id: bc06542b-84c8-4c6a-a305-effbd16d5630
source-git-commit: 9cb3b52d0cf172c16777eadbc4d78b267c3db513
workflow-type: tm+mt
source-wordcount: '2028'
ht-degree: 12%

---

# Hinzufügen eines Gebietsschemas für auf Kernkomponenten basierende adaptive Formulare {#supporting-new-locales-for-adaptive-forms-localization}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| Foundation-Komponenten | [Hier klicken](supporting-new-language-localization.md) |
| Kernkomponenten | Dieser Artikel |

<span class="preview"> Die Sprachunterstützungsfunktion von rechts nach links ist im Rahmen des Programms für frühe Anwender verfügbar. Sie können von Ihrer offiziellen E-Mail-Adresse aus an aem-forms-ea@adobe.com schreiben, um dem Early-Adopter-Programm beizutreten und den Zugang zu dieser Funktion zu beantragen. </span>

AEM Forms bietet vorkonfiguriert Unterstützung für die Gebietsschemata Englisch (en), Spanisch (es), Französisch (fr), Italienisch (it), Deutsch (de), Japanisch (ja), brasilianisches Portugiesisch (pt-BR), Chinesisch (zh-CN), Chinesisch – Taiwan (zh-TW) und Koreanisch (ko-KR). Sie können auch Unterstützung für weitere Gebietsschemata hinzufügen, wie Hindi (hi_IN). Sie können adaptive Formulare auch in einer RTL-Sprache (Right-to-Left, rechts nach links) wie Arabisch, Persisch und Urdu präsentieren, indem Sie diese Gebietsschemata hinzufügen.

## Wie bestimmt AEM Forms das Gebietsschema für ein adaptives Formular?

Die Auswahl des Gebietsschemas für die Wiedergabe eines adaptiven Formulars durch AEM Forms ist für eine ordnungsgemäße Lokalisierung von entscheidender Bedeutung. Im Folgenden finden Sie eine Aufschlüsselung des Auswahlprozesses:

### Prioritätsbasierte Gebietsschemaauswahl

AEM Forms priorisiert die folgenden Methoden zur Bestimmung des Gebietsschemas für ein adaptives Formular:

1. **URL-Gebietsschema-Auswahl ([locale])**:

   Das System priorisiert das in der URL angegebene Gebietsschema mithilfe der [locale] auswählen. Dieses Format ermöglicht die Zwischenspeicherung für eine bessere Leistung.

   Format: Die URL hat folgendes Format: http:/[AEM Forms-Server-URL]/content/forms/af/[afName].[locale].html?wcmmode=disabled.

   Beispiel: https://[server]/content/forms/af/contact-us.hi.html rendert das Formular in Hindi.


1. **afAcceptLang-Anforderungsparameter**:

   Um das Browsergebietsschema des Benutzers zu überschreiben, können Sie die `afAcceptLang` in der URL.

   Beispiel: https://[server]/forms/af/survey.ca-fr.html?afAcceptLang=ca-fr erzwingt die Wiedergabe des Formulars auf kanadischem Französisch.

1. **Gebietsschema des Browsers des Benutzers (Accept-Language-Header)**:

   Wenn kein anderes Gebietsschema angegeben ist, berücksichtigt AEM Forms das Browser-Gebietsschema des Benutzers, das mit der `Accept-Language` -Kopfzeile.


### Ausweichmechanismus:


* Wenn eine Client-Bibliothek (Prozess zum Hinzufügen eines neuen Gebietsschemas, der später in diesem Dokument erläutert wird) für das angeforderte Gebietsschema nicht verfügbar ist, sucht AEM Forms anhand des Sprachcodes im Gebietsschema nach einer Bibliothek.

  Beispiel: Wenn en_ZA (Südafrikanisches Englisch) angefordert wird und keine en_ZA-Bibliothek vorhanden ist, wird en (Englisch) verwendet, sofern verfügbar.

  Wenn keine geeignete Client-Bibliothek gefunden wird, wird das Standardwörterbuch (meist `en`) für die Authoring-Sprache des Formulars verwendet wird.

  Wenn keine Sprachinformationen vorhanden sind, wird das adaptive Formular in der während der Entwicklung verwendeten Originalsprache angezeigt.


## Voraussetzungen für das Hinzufügen eines Gebietsschemas

Bevor Sie mit dem Hinzufügen eines neuen Gebietsschemas für Ihre adaptive Forms beginnen, stellen Sie Folgendes sicher:

**Software:**

* Nur-Text-Editor (IDE): Während jeder Nur-Text-Editor funktionieren kann, kann eine integrierte Entwicklungsumgebung (IDE) wie [Microsoft Visual Studio Code](https://code.visualstudio.com/download) bietet erweiterte Funktionen zur einfacheren Bearbeitung.

* Git: Dieses Versionskontrollsystem ist für die Verwaltung von Code-Änderungen erforderlich. Wenn Sie es nicht installiert haben, laden Sie es von herunter [https://git-scm.com](https://git-scm.com).


**Code-Repository:**

Klonen Sie das Repository der adaptiven Forms-Kernkomponenten: Sie benötigen eine Client-Bibliothek aus diesem Repository, um ein Gebietsschema hinzuzufügen. So klonen Sie das Repository:

1. Öffnen Sie die Befehlszeile oder das Terminal-Fenster.

1. Navigieren Sie zum gewünschten Speicherort auf Ihrem Computer, auf dem Sie das Repository speichern möchten (z. B. /adaptive-forms-core-components).

1. Führen Sie den folgenden Befehl aus, um das Repository zu klonen:

   ```
   git clone https://github.com/adobe/aem-core-forms-components.git
   ```

   Mit diesem Befehl wird das Repository heruntergeladen und ein Ordner mit dem Namen `aem-core-forms-components` auf Ihrem Computer. In diesem Handbuch wird dieser Ordner als `[Adaptive Forms Core Components repository]`


## Hinzufügen eines Gebietsschemas {#add-localization-support-for-non-supported-locales}

Gehen Sie wie folgt vor, um einem adaptiven Formular, das auf Kernkomponenten basiert, Unterstützung für neue Gebietsschemata hinzuzufügen:

### Klonen Sie Ihr AEM as a Cloud Service Git-Repository

1. Öffnen Sie die Befehlszeile und wählen Sie einen Ordner aus, in dem Sie Ihr AEM as a Cloud Service Repository speichern möchten, z. B. `/cloud-service-repository/`.

1. Führen Sie den folgenden Befehl aus, um das Repository zu klonen:

   ```SHELL
   git clone https://git.cloudmanager.adobe.com/<organization-name>/<program id>/
   ```

   Zum Klonen Ihres Git-Repositorys benötigen Sie einige Informationen:

   * **Organisationsname**: Identifiziert Ihr Team oder Projekt in Adobe Experience Manager as a Cloud Service (AEM as a Cloud Service).

   * **Programm-ID**: Gibt das mit Ihrem Repository verknüpfte Programm an.

   * **Anmeldeinformationen**: Sie benötigen einen Benutzernamen und ein Kennwort (oder ein persönliches Zugriffstoken), um sicher auf das Repository zugreifen zu können.

   **Wo finden Sie diese Informationen?**

   Eine schrittweise Anleitung zum Auffinden dieser Details finden Sie im Adobe Experience League-Artikel &quot;[Zugriff auf Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git)&quot;.

   **Ihr Projekt ist fertig!**

   Wenn der Befehl erfolgreich abgeschlossen wurde, wird in Ihrem lokalen Verzeichnis ein neuer Ordner erstellt. Dieser Ordner wird nach Ihrem Programm benannt (z. B. program-id). Dieser Ordner enthält alle Dateien und den Code, die von Ihrem AEM as a Cloud Service Git-Repository heruntergeladen wurden.

   In diesem Handbuch wird dieser Ordner als `[AEMaaCS project directory]`.


### Hinzufügen des neuen Gebietsschemas zum Guide Localization Service

1. Öffnen Sie den Repository-Ordner in einem Editor.

   ![Repository-Ordner in einem Editor](/help/forms/assets/repository-folder-in-an-editor.png)

1. Suchen Sie die `Guide Localization Service.cfg.json` -Datei. Diese Datei steuert die von Ihrer AEM Forms-Anwendung unterstützten Gebietsschemata. Sie können diese Datei bearbeiten, um ein neues Gebietsschema hinzuzufügen.

   * **Vorhandene Datei**: Wenn die Datei bereits vorhanden ist, suchen Sie sie in Ihrem AEM Forms-Projektverzeichnis. Der typische Ort lautet:

     ```Shell
     [AEMaaCS project directory]/ui.config/src/main/content/jcr_root/apps/<appid>/osgiconfig/config`. 
     ```

     Ersetzen `<appid>` mit Ihrer projektspezifischen App-ID. Sie finden `<appid>` für Ihr AEM Projekt in `archetype.properties` -Datei.

     ![Archetyp-Eigenschaften](/help/forms/assets/archetype-properties.png)

   * **Neue Datei**: Wenn die Datei nicht vorhanden ist, müssen Sie sie an dem oben genannten Speicherort erstellen. Kopieren Sie nicht den Namen der Datei aus diesem Dokument, sondern geben Sie manuell den Namen ein. Der Dateiname `Guide Localization Service.cfg.json` enthält Leerzeichen. Dies ist beabsichtigt und kein Tippfehler in der Dokumentation.

     Eine Beispieldatei mit der Liste der von OOTB unterstützten Gebietsschemata ist:

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
   1. Verwenden Sie die [Liste der ISO 639-1-Codes](https://en.wikipedia.org/wiki/List_of_ISO_639_language_codes) , um den aus zwei Buchstaben bestehenden Code zu finden, der Ihre gewünschte Sprache darstellt.

   1. Gebietsschema-Code in die `Guide Localization Service.cfg.json` -Datei. Im Folgenden finden Sie einige Beispiele:

      * Sprachen von links nach rechts:
         * Englisch (USA): en-US
         * Spanisch (Spanien): es-ES
         * Französisch (Frankreich): fr-FR
      * Sprachen mit Rechts-nach-links-Schreibrichtung:
         * Arabisch (Vereinigte Arabische Emirate): ar-ae
         * Hebräisch: er (oder iw als historische Referenz)
         * Farsi: fa

1. Stellen Sie nach den Änderungen sicher, dass die `Guide Localization Service.cfg.json` korrekt als gültige JSON-Datei formatiert ist. Fehler in der JSON-Formatierung können die ordnungsgemäße Funktionsweise verhindern. Speichern Sie die Datei.



### Nutzen Sie die Beispiel-Client-Bibliothek für einfache Gebietsschema-Hinzufügung

AEM Forms bietet eine hilfreiche Beispiel-Client-Bibliothek, `clientlib-it-custom-locale`, um das Hinzufügen neuer Gebietsschemata zu vereinfachen. Diese Bibliothek ist Teil der [Adaptives Forms-Kernkomponenten-Repository](https://github.com/adobe/aem-core-forms-components), verfügbar auf GitHub.


Bevor wir beginnen, stellen Sie sicher, dass Sie über eine lokale Kopie der [Adaptives Forms-Kernkomponenten-Repository]. Wenn nicht, können Sie es einfach mithilfe von Git mit dem folgenden Befehl klonen:

```SHELL
git clone https://github.com/adobe/aem-core-forms-components.git
```

Mit diesem Befehl wird das gesamte Repository, einschließlich der clientlib-it-custom-locale -Bibliothek, in einen Ordner mit dem Namen aem-core-forms-components auf Ihrem Computer heruntergeladen.

![Repository-Ordner für adaptive Forms-Kernkomponenten auf einem lokalen Computer](/help/forms/assets/core-forms-components-repo-on-local-machine.png)

### Integrieren der Beispiel-Client-Bibliothek

Nehmen wir nun die `clientlib-it-custom-locale` -Bibliothek in Ihren AEM as a Cloud Service [AEMaaCS-Projektverzeichnis]:

1. Suchen Sie die Beispiel-Client-Bibliothek:

   In Ihrer lokalen Kopie der [Adaptives Forms-Kernkomponenten-Repository], navigieren Sie zum folgenden Pfad:

   ```
       /aem-core-forms-components/it/apps/src/main/content/jcr_root/apps/forms-core-components-it/clientlibs
   ```

1. Kopieren Sie die Bibliothek und fügen Sie sie ein:

   1. Kopieren Sie die `clientlib-it-custom-locale` Ordner.

      ![Kopieren von clientlib-it-custom-locale](/help/forms/assets/clientlib-it-custom-locale-copy.png)

   1. Navigieren Sie zum folgenden Verzeichnis in Ihrem [AEMaaCS-Projektverzeichnis]:

      ```
      /ui.apps/src/main/content/jcr_root/apps/<app-id>/clientlib
      ```

      **Wichtig**: Replace `<app-id>` mit der tatsächlichen Kennung Ihrer Anwendung.

   1. Kopieren `clientlib-it-custom-locale` in diesen Ordner.

      ![Einfügen von clientlib-it-custom-locale](/help/forms/assets/clientlib-it-custom-locale-paste.png)


### Erstellen Sie eine Datei für Ihr neues Gebietsschema:

1. Navigieren Sie zum Verzeichnis &quot;Locale&quot;:

   Innerhalb von `[AEMaaCS project directory]`, navigieren Sie zum folgenden Pfad:

   ```
       /ui.apps/src/main/content/jcr_root/apps/<program-id>/clientlibs/clientlib-it-custom-locale/resources/i18n/
   ```

   **Wichtig**: Replace `<program-id>` mit Ihrer eigentlichen Anwendungs-ID.

1. Suchen Sie die englischsprachige Beispieldatei:

   AEM Forms bietet eine [Beispiel für eine englische Gebietsschemadatei (.json) auf GitHub](https://github.com/adobe/aem-core-forms-components/blob/master/ui.af.apps/src/main/content/jcr_root/apps/core/fd/af-clientlibs/core-forms-components-runtime-all/resources/i18n/en.json).

   Die englische Sprachdatei enthält den Standardsatz von Zeichenfolgen, die referenziert werden sollen. Ihre gebietsschemaspezifische Datei sollte die Struktur der englischsprachigen Datei imitieren.

   In Sprachen wie Arabisch, Hebräisch und Farsi wird Text von rechts nach links (RTL) anstatt von links nach rechts (LTR) wie Englisch gelesen. Um sicherzustellen, dass Ihre Formulare in diesen Sprachen korrekt angezeigt werden, empfehlen wir die Verwendung unserer Gebietsschema-Beispieldateien als Anleitung. Diese Dateien enthalten eine Referenz zum Formatieren von Text, Daten und anderen Elementen für RTL-Sprachen. Sie finden Beispiele für Gebietsschemadateien für:

   * [Arabisch](/help/forms/assets/ar-ae.json)
   * [Hebräisch](/help/forms/assets/he.json)
   * [Farsi](/help/forms/assets/fa.json)

   Mithilfe dieser Beispieldateien können Sie sicherstellen, dass Ihre Formulare Benutzern, die in RTL-Sprachen arbeiten, eine nahtlose Arbeit ermöglichen.


1. Erstellen Sie Ihre Gebietsschema-Datei:

   1. Erstellen Sie eine neue JSON-Datei im `i18n` Verzeichnis.
   1. Benennen Sie die Datei mit dem entsprechenden Gebietsschema-Code für die gewünschte Sprache (z. B. fr-FR.json für Französisch und ar-ae.json für Arabisch). Die Struktur dieser Datei sollte die englische Gebietsschema-Datei widerspiegeln.


1. Struktur und Übersetzung:

   1. Öffnen Sie die neu erstellte Datei in einem Texteditor.

   1. Ersetzen Sie die englischen Werte durch die entsprechenden Übersetzungen für Ihre Zielsprache.

   1. Nachdem Sie mit der Übersetzung der Strings fertig sind, speichern Sie die Datei.




### Gebietsschema-Unterstützung zum Wörterbuch hinzufügen

Dieser Schritt gilt nur für andere Gebietsschemata als die folgenden häufig unterstützten Sprachen: Englisch (en), Deutsch (de), Spanisch (es), Französisch (fr), Italienisch (it), Brasilianisches Portugiesisch (pt-br), Chinesisch (vereinfacht - zh_cn), Chinesisch (traditionell - zh_tw), Japanisch (ja) und Koreanisch (ko_kr).

1. Suchen Sie den Konfigurationsordner:

   Navigieren Sie zum folgenden Verzeichnis in Ihrem [AEMaaCS-Projektverzeichnis]:

   ```
   /ui.content/src/main/content/jcr_root/etc
   ```

1. Erstellen Sie die erforderlichen Ordner (falls nicht vorhanden):

   Wenn die Variable `etc` Ordner ist nicht in `jcr_root` Ordner erstellen. Innerhalb `etc`erstellen Sie einen weiteren Ordner namens `languages` wenn sie fehlt.

1. Erstellen Sie die Konfigurationsdatei des Gebietsschemas:

   Innerhalb der `languages` erstellen Sie eine neue Datei mit dem Namen `.content.xml`. Kopieren Sie nicht den Namen der Datei aus diesem Dokument, sondern geben Sie manuell den Namen ein.

   ![eine neue Datei mit dem Namen `.content.xml`](etc-content-xml.png)

   Öffnen Sie diese Datei und fügen Sie den folgenden Inhalt ein, ersetzen Sie [LOCALE_CODE] mit dem tatsächlichen Gebietsschema-Code (z. B. ar-ae für Arabisch).


   ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
         jcr:primaryType="nt:unstructured"
         languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr,hi]"/>
   ```

   WARNUNG: Ersetzen Sie nicht die vorhandene Liste. Hängen Sie stattdessen Ihren neuen Gebietsschema-Code in eckigen Klammern, durch Kommas getrennt, wie z. B. (unter Verwendung von ar-ae als Beispiel) an:

   ```XML
   languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr,hi,ar-ae]"
   ```

1. Schließen Sie die neuen Ordner in filter.xml ein:

   Navigieren Sie zum `/ui.content/src/main/content/meta-inf/vault/filter.xml` in der Datei [AEMaaCS-Projektverzeichnis].

   Öffnen Sie die Datei und fügen Sie am Ende die folgende Zeile hinzu:

   ```
   <filter root="/etc/languages"/>
   ```

   ![Fügen Sie die erstellten Ordner in `filter.xml` unter `/ui.content/src/main/content/meta-inf/vault/filter.xml`](langauge-filter.png) hinzu

1. Speichern Sie die Datei.

### Bereitstellen des neu erstellten Gebietsschemas in Ihrer AEM-Umgebung

Sie sind nun alle so eingestellt, dass das neue Gebietsschema mit Ihrem adaptiven Forms verwendet wird. Sie können

* Bereitstellen des AEM as a Cloud Service, [AEMaaCS-Projektverzeichnis], um die neue Gebietsschema-Konfiguration auf Ihrem lokalen Computer auszuprobieren. So stellen Sie Folgendes in Ihrer lokalen Entwicklungsumgebung bereit:

   1. Stellen Sie sicher, dass Ihre lokale Entwicklungsumgebung aktiv ist. Wenn Sie noch keine lokale Entwicklungsumgebung eingerichtet haben, lesen Sie das Handbuch unter [Einrichten einer lokalen Entwicklungsumgebung für AEM Forms](/help/forms/setup-local-development-environment.md).

   1. Öffnen Sie das Terminal-Fenster oder die Eingabeaufforderung.

   1. Navigieren Sie zum [AEMaaCS-Projektverzeichnis]

   1. Führen Sie den folgenden Befehl aus:

      ```
      mvn -PautoInstallPackage clean install
      ```

* Bereitstellen des AEM as a Cloud Service, [AEMaaCS-Projektverzeichnis]in Ihrer Cloud Service-Umgebung. So stellen Sie Folgendes in Ihrer Cloud Service-Umgebung bereit:

   1. Übertragen Sie Ihre Änderungen:

      Bestätigen Sie nach dem Hinzufügen der neuen Gebietsschemakonfiguration Ihre Änderungen mit einer klaren Git-Meldung, die das Gebietsschema-Hinzufügen beschreibt (z. B. &quot;Hinzugefügte Unterstützung für [Gebietsschema-Name]&quot;).

   1. Bereitstellen des aktualisierten Codes:

      Trigger einer Bereitstellung Ihres Codes über die [vorhandene Vollstapelpipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline). Dadurch wird automatisch der aktualisierte Code mit der neuen Gebietsschema-Unterstützung erstellt und bereitgestellt.

      Wenn Sie noch keine Pipeline eingerichtet haben, lesen Sie das Handbuch unter [Einrichten einer Pipeline für AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline).


## Vorschau eines adaptiven Formulars mit dem neu hinzugefügten Gebietsschema

Diese Schritte führen Sie durch die Vorschau eines adaptiven Formulars mit dem neu hinzugefügten Gebietsschema:

1. Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Instanz an.
1. Gehen Sie zu **Formulare** > **Formulare und Dokumente**.
1. Wählen Sie ein adaptives Formular aus und klicken Sie auf **Wörterbuch hinzufügen**. Daraufhin wird der Assistent **Wörterbuch zum Übersetzungsprojekt hinzufügen** geöffnet.
1. Geben Sie den **Projekttitel** an und wählen Sie die **Zielsprachen** aus dem Dropdown-Menü im Assistenten **Wörterbuch zum Übersetzungsprojekt hinzufügen**.
1. Klicken auf **Fertig** und führen Sie das erstellte Übersetzungsprojekt aus.
1. Gehen Sie zu **Formulare** > **Formulare und Dokumente**.
1. Wählen Sie das adaptive Formular aus und wählen Sie die **Vorschau als HTML** -Option.
1. Anhängen `&afAcceptLang=<locale-name>` zur Vorschau-URL und drücken Sie die Eingabetaste. Ersetzen `<locale-name>` mit Ihrem tatsächlichen Gebietsschema-Code. Das adaptive Formular wird in dem angegebenen Gebietsschema angezeigt.

## Best Practices zur Unterstützung neuer Lokalisierungen {#best-practices}

* Adobe empfiehlt die Erstellung eines Übersetzungsprojekts nach der Erstellung eines adaptiven Formulars. Dadurch wird der Lokalisierungsprozess optimiert.


* Umgang mit neuen Feldern:

   * **Maschinelle Übersetzung**: Wenn Sie maschinelle Übersetzung verwenden, müssen Sie das Wörterbuch neu erstellen und[das Übersetzungsprojekt ausführen](/help/forms/using-aem-translation-workflow-to-localize-adaptive-forms-core-components.md) nach dem Hinzufügen neuer Felder zu einem vorhandenen adaptiven Formular. Neue Felder, die nach dem ersten Übersetzungsprojekt hinzugefügt wurden, bleiben unübersetzt.

   * **Menschliche Übersetzung**: Exportieren Sie für menschliche Übersetzungs-Workflows das Wörterbuch mithilfe der Benutzeroberfläche unter `[AEM Forms Server]/libs/cq/i18n/gui/translator.html`. Aktualisieren Sie das Wörterbuch für die neuen Felder und laden Sie die überarbeitete Version hoch.


## Siehe auch {#see-also}

{{see-also}}

* [Generieren eines Datensatzdokuments für adaptive Formulare](/help/forms/generate-document-of-record-core-components.md)
* [Hinzufügen eines adaptiven Formulars zu einer AEM Sites-Seite oder einem Experience Fragment](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)

