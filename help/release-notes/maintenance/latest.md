---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: d2c26a122bd2a0a970af7578932d88e6f93487d5
workflow-type: tm+mt
source-wordcount: '1772'
ht-degree: 13%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 25194 {#25194}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 25194, die am Donnerstag, 1. April 2026 veröffentlicht wurde. Die vorherige Wartungsversion war Version 24678.

Die Funktionsaktivierung von 2026.4.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Versions-Roadmap von Experience Manager](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

>[!NOTE]
>
>Version 24893 wurde als privat gekennzeichnet.

### Verbesserungen {#enhancements-25194}

* ASSETS-65127: Benutzerdefinierte Ereignis-Metadaten: Verbesserte Verarbeitung von Metadatennamen.
* ASSETS-63313: Erstellen Sie automatisch verknüpfte Links für exportierte Assets und übergeordnete Elemente basierend auf C2PA-Manifesten.
* ASSETS-10995: Anzahl der Assets in einer Download-Zip begrenzen.
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

### Behobene Probleme {#fixed-issues-25194}

* ASSETS-62882: Admin-Ansicht: Die Info-QuickInfo funktioniert nicht mehr, wenn mehrere ungültige Dateinamen hochgeladen werden.
* ASSETS-63642: Freigabe-Link kann Asset in einigen Entwicklungsumgebungen nicht rendern (SLA3).
* ASSETS-59267: NPE beim Laden von Anwendungsmetadaten für die Versand-Payload.
* ASSETS-59227: Metadatenexport: Nicht ausgewählte Eigenschaften sind aufgrund der Regex-Zuordnung nicht mehr enthalten.
* ASSETS-65187: CSV-Vorschau in der Cloud, wenn Spaltendaten Escape-Kommas enthalten.
* ASSETS-63441: Stellen Sie sicher, dass alle Benutzenden über Berechtigungen zum Lesen der Assets Omnisearch-Konfiguration verfügen.
* SITES-40095: Metadaten-Editor: Verweise auf lokale Inhaltsfragmente, die mehr als 10 Einträge umfassen.
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

#### AEM Guides {#guides-25194}

* GUIDES-38412 : Beim Bearbeiten einer Schematron-`(*.sch)` und bei Verwendung der Funktion zum Suchen und Ersetzen wird das Bedienfeld „Suchen und Ersetzen“ unten teilweise außerhalb des Bildschirms angezeigt, wodurch der Zugriff auf die Eingabefelder und Steuerelemente verhindert wird.
* GUIDES-37806: Wenn dasselbe Thema in mehreren Zuordnungen mit unterschiedlichen bedingten Vorgaben wiederverwendet wird, überschreibt die Veröffentlichung der neuesten Zuordnung in Salesforce den Themeninhalt, was dazu führt, dass Benutzenden zuvor veröffentlichter Zuordnungen falsche Daten angezeigt werden.
* GUIDES-39394: Wenn ein Bild, das ursprünglich als sprachspezifisches Asset mit einer bestimmten Version (z. B. unter `/en/`) verwaltet wurde, in einen globalen Ordner mit einer aktualisierten Version verschoben und ein Baseline-Export durchgeführt wird, verweist die neue Baseline weiterhin auf veraltete sprachspezifische Versionen dieses Bildes, was zu einem fehlgeschlagenen Baseline-Export führt.
* GUIDES-39054: Beim Erstellen einer dynamischen Baseline reagiert der Editor manchmal aufgrund mehrerer gleichzeitiger API-Anfragen nicht mehr, wodurch alle anderen Vorgänge angehalten werden.
* GUIDES-37781: Wenn Sie einen Benutzer einer Prüfungsaufgabe zuweisen, werden in der Dropdown-Liste alle Benutzer und nicht nur die mit den ausgewählten Projekten verknüpften aufgelistet. Dies führt zu ungültigen Benutzeroptionen.
* GUIDES-39385: Beim Öffnen eines Berichts für eine Zuordnung tritt beim Laden des Bedienfelds „Filter“ eine Verzögerung auf.

Weitere Informationen zu den neuen und verbesserten Funktionen sowie zu den Problemen, die in der Version behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekannte Probleme {#known-issues-25194}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-25194}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-25194}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. In dieser Wartungsversion wurden 9 identifizierte Schwachstellen behoben, was für einen noch robusteren Systemschutz sorgt.

### Eingebettete Technologien {#embedded-tech-25194}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1,90,0 | [Oak 1.90.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.90.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-Kernkomponenten | 2,30,4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
