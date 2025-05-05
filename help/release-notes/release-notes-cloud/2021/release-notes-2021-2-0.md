---
title: Versionshinweise für Version 2021.2.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2021.2.0
exl-id: 88dac54b-cc12-44a0-b429-6e691221f806
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 92%

---


# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!DNL Experience Manager] as a Cloud Service beschrieben.

## Veröffentlichungsdatum {#release-date}

Die Version 2021.2.0 von [!DNL Adobe Experience Manager] as a Cloud Service wurde am 25. Februar 2021 veröffentlicht.
Die folgende Version (2021.3.0) wird am 25. März 2021 veröffentlicht.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Headless-Content-Management {#headless}

* **[GraphQL-API für die Bereitstellung von Inhaltsfragmenten](/help/headless/graphql-api/content-fragments.md)**: Möglichkeit zur Abfrage von Inhaltsfragmenten mithilfe der GraphQL-Syntax und von auf Inhaltsfragmentmodellen basierenden Schemas für die Ausgabe im JSON-Format.

* **[Authentifizierungsunterstützung für GraphQL-API-Anfragen](/help/headless/security/authentication.md)**: Möglichkeit, Anfragen der GraphQL-API mit Zugriffs-Token für Server-seitige APIs zu authentifizieren.

* **[RemotePage-Komponente](/help/implementing/developing/hybrid/remote-page.md)**: Zusätzliche Unterstützung für das Anzeigen und Bearbeiten externer SPAs in AEM.

* **[Bearbeiten einer externen SPA in AEM](/help/implementing/developing/hybrid/editing-external-spa.md)**: Neue Möglichkeit, eine eigenständige Single Page Application in eine AEM-Instanz hochzuladen, bearbeitbare Inhaltsabschnitte hinzuzufügen und das Authoring zu aktivieren.

* Verbesserte JSON-Ausgabe aus der GraphQL-API, einschließlich der Möglichkeit, Rich-Text im JSON-Format und in Gebietsschemas auszugeben.

* Unterstützung für die Verschachtelung von Inhaltsfragmentmodellen, damit verschachtelte Inhaltsfragmentstrukturen über dedizierte Inhaltsfragmentreferenz-Datentypen oder Inhaltsfragmentreferenzen inline in mehrzeiligen Textfeldern erstellt werden können.

* Zusätzliche Validierungsregeln in den Datentypen des Inhaltsfragmentmodells verfügbar, einschließlich „unique“, „required“ und „translatable“.

* Möglichkeit, Inhaltsfragmentmodelle zu taggen und das Erstellen von Inhaltsfragmenten in einem Ordner mit Richtlinien durch Tags oder Pfade zu ermöglichen.

* Verbesserungen der Benutzerfreundlichkeit im Inhaltsfragmente-Editor, einschließlich Veröffentlichungsaktion und Anzeige des Modells, auf dem ein Fragment basiert.

* Möglichkeit zur Vorschau der JSON-Ausgabe direkt im Inhaltsfragmente-Editor.

<!--
### Progressive Web Apps (PWAs) {#pwa}

* [A Progressive Web App (PWA) version of a site](/help/sites-cloud/authoring/sites-console/enable-pwa.md)  can now be enabled at the project level via simple configuration.
-->

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

## Neue Funktionen in [!DNL Assets] {#what-is-new-assets}

* Assets können mit [!DNL Experience Manager Assets Brand Portal] bezogen werden. Es hilft, Assets für neue Marketing-Kampagnen, Fotoshootings und Projekte über die Agenturnutzer zu beschaffen.

* [!DNL Experience Manager Assets] as a [!DNL Cloud Service] ist berechtigt, eine vorkonfigurierte [!DNL Brand Portal]-Instanz zu haben. Der [!DNL Cloud Manager]-Nutzer kann [!DNL Brand Portal] unter [!DNL Experience Manager Assets] as a [!DNL Cloud Service] aktivieren. Siehe [Aktivieren von Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/brand-portal/configure-aem-assets-with-brand-portal.html?lang=de).

* Unternehmen können jetzt Assets mit [!DNL Brand Portal] beschaffen. Die Asset-Beschaffungsfunktion verwendet [!DNL Brand Portal], um Kunden bei der Zusammenarbeit mit Agenturen zu helfen, um Assets für neue Marketing-Kampagnen, Fotoshootings und Projekte zu beschaffen. Weitere Informationen finden Sie unter [Asset-Beschaffung in  [!DNL Brand Portal]](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html?lang=de).

* Der Nutzungsbericht für [!DNL Brand Portal] zeigt jetzt nur noch die aktiven Benutzer an. Die inaktiven Benutzer werden jetzt nicht mehr angezeigt. Aktive Benutzer sind diejenigen, deren Konto einem Produktprofil in der [!DNL Admin Console] zugewiesen ist. Weitere Informationen finden Sie unter [[!DNL Brand Portal] Berichte](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/admin-tools/brand-portal-reports.html?lang=de).

* In [!DNL Brand Portal] wird eine neue Download-Einstellung eingeführt, mit der Sie beim Herunterladen von Ordnern, Sammlungen usw. für jedes Asset einen eigenen Ordner erstellen können. Weitere Informationen finden Sie unter [Download-Einstellungen](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html?lang=de).

## Fehlerbehebungen in [!DNL Assets] {#bug-fixes-assets}

* Wenn mehrere Assets ausgewählt werden, um die Eigenschaften zu aktualisieren, tritt manchmal entweder ein Fehler auf oder die Eigenschaften eines nicht ausgewählten Assets werden aktualisiert. (CQ-4316532)
* Beim Versuch, die [!UICONTROL Suchleiste in der Asset-Verwaltung] zu öffnen, bleibt die Seite leer. Wenn Sie auf [!UICONTROL Bearbeiten] > [!UICONTROL Einstellungen] klicken, wird ein Fehler ausgegeben. (CQ-4315079)
* Wenn nach der Lösung des Benennungskonflikts eine neue Version eines vorhandenen Assets erstellt wird, werden die Metadaten des ursprünglichen Assets überschrieben. (CQ-4313594)
* Wenn ein Asset mit langem Anmerkungstext gedruckt wird, wird der Anmerkungstext gekürzt, auch wenn Platz verfügbar ist. (CQ-4314101)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Produkt-Experience-Management: Reichern Sie Produktkatalogseiten individuell mit Experience Fragments an.

* Erweiterte Eigenschaften der Produktkonsole zum Anzeigen verknüpfter Assets und Experience Fragments, einschließlich Aktionen zum schnellen Navigieren zum zugehörigen Inhalt.

* Freigabe der CIF Venia-Referenz-Website 2021.02.24, die die aktuelle CIF-Kernkomponenten Version 1.8.0 enthält. Weitere Informationen finden Sie unter [CIF Venia](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.02.24)Referenz-Site .

* Version 1.8.0 von CIF-Kernkomponenten veröffentlicht. Weitere Informationen finden Sie unter {[&#128279;](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.8.0)}CIF-Kernkomponenten.

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Die Version 2021.2.0 von Cloud Manager in AEM as a Cloud Service wurde am 11. Februar 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-cloud-manager}


* Assets-Kunden können jetzt selbst entscheiden, wann und wo sie ihre Brand Portal-Instanz über die Cloud Manager-Benutzeroberfläche bereitstellen möchten. Für ein reguläres (nicht Sandbox-) Programm mit Assets-Lösung kann Brand Portal jetzt in der Produktionsumgebung bereitgestellt werden. Die Bereitstellung kann nur einmal in der Produktionsumgebung durchgeführt werden.

* Der AEM-Projektarchetyp, der bei der Projekt- und Sandbox-Erstellung verwendet wird, wurde auf Version 25 aktualisiert.

* Die Liste der veralteten APIs, die beim Code-Scanning identifiziert wurden, wurde verfeinert und enthält nun zusätzliche Klassen und Methoden, die in den neuesten Cloud Service SDK-Versionen nicht mehr unterstützt werden.

* Das SonarQube-Profil für Cloud Manager wurde aktualisiert, um die Sonar-Regel squid:S2142 zu entfernen. Diese führt nicht mehr zu Konflikten mit Thread-Unterbrechungsprüfungen.

* Die Cloud Manager-Benutzeroberfläche informiert den Benutzer, der möglicherweise vorübergehend keinen Domain-Namen hinzufügen/aktualisieren kann, weil der zugehörigen Umgebung entweder eine laufende Pipeline angehängt ist oder sie sich derzeit im Schritt „Warten auf die Genehmigung“ befindet.

* Eigenschaften, die in `pom.xml`-Kundendateien mit dem Präfix „sonar“ festgelegt wurden, werden nun dynamisch entfernt, um Build- und Qualitätsprüfungsfehler zu vermeiden.

* Die Cloud Manager-Benutzeroberfläche informiert den Benutzer, der möglicherweise vorübergehend ein SSL-Zertifikat nicht auswählen kann, wenn es von einem Domain-Namen verwendet wird, der gerade bereitgestellt wird.

* Es wurden zusätzliche Code-Qualitätsregeln hinzugefügt, um Probleme mit der Kompatibilität von Cloud Services zu behandeln.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Beim Abgleichen des SSL-Zertifikats mit einem Domain-Namen wird nicht mehr zwischen Groß- und Kleinschreibung unterschieden.

* Die Cloud Manager-Benutzeroberfläche informiert jetzt einen Benutzer mit einer entsprechenden Fehlermeldung, wenn die privaten Schlüssel des Zertifikats nicht dem 2048-Bit-Limit entsprechen.

* Die Cloud Manager-Benutzeroberfläche informiert den Benutzer, der möglicherweise vorübergehend ein SSL-Zertifikat nicht auswählen kann, wenn es von einem Domain-Namen verwendet wird, der gerade bereitgestellt wird.

* In einigen Fällen kann ein internes Problem dazu führen, dass der Löschvorgang der Umgebung stecken bleibt.

* Einige Pipeline-Ausfälle wurden fälschlicherweise als Pipeline-Fehler gemeldet.

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool 1.2.4 wurde am 10. Februar 2021 veröffentlicht.

### Fehlerbehebungen {#bug-fixes-ctt}

* Beim Zuordnen mehrerer Benutzer wurden die IMS-IDs einiger Benutzer falsch zugeordnet. Dieses Problem wurde behoben.

### Veröffentlichungsdatum {#release-date-ctt-feb}

Das Content Transfer Tool 1.2.2 wurde am 1. Februar 2021 veröffentlicht.

### Neue Funktionen im Content Transfer Tool {#what-is-new-ctt}

* Neue Funktion und Benutzeroberfläche zum Content Transfer Tool – User Mapping Tool hinzugefügt. Diese Funktion ordnet bestehende Benutzer und Gruppen im Rahmen der Inhaltsmigration automatisch ihren Adobe Identity Management System-IDs zu.
Weitere Informationen finden Sie unter [Verwendung des Tools für die Benutzerzuordnung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=de).
* Das Content Transfer Tool migriert jetzt alle Gruppen und Benutzer, auf die im Migrationssatz verwiesen wird, einschließlich untergeordneter Elemente.
* Benutzer können beim Erstellen von Migrationssätzen bestimmte Pfade unter `/etc` auswählen.

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer 2.1.2 wurde am 18. Februar 2021 veröffentlicht.

### Neue Funktionen in Best Practices Analyzer {#what-is-new-bpa}

* Fähigkeit, die Verwendung von AEM Forms und die AEM Forms-Implementierung zu erkennen und Bereiche anzugeben, die für die Migration zu AEM Forms as a Cloud Service relevant sind.
* Möglichkeit, benutzerdefinierte Komponenten und Vorlagen zu erkennen und darüber zu berichten.
* Möglichkeit, den Typ des verwendeten Knotenspeichers und Datenspeichers zu erkennen.
* Möglichkeit, die Nutzung von Dynamic Media zu erkennen.
* Möglichkeit, die verwendete Java-Version zu erkennen.

## Code-Refaktorierungs-Tools {#code-refactoring-tools}

### Neue Funktionen in den Code-Refaktorierungs-Tools {#what-is-new-crt}

* Neue Version des AIO-CLI-Plug-ins veröffentlicht. Die neueste Version dieses Plug-ins enthält mehrere Fehlerbehebungen für den Repository Modernizer.
Weitere Informationen [ dieses Plug-in ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=de#benefits) Sie unter „Einheitliches Erlebnis“.

### Fehlerbehebungen {#bug-fixes-crt}

* Mehrere Fehlerbehebungen, die im Repository Modernizer vorgenommen wurden.
Weitere [ finden Sie unter „GitHub-Ressource: aem-cloud-service-source](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)migration“.
