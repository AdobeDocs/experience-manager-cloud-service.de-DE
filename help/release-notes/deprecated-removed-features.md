---
title: Veraltete und entfernte Funktionen
description: Spezifische Versionshinweise zu veralteten und entfernten Funktionen von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
mini-toc-levels: 1
exl-id: ef082184-4eb7-49c7-8887-03d925e3da6f
feature: Release Information
role: Admin
source-git-commit: 7ee534546cc8b9afd865b41f223caf9fd86ea45a
workflow-type: tm+mt
source-wordcount: '3548'
ht-degree: 89%

---

# Eingestellte und entfernte Funktionen und APIs {#deprecated-and-removed-features-apis}

>[!CONTEXTUALHELP]
>id="aem_cloud_deprecated_features"
>title="Eingestellte und entfernte Funktionen in AEM as a Cloud Service"
>abstract="AEM as a Cloud Service verfügt über ein Cloud-natives Bereitstellungsmodell. Auf dieser Registerkarte werden Funktionen vorgestellt, die durch ihre Cloud-nativen Gegenstücke ersetzt wurden."

Adobe überprüft regelmäßig Funktionen, einschließlich APIs und Konfigurationen, um sicherzustellen, dass sie den sich weiterentwickelnden Standards für Leistung, Sicherheit und Gesamtwert für AEM as a Cloud Service entsprechen. Basierend auf diesen Auswertungen können bestimmte Funktionen möglicherweise als veraltet gekennzeichnet werden. Wenn möglich, stellt Adobe einen geeigneten Ersatz bereit.

Wenn eine Einstellung angekündigt wird, bleibt die Funktion nur für einen begrenzten Zeitraum verfügbar und Kundinnen und Kunden müssen alle Nutzungsdaten vor einem angegebenen Entfernungsdatum entfernen. Adobe sorgt für angemessene Ankündigungen und Leitlinien, um einen reibungslosen Übergang zu unterstützen.

Während des Zeitfensters für die Einstellung erinnert Adobe die Kundinnen und Kunden durch E-Mail-Benachrichtigungen, Aktionscenter-Warnungen oder Erinnerungen in Cloud Manager an die Maßnahmen, die sie ergreifen müssen, um die Verwendung einer bestimmten Funktion einzustellen.

>[!WARNING]
>
>In einigen Fällen kann es erforderlich sein, eine Funktion zu entfernen, bevor ein neuer Cloud Manager-Build bereitgestellt oder auf die neueste Version von AEM as a Cloud Service aktualisiert wird.

>[!IMPORTANT]
>  Einige [veraltete APIs](#aem-apis) werden ab dem **. Februar 2026 entfernt**. Bitte überprüfen Sie diese wichtigen Daten und Auswirkungen:
>
> * **Ab 26. Januar 2026**: Benachrichtigungs-E-Mails zum Aktionscenter werden **wöchentlich pro Umgebung** gesendet, um Sie daran zu erinnern, die Verwendung dieser APIs zu entfernen.
> * **26. Februar 2026**: Cloud Manager-Pipelines, die Code enthalten, der diese APIs verwendet, **während** Schritts **Code-Qualität** angehalten. Bereitstellungs-Manager, Projekt-Manager oder Geschäftsinhaber können das Problem außer Kraft setzen, damit die Pipeline fortgesetzt werden kann.
> * **26. März 2026**: Cloud Manager-Pipelines, die Code enthalten, der diese APIs verwendet **schlagen** während des **Code-Qualitäts-**-Schritts fehl **blockieren Bereitstellungen** neuen Codes, bis die Verwendung entfernt wird.
> * **30. April 2026**: Umgebungen, die diese APIs weiterhin verwenden, **möglicherweise keine wichtigen Adobe-Versions-Updates mehr**.
>
> Um Bereitstellungsblöcke zu verhindern, entfernen Sie die API-Nutzung vor dem 26. März 2026.

## Veraltete Funktionalität {#deprecated-features}

Die Funktionen in der folgenden Tabelle wurden schon als veraltet angekündigt, jedoch bisher noch nicht entfernt.  Die Nutzung der Funktion muss vor dem Zieltermin für die Entfernung eingestellt werden, da ansonsten Probleme im Zusammenhang mit Leistung, Verfügbarkeit und Sicherheit auftreten könnten.

| Funktionen | Veraltete Funktion | Ersatz |
| ------------ | ------------------ | ----------- |
| Sites | [Unterstützung von Inhaltsfragmenten in dem Assets-HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md) | [Bereitstellung von Inhaltsfragmenten mit OpenAPI](/help/headless/aem-content-fragment-delivery-with-openapi.md)<br>zusammen mit<br> [OpenAPIs für das Management von Inhaltsfragmenten und Inhaltsfragmentmodellen](/help/headless/content-fragment-openapis.md) |
| Sites | [PWA-Funktionen](/help/sites-cloud/authoring/sites-console/enable-pwa.md) | Keine |
| Sites | [SPA-Editor](/help/implementing/developing/hybrid/introduction.md) | Die bevorzugten Editoren für die Verwaltung von Headless-Inhalten in AEM sind: <br>- der [universelle Editor](https://www.aem.live/docs/aem-authoring) zur visuellen Bearbeitung.<br>- der [Inhaltsfragment-Editor](/help/assets/content-fragments/content-fragments-managing.md) zur formularbasierten Bearbeitung. |
| [!DNL Sites] | [JavaScript-Anwendungs-API](https://github.com/adobe/htl-spec/blob/master/SPECIFICATION.md#42-javascript-use-api) | [Java-Anwendungs-API](https://experienceleague.adobe.com/de/docs/experience-manager-htl/content/java-use-api) |
| [!DNL Sites] | Eigenschaften von Experience Fragments für **Social-Media-Status**. | Die Funktion wird in Kürze entfernt werden. |
| Sites | [Automatisierung der Einrichtung von Experience Cloud](/help/sites-cloud/integrating/adobe-analytics-exc-setup-automation.md) | Keine |
| [!DNL Sites] | Vorlagenbasierte einfache Inhaltsfragmente. | Jetzt [Modellbasierte strukturierte Inhaltsfragmente](/help/assets/content-fragments/content-fragments-models.md). |
| [!DNL Assets] | `DAM Asset Update`-Workflow zur Verarbeitung erfasster Bilder. | Für die Asset-Aufnahme werden jetzt [Asset-Microservices](/help/assets/asset-microservices-overview.md) verwendet. |
| [!DNL Assets] | Hochladen von Assets direkt in [!DNL Experience Manager]. Siehe [Veraltete APIs zum Hochladen von Assets](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api). | Verwenden Sie den [direkten binären Upload](/help/assets/add-assets.md). Weitere technische Daten finden Sie im Abschnitt zu den [APIs für den direkten Upload](/help/assets/developer-reference-material-apis.md#upload-binary). |
| [!DNL Assets] | [Bestimmte Workflow-Schritte &#x200B;](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) im `DAM Asset Update`-Workflow werden nicht unterstützt, darunter der Aufruf von Befehlszeilen-Tools wie [!DNL ImageMagick]. | [Asset-Microservices](/help/assets/asset-microservices-overview.md) bieten Ersatz für viele Workflows. Verwenden Sie für die benutzerdefinierte Verarbeitung [Nachbearbeitungs-Workflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |
| [!DNL Assets] | FFmpeg-Transcodierung von Videos. | Verwenden Sie für die Generierung von FFmpeg-Miniaturen [Asset-Microservices](/help/assets/asset-microservices-overview.md). Verwenden Sie für die von FFmpeg-Transcodierung [Dynamic Media](/help/assets/manage-video-assets.md). |
| [!DNL Foundation] | Benutzeroberfläche für die Strukturreplikation auf der Registerkarte „Verteilung“ des Replikationsagenten (nach dem 30. September 2021 entfernt) | Ansätze zum [Verwalten der Veröffentlichung](/help/operations/replication.md#manage-publication) oder zum [Workflow-Schritt für die Strukturaktivierung](/help/operations/replication.md#tree-activation). |
| [!DNL Foundation] | Die Registerkarte „Verteilen“ im Admin-Bildschirm des Replikationsagenten und die Replikations-API können keine Inhaltspakete replizieren, die größer als 10 MB sind. | [Verwalten der Veröffentlichung](/help/operations/replication.md#manage-publication) oder [Workflow-Schritt für die Strukturaktivierung](/help/operations/replication.md#tree-activation) |
| [!DNL Foundation] | Integrationen mit Anmeldedaten, die aus Adobe Developer Console-Projekten generiert wurden, verlieren schrittweise die Unterstützung für Service-Konto-Anmeldedaten (JWT). Seit dem 1. Mai 2024 können in Adobe Developer Console keine neuen Anmeldedaten für Service-Konten (JWT) mehr erstellt werden. Vorhandene Anmeldedaten für Service-Konten (JWT) bleiben bis zum 1. Januar 2025 für konfigurierte Integrationen nutzbar. Danach funktionieren sie nicht mehr, sodass Kundinnen und Kunden zu OAuth-Server-zu-Server-Anmeldedaten migrieren müssen. [Weitere Informationen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/security/jwt-credentials-deprecation-in-adobe-developer-console). | [Migrieren](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration#migration-overview) Sie zu OAuth-Server-zu-Server-Anmeldedaten. |
| [!DNL Foundation] | Der Workflow für die Veröffentlichung der Inhaltsstruktur und der zugehörige Workflow-Schritt für die Veröffentlichung der Inhaltsstruktur, der für die Replikationen von Inhaltshierarchien verwendet wurde. | Verwenden Sie den [Workflow-Schritt für die Strukturaktivierung](/help/operations/replication.md#tree-activation), der leistungsfähiger ist. |
| [!DNL Foundation] | Verwendung von YUI zum Komprimieren/Minimieren der JavaScript-Client-Bibliotheken: Adobe plant keine weitere Aktualisierung der YUI-Bibliothek.  | Adobe empfiehlt Kundinnen und Kunden, für ihre Implementierung zum Google Closure Compiler (GCC) zu wechseln. |

## Entfernte Funktionalität {#removed-features}

In diesem Abschnitt werden Funktionen aufgelistet, die entfernt wurden.

| Bereich | Funktion | Ersatz | Zieltermin für die Entfernung |
| ------------ | ------------------ | ----------- | ------------------- |
| Benutzeroberfläche | Die Classic-Benutzeroberfläche wurde aus der Produkt-Benutzeroberfläche entfernt. Für einige ausgewählte Funktionen wie Link Checker, Versionsbereinigung und einige Cloud Service-Konfigurationen sind einige Dialogfelder der Classic-Benutzeroberfläche verfügbar. Künftige [Produkt-Updates](/help/release-notes/home.md) können weitere verfügbare Elemente der Classic-Benutzeroberfläche entfernen. | Standard-Benutzeroberfläche | Entfernt |
| [!DNL Dynamic Media] | Frühere Integrationen mit [Dynamic Media Classic](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/sites/administering/integration/scene7#integration) und dem [Dynamic Media-Hybridmodus](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/assets/dynamic/config-dynamic#dynamic) sind in [!DNL Experience Manager] as a [!DNL Cloud Service] nicht verfügbar. | Verwenden Sie [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md), das mit [!DNL Experience Manager] as a [!DNL Cloud Service]bereitgestellt wird. | Entfernt |
| [!DNL Sites] | Komponenten „Portal Director“ und „Portlet“ | Diese Funktionen gelten seit [!DNL Experience Manager] 6.4 als veraltet und wurden nun aus [!DNL Experience Manager] entfernt. | Entfernt |
| [!DNL Sites] | Design-Import-Tool | Diese Funktion wurde entfernt, da auf unveränderliche Abschnitte des [!DNL Experience Manager]-Repositorys nicht zur Laufzeit zugegriffen werden kann. | Entfernt |
| [!DNL Assets] | [!DNL Assets]-Freigabe für Marketing Cloud Assets Core Service und Creative Cloud-Services ist nicht verfügbar. | Zur Integration mit [!DNL Adobe Creative Cloud] verwenden Sie [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html). | Entfernt |
| [!DNL Foundation] | Unterstützung für Apache Sling-Datenquellen (OSGi-Bundle org.apache.sling.datasource) | Nicht zutreffend | Entfernt |
| [!DNL Foundation] | Unterstützung für JST-Skriptvorlagen (OSGi-Bundle org.apache.sling.scripting.jst) | Nicht zutreffend | Entfernt |
| [!DNL Foundation] | Unterstützung für das Apache Felix Http Whiteboard | OSGi Http Whiteboard | März 2022 |
| [!DNL Foundation] | Unterstützung für com.adobe.granite.oauth.server | Adobe IMS-Integration | März 2023 |
| [!DNL Foundation] | Unterstützung für die Funktion org.apache.sling.serviceusermapping, um die [Dienstbenutzer-ID abzurufen](https://sling.apache.org/apidocs/sling12/org/apache/sling/serviceusermapping/ServiceUserMapper.html#getServiceUserID-org.osgi.framework.Bundle-java.lang.String-) | Nicht zutreffend | 30.08.24 |
| [!DNL Foundation] | Java 11 Runtime ist veraltet und wurde von Adobe durch Java 21 Runtime ersetzt. Beachten Sie, dass es akzeptabel ist, Code weiterhin mit Java 11 zu erstellen (Java 17 und 21 sind die anderen Optionen) | Die Java 21-Laufzeit wird angewendet. Um die Kompatibilität sicherzustellen, müssen die Bibliotheksversionen aktualisiert werden, wie unter [Laufzeitanforderungen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements) beschrieben. | 29.05.25 |

## Veraltete APIs {#aem-apis}

Die APIs in der folgenden Tabelle (klicken Sie, um sie zu erweitern) wurden bereits als veraltet angekündigt, jedoch noch nicht entfernt.  Die Verwendung dieser APIs muss vor dem Zieltermin für die Entfernung beendet werden, da sonst Probleme im Zusammenhang mit Leistung, Verfügbarkeit und Sicherheit auftreten können. Einige APIs verweisen auf den Abschnitt „API-Entfernungsanleitung“ unten.

>[!IMPORTANT]
> Mehrere APIs sollen am (26 **Februar 2026) entfernt**. Bitte überprüfen Sie diese wichtigen Daten und Auswirkungen:
>
> * **Ab 26. Januar 2026**: Benachrichtigungs-E-Mails zum Aktionscenter werden **wöchentlich pro Umgebung** gesendet, um Sie daran zu erinnern, die Verwendung dieser APIs zu entfernen.
> * **26. Februar 2026**: Cloud Manager-Pipelines, die Code enthalten, der diese APIs verwendet, **während** Schritts **Code-Qualität** angehalten. Bereitstellungs-Manager, Projekt-Manager oder Geschäftsinhaber können das Problem außer Kraft setzen, damit die Pipeline fortgesetzt werden kann.
> * **26. März 2026**: Cloud Manager-Pipelines, die Code enthalten, der diese APIs verwendet **schlagen** während des **Code-Qualitäts-**-Schritts fehl **blockieren Bereitstellungen** neuen Codes, bis die Verwendung entfernt wird.
> * **30. April 2026**: Umgebungen, die diese APIs weiterhin verwenden, **möglicherweise keine wichtigen Adobe-Versions-Updates mehr**.
>
> Um Bereitstellungsblöcke zu verhindern, entfernen Sie die API-Nutzung vor dem 26. März 2026.


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
    <td>2/26/2026</td>
  </tr>
  <tr>
<td>org.eclipse.jetty.client<br>org.eclipse.jetty.client.api<br>org.eclipse.jetty.client.http<br>org.eclipse.jetty.client.util<br>org.eclipse.jetty.http<br>org.eclipse.jetty.http.pathmap<br>org.eclipse.jetty.io<br>org.eclipse.jetty.io.ssl<br>org.eclipse.jetty.security<br>org.eclipse.jetty.server<br>org.eclipse.jetty.server.handler<br>org.eclipse.jetty.server.handler.gzip<br>org.eclipse.jetty.server.session<br>org.eclipse.jetty.servlet<br>org.eclipse.jetty.servlet.listener<br>org.eclipse.jetty.util<br>org.eclipse.jetty.util.annotation<br>org.eclipse.jetty.util.component<br>org.eclipse.jetty.util.log<br>org.eclipse.jetty.util.resource<br>org.eclipse.jetty.util.security<br>org.eclipse.jetty.util.ssl<br>org.eclipse.jetty.util.statistic<br>org.eclipse.jetty.util.thread</td>
    <td>Die Pakete Eclipse Jetty und Felix Http Jetty werden nicht mehr unterstützt. <a href="#org.eclipse.jetty">Siehe die folgenden Hinweise zur Entfernung.</a></td>
    <td>27.05.2021</td>
    <td>2/26/2026</td>
  </tr>
 <tr>     <td>com.mongodb<br>com.mongodb.annotations<br>com.mongodb.assertions<br>com.mongodb.async<br>com.mongodb.binding<br>com.mongodb.bulk<br>com.mongodb.client<br>com.mongodb.client.gridfs<br>com.mongodb.client.gridfs.codecs<br>com.mongodb.client.gridfs.model<br>com.mongodb.client.jndi<br>com.mongodb.client.model<br>com.mongodb.client.model.changestream<br>com.mongodb.client.model.geojson<br>com.mongodb.client.model.geojson.codecs<br>com.mongodb.client.result<br>com.mongodb.connection<br>com.mongodb.connection.netty<br>com.mongodb.diagnostics.logging<br>com.mongodb.event<br>com.mongodb.gridfs<br>com.mongodb.internal<br>com.mongodb.internal.async<br>com.mongodb.internal.authentication<br>com.mongodb.internal.connection<br>com.mongodb.internal.dns<br>com.mongodb.internal.event<br>com.mongodb.internal.management.jmx<br>com.mongodb.internal.session<br>com.mongodb.internal.thread<br>com.mongodb.internal.validator<br>com.mongodb.management<br>com.mongodb.operation<br>com.mongodb.selector<br>com.mongodb.session<br>com.mongodb.util</td>
    <td>Die Verwendung dieses APIs wird in AEM as a Cloud Service nicht unterstützt. <a href="#com.mongodb">Siehe die folgenden Hinweise zur Entfernung.</a></td>
    <td>27.05.2021</td>
    <td>2/26/2026</td>
  </tr>
   <tr>
    <td>org.apache.abdera<br>org.apache.abdera.model<br>org.apache.abdera.factory<br>org.apache.abdera.ext.media<br>org.apache.abdera.util<br>org.apache.abdera.i18n.iri<br>org.apache.abdera.writer<br>org.apache.abdera.i18n.rfc4646<br>org.apache.abdera.i18n.rfc4646.enums<br>org.apache.abdera.i18n.text<br>org.apache.abdera.filter<br>org.apache.abdera.xpath<br>org.apache.abdera.i18n.text.io<br>org.apache.abdera.i18n.text.data<br>org.apache.abdera.parser</td>
    <td>Diese API wird nicht mehr unterstützt, da das Projekt Apache Abdera 2017 eingestellt wurde. <a href="#org.apache.abdera_or_org.apache.sling.atom.taglib">Siehe die folgenden Hinweise zur Entfernung.</a></td>
    <td>29.07.2021</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
    <td>org.apache.abdera.ext.opensearch<br>org.apache.abdera.ext.opensearch.model<br>org.apache.abdera.ext.opensearch.server<br>org.apache.abdera.ext.opensearch.server.impl<br>org.apache.abdera.ext.opensearch.server.processors<br>org.apache.abdera.i18n.iri.data<br>org.apache.abdera.i18n.lang<br>org.apache.abdera.i18n.templates<br>org.apache.abdera.i18n.unicode.data<br>org.apache.abdera.parser.stax<br>org.apache.abdera.parser.stax.util<br>org.apache.abdera.protocol<br>org.apache.abdera.protocol.client<br>org.apache.abdera.protocol.client.cache<br>org.apache.abdera.protocol.client.util<br>org.apache.abdera.protocol.error<br>org.apache.abdera.protocol.server<br>org.apache.abdera.protocol.server.context<br>org.apache.abdera.protocol.server.filters<br>org.apache.abdera.protocol.server.impl<br>org.apache.abdera.protocol.server.multipart<br>org.apache.abdera.protocol.server.processors<br>org.apache.abdera.protocol.server.provider.basic<br>org.apache.abdera.protocol.server.provider.managed<br>org.apache.abdera.protocol.server.servlet<br>org.apache.abdera.protocol.util<br>org.apache.abdera.util.filter</td>
    <td>Diese API wird nicht mehr unterstützt, da das Projekt Apache Abdera 2017 eingestellt wurde. <a href="#org.apache.abdera_or_org.apache.sling.atom.taglib">Siehe die folgenden Hinweise zur Entfernung.</a></td>
    <td>08.04.2019</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
    <td>org.apache.felix.http.whiteboard</td>
    <td>Das Apache Felix Http-Whiteboard wird nicht mehr unterstützt. Migrieren Sie Ihren Code zum OSGi Http-Whiteboard. <a href="#org.apache.felix.http.whiteboard">Siehe die folgenden Hinweise zur Entfernung.</a></td>
    <td>27.01.2022</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
    <td>org.apache.cocoon.xml.dom<br>org.apache.cocoon.xml.sax</td>
    <td>Diese API wird nicht mehr unterstützt. Migrieren Sie Ihren Code zu den vom JDK bereitgestellten XML-APIs.</td>
    <td>27.01.2022</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
    <td>ch.qos.logback.classic<br>ch.qos.logback.classic.boolex<br>ch.qos.logback.classic.db.names<br>ch.qos.logback.classic.db.script<br>ch.qos.logback.classic.encoder<br>ch.qos.logback.classic.filter<br>ch.qos.logback.classic.helpers<br>ch.qos.logback.classic.html<br>ch.qos.logback.classic.jmx<br>ch.qos.logback.classic.joran<br>ch.qos.logback.classic.joran.action<br>ch.qos.logback.classic.jul<br>ch.qos.logback.classic.layout<br>ch.qos.logback.classic.log4j<br>ch.qos.logback.classic.net<br>ch.qos.logback.classic.net.server<br>ch.qos.logback.classic.pattern<br>ch.qos.logback.classic.pattern.color<br>ch.qos.logback.classic.selector<br>ch.qos.logback.classic.selector.servlet<br>ch.qos.logback.classic.servlet<br>ch.qos.logback.classic.sift<br>ch.qos.logback.classic.spi<br>ch.qos.logback.classic.turbo<br>ch.qos.logback.classic.util<br>ch.qos.logback.core<br>ch.qos.logback.core.boolex<br>ch.qos.logback.core.encoder<br>ch.qos.logback.core.filter<br>ch.qos.logback.core.helpers<br>ch.qos.logback.core.hook<br>ch.qos.logback.core.html<br>ch.qos.logback.core.joran<br>ch.qos.logback.core.joran.action<br>ch.qos.logback.core.joran.conditional<br>ch.qos.logback.core.joran.event<br>ch.qos.logback.core.joran.event.stax<br>ch.qos.logback.core.joran.node<br>ch.qos.logback.core.joran.spi<br>ch.qos.logback.core.joran.util<br>ch.qos.logback.core.joran.util.beans<br>ch.qos.logback.core.layout<br>ch.qos.logback.core.net<br>ch.qos.logback.core.net.server<br>ch.qos.logback.core.net.ssl<br>ch.qos.logback.core.pattern<br>ch.qos.logback.core.pattern.color<br>ch.qos.logback.core.pattern.parser<br>ch.qos.logback.core.pattern.util<br>ch.qos.logback.core.property<br>ch.qos.logback.core.read<br>ch.qos.logback.core.recovery<br>ch.qos.logback.core.rolling<br>ch.qos.logback.core.rolling.helper<br>ch.qos.logback.core.sift<br>ch.qos.logback.core.spi<br>ch.qos.logback.core.status<br>ch.qos.logback.core.subst<br>ch.qos.logback.core.util</td>
    <td>AEM as a Cloud Service unterstützt diese interne Log-Back-API nicht. <a href="#ch.qos.logback">Siehe die folgenden Hinweise zur Entfernung.</a></td>
    <td>27.01.2022</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
    <td>org.slf4j.spi</td>
    <td>AEM as a Cloud Service unterstützt diese interne Log4j-API nicht. <a href="#org.slf4j">Siehe die folgenden Hinweise zur Entfernung.</a></td>
    <td>27.01.2022</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
    <td>org.apache.log4j<br>org.apache.log4j.helpers<br>org.apache.log4j.spi<br>org.apache.log4j.xml</td>
    <td>Apache Log4j 1 wurde 2015 eingestellt und wird nicht mehr unterstützt. <a href="#org.apache.log4j">Siehe die folgenden Hinweise zur Entfernung.</a></td>
    <td>27.01.2022</td>
    <td>2/26/2026</td>
  </tr>
  <tr>  <td>com.google.common.annotations<br>com.google.common.base<br>com.google.common.cache<br>com.google.common.collect<br>com.google.common.escape<br>com.google.common.eventbus<br>com.google.common.hash<br>com.google.common.html<br>com.google.common.io<br>com.google.common.math<br>com.google.common.net<br>com.google.common.primitives<br>com.google.common.reflect<br>com.google.common.util.concurrent<br>com.google.common.xml</td>
    <td>Die Google Guava-Kernbibliotheken werden in Cloud Service nicht mehr unterstützt. <a href="#com.google.common">Siehe die folgenden Hinweise zur Entfernung.</a></td>
    <td>15.05.2023</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
    <td>org.slf4j.event</td>
    <td>AEM as a Cloud Service unterstützt dieses interne slf4j-API nicht. <a href="#org.slf4j">Siehe die folgenden Hinweise zur Entfernung.</a></td>
    <td>11.04.2022</td>
    <td>2/26/2026</td>
  </tr> 
    <tr>
    <td>com.drew.*</td>
    <td>Das Extrahieren von Metadaten aus Bildern und Videos sollte über Asset Compute im Cloud Service oder über Apache POI oder Apache Tika erfolgen.</td>
    <td>17.09.2024</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.oak.plugins.blob.*</td>
    <td>Diese API dient nur zur internen Verwendung.</td>
    <td>23.09.2024</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.oak.plugins.memory</td>
    <td>Diese API dient nur zur internen Verwendung.</td>
    <td>23.09.2024</td>
    <td>2/26/2026</td>
  </tr>
  <tr>
<td>org.apache.felix.webconsole<br>org.apache.felix.webconsole.bundleinfo<br>org.apache.felix.webconsole.i18n<br>org.apache.felix.webconsole.spi</td>
    <td>Die Felix-Web-Konsole wird in Cloud-Umgebungen nicht unterstützt. <a href="#org.apache.felix.webconsole">Siehe die folgenden Hinweise zur Entfernung.</a></td>
    <td>30.4.2021</td>
    <td>2/26/2026</td>
  </tr>
<td>org.bson<br/>org.bson.assertions<br/>org.bson.codecs<br/>org.bson.codecs.configuration<br/>org.bson.codecs.pojo<br/>org.bson.codecs.pojo.annotations<br/>org.bson.conversions<br/>org.bson.diagnostics<br/>org.bson.internal<br/>org.bson.io<br/>org.bson.json<br/>org.bson.types<br/>org.bson.util</td>
    <td>Die Verwendung dieses APIs wird in AEM as a Cloud Service nicht unterstützt.</td>
    <td>31.10.2022</td>
    <td>2/26/2026</td>
  </tr>  
  <tr>
    <td>org.apache.sling.runmode</td>
    <td></td>
    <td>2015</td>
    <td>TBD</td>
  </tr>
  <tr>
    <td>org.json</td>
    <td>Die Apache Johnzon-Implementierung von <a href="https://johnzon.apache.org/index.html">javax.json</a> wird empfohlen und sollte verwendet werden. </td>
    <td>30.4.2021</td>
    <td>TBD</td>
  </tr>
  <tr>
<td>org.apache.commons.lang<br>org.apache.commons.lang.enums<br>org.apache.commons.lang.builder<br>org.apache.commons.lang.exception<br>org.apache.commons.lang.math<br>org.apache.commons.lang.mutable<br>org.apache.commons.lang.reflect<br>org.apache.commons.lang.text<br>org.apache.commons.lang.time</td>
    <td>Commons Lang 2 befindet sich im Wartungsmodus. Stattdessen sollte Commons Lang 3 verwendet werden. <a href="#apache.commons">Siehe die folgenden Hinweise zur Entfernung.</a></td>
    <td>30.4.2021</td>
    <td>TBD</td>
  </tr>
  <tr>
    <td>org.apache.commons.collections<br>org.apache.commons.collections.bag<br>org.apache.commons.collections.bidimap<br>org.apache.commons.collections.buffer<br>org.apache.commons.collections.collection<br>org.apache.commons.collections.comparators<br>org.apache.commons.collections.functors<br>org.apache.commons.collections.iterators<br>org.apache.commons.collections.keyvalue<br>org.apache.commons.collections.list<br>org.apache.commons.collections.map<br>org.apache.commons.collections.set</td>
    <td>Commons Collections 3 befindet sich im Wartungsmodus. Stattdessen sollte Commons Collections 4 verwendet werden. <a href="#apache.commons">Siehe die folgenden Hinweise zur Entfernung.</a></td>
    <td>30.4.2021</td>
    <td>TBD</td>
  </tr>
  <tr>
    <td>com.day.cq.contentsync.handler.util</td>
    <td>Diese API wird nicht mehr unterstützt. Verwenden Sie stattdessen die Builder von Apache Sling.</td>
    <td>31.10.2022</td>
    <td>TBD</td>
  </tr>
  <tr><td>org.apache.sling.commons.json<br>org.apache.sling.commons.json.http<br>org.apache.sling.commons.json.io<br>org.apache.sling.commons.json.jcr<br>org.apache.sling.commons.json.sling<br>org.apache.sling.commons.json.util<br>org.apache.sling.commons.json.xml</td>
    <td>AEM as a Cloud Service unterstützt diese API nicht.</td>
    <td>15.05.2023</td>
    <td>TBD</td>
  </tr>
  <tr>
    <td>com.day.cq.xss<br>com.day.cq.xss.taglib<br>com.day.cq.xss.impl</td>
    <td>Verwenden Sie stattdessen org.apache.sling.xss.</td>
    <td>12.12.2023</td>
    <td>TBD</td>
  </tr>
  <tr>
    <td>com.adobe.granite.xss<br>com.adobe.granite.xss.impl</td>
    <td>Verwenden Sie stattdessen org.apache.sling.xss.</td>
    <td>12.12.2023</td>
    <td>TBD</td>
  </tr>
  </tbody>
</table>
</details>

## Entfernte APIs {#removed-apis}

In diesem Abschnitt werden APIs aufgelistet, die veraltet sind und entfernt wurden. Einige APIs verweisen auf den Abschnitt „API-Entfernungsanleitung“ unten.

<details>
  <summary>Erweitern, um die Liste entfernter APIs anzuzeigen.</summary>
<table style="table-layout:auto">
  <tr>
    <th>Package/Klasse</th>
    <th>Kommentare</th>
  </tr>
<tbody>
  <tr>
    <td>com.day.cq.jcrclustersupport</td>
    <td>Verwenden Sie alternativ die Discovery-API von Sling</td>
  </tr>
  <tr>
    <td>org.apache.fop.apps</td>
    <td></td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.vault.util.xml.xerces.dom<br>org.apache.jackrabbit.vault.util.xml.xerces.util<br>org.apache.jackrabbit.vault.util.xml.xerces.xni<br>org.apache.jackrabbit.vault.util.xml.xerces.xni.parser</td>
    <td></td>
  </tr>
  <tr>
    <td>org.apache.felix.cm<br>org.apache.felix.cm.file</td>
    <td>Benutzerdefinierte Persistenz-Manager werden in AEM as a Cloud Service nicht unterstützt.</td>
  </tr>
  <tr>
    <td>org.apache.felix.systemready</td>
    <td>Es wird empfohlen, stattdessen die Apache Felix HealthCheck-API zu verwenden.</td>
  </tr>
  <tr> <td>org.apache.felix.http.jetty<br>org.eclipse.jetty.client.jmx<br>org.eclipse.jetty.jmx<br>org.eclipse.jetty.server.handler.jmx<br>org.eclipse.jetty.server.nio<br>org.eclipse.jetty.server.jmx<br>org.eclipse.jetty.servlet.jmx<br>org.eclipse.jetty.util.preventers<br>org.eclipse.jetty.util.thread.strategy<br>org.eclipse.jetty.webapp<br>org.eclipse.jetty.websocket.api<br>org.eclipse.jetty.websocket.api.annotations<br>org.eclipse.jetty.websocket.api.extensions<br>org.eclipse.jetty.websocket.api.util<br>org.eclipse.jetty.websocket.client<br>org.eclipse.jetty.websocket.client.io<br>org.eclipse.jetty.websocket.client.masks<br>org.eclipse.jetty.websocket.common<br>org.eclipse.jetty.websocket.common.events<br>org.eclipse.jetty.websocket.common.events.annotated<br>org.eclipse.jetty.websocket.common.extensions<br>org.eclipse.jetty.websocket.common.extensions.compress<br>org.eclipse.jetty.websocket.common.extensions.fragment<br>org.eclipse.jetty.websocket.common.extensions.identity<br>org.eclipse.jetty.websocket.common.frames<br>org.eclipse.jetty.websocket.common.io<br>org.eclipse.jetty.websocket.common.io.http<br>org.eclipse.jetty.websocket.common.io.payload<br>org.eclipse.jetty.websocket.common.message<br>org.eclipse.jetty.websocket.common.scopes<br>org.eclipse.jetty.websocket.common.util<br>org.eclipse.jetty.websocket.server<br>org.eclipse.jetty.websocket.server.pathmap<br>org.eclipse.jetty.websocket.servlet<br>org.eclipse.jetty.xml</td>
    <td>Die Pakete Eclipse Jetty und Felix Http Jetty werden nicht mehr unterstützt.</td>
  </tr>
  <tr>
    <td>org.apache.felix.metatype<br>org.apache.felix.scr<br>org.apache.felix.scr.info<br>org.apache.felix.scr.component</td>
    <td>Der Apache Felix-Metatyp und die SCR-APIs sind veraltet.  Verwenden Sie stattdessen den OSGi-Metatyp und die Declarative Service-APIs.</td>
  </tr>
  <tr>
    <td>org.slf4j.impl</td>
    <td>Protokollimplementierungsklassen sind mit AEM as a Cloud Service nicht kompatibel.</td>
  </tr>
  <tr>
    <td>org.apache.sling.startupfilter<br>com.adobe.granite.crypto.spi<br>com.adobe.granite.crpyto.spi.base<br>com.adobe.agl.impl.data.icudt40b<br>com.adobe.agl.impl.data.icudt40b.brkitr<br>com.adobe.agl.impl.data.icudt40b.coll<br>com.adobe.agl.impl.data.icudt40b.rbnf<br>com.<br>adobe.agl.impl.data.icudt40b.translit<br>com.adobe.internal.pdf.tika<br>com.adobe.internal.pdftoolkit.color<br>com.adobe.internal.pdftoolkit.core.encryption<br>com.adobe.internal.pdftoolkit.core.encryption.impl<br>com.adobe.internal.pdftoolkit.core.traverser<br>com.adobe.internal.pdftoolkit.graphicsDOM<br>com.adobe.internal.pdftoolkit.graphicsDOM.shading<br>com.adobe.internal.pdftoolkit.graphicsDOM.utils<br>com.adobe.internal.pdftoolkit.image<br>com.adobe.internal.pdftoolkit.pdf.content<br>com.adobe.internal.pdftoolkit.pdf.content.processor<br>com.adobe.internal.pdftoolkit.pdf.content.processor.base14fontwidths<br>com.adobe.internal.pdftoolkit.pdf.contentmodify<br>com.adobe.internal.pdftoolkit.pdf.contentmodify.impl<br>com.adobe.internal.pdftoolkit.pdf.digsig<br>com.adobe.internal.pdftoolkit.pdf.document<br>com.adobe.internal.pdftoolkit.pdf.document.listener<br>com.adobe.internal.pdftoolkit.pdf.document.permissionhandlers<br>com.adobe.internal.pdftoolkit.pdf.filters<br>com.adobe.internal.pdftoolkit.pdf.graphics<br>com.adobe.internal.pdftoolkit.pdf.graphics.colorspaces<br>com.adobe.internal.pdftoolkit.pdf.graphics.colorspaces.cmykresources<br>com.adobe.internal.pdftoolkit.pdf.graphics.font<br>com.adobe.internal.pdftoolkit.pdf.graphics.font.encodings<br>com.adobe.internal.pdftoolkit.pdf.graphics.font.impl<br>com.adobe.internal.pdftoolkit.pdf.graphics.impl<br>com.adobe.internal.pdftoolkit.pdf.graphics.optionalcontent<br>com.adobe.internal.pdftoolkit.pdf.graphics.patterns<br>com.adobe.internal.pdftoolkit.pdf.graphics.shading<br>com.adobe.internal.pdftoolkit.pdf.graphics.xobject<br>com.adobe.internal.pdftoolkit.pdf.impl<br>com.adobe.internal.pdftoolkit.pdf.inlineimage<br>com.adobe.internal.pdftoolkit.pdf.interactive<br>com.adobe.internal.pdftoolkit.pdf.interactive.action<br>com.adobe.internal.pdftoolkit.pdf.interactive.annotation<br>com.adobe.internal.pdftoolkit.pdf.interactive.forms<br>com.adobe.internal.pdftoolkit.pdf.interactive.forms.impl<br>com.adobe.internal.pdftoolkit.pdf.interactive.geospatial<br>com.adobe.internal.pdftoolkit.pdf.interactive.markedcontent<br>com.adobe.internal.pdftoolkit.pdf.interactive.navigation<br>com.adobe.internal.pdftoolkit.pdf.interactive.navigation.collection<br>com.adobe.internal.pdftoolkit.pdf.interactive.readerrequirements<br>com.adobe.internal.pdftoolkit.pdf.interactive.requirement<br>com.adobe.internal.pdftoolkit.pdf.interchange<br>com.adobe.internal.pdftoolkit.pdf.interchange.documentparts<br>com.adobe.internal.pdftoolkit.pdf.interchange.metadata<br>com.adobe.internal.pdftoolkit.pdf.interchange.prepress<br>com.adobe.internal.pdftoolkit.pdf.interchange.structure<br>com.adobe.internal.pdftoolkit.pdf.multimedia<br>com.adobe.internal.pdftoolkit.pdf.page<br>com.adobe.internal.pdftoolkit.pdf.rendering<br>com.adobe.internal.pdftoolkit.pdf.transparency<br>com.adobe.internal.pdftoolkit.pdf.utils<br>com.adobe.internal.pdftoolkit.services.Jpeg2000<br>com.adobe.internal.pdftoolkit.services.fontresources<br>com.adobe.internal.pdftoolkit.services.fontresources.subsetting<br>com.adobe.internal.pdftoolkit.services.interchange.structure<br>com.adobe.internal.pdftoolkit.services.optionalcontent<br>com.adobe.internal.pdftoolkit.services.optionalcontent.impl<br>com.adobe.internal.pdftoolkit.services.pdfParser<br>com.adobe.internal.pdftoolkit.services.permissions<br>com.adobe.internal.pdftoolkit.services.rasterizer<br>com.adobe.internal.pdftoolkit.services.readingorder<br>com.adobe.internal.pdftoolkit.services.security<br>com.adobe.internal.pdftoolkit.services.swf<br>com.adobe.internal.pdftoolkit.services.textextraction<br>com.adobe.internal.pdftoolkit.services.textextraction.impl<br>com.adobe.internal.pdftoolkit.services.xmp<br>com.adobe.internal.util.base64<br>com.adobe.internal.xmp.utils<br>com.day.crx.core.cluster<br>com.day.crx.packaging<br>com.day.crx.packaging.gfx<br>com.day.crx.query<br>com.day.crx.sling.server.jmx<br>com.day.durbo<br>com.day.durbo.io<br>com.day.imageio.plugins<br>org.apache.aries.jmx.codec<br>org.h2.mvstore<br>org.h2.mvstore.rtree<br>org.h2.mvstore.type<br>org.openxmlformats.schemas.drawingml.x2006.chart.impl<br>org.openxmlformats.schemas.drawingml.x2006.main.impl<br>org.openxmlformats.schemas.drawingml.x2006.picture.impl<br>org.openxmlformats.schemas.drawingml.x2006.spreadsheetDrawing.impl<br>org.openxmlformats.schemas.drawingml.x2006.wordprocessingDrawing.impl<br>org.openxmlformats.schemas.officeDocument.x2006.customProperties.impl<br>org.openxmlformats.schemas.officeDocument.x2006.docPropsVTypes.impl<br>org.openxmlformats.schemas.officeDocument.x2006.extendedProperties.impl<br>org.openxmlformats.schemas.officeDocument.x2006.relationships.impl<br>org.openxmlformats.schemas.presentationml.x2006.main.impl<br>org.openxmlformats.schemas.spreadsheetml.x2006.main.impl<br>org.openxmlformats.schemas.wordprocessingml.x2006.main.impl<br>org.openxmlformats.schemas.xpackage.x2006.contentTypes<br>org.openxmlformats.schemas.xpackage.x2006.contentTypes.impl<br>org.openxmlformats.schemas.xpackage.x2006.digitalSignature<br>org.openxmlformats.schemas.xpackage.x2006.digitalSignature.impl<br>org.openxmlformats.schemas.xpackage.x2006.metadata.coreProperties<br>org.openxmlformats.schemas.xpackage.x2006.metadata.coreProperties.impl<br>org.openxmlformats.schemas.xpackage.x2006.relationships<br>org.openxmlformats.schemas.xpackage.x2006.relationships.impl<br>com.adobe.internal.afml<br>com.adobe.internal.agm<br>com.adobe.internal.pdftoolkit.legacy.services.ap.es2<br>com.adobe.internal.pdftoolkit.legacy.services.ap.es3<br>com.adobe.internal.pdftoolkit.pdf.pieceinfo.compoundtype<br>com.adobe.internal.pdftoolkit.pdf.pieceinfo.editablepdf<br>com.adobe.internal.pdftoolkit.services.ap<br>com.adobe.internal.pdftoolkit.services.ap.annot<br>com.adobe.internal.pdftoolkit.services.ap.extension<br>com.adobe.internal.pdftoolkit.services.ap.impl<br>com.adobe.internal.pdftoolkit.services.ap.spi<br>com.adobe.internal.pdftoolkit.services.digsig<br>com.adobe.internal.pdftoolkit.services.digsig.cryptoprovider<br>com.adobe.internal.pdftoolkit.services.digsig.docmodanalysis<br>com.adobe.internal.pdftoolkit.services.digsig.spi<br>com.adobe.internal.pdftoolkit.services.fdf<br>com.adobe.internal.pdftoolkit.services.formflattener<br>com.adobe.internal.pdftoolkit.services.forms<br>com.adobe.internal.pdftoolkit.services.imageconversion<br>com.adobe.internal.pdftoolkit.services.javascript<br>com.adobe.internal.pdftoolkit.services.javascript.extension<br>com.adobe.internal.pdftoolkit.services.manipulations<br>com.adobe.internal.pdftoolkit.services.manipulations.impl<br>com.adobe.internal.pdftoolkit.services.optimizer<br>com.adobe.internal.pdftoolkit.services.pdfa<br>com.adobe.internal.pdftoolkit.services.pdfa.error<br>com.adobe.internal.pdftoolkit.services.pdfa2<br>com.adobe.internal.pdftoolkit.services.pdfa2.error<br>com.adobe.internal.pdftoolkit.services.pdfa2.error.codes<br>com.adobe.internal.pdftoolkit.services.pdfa3<br>com.adobe.internal.pdftoolkit.services.pdfport<br>com.adobe.internal.pdftoolkit.services.portfolio<br>com.adobe.internal.pdftoolkit.services.rcg<br>com.adobe.internal.pdftoolkit.services.rcg.impl<br>com.adobe.internal.pdftoolkit.services.redaction<br>com.adobe.internal.pdftoolkit.services.redaction.handler<br>com.adobe.internal.pdftoolkit.services.sanitization<br>com.adobe.internal.pdftoolkit.services.xbm<br>com.adobe.internal.pdftoolkit.services.xdp<br>com.adobe.internal.pdftoolkit.services.xfa<br>com.adobe.internal.pdftoolkit.services.xfa.form<br>com.adobe.internal.pdftoolkit.services.xfatext<br>com.adobe.internal.pdftoolkit.services.xfdf<br>com.adobe.internal.pdftoolkit.services.xobjhandler<br>com.adobe.internal.pdftoolkit.xml<br>com.adobe.octopus.extract<br>opennlp.tools.doccat<br>opennlp.tools.entitylinker<br>opennlp.tools.formats<br>opennlp.tools.formats.ad<br>opennlp.tools.formats.brat<br>opennlp.tools.formats.convert<br>opennlp.tools.formats.frenchtreebank<br>opennlp.tools.formats.muc<br>opennlp.tools.formats.ontonotes<br>opennlp.tools.lemmatizer<br>opennlp.tools.parser<br>opennlp.tools.parser.chunking<br>opennlp.tools.parser.lang.en<br>opennlp.tools.parser.lang.es<br>opennlp.tools.parser.treeinsert<br>opennlp.tools.sentdetect<br>opennlp.tools.sentdetect.lang<br>opennlp.tools.sentdetect.lang.th<br>opennlp.tools.stemmer<br>opennlp.tools.stemmer.snowball<br>opennlp.tools.tokenize.lang.en<br>org.apache.commons.imaging.color<br>org.apache.commons.imaging.common<br>org.apache.commons.imaging.common.itu_t4<br>org.apache.commons.imaging.common.mylzw<br>org.apache.commons.imaging.formats.bmp<br>org.apache.commons.imaging.formats.dcx<br>org.apache.commons.imaging.formats.gif<br>org.apache.commons.imaging.formats.icns<br>org.apache.commons.imaging.formats.ico<br>org.apache.commons.imaging.formats.jpeg<br>org.apache.commons.imaging.formats.jpeg.decoder<br>org.apache.commons.imaging.formats.jpeg.exif<br>org.apache.commons.imaging.formats.jpeg.iptc<br>org.apache.commons.imaging.formats.jpeg.segments<br>org.apache.commons.imaging.formats.jpeg.xmp<br>org.apache.commons.imaging.formats.pcx<br>org.apache.commons.imaging.formats.png<br>org.apache.commons.imaging.formats.png.chunks<br>org.apache.commons.imaging.formats.png.scanlinefilters<br>org.apache.commons.imaging.formats.png.transparencyfilters<br>org.apache.commons.imaging.formats.pnm<br>org.apache.commons.imaging.formats.psd<br>org.apache.commons.imaging.formats.psd.dataparsers<br>org.apache.commons.imaging.formats.psd.datareaders<br>org.apache.commons.imaging.formats.rgbe<br>org.apache.commons.imaging.formats.tiff<br>org.apache.commons.imaging.formats.tiff.constants<br>org.apache.commons.imaging.formats.tiff.datareaders<br>org.apache.commons.imaging.formats.tiff.fieldtypes<br>org.apache.commons.imaging.formats.tiff.photometricinterpreters<br>org.apache.commons.imaging.formats.tiff.taginfos<br>org.apache.commons.imaging.formats.tiff.write<br>org.apache.commons.imaging.formats.wbmp<br>org.apache.commons.imaging.formats.xbm<br>org.apache.commons.imaging.formats.xpm<br>org.apache.commons.imaging.icc<br>org.apache.commons.imaging.palette<br>org.apache.commons.imaging.util<br>com.adobe.dam.print.ids.utils<br>com.day.cq.dam.api.reporting<br>com.day.cq.dam.entitlement.api<br>com.day.cq.dam.handler.standard.epub<br>com.day.cq.dam.handler.standard.keynote<br>com.day.cq.dam.handler.standard.mp3<br>com.day.cq.dam.handler.standard.msoffice<br>com.day.cq.dam.handler.standard.msoffice.wmf<br>com.day.cq.dam.handler.standard.ooxml<br>com.day.cq.dam.handler.standard.pdf<br>com.day.cq.dam.handler.standard.pict<br>com.day.cq.dam.handler.standard.ps<br>com.day.cq.dam.handler.standard.psd<br>com.day.cq.dam.handler.standard.zip<br>com.day.cq.dam.word.extraction<br>com.day.cq.dam.word.process<br>com.adobe.xmp.worker.files<br>com.adobe.cq.address.api<br>com.adobe.cq.address.api.location<br>com.day.cq.mcm.emailprovider.impl.types<br>com.day.io<br>com.day.io.disk<br>com.day.io.file<br>org.apache.commons.exec.environment<br>org.apache.commons.exec.launcher<br>org.apache.commons.exec.util<br>com.google.zxing<br>com.google.zxing.common<br>com.google.zxing.common.reedsolomon<br>com.google.zxing.qrcode.decoder<br>com.google.zxing.qrcode.encoder<br>com.adobe.cq.dam.dm.internalapi.image_server<br>com.day.cq.dam.api.s7dam.jobs<br>com.day.cq.dam.api.s7dam.omnisearch<br>com.day.cq.dam.api.s7dam.scene7<br>com.day.cq.dam.scene7<br>com.day.cq.dam.scene7.api.net<br>com.day.cq.analytics.sitecatalyst.rsmerger<br>com.day.cq.searchpromote<br>com.day.cq.searchpromote.xml<br>com.day.cq.searchpromote.xml.form<br>com.day.cq.searchpromote.xml.result&gt;</td>
    <td>Altes AEM 6.x-API.</td>
  </tr>
  <tr>
    <td>org.apache.sling.discovery.commons<br>org.apache.sling.discovery.commons.providers<br>org.apache.sling.discovery.commons.providers.base<br>org.apache.sling.discovery.commons.providers.spi<br>org.apache.sling.discovery.commons.providers.spi.base<br>org.apache.sling.discovery.commons.providers.util</td>
    <td>Diese API wird in Cloud Service nicht unterstützt.</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.vault.util.xml<br>org.apache.jackrabbit.vault.util.xml.serialize</td>
    <td>Util-Klassen, die sich auf Apache Xerces beziehen, werden in späteren Versionen entfernt, was eine größere Versionsänderung zur Folge hat. Da diese Util-Klassen für den internen Gebrauch im File-Vault bestimmt sind, wird die API aus der öffentlichen API-Oberfläche entfernt.</td>
  </tr>
  <tr>
    <td>org.apache.sling.atom.taglib<br>org.apache.sling.atom.taglib.media</td>
    <td>Altes AEM 6.x-API. <a href="#org.apache.abdera_or_org.apache.sling.atom.taglib">Siehe die folgenden Hinweise zur Entfernung.</a></td>
  </tr>
  <tr>
    <td>org.apache.sling.commons.log.logback<br>org.apache.sling.commons.log.logback.webconsole</td>
    <td>AEM as a Cloud Service unterstützt diese interne Log-Back-API nicht.</td>
  </tr>
  <tr>
    <td>com.github.jknack.handlebars.js</td>
    <td>Aufgrund von Sicherheitslücken ist ein Upgrade von Handlebars von 4.0.5 auf 4.3.0 erforderlich. Dieses Paket ist in der aktualisierten Handlebars-Version nicht mehr vorhanden.</td>
  </tr>
  <tr>
    <td>com.adobe.granite.resourceresolverhelper</td>
    <td>Diese API wird nicht mehr unterstützt. Verwenden Sie stattdessen org.apache.sling.api.resource.ResourceResolverFactory.</td>
  </tr>
  <tr>
    <td>org.apache.sling.repoinit.jcr<br>org.apache.sling.repoinit.parser.operations</td>
    <td>Die Verwendung dieses APIs wird in AEM as a Cloud Service nicht unterstützt.</td>
  </tr>
  <tr>
    <td>org.apache.jackrabbit.oak.cache</td>
    <td>Diese API dient nur zur internen Verwendung.</td>
  </tr>
</tbody>
</table>
</details>

## Anleitung zur API-Entfernung {#api-removal-guidance}

Dieser Abschnitt enthält Anleitungen zum Entfernen von APIs für verschiedene APIs in den obigen Tabellen.

Um festzustellen, welche veralteten Java-APIs Ihr Code verwendet, integrieren Sie das [AEM as a Cloud Service SDK Build Analyzer Maven-Plug-](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin) in Ihr Maven-Projekt und führen Sie es lokal aus. Der Bericht listet alle erkannten veralteten API-Verwendungen auf und zeigt an, welches OSGi-Bundle auf die einzelnen APIs verweist.

Sie sollten zwar alle veralteten APIs im Laufe der Zeit beheben, aber priorisieren Sie alle APIs, die in der Tabelle Veraltete APIs aufgeführt sind, mit dem Zieldatum für die Entfernung am 26. Februar 2026 (oder früher). Im AEM Analyzer-Bericht können diese APIs mit dem Datum der wirksamen Entfernung 8/31/2025 angezeigt werden.

Überprüfen Sie nach dem Aktualisieren des Codes, ob keine veraltete API-Nutzung in Cloud Manager verbleibt, indem Sie die Ergebnisse des Code-Qualitätsschritts überprüfen.

### Entfernung von `org.apache.sling.commons.auth*` {#org.apache.sling.commons.auth}

Wenn Sie `org.apache.sling.commons.auth` und/oder `org.apache.sling.commons.auth.spi` verwenden, kann die Verwendung ersetzt werden durch eine Migration des Codes zu `org.apache.sling.auth` bzw. `org.apache.sling.auth.spi`. Wenn Sie eine alte [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/)-Version verwenden, stellen Sie sicher, dass Sie auf die neueste Version aktualisieren.

Aktionsliste:

* Aktualisieren von ACS AEM Commons auf die neueste Version (mindestens 6.11.0)
* Migration von `org.apache.sling.commons.auth` und/oder `org.apache.sling.commons.auth.spi` zu `org.apache.sling.auth` bzw. `org.apache.sling.auth.spi`.

### Entfernung von `org.apache.felix.webconsole*` {#org.apache.felix.webconsole}

Wenn Sie Pakete aus `org.apache.felix.webconsole*` verwenden, entfernen Sie diesen Code aus Ihrem Projekt. Auf die Web-Konsole kann in Cloud Service nicht zugegriffen werden.

Aktionsliste:

* Entfernen von Code mithilfe von Paketen aus `org.apache.felix.webconsole*`

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

Je nach Ihren Anforderungen können Sie eine andere Version auswählen.

### Entfernung von `com.google.common*` {#com.google.common}

Entfernen Sie die Verwendung der Google Guava-Kernbibliotheken oder nehmen Sie eine geeignete Version in Ihr Projekt auf. In vielen Fällen kann die Verwendung dieser Bibliothek durch Sammlungsklassen aus JDK oder Apache Commons Collections4 ersetzt werden. Wenn Sie keinen Ersatz finden, verwenden Sie die neueste Version der Google Guava-Kernbibliothek in Ihrem Projekt. Wenn Sie eine alte [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/)-Version verwenden, stellen Sie sicher, dass Sie auf die neueste Version aktualisieren.

Aktionsliste:

* Aktualisieren von ACS AEM Commons auf die neueste Version (mindestens 6.11.0)
* Ersetzen der Verwendung der Google Guava-Kernbibliothek durch JDK-Sammlungen oder Apache Commons Collections4
* Falls weiterhin erforderlich, fügen Sie Ihrem Projekt dieses Paket hinzu (ersetzen Sie die Version durch die neueste verfügbare):
   * `com.google.guava:guava:33.4.8-jre`

### Entfernung von `Apache Commons Lang 2 and Apache Commons Collections 3` {#apache.commons}

Entfernen Sie die Verwendung der nicht verwalteten Apache Commons-Bibliotheken und ersetzen Sie sie durch die Verwendung der unterstützten Versionen. In den meisten Fällen reicht es, Paketimporte anzupassen, nur in einigen Fällen wurden Klassen oder Methoden umbenannt. Wenn Sie eine alte [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/)-Version verwenden, stellen Sie sicher, dass Sie auf die neueste Version aktualisieren.

Aktionsliste:

* Aktualisieren von ACS AEM Commons auf die neueste Version (mindestens 6.11.0)
* Importe von `org.apache.commons.lang*` durch `org.apache.commons.lang3` ersetzen
* Importe von `org.apache.commons.collections*` durch `org.apache.commons.collecitons4` ersetzen

### Verwendung von `org.apache.abdera*` und `org.apache.sling.atom.taglib` {#org.apache.abdera_or_org.apache.sling.atom.taglib}

Ersetzen Sie die Verwendung von Paketen aus `org.apache.abdera` und `org.apache.sling.atom.taglib` durch eine Bibliothek eines Drittanbieters, die ähnliche Funktionen bietet, oder Ihren eigenen Code.

Aktionsliste:

* Ersetzen Sie die Verwendung von Paketen aus `org.apache.abdera` und `org.apache.sling.atom.taglib` durch andere Bibliotheken von Drittanbietern oder eigenen Code.

### Verwendung von `org.apache.felix.http.whiteboard` {#org.apache.felix.http.whiteboard}

Ersetzen Sie die Verwendung von `org.apache.felix.http.whiteboard` durch das [OSGi Http Whiteboard](https://docs.osgi.org/specification/osgi.cmpn/7.0.0/service.http.whiteboard.html). Die offizielle OSGi-API weist ähnliche Funktionen auf. Beim Ersetzen müssen in den meisten Fällen nur die Eigenschaften für die Dienstregistrierung geändert werden.

Aktionsliste:

* Ersetzen Sie die Verwendung von `org.apache.felix.http.whiteboard` durch [OSGi Http Whiteboard](https://docs.osgi.org/specification/osgi.cmpn/7.0.0/service.http.whiteboard.html)

### Verwendung von `ch.qos.logback*` {#ch.qos.logback}

Logback wird in Cloud Service nicht unterstützt. Es muss vollständig entfernt werden. Wenn Sie eine alte [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/)-Version verwenden, stellen Sie sicher, dass Sie auf die neueste Version aktualisieren.

Aktionsliste:

* Aktualisieren von ACS AEM Commons auf die neueste Version (mindestens 6.11.0)
* Entfernen des Codes mithilfe von Paketen aus `ch.qos.logback`

### Verwendung von `org.slf4j.event and org.slf4j.spi` {#org.slf4j}

Wenn Sie `org.slf4j.event` oder `org.slf4j.spi` verwenden, entfernen Sie alle Verwendungen davon. Wenn Sie eine alte [ACS AEM Commons](https://adobe-consulting-services.github.io/acs-aem-commons/)-Version verwenden, stellen Sie sicher, dass Sie auf die neueste Version aktualisieren.

Aktionsliste:

* Aktualisieren von ACS AEM Commons auf die neueste Version (mindestens 6.11.0)
* Entfernen des Codes mithilfe von `org.slf4j.event` und `org.slf4j.spi`

### Verwendung von `org.apache.log4j` {#org.apache.log4j}

Wenn Sie `org.apache.log4j` verwenden, wechseln Sie entweder zu SLF4J (`org.slf4j`) oder zu Log4J 2.x (`org.apache.logging.log4j`).

Aktionsliste:

* Ersetzen Sie die Verwendung von `org.apache.log4j` durch die Verwendung von `org.slf4j` (empfohlen) oder `org.apache.logging.log4j`

## OSGi-Konfiguration {#osgi-configuration}

Die folgenden Abschnitte spiegeln die OSGi-Konfigurationsoberfläche für AEM as a Cloud Service wider und beschreiben, was sich kundenseitig konfigurieren lässt.

1. Kunden-Code darf die aufgelisteten OSGi-Konfigurationen nicht konfigurieren.
1. Eine Liste der OSGi-Konfigurationen, deren Eigenschaften zwar konfiguriert werden können, aber die angegebenen Validierungsregeln einhalten müssen. Zu diesen Regeln gehört, ob die Deklaration der Eigenschaft erforderlich ist, ihr Typ und in einigen Fällen ihr zulässiger Wertebereich.

Der Kunden-Code kann alle OSGi-Konfigurationen konfigurieren, die nicht aufgeführt sind.

Diese Regeln werden während des Build-Prozesses von Cloud Manager validiert. Im Laufe der Zeit können zusätzliche Regeln hinzugefügt werden, und das erwartete Erzwingungsdatum wird in der Tabelle angegeben. Von Kunden wird erwartet, dass sie diese Regeln bis zum Zieltermin für die Erzwingung einhalten. Werden die Regeln nach dem Entfernungsdatum nicht eingehalten, treten im Build-Prozess von Cloud Manager Fehler auf. Maven-Projekte sollten das [Build Analyzer-Maven-Plug-in des AEM as a Cloud Service-SDK](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin) enthalten, um OSGi-Konfigurationsfehler während der lokalen SDK-Entwicklung zu kennzeichnen.

Weitere Informationen zur OSGi-Konfiguration finden Sie [hier](/help/implementing/deploying/configuring-osgi.md).

### Veraltete OSGi-Eigenschaften (bald unveränderbar) {#deprecated-unmodifiable-osgi-properties}

Eigenschaften für die folgenden OSGi-Komponenten-PIDs sind veraltet, und ihre Verwendung sollte zum Durchsetzungsdatum enden.

| **OSGi-Komponenten-ID** | **Nicht veränderbare Eigenschaften** | **Abschaffung** | **Durchsetzung** |
|---|---|---|---|
| **`org.apache.sling.commons.log.LogManager`** | alle | 24.4.25 | 31.8.25 (Konfiguration im Juni ignoriert) |
| **`org.apache.sling.commons.log.LogManager.factory.config`** | org.apache.sling.commons.log.file, org.apache.sling.commons.log.pattern | 24.4.25 | 31.8.25 (Konfiguration im Juni ignoriert) |
| **`org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`** | alle | 2024 | 31.8.25 |
| **`com.adobe.granite.toggle.impl.dev.DynamicToggleProviderImpl`** | alle | 3.6.25 | 31.8.25 |
| **`org.apache.http.proxyconfigurator`** | alle | 3.6.25 | 31.8.25 |

### Nicht veränderbare OSGi-Konfigurationen {#unmodifiable-osgi-properties}

Eigenschaften für die folgenden OSGi-Komponenten-PIDs können nicht verändert werden. Daher dürfen diese nicht konfiguriert werden.

| **OSGi-Komponenten-ID** | **Nicht veränderbare Eigenschaften** |
|---|---|
| **`com.day.cq.auth.impl.cug.CugSupportImpl`** |  |
| **`com.day.cq.jcrclustersupport.ClusterStartLevelController`** | alle |
| **`com.adobe.granite.toggle.impl.ToggleRouterImpl`** | alle |
| **`org.apache.sling.engine.impl.log.RequestLoggerFilter`** | alle |
| **`org.apache.sling.feature.apiregions.impl`** | alle |
| **`org.apache.sling.jcr.resource.internal.helper.jcr.BinaryDownloadUriProvider`** | alle |
| **`com.adobe.cq.unifiedshell.impl.discovery.DiscoveryServlet`** | alle |
| **`com.adobe.cq.unifiedshell.impl.ui.FrameErrorHandler`** | alle |
| **`com.adobe.cq.unifiedshell.impl.config.UnifiedShellConfService`** | alle |
| **`com.adobe.cq.unifiedshell.impl.config.RepositoryIdentifier`** | alle |
| **`org.apache.sling.feature.apiregions.factory`** | alle |
| **`com.adobe.granite.toggle.monitor.systemproperty`** | alle |


### Zukünftige erzwungene Einschränkungen für OSGi-Eigenschaften {#future-restrictions-osgi-properties}

In Zukunft wird Adobe die folgenden Einschränkungen für OSGi-Eigenschaften durchsetzen. Für die genannten PIDs dürfen nur die aufgelisteten Eigenschaften konfiguriert werden.

| PID von OSGi-Komponenten |   | Erforderlich | Typ | Einschränkung (falls anwendbar) |
|---|---|---|---|---|
| `com.day.cq.mailer.DefaultMailService` | `smtp.host` |   | Zeichenfolge |   |
|   | `smtp.port` | Ja | Ganzzahl | Entweder „465“, „587“ oder „25“ |
|   | `smtp.user` |   | Zeichenfolge |   |
|   | `smtp.password` |   | Zeichenfolge |   |
|   | `from.address` |   | Zeichenfolge |   |
|   | `smtp.ssl` |   | Zeichenfolge |   |
|   | `smtp.starttls` |   | Boolesch |   |
|   | `smtp.requiretls` |   | Boolesch |   |
|   | `debug.email` |   | Boolesch |   |
|   | `oauth.flow` |   | Boolesch |   |
| `org.apache.sling.commons.log.LogManager.factory.config` | `org.apache.sling.commons.log.level` | Ja | Zeichenfolge | Entweder „INFO“, „DEBUG“ oder &quot;TRACE&quot; |
|   | `org.apache.sling.commons.log.names` |   | Zeichenfolgen-Array |   |
|   | `org.apache.sling.commons.log.additiv` |   | Boolesch |   |
| `com.day.cq.commons.impl.ExternalizerImpl` | `externalizer.domains` | Nein | Zeichenfolge[] |   |
|   | `externalizer.encodedpath` | Nein | Boolesch |   |
|   | `externalizer.host` | Nein | Zeichenfolge |   |
|   | `externalizer.contextpath` | Nein | Zeichenfolge |   |

### Einschränkungen für OSGi-Eigenschaften {#restrictions-osgi-properties}

Die Werte dieser OSGi-Eigenschaften sind auf die unten beschriebenen Regeln beschränkt.

| PID von OSGi-Komponenten |   | Erforderlich | Typ | Einschränkung (falls anwendbar) |
|---|---|---|---|---|
| `org.apache.felix.eventadmin.impl.EventAdmin` | `org.apache.felix.eventadmin.ThreadPoolSize` | Ja | Ganzzahl | 2–100 |
|   | `org.apache.felix.eventadmin.AsyncToSyncThreadRatio` |   | Dezimalzahl | -- |
|   | `org.apache.felix.eventadmin.AsyncToSyncThreadRatio` |   | Ganzzahl | -- |
|   | `org.apache.felix.eventadmin.RequireTopic` |   | Boolesch | -- |
|   | `org.apache.felix.eventadmin.IgnoreTimeout` | Ja | Zeichenfolgen-Array | Erforderlicher Bereich: muss mindestens alles von `org.apache.felix*`, `org.apache.sling*`, `come.day*`, `com.adobe*` enthalten |
|   | `org.apache.felix.eventadmin.IgnoreTopic` |   | Zeichenfolgen-Array | -- |
| `org.apache.felix.http` | `org.apache.felix.http.timeout` |   | Ganzzahl |   |
|   | `org.apache.felix.http.session.timeout` |   | Ganzzahl |   |
|   | `org.apache.felix.http.jetty.threadpool.max` |   | Ganzzahl |   |
|   | `org.apache.felix.http.jetty.headerBufferSize` |   | Ganzzahl |   |
|   | `org.apache.felix.http.jetty.requestBufferSize` |   | Ganzzahl |   |
|   | `org.apache.felix.http.jetty.responseBufferSize` |   | Ganzzahl |   |
|   | `org.apache.felix.http.jetty.maxFormSize` |   | Ganzzahl |   |
|   | `org.apache.felix.https.jetty.session.cookie.httpOnly` |   | Boolesch |   |
|   | `org.apache.felix.https.jetty.session.cookie.secure` |   | Boolesch |   |
|   | `org.eclipse.jetty.servlet.SessionIdPathParameterName` |   | Zeichenfolge |   |
|   | `org.eclipse.jetty.servlet.CheckingRemoteSessionIdEncoding` |   | Boolesch |   |
|   | `org.eclipse.jetty.servlet.SessionCookie` |   | Zeichenfolge |   |
|   | `org.eclipse.jetty.servlet.SessionDomain` |   | Zeichenfolge |   |
|   | `org.eclipse.jetty.servlet.SessionPath` |   | Zeichenfolge |   |
|   | `org.eclipse.jetty.servlet.MaxAge` |   | Ganzzahl |   |
|   | `org.eclipse.jetty.servlet.SessionScavengingInterval` |   | Ganzzahl |   |
|   | `org.apache.felix.jetty.gziphandler.enable` |   | Boolesch |   |
|   | `org.apache.felix.jetty.gzip.minGzipSize` |   | Ganzzahl |   |
|   | `org.apache.felix.jetty.gzip.compressionLevel` |   | Ganzzahl |   |
|   | `org.apache.felix.jetty.gzip.inflateBufferSize` |   | Ganzzahl |   |
|   | `org.apache.felix.jetty.gzip.syncFlush` |   | Boolesch |   |
|   | `org.apache.felix.jetty.gzip.excludedUserAgents` |   | Zeichenfolge |   |
|   | `org.apache.felix.jetty.gzip.includedMethods` |   | Zeichenfolgen-Array |   |
|   | `org.apache.felix.jetty.gzip.excludedMethods` |   | Zeichenfolgen-Array |   |
|   | `org.apache.felix.jetty.gzip.includedPaths` |   | Zeichenfolgen-Array |   |
|   | `org.apache.felix.jetty.gzip.excludedPaths` |   | Zeichenfolgen-Array |   |
|   | `org.apache.felix.jetty.gzip.includedMimeTypes` |   | Zeichenfolgen-Array |   |
|   | `org.apache.felix.http.session.invalidate` |   | Boolesch |   |
|   | `org.apache.felix.http.session.container.attribute` |   | Zeichenfolgen-Array |   |
|   | `org.apache.felix.http.session.uniqueid` |   | Boolesch |   |
| `org.apache.sling.scripting.cache` | `org.apache.sling.scripting.cache.size` | Ja | Ganzzahl | >= 2048 |
|   | `org.apache.sling.scripting.cache.additional_extensions` | Ja | Zeichenfolgen-Array | Muss „js“ enthalten |
| `org.apache.sling.engine.impl.log.RequestLogger` | `request.log.output` | Nein | Zeichenfolge |   |
|   | `request.log.outputtype` | Nein | Zeichenfolge |   |
|   | `request.log.entry.format` | Nein | Zeichenfolge |   |
|   | `request.log.exit.format` | Nein | Zeichenfolge |   |
|   | `request.log.enabled` | Nein | Zeichenfolge |   |
|   | `access.log.output` | Nein | Zeichenfolge |   |
|   | `access.log.outputtype` | Nein | Zeichenfolge |   |
|   | `access.log.enabled` | Nein | Zeichenfolge |   |
| `org.apache.sling.servlets.resolver.SlingServletResolver` | `servletresolver.servletRoot` | Nein | Zeichenfolge |   |
|   | `servletresolver.cacheSize` | Nein | Ganzzahl |   |
|   | `servletresolver.paths` | Nein | Zeichenfolge[] |   |
|   | `servletresolver.defaultExtensions` | Nein | Zeichenfolge |   |
|   | `servletresolver.mountProviders` | Nein | Boolesch |   |
|   | `servletresolver.scriptUser` | Nein | Zeichenfolge | veraltet, nicht verwenden. |

## Aktualisierung von Java Runtime auf Version 21 {#java-runtime-update-21}

Adobe Experience Manager as a Cloud Service hat zur Java 21-Laufzeit gewechselt. Um die Kompatibilität sicherzustellen, müssen die Bibliotheksversionen wie unter [Laufzeitanforderungen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements) beschrieben aktualisiert werden.

