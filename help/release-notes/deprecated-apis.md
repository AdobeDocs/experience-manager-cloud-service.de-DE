---
title: Eingestellte APIs
description: Spezifische Versionshinweise für veraltete und entfernte APIs in [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
source-git-commit: 3c4b8f8d9b252cfc90823c475a4e21eefd1dfcf7
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Veraltete APIs {#deprecated-apis}

Nachstehend finden Sie eine umfassende Liste veralteter AEM-APIs und des erwarteten Entfernungsdatums. Von Kunden wird erwartet, dass sie die APIs bis zum geplanten Entfernungsdatum aus ihrem Code entfernen. Jede Verwendung der API nach dem Entfernungsdatum führt zu Fehlern in der lokalen SDK-/Entwicklungsumgebung und im Cloud Manager-Build-Prozess.


<table>
<thead>
  <tr>
    <th>Package/Class</th>
    <th>Kommentare</th>
    <th>Veraltungsdatum</th>
    <th>Target-Entfernungsdatum</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>org.apache.sling.commons.auth<br>org.apache.sling.commons.auth.spi</td>
    <td>Verwenden Sie als Alternative die SPI-Schnittstellen Auth-Core/Auth-Core von Sling.</td>
    <td>2015</td>
    <td>30.07.21</td>
  </tr>
  <tr>
    <td>org.apache.sling.runmode</td>
    <td></td>
    <td>2015</td>
    <td>30.07.21</td>
  </tr>
  <tr>
    <td>com.day.cq.jcrclustersupport</td>
    <td>Verwenden der Discovery-API von Sling als Alternative</td>
    <td>2015</td>
    <td>30.07.21</td>
  </tr>
  <tr>
    <td>org.apache.sling.settings</td>
    <td>AEM as a Cloud Service unterstützt keine Ausführungsmodi oder Dateisystemzugriff zur Laufzeit. </td>
    <td>05.10.20</td>
    <td>01.06.21</td>
  </tr>
  <tr>
    <td>org.apache.fop.apps</td>
    <td></td>
    <td>01.03.21</td>
    <td>01.06.21</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.vault.util.xml.xerces.dom<br>org.apache.jackrabbit.vault.util.xml.xerces.util<br>org.apache.jackrabbit.vault.util.xml.xerces.xni<br>org.apache.jackrabbit.vault.util.xml.xerces.xni.parser</td>
    <td></td>
    <td>05.03.21</td>
    <td>06.06.21</td>
  </tr>
  <tr>
    <td>org.json</td>
    <td>Die Apache Johnzon-Implementierung von <a href="https://johnzon.apache.org/index.html">javax.json</a> wird empfohlen und sollte verwendet werden. </td>
    <td>30.04.21</td>
    <td>30.07.21</td>
  </tr>
  <tr>
    <td>org.apache.felix.cm<br>org.apache.felix.cm.file</td>
    <td>Benutzerdefinierte Persistenzmanager werden in AEM als Cloud Service nicht unterstützt.</td>
    <td>30.04.21</td>
    <td>30.07.21</td>
  </tr>
  <tr>
    <td>org.apache.commons.lang<br>org.apache.commons.lang.enums<br>org.apache.commons.lang.builder<br>org.apache.commons.lang.exception<br>org.apache.commons.lang.math<br>org.apache.commons.lang.mutable<br>org.apache.commons.lang.reflect<br>org.apache.commons.lang.text<br>org.apache.commons.lang.time</td>
    <td>Commons Lang 2 befindet sich im Wartungsmodus. Commons Lang 3 sollte stattdessen verwendet werden.</td>
    <td>30.04.21</td>
    <td>30.07.21</td>
  </tr>
  <tr>
    <td>org.apache.commons.collections<br>org.apache.commons.collections.bag<br>org.apache.commons.collections.bidimap<br>org.apache.commons.collections.buffer<br>org.apache.commons.collections.collection<br>org.apache.commons.collections.comparators<br>org.apache.commons.collections.functors<br>org.apache.commons.collections.iterators<br>org.apache.commons.collections.keyvalue<br>org.apache.commons.collections.list<br>org.apache.commons.collections.map<br>org.apache.commons.collections.set</td>
    <td>Allgemeine Sammlungen 3 befinden sich im Wartungsmodus. Gemeinsame Sammlungen 4 sollten stattdessen verwendet werden.</td>
    <td>30.04.21</td>
    <td>30.07.21</td>
  </tr>
  <tr>
    <td>org.apache.felix.systemready</td>
    <td>Es wird empfohlen, stattdessen die Apache Felix HealthCheck-API zu verwenden</td>
    <td>30.04.21</td>
    <td>30.07.21</td>
  </tr>
  <tr>
    <td>org.apache.felix.webconsole<br>org.apache.felix.webconsole.bundleinfo<br>org.apache.felix.webconsole.i18n</td>
    <td>Die Felix-Webkonsole wird in Cloud-Umgebungen nicht unterstützt</td>
    <td>30.04.21</td>
    <td>30.07.21</td>
  </tr>
  <tr>
    <td>org.apache.felix.http.jetty<br>org.eclipse.jetty.http<br>org.eclipse.jetty.http.pathmap<br>org.eclipse.jetty.io<br>org.eclipse.jetty.io.ssl<br>org.eclipse.jetty.jmx<br>org.eclipse.jetty.security<br>org.eclipse.jetty.server<br>org.eclipse.jetty.server.handler<br>org.eclipse.jetty.server.handler.gzip<br>org.eclipse.jetty.server.handler.jmx<br>org.eclipse.jetty.server.jmx<br>org.eclipse.jetty.server.nio<br>org.eclipse.jetty.server.session<br>org.eclipse.jetty.servlet<br>org.eclipse.jetty.servlet.jmx<br>org.eclipse.jetty.servlet.listener<br>org.eclipse.jetty.util<br>org.eclipse.jetty.util.annotation<br>org.eclipse.jetty.util.component<br>org.eclipse.jetty.util.log<br>org.eclipse.jetty.util.preventers<br>org.eclipse.jetty.util.resource<br>org.eclipse.jetty.util.security<br>org.eclipse.jetty.util.ssl<br>org.eclipse.jetty.util.statistic<br>org.eclipse.jetty.util.thread<br>org.eclipse.jetty.util.thread.strategy<br>org.eclipse.jetty.webapp<br>org.eclipse.jetty.websocket.api<br>org.eclipse.jetty.websocket.api.annotations<br>org.eclipse.jetty.websocket.api.extensions<br>org.eclipse.jetty.websocket.api.util<br>org.eclipse.jetty.websocket.client<br>org.eclipse.jetty.websocket.client.io<br>org.eclipse.jetty.websocket.client.masks<br>org.eclipse.jetty.websocket.common<br>org.eclipse.jetty.websocket.common.events<br>org.eclipse.jetty.websocket.common.events.annotated<br>org.eclipse.jetty.websocket.common.extensions<br>org.eclipse.jetty.websocket.common.extensions.compress<br>org.eclipse.jetty.websocket.common.extensions.fragment<br>org.eclipse.jetty.websocket.common.extensions.identity<br>org.eclipse.jetty.websocket.common.frames<br>org.eclipse.jetty.websocket.common.io<br>org.eclipse.jetty.websocket.common.io.http<br>org.eclipse.jetty.websocket.common.io.payload<br>org.eclipse.jetty.websocket.common.message<br>org.eclipse.jetty.websocket.common.scopes<br>org.eclipse.jetty.websocket.common.util<br>org.eclipse.jetty.websocket.server<br>org.eclipse.jetty.websocket.server.pathmap<br>org.eclipse.jetty.websocket.servlet<br>org.eclipse.jetty.xml<br>org.eclipse.jetty.client<br>org.eclipse.jetty.client.api<br>org.eclipse.jetty.client.http<br>org.eclipse.jetty.client.jmx<br>org.eclipse.jetty.client.util</td>
    <td>Die Eclipse Jetty- und Felix Http Jetty-Pakete werden nicht mehr unterstützt.</td>
    <td>27.05.21</td>
    <td>26.08.21</td>
  </tr>
  <tr>
    <td>com.mongodb<br>com.mongodb.annotations<br>com.mongodb.assertions<br>com.mongodb.async<br>com.mongodb.binding<br>com.mongodb.bulk<br>com.mongodb.client<br>com.mongodb.client.gridfs<br>com.mongodb.client.gridfs.codecs<br>com.mongodb.client.gridfs.model<br>com.mongodb.client.jndi<br>com.mongodb.client.model<br>com.mongodb.client.model.changestream<br>com.mongodb.client.model.geojson<br>com.mongodb.client.model.geojson.codecs<br>com.mongodb.client.result<br>com.mongodb.connection<br>com.mongodb.connection.netty<br>com.mongodb.diagnostics.logging<br>com.mongodb.event<br>com.mongodb.gridfs<br>com.mongodb.internal<br>com.mongodb.internal.async<br>com.mongodb.internal.authentication<br>com.mongodb.internal.connection<br>com.mongodb.internal.dns<br>com.mongodb.internal.event<br>com.mongodb.internal.management.jmx<br>com.mongodb.internal.session<br>com.mongodb.internal.thread<br>com.mongodb.internal.validator<br>com.mongodb.management<br>com.mongodb.operation<br>com.mongodb.selector<br>com.mongodb.session<br>com.mongodb.util</td>
    <td>Die Verwendung dieser API wird in AEM as a Cloud Service nicht unterstützt.</td>
    <td>27.05.21</td>
    <td>30.07.21</td>
  </tr>
  <tr>
    <td>org.apache.felix.metatype<br>org.apache.felix.scr<br>org.apache.felix.scr.info</td>
    <td>Der Apache Felix-Metatyp und die SCR-APIs werden nicht mehr unterstützt.  Verwenden Sie stattdessen den OSGi-Metatyp und die deklarativen Service-APIs .</td>
    <td>27.05.21</td>
    <td>26.08.21</td>
  </tr>
</tbody>
</table>