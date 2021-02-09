---
title: Implementieren von AEM-Connectoren
description: Implementieren von AEM-Connectoren
translation-type: tm+mt
source-git-commit: 69756d6831678151b0e8eb73db81113d49f17447
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 100%

---


Implementieren von AEM-Connectoren
=============================

Im Folgenden finden Sie nützliche Hinweise zum Erstellen von [AEM-Connectoren](https://www.adobe.io/apis/experiencecloud/aem/aemconnectors.html). Sie sollten zusammen mit Anleitungen zum [Senden](submit.md) und [Warten](maintain.md) von Connectoren gelesen werden.

Beachten Sie, dass eine Entwicklerlizenz für AEM über das [Adobe Exchange-Programm](https://partners.adobe.com/exchangeprogram/experiencecloud) erhältlich ist.

Gängige Integrationsmuster
---------------------------

AEM ist eine hochmoderne Web-Experience-Management-Lösung und bietet viele potenzielle Integrationsbereiche. Zu den gängigen Integrationsmustern gehören:

* Abruf von Daten von einem externen System in AEM. Exportieren Sie beispielsweise Kontaktinformationen aus einem CRM-System, um sie einer breiteren Zielgruppe beim Besuch einer AEM-basierten Website zur Verfügung zu stellen.  Implementierungen sollten die [geplanten Aufträge](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#scheduled-jobs) von Sling verwenden, die garantieren, dass der Auftrag auch dann ausgeführt wird, wenn die Container ausfallen. Code sollte so konzipiert sein, dass der Auftrag möglicherweise mehrmals ausgelöst werden kann.
* Exportieren von Daten aus AEM in ein externes System. Beispielsweise Einstellungen für ein Newsletter-Abonnement, die auf einer AEM-unterstützten Website an ein CRM-System gesendet werden.
* Abrufen von Assets aus AEM. Beispielsweise ein externes Content Management System (CMS), das auf ein in AEM Assets gespeichertes Asset verweist. Oder als weiteres Beispiel ein PIM-System, das mit einem Bild in AEM Assets verknüpft ist.
* Speichern von Assets in der AEM-Infrastruktur. Zum Beispiel ein Marketing-Ressourcen-Management (MRM)-System, das ein genehmigtes Asset in AEM Assets speichert.
* Konfigurieren und Rendern einer benutzerdefinierten Komponente der Benutzeroberfläche. Beispielsweise können Sie einem Autor gestatten, eine Videokomponente per Drag-and-Drop zu verschieben und ein bestimmtes Video für die Wiedergabe auf der Live-Site zu konfigurieren.
* Aktionen für ein Asset mit einem Partnerdienst. Senden eines Assets an eine Videoplattform, wenn eine Seite veröffentlicht wird.
* Analysieren einer Site, Seite oder eines Assets in der AEM Admin Console. So können Sie beispielsweise SEO-Empfehlungen für eine vorhandene oder unveröffentlichte Seite abgeben.
* Zugriff auf Benutzerdaten auf Seitenebene, die von einem externen Dienst verwaltet werden. Sie können beispielsweise demografische Informationen nutzen, um das Site-Erlebnis zu personalisieren. Lesen Sie mehr über ContextHub, ein Framework zum Speichern, Bearbeiten und Präsentieren von Kontextdaten.
* Übersetzung von Site-Kopien oder Asset-Metadaten. Im [AEM Translation Framework Bootstrap Connector](https://github.com/Adobe-Marketing-Cloud/aem-translation-framework-bootstrap-connector) finden Sie Beispiel-Code für das AEM Translation Framework, das die bevorzugte Implementierung von Übersetzungs-Connectoren ist.


Hilfreiche Dokumentationen
--------------------

Die [Dokumentation](../overview/introduction.md) zu Experience Manager as a Cloud Service bietet wertvolle Einblicke in die Entwicklung in AEM. Im Folgenden finden Sie einige spezifische technische Themen und Referenzen, die bei der Implementierung eines AEM-Connectors möglicherweise nützlich sein können:

* [AEM-Beispiele](http://adobe-consulting-services.github.io/acs-aem-samples/) von Adobe Consulting Services (ACS) für gut kommentierten Code zur Schulung von AEM-Entwicklern
* Die verschiedenen Dokumentations-Links im Abschnitt „Gängige Integrationsmuster“ dieses Artikels

Community-Ressourcen
--------------------

Zusätzlich zur obenstehenden statischen Dokumentation bieten Adobe und die AEM-Community Ressourcen an, um einen Connector auf den Markt zu bringen:

* Das [AEM-Forum](http://help-forums.adobe.com/content/adobeforums/en/experience-manager-forum/adobe-experience-manager.html) der Adobe Community ist eine aktive Website, auf der Ihre Kollegen Fragen stellen und beantworten
* Für bestimmte Partnerstufen stehen zusätzliche technische Ressourcen von Adobe zur Verfügung. Weitere Informationen zum [Adobe Exchange-Programm](https://partners.adobe.com/exchangeprogram/experiencecloud).
* Wenn Ihr Unternehmen Hilfe bei der Implementierung wünscht, wenden Sie sich an das [Professional Services](http://www.adobe.com/de/marketing-cloud/service-support/professional-consulting-training.html)-Team von Adobe oder suchen Sie im [Solution Partner Finder](https://solutionpartners.adobe.com/home/partnerFinder.html) eine Liste der Adobe-Partner auf der ganzen Welt

Regeln für die Paketstruktur
-----------------------

Um fortlaufende Bereitstellungen zu unterstützen, wird bei AEM as a Cloud Service-Paketen (z B. Connectoren) strikt zwischen „unveränderlichen“ und „veränderlichen“ Inhalten unterschieden. Es sollte klar zwischen Paketen mit den folgenden Inhalten unterschieden werden:

* `/apps`
* `/content` und `/conf`

Connectoren sollten sich an die in [diesem Artikel](/help/implementing/developing/introduction/aem-project-content-package-structure.md) beschriebenen Richtlinien zur Paketerstellung halten. Bestehende Connectoren sollten ebenfalls entsprechend umgestaltet werden.

Darüber hinaus sollte nur Adobe Code in `/libs` schreiben, während Kunden und Partner in `/apps` schreiben.

Bestehende Connectoren müssen möglicherweise auch umstrukturiert werden, um jede Konfiguration, die einmal in `/etc` platziert wurde, in andere Ordner der obersten Ebene, wie z. B. `/conf`, zu verschieben. Dies wird in der [AEM-Dokumentation](https://helpx.adobe.com/de/experience-manager/6-5/sites/deploying/using/repository-restructuring.html) beschrieben.

Es wird empfohlen, den Großteil des Connector-Codes unter `/apps/connectors/<vendor>` zu platzieren, um eine saubere Repository-Struktur für Kunden mit mehreren Connectoren zu unterstützen.

Cloud Services-Konfigurationen
-----------------------------

Ein Aspekt der Connector-Implementierung ist der Code, der die Konfiguration des Connectors unterstützt. Durch diesen Code wird eine Karte mit dem Namen des Connectors unter „Tools“ > „Vorgänge“ > „Cloud Services“ angezeigt. Beim Klicken wird ein [Konfigurations-Browser](/help/implementing/developing/introduction/configurations.md#using-configuration-browser) geöffnet, in dem der Kunde den übergeordneten Ordner für die Connector-Konfiguration auswählt. Der Code des Connectors sollte zu einem Formular mit allen zu konfigurierenden Eigenschaften führen und die Werte letztendlich in einem Konfigurationsordner unter `/conf` speichern. Dieser Ordner kann später auf der Registerkarte „Sites-Eigenschaften“ oder auf der Registerkarte „Asset-Eigenschaften“ ausgewählt werden.


Kontextabhängige Konfigurationen
-----------------------------

[Kontextabhängige Konfigurationen](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html) ermöglichen die Konfiguration von Ebenen über verschiedene Ordner hinweg, einschließlich `/libs`, `/apps`, `/conf` und der Unterordner unter `/conf`. Es wird die Vererbung unterstützt, sodass ein Kunde eine globale Konfiguration festlegen und gleichzeitig spezifische Änderungen für jede Microsite vornehmen kann. Da diese Funktion für Cloud Services-Konfigurationen genutzt werden kann, sollte der Connector-Code mithilfe der API für kontextabhängige Konfigurationen auf die Konfiguration verweisen, anstatt auf einen bestimmten Konfigurationsknoten zu verweisen.

Wenn im Connector geänderte Konfigurationen verwendet werden, können Sie den Connector so gestalten, dass zukünftige Aktualisierungen der vom Connector bereitgestellten Standardkonfigurationen mit Kundenkonfigurationen integriert/zusammengeführt werden. Denken Sie daran, dass das Ändern von benutzerdefinierten (also vom Kunden geänderten) Inhalten oder Konfigurationen ohne Warnung und Zustimmung des Kunden zu einer Unterbrechung (oder zu unerwartetem Verhalten) des Connectors führen kann.

Best Practices für die Kodierung
----------------------

Da AEM as a Cloud Service eine Cloud-native Lösung ist, gibt es einige Richtlinien, die die Code-Strategien eines Connectors beeinflussen können. Weitere Informationen finden Sie unter [Entwicklungsrichtlinien für AEM as a Cloud Service](/help/implementing/developing/introduction/development-guidelines.md).

Testen von AEM-Connectoren
-------------------------

Neue Connectoren sollten mithilfe lokaler Entwicklungstechniken erstellt (oder vorhandene Connectoren modifiziert) werden. Das Partner-Team stellt ISV-Partnern eine Sandbox-Umgebung zur Verfügung, in der sie ihren AEM-Connector in einem Basisprogramm bereitstellen können, um sicherzustellen, dass er funktioniert.
