---
title: Verwenden von Best Practices Analyzer
description: Erfahren Sie, wie Sie mit Best Practices Analyzer die Bereitschaft zu einem Upgrade erkennen können.
exl-id: e8498e17-f55a-4600-87d7-60584d947897
feature: Migration
role: Admin
source-git-commit: e1089810b3bf3db0cc440bb397e5549ade6eac37
workflow-type: tm+mt
source-wordcount: '2796'
ht-degree: 97%

---

# Verwenden von Best Practices Analyzer {#using-best-practices-analyzer}

>[!CONTEXTUALHELP]
>id="aemcloud_bpa_using"
>title="Verwenden von Best Practices Analyzer"
>abstract="Lesen Sie die Dokumentation zur Verwendung von Best Practices Analyzer (zuvor Cloud Readiness Analyzer) und des erstellten Berichts. Der Best Practices Analyzer-Bericht wird verwendet, um ein allgemeines Verständnis der Upgrade-Bereitschaft zu gewinnen."
>additional-url="https://my.adobeconnect.com/pqgrfezoxghs?proto=true" text="[Webinar] Einführung zu Tools zur beschleunigten Integration von Adobe Experience Manager as a Cloud Service"

## Wichtige Überlegungen zur Verwendung von Best Practices Analyzer {#imp-considerations}

Im folgenden Abschnitt finden Sie wichtige Überlegungen zur Verwendung von Best Practices Analyzer (BPA):

* Der BPA-Bericht wird mit der Ausgabe der Adobe Experience Manager (AEM)-[Mustererkennung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/pattern-detector.html?lang=de) erstellt. Die von BPA verwendete Version der Mustererkennung ist im BPA-Installationspaket enthalten.

* BPA kann nur vom **Administrator** oder einem Anwender **Administratorgruppe** ausgeführt werden.

* BPA wird in AEM-Instanzen mit Version 6.1 und höher unterstützt.

  >[!NOTE]
  >Besondere Anforderungen für die Installation von BPA unter AEM 6.1 finden Sie unter [Installieren in AEM 6.1](#installing-on-aem61).

* BPA kann in jeder Umgebung ausgeführt werden, es wird jedoch empfohlen, das Tool in einer *Staging*-Umgebung auszuführen.

  >[!NOTE]
  >Um Auswirkungen auf geschäftskritische Instanzen zu vermeiden, wird empfohlen, BPA auf einer *Staging*-Umgebung auszuführen, die der *Produktions*-Umgebung im Hinblick auf Anpassungen, Konfigurationen, Inhalte und Anwenderprogrammen möglichst nahekommt. Alternativ kann BPA in einem Klon der *Autoren*-Produktionsumgebung ausgeführt werden.

* Die Erstellung von BPA-Berichten kann sehr viel Zeit in Anspruch nehmen, von einigen Minuten bis zu einigen Stunden. Die benötigte Zeit hängt in hohem Maße von der Größe und Art des AEM-Repository-Inhalts, der AEM-Version und anderen Faktoren ab.

* Aufgrund der beträchtlichen Zeit, die zum Generieren des Berichtinhalts erforderlich sein könnte, wird dieser von einem Hintergrundprozess generiert und in einem Cache gespeichert. Der Bericht sollte relativ schnell angezeigt und heruntergeladen werden, da er den Inhalts-Cache nutzt, bis dieser abläuft oder der Bericht explizit aktualisiert wird. Während der Generierung von Berichtinhalten können Sie Ihre Browser-Registerkarte schließen und zu einem späteren Zeitpunkt zur Ansicht des Berichts zurückkehren, sobald der Inhalt im Cache verfügbar ist.

## Verfügbarkeit {#availability}

>[!CONTEXTUALHELP]
>id="aemcloud_bpa_download"
>title="Herunterladen des Best Practices Analyzer"
>abstract="Best Practices Analyzer kann als ZIP-Datei vom Software Distribution-Portal heruntergeladen werden. Sie können das Paket über Package Manager in Ihrer Quellinstanz von Adobe Experience Manager (AEM) installieren."

Best Practices Analyzer kann als ZIP-Datei vom Software Distribution-Portal heruntergeladen werden. Sie können das Paket über [Package Manager](/help/implementing/developing/tools/package-manager.md) in Ihrer Quellinstanz von Adobe Experience Manager (AEM) installieren.

>[!NOTE]
>Laden Sie Best Practices Analyzer aus dem [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/de/aemcloud.html)-Portal herunter.

## Konnektivität der Quellumgebung {#source-environment-connectivity}

Die Quell-AEM-Instanz wird möglicherweise hinter einer Firewall ausgeführt, wo sie nur bestimmte Hosts erreichen kann, die zu einer Zulassungsliste hinzugefügt wurden. Damit der BPA-generierte Bericht erfolgreich automatisch in Cloud Acceleration Manager hochgeladen werden kann, müssen die folgenden Endpunkte auf der Instanz verfügbar sein, auf der AEM ausgeführt wird:

* Der Azure Blob Storage-Service: `casstorageprod.blob.core.windows.net`


## Anzeigen des Best Practices Analyzer-Berichts {#viewing-report}

### Adobe Experience Manager 6.3.0 und höher {#aem-later-versions}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_bpa_upload_setup"
>title="Automatisches Hochladen des Best-Practices-Analyzer-Berichts in CAM"
>abstract="Stellen Sie den BPA-Upload-Schlüssel bereit, um den erstellten BPA-Bericht automatisch in Cloud Acceleration Manager (CAM) hochzuladen."

Folgen Sie diesem Abschnitt, um zu erfahren, wie Sie den Best Practices Analyzer-Bericht anzeigen können:

1. Wählen Sie Adobe Experience Manager aus und navigieren Sie zu „Tools“ > **Vorgänge** > **Best Practices Analyzer**.

   ![Best Practices Analyzer](/help/journey-migration/best-practices-analyzer/assets/BPA_pic1.png)

1. Klicken Sie auf **Bericht generieren**, um den Best Practices Analyzer auszuführen.

   ![Bericht erzeugen](/help/journey-migration/best-practices-analyzer/assets/BPA_pic2.png)

>[!NOTE]
> Ab der BPA-Version 2.1.54 wurde eine neue Funktion eingeführt, um den Lighthouse-Score zu erhalten.
1. Nachdem Sie auf **Bericht generieren** geklickt haben, wird ein Popup angezeigt, in dem Sie die URL der öffentlichen AEM-Site für den Lighthouse-Score anfordern. Der Benutzer muss eine gültige URL in das angegebene Feld eingeben.

   ![Bild](/help/journey-migration/best-practices-analyzer/assets/bpa_popup_url.png)

   1. Wenn die URL gültig ist, wird eine Erfolgsmeldung angezeigt.

      ![Bild](/help/journey-migration/best-practices-analyzer/assets/valid_url.png)

   1. Wenn die URL ungültig ist, wird eine Fehlermeldung angezeigt.

      ![Bild](/help/journey-migration/best-practices-analyzer/assets/invalid_url.png)

1. Geben Sie den BPA-Upload-Schlüssel an, um den generierten BPA-Bericht automatisch in [Cloud Acceleration Manager (CAM)](/help/journey-migration/cloud-acceleration-manager/introduction/benefits-cam.md) hochzuladen. Um den Upload-Schlüssel zu erhalten, navigieren Sie zur [Best-Practices-Analyse in CAM](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#best-practices-analysis).

   ![Festlegen des BPA-Upload-Schlüssels](/help/journey-migration/best-practices-analyzer/assets/BPA_upload_key.png)

>[!NOTE]
>Sie haben die Möglichkeit, das automatische Hochladen in CAM zu überspringen, indem Sie die Option für das Überspringen des automatischen Uploads in CAM **** wählen. Wenn Sie sich für das Überspringen entscheiden, müssen Sie den BPA-Bericht manuell als kommagetrennte Wertedatei herunterladen und die Datei dann in CAM hochladen. Es wird empfohlen, die Option für den Upload-Schlüssel zu verwenden, da sie den Vorgang optimiert.

>[!IMPORTANT]
>Beim manuellen Hochladen in CAM sind die Berichtsgrößen auf etwa 200 MB beschränkt. Für größere Berichte müssen Sie den automatischen Upload nutzen.

1. Die Schaltfläche **Generieren** wird aktiv, wenn ein gültiger Schlüssel angegeben wird. Klicken Sie auf **Erstellen**, um die Erstellung des Berichts einzuleiten.

   ![Bericht erzeugen](/help/journey-migration/best-practices-analyzer/assets/BPA_upload_key1.png)

1. Während der BPA den Bericht generiert, können Sie den Fortschritt des Tools auf dem Bildschirm verfolgen. Der Fortschritt wird in Prozent angezeigt. Dabei wird auch die Anzahl der analysierten Elemente und gefundenen Ergebnisse angezeigt.

   ![Erzeugen des Berichts](/help/journey-migration/best-practices-analyzer/assets/BPA_generate_upload.png)

>[!NOTE]
>Der Zeitstempel für den Ablauf des BPA-Upload-Schlüssels wird in der oberen rechten Ecke angezeigt. Sie sollten den BPA-Upload-Schlüssel erneuern, wenn er bald abläuft. Um den Schlüssel zu erneuern, können Sie auf **Erneuern** klicken, um zu CAM zu navigieren und den Schlüssel zu erneuern.

1. Sobald der BPA-Bericht erstellt wurde, werden eine Zusammenfassung sowie die Anzahl der Ergebnisse in tabellarischer Form angezeigt, die nach Ergebnistyp und Wichtigkeitsstufe geordnet sind. Um weitere Details zu einem bestimmten Ergebnis zu erhalten, können Sie die Zahl anklicken, die dem Typ des Ergebnisses in der Tabelle entspricht.

   ![Berichtsübersicht](/help/journey-migration/best-practices-analyzer/assets/BPA_report_upload.png)

1. Sie haben die Möglichkeit, den Bericht in einem kommagetrennten Format (CSV) herunterzuladen, indem Sie auf **In CSV exportieren** klicken. Sie können den Bericht auch in CAM anzeigen, indem Sie auf die Option zum Wechsel zu CAM **** klicken. Dadurch gelangen Sie auf die Seite [Best-Practices-Analyse](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#best-practices-analysis) in CAM.

Sie können den BPA zwingen, seinen Cache zu leeren und den Bericht neu zu generieren, indem Sie auf **Bericht aktualisieren** klicken.

![Bericht aktualisieren](/help/journey-migration/best-practices-analyzer/assets/BPA_report_upload.png)

1. Wenn der Cache abläuft, haben Sie die Möglichkeit, den zuletzt erstellten Bericht in CAM anzusehen, indem Sie auf die Option zum **Anzeigen des zuletzt in CAM erstellten Berichts** klicken, oder eine neue Berichtserstellung einzuleiten, indem Sie auf die Option zum **Erstellen eines neuen Berichts** klicken.

![Kein Bericht](/help/journey-migration/best-practices-analyzer/assets/BPA_regeneratereport.png)


#### Verwenden von Filtern im Bericht „Best Practices Analyzer“ {#bpa-filters}

Gehen Sie wie folgt vor, um Ergebnisse zu [ACS Commons](https://adobe-consulting-services.github.io/acs-aem-commons/) herauszufiltern:

1. Klicken Sie links auf der Seite auf das Symbol in der linken Leiste. Dadurch wird der **ACS Commons-Filter** angezeigt. Klicken Sie auf den **ACS Commons-Filter**, um das interaktive Kontrollkästchen anzuzeigen, wie in der nachfolgenden Abbildung dargestellt.

   ![ACS Commons-Filter](/help/journey-migration/best-practices-analyzer/assets/report_filter_1.png)

   >[!NOTE]
   >Das Symbol in der linken Leiste wird nur angezeigt, wenn BPA die Verwendung von ACS Commons erkennt.

1. Deaktivieren Sie das Kontrollkästchen, um alle Ergebnisse zu ACS Commons herauszufiltern. Im Bericht sollte ein **Zähler für die gefilterten Ergebnisse** angezeigt werden, wie in der nachfolgenden Abbildung dargestellt. Der Filter wird auch auf den Bericht angewendet, wenn er im CSV-Format (CSV) exportiert wird.

   ![Zähler für die gefilterten Ergebnisse](/help/journey-migration/best-practices-analyzer/assets/report_filter_2.png)

   >[!NOTE]
   >Die Ergebnisse von ACS Commons sollten nicht ignoriert werden. Informationen zur Kompatibilität mit AEM as a Cloud Service finden Sie in der [Dokumentation](https://adobe-consulting-services.github.io/acs-aem-commons/pages/compatibility.html#aem-as-a-cloud-service-feature-incompatibility).

<!--
### Adobe Experience Manager 6.2 and 6.1 {#aem-specific-versions}
 
The Best Practices Analyzer tool is limited in Adobe Experience Manager 6.2 to a link that generates and downloads the CSV report.

For Adobe Experience Manager 6.1, the tool is not functional and only the HTTP interface may be used.

>[!NOTE]
>In all versions, the included Pattern Detector may run independently.
-->

## Interpretieren des Best Practices Analyzer-Berichts {#cra-report}

>[!CONTEXTUALHELP]
>id="aemcloud_bpa_interpreting"
>title="Interpretieren des Best Practices Analyzer-Berichts"
>abstract="Es gibt zwei Optionen zum Anzeigen der BPA-Berichtausgabe: Benutzeroberfläche und CSV. Wenn das Best Practices Analyzer-Tool in der AEM-Instanz ausgeführt wird, wird der Benutzeroberflächen-Bericht als Ergebnis im Tool-Fenster angezeigt. Das CSV-Format des Berichts enthält Informationen, die aus der Mustererkennungsausgabe generiert wurden und nach Kategorie, Untertyp und Wichtigkeitsstufe sortiert und organisiert sind."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=de#analysis-report" text="Überprüfen des Berichts der Best-Practices-Analyse"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html?lang=de" text="Grundlegendes zu Best Practices Analyzer-Berichtkategorien"

Wenn das Best Practices Analyzer-Tool in der AEM-Instanz ausgeführt wird, wird der Bericht als Ergebnis im Tool-Fenster angezeigt.

Das Format des Berichts lautet:

* **Berichtsübersicht**: Informationen zum Bericht selbst, einschließlich der Folgenden:
   * **Berichtszeit**: Zeitpunkt der Erstellung und erstmaligen Bereitstellung des Berichtinhalts.
   * **Ablaufzeit**: Wann der Cache für den Inhalt des Berichts abläuft.
   * **Erstellungszeitraum**: Die Zeit, die der Prozess des Generierens des Berichtinhalts benötigt hat.
   * **Ergebniszähler**: Die Gesamtzahl der im Bericht enthaltenen Ergebnisse.
* **Systemübersicht**: Informationen zum AEM-System, für das BPA ausgeführt wurde.
* **Suchen von Kategorien**: Mehrere Abschnitte, die jeweils eine oder mehrere Ergebnisse derselben Kategorie behandeln. Jeder Abschnitt enthält Folgendes: Name der Kategorie, Untertypen, Anzahl und Wichtigkeit der Ergebnisse, Zusammenfassung, Link zur Dokumentation der Kategorien und individuelle Suchinformationen.

Jedem Ergebnis wird eine Wichtigkeitsstufe zugewiesen, um eine ungefähre Priorität für das Handeln anzugeben.

>[!NOTE]
>Weitere Informationen zu den einzelnen Kategorien finden Sie unter [Musterdetektorkategorien](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html?lang=de).

Sie finden die Wichtigkeitsstufen in der folgenden Tabelle:

| Wichtigkeit | Beschreibung |
|--- |--- |
| INFO | Diese Ergebnisse werden zu Informationszwecken bereitgestellt. |
| ADVISORY | Diese Ergebnisse stellen möglicherweise ein Problem bei der Aktualisierung dar. Weitere Untersuchungen werden empfohlen. |
| MAJOR | Diese Ergebnisse stellen wahrscheinlich ein Problem bei der Aktualisierung dar, das behoben werden sollte. |
| CRITICAL | Diese Ergebnisse stellen wahrscheinlich ein Problem bei der Aktualisierung dar, das behoben werden muss, um Funktionsverlust oder Leistungseinbußen zu vermeiden. |

## Interpretieren des Best Practices Analyzer-CSV-Berichts {#cra-csv-report}

Wenn Sie in Ihrer AEM-Instanz auf die Option **CSV** klicken, wird das CSV-Format des Best Practices Analyzer-Berichts aus dem Inhalts-Cache erstellt und an Ihren Browser zurückgegeben. Abhängig von Ihren Browser-Einstellungen wird dieser Bericht automatisch als Datei mit dem Standardnamen `results.csv` heruntergeladen.

Wenn der Cache abgelaufen ist, wird der Bericht erneut generiert, bevor die CSV-Datei erstellt und heruntergeladen wird.

Das CSV-Format des Berichts enthält Informationen, die aus der Mustererkennungsausgabe generiert wurden und nach Kategorie, Untertyp und Wichtigkeitsstufe sortiert und organisiert sind. Sein Format eignet sich zum Anzeigen und Bearbeiten in einem Programm wie Microsoft Excel. Alle Ergebnisinformationen werden in einem wiederholbaren Format bereitgestellt, das beim Vergleich von Berichten im Zeitverlauf zur Messung des Fortschritts hilfreich sein kann.

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

BPA bietet eine HTTP-Schnittstelle, die als Alternative zur AEM-Benutzeroberfläche verwendet werden kann. Die Schnittstelle unterstützt sowohl HEAD- als auch GET-Befehle. Sie kann zum Generieren des BPA-Berichts und zur Rückgabe in einem der drei folgenden Formate verwendet werden: JSON-, CSV- und tabulatorgetrennte Werte (TSV).

Die folgenden URLs stehen für den HTTP-Zugriff zur Verfügung, wobei `<host>` der Host-Name und gegebenenfalls der Port des Servers ist, auf dem BPA installiert ist:
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
* `respond-async` (boolesch, optional): Gibt an, dass die Antwort asynchron bereitgestellt werden soll. Die Verwendung von `respond-async=true`, wenn der Cache veraltet ist, führt dazu, dass der Server die Antwort `202 Accepted` zurückgibt und den Cache verarbeitet, ohne darauf zu warten, dass der Cache aktualisiert und der Bericht generiert wird. Wenn der Cache aktualisiert ist, hat dieser Parameter keine Auswirkung. Der Standardwert ist `false`. Ohne diesen Parameter oder den entsprechenden Header reagiert der Server synchron. Dies kann viel Zeit und eine Anpassung der maximalen Antwortzeit für den HTTP-Client erfordern.
* `may-refresh-cache` (boolesch, optional): Gibt an, dass der Server den Cache bei einer Anfrage aktualisieren kann, wenn der aktuelle Cache leer oder veraltet ist bzw. in Kürze veraltet sein wird. Wenn `may-refresh-cache=true` oder wenn dieser Wert nicht angegeben wird, dann kann der Server eine Hintergrundaufgabe initiieren, die den Musterdetektor aufruft und den Cache aktualisiert. Wenn `may-refresh-cache=false`, dann initiiert der Server keine Aktualisierungsaufgabe, die andernfalls ausgeführt worden wäre, wenn der Cache leer oder veraltet ist. In diesem Fall ist der Bericht leer. Auf eine Aktualisierungsaufgabe, die bereits in Bearbeitung ist, hat dieser Parameter keine Auswirkung.
* `return-minimal` (boolesch, optional): Gibt an, dass die Antwort des Servers nur den Status mit der Fortschrittsanzeige und dem Cache-Status im JSON-Format enthalten sollte. Wenn `return-minimal=true`, dann ist der Antworttext auf das Statusobjekt beschränkt. Wenn `return-minimal=false` oder der Wert nicht angegeben wird, wird eine vollständige Antwort bereitgestellt.
* `log-findings` (boolesch, optional): Gibt an, dass der Server den Inhalt des Caches beim ersten Erstellen oder Aktualisieren protokollieren soll. Jedes Ergebnis aus dem Cache wird als JSON-Zeichenfolge protokolliert. Diese Protokollierung erfolgt nur, wenn `log-findings=true` und die Anfrage einen neuen Cache generiert.

Wenn sowohl eine HTTP-Kopfzeile als auch ein entsprechender Abfrageparameter vorhanden sind, hat der Abfrageparameter Vorrang.

Mit dem folgenden Befehl können Sie die Generierung des Berichts einfach über die HTTP-Schnittstelle starten:
`curl -u admin:admin 'http://localhost:4502/apps/best-practices-analyzer/analysis/report.json?max-age=0&respond-async=true'`.

Nachdem eine Anfrage gestellt wurde, muss der Client nicht aktiv bleiben, damit der Bericht generiert wird. Die Berichterstellung kann mit einem Client mithilfe einer HTTP-GET-Anfrage initiiert und nach der Erstellung des Berichts aus dem Cache mit einem anderen Client oder dem BPA-Tool in der AEM-Benutzeroberfläche angezeigt werden.

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

Die standardmäßige BPA-Cache-Lebensdauer beträgt 24 Stunden. Mit der Option zum Aktualisieren eines Berichts und zum erneuten Generieren des Caches sowohl in der AEM-Instanz als auch in der HTTP-Schnittstelle ist dieser Standardwert wahrscheinlich für die meisten Verwendungen von BPA geeignet. Wenn die Zeit für die Berichterstellung für Ihre AEM-Instanz besonders lang ist, möchten Sie möglicherweise die Cache-Lebensdauer anpassen, um das erneute Generieren des Berichts zu minimieren.

Der Wert für die Cache-Lebensdauer wird als `maxCacheAge`-Eigenschaft im folgenden Repository-Knoten gespeichert:
`/apps/best-practices-analyzer/content/BestPracticesReport/jcr:content`

Der Wert dieser Eigenschaft ist die Cache-Lebensdauer in Sekunden. Ein Administrator kann die Cache-Lebensdauer mit CRX/DE Lite anpassen.

### Installieren in AEM 6.1 {#installing-on-aem61}

BPA verwendet ein System-Service-Anwenderkonto mit dem Namen `repository-reader-service` zum Ausführen der Mustererkennung. Dieses Konto ist auf AEM 6.2 und höher verfügbar. In AEM 6.1 muss dieses Konto *vor* der Installation von BPA wie folgt erstellt werden:

1. Befolgen Sie die Anweisungen unter [Erstellen eines neuen Service-Benutzers](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-service-users.html?lang=de#creating-a-new-service-user), um einen Benutzer zu erstellen. Legen Sie die UserID als `repository-reader-service` fest, lassen Sie den Zwischenpfad leer und klicken Sie dann auf das grüne Häkchen.

2. Befolgen Sie die Anweisungen unter [Verwalten von Benutzern und Gruppen](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html?lang=de#managing-users-and-groups), insbesondere die Anweisungen zum Hinzufügen von Benutzern zu einer Gruppe, um den `repository-reader-service`-Benutzer zur `administrators`-Gruppe hinzuzufügen.

3. Installieren Sie das BPA-Paket über den Package Manager auf Ihrer AEM-Quellinstanz. (Dadurch wird die erforderliche Konfigurationsänderung zur ServiceUserMapper-Konfiguration für den `repository-reader-service`-System-Service-Anwender hinzugefügt.)
