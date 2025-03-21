---
title: Adobe Digital Asset Management (DAM) und AEM
description: Erfahren Sie, wie Sie Adobe Digital Asset Management (DAM) mit Experience Manager Assets as a Cloud Service verwenden und verwalten.
contentOwner: AK
feature: Asset Management
role: User, Leader, Architect
exl-id: 4437f214-d058-4975-8b8f-869a12c8103b
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '973'
ht-degree: 97%

---


# Assets as a [!DNL Cloud Service] für Digital Asset Management in AEM {#assets-cloud-service-introduction}

<!-- Need review information from gklebus -->

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime und Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>AEM Assets-Integration mit Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Erweiterbarkeit der Benutzeroberfläche</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Aktivieren von Dynamic Media Prime und Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Best Practices für die Suche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Best Practices für Metadaten</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Dynamic Media mit OpenAPI-Funktionen</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Entwicklerdokumentation zu AEM Assets</b></a>
        </td>
    </tr>
</table>

Adobe Experience Manager Assets as a [!DNL Cloud Service] bietet eine Cloud-native PaaS-Lösung für Unternehmen, mit der sie nicht nur ihre DAM- und Dynamic Media-Vorgänge schnell und effektiv durchführen können, sondern auch intelligente Funktionen der nächsten Generation wie künstliche Intelligenz und maschinelles Lernen nutzen können, und zwar innerhalb eines Systems, das immer aktuell, verfügbar und lernbereit ist.

Die gleichzeitige Erfassung vieler oder komplexer Assets ist eine ressourcenintensive Aufgabe für eine Experience Manager-Autoreninstanz. Die primäre Instanz beansprucht in erheblichem Umfang CPU-, Speicher- und E/A-Ressourcen, wenn Assets hinzugefügt, verarbeitet oder sogar migriert werden. Diese Leistungsprobleme wirken sich auf das Authoring- und Browsing-Erlebnis von Endbenutzern aus.

Unternehmen benötigen Unterstützung für eine Vielzahl von Dateiformaten und Inhaltsauflösungen für Anwendungen in geräte-, standort- und sprachübergreifende Anwendungsfällen. Die Verarbeitungs- und Speicheranforderungen von Assets erfordern Ressourcen und Funktionen, die herkömmliche Lösungen überfordern können. In einigen Fällen verhindern technische Beschränkungen bei der Asset-Verarbeitung, dass die gewünschten Ergebnissen erzielt werden. In anderen Fällen schmälern die Speicherkosten die Gewinnspanne.

Zunächst ist es wichtig, die [Vorteile von Cloud-nativen Lösungen](#solution-benefits) für Digital Asset Management zu verstehen. Werfen Sie einen genaueren Blick auf die wesentlichen [Änderungen an Experience Manager as a [!DNL Cloud Service]](/help/release-notes/aem-cloud-changes.md), die sich auch auf Experience Manager Assets auswirken, gefolgt von den wesentlichen [Änderungen an Assets](/help/assets/assets-cloud-changes.md).

Machen Sie sich außerdem mit den [Details der neuen Assets-Funktionen](#whats-new-assets) und [bekannten Problemen](/help/release-notes/maintenance/latest.md) vertraut. Der Liste [veralteter oder entfernter Funktionen](/help/release-notes/deprecated-removed-features.md) können Sie entnehmen, was mit dieser Version entfernt wird. Und schließlich finden Sie in diesem [Glossar](/help/overview/terminology.md) Erläuterungen zu Experience Manager-Begriffen.

## Vorteile der Lösung {#solution-benefits}

Im Folgenden werden die wichtigsten Vorteile von Assets as a [!DNL Cloud Service] für Digital Asset Management beschrieben. Weitere Informationen finden Sie in der [Übersicht über Adobe Experience Manager as a [!DNL Cloud Service]](/help/overview/introduction.md).

* **Moderne Cloud-Services für die Asset-Verarbeitung**: Die neuen Asset-Microservices sind ein Cloud-basierter, skalierbarer, zuverlässiger und unkomplizierter Service zur Asset-Verarbeitung.
* **Hohe Skalierbarkeit**: Flexible Skalierbarkeit bei unterschiedlichsten Bereitstellungen. Nahezu unbegrenzte Ressourcen, die bei Bedarf zur Verfügung stehen, soweit und sobald diese benötigt werden. Spart Kosten für überflüssiges Design, die bei herkömmlichen Systemen anfallen können.
* **Neueste Software**: Immer auf dem neuesten Stand und immer aktualisiert. Allen Benutzern wird ausschließlich die neueste Software mit allen Patches, Features, Sicherheitsfunktionen und Fehlerbehebungen zur Verfügung gestellt. Entwickler und Integratoren verwenden die neuesten APIs, sodass Probleme im Zusammenhang mit der Unterstützung mehrerer Versionen vermieden werden.
* **Immer online**: Keine Ausfallzeiten (0 DT), da die Instanz in einem Cluster mit Backups und Redundanz bereitgestellt wird. Auch Upgrades erfolgen ohne Ausfallzeiten.
* **Durchgehende Überwachung**: Die Überwachung des Systems ist automatisiert. Integrierte Prüfungen und Trigger tragen zudem dazu bei, die Leistung, Verfügbarkeit und allgemeine Stabilität sicherzustellen.
* **Unkomplizierte Bereitstellungen**: Vorgänge in Cloud-basierten Experience Manager-Versionen sind komplett automatisiert und erfordern keine Benutzerinteraktionen. Für automatisierte Bereitstellungen automatisiert die Komponente „Cloud Manager“ (CM) die Erstellung bereitstellbarer Docker-Images, die Ihren spezifischen Code enthalten.

## Verfügbare Persona-basierte Erlebnisse für Digital Asset Management {#persona-based-experiences}

Adobe bietet stabile DAM-Lösungen (Digital Asset Management), mit denen Sie Ihre digitalen Assets optimal nutzen können. Adobe Experience Manager Assets verfügt über zwei separate Erlebnisse, die dasselbe Cloud Services-Repository verwenden:

* **Admin-Ansicht**: Die bestehende Assets as a Cloud Service-Benutzeroberfläche. Verwenden Sie die Admin-Ansicht für alle erweiterten Digital Asset Management-Funktionen, einschließlich Integrationen, Workflows, Inhaltsautomatisierung, Veröffentlichung usw.

* **Assets-Ansicht**: Das einfache Asset-Management-Erlebnis von Adobe zum Speichern, Verwalten, Entdecken und Verwenden digitaler Assets. Es handelt sich um eine optimierte Benutzeroberfläche mit den wesentlichen Digital Asset Management-Funktionen. Entwickelt für Benutzerinnen und Benutzer eines einfachen DAM mit Schwerpunkt auf Upload, Metadatenverwaltung, Suche, Download und Freigabe.

Benutzerinnen und Benutzer mit Zugriff auf die Admin-Ansicht können auch auf die Asset-Ansicht zugreifen. Die vereinfachte Benutzeroberfläche der Assets-Ansicht erleichtert das Verwalten, Erkennen und Verteilen digitaler Assets. Ein breites Spektrum von Benutzerinnen und Benutzern aus verschiedenen Funktionen, einschließlich Kreativ-, Marketing- und Branchen-Teams, kann an Assets zusammenarbeiten und auf die richtigen, genehmigten Assets zugreifen, wo und wann immer sie benötigt werden. Viele gelegentliche DAM-Benutzerinnen und -Benutzer bevorzugen die Asset-Ansicht, da sie nur eine Teilmenge der Funktionen enthält. Das Erlebnis richtet sich an Kreative, Nutzerinnen und Nutzer von schreibgeschützten Assets und einfache DAM-Benutzerinnen und -Benutzer.

DAM-Bibliothekarinnen und -Bibliothekare, -Entwicklungspersonen sowie -Superbenutzerinnen und -Superbenutzer können die Admin-Ansicht weiterhin verwenden oder bei Bedarf zwischen den Benutzeroberflächen wechseln. Sie können das Erlebnis auswählen, das für Ihre Rolle am besten geeignet ist.

![add-tags](assets/newui-overview.svg)

Informationen zum Zugriff auf die Assets-Ansicht und einige der Vereinfachungen, die sie gegenüber der Admin-Ansicht bietet, finden Sie unter [Einführung in die Assets-Ansicht](/help/assets/assets-view-introduction.md).

## Integration in das dokumentbasierte Authoring für Edge Delivery Services {#integrate-doc-authoring-edge-and-assets}

Mit der Edge-Bereitstellung können Sie schnelle und ansprechende Websites erstellen, auf denen Autorinnen und Autoren Inhalte schnell aktualisieren und veröffentlichen können und neue Sites schnell gestartet werden können.

Integrieren Sie AEM Assets in das dokumentbasierte Authoring für Edge Delivery Services, damit Website-Autorinnen und -Autoren in AEM Assets-Repositorys verfügbare Bilder beim Erstellen von Dokumenten in Microsoft Word oder Google Docs verwenden können. Weitere Informationen finden Sie unter [Integrieren von AEM Assets mit dokumentbasiertem Authoring](/help/edge/using.md#integrate-assets-edge).

## Integration mit Adobe Journey Optimizer {#integration-with-ajo}

[Adobe Journey Optimizer](https://business.adobe.com/de/products/journey-optimizer/adobe-journey-optimizer.html) vereinfacht das Journey-Management für Kundinnen und Kunden und stellt Omni-Channel-Kampagnen mit intelligenter Entscheidungsfindung und Erkenntnissen bereit. Bei der Erstellung von Nachrichten mit Journey Optimizer können Sie direkt über die Journey Optimizer-Benutzeroberfläche auf Assets als ein Cloud-Service-Repository zugreifen. Benutzende erhalten den Zugriff auf Assets über die eingebettete Benutzeroberfläche von Experience Manager Assets. Weitere Informationen finden Sie unter [Erstellen und Verwalten von Assets mit Experience Manager Assets](https://experienceleague.adobe.com/docs/journey-optimizer/using/content-management/assets-images/assets.html?lang=de).

## Neue Assets-Funktionen {#whats-new-assets}

Die wichtigsten neuen Funktionen:

* [Asset-Microservices](/help/assets/asset-microservices-overview.md)
* [Asset-Upload-Methoden](/help/assets/add-assets.md)

**Siehe auch**

* [Assets übersetzen](translate-assets.md)
* [Assets-HTTP-API](mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](file-format-support.md)
* [Suchen von Assets](search-assets.md)
* [Connected Assets](use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](asset-reports.md)
* [Metadatenschemata](metadata-schemas.md)
* [Herunterladen von Assets](download-assets-from-aem.md)
* [Verwalten von Metadaten](manage-metadata.md)
* [Suchfacetten](search-facets.md)
* [Verwalten von Sammlungen](manage-collections.md)
* [Massenimport von Metadaten](metadata-import-export.md)
* [Veröffentlichen von Assets in AEM und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
