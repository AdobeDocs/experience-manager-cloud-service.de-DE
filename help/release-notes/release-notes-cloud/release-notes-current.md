---
title: Aktuelle Versionshinweise für  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Aktuelle Versionshinweise für  [!DNL Adobe Experience Manager]  as a Cloud Service.
translation-type: tm+mt
source-git-commit: 801f1df5ceaa24289e2d88ecfe187a7a1497a6fe
workflow-type: tm+mt
source-wordcount: '1108'
ht-degree: 17%

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

Die Version 2021.2.0 von Cloud Manager in AEM as a Cloud Service wurde am 11. Februar 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-cloud-manager}

* Die Cloud Manager-Produktionspipeline umfasst jetzt benutzerdefinierte Testfunktionen für die Benutzeroberfläche.

* Assets, die Kunden jetzt über die Benutzeroberfläche von Cloud Manager auswählen können, wann und wo sie ihre Brand Portal-Instanz auf Self-Service-Weise bereitstellen. Für ein normales (nicht Sandbox-)Programm mit Assets-Lösung kann nun das Markenportal auf der Umgebung Produktion bereitgestellt werden. Die Bereitstellung kann nur einmal auf der Produktions-Umgebung erfolgen.

* Der AEM Projektarchiv, der in Project und Sandbox Creation verwendet wird, wurde auf Version 25 aktualisiert.

* Die Liste veralteter APIs, die während der Codeprüfung identifiziert wurden, wurde optimiert und enthält nun weitere Klassen und Methoden, die in den neuesten Cloud Service SDK-Versionen nicht mehr unterstützt werden.

* SonarQube-Profil für Cloud Manager aktualisiert, um die Sonar-Regel squid:S2142 zu entfernen. Dies steht nicht mehr in Konflikt mit Thread-Unterbrechungsüberprüfungen.

* Die Benutzeroberfläche von Cloud Manager informiert den Benutzer, der vorübergehend keinen Domänennamen hinzufügen/aktualisieren kann, da an der zugehörigen Umgebung entweder eine laufende Pipeline angehängt ist oder derzeit auf den Genehmigungsvorgang wartet.

* Eigenschaften, die in benutzerdefinierten Dateien mit dem Präfix &quot;sonar&quot;festgelegt wurden, werden nun dynamisch entfernt, um Fehler beim Erstellen und Überprüfen von Qualität zu vermeiden.`pom.xml`

* Die Benutzeroberfläche von Cloud Manager informiert den Benutzer, der vorübergehend kein SSL-Zertifikat auswählen kann, wenn es von einem Domänennamen verwendet wird, der derzeit bereitgestellt wird.

* Es wurden zusätzliche Regeln zur Codequalität hinzugefügt, um Probleme mit der Kompatibilität von Cloud Services zu behandeln.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Beim Abgleichen des SSL-Zertifikats mit einem Domänennamen wird nicht mehr zwischen Groß- und Kleinschreibung unterschieden.

* Die Benutzeroberfläche von Cloud Manager informiert nun einen Benutzer, wenn die privaten Schlüssel des Zertifikats die 2048-Bit-Grenze nicht erfüllen, und gibt eine entsprechende Fehlermeldung aus.

* Die Benutzeroberfläche von Cloud Manager informiert den Benutzer, der vorübergehend kein SSL-Zertifikat auswählen kann, wenn es von einem Domänennamen verwendet wird, der derzeit bereitgestellt wird.

* In einigen Fällen kann ein internes Problem dazu führen, dass der Löschvorgang der Umgebung blockiert wird.

* Einige Pipeline-Fehler wurden fälschlicherweise als Pipeline-Fehler gemeldet.

## AEM als Cloud Service Foundation {#aem-as-a-cloud-service-foundation}

### Neue Funktionen {#what-is-new-foundation}

* Authentifizierte API-Aufrufe von Server zu Server - Generieren Sie die entsprechenden Zugriffstoken, um authentifizierte Server-zu-Server-API-Aufrufe zwischen Ihren externen Anwendungen und AEM als Cloud Service-Umgebung durchzuführen. Weitere Informationen finden Sie in der [Dokumentation](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) oder im [Tutorial](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication).

### SDK Build Analyzer {#sdk-build-analyzers}

Das Build Analyzer-Maven-Plug-in des AEM as a Cloud Service-SDK erkennt Probleme in einem Maven-Projekt, einschließlich fehlender Abhängigkeiten. Es gibt Entwicklern die Möglichkeit, Probleme während der lokalen Entwicklung zu entdecken, lange bevor sie mit Cloud Manager in Cloud-Umgebungen bereitgestellt werden.

Für diese Version wurden zwei neue Analyzer hinzugefügt:

* Repoinit Analyzer
* bundle-nativecode

Weitere Informationen finden Sie in der Dokumentation [hier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=de#developing).

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt}

Das Veröffentlichungsdatum für das Inhaltsübermittlungs-Tool v1.2.4 ist der 10. Februar 2021.

### Fehlerbehebungen {#bug-fixes-ctt}

* Beim Zuordnen mehrerer Benutzer wurden die IMS-IDs einiger Benutzer falsch zugeordnet. Dies wurde behoben.

### Veröffentlichungsdatum {#release-date-ctt-feb}

Das Veröffentlichungsdatum für das Inhaltsübermittlungstool v1.2.2 ist der 1. Februar 2021.

### Neue Funktionen in [!DNL Content Transfer Tool] {#what-is-new-ctt}

* Neue Funktion und Benutzeroberfläche zum Inhaltsübermittlungstool - Benutzerzuordnungswerkzeug hinzugefügt. Diese Funktion ordnet bestehende Benutzer und Gruppen im Rahmen der Aktivität zur Inhaltsmigration automatisch ihrer Adobe Identity Management System-IDs zu. Weitere Informationen finden Sie unter [Verwenden des Tools für die Benutzerzuordnung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html).
* Content Transfer Tool migriert jetzt alle Gruppen und Benutzer, auf die im Migrationsset verwiesen wird, einschließlich untergeordneter Elemente.
* Benutzer können beim Erstellen von Migrationssätzen bestimmte Pfade unter `/etc` auswählen.

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa}

Das Veröffentlichungsdatum für Best Practices Analyzer v2.1.0 ist der 11. Februar 2021.

### Neue Funktionen in [!DNL Best-Practices-Analyzer] {#what-is-new-bpa}

* Möglichkeit, den Einsatz der AEM Forms- und AEM Forms-Implementierung zu ermitteln und Bereiche anzugeben, die für die Migration nach AEM Forms als Cloud Service relevant sind.
* Möglichkeit, benutzerdefinierte Komponenten und Vorlagen zu erkennen und darüber zu berichten.
* Möglichkeit, den Typ des verwendeten Knotenspeichers und Datenspeichers zu erkennen.
* Möglichkeit, die Nutzung von Dynamic Media zu erkennen.
* Möglichkeit, die verwendete Java-Version zu erkennen.







