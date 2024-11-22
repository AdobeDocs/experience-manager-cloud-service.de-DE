---
title: Veraltete und entfernte Funktionen
description: Spezifische Versionshinweise zu veralteten und entfernten Funktionen von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
exl-id: ef082184-4eb7-49c7-8887-03d925e3da6f
feature: Release Information
role: Admin
source-git-commit: 0ab75d1e49e06152cf3f4e8effe7d6d918b262c8
workflow-type: tm+mt
source-wordcount: '2709'
ht-degree: 93%

---

# Eingestellte und entfernte Funktionen und APIs {#deprecated-and-removed-features-apis}

>[!CONTEXTUALHELP]
>id="aem_cloud_deprecated_features"
>title="Veraltete und entfernte Funktionen in AEM as a Cloud Service"
>abstract="AEM as a Cloud Service verfügt über ein Cloud-natives Bereitstellungsmodell. Bestimmte Funktionen wurden durch Cloud-native Entsprechungen ersetzt. Diese Registerkarte zeigt diese Funktionen."

Adobe evaluiert fortlaufend Produktfunktionen, um ältere Funktionen zu überarbeiten oder durch modernere Alternativen zu ersetzen und so den Nutzen für die Kundschaft insgesamt zu verbessern, wobei stets auf Abwärtskompatibilität geachtet wird. Da [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] ein Cloud-natives Bereitstellungsmodell bietet, wurden bestimmte Funktionen und Features durch Cloud-native Entsprechungen ersetzt.

Für die Bekanntgabe des bevorstehenden Entfernens/Ersetzens von [!DNL Experience Manager]-Funktionen gelten die folgenden Regeln:

1. Zunächst wird angekündigt, dass die betreffende Funktion veraltet ist. Veraltete Funktionen bleiben weiterhin verfügbar, werden aber nicht weiter verbessert.
1. Funktionen, für die eine künftige Aufhebung der Unterstützung angekündigt wurde, werden frühestens in der nächsten Hauptversion entfernt. Der tatsächliche Termin für das Entfernen wird bekannt gegeben.

Dieser Prozess räumt Kunden mindestens einen Veröffentlichungszyklus ein, um ihre Implementierung an eine neue Version oder die Nachfolgeversion einer veralteten Funktion anzupassen, bevor die Funktion tatsächlich entfernt wird.

## Veraltete Funktionen {#deprecated-features}

In diesem Abschnitt werden Funktionen aufgeführt, die in [!DNL Experience Manager] as a [!DNL Cloud Service] als veraltet gekennzeichnet wurden. In der Regel werden Funktionen, die in einer künftigen Version entfernt werden sollen, zuerst als veraltet gekennzeichnet, wobei eine Alternative bereitgestellt wird.

Kunden wird empfohlen zu überprüfen, ob sie die Funktion in ihrer aktuellen Implementierung nutzen, und die Änderung ihrer Implementierung zu planen, um die bereitgestellte Alternative nutzen zu können.

| Funktionen | Veraltete Funktion | Ersatz |
| ------------ | ------------------ | ----------- |
| [!DNL Sites] | [JavaScript-Anwendungs-API](https://github.com/adobe/htl-spec/blob/master/SPECIFICATION.md#42-javascript-use-api) | [Java-Anwendungs-API](https://experienceleague.adobe.com/de/docs/experience-manager-htl/content/java-use-api) |
| [!DNL Sites] | Experience Fragments-Eigenschaften für **Social-Media-Status**. | Die Funktion wird bald entfernt. |
| [!DNL Sites] | Vorlagenbasierte einfache Inhaltsfragmente. | Jetzt [Modellbasierte strukturierte Inhaltsfragmente](/help/assets/content-fragments/content-fragments-models.md). |
| [!DNL Assets] | `DAM Asset Update`-Workflow zur Verarbeitung erfasster Bilder. | Für die Asset-Erfassung werden jetzt [Asset-Microservices](/help/assets/asset-microservices-overview.md) verwendet. |
| [!DNL Assets] | Hochladen von Assets direkt in [!DNL Experience Manager]. Siehe [Veraltete APIs zum Hochladen von Assets](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api). | Verwenden Sie den [direkten binären Upload](/help/assets/add-assets.md). Weitere technische Daten finden Sie im Abschnitt zu den [APIs für den direkten Upload](/help/assets/developer-reference-material-apis.md#upload-binary). |
| [!DNL Assets] | [Bestimmte Workflow-Schritte ](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) im `DAM Asset Update`-Workflow werden nicht unterstützt, darunter der Aufruf von Befehlszeilen-Tools wie [!DNL ImageMagick]. | [Asset-Microservices](/help/assets/asset-microservices-overview.md) bieten Ersatz für viele Workflows. Verwenden Sie für die benutzerdefinierte Verarbeitung [Nachbearbeitungs-Workflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |
| [!DNL Assets] | FFmpeg-Transcodierung von Videos. | Verwenden Sie für die Generierung von FFmpeg-Miniaturen [Asset-Microservices](/help/assets/asset-microservices-overview.md). Verwenden Sie für die von FFmpeg-Transcodierung [Dynamic Media](/help/assets/manage-video-assets.md). |
| [!DNL Foundation] | Benutzeroberfläche für die Strukturreplikation auf der Registerkarte „Verteilung“ des Replikationsagenten (wird nach dem 30. September 2021 entfernt) | Ansätze zum [Verwalten der Veröffentlichung](/help/operations/replication.md#manage-publication) oder zum [Workflow-Schritt für die Strukturaktivierung](/help/operations/replication.md#tree-activation). |
| [!DNL Foundation] | Weder die Registerkarte &quot;Verteilen&quot;des Administrationsbildschirms des Replikationsagenten noch die Replikations-API können zur Replikation von Inhaltspaketen über 10 MB verwendet werden. | [Veröffentlichung verwalten](/help/operations/replication.md#manage-publication) oder [Workflow für die Strukturaktivierung Schritt 3}](/help/operations/replication.md#tree-activation) |
| [!DNL Foundation] | Integrationen mit Anmeldeinformationen, die aus Adobe Developer Console-Projekten generiert wurden, verlieren schrittweise die Unterstützung für Service-Konto-Anmeldedaten (JWT). Neue Service-Konto-Anmeldedaten (JWT) können ab dem 1. Mai 2024 nicht mehr in der Adobe Developer Console erstellt werden. Vorhandene Service-Konto-Anmeldedaten (JWT) können jedoch noch bis zum 1. Januar 2025 für bereits konfigurierte Integrationen verwendet werden. Ab diesem Zeitpunkt funktionieren die vorhandenen Service-Konto-Anmeldedaten (JWT) nicht mehr und Kundinnen und Kunden müssen zu OAuth-Server-zu-Server-Anmeldedaten migrieren. [Weitere Informationen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/security/jwt-credentials-deprecation-in-adobe-developer-console). | [Migrieren](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#migration-overview) Sie zu OAuth-Server-zu-Server-Anmeldedaten. |
| [!DNL Foundation] | Publish Content Tree Workflow und der zugehörige Workflow-Schritt Publish-Inhaltsstruktur , der für die Replikation von Inhaltshierarchien verwendet wurde. | Verwenden Sie den Schritt [Workflow für die Strukturaktivierung](/help/operations/replication.md#tree-activation) , der leistungsfähiger ist. |


## Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden Funktionen aufgeführt, die aus [!DNL Experience Manager] mit [!DNL Experience Manager] as a [!DNL Cloud Service] entfernt wurden.

| Bereich | Funktion | Ersatz | Zieltermin für die Entfernung |
| ------------ | ------------------ | ----------- | ------------------- |
| Benutzeroberfläche | Die Classic-Benutzeroberfläche wurde aus der Produkt-Benutzeroberfläche entfernt. Für einige ausgewählte Funktionen wie Link Checker, Versionsbereinigung und einige Cloud Service-Konfigurationen sind einige Dialogfelder der Classic-Benutzeroberfläche verfügbar. Künftige [Produkt-Updates](/help/release-notes/home.md) können weitere verfügbare Elemente der Classic-Benutzeroberfläche entfernen. | Standard-Benutzeroberfläche | Entfernt |
| [!DNL Dynamic Media] | Frühere Integrationen mit [Dynamic Media Classic](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/scene7.html?lang=de#integration) und dem [Dynamic Media-Hybridmodus](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/config-dynamic.html?lang=de#dynamic) sind in [!DNL Experience Manager] as a [!DNL Cloud Service] nicht verfügbar. | Verwenden Sie [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md), das mit [!DNL Experience Manager] as a [!DNL Cloud Service]bereitgestellt wird. | Entfernt |
| [!DNL Sites] | Komponenten „Portal Director“ und „Portlet“ | Diese Funktionen gelten seit [!DNL Experience Manager] 6.4 als veraltet und wurden nun aus [!DNL Experience Manager] entfernt. | Entfernt |
| [!DNL Sites] | Design-Import-Tool | Diese Funktion wurde entfernt, da auf unveränderliche Abschnitte des [!DNL Experience Manager]-Repositorys nicht zur Laufzeit zugegriffen werden kann. | Entfernt |
| [!DNL Assets] | [!DNL Assets]-Freigabe für Marketing Cloud Assets Core Service und Creative Cloud-Services ist nicht verfügbar. | Zur Integration mit [!DNL Adobe Creative Cloud] verwenden Sie [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html). | Entfernt |
| [!DNL Foundation] | Unterstützung für Apache Sling-Datenquellen (OSGi-Bundle org.apache.sling.datasource) | Nicht zutreffend | Entfernt |
| [!DNL Foundation] | Unterstützung für JST-Skriptvorlagen (OSGi-Bundle org.apache.sling.scripting.jst) | Nicht zutreffend | Entfernt |
| [!DNL Foundation] | Unterstützung für das Apache Felix Http Whiteboard | OSGi Http Whiteboard | März 2022 |
| [!DNL Foundation] | Unterstützung für com.adobe.granite.oauth.server | Adobe IMS-Integration | März 2023 |
| [!DNL Foundation] | Unterstützung für die Funktion org.apache.sling.serviceusermapping, um die [Dienstbenutzer-ID abzurufen](https://sling.apache.org/apidocs/sling12/org/apache/sling/serviceusermapping/ServiceUserMapper.html#getServiceUserID-org.osgi.framework.Bundle-java.lang.String-) | Nicht zutreffend | 30.08.24 |


## AEM-APIs {#aem-apis}

Nachfolgend finden Sie eine ausführliche Liste veralteter AEM-APIs und das voraussichtliche Datum ihrer Entfernung. Von den Kunden wird erwartet, dass sie die APIs bis zum Zieltermin aus ihrem Code entfernen. Jegliche Verwendung der API nach dem Datum der Entfernung führt zu Fehlern in der lokalen SDK-/Entwicklungsumgebung und dem Cloud Manager-Build-Prozess.

<details>
  <summary>Erweitern, um die Liste veralteter APIs anzuzeigen.</summary>
<table style="table-layout:auto">
  <tr>
    <th>Package/Klasse</th>
    <th>Kommentare</th>
    <th>Verfallsdatum</th>
    <th>Zieltermin für die Entfernung</th>
  </tr>
<tbody>
  <tr>
    <td>org.apache.sling.commons.auth<br>org.apache.sling.commons.auth.spi</td>
    <td>Verwenden Sie alternativ die Auth Core-/Auth Core SPI-Schnittstellen von Sling. <a href="#org.apache.sling.commons.auth">Siehe die folgenden Hinweise zur Entfernung.</a></td>
    <td>2015</td>
    <td>30.07.2021</td>
  </tr>
  <tr>
    <td>org.apache.sling.runmode</td>
    <td></td>
    <td>2015</td>
    <td>30.07.2021</td>
  </tr>
  <tr>
    <td>com.day.cq.jcrclustersupport</td>
    <td>Verwenden Sie alternativ die Discovery-API von Sling</td>
    <td>2015</td>
    <td>entfernt</td>
  </tr>
  <tr>
    <td>org.apache.fop.apps</td>
    <td></td>
    <td>01.03.2021</td>
    <td>entfernt</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.vault.util.xml.xerces.dom<br>org.apache.jackrabbit.vault.util.xml.xerces.util<br>org.apache.jackrabbit.vault.util.xml.xerces.xni<br>org.apache.jackrabbit.vault.util.xml.xerces.xni.parser</td>
    <td></td>
    <td>05.03.2021</td>
    <td>entfernt</td>
  </tr>
  <tr>
    <td>org.json</td>
    <td>Die Apache Johnzon-Implementierung von <a href="https://johnzon.apache.org/index.html">javax.json</a> wird empfohlen und sollte verwendet werden. </td>
    <td>30.04.2021</td>
    <td>31.12.2021</td>
  </tr>
  <tr>
    <td>org.apache.felix.cm<br>org.apache.felix.cm.file</td>
    <td>Benutzerdefinierte Persistenz-Manager werden in AEM as a Cloud Service nicht unterstützt.</td>
    <td>30.04.2021</td>
    <td>entfernt</td>
  </tr>
  <tr>
    <td>org.apache.commons.lang<br>org.apache.commons.lang.enums<br>org.apache.commons.lang.builder<br>org.apache.commons.lang.exception<br>org.apache.commons.lang.math<br>org.apache.commons.lang.mutable<br>org.apache.commons.lang.reflect<br>org.apache.commons.lang.text<br>org.apache.commons.lang.time</td>
    <td>Commons Lang 2 befindet sich im Wartungsmodus. Stattdessen sollte Commons Lang 3 verwendet werden.</td>
    <td>30.04.2021</td>
    <td>31.12.2021</td>
  </tr>
  <tr>
    <td>org.apache.commons.collections<br>org.apache.commons.collections.bag<br>org.apache.commons.collections.bidimap<br>org.apache.commons.collections.buffer<br>org.apache.commons.collections.collection<br>org.apache.commons.collections.comparators<br>org.apache.commons.collections.functors<br>org.apache.commons.collections.iterators<br>org.apache.commons.collections.keyvalue<br>org.apache.commons.collections.list<br>org.apache.commons.collections.map<br>org.apache.commons.collections.set</td>
    <td>Commons Collections 3 befindet sich im Wartungsmodus. Stattdessen sollte Commons Collections 4 verwendet werden.</td>
    <td>30.04.2021</td>
    <td>31.12.2021</td>
  </tr>
  <tr>
    <td>org.apache.felix.systemready</td>
    <td>Es wird empfohlen, stattdessen die Apache Felix HealthCheck-API zu verwenden.</td>
    <td>30.04.2021</td>
    <td>entfernt</td>
  </tr>
  <tr>
    <td>org.apache.felix.webconsole<br>org.apache.felix.webconsole.bundleinfo<br>org.apache.felix.webconsole.i18n</td>
    <td>Die Felix-Web-Konsole wird in Cloud-Umgebungen nicht unterstützt.</td>
    <td>30.04.2021</td>
    <td>30.07.2021</td>
  </tr>
  <tr> <td>org.apache.felix.http.jetty<br>org.eclipse.jetty.client.jmx<br>org.eclipse.jetty.jmx<br>org.eclipse.jetty.server.handler.jmx<br>org.eclipse.jetty.server.nio<br>org.eclipse.jetty.server.jmx<br>org.eclipse.jetty.servlet.jmx<br>org.eclipse.jetty.util.preventers<br>org.eclipse.jetty.util.thread.strategy<br>org.eclipse.jetty.webapp<br>org.eclipse.jetty.websocket.api<br>org.eclipse.jetty.websocket.api.annotations<br>org.eclipse.jetty.websocket.api.extensions<br>org.eclipse.jetty.websocket.api.util<br>org.eclipse.jetty.websocket.client<br>org.eclipse.jetty.websocket.client.io<br>org.eclipse.jetty.websocket.client.masks<br>org.eclipse.jetty.websocket.common<br>org.eclipse.jetty.websocket.common.events<br>org.eclipse.jetty.websocket.common.events.annotated<br>org.eclipse.jetty.websocket.common.extensions<br>org.eclipse.jetty.websocket.common.extensions.compress<br>org.eclipse.jetty.websocket.common.extensions.fragment<br>org.eclipse.jetty.websocket.common.extensions.identity<br>org.eclipse.jetty.websocket.common.frames<br>org.eclipse.jetty.websocket.common.io<br>org.eclipse.jetty.websocket.common.io.http<br>org.eclipse.jetty.websocket.common.io.payload<br>org.eclipse.jetty.websocket.common.message<br>org.eclipse.jetty.websocket.common.scopes<br>org.eclipse.jetty.websocket.common.util<br>org.eclipse.jetty.websocket.server<br>org.eclipse.jetty.websocket.server.pathmap<br>org.eclipse.jetty.websocket.servlet<br>org.eclipse.jetty.xml</td>
    <td>Die Pakete Eclipse Jetty und Felix Http Jetty werden nicht mehr unterstützt. <a href="#org.eclipse.jetty">Siehe die folgenden Hinweise zur Entfernung.</a></td>
    <td>27.05.2021</td>
    <td>26.08.2021</td>
  </tr>
  <tr> <td>org.eclipse.jetty.client<br>org.eclipse.jetty.client.api<br>org.eclipse.jetty.client.http<br>org.eclipse.jetty.client.util<br>org.eclipse.jetty.http<br>org.eclipse.jetty.http.pathmap<br>org.eclipse.jetty.io<br>org.eclipse.jetty.io.ssl<br>org.eclipse.jetty.security<br>org.eclipse.jetty.server<br>org.eclipse.jetty.server.handler<br>org.eclipse.jetty.server.handler.gzip<br>org.eclipse.jetty.server.session<br>org.eclipse.jetty.servlet<br>org.eclipse.jetty.servlet.listener<br>org.eclipse.jetty.util<br>org.eclipse.jetty.util.annotation<br>org.eclipse.jetty.util.component<br>org.eclipse.jetty.util.log<br>org.eclipse.jetty.util.resource<br>org.eclipse.jetty.util.security<br>org.eclipse.jetty.util.ssl<br>org.eclipse.jetty.util.statistic<br>org.eclipse.jetty.util.thread
</td>
    <td>Die Pakete Eclipse Jetty und Felix Http Jetty werden nicht mehr unterstützt.</td>
    <td>27.05.2021</td>
    <td>26.08.2021</td>
  </tr>  
  <tr>     <td>com.mongodb<br>com.mongodb.annotations<br>com.mongodb.assertions<br>com.mongodb.async<br>com.mongodb.binding<br>com.mongodb.bulk<br>com.mongodb.client<br>com.mongodb.client.gridfs<br>com.mongodb.client.gridfs.codecs<br>com.mongodb.client.gridfs.model<br>com.mongodb.client.jndi<br>com.mongodb.client.model<br>com.mongodb.client.model.changestream<br>com.mongodb.client.model.geojson<br>com.mongodb.client.model.geojson.codecs<br>com.mongodb.client.result<br>com.mongodb.connection<br>com.mongodb.connection.netty<br>com.mongodb.diagnostics.logging<br>com.mongodb.event<br>com.mongodb.gridfs<br>com.mongodb.internal<br>com.mongodb.internal.async<br>com.mongodb.internal.authentication<br>com.mongodb.internal.connection<br>com.mongodb.internal.dns<br>com.mongodb.internal.event<br>com.mongodb.internal.management.jmx<br>com.mongodb.internal.session<br>com.mongodb.internal.thread<br>com.mongodb.internal.validator<br>com.mongodb.management<br>com.mongodb.operation<br>com.mongodb.selector<br>com.mongodb.session<br>com.mongodb.util</td>
    <td>Die Verwendung dieser API wird in AEM as a Cloud Service nicht unterstützt. <a href="#com.mongodb">Siehe die folgenden Hinweise zur Entfernung.</a></td>
    <td>27.05.2021</td>
    <td>30.07.2021</td>
  </tr>
  <tr>
    <td>org.apache.felix.metatype<br>org.apache.felix.scr<br>org.apache.felix.scr.info<br>org.apache.felix.scr.component</td>
    <td>Der Apache Felix-Metatyp und die SCR-APIs sind veraltet.  Verwenden Sie stattdessen den OSGi-Metatyp und die Declarative Service-APIs.</td>
    <td>27.05.2021</td>
    <td>entfernt</td>
  </tr>
  <tr>
    <td>org.slf4j.impl</td>
    <td>Protokollimplementierungsklassen sind mit AEM as a Cloud Service nicht kompatibel.</td>
    <td>04.07.2021</td>
    <td>entfernt</td>
  </tr>
  <tr>
    <td>org.apache.abdera<br>org.apache.abdera.model<br>org.apache.abdera.factory<br>org.apache.abdera.ext.media<br>org.apache.abdera.util<br>org.apache.abdera.i18n.iri<br>org.apache.abdera.writer<br>org.apache.abdera.i18n.rfc4646<br>org.apache.abdera.i18n.rfc4646.enums<br>org.apache.abdera.i18n.text<br>org.apache.abdera.filter<br>org.apache.abdera.xpath<br>org.apache.abdera.i18n.text.io<br>org.apache.abdera.i18n.text.data<br>org.apache.abdera.parser</td>
    <td>Diese API wird nicht mehr unterstützt, da das Projekt Apache Abdera 2017 eingestellt wurde. <a href="#org.apache.abdera_or_org.apache.sling.atom.taglib">Siehe die folgenden Hinweise zur Entfernung.</a></td>
    <td>29.07.2021</td>
    <td>29.09.2021</td>
  </tr>
  <tr>
    <td>org.apache.abdera.ext.opensearch<br>org.apache.abdera.ext.opensearch.model<br>org.apache.abdera.ext.opensearch.server<br>org.apache.abdera.ext.opensearch.server.impl<br>org.apache.abdera.ext.opensearch.server.processors<br>org.apache.abdera.i18n.iri.data<br>org.apache.abdera.i18n.lang<br>org.apache.abdera.i18n.templates<br>org.apache.abdera.i18n.unicode.data<br>org.apache.abdera.parser.stax<br>org.apache.abdera.parser.stax.util<br>org.apache.abdera.protocol<br>org.apache.abdera.protocol.client<br>org.apache.abdera.protocol.client.cache<br>org.apache.abdera.protocol.client.util<br>org.apache.abdera.protocol.error<br>org.apache.abdera.protocol.server<br>org.apache.abdera.protocol.server.context<br>org.apache.abdera.protocol.server.filters<br>org.apache.abdera.protocol.server.impl<br>org.apache.abdera.protocol.server.multipart<br>org.apache.abdera.protocol.server.processors<br>org.apache.abdera.protocol.server.provider.basic<br>org.apache.abdera.protocol.server.provider.managed<br>org.apache.abdera.protocol.server.servlet<br>org.apache.abdera.protocol.util<br>org.apache.abdera.util.filter</td>
    <td>Diese API wird nicht mehr unterstützt, da das Projekt Apache Abdera 2017 eingestellt wurde.</td>
    <td>08.04.2019</td>
    <td>29.09.2021</td>
  </tr>
  <tr>
    <td>org.apache.sling.startupfilter<br>com.adobe.granite.crypto.spi<br>com.adobe.granite.crpyto.spi.base<br>com.adobe.agl.impl.data.icudt40b<br>com.adobe.agl.impl.data.icudt40b.brkitr<br>com.adobe.agl.impl.data.icudt40b.coll<br>com.adobe.agl.impl.data.icudt40b.rbnf<br>com.<br>adobe.agl.impl.data.icudt40b.translit<br>com.adobe.internal.pdf.tika<br>com.adobe.internal.pdftoolkit.color<br>com.adobe.internal.pdftoolkit.core.encryption<br>com.adobe.internal.pdftoolkit.core.encryption.impl<br>com.adobe.internal.pdftoolkit.core.traverser<br>com.adobe.internal.pdftoolkit.graphicsDOM<br>com.adobe.internal.pdftoolkit.graphicsDOM.shading<br>com.adobe.internal.pdftoolkit.graphicsDOM.utils<br>com.adobe.internal.pdftoolkit.image<br>com.adobe.internal.pdftoolkit.pdf.content<br>com.adobe.internal.pdftoolkit.pdf.content.processor<br>com.adobe.internal.pdftoolkit.pdf.content.processor.base14fontwidths<br>com.adobe.internal.pdftoolkit.pdf.contentmodify<br>com.adobe.internal.pdftoolkit.pdf.contentmodify.impl<br>com.adobe.internal.pdftoolkit.pdf.digsig<br>com.adobe.internal.pdftoolkit.pdf.document<br>com.adobe.internal.pdftoolkit.pdf.document.listener<br>com.adobe.internal.pdftoolkit.pdf.document.permissionhandlers<br>com.adobe.internal.pdftoolkit.pdf.filters<br>com.adobe.internal.pdftoolkit.pdf.graphics<br>com.adobe.internal.pdftoolkit.pdf.graphics.colorspaces<br>com.adobe.internal.pdftoolkit.pdf.graphics.colorspaces.cmykresources<br>com.adobe.internal.pdftoolkit.pdf.graphics.font<br>com.adobe.internal.pdftoolkit.pdf.graphics.font.encodings<br>com.adobe.internal.pdftoolkit.pdf.graphics.font.impl<br>com.adobe.internal.pdftoolkit.pdf.graphics.impl<br>com.adobe.internal.pdftoolkit.pdf.graphics.optionalcontent<br>com.adobe.internal.pdftoolkit.pdf.graphics.patterns<br>com.adobe.internal.pdftoolkit.pdf.graphics.shading<br>com.adobe.internal.pdftoolkit.pdf.graphics.xobject<br>com.adobe.internal.pdftoolkit.pdf.impl<br>com.adobe.internal.pdftoolkit.pdf.inlineimage<br>com.adobe.internal.pdftoolkit.pdf.interactive<br>com.adobe.internal.pdftoolkit.pdf.interactive.action<br>com.adobe.internal.pdftoolkit.pdf.interactive.annotation<br>com.adobe.internal.pdftoolkit.pdf.interactive.forms<br>com.adobe.internal.pdftoolkit.pdf.interactive.forms.impl<br>com.adobe.internal.pdftoolkit.pdf.interactive.geospatial<br>com.adobe.internal.pdftoolkit.pdf.interactive.markedcontent<br>com.adobe.internal.pdftoolkit.pdf.interactive.navigation<br>com.adobe.internal.pdftoolkit.pdf.interactive.navigation.collection<br>com.adobe.internal.pdftoolkit.pdf.interactive.readerrequirements<br>com.adobe.internal.pdftoolkit.pdf.interactive.requirement<br>com.adobe.internal.pdftoolkit.pdf.interchange<br>com.adobe.internal.pdftoolkit.pdf.interchange.documentparts<br>com.adobe.internal.pdftoolkit.pdf.interchange.metadata<br>com.adobe.internal.pdftoolkit.pdf.interchange.prepress<br>com.adobe.internal.pdftoolkit.pdf.interchange.structure<br>com.adobe.internal.pdftoolkit.pdf.multimedia<br>com.adobe.internal.pdftoolkit.pdf.page<br>com.adobe.internal.pdftoolkit.pdf.rendering<br>com.adobe.internal.pdftoolkit.pdf.transparency<br>com.adobe.internal.pdftoolkit.pdf.utils<br>com.adobe.internal.pdftoolkit.services.Jpeg2000<br>com.adobe.internal.pdftoolkit.services.fontresources<br>com.adobe.internal.pdftoolkit.services.fontresources.subsetting<br>com.adobe.internal.pdftoolkit.services.interchange.structure<br>com.adobe.internal.pdftoolkit.services.optionalcontent<br>com.adobe.internal.pdftoolkit.services.optionalcontent.impl<br>com.adobe.internal.pdftoolkit.services.pdfParser<br>com.adobe.internal.pdftoolkit.services.permissions<br>com.adobe.internal.pdftoolkit.services.rasterizer<br>com.adobe.internal.pdftoolkit.services.readingorder<br>com.adobe.internal.pdftoolkit.services.security<br>com.adobe.internal.pdftoolkit.services.swf<br>com.adobe.internal.pdftoolkit.services.textextraction<br>com.adobe.internal.pdftoolkit.services.textextraction.impl<br>com.adobe.internal.pdftoolkit.services.xmp<br>com.adobe.internal.util.base64<br>com.adobe.internal.xmp.utils<br>com.day.crx.core.cluster<br>com.day.crx.packaging<br>com.day.crx.packaging.gfx<br>com.day.crx.query<br>com.day.crx.sling.server.jmx<br>com.day.durbo<br>com.day.durbo.io<br>com.day.imageio.plugins<br>org.apache.aries.jmx.codec<br>org.h2.mvstore<br>org.h2.mvstore.rtree<br>org.h2.mvstore.type<br>org.openxmlformats.schemas.drawingml.x2006.chart.impl<br>org.openxmlformats.schemas.drawingml.x2006.main.impl<br>org.openxmlformats.schemas.drawingml.x2006.picture.impl<br>org.openxmlformats.schemas.drawingml.x2006.spreadsheetDrawing.impl<br>org.openxmlformats.schemas.drawingml.x2006.wordprocessingDrawing.impl<br>org.openxmlformats.schemas.officeDocument.x2006.customProperties.impl<br>org.openxmlformats.schemas.officeDocument.x2006.docPropsVTypes.impl<br>org.openxmlformats.schemas.officeDocument.x2006.extendedProperties.impl<br>org.openxmlformats.schemas.officeDocument.x2006.relationships.impl<br>org.openxmlformats.schemas.presentationml.x2006.main.impl<br>org.openxmlformats.schemas.spreadsheetml.x2006.main.impl<br>org.openxmlformats.schemas.wordprocessingml.x2006.main.impl<br>org.openxmlformats.schemas.xpackage.x2006.contentTypes<br>org.openxmlformats.schemas.xpackage.x2006.contentTypes.impl<br>org.openxmlformats.schemas.xpackage.x2006.digitalSignature<br>org.openxmlformats.schemas.xpackage.x2006.digitalSignature.impl<br>org.openxmlformats.schemas.xpackage.x2006.metadata.coreProperties<br>org.openxmlformats.schemas.xpackage.x2006.metadata.coreProperties.impl<br>org.openxmlformats.schemas.xpackage.x2006.relationships<br>org.openxmlformats.schemas.xpackage.x2006.relationships.impl<br>com.adobe.internal.afml<br>com.adobe.internal.agm<br>com.adobe.internal.pdftoolkit.legacy.services.ap.es2<br>com.adobe.internal.pdftoolkit.legacy.services.ap.es3<br>com.adobe.internal.pdftoolkit.pdf.pieceinfo.compoundtype<br>com.adobe.internal.pdftoolkit.pdf.pieceinfo.editablepdf<br>com.adobe.internal.pdftoolkit.services.ap<br>com.adobe.internal.pdftoolkit.services.ap.annot<br>com.adobe.internal.pdftoolkit.services.ap.extension<br>com.adobe.internal.pdftoolkit.services.ap.impl<br>com.adobe.internal.pdftoolkit.services.ap.spi<br>com.adobe.internal.pdftoolkit.services.digsig<br>com.adobe.internal.pdftoolkit.services.digsig.cryptoprovider<br>com.adobe.internal.pdftoolkit.services.digsig.docmodanalysis<br>com.adobe.internal.pdftoolkit.services.digsig.spi<br>com.adobe.internal.pdftoolkit.services.fdf<br>com.adobe.internal.pdftoolkit.services.formflattener<br>com.adobe.internal.pdftoolkit.services.forms<br>com.adobe.internal.pdftoolkit.services.imageconversion<br>com.adobe.internal.pdftoolkit.services.javascript<br>com.adobe.internal.pdftoolkit.services.javascript.extension<br>com.adobe.internal.pdftoolkit.services.manipulations<br>com.adobe.internal.pdftoolkit.services.manipulations.impl<br>com.adobe.internal.pdftoolkit.services.optimizer<br>com.adobe.internal.pdftoolkit.services.pdfa<br>com.adobe.internal.pdftoolkit.services.pdfa.error<br>com.adobe.internal.pdftoolkit.services.pdfa2<br>com.adobe.internal.pdftoolkit.services.pdfa2.error<br>com.adobe.internal.pdftoolkit.services.pdfa2.error.codes<br>com.adobe.internal.pdftoolkit.services.pdfa3<br>com.adobe.internal.pdftoolkit.services.pdfport<br>com.adobe.internal.pdftoolkit.services.portfolio<br>com.adobe.internal.pdftoolkit.services.rcg<br>com.adobe.internal.pdftoolkit.services.rcg.impl<br>com.adobe.internal.pdftoolkit.services.redaction<br>com.adobe.internal.pdftoolkit.services.redaction.handler<br>com.adobe.internal.pdftoolkit.services.sanitization<br>com.adobe.internal.pdftoolkit.services.xbm<br>com.adobe.internal.pdftoolkit.services.xdp<br>com.adobe.internal.pdftoolkit.services.xfa<br>com.adobe.internal.pdftoolkit.services.xfa.form<br>com.adobe.internal.pdftoolkit.services.xfatext<br>com.adobe.internal.pdftoolkit.services.xfdf<br>com.adobe.internal.pdftoolkit.services.xobjhandler<br>com.adobe.internal.pdftoolkit.xml<br>com.adobe.octopus.extract<br>opennlp.tools.doccat<br>opennlp.tools.entitylinker<br>opennlp.tools.formats<br>opennlp.tools.formats.ad<br>opennlp.tools.formats.brat<br>opennlp.tools.formats.convert<br>opennlp.tools.formats.frenchtreebank<br>opennlp.tools.formats.muc<br>opennlp.tools.formats.ontonotes<br>opennlp.tools.lemmatizer<br>opennlp.tools.parser<br>opennlp.tools.parser.chunking<br>opennlp.tools.parser.lang.en<br>opennlp.tools.parser.lang.es<br>opennlp.tools.parser.treeinsert<br>opennlp.tools.sentdetect<br>opennlp.tools.sentdetect.lang<br>opennlp.tools.sentdetect.lang.th<br>opennlp.tools.stemmer<br>opennlp.tools.stemmer.snowball<br>opennlp.tools.tokenize.lang.en<br>org.apache.commons.imaging.color<br>org.apache.commons.imaging.common<br>org.apache.commons.imaging.common.itu_t4<br>org.apache.commons.imaging.common.mylzw<br>org.apache.commons.imaging.formats.bmp<br>org.apache.commons.imaging.formats.dcx<br>org.apache.commons.imaging.formats.gif<br>org.apache.commons.imaging.formats.icns<br>org.apache.commons.imaging.formats.ico<br>org.apache.commons.imaging.formats.jpeg<br>org.apache.commons.imaging.formats.jpeg.decoder<br>org.apache.commons.imaging.formats.jpeg.exif<br>org.apache.commons.imaging.formats.jpeg.iptc<br>org.apache.commons.imaging.formats.jpeg.segments<br>org.apache.commons.imaging.formats.jpeg.xmp<br>org.apache.commons.imaging.formats.pcx<br>org.apache.commons.imaging.formats.png<br>org.apache.commons.imaging.formats.png.chunks<br>org.apache.commons.imaging.formats.png.scanlinefilters<br>org.apache.commons.imaging.formats.png.transparencyfilters<br>org.apache.commons.imaging.formats.pnm<br>org.apache.commons.imaging.formats.psd<br>org.apache.commons.imaging.formats.psd.dataparsers<br>org.apache.commons.imaging.formats.psd.datareaders<br>org.apache.commons.imaging.formats.rgbe<br>org.apache.commons.imaging.formats.tiff<br>org.apache.commons.imaging.formats.tiff.constants<br>org.apache.commons.imaging.formats.tiff.datareaders<br>org.apache.commons.imaging.formats.tiff.fieldtypes<br>org.apache.commons.imaging.formats.tiff.photometricinterpreters<br>org.apache.commons.imaging.formats.tiff.taginfos<br>org.apache.commons.imaging.formats.tiff.write<br>org.apache.commons.imaging.formats.wbmp<br>org.apache.commons.imaging.formats.xbm<br>org.apache.commons.imaging.formats.xpm<br>org.apache.commons.imaging.icc<br>org.apache.commons.imaging.palette<br>org.apache.commons.imaging.util<br>com.adobe.dam.print.ids.utils<br>com.day.cq.dam.api.reporting<br>com.day.cq.dam.entitlement.api<br>com.day.cq.dam.handler.standard.epub<br>com.day.cq.dam.handler.standard.keynote<br>com.day.cq.dam.handler.standard.mp3<br>com.day.cq.dam.handler.standard.msoffice<br>com.day.cq.dam.handler.standard.msoffice.wmf<br>com.day.cq.dam.handler.standard.ooxml<br>com.day.cq.dam.handler.standard.pdf<br>com.day.cq.dam.handler.standard.pict<br>com.day.cq.dam.handler.standard.ps<br>com.day.cq.dam.handler.standard.psd<br>com.day.cq.dam.handler.standard.zip<br>com.day.cq.dam.word.extraction<br>com.day.cq.dam.word.process<br>com.adobe.xmp.worker.files<br>com.adobe.cq.address.api<br>com.adobe.cq.address.api.location<br>com.day.cq.mcm.emailprovider.impl.types<br>com.day.io<br>com.day.io.disk<br>com.day.io.file<br>org.apache.commons.exec.environment<br>org.apache.commons.exec.launcher<br>org.apache.commons.exec.util<br>com.google.zxing<br>com.google.zxing.common<br>com.google.zxing.common.reedsolomon<br>com.google.zxing.qrcode.decoder<br>com.google.zxing.qrcode.encoder<br>com.adobe.cq.dam.dm.internalapi.image_server<br>com.day.cq.dam.api.s7dam.jobs<br>com.day.cq.dam.api.s7dam.omnisearch<br>com.day.cq.dam.api.s7dam.scene7<br>com.day.cq.dam.scene7<br>com.day.cq.dam.scene7.api.net<br>com.day.cq.analytics.sitecatalyst.rsmerger<br>com.day.cq.searchpromote<br>com.day.cq.searchpromote.xml<br>com.day.cq.searchpromote.xml.form<br>com.day.cq.searchpromote.xml.result&gt;</td>
    <td>Alte AEM 6.x-API.</td>
    <td>08.04.2019</td>
    <td>entfernt</td>
  </tr>
  <tr>
    <td>org.apache.sling.discovery.commons<br>org.apache.sling.discovery.commons.providers<br>org.apache.sling.discovery.commons.providers.base<br>org.apache.sling.discovery.commons.providers.spi<br>org.apache.sling.discovery.commons.providers.spi.base<br>org.apache.sling.discovery.commons.providers.util</td>
    <td>Diese API wird in Cloud Service nicht unterstützt.</td>
    <td>30.09.21</td>
    <td>entfernt</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.vault.util.xml<br>org.apache.jackrabbit.vault.util.xml.serialize</td>
    <td>Util-Klassen, die sich auf Apache Xerces beziehen, werden in späteren Versionen entfernt, was eine größere Versionsänderung zur Folge hat. Da diese Util-Klassen für den internen Gebrauch in Filevault bestimmt sind, wird die API aus der öffentlichen API-Oberfläche entfernt.</td>
    <td>01.09.21</td>
    <td>entfernt</td>
  <tr>
    <td>org.apache.sling.atom.taglib<br>org.apache.sling.atom.taglib.media</td>
    <td>Alte AEM 6.x-API. <a href="#org.apache.abdera_or_org.apache.sling.atom.taglib">Siehe die folgenden Hinweise zur Entfernung.</a></td>
    <td>08.04.2019</td>
    <td>29.09.2021</td>
  </tr>
  <tr>
    <td>org.apache.felix.http.whiteboard</td>
    <td>Das Apache Felix Http-Whiteboard wird nicht mehr unterstützt. Migrieren Sie Ihren Code zum OSGi Http-Whiteboard. <a href="#org.apache.felix.http.whiteboard">Siehe die folgenden Hinweise zur Entfernung.</a></td>
    <td>27.01.2022</td>
    <td>24.03.2022</td>
  </tr>
  <tr>
    <td>org.apache.cocoon.xml.dom<br>org.apache.cocoon.xml.sax</td>
    <td>Diese API ist veraltet. Migrieren Sie Ihren Code zu den vom JDK bereitgestellten XML-APIs.</td>
    <td>27.01.2022</td>
    <td>24.03.2022</td>
  </tr>
  <tr>
    <td>ch.qos.logback.classic<br>ch.qos.logback.classic.boolex<br>ch.qos.logback.classic.db.names<br>ch.qos.logback.classic.db.script<br>ch.qos.logback.classic.encoder<br>ch.qos.logback.classic.filter<br>ch.qos.logback.classic.helpers<br>ch.qos.logback.classic.html<br>ch.qos.logback.classic.jmx<br>ch.qos.logback.classic.joran<br>ch.qos.logback.classic.joran.action<br>ch.qos.logback.classic.jul<br>ch.qos.logback.classic.layout<br>ch.qos.logback.classic.log4j<br>ch.qos.logback.classic.net<br>ch.qos.logback.classic.net.server<br>ch.qos.logback.classic.pattern<br>ch.qos.logback.classic.pattern.color<br>ch.qos.logback.classic.selector<br>ch.qos.logback.classic.selector.servlet<br>ch.qos.logback.classic.servlet<br>ch.qos.logback.classic.sift<br>ch.qos.logback.classic.spi<br>ch.qos.logback.classic.turbo<br>ch.qos.logback.classic.util<br>ch.qos.logback.core<br>ch.qos.logback.core.boolex<br>ch.qos.logback.core.encoder<br>ch.qos.logback.core.filter<br>ch.qos.logback.core.helpers<br>ch.qos.logback.core.hook<br>ch.qos.logback.core.html<br>ch.qos.logback.core.joran<br>ch.qos.logback.core.joran.action<br>ch.qos.logback.core.joran.conditional<br>ch.qos.logback.core.joran.event<br>ch.qos.logback.core.joran.event.stax<br>ch.qos.logback.core.joran.node<br>ch.qos.logback.core.joran.spi<br>ch.qos.logback.core.joran.util<br>ch.qos.logback.core.joran.util.beans<br>ch.qos.logback.core.layout<br>ch.qos.logback.core.net<br>ch.qos.logback.core.net.server<br>ch.qos.logback.core.net.ssl<br>ch.qos.logback.core.pattern<br>ch.qos.logback.core.pattern.color<br>ch.qos.logback.core.pattern.parser<br>ch.qos.logback.core.pattern.util<br>ch.qos.logback.core.property<br>ch.qos.logback.core.read<br>ch.qos.logback.core.recovery<br>ch.qos.logback.core.rolling<br>ch.qos.logback.core.rolling.helper<br>ch.qos.logback.core.sift<br>ch.qos.logback.core.spi<br>ch.qos.logback.core.status<br>ch.qos.logback.core.subst<br>ch.qos.logback.core.util</td>
    <td>Diese interne Logback-API wird von AEM as a Cloud Service nicht unterstützt.</td>
    <td>27.01.2022</td>
    <td>24.03.2022</td>
  </tr>
  <tr>
    <td>org.slf4j.spi</td>
    <td>Diese interne log4j-API wird von AEM as a Cloud Service nicht unterstützt.</td>
    <td>27.01.2022</td>
    <td>24.03.2022</td>
  </tr>
  <tr>
    <td>org.apache.log4j<br>org.apache.log4j.helpers<br>org.apache.log4j.spi<br>org.apache.log4j.xml</td>
    <td>Apache Log4j 1 wurde 2015 eingestellt und wird nicht mehr unterstützt.</td>
    <td>27.01.2022</td>
    <td>24.03.2022</td>
  </tr>
  <tr>
    <td>org.apache.sling.commons.log.logback<br>org.apache.sling.commons.log.logback.webconsole</td>
    <td>Diese interne Logback-API wird von AEM as a Cloud Service nicht unterstützt.</td>
    <td>27.01.2022</td>
    <td>entfernt</td>
  </tr>
  <tr>
    <td>com.github.jknack.handlebars.js</td>
    <td>Aufgrund von Sicherheitslücken ist ein Upgrade von Handlebars von 4.0.5 auf 4.3.0 erforderlich. Dieses Paket ist in der aktualisierten Handlebars-Version nicht mehr vorhanden.</td>
    <td>5.5.2022</td>
    <td>5.8.2022</td>
  </tr>
  <tr>
    <td>com.adobe.granite.resourceresolverhelper</td>
    <td>Diese API wird nicht mehr unterstützt. Verwenden Sie stattdessen org.apache.sling.api.resource.ResourceResolverFactory.</td>
    <td>29.9.2022</td>
    <td>24.11.2022</td>
  </tr>
  <tr>
    <td>com.day.cq.contentsync.handler.util</td>
    <td>Diese API wird nicht mehr unterstützt. Verwenden Sie stattdessen die Builder von Apache Sling.</td>
    <td>31.10.2022</td>
    <td>01.01.2023</td>
  </tr>
  <tr><td>org.apache.sling.commons.json<br>org.apache.sling.commons.json.http<br>org.apache.sling.commons.json.io<br>org.apache.sling.commons.json.jcr<br>org.apache.sling.commons.json.sling<br>org.apache.sling.commons.json.util<br>org.apache.sling.commons.json.xml</td>
    <td>Diese API wird von AEM as a Cloud Service nicht unterstützt.</td>
    <td>15.5.2023</td>
    <td>15.6.2023</td>
  </tr><td>com.google.common.annotations<br>com.google.common.base<br>com.google.common.cache<br>com.google.common.collect<br>com.google.common.escape<br>com.google.common.eventbus<br>com.google.common.hash<br>com.google.common.html<br>com.google.common.io<br>com.google.common.math<br>com.google.common.net<br>com.google.common.primitives<br>com.google.common.reflect<br>com.google.common.util.concurrent<br>com.google.common.xml</td>
    <td>Die Google Guava-Kernbibliotheken werden nicht mehr unterstützt.</td>
    <td>15.5.2023</td>
    <td>15.6.2023</td>
  </tr>
  <tr>
    <td>org.slf4j.event    </td>
    <td>Diese interne slf4j-API wird von AEM as a Cloud Service nicht unterstützt.</td>
    <td>11.4.2022</td>
    <td>30.08.2024</td>
  </tr>
  <tr>
    <td>org.apache.sling.repoinit.jcr<br>org.apache.sling.repoinit.parser.operations</td>
    <td>Die Verwendung dieser API wird in AEM as a Cloud Service nicht unterstützt.</td>
    <td>17.05.2024</td>
    <td>30.06.2024</td>
  </tr>
  <tr>
    <td>com.day.cq.xss<br>com.day.cq.xss.taglib<br>com.day.cq.xss.impl</td>
    <td>Verwenden Sie stattdessen org.apache.sling.xss.</td>
    <td>12.12.2023</td>
    <td>30.06.2024</td>
  </tr>
  <tr>
    <td>com.adobe.granite.xss<br>com.adobe.granite.xss.impl</td>
    <td>Verwenden Sie stattdessen org.apache.sling.xss.</td>
    <td>12.12.2023</td>
    <td>30.06.2024</td>
  </tr>  
  <tr>
    <td>com.drew.*</td>
    <td>Das Extrahieren von Metadaten aus Bildern und Videos sollte über Asset Compute im Cloud Service oder über Apache POI oder Apache Tika erfolgen.</td>
    <td>17.09.2024</td>
    <td>17.12.2024</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.oak.plugins.blob.*</td>
    <td></td>
    <td>23.09.2024</td>
    <td>23.12.2024</td>
  </tr>       
</tbody>
</table>
</details>

### Entfernung von `org.apache.sling.commons.auth*` {#org.apache.sling.commons.auth}

Wenn Sie `org.apache.sling.commons.auth` und/oder `org.apache.sling.commons.auth.spi` verwenden, kann die Verwendung durch eine Migration des Codes zu `org.apache.sling.auth` bzw. `org.apache.sling.auth.spi` ersetzt werden. Wenn Sie eine alte [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/)-Version verwenden, stellen Sie sicher, dass Sie auf die neueste Version aktualisieren.

Aktionsliste:
* Aktualisieren von ACS AEM Commons auf die neueste Version
* Migration von `org.apache.sling.commons.auth` und/oder `org.apache.sling.commons.auth.spi` zu `org.apache.sling.auth` bzw. `org.apache.sling.auth.spi`.

### Entfernung von `org.eclipse.jetty*` {#org.eclipse.jetty}

Wenn Sie Bestandteile aus dem Paket `org.eclipse.jetty` oder einem seiner Unterpakete verwenden, empfiehlt es sich möglicherweise, auf andere Bibliotheken von Drittanbietern mit einer ähnlichen Funktionalität zu migrieren. Wenn die Migration nicht möglich ist, fügen Sie Ihrem Projekt die erforderlichen Bundles aus der folgenden Liste hinzu.

Aktionsliste:
* Ersetzen Sie die Verwendung von `org.eclipse.jetty`-Paketen durch andere Drittanbieter-Bibliotheken bzw. eigenen Code oder
* Wählen Sie die erforderlichen Bundles aus dieser Liste aus und fügen Sie sie zu Ihrem Projekt hinzu:
   * `org.eclipse.jetty:jetty-client:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-http:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-io:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-security:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-servlet:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-server:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-util:9.4.54.v20240208`
   * `org.eclipse.jetty:jetty-util-ajax:9.4.54.v20240208`

### Entfernung von `com.mongodb` {#com.mongodb}

Fügen Sie die Mongo-Client-API zu Ihrem Projekt hinzu.

Aktionsliste:
* Fügen Sie dieses Bundle zu Ihrem Projekt hinzu
   * `org.mongodb:mongo-java-driver:3.12.7`

### Verwendung von `org.apache.abdera*` und `org.apache.sling.atom.taglib` {#org.apache.abdera_or_org.apache.sling.atom.taglib}

Ersetzen Sie die Verwendung von Paketen aus `org.apache.abdera` und `org.apache.sling.atom.taglib` durch eine Bibliothek eines Drittanbieters, die ähnliche Funktionen bietet, oder Ihren eigenen Code.

Aktionsliste:
* Ersetzen Sie die Verwendung von Paketen aus `org.apache.abdera` und `org.apache.sling.atom.taglib` durch andere Bibliotheken von Drittanbietern oder eigenen Code.

### Verwendung von `org.apache.felix.http.whiteboard` {#org.apache.felix.http.whiteboard}

Ersetzen Sie die Verwendung von `org.apache.felix.http.whiteboard` durch das [OSGi Http Whiteboard](https://docs.osgi.org/specification/osgi.cmpn/7.0.0/service.http.whiteboard.html). Die offizielle OSGi-API weist ähnliche Funktionen auf. Beim Ersetzen müssen in den meisten Fällen nur die Eigenschaften für die Dienstregistrierung geändert werden.

Aktionsliste:
* Ersetzen Sie die Verwendung von `org.apache.felix.http.whiteboard` durch [OSGi Http Whiteboard](https://docs.osgi.org/specification/osgi.cmpn/7.0.0/service.http.whiteboard.html)

## OSGi-Konfiguration {#osgi-configuration}

Die beiden folgenden Listen spiegeln die OSGi-Konfigurationsoberfläche für AEM as a Cloud Service wider und beschreiben, was Kunden konfigurieren können.

1. Eine Liste der OSGi-Konfigurationen, die nicht per Kunden-Code konfiguriert werden dürfen.
1. Eine Liste der OSGi-Konfigurationen, deren Eigenschaften zwar konfiguriert werden können, aber die angegebenen Validierungsregeln einhalten müssen. Zu diesen Regeln gehört, ob die Deklaration der Eigenschaft erforderlich ist, ihr Typ und in einigen Fällen ihr zulässiger Wertebereich.

Wenn eine OSGi-Konfiguration nicht aufgeführt ist, kann sie durch Kunden-Code konfiguriert werden.

Diese Regeln werden während des Build-Prozesses von Cloud Manager validiert. Im Laufe der Zeit können zusätzliche Regeln hinzugefügt werden, und das erwartete Erzwingungsdatum wird in der Tabelle angegeben. Von Kunden wird erwartet, dass sie diese Regeln bis zum Zieltermin für die Erzwingung einhalten. Werden die Regeln nach dem Entfernungsdatum nicht eingehalten, treten im Build-Prozess von Cloud Manager Fehler auf. Maven-Projekte sollten das [Build Analyzer-Maven-Plug-in des AEM as a Cloud Service-SDK](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=de) enthalten, um OSGi-Konfigurationsfehler während der lokalen SDK-Entwicklung zu kennzeichnen.

Weitere Informationen zur OSGi-Konfiguration finden Sie [hier](/help/implementing/deploying/configuring-osgi.md).

+++OSGi-Konfigurationen, die nicht geändert werden können.
* **`org.apache.felix.webconsole.internal.servlet.OsgiManager`** (Ankündigungsdatum: 30.04.2021, Erzwingungsdatum: 31.07.2021)
* **`com.day.cq.auth.impl.cug.CugSupportImpl`** (Ankündigungsdatum: 30.04.2021, Erzwingungsdatum: 31.07.2021)
* **`com.day.cq.jcrclustersupport.ClusterStartLevelController`** (Ankündigungsdatum: 30.04.2021, Erzwingungsdatum: 31.07.2021)
* **`org.apache.felix.http (Factory)`** (Ankündigungsdatum: 30.04.2021, Erzwingungsdatum: 31.07.2021)
* **`org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`** (Ankündigungsdatum: 25.08.2021, Erzwingungsdatum: 26.11.2021)
+++

+++OSGi-Konfigurationen, die Build-Validierungsregeln unterliegen.
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
* **`org.apache.sling.commons.log.LogManager.factory.config`** (Ankündigungsdatum: 16.11.2021, Erzwingungsdatum: 16.02.2021)
   * `org.apache.sling.commons.log.level`
      * Typ: enumeration
      * Erforderlicher Bereich: INFO, DEBUG oder TRACE
   * `org.apache.sling.commons.log.names`
      * Typ: string
   * `org.apache.sling.commons.log.file`
      * Typ: string
   * `org.apache.sling.commons.log.additiv`
      * Typ: boolean
+++

## Aktualisierung von Java Runtime auf Version 21 {#java-runtime-update-21}

AEM as a Cloud Service wechselt zu Java Runtime 21. Um die Kompatibilität zu gewährleisten, müssen folgende Anpassungen vorgenommen werden:

### Anforderungen an die Build-Zeit :

#### Mindestversion von org.objectweb.asm {#org.objectweb.asm}

Aktualisieren Sie org.objectweb.asm auf Version 9.5 oder höher, um Unterstützung für neuere JVM-Laufzeitumgebungen sicherzustellen.

#### Mindestversion von org.apache.groovy {#org.apache.groovy}

Aktualisieren Sie org.apache.groovy auf Version 4.0.22 oder höher, um Unterstützung für neuere JVM-Laufzeitumgebungen sicherzustellen.

Dieses Paket kann indirekt durch Hinzufügen von Abhängigkeiten von Dritten wie der AEM Groovy Console eingeschlossen werden.

#### Minimale Version von bnd-maven-plugin {#bnd-maven-plugin}

Aktualisieren Sie die Verwendung von bnd-maven-plugin auf Version 6.4.0 oder höher, um Unterstützung für neuere JVM-Laufzeitumgebungen sicherzustellen.

#### Minimale Version von aemanalyser-maven-plugin {#aemanalyser-maven-plugin}

Aktualisieren Sie die Verwendung von aemanalyser-maven-plugin auf Version 1.6.6 oder höher, um Unterstützung für neuere JVM-Laufzeitumgebungen sicherzustellen.

#### Mindestversion von maven-bundle-plugin  {#maven-bundle-plugin}

Aktualisieren Sie die Verwendung von maven-bundle-plugin auf Version 5.1.5 oder höher, um Unterstützung für neuere JVM-Laufzeitumgebungen sicherzustellen.

#### Aktualisieren von Abhängigkeiten im maven-scr-plugin  {#maven-scr-plugin}

Die `maven-scr-plugin` ist nicht direkt mit Java 17 und 21 kompatibel. Es ist jedoch möglich, die Deskriptordateien zu generieren, indem die ASM-Abhängigkeitsversion innerhalb der Plug-in-Konfiguration aktualisiert wird, ähnlich dem unten stehenden Snippet:

```
[source,xml]
 <project>
   ...
   <build>
     ...
     <plugins>
       ...
       <plugin>
         <groupId>org.apache.felix</groupId>
         <artifactId>maven-scr-plugin</artifactId>
         <version>1.26.4</version>
         <executions>
           <execution>
             <id>generate-scr-scrdescriptor</id>
             <goals>
               <goal>scr</goal>
             </goals>
           </execution>
         </executions>
         <dependencies>
           <dependency>
             <groupId>org.ow2.asm</groupId>
             <artifactId>asm-analysis</artifactId>
             <version>9.7.1</version>
             <scope>compile</scope>
           </dependency>
         </dependencies>
       </plugin>
       ...
     </plugins>
     ...
   </build>
   ...
 </project>
```
