---
title: Versionshinweise für Version 2021.2.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2021.2.0
exl-id: 88dac54b-cc12-44a0-b429-6e691221f806
translation-type: tm+mt
source-git-commit: b842f70bd53676d23229e24edb4a957ff7613824
workflow-type: tm+mt
source-wordcount: '1237'
ht-degree: 39%

---


# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!DNL Experience Manager] as a Cloud Service beschrieben.

## Veröffentlichungsdatum {#release-date}

Die Version 2021.2.0 von [!DNL Adobe Experience Manager] as a Cloud Service wurde am 25. Februar 2021 veröffentlicht.
Die folgende Version (2021.3.0) wird am 25. März 2021 veröffentlicht.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Headless-Content-Management {#headless}

* **[GraphQL-API für die Bereitstellung von Inhaltsfragmenten](/help/assets/content-fragments/graphql-api-content-fragments.md)**: Möglichkeit zur Abfrage von Inhaltsfragmenten mithilfe der GraphQL-Syntax und von auf Inhaltsfragmentmodellen basierenden Schemas für die Ausgabe im JSON-Format.

* **[Authentifizierungsunterstützung für GraphQL-API-Anfragen](/help/assets/content-fragments/graphql-authentication-content-fragments.md)**: Möglichkeit, Anfragen der GraphQL-API mit Zugriffs-Token für Server-seitige APIs zu authentifizieren.

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

* [A Progressive Web App (PWA) version of a site](/help/sites-cloud/authoring/features/enable-pwa.md)  can now be enabled at the project level via simple configuration.
-->

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

## Neue Funktionen in [!DNL Assets] {#what-is-new-assets}

* Assets können mit [!DNL Experience Manager Assets Brand Portal] bezogen werden. Es hilft, Assets von Agenturbenutzern für neue Marketing-Kampagnen, Fotoaufnahmen und Projekte zu beziehen.

* [!DNL Experience Manager Assets] als eine  [!DNL Cloud Service] berechtigt ist, über eine vorkonfigurierte  [!DNL Brand Portal] Instanz zu verfügen. Der [!DNL Cloud Manager]-Benutzer kann [!DNL Brand Portal] unter [!DNL Experience Manager Assets] als [!DNL Cloud Service] aktivieren. Siehe [Aktivieren des Markenportals](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/brand-portal/configure-aem-assets-with-brand-portal.html?lang=de).

* Unternehmen können jetzt Assets mit [!DNL Brand Portal] ausgeben. Die Asset-Sourcing-Funktion nutzt [!DNL Brand Portal], um Kunden bei der Interaktion mit Agenturbenutzern zu helfen, Assets für neue Marketing-Kampagnen, Fotografien und Projekte zu beziehen. Siehe [Asset-Sourcing in [!DNL Brand Portal]](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html).

* Der Nutzungsbericht zeigt jetzt nur die aktiven Benutzer an. [!DNL Brand Portal] Die inaktiven Benutzer werden jetzt nicht angezeigt. Aktive Benutzer sind diejenigen, deren Konto einem Profil im [!DNL Admin Console] zugewiesen ist. Siehe [[!DNL Brand Portal] Berichte](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/admin-tools/brand-portal-reports.html).

* In [!DNL Brand Portal] wird eine neue Downloadeinstellung eingeführt, mit der Sie separate Ordner für jedes Asset erstellen können, wenn Sie Ordner, Sammlungen usw. herunterladen. Weitere Informationen finden Sie unter [Download-Einstellungen](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html).

## Fehlerbehebungen in [!DNL Assets] {#bug-fixes-assets}

* Wenn mehrere Assets ausgewählt sind, um die Eigenschaften zu aktualisieren, tritt manchmal entweder ein Fehler auf oder Eigenschaften eines nicht ausgewählten Assets werden aktualisiert. (CQ-4316532)
* Beim Versuch, [!UICONTROL Assets Admin Search Rail] zu öffnen, bleibt die Seite leer, und wenn Sie auf [!UICONTROL Bearbeiten] > [!UICONTROL Einstellungen] klicken, wird ein Fehler ausgegeben. (CQ-4315079)
* Wenn nach dem Auflösen des Namenskonflikts eine neue Version eines vorhandenen Assets erstellt wird, werden die Metadaten des ursprünglichen Assets überschrieben. (CQ-4313594)
* Wenn ein Asset mit langem Anmerkungstext gedruckt wird, wird der Anmerkungstext abgeschnitten, auch wenn Leerzeichen vorhanden sind. (CQ-4314101)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Produkt-Experience-Management: Richten Sie Produktkatalogseiten einzeln mit Erlebnisfragmenten ein.

* Die Eigenschaften der Produktkonsole wurden erweitert, um verknüpfte Assets und Erlebnisfragmente anzuzeigen, einschließlich Aktionen zum schnellen Navigieren zu den zugehörigen Inhalten.

* Freigabe der CIF Venia-Referenz-Website 2021.02.24, die die aktuelle CIF-Kernkomponenten Version 1.8.0 enthält. Weitere Informationen finden Sie unter [CIF Venia-Referenz-Website](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2021.02.24).

* Version 1.8.0 von CIF-Kernkomponenten veröffentlicht. Weitere Informationen finden Sie unter [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.8.0).

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Die Version 2021.2.0 von Cloud Manager in AEM as a Cloud Service wurde am 11. Februar 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-cloud-manager}


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

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt}

Das Veröffentlichungsdatum für das Inhaltsübermittlungstool v1.2.4 ist der 10. Februar 2021.

### Fehlerbehebungen {#bug-fixes-ctt}

* Beim Zuordnen mehrerer Benutzer wurden die IMS-IDs einiger Benutzer falsch zugeordnet. Dieses Problem wurde behoben.

### Veröffentlichungsdatum {#release-date-ctt-feb}

Das Content Transfer Tool 1.2.2 wurde am 1. Februar 2021 veröffentlicht.

### Neue Funktionen in Content Transfer Tool {#what-is-new-ctt}

* Neue Funktion und Benutzeroberfläche zum Content Transfer Tool – User Mapping Tool hinzugefügt. Diese Funktion ordnet bestehende Benutzer und Gruppen im Rahmen der Inhaltsmigration automatisch ihren Adobe Identity Management System-IDs zu.
Weitere Informationen finden Sie unter [Verwenden des User Mapping Tools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=de).
* Das Content Transfer Tool migriert jetzt alle Gruppen und Benutzer, auf die im Migrationssatz verwiesen wird, einschließlich untergeordneter Elemente.
* Benutzer können beim Erstellen von Migrationssätzen bestimmte Pfade unter `/etc` auswählen.

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa}

Das Veröffentlichungsdatum für Best Practices Analyzer v2.1.2 ist der 18. Februar 2021.

### Neue Funktionen in Best Practices Analyzer {#what-is-new-bpa}

* Möglichkeit, den Einsatz der AEM Forms- und AEM Forms-Implementierung zu ermitteln und Bereiche anzugeben, die für die Migration nach AEM Forms als Cloud Service relevant sind.
* Möglichkeit, benutzerdefinierte Komponenten und Vorlagen zu erkennen und darüber zu berichten.
* Möglichkeit, den Typ des verwendeten Knotenspeichers und Datenspeichers zu erkennen.
* Möglichkeit, die Nutzung von Dynamic Media zu erkennen.
* Möglichkeit, die verwendete Java-Version zu erkennen.

## Code-Refaktorierungs-Tools {#code-refactoring-tools}

### Neue Funktionen in den Code Refactoring Tools {#what-is-new-crt}

* Neue Version des AIO-CLI-Plug-ins veröffentlicht. Die neueste Version dieses Plugins enthält mehrere Fehlerbehebungen für den Repository Modernizer.
Weitere Informationen zu diesem Plugin finden Sie unter [Unified Experience](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/unified-experience.html?lang=de#benefits).

### Fehlerbehebungen {#bug-fixes-crt}

* Mehrere Fehlerkorrekturen, die im Repository Modernizer vorgenommen wurden.
Siehe [GitHub-Ressource: aem-cloud-service-source-migration](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) für weitere Informationen.
