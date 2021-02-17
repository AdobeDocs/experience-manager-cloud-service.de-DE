---
title: Versionshinweise für Version 2020.9.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: '[!DNL Adobe Experience Manager] as a Cloud Service – Versionshinweise für Version 2020.9.0.'
translation-type: tm+mt
source-git-commit: 13774cc8684166c98f85bf4096d2c7de8d257746
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 100%

---


# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2020.9.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!DNL Experience Manager] as a Cloud Service 2020.9.0 beschrieben.

## Veröffentlichungsdatum {#release-date}

Die Version 2020.9.0 von [!DNL Adobe Experience Manager] as a Cloud Service wurde am Donnerstag, 24. September 2020 veröffentlicht.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Neue Funktionen in [!DNL Sites] {#what-is-new-sites}

* Das JavaScript-SDK für den Single Page Application (SPA)-Editor [ist jetzt Open-Source-basiert.](/help/implementing/developing/hybrid/reference-materials.md)

## [!DNL Adobe Experience Manager Assets] als Cloud Service  {#assets}

### Neue Funktionen in [!DNL Assets] {#what-is-new-assets}

* Bei Ausgabedarstellungen, die mit Asset-Microservices generiert wurden, werden Bilddateien mit Wasserzeichen unterstützt. Sie können als Verarbeitungsprofile konfiguriert werden und verwenden eine PNG-Datei als Wasserzeichen. Siehe [Assets mit Wasserzeichen versehen](/help/assets/watermark-assets.md).

* Verbesserungen in [!DNL Dynamic Media]

   * Selektive Veröffentlichung – Marketing-Teams können nun auf mit [!DNL Dynamic Media] synchronisierte Smart-Crop-Bilder und dynamische Ausgabedarstellungen von [!DNL Dynamic Media] zurückgreifen, um Werbematerial zu erstellen, ohne dass diese Assets für den weltweiten Versand in [!DNL Dynamic Media] veröffentlicht werden müssen. Die [!DNL Experience Manager]- und die [!DNL Dynamic Media]-Veröffentlichung sind entkoppelt und können separat erfolgen, um dies zu erreichen. Siehe [Selektive Veröffentlichung](/help/assets/dynamic-media/selective-publishing.md).
   * Administratoren können jetzt das bei der Bereitstellung erhaltene [!DNL Dynamic Media] Cloud Service-Passwort zurücksetzen. Das Zurücksetzen kann in der Benutzeroberfläche von [!DNL Experience Manager] erfolgen, ohne dass das [!DNL Dynamic Media Classic]-Desktop-Programm verwendet werden muss.

* Weitere Informationen zu den folgenden Verbesserungen finden Sie unter [Neue Funktionen in Brand Portal](https://docs.adobe.com/content/help/de/experience-manager-brand-portal/using/introduction/whats-new.html).

   * Verbesserte PDF-Vorschau mit Adobe Document Cloud View SDK-Integration.
   * Funktion für Downloads mit einem Klick.
   * Neue Verwaltungskonfigurationen für das Download-Erlebnis.

<!--
### Bugs Fixed {#bugs-fixed-assets}

TBD: list of Assets aaCS bugs that are fixed.
-->

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Version 1.3.0 von CIF-Kernkomponenten veröffentlicht. Weitere Informationen finden Sie unter [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.3.0).

* Es gibt nun eine Vorschaufunktion mit Produkt/Kategorie für Produkt- und Kategorievorlagen. So können Geschäftsbenutzer/Marketing-Experten in AEM die Produkt-/Kategorievorlagen mit echten Daten anzeigen.

* Produkten und Kategorien wurde eine Eigenschaftenseite hinzugefügt, damit Geschäftsbenutzer zur Produkt-SKU/Kategorie-ID gehörende Details anzeigen können.

* Der Produktkonsole wurde eine Sortierungsfunktion hinzugefügt wurde, um das Sortieren von Produkten/Kategorien nach Name oder Preisattributen zu ermöglichen.

* Produktsuchfunktion zur Produktkonsole hinzugefügt.

### Fehlerbehebungen {#bug-fixes-commerce}

* Bei Commerce Cloud-Konfigurationen wurde Vererbung nicht berücksichtigt. Dieser Fehler wurde behoben, um sicherzustellen, dass Konfigurationen Werte übernehmen.

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Die Version 2020.9.0 von [!UICONTROL Cloud Manager] wurde am 03. September 2020 veröffentlicht.

### Neue Funktionen {#what-is-new-cloud-manager}

* Inhaltsprüfung wurde in Erlebnisprüfung umbenannt.
* Der Build-Prozess wurde in drei separate Maven-Befehle unterteilt.
* Wenn das Git-Repository nicht geklont werden kann, wird dies bis zu dreimal erneut versucht.

### Fehlerbehebungen {#bug-fixes-cm}

* Auf der Registerkarte „Inhaltsprüfung“ wurde die Basis-URL fälschlicherweise unter Verwendung der Autoren-Domain und nicht der Veröffentlichungs-Domain angezeigt.

## Cloud Readiness Analyzer {#cloud-readiness-analyzer}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für Cloud Readiness Analyzer Version 1.1.0.

### Neue Funktionen {#what-is-new-cra}

* CRA (Cloud Readiness Analyzer) verfügt über eine Anfangsstatuskonsole, die dem Benutzer eine explizite Schaltfläche für **Bericht erstellen** anzeigt, auf die er klicken kann, um CRA auszuführen.

* Die CRA-Benutzeroberfläche zeigt während der Ausführung den Fortschritt an. Sie zeigt Elemente, die gerade analysiert werden, sowie während der Ausführung gefundene Ergebnisse an.

* Der CRA-Bericht enthält eine Zusammenfassung und die Zahl der Ergebnisse in Tabellenform, angeordnet nach Art der Ergebnisse und der Wichtigkeitsstufe. Wenn Sie auf die Zahl eines Ergebnisses klicken, wird automatisch ein Bildlauf zur Position dieses Ergebnisses im Bericht durchgeführt.

### Fehlerbehebungen {#cra-bug-fixes}

* In bestimmten Fällen wurde der CRA-Bericht nach einer erzwungenen Aktualisierung nicht aktualisiert. Dieses Problem wurde in dieser Version behoben.

## Content Transfer-Tool {#content-transfer-tool}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und Updates für das Content Transfer Tool Version 1.1.10.

### Neue Funktionen {#what-is-new-ctt}

* Das Content Transfer Tool (CTT) unterstützt Azure Blob Store-Datenspeicher.

* Die CTT-Benutzeroberfläche bietet eine Funktion zum automatischen Neuladen, mit der die Übersichtsseite alle 30 Sekunden neu geladen wird.

* Schaltfläche zur CTT-Benutzeroberfläche hinzugefügt, damit sich das *Zugriffs-Token* leicht abrufen lässt.

* Beschreibende Validierungsnachricht hinzugefügt zu *URL* und *Migrationssatzname*.

## Code-Refaktorierungs-Tools {#code-refactoring}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und Updates für die Code-Refaktorierungs-Tools.

### Neue Funktionen {#what-is-new-refactoring}

* Das AIO-CLI-Plug-in unterstützt Repository Modernizer und ermöglicht es Benutzern, das Tool mit dem Plug-in auszuführen.

   Weitere Informationen finden Sie unter [Git-Ressource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration).

* Das Dienstprogramm „Repository Modernizer“ kann verwendet werden, um bestehende Projektpakete in Pakete umzustrukturieren, die mit der für AEM as a Cloud Service definierten Projektstruktur kompatibel sind.

   Siehe [Git-Ressource: Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer), um mehr zu erfahren.

