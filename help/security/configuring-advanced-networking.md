---
title: Erweiterte Netzwerke für AEM as a Cloud Service konfigurieren
description: Erfahren Sie, wie Sie erweiterte Netzwerkfunktionen wie VPN oder eine flexible oder dedizierte Ausgangs-IP-Adresse für AEM as a Cloud Service konfigurieren.
source-git-commit: 2f9ba938d31c289201785de24aca2d617ab9dfca
workflow-type: tm+mt
source-wordcount: '2836'
ht-degree: 8%

---


# Erweiterte Netzwerke für AEM as a Cloud Service konfigurieren {#configuring-advanced-networking}

Dieser Artikel soll Ihnen die verschiedenen erweiterten Netzwerkfunktionen in AEM as a Cloud Service vorstellen, einschließlich der Bereitstellung von VPN-Self-Service, nicht standardmäßigen Ports und dedizierten Ausgangs-IP-Adressen.

## Übersicht {#overview}

AEM as a Cloud Service bietet verschiedene Arten erweiterter Netzwerkfunktionen, die von Kunden mithilfe von Cloud Manager-APIs konfiguriert werden können. Dazu gehören:

* [Flexibles Port-Egress](#flexible-port-egress) - konfigurieren Sie AEM as a Cloud Service, um ausgehenden Traffic aus nicht standardmäßigen Ports zu ermöglichen.
* [Dedizierte Ausgangs-IP-Adresse](#dedicated-egress-IP-address) - Konfigurieren des Traffics aus AEM as a Cloud Service, der von einer eindeutigen IP stammt
* [Virtuelles privates Netzwerk (VPN)](#vpn) - sicheren Datenverkehr zwischen der Infrastruktur eines Kunden und AEM as a Cloud Service für Kunden mit VPN-Technologie

In diesem Artikel werden die einzelnen Optionen detailliert beschrieben, einschließlich ihrer Konfiguration. Als allgemeine Konfigurationsstrategie sollte die `/networkInfrastructures` Der API-Endpunkt wird auf Programmebene aufgerufen, um den gewünschten Typ von erweitertem Netzwerk zu deklarieren, gefolgt von einem Aufruf an die `/advancedNetworking` Endpunkt für jede Umgebung, um die Infrastruktur zu aktivieren und umgebungsspezifische Parameter zu konfigurieren. Referenzieren Sie die entsprechenden Endpunkte in der Dokumentation zur Cloud Manager-API für jede formale Syntax sowie Beispielanfragen und -antworten.

Ein Programm kann eine einzige erweiterte Netzwerkvariante bereitstellen. Bei der Entscheidung zwischen flexiblem Port-Ausgang und dedizierter Ausgangs-IP-Adresse wird empfohlen, einen flexiblen Port-Ausgang zu wählen, wenn keine bestimmte IP-Adresse erforderlich ist, da Adobe die Leistung des flexiblen Ausgangs-Traffics an Ports optimieren kann.

>[!INFO]
>
>Erweiterte Netzwerke sind für das Sandbox-Programm nicht verfügbar.
>Außerdem müssen Umgebungen auf AEM Version 5958 oder höher aktualisiert werden.

>[!NOTE]
>
>Kunden, die bereits über eine veraltete dedizierte Egress-Technologie verfügen und eine dieser Optionen konfigurieren müssen, sollten dies nicht tun, da dies sonst die Site-Konnektivität beeinträchtigt sein könnte. Wenden Sie sich für Unterstützung an den Support der Adobe.

## Flexibler Hafenausbau {#flexible-port-egress}

Mit dieser erweiterten Netzwerkfunktion können Sie AEM as a Cloud Service konfigurieren, um Traffic über andere standardmäßig geöffnete Ports als HTTP (Port 80) und HTTPS (Port 443) zu fördern.

### Zu beachten {#flexible-port-egress-considerations}

Eine flexible Port-Ausfahrt ist die empfohlene Wahl, wenn Sie kein VPN benötigen und keine dedizierte Ausgangs-IP-Adresse benötigen, da Traffic, der nicht auf ein dediziertes Egress angewiesen ist, einen höheren Durchsatz erzielen kann.

### Konfiguration {#configuring-flexible-port-egress-provision}

Einmal pro Programm, die POST `/program/<programId>/networkInfrastructures` Endpunkt wird aufgerufen und übergibt einfach den Wert von `flexiblePortEgress` für `kind` Parameter und Region. Der Endpunkt antwortet mit der `network_id`sowie andere Informationen, einschließlich des Status. Der vollständige Satz von Parametern und die genaue Syntax sollten in den API-Dokumenten referenziert werden.

Nach dem Aufruf dauert es in der Regel etwa 15 Minuten, bis die Netzwerkinfrastruktur bereitgestellt wird. Ein Aufruf an die Cloud Manager - [GET-Endpunkt der Netzwerkinfrastruktur](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getNetworkInfrastructure) würde den Status &quot;ready&quot;anzeigen.

Wenn die Konfiguration der flexiblen Port-Ausdrücke für das Programm bereit ist, wird die `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` -Endpunkt muss pro Umgebung aufgerufen werden, um die Vernetzung auf Umgebungsebene zu aktivieren und optional alle Regeln für die Anschlussweiterleitung zu deklarieren. Parameter können je Umgebung konfiguriert werden, um Flexibilität zu bieten.

Regeln für die Hafenweiterleitung sollten für alle anderen Ports als 80/443 deklariert werden, indem der Satz der Ziel-Hosts (Namen oder IP und mit Ports) angegeben wird. Für jeden Ziel-Host müssen Kunden den vorgesehenen Zielport einem Port von 30000 bis 30999 zuordnen.

Die API sollte in nur wenigen Sekunden reagieren und einen Aktualisierungsstatus angeben. Nach etwa 10 Minuten sollte der Endpunkt `GET` -Methode sollte anzeigen, dass die erweiterte Vernetzung aktiviert ist.

### Updates {#updating-flexible-port-egress-provision}

Die Konfiguration auf Programmebene kann aktualisiert werden, indem die `PUT /api/program/<program_id>/network/<network_id>` -Endpunkt gesetzt und wird innerhalb weniger Minuten wirksam.

>[!NOTE]
>
> Der Parameter &quot;type&quot;(`flexiblePortEgress`, `dedicatedEgressIP` oder `VPN`) kann nicht geändert werden. Wenden Sie sich an den Support, um Unterstützung zu erhalten, und beschreiben Sie, was bereits erstellt wurde und warum die Änderung vorgenommen wurde.

Die Regeln für die Port-Weiterleitung pro Umgebung können aktualisiert werden, indem Sie erneut die `PUT /program/{programId}/environment/{environmentId}/advancedNetworking` -Endpunkt und stellen Sie sicher, dass Sie den vollständigen Satz von Konfigurationsparametern und nicht eine Teilmenge einschließen.

### Löschen oder Deaktivieren des flexiblen Port-Fortschritts {#deleting-disabling-flexible-port-egress-provision}

Um **delete** Senden Sie ein Support-Ticket über die Netzwerkinfrastruktur, in dem beschrieben wird, was erstellt wurde und warum es gelöscht werden muss.

Um **disable** flexible Port-Auslösung aus einer bestimmten Umgebung, aufrufen `DELETE [/program/{programId}/environment/{environmentId}/advancedNetworking]()`.

Weitere Informationen finden Sie unter [Dokumentation zur Cloud Manager-API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration).

### Traffic-Routing {#flexible-port-egress-traffic-routing}

HTTP- oder HTTPS-Traffic, der über die Ports 80 oder 443 an Ziele geleitet wird, durchläuft einen vorkonfigurierten Proxy, vorausgesetzt, die standardmäßige Java-Netzwerkbibliothek wird verwendet. Für HTTP- oder HTTPS-Traffic, der über andere Ports erfolgt, sollte ein Proxy mit den folgenden Eigenschaften konfiguriert werden.

* `AEM_HTTP_PROXY_HOST / AEM_HTTPS_PROXY_HOST`
* `AEM_HTTP_PROXY_PORT / AEM_HTTPS_PROXY_PORT`

Hier finden Sie beispielsweise Beispielcode zum Senden einer Anfrage an `www.example.com:8443`:

```java
String url = "www.example.com:8443"
var proxyHost = System.getenv("AEM_HTTPS_PROXY_HOST");
var proxyPort = Integer.parseInt(System.getenv("AEM_HTTPS_PROXY_PORT"));
HttpClient client = HttpClient.newBuilder()
      .proxy(ProxySelector.of(new InetSocketAddress(proxyHost, proxyPort)))
      .build();
 
HttpRequest request = HttpRequest.newBuilder().uri(URI.create(url)).build();
HttpResponse<String> response = client.send(request, BodyHandlers.ofString());
```

Wenn Sie nicht standardmäßige Java-Netzwerkbibliotheken verwenden, konfigurieren Sie Proxys für den gesamten Traffic mithilfe der oben genannten Eigenschaften.

Nicht-HTTP/s-Traffic mit Zielen über Häfen, die im `portForwards` -Parameter sollte auf eine Eigenschaft mit der Bezeichnung `AEM_PROXY_HOST`, zusammen mit dem zugeordneten Port. Beispiel:

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
    <th>Beispiel</th>
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
    <td>Nicht standardmäßiger Traffic (an anderen Ports außerhalb von 80 oder 443) über HTTP-Proxy, der mit diesen Umgebungsvariablen konfiguriert wurde:<br><ul>
     <li>AEM_HTTP_PROXY_HOST / AEM_HTTPS_PROXY_HOST</li>
     <li>AEM_HTTP_PROXY_PORT / AEM_HTTPS_PROXY_PORT</li>
    </ul>
    <td>Ports außerhalb 80 oder 443</td>
    <td>Zugelassen</td>
  </tr>
  <tr>
    <td></td>
    <td>Nicht standardmäßiger Traffic (an anderen Ports außerhalb der Ports 80 oder 443), der nicht HTTP-Proxy verwendet</td>
    <td>Ports außerhalb 80 oder 443</td>
    <td>Blockiert</td>
    <td></td>
  </tr>
  <tr>
    <td><b>Nicht-HTTP oder Nicht-HTTPS</b></td>
    <td>Der Client stellt eine Verbindung zum <code>AEM_PROXY_HOST</code> Umgebungsvariable mithilfe einer <code>portOrig</code> im <code>portForwards</code> API-Parameter.</td>
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

Die Apache-/Dispatcher-Ebene von AEM Cloud Service `mod_proxy` -Anweisung kann mit den oben beschriebenen Eigenschaften konfiguriert werden.

```
ProxyRemote "http://example.com" "http://${AEM_HTTP_PROXY_HOST}:${AEM_HTTP_PROXY_PORT}"
ProxyPass "/somepath" "http://example.com"
ProxyPassReverse "/somepath" "http://example.com"
```

```
SSLProxyEngine on //needed for https backends
 
ProxyRemote "https://example.com:8443" "http://${AEM_HTTPS_PROXY_HOST}:${AEM_HTTPS_PROXY_PORT}"
ProxyPass "/somepath" "https://example.com:8443"
ProxyPassReverse "/somepath" "https://example.com:8443"
```

## Dedizierte Ausgangs-IP-Adresse {#dedicated-egress-IP-address}

>[!NOTE]
>
>Wenn Sie vor der Version vom September 2021 über eine dedizierte Ausgangs-IP verfügen (06.10.21), lesen Sie bitte den Abschnitt [Alte dedizierte Egress-Adresskunden](#legacy-dedicated-egress-address-customers).

### Vorteile {#benefits}

Diese dedizierte IP-Adresse kann die Sicherheit bei der Integration mit SaaS-Anbietern (wie z. B. einem CRM-Anbieter) oder anderen Integrationen außerhalb von AEM as a Cloud Service, die eine Zulassungsliste von IP-Adressen anbieten, erhöhen. Durch Hinzufügen der dedizierten IP-Adresse zur Zulassungsliste wird sichergestellt, dass nur der Traffic aus der AEM Cloud Service des Kunden in den externen Dienst fließen darf. Dies geschieht zusätzlich zum Traffic von allen anderen zulässigen IPs.

Wenn die Funktion der dedizierten IP-Adresse nicht aktiviert ist, fließt der Traffic von AEM as a Cloud Service über eine Reihe von IPs, die mit anderen Kunden gemeinsam genutzt werden.

### Konfiguration {#configuring-dedicated-egress-provision}

>[!INFO]
>
>Die Splunk-Weiterleitungsfunktion ist über eine dedizierte Ausgangs-IP-Adresse nicht möglich.

Die Konfiguration der dedizierten Ausgangs-IP-Adresse ist mit dem Szenario [flexibler Port-Ausgang](#configuring-flexible-port-egress-provision).

Der Hauptunterschied besteht darin, dass der Traffic immer von einer dedizierten, eindeutigen IP-Adresse ausgeht. Um diese IP zu finden, verwenden Sie einen DNS-Resolver, um die IP-Adresse zu identifizieren, die mit `p{PROGRAM_ID}.external.adobeaemcloud.com`. Es wird nicht erwartet, dass sich die IP-Adresse ändert. Sollte sich die IP jedoch in Zukunft ändern, wird eine erweiterte Benachrichtigung bereitgestellt.

Zusätzlich zu den Routing-Regeln, die von flexiblen Port-Ausgängen im `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` Endpunkt: Die dedizierte Ausgangs-IP-Adresse unterstützt eine `nonProxyHosts` Parameter. Auf diese Weise können Sie eine Gruppe von Hosts deklarieren, die über einen gemeinsamen IP-Adressbereich statt über die dedizierte IP weitergeleitet werden sollen. Dies kann nützlich sein, da das Traffic-egressing über freigegebene IPs weiter optimiert werden kann. Die `nonProxyHost` URLs können dem Muster von `example.com` oder `*.example.com`, wobei der Platzhalter nur zu Beginn der Domäne unterstützt wird.

Bei der Entscheidung zwischen flexiblem Port-Ausgang und dedizierter Ausgangs-IP-Adresse sollten Kunden eine flexible Port-Ausfahrt wählen, wenn keine bestimmte IP-Adresse erforderlich ist, da Adobe die Leistung des flexiblen Ausgangs-Traffics an Ports optimieren kann.

### Traffic-Routing {#dedcated-egress-ip-traffic-routing}

<table>
<thead>
  <tr>
    <th>Traffic</th>
    <th>Zielbedingung</th>
    <th>Port</th>
    <th>Verbindung</th>
    <th>Beispiel</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>HTTP- oder HTTPS-Protokoll</b></td>
    <td>Traffic zu Azure- oder Adobe-Diensten</td>
    <td>Alle</td>
    <td>Über die freigegebenen Cluster-IPs (nicht die dedizierte IP)</td>
    <td>adobe.io<br>api.windows.net</td>
  </tr>
  <tr>
    <td></td>
    <td>Host, der mit dem <code>nonProxyHosts</code> parameter</td>
    <td>80 oder 443</td>
    <td>Über die freigegebenen Cluster-IPs</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Host, der mit dem <code>nonProxyHosts</code> parameter</td>
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
    <td>Ignoriert die HTTP-Proxy-Konfiguration (z. B. wenn diese explizit aus der standardmäßigen Java-HTTP-Client-Bibliothek entfernt wurde oder wenn eine Java-Bibliothek verwendet wird, die die standardmäßige Proxy-Konfiguration ignoriert)</td>
    <td>80 oder 443</td>
    <td>Über die freigegebenen Cluster-IPs</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Ignoriert die HTTP-Proxy-Konfiguration (z. B. wenn diese explizit aus der standardmäßigen Java-HTTP-Client-Bibliothek entfernt wurde oder wenn eine Java-Bibliothek verwendet wird, die die standardmäßige Proxy-Konfiguration ignoriert)</td>
    <td>Ports außerhalb 80 oder 443</td>
    <td>Blockiert</td>
    <td></td>
  </tr>
  <tr>
    <td><b>Nicht-HTTP oder Nicht-HTTPS</b></td>
    <td>Der Client stellt eine Verbindung zu <code>AEM_PROXY_HOST</code> env -Variable mithilfe einer <code>portOrig</code> im <code>portForwards</code> API-Parameter</td>
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

## Alte dedizierte Egress-Adresskunden {#legacy-dedicated-egress-address-customers}

Wenn Sie vor 2021.09.30 über eine dedizierte Ausgangs-IP verfügen, funktioniert Ihre dedizierte Ausgangs-IP-Funktion wie unten beschrieben.

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

Beispiel für die Verwendung von Apache HttpClient, für das explizite Aufrufe von
[`HttpClientBuilder.useSystemProperties()`](https://hc.apache.org/httpcomponents-client-4.5.x/current/httpclient/apidocs/org/apache/http/impl/client/HttpClientBuilder.html) oder Verwendung
[`HttpClients.createSystem()`](https://hc.apache.org/httpcomponents-client-4.5.x/current/httpclient/apidocs/org/apache/http/impl/client/HttpClients.html#createSystem()):

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

Um zu überprüfen, ob der Traffic tatsächlich über die erwartete dedizierte IP-Adresse ausgeht, überprüfen Sie die Protokolle im Ziel-Service, sofern verfügbar. Andernfalls kann es nützlich sein, einen Debugging-Dienst wie [https://ifconfig.me/IP](https://ifconfig.me/IP), wodurch die aufrufende IP-Adresse zurückgegeben wird.

## Virtuelles privates Netzwerk (VPN) {#vpn}

VPN ermöglicht die Verbindung zu einer On-Premise-Infrastruktur oder einem Datenzentrum von der Autoren-, Veröffentlichungs- oder Vorschau aus. Beispielsweise für die Mittel zum Zugriff auf eine Datenbank.

Es ermöglicht auch die Verbindung zu SaaS-Anbietern, wie z. B. einem CRM-Anbieter, der VPN unterstützt oder eine Verbindung von einem Unternehmensnetzwerk mit AEM as a Cloud Service Autoren-, Vorschau- oder Veröffentlichungsinstanz herstellt.

Die meisten VPN-Geräte mit IPSec-Technologie werden unterstützt. Sehen Sie sich die Liste der Geräte an unter [diese Seite](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpn-devices#devicetable)auf der Grundlage der Informationen in der **RouteBased-Konfigurationsanweisungen** Spalte. Konfigurieren Sie das Gerät wie in der Tabelle beschrieben.

### Allgemeine Überlegungen: {#general-vpn-considerations}

* Unterstützung ist auf eine einzelne VPN-Verbindung beschränkt
* Die Splunk-Weiterleitungsfunktion ist über eine VPN-Verbindung nicht möglich.

### Kreation {#vpn-creation}

Einmal pro Programm, die POST `/program/<programId>/networkInfrastructures` Endpunkt wird aufgerufen und übergibt eine Payload mit Konfigurationsinformationen, darunter: der Wert von &quot;vpn&quot;für die `kind` Parameter, Region, Adressraum (Liste der CIDRs - dies kann später nicht geändert werden), DNS-Resolver (zur Namensauflösung im Netzwerk des Kunden) und VPN-Verbindungsinformationen wie Gateway-Konfiguration, freigegebener VPN-Schlüssel und IP-Sicherheitsrichtlinie. Der Endpunkt antwortet mit der `network_id`sowie andere Informationen, einschließlich des Status. Der vollständige Satz von Parametern und die genaue Syntax sollten im Abschnitt [API-Dokumentation](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure).

Nach dem Aufruf dauert es in der Regel zwischen 45 und 60 Minuten, bis die Netzwerkinfrastruktur bereitgestellt wird. Die GET-Methode der API kann aufgerufen werden, um den aktuellen Status zurückzugeben, der schließlich von `creating` nach `ready`. In der API-Dokumentation finden Sie alle Status.

Wenn die programmgesteuerte VPN-Konfiguration fertig ist, wird die `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` -Endpunkt muss pro Umgebung aufgerufen werden, um die Vernetzung auf Umgebungsebene zu ermöglichen und um alle Regeln für die Weiterleitung von Ports zu deklarieren. Parameter können je Umgebung konfiguriert werden, um Flexibilität zu bieten.

Siehe [API-Dokumentation](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/enableEnvironmentAdvancedNetworkingConfiguration) für weitere Informationen.

Regeln für die Port-Weiterleitung sollten für jeden TCP-Traffic, der nicht HTTP/s-Protokoll ist und über das VPN geleitet werden soll, deklariert werden, indem der Satz von Ziel-Hosts (Namen oder IP und Ports) angegeben wird. Für jeden Ziel-Host müssen Kunden den beabsichtigten Ziel-Port einem Port von 30000 bis 30999 zuordnen, wobei die Werte in allen Umgebungen im Programm eindeutig sein müssen. Kunden können auch eine Reihe von URLs im `nonProxyHosts` -Parameter, der die URL angibt, für die der Traffic das VPN-Routing umgehen soll, sondern stattdessen über einen freigegebenen IP-Bereich. Es folgt den Mustern von `example.com` oder `*.example.com`, wobei der Platzhalter nur zu Beginn der Domäne unterstützt wird.

Die API sollte in nur wenigen Sekunden reagieren und den Status `updating` und nach etwa 10 Minuten zeigt ein Aufruf des Umgebungs-GET von Cloud Manager den Status `ready`, um anzugeben, dass die Aktualisierung der Umgebung durchgeführt wurde.

Beachten Sie, dass auch dann, wenn es keine Regeln für das Traffic-Routing der Umgebung (Hosts oder Umgehungen) gibt, `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` muss weiterhin aufgerufen werden, nur mit einer leeren Payload.

### VPN aktualisieren {#updating-the-vpn}

Die VPN-Konfiguration auf Programmebene kann aktualisiert werden, indem die `PUT /api/program/<program_id>/network/<network_id>` -Endpunkt.

Beachten Sie, dass der Adressraum nach der ersten VPN-Bereitstellung nicht mehr geändert werden kann. Wenden Sie sich bei Bedarf an den Support. Darüber hinaus wird die `kind` Parameter (`flexiblePortEgress`, `dedicatedEgressIP` oder `VPN`) kann nicht geändert werden. Wenden Sie sich an den Support, um Unterstützung zu erhalten, und beschreiben Sie, was bereits erstellt wurde und warum die Änderung vorgenommen wurde.

Die Routing-Regeln pro Umgebung können aktualisiert werden, indem Sie erneut die `PUT /program/{programId}/environment/{environmentId}/advancedNetworking` -Endpunkt und stellen Sie sicher, dass Sie den vollständigen Satz von Konfigurationsparametern und nicht eine Teilmenge einschließen. Die Anwendung von Umgebungsaktualisierungen dauert in der Regel 5-10 Minuten.

### VPN löschen oder deaktivieren {#deleting-or-disabling-the-vpn}

Um die Netzwerkinfrastruktur zu löschen, senden Sie ein Support-Ticket, in dem beschrieben wird, was erstellt wurde und warum es gelöscht werden muss.

Um VPN für eine bestimmte Umgebung zu deaktivieren, rufen Sie auf `DELETE /program/{programId}/environment/{environmentId}/advancedNetworking`. Weitere Informationen finden Sie unter [API-Dokumentation](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration).

### Traffic-Routing {#vpn-traffic-routing}

In der folgenden Tabelle wird das Traffic-Routing beschrieben.

<table>
<thead>
  <tr>
    <th>Traffic</th>
    <th>Zielbedingung</th>
    <th>Port</th>
    <th>Verbindung</th>
    <th>Beispiel</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><b>HTTP- oder HTTPS-Protokoll</b></td>
    <td>Traffic zu Azure- oder Adobe-Diensten</td>
    <td>Alle</td>
    <td>Über die freigegebenen Cluster-IPs (nicht die dedizierte IP)</td>
    <td>adobe.io<br>api.windows.net</td>
  </tr>
  <tr>
    <td></td>
    <td>Host, der mit dem <code>nonProxyHosts</code> parameter</td>
    <td>80 oder 443</td>
    <td>Über die freigegebenen Cluster-IPs</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Host, der mit dem <code>nonProxyHosts</code> parameter</td>
    <td>Ports außerhalb 80 oder 443</td>
    <td>Blockiert</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Wenn die IP in die <i>VPN-Gateway-Adresse</i> Platzierungsbereich und über die HTTP-Proxy-Konfiguration (standardmäßig für HTTP/s-Traffic mit der standardmäßigen Java-HTTP-Client-Bibliothek konfiguriert)</td>
    <td>Alle</td>
    <td>Über VPN</td>
    <td><code>10.0.0.1:443</code>Es kann auch ein Hostname sein.</td>
  </tr>
  <tr>
    <td></td>
    <td>Wenn die IP nicht in die <i>VPN-Gateway-Adressraum</i> Bereich und über die HTTP-Proxy-Konfiguration (standardmäßig für den HTTP/s-Traffic mit der standardmäßigen Java-HTTP-Client-Bibliothek konfiguriert)</td>
    <td>Alle</td>
    <td>Über die dedizierte Ausgangs-IP</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Ignoriert die HTTP-Proxy-Konfiguration (z. B. wenn diese explizit aus der standardmäßigen Java-HTTP-Client-Bibliothek entfernt wurde oder wenn Java-Bibliothek verwendet wird, die die standardmäßige Proxy-Konfiguration ignoriert)
</td>
    <td>80 oder 443</td>
    <td>Über die freigegebenen Cluster-IPs</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Ignoriert die HTTP-Proxy-Konfiguration (z. B. wenn diese explizit aus der standardmäßigen Java-HTTP-Client-Bibliothek entfernt wurde oder wenn Java-Bibliothek verwendet wird, die die standardmäßige Proxy-Konfiguration ignoriert)</td>
    <td>Ports außerhalb 80 oder 443</td>
    <td>Blockiert</td>
    <td></td>
  </tr>
  <tr>
    <td><b>Nicht-HTTP oder Nicht-HTTPS</b></td>
    <td>Wenn die IP in die <i>VPN-Gateway-Adressraum</i> Bereich und Client verbindet sich mit <code>AEM_PROXY_HOST</code> env -Variable mithilfe einer <code>portOrig</code> im <code>portForwards</code> API-Parameter</td>
    <td>Alle</td>
    <td>Über VPN</td>
    <td><code>10.0.0.1:3306</code>Es kann auch ein Hostname sein.</td>
  </tr>
  <tr>
    <td></td>
    <td>Wenn die IP nicht in die <i>VPN-Gateway-Adressraum</i> Bereich- und Client-Verbindungen <code>AEM_PROXY_HOST</code> env -Variable mithilfe einer <code>portOrig</code> im <code>portForwards</code> API-Parameter</td>
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

### Nützliche Domänen für die Konfiguration{#vpn-useful-domains-for-configuration}

Das folgende Diagramm zeigt eine visuelle Darstellung einer Reihe von Domänen und zugehörigen IPs, die für die Konfiguration und Entwicklung nützlich sind. Die Tabelle weiter unten im Diagramm beschreibt diese Domänen und IPs.

![VPN-Domänenkonfiguration](/help/security/assets/AdvancedNetworking.jpg)

<table>
<thead>
  <tr>
    <th>Domänenmuster</th>
    <th>Ausgang (aus AEM) Bedeutung</th>
    <th>Eingang (AEM) Bedeutung</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><code>p{PROGRAM_ID}.external.adobeaemcloud.com</code></td>
    <td>Dedizierte Ausgangs-IP-Adresse für Traffic, der zum Internet statt über private Netzwerke geleitet wird </td>
    <td>Verbindungen des VPN würden beim CDN als von dieser IP kommend angezeigt. Um nur Verbindungen vom VPN in AEM zulassen, konfigurieren Sie Cloud Manager so, dass nur diese IP zugelassen und alles andere blockiert wird. Weitere Informationen finden Sie im Abschnitt "Eingänge zu VPN-Verbindungen beschränken".</td>
  </tr>
  <tr>
    <td><code>p{PROGRAM_ID}-gateway.external.adobeaemcloud.com</code></td>
    <td>Nicht zutreffend</td>
    <td>Die IP des VPN-Gateways auf der AEM. Das Netzwerk-Engineering-Team eines Kunden kann dies verwenden, um nur VPN-Verbindungen zu seinem VPN-Gateway von einer bestimmten IP-Adresse aus zuzulassen. </td>
  </tr>
  <tr>
    <td><code>p{PROGRAM_ID}.inner.adobeaemcloud.net</code></td>
    <td>Die IP des Traffics von der AEM Seite des VPN zur Kundenseite. Dies kann in der Kundenkonfiguration auf die Zulassungsliste gesetzt werden, um sicherzustellen, dass Verbindungen nur von AEM aus hergestellt werden können.</td>
    <td>Wenn der Kunde nur VPN-Zugriff auf AEM zulassen möchte, sollte er CNAME-DNS-Einträge für die Zuordnung konfigurieren <code>author-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code>  und/oder <code>publish-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code> zu diesem Zweck.</td>
  </tr>
</tbody>
</table>

### VPN auf eingehende Verbindungen beschränken {#restrict-vpn-to-ingress-connections}

Wenn Sie nur VPN-Zugriff auf AEM zulassen möchten, können die Umgebungsauf die Zulassungsliste setzte in Cloud Manager so konfiguriert werden, dass nur die von `p{PROGRAM_ID}.external.adobeaemcloud.com` darf mit der Umgebung reden. Dies kann auf dieselbe Weise wie jede andere IP-basierte Zulassungsliste in Cloud Manager erfolgen.

Wenn Regeln pfadbasiert sein müssen, verwenden Sie standardmäßige HTTP-Anweisungen auf Dispatcher-Ebene, um bestimmte IPs zu verweigern oder zuzulassen. Sie sollten sicherstellen, dass die gewünschten Pfade auch im CDN nicht zwischenspeicherbar sind, sodass die Anfrage immer an den Ursprung gelangt.

**Beispiel für Httpd-Konfiguration**

```
Order deny,allow
Deny from all
Allow from 192.168.0.1
Header always set Cache-Control private
```

## Übergang zwischen fortgeschrittenen Netzwerktypen {#transitioning-between-advanced-networking-types}

Seit `kind` -Parameter kann nicht geändert werden. Wenden Sie sich an den Support, um Hilfe zu erhalten, und beschreiben Sie, was bereits erstellt wurde und warum die Änderung vorgenommen wurde.
