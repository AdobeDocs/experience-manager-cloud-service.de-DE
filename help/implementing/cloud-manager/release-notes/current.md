---
title: Versionshinweise für Cloud Manager 2025.5.0
description: Erfahren Sie mehr über die Version Cloud Manager 2025.5.0 in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 12388df411b9bf0693358a82de17fec90d83877a
workflow-type: tm+mt
source-wordcount: '1050'
ht-degree: 16%

---

# Versionshinweise für Cloud Manager 2025.5.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

Erfahren Sie mehr über die Version Cloud Manager 2025.5.0 in AEM (Adobe Experience Manager) as a Cloud Service.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Die Version 2025.5.0 von Cloud Manager in AEM as a Cloud Service wurde am Donnerstag, dem Freitag, 8. Mai 2025 veröffentlicht.

Die Veröffentlichung der nächsten Version ist für Donnerstag, den Freitag, 5. Juni 2025 geplant.

## Neue Funktionen {#what-is-new}

### Konfigurieren der Inhaltsquelle für Edge Delivery Services mit einem Klick

Adobe Experience Manager (AEM) Edge Delivery Services ermöglicht die Bereitstellung von Inhalten aus mehreren Quellen wie Google Drive, SharePoint oder AEM selbst mithilfe eines schnellen, global verteilten Edge-Netzwerks.

Die Konfiguration der Inhaltsquellen unterscheidet sich zwischen Helix 4 und Helix 5 wie folgt:

| Version | Konfigurationsmethode der Inhaltsquelle |
| --- | --- |
| Helix 4 | YAML-Datei (`fstab.yaml`) |
| Helix 5 | Konfigurations-Service-API (*keine`fstab.yaml`*) |

Dieser Artikel enthält umfassende Konfigurationsschritte, Beispiele und Validierungsanweisungen für beide Versionen.

**Bevor Sie beginnen**

Wenn Sie Edge Delivery mit [ Klick in Cloud Manager verwenden, ](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md##one-click-edge-delivery-site) Ihre Website Helix 5 mit einem einzigen Repository. Befolgen Sie die Helix 5-Anweisungen und verwenden Sie die bereitgestellte Helix 4 YAML-Version der Anweisungen als Ausweichlösung.

**Helix-Version ermitteln**

* Helix 4: Ihr Projekt enthält eine `fstab.yaml`.
* Helix 5: Ihr Projekt ** verwendet keine `fstab.yaml` und wurde über die Edge Delivery Services-Benutzeroberfläche oder -API eingerichtet.

Bestätigen Sie dies anhand der Repository-Metadaten oder wenden Sie sich an Ihren Administrator, wenn Sie sich noch nicht sicher sind.

#### Konfigurieren der Inhaltsquelle für Helix 4

In Helix 4 definiert die Datei fstab.yaml die Inhaltsquelle für Ihre Site. Diese Datei befindet sich im Stammverzeichnis Ihres GitHub-Repositorys und ordnet URL-Pfadpräfixe (so genannte mountpoints) externen Inhaltsquellen zu. Ein typisches Beispiel sieht wie folgt aus:

```yaml
mountpoints:
  /: https://drive.google.com/drive/folders/your-folder-id
```

Dieses Beispiel dient nur zur Veranschaulichung. Die eigentliche URL sollte auf Ihre Inhaltsquelle verweisen, z. B. auf einen Google Drive-Ordner, einen SharePoint-Ordner oder einen AEM-Pfad.

**So konfigurieren Sie die Inhaltsquelle für Helix 4:**

Die Schritte variieren je nach verwendetem Quellsystem.

* **Google Drive**

   1. Erstellen Sie einen Google Drive-Ordner.
   1. Freigeben des Ordners für `helix@adobe.com`.
   1. Abrufen des Links für freigebbare Ordner .
   1. Aktualisieren Sie Ihre `fstab.yaml` wie folgt:

      ```yaml
      mountpoints: 
          /: https://drive.google.com/drive/folders/<folder-id>
      ```

   1. Übertragen Sie Änderungen und übertragen Sie sie auf GitHub.

* **SharePoint**

   1. Erstellen Sie einen SharePoint-Ordner oder eine Dokumentbibliothek.
   1. Freigeben des Zugriffs für `helix@adobe.com`
   1. Abrufen der Ordner-URL.
   1. Aktualisieren Sie Ihre `fstab.yaml` wie folgt:

      ```yaml
      mountpoints:
        /: https://<tenant>.sharepoint.com/sites/<site>/Shared%20Documents/<folder>
      ```

   1. Übertragen Sie Änderungen und übertragen Sie sie auf GitHub.

* **AEM**

   1. Identifizieren Sie Ihren AEM-Inhaltspfad.
   1. Verwenden Sie die AEM-Inhaltsexport-URL wie folgt:

      ```yaml
      mountpoints:
        /: https://author.<your-aem-instance>.com/bin/franklin.delivery/<org>/<repo>/main
      ```

   1. Übertragen Sie Änderungen und übertragen Sie sie auf GitHub.

##### Validierung

* Klicken Sie mithilfe der AEM Sidekick Chrome-Erweiterung auf **Vorschau** > **Veröffentlichen** > **Live-Site testen**.
* URL validieren: `https://main--<repo>--<org>.hlx.page/`

#### Konfigurieren der Inhaltsquelle für Helix 5

Helix 5 ist reaktionslos, verwendet keine `fstab.yaml` und unterstützt mehrere Websites, die dasselbe Verzeichnis gemeinsam nutzen. Die Konfiguration wird über die Konfigurations-Service-API oder die Edge Delivery Services-Benutzeroberfläche verwaltet. Die Konfiguration erfolgt auf Site-Ebene (nicht auf Repository-Ebene).

Die konzeptionellen Unterschiede sind:

| Aspekt | Helix 4 | Helix 5 |
| --- | --- | --- |
| Konfiguration | Erledigt durch `fstab.yaml` | Erledigt über die API oder die Benutzeroberfläche anstelle von YAML. |
| Bereitstellungspunkte | Definiert in `fstab.yaml`. | Nicht erforderlich. Der Stamm wird implizit verstanden. |

**So konfigurieren Sie die Inhaltsquelle für Helix 5:**

1. Authentifizieren Sie sich mithilfe der Konfigurations-Service-API über einen API-Schlüssel oder ein Zugriffstoken.
1. Führen Sie den folgenden `PUT`-API-Aufruf aus:

   ```bash {.line-numbering}
   PUT /api/{program}/{programId}/site/{siteId}
   Content-Type: application/json
   
   {
     "sitename": "my-site",
     "branchName": "main",
     "version": "v5",
     "repo": "my-content-repo-link"
   }
   ```

1. Antwort validieren (erwartet: HTTP 200 OK).

##### Validierung

* Klicken Sie mithilfe der AEM Sidekick Chrome-Erweiterung auf **Vorschau** > **Veröffentlichen** > **Live-Site testen**.
* URL validieren: `https://main--<repo>--<org>.aem.page/`
* (Optional) Überprüfen Sie die aktuelle Konfiguration mithilfe des folgenden `GET`-API-Aufrufs:

  ```bash
  GET /api/{program}/{programId}/site/{siteId}
  ```

<!--
* **AI-powered build summaries now available for internal use**

    Internal users can now use AI-powered build summaries to simplify build log analysis. The feature provides actionable recommendations and helps identify the root causes of build failures.

    ![Build Summary dialog box](/help/implementing/cloud-manager/release-notes/assets/build-summary.png)
-->


## Early-Adopter-Programm {#early-adoption}

Nehmen Sie am Early-Adopter-Programm von Cloud Manager teil, um exklusiven Zugriff auf bevorstehende Funktionen vor deren allgemeiner Veröffentlichung zu erhalten.

Die folgenden Early-Adopter-Möglichkeiten stehen derzeit zur Verfügung:

### Edge Delivery-Konfigurations-Pipeline hinzufügen {#add-eds-pipeline}

Konfigurations-Pipelines werden jetzt für Sites unterstützt, die mit Edge Delivery Services erstellt wurden, wodurch diese Funktion über Cloud Service-Umgebungen hinaus erweitert wird. Sie können **Konfigurations-Pipelines** verwenden, um Einstellungen wie Traffic-Filterregeln und gegebenenfalls Konfigurationen der Web Application Firewall (WAF) zu verwalten. Siehe [Unterstützte Konfigurationen](/help/operations/config-pipeline.md#configurations).

![Edge Delivery-Pipeline hinzufügen in der Dropdown-Liste „Pipeline hinzufügen“](/help/implementing/cloud-manager/release-notes/assets/add-edge-delivery-pipeline.png)

Wenn Sie diese neue Funktion testen und Ihr Feedback geben möchten, senden Sie von Ihrer mit Ihrer Adobe ID verknüpften E-Mail-Adresse eine E-](mailto:grp-aemeds-config-pipeline-adopter@adobe.com) an [grp-aemeds-config-pipeline-adopter@adobe.com.

### Holen Sie Ihr eigenes Git - jetzt mit Unterstützung für Azure DevOps {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Kunden können jetzt ihre Azure DevOps-Git-Repositorys in Cloud Manager integrieren, wobei sowohl moderne Azure DevOps- als auch ältere VSTS-Repositorys (Visual Studio Team Services) unterstützt werden.

* Für Edge Delivery Services-Benutzer kann das integrierte Repository zum Synchronisieren und Bereitstellen von Site-Code verwendet werden.
* Für Benutzende von AEM as a Cloud Service und Adobe Managed Services (AMS) kann das Repository mit Full-Stack- und Frontend-Pipelines verknüpft werden.

Die Unterstützung für zusätzliche Pipeline-Typen und die Validierung von Pull-Anforderungen durch Code-Qualitäts-Pipelines wird bald verfügbar sein.

Siehe [Hinzufügen von externen Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

![Dialogfeld „Repository hinzufügen“](/help/implementing/cloud-manager/release-notes/assets/azure-repo.png)

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com). Geben Sie unbedingt an, welche Git-Plattform Sie verwenden möchten und ob Sie sich in einer privaten/öffentlichen oder einer Unternehmens-Repository-Struktur befinden.

#### Häufig gestellte Fragen zu Bring Your Own Git

| Frage | Antwort |
|---|---|
| *Wie kann ein Projekt bei Bedarf zurück zum von Adobe verwalteten Git-Repository wechseln?* | Ein Zurückwechseln ist unkompliziert. [Aktualisieren Sie die Pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md), um auf das Adobe-Repository zu verweisen, und entfernen Sie das externe Repository, wenn es nicht mehr benötigt wird. |
| *Ist es möglich, verschiedene Repositorys für verschiedene Umgebungen zu konfigurieren (z. B. Nicht-Produktion versus Produktion), um Tests zuerst in Nicht-Produktion zu ermöglichen?* | Ja, verschiedene Repositorys können für separate Umgebungen konfiguriert werden. Beispielsweise kann die Entwicklungs- oder Code-Qualitäts-Pipeline auf ein externes Repository verweisen, während die Produktions-Pipeline mit dem Adobe-Repository verbunden bleibt. Stellen Sie sicher, dass der Synchronisierungsauftrag zwischen den beiden Repositorys während dieser Konfiguration aktiv bleibt. |
| *Funktionieren bestehende Einstellungen wie IP-Zulassungslisten weiterhin?* | Ja, bestehende IP-Zulassungslisten funktionieren weiterhin wie gewohnt. Wenn das externe Git-Repository jedoch durch eine Firewall geschützt ist, müssen die erforderlichen [Adobe-IP-Adressen zur Zulassungsliste hinzugefügt werden](/help/implementing/cloud-manager/ip-allow-lists/introduction.md). |
| *Funktionieren alle GitLab-Repository-URLs? Die verwendete Repository-URL folgt dem Format `https://gitlab_dedicated_url.com/path/repo-name.git`, das sich vom Beispiel in der Dokumentation unterscheidet.* | Ja, jedes GitLab-Repository, das API V3 oder V4 unterstützt, wird unterstützt, einschließlich selbst gehosteter GitLab-URLs wie unter [Hinzufügen externer Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md) (`https://git-vendor-name.com/org-name/repo-name.git`) beschrieben. |


<!--
## Bug fixes

* Issue

* Issue

* Issue
-->

<!-- ## Known issues {#known-issues} -->

