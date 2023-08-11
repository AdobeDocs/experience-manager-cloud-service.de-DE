---
title: Versionshinweise für Cloud Manager 2023.8.0 in Adobe Experience Manager as a Cloud Service
description: Dies sind die Versionshinweise für Cloud Manager 2023.8.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 99772a1a3faa454a9b07dd92c9e7622ddb37ce2d
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 21%

---


# Versionshinweise für Cloud Manager 2023.8.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise zu Cloud Manager 2023.8.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Siehe [diese Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) für die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Version 2023.8.0 von Cloud Manager in AEM as a Cloud Service wurde am 10. August 2023 veröffentlicht. Die nächste Version wird am 7. September 2023 veröffentlicht.

## Neue Funktionen {#what-is-new}

* Beim Konfigurieren eines Inhalts, der auf [Inhalt kopieren,](/help/implementing/developing/tools/content-copy.md) [kontextbezogene Konfigurationen](/help/implementing/developing/introduction/configurations.md) sind jetzt in Inhaltssätzen in der Benutzeroberfläche zulässig.
* Es wurden Verbesserungen vorgenommen, um die Verständlichkeit und das Erscheinungsbild von Fehlermeldungen in der Cloud Manager-Benutzeroberfläche zu verbessern.

## Frühzeitige Annahme des Programms {#early-adoption}

Nehmen Sie an unserem Programm teil und haben Sie die Möglichkeit, einige bevorstehende Funktionen zu testen.

### Self-Service Content Restore {#content-restore}

[Neue Funktion zur Wiederherstellung von Self-Service-Inhalten](/help/operations/restore.md) bietet jetzt eine Backup-Wiederherstellung für bis zu sieben Tage und steht frühen Anwendern zu Auswertungszwecken zur Verfügung:

* Point-in-Time-Backup-Wiederherstellung für die letzten 24 Stunden
* Feste Zeitwiederherstellung für bis zu sieben Tage

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte eine E-Mail an `aemcs-restorefrombackup-adopter@adobe.com` aus Ihrer mit Ihrer Adobe ID verknüpften E-Mail. Hinweis:

* Das Programm für den frühen Anwender ist auf Entwicklungsumgebungen beschränkt.
* Die Verfügbarkeit des frühen Adopter-Programms dieser Funktion ist begrenzt.
* Diese Funktion dient zum Wiederherstellen versehentlich gelöschter Inhalte und ist nicht für die Notfallwiederherstellung vorgesehen.

### Experience Audit-Dashboard {#experience-audit-dashboard}

[Das Dashboard &quot;Experience Audit&quot;von Cloud Manager](/help/implementing/cloud-manager/experience-audit-dashboard.md) enthält eine Trendansicht Ihrer Seitenleistungsbewertungen sowie Einblicke und Empfehlungen, die Sie bei der Verbesserung unterstützen. Experience Audit ist ein Schritt in der Produktions-Pipeline von Cloud Manager.

Das Dashboard nutzt Google Lighthouse, ein Open-Source-Tool zur Verbesserung der Qualität Ihrer Web-Apps. Sie können sie für jede Web-Seite ausführen, öffentlich oder authentifizierungspflichtig. Sie enthält Prüfungen zu Leistung, Barrierefreiheit, progressiven Web-Apps, SEO und mehr.

Möchten Sie das neue Dashboard testen? Bitte senden Sie eine E-Mail an `aem-lighthouse-pilot@adobe.com` von Ihrer mit Ihrer Adobe ID verknüpften E-Mail aus und wir können Ihnen den Einstieg erleichtern.

## Fehlerbehebungen {#bug-fixes}

* Die **Umgebungen** Menü wird nun geschlossen, nachdem die **[Inhalt kopieren](/help/implementing/developing/tools/content-copy.md)** modal.
* [Neuausführung einer Pipeline](/help/implementing/cloud-manager/deploy-code.md#reexecute-deployment) ist nicht mehr zulässig, wenn die vorherige Ausführung nicht über eine `commitId` wird auf den Build-Phase-Status gesetzt.
* Für seltene Fehler wird jetzt eine verständlichere Meldung angezeigt, wenn ein Benutzer auf eine Pipeline in der **Aktivität** oder **Pipeline** Bildschirme.
* Die `contentSetName` -Wert fehlt nicht mehr in den Protokollen und wird jetzt beim Starten einer [Inhaltskopie](/help/implementing/developing/tools/content-copy.md) Vorgang.
* Unter bestimmten seltenen Umständen ist es nicht mehr möglich, zwei Ausführungen derselben Pipeline zu starten, die zu einem &quot;blockierten&quot;Zustand führen.
* Wenn ein Zertifikat abläuft, werden die mit dem Zertifikat verknüpften Domänennamen und IP-Zulassungslisten nicht mehr aus dem CDN entfernt.
   * In solchen Fällen ist die Site weiterhin erreichbar.
   * [](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)Die Benutzeroberfläche von Cloud Manager bietet sichtbarere Warnhinweise, dass das SSL-Zertifikat bald abläuft.
* Ein Problem mit dem AEM, den Zugriff auf einen Veröffentlichungsendpunkt zu verlieren, wurde in Situationen behoben, in denen Sites als Lösung für ein Programm &quot;Nur Assets&quot;hinzugefügt wurde.
