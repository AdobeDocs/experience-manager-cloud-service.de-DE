---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 7bc6d9a947a5ce7c56481eaec8a2f186caf36c64
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 41%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 18099 {#release-18099}

Im Folgenden finden Sie eine Zusammenfassung der kontinuierlichen Verbesserungen für die Wartungsversion 18099, die am Donnerstag, 9. Oktober 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 17964.

Die Funktionsaktivierung von 2024.10.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-18099}

* ASSETS-38322: Aktivieren des HTTP-Anforderungsereignisses für AEM.
* ASSETS-41448: Aktualisieren Sie das Bundle auth.ims , um FI für Gruppenzuordnungen zu unterstützen.
* ASSETS-41684: Fügen Sie OOB-OSGi-Konfigurationen hinzu, um die Zuordnung von FI zu Gruppen für Assets, Foundation, Sites und Forms zu definieren.
* ASSETS-43015: Aktualisierung auf das neueste auth.ims-Bundle.
* CQ-4356633: Fügen Sie in der QuickInfo &quot;Nur Inhalt&quot;zusätzliche Zeichen hinzu.
* GRANITE-50948: Integrieren Sie den Repository-Dienst in AEM Unterstützung für Repository-Dienst.
* GRANITE-52454: Support Helper 0.1.2 hinzufügen.
* GRANITE-52454: Upgrade-Support-Helper GRANITE-52454 Upgrade-Support-Helfer zur Verwendung der neuesten Version für AEMaaCS.
* GRANITE-53287: Aktualisieren der Testversion der Integration von Sicherheitsberechtigungen.
* GRANITE-53485: Support Service Principal Authentifizierung für die Replikation Azure Blob Storage.
* GRANITE-53514: Treeactivation aktualisiert auf Version 1.0.26.
* GRANITE-53870: Erstellen Sie einen internen Mechanismus, um die maximale JVM-Versionsüberprüfung für den Schnellstart zu überspringen.
* GRANITE-53914: Fehlerbehebung bei Platform-Tests mit Java 17 Aktualisierte Modulversion.
* GRANITE-53966: Verwenden Sie einen separaten Thread-Pool für die Inhaltsverteilung.
* GRANITE-54006: Update Jackson auf 2.17.2.
* GRANITE-54038: Fügen Sie die Creative Cloud Enterprise IMS-Client-Zulassungsliste zur AEM IMS-Client- hinzu.
* GRANITE-54054: Umgebungsvariable für com.adobe.granite.repository.impl.SystemUserValidation warnOnly.
* GRANITE-54266: Produktions-SDK fehlt Suchvorschlagsdienst.
* GRANITE-54274: Firefly IMS-Client akzeptieren.
* GRANITE-54300: Update von Oak auf die neueste öffentliche Version (1.70.0).
* GUIDES-19069: Fügen Sie guidesPeerLinkIndex für AEM-Handbücher hinzu.
* SITES-23584: Fehlerhaften Test für Foundation-Komponente in Java 17 behoben.
* SKYOPS-69768: SlingModels deserialisieren ResourceResolvers nicht.
* SKYOPS-76378: Verbessern Sie die Thread-Sicherheit der ResourceBundle-Registrierung/-Registrierung in i18n.
* SKYOPS-79285: Aktualisierung von Sling XSS auf 2.4.2.
* SKYOPS-82383: Zeigen Sie das Ergebnis &quot;helm-values&quot;convert-merge-analyze im Befehlsausführungsdeskriptor an.
* SKYOPS-84810: Überspringen Sie die Ausführung &quot;40-initialize-publish.sh&quot;beim Start für RDE.
* SKYOPS-84951: Fehlerbehebung für den Generierungscode der veränderlichen Inhaltsprüfsumme.
* SKYOPS-85335: Aktualisieren Sie org.apache.sling.jcr.repoinit auf 1.1.52.
* SKYOPS-85336: Aktualisieren von Sling Commons Threads auf 3.3.0.
* SKYOPS-86329: Aktualisieren von Versionen von Plattformtestmodulen für die Unterstützung von Java 21 SDK.

### Behobene Probleme {#fixed-issues-18099}

* CNTBF-298: Entfernen Sie jcr:uuid aus CC-exportierten Paketen.
* SKYOPS-83910: Behebung von gleichzeitigen Problemen, die in SKYOPS-82371 festgestellt wurden.
* GRANITE-52876: Update auf com.adobe.granite.ui.content 0.8.1448.
* GRANITE-53088: Regression eingeführt durch die Fixierung von SITES-11992.
* GUIDES-14445: Die native PDF-Generierung schlägt mit einem Fehler bezüglich der Abrufen von Abhängigkeiten für Node.js fehl.
* GUIDES-16961: Der Titel mit `<conref>` wird nicht in den Dashboards &quot;Grundlinie&quot;und &quot;Übersetzung&quot;des Web Editors aufgelöst.
* GUIDES-17283: Bei Auswahl der Option **In der topicmeta hinzugefügte Metadaten verwenden** werden die Metadateneigenschaften nicht in den Dokumenteigenschaften der nativen PDF-Ausgabe propagiert.
* GUIDES-17793: Die referenzierte PDF wird während der Massenaktivierung veröffentlichter Inhalte nicht über das **Bulk Publish Dashboard** aktiviert.

Weitere Informationen zu den neuen und verbesserten Guides-Funktionen und -Problemen, die in der Version behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekannte Probleme {#known-issues-18099}

* FORMS-15818: Component descriptor entry `OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml` not found -Anweisungen in Serverprotokollen. Dies sind harmlose Protokollanweisungen.

### Eingestellte Funktionen und APIs {#deprecated-18099}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

Im Folgenden finden Sie eine Zusammenfassung der Funktionen, die vor Kurzem eingestellt wurden bzw. demnächst eingestellt werden.

#### JavaScript-Anwendungs-API {#javascript-use-api}

[Das JavaScript-Anwendungs-API](https://github.com/adobe/htl-spec/blob/master/SPECIFICATION.md#42-javascript-use-api) ist offiziell eingestellt, da Benutzer Probleme beim Debugging und Verwalten von Code haben, der das API nutzt, sowie aufgrund von Leistungsbeschränkungen im Vergleich zur Java-Alternative.

Sie sollten auf [das Java-Anwendungs-API](https://experienceleague.adobe.com/de/docs/experience-manager-htl/content/java-use-api) umsteigen, das bessere Leistung, einfacheres Debugging und längerfristige Unterstützung bietet.

#### com.day.cq.wcm.api {#com-day-cq-wcm-api}

Beachten Sie, dass Adobe `com.day.cq.wcm.api` derzeit aktualisiert. Einige der Methoden und Klassen wurden in der aktuellen Version als `@Deprecated` markiert. Diese werden in zukünftigen Versionen entfernt. Überlegen Sie, zu den vorgeschlagenen Alternativen zu wechseln.

#### org.apache.jackrabbit.oak.plugins.blob {#org.apache.jackrabbit.oak.plugins.blob}

* GRANITE-54165: Veraltete org.apache.jackrabbit.oak.plugins.blob in der öffentlichen API.

### Sicherheitskorrekturen {#security-18099}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 2 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-18099}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1,70,0 | [Oak-API 1.70.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.70.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.27.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
