---
title: OSGi-Konfigurations-API
description: Beschreibung der OSGi-Konfigurationsoberfläche für AEM als Cloud Service
feature: Bereitstellen
source-git-commit: 4be76f19c27aeab84de388106a440434a99a738c
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 5%

---


# OSGi-Konfigurations-API

Die beiden folgenden Listen spiegeln die AEM als OSGi-Konfigurationsoberfläche für Cloud Service wider und beschreiben, was Kunden konfigurieren können.

1. Eine Liste der OSGi-Konfigurationen, die nicht vom Kundencode konfiguriert werden dürfen
1. Eine Liste der OSGi-Konfigurationen, deren Eigenschaften zwar konfiguriert werden können, aber die angegebenen Validierungsregeln einhalten müssen. Zu diesen Regeln gehören, ob eine Deklaration der Eigenschaft erforderlich ist, der Typ und in einigen Fällen der zulässige Wertebereich.

Wenn eine OSGi-Konfiguration nicht aufgeführt ist, kann sie durch Kundencode konfiguriert werden.

Diese Regeln werden während des Build-Prozesses von Cloud Manager validiert. Im Laufe der Zeit können zusätzliche Regeln hinzugefügt werden, und das erwartete Durchführungsdatum wird in der Tabelle angegeben. Von Kunden wird erwartet, dass sie diese Regeln bis zum Zieltermin für die Durchsetzung einhalten. Wenn Sie sich nach dem Entfernungsdatum nicht an die Regeln halten, treten im Cloud Manager-Build-Prozess Fehler auf. Maven-Projekte sollten das [AEM as a Cloud Service SDK Build Analyzer Maven Plugin](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html) enthalten, um OSGi-Konfigurationsfehler während der lokalen SDK-Entwicklung zu kennzeichnen.

Weitere Informationen zur OSGi-Konfiguration finden Sie unter [diesem Speicherort](/help/implementing/deploying/configuring-osgi.md).

## OSGi-Konfigurationen, die nicht geändert werden können {#osgi-configurations-that-cannot-be-modified}

* **`org.apache.felix.webconsole.internal.servlet.OsgiManager`** (Datum der Mitteilung: 30.4.2021, Vollstreckungsdatum: 31.7.2021)
* **`com.day.cq.auth.impl.cug.CugSupportImpl`** (Datum der Mitteilung: 30.4.2021, Vollstreckungsdatum: 31.7.2021)
* **`com.day.cq.jcrclustersupport.ClusterStartLevelController`** (Datum der Mitteilung: 30.4.2021, Vollstreckungsdatum: 31.7.2021)
* **`org.apache.felix.http (Factory)`** (Datum der Mitteilung: 30.4.2021, Vollstreckungsdatum: 31.7.2021)

## OSGi-Konfigurationen, die Build-Validierungsregeln unterliegen {#osgi-configurations-subject-to-build-validation-rules}

* **`org.apache.felix.eventadmin.impl.EventAdmin`** (Datum der Mitteilung: 30.4.2021, Vollstreckungsdatum: 31.7.2021)
   * `org.apache.felix.eventadmin.ThreadPoolSize`
      * Typ: integer
      * Erforderlicher Bereich: 2-100
   * `org.apache.felix.eventadmin.AsyncToSyncThreadRatio`
      * Typ: double
   * `org.apache.felix.eventadmin.Timeout`
      * Typ: integer
   * `org.apache.felix.eventadmin.RequireTopic`
      * Typ: boolean
   * `org.apache.felix.eventadmin.IgnoreTimeout`
      * Erforderlich
      * Typ: Zeichenfolgen-Array
      * Erforderlicher Bereich: Muss mindestens alle `org.apache.felix*`, `org.apache.sling*`, `come.day*`, `com.adobe*` enthalten
   * `org.apache.felix.eventadmin.IgnoreTopic`
      * Typ: Zeichenfolgen-Array
* **`org.apache.felix.http`** (Datum der Mitteilung: 30.4.2021, Vollstreckungsdatum: 31.7.2021)
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
      * Type: string
   * `org.eclipse.jetty.servlet.CheckingRemoteSessionIdEncoding`
      * Typ: boolean
   * `org.eclipse.jetty.servlet.SessionCookie`
      * Typ: Zeichenfolge
   * `org.eclipse.jetty.servlet.SessionDomain`
      * Typ: Zeichenfolge
   * `org.eclipse.jetty.servlet.SessionPath`
      * Typ: Zeichenfolge
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
      * Typ: Zeichenfolge
   * `org.apache.felix.jetty.gzip.includedMethods`
      * Typ: Zeichenfolgen-Array
   * `org.apache.felix.jetty.gzip.excludedMethods`
      * Typ: Zeichenfolgen-Array
   * `org.apache.felix.jetty.gzip.includedPaths`
      * Typ: Zeichenfolgen-Array
   * `org.apache.felix.jetty.gzip.excludedPaths`
      * Typ: Zeichenfolgen-Array
   * `org.apache.felix.jetty.gzip.includedMimeTypes`
      * Typ: Zeichenfolgen-Array
   * `org.apache.felix.jetty.gzip.excludedMimeTypes`
      * Typ: Zeichenfolgen-Array
   * `org.apache.felix.http.session.invalidate`
      * Typ: boolean
   * `org.apache.felix.http.session.container.attribute`
      * Typ: Zeichenfolgen-Array
   * `org.apache.felix.http.session.uniqueid`
      * Typ: boolean
* **`org.apache.sling.scripting.cache`** (Datum der Mitteilung: 30.4.2021, Vollstreckungsdatum: 31.7.2021)
   * `org.apache.sling.scripting.cache.size`
      * Typ: integer
      * Erforderlicher Bereich: >= 2048
   * `org.apache.sling.scripting.cache.additional_extensions`
      * Erforderlich
      * Typ: Zeichenfolgen-Array
      * Erforderlicher Bereich: muss js enthalten
* **`com.day.cq.mailer.DefaultMailService`** (Datum der Mitteilung: 30.4.2021, Vollstreckungsdatum: 31.7.2021)
   * `smtp.host`
      * Typ: Zeichenfolge
   * `smtp.port`
      * Typ: integer
      * Erforderlicher Bereich: 465, 587 oder 25
   * `smtp.user`
      * Typ: Zeichenfolge
   * `smtp.password`
      * Typ: Zeichenfolge
   * `from.address`
      * Typ: Zeichenfolge
   * `smtp.ssl`
      * Typ: Zeichenfolge
   * `smtp.starttls`
      * Typ: boolean
   * `smtp.requiretls`
      * Typ: boolean
   * `debug.email`
      * Typ: boolean
   * `oauth.flow`
      * Typ: boolean
