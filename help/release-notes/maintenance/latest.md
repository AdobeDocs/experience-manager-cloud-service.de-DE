---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 6fa6fc9015624bec9113a198285531a3bdd7e29c
workflow-type: ht
source-wordcount: '773'
ht-degree: 100%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 18175 {#release-18175}

Im Folgenden finden Sie eine Zusammenfassung der kontinuierlichen Verbesserungen für die Wartungsversion 18175, die am 10. Oktober 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 17964. Version 18099 wurde wegen eines Problems privat gemacht.

Die Funktionsaktivierung von 2024.10.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-18175}

* ASSETS-38322: Aktivieren des HTTP-Anfrageereignisses für AEM.
* ASSETS-41448: Update des auth.ims-Pakets, um FI für Gruppenzuordnungen zu unterstützen.
* ASSETS-41684: Hinzufügen von OOB-OSGi-Konfigurationen, um FI für Gruppenzuordnungen für Assets, Foundation, Sites und Formulare zu definieren.
* ASSETS-43015: Update auf das neueste auth.ims-Paket.
* CQ-4356633: Hinzufügen eines zusätzlichen Zeichens in die QuickInfo „Nur Inhalt“.
* GRANITE-50948: Integrieren des Repository-Dienstes in AEM; Unterstützung für Repository-Dienst.
* GRANITE-52454: Hinzufügen des Support-Helfers 0.1.2.
* GRANITE-52454: Upgrade des Support-Helfers GRANITE-52454 Upgrade des Support-Helfers zur Verwendung der neuesten Version für AEMaaCS.
* GRANITE-53287: Update der Testversion der Integration von Sicherheitsberechtigungen.
* GRANITE-53485: Authentifizierung des Support-Service-Prinzipals für die Replikation Azure Blob Storage.
* GRANITE-53514: Update von Treeactivation auf Version 1.0.26.
* GRANITE-53870: Erstellen eines internen Mechanismus, um die Überprüfung auf die maximale JVM-Version für den Schnellstart zu überspringen.
* GRANITE-53914: Behebung von Fehlern bei Plattformtests mit der aktualisierten Modulversion von Java 17.
* GRANITE-53966: Verwenden eines separaten Thread-Pools für die Inhaltsverteilung.
* GRANITE-54006: Update von Jackson auf 2.17.2.
* GRANITE-54038: Hinzufügen des Creative Cloud Enterprise IMS-Clients zur AEM IMS-Client-Zulassungsliste.
* GRANITE-54054: Umgebungsvariable für com.adobe.granite.repository.impl.SystemUserValidation warnOnly.
* GRANITE-54266: Im Produktions-SDK fehlt der Suchvorschlagsdienst.
* GRANITE-54274: Akzeptieren von Firefly IMS-Client.
* GRANITE-54300: Update von Oak auf die neueste öffentliche Version (1.70.0).
* GUIDES-19069: Hinzufügen von guidesPeerLinkIndex für AEM-Handbücher-Add-on.
* SITES-23583: Korrektur eines fehlgeschlagenen Tests für die Foundation-Komponente unter Java 17.
* SKYOPS-69768: SlingModels deserialisieren ResourceResolvers nicht.
* SKYOPS-76378: Verbessern der Thread-Sicherheit der ResourceBundle-Registrierung/-Deregistrierung in i18n.
* SKYOPS-79285: Update von Sling XSS auf 2.4.2
* SKYOPS-82383: Anzeigen des Ergebnisses „helm-values“ convert-merge-analyze im Befehlsausführungsdeskriptor.
* SKYOPS-84810: Überspringen der Ausführung von „40-initialize-publish.sh“ beim Start für RDE.
* SKYOPS-84951: Fehlerbehebung für den Generierungs-Code der veränderlichen Inhaltsprüfsumme.
* SKYOPS-85335: Update von org.apache.sling.jcr.repoinit auf 1.1.52.
* SKYOPS-85336: Update von Sling Commons Threads auf 3.3.0.
* SKYOPS-86329: Update von Versionen von Plattformtestmodulen für die Unterstützung von Java 21 SDK.

### Behobene Probleme {#fixed-issues-18175}

* CNTBF-298: Entfernen von jcr:uuid aus CC-Exportpaketen.
* SKYOPS-83910: Beheben von Parallelitätsproblemen, die in SKYOPS-82371 festgestellt wurden.
* GRANITE-52876: Update auf com.adobe.granite.ui.content 0.8.1448.
* GUIDES-14445: Die native PDF-Generierung schlägt mit einem Fehler bezüglich des Abrufs von Abhängigkeiten für Node.js fehl.
* GUIDES-16961: Der Titel mit `<conref>` wird in den Dashboards „Grundlinie“ und „Übersetzung“ des Web-Editors nicht aufgelöst.
* GUIDES-17283: Bei Auswahl der Option **In topicmeta hinzugefügte Metadaten verwenden** werden die Metadaten-Eigenschaften nicht in die Dokumenteigenschaften der nativen PDF-Ausgabe übernommen.
* GUIDES-17793: Die referenzierte PDF wird während der Massenaktivierung veröffentlichter Inhalte nicht über das Dashboard **Massenveröffentlichung** aktiviert.

Weitere Informationen zu den neuen und verbesserten Handbuch-Funktionen sowie zu den Problemen, die in der Version behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekannte Probleme {#known-issues-18175}

* FORMS-15818: Angaben „Komponenten-Beschreibungseintrag `OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml` nicht gefunden“ in Server-Protokollen. Dies sind harmlose Protokollanweisungen.

### Eingestellte Funktionen und APIs {#deprecated-18175}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

Im Folgenden finden Sie eine Zusammenfassung der Funktionen, die vor Kurzem eingestellt wurden bzw. demnächst eingestellt werden.

#### JavaScript-Anwendungs-API {#javascript-use-api}

[Das JavaScript-Anwendungs-API](https://github.com/adobe/htl-spec/blob/master/SPECIFICATION.md#42-javascript-use-api) ist offiziell eingestellt, da Benutzer Probleme beim Debugging und Verwalten von Code haben, der das API nutzt, sowie aufgrund von Leistungsbeschränkungen im Vergleich zur Java-Alternative.

Sie sollten auf [das Java-Anwendungs-API](https://experienceleague.adobe.com/de/docs/experience-manager-htl/content/java-use-api) umsteigen, das bessere Leistung, einfacheres Debugging und längerfristige Unterstützung bietet.

#### com.day.cq.wcm.api {#com-day-cq-wcm-api}

Beachten Sie, dass Adobe `com.day.cq.wcm.api` derzeit aktualisiert. Einige der Methoden und Klassen wurden in der aktuellen Version als `@Deprecated` markiert. Diese werden in zukünftigen Versionen entfernt. Überlegen Sie, zu den vorgeschlagenen Alternativen zu wechseln.

#### org.apache.jackrabbit.oak.plugins.blob {#org.apache.jackrabbit.oak.plugins.blob}

* GRANITE-54165: Veraltete org.apache.jackrabbit.oak.plugins.blob in der öffentlichen API.

### Sicherheitskorrekturen {#security-18175}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 2 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-18175}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.70.0 | [Oak-API 1.70.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.70.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.27.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
