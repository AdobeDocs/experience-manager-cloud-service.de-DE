---
title: Fehlerbehebung in AEM Assets und Forms
description: Beheben Sie häufige Probleme mit AEM Assets und Forms mithilfe der Link zu Artikeln für wichtige Bereiche wie Uploads, Metadaten, Suche, Bereitstellung, Formularerstellung, Übermittlung und Integration.
hidefromtoc: true
hide: true
source-git-commit: 5074e777c68c51955b9ad8f055e04067163b9596
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 2%

---


# Fehlerbehebung bei Problemen mit AEM Assets und Forms {#troubleshoot-aem-assets-forms}

AEM as a Cloud Service bietet umfassende Lösungen für Digital Asset Management über AEM Assets und leistungsstarke Formularerstellungsfunktionen über AEM Forms. Beide Services bieten Cloud-native PaaS-Lösungen mit intelligenten Funktionen der nächsten Generation wie KI/ML - alles innerhalb eines Systems, das immer aktuell, immer verfügbar und lernbereit ist.

Komplexe Unternehmensumgebungen können jedoch auf verschiedene technische Herausforderungen in verschiedenen Bereichen stoßen.

Dieses umfassende Handbuch zur Fehlerbehebung bietet systematische Diagnoseansätze, kategorisierte Lösungen und schrittweise Auflösungspfade für AEM Assets und Forms. Jeder Abschnitt enthält Kurzanleitungen, detaillierte Methoden zur Fehlerbehebung und umfassende Links zu Ressourcen, mit denen Sie Probleme effizient beheben und Ihre AEM Cloud Service-Umgebung optimieren können.

## Fehlerbehebung bei AEM Assets {#aem-assets-troubleshooting}

AEM Assets optimiert die Verwaltung, Organisation und Bereitstellung digitaler Assets für unterschiedliche Erlebnisse. Es können jedoch Probleme auftreten, die sich auf Asset-Uploads, Metadaten, Integrationen oder die Bereitstellung auswirken. Dieser Artikel enthält Schritte zur Fehlerbehebung, mit denen Sie häufige AEM Assets-Probleme diagnostizieren und beheben können. Wenn Sie die hier beschriebenen Anleitungen befolgen, können Sie Workflows effizient wiederherstellen und sicherstellen, dass Assets kanalübergreifend zugänglich, genau und einsatzbereit bleiben.

### Asset-Verarbeitung und -Ausgabedarstellungen {#asset-processing-renditions-issues}

<table>
  <tbody>
  <tr>
    <td><strong>Hochladen und Verarbeiten</strong></td>
    <td><strong>Ausgabedarstellungen</strong></td>
    <td><strong>PDF und Textextraktion</strong></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26610">Fehler bei der Asset-Verarbeitung für große MP4-Dateien in AEM as a Cloud Service</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26639">DAM-Ausgabedarstellungen stimmen nicht mit den Originaldateien überein</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26785">AEM kürzt extrahierten Text aus großen PDFs nach 100.000-Token</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-23916">TIFF-Datei mit ZIP-Komprimierungs-Uploads generieren keine Ausgabedarstellungen</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26233">Bilder ohne Miniaturansicht-Ausgabedarstellungen in AEM as a Cloud Service</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25518">Einschränkungen bei der Textextraktion für große PDFs in AEM as a Cloud Service</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-21865">Drag-and-Drop eines Asset-Ordners in die AEM Assets-Web-Benutzeroberfläche schlägt fehl</a></td>
    <td></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26528">Problem mit der Asset-Rotation macht nachfolgende Rotationen unsichtbar</a></td>
  </tr>
  <tr>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26450">Erhöhen der Obergrenze für den Asset-Upload für einzelne Teile für die Photoshop Firefly-API-Integration</a></td>
  <td></td>
  <td></td>
  </tr>
  </tbody>
</table>

### Dynamic Media {#dynamic-media-issues}

<table>
  <tbody>
  <tr>
    <td><strong>Video</strong></td>
    <td><strong>Rotationssets und smartes Zuschneiden</strong></td>
    <td><strong>Versand und Einstellungen</strong></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26533">Beheben von Problemen beim Hochladen, Verarbeiten und Rendern von Videos in AEM</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26715">Rotationssets bleiben im Verarbeitungsstatus hängen</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-17628">Ändern der Dynamic Media-URL für Assets</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26677">Fehlende Übereinstimmung der Videominiaturansicht zwischen Dynamic Media- und DAM-Kartenansicht</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26873">Ausgabedarstellungen für smartes Zuschneiden werden in AEM as a Cloud Service nicht generiert</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26367">Beschädigtes Bildproblem mit smartem Zuschneiden in AEM 6.5</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26610">Fehler bei der Asset-Verarbeitung in AEM Dynamic Media</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26637">Problem mit der Hintergrundfarbe für TIFF-Ausgabedarstellungen</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25294">Die Seite „Allgemeine Dynamic Media-Einstellungen“ wird nicht geöffnet</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26197">Beheben von Audioproblemen in Videodateien mit Dynamic Media</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25885">Fehler bei der Asset-Synchronisierung in Dynamic Media</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26461">Beheben von Diskrepanzen bei Asset-Namen in Umgebungen</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26871">Der Dynamic Media-Video-Player funktioniert in niedrigeren Umgebungen nicht</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25471">Benutzerempfehlungen für die Dynamic Media-Synchronisierung</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26902">Exportieren von Assets und Metadaten aus Dynamic Media mithilfe der -API</a></td>
  </tr>
  </tbody>
</table>

### Metadaten, Tagging und Freigabe {#metadata-tagging-sharing-issues}

<table>
  <tbody>
  <tr>
    <td><strong>Metadaten</strong></td>
    <td><strong>Smart-Tags</strong></td>
    <td><strong>Zugriff und Freigabe</strong></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25828">Diskrepanz bei Bildmetadaten in AEM Assets</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25925">Automatisches Tagging neu hochgeladener Assets</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26928">Eingeschränktes Kommentieren in der Assets-Ansicht trotz Lesezugriff</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26655">Beheben von Problemen mit der Sichtbarkeit von Metadatenschemata für Benutzer ohne Administratorrechte</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25889">Smart-Tags funktionieren nach der Migration von JWT zu OAuth nicht</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25903">Beheben von Problemen mit freigegebenen Links in AEM Managed Services</a></td>
  </tr>

</tbody>
</table>

### Integrationen und Zugriff {#integrations-access}

<table>
  <tbody>
    <tr>
      <td><strong>Asset Link</strong></td>
      <td><strong>Lizenzierung und Anpassungen</strong></td>
    </tr>
    <tr>
      <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26922">Adobe Asset Link lässt Links in InDesign nicht zugänglich</a></td>
      <td>
        <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26616">Inhaltsfragmente sind nicht in der AEM Assets-Lizenz enthalten</a><br>
        </td>
    </tr>
    <tr>
      <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25562">Beheben von Verbindungsproblemen mit AEM Asset Link in InDesign</a></td>
      <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25525">Beheben von Problemen bei der Asset-Verarbeitung in AEM as a Cloud Service</a></td>
    </tr>
    <tr>
      <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25506">Adobe Asset Link Plug-in-Netzwerkfehler: Server nicht erreichbar</a></td>
      <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25829">Aktualisieren von benutzerdefinierten Miniaturansichten für Video-Assets in AEM as a Cloud Service</a>
      </td>
    </tr>
  </tbody>
</table>




## Fehlerbehebung bei AEM Forms {#aem-forms-troubleshooting}

AEM Forms as a Cloud Service bietet leistungsstarke Funktionen zum Erstellen und Verwalten von Formularen. Bei der Installation, Konfiguration, Formularerstellung oder Übermittlung von Formularen können jedoch Probleme auftreten. Dieser Abschnitt enthält umfassende Anleitungen zur Fehlerbehebung bei häufigen AEM Forms-Problemen.

### Installations- und Konfigurationsprobleme

<table>
  <tbody>
  <tr>
    <td><strong>Einrichtung und Konfiguration</strong></td>
    <td><strong>Probleme bei der Formularerstellung</strong></td>
    <td><strong>Leistung und Caching</strong></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-installation-and-configuration.md">Forms-Option in der Navigation nicht verfügbar</a></td>
    <td><a href="/help/forms/form-creation-failing.md">Die Formularerstellung schlägt nach der Vorlagenveröffentlichung fehl</a></td>
    <td><a href="/help/forms/troubleshooting-caching-performance.md">Probleme mit dem Caching von adaptiven Forms</a></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-installation-and-configuration.md#build-pipeline-fails">Fehler beim Erstellen der Pipeline</a></td>
    <td><a href="/help/forms/form-creation-failing.md#cause-form-creation-fails">Sequenzprobleme bei der Vorlagenveröffentlichung</a></td>
    <td><a href="/help/forms/troubleshooting-caching-performance.md#images-videos-not-invalidated">Probleme bei der Cache-Invalidierung in Dispatcher</a></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-installation-and-configuration.md#bundles-inactive-state">Probleme bei der Paketaktivierung</a></td>
    <td><a href="/help/forms/known-issues.md">Bekannte Einschränkungen bei der Formularerstellung</a></td>
    <td><a href="/help/forms/troubleshooting-caching-performance.md#cdn-caching-stops-working-after-300-seconds">CDN-Caching-Fehler</a></td>
  </tr>
  </tbody>
</table>

### Probleme bei der Formularübermittlung und -integration

<table>
  <tbody>
  <tr>
    <td><strong>Edge Delivery Services</strong></td>
    <td><strong>Benutzerdefinierte Übermittlungsaktionen</strong></td>
    <td><strong>Integrationsprobleme</strong></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-403-forbidden-edge-delivery-form-submission.md">403 Unzulässige Fehler bei der Formularübermittlung</a></td>
    <td><a href="/help/forms/custom-submit-action-troubleshooting.md">502 Fehler bei benutzerdefinierten Übermittlungsaktionen</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27434">DRM-SAML-Umleitungsfehler</a></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-403-forbidden-edge-delivery-form-submission.md#cors-issues">CORS-Konfigurationsprobleme</a></td>
    <td><a href="/help/forms/custom-submit-action-troubleshooting.md#resolution">Nicht behandelte Ausnahmebehandlung</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27075">Senden-Schaltfläche in AEM Sites deaktiviert</a></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-403-forbidden-edge-delivery-form-submission.md#referrer-filter-issues">Konfiguration des Referrer-Filters</a></td>
    <td><a href="/help/forms/custom-submit-action-for-adaptive-forms-based-on-core-components.md">Best Practices für benutzerdefinierte Aktionen</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26532">Sichtbarkeit ausgeblendeter Felder nach Upgrades</a></td>
  </tr>
  </tbody>
</table>

### Designer und Entwicklungsprobleme

<table>
  <tbody>
  <tr>
    <td><strong>AEM Forms Designer</strong></td>
    <td><strong>Entwicklungsumgebung</strong></td>
    <td><strong>Version und Kompatibilität</strong></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26558">Designer 6.5 wird nach dem Upgrade nicht geöffnet</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27089">Locators können nicht mit JDK 8/11 beginnen</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26862">Probleme mit der AEM Forms-Paketversion (AEMFD)</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-21018">PDF Generator JPEG 2000-Fehler</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-22689">Konfiguration des JBoss-Protokollpfads</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26846">Falsche Versionsnummern in Windows</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27406">Schaltfläche fehlt in der PDF-Ausgabe</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-18084">Fehler beim Upgrade von Configuration Manager</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-17339">Problemumgehungen bei Indexbeschädigungen</a></td>
  </tr>
  </tbody>
</table>



