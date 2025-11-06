---
title: Konfigurieren der Inhaltsquelle
description: Erfahren Sie, wie Sie die Inhaltsquelle für Ihre Edge Delivery-Site konfigurieren. Verwenden Sie „fstab.yaml“ mit der Helix 4-Architektur oder verwenden Sie den geführten Assistenten in Cloud Manager (oder das Konfigurations-Service-API) mit der Helix 5-Architektur.
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: f82eafc0-03d0-4c69-9b28-e769a012531b
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 100%

---

# Konfigurieren der Inhaltsquelle für Edge Delivery Services mit einem Klick {#config-content-source}

>[!IMPORTANT]
>
>*Helix* ist der interne Name für die zugrunde liegende Architektur, die AEM Sites mit dokumentbasiertem Authoring unterstützt. Es handelt sich nicht um einen Funktions- oder Produktnamen. In diesem Artikel bezieht sich *Helix* auf die Architekturversion, die von Ihren Edge Delivery Sites verwendet wird. Helix 5 ist die aktuelle Version der zugrunde liegenden Architektur; Helix 4 ist die vorherige Version.

Adobe Experience Manager (AEM) Edge Delivery Services ermöglicht die Bereitstellung von Inhalten aus mehreren Quellen wie Google Drive, SharePoint oder AEM selbst mithilfe eines schnellen, global verteilten Edge Networks.

Die Konfiguration der Inhaltsquellen unterscheidet sich bei den beiden Architekturversionen wie folgt:

| Version | Methode zur Konfiguration der Inhaltsquelle |
| --- | --- |
| Helix 4 | YAML-Datei (`fstab.yaml`) |
| Helix 5 | Konfigurations-Service-API (*ohne`fstab.yaml`*) |

Dieser Artikel enthält umfassende Konfigurationsschritte, Beispiele und Validierungsanweisungen für beide Versionen.

**Bevor Sie beginnen**

Wenn Sie die Funktion zum [Erstellen einer Edge Delivery-Site in Cloud Manager mit einem Klick](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md##one-click-edge-delivery-site) verwenden, handelt es sich um eine Helix 5-Site mit einem einzigen Repository. [Befolgen Sie die Helix 5-Anweisungen](#config-helix5) und verwenden Sie die bereitgestellte Helix 4-YAML-Version der Anweisungen als Fallback.

**Ermitteln der Helix-Version**

* Helix 4: Ihr Projekt enthält die Datei `fstab.yaml`.
* Helix 5: Ihr Projekt *verwendet nicht* die Datei `fstab.yaml` und wurde über [Cloud Manager unter Verwendung des geführten Assistenten](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md) oder das entsprechende API eingerichtet.

Bestätigen Sie dies anhand der Repository-Metadaten oder wenden Sie sich an Ihre bzw. Ihren Admin, wenn Sie nach wie vor unsicher sind.

## Konfigurieren der Inhaltsquelle für Helix 4

In Helix 4 definiert die Datei `fstab.yaml` die Inhaltsquelle für Ihre Site. Diese Datei befindet sich im Stammverzeichnis Ihres GitHub-Repositorys und ordnet Präfixe von URL-Pfaden (sogenannte Bereitstellungspunkte) externen Inhaltsquellen zu. Ein typisches Beispiel sieht wie folgt aus:

```yaml
mountpoints:
  /: https://drive.google.com/drive/folders/your-folder-id
```

Das Beispiel oben dient nur zu Veranschaulichungszwecken. Die eigentliche URL sollte auf Ihre Inhaltsquelle verweisen, z. B. auf einen Google Drive-Ordner, ein SharePoint-Verzeichnis oder einen AEM-Pfad.

**Konfigurieren der Inhaltsquelle für Helix 4:**

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

Helix 5 hat kein Repository, verwendet nicht die Datei `fstab.yaml` und unterstützt mehrere Sites, die dasselbe Verzeichnis nutzen. Die Konfiguration wird über das Konfigurations-Service-API oder die Edge Delivery Sites-Benutzeroberfläche verwaltet. Die Konfiguration erfolgt auf Site-Ebene (nicht auf Repository-Ebene).

Die konzeptionellen Unterschiede sind:

| Aspekt | Helix 4 | Helix 5 |
| --- | --- | --- |
| Konfiguration | Erfolgt durch `fstab.yaml` | Erfolgt über das API oder die Benutzeroberfläche anstelle von YAML. |
| Bereitstellungspunkte | Definiert in `fstab.yaml`. | Nicht erforderlich Der Stamm wird implizit verstanden. |

**Konfigurieren der Inhaltsquelle für Helix 5:**

1. Führen Sie eine Authentifizierung über einen API-Schlüssel oder ein Zugriffs-Token mithilfe des Konfigurations-Service-APIs durch.
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
