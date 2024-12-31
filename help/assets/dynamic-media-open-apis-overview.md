---
title: Dynamic Media mit OpenAPI-Funktionen
description: Erfahren Sie mehr über Schlüsselkonzepte wie die Verwendung von Dynamic Media mit OpenAPI-Funktionen und wie diese aktiviert wird.
role: User
exl-id: 658b6eff-9f5a-4166-9ff6-5dc8eb92ada3
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 100%

---

# Dynamic Media mit OpenAPI-Funktionen {#new-dynaminc-media-apis-overview}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|-----|

>[!AVAILABILITY]
>
>Das Handbuch zu Dynamic Media mit OpenAPI-Funktionen ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den KI-Assistenten von Adobe Acrobat, um Ihre Fragen zu beantworten.
>
>[!BADGE Handbuch zu Dynamic Media mit OpenAPI-Funktionen als PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

In der modernen digitalen Welt ist die Erschließung des vollen Potenzials der digitalen Assets Ihrer Marke von entscheidender Bedeutung, um den Wettbewerb anzuführen. Eine ganzheitliche Digital Assets Management(DAM)-Lösung erleichtert die Governance von Assets, fördert die Markenkonsistenz und beschleunigt die Bereitstellung von Inhalten bei gleichzeitiger Gewährleistung von Markenintegrität und außergewöhnlichen Kundenerlebnissen.

Dynamic Media mit OpenAPI-Funktionen stellt das DAM in den Mittelpunkt eines agilen und effizienten Content-Lieferkettenökosystems, um die Governance und Bereitstellung von Assets sicherzustellen.

## Warum sollte Dynamic Media mit OpenAPI-Funktionen verwendet werden? {#dynamic-media-open-api-features}

Dynamic Media mit OpenAPI-Funktionen bietet die folgenden Hauptvorteile:

* **Nahtlose Integrationen**: Dynamic Media mit OpenAPI-Funktionen bietet einen umfassenden Satz von Such- und Bereitstellungs-APIs. Dadurch können Ihre Entwickelnden die [Bereitstellung von Assets ganz einfach in ihre Anwendungen integrieren](/help/assets/integrate-dynamic-media-open-apis.md). Zu den Anwendungen gehören Adobe sowie Anwendungen von Drittanbietern. Es bietet eine [Benutzeroberfläche für die Auswahl der Mikro-Frontend-Assets](/help/assets/overview-asset-selector.md) zum Suchen und Auswählen genehmigter Assets. Die Auswahl kann mühelos in jede Anwendung integriert werden, die auf JavaScript-Frameworks wie React JS, Angular JS und Vanilla JS basiert.

* **Zentralisierte Verwaltung digitaler Assets**: DAM ist die zentrale Datenquelle für alle digitalen Assets. Ihre digitalen Assets werden zentral in AEM Assets verwaltet und verarbeitenden Anwendungen durch Verweise über Bereitstellungs-URLs bereitgestellt, ohne Asset-Binärdateien zu kopieren.

* **Echtzeit-Aktualisierungen**: Alle Änderungen an genehmigten Assets in DAM, einschließlich Versionsaktualisierungen und Metadatenänderungen, werden automatisch in die Bereitstellungs-URLs übernommen. Mit einem niedrigen Time-to-Live(TTL)-Wert von 10 Minuten für die Dynamic Media mit OpenAPI-Funktion per CDN werden Aktualisierungen in weniger als 10 Minuten in allen Authoring- und Publishing-Oberflächen sichtbar.

* **Markenkonsistenz**: Nur [markenkonforme Assets](/help/assets/approve-assets.md) werden nachgelagerten Anwendungen offengelegt. [Markenverantwortliche und Marketing-Fachleute behalten die strenge Kontrolle über Marken-Assets](/help/assets/restrict-assets-delivery.md). Es können nur genehmigte und neueste Versionen des Assets verwendet werden. Dadurch wird die Markenkonsistenz in allen Kanälen und Anwendungen sichergestellt.

* **Web-optimierte Bereitstellung**: Digitale Assets werden in Web-optimierten Formaten bereitgestellt, um die Core Web Vitals Ihrer digitalen Erlebnisse zu verbessern. Dazu gehören die Unterstützung von WebP-Ausgabedarstellungen für Bilder, das adaptive Streaming über HLS- oder DASH-Protokolle für Videos und Original-Ausgabedarstellungen für Dokumente.

* **Dynamische Asset-Transformation**: Unser System ermöglicht die direkte Bildumwandlung mithilfe von URL-Parametern, die als Bildmodifikatoren bezeichnet werden. [Zum Beispiel Breite, Höhe, Drehung, Spiegelung, Qualität, Zuschnitt, Format und intelligenter Zuschnitt](/help/assets/deliver-assets-apis.md). Umgewandelte Ausgabedarstellungen werden dynamisch generiert und nahtlos über das CDN bereitgestellt.

* **Sichere Bereitstellung von Assets**: Dynamic Media mit OpenAPI-Funktionen bietet einen Mechanismus zur Steuerung des Zugriffs auf Ihre digitalen Assets. Sie können Benutzerrollen oder Gruppen als Metadaten für zu sichernde Assets angeben und einen vordefinierten Zeitraum festlegen, in dem [nur autorisierte Benutzende auf diese Assets zugreifen können](/help/assets/restrict-assets-delivery.md). Während des eingeschränkten Zeitraums werden die Bereitstellungs-URLs für gesicherte Assets für nicht autorisierte Benutzende nicht aufgelöst.

* **Dateneinblicke, um fundierte Entscheidungen treffen zu können (anstehende Version)**: Neben Asset-Management und -Bereitstellung werden Versanddateneinblicke in Asset-Sendungen im CDN erfasst, sodass Markenverantwortliche Versandmetriken kanalübergreifend verfolgen können. Es ermöglicht ihnen, datenbasierte Entscheidungen zur kontinuierlichen Optimierung von Asset-Governance und Bereitstellungsstrategien zu treffen.

![Dynamic Media OpenAPI-Datenflussdiagramm](assets/dm-openapi-dfd.png)

## Voraussetzungen für den Zugriff auf Dynamic Media mit OpenAPI-Funktionen {#prerequisites-dynaminc-media-open-apis}

Für den Zugriff auf Dynamic Media mit OpenAPI-Funktionen benötigen Sie folgende Lizenzen:

* AEM Assets as a Cloud Service

* AEM Dynamic Media

## Wie wird Dynamic Media mit OpenAPI-Funktionen aktiviert? {#enable-dynamic-media-open-apis}

Bevor Sie eine Anfrage zur Aktivierung von Dynamic Media mit OpenAPI-Funktionen in AEM as a Cloud Service senden, stellen Sie sicher, dass diese Option nicht bereits aktiviert ist.

Sobald die [Voraussetzungen](#prerequisites-dynaminc-media-open-apis) erfüllt sind und Dynamic Media mit OpenAPI-Funktionen in Ihrer AEM as a Cloud Service-Instanz aktiviert ist, steht für jedes genehmigte Asset im Repository eine Bereitstellungs-URL zur Verfügung. Informationen zum Kopieren der Bereitstellungs-URL finden Sie unter [Kopieren der Bereitstellungs-URL für genehmigte Assets](approve-assets.md#copy-delivery-url-approved-assets). Adobe empfiehlt die Verwendung dieser Methode, um zu überprüfen, ob Dynamic Media mit OpenAPI-Funktionen in AEM as a Cloud Service aktiviert ist, bevor ein Support-Ticket zur Aktivierung gesendet wird.

Um Dynamic Media mit OpenAPI-Funktionen in AEM as a Cloud Service zu aktivieren, senden Sie ein Adobe-Support-Ticket mit den folgenden Details:

* Cloud Services-Programm und Umgebungs-ID

* Einzelheiten zu dem Anwendungsfall, der mit der Integration von Dynamic Media mit OpenAPI-Funktionen gelöst werden soll.

* Details der nachgelagerten Anwendungen, die in Dynamic Media mit OpenAPI-Funktionen integriert werden sollen.

  >[!NOTE]
  >
  >Geben Sie zur Integration in eine Adobe-fremde Anwendung Domain-Namen für die Zulassungsliste an, auf denen die Anwendung gehostet wird.

* Details der wichtigsten Kundenkontakte, die am Integrationsprojekt beteiligt sind.

* Liste der wichtigsten Mitglieder des Adobe-Accountteams (E-Mail-Adressen).

Nachdem Sie das Support-Ticket übermittelt haben, aktiviert Adobe Dynamic Media mit OpenAPI-Funktionen in Ihrer Cloud Services-Umgebung und teilt Details wie die IMS-Client-ID, damit Sie mit der Integration fortfahren können.

>[!NOTE]
>
>Schließen Sie `/conf/global/settings/dam/assets-configurations/assetdelivery` aus allen Inhaltspaketen aus, um eine Deaktivierung von Dynamic Media mit OpenAPI-Funktionen zu vermeiden.

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
      <em>Genehmigen Sie Assets in AEM Assets, um das Asset-Management zu optimieren und so einen kontrollierten und effizienten Prozess für den Umgang mit Assets sicherzustellen.</em>
   </p>
</td>
<td>
   <a href="/help/assets/integrate-dynamic-media-open-apis.md">
   <img alt="Integrieren von AEM Assets mit nachgelagerten Anwendungen" src="./assets/asset-selector-integration.png" />
   </a>
   <div>
      <a href="/help/assets/integrate-dynamic-media-open-apis.md">
      <strong>Integrieren von AEM Assets mit nachgelagerten Anwendungen</strong>
      </a>
   </div>
   <p>
      <em>Sie können Ihre eigene benutzerdefinierte Benutzeroberfläche mit dem Experience Manager Assets-Repository integrieren, indem Sie die Such- und Bereitstellungs-APIs verwenden, oder nutzen Sie den Micro-Frontend-Asset-Wähler von Adobe.</em>
   </p>
</td>
<td>
   <a href="/help/assets/overview-asset-selector.md">
   <img alt="Asset-Wähler von Adobe" src="./assets/asset-selector-prereqs.png" />
   </a>
   <div>
      <a href="/help/assets/overview-asset-selector.md">
      <strong>Micro-Frontend-Asset-Wähler von Adobe</strong>
      </a>
   </div>
   <p>
      <em>Eine Benutzeroberfläche, die mit dem AEM Assets-Repository interagiert, um Assets zu suchen und diese dann für die Erstellung von Anwendungen zu verwenden.</em>
   </p>
</td>
</table>
<table>



<table>
<td>
   <a href="/help/assets/search-assets-api.md">
   <img alt="Suchen von Assets im Experience Manager Assets-Repository" src="./assets/search-assets-api-overview.png" />
   </a>
   <div>
      <a href="/help/assets/search-assets-api.md">
      <strong>Suchen von Assets im Experience Manager Assets-Repository</strong>
      </a>
   </div>
   <p>
      <em>Suchen Sie Assets im AEM Assets-Repository, damit sie für nachgelagerte Anwendungen bereitgestellt werden können.</em>
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
      <em>DAM-Admins oder Markenverantwortliche können den Zugriff einschränken, indem sie Rollen für genehmigte Assets in der Autoreninstanz von AEM as a Cloud Service konfigurieren.</em>
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
      <strong>Integrieren der Remote-Version von AEM Assets mit AEM Sites</strong>
      </a>
   </div>
   <p>
      <em>Erfahren Sie, wie Sie die Remote-Version von AEM Assets mit der AEM Sites-Umgebung integrieren. </em>
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
      <strong>Konfigurieren einer benutzerdefinierten Domain</strong>
      </a>
   </div>
   <p>
      <em>AEM as a Cloud Service verfügt zwar über eine Standard-Domain, Sie können sie aber nach Bedarf anpassen.</em>
   </p>
</td>

</table>
