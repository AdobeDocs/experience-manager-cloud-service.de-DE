---
title: Verwenden von Best Practices-Analyzer
description: Verwenden von Best Practices-Analyzer
translation-type: tm+mt
source-git-commit: dc2d529c6bbdb4e0fd963021e40bc333b321c95c
workflow-type: tm+mt
source-wordcount: '2362'
ht-degree: 69%

---


# Verwenden von Best Practices-Analyzer {#using-best-practices-analyzer}

>[!CONTEXTUALHELP]
>id="aemcloud_bpa_using"
>title="Verwenden des Best Practices-Analyzers"
>abstract="Lesen Sie die Dokumentation zur Verwendung von Best Practices Analyzer (früher Cloud Readiness Analyzer) und dem erstellten Bericht. Der Bericht &quot;Best Practices-Analyzer&quot;wird verwendet, um ein allgemeines Verständnis der allgemeinen Aktualisierungsbereitschaft zu gewinnen."
>"https://my.adobeconnect.com/pqgrfezoxghs?proto=true" text="[Webinar] Introducing Tools to Accelerate the Journey to Adobe Experience Manager as a Cloud Service"

## Wichtige Überlegungen zur Verwendung von Best Practices Analyzer {#imp-considerations}

Befolgen Sie den folgenden Abschnitt, um die wichtigen Überlegungen zum Ausführen des Best Practices-Analyzer (BPA) zu verstehen:

* Der BPA-Bericht wird mit der Ausgabe von Adobe Experience Manager (AEM) [Mustererkennung](https://docs.adobe.com/content/help/de-DE/experience-manager-65/deploying/upgrading/pattern-detector.html) erstellt. Die von BPA verwendete Version des Musterdetektors ist im BPA-Installationspaket enthalten.

* BPA kann nur vom Benutzer **admin** oder einem Benutzer in der Gruppe **administrators** ausgeführt werden.

* BPA wird auf AEM Instanzen mit Version 6.1 und höher unterstützt.

   >[!NOTE]
Bitte lesen Sie  [Installing on AEM 6.1 ](#installing-on-aem61) für spezielle Anforderungen für die Installation von BPA auf AEM 6.1.

* BPA kann auf jeder Umgebung ausgeführt werden, es wird jedoch empfohlen, dass es auf einer *Stage*-Umgebung ausgeführt wird.

   >[!NOTE]
Um Auswirkungen auf geschäftskritische Instanzen zu vermeiden, wird empfohlen, BPA in einer  ** Authoring-Umgebung auszuführen, die der  ** Produktionsumgebung in den Bereichen Anpassungen, Konfigurationen, Inhalt und Benutzeranwendungen so nahe wie möglich ist. Alternativ kann CRA in einem Klon der *Autoren*-Produktionsumgebung ausgeführt werden.

* Die Generierung von BPA-Berichtinhalten kann sehr lange dauern, von einigen Minuten bis zu einigen Stunden. Die benötigte Zeit hängt in hohem Maße von der Größe und Art des AEM-Repository-Inhalts, der AEM-Version und anderen Faktoren ab.

* Aufgrund der beträchtlichen Zeit, die zum Generieren des Berichtinhalts erforderlich sein könnte, wird dieser von einem Hintergrundprozess generiert und in einem Cache gespeichert. Der Bericht sollte relativ schnell angezeigt und heruntergeladen werden, da er den Inhalts-Cache nutzt, bis dieser abläuft oder der Bericht explizit aktualisiert wird. Während der Generierung von Berichtinhalten können Sie Ihre Browser-Registerkarte schließen und zu einem späteren Zeitpunkt zur Ansicht des Berichts zurückkehren, sobald der Inhalt im Cache verfügbar ist.

## Verfügbarkeit {#availability}

[!CONTEXTUALHELP]
id="aemcloud_bpa_download"
title="Herunterladen des Best Practices-Analyzers"
abstract="Der Best Practices-Analyzer kann als ZIP-Datei vom Software Distribution Portal heruntergeladen werden. Sie können das Paket über Package Manager in Ihrer Quelldistanz von Adobe Experience Manager (AEM) installieren."

Der Best Practices-Analyzer kann als ZIP-Datei vom Software Distribution Portal heruntergeladen werden. Sie können das Paket über Package Manager in Ihrer Quelldistanz von Adobe Experience Manager (AEM) installieren.

>[!NOTE]
Laden Sie den Best Practices Analyzer über das  [Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) Distributionportal herunter.

## Ansicht des Berichts &quot;Best Practices Analyzer&quot; {#viewing-report}

### Adobe Experience Manager 6.3.0 und höher {#aem-later-versions}

In diesem Abschnitt erfahren Sie, wie der Bericht Best Practices-Analyzer Ansicht wird:

1. Wählen Sie Adobe Experience Manager und navigieren Sie zu Tools -> **Vorgänge** -> **Best Practices Analyzer**.

   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/BPA_pic1.png)

1. Klicken Sie auf **Bericht erstellen**, um den Best Practices-Analyzer auszuführen.

   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/BPA_pic2.png)

1. Während die BPA den Bericht generiert, können Sie den Fortschritt des Tools auf dem Bildschirm sehen. Dabei wird die Anzahl der analysierten Elemente und gefundenen Ergebnisse angezeigt.

   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/BPA_pic3.png)


1. Sobald der BPA-Bericht erstellt wurde, wird eine Zusammenfassung und die Anzahl der Ergebnisse in tabellarischer Form angezeigt, die nach der Art der Feststellung und der Wichtigkeitsstufe geordnet sind. Um weitere Details zu einem bestimmten Ergebnis zu erhalten, können Sie auf die Zahl klicken, die dem Typ des Ergebnisses in der Tabelle entspricht.

   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/BPA_pic4.png)

   Mit der oben beschriebenen Aktion wird automatisch ein Bildlauf zur Position des Ergebnisses im Bericht durchgeführt.

   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/BPA_pic5.png)

1. Sie haben die Möglichkeit, den Bericht im CSV-Format herunterzuladen, indem Sie auf **CSV** klicken, wie in der folgenden Abbildung dargestellt.

   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/BPA_pic6.png)

   >[!NOTE]
Sie können die BPA zwingen, ihren Cache zu leeren und den Bericht neu zu generieren, indem Sie auf Bericht  **aktualisieren** klicken.

   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/BPA_pic7.png)

   >[!NOTE]
Während der Berichterstellung wird der Fortschritt in Prozent angezeigt, wie in der Abbildung unten dargestellt.

   ![image](/help/move-to-cloud-service/best-practices-analyzer/assets/BPA_pic8.png)


### Adobe Experience Manager 6.2 und 6.1 {#aem-specific-versions}

Das Analyzer-Tool für Best Practices ist in Adobe Experience Manager 6.2 auf einen Link beschränkt, über den der CSV-Bericht generiert und heruntergeladen wird.

In Adobe Experience Manager 6.1 funktioniert das Tool nicht und es kann nur die HTTP-Schnittstelle verwendet werden.

>[!NOTE]
In allen Versionen kann die enthaltene Mustererkennung unabhängig ausgeführt werden.

## Interpretieren des Berichts Best Practices Analyzer {#cra-report}

[!CONTEXTUALHELP]
id="aemcloud_bpa_interpreting"
title="Interpretieren des Berichts &quot;Best Practices Analyzer&quot;"
abstract="Es gibt zwei Optionen zum Anzeigen der BPA-Berichtausgabe: Benutzeroberfläche und CSV. Wenn das Analyzer-Tool für Best Practices in der AEM-Instanz ausgeführt wird, wird der UI-Bericht als Ergebnisse im Tool-Fenster angezeigt. Das CSV-Format des Berichts enthält Informationen, die aus der Mustererkennungsausgabe generiert wurden und nach Kategorie, Untertyp und Wichtigkeitsstufe sortiert und organisiert sind."
additional-url="https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html?lang=en" text="Kategorien zu Best Practices für Analyzer-Berichte"

Wenn das Analyzer-Tool für Best Practices in der AEM-Instanz ausgeführt wird, wird der Bericht als Ergebnis im Tool-Fenster angezeigt.

Das Format des Berichts lautet:

* **Berichtsübersicht**: Informationen zum Bericht selbst, einschließlich der Folgenden:
   * **Berichtszeit**: Zeitpunkt der Erstellung und erstmaligen Bereitstellung des Berichtinhalts.
   * **Ablaufzeit**: Wann der Cache für den Inhalt des Berichts abläuft.
   * **Erstellungszeitraum**: Die Zeit, die der Prozess des Generierens des Berichtinhalts benötigt hat.
   * **Ergebniszähler**: Die Gesamtzahl der im Bericht enthaltenen Ergebnisse.
* **Systemübersicht**: Informationen über das AEM System, auf dem die BPA ausgeführt wurde.
* **Suchen von Kategorien**: Mehrere Abschnitte, die jeweils eine oder mehrere Ergebnisse derselben Kategorie behandeln. Jeder Abschnitt enthält Folgendes: Name der Kategorie, Untertypen, Anzahl und Wichtigkeit der Ergebnisse, Zusammenfassung, Link zur Dokumentation der Kategorien und individuelle Suchinformationen.

Jedem Ergebnis wird eine Wichtigkeitsstufe zugewiesen, um eine ungefähre Priorität für das Handeln anzugeben.

>[!NOTE]
Weitere Informationen zu den einzelnen Kategorien finden Sie unter [Musterdetektorkategorien](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html).

Sie finden die Wichtigkeitsstufen in der folgenden Tabelle:

| Wichtigkeit | Beschreibung |
|--- |--- |
| INFO | Diese Ergebnisse werden zu Informationszwecken bereitgestellt. |
| ADVISORY | Diese Ergebnisse stellen möglicherweise ein Problem bei der Aktualisierung dar. Weitere Untersuchungen werden empfohlen. |
| MAJOR | Diese Ergebnisse stellen wahrscheinlich ein Problem bei der Aktualisierung dar, das behoben werden sollte. |
| CRITICAL | Diese Ergebnisse stellen wahrscheinlich ein Problem bei der Aktualisierung dar, das behoben werden muss, um Funktionsverlust oder Leistungseinbußen zu vermeiden. |


## Interpretieren des CSV-Berichts zu Best Practices für Analyzer {#cra-csv-report}

Wenn Sie in Ihrer AEM auf die Option **CSV** klicken, wird das CSV-Format des Berichts Best Practices Analyzer aus dem Inhaltscache erstellt und an Ihren Browser zurückgegeben. Abhängig von Ihren Browser-Einstellungen wird dieser Bericht automatisch als Datei mit dem Standardnamen `results.csv` heruntergeladen.

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

Die BPA stellt eine HTTP-Schnittstelle bereit, die als Alternative zur Benutzeroberfläche in AEM verwendet werden kann. Die Schnittstelle unterstützt sowohl HEAD- als auch GET-Befehle. Er kann zum Generieren des BPA-Berichts und zur Rückgabe in einem der drei folgenden Formate verwendet werden: JSON-, CSV- und tabulatorgetrennte Werte (TSV).

Die folgenden URLs stehen für HTTP-Zugriff zur Verfügung, wobei `<host>` Hostname und gegebenenfalls Anschluss des Servers ist, auf dem die BPA installiert ist:
* `http://<host>/apps/best-practices-analyzer/analysis/report.json` für das JSON-Format
* `http://<host>/apps/best-practices-analyzer/analysis/report.csv` für das CSV-Format
* `http://<host>/apps/best-practices-analyzer/analysis/report.tsv` für das TSV-Format

### Ausführen einer HTTP-Anfrage {#executing-http-request}

Die HTTP-Schnittstelle kann auf verschiedene Weise verwendet werden.

Eine einfache Möglichkeit besteht darin, eine Browser-Registerkarte im selben Browser zu öffnen, in dem Sie sich bereits als Administrator bei AEM angemeldet haben. Sie können die URL in der Browser-Registerkarte eingeben und die Ergebnisse vom Browser anzeigen oder herunterladen lassen.

Sie können auch ein Befehlszeilen-Tool wie `curl` oder `wget` oder eine beliebige HTTP-Client-Anwendung verwenden. Wenn Sie keine Browser-Registerkarte mit einer authentifizierten Sitzung verwenden, müssen Sie als Teil des Kommentars einen Administrator-Benutzernamen und ein Kennwort angeben.

Im Folgenden ein Beispiel:
`curl -u admin:admin 'http://localhost:4502/apps/best-practices-analyzer/analysis/report.csv' > report.csv`.

### Kopfzeilen und Parameter {#http-headers-and-parameters}

Diese Schnittstelle verwendet die folgenden HTTP-Kopfzeilen:

* `Cache-Control: max-age=<seconds>`: Gibt die Lebensdauer der Cache-Aktualisierung in Sekunden an. (Siehe [RFC 7234](https://tools.ietf.org/html/rfc7234#section-5.2.2.8).)
* `Prefer: respond-async`: Gibt an, dass der Server asynchron reagieren soll. (Siehe [RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.1).)
* `Prefer: return=minimal`: Gibt an, dass der Server eine minimale Antwort zurückgeben soll. (Siehe [RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.2).)

Die folgenden HTTP-Abfrageparameter stehen zur Verfügung, wenn HTTP-Kopfzeilen möglicherweise nicht einfach verwendet werden können:

* `max-age` (Zahl, optional): Gibt die Lebensdauer der Cache-Aktualisierung in Sekunden an. Diese Zahl muss 0 oder höher sein. Die Standardlebensdauer für die Aktualisierung beträgt 86400 Sekunden. Ohne diesen Parameter oder den entsprechenden Header wird ein Aktualisierungs-Cache verwendet, um Anfragen 24 Stunden lang zu verarbeiten, bevor der Bericht neu generiert werden muss. Durch die Verwendung von `max-age=0` wird das Löschen des Caches erzwungen und eine Neuerstellung des Berichts eingeleitet. Dazu wird die zuvor festgelegte Lebensdauer für die Aktualisierung mit einem Wert, der ungleich null ist, für den neu generierten Cache verwendet.
* `respond-async` (boolesch, optional): Gibt an, dass die Antwort asynchron bereitgestellt werden soll. Die Verwendung von `respond-async=true`, wenn der Cache veraltet ist, führt dazu, dass der Server die Antwort `202 Accepted` zurückgibt und den Cache verarbeitet, ohne darauf zu warten, dass der Cache aktualisiert und der Bericht generiert wird. Wenn der Cache aktualisiert ist, hat dieser Parameter keine Auswirkung. Der Standardwert lautet `false`. Ohne diesen Parameter oder den entsprechenden Header reagiert der Server synchron. Dies kann viel Zeit und eine Anpassung der maximalen Antwortzeit für den HTTP-Client erfordern.
* `may-refresh-cache` (boolesch, optional): Gibt an, dass der Server den Cache bei einer Anfrage aktualisieren kann, wenn der aktuelle Cache leer oder veraltet ist bzw. in Kürze veraltet sein wird. Wenn `may-refresh-cache=true` oder wenn dieser Wert nicht angegeben wird, dann kann der Server eine Hintergrundaufgabe initiieren, die den Musterdetektor aufruft und den Cache aktualisiert. Wenn `may-refresh-cache=false`, dann initiiert der Server keine Aktualisierungsaufgabe, die andernfalls ausgeführt worden wäre, wenn der Cache leer oder veraltet ist. In diesem Fall ist der Bericht leer. Auf eine Aktualisierungsaufgabe, die bereits in Bearbeitung ist, hat dieser Parameter keine Auswirkung.
* `return-minimal` (boolesch, optional): Gibt an, dass die Antwort des Servers nur den Status mit der Fortschrittsanzeige und dem Cache-Status im JSON-Format enthalten sollte. Wenn `return-minimal=true`, dann ist der Antworttext auf das Statusobjekt beschränkt. Wenn `return-minimal=false` oder der Wert nicht angegeben ist, wird eine vollständige Antwort bereitgestellt.
* `log-findings` (boolesch, optional): Gibt an, dass der Server den Inhalt des Caches beim ersten Erstellen oder Aktualisieren protokollieren soll. Jedes Ergebnis aus dem Cache wird als JSON-Zeichenfolge protokolliert. Diese Protokollierung erfolgt nur, wenn `log-findings=true` und die Anfrage einen neuen Cache generiert.

Wenn sowohl eine HTTP-Kopfzeile als auch ein entsprechender Abfrageparameter vorhanden sind, hat der Abfrageparameter Vorrang.

Mit dem folgenden Befehl können Sie die Generierung des Berichts einfach über die HTTP-Schnittstelle starten:
`curl -u admin:admin 'http://localhost:4502/apps/best-practices-analyzer/analysis/report.json?max-age=0&respond-async=true'`.

Nachdem eine Anfrage gestellt wurde, muss der Client nicht aktiv bleiben, damit der Bericht generiert wird. Die Berichtgenerierung kann mit einem Client über eine HTTP-GET-Anforderung initiiert und nach der Berichterstellung mit einem anderen Client oder mit dem BPA-Tool in der AEM Benutzeroberfläche aus dem Cache angezeigt werden.

### Antworten {#http-responses}

Die folgenden Antwortwerte sind möglich:

* `200 OK`: Gibt an, dass die Antwort Ergebnisse des Musterdetektors enthält, die während der Lebensdauer für die Aktualisierung des Caches generiert wurden.
* `202 Accepted`: Wird verwendet, um anzugeben, dass der Cache veraltet ist. Wenn `respond-async=true` und `may-refresh-cache=true`, dann weist diese Antwort darauf hin, dass eine Aktualisierungsaufgabe ausgeführt wird. Wenn `may-refresh-cache=false`, gibt diese Antwort einfach an, dass der Cache veraltet ist.
* `400 Bad Request`: Gibt an, dass bei der Anfrage ein Fehler aufgetreten ist. Eine Meldung im Format für Problemdetails (siehe [RFC 7807](https://tools.ietf.org/html/rfc7807)) enthält weitere Details.
* `401 Unauthorized`: Gibt an, dass die Anfrage nicht genehmigt wurde.
* `500 Internal Server Error`: Gibt an, dass ein interner Server-Fehler aufgetreten ist. Eine Meldung im Format für Problemdetails enthält weitere Details.
* `503 Service Unavailable`: Zeigt an, dass der Server mit einer anderen Antwort beschäftigt ist und diese Anfrage nicht rechtzeitig bearbeiten kann. Dies tritt aller Wahrscheinlichkeit nach nur dann auf, wenn synchrone Anfragen gestellt werden. Eine Meldung im Format für Problemdetails enthält weitere Details.

## Administratorinformationen

### Anpassung der Cache-Lebensdauer {#cache-adjustment}

Die Standardlebensdauer des BPA-Cache beträgt 24 Stunden. Mit der Option zum Aktualisieren eines Berichts und zum erneuten Generieren des Zwischenspeichers in der AEM- und der HTTP-Schnittstelle ist dieser Standardwert für die meisten Verwendungen der BPA geeignet. Wenn die Zeit für die Berichterstellung für Ihre AEM-Instanz besonders lang ist, möchten Sie möglicherweise die Cache-Lebensdauer anpassen, um das erneute Generieren des Berichts zu minimieren.

Der Wert für die Cache-Lebensdauer wird als `maxCacheAge`-Eigenschaft im folgenden Repository-Knoten gespeichert:
`/apps/best-practices-analyzer/content/BestPracticesReport/jcr:content`

Der Wert dieser Eigenschaft ist die Cache-Lebensdauer in Sekunden. Ein Administrator kann die Cache-Lebensdauer mit CRX/DE Lite anpassen.

### Installieren in AEM 6.1 {#installing-on-aem61}

BPA verwendet ein Systemdienst-Benutzerkonto mit dem Namen `repository-reader-service`, um den Musterdetektor auszuführen. Dieses Konto ist auf AEM 6.2 und höher verfügbar. In AEM 6.1 muss dieses Konto vor der Installation von BPA wie folgt erstellt werden:**

1. Befolgen Sie die Anweisungen unter [Erstellen eines neuen Service-Benutzers](https://docs.adobe.com/content/help/de-DE/experience-manager-65/administering/security/security-service-users.html#creating-a-new-service-user), um einen Benutzer zu erstellen. Legen Sie die UserID als `repository-reader-service` fest, lassen Sie den Zwischenpfad leer und klicken Sie dann auf das grüne Häkchen.

2. Befolgen Sie die Anweisungen unter [Verwalten von Benutzern und Gruppen](https://docs.adobe.com/content/help/de-DE/experience-manager-65/administering/security/security.html#managing-users-and-groups), insbesondere die Anweisungen zum Hinzufügen von Benutzern zu einer Gruppe, um den `repository-reader-service`-Benutzer zur `administrators`-Gruppe hinzuzufügen.

3. Installieren Sie das BPA-Paket über Package Manager auf Ihrer AEM. (Dadurch wird die erforderliche Konfigurationsänderung zur ServiceUserMapper-Konfiguration für den `repository-reader-service`-System-Service-Benutzer hinzugefügt.)
