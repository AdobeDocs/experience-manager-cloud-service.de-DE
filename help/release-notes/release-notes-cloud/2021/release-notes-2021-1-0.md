---
title: Versionshinweise für Version 2021.1.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2021.1.0
exl-id: cd639736-6e3d-4b69-b8ae-11e4e6490535
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 92%

---


# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!DNL Experience Manager] as a Cloud Service beschrieben.

## Veröffentlichungsdatum {#release-date}

Die Version 2021.1.0 von [!DNL Adobe Experience Manager] as a Cloud Service wurde am 3. Februar 2021 veröffentlicht.
Die folgende Version (2021.2.0) wird am 25. Februar 2021 veröffentlicht.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

* **[HTTP-API für Inhaltsfragmente](/help/assets/content-fragments/assets-api-content-fragments.md)**: Hinzufügen der Möglichkeit zum Hinzufügen/Aktualisieren und Löschen von Varianten von Inhaltsfragmenten über die HTTP-API.

* **[GraphQL-API für die Bereitstellung von Inhaltsfragmenten](/help/headless/graphql-api/content-fragments.md)**: Möglichkeit zur Abfrage von Inhaltsfragmenten mithilfe der GraphQL-Syntax und von auf Inhaltsfragmentmodellen basierenden Schemas für die Ausgabe im JSON-Format.

* **[Authentifizierungsunterstützung für GraphQL-API-Anfragen](/help/headless/security/authentication.md)**: Möglichkeit, Anfragen der GraphQL-API mit Zugriffs-Token für Server-seitige APIs zu authentifizieren.

* Verbesserte JSON-Ausgabe aus der GraphQL-API, einschließlich der Möglichkeit, Rich-Text im JSON-Format und in Gebietsschemas auszugeben.

* Unterstützung für die Verschachtelung von Inhaltsfragmentmodellen, damit verschachtelte Inhaltsfragmentstrukturen über dedizierte Inhaltsfragmentreferenz-Datentypen oder Inhaltsfragmentreferenzen inline in mehrzeiligen Textfeldern erstellt werden können.

* Zusätzliche Validierungsregeln in den Datentypen des Inhaltsfragmentmodells verfügbar, einschließlich „unique“, „required“ und „translatable“.

* Möglichkeit, Inhaltsfragmentmodelle zu taggen und das Erstellen von Inhaltsfragmenten in einem Ordner mit Richtlinien durch Tags oder Pfade zu ermöglichen.

* Verbesserungen der Benutzerfreundlichkeit im Inhaltsfragmente-Editor, einschließlich Veröffentlichungsaktion und Anzeige des Modells, auf dem ein Fragment basiert.

* Möglichkeit zur Vorschau der JSON-Ausgabe direkt im Inhaltsfragmente-Editor.


## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

* [!DNL Experience Manager] as a [!DNL Cloud Service] erweitert die Smart-Tags-Funktion, um die Identifizierung von Suchbegriffen und Entitäten in textbasierten Assets zu unterstützen. Der Text wird identifiziert, indiziert und in Form von Metadaten zur Verbesserung der Sucherfahrung bereitgestellt, ohne dass eine Konfiguration erforderlich ist. Siehe [Smart-Tags](/help/assets/smart-tags.md).

* Das MXF-Dateiformat wird jetzt unterstützt. Siehe [Unterstützte Dateiformate](/help/assets/file-format-support.md#video-formats).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Produkterlebnis-Management: Neue Eigenschaftenseite „Commerce“ für Assets und Experience Fragments. Auf dieser Registerkarte können Sie Produkte/Kategorien mit Assets und Experience Fragments verknüpfen. Auf der Registerkarte werden auch Echtzeitdaten für verknüpfte Produkte/Kategorien sowie ein Link zur Anzeige von Details in der Produktkonsole angezeigt.

* Freigabe der CIF Venia-Referenz-Website 2021.02.02, die die aktuelle CIF-Kernkomponenten Version 1.7.0 enthält. Weitere Informationen finden Sie unter [CIF Venia](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.02.02)Referenz-Site .

* Version 1.7.0 von CIF-Kernkomponenten veröffentlicht. Weitere Informationen finden Sie unter {[&#128279;](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.7.0)}CIF-Kernkomponenten.

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Die Version 2021.1.0 von Cloud Manager in AEM as a Cloud Service wurde am 14. Januar 2021 veröffentlicht.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Die Assets-Produktionsinstanz kann gelegentlich den Brand Portal-Status auf der Seite **Umgebungsdetails** als *Ausstehend* anzeigen, ohne dass der Benutzer aktiv werden kann.

* Wenn das Zurückholen aus dem Ruhezustand in Cloud Manager ausgelöst wurde, wurde manchmal eine Fehlermeldung angezeigt, obwohl der Vorgang erfolgreich gestartet wurde.

* Seltene Fälle von Fehlern beim Erstellen oder Löschen der Umgebung wurden behoben.

## Code-Refaktorierungs-Tools {#code-refactoring-tools}

### Neue Funktionen in [!DNL Code Refactoring Tools] {#what-is-new-crt}

* Neue Version des AIO-CLI-Plug-ins veröffentlicht. Die neueste Version dieses Plug-ins enthält Fehlerbehebungen für den AEM Dispatcher Converter und den Repository Modernizer und unterstützt auch ein neues Dienstprogramm - den Index Converter. Weitere Informationen [ dieses Plug-in ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=de#benefits) Sie unter „Einheitliches Erlebnis“.

* Index Converter ist ein Dienstprogramm, das verwendet werden kann, um die benutzerdefinierten OAK-Indexdefinitionen eines Kunden in mit AEM as a Cloud Service kompatible OAK-Indexdefinitionen umzuwandeln. Weitere Informationen finden [ unter ](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/index-converter)Index Converter“.

* Neue Funktion zu [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) hinzugefügt, die ein separates Paket `ui.config` erstellt, das alle OSGi-Konfigurationen enthält.

### Fehlerbehebungen {#crt-bug-fixes}

* Es wurden mehrere Fehlerkorrekturen an den Tools AEM Dispatcher Converter und Repository Modernizer durchgeführt. Siehe [AEM Dispatcher Converter](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/dispatcher-converter) und [Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer).

## AEM as a Cloud Service Foundation {#aem-as-a-cloud-service-foundation}

### Neue Funktionen {#what-is-new-foundation}

* Authentifizierte API-Aufrufe von Server zu Server: Generieren Sie die entsprechenden Zugriffs-Tokens, um authentifizierte Server-zu-Server-API-Aufrufe zwischen Ihren externen Programmen und AEM as a Cloud Service-Umgebungen durchzuführen. Weitere Informationen finden Sie in der [Dokumentation](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) oder im [Tutorial](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=de#authentication).

### SDK Build Analyzer {#sdk-build-analyzers}

Das Build Analyzer-Maven-Plug-in des AEM as a Cloud Service-SDK erkennt Probleme in einem Maven-Projekt, einschließlich fehlender Abhängigkeiten. Es gibt Entwicklern die Möglichkeit, Probleme während der lokalen Entwicklung zu entdecken, lange bevor sie mit Cloud Manager in Cloud-Umgebungen bereitgestellt werden.

Für diese Version wurden zwei neue Analyzer hinzugefügt:

* Repoinit Analyzer
* bundle-nativecode

Weitere Informationen finden Sie in der Dokumentation [hier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=de#developing).

## Cloud-Umstellungs-Tools {#code-transition-tools}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool 1.2.2 wurde am 1. Februar 2021 veröffentlicht.

### Neue Funktionen in [!DNL Content Transfer Tool] {#what-is-new-ctt}

* Neue Funktion und Benutzeroberfläche zum Content Transfer Tool – User Mapping Tool hinzugefügt. Diese Funktion ordnet bestehende Benutzer und Gruppen im Rahmen der Inhaltsmigration automatisch ihren Adobe Identity Management System-IDs zu. Weitere Informationen finden Sie unter [Verwendung des Tools für die Benutzerzuordnung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=de).
* Das Content Transfer Tool migriert jetzt alle Gruppen und Benutzer, auf die im Migrationssatz verwiesen wird, einschließlich untergeordneter Elemente.
* Benutzer können beim Erstellen von Migrationssätzen bestimmte Pfade unter `/etc` auswählen.
