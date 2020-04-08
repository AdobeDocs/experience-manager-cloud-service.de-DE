---
title: Versionshinweise für Version 2020.4.0
description: Versionshinweise für Version 2020.4.0
translation-type: tm+mt
source-git-commit: c6c0e93d881762a2b501abb3d8c8356046a5f082

---


# Release Notes for AEM as a Cloud Service 2020.4.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager als Cloud-Dienst 2020.4.0 beschrieben.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für Experience Manager als Cloud-Dienst 2020.4.0 ist der 9. April 2020.

## Assets {#assets}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für Experience Manager Assets und dynamische Medien in AEM als Cloud-Service-Version 2020.4.0.

### Neuerungen {#assets-what-is-new}

* [Markenportal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) ist für AEM als Cloud-Dienst-Assets verfügbar und unterstützt Anwendungsfälle für die Asset-Verteilung. Brand Portal unterstützt Unternehmen dabei, ihre Marketing-Anforderungen zu erfüllen, indem zugelassene Marken- und Produktressourcen sicher zum Herunterladen an externe Agenturen, Partner, interne Teams und Wiederverkäufer verteilt werden.
   * Die Konfiguration des Markenportals erfolgt über die Adobe I/O-Konsole.
   * Die Asset-Beschaffung im Markenportal wird von AEM als Cloud-Dienst noch nicht unterstützt
* Die neue Version von [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) 2.0 wird von AEM als Cloud-Dienst unterstützt. Adobe Asset Link optimiert die Zusammenarbeit zwischen Kreativen und Marketingexperten bei der Inhaltserstellung, indem AEM Assets über das In-App-Bedienfeld &quot;Asset-Link&quot;mit den Creative Cloud-Desktop-Apps Fotoshop, Illustrator und InDesign verknüpft werden.
   * AEM als Cloud-Dienst ist für Adobe Asset Link vorkonfiguriert, was zu einer [vereinfachten Konfiguration](https://helpx.adobe.com/enterprise/using/configure-aem-assets-for-asset-link.html)führt.
   * Asset Link unterstützt jetzt einen [AEM Umgebung-Umschalter](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink), der es kreativen Benutzern ermöglicht, sich einfacher mit verschiedenen AEM-Umgebungen zu verbinden (z. B. bei Agenturen, die mit mehreren Clients mit AEM Assets arbeiten)
* Der automatische Beginn für [Arbeitsabläufe](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) nach der Verarbeitung kann in der Benutzeroberfläche &quot;Ordnereigenschaften&quot;für bestimmte Ordnerhierarchien konfiguriert werden.
   * Die Benutzeroberfläche &quot;Ordnereigenschaften&quot;wurde vereinfacht. Die neue Registerkarte &quot;Asset-Verarbeitung&quot;enthält Metadaten-Profil, Profil für die Verarbeitung und die neue Konfiguration des Arbeitsablaufs für den automatischen Beginn
* Das Dialogfeld zur Asset-Wiederaufarbeitung ermöglicht die Auswahl eines bestimmten verarbeitenden Profils und die Entscheidung, die Verarbeitung in Unterordnern erneut durchzuführen
* Dynamische Medien: Die Konfiguration für selektive Veröffentlichung wurde hinzugefügt. Das bedeutet, dass Assets nur zur sicheren Vorschau automatisch veröffentlicht werden und explizit in AEM veröffentlicht werden können, ohne DMS7 für Versand in der öffentlichen Domäne zu veröffentlichen.

### Fehlerbehebungen  {#assets-bug-fixes}

* Fehlerbehebungen in der Asset-Verarbeitung
* Fehlerbehebungen in der Konfiguration von Dynamischen Medien und beim Veröffentlichen von Assets im Dynamischen Media Versand-Dienst
