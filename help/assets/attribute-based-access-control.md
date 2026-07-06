---
title: Attributbasierte Zugriffssteuerung
description: Erfahren Sie, wie Sie die attributbasierte Zugriffssteuerung aktivieren, um metadatenbasierte Regeln und die Zugriffsebene für in Content Hub verfügbare Assets zu definieren
role: Admin
badgeSaas: label="AEM Assets" type="Positive" tooltip="Gilt für AEM Assets)."
exl-id: 05f54b05-40b8-4a6c-af8f-5c3f7a2089d4
source-git-commit: 230ca753bd5f3d5b26b30a962a526dc0edfc9bd4
workflow-type: tm+mt
source-wordcount: '2182'
ht-degree: 20%

---


# Attributbasierte Zugriffssteuerung {#attribute-based-access-control}

Mit der attributbasierten Zugriffssteuerung (ABAC) können Content Hub-Admins metadatenbasierte Regeln definieren, um die Zugriffsebene auf in Content Hub verfügbare Assets zu steuern.

Admins für eine Organisation definieren Regeln für Benutzergruppen, die einer Gruppen-ID zugeordnet sind. Regeln sind eine Mischung aus [- und Vergleichsoperatoren](#supported-rule-constructs) und Admins können so viele Regeln definieren, wie benötigt werden, um den Asset-Zugriff in Content Hub zu verwalten.

Die Regeln basieren auf Metadaten. Wenn die in einer Regel definierten Bedingungen mit den Asset-Metadaten übereinstimmen, wird das Asset der Benutzergruppe angezeigt. Content Hub scannt die Asset-Metadaten, einschließlich benutzerdefinierter Metadaten, auf alle Assets, die in **Alle Assets** und **Sammlungen** verfügbar sind, um die Ergebnisse für Benutzergruppen anzuzeigen.

Beispiel: ERLAUBEN Sie den Zugriff auf eine Benutzergruppe mit Gruppen-ID = 1011, wenn die Asset-Metadaten mit „Marke = Marke X“ UND „Region = EMEA ODER Amerika“ übereinstimmen. Content Hub zeigt der Benutzergruppe mit der ID = 1011 nur die Assets an, für die „Marke = Marke X“ und „Region = EMEA oder Amerika“ gelten.

ABAC-Regeln in Content Hub können mithilfe der folgenden Ansätze konfiguriert werden:

* **Self-Service-Konfiguration** mithilfe des [KI-Assistenten in Content Hub](#configure-abac-using-ai-assistant-in-content-hub), unterstützt durch den AEM Governance Agent
* **Tabellenbasierte Konfiguration** durch [Adobe-Support](#configure-abac-using-spreadsheet)

Mit dem KI-Assistenten in Content Hub können Admins ABAC-Regeln mithilfe von Metadaten und natürlicher Sprache definieren und verwalten. Dies ermöglicht eine schnellere Regelkonfiguration und reduziert die Abhängigkeit von manuellen Support-Workflows.

Zu den wichtigsten Vorteilen der attributbasierten Zugriffssteuerung gehören:

* Beseitigt die Abhängigkeit von der Ordnerstruktur für Berechtigungen
* Ermöglicht es Admins, Assets hochzuladen und Berechtigungsstrukturen rückwirkend zu bestimmen
* Verringert die Anzahl der Duplikate und verbessert die Integrität des Assets. Duplikate sind in ordnerbasierten Berechtigungen erforderlich, wenn dieselben Assets für verschiedene Gruppen freigegeben werden.
* Ermöglicht granularen, regelbasierten Zugriff
* Unterstützt eine skalierbare Governance über Marken und Regionen hinweg
* Verbessert das Asset-Management

>[!VIDEO](https://video.tv.adobe.com/v/3475423/?captions=ger&learn=on&enablevpops){transcript=true}

## Aktivieren der attributbasierten Zugriffssteuerung {#enable-attribute-based-access-control}

ABAC-Regeln in Content Hub können mithilfe der folgenden Ansätze konfiguriert werden:

* **Self-Service-Konfiguration mit dem KI-Assistenten in Content Hub (unterstützt von AEM Governance Agent)**\
  Administratoren können ABAC-Regeln direkt in natürlicher Sprache in Content Hub definieren und verwalten.

* **Tabellenbasierte Konfiguration über den Adobe-Support**\
  Administratoren können ABAC-Regeln in einer Tabelle definieren und über den Adobe-Support zur Konfiguration übermitteln.

## Konfigurieren von ABAC mithilfe des KI-Assistenten in Content Hub

Mit dem KI-Assistenten in Content Hub auf Basis des AEM Governance Agent können Sie ABAC-Regeln direkt in Content Hub in natürlicher Sprache erstellen und verwalten.

Sie haben folgende Möglichkeiten:
* Suchen nach vorhandenen Regeln
* Regeln erstellen
* Regeln aktualisieren
* Regeln löschen

Dadurch können Admins Zugriffsregeln erstellen und verwalten, ohne auf Support-Workflows angewiesen zu sein.

### Voraussetzungen {#before-you-begin-ai-assistant}

Stellen Sie Folgendes sicher, bevor Sie den KI-Assistenten in Content Hub für die ABAC-Regelkonfiguration verwenden:

* Sie sind für AEM as a Cloud Service lizenziert
* Für Ihr Unternehmen ist ein KI-Assistent mit AEM Governance Agent verfügbar
* Wenn Sie noch keinen Zugriff haben, wenden Sie sich an den Adobe-Support und führen Sie die erforderlichen Lizenzierungsschritte aus
* Für das Try-Buy-Programm ist kein GenAI-Fahrer erforderlich

### Schritte zum Konfigurieren von ABAC-Regeln mithilfe des KI-Assistenten {#steps-ai-assistant}

1. Öffnen Sie den KI-Assistenten in Content Hub.

1. Beginnen Sie mit einer einfachen Anweisung.

   Beispiel:

   `Create a new rule in Content Hub`

   Der KI-Assistent führt Sie zu den Informationen, die zum Erstellen der Regel erforderlich sind.

1. Definieren Sie die Regel in natürlicher Sprache.

   Beispiel:

   `Frescopa Web Marketers user group should have access to assets where product equals Frescopa`

1. Umgebung auswählen, auf die die ABAC-Regel angewendet werden soll.

1. Überprüfen Sie die Regel, bevor Sie sie anwenden.

   Der KI-Assistent generiert eine strukturierte Vorschau der Regel. Nichts wird automatisch angewendet. Sie können die generierte Regel überprüfen, bei Bedarf anpassen oder die Aktion abbrechen, bevor Sie sie anwenden.

1. Speichern und wenden Sie die Regel an.

   Nach dem Speichern wird die Regel basierend auf Metadaten dynamisch erzwungen.

Dieser Überprüfungsschritt trägt dazu bei, die Genauigkeit sicherzustellen, bevor die Regel angewendet wird.

### ABAC-Regeln mithilfe von Eingabeaufforderungen verwalten {#manage-abac-rules-using-prompts}

Nachdem Sie mit der Verwendung des KI-Assistenten begonnen haben, können Sie ABAC-Regeln im Gespräch verwalten.

**Regeln entdecken**

* Alle vorhandenen Content Hub ABAC-Regeln anzeigen

**Regeln erstellen**

* Erstellen einer Regel, die der Marketing-Produktgruppe Zugriff auf alle Assets gewährt
* Zugriffsberechtigung der Vertriebsgruppe auf Assets, bei denen Region gleich EMEA ist

**Regeln aktualisieren**

* Aktualisierungsregel für die EMEA-Marketing-Gruppe, um APAC einzuschließen

**Regeln löschen**

* Löschen der Regel für die Produkt-Marketing-Gruppe

**Erkunden von Metadaten und Gruppen**

* Verfügbare Gruppen und Metadateneigenschaften anzeigen, um Regeln festzulegen

## ABAC mithilfe von Tabellenkalkulation konfigurieren

Wenn der KI-Assistent für Ihr Unternehmen nicht aktiviert ist, können Sie ABAC-Regeln mithilfe des tabellenbasierten Workflows konfigurieren.

Klicken Sie auf **Tabelle herunterladen**, um Regeln in einer Tabelle herunterzuladen und zu definieren. Erstellen Sie ein Adobe-Support-Ticket und stellen Sie Adobe die in der Tabelle definierten Regeln zur Verfügung.

[!BADGE Tabelle herunterladen]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/ABAC_Get_Started_Template.xlsx"}

Definieren Sie Regeln in der Tabelle anhand der in diesem Artikel beschriebenen Richtlinien.

>[!IMPORTANT]
>
>Navigieren Sie nach der Definition der Regeln zur Registerkarte **Validierungsfehler** des Arbeitsblatts und klicken Sie auf **ABAC-Validierungen ausführen**. Die **Alle Validierungen erfolgreich** bestätigt, dass Sie die definierten Regeln für Adobe bereitstellen können.

### Schritte zum Konfigurieren von ABAC-Regeln mithilfe von Tabellen {#steps-spreadsheet}

1. ABAC-Tabellenvorlage herunterladen.
1. Definieren Sie Regeln in der Tabelle mithilfe von metadatenbasierten Bedingungen.
1. Ordnen Sie jede Regel der entsprechenden IMS-Gruppen-ID zu.
1. Erfassen Sie die geschäftliche Absicht der Regel in Kommentaren.
1. Senden Sie ein Adobe-Support-Ticket und teilen Sie die ausgefüllte Tabelle mit Adobe.
1. Adobe konfiguriert die Regeln für Ihre Organisation.

## Anwendungsfall für die attributbasierte Zugriffssteuerung {#example-metadata-based-rules}

Um einen groß angelegten Marketing-Rollout zu unterstützen, benötigen verschiedene Team-Mitglieder in verschiedenen Regionen und Marken Zugriff auf digitale Assets. Jede Persona hat einen bestimmten Umfang, der von Region und Marke abhängt. ABAC erzwingt diese Regeln automatisch mithilfe von Asset-Metadaten. Die folgende Tabelle zeigt die Rollen für diesen Anwendungsfall und die angewendeten Regeln:

| Persona | Rolle | Rollenbeschreibung | Gruppen-ID | ABAC-Regel |
|---|---|---|---|---|
| John | EMEA Marketing Lead | Überwacht die Marketing-Ausführung aller Marken in EMEA. Benötigt Zugriff auf genehmigte Assets für alle Marken, die für EMEA-Märkte vorgesehen sind. | group-emea-marketing | Region = „EMEA“ |
| Mike | APAC-Marketingleiter | Überwacht die Marketing-Ausführung aller Marken in APAC. Benötigt Zugriff auf genehmigte Assets für alle Marken, die für APAC-Märkte vorgesehen sind. | group-apac-marketing | Region = „APAC“ |
| Sophie | Brand X Manager (EMEA) | Verwaltet die Identität der Marke X in EMEA. Darf nur für Marke X genehmigte Inhalte anzeigen, die auf EMEA-Märkte zugeschnitten sind. | group-emea-brands | Region = „EMEA“ &amp;&amp; Marke = „Marke X“ |
| Tom | Brand Y Manager (APAC) | Verwaltet die Identität der Marke Y in APAC. Darf nur für Marke Y genehmigte Inhalte sehen, die auf APAC-Märkte zugeschnitten sind. | group-apac-brandy | Region = „APAC“ &amp;&amp; Marke = „Marke Y“ |

Mithilfe dieser Regeln haben Content Hub-Admins folgende Möglichkeiten:

* **Granularer, regelbasierter Zugriff**: Benutzer sehen nur die Assets, die für ihre Region und Marke relevant sind, ohne manuelle Zugriffszuweisungen.
* **Nahtlose globale Zusammenarbeit**: Regional- und Marken-Teams arbeiten parallel, ohne dass Zugriffskonflikte auftreten.
* **Skalierbare und zukunftssichere Berechtigungen**: Wenn neue Regionen oder Marken hinzugefügt werden, können Regeln basierend auf Metadaten aktualisiert werden.

### Weitere Szenarien, in denen ABAC nützlich ist {#additional-scenarios-abac}

ABAC kann auch bei folgenden Szenarien helfen:

* **Globaler und regionaler Zugriff**: Teams sehen nur Assets, die für ihre Marke und ihren Markt relevant sind.
* **Zusammenarbeit zwischen Agenturen und Partnern**: Externe Agenturen und Partner können nur auf die für sie relevanten Kampagnen-Assets zugreifen.
* **Rollenbasierter Zugriff für verschiedene Teams**: Teams wie Marketing, Vertrieb und Rechtsabteilung können auf Assets zugreifen, die für ihre Funktion relevant sind.
* **Regionsspezifische rechtliche Konformität**: Benutzer können auf Assets beschränkt werden, die für bestimmte regulatorische oder regionale Anforderungen genehmigt wurden.

>[!IMPORTANT]
>
>Standardmäßig wird allen anderen Benutzergruppen, die nicht mit Regeln im [Arbeitsblatt“ angegeben &#x200B;](#configure-abac-spreadsheet), der Zugriff verweigert. Wenn ein(e) Benutzende(r) nicht zu einer Gruppe gehört, für die ABAC-Regeln definiert sind, kann er/sie nicht auf Assets zugreifen. Wenn einige Benutzende Zugriff auf alle Assets haben müssen, z. B. Administratoren, schließen Sie eine Gruppe mit einer Gruppen-ID in die Tabelle ein und geben Sie an, dass die Gruppe Zugriff auf alle Assets benötigt, damit Adobe sie entsprechend konfigurieren kann.

## Unterstützte Regelkonstrukte {#supported-rule-constructs}

* **Logische Operatoren**:
   * UND: Alle Bedingungen müssen erfüllt sein
   * ODER: Mindestens eine Bedingung muss erfüllt sein

* **Vergleichsoperatoren**:
   * Gleich (=): Prüft, ob ein Benutzer- oder Asset-Attribut mit einem Wert übereinstimmt
   * Ungleich (!=): Überprüft, ob ein Benutzer- oder Asset-Attribut mit einem Wert nicht übereinstimmt

Wenn Asset-Metadatenfelder Arrays enthalten, z. B. mehrere Regionen oder Tags, bezieht sich Gleich auf enthält Logik und Nicht Gleich auf enthält keine Logik.

Auf diese Weise können Sie einfache und ausdrucksstarke Regeln schreiben, wie z. B. ALLOW, wenn Region = EMEA ist, UND assetType != Prototyp UND Tags != vertraulich.

## Richtlinien {#guidelines-attribute-based-access-control}

Die folgenden Richtlinien gelten sowohl für die KI-Assistentenkonfiguration als auch für die tabellenbasierte Konfiguration:

* ABAC-Regeln gelten nur für Assets, die für Content Hub genehmigt wurden. Weitere Informationen finden Sie unter [Genehmigen von Assets für Content Hub](/help/assets/approve-assets-content-hub.md).
* Definieren Sie keine Ablehnungsregeln. Konvertieren Sie „Ablehnen“-Regeln immer in „Zulassen“-Regeln. Beispiel: ZULASSEN, wenn Region = Benutzerregion ABLEHNEN, wenn AssetType = Prototyp UND vertraulich = Ja konvertiert werden kann, wenn Region = Benutzerregion UND (assetType != Prototyp ODER vertraulich != Ja).
* ABAC-Regeln werden mithilfe der IMS-Gruppen-ID, die in der Admin Console verfügbar ist, auf Benutzergruppen angewendet.
* Sie können das [Validierungsziel](/help/assets/approve-assets-content-hub.md#set-approval-target) für Assets mithilfe der AEM as a Cloud Service-Autorenumgebung festlegen. ABAC-Regeln werden auf Assets angewendet, die mit Validierungsziel = Content Hub validiert wurden, da Validierungsziel = Bereitstellung für Assets ist, die für Bereitstellung + Content Hub verfügbar sind. Assets, die als Validierungsziel = Versand gekennzeichnet sind, sind in Content Hub für alle sichtbar.
* Stellen Sie sicher, dass die in ABAC-Regeln verwendeten Metadatenschemata korrekt definiert und in AEM verfügbar sind. Geben Sie den vollständigen Pfad des Metadatenschemas bzw. der Metadatenschemas in AEM an, die in ABAC-Regeln referenzierte Eigenschaften definieren. Optional können Sie einen Testordner mit Beispiel-Assets erstellen, die den ABAC-Bedingungen entsprechen, um das Regelverhalten zu überprüfen und den Zugriff genau auszuwerten.
* Erfassen Sie die geschäftliche Absicht der Regel in Kommentaren, auch wenn die Bedingung korrekt geschrieben ist, da die Absicht bei der Validierung und Korrektur der Logik hilft, falls erforderlich.
* Stellen Sie sicher, dass Metadatenwerte, die für Zugriffsregeln wie Marke, Region und Produkt verwendet werden, über Assets hinweg konsistent verwaltet werden.
* Beginnen Sie mit wichtigen Anwendungsfällen wie markenbasiertem oder regionsbasiertem Zugriff.
* Verwenden Sie klare Eingabeaufforderungen beim Definieren von Regeln mit dem KI-Assistenten. Beschreiben Sie die Absicht in der Geschäftssprache, damit der KI-Assistent sie in eine strukturierte Regel übersetzen kann.
* Lizenzieren PDF-Dateien, die für DRM festgelegt sind, müssen für alle Benutzenden sichtbar bleiben, damit sie die Lizenzinformationen beim Herunterladen des Assets mit Lizenz überprüfen können.

## Häufig gestellte Fragen {#faqs-attribute-based-access-control-content-hub}

### Was ist die attributbasierte Zugriffssteuerung (ABAC) in AEM Assets Content Hub?

Mit der attributbasierten Zugriffssteuerung (ABAC) in AEM Assets Content Hub können Admins metadatenbasierte Regeln definieren, um die Zugriffsebene verschiedener Benutzergruppen auf digitale Assets zu steuern. Der Zugriff wird davon bestimmt, ob die Asset-Metadaten den in den Regeln angegebenen Bedingungen entsprechen, was eine granulare und dynamische Verwaltung der Asset-Sichtbarkeit ermöglicht.

### Wie definieren Administratoren Zugriffsregeln mithilfe von ABAC in AEM Assets Content Hub?

Admins definieren Zugriffsregeln, indem sie Bedingungen basierend auf Asset-Metadaten wie Marke oder Region erstellen und diese mit bestimmten Benutzergruppen-IDs verknüpfen. Diese Regeln verwenden logische Operatoren und Vergleichsoperatoren, um genau anzugeben, welche Assets für welche Benutzergruppen sichtbar sind.

### Was sind die Hauptvorteile der Verwendung von ABAC gegenüber herkömmlichen ordnerbasierten Berechtigungen in AEM Assets Content Hub?

ABAC beseitigt die Abhängigkeit von Ordnerstrukturen bei Berechtigungen, ermöglicht es Administratoren, Assets rückwirkend hochzuladen und Berechtigungen zuzuweisen, und reduziert die Anzahl der benötigten doppelten Assets. Dies verbessert die Asset-Integrität und vereinfacht die Berechtigungsverwaltung, insbesondere wenn Assets für mehrere Gruppen freigegeben werden müssen.

### Können Administratoren ABAC-Regeln direkt in der Benutzeroberfläche von AEM Assets Content Hub einrichten?

Administratoren können ABAC-Regeln mithilfe des KI-Assistenten in Content Hub konfigurieren, wenn diese für ihr Unternehmen aktiviert sind. Sie können den tabellenbasierten Workflow auch weiterhin über den Adobe-Support verwenden.

### Welche Arten von Metadatenbedingungen können beim Einrichten von ABAC-Regeln in AEM Assets Content Hub verwendet werden?

ABAC-Regeln in AEM Assets Content Hub können logische Operatoren wie UND und ODER sowie Vergleichsoperatoren wie Gleich und Nicht Gleich verwenden. Metadateneigenschaften, die in den Regeln verwendet werden, müssen korrekt definiert und in den AEM-Metadatenschemata verfügbar sein und können Felder wie Region, Marke, Produkt, Kampagne, Asset-Typ oder Veröffentlichungsstatus enthalten.

### Warum ist AEM Assets Content Hub ABAC besonders für Unternehmen mit großen Teams und unterschiedlichem Asset-Bedarf nützlich?

ABAC ist für Unternehmen mit großen Teams nützlich, da es einen granularen, regelbasierten Zugriff auf Assets basierend auf Benutzerrollen, Regionen, Marken oder Geschäftsanforderungen ermöglicht. Dadurch wird sichergestellt, dass Benutzende nur Assets sehen, die für ihre Zuständigkeiten relevant sind, ohne manuelle Zugriffsberechtigungen oder übermäßige Duplizierung von Assets.

### Wie sollten Administratoren die ABAC-Tabelle für AEM Assets Content Hub vorbereiten, bevor sie sie an den Adobe-Support senden?

Administratoren sollten Benutzergruppen in der Adobe Admin Console erstellen, ihre Gruppen-IDs notieren, die Berechtigungen und Bedingungen für jede Gruppe in der Tabelle klar definieren, sicherstellen, dass alle Metadateneigenschaften den entsprechenden Schemata korrekt zugeordnet sind, und die Spalte „Kommentare“ verwenden, um den geschäftlichen Zweck jeder Regel zu verdeutlichen.

**Siehe auch**

* [Assets übersetzen](/help/assets/translate-assets.md)
* [Assets-HTTP-API](/help/assets/mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](/help/assets/file-format-support.md)
* [Suchen von Assets](/help/assets/search-assets.md)
* [Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](/help/assets/asset-reports.md)
* [Metadatenschemata](/help/assets/metadata-schemas.md)
* [Herunterladen von Assets](/help/assets/download-assets-from-aem.md)
* [Verwalten von Metadaten](/help/assets/manage-metadata.md)
* [Verwalten von Dynamic Media-Vorlagen](/help/assets/dynamic-media/manage-dynamic-media-templates.md)
* [Verwalten von Berichten](/help/assets/manage-reports-assets-view.md)
* [Suchfacetten](/help/assets/search-facets.md)
* [Verwalten von Sammlungen](/help/assets/manage-collections.md)
* [Massenimport von Metadaten](/help/assets/metadata-import-export.md)
* [Veröffentlichen von Assets in AEM und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
