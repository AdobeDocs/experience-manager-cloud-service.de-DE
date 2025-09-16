---
title: Neue Funktionen in Content Hub
description: Erfahren Sie mehr über einige der kürzlich eingeführten Content Hub-Funktionen
role: User
exl-id: 77a5c54c-bbc5-4dfb-9c3a-aa0620e836d0
source-git-commit: 62ac097fca0142265f2e1ef28117619d59045e6c
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 99%

---

# Neue Funktionen in Content Hub {#whats-new-content-hub}

Content Hub ist als Teil von Experience Manager Assets as a Cloud Service für die Demokratisierung des Zugriffs auf Markeninhalte für Unternehmen und ihre Geschäftspartner verfügbar. Der Schwerpunkt liegt auf der Verteilung von Assets zur skalierten Aktivierung und der Erstellung von Markeninhaltsvarianten, um die Marketing-Agilität zu verbessern.

Das folgende Video zeigt die wichtigsten Funktionen von Content Hub:

>[!VIDEO](https://video.tv.adobe.com/v/3463712)

>[!IMPORTANT]
>
>[Assets Ultimate](/help/assets/assets-ultimate-overview.md) und Assets as a Cloud Service umfassen 250 Content Hub Limited-Benutzende. [Assets Prime](/help/assets/assets-prime.md) umfasst 50 Content Hub Limited-Benutzende.

## Veröffentlichungsdatum {#release-date}

Das Datum der Content Hub-Funktionsveröffentlichung (2025.8.0) ist der 28. August 2025 (identisch mit dem der AEM as a Cloud Service-Version). Die nächste Version mit neuen Funktionen (2025.9.0) ist für den 25. September 2025 geplant.

## Funktionen der August-Version {#august-release-features}

**Massensuche über Filtereigenschaften**

Mit Content Hub können Sie jetzt schneller die benötigten Assets finden. Mit der neuen Funktion für die Massensuche können Sie mehrere Werte für eine beliebige Filtereigenschaft eingeben – getrennt durch ein Trennzeichen (z. B. mehrere SKU-IDs) – und sofort alle übereinstimmenden Assets mit einer einzigen Suche abrufen.

[!BADGE Weitere Informationen zu dieser Funktion]{type=Informative url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/content-hub/search-assets-content-hub#bulk-search"}

## Funktionen der Juli-Version {#july-release-features}

**Verbesserte Branding-Flexibilität in Content Hub**

Aufbauend auf vorhandenen Personalisierungsfunktionen ermöglicht Content Hub Admins jetzt die weitere Anpassung ihrer Bereitstellung, indem sie benutzerdefinierte Logobilder hinzufügen. Die Unterstützung des TIFF-Dateiformats wurde sowohl für Banner- als auch für Logogbilder hinzugefügt, was die Design-Flexibilität erhöht.

[!BADGE Weitere Informationen zu dieser Funktion]{type=Informative url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/content-hub/configure-content-hub-ui-options#configure-branding-content-hub"}

**Intelligentere Freigabe mit benannten Links**

Sie können jetzt beim Generieren eines freigegebenen Links einen Titel hinzufügen – sowohl in der Asset-Detailansicht als auch nach der Auswahl eines oder mehrerer Assets. Auf diese Weise können die Personen, die den Link bekommen, den Zweck jedes Links leicht identifizieren, insbesondere, wenn sie mehrere freigegebene Assets erhalten.

![Privater und öffentlicher Link](/help/assets/assets/shared-link-for-assets.png)

[!BADGE Weitere Informationen zu dieser Funktion]{type=Informative url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/content-hub/share-assets-content-hub"}

**Verbesserte Filternavigation**

Content Hub enthält jetzt in Filtern die Option **Alle anzeigen**, mit der Benutzende alle verfügbaren Facetten zusammen mit der Asset-Anzahl im Zusammenhang mit der aktuellen Einschränkung auf bis zu zehn Facetten anzeigen können. Verbesserte Such- und Sortierfunktionen in jedem Filter erleichtern die effizientere Erkennung und Verwaltung von Assets.

## Funktionen der Juni-Version {#june-release-features}

### Governance von Sammlungen {#collections-governance}

Mit Content Hub können Sie jetzt den Zugriff auf Sammlungen während der Erstellung steuern, sodass sichergestellt wird, dass nur autorisierte Benutzende gruppierte Assets anzeigen oder verwalten können. Dies sorgt für verbesserte Sicherheit, eine bessere Zusammenarbeit, ein organisiertes Asset-Management und eine vereinfachte Governance.

>[!VIDEO](https://video.tv.adobe.com/v/3463336)

[!BADGE Weitere Informationen zu dieser Funktion]{type=Informative url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/content-hub/collections-content-hub#create-collections"}

## Funktionen der Mai-Version {#may-release-features}

Die Mai-Version von Content Hub umfasst die folgenden Funktionen:

* [Attributbasierte Zugriffssteuerung](#attribute-based-access-control)

* [UI-Branding](#ui-branding)

* [Öffentliche Link-Freigabe](#public-link-sharing)

* [Mehrere Assets als ZIP-Datei herunterladen](#download-multiple-assets-as-zip)

* [Dynamic Media-Ausgabedarstellungen in Content Hub](#dynamic-media-renditions)

### Attributbasierte Zugriffssteuerung (Attribute-based Access Control, ABAC) {#attribute-based-access-control}

Mit Content Hub können Sie jetzt regelbasierte Einschränkungen für den Zugriff auf Assets anwenden. Asset-Berechtigungen gewährleisten die Governance und stellen außerdem sicher, dass nur die relevanten Assets für Benutzende zugänglich sind.

Die Regeln für die Asset-Einschränkung basieren auf Metadaten. Wenn die Asset-Metadaten den in der Regel definierten Bedingungen entsprechen, wird das Asset den Benutzergruppen angezeigt.

Zu den wichtigsten Vorteilen der attributbasierten Zugriffssteuerung gehören:

* Beseitigt die Abhängigkeit von der Ordnerstruktur für Berechtigungen

* Ermöglicht es Admins, Assets hochzuladen und Berechtigungsstrukturen rückwirkend zu bestimmen

* Reduziert die Anzahl der Duplikate – verbessert die Integrität der Assets. Duplikate sind in ordnerbasierten Berechtigungen erforderlich, wenn dieselben Assets für verschiedene Gruppen freigegeben werden.

[!BADGE Weitere Informationen zu dieser Funktion]{type=Informative url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/content-hub/attribute-based-access-control"}

### UI-Branding {#ui-branding}

Content Hub ermöglicht es Admins jetzt, die Benutzeroberfläche mit markenspezifischen Elementen anzupassen, einschließlich Bannerbildern, Bannertiteln und des Textkörpers sowie Primär- und Sekundärfarben. Diese Verbesserungen tragen dazu bei, Markenkonsistenz zu gewährleisten, das Onboarding von Benutzenden zu vereinfachen und Vertrauen aufzubauen.

![UI-Branding](/help/assets/assets/content-hub-ui-branding.png)

[!BADGE Weitere Informationen zu dieser Funktion]{type=Informative url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/content-hub/configure-content-hub-ui-options#configure-branding-content-hub"}

### Öffentliche Link-Freigabe {#public-link-sharing}

Content Hub unterstützt jetzt das Generieren von freigabefähigen Links, damit externe Benutzende ohne Programmzugriff Asset-Metadaten anzeigen oder Assets herunterladen können.

![UI-Branding](/help/assets/assets/public-and-private-link.png)

[!BADGE Weitere Informationen zu dieser Funktion]{type=Informative url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/content-hub/share-assets-content-hub"}

### Mehrere Assets als ZIP-Datei herunterladen {#download-multiple-assets-as-zip}

Mit Content Hub können Sie jetzt auch die ausgewählten Assets und ihre Ausgabedarstellungen in einer ZIP-Datei herunterladen und nicht als separate Dateien, was die Dateiverwaltung für Sie vereinfacht.

[!BADGE Weitere Informationen zu dieser Funktion]{type=Informative url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/content-hub/download-assets-content-hub#download-asset-renditions"}

### Dynamic Media-Ausgabedarstellungen in Content Hub {#dynamic-media-renditions}

Greifen Sie direkt über die Benutzeroberfläche von Content Hub auf alle voreingestellten Dynamic Media-Ausgabedarstellungen und intelligenten Zuschnitte zum Herunterladen zu.

![Dynamic Media-Ausgabedarstellungen](/help/assets/assets/dm-renditions-content-hub.png)

[!BADGE Weitere Informationen zu dieser Funktion]{type=Informative url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/content-hub/download-assets-content-hub#download-asset-renditions"}
