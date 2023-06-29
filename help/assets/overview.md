---
title: Einführung in Assets as a [!DNL Cloud Service]
description: Neue Funktionen in Assets as a [!DNL Cloud Service].
contentOwner: AG
feature: Asset Management
role: User,Leader,Architect
exl-id: 4437f214-d058-4975-8b8f-869a12c8103b
source-git-commit: 5a7938d5e52388516f8b66bbcf8ffdee332a51a3
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 67%

---

# Neu: Assets as a [!DNL Cloud Service] {#assets-cloud-service-introduction}

<!-- Need review information from gklebus -->

Adobe Experience Manager Assets as a [!DNL Cloud Service] bietet eine Cloud-native PaaS-Lösung für Unternehmen, mit der sie nicht nur ihre DAM- und Dynamic Media-Vorgänge schnell und effektiv durchführen können, sondern auch intelligente Funktionen der nächsten Generation wie künstliche Intelligenz und maschinelles Lernen nutzen können, und zwar innerhalb eines Systems, das immer aktuell, verfügbar und lernbereit ist.

Die gleichzeitige Erfassung vieler oder komplexer Assets ist eine ressourcenintensive Aufgabe für eine Experience Manager-Autoreninstanz. Die primäre Instanz beansprucht in erheblichem Umfang CPU-, Speicher- und E/A-Ressourcen, wenn Assets hinzugefügt, verarbeitet oder sogar migriert werden. Diese Leistungsprobleme wirken sich auf das Authoring- und Browsing-Erlebnis von Endbenutzern aus.

Unternehmen benötigen Unterstützung für eine Vielzahl von Dateiformaten und Inhaltsauflösungen für Anwendungen in geräte-, standort- und sprachübergreifende Anwendungsfällen. Die Verarbeitungs- und Speicheranforderungen von Assets erfordern Ressourcen und Funktionen, die herkömmliche Lösungen überfordern können. In einigen Fällen verhindern technische Beschränkungen bei der Asset-Verarbeitung, dass die gewünschten Ergebnissen erzielt werden. In anderen Fällen schmälern die Speicherkosten die Gewinnspanne.

Zunächst ist es wichtig, die [Vorteile von Cloud-nativen Lösungen](#solution-benefits) zu verstehen. Werfen Sie einen genaueren Blick auf die wesentlichen [Änderungen an Experience Manager as a [!DNL Cloud Service]](/help/release-notes/aem-cloud-changes.md), die sich auch auf Experience Manager Assets auswirken, gefolgt von den wesentlichen [Änderungen an Assets](/help/assets/assets-cloud-changes.md).

Machen Sie sich außerdem mit den [Details der neuen Assets-Funktionen](#whats-new-assets) und [bekannten Problemen](/help/release-notes/maintenance/latest.md) vertraut. Der Liste [veralteter oder entfernter Funktionen](/help/release-notes/deprecated-removed-features.md) können Sie entnehmen, was mit dieser Version entfernt wird. Und schließlich finden Sie in diesem [Glossar](/help/overview/terminology.md) Erläuterungen zu Experience Manager-Begriffen.

## Vorteile der Lösung {#solution-benefits}

Im Folgenden werden die wichtigsten Vorteile von Assets as a [!DNL Cloud Service] beschrieben. Weitere Informationen finden Sie in der [Übersicht über Adobe Experience Manager as a [!DNL Cloud Service]](/help/overview/introduction.md).

* **Moderne Cloud-Services für die Asset-Verarbeitung**: Die neuen Asset-Microservices sind ein Cloud-basierter, skalierbarer, zuverlässiger und unkomplizierter Service zur Asset-Verarbeitung.
* **Hohe Skalierbarkeit**: Flexible Skalierbarkeit bei unterschiedlichsten Bereitstellungen. Nahezu unbegrenzte Ressourcen, die bei Bedarf zur Verfügung stehen, soweit und sobald diese benötigt werden. Spart Kosten für überflüssiges Design, die bei herkömmlichen Systemen anfallen können.
* **Neueste Software**: Immer auf dem neuesten Stand und immer aktualisiert. Allen Benutzern wird ausschließlich die neueste Software mit allen Patches, Features, Sicherheitsfunktionen und Fehlerbehebungen zur Verfügung gestellt. Entwickler und Integratoren verwenden die neuesten APIs, sodass Probleme im Zusammenhang mit der Unterstützung mehrerer Versionen vermieden werden.
* **Immer online**: Keine Ausfallzeiten (0 DT), da die Instanz in einem Cluster mit Backups und Redundanz bereitgestellt wird. Auch Upgrades erfolgen ohne Ausfallzeiten.
* **Durchgehende Überwachung**: Die Überwachung des Systems ist automatisiert. Integrierte Prüfungen und Trigger tragen zudem dazu bei, die Leistung, Verfügbarkeit und allgemeine Stabilität sicherzustellen.
* **Unkomplizierte Bereitstellungen**: Vorgänge in Cloud-basierten Experience Manager-Versionen sind komplett automatisiert und erfordern keine Benutzerinteraktionen. Für automatisierte Bereitstellungen automatisiert die Komponente „Cloud Manager“ (CM) die Erstellung bereitstellbarer Docker-Images, die Ihren spezifischen Code enthalten.

## Verfügbare personalbasierte Erlebnisse {#persona-based-experiences}

Adobe bietet stabile DAM-Lösungen (Digital Asset Management), mit denen Sie Ihre digitalen Assets optimal nutzen können. Adobe Experience Manager Assets verfügt über zwei separate Erlebnisse, die dasselbe Cloud Services-Repository verwenden:

* **Admin-Ansicht**: Die bestehende as a Cloud Service Benutzeroberfläche von Assets. Verwenden Sie die Admin-Ansicht für alle erweiterten Asset-Management-Funktionen, einschließlich Integrationen, Workflows, Inhaltsautomatisierung, Veröffentlichung und mehr.

* **Asset-Ansicht**: Das einfache Asset-Management-Erlebnis von Adobe zum Speichern, Verwalten, Entdecken und Verwenden digitaler Assets. Optimierte Benutzeroberfläche mit wesentlichen Asset-Management-Funktionen. Entwickelt für kleine DAM-Benutzer mit Schwerpunkt auf Upload, Metadatenverwaltung, Suche, Download und Freigabe.

Benutzer mit Zugriff auf die Admin-Ansicht können auch auf die Asset-Ansicht zugreifen. Die Asset-Ansicht bietet eine vereinfachte Benutzeroberfläche, die die Verwaltung, Erkennung und Verteilung digitaler Assets erleichtert. Ein breites Spektrum von Benutzern aus verschiedenen Funktionen, einschließlich Kreativen, Marketing- und Geschäftsfeldern, kann an Assets zusammenarbeiten und auf die richtigen, genehmigten Assets zugreifen, wann und wo sie benötigt werden. Viele gelegentliche DAM-Benutzer bevorzugen die Asset-Ansicht, da sie nur eine Untergruppe von Funktionen enthält. Das Erlebnis richtet sich an Kreative, schreibgeschützte Asset-Verbraucher und einfache DAM-Benutzer.

DAM-Bibliothekare, -Entwickler und -Superbenutzer können die Admin-Ansicht weiterhin verwenden oder bei Bedarf zwischen den Benutzeroberflächen wechseln. Sie können das Erlebnis auswählen, das für Ihre Rolle am besten geeignet ist.

![add-tags](assets/newui-overview.svg)

Informationen zum Zugriff auf die Asset-Ansicht und einige der Vereinfachungen, die sie über die Admin-Ansicht bietet, finden Sie unter [Einführung in die Asset-Ansicht](/help/assets/assets-view-introduction.md).

## Neue Assets-Funktionen {#whats-new-assets}

Die wichtigsten neuen Funktionen:

* [Asset-Microservices](/help/assets/asset-microservices-overview.md)
* [Asset-Upload-Methoden](/help/assets/add-assets.md)

**Siehe auch**

* [Assets übersetzen](translate-assets.md)
* [Assets-HTTP-API](mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](file-format-support.md)
* [Suchen von Assets](search-assets.md)
* [Verbundene Assets](use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](asset-reports.md)
* [Metadatenschemata](metadata-schemas.md)
* [Herunterladen von Assets](download-assets-from-aem.md)
* [Verwalten von Metadaten](manage-metadata.md)
* [Suchfacetten](search-facets.md)
* [Verwalten von Sammlungen](manage-collections.md)
* [Massenimport von Metadaten](metadata-import-export.md)
