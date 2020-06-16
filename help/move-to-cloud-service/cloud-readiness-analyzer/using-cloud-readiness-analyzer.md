---
title: Verwenden von Cloud Readiness Analyzer
description: Verwenden von Cloud Readiness Analyzer
translation-type: tm+mt
source-git-commit: f65580a4608167a869669b03cec5d8ab730a848a
workflow-type: tm+mt
source-wordcount: '1749'
ht-degree: 1%

---


# Verwenden von Cloud Readiness Analyzer {#using-cloud-readiness-analyzer}

## Wichtige Überlegungen zur Verwendung von Cloud Readiness Analyzer {#imp-considerations}

Gehen Sie wie folgt vor, um die wichtigen Überlegungen beim Ausführen des Cloud Readiness Analyzer (CRA) zu verstehen:

* Der CRA-Bericht wird mit der Ausgabe des [Musterdetektors](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html)für Adobe Experience Manager (AEM) erstellt. Die von CRA verwendete Version des Musterdetektors ist im CRA-Installationspaket enthalten.

* Die CRA kann nur vom **Administrator** oder einem Benutzer in den **Administratoren** ausgeführt werden.

* CRA wird auf AEM-Instanzen mit Version 6.1 und höher unterstützt.

* CRA kann auf jeder Umgebung ausgeführt werden, es wird jedoch empfohlen, sie auf einer *Stage* -Umgebung auszuführen.

   >[!NOTE]
   >Um Auswirkungen auf geschäftskritische Instanzen zu vermeiden, wird empfohlen, CRA auf einer *Author* -Umgebung auszuführen, die der *Production* -Umgebung in den Bereichen Anpassungen, Konfigurationen, Inhalte und Benutzeranwendungen so nahe wie möglich ist. Alternativ kann es auf einem Klon der Produktionsautor- *Umgebung* ausgeführt werden.

* Die Generierung von CRA-Berichtinhalten kann sehr lange dauern, von einigen Minuten bis zu einigen Stunden. Die benötigte Zeit hängt in hohem Maße von der Größe und Art des AEM-Repository-Inhalts, der AEM-Version und anderen Faktoren ab.

* Aufgrund der beträchtlichen Zeit, die zum Generieren des Berichtinhalts erforderlich sein könnte, werden diese von einem Hintergrundprozess generiert und in einem Cache gespeichert. Der Bericht sollte relativ schnell angezeigt und heruntergeladen werden, da er den Inhaltscache nutzt, bis er abläuft oder der Bericht explizit aktualisiert wird. Während der Generierung von Berichtinhalten können Sie Ihre Browser-Registerkarte schließen und zu einem späteren Zeitpunkt zur Ansicht des Berichts zurückkehren, sobald der Inhalt im Cache verfügbar ist.

## Verfügbarkeit {#availability}

Der Cloud Readiness Analyzer kann als ZIP-Datei vom Software Distribution Portal heruntergeladen werden. Sie können das Paket über Package Manager in Ihrer Quelldistanz von Adobe Experience Manager (AEM) installieren.

>[!NOTE]
>Laden Sie den Cloud Readiness Analyzer aus dem Software Distribution Portal *ausstehend* herunter.

## Ausführen des Cloud Readiness Analyzer {#running-tool}

In diesem Abschnitt erfahren Sie, wie Sie Cloud Readiness Analyzer ausführen:

1. Wählen Sie Adobe Experience Manager und navigieren Sie zu Tools -> **Vorgänge** -> **Cloud Readiness Analyzer**.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-1.png)

1. Wenn Sie auf **Cloud-Bereitstellungsanalysator** klicken, erstellt der Tool-Beginn den Bericht und zeigt ihn an, sobald er verfügbar ist.

   >[!NOTE]
   >Sie müssen einen Bildlauf nach unten durchführen, um den vollständigen Bericht Ansicht.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-2.png)

## Interpretieren des Berichts &quot;Cloud-Bereitschaftsanalysator&quot; {#cra-report}

Wenn der Cloud Readiness Analyzer in der AEM-Instanz ausgeführt wird, wird der Bericht als Ergebnis im Tool-Fenster angezeigt.

Das Format des Berichts lautet:

* *Berichtsübersicht*: Informationen zum Bericht selbst, einschließlich des Zeitpunkts seiner Erstellung.
* *Systemübersicht*: Informationen zum AEM-System, auf dem die CRA ausgeführt wurde.
* *Suchen von Kategorien*: Mehrere Abschnitte, die jeweils eine oder mehrere Ergebnisse derselben Kategorie ansprechen. Jeder Abschnitt enthält Folgendes: Name der Kategorie, Untertypen, Anzahl und Bedeutung der Suche, Zusammenfassung, Link zur Dokumentation der Kategorie und individuelle Suchinformationen.

Jedem Ergebnis wird eine wichtige Priorität zugewiesen, um eine ungefähre Priorität für Maßnahmen anzugeben.

Befolgen Sie die folgende Tabelle, um die wichtigen Ebenen zu verstehen:

| Importance | Beschreibung |
|--- |--- |
| INFO | Diese Ergebnisse werden zu Informationszwecken bereitgestellt. |
| BERATUNG | Diese Feststellung stellt möglicherweise ein Problem bei der Aktualisierung dar. Weitere Untersuchungen werden empfohlen. |
| MAJOR | Diese Feststellung ist wahrscheinlich ein Aktualisierungsfehler, der behoben werden sollte. |
| KRITISCH | Diese Feststellung ist wahrscheinlich ein Aktualisierungsfehler, der behoben werden muss, um Funktionsverlust oder Leistungseinbußen zu vermeiden. |

### Adobe Experience Manager 6.3 und höher {#aem-older-version}

Für AEM 6.3 und höher besteht die primäre Möglichkeit zum Ausführen von Cloud Readiness Analyzer in folgenden Schritten:

1. Wählen Sie die Instanz des Adobe Experience Managers aus und navigieren Sie zu Tools -> **Vorgänge** -> **Cloud Readiness Analyzer**.

   >[!NOTE]
   >Die Ratingagentur beginnt mit einem Hintergrundprozess, um den Bericht zu generieren, sobald das Tool geöffnet wird. Es wird ein Hinweis angezeigt, dass die Berichtgenerierung läuft, bis der Bericht fertig ist. Sie können die Browser-Registerkarte schließen und zu einem späteren Zeitpunkt zur Ansicht des Berichts zurückkehren, sobald dieser abgeschlossen ist.

1. Nachdem der CRA-Bericht generiert und angezeigt wurde, haben Sie die Möglichkeit, den Bericht in Form von CSV (kommagetrennten Werten) herunterzuladen. Klicken Sie auf **CSV** , um den vollständigen CRA-Bericht im CSV-Format (CSV) herunterzuladen, wie in der folgenden Abbildung dargestellt.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-3.png)

   >[!NOTE]
   >Sie können die CRA zwingen, ihren Cache zu leeren und den Bericht neu zu generieren, indem Sie auf Bericht **aktualisieren** klicken.

### Adobe Experience Manager 6.2 und 6.1 {#aem-specific-versions}

Der Cloud Readiness Analyzer ist in Adobe Experience Manager 6.2 auf einen Link beschränkt, der den CSV-Bericht generiert und herunterlädt.

In Adobe Experience Manager 6.1 funktioniert das Tool nicht und es kann nur die HTTP-Schnittstelle verwendet werden.

>[!NOTE]
>In allen Versionen kann der enthaltene Musterdetektor unabhängig ausgeführt werden.

## Interpretieren des CSV-Berichts zur Cloud-Bereitschaftsanalyse {#cra-csv-report}

Wenn Sie in Ihrer AEM-Instanz auf die **CSV** -Option klicken, wird das CSV-Format des Berichts Cloud-Bereitstellungsanalysator aus dem Inhaltscache erstellt und an Ihren Browser zurückgegeben. Abhängig von Ihren Browsereinstellungen wird dieser Bericht automatisch als Datei mit dem Standardnamen `results.csv`heruntergeladen.

Wenn der Cache abgelaufen ist, wird der Bericht erneut generiert, bevor die CSV-Datei erstellt und heruntergeladen wird.

Das CSV-Format des Berichts enthält Informationen, die aus der Musterdetektorausgabe generiert wurden und nach Kategorie, Untertyp und Wichtigkeitsstufe sortiert und organisiert sind. Das Format eignet sich für die Anzeige und Bearbeitung in einer Anwendung wie Microsoft Excel. Es soll alle Suchinformationen in einem wiederholbaren Format bereitstellen, das beim Vergleich von Berichten im Zeitverlauf zur Messung des Fortschritts hilfreich sein kann.

Die Spalten des CSV-Formatberichts sind:

* **code**: der Kategorie
* **type**: der Name der Kategorie
* **subtype**: der Untertyp Kategorie
* **Wichtigkeit**: die Bedeutung
* **Bezeichner**: der primäre Bezeichner der Feststellung
* **sonstige**: zusätzliche Informationen über die Suche
* **message**: die für die Suche angegebene Meldung
* **moreInfo**: einen Link, über den Sie auf die Online-Hilfe zur Kategorie zugreifen können
* **context**: eine JSON-Zeichenfolge zum Suchen von Daten

Der Wert &quot;\N&quot;in einer Spalte für eine einzelne Suche zeigt an, dass keine Daten bereitgestellt wurden.

## HTTP-Schnittstelle {#http-interface}

Die CRA stellt eine HTTP-Schnittstelle bereit, die als Alternative zu ihrer Benutzeroberfläche in AEM verwendet werden kann. Die Oberfläche unterstützt sowohl HEAD- als auch GET-Befehle. Er kann zum Generieren des CRA-Berichts und zur Rückgabe in einem der drei folgenden Formate verwendet werden: JSON-, CSV- und tabulatorgetrennte Werte (TSV).

Die folgenden URLs stehen für den HTTP-Zugriff zur Verfügung, wobei `<host>` der Hostname und gegebenenfalls der Anschluss des Servers, auf dem die CRA installiert ist, angegeben werden:
* `http://<host>/apps/readiness-analyzer/analysis/result.json` für JSON-Format
* `http://<host>/apps/readiness-analyzer/analysis/result.csv` für CSV-Format
* `http://<host>/apps/readiness-analyzer/analysis/result.tsv` für das TSV-Format

### Ausführen einer HTTP-Anforderung {#executing-http-request}

Die HTTP-Schnittstelle kann auf verschiedene Weise verwendet werden.

Eine einfache Möglichkeit besteht darin, eine Browser-Registerkarte im selben Browser zu öffnen, in dem Sie sich bereits als Administrator bei AEM angemeldet haben. Sie können die URL auf der Registerkarte &quot;Browser&quot;eingeben und die Ergebnisse vom Browser anzeigen oder herunterladen lassen.

Sie können auch ein Befehlszeilenwerkzeug wie `curl` oder `wget` eine beliebige HTTP-Clientanwendung verwenden. Wenn Sie keine Browserregisterkarte mit einer authentifizierten Sitzung verwenden, müssen Sie als Teil des Kommentars einen administrativen Benutzernamen und ein Kennwort angeben.

Im Folgenden sehen Sie ein Beispiel dafür, wie dies möglich ist:
`curl -u admin:admin 'http://localhost:4502/apps/readiness-analyzer/analysis/result.csv' > result.csv`.

### Überschriften und Parameter {#http-headers-and-parameters}

Diese Schnittstelle verwendet die folgenden HTTP-Header:

* `Cache-Control: max-age=<seconds>`: Geben Sie die Dauer der Cache-Frische in Sekunden an. (Siehe [RFC 7234](https://tools.ietf.org/html/rfc7234#section-5.2.2.8).)
* `Prefer: respond-async`: Gibt an, dass der Server asynchron reagieren soll. (Siehe [RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.1).)

Die folgenden HTTP-Abfrage-Parameter stehen zur Verfügung, wenn HTTP-Header möglicherweise nicht einfach verwendet werden können:

* `max-age` (Nummer, optional): Geben Sie die Dauer der Cache-Frische in Sekunden an. Diese Zahl muss 0 oder höher sein. Die Standardlebensdauer der Frische beträgt 86400 Sekunden, d. h., ohne diesen Parameter oder den entsprechenden Header wird ein neuer Cache verwendet, um Anforderungen 24 Stunden zu bearbeiten, bevor der Bericht neu generiert werden muss. Die Verwendung `max-age=0` erzwingt die Löschung des Zwischenspeichers und löst eine Regeneration des Berichts aus. Unmittelbar nach dieser Anforderung wird die Frischheitslebensdauer auf den vorherigen Wert ungleich null zurückgesetzt.
* `respond-async` (boolean, optional): Geben Sie an, dass die Antwort asynchron bereitgestellt werden soll. Wenn `respond-async=true` der Cache statisch ist, gibt der Server eine Antwort von zurück, `202 Accepted, processing cache` ohne darauf zu warten, dass der Bericht generiert und der Cache aktualisiert wird. Wenn der Cache frisch ist, hat dieser Parameter keine Auswirkungen. Der Standardwert ist `false`also, dass der Server ohne diesen Parameter oder den entsprechenden Header synchron reagiert. Dies kann eine erhebliche Zeitspanne erfordern und eine Anpassung der maximalen Antwortzeit für den HTTP-Client erfordern.

Wenn sowohl ein HTTP-Header als auch ein entsprechender Parameter für die Abfrage vorhanden sind, hat der Parameter &quot;Abfrage&quot;Vorrang.

Die Generierung des Berichts über die HTTP-Oberfläche kann einfach mit dem folgenden Befehl initiiert werden:
`curl -u admin:admin 'http://localhost:4502/apps/readiness-analyzer/analysis/result.json?max-age=0&respond-async=true'`.

Nachdem eine Anforderung gestellt wurde, muss der Client nicht aktiv bleiben, damit der Bericht generiert wird. Die Berichtgenerierung kann mit einem Client über eine HTTP GET-Anforderung initiiert und nach der Berichterstellung aus dem Cache eines anderen Clients oder dem CSV-Tool in der Benutzeroberfläche von AEM angezeigt werden.

### Antworten (#http-response)

Die folgenden Antwortwerte sind möglich:

* `200 OK`: Die Antwort enthält Ergebnisse des Musterdetektors, die während der Frischheitsdauer des Zwischenspeichers generiert wurden.
* `202 Accepted, processing cache`: Es wurden asynchrone Antworten bereitgestellt, um anzuzeigen, dass der Cache nicht mehr verfügbar war und dass eine Aktualisierung ausgeführt wird.
* `400 Bad Request`: Gibt an, dass bei der Anforderung ein Fehler aufgetreten ist. Eine Meldung im Format Problemdetails (siehe [RFC 7807](https://tools.ietf.org/html/rfc7807)) enthält weitere Details.
* `401 Unauthorized`: Der Antrag wurde nicht genehmigt.
* `500 Internal Server Error`: Gibt an, dass ein interner Serverfehler aufgetreten ist. Eine Meldung im Format Problemdetails enthält weitere Details.
* `503 Service Unavailable`: Gibt an, dass der Server mit einer anderen Antwort beschäftigt ist und diese Anforderung nicht zeitnah bearbeiten kann. Dies tritt nur dann auf, wenn synchrone Anforderungen gestellt werden. Eine Meldung im Format Problemdetails enthält weitere Details.

## Cache-Lebenszeitanpassung {#cache-adjustment}

Die standardmäßige CRA-Cache-Lebensdauer beträgt 24 Stunden. Mit der Option zum Aktualisieren eines Berichts und zum Wiederherstellen des Cache sowohl in der AEM-Instanz als auch in der HTTP-Schnittstelle ist dieser Standardwert für die meisten Verwendungen der CRA geeignet. Wenn die Berichtgenerierungszeit für Ihre AEM-Instanz besonders lang ist, sollten Sie die Cache-Lebensdauer anpassen, um die Regeneration des Berichts zu minimieren.

Der Wert für die Cache-Lebensdauer wird als `maxCacheAge` Eigenschaft auf dem folgenden Repository-Knoten gespeichert:
`/apps/readiness-analyzer/content/CloudReadinessReport/jcr:content`

Der Wert dieser Eigenschaft ist die Cache-Lebensdauer in Sekunden. Ein Administrator kann die Cache-Lebensdauer mit CRXDE Lite anpassen.





