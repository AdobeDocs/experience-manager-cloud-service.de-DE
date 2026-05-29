---
title: Neue Funktionen in Content Hub
description: Erfahren Sie mehr über einige der kürzlich eingeführten Content Hub-Funktionen
role: User
badgeSaas: label="AEM Assets" type="Positive" tooltip="Gilt für AEM Assets)."
exl-id: 77a5c54c-bbc5-4dfb-9c3a-aa0620e836d0
source-git-commit: 02f28aef708166b210d5508e714352a800114c14
workflow-type: tm+mt
source-wordcount: '1492'
ht-degree: 58%

---

# Neue Funktionen in Content Hub {#whats-new-content-hub}

Content Hub ist als Teil von Experience Manager Assets as a Cloud Service für die Demokratisierung des Zugriffs auf Markeninhalte für Unternehmen und ihre Geschäftspartner verfügbar. Der Schwerpunkt liegt auf der Verteilung von Assets zur skalierten Aktivierung und der Erstellung von Markeninhaltsvarianten, um die Marketing-Agilität zu verbessern.

Das folgende Video zeigt die wichtigsten Funktionen von Content Hub:

>[!VIDEO](https://video.tv.adobe.com/v/3463712)

>[!IMPORTANT]
>
>[Assets Ultimate](/help/assets/assets-ultimate-overview.md) und Assets as a Cloud Service umfassen 250 Content Hub Limited-Benutzende. [Assets Prime](/help/assets/assets-prime.md) umfasst 50 Content Hub Limited-Benutzende.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der Content Hub-Funktionsveröffentlichung (2026.05.0) ist der 28. Mai 2026 (identisch mit dem der AEM as a Cloud Service-Version). Die nächste Version (2026.06.0) ist für den 25. Juni 2026 geplant.

## Funktionen der Version Mai 2026 {#may-2026-release-features}

**KI-Suche**

AEM Assets Content Hub enthält jetzt KI-Suchen, eine erweiterte Suchfunktion, die die Bedeutung und den Zweck von Benutzerabfragen versteht, anstatt sich nur auf exakte Keyword-Übereinstimmungen zu verlassen. KI-Suche liefert genauere und kontextbezogene Ergebnisse, indem sie die Beziehungen zwischen Wörtern, Konzepten und der Absicht der Benutzenden erkennt. Es unterstützt mehrsprachige Abfragen, verarbeitet Rechtschreibfehler und Tippfehler, versteht Synonyme und zeigt relevante Assets, auch wenn Benutzende keine exakten Metadatenbegriffe verwenden.

Bei einer Suche nach `Woman drinking coffee` können beispielsweise auch Assets zurückgegeben werden, die mit verwandten Begriffen wie `Lady`, `Girl`, `Latte` oder `Cappuccino` getaggt wurden.

Admins können KI-Suchen in Content Hub über das Konfigurationsmenü aktivieren oder deaktivieren, indem sie entweder KI-Suchen oder die herkömmliche Keyword-Suche auswählen.


**Benutzerdefinierte Sortieroptionen**

Mit Content Hub können Admins jetzt benutzerdefinierte Metadatenfelder als Sortieroptionen auf der Content Hub-Startseite aktivieren. Zusätzlich zu den standardmäßigen Sortieroptionen, Größe, Geändert, Name und Relevanz können Admins geschäftsspezifische Metadatenfelder wie Kanal, Region, SKU oder Kampagne konfigurieren, um Benutzenden zu helfen, Suchergebnisse effektiver zu organisieren.

**Asset-Suche und Download-Ereignisunterstützung für Bereitstellungs-APIs**

AEM Assets-Bereitstellungs-APIs unterstützen jetzt die Asset-Suche und Asset-Download-Ereignisse, sodass Unternehmen verfolgen und darauf reagieren können, wie Assets in allen verbundenen Anwendungen und Erlebnissen erkannt und genutzt werden. Diese Ereignisse verbessern die Sichtbarkeit von Asset-Nutzungsmustern, unterstützen Analyse- und Reporting-Workflows und vereinfachen die Integration mit externen Systemen und Automatisierungsprozessen.

Mit ereignisgesteuerten Einblicken können Teams die Interaktion mit Inhalten besser verstehen und vernetztere Workflows für digitale Assets erstellen. Weitere Informationen finden Sie in der [API-Dokumentation](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/asset_downloaded).

>[!IMPORTANT]
>
>Diese Funktionen sind als Funktionen mit begrenzter Verfügbarkeit verfügbar. Sie können [einen Adobe-Support-Fall erstellen und übermitteln](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) um die Funktion für Ihre Bereitstellung zu aktivieren.

## Funktionen der Version Februar 2026 {#february-2026-release-features}

**Berechtigungsverwaltung in Content Hub mit dem AEM Governance Agent**

In Content Hub stellt der AEM Governance Agent sicher, dass nur die richtigen Personen zum richtigen Zeitpunkt auf die richtigen Assets zugreifen. Durch die Anwendung granularer, attributbasierter Steuerelemente und Verwendungsrechte schützt sie sensible Inhalte und ermöglicht gleichzeitig eine sichere Zusammenarbeit. Dies bedeutet weniger Compliance-Risiken, eine stärkere Markenintegrität und schnellere Workflows. Teams können Assets sicher freigeben und wiederverwenden, ohne sich über den unbefugten Zugriff oder Missbrauch Gedanken machen zu müssen. Dieses Gleichgewicht aus Sicherheit und Flexibilität führt zu einer höheren betrieblichen Effizienz und zu mehr Vertrauen im gesamten Unternehmen.

![Übersicht über die Berechtigungsverwaltung](/help/ai-in-aem/agents/governance/assets/permission-management.png)

[!BADGE Weitere Informationen zu dieser Funktion]{type=Informative url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/ai-in-aem/agents/governance/overview#permission-and-digital-rights-management"}


## Funktionen der Version Oktober 2025 {#october-2025-release-features}

**Verbesserungen am Content Hub-Download-Erlebnis**

Content Hub unterstützt jetzt das Herunterladen mehrerer Asset-Ausgabedarstellungen in einer flachen Hierarchie, sodass nicht mehr mehrere Ordner durchsucht werden müssen. Benutzereinstellungen für das Download-Verhalten werden jetzt für ein sitzungsübergreifendes konsistentes Erlebnis beibehalten. Das neue Asset-Download-Erlebnis optimiert das Asset-Management und verbessert die Effizienz, indem heruntergeladene Dateien leichter zu finden und zu organisieren sind.

[!BADGE Weitere Informationen zu dieser Funktion]{type=Informative url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/content-hub/download-assets-content-hub#download-asset-renditions"}

## Funktionen der Version September 2025 {#september-2025-release-features}

**Sammlungen als Favoriten markieren**

Sie können Sammlungen in Content Hub jetzt als Favoriten markieren, was das Organisieren und Abrufen erleichtert. Nach dem Hinzufügen sind Ihre Lieblingssammlungen bequem über die Registerkarte **[!UICONTROL Favoriten]** auf der Content Hub-Startseite verfügbar.

**Sammlungen für schnellen Zugriff anheften**

Content Hub-Administratoren können jetzt Sammlungen in Content Hub anheften, um schnell darauf zugreifen zu können. Angeheftete Sammlungen werden in einem speziellen Abschnitt **[!UICONTROL Angeheftet]** auf der Startseite von Sammlungen angezeigt, wodurch es einfacher ist, wichtige Sammlungen in Reichweite zu halten.

[!BADGE Weitere Informationen zu dieser Funktion]{type=Informative url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/content-hub/collections-content-hub#pin-unpin-collection"}

## Funktionen der Version August 2025 {#august-release-features}

**Massensuche über Filtereigenschaften**

Mit Content Hub können Sie jetzt schneller die benötigten Assets finden. Mit der neuen Funktion für die Massensuche können Sie mehrere Werte für eine beliebige Filtereigenschaft eingeben – getrennt durch ein Trennzeichen (z. B. mehrere SKU-IDs) – und sofort alle übereinstimmenden Assets mit einer einzigen Suche abrufen.

[!BADGE Weitere Informationen zu dieser Funktion]{type=Informative url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/content-hub/search-assets-content-hub#bulk-search"}

## Funktionen der Version Juli 2025 {#july-2025-release-features}

**Verbesserte Branding-Flexibilität in Content Hub**

Aufbauend auf vorhandenen Personalisierungsfunktionen ermöglicht Content Hub Admins jetzt die weitere Anpassung ihrer Bereitstellung, indem sie benutzerdefinierte Logobilder hinzufügen. Die Unterstützung des TIFF-Dateiformats wurde sowohl für Banner- als auch für Logogbilder hinzugefügt, was die Design-Flexibilität erhöht.

[!BADGE Weitere Informationen zu dieser Funktion]{type=Informative url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/content-hub/configure-content-hub-ui-options#configure-branding-content-hub"}

**Intelligentere Freigabe mit benannten Links**

Sie können jetzt beim Generieren eines freigegebenen Links einen Titel hinzufügen – sowohl in der Asset-Detailansicht als auch nach der Auswahl eines oder mehrerer Assets. Auf diese Weise können die Personen, die den Link bekommen, den Zweck jedes Links leicht identifizieren, insbesondere, wenn sie mehrere freigegebene Assets erhalten.

![Privater und öffentlicher Link](/help/assets/assets/shared-link-for-assets.png)

[!BADGE Weitere Informationen zu dieser Funktion]{type=Informative url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/content-hub/share-assets-content-hub"}

**Verbesserte Filternavigation**

Content Hub enthält jetzt in Filtern die Option **Alle anzeigen**, mit der Benutzende alle verfügbaren Facetten zusammen mit der Asset-Anzahl im Zusammenhang mit der aktuellen Einschränkung auf bis zu zehn Facetten anzeigen können. Verbesserte Such- und Sortierfunktionen in jedem Filter erleichtern die effizientere Erkennung und Verwaltung von Assets.

## Funktionen der Version Juni 2025 {#june-2025-release-features}

### Governance von Sammlungen {#collections-governance}

Mit Content Hub können Sie jetzt den Zugriff auf Sammlungen während der Erstellung steuern, sodass sichergestellt wird, dass nur autorisierte Benutzende gruppierte Assets anzeigen oder verwalten können. Dies sorgt für verbesserte Sicherheit, eine bessere Zusammenarbeit, ein organisiertes Asset-Management und eine vereinfachte Governance.

>[!VIDEO](https://video.tv.adobe.com/v/3463336)

[!BADGE Weitere Informationen zu dieser Funktion]{type=Informative url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/content-hub/collections-content-hub#create-collections"}

## Funktionen der Version Mai 2025 {#may-2025-release-features}

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
