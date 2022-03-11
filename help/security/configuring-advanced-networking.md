---
title: Erweiterte Netzwerkfunktionen für AEM as a Cloud Service konfigurieren
description: Erfahren Sie, wie Sie erweiterte Netzwerkfunktionen wie VPN oder eine flexible oder dedizierte Ausgangs-IP-Adresse für AEM as a Cloud Service konfigurieren.
exl-id: 968cb7be-4ed5-47e5-8586-440710e4aaa9
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '2982'
ht-degree: 93%

---

# Erweiterte Netzwerkfunktionen für AEM as a Cloud Service konfigurieren {#configuring-advanced-networking}

Dieser Artikel soll Ihnen die verschiedenen erweiterten Netzwerkfunktionen in AEM as a Cloud Service vorstellen, einschließlich der Bereitstellung von VPN im Self-Service, nicht standardmäßige Ports und dedizierte Ausgangs-IP-Adressen.

>[!INFO]
>
>Eine Reihe von Artikeln, die Sie durch die erweiterten Netzwerkoptionen führen, finden Sie hier . [location](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html?lang=en).

## Übersicht {#overview}

AEM as a Cloud Service bietet verschiedene Arten erweiterter Netzwerkfunktionen, die von den Kunden mithilfe von Cloud Manager-APIs konfiguriert werden können. Dazu gehören:

* [Flexibler Port-Ausgang](#flexible-port-egress): konfigurieren Sie AEM as a Cloud Service, um ausgehenden Traffic aus nicht standardmäßigen Ports zuzulassen.
* [Dedizierte Ausgangs-IP-Adresse](#dedicated-egress-IP-address): Konfigurieren des Traffics aus AEM as a Cloud Service, der von einer eindeutigen IP stammt
* [Virtuelles privates Netzwerk (VPN)](#vpn): Sicherung des Traffics zwischen der Infrastruktur eines Kunden und AEM as a Cloud Service, für Kunden mit VPN-Technologie

In diesem Artikel werden die einzelnen Optionen detailliert beschrieben, einschließlich ihrer Konfiguration. Als allgemeine Konfigurationsstrategie sollte der `/networkInfrastructures`-API-Endpunkt auf Programmebene aufgerufen werden, um den gewünschten Typ von erweitertem Netzwerk zu deklarieren, gefolgt von einem Aufruf an den `/advancedNetworking`-Endpunkt für jede Umgebung, um die Infrastruktur zu aktivieren und umgebungsspezifische Parameter zu konfigurieren. Für jede formale Syntax finden Sie die entsprechenden Endpunkte in der Dokumentation der Cloud Manager-API, sowie Beispiele für Anfragen und Antworten.

Ein Programm kann eine einzige erweiterte Netzwerkvariante bereitstellen. Bei der Entscheidung zwischen flexiblem Port-Ausgang und dedizierter Ausgangs-IP-Adresse wird empfohlen, einen flexiblen Port-Ausgang zu wählen, wenn keine bestimmte IP-Adresse erforderlich ist, da Adobe die Traffic-Leistung des flexiblen Port-Ausgangs optimieren kann.

>[!INFO]
>
>Erweiterte Netzwerke sind für das Sandbox-Programm nicht verfügbar.
>Außerdem müssen Umgebungen auf AEM Version 5958 oder höher aktualisiert werden.

>[!NOTE]
>
>Kunden, die bereits über eine alte Technologie für dedizierte Ausgänge verfügen und eine dieser Optionen konfigurieren müssen, sollten dies nicht tun, da dies sonst die Website-Konnektivität beeinträchtigt sein könnte. Wenn Sie Unterstützung benötigen, wenden Sie sich bitte an den Adobe-Support.

## Flexibler Port-Ausgang {#flexible-port-egress}

Diese erweiterte Netzwerkfunktion ermöglicht es Ihnen, AEM as a Cloud Service so zu konfigurieren, dass der Ausgangs-Traffic über andere Ports als HTTP (Port 80) und HTTPS (Port 443), die standardmäßig geöffnet sind, läuft.

### Zu beachten {#flexible-port-egress-considerations}

Ein flexibler Port-Ausgang ist die empfohlene Wahl, wenn Sie kein VPN benötigen und keine dedizierte Ausgangs-IP-Adresse benötigen, da Traffic, der nicht auf einen dedizierten Ausgang angewiesen ist, einen höheren Durchsatz erzielen kann.

### Konfiguration {#configuring-flexible-port-egress-provision}

Einmal pro Programm wird der Endpunkt POST `/program/<programId>/networkInfrastructures` aufgerufen, wobei einfach der Wert von `flexiblePortEgress` für den Parameter `kind` und die Region übergeben wird. Der Endpunkt antwortet mit der `network_id` sowie anderen Informationen, einschließlich des Status. Der vollständige Satz von Parametern und die genaue Syntax können in den API-Dokumenten nachgelesen werden.

Nach dem Aufruf dauert es in der Regel etwa 15 Minuten, bis die Netzwerkinfrastruktur bereitgestellt wird. Ein Aufruf an die Cloud Manager - [GET-Endpunkt der Netzwerkinfrastruktur](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getNetworkInfrastructure) würde den Status &quot;ready&quot;anzeigen.

Wenn die Konfiguration der flexiblen Port-Ausdrücke für das Programm bereit ist, wird die `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` -Endpunkt muss pro Umgebung aufgerufen werden, um die Vernetzung auf Umgebungsebene zu aktivieren und optional alle Regeln für die Anschlussweiterleitung zu deklarieren. Parameter können je Umgebung konfiguriert werden, um Flexibilität zu bieten.

Regeln für die Port-Weiterleitung sollten für alle anderen Ports als 80/443 deklariert werden, indem der Satz der Ziel-Hosts (Namen oder IP und mit Ports) angegeben wird. Für jeden Ziel-Host müssen Kunden den vorgesehenen Ziel-Port einem Port von 30000 bis 30999 zuordnen.

Die API sollte in nur wenigen Sekunden antworten und einen Aktualisierungsstatus angeben. Nach etwa 10 Minuten sollte die `GET`-Methode des Endpunkts anzeigen, dass das erweiterte Netzwerk aktiviert ist.

### Updates {#updating-flexible-port-egress-provision}

Die Konfiguration auf Programmebene kann durch Aufrufen des `PUT /api/program/<program_id>/network/<network_id>`-Endpunkts aktualisiert werden und wird innerhalb weniger Minuten wirksam.

>[!NOTE]
>
> Der Parameter „kind“ (`flexiblePortEgress`, `dedicatedEgressIP` oder `VPN`) kann nicht geändert werden. Wenn Sie Unterstützung benötigen, wenden Sie sich an den Support und beschreiben Sie, was bereits erstellt wurde und warum Sie die Änderung vornehmen möchten.

Die Regeln für die Port-Weiterleitung pro Umgebung können durch erneutes Aufrufen des `PUT /program/{programId}/environment/{environmentId}/advancedNetworking`-Endpunkts aktualisiert werden, wobei darauf zu achten ist, dass der gesamte Satz an Konfigurationsparametern und nicht nur eine Teilmenge angegeben wird.

### Löschen oder Deaktivieren des flexiblen Port-Ausgangs {#deleting-disabling-flexible-port-egress-provision}

Um die Netzinfrastruktur zu **löschen**, reichen Sie ein Support-Ticket ein, in dem Sie beschreiben, was erstellt wurde und warum sie gelöscht werden muss.

Um den flexiblen Port-Ausgang in einer bestimmten Umgebung zu **deaktivieren**, rufen Sie `DELETE [/program/{programId}/environment/{environmentId}/advancedNetworking]()` auf.

Weitere Informationen finden Sie in der [Dokumentation zur Cloud Manager-API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration).

### Traffic-Routing {#flexible-port-egress-traffic-routing}

Für HTTP- oder HTTPS-Traffic, der an andere Ports als 80 oder 443 geleitet wird, sollte ein Proxy mit den folgenden Host- und Port-Umgebungsvariablen konfiguriert werden:

* für HTTP: `AEM_PROXY_HOST` / `AEM_HTTP_PROXY_PORT ` (Standardeinstellung ist `proxy.tunnel:3128` in AEM Versionen &lt; 6094)
* für HTTPS: `AEM_PROXY_HOST` / `AEM_HTTPS_PROXY_PORT ` (Standardeinstellung ist `proxy.tunnel:3128` in AEM Versionen &lt; 6094)

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
    <td>Nicht standardmäßiger Traffic (an anderen Ports außerhalb von 80 oder 443) über HTTP-Proxy, der mit der folgenden Umgebungsvariablen und der Proxy-Anschlussnummer konfiguriert wurde. Deklarieren Sie den Zielport nicht im Parameter portForwards des Cloud Manager-API-Aufrufs:<br><ul>
     <li>AEM_PROXY_HOST (in AEM Versionen &lt; 6094 standardmäßig "proxy.tunnel")</li>
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

**Apache-/Dispatcher-Konfiguration**

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

## Dedizierte Ausgangs-IP-Adresse {#dedicated-egress-IP-address}

>[!NOTE]
>
>Wenn Sie vor dem Release vom September 2021 (6.10.21) eine dedizierte Ausgangs-IP erhalten haben, lesen Sie bitte [Kunden mit alten dedizierten Ausgang-Adressen](#legacy-dedicated-egress-address-customers).

### Vorteile {#benefits}

Diese dedizierte IP-Adresse kann die Sicherheit bei der Integration mit SaaS-Anbietern (wie z. B. einem CRM-Anbieter) oder anderen Integrationen außerhalb von AEM as a Cloud Service, die eine Zulassungsliste von IP-Adressen anbieten, erhöhen. Durch Hinzufügen der dedizierten IP-Adresse zur Zulassungsliste wird sichergestellt, dass nur Traffic vom AEM Cloud-Service des Kunden in den externen Service fließen darf. Dies geschieht zusätzlich zum Traffic von allen anderen zulässigen IPs.

Wenn die Funktion der dedizierten IP-Adresse nicht aktiviert ist, fließt der Traffic von AEM as a Cloud Service über eine Reihe von IPs, die mit anderen Kunden gemeinsam genutzt werden.

### Konfiguration {#configuring-dedicated-egress-provision}

>[!INFO]
>
>Die Splunk-Weiterleitungsfunktion ist über eine dedizierte Ausgangs-IP-Adresse nicht möglich.

Die Konfiguration der dedizierten Ausgangs-IP-Adresse ist mit dem Szenario [flexibler Port-Ausgang](#configuring-flexible-port-egress-provision) identisch.

Der Hauptunterschied besteht darin, dass der Traffic immer von einer dedizierten, eindeutigen IP-Adresse ausgeht. Um diese IP zu finden, verwenden Sie einen DNS-Resolver, um die IP-Adresse zu identifizieren, die mit `p{PROGRAM_ID}.external.adobeaemcloud.com` verbunden ist. Es wird nicht erwartet, dass sich die IP-Adresse ändert. Sollte sich die IP jedoch in Zukunft ändern, wird eine erweiterte Benachrichtigung bereitgestellt.

Zusätzlich zu den Routing-Regeln, die vom flexiblen Port-Ausgang im `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking`-Endpunkt unterstützt werden, unterstützt die dedizierte Ausgangs-IP-Adresse einen `nonProxyHosts`-Parameter. Auf diese Weise können Sie eine Gruppe von Hosts deklarieren, die über einen gemeinsamen IP-Adressbereich statt über die dedizierte IP weitergeleitet werden sollen. Dies kann nützlich sein, da ausgehender Traffic über freigegebene IPs weiter optimiert werden kann. Die `nonProxyHost`-URLs können dem Muster von `example.com` oder `*.example.com` folgen, wobei der Platzhalter nur am Beginn der Domain unterstützt wird.

Bei der Entscheidung zwischen flexiblem Port-Ausgang und dedizierter Ausgangs-IP-Adresse sollten Kunden einen flexiblen Port-Ausgangt wählen, wenn keine bestimmte IP-Adresse erforderlich ist, da Adobe die Traffic-Leistung an flexiblen Ports-Ausgängen optimieren kann.

### Traffic-Routing {#dedcated-egress-ip-traffic-routing}

HTTP- oder HTTPS-Traffic, der über die Ports 80 oder 443 an Ziele geleitet wird, durchläuft einen vorkonfigurierten Proxy, vorausgesetzt, die standardmäßige Java-Netzwerkbibliothek wird verwendet. Für HTTP- oder HTTPS-Traffic, der über andere Ports erfolgt, sollte ein Proxy mit den folgenden Eigenschaften konfiguriert werden.

```
AEM_HTTP_PROXY_HOST / AEM_HTTPS_PROXY_HOST
AEM_HTTP_PROXY_PORT / AEM_HTTPS_PROXY_PORT
```

Hier finden Sie Beispielcode zum Senden einer Anfrage an `www.example.com:8443`:

```java
String url = "www.example.com:8443"
String proxyHost = System.getenv("AEM_HTTPS_PROXY_HOST");
int proxyPort = Integer.parseInt(System.getenv("AEM_HTTPS_PROXY_PORT"));

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

## Kunden mit alten dediziertes Ausgangs-Adressen {#legacy-dedicated-egress-address-customers}

Wenn Sie vor 2021.09.30 eine dedizierte Ausgangs-IP erhalten haben, funktioniert die Funktion der dedizierten Ausgangs-IP wie unten beschrieben.

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

Dieselbe dedizierte IP wird auf alle Programme eines Kunden in seiner Adobe-Organisation und auf alle Umgebungen in jedem seiner Programme angewendet. Sie gilt sowohl für Autoren- als auch für Veröffentlichungs-Services.

Es werden nur HTTP- und HTTPS-Ports unterstützt. Dazu gehören HTTP/1.1 und HTTP/2 bei Verschlüsselung.

### Überlegungen zum Debugging {#debugging-considerations}

Um zu überprüfen, ob der Traffic tatsächlich über die erwartete dedizierte IP-Adresse ausgeht, überprüfen Sie die Protokolle im Ziel-Service, sofern verfügbar. Andernfalls kann es nützlich sein, einen Debugging-Service wie [https://ifconfig.me/IP](https://ifconfig.me/IP) aufzurufen, der die aufrufende IP-Adresse zurückgibt.

## Virtuelles privates Netzwerk (VPN) {#vpn}

VPN ermöglicht die Verbindung zu einer On-Premise-Infrastruktur oder einem Rechenzentrum von der Autoren-, Veröffentlichungs- oder Vorschau-Instanz aus. Beispielsweise für die Mittel zum Zugriff auf eine Datenbank.

Es ermöglicht auch die Verbindung zu SaaS-Anbietern, wie z. B. einem CRM-Anbieter, der VPN unterstützt oder eine Verbindung von einem Unternehmensnetzwerk mit AEM as a Cloud Service Autoren-, Vorschau- oder Veröffentlichungsinstanzen herstellt.

Die meisten VPN-Geräte mit IPSec-Technologie werden unterstützt. Schauen Sie sich die Liste der Geräte auf [dieser Seite](https://docs.microsoft.com/de-de/azure/vpn-gateway/vpn-gateway-about-vpn-devices#devicetable) an, die auf den Informationen in der Spalte **RouteBased configuration instructions** basiert. Konfigurieren Sie das Gerät wie in der Tabelle beschrieben.

### Allgemeine Überlegungen: {#general-vpn-considerations}

* Unterstützung ist auf eine einzelne VPN-Verbindung beschränkt
* Die Splunk-Weiterleitungsfunktion ist über eine VPN-Verbindung nicht möglich.

### Kreation {#vpn-creation}

Einmal pro Programm wird der Endpunkt POST `/program/<programId>/networkInfrastructures` aufgerufen, wobei eine Payload mit Konfigurationsinformationen übergeben wird, darunter: der Wert von „vpn“ für den Parameter `kind`, Region, Adressraum (Liste der CIDRs – beachten Sie, dass dies später nicht geändert werden kann), DNS-Resolver (für die Auflösung von Namen im Kundennetz) und VPN-Verbindungsinformationen wie Gateway-Konfiguration, gemeinsamer VPN-Schlüssel und die IP-Sicherheitsrichtlinie. Der Endpunkt antwortet mit der `network_id` sowie anderen Informationen, einschließlich des Status. Der vollständige Satz von Parametern und die genaue Syntax sind in der [API-Dokumentation](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure) zu finden.

Nach dem Aufruf dauert es in der Regel zwischen 45 und 60 Minuten, bis die Netzwerkinfrastruktur bereitgestellt wird. Die GET-Methode der API kann aufgerufen werden, um den aktuellen Status zurückzugeben, der schließlich von `creating` zu `ready` wechselt. In der API-Dokumentation finden Sie alle Status.

Wenn die Konfiguration der VPN-Konfiguration für das Programm fertig ist, muss der `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking`-Endpunkt pro Umgebung aufgerufen werden, um die Vernetzung auf Umgebungsebene zu aktivieren und alle Regeln für die Portweiterleitung zu deklarieren. Parameter können je Umgebung konfiguriert werden, um Flexibilität zu bieten.

Weitere Informationen finden Sie in der [API-Dokumentation](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/enableEnvironmentAdvancedNetworkingConfiguration).

Regeln für die Port-Weiterleitung sollten für jeden TCP-Traffic, der nicht HTTP/s-Protokoll ist und über das VPN geleitet werden soll, deklariert werden, indem der Satz von Ziel-Hosts (Namen oder IP und Ports) angegeben wird. Für jeden Ziel-Host müssen Kunden den beabsichtigten Ziel-Port einem Port von 30000 bis 30999 zuordnen, wobei die Werte in allen Umgebungen im Programm eindeutig sein müssen. Kunden können auch eine Reihe von URLs im `nonProxyHosts`-Parameter auflisten, die angeben, dass der Traffic nicht über das VPN-Routing, sondern über einen gemeinsamen IP-Bereich laufen soll. Es folgt den Mustern von `example.com` oder `*.example.com`, wobei der Platzhalter nur am Beginn der Domain unterstützt wird.

Die API sollte innerhalb weniger Sekunden mit dem Status `updating` antworten, und nach etwa 10 Minuten würde ein Aufruf des GET-Endpunkts für die Umgebung des Cloud Managers den Status `ready` anzeigen, was bedeutet, dass die Aktualisierung der Umgebung durchgeführt wurde.

Beachten Sie, dass `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` auch dann aufgerufen werden muss, wenn es keine Regeln für die Weiterleitung des Umgebungs-Traffics (Hosts oder Bypässe) gibt, nur mit einer leeren Payload.

### VPN aktualisieren {#updating-the-vpn}

Die VPN-Konfiguration auf Programmebene kann durch Aufrufen des `PUT /api/program/<program_id>/network/<network_id>`-Endpunkts aktualisiert werden.

Beachten Sie, dass der Adressraum nach der ersten VPN-Bereitstellung nicht mehr geändert werden kann. Wenden Sie sich bei Bedarf an den Support. Darüber hinaus kann der `kind`-Parameter (`flexiblePortEgress`, `dedicatedEgressIP` oder `VPN`) nicht geändert werden. Wenn Sie Unterstützung benötigen, wenden Sie sich an den Support und beschreiben Sie, was bereits erstellt wurde und warum Sie die Änderung vornehmen möchten.

Die Routing-Regeln für die einzelnen Umgebungen können durch erneutes Aufrufen des `PUT /program/{programId}/environment/{environmentId}/advancedNetworking`-Endpunkts aktualisiert werden, wobei darauf zu achten ist, dass der gesamte Satz an Konfigurationsparametern und nicht nur eine Teilmenge angegeben wird. Die Übernahme von Umgebungsaktualisierungen dauert in der Regel 5–10 Minuten.

### VPN löschen oder deaktivieren {#deleting-or-disabling-the-vpn}

Um die Netzwerkinfrastruktur zu löschen, senden Sie ein Support-Ticket, in dem beschrieben wird, was erstellt wurde und warum sie gelöscht werden muss.

Um VPN für eine bestimmte Umgebung zu deaktivieren, rufen Sie `DELETE /program/{programId}/environment/{environmentId}/advancedNetworking` auf. Weitere Informationen finden Sie in der [API-Dokumentation](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration).

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
    <td><code>10.0.0.1:443</code>Es kann auch ein Hostname sein.</td>
  </tr>
  <tr>
    <td></td>
    <td>Wenn die IP nicht in den <i>Adressbereich des VPN-Gateways</i> fällt, durch die HTTP-Proxy-Konfiguration (standardmäßig für den HTTP/s-Traffic mit der standardmäßigen Java-HTTP-Client-Bibliothek konfiguriert)</td>
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
    <td><code>10.0.0.1:3306</code>Es kann auch ein Hostname sein.</td>
  </tr>
  <tr>
    <td></td>
    <td>Wenn die IP nicht in den <i>Adressbereich des VPN-Gateways</i> fällt und der Client sich mithilfe einer <code>portOrig</code>, die im API-Parameter <code>portForwards</code> deklariert wurde, mit der <code>AEM_PROXY_HOST</code>-Umgebungs-Variable verbindet</td>
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

### Nützliche Domains für die Konfiguration{#vpn-useful-domains-for-configuration}

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
    <td><code>p{PROGRAM_ID}-gateway.external.adobeaemcloud.com</code></td>
    <td>Nicht zutreffend</td>
    <td>Die IP des VPN-Gateways auf der Seite von AEM. Das Netzwerk-Engineering-Team eines Kunden kann dies verwenden, um zu seinem VPN-Gateway von einer bestimmten IP-Adresse aus nur VPN-Verbindungen zuzulassen. </td>
  </tr>
  <tr>
    <td><code>p{PROGRAM_ID}.inner.adobeaemcloud.net</code></td>
    <td>Die IP des Traffics kommt dabei von der AEM-Seite des VPN zur Kundenseite. Dies kann in der Kundenkonfiguration auf die Zulassungsliste gesetzt werden, um sicherzustellen, dass Verbindungen nur von AEM aus hergestellt werden können.</td>
    <td>Wenn der Kunde nur VPN-Zugriff auf AEM zulassen möchte, sollte er CNAME-DNS-Einträge konfigurieren, um <code>author-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code> und/oder <code>publish-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code> diesen zuzuordnen.</td>
  </tr>
</tbody>
</table>

### VPN auf eingehende Verbindungen beschränken {#restrict-vpn-to-ingress-connections}

Wenn Sie nur den VPN-Zugriff auf AEM zulassen möchten, können Umgebungszulassungslisten in Cloud Manager so konfiguriert werden, dass nur die durch `p{PROGRAM_ID}.external.adobeaemcloud.com` definierte IP mit der Umgebung kommunizieren darf. Dies kann auf dieselbe Weise wie bei jeder anderen IP-basierten Zulassungsliste in Cloud Manager erfolgen.

Wenn Regeln pfadbasiert sein müssen, verwenden Sie standardmäßige HTTP-Anweisungen auf Dispatcher-Ebene, um bestimmte IPs zu blockieren oder zuzulassen. Sie sollten sicherstellen, dass die gewünschten Pfade auch im CDN nicht zwischenspeicherbar sind, sodass die Anfrage immer an den Ursprung gelangt.

**Beispiel für httpd-Konfiguration**

```
Order deny,allow
Deny from all
Allow from 192.168.0.1
Header always set Cache-Control private
```

## Übergang zwischen Typen von erweiterten Netzwerken {#transitioning-between-advanced-networking-types}

Da der `kind`-Parameter nicht geändert werden kann, wenden Sie sich bitte an den Support und schildern Sie, was bereits erstellt wurde und warum Sie ihn ändern möchten.
