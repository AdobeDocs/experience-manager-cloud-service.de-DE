---
title: Checkliste vor der Live-Schaltung
description: Erfahren Sie mehr über alle Elemente, die vorhanden sein müssen, um eine erfolgreiche Live-Schaltung mit AEM as a Cloud Service zu ermöglichen.
exl-id: b424a9db-0f3b-4a8d-be84-365d68df46ca
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 4a369104ea8394989149541ee1a7b956383c8f12
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 56%

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
* Überprüfen von Dispatcher-Konfigurationen.
   * Lokalen Dispatcher-Validator verwenden, der die lokale Konfiguration, Validierung und Simulation von Dispatcher erleichtert
      * [Richten Sie die lokalen Dispatcher-Tools ein](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools#prerequisites).
   * Überprüfen Sie die Konfiguration des virtuellen Hosts sorgfältig.
      * Die einfachste (und standardmäßige) Lösung besteht darin, `ServerAlias *` in Ihre Virtual-Host-Datei in den `/dispatcher/src/conf.d/available_vhostsfolder` aufzunehmen. Auf diese Weise können die von Funktionstests für das Produkt, der Invalidierung des Dispatcher-Cache und von Klonen verwendeten Host-Aliase funktionieren.
      * Wenn `ServerAlias *` jedoch nicht akzeptabel ist, müssen zusätzlich zu Ihren benutzerdefinierten Domänen mindestens die folgenden `ServerAlias` -Einträge zulässig sein:
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
         * [Einführung in die Verwaltung von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
         * [SSL-Zertifikate verwalten](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
      * Verwalten von benutzerdefinierten Domain-Namen (DNS)
         * Stellen Sie sicher, dass die DNS-Umstellung keine unerwarteten Probleme verursacht. Erstellen Sie eine Test-Subdomain, mit der Sie Ihre Produktionsinstanz verbinden können, bevor Sie live gehen und eine Reihe von UAT-Tests durchführen. Wenn Ihre Domäne also example.com ist, können Sie eine Subdomain test.example.com erstellen und sie auf die Produktion anwenden. Suchen Sie während des UAT-Tests der Domäne nach Elementen wie der richtigen Link-Umleitung, Zwischenspeicherung und Dispatcher-Konfigurationen.
         * [Einführung in benutzerdefinierte Domänennamen](/help/implementing/cloud-manager/custom-domain-names/introduction.md)
         * [Benutzerdefinierten Domänennamen hinzufügen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)
         * [Benutzerdefinierten Domänennamen verwalten](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)
   * Denken Sie daran, den TTL-Satz für Ihren DNS-Eintrag zu überprüfen.
      * Die TTL ist die Zeit, die ein DNS-Eintrag in einem Cache verbleibt, bevor der Server um eine Aktualisierung gebeten wird.
      * Wenn Sie eine sehr hohe TTL haben, dauert die Aktualisierung Ihres DNS-Eintrags länger, bis es weitergegeben wird.
* Führen Sie Leistungs- und Sicherheitstests durch, die Ihren Geschäftsanforderungen und -zielen entsprechen.
   * Führen Sie Tests in einer Staging-Umgebung durch.  Sie hat dieselbe Größe wie die Produktion.
   * Entwicklungsumgebungen haben nicht die gleiche Größe wie Staging- und Produktionsumgebungen.
* Stellen Sie um und gehen Sie sicher, dass die tatsächliche Live-Schaltung ohne neue Bereitstellung oder Inhaltsaktualisierung durchgeführt wird.
* Erstellen Sie Admin Console-Benutzerbenachrichtigungsprofile. Siehe [Benachrichtigungsprofile](/help/journey-onboarding/notification-profiles.md)
* Ziehen Sie die Konfiguration von Traffic-Filterregeln in Erwägung, um zu steuern, welcher Traffic auf Ihrer Website nicht zulässig sein soll.
   * Regeln zum Traffic-Filter für Ratenbegrenzungen können ein effektives Werkzeug gegen DDoS-Angriffe sein. Eine spezielle Kategorie von Traffic-Filterregeln, so genannte WAF (Web Application Firewall)-Regeln, erfordert eine separate Lizenz.
   * Weitere Informationen finden Sie in der Dokumentation zu einigen [vorgeschlagenen Startregeln](/help/security/traffic-filter-rules-including-waf.md#recommended-starter-rules).

Sie können jederzeit auf die Liste zurückgreifen, falls Sie Ihre Aufgaben während der Live-Schaltung neu kalibrieren müssen.
