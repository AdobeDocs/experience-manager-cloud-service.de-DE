---
title: Attributbasierte Zugriffssteuerung – Übersicht
description: Erfahren Sie, wie Sie die attributbasierte Zugriffssteuerung aktivieren, um metadatenbasierte Regeln zu definieren, um die Zugriffsebene auf in Content Hub verfügbare Assets zu definieren
role: Admin
exl-id: 05f54b05-40b8-4a6c-af8f-5c3f7a2089d4
source-git-commit: ea1760a3076fa0e18dca38fe856ff0ef78b18f07
workflow-type: tm+mt
source-wordcount: '976'
ht-degree: 5%

---

# Attributbasierte Zugriffssteuerung – Übersicht {#attribute-based-access-control}

Mit der attributbasierten Zugriffssteuerung (ABAC) können Content Hub-Admins metadatenbasierte Regeln definieren, um die Zugriffsebene auf in Content Hub verfügbare Assets zu definieren.

Administratoren für eine Organisation definieren Regeln für Benutzergruppen, die einer Gruppen-ID zugeordnet sind. Regeln sind eine Mischung aus [- und Vergleichsoperatoren](#supported-rule-constructs) und Administratoren können so viele Regeln definieren, wie sie benötigen, um den Asset-Zugriff in Content Hub zu verwalten.

Die Regeln basieren auf Metadaten. Wenn die in der Regel definierten Bedingungen mit den Asset-Metadaten übereinstimmen, wird das Asset der Benutzergruppe angezeigt. Content Hub scannt die Asset-Metadaten einschließlich der benutzerdefinierten Metadaten für alle in **Alle Assets** und **Sammlungen** verfügbaren Assets, um die Ergebnisse für Benutzergruppen anzuzeigen.

Beispiel: ERLAUBEN Sie den Zugriff auf eine Benutzergruppe mit Gruppen-ID = 1011, wenn die Asset-Metadaten mit „Marke = Marke X“ UND „Region = EMEA ODER Nord- und Südamerika“ übereinstimmen. Content Hub zeigt der Benutzergruppe mit der ID = 1011 nur die Assets an, bei denen Brand = `Brand X` und Region = `EMEA` oder `Americas`.

Zu den wichtigsten Vorteilen der attributbasierten Zugriffssteuerung gehören:

* Beseitigt die Abhängigkeit von der Ordnerstruktur für Berechtigungen

* Ermöglicht es Admins, Assets hochzuladen und Berechtigungsstrukturen rückwirkend zu bestimmen

* Reduziert die Anzahl der Duplikate – verbessert die Integrität der Assets. Duplikate sind in ordnerbasierten Berechtigungen erforderlich, wenn dieselben Assets für verschiedene Gruppen freigegeben werden.

## Wie wird die attributbasierte Zugriffssteuerung aktiviert? {#enable-attribute-based-access-control}

Derzeit können Sie keine attributbasierten Zugriffssteuerungsregeln eigenständig über die Content Hub-Benutzeroberfläche erstellen.

Klicken Sie **Tabelle herunterladen**, um Regeln in einer Tabelle herunterzuladen und zu definieren. Erstellen Sie ein Adobe-Support-Ticket und stellen Sie Adobe die in der Tabelle definierten Regeln zur Verfügung.

[!BADGE Arbeitsblatt herunterladen]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/ABAC_Get_Started_Template_Validator.xlsx"}


Definieren Sie Regeln in der Tabelle anhand der in diesem Artikel definierten Richtlinien.

>[!IMPORTANT]
>
> Navigieren Sie nach der Definition der Regeln zur Registerkarte **Validierungsfehler** des Arbeitsblatts und klicken Sie auf **ABAC-Validierungen ausführen**. **Alle Validierungen erfolgreich** bestätigt die Meldung, dass Sie die definierten Regeln für Adobe bereitstellen können.

## Beispiel für einen Anwendungsfall der attributbasierten Zugriffssteuerung {#example-metadata-based-rules}

Um einen groß angelegten Marketing-Rollout zu unterstützen, benötigen verschiedene Team-Mitglieder in verschiedenen Regionen und Marken Zugriff auf digitale Assets. Jede Rolle hat einen bestimmten Umfang, der von Region und Marke abhängt. ABAC setzt diese Regeln automatisch über Asset-Metadaten um. Die folgende Tabelle zeigt die verschiedenen Personas für diesen Anwendungsfall und die angewendeten Regeln:

| Persona | Rolle | Rollenbeschreibung | Gruppen-ID | ABAC-Regel |
|---------------------|----------------|-----------------|------------|------------|
| John | EMEA Marketing Lead | Überwacht die Marketing-Ausführung aller Marken in EMEA. benötigt Zugriff auf genehmigte Assets für alle Marken, die für EMEA-Märkte vorgesehen sind. | group-emea-marketing | Region = „EMEA“ |
| Mike | APAC-Marketingleiter | Überwacht die Marketing-Ausführung aller Marken in APAC. benötigt Zugriff auf genehmigte Assets für alle Marken, die für APAC-Märkte vorgesehen sind. | group-apac-marketing | Region = „APAC“ |
| Sophie | Brand X Manager (EMEA) | Verwaltet die Marke-X-Identität in EMEA. Darf nur von Brand X genehmigte Inhalte anzeigen, die auf EMEA-Märkte zugeschnitten sind. | group-emea-brands | Region = „EMEA“ &amp;&amp; Marke = „Marke X“ |
| Tom | Brand Y Manager (APAC) | Verwaltet die Identität von Brand Y in APAC. Darf nur von Marke Y genehmigte Inhalte sehen, die auf APAC-Märkte zugeschnitten sind. | group-apac-brandy | Region = „APAC“ &amp;&amp; Marke = „Marke Y“ |

Mithilfe dieser Regeln haben Content Hub-Administratoren folgende Möglichkeiten:

* **Granularer, regelbasierter Zugriff**: Benutzer sehen nur die Assets, die für ihre Region und Marke relevant sind - keine manuellen Berechtigungszuweisungen.

* **Nahtlose globale Zusammenarbeit**: Regional- und Marken-Teams arbeiteten parallel, ohne dass Zugriffskonflikte auftraten.

* **Skalierbare und zukunftssichere Berechtigungen**: Wenn neue Regionen oder Marken hinzugefügt werden, können Regeln basierend auf Metadaten aktualisiert werden.

>[!IMPORTANT]
>
> Standardmäßig wird allen anderen Benutzergruppen, die nicht mit Regeln in der [Tabelle) angegeben ](#enable-attribute-based-access-control), der Zugriff verweigert. Wenn ein(e) Benutzende(r) nicht zu einer Gruppe gehört, für die ABAC-Regeln definiert sind, kann er/sie nicht auf Assets zugreifen. Wenn Sie Benutzende benötigen, um Zugriff auf alle Assets zu erhalten (z. B. Administratoren), muss in der Tabelle eine Gruppe mit einer Gruppen-ID angegeben werden, die die Details enthält, dass diese bestimmte Gruppe Zugriff auf alle Assets benötigt und Adobe sie für Sie konfigurieren wird.


## Unterstützte Regelkonstrukte {#supported-rule-constructs}

* **Logische**:
   * UND: Alle Bedingungen müssen erfüllt sein
   * ODER: Mindestens eine Bedingung muss wahr sein
* **Vergleichsoperatoren**:
   * Gleich (=): Prüft, ob ein Benutzer- oder Asset-Attribut mit einem Wert übereinstimmt
   * Ungleich (!=): Prüft, ob ein Benutzer- oder Asset-Attribut mit einem Wert nicht übereinstimmt

Wenn Asset-Metadatenfelder Arrays enthalten (z. B. mehrere Regionen oder Tags), bezieht sich `Equals` auf `contains` Logik und `Not Equals` auf `does not contain`.

Auf diese Weise können Sie einfache und ausdrucksvolle Regeln schreiben, wie etwa: ZULASSEN, wenn Region = EMEA UND assetType != Prototyp UND Tags != vertraulich.

## Richtlinien {#guidelines-attribute-based-access-control}

* ABAC-Regeln gelten nur für Assets, die für Content Hub genehmigt wurden. Weitere Informationen finden Sie unter [Assets für Content Hub genehmigen](/help/assets/approve-assets-content-hub.md).

* Verweigern Sie keine Regeln, sondern konvertieren Sie „VERWEIGERN“ immer in „ZULASSEN“. Beispielsweise können `ALLOW if region = <user-region> DENY if assetType = prototype AND confidential = yes` in `ALLOW if region = <user-region> AND (assetType != prototype OR confidential != yes)` konvertiert werden.

* ABAC-Regeln werden mithilfe der IMS-Gruppen-ID, die in der Admin Console verfügbar ist, auf Benutzergruppen angewendet.


* Sie können die [Validierungsziel](/help/assets/approve-assets-content-hub.md#set-approval-target) für Assets mithilfe der AEM as a Cloud Service-Autorenumgebung festlegen. ABAC-Regeln werden auf Assets angewendet, die mit Validierungsziel = `Content Hub` genehmigt wurden, da Validierungsziel = `Delivery` für Assets gilt, die für `Delivery` + `Content Hub` verfügbar sind. Assets, die als Validierungsziel = `Delivery` gekennzeichnet sind, sind im Materialien-Hub für alle sichtbar.

* Stellen Sie sicher, dass die in ABAC-Regeln verwendeten Metadatenschemata korrekt definiert und in AEM verfügbar sind. Geben Sie den vollständigen Pfad der Metadatenschemata in AEM an, die Eigenschaften definieren, auf die in ABAC-Regeln verwiesen wird. Sie können optional einen Testordner mit einigen Beispiel-Assets mit Metadatenwerten erstellen, die den ABAC-Bedingungen entsprechen. Dies hilft bei der Überprüfung des Regelverhaltens und der korrekten Bewertung des Zugriffs.

* Erfassen Sie die geschäftliche Absicht der Regel im Kommentar, unabhängig davon, ob die Bedingung korrekt geschrieben wurde, da der Zweck uns dabei hilft, die Logik bei Bedarf zu validieren und zu korrigieren.

* Die PDF-Lizenzdateien, die für DRM festgelegt sind, müssen für alle sichtbar sein, damit die Benutzer sie sehen können, wenn sie das Asset mit der -Lizenz herunterladen.
