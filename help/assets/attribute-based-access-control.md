---
title: Attributbasierte Zugriffssteuerung
description: Erfahren Sie, wie Sie die attributbasierte Zugriffssteuerung aktivieren, um metadatenbasierte Regeln und die Zugriffsebene für in Content Hub verfügbare Assets zu definieren
role: Admin
exl-id: 05f54b05-40b8-4a6c-af8f-5c3f7a2089d4
source-git-commit: 655f84593adb1199bcfc21cb54071feb3c8523c5
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 99%

---

# Attributbasierte Zugriffssteuerung {#attribute-based-access-control}

Mit der attributbasierten Zugriffssteuerung (ABAC) können Content Hub-Admins metadatenbasierte Regeln definieren, um die Zugriffsebene für in Content Hub verfügbare Assets zu definieren.

Admins für eine Organisation definieren Regeln für Benutzergruppen, die einer Gruppen-ID zugeordnet sind. Regeln sind eine Mischung aus [logischen und Vergleichsoperatoren](#supported-rule-constructs). Admins können so viele Regeln definieren, wie sie benötigen, um den Asset-Zugriff in Content Hub zu verwalten.

Die Regeln für die Asset-Einschränkung basieren auf Metadaten. Wenn die Asset-Metadaten den in der Regel definierten Bedingungen entsprechen, wird das Asset den Benutzergruppen angezeigt. Content Hub scannt die Asset-Metadaten einschließlich der benutzerdefinierten Metadaten für alle unter **Alle Assets** und **Sammlungen** verfügbaren Assets, um die Ergebnisse für Benutzergruppen anzuzeigen.

Beispiel: Zugriff auf eine Benutzergruppe mit Gruppen-ID = 1011 ZULASSEN, wenn die Asset-Metadaten mit „Marke = Marke X“ UND „Region = EMEA ODER Nord- und Südamerika“ übereinstimmen. Content Hub zeigt der Benutzergruppe mit der ID = 1011 nur die Assets an, bei denen Marke = `Brand X` und Region = `EMEA` oder `Americas`.

Zu den wichtigsten Vorteilen der attributbasierten Zugriffssteuerung gehören:

* Beseitigt die Abhängigkeit von der Ordnerstruktur für Berechtigungen

* Ermöglicht es Admins, Assets hochzuladen und Berechtigungsstrukturen rückwirkend zu bestimmen

* Reduziert die Anzahl der Duplikate – verbessert die Integrität der Assets. Duplikate sind in ordnerbasierten Berechtigungen erforderlich, wenn dieselben Assets für verschiedene Gruppen freigegeben werden.

>[!VIDEO](https://video.tv.adobe.com/v/3475413/?learn=on&enablevpops){transcript=true}

## Wie wird die attributbasierte Zugriffssteuerung aktiviert? {#enable-attribute-based-access-control}

Derzeit können Sie keine attributbasierten Zugriffssteuerungsregeln eigenständig über die Content Hub-Benutzeroberfläche erstellen.

Klicken Sie auf **Tabelle herunterladen**, um Regeln in einer Tabelle herunterzuladen und zu definieren. Erstellen Sie ein Adobe-Support-Ticket und stellen Sie Adobe die in der Tabelle definierten Regeln bereit.

[!BADGE Tabelle herunterladen]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/ABAC_Get_Started_Template.xlsx"}


Definieren Sie Regeln in der Tabelle anhand der in diesem Artikel definierten Richtlinien.

<!--

>[!IMPORTANT]
>
> After defining the rules, navigate to the **Validation Errors** tab of the spreadsheet and click **Run ABAC Validations**. **All validations passed** message confirms that you can provide the defined rules to Adobe.

-->

## Anwendungsbeispiel für die attributbasierte Zugriffssteuerung {#example-metadata-based-rules}

Um einen groß angelegten Marketing-Rollout zu unterstützen, benötigen verschiedene Team-Mitglieder in verschiedenen Regionen und Marken Zugriff auf digitale Assets. Jede Persona hat einen bestimmten Umfang, der von Region und Marke abhängt. ABAC setzt diese Regeln automatisch über Asset-Metadaten um. Die folgende Tabelle zeigt die verschiedenen Personas für diesen Anwendungsfall und die angewendeten Regeln:

| Persona | Rolle | Rollenbeschreibung | Gruppen-ID | ABAC-Regel |
|---------------------|----------------|-----------------|------------|------------|
| John | EMEA Marketing Lead | Überwacht die Marketing-Ausführung aller Marken in EMEA. Benötigt Zugriff auf genehmigte Assets für alle Marken, die für EMEA-Märkte vorgesehen sind. | group-emea-marketing | Region = „EMEA“ |
| Mike | APAC-Marketingleiter | Überwacht die Marketing-Ausführung aller Marken in APAC. Benötigt Zugriff auf genehmigte Assets für alle Marken, die für APAC-Märkte vorgesehen sind. | group-apac-marketing | Region = „APAC“ |
| Sophie | Brand X Manager (EMEA) | Verwaltet die Identität der Marke X in EMEA. Darf nur für Marke X genehmigte Inhalte anzeigen, die auf EMEA-Märkte zugeschnitten sind. | group-emea-brands | Region = „EMEA“ &amp;&amp; Marke = „Marke X“ |
| Tom | Brand Y Manager (APAC) | Verwaltet die Identität der Marke Y in APAC. Darf nur für Marke Y genehmigte Inhalte sehen, die auf APAC-Märkte zugeschnitten sind. | group-apac-brandy | Region = „APAC“ &amp;&amp; Marke = „Marke Y“ |

Mithilfe dieser Regeln haben Content Hub-Admins folgende Möglichkeiten:

* **Granularer, regelbasierter Zugriff**: Benutzerinnen und Benutzer sehen nur die Assets, die für ihre Region und Marke relevant sind. Manuelle Berechtigungszuweisungen sind nicht erforderlich.

* **Nahtlose globale Zusammenarbeit**: Regional- und Marken-Teams arbeiten parallel, ohne dass Zugriffskonflikte auftreten.

* **Skalierbare und zukunftssichere Berechtigungen**: Wenn neue Regionen oder Marken hinzugefügt werden, können Regeln basierend auf Metadaten aktualisiert werden.

>[!IMPORTANT]
>
> Standardmäßig wird allen anderen Benutzergruppen, die nicht in den Regeln der [Tabelle](#enable-attribute-based-access-control) angegeben sind, der Zugriff verweigert. Wenn eine Person nicht zu einer Gruppe gehört, für die ABAC-Regeln definiert sind, kann sie nicht auf Assets zugreifen. Wenn einige Benutzerinnen und Benutzer Zugriff auf alle Assets erhalten müssen (z. B. Admins), müssen Sie in der Tabelle eine Gruppe einschließlich Gruppen-ID angeben und darin erläutern, dass diese bestimmte Gruppe Zugriff auf alle Assets benötigt. Adobe konfiguriert die Gruppe dann für Sie.


## Unterstützte Regelkonstrukte {#supported-rule-constructs}

* **Logische Operatoren**:
   * UND: Alle Bedingungen müssen erfüllt sein
   * ODER: Mindestens eine Bedingung muss erfüllt sein
* **Vergleichsoperatoren**:
   * Gleich (=): Prüft, ob ein Benutzer- oder Asset-Attribut mit einem Wert übereinstimmt
   * Ungleich (!=): Prüft, ob ein Benutzer- oder Asset-Attribut mit einem Wert nicht übereinstimmt

Wenn Asset-Metadatenfelder Arrays enthalten (z. B. mehrere Regionen oder Tags), entspricht `Equals` dem logischen Operator `contains` und `Not Equals` dem logischen Operator `does not contain`.

Auf diese Weise können Sie einfache und ausdrucksvolle Regeln schreiben, wie etwa: ZULASSEN, wenn Region = EMEA UND assetType != Prototyp UND Tags != vertraulich.

## Richtlinien {#guidelines-attribute-based-access-control}

* ABAC-Regeln gelten nur für Assets, die für Content Hub genehmigt wurden. Weitere Informationen finden Sie unter [Genehmigen von Assets für Content Hub](/help/assets/approve-assets-content-hub.md).

* Erstellen Sie keine VERWEIGERN-Regeln, sondern konvertieren Sie „VERWEIGERN“ immer in „ZULASSEN“. Beispielsweise können Sie `ALLOW if region = <user-region> DENY if assetType = prototype AND confidential = yes` in `ALLOW if region = <user-region> AND (assetType != prototype OR confidential != yes)` umwandeln.

* ABAC-Regeln werden mithilfe der IMS-Gruppen-ID, die in der Admin Console verfügbar ist, auf Benutzergruppen angewendet.


* Sie können das [Validierungsziel](/help/assets/approve-assets-content-hub.md#set-approval-target) für Assets mithilfe der AEM as a Cloud Service-Autorenumgebung festlegen. ABAC-Regeln werden auf Assets angewendet, die mit Validierungsziel = `Content Hub` genehmigt wurden, da Validierungsziel = `Delivery` für Assets gilt, die für `Delivery` + `Content Hub` verfügbar sind. Assets, die mit Validierungsziel = `Delivery` gekennzeichnet sind, sind im Materialien-Hub für alle sichtbar.

* Stellen Sie sicher, dass die in ABAC-Regeln verwendeten Metadatenschemata korrekt definiert und in AEM verfügbar sind. Geben Sie den vollständigen Pfad der Metadatenschemata in AEM an, die Eigenschaften definieren, auf die in ABAC-Regeln verwiesen wird. Sie können optional einen Testordner mit einigen Beispiel-Assets mit Metadatenwerten erstellen, die den ABAC-Bedingungen entsprechen. Dies hilft bei der Überprüfung des Regelverhaltens und der korrekten Bewertung des Zugriffs.

* Erfassen Sie die geschäftliche Absicht der Regel im Kommentar, unabhängig davon, ob die Bedingung korrekt geschrieben wurde, da der Zweck uns dabei hilft, die Logik bei Bedarf zu validieren und zu korrigieren.

* Die PDF-Lizenzdateien, die für DRM festgelegt sind, müssen für alle sichtbar sein, damit die Benutzer sie sehen können, wenn sie das Asset mit der Lizenz herunterladen.
