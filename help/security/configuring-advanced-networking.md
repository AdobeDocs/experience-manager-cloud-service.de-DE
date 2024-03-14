---
title: Erweiterte Netzwerkfunktionen für AEM as a Cloud Service konfigurieren
description: Erfahren Sie, wie Sie erweiterte Netzwerkfunktionen wie VPN oder eine flexible oder dedizierte Ausgangs-IP-Adresse für AEM as a Cloud Service konfigurieren.
exl-id: 968cb7be-4ed5-47e5-8586-440710e4aaa9
source-git-commit: a284c0139b45e618749866385cdcc81d1ceb61e7
workflow-type: tm+mt
source-wordcount: '5145'
ht-degree: 45%

---


# Erweiterte Netzwerkfunktionen für AEM as a Cloud Service konfigurieren {#configuring-advanced-networking}

In diesem Artikel werden die verschiedenen erweiterten Netzwerkfunktionen in AEM as a Cloud Service vorgestellt, einschließlich der Self-Service- und API-Bereitstellung von VPN, nicht standardmäßigen Ports und dedizierten Ausgangs-IP-Adressen.

>[!TIP]
>
>Zusätzlich zu dieser Dokumentation gibt es auch eine Reihe von Tutorials, die Sie durch die erweiterten Netzwerkoptionen auf dieser Seite führen sollen [Standort.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html?lang=de)

## Übersicht {#overview}

AEM as a Cloud Service bietet die folgenden erweiterten Netzwerkoptionen:

* [Flexibles Port-Egress](#flexible-port-egress) - Konfigurieren Sie AEM as a Cloud Service, um ausgehenden Traffic von nicht standardmäßigen Ports zu ermöglichen.
* [Dedizierte Ausgangs-IP-Adresse](#dedicated-egress-ip-address) - Konfigurieren Sie den Traffic von AEM as a Cloud Service aus, um von einer eindeutigen IP zu stammen.
* [Virtuelles privates Netzwerk (VPN)](#vpn) - Sichern Sie den Datenverkehr zwischen Ihrer Infrastruktur und AEM as a Cloud Service, wenn Sie über ein VPN verfügen.

In diesem Artikel werden diese Optionen zunächst im Detail beschrieben und Sie erfahren, warum Sie sie verwenden können, bevor Sie beschreiben, wie sie über die Cloud Manager-Benutzeroberfläche und die API konfiguriert werden, und abschließend einige erweiterte Anwendungsfälle beschrieben.

>[!CAUTION]
>
>Wenn Sie bereits über eine ältere dedizierte Egress-Technologie verfügen und eine dieser erweiterten Netzwerkoptionen konfigurieren möchten, [Wenden Sie sich zunächst an die Adobe Client Care.](https://experienceleague.adobe.com/?support-solution=Experience+Manager&amp;lang=de#home)
>
>Der Versuch, erweiterte Netzwerke mit veralteter Egress-Technologie zu konfigurieren, kann sich auf die Site-Konnektivität auswirken.

### Anforderungen und Einschränkungen {#requirements}

Bei der Konfiguration erweiterter Netzwerkfunktionen gelten die folgenden Einschränkungen.

* Ein Programm kann eine einzelne erweiterte Netzwerkoption (flexible Port-Ausfahrt, dedizierte Ausgangs-IP-Adresse oder VPN) bereitstellen.
* Erweiterte Netzwerke sind nicht verfügbar für [Sandbox-Programme.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)
* Ein Benutzer in muss über die **Administrator** Rolle, um die Netzwerkinfrastruktur in Ihrem Programm hinzuzufügen und zu konfigurieren.
* Die Produktionsumgebung muss erstellt werden, bevor in Ihrem Programm eine Netzwerkinfrastruktur hinzugefügt werden kann.
* Ihre Netzwerkinfrastruktur muss sich in derselben Region befinden wie die primäre Region Ihrer Produktionsumgebung.
   * Wenn Ihre Produktionsumgebung [zusätzliche Veröffentlichungsregionen,](/help/implementing/cloud-manager/manage-environments.md#multiple-regions) Sie können zusätzliche Netzwerkinfrastruktur erstellen, die jede zusätzliche Region widerspiegelt.
   * Es ist nicht zulässig, mehr Netzwerkinfrastrukturen als die in Ihrer Produktionsumgebung konfigurierte maximale Anzahl von Regionen zu erstellen.
   * Sie können in Ihrer Produktionsumgebung so viele Netzwerkinfrastrukturen wie möglich definieren, aber die neue Infrastruktur muss vom gleichen Typ sein wie die zuvor erstellte Infrastruktur.
   * Bei der Erstellung mehrerer Infrastrukturen dürfen Sie nur die Regionen auswählen, in denen keine erweiterte Netzwerkinfrastruktur erstellt wurde.

### Konfigurieren und Aktivieren erweiterter Netzwerke {#configuring-enabling}

Die Verwendung erweiterter Netzwerkfunktionen erfordert zwei Schritte:

1. Konfiguration der erweiterten Netzwerkoption, ob [flexibles Auslaufen von Ports,](#flexible-port-egress) [dedizierte Ausgangs-IP-Adresse,](#dedicated-egress-ip-address) oder [VPN,](#vpn) muss zunächst auf der Programmebene erfolgen.
1. Damit sie verwendet werden kann, muss die erweiterte Netzwerkoption auf Umgebungsebene aktiviert sein.

Beide Schritte können entweder über die Cloud Manager-Benutzeroberfläche oder die Cloud Manager-API durchgeführt werden.

* Bei Verwendung der Cloud Manager-Benutzeroberfläche müssen erweiterte Netzwerkkonfigurationen mithilfe eines Assistenten auf Programmebene erstellt und dann die einzelnen Umgebungen bearbeitet werden, in denen die Konfiguration aktiviert werden soll.

* Bei Verwendung der Cloud Manager-API muss die `/networkInfrastructures` Der API-Endpunkt wird auf Programmebene aufgerufen, um den gewünschten Typ von erweitertem Netzwerk zu deklarieren, gefolgt von einem Aufruf an die `/advancedNetworking` Endpunkt für jede Umgebung, um die Infrastruktur zu aktivieren und umgebungsspezifische Parameter zu konfigurieren.

## Flexibler Port-Ausgang {#flexible-port-egress}

Diese erweiterte Netzwerkfunktion ermöglicht es Ihnen, AEM as a Cloud Service so zu konfigurieren, dass der Ausgangs-Traffic über andere Ports als HTTP (Port 80) und HTTPS (Port 443), die standardmäßig geöffnet sind, läuft.

>[!TIP]
>
>Bei der Entscheidung zwischen flexiblem Port-Ausgang und dedizierter Ausgangs-IP-Adresse wird empfohlen, einen flexiblen Port-Ausgang zu wählen, wenn keine bestimmte IP-Adresse erforderlich ist, da Adobe die Traffic-Leistung des flexiblen Port-Ausgangs optimieren kann.

>[!NOTE]
>
>Nach der Erstellung können die Infrastrukturtypen der flexiblen Ports nicht mehr bearbeitet werden. Die einzige Möglichkeit, Konfigurationswerte zu ändern, besteht darin, sie zu löschen und neu zu erstellen.

### UI-Konfiguration {#configuring-flexible-port-egress-provision-ui}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie im Bildschirm **[Eigene Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** das Programm aus.

1. Aus dem **Programmübersicht** Seite, navigieren Sie zur **Umgebungen** Registerkarte und wählen Sie **Netzwerkinfrastruktur** im linken Bereich.

   ![Hinzufügen von Netzwerkinfrastruktur](assets/advanced-networking-ui-network-infrastructure.png)

1. Im **Netzwerkinfrastruktur hinzufügen** Assistent, der gestartet wird, wählen Sie **Flexibles Port-Egress** und die Region, in der sie erstellt werden soll, aus der **Region** Dropdown-Menü und tippen oder klicken Sie auf **Weiter**.

   ![Konfigurieren des flexiblen Port-Ausgangs](assets/advanced-networking-ui-flexible-port-egress.png)

1. Die **Bestätigung** -Tab fasst Ihre Auswahl und die nächsten Schritte zusammen. Tippen oder klicken **Speichern** , um die Infrastruktur zu erstellen.

   ![Konfiguration der flexiblen Port-Ausfahrt bestätigen](assets/advanced-networking-ui-flexible-port-egress-confirmation.png)

Unter dem **Netzwerkinfrastruktur** -Überschrift im seitlichen Bedienfeld mit Details zum Typ der Infrastruktur, des Status, der Region und der Umgebungen, in denen sie aktiviert wurde.

![Neuer Eintrag unter &quot;Netzinfrastruktur&quot;](assets/advanced-networking-ui-flexible-port-egress-new-entry.png)

>[!NOTE]
>
>Die Erstellung der Infrastruktur für flexible Port-Ausgänge kann bis zu einer Stunde dauern, nach der sie auf Umgebungsebene konfiguriert werden kann.

### API-Konfiguration {#configuring-flexible-port-egress-provision-api}

Einmal pro Programm wird der Endpunkt POST `/program/<programId>/networkInfrastructures` aufgerufen, wobei einfach der Wert von `flexiblePortEgress` für den Parameter `kind` und die Region übergeben wird. Der Endpunkt antwortet mit der `network_id`und andere Informationen, einschließlich des Status.

Nach dem Aufruf dauert es in der Regel etwa 15 Minuten, bis die Netzwerkinfrastruktur bereitgestellt wird. Ein Aufruf an die Cloud Manager - [GET-Endpunkt der Netzwerkinfrastruktur](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getNetworkInfrastructure) würde den Status von **ready**.

>[!TIP]
>
>den vollständigen Satz von Parametern, die genaue Syntax und wichtige Informationen wie die Informationen, welche Parameter später nicht mehr geändert werden können, [kann in der API-Dokumentation referenziert werden.](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure)

### Traffic-Routing {#flexible-port-egress-traffic-routing}

Für HTTP- oder HTTPS-Traffic, der an andere Ports als 80 oder 443 geleitet wird, sollte ein Proxy mit den folgenden Host- und Port-Umgebungsvariablen konfiguriert werden:

* für HTTP: `AEM_PROXY_HOST` / `AEM_HTTP_PROXY_PORT ` (Standardeinstellung ist `proxy.tunnel:3128` in AEM-Versionen &lt; 6094)
* für HTTPS: `AEM_PROXY_HOST` / `AEM_HTTPS_PROXY_PORT ` (Standardeinstellung ist `proxy.tunnel:3128` in AEM-Versionen &lt; 6094)

Hier finden Sie Beispielcode zum Senden einer Anfrage an `www.example.com:8443`:

```java
String url = "www.example.com:8443"
String proxyHost = System.getenv().getOrDefault("AEM_PROXY_HOST", "proxy.tunnel");
int proxyPort = Integer.parseInt(System.getenv().getOrDefault("AEM_HTTPS_PROXY_PORT", "3128"));
HttpClient client = HttpClient.newBuilder()
      .proxy(ProxySelector.of(new InetSocketAddress(proxyHost, proxyPort)))
      .build();
 
HttpRequest request = HttpRequest.newBuilder().uri(URI.create(url)).build();
HttpResponse<String> response = client.send(request, BodyHandlers.ofString());
```

Wenn Sie nicht standardmäßige Java-Netzwerkbibliotheken verwenden, konfigurieren Sie mithilfe der oben genannten Eigenschaften Proxys für den gesamten Traffic.

Nicht-HTTP/s-Traffic mit Zielen über Ports, die im `portForwards`-Parameter deklariert wurden, sollte auf eine Eigenschaft namens `AEM_PROXY_HOST` verweisen, zusammen mit dem zugeordneten Port. Beispiel:

```java
DriverManager.getConnection("jdbc:mysql://" + System.getenv("AEM_PROXY_HOST") + ":53306/test");
```

In der folgenden Tabelle wird das Traffic-Routing beschrieben:

<table>
<thead>
  <tr>
    <th>Traffic</th>
    <th>Zielbedingung</th>
    <th>Port</th>
    <th>Verbindung</th>
    <th>Beispiel für ein externes Ziel</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>HTTP- oder HTTPS-Protokoll</b></td>
    <td>Standard-HTTP/s-Traffic</td>
    <td>80 oder 443</td>
    <td>Zugelassen</td>
    <td></td>
  </tr> 
  <tr>
    <td></td>
    <td>Nicht standardmäßiger Traffic (an anderen Ports außerhalb von 80 oder 443) über HTTP-Proxy, der mit der folgenden Umgebungsvariablen und der Proxy-Port-Nummer konfiguriert wurde. Deklarieren Sie den Ziel-Port nicht im Parameter portForwards des Cloud Manager-API-Aufrufs:<br><ul>
     <li>AEM_PROXY_HOST (in AEM-Versionen &lt; 6094 standardmäßig "proxy.tunnel")</li>
     <li>AEM_HTTPS_PROXY_PORT (standardmäßig Port 3128 in AEM Versionen &lt; 6094)</li>
    </ul>
    <td>Ports außerhalb 80 oder 443</td>
    <td>Zugelassen</td>
    <td>example.com:8443</td>
  </tr>
  <tr>
    <td></td>
    <td>Nicht standardmäßiger Traffic (an anderen Ports außerhalb der Ports 80 oder 443), der keinen HTTP-Proxy verwendet</td>
    <td>Ports außerhalb 80 oder 443</td>
    <td>Blockiert</td>
    <td></td>
  </tr>
  <tr>
    <td><b>Nicht-HTTP oder Nicht-HTTPS</b></td>
    <td>Der Client verbindet sich mit der Umgebungsvariablen <code>AEM_PROXY_HOST</code> über ein <code>portOrig</code>, das im API-Parameter <code>portForwards</code> angegeben ist.</td>
    <td>Alle</td>
    <td>Zugelassen</td>
    <td><code>mysql.example.com:3306</code></td>
  </tr>
  <tr>
    <td></td>
    <td>Alles andere</td>
    <td>Alle</td>
    <td>Blockiert</td>
    <td><code>db.example.com:5555</code></td>
  </tr>
</tbody>
</table>

#### Apache-/Dispatcher-Konfiguration {#apache-dispatcher}

Die `mod_proxy`-Direktive der Apache/Dispatcher-Schicht von AEM as a Cloud Service kann mithilfe der oben beschriebenen Eigenschaften konfiguriert werden.

```
ProxyRemote "http://example.com:8080" "http://${AEM_PROXY_HOST}:3128"
ProxyPass "/somepath" "http://example.com:8080"
ProxyPassReverse "/somepath" "http://example.com:8080"
```

```
SSLProxyEngine on //needed for https backends
 
ProxyRemote "https://example.com:8443" "http://${AEM_PROXY_HOST}:3128"
ProxyPass "/somepath" "https://example.com:8443"
ProxyPassReverse "/somepath" "https://example.com:8443"
```

## Dedizierte Ausgangs-IP-Adresse {#dedicated-egress-ip-address}

Eine dedizierte IP-Adresse kann die Sicherheit bei der Integration mit SaaS-Anbietern (wie z. B. einem CRM-Anbieter) oder anderen Integrationen außerhalb AEM as a Cloud Service verbessern, die eine Zulassungsliste von IP-Adressen bieten. Durch Hinzufügen der dedizierten IP-Adresse zur Zulassungsliste wird sichergestellt, dass nur Traffic vom AEM Cloud-Service des Kunden in den externen Service fließen darf. Dies geschieht zusätzlich zum Traffic von allen anderen zulässigen IPs.

Dieselbe dedizierte IP wird auf alle Programme in Ihrer Adobe-Organisation und für alle Umgebungen in jedem Programm angewendet. Sie gilt sowohl für Autoren- als auch für Veröffentlichungs-Services.

Ohne aktivierte dedizierte IP-Adressenfunktion fließt der Traffic aus AEM as a Cloud Service Datenströmen über eine Reihe von IPs, die mit anderen AEM as a Cloud Service Kunden geteilt werden.

Die Konfiguration der dedizierten Ausgangs-IP-Adresse ähnelt der [flexibler Port-Ausgang.](#flexible-port-egress) Der Hauptunterschied besteht darin, dass nach der Konfiguration der Traffic immer von einer dedizierten, eindeutigen IP-Adresse ausgeht. Um diese IP zu finden, verwenden Sie einen DNS-Resolver, um die IP-Adresse zu identifizieren, die mit `p{PROGRAM_ID}.external.adobeaemcloud.com` verbunden ist. Es wird nicht erwartet, dass sich die IP-Adresse ändert. Wenn sie sich jedoch ändern muss, wird eine erweiterte Benachrichtigung bereitgestellt.

>[!TIP]
>
>Bei der Entscheidung zwischen flexiblem Port-Ausgang und dedizierter Ausgangs-IP-Adresse wird empfohlen, einen flexiblen Port-Ausgang zu wählen, wenn keine bestimmte IP-Adresse erforderlich ist, da Adobe die Traffic-Leistung des flexiblen Port-Ausgangs optimieren kann.

>[!NOTE]
>
>Wenn Sie vor 2021.09.30 über eine dedizierte Ausgangs-IP verfügen (d. h. vor der Version vom September 2021), unterstützt Ihre dedizierte Ausgangs-IP-Funktion nur HTTP- und HTTPS-Ports.
>
>Dazu gehören HTTP/1.1 und HTTP/2 bei Verschlüsselung. Darüber hinaus kann ein dedizierter Ausgangsendpunkt nur über HTTP/HTTPS an den Ports 80/443 mit einem beliebigen Ziel kommunizieren.

>[!NOTE]
>
>Nach der Erstellung können keine dedizierten Ausgangs-IP-Adressen-Infrastrukturtypen bearbeitet werden. Die einzige Möglichkeit, Konfigurationswerte zu ändern, besteht darin, sie zu löschen und neu zu erstellen.

>[!INFO]
>
>Die Splunk-Weiterleitungsfunktion ist über eine dedizierte Ausgangs-IP-Adresse nicht möglich.

### UI-Konfiguration {#configuring-dedicated-egress-provision-ui}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie im Bildschirm **[Eigene Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** das Programm aus.

1. Aus dem **Programmübersicht** Seite, navigieren Sie zur **Umgebungen** Registerkarte und wählen Sie **Netzwerkinfrastruktur** im linken Bereich.

   ![Hinzufügen von Netzwerkinfrastruktur](assets/advanced-networking-ui-network-infrastructure.png)

1. Im **Netzwerkinfrastruktur hinzufügen** Assistent, der gestartet wird, wählen Sie **Dedizierte Ausgangs-IP-Adresse** und die Region, in der sie erstellt werden soll, aus der **Region** Dropdown-Menü und tippen oder klicken Sie auf **Weiter**.

   ![Konfigurieren der dedizierten Ausgangs-IP-Adresse](assets/advanced-networking-ui-dedicated-egress.png)

1. Die **Bestätigung** -Tab fasst Ihre Auswahl und die nächsten Schritte zusammen. Tippen oder klicken **Speichern** , um die Infrastruktur zu erstellen.

   ![Konfiguration der flexiblen Port-Ausfahrt bestätigen](assets/advanced-networking-ui-dedicated-egress-confirmation.png)

Unter dem **Netzwerkinfrastruktur** -Überschrift im seitlichen Bedienfeld mit Details zum Typ der Infrastruktur, des Status, der Region und der Umgebungen, in denen sie aktiviert wurde.

![Neuer Eintrag unter &quot;Netzinfrastruktur&quot;](assets/advanced-networking-ui-flexible-port-egress-new-entry.png)

>[!NOTE]
>
>Die Erstellung der Infrastruktur für flexible Port-Ausgänge kann bis zu einer Stunde dauern, nach der sie auf Umgebungsebene konfiguriert werden kann.

### API-Konfiguration {#configuring-dedicated-egress-provision-api}

Einmal pro Programm wird der Endpunkt POST `/program/<programId>/networkInfrastructures` aufgerufen, wobei einfach der Wert von `dedicatedEgressIp` für den Parameter `kind` und die Region übergeben wird. Der Endpunkt antwortet mit der `network_id`und andere Informationen, einschließlich des Status.

Nach dem Aufruf dauert es in der Regel etwa 15 Minuten, bis die Netzwerkinfrastruktur bereitgestellt wird. Ein Aufruf an die Cloud Manager - [GET-Endpunkt der Netzwerkinfrastruktur](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getNetworkInfrastructure) würde den Status von **ready**.

>[!TIP]
>
>den vollständigen Satz von Parametern, die genaue Syntax und wichtige Informationen wie die Informationen, welche Parameter später nicht mehr geändert werden können, [kann in der API-Dokumentation referenziert werden.](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure)

### Traffic-Routing {#dedicated-egress-ip-traffic-routing}

HTTP- oder HTTPS-Datenverkehr durchläuft einen vorkonfigurierten Proxy, wenn er standardmäßige Java-Systemeigenschaften für Proxy-Konfigurationen verwendet.

Nicht-HTTP/s-Traffic mit Zielen über Ports, die im `portForwards`-Parameter deklariert wurden, sollte auf eine Eigenschaft namens `AEM_PROXY_HOST` verweisen, zusammen mit dem zugeordneten Port. Beispiel:

```java
DriverManager.getConnection("jdbc:mysql://" + System.getenv("AEM_PROXY_HOST") + ":53306/test");
```

<table>
<thead>
  <tr>
    <th>Traffic</th>
    <th>Zielbedingung</th>
    <th>Port</th>
    <th>Verbindung</th>
    <th>Beispiel für ein externes Ziel</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>HTTP- oder HTTPS-Protokoll</b></td>
    <td>Traffic zu Azure- oder Adobe-Services</td>
    <td>Alle</td>
    <td>Über die freigegebenen Cluster-IPs (nicht die dedizierte IP)</td>
    <td>adobe.io<br>api.windows.net</td>
  </tr>
  <tr>
    <td></td>
    <td>Host, der dem Parameter <code>nonProxyHosts</code> entspricht</td>
    <td>80 oder 443</td>
    <td>Über die freigegebenen Cluster-IPs</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Host, der dem Parameter <code>nonProxyHosts</code> entspricht</td>
    <td>Ports außerhalb 80 oder 443</td>
    <td>Blockiert</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Durch die HTTP-Proxy-Konfiguration, die standardmäßig für den HTTP/s-Traffic mithilfe der standardmäßigen Java-HTTP-Client-Bibliothek konfiguriert ist</td>
    <td>Alle</td>
    <td>Über die dedizierte Ausgangs-IP</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Ignoriert die HTTP-Proxy-Konfiguration (z. B. wenn diese explizit aus der standardmäßigen Java-HTTP-Client-Bibliothek entfernt wurde oder wenn eine Java-Bibliothek verwendet wird, die die standardmäßige Proxy-Konfiguration ignoriert)</td>
    <td>80 oder 443</td>
    <td>Über die freigegebenen Cluster-IPs</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Ignoriert die HTTP-Proxy-Konfiguration (z. B. wenn diese explizit aus der standardmäßigen Java-HTTP-Client-Bibliothek entfernt wurde oder wenn eine Java-Bibliothek verwendet wird, die die standardmäßige Proxy-Konfiguration ignoriert)</td>
    <td>Ports außerhalb 80 oder 443</td>
    <td>Blockiert</td>
    <td></td>
  </tr>
  <tr>
    <td><b>Nicht-HTTP oder Nicht-HTTPS</b></td>
    <td>Der Client stellt eine Verbindung zur Umgebungsvariablen <code>AEM_PROXY_HOST</code> her, indem er ein im API-Parameter <code>portForwards</code> angegebenes <code>portOrig</code> verwendet</td>
    <td>Alle</td>
    <td>Über die dedizierte Ausgangs-IP</td>
    <td><code>mysql.example.com:3306</code></td>
  </tr>
  <tr>
    <td></td>
    <td>Alles andere</td>
    <td></td>
    <td>Blockiert</td>
    <td></td>
  </tr>
</tbody>
</table>

### Verwendung der Funktion {#feature-usage}

Die Funktion ist mit Java-Code oder Bibliotheken kompatibel, die zu ausgehendem Datenverkehr führen, sofern sie Standard-Java-Systemeigenschaften für Proxy-Konfigurationen verwenden. In der Praxis sollte dies die gängigsten Bibliotheken umfassen.

Nachfolgend finden Sie ein Code-Beispiel:

```java
public JSONObject getJsonObject(String relativePath, String queryString) throws IOException, JSONException {
  String relativeUri = queryString.isEmpty() ? relativePath : (relativePath + '?' + queryString);
  URL finalUrl = endpointUri.resolve(relativeUri).toURL();
  URLConnection connection = finalUrl.openConnection();
  connection.addRequestProperty("Accept", "application/json");
  connection.addRequestProperty("X-API-KEY", apiKey);

  try (InputStream responseStream = connection.getInputStream(); Reader responseReader = new BufferedReader(new InputStreamReader(responseStream, Charsets.UTF_8))) {
    return new JSONObject(new JSONTokener(responseReader));
  }
}
```

Einige Bibliotheken erfordern eine explizite Konfiguration, um standardmäßige Java-Systemeigenschaften für Proxy-Konfigurationen zu verwenden.

Ein Beispiel mit Apache HttpClient, das explizite Aufrufe an
[`HttpClientBuilder.useSystemProperties()`](https://hc.apache.org/httpcomponents-client-4.5.x/current/httpclient/apidocs/org/apache/http/impl/client/HttpClientBuilder.html) oder die Verwendung von
[`HttpClients.createSystem()`](https://hc.apache.org/httpcomponents-client-4.5.x/current/httpclient/apidocs/org/apache/http/impl/client/HttpClients.html#createSystem()) erfordert:

```java
public JSONObject getJsonObject(String relativePath, String queryString) throws IOException, JSONException {
  String relativeUri = queryString.isEmpty() ? relativePath : (relativePath + '?' + queryString);
  URL finalUrl = endpointUri.resolve(relativeUri).toURL();

  HttpClient httpClient = HttpClientBuilder.create().useSystemProperties().build();
  HttpGet request = new HttpGet(finalUrl.toURI());
  request.setHeader("Accept", "application/json");
  request.setHeader("X-API-KEY", apiKey);
  HttpResponse response = httpClient.execute(request);
  String result = EntityUtils.toString(response.getEntity());
}
```

### Überlegungen zum Debugging {#debugging-considerations}

Um zu überprüfen, ob der Traffic tatsächlich über die erwartete dedizierte IP-Adresse ausgeht, überprüfen Sie die Protokolle im Zieldienst, sofern verfügbar. Andernfalls kann es nützlich sein, einen Debugging-Service wie [https://ifconfig.me/IP](https://ifconfig.me/IP) aufzurufen, der die aufrufende IP-Adresse zurückgibt.

## Virtuelles privates Netzwerk (VPN) {#vpn}

Ein VPN ermöglicht die Verbindung zu einer On-Premise-Infrastruktur oder einem Rechenzentrum von der Autoren-, Veröffentlichungs- oder Vorschauinstanz aus. Dies kann beispielsweise nützlich sein, um den Zugriff auf eine Datenbank zu sichern. Es ermöglicht auch die Verbindung zu SaaS-Anbietern wie einem CRM-Anbieter, der VPN unterstützt oder eine Verbindung von einem Unternehmensnetzwerk mit AEM as a Cloud Service Autoren-, Vorschau- oder Veröffentlichungsinstanz herstellt.

Die meisten VPN-Geräte mit IPSec-Technologie werden unterstützt. Lesen Sie die Informationen im Abschnitt **RouteBased-Konfigurationsanweisungen** Spalte in [diese Liste von Geräten.](https://docs.microsoft.com/de-de/azure/vpn-gateway/vpn-gateway-about-vpn-devices#devicetable) Konfigurieren Sie das Gerät wie in der Tabelle beschrieben.

>[!NOTE]
>
>Beachten Sie diese Einschränkungen der VPN-Infrastruktur:
>
>* Unterstützung ist auf eine einzelne VPN-Verbindung beschränkt
>* Die Splunk-Weiterleitungsfunktion ist über eine VPN-Verbindung nicht möglich.
>* DNS-Resolver müssen im Gateway-Adressraum aufgelistet sein, um private Hostnamen aufzulösen.

### UI-Konfiguration {#configuring-vpn-ui}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie im Bildschirm **[Eigene Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** das Programm aus.

1. Aus dem **Programmübersicht** Seite, navigieren Sie zur **Umgebungen** Registerkarte und wählen Sie **Netzwerkinfrastruktur** im linken Bereich.

   ![Hinzufügen von Netzwerkinfrastruktur](assets/advanced-networking-ui-network-infrastructure.png)

1. Im **Netzwerkinfrastruktur hinzufügen** Assistent, der gestartet wird, wählen Sie **Virtuelles privates Netzwerk** und geben Sie die erforderlichen Informationen ein, bevor Sie auf **Weiter**.

   * **Region** - Dies ist die Region, in der Infrastruktur geschaffen werden sollte.
   * **Adresse** - Der Adressraum darf nur ein /26 CIDR (64 IP-Adressen) oder ein größerer IP-Bereich im Kundenbereich sein.
      * Dieser Wert kann später nicht mehr geändert werden.
   * **DNS-Informationen** - Dies ist eine Liste der Remote-DNS-Resolver.
      * Presse `Enter` nach Eingabe einer DNS-Server-Adresse, um eine weitere hinzuzufügen.
      * Tippen oder klicken Sie auf `X` nach einer Adresse, um sie zu entfernen.
   * **Gemeinsamer Schlüssel** - Dies ist Ihr VPN-vorgegebener Schlüssel.
      * Auswählen **Freigegebenen Schlüssel anzeigen** , um den Schlüssel anzuzeigen, dessen Wert überprüft werden soll.

   ![VPN konfigurieren](assets/advanced-networking-ui-vpn.png)

1. Im **Verbindungen** Registerkarte des Assistenten, geben Sie eine **Verbindungsname** um Ihre VPN-Verbindung zu identifizieren, tippen oder klicken Sie auf **Verbindung hinzufügen**.

   ![Verbindung hinzufügen](assets/advanced-networking-ui-vpn-add-connection.png)

1. Im **Verbindung hinzufügen** Dialogfeld, definieren Sie Ihre VPN-Verbindung und tippen oder klicken Sie auf **Speichern**.

   * **Verbindungsname** - Dies ist ein beschreibender Name Ihrer VPN-Verbindung, den Sie im vorherigen Schritt angegeben haben und hier aktualisiert werden können.
   * **Adresse** - Dies ist die IP-Adresse des VPN-Geräts.
   * **Adressraum** - Dies sind die IP-Adressbereiche, die über das VPN weitergeleitet werden.
      * Presse `Enter` nach Eingabe eines Bereichs, um einen weiteren hinzuzufügen.
      * Tippen oder klicken Sie auf `X` nach einem Bereich, um ihn zu entfernen.
   * **IP-Sicherheitsrichtlinie** - Passen Sie bei Bedarf von den Standardwerten an.

   ![VPN-Verbindung hinzufügen](assets/advanced-networking-ui-vpn-adding-connection.png)

1. Das Dialogfeld wird geschlossen und Sie kehren zum **Verbindungen** im Assistenten. Tippen oder klicken Sie auf **Weiter**.

   ![Eine VPN-Verbindung wird hinzugefügt](assets/advanced-networking-ui-vpn-connection-added.png)

1. Die **Bestätigung** -Tab fasst Ihre Auswahl und die nächsten Schritte zusammen. Tippen oder klicken **Speichern** , um die Infrastruktur zu erstellen.

   ![Konfiguration der flexiblen Port-Ausfahrt bestätigen](assets/advanced-networking-ui-vpn-confirm.png)

Unter dem **Netzwerkinfrastruktur** -Überschrift im seitlichen Bedienfeld mit Details zum Typ der Infrastruktur, des Status, der Region und der Umgebungen, in denen sie aktiviert wurde.

### API-Konfiguration {#configuring-vpn-api}

Die POST `/program/<programId>/networkInfrastructures` Endpunkt wird aufgerufen und eine Payload mit Konfigurationsinformationen übergeben, einschließlich: des Werts von **vpn** für die `kind` Parameter, Region, Adressraum (Liste der CIDRs - dies kann später nicht geändert werden), DNS-Resolver (zur Namensauflösung im Netzwerk des Kunden) und VPN-Verbindungsinformationen wie Gateway-Konfiguration, freigegebener VPN-Schlüssel und IP-Sicherheitsrichtlinie. Der Endpunkt antwortet mit der `network_id`und andere Informationen, einschließlich des Status.

Nach dem Aufruf dauert es in der Regel zwischen 45 und 60 Minuten, bis die Netzwerkinfrastruktur bereitgestellt wird. Die GET-Methode der API kann aufgerufen werden, um den aktuellen Status zurückzugeben, der schließlich von `creating` zu `ready` wechselt. In der API-Dokumentation finden Sie alle Status.

>[!TIP]
>
>den vollständigen Satz von Parametern, die genaue Syntax und wichtige Informationen wie die Informationen, welche Parameter später nicht mehr geändert werden können, [kann in der API-Dokumentation referenziert werden.](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure)

### Traffic-Routing {#vpn-traffic-routing}

In der folgenden Tabelle wird das Traffic-Routing beschrieben.

<table>
<thead>
  <tr>
    <th>Traffic</th>
    <th>Zielbedingung</th>
    <th>Port</th>
    <th>Verbindung</th>
    <th>Beispiel für ein externes Ziel</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>HTTP- oder HTTPS-Protokoll</b></td>
    <td>Traffic zu Azure- oder Adobe-Services</td>
    <td>Alle</td>
    <td>Über die freigegebenen Cluster-IPs (nicht die dedizierte IP)</td>
    <td>adobe.io<br>api.windows.net</td>
  </tr>
  <tr>
    <td></td>
    <td>Host, der dem Parameter <code>nonProxyHosts</code> entspricht</td>
    <td>80 oder 443</td>
    <td>Über die freigegebenen Cluster-IPs</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Host, der dem Parameter <code>nonProxyHosts</code> entspricht</td>
    <td>Ports außerhalb 80 oder 443</td>
    <td>Blockiert</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Wenn die IP-Adresse in den <i>Adressbereich des VPN-Gateways</i> fällt, durch die HTTP-Proxy-Konfiguration (standardmäßig für HTTP/s-Traffic unter Verwendung der Standard-Java-HTTP-Client-Bibliothek konfiguriert)</td>
    <td>Alle</td>
    <td>Durch das VPN</td>
    <td><code>10.0.0.1:443</code><br>Es kann auch ein Hostname sein.</td>
  </tr>
  <tr>
    <td></td>
    <td>Wenn die IP nicht zum <i>Adressbereich des VPN-Gateways</i> gehört, durch die HTTP-Proxy-Konfiguration (standardmäßig für den HTTP/s-Traffic mit der standardmäßigen Java-HTTP-Client-Bibliothek konfiguriert)</td>
    <td>Alle</td>
    <td>Über die dedizierte Ausgangs-IP</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Ignoriert die HTTP-Proxy-Konfiguration (z. B. wenn diese explizit aus der standardmäßigen Java-HTTP-Client-Bibliothek entfernt wurde oder wenn eine Java-Bibliothek verwendet wird, die die standardmäßige Proxy-Konfiguration ignoriert)
</td>
    <td>80 oder 443</td>
    <td>Über die freigegebenen Cluster-IPs</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Ignoriert die HTTP-Proxy-Konfiguration (z. B. wenn diese explizit aus der standardmäßigen Java-HTTP-Client-Bibliothek entfernt wurde oder wenn eine Java-Bibliothek verwendet wird, die die standardmäßige Proxy-Konfiguration ignoriert)</td>
    <td>Ports außerhalb 80 oder 443</td>
    <td>Blockiert</td>
    <td></td>
  </tr>
  <tr>
    <td><b>Nicht-HTTP oder Nicht-HTTPS</b></td>
    <td>Wenn die IP in den <i>Adressbereich des VPN-Gateways</i> fällt und der Client sich mithilfe einer <code>portOrig</code>, die im API-Parameter <code>portForwards</code> deklariert wurde, mit der <code>AEM_PROXY_HOST</code>-Umgebungs-Variable verbindet</td>
    <td>Alle</td>
    <td>Durch das VPN</td>
    <td><code>10.0.0.1:3306</code><br>Es kann auch ein Hostname sein.</td>
  </tr>
  <tr>
    <td></td>
    <td>Wenn die IP nicht zum <i>Adressbereich des VPN-Gateways</i> gehört und der Client sich mithilfe einer <code>portOrig</code>, die im API-Parameter <code>portForwards</code> deklariert wurde, mit der Umgebungs-Variable <code>AEM_PROXY_HOST</code> verbindet</td>
    <td>Alle</td>
    <td>Über die dedizierte Ausgangs-IP</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Alles andere</td>
    <td>Alle</td>
    <td>Blockiert</td>
    <td></td>
  </tr>
</tbody>
</table>

### Nützliche Domains für die Konfiguration {#vpn-useful-domains-for-configuration}

Das folgende Diagramm zeigt eine visuelle Darstellung einer Reihe von Domains und zugehörigen IPs, die für die Konfiguration und Entwicklung nützlich sind. Die Tabelle weiter unten im Diagramm beschreibt diese Domains und IPs.

![VPN-Domain-Konfiguration](/help/security/assets/AdvancedNetworking.jpg)

<table>
<thead>
  <tr>
    <th>Domain-Muster</th>
    <th>Ausgang (aus AEM) Bedeutung</th>
    <th>Eingang (in AEM) Bedeutung</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><code>p{PROGRAM_ID}.external.adobeaemcloud.com</code></td>
    <td>Dedizierte Ausgangs-IP-Adresse für Traffic, der zum Internet statt über private Netzwerke geleitet wird </td>
    <td>Verbindungen des VPN würden beim CDN als von dieser IP kommend angezeigt. Um für den Eingang in AEM nur Verbindungen vom VPN zuzulassen, konfigurieren Sie Cloud Manager so, dass nur diese IP zugelassen und alles andere blockiert wird. Weitere Informationen finden Sie im Abschnitt „Eingänge auf VPN-Verbindungen beschränken“.</td>
  </tr>
  <tr>
    <td><code>p{PROGRAM_ID}.{REGION}-gateway.external.adobeaemcloud.com</code></td>
    <td>Nicht zutreffend</td>
    <td>Die IP des VPN-Gateways auf der Seite von AEM. Das Netzwerk-Engineering-Team eines Kunden kann dies verwenden, um zu seinem VPN-Gateway von einer bestimmten IP-Adresse aus nur VPN-Verbindungen zuzulassen. </td>
  </tr>
  <tr>
    <td><code>p{PROGRAM_ID}.{REGION}.inner.adobeaemcloud.net</code></td>
    <td>Die IP des Traffics kommt dabei von der AEM-Seite des VPN zur Kundenseite. Dies kann in der Kundenkonfiguration auf die Zulassungsliste gesetzt werden, um sicherzustellen, dass Verbindungen nur von AEM aus hergestellt werden können.</td>
    <td>Wenn der Kunde nur VPN-Zugriff auf AEM zulassen möchte, sollte er CNAME-DNS-Einträge konfigurieren, um <code>author-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code> und/oder <code>publish-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code> diesen zuzuordnen.</td>
  </tr>
</tbody>
</table>

### VPN auf eingehende Verbindungen beschränken {#restrict-vpn-to-ingress-connections}

Wenn Sie nur den VPN-Zugriff auf AEM zulassen möchten, können Umgebungszulassungslisten in Cloud Manager so konfiguriert werden, dass nur die durch `p{PROGRAM_ID}.external.adobeaemcloud.com` definierte IP mit der Umgebung kommunizieren darf. Dies kann auf dieselbe Weise wie bei jeder anderen IP-basierten Zulassungsliste in Cloud Manager erfolgen.

Wenn Regeln pfadbasiert sein müssen, verwenden Sie standardmäßige HTTP-Anweisungen auf Dispatcher-Ebene, um bestimmte IPs zu blockieren oder zuzulassen. Sie sollten sicherstellen, dass die gewünschten Pfade auch im CDN nicht zwischenspeicherbar sind, sodass die Anfrage immer an den Ursprung gelangt.

#### Beispiel für Httpd-Konfiguration {#httpd-example}

```
Order deny,allow
Deny from all
Allow from 192.168.0.1
Header always set Cache-Control private
```

## Aktivieren erweiterter Netzwerkkonfigurationen in Umgebungen {#enabling}

Sobald Sie eine erweiterte Netzwerkoption für ein Programm konfiguriert haben, können Sie entscheiden, ob [flexibles Auslaufen von Ports,](#flexible-port-egress) [dedizierte Ausgangs-IP-Adresse,](#dedicated-egress-ip-address) oder [VPN,](#vpn) Um sie verwenden zu können, müssen Sie sie auf Umgebungsebene aktivieren.

Wenn Sie eine erweiterte Netzwerkkonfiguration für eine Umgebung aktivieren, können Sie die optionale Anschlussweiterleitung und Nicht-Proxy-Hosts aktivieren. Parameter können je nach Umgebung konfiguriert werden, um Flexibilität zu bieten.

* **Hafenweiterleitung** - Regeln für die Hafenweiterleitung sollten für alle Zielports mit Ausnahme von 80/443 deklariert werden, jedoch nur, wenn sie nicht das HTTP- oder HTTPS-Protokoll verwenden.
   * Regeln für die Anschlussweiterleitung werden definiert, indem der Satz von Ziel-Hosts (Namen oder IP und Ports) angegeben wird.
   * Die Clientverbindung, die Port 80/443 über HTTP/https verwendet, muss in ihrer Verbindung weiterhin Proxy-Einstellungen verwenden, damit die Eigenschaften des erweiterten Netzwerks auf die Verbindung angewendet werden.
   * Für jeden Ziel-Host müssen Kunden den vorgesehenen Ziel-Port einem Port von 30000 bis 30999 zuordnen.
   * Regeln zur Port-Weiterleitung sind für alle erweiterten Netzwerktypen verfügbar.

* **Nicht-Proxy-Hosts** - Nicht-Proxy-Hosts ermöglichen es Ihnen, eine Gruppe von Hosts zu deklarieren, die über einen freigegebenen IP-Adressbereich statt über die dedizierte IP weitergeleitet werden sollen.
   * Dies kann nützlich sein, da das Traffic-egressing über freigegebene IPs weiter optimiert werden kann.
   * Nicht-Proxy-Hosts sind nur für dedizierte Egress-IP-Adressen und VPN-erweiterte Netzwerktypen verfügbar.

>[!NOTE]
>
>Sie können keine erweiterte Netzwerkkonfiguration für eine Umgebung aktivieren, wenn sich die Umgebung in der **Aktualisieren** -Status.

### Aktivieren über die Benutzeroberfläche {#enabling-ui}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie im Bildschirm **[Eigene Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** das Programm aus.

1. Aus dem **Programmübersicht** Seite, navigieren Sie zur **Umgebungen** und wählen Sie die Umgebung aus, in der Sie die erweiterte Netzwerkkonfiguration aktivieren möchten, unter **Umgebungen** im linken Bereich. Wählen Sie dann die **Erweiterte Netzwerkkonfiguration** Registerkarte der ausgewählten Umgebung und tippen oder klicken Sie auf **Netzwerkinfrastruktur aktivieren**.

   ![Umgebung auswählen, um erweiterte Netzwerke zu aktivieren](assets/advanced-networking-ui-enable-environments.png)

1. Die **Erweiterte Netzwerkkonfiguration** wird geöffnet.

1. Im **Nicht-Proxy-Hosts** für dedizierte Ausgangs-IP-Adressen und VPNs können Sie optional eine Reihe von Hosts definieren, die über einen freigegebenen IP-Adressbereich und nicht über die dedizierte IP weitergeleitet werden sollen, indem Sie den Hostnamen im **Nicht-Proxy-Host** Feld und Tippen oder Klicken **Hinzufügen**.

   * Der Host wird der Hostliste auf der Registerkarte hinzugefügt.
   * Wiederholen Sie diesen Schritt, um mehrere Hosts hinzuzufügen.
   * Tippen oder klicken Sie auf das X rechts neben der Zeile, um einen Host zu entfernen.
   * Diese Registerkarte ist nicht für flexible Port-Ausstiegskonfigurationen verfügbar.

   ![Nicht-Proxy-Hosts hinzufügen](assets/advanced-networking-ui-enable-non-proxy-hosts.png)

1. Im **Hafen vorwärts** -Registerkarte können Sie optional Regeln für die Anschlussweiterleitung für beliebige Zielports definieren, die über 80/443 hinausgehen, wenn Sie HTTP oder HTTPS nicht verwenden. Stellen Sie eine **Name**, **Port Orig**, und **Port Dest** und tippen oder klicken Sie **Hinzufügen**.

   * Die Regel wird der Regelliste auf der Registerkarte hinzugefügt.
   * Wiederholen Sie diesen Schritt, um mehrere Regeln hinzuzufügen.
   * Tippen oder klicken Sie auf das X rechts neben der Zeile, um eine Regel zu entfernen.

   ![Definieren optionaler Anschlussvorführungen](assets/advanced-networking-ui-port-forwards.png)

1. Tippen oder klicken **Speichern** im Dialogfeld, um die Konfiguration auf die Umgebung anzuwenden.

Die erweiterte Netzwerkkonfiguration wird auf die ausgewählte Umgebung angewendet. Zurück auf **Umgebungen** angezeigt, können Sie die Details der auf die ausgewählte Umgebung angewendeten Konfiguration und ihren Status anzeigen.

![Umgebung mit erweitertem Netzwerk](assets/advanced-networking-ui-configured-environment.png)

### Aktivieren mit der API {#enabling-api}

Um eine erweiterte Netzwerkkonfiguration für eine Umgebung zu aktivieren, muss die `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` -Endpunkt muss pro Umgebung aufgerufen werden.

Die API sollte innerhalb weniger Sekunden mit dem Status `updating` antworten, und nach etwa 10 Minuten würde ein Aufruf des GET-Endpunkts für die Umgebung des Cloud Managers den Status `ready` anzeigen, was bedeutet, dass die Aktualisierung der Umgebung durchgeführt wurde.

Pro Umgebung können die Regeln für die Portweiterleitung aktualisiert werden, indem Sie die `PUT /program/{programId}/environment/{environmentId}/advancedNetworking` -Endpunkt und einschließlich des vollständigen Satzes von Konfigurationsparametern anstelle einer Teilmenge.

Die dedizierte Ausgangs-IP-Adresse und die erweiterten VPN-Netzwerktypen unterstützen eine `nonProxyHosts` -Parameter. Auf diese Weise können Sie eine Gruppe von Hosts deklarieren, die über einen freigegebenen IP-Adressbereich statt über die dedizierte IP weitergeleitet werden sollen. Die `nonProxyHost`-URLs können dem Muster von `example.com` oder `*.example.com` folgen, wobei der Platzhalter nur am Beginn der Domain unterstützt wird.

`PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` muss auch dann aufgerufen werden, wenn es keine Regeln für die Weiterleitung des Umgebungs-Traffics (Hosts oder Bypässe) gibt, aber dann mit einer leeren Payload.

>[!TIP]
>
>den vollständigen Satz von Parametern, die genaue Syntax und wichtige Informationen wie die Informationen, welche Parameter später nicht mehr geändert werden können, [kann in der API-Dokumentation referenziert werden.](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure)

## Bearbeiten und Löschen erweiterter Netzwerkkonfigurationen in Umgebungen {#editing-deleting-environments}

Nachher [Aktivierung der erweiterten Netzwerkkonfiguration für Umgebungen,](#enabling) Sie können die Details dieser Konfigurationen aktualisieren oder löschen.

>[!NOTE]
>
>Sie können die Netzwerkinfrastruktur nicht bearbeiten, wenn sie den Status aufweist. **Erstellen**, **Aktualisieren** oder **Löschen**.

### Bearbeiten oder Löschen über die Benutzeroberfläche {#editing-ui}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie im Bildschirm **[Eigene Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** das Programm aus.

1. Aus dem **Programmübersicht** Seite, navigieren Sie zur **Umgebungen** und wählen Sie die Umgebung aus, in der Sie die erweiterte Netzwerkkonfiguration aktivieren möchten, unter **Umgebungen** im linken Bereich. Wählen Sie dann die **Erweiterte Netzwerkkonfiguration** und tippen oder klicken Sie auf die Suchschaltfläche .

   ![Auswahl der Bearbeitung oder Löschung von erweiterten Netzwerken auf Programmebene](assets/advanced-networking-ui-edit-delete.png)

1. Wählen Sie im Menü mit den Auslassungspunkten entweder **Bearbeiten** oder **Löschen**.

   * Wenn Sie **Bearbeiten** aktualisieren Sie die Informationen gemäß den im vorherigen Abschnitt beschriebenen Schritten. [Aktivieren der Benutzeroberfläche,](#enabling-ui) und tippen oder klicken Sie **Speichern**.
   * Wenn Sie **Löschen**, bestätigen Sie den Löschvorgang im **Netzwerkkonfiguration löschen** Dialogfeld mit **Löschen** oder abbrechen mit **Abbrechen**.

Die Änderungen werden im **Umgebungen** Registerkarte.

### Bearbeiten oder Löschen mit der API {#editing-api}

Um das erweiterte Netzwerk für eine bestimmte Umgebung zu löschen, rufen Sie `DELETE [/program/{programId}/environment/{environmentId}/advancedNetworking]()`.

>[!TIP]
>
>den vollständigen Satz von Parametern, die genaue Syntax und wichtige Informationen wie die Informationen, welche Parameter später nicht mehr geändert werden können, [kann in der API-Dokumentation referenziert werden.](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure)

## Bearbeiten und Löschen der Netzwerkinfrastruktur eines Programms {#editing-deleting-program}

Sobald die Netzwerkinfrastruktur für ein Programm erstellt wurde, können nur begrenzte Eigenschaften bearbeitet werden. Wenn Sie es nicht mehr benötigen, können Sie die erweiterte Netzwerkinfrastruktur für Ihr gesamtes Programm löschen.

>[!NOTE]
>
>Beachten Sie die folgenden Einschränkungen beim Bearbeiten und Löschen der Netzwerkinfrastruktur:
>
>* Durch Löschen wird die Infrastruktur nur gelöscht, wenn die erweiterte Vernetzung aller Umgebungen deaktiviert sind.
>* Sie können die Netzwerkinfrastruktur nicht bearbeiten, wenn sie den Status aufweist. **Erstellen**, **Aktualisieren** oder **Löschen**.
>* Nur der erweiterte VPN-Netzwerkinfrastrukturtyp kann nach der Erstellung bearbeitet werden und nur begrenzte Felder.
>* Aus Sicherheitsgründen muss die Variable **Gemeinsamer Schlüssel** muss immer bei der Bearbeitung einer VPN-erweiterten Netzwerkinfrastruktur bereitgestellt werden, auch wenn Sie den Schlüssel selbst nicht bearbeiten.

### Bearbeiten und Löschen mit der Benutzeroberfläche {#delete-ui}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus

1. Wählen Sie im Bildschirm **[Eigene Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** das Programm aus.

1. Aus dem **Programmübersicht** Seite, navigieren Sie zur **Umgebungen** Registerkarte und wählen Sie **Netzwerkinfrastruktur** im linken Bereich. Tippen oder klicken Sie dann auf die Suchschaltfläche neben der Infrastruktur, die Sie löschen möchten.

   ![Auswahl der Bearbeitung oder Löschung von erweiterten Netzwerken auf Programmebene](assets/advanced-networking-ui-delete-infrastructure.png)

1. Wählen Sie im Menü mit den Auslassungspunkten entweder **Bearbeiten** oder **Löschen**.

1. Wenn Sie **Bearbeiten**, die **Netzwerkinfrastruktur bearbeiten** wird geöffnet. Bearbeiten Sie nach Bedarf entsprechend den Schritten, die beim Erstellen der Infrastruktur beschrieben werden.

1. Wenn Sie **Löschen**, bestätigen Sie den Löschvorgang im **Netzwerkkonfiguration löschen** Dialogfeld mit **Löschen** oder abbrechen mit **Abbrechen**.

Die Änderungen werden im **Umgebungen** Registerkarte.

### Bearbeiten und Löschen mit der API {#delete-api}

Um die Netzwerkinfrastruktur für ein Programm zu **löschen**, rufen Sie `DELETE /program/{program ID}/networkinfrastructure/{networkinfrastructureID}` auf.

## Ändern des Typs der erweiterten Netzwerkinfrastruktur eines Programms {#changing-program}

Es ist nur möglich, eine Art von erweiterter Netzwerkinfrastruktur gleichzeitig für ein Programm zu konfigurieren, entweder flexible Port-Ausgänge, dedizierte Ausgangs-IP-Adressen oder VPN.

Wenn Sie entscheiden, dass Sie einen anderen fortgeschrittenen Netzwerkinfrastrukturtyp als den bereits konfigurierten benötigen, müssen Sie die vorhandene löschen und eine neue erstellen. Gehen Sie wie folgt vor:

1. [Löschen Sie erweiterte Netzwerke in allen Umgebungen.](#editing-deleting-environments)
1. [Löschen Sie die erweiterte Netzwerkinfrastruktur.](#editing-deleting-program)
1. Erstellen Sie den von Ihnen jetzt benötigten erweiterten Netzwerkinfrastrukturtyp: [flexibles Auslaufen von Ports,](#flexible-port-egress) [dedizierte Ausgangs-IP-Adresse,](#dedicated-egress-ip-address) oder [VPN.](#vpn)
1. [Erneutes Aktivieren erweiterter Netzwerke auf Umgebungsebene.](#enabling)

>[!WARNING]
>
> Diese Vorgehensweise führt zu einer Ausfallzeit von Services für erweiterte Vernetzung zwischen dem Löschen und der erneuten Erstellung.
> Wenn Ausfallzeiten erhebliche geschäftliche Auswirkungen haben würden, wenden Sie sich an den Support, um Hilfe zu erhalten, und beschreiben Sie, was bereits erstellt wurde und warum die Änderung vorgenommen wurde.

## Erweiterte Netzwerkkonfiguration für zusätzliche Veröffentlichungsregionen {#advanced-networking-configuration-for-additional-publish-regions}

Wenn eine zusätzliche Region zu einer Umgebung hinzugefügt wird, in der bereits ein erweitertes Netzwerk konfiguriert ist, wird der Traffic aus der zusätzlichen Veröffentlichungsregion, der den erweiterten Netzwerkregeln entspricht, standardmäßig durch die primäre Region geleitet. Wenn die primäre Region jedoch nicht verfügbar ist, wird der erweiterte Netzwerk-Traffic abgebrochen, wenn in der zusätzlichen Region das erweiterte Netzwerk nicht aktiviert wurde. Wenn Sie die Latenz optimieren und die Verfügbarkeit im Falle eines Ausfalls in einer der Regionen erhöhen möchten, ist es erforderlich, für die zusätzliche(n) Veröffentlichungsregion(en) ein erweitertes Netzwerk zu aktivieren. In den folgenden Abschnitten werden zwei verschiedene Szenarien beschrieben.

>[!NOTE]
>
>Alle Regionen teilen sich die gleiche [erweiterte Netzwerkkonfiguration der Umgebung](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Environment-Advanced-Networking-Configuration), sodass es nicht möglich ist, Traffic basierend auf der Region, aus der der Traffic austritt, zu verschiedenen Zielen zu leiten.

### Dedizierte Ausgangs-IP-Adressen {#additional-publish-regions-dedicated-egress}

#### Bereits aktiviertes erweitertes Netzwerk in der primären Region {#already-enabled}

Wenn in der primären Region bereits eine erweiterte Netzwerkkonfiguration aktiviert ist, führen Sie die folgenden Schritte aus:

1. Wenn Sie Ihre Infrastruktur so gesperrt haben, dass die dedizierte AEM-IP-Adresse auf der Zulassungsliste ist, wird empfohlen, alle Regeln zur Ablehnung in dieser Infrastruktur vorübergehend zu deaktivieren. Andernfalls werden Anfragen von den IP-Adressen der neuen Region für eine kurze Zeit von Ihrer eigenen Infrastruktur abgelehnt. Dies ist nicht erforderlich, wenn Sie Ihre Infrastruktur über einen vollständig qualifizierten Domain-Namen (Fully Qualified Domain Name, FQDN) gesperrt haben (z. B. `p1234.external.adobeaemcloud.com`), da alle AEM-Regionen den erweiterten Netzwerk-Traffic von demselben FQDN ausgeben
1. Erstellen Sie die programmweite Netzwerkinfrastruktur für die sekundäre Region durch einen POST-Aufruf an die Cloud Manager-API zum Erstellen einer Netzwerkinfrastruktur, wie in der Dokumentation zu erweiterten Netzwerken beschrieben. Der einzige Unterschied in der JSON-Konfiguration der Payload im Verhältnis zur primären Region ist die Regionseigenschaft.
1. Wenn Ihre Infrastruktur nach IP gesperrt werden muss, um AEM-Traffic zu ermöglichen, fügen Sie die IPs hinzu, die mit `p1234.external.adobeaemcloud.com` übereinstimmen. Pro Region sollte es eine geben.

#### Noch kein erweitertes Netzwerk in einer Region konfiguriert {#not-yet-configured}

Das Verfahren ähnelt größtenteils den vorherigen Anweisungen. Wenn die Produktionsumgebung jedoch noch nicht für erweiterte Netzwerke aktiviert wurde, besteht die Möglichkeit, die Konfiguration zu testen, indem sie zuerst in einer Staging-Umgebung aktiviert wird:

1. Erstellen Sie eine Netzwerkinfrastruktur für alle Regionen durch einen POST-Aufruf an die [Cloud Manager-API zum Erstellen einer Netzwerkinfrastruktur](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Network-infrastructure/operation/createNetworkInfrastructure). Der einzige Unterschied in der JSON-Konfiguration der Payload im Verhältnis zur primären Region ist die Regionseigenschaft.
1. Aktivieren und konfigurieren Sie für die Staging-Umgebung das erweiterte Netzwerk, das im Umgebungsumfang verfügbar ist, indem Sie `PUT api/program/{programId}/environment/{environmentId}/advancedNetworking` ausführen. Weitere Informationen finden Sie in der API-Dokumentation [hier](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Environment-Advanced-Networking-Configuration/operation/enableEnvironmentAdvancedNetworkingConfiguration)
1. Sperren Sie ggf. die externe Infrastruktur, vorzugsweise nach FQDN (z. B. `p1234.external.adobeaemcloud.com`). Andernfalls können Sie auch die IP-Adresse verwenden.
1. Wenn die Staging-Umgebung erwartungsgemäß funktioniert, aktivieren und konfigurieren Sie die erweiterte Netzwerkkonfiguration der Umgebung für die Produktion.

#### VPN {#vpn-regions}

Das Verfahren ist fast identisch mit den Anweisungen für dedizierte Ausgangs-IP-Adressen. Der einzige Unterschied besteht darin, dass zusätzlich zur Regionseigenschaft, die anders konfiguriert ist als im primären Bereich, auch das Feld `connections.gateway` optional so konfiguriert werden kann, dass es zu einem anderen VPN-Endpunkt weiterleitet, der von Ihrem Unternehmen verwaltet wird und möglicherweise geografisch näher an der neuen Region liegt.
