---
title: Checkliste vor der Live-Schaltung
description: Erfahren Sie mehr über alle Elemente, die für eine erfolgreiche Live-Schaltung mit AEM as a Cloud Service vorhanden sein müssen.
exl-id: b424a9db-0f3b-4a8d-be84-365d68df46ca
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: ht
source-wordcount: '575'
ht-degree: 100%

---

# Checkliste vor der Live-Schaltung {#Go-Live-Checklist}

Überprüfen Sie diese Liste der Aktivitäten, um sicherzustellen, dass Sie eine reibungslose und erfolgreiche Live-Schaltung durchführen können.

* Führen Sie eine End-to-End-Produktions-Pipeline mit Funktions- und Benutzeroberflächentests aus, um ein **immer aktuelles** AEM Produkterlebnis zu gewährleisten. Sehen Sie sich die folgenden Ressourcen an.
   * [AEM-Versionsaktualisierungen](/help/implementing/deploying/aem-version-updates.md)
   * [Benutzerdefinierte Funktionstests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing)
   * [Testen der Benutzeroberfläche](/help/implementing/cloud-manager/ui-testing.md)
* Wenn Sie von AEM 6.5 migrieren, sollten Sie Inhalte in die Produktion migrieren und sicherstellen, dass eine relevante Teilmenge während des Tests verfügbar ist.
   * Die Best Practices von DevOps für AEM sehen vor, dass der Code von der Entwicklungs- zur Produktionsumgebung nach oben verschoben wird, während die Inhalte von der Produktionsumgebung nach unten verschoben werden.
* Planen der Periode zum Einfrieren von Code und Inhalten.
   * Siehe auch den Abschnitt [Zeitpläne für das Einfrieren von Code und Inhalten für die Migration](#code-content-freeze).
* Ausführen der endgültigen Inhaltsauffüllung.
* Überprüfen Sie die Dispatcher-Konfigurationen.
   * Verwenden Sie einen lokalen Dispatcher-Validator, der die Konfiguration, Validierung und Simulation des Dispatchers lokal unterstützt.
      * [Richten Sie die lokalen Dispatcher-Tools ein.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html?lang=de#prerequisites)
   * Überprüfen Sie die Konfiguration des virtuellen Hosts sorgfältig.
      * Die einfachste (und standardmäßige) Lösung besteht darin, `ServerAlias *` in Ihrer virtuellen Host-Datei im `/dispatcher/src/conf.d/available_vhostsfolder` einzuschließen.
         * Dadurch können die von Produktfunktionstests, Dispatcher-Cache-Invalidierung und vom Klonen verwendeten Host-Aliase funktionieren.
      * Wenn `ServerAlias *` nicht akzeptabel ist, müssen mindestens die folgenden `ServerAlias`-Einträge zusätzlich zu Ihren benutzerdefinierten Domains zulässig sein:
         * `localhost`
         * `*.local`
         * `publish*.adobeaemcloud.net`
         * `publish*.adobeaemcloud.com`
* Konfigurieren Sie CDN, SSL und DNS.
   * Wenn Sie Ihr eigenes CDN verwenden, geben Sie ein Support-Ticket ein, um das entsprechende Routing zu konfigurieren.
      * Weitere Einzelheiten finden Sie im Abschnitt [Kunden-CDN verweist auf von AEM verwaltetes CDN](/help/implementing/dispatcher/cdn.md#point-to-point-cdn) in der CDN-Dokumentation.
      * Konfigurieren Sie SSL und DNS gemäß der Dokumentation des CDN-Anbieters.
   * Wenn Sie kein zusätzliches CDN verwenden, verwalten Sie SSL und DNS gemäß der folgenden Dokumentation:
      * Verwalten von SSL-Zertifikaten
         * [Einführung – Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
         * [Verwalten eines SSL-Zertifikats](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
      * Verwalten von benutzerdefinierten Domain-Namen (DNS)
         * Um sicherzustellen, dass die DNS-Umstellung keine unerwarteten Probleme verursacht, wird empfohlen, eine Test-Subdomain zu erstellen, mit der Sie Ihre Produktionsinstanz verbinden können, bevor Sie live gehen, und eine Reihe von UAT-Tests durchzuführen. Wenn Ihre Domain also example.com lautet, können Sie die Subdomain test.example.com erstellen und sie auf die Produktion anwenden. Während des UAT-Tests der Domain sollten Sie Dinge wie richtige Link-Umleitungen, Caching und Dispatcher-Konfigurationen prüfen.
         * [Einführung in benutzerdefinierte Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/introduction.md)
         * [Hinzufügen eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)
         * [Verwalten eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)
   * Denken Sie daran, den TTL-Satz für Ihren DNS-Eintrag zu überprüfen.
      * Die TTL ist die Zeit, die ein DNS-Eintrag in einem Cache verbleibt, bevor der Server um eine Aktualisierung gebeten wird.
      * Wenn Sie eine sehr hohe TTL haben, dauert die Aktualisierung Ihres DNS-Eintrags länger.
* Führen Sie Leistungs- und Sicherheitstests durch, die Ihren Geschäftsanforderungen und -zielen entsprechen.
   * Führen Sie Tests in der Staging-Umgebung durch.  Sie hat dieselbe Größe wie die Produktion.
   * Entwicklungsumgebungen haben nicht die gleiche Größe wie Staging- und Produktionsumgebungen.
* Stellen Sie um und gehen Sie sicher, dass die tatsächliche Live-Schaltung ohne neue Bereitstellung oder Inhaltsaktualisierung durchgeführt wird.
* Erstellen Sie Benachrichtigungsprofile für die Benutzenden der Admin Console. Siehe [Benachrichtigungsprofile](/help/journey-onboarding/notification-profiles.md)
* Ziehen Sie die Konfiguration von Traffic-Filterregeln in Erwägung, um zu steuern, welcher Traffic auf Ihrer Website nicht zulässig sein soll.
   * Regeln für Traffic-Filter mit Ratenbegrenzungen können ein effektives Werkzeug gegen DDoS-Angriffe sein. Eine spezielle Kategorie von Traffic-Filterregeln namens „WAF-Regeln“ erfordert eine gesonderte Lizenz.
   * Weitere Informationen finden Sie in der Dokumentation zu einigen [vorgeschlagenen Startregeln](/help/security/traffic-filter-rules-including-waf.md#recommended-starter-rules).

Sie können jederzeit auf die Liste zurückgreifen, falls Sie Ihre Aufgaben während der Live-Schaltung neu kalibrieren müssen.
