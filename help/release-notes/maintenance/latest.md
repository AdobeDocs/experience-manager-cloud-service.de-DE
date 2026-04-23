---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 9d9acd2151aca65a0c988b90bc4f94e088395f3f
workflow-type: tm+mt
source-wordcount: '2221'
ht-degree: 9%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 25520 {#25520}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 25520, die am Freitag, 23. April 2026 veröffentlicht wurde. Die vorherige Wartungsversion war Version 25194.

Die Funktionsaktivierung von 2026.4.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).


### Verbesserungen {#enhancements-25520}

* FORMS-24388: Es wurde eine lokale Entwicklungsumgebung für den IC-Editor (Interactive Communication) hinzugefügt, mit der Entwicklerinnen und Entwickler Konfigurationen erstellen und testen können, ohne auf freigegebene Server angewiesen zu sein. Diese Verbesserung hilft Unternehmenskunden, schneller zu iterieren, Umgebungsabhängigkeiten zu reduzieren und die Gesamtproduktivität der Entwicklung zu verbessern.
* FORMS-24014: Der Regeleditor für Dateianlagenkomponenten wurde erweitert, um die Kombination von Bedingungen mithilfe der Logik „UND“ zu unterstützen - z. B. das Zulassen von Regeln wie „Wenn der Dateianhang geändert wird und das Bedienfeld gültig ist, dann tun Sie dies.“ Zuvor war es nicht möglich, zusätzliche Bedingungen mit Dateianlagen zu verwenden. Diese Aktualisierung ermöglicht komplexere Regeldefinitionen zur Unterstützung erweiterter Workflows.
* FORMS-23571: Die vorhandene vereinfachte Grammatikansicht für Ereignisregeln für Trigger wurde erweitert, indem zusätzlich zu benutzerdefinierten Ereignissen auch vordefinierte Ereignisse unterstützt werden. Zuvor konnten Benutzende die vereinfachte Grammatik nur für benutzerspezifische Ereignisse verwenden und mussten zwischen „WENN“- und „EIN-TRIGGER-EREIGNIS“-Regeln wechseln, um vordefinierte und benutzerdefinierte Ereignisse separat zu konfigurieren. Mit diesem Update können sowohl OOTB- als auch benutzerdefinierte Ereignisse in derselben vereinfachten Grammatik verwendet werden, wodurch die Regelkonfiguration optimiert und die Notwendigkeit von Wechselkontexten reduziert wird.
* FORMS-24462: Es wurde Unterstützung für die Komponente „Freihandsignatur“ in React-Vanilla-Komponenten für Headless Adaptive Forms (AF) hinzugefügt. Diese Verbesserung ermöglicht es Benutzenden, handschriftliche Signaturen direkt in React-basierten Formularen zu erfassen, indem sie Workflows für digitale Signaturen und geplante Zeitpläne für die Live-Schaltung für Unternehmenskunden unterstützen.
* FORMS-24343: Es wurde eine optimierte Handhabung für `custom:setProperty` im Formularmodell JavaScript Object Notation (JSON) hinzugefügt, was eine schnellere Verarbeitung von dynamischen Eigenschaftenaktualisierungen ermöglicht. Diese Leistungsverbesserung verbessert die Leistung für komplexe adaptive Forms (AF), die häufig Laufzeitänderungen erfordern, was zu reibungsloseren Benutzerinteraktionen und kürzeren Ladezeiten führt.
* FORMS-24358: Es wurde Unterstützung für die Verwendung der `items`-Eigenschaft in der Modellstruktur der JavaScript Object Notation (JSON) anstelle von `:items` und `:itemsOrder` hinzugefügt. Diese Verbesserung ermöglicht es Entwicklerinnen und Entwicklern, mit einem saubereren, intuitiveren Datenmodell zu arbeiten, das besser an gängigen JSON-Konventionen ausgerichtet ist und die Integration mit externen Systemen vereinfacht.
* FORMS-24087: Es wurde Unterstützung für die Definition von Regeln und Ereignissen direkt in Fragment-Containern in Adaptive Forms (AF) hinzugefügt. Diese Verbesserung ermöglicht es Autorinnen und Autoren, bedingte Logik und Interaktionen auf Container-Ebene anzuwenden, wodurch die Wiederverwendung verbessert wird und die Notwendigkeit, Regeln über einzelne Fragmentfelder hinweg zu duplizieren, reduziert wird.
* FORMS-24440: Es wurde die neue Aktion „Feld entfernen“ im Dropdown-Menü „DANN“ des Regeleditors für den Editor für interaktive Kommunikation hinzugefügt, mit der Benutzende eine ausgewählte Komponente vollständig aus dem Formular entfernen können, wenn eine Regelbedingung erfüllt ist. Diese Verbesserung unterstützt Workflows, die eine dynamische Neustrukturierung von Formularen erfordern, anstatt nur Felder auszublenden, während weiterhin das entsprechende `forms_ready`-Skript für konsistentes Verhalten ausgelöst wird.
* FORMS-23898: Es wurde Unterstützung für die Definition von Variablen mithilfe `@` Notation im Editor für interaktive Kommunikation (IC) hinzugefügt, sodass Benutzende dynamische Tabellen intuitiver konfigurieren können. Diese Verbesserung vereinfacht die Einrichtung variablengesteuerter Tabelleninhalte und verbessert die Klarheit bei der Verwaltung dynamischer Daten im Authoring-Erlebnis.
* FORMS-23702: Es wurde eine zertifikatbasierte Authentifizierung für SharePoint List (SPList)-Verbindungen hinzugefügt, die einen sichereren, zertifikatgesteuerten Zugriff auf SharePoint-Daten ermöglicht. Diese Verbesserung hilft Unternehmenskunden, strengere Sicherheits- und Compliance-Anforderungen zu erfüllen und gleichzeitig die Abhängigkeit von der kennwortbasierten Authentifizierung zu reduzieren.
* FORMS-23800: Es wurde Unterstützung zum Überschreiben von reCAPTCHA-Geheimschlüsseln in Sling-Konfigurationen hinzugefügt, sodass Unternehmenskunden ihre eigenen Sicherheits- und Compliance-Anforderungen erfüllen können. Diese Verbesserung ermöglicht eine umgebungsspezifische Verwaltung von geheimen Schlüsseln, sodass Admins reCAPTCHA sicher und ohne Code-Änderungen integrieren können.
* SITES-39116: Der Endpunkt GET für Inhaltsfragmente enthält jetzt Metadatenschema-Informationen.
* SITES-41449: Neuer dedizierter GET-Endpunkt zum Abrufen von Inhaltsfragment-Metadaten.
* SITES-39434: Inhaltsfragmente und Ordner können jetzt mit Metadatenschemata für die strukturierte Metadatenverwaltung verknüpft werden.
* SITES-39567: Die Metadaten von Inhaltsfragmenten werden jetzt gemäß dem verknüpften Metadatenschema validiert und gespeichert.
* SITES-40006: Inhaltsfragmente können jetzt mithilfe von Metadatenfeldwerten durchsucht und gefiltert werden.
* SITES-41391: Die API zum Abrufen einzelner Inhaltsfragmente enthält jetzt Statusinformationen zum Ein-/Auschecken
* SITES-42214: Verbesserte Zuverlässigkeit und Leistung bei Vorgängen zum Verschieben von Inhaltsfragmenten
* SITES-41351: Das Anzeigeformat von Metadaten in Inhaltsfragmenten wurde verbessert, um die Lesbarkeit zu verbessern.
* SITES-42458: Standardmetadaten können jetzt ohne strikte Schemavalidierung hinzugefügt werden, um die Flexibilität zu erhöhen.
* SITES-35508: Edge Delivery mit universellem Editor: Hinzufügen von Unterstützung für Bilder im RTE.
* SITES-37078: Edge Delivery mit universellem Editor: Entfernen von universellen Editor-Instrumentierungen, wenn Seiten schreibgeschützt sind.
* SITES-40206: Edge Delivery mit universellem Editor: Hinzufügen einer Namensvalidierung zum Seitenerstellungsassistenten.
* SITES-40255: Edge Delivery mit universellem Editor: Verhindern Sie die Veröffentlichung von Kalkulationstabellen als `/config.json`.
* SITES-40757: Edge Delivery mit universellem Editor: Stellen Sie im Assistenten zur Site-Erstellung die Eindeutigkeit von Edge Delivery-Konfigurationen sicher.
* SITES-41134: Edge Delivery mit universellem Editor: Veröffentlichung der dateibasierten Konfiguration schlägt fehl.

### Behobene Probleme {#fixed-issues-25520}

* FORMS-24811: Bei der Verwaltung von Formularlogikregeln sind Probleme aufgetreten. Beim Versuch, zuvor erstellte Regeln zu ändern, ließ der Regeleditor keine Änderungen zu, sodass Benutzer Regeln von Grund auf neu erstellen mussten und die Formularwartung verlangsamt wurde.
* FORMS-24720: Bei der Konfiguration neu erstellter Variablen in Adaptive Forms (AF) sind Probleme aufgetreten. Beim Hinzufügen von Regeln zu datengebundenen oder ungebundenen Variablen wurden die Regeln nicht wie erwartet gespeichert, was die Benutzer zwang, ihre Logik neu zu erstellen, und die Arbeitsabläufe für die Formularerstellung verlangsamte.
* FORMS-24195: Beim Zurücksetzen von Dropdown-Feldern in Adaptive Forms (AF) ist ein inkonsistentes Verhalten aufgetreten. Wenn für eine Dropdown-Liste ein Platzhalter konfiguriert war und das Formular oder die Komponente zurückgesetzt wurde, wurde das Feld leer, anstatt zum Platzhalterwert zurückzukehren, was zu Verwirrung bei der erforderlichen Auswahl führte.
* FORMS-24718: Bei Auswahl der Schaltfläche „Startseite“ traten Navigationsprobleme im IC-Editor (Interactive Communication) auf. Statt zur Adobe Experience Manager-Hauptbenutzeroberfläche (AEM) zurückzukehren, wurde die Schaltfläche nicht wie erwartet umgeleitet, was den Arbeitsablauf der Benutzenden beim Wechsel zwischen der IC-Bearbeitung und dem AEM-Startbildschirm störte.
* FORMS-24810: Beim ersten Versuch, die adaptive Benutzeroberfläche (AUI) für Formulare zu laden, traten zeitweise Fehler auf. In einigen Sitzungen wurde die ursprüngliche Seite nicht korrekt wiedergegeben, sodass Benutzende sie aktualisieren oder erneut versuchen mussten, bevor sie mit dem Ausfüllen ihrer Formulare beginnen konnten.
* FORMS-24520: In der Druckvorschau der Benutzeroberfläche für Agenten (UI) für Formulare, die die adaptive Benutzeroberfläche (AUI) verwenden, fehlten Seitenzahlen. Beim Öffnen der Druckvorschau durch Kundendienstmitarbeiter erschien das Feld Seitenzahl manchmal leer, was es schwieriger machte, auf bestimmte Seiten zu verweisen, wenn Druckkopien überprüft oder freigegeben wurden.
* FORMS-24532: Bei der Verwendung des Formulardatenmodells (FDM) zum Vorbefüllen mit SharePoint-`/teams` sind Fehler aufgetreten. Regierungsbehörden, die auf diese Listen angewiesen sind, konnten Formulare ohne erwartete, vorausgefüllte Daten laden, wodurch die Datenerfassungs-Workflows unterbrochen und der manuelle Erfassungsaufwand erhöht wurde.
* FORMS-24516: Nach einem SDK-Upgrade in AEM Forms as a Cloud Service fehlten im Datensatzdokument (Document of Record, DoR) die Daten zur Freihandsignatur. Beim Signieren von Formularen mit der Option Freihand zeigte das generierte DoR die erfasste Signatur nicht an, was bei Unternehmenskunden zu Verwirrung und unvollständigen Datensätzen führte.
* FORMS-18631: Benutzende hatten Probleme mit der Barrierefreiheit bei Rasterlayouts auf Desktopgeräten, responsivem Webdesign (RWD)-Tablet und RWD-Mobilansichten. Bei der Verwendung von Chrome unter Windows 11 mit der Bildschirmlesehilfe NVDA (NonVisual Desktop Access) fehlten in Rastern die entsprechenden Rollen und Attribute, sodass Hilfstechnologien den Inhalt nur schwer richtig interpretieren und darin navigieren konnten.
* FORMS-24798: Bei der Verwendung `else` Bedingungen in adaptiven Forms-Regeln (AF) in der AEM Forms-Benutzeroberfläche (UI) kam es zu einem inkonsistenten Verhalten. Wenn die Primärregelbedingung nicht erfüllt war, wurden die zugehörigen `else` nicht ausgeführt, was dazu führte, dass sich die Formularlogik und die Feldsichtbarkeit anders verhielten als von den Autoren konfiguriert.
* FORMS-24334: Bei der Arbeit mit einem eingebetteten adaptiven Formular (AF) in Adobe Experience Manager (AEM) Forms as a Cloud Service traten Fehler beim Vorbefüllen und Zusammenführen von JavaScript Object Notation (JSON) auf. Beim Laden migrierter Formulare wurden die erwarteten vorausgefüllten Daten nicht angezeigt und der zusammengeführte JSON-Inhalt war unvollständig oder falsch. Dies blockierte die Migration von On-Premise-AEM 6.5 zu AEM Forms as a Cloud Service für betroffene Umgebungen.
* FORMS-24441: Bei der Konfiguration der Datensatzdokument-Vorlage (DoR) in Adobe Experience Manager (AEM) Forms as a Cloud Service sind Probleme aufgetreten. Beim Speichern einer benutzerdefinierten DoR-Vorlage in der schnellen Entwicklungsumgebung wurde die Vorlage auf die Standardversion zurückgesetzt, sodass sie ihr beabsichtigtes Layout und ihre Einstellungen nicht beibehalten konnte.
* FORMS-24393: Es kam zu Verwirrung, wenn ältere Vorlagen weiterhin als „Unbenannt“ angezeigt wurden, anstatt aussagekräftige Namen anzuzeigen. Dadurch war es bei der täglichen Bearbeitung schwierig, vorhandene Vorlagen zu unterscheiden und wiederzuverwenden.
* FORMS-24163: Bei der Vorschau von Formularen der Version 2, die Fragmente enthielten, traten Probleme auf. Im Vorschaumodus wurde der Formularinhalt nicht wie erwartet gerendert, was Benutzer daran hinderte, das Layout und das Verhalten vor der Veröffentlichung zu überprüfen.
* FORMS-24328: Bei der Verwendung von Invisible reCAPTCHA v2 mit der Option „CAPTCHA durch Benutzeraktion validieren“ wurden Formularübermittlungen nicht abgeschlossen. Unternehmenskunden haben festgestellt, dass Formulare in betroffenen Umgebungen nicht erwartungsgemäß übermittelt wurden, was die Workflows für Kontakte und Angebotsanfragen störte.
* SITES-42118: Neuschreibungsregeln für `/graphql/execute.json` überspringen.
* SITES-40095: Korrigieren Sie die lokale Referenzliste im Metadaten-Editor.
* SITES-42191: Beheben Sie das Problem, dass in GraphQL JSON eingebettete Bildverweise weggelassen werden, wenn DAM-Dateinamen Leerzeichen/Nicht-ASCII-Zeichen enthalten.
* SITES-22336: Nicht lokalisierte Zeichenfolge „Inhaltsfragmentmodelle“ in Assets > Erstellen > Inhaltsfragment.
* SITES-19796: Nicht lokalisierte Zeichenfolge „Ungültiger Name angegeben“ wird beim Hinzufügen eines ungültigen Zeichens beim Erstellen eines Inhaltsfragments unter Assets angezeigt.
* SITES-42531: Die QuickInfo ist nicht lokalisiert, wenn „Inhaltsfragment“ auf der Seite &quot;Assets&quot; gesperrt wird.
* SITES-42532: Nicht lokalisierte Zeichenfolge „Later“ bei der Veröffentlichung von CF in AEM in Assets.
* SITES-39250: Lokalisierte Zeichen werden in einem Link in Assets > Inhaltsfragment-Editor falsch angezeigt.
* SITES-41117: Nicht lokalisiert „Der ausgewählte Wert muss ein gültiger Modelltyp in `{}` oder ein globales Modell sein.“ Zeichenfolge im Inhaltsfragmentmodell-Editor.
* SITES-41431: Weniger ausführlich Feedback von Bildschirmlesehilfen für die Sperrschaltfläche, um klarere, knappere Ankündigungen zu erhalten.
* SITES-40819: Es wurde ein Tastaturfokus korrigiert, der nach einer Interaktion nicht zum auslösenden Element zurückkehrt, wodurch eine vorhersehbare Fokusreihenfolge sichergestellt wurde.
* SITES-40751: Es wurden sichtbare Beschriftungen zum Tastaturfokus für Symbolleistenelemente hinzugefügt, damit Tastaturbenutzer Aktionen klar identifizieren können.
* SITES-25524: Die Verwendung von aria-gepressten Gerätetasten wurde korrigiert, sodass Hilfstechnologien genaue Zustandsinformationen erhalten.
* SITES-25321: Textfarben wurden aktualisiert, um die minimalen Kontrastanforderungen zu erfüllen und die Lesbarkeit für Benutzer mit Sehschwäche zu verbessern.
* SITES-25304: Verhindert, dass die reduzierte demografische Symbolleiste fälschlicherweise den Fokus erhält, wobei eine logische Fokussequenz beibehalten wird.
* SITES-25292: Klarere Ankündigungen der Sprachausgabe für die Schaltfläche zum Drehen des Geräts, um dessen Zweck und Zustand besser zu beschreiben.
* SITES-25290: Es wurde ein sichtbarer, gedrückter Status für die Desktop-Umschalter-Schaltfläche hinzugefügt, um den Auswahlstatus für Benutzer offensichtlich zu machen.
* SITES-25287: Verbesserter Kontext für die Linealmessung beim Bearbeiten des Layouts, sodass Benutzende von Bildschirmlesehilfen verständliche Messinformationen erhalten.
* SITES-25284: Das Abschneiden der Schaltflächenbeschriftung &quot;iPhone 8 Plus“ im nicht aktivierten Zustand wurde korrigiert, sodass der vollständige Gerätename angekündigt und angezeigt wird.
* SITES-25251: Es wurde Feedback für Benutzende von Bildschirmlesehilfen eingeführt, wenn die Liste „Neue Komponente einfügen“ gefiltert wird, was anzeigt, dass die Ergebnisse geändert wurden.
* SITES-25221: Die Touch-Zielgröße der Schaltfläche „Bearbeiten“ in der Asset-Seitenleiste wurde erhöht, um die Richtlinien für die minimale Zielgröße zu erfüllen.
* SITES-25220: Es wurde ein Warnhinweis/ein Hinweis hinzugefügt, dass die Schaltfläche Bearbeiten in der linken Leiste von Assets eine neue Registerkarte öffnet, was die Vorhersehbarkeit für Benutzende von Hilfstechnologien verbessert.
* SITES-24993: Der Titel der Arbeitsflächen-Kopfzeile des Editors wurde aktualisiert, um eine ordnungsgemäße Überschriftenrolle zu verwenden und die Dokumentstruktur für Bildschirmlesehilfen zu verbessern.
* SITES-24954: Die Fokusreihenfolge für die Emulator-Schaltfläche wurde korrigiert, sodass sie einer natürlichen und logischen Navigationssequenz folgt.
* SITES-41586: Korrektur für das Kopieren und Einfügen der Inhaltsfragment-Komponente im Editor, wobei ein Verweis auf das Inhaltsfragment verloren geht.
* SITES-42195: Behebung von `CommerceLinksTransformerFactory`, die keine Sling-Zuordnungen in der Veröffentlichungsinstanz berücksichtigen.
* SITES-41238: Behebung eines Fehlers in ThumbnailServlet, der zu einer Protokollflut führte.
* SITES-41041: Korrigieren von CIF-Komponenten, die nicht in der Versionsvorschau/im Vergleich gerendert werden.
* SITES-40756: Korrigieren Sie das nicht lokalisierte Datumsformat in Live Copy-Übersicht > Beziehungsstatus.
* SITES-40219: Es wurde ein Fehler behoben, durch den CatalogPageNotFoundFilter nicht für bestimmte Produkt- oder Kategorieseiten aufgerufen wurde.
* SITES-40218: Beheben Sie das Problem, dass in SpecificPageFilterFactory die Registrierung des Ressourcentyps der Seite v3 fehlt.
* SITES-40347: Unterbrechen Sie die Vererbung für den Titel, wenn Sie eine Live Copy mit einem neuen Titelsatz erstellen.
* SITES-41544: E-Tag-Berechnungen für Inhaltsfragmente schließen jetzt Metadaten aus.
* SITES-42734: Es wurde ein Problem behoben, bei dem der Endpunkt für GET-Metadaten bei Verwendung des Standardschemas leere Felder zurückgab.
* SITES-37955: Edge Delivery mit universellem Editor: Stellen Sie sicher, dass die Veröffentlichungsvoraussetzungen konsistent überprüft werden.
* SITES-40877: Edge Delivery mit universellem Editor: Beheben von Veröffentlichungsfehlern für Seiten, die nicht-ASCII-Sonderzeichen enthalten.
* SITES-42092: Edge Delivery mit universellem Editor: Korrigieren Sie das tiefe Rückgängigmachen der Veröffentlichung für Pfade, die auf `-s` enden.
* SITES-24650: iframe hat keinen Titel.

### Bekannte Probleme {#known-issues-25520}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-25520}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-25520}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. In dieser Wartungsversion wurden 24 identifizierte Schwachstellen behoben, was für einen noch robusteren Systemschutz sorgt.

### Eingebettete Technologien {#embedded-tech-25520}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1,90,0 | [Oak 1.90.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.90.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-Kernkomponenten | 2,30,4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
