---
title: Verbinden von AEM Forms mit Adobe Experience Platform (AEP) | Handbuch zur Datenintegration
description: Erfahren Sie, wie Sie AEM Forms mit Adobe Experience Platform integrieren können, um Kundenprofile zu nutzen, Formulardaten zu übermitteln und personalisierte Erlebnisse zu erstellen. Schrittweise Anleitung.
contentOwner: Khushwant Singh
docset: CloudService
role: Admin, Developer, User
feature: Adaptive Forms, Core Components
exl-id: b0eb19d3-0297-4583-8471-edbb7257ded4
source-git-commit: bc422429d4a57bbbf89b7af2283b537a1f516ab5
workflow-type: tm+mt
source-wordcount: '2047'
ht-degree: 2%

---

# Integration von AEM Forms mit Adobe Experience Platform (AEP) {#aem-forms-aep-integration}

<span class="preview"> Die Funktion zum Verbinden von Adaptive Forms (AEM Forms) mit Adobe Experience Platform (AEP) wird derzeit im Rahmen des EARLY ACCESS-Programms unterstützt. Um Zugriff auf die Funktion anzufordern, senden Sie einfach eine E-Mail von Ihrer offiziellen Adresse an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com?subject=Request%20for%20Early%20Access%20to%20AEP%20Connector%20\(AEM%20Forms%20Integration%20with%20Adobe%20Experience%20Platform\)&body=Dear%20AEM%20Forms%20Team%2C%0D%0A%0D%0AI%20hope%20this%20message%20finds%20you%20well.%0D%0A%0D%0AI%20am%20writing%20to%20request%20access%20to%20the%20Early%20Access%20Program%20for%20the%20AEP%20Connector%2C%20which%20enables%20integration%20between%20AEM%20Forms%20and%20Adobe%20Experience%20Platform.%0D%0A%0D%0AOrganization%20Name%3A%20%5BYour%20organization%20name%5D%0D%0AOrganization%20ID%3A%20%5BYour%20organization%20ID%2C%20if%20available%5D%0D%0AUse%20Case%3A%20%5BBriefly%20describe%20your%20intended%20use%20case%2C%20including%20goals%20or%20benefits%20you%20aim%20to%20achieve%20with%20the%20integration%5D%0D%0A%0D%0AThank%20you%20for%20your%20time%20and%20consideration.%0D%0A%0D%0ABest%20regards%2C%0D%0A%5BYour%20Full%20Name%5D%0D%0A%5BYour%20Job%20Title%2C%20if%20applicable%5D%0D%0A%5BYour%20Contact%20Information%2C%20if%20appropriate%5D). Besuchen Sie auch die Seite <a href="/help/forms/early-access-ea-features.md">Early Access Program</a>, um alle verfügbaren Innovationen und Funktionen zu entdecken. </span>

## Überblick {#overview}

Sie können AEM Forms mit Adobe Experience Platform verbinden, um Ihre Formularerlebnisse zu transformieren. Diese leistungsstarke Integration ermöglicht es Unternehmen, Echtzeit-Kundenprofile für personalisierte Formularerlebnisse zu nutzen, die **AEM Forms-Datenübermittlung an Experience Platform** zu optimieren und einheitliche Kundendatensätze im gesamten Adobe-Ökosystem zu erstellen. Durch die Verbindung Ihrer adaptiven Formulare mit den robusten Datenverwaltungsfunktionen von Experience Platform können Sie relevantere Erlebnisse erstellen und die Konversionsraten verbessern, während Sie eine einzige Datenquelle für Kundendaten beibehalten.

### Was ist AEM Forms Connector für Adobe Experience Platform (AEP)? {#what-is-connector}

Der AEM Forms-Connector für Adobe Experience Platform (AEP) ist ein von AEM Forms bereitgestellter vorkonfigurierter Connector, der eine nahtlose Integration zwischen AEM Forms und Adobe Experience Platform (AEP) ermöglicht. Bei dieser Integration können Sie Formulare mit XDM-Schemata erstellen, die in AEP verfügbar sind, und Daten zu Personalisierungs- und Profilhydratationszwecken zurück an AEP senden.

## Warum sollte man AEM Forms mit Adobe Experience Platform (AEP) verbinden? {#benefits}

Die Verbindung Ihres adaptiven Forms mit Adobe Experience Platform bietet sowohl für Ihr Unternehmen als auch für Ihre Kunden erhebliche Vorteile:

* **Einheitliche Kundenprofile** - Anreicherung von Kundenprofilen mit Formularübermittlungsdaten, um eine umfassende Ansicht von Kundeninteraktionen und -präferenzen zu erhalten
* **Personalisierte Formularerlebnisse** - Nutzen Sie vorhandene Profildaten, um Felder vorauszufüllen und Formulare basierend auf bekannten Kundeninformationen anzupassen
* **Optimierte Datenerfassung** - Direkte Erfassung von Formulardaten in AEP-Datensätzen ohne Erstellung benutzerdefinierter Connectoren oder Integrations-Code
* **Echtzeit-Datenaktivierung** - Senden von Formularübermittlungsdaten über Real-Time CDP zur sofortigen Aktivierung an andere Adobe-Programme
* **Vereinfachtes Compliance-Management** - Einverständnis- und Data Governance-Richtlinien zentral über AEP verwalten
* **Verkürzte Entwicklungszeit** - Keine benutzerdefinierten Integrationsaufgaben mit einem vorkonfigurierten Connector, der Best Practices folgt
* **Anreicherung von Kundenprofilen mit Formulardaten** - Automatisches Aktualisieren und Erweitern von Kundenprofilen mit jeder Formularübermittlung, wodurch umfassendere Kundeneinblicke geschaffen werden

## Wichtigste Funktionen {#key-features}

* Erstellen von Formularen mit AEP-XDM-Schemata
* Senden von Formulardaten zur Personalisierung an AEP
* Unterstützung für die Streaming-Datenaufnahme
* Aktivieren der Profilhydrierung für erweiterte Benutzererlebnisse
* Integration mit dem Profilsystem von AEP
* Integration von XDM-Schemata mit adaptiven Formularen für eine standardisierte Datenerfassung
* AEP-Streaming-Verbindung für Formulare, die Echtzeit-Datenverarbeitung ermöglicht

Das folgende Video enthält eine schrittweise Anleitung zu den Voraussetzungen (wie Erstellen eines Schemas, Einrichten der Datenkonfiguration und Authentifizierung) und zeigt, wie Sie Adaptive Forms erstellen und mit Adobe Experience Platform (AEP) verbinden

>[!VIDEO](https://video.tv.adobe.com/v/3457850/)

<span> Dieses Video gilt nur für Kernkomponenten. Informationen zu UE/Foundation-Komponenten finden Sie im Artikel</span>

## Voraussetzungen {#prerequisites}

Bevor Sie den AEP-Connector in AEM Forms einrichten, stellen Sie sicher, dass Sie Folgendes in Adobe Experience Platform abgeschlossen haben:

1. Schema-Setup
   * [Erstellen eines XDM-Schemas](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/create-schema-ui)
   * [Aktivieren eines Schemas für die Profilerstellung](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/create-schema-ui#profile)
   * [Identitätsfeld definieren](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/create-schema-ui#profile)

2. Datenkonfiguration
   * [Erstellen eines Datensatzes](https://experienceleague.adobe.com/en/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/create-datasets)
   * [Streaming-Verbindung einrichten](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/tutorials/create-streaming-connection) (Sie benötigen die Streaming-Endpunkt-URL später. Notieren Sie sich diese also jetzt.)

3. Authentifizierung
   * [Generieren von API-](https://experienceleague.adobe.com/en/docs/experience-platform/landing/platform-apis/api-authentication#generate-credentials) (Client-ID und Client-Geheimnis) aus Adobe Developer Console


## Implementierungsschritte

### &#x200B;1. Erstellen der AEP-Cloud-Konfiguration

1. Navigieren Sie zu Ihrer **Adobe Experience Manager** > **Tools** > **Cloud Services** > **Adobe Experience Platform**.
1. Wählen Sie einen **Konfigurations-Container** aus, um die Konfiguration zu speichern.
1. Klicken Sie **Erstellen**, um den AEP-Konfigurationsassistenten zu öffnen
1. Geben Sie die folgenden Details ein:
   * Titel
   * Client-ID (bezogen von der Entwicklerkonsole)
   * Client-Geheimnis (bezogen von der Entwicklerkonsole)
   * OAuth-URL (Es gibt eine Standard-URL, sie kann jedoch auch über die Entwicklerkonsole bezogen werden)

   ![AEP-Cloud-Konfiguration](/help/forms/assets/aep-cloud-configuration.png)

1. Klicken Sie auf **Verbinden**, um die Verbindung herzustellen. Konfigurieren Sie nach dem Verbindungsaufbau die folgenden zusätzlichen Einstellungen:
   * Basis-URL: platform.adobe.io (Dies ist eine Standard-URL, die über die Entwicklerkonsole abgerufen werden kann. Die OAuth- und Platform-URLs werden standardmäßig auf Produktions-URLs festgelegt. In diesem Fall müssen Sie eine Verbindung zum Staging herstellen. Staging-URLs sollten verwendet werden.)
   * Organisations-ID (wird zusammen mit der Client-ID/dem Client-Geheimnis von der Entwicklerkonsole abgerufen)
   * Sandbox-Name (erforderlich für Entwicklungs- und Produktionsumgebungen)

### &#x200B;2. Formularerstellung mit XDM-Schemaintegration {#form-creation}

>[!BEGINTABS]

>[!TAB Foundation-Komponente]

Führen Sie die folgenden Schritte aus, um ein adaptives Formular basierend auf Foundation-Komponenten mit Schemaintegration zu erstellen:

1. Zugriff auf den Assistenten zur Formularerstellung:
   * Navigieren Sie zu Ihrer **Adobe Experience Manager** > **Forms** > **Forms und Dokumente**.
   * Klicken Sie **Erstellen** > **Adaptives Formular**.
1. Wählen Sie auf **Registerkarte** eine Foundation-Vorlage aus.
1. Wählen Sie auf **Registerkarte** die Option **Adobe Experience Platform** aus.
1. Wählen Sie im Eigenschaftenbereich Ihre Cloud-Konfiguration aus.

   ![](/help/forms/assets/xdm-schema-integration.png)

   Das System lädt alle verfügbaren Schemata aus Adobe Experience Platform

   >[!NOTE]
   >
   >
   > * Es werden nur profilaktivierte und nicht systemgenerierte Schemas abgerufen.
   > * Das erste Laden des Schemas kann bei der erstmaligen Einrichtung einige Zeit in Anspruch nehmen.

1. Auswahl der entsprechenden/erforderlichen Felder des Schemas. (Siehe Video mit detaillierten Schritten)
1. Auf der Registerkarte Übermittlung :
   * Wählen Sie die **An Adobe Experience Platform übermitteln** Übermittlungsaktion
   * Konfigurieren Sie die Einstellungen für die Formularübermittlung für die **AEM Forms-Datenübermittlung an Experience Platform**
1. Im Bereich Eigenschaften :
   * Fügen Sie die Streaming-URL hinzu (bezogen aus AEP-Quellen > Streaming-Verbindung)
   * Fügen Sie die Datenfluss-ID hinzu (unter AEP-Quellen > Fluss > API-Nutzungsinformationen)
1. Klicken Sie auf **Speichern**. Geben Sie die Formulardetails an:
   * Titel
   * Name
   * Speicherpfad
1. Fügen Sie die Schaltfläche Senden zum Formular hinzu. Ihr Formular ist bereit, Daten an AEP zu senden.

>[!TAB Kernkomponente]

Führen Sie die folgenden Schritte aus, um ein adaptives Formular basierend auf Kernkomponenten mit Schemaintegration zu erstellen:

1. Zugriff auf den Assistenten zur Formularerstellung:
   * Navigieren Sie zu Ihrer **Adobe Experience Manager** > **Forms** > **Forms und Dokumente**.
   * Klicken Sie **Erstellen** > **Adaptives Formular**.
1. Wählen **auf der** „Quelle“ eine auf Kernkomponenten basierende Vorlage aus.
1. Wählen Sie auf **Registerkarte** die Option **Adobe Experience Platform** aus.
1. Wählen Sie im Eigenschaftenbereich Ihre Cloud-Konfiguration aus.

   ![](/help/forms/assets/xdm-schema-integration.png)

   Das System lädt alle verfügbaren Schemata aus Adobe Experience Platform

   >[!NOTE]
   >
   >
   > * Es werden nur profilaktivierte und nicht systemgenerierte Schemas abgerufen.
   > * Das erste Laden des Schemas kann bei der erstmaligen Einrichtung einige Zeit in Anspruch nehmen.

1. Auswahl der entsprechenden/erforderlichen Felder des Schemas. (Siehe Video mit detaillierten Schritten)
1. Auf der Registerkarte Übermittlung :
   * Wählen Sie die **An Adobe Experience Platform übermitteln** Übermittlungsaktion
   * Konfigurieren Sie die Einstellungen für die Formularübermittlung für die **AEM Forms-Datenübermittlung an Experience Platform**
1. Im Bereich Eigenschaften :
   * Fügen Sie die Streaming-URL hinzu (bezogen aus AEP-Quellen > Streaming-Verbindung)
   * Fügen Sie die Datenfluss-ID hinzu (unter AEP-Quellen > Fluss > API-Nutzungsinformationen)
1. Klicken Sie auf **Speichern**. Geben Sie die Formulardetails an:
   * Titel
   * Name
   * Speicherpfad
1. Fügen Sie die Schaltfläche Senden zum Formular hinzu. Ihr Formular ist bereit, Daten an AEP zu senden.

>[!TAB Universeller Editor]

Führen Sie die folgenden Schritte aus, um ein adaptives Formular zu erstellen, das mit dem universellen Editor mit Schemaintegration erstellt wurde:

1. Zugriff auf den Assistenten zur Formularerstellung:
   * Navigieren Sie zu Ihrer **Adobe Experience Manager** > **Forms** > **Forms und Dokumente**.
   * Klicken Sie **Erstellen** > **Adaptives Formular**.
1. Wählen Sie auf der **Quelle** die Option Edge Delivery-basierte Vorlage aus.
1. Wählen Sie auf **Registerkarte** die Option **Adobe Experience Platform** aus.
1. Wählen Sie im Eigenschaftenbereich Ihre Cloud-Konfiguration aus.

   ![Schemaintegration](/help/forms/assets/xdm-schema-integration.png)

   Das System lädt alle verfügbaren Schemata aus Adobe Experience Platform

   >[!NOTE]
   >
   >
   > * Es werden nur profilaktivierte und nicht systemgenerierte Schemas abgerufen.
   > * Das erste Laden des Schemas kann bei der erstmaligen Einrichtung einige Zeit in Anspruch nehmen.

1. Auswahl der entsprechenden/erforderlichen Felder des Schemas. (Siehe Video mit detaillierten Schritten)
1. Auf der Registerkarte Übermittlung :
   * Wählen Sie die **An Adobe Experience Platform übermitteln** Übermittlungsaktion
   * Konfigurieren Sie die Einstellungen für die Formularübermittlung für die **AEM Forms-Datenübermittlung an Experience Platform**

     >[!NOTE]
     >
     >* Wenn das Symbol „Datenquellen“ in der Benutzeroberfläche des universellen Editors oder die Eigenschaft „Bindungsverweis“ im rechten Eigenschaftenbereich nicht angezeigt wird, aktivieren Sie die **Datenquelle** in Extension Manager.
     >* Wenn das Symbol **Formulareigenschaften bearbeiten** in der Benutzeroberfläche des universellen Editors nicht angezeigt wird, aktivieren Sie die Erweiterung **Formulareigenschaften bearbeiten** in der Extension Manager.
     > 
     > * Informationen zum Aktivieren oder Deaktivieren von Erweiterungen im universellen Editor finden [ im Artikel ](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)Extension Manager-Feature-Highlights}.

   Der Vorbefüllungsdienst für Formulare im universellen Editor wird derzeit nicht unterstützt.

1. Im Bereich Eigenschaften :
   * Fügen Sie die Streaming-URL hinzu (bezogen aus AEP-Quellen > Streaming-Verbindung)
   * Fügen Sie die Datenfluss-ID hinzu (unter AEP-Quellen > Fluss > API-Nutzungsinformationen)
1. Klicken Sie auf **Speichern**. Geben Sie die Formulardetails an:
   * Titel
   * Name
   * Speicherpfad
1. Fügen Sie die Schaltfläche Senden zum Formular hinzu. Ihr Formular ist bereit, Daten an AEP zu senden.

>[!ENDTABS]

## Wichtige Hinweise {#important-notes}

* Daten, die über Formulare gesendet werden, werden nach etwa 10-15 Minuten in AEP angezeigt
* Standardmäßig werden nur profilaktivierte Schemata aufgelistet
* Während die Datenübermittlung für alle Schemata funktioniert, ist die Vorbefüllungsfunktion auf profilaktivierte Schemata beschränkt
* Daten in nicht profilaktivierten Schemata werden nicht für die Profilerstellung verwendet, auch wenn das Schema später für die Profilerstellung aktiviert wird
* **Die Anreicherung des Kundenprofils mit Formulardaten** erfordert eine ordnungsgemäße Konfiguration der Identitätsfelder in Ihrem XDM-Schema
* **AEM Forms-Datenübermittlung an Experience Platform** Verwendet **AEP-Streaming-Verbindung für Forms** um den Echtzeit-Datenfluss sicherzustellen

## Best Practices {#best-practices}

1. Schemastruktur sorgfältig planen, bevor die Profilerstellung aktiviert wird
1. Berücksichtigen Sie beim Einrichten der **AEP-Streaming-Verbindung für Forms die Anforderungen an das Datenvolumen und die Systemskalierung**
1. Testen Sie die Integration gründlich vor der Produktionsbereitstellung.
1. Überwachen der Datenaufnahme und der Profilerstellungsprozesse
1. Entwerfen Sie Ihre **XDM-Schemaintegration mit adaptiven Formularen** um nur erforderliche Daten zu erfassen
1. Strategische Verwendung **Anreicherung von Kundenprofilen mit Formulardaten** zur Verbesserung der Personalisierung

## Technische Überlegungen {#technical-considerations}

* Der Connector verwendet öffentliche Streaming-APIs für die Datenübermittlung
* Die Profilerstellung basiert auf dem Identitätsfeld .
* Die Datenvereinheitlichung erfolgt automatisch in AEP
* Die Integration unterstützt sowohl die Erstellung neuer Formulare als auch vorhandene Formularänderungen
* Die XDM-Schemaintegration mit adaptiven Formularen standardisiert die Datenstruktur über verschiedene Touchpoints hinweg
* Die AEP-Streaming-Verbindung für Forms bietet Funktionen zur Datenaufnahme in Echtzeit

## Häufig gestellte Fragen (FAQ) {#faq}

### Allgemeine Fragen {#general-questions}

**F: „Ist dieser Connector mit mehreren Angeboten von AEM Forms verfügbar?**
A: Nein, diese Integration ist nur für AEM Forms as a Cloud Service verfügbar und unterliegt dem Early Access -Programm.

**F: Funktioniert dieser Connector sowohl mit Kernkomponenten von Adaptive Forms als auch mit Foundation-Komponenten?**
A: Dieser Connector funktioniert sowohl mit Kernkomponenten von Adaptive Forms als auch mit Foundation-Komponenten von Adaptive Forms.

**F: Kann ich Daten von einem einzigen Formular an mehrere AEP-Datensätze senden?**
A.: Derzeit kann jedes Formular nur an einen Datensatz gesendet werden.

**F: Gibt es eine Begrenzung dafür, wie viele Formularübermittlungen verarbeitet werden können?**
A.: Formularübermittlungen unterliegen der Streaming-Aufnahme in AEP [Kontingente und ](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/api/quota)).

<!-- 
>
**Q: Can form attachments be sent to AEP?**
A: No, form attachments cannot be directly sent to AEP. You would need to store attachments separately and only send metadata to AEP. -->

### Fragen zur Implementierung {#implementation-questions}

**F: Wie behebe ich Verbindungsprobleme zwischen AEM Forms und AEP?**
A.: Überprüfen Sie Ihre Cloud-Konfigurationseinstellungen, stellen Sie sicher, dass die API-Anmeldeinformationen korrekt sind, und überprüfen Sie, ob die Streaming-Endpunkt-URL ordnungsgemäß konfiguriert ist.

**F: Kann ich benutzerdefinierte XDM-Schemata mit dieser Integration verwenden?**
A: Ja, Sie können jedes benutzerdefinierte XDM-Schema verwenden, solange es ordnungsgemäß in AEP konfiguriert und für die Vorbefüllungsfunktion für Profile aktiviert ist.

**F: Wie aktiviere ich das Vorausfüllen von Formularen mit AEP-Profildaten?**
A: Stellen Sie sicher, dass Ihr Schema profilaktiviert ist und Ihr Formular so konfiguriert ist, dass es dasselbe Identitätsfeld verwendet, das in Ihrem Schema definiert ist.

**F: Was passiert, wenn ich Daten transformieren muss, bevor ich sie an AEP sende?**
A.: Sie können Formularregeln oder benutzerdefinierte Funktionen verwenden, um Daten vor der Übermittlung zu transformieren. Bei komplexen Umwandlungen sollten Sie eine benutzerdefinierte Übermittlungsaktion verwenden.

**F: Kann ich diese Integration in einem Hybrid-Bereitstellungsmodell verwenden?**
A: Nein, diese Integration ist spezifisch für AEM Forms as a Cloud Service.

## Zusammenfassung und nächste Schritte {#summary-next-steps}

Die AEM Forms-Integration mit Adobe Experience Platform ermöglicht es Unternehmen, einen nahtlosen Datenfluss zwischen Formularen und dem Experience Platform-Ökosystem im Allgemeinen zu erstellen. Durch diese Integration können Sie stärker personalisierte Formularerlebnisse schaffen, die Datenerfassung optimieren und Kundenprofile mit wertvollen Daten zur Formularübermittlung verbessern.

Erste Schritte mit dieser Integration:

1. **Zugriff anfordern** - Falls noch nicht geschehen, treten Sie dem Early Access-Programm bei, indem Sie sich an [aem-forms-ea@adobe.com wenden](mailto:aem-forms-ea@adobe.com?subject=Request%20for%20Early%20Access%20to%20AEP%20Connector%20\(AEM%20Forms%20Integration%20with%20Adobe%20Experience%20Platform\)&body=Dear%20AEM%20Forms%20Team%2C%0D%0A%0D%0AI%20hope%20this%20message%20finds%20you%20well.%0D%0A%0D%0AI%20am%20writing%20to%20request%20access%20to%20the%20Early%20Access%20Program%20for%20the%20AEP%20Connector%2C%20which%20enables%20integration%20between%20AEM%20Forms%20and%20Adobe%20Experience%20Platform.%0D%0A%0D%0AOrganization%20Name%3A%20%5BYour%20organization%20name%5D%0D%0AOrganization%20ID%3A%20%5BYour%20organization%20ID%2C%20if%20available%5D%0D%0AUse%20Case%3A%20%5BBriefly%20describe%20your%20intended%20use%20case%2C%20including%20goals%20or%20benefits%20you%20aim%20to%20achieve%20with%20the%20integration%5D%0D%0A%0D%0AThank%20you%20for%20your%20time%20and%20consideration.%0D%0A%0D%0ABest%20regards%2C%0D%0A%5BYour%20Full%20Name%5D%0D%0A%5BYour%20Job%20Title%2C%20if%20applicable%5D%0D%0A%5BYour%20Contact%20Information%2C%20if%20appropriate%5D)
2. **Umgebung vorbereiten** - Vergewissern Sie sich, dass Sie sowohl in AEM Forms als auch in Adobe Experience Platform über die erforderlichen Berechtigungen und Konfigurationen verfügen
3. **Befolgen Sie die Implementierungsschritte** - Verwenden Sie das obige Handbuch, um Ihre Cloud-Konfiguration einzurichten und Ihr erstes Formular mit AEP-Verbindung und XDM-Schemaintegration zu erstellen
4. **Gründlich testen** - Validieren der Datenübermittlungs- und Vorbefüllungsfunktionen in einer Entwicklungsumgebung
5. **Für die Produktion planen** - Arbeiten Sie mit Ihrem Implementierungs-Team zusammen, um die Bereitstellung der AEM Forms-Datenübermittlung an Experience Platform während der Produktion zu planen

## Zugehörige Ressourcen {#related-resources}

* [Dokumentation zu AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html?lang=de)
* [Dokumentation zu Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/landing/home.html?lang=de)
* [XDM-System - Übersicht](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html?lang=de)
* [Streaming-Aufnahme in Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html)
* [Übersicht über das Echtzeit-Kundenprofil](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html)
* [AEM Forms EARLY ACCESS-Funktionen](/help/forms/early-access-ea-features.md)
* [Erstellen von adaptiven Forms mit Kernkomponenten](/help/forms/creating-adaptive-form-core-components.md)
* [Verwenden von Formulardatenmodellen in AEM Forms](/help/forms/using-form-data-model.md)

<!--
Schema markup for technical documentation
{
  "@context": "https://schema.org",
  "@type": "TechArticle",
  "headline": "Connect AEM Forms with Adobe Experience Platform (AEP) | Data Integration Guide",
  "description": "Learn how to integrate AEM Forms with Adobe Experience Platform to leverage customer profiles, submit form data, and create personalized experiences.",
  "datePublished": "2025-05-28",
  "author": {
    "@type": "Corporation",
    "name": "Adobe"
  },
  "publisher": {
    "@type": "Organization",
    "name": "Adobe Experience League",
    "logo": {
      "@type": "ImageObject",
      "url": "https://experienceleague.adobe.com/assets/img/favicons/apple-touch-icon.png"
    }
  },
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/aem-forms-aep-connector.html"
  },
  "articleSection": "AEM Forms",
  "keywords": "AEM Forms, Adobe Experience Platform, XDM schema, data integration, form submission, customer profiles, personalization"
}
-->
