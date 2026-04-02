---
title: Netzwerkverbindungstest
description: Verwenden Sie den Netzwerkkonnektivitätstest in Cloud Manager, um die erweiterte Netzwerk- und VPN-Konfiguration aus dem Ausgangspfad Ihres Programms zu validieren, bevor Sie das Netzwerk in Umgebungen aktivieren.
feature: Security
role: Admin
source-git-commit: b29b3a980a0bc1c619fb23c52acda79fae9bf945
workflow-type: tm+mt
source-wordcount: '2047'
ht-degree: 2%

---


# Netzwerkverbindungstest {#network-connectivity-test}

Der **Netzwerkkonnektivitätstest** ist ein Cloud Manager-Diagnose-Tool, mit dem Sie die erweiterte Netzwerk- und VPN-Konfiguration validieren können, bevor Sie die erweiterte Vernetzung in Ihren Umgebungen aktivieren und bevor Sie live gehen. Vergewissern Sie sich, dass die Hosts und Ports, die AEM erreichen muss, einschließlich interner oder privater Endpunkte, über denselben Verbindungspfad erreichbar sind, den Advanced Networking verwenden wird.

Der Test wird von der **Ausgangs-Proxy-Infrastruktur** ausgeführt, die zum erweiterten Netzwerksetup Ihres Programms gehört, und nicht von einem Autoren- oder Veröffentlichungs-Pod. Es wird derselbe ausgehende Netzwerkpfad verwendet, den AEM verwendet, wenn das erweiterte Netzwerk aktiv ist. Dieses Design ist besonders für **VPN**-Szenarien nützlich: Sie können die DNS-Auflösung, das Netzwerk-Routing, Firewall-Regeln und die Dienstverfügbarkeit für private oder lokale Systeme überprüfen, bevor Sie live gehen.

Hintergrundinformationen zur Bereitstellung von VPN, dedizierter Ausgangs-IP oder flexibler Ausgangs-Port finden Sie unter [Konfigurieren von erweiterten Netzwerkfunktionen für AEM as a Cloud Service](/help/security/configuring-advanced-networking.md).

>[!IMPORTANT]
>
>Ein erfolgreicher Konnektivitätstest belegt, dass der Netzwerkpfad von Advanced Networking Ihr Ziel erreichen kann. Ihr Anwendungs-Code muss weiterhin so konfiguriert sein, dass er bei Bedarf den erweiterten Netzwerk-Proxy verwendet (z. B. Proxy-bezogene Umgebungsvariablen und Port-Weiterleitung). Wenn der Code den Proxy umgeht, wird möglicherweise kein Traffic vom erwarteten Ausstiegspfad angezeigt, selbst wenn der Test erfolgreich ist.

## Verwendung dieses Tools {#when-to-use}

* Nach **Erweiterte**&quot; wird auf der **Programm**-Ebene und **davor** oder bei Aktivierung in **Umgebungen** erstellt.
* Zur Überprüfung der **VPN**-Konnektivität mit privaten oder lokalen Systemen, die Sie betreiben (z. B. interne Hostnamen oder private IP-Adressen).
* Um DNS-Probleme im Vergleich zur Firewall oder Routing-Probleme einzugrenzen, wenn ein Service nicht wie erwartet reagiert.

>[!NOTE]
>
>Dieses Tool ist für Programme vorgesehen, die erweiterte Netzwerkfunktionen (VPN, dedizierte Ausgangs-IP oder flexible Port-Ausgangs-IP) verwenden. Es handelt sich hierbei nicht um einen allgemeinen Test der standardmäßigen AEM-Konnektivität ohne erweiterte Netzwerkfunktionen.

## Voraussetzungen {#prerequisites}

* Ein Cloud Manager-Programm.
* Die Infrastruktur für erweiterte Netzwerke wurde bereits für das Programm erstellt (siehe [Konfigurieren erweiterter Netzwerke](/help/security/configuring-advanced-networking.md)).

## Ausführen eines Tests {#how-to-run-a-test}

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an und öffnen Sie Ihr Unternehmen und Ihr Programm.
1. Öffnen Sie die **Umgebungen** für das Programm. Wählen Sie in der linken Seitenleiste **Netzwerkinfrastruktur** aus.

1. Suchen Sie auf **Seite &quot;**&quot; Ihre Infrastruktur in der Tabelle. Wählen Sie entweder eine Zeile aus, um das Testerlebnis zu öffnen, oder öffnen Sie das Menü für Zeilenaktionen (![Adobe Spectrum Small More icon für das Menü mit den horizontalen &#x200B;](assets/ellipsis.svg)) und wählen Sie **Test**.

   ![Cloud Manager-Programmumgebungen mit dem Menü Netzwerkinfrastrukturtabelle, Infrastrukturzeilen und Zeilenaktionen , das zum Starten des Netzwerkkonnektivitätstests verwendet wird](assets/network-connectivity-test-cloud-manager-open-test-from-infrastructure-list.png)

1. Das **Netzwerktest** wird geöffnet. Geben Sie **Host** und **Port** ein, wählen Sie **Test** aus und überprüfen Sie die DNS-Auflösung, das Öffnen des Ports, die HTTP-Konnektivität und die Erreichbarkeit im Ergebnisbereich. Optionale Aktionen wie **In Zwischenablage kopieren** und der aktuelle Testverlauf werden im Dialogfeld angezeigt. Informationen [&#x200B; Interpretation der einzelnen &#x200B;](#understanding-results) finden Sie unter „Grundlegendes zu Ergebnissen“.

   ![Testdialogfeld für Cloud Manager-Netzwerkkonnektivität mit Host- und Port-Feldern, Testaktion und Ergebnissen für DNS-Auflösung, Port-Öffnung, HTTP-Konnektivität und Erreichbarkeit](assets/network-connectivity-test-cloud-manager-results-dialog.png)

### Eingabefelder {#input-fields}

| Feld | Beschreibung | Beispiele |
| --- | --- | --- |
| **Host** | Hostname oder IP-Adresse des Dienstes, den AEM erreichen sollte. | `internal-api.example.com`, `10.0.1.50` |
| **port** | TCP-Port auf dem Ziel-Host (1-65535). Häufige Werte können in einer Liste mit Shortcuts angezeigt werden (z. B. 80, 443, 587, 22). | `443` |

### Schritte {#test-steps}

1. Geben Sie **Host** und **Port** ein.
1. Wählen Sie **Test** aus. Die Ergebnisse werden in der Regel innerhalb weniger Sekunden angezeigt.
1. Optional: Verwenden Sie **In Zwischenablage kopieren**, um das vollständige JSON-Ergebnis zu erfassen (nützlich für Support-Fälle).
1. Kürzlich durchgeführte Tests können zur schnellen Wiederholung aufgelistet werden.

## Grundlegendes zu Ergebnissen {#understanding-results}

Das Tool meldet mehrere Dimensionen. Zusammen beschreiben sie, ob das Ziel über erweiterte Netzwerke erreichbar ist und wie sich HTTP-fähige Prüfungen verhielten.

### DNS-Auflösung {#dns-resolution}

| Ergebnis | Bedeutung |
| --- | --- |
| `ips: ["10.0.1.50"]` | DNS-Auflösung erfolgreich. Der Hostname wurde mithilfe der Resolver, die mit Ihrer erweiterten Netzwerkkonfiguration verknüpft sind, in die aufgelisteten IP-Adressen aufgelöst. |
| `error: "DNS resolution error: ..."` | DNS-Auflösung fehlgeschlagen. Die konfigurierten DNS-Server konnten den Host-Namen nicht auflösen (falscher Name, nicht erreichbarer Resolver, fehlende Einträge und ähnliche Ursachen). |

>[!NOTE]
>
>Wenn Sie anstelle **Hostnamens eine numerische IP**, wird die DNS-Auflösung für diesen Wert übersprungen und die IP wird direkt verwendet.

### Port offen {#port-open}

| Ergebnis | Bedeutung |
| --- | --- |
| `Yes`/true | TCP-Verbindung erfolgreich - Der Port ist offen und akzeptiert Verbindungen. |
| `No`/false | Der Port wird geschlossen, durch eine Firewall gefiltert oder der Host ist nicht erreichbar. |

### HTTP-Verbindung {#http-connectivity}

Eine HTTP/HTTPS-Anfrage wird an (**Ports)**. Das Tool versucht immer zuerst **HTTPS** und kehrt dann auf **HTTP** zurück. Wenn keines von beiden funktioniert, wird das Ergebnis einer kurzen, lesbaren **(**) zugeordnet (siehe Tabelle unten).

**Erfolgreiche Ausgaben**

| Ausgabe | Bedeutung |
| --- | --- |
| `protocol: "https"`, `status_code: 200`, `reason: "200 OK"` | HTTPS-Verbindung erfolgreich. |
| `protocol: "http"`, `status_code: 301`, `reason: "301 Moved Permanently"` | HTTP-Verbindung erfolgreich; der Dienst wird umgeleitet (normalerweise zu HTTPS). Das ist normal. |

**Klassifizierte Fehlerausgaben**

| Fehler | Hinweis | Bedeutung |
| --- | --- | --- |
| `"Not an HTTP/HTTPS service"` | `"The service appears to be a non-HTTP service (e.g., database, message queue, or custom TCP). Use the port_open and reachability fields to verify connectivity."` | Der Port ist offen, aber der Service spricht kein HTTP. Dies wird für Datenbanken, SFTP, benutzerdefiniertes TCP und ähnliche Services erwartet. |
| `"Connection refused"` | `"The port is not accepting connections. Verify the service is running and listening on this port."` | An diesem Port wird nichts abgehört. |
| `"Connection timed out"` | `"The connection timed out. Check firewall rules and network routing."` | Ein Firewall- oder Routing-Problem verhindert die Verbindung. |
| `"No IPs resolved for host"` | — | DNS-Auflösung fehlgeschlagen; HTTP kann nicht getestet werden. |

>[!NOTE]
>
>Jeder HTTP-Status-Code vom Ziel-Service (z. B. `200`, `301`, `302`, `403`, `404` oder `500`) ist ein **Erfolgssignal** für die Konnektivität, d. h. der **Netzwerkpfad** funktioniert. Der Status-Code spiegelt die eigene Antwort des Service wider, nicht den allgemeinen Netzwerkzustand. Für Nicht-HTTP-Services gibt das Tool an **keinen HTTP/HTTPS-Service** verwenden Sie **Port Open** und **Reachability** als zuverlässige Indikatoren für diese Services.

### Erreichbarkeit {#reachability}

| Ergebnis | Bedeutung |
| --- | --- |
| **Erreichbar** | Der Ziel-Host und -Port sind über die erweiterte Netzwerkinfrastruktur erreichbar. Die Netzwerkkonfiguration ist korrekt. |
| **Unerreichbar: Port nicht zugänglich** | DNS wurde erfolgreich aufgelöst, aber TCP zum Port war nicht erfolgreich. Dies ist normalerweise eine Firewall oder ein Routing-Problem. |
| **Unerreichbar: DNS-Auflösung fehlgeschlagen** | Der Hostname konnte mit Ihrer Konfiguration nicht aufgelöst werden. Dies ist ein Hinweis auf ein DNS-Konfigurationsproblem. |

### Mehrere DNS-Resolver {#multiple-dns-resolvers}

Wenn Ihre Infrastruktur für erweiterte Netzwerke (**einen DNS-Resolver)**:

* Wenn **alle Resolver identische Ergebnisse zurückgeben** wird ein (**konsolidiertes** Ergebnis mit der Bezeichnung `default` angezeigt.
* Wenn Resolver **verschiedene Ergebnisse** zurückgeben, wird das Ergebnis jedes Resolvers **separat** (mit `resolver_1`, `resolver_2` usw. gekennzeichnet) **mit der Resolver-IP** angezeigt, sodass Sie sehen können, welcher DNS-Server die Inkonsistenz verursacht.

## Fehlerbehebung {#troubleshooting}

Die folgenden Szenarien kombinieren das, was Sie wahrscheinlich im Tool sehen werden, mit Schritten, um die Ursache einzugrenzen. Eine vollständige JSON-Datei **In Zwischenablage kopieren**, die dieselben Situationen veranschaulicht, finden Sie unter [Beispielausgaben](#example-outputs).

### DNS-Auflösung fehlgeschlagen {#dns-failed}

#### Ausgabe

Der Hostname wurde nicht mithilfe der DNS-Einstellungen für die erweiterten Netzwerkfunktionen aufgelöst, sodass das Tool den Port nicht testen kann. In der Ergebnisansicht zeigt **DNS-Auflösung** eine Fehlerzeichenfolge an und **Erreichbarkeit** meldet, dass DNS fehlgeschlagen ist:

```
DNS Resolution: error: "DNS resolution error: ..."
Reachability: "Unreachable: DNS resolution failed"
```

#### Empfehlungen

1. **Überprüfen Sie, ob der Hostname korrekt ist**—Überprüfen Sie auf Tippfehler und dass Sie die beabsichtigte **DNS-Zone** verwenden (die falsche Zone ist ein häufiger Fehler).
1. Stellen Sie **Ihre DNS-Resolver** - die in der Netzwerkinfrastruktur konfigurierten - sicher, dass sie **über den CIDR-Bereich für erweiterte Netzwerke erreichbar) sind** derselbe Adressraum, den das Tool und AEM für ausgehende Prüfungen verwenden). Wenn Sie auf ein privates DNS angewiesen sind, müssen diese Server über den VPN-Tunnel oder innerhalb des Netzwerkadressbereichs, den das Routing für erweiterte Netzwerke bereitstellt, erreichbar sein.
1. **Überprüfen Sie, ob Ihre konfigurierten DNS-Server den Hostnamen auflösen können** — Advanced Networking verwendet **nur** die in Ihrer Netzwerkinfrastruktur-Einrichtung definierten Resolver, **nicht** öffentliches DNS (z. B. `8.8.8.8`). Wenn Ihr internes DNS keinen Eintrag für diesen Hostnamen hat, schlägt die Auflösung fehl.
1. **Bei VPN-Setups:** Bestätigen Sie, dass die IP-Adressen des DNS-Servers im VPN-Adressraum liegen (das Remote-Netzwerk CIDR, für das der Tunnel erstellt wurde). Resolver in einem Subnetz, das nicht durch den VPN-Tunnel geleitet wird, sind über das erweiterte Netzwerk nicht erreichbar.

### DNS funktioniert, aber der Port ist nicht zugänglich {#dns-ok-port-blocked}

#### Ausgabe

Das Tool kann den Host auflösen, aber TCP zum Port ist nicht erfolgreich. Eine Zusammenfassung sieht oft wie folgt aus:

```
DNS Resolution: ips: ["10.0.1.50"]
Port Open: No
Reachability: "Unreachable: Port not accessible"
```

#### Empfehlungen

1. **Überprüfen der Firewall- und Zulassungslisten-Regeln für den Ziel-Service** - Eingehender Traffic aus dem CIDR-Bereich Ihrer erweiterten Netzwerkinfrastruktur (und den von AEM verwendeten Ausgangs-IP-Adressen) muss zulässig sein. Wenn Sie ein VPN verwenden, schließen Sie je nach Design Remote-Netzwerk-CIDRs ein.
1. **Stellen Sie sicher, dass der Dienst ausgeführt wird** und **überwachen Sie den Host und Port**, die Sie beim Test eingegeben haben.
1. **Bei VPN-Setups:** Sie, dass der Tunnel hochgefahren ist, das Routing das Ziel-Subnetz erreicht und die Zieladresse im Remote-Netzwerkadressraum liegt, der über das VPN übertragen wird.
1. Überprüfen Sie in Ihrer Infrastruktur **Netzwerksicherheitsgruppen (NSGs), Sicherheitsregeln oder Ähnliches** die den Port zwischen erweiterten Netzwerkfunktionen und dem Ziel blockieren könnten.
1. **Bestätigen Sie die Portnummer** - stellen Sie sicher, dass der Prozess tatsächlich auf dem zu testenden Port wartet.

### Test zeigt Erreichbarkeit an, aber AEM stellt keine Verbindung her {#reachable-but-aem-fails}

#### Ausgabe

Die Konnektivitätsprüfung selbst ist erfolgreich. Eine verkürzte Zusammenfassung sieht oft wie folgt aus:

```
Port Open: Yes
Reachability: "Reachable"
```

Dies bedeutet, dass der Pfad von den erweiterten Netzwerkfunktionen zum getesteten Host und Port offen ist. Es ist nicht garantiert, dass der Traffic der AEM-Anwendung diesen Pfad verwendet: Wenn Ihr Code ausgeführt wird, zeigen Service-Protokolle möglicherweise immer noch keine Anforderungen von der erwarteten Ausgangs-IP an.

#### Empfehlungen

1. **Der Anwendungs-Code muss für die Verwendung des Proxys konfiguriert werden**. Der Konnektivitätstest belegt, dass der Netzwerkpfad funktioniert, aber AEM muss Anforderungen explizit über den **erweiterten Netzwerk-Proxy** weiterleiten (z. B. über die **`AEM_PROXY_HOST`** Umgebungsvariable ). Wenn der Code direkte Verbindungen ohne den Proxy herstellt, erfolgt kein Traffic über die Infrastruktur des erweiterten Netzwerks.
1. **Überprüfen der Proxy-Einstellungen in Ihren HTTP** Clients: HTTP-Clients sollten dieselbe Proxy-Konfiguration verwenden (`AEM_PROXY_HOST` und Port-Weiterleitung, falls zutreffend).
1. **Überprüfen Sie die Port-Weiterleitungskonfiguration** für erweiterte Vernetzung auf der **Umgebung**-Ebene: In `portForwards` muss jeder Eintrag **`portOrig`** **`portDest`** auf dem rechten **Ziel-Host** zuordnen. **`portOrig`** ist der **Port, mit dem Ihr AEM-Anwendungs-Code**, wenn er die ausgehende Verbindung über den Proxy öffnet. **`portDest`** ist der **tatsächliche Port auf dem Ziel-Service** auf den der Remote-Prozess wartet. Der **Ziel-Host** ist der **Hostname oder die Adresse dieses Service** wie in der Weiterleitung verwendet. Alle drei müssen mit der Art und Weise übereinstimmen, wie die Anwendung für die Verbindung geschrieben wurde.
1. **Überprüfen Sie`nonProxyHosts`**. Wenn der Ziel-Host dort aufgeführt ist, **Anfragen (** überspringen) für diesen Host und folgen nicht dem von Ihnen validierten Pfad für erweiterte Netzwerke.

### HTTP zeigt einen Fehler an, aber Port ist offen {#http-error-port-open}

#### Ausgabe

TCP ist erfolgreich, aber der HTTP/HTTPS-Test meldet weiterhin einen Fehler. Eine Zusammenfassung sieht oft wie folgt aus:

```
Port Open: Yes
HTTP Connectivity: error: "Connection error: ..." or "Both HTTPS and HTTP failed. ..."
Reachability: "Reachable"
```

#### Empfehlungen

1. **Der Service spricht möglicherweise nicht HTTP oder HTTPS**, z. B. rohe TCP, gRPC oder ein anderes Protokoll. Der HTTP-Test kann fehlschlagen, während `Port open: Yes` und `Reachability: Reachable` noch bestätigen, dass der Netzwerkpfad funktioniert. Verwenden Sie diese Felder als Datenquelle für Nicht-HTTP-Services.
1. **TLS- und Zertifikatkonfiguration**. Wenn HTTPS fehlschlägt, aber HTTP erfolgreich ist (was manchmal durch einen Hinweis wie `HTTPS failed, HTTP succeeded` angezeigt wird), kann der Service Zertifikatsprobleme haben oder nur HTTP auf diesem Port anbieten.

### Zeitüberschreitung der Anfrage {#timeout}

#### Ausgabe

```json
{ "error": "Request timeout" }
```

#### Empfehlungen

1. **Service-Antwortzeit zulassen** - Die Prüfung verwendet eine Zeitüberschreitung von 5 Sekunden. Ziele, die langsamer reagieren, werden eine Zeitüberschreitung erfahren, selbst wenn sie ansonsten gesund sind.
1. **Konto für Netzwerklatenz**. Bei VPN-Verbindungen kann eine hohe Latenz oder ein ungesunder Tunnel den Hin- und Rückflug über das Limit schieben und den Tunnelstatus und das Routing überprüfen.
1. **Führen Sie den Test erneut**. Einmalige Netzwerkfehler können zu einem Timeout führen, das nicht erneut auftritt.

## Beispielausgaben {#example-outputs}

### Erfolgreicher HTTPS-Test (z. B. interne API an Port 443) {#example-output-successful-https}

```json
{
  "resolvers": [
    {
      "name": "default",
      "dns_resolution": {
        "ips": ["10.0.1.50"]
      },
      "port_open": true,
      "http_connectivity": {
        "protocol": "https",
        "status_code": 200,
        "reason": "200 OK"
      },
      "reachability": "Reachable"
    }
  ]
}
```

### Erfolgreicher Non-HTTP-Service-Test (z. B. Datenbank auf Port 5432) {#example-output-successful-non-http}

```json
{
  "resolvers": [
    {
      "name": "default",
      "dns_resolution": {
        "ips": ["10.0.1.50"]
      },
      "port_open": true,
      "http_connectivity": {
        "error": "Not an HTTP/HTTPS service",
        "note": "The service appears to be a non-HTTP service (e.g., database, message queue, or custom TCP). Use the port_open and reachability fields to verify connectivity."
      },
      "reachability": "Reachable"
    }
  ]
}
```

>[!NOTE]
>
>Der HTTP-Fehler wird für Nicht-HTTP-Services erwartet. **Port offen: true** und **Erreichbarkeit:**) bestätigen, dass der Netzwerkpfad funktioniert.

### DNS-Auflösungsfehler {#example-output-dns-resolution-failure}

```json
{
  "resolvers": [
    {
      "name": "default",
      "dns_resolution": {
        "error": "DNS resolution error: dial udp 10.0.0.2:53: i/o timeout"
      },
      "port_open": false,
      "http_connectivity": {
        "error": "DNS resolution failed"
      },
      "reachability": "Unreachable: DNS resolution failed"
    }
  ]
}
```

### Port nicht zugänglich (Firewall / Service nicht verfügbar) {#example-output-port-not-accessible}

```json
{
  "resolvers": [
    {
      "name": "default",
      "dns_resolution": {
        "ips": ["10.0.1.50"]
      },
      "port_open": false,
      "http_connectivity": {
        "error": "Connection error: dial tcp 10.0.1.50:443: i/o timeout"
      },
      "reachability": "Unreachable: Port not accessible"
    }
  ]
}
```

## Wichtige Hinweise {#important-notes}

### Was dieser Test nicht tut {#what-this-test-does-not-do}

* Der Test wird nicht innerhalb eines AEM-Autoren- oder Veröffentlichungs-Pods ausgeführt. Es läuft von **Ausgangs-Proxy-Infrastruktur**. Dadurch wird die Netzwerkschicht validiert, nicht die Proxy-Konfiguration auf Anwendungsebene in Ihrem Code.
* Die Proxy-Einstellungen Ihres AEM-Programms werden nicht validiert. Auch wenn das Ergebnis `Reachable` ist, muss AEM-Code weiterhin für die Verwendung des Proxys konfiguriert werden.
* Die Konfiguration der Port-Weiterleitung auf Umgebungsebene wird nicht automatisch validiert. Die Rohkonnektivität wird über den Infrastrukturpfad getestet.
* Es werden keine benutzerdefinierten Payloads gesendet. HTTP-Tests geben eine einfache `GET` an `/` aus.

### Antwortzeit {#response-time}

* **Typisch:** etwa 2 bis 3 Sekunden.
* **Maximum:** Zeitüberschreitung nach etwa fünf Sekunden.
* **Alle DNS-Resolver** und Konnektivitätsprüfungen werden parallel ausgeführt.

### HTTP im Vergleich zu Nicht-HTTP-Services {#http-vs-non-http-services}

Das Tool versucht eine HTTP/HTTPS-Verbindung an jedem Port. Bei Nicht-HTTP-Services (z. B. PostgreSQL an Port 5432, MySQL an 3306, SFTP an 22, Redis an 6379) kann die HTTP-Prüfung mit einem Verbindungsfehler fehlschlagen - dies ist zu erwarten. Verlassen Sie sich auf `Port open` und `Reachability`, um die Konnektivität für diese Services zu bestätigen.

## Ergänzende Informationen {#related-information}

* [Konfigurieren der erweiterten Netzwerkfunktionen für AEM as a Cloud Service](/help/security/configuring-advanced-networking.md)
* [Tutorials zu erweiterten Netzwerken in Experience League](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/networking/advanced-networking)
