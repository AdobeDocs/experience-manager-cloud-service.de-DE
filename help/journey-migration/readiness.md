---
title: Bereitschaftsphase
description: Erfahren Sie mehr über die Schritte, die Sie ausführen müssen, damit Sie sicherstellen können, dass Ihre AEM-Installation bereit zum Verschieben in die Cloud ist.
exl-id: 3bc8c037-d82a-4455-bce6-3c80c359a4ae
source-git-commit: a9aa82c8258e6a5f43680069c65518093c0baf8d
workflow-type: tm+mt
source-wordcount: '2066'
ht-degree: 58%

---

# Bereitschaftsphase {#readiness-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_planning"
>title="Planen Ihrer Umstellung"
>abstract="Machen Sie sich mit AEM as a Cloud Service vertraut, bevor Sie mit der Umstellung auf Cloud Service beginnen. Überprüfen Sie die wesentlichen Änderungen, die daran vorgenommen wurden, und die Funktionen, die ersetzt oder eingestellt wurden."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=de" text="Best Practices Analyzer"

In dieser Phase der AEM as a Cloud Service Migration Journey machen Sie sich mit AEM as a Cloud Service vertraut. Sie können die wesentlichen Änderungen überprüfen, die eingeführt wurden, und verstehen, was für die Planung einer erfolgreichen Migration in die Cloud erforderlich ist.

## Ihre bisherige Tour {#story-so-far}

das vorherige Dokument, [Erste Schritte mit dem Übergang zu AEM as a Cloud Service](/help/journey-migration/getting-started.md)enthält eine Liste der Phasen, die Sie durchführen müssen, damit Sie zu AEM as a Cloud Service migrieren können. Außerdem werden die Vorteile der Migration erläutert.

## Ziel {#objective}

Dieses Dokument hilft Ihnen dabei zu verstehen, welche Faktoren Sie berücksichtigen müssen, damit Sie sicherstellen können, dass Ihre AEM-Installation bereit zum Verschieben in die Cloud ist:

* Erfahren Sie mehr über wesentliche Änderungen und veraltete Funktionen
* Erfahren Sie, wie Sie die Migration zu AEM as a Cloud Service planen

## Überprüfen Sie die wesentlichen Änderungen in der Architektur von AEM as a Cloud Service {#notable-changes-in-aem-cloud-service-architecture}

AEM as a Cloud Service bietet viele neue Funktionen und Möglichkeiten zur Verwaltung Ihrer AEM.

Neben diesen Verbesserungen gibt es mehrere Unterschiede zwischen On-Premise-Installationen von AEM und Adobe Managed Services im Vergleich zu AEM as a Cloud Service.

Die Liste der Elemente in der folgenden Tabelle ist die Teilmenge der Änderungen, die für eine Migration zu AEM as a Cloud Service am relevantesten sind. Die vollständige Liste der wesentlichen Änderungen finden Sie [hier](/help/release-notes/aem-cloud-changes.md).

<table>
<thead>
  <tr>
    <th>Was hat sich geändert?</th>
    <th>Verweis</th>
    <th>Wichtige Vorteile</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Trennen veränderlicher und unveränderlicher Filter in entsprechende Pakete</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes.html?lang=de">Wesentliche Änderungen in AEM as a Cloud Service</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html#mutable-vs-immutable">AEM-Projektstruktur für AEM as a Cloud Service</a></td>
    <td>Ein einzelnes Paket, das in AEM as a Cloud Service bereitgestellt werden kann, kann Unterpakete enthalten, die in erster Linie veränderliche und unveränderliche Inhalte enthalten, die in eigene Pakete unterteilt sind.</td>
  </tr>
  <tr>
    <td>Repo Init</td>
    <td><a href="https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language">Dokumentation zu Apache Sling RepoInit</a></td>
    <td>Repoinit-Skripte sind die Best Practice zum Erstellen von anfänglichen Knotenstrukturen, Benutzern, Gruppen oder Dienstbenutzern. Da diese Skripte im Ausführungsmodus aufgerufen werden können und über die Bereitstellung von Code-Paketen verwaltbar sind, bieten sie viel Flexibilität für Repository-Initialisierungsaufgaben.</td>
  </tr>
  <tr>
    <td>Benutzerdefinierte Ausführungsmodi sind nicht zulässig</td>
    <td></td>
    <td>Es werden nur Ausführungsmodi unterstützt, die standardmäßig mit AEM as a Cloud Service bereitgestellt werden.<br>Wenn zusätzliche Entwicklungsumgebungen hinzugefügt werden, sind alle mit dem Ausführungsmodus "dev"verknüpft.</td>
  </tr>
  <tr>
    <td>Die Cloud Manager-Pipeline-Ausführung ist die einzige Möglichkeit zur Bereitstellung</td>
    <td></td>
    <td>In AEM as a Cloud Service ist der Zugriff auf „/system/console“ nicht zulässig. Daher müssen alle OSGi-Konfigurationen Teil des Codes sein und als Code bereitgestellt werden.<br>Die OSGi-Konfigurationen sind im schreibgeschützten Modus verfügbar und können über die Entwicklerkonsole über Cloud Manager angezeigt werden</td>
  </tr>
  <tr>
    <td>Replikationsagenten werden durch Sling-Inhaltsverteilung ersetzt</td>
    <td></td>
    <td>Das Konzept des Replikationsagenten wird durch Sling-Inhaltsverteilung ersetzt. Wenn es Anpassungen gibt, die Replikationsagenten verwenden, müssen diese neu gestaltet werden.<br>Rückwärtsreplikation wird nicht unterstützt</td>
  </tr>
  <tr>
    <td>CRX/DE und Package Manager</td>
    <td></td>
    <td>CRX/DE ist nur in der Entwicklungsumgebung zulässig.<br>Package Manager ist für alle Autoreninstanzen verfügbar. Die bereitzustellenden Pakete dürfen jedoch nur veränderliche Inhalte enthalten ( z. B.: /content oder /conf)</td>
  </tr>
  <tr>
    <td>Integriertes CDN und Abrufen eines eigenen CDN </td>
    <td></td>
    <td>AEM as a Cloud Service umfasst das CDN für alle Umgebungen, das für die meisten Anwendungsfälle optimiert ist.<br>Wenn Sie Ihr eigenes CDN einrichten möchten, müssen Sie eine Anfrage an den Adobe Support senden, damit es genehmigt werden kann.<br>Wenn es genehmigt ist, verweist das CDN auf Fastly und nicht auf Instanzen in Umgebungen AEM.</td>
  </tr>
  <tr>
    <td>Lang laufende Aufträge</td>
    <td></td>
    <td>Vermeiden Sie Aufträge mit langer Laufzeit wie Sling Scheduler- oder Cron-Aufträge, da die AEM Instanzen, die in den Containern ausgeführt werden, jederzeit ausgeführt werden können.<br>Überdenken Sie diese Funktionen, damit Sie sie in Adobe Developer abladen können.</td>
  </tr>
  <tr>
    <td>Wechseln zu asynchronen Vorängen</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/asynchronous-jobs.html?lang=en#configuring-asynchronous-msm-operations">Konfigurieren asynchroner Vorgänge</a></td>
    <td>Um die Gesamtleistung Ihrer Umgebungen zu verbessern, werden bestimmte Vorgänge im asynchronen Modus ausgeführt. Die asynchronen Aufträge werden in die Warteschlange gestellt und ausgeführt, wenn Systemressourcen verfügbar sind.</td>
  </tr>
  <tr>
    <td>Token-basierte Authentifizierungs- und Integrationsstrategien</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#the-server-to-server-flow">Generieren von Zugriffs-Token für Server-seitige APIs</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=de#authentication">Tutorial zur Token-basierten Authentifizierung</a></td>
    <td>Es ist üblich, dassexterne Systeme versuchen, HTTP-Vorgänge innerhalb von AEM auszuführen.<br>Es wird empfohlen, die hier beschriebenen Strategien zu implementieren, anstatt sich auf die Erstellung lokaler Benutzernamen mit Passwörtern in AEM zu verlassen.</td>
  </tr>
  <tr>
    <td>Datei-IO/Festplattenauslastung</td>
    <td></td>
    <td>Es gibt keine Garantie dafür, wie viel Festplattenspeicher zugewiesen wird, und die Instanzen in Containern kommen und gehen. Daher ist es nicht ratsam, Datei-I/O-Vorgänge zu verwenden, um von der Festplatte zu schreiben oder zu lesen, die mit der AEM-Instanz verbunden ist.</td>
  </tr>
  <tr>
    <td>Workflow „DAM-Update-Asset“</td>
    <td><a href="https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html?lang=de">Asset Compute Service</a></td>
    <td>Die Medienverarbeitungsschritte, die Teil des Workflows „DAM-Update-Asset“ sind, werden jetzt durch den Asset Compute Service ersetzt</td>
  </tr>
  <tr>
    <td>Asset-Upload-Methoden und unterstützte Workflow-Prozessschritte in AEM as a Cloud Service</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/developer-reference-material-apis.html?lang=en#post-processing-workflows-steps">Hochladen von API-Vergleichen und unterstützten WF-Prozessschritten</a></td>
    <td>In AEM as a Cloud Service werden Assets entweder beim Hochladen oder Herunterladen eines Assets direkt in den oder aus dem Binärspeicher übertragen. <br>Nicht alle Workflow-Prozessschritte werden in AEMaaCS unterstützt.</td>
  </tr>
  <tr>
    <td>Workflow-Starter</td>
    <td></td>
    <td>Entfernen Sie alle Workflow-Starter, die vordefinierten oder benutzerdefinierten Workflow "DAM-Update-Asset"auslösen, aus Ihrem Code. <br>Alle Assets, die in AEM as a Cloud Service hochgeladen wurden, werden vom Asset Processing Service verarbeitet. Informationen zu benutzerdefinierten Schritten finden Sie unter <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use.html?lang=de#post-processing-workflows"> Nachbearbeitungs-Workflows</a> Informationen zum Einrichten und Konfigurieren von Nachbearbeitungs-Workflows.</td>
  </tr>
  <tr>
    <td>Schritte für benutzerdefinierte Ausgabedarstellungen</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use.html?lang=de">Verarbeitungsprofile</a></td>
    <td>Alle benutzerdefinierten Ausgabedarstellungs-, Bildkonvertierungs- oder Videokodierungen müssen durch Erstellen entsprechender Verarbeitungsprofile in den Asset-Verarbeitungsdienst abgeladen werden.</td>
  </tr>
  <tr>
    <td>Inhaltssuche und -indizierung</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=de">Inhaltssuche und Indizierung von Änderungen</a></td>
    <td>Die zugrunde liegende Verarbeitung von Indizes und der Zeitpunkt, zu dem sie eingeführt wird, haben sich erheblich verändert.<br>Machen Sie sich mit den Oak-Indizes vollständig vertraut und refaktorieren Sie sie, bevor Sie sie in dem von Ihnen bereitgestellten Code verwalten.</td>
  </tr>
  <tr>
    <td>Es sind nicht alle Wartungsaufgaben konfigurierbar</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/maintenance.html?lang=en">Wartungsaufgaben in AEM as a Cloud Service</a></td>
    <td>Sie können nur bestimmte Wartungsaufgaben mit AEM as a Cloud Service konfigurieren.</td>
  </tr>
  <tr>
    <td>Änderungen am Veröffentlichungs-Repository</td>
    <td></td>
    <td>Direkte Änderungen am Publish-Repository sind nicht zulässig, mit Ausnahme der Änderungen unter /home. Es wird immer empfohlen, dass alle Änderungen, die an der Autoreninstanz vorgenommen werden, verteilt werden. Alle Code- und Konfigurationsänderungen müssen über die entsprechende Cloud Manager-Pipeline bereitgestellt werden.</td>
  </tr>
  <tr>
    <td>Dispatcher-Konfigurationen und Caching</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html?lang=de">Dispatcher in der Cloud</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/caching.html?lang=en#other-content">Cache-Verwaltung<br></td>
    <td>Die Dispatcher-Konfigurationen müssen einer bestimmten Struktur entsprechen.<br>Die Konfigurationen müssen als Teil des Codes verwaltet und über die Cloud Manager-Pipeline bereitgestellt werden.</td>
  </tr>
  <tr>
    <td>Sichern und Wiederherstellen</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/backup.html?lang=de">AEM as a Cloud Service – Sichern und Wiederherstellen</a></td>
    <td></td>
  </tr>
  <tr>
    <td>Änderungen an der Authentifizierung</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html?lang=de">IMS-Unterstützung für AEM as a Cloud Service</td>
    <td>Wenn Sie zuvor die SAML 2.0-Integration sowohl für Autoren- als auch Veröffentlichungsinstanz verwendet haben, bevor Sie zu Cloud Service wechseln, besteht die Hauptänderung darin, dass AEM as a Cloud Service Autoreninstanz nur mit Adobe IMS integriert wird. AEM as a Cloud Service Veröffentlichungsstufe kann jedoch weiterhin SAML oder andere Authentifizierungsintegrationen verwenden. AEM as a Cloud Service bietet IMS-Authentifizierungsunterstützung nur für Autoren-, Admin- und Entwickler-Benutzer. Die IMS-Authentifizierung bietet keine Unterstützung für externe Endbenutzer von Kunden-Sites wie Site-Besucher.</td>
  </tr>
</tbody>
</table>

## Veraltete Funktionen {#deprecated-features}

Adobe evaluiert fortlaufend Produktfunktionen, um ältere Features zu überarbeiten oder durch modernere Alternativen zu ersetzen und so den Nutzen für die Kunden insgesamt zu verbessern, wobei stets auf Abwärtskompatibilität geachtet wird.

Adobe empfiehlt Ihnen, [Eingestellte Funktionen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/deprecated-removed-features.html#deprecated-features) , um sich mit den Funktionen und Leistungsmerkmalen vertraut zu machen, die in Experience Manager as a Cloud Service als veraltet gekennzeichnet sind. Erfahren Sie, welche Auswirkungen dies auf Ihre AEM-Implementierung hat.

## Planen einer Überprüfung Ihrer AEM-Installation {#review-planning}

Nachdem Sie sich mit den mit AEM as a Cloud Service eingeführten Änderungen vertraut gemacht haben, ist es an der Zeit, mit der Planung einer Überprüfung Ihrer bestehenden Installation zu beginnen. Auf diese Weise können Sie den Grad der Änderungen messen, die erforderlich sind, um sie in die Cloud zu verschieben.

Die folgende Abbildung zeigt die wichtigsten Schritte der Planungsphase:

![image](/help/journey-migration/assets/planning-phaseimg1.png)

Als Nächstes erfahren Sie im Detail, was jeder dieser Schritte bedeutet.

### Bewerten der Cloud Service-Bereitschaft {#assess-cloud-readiness}

Der erste Schritt besteht darin, Ihre Bereitschaft zu bewerten, von Ihrer bestehenden AEM auf den Cloud Service umzustellen, und Bereiche zu bestimmen, die eine Umgestaltung erfordern, um mit AEM as a Cloud Service kompatibel zu sein.

Nehmen Sie eine umfassende Bewertung Ihres aktuellen AEM-Quellcodes anhand der wesentlichen Änderungen und veralteten Funktionen vor, um den für die Journey erwarteten Aufwand zu bestimmen.

Die Anzahl der Ergebnisse kann sich direkt auf die Zeitpläne und den Gesamterfolg des Projekts auswirken. Daher empfiehlt Adobe, so viel wie möglich zu entdecken, damit Sie den Versand planen können. Oder initiieren Sie die Gespräche, damit Sie alle Anpassungen neu gestalten können, die erforderlich sind, um AEM as a Cloud Service Best Practice zu entsprechen.

**Best Practice Analyzer**

Sie können die Bewertung beschleunigen, indem Sie Best Practices Analyzer für Ihre aktuelle AEM-Version ausführen. Ein gutes Verständnis dessen, wie alles funktioniert, ist entscheidend, um Ihre Bewertungsplanung zu beschleunigen.

Informationen zur Funktionsweise finden Sie in der Dokumentation zu [Best Practices Analyzer](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md).

**Erstellen eines Berichts zur Bewertung der Bereitschaft für die Cloud**

Der nächste Schritt besteht darin, einen Bericht zu erstellen, der auf den bisherigen Erkenntnissen basiert. Sie erstellen den Bericht, indem Sie Best Practices Analyzer-Berichte aus den Staging- und Produktionsinstanzen generieren. [laden Sie sie dann in Cloud Acceleration Manager hoch.](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#readiness-phase-cam) für einen verdaulichen Bericht mit verwertbaren Elementen.

Ein typischer Bericht sollte die folgenden Eingaben enthalten:

* Dokumentation mit Details zum Funktionssatz Ihrer jeweiligen AEM-Installation
* Details zu Ihren benutzerdefinierten AEM-Konfigurationen und zum Code
* Produktions-Dispatcher-Konfigurationen
* CDN-Konfigurationen (falls vorhanden)

**Verteilen des Berichts**

Nachdem die Best Practices Analyzer-Berichte abgeschlossen sind, teilen Sie sie mit den entsprechenden Teams mit, damit Sie Ihre Ergebnisse bestätigen und die nächsten Schritte planen können. Je nach Vorlieben können Sie auch eine gedruckte Version des Berichts verteilen, indem Sie die [Druckvorschau](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#print-preview-cam) verwenden.

### Überprüfen der Ressourcenplanung {#review-resource-planning}

Nachdem Sie den für die Umstellung auf Cloud Service erforderlichen Arbeitsaufwand geschätzt haben, sollten Sie Ressourcen identifizieren, ein Team bilden und Rollen und Verantwortlichkeiten für die Umstellung zuordnen.

### Festlegen von KPIs {#establish-kpis}

Wenn Sie zuvor noch keine Bewertungsparameter (Key Performance Indicators, KPIs) festgelegt haben, wird empfohlen, KPIs für Ihre AEM-Implementierung festzulegen, damit sich Ihr Team auf das Wesentliche konzentrieren kann.

Siehe [Entwickeln von KPIs](https://experienceleague.adobe.com/welcome/aem/part6.html?lang=de) damit Sie lernen können, wie Sie die richtigen KPIs für Ihre Geschäftsziele auswählen können.

## Wie geht es weiter {#what-is-next}

Sobald Sie den Umfang der Änderungen kennen, die erforderlich sind, um zu AEM as a Cloud Service zu wechseln, ist es an der Zeit, [Code und Inhalte für die Cloud vorzubereiten](/help/journey-migration/implementation.md), bevor Sie die Migration tatsächlich durchführen.

## Zusätzliche Ressourcen {#additional-resources}

* [Erste Schritte mit Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/using-cam/getting-started-cam.md) – Eine umfassende Anleitung zur Verwendung von Cloud Acceleration Manager, um den Wechsel zur Cloud zu beschleunigen.
* [AEM as a Cloud Service: Einführung, Architektur und Denken unterschiedlich](https://experienceleague.adobe.com/?launch=ExperienceManager-D-1-2021.1.migration&amp;recommended=ExperienceManager-D-1-2021.1.migration&amp;lang=de#dashboard/learning)
* [Startseite von AEM as a Cloud Service](/help/overview/home.md) – Beginnen Sie hier, um einen Überblick über die Dokumentation zu Experience Manager as a Cloud Service zu erhalten.
* [Überblick über AEM as a Cloud Service](/help/overview/home.md) – Dieses Handbuch bietet einen Überblick über Experience Manager as a Cloud Service, einschließlich Einführung, Terminologie und Architektur.
* [Onboarding-Tour](/help/journey-onboarding/overview.md) – Dieses Handbuch bietet eine Zusammenfassung der ersten Schritte mit Experience Manager as a Cloud Service, einschließlich der Zugriffsmöglichkeiten und der Einrichtung des Teams..
