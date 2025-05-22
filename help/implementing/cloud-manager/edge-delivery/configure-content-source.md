---
title: Konfigurieren des Source-Inhalts
description: Erfahren Sie, wie Sie die Inhaltsquelle für Ihre Edge Delivery-Site konfigurieren. Verwenden Sie „fstab.yaml“ mit der Helix 4-Architektur oder verwenden Sie den geführten Assistenten in Cloud Manager (oder der Konfigurations-Service-API) mit der Helix 5-Architektur.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: f82eafc0-03d0-4c69-9b28-e769a012531b
source-git-commit: 71618a5603328990603db2ee7554048c9020a883
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 40%

---

# Konfigurieren Sie Ihre Inhaltsquelle für Edge Delivery Services mit einem Klick {#config-content-source}

>[!IMPORTANT]
>
>*Helix* ist der interne Name für die zugrunde liegende Architektur, die AEM Sites mit dokumentbasiertem Authoring unterstützt. Es handelt sich nicht um einen Funktions- oder Produktnamen. In diesem Artikel bezieht sich *Helix* auf die Architekturversion, die von Ihren Edge Delivery Sites verwendet wird. Helix 5 ist die aktuelle Version der zugrunde liegenden Architektur; Helix 4 ist die vorherige Version.

Adobe Experience Manager (AEM) Edge Delivery Services ermöglicht die Bereitstellung von Inhalten aus mehreren Quellen wie Google Drive, SharePoint oder AEM selbst mithilfe eines schnellen, global verteilten Edge Network.

Die Konfiguration der Inhaltsquellen unterscheidet sich zwischen den beiden Architekturversionen wie folgt:

| Version | Konfigurationsmethode der Inhaltsquelle |
| --- | --- |
| Helix 4 | YAML-Datei (`fstab.yaml`) |
| Helix 5 | Konfigurations-Service-API (*ohne`fstab.yaml`*) |

Dieser Artikel enthält umfassende Konfigurationsschritte, Beispiele und Validierungsanweisungen für beide Versionen.

**Bevor Sie beginnen**

Wenn Sie Edge Delivery mit [ Klick in Cloud Manager verwenden](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md##one-click-edge-delivery-site) verwendet Ihre Site Helix 5 mit einem einzigen Repository. [Befolgen Sie die Helix 5](#config-helix5)Anweisungen und verwenden Sie die bereitgestellte Helix 4 YAML-Version der Anweisungen als Ausweichlösung.

**Ermitteln der Helix-Version**

* Helix 4: Ihr Projekt enthält die Datei `fstab.yaml`.
* Helix 5: Ihr Projekt *verwendet*) verwendet `fstab.yaml` und wurde über [Cloud Manager mithilfe des Assistenten oder ](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md) API eingerichtet.

Bestätigen Sie dies anhand der Repository-Metadaten oder wenden Sie sich an Ihre bzw. Ihren Admin, wenn Sie nach wie vor unsicher sind.

## Konfigurieren der Inhaltsquelle für Helix 4

In Helix 4 definiert die `fstab.yaml` die Inhaltsquelle für Ihre Site. Diese Datei befindet sich im Stammverzeichnis Ihres GitHub-Repositorys und ordnet URL-Pfadpräfixe (so genannte mountpoints) externen Inhaltsquellen zu. Ein typisches Beispiel sieht wie folgt aus:

```yaml
mountpoints:
  /: https://drive.google.com/drive/folders/your-folder-id
```

Das obige Beispiel dient nur zur Veranschaulichung. Die eigentliche URL sollte auf Ihre Inhaltsquelle verweisen, z. B. auf einen Google Drive-Ordner, einen SharePoint-Ordner oder einen AEM-Pfad.

**So konfigurieren Sie die Inhaltsquelle für Helix 4:**

Die Schritte variieren je nach verwendetem Quellsystem.

* **Google Drive**

   1. Erstellen Sie einen Google Drive-Ordner.
   1. Geben Sie den Ordner für `helix@adobe.com` frei.
   1. Rufen Sie den freigebbaren Ordner-Link ab.
   1. Aktualisieren Sie die Datei `fstab.yaml` wie folgt:

      ```yaml
      mountpoints: 
          /: https://drive.google.com/drive/folders/<folder-id>
      ```

   1. Übergeben und pushen Sie die Änderungen auf GitHub.

* **SharePoint**

   1. Erstellen Sie einen SharePoint-Ordner oder eine Dokumentenbibliothek.
   1. Geben Sie den Zugriff für `helix@adobe.com` frei.
   1. Rufen Sie die Ordner-URL ab.
   1. Aktualisieren Sie die Datei `fstab.yaml` wie folgt:

      ```yaml
      mountpoints:
        /: https://<tenant>.sharepoint.com/sites/<site>/Shared%20Documents/<folder>
      ```

   1. Übergeben und pushen Sie die Änderungen auf GitHub.

* **AEM**

   1. Identifizieren Sie Ihren AEM-Inhaltspfad.
   1. Verwenden Sie die URL für den AEM-Inhaltsexport wie folgt:

      ```yaml
      mountpoints:
        /: https://author.<your-aem-instance>.com/bin/franklin.delivery/<org>/<repo>/main
      ```

   1. Übergeben und pushen Sie die Änderungen auf GitHub.

### Validierung

* Klicken Sie mithilfe der AEM Sidekick Chrome-Erweiterung auf **Vorschau** > **Veröffentlichen** > **Live-Site testen**.
* Validieren Sie folgende URL: `https://main--<repo>--<org>.hlx.page/`.

## Konfigurieren der Inhaltsquelle für Helix 5 {#config-helix5}

Helix 5 ist reaktionslos, verwendet keine `fstab.yaml` und unterstützt mehrere Websites, die dasselbe Verzeichnis gemeinsam nutzen. Die Konfiguration wird über die Konfigurations-Service-API oder die Edge Delivery Sites-Benutzeroberfläche verwaltet. Die Konfiguration erfolgt auf Site-Ebene (nicht auf Repository-Ebene).

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

1. Validieren Sie die Antwort (erwartet: HTTP 200 OK).

### Validierung

* Klicken Sie mithilfe der AEM Sidekick Chrome-Erweiterung auf **Vorschau** > **Veröffentlichen** > **Live-Site testen**.
* Validieren Sie folgende URL: `https://main--<repo>--<org>.aem.page/`.
* (Optional) Überprüfen Sie die aktuelle Konfiguration mithilfe des folgenden `GET`-API-Aufrufs:

  ```bash
  GET /api/{program}/{programId}/site/{siteId}
  ```
