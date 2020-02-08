---
title: Implementieren eines AEM Connector
description: Implementieren eines AEM Connector
translation-type: tm+mt
source-git-commit: 629de3a9f55d2e4c52ef91c9e0bb5d439aebe84f

---


Implementieren eines AEM Connector
=============================

Im Folgenden finden Sie nützliche Hinweise zum Erstellen von [AEM Connectors](https://www.adobe.io/apis/experiencecloud/aem/aemconnectors.html) . Sie sollten zusammen mit Anleitungen zum [Senden](submit.md) und [Warten](maintain.md) von Connectors gelesen werden.

Beachten Sie, dass eine Entwicklerlizenz für AEM über das [Adobe Exchange-Programm](https://marketing.adobe.com/resources/content/resources/exchange-partner-program.html)erhältlich ist.

Gemeinsame Integrationsmuster
---------------------------

AEM ist eine topaktuelle Web Experience Management-Lösung und bietet viele potenzielle Integrationsbereiche. Häufige Integrationsmuster umfassen:

* Abruf von Daten von einem externen System in AEM. Exportieren Sie beispielsweise Kontaktinformationen aus einem CRM-System, um sie einer breiteren Zielgruppe beim Besuch einer AEM-basierten Website zur Verfügung zu stellen.  Implementierungen sollten die [geplanten Aufträge](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#scheduled-jobs)von Sling verwenden, die garantieren, dass der Auftrag auch dann ausgeführt wird, wenn die Container ausfallen. Code sollte so konzipiert sein, dass davon ausgegangen werden kann, dass der Auftrag möglicherweise mehrmals ausgelöst werden kann.
* Exportieren von Daten aus AEM in ein externes System. Beispielsweise Einstellungen für das Newsletter-Abonnement, die auf einer AEM-basierten Website an ein CRM-System gesendet werden.
* Abrufen von Assets aus AEM Beispiel: Ein externes Content Management System (CMS), das auf ein in AEM Assets gespeichertes Asset verweist. Oder ein anderes Beispiel: Ein PIM-System, das mit einem Bild in AEM Assets verknüpft ist.
* Speichern von Assets in der AEM-Infrastruktur Beispiel: Ein Marketing Resource Management (MRM)-System, das ein genehmigtes Asset in AEM Assets speichert.
* Konfigurieren und Rendern einer benutzerdefinierten UI-Komponente. Beispielsweise können Sie einem Autor gestatten, eine Videokomponente per Drag &amp; Drop zu verschieben und ein bestimmtes Video für die Wiedergabe auf der Live-Site zu konfigurieren.
* Aktionen für ein Asset mit einem Partnerdienst. Senden eines Assets an eine Videoplattform, wenn eine Seite veröffentlicht wird.
* Analysieren einer Site, Seite oder eines Assets in der AEM-Admin-Konsole. So können Sie beispielsweise SEO-Empfehlungen für eine vorhandene oder unveröffentlichte Seite abgeben.
* Zugriff auf Benutzerdaten auf Seitenebene, die von einem externen Dienst verwaltet werden. Sie können beispielsweise demografische Informationen nutzen, um das Site-Erlebnis zu personalisieren. Lesen Sie mehr über ContextHub, ein Framework zum Speichern, Manipulieren und Präsentieren von Kontextdaten.
* Übersetzung von Site-Kopien oder Asset-Metadaten. Im Bootstrap Connector[ für das ](https://github.com/Adobe-Marketing-Cloud/aem-translation-framework-bootstrap-connector)AEM Translation Framework finden Sie Beispielcode mit dem AEM Translation Framework, bei dem es sich um die bevorzugte Implementierung von Übersetzungsschnittstellen handelt.


Nützliche Dokumentation
--------------------

Die [Dokumentation](../overview/introduction.md) zu Experience Manager als Cloud-Dienst bietet wertvolle Einblicke in die Entwicklung in AEM. Im Folgenden finden Sie einige spezifische technische Themen und Referenzen, die Sie bei der Implementierung eines AEM-Connectors für nützlich halten können:

* Adobe Consulting Services (ACS) [AEM-Beispiele](http://adobe-consulting-services.github.io/acs-aem-samples/) für gut kommentierten Code zur Unterstützung von AEM-Entwicklern
* Die verschiedenen Dokumentationslinks im Abschnitt &quot;Gemeinsame Integrationsmuster&quot;in diesem Artikel

Community-Ressourcen
--------------------

Zusätzlich zur oben stehenden statischen Dokumentation bieten Adobe und die AEM-Community Ressourcen an, um einen Connector auf den Markt zu bringen:

* Das [AEM-Forum](http://help-forums.adobe.com/content/adobeforums/en/experience-manager-forum/adobe-experience-manager.html) der Adobe Community ist eine aktive Website, auf der Ihre Kollegen Fragen stellen und beantworten
* Für bestimmte Partnerstufen stehen zusätzliche technische Ressourcen von Adobe zur Verfügung. Erfahren Sie mehr über das [Adobe Exchange-Programm](https://marketing.adobe.com/resources/content/resources/exchange-partner-program.html).
* Wenn Ihr Unternehmen Hilfe bei der Implementierung benötigen möchte, wenden Sie sich an das Adobe [Professional Services](http://www.adobe.com/marketing-cloud/service-support/professional-consulting-training.html) -Team oder besuchen Sie den [Solution Partner Finder](https://solutionpartners.adobe.com/home/partnerFinder.html) , um eine Liste der Adobe-Partner weltweit anzuzeigen.

Paketstrukturregeln
-----------------------

Um rollierende Implementierungen zu unterstützen, haben AEM als Cloud-Service-Pakete, von denen Connectors Beispiele sind, eine strikte Trennung zwischen &quot;unveränderlichem&quot;und &quot;veränderlichem&quot;Inhalt. Pakete sollten sauber zwischen den Paketen unterschieden werden, die Folgendes umfassen:

* `/apps`
* `/content` und `/conf`

Connectors sollten sich an die in [diesem Artikel](/help/implementing/developing/introduction/aem-project-content-package-structure.md)beschriebenen Verpackungsrichtlinien halten. Bestehende Stecker sollten ebenfalls entsprechend umgestaltet werden.

Darüber hinaus sollte nur Adobe Code schreiben, in `/libs`den Kunden und Partner schreiben `/apps`.

Bestehende Connectors müssen ggf. auch neu gestaltet werden, um Konfigurationen, die einmal platziert wurden, `/etc` in andere Ordner der obersten Ebene zu verschieben, z. B. `/conf`. Dies wird in der [AEM-Dokumentation](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/repository-restructuring.html)beschrieben.

Es wird empfohlen, den Großteil des Connector-Codes unter `/apps/connectors/<vendor>` zu platzieren, um eine saubere Repository-Struktur für Kunden mit mehreren Connectors zu fördern.

Cloud Service-Konfigurationen
-----------------------------

Ein Aspekt der Connector-Implementierung ist der Code, der die Konfiguration des Connectors unterstützt. Durch diesen Code wird eine Karte mit dem Namen des Connectors unter &quot;Extras&quot;> &quot;Vorgänge&quot;> &quot;Cloud-Dienste&quot;angezeigt. Beim Klicken wird ein Konfigurationsbrowser geöffnet, in dem der Kunde den übergeordneten Ordner für die Connector-Konfiguration auswählt. Der Code des Connectors sollte zu einem Formular mit allen zu konfigurierenden Eigenschaften führen und die Werte letztendlich in einem Konfigurationsordner unter `/conf`speichern. Dieser Ordner kann später auf der Registerkarte &quot;Eigenschaften&quot;der Sites oder auf der Registerkarte &quot;Eigenschaften&quot;ausgewählt werden.


Kontextsensitive Konfigurationen
-----------------------------

[Die Context-Aware-Konfigurationen](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html) ermöglichen die Ebenenkonfiguration über verschiedene Ordner hinweg, einschließlich `/libs`, `/apps`und `/conf` Unterordner unter `/conf`. Es unterstützt Vererbung, sodass ein Kunde die globale Konfiguration konfigurieren und gleichzeitig spezifische Änderungen für jede Mikrosite vornehmen kann. Da diese Funktion für Cloud-Services-Konfigurationen genutzt werden kann, sollte der Connector-Code mithilfe der Context-Aware-Konfigurations-API auf die Konfiguration verweisen, anstatt auf einen bestimmten Konfigurationsknoten zu verweisen.

Wenn im Connector geänderte Konfigurationen verwendet werden, müssen Sie den Connector so konfigurieren, dass zukünftige Updates mit von Connector bereitgestellten Standardkonfigurationen mit beliebigen Kundenkonfigurationen verarbeitet und zusammengeführt werden. Denken Sie daran, dass eine Änderung von angepassten Inhalten oder Konfigurationen (wie sie vom Kunden geändert wurden) ohne Kundenwarnung und Zustimmung zu einem Ausfall (oder unerwartetem Verhalten) mit dem Connector führen kann.

Coding Best Practices
----------------------

Da AEM als Cloud-Dienst eine Cloud-native Lösung ist, gibt es einige Richtlinien, die die Codestrategien eines Connectors beeinflussen können. Weitere Informationen finden Sie unter [AEM als Richtlinien](/help/implementing/developing/introduction/development-guidelines.md) zur Entwicklung von Cloud-Diensten.

AEM Connector testen
-------------------------

Neue Connectors sollten mithilfe lokaler Entwicklungstechniken erstellt (oder vorhandene Connectors modifiziert) werden. Das Partnerteam stellt ISV-Partnern eine Sandbox-Umgebung zur Verfügung, in der sie ihren AEM Connector in einer Vanilleanwendung bereitstellen können, um sicherzustellen, dass diese funktioniert.
