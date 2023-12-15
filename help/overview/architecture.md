---
title: Einführung in die Architektur von Adobe Experience Manager as a Cloud Service
description: Einführung in die Architektur von Adobe Experience Manager as a Cloud Service.
exl-id: 3fe856b7-a0fc-48fd-9c03-d64c31a51c5d
source-git-commit: 3e40832ee4351c92ffc4eb22540223e331323821
workflow-type: tm+mt
source-wordcount: '2696'
ht-degree: 11%

---

# Einführung in die Architektur von Adobe Experience Manager as a Cloud Service {#an-introduction-to-the-architecture-adobe-experience-manager-as-a-cloud-service}

>[!CONTEXTUALHELP]
>id="intro_aem_cloudservice_architecture"
>title="Einführung in die Architektur von AEM as a Cloud Service"
>abstract="Auf dieser Registerkarte können Sie die neue Architektur von AEM as a Cloud Service anzeigen und die Änderungen verstehen. AEM hat zu einer dynamischen Architektur mit einer variablen Anzahl von Bildern geführt, sodass es wichtig ist, sich Zeit dafür zu nehmen, die Cloud-Architektur zu verstehen."
>additional-url="https://video.tv.adobe.com/v/330542/" text="Architekturüberblick"

Adobe Experience Manager (AEM) as a Cloud Service bietet eine Reihe von zusammenstellbaren Services für die Erstellung und Verwaltung von Erlebnissen mit hoher Wirkung.

Diese Seite bietet eine Einführung in die logische Architektur, die Dienstarchitektur, die Systemarchitektur und die Entwicklungsarchitektur für AEM as a Cloud Service.

## Logische Architektur {#logical-architecture}

AEM as a Cloud Service besteht aus allgemeinen Lösungen wie AEM Sites, AEM Assets und AEM Forms. Diese Dienste sind einzeln lizenziert, können aber in Zusammenarbeit verwendet werden. Jede Lösung verwendet eine Kombination aus zusammenstellbaren Diensten, die von AEM as a Cloud Service bereitgestellt werden, abhängig von den jeweiligen Anwendungsfällen.

### Programme {#programs}

AEM werden in Form eines [Programm](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) die Sie in der Cloud Manager-Anwendung gemäß Ihren Lizenzberechtigungen erstellen. Diese Programme geben Ihnen vollständige Kontrolle darüber, wie die zugehörige AEM benannt, konfiguriert und wie Berechtigungen im Kontext eines bestimmten Projekts zugewiesen werden.

Als Kunde werden Sie in der Regel durch Adobe als **Mandant**, auch als *IMS-Organisation* (Identity Management-System). Ein Mandant kann beliebig viele Programme haben und lizenziert sein. So ist es zum Beispiel üblich, ein zentrales Programm für AEM Assets zu sehen, während AEM Sites in mehreren Programmen verwendet werden kann, die mehreren Online-Erlebnissen entsprechen.

>[!NOTE]
>
>AEM Edge Delivery Services werden in Cloud Manager als Top-Level-Lösung bereitgestellt und sind gleichzeitig Teil der anderen Hauptlösungen aus Lizenzierungsgründen. Beispielsweise AEM Sites mit Edge Delivery Services.

Ein Programm kann mit einer beliebigen Kombination der übergeordneten Lösungen konfiguriert werden. Jede Lösung kann von 1:n-Add-ons unterstützt werden. z. B. Commerce oder Screens für AEM Sites, Dynamic Media oder Brand Portal für AEM Assets.

![AEM as a Cloud Service - Programme](assets/architecture-aem-edge-programs.png "AEM as a Cloud Service - Implementierungsarchitektur")

### Umgebungen {#environments}

Sobald ein Programm mit den Lösungen AEM Sites, AEM Assets oder AEM Forms erstellt wurde, werden die zugehörigen AEM in Form von AEM Umgebungen in diesem Programm dargestellt.

Es gibt vier Arten von [Umgebung](/help/implementing/cloud-manager/manage-environments.md) verfügbar mit AEM as a Cloud Service:

* Produktionsumgebung:

   * Eine Produktionsumgebung hostet die Anwendungen für Geschäftsleute und führt die Live-Erlebnisse aus.

* Staging-Umgebung:

   * Eine Staging-Umgebung ist in der Regel mit einer Produktionsumgebung in einer 1:1-Beziehung verknüpft.
   * Die Staging-Umgebung ist in erster Linie für automatisierte Tests ausgelegt, bevor Änderungen an der Anwendung in die Produktionsumgebung übertragen werden.
      * Dies ist unabhängig von den Änderungen, die entweder von Adobe im Rahmen eines Wartungsupdates oder von Ihren Code-Bereitstellungen initiiert werden.
      * Im Falle einer Code-Implementierung können Sie auch manuelle Tests durchführen.
   * Der Inhalt der Staging-Umgebung wird in der Regel mithilfe der Self-Service-Funktion zum Kopieren von Inhalten mit dem Produktionsinhalt synchronisiert.
   * Führen Sie Leistungs- und Sicherheitstests in der Staging-Umgebung durch.  Sie hat dieselbe Größe wie die Produktion.
* Entwicklungsumgebung:
   * Mit einer Entwicklungsumgebung können Entwickler AEM Anwendungen unter denselben Laufzeitbedingungen wie die Staging- und Produktionsumgebungen implementieren und testen.
   * Die Änderungen durchlaufen eine Bereitstellungs-Pipeline, die für dieselben Code-Qualitäts- und Sicherheitstests wie in Produktions-Bereitstellungs-Pipelines sorgt.
   * Entwicklungsumgebungen haben nicht dieselbe Größe wie Staging- und Produktionsumgebungen und sollten nicht für Leistungs- und Sicherheitstests verwendet werden.
* Rapid Development Environment (RDE):
   * Eine RDE-Umgebung ermöglicht eine schnelle Entwicklung von Iterationen bei der Bereitstellung von neuem oder vorhandenem Code in den RDE-Instanzen, ohne dass eine formale Bereitstellungs-Pipeline wie in regulären Entwicklungsumgebungen durchlaufen wird.

### Edge Delivery Services {#logical-architecture-edge-delivery-services}

Ein AEM Programm kann mit der [Edge-Bereitstellungsdienste](/help/edge/overview.md) sowie.

Nach der Konfiguration kann AEM auf GitHub-Code-Repositorys verweisen, die zum Erstellen der Erlebnisse mit Edge Delivery Services verwendet werden. Daher stehen neue Konfigurationsoptionen für die zugehörigen Erlebnisse zur Verfügung. Dazu gehören die Einrichtung des Adobe-verwalteten CDN und der Zugriff auf Lizenzierungsmetriken oder SLA-Berichte.

## Dienstarchitektur {#service-architecture}

Die Liste der übergeordneten, zusammenstellbaren Dienste in AEM as a Cloud Service kann mit zwei Segmenten dargestellt werden: Content Management und Experience Delivery:

![AEM as a Cloud Service Übersicht - mit Edge Delivery Services](assets/architecture-aem-edge.png "AEM as a Cloud Service Übersicht - mit Edge Delivery Services")

Für das Content Management gibt es zwei Hauptdienste für die Inhaltserstellung, die beide als *Inhaltsquellen*:

* AEM-Autorenstufe: Bietet eine webbasierte Schnittstelle (mit zugehörigen APIs) für die Verwaltung von Webinhalten. Dies funktioniert für beide Ansätze:
   * Headful - über den Seiten-Editor und den universellen Editor
   * Headless - über den Inhaltsfragment-Editor
* Die dokumentbasierte Authoring-Ebene: Ermöglicht die Erstellung von Inhalten mithilfe von Standardanwendungen wie:
   * Microsoft Word und Excel - über SharePoint
   * Google Docs and Sheets - über Google Drive

Bei der Bereitstellung von Erlebnissen gibt es bei der Verwendung von AEM Sites oder AEM Forms auch zwei Hauptdienste, die sich nicht gegenseitig ausschließen und unter einem gemeinsam genutzten Adobe-verwalteten CDN (Content Delivery Network) mit unterschiedlichen Ursachen arbeiten:

* Die AEM Veröffentlichungsstufe:
   * Führt eine Farm mit standardmäßigen AEM-Herausgebern und Dispatchern aus, wodurch Webseiten und API-Inhalte (z. B. GraphQL), die mit veröffentlichten Inhalten zusammengestellt wurden, dynamisch gerendert werden können.
   * basiert hauptsächlich auf der serverseitigen Anwendungslogik.
* Veröffentlichungsstufe in Edge-Bereitstellung:
   * Ermöglicht das dynamische Rendering von Webseiten und API-Inhalten aus verschiedenen Inhaltsquellen, z. B. der AEM-Autorenstufe oder der dokumentbasierten Authoring-Ebene.
   * basiert auf der Client-seitigen Anwendungslogik und wurde für maximale Leistung entwickelt.

Es gibt auch die wichtigsten benachbarten Dienste:

* Die Edge-Zustellungs-Assets-Ebene:
   * Ermöglicht die Bereitstellung genehmigter und veröffentlichter Medienelemente aus AEM Assets. Zum Beispiel Bilder und Videos.
   * Die Medienelemente werden in der Regel aus Erlebnissen referenziert, die auf der AEM Veröffentlichungsstufe oder der Edge-Veröffentlichungsstufe ausgeführt werden, oder aus jeder anderen in AEM Assets integrierten Adobe Experience Cloud-Anwendung.
* Die AEM Vorschaustufe und die Edge Delivery Services-Vorschaustufe:
   * Sind auch für Erlebnisse verfügbar, die mit der Veröffentlichungsstufe AEM oder der Veröffentlichungsstufe Edge Delivery erstellt wurden.
   * Ermöglicht es Autoren von Inhalten, kontextbezogene Inhalte vor Veröffentlichungsvorgängen in der Vorschau anzuzeigen.

>[!NOTE]
>
>Standardmäßig verfügen Programme, die nur für Assets vorgesehen sind, weder über eine Veröffentlichungsstufe noch über eine Vorschauebene.

Es gibt weitere benachbarte Dienstleistungen:

* Der Replikationsdienst:
   * Wird zwischen der Content-Management-Ebene und der Erlebnis-Bereitstellungsebene platziert.
   * Ist für die Verarbeitung der *publish* Vorgänge, die von Inhaltsautoren herausgegeben werden und dann die veröffentlichten Inhalte für die Veröffentlichungsstufen (AEM oder Edge-Bereitstellung) bereitstellen.

  >[!NOTE]
  >Der Replikationsdienst durchlief eine vollständige Neugestaltung im Vergleich zu den 6.x-Versionen von AEM, da das Replikations-Framework aus früheren Versionen von AEM nicht mehr zum Veröffentlichen von Inhalten verwendet wird.
  >
  >Die neueste Architektur basiert auf einer *Publizieren und abonnieren* -Ansatz mit Cloud-basierten Inhaltswarteschlangen. Für die AEM Veröffentlichungsstufe ermöglicht es einer variablen Anzahl von Herausgebern, den Veröffentlichungsinhalt zu abonnieren, und ist ein wesentlicher Bestandteil des Erreichens einer echten und schnellen automatischen Skalierung für AEM as a Cloud Service

* Der Content Repository-Dienst:
   * Wird von der AEM Autorenstufe verwendet.
   * ist eine Cloud-basierte Instanz eines JCR-kompatiblen Inhalts-Repositorys, das von der Apache Oak-Technologie implementiert wird.
   * Die Persistenz von Inhalten basiert hauptsächlich auf blob-basiertem Cloud-Speicher.
* Der CI/CD-Dienst:
   * Stellt die Untergruppe der Cloud Manager-Funktionen dar, die für die Verwaltung von Bereitstellungs-Pipelines für die AEM Umgebungen vorgesehen sind.
* Der Testdienst:
   * Stellt die zugrunde liegende Infrastruktur dar, die für die Ausführung verwendet wird:
      * Funktionstests,
      * UI-Tests: z. B. basierend auf Selenium- oder Cypress-Skripten,
      * Erlebnisprüfungstests: z. B. Lighthouse-Bewertungen,

     als Teil einer Bereitstellungs-Pipeline in eine AEM-Umgebung oder als Teil einer GitHub-Pull-Anfrage an ein Edge-Bereitstellungscode-Repository.
* Der Data-Dienst:
   * ist für die Anzeige von Kundendaten wie Lizenzierungsmetriken (z. B. Inhaltsanforderungen, Speicher, Benutzer) oder Nutzungsberichten (z. B. die Anzahl der Uploads und Downloads) verantwortlich.
   * Die Kundendaten können über APIs und über Produktbenutzeroberflächen (z. B. Cloud Manager) bereitgestellt werden.
* Der RUM-Dienst (Real-User Metric):
   * ist für die Erfassung von Schlüsselmetriken aus einem Kundenerlebnis (z. B. Seitenansichten, Web-Lebenszyklen, Konversionsereignisse) und die Beantwortung von zugehörigen Abfragen (z. B. Top-Seitenansichten für eine bestimmte Domäne in den letzten 7 Tagen) zuständig.
* Der Assets Compute-Dienst:
   * ist für die Verarbeitung hochgeladener Bilder, Videos und Dokumente zuständig, z. B. PDF- und Adobe Photoshop-Dateien. Die Verarbeitung kann Adobe Sensei verwenden, um Bild- und Videometadaten (wie beschreibende Tags oder primäre Farbtöne) zu extrahieren und dann Ausgabedarstellungen (wie unterschiedliche Größen oder Formate) mit Zugriff auf APIs wie die Adobe Photoshop- und Adobe Lightroom-APIs zu generieren.
* Der Identity Management-Dienst (IMS):
   * ist der zentrale Ort, der für die Verwaltung und Authentifizierung von Benutzern und Benutzergruppen für eine bestimmte Adobe Experience Cloud-Anwendung zuständig ist (z. B. Cloud Manager oder AEM Autorenstufe).
   * Der Zugriff erfolgt über Adobe Admin Console.

## Systemarchitektur {#system-architecture}

### AEM-, Vorschau- und Veröffentlichungsebenen {#aem-author-preview-publish-tiers}

Die AEM Autoren- und Veröffentlichungsstufen werden als Satz von Docker-Containern implementiert, die von einem standardmäßigen Container Orchestration Service verwaltet werden. Die daraus resultierende containerisierte Architektur ist ein vollständig dynamisches System mit einer variablen Anzahl von Pods, die von der tatsächlichen Aktivität (für Content Management) und dem tatsächlichen Traffic (für die Bereitstellung von Erlebnissen) abhängt. Dadurch können AEM as a Cloud Service Ihre Traffic-Muster bei deren Änderung berücksichtigen.

Die AEM Autorenstufe wird als Cluster von AEM Autorenpods verwendet, die ein einzelnes Inhalts-Repository gemeinsam nutzen. Mindestens zwei Pods ermöglichen die Kontinuität des Geschäftsbetriebs, während Wartungsaufgaben ausgeführt werden oder ein Bereitstellungsprozess stattfindet.

Die AEM Veröffentlichungsstufe wird als Farm AEM Veröffentlichungsinstanzen mit jeweils einem eigenen Inhalts-Repository mit veröffentlichten Inhalten betrieben. Jeder Herausgeber ist an eine einzige Apache-Instanz gekoppelt, die mit dem AEM Dispatcher-Modul für eine materialisierte Ansicht des Inhalts ausgestattet ist und als Ursprung für das von Adobe verwaltete CDN dient. Mindestens zwei Pods ermöglichen auch die Kontinuität des Geschäftsbetriebs, aber es ist nicht ungewöhnlich, dass sich diese Zahl in Zeiten hohen Traffics ausweitet.

Die AEM Vorschaustufe besteht aus einem einzigen AEM Knoten. Dies wird zur Qualitätssicherung von Inhalten vor der Veröffentlichung in der Veröffentlichungsstufe verwendet. Gelegentliche Ausfallzeiten, insbesondere bei Bereitstellungen, können auf der Vorschauebene auftreten.

### Edge Delivery Services {#system-architecture-edge-delivery-services}

Die Edge Delivery Services werden auf einer CDN- und Server-losen Infrastruktur betrieben, um die Seiten optimal zusammenzustellen. Wenn eine Ressource angefordert wird, ist die Server-lose Infrastruktur für die Konvertierung der veröffentlichten Inhalte in semantische HTML verantwortlich und dient als Ursprung für das CDN.

Die Konvertierung in die semantische HTML erfolgt über den veröffentlichten Inhalt, der von der AEM Autorenstufe oder der dokumentbasierten Authoring-Umgebung bereitgestellt wird.

Das folgende Diagramm zeigt, wie Sie Sites-Inhalte in Microsoft Word (dokumentbasiertes Authoring) bearbeiten und in der Edge-Bereitstellung veröffentlichen können. Es zeigt auch die herkömmliche AEM-Veröffentlichungsmethode mit den verschiedenen Editoren.

![AEM Sites as a Cloud Service - mit Edge Delivery Services](assets/architecture-aem-edge-author-publish.png "AEM Sites as a Cloud Service - mit Edge Delivery Services")

Da Edge Delivery Services Teil von Adobe Experience Manager sind und als solche die Edge-Bereitstellung sind, können AEM Sites und AEM Assets gleichzeitig in derselben Domäne vorhanden sein. Dies ist ein häufiger Anwendungsfall für größere Websites. So kann ein Kunde beispielsweise eine bestimmte Seite mit hohem Traffic zu Edge Delivery Services migrieren, während alle anderen Seiten auf der AEM Veröffentlichungsebene verbleiben können.

## Entwicklungsarchitektur {#development-architecture}

### Code-Repositories {#code-repositories}

Der Code und die Konfiguration für AEM Projekte werden in einem Code-Repository gespeichert, aus dem bei Änderungen Bereitstellungs-Pipelines ausgegeben werden. Es gibt verschiedene Typen von Code-Repositorys:

* AEM vollständigen Stapel:
   * Zum Speichern von serverseitigem Java-Code und OSGi-Konfigurationen für die AEM-Autoren- und Veröffentlichungsstufe.
* AEM Frontend:
   * Zum Speichern von clientseitigem JS-, CSS- und HTML-Code für die AEM Autoren- und Veröffentlichungsstufe.
Weitere Informationen zu Client-seitigen Bibliotheken finden Sie unter [Verwenden Client-seitiger Bibliotheken auf AEM as a Cloud Service.](/help/implementing/developing/introduction/clientlibs.md)
* AEM Webstufe:
   * Speichert die Dispatcher-Konfigurationsdateien für die AEM Veröffentlichungsstufe.
* AEM Konfiguration:
   * Ermöglicht das Speichern verschiedener Konfigurationsoptionen (z. B. CDN-Einstellungen oder Einstellungen für Wartungsaufgaben) für die AEM Veröffentlichungsstufe und die Edge Delivery Services-Veröffentlichungsstufe.
* AEM Edge-Bereitstellung:
   * Zum Speichern des clientseitigen JS-, CSS- und HTML-Codes für Sites, die mit den Edge Delivery Services erstellt wurden

### Implementierungs-Pipelines {#deployment-pipelines}

Entwickler und Administratoren verwalten die AEM as a Cloud Service Anwendung mit einem CI/CD-Dienst (Continuous Integration/Continuous Delivery), der über Cloud Manager bereitgestellt wird. Cloud Manager bietet außerdem alles, was mit Überwachung, Wartung, Fehlerbehebung (z. B. Zugriff auf Protokolldateien) und Lizenzierung zu tun hat.

![AEM as a Cloud Service – Bereitstellungsarchitektur](assets/architecture-aem-edge-deployment-pipelines.png "AEM as a Cloud Service – Bereitstellungsarchitektur")

Cloud Manager verwaltet alle Aktualisierungen Ihrer Instanzen des AEM as a Cloud Service. Dies ist die einzige Möglichkeit, die Kundenanwendung zu erstellen, zu testen und für die Autoren-, Vorschau- und Veröffentlichungsschicht bereitzustellen. Diese Aktualisierungen können durch Adobe ausgelöst werden, wenn eine neue Version der AEM Cloud Service fertig ist, oder durch Sie selbst, wenn eine neue Version Ihrer Anwendung bereit ist.

Dies wird durch eine Bereitstellungs-Pipeline implementiert, die an jede Umgebung innerhalb eines Programms gekoppelt ist. Wenn eine Cloud Manager-Pipeline ausgeführt wird, wird eine neue Version der Kundenanwendung erstellt, sowohl für die Autorenstufe als auch für die Veröffentlichungsstufe. Dies wird erreicht, indem die neuesten Kundenpakete mit dem neuesten Grundlinien-Adobe-Image kombiniert werden.

Die Bereitstellungs-Pipeline wird ausgelöst, wenn Kunden Code-Änderungen vornehmen oder wenn Adobe eine neue Wartungsversion bereitstellt.

In beiden Fällen wird derselbe Satz automatisierter Tests ausgeführt. Er besteht aus folgenden Tests:

* von Adobe zur Gewährleistung der Produktintegrität beigetragen
* vom Kunden hinzugefügte Tests
   * Funktionstests: über HTTP-Anforderungen an die AEM- oder Veröffentlichungsstufe
   * UI-Tests auf Basis von Selenium- oder Cypress-Technologie

Diese automatisierten Tests werden in der Staging-Umgebung ausgeführt. Daher ist es wichtig, den Inhalt der Staging-Umgebung so nah wie möglich an den Inhalt in der Produktionsinstanz zu halten.

Sobald alle Tests erfolgreich bestanden wurden, wird der neue Code in der Produktionsumgebung bereitgestellt.

### Rollierende Aktualisierungen {#rolling-updates}

Cloud Manager automatisiert den Cut-over-Vorgang vollständig auf die neueste Version der AEM Anwendung, indem alle Dienstknoten mithilfe eines kontinuierlichen Aktualisierungsmusters aktualisiert werden. Das bedeutet, dass **keine Ausfallzeiten** für den Autoren- oder Veröffentlichungsdienst.

## Wichtige Innovationen seit AEM 6.x {#major-innovations-since-aem-6x}

Die neueste Architektur für AEM as a Cloud Service bietet einige grundlegende Änderungen und Innovationen im Vergleich zu früheren Generationen (AEM 6.x und früher):

* Alle Dateien werden direkt aus einem Cloud-Datenspeicher hochgeladen und bereitgestellt. Der zugehörige Bitstrom durchläuft niemals die JVM der AEM-Autoren- und Veröffentlichungs-Services. Daher können die Knoten der AEM Autoren- und Veröffentlichungsdienste kleiner sein und daher besser mit der Erwartung einer schnellen automatischen Skalierung kompatibel sein. Für Geschäftsleute führt dies zu einem schnelleren Erlebnis beim Hochladen und Herunterladen von Bildern, Videos und anderen Aufgaben.

* Alle Vorgänge, die aus der Veröffentlichung von Inhalten bestehen, beinhalten jetzt eine Pipeline nach einem Abonnementmuster. Veröffentlichte Inhalte werden an verschiedene Warteschlangen in der Pipeline gesendet, die von allen Knoten des Veröffentlichungs-Service abonniert werden. Daher muss die Autorenebene nicht wissen, wie viele Knoten im Veröffentlichungs-Service vorhanden sind. Dies ermöglicht eine schnelle automatische Skalierung der Veröffentlichungsebene.

* Die Architektur trennt den Anwendungsinhalt vollständig vom Anwendungs-Code und der Konfiguration. Der gesamte Code und die Konfiguration sind praktisch unveränderlich und werden in das Grundlinienbild zur Erstellung der verschiedenen Knoten des Autoren- und Veröffentlichungs-Service zurückgeschrieben. Daher gibt es eine absolute Garantie, dass jeder Knoten identisch ist und die Änderungen am Code und der Konfiguration nur global vorgenommen werden können, indem eine Cloud Manager-Pipeline ausgeführt wird.

* Die Architektur umfasst mehrere Microservices, die auf Server-loser Technologie basieren, insbesondere mit der Adobe I/O-Laufzeit

## Weiterführende Informationen {#further-information}

Siehe auch:

* Edge Delivery Services:

   * [AEM as a Cloud Service Übersicht - mit Edge Delivery Services](/help/edge/overview.md)
   * [Verwenden von Edge Delivery Services](/help/edge/using.md)
   * [Erkunden Sie die zugrunde liegende Architektur und wichtige AEM, die mit Edge Delivery Services as a Cloud Service sind.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/introduction/architecture.html?lang=de)
