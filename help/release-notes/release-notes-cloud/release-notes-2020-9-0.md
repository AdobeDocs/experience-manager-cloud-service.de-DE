---
title: Versionshinweise für  [!DNL Adobe Experience Manager]  as a Cloud Service 2020.9.0.
description: Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service für 2020.9.0.
translation-type: tm+mt
source-git-commit: 701d9ff3c9553c28bce0ef417487facedb22373f
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 18%

---


# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2020.9.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!DNL Experience Manager] als Cloud Service 2020.9.0 beschrieben.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für [!DNL Adobe Experience Manager] als Cloud Service 2020.9.0 ist der 24. September 2020.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Neue Funktionen in [!DNL Sites] {#what-is-new-sites}

* Das JavaScript-SDK für die Einzelseitenanwendung (SPA) Editor [ist jetzt Open Source.](/help/implementing/developing/hybrid/reference-materials.md)

## [!DNL Adobe Experience Manager Assets] als Cloud Service  {#assets}

### Neue Funktionen in [!DNL Assets] {#what-is-new-assets}

* Wasserzeichen-Bilddateien werden für Darstellungen unterstützt, die mit Asset-Mikrodiensten generiert wurden. Es kann als verarbeitendes Profil konfiguriert werden und verwendet eine PNG-Datei als Wasserzeichen. Siehe [Wasserzeichen Ihrer Assets](/help/assets/watermark-assets.md).

* Erweiterungen in [!DNL Dynamic Media]

   * Selektive Veröffentlichung - Ein Marketingteam kann nun auf [!DNL Dynamic Media]-Bilder mit intelligenten Zuschnitten und dynamische Darstellungen zugreifen, die mit [!DNL Dynamic Media] synchronisiert werden, damit sie Werbematerialien erstellen können, ohne diese Elemente für globalen Versand auf [!DNL Dynamic Media] veröffentlichen zu müssen. [!DNL Experience Manager] und die  [!DNL Dynamic Media] Veröffentlichung ist entkoppelt und kann separat erfolgen, um dies zu erreichen. Siehe [selektive Veröffentlichung](/help/assets/dynamic-media/selective-publishing.md).
   * Administratoren können jetzt das [!DNL Dynamic Media]-Kennwort des Cloud Service zurücksetzen, das bei der Bereitstellung erhalten wird. Das Zurücksetzen kann in der [!DNL Experience Manager]-Benutzeroberfläche erfolgen, ohne dass die [!DNL Dynamic Media Classic] Desktop-App verwendet werden muss.

* Informationen zu den folgenden Verbesserungen finden Sie unter [Neue Funktionen im Markenportal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/whats-new.html).

   * Verbesserte PDF-Vorschau mit Adobe Document Cloud Ansicht SDK-Integration.
   * Download-Funktion mit einem Klick.
   * Neue Verwaltungskonfigurationen für das Download-Erlebnis.

<!--
### Bugs Fixed {#bugs-fixed-assets}

TBD: list of Assets aaCS bugs that are fixed.
-->

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Version 1.3.0 der CIF-Kernkomponenten Weitere Informationen finden Sie unter [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.3.0).

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

* Der Cloud-Bereitschaftsanalysator (CRA) verfügt über eine Beginn-Statuskonsole, die eine explizite Schaltfläche **Bericht erzeugen** anzeigt, auf die der Benutzer klicken kann, um die CRA auszuführen.

* Die CRA-Benutzeroberfläche zeigt den Fortschritt während der Ausführung an. Es zeigt Elemente an, die analysiert werden, und die während der Ausführung gefundenen Ergebnisse.

* Der CRA-Bericht enthält eine Zusammenfassung und die Anzahl der Ergebnisse in Tabellenform, die nach Art der Befunde und der Wichtigkeitsstufe geordnet sind. Wenn Sie auf die Anzahl dieser Suche klicken, wird automatisch ein Bildlauf zur Position dieser Suche im Bericht durchgeführt.

### Fehlerbehebungen {#cra-bug-fixes}

* In bestimmten Fällen wurde der CRA-Bericht nach der erzwungenen Aktualisierung nicht aktualisiert. Dieses Problem wurde in dieser Version behoben.

## Content Transfer-Tool {#content-transfer-tool}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für Content Transfer Tool Release v1.1.10.

### Neue Funktionen {#what-is-new-ctt}

* Das Content Transfer Tool (CTT) unterstützt den Blue Blob Store Data Store.

* Die CTT-Benutzeroberfläche verfügt über eine Funktion zum automatischen Neuladen, mit der die Übersichtsseite alle 30 Sekunden neu geladen wird.

* Schaltfläche zur CTT-Benutzeroberfläche hinzugefügt, um *Zugriffstoken* einfach abzurufen.

* Beschreibende Überprüfungsmeldung hinzugefügt für *URL* und *Migrationssatzname*.

## Code-Refaktorierungs-Tools {#code-refactoring}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für die Code Refactoring Tools.

### Neue Funktionen {#what-is-new-refactoring}

* Das AIO-CLI-Plugin unterstützt Repository Modernizer und ermöglicht es Benutzern, das Tool mit dem Plugin auszuführen.

   Siehe [Git-Ressource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration) für weitere Informationen.

* Das Dienstprogramm &quot;Repository Moderner&quot;kann verwendet werden, um bestehende Projektpakete in Pakete umzustrukturieren, die mit der Projektstruktur kompatibel sind, die für AEM als Cloud Service definiert wurde.

   Siehe [Git-Ressource: Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer) für weitere Details.

