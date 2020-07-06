---
title: Verwenden von Cloud Readiness Analyzer
description: Verwenden von Cloud Readiness Analyzer
translation-type: tm+mt
source-git-commit: a0e58c626f94b778017f700426e960428b657806
workflow-type: tm+mt
source-wordcount: '1871'
ht-degree: 58%

---


# Verwenden von Cloud Readiness Analyzer {#using-cloud-readiness-analyzer}

## Wichtige Überlegungen zur Verwendung von Cloud Readiness Analyzer {#imp-considerations}

Gehen Sie wie folgt vor, um die wichtigen Überlegungen zum Ausführen des Cloud Readiness Analyzer (CRA) zu verstehen:

* Der CRA-Bericht wird mit der Ausgabe der Adobe Experience Manager (AEM)-[Mustererkennung](https://docs.adobe.com/content/help/de-DE/experience-manager-65/deploying/upgrading/pattern-detector.html) erstellt. Die von CRA verwendete Version der Mustererkennung ist im CRA-Installationspaket enthalten.

* CRA may only be run by the **admin** user or a user in the **administrators** group.

* CRA wird in AEM-Instanzen mit Version 6.1 und höher unterstützt.

   >[!NOTE]
   > Besondere Anforderungen für die Installation von CRA auf AEM 6.1 finden Sie unter [Installieren auf AEM 6.1](#installing-on-aem61) .

* CRA kann in jeder Umgebung ausgeführt werden, es wird jedoch empfohlen, das Tool in einer *Staging*-Umgebung auszuführen.

   >[!NOTE]
   >In order to avoid an impact on business critical instances, it is recommended that you run CRA on an *Author* environment that is as close as possible to the *Production* environment in the areas of customizations, configurations, content and user applications. Alternativ kann CRA in einem Klon der *Autoren*-Produktionsumgebung ausgeführt werden.

* Die Generierung von CRA-Berichtinhalten kann sehr lange dauern, von einigen Minuten bis zu einigen Stunden. Die benötigte Zeit hängt in hohem Maße von der Größe und Art des AEM-Repository-Inhalts, der AEM-Version und anderen Faktoren ab.

* Aufgrund der beträchtlichen Zeit, die zum Generieren des Berichtinhalts erforderlich sein könnte, werden diese von einem Hintergrundprozess generiert und in einem Cache gespeichert. Der Bericht sollte relativ schnell angezeigt und heruntergeladen werden, da er den Inhaltscache nutzt, bis er abläuft oder der Bericht explizit aktualisiert wird. Während der Generierung von Berichtinhalten können Sie Ihre Browser-Registerkarte schließen und zu einem späteren Zeitpunkt zur Ansicht des Berichts zurückkehren, sobald der Inhalt im Cache verfügbar ist.

## Verfügbarkeit {#availability}

Der Cloud Readiness Analyzer kann als ZIP-Datei vom Software Distribution Portal heruntergeladen werden. Sie können das Paket über Package Manager in Ihrer Quelldistanz von Adobe Experience Manager (AEM) installieren.

>[!NOTE]
>Download the Cloud Readiness Analyzer from the [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) portal.

## Ansicht des Berichts &quot;Cloud-Bereitschaftsanalysebericht&quot; {#viewing-report}

### Adobe Experience Manager 6.3.0 und höher {#aem-later-versions}

In diesem Abschnitt erfahren Sie, wie Sie den Bericht &quot;Cloud-Bereitschaftsanalyzer&quot;Ansicht haben:

1. Select Adobe Experience Manager and navigate to tools -> **Operations** -> **Cloud Readiness Analyzer**.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-1.png)

1. Wenn Sie auf **Cloud-Bereitstellungsanalysator** klicken, erstellt der Tool-Beginn den Bericht und zeigt ihn an, sobald er verfügbar ist.

   >[!NOTE]
   >Sie müssen auf der Seite nach unten scrollen, um den vollständigen Bericht anzuzeigen.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-tool-1.png)

1. Sobald der CRA-Bericht generiert und angezeigt wurde, haben Sie die Möglichkeit, den Bericht im CSV-Format (CSV) herunterzuladen, indem Sie auf **CSV** klicken, wie in der folgenden Abbildung dargestellt.

   ![image](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-tool-2.png)

   >[!NOTE]
   >Sie können die CRA zwingen, ihren Cache zu leeren und den Bericht neu zu generieren, indem Sie auf Bericht **aktualisieren** klicken.

### Adobe Experience Manager 6.2 und 6.1 {#aem-specific-versions}

Das Cloud Readiness Analyzer-Tool ist in Adobe Experience Manager 6.2 auf einen Link beschränkt, der den CSV-Bericht generiert und herunterlädt.

In Adobe Experience Manager 6.1 funktioniert das Tool nicht und es kann nur die HTTP-Schnittstelle verwendet werden.

>[!NOTE]
>In allen Versionen kann die enthaltene Mustererkennung unabhängig ausgeführt werden.

## Interpretieren des Berichts &quot;Cloud-Bereitschaftsanalysator&quot; {#cra-report}

Wenn das Cloud Readiness Analyzer-Tool in der AEM-Instanz ausgeführt wird, wird der Bericht als Ergebnis im Tool-Fenster angezeigt.

Das Format des Berichts lautet:

* **Berichtsübersicht**: Informationen zum Bericht selbst, die die folgenden Informationen enthalten:
   * **Berichtszeit**: Zeitpunkt der Erstellung und erstmaligen Bereitstellung des Berichtinhalts.
   * **Ablaufzeit**: Wenn der Inhalt des Berichts abläuft, läuft der Cache ab.
   * **Erstellungszeitraum**: Die Zeit, die beim Generieren des Berichtinhalts verbracht wird.
   * **Suchzähler**: Die Gesamtzahl der im Bericht enthaltenen Feststellungen.
* **Systemübersicht**: Informationen zum AEM-System, für das CRA ausgeführt wurde.
* **Suchen von Kategorien**: Mehrere Abschnitte, die jeweils eine oder mehrere Ergebnisse derselben Kategorie behandeln. Jeder Abschnitt enthält Folgendes: Name der Kategorie, Untertypen, Anzahl und Wichtigkeit der Ergebnisse, Zusammenfassung, Link zur Dokumentation der Kategorien und individuelle Suchinformationen.

Jedem Ergebnis wird eine Wichtigkeitsstufe zugewiesen, um eine ungefähre Priorität für das Handeln anzugeben.

Sie finden die Wichtigkeitsstufen in der folgenden Tabelle:

| Wichtigkeit | Beschreibung |
|--- |--- |
| INFO | Diese Ergebnisse werden zu Informationszwecken bereitgestellt. |
| ADVISORY | Diese Ergebnisse stellen möglicherweise ein Problem bei der Aktualisierung dar. Weitere Untersuchungen werden empfohlen. |
| MAJOR | Diese Ergebnisse stellen wahrscheinlich ein Problem bei der Aktualisierung dar, das behoben werden sollte. |
| CRITICAL | Diese Ergebnisse stellen wahrscheinlich ein Problem bei der Aktualisierung dar, das behoben werden muss, um Funktionsverlust oder Leistungseinbußen zu vermeiden. |


## Interpretieren des CSV-Berichts zur Cloud-Bereitschaftsanalyse {#cra-csv-report}

When you click the **CSV** option from your AEM instance, the CSV format of the Cloud Readiness Analyzer report is built from the content cache and returned to your browser. Abhängig von Ihren Browser-Einstellungen wird dieser Bericht automatisch als Datei mit dem Standardnamen `results.csv` heruntergeladen. 

Wenn der Cache abgelaufen ist, wird der Bericht erneut generiert, bevor die CSV-Datei erstellt und heruntergeladen wird.

Das CSV-Format des Berichts enthält Informationen, die aus der Mustererkennungsausgabe generiert wurden und nach Kategorie, Untertyp und Wichtigkeitsstufe sortiert und organisiert sind. Sein Format eignet sich zum Anzeigen und Bearbeiten in einer Anwendung wie Microsoft Excel. Alle Ergebnisinformationen werden in einem wiederholbaren Format bereitgestellt, das beim Vergleich von Berichten im Zeitverlauf zur Messung des Fortschritts hilfreich sein kann.

Die Spalten des Berichts im CSV-Format sind:

* **code**: der Code der Kategorie
* **type**: der Name der Kategorie
* **subtype**: der Untertyp der Kategorie
* **importance**: die Wichtigkeitsstufe
* **identifier**: die primäre Kennung des Ergebnisses
* **other**: zusätzliche Informationen zum Ergebnis
* **message**: die für das Ergebnis angegebene Meldung
* **moreInfo**: ein Link, über den Sie auf die Online-Hilfe zur Kategorie zugreifen können
* **context**: eine JSON-Zeichenfolge von Ergebnisdaten

Der Wert „\N“ in einer Spalte für ein einzelnes Ergebnis zeigt an, dass keine Daten bereitgestellt wurden.

## HTTP-Schnittstelle {#http-interface}

Die CRA stellt eine HTTP-Schnittstelle bereit, die als Alternative zu ihrer Benutzeroberfläche in AEM verwendet werden kann. Die Schnittstelle unterstützt sowohl HEAD- als auch GET-Befehle. Sie kann zum Generieren des CRA-Berichts und zur Rückgabe in einem der drei folgenden Formate verwendet werden: JSON-, CSV- und tabulatorgetrennte Werte (TSV).

Die folgenden URLs stehen für den HTTP-Zugriff zur Verfügung, wobei `<host>` der Host-Name und gegebenenfalls der Port des Servers ist, auf dem CRA installiert ist:
* `http://<host>/apps/readiness-analyzer/analysis/result.json` für das JSON-Format
* `http://<host>/apps/readiness-analyzer/analysis/result.csv` für das CSV-Format
* `http://<host>/apps/readiness-analyzer/analysis/result.tsv` für das TSV-Format

### Ausführen einer HTTP-Anfrage {#executing-http-request}

Die HTTP-Schnittstelle kann auf verschiedene Weise verwendet werden.

Eine einfache Möglichkeit besteht darin, eine Browser-Registerkarte im selben Browser zu öffnen, in dem Sie sich bereits als Administrator bei AEM angemeldet haben. Sie können die URL in der Browser-Registerkarte eingeben und die Ergebnisse vom Browser anzeigen oder herunterladen lassen.

Sie können auch ein Befehlszeilen-Tool wie `curl` oder `wget` oder eine beliebige HTTP-Client-Anwendung verwenden. Wenn Sie keine Browserregisterkarte mit einer authentifizierten Sitzung verwenden, müssen Sie als Teil des Kommentars einen administrativen Benutzernamen und ein Kennwort angeben.

Im Folgenden ein Beispiel:
`curl -u admin:admin 'http://localhost:4502/apps/readiness-analyzer/analysis/result.csv' > result.csv`.

### Kopfzeilen und Parameter {#http-headers-and-parameters}

Diese Schnittstelle verwendet die folgenden HTTP-Kopfzeilen:

* `Cache-Control: max-age=<seconds>`: Gibt die Lebensdauer der Cache-Aktualisierung in Sekunden an. (Siehe [RFC 7234](https://tools.ietf.org/html/rfc7234#section-5.2.2.8).)
* `Prefer: respond-async`: Gibt an, dass der Server asynchron reagieren soll. (Siehe [RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.1).)

Die folgenden HTTP-Abfrageparameter stehen zur Verfügung, wenn HTTP-Kopfzeilen möglicherweise nicht einfach verwendet werden können:

* `max-age` (Zahl, optional): Gibt die Lebensdauer der Cache-Aktualisierung in Sekunden an. Diese Zahl muss 0 oder höher sein. Die Standardlebensdauer für die Aktualisierung beträgt 86400 Sekunden. Dies bedeutet, dass ohne diesen Parameter oder die entsprechende Kopfzeile ein Aktualisierungs-Cache verwendet wird, um Anfragen 24 Stunden lang zu bedienen, bevor der Bericht neu generiert werden muss. Durch die Verwendung von `max-age=0` wird das Löschen des Caches erzwungen und eine Neuerstellung des Berichts eingeleitet. Unmittelbar nach dieser Anfrage wird die Lebensdauer der Aktualisierung auf den vorherigen Wert ungleich null zurückgesetzt.
* `respond-async` (boolesch, optional): Gibt an, dass die Antwort asynchron bereitgestellt werden soll. Die Verwendung von `respond-async=true`, wenn der Cache veraltet ist, führt dazu, dass der Server die Antwort `202 Accepted, processing cache` zurückgibt und den Cache verarbeitet, ohne darauf zu warten, dass der Bericht generiert und der Cache aktualisiert wird. Wenn der Cache aktualisiert ist, hat dieser Parameter keine Auswirkung. Der Standardwert ist `false`. Dies bedeutet, dass der Server ohne diesen Parameter oder die entsprechende Kopfzeile synchron reagiert. Dies kann viel Zeit und eine Anpassung der maximalen Antwortzeit für den HTTP-Client erfordern.

Wenn sowohl eine HTTP-Kopfzeile als auch ein entsprechender Abfrageparameter vorhanden sind, hat der Abfrageparameter Vorrang.

Mit dem folgenden Befehl können Sie die Generierung des Berichts einfach über die HTTP-Schnittstelle starten:
`curl -u admin:admin 'http://localhost:4502/apps/readiness-analyzer/analysis/result.json?max-age=0&respond-async=true'`.

Nachdem eine Anfrage gestellt wurde, muss der Client nicht aktiv bleiben, damit der Bericht generiert wird. Die Berichtgenerierung kann mit einem Client über eine HTTP GET-Anforderung initiiert und nach der Berichterstellung aus dem Cache eines anderen Clients oder dem CSV-Tool in der Benutzeroberfläche von AEM angezeigt werden.

### Antworten {#http-responses}

Die folgenden Antwortwerte sind möglich:

* `200 OK`: Die Antwort enthält Ergebnisse der Mustererkennung, die während der Lebensdauer der Aktualisierung des Caches generiert wurden.
* `202 Accepted, processing cache`: Vorgesehen für asynchrone Antworten, um anzuzeigen, dass der Cache veraltet war und eine Aktualisierung ausgeführt wird.
* `400 Bad Request`: Gibt an, dass bei der Anfrage ein Fehler aufgetreten ist. A message in Problem Details format (see [RFC 7807](https://tools.ietf.org/html/rfc7807)) for more details.
* `401 Unauthorized`: Die Anfrage wurde nicht genehmigt.
* `500 Internal Server Error`: Gibt an, dass ein interner Server-Fehler aufgetreten ist. Eine Meldung im Format für Problemdetails enthält weitere Details.
* `503 Service Unavailable`: Zeigt an, dass der Server mit einer anderen Antwort beschäftigt ist und diese Anfrage nicht rechtzeitig bearbeiten kann. Dies tritt nur bei synchronen Anfragen auf. Eine Meldung im Format für Problemdetails enthält weitere Details.

## Administratorinformationen

### Anpassung der Cache-Lebensdauer {#cache-adjustment}

Die standardmäßige CRA-Cache-Lebensdauer beträgt 24 Stunden. Mit der Option zum Aktualisieren eines Berichts und zum Wiederherstellen des Cache sowohl in der AEM-Instanz als auch in der HTTP-Schnittstelle ist dieser Standardwert für die meisten Verwendungen der CRA geeignet. Wenn die Zeit für die Berichterstellung für Ihre AEM-Instanz besonders lang ist, möchten Sie möglicherweise die Cache-Lebensdauer anpassen, um das erneute Generieren des Berichts zu minimieren.

Der Wert für die Cache-Lebensdauer wird als `maxCacheAge`-Eigenschaft im folgenden Repository-Knoten gespeichert:
`/apps/readiness-analyzer/content/CloudReadinessReport/jcr:content`

Der Wert dieser Eigenschaft ist die Cache-Lebensdauer in Sekunden. Ein Administrator kann die Cache-Lebensdauer mit CRX/DE Lite anpassen.

### Installieren auf AEM 6.1 {#installing-on-aem61}

CRA verwendet ein Systemdienst-Benutzerkonto mit dem Namen `repository-reader-service` zum Ausführen des Musterdetektors. Dieses Konto ist auf AEM 6.2 und höher verfügbar. In AEM 6.1 muss dieses Konto *vor* der Installation von CRA wie folgt erstellt werden:

1. Befolgen Sie die Anweisungen unter [Erstellen eines neuen Dienstbenutzers](https://docs.adobe.com/content/help/en/experience-manager-65/administering/security/security-service-users.html#creating-a-new-service-user) , um einen Benutzer zu erstellen. Legen Sie die UserID fest, lassen Sie den Zwischenpfad leer `repository-reader-service` und klicken Sie dann auf das grüne Häkchen.

2. Befolgen Sie die Anweisungen unter [Verwalten von Benutzern und Gruppen](https://docs.adobe.com/content/help/en/experience-manager-65/administering/security/security.html#managing-users-and-groups), insbesondere die Anweisungen zum Hinzufügen von Benutzern zu einer Gruppe, um den `repository-reader-service` Benutzer zur `administrators` Gruppe hinzuzufügen.

3. Installieren Sie das CRA-Paket über Package Manager auf Ihrer AEM-Quellinstanz. (Dadurch wird die erforderliche Konfigurationsänderung zur ServiceUserMapper-Konfiguration für den `repository-reader-service` Systemdienstbenutzer hinzugefügt.)
