---
title: Protokollierung
description: Erfahren Sie, wie Sie globale Parameter für den zentralen Protokollierungsdienst konfigurieren, bestimmte Einstellungen für einzelne Dienste festlegen oder eine Datenprotokollierung anfordern können.
translation-type: tm+mt
source-git-commit: 49bb443019edc6bdec22e24b8a8c7733abe54e35
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 17%

---


# Protokollierung {#logging}

AEM as a Cloud Service ist eine Plattform, auf der Kunden benutzerdefinierten Code einbinden können, um einzigartige Erlebnisse für ihre Kunden zu erstellen. Vor diesem Hintergrund ist die Protokollierung eine wichtige Funktion, um die Codeausführung bei lokalen Entwicklungs- und Cloud-Umgebung zu debuggen und zu verstehen, insbesondere die AEM als Dev-Umgebung eines Cloud Service.

AEM Protokollierungs- und Protokollierungsebenen werden in Konfigurationsdateien verwaltet, die als Teil des AEM Projekts in Git gespeichert und als Teil des AEM Projekts über Cloud Manager bereitgestellt werden. Die Anmeldung AEM als Cloud Service kann in zwei logische Sätze unterteilt werden:

* AEM Protokollierung, die die Protokollierung auf AEM Anwendungsebene durchführt
* Apache HTTPD Web Server/Dispatcher-Protokollierung, die die Protokollierung des Webservers und des Dispatchers auf der Veröffentlichungsstufe durchführt.

## AEM {#aem-loggin}

Die Protokollierung auf AEM Anwendungsebene erfolgt über drei Protokolle:

1. AEM Java-Protokolle, die Java-Protokollanweisungen für die AEM Anwendung wiedergeben.
1. HTTP-Anforderungsprotokolle, die Informationen zu HTTP-Anforderungen und deren Antworten AEM
1. HTTP-Zugriffsprotokolle, in denen zusammengefasste Informationen und HTTP-Anforderungen, die von AEM bereitgestellt werden, protokolliert werden

Beachten Sie, dass HTTP-Anforderungen, die vom Dispatcher-Cache der Veröffentlichungsstufe oder vom Upstream-CDN bereitgestellt werden, nicht in diesen Protokollen angezeigt werden.

### AEM Java-Protokollierung {#aem-java-logging}

AEM als Cloud Service bietet Zugriff auf Java-Protokollanweisungen. Entwickler von Anwendungen für AEM sollten sich an die allgemeinen Best Practices für die Java-Protokollierung halten und relevante Anweisungen zur Ausführung von benutzerdefiniertem Code auf den folgenden Protokollebenen protokollieren:

<table>
<tr>
<td>
<b>AEM Umgebung</b></td>
<td>
<b>Protokollebene</b></td>
<td>
<b>Beschreibung</b></td>
<td>
<b>Verfügbarkeit der Protokollerklärung</b></td>
</tr>
<tr>
<td>
Entwicklung</td>
<td>
DEBUG</td>
<td>
Beschreibt, was in der Anwendung geschieht.<br>

Wenn die DEBUG-Protokollierung aktiv ist, werden Anweisungen protokolliert, die ein klares Bild von den auftretenden Aktivitäten sowie allen wichtigen Parametern, die sich auf die Verarbeitung auswirken, vermitteln.</td>
<td>
<ul>
<li> Lokale Entwicklung</li>
<li>Entwicklung</li>
</ul></td>
</tr>
<tr>
<td>
Staging</td>
<td>
WARN</td>
<td>
Beschreibt Bedingungen, bei denen Fehler auftreten können.<br>
Wenn die WARN-Protokollierung aktiv ist, werden nur Anweisungen protokolliert, die auf Bedingungen hinweisen, die sich der Unter-Optimalität nähern.</td>
<td>
<ul>
<li> Lokale Entwicklung</li>
<li>Entwicklung</li>
<li>Staging</li>
</ul></td>
</tr>
<tr>
<td>
Produktion</td>
<td>
FEHLER</td>
<td>
Beschreibt Bedingungen, die auf einen Fehler hinweisen und gelöst werden müssen.<br>
Wenn die ERROR-Protokollierung aktiv ist, werden nur Anweisungen protokolliert, die auf Fehler hinweisen. ERROR-Protokollerklärungen deuten auf ein schwerwiegendes Problem hin, das so bald wie möglich gelöst werden sollte.</td>
<td>
<ul>
<li> Lokale Entwicklung</li>
<li>Entwicklung</li>
<li>Staging</li>
<li>Produktion</li>
</ul></td>
</tr>
</table>