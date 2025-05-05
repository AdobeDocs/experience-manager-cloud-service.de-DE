---
title: Bereitschaftsphase
description: Erfahren Sie mehr über die Schritte, die Sie ausführen müssen, um sicherzustellen, dass Ihre AEM-Installation bereit zum Verschieben in die Cloud ist.
exl-id: 3bc8c037-d82a-4455-bce6-3c80c359a4ae
feature: Migration
role: Admin
source-git-commit: 1683d53491e06ebe2dfcc96184ce251539ecf732
workflow-type: tm+mt
source-wordcount: '1915'
ht-degree: 100%

---

# Bereitschaftsphase {#readiness-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_planning"
>title="Planen Ihrer Umstellung"
>abstract="Machen Sie sich mit AEM as a Cloud Service vertraut, bevor Sie mit der Umstellung auf Cloud Service beginnen. Betrachten Sie die wesentlichen Änderungen, die daran vorgenommen wurden, und die Funktionen, die ersetzt oder eingestellt wurden."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=de" text="Best Practices Analyzer"

In dieser Phase der AEM as a Cloud Service-Migrations-Tour machen Sie sich mit AEM as a Cloud Service vertraut. Sie können die wesentlichen Änderungen Revue passieren lassen, die eingeführt wurden, und verstehen, was für die Planung einer erfolgreichen Migration in die Cloud erforderlich ist.

## Die bisherige Entwicklung {#story-so-far}

Das vorherige Dokument [Einstieg in die Migration zu AEM as a Cloud Service](/help/journey-migration/getting-started.md) enthält eine Liste von Phasen, die Sie durchlaufen müssen, damit Sie zu AEM as a Cloud Service migrieren können. Außerdem werden die Vorteile der Migration erläutert.

## Ziel {#objective}

In diesem Dokument erfahren Sie, welche Faktoren Sie berücksichtigen müssen, um sicherzustellen, dass Ihre AEM-Installation bereit für die Migration in die Cloud ist:

* Erfahren Sie mehr über wesentliche Änderungen und veraltete Funktionen
* Erfahren Sie, wie Sie die Migration zu AEM as a Cloud Service planen

## Überprüfen Sie die wesentlichen Änderungen in der Architektur von AEM as a Cloud Service {#notable-changes-in-aem-cloud-service-architecture}

AEM as a Cloud Service bietet viele neue Funktionen und Möglichkeiten zur Verwaltung Ihrer AEM-Projekte.

Neben diesen Verbesserungen gibt es mehrere Unterschiede zwischen On-Premise-Installationen von AEM und Adobe Managed Services im Vergleich zu AEM as a Cloud Service.

Die Liste der Elemente in der folgenden Tabelle ist die Teilmenge der Änderungen, die für eine Migration zu AEM as a Cloud Service am relevantesten sind. Sie können die vollständige Liste der [wesentlichen Änderungen an Adobe Experience Manager as a Cloud Service](/help/release-notes/aem-cloud-changes.md) anzeigen.

<table>
<thead>
  <tr>
    <th>Was hat sich geändert?</th>
    <th>Referenz</th>
    <th>Wichtige Vorteile</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Trennen veränderlicher und unveränderlicher Filter in entsprechende Pakete</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes.html?lang=de">Wesentliche Änderungen in AEM as a Cloud Service</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=de#mutable-vs-immutable">AEM-Projektstruktur für AEM as a Cloud Service</a></td>
    <td>Ein einzelnes Paket, das in AEM as a Cloud Service bereitgestellt werden kann, kann Unterpakete enthalten, die in erster Linie veränderliche und unveränderliche Inhalte enthalten, die in eigene Pakete unterteilt sind.</td>
  </tr>
  <tr>
    <td>Repo Init</td>
    <td><a href="https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language">Dokumentation zu Apache Sling RepoInit</a></td>
    <td>RepoInit-Skripte sind die Best Practice zum Erstellen von anfänglichen Knotenstrukturen, Benutzenden, Gruppen oder Dienstbenutzenden. Da diese Skripte im Ausführungsmodus aufgerufen werden können und über die Bereitstellung von Code-Paketen verwaltbar sind, bieten sie viel Flexibilität für Repository-Initialisierungsaufgaben.</td>
  </tr>
  <tr>
    <td>Benutzerdefinierte Ausführungsmodi sind nicht zulässig</td>
    <td></td>
    <td>Es werden nur Ausführungsmodi unterstützt, die standardmäßig mit AEM as a Cloud Service bereitgestellt werden.<br>Wenn zusätzliche Entwicklungsumgebungen hinzugefügt werden, sind diese alle mit dem Ausführungsmodus „Dev“ verknüpft.</td>
  </tr>
  <tr>
    <td>Die Cloud Manager-Pipeline-Ausführung ist die einzige Möglichkeit zur Bereitstellung</td>
    <td></td>
    <td>In AEM as a Cloud Service ist der Zugriff auf „/system/console“ nicht zulässig. Daher müssen alle OSGi-Konfigurationen Teil des Codes sein und als Code bereitgestellt werden.<br>Die OSGi-Konfigurationen sind im schreibgeschützten Modus verfügbar und können über die Entwicklerkonsole über Cloud Manager angezeigt werden</td>
  </tr>
  <tr>
    <td>Replikationsagenten werden durch Sling-Inhaltsverteilung ersetzt</td>
    <td></td>
    <td>Das Konzept des Replikationsagenten wird durch Sling-Inhaltsverteilung ersetzt. Wenn es Anpassungen gibt, die Replikationsagenten nutzen, müssen diese neu gestaltet werden.<br>Rückwärtsreplikation wird nicht unterstützt</td>
  </tr>
  <tr>
    <td>CRX/DE und Package Manager</td>
    <td></td>
    <td>CRX/DE ist nur in der Entwicklungsumgebung zulässig.<br>Package Manager ist für alle Autoreninstanzen verfügbar. Die bereitzustellenden Pakete dürfen jedoch nur veränderliche Inhalte enthalten ( z. B.: /content oder /conf)</td>
  </tr>
  <tr>
    <td>Integriertes CDN und Abrufen eines eigenen CDN </td>
    <td></td>
    <td>AEM as a Cloud Service umfasst das CDN für alle Umgebungen, das für die meisten Anwendungsfälle optimiert ist.<br>Wenn Sie Ihr eigenes CDN einrichten möchten, müssen Sie eine Anfrage an den Adobe Support senden, damit es genehmigt werden kann.<br>Wenn es genehmigt ist, verweist das CDN auf Fastly und nicht auf AEM-Instanzen in beliebigen Umgebungen.</td>
  </tr>
  <tr>
    <td>Lang laufende Aufträge</td>
    <td></td>
    <td>Vermeiden Sie lang laufende Aufträge wie Sling Scheduler oder Cron-Aufträge, da die in den Containern ausgeführten AEM-Instanzen jederzeit kommen und gehen können.<br>Überdenken Sie diese Funktionen so, dass Sie sie an Adobe Developer auslagern können.</td>
  </tr>
  <tr>
    <td>Wechseln zu asynchronen Vorgängen</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/asynchronous-jobs.html?lang=de#configuring-asynchronous-msm-operations">Konfigurieren asynchroner Vorgänge</a></td>
    <td>Um die Gesamtleistung Ihrer Umgebungen zu verbessern, werden bestimmte Vorgänge im asynchronen Modus ausgeführt. Die asynchronen Aufträge werden in die Warteschlange gestellt und ausgeführt, wenn Systemressourcen verfügbar sind.</td>
  </tr>
  <tr>
    <td>Token-basierte Authentifizierungs- und Integrationsstrategien</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=de#the-server-to-server-flow">Generieren von Zugriffs-Token für Server-seitige APIs</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=de#authentication">Tutorial zur Token-basierten Authentifizierung</a></td>
    <td>Es ist üblich, dassexterne Systeme versuchen, HTTP-Vorgänge innerhalb von AEM auszuführen.<br>Es wird empfohlen, die hier beschriebenen Strategien zu implementieren, anstatt sich auf die Erstellung lokaler Benutzernamen mit Passwörtern in AEM zu verlassen.</td>
  </tr>
  <tr>
    <td>Datei-IO/Festplattenauslastung</td>
    <td></td>
    <td>Es gibt keine Garantie dafür, wie viel Festplattenspeicher zugewiesen wird, und die Instanzen in Containern können kommen und gehen. Daher ist es nicht ratsam, Datei-E/A-Vorgänge zu verwenden, um von der Festplatte zu schreiben oder zu lesen, die mit der AEM-Instanz verbunden ist.</td>
  </tr>
  <tr>
    <td>Workflow „DAM-Update-Asset“</td>
    <td><a href="https://experienceleague.adobe.com/docs/asset-compute/using/introduction.html?lang=de">Asset Compute Service</a></td>
    <td>Die Medienverarbeitungsschritte, die Teil des Workflows „DAM-Update-Asset“ sind, werden jetzt durch den Asset Compute Service ersetzt</td>
  </tr>
  <tr>
    <td>Asset-Upload-Methoden und unterstützte Workflow-Prozessschritte in AEM as a Cloud Service</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/developer-reference-material-apis.html?lang=de#post-processing-workflows-steps">Hochladen von API-Vergleichen und unterstützten WF-Prozessschritten</a></td>
    <td>In AEM as a Cloud Service werden Assets entweder beim Hochladen oder Herunterladen eines Assets direkt in den oder aus dem Binärspeicher übertragen. <br>Nicht alle Workflow-Prozessschritte werden in AEMaaCS unterstützt.</td>
  </tr>
  <tr>
    <td>Workflow-Starter</td>
    <td></td>
    <td>Entfernen Sie alle Workflow-Launcher aus Ihrem Code, die entweder einen standardmäßigen oder einen benutzerdefinierten DAM-Update-Asset-Workflow auslösen. <br>Alle Assets, die in AEM as a Cloud Service hochgeladen wurden, werden vom Asset Processing Service verarbeitet. Informationen zu benutzerdefinierten Schritten finden Sie unter <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use.html?lang=de#post-processing-workflows"> Nachbearbeitungs-Workflows</a>, wo es um die Einrichtung und Konfiguration von Nachbearbeitungs-Workflows geht.</td>
  </tr>
  <tr>
    <td>Schritte für benutzerdefinierte Ausgabedarstellungen</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use.html?lang=de">Verarbeitungsprofile</a></td>
    <td>Jede benutzerdefinierte Ausgabegenerierung, Bildkonvertierung oder Videocodierung muss durch Erstellen entsprechender Verarbeitungsprofile in den Asset Processing Service ausgelagert werden.</td>
  </tr>
  <tr>
    <td>Inhaltssuche und -indizierung</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=de">Inhaltssuche und Indizierung von Änderungen</a></td>
    <td>Die zugrunde liegende Verarbeitung von Indizes und der Zeitpunkt, zu dem sie eingeführt wird, haben sich erheblich verändert.<br>Machen Sie sich mit den Oak-Indizes vollständig vertraut und überarbeiten Sie sie, bevor Sie sie im Code verwalten, den Sie bereitstellen.</td>
  </tr>
  <tr>
    <td>Nicht alle Wartungsaufgaben sind konfigurierbar</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/maintenance.html?lang=de">Wartungsaufgaben in AEM as a Cloud Service</a></td>
    <td>Sie können nur bestimmte Wartungsaufgaben mit AEM as a Cloud Service konfigurieren.</td>
  </tr>
  <tr>
    <td>Änderungen am Veröffentlichungs-Repository</td>
    <td></td>
    <td>Direkte Änderungen am Publish-Repository sind nicht erlaubt, mit Ausnahme von Änderungen unter „/home“. Es wird immer empfohlen, dass alle Änderungen, die an Author vorgenommen werden, verteilt werden. Alle Code- und Konfigurationsänderungen müssen über die entsprechende Cloud Manager-Pipeline bereitgestellt werden.</td>
  </tr>
  <tr>
    <td>Dispatcher-Konfigurationen und Caching</td>
    <td><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html?lang=de">Dispatcher in der Cloud</a><br><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/caching.html?lang=de#other-content">Cache-Verwaltung<br></td>
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
    <td>Wenn Sie zuvor die SAML 2.0-Integration sowohl für Author als auch für Publish verwendet haben, bevor Sie zu Cloud Service gewechselt sind, besteht die Hauptänderung darin, dass Author in AEM as a Cloud Service nur mit Adobe IMS integriert ist. Die Veröffentlichungsebene von AEM as a Cloud Service kann jedoch weiterhin SAML- oder andere Authentifizierungsintegrationen nutzen. AEM as a Cloud Service bietet IMS-Authentifizierungsunterstützung nur für Autoren-, Admin- und Entwicklungsbenutzende. Die IMS-Authentifizierung bietet keine Unterstützung für externe Endbenutzer von Kunden-Sites wie Site-Besucher.</td>
  </tr>
</tbody>
</table>

## Veraltete Funktionen {#deprecated-features}

Adobe evaluiert fortlaufend Produktfunktionen, um ältere Features zu überarbeiten oder durch modernere Alternativen zu ersetzen und so den Nutzen für die Kunden insgesamt zu verbessern, wobei stets auf Abwärtskompatibilität geachtet wird.

Adobe empfiehlt, dass Sie [Veraltete Funktionen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/deprecated-removed-features.html?lang=de#deprecated-features) konsultieren, um sich mit den Funktionen und Möglichkeiten vertraut zu machen, die in Experience Manager as a Cloud Service als veraltet gekennzeichnet sind. Erfahren Sie, welche Auswirkungen dies auf Ihre AEM-Bereitstellung hat.

## Planen einer Überprüfung Ihrer AEM-Installation {#review-planning}

Nachdem Sie sich mit den mit AEM as a Cloud Service eingeführten Änderungen vertraut gemacht haben, ist es an der Zeit, mit der Planung einer Überprüfung Ihrer bestehenden Installation zu beginnen. Auf diese Weise können Sie den Grad der Änderungen messen, die erforderlich sind, um sie in die Cloud zu verschieben.

Die folgende Abbildung zeigt die wichtigsten Schritte der Prüfphase:

![Wichtige Schritte während der Prüfphase](/help/journey-migration/assets/planning-phaseimg1.png)

Als Nächstes werden Sie im Detail untersuchen, was jeder dieser Schritte bedeutet.

### Bewerten der Cloud-Service-Bereitschaft {#assess-cloud-readiness}

Der erste Schritt besteht darin, zu beurteilen, ob Sie bereit sind, von Ihrer bestehenden AEM-Version auf den Cloud-Service umzusteigen, und die Bereiche zu bestimmen, die eine Überarbeitung erfordern, um mit AEM as a Cloud Service kompatibel zu sein.

Führen Sie eine umfassende Bewertung Ihres aktuellen AEM-Quell-Codes anhand der wichtigen Änderungen und veralteten Funktionen durch, um den für die Umstellung zu erwartenden Aufwand zu bestimmen.

Die Anzahl der Ergebnisse wird sich direkt auf die Zeitpläne und den Gesamterfolg des Projekts auswirken. Adobe empfiehlt daher, so viel wie möglich herauszufinden, damit Sie die Bereitstellung planen können. Oder initiieren Sie die Gespräche, damit Sie alle erforderlichen Anpassungen neu entwerfen können, um den Best Practices für AEM as a Cloud Service gerecht zu werden.

**Best Practice Analyzer**

Sie können die Bewertung beschleunigen, indem Sie Best Practices Analyzer für Ihre aktuelle AEM-Version ausführen. Ein gutes Verständnis dessen, wie alles funktioniert, ist entscheidend, um Ihre Bewertungsplanung zu beschleunigen.

Informationen zur Funktionsweise finden Sie in der Dokumentation zu [Best Practices Analyzer](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md).

**Erstellen eines Berichts zur Bewertung der Bereitschaft für die Cloud**

Der nächste Schritt besteht darin, einen Bericht zu erstellen, der sich auf die bisher gesammelten Erkenntnisse stützt. Sie erstellen den Bericht, indem Sie Best Practices Analyzer-Berichte aus den Staging- und Produktionsinstanzen generieren [und diese dann in Cloud Acceleration Manager hochladen](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#readiness-phase-cam), um einen verständlichen Bericht mit umsetzbaren Elementen zu erhalten.

Ein typischer Bericht sollte die folgenden Eingaben enthalten:

* Dokumentation mit Details zum Funktionssatz Ihrer jeweiligen AEM-Installation
* Details zu Ihren benutzerdefinierten AEM-Konfigurationen und zum Code
* Produktions-Dispatcher-Konfigurationen
* Domain-Zuordnungen (CDN-Konfigurationen), falls vorhanden

**Weitergeben des Berichts**

Sobald die Best Practices Analyzer-Berichte abgeschlossen sind, geben Sie sie an die entsprechenden Teams weiter, um Ihre Ergebnisse zu bestätigen und die nächsten Schritte zu planen. Je nach Vorlieben können Sie auch eine gedruckte Version des Berichts verteilen, indem Sie die [Druckvorschau](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#print-preview-cam) verwenden.

### Überprüfen der Ressourcenplanung {#review-resource-planning}

Nachdem Sie den für die Umstellung auf Cloud Service erforderlichen Arbeitsaufwand geschätzt haben, sollten Sie Ressourcen identifizieren, ein Team bilden und Rollen und Verantwortlichkeiten für die Umstellung zuordnen.

### Festlegen von KPIs {#establish-kpis}

Wenn Sie zuvor noch keine Bewertungsparameter (Key Performance Indicators, KPIs) festgelegt haben, wird empfohlen, KPIs für Ihre AEM-Implementierung festzulegen, damit sich Ihr Team auf das Wesentliche konzentrieren kann.

Unter [Entwickeln von KPIs](https://experienceleague.adobe.com/welcome/aem/part6.html?lang=de) erfahren Sie, wie Sie die richtigen KPIs für Ihre Geschäftsziele auswählen.

## Wie geht es weiter {#what-is-next}

Sobald Sie den Umfang der Änderungen kennen, die erforderlich sind, um zu AEM as a Cloud Service zu wechseln, ist es an der Zeit, [Code und Inhalte für die Cloud vorzubereiten](/help/journey-migration/implementation.md), bevor Sie die Migration tatsächlich durchführen.

## Zusätzliche Ressourcen {#additional-resources}

* [Erste Schritte mit Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/using-cam/getting-started-cam.md) – Eine umfassende Anleitung zur Verwendung von Cloud Acceleration Manager, um den Wechsel zur Cloud zu beschleunigen.
* [AEM as a Cloud Service: Einführung, Architektur und neuer Ansatz](https://experienceleague.adobe.com/de?launch=ExperienceManager-D-1-2021.1.migration&amp;recommended=ExperienceManager-D-1-2021.1.migration&amp;lang=de#dashboard/learning)
* [Startseite von AEM as a Cloud Service](/help/overview/introduction.md) – Beginnen Sie hier, um einen Überblick über die Dokumentation zu Experience Manager as a Cloud Service zu erhalten.
* [Überblick über AEM as a Cloud Service](/help/overview/introduction.md) – Dieses Handbuch bietet einen Überblick über Experience Manager as a Cloud Service, einschließlich Einführung, Terminologie und Architektur.
* [Onboarding-Tour](/help/journey-onboarding/overview.md) – Dieses Handbuch bietet eine Zusammenfassung der ersten Schritte mit Experience Manager as a Cloud Service, einschließlich der Zugriffsmöglichkeiten und der Einrichtung des Teams.
