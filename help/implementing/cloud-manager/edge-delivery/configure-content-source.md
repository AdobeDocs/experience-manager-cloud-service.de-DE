---
title: Konfigurieren des Source-Inhalts
description: Erfahren Sie, wie Sie die Inhaltsquelle für Ihre Edge Delivery-Site entweder mit fstab.yaml in Helix 4 oder mit dem geführten Assistenten in Cloud Manager (oder der Konfigurations-Service-API) in Helix 5 konfigurieren.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: f82eafc0-03d0-4c69-9b28-e769a012531b
source-git-commit: 56ab7a402a2fa7bdcf30bd66045b04e9314bed64
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 2%

---

# Konfigurieren Sie Ihre Inhaltsquelle für Edge Delivery Services mit einem Klick {#config-content-source}

Adobe Experience Manager (AEM) Edge Delivery Services ermöglicht die Bereitstellung von Inhalten aus mehreren Quellen wie Google Drive, SharePoint oder AEM selbst mithilfe eines schnellen, global verteilten Edge-Netzwerks.

Die Konfiguration der Inhaltsquellen unterscheidet sich zwischen Helix 4 und Helix 5 wie folgt:

| Version | Konfigurationsmethode der Inhaltsquelle |
| --- | --- |
| Helix 4 | YAML-Datei (`fstab.yaml`) |
| Helix 5 | Konfigurations-Service-API (*keine`fstab.yaml`*) |

Dieser Artikel enthält umfassende Konfigurationsschritte, Beispiele und Validierungsanweisungen für beide Versionen.

**Bevor Sie beginnen**

Wenn Sie Edge Delivery mit [ Klick in Cloud Manager verwenden, ](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md##one-click-edge-delivery-site) Ihre Website Helix 5 mit einem einzigen Repository. [Befolgen Sie die Helix 5](#config-helix5)Anweisungen und verwenden Sie die bereitgestellte Helix 4 YAML-Version der Anweisungen als Ausweichlösung.

**Helix-Version ermitteln**

* Helix 4: Ihr Projekt enthält eine `fstab.yaml`.
* Helix 5: Ihr Projekt *verwendet*) verwendet `fstab.yaml` und wurde über [Cloud Manager mithilfe des Assistenten oder ](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md) API eingerichtet.

Bestätigen Sie dies anhand der Repository-Metadaten oder wenden Sie sich an Ihren Administrator, wenn Sie sich noch nicht sicher sind.

## Konfigurieren der Inhaltsquelle für Helix 4

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

### Validierung

* Klicken Sie mithilfe der AEM Sidekick Chrome-Erweiterung auf **Vorschau** > **Veröffentlichen** > **Live-Site testen**.
* URL validieren: `https://main--<repo>--<org>.hlx.page/`

## Konfigurieren der Inhaltsquelle für Helix 5 {#config-helix5}

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

### Validierung

* Klicken Sie mithilfe der AEM Sidekick Chrome-Erweiterung auf **Vorschau** > **Veröffentlichen** > **Live-Site testen**.
* URL validieren: `https://main--<repo>--<org>.aem.page/`
* (Optional) Überprüfen Sie die aktuelle Konfiguration mithilfe des folgenden `GET`-API-Aufrufs:

  ```bash
  GET /api/{program}/{programId}/site/{siteId}
  ```
