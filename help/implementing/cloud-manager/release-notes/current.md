---
title: Versionshinweise für Cloud Manager 2023.11.0 in Adobe Experience Manager as a Cloud Service
description: Dies sind die Versionshinweise für Cloud Manager 2023.11.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 4e2ea040ec14515525424b42f524601d34786cb8
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 14%

---


# Versionshinweise für Cloud Manager 2023.11.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise zu Cloud Manager 2023.11.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Version 2023.11.0 von Cloud Manager in AEM as a Cloud Service wurde am 14. November 2023 veröffentlicht. Die nächste Version wurde am 7. Dezember 2023 veröffentlicht.

## Neue Funktionen {#what-is-new}

* Der Schutz der Web Application Firewall-DDOS (WAF-DDOS) ist jetzt im Rahmen Ihrer AEM as a Cloud Service Berechtigungen zum Kauf verfügbar. [kann auf Self-Service-Art konfiguriert werden.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)
* Spezialisiert [Konfigurations-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) sind jetzt verfügbar, um innerhalb von Minuten Traffic-Filterregeln, einschließlich WAF-Regeln, zu konfigurieren und bereitzustellen.
* [Beim Kopieren von Inhalten](/help/implementing/developing/tools/content-copy.md) von einer höheren Umgebung in eine Entwicklungsumgebung zu übertragen, wird jetzt eine Meldung angezeigt, die beim Kopieren großer Inhaltssets Vorsicht weckt, da die Entwicklungsumgebungen nur über eine begrenzte Kapazität verfügen.
* [Seite mit Details zur Pipelineausführung](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details) zeigt nun alle Schritte in einer Pipeline-Ausführung an, bei denen die Schritte noch nicht ausgegraut wurden.
* Bei beiden **[Aktivität](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#activity)** und **[Pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#pipelines)** Seiten enthält, ist jetzt eine Zusammenfassung der Pipeline-Ausführung verfügbar, wenn auf eine Pipeline mit einem Ausführungsstatus geklickt wird.
* Eine neue **Dauer** wurde zum Abschnitt [Pipeline-Detailseite](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details) , die die durchschnittliche Dauer des Pipeline-Schritts basierend auf dem historischen Trend für dieses Programm enthält.
* Im [Pipeline-Ausführungsseite,](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#activity-window) Die abgeschlossenen Schritte zeigen nun die Dauer an.
* Ausführungen, die [Build-Artefakte wiederverwenden](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) zeigt nun den Link zur Ausführung, die diese Artefakte ursprünglich erstellt hat.
* Die ausgewählte Option **Wichtige Metrikfehler** kann jetzt konfiguriert werden für [Code-Qualitäts-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) sowie.


## Frühzeitige Annahme des Programms {#early-adoption}

Nehmen Sie an unserem Programm teil und haben Sie die Möglichkeit, einige bevorstehende Funktionen zu testen.

### Erstellen Sie Ihren eigenen GitHub {#byo-github}

Wenn Sie Ihre Repositorys mit GitHub verwalten, [Sie können jetzt Code direkt in Ihren GitHub-Repositorys über Cloud Manager validieren.](/help/implementing/cloud-manager/managing-code/byo-github.md) Durch diese Integration entfällt die Notwendigkeit, Code konsistent mit dem Adobe-Repository zu synchronisieren, und Sie können Pull-Anforderungen überprüfen, bevor Sie sie in die Hauptverzweigungen zusammenführen.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte eine E-Mail an `Grp-CloudManager_BYOG@adobe.com` von Ihrer mit Ihrer Adobe ID verknüpften E-Mail-Adresse aus.

### Benutzerdefinierte Berechtigungen {#custom-permissions}

[Benutzerdefinierte Berechtigungen für Cloud Manager](/help/implementing/cloud-manager/custom-permissions.md) können Sie neue benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen, um den Zugriff auf Programme, Pipelines und Umgebungen für Cloud Manager-Benutzer zu beschränken.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte eine E-Mail `Grp-CloudManager-custom-permissions@adobe.com` von Ihrer mit Ihrer Adobe ID verknüpften E-Mail-Adresse aus.

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

## Bekannte Probleme {#known-issues}

Es gibt einen bekannten Fehler, der verhindert [Konfigurations-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md##config-deployment-pipeline) von in die Produktion verschoben werden.

Wenn die Variable **Anhalten vor der Bereitstellung in der Produktion** -Option für eine Konfigurations-Pipeline erforderlich ist, ist die folgende empfohlene Problemumgehung, bis der Fehler behoben ist.

1. Pipeline ausführen.
1. Testen Sie den Code in der Staging-Umgebung.
1. Wenn die Bereitstellung und Genehmigung verfügbar ist, klicken Sie auf **Ablehnen**.
1. Bearbeiten Sie die Pipeline, um die **Anhalten vor der Bereitstellung in der Produktion** -Option.
1. Führen Sie die Pipeline erneut aus. Es wird erneut beim Staging und dann bei der Produktion ausgeführt.
