---
title: Einführung in Assets as a [!DNL Cloud Service]
description: Neue Funktionen in Assets as a [!DNL Cloud Service].
contentOwner: AG
feature: Asset Management
role: Business Practitioner,Leader,Architect
translation-type: tm+mt
source-git-commit: 8093f6cec446223af58515fd8c91afa5940f9402
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 98%

---


# Neu: Assets as a [!DNL Cloud Service] {#assets-cloud-service-introduction}

<!-- Need review information from gklebus -->

Adobe Experience Manager Assets as a [!DNL Cloud Service] bietet eine Cloud-native PaaS-Lösung für Unternehmen, mit der sie nicht nur ihre Digital Asset Management- und Dynamic Media-Vorgänge schnell und effektiv durchführen können, sondern auch intelligente Funktionen der nächsten Generation wie künstliche Intelligenz und maschinelles Lernen nutzen können, und zwar innerhalb eines Systems, das immer aktuell, verfügbar und lernbereit ist.

Die gleichzeitige Erfassung vieler oder komplexer Assets ist eine ressourcenintensive Aufgabe für eine AEM-Autoreninstanz. Die primäre Instanz beansprucht in erheblichem Umfang CPU-, Speicher- und E/A-Ressourcen, wenn Assets hinzugefügt, verarbeitet oder sogar migriert werden. Diese Leistungsprobleme wirken sich auf das Authoring- und Browsing-Erlebnis von Endbenutzern aus.

Unternehmen benötigen Unterstützung für eine Vielzahl von Dateiformaten und Inhaltsauflösungen für Anwendungen in geräte-, standort- und sprachübergreifende Anwendungsfällen. Die Verarbeitungs- und Speicheranforderungen von Assets erfordern Ressourcen und Funktionen, die herkömmliche Lösungen überfordern können. In einigen Fällen verhindern technische Beschränkungen bei der Asset-Verarbeitung, dass die gewünschten Ergebnissen erzielt werden. In anderen Fällen schmälern die Speicherkosten die Gewinnspanne.

Zunächst ist es wichtig, die [Vorteile von Cloud-nativen Lösungen](#solution-benefits) zu verstehen. Werfen Sie einen genaueren Blick auf die wesentlichen [Änderungen an AEM as a [!DNL Cloud Service]](/help/release-notes/aem-cloud-changes.md), die sich auch auf Experience Manager Assets auswirken, gefolgt von den wesentlichen [Änderungen an Assets](/help/assets/assets-cloud-changes.md).

Machen Sie sich außerdem mit den [Details der neuen Assets-Funktionen](#whats-new-assets) und [bekannten Problemen](/help/release-notes/known-issues.md) vertraut. Sehen Sie sich eine Liste der [veralteten oder entfernten Funktionen](/help/release-notes/deprecated-removed-features.md) an, um zu erfahren, welche Funktionen in dieser Version nicht mehr enthalten sind. Sehen Sie sich außerdem eine [Liste der künftig verfügbaren Funktionen](/help/release-notes/known-issues.md#upcoming-assets-capabilities) an, um zu erfahren, welche Funktionen Ihnen demnächst zur Verfügung stehen. Darüber hinaus finden Sie in diesem [Glossar](/help/overview/terminology.md) Erläuterungen zu AEM-Begriffen.

## Vorteile der Lösung {#solution-benefits}

Im Folgenden werden die wichtigsten Vorteile von Assets as a [!DNL Cloud Service] beschrieben. Weitere Informationen finden Sie in der [Übersicht über Adobe Experience Manager as a [!DNL Cloud Service]](/help/overview/introduction.md).

* **Moderne Cloud-Services für die Asset-Verarbeitung**: Die neuen Asset-Microservices sind ein Cloud-basierter, skalierbarer, zuverlässiger und unkomplizierter Dienst zur Asset-Verarbeitung.
* **Hohe Skalierbarkeit**: Flexible Skalierbarkeit bei unterschiedlichsten Bereitstellungen. Nahezu unbegrenzte Ressourcen, die bei Bedarf zur Verfügung stehen, soweit und sobald diese benötigt werden. Spart Kosten für überflüssiges Design, die bei herkömmlichen Systemen anfallen können.
* **Neueste Software**: Immer auf dem neuesten Stand und immer aktualisiert. Allen Benutzern wird ausschließlich die neueste Software mit allen Patches, Features, Sicherheitsfunktionen und Fehlerbehebungen zur Verfügung gestellt. Entwickler und Integratoren verwenden die neuesten APIs, sodass Probleme im Zusammenhang mit der Unterstützung mehrerer Versionen vermieden werden.
* **Immer online**: Keine Ausfallzeiten (0 DT), da die Instanz in einem Cluster mit Backups und Redundanz bereitgestellt wird. Auch Upgrades erfolgen ohne Ausfallzeiten.
* **Durchgehende Überwachung**: Die Überwachung des Systems ist automatisiert. Integrierte Prüfungen und Trigger tragen zudem dazu bei, die Leistung, Verfügbarkeit und allgemeine Stabilität sicherzustellen.
* **Unkomplizierte Bereitstellungen**: Vorgänge in Cloud-basierten AEM-Versionen sind umfassend automatisiert und erfordern keine Benutzerinteraktionen. Für automatisierte Bereitstellungen automatisiert die Komponente „Cloud Manager“ (CM) die Erstellung bereitstellbarer Docker-Images, die Ihren spezifischen Code enthalten.

## Neue Assets-Funktionen {#whats-new-assets}

Die wichtigsten neuen Funktionen:

* [Asset-Microservices](/help/assets/asset-microservices-overview.md)
* [Asset-Upload-Methoden](/help/assets/add-assets.md)
