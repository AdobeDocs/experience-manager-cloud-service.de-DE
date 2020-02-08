---
title: Bekannte Probleme
description: Versionshinweise zu bekannten Problemen mit Adobe Experience Manager als Cloud-Dienst
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# Bekannte Probleme {#known-issues}

In diesem Artikel werden die bekannten Probleme mit Adobe Experience Manager als Cloud-Service-Angebot aufgeführt. Die Liste wird mit jeder kontinuierlichen Version von Experience Manager überarbeitet und aktualisiert.

[Wenden Sie sich an den Support](https://helpx.adobe.com/support/experience-manager.html) , um weitere Informationen zu den bekannten Problemen zu erhalten.

<!-- 
## Platform {#platform}

## Sites {#sites}
-->

## Assets {#assets}

<!-- Jira label: assets-cloud-known-issues -->

Einige bekannte Probleme sind:

* **Metadatenschema**: Das Widget zur Asset-Bewertung kann einen JSP-Kompilierungsfehler verursachen. Eine Lösung besteht darin, die Asset-Bewertungskomponente aus dem Metadatenschema zu entfernen. <!-- CQ-4282865 -->

Einige Einschränkungen der Assets-Funktion sind:

* Bei AEM Assets als Cloud-Dienst funktioniert die Funktion &quot;Verbundene Assets&quot;, wenn AEM 6.5 Sites auf AMS bereitgestellt werden.

### Funktionen für bevorstehende Assets {#upcoming-assets-capabilities}

Einige Funktionen von Adobe Experience Manager-Assets, die von den Grundfunktionen abhängen, die noch nicht in Experience Manager als Cloud-Service-Bereitstellungsarchitektur verfügbar sind, werden voraussichtlich zu einem späteren Zeitpunkt aktiviert:

* Das Veröffentlichen im Markenportal ist derzeit nicht aktiviert. Sie können die Implementierung von [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/) erweitern und für die Asset-Verteilung bereitstellen.
* Erweiterte Funktionen für intelligentes Tagging, die AI-Dienste von Adobe I/O nutzen, sind derzeit nicht verfügbar.
* Aufgrund der Abhängigkeit von Commerce Integration Framework-APIs sind Funktionen derzeit nicht aktiviert:
   * Fotografieren von Workflow-Modellen
   * Die Registerkarte &quot;Produktinformationen&quot;in der Benutzeroberfläche der Asset-Eigenschaften wird nicht ausgefüllt.
* Funktionen sind derzeit aufgrund der Abhängigkeit von der InDesign Server-Integration nicht aktiviert:
   * Asset-Vorlagen und Asset-Kataloge.
   * Mehrseitige Vorschau von InDesign-Dateien.

>[!MORELIKETHIS]
>
>* [Wichtige Änderungen in AEM](aem-cloud-changes.md)
>* [Veraltete und entfernte Funktionen](deprecated-removed-features.md)
>* [Versionshinweise;](home.md)

