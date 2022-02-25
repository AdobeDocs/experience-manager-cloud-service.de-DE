---
title: Bereitschaftsphase
description: Erfahren Sie mehr über die Schritte, die Sie ausführen müssen, um sicherzustellen, dass Ihre AEM-Installation bereit zum Verschieben in die Cloud ist.
source-git-commit: d851ca19070232e1d43f5c5e546d4174e2c310a2
workflow-type: tm+mt
source-wordcount: '2078'
ht-degree: 10%

---

# Bereitschaftsphase {#readiness-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_planning"
>title="Planen Ihrer Umstellung"
>abstract="Bevor Sie mit der Umstellung auf Cloud Service beginnen, sollten Sie sich mit AEM as a Cloud Service vertraut machen und die wichtigen Änderungen und Funktionen einsehen, die ersetzt oder eingestellt wurden."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=de" text="Best Practices Analyzer"

In dieser Phase der Journey zur AEM as a Cloud Service Migration werden Sie sich mit AEM as a Cloud Service vertraut machen, die wesentlichen Änderungen, die eingeführt wurden, überprüfen und verstehen, was für die Planung einer erfolgreichen Migration in die Cloud erforderlich ist.

## Die bisherige Entwicklung {#story-so-far}

das vorherige Dokument, [Erste Schritte mit dem Übergang zu AEM as a Cloud Service](/help/journey-migration/getting-started.md)enthält eine Liste der Phasen, die Sie durchführen müssen, um zu AEM as a Cloud Service zu migrieren, sowie die Vorteile, die dies mit sich bringt.

## Ziel {#objective}

In diesem Dokument erfahren Sie, welche Faktoren Sie berücksichtigen müssen, um sicherzustellen, dass Ihre AEM-Installation bereit zum Verschieben in die Cloud ist:

* Erfahren Sie mehr über wichtige Änderungen und veraltete Funktionen
* Erfahren Sie, wie Sie die Migration auf AEM as a Cloud Service planen.

## Überprüfen Sie die wesentlichen Änderungen in der AEM as a Cloud Service Architektur. {#notable-changes-in-aem-cloud-service-architecture}

AEM as a Cloud Service bietet viele neue Funktionen und Möglichkeiten zur Verwaltung Ihrer AEM-Projekte.

Neben diesen Verbesserungen wurden mehrere Unterschiede zwischen On-Premise-Installationen von AEM und Adobe Managed Services im Vergleich zu AEM as a Cloud Service eingeführt.

Die Liste der Elemente in der folgenden Tabelle ist die Teilmenge der Änderungen, die für eine Migration am relevantesten AEM as a Cloud Service sind. Die vollständige Liste der wesentlichen Änderungen finden Sie hier . [here](/help/release-notes/aem-cloud-changes.md).

<table>
<thead>
  <tr>
    <th>Was hat sich geändert?</th>
    <th>Verweis</th>
    <th>Wichtige Takeaways</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Trennen Sie veränderliche und unveränderliche Filter in entsprechende Pakete.</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/aem-cloud-changes.html?lang=de">AEM as a Cloud Service wesentlichen Änderungen</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html#mutable-vs-immutable">AEM Projektstruktur für AEM as a Cloud Service</a></td>
    <td>Ein einzelnes Paket, das in AEM as a Cloud Service bereitgestellt werden kann, kann Unterpakete enthalten, die in erster Linie veränderliche und unveränderliche Inhalte enthalten, die in eigene Pakete unterteilt sind.</td>
  </tr>
  <tr>
    <td>Repo Init</td>
    <td><a href="https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language">Dokumentation zu Apache Sling RepoInit</a></td>
    <td>Repoinit-Skripte sind die Best Practice zum Erstellen von anfänglichen Knotenstrukturen, Benutzern, Gruppen oder Dienstbenutzern. Da diese Skripte auf den Ausführungsmodus ausgerichtet und über die Bereitstellung von Code-Paketen verwaltbar sind, bieten sie viel Flexibilität, um Repository-Initialisierungsaufgaben zu erledigen.</td>
  </tr>
  <tr>
    <td>Benutzerdefinierte Ausführungsmodi sind nicht zulässig</td>
    <td></td>
    <td>Es werden nur Ausführungsmodi unterstützt, die standardmäßig mit AEM as a Cloud Service bereitgestellt werden.<br>Wenn zusätzliche Entwicklungsumgebungen hinzugefügt werden, sind alle mit dem Ausführungsmodus "dev"verknüpft.</td>
  </tr>
  <tr>
    <td>Die Cloud Manager-Pipeline-Ausführung ist die einzige Möglichkeit zur Bereitstellung</td>
    <td></td>
    <td>In AEM as a Cloud Service ist der Zugriff auf /system/console nicht erlaubt. Daher müssen alle OSGi-Konfigurationen Teil des Codes sein und als Code bereitgestellt werden.<br>Die OSGi-Konfigurationen sind im schreibgeschützten Modus verfügbar und können über die Developer Console über Cloud Manager angezeigt werden.</td>
  </tr>
  <tr>
    <td>Replikationsagenten werden durch Sling Content Distribution ersetzt.</td>
    <td></td>
    <td>Das Konzept des Replikationsagenten wird durch Sing Content Distribution ersetzt. Wenn es Anpassungen gibt, die Replikationsagenten nutzen, müssen diese neu gestaltet werden.<br>Rückwärtsreplikation wird nicht unterstützt</td>
  </tr>
  <tr>
    <td>CRX/DE und Package Manager</td>
    <td></td>
    <td>CRX/DE ist nur in der Entwicklungsumgebung zulässig.<br>Der Package Manager ist für alle Autoreninstanzen verfügbar. Die bereitzustellenden Pakete dürfen jedoch nur veränderliche Inhalte enthalten ( z. B.: /content oder /conf)</td>
  </tr>
  <tr>
    <td>Entwickelt in CDN und eigene CDN abrufen</td>
    <td></td>
    <td>AEM as a Cloud Service umfasst das CDN für alle Umgebungen, das für die meisten Anwendungsfälle optimiert ist.<br>Wenn Sie Ihr eigenes CDN einrichten möchten, müssen Sie eine Anfrage an den Adobe Support senden, damit es genehmigt werden kann.<br>Wenn es genehmigt ist, verweist das CDN auf Fastly und nicht auf Instanzen in Umgebungen AEM.</td>
  </tr>
  <tr>
    <td>Lang laufende Aufträge</td>
    <td></td>
    <td>Vermeiden Sie die Ausführung langwieriger Aufträge wie Sling Scheduler- oder Cron-Aufträge, da die AEM Instanzen, die in den Containern ausgeführt werden, jederzeit ausgeführt werden können.<br>Überdenken Sie diese Funktionen neu, um sie in die Adobe I/O zu laden.</td>
  </tr>
  <tr>
    <td>Zu "Asynchrone Vorgänge"wechseln</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/asynchronous-jobs.html?lang=en#configuring-asynchronous-msm-operations">Konfigurieren asynchroner Vorgänge</a></td>
    <td>Um die Gesamtleistung Ihrer Umgebungen zu verbessern, werden bestimmte Vorgänge im asynchronen Modus ausgeführt. Die asynchronen Aufträge werden in die Warteschlange gestellt und ausgeführt, wenn Systemressourcen verfügbar sind.</td>
  </tr>
  <tr>
    <td>Token-basierte Authentifizierungs- und Integrationsstrategien</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#the-server-to-server-flow">Generieren von Zugriffstoken für serverseitige APIs</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=de#authentication">Tutorial zur Token-basierten Authentifizierung</a></td>
    <td>Es ist üblich, dass externe Systeme versuchen, HTTP-Vorgänge innerhalb von AEM auszuführen.<br>Es wird empfohlen, die hier beschriebenen Strategien zu implementieren, anstatt sich auf die Erstellung lokaler Benutzernamen mit Passwörtern in AEM zu verlassen.</td>
  </tr>
  <tr>
    <td>Datei-IO/Festplattenauslastung</td>
    <td></td>
    <td>Da nicht garantiert ist, wie viel Festplattenspeicher zugewiesen wird und die Instanzen in Containern kommen und gehen, ist es nicht ratsam, Datei-I/O-Vorgänge zu verwenden, um von der Festplatte zu schreiben oder zu lesen, die an die AEM-Instanz angehängt ist.</td>
  </tr>
  <tr>
    <td>DAM-Update-Asset-Workflow</td>
    <td><a href="https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html?lang=en">Asset Compute Service</a></td>
    <td>Die Medienverarbeitungsschritte, die Teil des Workflows "DAM-Update-Asset"sind, werden jetzt durch den Asset compute-Service ersetzt</td>
  </tr>
  <tr>
    <td>Asset-Upload-Methoden und unterstützte Workflow-Prozessschritte in AEM as a Cloud Service</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/developer-reference-material-apis.html?lang=en#post-processing-workflows-steps">Hochladen von API-Vergleichen und unterstützten WF-Prozessschritten</a></td>
    <td>In AEM as a Cloud Service Fällen werden Assets entweder beim Hochladen oder Herunterladen eines Assets direkt in den binären Speicher oder aus dem Binärspeicher übertragen.</br>Nicht alle Workflow-Prozessschritte werden in AEMaaCS unterstützt.</td>
  </tr>
  <tr>
    <td>Workflow-Starter</td>
    <td></td>
    <td>Entfernen Sie alle Workflow-Starter, die einen OOTB- oder benutzerdefinierten DAM Update Asset Workflow auslösen.</br>Alle Assets, die in AEM as a Cloud Service hochgeladen wurden, werden vom Asset-Verarbeitungsdienst verarbeitet. Informationen zu benutzerdefinierten Schritten finden Sie unter <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use.html?lang=en#post-processing-workflows"> Nachbearbeitungs-Workflows</a> Informationen zum Einrichten und Konfigurieren von Nachbearbeitungs-Workflows.</td>
  </tr>
  <tr>
    <td>Schritte für benutzerdefinierte Ausgaben</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/asset-microservices-configure-and-use.html?lang=en#manage">Verarbeitungsprofile</a></td>
    <td>Jede benutzerdefinierte Ausgabegenerierung, Bildkonvertierung oder Videokodierung muss durch Erstellen entsprechender Verarbeitungsprofile in den Asset-Verarbeitungsdienst abgeladen werden.</td>
  </tr>
  <tr>
    <td>Inhaltssuche und -indizierung</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en">Änderungen bei der Inhaltssuche und -indizierung</a></td>
    <td>Die zugrunde liegende Verarbeitung von Indizes und der Zeitpunkt, zu dem sie eingeführt wird, sind erheblich verändert.<br>Machen Sie sich mit den Oak-Indizes vollständig vertraut und refaktorieren Sie sie, bevor Sie sie in dem Code verwalten, den Sie bereitstellen werden.</td>
  </tr>
  <tr>
    <td>Es sind nicht alle Wartungsaufgaben konfigurierbar</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/maintenance.html?lang=en">AEM as a Cloud Service Wartungsaufgaben</a></td>
    <td>Sie können nur bestimmte Wartungsaufgaben mit AEM as a Cloud Service konfigurieren.</td>
  </tr>
  <tr>
    <td>Änderungen am Publishing-Repository</td>
    <td></td>
    <td>Direkte Änderungen am Publish-Repository sind nicht zulässig, mit Ausnahme der Änderungen unter /home. Es wird immer empfohlen, die Änderungen an der Autoreninstanz vorzunehmen und sie zu verteilen. Alle Code- und Konfigurationsänderungen müssen über die entsprechende Cloud Manager-Pipeline bereitgestellt werden.</td>
  </tr>
  <tr>
    <td>Dispatcher-Konfigurationen und Caching</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=de#content-delivery">Dispatcher in der Cloud</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/caching.html?lang=en#other-content">Cacheverwaltung<br></td>
    <td>Die Dispatcher-Konfigurationen müssen einer bestimmten Struktur entsprechen.<br>Die Konfigurationen müssen als Teil des Codes verwaltet und über die Cloud Manager-Pipeline bereitgestellt werden.</td>
  </tr>
  <tr>
    <td>Sichern und Wiederherstellen</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/backup.html?lang=en">as a Cloud Service Sicherung und Wiederherstellung AEM</a></td>
    <td></td>
  </tr>
  <tr>
    <td>Änderungen an der Authentifizierung</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html?lang=en">IMS-Unterstützung für AEM as a Cloud Service</td>
    <td>Wenn Sie zuvor die SAML 2.0-Integration sowohl für die Autoren- als auch für die Veröffentlichungsinstanz verwendet haben, bevor Sie zu Cloud Service wechseln, besteht die Hauptänderung darin, dass AEM as a Cloud Service Autoreninstanz nur mit Adobe IMS integriert wird. AEM as a Cloud Service Veröffentlichungsstufe kann jedoch weiterhin SAML- oder andere Authentifizierungsintegrationen nutzen. AEM as a Cloud Service bietet IMS-Authentifizierungsunterstützung nur für Autoren-, Admin- und Entwicklungsbenutzer. Die IMS-Authentifizierung bietet keine Unterstützung für externe Endbenutzer von Kunden-Sites wie Site-Besucher.</td>
  </tr>
</tbody>
</table>

## Veraltete Funktionen {#deprecated-features}

Adobe evaluiert fortlaufend Produktfunktionen, um ältere Features zu überarbeiten oder durch modernere Alternativen zu ersetzen und so den Nutzen für die Kunden insgesamt zu verbessern, wobei stets auf Abwärtskompatibilität geachtet wird.

Wir empfehlen Ihnen, die [Eingestellte Funktionen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/deprecated-removed-features.html?lang=de#deprecated-features) , um sich mit den Funktionen und Leistungsmerkmalen vertraut zu machen, die in Experience Manager as a Cloud Service als veraltet gekennzeichnet wurden, und zu sehen, welche Auswirkungen dies auf Ihre AEM-Implementierung hat.

## Planen Sie eine Überprüfung Ihrer AEM Installation. {#review-planning}

Sobald Sie sich mit den mit AEM as a Cloud Service eingeführten Änderungen vertraut gemacht haben, ist es an der Zeit, mit der Planung einer Überprüfung Ihrer bestehenden Installation zu beginnen, um abzuschätzen, wie viele Änderungen erforderlich sind, um sie in die Cloud zu verschieben.

Die folgende Abbildung zeigt die wichtigsten Schritte, die während der Überprüfungsphase durchgeführt wurden:

![image](/help/journey-migration/assets/planning-phaseimg1.png)

Als Nächstes werden wir im Einzelnen untersuchen, was jeder dieser Schritte bedeutet.

### Bewerten der Cloud Service-Bereitschaft {#assess-cloud-readiness}

Der erste Schritt besteht darin, Ihre Bereitschaft zu bewerten, von Ihrer bestehenden AEM auf den Cloud Service umzustellen, und Bereiche zu bestimmen, die eine Umgestaltung erfordern, um mit AEM as a Cloud Service kompatibel zu sein.

Sie müssen eine umfassende Bewertung Ihres aktuellen AEM-Quellcodes anhand der wesentlichen Änderungen und veralteten Funktionen vornehmen, um den für die Journey erwarteten Aufwand zu bestimmen.

Die Anzahl der Ergebnisse wird sich direkt auf die Zeitpläne und den Gesamterfolg des Projekts auswirken. Es wird daher empfohlen, den Versand so weit wie möglich zu planen oder die Gespräche einzuleiten, die zur Neugestaltung aller Anpassungen erforderlich sind, um AEM as a Cloud Service Best Practice zu entsprechen.

**Best Practice Analyzer**

Sie können die Bewertung beschleunigen, indem Sie den Best Practices Analyzer für Ihre aktuelle AEM ausführen. Ein gutes Verständnis dessen, wie es funktioniert, ist entscheidend, um Ihre Bewertungsplanung zu beschleunigen.

Lesen Sie die Funktionsweise des Programms, indem Sie die [Best Practices Analyzer](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md) Dokumentation.

**Erstellen eines Cloud Readiness Assessment-Berichts**

Der nächste Schritt besteht darin, einen Bericht zu erstellen, der sich auf die bisher gesammelten Erkenntnisse stützt. Sie können dies erreichen, indem Sie Best Practices Analyzer-Berichte aus den Staging- und Produktionsinstanzen generieren. [dann in Cloud Acceleration Manager hochladen](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#readiness-phase-cam) für einen verdaulichen Bericht mit verwertbaren Elementen.

Ein typischer Bericht sollte die folgenden Eingaben enthalten:

* Dokumentation mit Details zum Funktionssatz Ihrer jeweiligen AEM Installation
* Details zu Ihren AEM benutzerdefinierten Konfigurationen und Code
* Produktions-Dispatcher-Konfigurationen
* CDN-Konfigurationen (falls vorhanden)

**Bericht sozialisieren**

Nachdem die Best Practices Analyzer-Berichte abgeschlossen sind, teilen Sie sie mit den entsprechenden Teams mit, um Ihre Ergebnisse zu bestätigen und die nächsten Schritte zu planen. Je nach Voreinstellung können Sie auch eine gedruckte Version des Berichts verteilen, indem Sie [Druckvorschau](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#print-preview-cam).

### Überprüfen der Ressourcenplanung {#review-resource-planning}

Nachdem Sie den für die Umstellung auf Cloud Service erforderlichen Aufwand geschätzt haben, sollten Sie Ressourcen identifizieren, ein Team erstellen und Rollen und Verantwortlichkeiten für den Übergangsprozess zuordnen.

### Festlegen von KPIs {#establish-kpis}

Wenn Sie zuvor noch keine KPIs (Key Performance Indicators) festgelegt haben, wird empfohlen, KPIs für Ihre AEM-Implementierung zu erstellen, damit sich Ihr Team auf das Wesentliche konzentrieren kann.

Siehe [Entwickeln von KPIs](https://guided.adobe.com/welcome/aem/part6.html) um zu erfahren, wie Sie die richtigen KPIs für Ihre Geschäftsziele auswählen.

## Wie geht es weiter {#what-is-next}

Sobald Sie den Umfang der Änderungen kennen, die erforderlich sind, um zu AEM as a Cloud Service zu wechseln, ist es an der Zeit, [Bereiten Sie Code und Content Cloud bereit](/help/journey-migration/implementation.md) bevor Sie die Migration tatsächlich durchführen.

## Zusätzliche Ressourcen {#additional-resources}

* [Erste Schritte mit Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/using-cam/getting-started-cam.md) - Eine umfassende Anleitung zur Verwendung von Cloud Acceleration Manager, um den Wechsel zur Cloud zu beschleunigen
* [AEM as a Cloud Service: Einführung, Architektur und Denken - unterschiedlich](https://experienceleague.adobe.com/?launch=ExperienceManager-D-1-2021.1.migration&amp;recommended=ExperienceManager-D-1-2021.1.migration&amp;lang=en#dashboard/learning)
* [Cloud Service-Homepage AEM](/help/overview/home.md) - Beginnen Sie hier, um einen Überblick über die as a Cloud Service Dokumentation zu Experience Manager zu erhalten.
* [AEM as a Cloud Service Übersicht](/help/overview/home.md) - Dieses Handbuch bietet einen Überblick über Experience Manager as a Cloud Service, einschließlich Einführung, Terminologie und Architektur.
* [Onboarding](/help/onboarding/home.md)- Dieses Handbuch bietet eine Zusammenfassung der ersten Schritte mit Experience Manager as a Cloud Service, einschließlich der Möglichkeiten für den Zugriff und die Einrichtung Ihres Teams
