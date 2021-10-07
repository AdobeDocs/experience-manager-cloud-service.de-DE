---
title: Erweiterte Netzwerke für AEM as a Cloud Service konfigurieren
description: Erfahren Sie, wie Sie erweiterte Netzwerkfunktionen wie VPN oder eine dedizierte Ausgangs-IP-Adresse für AEM as a Cloud Service konfigurieren.
source-git-commit: d37193833d784f3f470780b8f28e53b473fd4e10
workflow-type: tm+mt
source-wordcount: '2797'
ht-degree: 8%

---


# Erweiterte Netzwerke für AEM as a Cloud Service konfigurieren {#configuring-advanced-networking}

>[!INFO]
>
>Die Funktion für erweiterte Netzwerke ist Teil der Version 2021.9.0 und wird Mitte Oktober für Kunden aktiviert.

AEM as a Cloud Service bietet verschiedene Arten erweiterter Netzwerkfunktionen, die von Kunden mithilfe von Cloud Manager-APIs konfiguriert werden können. Dazu gehören:

* [Flexibler Port-Ausgang](#flexible-port-egress)  - Konfigurieren Sie AEM as a Cloud Service, um ausgehenden Traffic aus nicht standardmäßigen Ports zu ermöglichen.
* [Dedizierte Ausgangs-IP-Adresse](#dedicated-egress-IP-address) : Konfigurieren Sie den Traffic aus AEM as a Cloud Service, um von einer eindeutigen IP zu stammen
* [Virtuelles privates Netzwerk](#vpn)  - sicherer Datenverkehr zwischen der Infrastruktur eines Kunden und AEM as a Cloud Service für Kunden mit VPN-Technologie

In diesem Artikel werden die einzelnen Optionen detailliert beschrieben, einschließlich ihrer Konfiguration. Als allgemeine Konfigurationsstrategie wird der API-Endpunkt `/networkInfrastructures` auf Programmebene aufgerufen, um den gewünschten Typ von erweitertem Netzwerk zu deklarieren, gefolgt von einem Aufruf des Endpunkts `/advancedNetworking` für jede Umgebung, um die Infrastruktur zu aktivieren und umgebungsspezifische Parameter zu konfigurieren. Referenzieren Sie die entsprechenden Endpunkte in der Dokumentation zur Cloud Manager-API für jede formale Syntax sowie Beispielanfragen und -antworten.

Bei der Entscheidung zwischen flexiblem Port-Ausgang und dedizierter Ausgangs-IP-Adresse wird empfohlen, einen flexiblen Port-Ausgang zu wählen, wenn keine bestimmte IP-Adresse erforderlich ist, da Adobe die Leistung des flexiblen Ausgangs-Traffics an Ports optimieren kann.

>[!INFO]
>
>Erweiterte Netzwerke sind für das Sandbox-Programm nicht verfügbar.

>[!NOTE]
>
>Kunden, die bereits über eine veraltete dedizierte Egress-Technologie verfügen und eine dieser Optionen konfigurieren müssen, sollten dies nicht tun, da dies sonst die Site-Konnektivität beeinträchtigt sein könnte. Wenden Sie sich für Unterstützung an den Support der Adobe.

## Flexibler Hafenausbau {#flexible-port-egress}

Mit dieser erweiterten Netzwerkfunktion können Sie AEM as a Cloud Service konfigurieren, um Traffic über andere standardmäßig geöffnete Ports als HTTP (Port 80) und HTTPS (Port 443) zu fördern.

### Aspekte {#flexible-port-egress-considerations}

Eine flexible Port-Ausfahrt ist die empfohlene Wahl, wenn Sie kein VPN benötigen und keine dedizierte Ausgangs-IP-Adresse benötigen, da Traffic, der nicht auf ein dediziertes Egress angewiesen ist, einen höheren Durchsatz erzielen kann.

### Konfiguration {#configuring-flexible-port-egress-provision}

Einmal pro Programm wird der Endpunkt der POST `/program/<programId>/networkInfrastructures` aufgerufen und der Wert `flexiblePortEgress` für den Parameter und die Region `kind` wird einfach übergeben. Der Endpunkt antwortet mit `network_id` sowie anderen Informationen, einschließlich des Status. Der vollständige Satz von Parametern und die genaue Syntax sollten in den API-Dokumenten referenziert werden.

Nach dem Aufruf dauert es in der Regel etwa 15 Minuten, bis die Netzwerkinfrastruktur bereitgestellt wird. Bei einem Aufruf des [Umgebungs-GET-Endpunkts](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getEnvironment) von Cloud Manager wird der Status &quot;ready&quot;angezeigt.

Wenn die Konfiguration für den programmgesteuerten flexiblen Port-Ausgang fertig ist, muss der `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking`-Endpunkt pro Umgebung aufgerufen werden, um die Vernetzung auf Umgebungsebene zu ermöglichen und um alle Regeln für die Anschlussweiterleitung zu deklarieren. Parameter können je Umgebung konfiguriert werden, um Flexibilität zu bieten.

Regeln für die Hafenweiterleitung sollten für alle anderen Ports als 80/443 deklariert werden, indem der Satz der Ziel-Hosts (Namen oder IP und mit Ports) angegeben wird. Für jeden Ziel-Host müssen Kunden den vorgesehenen Zielport einem Port von 30000 bis 30999 zuordnen.

Die API sollte in nur wenigen Sekunden reagieren und einen Aktualisierungsstatus anzeigen. Nach etwa 10 Minuten sollte die `GET`-Methode des Endpunkts darauf hinweisen, dass erweiterte Netzwerke aktiviert sind.

### Updates {#updating-flexible-port-egress-provision}

Die Konfiguration auf Programmebene kann durch Aufrufen des Endpunkts `PUT /api/program/<program_id>/network/<network_id>` aktualisiert werden und wird innerhalb weniger Minuten wirksam.

>[!NOTE]
>
> Der &quot;type&quot;-Parameter (`flexiblePortEgress`, `dedicatedEgressIP` oder `VPN`) kann nicht geändert werden. Wenden Sie sich an den Support, um Unterstützung zu erhalten, und beschreiben Sie, was bereits erstellt wurde und warum die Änderung vorgenommen wurde.

Die Regeln für die Anschlussweiterleitung pro Umgebung können aktualisiert werden, indem Sie den Endpunkt `PUT /program/{programId}/environment/{environmentId}/advancedNetworking` erneut aufrufen. Stellen Sie dabei sicher, dass Sie den vollständigen Satz an Konfigurationsparametern und nicht eine Teilmenge einschließen.

### Löschen oder Deaktivieren des flexiblen Port-Fortschritts {#deleting-disabling-flexible-port-egress-provision}

Um **die Netzwerkinfrastruktur zu löschen, senden Sie ein Support-Ticket, in dem beschrieben wird, was erstellt wurde und warum es gelöscht werden muss.**

Um **disable** flexible Port-Ausgangs aus einer bestimmten Umgebung aufzurufen, rufen Sie `DELETE [/program/{programId}/environment/{environmentId}/advancedNetworking]()` auf.

Weitere Informationen finden Sie in der [Cloud Manager-API-Dokumentation](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/disableEnvironmentAdvancedNetworkingConfiguration).

### Traffic-Routing {#flexible-port-egress-traffic-routing}

HTTP- oder HTTPS-Traffic, der über die Ports 80 oder 443 an Ziele geleitet wird, durchläuft einen vorkonfigurierten Proxy, vorausgesetzt, die standardmäßige Java-Netzwerkbibliothek wird verwendet. Für HTTP- oder HTTPS-Traffic, der über andere Ports erfolgt, sollte ein Proxy mit den folgenden Eigenschaften konfiguriert werden.

* `AEM_HTTP_PROXY_HOST / AEM_HTTPS_PROXY_HOST`
* `AEM_HTTP_PROXY_PORT / AEM_HTTPS_PROXY_PORT`

Hier finden Sie beispielsweise einen Beispielcode zum Senden einer Anfrage an `www.example.com:8443`:

```java
HttpsHost target = new HttpsHost("example.com", 8443, "https");
 
HttpHost proxy = new HttpHost(System.getenv("AEM_HTTPS_PROXY_HOST"),
                              Integer.parseInt(System.getenv("AEM_HTTPS_PROXY_PORT")),
                              "https");
 
RequestConfig config = RequestConfig.custom().setProxy(proxy).build();
 
HttpGet request = new HttpGet("/");
request.setConfig(config);
CloseableHttpResponse response = httpclient.execute(target, request);
```

Wenn Sie nicht standardmäßige Java-Netzwerkbibliotheken verwenden, konfigurieren Sie Proxys für den gesamten Traffic mithilfe der oben genannten Eigenschaften.

Nicht-HTTP/s-Traffic mit Zielen über im Parameter `portForwards` deklarierte Ports sollte zusammen mit dem zugeordneten Port auf eine Eigenschaft mit der Bezeichnung `AEM_PROXY_HOST` verweisen. Zum Beispiel:

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
    <td>Der Client stellt eine Verbindung zur Umgebungsvariablen <code>AEM_PROXY_HOST</code> her, indem eine <code>portOrig</code> verwendet wird, die im API-Parameter <code>portForwards</code> deklariert ist.</td>
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

Die Anweisung `mod_proxy` der AEM Cloud Service-Apache-/Dispatcher-Ebene kann mit den oben beschriebenen Eigenschaften konfiguriert werden.

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
>Wenn Sie vor der Version vom September 2021 über eine dedizierte Ausgangs-IP verfügen (06.10.21), verweisen Sie auf [Ältere Kunden mit dedizierten Ausstiegsadressen](#legacy-dedicated-egress-address-customers).

### Vorteile {#benefits}

Diese dedizierte IP-Adresse kann die Sicherheit bei der Integration mit SaaS-Anbietern (wie z. B. einem CRM-Anbieter) oder anderen Integrationen außerhalb von AEM as a Cloud Service, die eine Zulassungsliste von IP-Adressen anbieten, erhöhen. Durch Hinzufügen der dedizierten IP-Adresse zur Zulassungsliste wird sichergestellt, dass nur der Traffic aus der AEM Cloud Service des Kunden in den externen Dienst fließen darf. Dies geschieht zusätzlich zum Traffic von allen anderen zulässigen IPs.

Wenn die Funktion der dedizierten IP-Adresse nicht aktiviert ist, fließt der Traffic von AEM as a Cloud Service über eine Reihe von IPs, die mit anderen Kunden gemeinsam genutzt werden.

### Konfiguration {#configuring-dedicated-egress-provision}

>[!INFO]
>
>Die Splunk-Weiterleitungsfunktion ist über eine dedizierte Ausgangs-IP-Adresse nicht möglich.

Die Konfiguration der dedizierten Ausgangs-IP-Adresse ist identisch mit [Flexibler Port-Ausstieg](#configuring-flexible-port-egress-provision).

Der Hauptunterschied besteht darin, dass der Traffic immer von einer dedizierten, eindeutigen IP-Adresse ausgeht. Um diese IP zu finden, verwenden Sie einen DNS-Resolver, um die IP-Adresse zu identifizieren, die `p{PROGRAM_ID}.external.adobeaemcloud.com` zugeordnet ist. Es wird nicht erwartet, dass sich die IP-Adresse ändert. Sollte sich die IP jedoch in Zukunft ändern, wird eine erweiterte Benachrichtigung bereitgestellt.

Zusätzlich zu den Routing-Regeln, die von flexiblen Port-Ausgängen im Endpunkt `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` unterstützt werden, unterstützt die dedizierte Ausgangs-IP-Adresse einen Parameter `nonProxyHosts`. Auf diese Weise können Sie eine Gruppe von Hosts deklarieren, die über einen gemeinsamen IP-Adressbereich statt über die dedizierte IP weitergeleitet werden sollen. Dies kann nützlich sein, da das Traffic-egressing über freigegebene IPs weiter optimiert werden kann. Die `nonProxyHost`-URLs können den Mustern von `example.com` oder `*.example.com` folgen, wobei der Platzhalter nur zu Beginn der Domäne unterstützt wird.

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
    <td>Host, der mit dem Parameter <code>nonProxyHosts</code> übereinstimmt</td>
    <td>80 oder 443</td>
    <td>Über die freigegebenen Cluster-IPs</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Host, der mit dem Parameter <code>nonProxyHosts</code> übereinstimmt</td>
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
    <td>Der Client stellt eine Verbindung zur Variablen <code>AEM_PROXY_HOST</code> env her, indem eine Variable <code>portOrig</code> verwendet wird, die im API-Parameter <code>portForwards</code> deklariert ist.</td>
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
[`HttpClientBuilder.useSystemProperties()`](https://hc.apache.org/httpcomponents-client-4.5.x/current/httpclient/apidocs/org/apache/http/impl/client/HttpClientBuilder.html) oder verwenden Sie
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

### Überlegungen zum Debuggen {#debugging-considerations}

Um zu überprüfen, ob der Traffic tatsächlich über die erwartete dedizierte IP-Adresse ausgeht, überprüfen Sie die Protokolle im Ziel-Service, sofern verfügbar. Andernfalls kann es nützlich sein, einen Debugging-Dienst wie [https://ifconfig.me/IP](https://ifconfig.me/IP) aufzurufen, der die aufrufende IP-Adresse zurückgibt.

## Virtuelles privates Netzwerk (VPN) {#vpn}

VPN ermöglicht die Verbindung zu einer On-Premise-Infrastruktur oder einem Datenzentrum von der Autoren-, Veröffentlichungs- oder Vorschau aus. Beispielsweise für die Mittel zum Zugriff auf eine Datenbank.

Es ermöglicht auch die Verbindung zu SaaS-Anbietern, wie z. B. einem CRM-Anbieter, der VPN unterstützt oder eine Verbindung von einem Unternehmensnetzwerk mit AEM as a Cloud Service Autoren-, Vorschau- oder Veröffentlichungsinstanz herstellt.

Die meisten VPN-Geräte mit IPSec-Technologie werden unterstützt. Sehen Sie sich die Liste der Geräte unter [dieser Seite](https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpn-devices#devicetable) an, basierend auf den Informationen in der Spalte **RouteBased configuration instructions** . Konfigurieren Sie das Gerät wie in der Tabelle beschrieben.

### Allgemeine Überlegungen: {#general-vpn-considerations}

* Unterstützung ist auf eine einzelne VPN-Verbindung beschränkt
* Die Splunk-Weiterleitungsfunktion ist über eine VPN-Verbindung nicht möglich.

### Kreation {#vpn-creation}

Einmal pro Programm wird der Endpunkt der POST `/program/<programId>/networkInfrastructures` aufgerufen und eine Payload mit Konfigurationsinformationen übergeben, darunter: den Wert von &quot;vpn&quot;für den Parameter `kind`, die Region, den Adressraum (Liste der CIDRs - dies kann später nicht geändert werden), DNS-Resolver (zur Namensauflösung im Netzwerk des Kunden) und VPN-Verbindungsinformationen wie Gateway-Konfiguration, freigegebener VPN-Schlüssel und die IP-Sicherheitsrichtlinie. Der Endpunkt antwortet mit `network_id` sowie anderen Informationen, einschließlich des Status. Der vollständige Satz von Parametern und die genaue Syntax sollten in der [API-Dokumentation](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/createNetworkInfrastructure) referenziert werden.

Nach dem Aufruf dauert es in der Regel zwischen 45 und 60 Minuten, bis die Netzwerkinfrastruktur bereitgestellt wird. Die GET-Methode der API kann aufgerufen werden, um den aktuellen Status zurückzugeben, der schließlich von `creating` zu `ready` wechselt. In der API-Dokumentation finden Sie alle Status.

Wenn die programmgesteuerte VPN-Konfiguration bereit ist, muss der `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking`-Endpunkt pro Umgebung aufgerufen werden, um die Vernetzung auf Umgebungsebene zu ermöglichen und alle Port-Weiterleitungsregeln zu deklarieren. Parameter können je Umgebung konfiguriert werden, um Flexibilität zu bieten.

Weitere Informationen finden Sie in der [API-Dokumentation](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/enableEnvironmentAdvancedNetworkingConfiguration) .

Regeln für die Port-Weiterleitung sollten für jeden TCP-Traffic, der nicht HTTP/s-Protokoll ist und über das VPN geleitet werden soll, deklariert werden, indem der Satz von Ziel-Hosts (Namen oder IP und Ports) angegeben wird. Für jeden Ziel-Host müssen Kunden den beabsichtigten Ziel-Port einem Port von 30000 bis 30999 zuordnen, wobei die Werte in allen Umgebungen im Programm eindeutig sein müssen. Kunden können auch eine Reihe von URLs im Parameter `nonProxyHosts` auflisten, die URLs deklarieren, für die der Traffic das VPN-Routing umgehen soll, sondern über einen freigegebenen IP-Bereich. Sie folgt den Mustern von `example.com` oder `*.example.com`, wobei der Platzhalter nur zu Beginn der Domäne unterstützt wird.

Die API sollte in nur wenigen Sekunden antworten, was auf den Status `updating` verweist. Nach etwa 10 Minuten zeigt ein Aufruf des Umgebungs-GET von Cloud Manager den Status `ready` an, der angibt, dass die Aktualisierung der Umgebung angewendet wurde.

Beachten Sie, dass auch dann `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` aufgerufen werden muss, wenn keine Regeln zum Umgebungs-Traffic-Routing (Hosts oder Umgehungen) vorhanden sind, und zwar nur mit einer leeren Payload.

### VPN aktualisieren {#updating-the-vpn}

Die VPN-Konfiguration auf Programmebene kann aktualisiert werden, indem der Endpunkt `PUT /api/program/<program_id>/network/<network_id>` aufgerufen wird.

Beachten Sie, dass der Adressraum nach der ersten VPN-Bereitstellung nicht mehr geändert werden kann. Wenden Sie sich bei Bedarf an den Support. Darüber hinaus kann der Parameter `kind` (`flexiblePortEgress`, `dedicatedEgressIP` oder `VPN`) nicht geändert werden. Wenden Sie sich an den Support, um Unterstützung zu erhalten, und beschreiben Sie, was bereits erstellt wurde und warum die Änderung vorgenommen wurde.

Die Routing-Regeln pro Umgebung können aktualisiert werden, indem Sie den `PUT /program/{programId}/environment/{environmentId}/advancedNetworking`-Endpunkt erneut aufrufen. Stellen Sie dabei sicher, dass Sie den vollständigen Satz von Konfigurationsparametern und nicht eine Untergruppe einschließen. Die Anwendung von Umgebungsaktualisierungen dauert in der Regel 5-10 Minuten.

### VPN löschen oder deaktivieren {#deleting-or-disabling-the-vpn}

Um die Netzwerkinfrastruktur zu löschen, senden Sie ein Support-Ticket, in dem beschrieben wird, was erstellt wurde und warum es gelöscht werden muss.

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
    <td>Host, der mit dem Parameter <code>nonProxyHosts</code> übereinstimmt</td>
    <td>80 oder 443</td>
    <td>Über die freigegebenen Cluster-IPs</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Host, der mit dem Parameter <code>nonProxyHosts</code> übereinstimmt</td>
    <td>Ports außerhalb 80 oder 443</td>
    <td>Blockiert</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Wenn die IP in den Bereich <i>VPN-Gateway-Adresse</i> fällt, und über die HTTP-Proxy-Konfiguration (standardmäßig für HTTP/s-Traffic mithilfe der standardmäßigen Java-HTTP-Client-Bibliothek konfiguriert)</td>
    <td>Alle</td>
    <td>Über VPN</td>
    <td><code>10.0.0.1:443</code>Es kann auch ein Hostname sein.</td>
  </tr>
  <tr>
    <td></td>
    <td>Wenn die IP nicht in den Bereich <i>VPN-Gateway-Adressenbereich</i> fällt, und durch HTTP-Proxy-Konfiguration (standardmäßig für HTTP/s-Traffic mithilfe der standardmäßigen Java-HTTP-Client-Bibliothek konfiguriert)</td>
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
    <td>Wenn die IP in den Bereich <i>VPN-Gateway-Adressenbereich</i> fällt und der Client eine Verbindung zur <code>AEM_PROXY_HOST</code>-env-Variablen herstellt, indem er eine <code>portOrig</code> -Variable verwendet, die im API-Parameter <code>portForwards</code> deklariert ist.</td>
    <td>Alle</td>
    <td>Über VPN</td>
    <td><code>10.0.0.1:3306</code>Es kann auch ein Hostname sein.</td>
  </tr>
  <tr>
    <td></td>
    <td>Wenn die IP nicht in den Bereich <i>VPN-Gateway-Adressenbereich</i> fällt und der Client eine Verbindung zur <code>AEM_PROXY_HOST</code>-env-Variablen herstellt, indem eine <code>portOrig</code> verwendet wird, die im API-Parameter <code>portForwards</code> deklariert ist.</td>
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
    <td>Wenn der Kunde nur VPN-Zugriff auf AEM zulassen möchte, sollte er CNAME-DNS-Einträge so konfigurieren, dass <code>author-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code> und/oder <code>publish-p{PROGRAM_ID}-e{ENVIRONMENT_ID}.adobeaemcloud.com</code> zugeordnet werden.</td>
  </tr>
</tbody>
</table>

### VPN auf eingehende Verbindungen beschränken {#restrict-vpn-to-ingress-connections}

Wenn Sie nur VPN-Zugriff auf AEM zulassen möchten, können Umgebungsauf die Zulassungsliste setzte in Cloud Manager konfiguriert werden, sodass nur die von `p{PROGRAM_ID}.external.adobeaemcloud.com` definierte IP mit der Umgebung kommunizieren darf. Dies kann auf dieselbe Weise wie jede andere IP-basierte Zulassungsliste in Cloud Manager erfolgen.

Wenn Regeln pfadbasiert sein müssen, verwenden Sie standardmäßige HTTP-Anweisungen auf Dispatcher-Ebene, um bestimmte IPs zu verweigern oder zuzulassen. Sie sollten sicherstellen, dass die gewünschten Pfade auch im CDN nicht zwischenspeicherbar sind, sodass die Anfrage immer an den Ursprung gelangt.

**Beispiel für Httpd-Konfiguration**

```
Order deny,allow
Deny from all
Allow from 192.168.0.1
Header always set Cache-Control private
```

## Übergang zwischen fortgeschrittenen Netzwerktypen {#transitioning-between-advanced-networking-types}

Da der Parameter `kind` nicht geändert werden kann, wenden Sie sich an den Support, um Hilfe zu erhalten. Geben Sie an, was bereits erstellt wurde und warum die Änderung vorgenommen wurde.