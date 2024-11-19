---
title: Dynamic Media mit OpenAPI-Funktionen
description: Erfahren Sie mehr über Schlüsselkonzepte wie die Verwendung von Dynamic Media mit OpenAPI-Funktionen und die Aktivierung.
role: User
exl-id: 658b6eff-9f5a-4166-9ff6-5dc8eb92ada3
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 2%

---

# Dynamic Media mit OpenAPI-Funktionen {#new-dynaminc-media-apis-overview}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|-----|

>[!AVAILABILITY]
>
>Handbuch zu Dynamic Media mit OpenAPI-Funktionen ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den Adobe Acrobat AI-Assistenten, um Ihre Fragen zu beantworten.
>
>[!BADGE Handbuch für Dynamic Media mit OpenAPI-Funktionen PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

In der modernen digitalen Welt ist die Erschließung des vollen Potenzials der digitalen Assets Ihrer Marke von entscheidender Bedeutung, um dem Wettbewerb voraus zu sein. Eine ganzheitliche Digital Assets Management (DAM)-Lösung erleichtert die Verwaltung von Assets, fördert die Markenkonsistenz und beschleunigt die Inhaltsbereitstellung bei gleichzeitiger Gewährleistung von Markenintegrität und außergewöhnlichen Kundenerlebnissen.

Dynamic Media mit OpenAPI-Funktionen stellt DAM in den Mittelpunkt eines agilen und effizienten Content-Supply-Chain-Ökosystems, um Asset-Governance und -Bereitstellung sicherzustellen.

## Warum sollte Dynamic Media mit OpenAPI-Funktionen verwendet werden? {#dynamic-media-open-api-features}

Dynamic Media mit OpenAPI-Funktionen bietet die folgenden Hauptvorteile:

* **Nahtlose Integrationen**: Dynamic Media mit OpenAPI-Funktionen bietet einen umfassenden Satz von Such- und Bereitstellungs-APIs. Dadurch können Ihre Entwickler die Bereitstellung von Assets einfach in ihre Anwendungen integrieren](/help/assets/integrate-dynamic-media-open-apis.md). [ Zu den Anwendungen gehören Adobe sowie Anwendungen von Drittanbietern. Es bietet eine [Benutzeroberfläche für die Auswahl der Micro Frontend-Assets](/help/assets/overview-asset-selector.md) zum Suchen und Auswählen genehmigter Assets. Der Selektor kann mühelos in jede Anwendung integriert werden, die auf JavaScript-Frameworks wie React JS, Angular JS und Vanilla JS basiert.

* **Zentralisierte Verwaltung digitaler Assets**: DAM ist die zentrale Quelle der Wahrheit für alle digitalen Assets. Ihre digitalen Assets werden zentral in AEM Assets verwaltet und über Versand-URLs an verbrauchte Anwendungen bereitgestellt, ohne Asset-Binärdateien zu kopieren.

* **Echtzeit-Aktualisierungen**: Alle Änderungen, die an genehmigten Assets in DAM vorgenommen werden, einschließlich Versionsaktualisierungen und Metadatenänderungen, werden automatisch in den Versand-URLs übernommen. Mit einem kurzen TTL-Wert (Time-to-Live) von 10 Minuten, der für Dynamic Media mit OpenAPI-Funktionen über CDN konfiguriert wurde, werden Aktualisierungen in weniger als 10 Minuten auf allen Authoring- und veröffentlichten Benutzeroberflächen sichtbar.

* **Markenkonsistenz**: Nur [markengenehmigte Assets](/help/assets/approve-assets.md) werden nachgelagerten Anwendungen angezeigt. [Brand Manager und Marketingexperten behalten die strenge Kontrolle über Marken-Assets](/help/assets/restrict-assets-delivery.md). Es steht nur die genehmigte und neueste Version des Assets zur Verwendung zur Verfügung, wodurch Markenkonsistenz über alle Kanäle und Anwendungen hinweg gewährleistet ist.

* **Web-optimierte Bereitstellung**: Digitale Assets werden in weboptimierten Formaten bereitgestellt, um die Web-Vitals Ihrer digitalen Erlebnisse zu verbessern. Dazu gehören die Unterstützung von WebP-Ausgabeformaten für Bilder, das adaptive Streaming über HLS- oder DASH-Protokolle für Videos und Original-Ausgabeformate für Dokumente.

* **Dynamische Asset-Transformation**: Unser System ermöglicht die direkte Bildumwandlung mithilfe von URL-Parametern, die als Bild-Modifikatoren bezeichnet werden. [Zum Beispiel Breite, Höhe, Rotation, Spiegeln, Qualität, Zuschneiden, Format und smartes Zuschneiden](/help/assets/deliver-assets-apis.md). Transformierte Ausgabedarstellungen werden dynamisch generiert und nahtlos über das CDN bereitgestellt.

* **Sichere Bereitstellung von Assets**: Dynamic Media mit OpenAPI-Funktionen bietet einen Mechanismus zur Steuerung des Zugriffs auf Ihre digitalen Assets. Sie können Benutzerrollen oder Gruppen als Metadaten für zu sichernde Assets angeben und einen vordefinierten Zeitrahmen festlegen, innerhalb dessen [nur autorisierte Benutzer auf diese Assets zugreifen können](/help/assets/restrict-assets-delivery.md). Die Bereitstellungs-URLs für gesicherte Assets werden für nicht autorisierte Benutzer während des eingeschränkten Zeitraums nicht aufgelöst.

* **Dateneinblicke, um fundierte Entscheidungen treffen zu können (bevorstehende Version)**: Neben Asset-Management und -Bereitstellung erfasst es Versanddateneinblicke in Asset-Sendungen im CDN, sodass Brand Manager Versandmetriken kanalübergreifend verfolgen können. Sie ermöglichen es ihnen, datenbasierte Entscheidungen zur kontinuierlichen Optimierung von Asset-Governance und Bereitstellungsstrategien zu treffen.

![Dynamic Media Open API data flow diagramm](assets/dm-openapi-dfd.png)

## Voraussetzungen für den Zugriff auf Dynamic Media mit OpenAPI-Funktionen {#prerequisites-dynaminc-media-open-apis}

Für den Zugriff auf Dynamic Media mit OpenAPI-Funktionen benötigen Sie Lizenzen für:

* AEM Assets as a Cloud Service

* AEM Dynamic Media

## Wie kann Dynamic Media mit OpenAPI-Funktionen aktiviert werden? {#enable-dynamic-media-open-apis}

Bevor Sie eine Anfrage zur Aktivierung von Dynamic Media mit OpenAPI-Funktionen in AEM as a Cloud Service senden, stellen Sie sicher, dass diese Option nicht bereits aktiviert ist.

Sobald die [Voraussetzungen](#prerequisites-dynaminc-media-open-apis) erfüllt sind und Dynamic Media mit OpenAPI-Funktionen in Ihrer AEM as a Cloud Service-Instanz aktiviert ist, steht für jedes genehmigte Asset im Repository eine Bereitstellungs-URL zur Verfügung. Informationen zum Kopieren der Bereitstellungs-URL finden Sie unter [Versand-URL für genehmigte Assets kopieren](approve-assets.md#copy-delivery-url-approved-assets) . Adobe empfiehlt die Verwendung dieser Methode, um zu überprüfen, ob Dynamic Media mit OpenAPI-Funktionen in AEM as a Cloud Service aktiviert ist, bevor ein Support-Ticket zur Aktivierung gesendet wird.

Um Dynamic Media mit OpenAPI-Funktionen in AEM as a Cloud Service zu aktivieren, senden Sie ein Adobe-Support-Ticket mit den folgenden Details:

* Cloud Service-Programm und Umgebungs-ID

* Details des Anwendungsfalls zur Lösung mit der Integration von Dynamic Media mit OpenAPI-Funktionen.

* Details der nachgelagerten Anwendungen, die in Dynamic Media mit OpenAPI-Funktionen integriert werden sollen.

  >[!NOTE]
  >
  Geben Sie zur Integration in eine Nicht-Adobe-Anwendung Domänennamen für die Zulassungsliste an, auf der die Anwendung gehostet wird.

* Details der wichtigsten Kundenkontakte, die am Integrationsprojekt beteiligt sind.

* Liste der wichtigsten Adobe-Account-Team-Mitglieder (E-Mail).

Nachdem Sie das Support-Ticket übermittelt haben, ermöglicht Adobe Dynamic Media mit OpenAPI-Funktionen in Ihrer Cloud Service-Umgebung und gibt Details wie die IMS-Client-ID frei, damit Sie mit der Integration fortfahren können.

>[!NOTE]
>
Schließen Sie `/conf/global/settings/dam/assets-configurations/assetdelivery` aus einem Inhaltspaket aus, um die Deaktivierung von Dynamic Media mit OpenAPI-Funktionen zu vermeiden.

## Weitere Informationen zu wichtigen Funktionen {#learn-more-key-capabilities}

<table>
<td>
   <a href="/help/assets/approve-assets.md">
   <img alt="Genehmigen von Assets in Experience Manager Assets" src="./assets/approved-assets.jpeg" />
   </a>
   <div>
      <a href="/help/assets/approve-assets.md">
      <strong>Genehmigen von Assets in Experience Manager Assets</strong>
      </a>
   </div>
   <p>
      <em>Genehmigen Sie Assets in AEM Assets, um die Asset-Verwaltung zu optimieren und so einen kontrollierten und effizienten Prozess für die Verarbeitung von Assets sicherzustellen.</em>
   </p>
</td>
<td>
   <a href="/help/assets/integrate-dynamic-media-open-apis.md">
   <img alt="Integrieren von AEM Assets in nachgelagerte Anwendungen" src="./assets/asset-selector-integration.png" />
   </a>
   <div>
      <a href="/help/assets/integrate-dynamic-media-open-apis.md">
      <strong>Integrieren von AEM Assets mit nachgelagerten Anwendungen</strong>
      </a>
   </div>
   <p>
      <em>Integrieren Sie Ihre eigene benutzerdefinierte Benutzeroberfläche mit dem Experience Manager Assets-Repository mithilfe der Such- und Bereitstellungs-APIs oder verwenden Sie die Adobe Micro-Frontend-Asset-Auswahl.</em>
   </p>
</td>
<td>
   <a href="/help/assets/overview-asset-selector.md">
   <img alt="Adobe Asset-Auswahl" src="./assets/asset-selector-prereqs.png" />
   </a>
   <div>
      <a href="/help/assets/overview-asset-selector.md">
      <strong>Adobe-Micro-Frontend-Asset-Auswahl</strong>
      </a>
   </div>
   <p>
      <em>Eine Benutzeroberfläche, die mit dem AEM Assets-Repository interagiert, um Assets zu suchen und sie dann in Ihrer Anwendungsbearbeitung zu verwenden.</em>
   </p>
</td>
</table>
<table>



<table>
<td>
   <a href="/help/assets/search-assets-api.md">
   <img alt="Suchen nach Assets Experience Manager Assets Repository" src="./assets/search-assets-api-overview.png" />
   </a>
   <div>
      <a href="/help/assets/search-assets-api.md">
      <strong>Suchen von Assets im Experience Manager Assets-Repository</strong>
      </a>
   </div>
   <p>
      <em>Suchen Sie Assets im AEM Assets-Repository, damit sie an nachgelagerte Anwendungen bereitgestellt werden können.</em>
   </p>
</td>
<td>
   <a href="/help/assets/deliver-assets-apis.md">
   <img alt="Bereitstellen von Assets für nachgelagerte Anwendungen" src="./assets/delivery-url.png" />
   </a>
   <div>
      <a href="/help/assets/deliver-assets-apis.md">
      <strong>Bereitstellen von Assets an nachgelagerte Anwendungen</strong>
      </a>
   </div>
   <p>
      <em> Stellen Sie Assets mithilfe einer Bereitstellungs-URL an integrierte nachgelagerte Anwendungen bereit.</em>
   </p>
</td>
<td>
   <a href="/help/assets/restrict-assets-delivery.md">
   <img alt="Beschränken des Zugriffs auf Assets in Experience Manager" src="./assets/restricted-access.png" />
   </a>
   <div>
      <a href="/help/assets/restrict-assets-delivery.md">
      <strong>Beschränken des Zugriffs auf Assets in Experience Manager</strong>
      </a>
   </div>
   <p>
      <em> DAM Admin oder Brand Manager schränken den Zugriff ein, indem Rollen für genehmigte Assets in der AEM as a Cloud Service-Autoreninstanz konfiguriert werden.</em>
   </p>
</td>

</table>
<table>
<td>
   <a href="/help/assets/integrate-remote-approved-assets-with-sites.md">
   <img alt="Integrieren der Remote-Version von AEM Assets mit AEM Sites" src="./assets/connected-assets-rdam.png" />
   </a>
   <div>
      <a href="/help/assets/integrate-remote-approved-assets-with-sites.md">
      <strong>Integrieren von Remote AEM Assets mit AEM Sites</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie Remote-AEM Assets in die AEM Sites-Umgebung integrieren. </em>
   </p>
</td>
<td>
   <a href="/help/assets/dynamic-media-open-apis-faqs.md">
   <img alt="Häufig gestellte Fragen zu Dynamic Media mit OpenAPI-Funktionen" src="./assets/dynamic-media-faqs.jpeg" />
   </a>
   <div>
      <a href="/help/assets/dynamic-media-open-apis-faqs.md">
      <strong>Häufig gestellte Fragen zu Dynamic Media mit OpenAPI-Funktionen</strong>
      </a>
   </div>
   <p>
      <em>Erhalten Sie eine Antwort auf die am häufigsten gestellten Fragen zu Dynamic Media mit OpenAPI-Funktionen.</em>
   </p>
</td>
<td>
   <a href="/help/assets/configure-custom-domain.md">
   <img alt="Konfigurieren einer benutzerdefinierten Domain" src="./assets/configure-custom-domain.jpeg" />
   </a>
   <div>
      <a href="/help/assets/configure-custom-domain.md">
      <strong>Benutzerdefinierte Domäne konfigurieren</strong>
      </a>
   </div>
   <p>
      <em>AEM as a Cloud Service verfügt zwar über eine Standarddomäne, Sie können sie jedoch nach Bedarf anpassen.</em>
   </p>
</td>

</table>
