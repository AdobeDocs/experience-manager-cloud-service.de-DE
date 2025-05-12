---
title: Versionshinweise für Cloud Manager 2025.5.0
description: Erfahren Sie mehr über die Version Cloud Manager 2025.5.0 in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: effa19a98d59993e330e925fb933a436ff9d20d7
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 21%

---

# Versionshinweise für Cloud Manager 2025.5.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

Erfahren Sie mehr über die Version Cloud Manager 2025.5.0 in AEM (Adobe Experience Manager) as a Cloud Service.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Die Version 2025.5.0 von Cloud Manager in AEM as a Cloud Service wurde am Donnerstag, dem Freitag, 8. Mai 2025 veröffentlicht.

Die Veröffentlichung der nächsten Version ist für Donnerstag, den Freitag, 5. Juni 2025 geplant.

## Neue Funktionen {#what-is-new}

### Ändern der Inhaltsquelle mit einem Klick für Edge Delivery Services

Adobe Experience Manager (AEM) Edge Delivery Services ermöglicht die Bereitstellung von Inhalten aus mehreren Quellen wie Google Drive, SharePoint oder AEM selbst mithilfe eines schnellen, global verteilten Edge-Netzwerks.

Die Konfiguration der Inhaltsquellen unterscheidet sich zwischen Helix 4 und Helix 5 wie folgt:

| Version | Konfigurationsmethode |
| --- | --- |
| Helix 4 | YAML-Datei (`fstab.yaml`) |
| Helix 5 | Konfigurations-Service-API (*keine`fstab.yaml`*) |

Dieser Artikel enthält umfassende Konfigurationsschritte, Beispiele und Validierungsanweisungen für beide Versionen.

B **Bevor Sie beginnen**

Wenn Sie Edge Delivery mit [ Klick in Cloud Manager verwenden, ](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md##one-click-edge-delivery-site) Ihre Website Helix 5 mit einem einzigen Repository. Befolgen Sie die Helix 5-Anweisungen und verwenden Sie die bereitgestellte Helix 4 YAML-Version als Ausweichlösung.

**Helix-Version ermitteln**

* Helix 4: Ihr Projekt enthält eine `fstab.yaml`.
* Helix 5: Ihr Projekt ** verwendet keine `fstab.yaml` und wurde über die Edge Delivery Services-Benutzeroberfläche oder -API eingerichtet.

Bestätigen Sie dies anhand der Repository-Metadaten oder wenden Sie sich an Ihren Administrator, wenn Sie sich noch nicht sicher sind.

#### Konfigurieren der Inhaltsquelle (Helix 4)

In Helix 4 wird die Inhaltsquelle in einer YAML-Konfigurationsdatei mit dem Namen `fstab.yaml` definiert, die sich im Stammverzeichnis Ihres GitHub-Repositorys befindet.

##### YAML-Dateiformat

Die `fstab.yaml` definiert Bereitstellungspunkte (URL-Pfadpräfixe, die Inhaltsquellen-URLs zugeordnet sind) ähnlich dem folgenden Beispiel (nur zu Veranschaulichungszwecken):

```yaml
mountpoints:
  /: https://drive.google.com/drive/folders/your-folder-id
```

##### Inhaltsquelle ändern

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

#### Konfigurieren der Inhaltsquelle (Helix 5)

Helix 5 ist reaktionslos, verwendet keine `fstab.yaml` und unterstützt mehrere Websites, die denselben Ordner teilen. Die Konfiguration wird über die Konfigurations-Service-API oder die Edge Delivery Services-Benutzeroberfläche verwaltet. Die Konfiguration erfolgt auf Site-Ebene (nicht auf Repository-Ebene).

##### Konzeptionelle Unterschiede

| Aspekt | Helix 4 | Helix 5 |
| --- | --- | --- |
| Konfigurationsdatei | `fstab.yaml` | API- oder UI-Konfiguration |
| Bereitstellungspunkte | YAML-definiert | Nicht erforderlich (impliziter Stamm) |

##### Inhaltsquelle ändern

Verwenden Sie die Konfigurations-Service-API.

1. Authentifizierung über einen API-Schlüssel oder ein Zugriffstoken.
1. Führen Sie den folgenden `PUT`-API-Aufruf aus:

   ```bash
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

### Pipeline von Edge Delivery hinzufügen {#add-eds-pipeline}

**Pipelines** werden jetzt für Sites unterstützt, die mit Edge Delivery Services erstellt wurden, wodurch diese Funktion über Cloud Service-Umgebungen hinaus erweitert wird. Sie können **Pipelines** verwenden, um Einstellungen wie Traffic-Filterregeln und gegebenenfalls Konfigurationen der Web Application Firewall (WAF) zu verwalten. Siehe [Unterstützte Konfigurationen](/help/operations/config-pipeline.md#configurations).

<!-- ![Add Edge Delivery pipeline in Add Pipeline drop-down list](/help/implementing/cloud-manager/release-notes/assets/add-edge-delivery-pipeline.png) -->

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

<!--
## Bug fixes

* Issue

* Issue

* Issue
-->

<!-- ## Known issues {#known-issues} -->

