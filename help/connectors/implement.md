---
title: Implementieren von AEM-Connectoren
description: Erfahren Sie mehr über Connectoren und darüber, was sie tun können und wie Sie diese wertvollen Tools in Experience Manager implementieren können.
exl-id: 70024424-8c52-493e-bbc9-03d238b8a5f5
feature: Operations
role: Admin
source-git-commit: a9cec66cf518a19a5a6152d431a052369b5b503a
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 74%

---


Implementieren von AEM-Connectoren
=============================

Im Folgenden finden Sie nützliche Hinweise zum Erstellen von AEM Connectors. Sie sollten mit Anleitungen zu den Connectoren [Senden](submit.md) und [Warten](maintain.md) gelesen werden.

Eine Entwicklerlizenz für AEM kann über das [Adobe Exchange-Programm](https://partners.adobe.com/technologyprogram/experiencecloud.html) erworben werden.

Gängige Integrationsmuster
---------------------------

AEM ist eine hochmoderne Web-Experience-Management-Lösung und bietet viele potenzielle Integrationsbereiche. Zu den gängigen Integrationsmustern gehören:

* Abruf von Daten von einem externen System in AEM. Exportieren Sie beispielsweise Kontaktinformationen aus einem CRM-System, um sie einer breiteren Zielgruppe beim Besuch einer AEM-basierten Website zur Verfügung zu stellen.  Implementierungen sollten die [geplanten Aufträge](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#scheduled-jobs) von Sling verwenden, die garantieren, dass der Auftrag auch dann ausgeführt wird, wenn die Container ausfallen. Code sollte so konzipiert sein, dass der Auftrag möglicherweise mehrmals ausgelöst werden kann.
* Exportieren von Daten aus AEM in ein externes System. Beispielsweise werden Newsletter-Abonnementeinstellungen auf einer AEM-basierten Website an ein CRM-System gesendet.
* Abrufen von Assets aus AEM. Beispielsweise ein externes Content Management System (CMS), das auf ein in AEM Assets gespeichertes Asset verweist. Oder ein PIM-System, das mit einem Bild in AEM Assets verknüpft ist.
* Speichern von Assets in der AEM-Infrastruktur. Zum Beispiel ein Marketing-Ressourcen-Management (MRM)-System, das ein genehmigtes Asset in AEM Assets speichert.
* Konfigurieren und Rendern einer benutzerdefinierten Komponente der Benutzeroberfläche. Beispielsweise können Sie einem Autor gestatten, eine Videokomponente per Drag-and-Drop zu verschieben und ein bestimmtes Video für die Wiedergabe auf der Live-Site zu konfigurieren.
* Aktionen für ein Asset mit einem Partner-Service. Senden eines Assets an eine Videoplattform, wenn eine Seite veröffentlicht wird.
* Analysieren einer Site, Seite oder eines Assets in der AEM Admin Console. So können Sie beispielsweise SEO-Empfehlungen für eine vorhandene oder unveröffentlichte Seite abgeben.
* Zugriff auf Benutzerdaten auf Seitenebene, die von einem externen Service verwaltet werden. Sie können beispielsweise demografische Informationen nutzen, um das Site-Erlebnis zu personalisieren. Lesen Sie mehr über ContextHub, ein Framework zum Speichern, Bearbeiten und Präsentieren von Kontextdaten.
* Übersetzung von Site-Kopien oder Asset-Metadaten. Im [AEM Translation Framework Bootstrap Connector](https://github.com/Adobe-Marketing-Cloud/aem-translation-framework-bootstrap-connector) finden Sie Beispiel-Code für das AEM Translation Framework, das die bevorzugte Implementierung von Übersetzungs-Connectoren ist.


Hilfreiche Dokumentationen
--------------------

Die [Dokumentation](../overview/introduction.md) zu Experience Manager as a Cloud Service bietet wertvolle Einblicke in die Entwicklung in AEM. Im Folgenden finden Sie einige spezifische technische Themen und Referenzen, die bei der Implementierung eines AEM-Connectors möglicherweise nützlich sein können:

* [AEM-Beispiele](https://adobe-consulting-services.github.io/acs-aem-samples/) von Adobe Consulting Services (ACS) für gut kommentierten Code zur Schulung von AEM-Entwicklern
* Die verschiedenen Dokumentations-Links im Abschnitt „Gängige Integrationsmuster“ dieses Artikels

Community-Ressourcen
--------------------

Zusätzlich zur obenstehenden statischen Dokumentation bieten Adobe und die AEM-Community Ressourcen an, um einen Connector auf den Markt zu bringen:

* Das [AEM-Forum](https://help-forums.adobe.com/content/adobeforums/en/experience-manager-forum/adobe-experience-manager.html) der Adobe Community ist eine aktive Website, auf der Ihre Kollegen Fragen stellen und beantworten
* Für bestimmte Partnerstufen stehen zusätzliche technische Ressourcen von Adobe zur Verfügung. Weitere Informationen zum [Adobe Exchange-Programm](https://partners.adobe.com/technologyprogram/experiencecloud.html).
* Wenn Ihr Unternehmen Hilfe bei der Implementierung wünscht, wenden Sie sich an das [Professional Services](https://solutionpartners.adobe.com/s/directory)-Team von Adobe oder suchen Sie im [Solution Partner Finder](https://solutionpartners.adobe.com/s/directory/) eine Liste der Adobe-Partner auf der ganzen Welt

Regeln für die Paketstruktur
-----------------------

Um eine rollierende Bereitstellung zu erleichtern, halten AEM as a Cloud Service-Pakete - wie z. B. Connectoren - eine strikte Trennung zwischen &quot;unveränderlichen&quot;und &quot;veränderlichen&quot;Inhalten fest. Pakete sollten klar organisiert sein, um Folgendes zu umfassen:

* `/apps`
* `/content` und `/conf`

Connectoren sollten sich an die unter [Struktur von AEM-Projekten](/help/implementing/developing/introduction/aem-project-content-package-structure.md) beschriebenen Richtlinien zur Paketerstellung halten. Bestehende Connectoren sollten ebenfalls entsprechend umgestaltet werden.

Darüber hinaus sollte nur Adobe Code in `/libs` schreiben, während Kunden und Partner in `/apps` schreiben.

Bestehende Connectoren müssen möglicherweise auch umstrukturiert werden, um jede Konfiguration, die einmal in `/etc` platziert wurde, in andere Ordner der obersten Ebene, wie z. B. `/conf`, zu verschieben. Diese Umstrukturierung erfolgte im Rahmen von AEM 6.5 und wird in der [Dokumentation zu AEM 6.5](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/implementing/deploying/restructuring/repository-restructuring) beschrieben.

Adobe empfiehlt, den Großteil des Connector-Codes unter `/apps/connectors/<vendor>` zu platzieren, um eine saubere Repository-Struktur zu erhalten, insbesondere für Kunden, die mehrere Connectoren verwenden.

Cloud Services-Konfigurationen
-----------------------------

Ein Aspekt der Connector-Implementierung ist der Code, der die Konfiguration des Connectors unterstützt. Durch diesen Code wird eine Karte mit dem Namen des Connectors unter „Tools“ > „Vorgänge“ > „Cloud Services“ angezeigt. Beim Klicken wird ein [Konfigurations-Browser](/help/implementing/developing/introduction/configurations.md#using-configuration-browser) geöffnet, in dem der Kunde den übergeordneten Ordner für die Connector-Konfiguration auswählt. Der Code des Connectors sollte zu einem Formular mit allen zu konfigurierenden Eigenschaften führen und die Werte letztendlich in einem Konfigurationsordner unter `/conf` speichern. Dieser Ordner kann später auf der Registerkarte „Sites-Eigenschaften“ oder auf der Registerkarte „Asset-Eigenschaften“ ausgewählt werden.


Kontextabhängige Konfigurationen
-----------------------------

Mit [kontextbezogenen Konfigurationen](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html) können Sie die Ebenenkonfiguration über verschiedene Ordner hinweg festlegen, einschließlich `/libs`, `/apps`, `/conf` und Unterordnern unter `/conf`. Es wird die Vererbung unterstützt, sodass ein Kunde eine globale Konfiguration festlegen und gleichzeitig spezifische Änderungen für jede Microsite vornehmen kann. Da diese Funktion für Cloud Service-Konfigurationen verwendet werden kann, sollte der Connector-Code mithilfe der kontextsensitiven Konfigurations-API auf die Konfiguration verweisen, anstatt auf einen bestimmten Konfigurationsknoten zu verweisen.

Wenn im Connector geänderte Konfigurationen verwendet werden, können Sie den Connector so gestalten, dass zukünftige Aktualisierungen der vom Connector bereitgestellten Standardkonfigurationen mit Kundenkonfigurationen integriert/zusammengeführt werden. Beachten Sie, dass eine Änderung von kundenspezifischen Inhalten oder Konfigurationen ohne vorherige Ankündigung und Zustimmung zu unerwartetem Verhalten in ihrem Connector führen oder stören kann.

Best Practices für die Kodierung
----------------------

Da AEM as a Cloud Service eine Cloud-native Lösung ist, gibt es einige Richtlinien, die sich auf die Code-Strategien eines Connectors auswirken können. Weitere Informationen finden Sie unter [Entwicklungsrichtlinien für AEM as a Cloud Service](/help/implementing/developing/introduction/development-guidelines.md).

Testen von AEM-Connectoren
-------------------------

Neue Connectoren sollten mithilfe lokaler Entwicklungstechniken erstellt (oder vorhandene Connectoren modifiziert) werden. Das Partner-Team stellt ISV-Partnern eine Sandbox-Umgebung zur Verfügung, in der sie ihren AEM Connector in einer Vanilla-Anwendung bereitstellen können, um sicherzustellen, dass er funktioniert.
