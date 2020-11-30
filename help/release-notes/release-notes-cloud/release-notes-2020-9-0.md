---
title: Versionshinweise für  [!DNL Adobe Experience Manager]  as a Cloud Service 2020.9.0.
description: Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service für 2020.9.0.
translation-type: tm+mt
source-git-commit: db5ca67c583166f4ecb09884a064dfc1378f436e
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 18%

---


# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2020.9.0 {#release-notes}

The following section outlines the general Release Notes for [!DNL Experience Manager] as a Cloud Service 2020.9.0.

## Veröffentlichungsdatum {#release-date}

The Release Date for [!DNL Adobe Experience Manager] as a Cloud Service 2020.9.0 is September 24, 2020.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Neue Funktionen in [!DNL Sites] {#what-is-new-sites}

* Das JavaScript-SDK für die Einzelseitenanwendung (SPA) Editor [ist jetzt Open Source.](/help/implementing/developing/spa/reference-materials.md)

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### Neue Funktionen in [!DNL Assets] {#what-is-new-assets}

* Wasserzeichen-Bilddateien werden für Darstellungen unterstützt, die mit Asset-Mikrodiensten generiert wurden. Es kann als verarbeitendes Profil konfiguriert werden und verwendet eine PNG-Datei als Wasserzeichen. Siehe [Wasserzeichen für Ihre Assets](/help/assets/watermark-assets.md).

* Verbesserungen in [!DNL Dynamic Media]

   * Selektive Veröffentlichung - Ein Marketingteam kann nun auf synchronisierte [!DNL Dynamic Media] Bilder und dynamische Darstellungen zugreifen, um Werbematerial zu erstellen, ohne dass diese Assets für den weltweiten Versand veröffentlicht werden müssen. [!DNL Dynamic Media] [!DNL Dynamic Media] Dies ist möglich. [!DNL Experience Manager] und die [!DNL Dynamic Media] Veröffentlichung ist entkoppelt und kann separat erfolgen, um dies zu erreichen. Siehe [Selektive Veröffentlichung](/help/assets/dynamic-media/selective-publishing.md).
   * Administratoren können jetzt das bei der Bereitstellung erhaltene [!DNL Dynamic Media] Cloud Service-Kennwort zurücksetzen. Das Zurücksetzen kann in der [!DNL Experience Manager] Benutzeroberfläche erfolgen, ohne dass die [!DNL Dynamic Media Classic] Desktop-App verwendet werden muss.

* Weitere Informationen zu den folgenden Verbesserungen finden Sie unter [Neue Funktionen im Markenportal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/whats-new.html).

   * Verbesserte PDF-Vorschau mit Adobe Document Cloud Ansicht SDK-Integration.
   * Download-Funktion mit einem Klick.
   * Neue Verwaltungskonfigurationen für das Download-Erlebnis.

<!--
### Bugs Fixed {#bugs-fixed-assets}

TBD: list of Assets aaCS bugs that are fixed.
-->

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Version 1.3.0 der CIF-Kernkomponenten Weitere Informationen finden Sie unter [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.3.0) .

* Vorschau mit Produkt/Kategorie für Produkt- und Kategorie-Vorlagen ist jetzt verfügbar. Auf diese Weise können Geschäftsbenutzer/Marketingexperten in AEM die Produkt-/Kategorie-Vorlagen mit echten Daten Ansicht werden.

* Eigenschaftenseite zu Produkten und Kategorien hinzugefügt, damit Geschäftsbenutzer Details zur Ansicht der Produkt-SKU/Kategorien-ID eingeben können.

* Sortierungsfunktion, die der Produktkonsole hinzugefügt wurde, um das Sortieren von Produkten/Kategorien nach Namen oder Preisattributen zu ermöglichen.

* Produktsuchfunktion hinzugefügt.

### Fehlerbehebungen {#bug-fixes-commerce}

* Bei den Commerce Cloud-Konfigurationen wurde die Vererbung nicht berücksichtigt. Dieser Fehler wurde behoben, um sicherzustellen, dass die Konfiguration Werte erbt.

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Die Version 2020.9.0 von [!UICONTROL Cloud Manager] wurde am 03. September 2020 veröffentlicht.

### Neuerungen {#what-is-new-cloud-manager}

* Content Audit wurde als Experience Audit umbenannt.
* Der Build-Prozess wurde in drei separate Maven-Befehle unterteilt.
* Wenn das Git-Repository nicht geklont werden kann, wird es bis zu dreimal erneut versucht.

### Fehlerbehebungen {#bug-fixes-cm}

* Auf der Registerkarte &quot;Content Audit&quot;wurde die Basis-URL fälschlicherweise unter Verwendung der Autorendomäne und nicht der Veröffentlichungsdomäne angezeigt.

## Cloud Readiness Analyzer {#cloud-readiness-analyzer}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für Cloud Readiness Analyzer Version 1.1.0.

### Neue Funktionen {#what-is-new-cra}

* Die CRA (Cloud Readiness Analyzer) verfügt über eine Beginn-Statuskonsole, die eine explizite Schaltfläche zum **Generieren eines Berichts** anzeigt, auf die der Benutzer klicken kann, um die CRA auszuführen.

* Die CRA-Benutzeroberfläche zeigt den Fortschritt während der Ausführung an. Es zeigt Elemente an, die analysiert werden, und die während der Ausführung gefundenen Ergebnisse.

* Der CRA-Bericht enthält eine Zusammenfassung und die Anzahl der Ergebnisse in Tabellenform, die nach Art der Befunde und der Wichtigkeitsstufe geordnet sind. Wenn Sie auf die Anzahl dieser Suche klicken, wird automatisch ein Bildlauf zur Position dieser Suche im Bericht durchgeführt.

### Fehlerbehebungen {#cra-bug-fixes}

* In bestimmten Fällen wurde der CRA-Bericht nach der erzwungenen Aktualisierung nicht aktualisiert. Dieses Problem wurde in dieser Version behoben.

## Content Transfer-Tool {#content-transfer-tool}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für Content Transfer Tool Release v1.1.10.

### Neue Funktionen {#what-is-new-ctt}

* Das Content Transfer Tool (CTT) unterstützt den Blue Blob Store Data Store.

* Die CTT-Benutzeroberfläche verfügt über eine Funktion zum automatischen Neuladen, mit der die Übersichtsseite alle 30 Sekunden neu geladen wird.

* Schaltfläche zur CTT-Benutzeroberfläche hinzugefügt, um *Zugriffstoken* schnell abzurufen.

* Beschreibende Überprüfungsmeldung hinzugefügt für *URL* und *Migrationssatzname*.

## Code-Refaktorierungs-Tools {#code-refactoring}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für die Code Refactoring Tools.

### Neue Funktionen {#what-is-new-refactoring}

* Das AIO-CLI-Plugin unterstützt Repository Modernizer und ermöglicht es Benutzern, das Tool mit dem Plugin auszuführen.

   Refer to [Git Resource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) for more details.

* Das Dienstprogramm &quot;Repository Moderner&quot;kann verwendet werden, um bestehende Projektpakete in Pakete umzustrukturieren, die mit der Projektstruktur kompatibel sind, die für AEM als Cloud Service definiert wurde.

   Siehe [Git-Ressource: Repository Moderner](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) für weitere Details.

