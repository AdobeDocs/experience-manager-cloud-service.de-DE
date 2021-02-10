---
title: Aktuelle Versionshinweise für  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Aktuelle Versionshinweise für  [!DNL Adobe Experience Manager]  as a Cloud Service.
translation-type: tm+mt
source-git-commit: 071eefa3b6f5e9636ace612e968b6a9627c98550
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 21%

---


# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!DNL Experience Manager] as a Cloud Service beschrieben.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für [!DNL Adobe Experience Manager] als Cloud Service 2021.1.0 ist der 3. Februar 2021.
Die folgende Version (2021.2.0) wird am 25. Februar 2021 veröffentlicht.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Headless-Content-Management {#headless}

* **[GraphQL API für Content Fragment Versand](/help/assets/content-fragments/graphql-api-content-fragments.md)**: Möglichkeit zur Abfrage von Inhaltsfragmenten mithilfe der GraphQL-Syntax und von auf Inhaltsfragmentmodellen basierenden Schemas für die Ausgabe im JSON-Format.

* **[Authentifizierungsunterstützung für GraphQL-API-Anfragen](/help/assets/content-fragments/graphql-authentication-content-fragments.md)**: Möglichkeit, GraphQL API-Anfragen mit Zugriffstoken für serverseitige APIs zu authentifizieren.

* **[Die RemotePage-Komponente](/help/implementing/developing/hybrid/remote-page.md)**: Zusätzliche Unterstützung für das Anzeigen und Bearbeiten externer SPA in AEM.

* **[Bearbeiten eines externen SPA in AEM](/help/implementing/developing/hybrid/editing-external-spa.md)**: Es wurde die Möglichkeit hinzugefügt, eine eigenständige Einzelseitenanwendung in eine AEM Instanz hochzuladen, bearbeitbare Inhaltsabschnitte hinzuzufügen und das Authoring zu aktivieren.

* Verbesserte JSON-Ausgabe aus der GraphQL API, einschließlich der Möglichkeit, Rich-Text im JSON-Format und in Gebietsschemas auszugeben.

* Unterstützung für die Verschachtelung von Inhaltsfragmentmodellen, damit verschachtelte Inhaltsfragmentstrukturen über dedizierte Content Fragment Reference-Datentypen oder Inhaltsfragmentverweise inline in mehrzeiligen Textfeldern erstellt werden können.

* Zusätzliche Validierungsregeln, die in den Datentypen des Inhaltsfragmentmodells verfügbar sind, einschließlich &quot;eindeutig&quot;, &quot;erforderlich&quot;und &quot;übersetzbar&quot;.

* Möglichkeit, Content Fragment-Modelle zu taggen und die Erstellung von Inhaltsfragmenten in einem Ordner mit Richtlinien durch Tags oder Pfade zu ermöglichen.

* Verbesserungen der Benutzerfreundlichkeit im Inhaltsfragment-Editor, einschließlich Veröffentlichungsaktion und Anzeige des Modells, auf dem ein Fragment basiert.

* Möglichkeit zur Vorschau der JSON-Ausgabe direkt im Inhaltsfragment-Editor.

<!--
### Progressive Web Apps (PWAs) {#pwa}

* [A Progressive Web App (PWA) version of a site](/help/sites-cloud/authoring/features/enable-pwa.md)  can now be enabled at the project level via simple configuration.
-->

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

* [!DNL Experience Manager] als  [!DNL Cloud Service] Erweiterung der Funktion für intelligente Tags, um die Identifizierung von Suchbegriffen und Entitäten in textbasierten Assets zu unterstützen. Der Text wird identifiziert, indiziert und als Metadaten zur Verbesserung der Sucherfahrung bereitgestellt, ohne dass eine Konfiguration erforderlich ist. Siehe [Smart Tags](/help/assets/smart-tags.md).

* Das MXF-Dateiformat wird jetzt unterstützt. Siehe [Unterstützte Dateiformate](/help/assets/file-format-support.md#video-formats).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Produkt-Experience-Management: Neue Registerkarte &quot;Commerce&quot;-Eigenschaften für Assets und Erlebnisfragmente. Auf dieser Registerkarte können Sie Produkte/Kategorien mit Assets und Erlebnisfragmenten verknüpfen. Auf der Registerkarte werden auch Echtzeitdaten für verknüpfte Produkte/Kategorien sowie ein Link zur Anzeige von Details in der Produktkonsole angezeigt.

* CIF Venia-Referenzseite - 2021.02.02, die die neueste CIF-Kernkomponenten Version v1.7.0 enthält. Weitere Informationen finden Sie unter [CIF Venia Reference Site](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.02.02).

* Version 1.7.0 von CIF-Kernkomponenten veröffentlicht. Weitere Informationen finden Sie unter [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.7.0).

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Das Veröffentlichungsdatum für Cloud Manager in AEM als Cloud Service 2021.1.0 ist der 14. Januar 2021.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Die Assets Production-Instanz kann gelegentlich den Markenportalstatus auf der Detailseite **Umgebung** als *Ausstehend* anzeigen, ohne dass der Benutzer aktiv werden kann.

* Beim Auslösen einer Dehibernate aus Cloud Manager wurde manchmal eine Fehlermeldung angezeigt, auch wenn die Deaktivierung erfolgreich gestartet wurde.

* Seltene Fälle von Fehlern beim Erstellen oder Löschen von Umgebung wurden behoben.

## AEM als Cloud Service Foundation {#aem-as-a-cloud-service-foundation}

### Neue Funktionen {#what-is-new-foundation}

* Authentifizierte API-Aufrufe von Server zu Server - Generieren Sie die entsprechenden Zugriffstoken, um authentifizierte Server-zu-Server-API-Aufrufe zwischen Ihren externen Anwendungen und AEM als Cloud Service-Umgebung durchzuführen. Weitere Informationen finden Sie in der [Dokumentation](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) oder im [Tutorial](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication).

### SDK Build Analyzer {#sdk-build-analyzers}

Das Build Analyzer-Maven-Plug-in des AEM as a Cloud Service-SDK erkennt Probleme in einem Maven-Projekt, einschließlich fehlender Abhängigkeiten. Es gibt Entwicklern die Möglichkeit, Probleme während der lokalen Entwicklung zu entdecken, lange bevor sie mit Cloud Manager in Cloud-Umgebungen bereitgestellt werden.

Für diese Version wurden zwei neue Analyzer hinzugefügt:

* Repoinit Analyzer
* bundle-nativecode

Weitere Informationen finden Sie in der Dokumentation [hier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=de#developing).

## Cloud-Umstellungs-Tools {#code-transition-tools}

### Veröffentlichungsdatum {#release-date-ctt}

Das Veröffentlichungsdatum für das Inhaltsübermittlungstool v1.2.2 ist der 1. Februar 2021.

### Neue Funktionen in [!DNL Content Transfer Tool] {#what-is-new-ctt}

* Neue Funktion und Benutzeroberfläche zum Inhaltsübermittlungstool - Benutzerzuordnungswerkzeug hinzugefügt. Diese Funktion ordnet bestehende Benutzer und Gruppen im Rahmen der Aktivität zur Inhaltsmigration automatisch ihrer Adobe Identity Management System-IDs zu. Weitere Informationen finden Sie unter [Verwenden des Tools für die Benutzerzuordnung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html).
* Content Transfer Tool migriert jetzt alle Gruppen und Benutzer, auf die im Migrationsset verwiesen wird, einschließlich untergeordneter Elemente.
* Benutzer können beim Erstellen von Migrationssätzen bestimmte Pfade unter `/etc` auswählen.
