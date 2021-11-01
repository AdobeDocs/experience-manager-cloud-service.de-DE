---
title: OSGi-Konfigurations-API
description: Beschreibung der OSGi-Konfigurationsoberfläche für AEM as a Cloud Service
feature: Deploying
exl-id: 94d3df65-71d7-4442-8412-fe2cca7e79ff
source-git-commit: 96a0dacf69f6f9c5744f224d1a48b2afa11fb09e
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 98%

---

# OSGi-Konfigurations-API

Die beiden folgenden Listen spiegeln die OSGi-Konfigurationsoberfläche für AEM as a Cloud Service wider und beschreiben, was Kunden konfigurieren können.

1. Eine Liste der OSGi-Konfigurationen, die nicht per Kunden-Code konfiguriert werden dürfen.
1. Eine Liste der OSGi-Konfigurationen, deren Eigenschaften zwar konfiguriert werden können, aber die angegebenen Validierungsregeln einhalten müssen. Zu diesen Regeln gehört, ob die Deklaration der Eigenschaft erforderlich ist, ihr Typ und in einigen Fällen ihr zulässiger Wertebereich.

Wenn eine OSGi-Konfiguration nicht aufgeführt ist, kann sie durch Kunden-Code konfiguriert werden.

Diese Regeln werden während des Build-Prozesses von Cloud Manager validiert. Im Laufe der Zeit können zusätzliche Regeln hinzugefügt werden, und das erwartete Erzwingungsdatum wird in der Tabelle angegeben. Von Kunden wird erwartet, dass sie diese Regeln bis zum Zieltermin für die Erzwingung einhalten. Werden die Regeln nach dem Entfernungsdatum nicht eingehalten, treten im Build-Prozess von Cloud Manager Fehler auf. Maven-Projekte sollten das [Build Analyzer-Maven-Plug-in des AEM as a Cloud Service-SDK](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=de) enthalten, um OSGi-Konfigurationsfehler während der lokalen SDK-Entwicklung zu kennzeichnen.

Weitere Informationen zur OSGi-Konfiguration finden Sie [hier](/help/implementing/deploying/configuring-osgi.md).

## OSGi-Konfigurationen, die nicht geändert werden können {#osgi-configurations-that-cannot-be-modified}

* **`org.apache.felix.webconsole.internal.servlet.OsgiManager`** (Ankündigungsdatum: 30.04.2021, Erzwingungsdatum: 31.07.2021)
* **`com.day.cq.auth.impl.cug.CugSupportImpl`** (Ankündigungsdatum: 30.04.2021, Erzwingungsdatum: 31.07.2021)
* **`com.day.cq.jcrclustersupport.ClusterStartLevelController`** (Ankündigungsdatum: 30.04.2021, Erzwingungsdatum: 31.07.2021)
* **`org.apache.felix.http (Factory)`** (Ankündigungsdatum: 30.04.2021, Erzwingungsdatum: 31.07.2021)
* **`org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`** (Datum der Mitteilung: 25.8.2021, Vollstreckungsdatum: 26.11.2021)

## OSGi-Konfigurationen, die Build-Validierungsregeln unterliegen {#osgi-configurations-subject-to-build-validation-rules}

* **`org.apache.felix.eventadmin.impl.EventAdmin`** (Ankündigungsdatum: 30.04.2021, Erzwingungsdatum: 31.07.2021)
   * `org.apache.felix.eventadmin.ThreadPoolSize`
      * Typ: integer
      * Erforderlicher Bereich: 2–100
   * `org.apache.felix.eventadmin.AsyncToSyncThreadRatio`
      * Typ: double
   * `org.apache.felix.eventadmin.Timeout`
      * Typ: integer
   * `org.apache.felix.eventadmin.RequireTopic`
      * Typ: boolean
   * `org.apache.felix.eventadmin.IgnoreTimeout`
      * Erforderlich
      * Typ: array of strings
      * Erforderlicher Bereich: muss mindestens alles aus den Gruppen `org.apache.felix*`, `org.apache.sling*`, `come.day*`, `com.adobe*` enthalten
   * `org.apache.felix.eventadmin.IgnoreTopic`
      * Typ: array of strings
* **`org.apache.felix.http`** (Ankündigungsdatum: 30.04.2021, Erzwingungsdatum: 31.07.2021)
   * `org.apache.felix.http.timeout`
      * Typ: integer
   * `org.apache.felix.http.session.timeout`
      * Typ: integer
   * `org.apache.felix.http.jetty.threadpool.max`
      * Typ: integer
   * `org.apache.felix.http.jetty.headerBufferSize`
      * Typ: integer
   * `org.apache.felix.http.jetty.requestBufferSize`
      * Typ: integer
   * `org.apache.felix.http.jetty.responseBufferSize`
      * Typ: integer
   * `org.apache.felix.http.jetty.maxFormSize`
      * Typ: integer
   * `org.apache.felix.https.jetty.session.cookie.httpOnly`
      * Typ: boolean
   * `org.apache.felix.https.jetty.session.cookie.secure`
      * Typ: boolean
   * `org.eclipse.jetty.servlet.SessionIdPathParameterName`
      * Typ: string
   * `org.eclipse.jetty.servlet.CheckingRemoteSessionIdEncoding`
      * Typ: boolean
   * `org.eclipse.jetty.servlet.SessionCookie`
      * Typ: string
   * `org.eclipse.jetty.servlet.SessionDomain`
      * Typ: string
   * `org.eclipse.jetty.servlet.SessionPath`
      * Typ: string
   * `org.eclipse.jetty.servlet.MaxAge`
      * Typ: integer
   * `org.eclipse.jetty.servlet.SessionScavengingInterval`
      * Typ: integer
   * `org.apache.felix.jetty.gziphandler.enable`
      * Typ: boolean
   * `org.apache.felix.jetty.gzip.minGzipSize`
      * Typ: integer
   * `org.apache.felix.jetty.gzip.compressionLevel`
      * Typ: integer
   * `org.apache.felix.jetty.gzip.inflateBufferSize`
      * Typ: integer
   * `org.apache.felix.jetty.gzip.syncFlush`
      * Typ: boolean
   * `org.apache.felix.jetty.gzip.excludedUserAgents`
      * Typ: string
   * `org.apache.felix.jetty.gzip.includedMethods`
      * Typ: array of strings
   * `org.apache.felix.jetty.gzip.excludedMethods`
      * Typ: array of strings
   * `org.apache.felix.jetty.gzip.includedPaths`
      * Typ: array of strings
   * `org.apache.felix.jetty.gzip.excludedPaths`
      * Typ: array of strings
   * `org.apache.felix.jetty.gzip.includedMimeTypes`
      * Typ: array of strings
   * `org.apache.felix.jetty.gzip.excludedMimeTypes`
      * Typ: array of strings
   * `org.apache.felix.http.session.invalidate`
      * Typ: boolean
   * `org.apache.felix.http.session.container.attribute`
      * Typ: array of strings
   * `org.apache.felix.http.session.uniqueid`
      * Typ: boolean
* **`org.apache.sling.scripting.cache`** (Ankündigungsdatum: 30.04.2021, Erzwingungsdatum: 31.07.2021)
   * `org.apache.sling.scripting.cache.size`
      * Typ: integer
      * Erforderlicher Bereich: >= 2048
   * `org.apache.sling.scripting.cache.additional_extensions`
      * Erforderlich
      * Typ: array of strings
      * Erforderlicher Bereich: muss „js“ enthalten
* **`com.day.cq.mailer.DefaultMailService`** (Ankündigungsdatum: 30.04.2021, Erzwingungsdatum: 31.07.2021)
   * `smtp.host`
      * Typ: string
   * `smtp.port`
      * Typ: integer
      * Erforderlicher Bereich: 465, 587 oder 25
   * `smtp.user`
      * Typ: string
   * `smtp.password`
      * Typ: string
   * `from.address`
      * Typ: string
   * `smtp.ssl`
      * Typ: string
   * `smtp.starttls`
      * Typ: boolean
   * `smtp.requiretls`
      * Typ: boolean
   * `debug.email`
      * Typ: boolean
   * `oauth.flow`
      * Typ: boolean
