---
title: Dynamic Media mit OpenAPI-Funktionen
description: Erfahren Sie mehr über Schlüsselkonzepte wie die Verwendung von Dynamic Media mit OpenAPI-Funktionen und die Aktivierung.
role: User
source-git-commit: 540aa876ba7ea54b7ef4324634f6c5e220ad19d3
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 0%

---

# Dynamic Media mit OpenAPI-Funktionen {#new-dynaminc-media-apis-overview}

In der modernen digitalen Welt ist die Erschließung des vollen Potenzials der digitalen Assets Ihrer Marke von entscheidender Bedeutung, um dem Wettbewerb voraus zu sein. Eine ganzheitliche Digital Assets Management (DAM)-Lösung erleichtert die Verwaltung von Assets, fördert die Markenkonsistenz und beschleunigt die Inhaltsbereitstellung bei gleichzeitiger Gewährleistung von Markenintegrität und außergewöhnlichen Kundenerlebnissen.

Dynamic Media mit OpenAPI-Funktionen stellt DAM in den Mittelpunkt eines agilen und effizienten Content-Supply-Chain-Ökosystems, um Asset-Governance und -Bereitstellung sicherzustellen.

## Warum sollte Dynamic Media mit OpenAPI-Funktionen verwendet werden? {#dynamic-media-open-api-features}

Dynamic Media mit OpenAPI-Funktionen bietet die folgenden Hauptvorteile:

* **Nahtlose Integrationen**: Dynamic Media mit OpenAPI-Funktionen bietet einen umfassenden Satz von Such- und Bereitstellungs-APIs. Dadurch können Ihre Entwickler [Integration der Bereitstellung von Assets in ihre Anwendungen](/help/assets/integrate-dynamic-media-open-apis.md). Zu den Anwendungen gehören Adobe sowie Anwendungen von Drittanbietern. Sie bietet eine [Benutzeroberfläche für die Auswahl von Micro Frontend-Assets](/help/assets/asset-selector.md) , um genehmigte Assets zu suchen und auszuwählen. Der Selektor kann mühelos in jede Anwendung integriert werden, die auf JavaScript-Frameworks wie React JS, Angular JS und Vanilla JS basiert.

* **Zentralisierte Verwaltung digitaler Assets**: DAM ist die zentrale Quelle der Wahrheit für alle digitalen Assets. Ihre digitalen Assets werden zentral in AEM Assets verwaltet und über Versand-URLs an verbrauchte Anwendungen bereitgestellt, ohne Asset-Binärdateien zu kopieren.

* **Echtzeit-Updates**: Änderungen an genehmigten Assets in DAM, einschließlich Versionsaktualisierungen und Metadatenänderungen, werden automatisch in die Versand-URLs übernommen. Mit einem kurzen TTL-Wert (Time-to-Live) von 10 Minuten, der für Dynamic Media mit OpenAPI-Funktionen über CDN konfiguriert wurde, werden Aktualisierungen in weniger als 10 Minuten auf allen Authoring- und veröffentlichten Benutzeroberflächen sichtbar.

* **Markenkonsistenz**: Nur [markengenehmigte Assets](/help/assets/approve-assets.md) für nachgelagerte Anwendungen eingesetzt werden. [Brand Manager und Marketingexperten behalten die strenge Kontrolle über Marken-Assets](/help/assets/restrict-assets-delivery.md). Es steht nur die genehmigte und neueste Version des Assets zur Verwendung zur Verfügung, wodurch Markenkonsistenz über alle Kanäle und Anwendungen hinweg gewährleistet ist.

* **Weboptimierter Versand**: Digitale Assets werden in Web-optimierten Formaten bereitgestellt, um die Web-Vitals Ihrer digitalen Erlebnisse zu verbessern. Dazu gehören die Unterstützung von WebP-Ausgabeformaten für Bilder, das adaptive Streaming über HLS- oder DASH-Protokolle für Videos und Original-Ausgabeformate für Dokumente.

* **Dynamische Asset-Umwandlung**: Unser System ermöglicht eine direkte Bildumwandlung mithilfe von URL-Parametern, die als Bild-Modifikatoren bezeichnet werden. [Beispiel: Breite, Höhe, Drehen, Spiegeln, Qualität, Zuschneiden, Format und smartes Zuschneiden](/help/assets/deliver-assets-apis.md). Transformierte Ausgabedarstellungen werden dynamisch generiert und nahtlos über das CDN bereitgestellt.

* **Sichere Bereitstellung von Assets**: Dynamic Media mit OpenAPI-Funktionen bietet einen Mechanismus zur Steuerung des Zugriffs auf Ihre digitalen Assets. Sie können Benutzerrollen oder Gruppen als Metadaten für zu sichernde Assets angeben und einen vordefinierten Zeitrahmen festlegen, in dem [Nur autorisierte Benutzer können auf diese Assets zugreifen](/help/assets/restrict-assets-delivery.md). Die Bereitstellungs-URLs für gesicherte Assets werden für nicht autorisierte Benutzer während des eingeschränkten Zeitraums nicht aufgelöst.

* **Dateneinblicke für fundierte Entscheidungen (in Kürze verfügbar)**: Neben Asset-Management und -Bereitstellung werden damit Einblicke in Versanddaten in Asset-Sendungen im CDN erfasst, sodass Brand Manager Versandmetriken kanalübergreifend verfolgen können. Sie ermöglichen es ihnen, datenbasierte Entscheidungen zur kontinuierlichen Optimierung von Asset-Governance und Bereitstellungsstrategien zu treffen.

![Dynamic Media Open API-Datenflussdiagramm](assets/dm-openapi-dfd.png)

## Voraussetzungen für den Zugriff auf Dynamic Media mit OpenAPI-Funktionen {#prerequisites-dynaminc-media-open-apis}

Für den Zugriff auf Dynamic Media mit OpenAPI-Funktionen benötigen Sie Lizenzen für:

* AEM Assets as a Cloud Service

* AEM Dynamic Media

## Wie kann Dynamic Media mit OpenAPI-Funktionen aktiviert werden? {#enable-dynamic-media-open-apis}

Bevor Sie eine Anfrage zur Aktivierung von Dynamic Media mit OpenAPI-Funktionen in AEM as a Cloud Service senden, stellen Sie sicher, dass diese Option nicht bereits aktiviert ist.

Einmal die [Voraussetzungen](#prerequisites-dynaminc-media-open-apis) erfüllt sind und wenn Dynamic Media mit OpenAPI-Funktionen in Ihrer AEM as a Cloud Service-Instanz aktiviert ist, steht für jedes genehmigte Asset im Repository eine Bereitstellungs-URL zur Verfügung. Informationen zum Kopieren der Versand-URL finden Sie unter [Versand-URL für genehmigte Assets kopieren](approve-assets.md#copy-delivery-url-approved-assets) . Adobe empfiehlt die Verwendung dieser Methode, um zu überprüfen, ob Dynamic Media mit OpenAPI-Funktionen in AEM as a Cloud Service aktiviert ist, bevor ein Support-Ticket zur Aktivierung gesendet wird.

Um Dynamic Media mit OpenAPI-Funktionen in AEM as a Cloud Service zu aktivieren, senden Sie ein Adobe-Support-Ticket mit den folgenden Details:

* Cloud Service-Programm und Umgebungs-ID

* Details des Anwendungsfalls zur Lösung mit der Integration von Dynamic Media mit OpenAPI-Funktionen.

* Details der nachgelagerten Anwendungen, die in Dynamic Media mit OpenAPI-Funktionen integriert werden sollen.

  >[!NOTE]
  >
  > Geben Sie zur Integration in eine Nicht-Adobe-Anwendung Domänennamen an die Whitelist, auf der die Anwendung gehostet wird.

* Details der wichtigsten Kundenkontakte, die am Integrationsprojekt beteiligt sind.

* Liste der wichtigsten Adobe-Account-Team-Mitglieder (E-Mail).

Nachdem Sie das Support-Ticket übermittelt haben, ermöglicht Adobe Dynamic Media mit OpenAPI-Funktionen in Ihrer Cloud Service-Umgebung und gibt Details wie die IMS-Client-ID frei, damit Sie mit der Integration fortfahren können.

>[!NOTE]
>
>Ausschließen `/conf/global/settings/dam/assets-configurations/assetdelivery` aus einem beliebigen Inhaltspaket, um die Deaktivierung von Dynamic Media mit OpenAPI-Funktionen zu vermeiden.

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
      <strong>Integrieren von AEM Assets in nachgelagerte Anwendungen</strong>
      </a>
   </div>
   <p>
      <em>Integrieren Sie Ihre eigene benutzerdefinierte Benutzeroberfläche mit dem Experience Manager Assets-Repository mithilfe der Such- und Bereitstellungs-APIs oder verwenden Sie die Adobe Micro-Frontend-Asset-Auswahl.</em>
   </p>
</td>
<td>
   <a href="/help/assets/asset-selector.md">
   <img alt="Adobe Asset-Auswahl" src="./assets/asset-selector-prereqs.png" />
   </a>
   <div>
      <a href="/help/assets/asset-selector.md">
      <strong>Adobe Micro-Frontend-Asset-Auswahl</strong>
      </a>
   </div>
   <p>
      <em>Eine Benutzeroberfläche, die mit dem AEM Assets-Repository interagiert, um Assets zu suchen und sie dann in Ihrer Anwendungsbearbeitung zu verwenden.</em>
   </p>
</td>
</table>
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
      <strong>Bereitstellen von Assets für nachgelagerte Anwendungen</strong>
      </a>
   </div>
   <p>
      <em>Stellen Sie Assets mithilfe einer Bereitstellungs-URL für integrierte nachgelagerte Anwendungen bereit.</em>
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

